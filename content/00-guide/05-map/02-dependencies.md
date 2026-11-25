---
title: The dependencies between the volumes
nodes: []
sources: []
status: drafted
drafted_by: writer
reviewed_by: []
---
## The dependencies between the volumes

### The volumes

A volume uses the results of the volumes that the following table lists for it. Volumes 1 and 2 use only the prerequisites of Chapter 1. A volume that the table does not list for another volume is not needed to read it, although it can help.

| Volume | Needs |
|---|---|
| 3 | 1, and the compact groups of 2 |
| 4 | 1 |
| 5 | 2, 3, 4 |
| 6 | 2, 3 |
| 7 | 5, 6 |
| 8 | 5, 6; 7 helps |
| 9 | 6, 8 |
| 10 | 4, 5, 6, 8 |
| 11 | 4, 5, 10; the $p$-adic Hodge theory of Part I of 12 |
| 12 | for Part I: 1, 2 and rigid geometry; for Part II: 6, 11 |
| 13 | 2, 3, 6; Part III of 12 for the bridge to Fargues-Scholze |

The table has no cycle when the parts of Volume 12 count separately. Part I of Volume 12 comes before Volume 11, and Part II comes after it.

**Example 5.2.1 (the shortest way to modularity).** A reader who wants the proof of the modularity theorem needs Volume 11. Volume 11 needs Volumes 4, 5 and 10, and Volume 10 needs Volumes 4, 5, 6 and 8. Thus the reader needs Volumes 1 to 6, 8, 10 and 11, and Part I of Volume 12. Volumes 7, 9 and 13 are not needed.

### The tiers of the map

The nodes of the map fall into eleven tiers, T0 to T10. A tier uses only the tiers before it, with a few exceptions that the list of sources of the project states. The tiers correspond to the volumes as in the table.

| Tier | Subject | Volume |
|---|---|---|
| T0 | references: the standard texts that define the language | all |
| T1 | number fields, local fields and adeles | 1 |
| T2 | algebraic and reductive groups, root data, $L$-groups | 2 |
| T3 | class field theory and $GL_1$ | 3 |
| T4 | modular and automorphic forms of $GL_2$ | 4, 5 |
| T5 | smooth representations and local Langlands | 6 |
| T6 | $L$-functions, converse theorems and functoriality | 7 |
| T7 | the trace formula, endoscopy and Arthur's classification | 8, 9 |
| T8 | Shimura varieties, Galois representations and modularity | 10, 11 |
| T9 | $p$-adic Hodge theory, $p$-adic and mod $p$ Langlands, Fargues-Scholze | 12 |
| T10 | function fields and geometric Langlands | 13 |

A node of tier T8 can have a short statement and a long proof. For example, the statement of the modularity theorem needs only the vocabulary of Volume 4, but its node is in tier T8 because its proof needs Galois deformations. The handbook states such a theorem early, as Chapter 2 does, and proves it in the volume of its tier.
