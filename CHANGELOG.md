# Changelog

Each release has a section. The newest release is first.

## Unreleased

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
