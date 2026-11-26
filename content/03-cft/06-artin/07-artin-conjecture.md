---
title: Artin's conjecture
nodes: [LGEHB4MGJK, LGX6BXWH0J]
sources: [Del69, DS74, KW09, Kis09, Neu99]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Artin's conjecture

Brauer's theorem gives a meromorphic continuation of $L(s, \rho)$, but the integers $n_i$ in it can be negative. So the poles of the Hecke $L$-functions with $n_i > 0$ can survive, and the zeros of those with $n_i < 0$ can become poles. Artin conjectured in 1923 that no poles occur. This section states the conjecture, proves the cases that follow from the earlier sections, and describes what is known. The conjecture is open in general.

### The statement

**Conjecture 6.7.1 (Artin).** Let $L/F$ be a finite Galois extension of number fields, and let $\rho$ be an irreducible representation of $\mathrm{Gal}(L/F)$ that is not trivial. Then $L(s, \rho)$ extends to an entire function on $\mathbb{C}$.

Node: LGEHB4MGJK · Lean: `Langlands.ArtinConjecture`

For the statement and the known cases see also [Neu99], Chapter VII, Section 10. By additivity, the conjecture for all irreducible $\rho \ne \mathbf{1}$ is equivalent to the statement that $L(s, \rho)$ is entire for every representation $\rho$ that does not contain $\mathbf{1}$. The trivial representation must be excluded, because $L(s, \mathbf{1}) = \zeta_F(s)$ has a pole at $s = 1$. The statement is about $L(s, \rho)$, not about $\Lambda(s, \rho)$. The next proposition shows that the two forms are equivalent.

**Proposition 6.7.2 (the poles of $L$ and $\Lambda$).** Let $\rho$ be a representation with $\langle \rho, \mathbf{1} \rangle = 0$.
1. The function $\Lambda(s, \rho)$ is holomorphic on the half planes $\mathrm{Re}(s) > 1$ and $\mathrm{Re}(s) < 0$, and at $s = 0$ and $s = 1$.
2. The functions $L(s, \rho)$ and $\Lambda(s, \rho)$ have the same poles, with the same orders. All of them lie in the strip $0 \le \mathrm{Re}(s) \le 1$.

Lean: not stated yet

*Proof.* The function $\Gamma_\infty(s, \rho)$ is a product of the functions $\Gamma_\mathbb{R}(s)$, $\Gamma_\mathbb{R}(s + 1)$ and $\Gamma_\mathbb{C}(s)$. It has no zeros, and its poles lie at the integers $s \le 0$. For $\mathrm{Re}(s) > 1$ both factors of $\Lambda(s, \rho) = \Gamma_\infty(s, \rho) L(s, \rho)$ are holomorphic, by Theorem 6.2.2. The dual $\rho^\vee$ also satisfies $\langle \rho^\vee, \mathbf{1} \rangle = 0$, so $L(s, \rho^\vee)$ is holomorphic at $s = 1$ by Corollary 6.6.5. Hence $\Lambda(s, \rho^\vee)$ is holomorphic on $\mathrm{Re}(s) > 1$ and at $s = 1$. By Theorem 6.6.4, $\Lambda(s, \rho) = W(\rho) A(\rho)^{1/2 - s} \Lambda(1 - s, \rho^\vee)$, and the right side is holomorphic for $\mathrm{Re}(s) < 0$ and at $s = 0$. At $s = 1$ the function $\Gamma_\infty$ is holomorphic, and $L(s, \rho)$ is holomorphic by Corollary 6.6.5. This proves part 1. For part 2, $L(s, \rho) = \Lambda(s, \rho) / \Gamma_\infty(s, \rho)$, and $1/\Gamma_\infty$ is entire. So $L$ is holomorphic wherever $\Lambda$ is. At a point $s_0$ that is not an integer $\le 0$, the factor $\Gamma_\infty$ is holomorphic and not zero, so $L$ and $\Lambda$ have the same order there. At the integers $s_0 \le 0$ both functions are holomorphic, by part 1. $\square$

With the nonvanishing of Hecke $L$-functions on the line $\mathrm{Re}(s) = 1$, the same argument shows that the poles lie in the open strip $0 < \mathrm{Re}(s) < 1$. The proof uses the functional equation in an essential way. The fact that $\Gamma_\infty$ has no zeros only shows that every pole of $L$ is a pole of $\Lambda$. The converse needs part 1, because $\Gamma_\infty$ has poles.

### The monomial case

A representation is *monomial* if it is induced from a representation of dimension one of a subgroup. A finite group is an *M-group* if all of its irreducible representations are monomial.

**Corollary 6.7.3 (monomial representations).** Let $\rho$ be an irreducible representation of $G = \mathrm{Gal}(L/F)$ with $\rho \ne \mathbf{1}$. If $\rho$ is monomial, then $L(s, \rho)$ and $\Lambda(s, \rho)$ are entire. In particular Conjecture 6.7.1 holds when $G$ is an M-group, for example when $G$ is supersolvable, and so when $G$ is nilpotent or abelian.

Lean: not stated yet

*Proof.* Let $\rho = \mathrm{Ind}_H^G \psi$ with $\psi$ of dimension one. By Frobenius reciprocity $\langle \psi, \mathbf{1}_H \rangle = \langle \rho, \mathbf{1}_G \rangle = 0$, so $\psi \ne \mathbf{1}$. As in the proof of Theorem 6.6.4, $\psi$ is inflated from a nontrivial character $\psi'$ of an abelian extension $L'/M$, with $M = L^H$. By Theorem 6.3.3 and Proposition 6.4.5, $L(s, \rho) = L(s, \psi')$ and $\Lambda(s, \rho) = \Lambda(s, \psi')$. These are entire by Corollary 6.5.3. Supersolvable groups are M-groups, see Serre's *Linear representations of finite groups*, Chapter 8. $\square$

The group $S_3$ is supersolvable, so Corollary 6.7.3 covers Example 6.6.7 again. The smallest group that is not an M-group is $SL_2(\mathbb{F}_3)$, of order 24. It has no subgroup of index 2, so its irreducible representations of dimension 2 are not monomial. For such representations the methods of this chapter do not prove Conjecture 6.7.1.

### Reciprocity implies Artin's conjecture

Langlands conjectured that each irreducible $\rho$ of dimension $n$ corresponds to an automorphic representation of $GL_n$. Volume 4 develops the automorphic side. Here we use only the following facts about a cuspidal automorphic representation $\pi$ of $GL_n(\mathbb{A}_F)$. For almost all finite places $v$ it has a local factor $L(s, \pi_v) = \det(1 - A_v N(v)^{-s})^{-1}$, with $A_v \in GL_n(\mathbb{C})$ the Satake parameter. Let $S$ be a finite set of places that contains the archimedean places and the places where $\pi_v$ is ramified. The partial $L$-function $L^S(s, \pi) = \prod_{v \notin S} L(s, \pi_v)$ converges for $\mathrm{Re}(s)$ large. The contragredient $\pi^\vee$ is cuspidal, with Satake parameters $A_v^{-1}$.

**Conjecture 6.7.4 (strong Artin conjecture).** Let $\rho$ be an irreducible representation of $\mathrm{Gal}(L/F)$ of dimension $n$. There is a cuspidal automorphic representation $\pi$ of $GL_n(\mathbb{A}_F)$ such that $L(s, \pi_v) = L_v(s, \rho)$ for almost all finite places $v$.

Lean: not stated yet

For $n = 1$ this is Theorem 6.5.2, with $\pi = \omega_\chi$. At the places where both sides are unramified, the condition says that $A_v$ and $\rho(\mathrm{Frob}_v)$ are conjugate. In the geometric normalization of the local Langlands correspondence, Remark 6.1.6 shows that the expected relation at every place is $\mathrm{rec}(\pi_v) \cong \rho_v^\vee$, the dual of the restriction of $\rho$ to a decomposition group. The map node `Langlands.GlobalReciprocity` of Section 6.5 is the case $n = 1$.

**Theorem 6.7.5 (reciprocity implies Artin).** If Conjecture 6.7.4 holds for an irreducible $\rho \ne \mathbf{1}$, then $L(s, \rho)$ and $\Lambda(s, \rho)$ are entire.

Lean: not stated yet

*Proof.* If $n = 1$, this is Corollary 6.5.3. Let $n \ge 2$ and let $\pi$ be as in Conjecture 6.7.4. Godement and Jacquet proved in *Zeta functions of simple algebras* (Lecture Notes in Mathematics 260, 1972) that for cuspidal $\pi$ with $n \ge 2$ the function $L^S(s, \pi)$ extends to an entire function. Choose $S$ so large that it also contains the places where $\rho$ is ramified or where $L(s, \pi_v) \ne L_v(s, \rho)$. Then
$$L(s, \rho) = L^S(s, \pi) \prod_{v \in S \text{ finite}} L_v(s, \rho).$$
Each factor $L_v(s, \rho) = \det(1 - \rho(\mathrm{Frob}_w) N(v)^{-s} \mid V^{I_w})^{-1}$ has no zeros, and its poles lie on the line $\mathrm{Re}(s) = 0$, because the eigenvalues of $\rho(\mathrm{Frob}_w)$ are roots of unity. So $L(s, \rho)$ is holomorphic on $\mathrm{Re}(s) \ne 0$. The contragredient $\pi^\vee$ satisfies Conjecture 6.7.4 for $\rho^\vee$, since $A_v^{-1}$ is conjugate to $\rho^\vee(\mathrm{Frob}_v)$. So $L(s, \rho^\vee)$ is holomorphic on $\mathrm{Re}(s) = 1$, and so is $\Lambda(s, \rho^\vee)$. By the functional equation, $\Lambda(s, \rho)$ is holomorphic on $\mathrm{Re}(s) = 0$. By Proposition 6.7.2, part 2, the poles of $\Lambda(s, \rho)$ are those of $L(s, \rho)$, so $\Lambda(s, \rho)$ is holomorphic off the line $\mathrm{Re}(s) = 0$ too. So $\Lambda(s, \rho)$ is entire, and $L(s, \rho) = \Lambda(s, \rho) / \Gamma_\infty(s, \rho)$ is entire. $\square$

### Representations of dimension two

Let $\rho : \mathrm{Gal}(L/F) \to GL_2(\mathbb{C})$ be irreducible, and let $\bar\rho : \mathrm{Gal}(L/F) \to PGL_2(\mathbb{C})$ be its projective image. The finite subgroups of $PGL_2(\mathbb{C})$ are the cyclic groups, the dihedral groups, and the groups $A_4$, $S_4$ and $A_5$. If the image of $\bar\rho$ is cyclic, then $\rho$ is reducible. So an irreducible $\rho$ is of dihedral, tetrahedral, octahedral or icosahedral type. In the dihedral case $\rho$ is induced from a character of a subgroup of index 2, so Corollary 6.7.3 applies. The tetrahedral and octahedral cases have a solvable image, and $\rho$ need not be monomial. The representations of $SL_2(\mathbb{F}_3)$ of dimension 2 are tetrahedral.

**Theorem 6.7.6 (Langlands, Tunnell).** Let $F$ be a number field and let $\rho : \mathrm{Gal}(L/F) \to GL_2(\mathbb{C})$ be irreducible with solvable image. Then $\rho$ satisfies Conjecture 6.7.4. Hence $L(s, \rho)$ is entire.

Lean: not stated yet

Langlands proved the tetrahedral case in *Base change for GL(2)* (Annals of Mathematics Studies 96, 1980). His method is cyclic base change for $GL_2$ with the trace formula. He applies it to the extension of degree 3 that the quotient $A_4 \to \mathbb{Z}/3$ cuts out, where the restriction of $\rho$ becomes dihedral. Tunnell proved the octahedral case in 1981 (Bull. Amer. Math. Soc. 5). He uses the quotient $S_4 \to S_3$, base change to a quadratic extension, and the theorem of Gelbart and Jacquet on the symmetric square. This theorem of Langlands and Tunnell is the starting point of Wiles' proof of the modularity of semistable elliptic curves, because $PGL_2(\mathbb{F}_3) \cong S_4$ and $GL_2(\mathbb{F}_3)$ has a faithful representation of dimension 2 over $\mathbb{C}$ with octahedral projective image.

Over $\mathbb{Q}$ there is a finer result in terms of modular forms. Let $c$ be a complex conjugation. The representation $\rho$ is *odd* if $\det \rho(c) = -1$, and *even* if $\det \rho(c) = 1$. All complex conjugations are conjugate in $\mathrm{Gal}(L/\mathbb{Q})$, so the sign does not depend on $c$. For an odd $\rho$, $\rho(c)$ has the eigenvalues $1$ and $-1$, so $\Gamma_\infty(s, \rho) = \Gamma_\mathbb{C}(s)$. This is the gamma factor of a holomorphic modular form of weight 1.

**Theorem 6.7.7 (Khare, Wintenberger, Kisin).** Let $L/\mathbb{Q}$ be a finite Galois extension, and let $\rho : \mathrm{Gal}(L/\mathbb{Q}) \to GL_2(\mathbb{C})$ be irreducible and odd. Let $N$ be the positive generator of $\mathfrak{f}(\rho)$, and let $\varepsilon$ be the Dirichlet character that corresponds to $\det \rho$ by Example 6.5.4. Then there is a newform $f = \sum_{m \ge 1} a_m q^m$ of weight 1, level $N$ and character $\varepsilon$ with $L(s, \rho) = L(s, f) = \sum_{m \ge 1} a_m m^{-s}$. In particular $L(s, \rho)$ is entire.

Node: LGX6BXWH0J · Lean: `Langlands.ArtinOdd2Q`

The proof is the theorem of Khare and Wintenberger on Serre's modularity conjecture, *Serre's modularity conjecture (I)* [KW09] and its second part in the same volume, with Kisin's modularity lifting theorem for $p = 2$ [Kis09]. In the Lean project the weak form of Serre's conjecture is `Langlands.SerreModularityWeak`. Serre observed in 1987 (Duke Math. J. 54) that his conjecture implies Theorem 6.7.7. The argument runs as follows. The image of $\rho$ is finite, so $\rho$ is defined over the ring of integers $\mathcal{O}$ of a number field. For each prime $\lambda$ of $\mathcal{O}$, the reduction $\bar\rho_\lambda$ modulo $\lambda$ is odd, and it is irreducible for all but finitely many $\lambda$. By Serre's conjecture, $\bar\rho_\lambda$ comes from an eigenform modulo $\lambda$ of weight 1 and level $N$ if $\lambda \nmid N$ is large. For $p$ large, eigenforms of weight 1 modulo $p$ lift to characteristic 0. The space of forms of weight 1 and level $N$ has finite dimension. So one eigenform $f$ of characteristic 0 serves for infinitely many $\lambda$. Then $a_\ell(f) \equiv \mathrm{tr} \rho(\mathrm{Frob}_\ell)$ modulo infinitely many $\lambda$ for each $\ell \nmid N$, so the two numbers are equal. A comparison of the factors at the primes that divide $N$ completes the proof.

The converse is older.

**Theorem 6.7.8 (Deligne, Serre).** Let $f$ be a newform of weight 1, level $N$ and character $\varepsilon$. There is an irreducible odd representation $\rho_f : \mathrm{Gal}(\bar{\mathbb{Q}}/\mathbb{Q}) \to GL_2(\mathbb{C})$ with finite image, unramified outside $N$, such that $\mathrm{tr} \rho_f(\mathrm{Frob}_p) = a_p$ and $\det \rho_f(\mathrm{Frob}_p) = \varepsilon(p)$ for $p \nmid N$. Its Artin conductor is $N$, and $L(s, \rho_f) = L(s, f)$.

Lean: not stated yet

This is [DS74], Theorem 4.1, and the statement on the conductor is in [DS74], Section 4. The proof constructs $\rho_f$ as a limit of the $\ell$-adic representations attached to forms of higher weight by Deligne [Del69]. The reductions modulo $\ell$ of the representation have images of bounded order, by an estimate of the coefficients on average. So the image of $\rho_f$ is finite. Theorems 6.7.7 and 6.7.8 together give a bijection between the odd irreducible $\rho$ of dimension 2 over $\mathbb{Q}$, up to isomorphism, and the newforms of weight 1.

Before Khare and Wintenberger, the odd icosahedral case was known only in part. Buzzard and Taylor (1999), Buzzard, Dickinson, Shepherd-Barron and Taylor (2001) and Taylor (2003) proved it under conditions on $\rho$ at $2$, $3$ or $5$, with modularity lifting theorems and the icosahedral image of $SL_2(\mathbb{F}_5)$. Over totally real fields, the odd case of dimension 2 is now known in many cases through the work of Kassaei, Pilloni and Stroh, and Sasaki. The even icosahedral case over $\mathbb{Q}$ is open, and so is Conjecture 6.7.1 for most representations of dimension at least 3. For an even $\rho$ over $\mathbb{Q}$, $\Gamma_\infty(s, \rho)$ is $\Gamma_\mathbb{R}(s)^2$ or $\Gamma_\mathbb{R}(s + 1)^2$, and the expected $\pi$ corresponds to a Maass form of eigenvalue $1/4$. Such forms are not algebraic objects, and the methods of Khare and Wintenberger do not apply to them.

### The Lean statements

**Remark 6.7.9 (the Lean forms of Conjecture 6.7.1 and Theorem 6.7.7).** Both statements are in `Langlands/Statements/Galois.lean`, with the definitions of Remark 6.2.5. Neither is proved in the project.
1. `Langlands.ArtinConjecture` quantifies over a number field $K$, an intermediate field $L$ of `AlgebraicClosure K` that is finite and Galois over $K$, an integer $n$ and a homomorphism `ρ : Gal(L/K) →* GL (Fin n) ℂ` with `IsIrreducibleRep ρ` and `ρ ≠ 1`. It asserts that there is a function `F : ℂ → ℂ` with `Differentiable ℂ F` and `F s = artinLFunction ρ s` for $1 < \mathrm{Re}(s)$. A differentiable function on $\mathbb{C}$ is entire, and by the identity theorem it is unique. So `F` is the continuation of Conjecture 6.7.1. The condition `ρ ≠ 1` excludes only the trivial character, since an irreducible representation of dimension $n \ge 2$ is never trivial.
2. The Lean statement is about $L(s, \rho)$ and not about $\Lambda(s, \rho)$. The docstring of `ArtinConjecture` says that the archimedean factors have no zeros, so that the completed function has the same poles. That argument shows only that the poles of $L$ are poles of $\Lambda$. Proposition 6.7.2 gives the full equivalence, with the functional equation.
3. In `Langlands.ArtinOdd2Q` the base field is $\mathbb{Q}$. The condition of oddness is that $\det \rho(c) = -1$ for each $c$ with `IsComplexConjugationOf c`. This predicate says that there is a ring homomorphism `j : L →+* ℂ` with `j (c x) = conj (j x)` for all $x$. If $L$ is totally real, then $c = 1$ satisfies it, and $\det \rho(1) = 1$. So the hypothesis fails for every $\rho$ when $L$ is totally real, as it should, because such a $\rho$ is even. If $L$ is not totally real, every $c$ with this property is a complex conjugation in the sense of this section.
4. The conclusion of `ArtinOdd2Q` asserts that $L(s, \rho)$ has an entire continuation, and that there are $N > 0$, `χ : DirichletCharacter ℂ N` and `f : CuspForm (Gamma1 N) 1` with `IsNormalizedEigenformWithCharacter f χ`, such that `artinLFunction ρ s = LSeries (qCoeffGamma1 f) s` for $1 < \mathrm{Re}(s)$. The form is a normalized eigenform, not a newform, because Mathlib has no theory of oldforms yet. Two Dirichlet series that agree on a half plane have the same coefficients. So the $q$-expansion of `f` is that of the newform of Theorem 6.7.7, and `f` is this newform, viewed at a level that is a multiple of the conductor. The statement does not say that `χ` corresponds to $\det \rho$. This follows from the equality of the coefficients at $p$ and $p^2$ for $p \nmid N$, with the Hecke relation $a_{p^2} = a_p^2 - \chi(p)$.

**Example 6.7.10 (the pure cubic field, continued).** Let $\rho$ be the representation of dimension 2 of $\mathrm{Gal}(L/\mathbb{Q}) \cong S_3$, for $L = \mathbb{Q}(\sqrt[3]{2}, \sqrt{-3})$, from Example 6.3.5. Complex conjugation is a transposition, so $\det \rho(c) = -1$ and $\rho$ is odd. Its conductor is $108$ and $\det \rho$ is the sign character, which corresponds to $\chi_{-3}$. Theorem 6.7.7, which is classical here since $\rho$ is dihedral, gives a newform of weight 1, level 108 and character $\chi_{-3}$. It is
$$f(\tau) = \eta(6\tau) \eta(18\tau) = q \prod_{m \ge 1} (1 - q^{6m})(1 - q^{18m}), \qquad \eta(\tau) = q^{1/24} \prod_{m \ge 1} (1 - q^m).$$
So for $p \ne 2, 3$ the coefficient $a_p$ of $f$ is the number of solutions of $x^3 = 2$ in $\mathbb{F}_p$, minus 1. A computer check confirms this for all $p < 2000$. This is a reciprocity law for the cubic equation $x^3 = 2$ that no abelian extension of $\mathbb{Q}$ explains.
