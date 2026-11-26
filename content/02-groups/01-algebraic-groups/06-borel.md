---
title: Borel subgroups
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Borel subgroups

A Borel subgroup of a connected group $G$ is a maximal connected solvable subgroup. For $GL_n$ it is the stabilizer of a full flag, for example the upper triangular group $B_n$. The main theorem of this section says that all Borel subgroups are conjugate and that $G/B$ is a projective variety. The tool is Borel's fixed point theorem: a connected solvable group that acts on a complete variety has a fixed point. In this section $k$ is algebraically closed, all groups are smooth, and we identify a group with its group of $k$-points. We follow [Spr98], Chapter 6, and [Mil17], Chapter 17.

### Complete varieties and orbits

A variety $X$ is *complete* if for each variety $Y$ the projection $X \times Y \to Y$ maps closed sets to closed sets. This is the algebraic form of compactness.

**Proposition 1.6.1 (complete varieties).** Let $X$ be a complete variety.
1. Projective varieties are complete.
2. A closed subvariety of $X$ is complete. If $f : X \to Y$ is a morphism, then $f(X)$ is closed in $Y$ and complete.
3. A complete variety that is quasi-projective is projective.
4. If $X$ is connected and $Y$ is affine, then each morphism $X \to Y$ is constant. In particular a connected complete affine variety is a point.

Lean: not stated yet

See [Spr98], Chapter 6. Part 1 is the main theorem of elimination theory. Part 4 follows from part 2: the image of $X$ under each coordinate function is a closed connected complete subvariety of the affine line, and the only such sets are points.

**Proposition 1.6.2 (closed orbits).** Let $G$ act on a variety $X$ by a morphism $G \times X \to X$. Each orbit $G x$ is open in its closure. The boundary $\overline{G x} \smallsetminus G x$ is a union of orbits of strictly smaller dimension. In particular the orbits of minimal dimension are closed, and closed orbits exist.

Lean: not stated yet

*Proof.* The orbit $G x$ is the image of the morphism $G \to X$, $g \mapsto g x$, so it is a constructible set. Thus it contains a dense open subset $U$ of its closure $\overline{G x}$. The closure is $G$-stable, and $G x = \bigcup_{g} g U$ is open in $\overline{G x}$. The boundary is closed, $G$-stable, and has no interior point in $\overline{Gx}$. So each of its irreducible components has smaller dimension than the components of $\overline{Gx}$. Since $\overline{G x}$ is the closure of a single orbit, all its components have the dimension $\dim Gx$. $\square$

### The fixed point theorem

**Theorem 1.6.3 (Borel's fixed point theorem).** Let $G$ be a connected solvable group, and let $X$ be a nonempty complete variety with an action of $G$. Then $G$ has a fixed point in $X$.

Lean: not stated yet

We prove the theorem when $X$ is a closed $G$-stable subvariety of a projective space $\mathbb{P}(V)$, where $V$ is a finite-dimensional representation of $G$. This is the only case that we need. For the general case see [Spr98], Chapter 6, or [Mil17], Chapter 17.

*Proof in the linear case.* We argue by induction on $\dim V$. If $\dim V = 1$, then $X$ is a point. By Theorem 1.5.8 there is a $G$-stable line $L = k v$ in $V$. If $[v] \in X$, it is a fixed point. If not, let $\pi : \mathbb{P}(V) \smallsetminus \{[v]\} \to \mathbb{P}(V / L)$ be the projection from $[v]$. It is a $G$-equivariant morphism, and it is defined on $X$. By Proposition 1.6.1, the image $X' = \pi(X)$ is closed in $\mathbb{P}(V/L)$ and complete. It is $G$-stable. By induction, $G$ fixes a point $x'$ of $X'$. Let $P \subset V$ be the inverse image of the line $x'$. It is a $G$-stable plane that contains $L$. The set $F = X \cap \mathbb{P}(P)$ is closed in the projective line $\mathbb{P}(P)$, it is nonempty because $x' \in \pi(X)$, and it does not contain $[v]$. So $F$ is a proper closed subset of $\mathbb{P}^1$, hence finite. It is $G$-stable. The connected group $G$ permutes the finite set $F$, so it fixes each point of $F$, as in the proof of Theorem 1.4.12. $\square$

**Example 1.6.4 (a torus acting on the projective line).** Let $\mathbb{G}_m$ act on $\mathbb{P}^1$ by $t \cdot [x : y] = [t x : y]$. The fixed points are $[1 : 0]$ and $[0 : 1]$, and the other points form one orbit, which is open and dense. On the affine line $\mathbb{A}^1 = \mathbb{P}^1 \smallsetminus \{[1:0]\}$ the action of $\mathbb{G}_a$ by translation has no fixed point. So completeness is needed. For $X = \mathbb{P}^1$ and $G = SO_2$ over $\mathbb{R}$, acting through rotations of $\mathbb{R}^2$, there is no real fixed point. So the field must be algebraically closed.

### Borel subgroups

**Definition 1.6.5 (Borel subgroup).** Let $G$ be a connected group. A *Borel subgroup* of $G$ is a closed connected solvable subgroup of $G$ that is maximal for these properties.

Borel subgroups exist, by dimension. If $G$ is solvable, then $G$ itself is its only Borel subgroup.

**Theorem 1.6.6 (conjugacy of Borel subgroups).** Let $G$ be a connected group and let $B$ be a Borel subgroup. Then $G/B$ is a projective variety, and every Borel subgroup of $G$ is conjugate to $B$.

Lean: not stated yet

*Proof.* Choose a Borel subgroup $B$ of maximal dimension. By Theorem 1.2.8 there is a representation $V$ of $G$ and a line $L \subset V$ whose stabilizer is $B$. As explained after Theorem 1.2.8, the quotient $G/B$ is the orbit $G \cdot L$ in $\mathbb{P}(V)$. Let $n = \dim V$. By Theorem 1.5.8, applied to $B$ acting on $V/L$, there is a full flag $f_0 = (V_1 \subset V_2 \subset \dots \subset V_n = V)$ with $V_1 = L$ and with each $V_i$ stable under $B$. Let $\mathcal{F}$ be the variety of full flags in $V$. It is a closed subvariety of a product of Grassmannians, so it is projective. The stabilizer of $f_0$ in $G$ contains $B$ and fixes $L$, so it equals $B$.

Let $f$ be any flag in $\mathcal{F}$. In a basis adapted to $f$, the stabilizer $G_f$ maps into $B_n$, so $G_f$ is solvable, and $(G_f)^\circ$ is contained in a Borel subgroup. Thus $\dim G_f \le \dim B$, and
$$\dim G f = \dim G - \dim G_f \ge \dim G - \dim B = \dim G f_0.$$
So $G f_0$ is an orbit of minimal dimension in $\mathcal{F}$, and it is closed by Proposition 1.6.2. It is complete by Proposition 1.6.1. The map $\mathcal{F} \to \mathbb{P}(V)$, $f \mapsto V_1$, is a morphism, and it maps $G f_0$ onto $G \cdot L = G/B$. So $G/B$ is complete. It is quasi-projective, hence projective.

Let $B'$ be any Borel subgroup. It acts on $G/B = G \cdot L$, a closed subvariety of $\mathbb{P}(V)$ with a linear action. By Theorem 1.6.3 it has a fixed point $g B$. Then $B' g B = g B$, so $g^{-1} B' g \subset B$. Since $g^{-1} B' g$ is a Borel subgroup, it is maximal, and $g^{-1} B' g = B$. So every Borel subgroup is conjugate to $B$. In particular all Borel subgroups have the maximal dimension, and the first part of the proof applies to each of them. $\square$

A closed subgroup $P$ of $G$ is *parabolic* if $G/P$ is complete.

**Corollary 1.6.7 (parabolic subgroups).** A closed subgroup $P$ of a connected group $G$ is parabolic if and only if it contains a Borel subgroup. A Borel subgroup is a parabolic subgroup that is connected and solvable.

Lean: not stated yet

*Proof.* If $P \supset B$, then $G/P$ is the image of the complete variety $G/B$, so it is complete by Proposition 1.6.1. Conversely let $G/P$ be complete. By Theorem 1.2.8 and Proposition 1.6.1, $G/P$ is a closed orbit in a projective space $\mathbb{P}(V)$ with a linear action. So $B$ has a fixed point $g P$ by Theorem 1.6.3, and $g^{-1} B g \subset P$. For the last statement, let $P$ be parabolic, connected and solvable. Then $P$ contains a Borel subgroup $B$, and $B = P$ by maximality. Theorem 1.6.6 gives the converse. $\square$

**Theorem 1.6.8 (consequences).** Let $G$ be a connected group.
1. The maximal tori of $G$ are conjugate. Each maximal torus of a Borel subgroup is a maximal torus of $G$.
2. Each element of $G$ lies in a Borel subgroup, so $G$ is the union of the conjugates of $B$.
3. The normalizer of a Borel subgroup is the subgroup itself: $N_G(B) = B$.
4. The centralizer of a torus in $G$ is connected.

Lean: not stated yet

The proof of part 1 is short. Each torus $S$ is connected and solvable, so it lies in a Borel subgroup, which is conjugate to $B$. So each maximal torus is conjugate to a maximal torus of $B$, and these are conjugate in $B$ by Theorem 1.5.10. Parts 2 to 4 are harder. The proofs use the study of $G/B$ and an induction on $\dim G$. See [Spr98], Chapter 6, and [Mil17], Chapter 17.

### The examples

**Example 1.6.9 (the Borel subgroups of $GL_n$).** Let $f_{\mathrm{std}} = (\langle e_1 \rangle \subset \langle e_1, e_2 \rangle \subset \dots)$ be the standard flag of $V = k^n$. Its stabilizer in $GL_n$ is $B_n$, which is connected and solvable. We show that $B_n$ is a Borel subgroup. Let $H \supset B_n$ be closed, connected and solvable. By Theorem 1.5.8, $H$ fixes some full flag $f = (W_1 \subset \dots \subset W_n)$. Then $B_n$ fixes $f$. The only line fixed by $B_n$ is $\langle e_1 \rangle$, because the only line fixed by the diagonal torus and by the elementary matrices $1 + t E_{1j}$ is $\langle e_1 \rangle$. So $W_1 = \langle e_1 \rangle$. Applying the same argument to $B_n$ acting on $V / \langle e_1 \rangle$, through its image $B_{n-1}$, gives $W_2 = \langle e_1, e_2 \rangle$, and so on. So $f = f_{\mathrm{std}}$, and $H \subset B_n$. By Theorem 1.6.6, the Borel subgroups of $GL_n$ are the conjugates $g B_n g^{-1}$, that is, the stabilizers of the full flags $g f_{\mathrm{std}}$. Thus $GL_n / B_n$ is the variety $\mathcal{F}$ of full flags in $k^n$. For $n = 2$ it is the projective line, and for $n = 3$ it is the variety of pairs (point, line) in $\mathbb{P}^2$ with the point on the line, a hypersurface of $\mathbb{P}^2 \times \mathbb{P}^2$. The same holds for $SL_n$, with $B_n \cap SL_n$. The Borel subgroups that contain $D_n$ are the stabilizers of the flags $(\langle e_{\sigma(1)} \rangle \subset \langle e_{\sigma(1)}, e_{\sigma(2)} \rangle \subset \dots)$ with $\sigma \in S_n$. There are $n! = |W(GL_n, D_n)|$ of them, and they are the conjugates of $B_n$ by the permutation matrices.

**Example 1.6.10 (counting flags over a finite field).** The flag variety $\mathcal{F}$ is defined over $\mathbb{F}_q$, and $GL_n(\mathbb{F}_q)$ acts transitively on the flags in $\mathbb{F}_q^n$, with stabilizer $B_n(\mathbb{F}_q)$. We have
$$|GL_n(\mathbb{F}_q)| = \prod_{i=0}^{n-1} (q^n - q^i) = q^{n(n-1)/2} \prod_{i=1}^n (q^i - 1), \qquad |B_n(\mathbb{F}_q)| = (q - 1)^n q^{n(n-1)/2}.$$
So the number of full flags in $\mathbb{F}_q^n$ is
$$|\mathcal{F}(\mathbb{F}_q)| = \prod_{i=1}^n \frac{q^i - 1}{q - 1} = \prod_{i=1}^n (1 + q + \dots + q^{i-1}).$$
For $n = 3$ and $q = 2$ this is $1 \cdot 3 \cdot 7 = 21$: there are $7$ points in $\mathbb{P}^2(\mathbb{F}_2)$, and $3$ lines through each. As a polynomial in $q$, the number is $\sum_{w \in S_n} q^{\ell(w)}$, where $\ell(w)$ is the number of inversions of $w$. This reflects the Bruhat decomposition of Chapter 3, in which $\mathcal{F}$ is the disjoint union of cells $B w B / B \cong \mathbb{A}^{\ell(w)}$.

**Example 1.6.11 (the group $SL_2$).** Let $G = SL_2$, with Borel subgroup $B$ of upper triangular matrices, diagonal torus $T$, and $w = \left(\begin{smallmatrix} 0 & 1 \\ -1 & 0 \end{smallmatrix}\right)$. The map $g \mapsto g [e_1]$ identifies $G/B$ with $\mathbb{P}^1$. The Borel subgroups are the stabilizers of the points of $\mathbb{P}^1$. The normalizer of $T$ is $T \cup w T$, so $W(G, T) = \{1, w\}$ has order $2$. The torus $T$ has exactly two fixed points on $\mathbb{P}^1$, namely $[e_1]$ and $[e_2]$, and they correspond to the two Borel subgroups that contain $T$: the group $B$ and the group $w B w^{-1}$ of lower triangular matrices. The decomposition $G = B \sqcup B w B$ is the Bruhat decomposition of $SL_2$: the point $[e_1]$ is the cell $B/B$, and its complement $B w B / B$ is an affine line.

**Remark 1.6.12 (Borel subgroups over a field that is not algebraically closed).** Let $G$ be a connected reductive group over a field $k$. A *Borel subgroup of $G$ over $k$* is a closed subgroup $B$ of $G$ such that $B_{\bar k}$ is a Borel subgroup of $G_{\bar k}$. It need not exist. Let $G = SO(q)$ for $q = x^2 + y^2 + z^2$ over $\mathbb{R}$. Over $\mathbb{C}$, one checks that the Borel subgroups of $SO(q)$ are the stabilizers of the isotropic lines of $q$, so that $G_{\mathbb{C}} / B$ is the conic $q = 0$ in $\mathbb{P}^2$. A Borel subgroup defined over $\mathbb{R}$ would fix a real point of this conic. But $x^2 + y^2 + z^2 = 0$ has no nonzero real solution. So $G$ has no Borel subgroup over $\mathbb{R}$, in agreement with the fact that $G(\mathbb{R}) = SO_3(\mathbb{R})$ is compact. A group that has a Borel subgroup over $k$ is *quasi-split*. The split groups, such as $GL_n$ and $SL_n$, are quasi-split. Chapter 3 shows that the quasi-split forms of $G$ correspond to the actions of $\Gamma_k$ on the based root datum, and Chapter 5 uses this to define the L-group.
