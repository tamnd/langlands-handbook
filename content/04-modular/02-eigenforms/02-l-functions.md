---
title: L-functions and modularity
nodes: [LGZ55EK0PA, LGPNZWXVH5, LG5W3CRDEA]
sources: [Wil95, BCDT01]
status: checked
drafted_by: writer
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## L-functions and modularity

This section attaches a Dirichlet series to each cusp form, proves that it has an Euler product when the form is a normalized eigenform, and proves its analytic continuation and functional equation with the Mellin transform. Then it defines the $L$-function of an elliptic curve over $\mathbb{Q}$ and states the modularity theorem, which identifies it with the $L$-function of a newform of weight 2. The Hasse-Weil conjecture for elliptic curves over $\mathbb{Q}$ follows.

### The Dirichlet series of a cusp form

**Proposition 2.2.1 (Hecke's bound).** Let $\Gamma$ be a congruence subgroup that contains $T$, and let $f \in S_k(\Gamma)$ with $q$-expansion $\sum a_n q^n$. There is $C > 0$ with $|a_n| \le C n^{k/2}$ for all $n \ge 1$.

Lean: `CuspFormClass.qExpansion_isBigO`, from Mathlib

*Proof.* For each $y > 0$, $a_n = \int_0^1 f(x + iy) e^{-2\pi i n(x + iy)}\, dx$. By Lemma 1.4.3 there is $B$ with $y^{k/2}|f(x + iy)| \le B$ on $\mathbb{H}$. So $|a_n| \le e^{2\pi n y} B y^{-k/2}$. With $y = 1/n$ this is $|a_n| \le e^{2\pi} B n^{k/2}$. $\square$

This is Exercise 8 of Chapter 1. The Mathlib lemma `CuspFormClass.qExpansion_isBigO`, in the file `Mathlib/NumberTheory/ModularForms/Bounds.lean`, states it for the expansion in $q_h$ of a cusp form for an arithmetic subgroup, as $a_n = O(n^{k/2})$.

**Definition 2.2.2 (the $L$-function of a cusp form).** Let $f \in S_k(\Gamma_1(N))$ with $q$-expansion $\sum a_n q^n$. The *$L$-function* of $f$ is
$$L(f, s) = \sum_{n \ge 1} a_n n^{-s},$$
and the *completed $L$-function* is $\Lambda(f, s) = (2\pi)^{-s}\Gamma(s) L(f, s)$.

By Proposition 2.2.1 the series converges absolutely and uniformly on each half plane $\mathrm{Re}(s) \ge \sigma_0 > k/2 + 1$, so $L(f, s)$ is holomorphic for $\mathrm{Re}(s) > k/2 + 1$.

**Proposition 2.2.3 (Euler product).** Let $f \in S_k(N, \chi)$ be a normalized eigenform. For $\mathrm{Re}(s) > k/2 + 1$,
$$L(f, s) = \prod_p \bigl(1 - a_p p^{-s} + \chi(p) p^{k-1-2s}\bigr)^{-1},$$
and the product converges absolutely. Conversely, if $f \in S_k(N, \chi)$ and $L(f, s)$ is equal to such a product for $\mathrm{Re}(s)$ large, then $f$ is a normalized eigenform.

Lean: not stated yet

*Proof.* Let $\sigma = \mathrm{Re}(s)$. By the identity of power series after Theorem 2.1.3, with $X = p^{-s}$, the factor at $p$ is $\sum_{r \ge 0} a_{p^r} p^{-rs}$. Let $P$ be a finite set of primes. By condition 2 of Theorem 2.1.3, the product of the factors at $p \in P$ is $\sum a_n n^{-s}$ over the $n$ whose prime factors are in $P$; the product of finitely many absolutely convergent series may be expanded. The difference with $L(f, s)$ is at most $\sum_{n \ge m} |a_n| n^{-\sigma}$, where $m$ is the smallest prime not in $P$. It tends to 0 as $P$ grows, by Proposition 2.2.1. The absolute convergence of the product follows in the same way from $\sum_p |a_p p^{-s} - \chi(p)p^{k-1-2s}| < \infty$. For the converse, the Dirichlet coefficients of a series that converges absolutely in a half plane are determined by the series, so the coefficients of $f$ are those of the expanded product, and they satisfy the three conditions of Theorem 2.1.3. $\square$

For $f = \Delta$, the proposition is
$$\sum_{n \ge 1} \tau(n) n^{-s} = \prod_p (1 - \tau(p) p^{-s} + p^{11 - 2s})^{-1},$$
the form in which Ramanujan stated his first two conjectures.

### The functional equation in level one

**Theorem 2.2.4 (Hecke).** Let $k$ be even and $f \in S_k(SL_2(\mathbb{Z}))$. Then $\Lambda(f, s)$ extends to an entire function of $s$, bounded on each vertical strip $a \le \mathrm{Re}(s) \le b$, and
$$\Lambda(f, k - s) = (-1)^{k/2} \Lambda(f, s).$$

Lean: `CuspForm.differentiable_Λ`, `WeakFEPair.functional_equation`, from Mathlib

*Proof.* First let $\mathrm{Re}(s) > k/2 + 1$. For $n \ge 1$ and $\mathrm{Re}(s) > 0$, the substitution $u = 2\pi n y$ in the integral of the $\Gamma$-function gives
$$\int_0^\infty e^{-2\pi n y} y^{s-1}\, dy = (2\pi n)^{-s}\Gamma(s).$$
Multiply by $a_n$ and sum over $n$. The sum of the absolute values is $\sum |a_n| (2\pi n)^{-\sigma}\Gamma(\sigma) < \infty$, with $\sigma = \mathrm{Re}(s)$. So we may exchange the sum and the integral, and since $f(iy) = \sum a_n e^{-2\pi n y}$,
$$\Lambda(f, s) = \int_0^\infty f(iy) y^{s-1}\, dy.$$
This is the Mellin transform of $y \mapsto f(iy)$. Now $f$ is invariant under $S$, so $f(-1/\tau) = \tau^k f(\tau)$, and for $\tau = iy$ this is $f(i/y) = i^k y^k f(iy)$. Split the integral at $y = 1$, and substitute $y \mapsto 1/y$ in the part from 0 to 1:
$$\int_0^1 f(iy) y^{s-1}\, dy = \int_1^\infty f(i/y) y^{-s-1}\, dy = i^k \int_1^\infty f(iy) y^{k-s-1}\, dy.$$
So
$$\Lambda(f, s) = \int_1^\infty f(iy) \bigl(y^{s-1} + i^k y^{k-s-1}\bigr)\, dy.$$
On $y \ge 1$ we have $|f(iy)| \le \sum |a_n| e^{-2\pi n y} \le C e^{-2\pi y}$, where $C = \sum |a_n| e^{-2\pi(n-1)}$. So the last integral converges for every $s$, uniformly on vertical strips, and it defines an entire function that is bounded on each vertical strip. It is equal to $\Lambda(f, s)$ for $\mathrm{Re}(s) > k/2 + 1$. Replace $s$ by $k - s$: the two terms of the integrand are exchanged, and the factor $i^k$ moves from one to the other. Since $(i^k)^2 = 1$ for even $k$, this gives $\Lambda(f, k - s) = i^k \Lambda(f, s) = (-1)^{k/2}\Lambda(f, s)$. $\square$

The function $L(f, s) = (2\pi)^s \Gamma(s)^{-1} \Lambda(f, s)$ is then entire too, because $1/\Gamma$ is entire. For $f = \Delta$ and $k = 12$ the sign is $+1$, so $\Lambda(\Delta, 12 - s) = \Lambda(\Delta, s)$, with the center of symmetry at $s = 6$.

**Remark 2.2.5 (the $L$-function in Mathlib).** The file `Mathlib/NumberTheory/ModularForms/LFunction.lean` defines `ModularForm.Λ` and `ModularForm.L` for a modular form of weight $k > 0$ on an arithmetic subgroup. It builds a pair of functions `ModularForm.weakFEPair`, namely $t \mapsto f(it)$ and $t \mapsto (f|S)(it)$, with the sign $i^k$, and it defines $\Lambda$ as the completed Mellin transform of the abstract theory in `Mathlib/NumberTheory/LSeries/AbstractFuncEq.lean`. For a cusp form, `CuspForm.Λ_eq_mellin` is the formula $\Lambda(f, s) = \int_0^\infty f(iy) y^{s-1}\, dy$ of the proof, `CuspForm.differentiable_Λ` and `CuspForm.differentiable_L` are the analytic continuation, and `CuspForm.hasSum_L` is the series for $\mathrm{Re}(s) > k/2 + 1$. The abstract functional equation `WeakFEPair.functional_equation` gives $\Lambda(f, k - s) = i^k \Lambda(f|S, s)$. In level one $f|S = f$, and this is Theorem 2.2.4. For a subgroup $\Gamma$ of width $h$ at $\infty$, Mathlib uses the expansion in $q_h$, as in Remark 1.2.5.

### The functional equation in level $N$

For $N \ge 1$ let $W_N = \begin{pmatrix} 0 & -1 \\ N & 0 \end{pmatrix}$. For $\gamma = \begin{pmatrix} a & b \\ c & d \end{pmatrix} \in \Gamma_0(N)$ a direct computation gives
$$W_N \gamma W_N^{-1} = \begin{pmatrix} d & -c/N \\ -Nb & a \end{pmatrix} \in \Gamma_0(N).$$
So $W_N$ normalizes $\Gamma_0(N)$.

**Definition 2.2.6 (the Atkin-Lehner operator).** For $f \in S_k(\Gamma_0(N))$, let
$$(w_N f)(\tau) = N^{1 - k/2} (f|_k W_N)(\tau) = N^{-k/2} \tau^{-k} f\Bigl(-\frac{1}{N\tau}\Bigr).$$

By the computation above and Lemma 1.2.7, $w_N f \in S_k(\Gamma_0(N))$. Applying the formula twice gives $w_N^2 f = (-1)^k f$. For even $k$, $w_N$ is an involution, so $S_k(\Gamma_0(N))$ is the direct sum of the eigenspaces of $w_N$ for the eigenvalues $+1$ and $-1$. For $N = 1$, $w_1 f = f|_k S = f$.

**Theorem 2.2.7 (Hecke, level $N$).** Let $k$ be even, let $f \in S_k(\Gamma_0(N))$ and assume $w_N f = \varepsilon f$ with $\varepsilon = \pm 1$. Let
$$\Lambda_N(f, s) = N^{s/2} (2\pi)^{-s} \Gamma(s) L(f, s).$$
Then $\Lambda_N(f, s)$ extends to an entire function of $s$, bounded on vertical strips, and
$$\Lambda_N(f, k - s) = \varepsilon\, i^k\, \Lambda_N(f, s).$$
Each newform $f$ on $\Gamma_0(N)$ satisfies $w_N f = \pm f$.

Lean: not stated yet

*Proof.* As in the proof of Theorem 2.2.4, $\Lambda_N(f, s) = N^{s/2}\int_0^\infty f(iy) y^{s-1}\, dy$ for $\mathrm{Re}(s) > k/2 + 1$. Substitute $y = t/\sqrt{N}$. Then $\Lambda_N(f, s) = \int_0^\infty F(t) t^{s-1}\, dt$ with $F(t) = f(it/\sqrt{N})$. The condition $w_N f = \varepsilon f$ at $\tau = it/\sqrt{N}$ reads $F(1/t) = \varepsilon i^k t^k F(t)$. This is the relation of the level one case with the extra factor $\varepsilon$, and the proof of Theorem 2.2.4 applies word for word. Since $(\varepsilon i^k)^2 = 1$, it gives $\Lambda_N(f, k - s) = \varepsilon i^k \Lambda_N(f, s)$.

For the last claim, let $f$ be a newform on $\Gamma_0(N)$. For primes $p \nmid N$ the operator $w_N$ commutes with $T_p$ on $S_k(\Gamma_0(N))$; this follows from the description of $T_p$ by the matrices of determinant $p$, because $W_N$ normalizes this set of matrices up to $\Gamma_0(N)$. Also $w_N$ preserves the old space, since it sends $g(d\tau)$ to a multiple of $g'(d'\tau)$ with $dd' = N/M$ and $g' = w_M g$, and it preserves the Petersson product, so it preserves the new space. So $w_N f$ is a form in the new space with the same eigenvalues as $f$ for the $T_p$ with $p \nmid N$. By part 2 of Theorem 2.1.8, $w_N f = \varepsilon f$ for a scalar $\varepsilon$, and $\varepsilon^2 = 1$. $\square$

### Elliptic curves

Let $E$ be an elliptic curve over $\mathbb{Q}$, given by a minimal Weierstrass equation with integer coefficients. For each prime $p$ the reduction $\tilde{E}$ of the equation modulo $p$ is a curve over $\mathbb{F}_p$. If it is smooth, $E$ has *good reduction* at $p$. Otherwise $\tilde{E}$ has one singular point, a node or a cusp. At a node $E$ has *multiplicative reduction*, *split* if the two tangent lines at the node are defined over $\mathbb{F}_p$ and *nonsplit* otherwise. At a cusp $E$ has *additive reduction*. The curve is *semistable* if it has no prime of additive reduction.

**Definition 2.2.8 (the $L$-function of an elliptic curve).** Let $a_p(E) = p + 1 - |\tilde{E}(\mathbb{F}_p)|$ if $E$ has good reduction at $p$, where $\tilde{E}(\mathbb{F}_p)$ includes the point at infinity. Let $a_p(E) = 1$, $-1$ or $0$ if $E$ has split multiplicative, nonsplit multiplicative or additive reduction at $p$. The *$L$-function* of $E$ is
$$L(E, s) = \prod_{p \text{ good}} \bigl(1 - a_p(E) p^{-s} + p^{1 - 2s}\bigr)^{-1} \prod_{p \text{ bad}} \bigl(1 - a_p(E) p^{-s}\bigr)^{-1} = \sum_{n \ge 1} a_n(E) n^{-s}.$$
The *conductor* of $E$ is $N_E = \prod_p p^{f_p}$, where $f_p = 0$ at good primes, $f_p = 1$ at multiplicative primes, and $f_p \ge 2$ at additive primes, with $f_p = 2$ for $p \ge 5$.

Lean: `WeierstrassCurve.LFunction`, from Mathlib

The exponent $f_p$ at an additive prime $p = 2$ or $3$ is given by Ogg's formula; we do not need it. A curve is semistable if and only if $N_E$ is squarefree. With the convention $\chi(p) = 0$ for $p \mid N_E$, where $\chi$ is the trivial character modulo $N_E$, the local factors of $L(E, s)$ are those of Proposition 2.2.3 for $k = 2$. So the coefficients $a_n(E)$ satisfy the three conditions of Theorem 2.1.3 for $k = 2$ and the level $N_E$.

**Theorem 2.2.9 (Hasse).** Let $E$ have good reduction at $p$. Then $|a_p(E)| \le 2\sqrt{p}$.

Lean: not stated yet

*Proof.* Let $\phi$ be the Frobenius endomorphism $(x, y) \mapsto (x^p, y^p)$ of $\tilde{E}$ over $\bar{\mathbb{F}}_p$. The points of $\tilde{E}(\mathbb{F}_p)$ are the kernel of $1 - \phi$, and $1 - \phi$ is separable, so $|\tilde{E}(\mathbb{F}_p)| = \deg(1 - \phi)$. The degree is a positive definite quadratic form on the lattice $\mathrm{End}(\tilde{E})$, with $\deg \phi = p$. Its associated bilinear form gives $\deg(m - n\phi) = m^2 - tmn + pn^2$ for all integers $m, n$, where $t = 1 + p - \deg(1 - \phi) = a_p(E)$. This value is $\ge 0$ for all $m$ and $n$, so the discriminant $t^2 - 4p$ is $\le 0$. This is Silverman, *The arithmetic of elliptic curves*, Chapter V. $\square$

By Theorem 2.2.9 the product for $L(E, s)$ converges absolutely for $\mathrm{Re}(s) > 3/2$, by the argument of Proposition 2.2.3. In Mathlib, `WeierstrassCurve.LFunction` defines the coefficients $a_n(E)$ from the local factors of a minimal model, including the factors at the bad primes, and the Lean project writes `E.LFunction n` for $a_n(E)$.

### The modularity theorem

**Theorem 2.2.10 (Wiles and Taylor-Wiles).** Let $E$ be a semistable elliptic curve over $\mathbb{Q}$. There are $N \ge 1$ and $f \in S_2(\Gamma_0(N))$ such that $a_n(f) = a_n(E)$ for all $n \ge 1$.

Node: LGZ55EK0PA · Lean: `Langlands.ModularitySemistableQ`

*Outline of the proof.* This is [Wil95, Theorem 0.4], with the result of Taylor and Wiles that completes its proof. Let $\bar\rho_{E,3}$ be the representation of $G_\mathbb{Q}$ on the 3-torsion $E[3]$. Its image is in $GL_2(\mathbb{F}_3)$, a solvable group, and the theorem of Langlands and Tunnell, a case of the Artin conjecture of Section 2.5, shows that $\bar\rho_{E,3}$ comes from a modular form when it is irreducible. Wiles proved that a lifting of a modular residual representation with suitable local properties is again modular; the key step is the identification $R = \mathbb{T}$ of a universal deformation ring with a Hecke algebra, and Taylor and Wiles proved it. The representation on $T_3 E$ is such a lifting, so it is modular, and Section 2.4 turns this into the equality of coefficients. When $\bar\rho_{E,3}$ is reducible, Wiles uses the prime 5 and an auxiliary curve with the same 5-torsion. $\square$

**Theorem 2.2.11 (modularity of elliptic curves over $\mathbb{Q}$).** Let $E$ be an elliptic curve over $\mathbb{Q}$. There are $N \ge 1$ and $f \in S_2(\Gamma_0(N))$ such that $a_n(f) = a_n(E)$ for all $n \ge 1$.

Node: LGPNZWXVH5 · Lean: `Langlands.ModularityEllipticQ`

*Outline of the proof.* This is [BCDT01, Theorem A], by Breuil, Conrad, Diamond and Taylor. After the work of Wiles, Taylor-Wiles, Diamond, and Conrad, Diamond and Taylor, the remaining curves were those whose conductor is divisible by 27. For them the restriction of the representation on $T_3E$ to a decomposition group at 3 is far from semistable. The new input is a description of the local deformation rings at 3, through the theory of finite flat group schemes and Breuil modules. $\square$

**Remark 2.2.12 (the Lean form of modularity).** The Lean statement `Langlands.ModularityEllipticQ` asks for a level $N > 0$ and a cusp form $f$ on $\Gamma_0(N)$ of weight 2 with `Langlands.qCoeff f n = E.LFunction n` for all $n \ge 1$. So it asks for the equality of all the coefficients, at the bad primes too, and not only of the $a_p$ for almost all $p$. It does not fix the level and it does not ask that $f$ be an eigenform. If $f$ works at level $N$, it works at each multiple of $N$. By the theorem of Carayol on the conductors, the smallest level is $N = N_E$, and there $f$ is the newform $f_E$ of level $N_E$. At level $N_E$ the eigenform condition is automatic, by Theorem 2.1.3 and the remark after Definition 2.2.8. At a level $N$ with a prime $p \mid N$, $p \nmid N_E$, the predicate `Langlands.IsNormalizedEigenform f` fails, because `bad` asks $a_{p^2} = a_p^2$, while $a_{p^2}(E) = a_p(E)^2 - p$. So if one adds the eigenform condition to the statement, each prime that divides $N$ divides $N_E$, and the level has no extra primes. The statement `Langlands.ModularitySemistableQ` has the extra hypothesis `IsSemistable`, that $E$ has no additive reduction at any prime. The fidelity theorem `Langlands.Fidelity.modularitySemistableQ_of_modularityEllipticQ` proves in Lean that Theorem 2.2.11 implies Theorem 2.2.10.

**Corollary 2.2.13 (Hasse-Weil for elliptic curves over $\mathbb{Q}$).** Let $E$ be an elliptic curve over $\mathbb{Q}$ of conductor $N$, and let $\Lambda(E, s) = N^{s/2}(2\pi)^{-s}\Gamma(s) L(E, s)$ for $\mathrm{Re}(s) > 3/2$. Then $\Lambda(E, s)$ extends to an entire function, and there is $w \in \{1, -1\}$ with
$$\Lambda(E, 2 - s) = w\, \Lambda(E, s).$$

Node: LG5W3CRDEA · Lean: `Langlands.HasseWeilEllipticQ`

*Proof.* By Theorem 2.2.11 and Remark 2.2.12 there is a newform $f$ of level $N$ and weight 2 with $L(f, s) = L(E, s)$. By Theorem 2.2.7, $w_N f = \varepsilon f$ with $\varepsilon = \pm 1$, and $\Lambda(E, s) = \Lambda_N(f, s)$ extends to an entire function with $\Lambda_N(f, 2 - s) = \varepsilon i^2 \Lambda_N(f, s)$. So $w = -\varepsilon$. $\square$

The number $w$ is the *root number* of $E$. The conjecture of Birch and Swinnerton-Dyer predicts that $w = (-1)^r$, where $r$ is the rank of $E(\mathbb{Q})$. This was the conjecture of Hasse and Weil for elliptic curves over $\mathbb{Q}$, as in the introduction of [BCDT01]. For curves with complex multiplication Deuring proved it in the 1950s with Hecke characters, the theory of Volume 3, Chapter 5.

**Remark 2.2.14 (the Lean form of Hasse-Weil).** The statement `Langlands.HasseWeilEllipticQ` asks for $N > 0$, a sign $\varepsilon \in \{1, -1\}$ and a differentiable function $\Lambda : \mathbb{C} \to \mathbb{C}$ with $\Lambda(s) = N^{s/2}(2\pi)^{-s}\Gamma(s) L(E, s)$ for $\mathrm{Re}(s) > 3/2$ and $\Lambda(2 - s) = \varepsilon \Lambda(s)$ for all $s$. The $L$-series is formed from the coefficients `E.LFunction n`. The level $N$ is existential, as in Remark 2.2.12, and the statement does not say that it is the conductor. With $N$ the conductor the functional equation holds by Corollary 2.2.13. With another $N'$ the function would be $(N'/N)^{s/2}\Lambda(E, s)$, and the functional equation would acquire the factor $(N'/N)^{1-s}$, which is not constant; since $\Lambda(E, s)$ is not identically 0, the equation fails. So the only $N$ that works is the conductor, and the statement is equivalent to Corollary 2.2.13. The Lean project states it and does not prove it from `Langlands.ModularityEllipticQ`; the proof above needs the newforms and the operator $w_N$, which Mathlib does not have.

**Example 2.2.15 (conductor 11).** Let $E$ be the curve $y^2 + y = x^3 - x^2 - 10x - 20$. Its discriminant is $-11^5$, so it has good reduction outside 11. At 11 the reduction has a node with tangents defined over $\mathbb{F}_{11}$, so $a_{11}(E) = 1$ and $N_E = 11$. The form $f_{11} = \eta(\tau)^2\eta(11\tau)^2$ of Example 1.2.14 is the newform of level 11, and the values of $a_p$ in the introduction of this chapter are the first cases of $a_n(f_{11}) = a_n(E)$. The transformation law $\eta(-1/\tau)^2 = (\tau/i)\eta(\tau)^2$, applied to both factors, gives $f_{11}(-1/(11\tau)) = -11\tau^2 f_{11}(\tau)$, so $w_{11} f_{11} = -f_{11}$ and $\varepsilon = -1$. The root number is $w = +1$. This agrees with the rank, which is 0: the group $E(\mathbb{Q})$ is cyclic of order 5.

For a Weierstrass equation $y^2 + a_1xy + a_3y = x^3 + a_2x^2 + a_4x + a_6$ put $b_2 = a_1^2 + 4a_2$, $b_4 = 2a_4 + a_1a_3$ and $c_4 = b_2^2 - 24b_4$. A change of variables $x = u^2x' + r$, $y = u^3y' + su^2x' + t$ gives $\Delta' = u^{-12}\Delta$ and $c_4' = u^{-4}c_4$ (Silverman, Section VII.1). The next lemma is a test for semistability that does not need the minimal model.

**Lemma 2.2.16 (coprime $c_4$ and $\Delta$).** Let $E$ be given by a Weierstrass equation with coefficients in $\mathbb{Z}$, with $\Delta \ne 0$ and $\gcd(c_4, \Delta) = 1$. Then $E$ is semistable.

Lean: `Langlands.Modular.isSemistable_map_of_isCoprime`, with `Langlands.Modular.valuation_le_valuation_minimal` and `Langlands.Modular.not_hasAdditiveReduction_minimal`

*Proof.* Fix a prime $p$ and let $v$ be the valuation of $\mathbb{Q}_p$. Let $\Delta'$ and $c_4'$ belong to a minimal model over $\mathbb{Z}_p$, obtained from the given equation by a change of variables with scale $u$. The given equation is integral, so minimality gives $v(\Delta') \le v(\Delta)$. Since $\Delta' = u^{-12}\Delta$, this gives $v(u) \ge 0$, and then $v(c_4') = v(c_4) - 4v(u) \le v(c_4)$. Since $\gcd(c_4, \Delta) = 1$, the prime $p$ does not divide both, so $v(c_4) = 0$ or $v(\Delta) = 0$. Then $v(c_4') = 0$ or $v(\Delta') = 0$. By Silverman, Proposition VII.5.1, a minimal model has additive reduction exactly when $v(\Delta') > 0$ and $v(c_4') > 0$. So the reduction at $p$ is good or multiplicative. $\square$

The converse is false. A semistable curve can have an equation with $p \mid \gcd(c_4, \Delta)$, for example a model that is not minimal at $p$. The lemma is a sufficient test, and it is the one the Lean file uses, because it needs no computation of the minimal model and no Tate's algorithm.

**Example 2.2.17 (five semistable curves).** The curves 11a1, 14a1, 15a1, 17a1 and 37a1 of the tables of Cremona (*Algorithms for modular elliptic curves*, Table 1) have these equations, discriminants and values of $c_4$:
1. 11a1: $y^2 + y = x^3 - x^2 - 10x - 20$, with $\Delta = -11^5 = -161051$ and $c_4 = 496 = 2^4 \cdot 31$.
2. 14a1: $y^2 + xy + y = x^3 + 4x - 6$, with $\Delta = -2^6 \cdot 7^3 = -21952$ and $c_4 = -215 = -5 \cdot 43$.
3. 15a1: $y^2 + xy + y = x^3 + x^2 - 10x - 10$, with $\Delta = 3^4 \cdot 5^4 = 50625$ and $c_4 = 481 = 13 \cdot 37$.
4. 17a1: $y^2 + xy + y = x^3 - x^2 - x - 14$, with $\Delta = -17^4 = -83521$ and $c_4 = 33 = 3 \cdot 11$.
5. 37a1: $y^2 + y = x^3 - x$, with $\Delta = 37$ and $c_4 = 48 = 2^4 \cdot 3$.

For 14a1, for example, $b_2 = 1$ and $b_4 = 9$, so $c_4 = 1 - 216 = -215$. In each case the primes of $c_4$ do not divide $\Delta$, so Lemma 2.2.16 shows that the curve is semistable, and Theorem 2.2.10 applies. By the tables of Cremona these equations are global minimal models. For a semistable curve the conductor is the product of the primes of bad reduction, so the conductors are 11, 14, 15, 17 and 37. For 11a1 this is Example 2.2.15. In the Lean project, the file `Langlands/Modular/E5Instances.lean` defines the curves over $\mathbb{Q}$ as `Langlands.Modular.E11a1`, `Langlands.Modular.E14a1`, `Langlands.Modular.E15a1`, `Langlands.Modular.E17a1` and `Langlands.Modular.E37a1`, and the same equations over $\mathbb{Z}$ as `Langlands.Modular.E11a1Int` and so on. It computes $\Delta$ and $c_4$ over $\mathbb{Z}$ by `decide`, for example `Langlands.Modular.E11a1Int_Δ` and `Langlands.Modular.E11a1Int_c₄`. It proves the semistability in the sense of `Langlands.IsSemistable` with no hypothesis, as `Langlands.Modular.isSemistable_E11a1` and the four other cases. The modularity is conditional. The theorem `Langlands.Modular.modular_E11a1_of_semistable` takes the statement `Langlands.ModularitySemistableQ` of Theorem 2.2.10 as a hypothesis and gives a cusp form of weight 2 on $\Gamma_0(N)$ with the coefficients of $L(E, s)$. The theorem `Langlands.Modular.modular_E11a1_of_anthropicFLT` gives the same conclusion from the three hypotheses of `Langlands.Bridge.modularitySemistableQ_of_anthropicFLT`. These are `Langlands.Ported.AnthropicFLT.ModularityOfSemistableModel`, the statement of modularity of semistable models in the anthropics port, `Langlands.Bridge.SemistableIntegralModel`, the existence of an integral model that is semistable in the sense of the source, and `Langlands.Bridge.FullCoefficientsOfModular`, the passage from the modularity of the source to the equality of all the coefficients, as in Remark 2.2.12. The other four curves have the same theorems with their names. The file does not prove that the five equations are global minimal models, and it does not compute the conductors. Neither fact is needed for semistability, and the level $N$ in the conclusion is existential, as in Remark 2.2.12.
