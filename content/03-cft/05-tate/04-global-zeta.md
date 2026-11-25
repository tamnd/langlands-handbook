---
title: The global zeta integral
nodes: []
sources: [CF67, Neu99]
status: drafted
drafted_by: writer
reviewed_by: []
---
## The global zeta integral

This section proves Tate's main theorem: the global zeta integral of a Hecke character has a meromorphic continuation and a functional equation, with poles only when the character is a power of the idele norm. The proof uses only Theorem 5.3.5 and the compactness of $C_F^1$. The local theory of Section 5.2 is not used here. It enters in Section 5.5, where a good choice of $f$ turns the zeta integral into an $L$-function. We keep the notation of Section 5.3. Let $r_1$ and $r_2$ be the numbers of real and complex places of $F$, $n = [F : \mathbb{Q}]$, $h$ the class number, $R$ the regulator of Definition 1.3.10 of Volume 1, and $w$ the number of roots of unity in $F$.

### Hecke characters

**Definition 5.4.1 (Hecke characters).** A *Hecke character* of $F$ is a continuous homomorphism $\chi : J_F \to \mathbb{C}^\times$ that is trivial on $F^\times$, that is, a character of $C_F = J_F / F^\times$. Its *component* at a place $v$ is the character $\chi_v$ of $F_v^\times$ obtained by restriction to the factor $F_v^\times$ of $J_F$.

Hecke called these characters *Größencharaktere*. Tate calls them quasi-characters of $C_F$. They need not be unitary and need not have finite order. The idele norm $|\cdot|_\mathbb{A}$ is a Hecke character by the product formula, Theorem 3.3.4 of Volume 1.

**Proposition 5.4.2 (the structure of a Hecke character).** Let $\chi$ be a Hecke character of $F$.
1. For almost all finite places $v$ the component $\chi_v$ is unramified, and $\chi(x) = \prod_v \chi_v(x_v)$ for all $x \in J_F$.
2. There is a unique real number $\sigma$ with $|\chi(x)| = |x|_\mathbb{A}^\sigma$ for all $x$. Thus $\chi = \chi_0 |\cdot|_\mathbb{A}^\sigma$ with $\chi_0$ unitary, and $\sigma(\chi_v) = \sigma$ for each place $v$.
3. The character $\chi$ is trivial on $J_F^1$ if and only if $\chi = |\cdot|_\mathbb{A}^{s_0}$ for some $s_0 \in \mathbb{C}$. Then $s_0$ is unique, and $\mathrm{Re}(s_0) = \sigma$.
4. $\chi(-1) = 1$, where $-1 \in F^\times \subset J_F$.

Lean: not stated yet

*Proof.* Part 1 is Proposition 3.1.4 of Volume 1, for the restricted product of the groups $F_v^\times$ with respect to the groups $\mathcal{O}_v^\times$. For part 2, the map $x \mapsto |\chi(x)|$ is a continuous homomorphism $C_F \to \mathbb{R}_{>0}$. The image of the compact group $C_F^1$ (Theorem 3.5.2 of Volume 1) is a compact subgroup of $\mathbb{R}_{>0}$, so it is 1. By Proposition 3.4.6 of Volume 1, $|\chi|$ factors through $|\cdot|_\mathbb{A} : C_F / C_F^1 \cong \mathbb{R}_{>0}$, and a continuous homomorphism $\mathbb{R}_{>0} \to \mathbb{R}_{>0}$ is $t \mapsto t^\sigma$ for a unique real $\sigma$. The restriction of $|\cdot|_\mathbb{A}$ to $F_v^\times$ is $|\cdot|_v$, so $|\chi_v| = |\cdot|_v^\sigma$. Part 3 follows in the same way: $\chi$ factors through $J_F / J_F^1 \cong \mathbb{R}_{>0}$, and the characters of $\mathbb{R}_{>0}$ are $t \mapsto t^{s_0}$. Part 4 holds because $\chi$ is trivial on $F^\times$. $\square$

Part 4 gives $\prod_v \chi_v(-1) = 1$. This is a relation between the signs of $\chi$ at the real places and its finite components. At an infinite place, $\chi_v$ has parameters $(a_v, t_v)$ or $(n_v, t_v)$ as in Proposition 5.1.7, with $\mathrm{Re}(t_v) = \sigma$.

### Measures and the volume of $C_F^1$

**Definition 5.4.3 (the measures).** On $J_F$ let $d^\times x = \prod_v d^\times x_v$, the product of Tate's local measures of Definition 5.1.5 for the standard characters $\psi_v$. Let $\beta : \mathbb{R}_{>0} \to J_F$ be the homomorphism with $\beta(t)_v = t^{1/n}$ at the infinite places and $\beta(t)_v = 1$ at the finite places. Then $|\beta(t)|_\mathbb{A} = t$, and $x \mapsto (x / \beta(|x|_\mathbb{A}), |x|_\mathbb{A})$ is an isomorphism $J_F \cong J_F^1 \times \mathbb{R}_{>0}$. Let $d^\times x^1$ be the Haar measure on $J_F^1$ with $d^\times x = d^\times x^1 \cdot dt/t$ under this isomorphism. On $C_F^1 = J_F^1 / F^\times$ and on $C_F$ we use the quotient measures by the counting measure on the discrete group $F^\times$. Let $\kappa = \mathrm{vol}(C_F^1)$.

The product measure exists, because $\mathrm{vol}(\mathcal{O}_v^\times) = q_v^{-d_v/2} = 1$ for almost all $v$, by the proof of Proposition 3.3.2 of Volume 1. The volume $\kappa$ is finite, because $C_F^1$ is compact. Tate shows that $d^\times x^1$ does not depend on the choice of $\beta$, see [CF67], Chapter XV, Section 4.3. For $\beta$ as above, $\beta(\mathbb{R}_{>0})$ maps isomorphically to $C_F / C_F^1$, which gives the isomorphism $C_F \cong C_F^1 \times \mathbb{R}_{>0}$ of Proposition 3.4.6 of Volume 1.

**Proposition 5.4.4 (the volume of $C_F^1$).** For the measures of Definition 5.4.3,
$$\kappa = \mathrm{vol}(C_F^1) = \frac{2^{r_1} (2\pi)^{r_2} \, h R}{w \sqrt{|d_F|}}.$$

Lean: not stated yet

*Proof.* Let $\hat U = \prod_{v \nmid \infty} \mathcal{O}_v^\times$, let $U = F_\infty^\times \times \hat U$, and let $U^1 = U \cap J_F^1$. By Theorem 3.4.7 of Volume 1, $J_F / F^\times U \cong \mathrm{Cl}_F$. Each coset of $F^\times U$ meets $J_F^1$, because $U$ contains $\beta(\mathbb{R}_{>0})$. As $F^\times \subset J_F^1$, we get $J_F^1 \cap F^\times U = F^\times U^1$, and so $J_F^1 / F^\times U^1 \cong \mathrm{Cl}_F$. Thus the image of $U^1$ in $C_F^1$ is an open subgroup of index $h$, and it is isomorphic to $U^1 / (U^1 \cap F^\times) = U^1 / \mathcal{O}_F^\times$. So $\kappa = h \cdot \mathrm{vol}(U^1 / \mathcal{O}_F^\times)$.

We compute the measure on $U$. The finite part gives $\mathrm{vol}(\hat U) = \prod_v q_v^{-d_v/2} = |d_F|^{-1/2}$. For the infinite part, let $\ell : F_\infty^\times \to \mathbb{R}^{r_1 + r_2}$ be the map $x \mapsto (\log |x_v|_v)_v$. Its kernel is $K_\infty = \{\pm 1\}^{r_1} \times U(1)^{r_2}$. At a real place, $dx / |x|$ is the counting measure on $\{\pm 1\}$ times $du$, where $u = \log |x|$. At a complex place, write $z = r e^{i\theta}$ and $u = \log |z|_\mathbb{C} = 2 \log r$. Then $2 \, dx \, dy / |z|_\mathbb{C} = 2 r^{-1} dr \, d\theta = du \, d\theta$. So $d^\times x_\infty$ is the product of a measure of total mass $2^{r_1} (2\pi)^{r_2}$ on $K_\infty$ and the Lebesgue measure $du$ on $\mathbb{R}^{r_1 + r_2}$.

The norm one condition is $\sum_v u_v = 0$, the hyperplane $H$ of Volume 1, Section 1.3. In the coordinates $u$, the map $t \mapsto \beta(t)$ is $\tau = \log t \mapsto \tau e / n$, where $e$ has the entry 1 at the real places and 2 at the complex places, and the entries of $e/n$ have sum 1. Let $r = r_1 + r_2 - 1$, and use the first $r$ coordinates on $H$. The map $(u_1, \dots, u_r, \tau) \mapsto u^1 + \tau e/n$, with $u^1 \in H$, has determinant 1: add all rows to the last row, which becomes $(0, \dots, 0, 1)$. So the measure $d^\times x^1$ on $U^1$ is the product of the measure on $K_\infty$, the measure on $\hat U$, and the measure on $H$ given by the projection to the first $r$ coordinates. For this measure the lattice $\ell(\mathcal{O}_F^\times)$ has covolume $R$, by Definition 1.3.10 of Volume 1. The kernel of $\ell$ on $\mathcal{O}_F^\times$ is $\mu(F)$, of order $w$, and it acts freely on $K_\infty \times \hat U$. Thus
$$\mathrm{vol}(U^1 / \mathcal{O}_F^\times) = \frac{2^{r_1} (2\pi)^{r_2} \cdot |d_F|^{-1/2} \cdot R}{w}.$$
Multiplication by $h$ gives the claim. $\square$

### The zeta integral and its Euler product

**Definition 5.4.5 (the global zeta integral).** Let $\chi$ be a Hecke character and $f \in \mathcal{S}(\mathbb{A}_F)$. The *global zeta integral* is
$$Z(f, \chi, s) = \int_{J_F} f(x) \chi(x) |x|_\mathbb{A}^s \, d^\times x.$$

**Proposition 5.4.6 (convergence and the Euler product).** Let $\chi$ have exponent $\sigma$. The integral $Z(f, \chi, s)$ converges absolutely for $\mathrm{Re}(s) > 1 - \sigma$, and it is holomorphic there. If $f = \otimes_v f_v$, then
$$Z(f, \chi, s) = \prod_v Z(f_v, \chi_v, s), \qquad \mathrm{Re}(s) > 1 - \sigma,$$
and the product converges absolutely. Let $S$ be a finite set of places that contains the infinite places, the places where $f_v \ne 1_{\mathcal{O}_v}$, $d_v \ne 0$ or $\chi_v$ is ramified. Then $Z(f_v, \chi_v, s) = L(\chi_v, s)$ for $v \notin S$.

Lean: not stated yet

*Proof.* For $v \notin S$, the example after Proposition 5.1.9 gives $Z(f_v, \chi_v, s) = L(\chi_v, s) = (1 - \chi_v(\varpi_v) q_v^{-s})^{-1}$. Let $u = \sigma + \mathrm{Re}(s)$. Then $|\chi_v(\varpi_v) q_v^{-s}| = q_v^{-u}$. Each rational prime $p$ has at most $n$ places above it, and $q_v \ge p$ for these places. So $\sum_v q_v^{-u} \le n \sum_p p^{-u}$, which is finite for $u > 1$. Thus the product of the factors $(1 - q_v^{-u})^{-1}$ converges, and so does the product of the $L(\chi_v, s)$.

For a finite set $T \supset S$ let $J_T = \prod_{v \in T} F_v^\times \times \prod_{v \notin T} \mathcal{O}_v^\times$. These open subgroups exhaust $J_F$. On $J_T$ the function $|f(x) \chi(x) |x|^s|$ is a product, and the factors at $v \notin T$ are 1 on $\mathcal{O}_v^\times$. So its integral over $J_T$ is $\prod_{v \in T} Z(|f_v|, |\chi_v|, \mathrm{Re}(s))$. For $v \in T \smallsetminus S$ the factor is $(1 - q_v^{-u})^{-1}$. By monotone convergence the integral over $J_F$ is the infinite product, which is finite for $u > 1$. The same computation without the absolute values, and dominated convergence, give the product formula for $Z(f, \chi, s)$. A general $f$ is a finite linear combination of factorizable functions. The bounds are locally uniform in $s$, so $Z$ is holomorphic. $\square$

### Tate's main theorem

**Theorem 5.4.7 (the global functional equation).** Let $\chi$ be a Hecke character with exponent $\sigma$, and let $f \in \mathcal{S}(\mathbb{A}_F)$.
1. The function $Z(f, \chi, s)$ on $\mathrm{Re}(s) > 1 - \sigma$ extends to a meromorphic function on $\mathbb{C}$.
2. As meromorphic functions, $Z(f, \chi, s) = Z(\hat f, \chi^{-1}, 1 - s)$.
3. If $\chi$ is not trivial on $J_F^1$, then $Z(f, \chi, s)$ is entire. If $\chi = |\cdot|_\mathbb{A}^{s_0}$, then $Z(f, \chi, s)$ is holomorphic outside $\{-s_0, 1 - s_0\}$. At these points it has at most simple poles, with residue $-\kappa f(0)$ at $s = -s_0$ and residue $\kappa \hat f(0)$ at $s = 1 - s_0$.

Lean: not stated yet

*Proof.* Let $\mathrm{Re}(s) > 1 - \sigma$. Split $J_F$ into the parts $|x|_\mathbb{A} \ge 1$ and $|x|_\mathbb{A} \le 1$. Their intersection $J_F^1$ has measure 0. Write $Z = Z_+ + Z_-$ accordingly, with
$$Z_+(f, \chi, s) = \int_{|x| \ge 1} f(x) \chi(x) |x|^s \, d^\times x.$$
The function $Z_+(f, \chi, s)$ is entire. Indeed, for $s$ in a compact set and $|x| \ge 1$, we have $|x|^{\mathrm{Re}(s)} \le |x|^{c}$ for a real $c > 1 - \sigma$ that is larger than $\mathrm{Re}(s)$ on the compact set. The integral of $|f(x)| |x|^{\sigma + c}$ over $|x| \ge 1$ is finite by Proposition 5.4.6.

For $Z_-$ we fold the integral over $F^\times$. Since $\chi$ and $|\cdot|$ are trivial on $F^\times$,
$$Z_-(f, \chi, s) = \int_{C_F, \, |x| \le 1} \Big( \sum_{\xi \in F^\times} f(\xi x) \Big) \chi(x) |x|^s \, d^\times x.$$
Apply (5.3.1) with $a = x$. The sum in the integrand is $|x|^{-1} \sum_{\xi \in F^\times} \hat f(\xi x^{-1}) + |x|^{-1} \hat f(0) - f(0)$. This splits $Z_-$ into two terms, and both converge absolutely, as the computation shows.

The first term is
$$\int_{C_F, \, |x| \le 1} \sum_{\xi \in F^\times} \hat f(\xi x^{-1}) \chi(x) |x|^{s-1} \, d^\times x = \int_{C_F, \, |x| \ge 1} \sum_{\xi \in F^\times} \hat f(\xi x) \chi^{-1}(x) |x|^{1-s} \, d^\times x = Z_+(\hat f, \chi^{-1}, 1 - s).$$
The first step is the substitution $x \mapsto x^{-1}$, which preserves the Haar measure. The second step unfolds the sum again.

The second term is
$$\int_{C_F, \, |x| \le 1} \big( \hat f(0) |x|^{s-1} - f(0) |x|^s \big) \chi(x) \, d^\times x = \int_0^1 \big( \hat f(0) t^{s-1} - f(0) t^s \big) \chi(\beta(t)) \Big( \int_{C_F^1} \chi(y) \, d^\times y \Big) \frac{dt}{t},$$
by the decomposition $C_F \cong C_F^1 \times \mathbb{R}_{>0}$ of Definition 5.4.3. The integral of a nontrivial character over the compact group $C_F^1$ is 0. So the second term is 0 if $\chi$ is not trivial on $J_F^1$. If $\chi = |\cdot|^{s_0}$, then $\chi(\beta(t)) = t^{s_0}$, the inner integral is $\kappa$, and the second term is
$$\kappa \Big( \frac{\hat f(0)}{s + s_0 - 1} - \frac{f(0)}{s + s_0} \Big), \qquad \mathrm{Re}(s) > 1 - \sigma.$$
Let $\delta_\chi = 1$ if $\chi$ is trivial on $J_F^1$, and $\delta_\chi = 0$ otherwise. We have shown, for $\mathrm{Re}(s) > 1 - \sigma$,
$$Z(f, \chi, s) = Z_+(f, \chi, s) + Z_+(\hat f, \chi^{-1}, 1 - s) + \delta_\chi \, \kappa \Big( \frac{\hat f(0)}{s + s_0 - 1} - \frac{f(0)}{s + s_0} \Big). \tag{5.4.1}$$
The right side is meromorphic on $\mathbb{C}$. This proves part 1, and part 3 can be read off from it.

For part 2 replace $(f, \chi, s)$ by $(\hat f, \chi^{-1}, 1 - s)$ in the right side of (5.4.1). The character $\chi^{-1}$ is trivial on $J_F^1$ exactly when $\chi$ is, with $-s_0$ in place of $s_0$. As $\hat{\hat f}(x) = f(-x)$, we get $Z_+(\hat{\hat f}, \chi, s) = \chi(-1) Z_+(f, \chi, s) = Z_+(f, \chi, s)$, by part 4 of Proposition 5.4.2. Also $\hat{\hat f}(0) = f(0)$. The last term becomes
$$\kappa \Big( \frac{f(0)}{(1 - s) - s_0 - 1} - \frac{\hat f(0)}{(1 - s) - s_0} \Big) = \kappa \Big( \frac{\hat f(0)}{s + s_0 - 1} - \frac{f(0)}{s + s_0} \Big).$$
So the right side of (5.4.1) does not change. The right side for $(\hat f, \chi^{-1}, 1-s)$ is the continuation of $Z(\hat f, \chi^{-1}, 1-s)$ from $\mathrm{Re}(1 - s) > 1 + \sigma$. This proves part 2. $\square$

This is [CF67], Chapter XV, Theorem 4.4.1. The proof shows the source of the two poles. They come from the terms $\xi = 0$ in the Riemann-Roch theorem, which are lost when one sums over $F^\times$ instead of $F$. The residues are nonzero when $f(0) \ne 0$ and $\hat f(0) \ne 0$.

### The Dedekind zeta function

Let $\zeta_F(s) = \sum_\mathfrak{a} N(\mathfrak{a})^{-s} = \prod_\mathfrak{p} (1 - N(\mathfrak{p})^{-s})^{-1}$ for $\mathrm{Re}(s) > 1$, where $\mathfrak{a}$ runs over the nonzero ideals of $\mathcal{O}_F$, and let
$$\Lambda_F(s) = \Gamma_\mathbb{R}(s)^{r_1} \Gamma_\mathbb{C}(s)^{r_2} \zeta_F(s).$$

**Corollary 5.4.8 (the Dedekind zeta function).** The function $\Lambda_F(s)$ extends to a meromorphic function on $\mathbb{C}$. It is holomorphic except for simple poles at $s = 0$ and $s = 1$, and
$$\Lambda_F(s) = |d_F|^{1/2 - s} \Lambda_F(1 - s).$$
The residue of $\zeta_F(s)$ at $s = 1$ is
$$\mathrm{Res}_{s = 1} \zeta_F(s) = \frac{2^{r_1} (2\pi)^{r_2} \, h R}{w \sqrt{|d_F|}}.$$

Lean: not stated yet

*Proof.* Take $\chi = 1$, so $s_0 = 0$, and $f = \otimes_v f_v$ with $f_v = 1_{\mathcal{O}_v}$ at the finite places, $f_v(x) = e^{-\pi x^2}$ at the real places and $f_v(z) = e^{-2\pi z \bar z}$ at the complex places. By Propositions 5.2.3, 5.2.5 and 5.2.6, $Z(f_v, 1, s)$ is $q_v^{-d_v/2} (1 - q_v^{-s})^{-1}$, $\Gamma_\mathbb{R}(s)$ and $\pi \Gamma_\mathbb{C}(s)$. By Proposition 5.4.6,
$$Z(f, 1, s) = |d_F|^{-1/2} \pi^{r_2} \Lambda_F(s).$$
The transform is $\hat f = \otimes_v \hat f_v$ with $\hat f_v = q_v^{-d_v/2} 1_{\mathfrak{p}_v^{-d_v}}$ at the finite places, and the Gaussians are their own transforms. By Proposition 5.2.3 with $\chi = 1$, $Z(\hat f_v, 1, 1 - s) = q_v^{d_v (1/2 - s)} q_v^{-d_v/2} (1 - q_v^{s-1})^{-1}$. So
$$Z(\hat f, 1, 1 - s) = |d_F|^{1/2 - s} \, |d_F|^{-1/2} \pi^{r_2} \Lambda_F(1 - s).$$
Theorem 5.4.7 gives the continuation and the functional equation. We have $f(0) = 1$ and $\hat f(0) = |d_F|^{-1/2}$. So $Z(f, 1, s)$ has simple poles at $0$ and $1$, with residues $-\kappa$ and $\kappa |d_F|^{-1/2}$. At $s = 1$ we have $\Gamma_\mathbb{R}(1) = 1$ and $\Gamma_\mathbb{C}(1) = 1/\pi$. Thus $\mathrm{Res}_{s=1} \zeta_F(s) = \kappa$, and Proposition 5.4.4 gives the value. $\square$

This is the analytic class number formula that Volume 1 mentions after Definition 1.3.10. A proof with the classical methods of Hecke is in [Neu99], Chapter VII, Section 5. The residue $-\kappa$ at $s = 0$ gives the order and the leading coefficient of $\zeta_F$ at $s = 0$, see Exercise 7.
