---
title: Modular forms and q-expansions
nodes: []
sources: []
status: drafted
drafted_by: writer
reviewed_by: []
---
## Modular forms and q-expansions

This section defines modular forms and cusp forms of weight $k$ for a congruence subgroup, and their $q$-expansions at the cusps. Then it constructs the first examples: the Eisenstein series $G_k$ of level one, with their $q$-expansions, and the discriminant $\Delta$. The example to keep in mind is $\Delta = q - 24q^2 + 252 q^3 - \cdots$, a cusp form of weight 12 for $SL_2(\mathbb{Z})$ whose coefficients are integers.

### The slash operator

**Definition 1.2.1 (the slash operator).** Let $k \in \mathbb{Z}$, let $\gamma \in GL_2^+(\mathbb{R})$ and let $f : \mathbb{H} \to \mathbb{C}$ be a function. The function $f |_k \gamma$ is
$$(f|_k \gamma)(\tau) = \det(\gamma)^{k-1} \, j(\gamma, \tau)^{-k} \, f(\gamma \tau).$$

We often write $f|\gamma$ when $k$ is fixed. The factor $\det(\gamma)^{k-1}$ is the normalization of Diamond and Shurman and of Mathlib. Shimura uses $\det(\gamma)^{k/2}$, which makes the scalar matrices act trivially. The two normalizations agree on $SL_2(\mathbb{R})$. They differ by the factor $\det(\gamma)^{k/2 - 1}$, and this factor changes the Hecke operators by a power of $p$. Our choice makes the Hecke eigenvalues of the forms with integer coefficients integers.

**Lemma 1.2.2 (the slash operator is an action).** Let $\gamma, \gamma' \in GL_2^+(\mathbb{R})$ and $r > 0$. Then $(f|_k \gamma)|_k \gamma' = f|_k (\gamma \gamma')$, $f|_k (rI) = r^{k-2} f$, and $f|_k(-I) = (-1)^k f$.

Lean: not stated yet

*Proof.* By the cocycle relation of Lemma 1.1.2,
$$(f|\gamma\gamma')(\tau) = \det(\gamma)^{k-1} \det(\gamma')^{k-1} j(\gamma, \gamma'\tau)^{-k} j(\gamma', \tau)^{-k} f(\gamma(\gamma'\tau)) = \det(\gamma')^{k-1} j(\gamma', \tau)^{-k} (f|\gamma)(\gamma' \tau).$$
The right side is $((f|\gamma)|\gamma')(\tau)$. For $rI$ we have $\det = r^2$ and $j = r$, so the factor is $r^{2k-2} r^{-k} = r^{k-2}$. For $-I$ we have $\det = 1$ and $j = -1$. $\square$

So $GL_2^+(\mathbb{R})$ acts on the right on the space of functions on $\mathbb{H}$.

### Modular forms

**Definition 1.2.3 (modular forms and cusp forms).** Let $\Gamma$ be a congruence subgroup and let $k \in \mathbb{Z}$. A *modular form of weight $k$ for $\Gamma$* is a holomorphic function $f : \mathbb{H} \to \mathbb{C}$ with these properties.
1. $f|_k \gamma = f$ for each $\gamma \in \Gamma$.
2. $f$ is *holomorphic at the cusps*: for each $\alpha \in SL_2(\mathbb{Z})$ there is $Y > 0$ such that $f|_k \alpha$ is bounded on $\{\mathrm{Im}\, \tau \ge Y\}$.

A modular form $f$ is a *cusp form* if $(f|_k \alpha)(\tau) \to 0$ as $\mathrm{Im}\, \tau \to \infty$, for each $\alpha \in SL_2(\mathbb{Z})$. The modular forms and the cusp forms of weight $k$ for $\Gamma$ form complex vector spaces $M_k(\Gamma) \supset S_k(\Gamma)$.

Condition 1 for $\gamma = \begin{pmatrix} a & b \\ c & d \end{pmatrix} \in \Gamma$ reads $f(\gamma\tau) = (c\tau + d)^k f(\tau)$. The product of modular forms of weights $k$ and $l$ is a modular form of weight $k + l$, so $\bigoplus_k M_k(\Gamma)$ is a graded ring. If $\Gamma' \subset \Gamma$, then $M_k(\Gamma) \subset M_k(\Gamma')$.

**Lemma 1.2.4 ($q$-expansions).** Let $f$ be a holomorphic function on $\mathbb{H}$ with $f(\tau + h) = f(\tau)$ for some $h \ge 1$, and let $q_h = e^{2\pi i \tau/h}$.
1. There are unique numbers $a_n \in \mathbb{C}$, for $n \in \mathbb{Z}$, with $f(\tau) = \sum_{n \in \mathbb{Z}} a_n q_h^n$. The series converges absolutely and uniformly on each set $\{\mathrm{Im}\, \tau \ge Y\}$.
2. $f$ is bounded on $\{\mathrm{Im}\, \tau \ge Y\}$ for some $Y$ if and only if $a_n = 0$ for all $n < 0$. In this case $f(\tau) \to a_0$ as $\mathrm{Im}\, \tau \to \infty$, and $f$ is bounded on $\{\mathrm{Im}\, \tau \ge Y\}$ for every $Y > 0$.

Lean: not stated yet

*Proof.* The map $\tau \mapsto q_h$ sends $\mathbb{H}$ onto the punctured disc $\{0 < |q| < 1\}$, and two points have the same image if and only if they differ by a multiple of $h$. So there is a function $g$ on the punctured disc with $f(\tau) = g(q_h)$. It is holomorphic, because locally $\tau = \frac{h}{2\pi i} \log q$ for a branch of the logarithm. Its Laurent expansion $g(q) = \sum_n a_n q^n$ converges absolutely and uniformly on each annulus $\{r_1 \le |q| \le r_2\}$ with $0 < r_1$ and $r_2 < 1$, and the region $\{\mathrm{Im}\,\tau \ge Y\}$ corresponds to $|q| \le e^{-2\pi Y/h}$. On a punctured disc around 0, a holomorphic function is bounded if and only if the singularity at 0 is removable, by Riemann's theorem, and that holds if and only if $a_n = 0$ for $n < 0$. Then $g$ extends to a holomorphic function on the disc, the expansion converges uniformly on each disc $|q| \le r < 1$, and $g(q) \to g(0) = a_0$ as $q \to 0$. $\square$

Let $f \in M_k(\Gamma)$ and $\alpha \in SL_2(\mathbb{Z})$. Let $N$ be such that $\Gamma \supset \Gamma(N)$. Since $\Gamma(N)$ is normal, $\alpha T^N \alpha^{-1} \in \Gamma$, and so $(f|\alpha)|T^N = f|\alpha T^N \alpha^{-1} \alpha = f|\alpha$. The slash by $T^N$ is the translation $\tau \mapsto \tau + N$, because $j(T^N, \tau) = 1$. So Lemma 1.2.4 applies to $f|\alpha$ with $h = N$, or with any $h \ge 1$ such that $\alpha T^h \alpha^{-1} \in \Gamma$. The expansion of $f|\alpha$ is the *expansion of $f$ at the cusp $\alpha\infty$*. Condition 2 of Definition 1.2.3 says that it has no negative terms, and $f$ is a cusp form if and only if the constant term $a_0$ of each of these expansions is 0. If $\alpha' \infty$ and $\alpha \infty$ are in the same $\Gamma$-orbit, then $\alpha' = \pm \gamma \alpha T^m$ for some $\gamma \in \Gamma$ and $m \in \mathbb{Z}$, and $f|\alpha' = \pm (f|\alpha)|T^m$. So it suffices to check condition 2 at one point of each cusp, and the number of conditions is finite.

**Remark 1.2.5 ($q$-expansions at $\infty$ and the Lean coefficients).** For $\Gamma = \Gamma_0(N)$ or $\Gamma_1(N)$ the matrix $T$ is in $\Gamma$, so a modular form for $\Gamma$ has an expansion
$$f(\tau) = \sum_{n \ge 0} a_n(f) q^n, \qquad q = e^{2\pi i \tau},$$
at the cusp $\infty$. We call it the *$q$-expansion* of $f$, and $a_n(f)$ the $n$th *coefficient*. A modular form is determined by its $q$-expansion, because the expansion determines $f$ on $\mathbb{H}$. The Lean project writes `Langlands.qCoeff f n` for $a_n(f)$, for a cusp form $f$ on $\Gamma_0(N)$, and `Langlands.qCoeffGamma1 f n` for a cusp form on $\Gamma_1(N)$. Both are the coefficients of `UpperHalfPlane.qExpansion 1 f` of Mathlib, the expansion in $q = q_1$. The width is important here. An expansion in $q_N = e^{2\pi i \tau / N}$ is also an expansion of $f$, but it has the coefficient $a_n(f)$ at $q_N^{nN}$, and its coefficient at $q_N$ is 0 for $N \ge 2$. Volume 0, Example 3.2.2, shows how this changes the meaning of a statement.

**Proposition 1.2.6 (odd weight).** Let $\Gamma$ be a congruence subgroup that contains $-I$, and let $k$ be odd. Then $M_k(\Gamma) = 0$. In particular $M_k(\Gamma_0(N)) = 0$ for odd $k$.

Lean: not stated yet

*Proof.* By Lemma 1.2.2, $f = f|(-I) = (-1)^k f = -f$. $\square$

The groups $\Gamma_1(N)$ with $N \ge 3$ do not contain $-I$, and they have nonzero forms of odd weight. Section 1.5 shows that these forms have a nebentypus $\chi$ with $\chi(-1) = -1$.

**Lemma 1.2.7 (conjugation by a rational matrix).** Let $\Gamma$ be a congruence subgroup, $\alpha \in GL_2^+(\mathbb{Q})$ and $k \in \mathbb{Z}$.
1. The group $\Gamma_\alpha = \alpha^{-1}\Gamma\alpha \cap SL_2(\mathbb{Z})$ is a congruence subgroup.
2. If $f \in M_k(\Gamma)$, then $f|_k\alpha \in M_k(\Gamma_\alpha)$. If $f \in S_k(\Gamma)$, then $f|_k\alpha \in S_k(\Gamma_\alpha)$.

Lean: not stated yet

*Proof.* By Lemma 1.2.2, replacing $\alpha$ by a positive multiple changes $f|\alpha$ by a nonzero constant and does not change $\Gamma_\alpha$. So we may assume that $\alpha$ has integer entries. Let $M = \det \alpha$, and let $\Gamma \supset \Gamma(N)$. For $\gamma = I + NM X \in \Gamma(NM)$ we get
$$\alpha \gamma \alpha^{-1} = \alpha (I + NMX) \frac{\mathrm{adj}(\alpha)}{M} = I + N \alpha X \, \mathrm{adj}(\alpha),$$
where $\mathrm{adj}(\alpha) = M \alpha^{-1}$ has integer entries. So $\alpha \gamma \alpha^{-1} \in \Gamma(N)$, and $\Gamma(NM) \subset \Gamma_\alpha$. This proves part 1. For part 2, $f|\alpha$ is holomorphic, and for $\gamma \in \Gamma_\alpha$ we have $(f|\alpha)|\gamma = (f|\alpha\gamma\alpha^{-1})|\alpha = f|\alpha$. Let $\delta \in SL_2(\mathbb{Z})$. The first column of the integer matrix $\alpha \delta$ is $g \cdot (x, y)^t$ with $g > 0$ and $(x, y)$ primitive. Let $\delta' \in SL_2(\mathbb{Z})$ have the first column $(x, y)^t$. Then $\delta'^{-1} \alpha \delta$ has the first column $(g, 0)^t$, so it is $u = \begin{pmatrix} g & b \\ 0 & e \end{pmatrix}$ with $ge = M$ and $e > 0$. Now $f|\alpha\delta = F|u$ with $F = f|\delta'$, and
$$(F|u)(\tau) = M^{k-1} e^{-k} F\left(\frac{g\tau + b}{e}\right).$$
The imaginary part of $(g\tau + b)/e$ is $(g/e)\,\mathrm{Im}\, \tau$. By Lemma 1.2.4, $F$ is bounded on each region $\{\mathrm{Im}\,\tau \ge Y\}$, and it tends to 0 at $\infty$ if $f$ is a cusp form. So $F|u$ has the same properties. $\square$

**Example 1.2.8 (forms of level $N$ from level one).** Let $f \in M_k(SL_2(\mathbb{Z}))$ and $N \ge 1$, and let $f_N(\tau) = f(N\tau)$. Then $f_N \in M_k(\Gamma_0(N))$. Indeed, let $\alpha = \begin{pmatrix} N & 0 \\ 0 & 1 \end{pmatrix}$. Then $f|_k \alpha = N^{k-1} f_N$. For $\gamma = \begin{pmatrix} a & b \\ c & d \end{pmatrix} \in \Gamma_0(N)$ we have $\alpha \gamma \alpha^{-1} = \begin{pmatrix} a & Nb \\ c/N & d \end{pmatrix} \in SL_2(\mathbb{Z})$, so $\Gamma_0(N) \subset \Gamma_\alpha$, and Lemma 1.2.7 applies. The $q$-expansion of $f_N$ is $\sum a_n(f) q^{Nn}$. These forms are the first examples of *oldforms*, which Section 2.1 studies.

### Eisenstein series

**Proposition 1.2.9 (Eisenstein series).** Let $k \ge 3$ be an integer. The series
$$G_k(\tau) = \sum_{(m, n) \in \mathbb{Z}^2 \setminus \{0\}} \frac{1}{(m\tau + n)^k}$$
converges absolutely and uniformly on each compact subset of $\mathbb{H}$. Its sum is holomorphic, and $G_k(\gamma\tau) = (c\tau + d)^k G_k(\tau)$ for each $\gamma \in SL_2(\mathbb{Z})$. If $k$ is odd, then $G_k = 0$.

Lean: not stated yet

*Proof.* Let $K \subset \mathbb{H}$ be compact. The function $(u, v, \tau) \mapsto |u\tau + v|$ is continuous and positive on the compact set of the $(u, v, \tau)$ with $\max(|u|, |v|) = 1$ and $\tau \in K$. Let $c > 0$ be its minimum. By homogeneity, $|m\tau + n| \ge c \max(|m|, |n|)$ for all $(m, n)$ and $\tau \in K$. There are $8r$ pairs $(m, n)$ with $\max(|m|, |n|) = r$, so the series is bounded on $K$ by $c^{-k} \sum_{r \ge 1} 8 r^{1-k}$, which converges for $k \ge 3$. So the series converges normally on $K$, and its sum is holomorphic. For $\gamma \in SL_2(\mathbb{Z})$,
$$m \gamma\tau + n = \frac{(ma + nc)\tau + (mb + nd)}{c\tau + d},$$
and $(m, n) \mapsto (m, n)\gamma$ is a bijection of $\mathbb{Z}^2 \setminus \{0\}$. So $G_k(\gamma\tau) = (c\tau + d)^k G_k(\tau)$. If $k$ is odd, the terms of $(m, n)$ and $(-m, -n)$ cancel. $\square$

**Lemma 1.2.10 (the Lipschitz formula).** Let $k \ge 2$ and $\tau \in \mathbb{H}$, and let $q = e^{2\pi i\tau}$. Then
$$\sum_{n \in \mathbb{Z}} \frac{1}{(\tau + n)^k} = \frac{(-2\pi i)^k}{(k-1)!} \sum_{r \ge 1} r^{k-1} q^r.$$

Lean: not stated yet

*Proof.* We use the partial fraction expansion of the cotangent,
$$\pi \cot \pi\tau = \frac{1}{\tau} + \sum_{n \ge 1} \left( \frac{1}{\tau + n} + \frac{1}{\tau - n} \right),$$
where the series converges uniformly on compact subsets of $\mathbb{C} \setminus \mathbb{Z}$. On the other hand, $\cot z = i (e^{2iz} + 1)/(e^{2iz} - 1)$, and for $z = \pi\tau$ with $\tau \in \mathbb{H}$ we have $e^{2iz} = q$ and $|q| < 1$. So
$$\pi \cot \pi \tau = -\pi i \, \frac{1 + q}{1 - q} = -\pi i - 2\pi i \sum_{r \ge 1} q^r.$$
Differentiate both expressions $k - 1$ times with respect to $\tau$. The derivative of order $k - 1$ of $1/(\tau + n)$ is $(-1)^{k-1}(k-1)!\,(\tau + n)^{-k}$, and that of $q^r$ is $(2\pi i r)^{k-1} q^r$. We get
$$(-1)^{k-1} (k-1)! \sum_{n \in \mathbb{Z}} (\tau + n)^{-k} = -(2\pi i)^k \sum_{r \ge 1} r^{k-1} q^r,$$
which is the formula. For $k = 2$ the series on the left converges absolutely, and term by term differentiation is allowed in both cases by the uniform convergence on compact sets. $\square$

Let $\sigma_{k-1}(n) = \sum_{d \mid n} d^{k-1}$. Let $B_k$ be the Bernoulli numbers, defined by $t/(e^t - 1) = \sum_k B_k t^k / k!$. Euler's formula is $\zeta(k) = -(2\pi i)^k B_k / (2 \cdot k!)$ for even $k \ge 2$.

**Theorem 1.2.11 (the $q$-expansion of $G_k$).** Let $k \ge 4$ be even. Then $G_k \in M_k(SL_2(\mathbb{Z}))$, and
$$G_k(\tau) = 2\zeta(k) + \frac{2(2\pi i)^k}{(k-1)!} \sum_{n \ge 1} \sigma_{k-1}(n) q^n.$$
The *normalized Eisenstein series* $E_k = G_k / (2\zeta(k))$ has the $q$-expansion
$$E_k(\tau) = 1 - \frac{2k}{B_k} \sum_{n \ge 1} \sigma_{k-1}(n) q^n.$$

Lean: not stated yet

*Proof.* Split the sum into the terms with $m = 0$ and the terms with $m \ne 0$. The terms with $m = 0$ give $\sum_{n \ne 0} n^{-k} = 2\zeta(k)$. Since $k$ is even, the terms of $(m, n)$ and $(-m, -n)$ are equal, so the terms with $m \ne 0$ give $2 \sum_{m \ge 1} \sum_{n \in \mathbb{Z}} (m\tau + n)^{-k}$. By Lemma 1.2.10 applied to $m\tau$, this is
$$2 \frac{(2\pi i)^k}{(k-1)!} \sum_{m \ge 1} \sum_{r \ge 1} r^{k-1} q^{mr} = \frac{2 (2\pi i)^k}{(k-1)!} \sum_{n \ge 1} \sigma_{k-1}(n) q^n,$$
where we used $(-1)^k = 1$ and grouped the terms with $mr = n$. The double series converges absolutely, so the grouping is allowed. The $q$-expansion shows that $G_k$ is bounded on $\{\mathrm{Im}\,\tau \ge 1\}$. Since $SL_2(\mathbb{Z})$ has only the cusp $\infty$, and $G_k|\alpha = G_k$ for each $\alpha \in SL_2(\mathbb{Z})$ by Proposition 1.2.9, $G_k$ is holomorphic at the cusps. The formula for $E_k$ follows from Euler's formula: $\frac{2(2\pi i)^k}{(k-1)!} \cdot \frac{1}{2\zeta(k)} = \frac{(2\pi i)^k}{(k-1)!} \cdot \frac{-2 \cdot k!}{(2\pi i)^k B_k} = -\frac{2k}{B_k}$. $\square$

With $B_4 = -1/30$, $B_6 = 1/42$, $B_8 = -1/30$, $B_{10} = 5/66$ and $B_{12} = -691/2730$ we get
$$E_4 = 1 + 240 \sum_{n \ge 1} \sigma_3(n) q^n, \qquad E_6 = 1 - 504 \sum_{n \ge 1} \sigma_5(n) q^n,$$
$$E_8 = 1 + 480 \sum_{n \ge 1} \sigma_7(n) q^n, \qquad E_{10} = 1 - 264 \sum_{n \ge 1} \sigma_9(n) q^n, \qquad E_{12} = 1 + \frac{65520}{691} \sum_{n \ge 1} \sigma_{11}(n) q^n.$$
The prime 691 in $E_{12}$ is the start of Ramanujan's congruence $\tau(n) \equiv \sigma_{11}(n) \bmod 691$, see Exercise 6.

For $k = 2$ the series of Proposition 1.2.9 does not converge absolutely. The function $E_2 = 1 - 24 \sum \sigma_1(n) q^n$ is holomorphic on $\mathbb{H}$, but it is not a modular form: one has $E_2(-1/\tau) = \tau^2 E_2(\tau) + \frac{12\tau}{2\pi i}$. For each $N \ge 2$ the function $E_2(\tau) - N E_2(N\tau)$ is a modular form of weight 2 for $\Gamma_0(N)$. See Diamond and Shurman, Chapter 1, for these facts. We do not use them.

### The discriminant

**Definition 1.2.12 (the discriminant).** The *discriminant* is
$$\Delta = \frac{E_4^3 - E_6^2}{1728} = \sum_{n \ge 1} \tau(n) q^n.$$
The coefficients $\tau(n)$ form the *Ramanujan function*.

**Proposition 1.2.13 (the discriminant is a cusp form).** The function $\Delta$ is a nonzero cusp form of weight 12 for $SL_2(\mathbb{Z})$. Its coefficients $\tau(n)$ are integers, and
$$\Delta = q - 24 q^2 + 252 q^3 - 1472 q^4 + 4830 q^5 - 6048 q^6 - 16744 q^7 + 84480 q^8 + \cdots.$$

Lean: not stated yet

*Proof.* The function $E_4^3 - E_6^2$ is in $M_{12}(SL_2(\mathbb{Z}))$, and its constant term is $1 - 1 = 0$. So it is a cusp form. Write $E_4 = 1 + 240 A$ and $E_6 = 1 - 504 B$ with $A = \sum \sigma_3(n) q^n$ and $B = \sum \sigma_5(n) q^n$. Then
$$\frac{E_4^3 - E_6^2}{1728} = \frac{5A + 7B}{12} + 100 A^2 + 8000 A^3 - 147 B^2,$$
because $3 \cdot 240 = 5 \cdot 144$, $2 \cdot 504 = 7 \cdot 144$, $3 \cdot 240^2 = 100 \cdot 1728$, $240^3 = 8000 \cdot 1728$ and $504^2 = 147 \cdot 1728$. The coefficient of $q^n$ in $5A + 7B$ is $\sum_{d \mid n} d^3 (5 + 7d^2)$. Each term is divisible by 12. Modulo 4, either $d$ is even and $d^3 \equiv 0$, or $d$ is odd and $5 + 7d^2 \equiv 12 \equiv 0$. Modulo 3, either $3 \mid d$, or $d^2 \equiv 1$ and $5 + 7d^2 \equiv 0$. So all coefficients are integers. The coefficient of $q$ is $(5 + 7)/12 = 1$, so $\Delta \ne 0$. The other coefficients are a direct computation. $\square$

Jacobi's product formula says that $\Delta = q \prod_{n \ge 1} (1 - q^n)^{24}$. Serre proves it in *A course in arithmetic*, Chapter VII, Section 4, and we use it only in examples. Mathlib defines $\Delta$ by the product, as the 24th power of the Dedekind eta function $\eta = q^{1/24} \prod (1 - q^n)$. The statement $\Delta = (E_4^3 - E_6^2)/1728$ is `ModularForm.discriminant_eq_E₄_cube_sub_E₆_sq` in the file `Mathlib/NumberTheory/ModularForms/LevelOne/GradedRing.lean`. Together the two give Jacobi's formula. Proposition 1.3.3 below proves that $\Delta$ has no zero on $\mathbb{H}$, which is clear from the product.

**Example 1.2.14 (a cusp form of level 11).** Let
$$f_{11}(\tau) = \eta(\tau)^2 \eta(11\tau)^2 = q \prod_{n \ge 1} (1 - q^n)^2 (1 - q^{11n})^2 = \sum_{n \ge 1} a_n q^n.$$
The transformation law $\eta(-1/\tau) = \sqrt{\tau/i}\, \eta(\tau)$ and the theory of eta quotients show that $f_{11} \in S_2(\Gamma_0(11))$. A direct expansion of the product gives
$$f_{11} = q - 2q^2 - q^3 + 2q^4 + q^5 + 2q^6 - 2q^7 - 2q^9 - 2q^{10} + q^{11} - 2q^{12} + 4q^{13} + \cdots.$$
Let $E$ be the elliptic curve $y^2 + y = x^3 - x^2 - 10x - 20$ over $\mathbb{Q}$. It has good reduction at each prime $p \ne 11$. Counting the points of $E$ over $\mathbb{F}_p$, including the point at infinity, gives $p + 1 - |E(\mathbb{F}_p)| = -2, -1, 1, -2, 4, -2, 0$ for $p = 2, 3, 5, 7, 13, 17, 19$. These are the coefficients $a_p$ of $f_{11}$. This is the first case of the modularity theorem, Theorem 2.2.11. By Remark 1.3.11 the space $S_2(\Gamma_0(11))$ has dimension 1, so $f_{11}$ spans it.
