---
title: Reductive and semisimple groups
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Reductive and semisimple groups

This section defines reductive and semisimple groups, proves that the classical groups are reductive, and describes a reductive group as a central torus times a semisimple group, up to a finite kernel. It ends with the maximal tori and the notion of a split group. The example to keep in mind is $GL_n = \mathbb{G}_m \cdot SL_n$. We follow [Mil17], Chapters 17 and 19, and [Spr98], Chapters 7 and 8.

### Definitions

Let $G$ be a smooth connected algebraic group over $k$. If $H_1$ and $H_2$ are smooth connected normal solvable subgroups of $G_{\bar k}$, then so is $H_1 H_2$. Since the dimension is bounded, there is a largest such subgroup, and the same holds for unipotent subgroups (Chapter 1).

**Definition 3.1.1 (radical and unipotent radical).** Let $G$ be a smooth connected algebraic group over $k$. The *radical* $R(G_{\bar k})$ is the largest smooth connected normal solvable subgroup of $G_{\bar k}$. The *unipotent radical* $R_u(G_{\bar k})$ is the largest smooth connected normal unipotent subgroup of $G_{\bar k}$.

A unipotent group is solvable, so $R_u(G_{\bar k}) \subset R(G_{\bar k})$. In fact $R_u(G_{\bar k})$ is the unipotent part of $R(G_{\bar k})$, by the structure theorem for connected solvable groups of Chapter 1.

**Definition 3.1.2 (reductive and semisimple groups).** A smooth connected algebraic group $G$ over $k$ is *reductive* if $R_u(G_{\bar k}) = 1$. It is *semisimple* if $R(G_{\bar k}) = 1$.

A semisimple group is reductive. Both conditions are geometric: $G$ is reductive if and only if $G_{k'}$ is reductive for one, or for every, field extension $k'$ of $k$. Over an imperfect field a group can have no smooth connected normal unipotent subgroup over $k$ and still fail to be reductive. Such groups are called pseudo-reductive, and this handbook does not use them.

**Example 3.1.3 (first examples).** A torus $T$ is reductive. Indeed $T_{\bar k} \cong \mathbb{G}_m^r$ is commutative, so $R(T_{\bar k}) = T_{\bar k}$, and a diagonalizable group has no nontrivial unipotent subgroup. A torus is semisimple only if it is trivial. The additive group $\mathbb{G}_a$ is unipotent, so $R_u(\mathbb{G}_a) = \mathbb{G}_a$ and $\mathbb{G}_a$ is not reductive. Let $B_n \subset GL_n$ be the group of invertible upper triangular matrices, and $U_n$ the subgroup with ones on the diagonal. For $n \ge 2$, $U_n$ is a nontrivial smooth connected normal unipotent subgroup of $B_n$. So $B_n$ is not reductive. Here $R(B_n) = B_n$ and $R_u(B_n) = U_n$.

The next proposition is the standard way to prove that a group is reductive.

**Proposition 3.1.4 (a criterion).** Let $G \subset GL_V$ be a smooth connected closed subgroup, where $V$ is a finite dimensional vector space over $k$. Assume that $V_{\bar k}$ is a semisimple representation of $G_{\bar k}$. Then $G$ is reductive.

Lean: not stated yet

*Proof.* We work over $\bar k$. Let $U = R_u(G_{\bar k})$ and let $W \subset V_{\bar k}$ be a simple $G$-submodule. A unipotent group has a nonzero fixed vector in each nonzero representation (Chapter 1), so $W^U \ne 0$. The subspace $W^U$ is stable under $G(\bar k)$: for $g \in G(\bar k)$, $u \in U(\bar k)$ and $w \in W^U$ we have $u g w = g (g^{-1} u g) w = g w$, because $U$ is normal. As $G$ is smooth, $G(\bar k)$ is dense in $G$, and $W^U$ is a $G$-submodule. Thus $W^U = W$. Since $V_{\bar k}$ is a sum of simple submodules, $U$ acts trivially on $V_{\bar k}$. But $U \subset GL_V$, so $U = 1$. $\square$

**Example 3.1.5 (the classical groups are reductive).** The groups $GL_n$, $SL_n$, $Sp_{2n}$ and, when the characteristic of $k$ is not 2, $SO_n$ are smooth and connected ([Spr98], Chapter 2). The group $SL_n(\bar k)$ acts transitively on the nonzero vectors of $\bar k^n$, so $\bar k^n$ has no nonzero proper invariant subspace. The same holds for $GL_n$ and, by Witt's theorem, for $Sp_{2n}$, because each nonzero vector is the first vector of a symplectic basis. By Proposition 3.1.4 these groups are reductive. For $n \ge 3$ the standard representation of $SO_n$ is also irreducible (Exercise 1), so $SO_n$ is reductive. The group $SO_2$ is a torus of dimension 1.

### The structure of a reductive group

**Theorem 3.1.6 (center and derived group).** Let $G$ be a reductive group over $k$. Let $Z$ be the largest subtorus of the center of $G$, and $DG$ the derived group.
1. The radical $R(G_{\bar k})$ is equal to $Z_{\bar k}$.
2. The derived group $DG$ is semisimple.
3. The multiplication map $Z \times DG \to G$ is surjective with finite central kernel. Thus $Z \cap DG$ is finite and $G = Z \cdot DG$.

Lean: not stated yet

*Proof sketch.* Let $R = R(G_{\bar k})$. By the structure theorem for connected solvable groups (Chapter 1), $R$ is a semidirect product of a torus and its unipotent part $R_u$, and $R_u$ is a characteristic subgroup of $R$. So $R_u$ is a normal unipotent subgroup of $G_{\bar k}$, and $R_u = 1$. Thus $R$ is a torus. The group $G_{\bar k}$ is connected and acts on the normal torus $R$ by conjugation. The automorphism group of $R \cong \mathbb{G}_m^r$ is the discrete group $GL_r(\mathbb{Z})$, so the action is trivial, and $R$ is central. Conversely $Z_{\bar k}$ is a connected solvable normal subgroup, so $Z_{\bar k} \subset R$. This proves 1.

We prove the finiteness of $Z \cap DG$. Choose a faithful representation $V$ of $G$. Over $k_s$ it decomposes as $V = \bigoplus_\chi V_\chi$ under the torus $Z$, where $\chi$ runs through the characters of $Z$. Since $Z$ is central, $G$ preserves each $V_\chi$. The derived group acts on $V_\chi$ with determinant 1. An element $z \in Z \cap DG$ acts on $V_\chi$ by the scalar $\chi(z)$, so $\chi(z)^{n_\chi} = 1$ with $n_\chi = \dim V_\chi$. As $V$ is faithful, the characters $\chi$ with $V_\chi \ne 0$ generate a subgroup of finite index of $X^*(Z)$, and so do the characters $n_\chi \chi$. So $Z \cap DG$ lies in a finite diagonalizable group. The proof that $Z \cdot DG = G$ and that $DG$ is semisimple uses the root subgroups of Section 3.2. See [Mil17], Chapter 19, and [Spr98], Chapter 8. $\square$

**Example 3.1.7 (the group $GL_n$).** For $G = GL_n$ the torus $Z$ is the group $\mathbb{G}_m$ of scalar matrices, and $DG = SL_n$. The kernel of $\mathbb{G}_m \times SL_n \to GL_n$ is the group of pairs $(\zeta, \zeta^{-1})$ with $\zeta \in \mu_n$. On points over $\bar k$ the map is surjective: if $g \in GL_n(\bar k)$ and $z^n = \det g$, then $g = z \cdot (z^{-1} g)$ with $z^{-1} g \in SL_n(\bar k)$. When the characteristic of $k$ divides $n$, the kernel $\mu_n$ is not smooth, which is one reason to work with group schemes.

In characteristic 0 the reductive groups are exactly the groups whose representations are semisimple.

**Theorem 3.1.8 (complete reducibility in characteristic 0).** Let $k$ have characteristic 0, and let $G$ be a smooth connected algebraic group over $k$. Then $G$ is reductive if and only if each finite dimensional representation of $G$ is semisimple.

Lean: not stated yet

*Proof sketch.* If each representation is semisimple, apply Proposition 3.1.4 to a faithful representation. Conversely let $G$ be reductive and $V$ a representation. In characteristic 0 a subspace of $V$ is stable under $G$ if and only if it is stable under the Lie algebra $\mathfrak{g}$ ([Mil17], Chapter 10). By Theorem 3.1.6, $\mathfrak{g} = \mathfrak{z} \oplus \mathrm{Lie}(DG)$, where $\mathfrak{z} = \mathrm{Lie}(Z)$. The Lie algebra of the semisimple group $DG$ is a semisimple Lie algebra in characteristic 0, so $V$ is a semisimple $\mathrm{Lie}(DG)$-module by Weyl's theorem (Chapter 2). The torus $Z$ acts semisimply and commutes with $DG$, so it preserves the isotypic components of $V$ under $\mathrm{Lie}(DG)$. Each simple $\mathfrak{g}$-submodule then has a complement. $\square$

**Example 3.1.9 (a failure in characteristic 2).** Let $k$ have characteristic 2, and let $SL_2$ act on the space $V$ of quadratic forms $a x^2 + b xy + c y^2$ by substitution. The subspace $W$ spanned by $x^2$ and $y^2$ is stable, because $(\alpha x + \gamma y)^2 = \alpha^2 x^2 + \gamma^2 y^2$. A stable complement of $W$ would be a stable line, and since $SL_2$ has no nontrivial character, a line of fixed vectors. The substitution $y \mapsto x + y$ sends $a x^2 + bxy + cy^2$ to $(a + b + c)x^2 + bxy + cy^2$, so a fixed vector has $b = c$. The substitution $x \mapsto x + y$ gives $a = b$ in the same way. The torus element $x \mapsto tx$, $y \mapsto t^{-1} y$ multiplies $x^2$ by $t^2$, so $a = 0$. Thus there is no fixed vector, and $V$ is not semisimple although $SL_2$ is reductive. In characteristic $p$ the simple representations of a reductive group are still classified by their highest weights (Chapter 4), but a representation need not be a direct sum of simple ones.

### Maximal tori and split groups

**Theorem 3.1.10 (maximal tori).** Let $G$ be a smooth connected algebraic group over $k$.
1. The group $G$ has a maximal torus defined over $k$, and each maximal torus of $G$ remains maximal in $G_{\bar k}$.
2. Any two maximal tori of $G_{\bar k}$ are conjugate under $G(\bar k)$.
3. If $G$ is reductive and $T$ is a maximal torus of $G$, then $C_G(T) = T$.

Lean: not stated yet

*Proof sketch.* Part 1 is a theorem of Grothendieck. For a proof over an infinite field, see [Spr98], Chapter 13. Over a finite field it follows from Lang's theorem (Section 3.8). Part 2 is the conjugacy theorem of Chapter 1. For part 3, the centralizer $C = C_G(T)$ is smooth and connected (Chapter 1), and $T$ is a central maximal torus of $C$. Thus $C$ is nilpotent, and $C = T \times C_u$ with $C_u$ unipotent. The proof that $C_u = 1$ uses the reductive groups of semisimple rank one of Section 3.2. See [Spr98], Chapter 7, and [Mil17], Chapter 17. $\square$

**Definition 3.1.11 (rank, split torus, split reductive group).** The *rank* of a smooth connected group $G$ is the dimension of a maximal torus. The *semisimple rank* of a reductive group $G$ is the rank of $DG$. A torus $T$ over $k$ is *split* if $T \cong \mathbb{G}_m^r$ over $k$, or equivalently, if $\Gamma$ acts trivially on $X^*(T)$. A reductive group $G$ is *split* if it has a maximal torus that is split over $k$. A *split reductive group* is a pair $(G, T)$ of a reductive group $G$ and a split maximal torus $T$ of $G$.

By Theorem 3.1.6, the rank of $G$ is $\dim Z$ plus the semisimple rank. For a split pair $(G, T)$ we have $X^*(T) = \mathrm{Hom}(T, \mathbb{G}_m)$ over $k$, and every representation of $T$ over $k$ is a direct sum of weight spaces. Mathlib has the groups `Matrix.GeneralLinearGroup` and `Matrix.SpecialLinearGroup` as groups of matrices over a commutative ring, but it does not define reductive groups or their maximal tori.

**Example 3.1.12 (split and nonsplit groups).** The diagonal torus $T_n$ of $GL_n$ is split, so $GL_n$ is split of rank $n$ and semisimple rank $n - 1$. The groups $SL_n$, $Sp_{2n}$ and $SO_n$ for the forms of Section 3.7 are split. Let $q = x^2 + y^2 + z^2$ over $\mathbb{R}$ and $G = SO(q)$. Then $G(\mathbb{R})$ is compact, and $G$ is not split. Indeed, let $\lambda : \mathbb{G}_m \to G$ be a nontrivial cocharacter over $\mathbb{R}$. Then $\lambda(\mathbb{G}_m)$ is a split torus of $GL_3$, so $\lambda$ is diagonal in some basis of $\mathbb{R}^3$, with entries $t^{m_1}, t^{m_2}, t^{m_3}$, not all $m_i$ zero. Some entry of $\lambda(t)$ is then unbounded for $t \in \mathbb{R}^\times$, and this contradicts the compactness of $G(\mathbb{R})$. So $G$ has no nontrivial split torus. Its maximal tori are the groups of rotations about a fixed axis, and they are tori of dimension 1 with $T(\mathbb{R})$ a circle. Section 3.8 treats such groups as forms of a split group.
