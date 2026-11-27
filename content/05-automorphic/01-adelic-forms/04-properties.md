---
title: Analytic properties of the lift
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Analytic properties of the lift

Section 1.3 gave the transformation laws of $\phi_f$ under $GL_2(\mathbb{Q})$, $K_0(N)$, $SO(2)$ and the center. These laws do not see that $f$ is holomorphic, and they do not see the condition at the cusps. In this section we express these two conditions on the adelic side. Holomorphy becomes a differential equation for the action of the Lie algebra of $GL_2(\mathbb{R})$, and it implies an eigenvalue equation for the Casimir operator. The condition at the cusps becomes moderate growth, and the cusp forms are the functions with vanishing constant term. We fix $N$, $\chi$, $k$ and $f \in M_k(N, \chi)$ as in Section 1.3.

### The Lie algebra

Let $\mathfrak{g} = \mathfrak{gl}_2(\mathbb{R})$ be the Lie algebra of $GL_2(\mathbb{R})$, and let $\mathfrak{g}_\mathbb{C} = \mathfrak{gl}_2(\mathbb{C})$ be its complexification. We use these elements of $\mathfrak{g}$:
$$H = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}, \quad E = \begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix}, \quad F = \begin{pmatrix} 0 & 0 \\ 1 & 0 \end{pmatrix}, \quad W = E - F, \quad V = E + F.$$
Then $\exp(\theta W) = \kappa_\theta$, $\exp(tH) = a(e^{2t})$ and $\exp(tE) = n(t)$. Together with the identity matrix $I$, the elements $H$, $E$, $F$ are a basis of $\mathfrak{g}$, and $H$, $E$, $F$ are a basis of the Lie algebra $\mathfrak{sl}_2(\mathbb{R})$.

**Definition 1.4.1 (the action of the Lie algebra).** Let $\phi : GL_2(\mathbb{A}) \to \mathbb{C}$ be a function such that $h \mapsto \phi(g\,\iota_\infty(h))$ is smooth on $GL_2^+(\mathbb{R})$ for each $g$. For $X \in \mathfrak{g}$ let
$$(X\phi)(g) = \frac{d}{dt}\Big|_{t = 0} \phi(g \, \iota_\infty(\exp(tX))).$$
For $X + iY \in \mathfrak{g}_\mathbb{C}$ with $X, Y \in \mathfrak{g}$ let $(X + iY)\phi = X\phi + iY\phi$. Let
$$R = \tfrac{1}{2}(H + iV) = \frac{1}{2}\begin{pmatrix} 1 & i \\ i & -1 \end{pmatrix}, \qquad L = \tfrac{1}{2}(H - iV) = \frac{1}{2}\begin{pmatrix} 1 & -i \\ -i & -1 \end{pmatrix}.$$
The operators $R$ and $L$ are the *raising* and the *lowering operator*.

The operator $X$ is the derivative of the right translation in the direction $X$. It commutes with left translations by $GL_2(\mathbb{A})$ and with right translations by $GL_2(\mathbb{A}_f)$, because these act on other variables. The map $X \mapsto (\phi \mapsto X\phi)$ is a homomorphism of Lie algebras: $[X, Y]\phi = X(Y\phi) - Y(X\phi)$. This is the standard fact that the left invariant vector fields on a Lie group form a Lie algebra isomorphic to its Lie algebra, see [Bum97], Section 2.2. So the action extends to the universal enveloping algebra $U(\mathfrak{g}_\mathbb{C})$. We use the same names for the elements of $\mathfrak{g}_\mathbb{C}$ and for the operators.

**Lemma 1.4.2 (brackets).**
1. $[H, E] = 2E$, $[H, F] = -2F$, $[E, F] = H$, $[W, H] = -2V$ and $[W, V] = 2H$.
2. $[W, R] = 2iR$, $[W, L] = -2iL$ and $[R, L] = -iW$.
3. For $\theta \in \mathbb{R}$, $\kappa_\theta R \kappa_\theta^{-1} = e^{2i\theta} R$ and $\kappa_\theta L \kappa_\theta^{-1} = e^{-2i\theta} L$.

Lean: not formalized

*Proof.* Part 1 is a direct computation with $2 \times 2$ matrices. For example $WH = \begin{pmatrix} 0 & -1 \\ -1 & 0 \end{pmatrix}$ and $HW = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}$, so $[W, H] = -2V$. Part 2 follows from part 1 by linearity: $[W, R] = \frac{1}{2}(-2V + 2iH) = i(H + iV) = 2iR$, and $[W, L] = \frac{1}{2}(-2V - 2iH) = -2iL$. For the last bracket, $[R, L] = \frac{1}{4}[H + iV, H - iV] = -\frac{i}{2}[H, V]$, and $[H, V] = 2W$ since $HV = W$ and $VH = -W$. For part 3, $\kappa_\theta X \kappa_\theta^{-1} = \exp(\theta \, \mathrm{ad}\, W) X$, and $R$ and $L$ are eigenvectors of $\mathrm{ad}\, W$ with the eigenvalues $2i$ and $-2i$ by part 2. $\square$

**Definition 1.4.3 (the Casimir element).** The *Casimir element* is
$$\Delta = -\tfrac{1}{4}\left(H^2 + 2EF + 2FE\right) \in U(\mathfrak{g}_\mathbb{C}).$$

**Lemma 1.4.4 (the Casimir element).**
1. $\Delta$ is in the center of $U(\mathfrak{g}_\mathbb{C})$.
2. $\Delta = -\frac{1}{4}(2RL + 2LR - W^2) = -RL - \frac{i}{2} W + \frac{1}{4}W^2$.
3. Let $\phi$ be smooth in the sense of Definition 1.4.1 with $\phi(g\,\iota_\infty(\kappa_\theta)) = e^{ik\theta}\phi(g)$ for all $g$ and $\theta$. Then $W\phi = ik\phi$ and
$$\Delta\phi = -RL\phi + \frac{k}{2}\left(1 - \frac{k}{2}\right)\phi.$$

Lean: not formalized

*Proof.* For part 1 it is enough to show that $\Delta$ commutes with $H$, $E$, $F$ and $I$. The element $I$ is central in $\mathfrak{g}$. Let $C = H^2 + 2EF + 2FE$. By Lemma 1.4.2, $[E, H^2] = [E, H]H + H[E, H] = -2EH - 2HE$, $[E, EF] = E[E, F] = EH$ and $[E, FE] = [E, F]E = HE$. So $[E, C] = -2EH - 2HE + 2EH + 2HE = 0$. The same computation, with the roles of $E$ and $F$ exchanged and $[F, H] = 2F$, $[F, E] = -H$, gives $[F, C] = 0$. Finally $[H, EF] = [H, E]F + E[H, F] = 2EF - 2EF = 0$, in the same way $[H, FE] = 0$, and $[H, H^2] = 0$. For part 2, $E = \frac{1}{2}(V + W)$ and $F = \frac{1}{2}(V - W)$ give $2EF + 2FE = V^2 - W^2$. From $H = R + L$ and $iV = R - L$ we get $H^2 + V^2 = (R + L)^2 - (R - L)^2 = 2RL + 2LR$. This is the first formula. By Lemma 1.4.2, $LR = RL - [R, L] = RL + iW$, and the second formula follows. For part 3, $W\phi = \frac{d}{d\theta}\big|_{\theta = 0} e^{ik\theta}\phi = ik\phi$. So $-\frac{i}{2}W\phi = \frac{k}{2}\phi$ and $\frac{1}{4}W^2\phi = -\frac{k^2}{4}\phi$, and part 2 gives the formula. $\square$

The element $I$ acts on a function with $\phi(g \, \iota_\infty(r)) = \phi(g)$ for $r > 0$ by 0. So on such functions the action of $U(\mathfrak{g}_\mathbb{C})$ factors through $U(\mathfrak{sl}_2(\mathbb{C}))$.

### The operators in coordinates

By Lemma 1.1.7 each element of $GL_2^+(\mathbb{R})$ has the form $z \, n(x) a(y) \kappa_\theta$. Let $\phi$ be as in Definition 1.4.1, fix $g_0 \in GL_2(\mathbb{A})$, and assume that $\phi(g\,\iota_\infty(r)) = \phi(g)$ for $r > 0$. Then $\Phi(x, y, \theta) = \phi(g_0 \, \iota_\infty(n(x) a(y) \kappa_\theta))$ determines $\phi$ on $g_0 \, \iota_\infty(GL_2^+(\mathbb{R}))$.

**Proposition 1.4.5 (the operators in coordinates).** In the coordinates $(x, y, \theta)$,
$$W = \frac{\partial}{\partial\theta}, \qquad R = e^{2i\theta}\left(iy\frac{\partial}{\partial x} + y\frac{\partial}{\partial y} - \frac{i}{2}\frac{\partial}{\partial\theta}\right), \qquad L = e^{-2i\theta}\left(-iy\frac{\partial}{\partial x} + y\frac{\partial}{\partial y} + \frac{i}{2}\frac{\partial}{\partial\theta}\right).$$
That is, $(X\phi)(g_0\,\iota_\infty(n(x)a(y)\kappa_\theta))$ is the operator on the right applied to $\Phi$, for $X = W, R, L$.

Lean: not formalized

*Proof.* Let $X' = aH + bE + cW$ with $a, b, c \in \mathbb{R}$. The derivative at $t = 0$ of a function of $\exp(tX')$ depends only on $X'$ to first order, so we may replace $\exp(tX')$ by $\exp(taH)\exp(tbE)\exp(tcW) = a(e^{2ta}) \, n(tb) \, \kappa_{tc}$. Since $a(y) n(u) a(y)^{-1} = n(yu)$,
$$n(x)a(y) \, a(e^{2ta}) \, n(tb) \, \kappa_{tc} \, \kappa_\theta = n(x + tb y e^{2ta}) \, a(y e^{2ta}) \, \kappa_{\theta + tc}.$$
So the derivative of $t \mapsto \Phi$ along this path at $t = 0$ is $(by\,\partial_x + 2ay\,\partial_y + c\,\partial_\theta)\Phi$. Now let $X \in \mathfrak{g}_\mathbb{C}$. Since $\kappa_\theta \exp(tX) = \exp(t\,\kappa_\theta X\kappa_\theta^{-1})\kappa_\theta$, the value of $X\phi$ at $g_0\,\iota_\infty(n(x)a(y)\kappa_\theta)$ is the derivative of $t \mapsto \phi(g_0\,\iota_\infty(n(x)a(y)\exp(tX')\kappa_\theta))$ with $X' = \kappa_\theta X\kappa_\theta^{-1}$, extended linearly to complex $X'$. For $X = W$ we have $X' = W$, which gives $\partial_\theta$. For $X = L$ we have $X' = e^{-2i\theta}L$ by Lemma 1.4.2. Since $F = E - W$, we have $V = 2E - W$ and $L = \frac{1}{2}H - iE + \frac{i}{2}W$, so $(a, b, c) = (\frac{1}{2}, -i, \frac{i}{2})$. This gives the formula for $L$. In the same way $R = \frac{1}{2}H + iE - \frac{i}{2}W$ and $X' = e^{2i\theta}R$. $\square$

**Theorem 1.4.6 (holomorphy and the Casimir eigenvalue).** Let $f \in M_k(N, \chi)$. Then
$$L\phi_f = 0, \qquad W\phi_f = ik\phi_f, \qquad \Delta\phi_f = \frac{k}{2}\left(1 - \frac{k}{2}\right)\phi_f.$$

Lean: not formalized

*Proof.* We first compute $L$ on a function of the form $\Phi = y^{k/2} F(x + iy) e^{ik\theta}$, where $F$ is a smooth function on $\mathbb{H}$. The term $\frac{i}{2}\partial_\theta$ multiplies $\Phi$ by $\frac{i}{2} \cdot ik = -\frac{k}{2}$. The term $y\,\partial_y$ gives $\frac{k}{2}\Phi + y^{k/2 + 1} (\partial_y F) e^{ik\theta}$. So
$$L\Phi = e^{i(k-2)\theta} y^{k/2 + 1} \left(\partial_y F - i \partial_x F\right) = -2i \, y^{k/2+1} e^{i(k-2)\theta} \, \frac{\partial F}{\partial\bar\tau},$$
where $\partial/\partial\bar\tau = \frac{1}{2}(\partial_x + i\partial_y)$. Now fix $g_0 = \gamma\,\iota_\infty(g_\infty)\,k_0$ as in Proposition 1.3.5. For $h \in GL_2^+(\mathbb{R})$ we have $g_0\,\iota_\infty(h) = \gamma\,\iota_\infty(g_\infty h)\,k_0$, so
$$\phi_f(g_0\,\iota_\infty(h)) = \lambda(k_0)\,((f\|_k g_\infty)\|_k h)(i).$$
By the computation in the proof of Proposition 1.3.7, this is $\lambda(k_0) y^{k/2} F(x + iy) e^{ik\theta}$ for $h = n(x)a(y)\kappa_\theta$, with $F = f \|_k g_\infty$. The function $F$ is holomorphic. So $L\phi_f = 0$ by Proposition 1.4.5. The second claim is part 3 of Proposition 1.3.6, as in Lemma 1.4.4. The third claim follows from part 3 of Lemma 1.4.4. $\square$

The proof shows more: for a smooth $F$ the function $y^{k/2}F e^{ik\theta}$ is killed by $L$ exactly when $F$ is holomorphic. Section 1.5 uses this for the converse. The raising operator does not kill $\phi_f$. Exercise 7 computes $R\phi_f$, which has weight $k + 2$ and corresponds to the non-holomorphic function $2i f' + kf/y$, a form of the Maass raising operator.

**Remark 1.4.7 (weight 0 and Maass forms).** For a function of weight 0, $W\phi = 0$ and part 2 of Lemma 1.4.4 gives $\Delta\phi = -RL\phi$. Exercise 8 computes this in coordinates: if $\phi(\iota_\infty(n(x)a(y)\kappa_\theta)) = u(x + iy)$, then $\Delta$ acts as $-y^2(\partial_x^2 + \partial_y^2)$ on $u$. This is the hyperbolic Laplacian of the theory of Maass forms, see [Bum97], Section 2.2. Lean: `Langlands.hyperbolicLaplacian` is this operator on functions on $\mathbb{H}$. The eigenvalue in Theorem 1.4.6 has the form $s(1 - s)$ with $s = k/2$. Chapter 2 treats both kinds of forms as automorphic forms, distinguished by their component at infinity. In the Lean project the derivatives along the Lie algebra exist for $GL_n$ over a number field, as `Langlands.NumberFieldGL.lieDerivative`, and the center of $U(\mathfrak{gl}_n)$ appears through the Capelli operator `Langlands.NumberFieldGL.capelliOperator`. The project does not state Theorem 1.4.6.

### Moderate growth

The condition at the cusps becomes a growth condition. We measure the size of an element of $GL_2(\mathbb{A})$ by a height.

**Definition 1.4.8 (the height and moderate growth).** For $g \in GL_2(\mathbb{Q}_v)$ let $\|g\|_v = \max(|g_{11}|_v, |g_{12}|_v, |g_{21}|_v, |g_{22}|_v, |\det g|_v^{-1})$. For $g \in GL_2(\mathbb{A})$ let $\|g\| = \prod_v \|g_v\|_v$. A function $\phi$ on $GL_2(\mathbb{A})$ has *moderate growth* if there are constants $C$ and $M$ with $|\phi(g)| \le C\|g\|^M$ for all $g \in GL_2(\mathbb{A})$.

The product is finite, because $\|g_p\|_p = 1$ for $g_p \in K_p$, and $g_p \in K_p$ for almost all $p$. The function $\|\cdot\|$ is the height of [Bum97], Section 3.3. At a prime $p$ the ultrametric inequality gives $\|gh\|_p \le \|g\|_p\|h\|_p$. At the infinite place $|(gh)_{ij}| \le 2\max|g_{ij}|\max|h_{ij}|$, so $\|gh\|_\infty \le 2\|g\|_\infty\|h\|_\infty$, and $\|gh\| \le 2\|g\|\|h\|$ (Exercise 9).

To compare the height with the classical picture we use the following function. For $w$ in the row space $\mathbb{A}^2$ let $\mathcal{H}(w) = \prod_v \|w_v\|_v$, where $\|w_\infty\|_\infty$ is the euclidean norm and $\|w_p\|_p = \max(|w_{p,1}|_p, |w_{p,2}|_p)$. For $g \in GL_2(\mathbb{A})$ let
$$m(g) = \inf_{v \in \mathbb{Q}^2 \setminus 0} \mathcal{H}(vg), \qquad \mathfrak{h}(g) = \frac{|\det g|_\mathbb{A}}{m(g)^2}.$$
Here $v$ is a row vector. For $q \in \mathbb{Q}^\times$ we have $\mathcal{H}(qw) = |q|_\mathbb{A}\mathcal{H}(w) = \mathcal{H}(w)$ by the product formula. So in the infimum we may take $v = (c, d)$ with coprime integers $c$, $d$. For such $v$ and $g = 1$ we have $\mathcal{H}(v) = (c^2 + d^2)^{1/2} \ge 1$, because $\|v\|_p = 1$ for all $p$.

**Lemma 1.4.9 (the function $\mathfrak{h}$).**
1. $\mathfrak{h}(\gamma g z \kappa k) = \mathfrak{h}(g)$ for $\gamma \in GL_2(\mathbb{Q})$, $z \in \mathbb{A}^\times$, $\kappa \in O(2)$ at the infinite place and $k \in GL_2(\hat{\mathbb{Z}})$.
2. Let $g_\infty \in GL_2^+(\mathbb{R})$ and $\tau = g_\infty i$. Then $\mathfrak{h}(\iota_\infty(g_\infty)) = \max_{\sigma \in SL_2(\mathbb{Z})} \mathrm{Im}(\sigma\tau)$. The maximum is attained at each $\sigma$ with $\sigma\tau \in \mathcal{D}$, where $\mathcal{D}$ is the fundamental domain of Volume 4, Theorem 1.1.4. In particular $\mathfrak{h} \ge \sqrt{3}/2$.
3. $\mathfrak{h}(g) \le 8\|g\|^6$ for all $g \in GL_2(\mathbb{A})$.

Lean: not formalized

*Proof.* For part 1, $v \mapsto v\gamma$ is a bijection of $\mathbb{Q}^2 \setminus 0$, so $m(\gamma g) = m(g)$, and $|\det\gamma|_\mathbb{A} = 1$. The groups $O(2)$ and $GL_2(\mathbb{Z}_p)$ preserve the norms $\|\cdot\|_\infty$ and $\|\cdot\|_p$ on row vectors, so $m$ and $|\det|_\mathbb{A}$ do not change under right multiplication by $\kappa$ and $k$. Finally $m(gz) = |z|_\mathbb{A} m(g)$ and $|\det(gz)|_\mathbb{A} = |z|_\mathbb{A}^2|\det g|_\mathbb{A}$. For part 2 write $g_\infty = z\,n(x)a(y)\kappa_\theta$ as in Lemma 1.1.7. For coprime integers $c$, $d$ the vector $(c, d)\,\iota_\infty(g_\infty)$ has norm 1 at each prime, and at infinity
$$\|(c, d)\, g_\infty\|_\infty^2 = z^2\left(c^2 y + \frac{(cx + d)^2}{y}\right) = z^2 \, \frac{|c\tau + d|^2}{y}.$$
Since $\det g_\infty = z^2$, we get $\mathfrak{h}(\iota_\infty(g_\infty)) = \sup_{(c, d)} y/|c\tau + d|^2$. Each coprime pair $(c, d)$ is the lower row of some $\sigma \in SL_2(\mathbb{Z})$, and $\mathrm{Im}(\sigma\tau) = y/|c\tau + d|^2$ by Volume 4, Lemma 1.1.2. So $\mathfrak{h}(\iota_\infty(g_\infty))$ is the supremum of $\mathrm{Im}(\sigma\tau)$. Let $w = \sigma_0\tau \in \mathcal{D}$, which exists by Volume 4, Theorem 1.1.4. For integers $(c, d) \ne (0, 0)$, $|cw + d|^2 = c^2|w|^2 + 2cd\,\mathrm{Re}(w) + d^2 \ge c^2 + d^2 - |cd| \ge 1$, since $|w| \ge 1$ and $|\mathrm{Re}(w)| \le 1/2$. So $\mathrm{Im}(\sigma w) \le \mathrm{Im}(w)$ for all $\sigma$, the supremum is the maximum $\mathrm{Im}(w)$, and $\mathrm{Im}(w) \ge \sqrt{3}/2$ on $\mathcal{D}$.

For part 3 let $v = (c, d)$ with coprime integers, and let $u = vg$. At each place $w$, the entries of $g^{-1}$ are the entries of the adjugate matrix divided by $\det g$, so $|(g^{-1})_{ij}|_w \le \|g\|_w^2$. At a prime, $\|v\|_p = \|u g^{-1}\|_p \le \|u\|_p\|g\|_p^2$. At infinity, the Cauchy-Schwarz inequality gives $|(ug^{-1})_j| \le \|u\|_\infty \sqrt{2}\,\|g\|_\infty^2$, so $\|v\|_\infty \le 2\|u\|_\infty\|g\|_\infty^2$. The product over all places gives $1 \le \mathcal{H}(v) \le 2\mathcal{H}(vg)\|g\|^2$. So $m(g) \ge 1/(2\|g\|^2)$. Also $|\det g|_\infty \le 2\|g\|_\infty^2$ and $|\det g|_p \le \|g\|_p^2$, so $|\det g|_\mathbb{A} \le 2\|g\|^2$. Hence $\mathfrak{h}(g) \le 2\|g\|^2 \cdot 4\|g\|^4$. $\square$

By part 1 and Theorem 1.2.5, $\mathfrak{h}(g)$ for $g = \gamma\,\iota_\infty(g_\infty)\,k$ is the function $\max_\sigma \mathrm{Im}(\sigma g_\infty i)$ of part 2. It measures how far the point $g_\infty i$ is up in the cusp, after it is moved into $\mathcal{D}$.

**Proposition 1.4.10 (moderate growth of $\phi_f$).** Let $f \in M_k(N, \chi)$.
1. There is a constant $C$ with $|\phi_f(g)| \le C\,\mathfrak{h}(g)^{k/2}$ for all $g$. If $k \ge 0$, then $|\phi_f(g)| \le C 8^{k/2}\|g\|^{3k}$, so $\phi_f$ has moderate growth.
2. If $f \in S_k(N, \chi)$, then $\phi_f$ is bounded.

Lean: not formalized

*Proof.* Let $g = \gamma\,\iota_\infty(g_\infty)\,k_0$ and $\tau = g_\infty i$. By part 2 of Proposition 1.3.7, $|\phi_f(g)| = (\mathrm{Im}\,\tau)^{k/2}|f(\tau)|$. Choose $\sigma \in SL_2(\mathbb{Z})$ with $w = \sigma\tau \in \mathcal{D}$. Then $\mathrm{Im}\,\tau = \mathrm{Im}\,w/|j(\sigma^{-1}, w)|^2$ and $f(\tau) = j(\sigma^{-1}, w)^k (f|_k\sigma^{-1})(w)$, so
$$(\mathrm{Im}\,\tau)^{k/2}|f(\tau)| = (\mathrm{Im}\,w)^{k/2}|(f|_k\sigma^{-1})(w)|.$$
Since $f|_k\gamma' = f$ for $\gamma' \in \Gamma_1(N)$, the function $f|_k\alpha$ depends only on the coset $\Gamma_1(N)\alpha$, so there are only finitely many functions $f|_k\alpha$ with $\alpha \in SL_2(\mathbb{Z})$. Each of them is bounded on a region $\{\mathrm{Im} \ge Y\}$ by Volume 4, Definition 1.2.3, and it is continuous on the compact set $\mathcal{D} \cap \{\mathrm{Im} \le Y\}$. So there is $C$ with $|(f|_k\alpha)(w)| \le C$ for all $\alpha$ and all $w \in \mathcal{D}$. Parts 1 and 2 of Lemma 1.4.9 give $\mathrm{Im}\,w = \mathfrak{h}(g)$, which proves the first claim. The second claim follows from part 3 of Lemma 1.4.9. For part 2, Volume 4, Lemma 1.4.3, applied to $\Gamma = \Gamma_1(N)$, says that $(\mathrm{Im}\,\tau)^{k/2}|f(\tau)|$ is bounded on $\mathbb{H}$. $\square$

For $k < 0$ the space $M_k(N, \chi)$ is 0 by Volume 4, Proposition 1.3.10, so the condition $k \ge 0$ in part 1 is no restriction. The exponent $3k$ is not optimal. Exercise 9 shows that $\phi_{E_k}$ grows exactly like $\mathfrak{h}^{k/2}$ along the elements $\iota_\infty(a(y))$, and this is the growth of the constant term.

### The constant term and cusp forms

**Definition 1.4.11 (the constant term).** Let $\phi$ be a continuous function on $GL_2(\mathbb{A})$ with $\phi(n(\xi)g) = \phi(g)$ for $\xi \in \mathbb{Q}$. Its *constant term* is the function
$$\phi_N(g) = \int_{\mathbb{Q}\backslash\mathbb{A}} \phi(n(x)g)\,dx,$$
where $dx$ is the Haar measure on the compact group $\mathbb{Q}\backslash\mathbb{A}$ of total mass 1. The function $\phi$ is *cuspidal* if $\phi_N = 0$.

**Lemma 1.4.12 (properties of the constant term).**
1. The set $[0, 1) \times \hat{\mathbb{Z}}$ is a fundamental domain for $\mathbb{Q}$ in $\mathbb{A}$, and $dx$ is the product of the Lebesgue measure on $[0, 1)$ and the Haar measure of total mass 1 on $\hat{\mathbb{Z}}$.
2. Let $\phi$ be left invariant under $GL_2(\mathbb{Q})$. Then $\phi_N(n b g) = \phi_N(g)$ for $n \in N(\mathbb{A})$ and $b \in B(\mathbb{Q})$.
3. For $h \in GL_2(\mathbb{A})$, the constant term of $g \mapsto \phi(gh)$ is $g \mapsto \phi_N(gh)$.

Lean: not formalized

*Proof.* For part 1 let $x \in \mathbb{A}$. Its finite part is in $\mathbb{Z}_p$ for all $p$ outside a finite set $S$. For $p \in S$ choose $r_p \in \mathbb{Z}[1/p]$ with $x_p - r_p \in \mathbb{Z}_p$. The rational number $r = \sum_{p \in S} r_p$ is in $\mathbb{Z}_q$ for $q \notin S$, and $r - r_p \in \mathbb{Z}_p$ for $p \in S$. So $x - r$ has finite part in $\hat{\mathbb{Z}}$, and we subtract the integer part of its real component. If $\xi \in \mathbb{Q}$ maps $[0, 1) \times \hat{\mathbb{Z}}$ to a set that meets it, then $\xi \in \hat{\mathbb{Z}} \cap \mathbb{Q} = \mathbb{Z}$ and $\xi = 0$. The measure of the fundamental domain is 1, so the product measure is the normalized Haar measure. For part 2, the invariance under $N(\mathbb{A})$ is the invariance of $dx$ under translation. Write $b = n(s)\,\mathrm{diag}(a, d)$ with $s \in \mathbb{Q}$ and $a, d \in \mathbb{Q}^\times$. Then $n(x)b = b\,n(xd/a)$, so $\phi(n(x)bg) = \phi(n(xd/a)g)$. The map $x \mapsto xd/a$ is an automorphism of $\mathbb{Q}\backslash\mathbb{A}$, and it preserves $dx$, because $|d/a|_\mathbb{A} = 1$. Part 3 is clear. $\square$

**Proposition 1.4.13 (the constant terms of $\phi_f$).** Let $f \in M_k(N, \chi)$ and $\sigma \in SL_2(\mathbb{Z})$. Let $a_0(f|_k\sigma)$ be the constant term of the expansion of the periodic function $f|_k\sigma$ in powers of $e^{2\pi i\tau/N}$. Then for $x \in \mathbb{R}$, $y > 0$ and $\theta \in \mathbb{R}$,
$$\phi_{f, N}(\iota_\infty(n(x)a(y)\kappa_\theta)\,\sigma_f^{-1}) = y^{k/2}e^{ik\theta}\,a_0(f|_k\sigma).$$

Lean: not formalized

*Proof.* Let $\psi(g) = \phi_f(g\sigma_f^{-1})$. Then $\psi_N(g) = \phi_{f, N}(g\sigma_f^{-1})$ by part 3 of Lemma 1.4.12. The group $K(N)$ is normal in $GL_2(\hat{\mathbb{Z}})$ and contained in $K_1(N)$, so $\psi$ is right invariant under $\sigma_f K(N)\sigma_f^{-1} = K(N)$. Let $g = \iota_\infty(n(x)a(y)\kappa_\theta)$ and let $u = (u_\infty, u_f) \in [0, 1) \times \hat{\mathbb{Z}}$. Write $\hat{\mathbb{Z}} = \bigsqcup_{j = 0}^{N-1}(j + N\hat{\mathbb{Z}})$. For $u_f \in j + N\hat{\mathbb{Z}}$ the element $n(u_f - j)$ of $GL_2(\hat{\mathbb{Z}})$ is in $K(N)$, and $n(j)_f = n(j)\,\iota_\infty(n(-j))$ with $n(j) \in GL_2(\mathbb{Q})$. So
$$\psi(n(u)g) = \psi(\iota_\infty(n(u_\infty)) \, g \, n(j)_f \, n(u_f - j)_f) = \psi(\iota_\infty(n(u_\infty - j)) \, g).$$
Each class $j + N\hat{\mathbb{Z}}$ has measure $1/N$. By part 1 of Lemma 1.4.12 and part 3 of Proposition 1.3.7, with the weight $e^{ik\theta}$ from part 3 of Proposition 1.3.6,
$$\psi_N(g) = \frac{1}{N}\sum_{j = 0}^{N-1}\int_0^1 \psi(\iota_\infty(n(t - j)n(x)a(y)\kappa_\theta))\,dt = \frac{e^{ik\theta}y^{k/2}}{N}\int_{1 - N}^{1}(f|_k\sigma)(x + t + iy)\,dt.$$
The function $f|_k\sigma$ is invariant under $\sigma^{-1}\Gamma_1(N)\sigma \supset \Gamma(N)$, so it has period $N$. Its average over an interval of length $N$ is the constant term $a_0(f|_k\sigma)$ of its expansion. $\square$

**Theorem 1.4.14 (cusp forms).** Let $f \in M_k(N, \chi)$. Then $\phi_f$ is cuspidal if and only if $f \in S_k(N, \chi)$.

Lean: not formalized

*Proof.* Each $\gamma \in GL_2(\mathbb{Q})$ has the form $b\sigma^{-1}$ with $b \in B(\mathbb{Q})$ and $\sigma \in SL_2(\mathbb{Z})$. Indeed, multiply the lower row of $\gamma$ by a rational number to get coprime integers $(c, d)$, and choose $\sigma^{-1} \in SL_2(\mathbb{Z})$ with lower row $(c, d)$. Then $\gamma\sigma$ has lower row proportional to $(0, 1)$, so it is in $B(\mathbb{Q})$. Now let $g \in GL_2(\mathbb{A})$, and write $g = \gamma\,\iota_\infty(g_\infty)\,k_0$ as in Proposition 1.3.5 and $\gamma = b\sigma^{-1}$. Since $\sigma^{-1} = \iota_\infty(\sigma^{-1})\,\sigma_f^{-1}$, we get $g = b\,\iota_\infty(\sigma^{-1}g_\infty)\,\sigma_f^{-1}k_0$. Write $\sigma^{-1}g_\infty = z\,n(x)a(y)\kappa_\theta$. By part 2 of Lemma 1.4.12, part 4 of Proposition 1.3.6 and part 2 of Proposition 1.3.6,
$$\phi_{f, N}(g) = \lambda(k_0)\,\phi_{f, N}(\iota_\infty(n(x)a(y)\kappa_\theta)\,\sigma_f^{-1}) = \lambda(k_0)\,y^{k/2}e^{ik\theta}a_0(f|_k\sigma)$$
by Proposition 1.4.13. Hence $\phi_{f, N} = 0$ if and only if $a_0(f|_k\sigma) = 0$ for all $\sigma \in SL_2(\mathbb{Z})$. By Volume 4, Definition 1.2.3 and Lemma 1.2.4, this is the condition that $f$ is a cusp form. $\square$

The proof shows that the constant term of $\phi_f$ is determined by the constant terms of $f$ at all the cusps at the same time. On the classical side one must check each cusp separately. On the adelic side a single integral over $N(\mathbb{Q})\backslash N(\mathbb{A})$ does it, because the right translates by $GL_2(\hat{\mathbb{Z}})$ move the cusps, as in the remark after Proposition 1.3.7.

**Example 1.4.15 (the Eisenstein series).** Let $k \ge 4$ be even, and let $E_k = 1 - \frac{2k}{B_k}\sum_{n \ge 1}\sigma_{k-1}(n)q^n$ be the normalized Eisenstein series of level 1, as in Volume 4, Theorem 1.2.11. For $\sigma \in SL_2(\mathbb{Z})$ we have $E_k|_k\sigma = E_k$, so $a_0(E_k|_k\sigma) = 1$. The group $GL_2(\hat{\mathbb{Z}})$ fixes $\phi_{E_k}$, so Proposition 1.4.13 gives
$$\phi_{E_k, N}(\iota_\infty(n(x)a(y)\kappa_\theta)) = y^{k/2}e^{ik\theta}.$$
So $\phi_{E_k}$ is not cuspidal. On the elements $\iota_\infty(a(y))$ with $y \ge 1$, the function $\phi_{E_k} - \phi_{E_k, N}$ is $y^{k/2}(E_k(iy) - 1)$, which decreases exponentially. So the growth of $\phi_{E_k}$ in the cusp is the growth $y^{k/2}$ of its constant term. Exercise 11 computes the constant term on all of $GL_2(\mathbb{A})$: its value at $n\,\mathrm{diag}(t_1, t_2)\,\iota_\infty(\kappa_\theta)\,k_0$ is $|t_1/t_2|_\mathbb{A}^{k/2}e^{ik\theta}$, for $n \in N(\mathbb{A})$, ideles $t_1, t_2$ with positive infinite components, and $k_0 \in GL_2(\hat{\mathbb{Z}})$. This is a vector of an induced representation, and Chapter 2 builds Eisenstein series from such vectors.

**Remark 1.4.16 (cusp forms in the Lean project).** The Lean project defines the cuspidal condition for $GL_n$ over a number field $K$ as `Langlands.HasVanishingConstantTerm`, with an integral over $N_r(K)\backslash N_r(\mathbb{A}_K)$ for each maximal parabolic subgroup. For $n = 2$ and $K = \mathbb{Q}$ this is Definition 1.4.11. The structure `Langlands.IsCuspForm` asks for left invariance under $GL_n(K)$, right invariance under the principal congruence subgroup $K(N)$, a central character, the growth bound $|\phi(g)| \le C|\det g|^s$ and the vanishing of the constant terms. By part 2 of Proposition 1.3.6, Proposition 1.4.10 and Theorem 1.4.14, the lift $\phi_f$ of a cusp form $f \in S_k(N, \chi)$ satisfies these conditions with $s = 0$, apart from the continuity, which is part 5 of Proposition 1.3.6 together with the right invariance under the open subgroup $K_1(N)$. The project does not state this. Its definition has no condition at the infinite place, so it does not see the weight or the holomorphy.
