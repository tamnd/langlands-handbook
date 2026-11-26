---
title: The Lie algebra of an algebraic group
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## The Lie algebra of an algebraic group

This section defines Lie algebras and the Lie algebra of an affine algebraic group. The Lie algebra of $G$ is the kernel of the map $G(k[\varepsilon]) \to G(k)$, where $k[\varepsilon]$ is the ring of dual numbers, and its bracket comes from the adjoint representation. We compute the Lie algebras of $GL_n$, $SL_n$, $PGL_n$, $Sp_{2n}$, $O_n$, $\mathbb{G}_m$, $\mathbb{G}_a$ and $\mu_n$, and we prove that in characteristic 0 the Lie algebra determines the connected subgroups. The example to keep in mind is $GL_n$, with the Lie algebra $\mathfrak{gl}_n$ of all matrices and the bracket $XY - YX$. We follow [Mil17], Chapter 10, and [Spr98], Chapter 4.

### Lie algebras

In this section $k$ is a field.

**Definition 2.1.1 (Lie algebra).** A *Lie algebra* over $k$ is a vector space $\mathfrak{g}$ over $k$ with a bilinear map $[\cdot, \cdot] : \mathfrak{g} \times \mathfrak{g} \to \mathfrak{g}$, the *bracket*, with these properties:
1. $[x, x] = 0$ for all $x \in \mathfrak{g}$;
2. $[x, [y, z]] + [y, [z, x]] + [z, [x, y]] = 0$ for all $x, y, z \in \mathfrak{g}$ (the *Jacobi identity*).

The first property gives $[x, y] = -[y, x]$, if we expand $[x + y, x + y] = 0$. The Lie algebra is *abelian* if all brackets are 0. A *homomorphism* of Lie algebras is a linear map $\varphi$ with $\varphi([x, y]) = [\varphi(x), \varphi(y)]$. A *subalgebra* is a subspace that is closed under the bracket. An *ideal* is a subspace $\mathfrak{a}$ with $[\mathfrak{g}, \mathfrak{a}] \subset \mathfrak{a}$. The quotient $\mathfrak{g} / \mathfrak{a}$ by an ideal is a Lie algebra, and the kernel of a homomorphism is an ideal. The *center* of $\mathfrak{g}$ is the ideal $Z(\mathfrak{g}) = \{x : [x, \mathfrak{g}] = 0\}$.

Lean: `LieRing` and `LieAlgebra`, from Mathlib, with `LieIdeal` and `LieSubalgebra`

All Lie algebras of this chapter are finite dimensional.

**Example 2.1.2 (the linear Lie algebras).** Let $A$ be an associative $k$-algebra. Then $[x, y] = xy - yx$ is a Lie bracket on $A$. The Jacobi identity follows when we expand the nine terms. For $A = \mathrm{End}(V)$ with $V$ a vector space, we write $\mathfrak{gl}(V)$ for this Lie algebra, and $\mathfrak{gl}_n$ for $\mathfrak{gl}(k^n)$. The subalgebras of $\mathfrak{gl}(V)$ are the *linear Lie algebras*. These are the main examples.
1. The *special linear algebra* $\mathfrak{sl}_n = \{X \in \mathfrak{gl}_n : \mathrm{tr}\, X = 0\}$. It is a subalgebra, because $\mathrm{tr}(XY - YX) = 0$ for all $X, Y$. Its dimension is $n^2 - 1$.
2. Let $J \in GL_n(k)$. The set $\{X : X^t J + J X = 0\}$ is a subalgebra of $\mathfrak{gl}_n$. For $J = \begin{pmatrix} 0 & I_n \\ -I_n & 0 \end{pmatrix}$ it is the *symplectic algebra* $\mathfrak{sp}_{2n}$, of dimension $n(2n+1)$. For $J = I_n$ it is the *orthogonal algebra* $\mathfrak{so}_n$ of skew-symmetric matrices, of dimension $n(n-1)/2$.
3. The upper triangular matrices $\mathfrak{b}_n$ and the strictly upper triangular matrices $\mathfrak{n}_n$ are subalgebras of $\mathfrak{gl}_n$.

Lean: `LieAlgebra.SpecialLinear.sl`, `LieAlgebra.Symplectic.sp` and `LieAlgebra.Orthogonal.so`, from Mathlib

**Definition 2.1.3 (representations and the adjoint representation).** A *representation* of $\mathfrak{g}$ on a vector space $V$ is a homomorphism $\rho : \mathfrak{g} \to \mathfrak{gl}(V)$. We also say that $V$ is a $\mathfrak{g}$-*module*, and we write $x v$ for $\rho(x)(v)$. A *derivation* of $\mathfrak{g}$ is a linear map $D : \mathfrak{g} \to \mathfrak{g}$ with $D[y, z] = [Dy, z] + [y, Dz]$. For $x \in \mathfrak{g}$, the map $\mathrm{ad}\, x : y \mapsto [x, y]$ is a derivation, and $\mathrm{ad} : \mathfrak{g} \to \mathfrak{gl}(\mathfrak{g})$ is a representation, the *adjoint representation*. Both statements are forms of the Jacobi identity. The kernel of $\mathrm{ad}$ is the center $Z(\mathfrak{g})$.

Lean: `LieModule` and `LieAlgebra.ad`, from Mathlib

**Example 2.1.4 (the Lie algebra $\mathfrak{sl}_2$).** The matrices
$$e = \begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix}, \qquad f = \begin{pmatrix} 0 & 0 \\ 1 & 0 \end{pmatrix}, \qquad h = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}$$
form a basis of $\mathfrak{sl}_2$, and
$$[h, e] = 2e, \qquad [h, f] = -2f, \qquad [e, f] = h.$$
These three relations determine the bracket. A triple $(e, f, h)$ of elements of a Lie algebra with these relations is an $\mathfrak{sl}_2$-*triple*. In the basis $(e, h, f)$ the matrix of $\mathrm{ad}\, h$ is $\mathrm{diag}(2, 0, -2)$.

Lean: `IsSl2Triple`, from Mathlib

### The Lie algebra of an algebraic group

Let $G$ be an affine algebraic group over $k$, with coordinate ring $\mathcal{O}(G)$, as in Chapter 1. For a $k$-algebra $R$, the group $G(R)$ is the group of $k$-algebra homomorphisms $\mathcal{O}(G) \to R$. Let $k[\varepsilon] = k[t]/(t^2)$ be the ring of *dual numbers*, where $\varepsilon$ is the class of $t$. The homomorphism $k[\varepsilon] \to k$ with $\varepsilon \mapsto 0$ gives a homomorphism of groups $\pi : G(k[\varepsilon]) \to G(k)$.

**Definition 2.1.5 (the Lie algebra of $G$).** The *Lie algebra* of $G$ is the group
$$\mathrm{Lie}(G) = \ker\big(\pi : G(k[\varepsilon]) \to G(k)\big).$$
We also write $\mathfrak{g}$ for $\mathrm{Lie}(G)$.

Lean: not stated yet

The group $\mathrm{Lie}(G)$ is a vector space in a natural way. An element of $G(k[\varepsilon])$ in the kernel of $\pi$ is a homomorphism $\varphi : \mathcal{O}(G) \to k[\varepsilon]$ of the form $\varphi(f) = f(1) + \varepsilon D(f)$, where $f(1)$ is the value of $f$ at the identity and $D : \mathcal{O}(G) \to k$ is linear. The map $\varphi$ is multiplicative if and only if
$$D(fg) = f(1) D(g) + g(1) D(f) \quad \text{for all } f, g \in \mathcal{O}(G),$$
because $\varepsilon^2 = 0$. Such a $D$ is a *derivation at the identity*. Thus $\mathrm{Lie}(G)$ is the vector space of derivations $\mathcal{O}(G) \to k$ at the identity. Let $I = \{f : f(1) = 0\}$ be the ideal of the identity. A derivation at the identity vanishes on the constants and on $I^2$, and each linear form on $I / I^2$ extends to a unique derivation. Thus $\mathrm{Lie}(G) = (I / I^2)^*$, the tangent space of $G$ at 1. The group law of $\mathrm{Lie}(G) \subset G(k[\varepsilon])$ is the addition of derivations, and $c \in k$ acts through the endomorphism $\varepsilon \mapsto c \varepsilon$ of $k[\varepsilon]$. See [Mil17], Chapter 10, for the details.

A homomorphism $u : G \to H$ of algebraic groups maps $\ker(G(k[\varepsilon]) \to G(k))$ into $\ker(H(k[\varepsilon]) \to H(k))$. This gives a linear map $\mathrm{Lie}(u) : \mathrm{Lie}(G) \to \mathrm{Lie}(H)$, the *differential* of $u$. On derivations it is $D \mapsto D \circ u^*$, where $u^* : \mathcal{O}(H) \to \mathcal{O}(G)$ is the comorphism.

**Example 2.1.6 (the general linear group).** An element of $GL_n(k[\varepsilon])$ that maps to $1$ is a matrix $1 + \varepsilon X$ with $X \in M_n(k)$. Each such matrix is invertible, with inverse $1 - \varepsilon X$. Thus $\mathrm{Lie}(GL_n) = \{1 + \varepsilon X\} \cong M_n(k)$, and the group law is $(1 + \varepsilon X)(1 + \varepsilon Y) = 1 + \varepsilon(X + Y)$. More generally $\mathrm{Lie}(GL_V) = \mathrm{End}(V)$ for a finite dimensional vector space $V$. For $n = 1$ this is $\mathrm{Lie}(\mathbb{G}_m) = k$. For the additive group, $\mathbb{G}_a(k[\varepsilon]) = k[\varepsilon]$ and $\mathrm{Lie}(\mathbb{G}_a) = k \varepsilon \cong k$.

**Example 2.1.7 (subgroups of $GL_n$).** Let $G \subset GL_n$ be a closed subgroup. Then $\mathrm{Lie}(G) \subset \mathrm{Lie}(GL_n) = M_n(k)$ is the set of $X$ with $1 + \varepsilon X \in G(k[\varepsilon])$. We compute it from the equations of $G$.
1. For $SL_n$: $\det(1 + \varepsilon X) = 1 + \varepsilon \, \mathrm{tr}(X)$, because all products of two entries of $\varepsilon X$ vanish. Thus $\mathrm{Lie}(SL_n) = \mathfrak{sl}_n$.
2. For the group $G_J = \{g : g^t J g = J\}$ of a matrix $J \in GL_n(k)$:
$$(1 + \varepsilon X)^t J (1 + \varepsilon X) = J + \varepsilon(X^t J + J X).$$
Thus $\mathrm{Lie}(G_J) = \{X : X^t J + JX = 0\}$. This gives $\mathrm{Lie}(Sp_{2n}) = \mathfrak{sp}_{2n}$ and $\mathrm{Lie}(O_n) = \mathfrak{so}_n$.
3. For $\mu_m = \{x \in \mathbb{G}_m : x^m = 1\}$: $(1 + \varepsilon a)^m = 1 + m \varepsilon a$. Thus $\mathrm{Lie}(\mu_m) = 0$ if the characteristic $p$ of $k$ does not divide $m$, and $\mathrm{Lie}(\mu_m) = k$ if $p \mid m$.
4. For the diagonal torus $T_n \cong \mathbb{G}_m^n$, the Lie algebra is the space of diagonal matrices. For the upper triangular group $B_n$ it is $\mathfrak{b}_n$, and for the group $U_n$ of upper triangular unipotent matrices it is $\mathfrak{n}_n$.

### The adjoint representation and the bracket

The definition of the bracket needs a little more than Definition 2.1.5. For each $k$-algebra $R$, let $R[\varepsilon] = R \otimes_k k[\varepsilon]$. The kernel of $G(R[\varepsilon]) \to G(R)$ is $\mathrm{Lie}(G) \otimes_k R$, naturally in $R$ ([Mil17], Chapter 10). The group $G(R)$ acts on this kernel by conjugation, where we view $G(R)$ as a subgroup of $G(R[\varepsilon])$ through $R \subset R[\varepsilon]$. The action is $R$-linear and natural in $R$. Thus it is a homomorphism of algebraic groups
$$\mathrm{Ad} : G \to GL_{\mathrm{Lie}(G)},$$
the *adjoint representation* of $G$.

**Definition 2.1.8 (the bracket).** The *bracket* of $\mathrm{Lie}(G)$ is $[X, Y] = \mathrm{ad}(X)(Y)$, where
$$\mathrm{ad} = \mathrm{Lie}(\mathrm{Ad}) : \mathrm{Lie}(G) \to \mathrm{Lie}(GL_{\mathrm{Lie}(G)}) = \mathrm{End}(\mathrm{Lie}(G))$$
is the differential of the adjoint representation.

Lean: not stated yet

**Theorem 2.1.9 (the Lie algebra of an algebraic group).** Let $G$ be an affine algebraic group over $k$.
1. For $G = GL_V$, the bracket of Definition 2.1.8 is $[X, Y] = XY - YX$.
2. For a homomorphism $u : G \to H$, the differential $\mathrm{Lie}(u)$ preserves the brackets.
3. The bracket makes $\mathrm{Lie}(G)$ a Lie algebra. If $G$ is a closed subgroup of $GL_V$, then $\mathrm{Lie}(G)$ is a subalgebra of $\mathfrak{gl}(V)$.

Lean: not stated yet

*Proof.* For part 1, let $g \in GL_V(R)$ and $Y \in \mathrm{End}(V) \otimes R$. Then $g (1 + \varepsilon Y) g^{-1} = 1 + \varepsilon\, g Y g^{-1}$, so $\mathrm{Ad}(g) Y = g Y g^{-1}$. To differentiate, take $R = k[\varepsilon']$ and $g = 1 + \varepsilon' X$. Then
$$\mathrm{Ad}(1 + \varepsilon' X) Y = (1 + \varepsilon' X) Y (1 - \varepsilon' X) = Y + \varepsilon'(XY - YX).$$
The element $\mathrm{Ad}(1 + \varepsilon' X) = 1 + \varepsilon' (\mathrm{ad}\, X)$ of $GL(\mathrm{End}(V))(k[\varepsilon'])$ thus has $\mathrm{ad}(X)(Y) = XY - YX$.

For part 2, the map $u$ commutes with conjugation: $\mathrm{Lie}(u)(\mathrm{Ad}(g) Y) = \mathrm{Ad}(u(g)) \, \mathrm{Lie}(u)(Y)$ for $g \in G(R)$. Take $R = k[\varepsilon']$ and $g = 1 + \varepsilon' X$ with $X \in \mathrm{Lie}(G)$. The coefficients of $\varepsilon'$ on the two sides give $\mathrm{Lie}(u)([X, Y]) = [\mathrm{Lie}(u)(X), \mathrm{Lie}(u)(Y)]$.

For part 3, Chapter 1 shows that $G$ is isomorphic to a closed subgroup of $GL_V$ for some $V$. The inclusion $i : G \to GL_V$ gives an injective map $\mathrm{Lie}(i)$, because $G(k[\varepsilon]) \subset GL_V(k[\varepsilon])$. By parts 1 and 2, $\mathrm{Lie}(i)$ identifies $\mathrm{Lie}(G)$ with a subspace of $\mathfrak{gl}(V)$ that is closed under the commutator, and the bracket of $\mathrm{Lie}(G)$ with the commutator. The bracket of $\mathfrak{gl}(V)$ satisfies the two axioms of Definition 2.1.1, so the bracket of $\mathrm{Lie}(G)$ does too. $\square$

Thus all the Lie algebras of Example 2.1.7 have the commutator as bracket, and they are the linear Lie algebras of Example 2.1.2. If $G$ is commutative, then $\mathrm{Ad}$ is trivial and $\mathrm{Lie}(G)$ is abelian.

**Proposition 2.1.10 (kernels).** Let $u : G \to H$ be a homomorphism of affine algebraic groups with kernel $N$. Then $\mathrm{Lie}(N) = \ker \mathrm{Lie}(u)$, and $\mathrm{Lie}(N)$ is an ideal of $\mathrm{Lie}(G)$.

Lean: not stated yet

*Proof.* By definition $N(R) = \ker(G(R) \to H(R))$ for each $R$. An element $X \in \mathrm{Lie}(G)$ lies in $N(k[\varepsilon])$ if and only if $u(X) = 1$ in $H(k[\varepsilon])$, that is, if and only if $\mathrm{Lie}(u)(X) = 0$. The kernel of a homomorphism of Lie algebras is an ideal, by Theorem 2.1.9. $\square$

**Example 2.1.11 (the projective linear group).** The group $PGL_n$ is the quotient $GL_n / \mathbb{G}_m$ by the scalar matrices. Its Lie algebra is $\mathfrak{gl}_n / k$, the quotient by the scalar matrices. Indeed, the quotient map $GL_n \to PGL_n$ has kernel $\mathbb{G}_m$, so the differential $\mathfrak{gl}_n \to \mathrm{Lie}(PGL_n)$ has kernel $\mathrm{Lie}(\mathbb{G}_m) = k$ by Proposition 2.1.10. Its image has dimension $n^2 - 1$. The group $PGL_n$ is smooth of dimension $n^2 - 1$, so $\dim \mathrm{Lie}(PGL_n) = n^2 - 1$ by Theorem 2.1.12 below, and the differential is surjective. Consider now the isogeny $SL_n \to PGL_n$, with kernel $\mu_n$. If the characteristic $p$ divides $n$, then the scalar matrices lie in $\mathfrak{sl}_n$, and the differential $\mathfrak{sl}_n \to \mathfrak{gl}_n / k$ has the kernel $k = \mathrm{Lie}(\mu_n)$. So an isogeny need not induce an isomorphism of Lie algebras. Exercise 2 of Section 2.8 computes the image.

### Dimension and smoothness

An algebraic group $G$ over $k$ is *smooth* if $\mathcal{O}(G) \otimes_k \bar k$ is reduced. Springer's linear algebraic groups are the smooth affine algebraic groups over $\bar k$.

**Theorem 2.1.12 (dimension and smoothness).** Let $G$ be an affine algebraic group over $k$.
1. $\dim \mathrm{Lie}(G) \ge \dim G$, with equality if and only if $G$ is smooth.
2. (Cartier) If $k$ has characteristic 0, then $G$ is smooth.

Lean: not stated yet

*Proof sketch.* For part 1, the dimension of the tangent space of a scheme of finite type at a point is at least the local dimension, with equality at the regular points. Over $\bar k$ the translations act transitively on the points of $G$, so $G$ is regular everywhere as soon as it is regular at one point, and a group scheme over $\bar k$ that is regular is smooth. Part 2 is proved with Hopf algebras: in characteristic 0, the augmentation ideal $I$ is generated by elements whose powers are linearly independent modulo higher powers, and this forces $\mathcal{O}(G)$ to be reduced. See [Mil17], Chapter 1 and Chapter 3, and [Spr98], Chapter 4, for the variety case. $\square$

**Example 2.1.13 (failure in characteristic $p$).** Let $k$ have characteristic $p > 0$.
1. The group $\mu_p$ has dimension 0, and $\mathrm{Lie}(\mu_p) = k$ by Example 2.1.7. So $\mu_p$ is not smooth. Its coordinate ring $k[x]/(x^p - 1) = k[x]/((x - 1)^p)$ is not reduced.
2. The Frobenius map $F : \mathbb{G}_a \to \mathbb{G}_a$, $x \mapsto x^p$, is a homomorphism that is bijective on $\bar k$-points. Its differential is $0$, because $(a\varepsilon)^p = 0$.
3. The graph $H = \{(x, x^p)\}$ of $F$ is a smooth connected subgroup of $\mathbb{G}_a^2$, different from $\mathbb{G}_a \times 0$. Both have the Lie algebra $k \times 0$.

### Subgroups in characteristic zero

The third part of Example 2.1.13 does not happen in characteristic 0. Let $H, H'$ be closed subgroups of $G$. Their intersection $H \cap H'$ is the closed subgroup with $(H \cap H')(R) = H(R) \cap H'(R)$ for all $R$. In particular $\mathrm{Lie}(H \cap H') = \mathrm{Lie}(H) \cap \mathrm{Lie}(H')$ in any characteristic.

**Theorem 2.1.14 (the Lie algebra determines connected subgroups).** Let $k$ have characteristic 0, let $G$ be an affine algebraic group over $k$, and let $H$ and $H'$ be closed subgroups of $G$, with $H$ connected. Then $H \subset H'$ if and only if $\mathrm{Lie}(H) \subset \mathrm{Lie}(H')$. In particular, a connected closed subgroup is determined by its Lie algebra.

Lean: not stated yet

*Proof.* If $H \subset H'$, then $\mathrm{Lie}(H) \subset \mathrm{Lie}(H')$ by definition. Conversely, assume that $\mathrm{Lie}(H) \subset \mathrm{Lie}(H')$. Then $\mathrm{Lie}(H \cap H') = \mathrm{Lie}(H)$. By Theorem 2.1.12, the groups $H$ and $H \cap H'$ are smooth, and
$$\dim (H \cap H') = \dim \mathrm{Lie}(H \cap H') = \dim \mathrm{Lie}(H) = \dim H.$$
The identity component of $H \cap H'$ is a closed irreducible subvariety of the irreducible variety $H$ of the same dimension, so it is $H$. Thus $H \subset H \cap H' \subset H'$. $\square$

In characteristic 0 there are more results of this kind. A connected subgroup $H$ is normal in a connected group $G$ if and only if $\mathrm{Lie}(H)$ is an ideal of $\mathrm{Lie}(G)$. A connected group $G$ is commutative if and only if $\mathrm{Lie}(G)$ is abelian. The Lie algebra of the centralizer of a subgroup is the centralizer of its action. See [Mil17], Chapter 10. These statements fail in characteristic $p$. For example, in characteristic 2 the Lie algebra $\mathfrak{sl}_2$ is nilpotent, by Exercise 2 of Section 2.8, although $SL_2$ is simple.

**Remark 2.1.15 (real Lie groups).** Let $G$ be a real Lie group. Its Lie algebra is the tangent space $T_1 G$, with the bracket of the left invariant vector fields. The exponential map $\exp : T_1 G \to G$ is a local diffeomorphism at 0, and for $G = GL_n(\mathbb{R})$ it is the matrix exponential. If $G$ is an affine algebraic group over $\mathbb{R}$, then the Lie algebra of the Lie group $G(\mathbb{R})$ is $\mathrm{Lie}(G)$, and the bracket of the vector fields is the bracket of Definition 2.1.8. Chapter 4 uses this for the compact groups. Mathlib defines the Lie algebra of a Lie group as `GroupLieAlgebra`, the tangent space at the identity with the bracket of the invariant vector fields.
