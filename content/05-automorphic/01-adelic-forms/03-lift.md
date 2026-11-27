---
title: From modular forms to adelic functions
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## From modular forms to adelic functions

In this section we fix an integer $N \ge 1$, a Dirichlet character $\chi$ modulo $N$ and an integer $k$, and we let $f \in M_k(N, \chi)$ in the sense of Volume 4, Definition 1.5.2. So $f$ is a modular form of weight $k$ for $\Gamma_1(N)$ with $f|_k\gamma = \chi(d) f$ for each $\gamma = \begin{pmatrix} a & b \\ c & d \end{pmatrix} \in \Gamma_0(N)$. The matrix $-I$ is in $\Gamma_0(N)$, and $f|_k(-I) = (-1)^k f$ by Volume 4, Lemma 1.2.2. So $M_k(N, \chi) = 0$ unless $\chi(-1) = (-1)^k$, and we assume this condition. We attach to $f$ a function $\phi_f$ on $GL_2(\mathbb{A})$ and prove its transformation laws. The construction follows [Bum97], Section 3.6, and [Gel75], Chapter 3.

### The characters attached to the nebentypus

The character $\chi$ appears in two places on the adelic side: as a character of the compact group $K_0(N)$, and as the central character. The second one is a Hecke character in the sense of Volume 3, Chapter 5.

**Definition 1.3.1 (the Hecke character of $\chi$).** Let $\omega = \omega_\chi : \mathbb{Q}^\times \backslash \mathbb{A}^\times \to \mathbb{C}^\times$ be the character with $\omega(q r u) = \chi(u \bmod N)^{-1}$ for $q \in \mathbb{Q}^\times$, $r \in \mathbb{R}_{>0}$ and $u \in \hat{\mathbb{Z}}^\times$. Write $\omega = \prod_v \omega_v$ with $\omega_v = \omega \circ \iota_v$ on $\mathbb{Q}_v^\times$.

The definition makes sense because the factorization $z = qru$ of Section 1.1 is unique. The map $u \mapsto u \bmod N$ is a continuous homomorphism from $\hat{\mathbb{Z}}^\times$ to $(\mathbb{Z}/N\mathbb{Z})^\times$, so $\omega$ is a continuous character, trivial on $\mathbb{Q}^\times$. For a primitive character this is the Hecke character of Volume 3, Example 5.5.6, where the Dirichlet character is called $\eta$ and the Hecke character $\chi$. We keep the letter $\chi$ for the Dirichlet character, as in Volume 4.

**Lemma 1.3.2 (the components of $\omega$).**
1. For $t \in \mathbb{R}^\times$, $\omega_\infty(t) = \mathrm{sgn}(t)^k$.
2. Let $p \nmid N$. Then $\omega_p$ is trivial on $\mathbb{Z}_p^\times$, and $\omega_p(p) = \chi(p)$.
3. For $u \in \hat{\mathbb{Z}}^\times$, $\prod_{p} \omega_p(u_p) = \prod_{p \mid N} \omega_p(u_p) = \chi(u \bmod N)^{-1}$.

Lean: not formalized

*Proof.* The character $\omega$ is trivial on $\mathbb{R}_{>0}$ by definition. The rational number $-1$ is the idele with all components $-1$, and $\omega(-1) = 1$. So $\omega_\infty(-1) = \prod_p \omega_p(-1)^{-1} = \omega(u)^{-1}$ with $u = -1 \in \hat{\mathbb{Z}}^\times$, that is, $\omega_\infty(-1) = \chi(-1) = (-1)^k$. This is part 1. For part 3, $u = \prod_p \iota_p(u_p)$, and the product is finite in the sense that $\omega_p(u_p) = 1$ for $p \nmid N$: the element $\iota_p(u_p)$ for $p \nmid N$ is a unit of $\hat{\mathbb{Z}}$ that is 1 at each prime dividing $N$, so it is 1 modulo $N$. This also proves the first claim of part 2. For the second claim, the idele $\iota_p(p)$ is the product of the rational number $p$ and the idele $u'$ with components $p^{-1}$ at $\infty$ and at each prime $q \ne p$, and 1 at $p$. Write $u' = r u$ with $r = p^{-1}$ at $\infty$ and $u \in \hat{\mathbb{Z}}^\times$. Then $u \equiv p^{-1} \bmod N$, so $\omega_p(p) = \omega(u) = \chi(p^{-1})^{-1} = \chi(p)$. $\square$

**Definition 1.3.3 (the character of $K_0(N)$).** For $k \in K_0(N)$ with lower right entry $d_k$ let $\lambda(k) = \lambda_\chi(k) = \chi(d_k \bmod N)^{-1}$.

By part 3 of Lemma 1.1.4, $\lambda$ is a character of $K_0(N)$, trivial on $K_1(N)$. For a scalar matrix $u \in \hat{\mathbb{Z}}^\times$ we have $\lambda(u) = \omega(u)$. For $\gamma \in \Gamma_0(N)$ with finite part $\gamma_f \in K_0(N)$ we have $\lambda(\gamma_f) = \chi(d)^{-1}$, where $d$ is the lower right entry of $\gamma$. The inverse is forced by the left invariance, as the proof of Proposition 1.3.5 shows. Exercise 6 gives a second explanation, with the diamond operators.

### The lift

**Definition 1.3.4 (the unitary slash operator).** For $g \in GL_2^+(\mathbb{R})$ and a function $h$ on $\mathbb{H}$ let
$$(h \|_k g)(\tau) = \det(g)^{k/2} j(g, \tau)^{-k} h(g\tau) = \det(g)^{1 - k/2} (h|_k g)(\tau).$$

Here $\det(g)^{k/2}$ is the positive root. By the cocycle relation, $(h\|_k g)\|_k g' = h \|_k (gg')$, as in Volume 4, Lemma 1.2.2. The difference with the slash operator of Volume 4 is the factor $\det(g)^{1-k/2}$. With $\|_k$ the positive scalar matrices act trivially, since $\det(rI)^{k/2} j(rI, \tau)^{-k} = r^k r^{-k} = 1$. On $SL_2(\mathbb{R})$ the two operators agree.

**Proposition 1.3.5 (the lift).** There is a unique function $\phi_f : GL_2(\mathbb{A}) \to \mathbb{C}$ with
$$\phi_f(\gamma \, \iota_\infty(g_\infty) \, k) = \lambda(k) \, (f \|_k g_\infty)(i)$$
for all $\gamma \in GL_2(\mathbb{Q})$, $g_\infty \in GL_2^+(\mathbb{R})$ and $k \in K_0(N)$.

Lean: not formalized

*Proof.* By Theorem 1.2.5 each element of $GL_2(\mathbb{A})$ has the form $\gamma \, \iota_\infty(g_\infty) \, k$, so there is at most one such function. We show that the right side depends only on the product. Let $\gamma \, \iota_\infty(g_\infty) \, k = \gamma' \, \iota_\infty(g'_\infty) \, k'$, and let $\delta = \gamma'^{-1}\gamma \in GL_2(\mathbb{Q})$. Then $\delta \, \iota_\infty(g_\infty) \, k = \iota_\infty(g'_\infty) \, k'$. At the infinite place this says $\delta g_\infty = g'_\infty$, and at the finite places it says $\delta_f k = k'$. So $\delta \in GL_2(\mathbb{Q}) \cap GL_2^+(\mathbb{R}) K_0(N)$, and $\delta \in \Gamma_0(N)$ by Lemma 1.2.6. Let $d$ be the lower right entry of $\delta$. Since $\det \delta = 1$, $f \|_k \delta = f|_k\delta = \chi(d) f$. Hence
$$\lambda(k') (f \|_k g'_\infty)(i) = \lambda(\delta_f) \lambda(k) \, ((f \|_k \delta) \|_k g_\infty)(i) = \chi(d)^{-1} \lambda(k) \, \chi(d) \, (f \|_k g_\infty)(i) = \lambda(k) (f\|_k g_\infty)(i). \qquad \square$$

**Proposition 1.3.6 (the transformation laws).** The function $\phi = \phi_f$ has these properties.
1. $\phi(\gamma g) = \phi(g)$ for $\gamma \in GL_2(\mathbb{Q})$ and $g \in GL_2(\mathbb{A})$.
2. $\phi(gk) = \lambda(k) \phi(g)$ for $k \in K_0(N)$. In particular $\phi$ is right invariant under $K_1(N)$.
3. $\phi(g \, \iota_\infty(\kappa_\theta)) = e^{ik\theta} \phi(g)$ for $\theta \in \mathbb{R}$.
4. $\phi(zg) = \omega(z) \phi(g)$ for $z \in \mathbb{A}^\times = Z(\mathbb{A})$.
5. For each $g \in GL_2(\mathbb{A})$ the function $h \mapsto \phi(g\,\iota_\infty(h))$ on $GL_2^+(\mathbb{R})$ is smooth.

Lean: not formalized

*Proof.* Write $g = \gamma \, \iota_\infty(g_\infty) \, k$ as in Proposition 1.3.5. Part 1 holds by construction. For part 2, $gk' = \gamma \, \iota_\infty(g_\infty) \, (kk')$ and $\lambda(kk') = \lambda(k)\lambda(k')$. For part 3, $\iota_\infty(\kappa_\theta)$ commutes with $k$, so $\phi(g \, \iota_\infty(\kappa_\theta)) = \lambda(k) (f \|_k g_\infty \kappa_\theta)(i)$. Since $\kappa_\theta i = i$ and $j(\kappa_\theta, i) = e^{-i\theta}$,
$$(f \|_k g_\infty \kappa_\theta)(i) = ((f\|_k g_\infty)\|_k \kappa_\theta)(i) = e^{ik\theta} (f\|_k g_\infty)(i).$$
For part 4 write $z = qru$ as in Definition 1.3.1. The rational scalar $q$ is in $GL_2(\mathbb{Q})$ and central, so it does not change $\phi$ by part 1. Then $r u g = \gamma \, \iota_\infty(r g_\infty) \, (uk)$, and $f\|_k (rg_\infty) = f \|_k g_\infty$. So $\phi(zg) = \lambda(u) \phi(g)$, and $\lambda(u) = \omega(u) = \omega(z)$. For part 5, $g\,\iota_\infty(h) = \gamma \, \iota_\infty(g_\infty h) \, k$, and $h \mapsto \det(g_\infty h)^{k/2} j(g_\infty h, i)^{-k} f(g_\infty h i)$ is smooth, because $f$ is holomorphic and $j(g_\infty h, i) \ne 0$. $\square$

**Proposition 1.3.7 (the lift in coordinates).** Let $f \in M_k(N, \chi)$.
1. For $z > 0$, $x \in \mathbb{R}$, $y > 0$ and $\theta \in \mathbb{R}$,
$$\phi_f(\iota_\infty(z \, n(x) a(y) \kappa_\theta)) = y^{k/2} f(x + iy) e^{ik\theta}.$$
2. If $g = \gamma \, \iota_\infty(g_\infty) \, k$ as in Proposition 1.3.5 and $\tau = g_\infty i$, then $|\phi_f(g)| = (\mathrm{Im}\,\tau)^{k/2} |f(\tau)|$.
3. Let $\sigma \in SL_2(\mathbb{Z})$ with finite part $\sigma_f \in GL_2(\hat{\mathbb{Z}})$. For $g_\infty \in GL_2^+(\mathbb{R})$,
$$\phi_f(\iota_\infty(g_\infty) \, \sigma_f^{-1}) = ((f|_k \sigma) \|_k g_\infty)(i), \qquad \phi_f(\iota_\infty(n(x)a(y)) \, \sigma_f^{-1}) = y^{k/2} (f|_k\sigma)(x + iy).$$

Lean: not formalized

*Proof.* For part 1, $\det(z n(x)a(y)\kappa_\theta) = z^2$ and $j(z n(x) a(y) \kappa_\theta, i) = z y^{-1/2} e^{-i\theta}$ by Lemma 1.1.7. So $(f \|_k g)(i) = z^k z^{-k} y^{k/2} e^{ik\theta} f(x + iy)$. Part 2 follows from part 1, because $|\lambda(k)| = 1$ and $\mathrm{Im}(g_\infty i) = y$. For part 3, the rational element $\sigma^{-1}$ has the components $\sigma^{-1}$ at every place, so $\iota_\infty(g_\infty) \sigma_f^{-1} = \sigma^{-1} \, \iota_\infty(\sigma g_\infty)$. Proposition 1.3.5 with $k = 1$ gives $\phi_f(\iota_\infty(g_\infty)\sigma_f^{-1}) = (f\|_k \sigma g_\infty)(i) = ((f \|_k \sigma) \|_k g_\infty)(i)$, and $f\|_k\sigma = f|_k\sigma$ since $\det \sigma = 1$. The second formula is the case $g_\infty = n(x)a(y)$ of the first, by the computation of part 1. $\square$

Part 3 is the adelic form of the expansions at the cusps. The cusp $\sigma^{-1}\infty$ of $\Gamma_0(N)$ corresponds to the right translate of $\phi_f$ by the element $\sigma_f^{-1}$ of $GL_2(\hat{\mathbb{Z}})$. All the cusps are visible in the single function $\phi_f$, through its right translates by $GL_2(\hat{\mathbb{Z}})$. Section 1.4 uses this to describe the cusp forms.

**Remark 1.3.8 (normalizations).** The function $\phi_f$ uses the unitary slash operator $\|_k$, and not the slash operator $|_k$ of Volume 4. With $|_k$ the formula of Proposition 1.3.5 would still be well defined, but the central character would be $\omega(z)|z|_\mathbb{A}^{k-2}$ in place of $\omega(z)$, which is not unitary for $k \ne 2$. With $\|_k$ the center acts by the unitary character $\omega$, and $|\phi_f|$ is the function $(\mathrm{Im}\,\tau)^{k/2}|f(\tau)|$ of Volume 4, Lemma 1.4.3. The price is a factor $p^{1 - k/2}$ in the Hecke eigenvalues, see Theorem 1.6.8. Volume 7, Example 1.1.6, uses the same formula for $\Delta$, namely $\phi_\Delta(\gamma g_\infty k) = \Delta(g_\infty i) j(g_\infty, i)^{-12} (\det g_\infty)^6$, which is Proposition 1.3.5 for $k = 12$, $N = 1$. Some books use the character $k \mapsto \chi(a_k \bmod N)$ of the upper left entry instead of $\lambda$. It agrees with $\lambda$ on $\Gamma_0(N)$, because $a d \equiv 1 \bmod N$ there, and the resulting function is $\phi_f \cdot (\omega^{-1} \circ \det)$, with central character $\omega^{-1}$. Our choice gives $\omega_p(p) = \chi(p)$, so the central character at $p$ is the classical nebentypus at $p$.

**Example 1.3.9 (the lift of $\Delta$).** Let $N = 1$, $k = 12$ and $f = \Delta$. The character $\chi$ is trivial, so $\lambda$ and $\omega$ are trivial, and $K_0(1) = GL_2(\hat{\mathbb{Z}})$. Proposition 1.3.7 gives $\phi_\Delta(\iota_\infty(n(x)a(y)\kappa_\theta)) = y^6 \Delta(x + iy) e^{12i\theta}$. By Example 1.2.8, $\iota_p(\mathrm{diag}(p, 1)) = \delta \, \iota_\infty(\mathrm{diag}(p^{-1}, 1)) \, k$ with $\delta = \mathrm{diag}(p, 1)$ and $k \in GL_2(\hat{\mathbb{Z}})$. So
$$\phi_\Delta(\iota_p(\mathrm{diag}(p, 1))) = (\Delta \|_{12} \mathrm{diag}(p^{-1}, 1))(i) = p^{-6} \Delta(i/p) = p^{6} \Delta(pi),$$
where the last step uses $\Delta(-1/\tau) = \tau^{12}\Delta(\tau)$ at $\tau = i/p$: it gives $\Delta(pi) = p^{-12}\Delta(i/p)$. In the same way $\iota_p(\mathrm{diag}(1, p))$ corresponds to $\tau = pi$, and $(\Delta\|_{12}\mathrm{diag}(1, p^{-1}))(i) = p^{-6} p^{12} \Delta(pi) = p^6 \Delta(pi)$. The two values agree. This is expected: $\mathrm{diag}(1, p) = w \, \mathrm{diag}(p, 1) \, w^{-1}$ with $w = \begin{pmatrix} 0 & 1 \\ -1 & 0 \end{pmatrix}$, and $\iota_p(w) = w \cdot \iota_\infty(w)^{-1} \cdot k'$ with $k' \in GL_2(\hat{\mathbb{Z}})$, where $\iota_\infty(w) = \iota_\infty(\kappa_{\pi/2})$ acts by $e^{12 i \pi/2} = 1$.

**Example 1.3.10 (a character of odd weight).** Let $N = 4$ and let $\chi = \chi_{-4}$ be the character with $\chi(1) = 1$ and $\chi(3) = -1$. Then $\chi(-1) = -1$, so $M_k(4, \chi) \ne 0$ is possible only for odd $k$. The square of the theta series $\theta(\tau) = \sum_{n \in \mathbb{Z}} q^{n^2}$ is an element of $M_1(4, \chi_{-4})$. Its coefficient of $q^n$ is the number of ways to write $n$ as a sum of two squares. The character $\omega$ is trivial on $\mathbb{R}_{>0}$, equal to $\mathrm{sgn}$ on $\mathbb{R}^\times$ by Lemma 1.3.2, and $\omega_p(p) = \chi_{-4}(p) = (-1)^{(p-1)/2}$ for odd $p$. At $2$ it is the character $u \mapsto \chi_{-4}(u \bmod 4)^{-1} = \chi_{-4}(u \bmod 4)$ of $\mathbb{Z}_2^\times$. By class field theory, Volume 3, Chapter 7, $\omega$ is the quadratic character of $\mathbb{Q}^\times \backslash \mathbb{A}^\times$ attached to $\mathbb{Q}(i)$. The character $\lambda$ of $K_0(4)$ is $k \mapsto \chi_{-4}(d_k \bmod 4)$. The function $\phi_{\theta^2}$ satisfies $\phi_{\theta^2}(g\,\iota_\infty(\kappa_\theta)) = e^{i\theta}\phi_{\theta^2}(g)$ and $\phi_{\theta^2}(-g) = \phi_{\theta^2}(g)$, while $\iota_\infty(-I) = \iota_\infty(\kappa_\pi)$ acts by $e^{i\pi} = -1$ and $(-I)_f$ acts by $\lambda(-I) = \chi_{-4}(-1) = -1$. Exercise 5 shows that these signs always fit together, and that this is the adelic form of the condition $\chi(-1) = (-1)^k$.
