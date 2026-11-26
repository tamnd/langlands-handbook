---
title: Ramanujan-Petersson and Sato-Tate
nodes: [LGV8B6TVWZ, LG1DP2ZDPA, LGVZHDXVTZ]
sources: [Del74, BLGHT11]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Ramanujan-Petersson and Sato-Tate

This section states the bound $|a_p(f)| \le 2p^{(k-1)/2}$ for normalized eigenforms, which Deligne proved, and deduces Ramanujan's bound for $\tau(p)$. For elliptic curves the bound is Hasse's theorem, and the Sato-Tate theorem describes the distribution of the numbers $a_p(E)/2\sqrt{p}$ in $[-1, 1]$.

### Satake parameters

Let $f \in S_k(N, \chi)$ be a normalized eigenform and $p \nmid N$ a prime. The *Satake parameters* of $f$ at $p$ are the roots $\alpha_p, \beta_p$ of
$$X^2 - a_p(f) X + \chi(p) p^{k-1} = (X - \alpha_p)(X - \beta_p).$$
So the Euler factor of Proposition 2.2.3 at $p$ is $(1 - \alpha_p p^{-s})^{-1}(1 - \beta_p p^{-s})^{-1}$, and $a_{p^r}(f) = \sum_{i + j = r} \alpha_p^i\beta_p^j$.

**Lemma 2.3.1 (the bound and the parameters).** Let $f \in S_k(N, \chi)$ be a normalized eigenform and $p \nmid N$. Then $a_p(f) = \chi(p)\overline{a_p(f)}$, and these conditions are equivalent.
1. $|a_p(f)| \le 2p^{(k-1)/2}$.
2. $|\alpha_p| = |\beta_p| = p^{(k-1)/2}$.

Lean: not stated yet

*Proof.* By Theorem 1.6.2, $T_p^* = \langle p \rangle^{-1} T_p$, and $\langle p \rangle^{-1}$ acts on $S_k(N, \chi)$ by $\overline{\chi(p)}$. With the Petersson product, linear in the first variable,
$$a_p \langle f, f \rangle = \langle T_p f, f \rangle = \langle f, T_p^* f \rangle = \langle f, \overline{\chi(p)}a_p f\rangle = \chi(p)\overline{a_p}\langle f, f \rangle,$$
and $\langle f, f \rangle > 0$. This is the first claim. Let $u$ be a square root of $\chi(p)$, so $|u| = 1$ and $\bar u = u^{-1}$. Then $b = a_p/u$ satisfies $\bar b = \overline{a_p} u = \chi(p)^{-1}a_p u = b$, so $b$ is real. The numbers $\alpha_p/u$ and $\beta_p/u$ are the roots of $X^2 - bX + p^{k-1}$, a polynomial with real coefficients. If 2 holds, then $|a_p| = |\alpha_p + \beta_p| \le 2p^{(k-1)/2}$. If 1 holds, then $b^2 \le 4p^{k-1}$, so the roots $\alpha_p/u$ and $\beta_p/u$ are complex conjugate, or equal and real. In both cases each has absolute value $\sqrt{p^{k-1}}$, since their product is $p^{k-1}$. $\square$

The trivial bound from Proposition 2.2.1 is $|a_p| \le Cp^{k/2}$. Condition 2 says that the Euler factor at $p$ has its poles on the line $\mathrm{Re}(s) = (k-1)/2$, the analogue at $p$ of the Riemann hypothesis. Rankin improved the trivial bound to $O(p^{k/2 - 1/5})$ in 1939 with the Rankin-Selberg method.

### Deligne's theorem

**Theorem 2.3.2 (Ramanujan-Petersson conjecture, Deligne).** Let $N \ge 1$, let $f \in S_k(\Gamma_0(N))$ be a normalized eigenform, and let $p \nmid N$ be a prime. Then
$$|a_p(f)| \le 2p^{(k-1)/2}.$$

Node: LGV8B6TVWZ · Lean: `Langlands.RamanujanPeterssonHolomorphic`

*Outline of the proof.* The proof is in [Del74, Section 8]. For $k \ge 2$, Section 2.4 attaches to $f$ a representation $\rho$ of $G_\mathbb{Q}$ of dimension 2 with $\det(X - \rho(\mathrm{Frob}_p)) = X^2 - a_pX + p^{k-1}$ for $p \nmid N\ell$. Deligne constructed $\rho$ in the étale cohomology $H^{k-1}$ of a smooth proper variety over $\mathbb{Q}$, a resolution of the $(k-2)$-fold fibre product of the universal elliptic curve over a modular curve, which has good reduction at $p$. By his proof of the Weil conjectures in [Del74], the eigenvalues of Frobenius on $H^{k-1}$ of a smooth proper variety over $\mathbb{F}_p$ have absolute value $p^{(k-1)/2}$. So condition 2 of Lemma 2.3.1 holds. For $k = 2$ the variety is the modular curve, and the result is the theorem of Eichler, Shimura and Igusa with Weil's Riemann hypothesis for curves. $\square$

**Remark 2.3.3 (the Lean form).** The statement `Langlands.RamanujanPeterssonHolomorphic` quantifies over all $N > 0$, all $k \in \mathbb{Z}$ and all cusp forms $f$ on $\Gamma_0(N)$ of weight $k$ that satisfy `Langlands.IsNormalizedEigenform f` of Definition 2.1.4, and it concludes `‖qCoeff f p‖ ≤ 2 * p ^ ((k - 1) / 2)` for all primes $p \nmid N$, with a real exponent. There is no hypothesis on $k$. For odd $k$, $S_k(\Gamma_0(N)) = 0$ by Proposition 1.2.6, and for $k \le 0$, $S_k(\Gamma_0(N)) = 0$: the product of the forms $f|\gamma$ over the cosets of $\Gamma_0(N)$ in $SL_2(\mathbb{Z})$ is a cusp form of level one and of weight $\le 0$, so it is 0 by Proposition 1.3.3. In these cases no $f$ has $a_1 = 1$, and the statement holds trivially. For $k = 1$ the bound is a theorem of Deligne and Serre for $\Gamma_1(N)$, but it is empty on $\Gamma_0(N)$. The statement is for the trivial character only; Deligne's theorem holds for all $\chi$, with the same proof. By Remark 2.1.11 it does not matter that the statement is for all normalized eigenforms and not for newforms.

**Corollary 2.3.4 (Ramanujan's conjecture).** For each prime $p$,
$$|\tau(p)| \le 2p^{11/2}.$$

Node: LG1DP2ZDPA · Lean: `Langlands.Bridge.ramanujan_petersson_of_ramanujanPeterssonHolomorphic`

*Proof.* By Corollary 1.6.5, $\Delta$ is a normalized eigenform in $S_{12}(\Gamma_0(1))$ with $a_n(\Delta) = \tau(n)$. Apply Theorem 2.3.2 with $N = 1$, $k = 12$. $\square$

**Remark 2.3.5 (the Lean bridge).** The Lean project proves Corollary 2.3.4 from two hypotheses. The theorem `Langlands.Bridge.ramanujan_petersson_of_ramanujanPeterssonHolomorphic` takes `hΔ : DeltaIsEigenform` and `h : RamanujanPeterssonHolomorphic`, and it proves the statement `ramanujan_petersson` of the Formal Conjectures project, ported as `Langlands.Ported.FormalConjectures.RamanujanTau.ramanujan_petersson`. That statement defines $\Delta$ as the power series $X\prod_{n \ge 1}(1 - X^n)^{24}$ with integer coefficients, $\tau(n)$ as its coefficients, and asserts $|\tau(p)| \le 2p^{11/2}$ for each prime $p$. The hypothesis `Langlands.Bridge.DeltaIsEigenform` says that there is a cusp form $f$ on $\Gamma_0(1)$ of weight 12 with `IsNormalizedEigenform f` and `qCoeff f n = τ n` for all $n$. This is Mordell's theorem, Corollary 1.6.5, together with the product formula of Proposition 1.2.13. It is not proved in Lean, because Mathlib has no Hecke operators. The proof of the bridge is the proof of Corollary 2.3.4: it applies `h` to $f$ with $N = 1$ and $k = 12$ and compares the two descriptions of $\tau$. So this corollary is a Lean theorem whose hypotheses are a classical theorem and Deligne's theorem.

For $p = 2$, $|\tau(2)| = 24 \le 2 \cdot 2^{5.5} \approx 90.5$, and for $p = 3$, $|\tau(3)| = 252 \le 2 \cdot 3^{5.5} \approx 841.8$. The Satake parameters of $\Delta$ at 2 are $-12 \pm 4\sqrt{-119}$, of absolute value $\sqrt{144 + 1904} = 2^{11/2}$.

### Elliptic curves and the Sato-Tate theorem

Let $E$ be an elliptic curve over $\mathbb{Q}$ and $p$ a prime of good reduction. By Theorem 2.2.11, $a_p(E) = a_p(f_E)$ for a newform $f_E$ of weight 2, and Hasse's Theorem 2.2.9 is the case $k = 2$ of Theorem 2.3.2 for $f_E$. Conversely, Theorem 2.3.2 for $k = 2$ follows from Hasse's theorem for the abelian varieties of Section 2.4, a theorem of Weil. Write
$$a_p(E) = 2\sqrt{p}\cos\theta_p, \qquad \theta_p \in [0, \pi].$$
The angle $\theta_p$ is the *Sato-Tate angle* of $E$ at $p$, and $\sqrt{p}e^{\pm i\theta_p}$ are the Satake parameters. Sato and Tate conjectured around 1963 how the angles are distributed.

An elliptic curve $E$ over $\mathbb{Q}$ has *complex multiplication* if $\mathrm{End}(E_{\bar{\mathbb{Q}}})$ is larger than $\mathbb{Z}$. Then $\mathrm{End}(E_{\bar{\mathbb{Q}}})$ is an order in an imaginary quadratic field, its class number is 1 because $j(E) \in \mathbb{Q}$, and there are 13 such orders.

**Theorem 2.3.6 (Sato-Tate, Barnet-Lamb, Geraghty, Harris and Taylor).** Let $E$ be an elliptic curve over $\mathbb{Q}$ without complex multiplication. For $0 \le \alpha \le \beta \le \pi$,
$$\lim_{x \to \infty} \frac{|\{p \le x : p \text{ good},\ \theta_p \in [\alpha, \beta]\}|}{|\{p \le x\}|} = \frac{2}{\pi}\int_\alpha^\beta \sin^2\theta\, d\theta.$$

Node: LGVZHDXVTZ · Lean: `Langlands.SatoTate`

*Outline of the proof.* This is in [BLGHT11], which completes the earlier work of Clozel, Harris, Shepherd-Barron and Taylor for curves with a prime of multiplicative reduction. By a theorem of Serre, the equidistribution follows if the $L$-functions $L(\mathrm{Sym}^m E, s)$ of the symmetric powers, with the Euler factors $\prod_{i=0}^m (1 - \alpha_p^i\beta_p^{m-i}p^{-s})^{-1}$, are holomorphic and nonzero on $\mathrm{Re}(s) \ge 1 + m/2$ for all $m \ge 1$. The functions $\mathrm{Sym}^m$ of $\theta$, namely $\sin((m+1)\theta)/\sin\theta$, are the characters of $SU(2)$, and the measure $(2/\pi)\sin^2\theta\, d\theta$ is the image of the Haar measure of $SU(2)$ on its conjugacy classes. The authors prove that each $\mathrm{Sym}^m$ of the Galois representation of $E$ is potentially automorphic: it becomes automorphic over a suitable totally real field, which suffices for the analytic properties by Brauer's theorem. $\square$

**Remark 2.3.7 (the Lean form of Sato-Tate).** In Lean, `Langlands.cmJInvariants` is the set of the 13 rational numbers $0$, $1728$, $-3375$, $8000$, $-32768$, $54000$, $287496$, $-884736$, $-12288000$, $16581375$, $-884736000$, $-147197952000$ and $-262537412640768000$, the $j$-invariants of the orders of class number one, of discriminants $-3, -4, -7, -8, -11, -12, -16, -19, -27, -28, -43, -67, -163$. The predicate `Langlands.HasCMOverQ E` is $j(E) \in$ `cmJInvariants`, which is equivalent to complex multiplication over $\bar{\mathbb{Q}}$. The angle is `Langlands.satoTateAngle E p`, defined as $\arccos(a_p(E)/(2\sqrt{p}))$ with `E.LFunction p` for $a_p(E)$. The statement `Langlands.SatoTate` asserts, for $E$ without CM and $0 \le \alpha \le \beta \le \pi$, that the ratio of the number of primes $p \le x$ with angle in $[\alpha, \beta]$ to the number of primes $p \le x$ tends to $(2/\pi)\int_\alpha^\beta \sin^2\theta\, d\theta$. It counts all the primes, the bad ones too; for a bad prime $a_p \in \{0, \pm 1\}$ and the angle is defined, but finitely many primes do not change the limit. The fidelity theorems in `Langlands/Fidelity/Modularity.lean` check the normalization: `Langlands.Fidelity.satoTate_total_mass` proves that the measure has total mass 1, `Langlands.Fidelity.not_hasCMOverQ_X0_11` that the curve of Example 2.2.15 has no CM, and `Langlands.Fidelity.not_satoTateUniform` that `SatoTate` makes the variant with the uniform measure $d\theta/\pi$ false.

**Example 2.3.8 (a curve with complex multiplication).** Let $E$ be $y^2 = x^3 - x$, with $j = 1728$ and $\mathrm{End}(E_{\bar{\mathbb{Q}}}) = \mathbb{Z}[i]$, where $i$ acts by $(x, y) \mapsto (-x, iy)$. Its conductor is 32. For $p \equiv 3 \bmod 4$ the map $x \mapsto -x$ shows that the values $x^3 - x$ and $-(x^3 - x)$ occur equally often, and $-1$ is not a square modulo $p$. So exactly one of them is a nonzero square when $x^3 - x \ne 0$, and $|\tilde{E}(\mathbb{F}_p)| = p + 1$. So $a_p(E) = 0$ and $\theta_p = \pi/2$ for these $p$, which are half of the primes. A count of points gives
$$a_5 = -2, \quad a_{13} = 6, \quad a_{17} = 2, \quad a_{29} = -10, \quad a_{37} = -2, \quad a_{41} = 10,$$
and for $p \equiv 1 \bmod 4$ one has $a_p = \pm 2a$, where $p = a^2 + b^2$ with $a$ odd. For these primes Hecke's equidistribution theorem for the Hecke character of $\mathbb{Q}(i)$ shows that the angles are equidistributed for the measure $d\theta/\pi$. So the limit measure of the angles of $E$ is $\frac{1}{2}\delta_{\pi/2} + \frac{1}{2\pi}d\theta$, and not the Sato-Tate measure. The Lean project proves `Langlands.Fidelity.hasCMOverQ_congruentNumber`, that this curve satisfies `HasCMOverQ`, so it is outside the hypothesis of `Langlands.SatoTate`.
