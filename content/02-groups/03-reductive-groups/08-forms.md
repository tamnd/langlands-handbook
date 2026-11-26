---
title: Forms and quasi-split groups
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Forms and quasi-split groups

A reductive group over $k$ need not be split, but it becomes split over $k_s$. This section describes the groups over $k$ that become isomorphic to a given split group over $k_s$, by Galois cohomology. It defines quasi-split groups and the action of $\Gamma$ on the based root datum, and it shows that this action classifies the quasi-split groups. This action and the dual group of Chapter 5 together give the L-group. The examples to keep in mind are the unitary groups and the group of norm one elements of a quaternion algebra. We follow [Bor79], Section 1, and [Spr98], Chapter 16, and for Galois cohomology Serre, *Galois Cohomology* (Springer, 1997), Chapter III, Section 1.

### Forms

**Definition 3.8.1 (forms and inner forms).** Let $G$ be a reductive group over $k$. A *form* of $G$ is a reductive group $G'$ over $k$ with an isomorphism $\varphi \colon G_{k_s} \to G'_{k_s}$. For $\sigma \in \Gamma$, put $c_\sigma = \varphi^{-1} \circ {}^\sigma\varphi \in \mathrm{Aut}(G_{k_s})$. The form is *inner* if $\varphi$ can be chosen so that each $c_\sigma$ is an inner automorphism.

The map $\sigma \mapsto c_\sigma$ is a continuous 1-cocycle of $\Gamma$ with values in $\mathrm{Aut}(G_{k_s})$, that is, $c_{\sigma\tau} = c_\sigma \cdot {}^\sigma c_\tau$. A different choice of $\varphi$ changes $c$ to a cohomologous cocycle.

**Theorem 3.8.2 (forms and Galois cohomology).** The map $(G', \varphi) \mapsto [c]$ is a bijection from the set of isomorphism classes of forms of $G$ onto the pointed set $H^1(\Gamma, \mathrm{Aut}(G_{k_s}))$. The inner forms correspond to the image of $H^1(\Gamma, G_{ad}(k_s))$.

Lean: not stated yet

*Proof sketch.* Injectivity is a direct check: if two forms give cohomologous cocycles, the isomorphism $\varphi' \circ a \circ \varphi^{-1}$ for a suitable $a$ commutes with the action of $\Gamma$, so it descends to $k$. Surjectivity is Galois descent for affine varieties: a cocycle $c$ defines a twisted action $\sigma \ast x = c_\sigma({}^\sigma x)$ of $\Gamma$ on $G_{k_s}$, and the twisted action comes from a form over $k$. See Serre, *Galois Cohomology*, Chapter III, Section 1. $\square$

For a split group $G$, Theorem 3.6.7 gives $\mathrm{Aut}(G_{k_s}) = G_{ad}(k_s) \rtimes \mathrm{Aut}(\Psi_0)$, and $\Gamma$ acts trivially on $\mathrm{Aut}(\Psi_0)$. The map $H^1(\Gamma, \mathrm{Aut}(G_{k_s})) \to H^1(\Gamma, \mathrm{Aut}(\Psi_0)) = \mathrm{Hom}(\Gamma, \mathrm{Aut}(\Psi_0))/\text{conjugation}$ sends each form to the outer part of its cocycle.

**Example 3.8.3 (forms of tori).** The automorphism group of $\mathbb{G}_m^r$ is $GL_r(\mathbb{Z})$, with trivial action of $\Gamma$. So the forms of $\mathbb{G}_m^r$ are classified by the conjugacy classes of continuous homomorphisms $\Gamma \to GL_r(\mathbb{Z})$, that is, by the lattices of rank $r$ with a continuous action of $\Gamma$. This is the anti-equivalence $T \mapsto X^*(T)$ of Chapter 1. Let $K/k$ be a separable quadratic extension and $\tau$ its nontrivial automorphism. The lattice $\mathbb{Z}$ on which $\Gamma$ acts through $\mathrm{Gal}(K/k)$, with $\tau$ acting by $-1$, is the character group of the norm one torus $T = \ker(N \colon R_{K/k}\mathbb{G}_m \to \mathbb{G}_m)$. For $k = \mathbb{R}$ and $K = \mathbb{C}$, this torus is $SO_2 = \{(a, b) : a^2 + b^2 = 1\}$, and $SO_2(\mathbb{R})$ is the circle group. The split form $\mathbb{G}_m$ has $\mathbb{G}_m(\mathbb{R}) = \mathbb{R}^\times$, which is not compact.

**Example 3.8.4 (the norm one group of a quaternion algebra).** Let $D$ be a quaternion algebra over $k$, that is, a central simple algebra of dimension 4. Then $D \otimes_k k_s \cong M_2(k_s)$. Let $SL_1(D)$ be the group of elements of $D$ of reduced norm 1. The isomorphism $D \otimes_k k_s \cong M_2(k_s)$ gives an isomorphism $SL_1(D)_{k_s} \cong SL_{2, k_s}$, so $SL_1(D)$ is a form of $SL_2$. It is an inner form: by the Skolem-Noether theorem, every automorphism of $M_2(k_s)$ is conjugation by an element of $GL_2(k_s)$, so the cocycle takes values in $PGL_2(k_s)$. For $k = \mathbb{R}$ and $D = \mathbb{H}$, the reduced norm is $a^2 + b^2 + c^2 + d^2$, and $SL_1(\mathbb{H})(\mathbb{R})$ is the group of unit quaternions. It is compact, and it is isomorphic to $SU(2)$.

### Quasi-split groups and the action on the based root datum

**Definition 3.8.5 (quasi-split group).** A reductive group over $k$ is *quasi-split* if it has a Borel subgroup defined over $k$.

A split group is quasi-split by Theorem 3.4.3. A torus is quasi-split, since it is its own Borel subgroup.

**Example 3.8.6 (a group that is not quasi-split).** Let $k$ have characteristic 0, and let $D$ be a quaternion division algebra over $k$. Then $SL_1(D)$ is not quasi-split. Suppose that $B$ is a Borel subgroup defined over $k$. Its unipotent radical $U$ is defined over $k$ and has dimension 1. In characteristic 0 a unipotent group of positive dimension has a nontrivial $k$-point, so there is $u \in U(k) \subset D^\times$ with $u \ne 1$. In $D \otimes_k \bar k \cong M_2(\bar k)$ the element $u$ is unipotent, so $(u - 1)^2 = 0$. Thus $u - 1$ is a nonzero nilpotent element of the division algebra $D$, which is impossible.

Let $G$ be reductive over $k$. It has a maximal torus $T$ defined over $k$ ([Spr98], Chapter 13), and $T$ splits over $k_s$ (Chapter 1), so $(G_{k_s}, T_{k_s})$ is split. Let $\Psi = \Psi(G_{k_s}, T_{k_s})$. The group $\Gamma$ acts on $X = X^*(T)$ by $({}^\sigma\chi)(t) = \sigma(\chi(\sigma^{-1} t))$, and this action preserves $R$ and $R^\vee$. Fix a positive system $R^+$ with base $\Delta$. For $\sigma \in \Gamma$ the set ${}^\sigma R^+$ is again a positive system, so there is a unique $w_\sigma \in W$ with $w_\sigma({}^\sigma R^+) = R^+$. Put
$$\mu_G(\sigma) = w_\sigma \circ \sigma \colon X \to X.$$
This is the $\ast$*-action* of $\Gamma$ on the based root datum $\Psi_0 = (X, \Delta, X^\vee, \Delta^\vee)$.

**Proposition 3.8.7 (the $\ast$-action).** The map $\mu_G \colon \Gamma \to \mathrm{Aut}(\Psi_0)$ is a continuous homomorphism. Up to the canonical identifications of the based root data for different choices of $T$ and $R^+$, it depends only on $G$. Inner forms have the same $\ast$-action. If $T$ lies in a Borel subgroup $B$ defined over $k$ and $R^+ = R(B)$, then $w_\sigma = 1$ for all $\sigma$, so $\mu_G$ is the Galois action on $X$.

Lean: not stated yet

*Proof sketch.* The action of $\Gamma$ on $X$ normalizes the action of $W$, because $W$ is defined by the roots. So $\sigma \mapsto w_\sigma \sigma$ is a homomorphism to the group of automorphisms of $\Psi$ that preserve $\Delta$. It is continuous because $T$ splits over a finite extension. Independence of choices and the statement about inner forms follow from the fact that inner automorphisms act trivially on $\Psi_0$ (Theorem 3.6.7). For the last statement, if $B$ is defined over $k$, then ${}^\sigma B = B$, so ${}^\sigma R^+ = R^+$. See [Bor79], Section 1. $\square$

**Theorem 3.8.8 (classification of quasi-split groups).** Let $G_0$ be a split reductive group over $k$ with based root datum $\Psi_0$.
1. For each continuous homomorphism $\mu \colon \Gamma \to \mathrm{Aut}(\Psi_0)$ there is a quasi-split form $G_\mu$ of $G_0$ with $\ast$-action $\mu$. Two such groups $G_\mu$ and $G_{\mu'}$ are isomorphic if and only if $\mu$ and $\mu'$ are conjugate under $\mathrm{Aut}(\Psi_0)$.
2. Every form of $G_0$ is an inner form of exactly one quasi-split form $G_\mu$.

Lean: not stated yet

*Proof sketch.* Choose a pinning of $G_0$. By Theorem 3.6.7, $\mathrm{Aut}(\Psi_0)$ is a subgroup of $\mathrm{Aut}(G_0)$ that preserves the pinning, so $\mu$ is a cocycle with values in $\mathrm{Aut}(G_{0, k_s})$. The twisted action of $\Gamma$ preserves the Borel subgroup $B_0$ of the pinning, so $B_0$ descends to a Borel subgroup of the form $G_\mu$ over $k$, and $G_\mu$ is quasi-split. For part 2, a form has an image $[\mu]$ in $H^1(\Gamma, \mathrm{Aut}(\Psi_0))$, and the forms with the same image are the inner forms of $G_\mu$, by the twisting argument of Serre, *Galois Cohomology*, Chapter I, Section 5. For the uniqueness statements see [Spr98], Chapter 16. $\square$

So a quasi-split group is determined by its split form over $k_s$ and its $\ast$-action. A general reductive group is determined by its quasi-split inner form and a class in $H^1(\Gamma, G_{ad}(k_s))$, up to an action of the outer automorphisms.

**Example 3.8.9 (quasi-split unitary groups).** Let $K/k$ be a separable quadratic extension with nontrivial automorphism $\tau$, and let $J$ be the $n \times n$ matrix with entries 1 on the antidiagonal and 0 elsewhere. Let $U_n$ be the group over $k$ with
$$U_n(A) = \{g \in GL_n(K \otimes_k A) : \tau(g)^T J g = J\}$$
for a $k$-algebra $A$. Since $K \otimes_k K \cong K \times K$, the group $U_{n,K}$ is $GL_{n,K}$, and the Galois action becomes $g \mapsto J^{-1} (\tau(g)^T)^{-1} J$. So $U_n$ is a form of $GL_n$, and its cocycle has the outer part $g \mapsto (g^T)^{-1}$. The diagonal matrices $t = \mathrm{diag}(t_1, \dots, t_n)$ in $U_n$ form a maximal torus $T$ over $k$, with $\tau(t_i) t_{n+1-i} = 1$. The twisted action of $\tau$ sends $t$ to $\mathrm{diag}(\tau(t_n)^{-1}, \dots, \tau(t_1)^{-1})$, so $\tau$ acts on $X = \mathbb{Z}^n$ by $e_i \mapsto -e_{n+1-i}$. The upper triangular matrices in $U_n$ form a Borel subgroup over $k$: the map $g \mapsto J^{-1}(\tau(g)^T)^{-1} J$ preserves upper triangular matrices, because conjugation by $J$ exchanges upper and lower triangular matrices. So $U_n$ is quasi-split, and by Proposition 3.8.7 its $\ast$-action is $e_i \mapsto -e_{n+1-i}$. This maps $e_i - e_{i+1}$ to $e_{n-i} - e_{n+1-i}$, so it is the nontrivial automorphism of the diagram $A_{n-1}$ for $n \ge 3$. For $k = \mathbb{R}$, the hermitian form of $J$ has signature $(m, m)$ when $n = 2m$ and $(m+1, m)$ when $n = 2m+1$, so the quasi-split unitary groups over $\mathbb{R}$ are $U(m, m)$ and $U(m+1, m)$. The other groups $U(p, q)$ with $p + q = n$ are inner forms of these.

**Example 3.8.10 (quasi-split even orthogonal groups).** Let $n \ge 2$, let $d \in k^\times$ be a nonsquare, and assume that the characteristic is not 2. Consider the quadratic form
$$q = \sum_{i=1}^{n-1} x_i x_{-i} + x_n^2 - d y^2$$
in $2n$ variables. Over $K = k(\sqrt{d})$, the last two terms become $(x_n - \sqrt d\, y)(x_n + \sqrt d\, y)$, so $q$ is split over $K$ and $SO(q)$ is a form of $SO_{2n}$. The maximal torus is the product of $\mathbb{G}_m^{n-1}$, acting on the planes $\langle e_i, e_{-i} \rangle$, and the norm one torus of $K/k$, acting on the last plane. So $\tau$ acts on $X = \mathbb{Z}^n$ by $e_n \mapsto -e_n$ and fixes $e_1, \dots, e_{n-1}$. The stabilizer of the isotropic flag $\langle e_1 \rangle \subset \dots \subset \langle e_1, \dots, e_{n-1} \rangle$ is a Borel subgroup over $k$, so $SO(q)$ is quasi-split. The $\ast$-action exchanges the simple roots $e_{n-1} - e_n$ and $e_{n-1} + e_n$, which is the nontrivial automorphism of the diagram $D_n$ that fixes the other nodes.

**Theorem 3.8.11 (Lang).** Let $G$ be a connected algebraic group over a finite field $k$. Then $H^1(\Gamma, G(k_s)) = 1$. In particular every reductive group over a finite field is quasi-split, and it has no inner form other than itself.

Lean: not stated yet

The first statement is Lang's theorem, from Lang, "Algebraic groups over finite fields", *American Journal of Mathematics* 78 (1956). The proof shows that the Lang map $g \mapsto g^{-1} F(g)$ is surjective, where $F$ is the Frobenius. For the second statement, the Borel subgroups of $G_{\bar k}$ form a variety $G/B$ over $k$ on which $G$ acts transitively with connected stabilizers, and Lang's theorem gives a $k$-point of this variety. For the last statement, the inner forms of $G$ are classified by $H^1(\Gamma, G_{ad}(k_s))$, which is trivial.

**Example 3.8.12 (forms of $SL_2$ and $SL_n$ over $\mathbb{R}$).** The group $\mathrm{Aut}(\Psi_0)$ is trivial for $SL_2$, so every form of $SL_2$ is inner, and the forms are classified by $H^1(\mathbb{R}, PGL_2)$. This set also classifies the quaternion algebras over $\mathbb{R}$, by the cocycle of Example 3.8.4, and there are two of them, $M_2(\mathbb{R})$ and $\mathbb{H}$. So $SL_2$ has exactly two forms over $\mathbb{R}$: the split group $SL_2$ and the compact group $SL_1(\mathbb{H}) \cong SU(2)$. The second one is not quasi-split, by Example 3.8.6. For $n \ge 3$ the forms of $SL_n$ over $\mathbb{R}$ are $SL_n(\mathbb{R})$, the inner forms $SL_{n/2}(\mathbb{H})$ for $n$ even, and the outer forms $SU(p, q)$ with $p + q = n$, by Cartan's classification of the real simple Lie algebras.

### Toward the L-group

Chapter 5 exchanges the based root datum $\Psi_0$ with its dual $\Psi_0^\vee$. An automorphism of $\Psi_0$ is also an automorphism of $\Psi_0^\vee$, so $\mu_G$ gives an action of $\Gamma$ on the dual group $G^\vee$ that preserves a pinning, and the L-group is ${}^L G = G^\vee \rtimes \Gamma$. Inner forms have the same $\ast$-action, so they have the same L-group. For example $SL_2$ and $SL_1(D)$ both have the L-group $PGL_2(\mathbb{C}) \times \Gamma$, which is one reason why their representations are related, as in the Jacquet-Langlands correspondence.
