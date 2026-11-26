---
title: The Jordan decomposition
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## The Jordan decomposition

Each invertible matrix $g$ over a perfect field is the product $g = g_s g_u$ of a semisimple matrix and a unipotent matrix that commute. This section shows that the decomposition is intrinsic to an algebraic group. If $g \in G(k)$, then $g_s$ and $g_u$ lie in $G(k)$, they do not depend on the embedding of $G$ into $GL_n$, and homomorphisms preserve them. The proof uses the regular representation, where right translation by $g$ is a locally finite automorphism of the algebra $\mathcal{O}(G)$. We follow [Spr98], Section 2.4, and [Mil17], Chapter 9. In this section $k$ is a perfect field.

### Endomorphisms of a vector space

**Definition 1.3.1 (semisimple, nilpotent and unipotent endomorphisms).** Let $V$ be a finite-dimensional vector space over $k$ and let $a \in \mathrm{End}(V)$. Then $a$ is *semisimple* if $a \otimes \bar k$ is diagonalizable on $V \otimes \bar k$, *nilpotent* if $a^m = 0$ for some $m$, and *unipotent* if $a - 1$ is nilpotent.

An endomorphism is semisimple if and only if its minimal polynomial has distinct roots in $\bar k$. Over a perfect field this holds if and only if the minimal polynomial is squarefree, that is, if and only if each $a$-stable subspace has an $a$-stable complement. Mathlib uses this last condition for its definition `Module.End.IsSemisimple`. A unipotent endomorphism has the single eigenvalue $1$, and a semisimple unipotent endomorphism is the identity. If $a$ and $b$ commute, they can be diagonalized together over $\bar k$. So the sum and the product of two commuting semisimple endomorphisms are semisimple. Also the sum of two commuting nilpotent endomorphisms is nilpotent, by the binomial formula.

**Theorem 1.3.2 (additive Jordan decomposition).** Let $a \in \mathrm{End}(V)$. There are unique endomorphisms $a_s$ and $a_n$ of $V$ such that $a_s$ is semisimple, $a_n$ is nilpotent, $a_s a_n = a_n a_s$ and $a = a_s + a_n$. There is a polynomial $P \in k[T]$ with $P(0) = 0$ and $a_s = P(a)$. In particular, $a_s$ and $a_n$ commute with every endomorphism that commutes with $a$.

Lean: `Module.End.exists_isNilpotent_isSemisimple` and `Module.End.isNilpotent_isSemisimple_unique`, from Mathlib

*Proof.* First let $k$ be algebraically closed. Let $\lambda_1, \dots, \lambda_r$ be the distinct eigenvalues of $a$, with multiplicities $m_1, \dots, m_r$ in the characteristic polynomial. By the Chinese remainder theorem there is a polynomial $P$ with
$$P \equiv \lambda_i \pmod{(T - \lambda_i)^{m_i}} \text{ for each } i, \qquad P \equiv 0 \pmod{T}.$$
The second condition is a consequence of the first if $0$ is an eigenvalue, and it is compatible with the first otherwise. By the Cayley and Hamilton theorem, $V$ is the direct sum of the generalized eigenspaces $V_i = \ker (a - \lambda_i)^{m_i}$. On $V_i$, the endomorphism $P(a)$ is $\lambda_i$. So $a_s = P(a)$ is semisimple, and $a_n = a - P(a)$ is nilpotent on each $V_i$. They commute because they are polynomials in $a$. For uniqueness, let $a = s + n$ be a second decomposition. Then $s$ and $n$ commute with $a$, so they commute with $a_s$ and $a_n$. The element $a_s - s = n - a_n$ is semisimple and nilpotent, so it is $0$.

Now let $k$ be perfect. Then $\bar k / k$ is a Galois extension, and $\Gamma = \mathrm{Gal}(\bar k / k)$ acts on $V \otimes \bar k$ through the second factor. For $\sigma \in \Gamma$ we have $\sigma (a \otimes 1) \sigma^{-1} = a \otimes 1$, so $\sigma a_s \sigma^{-1}$ and $\sigma a_n \sigma^{-1}$ form a second Jordan decomposition of $a \otimes 1$. By uniqueness, $a_s$ and $a_n$ commute with $\Gamma$. An endomorphism of $V \otimes \bar k$ that commutes with $\Gamma$ comes from $\mathrm{End}(V)$, because the fixed field of $\Gamma$ is $k$. The polynomial $P$ can then be chosen in $k[T]$: the elements $a, a^2, a^3, \dots$ of $\mathrm{End}(V)$ span a subspace over $k$, and $a_s$ lies in its span over $\bar k$, hence in its span over $k$. $\square$

**Corollary 1.3.3 (multiplicative Jordan decomposition).** Let $g \in GL(V)$. There are unique elements $g_s, g_u \in GL(V)$ such that $g_s$ is semisimple, $g_u$ is unipotent, $g_s g_u = g_u g_s$ and $g = g_s g_u$.

Lean: not stated yet

*Proof.* The eigenvalues of $g_s$ are those of $g$, so $g_s$ is invertible. Put $g_u = 1 + g_s^{-1} g_n$. Since $g_s^{-1}$ is a polynomial in $g_s$, it commutes with $g_n$, so $g_s^{-1} g_n$ is nilpotent and $g_u$ is unipotent. Then $g_s g_u = g_s + g_n = g$. If $g = s u$ is a second decomposition, then $g = s + s(u - 1)$, where $s(u - 1)$ is nilpotent and commutes with $s$. By Theorem 1.3.2, $s = g_s$ and $s(u - 1) = g_n$, so $u = g_u$. $\square$

**Proposition 1.3.4 (functoriality).** Let $a \in \mathrm{End}(V)$, $b \in \mathrm{End}(W)$, and let $\varphi : V \to W$ be a linear map with $\varphi a = b \varphi$. Then $\varphi a_s = b_s \varphi$ and $\varphi a_n = b_n \varphi$. In particular:
1. an $a$-stable subspace $V'$ of $V$ is stable under $a_s$ and $a_n$, and the restriction of $a_s$ to $V'$ is $(a|_{V'})_s$; the same holds for the quotient $V/V'$;
2. for $g \in GL(V)$ and $h \in GL(W)$, one has $(g \otimes h)_s = g_s \otimes h_s$ and $(g \otimes h)_u = g_u \otimes h_u$;
3. the contragredient $g^\vee$ of $g$ on $V^\vee$ has $(g^\vee)_s = (g_s)^\vee$ and $(g^\vee)_u = (g_u)^\vee$.

Lean: not stated yet

*Proof.* The endomorphism $a_s \oplus b_s$ of $V \oplus W$ is semisimple, $a_n \oplus b_n$ is nilpotent, and they commute. So they are the Jordan components of $a \oplus b$. The graph $\Gamma_\varphi = \{(v, \varphi v)\}$ is stable under $a \oplus b$, because $\varphi a = b \varphi$. The endomorphism $a_s \oplus b_s$ is a polynomial in $a \oplus b$, so it also maps $\Gamma_\varphi$ to itself. This means that $(a_s v, b_s \varphi v)$ lies in the graph, that is, $\varphi a_s v = b_s \varphi v$. The same holds for $a_n$. For part 1, apply the first claim to the inclusion $V' \to V$ and to the projection $V \to V/V'$. For part 2, the elements $g_s \otimes h_s$ and $g_u \otimes h_u$ commute, their product is $g \otimes h$, the first is semisimple, and the second is unipotent because it is $(g_u \otimes 1)(1 \otimes h_u)$, a product of commuting unipotent elements. Part 3 is similar, since the inverse and the transpose of a semisimple or unipotent element have the same property. $\square$

**Example 1.3.5 (a computation).** Over $\mathbb{Q}$, let
$$g = \begin{pmatrix} 2 & 1 & 0 \\ 0 & 2 & 0 \\ 0 & 0 & 3 \end{pmatrix}.$$
The characteristic polynomial is $(T - 2)^2 (T - 3)$. We look for $P = 2 + c (T - 2)^2$ with $P(3) = 3$, so $c = 1$ and $P = T^2 - 4T + 6$. Then $P(g) = g^2 - 4g + 6 = \mathrm{diag}(2, 2, 3)$, which is $g_s$. The unipotent part is
$$g_u = g_s^{-1} g = \begin{pmatrix} 1 & 1/2 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{pmatrix}.$$
The decomposition need not be visible in the matrix entries. For $g = \left(\begin{smallmatrix} 1 & 1 \\ -1 & 3 \end{smallmatrix}\right)$ the trace is $4$ and the determinant is $4$, so the characteristic polynomial is $(T - 2)^2$. Thus $g_s = 2 \cdot 1$, $g_n = g - 2 = \left(\begin{smallmatrix} -1 & 1 \\ -1 & 1 \end{smallmatrix}\right)$ with $g_n^2 = 0$, and $g_u = g / 2$.

**Remark 1.3.6 (imperfect fields).** Theorem 1.3.2 fails over an imperfect field. Let $k = \mathbb{F}_2(t)$ and $g = \left(\begin{smallmatrix} 0 & t \\ 1 & 0 \end{smallmatrix}\right)$. The characteristic polynomial is $T^2 - t$, which is irreducible over $k$ and is $(T - \sqrt{t})^2$ over $\bar k$. Over $\bar k$, the semisimple part of $g$ is the scalar $\sqrt{t}$, which is not defined over $k$. So $g$ has no Jordan decomposition over $k$. Note also that $g$ is semisimple in the sense of Mathlib, since its minimal polynomial $T^2 - t$ is irreducible, but $g \otimes \bar k$ is not diagonalizable. This is why we take $k$ perfect. For an algebraic group over an arbitrary field, one decomposes the elements of $G(\bar k)$ or of $G(k^{p^{-\infty}})$.

### Locally finite endomorphisms

Let $V$ be a vector space of any dimension. An endomorphism $a$ of $V$ is *locally finite* if each $v \in V$ lies in a finite-dimensional $a$-stable subspace. Then $V$ is the union of its finite-dimensional $a$-stable subspaces $V'$. On each $V'$ we have the decomposition $a|_{V'} = (a|_{V'})_s + (a|_{V'})_n$. By Proposition 1.3.4, part 1, these are compatible: if $V' \subset V''$, then $(a|_{V''})_s$ restricts to $(a|_{V'})_s$. So they glue to endomorphisms $a_s$ and $a_n$ of $V$, which are locally finite and commute. We call $a$ semisimple if $a = a_s$, and locally nilpotent if $a = a_n$. Similarly an invertible locally finite $g$ has $g = g_s g_u$, because $g$ maps each finite-dimensional $g$-stable subspace onto itself, and Proposition 1.3.4 holds for locally finite endomorphisms, with the same proof applied to finite-dimensional stable subspaces. The tensor product statement applies to $V \otimes W$ with $V$ and $W$ of any dimension.

By Theorem 1.1.18, each $g \in G(k)$ acts locally finitely in each representation of $G$. The main case is the regular representation. There $g$ acts by the right translation $\rho_g$, with $(\rho_g a)(x) = a(xg)$.

### The decomposition in an algebraic group

**Theorem 1.3.7 (Jordan decomposition in $G$).** Let $G$ be an algebraic group over a perfect field $k$ and let $g \in G(k)$. There are unique elements $g_s$ and $g_u$ of $G(k)$ such that $g = g_s g_u = g_u g_s$ and such that, for each finite-dimensional representation $r : G \to GL_V$, one has $r(g)_s = r(g_s)$ and $r(g)_u = r(g_u)$. If $f : G \to H$ is a homomorphism, then $f(g)_s = f(g_s)$ and $f(g)_u = f(g_u)$. If $G$ is a closed subgroup of $GL_n$, then $g_s$ and $g_u$ are the Jordan components of the matrix $g$.

Lean: not stated yet

*Proof sketch.* Write $A = \mathcal{O}(G)$. The right translation $\rho_g$ is an automorphism of the algebra $A$, so $\rho_g \circ m = m \circ (\rho_g \otimes \rho_g)$, where $m : A \otimes A \to A$ is the multiplication. By Proposition 1.3.4 for locally finite endomorphisms, $(\rho_g)_s \circ m = m \circ ((\rho_g)_s \otimes (\rho_g)_s)$. So $(\rho_g)_s$ is an algebra endomorphism of $A$, and it is invertible since its eigenvalues on each finite-dimensional stable subspace are those of $\rho_g$. Right translation commutes with the comultiplication in the sense that $\Delta \circ \rho_g = (\mathrm{id} \otimes \rho_g) \circ \Delta$. The Jordan components of $\mathrm{id} \otimes \rho_g$ are $\mathrm{id} \otimes (\rho_g)_s$ and $\mathrm{id} \otimes (\rho_g)_u$, so Proposition 1.3.4 gives $\Delta \circ (\rho_g)_s = (\mathrm{id} \otimes (\rho_g)_s) \circ \Delta$.

Now let $\varphi$ be any algebra endomorphism of $A$ with $\Delta \circ \varphi = (\mathrm{id} \otimes \varphi) \circ \Delta$. Put $x = \varepsilon \circ \varphi$. It is a homomorphism $A \to k$, so $x \in G(k)$. Then
$$\varphi = (\mathrm{id} \otimes \varepsilon) \circ \Delta \circ \varphi = (\mathrm{id} \otimes \varepsilon \varphi) \circ \Delta = (\mathrm{id} \otimes x) \circ \Delta = \rho_x.$$
So $(\rho_g)_s = \rho_{g_s}$ and $(\rho_g)_u = \rho_{g_u}$ for unique elements $g_s, g_u \in G(k)$. Since $\rho$ is injective on $G(k)$, they commute and $g = g_s g_u$.

Let $V$ be a finite-dimensional representation with comodule map $\rho_V : V \to V \otimes A$. Let $V_0$ be the vector space $V$ with the trivial action of $G$. Then $\rho_V$ is an injective homomorphism of representations $V \to V_0 \otimes A$, where $G$ acts on $V_0 \otimes A$ by $\mathrm{id} \otimes \rho_g$. This is the comodule identity. So Proposition 1.3.4 gives $r(g)_s = r(g_s)$. The statement on homomorphisms follows by applying this to the representations of $G$ that come from representations of $H$, and to a faithful representation of $H$. The last statement is the case of the inclusion $G \to GL_n$. The details are in [Spr98], Section 2.4, and in [Mil17], Chapter 9. $\square$

**Definition 1.3.8 (semisimple and unipotent elements).** Let $G$ be an algebraic group over a perfect field $k$. An element $g \in G(k)$ is *semisimple* if $g = g_s$ and *unipotent* if $g = g_u$. We write $G(k)_s$ and $G(k)_u$ for these sets.

By Theorem 1.3.7, $g$ is semisimple if and only if $r(g)$ is semisimple for one faithful representation $r$, and then $r(g)$ is semisimple for all representations. The same holds for unipotent elements. A homomorphism maps semisimple elements to semisimple elements and unipotent elements to unipotent elements.

**Example 1.3.9 (the basic cases).** In $\mathbb{G}_a(k) = k$ every element is unipotent, because $t$ acts on $k^2$ by the unipotent matrix $\left(\begin{smallmatrix} 1 & t \\ 0 & 1 \end{smallmatrix}\right)$. In $\mathbb{G}_m(k) = k^\times$ every element is semisimple. So every homomorphism $\mathbb{G}_a \to \mathbb{G}_m$ is trivial on $k$-points, and every homomorphism $\mathbb{G}_m \to \mathbb{G}_a$ is trivial on $k$-points. In $D_n(k)$ every element is semisimple, and in $U_n(k)$ every element is unipotent. For $b \in B_n(k)$, the semisimple part need not be the diagonal of $b$. For instance, $b = \left(\begin{smallmatrix} 1 & 1 \\ 0 & 2 \end{smallmatrix}\right)$ has distinct eigenvalues, so $b$ is semisimple, but $b$ is not diagonal. Its semisimple part is $b$ itself, and it is conjugate in $B_2(k)$ to $\mathrm{diag}(1, 2)$. Let $\Gamma$ be a finite group and let $k$ have characteristic $p$. In the constant group $\Gamma$, an element of order prime to $p$ is semisimple, because its minimal polynomial divides $T^m - 1$ with $p \nmid m$, which has distinct roots. An element of order $p^r$ is unipotent, because $(g - 1)^{p^r} = g^{p^r} - 1 = 0$. So the Jordan decomposition of $g \in \Gamma$ is the decomposition into its $p'$-part and its $p$-part. In characteristic $0$, every element of a finite group is semisimple.

**Proposition 1.3.10 (the unipotent elements).** Let $k$ be algebraically closed and let $G$ be smooth. The set $G(k)_u$ is closed in $G(k)$.

Lean: not stated yet

*Proof.* Choose a closed embedding $G \to GL_n$ by Theorem 1.2.3. By Theorem 1.3.7, $g \in G(k)$ is unipotent if and only if $(g - 1)^n = 0$ as a matrix. The entries of $(g - 1)^n$ are polynomials in the entries of $g$, so this is a closed condition. $\square$

The set of semisimple elements is not closed in general. In $GL_2$, the matrices $\left(\begin{smallmatrix} 1 & 1 \\ 0 & 1 + t \end{smallmatrix}\right)$ are semisimple for $t \ne 0$, and their limit at $t = 0$ is not. For $G = GL_n$ over an algebraically closed field the semisimple elements contain the dense open set of matrices with distinct eigenvalues. In a connected group each semisimple element lies in a maximal torus ([Spr98], Chapter 6), so the semisimple elements are the union of the maximal tori.
