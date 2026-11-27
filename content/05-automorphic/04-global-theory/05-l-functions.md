---
title: The L-function and the functional equation
nodes: []
sources: [JL70, BH06]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## The L-function and the functional equation

Jacquet and Langlands attach to each irreducible admissible representation $\pi_v$ of $G_v$ a local $L$-factor $L(s, \pi_v)$ and a local $\varepsilon$-factor $\varepsilon(s, \pi_v, \psi_v)$. For a cuspidal automorphic representation the product of the local factors is an entire function with a functional equation. This section proves the functional equation from the Hecke integral, assuming the local theory of Chapter 3, and identifies the result for a newform with the theorem of Hecke in Volume 4.

### Local factors

Put $\Gamma_\mathbb{R}(s) = \pi^{-s/2}\Gamma(s/2)$ and $\Gamma_\mathbb{C}(s) = 2(2\pi)^{-s}\Gamma(s)$.

**Definition 4.5.1 (local $L$-factors).** Let $p$ be a prime and $\pi_p$ an irreducible admissible infinite-dimensional representation of $G_p$.
1. If $\pi_p = \chi_1 \times \chi_2$ is a principal series, $L(s, \pi_p) = L(s, \chi_1)L(s, \chi_2)$, where $L(s, \chi) = (1 - \chi(p)p^{-s})^{-1}$ for $\chi$ unramified and $L(s, \chi) = 1$ for $\chi$ ramified. In particular, for an unramified $\pi_p$ with Satake parameters $\alpha, \beta$, $L(s, \pi_p) = (1 - \alpha p^{-s})^{-1}(1 - \beta p^{-s})^{-1}$.
2. If $\pi_p = \mu\mathrm{St}$, then $L(s, \pi_p) = L(s + 1/2, \mu)$.
3. If $\pi_p$ is supercuspidal, then $L(s, \pi_p) = 1$.

At the real place, $L(s, D_k) = \Gamma_\mathbb{C}(s + (k-1)/2)$ for $k \ge 2$.

For a global representation $\pi = \bigotimes'_v\pi_v$ we write $L(s, \pi_f) = \prod_pL(s, \pi_p)$ for the finite part and $\Lambda(s, \pi) = L(s, \pi_\infty)L(s, \pi_f)$ for the completed function. With the unitary normalization, the finite part converges absolutely for $\mathrm{Re}(s) > 3/2$ when $\pi$ is cuspidal, by the bound $p^{-1/2} < |\alpha_p| < p^{1/2}$ of Proposition 4.7.3. Deligne's theorem moves this to $\mathrm{Re}(s) > 1$ in the holomorphic case.

The factors of Definition 4.5.1 are the greatest common divisors of the local zeta integrals. For $W$ in the Whittaker model $\mathcal{W}(\pi_v, \psi_v)$ put
$$Z(s, W) = \int_{\mathbb{Q}_v^\times}W(a(y))|y|^{s - 1/2}\,d^\times y, \qquad \tilde{Z}(s, W) = \int_{\mathbb{Q}_v^\times}W(a(y))\omega_v^{-1}(y)|y|^{s - 1/2}\,d^\times y,$$
where $\omega_v$ is the central character and $d^\times y$ gives $\mathbb{Z}_p^\times$ the volume 1. The contragredient $\tilde\pi_v$ is isomorphic to $\omega_v^{-1} \otimes \pi_v$ (Chapter 3), so $\tilde{Z}$ is the zeta integral of $\tilde\pi_v$ evaluated on the function $g \mapsto W(g)\omega_v^{-1}(\det g)$ of $\mathcal{W}(\tilde\pi_v, \psi_v)$.

**Theorem 4.5.2 (local functional equation, Jacquet and Langlands).** Let $\pi_v$ be an irreducible admissible infinite-dimensional representation of $G_v$.
1. The integrals $Z(s, W)$ converge for $\mathrm{Re}(s)$ large. For $v = p$ finite, the quotients $Z(s, W)/L(s, \pi_p)$ are polynomials in $p^{s}$ and $p^{-s}$, and they span $\mathbb{C}[p^s, p^{-s}]$. For $v = \infty$, the quotients are entire, and a finite sum of them is $1$.
2. There is a function $\varepsilon(s, \pi_v, \psi_v)$ of the form $cq^{-ms}$, with $c \in \mathbb{C}^\times$ and $m \in \mathbb{Z}$ at a finite place and a constant at the real place, such that for each $W \in \mathcal{W}(\pi_v, \psi_v)$
$$\frac{\tilde{Z}(1 - s, \pi_v(w)W)}{L(1 - s, \tilde\pi_v)} = \varepsilon(s, \pi_v, \psi_v)\frac{Z(s, W)}{L(s, \pi_v)}.$$

Lean: not formalized

This is in [JL70], Chapter I; see also Chapter 3 and [Bum97], Chapter 4. If $\pi_p$ is unramified and $\psi_p$ has conductor $\mathbb{Z}_p$, then $\varepsilon(s, \pi_p, \psi_p) = 1$. If $\pi_p$ has conductor exponent $c(\pi_p)$, then $\varepsilon(s, \pi_p, \psi_p) = \varepsilon(1/2, \pi_p, \psi_p)p^{c(\pi_p)(1/2 - s)}$, which is Volume 6, Definition 2.4.6. Some sources write $w^{-1} = -w$ in place of $w$, which multiplies the local factor by $\omega_v(-1)$ and does not change the global product, since $\omega(-1) = 1$.

### The unramified computation

**Proposition 4.5.3 (the spherical Whittaker function).** Let $\pi_p$ be an unramified principal series with Satake parameters $\alpha \ne \beta$, let $\psi_p$ have conductor $\mathbb{Z}_p$, and let $W^\circ \in \mathcal{W}(\pi_p, \psi_p)$ be nonzero and fixed by $K_p$. Then $W^\circ(1) \ne 0$, and with $W^\circ(1) = 1$,
$$W^\circ(a(p^r)) = \begin{cases} p^{-r/2}\dfrac{\alpha^{r+1} - \beta^{r+1}}{\alpha - \beta} & r \ge 0, \\ 0 & r < 0, \end{cases}$$
and $W^\circ(a(yu)) = W^\circ(a(y))$ for $u \in \mathbb{Z}_p^\times$. When $\alpha = \beta$ the same formula holds with $(\alpha^{r+1} - \beta^{r+1})/(\alpha - \beta) = (r + 1)\alpha^r$. In all cases $Z(s, W^\circ) = L(s, \pi_p)$.

Lean: not formalized

*Proof.* Since $a(u) \in K_p$ for $u \in \mathbb{Z}_p^\times$, $W^\circ(a(yu)) = W^\circ(a(y))$. For $x \in \mathbb{Z}_p$, $n(x) \in K_p$ and $a(y)n(x) = n(yx)a(y)$, so
$$W^\circ(a(y)) = W^\circ(a(y)n(x)) = \psi_p(yx)W^\circ(a(y)).$$
If $|y| > 1$, some $x \in \mathbb{Z}_p$ has $\psi_p(yx) \ne 1$, so $W^\circ(a(y)) = 0$. Now apply $T_p$ with Lemma 4.2.5. Since $W^\circ$ is fixed by $K_p$, $\pi(T_p)W^\circ = p^{1/2}(\alpha + \beta)W^\circ$ by Proposition 4.2.6. At $a(p^r)$, using $a(p^r)n(b)a(p) = n(p^rb)a(p^{r+1})$ and $\mathrm{diag}(1, p) = p\cdot a(p^{-1})$,
$$p^{1/2}(\alpha + \beta)W^\circ(a(p^r)) = \sum_{b = 0}^{p-1}\psi_p(p^rb)W^\circ(a(p^{r+1})) + \alpha\beta\,W^\circ(a(p^{r-1})).$$
For $r \ge 0$ the sum is $pW^\circ(a(p^{r+1}))$. Put $c_r = p^{r/2}W^\circ(a(p^r))$, so that $c_{-1} = 0$. Multiplying by $p^{(r-1)/2}$ gives
$$(\alpha + \beta)c_r = c_{r+1} + \alpha\beta\,c_{r-1} \qquad (r \ge 0).$$
This recursion, with $c_{-1} = 0$, has the unique solution $c_r = c_0(\alpha^{r+1} - \beta^{r+1})/(\alpha - \beta)$, as one checks by induction. If $c_0 = W^\circ(1)$ were $0$, then $W^\circ(a(y)) = 0$ for all $y$. By the Iwasawa decomposition every element of $G_p$ is $n(x)z\,a(y)k$ with $z$ central and $k \in K_p$, and $W^\circ(n(x)za(y)k) = \psi_p(x)\omega_p(z)W^\circ(a(y))$, so $W^\circ = 0$. So $c_0 \ne 0$. Finally, with $X = p^{-s}$,
$$Z(s, W^\circ) = \sum_{r \ge 0}W^\circ(a(p^r))p^{-r(s - 1/2)} = \sum_{r \ge 0}\frac{\alpha^{r+1} - \beta^{r+1}}{\alpha - \beta}X^r = \frac{1}{(1 - \alpha X)(1 - \beta X)},$$
the generating function of the complete homogeneous symmetric polynomials in $\alpha, \beta$. $\square$

This is the case $n = 2$ of the formula of Shintani and of Casselman and Shalika. For $\pi_p = \pi_{f,p}$ with $f$ a newform, $p^{r(k-1)/2}c_r/c_0$ is the coefficient $a_{p^r}(f)$, and the recursion is the relation $a_pa_{p^r} = a_{p^{r+1}} + p^{k-1}a_{p^{r-1}}$ of Volume 4.

### The Hecke integral

Let $\pi$ be a cuspidal automorphic representation with central character $\omega$ and $\phi \in V_\pi$. Its *Hecke integral* is
$$Z(s, \phi) = \int_{\mathbb{Q}^\times \backslash \mathbb{A}^\times}\phi(a(y))|y|^{s - 1/2}\,d^\times y, \qquad \tilde{Z}(s, \phi) = \int_{\mathbb{Q}^\times \backslash \mathbb{A}^\times}\phi(a(y))\omega^{-1}(y)|y|^{s - 1/2}\,d^\times y.$$

**Lemma 4.5.4 (the Hecke integral).** The integrals $Z(s, \phi)$ and $\tilde{Z}(s, \phi)$ converge for all $s$ and define entire functions, bounded in vertical strips. They satisfy
$$Z(s, \phi) = \tilde{Z}(1 - s, \pi(w)\phi).$$
If $W_\phi = \prod_vW_v$, then for $\mathrm{Re}(s)$ large $Z(s, \phi) = \prod_vZ(s, W_v)$ and $\tilde{Z}(s, \phi) = \prod_v\tilde{Z}(s, W_v)$.

Lean: not formalized

*Proof.* In $GL_2(\mathbb{A})$ we have $w\,a(y) = z(y)\,a(y^{-1})\,w$, where $z(y)$ is the scalar matrix $y$: both sides equal $\begin{pmatrix} 0 & 1 \\ -y & 0 \end{pmatrix}$. Since $\phi$ is left invariant under $w \in GL_2(\mathbb{Q})$,
$$\phi(a(y)) = \phi(w\,a(y)) = \omega(y)\,(\pi(w)\phi)(a(y^{-1})).$$
A cusp form is rapidly decreasing: $\phi(a(y))$ is $O(|y|^{-M})$ for every $M$ as $|y| \to \infty$, uniformly on $\mathbb{Q}^\times \backslash \mathbb{A}^\times$ with $|y|$ fixed (Chapter 2). The identity applied to $\pi(w)\phi$ gives the decay as $|y| \to 0$. So the integrals converge for all $s$, uniformly in vertical strips, and they are entire and bounded in strips. The substitution $y \mapsto y^{-1}$ in the identity gives
$$Z(s, \phi) = \int\omega(y)(\pi(w)\phi)(a(y^{-1}))|y|^{s - 1/2}\,d^\times y = \int\omega^{-1}(y)(\pi(w)\phi)(a(y))|y|^{1/2 - s}\,d^\times y = \tilde{Z}(1 - s, \pi(w)\phi).$$
For the factorization, insert the Fourier-Whittaker expansion and unfold the sum over $\xi \in \mathbb{Q}^\times$ with the integral over $\mathbb{Q}^\times \backslash \mathbb{A}^\times$:
$$Z(s, \phi) = \int_{\mathbb{Q}^\times \backslash \mathbb{A}^\times}\sum_{\xi \in \mathbb{Q}^\times}W_\phi(a(\xi y))|y|^{s - 1/2}\,d^\times y = \int_{\mathbb{A}^\times}W_\phi(a(y))|y|^{s - 1/2}\,d^\times y = \prod_vZ(s, W_v).$$
The exchange of sum and integral is justified for $\mathrm{Re}(s)$ large by the bound on $W_v$ at the unramified places that follows from Proposition 4.5.3 and Proposition 4.7.3. The integral over $\mathbb{A}^\times$ is the product of the local integrals, since $W_\phi(a(y)) = \prod_vW_v(a(y_v))$ and $W_p(a(y_p)) = 1$ for $y_p \in \mathbb{Z}_p^\times$ at almost all $p$. $\square$

**Theorem 4.5.5 (the functional equation, Jacquet and Langlands).** Let $\pi$ be a cuspidal automorphic representation of $GL_2(\mathbb{A})$. Then $\Lambda(s, \pi)$ extends to an entire function of $s$, bounded in vertical strips, and
$$\Lambda(s, \pi) = \varepsilon(s, \pi)\Lambda(1 - s, \tilde\pi), \qquad \varepsilon(s, \pi) = \prod_v\varepsilon(s, \pi_v, \psi_v).$$
The function $\varepsilon(s, \pi)$ is $\varepsilon(1/2, \pi)N(\pi)^{1/2 - s}$, where $N(\pi) = \prod_p p^{c(\pi_p)}$, and it does not depend on the choice of the nontrivial character $\psi$ of $\mathbb{A}/\mathbb{Q}$.

Lean: not formalized

*Proof.* Let $S$ be a finite set of places that contains $\infty$ and the primes where $\pi$ is ramified; the standard $\psi_p$ has conductor $\mathbb{Z}_p$ for every $p$. Take $\phi$ with $W_\phi = \prod_vW_v$, where $W_v = W_v^\circ$ is the spherical function of Proposition 4.5.3 for $v \notin S$ and $W_v$ is arbitrary for $v \in S$. For $v \notin S$ the element $w$ lies in $K_v$, so $\pi_v(w)W_v^\circ = W_v^\circ$, and $\tilde{Z}(s, W_v^\circ) = L(s, \tilde\pi_v)$ by Proposition 4.5.3 applied to $\tilde\pi_v$, with parameters $\alpha^{-1}, \beta^{-1}$. Lemma 4.5.4 gives
$$L^S(s, \pi)\prod_{v \in S}Z(s, W_v) = L^S(1 - s, \tilde\pi)\prod_{v \in S}\tilde{Z}(1 - s, \pi_v(w)W_v),$$
with $L^S$ the partial product over $v \notin S$. Divide by $\Lambda(s, \pi)$ and insert the local functional equations of Theorem 4.5.2 at $v \in S$:
$$\prod_{v \in S}\frac{Z(s, W_v)}{L(s, \pi_v)}\cdot\frac{\Lambda(s, \pi)}{\Lambda(1 - s, \tilde\pi)} = \prod_{v \in S}\frac{\tilde{Z}(1 - s, \pi_v(w)W_v)}{L(1 - s, \tilde\pi_v)} = \prod_{v \in S}\varepsilon(s, \pi_v, \psi_v)\frac{Z(s, W_v)}{L(s, \pi_v)}.$$
Choose the $W_v$ so that the product $\prod_{v \in S}Z(s, W_v)/L(s, \pi_v)$ is not identically zero. Then $\Lambda(s, \pi) = \varepsilon(s, \pi)\Lambda(1 - s, \tilde\pi)$ as meromorphic functions, since $\varepsilon(s, \pi_v, \psi_v) = 1$ for $v \notin S$. By Theorem 4.5.2, part 1, there is a finite sum of such $\phi$, with local functions at $v \in S$, for which $\sum\prod_{v \in S}Z(s, W_v) = \prod_{v \in S}L(s, \pi_v)$. For this sum $\Lambda(s, \pi)$ is the corresponding sum of the functions $Z(s, \phi)$, so it is entire and bounded in vertical strips by Lemma 4.5.4. The form $\varepsilon(1/2, \pi)N(\pi)^{1/2 - s}$ follows from the local form $\varepsilon(s, \pi_p, \psi_p) = \varepsilon(1/2, \pi_p, \psi_p)p^{c(\pi_p)(1/2 - s)}$ and the fact that $\varepsilon(s, \pi_\infty, \psi_\infty)$ is constant. Another nontrivial character of $\mathbb{A}/\mathbb{Q}$ is $\psi(a\,\cdot)$ with $a \in \mathbb{Q}^\times$. By the change of character formula of Volume 0, Remark 3.2.1, the local factor changes by $\omega_v(a)|a|_v^{2s - 1}$, and the product of these numbers over $v$ is $1$ by the product formula and $\omega(a) = 1$. $\square$

The proof is the one of [JL70], Chapter II, and of [Bum97], Chapter 3. It is an adelic version of Hecke's proof in Volume 4. The identity $Z(s, \phi) = \tilde{Z}(1 - s, \pi(w)\phi)$ is the transformation law under $\tau \mapsto -1/\tau$, and the local functional equations replace the explicit computation of the Mellin transform.

### The case of a newform

**Proposition 4.5.6 ($L$-functions of newforms).** Let $f$ be a newform of even weight $k \ge 2$ and level $N$ with trivial character, and put $s' = s + (k-1)/2$. Then for every prime $p$ the Euler factor of $L(f, s')$ at $p$ is $L(s, \pi_{f,p})$, so $L(s, \pi_{f,f}) = L(f, s')$, where $\pi_{f,f}$ is the finite part of $\pi_f$. In addition,
$$\Lambda(s, \pi_f) = \Gamma_\mathbb{C}(s')L(f, s') = 2(2\pi)^{-s'}\Gamma(s')L(f, s').$$

Lean: not formalized

*Proof.* At $p \nmid N$ the factor of $L(f, s')$ is $(1 - a_pp^{-s'} + p^{k-1-2s'})^{-1}$, and $p^{-s'} = p^{-(k-1)/2}p^{-s}$, $p^{k - 1 - 2s'} = p^{-2s}$. By Remark 4.2.7 this is $(1 - (\alpha_p + \beta_p)p^{-s} + p^{-2s})^{-1} = L(s, \pi_{f,p})$. Now compute the Hecke integral of $\phi_f$ directly. The quotient $\mathbb{Q}^\times \backslash \mathbb{A}^\times$ is $\mathbb{R}_{>0} \times \hat{\mathbb{Z}}^\times$. For $u \in \hat{\mathbb{Z}}^\times$, $a(u) \in K_0(N)$, so $\phi_f(a(y_\infty u)) = \phi_f(a(y_\infty)) = y_\infty^{k/2}f(iy_\infty)$ for $y_\infty > 0$. So
$$Z(s, \phi_f) = \int_0^\infty y^{k/2}f(iy)y^{s - 1/2}\,\frac{dy}{y} = \int_0^\infty f(iy)y^{s'}\,\frac{dy}{y} = (2\pi)^{-s'}\Gamma(s')L(f, s'),$$
by the Mellin transform of Volume 4, Section 2.2. On the other side, $\phi_f$ is the tensor product of the local newforms and of the weight $k$ vector at infinity (Step 5 of the proof of Theorem 4.3.3), so $W_{\phi_f} = c\prod_vW_v$ with $W_p$ the local newform and $c \ne 0$. By the theory of local newforms (Chapter 3), $W_p(1) \ne 0$, and normalized by $W_p(1) = 1$ it satisfies $Z(s, W_p) = L(s, \pi_{f,p})$. At infinity a direct computation with the Whittaker function $|y|^{k/2}e^{-2\pi|y|}$ of the weight $k$ vector, supported on a half line, gives $Z(s, W_\infty) = c'\Gamma_\mathbb{C}(s')$ with $c' \ne 0$. By Lemma 4.5.4,
$$(2\pi)^{-s'}\Gamma(s')L(f, s') = cc'\,\Gamma_\mathbb{C}(s')\prod_pL(s, \pi_{f,p}).$$
Cancel the Gamma factors and the factors at $p \nmid N$. What remains is $\prod_{p \mid N}(1 - a_pp^{-s'})^{-1} = C\prod_{p \mid N}L(s, \pi_{f,p})$ for a constant $C$. Comparing constant terms gives $C = 1$, and a finite Euler product determines its factors, so the factors agree at each $p \mid N$. $\square$

**Corollary 4.5.7 (the $\varepsilon$-factor of a newform).** Let $f$ be as in Proposition 4.5.6 and let $w_Nf = \varepsilon_Nf$ with the Atkin-Lehner operator of Volume 4, Definition 2.2.6. Then $\tilde\pi_f \cong \pi_f$ and
$$\varepsilon(s, \pi_f) = i^k\varepsilon_NN^{1/2 - s}.$$
In particular $N(\pi_f) = N$ and the root number is $\varepsilon(1/2, \pi_f) = i^k\varepsilon_N$.

Lean: not formalized

*Proof.* The central character is trivial, so $\tilde\pi_f \cong \pi_f$. Volume 4, Theorem 2.2.7, says that $\Lambda_N(f, s') = N^{s'/2}(2\pi)^{-s'}\Gamma(s')L(f, s')$ satisfies $\Lambda_N(f, k - s') = i^k\varepsilon_N\Lambda_N(f, s')$. By Proposition 4.5.6, $\Lambda(s, \pi_f) = 2N^{-s'/2}\Lambda_N(f, s')$. The substitution $s \mapsto 1 - s$ sends $s'$ to $k - s'$. So
$$\Lambda(1 - s, \pi_f) = 2N^{-(k - s')/2}i^k\varepsilon_N\Lambda_N(f, s') = N^{s' - k/2}i^k\varepsilon_N\Lambda(s, \pi_f) = N^{s - 1/2}i^k\varepsilon_N\Lambda(s, \pi_f).$$
Since $(i^k\varepsilon_N)^2 = 1$, this is $\Lambda(s, \pi_f) = i^k\varepsilon_NN^{1/2 - s}\Lambda(1 - s, \pi_f)$. Comparison with Theorem 4.5.5 gives the formula, since $\Lambda(1 - s, \pi_f)$ is not identically $0$. Comparing the exponents of $N$ gives $N(\pi_f) = N$ again. $\square$

**Example 4.5.8 (local root numbers).** For $N = 1$ the formula reads $\varepsilon(s, \pi_f) = i^k = (-1)^{k/2}$, the sign of Hecke's Theorem 2.2.4 in Volume 4, and the only nontrivial local factor is $\varepsilon(s, D_k, \psi_\infty) = i^k$. For $\Delta$, of weight 12, the root number is $(-1)^6 = +1$. Now let $p \parallel N$, so $\pi_{f,p} = \mu\mathrm{St}$ with $\mu$ unramified. The local newform is $W_p(a(y)) = \mu(y)|y|1_{\mathbb{Z}_p}(y)$, and $Z(s, W_p) = \sum_{r \ge 0}\mu(p)^rp^{-r}p^{-r(s - 1/2)} = L(s + 1/2, \mu)$, as Definition 4.5.1 requires. By Volume 6, Example 3.3.4, $\varepsilon(s, \mathrm{St}, \psi_p) = -p^{1/2 - s}$, and so $\varepsilon(s, \mu\mathrm{St}, \psi_p) = -\mu(p)p^{1/2 - s}$. For squarefree $N$ the product formula gives
$$i^k\varepsilon_N = i^k\prod_{p \mid N}(-\mu_p(p)), \qquad \varepsilon_N = \prod_{p \mid N}\left(-a_p(f)p^{1 - k/2}\right),$$
by Proposition 4.3.5, part 1. This is the classical formula of Atkin and Lehner for the eigenvalue of $w_N$ on a newform of squarefree level. For $f_{11}$: $\varepsilon(s, D_2, \psi_\infty) = -1$, $\varepsilon(s, \mathrm{St}, \psi_{11}) = -11^{1/2 - s}$, and $\varepsilon(s, \pi_{f_{11}}) = 11^{1/2 - s}$, with root number $+1$. This agrees with $w_{11}f_{11} = -f_{11}$ and Volume 4, Example 2.2.15.
