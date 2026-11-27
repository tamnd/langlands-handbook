---
title: The group GL(2) over the adeles
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## The group GL(2) over the adeles

This section defines the locally compact group $GL_2(\mathbb{A})$ and the compact open subgroups of its finite part that replace the congruence subgroups of Volume 4. It also fixes the notation for the standard subgroups and proves the Iwasawa decomposition at each place. We write $\mathbb{A} = \mathbb{R} \times \mathbb{A}_f$ for the adeles of $\mathbb{Q}$, where $\mathbb{A}_f = \prod'_p (\mathbb{Q}_p, \mathbb{Z}_p)$ is the ring of finite adeles, and $\hat{\mathbb{Z}} = \prod_p \mathbb{Z}_p$. The letter $v$ denotes a place of $\mathbb{Q}$, that is, a prime $p$ or $\infty$, and $\mathbb{Q}_\infty = \mathbb{R}$.

### The adelic points

**Definition 1.1.1 (the adelic group).** For each prime $p$ let $K_p = GL_2(\mathbb{Z}_p)$. It is a compact open subgroup of $GL_2(\mathbb{Q}_p)$. The group $GL_2(\mathbb{A}_f)$ is the restricted product of the groups $GL_2(\mathbb{Q}_p)$ with respect to the subgroups $K_p$: its elements are the families $(g_p)_p$ with $g_p \in GL_2(\mathbb{Q}_p)$ for all $p$ and $g_p \in K_p$ for all but finitely many $p$. Its topology is the one for which the subgroup $\prod_p K_p = GL_2(\hat{\mathbb{Z}})$, with the product topology, is open. We put $GL_2(\mathbb{A}) = GL_2(\mathbb{R}) \times GL_2(\mathbb{A}_f)$, with the product topology. For a place $v$ let $\iota_v : GL_2(\mathbb{Q}_v) \to GL_2(\mathbb{A})$ be the embedding with $v$-component $h$ and all other components 1. The group $GL_2(\mathbb{Q})$ embeds diagonally in $GL_2(\mathbb{A})$.

An element $g \in GL_2(\mathbb{A})$ is the same as a matrix with entries in $\mathbb{A}$ whose determinant is an idele. Indeed, if $g_p \in K_p$ for almost all $p$, then the entries of $g$ are adeles and $\det g \in \mathbb{Z}_p^\times$ for almost all $p$. Conversely, if the entries are adeles and $\det g$ is an idele, then for almost all $p$ the entries of $g_p$ are in $\mathbb{Z}_p$ and $\det g_p \in \mathbb{Z}_p^\times$, so $g_p \in K_p$. The topology is not the subspace topology from $M_2(\mathbb{A}) = \mathbb{A}^4$, for the same reason as for the ideles in Volume 1, Section 3.4. It is the topology induced by the map $g \mapsto (g, g^{-1})$ from $GL_2(\mathbb{A})$ to $M_2(\mathbb{A})^2$. In particular the inclusion $GL_2(\mathbb{A}) \to M_2(\mathbb{A})$ is continuous. The group $GL_2(\mathbb{A})$ is locally compact, because $GL_2(\mathbb{R}) \times GL_2(\hat{\mathbb{Z}})$ is an open subgroup that is locally compact.

**Lemma 1.1.2 (the rational points are discrete).** The subgroup $GL_2(\mathbb{Q})$ of $GL_2(\mathbb{A})$ is discrete. One has $GL_2(\mathbb{Q}) \cap (GL_2(\mathbb{R}) \times GL_2(\hat{\mathbb{Z}})) = GL_2(\mathbb{Z})$.

Lean: not formalized

*Proof.* By Volume 1, Theorem 3.2.4, $\mathbb{Q}$ is discrete in $\mathbb{A}$, so $M_2(\mathbb{Q})$ is discrete in $M_2(\mathbb{A})$. Let $\gamma \in GL_2(\mathbb{Q})$. There is an open set $U \subset M_2(\mathbb{A})$ with $U \cap M_2(\mathbb{Q}) = \{\gamma\}$. Its preimage in $GL_2(\mathbb{A})$ is open, because the inclusion is continuous, and it meets $GL_2(\mathbb{Q})$ only in $\gamma$. For the second claim, let $\gamma \in GL_2(\mathbb{Q})$ with $\gamma \in GL_2(\mathbb{Z}_p)$ for each $p$. The entries of $\gamma$ are rational numbers in $\mathbb{Z}_p$ for each $p$, so they are integers. The determinant is a rational number in $\mathbb{Z}_p^\times$ for each $p$, so it is $\pm 1$. Thus $\gamma \in GL_2(\mathbb{Z})$. The converse is clear. $\square$

The center of $GL_2(\mathbb{A})$ is the group $Z(\mathbb{A})$ of the scalar matrices $z I$ with $z \in \mathbb{A}^\times$. We identify it with $\mathbb{A}^\times$. By Volume 1, Example 3.4.8, each idele is in a unique way a product
$$z = q \, r \, u, \qquad q \in \mathbb{Q}^\times, \ r \in \mathbb{R}_{>0}, \ u \in \hat{\mathbb{Z}}^\times,$$
where $r$ sits at the infinite place and $u$ at the finite places. We use this factorization many times. The quotient $\mathbb{Q}^\times \backslash \mathbb{A}^\times / \mathbb{R}_{>0}\hat{\mathbb{Z}}^\times$ is trivial. This is the statement that the class number of $\mathbb{Q}$ is 1, and the determinant reduces all the global questions of this chapter to it.

### Compact open subgroups

**Definition 1.1.3 (the subgroups of level $N$).** Let $N \ge 1$ and let $p$ be a prime. Let
$$K_0(N)_p = \left\{ \begin{pmatrix} a & b \\ c & d \end{pmatrix} \in GL_2(\mathbb{Z}_p) : c \in N\mathbb{Z}_p \right\}, \qquad K_1(N)_p = \left\{ \begin{pmatrix} a & b \\ c & d \end{pmatrix} \in K_0(N)_p : d \in 1 + N\mathbb{Z}_p \right\},$$
$$K(N)_p = \left\{ k \in GL_2(\mathbb{Z}_p) : k \in I + N M_2(\mathbb{Z}_p) \right\}.$$
Let $K_0(N) = \prod_p K_0(N)_p$, $K_1(N) = \prod_p K_1(N)_p$ and $K(N) = \prod_p K(N)_p$. These are subgroups of $GL_2(\hat{\mathbb{Z}})$. For $p \nmid N$ the three local groups equal $K_p$, because $N$ is then a unit in $\mathbb{Z}_p$.

So $K_0(N)$ is the set of $k \in GL_2(\hat{\mathbb{Z}})$ whose lower left entry is in $N\hat{\mathbb{Z}}$. For $k \in K_0(N)$ with lower right entry $d_k \in \hat{\mathbb{Z}}$ and $p \mid N$, the entry $c$ of $k_p$ is in $p\mathbb{Z}_p$, so $a d_k \in \mathbb{Z}_p^\times$ at $p$ and $d_k \in \mathbb{Z}_p^\times$. Hence the class $d_k \bmod N$ in $\hat{\mathbb{Z}} / N \hat{\mathbb{Z}} = \mathbb{Z}/N\mathbb{Z}$ is a unit. This is the adelic form of the remark in Volume 4, Section 1.1, that the lower right entry of an element of $\Gamma_0(N)$ is a unit modulo $N$.

**Lemma 1.1.4 (properties of the subgroups of level $N$).** Let $N \ge 1$.
1. The groups $K_0(N) \supset K_1(N) \supset K(N)$ are compact open subgroups of $GL_2(\mathbb{A}_f)$.
2. The group $K(N)$ is the kernel of the reduction map $GL_2(\hat{\mathbb{Z}}) \to GL_2(\mathbb{Z}/N\mathbb{Z})$. This map is surjective, so $K(N)$ is normal in $GL_2(\hat{\mathbb{Z}})$ and $GL_2(\hat{\mathbb{Z}})/K(N) \cong GL_2(\mathbb{Z}/N\mathbb{Z})$.
3. The map $K_0(N) \to (\mathbb{Z}/N\mathbb{Z})^\times$, $k \mapsto d_k \bmod N$, is a surjective homomorphism with kernel $K_1(N)$.
4. One has $\det K_0(N) = \det K_1(N) = \hat{\mathbb{Z}}^\times$, and $\det K(N) = \{u \in \hat{\mathbb{Z}}^\times : u \equiv 1 \bmod N\}$.
5. One has $[GL_2(\hat{\mathbb{Z}}) : K_0(N)] = N \prod_{p \mid N} (1 + 1/p)$.

Lean: not formalized

*Proof.* By the Chinese remainder theorem, $\hat{\mathbb{Z}}/N\hat{\mathbb{Z}} = \prod_{p \mid N} \mathbb{Z}_p / N\mathbb{Z}_p = \mathbb{Z}/N\mathbb{Z}$. The reduction map $GL_2(\hat{\mathbb{Z}}) \to GL_2(\mathbb{Z}/N\mathbb{Z})$ is continuous for the discrete topology on the target, and $K(N)$ is its kernel by definition, so $K(N)$ is open. It is surjective: a matrix over $\mathbb{Z}/N\mathbb{Z}$ with unit determinant lifts, by the Chinese remainder theorem, to a matrix over $\mathbb{Z}_p$ for each $p \mid N$, with determinant a unit of $\mathbb{Z}_p$ because it is a unit modulo $p$. At the primes $p \nmid N$ we take the identity. This proves part 2. The groups $K_0(N)$ and $K_1(N)$ are the preimages of the subgroups of $GL_2(\mathbb{Z}/N\mathbb{Z})$ of the matrices $\begin{pmatrix} a & b \\ 0 & d \end{pmatrix}$ and $\begin{pmatrix} a & b \\ 0 & 1 \end{pmatrix}$, so they are open subgroups that contain $K(N)$. They are closed in the compact group $GL_2(\hat{\mathbb{Z}})$, so they are compact. This proves part 1. Part 3 follows from part 2, because the map $\begin{pmatrix} a & b \\ 0 & d \end{pmatrix} \mapsto d$ is a surjective homomorphism from the upper triangular matrices of $GL_2(\mathbb{Z}/N\mathbb{Z})$ to $(\mathbb{Z}/N\mathbb{Z})^\times$, with kernel the matrices with $d = 1$. For part 4, the matrix $\mathrm{diag}(u, 1)$ with $u \in \hat{\mathbb{Z}}^\times$ is in $K_1(N)$ and has determinant $u$. An element of $K(N)$ is congruent to $I$ modulo $N$, so its determinant is congruent to 1. Conversely $\mathrm{diag}(u, 1) \in K(N)$ for $u \equiv 1 \bmod N$. For part 5, by part 2 the index is the index in $GL_2(\mathbb{Z}/N\mathbb{Z})$ of the group $B(\mathbb{Z}/N\mathbb{Z})$ of the upper triangular matrices. By the Chinese remainder theorem it is the product of the indices for $N = p^e$. The group $GL_2(\mathbb{Z}/p^e\mathbb{Z})$ has $p^{4(e-1)} (p^2 - 1)(p^2 - p)$ elements, because the reduction to $GL_2(\mathbb{F}_p)$ is surjective with kernel $I + pM_2(\mathbb{Z}/p^e\mathbb{Z})$, of order $p^{4(e-1)}$. The group $B(\mathbb{Z}/p^e\mathbb{Z})$ has $(p^{e-1}(p-1))^2 p^e$ elements. The quotient is $p^{e-1}(p+1) = p^e(1 + 1/p)$. $\square$

The index in part 5 is the index $[SL_2(\mathbb{Z}) : \Gamma_0(N)]$ of Volume 4, Proposition 1.1.8. Exercise 4 explains why: the map $\sigma \Gamma_0(N) \mapsto \sigma K_0(N)$ is a bijection from $SL_2(\mathbb{Z})/\Gamma_0(N)$ to $GL_2(\hat{\mathbb{Z}})/K_0(N)$.

**Remark 1.1.5 (level structures in Lean).** The Lean project works with $GL_n$ over a number field $K$. It defines $GL_n(\mathbb{A}_K)$ as `Langlands.AdelicGL`, the embedding of $GL_n(K)$ as `Langlands.principalGL`, and the local embeddings $\iota_v$ as `Langlands.localGL`. The predicate `Langlands.IsInLevel N k` says that $k$ is in the principal congruence subgroup $K(N)$ at the finite places and that its archimedean components are the identity. So for $K = \mathbb{Q}$ and $n = 2$ the Lean level is $K(N)$, not $K_0(N)$. A form of level $K_0(N)$ is also of level $K(N)$, so the Lean definitions cover the forms of this chapter after one forgets the character of $K_0(N)$.

### Standard subgroups and coordinates

**Definition 1.1.6 (standard subgroups and elements).** Let $R$ be one of the rings $\mathbb{Q}$, $\mathbb{Q}_v$, $\mathbb{A}$. Let $B(R)$ be the group of the upper triangular matrices in $GL_2(R)$, $N(R)$ the group of the matrices $n(x) = \begin{pmatrix} 1 & x \\ 0 & 1 \end{pmatrix}$ with $x \in R$, and $Z(R)$ the group of the scalar matrices. Let $n^-(x) = \begin{pmatrix} 1 & 0 \\ x & 1 \end{pmatrix}$. In $GL_2(\mathbb{R})$ let
$$a(y) = \begin{pmatrix} y^{1/2} & 0 \\ 0 & y^{-1/2} \end{pmatrix} \ (y > 0), \qquad \kappa_\theta = \begin{pmatrix} \cos\theta & \sin\theta \\ -\sin\theta & \cos\theta \end{pmatrix} \ (\theta \in \mathbb{R}),$$
and let $SO(2) = \{\kappa_\theta\}$. Let $GL_2^+(\mathbb{R})$ be the subgroup of the matrices with positive determinant. For $g = \begin{pmatrix} a & b \\ c & d \end{pmatrix} \in GL_2^+(\mathbb{R})$ and $\tau \in \mathbb{H}$ let $g\tau = (a\tau + b)/(c\tau + d)$ and $j(g, \tau) = c\tau + d$, as in Volume 4, Section 1.1.

The map $\theta \mapsto \kappa_\theta$ is a homomorphism from $\mathbb{R}$ onto $SO(2)$ with kernel $2\pi\mathbb{Z}$. The sign convention is that of [Bum97]. One computes $\kappa_\theta i = (i\cos\theta + \sin\theta)/(-i\sin\theta + \cos\theta) = i$ and $j(\kappa_\theta, i) = \cos\theta - i \sin\theta = e^{-i\theta}$. The cocycle relation $j(gh, \tau) = j(g, h\tau) j(h, \tau)$ of Volume 4, Lemma 1.1.2, then gives
$$j(g\kappa_\theta, i) = e^{-i\theta} j(g, i), \qquad g\kappa_\theta i = g i \qquad (g \in GL_2^+(\mathbb{R})).$$
For $y > 0$ and $x \in \mathbb{R}$ we have $n(x)a(y) i = x + iy$ and $j(n(x)a(y), i) = y^{-1/2}$.

**Lemma 1.1.7 (the Iwasawa decomposition).**
1. Let $p$ be a prime. Then $GL_2(\mathbb{Q}_p) = B(\mathbb{Q}_p) K_p$.
2. Each $g \in GL_2^+(\mathbb{R})$ has a unique expression $g = z \, n(x) a(y) \kappa_\theta$ with $z > 0$, $x \in \mathbb{R}$, $y > 0$ and $\theta \in \mathbb{R}/2\pi\mathbb{Z}$. Here $z = \det(g)^{1/2}$ and $x + iy = g i$, and $j(g, i) = z y^{-1/2} e^{-i\theta}$.
3. One has $GL_2(\mathbb{A}) = B(\mathbb{A}) \, (O(2) \times GL_2(\hat{\mathbb{Z}}))$, where $O(2)$ is the orthogonal group at the infinite place.

Lean: not formalized

*Proof.* For part 1, let $g \in GL_2(\mathbb{Q}_p)$ with bottom row $(c, d) \ne (0, 0)$. Let $t \in \mathbb{Q}_p^\times$ be an element of the larger of $c$ and $d$ in absolute value, say $t = d$ if $|d|_p \ge |c|_p$ and $t = c$ otherwise. Then $w = t^{-1}(c, d)$ is a vector of $\mathbb{Z}_p^2$ with a coordinate equal to 1. Such a vector is the bottom row of a matrix $k \in K_p$: take $k = \begin{pmatrix} 1 & 0 \\ c/d & 1 \end{pmatrix}$ if $t = d$ and $k = \begin{pmatrix} 0 & -1 \\ 1 & d/c \end{pmatrix}$ if $t = c$. Then $(c, d) = t (0, 1) k$, so the bottom row of $g k^{-1}$ is $(c, d)k^{-1} = (0, t)$, and $b = g k^{-1}$ is upper triangular. So $g = bk$.

For part 2, let $g \in GL_2^+(\mathbb{R})$, let $z = \det(g)^{1/2}$ and $x + iy = gi$. The element $h = (z n(x) a(y))^{-1} g$ has determinant 1 and fixes $i$, because $z n(x)a(y) i = x + iy$ and scalars act trivially on $\mathbb{H}$. The stabilizer of $i$ in $SL_2(\mathbb{R})$ is $SO(2)$: if $\begin{pmatrix} a & b \\ c & d \end{pmatrix} i = i$, then $ai + b = -c + di$, so $d = a$, $c = -b$, and $a^2 + b^2 = 1$. So $h = \kappa_\theta$ for some $\theta$, unique modulo $2\pi$. The numbers $z$, $x$, $y$ are determined by $g$, and then $\kappa_\theta$ is determined. The value of $j(g, i)$ follows from $j(z n(x) a(y), i) = z y^{-1/2}$ and the formula for $j(g\kappa_\theta, i)$ above.

For part 3, part 1 gives $g_p = b_p k_p$ at each prime. For the primes with $g_p \in K_p$ take $b_p = 1$ and $k_p = g_p$. At the infinite place, $GL_2(\mathbb{R}) = GL_2^+(\mathbb{R}) \cup GL_2^+(\mathbb{R})\,\mathrm{diag}(1, -1)$, and part 2 writes an element of $GL_2^+(\mathbb{R})$ as an upper triangular matrix times an element of $SO(2)$. $\square$

**Example 1.1.8 (an Iwasawa factorization).** Let $p$ be a prime and $g = \begin{pmatrix} 1 & 0 \\ 1 & p \end{pmatrix} \in GL_2(\mathbb{Q}_p)$. Its bottom row is $(1, p)$, and $|1|_p \ge |p|_p$, so the proof of part 1 takes $t = 1$ and needs $k \in K_p$ with bottom row $(1, p)$. Let $k = \begin{pmatrix} 0 & -1 \\ 1 & p \end{pmatrix}$, of determinant 1. Then $k^{-1} = \begin{pmatrix} p & 1 \\ -1 & 0 \end{pmatrix}$ and
$$\begin{pmatrix} 1 & 0 \\ 1 & p \end{pmatrix} = \begin{pmatrix} p & 1 \\ 0 & 1 \end{pmatrix} \begin{pmatrix} 0 & -1 \\ 1 & p \end{pmatrix}.$$
The upper triangular factor is one of the $p + 1$ matrices that Section 1.6 uses for the Hecke operator $T_p$. This is not an accident. The matrix $g$ is integral with determinant $p$, and Lemma 1.6.5 shows that each such matrix is in one of the cosets $\begin{pmatrix} p & j \\ 0 & 1 \end{pmatrix} K_p$ or $\begin{pmatrix} 1 & 0 \\ 0 & p \end{pmatrix} K_p$. The decomposition of part 1 is not unique. One may replace $b$ by $b k'$ and $k$ by $k'^{-1}k$ for any $k' \in B(\mathbb{Q}_p) \cap K_p = B(\mathbb{Z}_p)$.

The decomposition of part 2 gives coordinates $(z, x, y, \theta)$ on $GL_2^+(\mathbb{R})$. They identify $GL_2^+(\mathbb{R})$ with $\mathbb{R}_{>0} \times \mathbb{H} \times \mathbb{R}/2\pi\mathbb{Z}$, and the map $g \mapsto gi$ with the projection to $\mathbb{H}$. So $\mathbb{H} = GL_2^+(\mathbb{R}) / \mathbb{R}_{>0} SO(2)$. The function $\phi_f$ of Section 1.3 is written in these coordinates as $y^{k/2} f(x + iy) e^{ik\theta}$. Section 1.4 writes the Lie algebra of $GL_2(\mathbb{R})$ as differential operators in the same coordinates.
