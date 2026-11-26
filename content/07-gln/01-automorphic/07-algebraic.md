---
title: Algebraic automorphic representations
nodes: []
sources: [Lan70, HLTT16]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Algebraic automorphic representations

Not every cuspidal representation should correspond to a Galois representation. A Maass form with Laplace eigenvalue $1/4 + r^2$ and $r$ irrational has no reason to have algebraic Hecke eigenvalues, and no Galois representation is expected. Clozel singled out the *algebraic* representations by a condition at the infinite places, on the infinitesimal character. This section defines it, first with the Harish-Chandra isomorphism and then with the Capelli determinant, which is the form of the Lean project. The examples are the Hecke characters of type $A_0$, the holomorphic modular forms, and the Maass forms with eigenvalue $1/4$, which are algebraic but not regular.

### The infinitesimal character

Let $\mathfrak{g} = \mathfrak{gl}_n(\mathbb{C})$, $U(\mathfrak{g})$ its universal enveloping algebra and $Z(\mathfrak{g})$ the center of $U(\mathfrak{g})$. Let $\mathfrak{h}$ be the diagonal subalgebra, and $\delta = (\frac{n-1}{2}, \frac{n-3}{2}, \ldots, \frac{1-n}{2})$, so that $\delta_i = \frac{n+1}{2} - i$. This is half the sum of the positive roots.

**Theorem 1.7.1 (Harish-Chandra).** There is an isomorphism $\gamma : Z(\mathfrak{g}) \to S(\mathfrak{h})^{S_n} = \mathbb{C}[h_1, \ldots, h_n]^{S_n}$ with this property: on the irreducible representation of $\mathfrak{g}$ with highest weight $\lambda$, each $z \in Z(\mathfrak{g})$ acts by the scalar $\gamma(z)(\lambda + \delta)$. So the characters of $Z(\mathfrak{g})$ correspond to the multisets $\{h_1, \ldots, h_n\}$ of complex numbers.

Lean: not stated yet

*Proof sketch.* Write $U(\mathfrak{g}) = U(\mathfrak{h}) \oplus (\mathfrak{n}^- U(\mathfrak{g}) + U(\mathfrak{g}) \mathfrak{n}^+)$, where $\mathfrak{n}^\pm$ are the upper and lower triangular nilpotent subalgebras. Let $p : Z(\mathfrak{g}) \to U(\mathfrak{h}) = S(\mathfrak{h})$ be the projection. On a highest weight vector of weight $\lambda$, the element $z$ acts by $p(z)(\lambda)$, so $p$ is a homomorphism. Let $\gamma(z)(h) = p(z)(h - \delta)$. Then $\gamma(z)$ is invariant under $S_n$: the Verma modules of highest weight $\lambda$ and $s_\alpha(\lambda + \delta) - \delta$ have a nonzero map between them for $\lambda$ dominant integral and a simple reflection $s_\alpha$, so $z$ acts on them by the same scalar, and the integral weights are Zariski dense. Injectivity follows from the density of the dominant weights and the fact that $Z(\mathfrak{g})$ acts on the finite dimensional representations by the characters they determine. Surjectivity follows from a comparison of the graded algebras with Chevalley's theorem $S(\mathfrak{g})^{G} \simeq S(\mathfrak{h})^{S_n}$. $\square$

Let $v$ be an infinite place of $F$ and $\pi_v$ an irreducible admissible representation of $GL_n(F_v)$. Then $Z(\mathfrak{g}_v)$ acts on the $K_v$-finite vectors of $\pi_v$ by a character, the *infinitesimal character* of $\pi_v$, where $\mathfrak{g}_v$ is the complexified Lie algebra of $GL_n(F_v)$. For $v$ real, $\mathfrak{g}_v = \mathfrak{gl}_n(\mathbb{C})$ and the infinitesimal character is one multiset $\{h_i\}$. For $v$ complex, $\mathfrak{g}_v = \mathfrak{gl}_n(\mathbb{C}) \times \mathfrak{gl}_n(\mathbb{C})$ and it is a pair of multisets $(\{h_i\}, \{h'_i\})$. In terms of the Langlands parameter, if $\pi_v$ corresponds to $\phi_v : W_{F_v} \to GL_n(\mathbb{C})$ and
$$\phi_v(z) = \mathrm{diag}(z^{p_1} \bar z^{q_1}, \ldots, z^{p_n} \bar z^{q_n}) \qquad (z \in \mathbb{C}^\times),$$
with $p_i, q_i \in \mathbb{C}$ and $p_i - q_i \in \mathbb{Z}$, then the infinitesimal character is $\{p_i\}$ at a real place, where $\{q_i\} = \{p_i\}$, and $(\{p_i\}, \{q_i\})$ at a complex place.

### Algebraic and regular algebraic representations

**Definition 1.7.2 (Clozel).** A cuspidal automorphic representation $\pi$ of $GL_n(\mathbb{A})$ is *algebraic* if, for each infinite place $v$, the parameter of $\pi_v \otimes |\det|_v^{(1-n)/2}$ has all $p_i, q_i \in \mathbb{Z}$. Equivalently, every parameter $h$ of the infinitesimal character of $\pi_v$ satisfies $h - \frac{n-1}{2} \in \mathbb{Z}$. It is *regular algebraic* if, in addition, at each infinite place the $h_i$ are distinct, and at a complex place also the $h'_i$ are distinct.

Lean: `Langlands.NumberFieldGL.IsAlgebraicForm` and `Langlands.NumberFieldGL.IsRegularAlgebraicForm`, definitions of the project, through the Capelli operators below

The equivalence of the two conditions is the formula for the infinitesimal character above: the twist by $|\det|_v^{(1-n)/2}$ shifts every $p_i$ and $q_i$ by $\frac{1-n}{2}$. By Theorem 1.7.1, $\pi$ is regular algebraic if and only if $\pi_v$ has, for each infinite place $v$, the infinitesimal character of an irreducible algebraic representation of $GL_n(F_v)$, the restriction of an algebraic representation of $\mathrm{Res}_{F/\mathbb{Q}} GL_n$. Buzzard and Gee call Clozel's condition *C-algebraic*, and the integrality of the $p_i$ and $q_i$ of $\pi_v$ itself *L-algebraic*. For $GL_n$ the two notions differ by the twist $|\det|^{(n-1)/2}$, so the choice is a matter of normalization. For other groups they differ in an essential way.

### The Capelli determinant

The Lean project avoids the Harish-Chandra isomorphism and gives the generators of the center explicitly, by the classical identity of Capelli.

**Definition 1.7.3 (Capelli operator).** Let $D_{ij}$, $1 \le i, j \le n$, be operators that satisfy the commutation relations of the elementary matrices, $[D_{ij}, D_{kl}] = \delta_{jk} D_{il} - \delta_{li} D_{kj}$. For $u \in \mathbb{C}$ let
$$C(u) = \sum_{\sigma \in S_n} \mathrm{sgn}(\sigma) (D + u)_{\sigma(1) 1} (D + u - 1)_{\sigma(2) 2} \cdots (D + u - n + 1)_{\sigma(n) n},$$
where $(D + c)_{ij} = D_{ij} + c \delta_{ij}$. A function $\varphi$ *has the Capelli roots* $l = \{l_1, \ldots, l_n\}$ if $C(u) \varphi = \prod_{i=1}^n (u + l_i) \varphi$ for all $u \in \mathbb{C}$.

Lean: `Langlands.NumberFieldGL.capelliOperator` and `Langlands.NumberFieldGL.HasCapelliRoots`, definitions of the project

**Theorem 1.7.4 (Capelli).** For $D_{ij} = E_{ij} \in U(\mathfrak{gl}_n)$ the coefficients of the polynomial $C(u)$ lie in $Z(\mathfrak{g})$ and generate it. On the irreducible representation of highest weight $\lambda$,
$$C(u) = \prod_{i=1}^n (u + \lambda_i - i + 1) = \prod_{i=1}^n \left( u + h_i - \frac{n-1}{2} \right),$$
with $h = \lambda + \delta$.

Lean: not stated yet

*Proof sketch.* The centrality is the Capelli identity. A direct proof uses the Yangian: $C(u)$ is the quantum determinant of the matrix $(E + u)$ with the column-ordered product, and the quantum determinant is central, as in Molev, Chapter 7. To find the eigenvalue, apply $C(u)$ to a highest weight vector $x$ of weight $\lambda$. In the column order, the rightmost factor of each term is $(E + u - n + 1)_{\sigma(n) n}$, and the other factors only involve the columns $1, \ldots, n - 1$. Induction on $n$, with the commutation relations, shows that the terms with $\sigma \ne 1$ act by $0$ on $x$, and the diagonal term acts by $\prod_j (u - j + 1 + \lambda_j)$. Since the eigenvalue is a symmetric polynomial in the $h_i$ of degree $n$ in $u$ with leading coefficient $1$, its coefficients are the elementary symmetric functions of the $h_i - \frac{n-1}{2}$, and these generate $S(\mathfrak{h})^{S_n}$. So the coefficients of $C(u)$ generate $Z(\mathfrak{g})$ by Theorem 1.7.1. $\square$

So $\pi$ is algebraic if and only if at each infinite place the Capelli operators act on the smooth vectors of $\pi_v$ by $\prod_i (u + l_i)$ with integers $l_i$, and regular algebraic if, in addition, the $l_i$ are distinct. At a complex place there are two Capelli operators, built from the holomorphic and the antiholomorphic operators.

**Example 1.7.5 ($n = 1$).** For $n = 1$ the Capelli operator is $C(u) = u + D_{11}$. For a Hecke character $\chi$ with $\chi_v(x) = |x|^{t} \mathrm{sgn}(x)^\epsilon$ at a real place, $D_{11} \chi = t \chi$, since $\frac{d}{d\tau} |1 + \tau|^t = t$ at $\tau = 0$. So $\chi$ is algebraic at $v$ if and only if $t \in \mathbb{Z}$. At a complex place the two operators give $\chi_v(z) = z^p \bar z^q$ with $p, q \in \mathbb{Z}$. These are the algebraic Hecke characters, of type $A_0$ in the terms of Weil, as in Volume 3. For example, the norm $\|\cdot\|$ is algebraic and the character $\|\cdot\|^{1/2}$ is not.

Lean: `Langlands.NumberFieldGL.capelliOperator_one`, proved in the project

**Example 1.7.6 (modular forms).** Let $f$ be a newform of weight $k \ge 2$ and $\pi = \pi_f$. Then $\pi_\infty$ is the discrete series $D_k$, which has the infinitesimal character of $\mathrm{Sym}^{k-2} \mathbb{C}^2 \otimes |\det|^{-(k-2)/2}$. So $h = \{\frac{k-1}{2}, -\frac{k-1}{2}\}$ and the Capelli roots are $l = \{\frac{k}{2} - 1, -\frac{k}{2}\}$. They are distinct, and they are integers if and only if $k$ is even. So $\pi_f$ is regular algebraic for $k$ even, and $\pi_f \otimes |\det|^{1/2}$ is regular algebraic for $k$ odd. For $k = 2$ the roots are $\{0, -1\}$, the same as for the constant function on $GL_2$, which is the trivial representation with $\lambda = 0$.

**Example 1.7.7 (Maass forms).** Let $\varphi$ be a Maass cusp form on $GL_2$ over $\mathbb{Q}$ with Laplace eigenvalue $\frac14 + r^2$, $r \ge 0$, and trivial central character. Then $\pi_\infty$ is a principal series $I(|\cdot|^{ir} \mathrm{sgn}^\epsilon, |\cdot|^{-ir} \mathrm{sgn}^\epsilon)$, the infinitesimal character is $h = \{ir, -ir\}$, and $l = \{ir - \frac12, -ir - \frac12\}$. So $\pi$ is never algebraic. For $r = 0$, the twist $\pi \otimes |\det|^{1/2}$ has $l = \{0, 0\}$: it is algebraic, and it is not regular. The Maass forms of weight $0$ attached by Maass to the class group characters of real quadratic fields, and the forms attached to even two-dimensional Artin representations, are of this kind. For the twist $\pi \otimes |\det|^{1/2}$ the Hecke polynomial below has the roots $\alpha_p, \beta_p$, the Satake parameters of $\pi$ itself. For the forms of Artin representations they are the eigenvalues of $\rho(\mathrm{Frob}_p)$, and so they are roots of unity.

### The Hecke polynomial

**Definition 1.7.8 (Hecke polynomial).** Let $\varphi$ be a Hecke eigenvector at a finite place $v$ with the eigenvalues $\lambda_1, \ldots, \lambda_n$ of $T_{v,1}, \ldots, T_{v,n}$. Its *Hecke polynomial* at $v$ is
$$H_v(X) = X^n + \sum_{i=1}^n (-1)^i q_v^{i(i-1)/2} \lambda_i X^{n-i}.$$

Lean: `Langlands.NumberFieldGL.heckePolynomial`, a definition of the project

**Proposition 1.7.9.** The roots of $H_v$ are the numbers $q_v^{(n-1)/2} \alpha_j$, where the $\alpha_j$ are the Satake parameters of Definition 1.4.7. These are the Satake parameters of $\pi_v \otimes |\det|_v^{(1-n)/2}$. For $n = 2$, $H_v(X) = X^2 - \lambda_1 X + q_v \lambda_2$.

Lean: `Langlands.NumberFieldGL.heckePolynomial_two`, proved in the project, for the last claim

*Proof.* By Proposition 1.4.4, $\lambda_i = q_v^{i(n-i)/2} e_i(\alpha)$. So the coefficient of $X^{n-i}$ is $(-1)^i q_v^{i(i-1)/2 + i(n-i)/2} e_i(\alpha) = (-1)^i q_v^{i(n-1)/2} e_i(\alpha) = (-1)^i e_i(q_v^{(n-1)/2} \alpha)$. The twist by $|\det|^{(1-n)/2}$ multiplies each $\chi_j(\varpi)$ by $|\varpi|^{(1-n)/2} = q_v^{(n-1)/2}$. $\square$

For a weight 2 newform with trivial character, $\lambda_1 = a_p$ and $\lambda_2 = 1$ by Example 1.4.9, and $H_p(X) = X^2 - a_p X + p$. This is the characteristic polynomial of the arithmetic Frobenius on the Galois representation of Eichler and Shimura in Volume 4. In general the coefficients of $H_v$ contain only integral powers of $q_v$, and Clozel's twist makes them algebraic, by the next theorem.

**Theorem 1.7.10 (Clozel).** Let $\pi$ be a regular algebraic cuspidal automorphic representation of $GL_n(\mathbb{A}_F)$. Then there is a number field $E \subset \mathbb{C}$ such that, for each finite place $v$ where $\pi$ is unramified, the coefficients of the Hecke polynomial $H_v$ lie in $E$.

Lean: not stated yet

*Proof sketch.* Let $\xi$ be the irreducible algebraic representation of $\mathrm{Res}_{F/\mathbb{Q}} GL_n$ whose infinitesimal character is the dual of that of $\pi_\infty$, which exists because $\pi$ is regular algebraic. Clozel shows, using the classification of the generic unitary representations of $GL_n(\mathbb{R})$ and $GL_n(\mathbb{C})$ and a computation of the relative Lie algebra cohomology, that $H^*(\mathfrak{g}, K_\infty; \pi_\infty \otimes \xi) \ne 0$. So the finite part of $\pi$ occurs in the cuspidal cohomology $H^*_{\mathrm{cusp}}(S_{K}, \mathcal{V}_\xi)$ of the locally symmetric space $S_K = GL_n(F) \backslash GL_n(\mathbb{A}) / K_\infty K$ with coefficients in the local system of $\xi$. This is a Hecke-stable summand of the cohomology, and Clozel proves that it is defined over $\mathbb{Q}$ with the rational structure of $\xi$. The Hecke operators with the integral normalization preserve a lattice in the cohomology. So the eigenvalues are algebraic, and $\sigma \in \mathrm{Aut}(\mathbb{C})$ sends $\pi^\infty$ to the finite part of another such representation. The finiteness of the cohomology gives the number field $E$. $\square$

For the Maass forms of the last example with $r \neq 0$, no such field is expected, and for $r = 0$ the theorem does not apply. The Galois representations of the second case are Artin representations, by the conjecture of Section 2.5.

**Remark 1.7.11 (algebraic forms in the Lean project).** The Lean condition is on a form, not on a representation. `Langlands.NumberFieldGL.IsAlgebraicForm φ` says that $\varphi$ is smooth at the infinite places, in the sense of `Langlands.NumberFieldGL.IsArchSmooth`, and that at each real place it has the Capelli roots $l$ for a multiset $l$ of integers, and at each complex place it has such roots for the holomorphic and for the antiholomorphic operators. The regular form asks that the multisets have no repeated element. The operators $D_{ij}$ are the derivatives of the right translation along $1 + tE_{ij}$ at a real place, and along $1 + tE_{ij}$ and $1 + itE_{ij}$ at a complex place, combined to the holomorphic and the antiholomorphic generators. These are the operators of $\mathfrak{g}_v$, so a smooth vector of $\pi$ has the Capelli roots of $\pi_v$. The smoothness is needed: Mathlib's `deriv` is $0$ at a point where a function is not differentiable, and without the smoothness a nowhere differentiable continuous form would have the Capelli roots $\{0, -1, \ldots, 1 - n\}$. A class is algebraic if it contains an algebraic form (`Langlands.NumberFieldGL.IsAlgebraicClass`). Since the smooth $K_\infty$-finite vectors of $\pi$ are dense and contain vectors of some level $K(N)$, this is Clozel's condition on $\pi$. The conditions are invariant under $l \mapsto -l$ and under the shift of all $l_i$ by $n - 1$, so they do not depend on the side of the action or on the passage to the contragredient.
