---
title: The group GL(n) over the adeles
nodes: []
sources: [Neu99]
status: drafted
drafted_by: writer
reviewed_by: []
---
## The group GL(n) over the adeles

This section defines the group $GL_n(\mathbb{A})$ and its topology, the compact open subgroups that play the role of the level, and the two decompositions that we use all the time: the Iwasawa decomposition and the finiteness of the double cosets. For $n = 1$ everything here is in Volume 1, Chapter 3, and the example to keep in mind is $GL_2(\mathbb{A}_\mathbb{Q})$ with the subgroup $GL_2(\widehat{\mathbb{Z}})$.

### The adelic group

Recall from Volume 1, Definition 3.2.1, that $\mathbb{A}$ is the restricted product of the completions $F_v$ with respect to the subrings $\mathcal{O}_v$, and from Definition 3.4.1 that the group of ideles $J_F = \mathbb{A}^\times$ is the restricted product of the groups $F_v^\times$ with respect to the subgroups $\mathcal{O}_v^\times$, with the restricted product topology. This topology is not the topology of a subspace of $\mathbb{A}$. It is the topology for which $x \mapsto (x, x^{-1})$ is a homeomorphism onto a closed subset of $\mathbb{A} \times \mathbb{A}$. The same construction works for $GL_n$.

**Definition 1.1.1 (the adelic group).** The group $GL_n(\mathbb{A})$ is the group of the invertible $n \times n$ matrices with entries in $\mathbb{A}$, with the topology for which $g \mapsto (g, g^{-1})$ is a homeomorphism onto a closed subset of $M_n(\mathbb{A}) \times M_n(\mathbb{A})$. Equivalently, it is the restricted product of the groups $GL_n(F_v)$ with respect to the compact open subgroups $K_v = GL_n(\mathcal{O}_v)$ at the finite places. We write $GL_n(\mathbb{A}) = GL_n(F_\infty) \times GL_n(\mathbb{A}_f)$, where $F_\infty = \prod_{v \mid \infty} F_v$ and $\mathbb{A}_f$ is the ring of finite adeles.

Lean: `Langlands.AdelicGL`, a definition of the project

In the Lean project, `Langlands.AdelicGL K n` is the group of units of the matrix ring $M_n(\mathbb{A}_K)$, with the topology of the units of a topological ring. That is the topology of the definition. The subgroup $GL_n(F)$ is embedded diagonally by `Langlands.principalGL`, and `Langlands.localGL v` embeds $GL_n(F_v)$ at a finite place $v$ with the identity at the other places. The two descriptions of the definition agree because a matrix $g \in GL_n(\mathbb{A})$ lies in $GL_n(\mathcal{O}_v)$ at almost all $v$: the entries of $g$ and of $g^{-1}$ are in $\mathcal{O}_v$ for almost all $v$, by the definition of $\mathbb{A}$.

The group $GL_n(F_v)$ has a maximal compact subgroup $K_v$: $GL_n(\mathcal{O}_v)$ at a finite place, $O(n)$ at a real place and $U(n)$ at a complex place. We write $K = \prod_v K_v$ and $K_\infty = \prod_{v \mid \infty} K_v$. For a nonzero ideal $\mathfrak{n}$ of $\mathcal{O}$, the *principal congruence subgroup* $K(\mathfrak{n}) = \prod_{v < \infty} K_v(\mathfrak{n})$ is the product of the groups
$$K_v(\mathfrak{n}) = \{ k \in GL_n(\mathcal{O}_v) : k \equiv 1 \bmod \mathfrak{n} \mathcal{O}_v \}.$$
It is a compact open subgroup of $GL_n(\mathbb{A}_f)$, and $K_v(\mathfrak{n}) = K_v$ for $v \nmid \mathfrak{n}$. Each compact open subgroup of $GL_n(\mathbb{A}_f)$ contains some $K(\mathfrak{n})$, because the groups $K_v(\varpi_v^m)$ form a basis of neighbourhoods of $1$ in $GL_n(F_v)$ and a compact open subgroup contains $K_v$ for almost all $v$. In the Lean project, `Langlands.IsInLevel N k` says that $k$ is the identity at the infinite places and that the entries of $k_v - 1$ and of $k_v^{-1} - 1$ lie in $N \mathcal{O}_v$ at each finite place. So the level of a cusp form in Lean is a group $K(N \mathcal{O})$ for an element $N \in \mathcal{O}$, and no condition is put at the infinite places.

### Discreteness and the Iwasawa decomposition

**Proposition 1.1.2 (discreteness).** The subgroup $GL_n(F)$ is discrete and closed in $GL_n(\mathbb{A})$. The center $Z(\mathbb{A}) = \mathbb{A}^\times$ meets $GL_n(F)$ in $F^\times$.

Lean: not stated yet

*Proof.* By Volume 1, Theorem 3.2.4, $F$ is discrete in $\mathbb{A}$, so $M_n(F)$ is discrete in $M_n(\mathbb{A})$ and the set of pairs $(\gamma, \gamma^{-1})$ is discrete in $M_n(\mathbb{A})^2$. A discrete subgroup of a Hausdorff topological group is closed. The second claim is clear. $\square$

**Proposition 1.1.3 (Iwasawa decomposition).** For each place $v$, $GL_n(F_v) = B(F_v) K_v$. Hence $GL_n(\mathbb{A}) = B(\mathbb{A}) K$.

Lean: not stated yet

*Proof.* At a real or complex place, the Gram-Schmidt process applied to the columns of $g^{-1}$, from the last to the first, writes $g = bk$ with $b$ upper triangular and $k$ orthogonal or unitary. At a finite place, right multiplication by $K_v$ allows the column operations with coefficients in $\mathcal{O}_v$. Move an entry of minimal valuation of the last row to the position $(n, n)$, clear the rest of the last row, and repeat with the upper left block. For the adelic claim, take $b_v = 1$ at the places where $g_v \in K_v$. $\square$

Write $g = n a k$ with $n \in N(\mathbb{A})$, $a = \mathrm{diag}(a_1, \ldots, a_n) \in T(\mathbb{A})$ and $k \in K$. The numbers $|a_i|_\mathbb{A}$ do not depend on the decomposition, because $B(\mathbb{A}) \cap K$ has diagonal entries of absolute value 1. The modulus character of $B$ is $\delta_B(na) = \prod_{i < j} |a_i / a_j|$. It is the factor that appears when one integrates over $G = BK$, in the formula $\int_G f(g) \, dg = \int_B \int_K f(bk) \, dk \, d_l b$ with a left Haar measure $d_l b$ on $B$.

### Double cosets and the class number

**Theorem 1.1.4 (strong approximation for $SL_n$).** Let $S$ be a nonempty set of places of $F$. Then $SL_n(F)$ is dense in the restricted product of the groups $SL_n(F_v)$ for $v \notin S$.

Lean: not stated yet

*Proof.* Let $U_{ij}$ be the root subgroup of the matrices $1 + x E_{ij}$, $i \ne j$, isomorphic to the additive group. By strong approximation for $\mathbb{A}$, Volume 1, Theorem 3.5.5, $U_{ij}(F)$ is dense in $U_{ij}(\mathbb{A}^S)$, where $\mathbb{A}^S$ is the restricted product over $v \notin S$. So the closure $H$ of $SL_n(F)$ in $SL_n(\mathbb{A}^S)$ contains every $U_{ij}(\mathbb{A}^S)$. A basic open set of $SL_n(\mathbb{A}^S)$ is $gW$ with $W = \prod_{v \in T} W_v \times \prod_{v \notin S \cup T} SL_n(\mathcal{O}_v)$ for a finite set $T$. Each $SL_n(F_v)$ is generated by elementary matrices, and after inserting identity factors we may write all $g_v$, $v \in T$, with the same sequence of positions. The corresponding product of elements of the $U_{ij}(\mathbb{A}^S)$, supported at $T$, lies in $H \cap gW$. So $H$ is dense and closed, hence everything. $\square$

**Theorem 1.1.5 (finiteness of the double cosets).** Let $U \subseteq GL_n(\mathbb{A}_f)$ be a compact open subgroup. Then $GL_n(F) \backslash GL_n(\mathbb{A}_f) / U$ is finite. If $\det(U) = \widehat{\mathcal{O}}^\times$, the map $\det$ induces a bijection
$$GL_n(F) \backslash GL_n(\mathbb{A}) / GL_n(F_\infty)^+ U \;\cong\; F_+^\times \backslash \mathbb{A}_f^\times / \widehat{\mathcal{O}}^\times,$$
where $GL_n(F_\infty)^+$ is the identity component and $F_+^\times$ is the group of totally positive elements. The right side is the narrow class group of $F$.

Lean: not stated yet

*Proof.* The map $\det$ is surjective and constant on the double cosets, because $\det(GL_n(F_\infty)^+ U)$ is the product of the positive reals at the real places, of $\mathbb{C}^\times$ at the complex places and of $\det U$. For injectivity let $g, g'$ have the same image. After a change of $g'$ by $\mathrm{diag}(f, 1, \ldots, 1)$ with $f \in F_+^\times$ on the left and by an element of $GL_n(F_\infty)^+ U$ on the right, $\det g' = \det g$, so $g' g^{-1} \in SL_n(\mathbb{A})$. By Theorem 1.1.4 with $S$ the infinite places, $SL_n(\mathbb{A}) = SL_n(F) \, SL_n(F_\infty) V$ for the open subgroup $V = g_f U g_f^{-1} \cap SL_n(\mathbb{A}_f)$. Write $g' g^{-1} = \gamma s_\infty g_f u g_f^{-1}$ accordingly. Then $g' = \gamma g (g_\infty^{-1} s_\infty g_\infty) u$, which lies in the double coset of $g$. The finiteness of the narrow class group, Volume 1, Corollary 3.5.3, gives the first claim. $\square$

**Example 1.1.6 (the classical dictionary).** Let $F = \mathbb{Q}$. Then the narrow class group is trivial, and Theorem 1.1.5 gives $GL_n(\mathbb{A}_\mathbb{Q}) = GL_n(\mathbb{Q}) \, GL_n(\mathbb{R})^+ \, U$ for each compact open $U$ with $\det U = \widehat{\mathbb{Z}}^\times$, for example $U = GL_n(\widehat{\mathbb{Z}})$ or the group $K_0(N)$ of matrices whose last row is congruent to $(0, \ldots, 0, *)$ modulo $N$. Let $\Gamma = GL_n(\mathbb{Q}) \cap GL_n(\mathbb{R})^+ U$, viewed as a subgroup of $GL_n(\mathbb{R})^+$. The map $g_\infty \mapsto GL_n(\mathbb{Q}) g_\infty U$ induces a homeomorphism
$$\Gamma \backslash GL_n(\mathbb{R})^+ \;\cong\; GL_n(\mathbb{Q}) \backslash GL_n(\mathbb{A}_\mathbb{Q}) / U.$$
For $U = GL_n(\widehat{\mathbb{Z}})$ one gets $\Gamma = SL_n(\mathbb{Z})$, and for $n = 2$ and $U = K_0(N)$ one gets $\Gamma = \Gamma_0(N)$ with the matrices of positive determinant. So a function on $GL_n(\mathbb{Q}) \backslash GL_n(\mathbb{A}_\mathbb{Q})$ that is invariant under $U$ is the same as a function on $\Gamma \backslash GL_n(\mathbb{R})^+$. The function $\varphi_\Delta$ of the introduction is the case $n = 2$ and $U = GL_2(\widehat{\mathbb{Z}})$.

### Finite volume

Let $GL_n(\mathbb{A})^1$ be the subgroup of the $g$ with $|\det g|_\mathbb{A} = 1$. It contains $GL_n(F)$, by the product formula of Volume 1, Theorem 3.3.4. For $t > 0$ let $a_t \in Z(F_\infty)$ be the scalar matrix with the entry $t^{1/(n[F:\mathbb{Q}])}$ at each infinite place. Then $GL_n(\mathbb{A}) = GL_n(\mathbb{A})^1 \times \{a_t\}$, and $\{a_t\} \cong \mathbb{R}_{>0}$.

**Theorem 1.1.7 (reduction theory).** For $c > 0$ let $A_c$ be the set of the diagonal matrices $a = \mathrm{diag}(t_1, \ldots, t_n)$ in $T(F_\infty)$ with the same real entries $t_i > 0$ at each infinite place, such that $|\det a|_\mathbb{A} = 1$ and $t_i / t_{i+1} \ge c$ for $1 \le i < n$. Let $\Omega$ be a compact subset of $B(\mathbb{A}) \cap GL_n(\mathbb{A})^1$. For $c$ small and $\Omega$ large, the Siegel set $\mathfrak{S} = \Omega A_c K$ satisfies $GL_n(\mathbb{A})^1 = GL_n(F) \, \mathfrak{S}$. The quotient $GL_n(F) \backslash GL_n(\mathbb{A})^1$ has finite volume, and $Z(\mathbb{A}) GL_n(F) \backslash GL_n(\mathbb{A})$ has finite volume.

Lean: not stated yet

*Proof sketch.* We follow Getz and Hahn. For $g \in GL_n(\mathbb{A})^1$ the lattice $\mathcal{O}^n g$ has a nonzero vector $\xi g$ of minimal height, by the adelic Minkowski theorem of Volume 1, Theorem 3.5.1. Move $\xi$ to $e_n$ by an element of $GL_n(F)$ and induct on $n$ with the quotient lattice. This gives $\gamma g = nak$ with $|a_i / a_{i+1}|$ bounded below. The compactness of $N(F) \backslash N(\mathbb{A})$ and of the norm one ideles modulo $F^\times$ then puts $\gamma g$ into $\Omega A_c K$. For the volume, the Haar measure on $\mathfrak{S}$ is $\delta_B(a)^{-1} d\omega \, da \, dk$, and $\delta_B^{-1}$ is a product of negative powers of the $t_i / t_{i+1} \ge c$, which are integrable. $\square$

For $F = \mathbb{Q}$ and $n = 2$ the Siegel set is essentially the region $\{x + iy : |x| \le 1/2, \, y \ge \sqrt{3}/2\}$, and the theorem says that $SL_2(\mathbb{Z}) \backslash \mathfrak{H}$ has finite area, as in Volume 4. The quotient is not compact for $n \ge 2$, because $A_c$ is not bounded. This is the reason for the growth conditions and the constant terms of the next section.
