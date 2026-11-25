---
title: The checks F1 to F7
nodes: []
sources: []
status: drafted
drafted_by: writer
reviewed_by: []
---
## The checks F1 to F7

A Lean statement is *faithful* if it means what the mathematics means. No program can decide this, because the mathematics is written in words. The project uses seven checks instead. Each check can find an error, and none of them proves that there is no error. The results of the checks are records in tamnd/langlands, and the site shows them.

### The seven checks

**F1. Elaboration.** The file builds with the pinned version of Lean and Mathlib. It contains no `sorry`, no `axiom` and no `opaque`. The command `#print axioms` shows at most the three standard axioms for each statement. The continuous integration runs this check.

**F2. Positive instances.** The statement implies known special cases, or a known case of it is proved from the definitions. For example, the statement of local reciprocity implies finite abelian local reciprocity (Lean: `Langlands.Fidelity.finiteAbelian_of_localReciprocityGL1`). The statement of global reciprocity holds for the trivial extension (Lean: `Langlands.Fidelity.isArtinMap_bot`). The full modularity statement implies the semistable one, and the Sato-Tate measure has total mass 1. A statement that fails a known case is wrong.

**F3. Negative instances.** A wrong variant of the statement is false or trivial. For example, the variant of local reciprocity without the condition on the uniformizer loses the uniqueness (next section). The variant of the Sato-Tate theorem with the uniform distribution of the angles is false for the curve $X_0(11)$: the Sato-Tate measure gives $[0, \pi/4]$ the mass $\frac14 - \frac1{2\pi}$, and the uniform measure gives it $\frac14$ (Lean: `Langlands.Fidelity.not_satoTateUniform`). If a wrong variant were also true, the statement would not see the difference between the right and the wrong mathematics.

**F4. Triviality attack.** A strong automatic prover tries to prove the statement in a trivial way, with a fixed budget. The usual ways are an argument by cardinality, an empty type, a quirk of the universes, and a topology that makes every set open. A success of the prover is a failure of the check.

**F5. Round trip.** An independent model translates the Lean statement into English without its documentation. A person compares the translation with the documentation and with the source paper.

**F6. Human review.** Two number theorists sign that the Lean statement means its documentation. Their names and the dates go into the records.

**F7. Pinning.** The hash of each statement file is in a manifest. A tool compares each proof with the pinned statement, so that a proof cannot change the statement that it proves.

### What the checks are for

A statement of a known theorem counts as done for the first goal of the project after F1 to F5. A statement of an open conjecture needs all seven checks before any proof of it is announced, and its two reviewers must come from two different research groups. After F6 the statement is frozen. A change after F6 starts the checks again.

The main risks that the checks look for are in the table.

| Risk | What goes wrong | Main check |
|---|---|---|
| a bijection by cardinality | a correspondence that loses a characterizing property is true for a trivial reason | F3, F4 |
| the topology of the Weil group | with the topology of a subspace of $G_K$, the group $W_K^{ab}$ is not isomorphic to $K^\times$ as a topological group | F2, F3 |
| the normalization | arithmetic and geometric Frobenius differ by an inverse | F3 |
| smooth and admissible | a definition with admissibility agrees with one without it only after a theorem of Jacquet and Bernstein | F2 |
| automorphic forms | classical, adelic, $L^2$ and $K$-finite definitions differ | F2 |
| $\varepsilon$-factors | the factor depends on the additive character and the Haar measure | F2, F3 |
| Satake parameters | unitary and arithmetic parameters differ by a power of $q$ | F2 |
| the choice of $\iota$ | a statement can depend on $\iota : \bar{\mathbb{Q}}_\ell \to \mathbb{C}$ without saying so | F5 |
| universes | a statement over all universes is proved for one universe only | F1, F4 |

The file `records/fidelity.json` of tamnd/langlands holds the result of each check for each statement. A tool writes it, and the site shows it. The handbook does not copy these results by hand, because they change with each run of the checks.
