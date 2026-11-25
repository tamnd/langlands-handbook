---
title: Numbers, Lean lines and statuses
nodes: []
sources: []
status: drafted
drafted_by: writer
reviewed_by: []
---
## Numbers, Lean lines and statuses

### The numbers

Each statement of a volume has a number with three parts. Theorem 2.3.4 is the fourth statement of the third section of Chapter 2 of its volume. Definitions, theorems, examples and remarks share one count, so the numbers in a section are consecutive. A reference to a statement of another volume adds the volume, as in Volume 3, Theorem 2.1.1. The numbers are written into the source files when the book is built, so the source on GitHub and the printed book use the same numbers.

### The line under a statement

A statement of the handbook that has a node in the map of the project has a line under it of this form.

```
Node: LGAV7YV6K6 · Lean: `Langlands.LocalReciprocityGL1` (status: stated)
```

The tag LGAV7YV6K6 names the node in the map of tamnd/langlands. The map is a list of the definitions, theorems and conjectures of the program, with the uses between them. In the online book the tag is a link to the page of the node. The Lean name is the name of the declaration in tamnd/langlands-lean that states the result. The status in brackets is not in the source of the handbook. The builder computes it from the Lean code and the records of the project at the time of the build, so it cannot go out of date in a release.

A statement without a node can still have a Lean line. The line "Lean: `Langlands.WeilGroup.isOpen_inertia`" names a lemma of the Lean code that proves the statement. The line "Lean: not stated yet, planned for milestone S3" says that the Lean statement does not exist yet, and it names the milestone of the project that plans it. A statement with no Lean line is a statement of the text only. Most examples and remarks are of this kind.

### The statuses

The map gives each node one status. The status says what the Lean code contains, not what the literature contains. Thus a theorem of 1930 can have the status unstated, and the status proved says more than "a proof is published".

| Status | Meaning |
|---|---|
| planned | The handbook names a milestone for the Lean statement, and the statement does not exist yet. |
| unstated | The node has no Lean statement. The map lists the definitions that the statement needs and that do not exist yet. |
| stated | The Lean statement exists, and it builds. |
| faithful | The Lean statement passed the fidelity checks of its class (Chapter 4). |
| defined | The node is a definition, and the Lean definition exists and builds. |
| proved | A Lean proof exists. It uses only the three standard axioms of Lean, and each node that it uses is proved. |
| proved-mod | A Lean proof exists, and it takes other nodes as named hypotheses. Each hypothesis is a published theorem that is not yet formalized. |
| open | The statement is an open conjecture. No proof is claimed. |
| refuted | A Lean proof of the negation of the statement exists. |
| claimed | The statement is a recent claim of a proof that the project has not checked. It is never a hypothesis of another node. |

Two of these statuses need a comment. The status proved-mod makes a conditional result visible. For example, a Lean proof of the Hasse-Weil conjecture for elliptic curves over $\mathbb{Q}$ that assumes the modularity theorem would have the status proved-mod, and the site would list the modularity theorem as its hypothesis. The status refuted applies to statements that are false as written. Chapter 4 gives an example: a published Lean statement of the modularity theorem that is false because of a wrong normalization.

The status open is never replaced by proved on the strength of a paper alone. A recent paper that claims a proof of an open conjecture gives the status claimed. A person with the right background must check the claim before the handbook treats the result as a theorem.
