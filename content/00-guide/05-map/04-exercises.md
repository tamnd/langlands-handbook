---
title: Exercises and notes
nodes: []
sources: [Tat79]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Exercises

1. Use the table of dependencies of the second section to list the volumes that a reader needs for Volume 9. Do the same for Volume 13.
2. Show that the table of dependencies has a cycle when Volume 12 counts as one volume with all the needs of its parts. Explain why the split of Volume 12 into parts removes the cycle.
3. Draw the graph of the "uses" relation of the nodes in the first section, from the fields `uses` of the node files: Kronecker-Weber uses global reciprocity, global reciprocity uses local reciprocity, and so on. Find the nodes that no other node uses.
4. The rule for the status proved asks that each node that a proof uses is proved. Give an example of two nodes $A$ and $B$, where $A$ uses $B$, $A$ has a Lean proof with the hypothesis $B$, and $B$ has no Lean proof. What is the status of $A$?
5. Pick one theorem of Chapter 2. Find its source in the reading list, and compare its statement there with the statement in Chapter 2. Check the normalization of the reciprocity map or of the coefficients of the $q$-expansion.

## Notes and history

The map follows the blueprints of the formalization projects in Lean, such as the blueprint of the project on Fermat's Last Theorem at Imperial College. It differs from them in three ways: the nodes are data and not LaTeX, the status is computed, and the map contains the open conjectures and the research routes. A tag is a stable name for a result in a text that changes, in the same way as a tag of the Stacks project.

The reading list is not complete. It gives the texts that the volumes of the handbook follow, and a few surveys. The proceedings of the Corvallis conference (1979), which contain Tate's article [Tat79], and the proceedings of the IHES summer school of 2022 on the Langlands program (2025) are two further sources that cover most parts of the program.
