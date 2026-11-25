---
title: The map of the project
nodes: []
sources: []
status: drafted
drafted_by: writer
reviewed_by: []
---
## The map of the project

### Nodes and edges

The *map* is a directed graph without cycles. Its nodes are statements and definitions of the program, and its edges are the relation "uses". The map is in the folder `blueprint/nodes/` of the repository tamnd/langlands, with one file for each node. Every other part of the project reads it: the Lean library, the site and the handbook.

Each node has a stable *tag*. The tag is the two letters `LG` and eight characters of base 32, for example `LGAV7YV6K6`. A tag never changes, and the handbook cites a node only by its tag. A node file has these fields:

- the *kind*: definition, theorem, lemma, conjecture, example, counterexample or check;
- the *title* and the *statement*, in words and in LaTeX;
- the *sources*: the papers and the places in them where the result is proved;
- the *uses*: the tags of the nodes that the statement or its proof needs;
- the *Lean names*: the name of the statement and, when it exists, the name of the proof;
- the *tier*: the part of the program to which the node belongs (second section).

The map holds the open conjectures as well as the theorems. Thus it is also the plan of the project. The research directions of the project are the *routes* in the file `blueprint/routes.yaml`. Each route names the nodes that it works on first.

### The records

The map has three kinds of records next to the nodes.

- A *paper record* in `papers/` gives the bibliographic data of one source, the version that the project read, and the reason why the project needs it. Its key, such as `Ser67` or `BCDT01`, is the key that the handbook uses in its citations.
- A *claim record* in `claims/` describes a recent result that is not yet checked by the community. Its node has the status claimed, and no other node uses it as a hypothesis.
- The *fidelity records* in `records/` give the results of the checks F1 to F7 of Chapter 4 for each Lean statement.

### The computed status

The status of a node is not written by hand. A tool of the project reads the Lean library and the records, and it computes the status of each node from them, with the rules of Chapter 1. For example, a node is proved only if its Lean proof exists, the proof uses only the three standard axioms, and each node that it uses is proved. The builder of the handbook reads the computed status at build time and writes it into each Node line. Thus a printed copy of the handbook shows the status on the date of its build, and the site shows the current status.

### The nodes of Volume 0

The following table lists the nodes of the map on the date of this draft, with the chapter and the section of this volume that cite them. The table gives no status, because the status changes. The Node lines in the text give it.

| Tag | Kind | Title | Place |
|---|---|---|---|
| LGBPNG162F | definition | The Weil group of a nonarchimedean local field | 3.1 |
| LGQVB4Z4KN | definition | Geometric Frobenius elements | 3.1 |
| LGVSG50K41 | definition | The abelianized Weil group | not cited |
| LGHEK0BGSD | theorem | Finite abelian local reciprocity | 2.1 |
| LGAV7YV6K6 | theorem | Local class field theory as the Langlands correspondence for $GL_1$ | 2.1, 4.3 |
| LG875TDM3B | theorem | The local existence theorem | 2.1 |
| LGVAKJJD8Y | theorem | Global reciprocity | 2.1 |
| LGX8K4ZEGW | theorem | The global existence theorem | 2.1 |
| LG06WS8A1Y | theorem | The theorem of Kronecker and Weber | 2.1 |
| LGZ55EK0PA | theorem | Modularity of semistable elliptic curves over $\mathbb{Q}$ | 2.2 |
| LGPNZWXVH5 | theorem | Modularity of elliptic curves over $\mathbb{Q}$ | 2.2 |
| LG5W3CRDEA | theorem | The Hasse-Weil conjecture for elliptic curves over $\mathbb{Q}$ | 2.2 |
| LGV8B6TVWZ | theorem | The Ramanujan-Petersson conjecture for holomorphic forms | 2.2 |
| LG1DP2ZDPA | theorem | The Ramanujan bound for $\tau$ follows from the statement of the project | 2.2 |
| LGVZHDXVTZ | theorem | The Sato-Tate conjecture for elliptic curves over $\mathbb{Q}$ | 2.2 |
| LG6W8W7GE6 | theorem | The Sato-Tate statement of formal-conjectures follows from the statement of the project | not cited |
| LGDD6VVKSR | counterexample | The modularity statement of formal-conjectures is false as written | 4.3 |

The titles are those of the node files. Some of them name a theorem by its old name, such as "the Hasse-Weil conjecture", although the result is now a theorem for elliptic curves over $\mathbb{Q}$.

The map grows with each milestone of the project. The first nodes are those of class field theory and of $GL_2$ over $\mathbb{Q}$. The next ones are the vocabulary of the local Langlands correspondence: smooth representations, Weil-Deligne representations, $L$-factors and $\varepsilon$-factors.
