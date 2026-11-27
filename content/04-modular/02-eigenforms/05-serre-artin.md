---
title: Serre's conjecture and the Artin conjecture
nodes: [LGKH3WKEVV, LGEHB4MGJK, LGX6BXWH0J]
sources: [KW09, Kis09, Kis09b, DS74, Neu99]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Serre's conjecture and the Artin conjecture

Section 2.4 goes from eigenforms to Galois representations. This section states two theorems that go in the other direction. Serre's conjecture, proved by Khare and Wintenberger, says that every odd irreducible representation of $G_\mathbb{Q}$ of dimension 2 over $\bar{\mathbb{F}}_p$ comes from an eigenform. The Artin conjecture for odd representations of dimension 2 over $\mathbb{C}$ follows, and it identifies their Artin $L$-functions with $L$-functions of forms of weight 1. The last subsection sets up the framed deformation rings of Mazur and Kisin. The modularity lifting theorems in the proofs of these results use them, and the Breuil-Mezard conjecture is a statement about their multiplicities.

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

### Framed deformation rings

The proofs of Theorems 2.5.3 and 2.5.9 use the modularity lifting theorems of Wiles, Taylor-Wiles and Kisin. These theorems compare a ring that classifies the lifts of a residual representation $\bar\rho$ with a Hecke algebra. This subsection defines the ring that classifies the lifts, the universal framed deformation ring of Mazur, and the quotients of it that Kisin uses. It proves the formal properties that follow from the definitions. The existence of the ring is a theorem of Mazur, and we give only an outline of its proof. Then it defines the Hilbert-Samuel multiplicity of the special fiber, which is the number in the Breuil-Mezard conjecture. The references are Mazur, "Deforming Galois representations" (1989), Schlessinger, "Functors of Artin rings" (1968), Kisin, "Potentially semi-stable deformation rings" (2008), and [Kis09b].

In this subsection $\Lambda$ is a commutative ring, $k$ is a field with a $\Lambda$-algebra structure, $G$ is a topological group and $\bar\rho : G \to GL_n(k)$ is a homomorphism. The main case is $\Lambda = W(k)$ for a finite field $k$ of characteristic $p$, $G = G_{\mathbb{Q}_p}$ and $n = 2$. For a local ring $A$ we write $\mathfrak{m}_A$ for its maximal ideal.

**Definition 2.5.11 (coefficient algebras).** A *coefficient algebra* is a noetherian local ring $A$ with a $\Lambda$-algebra structure, complete for the $\mathfrak{m}_A$-adic topology, together with a surjective homomorphism of $\Lambda$-algebras $\pi_A : A \to k$, the *residue map*. A *morphism* $f : A \to B$ of coefficient algebras is a homomorphism of $\Lambda$-algebras with $\pi_B \circ f = \pi_A$. The coefficient algebras and their morphisms form a category $\mathcal{C}_\Lambda$. For $N \ge 0$ the quotient $A / \mathfrak{m}_A^{N+1}$, with the residue map induced by $\pi_A$, is a coefficient algebra, and it is artinian.

Lean: `Langlands.CoeffAlg`, `Langlands.CoeffAlg.Hom`, `Langlands.CoeffAlg.quot`, `Langlands.CoeffAlg.toQuot`

The kernel of $\pi_A$ is a maximal ideal, because $\pi_A$ is surjective onto a field. So it is $\mathfrak{m}_A$, and $A / \mathfrak{m}_A = k$. A morphism sends $\mathfrak{m}_A$ into $\mathfrak{m}_B$, and so it sends $\mathfrak{m}_A^N$ into $\mathfrak{m}_B^N$. An artinian local $\Lambda$-algebra $A$ with a surjection $A \to k$ is a coefficient algebra: it is noetherian, and $\mathfrak{m}_A^N = 0$ for some $N$, so it is complete. If $\Lambda$ is a complete discrete valuation ring with residue field $k$, for example $W(k)$, then $\Lambda$ with its residue map is a coefficient algebra, and it is an initial object of $\mathcal{C}_\Lambda$: the structure map $\Lambda \to A$ is the only homomorphism of $\Lambda$-algebras.

**Definition 2.5.12 (framed lifts).** Let $A$ be a coefficient algebra. A *framed lift* of $\bar\rho$ to $A$ is a homomorphism $\rho : G \to GL_n(A)$ with these two properties.
1. The reduction $\pi_A \circ \rho$ is $\bar\rho$.
2. For each $N \ge 0$ the kernel of the composite $G \to GL_n(A) \to GL_n(A / \mathfrak{m}_A^N)$ is an open subgroup of $G$.

We write $D^\square_{\bar\rho}(A)$ for the set of the framed lifts of $\bar\rho$ to $A$. For a morphism $f : A \to B$ and $\rho \in D^\square_{\bar\rho}(A)$, put $f_* \rho = GL_n(f) \circ \rho$.

Lean: `Langlands.framedLifts`, `Langlands.pushforward`, `Langlands.framedDeformationFunctor`

Condition 2 is the continuity of $\rho$ for the $\mathfrak{m}_A$-adic topology on $A$. The word "framed" means that we do not identify two lifts that are conjugate by a matrix in $1 + M_n(\mathfrak{m}_A)$. The classes of lifts under this conjugation are the deformations of Mazur. The framed lifts are easier to handle, because the functor of Lemma 2.5.13 is pro-representable with no condition on $\bar\rho$. The functor of the deformations is pro-representable only under a condition, for example if the centralizer of the image of $\bar\rho$ is the group of scalars.

**Lemma 2.5.13 (the framed deformation functor).** Let $f : A \to B$ and $g : B \to C$ be morphisms of coefficient algebras.
1. If $\rho \in D^\square_{\bar\rho}(A)$, then $f_* \rho \in D^\square_{\bar\rho}(B)$.
2. $(g \circ f)_* = g_* \circ f_*$ and $(\mathrm{id}_A)_* = \mathrm{id}$. So $A \mapsto D^\square_{\bar\rho}(A)$ is a functor from $\mathcal{C}_\Lambda$ to the category of sets, the *framed deformation functor*.
3. If $A$ is artinian, a homomorphism $\rho : G \to GL_n(A)$ is a framed lift if and only if $\pi_A \circ \rho = \bar\rho$ and the kernel of $\rho$ is open.
4. Let $G = G_{\mathbb{Q}_p}$, $n = 2$ and $A$ artinian. Then $D^\square_{\bar\rho}(A)$ is the set `Langlands.FramedLift` of the file `Langlands/Statements/PadicGalois.lean`, for the residue map $\pi_A$.

Lean: `Langlands.map_mem_framedLifts`, `Langlands.pushforward_comp`, `Langlands.pushforward_id`, `Langlands.mem_framedLifts_iff_of_isArtinianRing`, `Langlands.framedLifts_eq_framedLift`

*Proof.* (1) We have $\pi_B \circ f_* \rho = GL_n(\pi_B \circ f) \circ \rho = \pi_A \circ \rho = \bar\rho$. Since $f(\mathfrak{m}_A^N) \subseteq \mathfrak{m}_B^N$, the map $f$ induces a homomorphism $\bar f : A / \mathfrak{m}_A^N \to B / \mathfrak{m}_B^N$, and the reduction of $f_* \rho$ modulo $\mathfrak{m}_B^N$ is $GL_n(\bar f)$ composed with the reduction of $\rho$ modulo $\mathfrak{m}_A^N$. So its kernel contains the kernel of the reduction of $\rho$. A subgroup of a topological group that contains an open subgroup is open.

(2) The two identities hold entry by entry, since $GL_n(g \circ f) = GL_n(g) \circ GL_n(f)$.

(3) Let $\rho$ be a framed lift. Since $A$ is artinian and local, $\mathfrak{m}_A^N = 0$ for some $N$. Then $A \to A / \mathfrak{m}_A^N$ is injective, so the kernel of $\rho$ is the kernel of its reduction modulo $\mathfrak{m}_A^N$, which is open. Conversely, if the kernel of $\rho$ is open, the kernel of each reduction contains it, so it is open.

(4) This is part 3, since `Langlands.FramedLift` asks for an open kernel and for $\pi_A \circ \rho = \bar\rho$. $\square$

**Definition 2.5.14 (universal framed deformation ring).** Let $R$ be a coefficient algebra and $\rho^u \in D^\square_{\bar\rho}(R)$. The pair $(R, \rho^u)$ is a *universal framed deformation* of $\bar\rho$ if for each artinian coefficient algebra $A$ and each $\rho \in D^\square_{\bar\rho}(A)$ there is a unique morphism $f : R \to A$ with $f_* \rho^u = \rho$. Then $R$ is a *universal framed deformation ring* of $\bar\rho$, and we write $R^\square_{\bar\rho}$ or $R^\square$ for it.

Lean: `Langlands.IsUniversalFramedDeformationRing`

The definition asks for the universal property only on the artinian coefficient algebras, as in the work of Schlessinger. The next theorem shows that it then holds on all of them. So $(R, \rho^u)$ pro-represents the functor $D^\square_{\bar\rho}$ on the artinian algebras and represents it on $\mathcal{C}_\Lambda$.

**Theorem 2.5.15 (the universal property on all coefficient algebras).** Let $(R, \rho^u)$ be a universal framed deformation of $\bar\rho$.
1. For each coefficient algebra $A$ and each $\rho \in D^\square_{\bar\rho}(A)$ there is a unique morphism $f : R \to A$ with $f_* \rho^u = \rho$.
2. The map $f \mapsto f_* \rho^u$ is a bijection from $\mathrm{Hom}_{\mathcal{C}_\Lambda}(R, A)$ to $D^\square_{\bar\rho}(A)$, and it is natural in $A$. So $R$ corepresents the functor $D^\square_{\bar\rho}$.

Lean: `Langlands.IsUniversalFramedDeformationRing.existsUnique_of_complete`, `Langlands.IsUniversalFramedDeformationRing.corepresentableBy`

*Proof.* (1) Let $A_N = A / \mathfrak{m}_A^{N+1}$, with the projections $q_N : A \to A_N$ and $q_{N, M} : A_N \to A_M$ for $M \le N$. Each $A_N$ is an artinian coefficient algebra, and $q_{N*} \rho$ is a framed lift to $A_N$ by part 1 of Lemma 2.5.13. So there is a unique morphism $g_N : R \to A_N$ with $g_{N*} \rho^u = q_{N*} \rho$. For $M \le N$ the morphism $q_{N, M} \circ g_N$ satisfies $(q_{N, M} \circ g_N)_* \rho^u = (q_{N, M} \circ q_N)_* \rho = q_{M*} \rho$, so $q_{N, M} \circ g_N = g_M$ by the uniqueness of $g_M$. The ring $A$ is complete, so $A$ is the inverse limit of the $A_N$, and the compatible family $(g_N)$ is induced by a unique homomorphism of $\Lambda$-algebras $f : R \to A$ with $q_N \circ f = g_N$ for each $N$. It is compatible with the residue maps, because $\pi_A = \pi_{A_0} \circ q_0$ and $\pi_{A_0} \circ g_0 = \pi_R$.

The lifts $f_* \rho^u$ and $\rho$ have the same image in $GL_n(A_N)$ for each $N$, since $q_{N*} f_* \rho^u = g_{N*} \rho^u = q_{N*} \rho$. So each entry of $f_* \rho^u(\gamma) - \rho(\gamma)$ lies in $\bigcap_N \mathfrak{m}_A^{N+1}$. This intersection is $0$, because $A$ is complete and so Hausdorff. Hence $f_* \rho^u = \rho$. If $f'$ is another morphism with $f'_* \rho^u = \rho$, then $q_N \circ f'$ is a morphism $R \to A_N$ with $(q_N \circ f')_* \rho^u = q_{N*} \rho$. By the uniqueness of $g_N$, $q_N \circ f' = q_N \circ f$ for all $N$, and $f' = f$ since $A$ is Hausdorff.

(2) Part 1 says that the map is bijective. It is natural, because $(h \circ f)_* \rho^u = h_* (f_* \rho^u)$ for a morphism $h : A \to B$, by part 2 of Lemma 2.5.13. $\square$

**Corollary 2.5.16 (uniqueness of the universal ring).** Let $(R, \rho^u)$ and $(R', \rho'^u)$ be universal framed deformations of $\bar\rho$.
1. There is a unique isomorphism $\varphi : R \to R'$ in $\mathcal{C}_\Lambda$ with $\varphi_* \rho^u = \rho'^u$.
2. If $(R, \rho^u)$ is universal and $e : R \to R''$ is an isomorphism in $\mathcal{C}_\Lambda$, then $(R'', e_* \rho^u)$ is universal.

Lean: `Langlands.IsUniversalFramedDeformationRing.existsUnique_iso`, `Langlands.IsUniversalFramedDeformationRing.of_iso`

*Proof.* (1) By part 1 of Theorem 2.5.15 for $R$ and the lift $\rho'^u$ to $R'$, there is a unique morphism $\varphi : R \to R'$ with $\varphi_* \rho^u = \rho'^u$. In the same way there is a unique morphism $\psi : R' \to R$ with $\psi_* \rho'^u = \rho^u$. Then $(\psi \circ \varphi)_* \rho^u = \rho^u = (\mathrm{id}_R)_* \rho^u$, so $\psi \circ \varphi = \mathrm{id}_R$ by the uniqueness in Theorem 2.5.15 for $A = R$. In the same way $\varphi \circ \psi = \mathrm{id}_{R'}$. So $\varphi$ is an isomorphism, and it is unique by the construction.

(2) The lift $e_* \rho^u$ is framed by part 1 of Lemma 2.5.13. Let $A$ be artinian and $\rho \in D^\square_{\bar\rho}(A)$, and let $f : R \to A$ be the morphism with $f_* \rho^u = \rho$. Then $(f \circ e^{-1})_* (e_* \rho^u) = \rho$. If $f' : R'' \to A$ satisfies $f'_* (e_* \rho^u) = \rho$, then $(f' \circ e)_* \rho^u = \rho$, so $f' \circ e = f$ and $f' = f \circ e^{-1}$. $\square$

So we may speak of *the* universal framed deformation ring, when it exists. The existence needs a finiteness condition on $G$. The group $G$ satisfies *Mazur's condition* $\Phi_p$ if for each open subgroup $H$ of $G$ there are only finitely many continuous homomorphisms $H \to \mathbb{Z}/p\mathbb{Z}$. By local class field theory, $G_{\mathbb{Q}_p}$ and more generally $G_K$ for a finite extension $K$ of $\mathbb{Q}_p$ satisfy $\Phi_p$, because $K$ has only finitely many extensions of degree $p$. The group $G_{\mathbb{Q}, S}$ of the maximal extension of $\mathbb{Q}$ unramified outside a finite set $S$ of places also satisfies it, by the theorem of Hermite and Minkowski.

**Theorem 2.5.17 (Mazur).** Let $k$ be a finite field of characteristic $p$, let $\Lambda = W(k)$, let $G$ be a profinite group that satisfies $\Phi_p$, and let $\bar\rho : G \to GL_n(k)$ be continuous. Then $\bar\rho$ has a universal framed deformation $(R^\square_{\bar\rho}, \rho^u)$. The ring $R^\square_{\bar\rho}$ is a quotient of a power series ring $W(k)[[x_1, \dots, x_m]]$ in $m = \dim_k Z^1(G, \mathrm{ad}\,\bar\rho)$ variables.

Lean: not proved, see Remark 2.5.25.

*Outline of the proof.* This is in the paper of Mazur cited above, for the deformations, and the framed case is simpler. We check the conditions of Schlessinger's criterion for the functor $D = D^\square_{\bar\rho}$ on the artinian coefficient algebras. First, $D(k)$ has one element, $\bar\rho$. Second, let $A \to C$ and $B \to C$ be morphisms of artinian coefficient algebras. Then $A \times_C B$ is an artinian coefficient algebra, $GL_n(A \times_C B) = GL_n(A) \times_{GL_n(C)} GL_n(B)$, and so $D(A \times_C B) \to D(A) \times_{D(C)} D(B)$ is a bijection. This gives the conditions (H1), (H2) and (H4) of Schlessinger. Third, the tangent space $D(k[\varepsilon])$, with $\varepsilon^2 = 0$, is the set of the lifts $(1 + \varepsilon c) \bar\rho$, and the lift is a homomorphism if and only if $c : G \to M_n(k)$ is a continuous $1$-cocycle for the adjoint action. So $D(k[\varepsilon]) = Z^1(G, \mathrm{ad}\,\bar\rho)$. The kernel $H$ of $\bar\rho$ is open, and the restriction to $H$ maps $Z^1(G, \mathrm{ad}\,\bar\rho)$ to $\mathrm{Hom}(H, M_n(k))$ with a kernel of finite dimension. By $\Phi_p$ the target is finite, so (H3) holds. Schlessinger's theorem gives a complete noetherian local $W(k)$-algebra $R$ that pro-represents $D$, and $R$ is a quotient of $W(k)[[x_1, \dots, x_m]]$ with $m$ the dimension of the tangent space. The lift $\rho^u$ is the inverse limit of the lifts to the quotients $R / \mathfrak{m}_R^{N+1}$. An alternative construction takes the quotient of the power series ring in the $n^2$ entries of the matrices of a set of topological generators by the relations of $G$, when $G$ is topologically finitely presented. $\square$

**Example 2.5.18 (characters of $\mathbb{Z}$).** Let $\Lambda$ be a complete noetherian local ring with residue field $k$, for example $\mathbb{Z}_p$ with $k = \mathbb{F}_p$. Let $G = \mathbb{Z}$ with the discrete topology, $n = 1$ and $\bar\rho = 1$. A framed lift to $A$ is a homomorphism $\rho : \mathbb{Z} \to A^\times$ with $\rho(1) \in 1 + \mathfrak{m}_A$, and condition 2 of Definition 2.5.12 is empty since $G$ is discrete. So $D^\square_{\bar\rho}(A) = 1 + \mathfrak{m}_A$. Let $R = \Lambda[[x]]$, with the residue map $x \mapsto 0$, and let $\rho^u(1) = 1 + x$. For an artinian $A$ and $a \in \mathfrak{m}_A$ we have $a^N = 0$ for some $N$. So $\sum_i c_i x^i \mapsto \sum_{i < N} c_i a^i$ is a morphism $f : R \to A$ with $f(x) = a$, and $f_* \rho^u(1) = 1 + a$. Each morphism $f'$ with $f'(x) = a$ kills $x^N$, so it factors through $R / (x^N) = \Lambda[x] / (x^N)$, and it is equal to $f$. So $(\Lambda[[x]], \rho^u)$ is a universal framed deformation of $\bar\rho$. In the notation of Theorem 2.5.17, $Z^1(\mathbb{Z}, k) = \mathrm{Hom}(\mathbb{Z}, k) = k$, and $m = 1$.

Kisin's rings are quotients of $R^\square$ whose points in fields of characteristic $0$ are the lifts of a given $p$-adic Hodge type. The Lean files define such a quotient for an arbitrary condition $P$ on the points. A *point* of $R$ is a homomorphism of $\Lambda$-algebras $x : R \to E$ to a field $E$. It gives the lift $x_* \rho^u = GL_n(x) \circ \rho^u : G \to GL_n(E)$. For each field $E$ with a $\Lambda$-algebra structure let $P_E$ be a condition on the homomorphisms $G \to GL_n(E)$. A point $x$ is *in $P$* if $x_* \rho^u$ satisfies $P_E$.

**Definition 2.5.19 (the quotient $R^\square(P)$).** Let $R$ be a coefficient algebra and $\rho^u : G \to GL_n(R)$ a homomorphism, for example a universal framed deformation. Let $P$ be a condition as above.
1. The *ideal of $P$* is the intersection $I(P)$ of the kernels of all the points $x : R \to E$ in $P$. So $r \in I(P)$ if and only if $x(r) = 0$ for each point $x$ in $P$.
2. The ring $R^\square(P) = R / I(P)$ is the *quotient of $P$*, and $\rho^u_P : G \to GL_n(R^\square(P))$ is the image of $\rho^u$.
3. The condition $P$ *has a point* if there is a point of $R$ in $P$.

Lean: `Langlands.pointIdeal`, `Langlands.PointQuotient`, `Langlands.pointQuotientLift`, `Langlands.HasPoint`

For Kisin's ring $R^\square(\lambda, \tau, \bar\rho)$ of the Breuil-Mezard conjecture, $P_E$ says that $E$ is a finite extension of $W(k)[1/p]$ and that the lift is potentially semistable with Hodge-Tate type $\lambda$ and inertial type $\tau$. The ring $R^\square(P)$ is then the Zariski closure of these points in $\mathrm{Spec}\, R^\square$, with its reduced structure.

**Proposition 2.5.20 (properties of $R^\square(P)$).** In the situation of Definition 2.5.19 the following hold.
1. An ideal $J$ of $R$ is contained in $I(P)$ if and only if $J$ is contained in the kernel of each point in $P$. Each point $x$ in $P$ factors as $x = x_P \circ q$, with the projection $q : R \to R^\square(P)$ and a unique point $x_P$ of $R^\square(P)$, and $x_{P*} \rho^u_P = x_* \rho^u$. So $R^\square(P)$ is the largest quotient of $R$ through which all the points in $P$ factor.
2. The ring $R^\square(P)$ is reduced.
3. Let $\varpi \in \Lambda$, and assume that $x(\varpi) \ne 0$ for each point $x$ in $P$. Then $\varpi$ is not a zero divisor in $R^\square(P)$. For $\Lambda = W(k)$, $\varpi = p$ and a condition $P$ that only allows fields of characteristic $0$, this says that $R^\square(P)$ has no $p$-torsion.
4. $I(P) \ne R$ if and only if $P$ has a point. In this case $I(P) \subseteq \mathfrak{m}_R$, the ring $R^\square(P)$ is a noetherian local ring, and $\pi_R$ induces a surjective residue map $R^\square(P) \to k$.
5. Assume that $P$ has a point, and let $\varpi \in \Lambda$ with image $0$ in $k$. Then the *special fiber* $R^\square(P) / \varpi R^\square(P)$ is a noetherian local ring.

Lean: `Langlands.mem_pointIdeal`, `Langlands.le_pointIdeal_iff`, `Langlands.pointLift`, `Langlands.map_pointLift_comp`, `Langlands.isRadical_pointIdeal`, `Langlands.isReduced_pointQuotient`, `Langlands.isSMulRegular_pointQuotient`, `Langlands.pointIdeal_ne_top_iff`, `Langlands.pointIdeal_le_maximalIdeal`, `Langlands.pointQuotientResidue`, `Langlands.isLocalRing_pointQuotient`, `Langlands.isLocalRing_specialFiber`

*Proof.* (1) If $J \subseteq I(P)$, then $J$ is in each kernel, since $I(P)$ is. Conversely, if $J$ is in each kernel, then $J$ is in their intersection. In particular $I(P) \subseteq \ker x$ for each point $x$ in $P$, so $x$ factors through $q$, in a unique way since $q$ is surjective. Then $x_{P*} \rho^u_P = GL_n(x_P) \circ GL_n(q) \circ \rho^u = GL_n(x) \circ \rho^u$.

(2) The kernel of a homomorphism to a field is a prime ideal, since the field has no zero divisors. An intersection of prime ideals is a radical ideal: if $r^m \in \mathfrak{p}$ for each $\mathfrak{p}$ in the family, then $r \in \mathfrak{p}$ for each $\mathfrak{p}$. The quotient by a radical ideal is reduced.

(3) Let $a, b \in R$ with $\varpi a \equiv \varpi b$ modulo $I(P)$. For each point $x$ in $P$, $x(\varpi) x(a - b) = x(\varpi (a - b)) = 0$ in the field $E$, and $x(\varpi) \ne 0$. So $x(a - b) = 0$ for each such $x$, and $a - b \in I(P)$. So multiplication by $\varpi$ is injective on $R^\square(P)$.

(4) If there is no point in $P$, then $I(P)$ is the empty intersection, which is $R$. If $x$ is a point in $P$, then $x(1) = 1 \ne 0$, so $1 \notin I(P)$. An ideal $I \ne R$ of a local ring is contained in $\mathfrak{m}_R$. Then $R / I(P)$ is a nonzero quotient of a noetherian local ring, so it is noetherian and local with the maximal ideal $\mathfrak{m}_R / I(P)$. Since $I(P) \subseteq \mathfrak{m}_R = \ker \pi_R$, the residue map factors through $R^\square(P)$.

(5) The image of $\varpi$ in $R^\square(P)$ maps to $0$ under the residue map of part 4, so the ideal $\varpi R^\square(P)$ is in the kernel $\mathfrak{m}_R / I(P)$ of this map. So the special fiber is a nonzero quotient of the noetherian local ring $R^\square(P)$, and it is noetherian and local. $\square$

The ring $R^\square(P)$ is also complete, as a quotient of a complete noetherian local ring, so it is a coefficient algebra. Lean does not prove this, see Remark 2.5.25. The points of $R^\square(P)$ in fields need not all be in $P$. Part 1 says only that the points in $P$ are among them. Part 3 matters for Kisin's rings: when $R^\square(P)$ has no $p$-torsion, it is flat over $\mathbb{Z}_p$, and it is the closure of its generic fiber $R^\square(P)[1/p]$. So the special fiber is determined by the points in characteristic $0$.

We now define the multiplicity. Let $S$ be a noetherian local ring with maximal ideal $\mathfrak{m}$ and Krull dimension $d$. For each $m \ge 1$ the ring $S / \mathfrak{m}^m$ is artinian, so it has a finite length $\ell(S / \mathfrak{m}^m)$ as an $S$-module. The function $m \mapsto \ell(S / \mathfrak{m}^m)$ is the *Hilbert-Samuel function* of $S$.

**Definition 2.5.21 (Hilbert-Samuel multiplicity).** Let $S$ be a noetherian local ring of Krull dimension $d$. The *Hilbert-Samuel multiplicity* of $S$ is
$$e(S) = \lim_{m \to \infty} \frac{d! \, \ell(S / \mathfrak{m}^m)}{m^d}.$$
In the situation of part 5 of Proposition 2.5.20 the *multiplicity of the special fiber* is $e(R^\square(P) / \varpi)$. If $P$ has no point, the special fiber is the zero ring, and we put its multiplicity equal to $0$.

Lean: `Langlands.hilbertSamuelFunction`, `Langlands.hilbertSamuelMultiplicity`, `Langlands.localMultiplicity`, `Langlands.SpecialFiber`, `Langlands.specialFiberMultiplicity`, `Langlands.specialFiberMultiplicity_eq`

**Theorem 2.5.22 (existence of the multiplicity).** Let $S$ be a noetherian local ring of Krull dimension $d$. There is a polynomial $Q \in \mathbb{Q}[T]$ of degree $d$ with $\ell(S / \mathfrak{m}^m) = Q(m)$ for all large $m$. Its leading coefficient is $e/d!$ for an integer $e \ge 1$. So the limit of Definition 2.5.21 exists, and $e(S) = e$ is a positive integer.

Lean: `Langlands.exists_hilbertSamuelPoly`, `Langlands.hasHilbertSamuelMultiplicity_hilbertSamuelMultiplicity`

*Outline of the proof.* This is classical, see for example Matsumura, "Commutative Ring Theory", Section 13. The graded ring $\mathrm{gr}(S) = \bigoplus_m \mathfrak{m}^m / \mathfrak{m}^{m+1}$ is generated over the field $S / \mathfrak{m}$ by the images of finitely many generators of $\mathfrak{m}$. By Hilbert's theorem on graded modules over a polynomial ring, $m \mapsto \dim \mathfrak{m}^m / \mathfrak{m}^{m+1}$ is a polynomial for large $m$. The sum of its values, which is $\ell(S / \mathfrak{m}^m)$, is a polynomial $Q$ for large $m$. The values of $Q$ at large integers are integers, so $Q$ is an integer combination of the binomial polynomials $\binom{T}{j}$, and its leading coefficient is $e / \deg Q!$ with an integer $e \ge 1$. The main theorem of dimension theory says that $\deg Q$ is the Krull dimension $d$. Then $d! \, Q(m) / m^d \to e$. $\square$

**Proposition 2.5.23 (examples of multiplicities).**
1. If $S$ is an artinian local ring, then $e(S) = \ell(S)$.
2. If $S$ is a field, then $e(S) = 1$.
3. If $S$ is a discrete valuation ring, then $e(S) = 1$. In particular $e(k[[x]]) = 1$ for a field $k$.

Lean: `Langlands.hilbertSamuelMultiplicity_of_isArtinianRing`, `Langlands.hilbertSamuelMultiplicity_field`, `Langlands.hilbertSamuelMultiplicity_of_isDiscreteValuationRing`, `Langlands.hilbertSamuelMultiplicity_powerSeries`

*Proof.* (1) An artinian local ring has Krull dimension $d = 0$, so $d! / m^d = 1$. Its maximal ideal is nilpotent, so $\mathfrak{m}^m = 0$ and $\ell(S / \mathfrak{m}^m) = \ell(S)$ for all large $m$. So the sequence is eventually constant with the value $\ell(S)$.

(2) A field is an artinian local ring of length $1$, so this is part 1.

(3) A discrete valuation ring has Krull dimension $1$. Let $t$ be a uniformizer. Then $\mathfrak{m}^j = t^j S$, and the chain $S \supset tS \supset \dots \supset t^m S$ has the quotients $t^j S / t^{j+1} S \cong S / tS$, which are simple. So $\ell(S / \mathfrak{m}^m) = m$, and the sequence is $1! \cdot m / m = 1$. The ring $k[[x]]$ is a discrete valuation ring with the uniformizer $x$. $\square$

**Example 2.5.24 (the lifts of order $p$).** Take $\Lambda = \mathbb{Z}_p$, $k = \mathbb{F}_p$ and $G = \mathbb{Z}$, $n = 1$ and $\bar\rho = 1$, as in Example 2.5.18, so $R = \mathbb{Z}_p[[x]]$ and $\rho^u(1) = 1 + x$. Let $P_E$ say that $E$ has characteristic $0$ and that $\rho(1)^p = 1$. A point $x_0 : R \to E$ is in $P$ if and only if $E$ has characteristic $0$ and $\zeta = 1 + x_0(x)$ satisfies $\zeta^p = 1$. Put $f = (1 + x)^p - 1 = x \, \Phi(x)$, with $\Phi(x) = \sum_{j=1}^{p} \binom{p}{j} x^{j-1}$. The element $\Phi(x)$ is a distinguished polynomial of degree $p - 1$ that satisfies Eisenstein's criterion, so the ideals $(x)$ and $(\Phi(x))$ are distinct prime ideals of the unique factorization domain $\mathbb{Z}_p[[x]]$. The kernel of each point in $P$ contains $f$, so it contains $x$ or $\Phi(x)$. The point $R \to \mathbb{Q}_p$ with $x \mapsto 0$ has the kernel $(x)$, and the point $R \to \mathbb{Q}_p(\zeta_p)$ with $x \mapsto \zeta_p - 1$ has the kernel $(\Phi(x))$. So
$$I(P) = (x) \cap (\Phi(x)) = (f), \qquad R^\square(P) = \mathbb{Z}_p[[x]] / ((1 + x)^p - 1).$$
This ring is reduced and has no $p$-torsion, as part 2 and part 3 of Proposition 2.5.20 say. Its special fiber is $\mathbb{F}_p[[x]] / (x^p)$, because $(1 + x)^p - 1 \equiv x^p$ modulo $p$. This is an artinian local ring of length $p$, so $e(R^\square(P) / p) = p$ by part 1 of Proposition 2.5.23. The two components of $\mathrm{Spec}\, R^\square(P)$ are the trivial lift, with the special fiber $\mathbb{F}_p[[x]] / (x)$ of multiplicity $1$, and the lifts of order exactly $p$, with the special fiber $\mathbb{F}_p[[x]] / (x^{p-1})$ of multiplicity $p - 1$. The multiplicity of the union is the sum $1 + (p - 1)$. The Breuil-Mezard conjecture is a statement of this kind: it writes the multiplicity of the special fiber of $R^\square(\lambda, \tau, \bar\rho)$ as a sum of contributions of the Serre weights.

**Remark 2.5.25 (the Lean status).** The file `Langlands/Deformation/Framed.lean` contains Definitions 2.5.11, 2.5.12, 2.5.14, 2.5.19 and the last part of 2.5.21, Lemma 2.5.13, Theorem 2.5.15, Corollary 2.5.16 and Proposition 2.5.20. The file `Langlands/Ring/HilbertSamuel.lean` defines the Hilbert-Samuel function and the multiplicity and proves Proposition 2.5.23. It defines $e(S)$ as the limit when the limit is a natural number and as $0$ otherwise, and the file `Langlands/Ring/HilbertSamuelPoly.lean` proves Theorem 2.5.22, so the limit always exists. The universal property of `Langlands.IsUniversalFramedDeformationRing` is asked only for the artinian algebras, and Theorem 2.5.15 extends it with `IsAdicComplete.liftAlgHom` of Mathlib. In Lean a morphism in $\mathcal{C}_\Lambda$ is a structure `Langlands.CoeffAlg.Hom` with a homomorphism of $\Lambda$-algebras and the compatibility with the residue maps, and $\mathcal{C}_\Lambda$ is a category of Mathlib. The following points are not in Lean.
1. *Existence.* Theorem 2.5.17 is not proved. It needs the condition $\Phi_p$, Schlessinger's criterion or a construction as a quotient of a power series ring, and the fact that a quotient of a complete noetherian local ring is complete. Mathlib does not have these results. So each result in Lean about $R^\square$ has the universal pair as a hypothesis.
2. *Completeness of $R^\square(P)$.* The quotient $R^\square(P)$ is not shown to be complete, so it is not shown to be an object of `Langlands.CoeffAlg`. The definition `Langlands.localMultiplicity` gives $e$ for a ring that is local and $0$ for the other rings, so that `Langlands.specialFiberMultiplicity` is defined for each $P$.
3. *The conditions.* The condition $P$ is arbitrary. The conditions of $p$-adic Hodge theory, such as potentially semistable of type $(\lambda, \tau)$, are not in Lean, because Mathlib does not have the Galois action on the period rings of Fontaine.

The Breuil-Mezard conjecture for $GL_2(\mathbb{Q}_p)$ is the node LGRMD7S8EV of the map. Its Lean form `Langlands.BreuilMezardGL2Qp`, in `Langlands/Statements/BreuilMezard.lean`, is a shape and not a statement: the structure `Langlands.BreuilMezardData` has the multiplicities $e(R^\square(\lambda, \tau, \bar\rho) \otimes k)$ as a field, and it does not use the definitions of this subsection. With a proof of Theorem 2.5.17 and the conditions of item 3, the field `deformationMultiplicity` could be defined as `Langlands.specialFiberMultiplicity` with $\varpi = p$ for Kisin's condition $P$.
