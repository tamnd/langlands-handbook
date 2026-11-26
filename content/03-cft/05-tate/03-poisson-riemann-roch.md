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

### Poisson summation on a lattice

Hecke worked with lattices in $F_\infty$, not with $\mathbb{A}_F / F$. The classical form of the Poisson summation formula is a statement about a lattice in a Euclidean space. It is the form that the Lean project proves. Let $V$ be a real inner product space of dimension $n$, with the Lebesgue measure $dv$ for which an orthonormal cube has volume 1. The Fourier transform is $\hat f(w) = \int_V f(v) e^{-2\pi i \langle v, w \rangle} \, dv$, so $\hat f(w) = \int_V f(v) \psi_\mathbb{R}(\langle v, w \rangle) \, dv$ with the character $\psi_\mathbb{R}$ of Section 5.1. A *lattice* $L \subset V$ is a discrete subgroup that spans $V$. Its *covolume* $\mathrm{covol}(L)$ is the volume of $V / L$, and its *dual lattice* is $L^\vee = \{\mu \in V : \langle \mu, \ell \rangle \in \mathbb{Z} \text{ for all } \ell \in L\}$.

**Proposition 5.3.8 (Poisson summation on a lattice).** Let $L \subset V$ be a lattice. Let $f : V \to \mathbb{C}$ be continuous, and assume that there are $C > 0$ and an integer $N > n$ with $|f(v)| \le C (1 + |v|)^{-N}$ for all $v$. Assume that $\sum_{\mu \in L^\vee} |\hat f(\mu)|$ is finite. Then for each $x \in V$,
$$\sum_{\ell \in L} f(x + \ell) = \frac{1}{\mathrm{covol}(L)} \sum_{\mu \in L^\vee} \hat f(\mu) \, e^{2\pi i \langle x, \mu \rangle}.$$

Lean: `Langlands.Tate.tsum_add_zlattice_eq_of_hasDecay`

*Proof.* First let $V = \mathbb{R}^n$ and $L = \mathbb{Z}^n$. The decay condition with $N > n$ shows that the series $Pf(x) = \sum_{m \in \mathbb{Z}^n} f(x + m)$ converges uniformly on compact sets. So $Pf$ is continuous, and it is a function on the torus $\mathbb{R}^n / \mathbb{Z}^n$. The cube $[0, 1)^n$ is a fundamental domain, and its translates by $\mathbb{Z}^n$ cover $\mathbb{R}^n$ without overlap. So the $k$-th Fourier coefficient of $Pf$ is
$$\int_{[0,1)^n} \sum_{m} f(y + m) e^{-2\pi i \langle y, k \rangle} \, dy = \int_{\mathbb{R}^n} f(y) e^{-2\pi i \langle y, k \rangle} \, dy = \hat f(k),$$
since $e^{-2\pi i \langle m, k \rangle} = 1$. The exchange of sum and integral is valid because $\sum_m \int_{[0,1)^n} |f(y + m)| \, dy = \int |f|$ is finite. The coefficients are absolutely summable by hypothesis. So the Fourier series converges uniformly to a continuous function with the same Fourier coefficients as $Pf$, and a continuous function on the torus is determined by its coefficients. This is the formula for $\mathbb{Z}^n$, and $\mathrm{covol}(\mathbb{Z}^n) = 1$.

In general, choose a basis $b_1, \dots, b_n$ of $L$, and let $A : \mathbb{R}^n \to V$ be the linear map with $A e_i = b_i$. Then $A(\mathbb{Z}^n) = L$ and $|\det A| = \mathrm{covol}(L)$. Let $D = (A^{-1})^*$ be the adjoint of $A^{-1}$. Then $\langle A u, D k \rangle = \langle u, k \rangle$, so $D(\mathbb{Z}^n) = L^\vee$. The function $g = f \circ A$ satisfies the hypotheses for $\mathbb{Z}^n$, and the substitution $w = Au$ gives
$$\hat g(k) = \int_{\mathbb{R}^n} f(Au) e^{-2\pi i \langle u, k \rangle} \, du = \frac{1}{\mathrm{covol}(L)} \int_V f(w) e^{-2\pi i \langle w, Dk \rangle} \, dw = \frac{\hat f(Dk)}{\mathrm{covol}(L)}.$$
Apply the formula for $\mathbb{Z}^n$ to $g$ at the point $A^{-1} x$, and note that $\langle A^{-1} x, k \rangle = \langle x, Dk \rangle$. $\square$

**Corollary 5.3.9 (the theta transformation formula).** Let $L \subset V$ be a lattice and $\theta_L(t) = \sum_{\ell \in L} e^{-\pi t |\ell|^2}$ for $t > 0$. Then
$$\theta_L(t) = \frac{1}{\mathrm{covol}(L) \, t^{n/2}} \, \theta_{L^\vee}(1/t).$$

Lean: `Langlands.Tate.tsum_zlattice_gaussian`

*Proof.* The function $f(v) = e^{-\pi t |v|^2}$ has $\hat f(w) = t^{-n/2} e^{-\pi |w|^2 / t}$. This follows from the case of dimension one in Section 5.1, applied in an orthonormal basis, with the substitution $v \mapsto t^{1/2} v$. Both $f$ and $\hat f$ decay faster than each power of $|v|$, so a Gaussian is summable on each lattice and Proposition 5.3.8 applies with $x = 0$. $\square$

**Corollary 5.3.10 (the theta formula of a number field).** Let $F$ be a number field of degree $n$, and let $F_\infty = F \otimes_\mathbb{Q} \mathbb{R} = \prod_{v \mid \infty} F_v$. Give $F_\infty$ the inner product $\langle x, y \rangle = \sum_{v \text{ real}} x_v y_v + \sum_{v \text{ complex}} 2 \mathrm{Re}(x_v \bar y_v)$, and put $\theta_\mathfrak{a}(t) = \sum_{\alpha \in \mathfrak{a}} e^{-\pi t \langle \alpha, \alpha \rangle}$ for a fractional ideal $\mathfrak{a}$. Then
$$\theta_{\mathcal{O}_F}(t) = \frac{1}{|d_F|^{1/2} \, t^{n/2}} \, \theta_{\mathfrak{D}^{-1}}(1/t),$$
where $\mathfrak{D} = \mathfrak{D}_{F/\mathbb{Q}}$ is the different.

Lean: `Langlands.Tate.dedekindTheta_inv_mul_different`

*Proof.* The Lebesgue measure of this inner product is $dx$ at a real place and $2 \, dx \, dy$ at a complex place, that is, the self-dual measure for $\psi_\infty = \prod_{v \mid \infty} \psi_v$. For this measure $\mathrm{vol}(F_\infty / \mathcal{O}_F) = |d_F|^{1/2}$, by Volume 1, Section 3.3. Let $y \mapsto \bar y$ be complex conjugation at the complex places. Then $\mathrm{Tr}_{F_\infty / \mathbb{R}}(xy) = \langle x, \bar y \rangle$. So the dual lattice of $\mathcal{O}_F$ is the conjugate of $\{\mu : \mathrm{Tr}(\mu \alpha) \in \mathbb{Z} \text{ for all } \alpha \in \mathcal{O}_F\} = \mathfrak{D}^{-1}$. Conjugation preserves $\langle \mu, \mu \rangle$, so $\theta_{(\mathcal{O}_F)^\vee} = \theta_{\mathfrak{D}^{-1}}$. Now apply Corollary 5.3.9. $\square$

For $F = \mathbb{Q}$ this is the formula of Example 5.3.6. The corollary is also the case $f = f_\infty \otimes \bigotimes_{v < \infty} 1_{\mathcal{O}_v}$, with a Gaussian $f_\infty$, of Theorem 5.3.4. Indeed, by Section 5.1 the transform of $1_{\mathcal{O}_v}$ is $q_v^{-d_v/2} 1_{\mathfrak{p}_v^{-d_v}}$, so $\hat f = |d_F|^{-1/2} \hat f_\infty \otimes \bigotimes_v 1_{\mathfrak{p}_v^{-d_v}}$. The elements $\xi \in F$ in the support of $f$ are the elements of $\mathcal{O}_F$, and those in the support of $\hat f$ are the elements of $\mathfrak{D}^{-1}$. The same computation with $f_v = 1_{\mathfrak{a}_v}$ gives the formula for $\theta_\mathfrak{a}$, with $\mathfrak{a}^{-1} \mathfrak{D}^{-1}$ in place of $\mathfrak{D}^{-1}$ and $N(\mathfrak{a}) |d_F|^{1/2}$ in place of $|d_F|^{1/2}$. Hecke used these formulas for his functional equation.

**Remark 5.3.11 (the Lean proof and its limits).** The Lean project proves Proposition 5.3.8 and Corollary 5.3.9 in the files `Langlands/Tate/PoissonSummation.lean`, `PoissonLattice.lean` and `PoissonTheta.lean`. The proof is the proof above: the case of $\mathbb{Z}^n$ is `Langlands.Tate.tsum_add_intPoint_eq_tsum_fourier`, and the passage to a lattice uses a basis and the adjoint map. The case $x = 0$ of Proposition 5.3.8 is `Langlands.Tate.tsum_zlattice_eq_of_hasDecay`, the version of Corollary 5.3.9 with a shift is `Langlands.Tate.tsum_add_zlattice_gaussian`, and the transform of the Gaussian is `Langlands.Tate.fourier_gaussian`. The decay condition $(1 + |v|)^N |f(v)| \le C$ is `Langlands.Tate.HasDecay`, and the theorems ask for $N > \dim V$ and for the summability of $\hat f$ on $L^\vee$, as in Proposition 5.3.8. The source files also prove the formulas for Schwartz functions with no extra hypothesis, as `SchwartzMap.tsum_zlattice_eq` and `SchwartzMap.tsum_add_zlattice_mul_eq`. These names are not under `Langlands`, and the record of the Lean build in the map does not list them. The Lean theorems have these limits. They concern a lattice in a Euclidean space with the Lebesgue measure of the inner product, and not the discrete subgroup $F$ of $\mathbb{A}_F$. So Theorem 5.3.4 and Theorem 5.3.5 are not in Lean.

**Remark 5.3.12 (the Lean form of Corollary 5.3.10).** The Lean project proves Corollary 5.3.10 for every nonzero fractional ideal $\mathfrak{a}$, and with one variable at each infinite place, in the files `Langlands/Tate/GlobalLattice.lean` and `DedekindTheta.lean`. For $t = (t_w)_{w \mid \infty}$ with $t_w > 0$, let $n_w = 1$ at a real place and $n_w = 2$ at a complex place, and let
$$\theta_\mathfrak{a}(t) = \sum_{\alpha \in \mathfrak{a}} \exp\Big(-\pi \sum_w n_w t_w |\alpha|_w^2\Big).$$
For $t_w = t$ at all $w$ this is the function $\theta_\mathfrak{a}(t)$ of the corollary. The theorem `Langlands.Tate.dedekindTheta_dual` says that
$$\theta_\mathfrak{a}(t) = \frac{1}{N(\mathfrak{a}) \, |d_F|^{1/2} \prod_w t_w^{n_w/2}} \, \theta_{\mathfrak{a}^\vee}(t^{-1}),$$
where $\mathfrak{a}^\vee = \{\mu \in F : \mathrm{Tr}_{F/\mathbb{Q}}(\mu \mathfrak{a}) \subset \mathbb{Z}\}$ is the dual of $\mathfrak{a}$ for the trace form and $t^{-1} = (t_w^{-1})_w$. The theorem `Langlands.Tate.dedekindTheta_inv_mul_different` writes $\mathfrak{a}^\vee = (\mathfrak{a} \mathfrak{D})^{-1}$, and `Langlands.Tate.dedekindTheta_dual_const` is the case of one variable. The proof is the proof above. The map $\alpha \mapsto (\sqrt{n_w t_w} \, \sigma_w(\alpha))_w$ sends $\mathfrak{a}$ to a lattice in a Euclidean space of dimension $n$, and `Langlands.Tate.covolume_globalLattice` computes its covolume. The dual lattice is the image of $\mathfrak{a}^\vee$ under the map $\beta \mapsto (\sqrt{n_w / t_w} \, \overline{\sigma_w(\beta)})_w$, and Corollary 5.3.9 gives the formula. The factor $2^{-r_2}$ in the covolume of the standard embedding cancels against the factors $\sqrt{n_w}^{\,n_w} = 2$ at the complex places.

**Remark 5.3.13 (Hecke's integral).** Hecke deduced the functional equation of $\zeta_F$ from the theta formula with a Mellin transform, and this is the route that the Lean project follows for Theorem 5.5.3 in the case of the Dedekind zeta function. For $\mathrm{Re}(s) > 0$ and $\alpha \in F^\times$,
$$\int_{(0, \infty)^{S_\infty}} \exp\Big(-\pi \sum_w n_w t_w |\alpha|_w^2\Big) \prod_w t_w^{n_w s/2} \, \frac{dt_w}{t_w} = \Gamma_F(s) \, |N_{F/\mathbb{Q}}(\alpha)|^{-s}, \qquad \Gamma_F(s) = \prod_w (\pi n_w)^{-n_w s/2} \, \Gamma(n_w s / 2).$$
This is a product of integrals of one variable, each of which is the integral of Euler for $\Gamma$. In the notation of Definition 5.2.2, $\Gamma_F(s) = \Gamma_\mathbb{R}(s)^{r_1} (\Gamma_\mathbb{C}(s)/2)^{r_2}$. The identity is `Langlands.Tate.integral_exp_mul_prod_eq_gammaK`, and $\Gamma_F$ is `Langlands.Tate.gammaK`. To finish the proof, one sums over the nonzero $\alpha \in \mathfrak{a}$ modulo the units $\mathcal{O}_F^\times$, so that the sum of $|N(\alpha)|^{-s}$ becomes $N(\mathfrak{a})^{-s}$ times the partial zeta function of the class of $\mathfrak{a}^{-1}$. The units act on the variables $t_w$, and the integral over $(0, \infty)^{S_\infty}$ modulo this action is an integral over a fundamental domain of the unit lattice of Volume 1, Section 1.3. Then one splits the integral at $\prod_w t_w^{n_w} = 1$ and applies the theta formula to the part with $\prod_w t_w^{n_w} < 1$. This gives the meromorphic continuation and the functional equation, with the poles at $s = 0$ and $s = 1$ and the residue of Proposition 5.4.4. Proposition 5.3.27 below does the integral over the fundamental domain of the units in advance, and gives a theta function of one variable with a transformation formula. Corollary 5.3.31 below writes its Mellin transform as a Dirichlet series. Theorem 5.3.34 below does the sum over the ideal classes and proves the functional equation of $\zeta_F$ in Lean for each number field. This is the case of the trivial character of `Langlands.HeckeFunctionalEquation`. The Lean statement is for all Hecke characters, and it is not proved yet.

### The Epstein zeta function of a lattice

Riemann's second proof of the functional equation of $\zeta(s)$ uses only the theta formula of Example 5.3.6 and a Mellin transform. The same proof works for each lattice. Epstein studied the functions that it gives in 1903. Let $V$ be a real inner product space of dimension $n \ge 1$, as in Proposition 5.3.8.

**Definition 5.3.14 (Epstein zeta functions).** Let $L \subset V$ be a lattice. The *Epstein zeta function* of $L$ is
$$Z_L(s) = \sum_{\ell \in L, \, \ell \ne 0} |\ell|^{-s},$$
and its *completed function* is $\Lambda_L(s) = \Gamma_\mathbb{R}(s) Z_L(s)$, with $\Gamma_\mathbb{R}(s) = \pi^{-s/2} \Gamma(s/2)$ as in Definition 5.2.2.

Lean: `Langlands.Tate.epsteinZeta`

The series converges absolutely for $\mathrm{Re}(s) > n$. Indeed, the number of $\ell \in L$ with $k \le |\ell| < k + 1$ is $O(k^{n-1})$, because the balls of a fixed small radius around these points do not meet and lie in a shell of volume $O(k^{n-1})$. So the series is dominated by $\sum_k k^{n - 1 - \sigma}$ with $\sigma = \mathrm{Re}(s)$.

**Theorem 5.3.15 (the functional equation of the Epstein zeta function).** Let $L \subset V$ be a lattice. Then $\Lambda_L$ has a meromorphic continuation to $\mathbb{C}$. It is holomorphic outside $s = 0$ and $s = n$, and it has a simple pole with residue $2 \, \mathrm{covol}(L)^{-1}$ at $s = n$. It satisfies
$$\Lambda_L(n - s) = \frac{1}{\mathrm{covol}(L)} \, \Lambda_{L^\vee}(s).$$

Lean: `Langlands.Tate.completedEpsteinZeta_sub`

*Proof.* Let $\theta_L(t) = \sum_{\ell \in L} e^{-\pi t |\ell|^2}$, as in Corollary 5.3.9. Since $L$ is discrete, there is $c > 0$ with $|\ell|^2 \ge c$ for each nonzero $\ell \in L$. For $t \ge 1$ each term with $\ell \ne 0$ satisfies $e^{-\pi t |\ell|^2} \le e^{-\pi c (t - 1)} e^{-\pi |\ell|^2}$, so
$$0 \le \theta_L(t) - 1 \le e^{-\pi c (t - 1)} \big(\theta_L(1) - 1\big).$$
So $\theta_L(t) - 1$ decays exponentially as $t \to \infty$. For $\mathrm{Re}(s) > n$ and $\ell \ne 0$, the substitution $u = \pi t |\ell|^2$ in the integral of Euler gives $\int_0^\infty e^{-\pi t |\ell|^2} t^{s/2} \, dt / t = \Gamma_\mathbb{R}(s) |\ell|^{-s}$. The sum over $\ell$ of the integrals of the absolute values converges, because $Z_L(\sigma)$ converges. So we can exchange the sum and the integral, and
$$\Lambda_L(s) = \int_0^\infty \big(\theta_L(t) - 1\big) \, t^{s/2} \, \frac{dt}{t}.$$
Split the integral at $t = 1$. On $(0, 1)$ substitute $t \mapsto 1/t$ and use Corollary 5.3.9 in the form $\theta_L(1/t) = \mathrm{covol}(L)^{-1} t^{n/2} \theta_{L^\vee}(t)$. With $\theta_L(1/t) - 1 = \mathrm{covol}(L)^{-1} t^{n/2} (\theta_{L^\vee}(t) - 1) + \mathrm{covol}(L)^{-1} t^{n/2} - 1$, a calculation gives
$$\Lambda_L(s) = \int_1^\infty \big(\theta_L(t) - 1\big) t^{s/2} \, \frac{dt}{t} + \frac{1}{\mathrm{covol}(L)} \int_1^\infty \big(\theta_{L^\vee}(t) - 1\big) t^{(n - s)/2} \, \frac{dt}{t} - \frac{2}{s} - \frac{2}{\mathrm{covol}(L) (n - s)}.$$
The two integrals converge for all $s$ and are entire functions of $s$, because the integrands decay exponentially. So the right side is the meromorphic continuation, with the poles and the residue of the theorem. The dual lattice of $L^\vee$ is $L$, and $\mathrm{covol}(L^\vee) = \mathrm{covol}(L)^{-1}$. The second identity follows from Corollary 5.3.9 at $t = 1$, applied to $L$ and to $L^\vee$. So the same formula for $\Lambda_{L^\vee}(n - s)$ is the formula for $\Lambda_L(s)$ with the two integrals in the other order and with the factor $\mathrm{covol}(L)^{-1}$. This is the functional equation. $\square$

**Example 5.3.16 (the Riemann zeta function and the Gaussian integers).** Let $V = \mathbb{R}$ and $L = \mathbb{Z}$. Then $L^\vee = \mathbb{Z}$, $\mathrm{covol}(L) = 1$ and $Z_L(s) = 2\zeta(s)$. Theorem 5.3.15 is the functional equation $\Lambda(1 - s) = \Lambda(s)$ for $\Lambda(s) = \Gamma_\mathbb{R}(s) \zeta(s)$, with the residue 1 at $s = 1$.

Next let $F = \mathbb{Q}(i)$, with $F_\infty = \mathbb{C}$ and the inner product $\langle x, y \rangle = 2 \mathrm{Re}(x \bar y)$ of Corollary 5.3.10. Let $L = \mathbb{Z}[i]$. Then $|\alpha|^2 = 2 N(\alpha)$, the covolume is $|d_F|^{1/2} = 2$, and the dual lattice is the conjugate of $\mathfrak{D}^{-1} = \frac{1}{2} \mathbb{Z}[i]$, which is $\frac{1}{2} L$. Since $\mathbb{Z}[i]$ is a principal ideal domain with four units, each nonzero ideal is $(\alpha)$ for exactly four $\alpha$. So $Z_L(s) = 4 \cdot 2^{-s/2} \zeta_F(s/2)$, and $Z_{L/2}(s) = 2^s Z_L(s)$. Put $u = s/2$ and $\Lambda_F(u) = |d_F|^{u/2} \Gamma_\mathbb{C}(u) \zeta_F(u) / 2 = \pi^{-u} \Gamma(u) \zeta_F(u)$, with $\Gamma_\mathbb{C}$ as in Definition 5.2.2. Then $\Lambda_L(s) = 4 \cdot 2^{-u} \Lambda_F(u)$, and Theorem 5.3.15 becomes $\Lambda_F(1 - u) = \Lambda_F(u)$. This is the functional equation of the Dedekind zeta function of $\mathbb{Q}(i)$.

**Remark 5.3.17 (Epstein and Dedekind).** The method of Example 5.3.16 works for $F = \mathbb{Q}$ and for each imaginary quadratic field $F$, and only for these fields. For a fractional ideal $\mathfrak{a}$ the function $Z_\mathfrak{a}(s)$ is a sum of $\big(\sum_w n_w |\alpha|_w^2\big)^{-s/2}$, while the partial zeta function of the class of $\mathfrak{a}^{-1}$ is a sum of $|N(\alpha)|^{-s}$ over $\alpha$ modulo units. The two sums agree up to a constant when $F$ has only one infinite place, since then $\sum_w n_w |\alpha|_w^2 = n |N(\alpha)|^{2/n}$. The fields with one infinite place are $\mathbb{Q}$ and the imaginary quadratic fields. By the unit theorem their unit groups are finite, so the sum over $\alpha$ modulo units is a finite multiple of the sum over $\alpha$. For the other fields the theta function needs one variable at each infinite place, as in Remark 5.3.12, and Hecke's integral of Remark 5.3.13 replaces the Mellin transform in one variable.

**Remark 5.3.18 (the Lean proof).** The file `Langlands/Tate/EpsteinZeta.lean` proves Theorem 5.3.15 for each lattice in a real inner product space of dimension $n \ge 1$. The function $\Lambda_L$ is `Langlands.Tate.completedEpsteinZeta`. The identity $\Lambda_L(s) = \Gamma_\mathbb{R}(s) Z_L(s)$ for $\mathrm{Re}(s) > n$ is `Langlands.Tate.completedEpsteinZeta_eq`, the holomorphy outside $\{0, n\}$ is `Langlands.Tate.differentiableAt_completedEpsteinZeta`, and the residue is `Langlands.Tate.completedEpsteinZeta_residue`. The identities $L^{\vee\vee} = L$ and $\mathrm{covol}(L^\vee) = \mathrm{covol}(L)^{-1}$ are `Langlands.Tate.dualLattice_dualLattice` and `Langlands.Tate.covolume_dualLattice`. The proof does not split the integral by hand. The pair $(\theta_L, \theta_{L^\vee})$ satisfies the hypotheses of the structure `WeakFEPair` of Mathlib, with the weight $n/2$, and Mathlib proves the continuation and the functional equation for each such pair with the computation of the proof above. Remark 5.3.25 gives the Lean form of the application to the imaginary quadratic fields.

### The zeta function of an ideal class

We now apply Theorem 5.3.15 to the lattices of Corollary 5.3.10 and make Remark 5.3.17 precise. Let $F$ be a number field of degree $n$, and give $F_\infty$ the inner product of Corollary 5.3.10. For $x \in F$ we have $\langle x, x \rangle = \sum_{v \mid \infty} n_v |x|_v^2$, where $|x|_v$ is the ordinary absolute value of the image of $x$ in $\mathbb{R}$ or $\mathbb{C}$, and $n_v = 1$ at a real place and $n_v = 2$ at a complex place. Each nonzero fractional ideal $\mathfrak{a}$ is a lattice in $F_\infty$.

**Definition 5.3.19 (the zeta function of a fractional ideal).** Let $\mathfrak{a}$ be a nonzero fractional ideal of $F$. Its *completed zeta function* is the completed Epstein zeta function $\Lambda_\mathfrak{a} = \Lambda_L$ of the lattice $L = \mathfrak{a}$ in $F_\infty$. So for $\mathrm{Re}(s) > n$,
$$\Lambda_\mathfrak{a}(s) = \Gamma_\mathbb{R}(s) \sum_{\alpha \in \mathfrak{a}, \, \alpha \ne 0} \Big( \sum_{v \mid \infty} n_v |\alpha|_v^2 \Big)^{-s/2}.$$

Lean: `Langlands.Tate.completedIdealZeta`

**Proposition 5.3.20 (the functional equation for a fractional ideal).** Let $\mathfrak{a}$ be a nonzero fractional ideal of $F$, and let $\mathfrak{a}^\vee = \mathfrak{a}^{-1} \mathfrak{D}^{-1}$, with the different $\mathfrak{D}$ of $F/\mathbb{Q}$. Then $\Lambda_\mathfrak{a}$ is holomorphic outside $s = 0$ and $s = n$, it has a simple pole with residue $2 \, (N(\mathfrak{a}) |d_F|^{1/2})^{-1}$ at $s = n$, and
$$\Lambda_\mathfrak{a}(n - s) = \frac{1}{N(\mathfrak{a}) |d_F|^{1/2}} \, \Lambda_{\mathfrak{a}^\vee}(s).$$

Lean: `Langlands.Tate.completedIdealZeta_sub`

*Proof.* By Theorem 5.3.15 it is sufficient to find the covolume and the dual lattice of $L = \mathfrak{a}$. The proof of Corollary 5.3.10 gives $\mathrm{covol}(\mathcal{O}_F) = |d_F|^{1/2}$. If $\mathfrak{a} \subset \mathcal{O}_F$, then $\mathfrak{a}$ has index $N(\mathfrak{a})$ in $\mathcal{O}_F$, so $\mathrm{covol}(\mathfrak{a}) = N(\mathfrak{a}) |d_F|^{1/2}$. For a general $\mathfrak{a}$, take an integer $m \ne 0$ with $m \mathfrak{a} \subset \mathcal{O}_F$. Multiplication by $m$ multiplies the covolume and the norm by $|m|^n$, so the formula is true for $\mathfrak{a}$ too. As in the proof of Corollary 5.3.10, $\mathrm{Tr}(xy) = \langle x, \bar y \rangle$, so $L^\vee$ is the conjugate of $\{\mu \in F_\infty : \mathrm{Tr}(\mu \alpha) \in \mathbb{Z} \text{ for all } \alpha \in \mathfrak{a}\}$. This set is $\mathfrak{a}^{-1} \mathfrak{D}^{-1}$ by the definition of the different. Conjugation is an isometry of $F_\infty$, so it does not change the Epstein zeta function, and $\Lambda_{L^\vee} = \Lambda_{\mathfrak{a}^\vee}$. $\square$

Now let $F$ be an imaginary quadratic field. Then $F$ has one infinite place $v$, which is complex, and $n = 2$. For $\alpha \in F$ we have $\langle \alpha, \alpha \rangle = 2 |\alpha|_v^2 = 2 N(\alpha)$, where $N(\alpha) = \alpha \bar \alpha = |N_{F/\mathbb{Q}}(\alpha)|$. Let $w_F$ be the number of roots of unity in $F$. It is the order of $\mathcal{O}_F^\times$, and it is 2, 4 or 6. For a nonzero fractional ideal $\mathfrak{a}$ put
$$c_\mathfrak{a} = \big( N(\mathfrak{a}) \, |d_F|^{1/2} \big)^{1/2}, \qquad \psi_\mathfrak{a}(s) = c_\mathfrak{a}^s \, \Lambda_\mathfrak{a}(s).$$

**Lemma 5.3.21 (class invariance).** Let $F$ be imaginary quadratic, let $\mathfrak{a}$ be a nonzero fractional ideal and let $x \in F^\times$. Then $\psi_{x \mathfrak{a}}(s) = \psi_\mathfrak{a}(s)$ for $s \ne 0, 2$.

Lean: `Langlands.Tate.classTerm_toPrincipalIdeal_mul`

*Proof.* First let $\mathrm{Re}(s) > 2$. The map $\alpha \mapsto x \alpha$ is a bijection from $\mathfrak{a}$ to $x \mathfrak{a}$, and $N(x \alpha) = N(x) N(\alpha)$. So the series of Definition 5.3.19 gives $\Lambda_{x \mathfrak{a}}(s) = N(x)^{-s/2} \Lambda_\mathfrak{a}(s)$. Also $N(x \mathfrak{a}) = N(x) N(\mathfrak{a})$, so $c_{x \mathfrak{a}}^s = N(x)^{s/2} c_\mathfrak{a}^s$. The two factors cancel, and $\psi_{x \mathfrak{a}}(s) = \psi_\mathfrak{a}(s)$. Next, both functions are holomorphic on $U = \mathbb{C} \setminus \{0, 2\}$ by Proposition 5.3.20. The set $U$ is open and connected, and the two functions agree on the half plane $\mathrm{Re}(s) > 2$. By the identity theorem they agree on $U$. $\square$

So for $s \ne 0, 2$ the value $\psi_C(s) = \psi_\mathfrak{a}(s)$ for an ideal class $C$ does not depend on the choice of $\mathfrak{a} \in C$.

**Theorem 5.3.22 (the class zeta function of an imaginary quadratic field).** Let $F$ be imaginary quadratic, and let $\Lambda_F^{\mathrm{cl}}(s) = \sum_{C} \psi_C(s)$, where $C$ runs through the ideal class group of $F$.
1. For $s \ne 0, 2$, $\Lambda_F^{\mathrm{cl}}(2 - s) = \Lambda_F^{\mathrm{cl}}(s)$.
2. For $\mathrm{Re}(u) > 1$, $\Lambda_F^{\mathrm{cl}}(2u) = \frac{w_F}{2} \, |d_F|^{u/2} \, \Gamma_\mathbb{C}(u) \, \zeta_F(u)$.

Lean: `Langlands.Tate.classZeta_two_sub`, `Langlands.Tate.classZeta_two_mul`

*Proof.* For (1), Proposition 5.3.20 with $c_\mathfrak{a}^2 = N(\mathfrak{a}) |d_F|^{1/2}$ gives
$$\psi_\mathfrak{a}(2 - s) = c_\mathfrak{a}^{2 - s} c_\mathfrak{a}^{-2} \Lambda_{\mathfrak{a}^\vee}(s) = c_\mathfrak{a}^{-s} \Lambda_{\mathfrak{a}^\vee}(s).$$
Since $N(\mathfrak{D}) = |d_F|$, we have $N(\mathfrak{a}^\vee) |d_F|^{1/2} = (N(\mathfrak{a}) |d_F|^{1/2})^{-1}$, so $c_{\mathfrak{a}^\vee} = c_\mathfrak{a}^{-1}$ and $\psi_\mathfrak{a}(2 - s) = \psi_{\mathfrak{a}^\vee}(s)$. The class of $\mathfrak{a}^\vee$ is $(C [\mathfrak{D}])^{-1}$ if $\mathfrak{a} \in C$, and $C \mapsto (C [\mathfrak{D}])^{-1}$ is a bijection of the class group. So the sum over $C$ of $\psi_C(2 - s)$ is the sum over $C$ of $\psi_C(s)$, by Lemma 5.3.21.

For (2), put $s = 2u$ and let $\mathfrak{a} \in C$. For each nonzero $\alpha \in \mathfrak{a}$ the ideal $\mathfrak{b} = \alpha \mathfrak{a}^{-1}$ is integral, it is in the class $C^{-1}$, and $N(\mathfrak{b}) = N(\alpha) / N(\mathfrak{a})$. Conversely, each integral $\mathfrak{b} \in C^{-1}$ has $\mathfrak{b} \mathfrak{a} = (\alpha)$ for an $\alpha \in \mathfrak{a}$, and $\alpha$ is unique up to a unit. The group $\mathcal{O}_F^\times$ of order $w_F$ acts freely on the nonzero elements of $\mathfrak{a}$. So
$$\sum_{\alpha \in \mathfrak{a}, \, \alpha \ne 0} N(\alpha)^{-u} = w_F \, N(\mathfrak{a})^{-u} \zeta(C^{-1}, u), \qquad \zeta(C^{-1}, u) = \sum_{\mathfrak{b} \in C^{-1}, \, \mathfrak{b} \subset \mathcal{O}_F} N(\mathfrak{b})^{-u}.$$
With $\Gamma_\mathbb{R}(2u) = \pi^{-u} \Gamma(u)$ and $(2 N(\alpha))^{-u} = 2^{-u} N(\alpha)^{-u}$ this gives
$$\psi_C(2u) = w_F \, |d_F|^{u/2} (2\pi)^{-u} \Gamma(u) \, \zeta(C^{-1}, u) = \frac{w_F}{2} |d_F|^{u/2} \Gamma_\mathbb{C}(u) \, \zeta(C^{-1}, u).$$
The sum over $C$ of $\zeta(C^{-1}, u)$ is $\zeta_F(u)$. $\square$

With $\Lambda_F(u) = \Gamma_\mathbb{C}(u) \zeta_F(u)$ as in Corollary 5.4.8, part (2) says $\Lambda_F^{\mathrm{cl}}(2u) = \frac{w_F}{2} |d_F|^{u/2} \Lambda_F(u)$. So part (1) is the functional equation $\Lambda_F(u) = |d_F|^{1/2 - u} \Lambda_F(1 - u)$ of Corollary 5.4.8 for an imaginary quadratic field, and part (2) gives the continuation of $\zeta_F$. Example 5.3.16 is the case $F = \mathbb{Q}(i)$, with one ideal class and $w_F = 4$.

**Corollary 5.3.23 (the Dedekind zeta function of an imaginary quadratic field).** Let $F$ be imaginary quadratic, and let $\xi_F(u) = \Lambda_F^{\mathrm{cl}}(2u)$.
1. The function $\xi_F$ is holomorphic on $\mathbb{C} \setminus \{0, 1\}$, and $\xi_F(1 - u) = \xi_F(u)$ for $u \ne 0, 1$.
2. For $\mathrm{Re}(u) > 1$, $\xi_F(u) = \frac{w_F}{2} |d_F|^{u/2} \Gamma_\mathbb{C}(u) \zeta_F(u)$.
3. The function $\zeta_F$ extends to a holomorphic function on $\mathbb{C} \setminus \{1\}$. It has a simple pole at $u = 1$ with residue $2\pi h_F / (w_F |d_F|^{1/2})$.

Lean: `Langlands.Tate.completedQuadraticZeta_one_sub`, `Langlands.Tate.differentiableAt_completedQuadraticZeta`, `Langlands.Tate.completedQuadraticZeta_eq`

*Proof.* By Proposition 5.3.20 with $n = 2$, each $\psi_C$ is holomorphic outside $s = 0$ and $s = 2$. So $\xi_F$ is holomorphic outside $u = 0$ and $u = 1$. Since $2(1 - u) = 2 - 2u$, part (1) of Theorem 5.3.22 gives $\xi_F(1 - u) = \xi_F(u)$. Part (2) is part (2) of Theorem 5.3.22.

For (3), we have $\Gamma_\mathbb{C}(u) = 2 (2\pi)^{-u} \Gamma(u)$. The function $1 / \Gamma$ is entire, and it has a simple zero at $u = 0$. So the function
$$Z(u) = \frac{2}{w_F} |d_F|^{-u/2} \frac{\xi_F(u)}{\Gamma_\mathbb{C}(u)}$$
is holomorphic on $\mathbb{C} \setminus \{0, 1\}$, and $Z(u) = \zeta_F(u)$ for $\mathrm{Re}(u) > 1$ by (2). By the functional equation of Proposition 5.3.20, the pole of each $\psi_C$ at $s = 0$ is the pole of a term at $s = 2$, so it is simple. Thus $\xi_F$ has at most a simple pole at $u = 0$, and the zero of $1 / \Gamma$ cancels it. So $Z$ is holomorphic at $u = 0$. At $u = 1$, Remark 5.3.24 gives the residue $2 h_F$ of $\Lambda_F^{\mathrm{cl}}$ at $s = 2$, so $\xi_F$ has the residue $h_F$ at $u = 1$. With $\Gamma_\mathbb{C}(1) = 1/\pi$ the residue of $Z$ at $u = 1$ is $2\pi h_F / (w_F |d_F|^{1/2})$. $\square$

This is the analytic class number formula of Corollary 5.4.8 for an imaginary quadratic field. For $F = \mathbb{Q}(\sqrt{-5})$ we have $h_F = 2$, $w_F = 2$ and $d_F = -20$. So the residue of $\zeta_F$ at $u = 1$ is $2\pi / \sqrt{20} = \pi / \sqrt{5}$. Since $\zeta_F = \zeta \cdot L(\chi_{-20}, \cdot)$ and $\zeta$ has residue $1$, this is the value $L(1, \chi_{-20}) = \pi / \sqrt{5}$.

**Remark 5.3.24 (the theta function and the class group).** The proof of part (1) uses the functional equation of each term and a bijection of the class group. Hecke's proof uses one theta function for each ideal class, and the duality $C \mapsto (C [\mathfrak{D}])^{-1}$ appears in the theta formula of Corollary 5.3.10 for $\theta_\mathfrak{a}$. The class number $h_F$ enters part (2) only through the sum over $C$. For $s \to 2$ each $\psi_C$ has residue $2 c_\mathfrak{a}^2 (N(\mathfrak{a}) |d_F|^{1/2})^{-1} = 2$ by Proposition 5.3.20, so $\Lambda_F^{\mathrm{cl}}$ has residue $2 h_F$ at $s = 2$. With part (2) this gives $\mathrm{Res}_{u = 1} \zeta_F(u) = 2\pi h_F / (w_F |d_F|^{1/2})$, which is the residue of Corollary 5.4.8 for $r_1 = 0$, $r_2 = 1$ and $R = 1$.

**Remark 5.3.25 (the Lean proof).** The file `Langlands/Tate/IdealZeta.lean` proves Proposition 5.3.20 for each number field. The function $\Lambda_\mathfrak{a}$ is `Langlands.Tate.completedIdealZeta`, the series for $\mathrm{Re}(s) > n$ is `Langlands.Tate.completedIdealZeta_eq`, and the residue is `Langlands.Tate.completedIdealZeta_residue`. The dual ideal is `Langlands.Tate.dualUnit`, and its norm is `Langlands.Tate.absNorm_dualUnit`. The Lean proof does not use complex conjugation as an isometry. It shows that the lattice $L^\vee$ and the lattice of $\mathfrak{a}^\vee$ have the same theta function and the same covolume, and that $\Lambda_L$ depends only on these two data, by `Langlands.Tate.completedEpsteinZeta_congr`. The file `Langlands/Tate/ImaginaryQuadratic.lean` proves Lemma 5.3.21 and part (1) of Theorem 5.3.22. The function $\psi_\mathfrak{a}$ is `Langlands.Tate.classTerm`, the constant $c_\mathfrak{a}$ is `Langlands.Tate.idealScale`, and $\Lambda_F^{\mathrm{cl}}$ is `Langlands.Tate.classZeta`, with a choice `Langlands.Tate.classRep` of an ideal in each class. The identity theorem in the form of the proof of Lemma 5.3.21 is `Langlands.Tate.eq_of_eq_of_lt_re`. The series of $\Lambda_F^{\mathrm{cl}}$ for $\mathrm{Re}(s) > 2$ is `Langlands.Tate.classZeta_eq`. It is the first step of part (2). The file `Langlands/Tate/QuadraticDedekind.lean` proves part (2) of Theorem 5.3.22 as `Langlands.Tate.classZeta_two_mul`, with `NumberField.dedekindZeta` of Mathlib for $\zeta_F$. The proof is the count of the proof above, with an integral ideal $\mathfrak{a} = J$ in each class. For a nonzero $\alpha \in J$ there is a unique integral ideal $I$ with $(\alpha) = J I$, and `Langlands.Tate.elementEquiv` sorts the nonzero elements of $J$ by $I$. The number of generators of $J I$ is `Langlands.Tate.natCard_generators`. It is $w_F$ if $[I] = [J]^{-1}$, and $0$ if not. The fact that each unit of $F$ is a root of unity is `Langlands.Tate.mem_torsion_of_isQuadratic`. It follows from the Dirichlet unit theorem of Mathlib, because the unit rank $r_1 + r_2 - 1$ is $0$. Parts (1) and (2) of Corollary 5.3.23 are in the same file, with $\xi_F$ as `Langlands.Tate.completedQuadraticZeta`. Part (3), the residue at $u = 1$ and the behaviour at $u = 0$, is not in Lean yet.

### The theta function averaged over the units

Remark 5.3.17 explains why the method of the Epstein zeta function stops at the imaginary quadratic fields: when the unit group is infinite, the sum over $\alpha \in \mathfrak{a}$ counts each principal ideal infinitely often. Hecke's remedy is to average the theta function of Remark 5.3.12 over the action of the units on the variables $t_w$. The average is a function of one variable $y > 0$, and it keeps the transformation formula. In this subsection $F$ is a number field of degree $n$ with $r_1$ real and $r_2$ complex places, $r = r_1 + r_2 - 1$, and $\varepsilon_1, \dots, \varepsilon_r$ is a system of fundamental units. We write $n_w$ and $\theta_\mathfrak{a}(t)$ as in Remark 5.3.12.

**Definition 5.3.26 (the unit average).** For $y > 0$ and $c \in \mathbb{R}^r$ let $t(y, c)$ be the vector with the coordinates
$$t(y, c)_w = y \exp\Big(2 \sum_{i=1}^r c_i \log |\varepsilon_i|_w\Big), \qquad w \mid \infty.$$
For a nonzero fractional ideal $\mathfrak{a}$, the *unit average* of its theta function is
$$\Theta_\mathfrak{a}(y) = \int_{[0, 1)^r} \theta_\mathfrak{a}(t(y, c)) \, dc.$$

The vector $t(y, c)$ has three simple properties. First, the product formula $\sum_w n_w \log |\varepsilon_i|_w = 0$ for a unit gives $\prod_w t(y, c)_w^{n_w/2} = y^{n/2}$ for each $c$. Second, $t(y, c)^{-1} = t(y^{-1}, -c)$. Third, for $k \in \mathbb{Z}^r$ and $u = \prod_i \varepsilon_i^{k_i}$ we have $t(y, c + k)_w = t(y, c)_w \, |u|_w^2$. Since $\alpha \mapsto u \alpha$ is a bijection of $\mathfrak{a}$, the third property gives $\theta_\mathfrak{a}(t(y, c + k)) = \theta_\mathfrak{a}(t(y, c))$. So the integrand of $\Theta_\mathfrak{a}$ is a periodic function of $c$ for the lattice $\mathbb{Z}^r$, and $[0, 1)^r$ is a fundamental domain for this lattice. When $r = 0$ there is no integral, and $\Theta_\mathfrak{a}(y) = \theta_\mathfrak{a}(y)$ is the function of Corollary 5.3.10.

**Proposition 5.3.27 (the transformation formula of the unit average).** Let $\mathfrak{a}$ be a nonzero fractional ideal of $F$ and let $\mathfrak{a}^\vee$ be its dual for the trace form.

1. For $y > 0$, $$\Theta_\mathfrak{a}(1/y) = \frac{y^{n/2}}{N(\mathfrak{a}) \, |d_F|^{1/2}} \, \Theta_{\mathfrak{a}^\vee}(y).$$
2. Let $m = \exp\big(-2 \sum_i \sum_w |\log |\varepsilon_i|_w|\big)$. Then $1 \le \Theta_\mathfrak{a}(y) \le \theta_\mathfrak{a}(y m)$ for $y > 0$. In particular $\Theta_\mathfrak{a}(y) - 1$ decreases faster than each power of $y$ as $y \to \infty$.
3. The function $\Theta_\mathfrak{a}$ is continuous on $(0, \infty)$.

*Proof.* (1) Fix $c$ and apply the theta formula of Remark 5.3.12 at $t = t(y^{-1}, c)$. By the first property, $\prod_w t_w^{n_w/2} = y^{-n/2}$, and by the second property $t^{-1} = t(y, -c)$. So
$$\theta_\mathfrak{a}(t(y^{-1}, c)) = \frac{y^{n/2}}{N(\mathfrak{a}) \, |d_F|^{1/2}} \, \theta_{\mathfrak{a}^\vee}(t(y, -c)).$$
Integrate over $c \in [0, 1)^r$. Put $G(c) = \theta_{\mathfrak{a}^\vee}(t(y, c))$. The substitution $c \mapsto -c$ preserves the Lebesgue measure, so $\int_{[0, 1)^r} G(-c) \, dc = \int_{(-1, 0]^r} G(c) \, dc$. The set $(-1, 0]^r$ is also a fundamental domain of $\mathbb{Z}^r$, and $G$ is periodic for $\mathbb{Z}^r$. The integrals of a periodic function over two fundamental domains are equal, because each one is the integral over the quotient $\mathbb{R}^r / \mathbb{Z}^r$. This gives the formula.

(2) Each term of $\theta_\mathfrak{a}(t)$ decreases when one coordinate $t_w$ increases, so $\theta_\mathfrak{a}(t) \le \theta_\mathfrak{a}(s)$ if $0 < s_w \le t_w$ for all $w$. For $c \in [0, 1]^r$ we have $c_i \log |\varepsilon_i|_w \ge -|\log |\varepsilon_i|_w|$, hence $t(y, c)_w \ge y m$ at each $w$. So $\theta_\mathfrak{a}(t(y, c)) \le \theta_\mathfrak{a}(y m)$, and the integral over a set of volume $1$ gives the upper bound. The term $\alpha = 0$ gives $\theta_\mathfrak{a}(t) \ge 1$ and the lower bound. The decay follows from the bound $\theta_\mathfrak{a}(x) - 1 = O(e^{-\pi \delta x})$ for the lattice $\mathfrak{a}$, with $\delta$ the minimum of $\langle \alpha, \alpha \rangle$ over $\alpha \ne 0$.

(3) The series of $\theta_\mathfrak{a}(t)$ converges uniformly on the set of $t$ with $t_w > t^0_w / 2$ for all $w$, because it is dominated there by the series of $\theta_\mathfrak{a}(t^0/2)$. So $\theta_\mathfrak{a}$ is continuous wherever all $t_w > 0$. For $y$ near $y_0$ with $y > y_0/2$, the argument of (2) bounds the integrand by the constant $\theta_\mathfrak{a}(y_0 m / 2)$. The theorem of dominated convergence gives the continuity of $\Theta_\mathfrak{a}$ at $y_0$. $\square$

The proposition says that the pair $(\Theta_\mathfrak{a}, \Theta_{\mathfrak{a}^\vee})$ has the same three properties as the pair $(\theta_L, \theta_{L^\vee})$ in the proof of Theorem 5.3.15: a transformation formula with weight $n/2$, the constant term $1$, and rapid decay. So the proof of Theorem 5.3.15 applies word for word. The Mellin transform
$$\Lambda(\Theta_\mathfrak{a}, s) = \int_0^\infty \big(\Theta_\mathfrak{a}(y) - 1\big) \, y^s \, \frac{dy}{y}$$
converges for $\mathrm{Re}(s) > n/2$, it has a meromorphic continuation with simple poles at $s = 0$ and $s = n/2$ only, and $\Lambda(\Theta_\mathfrak{a}, n/2 - s) = (N(\mathfrak{a}) |d_F|^{1/2})^{-1} \Lambda(\Theta_{\mathfrak{a}^\vee}, s)$. To obtain the functional equation of $\zeta_F$, it remains to show that $\Lambda(\Theta_\mathfrak{a}, s)$ is a constant times $\Gamma_F(2s/n) \, N(\mathfrak{a})^{-2s/n}$ times the partial zeta function of the class of $\mathfrak{a}^{-1}$ at $2s/n$. This is the unfolding of Remark 5.3.13. The variable $y$ and the variables $c$ together are coordinates on $(0, \infty)^{S_\infty}$, and the integral over $c \in [0, 1)^r$ together with the sum over $\alpha$ modulo the units is the integral over all of $(0, \infty)^{S_\infty}$ for each class of associated elements. The constant depends only on $F$, through $n$, the number $w_F$ of roots of unity and the regulator, which is the Jacobian of the change of coordinates.

**Remark 5.3.28 (the Lean proof).** The file `Langlands/Tate/UnitTheta.lean` proves Proposition 5.3.27 for each number field. The vector $t(y, c)$ is `Langlands.Tate.unitScale`, with the fundamental units `NumberField.Units.fundSystem` of Mathlib, and $\Theta_\mathfrak{a}$ is `Langlands.Tate.unitTheta`. The three properties of $t(y, c)$ are `Langlands.Tate.prod_sqrt_unitScale`, `Langlands.Tate.unitScale_inv` and `Langlands.Tate.dedekindTheta_unitScale_add_int`. Part (1) is `Langlands.Tate.unitTheta_inv`, and the step with the two fundamental domains is `Langlands.Tate.setIntegral_comp_neg_of_periodic`, which uses the fundamental domains of Mathlib for the action of a lattice. Part (2) is `Langlands.Tate.one_le_unitTheta` and `Langlands.Tate.isBigO_unitTheta_sub_one`, and part (3) is `Langlands.Tate.continuousOn_unitTheta`, with the continuity of $\theta_\mathfrak{a}$ in `Langlands.Tate.continuousAt_dedekindTheta`. The pair $(\Theta_\mathfrak{a}, \Theta_{\mathfrak{a}^\vee})$ is `Langlands.Tate.unitThetaFEPair`, a `WeakFEPair` of Mathlib, so the continuation and the functional equation of $\Lambda(\Theta_\mathfrak{a}, s)$ follow from Mathlib as in Remark 5.3.18. The unfolding of the last paragraph is the subject of the next subsection.

### The unfolding of the unit average

We now carry out the unfolding that the last paragraph describes. We keep the notation of the previous subsection. Let $w_F$ be the number of roots of unity in $F$ and let $R_F$ be the regulator. For $\alpha \in F$ and $t \in (0, \infty)^{S_\infty}$ we write
$$\vartheta(\alpha, t) = \exp\Big(-\pi \sum_w n_w t_w |\alpha|_w^2\Big)$$
for one term of the theta function, so that $\theta_\mathfrak{a}(t) = \sum_{\alpha \in \mathfrak{a}} \vartheta(\alpha, t)$. The first step computes the integral of one term over all unit coordinates. The second step shows that the sum over $\mathfrak{a}$ and the integral over $[0, 1)^r$ together give these integrals, once for each principal ideal.

**Lemma 5.3.29 (one orbit of the units).** Let $\alpha \in F^\times$, let $\mathrm{Re}(s) > 0$ and put $s' = 2s/n$. Then
$$2^{r - r_2} \, n \, R_F \int_0^\infty \Big(\int_{\mathbb{R}^r} \vartheta(\alpha, t(y, c)) \, dc\Big) \, y^s \, \frac{dy}{y} = \Gamma_F(s') \, |N_{F/\mathbb{Q}}(\alpha)|^{-s'}.$$

*Proof.* The integral of Remark 5.3.13 at $s'$ is an integral over $(0, \infty)^{S_\infty}$ for the measure $\prod_w dt_w / t_w$. We change the variables to $(y, c) \in (0, \infty) \times \mathbb{R}^r$ with $t = t(y, c)$. Put $u = \log y$, $x_w = \log t_w$ and $\ell_i(w) = \log |\varepsilon_i|_w$. Then $x_w = u + 2 \sum_i c_i \ell_i(w)$. This is a linear map from $\mathbb{R}^{1 + r}$ to $\mathbb{R}^{S_\infty}$, and both spaces have dimension $r_1 + r_2 = r + 1$. Its matrix has the column $(1)_w$ and the columns $(2 \ell_i(w))_w$. We compute its determinant $D$. Take out the factor $2$ of each of the last $r$ columns. Then multiply the row of a place $w_0$ by $n_{w_0}$ and add to it $n_w$ times each other row $w$. The new row is $(n, 0, \dots, 0)$, because $\sum_w n_w = n$ and $\sum_w n_w \ell_i(w) = 0$ by the product formula. So
$$|D| = \frac{2^r \, n}{n_{w_0}} \, \big|\det(\ell_i(w))_{w \ne w_0, \, i}\big| = \frac{2^r \, n}{n_{w_0}} \cdot \frac{R_F}{\prod_{w \ne w_0} n_w} = 2^{r - r_2} \, n \, R_F,$$
since $R_F = |\det(n_w \ell_i(w))_{w \ne w_0, \, i}|$ and $\prod_w n_w = 2^{r_2}$. In the variables $x$ the measure $\prod_w dt_w / t_w$ is the Lebesgue measure $dx$, and in the variables $(u, c)$ it is $|D| \, du \, dc = |D| \, dc \, dy / y$. The product formula also gives $\prod_w t(y, c)_w^{n_w s' / 2} = y^{n s' / 2} = y^s$. So the integral of Remark 5.3.13 is the left side of the lemma, by Fubini's theorem for the integrable function $\vartheta(\alpha, t) \prod_w t_w^{n_w s'/2}$. Since $\mathrm{Re}(s') > 0$, Remark 5.3.13 gives the right side. $\square$

For a nonzero $\alpha \in \mathfrak{a}$ the ideal $(\alpha) \mathfrak{a}^{-1}$ is an integral ideal $I$ with $\mathfrak{a} I = (\alpha)$. Conversely, if $I$ is an integral ideal and $\mathfrak{a} I$ is principal, then each generator $\alpha_I$ of $\mathfrak{a} I$ is a nonzero element of $\mathfrak{a}$. The integral ideals $I$ with $\mathfrak{a} I$ principal are the integral ideals in the ideal class $[\mathfrak{a}]^{-1}$. For each such $I$ we fix a generator $\alpha_I$ of $\mathfrak{a} I$. Then $|N_{F/\mathbb{Q}}(\alpha_I)| = N(\mathfrak{a}) N(I)$, because the absolute norm is multiplicative and $N((\alpha)) = |N_{F/\mathbb{Q}}(\alpha)|$.

**Proposition 5.3.30 (the unfolding).** Let $\mathfrak{a}$ be a nonzero fractional ideal of $F$. For $y > 0$,
$$\Theta_\mathfrak{a}(y) - 1 = w_F \sum_I \int_{\mathbb{R}^r} \vartheta(\alpha_I, t(y, c)) \, dc,$$
where $I$ runs over the integral ideals in the class $[\mathfrak{a}]^{-1}$. The series converges, and each integral is finite.

*Proof.* The term $\alpha = 0$ of $\theta_\mathfrak{a}$ is $1$, and $[0, 1)^r$ has volume $1$. So
$$\Theta_\mathfrak{a}(y) - 1 = \int_{[0, 1)^r} \sum_{\alpha \in \mathfrak{a}, \, \alpha \ne 0} \vartheta(\alpha, t(y, c)) \, dc.$$
We sort the nonzero $\alpha \in \mathfrak{a}$ by the ideal $I = (\alpha) \mathfrak{a}^{-1}$. Two generators of the same principal ideal differ by a unit, so the $\alpha$ with a given $I$ are the elements $v \alpha_I$ with $v \in \mathcal{O}_F^\times$, and $v \mapsto v \alpha_I$ is injective. By the unit theorem, each unit is $v = \zeta \prod_i \varepsilon_i^{k_i}$ for a unique root of unity $\zeta$ and a unique $k \in \mathbb{Z}^r$. Since $|\zeta|_w = 1$ and $t(y, c + k)_w = t(y, c)_w \, |\prod_i \varepsilon_i^{k_i}|_w^2$,
$$\vartheta(v \alpha_I, t(y, c)) = \vartheta(\alpha_I, t(y, c + k)).$$
All the terms are positive, so we can exchange the sums and the integral by the theorem of monotone convergence. This gives
$$\Theta_\mathfrak{a}(y) - 1 = \sum_I w_F \sum_{k \in \mathbb{Z}^r} \int_{[0, 1)^r} \vartheta(\alpha_I, t(y, c + k)) \, dc = w_F \sum_I \int_{\mathbb{R}^r} \vartheta(\alpha_I, t(y, c)) \, dc.$$
The last step holds because the translates $[0, 1)^r + k$ for $k \in \mathbb{Z}^r$ are disjoint and cover $\mathbb{R}^r$. The left side is finite by part (2) of Proposition 5.3.27, so the series converges and each term is finite. $\square$

When $r = 0$ the integrals are values of $\vartheta$, and the proposition is the count of Theorem 5.3.22 in the proof of part (2): each principal ideal $\mathfrak{a} I$ has exactly $w_F$ generators. For $r > 0$ each principal ideal has infinitely many generators, and the integral over $\mathbb{R}^r$ absorbs the infinite part of this count. This is the point of the average over the units.

**Corollary 5.3.31 (the Mellin transform as a Dirichlet series).** Let $\mathfrak{a}$ be a nonzero fractional ideal of $F$. For $\mathrm{Re}(s) > n/2$ and $s' = 2s/n$,
$$\Lambda(\Theta_\mathfrak{a}, s) = \frac{w_F}{2^{r - r_2} \, n \, R_F} \, \Gamma_F(s') \sum_I |N_{F/\mathbb{Q}}(\alpha_I)|^{-s'} = \frac{w_F}{2^{r - r_2} \, n \, R_F} \, \Gamma_F(s') \, N(\mathfrak{a})^{-s'} \sum_I N(I)^{-s'},$$
where $I$ runs over the integral ideals in the class $[\mathfrak{a}]^{-1}$.

*Proof.* Multiply the identity of Proposition 5.3.30 by $y^{s - 1}$ and integrate over $(0, \infty)$. The terms of the series are $y^{s - 1}$ times positive functions of $y$. So the sum of the absolute values of the terms is $|y^{s - 1}| \, (\Theta_\mathfrak{a}(y) - 1)$, and this function is integrable for $\mathrm{Re}(s) > n/2$, as in the discussion after Proposition 5.3.27. So we can integrate the series term by term, by the theorem of dominated convergence. Lemma 5.3.29 gives the integral of each term, since $\mathrm{Re}(s) > n/2 > 0$. The second form uses $|N_{F/\mathbb{Q}}(\alpha_I)| = N(\mathfrak{a}) N(I)$. $\square$

The sum $\zeta(s', C) = \sum_{I \in C} N(I)^{-s'}$ over the integral ideals of a class $C$ is the partial zeta function of $C$, and $\zeta_F = \sum_C \zeta(\cdot, C)$. So Corollary 5.3.31 says that $N(\mathfrak{a})^{s'} \Lambda(\Theta_\mathfrak{a}, s)$ is a constant times $\Gamma_F(s') \zeta(s', [\mathfrak{a}]^{-1})$. To finish the proof of the functional equation of $\zeta_F$, choose an ideal $\mathfrak{a}_C$ in each class and sum over the classes. The functional equation of $\Lambda(\Theta_\mathfrak{a}, s)$ after Proposition 5.3.27 relates $\mathfrak{a}$ and $\mathfrak{a}^\vee = \mathfrak{a}^{-1} \mathfrak{D}^{-1}$, and $[\mathfrak{a}] \mapsto [\mathfrak{a}^\vee]$ is a bijection of the class group. This is the argument of the proof of part (1) of Theorem 5.3.22, with Lemma 5.3.21 for the independence of the choice of $\mathfrak{a}_C$. Theorem 5.3.34 below gives the details.

**Remark 5.3.32 (the Lean proof).** The file `Langlands/Tate/UnitMellin.lean` proves Lemma 5.3.29 as `Langlands.Tate.integral_unitScale`. The term $\vartheta(\alpha, t)$ is `Langlands.Tate.thetaTerm`, and the constant $2^{-r_2} n R_F$ is `Langlands.Tate.unitConst`. The Lean proof does not compute the determinant $D$ directly. It uses the map `expMapBasis` of Mathlib, which sends $x \in \mathbb{R}^{S_\infty}$ to the point with the coordinates $e^{x_{w_0}} \prod_i |\varepsilon_i|_w^{x_{w_i}}$, and whose Jacobian is in Mathlib. The formula in these coordinates is `Langlands.Tate.unitConst_mul_integral_expMapBasis`, and the substitution $c \mapsto 2c$ gives the factor $2^r$. The file `Langlands/Tate/UnitUnfold.lean` proves Proposition 5.3.30 and Corollary 5.3.31. The ideal $(\alpha) \mathfrak{a}^{-1}$ is `Langlands.Tate.idealOf`, the set of the ideals $I$ is `Langlands.Tate.Orbits`, and the generator $\alpha_I$ is `Langlands.Tate.orbitRep`. The decomposition $v = \zeta \prod_i \varepsilon_i^{k_i}$ of the units is `Langlands.Tate.unitsEquiv`. The tiling of $\mathbb{R}^r$ by the translates of $[0, 1)^r$ is `Langlands.Tate.lintegral_eq_tsum_unitCube`. The proposition is first proved with values in $[0, \infty]$, as `Langlands.Tate.lintegral_unitCube_eq_tsum`, and then as a convergent series of real numbers, as `Langlands.Tate.hasSum_unitTheta_sub_one`. The first form of Corollary 5.3.31 is `Langlands.Tate.hasSum_Λ_unitThetaFEPair`. In Lean the set `Orbits` is the set of the integral ideals $I$ with $\mathfrak{a} I$ principal. The file `Langlands/Tate/UnitClass.lean` proves that this set is the class $[\mathfrak{a}]^{-1}$, as `Langlands.Tate.mem_orbits_iff`, and that $|N_{F/\mathbb{Q}}(\alpha_I)| = N(\mathfrak{a}) N(I)$, as `Langlands.Tate.abs_norm_orbitRep`. The second form of Corollary 5.3.31 is `Langlands.Tate.hasSum_Λ_unitThetaFEPair_absNorm`, and its form as a series over all the nonzero integral ideals is `Langlands.Tate.hasSum_Λ_unitThetaFEPair_class`. The sum over the classes of the last paragraph is Theorem 5.3.34 below.

### The functional equation of the Dedekind zeta function

We now sum over the ideal classes and prove the functional equation of $\zeta_F$ for each number field $F$. Let $n$, $r$, $r_2$, $w_F$ and $R_F$ be as in Corollary 5.3.31. For a nonzero fractional ideal $\mathfrak{a}$ of $F$ put
$$\varphi_\mathfrak{a}(u) = |d_F|^{u/2} \, N(\mathfrak{a})^u \, \Lambda(\Theta_\mathfrak{a}, n u / 2).$$
When $F$ is imaginary quadratic, $\varphi_\mathfrak{a}$ is not the function $\psi_\mathfrak{a}$ of Lemma 5.3.21, because $\Theta_\mathfrak{a}$ is the average over the units and not the theta function of the lattice $\mathfrak{a}$.

**Lemma 5.3.33 (the function of a fractional ideal).** Let $\mathfrak{a}$ be a nonzero fractional ideal of $F$, and let $\mathfrak{a}^\vee = \mathfrak{a}^{-1} \mathfrak{D}^{-1}$.
1. The function $\varphi_\mathfrak{a}$ is holomorphic on $\mathbb{C} \setminus \{0, 1\}$, and $\varphi_\mathfrak{a}(1 - u) = \varphi_{\mathfrak{a}^\vee}(u)$ for $u \ne 0, 1$.
2. For $\mathrm{Re}(u) > 1$, $\varphi_\mathfrak{a}(u) = \frac{w_F}{2^{r - r_2} \, n \, R_F} \, |d_F|^{u/2} \, \Gamma_F(u) \, \zeta(u, [\mathfrak{a}]^{-1})$.
3. If $\mathfrak{b}$ is a nonzero fractional ideal in the class of $\mathfrak{a}$, then $\varphi_\mathfrak{b}(u) = \varphi_\mathfrak{a}(u)$ for $u \ne 0, 1$.

Lean: `Langlands.Tate.classXi_one_sub`, `Langlands.Tate.hasSum_classXi`, `Langlands.Tate.classXi_eq_of_mk_eq`

*Proof.* For (1), the function $\Lambda(\Theta_\mathfrak{a}, s)$ is holomorphic outside $s = 0$ and $s = n/2$, as in the discussion after Proposition 5.3.27. For $s = n u / 2$ these points are $u = 0$ and $u = 1$. The factors $|d_F|^{u/2}$ and $N(\mathfrak{a})^u$ are entire functions of $u$. So $\varphi_\mathfrak{a}$ is holomorphic on $\mathbb{C} \setminus \{0, 1\}$. Put $s = n u / 2$. Then $n (1 - u) / 2 = n/2 - s$, and the functional equation of $\Lambda(\Theta_\mathfrak{a}, s)$ gives
$$\varphi_\mathfrak{a}(1 - u) = |d_F|^{(1 - u)/2} N(\mathfrak{a})^{1 - u} \, \frac{\Lambda(\Theta_{\mathfrak{a}^\vee}, s)}{N(\mathfrak{a}) \, |d_F|^{1/2}} = |d_F|^{-u/2} N(\mathfrak{a})^{-u} \, \Lambda(\Theta_{\mathfrak{a}^\vee}, s).$$
Since $N(\mathfrak{D}) = |d_F|$, we have $N(\mathfrak{a}^\vee) = N(\mathfrak{a})^{-1} |d_F|^{-1}$. So $|d_F|^{u/2} N(\mathfrak{a}^\vee)^u = |d_F|^{-u/2} N(\mathfrak{a})^{-u}$, and the right side is $\varphi_{\mathfrak{a}^\vee}(u)$.

For (2), put $s = n u / 2$. Then $\mathrm{Re}(s) = n \, \mathrm{Re}(u) / 2 > n / 2$ and $s' = 2s/n = u$. Corollary 5.3.31 gives
$$\Lambda(\Theta_\mathfrak{a}, s) = \frac{w_F}{2^{r - r_2} \, n \, R_F} \, \Gamma_F(u) \, N(\mathfrak{a})^{-u} \, \zeta(u, [\mathfrak{a}]^{-1}).$$
We multiply by $|d_F|^{u/2} N(\mathfrak{a})^u$, and the factor $N(\mathfrak{a})^{-u}$ cancels.

For (3), first let $\mathrm{Re}(u) > 1$. Then $[\mathfrak{b}]^{-1} = [\mathfrak{a}]^{-1}$, so the right sides of (2) for $\mathfrak{a}$ and for $\mathfrak{b}$ are equal. Both functions are holomorphic on $U = \mathbb{C} \setminus \{0, 1\}$ by (1). The set $U$ is open and connected, and the two functions agree on the half plane $\mathrm{Re}(u) > 1$. By the identity theorem they agree on $U$. $\square$

**Theorem 5.3.34 (the functional equation of the Dedekind zeta function).** Let $F$ be a number field. Choose a nonzero fractional ideal $\mathfrak{a}_C$ in each ideal class $C$ of $F$, and put
$$\xi_F(u) = \frac{2^{r - r_2} \, n \, R_F}{w_F} \sum_C \varphi_{\mathfrak{a}_C}(u).$$
1. The function $\xi_F$ is holomorphic on $\mathbb{C} \setminus \{0, 1\}$, and it does not depend on the choice of the ideals $\mathfrak{a}_C$.
2. For $\mathrm{Re}(u) > 1$, $\xi_F(u) = |d_F|^{u/2} \, \Gamma_F(u) \, \zeta_F(u)$.
3. For $u \ne 0, 1$, $\xi_F(1 - u) = \xi_F(u)$.

Lean: `Langlands.Tate.dedekindXi_one_sub`, `Langlands.Tate.dedekindXi_eq`, `Langlands.Tate.differentiableAt_dedekindXi`

*Proof.* For (1), the class group is finite, so $\xi_F$ is a finite sum of the functions of Lemma 5.3.33. Each of them is holomorphic on $\mathbb{C} \setminus \{0, 1\}$ by part (1) of the lemma, and it does not depend on the choice of $\mathfrak{a}_C$ by part (3).

For (2), part (2) of Lemma 5.3.33 gives
$$\xi_F(u) = |d_F|^{u/2} \, \Gamma_F(u) \sum_C \zeta(u, C^{-1}),$$
because $[\mathfrak{a}_C] = C$. The map $C \mapsto C^{-1}$ is a bijection of the class group. Each nonzero integral ideal is in exactly one class, and for $\mathrm{Re}(u) > 1$ the series of $\zeta_F(u)$ converges absolutely. So $\sum_C \zeta(u, C^{-1}) = \sum_C \zeta(u, C) = \zeta_F(u)$.

For (3), part (1) of Lemma 5.3.33 gives $\varphi_{\mathfrak{a}_C}(1 - u) = \varphi_{\mathfrak{a}_C^\vee}(u)$. The class of $\mathfrak{a}_C^\vee = \mathfrak{a}_C^{-1} \mathfrak{D}^{-1}$ is $C^* = (C [\mathfrak{D}])^{-1}$. So $\varphi_{\mathfrak{a}_C^\vee}(u) = \varphi_{\mathfrak{a}_{C^*}}(u)$ by part (3) of the lemma. The map $C \mapsto C^*$ is a bijection of the class group, because $(C^*)^* = C$. Thus
$$\sum_C \varphi_{\mathfrak{a}_C}(1 - u) = \sum_C \varphi_{\mathfrak{a}_{C^*}}(u) = \sum_C \varphi_{\mathfrak{a}_C}(u),$$
and we multiply by the constant. $\square$

By Remark 5.3.13, $\Gamma_F(u) = \Gamma_\mathbb{R}(u)^{r_1} (\Gamma_\mathbb{C}(u)/2)^{r_2}$. So part (2) says $\xi_F(u) = 2^{-r_2} |d_F|^{u/2} \Lambda_F(u)$, with $\Lambda_F$ as in Corollary 5.4.8. Then part (3) is the functional equation $\Lambda_F(u) = |d_F|^{1/2 - u} \Lambda_F(1 - u)$ of Corollary 5.4.8. The function $1/\Gamma$ is entire, so $\zeta_F(u) = |d_F|^{-u/2} \xi_F(u) / \Gamma_F(u)$ extends to a holomorphic function on $\mathbb{C} \setminus \{0, 1\}$. This is Hecke's proof of the functional equation of $\zeta_F$. It uses the Poisson summation formula on the lattices $\mathfrak{a}$, and not the adelic Fourier analysis of Section 5.4. When $F$ is imaginary quadratic, we have $r = 0$, $r_2 = 1$, $n = 2$ and $R_F = 1$, and the function $\xi_F$ of Corollary 5.3.23 is $w_F$ times the function $\xi_F$ of the theorem.

**Remark 5.3.35 (the Lean proof).** The file `Langlands/Tate/DedekindFE.lean` proves Lemma 5.3.33 and Theorem 5.3.34 for each number field, with `NumberField.dedekindZeta` of Mathlib for $\zeta_F$. The function $\varphi_\mathfrak{a}$ is `Langlands.Tate.classXi`, and $\xi_F$ is `Langlands.Tate.dedekindXi`. Part (2) of Lemma 5.3.33 is a series over all the nonzero integral ideals $I$ of $F$, in which the term of $I$ is $0$ if $[I] \ne [\mathfrak{a}]^{-1}$. This form makes the sum over the classes in part (2) of Theorem 5.3.34 a sum of series over one index set. The ideal $\mathfrak{a}_C$ is the integral ideal `Langlands.Tate.classIdeal` of $C$, as a fractional ideal `Langlands.Tate.classRepUnit`. The bijection $C \mapsto C^*$ is `Langlands.Tate.dualClass`. The theta formula after Proposition 5.3.27 has a root number. The Lean proof shows that the root number of the pair of $\mathfrak{a}$, after the exchange of the two theta functions, is the root number of the pair of $\mathfrak{a}^\vee$. This is `Langlands.Tate.symm_Λ_unitThetaFEPair`. The residue of $\xi_F$ at $u = 1$ and the order of $\zeta_F$ at $u = 0$ are not in Lean yet. Theorem 5.3.34 is the case of the trivial character of Theorem 5.5.3, but `Langlands.HeckeFunctionalEquation` asserts Theorem 5.5.3 for all Hecke characters, and it is not proved yet.
