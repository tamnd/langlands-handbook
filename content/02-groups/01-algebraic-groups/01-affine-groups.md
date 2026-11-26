---
title: Affine groups and Hopf algebras
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Affine groups and Hopf algebras

This section defines an algebraic group as a functor on $k$-algebras that is represented by a Hopf algebra. It gives the standard examples, compares the definition with the classical one by points over an algebraically closed field, and defines representations as comodules. We follow [Mil17], Chapters 1 to 4. In this chapter $k$ is a field, a $k$-algebra is commutative with a unit, and $\mathrm{Alg}_k$ is the category of $k$-algebras.

### Group functors and Hopf algebras

**Definition 1.1.1 (affine group).** An *affine group* over $k$ is a functor $G : \mathrm{Alg}_k \to \mathrm{Grp}$ for which there is a $k$-algebra $A$ and a bijection $G(R) \cong \mathrm{Hom}_{k\text{-alg}}(A, R)$, natural in $R$. The algebra $A$ is the *coordinate ring* $\mathcal{O}(G)$. The affine group $G$ is an *algebraic group* if $\mathcal{O}(G)$ is a finitely generated $k$-algebra. A *homomorphism* $f : G \to H$ of affine groups is a natural transformation such that each map $f_R : G(R) \to H(R)$ is a homomorphism of groups.

In the language of schemes, an affine group is an affine group scheme $\mathrm{Spec}\, A$ over $k$, and $G(R)$ is the set of its points with values in $R$. We use only the functor. In this volume every algebraic group is affine, and we say "algebraic group" for "affine algebraic group". An element $a \in \mathcal{O}(G)$ is a function on $G$: its value at $x \in G(R) = \mathrm{Hom}(\mathcal{O}(G), R)$ is $a(x) = x(a) \in R$. For $R = k$ this is the usual notion of a polynomial function on the points.

For a $k$-algebra $A$ let $h^A = \mathrm{Hom}_{k\text{-alg}}(A, -)$ be the functor that $A$ represents.

**Lemma 1.1.2 (Yoneda).** Let $A$ and $B$ be $k$-algebras. Each natural transformation $\varphi : h^A \to h^B$ is $h^\alpha$ for a unique homomorphism $\alpha : B \to A$, namely $\alpha = \varphi_A(\mathrm{id}_A)$. Thus $A \mapsto h^A$ is an anti-equivalence from $k$-algebras to the representable functors on $\mathrm{Alg}_k$.

Lean: `CategoryTheory.Coyoneda.fullyFaithful`, from Mathlib

*Proof.* Let $\alpha = \varphi_A(\mathrm{id}_A) \in \mathrm{Hom}(B, A)$. For $x \in h^A(R)$, that is $x : A \to R$, naturality applied to $x$ gives $\varphi_R(x) = \varphi_R(x \circ \mathrm{id}_A) = x \circ \varphi_A(\mathrm{id}_A) = x \circ \alpha$. So $\varphi = h^\alpha$. Conversely $h^\alpha_A(\mathrm{id}_A) = \alpha$, so $\alpha$ is unique. $\square$

**Definition 1.1.3 (Hopf algebra).** A *Hopf algebra* over $k$ is a $k$-algebra $A$ with $k$-algebra homomorphisms
$$\Delta : A \to A \otimes_k A, \qquad \varepsilon : A \to k, \qquad S : A \to A,$$
the *comultiplication*, the *counit* and the *antipode*, such that
$$(\Delta \otimes \mathrm{id}) \circ \Delta = (\mathrm{id} \otimes \Delta) \circ \Delta, \qquad (\varepsilon \otimes \mathrm{id}) \circ \Delta = \mathrm{id} = (\mathrm{id} \otimes \varepsilon) \circ \Delta, \qquad m \circ (S \otimes \mathrm{id}) \circ \Delta = \eta \circ \varepsilon = m \circ (\mathrm{id} \otimes S) \circ \Delta.$$
Here $m : A \otimes A \to A$ is the multiplication and $\eta : k \to A$ is the unit. In the second identity we identify $k \otimes A$ and $A \otimes k$ with $A$. A *Hopf ideal* is an ideal $I$ with $\Delta(I) \subset I \otimes A + A \otimes I$, $\varepsilon(I) = 0$ and $S(I) \subset I$. Then $A/I$ is again a Hopf algebra.

Lean: `HopfAlgebra`, from Mathlib

All Hopf algebras in this volume are commutative. Mathlib allows noncommutative ones, as does the theory of quantum groups.

**Theorem 1.1.4 (affine groups and Hopf algebras).** The functor $G \mapsto \mathcal{O}(G)$ is an anti-equivalence from the category of affine groups over $k$ to the category of commutative Hopf algebras over $k$. For an affine group $G$, the maps $\Delta$, $\varepsilon$ and $S$ are characterized by
$$(\Delta a)(x, y) = a(xy), \qquad \varepsilon(a) = a(e), \qquad (S a)(x) = a(x^{-1})$$
for $a \in \mathcal{O}(G)$ and $x, y \in G(R)$, where $\mathcal{O}(G) \otimes \mathcal{O}(G)$ is the coordinate ring of $G \times G$.

Lean: `AlgebraicGeometry.hopfSpec.fullyFaithful`, from Mathlib, for the full faithfulness of $\mathrm{Spec}$ on commutative Hopf algebras

*Proof.* Let $A = \mathcal{O}(G)$. The functor $R \mapsto G(R) \times G(R)$ is represented by $A \otimes A$, because a homomorphism $A \otimes A \to R$ is a pair of homomorphisms $A \to R$. The one point functor $R \mapsto \{e\}$ is represented by $k$. The multiplication $G \times G \to G$, the unit $\{e\} \to G$ and the inverse $G \to G$ are natural transformations, so by Lemma 1.1.2 they are $h^\Delta$, $h^\varepsilon$ and $h^S$ for unique homomorphisms $\Delta$, $\varepsilon$ and $S$. The formulas of the theorem say exactly this. The associativity of the group law is the equality of two natural transformations $G \times G \times G \to G$, and by Lemma 1.1.2 it is equivalent to the coassociativity of $\Delta$. In the same way the axiom $ex = x = xe$ is equivalent to the counit axiom, and $x^{-1} x = e = x x^{-1}$ is equivalent to the antipode axiom. Thus $\mathcal{O}(G)$ is a Hopf algebra, and conversely each commutative Hopf algebra $A$ makes $h^A$ a functor to groups. A natural transformation $G \to H$ is a homomorphism of groups at each $R$ if and only if the corresponding map $\mathcal{O}(H) \to \mathcal{O}(G)$ commutes with $\Delta$. It then commutes with $\varepsilon$ and $S$ as well, because a map of groups that preserves products also preserves the unit and inverses. $\square$

### Examples

**Example 1.1.5 (the additive group).** The functor $\mathbb{G}_a(R) = (R, +)$ is represented by $k[t]$, since a homomorphism $k[t] \to R$ is the choice of the image of $t$. The formula $(\Delta a)(x, y) = a(x + y)$ gives
$$\Delta(t) = t \otimes 1 + 1 \otimes t, \qquad \varepsilon(t) = 0, \qquad S(t) = -t.$$

**Example 1.1.6 (the multiplicative group).** The functor $\mathbb{G}_m(R) = R^\times$ is represented by $k[t, t^{-1}]$, and
$$\Delta(t) = t \otimes t, \qquad \varepsilon(t) = 1, \qquad S(t) = t^{-1}.$$
More generally $\mathbb{G}_m^r(R) = (R^\times)^r$ is represented by $k[t_1^{\pm 1}, \dots, t_r^{\pm 1}]$.

**Example 1.1.7 (the general and special linear groups).** The functor $GL_n(R)$, the group of invertible $n \times n$ matrices with entries in $R$, is represented by
$$\mathcal{O}(GL_n) = k[x_{ij} : 1 \le i, j \le n][1/\det],$$
because a matrix over $R$ is invertible if and only if its determinant is a unit. The rule for the product of matrices gives $\Delta(x_{ij}) = \sum_{l} x_{il} \otimes x_{lj}$, the counit is $\varepsilon(x_{ij}) = \delta_{ij}$, and $S(x_{ij})$ is the $(i, j)$ entry of the inverse matrix, a polynomial in the $x_{lm}$ divided by $\det$. Since $\det$ is multiplicative, $\Delta(\det) = \det \otimes \det$. The group $SL_n(R) = \{g \in GL_n(R) : \det g = 1\}$ is represented by $\mathcal{O}(SL_n) = k[x_{ij}] / (\det - 1)$. For a finite-dimensional vector space $V$ we write $GL_V(R) = \mathrm{Aut}_R(V \otimes_k R)$. A basis of $V$ identifies $GL_V$ with $GL_n$.

Lean: `Matrix.GeneralLinearGroup` and `Matrix.SpecialLinearGroup`, from Mathlib, for the groups of points $GL_n(R)$ and $SL_n(R)$ of one ring

**Example 1.1.8 (roots of unity).** For $n \ge 1$ let $\mu_n(R) = \{r \in R : r^n = 1\}$. It is represented by $k[t] / (t^n - 1)$, with the comultiplication of $\mathbb{G}_m$. Assume that $k$ has characteristic $p > 0$. Then $t^p - 1 = (t - 1)^p$, so $\mathcal{O}(\mu_p) = k[t]/(t - 1)^p$ is not reduced. For a reduced $k$-algebra $R$ an element with $r^p = 1$ satisfies $(r - 1)^p = 0$, so $r = 1$. Thus $\mu_p(R) = \{1\}$ for every reduced $R$, and in particular for every field. But $\mu_p$ is not the trivial group, since $\mu_p(k[t]/(t-1)^p)$ contains the element $t$.

Lean: `rootsOfUnity`, from Mathlib, for the group $\mu_n(R)$ of one ring

**Example 1.1.9 (constant groups and $\alpha_p$).** Let $\Gamma$ be a finite group. The algebra $k^\Gamma$ of all functions $\Gamma \to k$ is a Hopf algebra with $(\Delta f)(x, y) = f(xy)$, where we identify $k^\Gamma \otimes k^\Gamma$ with $k^{\Gamma \times \Gamma}$. The affine group $\Gamma_k$ that it represents sends $R$ to the set of families $(e_\gamma)_{\gamma \in \Gamma}$ of orthogonal idempotents of $R$ with sum $1$, which is $\Gamma$ when $R$ has no idempotents other than $0$ and $1$. This is the *constant group* $\Gamma_k$. In characteristic $p$ the group $\alpha_p(R) = \{r \in R : r^p = 0\}$, with the addition of $R$, is represented by $k[t]/(t^p)$ with the comultiplication of $\mathbb{G}_a$. Like $\mu_p$, it has only one point in each field.

**Example 1.1.10 (orthogonal and symplectic groups).** Let $J \in GL_n(k)$. The functor
$$G_J(R) = \{g \in GL_n(R) : g^{t} J g = J\}$$
is represented by the quotient of $\mathcal{O}(GL_n)$ by the ideal generated by the entries of $x^t J x - J$, where $x = (x_{ij})$. For $J$ symmetric this is the orthogonal group $O(q)$ of the quadratic form $q(v) = v^t J v$, and $SO(q)$ is its intersection with $SL_n$. For $n = 2m$ and
$$J = \begin{pmatrix} 0 & I_m \\ -I_m & 0 \end{pmatrix}$$
it is the symplectic group $Sp_{2m}$. Chapter 3 computes the root data of these groups.

### Smooth groups and their points

An algebraic group over $k$ is a scheme of finite type over $k$, and it may be smooth or not. For algebraic groups smoothness has a simple form.

**Definition 1.1.11 (smooth algebraic group).** An algebraic group $G$ over $k$ is *smooth* if the $\bar k$-algebra $\mathcal{O}(G) \otimes_k \bar k$ is reduced.

Lean: `AlgebraicGeometry.smooth_of_grpObj`, from Mathlib, which shows that a geometrically reduced group scheme locally of finite type over a field is smooth

By that result, Definition 1.1.11 agrees with the definition of a smooth scheme. If $k$ is perfect, $G$ is smooth if and only if $\mathcal{O}(G)$ is reduced. The groups $\mathbb{G}_a$, $\mathbb{G}_m$, $GL_n$ and $SL_n$ are smooth. The group $\mu_n$ is smooth if and only if the characteristic of $k$ does not divide $n$, because $t^n - 1$ is then separable. The groups $\mu_p$ and $\alpha_p$ in characteristic $p$ are not smooth. In characteristic $0$ such examples do not exist.

**Theorem 1.1.12 (Cartier).** Every algebraic group over a field of characteristic $0$ is smooth.

Lean: not stated yet

*Proof sketch.* We may assume that $k$ is algebraically closed. Let $A = \mathcal{O}(G)$ and let $\mathfrak{m} = \ker \varepsilon$, the maximal ideal of the identity. The translations by the points of $G(k)$ act transitively on the maximal ideals of $A$, so it suffices to show that the local ring $A_\mathfrak{m}$ is regular. Then all local rings of $A$ at maximal ideals are regular, and $A$ is reduced.

Let $X : A \to k$ be a derivation at $e$, that is, a linear map with $X(ab) = a(e) X(b) + X(a) b(e)$. Then $D = (\mathrm{id} \otimes X) \circ \Delta$ is a derivation of $A$ with $D(a)(e) = X(a)$, and $D(\mathfrak{m}^j) \subset \mathfrak{m}^{j-1}$. Choose $x_1, \dots, x_n \in \mathfrak{m}$ whose classes form a basis of $\mathfrak{m}/\mathfrak{m}^2$, and derivations $D_1, \dots, D_n$ of this form with $D_i(x_j)(e) = \delta_{ij}$. Let $P$ be a homogeneous polynomial of degree $d$ with $P(x_1, \dots, x_n) \in \mathfrak{m}^{d+1}$. For a multi-index $\alpha$ with $|\alpha| = d$, apply $D^\alpha = D_1^{\alpha_1} \cdots D_n^{\alpha_n}$ and evaluate at $e$. The right side gives $0$, since $D^\alpha(\mathfrak{m}^{d+1}) \subset \mathfrak{m}$. On the left side only the terms in which each derivation meets a different factor $x_j$ survive, and the result is $\alpha!$ times the coefficient of $x^\alpha$ in $P$. In characteristic $0$ the integer $\alpha!$ is invertible, so $P = 0$. Thus the graded ring $\bigoplus_j \mathfrak{m}^j / \mathfrak{m}^{j+1}$ of $A_\mathfrak{m}$ is a polynomial ring in $n$ variables, so $\dim A_\mathfrak{m} = n = \dim \mathfrak{m}/\mathfrak{m}^2$, and $A_\mathfrak{m}$ is regular. See [Mil17], Chapter 3, for the details. $\square$

In characteristic $p$ the argument fails at the last step, and $\mu_p$ shows that the theorem fails too: for $x = t - 1$ in $\mathcal{O}(\mu_p)$ one has $x^p = 0$, and $D^p$ applied to $x^p$ gives $p! = 0$.

Over an algebraically closed field a smooth algebraic group is determined by its points. This is the bridge to the classical theory of [Spr98], which works with the variety $G(k)$.

**Proposition 1.1.13 (smooth groups and their points).** Let $k$ be algebraically closed, and let $G$ and $H$ be smooth algebraic groups over $k$.
1. The map from $\mathcal{O}(G)$ to the ring of functions $G(k) \to k$ is injective.
2. A homomorphism $f : G \to H$ is determined by the map $f_k : G(k) \to H(k)$.
3. Let $\alpha : \mathcal{O}(H) \to \mathcal{O}(G)$ be a homomorphism of $k$-algebras whose map on points $G(k) \to H(k)$ is a homomorphism of groups. Then $\alpha$ is a homomorphism of Hopf algebras, so it comes from a homomorphism $G \to H$.

Lean: not stated yet

*Proof.* (1) The algebra $\mathcal{O}(G)$ is finitely generated and reduced. An element that vanishes at every point of $G(k)$ lies in every maximal ideal, by the Nullstellensatz, so it is nilpotent, and thus it is $0$. (2) Let $f, f' : G \to H$ agree on $G(k)$. For $b \in \mathcal{O}(H)$, the function $f^*(b) - f'^*(b)$ vanishes on $G(k)$, so it is $0$ by (1). Thus $f^* = f'^*$, and $f = f'$ by Theorem 1.1.4. (3) The algebra $\mathcal{O}(G) \otimes \mathcal{O}(G)$ is reduced, because $k$ is algebraically closed, and its points are $G(k) \times G(k)$. For $b \in \mathcal{O}(H)$, the two elements $\Delta_G(\alpha(b))$ and $(\alpha \otimes \alpha)(\Delta_H(b))$ have the values $b(f(xy))$ and $b(f(x) f(y))$ at $(x, y)$, and these agree. By (1) for $G \times G$, the two elements are equal. $\square$

**Remark 1.1.14 (why functors).** Over an algebraically closed field, Proposition 1.1.13 shows that the smooth algebraic groups are the linear algebraic groups of the classical theory. Why use functors at all? There are three reasons. First, the groups of the Langlands program are defined over $\mathbb{Q}$, over number fields and over $p$-adic fields, and the functor gives $G(\mathbb{Q})$, $G(\mathbb{Q}_p)$, $G(\mathbb{Z}_p)$ and $G(\mathbb{A}_F)$ at once. Second, kernels of homomorphisms of smooth groups need not be smooth. The kernel of the $p$-th power map of $\mathbb{G}_m$ in characteristic $p$ is $\mu_p$, and the centre of $SL_p$ is $\mu_p$. A theory of points only would lose these groups. Third, a property of $G$ over $k$ can be tested after a field extension: for an extension $K / k$, the base change $G_K$ is the restriction of $G$ to $K$-algebras, and $\mathcal{O}(G_K) = \mathcal{O}(G) \otimes_k K$.

### Representations and comodules

**Definition 1.1.15 (representation and comodule).** A *representation* of an affine group $G$ on a $k$-vector space $V$ is a family of $R$-linear actions of $G(R)$ on $V \otimes_k R$, natural in $R$. If $V$ is finite-dimensional, this is a homomorphism $r : G \to GL_V$. A *comodule* over a Hopf algebra $A$ is a vector space $V$ with a linear map $\rho : V \to V \otimes A$ such that
$$(\rho \otimes \mathrm{id}_A) \circ \rho = (\mathrm{id}_V \otimes \Delta) \circ \rho, \qquad (\mathrm{id}_V \otimes \varepsilon) \circ \rho = \mathrm{id}_V.$$

**Proposition 1.1.16 (representations are comodules).** Let $A = \mathcal{O}(G)$. A comodule $\rho : V \to V \otimes A$ defines a representation by the rule
$$g \cdot v = \sum_i v_i \otimes g(a_i) \quad \text{for } g \in G(R), \text{ where } \rho(v) = \sum_i v_i \otimes a_i.$$
Each representation of $G$ arises in this way from a unique comodule structure on $V$. A subspace $W \subset V$ is a subrepresentation if and only if $\rho(W) \subset W \otimes A$.

Lean: not stated yet

*Proof.* Let a representation be given. The identity $\mathrm{id}_A$ is a point of $G(A)$, the *universal point*. Its action on $v \otimes 1 \in V \otimes A$ defines $\rho(v)$. Each $g \in G(R)$ is the image of the universal point under $g : A \to R$, so naturality gives $g \cdot v = (\mathrm{id}_V \otimes g)(\rho(v))$, which is the rule of the proposition. Thus $\rho$ determines the representation. The comodule identities express the action axioms $(gh) \cdot v = g \cdot (h \cdot v)$ and $e \cdot v = v$ for the universal point of $G \times G$ and for $e$. The last claim follows from the same formula. $\square$

**Example 1.1.17 (the regular representation).** The comultiplication $\Delta : A \to A \otimes A$ makes $A = \mathcal{O}(G)$ a comodule. The corresponding representation is the right translation: for $g \in G(R)$ and $a \in A$, the element $g \cdot a$ is the function $x \mapsto a(xg)$, because $(\Delta a)(x, g) = a(xg)$. This is the *regular representation* of $G$. For $G = \mathbb{G}_m$, the line $k t^n$ is a subrepresentation, and $g \in R^\times$ acts on it by $g^n$.

**Theorem 1.1.18 (local finiteness).** Every representation of an affine group is the union of its finite-dimensional subrepresentations.

Lean: not stated yet

*Proof.* Let $\rho : V \to V \otimes A$ be the comodule and let $v \in V$. Choose a basis $(a_i)$ of $A$, and write $\rho(v) = \sum_i v_i \otimes a_i$, a finite sum. Write $\Delta(a_i) = \sum_{j, l} c_{ijl} \, a_j \otimes a_l$ with $c_{ijl} \in k$. The first comodule identity gives
$$\sum_i \rho(v_i) \otimes a_i = \sum_i v_i \otimes \Delta(a_i) = \sum_{i, j, l} c_{ijl} \, v_i \otimes a_j \otimes a_l.$$
We compare the coefficients of $a_l$ in the last factor. This gives $\rho(v_l) = \sum_{i, j} c_{ijl} \, v_i \otimes a_j$. So the span $W$ of the $v_i$ satisfies $\rho(W) \subset W \otimes A$, and $W$ is a finite-dimensional subrepresentation. The second comodule identity gives $v = \sum_i \varepsilon(a_i) v_i \in W$. $\square$

The theorem fails for abstract groups and their representations, and it is the main reason why the representation theory of algebraic groups is close to that of finite groups. The next section uses it to embed every algebraic group in some $GL_n$.
