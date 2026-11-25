---
title: The class number and the unit theorem
nodes: []
sources: [Neu99]
status: drafted
drafted_by: writer
reviewed_by: []
---
## The class number and the unit theorem

Minkowski's idea is to view $\mathcal{O}_F$ as a lattice in a real vector space of dimension $n$. A convex set of large volume then contains a nonzero lattice point. This one argument proves the two finiteness theorems of algebraic number theory: the class group is finite, and the unit group is finitely generated of rank $r_1 + r_2 - 1$. We follow [Neu99], Chapter I, Sections 4 to 7.

### Lattices

Let $V$ be a real vector space of dimension $n$. A *lattice* in $V$ is a subgroup of the form $\Gamma = \mathbb{Z} v_1 + \dots + \mathbb{Z} v_m$ with $v_1, \dots, v_m$ linearly independent. It is *complete* if $m = n$. Then the set $P = \{\sum x_i v_i : 0 \le x_i < 1\}$ is a *fundamental domain*: each $v \in V$ is $\gamma + p$ for a unique $\gamma \in \Gamma$ and $p \in P$. Fix a Haar measure $\mu$ on $V$. The *covolume* of a complete lattice is $\mathrm{vol}(V/\Gamma) = \mu(P)$. It does not depend on the choice of the basis.

**Proposition 1.3.1 (lattices are the discrete subgroups).** A subgroup $\Gamma$ of $V$ is a lattice if and only if it is discrete. A discrete subgroup $\Gamma$ is a complete lattice if and only if $V / \Gamma$ is compact.

Lean: not stated yet

*Proof.* A lattice is discrete, because in the coordinates of a basis that extends $v_1, \dots, v_m$, it is $\mathbb{Z}^m \times 0$. Conversely, let $\Gamma$ be discrete, and let $V_0$ be the subspace that $\Gamma$ spans. Choose a basis $v_1, \dots, v_m$ of $V_0$ in $\Gamma$, and let $\Gamma_0 = \sum \mathbb{Z} v_i$. Each element of $\Gamma$ is in $\Gamma_0 + P_0$, where $P_0$ is the bounded set $\{\sum x_i v_i : 0 \le x_i < 1\}$. A discrete subgroup meets a bounded set in a finite set, so $\Gamma / \Gamma_0$ is finite, of order $q$ say. Then $q \Gamma \subset \Gamma_0$, so $\Gamma \subset \frac{1}{q} \Gamma_0$, and $\Gamma$ is a subgroup of a free group of rank $m$ that contains a free group of rank $m$. Thus $\Gamma$ is a lattice of rank $m$. Finally $V / \Gamma \cong V_0 / \Gamma \times V / V_0$, and this is compact if and only if $V = V_0$. $\square$

**Theorem 1.3.2 (Minkowski's lattice point theorem).** Let $\Gamma$ be a complete lattice in $V$ and $X \subset V$ a convex set that is symmetric about $0$. If $\mu(X) > 2^n \mathrm{vol}(V/\Gamma)$, then $X$ contains a nonzero point of $\Gamma$.

Lean: `MeasureTheory.exists_ne_zero_mem_lattice_of_measure_mul_two_pow_lt_measure`, from Mathlib

*Proof.* The sets $\frac12 X + \gamma$, for $\gamma \in \Gamma$, are not pairwise disjoint. Indeed, if they were disjoint, then their intersections with the fundamental domain $P$ would be disjoint, and
$$\mathrm{vol}(V/\Gamma) = \mu(P) \ge \sum_{\gamma} \mu\big(P \cap (\tfrac12 X + \gamma)\big) = \sum_\gamma \mu\big((P - \gamma) \cap \tfrac12 X\big) = \mu(\tfrac12 X) = 2^{-n} \mu(X),$$
because the sets $P - \gamma$ cover $V$ and are disjoint. This contradicts the hypothesis. So there are $\gamma_1 \ne \gamma_2$ and $x_1, x_2 \in X$ with $\frac12 x_1 + \gamma_1 = \frac12 x_2 + \gamma_2$. Then $\gamma_1 - \gamma_2 = \frac12 x_2 - \frac12 x_1$. This point is in $X$, because $-x_1 \in X$ and $X$ is convex. It is a nonzero element of $\Gamma$. $\square$

### The Minkowski space

For each real embedding $\sigma$ of $F$ we take one copy of $\mathbb{R}$, and for each pair $\sigma, \bar\sigma$ of complex embeddings we take one copy of $\mathbb{C}$, indexed by one embedding of the pair. These indices are the *infinite places* $v$ of $F$, and we write $v \mid \infty$. They are $r_1 + r_2$ in number. Let
$$F_\infty = \prod_{v \mid \infty} F_v \cong \mathbb{R}^{r_1} \times \mathbb{C}^{r_2}, \qquad j : F \to F_\infty, \quad j(x) = (\sigma_v(x))_v,$$
where $F_v$ is $\mathbb{R}$ or $\mathbb{C}$ and $\sigma_v$ is the embedding of the place $v$. This is the *Minkowski space* of $F$. It is a real vector space of dimension $n$, and $j$ is an injective ring homomorphism. Chapter 2 shows that $F_v$ is the completion of $F$ at $v$, and that $F_\infty \cong F \otimes_\mathbb{Q} \mathbb{R}$.

On $F_\infty$ we use the measure $\mu_\infty$ that is the product of the Lebesgue measure $dx$ on each real factor and of twice the Lebesgue measure, $2 \, dx \, dy$, on each complex factor. This is the measure of Chapter 3, and with it the formulas have no powers of 2. The absolute value at $v$ is
$$|x|_v = |\sigma_v(x)| \text{ if } v \text{ is real}, \qquad |x|_v = |\sigma_v(x)|^2 \text{ if } v \text{ is complex}.$$
With this convention $|N_{F/\mathbb{Q}}(x)| = \prod_{v \mid \infty} |x|_v$, and multiplication by $a \in F_\infty^\times$ multiplies $\mu_\infty$ by $\prod_v |a_v|_v$.

**Proposition 1.3.3 (covolume of an ideal).** For each nonzero ideal $\mathfrak{a}$ of $\mathcal{O}_F$, the image $j(\mathfrak{a})$ is a complete lattice in $F_\infty$, and
$$\mathrm{vol}(F_\infty / j(\mathfrak{a})) = N(\mathfrak{a}) \, |d_F|^{1/2}.$$

Lean: not stated yet

*Proof.* Let $\omega_1, \dots, \omega_n$ be an integral basis. Identify $F_\infty$ with $\mathbb{R}^n$ by the coordinates $\sigma_v(x)$ for real $v$, and $\mathrm{Re}\, \sigma_v(x), \mathrm{Im}\, \sigma_v(x)$ for complex $v$. Let $A$ be the real $n \times n$ matrix whose columns are the coordinates of $j(\omega_1), \dots, j(\omega_n)$. Let $D = \det(\sigma_i(\omega_k))$ as in Section 1.1, with all $n$ embeddings. The rows of $D$ for $\sigma$ and $\bar\sigma$ are $\mathrm{Re} + i \, \mathrm{Im}$ and $\mathrm{Re} - i \, \mathrm{Im}$ of the corresponding rows of $A$. This row operation multiplies the determinant by $-2i$. Thus $|D| = 2^{r_2} |\det A|$. The Lebesgue measure of the fundamental domain is $|\det A|$, and the factor 2 on each complex factor gives
$$\mathrm{vol}(F_\infty / j(\mathcal{O}_F)) = 2^{r_2} |\det A| = |D| = |d_F|^{1/2}.$$
In particular the $j(\omega_k)$ are linearly independent, and $j(\mathcal{O}_F)$ is a complete lattice. A sublattice of index $N(\mathfrak{a})$ has a covolume $N(\mathfrak{a})$ times larger. $\square$

**Theorem 1.3.4 (an element of small norm).** Let $\mathfrak{a}$ be a nonzero ideal of $\mathcal{O}_F$, and let $c_v > 0$ for $v \mid \infty$ with
$$\prod_{v \mid \infty} c_v > \left(\frac{2}{\pi}\right)^{r_2} |d_F|^{1/2} N(\mathfrak{a}).$$
Then there is a nonzero $\alpha \in \mathfrak{a}$ with $|\alpha|_v < c_v$ for all $v \mid \infty$. In particular each nonzero ideal $\mathfrak{a}$ contains a nonzero element $\alpha$ with
$$|N_{F/\mathbb{Q}}(\alpha)| \le \left(\frac{2}{\pi}\right)^{r_2} |d_F|^{1/2} N(\mathfrak{a}).$$

Lean: not stated yet

*Proof.* The set $X = \{y \in F_\infty : |y_v|_v < c_v \text{ for all } v\}$ is convex and symmetric. It is a product of intervals of length $2 c_v$ and of discs of radius $c_v^{1/2}$. Its volume is
$$\mu_\infty(X) = \prod_{v \text{ real}} 2 c_v \prod_{v \text{ complex}} 2 \pi c_v = 2^{r_1 + r_2} \pi^{r_2} \prod_v c_v.$$
The hypothesis says that this is larger than $2^n N(\mathfrak{a}) |d_F|^{1/2}$, because $n - r_1 - r_2 = r_2$. Theorem 1.3.2 and Proposition 1.3.3 give the element $\alpha$. For the second claim, let $B$ be the bound and $\varepsilon > 0$. Choose $c_v = (B + \varepsilon)^{1/(r_1 + r_2)}$ for all $v$. The first claim gives $\alpha \in \mathfrak{a}$ with $|N(\alpha)| = \prod_v |\alpha|_v < B + \varepsilon$. For $\varepsilon \le 1$ these elements lie in one bounded set, and $j(\mathfrak{a})$ has only finitely many points in a bounded set. Thus one $\alpha$ works for arbitrarily small $\varepsilon$, and $|N(\alpha)| \le B$. $\square$

### The class number

**Theorem 1.3.5 (finiteness of the class number).** Let $M_F = (2/\pi)^{r_2} |d_F|^{1/2}$. Each class of $\mathrm{Cl}_F$ contains an integral ideal $\mathfrak{b}$ with $N(\mathfrak{b}) \le M_F$. The class group $\mathrm{Cl}_F$ is finite.

Lean: `NumberField.RingOfIntegers.instFintypeClassGroup`, from Mathlib

*Proof.* Let $c$ be a class and $\mathfrak{a}_1$ a fractional ideal in the inverse class $c^{-1}$. Multiply $\mathfrak{a}_1$ by an integer so that it becomes an integral ideal $\mathfrak{a}$ in $c^{-1}$. By Theorem 1.3.4 there is $\alpha \in \mathfrak{a}$ nonzero with $|N(\alpha)| \le M_F N(\mathfrak{a})$. The ideal $\mathfrak{b} = \alpha \mathfrak{a}^{-1}$ is integral, since $\alpha \mathcal{O}_F \subset \mathfrak{a}$. It lies in the class $c$, and $N(\mathfrak{b}) = |N(\alpha)| / N(\mathfrak{a}) \le M_F$ by Proposition 1.2.9.

There are only finitely many integral ideals of norm at most $M_F$. Indeed an ideal $\mathfrak{b}$ of norm $m$ contains $m$, because $m$ kills the group $\mathcal{O}_F / \mathfrak{b}$. Thus $\mathfrak{b}$ corresponds to an ideal of the finite ring $\mathcal{O}_F / m\mathcal{O}_F$. $\square$

The constant $M_F$ is not the best one. With the convex set $\{y : \sum_\sigma |\sigma(y)| \le t\}$ instead of a box, the same proof gives the *Minkowski bound*
$$N(\mathfrak{b}) \le \frac{n!}{n^n} \left(\frac{4}{\pi}\right)^{r_2} |d_F|^{1/2}.$$
See [Neu99], Chapter I, Section 6, and its exercises.

**Corollary 1.3.6 (Hermite and Minkowski).** If $F \ne \mathbb{Q}$, then $|d_F| > 2$.

Lean: `NumberField.abs_discr_gt_two`, from Mathlib

*Proof.* The class of $\mathcal{O}_F$ contains an ideal of norm at least 1 and at most the Minkowski bound. Thus $|d_F|^{1/2} \ge a_n := (\pi/4)^{n/2} n^n / n!$, because $r_2 \le n/2$ and $\pi / 4 < 1$. We have $a_2 = \pi/2$ and $a_{n+1}/a_n = (\pi/4)^{1/2} (1 + 1/n)^n \ge (\pi / 4)^{1/2} \cdot 2 > 1$. So $|d_F| \ge a_n^2 \ge \pi^2 / 4 > 2$ for $n \ge 2$. $\square$

Section 1.4 shows that a prime number $p$ is ramified in $F$ if and only if $p$ divides $d_F$. Thus each number field other than $\mathbb{Q}$ has a ramified prime. Hermite also proved that there are only finitely many number fields with a given discriminant ([Neu99], Chapter III, Section 2).

**Example 1.3.7 (class numbers of small fields).** For $F = \mathbb{Q}(i)$ we have $r_2 = 1$ and $d_F = -4$, so $M_F = 4/\pi < 2$. Each class contains the ideal $\mathcal{O}_F$, and $h_F = 1$. For $F = \mathbb{Q}(\sqrt{-5})$ we have $d_F = -20$ and $M_F = (2/\pi) \sqrt{20} < 3$. The only ideals of norm at most 2 are $\mathcal{O}_F$ and the ideal $\mathfrak{p}$ of Example 1.2.7, which is not principal. Thus $h_F = 2$.

### The unit theorem

The *roots of unity* in $F$ form a group $\mu(F)$. It is finite, because a root of unity of order $m$ has degree $\varphi(m)$ over $\mathbb{Q}$, and $\varphi(m) \le n$ holds only for finitely many $m$. A finite subgroup of the multiplicative group of a field is cyclic, so $\mu(F)$ is cyclic.

**Lemma 1.3.8 (bounded integers).** For each $c > 0$, the set of $\alpha \in \mathcal{O}_F$ with $|\sigma(\alpha)| \le c$ for all embeddings $\sigma$ is finite. An element $\alpha \in \mathcal{O}_F$ with $|\sigma(\alpha)| = 1$ for all $\sigma$ is a root of unity.

Lean: not stated yet

*Proof.* The polynomial $\prod_\sigma (X - \sigma(\alpha))$ has integer coefficients by Lemma 1.1.3. Its $k$-th coefficient is bounded by $\binom{n}{k} c^k$. There are finitely many such polynomials, and each has at most $n$ roots. For the second claim, all the powers of $\alpha$ satisfy the same bound with $c = 1$, so they lie in a finite set. Thus $\alpha^a = \alpha^b$ for some $a < b$, and $\alpha$ is a root of unity. $\square$

Let $r = r_1 + r_2 - 1$. The *logarithmic embedding* is the homomorphism
$$\lambda : \mathcal{O}_F^\times \to \mathbb{R}^{r_1 + r_2}, \qquad \lambda(u) = (\log |u|_v)_{v \mid \infty}.$$
By Lemma 1.1.3, $\prod_v |u|_v = |N(u)| = 1$ for a unit $u$. Thus $\lambda$ takes values in the hyperplane $H = \{x : \sum_v x_v = 0\}$, which has dimension $r$.

**Theorem 1.3.9 (Dirichlet's unit theorem).** The kernel of $\lambda$ is $\mu(F)$, and the image $\lambda(\mathcal{O}_F^\times)$ is a complete lattice in $H$. Thus
$$\mathcal{O}_F^\times \cong \mu(F) \times \mathbb{Z}^{r_1 + r_2 - 1}.$$
There are units $\varepsilon_1, \dots, \varepsilon_r$, the *fundamental units*, such that each unit is $\zeta \varepsilon_1^{a_1} \cdots \varepsilon_r^{a_r}$ for a unique $\zeta \in \mu(F)$ and unique integers $a_i$.

Lean: `NumberField.Units.exist_unique_eq_mul_prod`, from Mathlib

*Proof.* The kernel. A unit $u$ with $\lambda(u) = 0$ has $|\sigma(u)| = 1$ for all $\sigma$, so it is a root of unity by Lemma 1.3.8. Conversely each root of unity is in the kernel.

The image is discrete. A bounded set of $H$ is contained in a set $\{x : x_v \le \log c\}$. Its inverse image consists of units with $|u|_v \le c$ for all $v$. These units satisfy $|\sigma(u)| \le \max(c, c^{1/2})$ for all $\sigma$, so they form a finite set by Lemma 1.3.8. By Proposition 1.3.1, $\lambda(\mathcal{O}_F^\times)$ is a lattice in $H$.

The image is complete. Fix an infinite place $v_0$ and a number $t > (2/\pi)^{r_2} |d_F|^{1/2}$. We construct a unit $u$ with $|u|_v < 1$ for all $v \ne v_0$. By Theorem 1.3.4 with $\mathfrak{a} = \mathcal{O}_F$, there is a nonzero $\alpha_1 \in \mathcal{O}_F$ with $|N(\alpha_1)| < t$. Given $\alpha_k$, choose $c_v$ with $0 < c_v < |\alpha_k|_v$ for $v \ne v_0$, and choose $c_{v_0}$ so that $\prod_v c_v = t$. Theorem 1.3.4 gives a nonzero $\alpha_{k+1} \in \mathcal{O}_F$ with $|\alpha_{k+1}|_v < |\alpha_k|_v$ for $v \ne v_0$ and $|N(\alpha_{k+1})| < t$. The principal ideals $\alpha_k \mathcal{O}_F$ have norm less than $t$, and there are only finitely many such ideals. Thus $\alpha_k \mathcal{O}_F = \alpha_l \mathcal{O}_F$ for some $k < l$, and $u = \alpha_l / \alpha_k$ is a unit with $|u|_v < 1$ for all $v \ne v_0$.

Number the infinite places $v_1, \dots, v_{r+1}$. For each $i \le r$ choose a unit $u_i$ with $|u_i|_v < 1$ for $v \ne v_i$. Let $A$ be the $r \times r$ matrix with entries $a_{ik} = \log |u_i|_{v_k}$ for $i, k \le r$. Its entries off the diagonal are negative. The sum of the entries of row $i$ is $-\log |u_i|_{v_{r+1}} > 0$, because the full row of $\lambda(u_i)$ has sum 0. Such a matrix is invertible. Indeed, let $Ax = 0$ with $x \ne 0$, and choose $k$ with $|x_k|$ maximal, and $x_k > 0$ after a change of sign. Then
$$0 = \sum_j a_{kj} x_j \ge a_{kk} x_k + \sum_{j \ne k} a_{kj} x_k = x_k \sum_j a_{kj} > 0,$$
because $a_{kj} < 0$ and $x_j \le x_k$ for $j \ne k$. This is a contradiction. Thus $\lambda(u_1), \dots, \lambda(u_r)$ are linearly independent, and they span $H$.

The structure. The group $\mathcal{O}_F^\times / \mu(F)$ is isomorphic to a lattice of rank $r$, so it is free of rank $r$. Lifts $\varepsilon_1, \dots, \varepsilon_r$ of a basis are fundamental units. $\square$

**Definition 1.3.10 (regulator).** Let $\varepsilon_1, \dots, \varepsilon_r$ be fundamental units. The *regulator* of $F$ is $R_F = |\det(\log |\varepsilon_i|_{v_k})_{1 \le i, k \le r}|$. It does not depend on the choice of the fundamental units, nor on the place $v_{r+1}$ that the matrix leaves out. The covolume of $\lambda(\mathcal{O}_F^\times)$ in $H$, for the measure on $H$ that the projection to the first $r$ coordinates gives, is $R_F$.

Lean: `NumberField.Units.regulator`, from Mathlib

The class number and the regulator appear together in the residue of the Dedekind zeta function at $s = 1$. This is the analytic class number formula. Tate's thesis proves it with the adelic methods of Chapter 3, and Volume 3 treats the local part of Tate's thesis.

**Example 1.3.11 (units of quadratic fields).** Let $F$ be imaginary quadratic. Then $r_1 = 0$ and $r_2 = 1$, so $r = 0$, and $\mathcal{O}_F^\times = \mu(F)$. This group is $\{\pm 1\}$, except for $\mathbb{Q}(i)$, where it has order 4, and $\mathbb{Q}(\sqrt{-3})$, where it has order 6. Let $F = \mathbb{Q}(\sqrt d)$ be real quadratic. Then $r = 1$ and $\mathcal{O}_F^\times = \{\pm \varepsilon^a : a \in \mathbb{Z}\}$ for a unique fundamental unit $\varepsilon > 1$. For $d = 2$ the unit is $1 + \sqrt 2$, and for $d = 5$ it is $(1 + \sqrt 5)/2$. The units of $\mathbb{Z}[\sqrt d]$ give the solutions of Pell's equation $x^2 - d y^2 = \pm 1$.
