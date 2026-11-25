---
title: What the handbook contains
nodes: []
sources: []
status: drafted
drafted_by: writer
reviewed_by: []
---
## What the handbook contains

The Langlands program is a set of conjectures and theorems that connect three kinds of objects. The first kind is the representations of Galois groups of number fields and of local fields. The second kind is the automorphic representations of reductive groups over the adeles, and the smooth representations of reductive groups over local fields. The third kind is the L-functions and the $\varepsilon$-factors that both kinds carry. The program predicts that the objects of the first two kinds match, and that the match keeps the L-functions.

The simplest case is the group $GL_1$. For $GL_1$ the program is class field theory, which is a theorem. Volume 3 proves it. The next case is $GL_2$. For $GL_2$ over a local field the correspondence is a theorem of Kutzko, and over $\mathbb{Q}$ the modularity of elliptic curves is a theorem of Wiles, Taylor-Wiles and Breuil-Conrad-Diamond-Taylor. Volumes 4 to 7 prove the local results and explain the global ones. The general case is open. Volume 13 states the open conjectures, and it says which parts of them are proved, which are claimed, and which are not understood.

Each volume is a textbook. A chapter has definitions, theorems with proofs, examples and exercises. A chapter ends with a section of notes and history, which names the people who found the results and gives the sources.

The handbook has a second side. Each theorem that has a Lean statement has a line under it with the name of the Lean declaration and its status. The status is not written by hand. A tool reads it from the Lean code of tamnd/langlands-lean when the book is built. Thus the reader can see which results of the book have a checked proof, which have only a statement, and which have neither.

The book does not claim a proof of any open conjecture of the program. When a chapter states a conjecture, the line under it says "open".
