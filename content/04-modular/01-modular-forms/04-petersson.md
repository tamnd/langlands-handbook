---
title: The Petersson inner product
nodes: []
sources: []
status: drafted
drafted_by: writer
reviewed_by: []
---
## The Petersson inner product

Petersson defined in 1939 an inner product on each space of cusp forms. The Hecke operators of Section 1.5 are normal for it, and this is the reason that the spaces of cusp forms have bases of eigenforms. This section defines the inner product, proves that it converges, and computes the adjoint of the slash operator of a single matrix. As an application it proves that the Eisenstein series are orthogonal to the cusp forms.

**Lemma 1.4.1 (invariance).** Let $d\mu = dx\,dy/y^2$ on $\mathbb{H}$, with $\tau = x + iy$. Then $d\mu$ is invariant under $GL_2^+(\mathbb{R})$. Let $f$ and $g$ be functions on $\mathbb{H}$, let $k \in \mathbb{Z}$, and let $\alpha \in GL_2^+(\mathbb{R})$. Then
$$(f|_k\alpha)(\tau)\, \overline{(g|_k\alpha)(\tau)}\, (\mathrm{Im}\,\tau)^k = \det(\alpha)^{k-2}\, f(\alpha\tau)\, \overline{g(\alpha\tau)}\, (\mathrm{Im}\,\alpha\tau)^k.$$
In particular, if $f, g \in M_k(\Gamma)$, then the function $f(\tau)\overline{g(\tau)}(\mathrm{Im}\,\tau)^k$ is invariant under $\Gamma$.

Lean: not stated yet

*Proof.* The scalar matrices act trivially on $\mathbb{H}$, so for the first claim we may assume $\det \alpha = 1$. The map $\tau \mapsto \alpha\tau$ is holomorphic with derivative $j(\alpha, \tau)^{-2}$, so its real Jacobian is $|j(\alpha,\tau)|^{-4}$. By Lemma 1.1.2, $\mathrm{Im}\,\alpha\tau = \mathrm{Im}\,\tau / |j(\alpha,\tau)|^2$. So $(\mathrm{Im}\,\alpha\tau)^{-2}$ times the Jacobian is $(\mathrm{Im}\,\tau)^{-2}$, which is the invariance of $d\mu$. For the identity, the left side is $\det(\alpha)^{2k-2} |j(\alpha,\tau)|^{-2k} f(\alpha\tau)\overline{g(\alpha\tau)} (\mathrm{Im}\,\tau)^k$. By Lemma 1.1.2 for a general $\alpha$, $(\mathrm{Im}\,\tau)^k |j(\alpha,\tau)|^{-2k} = \det(\alpha)^{-k} (\mathrm{Im}\,\alpha\tau)^k$. $\square$

Let $\Gamma$ be a congruence subgroup and $\bar\Gamma$ its image in $PSL_2(\mathbb{Z}) = SL_2(\mathbb{Z})/\{\pm I\}$. A *fundamental domain* for $\Gamma$ is a measurable set $D \subset \mathbb{H}$ such that the sets $\gamma D$, for $\gamma \in \bar\Gamma$, cover $\mathbb{H}$, and two different ones meet in a set of measure zero. If $D$ and $D'$ are fundamental domains and $\phi \ge 0$ is a measurable function invariant under $\Gamma$, then
$$\int_D \phi \, d\mu = \sum_{\gamma \in \bar\Gamma} \int_{D \cap \gamma D'} \phi \, d\mu = \sum_{\gamma \in \bar\Gamma} \int_{\gamma^{-1} D \cap D'} \phi\, d\mu = \int_{D'} \phi\, d\mu,$$
and the same holds for integrable $\phi$ of any sign. By Theorem 1.1.4 and Lemma 1.4.1, the set $\mathcal{D}$ is a fundamental domain for $SL_2(\mathbb{Z})$: its boundary has measure zero. If $PSL_2(\mathbb{Z}) = \bigsqcup_{i=1}^{d} \bar\Gamma \gamma_i$, then $D_\Gamma = \bigcup_i \gamma_i \mathcal{D}$ is a fundamental domain for $\Gamma$. Its volume is
$$V_\Gamma = \int_{D_\Gamma} d\mu = d \int_{\mathcal{D}} d\mu = d \int_{-1/2}^{1/2} \int_{\sqrt{1 - x^2}}^\infty \frac{dy}{y^2}\, dx = d \int_{-1/2}^{1/2} \frac{dx}{\sqrt{1 - x^2}} = \frac{d\pi}{3}.$$

**Definition 1.4.2 (the Petersson inner product).** Let $\Gamma$ be a congruence subgroup and $k \in \mathbb{Z}$. For $f, g \in M_k(\Gamma)$ such that at least one of them is a cusp form, the *Petersson inner product* is
$$\langle f, g \rangle = \frac{1}{V_\Gamma} \int_{D} f(\tau) \overline{g(\tau)} (\mathrm{Im}\,\tau)^k \, d\mu(\tau),$$
where $D$ is a fundamental domain for $\Gamma$.

**Lemma 1.4.3 (cusp forms are bounded).** Let $f \in S_k(\Gamma)$. Then the function $(\mathrm{Im}\,\tau)^{k/2} |f(\tau)|$ is bounded on $\mathbb{H}$.

Lean: not stated yet

*Proof.* Let $\phi_f(\tau) = (\mathrm{Im}\,\tau)^{k/2} |f(\tau)|$. By Lemma 1.4.1 with $g = f$, $\phi_f$ is invariant under $\Gamma$, and $\phi_f(\gamma\tau) = \phi_{f|\gamma}(\tau)$ for $\gamma \in SL_2(\mathbb{Z})$. So it suffices to bound each $\phi_{f|\gamma_i}$ on $\mathcal{D}$. Let $h$ be such that $f|\gamma_i$ is invariant under $T^h$. Its expansion $\sum_{n \ge 1} b_n q_h^n$ has no constant term, so $|(f|\gamma_i)(\tau)| \le C e^{-2\pi y/h}$ for $y \ge \sqrt{3}/2$, by Lemma 1.2.4. The function $y^{k/2} e^{-2\pi y/h}$ is bounded on $y \ge \sqrt{3}/2$. $\square$

**Proposition 1.4.4 (properties of the inner product).** Let $f, g \in M_k(\Gamma)$, and let at least one of them be a cusp form.
1. The integral of Definition 1.4.2 converges absolutely, and it does not depend on the fundamental domain.
2. If $\Gamma' \subset \Gamma$ is a congruence subgroup, the products for $\Gamma'$ and for $\Gamma$ are equal.
3. On $S_k(\Gamma)$ the product is linear in $f$, conjugate linear in $g$, Hermitian and positive definite.

Lean: not stated yet

*Proof.* Let $f$ be the cusp form. Use the domain $D_\Gamma$. The integral over $\gamma_i \mathcal{D}$ is the integral over $\mathcal{D}$ of $(f|\gamma_i)\overline{(g|\gamma_i)} y^k$, by Lemma 1.4.1. On $\mathcal{D}$ with $y \ge 1$, we have $|f|\gamma_i| \le Ce^{-2\pi y/h}$ and $|g|\gamma_i| \le C$. So the integrand is $O(y^{k-2} e^{-2\pi y/h})$, which is integrable on $\{|x| \le 1/2, y \ge 1\}$. The rest of $\mathcal{D}$ is compact. This proves the convergence, and the independence of the domain is the computation before Definition 1.4.2. For part 2, if $\bar\Gamma = \bigsqcup_j \bar\Gamma' \delta_j$, then $\bigcup_j \delta_j D_{\Gamma}$ is a fundamental domain for $\Gamma'$. The integral over it is $[\bar\Gamma : \bar\Gamma']$ times the integral over $D_\Gamma$, and the same holds for the volumes. For part 3, the product is Hermitian because $\overline{f \bar g} = g \bar f$. Also $\langle f, f \rangle = V_\Gamma^{-1}\int_D |f|^2 y^k\, d\mu \ge 0$, with equality only if $f = 0$ on the interior of $D$, and then $f = 0$ on $\mathbb{H}$. $\square$

Part 2 is the reason for the normalization by $V_\Gamma$. With it, the inner product of two forms does not depend on the group used to compute it, and we do not write the group.

**Proposition 1.4.5 (the adjoint of a matrix).** Let $\alpha \in GL_2^+(\mathbb{Q})$ and $\alpha' = \det(\alpha)\alpha^{-1}$. Let $f, g \in M_k(\Gamma)$, and let at least one of them be a cusp form. Then
$$\langle f|_k \alpha, g \rangle = \langle f, g|_k \alpha' \rangle.$$
Also $[\bar\Gamma : \overline{\Gamma \cap \alpha^{-1}\Gamma\alpha}] = [\bar\Gamma : \overline{\Gamma \cap \alpha\Gamma\alpha^{-1}}]$.

Lean: not stated yet

*Proof.* By Lemma 1.2.7, $f|\alpha$ and $g$ are modular for $\Gamma_1 = \Gamma \cap \alpha^{-1}\Gamma\alpha$, and $f$ and $g|\alpha'$ are modular for $\Gamma_2 = \Gamma \cap \alpha\Gamma\alpha^{-1} = \alpha\Gamma_1\alpha^{-1}$. Here we use that $\alpha'$ and $\alpha^{-1}$ differ by a scalar, so $g|\alpha' = \det(\alpha)^{k-2} g|\alpha^{-1}$ by Lemma 1.2.2. Let $D_1$ be a fundamental domain for $\Gamma_1$. Then $\alpha D_1$ is a fundamental domain for $\Gamma_2$, and it has the same volume, because $d\mu$ is invariant. So $V_{\Gamma_1} = V_{\Gamma_2}$, which is the claim about the indices. By Lemma 1.4.1, applied to $f$ and $g|\alpha^{-1}$,
$$(f|\alpha)(\tau)\overline{g(\tau)}(\mathrm{Im}\,\tau)^k = \det(\alpha)^{k-2} f(\alpha\tau) \overline{(g|\alpha^{-1})(\alpha\tau)} (\mathrm{Im}\,\alpha\tau)^k = f(\alpha\tau) \overline{(g|\alpha')(\alpha\tau)} (\mathrm{Im}\,\alpha\tau)^k.$$
We integrate over $D_1$ and substitute $\tau' = \alpha\tau$. The left side gives $V_{\Gamma_1}\langle f|\alpha, g\rangle$, and the right side gives $V_{\Gamma_2}\langle f, g|\alpha'\rangle$. $\square$

The Eisenstein series of level one can be written as a sum over a quotient. A pair $(c, d)$ of coprime integers is the bottom row of a matrix $\gamma \in SL_2(\mathbb{Z})$, and two matrices have the same bottom row if and only if they differ by a power of $T$ on the left. Since $G_k = \sum_{n \ge 1} n^{-k} \sum_{\gcd(c,d) = 1} (c\tau + d)^{-k}$, we get
$$E_k(\tau) = \frac{1}{2}\sum_{\gcd(c, d) = 1} (c\tau + d)^{-k} = \sum_{\gamma \in \bar\Gamma_\infty \backslash PSL_2(\mathbb{Z})} j(\gamma, \tau)^{-k},$$
where $\bar\Gamma_\infty$ is the image of $\{\pm T^n\}$. The term of $\gamma$ is well defined because $k$ is even.

**Proposition 1.4.6 (Eisenstein series are orthogonal to cusp forms).** Let $k \ge 4$ be even and $f \in S_k(SL_2(\mathbb{Z}))$. Then $\langle f, E_k \rangle = 0$.

Lean: not stated yet

*Proof.* For $\gamma \in SL_2(\mathbb{Z})$ we have $f(\tau)\overline{j(\gamma,\tau)}^{-k} y^k = f(\gamma\tau) j(\gamma,\tau)^{-k}\, \overline{j(\gamma,\tau)}^{-k} y^k = f(\gamma\tau)(\mathrm{Im}\,\gamma\tau)^k$. So
$$\frac{\pi}{3}\langle f, E_k \rangle = \int_{\mathcal{D}} \sum_{\gamma \in \bar\Gamma_\infty\backslash PSL_2(\mathbb{Z})} f(\gamma\tau) (\mathrm{Im}\,\gamma\tau)^k\, d\mu = \int_{0}^\infty \int_0^1 f(x + iy)\, y^{k-2} \, dx\, dy.$$
The second equality holds because the sets $\gamma\mathcal{D}$, for $\gamma$ in a set of representatives of $\bar\Gamma_\infty \backslash PSL_2(\mathbb{Z})$, form a fundamental domain for $\bar\Gamma_\infty$, and the strip $\{0 \le x \le 1\}$ is another one. To justify the exchange of sum and integral we check that the last integral converges absolutely. By Lemma 1.4.3, $|f(x+iy)| y^{k-2} \le C y^{k/2 - 2}$, which is integrable near $y = 0$ because $k/2 - 2 > -1$. For $y \ge 1$, $|f| \le C e^{-2\pi y}$. Now $\int_0^1 f(x + iy)\, dx = a_0(f) = 0$ for each $y$. $\square$

So $M_k = \mathbb{C} E_k \oplus S_k$ in Theorem 1.3.4 is an orthogonal decomposition, in the sense that $E_k$ is orthogonal to $S_k$ for the pairing of Definition 1.4.2. The pairing is not defined on $E_k$ with itself, because $|E_k|^2 y^k$ is not integrable on $\mathcal{D}$.

**Remark 1.4.7 (the Petersson product in Mathlib).** Mathlib defines the integrand and not the integral. The function `UpperHalfPlane.petersson k f f' τ` is $\overline{f(\tau)}\, f'(\tau)\, (\mathrm{Im}\,\tau)^k$. It is conjugate linear in the first variable, so it is the integrand of $\langle f', f \rangle$ in our notation. The lemma `UpperHalfPlane.petersson_slash` is Lemma 1.4.1, with the factor $|\det g|^{k-2}$, and `UpperHalfPlane.petersson_slash_SL` is the case of $SL_2(\mathbb{Z})$. The Lean project does not use the inner product. Its statements about eigenforms are conditions on $q$-expansions, see Section 2.1.
