---
title: The Bruhat decomposition
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## The Bruhat decomposition

The Bruhat decomposition writes a split reductive group as a disjoint union of double cosets $BwB$, one for each element $w$ of the Weyl group. This section proves it for $GL_n$ by row and column reduction. It then defines Tits systems, proves the Bruhat decomposition for every Tits system, and states that a split reductive group has a Tits system. It ends with the cells of the flag variety and the order of $G(\mathbb{F}_q)$. The decomposition is used again and again in representation theory: the Iwahori decomposition of a $p$-adic group, the Mackey theory of parabolic induction and the Satake isomorphism all start from it. We follow [Spr98], Chapter 8.

### The Bruhat decomposition of $GL_n$

Let $B$ be the group of invertible upper triangular matrices in $GL_n(k)$. For $\sigma \in S_n$ we also write $\sigma$ for the permutation matrix with $\sigma e_j = e_{\sigma(j)}$. Its entry in row $\sigma(j)$ and column $j$ is 1, and its other entries are 0.

**Theorem 3.5.1 (Bruhat decomposition of $GL_n$).** The group $GL_n(k)$ is the disjoint union of the double cosets $B \sigma B$ for $\sigma \in S_n$.

Lean: not stated yet

*Proof.* Multiplication on the left by an element of $B$ is a sequence of row operations of two kinds: scale a row by a nonzero element, and add a multiple of row $j$ to row $i$ with $i < j$. Multiplication on the right by an element of $B$ is a sequence of column operations of two kinds: scale a column, and add a multiple of column $i$ to column $j$ with $i < j$. Each operation of these kinds is multiplication by an element of $B$.

Existence. Let $g \in GL_n(k)$. Let $i_1$ be the largest index with $g_{i_1 1} \ne 0$. Add multiples of row $i_1$ to the rows above it so that column 1 has a single nonzero entry, in row $i_1$. Then add multiples of column 1 to the later columns so that row $i_1$ has a single nonzero entry, in column 1. Now look at column 2. Its entry in row $i_1$ is 0. Let $i_2$ be the largest index with a nonzero entry in column 2. Clear column 2 above row $i_2$ by adding multiples of row $i_2$ to the rows above it. Row $i_2$ is 0 in column 1, so column 1 does not change. Then clear row $i_2$ to the right of column 2 with column operations. Continue with columns $3, \dots, n$. The result is a monomial matrix, with a nonzero entry in row $i_j$ and column $j$ for each $j$. Scale the rows to make these entries 1. The result is the permutation matrix $\sigma$ with $\sigma(j) = i_j$, so $g \in B \sigma B$.

Uniqueness. For $g \in GL_n(k)$ and $1 \le i, j \le n$, let $r_{ij}(g)$ be the rank of the submatrix of $g$ with rows $i, \dots, n$ and columns $1, \dots, j$. Let $b \in B$. Rows $i, \dots, n$ of $bg$ are the product of the lower right block of $b$ of size $n - i + 1$ with rows $i, \dots, n$ of $g$, and this block is invertible. So $r_{ij}(bg) = r_{ij}(g)$. In the same way, columns $1, \dots, j$ of $gb$ are columns $1, \dots, j$ of $g$ times the upper left block of $b$ of size $j$, so $r_{ij}(gb) = r_{ij}(g)$. Thus the numbers $r_{ij}$ are constant on double cosets. For a permutation matrix,
$$r_{ij}(\sigma) = |\{m \le j : \sigma(m) \ge i\}|.$$
So $r_{ij}(\sigma) - r_{i, j-1}(\sigma)$ is 1 if $\sigma(j) \ge i$ and 0 otherwise, with $r_{i0} = 0$. These numbers determine $\sigma(j)$ for each $j$. So $B \sigma B = B \tau B$ implies $\sigma = \tau$. $\square$


**Example 3.5.2 (the Bruhat decomposition of $SL_2$).** Let $G = SL_2$, $B$ the upper triangular subgroup of $SL_2(k)$ and $w = \left(\begin{smallmatrix} 0 & 1 \\ -1 & 0 \end{smallmatrix}\right)$. Let $g = \left(\begin{smallmatrix} a & b \\ c & d \end{smallmatrix}\right) \in SL_2(k)$. If $c = 0$, then $g \in B$. If $c \ne 0$, then
$$\begin{pmatrix} a & b \\ c & d \end{pmatrix} = \begin{pmatrix} 1 & a/c \\ 0 & 1 \end{pmatrix} \begin{pmatrix} 0 & 1 \\ -1 & 0 \end{pmatrix} \begin{pmatrix} -c & -d \\ 0 & -1/c \end{pmatrix},$$
as one checks with $ad - bc = 1$. So $SL_2(k) = B \sqcup BwB$. The group $SL_2(k)$ acts on $\mathbb{P}^1(k)$ by fractional linear maps, $B$ is the stabilizer of $\infty$, and $SL_2(k)/B = \mathbb{P}^1(k)$. The decomposition says that $\mathbb{P}^1(k)$ is the union of the fixed point $\infty$ of $B$ and the orbit $B \cdot 0 = k$ of $B$.

### Tits systems

**Definition 3.5.3 (Tits system).** A *Tits system*, or *BN pair*, is a quadruple $(G, B, N, S)$ where $G$ is a group, $B$ and $N$ are subgroups of $G$ and $S$ is a subset of $N/(B \cap N)$, with the following properties.
1. The subgroups $B$ and $N$ generate $G$, and $T = B \cap N$ is a normal subgroup of $N$.
2. The set $S$ generates the group $W = N/T$, and each element of $S$ has order 2.
3. (T1) For $s \in S$ and $w \in W$, $sBw \subset BwB \cup BswB$.
4. (T2) For $s \in S$, $sBs \ne B$.

The group $W$ is the *Weyl group* of the Tits system.

Since $T \subset B$, the sets $wB$, $Bw$ and $BwB$ are well defined for $w \in W$. The length $\ell(w)$ is the smallest number of elements of $S$ whose product is $w$.

**Theorem 3.5.4 (split reductive groups have a Tits system).** Let $(G, T)$ be a split reductive group over $k$, $B \supset T$ a Borel subgroup with base $\Delta$, and $N = N_G(T)(k)$. Then $B(k) \cap N = T(k)$, the group $N / T(k)$ is $W$, and $(G(k), B(k), N, \{s_\alpha : \alpha \in \Delta\})$ is a Tits system.

Lean: not stated yet

The proof over $\bar k$ is in [Spr98], Chapter 8, and the case of a split group over an arbitrary field is in [Spr98], Chapter 16. The main step is (T1) for $s = s_\alpha$ with $\alpha \in \Delta$. It reduces to the computation of Example 3.5.2 inside the image of $\varphi_\alpha$, because $s_\alpha$ permutes $R^+ \setminus \{\alpha\}$ (Chapter 2), so that $n_\alpha$ normalizes the product of the $U_\beta$ with $\beta \in R^+ \setminus \{\alpha\}$. Bourbaki, *Lie Groups and Lie Algebras*, Chapter IV, Section 2, develops the theory of Tits systems as abstract groups.

**Theorem 3.5.5 (Bruhat decomposition for a Tits system).** Let $(G, B, N, S)$ be a Tits system with Weyl group $W$. Then $G$ is the disjoint union of the double cosets $BwB$ for $w \in W$.

Lean: not stated yet

*Proof.* Let $\Omega = \bigcup_{w \in W} BwB$. By (T1), for $s \in S$ and $w \in W$,
$$s \cdot BwB \subset (BwB \cup BswB) B = BwB \cup BswB \subset \Omega.$$
So $\Omega$ is stable under left multiplication by $B$, by $T$ and by the elements of $S$. Since $S$ generates $W$ and $s^{-1} \in sT$, the set $\Omega$ is stable under left multiplication by $N$. Since $B$ and $N$ generate $G$, we get $G \Omega \subset \Omega$, and $\Omega = G$ because $1 \in \Omega$.

For disjointness we prove the following claim by induction on $n$: if $BwB = Bw'B$ and $\min(\ell(w), \ell(w')) \le n$, then $w = w'$. Let $\ell(w) \le \ell(w')$. If $\ell(w) = 0$, then $w = 1$ and $w' \in B \cap N = T$, so $w' = 1$ in $W$. Assume the claim for $n - 1$, and let $\ell(w) = n \ge 1$. Write $w = s v$ with $s \in S$ and $\ell(v) = n - 1$. Since $s^2 \in T$, the element $sw$ lies in $BvB$. By (T1),
$$sw \in s \cdot BwB = s \cdot Bw'B \subset Bw'B \cup Bsw'B.$$
So $BvB = Bw'B$ or $BvB = Bsw'B$. In the first case the induction hypothesis gives $v = w'$, which is false because $\ell(v) < \ell(w')$. In the second case the induction hypothesis gives $v = sw'$, so $w = sv = w'$. $\square$

The proof uses only (T1). Axiom (T2) is used for the finer statements, for example that the set $S$ is determined by $B$ and $N$.

**Corollary 3.5.6 (standard parabolic subgroups).** Let $(G, B, N, S)$ be a Tits system. For $I \subset S$, let $W_I$ be the subgroup of $W$ generated by $I$. Then $P_I = B W_I B$ is a subgroup of $G$.

Lean: not stated yet

*Proof.* The set $P_I$ contains 1 and is stable under left multiplication by $B$. For $s \in I$ and $w \in W_I$, (T1) gives $s BwB \subset BwB \cup BswB \subset P_I$. As in the proof of Theorem 3.5.5, $P_I$ is stable under left multiplication by the subgroup generated by $B$ and $I$, and this subgroup contains $P_I$. So $P_I P_I \subset P_I$. Also $(BwB)^{-1} = Bw^{-1}B$ and $W_I$ is a group, so $P_I$ is stable under inverses. $\square$

Bourbaki, *Lie Groups and Lie Algebras*, Chapter IV, Section 2, proves with (T2) that every subgroup of $G$ that contains $B$ is $P_I$ for exactly one $I \subset S$. For a split reductive group the $P_I$ are the groups of $k$-points of the parabolic subgroups of $G$ that contain $B$. These *standard parabolic subgroups* are the groups from which parabolic induction starts in Volume 6.

**Example 3.5.7 (standard parabolics of $GL_n$).** Let $G = GL_n$ with $S = \{s_1, \dots, s_{n-1}\}$, where $s_i$ is the transposition $(i \;\, i+1)$. A subset $I \subset S$ is given by the indices $i$ with $s_i \notin I$. These indices cut $\{1, \dots, n\}$ into consecutive blocks of sizes $n_1, \dots, n_m$ with $n_1 + \dots + n_m = n$. Then $W_I = S_{n_1} \times \dots \times S_{n_m}$, the permutations that preserve each block, and $P_I$ is the group of invertible block upper triangular matrices with diagonal blocks of sizes $n_1, \dots, n_m$. It is the stabilizer of the partial flag
$$\langle e_1, \dots, e_{n_1} \rangle \subset \langle e_1, \dots, e_{n_1 + n_2} \rangle \subset \dots \subset k^n.$$
It is the semidirect product of the block diagonal group $GL_{n_1} \times \dots \times GL_{n_m}$, its *Levi factor*, and its unipotent radical, the matrices with identity diagonal blocks and zeros below them. For $I = \emptyset$ we get $B$, and for $I = S$ we get $GL_n$.

### Cells and point counts

Let $(G, T)$ be split, $B = TU$ a Borel subgroup containing $T$ with positive system $R^+$, and for $w \in W$ let $n_w \in N_G(T)(k)$ be a representative. Let $U_w$ be the product of the $U_\alpha$ with $\alpha \in R^+$ and $w^{-1} \alpha \in -R^+$, in some order. It has dimension $\ell(w^{-1}) = \ell(w)$.

**Proposition 3.5.8 (Bruhat cells).** The map $(u, b) \mapsto u n_w b$ is an isomorphism of varieties $U_w \times B \to B n_w B$. So $B n_w B / B \cong U_w \cong \mathbb{A}^{\ell(w)}$, and the flag variety $G/B$ is the disjoint union of the locally closed cells $B n_w B / B$.

Lean: not stated yet

*Proof sketch.* Let $U'_w$ be the product of the $U_\alpha$ with $\alpha \in R^+$ and $w^{-1} \alpha \in R^+$. By Theorem 3.4.3 and the commutator formula (Proposition 3.2.7), $U = U_w U'_w$, and $n_w^{-1} U'_w n_w \subset U$. So $B n_w B = U n_w B = U_w n_w B$. If $u n_w B = u' n_w B$ with $u, u' \in U_w$, then $n_w^{-1} u'^{-1} u n_w \in B$. This element lies in the product of the $U_{w^{-1}\alpha}$ with $w^{-1}\alpha \in -R^+$, which meets $B$ only in 1. So $u = u'$. That the map is an isomorphism of varieties, and not only a bijection on points, is proved in [Spr98], Chapter 8. $\square$


**Example 3.5.9 (the order of $G(\mathbb{F}_q)$).** Let $G$ be split of rank $r$ over $\mathbb{F}_q$, with $N = |R^+|$. Then $T(\mathbb{F}_q) \cong (\mathbb{F}_q^\times)^r$ has $(q-1)^r$ elements, and $U(\mathbb{F}_q)$ has $q^N$ elements by Theorem 3.4.3. By Proposition 3.5.8 the cell $B n_w B / B$ has $q^{\ell(w)}$ points over $\mathbb{F}_q$, so
$$|G(\mathbb{F}_q)| = q^N (q-1)^r \sum_{w \in W} q^{\ell(w)}.$$
For $GL_n$ we have $r = n$, $N = n(n-1)/2$ and $\ell(\sigma) = \mathrm{inv}(\sigma)$, the number of inversions. We claim that
$$\sum_{\sigma \in S_n} q^{\mathrm{inv}(\sigma)} = \prod_{m=1}^{n} \frac{q^m - 1}{q - 1}.$$
Write $\sigma \in S_n$ as the word $\sigma(1) \sigma(2) \cdots \sigma(n)$. Delete the letter $n$. The result is a word for a permutation $\tau \in S_{n-1}$. If $n$ was in position $p$, it formed an inversion with each of the $n - p$ letters after it, so $\mathrm{inv}(\sigma) = \mathrm{inv}(\tau) + n - p$. Each pair $(\tau, p)$ occurs once, so the sum for $S_n$ is the sum for $S_{n-1}$ times $1 + q + \dots + q^{n-1}$. The claim follows by induction. So
$$|GL_n(\mathbb{F}_q)| = q^{n(n-1)/2} \prod_{m=1}^{n} (q^m - 1),$$
which agrees with the direct count $\prod_{m=0}^{n-1} (q^n - q^m)$ of the ordered bases of $\mathbb{F}_q^n$. The number of points of $GL_n/B$ is the number of complete flags in $\mathbb{F}_q^n$.
