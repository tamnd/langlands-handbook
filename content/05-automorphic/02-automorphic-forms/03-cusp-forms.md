---
title: Cusp forms and the cuspidal spectrum
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Cusp forms and the cuspidal spectrum

A modular form $f$ is a cusp form when its constant coefficient vanishes at every cusp. On $GL_2(\mathbb{A})$ all the cusps become one condition: the integral of $\varphi(u(x)g)$ over $x \in \mathbb{Q}\backslash\mathbb{A}$ vanishes for all $g$. This section defines this constant term, proves that $\phi_f$ is cuspidal exactly when $f$ is a cusp form, and proves that cusp forms decay rapidly on a Siegel set. So cusp forms are bounded and square integrable, and they form a part of $L^2$ that decomposes discretely. The model is the exponential decay of $f(x + iy)$ as $y \to \infty$, which comes from the vanishing of the constant coefficient.

### The constant term

Let $dx$ be the Haar measure on $\mathbb{Q}\backslash\mathbb{A}$ of total mass $1$. The quotient is compact by Volume 1, Theorem 3.2.4.

**Definition 2.3.1 (constant term).** Let $\varphi$ be a continuous function on $G(\mathbb{Q})\backslash G(\mathbb{A})$. Its *constant term* is the function
$$\varphi_U(g) = \int_{\mathbb{Q}\backslash\mathbb{A}} \varphi(u(x)g)\,dx, \qquad g \in G(\mathbb{A}).$$

Lean: `Langlands.HasVanishingConstantTerm` states that the constant terms vanish

The integral is well defined, since $\varphi(u(x)g)$ depends only on $x$ modulo $\mathbb{Q}$.

**Lemma 2.3.2 (properties of the constant term).** Let $\varphi$ be as in Definition 2.3.1.
1. The function $\varphi_U$ is left invariant under $U(\mathbb{A})$ and under $B(\mathbb{Q})$.
2. For $\gamma \in G(\mathbb{Q})$ the constant term along the unipotent group $\gamma^{-1}U\gamma$, that is $\int_{\mathbb{Q}\backslash\mathbb{A}}\varphi(\gamma^{-1}u(x)\gamma g)\,dx$, is $\varphi_U(\gamma g)$.
3. The map $\varphi \mapsto \varphi_U$ commutes with right translations and, for smooth $\varphi$, with right derivatives.

Lean: not formalized

*Proof.* The first claim for $U(\mathbb{A})$ follows from the invariance of $dx$. For $b = \left(\begin{smallmatrix} a & c \\ 0 & d \end{smallmatrix}\right) \in B(\mathbb{Q})$ we have $u(x)b = b\,u(d x/a)$, so
$$\varphi_U(bg) = \int \varphi(b\,u(dx/a)g)\,dx = \int \varphi(u(dx/a)g)\,dx = \varphi_U(g),$$
since $\varphi$ is left invariant under $b$ and the map $x \mapsto dx/a$ preserves $\mathbb{Q}$ and, by the product formula, the measure $dx$. For the second claim, $\varphi(\gamma^{-1}u(x)\gamma g) = \varphi(u(x)\gamma g)$ by left invariance. The third claim holds since the integral is over the left variable. $\square$

**Definition 2.3.3 (cusp form).** An automorphic form $\varphi$ is a *cusp form* if $\varphi_U = 0$. We write $\mathcal{A}_0(G)$ and $\mathcal{A}_0(G, \omega)$ for the spaces of cusp forms in $\mathcal{A}(G)$ and $\mathcal{A}(G, \omega)$.

Lean: `Langlands.IsCuspForm`, a definition of the project, with the differences of Remark 2.2.5 and Volume 7, Remark 1.2.6

Each proper parabolic subgroup of $GL_2$ over $\mathbb{Q}$ is the stabilizer of a line in $\mathbb{Q}^2$, and $G(\mathbb{Q})$ acts transitively on the lines, so it is $\gamma^{-1}B\gamma$ for some $\gamma \in G(\mathbb{Q})$. By Lemma 2.3.2, the vanishing of $\varphi_U$ implies the vanishing of the constant terms along all unipotent radicals. This is the form of the condition in `Langlands.IsCuspForm`, which asks for the vanishing along the standard maximal parabolic subgroups of $GL_n$. By Lemma 2.3.2 and Proposition 2.2.12, $\mathcal{A}_0(G)$ is a $(\mathfrak{g}, K_\infty) \times G(\mathbb{A}_f)$-submodule of $\mathcal{A}(G)$.

**Proposition 2.3.4 (cusp forms and $\phi_f$).** Let $f \in M_k(\Gamma_0(N))$. Then $\phi_f$ is a cusp form if and only if $f \in S_k(\Gamma_0(N))$.

Lean: not formalized

*Proof.* Write $\varphi = \phi_f$. By Lemma 2.3.2 the constant term $\varphi_U$ is left invariant under $B(\mathbb{Q})$ and right invariant under $K_0(N)$. Since $G(\mathbb{A}) = G(\mathbb{Q})G(\mathbb{R})^+K_0(N)$ and $G(\mathbb{Q}) = B(\mathbb{Q})SL_2(\mathbb{Z})$, the constant term vanishes if and only if $\varphi_U(\sigma g_\infty) = 0$ for all $\sigma \in SL_2(\mathbb{Z})$ and $g_\infty \in G(\mathbb{R})^+$. Since $\mathbb{A} = \mathbb{Q} + \mathbb{R} + N\widehat{\mathbb{Z}}$ and $\mathbb{Q} \cap (\mathbb{R} + N\widehat{\mathbb{Z}}) = N\mathbb{Z}$, the set $[0, N) \times N\widehat{\mathbb{Z}}$ is a fundamental domain for $\mathbb{Q}\backslash\mathbb{A}$, and the measure $dx$ on it is $N^{-1}dx_\infty$ times the Haar measure of mass $1$ on $N\widehat{\mathbb{Z}}$. For $x_f \in N\widehat{\mathbb{Z}}$ the element $\sigma^{-1}u(x_f)\sigma$ of $K_f$ is congruent to $1$ modulo $N$, so it lies in $K_0(N)$. With the left invariance under $\sigma$ this gives
$$\varphi_U(\sigma g_\infty) = \int \varphi(\sigma^{-1}u(x)\sigma g_\infty)\,dx = \frac{1}{N}\int_0^N \varphi\left(\sigma^{-1}u(x_\infty)\sigma g_\infty\right)dx_\infty,$$
where the argument on the right lies in $G(\mathbb{R})^+$. Put $f_\sigma(z) = f(\sigma^{-1}z)\,j(\sigma^{-1}, z)^{-k}$. The cocycle relation $j(\sigma^{-1}h, i) = j(\sigma^{-1}, hi)\,j(h, i)$ gives $F_f(\sigma^{-1}h) = F_{f_\sigma}(h)$ in the notation of Example 2.1.8. Let $h = \sigma g_\infty$ have the Iwasawa coordinates $(x_0, y, z, \theta)$. Then
$$\varphi_U(\sigma g_\infty) = \frac{y^{k/2}e^{ik\theta}}{N}\int_0^N f_\sigma(x + x_0 + iy)\,dx.$$
The function $f_\sigma$ has period $N$, since $\sigma^{-1}u(N)\sigma \in \Gamma(N) \subseteq \Gamma_0(N)$, and the integral is $N$ times the constant coefficient of the $q$-expansion of $f_\sigma$, that is, the value of $f$ at the cusp $\sigma^{-1}\infty$. As $\sigma$ runs over $SL_2(\mathbb{Z})$, the cusp $\sigma^{-1}\infty$ runs over $\mathbb{P}^1(\mathbb{Q})$. So $\varphi_U = 0$ if and only if $f$ vanishes at all cusps. $\square$

**Example 2.3.5 (forms that are not cuspidal).** For the character $\varphi = \chi \circ \det$ of Example 2.2.8, $\varphi(u(x)g) = \varphi(g)$, so $\varphi_U = \varphi \ne 0$. For the Eisenstein series of Example 2.2.9 the constant term is
$$E_U(g, s) = f_s(g) + \frac{\xi(2s - 1)}{\xi(2s)}f_{1-s}(g), \qquad \xi(s) = \pi^{-s/2}\Gamma(s/2)\zeta(s),$$
which restricts on $SL_2(\mathbb{R})$ to the constant term $y^s + \varphi(s)y^{1-s}$ of Volume 4, Example 2.6.4. The first term comes from the identity coset of $B(\mathbb{Q})\backslash G(\mathbb{Q})$, and the second from the big cell $B(\mathbb{Q})wU(\mathbb{Q})$; the computation is in [Bum97], Chapter 3.

### Siegel sets and the volume of the quotient

**Proposition 2.3.6 (Siegel set).** Let $\mathfrak{S}$ be the set of the products $u(x)a(t)zk$ with $u(x)a(t)z \in G(\mathbb{R})$, $|x| \le \frac{1}{2}$, $t \ge \frac{\sqrt{3}}{2}$, $z \in Z(\mathbb{R})^+$, and $k \in K$. Then $G(\mathbb{A}) = G(\mathbb{Q})\mathfrak{S}$.

Lean: not formalized

*Proof.* Chapter 1 proves $G(\mathbb{A}) = G(\mathbb{Q})G(\mathbb{R})^+K_f$, from strong approximation for $SL_2$ and $\mathbb{A}^\times = \mathbb{Q}^\times\mathbb{R}_{>0}\widehat{\mathbb{Z}}^\times$. So let $g = \gamma g_\infty k_f$ with $g_\infty \in G(\mathbb{R})^+$. Write $g_\infty = z h$ with $z \in Z(\mathbb{R})^+$ and $h \in SL_2(\mathbb{R})$. There is $\sigma \in SL_2(\mathbb{Z})$ that maps $h i$ into the standard fundamental domain $\{\tau : |\mathrm{Re}\,\tau| \le \frac{1}{2},\ |\tau| \ge 1\}$ of Volume 4, so $\sigma h i = x + iy$ with $|x| \le \frac{1}{2}$ and $y \ge \frac{\sqrt{3}}{2}$. By Lemma 2.1.2, $\sigma h = u(x)\,\mathrm{diag}(y^{1/2}, y^{-1/2})\,\kappa_\theta = u(x)a(y)\,y^{-1/2}\kappa_\theta$. Since $\sigma$ is rational, its finite component $\sigma_f$ lies in $K_f$, and
$$g = \gamma\sigma^{-1}\cdot\left(u(x)a(y)\,y^{-1/2}z\,\kappa_\theta\right)(\sigma_f k_f)$$
with $\gamma\sigma^{-1} \in G(\mathbb{Q})$ and $\kappa_\theta\sigma_f k_f \in K$. $\square$

**Corollary 2.3.7 (finite volume).** The quotient $Z(\mathbb{A})G(\mathbb{Q})\backslash G(\mathbb{A})$ has finite volume for the Haar measure.

Lean: not formalized

*Proof.* In the coordinates $g = u(x)a(t)zk$ the Haar measure of $G(\mathbb{A})$ is $t^{-2}dx\,dt\,dz\,dk$ up to a constant, since the modulus character of $B(\mathbb{R})$ at $a(t)$ is $t$. The image of $\mathfrak{S}$ in $Z(\mathbb{A})\backslash G(\mathbb{A})$ has volume at most a constant times $\int_{-1/2}^{1/2}\int_{\sqrt{3}/2}^\infty t^{-2}\,dt\,dx < \infty$, and it covers the quotient by Proposition 2.3.6. $\square$

### Fourier expansion and rapid decay

**Definition 2.3.8 (the additive character).** Let $\psi = \prod_v \psi_v$ be the character of $\mathbb{A}$ with $\psi_\infty(x) = e^{2\pi i x}$ and $\psi_p(x) = e^{-2\pi i\{x\}_p}$, where $\{x\}_p$ is the fractional part of Volume 0, Section 3.2. For a continuous function $\varphi$ on $G(\mathbb{Q})\backslash G(\mathbb{A})$ and $\xi \in \mathbb{Q}$ the $\xi$-th *Fourier coefficient* of $\varphi$ is
$$\varphi_\xi(g) = \int_{\mathbb{Q}\backslash\mathbb{A}}\varphi(u(x)g)\,\psi(-\xi x)\,dx.$$

Lean: not formalized

The character $\psi$ is $x \mapsto \psi_0(-x)$, where $\psi_0$ is the standard character of Volume 0, Section 3.2. We take the opposite sign so that $\psi_\infty(x) = e^{2\pi ix}$ and the Fourier expansion of $\phi_f$ is the $q$-expansion of $f$, with $q = e^{2\pi i z}$. The character $\psi$ is trivial on $\mathbb{Q}$, since $\psi_0$ is, and $\psi_p$ is trivial on $\mathbb{Z}_p$ and not on $p^{-1}\mathbb{Z}_p$. The coefficient $\varphi_0$ is the constant term, and $\varphi_\xi(u(y)g) = \psi(\xi y)\varphi_\xi(g)$ for $y \in \mathbb{A}$.

**Lemma 2.3.9 (Fourier expansion along $U$).** Let $\varphi$ be smooth and left invariant under $G(\mathbb{Q})$, and fix $g \in G(\mathbb{A})$. There is an integer $M \ge 1$ with $\varphi_\xi(g) = 0$ unless $\xi \in M^{-1}\mathbb{Z}$, and
$$\varphi(g) = \sum_{\xi \in \mathbb{Q}}\varphi_\xi(g),$$
with absolute convergence. The integer $M$ depends only on the finite component $g_f$ of $g$.

Lean: not formalized

*Proof.* Let $K'$ be an open compact subgroup that fixes $\varphi$ on the right. There is $M$ with $u(y) \in g_fK'g_f^{-1}$ for all $y \in M\widehat{\mathbb{Z}}$, and then $x \mapsto \varphi(u(x)g)$ is invariant under $\mathbb{Q} + M\widehat{\mathbb{Z}}$. As in the proof of Proposition 2.3.4, it is a smooth function on $\mathbb{Q}\backslash\mathbb{A}/M\widehat{\mathbb{Z}} = \mathbb{R}/M\mathbb{Z}$, and its Fourier series converges absolutely. For $\xi = n/M$ the character $x \mapsto \psi(\xi x)$ is trivial on $M\widehat{\mathbb{Z}}$ and restricts to $e^{2\pi i n x_\infty/M}$ on $\mathbb{R}$, and for $\xi \notin M^{-1}\mathbb{Z}$ it is nontrivial on $M\widehat{\mathbb{Z}}$, so $\varphi_\xi(g) = 0$. The Fourier series at $x = 0$ is the claimed sum. $\square$

**Theorem 2.3.10 (rapid decay of cusp forms).** Let $\varphi \in \mathcal{A}_0(G, \omega)$ with $\omega$ unitary. For each $A > 0$ there is a constant $C$ with
$$|\varphi(u(x)a(t)zk)| \le C t^{-A} \qquad \text{for all } u(x)a(t)zk \in \mathfrak{S}.$$

Lean: not formalized

*Proof.* The translates $\rho(k)\varphi$, $k \in K$, lie in a finite-dimensional space with a basis $\varphi_1, \dots, \varphi_r$ of cusp forms, and $\rho(k)\varphi = \sum_i c_i(k)\varphi_i$ with bounded functions $c_i$. Since $|\omega(z)| = 1$, it suffices to bound $|\varphi_i(h)|$ for $h = u(x)a(t) \in G(\mathbb{R})$ with $|x| \le \frac{1}{2}$ and $t \ge \frac{\sqrt{3}}{2}$. Fix one $\varphi_i$, write $\varphi$ for it, and let $M$ be as in Lemma 2.3.9 for $g_f = 1$. Let $E = \left(\begin{smallmatrix} 0 & 1 \\ 0 & 0 \end{smallmatrix}\right) \in \mathfrak{g}$. Since $h\exp(sE) = u(x + ts)a(t) = u(ts)h$, the Fourier coefficients satisfy
$$(E\varphi)_\xi(h) = \frac{d}{ds}\Big|_{s=0}\varphi_\xi(u(ts)h) = 2\pi i\xi t\,\varphi_\xi(h), \quad\text{so}\quad (E^m\varphi)_\xi(h) = (2\pi i\xi t)^m\varphi_\xi(h).$$
By Corollary 2.2.11 there is $r$, independent of $m$, with $|E^m\varphi(g)| \le C_m\|g\|^r$. For $y$ in the fundamental domain $[0, M) \times M\widehat{\mathbb{Z}}$ the height of $u(y)h$ is at most a constant times $t$ by Lemma 2.2.2. So $|(E^m\varphi)_\xi(h)| \le C'_m t^r$, and
$$|\varphi_\xi(h)| \le C'_m t^{r - m}(2\pi|\xi|)^{-m}.$$
Since $\varphi_0 = \varphi_U = 0$, Lemma 2.3.9 gives, for $m \ge 2$,
$$|\varphi(h)| \le C'_m t^{r - m}\sum_{\xi \in M^{-1}\mathbb{Z},\ \xi \ne 0}(2\pi|\xi|)^{-m} = C''_m t^{r - m}.$$
Take $m \ge r + A$. $\square$

**Corollary 2.3.11 (cusp forms are bounded and square integrable).** Let $\varphi \in \mathcal{A}_0(G, \omega)$ with $\omega$ unitary. Then $\varphi$ is bounded on $G(\mathbb{A})$, and $|\varphi|$ is square integrable on $Z(\mathbb{A})G(\mathbb{Q})\backslash G(\mathbb{A})$.

Lean: not formalized

*Proof.* The function $|\varphi|$ is left invariant under $G(\mathbb{Q})$, so by Proposition 2.3.6 its supremum over $G(\mathbb{A})$ is its supremum over $\mathfrak{S}$, which is finite by Theorem 2.3.10. A bounded function on a space of finite volume (Corollary 2.3.7) is square integrable. $\square$

**Example 2.3.12 (the classical bound).** For $f \in S_k(\Gamma_0(N))$ and $g_\infty \in G(\mathbb{R})^+$ with $g_\infty i = x + iy$, (2.2.1) gives $|\phi_f(g_\infty)| = y^{k/2}|f(x + iy)|$. Corollary 2.3.11 says that $y^{k/2}|f(x + iy)|$ is bounded on $\mathbb{H}$, which is Volume 4, Lemma 1.4.3. Theorem 2.3.10 for $k \in K_f$ gives the exponential decay of $f$ at each cusp, from the decay at $\infty$ of the forms $f_\sigma$ of the proof of Proposition 2.3.4. For a modular form that is not cuspidal, $y^{k/2}|f(x + iy)|$ grows like $y^{k/2}|a_0|$, and $\phi_f$ has moderate growth but is not bounded.

### The discreteness of the cuspidal spectrum

Let $\omega$ be a unitary character of $\mathbb{Q}^\times\backslash\mathbb{A}^\times$. Let $L^2(\omega)$ be the space of measurable functions $\varphi$ on $G(\mathbb{A})$ with $\varphi(\gamma zg) = \omega(z)\varphi(g)$ for $\gamma \in G(\mathbb{Q})$ and $z \in Z(\mathbb{A})$, and with $\int|\varphi|^2 < \infty$ over $Z(\mathbb{A})G(\mathbb{Q})\backslash G(\mathbb{A})$. The group $G(\mathbb{A})$ acts on it unitarily by right translation $\rho$.

**Definition 2.3.13 (the cuspidal subspace).** The *cuspidal subspace* $L^2_0(\omega)$ is the closed subspace of the $\varphi \in L^2(\omega)$ with $\varphi_U(g) = 0$ for almost all $g$.

Lean: not formalized

The constant term of an $L^2$ function is defined almost everywhere by Fubini's theorem, since $\mathbb{Q}\backslash\mathbb{A}$ is compact. The subspace is stable under $\rho$ by Lemma 2.3.2, and it contains $\mathcal{A}_0(G, \omega)$ by Corollary 2.3.11. For $\beta$ a smooth function with compact support on $G(\mathbb{A})$, that is, a product of a smooth function with compact support on $G(\mathbb{R})$ and a locally constant function with compact support on $G(\mathbb{A}_f)$, put $\rho(\beta)\varphi(g) = \int_{G(\mathbb{A})}\varphi(gh)\beta(h)\,dh$.

**Theorem 2.3.14 (discreteness of the cuspidal spectrum, Gelfand, Graev and Piatetski-Shapiro).** For each smooth function $\beta$ with compact support on $G(\mathbb{A})$, the operator $\rho(\beta)$ on $L^2_0(\omega)$ is compact. The representation $\rho$ on $L^2_0(\omega)$ is a Hilbert direct sum of irreducible unitary representations of $G(\mathbb{A})$, and each one occurs with finite multiplicity.

Lean: not formalized

*Outline of the proof.* The theorem is Volume 7, Theorem 1.3.2, for $n = 2$. The proof is in Gelfand, Graev and Piatetski-Shapiro, *Representation Theory and Automorphic Functions* (Saunders 1969), Chapter 1, and in [Bum97], Chapter 3, and we give its steps.

1. The operator $\rho(\beta)$ is an integral operator on $L^2(\omega)$, with the kernel $K_\beta(g, h) = \sum_{\gamma \in Z(\mathbb{Q})\backslash G(\mathbb{Q})}\beta_\omega(g^{-1}\gamma h)$, where $\beta_\omega(g) = \int_{Z(\mathbb{A})}\beta(zg)\omega(z)\,dz$. This follows by unfolding the integral over $G(\mathbb{A})$ into an integral over the quotient.
2. For $\varphi \in L^2_0(\omega)$ we have $\int K_\beta(u(x)g, h)\varphi(h)\,dh$ integrated over $x \in \mathbb{Q}\backslash\mathbb{A}$ equal to $(\rho(\beta)\varphi)_U(g) = 0$. So on $L^2_0(\omega)$ one may replace $K_\beta(g, h)$ by $K_\beta(g, h) - \int_{\mathbb{Q}\backslash\mathbb{A}}K_\beta(u(x)g, h)\,dx$.
3. The modified kernel is the sum of the nonzero Fourier coefficients of $x \mapsto K_\beta(u(x)g, h)$. By Poisson summation over $U(\mathbb{Q})\backslash U(\mathbb{A})$ and the argument of Theorem 2.3.10, applied to the smooth function $\beta$, these are bounded by $C_A t(g)^{-A}$ for $g \in \mathfrak{S}$ with $t(g)$ large, uniformly in $h$. It follows that $|\rho(\beta)\varphi(g)| \le C_A t(g)^{-A}\|\varphi\|_2$ on $\mathfrak{S}$, and the same bound holds for the derivatives $X\rho(\beta)\varphi = \rho(X\beta)\varphi$.
4. So $\rho(\beta)$ maps the unit ball of $L^2_0(\omega)$ to a set of functions that are uniformly bounded, equicontinuous and uniformly small where $t(g)$ is large. By the theorem of Arzela and Ascoli this set is relatively compact in $L^2(\omega)$, and $\rho(\beta)$ is compact.
5. Let $\beta_n$ be a sequence of functions with $\beta_n(g^{-1}) = \overline{\beta_n(g)}$ that converge to the delta function at $1$. Then $\rho(\beta_n)$ is compact and self-adjoint, and $\rho(\beta_n)\varphi \to \varphi$ for each $\varphi$. The spectral theorem for compact self-adjoint operators decomposes $L^2_0(\omega)$ into finite-dimensional eigenspaces, and a standard argument (Volume 7, Theorem 1.3.2) gives the decomposition into irreducible representations with finite multiplicities. $\square$

The space $L^2(\omega)$ itself does not decompose discretely: the Eisenstein series $E(g, \frac{1}{2} + it)$ give, through their integrals over $t$, a continuous part of the spectrum. The constant term is exactly what separates the two parts.

**Corollary 2.3.15 (finiteness for cusp forms).** Let $K'$, $\tau$ and $J$ be as in Proposition 2.2.13. The space of the $\varphi \in \mathcal{A}_0(G, \omega)$ that are right invariant under $K'$, killed by $J$ and of $K_\infty$-types in $\tau$ is finite-dimensional.

Lean: not formalized

*Proof.* Let $V$ be this space. By Theorem 2.2.10 there is a smooth function $\alpha$ with compact support on $G(\mathbb{R})$, depending only on $\tau$ and $J$, with $\varphi * \alpha = \varphi$ for all $\varphi \in V$. Let $\beta(h) = \alpha(h_\infty^{-1})\mathbf{1}_{K'}(h_f)/\mathrm{vol}(K')$. Then $\rho(\beta)\varphi = \varphi$ for $\varphi \in V$. By Corollary 2.3.11, $V \subseteq L^2_0(\omega)$, so $V$ lies in the eigenspace of eigenvalue $1$ of the compact operator $\rho(\beta)$, which is finite-dimensional by Theorem 2.3.14. $\square$

For $K' = K_0(N)$, the weights $\pm k$ and $J = (Z, \Delta - \frac{k}{2}(1 - \frac{k}{2}))$, this gives $\dim S_k(\Gamma_0(N)) < \infty$, Volume 4, Proposition 1.3.10, without the valence formula. For the weight $0$ it gives the finite multiplicity of each Laplace eigenvalue on Maass cusp forms of level $N$.

### Cuspidal automorphic representations

**Definition 2.3.16 (cuspidal automorphic representation).** A *cuspidal automorphic representation* of $G(\mathbb{A})$ with central character $\omega$ is an irreducible $(\mathfrak{g}, K_\infty) \times G(\mathbb{A}_f)$-module that is isomorphic to a submodule of $\mathcal{A}_0(G, \omega)$.

Lean: not formalized

**Proposition 2.3.17 (decomposition of the space of cusp forms).** Let $\omega$ be unitary. The module $\mathcal{A}_0(G, \omega)$ is the direct sum of its irreducible submodules. Each of them is admissible. The isotypic component of a cuspidal automorphic representation $\pi$ is the space of $K$-finite smooth vectors of the $\pi$-isotypic part of $L^2_0(\omega)$, and it has finite length.

Lean: not formalized

*Outline of the proof.* Let $\varphi \in \mathcal{A}_0(G, \omega)$, and let $V$ be the finite-dimensional space of Corollary 2.3.15 that contains it, for suitable $K'$, $\tau$ and $J$. Decompose $L^2_0(\omega) = \widehat{\bigoplus}\,m(\Pi)\Pi$ by Theorem 2.3.14. The orthogonal projection to the $\Pi$-isotypic part commutes with $\rho(K')$, with $\rho(K_\infty)$ and, on smooth vectors, with $Z(\mathfrak{g})$, so it maps $V$ to $V$. Since $V$ is finite-dimensional, only finitely many $\Pi$ have a nonzero projection of $\varphi$, and $\varphi$ is the sum of its projections. The $K$-finite smooth vectors of an irreducible unitary representation $\Pi$ form an irreducible admissible $(\mathfrak{g}, K_\infty) \times G(\mathbb{A}_f)$-module (Harish-Chandra for the real place), and these give the irreducible submodules of $\mathcal{A}_0(G, \omega)$. The details are in [Bum97], Chapter 3, and [GH24]. $\square$

**Remark 2.3.18 (other central characters).** Each character of $\mathbb{Q}^\times\backslash\mathbb{A}^\times$ is $\omega_0|\cdot|_\mathbb{A}^\sigma$ with $\omega_0$ unitary and $\sigma \in \mathbb{C}$. Multiplication by $|\det g|_\mathbb{A}^{-\sigma/2}$ is an isomorphism $\mathcal{A}_0(G, \omega) \to \mathcal{A}_0(G, \omega_0)$, since $\det z = z^2$ for a scalar matrix $z$, and the new central character is unitary. So the results of this section extend to all central characters. The adelic quotient of the Lean project is the type `Langlands.AdeleQuotient`, and none of the analytic statements of this section is formalized.
