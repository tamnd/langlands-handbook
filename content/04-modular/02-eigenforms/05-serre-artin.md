---
title: Serre's conjecture and the Artin conjecture
nodes: [LGKH3WKEVV, LGEHB4MGJK, LGX6BXWH0J]
sources: [KW09, Kis09, Kis09b, DS74, Neu99, BH06]
status: checked
drafted_by: writer
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## Serre's conjecture and the Artin conjecture

Section 2.4 goes from eigenforms to Galois representations. This section states two theorems that go in the other direction. Serre's conjecture, proved by Khare and Wintenberger, says that every odd irreducible representation of $G_\mathbb{Q}$ of dimension 2 over $\bar{\mathbb{F}}_p$ comes from an eigenform. The Artin conjecture for odd representations of dimension 2 over $\mathbb{C}$ follows, and it identifies their Artin $L$-functions with $L$-functions of forms of weight 1. The next subsection sets up the framed deformation rings of Mazur and Kisin. The modularity lifting theorems in the proofs of these results use them, and the Breuil-Mezard conjecture is a statement about their multiplicities. The last two subsections construct the two inputs of that conjecture: the crystalline and semistable period rings of Fontaine, which define the $p$-adic Hodge conditions on the lifts, and the inertial types of Henniart with the Serre weight multiplicities $n_{a,b}(\lambda, \tau)$.

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

For the trivial representation, $L(\mathbf{1}, s)$ is the Dedekind zeta function $\zeta_K(s)$. For $n = 1$, $\rho$ is a character of $\mathrm{Gal}(L/K)^{ab}$, and by class field theory, Volume 3, $L(\rho, s)$ is the $L$-function of a Hecke character of finite order. The function $L(\rho, s)$ is additive in $\rho$ and compatible with induction. Artin proved these facts, and Brauer proved with his induction theorem that $L(\rho, s)$ has a meromorphic continuation to $\mathbb{C}$ and a functional equation. This is in [Neu99, Chapter VII, Sections 10 and 12]. The Lean definition `Langlands.artinLFunction` is the product over all the primes $v$ of the local factors `Langlands.artinLocalFactor`, which use the projector $e_I = |I|^{-1}\sum_{\tau \in I}\rho(\tau)$ onto $V^{I_P}$ and an arithmetic Frobenius `Langlands.frobeniusAbove`. The fidelity theorem `Langlands.Fidelity.artinLFunction_one` proves that for the trivial character it is the Euler product of $\zeta_K$, with a factor at each prime.

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

*Outline of the proof.* This is classical, see for example Matsumura, "Commutative Ring Theory", Sections 13 and 14. The graded ring $\mathrm{gr}(S) = \bigoplus_m \mathfrak{m}^m / \mathfrak{m}^{m+1}$ is generated over the field $S / \mathfrak{m}$ by the images of finitely many generators of $\mathfrak{m}$. By Hilbert's theorem on graded modules over a polynomial ring, $m \mapsto \dim \mathfrak{m}^m / \mathfrak{m}^{m+1}$ is a polynomial for large $m$. The sum of its values, which is $\ell(S / \mathfrak{m}^m)$, is a polynomial $Q$ for large $m$. The values of $Q$ at large integers are integers, so $Q$ is an integer combination of the binomial polynomials $\binom{T}{j}$, and its leading coefficient is $e / \deg Q!$ with an integer $e \ge 1$. The main theorem of dimension theory says that $\deg Q$ is the Krull dimension $d$. Then $d! \, Q(m) / m^d \to e$. $\square$

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
3. *The conditions.* The condition $P$ is arbitrary. The conditions of $p$-adic Hodge theory, such as potentially semistable of type $(\lambda, \tau)$, are not in Lean. The period rings $B_{\mathrm{dR}}$, $B_{\mathrm{cris}}$ and $B_{\mathrm{st}}$ and the Galois action on $B_{\mathrm{cris}}$ are now in Lean, see the next subsection, but the Galois action on $B_{\mathrm{st}}$ and the Hodge-Tate type are not, see Remark 2.5.38.

The Breuil-Mezard conjecture for $GL_2(\mathbb{Q}_p)$ is the node LGRMD7S8EV of the map. Its Lean form `Langlands.BreuilMezardGL2Qp`, in `Langlands/Statements/BreuilMezard.lean`, is a shape and not a statement: the structure `Langlands.BreuilMezardData` has the multiplicities $e(R^\square(\lambda, \tau, \bar\rho) \otimes k)$ as a field, and it does not use the definitions of this subsection. With a proof of Theorem 2.5.17 and the conditions of item 3, the field `deformationMultiplicity` could be defined as `Langlands.specialFiberMultiplicity` with $\varpi = p$ for Kisin's condition $P$.

### Crystalline and semistable period rings

Kisin's condition $P$ asks that a lift is potentially semistable of a given type. The definition of this condition needs the period rings of Fontaine. Volume 12 will treat $p$-adic Hodge theory in full. This subsection constructs the rings $A_{\mathrm{cris}}$, $B_{\mathrm{cris}}^+$, $B_{\mathrm{cris}}$ and $B_{\mathrm{st}}$, the element $t$ and the Kummer cocycle, and it proves the properties that follow from the constructions. These are the parts that the Lean files prove. For the deeper properties we give the statements and an outline, and we mark them as such. The references are Fontaine, "Le corps des périodes $p$-adiques", Astérisque 223 (1994), the book of Fontaine and Ouyang, "Theory of $p$-adic Galois representations", and the notes of Brinon and Conrad, "CMI summer school notes on $p$-adic Hodge theory".

In this subsection $p$ is a prime and $R$ is a commutative ring that is complete for the $p$-adic topology, in which $p$ is not a unit. The main case is $R = \mathcal{O}_{\mathbb{C}_p}$, the ring of integers of the completion $\mathbb{C}_p$ of $\bar{\mathbb{Q}}_p$. Each $\sigma \in G_{\mathbb{Q}_p}$ preserves the absolute value of $\bar{\mathbb{Q}}_p$, so it extends by continuity to $\mathbb{C}_p$, and the extension preserves $\mathcal{O}_{\mathbb{C}_p}$. So $G_{\mathbb{Q}_p}$ acts on $\mathcal{O}_{\mathbb{C}_p}$ by ring automorphisms.

**Definition 2.5.26 (the tilt, the map $\theta$ and admissible representations).**
1. The *tilt* $R^\flat$ is the set of the sequences $(x_0, x_1, \dots)$ of elements of $R/pR$ with $x_{n+1}^p = x_n$ for all $n$, with the operations term by term. It is a perfect ring of characteristic $p$. For $x \in R^\flat$ and lifts $\hat x_n \in R$ of the $x_n$, the limit $x^\sharp = \lim_n \hat x_n^{p^n}$ exists in $R$ and does not depend on the lifts. The map $x \mapsto x^\sharp$ is multiplicative, and it is the *untilt*.
2. Let $W(R^\flat)$ be the ring of Witt vectors of $R^\flat$, with the Teichmüller map $x \mapsto [x]$ and the Frobenius $\varphi$. Each element of $W(R^\flat)$ is $\sum_{n \ge 0} p^n [x_n]$ for a unique sequence $(x_n)$ in $R^\flat$. *Fontaine's map* is the ring homomorphism $\theta : W(R^\flat) \to R$ with $\theta(\sum_n p^n [x_n]) = \sum_n p^n x_n^\sharp$. We write $\theta$ also for its extension $W(R^\flat)[1/p] \to R[1/p]$.
3. The ring $B_{\mathrm{dR}}^+(R)$ is the completion $\varprojlim_n W(R^\flat)[1/p] / I^n$ of $W(R^\flat)[1/p]$ at the ideal $I = \ker \theta$. The ring $B_{\mathrm{dR}}(R)$ is the localization of $B_{\mathrm{dR}}^+(R)$ at the submonoid generated by the images of the elements $a$ with $I = a W(R^\flat)[1/p]$.
4. Let $K$ be a field, $G$ a group and $B$ a $K$-algebra on which $G$ acts by $K$-algebra homomorphisms. For a representation $V$ of $G$ on a $K$-vector space of finite dimension, put $D_B(V) = (B \otimes_K V)^G$, with $G$ acting on both factors. It is a module over $B^G$. The representation $V$ is *$B$-admissible* if the rank of $D_B(V)$ over $B^G$ is $\dim_K V$. A representation of $G_{\mathbb{Q}_p}$ on a $\mathbb{Q}_p$-vector space of finite dimension is *de Rham* if it is $B_{\mathrm{dR}}(\mathcal{O}_{\mathbb{C}_p})$-admissible.

Lean: Mathlib's `PreTilt`, `PreTilt.untilt`, `fontaineTheta`, `BDeRhamPlus`, `BDeRham`, and `Langlands.Padic.deRhamInvariants`, `Langlands.Padic.IsAdmissible`, `Langlands.Padic.IsDeRhamQp`

A ring homomorphism $f : R \to S$ acts term by term on the sequences, so it gives a homomorphism $f^\flat : R^\flat \to S^\flat$ with $f^\flat(x)^\sharp = f(x^\sharp)$. Then $W(f^\flat)$ satisfies $\theta_S \circ W(f^\flat) = f \circ \theta_R$, so it maps $\ker \theta_R$ into $\ker \theta_S$, and it induces a homomorphism $B_{\mathrm{dR}}^+(R) \to B_{\mathrm{dR}}^+(S)$. If a group acts on $R$ by ring automorphisms, it acts on all these rings. This is how $G_{\mathbb{Q}_p}$ acts on $B_{\mathrm{dR}}(\mathcal{O}_{\mathbb{C}_p})$. In the cases of interest $B^G$ is a field. Fontaine proved that then $\dim_{B^G} D_B(V) \le \dim_K V$ for the rings of this subsection, so admissibility says that $D_B(V)$ is as large as possible. The definition of a de Rham representation makes sense only if $B_{\mathrm{dR}}(\mathcal{O}_{\mathbb{C}_p})$ is not the zero ring. The next proposition proves this.

**Proposition 2.5.27 ($B_{\mathrm{dR}}(\mathcal{O}_{\mathbb{C}_p})$ is not zero).** Choose $y_n \in \mathcal{O}_{\mathbb{C}_p}$ with $y_0 = p$ and $y_{n+1}^p = y_n$. Let $p^\flat \in \mathcal{O}_{\mathbb{C}_p}^\flat$ be the sequence of the classes of the $y_n$, and put $\xi = p - [p^\flat] \in W(\mathcal{O}_{\mathbb{C}_p}^\flat)$.
1. $(p^\flat)^\sharp = p$, and $p^\flat \ne 0$.
2. $\theta(\xi) = 0$, and $\xi \ne 0$.
3. The rings $\mathcal{O}_{\mathbb{C}_p}^\flat$, $W(\mathcal{O}_{\mathbb{C}_p}^\flat)$ and $W(\mathcal{O}_{\mathbb{C}_p}^\flat)[1/p]$ are domains, and $I = \ker \theta$ is a nonzero proper ideal of $W(\mathcal{O}_{\mathbb{C}_p}^\flat)[1/p]$.
4. Let $R$ be such that $R[1/p] \ne 0$ and $W(R^\flat)[1/p]$ is a domain, and assume that $\ker \theta \ne 0$ in $W(R^\flat)[1/p]$. Then $B_{\mathrm{dR}}(R)$ is not the zero ring.
5. $B_{\mathrm{dR}}(\mathcal{O}_{\mathbb{C}_p}) \ne 0$, and the trivial representation $\mathbb{Q}_p$ of $G_{\mathbb{Q}_p}$ is de Rham.

Lean: `Langlands.Padic.untilt_pFlat`, `Langlands.Padic.pFlat_ne_zero`, `Langlands.Padic.fontaineTheta_xiCp`, `Langlands.Padic.xiCp_ne_zero`, `Langlands.Padic.isDomain_locWitt`, `Langlands.Padic.ker_fontaineThetaInvertP_ne_bot`, `Langlands.Padic.nontrivial_bdr`, `Langlands.Padic.nontrivial_bdr_padicComplexInt`, `Langlands.Padic.isDeRhamQp_trivial`

*Proof.* (1) The $y_n$ are lifts of the terms of $p^\flat$, so $(p^\flat)^\sharp = \lim_n y_n^{p^n} = \lim_n p = p$. If $p^\flat = 0$, then $y_1 \in p\mathcal{O}_{\mathbb{C}_p}$, so $|y_1| \le p^{-1}$. But $|y_1| = p^{-1/p} > p^{-1}$.

(2) We have $\theta(p) = p$ and $\theta([p^\flat]) = (p^\flat)^\sharp = p$, so $\theta(\xi) = 0$. For a ring $A$ of characteristic $p$, the map $W(A) \to A$ that takes the first Witt coordinate is a ring homomorphism. It sends $p$ to $0$ and $[x]$ to $x$. So it sends $\xi$ to $-p^\flat \ne 0$, and $\xi \ne 0$.

(3) Let $x = (x_n) \in \mathcal{O}_{\mathbb{C}_p}^\flat$, and let $x^{(n)} = \lim_m \hat x_{n+m}^{p^m}$, so that $x^{(0)} = x^\sharp$, $(x^{(n+1)})^p = x^{(n)}$ and $x^{(n)}$ lifts $x_n$. If $x^\sharp = 0$, then each $x^{(n)}$ is $0$, because $\mathcal{O}_{\mathbb{C}_p}$ is a domain, and so $x = 0$. Since $x \mapsto x^\sharp$ is multiplicative and $\mathcal{O}_{\mathbb{C}_p}$ is a domain, $\mathcal{O}_{\mathbb{C}_p}^\flat$ is a domain. Let $A$ be a perfect domain of characteristic $p$. In $W(A)$ we have $p \cdot (a_0, a_1, \dots) = (0, a_0^p, a_1^p, \dots)$. So each nonzero $x \in W(A)$ is $p^a x'$ with $x'_0 \ne 0$, where $a$ is the first index with $x_a \ne 0$, and $p^a z = 0$ only for $z = 0$. If $x = p^a x'$ and $y = p^b y'$ are nonzero, then the first coordinate of $x'y'$ is $x'_0 y'_0 \ne 0$, so $xy = p^{a+b} x'y' \ne 0$. So $W(A)$ is a domain, $p \ne 0$ in it, and the localization $W(A)[1/p]$ is a domain that contains $W(A)$. The element $\xi$ is a nonzero element of $I$ by part 2. The ideal $I$ is proper, because it is the kernel of a homomorphism to the nonzero ring $\mathbb{C}_p$.

(4) Put $A = W(R^\flat)[1/p]$. The ideal $I$ is proper, since $R[1/p] \ne 0$. Let $S$ be the submonoid of Definition 2.5.26, part 3. A localization is the zero ring if and only if the submonoid contains $0$. Each $s \in S$ is the image of a product $b = a_1 \cdots a_k$ of generators of $I$, so $bA = I^k$, and $b \ne 0$ since $A$ is a domain and $I \ne 0$. Suppose that the image of $b$ in $B_{\mathrm{dR}}^+(R)$ is $0$. Then $b \in I^{k+1} = bI$, so $b = bc$ with $c \in I$. Then $b(1 - c) = 0$, so $c = 1$ and $I = A$, a contradiction. So $0 \notin S$. If $I$ is not principal, $S = \{1\}$, and $B_{\mathrm{dR}}(R) = B_{\mathrm{dR}}^+(R)$ maps onto $A/I \ne 0$.

(5) The first claim follows from parts 3 and 4, with $\mathcal{O}_{\mathbb{C}_p}[1/p] = \mathbb{C}_p$. For the trivial representation $D_B(\mathbb{Q}_p) = B^G$, which is free of rank $1$ over $B^G$ when $B^G \ne 0$. Here $B^G$ contains $1 \ne 0$. $\square$

We now turn to the crystalline rings. For $n \ge 0$ write $n! = p^v m$ with $p \nmid m$. The integer $m$ is a unit in $\mathbb{Z}_p$, so it is a unit in each $\mathbb{Z}_p$-algebra, for example in $W(R^\flat)$, which is a $W(\mathbb{F}_p) = \mathbb{Z}_p$-algebra. So $n!$ is a unit in $W(R^\flat)[1/p]$.

**Definition 2.5.28 (the rings $A_{\mathrm{cris}}$ and $B_{\mathrm{cris}}^+$).**
1. For $x \in \ker \theta \subseteq W(R^\flat)$ and $n \ge 0$ the *divided power* $x^{[n]} = x^n / n!$ is the unique $y \in W(R^\flat)[1/p]$ with $n! \, y = x^n$.
2. The ring $A_{\mathrm{cris}}^0(R)$ is the $W(R^\flat)$-subalgebra of $W(R^\flat)[1/p]$ generated by the divided powers $x^{[n]}$, for $x \in \ker \theta$ and $n \ge 0$.
3. The ring $A_{\mathrm{cris}}(R)$ is the $p$-adic completion $\varprojlim_m A_{\mathrm{cris}}^0(R) / p^m A_{\mathrm{cris}}^0(R)$.
4. The ring $B_{\mathrm{cris}}^+(R)$ is $A_{\mathrm{cris}}(R)[1/p]$.

Lean: `Langlands.Padic.dividedPowers`, `Langlands.Padic.acrisZero`, `Langlands.Padic.Acris`, `Langlands.Padic.BcrisPlus`

Fontaine defines $A_{\mathrm{cris}}$ as the $p$-adic completion of the divided power envelope of $W(R^\flat)$ at $\ker \theta$. The ring $A_{\mathrm{cris}}^0(R)$ is the image of this envelope in $W(R^\flat)[1/p]$. For $R = \mathcal{O}_{\mathbb{C}_p}$ the kernel of $\theta$ on $W(\mathcal{O}_{\mathbb{C}_p}^\flat)$ is generated by $\xi$, and the envelope is the subring $W(\mathcal{O}_{\mathbb{C}_p}^\flat)[\xi^n / n! : n \ge 0]$ of $W(\mathcal{O}_{\mathbb{C}_p}^\flat)[1/p]$, see the paper of Fontaine cited above. So for the main case the two definitions agree. The definition by the image avoids divided power envelopes, which Mathlib does not have.

**Proposition 2.5.29 (functoriality and Frobenius).** Let $f : R \to S$ be a ring homomorphism between two rings of the kind above.
1. The map $W(f^\flat)[1/p]$ sends $A_{\mathrm{cris}}^0(R)$ into $A_{\mathrm{cris}}^0(S)$. It induces ring homomorphisms $A_{\mathrm{cris}}(R) \to A_{\mathrm{cris}}(S)$ and $B_{\mathrm{cris}}^+(R) \to B_{\mathrm{cris}}^+(S)$, and these are compatible with identities and composites.
2. For each $x \in W(R^\flat)$ there is $z \in W(R^\flat)$ with $\varphi(x) = x^p + pz$.
3. For each $m \ge 0$ the element $p^m / m!$ of $W(R^\flat)[1/p]$ is the image of an element of $W(R^\flat)$.
4. The Frobenius $\varphi$ of $W(R^\flat)[1/p]$ sends $A_{\mathrm{cris}}^0(R)$ into itself. So it induces ring endomorphisms $\varphi$ of $A_{\mathrm{cris}}(R)$ and $B_{\mathrm{cris}}^+(R)$, and these commute with the maps of part 1.
5. Let a monoid $M$ act on $R$ by ring endomorphisms. Then $M$ acts on $A_{\mathrm{cris}}(R)$ and on $B_{\mathrm{cris}}^+(R)$ by ring endomorphisms, and $\varphi(gx) = g\varphi(x)$ for $g \in M$. Each nonzero $a \in \mathbb{Z}_p$ is a unit in $B_{\mathrm{cris}}^+(R)$. So $B_{\mathrm{cris}}^+(R)$ is a $\mathbb{Q}_p$-algebra, and $M$ acts by $\mathbb{Q}_p$-algebra homomorphisms.

Lean: `Langlands.Padic.locMap_mem_acrisZero`, `Langlands.Padic.acrisMap`, `Langlands.Padic.acrisMap_id`, `Langlands.Padic.acrisMap_comp`, `Langlands.Padic.bcrisPlusMap_comp`, `Langlands.Padic.exists_frobenius_eq_pow_add`, `Langlands.Padic.exists_factorial_mul_eq_p_pow`, `Langlands.Padic.locFrob_mem_acrisZero`, `Langlands.Padic.acrisFrob`, `Langlands.Padic.bcrisPlusFrob`, `Langlands.Padic.acrisMap_comp_acrisFrob`, `Langlands.Padic.bcrisPlusMap_comp_bcrisPlusFrob`, `Langlands.Padic.acrisFrob_smul`, `Langlands.Padic.bcrisPlusFrob_smul`, `Langlands.Padic.isUnit_zpToBcrisPlus`, `Langlands.Padic.bcrisPlusQpAlgebra`, `Langlands.Padic.bcris_smulCommClass`

*Proof.* (1) The identity $\theta_S \circ W(f^\flat) = f \circ \theta_R$ shows that $W(f^\flat)$ maps $\ker \theta_R$ into $\ker \theta_S$. If $n! \, y = x^n$, then $n! \, W(f^\flat)(y) = W(f^\flat)(x)^n$, so $W(f^\flat)$ sends $x^{[n]}$ to $W(f^\flat)(x)^{[n]}$. It sends $W(R^\flat)$ into $W(S^\flat)$ and the generators of $A_{\mathrm{cris}}^0(R)$ into $A_{\mathrm{cris}}^0(S)$, so it sends $A_{\mathrm{cris}}^0(R)$ into $A_{\mathrm{cris}}^0(S)$. It maps $p A_{\mathrm{cris}}^0(R)$ into $p A_{\mathrm{cris}}^0(S)$, so it induces a map of the $p$-adic completions, and then a map after $p$ is inverted. The compatibility with identities and composites holds for $W(\cdot^\flat)$, and it passes to the completions by the uniqueness of the induced maps.

(2) For a perfect ring $A$ of characteristic $p$ the map $x \mapsto x_0$ identifies $W(A)/pW(A)$ with $A$, since $p \cdot (a_0, a_1, \dots) = (0, a_0^p, a_1^p, \dots)$ and $a \mapsto a^p$ is bijective. The Frobenius $\varphi = W(a \mapsto a^p)$ induces $a \mapsto a^p$ on $A$. So $\varphi(x) - x^p$ maps to $0$ in $A$, and it lies in $pW(A)$.

(3) By Legendre's formula $v_p(m!) = \sum_{i \ge 1} \lfloor m / p^i \rfloor \le m/(p-1) \le m$. So $m! = p^v u$ with $v \le m$ and $p \nmid u$, and $p^m / m! = p^{m - v} u^{-1}$ with $u^{-1} \in \mathbb{Z}_p$.

(4) Let $x \in \ker \theta$ and $n \ge 0$, and write $\varphi(x) = x^p + pz$ by part 2. Since $\varphi(n!) = n!$, we have $\varphi(x^{[n]}) = \varphi(x)^n / n!$, and the binomial formula gives
$$\varphi(x)^n / n! = \sum_{k=0}^{n} \frac{x^{pk}}{k!} \cdot \frac{p^{n-k}}{(n-k)!} \, z^{n-k} = \sum_{k=0}^{n} \frac{(pk)!}{k!} \cdot x^{[pk]} \cdot \frac{p^{n-k}}{(n-k)!} \, z^{n-k}.$$
In each term $(pk)!/k!$ is an integer, $x^{[pk]} \in A_{\mathrm{cris}}^0(R)$, the element $p^{n-k}/(n-k)!$ comes from $W(R^\flat)$ by part 3, and $z \in W(R^\flat)$. So $\varphi(x^{[n]}) \in A_{\mathrm{cris}}^0(R)$. Since $\varphi$ also maps $W(R^\flat)$ into itself, it maps $A_{\mathrm{cris}}^0(R)$ into itself. It maps $p A_{\mathrm{cris}}^0(R)$ into itself, so it induces maps of the completions. The Frobenius of Witt vectors is natural, $W(f^\flat) \circ \varphi = \varphi \circ W(f^\flat)$, because $f^\flat$ commutes with $a \mapsto a^p$. This identity passes to $A_{\mathrm{cris}}^0$ and then to the completions.

(5) The element $g \in M$ acts by the map of part 1 for the homomorphism $x \mapsto gx$ of $R$. The action laws follow from the compatibility with composites, and $\varphi(gx) = g\varphi(x)$ is part 4. The map $\mathbb{Z}_p = W(\mathbb{F}_p) \to W(R^\flat)$ comes from the unique homomorphism $\mathbb{F}_p \to R^\flat$. A nonzero $a \in \mathbb{Z}_p$ is $p^v u$ with $u \in \mathbb{Z}_p^\times$, and $p$ is a unit in $B_{\mathrm{cris}}^+(R)$, so $a$ is a unit there. The maps of part 1 commute with the maps from $\mathbb{Z}_p$, by the uniqueness of $\mathbb{F}_p \to S^\flat$. So the action is $\mathbb{Q}_p$-linear. $\square$

**Proposition 2.5.30 (the element $\log [\varepsilon]$).** Let $\varepsilon \in R^\flat$ with $\varepsilon^\sharp = 1$.
1. $[\varepsilon] - 1 \in \ker \theta$, so $([\varepsilon] - 1)^{[j]} \in A_{\mathrm{cris}}^0(R)$ for all $j \ge 0$.
2. For $j \ge 0$ put $\ell_j = (-1)^j ([\varepsilon] - 1)^{j+1} / (j+1) = (-1)^j \, j! \, ([\varepsilon] - 1)^{[j+1]}$. Then $\ell_j \in A_{\mathrm{cris}}^0(R)$, and $\ell_j \in p^m A_{\mathrm{cris}}^0(R)$ when $pm \le j$.
3. Let $s_N = \sum_{j < N} \ell_j$. For $m \le n$ we have $s_{pn} \equiv s_{pm}$ modulo $p^m A_{\mathrm{cris}}^0(R)$. So the sequence $(s_N)$ converges in $A_{\mathrm{cris}}(R)$. Its limit is
$$\log [\varepsilon] = \sum_{j \ge 1} (-1)^{j-1} \frac{([\varepsilon] - 1)^j}{j} \in A_{\mathrm{cris}}(R).$$
4. For a ring homomorphism $f : R \to S$ we have $f^\flat(\varepsilon)^\sharp = 1$, and the map of $A_{\mathrm{cris}}$ sends $\log [\varepsilon]$ to $\log [f^\flat(\varepsilon)]$. If $M$ acts on $R$, then $g \log [\varepsilon] = \log [g\varepsilon]$ for $g \in M$.
5. $(\varepsilon^p)^\sharp = 1$ and $\varphi(\log [\varepsilon]) = \log [\varepsilon^p]$.

Lean: `Langlands.Padic.teichmuller_sub_one_mem_ker`, `Langlands.Padic.logDiv_mem`, `Langlands.Padic.logTerm`, `Langlands.Padic.logTerm_mem`, `Langlands.Padic.isAdicCauchy_logPartial`, `Langlands.Padic.logTeich`, `Langlands.Padic.acrisMap_logTeich`, `Langlands.Padic.smul_logTeich`, `Langlands.Padic.acrisFrob_logTeich`

*Proof.* (1) $\theta([\varepsilon]) = \varepsilon^\sharp = 1$.

(2) The two forms of $\ell_j$ agree, since $(j+1)! = (j+1) \, j!$. The second form is in $A_{\mathrm{cris}}^0(R)$ by part 1. If $pm \le j$, then $v_p(j!) \ge \lfloor j/p \rfloor \ge m$, so $j! = p^m c$ with $c \in \mathbb{Z}$, and $\ell_j = p^m \cdot (-1)^j c \, ([\varepsilon] - 1)^{[j+1]}$.

(3) The difference $s_{pn} - s_{pm}$ is the sum of the $\ell_j$ with $pm \le j < pn$, and each of them is in $p^m A_{\mathrm{cris}}^0(R)$ by part 2. In the same way $s_N - s_{pm} \in p^m A_{\mathrm{cris}}^0(R)$ for $N \ge pm$. So the sequence is Cauchy for the $p$-adic topology, and it has a limit in the completion.

(4) The untilt is natural, so $f^\flat(\varepsilon)^\sharp = f(\varepsilon^\sharp) = 1$. The map $W(f^\flat)$ sends $[\varepsilon]$ to $[f^\flat(\varepsilon)]$, and divided powers to divided powers by the proof of Proposition 2.5.29. So it sends the partial sums $s_N$ for $\varepsilon$ to the partial sums for $f^\flat(\varepsilon)$. The map of completions sends the limit of a Cauchy sequence to the limit of its image. The second claim is the case of the homomorphism $x \mapsto gx$.

(5) $(\varepsilon^p)^\sharp = (\varepsilon^\sharp)^p = 1$. In the Witt vectors of a perfect ring $\varphi([\varepsilon]) = [\varepsilon^p]$. Since $\varphi(j!) = j!$, the Frobenius sends $([\varepsilon] - 1)^{[j]}$ to $([\varepsilon^p] - 1)^{[j]}$, and we conclude as in part 4. $\square$

**Lemma 2.5.31 (the element $\varepsilon$).** Choose $z_n \in \mathbb{C}_p$ with $z_0 = 1$, $z_1$ a primitive $p$-th root of unity and $z_{n+1}^p = z_n$. Each $z_n$ lies in $\mathcal{O}_{\mathbb{C}_p}$. Let $\varepsilon \in \mathcal{O}_{\mathbb{C}_p}^\flat$ be the sequence of the classes of the $z_n$. Then $\varepsilon^\sharp = 1$ and $\varepsilon \ne 1$.

Lean: `Langlands.Padic.epsCp`, `Langlands.Padic.untilt_epsCp`, `Langlands.Padic.pow_p_sub_one_mem`, `Langlands.Padic.epsCp_ne_one`

*Proof.* We have $z_n^{p^n} = z_0 = 1$, so $|z_n| = 1$ and $\varepsilon^\sharp = \lim_n z_n^{p^n} = 1$. Let $x \in \mathcal{O}_{\mathbb{C}_p}$ with $x \equiv 1$ modulo $p$, and write $x = 1 + y$ with $y \in p\mathcal{O}_{\mathbb{C}_p}$. Then $x^p - 1 = \sum_{0 < i < p} \binom{p}{i} y^i + y^p$. Each $\binom{p}{i}$ with $0 < i < p$ is divisible by $p$, and $y^p \in p^2 \mathcal{O}_{\mathbb{C}_p}$, so $x^p \equiv 1$ modulo $p^2$. Suppose now that $\varepsilon = 1$. Then $z_2 \equiv 1$ modulo $p$, so $z_1 = z_2^p \equiv 1$ modulo $p^2$. But $z_1 - 1$ is a root of the Eisenstein polynomial $\Phi_p(1 + X)$ of degree $p - 1$, so $|z_1 - 1| = p^{-1/(p-1)} \ge p^{-1} > p^{-2}$. This is a contradiction. $\square$

The proof uses $z_2$ and not $z_1$, because for $p = 2$ we have $z_1 = -1 \equiv 1$ modulo $2$. From now on $\varepsilon$ is the element of Lemma 2.5.31 and $t = \log [\varepsilon] \in A_{\mathrm{cris}}(\mathcal{O}_{\mathbb{C}_p})$. This is Fontaine's $2\pi i$ of $p$-adic Hodge theory.

**Definition 2.5.32 ($B_{\mathrm{cris}}$ and crystalline representations).** Let $M$ act on $R$, let $\varepsilon \in R^\flat$ with $\varepsilon^\sharp = 1$, and let $t = \log [\varepsilon]$.
1. The ring $B_{\mathrm{cris}}(R)$ is the localization of $B_{\mathrm{cris}}^+(R)$ at the submonoid generated by the elements $gt$ for $g \in M$. Each $h \in M$ maps this submonoid into itself, since $h(gt) = (hg)t$, so $M$ acts on $B_{\mathrm{cris}}(R)$ by $\mathbb{Q}_p$-algebra homomorphisms.
2. We write $B_{\mathrm{cris}}$ for $B_{\mathrm{cris}}(\mathcal{O}_{\mathbb{C}_p})$ with $M = G_{\mathbb{Q}_p}$ and the $\varepsilon$ of Lemma 2.5.31.
3. A representation $V$ of $G_{\mathbb{Q}_p}$ on a $\mathbb{Q}_p$-vector space of finite dimension is *crystalline* if it is $B_{\mathrm{cris}}$-admissible. We write $D_{\mathrm{cris}}(V) = D_{B_{\mathrm{cris}}}(V)$.

Lean: `Langlands.Padic.bcrisSubmonoid`, `Langlands.Padic.Bcris`, `Langlands.Padic.bcrisMap`, `Langlands.Padic.smul_algebraMap_bcris`, `Langlands.Padic.BcrisCp`, `Langlands.Padic.IsCrystallineQp`, `Langlands.Padic.isCrystallineQp_trivial_of_nontrivial`

Fontaine defines $B_{\mathrm{cris}} = B_{\mathrm{cris}}^+[1/t]$. Part 2 of the next theorem gives $gt = \chi(g) t$ with $\chi(g) \in \mathbb{Z}_p^\times$, which is a unit in $B_{\mathrm{cris}}^+$. So inverting all the $gt$ is the same as inverting $t$, and the two definitions agree. Definition 2.5.32 does not need this formula to define the action. As in part 5 of Proposition 2.5.27, the trivial representation is crystalline as soon as $B_{\mathrm{cris}} \ne 0$.

**Theorem 2.5.33 (Fontaine).** Let $\chi : G_{\mathbb{Q}_p} \to \mathbb{Z}_p^\times$ be the cyclotomic character, with $g(z_n) = z_n^{\chi(g)}$ for all $n$.
1. For $a, b \in \mathcal{O}_{\mathbb{C}_p}^\flat$ with $a^\sharp = b^\sharp = 1$ we have $\log [ab] = \log [a] + \log [b]$. For $c \in \mathbb{Z}_p$ the power $\varepsilon^c$ is defined, and $\log [\varepsilon^c] = ct$.
2. $\varphi(t) = pt$, and $gt = \chi(g) t$ for $g \in G_{\mathbb{Q}_p}$.
3. The ring $A_{\mathrm{cris}}(\mathcal{O}_{\mathbb{C}_p})$ has no $p$-torsion, and $B_{\mathrm{cris}}^+$ embeds into $B_{\mathrm{dR}}^+(\mathcal{O}_{\mathbb{C}_p})$ compatibly with $G_{\mathbb{Q}_p}$. The image of $t$ generates the maximal ideal of $B_{\mathrm{dR}}^+$. In particular $t \ne 0$ and $B_{\mathrm{cris}} \ne 0$.
4. $B_{\mathrm{cris}}^{G_{\mathbb{Q}_p}} = \mathbb{Q}_p$, and $\dim_{\mathbb{Q}_p} D_{\mathrm{cris}}(V) \le \dim_{\mathbb{Q}_p} V$ for each $V$.

Lean: proved in part, see Theorem 2.5.56 and Remark 2.5.65.

*Outline of the proof.* (1) In $\mathbb{Q}[[X, Y]]$ we have $\log((1 + X)(1 + Y)) = \log(1 + X) + \log(1 + Y)$. Put $X = [a] - 1$ and $Y = [b] - 1$, so that $[ab] - 1 = X + Y + XY$. Both sides are $p$-adically convergent series in the divided powers $X^{[i]} Y^{[j]}$, because $(X + Y)^{[n]} = \sum_i X^{[i]} Y^{[n-i]}$ and $(XY)^{[n]} = n! \, X^{[n]} Y^{[n]}$. A rearrangement of the series then gives the identity in $A_{\mathrm{cris}}$. The element $\varepsilon - 1$ is topologically nilpotent in $\mathcal{O}_{\mathbb{C}_p}^\flat$, so $\varepsilon^c = \lim \varepsilon^{c_n}$ for integers $c_n \to c$, and the formula for $\log [\varepsilon^c]$ follows by continuity. (2) Part 5 of Proposition 2.5.30 and part 1 give $\varphi(t) = \log [\varepsilon^p] = pt$. The element $g$ acts on $\varepsilon$ term by term, so $g\varepsilon = \varepsilon^{\chi(g)}$, and part 4 of Proposition 2.5.30 gives $gt = \log [\varepsilon^{\chi(g)}] = \chi(g) t$. (3) and (4) are in the paper of Fontaine cited above, and in the book of Fontaine and Ouyang. The embedding comes from the fact that the divided powers of $\xi$ converge in $B_{\mathrm{dR}}^+$. Then $\theta(t) = \log(\varepsilon^\sharp) = 0$, and the image of $t$ is $\xi$ times a unit. $\square$

So $\mathbb{Q}_p(1)$, the line on which $G_{\mathbb{Q}_p}$ acts by $\chi$, is crystalline: the vector $t^{-1} \otimes e$ is invariant, since $g(t^{-1}) = \chi(g)^{-1} t^{-1}$. By a theorem of Faltings, the conjecture $C_{\mathrm{cris}}$ of Fontaine, the representation $V_p E = T_p E \otimes \mathbb{Q}_p$ of an elliptic curve $E$ over $\mathbb{Q}_p$ with good reduction is crystalline. For bad semistable reduction one needs a larger ring.

**Definition 2.5.34 (the Kummer elements and $B_{\mathrm{st}}$).**
1. Let $y_n$ and $p^\flat$ be as in Proposition 2.5.27. For $\sigma \in G_{\mathbb{Q}_p}$ put $w_n(\sigma) = \sigma(y_n) / y_n \in \mathbb{C}_p$. Let $\eta_\sigma \in \mathcal{O}_{\mathbb{C}_p}^\flat$ be the sequence of the classes of the $w_n(\sigma)$. The *Kummer element* of $\sigma$ is $\eta_\sigma$, and its logarithm is $\log [\eta_\sigma] \in A_{\mathrm{cris}}(\mathcal{O}_{\mathbb{C}_p})$.
2. For a commutative ring $A$ the *monodromy operator* on the polynomial ring $A[u]$ is $N = -d/du$.
3. The ring $B_{\mathrm{st}}(R)$ is the polynomial ring $B_{\mathrm{cris}}(R)[u]$ with the operator $N$. We write $B_{\mathrm{st}} = B_{\mathrm{st}}(\mathcal{O}_{\mathbb{C}_p})$.

Lean: `Langlands.Padic.kummerRoots`, `Langlands.Padic.kummerFlat`, `Langlands.Padic.kummerLog`, `Langlands.Padic.monodromy`, `Langlands.Padic.Bst`, `Langlands.Padic.BstCp`

The variable $u$ stands for $\log [p^\flat]$. This logarithm does not converge in $B_{\mathrm{cris}}^+$, because $\theta([p^\flat]) = p$ is not $1$, so Fontaine adds it as a new variable. Part 1 of Definition 2.5.34 needs part 1 of the next proposition.

**Proposition 2.5.35 (the Kummer cocycle and the monodromy).** Let $\sigma, \tau \in G_{\mathbb{Q}_p}$.
1. Each $w_n(\sigma)$ is a $p^n$-th root of unity, $w_{n+1}(\sigma)^p = w_n(\sigma)$, $|w_n(\sigma)| = 1$, and $\eta_\sigma^\sharp = 1$. So $\log [\eta_\sigma]$ is defined.
2. $\sigma(p^\flat) = \eta_\sigma \, p^\flat$ in $\mathcal{O}_{\mathbb{C}_p}^\flat$.
3. $\eta_{\sigma\tau} = \sigma(\eta_\tau) \, \eta_\sigma$.
4. On $A[u]$ we have $N(u) = -1$, $N(b) = 0$ for $b \in A$ and $N(xy) = x N(y) + y N(x)$. If $A$ contains $\mathbb{Q}$, then the kernel of $N$ is $A$. In particular $B_{\mathrm{st}}^{N = 0} = B_{\mathrm{cris}}$.

Lean: `Langlands.Padic.kummerRoots_pow`, `Langlands.Padic.kummerRoots_succ_pow`, `Langlands.Padic.norm_kummerRoots`, `Langlands.Padic.untilt_kummerFlat`, `Langlands.Padic.preTiltMap_pFlat`, `Langlands.Padic.kummerFlat_mul`, `Langlands.Padic.monodromy_X`, `Langlands.Padic.monodromy_C`, `Langlands.Padic.monodromy_mul`

*Proof.* (1) The $y_n$ are nonzero, and $\sigma(y_n)^{p^n} = \sigma(p) = p = y_n^{p^n}$, so $w_n(\sigma)^{p^n} = 1$. Next $w_{n+1}(\sigma)^p = \sigma(y_{n+1}^p) / y_{n+1}^p = w_n(\sigma)$. A root of unity has absolute value $1$, so $w_n(\sigma) \in \mathcal{O}_{\mathbb{C}_p}$, and the sequence of its classes lies in the tilt. Its untilt is $\lim_n w_n(\sigma)^{p^n} = 1$.

(2) The element $\sigma$ acts on the tilt term by term. The $n$-th term of $\sigma(p^\flat)$ is the class of $\sigma(y_n) = w_n(\sigma) y_n$, which is the $n$-th term of $\eta_\sigma p^\flat$.

(3) By part 2, $(\sigma\tau)(p^\flat) = \sigma(\eta_\tau p^\flat) = \sigma(\eta_\tau) \, \eta_\sigma \, p^\flat$, and also $(\sigma\tau)(p^\flat) = \eta_{\sigma\tau} p^\flat$. The tilt is a domain and $p^\flat \ne 0$, by Proposition 2.5.27, so we may cancel $p^\flat$.

(4) The first three claims are the rules for the derivative of polynomials. If $N(\sum_i b_i u^i) = -\sum_{i \ge 1} i \, b_i u^{i-1} = 0$, then $i \, b_i = 0$ for $i \ge 1$, and $b_i = 0$ since $i$ is a unit in $A$. The ring $B_{\mathrm{cris}}$ is a $\mathbb{Q}_p$-algebra by part 5 of Proposition 2.5.29. $\square$

Define $c(\sigma) \in \mathbb{Z}_p$ by $\sigma(y_n) = z_n^{c(\sigma)} y_n$ for all $n$. Then $w_n(\sigma) = z_n^{c(\sigma)}$, so $\eta_\sigma = \varepsilon^{c(\sigma)}$. The function $c : G_{\mathbb{Q}_p} \to \mathbb{Z}_p$ is the *Kummer cocycle* of $p$. Since $\sigma(\varepsilon^a) = \varepsilon^{\chi(\sigma) a}$, part 3 of Proposition 2.5.35 says that
$$c(\sigma\tau) = c(\sigma) + \chi(\sigma) c(\tau),$$
so $c$ is a $1$-cocycle with values in $\mathbb{Z}_p(1)$. By part 1 of Theorem 2.5.33, $\log [\eta_\sigma] = c(\sigma) t$. This is the formula that defines the action of $G_{\mathbb{Q}_p}$ on $B_{\mathrm{st}}$.

**Definition 2.5.36 (semistable representations).** Let $G_{\mathbb{Q}_p}$ act on $B_{\mathrm{st}} = B_{\mathrm{cris}}[u]$ by its action on the coefficients and by $g(u) = u + c(g) t$, and let $\varphi$ act by its action on $B_{\mathrm{cris}}$ and by $\varphi(u) = pu$. A representation $V$ of $G_{\mathbb{Q}_p}$ on a $\mathbb{Q}_p$-vector space of finite dimension is *semistable* if it is $B_{\mathrm{st}}$-admissible. We write $D_{\mathrm{st}}(V) = D_{B_{\mathrm{st}}}(V)$, with the operators $\varphi \otimes 1$ and $N \otimes 1$. A representation is *potentially semistable* if its restriction to $G_L$ is semistable for a finite extension $L$ of $\mathbb{Q}_p$, where one uses the same rings with $G_L$ in place of $G_{\mathbb{Q}_p}$.

Lean: see Definition 2.5.62 and Remark 2.5.65.

The formula is an action: $g(h(u)) = g(u + c(h)t) = u + c(g)t + c(h)\chi(g)t = u + c(gh)t$ by the cocycle relation and part 2 of Theorem 2.5.33. The operator $N$ commutes with $G_{\mathbb{Q}_p}$, since $N(g(u)) = -1 = g(N(u))$, and $N\varphi = p\varphi N$, since $N(\varphi(u)) = -p = p\varphi(N(u))$. Fontaine proved that $B_{\mathrm{st}}^{G_{\mathbb{Q}_p}} = \mathbb{Q}_p$ and that $\dim_{\mathbb{Q}_p} D_{\mathrm{st}}(V) \le \dim_{\mathbb{Q}_p} V$. By part 4 of Proposition 2.5.35, $D_{\mathrm{cris}}(V) = D_{\mathrm{st}}(V)^{N = 0}$. So a crystalline representation is semistable, and a semistable representation $V$ is crystalline if and only if $N = 0$ on $D_{\mathrm{st}}(V)$. Fontaine attached to each potentially semistable $V$ a Weil-Deligne representation $\mathrm{WD}(V)$, whose monodromy comes from $N$ and whose restriction to inertia records the extension $L$. This is the $p$-adic replacement for Grothendieck's monodromy theorem, see Volume 6, Remark 2.3.9. Each de Rham representation is potentially semistable, by the $p$-adic monodromy theorem of Berger.

**Example 2.5.37 (the Kummer extension is semistable and not crystalline).** Let $V$ have the basis $e_1, e_2$, and let $G_{\mathbb{Q}_p}$ act by
$$g e_1 = \chi(g) e_1, \qquad g e_2 = e_2 + c(g) e_1.$$
This is a representation by the cocycle relation: $g(h e_2) = e_2 + c(g)e_1 + c(h)\chi(g)e_1 = e_2 + c(gh)e_1$. It is the extension of $\mathbb{Q}_p$ by $\mathbb{Q}_p(1)$ with the Kummer class of $p$, and by Tate's uniformization it is $V_p E$ for the Tate curve $E = \mathbb{G}_m / p^\mathbb{Z}$, which has split multiplicative reduction. We use Theorem 2.5.33 and Definition 2.5.36. In $B_{\mathrm{st}} \otimes V$ put
$$f_1 = t^{-1} \otimes e_1, \qquad f_2 = 1 \otimes e_2 - u t^{-1} \otimes e_1.$$
Then $g f_1 = \chi(g)^{-1} t^{-1} \otimes \chi(g) e_1 = f_1$, and
$$g f_2 = 1 \otimes (e_2 + c(g) e_1) - \frac{u + c(g)t}{\chi(g) t} \otimes \chi(g) e_1 = 1 \otimes e_2 - ut^{-1} \otimes e_1 = f_2.$$
The vectors $f_1, f_2$ are linearly independent over $B_{\mathrm{st}}$, since the matrix of their coordinates is triangular with the units $t^{-1}$ and $1$ on the diagonal. So $\dim D_{\mathrm{st}}(V) \ge 2$, and by the bound of Definition 2.5.36 $D_{\mathrm{st}}(V) = \mathbb{Q}_p f_1 \oplus \mathbb{Q}_p f_2$. So $V$ is semistable. The operator $N$ gives $N f_1 = 0$ and $N f_2 = -N(u) t^{-1} \otimes e_1 = f_1$. So $N \ne 0$ on $D_{\mathrm{st}}(V)$, and $D_{\mathrm{cris}}(V) = \ker N = \mathbb{Q}_p f_1$ has dimension $1$. So $V$ is not crystalline. Its Weil-Deligne representation has trivial restriction to inertia and $N \ne 0$, which is the Galois side of a twist of the Steinberg representation.

**Remark 2.5.38 (the Lean status).** The file `Langlands/Padic/DeRhamNonzero.lean` proves Proposition 2.5.27, and so the predicate `Langlands.Padic.IsDeRhamQp` of `Langlands/Padic/DeRhamQp.lean` has no open hypothesis for the trivial representation. The file `Langlands/Padic/Crystalline.lean` contains Definitions 2.5.28 and 2.5.32, parts 2 and 3 of Definition 2.5.34, Proposition 2.5.29, parts 1 to 3 of Proposition 2.5.30, Lemma 2.5.31 without the claim $\varepsilon \ne 1$, and part 4 of Proposition 2.5.35. The file `Langlands/Padic/Semistable.lean` contains the claim $\varepsilon \ne 1$, parts 4 and 5 of Proposition 2.5.30, part 1 of Definition 2.5.34 and parts 1 to 3 of Proposition 2.5.35. In Lean the series of $\log [\varepsilon]$ is the limit of the subsequence $(s_{pk})$ of Proposition 2.5.30, and the definitions take an arbitrary monoid $M$ that acts on $R$. The following points are not in Lean.
1. *The functional equation.* Part 1 of Theorem 2.5.33 is not proved. So the formulas $\varphi(t) = pt$, $gt = \chi(g)t$ and $\log [\eta_\sigma] = c(\sigma)t$ are not proved, and $B_{\mathrm{cris}}$ in Lean inverts all the $gt$ and not only $t$.
2. *Nontriviality.* The claim $t \ne 0$ is not proved. So `Langlands.Padic.isCrystallineQp_trivial_of_nontrivial` has the hypothesis that $B_{\mathrm{cris}}$ is not the zero ring.
3. *The semistable side.* The Frobenius and the Galois action on $B_{\mathrm{st}}$, and so Definition 2.5.36 and the predicates for semistable and potentially semistable representations, are not in Lean. Example 2.5.37 is not in Lean.
4. *The invariants.* Part 4 of Theorem 2.5.33 and the bound $\dim D_B(V) \le \dim V$ are not proved. The predicate `Langlands.Padic.IsAdmissible` uses the rank `Module.finrank` over $B^G$, which is the dimension when $B^G$ is a field.

### Inertial types and Serre weight multiplicities

The other side of the Breuil-Mezard conjecture is a computation in the representation theory of $GL_2(\mathbb{Z}_p)$. An inertial type $\tau$ gives, by a theorem of Henniart, a representation $\sigma(\tau)$ of $GL_2(\mathbb{Z}_p)$. A Hodge-Tate type $\lambda$ gives an algebraic representation. The tensor product $\sigma(\lambda, \tau)$ has a stable lattice, and the numbers $n_{a,b}(\lambda, \tau)$ count the Serre weights in the reduction of this lattice. This subsection defines these numbers and proves that they do not depend on the lattice. The reference is the paper of Breuil and Mezard, "Multiplicités modulaires et représentations de $GL_2(\mathbb{Z}_p)$ et de $\mathrm{Gal}(\bar{\mathbb{Q}}_p/\mathbb{Q}_p)$ en $\ell = p$", Duke Math. J. 115 (2002), with the appendix of Henniart. For the Brauer-Nesbitt theorem see Serre, "Linear representations of finite groups", Chapter 15.

We first count composition factors. Let $A$ be a ring and $M$ an $A$-module of finite length. By the Jordan-Hölder theorem, two composition series $0 = M_0 \subset M_1 \subset \dots \subset M_r = M$ have the same factors $M_i / M_{i-1}$ up to order and isomorphism.

**Definition 2.5.39 (Jordan-Hölder multiplicity).** Let $S$ be an $A$-module. The *multiplicity* $[M : S]$ of $S$ in $M$ is the number of indices $i$ with $M_i / M_{i-1} \cong S$, for a composition series $(M_i)$ of $M$. If $M$ does not have finite length, we put $[M : S] = 0$.

Lean: `Langlands.compositionCount`, `Langlands.compositionCount_eq_of_equivalent`, `Langlands.jhMultiplicity`, `Langlands.jhMultiplicity_eq`

The Jordan-Hölder theorem says that the count does not depend on the series. When $S$ is simple, $[M : S]$ is the usual multiplicity. A representation of a group $G$ on a vector space $V$ over a field $k$ is a module over the group algebra $k[G]$, and we write $[V : W]$ for the multiplicity of $W$ in $V$ as $k[G]$-modules. If $\dim_k V$ is finite, then $V$ has finite length, since a chain of subrepresentations has at most $\dim_k V + 1$ terms.

**Lemma 2.5.40 (properties of the multiplicity).** Let $S$ be an $A$-module.
1. If $M$ is simple, then $[M : S] = 1$ if $M \cong S$ and $[M : S] = 0$ otherwise. If $M = 0$, then $[M : S] = 0$.
2. If $M \cong M'$, then $[M : S] = [M' : S]$.
3. Let $0 \to N \to M \to P \to 0$ be an exact sequence, with $M$ of finite length. Then $[M : S] = [N : S] + [P : S]$.
4. For a linear map $f : M \to N$, with $M$ of finite length, $[M : S] = [\ker f : S] + [\operatorname{im} f : S]$.
5. Let $f : M \to N$ and $g : N \to M$ be linear maps, with $M$ and $N$ of finite length, $\operatorname{im} f = \ker g$ and $\operatorname{im} g = \ker f$. Then $[M : S] = [N : S]$.

Lean: `Langlands.jhMultiplicity_of_isSimpleModule`, `Langlands.jhMultiplicity_of_subsingleton`, `Langlands.jhMultiplicity_congr`, `Langlands.jhMultiplicity_eq_add_of_exact`, `Langlands.jhMultiplicity_eq_ker_add_range`, `Langlands.jhMultiplicity_eq_of_range_eq_ker`

*Proof.* (1) A simple module has the composition series $0 \subset M$ with the single factor $M$. The zero module has the series $0$ with no factors.

(2) An isomorphism $e : M \to M'$ sends a composition series of $M$ to a composition series of $M'$, and it induces isomorphisms of the factors.

(3) We identify $N$ with a submodule of $M$ and $P$ with $M/N$. Submodules and quotients of a module of finite length have finite length. Take composition series $(N_i)_{i \le r}$ of $N$ and $(P_j)_{j \le s}$ of $P$, and let $M_j$ be the inverse image of $P_j$ in $M$. Then
$$0 = N_0 \subset \dots \subset N_r = N = M_0 \subset M_1 \subset \dots \subset M_s = M$$
is a composition series of $M$, because $M_j / M_{j-1} \cong P_j / P_{j-1}$. Its factors are the factors of $(N_i)$ and the factors of $(P_j)$.

(4) Apply part 3 to $0 \to \ker f \to M \to \operatorname{im} f \to 0$.

(5) By part 4 and part 2,
$$[M : S] = [\ker f : S] + [\operatorname{im} f : S] = [\operatorname{im} g : S] + [\ker g : S] = [N : S]. \qquad \square$$

Now let $O$ be a local ring with maximal ideal $\mathfrak{m}$ and residue field $k = O / \mathfrak{m}$. For the main results $O$ is a discrete valuation ring with a uniformizer $\varpi$ and the fraction field $C$, for example the ring of integers $\mathcal{O}_E$ of a finite extension $E$ of $\mathbb{Q}_p$.

**Definition 2.5.41 (reductions, stable lattices and Serre weights).** Let $G$ be a group.
1. Let $\sigma$ be a representation of $G$ on an $O$-module $L$. The *reduction* of $\sigma$ is the representation $\bar\sigma$ of $G$ on the $k$-vector space $L / \mathfrak{m} L$. For a representation $W$ of $G$ over $k$ put $n_W(\sigma) = [L / \mathfrak{m}L : W]$.
2. Let $\rho$ be a representation of $G$ on a $C$-vector space $V$ of finite dimension. A *lattice* in $V$ is a finitely generated $O$-submodule $L$ that spans $V$ over $C$. The lattice $L$ is *stable* if $\rho(g) L \subseteq L$ for all $g \in G$. Then $\rho$ restricts to a representation $\rho_L$ of $G$ on $L$, and we put $n_W(\rho, L) = n_W(\rho_L)$.
3. Let $\theta : G \to GL_2(k)$ be a homomorphism, and let $a, b \ge 0$ be integers. Let $\mathrm{Sym}^a k^2$ be the space of the homogeneous polynomials of degree $a$ in $x, y$ over $k$, with $GL_2(k)$ acting by the linear substitution of the variables. The *Serre weight* $\sigma_{a,b}$ is the representation $\mathrm{Sym}^a k^2 \otimes \det^b$ of $G$ through $\theta$. We write $n_{a,b}(\rho, L) = n_{\sigma_{a,b}}(\rho, L)$.

Lean: `Langlands.Reduction`, `Langlands.reduceEnd`, `Langlands.reduction`, `Langlands.reductionMultiplicity`, `Langlands.IsStable`, `Langlands.IsStableLattice`, `Langlands.latticeRep`, `Langlands.latticeMultiplicity`, `Langlands.serreWeightRep`, `Langlands.latticeSerreMultiplicity`

For the Breuil-Mezard conjecture $G = GL_2(\mathbb{Z}_p)$ and $\theta$ is the reduction $GL_2(\mathbb{Z}_p) \to GL_2(\mathbb{F}_p) \subseteq GL_2(k)$. Then the $\sigma_{a,b}$ with $0 \le a \le p - 1$ and $0 \le b \le p - 2$ are simple (Exercise 16) and pairwise non-isomorphic, and they are all the simple representations of $GL_2(\mathbb{F}_p)$ over $k$, up to isomorphism. This is a classical result in the modular representation theory of $GL_2(\mathbb{F}_p)$.

**Lemma 2.5.42 (existence of stable lattices).** Let $O$ be a complete discrete valuation ring, let $G$ be a compact group and let $\rho : G \to GL(V)$ be continuous, for the topology of $GL(V)$ that a basis of $V$ gives. Then $V$ has a stable lattice.

Lean: not proved, see Remark 2.5.53.

*Proof.* Let $L_0$ be the $O$-span of a basis of $V$. The set $H = \{g \in G : \rho(g) L_0 = L_0\}$ is a subgroup. It contains the inverse image under $\rho$ of the open subgroup $GL(L_0) = GL_n(O)$ of $GL_n(C)$, so it is open. Since $G$ is compact, $H$ has finite index. Let $g_1, \dots, g_r$ be representatives of $G/H$, and put $L = \sum_i \rho(g_i) L_0$. This is a finitely generated $O$-module that contains $L_0$, so it is a lattice. For $g \in G$, the elements $g g_i$ are $g_{j(i)} h_i$ with $h_i \in H$, and $j$ is a permutation, so $\rho(g) L = \sum_i \rho(g_{j(i)}) L_0 = L$. $\square$

**Theorem 2.5.43 (Brauer-Nesbitt for lattices).** Let $O$ be a discrete valuation ring with the uniformizer $\varpi$ and the fraction field $C$. Let $\rho$ be a representation of a group $G$ on a $C$-vector space $V$ of finite dimension, and let $L$ and $L'$ be stable lattices. Then $n_W(\rho, L) = n_W(\rho, L')$ for each representation $W$ of $G$ over $k$. In particular $n_{a,b}(\rho, L)$ does not depend on $L$, and we write it $n_{a,b}(\rho)$.

Lean: `Langlands.reductionMultiplicity_eq_of_comp`, `Langlands.latticeMultiplicity_eq_of_smul_le`, `Langlands.latticeMultiplicity_eq_of_pow_smul_le`, `Langlands.exists_pow_smul_le`, `Langlands.latticeMultiplicity_eq_of_isStableLattice`, `Langlands.serreMultiplicityIndependent`, `Langlands.serreMultiplicity`, `Langlands.serreMultiplicity_eq_latticeSerreMultiplicity`, `Langlands.serreMultiplicityIndependent_integer`

*Proof.* All the $O$-submodules of $V$ have no $\varpi$-torsion, since $\varpi$ is a unit in $C$. A finitely generated $O$-module $L$ has a reduction $L/\varpi L$ of finite dimension over $k$, so the reductions have finite length as representations. The proof has three steps.

*Step 1.* Let $L' \subseteq L$ be stable finitely generated submodules with $\varpi L \subseteq L'$. Then $n_W(\rho_L) = n_W(\rho_{L'})$. Let $i : L' \to L$ be the inclusion and $j : L \to L'$ the map $x \mapsto \varpi x$. Both commute with $G$, and $i \circ j$ and $j \circ i$ are the multiplication by $\varpi$. Let $\bar\imath : L'/\varpi L' \to L/\varpi L$ and $\bar\jmath : L/\varpi L \to L'/\varpi L'$ be the induced maps. Then
$$\operatorname{im} \bar\imath = (L' + \varpi L)/\varpi L = L'/\varpi L, \qquad \ker \bar\jmath = \{x \in L : \varpi x \in \varpi L'\}/\varpi L = L'/\varpi L,$$
where we use that $\varpi x \in \varpi L'$ implies $x \in L'$, since there is no $\varpi$-torsion. In the same way
$$\operatorname{im} \bar\jmath = \varpi L/\varpi L', \qquad \ker \bar\imath = (L' \cap \varpi L)/\varpi L' = \varpi L/\varpi L'.$$
So $\operatorname{im} \bar\imath = \ker \bar\jmath$ and $\operatorname{im} \bar\jmath = \ker \bar\imath$. These are maps of $k[G]$-modules, and part 5 of Lemma 2.5.40 gives the claim.

*Step 2.* Let $L' \subseteq L$ be stable submodules with $L$ finitely generated and $\varpi^m L \subseteq L'$ for some $m \ge 0$. Then $n_W(\rho_L) = n_W(\rho_{L'})$. Put $\Lambda_n = L' + \varpi^n L$ for $0 \le n \le m$. These are stable, $\Lambda_0 = L$ and $\Lambda_m = L'$. They are finitely generated, because $O$ is noetherian and they are submodules of $L$. We have $\Lambda_{n+1} \subseteq \Lambda_n$ and $\varpi \Lambda_n = \varpi L' + \varpi^{n+1} L \subseteq \Lambda_{n+1}$. Step 1 applies to each pair $\Lambda_{n+1} \subseteq \Lambda_n$.

*Step 3.* Let $L$ and $L'$ be stable lattices. Let $v_1, \dots, v_r$ generate $L$. Each $v_i$ is a $C$-linear combination of elements of $L'$, since $L'$ spans $V$. Each element of $C$ is $\varpi^{-e} u$ with $u \in O$, so there is $m$ with $\varpi^m v_i \in L'$ for all $i$, and then $\varpi^m L \subseteq L'$. The intersection $L \cap L'$ is stable, and $\varpi^m L \subseteq L \cap L' \subseteq L$. By Step 2, $n_W(\rho_L) = n_W(\rho_{L \cap L'})$. In the same way $n_W(\rho_{L'}) = n_W(\rho_{L \cap L'})$. $\square$

The reductions of two stable lattices need not be isomorphic. Only their composition factors agree (Exercise 15). This is why the Breuil-Mezard conjecture uses the multiplicities and not the reductions.

**Example 2.5.44 (the trivial representation).** Let $\rho$ be the trivial representation of $G$ on $C$, with the stable lattice $O$. The reduction $O/\mathfrak{m}$ is the trivial representation $k$, which is simple. A Serre weight $\sigma_{a,b}$ with $a \ge 1$ has dimension $a + 1 \ge 2$, so it is not isomorphic to $k$, and $n_{a,b}(\rho) = 0$. The weight $\sigma_{0,b}$ is the character $\det^b \circ \theta$, so $n_{0,b}(\rho) = 1$ if $\det(\theta(g))^b = 1$ for all $g$, and $n_{0,b}(\rho) = 0$ otherwise. In particular $n_{0,0}(\rho) = 1$. For $G = GL_2(\mathbb{Z}_p)$ and the reduction map $\theta$, the determinant maps $G$ onto $\mathbb{F}_p^\times$, which is cyclic of order $p - 1$. So $n_{0,b}(\rho) = 1$ if and only if $p - 1$ divides $b$.

Lean: `Langlands.reductionTrivialEquiv`, `Langlands.reductionMultiplicity_trivial`, `Langlands.reductionMultiplicity_trivial_of_ne_zero`, `Langlands.reductionMultiplicity_trivial_zero`

We now come to the types. Let $K$ be a non-archimedean local field with the ring of integers $\mathcal{O}_K$, the Weil group $W_K$ and the inertia group $I_K \subseteq W_K$, see Volume 6, Definition 2.1.1. Recall that $I_K$ is an open compact subgroup of $W_K$.

**Definition 2.5.45 (inertial types).** Let $m \ge 1$.
1. An *inertial representation* of dimension $m$ is a homomorphism $\tau : I_K \to GL_m(\mathbb{C})$ for which there is a homomorphism $r : W_K \to GL_m(\mathbb{C})$ with open kernel and with $r|_{I_K} = \tau$.
2. Two inertial representations $\tau$ and $\tau'$ are *isomorphic* if there is $g \in GL_m(\mathbb{C})$ with $\tau'(i) = g \tau(i) g^{-1}$ for all $i \in I_K$. This is an equivalence relation. An *inertial type* is an equivalence class.
3. Let $(r, N)$ be a Weil-Deligne representation of dimension $m$, see Volume 6, Definition 2.2.1. Its *inertial type* is the class of $r|_{I_K}$. Isomorphic Weil-Deligne representations have the same inertial type.

Lean: `Langlands.InertialRep`, `Langlands.InertialRep.Iso`, `Langlands.InertialRep.setoid`, `Langlands.InertialType`, `Langlands.InertialType.mk`, `Langlands.WeilDeligneRep.inertialRep`, `Langlands.WDIso.inertialType`, `Langlands.WDIso.inertialType_mk`, `Langlands.WDIso.HasZeroMonodromy`

**Lemma 2.5.46 (inertial representations have finite image).** Let $\tau$ be an inertial representation. Then $\ker \tau$ is open in $I_K$, and the image of $\tau$ is finite.

Lean: `Langlands.InertialRep.isOpen_ker`

*Proof.* Let $r$ extend $\tau$. Then $\ker \tau = I_K \cap \ker r$, which is open in $I_K$ because $\ker r$ is open in $W_K$. The group $I_K$ is compact, so its open subgroup $\ker \tau$ has finite index, and the image $I_K / \ker \tau$ is finite. $\square$

The Lean file proves only the first claim. By Grothendieck's monodromy theorem, each $\ell$-adic representation of $G_K$ with $\ell \ne p$ gives a Weil-Deligne representation, and so an inertial type. For $\ell = p$ the same holds for a potentially semistable representation, through Fontaine's functor $\mathrm{WD}$ of the previous subsection, after a choice of an isomorphism $\bar{\mathbb{Q}}_p \cong \mathbb{C}$.

Let $\mathrm{rec}$ be a bijection from the isomorphism classes of the irreducible smooth representations of $GL_2(K)$ over $\mathbb{C}$ to the isomorphism classes of the Weil-Deligne representations of dimension $2$. The main example is the local Langlands correspondence of Volume 6, Theorem 3.3.1. A smooth representation $\sigma$ of $GL_2(\mathcal{O}_K)$ *occurs in* a smooth representation $\pi$ of $GL_2(K)$ if there is a nonzero linear map $f : \sigma \to \pi$ with $f(\sigma(g) v) = \pi(g) f(v)$ for all $g \in GL_2(\mathcal{O}_K)$.

**Definition 2.5.47 (Henniart types).** Let $\tau$ be an inertial type of dimension $2$, and let $\sigma$ be an irreducible smooth representation of $GL_2(\mathcal{O}_K)$ of finite dimension.
1. $\sigma$ is a *type* for $\tau$ if, for each irreducible smooth representation $\pi$ of $GL_2(K)$ of infinite dimension, $\sigma$ occurs in $\pi$ if and only if $\mathrm{rec}(\pi)$ has the inertial type $\tau$.
2. $\sigma$ is a *crystalline type* for $\tau$ if, for each such $\pi$, $\sigma$ occurs in $\pi$ if and only if $\mathrm{rec}(\pi) = (r, N)$ has the inertial type $\tau$ and $N = 0$.

These properties depend only on the isomorphism class of $\sigma$.

Lean: `Langlands.HasTypeHom`, `Langlands.IsHenniartType`, `Langlands.IsHenniartCrysType`, `Langlands.HasTypeHom.of_iso`, `Langlands.IsHenniartType.of_iso`, `Langlands.IsHenniartCrysType.of_iso`, `Langlands.SmoothRep.IsIrreducible.of_iso`

The last claim holds because an isomorphism $\sigma \cong \sigma'$ composed with a nonzero map $\sigma' \to \pi$ is a nonzero map $\sigma \to \pi$. The condition is only on the representations of infinite dimension. The characters $\chi \circ \det$ of $GL_2(K)$ must be excluded. For example, for an unramified $\chi$ the Weil-Deligne representation $\mathrm{rec}(\chi \circ \det)$ has the trivial inertial type and $N = 0$, but $\chi \circ \det$ contains only the trivial representation of $GL_2(\mathcal{O}_K)$, and not the representation $\mathrm{st}$ of Example 2.5.49.

**Theorem 2.5.48 (Henniart).** Let $\mathrm{rec}$ be the local Langlands correspondence for $GL_2(K)$. Each inertial type $\tau$ of dimension $2$ has a type $\sigma(\tau)$ and a crystalline type $\sigma^{\mathrm{cr}}(\tau)$, and they are unique up to isomorphism.

Lean: `Langlands.HasHenniartTypes`, not proved.

*Outline of the proof.* The existence comes from the theory of types of Bushnell and Kutzko, see [BH06]. One sorts the representations $\pi$ by their restriction to inertia, through Volume 6, Proposition 3.3.3: the principal series with a given restriction of the characters to $\mathcal{O}_K^\times$, the twists of the Steinberg representation, and the supercuspidal representations. For each class one writes down a representation of $GL_2(\mathcal{O}_K)$ that is induced from an open compact subgroup and checks that it detects the class. The uniqueness is the main result of Henniart's appendix to the paper of Breuil and Mezard. $\square$

**Example 2.5.49 (the trivial type).** Let $\tau = 1 \oplus 1$ be the trivial inertial type of dimension $2$, and let $\bar G = GL_2(k_K)$, where $k_K$ is the residue field of $K$ with $q$ elements. The space of the functions $\bar B \backslash \bar G \to \mathbb{C}$, for the upper triangular subgroup $\bar B$, is the trivial representation $1$ plus the Steinberg representation $\mathrm{st}$ of dimension $q$, see Volume 6, Definition 1.5.3. We inflate both to $GL_2(\mathcal{O}_K)$. The $\pi$ of infinite dimension with $\mathrm{rec}(\pi)|_{I_K}$ trivial are the unramified principal series, with $N = 0$, and the unramified twists of the Steinberg representation of $GL_2(K)$, with $N \ne 0$. An unramified principal series has a nonzero vector fixed by $GL_2(\mathcal{O}_K)$, see Volume 6, Section 1.2, and its vectors fixed by the Iwahori subgroup generate a copy of $1 \oplus \mathrm{st}$. A twist of the Steinberg representation contains $\mathrm{st}$ and does not contain $1$. So
$$\sigma(1 \oplus 1) = \mathrm{st}, \qquad \sigma^{\mathrm{cr}}(1 \oplus 1) = 1.$$

Now let $K = \mathbb{Q}_p$, let $E$ be a finite extension of $\mathbb{Q}_p$ with the ring of integers $\mathcal{O}_E$ and the residue field $k$, and let $\bar{\mathbb{Q}}_p$ be an algebraic closure of $E$. A *Hodge-Tate type* is a pair $\lambda = (\lambda_1, \lambda_2)$ of integers with $\lambda_1 > \lambda_2$.

**Definition 2.5.50 (the representations $\sigma(\lambda, \tau)$).** Let $C$ be a field that contains $\mathbb{Q}_p$, and let $\iota : \mathbb{C} \to C$ be a ring homomorphism. Let $\lambda$ be a Hodge-Tate type and let $\sigma$ be a smooth representation of $GL_2(\mathbb{Z}_p)$ over $\mathbb{C}$ of finite dimension.
1. For $a \ge 0$ and $b \in \mathbb{Z}$, the representation $\mathrm{Sym}^a C^2 \otimes \det^b$ of $GL_2(\mathbb{Z}_p)$ is the action on the homogeneous polynomials of degree $a$ over $C$, through $GL_2(\mathbb{Z}_p) \subseteq GL_2(C)$, multiplied by $\det^b$.
2. The representation $\iota_* \sigma$ over $C$ has the matrices $\iota(\sigma(g))$ in a fixed basis of $\sigma$.
3. Put
$$\sigma(\lambda, \sigma) = \mathrm{Sym}^{\lambda_1 - \lambda_2 - 1} C^2 \otimes \det^{\lambda_2} \otimes_C \iota_* \sigma.$$
For $\sigma = \sigma(\tau)$ we write $\sigma(\lambda, \tau)$, and for $\sigma = \sigma^{\mathrm{cr}}(\tau)$ we write $\sigma^{\mathrm{cr}}(\lambda, \tau)$.
4. For $C = E$, the integers $n_{a,b}(\lambda, \tau)$ and $n^{\mathrm{cr}}_{a,b}(\lambda, \tau)$ are the multiplicities $n_{a,b}$ of Theorem 2.5.43 for $\sigma(\lambda, \tau)$ and $\sigma^{\mathrm{cr}}(\lambda, \tau)$, with $O = \mathcal{O}_E$ and $\theta$ the reduction $GL_2(\mathbb{Z}_p) \to GL_2(k)$.

Lean: `Langlands.symDetRep`, `Langlands.symDetRep_natCast`, `Langlands.baseChangeRep`, `Langlands.glIntegersTo`, `Langlands.sigmaLambdaTau`, `Langlands.typeMultiplicity`, `Langlands.coeffEmbedding`, `Langlands.coeffRed`, `Langlands.charP_residueField`

Part 4 needs a comment. The representation $\sigma(\tau)$ is smooth and of finite dimension, so its kernel is open and its image is finite. A representation of a finite group over $\mathbb{C}$ can be written with matrices over a number field, so $\sigma(\tau)$ is defined over $\bar{\mathbb{Q}}$, and so over $\bar{\mathbb{Q}}_p$ after a choice of an embedding $\bar{\mathbb{Q}} \to \bar{\mathbb{Q}}_p$. We take $E$ so large that $\sigma(\tau)$ is defined over $E$. Then $\sigma(\lambda, \tau)$ is a representation of the compact group $GL_2(\mathbb{Z}_p)$ over $E$. It is continuous, so it has a stable lattice by Lemma 2.5.42, and $n_{a,b}(\lambda, \tau)$ does not depend on the lattice by Theorem 2.5.43. It does not depend on $E$ either, because a lattice over $\mathcal{O}_E$ gives a lattice over $\mathcal{O}_{E'}$ for $E' \supseteq E$, with the reduction extended from $k$ to $k'$.

**Conjecture 2.5.51 (Breuil and Mezard).** Let $p$ be a prime and $\bar\rho : G_{\mathbb{Q}_p} \to GL_2(k)$ continuous. There are integers $\mu_{a,b}(\bar\rho) \ge 0$, for $0 \le a \le p - 1$ and $0 \le b \le p - 2$, such that for each Hodge-Tate type $\lambda$ and each inertial type $\tau$
$$e\big(R^\square(\lambda, \tau, \bar\rho) \otimes_{\mathcal{O}_E} k\big) = \sum_{a,b} n_{a,b}(\lambda, \tau) \, \mu_{a,b}(\bar\rho).$$
The same integers give the multiplicities of the potentially crystalline rings $R^{\square, \mathrm{cr}}(\lambda, \tau, \bar\rho)$, with $n^{\mathrm{cr}}_{a,b}(\lambda, \tau)$ in place of $n_{a,b}(\lambda, \tau)$.

Lean: `Langlands.BreuilMezardGL2Qp`, a shape only, see Remark 2.5.53.

Kisin proved the conjecture for most $\bar\rho$ with $p > 2$, with the $p$-adic local Langlands correspondence of Colmez and with global arguments. Paškūnas gave a local proof, and Hu and Tan completed the remaining cases with $p > 2$. The integers $\mu_{a,b}(\bar\rho)$ are not arbitrary: they are the multiplicities of the special fibers of the crystalline rings of small weight, as the next example shows.

**Example 2.5.52 (crystalline lifts of small weight).** Let $\tau$ be the trivial type and $\lambda = (k_0 - 1, 0)$ with $k_0 \ge 2$. By Example 2.5.49, $\sigma^{\mathrm{cr}}(\tau) = 1$, so $\sigma^{\mathrm{cr}}(\lambda, \tau) = \mathrm{Sym}^{k_0 - 2} E^2$. The lattice $\mathrm{Sym}^{k_0 - 2} \mathcal{O}_E^2$ is stable, and its reduction is $\mathrm{Sym}^{k_0 - 2} k^2 = \sigma_{k_0 - 2, 0}$.
1. If $2 \le k_0 \le p + 1$, then $\sigma_{k_0 - 2, 0}$ is simple by Exercise 16. So $n^{\mathrm{cr}}_{a,b}(\lambda, \tau)$ is $1$ for $(a, b) = (k_0 - 2, 0)$ and $0$ otherwise, and the conjecture says that the multiplicity of the special fiber of $R^{\square, \mathrm{cr}}(\lambda, 1, \bar\rho)$ is $\mu_{k_0 - 2, 0}(\bar\rho)$. This is the way to compute $\mu_{a,0}(\bar\rho)$. For $k_0 \le p$ the theory of Fontaine and Laffaille shows that this ring is zero or formally smooth over $\mathcal{O}_E$, so $\mu_{k_0 - 2, 0}(\bar\rho)$ is $0$ or $1$.
2. If $k_0 = p + 2$, then the reduction is $\mathrm{Sym}^p k^2$. The span of $x^p$ and $y^p$ is a subrepresentation, since $(\alpha x + \gamma y)^p = \alpha x^p + \gamma y^p$ for $\alpha, \gamma \in \mathbb{F}_p$. The map $\ell \mapsto \ell^p$ on the linear forms is an isomorphism of $\sigma_{1,0}$ onto it. The quotient $Q$ has the basis of the classes of $x^i y^{p-i}$ for $0 < i < p$. An element of $GL_2(\mathbb{F}_p)$ with the eigenvalues $\alpha, \beta$ in $\bar{\mathbb{F}}_p$ acts on $Q$ with the eigenvalues $\alpha^i \beta^{p-i} = \alpha\beta \cdot \alpha^{i-1}\beta^{p-1-i}$ for $0 < i < p$, which are the eigenvalues on $\sigma_{p-2,1}$. By the theory of Brauer characters, see Serre, "Linear representations of finite groups", Chapter 18, $Q$ and $\sigma_{p-2,1}$ have the same composition factors, and $\sigma_{p-2,1}$ is simple. The two weights are not isomorphic. For $p \ne 3$ their dimensions $2$ and $p - 1$ differ, and for $p = 3$ an element of order $8$ with the eigenvalues $\alpha, \alpha^3$ acts on $\sigma_{1,1}$ with the eigenvalues $\alpha^5, \alpha^7$. So $n^{\mathrm{cr}}_{1,0} = n^{\mathrm{cr}}_{p-2,1} = 1$, where for $p = 2$ we read $\sigma_{0,1}$ as $\sigma_{0,0}$, and the other multiplicities are $0$. The conjecture predicts $e = \mu_{1,0}(\bar\rho) + \mu_{p-2,1}(\bar\rho)$.

**Remark 2.5.53 (the Lean status).** The file `Langlands/Local/BreuilMezardTypes.lean` contains Definitions 2.5.39, 2.5.41, 2.5.45, 2.5.47 and 2.5.50, part 1 of Lemma 2.5.40, Lemma 2.5.46 without the claim on the image, the statement of Theorem 2.5.48 and the claim $n_{0,0} = 1$ of Example 2.5.44. The file `Langlands/Local/BreuilMezardLattices.lean` proves parts 2 to 5 of Lemma 2.5.40, Theorem 2.5.43 and the rest of Example 2.5.44. In Lean the multiplicity $[M : S]$ is defined for an arbitrary module $S$, and it is $0$ when $M$ has no composition series. The function `Langlands.serreMultiplicity` uses a chosen stable lattice, and `Langlands.serreMultiplicity_eq_latticeSerreMultiplicity` says that the choice does not matter. The following points are not in Lean.
1. *Existence of lattices.* Lemma 2.5.42 is not proved. The representations in Lean have no topology, and a representation with no stable lattice has $n_{a,b} = 0$ by definition.
2. *Henniart's theorem.* `Langlands.HasHenniartTypes` is a statement for an arbitrary bijection $\mathrm{rec}$. It is not proved, and it has content only for the local Langlands correspondence, which is not in Lean. Example 2.5.49 is not in Lean.
3. *The coefficients.* `Langlands.typeMultiplicity` moves $\sigma$ to $C$ with a ring homomorphism $\iota : \mathbb{C} \to C$. There is no such homomorphism to a finite extension $E$ of $\mathbb{Q}_p$: its image would be an algebraically closed subfield of $E$, and so $E$ would contain all the roots $p^{1/n}$, which is false since the valuation of $E$ is discrete. A homomorphism to $\bar{\mathbb{Q}}_p$ exists, by a choice of an isomorphism of fields $\mathbb{C} \cong \bar{\mathbb{Q}}_p$. But the ring of integers of $\bar{\mathbb{Q}}_p$ is not a discrete valuation ring, so Theorem 2.5.43 does not apply to it. The Lean files prove Theorem 2.5.43 over $\mathcal{O}_E$ as `Langlands.serreMultiplicityIndependent_integer`, with the maps `Langlands.coeffEmbedding` of $E$ into $\bar{\mathbb{Q}}_p$ and `Langlands.coeffRed` of $\mathbb{Z}_p$ to the residue field $k$, but they do not yet descend $\sigma(\tau)$ to $E$.
4. *The conjecture.* Conjecture 2.5.51 is not stated with these definitions. The field `typeMultiplicity` of `Langlands.BreuilMezardData` could be defined with `Langlands.typeMultiplicity` once item 3 is resolved, and the field `deformationMultiplicity` needs the semistable conditions of Remark 2.5.38, item 3. Example 2.5.52 is not in Lean.

### The functional equation of the logarithm

This subsection proves part 1 of Theorem 2.5.33 for a product of two elements, and the formula $\varphi(t) = pt$ of part 2. The proof does not rearrange infinite series. It compares the partial sums of the three logarithms with a polynomial identity in one variable, and it bounds the error with divided powers. The Lean file is `Langlands/Padic/LogTeich.lean`. As before, $R$ is a ring of the kind of Definition 2.5.26, and all positive integers are units in $W(R^\flat)[1/p]$.

**Lemma 2.5.54 (the truncated logarithm).** Let $A$ be a commutative ring and let $(a_j)_{j \ge 0}$ be elements of $A$ with $(j + 1) a_j = (-1)^j$ for all $j$. Let $N \ge 1$. For a polynomial $q \in A[X]$ put $\ell_N(q) = \sum_{j < N} a_j q^{j+1}$, and for $x, y \in A$ put
$$D(X) = \ell_N\big((1 + xX)(1 + yX) - 1\big) - \ell_N(xX) - \ell_N(yX) \in A[X].$$
1. $\ell_N(q)' = q' \sum_{j < N} (-q)^j$, and $X^N$ divides the derivative $D'$.
2. If $1, 2, \dots, N$ are units in $A$, then the coefficient $D_d$ of $X^d$ in $D$ is $0$ for $d \le N$.
3. For $d > N$ the coefficient is $D_d = \sum a_j \binom{j+1}{k} (xy)^k (x + y)^{j+1-k}$, where the sum runs over the pairs $(j, k)$ with $j < N$, $k \le j + 1$ and $j + 1 + k = d$.
4. Assume that $1, 2, \dots, N$ are units in $A$. Let $J \subseteq A$ be an additive subgroup that contains each term $a_j \binom{j+1}{k} (xy)^k (x + y)^{j+1-k}$ with $j < N$, $k \le j + 1$ and $j + 1 + k > N$. Then, with $\ell_N(z) = \sum_{j < N} a_j z^{j+1}$ for $z \in A$,
$$\ell_N\big((1 + x)(1 + y) - 1\big) - \ell_N(x) - \ell_N(y) \in J.$$

Lean: `Langlands.Padic.logPoly`, `Langlands.Padic.derivative_logPoly`, `Langlands.Padic.geom_neg_mul`, `Langlands.Padic.logDefect`, `Langlands.Padic.X_pow_dvd_derivative_logDefect`, `Langlands.Padic.coeff_logDefect_eq_zero`, `Langlands.Padic.pow_eq_sum_monomial`, `Langlands.Padic.coeff_logDefect_mem`, `Langlands.Padic.eval_one_logDefect`, `Langlands.Padic.logTrunc_defect_mem`

*Proof.* (1) The derivative of $a_j q^{j+1}$ is $(j + 1) a_j q^j q' = (-q)^j q'$. Put $S(z) = \sum_{j < N} (-z)^j$, so that $S(z)(1 + z) = 1 - (-z)^N$. Let $q = (1 + xX)(1 + yX) - 1$. Then $1 + q = (1 + xX)(1 + yX)$ and $q' = x(1 + yX) + y(1 + xX)$. We multiply $D' = q' S(q) - x S(xX) - y S(yX)$ by $1 + q$ and find
$$(1 + q) D' = q'\big(1 - (-q)^N\big) - x(1 + yX)\big(1 - (-xX)^N\big) - y(1 + xX)\big(1 - (-yX)^N\big) = -q'(-q)^N + x(1 + yX)(-xX)^N + y(1 + xX)(-yX)^N.$$
The polynomial $X$ divides $q$, so $X^N$ divides the right side. The constant term of $1 + q$ is $1$, so $1 + q$ is a unit in $A[X]/(X^N)$, and $X^N$ divides $D'$.

(2) The constant term of $D$ is $0$, because $q$, $xX$ and $yX$ have constant term $0$. For $1 \le d \le N$ the coefficient of $X^{d-1}$ in $D'$ is $d D_d$. It is $0$ by part 1, since $d - 1 < N$. Since $d$ is a unit, $D_d = 0$.

(3) We have $q = X\big(xyX + (x + y)\big)$, so the binomial formula gives
$$q^n = \sum_{k=0}^{n} \binom{n}{k} (xy)^k (x + y)^{n-k} X^{n+k}.$$
The polynomials $\ell_N(xX)$ and $\ell_N(yX)$ have degree at most $N$, so they do not contribute to $D_d$ for $d > N$. Take $n = j + 1$ and collect the terms of degree $d$.

(4) The left side is $D(1) = \sum_d D_d$. By part 2 only the $D_d$ with $d > N$ contribute, and by part 3 each of them is a sum of terms in $J$. $\square$

The lemma replaces the identity $\log((1 + X)(1 + Y)) = \log(1 + X) + \log(1 + Y)$ of formal power series by a finite statement about polynomials. The error of the truncation sits in the degrees above $N$, and part 3 gives it in closed form. We now take $A = W(R^\flat)[1/p]$. Let $a, b \in R^\flat$ with $a^\sharp = b^\sharp = 1$, put $x = [a] - 1$ and $y = [b] - 1$, and let $a_j = (-1)^j \, j! / (j+1)!$. Then $[ab] - 1 = (1 + x)(1 + y) - 1$. The term $\ell_j$ of Proposition 2.5.30 is $a_j ([\varepsilon] - 1)^{j+1}$, so the partial sum $s_N(\varepsilon)$ of that proposition is $\ell_N([\varepsilon] - 1)$. We write $p^m A_{\mathrm{cris}}^0(R)$ for the set of the elements $p^m c$ with $c \in A_{\mathrm{cris}}^0(R)$.

**Lemma 2.5.55 (the divided power estimate).** Let $a, b, x, y$ and $a_j$ be as above, and let $j, k, m \ge 0$ with $k \le j + 1$ and $pm \le j$. Then
$$a_j \binom{j+1}{k} (xy)^k (x + y)^{j+1-k} = (-1)^j \, j! \; x^{[k]} \, (x + y)^{[j+1-k]} \, y^k,$$
and this element lies in $p^m A_{\mathrm{cris}}^0(R)$.

Lean: `Langlands.Padic.dpowLoc`, `Langlands.Padic.factorial_mul_dpowLoc`, `Langlands.Padic.dpowLoc_mem`, `Langlands.Padic.logCoeff`, `Langlands.Padic.logCoeff_mul_factorial`, `Langlands.Padic.logCoeff_mul`, `Langlands.Padic.isUnit_succ_loc`, `Langlands.Padic.coe_logTerm`, `Langlands.Padic.pPowAcrisZero`, `Langlands.Padic.logCoeff_mul_mem`

*Proof.* We have $\binom{j+1}{k} \, k! \, (j + 1 - k)! = (j + 1)!$, so $a_j \binom{j+1}{k} = (-1)^j \, j! / \big(k! \, (j + 1 - k)!\big)$. Since $x^k / k! = x^{[k]}$ and $(x + y)^{j+1-k} / (j + 1 - k)! = (x + y)^{[j+1-k]}$, this gives the identity. By part 1 of Proposition 2.5.30 the elements $x$ and $y$ lie in $\ker \theta$, and so does $x + y$. So both divided powers lie in $A_{\mathrm{cris}}^0(R)$. Since $pm \le j$, we have $j! = p^m c$ with $c \in \mathbb{Z}$, as in the proof of part 2 of Proposition 2.5.30. So the element is $p^m$ times $(-1)^j c \, x^{[k]} (x + y)^{[j+1-k]} y^k \in A_{\mathrm{cris}}^0(R)$. $\square$

The coefficient $a_j \binom{j+1}{k}$ divides by $k! \, (j + 1 - k)!$, and the two divided powers absorb these two factorials. The factor $j!$ that is left is the source of the divisibility by $p^m$. The power $y^k$ needs no division.

**Theorem 2.5.56 (the functional equation of the logarithm).** Let $a, b \in R^\flat$ with $a^\sharp = b^\sharp = 1$.
1. Let $m \ge 0$ and $N > 2pm$. Then $s_N(ab) - s_N(a) - s_N(b) \in p^m A_{\mathrm{cris}}^0(R)$.
2. $\log [ab] = \log [a] + \log [b]$ in $A_{\mathrm{cris}}(R)$.

Lean: `Langlands.Padic.logPartial_mul_sub_mem`, `Langlands.Padic.logTeich_mul`

*Proof.* (1) By the remark before Lemma 2.5.55, the left side is $\ell_N((1 + x)(1 + y) - 1) - \ell_N(x) - \ell_N(y)$. We apply part 4 of Lemma 2.5.54 with $J = p^m A_{\mathrm{cris}}^0(R)$, which is an additive subgroup. Take a term with $j < N$, $k \le j + 1$ and $j + 1 + k > N$. Then $2(j + 1) \ge j + 1 + k > N > 2pm$, so $j + 1 > pm$ and $pm \le j$. Lemma 2.5.55 shows that the term lies in $J$.

(2) By Proposition 2.5.30 and Remark 2.5.38, $\log [\varepsilon]$ is the class in the $p$-adic completion of the sequence $(s_{pk}(\varepsilon))_{k \ge 0}$, and $s_{pk}(\varepsilon) \equiv s_{pn}(\varepsilon)$ modulo $p^n A_{\mathrm{cris}}^0(R)$ for $k \ge n$. Put $d_k = s_{pk}(ab) - s_{pk}(a) - s_{pk}(b)$. Then also $d_k \equiv d_n$ modulo $p^n A_{\mathrm{cris}}^0(R)$ for $k \ge n$. For each $n$ we have $p(2n + 1) > 2pn$, so part 1 gives $d_{2n+1} \in p^n A_{\mathrm{cris}}^0(R)$, and then $d_n \in p^n A_{\mathrm{cris}}^0(R)$. So the image of $(d_k)$ in each quotient $A_{\mathrm{cris}}^0(R) / p^n A_{\mathrm{cris}}^0(R)$ is $0$, and its class in the completion is $0$. This class is $\log [ab] - \log [a] - \log [b]$. $\square$

**Corollary 2.5.57 (consequences of the functional equation).** Let $\varepsilon \in R^\flat$ with $\varepsilon^\sharp = 1$.
1. $\log [1] = 0$, and $\log [\varepsilon^n] = n \log [\varepsilon]$ for each integer $n \ge 0$.
2. $\varphi(\log [\varepsilon]) = p \log [\varepsilon]$. In particular $\varphi(t) = pt$.
3. For $R = \mathcal{O}_{\mathbb{C}_p}$ and $\sigma, \tau \in G_{\mathbb{Q}_p}$, the Kummer elements of Definition 2.5.34 satisfy $\log [\eta_{\sigma\tau}] = \sigma(\log [\eta_\tau]) + \log [\eta_\sigma]$ and $\log [\eta_1] = 0$.

Lean: `Langlands.Padic.logTeich_congr`, `Langlands.Padic.logTeich_one`, `Langlands.Padic.logTeich_pow`, `Langlands.Padic.acrisFrob_logTeich_eq`, `Langlands.Padic.kummerLog_mul`, `Langlands.Padic.kummerLog_one`

*Proof.* (1) The untilt is multiplicative, so $(\varepsilon^n)^\sharp = 1$. Theorem 2.5.56 with $a = b = 1$ gives $\log [1] = 2 \log [1]$, so $\log [1] = 0$. This is the case $n = 0$, and Theorem 2.5.56 with $a = \varepsilon^n$ and $b = \varepsilon$ gives the step from $n$ to $n + 1$.

(2) By part 5 of Proposition 2.5.30 and part 1, $\varphi(\log [\varepsilon]) = \log [\varepsilon^p] = p \log [\varepsilon]$.

(3) By part 3 of Proposition 2.5.35, $\eta_{\sigma\tau} = \sigma(\eta_\tau) \, \eta_\sigma$, and $\sigma(\eta_\tau)^\sharp = \sigma(\eta_\tau^\sharp) = 1$. Theorem 2.5.56 and part 4 of Proposition 2.5.30 give $\log [\eta_{\sigma\tau}] = \log [\sigma(\eta_\tau)] + \log [\eta_\sigma] = \sigma(\log [\eta_\tau]) + \log [\eta_\sigma]$. For $\sigma = \tau = 1$ this says $\log [\eta_1] = 2 \log [\eta_1]$. $\square$

In Lean the element $\log [\varepsilon]$ carries a proof of $\varepsilon^\sharp = 1$ as an argument, and `Langlands.Padic.logTeich_congr` says that it depends only on $\varepsilon$. So part 1 of Theorem 2.5.33 is now proved for products, and for the powers $\varepsilon^c$ with $c \in \mathbb{N}$. The case $c \in \mathbb{Z}_p$ needs the continuity of $\varepsilon \mapsto \log [\varepsilon]$, which is not in Lean. Of part 2, the formula $\varphi(t) = pt$ is proved. The formula $gt = \chi(g) t$ is not, because $\chi(g)$ is a $p$-adic integer and not a natural number. Part 3 of the corollary is the cocycle relation of $\sigma \mapsto \log [\eta_\sigma]$ with values in $A_{\mathrm{cris}}(\mathcal{O}_{\mathbb{C}_p})$. It holds without the formula $\log [\eta_\sigma] = c(\sigma) t$, and the next subsection shows that it is all that the action on $B_{\mathrm{st}}$ needs.

### The Frobenius, the Galois action and the monodromy of $B_{\mathrm{st}}$

This subsection constructs the Galois action and the Frobenius on $B_{\mathrm{st}}$ that Definition 2.5.36 uses, and it proves the relations between them and $N$. The Lean file is `Langlands/Padic/Semistable2.lean`. There are two steps. First we attach a ring $B[u]$ with an action to an arbitrary cocycle. Then we take the cocycle $\sigma \mapsto \log [\eta_\sigma]$.

**Proposition 2.5.58 (the Frobenius of $B_{\mathrm{cris}}$).** Let a monoid $M$ act on $R$, let $\varepsilon \in R^\flat$ with $\varepsilon^\sharp = 1$ and $t = \log [\varepsilon]$, and let $S$ be the submonoid of $B_{\mathrm{cris}}^+(R)$ generated by the $gt$, so that $B_{\mathrm{cris}}(R) = S^{-1} B_{\mathrm{cris}}^+(R)$ as in Definition 2.5.32.
1. $\varphi(gt) = p \cdot gt$ for $g \in M$.
2. The Frobenius $\varphi$ of $B_{\mathrm{cris}}^+(R)$ extends to a unique ring endomorphism $\varphi$ of $B_{\mathrm{cris}}(R)$.
3. $\varphi(gx) = g \varphi(x)$ for $g \in M$ and $x \in B_{\mathrm{cris}}(R)$.

Lean: `Langlands.Padic.bcrisPlusFrob_smul_logTeich`, `Langlands.Padic.bcrisSubmonoid_le_frob`, `Langlands.Padic.bcrisFrob`, `Langlands.Padic.bcrisFrob_algebraMap`, `Langlands.Padic.bcrisFrob_smul`

*Proof.* (1) By part 5 of Proposition 2.5.29 and part 2 of Corollary 2.5.57, $\varphi(gt) = g\varphi(t) = g(pt) = p \cdot gt$.

(2) By the universal property of the localization, it suffices that the composite $B_{\mathrm{cris}}^+(R) \to B_{\mathrm{cris}}^+(R) \to B_{\mathrm{cris}}(R)$ of $\varphi$ and the localization map sends each $s \in S$ to a unit. The elements that it sends to units form a submonoid. It contains each generator $gt$, since $\varphi(gt) = p \cdot gt$ is a product of two units of $B_{\mathrm{cris}}(R)$. So it contains $S$.

(3) Both $\varphi \circ g$ and $g \circ \varphi$ are ring endomorphisms of $B_{\mathrm{cris}}(R)$. They agree on $B_{\mathrm{cris}}^+(R)$ by part 5 of Proposition 2.5.29. A ring homomorphism out of a localization is determined by its restriction to the ring. $\square$

**Definition 2.5.59 (cocycles and the ring $B[u]_c$).** Let a monoid $M$ act on a commutative ring $B$ by ring endomorphisms.
1. A *cocycle* is a map $c : M \to B$ with $c(1) = 0$ and $c(gh) = g\, c(h) + c(g)$ for all $g, h \in M$.
2. Let $c$ be a cocycle. Let $g \in M$ act on the polynomial ring $B[u]$ by $g\big(\sum_i b_i u^i\big) = \sum_i g(b_i) \, (u + c(g))^i$. We write $B[u]_c$ for $B[u]$ with this action.
3. Let $\varphi$ be a ring endomorphism of $B$ and let $q \in B$. The *Frobenius* of $B[u]_c$ is $\varphi\big(\sum_i b_i u^i\big) = \sum_i \varphi(b_i) \, (qu)^i$.
4. The *monodromy* of $B[u]_c$ is $N = -d/du$, as in Definition 2.5.34.

Lean: `Langlands.Padic.BstCocycle`, `Langlands.Padic.bstMap`, `Langlands.Padic.bstMap_apply`, `Langlands.Padic.BstPoly`, `Langlands.Padic.bstPolyAction`, `Langlands.Padic.bstC`, `Langlands.Padic.bstU`, `Langlands.Padic.bstFrob`, `Langlands.Padic.bstN`

The condition $c(1) = 0$ follows from the relation with $g = h = 1$, since $1$ acts trivially on $B$. The Lean structure lists it as a separate field. The order in the relation, $c(gh) = g\,c(h) + c(g)$, is the one of Corollary 2.5.57, part 3.

**Proposition 2.5.60 (the relations in $B[u]_c$).** In the situation of Definition 2.5.59 the following hold.
1. Each $g \in M$ acts on $B[u]_c$ by a ring endomorphism that extends its action on $B$ and sends $u$ to $u + c(g)$. The element $1$ acts as the identity, and $(gh)f = g(hf)$. If $B$ is a $K$-algebra and $M$ acts $K$-linearly on $B$, then $M$ acts $K$-linearly on $B[u]_c$.
2. The Frobenius is a ring endomorphism of $B[u]_c$ that extends $\varphi$ and sends $u$ to $qu$. If $\varphi(gb) = g\varphi(b)$, $gq = q$ and $\varphi(c(g)) = q\, c(g)$ for all $g \in M$ and $b \in B$, then $\varphi(gf) = g\varphi(f)$ for all $f \in B[u]_c$.
3. $N(u) = -1$, $N(b) = 0$ for $b \in B$, $N(gf) = g N(f)$ and $N(\varphi(f)) = q\, \varphi(N(f))$ for all $g \in M$ and $f \in B[u]_c$.

Lean: `Langlands.Padic.bstMap_C`, `Langlands.Padic.bstMap_X`, `Langlands.Padic.bstMap_one`, `Langlands.Padic.bstMap_mul`, `Langlands.Padic.smul_bstC`, `Langlands.Padic.smul_bstU`, `Langlands.Padic.bstPoly_smulCommClass`, `Langlands.Padic.bstFrob_bstC`, `Langlands.Padic.bstFrob_bstU`, `Langlands.Padic.bstFrob_smul`, `Langlands.Padic.bstN_bstU`, `Langlands.Padic.bstN_bstC`, `Langlands.Padic.monodromy_bstMap`, `Langlands.Padic.bstN_smul`, `Langlands.Padic.monodromy_bstFrob`, `Langlands.Padic.bstN_bstFrob`

*Proof.* (1) The map of $g$ is the composite of the map $g$ on the coefficients and the substitution $u \mapsto u + c(g)$. Both are ring homomorphisms. A ring homomorphism out of $B[u]$ is determined by its values on $B$ and on $u$, so it suffices to check the two action laws there. On $B$ they are the laws of the action on $B$. On $u$ we have $1 \cdot u = u + c(1) = u$ and
$$g(hu) = g\big(u + c(h)\big) = u + c(g) + g\,c(h) = u + c(gh) = (gh)u.$$
The $K$-linearity holds because $g$ fixes the image of $K$ in $B$.

(2) The first claim holds by construction. For the second claim, $\varphi \circ g$ and $g \circ \varphi$ are ring homomorphisms, so we compare them on $B$ and on $u$. On $b \in B$ both give $g\varphi(b)$. On $u$,
$$\varphi(gu) = \varphi\big(u + c(g)\big) = qu + \varphi(c(g)) = qu + q\,c(g), \qquad g\varphi(u) = g(q) \, g(u) = q\big(u + c(g)\big).$$

(3) The first two claims are part 4 of Proposition 2.5.35. Write $f^g$ for $f$ with $g$ applied to the coefficients. Then $gf = f^g(u + c(g))$, and the chain rule gives $\frac{d}{du} f^g(u + c(g)) = (f')^g(u + c(g))$, since $u + c(g)$ has derivative $1$. In the same way $\frac{d}{du} f^\varphi(qu) = q \, (f')^\varphi(qu)$. Multiply by $-1$. $\square$

The relation $N\varphi = q\varphi N$ needs no hypothesis. The commutation of $\varphi$ with $M$ needs $\varphi(c(g)) = q\,c(g)$, which is a property of the cocycle.

**Proposition 2.5.61 (cocycles with values in $A_{\mathrm{cris}}$).** Let $M$, $R$ and $\varepsilon$ be as in Proposition 2.5.58, let $k : M \to A_{\mathrm{cris}}(R)$ be a cocycle, and let $c(g) \in B_{\mathrm{cris}}(R)$ be the image of $k(g)$.
1. The map $c$ is a cocycle with values in $B_{\mathrm{cris}}(R)$.
2. Assume that $\varphi(k(g)) = p\, k(g)$ for all $g$. Let $B_{\mathrm{cris}}(R)[u]_c$ have the Frobenius of Definition 2.5.59 for the $\varphi$ of Proposition 2.5.58 and $q = p$. Then $\varphi(c(g)) = p\,c(g)$, $\varphi(gf) = g\varphi(f)$, and $N\varphi = p\varphi N$.
3. Let $\eta : M \to R^\flat$ with $\eta_g^\sharp = 1$ for all $g$, and assume that $k(g) = \log [\eta_g]$ is a cocycle. Then the assumption of part 2 holds.

Lean: `Langlands.Padic.smul_algebraMap_algebraMap`, `Langlands.Padic.algebraMap_cocycle`, `Langlands.Padic.BstCocycle.ofAcris`, `Langlands.Padic.BstCocycle.frob_ofAcris`, `Langlands.Padic.BstCocycle.frob_ofAcris_logTeich`, `Langlands.Padic.bstFrobBcris`, `Langlands.Padic.bstFrobBcris_bstU`, `Langlands.Padic.bstFrobBcris_bstC`, `Langlands.Padic.bstN_bstFrobBcris`, `Langlands.Padic.bstFrobBcris_smul`, `Langlands.Padic.bstFrobBcris_smul_ofAcris`

*Proof.* (1) The maps $A_{\mathrm{cris}}(R) \to B_{\mathrm{cris}}^+(R) \to B_{\mathrm{cris}}(R)$ are ring homomorphisms that commute with $M$, by Proposition 2.5.29 and Definition 2.5.32.

(2) The Frobenius of $B_{\mathrm{cris}}(R)$ extends the Frobenius of $A_{\mathrm{cris}}(R)$, by part 2 of Proposition 2.5.58 and part 4 of Proposition 2.5.29. So $\varphi(c(g)) = p\,c(g)$. The element $p$ is fixed by $M$, and $\varphi$ commutes with $M$ by part 3 of Proposition 2.5.58. Proposition 2.5.60 gives the rest.

(3) Part 2 of Corollary 2.5.57 with $\varepsilon = \eta_g$. $\square$

**Definition 2.5.62 ($B_{\mathrm{st}}$ and semistable representations).** Let $R = \mathcal{O}_{\mathbb{C}_p}$, $M = G_{\mathbb{Q}_p}$, and let $\varepsilon$ be the element of Lemma 2.5.31.
1. The *Kummer cocycle* in $B_{\mathrm{cris}}$ is the map $\sigma \mapsto \log [\eta_\sigma]$. It is a cocycle by part 3 of Corollary 2.5.57 and part 1 of Proposition 2.5.61.
2. The ring $B_{\mathrm{st}}$ is $B_{\mathrm{cris}}[u]_c$ for the Kummer cocycle $c$, with the Frobenius for $q = p$ and the monodromy $N$. So $\sigma(u) = u + \log [\eta_\sigma]$ and $\varphi(u) = pu$.
3. A representation $V$ of $G_{\mathbb{Q}_p}$ on a $\mathbb{Q}_p$-vector space of finite dimension is *semistable* if it is $B_{\mathrm{st}}$-admissible.
4. For an intermediate field $\mathbb{Q}_p \subseteq L \subseteq \bar{\mathbb{Q}}_p$ let $G_L \subseteq G_{\mathbb{Q}_p}$ be the subgroup of the elements that fix $L$. It acts on $B_{\mathrm{st}}$ by restriction. The representation $V$ is *potentially semistable* if there is such an $L$ of finite degree over $\mathbb{Q}_p$ for which the restriction of $V$ to $G_L$ is $B_{\mathrm{st}}$-admissible.

Lean: `Langlands.Padic.kummerCocycle`, `Langlands.Padic.BstGal`, `Langlands.Padic.uBst`, `Langlands.Padic.smul_uBst`, `Langlands.Padic.bstFrobCp`, `Langlands.Padic.bstFrobCp_uBst`, `Langlands.Padic.IsSemistableQp`, `Langlands.Padic.galFixing`, `Langlands.Padic.IsPotentiallySemistableQp`

As in Fontaine's theory, the ring $B_{\mathrm{st}}$ is the same for all $L$, and only the group changes. The ring of part 2 is the ring $B_{\mathrm{st}}$ of Definition 2.5.34 with an action. Remark 2.5.65 compares it with Definition 2.5.36.

**Theorem 2.5.63 (Fontaine's relations on $B_{\mathrm{st}}$).** Let $\sigma \in G_{\mathbb{Q}_p}$ and $f \in B_{\mathrm{st}}$.
1. $\varphi(\log [\eta_\sigma]) = p \log [\eta_\sigma]$ in $A_{\mathrm{cris}}(\mathcal{O}_{\mathbb{C}_p})$.
2. $\varphi(\sigma f) = \sigma \varphi(f)$.
3. $N(\sigma f) = \sigma N(f)$.
4. $N(\varphi(f)) = p\, \varphi(N(f))$.

Lean: `Langlands.Padic.acrisFrob_kummerLog`, `Langlands.Padic.bstFrobCp_smul`, `Langlands.Padic.bstN_smul_cp`, `Langlands.Padic.bstN_bstFrobCp`

*Proof.* (1) is part 2 of Corollary 2.5.57 with $\varepsilon = \eta_\sigma$. (2) follows from parts 2 and 3 of Proposition 2.5.61. (3) and (4) are part 3 of Proposition 2.5.60 with $q = p$. $\square$

So $\varphi \otimes 1$ and $N \otimes 1$ commute with $G_{\mathbb{Q}_p}$ on $B_{\mathrm{st}} \otimes V$, and they preserve $D_{\mathrm{st}}(V)$. On $D_{\mathrm{st}}(V)$ they satisfy $N\varphi = p\varphi N$. This is the structure of a $(\varphi, N)$-module of Fontaine.

**Lemma 2.5.64 (admissibility along a surjection).** Let $K$ be a field, let $f : H \to G$ be a surjective homomorphism of groups, let $G$ act on a $K$-algebra $B$, and let $H$ act on $B$ by $hb = f(h)b$.
1. For a representation $\rho$ of $G$ on a $K$-vector space of finite dimension, $\rho \circ f$ is $B$-admissible if and only if $\rho$ is $B$-admissible.
2. A semistable representation is potentially semistable.
3. If $B_{\mathrm{cris}} \ne 0$, then the trivial representation $\mathbb{Q}_p$ of $G_{\mathbb{Q}_p}$ is semistable.

Lean: `Langlands.Padic.isAdmissible_comp_iff`, `Langlands.Padic.IsSemistableQp.isPotentiallySemistableQp`, `Langlands.Padic.isSemistableQp_trivial_of_nontrivial`

*Proof.* (1) The element $h$ acts on $B \otimes_K V$ as $f(h)$. Since $f$ is surjective, an element is fixed by $H$ if and only if it is fixed by $G$. So $B^H = B^G$, and $D_B(\rho \circ f) = D_B(\rho)$ as modules over this ring.

(2) Take $L = \mathbb{Q}_p$. Then $G_L = G_{\mathbb{Q}_p}$, and the inclusion $G_L \to G_{\mathbb{Q}_p}$ is surjective. Apply part 1.

(3) The ring $B_{\mathrm{st}} = B_{\mathrm{cris}}[u]$ is not zero. As in part 5 of Proposition 2.5.27, $D_{B_{\mathrm{st}}}(\mathbb{Q}_p) = B_{\mathrm{st}}^{G_{\mathbb{Q}_p}}$ is free of rank $1$ over itself, and this ring contains $1 \ne 0$. $\square$

**Remark 2.5.65 (comparison with Definition 2.5.36, and the Lean status).** Definition 2.5.36 uses $\sigma(u) = u + c(\sigma) t$, and Definition 2.5.62 uses $\sigma(u) = u + \log [\eta_\sigma]$. The two agree by the formula $\log [\eta_\sigma] = c(\sigma) t$, which follows from part 1 of Theorem 2.5.33 for exponents in $\mathbb{Z}_p$. With this formula the two rings are the same, with the same action of $G_{\mathbb{Q}_p}$, the same $\varphi$ and the same $N$. The Lean definition does not need the formula: the cocycle relation of Corollary 2.5.57 suffices for the action, and part 1 of Theorem 2.5.63 suffices for the Frobenius. The two files of the last two subsections update Remark 2.5.38. Item 1 of that remark is now proved for products and for the powers $\varepsilon^n$ with $n \in \mathbb{N}$, and the formula $\varphi(t) = pt$ is proved. Item 3 is now in Lean, apart from Example 2.5.37. The following points are still not in Lean.
1. *The exponents in $\mathbb{Z}_p$.* The formulas $\log [\varepsilon^c] = ct$ for $c \in \mathbb{Z}_p$, $gt = \chi(g) t$ and $\log [\eta_\sigma] = c(\sigma) t$ are not proved. So $B_{\mathrm{cris}}$ in Lean still inverts all the $gt$.
2. *Nontriviality.* The claim $t \ne 0$ is not proved. So part 3 of Lemma 2.5.64 has the hypothesis $B_{\mathrm{cris}} \ne 0$.
3. *The invariants.* Fontaine's theorem $B_{\mathrm{st}}^{G_{\mathbb{Q}_p}} = \mathbb{Q}_p$ and the bound $\dim D_{\mathrm{st}}(V) \le \dim V$ are not proved. So the claim of Definition 2.5.36 that a crystalline representation is semistable is not proved in Lean, and the predicate for semistable representations uses the rank over $B_{\mathrm{st}}^{G}$ as in item 4 of Remark 2.5.38.
4. *Example 2.5.37.* It needs the formulas of item 1 and the invertibility of $t$, and it is not in Lean.

### Serre weights and the full statement of the conjecture

The file `Langlands/Local/BreuilMezardSym.lean` proves the simplicity of the Serre weights $\sigma_{a,b}$ with $a \le p - 1$, which Exercise 16 asks for and Example 2.5.52 uses. It also defines the multiplicities $n_{a,b}(\lambda, \tau)$ for a representation $\tau$ over an arbitrary field, which resolves item 3 of Remark 2.5.53. The file `Langlands/Statements/BreuilMezardFull.lean` then states Conjecture 2.5.51 with the objects of this section. In Lean, $\mathrm{Sym}^a k^2$ is the space of the homogeneous polynomials $P(X_0, X_1)$ of degree $a$, and $g \in GL_2(k)$ acts by $(gP)(X_0, X_1) = P\big((X_0, X_1) g\big)$, with the row vector $(X_0, X_1)$. Put
$$u^- = \begin{pmatrix} 1 & 0 \\ 1 & 1 \end{pmatrix}, \qquad w = \begin{pmatrix} 0 & 1 \\ -1 & 0 \end{pmatrix}.$$
Then $(X_0, X_1) u^- = (X_0 + X_1, X_1)$ and $(X_0, X_1) w = (-X_1, X_0)$.

**Theorem 2.5.66 (irreducibility of the Serre weights).** Let $k$ be a field of characteristic $p$, let $0 \le a \le p - 1$ and $b \ge 0$, and let $\theta : G \to GL_2(k)$ be a homomorphism whose image contains $u^-$ and $w$. Then the only subspaces of $\sigma_{a,b}$ that are stable under $G$ are $0$ and $\sigma_{a,b}$. So $\sigma_{a,b}$ is a simple $k[G]$-module.

Lean: `Langlands.isIrreducible_serreWeightRep`, `Langlands.isSimpleModule_serreWeightRep`

*Proof.* The matrices $u^-$ and $w$ have determinant $1$, so they act on $\sigma_{a,b}$ as on $\mathrm{Sym}^a k^2$. It suffices to show that a nonzero subspace $W$ that is stable under $u^-$ and $w$ is the whole space. The *dehomogenization* $P \mapsto P(X, 1)$ is a linear bijection from $\mathrm{Sym}^a k^2$ onto the polynomials of degree at most $a$ in $k[X]$, with the inverse $f \mapsto X_1^a f(X_0/X_1)$. It sends $u^- P$ to $f(X + 1)$, where $f = P(X, 1)$. It sends $X_1^a$ to $1$ and $X_0^a$ to $X^a$, and $w X_1^a = X_0^a$.

*Step 1 (the forward difference).* Let $f = \sum_i c_i X^i$ have degree $n + 1$ with $n + 1 < p$, and put $\Delta f = f(X + 1) - f$. The coefficient of $X^m$ in $f(X + 1)$ is $\sum_{i \ge m} \binom{i}{m} c_i$. So the coefficient of $X^{n+1}$ in $\Delta f$ is $0$, the coefficients of higher degree are $0$, and the coefficient of $X^n$ is $(n + 1) c_{n+1}$. This is not zero, because $0 < n + 1 < p$. So $\Delta f$ has degree exactly $n$.

*Step 2 (the fixed line).* Choose a nonzero $P \in W$ for which $f = P(X, 1)$ has the smallest degree. If this degree is $n + 1 \ge 1$, then $n + 1 \le a < p$, and $u^- P - P \in W$ has the dehomogenization $\Delta f$ of degree $n$ by Step 1. It is not zero, so this contradicts the choice of $P$. So $f$ is a nonzero constant $c$, $P = c X_1^a$, and $X_1^a \in W$.

*Step 3.* Since $W$ is stable under $w$, it contains $X_0^a$. Let $U$ be the image of $W$ in $k[X]$. It contains $X^a$ and it is stable under $f \mapsto f(X + 1)$, so it contains the iterated differences $\Delta^j X^a$ for $0 \le j \le a$. By Step 1, $\Delta^j X^a$ has degree exactly $a - j$. These $a + 1$ polynomials form a triangular basis of the polynomials of degree at most $a$. So $U$ is this whole space, and $W = \mathrm{Sym}^a k^2$ since the dehomogenization is injective. $\square$

The proof uses the hypothesis $a < p$ only in Step 1. For $a = p$ we have $\Delta X^p = 1$, and the theorem fails (Exercise 23). Lean proves the simplicity, but not the claims of the paragraph after Definition 2.5.41 that the $\sigma_{a,b}$ are pairwise non-isomorphic and that they are all the simple representations of $GL_2(\mathbb{F}_p)$.

**Corollary 2.5.67 (the Serre weights of $GL_2(\mathbb{F}_p)$).** Let $k$ be a field of characteristic $p$, let $0 \le a \le p - 1$ and $b \ge 0$. Then $\sigma_{a,b}$ is simple as a representation of $SL_2(\mathbb{F}_p)$ and of $GL_2(\mathbb{F}_p)$, through the maps to $GL_2(k)$ that the inclusion $\mathbb{F}_p \subseteq k$ gives. The same holds for $GL_2(\mathbb{Z}_p)$ with the reduction map $\theta$ of Definition 2.5.41.

Lean: `Langlands.slFpTo`, `Langlands.glFpTo`, `Langlands.slFpTo_apply`, `Langlands.exists_slFpTo_eq_lowerUnipotent`, `Langlands.exists_slFpTo_eq_weylElement`, `Langlands.isIrreducible_serreWeightRep_slFpTo`, `Langlands.isIrreducible_serreWeightRep_glFpTo`, `Langlands.isSimpleModule_serreWeightRep_glFpTo`

*Proof.* The matrices $u^-$ and $w$ have entries $0$ and $\pm 1$ and determinant $1$. So they lie in $SL_2(\mathbb{F}_p) \subseteq GL_2(\mathbb{F}_p)$, and they are the reductions of elements of $GL_2(\mathbb{Z}_p)$. Apply Theorem 2.5.66. $\square$

This proves the first claim of Exercise 16, with a proof that avoids the Vandermonde determinant. It also gives the simplicity of $\sigma_{k_0 - 2, 0}$ in part 1 of Example 2.5.52. Lean states the result for $GL_2(\mathbb{F}_p)$, and the case of $GL_2(\mathbb{Z}_p)$ is an application of `Langlands.isIrreducible_serreWeightRep`.

**Proposition 2.5.68 (invariance under isomorphism).** Let $O$ be a discrete valuation ring with the fraction field $C$ and the residue field $k$, and let $G$ be a group.
1. Let $\sigma_1$ and $\sigma_2$ be representations of $G$ on $O$-modules $L_1$ and $L_2$, and let $f : L_1 \to L_2$ be an isomorphism that commutes with $G$. Then $n_W(\sigma_1) = n_W(\sigma_2)$ for each representation $W$ of $G$ over $k$.
2. Let $e : V \to V'$ be an isomorphism of representations of $G$ over $C$. Then $e$ maps the stable lattices of $V$ onto the stable lattices of $V'$, $n_{a,b}(\rho, L) = n_{a,b}(\rho', e(L))$, and $n_{a,b}(\rho) = n_{a,b}(\rho')$.

Lean: `Langlands.reductionMultiplicity_congr`, `Langlands.IsStableLattice.map`, `Langlands.latticeSerreMultiplicity_congr`, `Langlands.serreMultiplicity_congr`

*Proof.* (1) The map $f$ induces an isomorphism $L_1 / \mathfrak{m} L_1 \to L_2 / \mathfrak{m} L_2$ that commutes with $G$. Apply part 2 of Lemma 2.5.40.

(2) The image $e(L)$ is a finitely generated $O$-module. It spans $V'$, since $e$ is $C$-linear and bijective, and it is stable, since $e$ commutes with $G$. The same holds for $e^{-1}$. The restriction of $e$ is an isomorphism $L \to e(L)$ that commutes with $G$, and part 1 gives the second claim. If $V$ has a stable lattice, the third claim follows from Theorem 2.5.43. If it has none, then $V'$ has none, and both sides are $0$ by the convention of Remark 2.5.53, item 1. $\square$

**Definition 2.5.69 (type multiplicities over a field).** Let $K$ be a non-archimedean local field with the ring of integers $\mathcal{O}_K$. Let $O$ be a discrete valuation ring with the fraction field $C$ and the residue field $k$, let $\mathcal{O}_K \to C$ be a ring homomorphism, and let $\mathrm{red} : \mathcal{O}_K \to k$ be a ring homomorphism. Let $\lambda$ be a Hodge-Tate type and let $\tau$ be a representation of $GL_2(\mathcal{O}_K)$ on a $C$-vector space of finite dimension.
1. Put $\sigma(\lambda, \tau) = \mathrm{Sym}^{\lambda_1 - \lambda_2 - 1} C^2 \otimes \det^{\lambda_2} \otimes_C \tau$, where $GL_2(\mathcal{O}_K)$ acts on $C^2$ through $GL_2(\mathcal{O}_K) \to GL_2(C)$.
2. The *type multiplicity* $n_{a,b}(\lambda, \tau)$ is the multiplicity $n_{a,b}(\sigma(\lambda, \tau))$ of Theorem 2.5.43, with $\theta : GL_2(\mathcal{O}_K) \to GL_2(k)$ induced by $\mathrm{red}$.

Lean: `Langlands.typeRep`, `Langlands.typeMultiplicityOf`

This differs from Definition 2.5.50 only in that $\tau$ is given over $C$, and no map $\iota : \mathbb{C} \to C$ is needed.

**Proposition 2.5.70 (comparison with Definition 2.5.50).** In the situation of Definition 2.5.69 the following hold.
1. Let $\iota : \mathbb{C} \to C$ be a ring homomorphism and let $\sigma$ be a smooth representation of $GL_2(\mathcal{O}_K)$ over $\mathbb{C}$ of finite dimension. Then $n_{a,b}(\lambda, \sigma)$ of Definition 2.5.50 is $n_{a,b}(\lambda, \tau)$ for $\tau = \iota_* \sigma$, and for each $\tau$ that is isomorphic to $\iota_* \sigma$.
2. If $\tau \cong \tau'$ over $C$, then $n_{a,b}(\lambda, \tau) = n_{a,b}(\lambda, \tau')$. In particular this holds for $O = \mathcal{O}_E$ and $C = E$.

Lean: `Langlands.typeMultiplicity_eq_typeMultiplicityOf`, `Langlands.typeMultiplicityOf_congr`, `Langlands.typeMultiplicity_eq_of_equiv`, `Langlands.typeMultiplicityOf_integer_congr`

*Proof.* (1) The first claim holds by the definitions, and the second follows from part 2. (2) Let $e : \tau \to \tau'$ be an isomorphism. Then $1 \otimes e$ is an isomorphism $\sigma(\lambda, \tau) \to \sigma(\lambda, \tau')$ that commutes with $GL_2(\mathcal{O}_K)$. Apply part 2 of Proposition 2.5.68. $\square$

By item 3 of Remark 2.5.53, part 1 has no content for $C = E$, because there is no ring homomorphism $\mathbb{C} \to E$. The full statement therefore applies Definition 2.5.69 to a model of $\sigma(\tau)$ over $E$. Part 2 shows that the model matters only up to isomorphism over $E$. The independence of $E$ and of the embedding $E \to \mathbb{C}$, which the comment after Definition 2.5.50 proves, is not in Lean.

**Definition 2.5.71 (potentially semistable lifts and models).** Let $E$ be a field with a ring homomorphism $\mathbb{Z}_p \to E$, and let $\rho : G_{\mathbb{Q}_p} \to GL_2(E)$ be a homomorphism.
1. If $E$ is a $\mathbb{Q}_p$-algebra, $\rho_{\mathbb{Q}_p}$ is the representation $\rho$ on $E^2$, seen as a representation over $\mathbb{Q}_p$.
2. An *inertial type map* is a function $\mathrm{wd}$ that assigns to each field $E$ over $\mathbb{Q}_p$ and each $\rho : G_{\mathbb{Q}_p} \to GL_2(E)$ an inertial type $\mathrm{wd}(E, \rho)$ of $\mathbb{Q}_p$ of dimension $2$.
3. Let $\lambda$ be a Hodge-Tate type, $\tau$ an inertial type of dimension $2$ and $\mathrm{wd}$ an inertial type map. The lift $\rho$ is *potentially semistable of type $(\lambda, \tau)$* if $E$ is a $\mathbb{Q}_p$-algebra of finite dimension whose structure map extends $\mathbb{Z}_p \to E$, $\rho_{\mathbb{Q}_p}$ is continuous and potentially semistable in the sense of Definition 2.5.62, the set of the Hodge-Tate weights of $\rho_{\mathbb{Q}_p}$ is $\{-\lambda_1, -\lambda_2\}$, and $\mathrm{wd}(E, \rho) = \tau$.
4. Let $H$ be a group, let $j : E \to \mathbb{C}$ be a ring homomorphism, let $\tau_E$ be a representation of $H$ on an $E$-vector space of finite dimension $n$, and let $\sigma$ be a representation of $H$ over $\mathbb{C}$. Then $\tau_E$ is a *model* of $\sigma$ along $j$ if, in a basis of $\tau_E$, the matrices of $\tau_E$ with $j$ applied to the entries give a representation on $\mathbb{C}^n$ that is isomorphic to $\sigma$.

Lean: `Langlands.restrictToQp`, `Langlands.InertialTypeMap`, `Langlands.IsPstLift`, `Langlands.IsModelOf`

The sign in part 3 comes from the conventions. In the project the cyclotomic character has the Hodge-Tate weight $-1$. The representation $\mathrm{Sym}^{\lambda_1 - \lambda_2 - 1} \otimes \det^{\lambda_2}$ fits the weights $\{\lambda_1, \lambda_2\}$ in the convention where the cyclotomic character has the weight $1$. The weights are taken as a set, so the condition does not see multiplicities. The map $\mathrm{wd}$ stands for $\rho \mapsto \mathrm{WD}(\rho)|_{I_{\mathbb{Q}_p}}$, see the comments after Definition 2.5.36 and Lemma 2.5.46. This needs $D_{\mathrm{pst}}$ and an isomorphism $\bar{\mathbb{Q}}_p \cong \mathbb{C}$, which are not in Lean.

**Conjecture 2.5.72 (Breuil and Mezard, the full form).** Let $p$ be a prime and let $\mathrm{wd}$ be an inertial type map. Let $k$ be a finite field of characteristic $p$ with a ring homomorphism $\mathbb{Z}_p \to k$, let $\bar\rho : G_{\mathbb{Q}_p} \to GL_2(k)$ have open kernel, let $\mathrm{art}$ be a local Artin map and let $\mathrm{rec}$ be a bijection with the properties of `Langlands.IsLanglandsMap` for $\mathrm{art}$, see Volume 6, Remark 3.1.9. Let $R$ be a universal framed deformation ring of $\bar\rho$ over $\mathbb{Z}_p$ with the universal lift $\rho^u$. Then there are integers $\mu_{a,b} \ge 0$ with the following property. Let $\lambda$ be a Hodge-Tate type, $\tau$ an inertial type of dimension $2$ and $\sigma$ a type for $\tau$ in the sense of part 1 of Definition 2.5.47, for $\mathrm{rec}$. Let $E$ be a finite extension of $\mathbb{Q}_p$, $j : E \to \mathbb{C}$ a ring homomorphism and $\tau_E$ a model of $\sigma$ along $j$. Then
$$e\big(R(\lambda, \tau) / p\big) = \sum_{a=0}^{p-1} \sum_{b=0}^{p-2} n_{a,b}(\lambda, \tau_E) \, \mu_{a,b}.$$
Here $R(\lambda, \tau)$ is the quotient $R^\square(P)$ of Definition 2.5.19 for the condition $P$ of part 3 of Definition 2.5.71, $e$ is the multiplicity of the special fiber of Definition 2.5.21 with $\varpi = p$, and $n_{a,b}(\lambda, \tau_E)$ is the multiplicity of Definition 2.5.69 with $O = \mathcal{O}_E$ and $\mathrm{red} : \mathbb{Z}_p \to k_E$ the reduction.

Lean: `Langlands.BreuilMezardFullFor`, `Langlands.BreuilMezardGL2QpFull`, stated and not proved.

The integers $\mu_{a,b}$ are chosen after $R$ and before $\lambda$, $\tau$, $E$ and the model, as in Conjecture 2.5.51. The proposition `Langlands.BreuilMezardFullFor p k ρbar rec wd` is the statement for one $\bar\rho$, one $\mathrm{rec}$ and one $\mathrm{wd}$, and `Langlands.BreuilMezardGL2QpFull wd` quantifies over $k$, $\bar\rho$, $\mathrm{art}$ and $\mathrm{rec}$. This statement does not replace the shape `Langlands.BreuilMezardGL2Qp` of Conjecture 2.5.51, which other Lean files use. Only the semistable half of Conjecture 2.5.51 is stated: there is no crystalline version with $\sigma^{\mathrm{cr}}(\tau)$.

**Proposition 2.5.73 (checks of the statement).** Let $O$ be a discrete valuation ring with the fraction field $C$ and the residue field $k$, and let $\lambda = (1, 0)$.
1. The image of $O$ in $C$ is a stable lattice of the trivial representation of each group $G$, and $n_W(C) = [k : W]$ for the trivial representation $C$ and each $W$.
2. For the trivial representation $\tau = C$ of $GL_2(\mathcal{O}_K)$, $\sigma(\lambda, \tau)$ is the trivial representation. So $n_{0,0}(\lambda, C) = 1$ and $n_{a,b}(\lambda, C) = 0$ for $a \ne 0$. In particular $n_{0,0}(\lambda, E) = 1$ for each finite extension $E$ of $\mathbb{Q}_p$ in the statement.
3. Assume Conjecture 2.5.72 for $\bar\rho$, $\mathrm{rec}$ and $\mathrm{wd}$. Let $\lambda$, $\tau$, $\sigma$, $E$ and $\tau_E$ be as in the conjecture, and assume that there are $a_0 \le p - 1$ and $b_0 \le p - 2$ with $n_{a,b}(\lambda, \tau_E) = 1$ for $(a, b) = (a_0, b_0)$ and $n_{a,b}(\lambda, \tau_E) = 0$ for the other $(a, b)$ in the sum. Then $e(R(\lambda, \tau) / p) = \mu_{a_0, b_0}$.

Lean: `Langlands.isStableLattice_range_trivial`, `Langlands.serreMultiplicity_trivial`, `Langlands.typeRep_one_zero_trivial`, `Langlands.typeMultiplicityOf_one_zero_trivial`, `Langlands.typeMultiplicityOf_one_zero_trivial_zero_zero`, `Langlands.typeMultiplicityOf_one_zero_trivial_of_ne_zero`, `Langlands.typeMultiplicityOf_coeffRed_trivial`, `Langlands.BreuilMezardFullFor.exists_mu`

*Proof.* (1) The image $O \cdot 1$ is finitely generated, spans $C$ and is stable. Its reduction is the trivial representation $k$. (2) For $\lambda = (1, 0)$ we have $\lambda_1 - \lambda_2 - 1 = 0$ and $\lambda_2 = 0$, so $\sigma(\lambda, \tau) = \mathrm{Sym}^0 C^2 \otimes \det^0 \otimes C$, which is the trivial representation. Part 1 and Example 2.5.44 give the values. (3) In the sum only the term $(a_0, b_0)$ is not zero, and it is $\mu_{a_0, b_0}$. $\square$

The trivial representation of $GL_2(\mathbb{Z}_p)$ is $\sigma^{\mathrm{cr}}(1 \oplus 1)$ and not $\sigma(1 \oplus 1)$, by Example 2.5.49. So part 2 does not give an input of the semistable statement. It shows only that the function $n_{a,b}$ of the statement is not identically zero, so that the right side of the conjecture is not forced to be $0$. Exercise 24 computes the input $\sigma(1 \oplus 1) = \mathrm{st}$ with $\lambda = (1, 0)$, for which part 3 applies.

**Remark 2.5.74 (the Lean status of the full statement).** The statement of Conjecture 2.5.72 resolves item 4 of Remark 2.5.53, with the following reservations. They are listed in the documentation of `Langlands/Statements/BreuilMezardFull.lean`.
1. *The inertial type of a lift.* It is the parameter $\mathrm{wd}$. The statement is the conjecture only when $\mathrm{wd}$ sends a potentially semistable lift to the restriction to inertia of $\mathrm{WD}(\rho)$, moved to $\mathbb{C}$. For other maps it is a different claim. The values of $\mathrm{wd}$ on lifts that are not potentially semistable have no effect.
2. *The correspondence.* The predicate `Langlands.IsLanglandsMap` does not fix $\mathrm{rec}$ on the supercuspidal representations, by item 3 of Volume 6, Remark 3.1.9. So for supercuspidal types the statement asks for the formula for each such $\mathrm{rec}$. If $\mathrm{rec}$ is not unique, this is a stronger claim than the conjecture.
3. *Existence.* Lean does not prove that a universal framed deformation ring exists, that Henniart types exist (Theorem 2.5.48), or that models over $E$ exist. If one of them does not exist, the statement is empty for that input.
4. *The ring $R(\lambda, \tau)$.* It is the quotient by the ideal of the points, which is Kisin's ring when the points are dense. Lean does not prove that it is Kisin's ring, or that it is local and nonzero when it has a point. If it is not local, its multiplicity is $0$ by the Lean convention.
5. *Facts used by the mathematics.* Lean does not prove that a potentially semistable representation is de Rham, that $B_{\mathrm{st}}^{G_L}$ is a field, or that $n_{a,b}(\lambda, \tau_E)$ does not depend on $E$ and the model.
6. *The prime $2$.* The statement includes $p = 2$. The results of Kisin, Paškūnas, and Hu and Tan cited after Conjecture 2.5.51 assume $p > 2$, so for $p = 2$ the statement is still a conjecture.
