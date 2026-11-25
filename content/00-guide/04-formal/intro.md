# What it means to formalize a statement

A Lean proof of a theorem is only as good as the Lean statement of the theorem. If the statement says something else than the mathematics, a complete proof of it proves the wrong thing. If the statement is false, no proof exists, and the work on it is lost. If the statement is trivial, a short proof exists that says nothing. Thus the project checks each statement before it tries to prove it.

This chapter explains these checks. The first section explains why a statement of the project is a definition of a proposition and not an axiom. The second section lists the seven checks F1 to F7. The third section gives two errors that the checks found: a statement whose uniqueness fails without the normalization, and a published statement of the modularity theorem that is false. The reader does not need to know Lean. The few lines of Lean code in the chapter are explained in words.
