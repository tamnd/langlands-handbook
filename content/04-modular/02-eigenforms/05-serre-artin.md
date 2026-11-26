---
title: Serre's conjecture and the Artin conjecture
nodes: [LGKH3WKEVV, LGEHB4MGJK, LGX6BXWH0J]
sources: [KW09, Kis09, DS74, Neu99]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Serre's conjecture and the Artin conjecture

Section 2.4 goes from eigenforms to Galois representations. This section states two theorems that go in the other direction. Serre's conjecture, proved by Khare and Wintenberger, says that every odd irreducible representation of $G_\mathbb{Q}$ of dimension 2 over $\bar{\mathbb{F}}_p$ comes from an eigenform. The Artin conjecture for odd representations of dimension 2 over $\mathbb{C}$ follows, and it identifies their Artin $L$-functions with $L$-functions of forms of weight 1.

### Residual representations

**Definition 2.5.1 (odd and irreducible representations).** Let $F$ be a field and $\rho : G_\mathbb{Q} \to GL_2(F)$ a homomorphism. An element $c \in G_\mathbb{Q}$ is a *complex conjugation* if there is an embedding $j : \bar{\mathbb{Q}} \to \mathbb{C}$ with $j(c(x)) = \overline{j(x)}$ for all $x$. The representation $\rho$ is *odd* if $\det\rho(c) = -1$ for each complex conjugation $c$. It is *irreducible* if $F^2$ has no line that is stable under $\rho(G_\mathbb{Q})$.

Lean: `Langlands.IsOddRep`, `Langlands.IsIrreducibleRep`, `Langlands.IsComplexConjugation`

The complex conjugations form one conjugacy class of elements of order 2 in $G_\mathbb{Q}$, so $\det\rho(c)$ does not depend on $c$, and $\det\rho(c) = \pm 1$. In characteristic 2, $-1 = 1$, so every representation over a field of characteristic 2 is odd. For $F = \bar{\mathbb{F}}_p$, which is algebraically closed, irreducibility is absolute irreducibility. A homomorphism $\bar\rho : G_\mathbb{Q} \to GL_2(\bar{\mathbb{F}}_p)$ is continuous for the discrete topology on $\bar{\mathbb{F}}_p$ if and only if its kernel is open, that is, if it factors through $\mathrm{Gal}(L/\mathbb{Q})$ for a finite Galois extension $L$. Then $\bar\rho$ is unramified outside the primes that ramify in $L$.

**Proposition 2.5.2 (reduction of $\rho_{f,\iota}$).** Let $\rho : G_\mathbb{Q} \to GL_2(E)$ be continuous, where $E$ is a finite extension of $\mathbb{Q}_\ell$ with ring of integers $\mathcal{O}$ and residue field $k$.
1. There is an $\mathcal{O}$-lattice $\Lambda \subset E^2$ stable under $G_\mathbb{Q}$. The reduction $\bar\rho_\Lambda : G_\mathbb{Q} \to GL(\Lambda/\lambda\Lambda) \cong GL_2(k)$ is continuous, and its semisimplification does not depend on $\Lambda$.
2. If $\rho = \rho_{f,\iota}$ for a normalized eigenform $f \in S_k(N, \chi)$, then $\mathrm{tr}\,\bar\rho(\mathrm{Frob}_p)$ and $\det\bar\rho(\mathrm{Frob}_p)$ are the reductions of $\iota^{-1}(a_p(f))$ and $\iota^{-1}(\chi(p))p^{k-1}$ for $p \nmid N\ell$, and $\bar\rho$ is odd.

Lean: not stated yet

*Proof.* The group $G_\mathbb{Q}$ is compact, so its image $\rho(G_\mathbb{Q})$ is a compact subgroup of $GL_2(E)$. The lattice $\Lambda_0 = \mathcal{O}^2$ has an open stabilizer, so its orbit under the image is finite, and the sum $\Lambda$ of the lattices in the orbit is a stable lattice. Two stable lattices give reductions with the same characteristic polynomials at each element, and by the theorem of Brauer and Nesbitt they have the same semisimplification. Part 2 follows from Theorem 2.4.4 and Proposition 2.4.6, since the traces and determinants reduce, and $\det\bar\rho(c) = -1$ in $k$. $\square$

For $f = \Delta$ and $\ell = 691$, the congruence $\tau(p) \equiv 1 + p^{11} \bmod 691$ of Exercise 6 of Chapter 1 shows that $\bar\rho_{\Delta}$ has the same traces at Frobenius as $1 \oplus \bar\varepsilon_{691}^{11}$. So its semisimplification is reducible. For the curve $E$ of Example 2.2.15 and $\ell = 5$, the rational point of order 5 spans a line in $E[5]$ fixed by $G_\mathbb{Q}$, so $\bar\rho_{E,5}$ is reducible, and its semisimplification is $1 \oplus \bar\varepsilon_5$. This gives $a_p(f_{11}) \equiv 1 + p \bmod 5$ for $p \ne 11$, as in $a_2 = -2 \equiv 3$, $a_3 = -1 \equiv 4$ and $a_{13} = 4 \equiv 14$.

### Serre's conjecture

**Theorem 2.5.3 (Serre's conjecture, Khare and Wintenberger).** Let $p$ be a prime and $\bar\rho : G_\mathbb{Q} \to GL_2(\bar{\mathbb{F}}_p)$ a continuous representation that is irreducible and odd. There are $N \ge 1$, $k \ge 2$, a Dirichlet character $\chi$ modulo $N$, a normalized eigenform $f \in S_k(N, \chi)$ and a ring homomorphism $\theta : \mathbb{Z}[a_n(f), \chi] \to \bar{\mathbb{F}}_p$ such that for all primes $q \nmid Np$,
$$\mathrm{tr}\,\bar\rho(\mathrm{Frob}_q) = \theta(a_q(f)), \qquad \det\bar\rho(\mathrm{Frob}_q) = \theta(\chi(q))\,q^{k-1}.$$

Node: LGKH3WKEVV · Lean: `Langlands.SerreModularityWeak`

*Outline of the proof.* The proof is in [KW09, Parts I and II]. Khare and Wintenberger lift $\bar\rho$ to a compatible system of $\ell$-adic representations, with the potential modularity theorems of Taylor. They then change the prime and reduce the conductor and the weight step by step, as in an idea of Dieulefait: at each step a member of the compatible system at another prime has a residual representation of smaller conductor or weight, and the modularity lifting theorems of Wiles, Taylor-Wiles and Kisin carry modularity from one residual representation to the next. The induction ends at representations of small conductor and weight, where discriminant bounds, as in the theorems of Tate for $p = 2$ and Serre for $p = 3$, show that no irreducible odd $\bar\rho$ exists. The case $p = 2$ uses the 2-adic modularity lifting theorem of [Kis09]. $\square$

Oddness is necessary for $p$ odd: by Proposition 2.5.2, if $\bar\rho$ has the traces and determinants of a form, then $\det\bar\rho = \bar\chi\bar\varepsilon_p^{k-1}$ by Chebotarev, and this character is odd.

**Remark 2.5.4 (the Lean form and the strong form).** The statement `Langlands.SerreModularityWeak` takes a prime $p$ and a homomorphism $\rho$ from $G_\mathbb{Q}$ to $GL_2$ of `AlgebraicClosure (ZMod p)` with an open kernel, with `IsIrreducibleRep ρ` and `IsOddRep ρ`. It asks for $N > 0$, $k \ge 2$, a character $\chi$, a cusp form $f$ on $\Gamma_1(N)$ with `IsNormalizedEigenformWithCharacter f χ`, and a ring homomorphism $\theta$ from `Langlands.coeffRing f χ`, the subring of $\mathbb{C}$ generated by the coefficients of $f$ and the values of $\chi$, such that for each prime $q \nmid Np$ and each $\sigma$ with `IsFrobeniusAt q σ` the trace and the determinant of $\rho(\sigma)$ are $\theta(a_q(f))$ and $\theta(\chi(q))q^{k-1}$. This is the weak form of Serre's conjecture. It does not state the strong form, in which Serre gives a recipe for the minimal level $N(\bar\rho)$, the Artin conductor of $\bar\rho$ away from $p$, and for the minimal weight $k(\bar\rho)$, which depends only on the restriction of $\bar\rho$ to an inertia group at $p$. The weak form implies the strong form by the work of Ribet, Edixhoven, Carayol, Diamond and others on the lowering of the level and the weight. Khare and Wintenberger proved the strong form. For $p = 2$ the hypothesis `IsOddRep ρ` holds for every $\rho$, as noted after Definition 2.5.1, and the theorem is true without it, because every representation in characteristic 2 is odd. For odd $p$ the hypothesis cannot be removed, by the remark after Theorem 2.5.3.

**Example 2.5.5 (torsion of elliptic curves).** Let $E$ be an elliptic curve over $\mathbb{Q}$ and $p$ a prime. The action of $G_\mathbb{Q}$ on $E[p] \cong \mathbb{F}_p^2$ gives $\bar\rho_{E,p} : G_\mathbb{Q} \to GL_2(\mathbb{F}_p)$, unramified outside $pN_E$. The Weil pairing gives $\det\bar\rho_{E,p} = \bar\varepsilon_p$, so $\bar\rho_{E,p}$ is odd. If $E$ has no complex multiplication, Serre proved that $\bar\rho_{E,p}$ is surjective, so irreducible, for all $p$ outside a finite set. Theorem 2.5.3 then gives a form whose coefficients are congruent to $a_q(E)$ modulo a prime over $p$. This is weaker than Theorem 2.2.11, which gives a form of weight 2 with exactly these coefficients. Serre observed that the strong form of his conjecture for the representations $\bar\rho_{E,p}$ of a curve $y^2 = x(x - a^p)(x + b^p)$ attached to a solution of $a^p + b^p = c^p$ would give a form of weight 2 and level 2, and $S_2(\Gamma_0(2)) = 0$. Ribet proved the level lowering needed for this, so Theorem 2.2.10 implies Fermat's last theorem.

### Artin L-functions

Let $K$ be a number field, $L/K$ a finite Galois extension and $\rho : \mathrm{Gal}(L/K) \to GL_n(\mathbb{C})$ a representation on $V = \mathbb{C}^n$. For a prime $v$ of $K$ let $P$ be a prime of $L$ over $v$, with inertia group $I_P$, and let $\sigma_P$ be an arithmetic Frobenius at $P$. The action of $\sigma_P$ on the invariants $V^{I_P}$ does not depend on the choice of $\sigma_P$, and its conjugacy class does not depend on $P$, by the argument of Lemma 2.4.3.

**Definition 2.5.6 (Artin $L$-function).** The *Artin $L$-function* of $\rho$ is
$$L(\rho, s) = \prod_v \det\bigl(1 - \rho(\sigma_P) N(v)^{-s} \,\big|\, V^{I_P}\bigr)^{-1},$$
the product over all finite primes $v$ of $K$. It converges absolutely for $\mathrm{Re}(s) > 1$.

Lean: `Langlands.artinLFunction`

For the trivial representation, $L(\mathbf{1}, s)$ is the Dedekind zeta function $\zeta_K(s)$. For $n = 1$, $\rho$ is a character of $\mathrm{Gal}(L/K)^{ab}$, and by class field theory, Volume 3, $L(\rho, s)$ is the $L$-function of a Hecke character of finite order. The function $L(\rho, s)$ is additive in $\rho$ and compatible with induction. Artin proved these facts, and Brauer proved with his induction theorem that $L(\rho, s)$ has a meromorphic continuation to $\mathbb{C}$ and a functional equation. This is in [Neu99, Chapter VII, Section 10]. The Lean definition `Langlands.artinLFunction` is the product over all the primes $v$ of the local factors `Langlands.artinLocalFactor`, which use the projector $e_I = |I|^{-1}\sum_{\tau \in I}\rho(\tau)$ onto $V^{I_P}$ and an arithmetic Frobenius `Langlands.frobeniusAbove`. The fidelity theorem `Langlands.Fidelity.artinLFunction_one` proves that for the trivial character it is the Euler product of $\zeta_K$, with a factor at each prime.

**Conjecture 2.5.7 (Artin).** Let $L/K$ be a finite Galois extension of number fields and $\rho : \mathrm{Gal}(L/K) \to GL_n(\mathbb{C})$ an irreducible representation with $\rho \ne \mathbf{1}$. Then $L(\rho, s)$ extends to an entire function.

Node: LGEHB4MGJK · Lean: `Langlands.ArtinConjecture`

For $n = 1$ the conjecture is true, by Hecke's theorem on the $L$-functions of Hecke characters, Volume 3, Chapter 5. It is open in general. The Lean statement asks for an entire function equal to `artinLFunction ρ s` for $\mathrm{Re}(s) > 1$; by the theorem of Brauer this is the same as the absence of poles of the meromorphic continuation. The archimedean factors have no zeros, so it does not matter that the statement is for the $L$-function without them. In the Langlands program, the conjecture is expected to follow from the existence of a cuspidal automorphic representation of $GL_n(\mathbb{A}_K)$ with the same $L$-function, whose $L$-function is entire by the theory of Godement and Jacquet.

**Theorem 2.5.8 (Deligne and Serre).** Let $f \in S_1(N, \chi)$ be a newform of weight 1. There is an irreducible representation $\rho : G_\mathbb{Q} \to GL_2(\mathbb{C})$ with finite image, unramified at the primes $p \nmid N$, with $\mathrm{tr}\,\rho(\mathrm{Frob}_p) = a_p(f)$ and $\det\rho(\mathrm{Frob}_p) = \chi(p)$ for $p \nmid N$. It is odd, and $L(\rho, s) = L(f, s)$.

Lean: not stated yet

*Outline of the proof.* This is [DS74, Theorem 4.1]. For each prime $\ell$, the form $f$ is congruent modulo $\ell$ to forms of weight $\ge 2$, and Theorem 2.4.4 with Proposition 2.5.2 gives representations $\bar\rho_\ell : G_\mathbb{Q} \to GL_2(\bar{\mathbb{F}}_\ell)$ with traces $a_p(f) \bmod \ell$. Deligne and Serre prove an estimate, from the Rankin-Selberg method, which shows that the images of the $\bar\rho_\ell$ have bounded order as $\ell$ varies. So for infinitely many $\ell$ the $\bar\rho_\ell$ lift to one representation with finite image in characteristic 0. The equality of $L$-functions at the primes $p \mid N$ uses the theory of newforms. $\square$

Since $\rho$ has finite image, the eigenvalues of $\rho(\mathrm{Frob}_p)$ are roots of unity, so $|a_p(f)| \le 2$. This is the Ramanujan-Petersson bound in weight 1.

**Theorem 2.5.9 (Artin's conjecture for odd representations of dimension 2 over $\mathbb{Q}$).** Let $L/\mathbb{Q}$ be a finite Galois extension and $\rho : \mathrm{Gal}(L/\mathbb{Q}) \to GL_2(\mathbb{C})$ an irreducible representation with $\det\rho(c) = -1$ for each complex conjugation $c$. Then $L(\rho, s)$ extends to an entire function. More precisely, there are $N \ge 1$, a character $\chi$ modulo $N$ and a newform $f \in S_1(N, \chi)$ with $L(\rho, s) = L(f, s)$.

Node: LGX6BXWH0J · Lean: `Langlands.ArtinOdd2Q`

*Outline of the proof.* The projective image of $\rho$ is a finite subgroup of $PGL_2(\mathbb{C})$, so it is cyclic, dihedral, or isomorphic to $A_4$, $S_4$ or $A_5$. The cyclic case does not occur since $\rho$ is irreducible. The dihedral case is due to Hecke, through theta series of binary quadratic forms. Langlands proved the case $A_4$ and Tunnell the case $S_4$, with base change for $GL_2$. The remaining case $A_5$ follows from the work of Khare and Wintenberger [KW09, Part I] and of Kisin [Kis09]. The argument is due to Serre. The image of $\rho$ is defined over the ring of integers of a number field, and for each large prime $p$ its reduction $\bar\rho_p$ modulo a prime over $p$ is irreducible, odd, and unramified at $p$. The strong form of Serre's conjecture gives for each such $p$ a form modulo $p$ of weight 1 and of level the Artin conductor $N$ of $\rho$. For large $p$ these forms lift to characteristic 0, and there are finitely many newforms of weight 1 and level $N$. So one newform $f$ has $a_q(f) \equiv \mathrm{tr}\,\rho(\mathrm{Frob}_q)$ modulo primes over infinitely many $p$, and then $a_q(f) = \mathrm{tr}\,\rho(\mathrm{Frob}_q)$ for all $q \nmid N$. By Chebotarev, $\rho$ is the representation of $f$ of Theorem 2.5.8, and $L(\rho, s) = L(f, s)$. This $L$-function is entire, by Theorem 2.2.7 in its form for $\Gamma_1(N)$. $\square$

Conversely, Theorem 2.5.8 shows that every newform of weight 1 arises in this way, so the newforms of weight 1 and the odd irreducible representations of dimension 2 of $G_\mathbb{Q}$ with complex coefficients correspond to each other. This is the simplest case of the Langlands correspondence with nonabelian Galois groups in which both sides are known.

**Remark 2.5.10 (the Lean form of Theorem 2.5.9).** The statement `Langlands.ArtinOdd2Q` takes a finite Galois extension $L$ of $\mathbb{Q}$ inside `AlgebraicClosure ℚ` and $\rho$ with `IsIrreducibleRep ρ` and $\det\rho(c) = -1$ for each $c$ with `IsComplexConjugationOf c`, an element of $\mathrm{Gal}(L/\mathbb{Q})$ that is complex conjugation for some embedding $L \to \mathbb{C}$. It asks for an entire function equal to `artinLFunction ρ s` for $\mathrm{Re}(s) > 1$, and for $N > 0$, $\chi$ and a cusp form $f$ of weight 1 on $\Gamma_1(N)$ with `IsNormalizedEigenformWithCharacter f χ` and `artinLFunction ρ s = LSeries (qCoeffGamma1 f) s` for $\mathrm{Re}(s) > 1$. The equality of the Dirichlet series for $\mathrm{Re}(s) > 1$ is the equality of all the coefficients, at the ramified primes too. So, unlike in Remark 2.1.11, the statement is about the newform of level the Artin conductor of $\rho$, with $\chi$ the character of $\det\rho$. The first part of the conclusion, the entire continuation, is the case $K = \mathbb{Q}$, $n = 2$ of `Langlands.ArtinConjecture` for odd $\rho$. The converse direction, Theorem 2.5.8, is not stated in Lean.
