---
title: Supercuspidal representations
nodes: []
sources: [BH06, Kut80]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Supercuspidal representations

A representation that is induced from a proper parabolic subgroup can be understood through the smaller group $M$. The representations that do not occur in this way are the supercuspidal ones. They are the hardest part of the theory, and they are the part where the local Langlands correspondence carries real arithmetic information. This section gives the two definitions, by Jacquet modules and by matrix coefficients, shows that each irreducible representation embeds in an induced representation from a supercuspidal one, and constructs supercuspidal representations by compact induction.

### Two definitions

**Definition 1.4.1 (supercuspidal representation).** A smooth representation $\pi$ of $G = GL_n(K)$ is *supercuspidal*, or *cuspidal*, if $r_P(\pi) = 0$ for each proper parabolic subgroup $P$ of $G$.

Lean: `Langlands.SmoothRep.IsSupercuspidal`, with the definition of Theorem 1.4.3

For $p$-adic groups and complex representations the words cuspidal and supercuspidal mean the same thing. The two words differ for representations over fields of positive characteristic, where Vignéras showed that a cuspidal representation can be a subquotient of an induced representation without being a subrepresentation of one. We use the word supercuspidal, which is the usual one in the statement of the local Langlands correspondence.

The Jacquet functors compose: if $Q \subseteq P$ are parabolic subgroups with Levi subgroups $L \subseteq M$, then $r_Q = r_{Q \cap M} \circ r_P$, since $V(U) \supseteq V(N)$ for the unipotent radicals $U \supseteq N$ and the modulus characters multiply. So $\pi$ is supercuspidal if and only if $r_P(\pi) = 0$ for each maximal standard parabolic subgroup $P$. For $GL_n$ these are the groups of type $(m, n - m)$ with $0 < m < n$. By Proposition 1.3.5 and Theorem 1.3.3, an irreducible $\pi$ is supercuspidal if and only if it is not a subrepresentation of any $\mathrm{Ind}_P^G \sigma$ with $P$ proper.

**Proposition 1.4.2 (characters and the trivial representation are not supercuspidal).** For $n \ge 2$, a character $\chi \circ \det$ of $GL_n(K)$ is not supercuspidal. More generally, a finite-dimensional smooth representation of $GL_n(K)$ is not supercuspidal.

Lean: not stated yet

*Proof.* The unipotent radical $N$ of each parabolic subgroup lies in $SL_n(K)$, and $SL_n(K)$ acts trivially on a finite-dimensional smooth representation, by Example 1.1.3. So $V(N) = 0$ and $r_P(V) = V \ne 0$. $\square$

The second definition uses matrix coefficients. For $v \in V$ and $\lambda \in V^\vee$ the function $c_{v, \lambda}(g) = \lambda(\pi(g) v)$ is a *matrix coefficient* of $\pi$. It is locally constant, and it is bi-invariant under a compact open subgroup.

**Theorem 1.4.3 (Jacquet, Harish-Chandra).** Let $\pi$ be an irreducible smooth representation of $G = GL_n(K)$ with center $Z = K^\times$. The following are equivalent.
1. $\pi$ is supercuspidal.
2. Each matrix coefficient of $\pi$ has compact support modulo $Z$: for $v \in V$ and $\lambda \in V^\vee$ there is a compact set $C \subseteq G$ such that $c_{v, \lambda}(g) \ne 0$ implies $g \in C Z$.

Lean: not stated yet

*Sketch of proof.* Let $A^-$ be the set of the diagonal matrices $\varpi^\lambda$ with $\lambda_1 \ge \dots \ge \lambda_n$. By the Cartan decomposition $G = K_0 A^- K_0$, it is enough to study $c_{v, \lambda}(a)$ for $a \in A^-$, as $v$ and $\lambda$ run over finitely many translates under $K_0$. Fix a compact open subgroup $J$ with an Iwahori decomposition that fixes $v$ and $\lambda$. Let $a = \varpi^\mu \in A^-$, and suppose that $\mu_m - \mu_{m+1}$ is large for some $m$. Let $P$ be the parabolic subgroup of type $(m, n - m)$ with unipotent radical $N$. The entry $(i, j)$ of $a^{-1} n a$ is $\varpi^{\mu_j - \mu_i} n_{ij}$, so $a^{-1}$ expands $N$, and $N_a = a^{-1} (J \cap N) a$ is a large compact open subgroup of $N$. Since $\lambda$ is fixed by $J \cap N$, we have $c_{v, \lambda}(a) = \lambda(\pi(a) e_{N_a} v)$, where $e_{N_a}$ is the average over $N_a$. If $r_P(\pi) = 0$, then $v$ lies in $V(N)$, and by Proposition 1.3.5 there is a compact open subgroup $N_0$ of $N$ with $e_{N_0} v = 0$. Then $e_{N_1} v = 0$ for each compact open $N_1 \supseteq N_0$. For $\mu_m - \mu_{m+1}$ large, $N_a \supseteq N_0$, and so $c_{v, \lambda}(a) = 0$. So $c_{v, \lambda}(a) = 0$ unless all the differences $\mu_m - \mu_{m+1}$ are bounded. The set of such $a$ is compact modulo $Z$. This proves that 1 implies 2.

Conversely, suppose 2, and suppose that $r_P(\pi) \ne 0$ for a maximal $P$. Choose $\bar v \ne 0$ in $r_P(\pi)$ and a lift $v$. Casselman's pairing between $r_P(\pi)$ and $r_{\bar P}(\pi^\vee)$ gives $\lambda \in V^\vee$ such that $c_{v, \lambda}(z^k)$ equals a nonzero constant times $\delta_P(z)^{k/2} \langle r_P(\pi)(z)^k \bar v, \bar \lambda \rangle$ for all large $k$, where $z$ is a central element of $M$ that contracts $N$. This expression is not identically zero for large $k$, since $r_P(\pi)(z)$ acts on a finite-dimensional space generated by $\bar v$ through an invertible map. But $z^k$ leaves every compact set modulo $Z$. This contradicts 2. $\square$

**Remark 1.4.4 (the Lean definition).** The Lean declaration `Langlands.SmoothRep.IsSupercuspidal π ι` takes a group $Z$ with a homomorphism $\iota : Z \to G$ to the center. It says that for each $v$ and each smooth linear form $\lambda$ there is a compact set $C$ with $c_{v, \lambda}(g) \ne 0 \Rightarrow g \in C \cdot \iota(Z)$. This is condition 2 of Theorem 1.4.3, with $\iota$ the embedding `Langlands.scalarGL` of $K^\times$ as the scalar matrices. The Lean project has the Jacquet module `Langlands.SmoothRep.jacquet` of Section 1.3, but among the parabolic subgroups it has only the Borel subgroup `Langlands.GL2.borel` of $GL_2$. So the definition by Jacquet modules is not in the Lean project, and the equivalence of Theorem 1.4.3 is not stated there. The linear forms $\lambda$ are the smooth ones, as in Definition 1.1.5. This matters: for an arbitrary linear form on an infinite-dimensional space, the coefficient need not have compact support.

### The subrepresentation theorem

**Theorem 1.4.5 (admissibility and the subrepresentation theorem).** Let $\pi$ be an irreducible smooth representation of $G = GL_n(K)$.
1. If $\pi$ is supercuspidal, then $\pi$ is admissible.
2. There are a standard parabolic subgroup $P = MN$ and an irreducible supercuspidal representation $\sigma$ of $M$ such that $\pi$ is isomorphic to a subrepresentation of $\mathrm{Ind}_P^G \sigma$.

Lean: not stated yet

*Proof.* For part 1, fix $0 \ne \lambda \in V^\vee$ and consider the map $V \to C^\infty(G)$, $v \mapsto c_{v, \lambda}$. It is injective and $G$-equivariant for the right translation action, since $\pi$ is irreducible. Its image consists of functions with compact support modulo $Z$, by Theorem 1.4.3, and all these functions have the central character $\omega_\pi$. Fix a compact open subgroup $J$. A vector $v \in V^J$ gives a function $c_{v, \lambda}$ that is right invariant under $J$ and left invariant under the stabilizer $J_\lambda$ of $\lambda$. Theorem 1.4.3 gives a compact set $C$ that contains the supports of all these functions modulo $Z$, uniformly in $v \in V^J$; this uniformity is part of the proof of Theorem 1.4.3, since the bound on the differences $\mu_m - \mu_{m+1}$ depends only on $J$. A function on $J_\lambda \backslash C Z / J$ with central character $\omega_\pi$ is determined by finitely many values. So $V^J$ has finite dimension.

For part 2, choose $P = MN$ minimal among the standard parabolic subgroups with $r_P(\pi) \ne 0$. The space $r_P(\pi)$ is finitely generated by Bernstein's form of Theorem 1.3.6, since $\pi$ is generated by one vector. So it has an irreducible quotient $\sigma$, by Zorn's lemma. If $\sigma$ were not supercuspidal, then $r_{Q \cap M}(\sigma) \ne 0$ for a proper parabolic $Q \cap M$ of $M$, and then $r_Q(\pi) \ne 0$ by exactness and the composition of Jacquet functors, against the minimality of $P$. By Theorem 1.3.3, the quotient map $r_P(\pi) \to \sigma$ gives a nonzero map $\pi \to \mathrm{Ind}_P^G \sigma$, which is injective since $\pi$ is irreducible. $\square$

This completes the sketch of Theorem 1.1.11. By part 2 and induction on $n$, $\sigma$ is admissible, and so is $\mathrm{Ind}_P^G \sigma$ by Proposition 1.3.4, and then so is $\pi$.

**Theorem 1.4.6 (uniqueness of the supercuspidal support).** Let $\pi$ be an irreducible smooth representation of $GL_n(K)$. Suppose that $\pi$ is a subquotient of $\mathrm{Ind}_P^G \sigma$ and of $\mathrm{Ind}_{P'}^G \sigma'$, with $\sigma$ and $\sigma'$ irreducible supercuspidal representations of Levi subgroups $M$ and $M'$. Then there is $w \in G$ with $w M w^{-1} = M'$ and $\sigma' \cong w \sigma$.

Lean: not stated yet

*Sketch of proof.* By Theorem 1.3.8, the semisimplification of $r_{P'}(\mathrm{Ind}_P^G \sigma)$ is a sum of representations induced from Jacquet modules of $\sigma$. Since $\sigma$ is supercuspidal, these Jacquet modules vanish unless the double coset is such that $w M w^{-1} = M'$ up to the Levi of a smaller parabolic, and the nonzero pieces are the $w \sigma$. If $\pi$ is a subquotient of both induced representations, then $r_{P'}(\pi)$ is nonzero, and it is a subquotient of the Jacquet modules of both. By Frobenius reciprocity applied to an embedding of $\pi$ in $\mathrm{Ind}_{P'}^G \sigma'$, $\sigma'$ is a subquotient of $r_{P'}(\pi)$. So $\sigma'$ is one of the $w \sigma$. $\square$

The conjugacy class of the pair $(M, \sigma)$ is the *supercuspidal support* of $\pi$. For $GL_n$ a pair $(M, \sigma)$ with $M = GL_{n_1} \times \dots \times GL_{n_r}$ and $\sigma = \sigma_1 \otimes \dots \otimes \sigma_r$ is the same as a multiset $\{\sigma_1, \dots, \sigma_r\}$ of supercuspidal representations of groups $GL_{n_i}(K)$ with $\sum n_i = n$. The local Langlands correspondence sends the supercuspidal support of $\pi$ to the semisimplification of the restriction of the Weil-Deligne representation to $W_K$, with $N$ forgotten.

### Compact induction

The supercuspidal representations are constructed by inducing from subgroups that are compact modulo the center. Let $J$ be an open subgroup of $G$ that contains $Z$ and is compact modulo $Z$. Let $(\Lambda, W)$ be an irreducible smooth representation of $J$. It has finite dimension, since $J / Z$ is compact and an open subgroup of $J$ acts trivially on a nonzero vector, so on a subspace of finite dimension that is stable under the finitely many cosets.

**Definition 1.4.7 (compact induction).** The *compactly induced representation* $\mathrm{c\text{-}Ind}_J^G \Lambda$ is the space of the functions $f : G \to W$ with $f(j g) = \Lambda(j) f(g)$ for $j \in J$, whose support is a finite union of cosets $J g$, with $G$ acting by right translation.

Lean: not stated yet. The induction `Langlands.SmoothRep.ind` of Section 1.3 has no condition on the support, so it is the full smooth induction and not $\mathrm{c\text{-}Ind}$.

For $g \in G$ let $\Lambda^g$ be the representation $x \mapsto \Lambda(g^{-1} x g)$ of $g J g^{-1}$. The element $g$ *intertwines* $\Lambda$ if $\mathrm{Hom}_{J \cap g J g^{-1}}(\Lambda, \Lambda^g) \ne 0$. By Mackey's formula, $\mathrm{End}_G(\mathrm{c\text{-}Ind}_J^G \Lambda)$ is the direct sum, over the double cosets $J g J$ of the elements $g$ that intertwine $\Lambda$, of the intertwining spaces $\mathrm{Hom}_{J \cap g J g^{-1}}(\Lambda, \Lambda^g)$.

**Theorem 1.4.8 (irreducibility of compact induction).** Suppose that an element $g \in G$ intertwines $\Lambda$ only if $g \in J$. Then $\mathrm{c\text{-}Ind}_J^G \Lambda$ is irreducible and supercuspidal.

Lean: not stated yet

*Proof.* Put $\pi = \mathrm{c\text{-}Ind}_J^G \Lambda$, and let $W_1 \subseteq \pi$ be the space of the functions supported on $J$. The map $f \mapsto f(1)$ identifies $W_1$ with $\Lambda$ as a representation of $J$. By Mackey's formula, the restriction of $\pi$ to $J$ is the direct sum over $g \in J \backslash G / J$ of the representations $\mathrm{Ind}_{J \cap g^{-1} J g}^J \Lambda^{g^{-1}}$, and by Frobenius reciprocity for the finite index subgroup $J \cap g^{-1} J g$ of $J$, the summand for $g$ contains $\Lambda$ only if $g$ intertwines $\Lambda$. So the $\Lambda$-isotypic part of $\pi |_J$ is $W_1$. The restriction $\pi|_J$ is semisimple, since $J / Z$ is compact and $Z$ acts by a character. Let $U \subseteq \pi$ be a nonzero subrepresentation. Choose $u \in U$ and $g$ with $u(g) \ne 0$. Then $u' = \pi(g) u \in U$ has $u'(1) \ne 0$. The map $f \mapsto f(1)$ is $J$-equivariant from $\pi$ to $\Lambda$, so it is zero on the isotypic parts of $\pi|_J$ of type different from $\Lambda$. So the projection of $u'$ to $W_1$ is not zero. This projection lies in $U$, since the projection to an isotypic part of a semisimple representation preserves subrepresentations. So $U \cap W_1 \ne 0$, and $W_1 \subseteq U$ since $W_1$ is irreducible. The translates of $W_1$ span $\pi$, so $U = \pi$. A matrix coefficient of $\pi$ for $v \in W_1$ and a linear form supported on $J$ has support in $J$. All the matrix coefficients are finite sums of translates of such coefficients, so they have compact support modulo $Z$. By Theorem 1.4.3, $\pi$ is supercuspidal. $\square$

**Example 1.4.9 (the supercuspidal representations of depth zero of $GL_2$).** Let $k_2$ be the quadratic extension of the residue field $k$, and let $\theta$ be a character of $k_2^\times$ with $\theta \ne \theta^q$. The theory of Deligne and Lusztig, or the classical work of Green for $GL_2$, attaches to $\theta$ an irreducible cuspidal representation $\lambda_\theta$ of $GL_2(k)$, of dimension $q - 1$. Cuspidal means that $\lambda_\theta$ has no nonzero vector fixed by the group of upper triangular unipotent matrices of $GL_2(k)$. Let $J = K^\times GL_2(\mathcal{O}_K)$, and let $\Lambda$ be the representation of $J$ that is $\lambda_\theta$ on $GL_2(\mathcal{O}_K)$, through the reduction map, and the scalar $\theta(\varpi)$ on $\varpi$, for a fixed choice. Let $g \notin J$. By the Cartan decomposition we may take $g = \mathrm{diag}(\varpi^a, 1)$ with $a \ge 1$. Then $J \cap g J g^{-1}$ contains the group $\bar N(\mathcal{O}_K)$ of the matrices $\bar n_y = \left(\begin{smallmatrix} 1 & 0 \\ y & 1 \end{smallmatrix}\right)$ with $y \in \mathcal{O}_K$, since $g^{-1} \bar n_y g = \bar n_{\varpi^a y}$. For the same reason $\Lambda^g$ is trivial on $\bar N(\mathcal{O}_K)$, because $\bar n_{\varpi^a y}$ reduces to $1$ modulo $\mathfrak{p}$. So an intertwining operator $T$ satisfies $T(\Lambda(\bar n) w) = T(w)$ for $\bar n \in \bar N(\mathcal{O}_K)$. It factors through the coinvariants of $\lambda_\theta$ under the lower unipotent group of $GL_2(k)$, which is a finite group. These coinvariants are isomorphic to the invariants, and the invariants are zero, since $\lambda_\theta$ is cuspidal and the lower and upper unipotent groups are conjugate in $GL_2(k)$. So Theorem 1.4.8 applies, and $\mathrm{c\text{-}Ind}_J^G \Lambda$ is an irreducible supercuspidal representation. These are the supercuspidal representations of *depth zero*, or *level zero*. By Chapter 3, their Langlands parameters are the representations of $W_K$ induced from tamely ramified characters of the unramified quadratic extension of $K$.

**Theorem 1.4.10 (Kutzko, Bushnell-Kutzko).** Each irreducible supercuspidal representation of $GL_n(K)$ is isomorphic to $\mathrm{c\text{-}Ind}_J^G \Lambda$ for an open subgroup $J$ that is compact modulo the center and an irreducible representation $\Lambda$ of $J$ that satisfies the hypothesis of Theorem 1.4.8.

Lean: not stated yet

For $GL_2$ this is the theorem of Kutzko [Kut80], who also proved the local Langlands correspondence for $GL_2$ in the same paper. For $GL_n$ it is the theorem of Bushnell and Kutzko on simple types, from their book of 1993 on the admissible dual of $GL_n$. The pairs $(J, \Lambda)$ are the *extended maximal simple types*. They are built from strata of the hereditary orders of $M_n(K)$, and they are unique up to conjugation. Chapter 3 recalls the description of [BH06] for $GL_2$, where $(J, \Lambda)$ comes from an admissible pair $(E / K, \xi)$, a tamely ramified quadratic extension and a character of $E^\times$, when $p \ne 2$.
