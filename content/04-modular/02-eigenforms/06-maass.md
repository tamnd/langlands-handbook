---
title: Maass forms
nodes: [LG0S1WN9ND, LG75ERTV5K]
sources: [Sel65, Kim03]
status: checked
drafted_by: writer
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## Maass forms

The holomorphic forms of the previous sections are not the only automorphic forms for $GL_2$ over $\mathbb{Q}$. Maass forms are real analytic functions on $\mathbb{H}$ that are invariant under a congruence subgroup and are eigenfunctions of the hyperbolic Laplacian. They have Hecke operators and $L$-functions, but no known Galois representations in general, and the Ramanujan conjecture for them is open. This section states the two conjectures of the map on Maass forms: the Selberg eigenvalue conjecture and the Ramanujan conjecture at the finite primes. It is short, and it follows the conventions of the Lean statements.

### The Laplacian

**Definition 2.6.1 (hyperbolic Laplacian).** For a function $f : \mathbb{H} \to \mathbb{C}$ of class $C^2$, with $z = x + iy$, the *hyperbolic Laplacian* is
$$\Delta f = -y^2\left(\frac{\partial^2 f}{\partial x^2} + \frac{\partial^2 f}{\partial y^2}\right).$$

Lean: `Langlands.hyperbolicLaplacian`

The operator $\Delta$ commutes with the action of $SL_2(\mathbb{R})$ on functions by $f \mapsto f \circ g$. The sign makes $\Delta$ a nonnegative operator. For $s \in \mathbb{C}$ the function $y^s$ satisfies $\Delta y^s = -y^2 s(s - 1)y^{s-2} = s(1 - s)y^s$. In Lean the function $f$ is extended to $\mathbb{C}$ by `UpperHalfPlane.ofComplex`, and $\partial_x^2 + \partial_y^2$ is `Laplacian.laplacian` of Mathlib on $\mathbb{C} = \mathbb{R}^2$. The values outside $\mathbb{H}$ have no effect, since $\mathbb{H}$ is open.

**Definition 2.6.2 (square integrable eigenfunction).** Let $\Gamma \subseteq SL_2(\mathbb{Z})$ be a subgroup and $\lambda \in \mathbb{R}$. A function $f : \mathbb{H} \to \mathbb{C}$ is a *square integrable eigenfunction* on $\Gamma\backslash\mathbb{H}$ with eigenvalue $\lambda$ if it is smooth, $f(\gamma z) = f(z)$ for all $\gamma \in \Gamma$, $\Delta f = \lambda f$, and for each $g \in SL_2(\mathbb{Z})$
$$\int_{\mathcal{F}} |f(gz)|^2 \frac{dx\,dy}{y^2} < \infty,$$
where $\mathcal{F}$ is the standard fundamental domain of $SL_2(\mathbb{Z})$.

Lean: `Langlands.IsL2Eigenfunction`

The four conditions are the fields `smooth`, `invariant`, `eigen` and `squareIntegrable`. If $\Gamma$ has finite index, finitely many translates $g\mathcal{F}$ cover a fundamental domain of $\Gamma$, so the last condition says that $f$ is in $L^2(\Gamma\backslash\mathbb{H})$ for the measure $dx\,dy/y^2$. The area of $\mathcal{F}$ is $\pi/3$, and the Lean theorem `Langlands.Fidelity.integrableOn_fd` shows that it is finite. So the constant function 1 is a square integrable eigenfunction with $\lambda = 0$ for every $\Gamma$. This is `Langlands.Fidelity.isL2Eigenfunction_one`.

**Proposition 2.6.3 (the eigenvalues are nonnegative).** Let $\Gamma$ be a subgroup of finite index in $SL_2(\mathbb{Z})$ and $f \ne 0$ a square integrable eigenfunction on $\Gamma\backslash\mathbb{H}$ with eigenvalue $\lambda$. Then $\lambda \ge 0$, and $\lambda = 0$ only if $f$ is constant.

Lean: not stated yet

*Outline of the proof.* Let $D$ be a fundamental domain of $\Gamma$. Since $dx\,dy/y^2$ cancels the factor $y^2$ of $\Delta$, Green's formula gives
$$\lambda\int_D |f|^2 \frac{dx\,dy}{y^2} = \int_D \Delta f \cdot \bar f \,\frac{dx\,dy}{y^2} = \int_D \left(|\partial_x f|^2 + |\partial_y f|^2\right) dx\,dy.$$
The boundary terms on the sides of $D$ cancel in pairs, since $f$ is invariant under $\Gamma$. The terms at the cusps go to 0, since $f$ is square integrable: this needs the domain of the self-adjoint Laplacian on $L^2(\Gamma\backslash\mathbb{H})$, and the Lean file explains why $f$ is in it. The right side is nonnegative, so $\lambda \ge 0$. If $\lambda = 0$, then $\partial_x f = \partial_y f = 0$ and $f$ is constant. $\square$

**Example 2.6.4 (Eisenstein series and the continuous spectrum).** Let $\Gamma_\infty$ be the stabilizer of $\infty$ in $SL_2(\mathbb{Z})$. For $\mathrm{Re}(s) > 1$ the series
$$E(z, s) = \sum_{\gamma \in \Gamma_\infty\backslash SL_2(\mathbb{Z})} \mathrm{Im}(\gamma z)^s$$
converges and is invariant under $SL_2(\mathbb{Z})$. Each term is $y^s \circ \gamma$, so $\Delta E(z, s) = s(1 - s)E(z, s)$. Its constant term is $y^s + \varphi(s)y^{1-s}$ with $\varphi(s) = \xi(2s - 1)/\xi(2s)$ and $\xi(s) = \pi^{-s/2}\Gamma(s/2)\zeta(s)$, so $E(z, s)$ is not square integrable. It has a meromorphic continuation to $\mathbb{C}$ with $\xi(2s)E(z, s) = \xi(2 - 2s)E(z, 1 - s)$, and a simple pole at $s = 1$ with constant residue $3/\pi$. On the line $s = 1/2 + ir$ the eigenvalue is $s(1 - s) = 1/4 + r^2$. Integrals of $E(z, 1/2 + ir)$ against functions of $r$ give the continuous spectrum $[1/4, \infty)$ of $\Delta$ on $L^2(SL_2(\mathbb{Z})\backslash\mathbb{H})$. The orthogonal complement of the Eisenstein part and the constants is the space of cusp forms, where $\Delta$ has a discrete spectrum. The same holds for a congruence subgroup, with one Eisenstein series for each cusp.

### Selberg's conjecture

Write an eigenvalue as $\lambda = s(1 - s)$ with $s = 1/2 + ir$. Then $\lambda \ge 1/4$ if and only if $r$ is real. An eigenvalue $0 < \lambda < 1/4$ is *exceptional*. It has $s = 1/2 + \theta$ with $0 < \theta < 1/2$ real and $\lambda = 1/4 - \theta^2$.

**Conjecture 2.6.5 (Selberg).** Let $\Gamma$ be a congruence subgroup of $SL_2(\mathbb{Z})$. Each eigenvalue $\lambda \ne 0$ of $\Delta$ on $L^2(\Gamma\backslash\mathbb{H})$ satisfies $\lambda \ge 1/4$.

Node: LG0S1WN9ND · Lean: `Langlands.SelbergEigenvalue`

**Remark 2.6.6 (the Lean form and the known bounds).** The statement `Langlands.SelbergEigenvalue` quantifies over all subgroups $\Gamma$ with `IsCongruenceSubgroup Γ`, all $f \ne 0$ and all real $\lambda$, with `IsL2Eigenfunction Γ f ev` and $\lambda \ne 0$, and it concludes $1/4 \le \lambda$. The textbook form is $\lambda_1(\Gamma) \ge 1/4$ for the smallest positive eigenvalue. The two forms are the same. Below $1/4$ there is no continuous spectrum, and for a congruence subgroup the only square integrable eigenfunctions that are orthogonal to the cusp forms are the constants. The hypothesis $\lambda \ne 0$ is necessary, since the constants have $\lambda = 0$. The Lean theorem `Langlands.Fidelity.not_selbergEigenvalue_of_eigenvalue_zero` proves that the statement without it is false, with $\Gamma = SL_2(\mathbb{Z})$ and $f = 1$. The congruence condition is also necessary: for subgroups of finite index that are not congruence subgroups, $\lambda_1$ can be arbitrarily small. Selberg proved $\lambda \ge 3/16 = 1/4 - (1/4)^2$ [Sel65]. His proof uses the Kloosterman zeta function $\sum_c S(m, n; c)c^{-2s}$: an exceptional eigenvalue gives a pole at $s = 1/2 + \theta$, and the Weil bound $|S(m, n; c)| \le \tau(c)\gcd(m, n, c)^{1/2}c^{1/2}$ gives convergence for $\mathrm{Re}(s) > 3/4$, so $\theta \le 1/4$. The best known bound is $\lambda \ge 975/4096 = 1/4 - (7/64)^2$, by Kim and Sarnak [Kim03, Appendix 2]. For $SL_2(\mathbb{Z})$ itself the conjecture is known: there are no eigenvalues in $(0, 1/4)$, and the smallest positive eigenvalue is $\lambda_1 \approx 91.14$, with $r \approx 9.5337$.

### Maass cusp forms and Hecke operators

**Definition 2.6.7 (Maass cusp form).** Let $N \ge 1$, $\chi$ a Dirichlet character modulo $N$ and $\lambda \in \mathbb{R}$. A *Maass cusp form* on $\Gamma_1(N)$ with character $\chi$ and eigenvalue $\lambda$ is a square integrable eigenfunction $f$ on $\Gamma_1(N)\backslash\mathbb{H}$ with eigenvalue $\lambda$ such that $f(\gamma z) = \chi(d)f(z)$ for all $\gamma = \begin{pmatrix} a & b \\ c & d \end{pmatrix} \in \Gamma_0(N)$, and
$$\int_0^N f(g(x + iy))\,dx = 0 \quad \text{for all } g \in SL_2(\mathbb{Z}) \text{ and } y > 0.$$

Lean: `Langlands.IsMaassCuspForm`

The fields are `eigenfunction`, `nebentypus` and `cuspidal`. The function $f \circ g$ is invariant under $z \mapsto z + N$, so the last condition says that the constant term of $f$ at the cusp $g\infty$ vanishes. Since $-I$ acts trivially on $\mathbb{H}$, a nonzero $f$ forces $\chi(-1) = 1$. For $N = 1$ a Maass cusp form has an expansion
$$f(z) = \sum_{n \ne 0} \rho(n)\, y^{1/2}K_{ir}(2\pi|n|y)\, e^{2\pi inx}, \qquad \lambda = 1/4 + r^2,$$
with the $K$-Bessel function $K_{ir}$, which decays exponentially as $y \to \infty$. This is the analogue of the $q$-expansion of Lemma 1.2.4, and the coefficients $\rho(n)$ play the part of $a_n$.

**Definition 2.6.8 (Hecke operator for Maass forms).** Let $\chi$ be a Dirichlet character modulo $N$ and $p$ a prime. For $f : \mathbb{H} \to \mathbb{C}$,
$$T_p f(z) = p^{-1/2}\left(\chi(p)f(pz) + \sum_{b=0}^{p-1} f\left(\frac{z + b}{p}\right)\right).$$

Lean: `Langlands.heckeOperator`

This is the *unitary normalization*. For $p \nmid N$ the operator $T_p$ preserves the Maass cusp forms on $\Gamma_1(N)$ with character $\chi$ and eigenvalue $\lambda$, it commutes with $\Delta$, and its adjoint for the Petersson inner product is $\overline{\chi(p)}T_p$, as in Theorem 1.6.2. An eigenvalue $c$ of $T_p$ on a cusp form thus satisfies $c = \chi(p)\bar c$. The *Satake parameters* $\alpha_p, \beta_p$ are the roots of $X^2 - cX + \chi(p)$. The argument of Lemma 2.3.1, with $k - 1$ replaced by 0, shows that $|c| \le 2$ if and only if $|\alpha_p| = |\beta_p| = 1$.

**Example 2.6.9 (the constants and the Eisenstein series).** Take $N = 1$ and $\chi = 1$. For the function $y^s$, the term $f(pz)$ gives $p^sy^s$ and each of the $p$ terms $f((z + b)/p)$ gives $p^{-s}y^s$. So
$$T_p y^s = p^{-1/2}\left(p^s + p^{1-s}\right)y^s = \left(p^{s - 1/2} + p^{1/2 - s}\right)y^s.$$
A computation with the sum over $\Gamma_\infty\backslash SL_2(\mathbb{Z})$ shows that the Eisenstein series $E(z, s)$ has the same eigenvalue. On the line $s = 1/2 + it$ the eigenvalue is $p^{it} + p^{-it} = 2\cos(t\log p)$, of absolute value at most 2, and the Satake parameters $p^{\pm it}$ have absolute value 1. At $s = 0$, where $y^s = 1$, the eigenvalue is $p^{1/2} + p^{-1/2} > 2$. It is also the eigenvalue at $s = 1$, so it is the eigenvalue of the residue $3/\pi$ of $E(z, s)$. The Lean theorem `Langlands.Fidelity.heckeOperator_one` proves $T_p 1 = (p^{1/2} + p^{-1/2})\cdot 1$ in level 1. The theorem `Langlands.Fidelity.two_lt_heckeEigenvalue_one` proves that the constant function 1 satisfies all the conditions of Definition 2.6.7 except the cuspidal condition, with $T_p 1 = c \cdot 1$ and $|c| > 2$. So the next conjecture fails without the cuspidal condition.

**Conjecture 2.6.10 (Ramanujan for Maass forms).** Let $N \ge 1$, $\chi$ a Dirichlet character modulo $N$, $f \ne 0$ a Maass cusp form on $\Gamma_1(N)$ with character $\chi$, and $p \nmid N$ a prime. If $T_p f = cf$, then $|c| \le 2$.

Node: LG75ERTV5K · Lean: `Langlands.RamanujanMaass`

**Remark 2.6.11 (the Lean form, the bounds and the place at infinity).** The statement `Langlands.RamanujanMaass` takes $N > 0$, $\chi$, $f \ne 0$ and $\lambda$ with `IsMaassCuspForm N χ f ev`, and for each prime $p \nmid N$ and $c \in \mathbb{C}$ with `heckeOperator χ p f = c • f` it concludes `‖c‖ ≤ 2`. The textbook form is for a newform that is an eigenfunction of all $T_n$ with $(n, N) = 1$. The statement here is for each eigenvector of one $T_p$. The two forms are equivalent, for the reasons of Remark 2.1.11: the space of cusp forms with a given $\lambda$ has finite dimension and a basis of common eigenvectors of the normal operators $T_n$, and an oldform has the eigenvalues of a newform of lower level. In the arithmetic normalization, without the factor $p^{-1/2}$, the bound is $2p^{1/2}$, which is the bound of Theorem 2.3.2 with $k = 2$. The best known bound is $|c| \le p^{7/64} + p^{-7/64}$, by Kim and Sarnak [Kim03, Appendix 2]. Kim proved that the symmetric fourth power of a cusp form on $GL_2$ is automorphic on $GL_5$, and the bound follows from the analytic properties of the $L$-functions of this lift and of its Rankin-Selberg products. The same method gives $\theta \le 7/64$ in Remark 2.6.6. The proof of Deligne's theorem in Section 2.3 does not extend: a Maass form has no known Galois representation and no known motive, and $\lambda$ is not expected to be algebraic in general. The exception is the case $\lambda = 1/4$, $r = 0$. Some Maass forms with $\lambda = 1/4$ correspond to even irreducible Galois representations of dimension 2 with finite image, such as the forms that Maass built from the Hecke characters of real quadratic fields. For them the Satake parameters are the eigenvalues of matrices of finite order, so they have absolute value 1 and Conjecture 2.6.10 holds. In the language of automorphic representations, Conjecture 2.6.10 says that the local component at $p$ of the representation of $f$ is tempered, and Conjecture 2.6.5 says the same at the real place, where the local component is a principal series with parameter $ir$ and is tempered if and only if $r$ is real. So Selberg's conjecture is the Ramanujan conjecture at the infinite prime. The two together are the Ramanujan conjecture for $GL_2$ over $\mathbb{Q}$, of which Theorem 2.3.2 is the case of the holomorphic forms.
