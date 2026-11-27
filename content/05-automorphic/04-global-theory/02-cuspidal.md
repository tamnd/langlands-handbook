---
title: Cuspidal automorphic representations
nodes: []
sources: [JL70]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Cuspidal automorphic representations

This section defines the cuspidal automorphic representations of $GL_2(\mathbb{A})$ and proves the first properties of their local components. The main point is that the components are unitary, that none of them is one-dimensional, and that the component at an unramified prime is described by two complex numbers, the Satake parameters. We compute the Hecke eigenvalues of the spherical vector in terms of these parameters.

### Definitions

Let $\omega$ be a unitary character of $\mathbb{Q}^\times \backslash \mathbb{A}^\times$. Chapter 2 defines the space $\mathcal{A}_0(\omega)$ of cusp forms with central character $\omega$. Its elements are the smooth functions $\phi$ on $GL_2(\mathbb{Q}) \backslash GL_2(\mathbb{A})$ that are $K_\infty$-finite, $\mathcal{Z}(\mathfrak{g})$-finite and of moderate growth, that satisfy $\phi(zg) = \omega(z)\phi(g)$ for $z \in Z(\mathbb{A})$, and whose constant terms vanish:
$$\int_{\mathbb{Q} \backslash \mathbb{A}} \phi(n(x)g)\,dx = 0 \quad \text{for all } g \in GL_2(\mathbb{A}).$$
The group $GL_2(\mathbb{A}_f)$ acts on $\mathcal{A}_0(\omega)$ by right translation, and $(\mathfrak{g}, K_\infty)$ acts by differentiation and right translation. A cusp form is rapidly decreasing on a Siegel domain (Chapter 2), so it is bounded and square-integrable modulo the centre, and the Petersson product
$$\langle \phi_1, \phi_2 \rangle = \int_{Z(\mathbb{A})GL_2(\mathbb{Q}) \backslash GL_2(\mathbb{A})} \phi_1(g)\overline{\phi_2(g)}\,dg$$
converges. It is invariant under the action, because $\omega$ is unitary.

**Definition 4.2.1 (cuspidal automorphic representation).** A *cuspidal automorphic representation* of $GL_2(\mathbb{A})$ with central character $\omega$ is an irreducible $(\mathfrak{g}, K_\infty) \times GL_2(\mathbb{A}_f)$-submodule of $\mathcal{A}_0(\omega)$. We say that an abstract irreducible module is cuspidal automorphic if it is isomorphic to such a submodule.

We recall the main structural result of Chapter 2.

**Theorem 4.2.2 (decomposition of the cuspidal spectrum).** The space $\mathcal{A}_0(\omega)$ is the algebraic direct sum of irreducible admissible submodules $V_\pi$. Each irreducible module occurs in $\mathcal{A}_0(\omega)$ at most once.

Lean: not formalized

The first statement comes from the compactness of the operators $\phi \mapsto \phi * f$ on $L^2_0$, and the second from the uniqueness of Whittaker models. Both are in Chapter 2, and in [JL70], Chapter II, and [Bum97], Chapter 3. For a cuspidal automorphic representation $\pi$ we write $V_\pi$ for the unique subspace of $\mathcal{A}_0(\omega)$ on which it is realized. A cusp form $\phi \ne 0$ that is an eigenvector for almost all Hecke algebras $\mathcal{H}(G_p, K_p)$ need not lie in a single $V_\pi$ a priori, but it does by strong multiplicity one (Section 4.4).

### The local components

**Proposition 4.2.3 (local components of a cuspidal representation).** Let $\pi$ be a cuspidal automorphic representation with central character $\omega$, and let $\pi = \bigotimes'_v\pi_v$ be its decomposition by Theorem 4.1.6. Then:
1. $\pi_v$ has central character $\omega_v$ for each $v$;
2. $\pi_p$ is unitary for each prime $p$, and $\pi_\infty$ is the module of $K_\infty$-finite vectors of a unitary representation of $GL_2(\mathbb{R})$;
3. $\pi_p$ is unramified for almost all $p$;
4. $\pi_v$ is infinite-dimensional for each $v$.

Lean: not formalized

*Proof.* Part 1 holds since $Z(\mathbb{Q}_v)$ acts on $V_\pi$ by $\omega_v$ and the decomposition is equivariant. Part 3 is part of Theorem 4.1.6. For part 2, the Petersson product restricted to a pure tensor line $\pi_p \otimes x^p$, with $x^p$ a fixed vector away from $p$, gives a positive definite invariant inner product on $\pi_p$. At infinity the same argument gives an invariant inner product on the $(\mathfrak{g}, K_\infty)$-module, and the completion of $V_\pi$ for the Petersson norm is a unitary representation of $GL_2(\mathbb{A})$ whose $K$-finite vectors give $\pi_\infty$.

Part 4 is the substance. Suppose that $\pi_v$ is one-dimensional for some place $v$. Then $\pi_v = \chi \circ \det$ for a character $\chi$ of $\mathbb{Q}_v^\times$ when $v$ is finite, and $\mathfrak{sl}_2$ acts by $0$ on $\pi_\infty$ when $v = \infty$. In both cases the group $SL_2(\mathbb{Q}_v)$ acts trivially on $V_\pi$. At infinity this uses the fact that $SL_2(\mathbb{R})$ is connected and that the elements of $V_\pi$ are smooth, so that a function killed by $\mathfrak{sl}_2$ is right invariant under $SL_2(\mathbb{R})$. Let $\phi \in V_\pi$ and $g \in GL_2(\mathbb{A})$. For $h \in SL_2(\mathbb{Q}_v)$ the element $g^{-1}hg$ has component $g_v^{-1}hg_v \in SL_2(\mathbb{Q}_v)$ at $v$, since $SL_2(\mathbb{Q}_v)$ is normal in $GL_2(\mathbb{Q}_v)$, and component 1 at the other places. So
$$\phi(hg) = \phi(g \cdot g^{-1}hg) = \phi(g).$$
By strong approximation for $SL_2$ (Chapter 1), $SL_2(\mathbb{Q})SL_2(\mathbb{Q}_v)$ is dense in $SL_2(\mathbb{A})$. Let $h \in SL_2(\mathbb{A})$ be the limit of $\gamma_jh_j$ with $\gamma_j \in SL_2(\mathbb{Q})$ and $h_j \in SL_2(\mathbb{Q}_v)$. Since $\phi$ is continuous and left invariant under $GL_2(\mathbb{Q})$,
$$\phi(hg) = \lim_j \phi(\gamma_jh_jg) = \lim_j \phi(h_jg) = \phi(g).$$
So $\phi$ is left invariant under $SL_2(\mathbb{A})$, and in particular under $N(\mathbb{A})$. Then the constant term of $\phi$ at $g$ is $\phi(g)\,\mathrm{vol}(\mathbb{Q} \backslash \mathbb{A}) = \phi(g)$. It vanishes, so $\phi = 0$. This holds for each $\phi \in V_\pi$, which is a contradiction. $\square$

The functions $\chi(\det g)$ are automorphic forms but not cusp forms; they form the residual spectrum of Chapter 2. At an unramified prime, part 4 excludes the Satake parameters $\{\chi(p)p^{1/2}, \chi(p)p^{-1/2}\}$ of the one-dimensional representation $\chi \circ \det$.

By part 2 and Chapter 3, each $\pi_p$ is an irreducible unitary admissible representation of $G_p$, so it belongs to one of these classes: a principal series $\chi_1 \times \chi_2$ with $\chi_1, \chi_2$ unitary; a complementary series $\chi|\cdot|^\sigma \times \chi|\cdot|^{-\sigma}$ with $\chi$ unitary and $0 < \sigma < 1/2$; a twist $\mu\mathrm{St}$ of the Steinberg representation with $\mu$ unitary; a supercuspidal representation; or a one-dimensional representation. The last class is excluded by part 4. The list of the unitary representations is in [Bum97], Chapter 4, and in Volume 6, Chapter 1. The Ramanujan conjecture of Section 4.7 says that the complementary series does not occur either.

### Satake parameters and Hecke eigenvalues

Let $\pi_p$ be an irreducible unramified representation of $G_p$ that is infinite-dimensional. By Chapter 3 it is an irreducible principal series $\chi_1 \times \chi_2$ with $\chi_1, \chi_2$ unramified, and it determines the unordered pair $\{\chi_1, \chi_2\}$.

**Definition 4.2.4 (Satake parameters).** The *Satake parameters* of an unramified principal series $\pi_p = \chi_1 \times \chi_2$ are the numbers $\alpha_p = \chi_1(p)$ and $\beta_p = \chi_2(p)$, as an unordered pair. Its *Satake matrix* is $\mathrm{diag}(\alpha_p, \beta_p) \in GL_2(\mathbb{C})$, up to conjugacy. For a cuspidal automorphic representation $\pi$ and a prime $p$ where $\pi_p$ is unramified, these are the Satake parameters of $\pi$ at $p$.

By Proposition 4.2.3, part 1, $\alpha_p\beta_p = \omega_p(p)$. If $\omega$ is trivial, then $\alpha_p\beta_p = 1$. This is the unitary normalization of Volume 0: in it, a unitary unramified principal series has parameters of absolute value 1. The arithmetic normalization of Volume 4 multiplies both parameters by $p^{(k-1)/2}$.

**Lemma 4.2.5 (the coset decomposition).** There is a disjoint union
$$K_p\,a(p)\,K_p = \bigsqcup_{b = 0}^{p - 1}\begin{pmatrix} p & b \\ 0 & 1 \end{pmatrix}K_p \ \sqcup\ \begin{pmatrix} 1 & 0 \\ 0 & p \end{pmatrix}K_p.$$

Lean: not formalized

*Proof.* The double coset is the set of matrices in $M_2(\mathbb{Z}_p)$ whose determinant has valuation 1. Such a matrix $g$ is not divisible by $p$, so its elementary divisors are $1$ and $p$. By column operations, that is right multiplication by $K_p$, we can bring $g$ into upper triangular form $\begin{pmatrix} p^i & b \\ 0 & p^j \end{pmatrix}$ with $i + j = 1$. Adding a multiple of the first column to the second changes $b$ by a multiple of $p^i$, so we can take $b$ modulo $p^i$. This gives the $p + 1$ matrices of the lemma. They lie in different cosets: if $g^{-1}g' \in K_p$ for two of them, then the lower left entry is $0$ and the diagonal entries are units, which forces $i = i'$ and $b \equiv b' \bmod p^i$. $\square$

Let $T_p \in \mathcal{H}(G_p, K_p)$ be the characteristic function of $K_pa(p)K_p$ and $R_p$ the characteristic function of $pK_p$. On a vector $v$ fixed by $K_p$, Lemma 4.2.5 gives
$$\pi(T_p)v = \sum_{b = 0}^{p - 1}\pi\begin{pmatrix} p & b \\ 0 & 1 \end{pmatrix}v + \pi\begin{pmatrix} 1 & 0 \\ 0 & p \end{pmatrix}v, \qquad \pi(R_p)v = \pi(p)v.$$

**Proposition 4.2.6 (Hecke eigenvalues of the spherical vector).** Let $\pi_p = \chi_1 \times \chi_2$ be an unramified principal series with Satake parameters $\alpha, \beta$, and let $v \in \pi_p^{K_p}$ be nonzero. Then
$$\pi_p(T_p)v = p^{1/2}(\alpha + \beta)v, \qquad \pi_p(R_p)v = \alpha\beta v.$$

Lean: `Langlands.satakePolynomial`

*Proof.* Realize $\pi_p$ on the functions $f$ on $G_p$ with $f(n(x)\,\mathrm{diag}(a, d)\,g) = \chi_1(a)\chi_2(d)|a/d|^{1/2}f(g)$. By the Iwasawa decomposition $G_p = B(\mathbb{Q}_p)K_p$, the spherical vector is the function $f^\circ$ with $f^\circ(bk) = \chi_1(a)\chi_2(d)|a/d|^{1/2}$ for $b = n(x)\,\mathrm{diag}(a, d)$. By Corollary 4.1.5, $\pi_p(T_p)f^\circ = cf^\circ$ for a scalar $c$, and $c = (\pi_p(T_p)f^\circ)(1)$ since $f^\circ(1) = 1$. Now
$$c = \sum_{b = 0}^{p - 1}f^\circ\begin{pmatrix} p & b \\ 0 & 1 \end{pmatrix} + f^\circ\begin{pmatrix} 1 & 0 \\ 0 & p \end{pmatrix} = p \cdot \chi_1(p)p^{-1/2} + \chi_2(p)p^{1/2} = p^{1/2}(\alpha + \beta),$$
since $\begin{pmatrix} p & b \\ 0 & 1 \end{pmatrix} = n(b)\,\mathrm{diag}(p, 1)$ with $|p| = p^{-1}$. The element $p = \mathrm{diag}(p, p)$ acts by $\chi_1\chi_2(p) = \alpha\beta$. $\square$

So $\alpha_p$ and $\beta_p$ are the roots of $X^2 - p^{-1/2}\lambda_1X + \lambda_2$, where $\lambda_1$ and $\lambda_2$ are the eigenvalues of $T_p$ and $R_p$. This is the polynomial `Langlands.satakePolynomial` of the Lean project for $n = 2$, with $q = p$, and the multiset of its roots is `Langlands.satake`. For the trivial representation, which is a quotient of $|\cdot|^{1/2} \times |\cdot|^{-1/2}$, the computation gives $\lambda_1 = p + 1$, the number of cosets, and the parameters $p^{\pm 1/2}$.

**Remark 4.2.7 (comparison with the classical operator).** Let $f \in S_k(\Gamma_0(N))$ be an eigenform of the classical operator $T_p$ of Volume 4 with eigenvalue $a_p(f)$, and let $p \nmid N$. Chapter 1 attaches to $f$ the function $\phi_f(\gamma g_\infty k_f) = (f|_kg_\infty)(i)$, for $\gamma \in GL_2(\mathbb{Q})$, $g_\infty \in GL_2(\mathbb{R})^+$ and $k_f \in K_0(N)$, where $(f|_kg)(\tau) = \det(g)^{k/2}(c\tau + d)^{-k}f(g\tau)$. With this normalization of the slash operator, the adelic operator $T_p$ at $p$ satisfies $\pi(T_p)\phi_f = p^{1 - k/2}\phi_{T_pf}$, where $\pi$ denotes right translation (Exercise 2). So if $\phi_f$ lies in a cuspidal representation $\pi$, the Satake parameters of $\pi$ at $p$ satisfy
$$\alpha_p + \beta_p = p^{-(k-1)/2}a_p(f), \qquad \alpha_p\beta_p = 1.$$
In terms of the arithmetic parameters $\alpha_p', \beta_p'$ of Volume 4, Section 2.3, the roots of $X^2 - a_p(f)X + p^{k-1}$, this reads $\alpha_p' = p^{(k-1)/2}\alpha_p$ and $\beta_p' = p^{(k-1)/2}\beta_p$.

**Example 4.2.8 (the parameters of $\Delta$ and of $f_{11}$).** For $\Delta$ and $p = 2$ we have $\tau(2) = -24$, so $\alpha_2 + \beta_2 = -24 \cdot 2^{-11/2} = -3/(4\sqrt{2}) \approx -0.530$. This number lies in $[-2, 2]$, so $\alpha_2$ and $\beta_2$ are complex conjugate of absolute value 1. For $f_{11}$ and $p = 2$, $a_2 = -2$, so $\alpha_2 + \beta_2 = -\sqrt{2}$ and $\alpha_2, \beta_2 = e^{\pm 3\pi i/4}$, two primitive 8th roots of unity. For $p = 3$, $a_3 = -1$, so $\alpha_3 + \beta_3 = -1/\sqrt{3}$, and $\alpha_3 = e^{i\theta}$ with $\cos\theta = -1/(2\sqrt{3})$. In both examples the parameters have absolute value 1. Section 4.7 explains that this is Deligne's theorem.

**Remark 4.2.9 (the Lean form of cusp forms).** The Lean project defines `Langlands.IsCuspForm` for $GL_n$ over a number field $K$. It does not ask for $K_\infty$-finiteness or $\mathcal{Z}(\mathfrak{g})$-finiteness. The predicates `Langlands.IsSphericalAt` and `Langlands.IsHeckeEigenAt` express that a function is invariant under $GL_n(\mathcal{O}_v)$ and an eigenvector of the operators `Langlands.adelicHeckeOperator` at $v$, which are built from the double cosets `Langlands.HeckeCoset`. The theorem `Langlands.isCuspForm_one` says that the constant function 1 is a cusp form on $GL_1$, where the cuspidal condition is empty.
