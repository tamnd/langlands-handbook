# Changelog

Each release has a section. The newest release is first.

## Unreleased

### Added

- Backfill the pinned L-group, the L-group of U(n), the factors of pairs, LocalLanglandsGLFull and its fidelity checks (Sections 2.5.4 and 6.3.1).

- Volume 2, Section 3.6: add Chevalley's construction of the adjoint group (Chevalley basis, divided powers, root, Weyl and torus elements, the examples sl2 and A2, Chevalley's theorem) with the Lean status and Exercises 12 to 14.

## v0.1.26 (2026-11-27)

### Added

- Volume 4, Section 2.5: add Fontaine's period rings A_cris, B_cris and B_st with t and the Kummer cocycle, and the Breuil-Mezard side (Jordan-Hölder multiplicities, Brauer-Nesbitt for lattices, inertial types, Henniart types, σ(λ,τ)), with the Lean status and Exercises 13 to 16.

## v0.1.25 (2026-11-27)

### Added

- Section 5.5 proves Hecke's theorem for all Hecke characters, and Section 4.2.5 adds framed deformation rings.

- Section 5.5 now says that each Hecke character with one shift is proved in Lean.

## v0.1.24 (2026-11-27)

### Added

- Section 5.5 gives the Lean status after the proof for any signs at the complex places.

- Volume 3 Sections 5.2 and 5.5 are checked, with fixes to Lemma 5.2.25, the Lean status remarks and Exercise 21.

## v0.1.23 (2026-11-27)

### Added

- Section 5.2 of Volume 3 now follows the Lean proof of the local functional equation for a ramified character and each Schwartz-Bruhat function.

- Section 5.5 of Volume 3 now follows the Lean proof of Hecke's functional equation for imaginary quadratic fields, with the Gauss sums and the weighted theta series.

- Section 1.5 of Volume 6 now follows the Lean proofs of the irreducibility criterion, Jacquet's lemma and the classification for GL(2).

- Volume 6, Section 1.5 and the Chapter 1 exercises are checked. The Steinberg coefficient in Proposition 1.5.4 is corrected.

- Volume 0 and Volume 2 name the Lean shapes of the local Langlands conjecture and of functoriality, and Volume 0 names `LocalLanglandsGL`.

## v0.1.22 (2026-11-26)

### Added

- Volume 6, Section 1.5: an elementary proof of the irreducibility criterion that follows the Lean proof, and Exercise 21.

- A checking pass over the new ray class text of Volume 3, Section 5.5, with the Lean remarks for RayClassQuadratic.lean and RayClassFE.lean.

- Volume 3, Section 5.5: Hecke characters of ray class type, the ray class group and the functional equation for ramified characters, with Exercises 19 to 21.

## v0.1.21 (2026-11-26)

### Added

- A checking pass over the new text of Volume 6, Section 3.2, with a correction to Exercise 14 and the regularity hypothesis of the Lean theorems.

- A checking pass over the new text of Volume 6, Chapter 1, with the Lean lines for JacquetPrincipal.lean and a fix to the numbering of Section 1.3.

- Volume 6, Section 3.2: Tate's local computation of the zeta integral and the local Langlands correspondence for GL(1) with the L-factors, with Exercises 13 and 14.

- Volume 6, Chapter 1: the Bruhat decomposition of GL(2), Jacquet's lemma, the exactness of the Jacquet functor and the big cell filtration of the principal series, with Exercises 18 to 20.

## v0.1.20 (2026-11-26)

### Added

- A checking pass over Volume 6, Chapter 2. All six section files are at status checked, with corrections to Example 2.1.14, Lemma 2.2.2, Theorem 2.3.4 and Proposition 2.4.3.

- A checking pass over Volume 6, Chapter 3. All seven section files are at status checked, with a correction to the history after Theorem 3.1.4 and to two Lean lines of Section 3.2.

## v0.1.19 (2026-11-26)

### Added

- A checking pass over Volume 6, Chapter 1. All eight section files are at status checked, with corrections to Propositions 1.2.2, Theorems 1.4.5, 1.4.6 and 1.5.1, Jacquet's lemma and Exercises 4, 10 and 16.

- Volume 6, Section 3.2: the subsection on the case n = 1 in full, items 3.2.9 to 3.2.15, and Exercise 12 of Chapter 3. It follows Langlands/Local/GL1.lean.

- Volume 6, Chapter 1: the Iwasawa decomposition for GL2, a new proof of Proposition 1.3.4, Exercise 17 and Lean lines from Langlands/Smooth/PrincipalSeries.lean.

## v0.1.18 (2026-11-26)

### Added

- A checking pass over Volume 3, Section 5.2, items 5.2.13 to 5.2.23, and Exercises 16 to 18 of Chapter 5. Both files are at status checked again.

- Volume 3, Section 5.2: the subsection on ramified places and finite Gauss sums, items 5.2.13 to 5.2.23, and Exercises 16 to 18 of Chapter 5. It follows Langlands/Tate/LocalRamified.lean.

- Volume 6, Chapter 1: Lean lines for smooth vectors, admissibility, induction, Frobenius reciprocity and the Jacquet module, from Langlands/Smooth/Induction.lean, and six corrections.

## v0.1.17 (2026-11-26)

### Added

- Volume 6, Chapter 3, The local Langlands correspondence. The chapter covers the statement for GL_n, the cases n = 1 and n = 2, the L-packets of SL_2, the local Jacquet-Langlands correspondence and the correspondence for GSp_4, with 11 exercises.

- Volume 6, Chapter 2, Weil-Deligne representations. The chapter covers the Weil group, Weil-Deligne representations, the monodromy theorem of Grothendieck, the local factors of Langlands and Deligne, and the L-factor of Godement and Jacquet, with 10 exercises.

- Volume 3, Section 5.5: the subsection on twists by a power of the norm, items 5.5.36 to 5.5.44. Volume 2, Chapter 5: the Lean lines for the results of Langlands/Groups/RootDatum.lean, and Remark 5.4.8.

## v0.1.16 (2026-11-26)

### Added

- Volume 2, Chapter 5, The dual group and the L-group. The chapter covers the dual root datum, the dual group, the dual groups of the classical groups, the L-group of a quasi-split group, the Satake isomorphism and L-parameters, with 11 exercises.

- Volume 2, Chapter 4, Representations of reductive groups. The chapter covers weights, the theorem of the highest weight, the Weyl character formula, the representations of SL_2 and GL_n, compact groups and the theorem of Peter and Weyl, and compact forms, with 12 exercises.

- Volume 3, Section 5.5: the subsection on Hecke characters of class group type, items 5.5.25 to 5.5.35, with the example of Q(sqrt(-5)) and Exercises 14 and 15 of Chapter 5. It follows Langlands/Tate/HeckeUnramified.lean.

- Volume 2, Chapter 2, Lie algebras and root systems. The chapter covers the Lie algebra of an algebraic group, solvable, nilpotent and semisimple Lie algebras, the representations of sl_2, the root space decomposition, root systems and the Weyl group, the Cartan matrix and the classification, and the theorem of the highest weight, with 11 exercises.

- Volume 2, Chapter 3, Reductive groups. The chapter covers reductive and semisimple groups, maximal tori and roots, root data, Borel subgroups and the Weyl group, the Bruhat decomposition, the isomorphism and existence theorems, the root data of the classical groups, and forms and quasi-split groups, with 11 exercises.

## v0.1.15 (2026-11-26)

### Added

- Volume 2, Algebraic groups and their duals, with its introduction and Chapter 1, Linear algebraic groups. The chapter has seven sections: affine groups and Hopf algebras, subgroups and quotients, the Jordan decomposition, diagonalizable groups and tori, unipotent and solvable groups, Borel subgroups, and the exercises with notes.

## v0.1.14 (2026-11-26)

### Changed

- Git ignores the folder `solutions/`. The solutions of the exercises are private (spec 11.3), so they stay out of the public repository.
- Volume 3, Chapters 1 to 4 have the status `checked`. The second pass fixed the proof of Theorem 1.1.3, the topology of the Weil group in Section 1.3, some citations of [Ser79], [Ser67] and [Tat79], and the notes on the Lean status of Theorems 2.3.3, 4.2.3, 4.5.2 and 4.5.4.
- Volume 3, Chapter 5 has the status `checked`. The second pass fixed a sign in the proof of Lemma 5.2.1, two statements in the Notes of Section 5.6 and the source of `unitThetaFEPair` in Remark 5.3.37.

## v0.1.13 (2026-11-26)

### Added

- Volume 3, Section 7.9: Exercise 13 on norm limitation for an extension that need not be Galois.

### Changed

- Volume 3, Chapter 7 has the status `checked`. The second pass fixed citations, cross-references, a sign in the remark after Theorem 7.2.5, the form of Neukirch's axioms in Section 7.3 and the uniqueness proof in Section 7.4.
- Volume 3, Chapter 6 has the status `checked`. The second pass fixed Remarks 6.2.5 and 6.7.9 to match the Lean statements, and Exercises 1 and 3 of Section 6.8.

## v0.1.12 (2026-11-26)

### Added

- Volume 3, Chapter 5, Section 5: a new subsection on class group characters in Lean, with Definition 5.5.17 (class group characters), Lemma 5.5.18 (the values of a class group character), Proposition 5.5.19 (the Dirichlet series), Theorem 5.5.20 (the functional equation), Theorem 5.5.21 (Hecke's theorem for class group characters), Remark 5.5.22 on the root number, Remark 5.5.23 on the link with Hecke characters and Remark 5.5.24 on the Lean proof in `Langlands/Tate/ClassCharacter.lean`.

### Changed

- Remark 5.5.16 now refers to the new subsection on class group characters.
- Remark 5.3.35 now refers to Theorem 5.5.10, not Theorem 5.5.9.

## v0.1.11 (2026-11-26)

### Added

- Volume 3, Chapter 5, Section 5: a new subsection on the characters |x|^s_0 in Lean, with Lemma 5.5.12 (the norm of a local idele), Lemma 5.5.13 (the data of |x|^s_0), Theorem 5.5.14 (Hecke's theorem for |x|^s_0), Remark 5.5.15 on the root number and Remark 5.5.16 on the Lean proof in `Langlands/Tate/HeckeNormPower.lean`.

### Changed

- Remarks 5.5.4 and 5.5.11 now refer to Theorem 5.5.14.

## v0.1.10 (2026-11-26)

### Added

- Volume 3, Chapter 5, Section 3: a new subsection on the poles of the function xi_F, with Proposition 5.3.36 (simple poles at 0 and 1 and their residues), the analytic class number formula by the methods of Hecke, and Remark 5.3.37 on the Lean proof in `Langlands/Tate/HeckeTrivial.lean`.
- Volume 3, Chapter 5, Section 5: a new subsection on the trivial character in Lean, with Lemma 5.5.8 (the data of the trivial character), Proposition 5.5.9 (the Euler product of the Dedekind zeta function), Theorem 5.5.10 (Hecke's theorem for the trivial character) and Remark 5.5.11 on the Lean proof.

### Changed

- Volume 3, Chapter 5: Corollary 5.4.8, Remark 5.3.35 and Remark 5.5.4 now give the new Lean theorems.

## v0.1.9 (2026-11-26)

### Added

- Volume 3, Chapter 5, Section 3: a new subsection on the functional equation of the Dedekind zeta function of each number field, with Lemma 5.3.33 (the function of a fractional ideal), Theorem 5.3.34 (the functional equation) and Remark 5.3.35 on the Lean proof in `Langlands/Tate/DedekindFE.lean`.

### Changed

- Remark 5.3.13, Remark 5.3.32 and Corollary 5.4.8 now give the Lean names of the class sum and of the functional equation, which are proved in `Langlands/Tate/UnitClass.lean` and `Langlands/Tate/DedekindFE.lean`.

## v0.1.8 (2026-11-26)

### Added

- Volume 3, Chapter 5, Section 3: a new subsection on the unfolding of the unit average, with Lemma 5.3.29 (the Mellin transform of one orbit of the units), Proposition 5.3.30 (the unfolding), Corollary 5.3.31 (the Mellin transform as a Dirichlet series) and Remark 5.3.32 on the Lean proof in `Langlands/Tate/UnitMellin.lean` and `Langlands/Tate/UnitUnfold.lean`. Remark 5.3.13 and Remark 5.3.28 now refer to the new subsection.

## v0.1.7 (2026-11-26)

### Added

- Volume 3, Chapter 5, Section 3: a new subsection on the theta function averaged over the units, with Definition 5.3.26, Proposition 5.3.27 (the transformation formula, the bounds and the continuity) and Remark 5.3.28 on the Lean proof in `Langlands/Tate/UnitTheta.lean`. Remark 5.3.13 now refers to the new subsection.

## v0.1.6 (2026-11-26)

### Added

- Volume 3, Chapter 5, Section 3: Corollary 5.3.23, the continuation, the functional equation and the residue of the Dedekind zeta function of an imaginary quadratic field, with the example Q(sqrt(-5)). Theorem 5.3.22 part (2) and Corollary 5.3.23 parts (1) and (2) now have Lean names from `Langlands/Tate/QuadraticDedekind.lean`. Remark 5.3.25 describes the Lean proof. The two remarks after the corollary are now Remark 5.3.24 and Remark 5.3.25.

## v0.1.5 (2026-11-26)

### Added

- Volume 3, Chapter 5, Section 3: the zeta function of a fractional ideal and its functional equation with the dual ideal (Proposition 5.3.20), the class invariance for an imaginary quadratic field by the identity theorem (Lemma 5.3.21), and the class zeta function of an imaginary quadratic field with its functional equation and its relation to the Dedekind zeta function (Theorem 5.3.22). A remark derives the residue of the Dedekind zeta function from the residues of the terms. Exercise 13 treats Q(sqrt(-5)). The Lean names are from langlands-lean at the merge of the imaginary quadratic file.

## v0.1.4 (2026-11-26)

### Added

- Volume 3, Chapter 5, Section 3: the Epstein zeta function of a lattice, its continuation, its residue and its functional equation with the dual lattice, with the proof by the theta formula and the Mellin transform. Two examples derive the functional equations of the Riemann zeta function and of the Dedekind zeta function of Q(i). A remark explains why this method works only for Q and the imaginary quadratic fields. Exercise 12 treats Q(sqrt(-2)) and Q(sqrt(2)). The Lean names are from the export of langlands-lean at d9630f7.

## v0.1.3 (2026-11-26)

### Added

- Volume 7, "L-functions, converse theorems and functoriality for GL(n)", Chapter 1: the group GL(n) over the adeles, automorphic forms and cusp forms, Hecke operators and the Satake isomorphism, the cuspidal spectrum, Whittaker models and multiplicity one, the standard L-function, and algebraic automorphic representations, with exercises and the notes. Each Lean name that the chapter cites is in the export of langlands-lean at 9a88d56.
- Volume 6, "Representations of p-adic groups and the local Langlands correspondence", Chapter 1, "Smooth representations": smooth and admissible representations, the Hecke algebra, parabolic induction and Jacquet modules, supercuspidal representations, the representations of GL(2), the classification of Bernstein and Zelevinsky in outline, and Whittaker models, with exercises and the notes. Each Lean definition that the chapter uses has its name.
- Volume 3, Chapter 7, "Global class field theory": ideles in extensions and the ray class groups, the global norm residue map and the reciprocity law, the two inequalities and the abstract class field theory of Neukirch with the plan of the Lean proof, norm limitation and the existence theorem, the theorem of Kronecker and Weber, ray class fields and conductors, the Hilbert class field and the principal ideal theorem, Hecke characters of finite order as Galois characters, and the global Weil group, with twelve exercises and the notes.
- Volume 3, Chapter 5: Poisson summation on a lattice and the theta transformation formula, with their Lean names, and a remark on the Lean form of the local functional equation and its limits.

### Changed

- Volume 3, Chapter 5: Corollary 5.3.10 has its Lean name, and two new remarks give the Lean form of the theta formula of a number field and the Hecke integral, with the steps that are still missing for the functional equation of the Dedekind zeta function.
- Volume 3, Chapter 5: the local functional equations at the finite, real and complex places have their Lean names.
- Volume 3, Chapter 1: the definitions and theorems have numbers.

## v0.1.2 (2026-11-26)

### Added

- Volume 3, Chapter 6, "Artin L-functions": the local factors with the inertia invariants and the arithmetic Frobenius, the Euler product and its convergence, additivity, inflation and induction, the Artin conductor and the gamma factors, the abelian case through global reciprocity, the induction theorems of Artin and Brauer with the meromorphic continuation and the functional equation, the theorem of Aramata and Brauer, and Artin's conjecture with the theorems of Langlands and Tunnell, of Khare, Wintenberger and Kisin, and of Deligne and Serre, with eleven exercises and the notes.
- Volume 4, "Modular forms and elliptic curves", Chapters 1 and 2: Chapter 1 on modular forms and Hecke operators (the upper half-plane, modular forms and cusp forms, dimensions, the Petersson inner product, Hecke operators and their adjoints), and Chapter 2 on eigenforms, L-functions and Galois representations (normalized eigenforms and newforms, the Euler product and the functional equation, modularity of elliptic curves, the Ramanujan-Petersson and Sato-Tate theorems, Eichler-Shimura and Deligne, Serre's conjecture and the Artin conjecture for odd representations, and Maass forms with the conjectures of Selberg and Ramanujan). Each chapter has exercises and notes, and each statement on the map has its node and its Lean name.

## v0.1.1 (2026-11-25)

### Added

- Volume 3, Chapter 5, "Tate's thesis": additive characters and self-dual measures, the local zeta integrals and the local functional equation, Poisson summation and the Riemann-Roch theorem of Tate, the global zeta integral, and Hecke's theorem for the completed L-function of a Hecke character, with eleven exercises and the notes.
- Volume 1, "Number fields, local fields and adeles": Chapter 1 on number fields (integers, ideals, the geometry of numbers, primes, cyclotomic and quadratic fields), Chapter 2 on local fields (absolute values, completions, the structure of local fields, extensions, ramification, the different), and Chapter 3 on adeles (restricted products, adeles, Haar measures, ideles, the compactness of the idele classes of norm one). Each chapter has exercises and notes. The volume follows Neukirch and Chapter II of Cassels and Frohlich.
- Volume 3, Chapter 2, "Local class field theory": the statement of local reciprocity, the unramified case, the form with the Weil group, functoriality, examples, eleven exercises and the notes.
- Volume 3, Chapter 3, "Lubin-Tate theory": formal groups, Lubin-Tate groups, the torsion points, the reciprocity map of Lubin-Tate, the main theorems, ten exercises and the notes.
- Volume 3, Chapter 4, "Characters of the Weil group": characters, the correspondence for GL(1), local factors, twists, tori, ten exercises and the notes.

### Fixed

- Volume 3, Chapter 3: the reference to the exercises on $F(X, 0) = X$ and on $i(X)$ had the wrong order.
- Volume 3, Chapter 2, Exercise 7: the composite of the transfer with the map $j$ now has the correct order, $j \circ \mathrm{Ver}$.

## v0.1.0 (2026-11-25)

### Added

- The draft of Volume 0, "Guide", in five chapters: how to read the handbook, the program in one chapter, notation and normalizations, what it means to formalize a statement, and the map and the reading list, with exercises and notes.

## v0.0.1 (2026-11-25)

### Added

- The builder `lhb`, a copy of `shb` of the singularity handbook, with the names and the volumes of the Langlands program.
- Volume 3, Chapter 1, "The Weil group of a local field": local fields and unramified extensions, the Frobenius and the inertia group, the Weil group and its topology, the abelianization, eight exercises and the notes.
