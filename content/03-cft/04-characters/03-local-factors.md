---
title: Tate's local factors
nodes: []
sources: [Tat79]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Tate's local factors

The $L$-factor and the $\varepsilon$-factor are the invariants that the local Langlands correspondence must preserve for $GL_n$. For $GL_1$ they come from the local functional equation in Tate's thesis. This section states that equation without proof and computes the factors.

### Additive characters and measures

Fix a nontrivial character $\psi$ of the additive group $K$. Every other character of $K$ is $\psi_a(x) = \psi(ax)$ for a unique $a \in K$. We assume that $\psi$ has *conductor* $\mathcal{O}_K$: it is trivial on $\mathcal{O}_K$ and not on $\varpi^{-1} \mathcal{O}_K$. For $K = \mathbb{Q}_p$ the standard choice is $\psi(x) = e^{2\pi i \{x\}_p}$, where $\{x\}_p \in \mathbb{Z}[1/p]$ is the fractional part of $x$. This is the local component of the character of Tate's thesis at a finite place. Let $dx$ be the Haar measure on $K$ with $\mathrm{vol}(\mathcal{O}_K) = 1$, and let $d^\times x$ be the Haar measure on $K^\times$ with $\mathrm{vol}(\mathcal{O}_K^\times) = 1$. For a locally constant function $f$ with compact support on $K$, a *Schwartz-Bruhat function*, the Fourier transform is
$$\hat f(y) = \int_K f(x) \psi(xy) \, dx.$$
With the conductor $\mathcal{O}_K$ the measure $dx$ is self-dual: $\hat{\hat f}(x) = f(-x)$, and the transform of $1_{\mathcal{O}_K}$ is $1_{\mathcal{O}_K}$.

### The functional equation

For a character $\chi$ of $K^\times$ and a Schwartz-Bruhat function $f$, the *local zeta integral* is
$$Z(f, \chi, s) = \int_{K^\times} f(x) \chi(x) |x|^s \, d^\times x.$$
The *$L$-factor* is $L(\chi, s) = (1 - \chi(\varpi) q^{-s})^{-1}$ if $\chi$ is unramified, and $L(\chi, s) = 1$ if $\chi$ is ramified.

**Theorem 4.3.1 (Tate's local functional equation).** Let $\chi$ be a character of $K^\times$ with exponent $\sigma$.
1. The integral $Z(f, \chi, s)$ converges for $\mathrm{Re}(s) > -\sigma$. It extends to a rational function of $q^{-s}$, and $Z(f, \chi, s) / L(\chi, s)$ is a polynomial in $q^{s}$ and $q^{-s}$.
2. There is a function $\varepsilon(\chi, s, \psi)$ of the form $c q^{-ms}$, with $c \in \mathbb{C}^\times$ and $m \in \mathbb{Z}$, such that for every $f$
$$Z(\hat f, \chi^{-1}, 1 - s) = \gamma(\chi, s, \psi) Z(f, \chi, s), \qquad \gamma(\chi, s, \psi) = \varepsilon(\chi, s, \psi) \frac{L(\chi^{-1}, 1 - s)}{L(\chi, s)}.$$

Lean: not stated yet

The proof is in Tate's thesis and in [Tat79], Section 3. Its key step is the identity $Z(f, \chi, s) Z(\hat g, \chi^{-1}, 1-s) = Z(\hat f, \chi^{-1}, 1-s) Z(g, \chi, s)$ for all $f$ and $g$, which follows from Fubini's theorem. Thus $\gamma$ does not depend on $f$. The factor $\varepsilon$ is then found by a computation with one good $f$ for each $\chi$, as in the next two propositions.

**Proposition 4.3.2 (unramified characters).** If $\chi$ is unramified, then $\varepsilon(\chi, s, \psi) = 1$.

Lean: not stated yet

*Proof.* Take $f = 1_{\mathcal{O}_K}$, so $\hat f = f$. The set $\mathcal{O}_K \smallsetminus \{0\}$ is the disjoint union of the sets $\varpi^m \mathcal{O}_K^\times$ for $m \ge 0$, and each has measure 1 for $d^\times x$. Thus
$$Z(f, \chi, s) = \sum_{m \ge 0} \chi(\varpi)^m q^{-ms} = L(\chi, s), \qquad Z(\hat f, \chi^{-1}, 1-s) = L(\chi^{-1}, 1-s).$$
Comparing with Theorem 4.3.1 gives $\varepsilon = 1$. $\square$

For a ramified character of conductor exponent $n$, the *Gauss sum* is
$$G(\chi^{-1}, \psi) = \sum_{u \in (\mathcal{O}_K/\varpi^n)^\times} \chi^{-1}(u) \psi(u / \varpi^n).$$
Each term depends only on $u$ modulo $\varpi^n$, because $\chi$ is trivial on $U^{(n)}$ and $\psi$ is trivial on $\mathcal{O}_K$.

**Proposition 4.3.3 (ramified characters).** Let $\chi$ be ramified with $a(\chi) = n \ge 1$. Then
$$\varepsilon(\chi, s, \psi) = \chi(\varpi)^n q^{-ns} G(\chi^{-1}, \psi).$$

Lean: not stated yet

*Proof.* Take $f = 1_{U^{(n)}}$, and let $c = \mathrm{vol}(U^{(n)}) = 1/((q-1)q^{n-1})$ for $d^\times x$. As $\chi |\cdot|^s$ is 1 on $U^{(n)}$, $Z(f, \chi, s) = c$. Next, for $y \in K$,
$$\hat f(y) = \int_{1 + \varpi^n \mathcal{O}_K} \psi(xy) \, dx = \psi(y) \int_{\varpi^n \mathcal{O}_K} \psi(ty) \, dt = q^{-n} \psi(y) 1_{\varpi^{-n}\mathcal{O}_K}(y),$$
because the integral of a nontrivial character over a compact group is 0. We compute $Z(\hat f, \chi^{-1}, 1-s)$ on each set $\varpi^m \mathcal{O}_K^\times$ with $m \ge -n$. For $m \ge 0$ the integrand on this set is a constant times $\chi^{-1}(u)$, and $\int_{\mathcal{O}_K^\times} \chi^{-1}(u) \, d^\times u = 0$ because $\chi$ is ramified. For $-n < m < 0$ let $k = -m$. The function $u \mapsto \psi(\varpi^m u)$ is constant on the cosets of $U^{(k)}$, and $\chi^{-1}$ is not trivial on $U^{(k)}$ since $k < n$. Thus the integral over each coset of $U^{(k)}$ is 0. Only $m = -n$ remains, and there
$$Z(\hat f, \chi^{-1}, 1 - s) = q^{-n} \chi(\varpi)^n q^{n(1-s)} \int_{\mathcal{O}_K^\times} \chi^{-1}(u) \psi(u/\varpi^n) \, d^\times u = \chi(\varpi)^n q^{-ns} \, c \, G(\chi^{-1}, \psi).$$
Both $L$-factors are 1, so $\varepsilon = \gamma = \chi(\varpi)^n q^{-ns} G(\chi^{-1}, \psi)$. $\square$

The right side does not depend on the choice of $\varpi$, see Exercise 6. The exponent $m$ of Theorem 4.3.1 is $a(\chi)$ in both cases, so the $\varepsilon$-factor also records the conductor.

**Proposition 4.3.4 (the product formula).** For each character $\chi$,
$$\varepsilon(\chi, s, \psi) \, \varepsilon(\chi^{-1}, 1 - s, \psi) = \chi(-1).$$

Lean: not stated yet

*Proof.* Apply Theorem 4.3.1 twice, first to $f$ and $\chi$, then to $\hat f$ and $\chi^{-1}$ at $1 - s$:
$$Z(\hat{\hat f}, \chi, s) = \gamma(\chi^{-1}, 1-s, \psi) \gamma(\chi, s, \psi) Z(f, \chi, s).$$
Now $\hat{\hat f}(x) = f(-x)$, and the substitution $x \mapsto -x$ gives $Z(\hat{\hat f}, \chi, s) = \chi(-1) Z(f, \chi, s)$. Choose $f$ with $Z(f, \chi, s) \ne 0$, as in the proofs above. Then $\gamma(\chi, s, \psi)\gamma(\chi^{-1}, 1-s, \psi) = \chi(-1)$. In this product the $L$-factors cancel. $\square$

For a unitary $\chi$, the conjugate of $\varepsilon(\chi, 1/2, \psi)$ is $\chi(-1)\varepsilon(\chi^{-1}, 1/2, \psi)$, and the proposition gives $|\varepsilon(\chi, 1/2, \psi)| = 1$. Exercise 5 checks this directly with the Gauss sum.

**Remark 4.3.5 (change of $\psi$).** For $a \in K^\times$ the factor for $\psi_a$ is
$$\varepsilon(\chi, s, \psi_a) = \chi(a) |a|^{s - 1/2} \varepsilon(\chi, s, \psi),$$
where for $\psi_a$ one uses its self-dual measure $|a|^{1/2} dx$. It follows from the formulas of [Tat79], Section 3.2, for a change of $\psi$ and of the measure. The $L$-factor does not depend on $\psi$.

**Example 4.3.6 (a quadratic character).** Let $p$ be odd, $K = \mathbb{Q}_p$ and $\psi(x) = e^{2\pi i\{x\}_p}$. Let $\chi = \chi_{p^*}$ with $p^* = (-1)^{(p-1)/2} p$. By Example 3.5.6, $\chi(p) = 1$ and $\chi(u)$ is the Legendre symbol of $u$, so $a(\chi) = 1$. Proposition 4.3.3 gives
$$\varepsilon(\chi, 1/2, \psi) = p^{-1/2} \sum_{u = 1}^{p-1} \left(\frac{u}{p}\right) e^{2\pi i u/p}.$$
By Gauss, the sum is $\sqrt p$ if $p \equiv 1$ modulo 4 and $i\sqrt p$ if $p \equiv 3$ modulo 4. Thus $\varepsilon(\chi, 1/2, \psi)$ is 1 or $i$. The square is $\chi(-1) = \left(\frac{-1}{p}\right)$, as Proposition 4.3.4 predicts.

### The Galois side

For a character $\phi$ of $W_K$, let $L(\phi, s) = (1 - \phi(\Phi) q^{-s})^{-1}$ if $\phi$ is unramified, and $L(\phi, s) = 1$ otherwise. Here $\Phi$ is a geometric Frobenius. By Theorem 4.2.3, part 3, $L(\phi, s) = L(\chi_\phi, s)$. One defines $\varepsilon(\phi, s, \psi) = \varepsilon(\chi_\phi, s, \psi)$.

**Remark 4.3.7 (why the geometric normalization).** The formula $L(\phi, s) = L(\chi_\phi, s)$ needs $\chi_\phi(\varpi) = \phi(\Phi)$ with the geometric Frobenius $\Phi$. In the arithmetic normalization, $\phi \circ \mathrm{Art}_K$ takes the value $\phi(\mathrm{Frob}) = \phi(\Phi)^{-1}$ at $\varpi$, and the $L$-factors match only after $\chi$ is replaced by $\chi^{-1}$. The $L$-function of a representation $V$ of $W_K$ is $\det(1 - \Phi q^{-s} \mid V^{I_K})^{-1}$, with the geometric Frobenius, because this matches the zeta function of a variety over a finite field. This is the reason for the convention of Deligne and of [Tat79].

**Theorem 4.3.8 (Langlands and Deligne).** There is a unique way to attach a factor $\varepsilon(\rho, s, \psi)$ to each finite-dimensional continuous representation $\rho$ of $W_K$ and each $\psi$, with the following properties.
1. It is multiplicative in short exact sequences of representations.
2. For a character $\phi$ of $W_K$, it is $\varepsilon(\chi_\phi, s, \psi)$.
3. For a finite separable extension $L / K$ and a virtual representation $\rho$ of $W_L$ of dimension 0, $\varepsilon(\mathrm{Ind}_{W_L}^{W_K} \rho, s, \psi) = \varepsilon(\rho, s, \psi \circ \mathrm{Tr}_{L/K})$.

Lean: not stated yet

Uniqueness follows from Brauer's induction theorem, and existence is the hard part. Langlands found a local proof in an unpublished manuscript. Deligne published a proof in 1973 that uses global methods. The theorem is in [Tat79], Section 3. It shows that the $\varepsilon$-factors of $GL_1$ already determine the $\varepsilon$-factors of all representations of $W_K$.
