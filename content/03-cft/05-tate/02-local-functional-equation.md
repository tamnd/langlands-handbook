---
title: The local functional equation
nodes: []
sources: [CF67, Tat79]
status: checked
drafted_by: writer
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## The local functional equation

This section proves the local functional equation for every local field $K$ and every character $\chi$ of $K^\times$. The method is Tate's. One identity, Lemma 5.2.1, shows that the ratio of $Z(\hat f, \chi^{-1}, 1 - s)$ and $Z(f, \chi, s)$ does not depend on $f$. Then one good function for each $\chi$ gives the ratio and the meromorphic continuation. We fix a nontrivial character $\psi$ of $K$, the self-dual measure $dx$ and Tate's measure $d^\times x$ of Definition 5.1.5. Let $\sigma = \sigma(\chi)$.

### Tate's lemma

**Lemma 5.2.1 (Tate's lemma).** Let $f, g \in \mathcal{S}(K)$. For $-\sigma < \mathrm{Re}(s) < 1 - \sigma$,
$$Z(f, \chi, s) \, Z(\hat g, \chi^{-1}, 1 - s) = Z(\hat f, \chi^{-1}, 1 - s) \, Z(g, \chi, s).$$

Lean: not stated yet

*Proof.* In the strip all four integrals converge absolutely, by Proposition 5.1.9. For $Z(\hat g, \chi^{-1}, 1-s)$ the condition is $\mathrm{Re}(1 - s) > -\sigma(\chi^{-1}) = \sigma$. The left side is the absolutely convergent double integral
$$\int_{K^\times} \int_{K^\times} f(x) \hat g(y) \chi(x y^{-1}) |x|^s |y|^{1-s} \, d^\times x \, d^\times y.$$
For fixed $x$ substitute $y = xt$. The measure $d^\times y$ is invariant, so the double integral is
$$\int_{K^\times} \chi(t)^{-1} |t|^{1-s} \Big( \int_{K^\times} f(x) \hat g(xt) |x| \, d^\times x \Big) d^\times t.$$
By Section 5.1, $|x| \, d^\times x = c_K \, dx$. So the inner integral is
$$c_K \int_K f(x) \hat g(xt) \, dx = c_K \int_K \int_K f(x) g(y) \psi(txy) \, dy \, dx.$$
The function $f(x) g(y)$ is integrable on $K \times K$, so Fubini's theorem applies. The last integral is symmetric in $f$ and $g$. Thus the double integral does not change if we exchange $f$ and $g$. After the exchange it is the right side of the lemma. $\square$

### The $L$-factors and the standard functions

**Definition 5.2.2 (local $L$-factors).** Let $\Gamma_\mathbb{R}(s) = \pi^{-s/2} \Gamma(s/2)$ and $\Gamma_\mathbb{C}(s) = 2 (2\pi)^{-s} \Gamma(s)$. The $L$-factor $L(\chi, s)$ of a character $\chi$ of $K^\times$ is:
1. if $K$ is nonarchimedean, $L(\chi, s) = (1 - \chi(\varpi) q^{-s})^{-1}$ for unramified $\chi$, and $L(\chi, s) = 1$ for ramified $\chi$;
2. if $K = \mathbb{R}$ and $\chi = \mathrm{sgn}^a |\cdot|^t$ with $a \in \{0, 1\}$, $L(\chi, s) = \Gamma_\mathbb{R}(s + t + a)$;
3. if $K = \mathbb{C}$ and $\chi(z) = (z / \sqrt{z \bar z})^n |z|_\mathbb{C}^t$, $L(\chi, s) = \Gamma_\mathbb{C}(s + t + |n|/2)$.

The parameters are unique by Proposition 5.1.7, so the definition makes sense. The nonarchimedean case is the definition of Chapter 4. The $L$-factor has no zeros. It has poles only for $\mathrm{Re}(s) \le -\sigma$: the zero of $1 - \chi(\varpi) q^{-s}$ has $|\chi(\varpi)| q^{-\mathrm{Re}(s)} = 1$, that is, $\mathrm{Re}(s) = -\sigma$, and the poles of $\Gamma$ are at $0, -1, -2, \dots$. The function $1 / L(\chi, s)$ is entire. The duplication formula of $\Gamma$ gives $\Gamma_\mathbb{C}(s) = \Gamma_\mathbb{R}(s) \Gamma_\mathbb{R}(s + 1)$.

The next four propositions give, for each $\chi$, a *standard function* $f_\chi$, a constant $c_\chi \ne 0$ and a function $\varepsilon(\chi, s, \psi)$ with
$$Z(f_\chi, \chi, s) = c_\chi L(\chi, s), \qquad Z(\hat f_\chi, \chi^{-1}, 1 - s) = c_\chi \, \varepsilon(\chi, s, \psi) \, L(\chi^{-1}, 1 - s). \tag{5.2.1}$$
The first identity holds for $\mathrm{Re}(s) > -\sigma$ and the second for $\mathrm{Re}(s) < 1 - \sigma$, where the integrals converge. In Theorem 5.2.7 the function $\varepsilon(\chi, s, \psi)$ becomes the $\varepsilon$-factor.

**Proposition 5.2.3 (unramified characters).** Let $K$ be nonarchimedean, $d = d(\psi)$, and let $\chi$ be unramified. Let $f_\chi = 1_{\mathcal{O}_K}$ and $c_\chi = q^{-d/2}$. Then (5.2.1) holds with
$$\varepsilon(\chi, s, \psi) = \chi(\varpi)^d q^{d(1/2 - s)}.$$

Lean: `Langlands.Tate.NonArchimedean.localFunctionalEquation_unramified`

*Proof.* The first identity is the example after Proposition 5.1.9. By the formula for $\hat 1_{b + \mathfrak{p}^m}$ in Section 5.1, $\hat f_\chi = q^{-d/2} 1_{\mathfrak{p}^{-d}}$. The set $\mathfrak{p}^{-d} \smallsetminus \{0\}$ is the union of the shells $\varpi^k \mathcal{O}_K^\times$ with $k \ge -d$, each of volume $q^{-d/2}$. So
$$Z(\hat f_\chi, \chi^{-1}, 1 - s) = q^{-d/2} \cdot q^{-d/2} \sum_{k \ge -d} \chi(\varpi)^{-k} q^{-k(1-s)} = q^{-d} \chi(\varpi)^d q^{d(1-s)} L(\chi^{-1}, 1 - s).$$
This is $q^{-d/2} \cdot \chi(\varpi)^d q^{d(1/2 - s)} L(\chi^{-1}, 1-s)$. $\square$

For a ramified character $\chi$ with $a(\chi) = n \ge 1$, let
$$G(\chi^{-1}, \psi) = \sum_{u \in (\mathcal{O}_K / \mathfrak{p}^n)^\times} \chi^{-1}(u) \, \psi(\varpi^{-n-d} u), \qquad d = d(\psi).$$
Each term depends only on $u$ modulo $\mathfrak{p}^n$, because $\chi$ is trivial on $U^{(n)}$ and $\psi$ is trivial on $\varpi^{-n-d} \mathfrak{p}^n = \mathfrak{p}^{-d}$. For $d = 0$ this is the Gauss sum of Chapter 4.

**Proposition 5.2.4 (ramified characters).** Let $K$ be nonarchimedean, $d = d(\psi)$, and let $\chi$ be ramified with $a(\chi) = n \ge 1$. Let $f_\chi = 1_{U^{(n)}}$ and $c_\chi = \mathrm{vol}(U^{(n)}, d^\times x) = q^{-d/2} / ((q-1) q^{n-1})$. Then (5.2.1) holds with
$$\varepsilon(\chi, s, \psi) = \chi(\varpi)^{n+d} q^{d/2 - (n+d)s} \, G(\chi^{-1}, \psi).$$

Lean: `Langlands.Tate.NonArchimedean.localFunctionalEquation_ramified`

*Proof.* On $U^{(n)}$ the function $\chi(x) |x|^s$ is 1, so $Z(f_\chi, \chi, s) = c_\chi$. Both $L$-factors are 1. By the formula of Section 5.1 with $b = 1$ and $m = n$,
$$\hat f_\chi(y) = \psi(y) \, q^{-n-d/2} \, 1_{\mathfrak{p}^{-n-d}}(y).$$
We compute $Z(\hat f_\chi, \chi^{-1}, 1 - s)$ shell by shell. On the shell $\varpi^k \mathcal{O}_K^\times$ with $k \ge -n-d$, write $y = \varpi^k u$. The contribution of the shell is $q^{-n-d/2} \chi(\varpi)^{-k} q^{-k(1-s)}$ times
$$I_k = \int_{\mathcal{O}_K^\times} \psi(\varpi^k u) \chi^{-1}(u) \, d^\times u.$$
If $k \ge -d$, then $\psi(\varpi^k u) = 1$, and $I_k = 0$ because $\chi$ is not trivial on $\mathcal{O}_K^\times$. If $-n-d < k < -d$, let $m = -k-d$, so $1 \le m < n$. For $z \in \mathfrak{p}^m$ we have $\varpi^k u z \in \mathfrak{p}^{-d}$. So $u \mapsto \psi(\varpi^k u)$ is constant on the cosets of $U^{(m)}$. The character $\chi^{-1}$ is not trivial on $U^{(m)}$, because $m < a(\chi)$. So the integral over each coset is 0, and $I_k = 0$. Only $k = -n-d$ remains. There the integrand depends only on $u$ modulo $U^{(n)}$, and $I_{-n-d} = c_\chi \, G(\chi^{-1}, \psi)$. Thus
$$Z(\hat f_\chi, \chi^{-1}, 1 - s) = q^{-n-d/2} \chi(\varpi)^{n+d} q^{(n+d)(1-s)} c_\chi \, G(\chi^{-1}, \psi) = c_\chi \, \chi(\varpi)^{n+d} q^{d/2 - (n+d)s} \, G(\chi^{-1}, \psi).$$
This is the claim. $\square$

For $d = 0$ the formula is Proposition 4.3.3. The same computation gives the integral form
$$\varepsilon(\chi, s, \psi) = \int_{\varpi^{-n-d} \mathcal{O}_K^\times} \chi^{-1}(x) |x|^{-s} \psi(x) \, dx,$$
which does not use a choice of $\varpi$, see Exercise 3.

**Proposition 5.2.5 (the real place).** Let $K = \mathbb{R}$, $\psi = \psi_\mathbb{R}$ and $\chi = \mathrm{sgn}^a |\cdot|^t$ with $a \in \{0, 1\}$. Let $f_\chi(x) = x^a e^{-\pi x^2}$ and $c_\chi = 1$. Then (5.2.1) holds with
$$\varepsilon(\chi, s, \psi_\mathbb{R}) = (-i)^a.$$

Lean: `Langlands.Tate.real_local_functional_equation`

*Proof.* The function $e^{-\pi x^2}$ is its own transform. Differentiate the identity $\int e^{-\pi x^2} e^{-2\pi i x y} dx = e^{-\pi y^2}$ with respect to $y$. This gives the transform of $x e^{-\pi x^2}$: it is $\frac{1}{-2\pi i} (-2\pi y) e^{-\pi y^2} = -i y e^{-\pi y^2}$. So $\hat f_\chi = (-i)^a f_\chi$. Next, $f_\chi(x) \chi(x) = |x|^{a+t} e^{-\pi x^2}$, and
$$Z(f_\chi, \chi, s) = 2 \int_0^\infty x^{s + t + a} e^{-\pi x^2} \frac{dx}{x} = \pi^{-(s+t+a)/2} \Gamma\Big(\frac{s+t+a}{2}\Big) = L(\chi, s).$$
The character $\chi^{-1} = \mathrm{sgn}^a |\cdot|^{-t}$ has the same sign exponent. The same computation gives $Z(\hat f_\chi, \chi^{-1}, 1-s) = (-i)^a \Gamma_\mathbb{R}(1 - s - t + a) = (-i)^a L(\chi^{-1}, 1 - s)$. $\square$

**Proposition 5.2.6 (the complex place).** Let $K = \mathbb{C}$, $\psi = \psi_\mathbb{C}$ and $\chi(z) = (z / \sqrt{z \bar z})^n |z|_\mathbb{C}^t$. Let $f_\chi(z) = \bar z^n e^{-2\pi z \bar z}$ if $n \ge 0$, and $f_\chi(z) = z^{|n|} e^{-2\pi z \bar z}$ if $n < 0$. Let $c_\chi = \pi$. Then (5.2.1) holds with
$$\varepsilon(\chi, s, \psi_\mathbb{C}) = (-i)^{|n|}.$$

Lean: `Langlands.Tate.complex_local_functional_equation`

*Proof.* Let $n \ge 0$; the case $n < 0$ is the same with $z$ and $\bar z$ exchanged. Let $g_0(z) = e^{-2\pi z \bar z}$, which is its own transform by Section 5.1. We show by induction that the transform of $\bar z^n g_0$ is $(-i)^n w^n g_0(w)$. We have $\psi_\mathbb{C}(zw) = e^{-2\pi i (zw + \bar z \bar w)}$, so $\partial_{\bar w} \psi_\mathbb{C}(zw) = -2\pi i \bar z \, \psi_\mathbb{C}(zw)$. Differentiation under the integral gives
$$\partial_{\bar w} \big( (\bar z^n g_0)^\wedge \big) = -2\pi i \, (\bar z^{n+1} g_0)^\wedge.$$
If $(\bar z^n g_0)^\wedge(w) = (-i)^n w^n e^{-2\pi w \bar w}$, the left side is $-2\pi (-i)^n w^{n+1} e^{-2\pi w \bar w}$. Division by $-2\pi i$ gives $(\bar z^{n+1} g_0)^\wedge(w) = (-i)^{n+1} w^{n+1} e^{-2\pi w \bar w}$.

Now $f_\chi(z) \chi(z) = |z|^n e^{-2\pi |z|^2} |z|^{2t}$, where $|z| = \sqrt{z \bar z}$. In polar coordinates $2 \, dx \, dy = 2 r \, dr \, d\theta$, and $d^\times z = 2 r^{-1} dr \, d\theta$. With $u = r^2$,
$$Z(f_\chi, \chi, s) = 4\pi \int_0^\infty r^{2(s+t) + n} e^{-2\pi r^2} \frac{dr}{r} = 2\pi \int_0^\infty u^{s + t + n/2} e^{-2\pi u} \frac{du}{u} = \pi \, \Gamma_\mathbb{C}(s + t + n/2).$$
For the dual side, $w^n \chi^{-1}(w) = |w|^n |w|_\mathbb{C}^{-t}$. The same computation gives $Z(\hat f_\chi, \chi^{-1}, 1 - s) = (-i)^n \pi \, \Gamma_\mathbb{C}(1 - s - t + n/2) = (-i)^n \pi \, L(\chi^{-1}, 1 - s)$. $\square$

### The functional equation

**Theorem 5.2.7 (the local functional equation).** Let $K$ be a local field, $\psi$ a nontrivial character of $K$, and $\chi$ a character of $K^\times$ with exponent $\sigma$. If $K$ is archimedean, assume that $\psi$ is the standard character. Let $\varepsilon(\chi, s, \psi)$ be the function of Propositions 5.2.3 to 5.2.6, and let
$$\gamma(\chi, s, \psi) = \varepsilon(\chi, s, \psi) \frac{L(\chi^{-1}, 1 - s)}{L(\chi, s)}.$$
1. For each $f \in \mathcal{S}(K)$ the function $Z(f, \chi, s)$ on $\mathrm{Re}(s) > -\sigma$ extends to a meromorphic function on $\mathbb{C}$, and $Z(f, \chi, s) / L(\chi, s)$ is entire. If $K$ is nonarchimedean, it is a polynomial in $q^s$ and $q^{-s}$.
2. For each $f \in \mathcal{S}(K)$, as meromorphic functions of $s$,
$$Z(\hat f, \chi^{-1}, 1 - s) = \gamma(\chi, s, \psi) \, Z(f, \chi, s).$$
3. The function $\varepsilon(\chi, s, \psi)$ is entire and has no zeros. If $K$ is nonarchimedean, then $\varepsilon(\chi, s, \psi) = \varepsilon(\chi, 1/2, \psi) \, q^{(a(\chi) + d(\psi))(1/2 - s)}$. If $K$ is archimedean, it does not depend on $s$.
4. For all $s$, $\varepsilon(\chi, s, \psi) \, \varepsilon(\chi^{-1}, 1 - s, \psi) = \chi(-1)$.

Lean: not stated yet

*Proof.* Part 3, except the absence of zeros, can be read off from the four propositions. Let $S$ be the strip $-\sigma < \mathrm{Re}(s) < 1 - \sigma$. For $s \in S$ apply Lemma 5.2.1 with $g = f_\chi$, and use (5.2.1). The constant $c_\chi$ cancels, and
$$Z(f, \chi, s) \, \varepsilon(\chi, s, \psi) \, L(\chi^{-1}, 1 - s) = Z(\hat f, \chi^{-1}, 1 - s) \, L(\chi, s), \qquad s \in S. \tag{5.2.2}$$

We prove part 4 on $S$. The strip for $\chi^{-1}$ at the point $1 - s$ is again $S$. Apply (5.2.2) to $\chi^{-1}$, to the function $\hat f$ and to the point $1 - s$. As $\hat{\hat f}(x) = f(-x)$, the substitution $x \mapsto -x$ gives $Z(\hat{\hat f}, \chi, s) = \chi(-1) Z(f, \chi, s)$. So
$$Z(\hat f, \chi^{-1}, 1 - s) \, \varepsilon(\chi^{-1}, 1 - s, \psi) \, L(\chi, s) = \chi(-1) \, Z(f, \chi, s) \, L(\chi^{-1}, 1 - s).$$
Multiply (5.2.2) by $\varepsilon(\chi^{-1}, 1 - s, \psi)$ and compare with this identity. The result is
$$Z(f, \chi, s) \, L(\chi^{-1}, 1 - s) \big( \varepsilon(\chi, s, \psi) \, \varepsilon(\chi^{-1}, 1 - s, \psi) - \chi(-1) \big) = 0.$$
For $f = f_\chi$ the first two factors are $c_\chi L(\chi, s) L(\chi^{-1}, 1-s)$, which is not zero on $S$. So part 4 holds on $S$. Both sides of part 4 are entire functions of $s$ by the four propositions, so part 4 holds everywhere. In particular $\varepsilon(\chi, s, \psi)$ has no zeros, which completes part 3.

For part 1, consider the two functions
$$A(s) = \frac{Z(f, \chi, s)}{L(\chi, s)}, \qquad B(s) = \chi(-1) \, \varepsilon(\chi^{-1}, 1 - s, \psi) \frac{Z(\hat f, \chi^{-1}, 1 - s)}{L(\chi^{-1}, 1 - s)}.$$
The function $A$ is holomorphic on $\mathrm{Re}(s) > -\sigma$, because $Z(f, \chi, s)$ is holomorphic there and $1 / L$ is entire. In the same way $B$ is holomorphic on $\mathrm{Re}(s) < 1 - \sigma$. By (5.2.2) and part 4, $A = B$ on $S$. The two half planes cover $\mathbb{C}$, and their intersection $S$ is connected, so $A$ and $B$ glue to an entire function. Thus $Z(f, \chi, s) = L(\chi, s) A(s)$ is meromorphic on $\mathbb{C}$, and $Z / L$ is entire. Part 2 holds on $S$ by (5.2.2), so it holds on $\mathbb{C}$ by the uniqueness of meromorphic continuation.

It remains to prove the last claim of part 1. Let $K$ be nonarchimedean. Choose $N$ such that $f$ is constant on $\mathfrak{p}^N$. The function $g = f - f(0) 1_{\mathfrak{p}^N}$ vanishes on $\mathfrak{p}^N$ and outside some $\mathfrak{p}^{-M}$. So $Z(g, \chi, s)$ is a finite sum over the shells $\varpi^k \mathcal{O}_K^\times$ with $-M \le k < N$. The contribution of each shell is a constant times $q^{-ks}$. Next, $Z(1_{\mathfrak{p}^N}, \chi, s) = \chi(\varpi)^N q^{-Ns} q^{-d/2} L(\chi, s)$ if $\chi$ is unramified, and it is 0 if $\chi$ is ramified, because then the integral of $\chi$ over each shell is 0. Thus $Z(f, \chi, s) = P + f(0) \, C q^{-Ns} L(\chi, s)$, where $P$ is a polynomial in $q^s$ and $q^{-s}$ and $C$ is a constant. Division by $L(\chi, s)$ gives a polynomial in $q^s$ and $q^{-s}$, because $1 / L(\chi, s)$ is one. $\square$

For a nonarchimedean $K$ and $d(\psi) = 0$ the theorem is Theorem 4.3.1, with $m = a(\chi)$. Part 4 is Proposition 4.3.4. The theorem holds for every nontrivial $\psi$ on an archimedean field too, with the factor of Proposition 5.2.10 below. In summary, the $\varepsilon$-factors for the standard situation are:
1. $\chi(\varpi)^d q^{d(1/2 - s)}$ for unramified $\chi$ on a nonarchimedean field, with $d = d(\psi)$;
2. $\chi(\varpi)^{n+d} q^{d/2 - (n+d)s} G(\chi^{-1}, \psi)$ for ramified $\chi$ with $a(\chi) = n$;
3. $(-i)^a$ for $\chi = \mathrm{sgn}^a |\cdot|^t$ on $\mathbb{R}$, with $\psi_\mathbb{R}$;
4. $(-i)^{|n|}$ for $\chi = (z / \sqrt{z \bar z})^n |\cdot|_\mathbb{C}^t$ on $\mathbb{C}$, with $\psi_\mathbb{C}$.

**Remark 5.2.8 (Tate's factor $\rho$).** Tate writes the local functional equation as $\zeta(f, c) = \rho(c) \zeta(\hat f, \hat c)$, where $c = \chi |\cdot|^s$ and $\hat c = |\cdot| c^{-1} = \chi^{-1} |\cdot|^{1 - s}$. See [CF67], Chapter XV, Theorem 2.4.1. Thus $\rho(\chi |\cdot|^s) = \gamma(\chi, s, \psi)^{-1}$. Tate computes $\rho$ for each type of character in his Section 2.5, without the splitting into $L$ and $\varepsilon$. For example, for $K = \mathbb{R}$ and $\chi = 1$ he finds $\rho(|\cdot|^s) = 2^{1-s} \pi^{-s} \cos(\pi s / 2) \Gamma(s)$. The duplication formula and the reflection formula of $\Gamma$ show that this equals $\Gamma_\mathbb{R}(s) / \Gamma_\mathbb{R}(1 - s)$, which is $\gamma(1, s, \psi_\mathbb{R})^{-1}$. The splitting $\gamma = \varepsilon L(\chi^{-1}, 1-s) / L(\chi, s)$ is in [Tat79], Section 3.

### Consequences

**Corollary 5.2.9 (the absolute value of $\varepsilon$).** Let $\chi = \chi_0 |\cdot|^\sigma$ with $\chi_0$ unitary. Then $\varepsilon(\chi, s, \psi) = \varepsilon(\chi_0, s + \sigma, \psi)$, and $|\varepsilon(\chi_0, 1/2, \psi)| = 1$.

Lean: not stated yet

*Proof.* The first claim holds because $Z(f, \chi, s) = Z(f, \chi_0, s + \sigma)$, $Z(\hat f, \chi^{-1}, 1 - s) = Z(\hat f, \chi_0^{-1}, 1 - (s + \sigma))$, and the same shift relates the $L$-factors. For the second claim let $\chi = \chi_0$ and $s = 1/2$. This point lies in the strip $S$ of the proof above, so all the integrals converge. The complex conjugate of $\psi$ is $\psi_{-1}$, and $\bar\chi = \chi^{-1}$. For $g = \bar f$ this gives $\overline{\hat f(y)} = \hat g(-y)$, so
$$\overline{Z(\hat f, \chi^{-1}, 1/2)} = \chi(-1) Z(\hat g, \chi, 1/2), \qquad \overline{Z(f, \chi, 1/2)} = Z(g, \chi^{-1}, 1/2).$$
The conjugate of the functional equation for $f$ and $\chi$ at $s = 1/2$ is thus $\chi(-1) Z(\hat g, \chi, 1/2) = \overline{\gamma(\chi, 1/2, \psi)} \, Z(g, \chi^{-1}, 1/2)$. The functional equation for $g$ and $\chi^{-1}$ at $s = 1/2$ gives $Z(\hat g, \chi, 1/2) = \gamma(\chi^{-1}, 1/2, \psi) Z(g, \chi^{-1}, 1/2)$. Choose $f$ with $Z(g, \chi^{-1}, 1/2) \ne 0$. Then $\overline{\gamma(\chi, 1/2, \psi)} = \chi(-1) \gamma(\chi^{-1}, 1/2, \psi)$. The conjugate of $L(\chi, 1/2)$ is $L(\chi^{-1}, 1/2)$, so the $L$-factors cancel, and $\overline{\varepsilon(\chi, 1/2, \psi)} = \chi(-1) \varepsilon(\chi^{-1}, 1/2, \psi)$. Part 4 of Theorem 5.2.7 at $s = 1/2$ now gives $|\varepsilon(\chi, 1/2, \psi)|^2 = \chi(-1)^2 = 1$. $\square$

**Proposition 5.2.10 (change of $\psi$).** Let $a \in K^\times$, and use the self-dual measure $|a|^{1/2} dx$ for $\psi_a$. Then
$$\varepsilon(\chi, s, \psi_a) = \chi(a) |a|^{s - 1/2} \varepsilon(\chi, s, \psi).$$
Here $\varepsilon(\chi, s, \psi_a)$ is defined by part 2 of Theorem 5.2.7 for $\psi_a$, that is, as $\gamma(\chi, s, \psi_a) L(\chi, s) / L(\chi^{-1}, 1-s)$.

Lean: not stated yet

*Proof.* The factor $\gamma$ is a ratio of two zeta integrals for the same multiplicative measure, so we may use the same $d^\times x$ for $\psi$ and $\psi_a$. Let $\mathcal{F}_a f$ be the transform for $\psi_a$ and $|a|^{1/2} dx$. Then $\mathcal{F}_a f(y) = |a|^{1/2} \hat f(ay)$. The substitution $u = ay$ gives
$$Z(\mathcal{F}_a f, \chi^{-1}, 1 - s) = |a|^{1/2} \int_{K^\times} \hat f(ay) \chi^{-1}(y) |y|^{1-s} d^\times y = |a|^{1/2} \chi(a) |a|^{s - 1} Z(\hat f, \chi^{-1}, 1 - s).$$
So $\gamma(\chi, s, \psi_a) = \chi(a) |a|^{s - 1/2} \gamma(\chi, s, \psi)$. The $L$-factors do not depend on $\psi$. $\square$

This proves Remark 4.3.5. It also defines $\varepsilon(\chi, s, \psi)$ for every nontrivial $\psi$ on $\mathbb{R}$ and $\mathbb{C}$, because each such $\psi$ is $(\psi_\mathbb{R})_a$ or $(\psi_\mathbb{C})_a$ by Proposition 5.1.2. Parts 1, 2 and 4 of Theorem 5.2.7 then hold for every $\psi$, and the form of $\varepsilon$ in part 3 holds for every $\psi$ too. For a nonarchimedean field the proposition is consistent with Propositions 5.2.3 and 5.2.4, because $d(\psi_a) = d(\psi) + v(a)$.

**Example 5.2.11 (the sign at a real place).** Let $K = \mathbb{R}$ and $\psi(x) = e^{2\pi i x}$. Many texts use this character. It is $(\psi_\mathbb{R})_{-1}$, so Proposition 5.2.10 gives
$$\varepsilon(\mathrm{sgn}^a |\cdot|^t, s, \psi) = \mathrm{sgn}(-1)^a (-i)^a = i^a.$$
For $a = 1$ part 4 of Theorem 5.2.7 reads $i \cdot i = -1 = \mathrm{sgn}(-1)$. The sign of a local $\varepsilon$-factor thus depends on the choice of $\psi$. For the global character, a change from $\psi$ to $\psi_{-1}$ changes the sign at all places at once. Proposition 5.5.2 shows that the global $\varepsilon$-factor does not change.

**Remark 5.2.12 (the Lean proof and its limits).** The Lean project tamnd/langlands-lean proves Propositions 5.2.3 to 5.2.6 in the folder `Langlands/Tate`. The nonarchimedean theorems are in the files `NonArchimedeanLocalEquation.lean` and `NonArchimedeanGauss.lean`, and the archimedean theorems are in `ArchimedeanFourier.lean`. These theorems are not on the map, so their lines have no `Node:`. They are weaker than the propositions in the following ways.
1. The nonarchimedean field is the completion $K_v$ of a number field at a finite place $v$, not an arbitrary nonarchimedean local field. So the Lean theorems do not cover the fields $\mathbb{F}_q((t))$.
2. The additive character is an abstract character $\psi$ of $K_v$ with conductor exponent $d$: it is trivial on the ball $\{|x|_v \le q^d\} = \mathfrak{p}^{-d}$ and not trivial on $\mathfrak{p}^{-d-1}$. So $d$ is the exponent $d(\psi)$ of Definition 5.1.1. The proofs use only these two properties, and they do not use the standard character of Section 5.1.
3. The additive measure is the Haar measure $dx$ with $\mathrm{vol}(\mathcal{O}_v) = 1$, not the self-dual measure, and $d^\times x = (1 - q^{-1})^{-1} |x|_v^{-1} dx$. The multiplicative measure cancels in the ratio of the two zeta integrals, but the additive measure enters the transform $\hat f$. Our $dx$ is $q^{d/2}$ times the self-dual measure, so the Lean $\varepsilon$-factors are $q^{d/2}$ times the factors of Propositions 5.2.3 and 5.2.4. For an unramified $\chi$, `Langlands.Tate.NonArchimedean.epsilonUnramified_eq` gives $\varepsilon = \chi(\varpi)^d q^{d(1/2 - s)} \cdot q^{d/2}$. For a ramified $\chi$ with $a(\chi) = n$, the Lean factor is $\chi(c)^{-1} |c|_v^{1-s} G(\chi^{-1}, \psi, c)$ with $|c|_v = q^{n+d}$ and the Gauss integral $G(\chi^{-1}, \psi, c) = \int_{\mathcal{O}_v^\times} \chi^{-1}(u) \psi(cu) \, du$. For $c = \varpi^{-n-d}$ this integral is $q^{-n} G(\chi^{-1}, \psi)$, and the Lean factor is again $q^{d/2}$ times the factor of Proposition 5.2.4.
4. The theorem `Langlands.Tate.NonArchimedean.norm_gaussSum_sq` gives $|G(\chi, \psi, c)|^2 = q^{-a(\chi)}$ for $|c|_v = q^{a(\chi) + d}$, and `Langlands.Tate.NonArchimedean.gaussSum_mul_gaussSum_inv` gives $G(\chi, \psi, c) \, G(\chi^{-1}, \psi, -c) = q^{-a(\chi)}$. For the finite sum the first identity is $|G(\chi^{-1}, \psi)|^2 = q^n$. For a unitary ramified $\chi$ it is the equality $|\varepsilon(\chi, 1/2, \psi)| = 1$ of Corollary 5.2.9, and the second identity is part 4 of Theorem 5.2.7 for a ramified $\chi$. In both cases the Lean form carries the extra factor of item 3: $|\varepsilon| = q^{d/2}$, and the product of the two factors is $\chi(-1) q^d$. The theorem `Langlands.Tate.NonArchimedean.epsilonRamified_ne_zero` says that the ramified factor is not zero.
5. The test functions are only the standard functions $1_{\mathcal{O}_v}$, $1_{U^{(n)}}$, $x^a e^{-\pi x^2}$ and $\bar z^n e^{-2\pi z \bar z}$ or $z^{|n|} e^{-2\pi z \bar z}$. Tate's lemma 5.2.1 is not in Lean. So the Lean project does not prove the functional equation for a general $f \in \mathcal{S}(K)$, and it does not prove that $\varepsilon$ is independent of $f$. Parts 1 and 4 of Theorem 5.2.7, and the meromorphic continuation, are not in Lean either.
6. The Lean identities hold only in a region of convergence. For an unramified $\chi$ the hypotheses are $|\chi(\varpi)| < q^{\mathrm{Re}(s)}$ and $|\chi^{-1}(\varpi)| < q^{\mathrm{Re}(1-s)}$, that is $s$ in the strip $-\sigma < \mathrm{Re}(s) < 1 - \sigma$, and the equation is multiplied out: $Z(\hat f, \chi^{-1}, 1 - s) L(\chi, s) = \varepsilon \, L(\chi^{-1}, 1 - s) \, Z(f, \chi, s)$. For a ramified $\chi$ the hypothesis is $|\chi^{-1}(\varpi)| < q^{\mathrm{Re}(1-s)}$. Outside this region the Lean integral is the Bochner integral of a function that is not integrable. By convention it is $0$, and the formula is false as stated there. At the real and the complex places the hypothesis is $0 < \mathrm{Re}(s + t) < 1$, the same strip.
7. At the archimedean places the Lean conventions are those of this section: $\psi_\mathbb{R}(x) = e^{-2\pi i x}$, $\psi_\mathbb{C} = \psi_\mathbb{R} \circ \mathrm{Tr}_{\mathbb{C}/\mathbb{R}}$, and the self-dual measures $dx$ and $2 \, dx \, dy$. So the root numbers `Langlands.Tate.realRootNumber` and `Langlands.Tate.complexRootNumber` are exactly $(-i)^a$ and $(-i)^{|n|}$. The Lean theorems treat only these standard characters, not the characters $(\psi_\mathbb{R})_a$ of Proposition 5.2.10.

### Ramified places and finite Gauss sums

This subsection returns to a ramified character at a nonarchimedean place. Proposition 5.2.4 used a finite Gauss sum, and Remark 5.2.12 used an integral over $\mathcal{O}_K^\times$. Here we prove that the two agree, we prove $|\tau|^2 = q^{a(\chi)}$ for the finite sum, and we explain why the $L$-factor of a ramified character is 1. Then we give the $\varepsilon$-factor of the test function $1_{U^{(a)}}$ with both normalizations of the measure. The Lean proofs are in the file `Langlands/Tate/LocalRamified.lean`, which uses the Gauss integral and the test function of the files of Remark 5.2.12. In this subsection $K$ is nonarchimedean, with ring of integers $\mathcal{O}_K$, maximal ideal $\mathfrak{p}$, uniformizer $\varpi$ and residue field of order $q$. Let $U^{(0)} = \mathcal{O}_K^\times$ and $U^{(m)} = 1 + \mathfrak{p}^m$ for $m \ge 1$. We fix $\psi$ with exponent $d = d(\psi)$, so $\psi$ is trivial on $\{|x| \le q^d\} = \mathfrak{p}^{-d}$ and not on $\mathfrak{p}^{-d-1}$. Two Haar measures on $K$ occur. The measure $du$ has $\mathrm{vol}(\mathcal{O}_K, du) = 1$; the Lean project uses it. The measure $dx = q^{-d/2} du$ is self-dual for $\psi$ by Proposition 5.1.4.

**Proposition 5.2.13 (the conductor exponent).** Let $\chi$ be a character of $K^\times$. Then $\chi$ is trivial on $U^{(m)}$ for some $m \ge 0$, so the conductor exponent $a(\chi)$ of Definition 4.1.3 exists. If $a = a(\chi) \ge 1$, then $\chi$ is trivial on $U^{(a)}$ and not trivial on $U^{(a-1)}$. Let $F$ be a number field, $v$ a finite place and $\chi$ a Hecke character of $F$. Then $a(\chi_v) \ge 1$ if and only if $\chi$ is ramified at $v$.

Lean: `Langlands.Tate.NonArchimedean.exists_isTrivialOnHigherUnits`, `Langlands.Tate.NonArchimedean.conductorExponent_ne_zero`, `Langlands.Tate.NonArchimedean.not_isTrivialOnHigherUnits_conductorExponent_sub_one`

*Proof.* Let $D = \{z \in \mathbb{C} : |z - 1| < 1\}$. The set $\chi^{-1}(D)$ is an open neighbourhood of 1 in $K^\times$, so it contains some $U^{(m)}$, because these groups form a basis of neighbourhoods of 1. The image $\chi(U^{(m)})$ is a subgroup of $\mathbb{C}^\times$ in $D$. Let $z$ be in this subgroup. All powers $z^n$ with $n \in \mathbb{Z}$ lie in $D$, so they are bounded, and so are the powers of $z^{-1}$. Thus $|z| = 1$, and $z = e^{i\theta}$ with $-\pi < \theta \le \pi$. If $\theta \ne 0$, some multiple $n\theta$ lies in $[\pi/2, 3\pi/2]$ modulo $2\pi$, and then $|z^n - 1| \ge \sqrt 2$. So $z = 1$, and $\chi$ is trivial on $U^{(m)}$. The second claim is the minimality of $a(\chi)$. For the last claim, $\chi_v$ is unramified if and only if it is trivial on $U^{(0)}$, that is, $a(\chi_v) = 0$. $\square$

In Lean, the conductor exponent of a Hecke character at $v$ is `Langlands.HeckeCharacter.conductorExponent`. Its existence uses the continuity of $\chi$ on the ideles, as in the proof above.

**Lemma 5.2.14 (the finite ring $\mathcal{O}_K / \mathfrak{p}^m$).** Let $m \ge 1$.
1. The ring $\mathcal{O}_K / \mathfrak{p}^m$ is finite of order $q^m$.
2. The class of $x \in \mathcal{O}_K$ is a unit of $\mathcal{O}_K / \mathfrak{p}^m$ if and only if $|x| = 1$. Thus $(\mathcal{O}_K / \mathfrak{p}^m)^\times = \mathcal{O}_K^\times / U^{(m)}$, and its order is $(q - 1) q^{m-1}$.
3. The group $\mathcal{O}_K^\times$ is the disjoint union of the balls $u + \mathfrak{p}^m = u U^{(m)}$, one for each class $u \in (\mathcal{O}_K / \mathfrak{p}^m)^\times$.

Lean: `Langlands.Tate.NonArchimedean.ResidueRing`, `Langlands.Tate.NonArchimedean.sphere_eq_iUnion`, `Langlands.Tate.NonArchimedean.pairwise_disjoint_closedBall_rep`

*Proof.* Multiplication by $\varpi^i$ gives an isomorphism $\mathcal{O}_K / \mathfrak{p} \to \mathfrak{p}^i / \mathfrak{p}^{i+1}$ of groups. The filtration $\mathcal{O}_K \supset \mathfrak{p} \supset \dots \supset \mathfrak{p}^m$ has $m$ steps of order $q$, which gives part 1. For part 2, if $|x| = 1$, then $x^{-1} \in \mathcal{O}_K$ and the class of $x^{-1}$ is an inverse. Conversely, if $xy \equiv 1$ modulo $\mathfrak{p}^m$ for some $y \in \mathcal{O}_K$, then $|xy - 1| < 1$, so $|xy| = 1$ by the ultrametric inequality. As $|y| \le 1$, this gives $|x| = 1$. The kernel of $\mathcal{O}_K^\times \to (\mathcal{O}_K / \mathfrak{p}^m)^\times$ is $U^{(m)}$. The units are the complement of $\mathfrak{p} / \mathfrak{p}^m$, which has $q^{m-1}$ elements, so their number is $q^m - q^{m-1}$. Part 3 restates part 2: two units have the same class if and only if they lie in the same ball $u + \mathfrak{p}^m$, and $u + \mathfrak{p}^m = u(1 + u^{-1}\mathfrak{p}^m) = u U^{(m)}$. $\square$

The Lean proof of part 1 is different. It uses that $\mathcal{O}_K$ is compact and that $\mathfrak{p}^m$ is open, so the quotient is finite. It does not compute the order. Lean represents a class $u$ by a chosen element `Langlands.Tate.NonArchimedean.rep` of $\mathcal{O}_K$. Below, a sum over $(\mathcal{O}_K / \mathfrak{p}^m)^\times$ means a sum over a set of representatives in $\mathcal{O}_K^\times$, and each summand will be independent of the choice.

**Lemma 5.2.15 (integrals over the units as finite sums).** Let $m \ge 1$, and let $g : \mathcal{O}_K^\times \to \mathbb{C}$ be constant on each ball $u + \mathfrak{p}^m$. Then
$$\int_{\mathcal{O}_K^\times} g(u) \, du = q^{-m} \sum_{u \in (\mathcal{O}_K / \mathfrak{p}^m)^\times} g(u).$$

Lean: `Langlands.Tate.NonArchimedean.setIntegral_sphere_eq_sum`

*Proof.* By part 3 of Lemma 5.2.14 the integral is the sum of the integrals over the balls $u + \mathfrak{p}^m$. On each ball $g$ is the constant $g(u)$, and the ball has measure $\mathrm{vol}(\mathfrak{p}^m, du) = q^{-m}$, by translation invariance. $\square$

**Definition 5.2.16 (Gauss sums).** Let $m \ge 1$, let $\chi$ be a character of $K^\times$ that is trivial on $U^{(m)}$, and let $c \in K$ with $|c| \le q^{m+d}$. The *finite Gauss sum* and the *Gauss integral* are
$$\tau_m(\chi, \psi, c) = \sum_{u \in (\mathcal{O}_K / \mathfrak{p}^m)^\times} \chi(u) \psi(cu), \qquad G(\chi, \psi, c) = \int_{\mathcal{O}_K^\times} \chi(u) \psi(cu) \, du.$$
If $a(\chi) = a \ge 1$, $m = a$ and $|c| = q^{a+d}$, we write $\tau(\chi, \psi, c)$ for $\tau_a(\chi, \psi, c)$.

Lean: `Langlands.Tate.NonArchimedean.gaussSumFinite`, `Langlands.Tate.NonArchimedean.gaussSum`, `Langlands.Tate.NonArchimedean.gaussSumFinite_eq_sum_of_mk`

The summand $\chi(u) \psi(cu)$ depends only on the class of $u$. Let $u' = u + z$ with $u \in \mathcal{O}_K^\times$ and $z \in \mathfrak{p}^m$. Then $u'/u \in U^{(m)}$, so $\chi(u') = \chi(u)$. Also $|cz| \le q^{m+d} q^{-m} = q^d$, so $\psi(cu') = \psi(cu) \psi(cz) = \psi(cu)$. The Gauss sum of Proposition 5.2.4 is $G(\chi^{-1}, \psi) = \tau(\chi^{-1}, \psi, \varpi^{-n-d})$ with $n = a(\chi)$. The integral with three arguments is the one of Remark 5.2.12. For a unit $w$, the substitution $u \mapsto w^{-1} u$ gives
$$\tau_m(\chi, \psi, cw) = \chi(w)^{-1} \tau_m(\chi, \psi, c). \tag{5.2.3}$$
So $|\tau(\chi, \psi, c)|$ depends only on $|c|$. The same substitution in the integral gives $G(\chi, \psi, c) = \chi(w) G(\chi, \psi, cw)$, which is `Langlands.Tate.NonArchimedean.gaussSum_eq_mul`.

**Proposition 5.2.17 (the integral and the sum).** Under the hypotheses of Definition 5.2.16,
$$G(\chi, \psi, c) = q^{-m} \, \tau_m(\chi, \psi, c).$$

Lean: `Langlands.Tate.NonArchimedean.gaussSum_eq_gaussSumFinite`

*Proof.* The function $u \mapsto \chi(u) \psi(cu)$ is constant on the balls $u + \mathfrak{p}^m$, by the remark after Definition 5.2.16. Lemma 5.2.15 gives the claim. $\square$

**Lemma 5.2.18 (orthogonality).** Let $m \ge 1$, let $\chi$ be trivial on $U^{(m)}$, and let $H$ be a subgroup of $(\mathcal{O}_K / \mathfrak{p}^m)^\times$ such that $\chi$ is not trivial on $H$. Then $\sum_{u \in H} \chi(u) = 0$. In particular, if $\chi$ is ramified, then $\sum_{u \in (\mathcal{O}_K / \mathfrak{p}^m)^\times} \chi(u) = 0$.

Lean: `Langlands.Tate.NonArchimedean.sum_charExt_rep_eq_zero`, `Langlands.Tate.NonArchimedean.residueChar`

*Proof.* By Lemma 5.2.14, $\chi$ induces a character $\bar\chi$ of the finite group $(\mathcal{O}_K / \mathfrak{p}^m)^\times$. Choose $h \in H$ with $\bar\chi(h) \ne 1$. The map $u \mapsto hu$ is a bijection of $H$, so the sum $S$ satisfies $S = \bar\chi(h) S$. Thus $S = 0$. For the second claim take $H$ equal to the whole group. $\bar\chi$ is not trivial on it, because $\chi$ is not trivial on $\mathcal{O}_K^\times$. $\square$

For a Hecke character ramified at $v$, the second claim with $m = a(\chi_v)$ is `Langlands.Tate.NonArchimedean.sum_finiteComponent_eq_zero`.

**Theorem 5.2.19 (the absolute value of a Gauss sum).** Let $\chi$ be a character of $K^\times$ with $a = a(\chi) \ge 1$, and let $c \in K$ with $|c| = q^{a+d}$. Then
$$|\tau(\chi, \psi, c)|^2 = q^a, \qquad \tau(\chi, \psi, c) \, \tau(\chi^{-1}, \psi, -c) = q^a.$$
Equivalently, $|G(\chi, \psi, c)|^2 = q^{-a}$ and $G(\chi, \psi, c) \, G(\chi^{-1}, \psi, -c) = q^{-a}$.

Lean: `Langlands.Tate.NonArchimedean.norm_gaussSumFinite_sq`, `Langlands.Tate.NonArchimedean.gaussSumFinite_mul_gaussSumFinite_inv`, `Langlands.Tate.NonArchimedean.norm_gaussSumFinite_uniformizer_sq`, `Langlands.Tate.NonArchimedean.norm_gaussSumFinite_finiteComponent_sq`

*Proof.* Let $R = \mathcal{O}_K / \mathfrak{p}^a$. First we compute, for $x \in \mathcal{O}_K$, the sum
$$S(x) = \sum_{w \in R^\times} \psi(cwx).$$
The map $\lambda_x : w \mapsto \psi(cxw)$ is a character of the additive group $R$, because $|cxz| \le q^d$ for $z \in \mathfrak{p}^a$. For each $k \in \mathbb{Z}$, the character $\psi$ is trivial on $\mathfrak{p}^k$ if and only if $k \ge -d$, by Definition 5.1.1. So $\lambda_x$ is trivial on $\mathfrak{p}^j / \mathfrak{p}^a$ if and only if $\psi$ is trivial on $cx\mathfrak{p}^j$, that is, if and only if $x = 0$ or $v(x) - a - d + j \ge -d$. This condition is $x \in \mathfrak{p}^{a-j}$. The sum of a character over a finite group is the order of the group if the character is trivial, and $0$ otherwise. Apply this to $R$ (with $j = 0$) and to the subgroup $\mathfrak{p} / \mathfrak{p}^a$ of the nonunits (with $j = 1$), which has order $q^{a-1}$. The difference of the two sums is
$$S(x) = q^a \, 1_{\mathfrak{p}^a}(x) - q^{a-1} \, 1_{\mathfrak{p}^{a-1}}(x).$$

Next we expand $|\tau|^2$. The group $\chi(\mathcal{O}_K^\times)$ is a compact subgroup of $\mathbb{C}^\times$, so it lies in the unit circle, and $\overline{\chi(w)} = \chi(w)^{-1}$ for $w \in \mathcal{O}_K^\times$. Also $\overline{\psi(y)} = \psi(-y)$. Thus
$$|\tau(\chi, \psi, c)|^2 = \sum_{u, w \in R^\times} \chi(u w^{-1}) \psi(c(u - w)).$$
For fixed $w$, substitute $u = tw$. As $t$ runs over $R^\times$, so does $u$. This gives
$$|\tau(\chi, \psi, c)|^2 = \sum_{t \in R^\times} \chi(t) \sum_{w \in R^\times} \psi(cw(t - 1)) = \sum_{t \in R^\times} \chi(t) S(t - 1) = q^a \sum_{t \in H_a} \chi(t) - q^{a-1} \sum_{t \in H_{a-1}} \chi(t),$$
where $H_j$ is the set of $t \in R^\times$ with $t \equiv 1$ modulo $\mathfrak{p}^j$. The set $H_a$ is $\{1\}$, so the first sum is $1$. The set $H_{a-1}$ is the image of $U^{(a-1)}$ in $R^\times$. If $a = 1$, this is all of $R^\times$, the image of $U^{(0)} = \mathcal{O}_K^\times$. The character $\chi$ is not trivial on $U^{(a-1)}$, by Proposition 5.2.13, so the second sum is $0$ by Lemma 5.2.18. Hence $|\tau|^2 = q^a$. The conjugate of $\tau(\chi, \psi, c)$ is $\sum_u \chi^{-1}(u) \psi(-cu) = \tau(\chi^{-1}, \psi, -c)$, which gives the product formula. The statements on $G$ follow by Proposition 5.2.17. $\square$

The Lean proof takes the other route. It proves the identities for $G$ first, as `Langlands.Tate.NonArchimedean.norm_gaussSum_sq` and `Langlands.Tate.NonArchimedean.gaussSum_mul_gaussSum_inv`, by the same substitution in a double integral over $\mathcal{O}_K^\times \times \mathcal{O}_K^\times$. The inner integral is $\int_{\mathcal{O}_K^\times} \psi(cw(t-1)) \, dw = 1_{U^{(a)}}(t) - q^{-1} 1_{U^{(a-1)}}(t)$, which is $q^{-a} S(t - 1)$. Then it applies Proposition 5.2.17. The special case $c = \varpi^{-(a+d)}$ is `norm_gaussSumFinite_uniformizer_sq`. The theorem `norm_gaussSumFinite_finiteComponent_sq` is the case of the local component $\chi_v$ of a Hecke character ramified at $v$, with $a$ the Lean conductor exponent.

**Proposition 5.2.20 (vanishing for ramified characters).** Let $\chi$ be ramified, and let $s \in \mathbb{C}$.
1. For each $k \in \mathbb{Z}$, $\int_{\varpi^k \mathcal{O}_K^\times} \chi(x) |x|^s \, d^\times x = 0$.
2. Let $f \in \mathcal{S}(K)$ with $f(ux) = f(x)$ for all $u \in \mathcal{O}_K^\times$ and $x \in K$. Then $Z(f, \chi, s) = 0$ for $\mathrm{Re}(s) > -\sigma(\chi)$.

Lean: `Langlands.Tate.NonArchimedean.setIntegral_sphere_charExt_of_ramified`, `Langlands.Tate.NonArchimedean.zetaIntegral_eq_zero_of_ramified`

*Proof.* Choose $w \in \mathcal{O}_K^\times$ with $\chi(w) \ne 1$. Let $h(x) = f(x) \chi(x) |x|^s$, where $f = 1_{\varpi^k \mathcal{O}_K^\times}$ in part 1. In both parts $f(wx) = f(x)$, and so $h(wx) = \chi(w) h(x)$. The measure $d^\times x$ is invariant under $x \mapsto wx$, and the integral converges absolutely. Thus $\int h \, d^\times x = \chi(w) \int h \, d^\times x$, and the integral is $0$. $\square$

The functions of part 2 include $1_{\mathcal{O}_K}$ and all $1_{\mathfrak{p}^m}$. So the test function of Proposition 5.2.3 gives $Z = 0$ for a ramified character, and a ramified character needs a test function that is not invariant under the units, such as $1_{U^{(a)}}$. In Lean, the hypothesis on $\chi$ is only that it is not trivial on $\mathcal{O}_K^\times$, and there is no hypothesis on $s$. If the integrand is not integrable, the Lean integral is $0$ by convention, so the statement still holds.

**Corollary 5.2.21 (the local factor at a ramified place).** Let $\chi$ be ramified with $a(\chi) = a$, and let $\sigma = \sigma(\chi)$. For each $f \in \mathcal{S}(K)$, the function $Z(f, \chi, s)$ on $\mathrm{Re}(s) > -\sigma$ is a Laurent polynomial in $q^{-s}$. Each Laurent polynomial in $q^{-s}$ is $Z(f, \chi, s)$ for some $f \in \mathcal{S}(K)$. In particular, no zeta integral of $\chi$ has a pole, and $L(\chi, s) = 1$. For a Hecke character $\chi$ ramified at $v$, the local factor of $L(s, \chi)$ at $v$ is $1$.

Lean: `Langlands.Tate.NonArchimedean.localFactor_eq_one_of_not_isUnramifiedAt`

*Proof.* Let $f \in \mathcal{S}(K)$. As in the proof of part 1 of Theorem 5.2.7, choose $N$ with $f$ constant on $\mathfrak{p}^N$, and write $f = f(0) 1_{\mathfrak{p}^N} + g$. The integral $Z(g, \chi, s)$ is a finite sum over shells, and it is a Laurent polynomial in $q^{-s}$. By Proposition 5.2.20, $Z(1_{\mathfrak{p}^N}, \chi, s) = 0$. For the converse, let $k \in \mathbb{Z}$ and $f_k = 1_{\varpi^k U^{(a)}}$. On $\varpi^k U^{(a)}$ we have $\chi(x) |x|^s = \chi(\varpi)^k q^{-ks}$, so
$$Z(f_k, \chi, s) = \chi(\varpi)^k \, \mathrm{vol}(U^{(a)}, d^\times x) \, q^{-ks}.$$
The constant in front is not $0$, and linear combinations of the $f_k$ give every Laurent polynomial. $\square$

The corollary explains the choice $L(\chi, s) = 1$ in Definition 5.2.2. For an unramified $\chi$, the same argument shows that the zeta integrals are exactly the functions $L(\chi, s) P$ with $P$ a Laurent polynomial in $q^{-s}$: the proof of part 1 of Theorem 5.2.7 gives the inclusion in one direction, and the functions $1_{\mathfrak{p}^k}$ give $\chi(\varpi)^k q^{-d/2} q^{-ks} L(\chi, s)$ for each $k \in \mathbb{Z}$. So in both cases $L(\chi, s)$ is the generator $1/P(q^{-s})$, with $P$ a polynomial and $P(0) = 1$, of the space of zeta integrals as a module over the Laurent polynomials. Godement and Jacquet define the $L$-factor of a representation of $GL_n$ in this way. In Lean, the local factor `Langlands.HeckeCharacter.localFactor` is defined as $1$ at a ramified place, and the corollary is a direct consequence of this definition. The analytic content is Proposition 5.2.20.

**Theorem 5.2.22 (the $\varepsilon$-factor of $1_{U^{(a)}}$).** Let $\chi$ be ramified with $a = a(\chi)$, let $c \in K$ with $|c| = q^{a+d}$, and let $f = 1_{U^{(a)}}$. Let $\hat f_u$ be the Fourier transform for $\psi$ and $du$, and let $\hat f = q^{-d/2} \hat f_u$ be the transform for the self-dual measure $dx$. The zeta integrals use the measure $d^\times x$ of Definition 5.1.5.
1. $\hat f_u(y) = \psi(y) \, q^{-a} \, 1_{\mathfrak{p}^{-a-d}}(y)$, and $Z(f, \chi, s) = \mathrm{vol}(U^{(a)}, d^\times x)$ for all $s$.
2. For $\mathrm{Re}(s) < 1 - \sigma(\chi)$, $Z(\hat f_u, \chi^{-1}, 1 - s) = \varepsilon_u(\chi, s, \psi) \, Z(f, \chi, s)$, where
$$\varepsilon_u(\chi, s, \psi) = \chi(c)^{-1} |c|^{1-s} G(\chi^{-1}, \psi, c) = \chi(c)^{-1} q^{(a+d)(1/2 - s)} \, q^{d/2} \, \frac{\tau(\chi^{-1}, \psi, c)}{q^{a/2}}.$$
3. The $\varepsilon$-factor of Theorem 5.2.7 is
$$\varepsilon(\chi, s, \psi) = q^{-d/2} \varepsilon_u(\chi, s, \psi) = \chi(c)^{-1} q^{(a+d)(1/2 - s)} \, \frac{\tau(\chi^{-1}, \psi, c)}{q^{a/2}}.$$
It does not depend on $c$. For $c = \varpi^{-a-d}$ it is the factor of Proposition 5.2.4. The number $\tau(\chi^{-1}, \psi, c) / q^{a/2}$ has absolute value $1$.

Lean: `Langlands.Tate.NonArchimedean.fourier_testFunction`, `Langlands.Tate.NonArchimedean.epsilonRamified_eq_cpow`, `Langlands.Tate.NonArchimedean.localFunctionalEquation_ramified_gaussSumFinite`, `Langlands.Tate.NonArchimedean.norm_gaussSumFinite_div_eq_one`

*Proof.* Part 1 is the formula for $\hat 1_{b + \mathfrak{p}^m}$ in Section 5.1, with $b = 1$, $m = a$ and $\mathrm{vol}(\mathfrak{p}^a, du) = q^{-a}$. On $U^{(a)}$ the function $\chi(x)|x|^s$ is $1$, which gives $Z(f, \chi, s)$.

For part 2, the support of $\hat f_u$ is $\{|y| \le q^{a+d}\} = c\mathcal{O}_K$. Substitute $y = cx$ with $x \in \mathcal{O}_K \smallsetminus \{0\}$. The measure $d^\times y$ is invariant, so
$$Z(\hat f_u, \chi^{-1}, 1 - s) = \chi(c)^{-1} |c|^{1-s} q^{-a} \int_{\mathcal{O}_K \smallsetminus \{0\}} h(x) \, d^\times x, \qquad h(x) = \psi(cx) \chi^{-1}(x) |x|^{1-s}.$$
The integral converges absolutely, because $|h(x)| = |x|^{1 - \mathrm{Re}(s) - \sigma(\chi)}$ and the exponent is positive. Split $\mathcal{O}_K \smallsetminus \{0\}$ into the set $B$ of $x$ with $0 < |x| < 1$ and the set $\mathcal{O}_K^\times$. Choose $w \in U^{(a-1)}$ with $\chi(w) \ne 1$, which is possible by Proposition 5.2.13. For $x \in B$ we have $|c(w-1)x| \le q^{a+d} q^{-(a-1)} q^{-1} = q^d$, so $\psi(cwx) = \psi(cx)$, and $h(wx) = \chi(w)^{-1} h(x)$. Multiplication by $w$ maps $B$ onto $B$ and preserves $d^\times x$. As in Proposition 5.2.20, the integral over $B$ is $0$. On $\mathcal{O}_K^\times$ we have $d^\times x = \frac{q}{q-1} dx = \frac{q}{q-1} q^{-d/2} du$, so the integral over $\mathcal{O}_K^\times$ is $\frac{q}{q-1} q^{-d/2} G(\chi^{-1}, \psi, c)$. By Definition 5.1.5 and Lemma 5.2.14, $\mathrm{vol}(U^{(a)}, d^\times x) = \frac{q}{q-1} q^{-d/2} q^{-a}$. Together,
$$Z(\hat f_u, \chi^{-1}, 1 - s) = \chi(c)^{-1} |c|^{1-s} G(\chi^{-1}, \psi, c) \cdot \mathrm{vol}(U^{(a)}, d^\times x).$$
This is the first form of $\varepsilon_u$. The character $\chi^{-1}$ is trivial on $U^{(a)}$, and $|c| = q^{a+d}$, so Proposition 5.2.17 gives $G(\chi^{-1}, \psi, c) = q^{-a} \tau(\chi^{-1}, \psi, c)$. Then
$$|c|^{1-s} q^{-a} = q^{(a+d)(1-s) - a} = q^{(a+d)(1/2 - s)} \, q^{(a+d)/2 - a} = q^{(a+d)(1/2 - s)} \, q^{d/2} \, q^{-a/2},$$
which gives the second form.

For part 3, both $L$-factors are $1$, so $\varepsilon(\chi, s, \psi)$ is the ratio $Z(\hat f, \chi^{-1}, 1-s) / Z(f, \chi, s)$, and $\hat f = q^{-d/2} \hat f_u$. If $c$ is replaced by $cw$ with $w \in \mathcal{O}_K^\times$, then $\chi(cw)^{-1} = \chi(c)^{-1} \chi(w)^{-1}$, and $\tau(\chi^{-1}, \psi, cw) = \chi(w) \tau(\chi^{-1}, \psi, c)$ by (5.2.3) applied to $\chi^{-1}$. The two factors cancel, so the formula does not depend on $c$. For $c = \varpi^{-a-d}$ we have $\chi(c)^{-1} = \chi(\varpi)^{a+d}$ and $\tau(\chi^{-1}, \psi, c) = G(\chi^{-1}, \psi)$, and
$$q^{(a+d)(1/2 - s)} q^{-a/2} = q^{d/2 - (a+d)s}.$$
This is Proposition 5.2.4 with $n = a$. Finally $\chi^{-1}$ has conductor exponent $a$, so Theorem 5.2.19 for $\chi^{-1}$ gives $|\tau(\chi^{-1}, \psi, c)|^2 = q^a$. $\square$

For a unitary $\chi$ we have $|\chi(c)| = 1$, so part 3 gives $|\varepsilon(\chi, 1/2, \psi)| = 1$ directly, without Corollary 5.2.9. With the measure $du$ the same computation gives $|\varepsilon_u(\chi, 1/2, \psi)| = q^{d/2}$. This is the extra factor of item 3 of Remark 5.2.12. If $d = 0$, the two measures agree. The Lean theorem `localFunctionalEquation_ramified_gaussSumFinite` states part 2 in the form $Z(\hat f_u, \chi^{-1}, 1 - s) = \varepsilon_u \, Z(f, \chi, s)$, with the hypothesis $|\chi^{-1}(\varpi)| < q^{\mathrm{Re}(1-s)}$, which is $\mathrm{Re}(s) < 1 - \sigma(\chi)$. Its multiplicative measure is $(1 - q^{-1})^{-1} |x|^{-1} du$, so it has $Z(f, \chi, s) = (1 - q^{-1})^{-1} q^{-a}$. This changes both zeta integrals by the same factor $q^{d/2}$, and it does not change $\varepsilon_u$.

**Example 5.2.23 (a Dirichlet character of conductor $p$).** Let $K = \mathbb{Q}_p$, $\varpi = p$ and $\psi = \psi_{\mathbb{Q}_p}$, so $d = 0$ and $du = dx$. Let $\eta$ be a nontrivial character of $(\mathbb{Z}/p\mathbb{Z})^\times$. Let $\chi = \chi_\eta$ be the character of Example 4.1.6, with $\chi(p) = 1$ and $\chi(u) = \eta(u \bmod p)$ for $u \in \mathbb{Z}_p^\times$. Then $a(\chi) = 1$, and $\mathbb{Z}_p / p\mathbb{Z}_p = \mathbb{F}_p$ with the representatives $1, \dots, p - 1$ of the units. Take $c = p^{-1}$. For $1 \le u \le p - 1$ the fractional part of $u/p$ is $u/p$, so $\psi(u/p) = e^{2\pi i u/p}$. Thus
$$\tau(\chi, \psi, p^{-1}) = \sum_{u=1}^{p-1} \eta(u) e^{2\pi i u/p} = \tau(\eta)$$
is the classical Gauss sum, and Theorem 5.2.19 is the classical identity $|\tau(\eta)|^2 = p$. Lemma 5.2.18 is the identity $\sum_{u=1}^{p-1} \eta(u) = 0$, and Proposition 5.2.20 gives $Z(1_{\mathbb{Z}_p}, \chi, s) = 0$. By Proposition 5.2.17, $G(\chi, \psi, p^{-1}) = p^{-1} \tau(\eta)$. As $\chi(c)^{-1} = \chi(p) = 1$, Theorem 5.2.22 gives
$$\varepsilon(\chi, s, \psi) = p^{1/2 - s} \frac{\tau(\bar\eta)}{p^{1/2}} = p^{-s} \tau(\bar\eta).$$
This is Exercise 7 of Chapter 4 for $n = 1$.

For a numerical check let $p = 5$, and let $\eta$ be the character of order 4 with $\eta(2) = i$. The powers of $2$ modulo $5$ are $2, 4, 3$, so $\eta(4) = -1$ and $\eta(3) = -i$. Let $\zeta = e^{2\pi i/5}$. Then
$$\tau(\eta) = \zeta + i\zeta^2 - i\zeta^3 - \zeta^4 = (\zeta - \zeta^4) + i(\zeta^2 - \zeta^3) = -2\sin(4\pi/5) + 2i\sin(2\pi/5).$$
From $\sin^2(2\pi/5) = (5 + \sqrt 5)/8$ and $\sin^2(4\pi/5) = (5 - \sqrt 5)/8$ we get $|\tau(\eta)|^2 = 4 \cdot 10/8 = 5$. The proof of Theorem 5.2.19 gives the same value in another way. Here $a = 1$, $R = \mathbb{F}_5$ and $S(x) = 5 \cdot 1_{5\mathbb{Z}_5}(x) - 1$. So $|\tau(\eta)|^2 = 5\eta(1) - \sum_{t=1}^{4} \eta(t) = 5 - 0$. Since $\eta(-1) = \eta(4) = -1$, the product formula of Proposition 4.3.4 predicts $\varepsilon(\chi, s, \psi) \varepsilon(\chi^{-1}, 1-s, \psi) = -1$. Indeed this product is $5^{-1} \tau(\bar\eta) \tau(\eta)$, and $\tau(\bar\eta) = \sum_u \overline{\eta(u)} \zeta^u = \eta(-1) \overline{\tau(\eta)}$ by the substitution $u \mapsto -u$. So the product is $-|\tau(\eta)|^2 / 5 = -1$.
