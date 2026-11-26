---
title: Subgroups, homomorphisms and quotients
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Subgroups, homomorphisms and quotients

This section defines closed subgroups, kernels and quotient maps, proves that every algebraic group is a closed subgroup of some $GL_n$, and states the existence of quotients. It ends with the identity component. The quotient $G/N$ is the one construction of the theory whose proof is long, and we only state it. The example to keep in mind is the exact sequence $1 \to \mu_n \to SL_n \to PGL_n \to 1$. Its map $SL_n \to PGL_n$ is a quotient map, but in general it is not surjective on $k$-points. We follow [Mil17], Chapters 4 and 5, and [Spr98], Chapters 2 and 5.

### Closed subgroups

**Definition 1.2.1 (closed subgroup).** A *closed subgroup* of an affine group $G$ is a subfunctor $H \subset G$ such that each $H(R)$ is a subgroup of $G(R)$, and such that $H$ is represented by a quotient $\mathcal{O}(G)/I$, that is, $H(R) = \{x \in G(R) : a(x) = 0 \text{ for all } a \in I\}$. The ideal $I$ is then a Hopf ideal, and conversely each Hopf ideal defines a closed subgroup. A homomorphism $f : H \to G$ is a *closed embedding* if $f^* : \mathcal{O}(G) \to \mathcal{O}(H)$ is surjective. Then $f$ is an isomorphism of $H$ onto a closed subgroup of $G$.

Milne calls a closed subgroup an *algebraic subgroup*. A closed subgroup of an algebraic group is algebraic, because a quotient of a finitely generated algebra is finitely generated.

**Example 1.2.2 (subgroups of $GL_n$).** The following are closed subgroups of $GL_n$, given by their points in a $k$-algebra $R$:
1. the *diagonal torus* $D_n$ of the invertible diagonal matrices, with $\mathcal{O}(D_n) = \mathcal{O}(GL_n)/(x_{ij} : i \ne j) = k[x_{11}^{\pm 1}, \dots, x_{nn}^{\pm 1}]$, so that $D_n \cong \mathbb{G}_m^n$;
2. the *upper triangular group* $B_n$, defined by $x_{ij} = 0$ for $i > j$;
3. the *upper unitriangular group* $U_n$, defined by $x_{ij} = 0$ for $i > j$ and $x_{ii} = 1$;
4. $SL_n$, and the groups $G_J$ of Example 1.1.10.

For instance, $U_2 \cong \mathbb{G}_a$ by $t \mapsto \left(\begin{smallmatrix} 1 & t \\ 0 & 1 \end{smallmatrix}\right)$. The group $B_n$ is the semidirect product $D_n \ltimes U_n$: each $b \in B_n(R)$ is uniquely $b = d u$ with $d$ its diagonal and $u = d^{-1} b \in U_n(R)$, and $U_n$ is normal in $B_n$ because it is the kernel of the homomorphism $B_n \to D_n$ that keeps the diagonal.

**Theorem 1.2.3 (algebraic groups are linear).** Every algebraic group $G$ over $k$ has a closed embedding into $GL_n$ for some $n$.

Lean: not stated yet

*Proof.* Let $A = \mathcal{O}(G)$ with the regular representation of Example 1.1.17. Choose generators of the algebra $A$. By Theorem 1.1.18, they lie in a finite-dimensional subspace $W$ with $\Delta(W) \subset W \otimes A$. Choose a basis $w_1, \dots, w_n$ of $W$ and write
$$\Delta(w_j) = \sum_{i} w_i \otimes a_{ij}, \qquad a_{ij} \in A.$$
The counit identity $(\varepsilon \otimes \mathrm{id}) \circ \Delta = \mathrm{id}$ gives $w_j = \sum_i \varepsilon(w_i) a_{ij}$. So the $a_{ij}$ generate $A$ as an algebra. The identity $(\mathrm{id} \otimes \varepsilon) \circ \Delta = \mathrm{id}$ gives $\varepsilon(a_{ij}) = \delta_{ij}$. We compute $(\Delta \otimes \mathrm{id}) \Delta(w_j)$ in two ways:
$$\sum_{i, l} w_l \otimes a_{li} \otimes a_{ij} = \sum_l w_l \otimes \Delta(a_{lj}).$$
The $w_l$ are linearly independent, so $\Delta(a_{lj}) = \sum_i a_{li} \otimes a_{ij}$. The antipode identity gives $\sum_i S(a_{li}) a_{ij} = \varepsilon(a_{lj}) = \delta_{lj}$. Thus the matrix $(a_{ij})$ is invertible over $A$, and $\det(a_{ij})$ is a unit. The homomorphism $\mathcal{O}(GL_n) \to A$ with $x_{ij} \mapsto a_{ij}$ is therefore defined, it is surjective, and it commutes with the comultiplications. It is $f^*$ for a closed embedding $f : G \to GL_n$. On points, $f(g)$ is the matrix of $g$ acting on $W \otimes R$ in the basis $(w_i)$. $\square$

### Kernels and quotient maps

**Definition 1.2.4 (kernel).** The *kernel* of a homomorphism $f : G \to H$ is the functor $\ker(f)(R) = \ker(f_R : G(R) \to H(R))$. It is the closed subgroup of $G$ represented by $\mathcal{O}(G) / f^*(\mathfrak{m}_H) \mathcal{O}(G)$, where $\mathfrak{m}_H = \ker(\varepsilon_H)$. A closed subgroup $N$ of $G$ is *normal* if each $N(R)$ is normal in $G(R)$.

Indeed $x \in G(R)$ lies in the kernel if and only if $b(f(x)) = b(e)$ for all $b \in \mathcal{O}(H)$, that is, if and only if $x$ kills $f^*(b) - \varepsilon(b)$ for all $b$, and these elements generate $f^*(\mathfrak{m}_H) \mathcal{O}(G)$. A kernel is normal. The kernel of $\det : GL_n \to \mathbb{G}_m$ is $SL_n$. The kernel of the $n$-th power map $\mathbb{G}_m \to \mathbb{G}_m$ is $\mu_n$. In characteristic $p$, the second map with $n = p$ is injective on the points in every field, but its kernel is not trivial.

**Definition 1.2.5 (quotient map).** A homomorphism $f : G \to H$ of algebraic groups is a *quotient map* if $f^* : \mathcal{O}(H) \to \mathcal{O}(G)$ is injective.

By a theorem on Hopf algebras, $\mathcal{O}(G)$ is then a faithfully flat $\mathcal{O}(H)$-module ([Mil17], Chapter 5). The consequence that we use is this: for each $k$-algebra $R$ and each $h \in H(R)$, there is a faithfully flat $R$-algebra $R'$ such that the image of $h$ in $H(R')$ lifts to $G(R')$. In particular $G(\bar k) \to H(\bar k)$ is surjective. So a quotient map is surjective "locally", and not on the points of each algebra.

**Example 1.2.6 (two quotient maps).** The determinant $GL_n \to \mathbb{G}_m$ is a quotient map, because $\det$ is transcendental over $k$ in $\mathcal{O}(GL_n)$, and it is surjective on $R$-points for every $R$. The $n$-th power map $f : \mathbb{G}_m \to \mathbb{G}_m$ has $f^*(t) = t^n$, so it is a quotient map. On $\mathbb{Q}$-points it is $\mathbb{Q}^\times \to \mathbb{Q}^\times$, $x \mapsto x^n$, which is far from surjective. But each $a \in R^\times$ has an $n$-th root in $R' = R[s]/(s^n - a)$, which is free of rank $n$ over $R$ and thus faithfully flat.

**Theorem 1.2.7 (quotients by normal subgroups).** Let $N$ be a normal closed subgroup of an algebraic group $G$. There is an algebraic group $G/N$ and a quotient map $q : G \to G/N$ with kernel $N$. Each homomorphism $f : G \to H$ with $N \subset \ker f$ factors uniquely as $f = \bar f \circ q$. If $N = \ker f$, then $\bar f$ is a closed embedding, so $G/\ker(f)$ is isomorphic to the image of $f$, a closed subgroup of $H$. If $G$ is smooth, so is $G/N$.

Lean: not stated yet

*Outline of the proof.* By Chevalley's theorem below there is a representation $V$ of $G$ and a line in $V$ whose stabilizer is $N$. Since $N$ is normal one can replace $V$ by a representation in which $N$ is the kernel of the action, and the image of $G$ in $GL_V$ is then the quotient. The subalgebra of $\mathcal{O}(G)$ of the functions that are invariant under translation by $N$ is then $\mathcal{O}(G/N)$. The details are in [Mil17], Chapter 5, and for smooth groups over an algebraically closed field in [Spr98], Chapter 5. $\square$

**Theorem 1.2.8 (Chevalley).** Let $H$ be a closed subgroup of an algebraic group $G$. There is a finite-dimensional representation $V$ of $G$ and a line $L \subset V$ such that $H$ is the stabilizer of $L$: for each $R$, $H(R)$ is the set of $g \in G(R)$ with $g (L \otimes R) = L \otimes R$.

Lean: not stated yet

*Proof sketch.* Let $I \subset A = \mathcal{O}(G)$ be the ideal of $H$. Choose a finite-dimensional subrepresentation $W$ of the regular representation that contains a set of generators of $I$, and let $W' = W \cap I$, of dimension $d$. One shows that $g \in G(R)$ lies in $H(R)$ if and only if $g$ maps $W' \otimes R$ to itself. The reason is that $H$ is the stabilizer of $I$ in the regular representation, since $H(R)$ is the set of $g$ with $a(xg) \in I_R$ for all $a \in I$, and $W'$ generates $I$. Then $V = \Lambda^d W$ and $L = \Lambda^d W'$ have the required property, because a subspace of dimension $d$ is determined by its line in $\Lambda^d$. See [Mil17], Chapter 4. $\square$

For a closed subgroup $H$ that is not normal, the quotient $G/H$ still exists, but it is not an affine group. It is a quasi-projective scheme with an action of $G$, and $G \to G/H$ is the orbit map of the line $L$ of Theorem 1.2.8 in the projective space of $V$. For smooth groups over an algebraically closed field, $G/H$ is the orbit of $L$, a quasi-projective variety, and $\dim G/H = \dim G - \dim H$ ([Spr98], Chapter 5). Section 1.6 uses the case where $H$ is a Borel subgroup and $G/H$ is projective.

**Example 1.2.9 (the projective linear group).** The centre of $GL_n$ contains the scalar matrices, a closed subgroup isomorphic to $\mathbb{G}_m$. Its quotient is $PGL_n = GL_n / \mathbb{G}_m$. Its coordinate ring is the subring of the elements of degree $0$ in $\mathcal{O}(GL_n) = k[x_{ij}][1/\det]$, where $x_{ij}$ has degree $1$ and $\det$ has degree $n$. These are the functions invariant under scalars. For $n = 2$ it is generated by the functions $x_{ij} x_{lm} / \det$. The composite $SL_n \to GL_n \to PGL_n$ is a quotient map with kernel $\mu_n$, embedded as the scalars, so there is an exact sequence
$$1 \to \mu_n \to SL_n \to PGL_n \to 1.$$
On $k$-points one has $PGL_n(k) = GL_n(k)/k^\times$ (this uses Hilbert's Theorem 90). The image of $SL_n(k)$ is the set of classes of matrices whose determinant is an $n$-th power. Thus the sequence of points is
$$1 \to \mu_n(k) \to SL_n(k) \to PGL_n(k) \xrightarrow{\ \det\ } k^\times / k^{\times n} \to 1,$$
and it is exact. For $k = \mathbb{R}$ and $n = 2$ the last group is $\{\pm 1\}$. In characteristic $p$ with $n = p$, the map $SL_p(\bar k) \to PGL_p(\bar k)$ is a bijection, but $SL_p \to PGL_p$ is not an isomorphism, since its kernel is $\mu_p$.

**Remark 1.2.10 (the points of a quotient).** The last group in the sequence of Example 1.2.9 is the Galois cohomology group $H^1(k, \mu_n)$ of Kummer theory. In general an exact sequence $1 \to N \to G \to Q \to 1$ of smooth algebraic groups gives an exact sequence of pointed sets
$$1 \to N(k) \to G(k) \to Q(k) \to H^1(k, N) \to H^1(k, G),$$
and the failure of surjectivity on $k$-points is measured by Galois cohomology. Volume 9 meets such sequences in the theory of endoscopy, where the difference between $SL_2(F)$ and the image of $GL_2(F)$ in $PGL_2(F)$ gives the L-packets of $SL_2$.

### The identity component

From now on in this subsection, $k$ is algebraically closed and $G$ is smooth. Then $G(k)$ is an affine variety, and we use its Zariski topology.

**Proposition 1.2.11 (the identity component).** Let $G^\circ$ be the irreducible component of $G(k)$ that contains $e$. Then $G^\circ$ is the only irreducible component of $G(k)$ through $e$. It is a closed normal subgroup of finite index, and its cosets are the irreducible components and the connected components of $G(k)$.

Lean: not stated yet

*Proof.* Let $X_1, \dots, X_r$ be the irreducible components of $G(k)$ that contain $e$. The image of $X_1 \times \dots \times X_r$ under the multiplication map is irreducible, and so is its closure $Y$. Since $e \in X_j$ for each $j$, the set $Y$ contains each $X_i$. Each $X_i$ is a maximal irreducible closed set, so $X_i = Y$ for all $i$, and $r = 1$. Write $G^\circ = X_1$. The same argument shows that the closure of $G^\circ \cdot G^\circ$ is $G^\circ$, so $G^\circ$ is closed under products. The set $(G^\circ)^{-1}$ is an irreducible component through $e$, so it equals $G^\circ$. For $x \in G(k)$, the set $x G^\circ x^{-1}$ is an irreducible component through $e$, so it equals $G^\circ$. Thus $G^\circ$ is a normal subgroup. Translation by $x$ is an automorphism of the variety, so $x G^\circ$ is the only irreducible component through $x$. Thus the irreducible components are the cosets of $G^\circ$. They are disjoint, closed and finite in number, because $G(k)$ is a noetherian space. So they are also open, and they are the connected components. $\square$

The group $G^\circ$ is a smooth closed subgroup of $G$, and $G$ is *connected* if $G = G^\circ$. Over any field, each algebraic group has an identity component $G^\circ$, a normal closed subgroup such that $G / G^\circ$ is a finite étale group ([Mil17], Chapters 1 and 5). It commutes with base change.

**Proposition 1.2.12 (groups generated by connected varieties).** Let $(X_i)_{i \in I}$ be a family of irreducible varieties with morphisms $f_i : X_i \to G(k)$ such that $e \in f_i(X_i)$ for each $i$. Then the subgroup generated by the sets $f_i(X_i)$ is closed and connected.

Lean: not stated yet

*Proof sketch.* One may add the maps $x \mapsto f_i(x)^{-1}$ to the family. For each finite sequence $\underline{i} = (i_1, \dots, i_m)$, the closure $Y_{\underline{i}}$ of $f_{i_1}(X_{i_1}) \cdots f_{i_m}(X_{i_m})$ is irreducible and contains $e$. Choose $\underline{i}$ with $\dim Y_{\underline{i}}$ maximal, and write $Y = Y_{\underline{i}}$ and $U = f_{i_1}(X_{i_1}) \cdots f_{i_m}(X_{i_m})$. For each $\underline{j}$, the closure of $U \cdot f_{j_1}(X_{j_1}) \cdots f_{j_l}(X_{j_l})$ is irreducible, contains $Y$ and has the same dimension, so it equals $Y$. Thus $Y$ is stable under products and under inverses, and it is a closed subgroup that contains all the sets $f_i(X_i)$. The set $U$ is constructible and dense in $Y$, so it contains a dense open subset $V$ of $Y$. For $y \in Y$ the sets $V$ and $y V^{-1}$ are dense open, so they meet, and $y \in V V \subset U U$. Thus $Y = UU$ lies in the subgroup generated by the $f_i(X_i)$, and it equals that subgroup. See [Spr98], Chapter 2. $\square$

**Example 1.2.13 (connected groups).** The group $GL_n(k)$ is an open subset of the affine space of matrices, so it is irreducible and $GL_n$ is connected. The group $SL_n(k)$ is generated by the elementary matrices $1 + t E_{ij}$ with $i \ne j$ and $t \in k$, by row reduction. Each family $t \mapsto 1 + t E_{ij}$ is the image of $\mathbb{G}_a$, so $SL_n$ is connected by Proposition 1.2.12. The tori $D_n$, the groups $B_n$ and $U_n$, and $PGL_n$ are connected, the last one as an image of $GL_n$. Assume that the characteristic is not $2$ and that $q$ is a nondegenerate quadratic form in $n$ variables. Then $\det$ maps $O(q)$ onto $\mu_2 = \{\pm 1\}$, since a reflection has determinant $-1$. Thus $O(q)$ is not connected. Its identity component is $SO(q)$ ([Spr98], Chapter 2). The group $\mu_n$ with $n$ prime to the characteristic is the constant group $\mathbb{Z}/n\mathbb{Z}$, with $n$ components.

The real Lie group $PGL_2(\mathbb{R})$ has two connected components, the classes of the matrices with positive and with negative determinant. The algebraic group $PGL_2$ over $\mathbb{R}$ is connected. The two notions of connectedness differ, and the algebraic one is the one that matters for the structure theory.
