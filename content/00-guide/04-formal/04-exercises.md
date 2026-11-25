---
title: Exercises and notes
nodes: []
sources: [Ser67]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Exercises

1. Let $P$ be a proposition. Explain why the declarations `def P' : Prop := P` and `axiom h : P` have different effects on the theory. Show that if `axiom h : P` is added and $\neg P$ is provable, then every proposition is provable.
2. Write the statement of local reciprocity without the uniqueness, with $\exists$ in place of $\exists!$. Show that the proof of the Proposition of the third section does not refute this weaker statement. Which check would find the weakness of this variant?
3. Let $r : K^\times \to W_K^{ab}$ be an unnormalized Artin map, and let $u$ be a continuous automorphism of $K^\times$. Find a condition on $u$ under which $r \circ u$ is again an unnormalized Artin map. Show that $x \mapsto x^{-1}$ satisfies it.
4. Consider the statement "for each local field $K$ there is a bijection between the set of characters of $K^\times$ of finite order and the set of characters of $G_K$ of finite order". Show that it is true for a trivial reason when both sets are countably infinite. Which property of the reciprocity map is lost?
5. Let $f = \sum_{n \ge 1} a_n q^n$ be a cusp form on $\Gamma_0(N)$, with $q = e^{2\pi i \tau}$. Write $f$ as a series in $q_N = e^{2\pi i \tau / N}$, and show that its coefficient of $q_N^m$ is $a_{m/N}$ if $N \mid m$ and 0 otherwise.
6. Use the dimension formula for $S_2(SL_2(\mathbb{Z}))$, or the fact that $S_k(SL_2(\mathbb{Z})) = 0$ for $k < 12$, to complete the proof that the formal-conjectures statement fails for $N = 1$.
7. Repair the formal-conjectures statement in two ways: by the $q$-expansion with period 1, and by a condition on the coefficients of $q_N^{Nn}$. Show that the two repairs give the same statement.
8. The Sato-Tate measure on $[0, \pi]$ is $\frac{2}{\pi} \sin^2 \theta \, d\theta$. Show that it gives the interval $[0, \pi/4]$ the mass $\frac14 - \frac{1}{2\pi}$. Explain why this computation and the Sato-Tate theorem for $X_0(11)$ refute the variant of the theorem with the uniform measure.

## Notes and history

The checks F1 to F7 are the rules of the project tamnd/langlands. Some of them follow common practice in the formalization of mathematics: the build of Mathlib checks that each file elaborates, and a review of a pull request to Mathlib is a form of F6. The check F3 found the first error of the third section. The work on the bridges, which tried to prove the formal-conjectures statement equivalent to the statement of the project, found the second one.

The statement of formal-conjectures is in the file `FormalConjectures/Wikipedia/ModularityConjecture.lean` of the repository google-deepmind/formal-conjectures. The project ports it at the commit `9097e2f90e66d2f6244209cb1c07f7120d17ec53`. The refutation is in the file `Langlands/Bridge/FormalConjectures.lean` of tamnd/langlands-lean.

Serre's chapter in Cassels and Fröhlich [Ser67] is the reference proof of local class field theory, and the source of the statement `Langlands.LocalReciprocityGL1`. Chapter 3 of this volume gives the conventions of the handbook, and it compares them with the conventions of other sources.
