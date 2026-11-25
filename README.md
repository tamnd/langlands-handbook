# The Langlands Handbook

The Langlands Handbook is a textbook of the Langlands program. It starts with local fields and class field theory and goes to the local Langlands correspondence, the trace formula, modularity and the geometric program. It is for graduate students and for mathematicians, and it comes as a set of books in PDF and EPUB.

Each chapter is written as a mathematician writes a textbook. It defines its objects, states its results with numbers (Theorem 2.3.1), proves them, gives examples, and ends with exercises and notes. Where a result has a Lean form in the project [tamnd/langlands](https://github.com/tamnd/langlands), a line under the statement gives the node of the map, the Lean name and the status of the Lean proof. The web version of the map is at [langlands.tamnd.com](https://langlands.tamnd.com).

## What is open

Class field theory, the local Langlands correspondence for $GL_n$, the modularity of elliptic curves over $\mathbb{Q}$ and the unramified geometric conjecture in characteristic 0 are theorems. Functoriality, global reciprocity for $GL_n$ over number fields and the local correspondence for a general reductive group are open. The handbook does not claim a proof of an open conjecture. Volume 13 reports the work of the project on the open parts. The builder writes the status of each node from the records of the map at build time. No status in the books is written by hand.

## The volumes

| | Volume |
|---|---|
| 0 | Guide |
| 1 | Number fields, local fields and adeles |
| 2 | Algebraic groups and their representations |
| 3 | Class field theory and $GL_1$ |
| 4 | Modular forms and elliptic curves |
| 5 | Automorphic representations of $GL_2$ |
| 6 | Representations of $p$-adic groups and the local Langlands correspondence |
| 7 | L-functions, converse theorems and functoriality for $GL_n$ |
| 8 | The trace formula |
| 9 | Endoscopy and Arthur's classification |
| 10 | Shimura varieties and automorphic Galois representations |
| 11 | Galois deformations and modularity |
| 12 | $p$-adic Hodge theory and $p$-adic Langlands |
| 13 | Function fields, geometric Langlands and the open problems |

A volume has a release when all its chapters have the status `reviewed`. Volume 13 is the exception: it has a release at each milestone of the project, as a research report. The books are in the [releases](https://github.com/tamnd/langlands-handbook/releases).

## The content format

A volume is a folder `content/<NN-slug>/`, for example `content/00-guide/`. It has a file `volume.yaml` with `number`, `title` and `subtitle`. It can have an `intro.md`.

A chapter is a folder `content/<NN-volume>/<NN-chapter>/`. It has an optional `intro.md`, whose `#` heading is the title of the chapter, and one file `NN-<slug>.md` for each section. The number of the chapter is the `NN` of its folder.

A section file starts with YAML front matter:

```markdown
---
title: The local reciprocity map
nodes: [LG0000000A]
sources: [Ser67]
status: drafted
drafted_by: writer
reviewed_by: []
---
## The local reciprocity map

**Theorem (local reciprocity).** Let $K$ be a nonarchimedean local field ...

Node: LG0000000A · Lean: `Langlands.localReciprocityGL1`

*Proof.* ... $\square$
```

- `nodes` lists the tags of the nodes of the map that the section uses. Each tag must be a file `blueprint/nodes/<TAG>.yaml` of the map.
- `sources` lists the keys of the papers that the section cites. Each key must be a file `papers/<Key>.yaml` of the map. The build lists these papers at the end of the chapter.
- `status` is `drafted`, `checked` or `reviewed`. The status of a chapter is the lowest status of its sections. A chapter that is not `reviewed` is a draft: the PDF has a Draft mark on its first page, and the EPUB has a Draft mark at its start.
- `reviewed_by` lists the people who have read the section. A section at status `reviewed` must have at least one name.

The text of a section starts with a `##` heading. A statement starts with a bold head: `**Definition.**`, `**Theorem (Name).**`, and so on. The build numbers each `##` heading (2.3) and each statement (Theorem 2.3.1). `lhb number --write` writes the same numbers into the source files, so that the source on GitHub reads as the book does.

A statement that has a node has a line ``Node: <TAG> · Lean: `<Name>` `` under it. At build time `lhb` reads the status of the node and adds it to the line, for example "(status: proved)". The tag becomes a link to `https://langlands.tamnd.com/node/<TAG>/` in the PDF and in the EPUB. A status that is written in the source is replaced.

## The status of a node

`lhb` reads the map from a checkout of tamnd/langlands. If the map has a file `records/lean.json` that contains the Lean name of the statement of the node, the status comes from that record: "proved" when the record of the proof exists and has no `sorry`, "open" for a conjecture, and "stated" in the other cases. A record can also give the status itself. If there is no such record, the status is "unstated".

## Build

You need Python 3.11 or later, [pandoc](https://pandoc.org) 3.8 or later and [Tectonic](https://tectonic-typesetting.github.io). Put a checkout of [tamnd/langlands](https://github.com/tamnd/langlands) next to this repository, at `../langlands`, or give its path with `--map PATH` or the environment variable `LHB_MAP`.

```sh
pip install .
python scripts/style.py
python -m lhb check
python -m lhb number --write
python -m lhb build --volume 0,3 --formats pdf,epub
python -m unittest discover -s tests
```

`lhb check` reports a section with a bad front matter, a `Node:` line or a `nodes` tag that is not in the map, a source key that is not in the map, and an en dash or an em dash. It also gives warnings that do not fail the check, for example a theorem with no `Node:` line.

The books go to `build/langlands-handbook-<NN-slug>-<version>.pdf` and `.epub`. The version is in the first line of `EDITION`, and the second line gives the commit of tamnd/langlands that the edition describes. The pipeline is that of [The Riemann Handbook](https://github.com/tamnd/riemann-handbook): Markdown, then pandoc with `filters/lhb.lua`, then LaTeX with `tex/handbook.sty`, then Tectonic. The EPUB is EPUB 3 with MathML.

## Licence

The text is licensed under [CC BY 4.0](LICENSE-CONTENT). The builder `lhb`, the filter and the style files are licensed under the [MIT licence](LICENSE).

Please report errors at [issues](https://github.com/tamnd/langlands-handbook/issues). [CONTRIBUTING.md](CONTRIBUTING.md) tells how to send a change.
