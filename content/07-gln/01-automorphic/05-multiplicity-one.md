---
title: Whittaker models and multiplicity one
nodes: []
sources: [JL70]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Whittaker models and multiplicity one

A cusp form on $GL_2$ has a Fourier expansion, and the coefficients of a newform are determined by its Hecke eigenvalues. For $GL_n$ the analogue is the Whittaker expansion of Shalika and Piatetski-Shapiro. With the uniqueness of local Whittaker models it gives multiplicity one: each cuspidal representation occurs once in $L^2_0(\omega)$. Strong multiplicity one says more: a cuspidal representation is determined by its components at almost all places, and so by its Satake parameters. This is the theorem that lets the Lean project replace cuspidal representations by classes of eigenforms. The example to keep in mind is the $q$-expansion of a newform $f$, where $a_m(f)$ is a product of local factors given by the Satake parameters.

### Generic characters and Whittaker functions

Fix a nontrivial character $\psi$ of $F \backslash \mathbb{A}$, as in Volume 0, Chapter 3. The group $N$ is the group of the upper triangular unipotent matrices. Define the character $\psi_N$ of $N(\mathbb{A})$, trivial on $N(F)$, by
$$\psi_N(u) = \psi(u_{12} + u_{23} + \cdots + u_{n-1,n}).$$
In the same way we define $\psi_{N,v}$ on $N(F_v)$ from the local component $\psi_v$. Let $P_n \subset GL_n$ be the *mirabolic* subgroup of the matrices whose last row is $(0, \ldots, 0, 1)$.

**Definition 1.5.1 (Whittaker function).** For an automorphic form $\varphi$ on $GL_n(\mathbb{A})$ its *Whittaker function* is
$$W_\varphi(g) = \int_{N(F) \backslash N(\mathbb{A})} \varphi(ug) \, \overline{\psi_N(u)} \, du,$$
with the Haar measure of total mass $1$. It satisfies $W_\varphi(ug) = \psi_N(u) W_\varphi(g)$ for $u \in N(\mathbb{A})$.

Lean: not stated yet

**Theorem 1.5.2 (Whittaker expansion).** Let $\varphi$ be a cusp form on $GL_n(\mathbb{A})$. Then
$$\varphi(g) = \sum_{\gamma \in N_{n-1}(F) \backslash GL_{n-1}(F)} W_\varphi\left( \begin{pmatrix} \gamma & 0 \\ 0 & 1 \end{pmatrix} g \right),$$
where the sum converges absolutely and uniformly on compact sets.

Lean: not stated yet

*Proof sketch.* One proves by induction on $k$ a formula with a sum over $N_k(F) \backslash GL_k(F)$ and an integral over the unipotent matrices whose upper left $k \times k$ block is $1_k$. The case $k = n - 1$ is the theorem. For the inductive step, expand the integrand in a Fourier series on the compact group $F^{k+1} \backslash \mathbb{A}^{k+1}$ given by the column $k + 2$ above the diagonal. The term of the trivial character is an integral of a constant term of $\varphi$, so it vanishes because $\varphi$ is cuspidal. The group $GL_{k+1}(F)$ acts transitively on the nontrivial characters, with the mirabolic subgroup $P_{k+1}(F)$ as the stabilizer of one of them. So the remaining sum is over $P_{k+1}(F) \backslash GL_{k+1}(F)$, and $N_k \backslash GL_k \simeq N_{k+1} \backslash P_{k+1}$ completes the step. The convergence follows from the rapid decay of $\varphi$. $\square$

For $n = 2$ the sum is over $\gamma \in F^\times$, and the theorem is the Fourier expansion $\varphi(g) = \sum_{a \in F^\times} W_\varphi(\mathrm{diag}(a, 1) g)$. For $\varphi = \varphi_f$ and $g = g_\infty$ it is the $q$-expansion of $f$.

**Corollary 1.5.3.** If $\varphi$ is a cusp form and $W_\varphi = 0$, then $\varphi = 0$.

Lean: not stated yet

### Uniqueness of local Whittaker models

Let $v$ be a place and $\pi_v$ an irreducible admissible representation of $GL_n(F_v)$, smooth if $v$ is finite and a $(\mathfrak{g}, K_v)$-module if $v$ is infinite. A *Whittaker functional* on $\pi_v$ is a linear form $\Lambda$, continuous for $v$ infinite, with $\Lambda(\pi_v(u) x) = \psi_{N,v}(u) \Lambda(x)$ for $u \in N(F_v)$. If $\Lambda \neq 0$, then $x \mapsto (g \mapsto \Lambda(\pi_v(g)x))$ embeds $\pi_v$ into the space $\mathcal{W}(\psi_{N,v})$ of the functions $W$ with $W(ug) = \psi_{N,v}(u) W(g)$. Its image is the *Whittaker model* of $\pi_v$, and $\pi_v$ is called *generic*.

**Theorem 1.5.4 (local uniqueness).** The space of the Whittaker functionals on $\pi_v$ has dimension at most $1$.

Lean: not stated yet

*Proof sketch.* For $v$ finite this is due to Gelfand and Kazhdan, and to Shalika. Let $\iota(g) = w_0 {}^t g^{-1} w_0$, with $w_0$ the antidiagonal permutation matrix. Gelfand and Kazhdan prove that each distribution $T$ on $G_v$ with $T(u_1 g u_2) = \psi_{N,v}(u_1) \psi_{N,v}(u_2) T(g)$ is invariant under $\iota$, by an analysis of the Bruhat cells. Since $\tilde \pi_v \simeq \pi_v \circ \iota$, two independent Whittaker functionals on $\pi_v$ would give a distribution of this kind that is not invariant. For $v$ infinite the theorem is due to Shalika. $\square$

**Theorem 1.5.5 (multiplicity one).** Let $\pi$ be an irreducible admissible representation of $GL_n(\mathbb{A})$. Then $\pi$ occurs at most once in the space of cusp forms with central character $\omega$. Every cuspidal automorphic representation is generic at every place.

Lean: not stated yet

*Proof.* Let $V \subseteq \mathcal{A}_0(\omega)$ be a subspace isomorphic to $\pi = \bigotimes'_v \pi_v$, by Theorem 1.3.4. The map $\varphi \mapsto W_\varphi(1)$ is a nonzero Whittaker functional on $V$, by the corollary above. Its restriction to the pure tensors gives a nonzero Whittaker functional on each $\pi_v$, so each $\pi_v$ is generic. The global space of Whittaker functionals on $\pi$ is the restricted tensor product of the local spaces, so it has dimension $1$ by the local theorem. If $V_1$ and $V_2$ are two such subspaces with an isomorphism $A : V_1 \to V_2$, then $\varphi \mapsto W_\varphi(1)$ and $\varphi \mapsto W_{A \varphi}(1)$ are proportional on $V_1$. So $W_{A\varphi - c\varphi} = 0$ for some constant $c$, hence $A \varphi = c \varphi$ by the corollary, and $V_1 = V_2$. $\square$

### Strong multiplicity one

**Theorem 1.5.6 (strong multiplicity one).** Let $\pi$ and $\pi'$ be cuspidal automorphic representations of $GL_n(\mathbb{A})$. Suppose that $\pi_v \simeq \pi'_v$ for all places $v$ outside a finite set $S$. Then $\pi = \pi'$ as subspaces of $\mathcal{A}_0$.

Lean: not stated yet

*Proof sketch.* This is the proof of Piatetski-Shapiro. Assume first that $S$ contains no infinite place. Fix pure tensors and Whittaker models $\pi_v \simeq \mathcal{W}(\pi_v, \psi_{N,v})$ and $\pi'_v \simeq \mathcal{W}(\pi'_v, \psi_{N,v})$ for $v \notin S$, chosen to be equal. At $v \in S$ choose $W_v$ in the Whittaker model of $\pi_v$ and $W'_v$ in that of $\pi'_v$. By Theorem 1.5.5 and the Whittaker expansion, the cusp form $\varphi$ with $W_\varphi = \prod_v W_v$ satisfies, for $p \in P_n(\mathbb{A})$,
$$\varphi(p) = \sum_{\gamma \in N_{n-1}(F) \backslash GL_{n-1}(F)} \prod_v W_v \left( \begin{pmatrix} \gamma & 0 \\ 0 & 1 \end{pmatrix} p \right).$$
The key fact is the theory of Bernstein and Zelevinsky, and of Jacquet and Shalika: the restriction of $\mathcal{W}(\pi_v, \psi_{N,v})$ to $P_n(F_v)$ contains the compactly supported functions on $N(F_v) \backslash P_n(F_v)$ with the right transformation law. So we may choose $W_v = W'_v$ on $P_n(F_v)$ for $v \in S$. This argument needs $S$ to contain only finite places. For a set $S$ that contains infinite places, the theorem follows from the theorem of Jacquet and Shalika below, whose proof uses $L$-functions. Then $\varphi$ and $\varphi'$ agree on $P_n(\mathbb{A})$. Both are left invariant under $GL_n(F)$, and $GL_n(F) P_n(\mathbb{A})$ is dense in $GL_n(\mathbb{A})$, up to the center, by strong approximation for the last row. So $\varphi = \varphi'$, and $\pi \cap \pi' \ne 0$. Both are irreducible, so $\pi = \pi'$. $\square$

At a place $v \notin S$ where $\pi_v$ and $\pi'_v$ are unramified, $\pi_v \simeq \pi'_v$ if and only if they have the same Satake parameters, by Theorem 1.4.6. So the theorem has this form, which is the form of the Lean project.

**Corollary 1.5.7.** Two cuspidal automorphic representations of $GL_n(\mathbb{A})$ that have the same Satake parameters at almost all finite places are equal. Two cusp forms with unitary central characters that are Hecke eigenvectors with the same eigenvalues at almost all finite places generate the same cuspidal automorphic representation.

Lean: not stated yet

*Proof.* The first claim is Theorem 1.5.6 and Theorem 1.4.6. For the second, let $\varphi$ be such a cusp form. Its projection to each summand $\pi$ of $L^2_0(\omega)$ is again an eigenvector with the same eigenvalues, because the projections commute with the Hecke operators. By the first claim at most one summand has these eigenvalues, so $\varphi$ lies in one $\pi$. $\square$

**Example 1.5.8 (newforms on $GL_2$).** For a newform $f$ the corollary is the theorem of Atkin and Lehner and of Miyake in Volume 4: $f$ is determined by its eigenvalues $a_p$ for almost all $p$. The Whittaker function of the new vector is a product of local new vectors, and for $p \nmid N$ the local value is the Shintani formula
$$W_p(\mathrm{diag}(p^r, 1)) = p^{-r/2} \frac{\alpha_p^{r+1} - \beta_p^{r+1}}{\alpha_p - \beta_p}.$$
For $GL_n$ Shintani proved that the unramified Whittaker function at $\varpi^\lambda$ is $\delta_B^{1/2}(\varpi^\lambda)$ times the Schur polynomial $s_\lambda(\alpha)$.

The theorem is false for other groups. For $SL_2$ there are cuspidal representations that agree at almost all places but are not equal, by Labesse and Langlands. This is the origin of endoscopy, the topic of Volume 9. For $GL_2$, Ramakrishnan proved that agreement at a set of places of density larger than $7/8$ is enough, and this bound is sharp.

### Isobaric sums

The lifts of Chapter 2 are often not cuspidal. Their place is the class of the isobaric representations.

**Definition 1.5.9 (isobaric sum).** Let $\pi_1, \ldots, \pi_k$ be cuspidal automorphic representations of $GL_{m_1}(\mathbb{A}), \ldots, GL_{m_k}(\mathbb{A})$ with $\sum m_j = m$. The *isobaric sum* $\pi_1 \boxplus \cdots \boxplus \pi_k$ is the unique irreducible quotient, the Langlands quotient, of the representation of $GL_m(\mathbb{A})$ induced from $\pi_1 \otimes \cdots \otimes \pi_k$ on the standard parabolic subgroup of type $(m_1, \ldots, m_k)$, with the $\pi_j$ ordered by decreasing real part of the central exponent. It is an automorphic representation, a constituent of the space of Eisenstein series. Its Satake parameters at a place where all $\pi_j$ are unramified are the union of the Satake parameters of the $\pi_j$, and its $L$-function is $\prod_j L(s, \pi_j)$.

Lean: `Langlands.IsobaricCuspData`, a definition of the project, and `Langlands.IsobaricCuspData.HasSatakeAt`

The Lean structure `Langlands.IsobaricCuspData K m` is a finite family of nonzero cusp forms $\varphi_j$ on $GL_{m_j}$ with $\sum m_j = m$, and `HasSatakeAt D v A` says that the forms are Hecke eigenvectors at $v$ and that the union of their Satake parameters is the multiset $A$. So the Lean code records only the summands and their parameters at the unramified places. It does not construct the induced representation. This is enough for the statements of Chapter 2, which only compare Satake parameters.

**Theorem 1.5.10 (Jacquet and Shalika).** Let $\pi = \pi_1 \boxplus \cdots \boxplus \pi_k$ and $\pi' = \pi'_1 \boxplus \cdots \boxplus \pi'_l$ be isobaric sums with $\pi_v \simeq \pi'_v$ for almost all $v$. Then $k = l$, and the $\pi'_j$ are the $\pi_j$ after a permutation.

Lean: not stated yet

*Proof sketch.* For each cuspidal $\sigma$ the partial Rankin-Selberg $L$-functions satisfy $L^S(s, \pi \times \tilde \sigma) = \prod_j L^S(s, \pi_j \times \tilde \sigma) = L^S(s, \pi' \times \tilde \sigma)$. By the theorem of Jacquet, Piatetski-Shapiro and Shalika, $L^S(s, \pi_j \times \tilde \sigma)$ has a simple pole at $s = 1$ if $\pi_j \simeq \sigma$, and it is holomorphic and nonzero at $s = 1$ otherwise. So the order of the pole counts how often $\sigma$ occurs among the $\pi_j$, and also among the $\pi'_j$. $\square$

**Remark 1.5.11 (multiplicity one in the Lean project).** In `Langlands/Statements/NumberFieldGL.lean`, `Langlands.NumberFieldGL.CuspEigenform K n` is the type of the nonzero cusp forms of some level that are Hecke eigenvectors at almost all finite places, and `CuspEigenform.Equiv` is the relation "there is a finite set $S$ such that for $v \notin S$ both forms are eigenvectors at $v$ with the same eigenvalues". The project proves that this is an equivalence relation, using `Langlands.NumberFieldGL.heckeEigenvalue_unique`: the eigenvalues of a nonzero eigenvector are unique. The quotient `AutomorphicClass K n` is the set of cuspidal automorphic representations by Corollary 1.5.7, applied after a twist that makes the central character unitary. The project does not state Corollary 1.5.7. It uses the eigenvalues at almost all places as the definition, and this is a choice of definition, not a theorem of the Lean code.

Lean: `Langlands.NumberFieldGL.heckeEigenvalue_unique`, proved in the project
