---
title: The converse
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## The converse

Sections 1.3 and 1.4 proved a list of properties of $\phi_f$. In this section we show that the list characterizes the functions $\phi_f$. So the space $M_k(N, \chi)$ can be defined on the adelic side alone, and the cusp forms are the cuspidal functions in it. We follow [Bum97], Section 3.6, and [Gel75], Chapter 3. We fix $N$, $\chi$ and $k$ with $\chi(-1) = (-1)^k$, and we keep the characters $\omega$ of Definition 1.3.1 and $\lambda$ of Definition 1.3.3.

**Definition 1.5.1 (adelic modular forms).** Let $\mathcal{A}_k(N, \chi)$ be the space of the functions $\phi : GL_2(\mathbb{A}) \to \mathbb{C}$ with these properties.
1. $\phi(\gamma g) = \phi(g)$ for $\gamma \in GL_2(\mathbb{Q})$.
2. $\phi(gk) = \lambda(k)\phi(g)$ for $k \in K_0(N)$.
3. $\phi(g\,\iota_\infty(\kappa_\theta)) = e^{ik\theta}\phi(g)$ for $\theta \in \mathbb{R}$.
4. $\phi(g\,\iota_\infty(r)) = \phi(g)$ for $r > 0$, where $r$ is the scalar matrix.
5. For each $g$ the function $h \mapsto \phi(g\,\iota_\infty(h))$ on $GL_2^+(\mathbb{R})$ is smooth, and $L\phi = 0$.
6. $\phi$ has moderate growth.

Let $\mathcal{A}_k^0(N, \chi)$ be the subspace of the cuspidal functions in $\mathcal{A}_k(N, \chi)$.

The conditions imply the central character: for $z = qru$ as in Definition 1.3.1, conditions 1, 4 and 2 give $\phi(zg) = \phi(gz) = \lambda(u)\phi(g) = \omega(z)\phi(g)$. The functions $\phi$ in $\mathcal{A}_k(N, \chi)$ are continuous, since by Theorem 1.2.5 the set $GL_2(\mathbb{Q})\,\iota_\infty(GL_2^+(\mathbb{R}))\,K_1(N)$ is all of $GL_2(\mathbb{A})$, and $\phi$ is continuous on each open set $\gamma\,\iota_\infty(GL_2^+(\mathbb{R}))\,K_1(N)$. So the constant term of Definition 1.4.11 makes sense. By Propositions 1.3.6 and 1.4.10 and Theorem 1.4.6, $\phi_f \in \mathcal{A}_k(N, \chi)$ for each $f \in M_k(N, \chi)$.

**Theorem 1.5.2 (the converse).** Let $\phi \in \mathcal{A}_k(N, \chi)$. Then there is a unique $f \in M_k(N, \chi)$ with $\phi = \phi_f$. It is
$$f(x + iy) = y^{-k/2}\phi(\iota_\infty(n(x)a(y))).$$
The form $f$ is a cusp form if and only if $\phi$ is cuspidal.

Lean: not formalized

*Proof.* Let $\Phi(h) = \phi(\iota_\infty(h))$ for $h \in GL_2^+(\mathbb{R})$. We define a function $f$ on $\mathbb{H}$ by
$$f(h i) = \det(h)^{-k/2} j(h, i)^k \, \Phi(h).$$
This does not depend on the choice of $h$. Indeed, two choices differ by $h' = h\,r\kappa_\theta$ with $r > 0$, because the stabilizer of $i$ in $GL_2^+(\mathbb{R})$ is $\mathbb{R}_{>0}SO(2)$. By conditions 3 and 4, $\Phi(h') = e^{ik\theta}\Phi(h)$. By the cocycle relation, $j(h', i) = j(h, i)\,r\,e^{-i\theta}$, and $\det(h')^{-k/2} = r^{-k}\det(h)^{-k/2}$. So the right side does not change. With $h = n(x)a(y)$ we get the formula of the theorem, and so $f$ is smooth by condition 5. In other words,
$$\Phi(h) = (f\|_k h)(i), \qquad \Phi(n(x)a(y)\kappa_\theta) = y^{k/2}f(x + iy)e^{ik\theta}.$$

*Holomorphy.* By the computation in the proof of Theorem 1.4.6 and Proposition 1.4.5, $L\phi = 0$ at the points $\iota_\infty(h)$ means $\partial f/\partial\bar\tau = 0$. So $f$ is holomorphic.

*The transformation law.* Let $\gamma \in \Gamma_0(N)$ with lower right entry $d$. The rational matrix $\gamma$ is $\iota_\infty(\gamma)\,\gamma_f$, so $\iota_\infty(\gamma h) = \gamma\,\iota_\infty(h)\,\gamma_f^{-1}$. Conditions 1 and 2 give $\Phi(\gamma h) = \lambda(\gamma_f)^{-1}\Phi(h) = \chi(d)\Phi(h)$. Let $\tau = hi$. Since $\det\gamma = 1$ and $j(\gamma h, i) = j(\gamma, \tau)j(h, i)$,
$$f(\gamma\tau) = \det(h)^{-k/2}j(\gamma, \tau)^k j(h, i)^k\,\chi(d)\,\Phi(h) = \chi(d)\,j(\gamma, \tau)^k f(\tau).$$
So $f|_k\gamma = \chi(d)f$. In particular $f|_k\gamma = f$ for $\gamma \in \Gamma_1(N)$.

*The cusps.* Let $\sigma \in SL_2(\mathbb{Z})$. As in the proof of part 3 of Proposition 1.3.7, $\iota_\infty(h)\,\sigma_f^{-1} = \sigma^{-1}\iota_\infty(\sigma h)$, so condition 1 gives $\phi(\iota_\infty(h)\sigma_f^{-1}) = \Phi(\sigma h) = (f\|_k\sigma h)(i)$. For $h = n(x)a(y)$ this is
$$(f|_k\sigma)(x + iy) = y^{-k/2}\,\phi(\iota_\infty(n(x)a(y))\,\sigma_f^{-1}).$$
The element $\sigma_f^{-1}$ is in $GL_2(\hat{\mathbb{Z}})$, so it does not change the height. At infinity, $\|n(x)a(y)\|_\infty = \max(y^{1/2}, |x|y^{-1/2}, y^{-1/2}, 1)$. For $y \ge 1$ and $|x| \le N/2$ this is at most $Ny^{1/2}$. Condition 6 gives constants $C$ and $M$ with
$$|(f|_k\sigma)(x + iy)| \le CN^M y^{(M - k)/2} \qquad (y \ge 1, \ |x| \le N/2).$$
The function $f|_k\sigma$ is holomorphic, and it has period $N$, because it is invariant under $\sigma^{-1}\Gamma_1(N)\sigma \supset \Gamma(N)$. So it has a Fourier expansion $\sum_{n \in \mathbb{Z}} c_n e^{2\pi i n\tau/N}$, with
$$c_n = \frac{1}{N}\int_{-N/2}^{N/2}(f|_k\sigma)(x + iy)\,e^{-2\pi i n(x + iy)/N}\,dx$$
for each $y > 0$. The bound gives $|c_n| \le CN^M y^{(M-k)/2}e^{2\pi ny/N}$. For $n < 0$ the right side tends to 0 as $y \to \infty$, so $c_n = 0$. Hence $f|_k\sigma = \sum_{n \ge 0}c_n e^{2\pi in\tau/N}$, and it is bounded on $\{\mathrm{Im}\,\tau \ge 1\}$. This is the condition at the cusps of Volume 4, Definition 1.2.3. So $f \in M_k(N, \chi)$.

*The equality $\phi = \phi_f$.* By Proposition 1.3.5, $\phi_f(\iota_\infty(h)) = (f\|_k h)(i) = \Phi(h)$. Both $\phi$ and $\phi_f$ satisfy conditions 1 and 2. So they agree on $GL_2(\mathbb{Q})\,\iota_\infty(GL_2^+(\mathbb{R}))\,K_0(N)$, which is $GL_2(\mathbb{A})$ by Theorem 1.2.5.

*Uniqueness.* If $\phi_f = \phi_{f'}$, then part 1 of Proposition 1.3.7 gives $y^{k/2}f(x + iy) = y^{k/2}f'(x + iy)$, so $f = f'$. The last claim is Theorem 1.4.14. $\square$

**Corollary 1.5.3 (the classical and the adelic spaces).** The map $f \mapsto \phi_f$ is an isomorphism of complex vector spaces from $M_k(N, \chi)$ onto $\mathcal{A}_k(N, \chi)$. It maps $S_k(N, \chi)$ onto $\mathcal{A}^0_k(N, \chi)$. In particular $\dim\mathcal{A}_k(N, \chi) = \dim M_k(N, \chi)$ and $\dim\mathcal{A}^0_k(N, \chi) = \dim S_k(N, \chi)$.

Lean: not formalized

*Proof.* The map is linear, because the formula of Proposition 1.3.5 is linear in $f$. It is injective and surjective by Theorem 1.5.2, and it respects the cuspidal subspaces by Theorem 1.4.14. $\square$

**Example 1.5.4 (level 1).** Let $N = 1$, so $\chi$ is trivial, $\lambda$ and $\omega$ are trivial, and $K_0(1) = GL_2(\hat{\mathbb{Z}})$. For odd $k$ the space $\mathcal{A}_k(1, 1)$ is 0, since $\chi(-1) = 1 \ne (-1)^k$. Exercise 5 proves this on the adelic side. For even $k \ge 0$, Volume 4, Corollary 1.3.5, gives the dimension of $M_k$, and so of $\mathcal{A}_k(1, 1)$. For $k = 12$ the space $\mathcal{A}_{12}(1, 1)$ has the basis $\phi_{E_{12}}$, $\phi_\Delta$, and $\mathcal{A}^0_{12}(1, 1) = \mathbb{C}\phi_\Delta$. In terms of the converse, a cuspidal $\phi \in \mathcal{A}_{12}(1, 1)$ is a multiple of $\phi_\Delta$ because $S_{12} = \Delta M_0 = \mathbb{C}\Delta$, by Volume 4, Theorem 1.3.4. For $k = 24$ the space $\mathcal{A}^0_{24}(1, 1)$ has dimension 2, and Section 1.6 turns the two normalized Hecke eigenforms of $S_{24}$ into a basis of Hecke eigenfunctions of it.

**Remark 1.5.5 (the Casimir condition).** In condition 5 the equation $L\phi = 0$ can be replaced, for cusp forms, by the Casimir equation $\Delta\phi = \frac{k}{2}(1 - \frac{k}{2})\phi$. Here is the idea, see [Bum97], Chapter 2, for the details. The group $GL_2(\mathbb{R})$ acts by unitary operators on the space $L^2$ of functions on $GL_2(\mathbb{Q})\backslash GL_2(\mathbb{A})$ with the central character $\omega$, since $\omega$ is unitary. So each $X \in \mathfrak{g}$ acts by a skew adjoint operator on the smooth vectors, and $L^* = -\frac{1}{2}(H + iV) = -R$. If $\phi$ is cuspidal of weight $k$, smooth and the functions $\phi$, $L\phi$, $RL\phi$ are square integrable, then by part 3 of Lemma 1.4.4
$$\langle L\phi, L\phi\rangle = -\langle RL\phi, \phi\rangle = \Big\langle \Delta\phi - \frac{k}{2}\Big(1 - \frac{k}{2}\Big)\phi, \phi\Big\rangle.$$
So the Casimir equation implies $L\phi = 0$. The analytic conditions hold for cusp forms, which decay rapidly in the cusp, and this is the point of [Bum97], Chapter 2. The Casimir equation is the form of condition 5 that generalizes: it says that $\phi$ is an eigenvector of the center of $U(\mathfrak{g}_\mathbb{C})$, and Chapter 2 uses it in the definition of automorphic forms. The cuspidality is needed. For $k = 2$ let $E_2^*(\tau) = E_2(\tau) - 3/(\pi y)$ be the non-holomorphic Eisenstein series, where $E_2 = 1 - 24\sum_{n \ge 1}\sigma_1(n)q^n$. It is a classical fact that $E_2^*$ transforms like a modular form of weight 2 for $SL_2(\mathbb{Z})$. Its lift $\phi(\iota_\infty(n(x)a(y)\kappa_\theta)) = yE_2^*(x + iy)e^{2i\theta}$ is not killed by $L$. By the formula in the proof of Theorem 1.4.6, $L\phi = -2iy^2\,\partial E_2^*/\partial\bar\tau = 3/\pi$, a constant function of weight 0. So $RL\phi = 0$, and $\Delta\phi = 0 = \frac{k}{2}(1 - \frac{k}{2})\phi$ for $k = 2$, while $L\phi \ne 0$.

**Remark 1.5.6 (the group $\Gamma_1(N)$).** The construction works for $K_1(N)$ and the whole space $M_k(\Gamma_1(N))$. For $f \in M_k(\Gamma_1(N))$, Proposition 1.3.5 with the trivial character on $K_1(N)$ defines $\phi_f$, right invariant under $K_1(N)$. The quotient $K_0(N)/K_1(N) \cong (\mathbb{Z}/N\mathbb{Z})^\times$, by $k \mapsto d_k \bmod N$, acts on these functions by right translation. Exercise 6 shows that the right translation by $k_0$ with $d_{k_0} \equiv d \bmod N$ takes $\phi_f$ to $\phi_{\langle d\rangle^{-1}f}$, where $\langle d\rangle$ is the diamond operator of Volume 4, Definition 1.5.2. So the decomposition $M_k(\Gamma_1(N)) = \bigoplus_\chi M_k(N, \chi)$ of Volume 4, Proposition 1.5.3, is the decomposition of a representation of the finite abelian group $K_0(N)/K_1(N)$ into characters, and $M_k(N, \chi)$ corresponds to the character $\lambda_\chi$. This explains the inverse in Definition 1.3.3.
