---
title: The valence formula and dimensions
nodes: []
sources: []
status: drafted
drafted_by: writer
reviewed_by: []
---
## The valence formula and dimensions

In level one the zeros of a modular form obey one linear relation, the valence formula. It gives all the dimensions of the spaces $M_k(SL_2(\mathbb{Z}))$ and the structure of the graded ring. We follow Serre, *A course in arithmetic*, Chapter VII, Section 3. At the end we prove that the spaces of every level have finite dimension. In this section $M_k$ and $S_k$ mean $M_k(SL_2(\mathbb{Z}))$ and $S_k(SL_2(\mathbb{Z}))$.

**Definition 1.3.1 (orders).** Let $f$ be a nonzero meromorphic function on $\mathbb{H}$ and $p \in \mathbb{H}$. The *order* $v_p(f)$ is the integer $n$ such that $f(\tau)/(\tau - p)^n$ is holomorphic and nonzero at $p$. If $f \in M_k$ is nonzero, its *order at $\infty$* is $v_\infty(f) = \min\{n : a_n(f) \ne 0\}$.

If $f \in M_k$ and $\gamma \in SL_2(\mathbb{Z})$, then $f(\gamma\tau) = (c\tau + d)^k f(\tau)$ and $c\tau + d \ne 0$ on $\mathbb{H}$, so $v_{\gamma p}(f) = v_p(f)$. So $v_p(f)$ depends only on the orbit of $p$. Let $\rho = e^{2\pi i/3}$.

**Theorem 1.3.2 (the valence formula).** Let $k \in \mathbb{Z}$ and let $f \in M_k$ be nonzero. Then
$$v_\infty(f) + \frac{1}{2} v_i(f) + \frac{1}{3} v_\rho(f) + \sum_{p}^{*} v_p(f) = \frac{k}{12},$$
where $\sum^{*}$ is the sum over the orbits of $SL_2(\mathbb{Z})$ on $\mathbb{H}$ other than the orbits of $i$ and $\rho$. The sum is finite.

Lean: not stated yet

*Proof.* The function $f(\tau) = g(q)$ with $g$ holomorphic on the unit disc, by Lemma 1.2.4. The zeros of $g$ do not accumulate at $q = 0$, so there is $T > 1$ such that $f$ has no zero with $\mathrm{Im}\,\tau \ge T$. The part of $\mathcal{D}$ with $\mathrm{Im}\,\tau \le T$ is compact, so it contains only finitely many zeros. By Theorem 1.1.4 each orbit meets $\mathcal{D}$, so the sum is finite.

Assume first that $f$ has no zero on the boundary of $\mathcal{D}$, except possibly at $i$, $\rho$ and $-\bar\rho = \rho + 1$. Let $C$ be the boundary of the region $\{\tau \in \mathcal{D} : \mathrm{Im}\,\tau \le T\}$, oriented counterclockwise, with small arcs of radius $r$ that cut out $\rho$, $i$ and $\rho + 1$ from the region. Then $f$ has no zero on $C$, and by the argument principle
$$\frac{1}{2\pi i} \int_C \frac{f'(\tau)}{f(\tau)} \, d\tau = \sum_{p}^{*} v_p(f)$$
for all small $r$, because each orbit in $\sum^*$ has exactly one point in the interior of $\mathcal{D}$. We compute the integral in pieces.

The top segment runs from $\frac{1}{2} + iT$ to $-\frac{1}{2} + iT$. On it, $q = e^{2\pi i\tau}$ runs once clockwise around the circle $|q| = e^{-2\pi T}$, and $f'(\tau)\, d\tau / f(\tau) = g'(q)\,dq/g(q)$. The function $g$ has no zero in $0 < |q| \le e^{-2\pi T}$ and a zero of order $v_\infty(f)$ at $0$. So the top segment contributes $-v_\infty(f)$.

The two vertical sides are $\mathrm{Re}\,\tau = \pm \frac{1}{2}$. The translation $T$ maps the left side onto the right side, the contour runs up the right side and down the left side, and $f(\tau + 1) = f(\tau)$. So the two contributions cancel.

The arc around $\rho$ has angle tending to $\pi/3$, because the angle of $\mathcal{D}$ at $\rho$ is $\pi/3$, and the contour runs clockwise around $\rho$. Near $\rho$ we have $f'/f = v_\rho(f)/(\tau - \rho) + h(\tau)$ with $h$ holomorphic, so the arc contributes $-\frac{1}{6} v_\rho(f) + O(r)$. In the same way the arc around $\rho + 1$ contributes $-\frac{1}{6} v_{\rho}(f) + O(r)$, since $v_{\rho+1}(f) = v_\rho(f)$, and the arc around $i$, with angle tending to $\pi$, contributes $-\frac{1}{2} v_i(f) + O(r)$.

The rest of $C$ consists of the arc $A$ of the unit circle from $\rho$ to $i$ and the arc $A'$ from $i$ to $\rho + 1$, without the small arcs. The map $S\tau = -1/\tau$ sends $e^{i\theta}$ to $e^{i(\pi - \theta)}$, so it maps $A'$ onto $A$ with the opposite orientation. Let $\omega = f'(\tau)\,d\tau/f(\tau)$. Taking the logarithmic derivative of $f(S\tau) = \tau^k f(\tau)$ gives $S^* \omega = k\, d\tau/\tau + \omega$. So
$$\int_A \omega + \int_{A'} \omega = -\int_{A'} S^*\omega + \int_{A'} \omega = -k \int_{A'} \frac{d\tau}{\tau}.$$
On $A'$ we have $\tau = e^{i\theta}$ with $\theta$ going from $\pi/2$ to $\pi/3$, up to $O(r)$, so $\int_{A'} d\tau/\tau = -i\pi/6 + O(r)$. Divided by $2\pi i$, the two arcs contribute $k/12 + O(r)$.

Adding the pieces and letting $r \to 0$ gives $\sum^* v_p(f) = k/12 - v_\infty(f) - \frac{1}{2}v_i(f) - \frac{1}{3} v_\rho(f)$, which is the formula.

If $f$ has a zero $p$ on the boundary other than $i$, $\rho$ and $\rho + 1$, then $f$ also vanishes at the other boundary point of the orbit, which is $p \pm 1$ or $-1/p$. We change $C$ near the pair by a small arc that goes around $p$ into the interior and by its image under $T$ or $S$ around the other point, so that exactly one point of the pair is inside. The computation is the same. $\square$

The formula has one solution for each weight in a small range, and this gives the spaces of low weight.

**Proposition 1.3.3 (low weights).**
1. $M_k = 0$ if $k < 0$, if $k$ is odd, or if $k = 2$.
2. $M_0 = \mathbb{C}$, and $M_k = \mathbb{C} E_k$ for $k = 4, 6, 8, 10$. In these weights $S_k = 0$.
3. The zeros of $E_4$ are the orbit of $\rho$, simple, and the zeros of $E_6$ are the orbit of $i$, simple.
4. $\Delta$ has no zero on $\mathbb{H}$, and $v_\infty(\Delta) = 1$.

Lean: not stated yet

*Proof.* Let $f \in M_k$ be nonzero. The left side of the valence formula has the form $a + b/2 + c/3$ with integers $a, b, c \ge 0$. So $k \ge 0$. The value $1/6$ is not of this form, so $k \ne 2$. Odd $k$ is excluded by Proposition 1.2.6. If $0 \le k < 12$ and $f$ is a cusp form, then $v_\infty(f) \ge 1 > k/12$, which is impossible. So $S_k = 0$ for $k < 12$. For $k = 0$ and $f \in M_0$, the function $f - a_0(f)$ is a cusp form, so it is 0. For $k = 4, \ldots, 10$ and $f \in M_k$, the function $f - a_0(f) E_k$ is a cusp form, so it is 0. For $k = 4$ the only solution of $a + b/2 + c/3 = 1/3$ is $c = 1$, and for $k = 6$ the only solution of $a + b/2 + c/3 = 1/2$ is $b = 1$. For $\Delta$ we have $k/12 = 1$ and $v_\infty(\Delta) \ge 1$, so $v_\infty(\Delta) = 1$ and all other orders are 0. $\square$

**Theorem 1.3.4 (structure in level one).** Let $k \in \mathbb{Z}$.
1. Multiplication by $\Delta$ is an isomorphism $M_{k-12} \to S_k$.
2. If $k \ge 4$ is even, then $M_k = \mathbb{C} E_k \oplus S_k$.

Lean: not stated yet

*Proof.* For part 1, the product $\Delta g$ with $g \in M_{k-12}$ is in $M_k$ and has $v_\infty \ge 1$, so it is in $S_k$. The map is injective. Let $f \in S_k$. By Proposition 1.3.3, $f/\Delta$ is holomorphic on $\mathbb{H}$, and it satisfies the transformation law of weight $k - 12$. Its $q$-expansion is the quotient of two power series in $q$, and $v_\infty(f) \ge 1 = v_\infty(\Delta)$, so the quotient is a power series. So $f/\Delta \in M_{k-12}$. For part 2, $a_0(E_k) = 1$, and $f - a_0(f) E_k \in S_k$ for $f \in M_k$. $\square$

**Corollary 1.3.5 (the dimension formula).** Let $k \ge 0$ be even. Then
$$\dim M_k = \begin{cases} \lfloor k/12 \rfloor & \text{if } k \equiv 2 \bmod 12, \\ \lfloor k/12 \rfloor + 1 & \text{otherwise.} \end{cases}$$
For $k \ge 4$ even, $\dim S_k = \dim M_k - 1$.

Lean: not stated yet

*Proof.* For $0 \le k < 12$ the formula is Proposition 1.3.3. For $k \ge 12$, Theorem 1.3.4 gives $\dim M_k = 1 + \dim S_k = 1 + \dim M_{k-12}$, and both sides of the formula increase by 1 when $k$ increases by 12. $\square$

So $\dim S_k = 0$ for $k < 12$ and $k = 14$, and $\dim S_k = 1$ for $k = 12, 16, 18, 20, 22, 26$. The first weight with $\dim S_k = 2$ is $k = 24$. In particular $S_{12} = \mathbb{C}\Delta$.

**Corollary 1.3.6 (the graded ring).** For each even $k \ge 0$, the monomials $E_4^a E_6^b$ with $a, b \ge 0$ and $4a + 6b = k$ form a basis of $M_k$. So $\bigoplus_k M_k = \mathbb{C}[E_4, E_6]$, and $E_4$ and $E_6$ are algebraically independent.

Lean: not stated yet

*Proof.* We prove by induction on $k$ that the monomials span $M_k$. This is clear for $k = 0$ and $k = 2$. Let $k \ge 4$ be even. There are $a, b \ge 0$ with $4a + 6b = k$, and $g = E_4^a E_6^b$ has $a_0(g) = 1$. For $f \in M_k$, the function $f - a_0(f) g$ is in $S_k = \Delta M_{k-12}$. By induction $M_{k-12}$ is spanned by monomials, and $\Delta = (E_4^3 - E_6^2)/1728$, so $f$ is in the span.

For the independence, assume that $\sum c_{a,b} E_4^a E_6^b = 0$, summed over the pairs with $4a + 6b = k$. Two such pairs differ by a multiple of $(3, -2)$. Let $(a_1, b_1)$ be the pair with the largest $b$. Dividing by $E_4^{a_1} E_6^{b_1}$ gives $P(x) = 0$, where $x = E_4^3/E_6^2$ and $P$ is a polynomial with the coefficients $c_{a,b}$. The meromorphic function $x$ is not constant, because $x(\rho) = 0$ and $x$ has a pole at $i$ by Proposition 1.3.3. So $x$ takes infinitely many values, and $P = 0$. $\square$

**Example 1.3.7 (an identity for divisor sums).** The space $M_8$ has dimension 1, and both $E_8$ and $E_4^2$ have constant term 1. So $E_8 = E_4^2$. Comparing the coefficients of $q^n$ gives $480 \sigma_7(n) = 480 \sigma_3(n) + 240^2 \sum_{m=1}^{n-1} \sigma_3(m) \sigma_3(n - m)$, that is,
$$\sigma_7(n) = \sigma_3(n) + 120 \sum_{m=1}^{n-1} \sigma_3(m) \sigma_3(n-m).$$
For $n = 2$ both sides are $129$. In the same way $E_4 E_6 = E_{10}$ and $E_4 E_{10} = E_6 E_8 = E_{14}$.

**Proposition 1.3.8 (the $j$-invariant).** The function $j = E_4^3/\Delta$ is holomorphic on $\mathbb{H}$ and invariant under $SL_2(\mathbb{Z})$. It has the expansion $j = q^{-1} + 744 + \cdots$, and it induces a bijection from $SL_2(\mathbb{Z}) \backslash \mathbb{H}$ to $\mathbb{C}$. Also $j(\rho) = 0$ and $j(i) = 1728$.

Lean: not stated yet

*Proof.* The function is holomorphic because $\Delta$ has no zero, and it is invariant because $E_4^3$ and $\Delta$ have the same weight. The expansion follows from $E_4^3 = 1 + 720q + \cdots$ and $\Delta = q(1 - 24q + \cdots)$. Let $\lambda \in \mathbb{C}$ and $f_\lambda = E_4^3 - \lambda\Delta \in M_{12}$. Then $j(\tau) = \lambda$ if and only if $f_\lambda(\tau) = 0$, and $v_\infty(f_\lambda) = 0$. The equation $b/2 + c/3 + \sum^* v_p = 1$ has exactly three solutions in nonnegative integers: $\sum^* v_p = 1$ at one orbit, or $b = 2$, or $c = 3$. In each case $f_\lambda$ vanishes on exactly one orbit. So $j$ takes the value $\lambda$ on exactly one orbit. Finally $E_4(\rho) = 0$, and $E_6(i) = 0$ gives $1728\Delta(i) = E_4(i)^3$. $\square$

**Remark 1.3.9 (the level one theory in Mathlib).** Mathlib proves these results without the valence formula, by an argument on $q$-expansions. The file `Mathlib/NumberTheory/ModularForms/LevelOne/DimensionFormula.lean` contains `CuspForm.discriminantEquiv : CuspForm 𝒮ℒ k ≃ₗ[ℂ] ModularForm 𝒮ℒ (k - 12)`, which is the inverse of the map in Theorem 1.3.4. It also contains `ModularForm.dimension_level_one`, the formula of Corollary 1.3.5 for even $k : ℕ$ as a statement about `Module.rank`, `ModularForm.levelOne_weight_two_rank_zero`, `ModularForm.levelOne_odd_weight_rank_zero`, and the Sturm bound `ModularForm.sturm_bound_levelOne`: a form in $M_k$ whose $q$-expansion has order greater than $k/12$ is zero. The fact that $\Delta$ has no zero is `ModularForm.discriminant_ne_zero`, proved from the product formula.

At a general level we do not compute the dimensions here. We prove only that they are finite. The proof reduces the question to level one by a norm.

**Proposition 1.3.10 (finite dimension).** Let $\Gamma$ be a congruence subgroup with $m = [SL_2(\mathbb{Z}) : \Gamma]$, and let $h$ be the width of the cusp $\infty$ for $\Gamma$. Then $M_k(\Gamma) = 0$ for $k < 0$, and
$$\dim M_k(\Gamma) \le 1 + \frac{hkm}{12}$$
for $k \ge 0$.

Lean: not stated yet

*Proof.* Let $\gamma_1 = I, \gamma_2, \ldots, \gamma_m$ be representatives of the cosets $\Gamma\gamma_i$ in $SL_2(\mathbb{Z})$. For $f \in M_k(\Gamma)$ let $F = \prod_{i} f|_k \gamma_i$. For $\gamma \in SL_2(\mathbb{Z})$ there are a permutation $\sigma$ and elements $\eta_i \in \Gamma$ with $\gamma_i\gamma = \eta_i \gamma_{\sigma(i)}$, so $f|\gamma_i\gamma = f|\gamma_{\sigma(i)}$. For matrices of determinant 1 the slash operator is multiplicative, $(f_1 f_2)|_{k_1+k_2} \gamma = (f_1|_{k_1}\gamma)(f_2|_{k_2}\gamma)$. So $F|_{km}\gamma = F$. Each factor is bounded on $\{\mathrm{Im}\,\tau \ge 1\}$ by Definition 1.2.3 and Lemma 1.2.4, so $F \in M_{km}$. If $f \ne 0$, then $F \ne 0$, because the ring of holomorphic functions on $\mathbb{H}$ has no zero divisors. If $k < 0$, then $M_{km} = 0$ by Proposition 1.3.3, so $f = 0$.

Let $k \ge 0$ and let $r = \lfloor hkm/12 \rfloor + 1$. Consider the linear map that sends $f$ to its first $r$ coefficients in the expansion $f = \sum_n b_n q_h^n$ at $\infty$. Let $f$ be in the kernel. Then $|f(\tau)| \le C |q_h|^{r} = C |q|^{r/h}$ for $\mathrm{Im}\,\tau \ge 1$, and the other factors of $F$ are bounded there. So $|F(\tau)| \le C' |q|^{r/h}$, and $v_\infty(F) \ge r/h > km/12$. By Theorem 1.3.2, $F = 0$, so $f = 0$. The map is injective, and $\dim M_k(\Gamma) \le r$. $\square$

**Remark 1.3.11 (dimensions at higher level).** The exact dimensions at level $N$ come from the geometry of the modular curve $X(\Gamma)$ of Remark 1.1.11. Diamond and Shurman, Chapter 3, prove that $\dim S_2(\Gamma) = g$, the genus of $X(\Gamma)$, and give the formula
$$g(X_0(N)) = 1 + \frac{\mu}{12} - \frac{\nu_2}{4} - \frac{\nu_3}{3} - \frac{\nu_\infty}{2},$$
where $\mu = [SL_2(\mathbb{Z}) : \Gamma_0(N)]$, $\nu_2$ and $\nu_3$ are the numbers of orbits of elliptic points of order 2 and 3, and $\nu_\infty$ is the number of cusps. For $N = 11$ we have $\mu = 12$ and $\nu_\infty = 2$ by Example 1.1.10. Also $\nu_2 = 1 + \left(\frac{-1}{11}\right) = 0$ and $\nu_3 = 1 + \left(\frac{-3}{11}\right) = 0$, because $-1$ and $-3$ are not squares modulo 11. So $g(X_0(11)) = 1$, and $S_2(\Gamma_0(11)) = \mathbb{C} f_{11}$ with $f_{11}$ as in Example 1.2.14. The bound of Proposition 1.3.10 gives only $\dim M_2(\Gamma_0(11)) \le 3$.
