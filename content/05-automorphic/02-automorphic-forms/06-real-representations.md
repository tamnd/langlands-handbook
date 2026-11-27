---
title: The representations of GL_2(R)
nodes: []
sources: [JL70]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## The representations of $GL_2(\mathbb{R})$

Theorem 2.1.12 and Proposition 2.1.13 classify the irreducible $(\mathfrak{g}, K_\infty)$-modules by their weights and the Casimir eigenvalue. This section realizes them in induced representations and finds the unitary ones. It then identifies the archimedean component of a cusp form: a holomorphic form of weight $k$ gives the discrete series $D_k$, and a Maass form gives a principal series. The sources are [JL70], Chapter I, and [Bum97], Chapter 2.

**Definition 2.6.1 (principal series).** For characters $\chi_1, \chi_2$ of $\mathbb{R}^\times$, write $\chi_i(t) = |t|^{s_i}\mathrm{sgn}(t)^{\epsilon_i}$ with $\epsilon_i \in \{0, 1\}$. The *principal series* $I(\chi_1, \chi_2)$ is the space of the $K_\infty$-finite smooth functions $f$ on $G(\mathbb{R})$ with
$$f\left(\begin{pmatrix} a & b \\ 0 & d \end{pmatrix}g\right) = \chi_1(a)\chi_2(d)\left|\frac{a}{d}\right|^{1/2}f(g),$$
with $G(\mathbb{R})$ acting by right translation $\rho$. Put $s = \frac{1}{2}(s_1 - s_2 + 1)$.

Lean: not formalized

**Proposition 2.6.2 (weights of the principal series).** For each $m \equiv \epsilon_1 + \epsilon_2 \pmod 2$ there is a unique $f_m \in I(\chi_1, \chi_2)$ with $f_m(\kappa_\theta) = e^{im\theta}$, and these functions form a basis. Then $f_m(u(x)\mathrm{diag}(y^{1/2}, y^{-1/2})\kappa_\theta) = y^se^{im\theta}$ and
$$Rf_m = \left(s + \frac{m}{2}\right)f_{m+2}, \qquad Lf_m = \left(s - \frac{m}{2}\right)f_{m-2}, \qquad \rho(\varepsilon)f_m = (-1)^{\epsilon_1}f_{-m}.$$
The center acts by $\chi_1\chi_2$, and $\Delta$ acts by $s(1 - s)$.

Lean: not formalized

*Proof.* By Lemma 2.1.2 a function in $I(\chi_1, \chi_2)$ is determined by its restriction to $SO(2)$. The restriction is any $K$-finite function that satisfies $f(-\kappa_\theta) = \chi_1\chi_2(-1)f(\kappa_\theta)$, since $-1 = \kappa_\pi$ lies in both groups; this gives the parity condition. The value at $u(x)\mathrm{diag}(y^{1/2}, y^{-1/2})$ is $y^{(s_1 - s_2)/2}y^{1/2} = y^s$. The formulas for $R$ and $L$ follow from Lemma 2.1.7, since $y\partial_y$ gives $s$ and $\mp\frac{i}{2}\partial_\theta$ gives $\pm\frac{m}{2}$. For $\varepsilon$, we have $\kappa_\theta\varepsilon = \varepsilon\kappa_{-\theta}$, so $f_m(\kappa_\theta\varepsilon) = \chi_1(-1)e^{-im\theta}$. The value of $\Delta$ follows from (2.1.2): $(LR + \frac{H^2}{4} + \frac{H}{2})f_0 = s(s - 1)f_0$, and then (2.1.1) gives $\Delta f_0 = s(1 - s)f_0$. $\square$

**Theorem 2.6.3 (reducibility).** The $(\mathfrak{g}, K_\infty)$-module $I(\chi_1, \chi_2)$ is irreducible unless $\chi_1\chi_2^{-1}(t) = t^p\,\mathrm{sgn}(t)$ for a nonzero integer $p$. If $\chi_1\chi_2^{-1}(t) = t^{k-1}\mathrm{sgn}(t)$ with $k \ge 2$, so that $s = \frac{k}{2}$, then $I(\chi_1, \chi_2)$ has a unique irreducible submodule $D_k$, spanned by the $f_m$ with $|m| \ge k$, and the quotient is the irreducible module of dimension $k - 1$. For $p = 1 - k$ the roles are reversed: the finite-dimensional module is the submodule.

Lean: not formalized

*Proof.* A nonzero submodule is a sum of weight spaces, by $K$-finiteness, and each weight space is a line. By Proposition 2.6.2 the operators $R$ and $L$ move between neighbouring weights, and the module is irreducible unless $s + \frac{m}{2} = 0$ or $s - \frac{m}{2} = 0$ for an allowed $m$, that is unless $2s \in \mathbb{Z}$ with $2s \equiv \epsilon_1 + \epsilon_2 \pmod 2$. With $2s - 1 = s_1 - s_2 = p$ this says $\chi_1\chi_2^{-1} = |\cdot|^p\mathrm{sgn}^{p + 1}$, which is $t^p\mathrm{sgn}(t)$. For $p = 0$ we get $s = \frac{1}{2}$ and odd weights: $Rf_{-1} = 0$ and $Lf_1 = 0$, so the module splits under $(\mathfrak{g}, SO(2))$ into the weights $m \ge 1$ and $m \le -1$. The element $\varepsilon$ exchanges the two pieces, so the $(\mathfrak{g}, K_\infty)$-module is irreducible. For $s = \frac{k}{2}$ with $k \ge 2$, $Lf_k = 0$ and $Rf_{-k} = 0$, while $Rf_m \ne 0$ for $m \ge k$ and $Lf_m \ne 0$ for $m \le -k$. So the $f_m$ with $|m| \ge k$ span a submodule. It is irreducible, since $\varepsilon$ exchanges the two halves. The quotient has the $k - 1$ weights $1 - k, 3 - k, \dots, k - 1$. The case $p = 1 - k$ is the same with $s = 1 - \frac{k}{2}$. $\square$

**Definition 2.6.4 (discrete series).** For $k \ge 2$ the module $D_k$ of Theorem 2.6.3 is the *discrete series* of weight $k$. As a $(\mathfrak{g}, SO(2))$-module it is $D_k^+ \oplus D_k^-$ of Theorem 2.1.12. For $k = 1$ the irreducible module $I(\mathrm{sgn}, 1)$, the case $p = 0$ with $s = \frac{1}{2}$, is the *limit of discrete series* $D_1$.

Lean: `Langlands.IsDiscreteSeries`

The name comes from the fact that, for $k \ge 2$ and a unitary central character, the matrix coefficients of $D_k$ are square-integrable modulo the center, so $D_k$ occurs discretely in $L^2(G(\mathbb{R}))$.

**Proposition 2.6.5 (unitarity).** Let $V$ be an infinite-dimensional irreducible $(\mathfrak{g}, K_\infty)$-module with a positive definite invariant inner product and Casimir eigenvalue $\lambda = s(1 - s)$. If $V$ has a vector of weight $0$, then $\lambda > 0$, and either $s \in \frac{1}{2} + i\mathbb{R}$ or $0 < s < 1$. The discrete series $D_k$ are unitary.

Lean: not formalized

*Proof.* Invariance means that $H$, $X$ and $Y$ are skew-adjoint, so $R^* = -L$, and the weight spaces are orthogonal. For $v$ of weight $0$, (2.1.2) gives $LRv = s(s - 1)v = -\lambda v$, so $\|Rv\|^2 = -\langle LRv, v\rangle = \lambda\|v\|^2$. Here $Rv \ne 0$, since $V$ is infinite-dimensional and irreducible, so $\lambda > 0$. Since $\lambda$ is real and positive, $s \in \frac{1}{2} + i\mathbb{R}$ or $s$ is real with $0 < s < 1$. For $D_k^+$ define the inner product on the basis $v_k, v_{k+2}, \dots$ by $\|v_k\| = 1$ and $v_{m+2} = Rv_m$. The relation $R^* = -L$ holds if $\|v_{m+2}\|^2 = -\langle LRv_m, v_m\rangle$, and with $s = \frac{k}{2}$ (2.1.2) gives
$$-\left(\frac{k}{2} + \frac{m}{2}\right)\left(\frac{k}{2} - \frac{m}{2} - 1\right) = \frac{(m + k)(m + 2 - k)}{4} > 0 \qquad (m \ge k).$$
So the norms are positive, and the inner product is invariant. $D_k^-$ is the same, and $\varepsilon$ is made unitary by $\|\varepsilon v\| = \|v\|$. $\square$

Conversely the principal series with $s \in \frac{1}{2} + i\mathbb{R}$ are unitary for the $L^2$ inner product on $SO(2)$, and those with $0 < s < 1$ real, the *complementary series*, are unitary for a twisted inner product, [Bum97] Chapter 2. A unitary module is *tempered* if it is a discrete series, a limit of discrete series, or a principal series with $s \in \frac{1}{2} + i\mathbb{R}$.

**Theorem 2.6.6 (the archimedean component of a cusp form).** Let $\pi = \pi_\infty \otimes \pi_f$ be a cuspidal automorphic representation with unitary central character. Then $\pi_\infty$ is unitary and infinite-dimensional. If $\pi$ is generated by $\phi_f$ for a cusp form $f$ of weight $k \ge 2$, then $\pi_\infty \cong D_k$, twisted by a character of the center. If $\pi$ is generated by the adelic form of a Maass cusp form of eigenvalue $\lambda = s(1 - s)$, then $\pi_\infty$ is a principal series with Casimir eigenvalue $\lambda$.

Lean: not formalized

*Proof.* The $L^2$ inner product of Definition 2.3.13 is invariant and positive, and $\pi_\infty$ is infinite-dimensional by Corollary 2.5.5. The vector $\phi_f$ has weight $k$, satisfies $L\phi_f = 0$ by Example 2.1.8, and has $\Delta = \frac{k}{2}(1 - \frac{k}{2})$. By Theorem 2.1.12 the $(\mathfrak{g}, SO(2))$-module that it generates is $D_k^+$, and $\rho(\varepsilon)\phi_f$ generates $D_k^-$, so $\pi_\infty \supseteq D_k$, with equality by irreducibility. For a Maass form the vector has weight $0$ and $\lambda > 0$. It is not finite-dimensional, and the weight-$0$ vector excludes $D_k$. By Theorem 2.6.3 and Proposition 2.1.13, $\pi_\infty$ is an irreducible principal series with the same $\lambda$. $\square$

**Remark 2.6.7 (the Selberg conjecture).** By Proposition 2.6.5 a Maass cusp form of eigenvalue $\lambda$ gives a tempered $\pi_\infty$ if $\lambda \ge \frac{1}{4}$, and a complementary series if $0 < \lambda < \frac{1}{4}$. So Selberg's conjecture $\lambda \ge \frac{1}{4}$, Volume 4, Conjecture 2.6.5, is the Ramanujan conjecture at the real place: the archimedean component of a cuspidal representation of $GL_2$ is tempered. The holomorphic case has no such problem, since $D_k$ is tempered. The weight $k = 1$ gives $D_1$, and by the theorem of Deligne and Serre the newforms of weight $1$ correspond to odd two-dimensional Artin representations.
