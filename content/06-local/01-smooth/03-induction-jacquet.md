---
title: Parabolic induction and Jacquet modules
nodes: []
sources: [BH06]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Parabolic induction and Jacquet modules

This section defines the two functors that connect the representations of $G$ with those of its Levi subgroups. We state everything for $G = GL_n(K)$. The definitions and the proofs work for each reductive group, with the standard parabolic subgroups attached to a minimal parabolic subgroup.

### Parabolic subgroups

Let $n = n_1 + \dots + n_r$ be a composition of $n$. The *standard parabolic subgroup* $P$ of type $(n_1, \dots, n_r)$ is the group of the invertible block upper triangular matrices with diagonal blocks of sizes $n_1, \dots, n_r$. It is a semidirect product $P = M N$. Here $M \cong GL_{n_1}(K) \times \dots \times GL_{n_r}(K)$ is the group of block diagonal matrices, the *Levi subgroup*, and $N$ is the group of block upper triangular matrices with identity blocks on the diagonal, the *unipotent radical*. For the type $(1, \dots, 1)$ we get the Borel subgroup $B = T N_0$ of upper triangular matrices, with $T$ the diagonal torus. Each parabolic subgroup, that is, each closed subgroup that contains a conjugate of $B$, is conjugate to exactly one standard one. The opposite parabolic $\bar P = M \bar N$ is the group of block lower triangular matrices.

Lean: `Langlands.GL2.borel`, `Langlands.GL2.unipotent`, `Langlands.GL2.torus`. Lean has these subgroups only for $GL_2$, defined by conditions on the entries of the matrix, and `Langlands.GL2.borel_le_normalizer_unipotent` proves that $B$ normalizes $N$.

The group $P$ is not unimodular. Its *modulus character* is $\delta_P(m n) = |\det \mathrm{Ad}(m)|_{\mathrm{Lie}\, N}|$. For $m = (m_1, \dots, m_r)$ it is
$$\delta_P(m) = \prod_{i < j} |\det m_i|^{n_j} |\det m_j|^{-n_i}.$$
For the Borel subgroup of $GL_2$, $\delta_B \left(\begin{smallmatrix} a & x \\ 0 & d \end{smallmatrix}\right) = |a / d|$. The Iwasawa decomposition $G = P K_0$, with $K_0 = GL_n(\mathcal{O}_K)$, shows that $P \backslash G$ is compact.

### Parabolic induction

**Definition 1.3.1 (parabolic induction).** Let $P = MN$ be a parabolic subgroup and $(\sigma, W)$ a smooth representation of $M$. The *normalized parabolically induced representation* $\mathrm{Ind}_P^G \sigma$ is the space of the functions $f : G \to W$ such that
1. $f(m n g) = \delta_P(m)^{1/2} \sigma(m) f(g)$ for $m \in M$, $n \in N$, $g \in G$, and
2. there is a compact open subgroup $J$ with $f(g j) = f(g)$ for each $g \in G$ and $j \in J$.

The group $G$ acts by right translation, $(g \cdot f)(x) = f(x g)$. For $GL_n$ and $\sigma = \sigma_1 \otimes \dots \otimes \sigma_r$ we write $\sigma_1 \times \dots \times \sigma_r$ for $\mathrm{Ind}_P^G \sigma$.

Lean: `Langlands.SmoothRep.ind`, and `Langlands.principalSeries` for the Borel subgroup of $GL_2$. `SmoothRep.ind H σ` is the unnormalized induction from any subgroup $H$ of a smooth representation $\sigma$ of $H$, so the normalized $\mathrm{Ind}_P^G \sigma$ is `SmoothRep.ind` applied to the representation $mn \mapsto \delta_P(m)^{1/2} \sigma(m)$ of $P$.

The factor $\delta_P^{1/2}$ is the normalization. With it, the induction of a unitary representation is unitary, and the induction commutes with taking contragredients (Proposition 1.3.4). The Lean project has two forms of the principal series of $GL_2$. The first, `Langlands.principalSeries K χ₁ χ₂`, is $\chi_1 \times \chi_2$, the space of the locally constant functions with $f(bg) = \chi_1(a) \chi_2(d) |a/d|^{1/2} f(g)$.

Lean: `Langlands.principalSeriesInd`, `Langlands.GL2.borelChar`. This second form is `SmoothRep.ind` from `Langlands.GL2.borel` of the character $\chi_1 \otimes \chi_2$ of $B$, so it is not normalized: its functions satisfy $f(bg) = \chi_1(a) \chi_2(d) f(g)$, and it is $\chi_1 |\cdot|^{-1/2} \times \chi_2 |\cdot|^{1/2}$ in the notation of the text.

The two forms are not compared in Lean. The file `GSp4.lean` defines the principal series of $GSp_4$ in the same way as `Langlands.principalSeries`, see Section 3.6.

### Jacquet modules

**Definition 1.3.2 (Jacquet module).** Let $P = MN$ be a parabolic subgroup and $(\pi, V)$ a smooth representation of $G$. Let $V(N)$ be the subspace spanned by the vectors $\pi(n) v - v$ with $n \in N$ and $v \in V$. The *Jacquet module* is the space $V_N = V / V(N)$ of $N$-coinvariants, with the action of $M$ given by
$$r_P(\pi)(m) (v + V(N)) = \delta_P(m)^{-1/2} \pi(m) v + V(N).$$
We write $r_P(\pi)$ or $\pi_N$ for this representation of $M$.

Lean: `Langlands.SmoothRep.jacquet`, with $V(N)$ as `Langlands.SmoothRep.jacquetKer`. The Lean Jacquet module is not normalized, since $M$ acts by $\pi(m)$ with no factor $\delta_P(m)^{-1/2}$, and $M$ and $N$ are any two subgroups of $G$ with $M$ in the normalizer of $N$.

The subspace $V(N)$ is $M$-stable, because $M$ normalizes $N$. The Jacquet module is the largest quotient of $V$ on which $N$ acts trivially. So a map from $V_N$ to a representation $\tau$ of $M$ is the same as an $M$-map $V \to \tau$ that is invariant under $N$. The normalization by $\delta_P^{-1/2}$ is the one that makes the statements below symmetric. Some authors leave it out. The normalization changes the central characters of the constituents by explicit powers of $|\cdot|$, so we always use the normalized one.

Lean: `Langlands.SmoothRep.jacquetKer_stable`, `Langlands.SmoothRep.jacquetEquiv`. The universal property is a linear isomorphism from $\mathrm{Hom}_M(V_N, \tau)$ onto the $N$-invariant $M$-maps $V \to \tau$, which are `Langlands.SmoothRep.nInvariantHom`, for the unnormalized $V_N$.

**Theorem 1.3.3 (Frobenius reciprocity).** Let $\pi$ be a smooth representation of $G$ and $\sigma$ a smooth representation of $M$. There is a natural isomorphism
$$\mathrm{Hom}_G(\pi, \mathrm{Ind}_P^G \sigma) \cong \mathrm{Hom}_M(r_P(\pi), \sigma).$$

Lean: `Langlands.SmoothRep.frobenius`. The Lean isomorphism is $\mathrm{Hom}_G(\pi, \mathrm{Ind}_H^G \sigma) \cong \mathrm{Hom}_H(\pi|_H, \sigma)$ for the unnormalized induction from any subgroup $H$, with no Jacquet module.

*Proof.* Let $\mathrm{ev} : \mathrm{Ind}_P^G \sigma \to W$ be the evaluation $f \mapsto f(1)$. It satisfies $\mathrm{ev}(n \cdot f) = f(n) = f(1)$ and $\mathrm{ev}(m \cdot f) = \delta_P(m)^{1/2} \sigma(m) f(1)$. So $\mathrm{ev}$ factors through the Jacquet module. Because of the factor $\delta_P(m)^{-1/2}$ in the action of $r_P$, the map $\mathrm{ev}$ is $M$-equivariant from $r_P(\mathrm{Ind}_P^G \sigma)$ to $\sigma$. Given $A : \pi \to \mathrm{Ind}_P^G \sigma$, put $\alpha(v) = (A v)(1)$. Then $\alpha$ factors through $r_P(\pi)$ and is $M$-equivariant. Conversely, given $\alpha : r_P(\pi) \to \sigma$, put $(A v)(g) = \alpha(\pi(g) v + V(N))$. One checks that $A v$ satisfies condition 1 of Definition 1.3.1: $(A v)(m n g) = \alpha(\pi(m) \pi(n) \pi(g) v) = \delta_P(m)^{1/2} \sigma(m) \alpha(\pi(g) v)$, by the definition of the normalized action. Condition 2 holds since $v$ is smooth. The two constructions are inverse to each other. $\square$

The Lean proof splits this argument in two steps. Let $\sigma'$ be the representation $mn \mapsto \delta_P(m)^{1/2} \sigma(m)$ of $P$. First, `SmoothRep.frobenius` for $H = P$ gives $\mathrm{Hom}_G(\pi, \mathrm{Ind}_P^G \sigma) \cong \mathrm{Hom}_P(\pi|_P, \sigma')$, with the maps $A \mapsto (v \mapsto (Av)(1))$ and $\alpha \mapsto (v \mapsto (g \mapsto \alpha(\pi(g) v)))$ of the proof above. This step checks identities of functions and uses no property of $P$, so Lean proves it for every subgroup. Second, a $P$-map $\pi|_P \to \sigma'$ is an $M$-map that is invariant under $N$, since $N$ acts trivially on $\sigma'$. By `SmoothRep.jacquetEquiv` these maps are the $M$-maps from the unnormalized $V_N$ to $\delta_P^{1/2} \sigma$, that is, the maps $r_P(\pi) \to \sigma$. The proof in the text does the two steps at once. The Lean project does not state the composite isomorphism of Theorem 1.3.3.

**Proposition 1.3.4 (properties of induction).** Let $P = MN$ be a parabolic subgroup of $G$.
1. The functor $\mathrm{Ind}_P^G$ is exact.
2. If $\sigma$ is admissible, then $\mathrm{Ind}_P^G \sigma$ is admissible. If $\sigma$ is finitely generated, then $\mathrm{Ind}_P^G \sigma$ is finitely generated.
3. $(\mathrm{Ind}_P^G \sigma)^\vee \cong \mathrm{Ind}_P^G (\sigma^\vee)$.
4. If $\sigma$ is unitary, then $\mathrm{Ind}_P^G \sigma$ is unitary.
5. (Transitivity) If $Q \subseteq P$ is a parabolic subgroup with Levi subgroup $L \subseteq M$, and $\tau$ is a smooth representation of $L$, then $\mathrm{Ind}_P^G \mathrm{Ind}_{Q \cap M}^M \tau \cong \mathrm{Ind}_Q^G \tau$.

Lean: not stated yet. Only the fact that induction keeps injections, a part of part 1, is in Lean, as `Langlands.SmoothRep.indMap_injective` for the unnormalized induction from any subgroup.

*Proof.* By the Iwasawa decomposition, restriction of functions to $K_0$ is an isomorphism of $K_0$-representations from $\mathrm{Ind}_P^G \sigma$ to the space of smooth functions $f : K_0 \to W$ with $f(p k) = \sigma(p) f(k)$ for $p \in P \cap K_0$. Here $\delta_P$ is trivial on $P \cap K_0$, since $\delta_P$ takes values in $q^\mathbb{Z}$ and is trivial on compact subgroups. For part 1, exactness at the left and in the middle is clear. For surjectivity, let $\sigma \to \sigma''$ be surjective and $f'' \in \mathrm{Ind} \sigma''$ fixed by $J \subseteq K_0$ normal. Then $f''$ on $K_0$ is determined by its values on the finite set $(P \cap K_0) \backslash K_0 / J$. Lift each value to $W$, average the lift over the compact group $(P \cap K_0) \cap x J x^{-1}$ as in Proposition 1.1.4, and extend. For part 2, a $J$-fixed function on $K_0$ is determined by its values on the finite set $(P \cap K_0) \backslash K_0 / J$, and the value at $x$ lies in $W^{M \cap x J x^{-1}}$, which has finite dimension. Finite generation is similar. For part 3, the product $f(g) \lambda(g)$ of $f \in \mathrm{Ind}\, \sigma$ and $\lambda \in \mathrm{Ind}\, \sigma^\vee$, paired by $\sigma$ and $\sigma^\vee$, is a function $h$ with $h(pg) = \delta_P(p) h(g)$. On the space of such functions there is a unique $G$-invariant linear form up to a scalar, namely $h \mapsto \int_{K_0} h(k) \, dk$. This gives a nondegenerate invariant pairing, and by part 2 and Proposition 1.1.6 it identifies the two sides. Part 4 is the same argument with the Hermitian form. Part 5 follows from the definitions, since $\delta_Q = \delta_P \cdot \delta_{Q \cap M}$ on $L$. $\square$

The factor $\delta_P^{1/2}$ is exactly what makes part 3 and part 4 true. Without it, the dual of the induction of $\sigma$ is the induction of $\sigma^\vee \otimes \delta_P$.

### Exactness of the Jacquet functor

**Proposition 1.3.5 (Jacquet modules are exact).** Let $N$ be the unipotent radical of a parabolic subgroup.
1. A vector $v \in V$ lies in $V(N)$ if and only if $\int_{N_0} \pi(n) v \, dn = 0$ for some compact open subgroup $N_0$ of $N$.
2. The functor $V \mapsto V_N$ is exact.

Lean: not stated yet. Lean proves only that $V \mapsto V_N$ keeps surjections, as `Langlands.SmoothRep.jacquetMap_surjective`, and this holds for every subgroup $N$.

*Proof.* The group $N$ is the union of an increasing sequence of compact open subgroups $N_0 \subset N_1 \subset \dots$, for example $N_k = d^k N_0 d^{-k}$ with $N_0 = N \cap GL_n(\mathcal{O}_K)$ and $d = \mathrm{diag}(\varpi^{-(n-1)}, \dots, \varpi^{-1}, 1)$. The group $N_k$ is the set of the matrices in $N$ whose entry $(i, j)$ lies in $\mathfrak{p}^{-k(j - i)}$. The set of the matrices in $N$ with all entries in $\mathfrak{p}^{-k}$ is not a group in general, for example for the Borel subgroup of $GL_3$. If $\int_{N_k} \pi(n) v \, dn = 0$, then $v \in V(N_k) \subseteq V(N)$ by Proposition 1.1.4 for the compact group $N_k$. Conversely, $V(N)$ is spanned by the vectors $\pi(n) v - v$, and each such vector lies in $V(N_k)$ for $k$ with $n \in N_k$. Then $\int_{N_k} \pi(n') (\pi(n) v - v) \, dn' = 0$. This proves part 1. For part 2, the functor of coinvariants is right exact for every group. Let $U \subseteq V$ be a subrepresentation and $u \in U$ with $u \in V(N)$. By part 1, $\int_{N_k} \pi(n) u \, dn = 0$ for some $k$, and the same integral shows $u \in U(N)$. So $U_N \to V_N$ is injective. $\square$

The exactness is special to $p$-adic groups. It holds because $N$ is a union of compact subgroups, and it fails for real groups.

### Jacquet's lemma

The following lemma connects the Jacquet module with the fixed vectors of small compact open subgroups. Let $P = MN$ be standard and let $J$ be a compact open subgroup with an *Iwahori decomposition*
$$J = (J \cap \bar N)(J \cap M)(J \cap N).$$
The groups $K_r$ with $r \ge 1$ have such a decomposition for each standard parabolic subgroup. Let $z$ be an element of the center of $M$ that contracts $N$, that is, $z^k n z^{-k} \to 1$ for $n \in N$ as $k \to \infty$. For the Borel subgroup of $GL_2$ we can take $z = \mathrm{diag}(\varpi, 1)$. Then $z$ also expands $\bar N$, and $z^{-1} (J \cap \bar N) z \subseteq J \cap \bar N$.

**Theorem 1.3.6 (Jacquet's lemma).** Let $J$ be as above, and let $(\pi, V)$ be an admissible representation of $G$.
1. The projection $p : V^J \to (V_N)^{J \cap M}$ is surjective.
2. The Jacquet module $V_N$ is admissible.

Lean: not stated yet

*Proof.* Put $J_- = J \cap \bar N$, $J_0 = J \cap M$ and $J_+ = J \cap N$. Then $J = J_+ J_0 J_-$, and $e_J = e_{J_+} * e_{J_0} * e_{J_-}$. The group $J_0$ acts trivially on $(V_N)^{J_0}$, and $\delta_P$ is trivial on $J_0$. Two facts are used. First, $e_{J_+} x$ and $x$ have the same image in $V_N$ for each $x$, since $\pi(n) x - x \in V(N)$. Second, if $x$ is fixed by $J_-$ and its image is fixed by $J_0$, then $e_J x = e_{J_+} e_{J_0} x$ has the same image as $x$.

Let $\bar v \in (V_N)^{J_0}$ and let $v$ be a lift. Choose a compact open subgroup $J' \subseteq J$ with an Iwahori decomposition that fixes $v$. Since $z^{-1}$ contracts $\bar N$, there is $k \ge 0$ with $z^{-k} J_- z^k \subseteq J' \cap \bar N$. Then $u = \pi(z^k) v$ is fixed by $J_-$, and its image $\delta_P(z)^{k/2} r_P(\pi)(z)^k \bar v$ is fixed by $J_0$, since $z$ is central in $M$. By the second fact, $e_J u \in V^J$ has this image. So the image $I = p(V^J)$ contains $r_P(\pi)(z)^k \bar v$. The same facts show that $p(e_J \pi(z) x) = \delta_P(z)^{1/2} r_P(\pi)(z) p(x)$ for $x \in V^J$, because $\pi(z) x$ is fixed by $z J_- z^{-1} \supseteq J_-$. So $I$ is stable under $r_P(\pi)(z)$. The space $I$ has finite dimension, since $V$ is admissible, and $r_P(\pi)(z)$ is invertible. So $r_P(\pi)(z)$ is a bijection of $I$, and $\bar v = r_P(\pi)(z)^{-k} \big(r_P(\pi)(z)^k \bar v\big) \in I$. This proves part 1. For part 2, $(V_N)^{J_0}$ is the image of the finite-dimensional space $V^J$, and the groups $J \cap M$ form a basis of neighbourhoods of $1$ in $M$ as $J$ runs over the $K_r$. $\square$

Part 1 holds for every smooth representation, and the Jacquet module of a finitely generated representation is finitely generated. The proofs are in Bernstein's notes. A finer version of part 1 is due to Casselman. For $V$ admissible, the projection $V^J \to (V_N)^{J \cap M}$ is an isomorphism on the image of the Hecke operator $e_J \pi(z^k) e_J$ for $k$ large. Casselman used this to define a canonical pairing between $r_P(\pi)$ and $r_{\bar P}(\pi^\vee)$.

### Second adjointness and the geometric lemma

Frobenius reciprocity says that $r_P$ is left adjoint to $\mathrm{Ind}_P^G$. Bernstein proved that $r_{\bar P}$ is also right adjoint to it. This is a deep theorem, and we only state it.

**Theorem 1.3.7 (Bernstein's second adjointness).** Let $P = MN$ be a parabolic subgroup with opposite $\bar P = M \bar N$. For smooth representations $\sigma$ of $M$ and $\pi$ of $G$ there is a natural isomorphism
$$\mathrm{Hom}_G(\mathrm{Ind}_P^G \sigma, \pi) \cong \mathrm{Hom}_M(\sigma, r_{\bar P}(\pi)).$$

Lean: not stated yet

The theorem implies that $\mathrm{Ind}_P^G$ sends projective objects to projective objects, and that the category of smooth representations is Noetherian. Bernstein's proof uses his stabilization theorem for the spaces $V^J$. A proof is in the notes of Bernstein and in the book of Renard.

The second tool computes the Jacquet module of an induced representation. Let $W = S_n$ be the Weyl group of $T$ in $GL_n$, realized by permutation matrices. Let $P = MN$ and $Q = LU$ be standard parabolic subgroups. The *Bruhat decomposition* writes $G$ as the finite disjoint union of the double cosets $P w Q$, where $w$ runs over a set $W^{M, L}$ of representatives of $W_M \backslash W / W_L$ of minimal length. These double cosets can be ordered so that each union of an initial segment is open.

**Theorem 1.3.8 (the geometric lemma of Bernstein and Zelevinsky).** Let $\sigma$ be a smooth representation of $M$. The representation $r_Q(\mathrm{Ind}_P^G \sigma)$ of $L$ has a filtration indexed by $W^{M, L}$ whose subquotient for $w$ is
$$\mathrm{Ind}_{L \cap w^{-1} P w}^{L} \big( w^{-1} \circ r_{M \cap w Q w^{-1}}(\sigma) \big).$$
In particular, for $P = Q = B$ and a character $\chi = \chi_1 \otimes \dots \otimes \chi_n$ of $T$, the semisimplification of $r_B(\chi_1 \times \dots \times \chi_n)$ is $\bigoplus_{w \in S_n} w \chi$, where $(w\chi)_i = \chi_{w^{-1}(i)}$.

Lean: not stated yet

*Sketch of proof.* Filter $\mathrm{Ind}_P^G \sigma$ by the support of the functions in the open unions of the double cosets $P w Q$. The Jacquet functor is exact by Proposition 1.3.5, so it carries this filtration to a filtration of the Jacquet module. The subquotient for $w$ is the space of functions with compact support modulo $P$ on $P w Q$. Its Jacquet module is computed with the identification $P \backslash P w Q \cong (Q \cap w^{-1} P w) \backslash Q$ and Frobenius reciprocity in stages. The modulus characters fit together because of the normalizations. For $P = Q = B$ each piece is a character of $T$, and the character for $w$ is $w \chi$. $\square$

For $GL_2$ and $\chi = \chi_1 \otimes \chi_2$, the lemma says that there is an exact sequence of representations of $T$
$$0 \to \chi_2 \otimes \chi_1 \to r_B(\chi_1 \times \chi_2) \to \chi_1 \otimes \chi_2 \to 0.$$
The quotient comes from the closed orbit $B$, through evaluation at $1$, and the subspace from the open orbit $B w B$. Section 1.5 uses this sequence to find the reducible principal series of $GL_2$.

Lean: `Langlands.principalSeriesJacquet`. It is the Jacquet module, for `Langlands.GL2.unipotent` and as a representation of `Langlands.GL2.torus`, of the unnormalized `Langlands.principalSeriesInd`, and the exact sequence is not stated in Lean.
