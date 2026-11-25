---
title: Poisson summation and the Riemann-Roch theorem
nodes: []
sources: [CF67]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Poisson summation and the Riemann-Roch theorem

The global part of Tate's thesis has one analytic input. It is the Poisson summation formula for the discrete cocompact subgroup $F$ of $\mathbb{A}_F$. Tate wrote it in a form with an idele $a$ as parameter, and he called this form the Riemann-Roch theorem. This section proves both. Let $F$ be a number field. The additive character is $\psi = \prod_v \psi_v$, with the standard local characters of Section 5.1. The measure $dx = \prod_v dx_v$ on $\mathbb{A}_F$ is the product of the self-dual measures. This is the Tamagawa measure of Volume 1, Section 3.3. For a finite place $v$ let $d_v = d(\psi_v)$. Then $d_v = v(\mathfrak{D}_{F/\mathbb{Q}})$, so $d_v = 0$ for almost all $v$, and $\prod_v q_v^{d_v} = N(\mathfrak{D}_{F/\mathbb{Q}}) = |d_F|$.

### Adelic Fourier analysis

**Definition 5.3.1 (adelic Schwartz-Bruhat functions).** A *factorizable* Schwartz-Bruhat function on $\mathbb{A}_F$ is a function $f(x) = \prod_v f_v(x_v)$, where $f_v \in \mathcal{S}(F_v)$ for all $v$ and $f_v = 1_{\mathcal{O}_v}$ for almost all finite $v$. We write $f = \otimes_v f_v$. The space $\mathcal{S}(\mathbb{A}_F)$ of *Schwartz-Bruhat functions* is the space of finite linear combinations of these functions. The *Fourier transform* of $f \in \mathcal{S}(\mathbb{A}_F)$ is
$$\hat f(y) = \int_{\mathbb{A}_F} f(x) \psi(xy) \, dx.$$

For $x \in \mathbb{A}_F$ the product $\prod_v f_v(x_v)$ is finite, because $x_v \in \mathcal{O}_v$ and $f_v(x_v) = 1$ for almost all $v$. Let $f = \otimes_v f_v$, and let $S$ be a finite set of places that contains the infinite places, the places with $f_v \ne 1_{\mathcal{O}_v}$ and the places with $d_v \ne 0$. As in the proof of Proposition 3.3.2 of Volume 1, the integral over $\mathbb{A}_F$ is the limit of the integrals over the open subgroups $\prod_{v \in T} F_v \times \prod_{v \notin T} \mathcal{O}_v$ with $T \supset S$ finite. On each of them the integrand is a product, and $\mathrm{vol}(\mathcal{O}_v) = 1$ for $v \notin S$. Thus
$$\hat f = \otimes_v \hat f_v,$$
where the transform at $v$ is taken for $\psi_v$ and $dx_v$. For $v \notin S$, $\hat f_v = 1_{\mathcal{O}_v}$ by Section 5.1. So $\hat f$ is again in $\mathcal{S}(\mathbb{A}_F)$. Proposition 5.1.4 at each place gives $\hat{\hat f}(x) = f(-x)$.

**Proposition 5.3.2 (self-duality of $\mathbb{A}_F$).**
1. The map $a \mapsto \psi_a$, with $\psi_a(x) = \psi(ax)$, is an isomorphism of topological groups from $\mathbb{A}_F$ to its Pontryagin dual.
2. The character $\psi$ is trivial on $F$. A character $\psi_a$ is trivial on $F$ if and only if $a \in F$. Thus the characters of $\mathbb{A}_F / F$ are the maps $x \mapsto \psi(\xi x)$ with $\xi \in F$.

Lean: not stated yet

*Proof.* Let $\chi$ be a character of $\mathbb{A}_F$. By Proposition 3.1.4 of Volume 1, its restriction $\chi_v$ to $F_v$ is trivial on $\mathcal{O}_v$ for almost all $v$, and $\chi = \prod_v \chi_v$. By Proposition 5.1.2, $\chi_v = (\psi_v)_{a_v}$ for a unique $a_v \in F_v$. If $\chi_v$ is trivial on $\mathcal{O}_v$ and $d_v = 0$, then $\psi_v$ is trivial on $a_v \mathcal{O}_v$, so $a_v \in \mathcal{O}_v$. Thus $a = (a_v)$ is an adele, and $\chi = \psi_a$. The map is injective by Proposition 5.1.2. The proof that it is a homeomorphism is in [CF67], Chapter XV, Section 4.1.

The character $\psi$ is trivial on $F$ by [CF67], Chapter XV, Lemma 4.1.5, as stated in Volume 1, Section 3.3. Let $D$ be the set of $a \in \mathbb{A}_F$ with $\psi_a$ trivial on $F$. If $a \in D$ and $b \in F$, then $\psi_{ab}(\xi) = \psi_a(b\xi) = 1$ for $\xi \in F$. So $D$ is an $F$-vector space, and $F \subset D$. By Pontryagin duality, the characters of $\mathbb{A}_F$ that are trivial on $F$ form the dual of $\mathbb{A}_F / F$, with its topology. The group $\mathbb{A}_F / F$ is compact by Theorem 3.2.4 of Volume 1, so its dual is discrete. By part 1, $D$ is discrete in $\mathbb{A}_F$. Choose an open neighbourhood $U$ of 0 in $\mathbb{A}_F$ with $U \cap D = \{0\}$. If $u + \xi \in D$ with $u \in U$ and $\xi \in F$, then $u \in D \cap U$, so $u = 0$. Thus the image of $U$ in $\mathbb{A}_F / F$ meets $D / F$ only in 0, and $D / F$ is a discrete subgroup of the compact group $\mathbb{A}_F / F$. So $D / F$ is finite. A finite $F$-vector space is 0, so $D = F$. $\square$

### The Poisson summation formula

**Lemma 5.3.3 (convergence of the lattice sums).** Let $f \in \mathcal{S}(\mathbb{A}_F)$.
1. For each compact set $C \subset \mathbb{A}_F$, the sum $\sum_{\xi \in F} \sup_{x \in C} |f(x + \xi)|$ is finite.
2. For $a \in J_F$ the function $f_a(x) = f(ax)$ is in $\mathcal{S}(\mathbb{A}_F)$, and $\hat f_a(y) = |a|_\mathbb{A}^{-1} \hat f(a^{-1} y)$.

Lean: not stated yet

*Proof.* For part 1 we may assume $f = f_\infty \otimes f_{\mathrm{fin}}$, with $f_\infty \in \mathcal{S}(F_\infty)$ and $f_{\mathrm{fin}} = 1_{b + \mathfrak{m}}$. Here $F_\infty = \prod_{v \mid \infty} F_v \cong \mathbb{R}^n$ with $n = [F : \mathbb{Q}]$, $b$ is a finite adele, and $\mathfrak{m} = \prod_v \mathfrak{p}_v^{m_v} \mathcal{O}_v$ with $m_v = 0$ for almost all $v$. Every $f$ is a finite linear combination of such functions, because each $f_v$ at a finite place is a finite linear combination of functions $1_{b_v + \mathfrak{p}_v^{m}}$. We may assume $C = C_\infty \times C_{\mathrm{fin}}$ with both factors compact. If $f(x + \xi) \ne 0$ for some $x \in C$, then $\xi$ lies in the compact set $b + \mathfrak{m} - C_{\mathrm{fin}}$ of finite adeles. This set is covered by finitely many cosets $c_j + \mathfrak{m}$. The set of $\xi \in F$ in such a coset is empty or a coset $\xi_j + M$, where $M = F \cap \mathfrak{m}$ is a fractional ideal of $F$. The fractional ideal $M$ is a lattice in $F_\infty$. So the sum is at most
$$\sum_j \sum_{\mu \in M} \sup_{y \in C_\infty} |f_\infty(y + \xi_j + \mu)|.$$
Since $f_\infty$ is a Schwartz function, $|f_\infty(y)| \le c (1 + |y|)^{-n-1}$, and the sum of $(1 + |y + \mu|)^{-n-1}$ over a lattice $M$ is bounded for $y$ in a compact set. So the sum is finite.

For part 2 let $f = \otimes_v f_v$. Then $f_a = \otimes_v f_v(a_v \, \cdot)$. For almost all $v$ we have $a_v \in \mathcal{O}_v^\times$ and $f_v = 1_{\mathcal{O}_v}$, and then $f_v(a_v x) = 1_{\mathcal{O}_v}(x)$. So $f_a \in \mathcal{S}(\mathbb{A}_F)$. Multiplication by $a$ multiplies the Haar measure of $\mathbb{A}_F$ by $|a|_\mathbb{A}$, by Volume 1, Section 3.3. The substitution $u = ax$ gives
$$\hat f_a(y) = \int_{\mathbb{A}_F} f(ax) \psi(xy) \, dx = |a|_\mathbb{A}^{-1} \int_{\mathbb{A}_F} f(u) \psi(a^{-1} u y) \, du = |a|_\mathbb{A}^{-1} \hat f(a^{-1} y). \quad \square$$

**Theorem 5.3.4 (Poisson summation).** For $f \in \mathcal{S}(\mathbb{A}_F)$,
$$\sum_{\xi \in F} f(\xi) = \sum_{\xi \in F} \hat f(\xi),$$
and both sums converge absolutely.

Lean: not stated yet

*Proof.* Let $\varphi(x) = \sum_{\xi \in F} f(x + \xi)$. By Lemma 5.3.3 the sum converges uniformly on compact sets, so $\varphi$ is continuous. It is invariant under $F$, so it is a continuous function on the compact group $\mathbb{A}_F / F$. Give $\mathbb{A}_F / F$ the quotient of the Tamagawa measure by the counting measure on $F$. Its volume is 1, by Theorem 3.3.3 of Volume 1. By Proposition 5.3.2 the characters of $\mathbb{A}_F / F$ are $x \mapsto \psi(\eta x)$ with $\eta \in F$. The Fourier coefficient of $\varphi$ at $\eta$ is
$$\int_{\mathbb{A}_F / F} \varphi(x) \psi(-\eta x) \, dx = \int_{\mathbb{A}_F / F} \sum_{\xi \in F} f(x + \xi) \psi(-\eta (x + \xi)) \, dx = \int_{\mathbb{A}_F} f(x) \psi(-\eta x) \, dx = \hat f(-\eta).$$
In the first step we used $\psi(\eta \xi) = 1$. The second step unfolds the sum. It is valid because $\int_{\mathbb{A}_F / F} \sum_\xi |f(x + \xi)| \, dx = \int_{\mathbb{A}_F} |f| \, dx$ is finite. By Lemma 5.3.3 for $\hat f$, the sum $\sum_\eta |\hat f(-\eta)|$ is finite. So the series $\varphi_1(x) = \sum_{\eta \in F} \hat f(-\eta) \psi(\eta x)$ converges uniformly to a continuous function on $\mathbb{A}_F / F$. By the orthogonality of characters, $\varphi_1$ has the same Fourier coefficients as $\varphi$. Two continuous functions on a compact abelian group with the same Fourier coefficients are equal, because the characters span a dense subspace of the continuous functions. So $\varphi = \varphi_1$. At $x = 0$ this is $\sum_\xi f(\xi) = \sum_\eta \hat f(-\eta) = \sum_\eta \hat f(\eta)$. $\square$

### The Riemann-Roch theorem

**Theorem 5.3.5 (Tate's Riemann-Roch theorem).** For $f \in \mathcal{S}(\mathbb{A}_F)$ and $a \in J_F$,
$$\sum_{\xi \in F} f(a \xi) = \frac{1}{|a|_\mathbb{A}} \sum_{\xi \in F} \hat f(a^{-1} \xi).$$

Lean: not stated yet

*Proof.* Apply Theorem 5.3.4 to the function $f_a$ of Lemma 5.3.3, and use the formula for $\hat f_a$ in part 2 of that lemma. $\square$

This is [CF67], Chapter XV, Theorem 4.2.1. In the proof of the global functional equation we use it in the form
$$\sum_{\xi \in F^\times} f(a \xi) = \frac{1}{|a|_\mathbb{A}} \sum_{\xi \in F^\times} \hat f(a^{-1} \xi) + \frac{\hat f(0)}{|a|_\mathbb{A}} - f(0), \tag{5.3.1}$$
which is the same identity with the terms $\xi = 0$ moved to the right side.

**Example 5.3.6 (the theta function).** Let $F = \mathbb{Q}$, and let $f = f_\infty \otimes \bigotimes_p 1_{\mathbb{Z}_p}$ with $f_\infty(x) = e^{-\pi x^2}$. Each factor is its own transform, so $\hat f = f$. Let $t > 0$, and let $a$ be the idele with $a_\infty = t^{1/2}$ and $a_p = 1$ for all $p$, so $|a|_\mathbb{A} = t^{1/2}$. For $\xi \in \mathbb{Q}$ the value $f(a\xi)$ is 0 unless $\xi \in \mathbb{Z}_p$ for all $p$, that is, $\xi \in \mathbb{Z}$. Then $f(a \xi) = e^{-\pi t \xi^2}$. Theorem 5.3.5 becomes
$$\theta(t) = t^{-1/2} \theta(1/t), \qquad \theta(t) = \sum_{n \in \mathbb{Z}} e^{-\pi n^2 t}.$$
This is the transformation formula that Riemann used for his functional equation of $\zeta(s)$. For a number field $F$ and Gaussians at the infinite places, the same choice gives the theta series of the lattice $\mathcal{O}_F$ in $F_\infty$, which Hecke used.

**Remark 5.3.7 (the name).** Let $F$ be instead a function field of one variable over a finite field, and let $D$ be a divisor. Let $f$ be the characteristic function of the set of adeles $x$ with $v(x_v) \ge -n_v$ for all $v$, where $D = \sum n_v v$. Then $\sum_{\xi \in F} f(\xi)$ is the number of elements of the Riemann-Roch space $L(D)$. The transform of $f$ is a multiple of the characteristic function of a similar set, which belongs to the divisor $\kappa - D$ for a canonical divisor $\kappa$ attached to $\psi$. Then the Poisson summation formula is the Riemann-Roch theorem for the curve, in the form $q^{\ell(D)} = q^{\deg D + 1 - g} q^{\ell(\kappa - D)}$. For a number field the infinite places carry Gaussians instead of characteristic functions, and the counts become theta series.
