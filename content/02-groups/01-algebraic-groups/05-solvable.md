---
title: Unipotent and solvable groups
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Unipotent and solvable groups

A unipotent group is a group that can be put into upper triangular form with ones on the diagonal. A connected solvable group over an algebraically closed field can be put into upper triangular form, by the theorem of Lie and Kolchin. These two results are the base of the theory of Borel subgroups. This section proves both theorems with the classical arguments of [Spr98], Chapters 2 and 6, and states the structure theorem for connected solvable groups. For the group schemes that are not smooth we refer to [Mil17], Chapters 6, 14 and 16.

### Unipotent groups

**Definition 1.5.1 (unipotent group).** An affine group $G$ is *unipotent* if each nonzero representation of $G$ has a nonzero fixed vector, that is, a vector $v$ with $\rho(v) = v \otimes 1$.

If $G$ is unipotent and $V$ is a finite-dimensional representation, then $V$ has a fixed vector $v_1$, the quotient $V / k v_1$ has a fixed vector, and so on. This gives a basis of $V$ in which $G$ acts by matrices in $U_n$. So a unipotent algebraic group is isomorphic to a closed subgroup of $U_n$, by Theorem 1.2.3. The classical form of the converse is the following theorem.

**Theorem 1.5.2 (Kolchin).** Let $V$ be a nonzero finite-dimensional vector space over a field $k$, and let $\Gamma \subset GL(V)$ be a subgroup whose elements are all unipotent. Then $\Gamma$ fixes a nonzero vector of $V$. Thus there is a basis of $V$ in which $\Gamma$ is contained in $U_n(k)$.

Lean: not stated yet

*Proof.* The fixed vectors are the solutions of the linear equations $g v = v$ for $g \in \Gamma$. Such a system has a nonzero solution over $k$ if it has one over $\bar k$. So we may assume that $k$ is algebraically closed. We may also replace $V$ by a nonzero $\Gamma$-stable subspace of minimal dimension, so that $V$ is an irreducible representation of $\Gamma$. Let $n = \dim V$. By Burnside's theorem, the linear span of $\Gamma$ in $\mathrm{End}(V)$ is all of $\mathrm{End}(V)$, since $V$ is irreducible and $k$ is algebraically closed. Each element of $\Gamma$ is unipotent, so its trace is $n$. Let $g \in \Gamma$. For each $h \in \Gamma$, both $h$ and $gh$ lie in $\Gamma$, so
$$\mathrm{tr}((g - 1) h) = \mathrm{tr}(gh) - \mathrm{tr}(h) = n - n = 0.$$
By linearity $\mathrm{tr}((g - 1) x) = 0$ for all $x \in \mathrm{End}(V)$. The trace form is nondegenerate, so $g = 1$. Thus $\Gamma$ is trivial, and since $V$ is irreducible, $n = 1$. A trivial group fixes every vector. The last statement follows by induction on $\dim V$, applied to $V / k v_1$. $\square$

**Theorem 1.5.3 (unipotent groups).** Let $k$ be algebraically closed and let $G$ be a smooth algebraic group. The following conditions are equivalent:
1. $G$ is unipotent;
2. $G$ is isomorphic to a closed subgroup of $U_n$ for some $n$;
3. every element of $G(k)$ is unipotent.

Over any field, an algebraic group is unipotent if and only if it is isomorphic to a closed subgroup of some $U_n$, and closed subgroups, quotients and extensions of unipotent groups are unipotent.

Lean: not stated yet

*Proof.* Condition 1 implies condition 2 by the remark after Definition 1.5.1. Condition 2 implies condition 3 by Theorem 1.3.7, since the elements of $U_n(k)$ are unipotent matrices. Assume condition 3, and let $V$ be a nonzero finite-dimensional representation. By Theorem 1.3.7, $r(g)$ is unipotent for each $g \in G(k)$, so $r(G(k))$ fixes a nonzero vector $v$ by Theorem 1.5.2. The element $\rho(v) - v \otimes 1$ of $V \otimes \mathcal{O}(G)$ vanishes at each point of $G(k)$. Since $G$ is smooth and $k$ is algebraically closed, $\mathcal{O}(G)$ is reduced, and a function that vanishes at every $k$-point is $0$ by the Nullstellensatz. So $v$ is fixed by $G$. A general representation is the union of its finite-dimensional subrepresentations, by Theorem 1.1.18. This gives condition 1. The statements over any field are in [Mil17], Chapter 14. $\square$

**Example 1.5.4 (unipotent groups and $\mu_p$).** The groups $\mathbb{G}_a$, $U_n$ and $\alpha_p$ are unipotent. In characteristic $p$, a finite $p$-group, as a constant group, is unipotent. But $\mu_p$ in characteristic $p$ is not unipotent, although its only point in each field is $1$. Indeed $\mu_p = D(\mathbb{Z}/p\mathbb{Z})$, and its character $t$ defines a representation on $k$ without fixed vector. Condition 3 of Theorem 1.5.3 sees only the points, and it fails to detect this, so the theorem needs smoothness.

**Proposition 1.5.5 (unipotent and multiplicative groups).** An algebraic group that is both unipotent and diagonalizable is trivial. Every homomorphism from a unipotent group to a diagonalizable group is trivial.

Lean: not stated yet

*Proof.* Let $G = D(M)$ be unipotent. For $\chi \in M$, the representation of $G$ on $k$ by $\chi$ has a nonzero fixed vector, so $\chi = 1$. Thus $M = 0$ and $G$ is trivial. For a homomorphism $f : U \to D$, the image $U / \ker(f)$ of Theorem 1.2.7 is a quotient of $U$, so it is unipotent, since each representation of the quotient is a representation of $U$. It is also a closed subgroup of $D$, so it is diagonalizable by Corollary 1.4.6. So it is trivial. $\square$

For example, there is no nontrivial homomorphism $\mathbb{G}_a \to \mathbb{G}_m$, and none from $\mathbb{G}_m$ to $\mathbb{G}_a$ either. For the second, the image is a quotient of $\mathbb{G}_m$, so it is diagonalizable, and it is a closed subgroup of $\mathbb{G}_a$, so it is unipotent by Theorem 1.5.3.

### Solvable groups

From now on in this section $k$ is algebraically closed and all algebraic groups are smooth. We identify such a group with its group of $k$-points.

**Definition 1.5.6 (derived series).** Let $G$ be an algebraic group. The *derived group* $(G, G)$ is the subgroup generated by the commutators $x y x^{-1} y^{-1}$. The *derived series* is $D^0 G = G$ and $D^{i+1} G = (D^i G, D^i G)$. The *lower central series* is $C^0 G = G$ and $C^{i+1} G = (G, C^i G)$. The group $G$ is *solvable* if $D^n G = 1$ for some $n$, and *nilpotent* if $C^n G = 1$ for some $n$.

If $G$ is connected, then $(G, G)$ is closed and connected, by Proposition 1.2.12 applied to the commutator map $G \times G \to G$, whose image contains $e$. The same holds for each term of the two series. Thus a connected group $G$ is solvable if and only if the abstract group $G(k)$ is solvable. For a group that is not connected we use the abstract group $G(k)$ in the definitions.

**Example 1.5.7 (triangular groups).** For $1 \le m \le n$, let $U^{(m)}$ be the closed subgroup of $U_n$ of the matrices $u$ with $u_{ij} = 0$ for $0 < j - i < m$. So $U^{(1)} = U_n$, and $U^{(n)} = 1$. A computation with the matrix entries shows that $(U^{(a)}, U^{(b)}) \subset U^{(a + b)}$ and that $U^{(m)} / U^{(m+1)} \cong \mathbb{G}_a^{n - m}$, by the entries on the $m$-th diagonal above the main one. So $C^i U_n \subset U^{(i+1)}$, and $U_n$ is nilpotent. The map $B_n \to D_n$ that keeps the diagonal is a homomorphism to a commutative group with kernel $U_n$. So $(B_n, B_n) \subset U_n$, and $B_n$ is solvable. It is not nilpotent for $n \ge 2$. For $n = 2$, the commutator of $t = \mathrm{diag}(a, 1)$ and $u = \left(\begin{smallmatrix} 1 & x \\ 0 & 1 \end{smallmatrix}\right)$ is $\left(\begin{smallmatrix} 1 & (a - 1) x \\ 0 & 1 \end{smallmatrix}\right)$, so $C^i B_2 = U_2$ for all $i \ge 1$.

**Theorem 1.5.8 (Lie and Kolchin).** Let $k$ be algebraically closed, let $G$ be a connected solvable algebraic group, and let $V$ be a nonzero finite-dimensional representation of $G$. Then $G$ fixes a line in $V$. Thus there is a basis of $V$ in which $G$ maps into $B_n$.

Lean: not stated yet

*Proof.* We argue by induction on the length of the derived series of $G$ and on $\dim V$. If $G$ is trivial there is nothing to prove. We may replace $V$ by a nonzero $G$-stable subspace of minimal dimension, so we may assume that $V$ has no $G$-stable subspace other than $0$ and $V$. We shall show that $\dim V = 1$.

Let $H = (G, G)$. It is connected and solvable, with a shorter derived series. By induction, $H$ fixes a line in $V$, and it acts on this line by a character $\chi$ of $H$. For each character $\psi$ of $H$ let $V_\psi = \{v \in V : h v = \psi(h) v \text{ for all } h \in H\}$. The sum of the spaces $V_\psi$ is direct, by the argument of Lemma 1.4.2, so only finitely many of them are nonzero. Since $H$ is normal in $G$, each $g \in G$ maps $V_\psi$ to $V_{g \psi}$, where $(g \psi)(h) = \psi(g^{-1} h g)$. So $G$ permutes the finitely many nonzero spaces $V_\psi$. The stabilizer of $V_\chi$ in $G$ is a closed subgroup of finite index. Since $G$ is connected, it is all of $G$. So $V_\chi$ is a nonzero $G$-stable subspace, and $V_\chi = V$.

Thus each $h \in H$ acts on $V$ by the scalar $\chi(h)$. Each element of $H$ is a product of commutators, so its determinant on $V$ is $1$. Hence $\chi(h)^n = 1$ with $n = \dim V$, and $\chi$ takes values in the finite group $\mu_n(k)$. The image $\chi(H)$ is connected, since $H$ is connected. So $\chi$ is trivial, and $H$ acts trivially on $V$. The group $G$ then acts on $V$ through the commutative group $G / H$. Commuting endomorphisms of a vector space over an algebraically closed field have a common eigenvector, and its line is $G$-stable. So $\dim V = 1$. The last statement follows by induction on $\dim V$. $\square$

**Corollary 1.5.9 (the unipotent elements of a solvable group).** Let $G$ be a connected solvable group. The set $G_u$ of unipotent elements of $G$ is a closed normal subgroup. It contains $(G, G)$, and it is the kernel of a homomorphism from $G$ onto a torus.

Lean: not stated yet

*Proof.* Choose a closed embedding $G \to GL_n$. By Theorem 1.5.8 we may assume that $G \subset B_n$. An element of $B_n$ is unipotent if and only if its diagonal entries are all $1$. So $G_u$ is the kernel of the restriction $\delta : G \to D_n$ of the diagonal map. The image $\delta(G)$ is a closed connected subgroup of $D_n$. It is diagonalizable by Corollary 1.4.6, and it is a torus by Proposition 1.4.7. Since $D_n$ is commutative, $(G, G) \subset G_u$. $\square$

**Theorem 1.5.10 (structure of connected solvable groups).** Let $G$ be a connected solvable group over an algebraically closed field. Then:
1. the group $G_u$ is connected;
2. the maximal tori of $G$ are conjugate under $G_u$;
3. for each maximal torus $T$, the product map $T \ltimes G_u \to G$ is an isomorphism of algebraic groups, so $G / G_u \cong T$;
4. each semisimple element of $G$ lies in a maximal torus.

Lean: not stated yet

The proof is by induction on $\dim G$, with the study of the action of a torus on a commutative unipotent group. See [Spr98], Chapter 6, and, for groups over an arbitrary field, [Mil17], Chapter 16. In $B_n$, the diagonal torus $D_n$ is a maximal torus, $G_u = U_n$, and $B_n = D_n \ltimes U_n$ as in Example 1.2.2.

**Theorem 1.5.11 (commutative groups).** Let $G$ be a commutative algebraic group over an algebraically closed field. Then the sets $G_s$ and $G_u$ of semisimple and unipotent elements are closed subgroups, $G_s$ is diagonalizable, and the product map $G_s \times G_u \to G$ is an isomorphism of algebraic groups. If $G$ is connected, then $G_s$ is a torus.

Lean: not stated yet

*Proof sketch.* Since $G$ is commutative, $g_s$ and $h_s$ commute with $g_u$ and $h_u$, and so $(gh)_s = g_s h_s$ and $(gh)_u = g_u h_u$. Thus $G_s$ and $G_u$ are subgroups, and $g \mapsto (g_s, g_u)$ is a bijection $G \to G_s \times G_u$. Embed $G$ in $GL(V)$. Since $G$ is commutative, $V$ is the direct sum of the common generalized eigenspaces $V_i$ of $G$, and on each $V_i$ the elements of $G_s$ act by scalars. By Theorem 1.5.2, applied to the commutative group $G_u$ on each $V_i$, there is a basis of each $V_i$ in which $G_u$ acts by unipotent upper triangular matrices. So in a suitable basis, $G_s = G \cap D_n$ and $G_u = G \cap U_n$, which are closed. Then $G_s$ is diagonalizable by Theorem 1.4.5. One shows that $g \mapsto g_s$ is a morphism of varieties ([Spr98], Chapter 3). If $G$ is connected, then so is its image $G_s$ under this morphism, and $G_s$ is a torus by Proposition 1.4.7. $\square$

**Example 1.5.12 (the hypotheses of Lie and Kolchin).** The three hypotheses of Theorem 1.5.8 are all needed.
1. Connectedness. Let $T$ be the diagonal torus of $SL_2$ and $w = \left(\begin{smallmatrix} 0 & 1 \\ -1 & 0 \end{smallmatrix}\right)$. The normalizer $N = T \cup wT$ of $T$ is solvable, since $T$ is a commutative normal subgroup of index $2$. A line stable under $N$ is stable under $T$, so it is $k e_1$ or $k e_2$, since these are the eigenlines of $T$ with distinct characters. But $w$ exchanges them. So $N$ fixes no line.
2. Connectedness again. The quaternion group $Q_8 = \{\pm 1, \pm I, \pm J, \pm K\} \subset SL_2(\mathbb{C})$, with $I = \mathrm{diag}(i, -i)$, $J = \left(\begin{smallmatrix} 0 & 1 \\ -1 & 0 \end{smallmatrix}\right)$ and $K = IJ$, is nilpotent. The eigenlines of $I$ are $\mathbb{C} e_1$ and $\mathbb{C} e_2$, and $J$ exchanges them. So $Q_8$ fixes no line in $\mathbb{C}^2$. It is a finite group, and a finite nontrivial group is not connected.
3. An algebraically closed field. The group $SO_2$ over $\mathbb{R}$ is connected and commutative. A rotation by an angle that is not a multiple of $\pi$ has no real eigenvector, so $SO_2$ fixes no line in $\mathbb{R}^2$. Over $\mathbb{C}$ it fixes the lines of $e_1 \pm i e_2$, which are not defined over $\mathbb{R}$.

**Remark 1.5.13 (Lie's theorem).** The theorem of Lie and Kolchin has a counterpart for Lie algebras. Let $\mathfrak{g}$ be a solvable Lie algebra over an algebraically closed field of characteristic $0$. Then each nonzero finite-dimensional representation of $\mathfrak{g}$ has a common eigenvector. This is Lie's theorem. Chapter 2 uses it, and its proof is in [Hum72], Section 4. Lie's theorem fails in characteristic $p$, while the theorem of Lie and Kolchin holds in all characteristics. For a connected solvable group over $\mathbb{C}$, one can deduce the group version from the Lie algebra version through the exponential map, but the proof above works directly.

Lean: `LieModule.exists_nontrivial_weightSpace_of_isSolvable`, from Mathlib
