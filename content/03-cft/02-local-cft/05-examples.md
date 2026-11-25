---
title: Examples over the p-adic numbers
nodes: []
sources: [Ser79, Ser67, Mil20]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Examples over the $p$-adic numbers

This section computes norm groups for $K = \mathbb{Q}_p$. In each case the method is the same. One finds enough norms by hand, and then Theorem 2.1.2 gives the index of the norm group. When the subgroup of known norms has the correct index, it is the norm group.

### Cyclotomic extensions

Let $n \ge 1$, let $\zeta$ be a primitive root of unity of order $p^n$, and let $L = \mathbb{Q}_p(\zeta)$. The cyclotomic polynomial is
$$\Phi_{p^n}(X) = \frac{X^{p^n} - 1}{X^{p^{n-1}} - 1} = \sum_{j=0}^{p-1} X^{j p^{n-1}}.$$
The polynomial $\Phi_{p^n}(X + 1)$ is an Eisenstein polynomial of degree $\varphi(p^n) = p^{n-1}(p-1)$, see [Ser79], Chapter IV, Section 4. Thus $L / \mathbb{Q}_p$ is totally ramified of degree $\varphi(p^n)$, the element $1 - \zeta$ is a uniformizer of $L$, and the map $\mathrm{Gal}(L / \mathbb{Q}_p) \to (\mathbb{Z} / p^n \mathbb{Z})^\times$, $\sigma \mapsto a$ with $\sigma(\zeta) = \zeta^a$, is an isomorphism.

**Example 2.5.1 (the norm of $1 - \zeta$).** The conjugates of $\zeta$ are the primitive roots of unity of order $p^n$, and they are the roots of $\Phi_{p^n}$. Thus
$$N_{L/\mathbb{Q}_p}(1 - \zeta) = \prod_{a \in (\mathbb{Z}/p^n)^\times} (1 - \zeta^a) = \Phi_{p^n}(1) = p.$$
So $p$ is a norm from $L$. This agrees with Corollary 2.1.9, since $L$ is totally ramified.

**Lemma 2.5.2 ($p$-th powers of principal units).** Let $p$ be odd and $m \ge 1$. The map $x \mapsto x^p$ maps $1 + p^m \mathbb{Z}_p$ onto $1 + p^{m+1} \mathbb{Z}_p$. The map $x \mapsto x^{p-1}$ is a bijection of $1 + p \mathbb{Z}_p$ onto itself.

Lean: not stated yet

*Proof.* Let $x = 1 + p^m a$ with $a \in \mathbb{Z}_p$. By the binomial theorem,
$$x^p = 1 + p^{m+1} a + \binom{p}{2} p^{2m} a^2 + \dots + p^{pm} a^p.$$
The binomial coefficients $\binom{p}{i}$ for $0 < i < p$ are divisible by $p$, so the middle terms are divisible by $p^{2m+1}$, and $2m + 1 \ge m + 2$. The last term is divisible by $p^{pm}$, and $pm \ge m + 2$ since $p \ge 3$. Thus $x^p \equiv 1 + p^{m+1} a \pmod{p^{m+2}}$. So the $p$-th power maps $1 + p^m \mathbb{Z}_p$ into $1 + p^{m+1} \mathbb{Z}_p$, and it induces a surjection of each graded piece $U^{(i)} / U^{(i+1)}$ onto $U^{(i+1)} / U^{(i+2)}$ for $i \ge m$. The successive approximation of Proposition 2.2.2 then gives surjectivity. For the second claim, $1 + p \mathbb{Z}_p$ is a pro-$p$ group, so it is a module over $\mathbb{Z}_p$ by $(x, c) \mapsto x^c$. The integer $p - 1$ is a unit of $\mathbb{Z}_p$, so the power $x \mapsto x^{p-1}$ has the inverse $x \mapsto x^{1/(p-1)}$. $\square$

**Proposition 2.5.3 (norm group of a cyclotomic extension).** Let $p$ be odd and $L = \mathbb{Q}_p(\zeta_{p^n})$. Then
$$N_{L/\mathbb{Q}_p}(L^\times) = p^{\mathbb{Z}} \times (1 + p^n \mathbb{Z}_p).$$

Lean: not stated yet

*Proof.* Let $N$ be the norm group. By Example 2.5.1, $p \in N$. For $x \in 1 + p \mathbb{Z}_p$ one has $N_{L/\mathbb{Q}_p}(x) = x^{[L : \mathbb{Q}_p]} = (x^{p-1})^{p^{n-1}}$. By Lemma 2.5.2, applied $n - 1$ times, these elements fill $1 + p^n \mathbb{Z}_p$. Thus $N$ contains the group $p^{\mathbb{Z}} \times (1 + p^n \mathbb{Z}_p)$. The index of this group in $\mathbb{Q}_p^\times$ is $[\mathbb{Z}_p^\times : 1 + p^n \mathbb{Z}_p] = \varphi(p^n)$. By Theorem 2.1.2, the index of $N$ is $[L : \mathbb{Q}_p] = \varphi(p^n)$. A subgroup of $N$ with the same finite index is $N$. $\square$

The result is also true for $p = 2$, but for $n \ge 2$ the powers $x^{2^{n-1}}$ of units fill only $1 + 2^{n+1} \mathbb{Z}_2$, and the argument fails. Chapter 3 proves the formula for all $p$ with Lubin-Tate theory.

The proposition gives the kernel of $r_{L/\mathbb{Q}_p}$, but not the map itself. It shows that $r(p)$ fixes $\zeta_{p^n}$, and that $r$ induces an isomorphism of $\mathbb{Z}_p^\times / (1 + p^n \mathbb{Z}_p) = (\mathbb{Z}/p^n)^\times$ with $\mathrm{Gal}(L/\mathbb{Q}_p) \cong (\mathbb{Z}/p^n)^\times$. Chapter 3 shows that this isomorphism is the identity: $\mathrm{rec}(u)(\zeta) = \zeta^u$ for $u \in \mathbb{Z}_p^\times$. In the arithmetic normalization the formula is $\mathrm{Art}(u)(\zeta) = \zeta^{u^{-1}}$. On the unramified side, $\mathrm{rec}(p)$ acts on a root of unity $\xi$ of order prime to $p$ by $\xi \mapsto \xi^{a}$ with $a p \equiv 1$ modulo the order of $\xi$, which is the geometric Frobenius, and units act trivially. Thus $\mathrm{rec}$ maps $\mathbb{Q}_p^\times = p^{\mathbb{Z}} \times \mathbb{Z}_p^\times$ injectively into $\mathrm{Gal}(\mathbb{Q}_p(\mu_\infty) / \mathbb{Q}_p) \cong \hat{\mathbb{Z}} \times \mathbb{Z}_p^\times$. The local Kronecker-Weber theorem of Chapter 3 says that $\mathbb{Q}_p(\mu_\infty) = \mathbb{Q}_p^{ab}$.

### Quadratic extensions

Let $p$ be odd, and let $\varepsilon \in \mathbb{Z}_p^\times$ be a unit whose reduction is not a square in $\mathbb{F}_p$. A unit $u$ is a square in $\mathbb{Z}_p$ if and only if its reduction is a square in $\mathbb{F}_p$, by Hensel's lemma for $X^2 - u$. Thus $(\mathbb{Z}_p^\times)^2$ has index 2 in $\mathbb{Z}_p^\times$, and $(\mathbb{Q}_p^\times)^2 = p^{2\mathbb{Z}} \times (\mathbb{Z}_p^\times)^2$ has index 4 in $\mathbb{Q}_p^\times$, with the representatives $1, \varepsilon, p, \varepsilon p$. A quadratic extension of $\mathbb{Q}_p$ is $\mathbb{Q}_p(\sqrt d)$ for a nonsquare $d$, and $d$ matters only modulo squares. So $\mathbb{Q}_p$ has exactly three quadratic extensions, $\mathbb{Q}_p(\sqrt \varepsilon)$, $\mathbb{Q}_p(\sqrt p)$ and $\mathbb{Q}_p(\sqrt{\varepsilon p})$.

**Proposition 2.5.4 (norm groups of quadratic extensions).** Let $p$ be odd. The norm groups of the three quadratic extensions of $\mathbb{Q}_p$ are as follows.
1. For $\mathbb{Q}_p(\sqrt\varepsilon)$ it is $p^{2\mathbb{Z}} \times \mathbb{Z}_p^\times$, the set of $x$ with $v_p(x)$ even.
2. For $\mathbb{Q}_p(\sqrt p)$ it is $(-p)^{\mathbb{Z}} \times (\mathbb{Z}_p^\times)^2$.
3. For $\mathbb{Q}_p(\sqrt{\varepsilon p})$ it is $(-\varepsilon p)^{\mathbb{Z}} \times (\mathbb{Z}_p^\times)^2$.

Lean: not stated yet

*Proof.* Part 1 is Theorem 2.2.3, since $\mathbb{Q}_p(\sqrt\varepsilon)$ is unramified. Let $d = p$ or $d = \varepsilon p$, and let $L = \mathbb{Q}_p(\sqrt d)$. The norm of $a + b \sqrt d$ is $a^2 - d b^2$. Thus the norm group contains the squares and $N(\sqrt d) = -d$. The subgroup generated by $-d$ and the squares is $(-d)^{\mathbb{Z}} \times (\mathbb{Z}_p^\times)^2$, because $(-d)^2 = d^2$ is $p^2$ times a square unit. This subgroup has index 2 in $\mathbb{Q}_p^\times$. By Theorem 2.1.2 the norm group also has index 2, so the two groups are equal. $\square$

The three norm groups are the three subgroups of index 2 of $\mathbb{Q}_p^\times$ that contain the squares. Thus every subgroup of index 2 is a norm group, as the existence theorem predicts. The three groups are different, as Proposition 2.1.7 predicts for three different fields.

**Example 2.5.5 (the quadratic characters).** For a nonsquare $d$, let $\chi_d : \mathbb{Q}_p^\times \to \{\pm 1\}$ be the character with kernel $N(\mathbb{Q}_p(\sqrt d)^\times)$. In the classical notation $\chi_d(x) = (x, d)_p$ is the Hilbert symbol. By Theorem 2.3.3, $\chi_d$ is the composite of $\mathrm{rec}$ with the nontrivial character of $\mathrm{Gal}(\mathbb{Q}_p(\sqrt d)/\mathbb{Q}_p)$. Since $\chi_d$ has order 2, the normalization of $\mathrm{rec}$ does not matter here. Let $\left(\frac{\cdot}{p}\right)$ be the Legendre symbol. Proposition 2.5.4 gives the values:
1. $\chi_\varepsilon(x) = (-1)^{v_p(x)}$.
2. $\chi_p(u) = \left(\frac{\bar u}{p}\right)$ for a unit $u$, and $\chi_p(p) = \chi_p(-1) \chi_p(-p) = \left(\frac{-1}{p}\right)$.
3. $\chi_{\varepsilon p}(u) = \left(\frac{\bar u}{p}\right)$ for a unit $u$, and $\chi_{\varepsilon p}(p) = -\left(\frac{-1}{p}\right)$.

For example, $\chi_p(p) = 1$ for $p = 5$, so 5 is a norm from $\mathbb{Q}_5(\sqrt 5)$. Indeed $5 = 5^2 - 5 \cdot 2^2$. For $p = 3$ one has $\chi_3(3) = -1$, so 3 is not a norm from $\mathbb{Q}_3(\sqrt 3)$, although $-3$ is one. The values show that $\chi_\varepsilon \chi_p = \chi_{\varepsilon p}$. This is the multiplicativity of the Hilbert symbol in its second variable.

**Remark 2.5.6 (the prime 2).** For $p = 2$ the squares of $\mathbb{Z}_2^\times$ are the units congruent to 1 modulo 8. Thus $\mathbb{Q}_2^\times / (\mathbb{Q}_2^\times)^2$ has order 8, with the representatives $\pm 1, \pm 2, \pm 5, \pm 10$, and $\mathbb{Q}_2$ has seven quadratic extensions. Only $\mathbb{Q}_2(\sqrt 5) = \mathbb{Q}_2(\sqrt{-3})$ is unramified. Exercise 9 computes their norm groups.
