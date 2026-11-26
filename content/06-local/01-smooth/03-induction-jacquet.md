---
title: Parabolic induction and Jacquet modules
nodes: []
sources: [BH06]
status: checked
drafted_by: writer
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## Parabolic induction and Jacquet modules

This section defines the two functors that connect the representations of $G$ with those of its Levi subgroups. We state everything for $G = GL_n(K)$. The definitions and the proofs work for each reductive group, with the standard parabolic subgroups attached to a minimal parabolic subgroup.

### Parabolic subgroups

Let $n = n_1 + \dots + n_r$ be a composition of $n$. The *standard parabolic subgroup* $P$ of type $(n_1, \dots, n_r)$ is the group of the invertible block upper triangular matrices with diagonal blocks of sizes $n_1, \dots, n_r$. It is a semidirect product $P = M N$. Here $M \cong GL_{n_1}(K) \times \dots \times GL_{n_r}(K)$ is the group of block diagonal matrices, the *Levi subgroup*, and $N$ is the group of block upper triangular matrices with identity blocks on the diagonal, the *unipotent radical*. For the type $(1, \dots, 1)$ we get the Borel subgroup $B = T N_0$ of upper triangular matrices, with $T$ the diagonal torus. Each parabolic subgroup, that is, each closed subgroup that contains a conjugate of $B$, is conjugate to exactly one standard one. The opposite parabolic $\bar P = M \bar N$ is the group of block lower triangular matrices.

Lean: `Langlands.GL2.borel`, `Langlands.GL2.unipotent`, `Langlands.GL2.torus`. Lean has these subgroups only for $GL_2$, defined by conditions on the entries of the matrix, and `Langlands.GL2.borel_le_normalizer_unipotent` proves that $B$ normalizes $N$.

If $P \ne G$, the group $P$ is not unimodular. Its *modulus character* is $\delta_P(m n) = |\det \mathrm{Ad}(m)|_{\mathrm{Lie}\, N}|$. For $m = (m_1, \dots, m_r)$ it is
$$\delta_P(m) = \prod_{i < j} |\det m_i|^{n_j} |\det m_j|^{-n_i}.$$
For the Borel subgroup of $GL_2$, $\delta_B \left(\begin{smallmatrix} a & x \\ 0 & d \end{smallmatrix}\right) = |a / d|$.

Lean: `Langlands.GL2.modulus`, `Langlands.GL2.sqrtModulus`, `Langlands.GL2.modulus_apply`, `Langlands.GL2.sqrtModulus_sq`, `Langlands.GL2.conj_unipotent_val`. Lean defines $\delta_B$ as the character $|\cdot| \otimes |\cdot|^{-1}$ of $B$ and $\delta_B^{1/2}$ as $|\cdot|^{1/2} \otimes |\cdot|^{-1/2}$, and it proves $\delta_B(b) = |a/d|$ and $(\delta_B^{1/2})^2 = \delta_B$. The theorem `conj_unipotent_val` says that $b n(x) b^{-1} = n(ax/d)$ for $n(x) = \left(\begin{smallmatrix} 1 & x \\ 0 & 1 \end{smallmatrix}\right)$, so $|a/d|$ is $|\det \mathrm{Ad}(b)|_{\mathrm{Lie}\, N}|$. Lean does not identify $\delta_B$ with the modulus of a Haar measure of $B$.

The Iwasawa decomposition $G = P K_0$, with $K_0 = GL_n(\mathcal{O}_K)$, shows that $P \backslash G$ is compact. We prove it for $GL_2$, where it is used most in this chapter.

*Lemma (the Iwasawa decomposition for $GL_2$).* Let $G = GL_2(K)$, let $B$ be its upper triangular Borel subgroup and let $K_0 = GL_2(\mathcal{O}_K)$.
1. The group $K_0$ is a compact open subgroup of $G$.
2. Each $g \in G$ is a product $g = bk$ with $b \in B$ and $k \in K_0$. Thus $G = B K_0$.
3. Let $g = bk$ be such a product, let $(a, d)$ be the diagonal of $b$ and let $(r, s)$ be the lower row of $g$. Then $|d| = \max(|r|, |s|)$ and $|a| = |\det g| / |d|$. Two such products for the same $g$ differ by an element of $B \cap K_0$, that is, $b k = b' k'$ implies $b' = b u$ and $k' = u^{-1} k$ with $u \in B \cap K_0$.

Lean: `Langlands.GL2.maxCompact`, `Langlands.GL2.isCompact_maxCompact`, `Langlands.GL2.iwasawa`. Lean defines $K_0$ as the group of the $g$ such that $g$ and $g^{-1}$ have entries in $\mathcal{O}_K$, and it proves part 2 and the compactness in part 1. The proof of part 2 in Lean is the one below, with the matrices `Langlands.GL2.lowerUnip` and `Langlands.GL2.weylShear`. Part 3 and the openness of $K_0$ are not stated in Lean.

*Proof.* A matrix $g \in M_2(\mathcal{O}_K)$ is in $K_0$ if and only if $\det g \in \mathcal{O}_K^\times$, since $g^{-1} = (\det g)^{-1} \mathrm{adj}(g)$. For part 1, the map $g \mapsto (g, g^{-1})$ is a homeomorphism of $G$ onto the closed subset $\{(x, y) : xy = yx = 1\}$ of $M_2(K) \times M_2(K)$. It maps $K_0$ onto the intersection of this closed set with $M_2(\mathcal{O}_K) \times M_2(\mathcal{O}_K)$. This product is compact and open, since $\mathcal{O}_K$ is compact and open in $K$. So $K_0$ is compact and open.

For part 2, note that $g \mapsto g k^{-1}$ acts on the columns of $g$, and that $g k^{-1} \in B$ if and only if the lower left entry of $g k^{-1}$ is $0$. Let $(r, s)$ be the lower row of $g$. It is not zero, since $\det g \ne 0$. Suppose first that $|r| \le |s|$. Then $s \ne 0$ and $c = r/s \in \mathcal{O}_K$. Put
$$k = \begin{pmatrix} 1 & 0 \\ c & 1 \end{pmatrix} \in K_0, \qquad k^{-1} = \begin{pmatrix} 1 & 0 \\ -c & 1 \end{pmatrix}.$$
The lower row of $g k^{-1}$ is $(r - cs, s) = (0, s)$. Suppose next that $|r| > |s|$. Then $r \ne 0$ and $c = s/r \in \mathfrak{p}_K$. Put
$$k = \begin{pmatrix} 0 & -1 \\ 1 & c \end{pmatrix} \in K_0, \qquad k^{-1} = \begin{pmatrix} c & 1 \\ -1 & 0 \end{pmatrix}.$$
Here $\det k = 1$. The lower row of $g k^{-1}$ is $(rc - s, r) = (0, r)$. In both cases $b = g k^{-1} \in B$ and $g = bk$.

For part 3, the lower row of $g = bk$ is $d$ times the lower row $(r', s')$ of $k$. The entries $r', s'$ are in $\mathcal{O}_K$, and they are not both in $\mathfrak{p}_K$, since otherwise $\det k \in \mathfrak{p}_K$. So $\max(|r'|, |s'|) = 1$ and $\max(|r|, |s|) = |d|$. Also $|\det g| = |a| |d| |\det k| = |a| |d|$. If $b k = b' k'$, then $u = b^{-1} b' = k k'^{-1}$ lies in $B \cap K_0$. $\square$

By part 3, $\delta_B(b) = |a/d| = |\det g| / \max(|r|, |s|)^2$ depends only on $g$ and not on the choice of the decomposition. The same proof works for $GL_n$, by induction on $n$. In the last row of $g$, choose an entry of largest absolute value and move it to the last column with a permutation matrix. Column operations by elements of $\mathcal{O}_K$ then make the other entries of the last row zero, and the induction hypothesis applies to the upper left block of size $n - 1$. This gives $GL_n(K) = B K_0$, and so $G = P K_0$ for each standard parabolic subgroup $P$. Then $P \backslash G$ is the image of the compact set $K_0$, so it is compact.

### Parabolic induction

**Definition 1.3.1 (parabolic induction).** Let $P = MN$ be a parabolic subgroup and $(\sigma, W)$ a smooth representation of $M$. The *normalized parabolically induced representation* $\mathrm{Ind}_P^G \sigma$ is the space of the functions $f : G \to W$ such that
1. $f(m n g) = \delta_P(m)^{1/2} \sigma(m) f(g)$ for $m \in M$, $n \in N$, $g \in G$, and
2. there is a compact open subgroup $J$ with $f(g j) = f(g)$ for each $g \in G$ and $j \in J$.

The group $G$ acts by right translation, $(g \cdot f)(x) = f(x g)$. For $GL_n$ and $\sigma = \sigma_1 \otimes \dots \otimes \sigma_r$ we write $\sigma_1 \times \dots \times \sigma_r$ for $\mathrm{Ind}_P^G \sigma$.

Lean: `Langlands.SmoothRep.ind`, and `Langlands.principalSeries` for the Borel subgroup of $GL_2$. `SmoothRep.ind H σ` is the unnormalized induction from any subgroup $H$ of a smooth representation $\sigma$ of $H$, so the normalized $\mathrm{Ind}_P^G \sigma$ is `SmoothRep.ind` applied to the representation $mn \mapsto \delta_P(m)^{1/2} \sigma(m)$ of $P$.

The factor $\delta_P^{1/2}$ is the normalization. With it, the induction of a unitary representation is unitary, and the induction commutes with taking contragredients (Proposition 1.3.4). The Lean project has two forms of the principal series of $GL_2$. The first, `Langlands.principalSeries K χ₁ χ₂`, is $\chi_1 \times \chi_2$, the space of the locally constant functions with $f(bg) = \chi_1(a) \chi_2(d) |a/d|^{1/2} f(g)$.

Lean: `Langlands.principalSeriesInd`, `Langlands.GL2.borelChar`. This second form is `SmoothRep.ind` from `Langlands.GL2.borel` of the character $\chi_1 \otimes \chi_2$ of $B$, so it is not normalized: its functions satisfy $f(bg) = \chi_1(a) \chi_2(d) f(g)$, and it is $\chi_1 |\cdot|^{-1/2} \times \chi_2 |\cdot|^{1/2}$ in the notation of the text.

Lean: `Langlands.normPrincipalSeries`, `Langlands.normPrincipalSeries_eq`, `Langlands.normPrincipalSeries_iso`. The first is `SmoothRep.ind` from `Langlands.GL2.borel` of the character $(\chi_1 \otimes \chi_2) \delta_B^{1/2}$ of $B$, which is Definition 1.3.1 for $P = B$ with `GL2.sqrtModulus` as $\delta_B^{1/2}$. The second says that it is equal to `principalSeriesInd` of $\chi_1 |\cdot|^{1/2}$ and $\chi_2 |\cdot|^{-1/2}$. The third is an isomorphism from it onto `Langlands.principalSeries K χ₁ χ₂` that sends each function to the same function. So the two forms of the principal series agree in Lean.

The file `GSp4.lean` defines the principal series of $GSp_4$ in the same way as `Langlands.principalSeries`, see Section 3.6.

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

Lean: `Langlands.SmoothRep.indMap_injective`, `Langlands.SmoothRep.ind_isAdmissible`, `Langlands.SmoothRep.ind_borel_ext`, `Langlands.principalSeries_isAdmissible`. The proposition is not stated in Lean, and these are parts of it for the unnormalized induction. `indMap_injective` says that induction from any subgroup keeps injections, a part of part 1. `ind_isAdmissible` is a form of part 2: if $G = HC$ with $C$ compact, then the induction from $H$ of a representation of finite dimension is admissible. With the Iwasawa decomposition it gives `Langlands.principalSeriesInd_isAdmissible`, `Langlands.normPrincipalSeries_isAdmissible` and `principalSeries_isAdmissible`, the admissibility of the principal series of $GL_2$ in each of its forms. `ind_borel_ext` says that a vector of a representation induced from $B$ is determined by its restriction to $K_0$, which is the injectivity of the restriction map in the proof below.

*Proof.* Let $\mathcal{F}$ be the space of the smooth functions $f : K_0 \to W$ with $f(p k) = \sigma(p) f(k)$ for $p \in P \cap K_0$. Here $\delta_P$ is trivial on $P \cap K_0$, since $\delta_P$ takes values in $q^\mathbb{Z}$ and the only compact subgroup of $q^\mathbb{Z}$ is $\{1\}$. Restriction of functions to $K_0$ is an isomorphism of $K_0$-representations from $\mathrm{Ind}_P^G \sigma$ onto $\mathcal{F}$. It is injective, since $G = P K_0$ by the Iwasawa decomposition and $f(pk) = \delta_P(p)^{1/2} \sigma(p) f(k)$. It is surjective, since for $f \in \mathcal{F}$ the formula $f(pk) = \delta_P(p)^{1/2} \sigma(p) f(k)$ extends $f$ to $G$: if $pk = p'k'$, then $p'^{-1} p = k' k^{-1}$ lies in $P \cap K_0$, so the formula gives one value.

Let $J$ be an open normal subgroup of $K_0$. These subgroups form a basis of neighbourhoods of $1$, for example the groups $K_r$. The set $X = (P \cap K_0) \backslash K_0 / J$ is finite, since $K_0$ is compact and $J$ is open, so $K_0 / J$ is finite. By the Iwasawa decomposition, $X$ is also the set $P \backslash G / J$. Let $J_M$ be the image of $P \cap J$ in $M$. It is compact, and it is open in $M$ since it contains $M \cap J$. Fix a set of representatives $x \in K_0$ of $X$. If $f \in \mathcal{F}$ is fixed by $J$ and $p \in P \cap J$, then $x^{-1} p x \in J$, because $J$ is normal in $K_0$. So $\sigma(p) f(x) = f(px) = f(x \cdot x^{-1} p x) = f(x)$, and $f(x) \in W^{J_M}$. Conversely, for each family $(w_x)$ with $w_x \in W^{J_M}$, the formula $f(p x j) = \sigma(p) w_x$ for $p \in P \cap K_0$ and $j \in J$ defines a $J$-fixed function in $\mathcal{F}$. It is well defined, since $p x j = p' x j'$ implies $p'^{-1} p = x j' j^{-1} x^{-1} \in P \cap J$. Thus
$$(\mathrm{Ind}_P^G \sigma)^J \cong \bigoplus_{x \in X} W^{J_M}, \qquad f \mapsto (f(x))_x, \tag{1}$$
and this isomorphism is natural in $\sigma$.

For part 1, exactness at the left and in the middle is clear. Let $\sigma \to \sigma''$ be surjective. By Proposition 1.1.4 for the compact open subgroup $J_M$ of $M$, the map $W^{J_M} \to W''^{J_M}$ is surjective. By (1), $(\mathrm{Ind}\, \sigma)^J \to (\mathrm{Ind}\, \sigma'')^J$ is surjective for each $J$, and so $\mathrm{Ind}\, \sigma \to \mathrm{Ind}\, \sigma''$ is surjective. For part 2, let $\sigma$ be admissible. Then $W^{J_M}$ has finite dimension, $X$ is finite, and so $(\mathrm{Ind}_P^G \sigma)^J$ has finite dimension by (1). Each compact open subgroup $J'$ contains such a $J$, and $V^{J'} \subseteq V^J$, so $\mathrm{Ind}_P^G \sigma$ is admissible. Finite generation is similar. For part 3, the product $f(g) \lambda(g)$ of $f \in \mathrm{Ind}\, \sigma$ and $\lambda \in \mathrm{Ind}\, \sigma^\vee$, paired by $\sigma$ and $\sigma^\vee$, is a function $h$ with $h(pg) = \delta_P(p) h(g)$. On the space of such functions there is a unique $G$-invariant linear form up to a scalar, namely $h \mapsto \int_{K_0} h(k) \, dk$. This gives an invariant pairing, and so a map $\mathrm{Ind}\, \sigma^\vee \to (\mathrm{Ind}\, \sigma)^\vee$. It is enough to show that it is bijective on the $J$-fixed vectors for each $J$ as above. The $J$-fixed vectors of $(\mathrm{Ind}\, \sigma)^\vee$ are the dual of $(\mathrm{Ind}\, \sigma)^J$, by the remark after Definition 1.1.5. On the $J$-fixed vectors the pairing is $\sum_{x \in X} \mathrm{vol}((P \cap K_0) x J) \langle f(x), \lambda(x) \rangle$, since the integrand is constant on each double coset. With (1) for $\sigma$ and for $\sigma^\vee$, and with $(W^\vee)^{J_M} = (W^{J_M})^*$, the map is a direct sum of isomorphisms multiplied by nonzero volumes. So it is an isomorphism. This argument does not need $\sigma$ to be admissible. Part 4 is the same argument with the Hermitian form. Part 5 follows from the definitions, since $\delta_Q = \delta_P \cdot \delta_{Q \cap M}$ on $L$. $\square$

The Lean proof of `SmoothRep.ind_isAdmissible` is shorter than the proof of part 2 and does not use double cosets. Let $U$ be an open subgroup of $G$. The compact set $C$ is covered by finitely many cosets $x U$ with $x$ in a finite set $t \subseteq C$. A $U$-fixed vector $f$ satisfies $f(c) = f(x)$ for $c \in xU$, and $f(hc) = \sigma(h) f(c)$, so $f$ is determined by its values on $t$. So $V^U$ embeds in $W^t$, which has finite dimension. This proof needs $W$ to have finite dimension, which is the case for the principal series, and it works for each open subgroup $U$, not only for the subgroups of $K_0$.

The factor $\delta_P^{1/2}$ is exactly what makes part 3 and part 4 true. Without it, the dual of the induction of $\sigma$ is the induction of $\sigma^\vee \otimes \delta_P$.

### Exactness of the Jacquet functor

Over a $p$-adic field the space $V(N)$ has a second description, by averages over compact open subgroups of $N$, and this description makes the Jacquet functor exact. We first define the averages without measure theory. Let $(\pi, V)$ be a smooth representation of a topological group, let $N_0$ be a compact subgroup and let $v \in V$. The stabilizer $S_v = \{ n \in N_0 : \pi(n) v = v \}$ is open in $N_0$, since $v$ is smooth, so it has finite index in $N_0$. Put
$$A_{N_0}(v) = \frac{1}{[N_0 : S_v]} \sum_{n \in N_0 / S_v} \pi(n) v.$$
The sum runs over a set of representatives of the left cosets $n S_v$. It does not depend on the choice, because $S_v$ fixes $v$. If $dn$ is the Haar measure on $N_0$ of total mass $1$, then $A_{N_0}(v) = \int_{N_0} \pi(n) v \, dn$, since $n \mapsto \pi(n) v$ is constant on each coset $n S_v$ and each coset has measure $[N_0 : S_v]^{-1}$. Three elementary facts about $A_{N_0}$ are used below.

(a) If $S \subseteq S_v$ is a subgroup of finite index in $N_0$, then $\sum_{n \in N_0 / S} \pi(n) v = [S_v : S] \sum_{n \in N_0 / S_v} \pi(n) v$. Indeed each coset of $S_v$ is the union of $[S_v : S]$ cosets of $S$, and $\pi(n) v$ is constant on it. So $A_{N_0}(v)$ is also the average over $N_0 / S$, and $A_{N_0}$ is linear: for $u, v \in V$ take $S = S_u \cap S_v$.

(b) If $n_1 \in N_0$, then $A_{N_0}(\pi(n_1) v) = A_{N_0}(v)$. Let $S$ be the normal core of $S_v$ in $N_0$, the intersection of the conjugates $m S_v m^{-1}$ for $m \in N_0$. It is a finite intersection, since $m S_v m^{-1}$ depends only on the coset $m S_v$, so $S$ is a normal subgroup of finite index that fixes $v$. As $n$ runs over representatives of $N_0 / S$, so does $n n_1$, because $n S n_1 = n n_1 S$. So $\sum_{n \in N_0 / S} \pi(n) \pi(n_1) v = \sum_{n \in N_0 / S} \pi(n) v$, and (a) gives the claim.

(c) The vector $v - A_{N_0}(v) = [N_0 : S_v]^{-1} \sum_{n \in N_0 / S_v} (v - \pi(n) v)$ lies in the span of the vectors $\pi(n) v - v$ with $n \in N_0$.

**Proposition 1.3.5 (Jacquet modules are exact).** Let $N$ be the unipotent radical of a parabolic subgroup of $G$, and let $(\pi, V)$ be a smooth representation of $G$.
1. A vector $v \in V$ lies in $V(N)$ if and only if $\int_{N_0} \pi(n) v \, dn = 0$ for some compact open subgroup $N_0$ of $N$. If this holds for $N_0$, it holds for each compact open subgroup $N_1 \supseteq N_0$ of $N$.
2. For each short exact sequence $0 \to V' \to V \to V'' \to 0$ of smooth representations of $G$, the sequence $0 \to V'_N \to V_N \to V''_N \to 0$ is exact. So the functor $V \mapsto V_N$ is exact, and so is $r_P$.

Lean: `Langlands.SmoothRep.mem_jacquetKer_iff`, `Langlands.SmoothRep.exists_forall_nAverage_eq_zero`, `Langlands.SmoothRep.jacquetMap_injective`, `Langlands.SmoothRep.jacquetMap_shortExact`, `Langlands.SmoothRep.jacquetMap_unipotent_shortExact`. Lean proves the proposition for a subgroup $N$ of any topological group $G$ such that each finite subset of $N$ lies in a compact open subgroup of $N$ (`Langlands.SmoothRep.HasCompactOpenExhaustion`), and for any subgroup $M$ in the normalizer of $N$. The average is `Langlands.SmoothRep.nAverage`, the finite sum above over $N_0 / (N_0 \cap \mathrm{Stab}(v))$ divided by the number of cosets, so Lean uses no Haar measure. The first two theorems are part 1, the third is the injectivity of $V'_N \to V_N$, and the fourth is part 2. `Langlands.GL2.hasCompactOpenExhaustion_unipotent` proves the hypothesis for the unipotent radical $N$ of $GL_2(K)$, and `Langlands.SmoothRep.mem_jacquetKer_unipotent_iff`, `Langlands.SmoothRep.jacquetMap_unipotent_injective` and the fifth theorem are the results for this $N$. The unipotent radicals of $GL_n$ for $n > 2$ are not defined in Lean.

*Proof.* The group $N$ is the union of an increasing sequence of compact open subgroups $N_0 \subset N_1 \subset \dots$, for example $N_k = d^k N_0 d^{-k}$ with $N_0 = N \cap GL_n(\mathcal{O}_K)$ and $d = \mathrm{diag}(\varpi^{-(n-1)}, \dots, \varpi^{-1}, 1)$. The group $N_k$ is the set of the matrices in $N$ whose entry $(i, j)$ lies in $\mathfrak{p}^{-k(j - i)}$. The set of the matrices in $N$ with all entries in $\mathfrak{p}^{-k}$ is not a group in general, for example for the Borel subgroup of $GL_3$. So each finite subset of $N$ lies in some $N_k$, and each compact open subgroup of $N$ lies in some $N_k$.

For part 1, suppose first that $A_{N_0}(v) = 0$. By (c), $v = v - A_{N_0}(v)$ lies in $V(N)$. Conversely, let $v \in V(N)$, say $v = \sum_{i=1}^r c_i (\pi(n_i) v_i - v_i)$ with $n_i \in N$. Choose a compact open subgroup $N_0$ of $N$ that contains $n_1, \dots, n_r$. By (a) and (b), $A_{N_0}(v) = \sum_i c_i (A_{N_0}(\pi(n_i) v_i) - A_{N_0}(v_i)) = 0$. For the second statement, let $N_1 \supseteq N_0$ be a compact open subgroup of $N$. Then $N_0$ has finite index in $N_1$, and $S = N_0 \cap S_v$ has finite index in $N_1$. Grouping the cosets of $S$ in $N_1$ by the cosets of $N_0$, we get
$$\sum_{n \in N_1 / S} \pi(n) v = \sum_{m \in N_1 / N_0} \pi(m) \sum_{n \in N_0 / S} \pi(n) v,$$
and the inner sum is a multiple of $A_{N_0}(v)$ by (a). So $A_{N_0}(v) = 0$ implies $A_{N_1}(v) = 0$.

For part 2, let $\iota : V' \to V$ and $p : V \to V''$ be the maps of the sequence. They are $G$-maps, so they map $V'(N)$ into $V(N)$ and $V(N)$ into $V''(N)$, and they induce maps of the Jacquet modules. The image $p(V(N))$ is spanned by the vectors $\pi''(n) p(v) - p(v)$. Since $p$ is onto, these are all the generators of $V''(N)$, so $p(V(N)) = V''(N)$. Thus $V_N \to V''_N$ is onto. Let $v \in V$ with $p(v) \in V''(N)$. Then $p(v) = p(y)$ for some $y \in V(N)$, so $v - y = \iota(u)$ with $u \in V'$, and the class of $v$ in $V_N$ is the image of the class of $u$. This is the exactness in the middle. For the injectivity, let $u \in V'$ with $\iota(u) \in V(N)$. By part 1, $A_{N_0}(\iota(u)) = 0$ for some $N_0$. Since $\iota$ is injective, $u$ and $\iota(u)$ have the same stabilizer, so $A_{N_0}(\iota(u)) = \iota(A_{N_0}(u))$. Hence $A_{N_0}(u) = 0$, and $u \in V'(N)$ by part 1 for $V'$. $\square$

The proof uses only two properties of $N$: each finite subset of $N$ lies in a compact open subgroup of $N$, and $M$ normalizes $N$. So part 2 holds for smooth representations of every group that contains such an $N$, for instance for the representations of $B$ in the last subsection of this section. The exactness is special to $p$-adic groups. It holds because $N$ is a union of compact subgroups, and it fails for real groups.

Part 1 is often called Jacquet's lemma, and the Lean project uses this name for it. In this book the name belongs to Theorem 1.3.6, which is the form used in the proof of the admissibility of Jacquet modules. Part 1 and the exactness are in Section 2 of the paper of Bernstein and Zelevinsky of 1976 on the representations of $GL(n, F)$. Theorem 1.3.6 is in Section 3.3 of Casselman's notes. [BH06] proves the exactness for $GL_2$ in Chapter 3.

### Jacquet's lemma

The following lemma connects the Jacquet module with the fixed vectors of small compact open subgroups. Let $P = MN$ be standard and let $J$ be a compact open subgroup with an *Iwahori decomposition*
$$J = (J \cap \bar N)(J \cap M)(J \cap N).$$
The groups $K_r$ with $r \ge 1$ have such a decomposition for each standard parabolic subgroup. Let $z$ be an element of the center of $M$ that contracts $N$, that is, $z^k n z^{-k} \to 1$ for $n \in N$ as $k \to \infty$. For the Borel subgroup of $GL_2$ we can take $z = \mathrm{diag}(\varpi, 1)$. Then $z$ also expands $\bar N$. We also ask that $z^{-1} (J \cap \bar N) z \subseteq J \cap \bar N$. This holds for the groups $K_r$.

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
The quotient comes from the closed orbit $B$, through evaluation at $1$, and the subspace from the open orbit $B w B$. We prove this case in full in the next subsection, as Theorem 1.3.11. Section 1.5 uses the sequence to find the reducible principal series of $GL_2$.

### The Bruhat decomposition of GL(2) and the principal series

In this subsection $G = GL_2(K)$, $B = TN$ is the upper triangular Borel subgroup, and
$$w = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}, \qquad n(x) = \begin{pmatrix} 1 & x \\ 0 & 1 \end{pmatrix}, \qquad \bar n(y) = \begin{pmatrix} 1 & 0 \\ y & 1 \end{pmatrix}.$$
The group $N$ is the group of the $n(x)$, and $x \mapsto n(x)$ is an isomorphism of topological groups $K \cong N$. We prove the geometric lemma for $GL_2$ in three steps: the decomposition of $G$ into two $B$-orbits, the resulting filtration of the principal series, and the computation of the Jacquet module of each piece. This is the argument of [BH06], Chapter 3. The same decomposition over a finite field organizes the representations of $GL_2(\mathbb{F}_q)$ in [BH06], Chapter 2, and the general case is in the paper of Bernstein and Zelevinsky of 1976.

**Proposition 1.3.9 (the Bruhat decomposition of $GL_2$).** Let $K$ be a field and let $g = \left(\begin{smallmatrix} \alpha & \beta \\ \gamma & \delta \end{smallmatrix}\right) \in GL_2(K)$.
1. The element $g$ lies in $BwN = \{ b w n : b \in B, n \in N \}$ if and only if $\gamma \ne 0$. So $G$ is the disjoint union $G = B \sqcup BwN$, and $BwN$ is the complement of $B$.
2. If $b w n = b' w n'$ with $b, b' \in B$ and $n, n' \in N$, then $b = b'$ and $n = n'$.
3. If $K$ is a nonarchimedean local field, then $B$ is closed in $G$, the big cell $BwN$ is open and dense, and the map $B \times K \to BwN$, $(b, x) \mapsto b w n(x)$, is a homeomorphism.

Lean: `Langlands.GL2.bruhat`, `Langlands.GL2.disjoint_borel_bigCell`, `Langlands.GL2.bigCell_eq_compl`, `Langlands.GL2.mem_bigCell_iff`, `Langlands.GL2.bigCell_unique`. Lean proves parts 1 and 2 for every field $K$. The big cell is `Langlands.GL2.bigCell`, with $w$ as `Langlands.GL2.weyl` and $n(x)$ as `Langlands.GL2.unip`. Part 3 is not stated in Lean.

*Proof.* Let $b = \left(\begin{smallmatrix} a & y \\ 0 & d \end{smallmatrix}\right) \in B$. Then
$$b w n(x) = \begin{pmatrix} y & a \\ d & 0 \end{pmatrix} \begin{pmatrix} 1 & x \\ 0 & 1 \end{pmatrix} = \begin{pmatrix} y & yx + a \\ d & dx \end{pmatrix}. \tag{2}$$
The lower left entry is $d \ne 0$. So $BwN$ lies in the set $\{\gamma \ne 0\}$, and it does not meet $B = \{\gamma = 0\}$. Conversely, let $\gamma \ne 0$ and put $x = \delta / \gamma$. Then
$$g \, n(-x) \, w = \begin{pmatrix} \alpha & \beta - \alpha \delta / \gamma \\ \gamma & 0 \end{pmatrix} w = \begin{pmatrix} \beta - \alpha \delta / \gamma & \alpha \\ 0 & \gamma \end{pmatrix}. \tag{3}$$
This matrix $b$ lies in $B$, and $g = b w^{-1} n(x) = b w n(x)$ since $w^2 = 1$. This proves part 1.

For part 2, put $m = n' n^{-1} = n(t)$. From $b w n = b' w n'$ we get $b'^{-1} b = w m w^{-1} = w m w$. The right side is $\bar n(t)$, which lies in $B$ only if $t = 0$. So $n = n'$, and then $b = b'$.

For part 3, the set $B = \{\gamma = 0\}$ is closed, so $BwN$ is open. Each $g \in B$ is the limit of $g \bar n(y) \in BwN$ as $y \to 0$, since the lower left entry of $g \bar n(y)$ is $\delta y \ne 0$ for $y \ne 0$. So $BwN$ is dense. The map $(b, x) \mapsto b w n(x)$ is continuous, and by part 1 and part 2 it is a bijection onto $BwN$. Its inverse is $g \mapsto (g n(-\delta/\gamma) w, \delta / \gamma)$ by (3), which is continuous on $\{\gamma \ne 0\}$. $\square$

For each $t \in T$ we have $w t w = t^w$, with $t^w$ the diagonal matrix with the entries of $t$ in the other order. So $BwB = BwTN = Bt^w wN = BwN$, and part 1 is the decomposition of $G$ into the two double cosets $B$ and $BwB$ of Theorem 1.3.8. The map $Bg \mapsto$ the line of the lower row of $g$ is a bijection $B \backslash G \cong \mathbb{P}^1(K)$, since $B$ is the stabilizer of the line $K(0, 1)$ in the action of $G$ on row vectors from the right. By (2) the lower row of $b w n(x)$ is $d (1, x)$. So $B$ is the point $(0 : 1)$, the big cell is the affine line $\{(1 : x)\}$, and part 2 says that $x$ is a coordinate on it.

A direct computation gives the identity
$$w n(x) = \begin{pmatrix} -x^{-1} & 1 \\ 0 & x \end{pmatrix} \bar n(x^{-1}), \qquad x \ne 0, \tag{4}$$
which one checks by multiplying out.

Now let $\chi_1, \chi_2$ be smooth characters of $K^\times$, let $\chi(b) = \chi_1(a) \chi_2(d)$ for $b = \left(\begin{smallmatrix} a & y \\ 0 & d \end{smallmatrix}\right)$, and let $V = \chi_1 \times \chi_2$, so that $f(bg) = \chi \delta_B^{1/2}(b) f(g)$ for $f \in V$.

**Proposition 1.3.10 (the big cell filtration of the principal series).** Let $V_w = \{ f \in V : f(1) = 0 \}$.
1. A function $f \in V$ lies in $V_w$ if and only if $f$ vanishes on $B$, that is, if and only if its support lies in the big cell $BwN$. The subspace $V_w$ is stable under $B$.
2. The sequence of representations of $B$
$$0 \to V_w \to V \xrightarrow{\ f \mapsto f(1)\ } \chi \delta_B^{1/2} \to 0$$
is exact.
3. For $f \in V_w$ put $\phi_f(x) = f(w n(x))$. The map $f \mapsto \phi_f$ is a linear isomorphism of $V_w$ onto the space $C_c^\infty(K)$ of the locally constant functions with compact support on $K$. Its inverse sends $\phi$ to the function $f$ with $f(b w n(x)) = \chi \delta_B^{1/2}(b) \phi(x)$ on $BwN$ and $f = 0$ on $B$. In this model, $n(y)$ acts by $\phi \mapsto \phi(\cdot + y)$, and $t = \mathrm{diag}(t_1, t_2)$ acts by
$$(t \cdot \phi)(x) = \chi_1(t_2) \chi_2(t_1) \left| \frac{t_2}{t_1} \right|^{1/2} \phi\left( \frac{t_2}{t_1} x \right). \tag{5}$$

Lean: `Langlands.principalSeriesBigCell`, `Langlands.mem_principalSeriesBigCell_iff`, `Langlands.principalSeriesBigCell_stable`, `Langlands.principalSeriesEvalOne`, `Langlands.principalSeriesJacquetEval_surjective`. Lean works with the unnormalized `Langlands.principalSeriesInd`, where $\chi$ replaces $\chi \delta_B^{1/2}$, and by `Langlands.normPrincipalSeries_eq` this is the same statement. Lean defines $V_w$ as the kernel of the evaluation `Langlands.principalSeriesEvalOne` and proves part 1. `Langlands.principalSeriesBigCell_shortExact` is part 2 as an exact sequence of vector spaces. It does not state part 2 as a sequence of representations of $B$. For part 3, the map $f \mapsto \phi_f$ is `Langlands.bigCellFun`. Lean proves that it is injective on $V_w$ (`Langlands.bigCellFun_inj`), that $\phi_f$ vanishes outside a ball for $f \in V_w$ (`Langlands.bigCellFun_eventually_zero`), and the formulas for the action of $n(y)$ and of $t$ (`Langlands.bigCellFun_ρ_unip`, `Langlands.bigCellFun_ρ_torus`). In the unnormalized form, (5) has no factor $|t_2 / t_1|^{1/2}$. Lean does not prove that the map is onto $C_c^\infty(K)$. It only constructs one $f_0 \in V_w$ such that $\phi_{f_0}$ is the indicator function of a ball (`Langlands.exists_bigCellFun_indicator`).

*Proof.* For $b \in B$ we have $f(b) = \chi \delta_B^{1/2}(b) f(1)$. So $f(1) = 0$ if and only if $f$ vanishes on $B$, which is the complement of $BwN$ by Proposition 1.3.9. The same formula gives $(b \cdot f)(1) = f(b) = \chi \delta_B^{1/2}(b) f(1)$. So $V_w$ is stable under $B$, and the evaluation at $1$ is a map of representations of $B$ onto the character $\chi \delta_B^{1/2}$. This proves part 1 and all of part 2 except the surjectivity. For it, choose a compact open subgroup $U$ of $G$ such that $\chi \delta_B^{1/2}$ is trivial on $B \cap U$. Define $f(bu) = \chi \delta_B^{1/2}(b)$ on $BU$ and $f = 0$ outside $BU$. It is well defined, since $bu = b'u'$ implies $b'^{-1} b = u' u^{-1} \in B \cap U$. The set $BU$ and its complement are unions of cosets $gU$, so $f$ is right invariant under $U$. So $f \in V$ and $f(1) = 1$.

For part 3, let $f \in V_w$ and let $J$ be a compact open subgroup with $f(gj) = f(g)$ for $j \in J$. The function $\phi_f$ is locally constant, since $x \mapsto w n(x)$ is continuous. For $|x|$ large, $\bar n(x^{-1}) \in J$, and (4) gives $\phi_f(x) = \chi \delta_B^{1/2}(b_x) f(\bar n(x^{-1})) = \chi \delta_B^{1/2}(b_x) f(1) = 0$, where $b_x$ is the upper triangular factor of (4). So $\phi_f$ has compact support. The map is injective: $f$ vanishes on $B$, and on $BwN$ it is given by $f(b w n(x)) = \chi \delta_B^{1/2}(b) \phi_f(x)$. For the surjectivity, let $\phi \in C_c^\infty(K)$, say with $\phi(x) = 0$ for $|x| > R$, and define $f$ by the formula of part 3. By part 2 of Proposition 1.3.9 it is well defined, and it satisfies $f(bg) = \chi \delta_B^{1/2}(b) f(g)$. By part 3 of Proposition 1.3.9 it is locally constant on $BwN$. It is also locally constant near each point $b_0 \in B$. Indeed, let $h = \left(\begin{smallmatrix} \alpha & \beta \\ \gamma & \delta \end{smallmatrix}\right)$ be close enough to $1$ that $|\delta| = 1$ and $|\gamma| < R^{-1}$. If $\gamma = 0$, then $f(h) = 0$. If $\gamma \neq 0$, then $h = b w n(\delta / \gamma)$ by (3), and $|\delta / \gamma| > R$, so $f(h) = 0$ again. So $f$ vanishes near $1$, and then near $b_0$, since $f(b_0 h) = \chi \delta_B^{1/2}(b_0) f(h)$. A locally constant function on the compact set $K_0$ is right invariant under one open subgroup $J$ of $K_0$: cover $K_0$ by finitely many sets $k_i J_i$ on which $f$ is constant, and take $J = \bigcap_i J_i$. With $G = B K_0$ and $f(bkj) = \chi \delta_B^{1/2}(b) f(kj)$, the function $f$ is right invariant under $J$. So $f \in V_w$, and $\phi_f = \phi$.

The actions follow from the definitions. First, $(n(y) \cdot f)(w n(x)) = f(w n(x) n(y)) = f(w n(x + y))$. Next, $n(x) t = t \, n(t_2 x / t_1)$ and $w t = t^w w$, so $w n(x) t = t^w w n(t_2 x / t_1)$, and $\chi \delta_B^{1/2}(t^w) = \chi_1(t_2) \chi_2(t_1) |t_2 / t_1|^{1/2}$. This gives (5). $\square$

**Theorem 1.3.11 (the Jacquet module of the principal series of $GL_2$).** The Jacquet module $r_B(\chi_1 \times \chi_2)$ has dimension $2$. The image of $V_w$ in it is the character $\chi^w = \chi_2 \otimes \chi_1$ of $T$, and the evaluation at $1$ induces an isomorphism of the quotient by this image onto $\chi = \chi_1 \otimes \chi_2$. So there is an exact sequence of representations of $T$
$$0 \to \chi_2 \otimes \chi_1 \to r_B(\chi_1 \times \chi_2) \to \chi_1 \otimes \chi_2 \to 0.$$

Lean: `Langlands.finrank_principalSeriesJacquet`, `Langlands.principalSeriesJacquet_shortExact`, `Langlands.bigCellJacquet_iso`, `Langlands.principalSeriesBigCell_shortExact`. These are in the file `Langlands/Smooth/JacquetPrincipal.lean`, for the space $V$ of `principalSeriesInd χ₁ χ₂` and the unnormalized Jacquet module. The first says that $V_N$ has dimension $2$. The second gives the exact sequence $0 \to (V_w)_N \to V_N \to \chi_1 \otimes \chi_2 \to 0$ of representations of $T$. The third says that $(V_w)_N$ is the character `Langlands.bigCellChar`, $\mathrm{diag}(a, d) \mapsto \chi_2(a) |a| \chi_1(d) |d|^{-1}$. The fourth is part 2 of Proposition 1.3.10 as a sequence of vector spaces. This is the theorem in another normalization. The space `principalSeriesInd χ₁ χ₂` is $\chi_1' \times \chi_2'$ with $\chi_1' = \chi_1 |\cdot|^{-1/2}$ and $\chi_2' = \chi_2 |\cdot|^{1/2}$. The theorem gives $\chi_2' \otimes \chi_1'$ on $(V_w)_N$ and $\chi_1' \otimes \chi_2'$ on the quotient for the action of $r_B$. The unnormalized action is this action multiplied by $\delta_B^{1/2} = |\cdot|^{1/2} \otimes |\cdot|^{-1/2}$, and this gives $\chi_2 |\cdot| \otimes \chi_1 |\cdot|^{-1}$ and $\chi_1 \otimes \chi_2$. Equivalently, for $V = \chi_1 \times \chi_2$ the unnormalized action of $T$ on $(V_w)_N$ is $\chi^w \delta_B^{1/2}$, as in the proof below. The Lean proof uses no Haar measure. In place of the integral $\lambda$, it shows with the coset sums of Proposition 1.3.5 that each class in $(V_w)_N$ is a multiple of the class of one vector $f_0$, with $\phi_{f_0}$ the indicator function of a ball. Part 1 of Proposition 1.3.5 then shows that $f_0 \notin V(N)$ and that $V_w \cap V(N) = V_w(N)$, which gives the injectivity of $(V_w)_N \to V_N$.

*Proof.* The Jacquet module of $V$ depends only on the restriction of $V$ to $B$. Apply the Jacquet functor of $N$ to the sequence of part 2 of Proposition 1.3.10. By Proposition 1.3.5 and the remark after it, the result is an exact sequence
$$0 \to (V_w)_N \to V_N \to (\chi \delta_B^{1/2})_N \to 0$$
of representations of $T$. The group $N$ acts trivially on the character $\chi \delta_B^{1/2}$, so its Jacquet module is the same character, and the normalization by $\delta_B^{-1/2}$ turns it into $\chi$.

By part 3 of Proposition 1.3.10, $(V_w)_N$ is the space of coinvariants of $C_c^\infty(K)$ under translations. Let $dx$ be a Haar measure on $K$ and $\lambda(\phi) = \int_K \phi(x) \, dx$. We claim that $\lambda$ induces an isomorphism $C_c^\infty(K)_K \cong \mathbb{C}$. The form $\lambda$ is invariant under translation and is not zero, so it factors through the coinvariants and is onto. Let $\phi$ have integral $0$. There is $m$ such that $\phi$ is constant on the cosets of $\mathfrak{p}^m$, and $\phi$ vanishes outside a finite union of these cosets. So $\phi = \sum_i c_i 1_{a_i + \mathfrak{p}^m}$ with finitely many $a_i$. Each difference $1_{a_i + \mathfrak{p}^m} - 1_{\mathfrak{p}^m}$ is a translate of $1_{\mathfrak{p}^m}$ minus $1_{\mathfrak{p}^m}$, so it lies in the span of the vectors $n(y) \phi' - \phi'$. Hence $\phi \equiv c \, 1_{\mathfrak{p}^m}$ modulo this span, with $c = \sum_i c_i$, and $0 = \lambda(\phi) = c \, \mathrm{vol}(\mathfrak{p}^m)$ gives $c = 0$. This proves the claim.

It remains to find the action of $T$ on the line $(V_w)_N$. By (5) and the change of variables $x \mapsto (t_1 / t_2) x$, which multiplies $dx$ by $|t_1 / t_2|$,
$$\lambda(t \cdot \phi) = \chi_1(t_2) \chi_2(t_1) \left| \frac{t_2}{t_1} \right|^{1/2} \left| \frac{t_1}{t_2} \right| \lambda(\phi) = \chi_2(t_1) \chi_1(t_2) \left| \frac{t_1}{t_2} \right|^{1/2} \lambda(\phi) = \chi^w \delta_B^{1/2}(t) \, \lambda(\phi).$$
After the normalization by $\delta_B^{-1/2}$, the torus acts on $(V_w)_N$ by $\chi^w$. $\square$

The closed orbit $B$ contributes $\chi$ through the evaluation at $1$, and the open orbit contributes $\chi^w$ through the integral over $N$. The factor $|t_1 / t_2|$ of the change of variables is exactly what turns $\delta_B^{1/2}(t^w) = \delta_B^{-1/2}(t)$ into $\delta_B^{1/2}(t)$. This matches the general statement of Theorem 1.3.8, with $(w\chi)_1 = \chi_2$ and $(w\chi)_2 = \chi_1$. If $\chi \ne \chi^w$, the sequence splits, since $T$ acts on the two lines by different characters (see the proof of Proposition 1.5.2).

**Example 1.3.12 (an explicit vector of the big cell).** Take $\phi = 1_{\mathcal{O}_K}$ in part 3 of Proposition 1.3.10, and let $f \in V_w$ be the corresponding function. For $g = \left(\begin{smallmatrix} \alpha & \beta \\ \gamma & \delta \end{smallmatrix}\right)$ with $\gamma \ne 0$, formula (3) gives $g = b w n(\delta / \gamma)$ with $b$ of diagonal $(a, d) = (-\det g / \gamma, \gamma)$. So
$$f(g) = \chi_1\left( -\frac{\det g}{\gamma} \right) \chi_2(\gamma) \left| \frac{\det g}{\gamma^2} \right|^{1/2} 1_{\mathcal{O}_K}\left( \frac{\delta}{\gamma} \right),$$
and $f(g) = 0$ if $\gamma = 0$. The function vanishes on the set $|\delta| > |\gamma|$, which contains a neighbourhood of $B$, as the proof predicts. With $dx$ normalized by $\mathrm{vol}(\mathcal{O}_K) = 1$, we have $\lambda(\phi) = 1$. So the image of $f$ spans the line $\chi^w$ in $r_B(\chi_1 \times \chi_2)$, while $f(1) = 0$. A vector $f'$ with $f'(1) = 1$, as in the proof of part 2 of Proposition 1.3.10, together with $f$ gives a basis of the Jacquet module.
