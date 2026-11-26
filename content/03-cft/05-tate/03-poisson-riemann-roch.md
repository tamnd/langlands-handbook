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
This is a product of integrals of one variable, each of which is the integral of Euler for $\Gamma$. In the notation of Definition 5.2.2, $\Gamma_F(s) = \Gamma_\mathbb{R}(s)^{r_1} (\Gamma_\mathbb{C}(s)/2)^{r_2}$. The identity is `Langlands.Tate.integral_exp_mul_prod_eq_gammaK`, and $\Gamma_F$ is `Langlands.Tate.gammaK`. To finish the proof, one sums over the nonzero $\alpha \in \mathfrak{a}$ modulo the units $\mathcal{O}_F^\times$, so that the sum of $|N(\alpha)|^{-s}$ becomes $N(\mathfrak{a})^{-s}$ times the partial zeta function of the class of $\mathfrak{a}^{-1}$. The units act on the variables $t_w$, and the integral over $(0, \infty)^{S_\infty}$ modulo this action is an integral over a fundamental domain of the unit lattice of Volume 1, Section 1.3. Then one splits the integral at $\prod_w t_w^{n_w} = 1$ and applies the theta formula to the part with $\prod_w t_w^{n_w} < 1$. This gives the meromorphic continuation and the functional equation, with the poles at $s = 0$ and $s = 1$ and the residue of Proposition 5.4.4. These last steps are not in Lean yet, so `Langlands.HeckeFunctionalEquation` is not proved even for the trivial character of a number field other than $\mathbb{Q}$.
