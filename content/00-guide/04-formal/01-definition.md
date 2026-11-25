---
title: A statement is a definition
nodes: []
sources: []
status: drafted
drafted_by: writer
reviewed_by: []
---
## A statement is a definition

### Propositions as definitions

In Lean a proposition is a term of the type `Prop`. A proof of a proposition `P` is a term of the type `P`. The project states each theorem and each conjecture of the map as a definition of a proposition. For example, the theorem of Kronecker and Weber is the following definition in the file `Langlands/Statements/ClassField.lean` of tamnd/langlands-lean.

```lean
def KroneckerWeber : Prop :=
  ∀ L : IntermediateField ℚ (AlgebraicClosure ℚ),
    FiniteDimensional ℚ L → IsAbelianGalois ℚ L →
    ∃ (n : ℕ) (ζ : AlgebraicClosure ℚ), 0 < n ∧ IsPrimitiveRoot ζ n ∧
      L ≤ IntermediateField.adjoin ℚ {ζ}
```

In words: for each subfield $L$ of $\bar{\mathbb{Q}}$ that is finite and abelian over $\mathbb{Q}$, there are an integer $n > 0$ and a primitive $n$-th root of unity $\zeta$ with $L \subseteq \mathbb{Q}(\zeta)$. The definition gives a name to the proposition. It does not claim that the proposition is true. A proof is a separate declaration of the form `theorem kroneckerWeber : KroneckerWeber`, and the status of the node becomes proved only when such a declaration exists and uses no other assumption.

The definition makes four things possible. One can prove the proposition. One can prove its negation, if the statement is false. One can prove special cases of it, or derive it from other statements. And one can use it as a named hypothesis of another theorem, as in the following form.

```lean
theorem modularitySemistableQ_of_modularityEllipticQ (h : ModularityEllipticQ) :
    ModularitySemistableQ :=
  fun E _ _ => h E
```

This theorem, in the namespace `Langlands.Fidelity`, says that the full modularity theorem implies the semistable case. The proof applies the hypothesis `h` to the curve `E` and forgets the semistability. The point of the theorem is the check that the two statements fit together, which is the check F2 of the next section.

### Why not an axiom

Lean also has the command `axiom`, which adds a proposition to the theory without proof. An axiom cannot be tested, because the theory treats it as true from the moment it is added. If its negation is provable, the theory becomes inconsistent and proves every proposition, the false ones included. Lean then accepts each proof that uses it, and nothing in the proof shows the error. The project therefore never adds an axiom. The command `#print axioms` lists the axioms that a proof uses, and the continuous integration of the project checks that each proof uses only the three standard axioms of Lean: `propext`, `Quot.sound` and `Classical.choice`.

A conditional result is a theorem with the statement as a hypothesis, not an axiom. The Lean type of the theorem then shows the hypothesis, and the map records it. This is the status proved-mod of Chapter 1. For the same reason, a recent claim is never a hypothesis of another node until a person has checked it.

### The vocabulary

A statement needs definitions: the Weil group, the norm group of an extension, the $q$-expansion of a cusp form, the Weil-Deligne representations. Some of them are in Mathlib, the library of mathematics of Lean. The project writes the others in the file `Langlands/Statements/Basic.lean` and in the files next to it. A definition can be wrong in the same ways as a statement. The project tests the main definitions by checks of the same kind, and Chapter 3 lists the conventions that the definitions follow. When a statement needs a definition that does not exist yet, the node has the status unstated, and the map lists the missing definitions.
