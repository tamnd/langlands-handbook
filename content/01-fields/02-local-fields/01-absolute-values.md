---
title: Absolute values
nodes: []
sources: [Ser79]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Absolute values

This section defines absolute values and their equivalence. It proves Ostrowski's theorem for $\mathbb{Q}$, the product formula for $\mathbb{Q}$, and the approximation theorem of Artin and Whaples. We follow [Neu99], Chapter II, Sections 3 and 4.

### Definitions

**Definition 2.1.1 (absolute value).** An *absolute value* on a field $F$ is a map $|\cdot| : F \to \mathbb{R}_{\ge 0}$ with these properties:
1. $|x| = 0$ if and only if $x = 0$;
2. $|xy| = |x| \, |y|$;
3. $|x + y| \le |x| + |y|$.

The absolute value is *nonarchimedean* if it satisfies the stronger inequality $|x + y| \le \max(|x|, |y|)$, and *archimedean* otherwise. The *trivial* absolute value has $|x| = 1$ for all $x \ne 0$.

Lean: `AbsoluteValue`, from Mathlib

An absolute value defines a metric $d(x, y) = |x - y|$, and thus a topology on $F$. For this topology the field operations are continuous. The trivial absolute value gives the discrete topology.

**Example 2.1.2 (the absolute values of $\mathbb{Q}$).** The usual absolute value $|x|_\infty = \max(x, -x)$ is archimedean. Let $p$ be a prime. Each nonzero $x \in \mathbb{Q}$ is $x = p^{v} a / b$ with $a, b \in \mathbb{Z}$ prime to $p$, and the integer $v = v_p(x)$ is the $p$-adic valuation of $x$. The $p$-adic absolute value is $|x|_p = p^{-v_p(x)}$, with $|0|_p = 0$. It is nonarchimedean, because $v_p(x + y) \ge \min(v_p(x), v_p(y))$. More generally, let $F$ be a number field and $\mathfrak{p}$ a prime of $\mathcal{O}_F$. For $x \in F^\times$, let $v_\mathfrak{p}(x)$ be the exponent of $\mathfrak{p}$ in the factorization of $x \mathcal{O}_F$ (Theorem 1.2.4). Then $|x|_\mathfrak{p} = N(\mathfrak{p})^{-v_\mathfrak{p}(x)}$ is a nonarchimedean absolute value on $F$.

In a nonarchimedean absolute value, if $|x| \ne |y|$ then $|x + y| = \max(|x|, |y|)$. Indeed, let $|x| > |y|$. Then $|x| \le \max(|x + y|, |{-y}|)$ forces $|x| \le |x + y|$, and $|x + y| \le |x|$ holds anyway. Thus every triangle is isosceles, and every point of a ball is a center of the ball.

**Lemma 2.1.3 (a test for the nonarchimedean property).** An absolute value $|\cdot|$ on $F$ is nonarchimedean if and only if $|n \cdot 1| \le 1$ for all $n \in \mathbb{Z}$.

Lean: not stated yet

*Proof.* If $|\cdot|$ is nonarchimedean, then $|n \cdot 1| = |1 + \dots + 1| \le 1$ for $n \ge 0$, and $|{-1}| = 1$. Conversely, assume that $|n \cdot 1| \le 1$ for all $n$. Let $x, y \in F$ and $N \ge 1$. By the binomial theorem,
$$|x + y|^N = \Big| \sum_{k=0}^N \binom{N}{k} x^k y^{N-k} \Big| \le (N + 1) \max(|x|, |y|)^N.$$
Take the $N$-th root and let $N \to \infty$. Then $(N+1)^{1/N} \to 1$, so $|x + y| \le \max(|x|, |y|)$. $\square$

In particular every absolute value on a field of characteristic $p > 0$ is nonarchimedean, because the set $\{n \cdot 1\}$ is finite and its elements are roots of unity or $0$.

### Equivalence

**Definition 2.1.4 (equivalent absolute values).** Two absolute values on $F$ are *equivalent* if they define the same topology on $F$.

**Proposition 2.1.5 (criteria for equivalence).** Let $|\cdot|_1$ and $|\cdot|_2$ be absolute values on $F$, with $|\cdot|_1$ nontrivial. The following are equivalent.
1. They are equivalent.
2. For all $x \in F$, $|x|_1 < 1$ implies $|x|_2 < 1$.
3. There is a real number $s > 0$ with $|x|_2 = |x|_1^s$ for all $x \in F$.

Lean: `AbsoluteValue.isEquiv_iff_exists_rpow_eq`, from Mathlib

*Proof.* Part 3 implies part 1, because the two metrics have the same open balls around each point. Part 1 implies part 2: $|x|_1 < 1$ means that $x^n \to 0$ in the topology, so it is a property of the topology. Assume part 2. Choose $y \in F$ with $|y|_1 > 1$, which exists because $|\cdot|_1$ is nontrivial. Then $|y|_2 > 1$ by part 2 applied to $1/y$. Let $x \in F^\times$ and write $|x|_1 = |y|_1^\alpha$ with $\alpha \in \mathbb{R}$. Let $m/n$ be a rational number with $m/n > \alpha$ and $n > 0$. Then $|x^n / y^m|_1 < 1$, so $|x^n / y^m|_2 < 1$, and $|x|_2 < |y|_2^{m/n}$. In the same way $m/n < \alpha$ gives $|x|_2 > |y|_2^{m/n}$. Thus $|x|_2 = |y|_2^\alpha$. With $s = \log |y|_2 / \log |y|_1 > 0$ this gives $|x|_2 = |x|_1^s$. $\square$

An absolute value need not satisfy the triangle inequality after it is raised to a power $s > 1$. For example $|\cdot|_\infty^2$ on $\mathbb{Q}$ does not, because $|1 + 1|_\infty^2 = 4 > 2$. The handbook nevertheless uses the square of the usual absolute value at the complex places of a number field, as in Section 2.2. The topology is the same, and the product formula then holds without exponents.

### Ostrowski's theorem

**Theorem 2.1.6 (Ostrowski).** Each nontrivial absolute value on $\mathbb{Q}$ is equivalent to $|\cdot|_\infty$ or to $|\cdot|_p$ for exactly one prime $p$.

Lean: `Rat.AbsoluteValue.equiv_real_or_padic`, from Mathlib

*Proof.* Let $|\cdot|$ be a nontrivial absolute value on $\mathbb{Q}$. First assume that $|n| > 1$ for some integer $n$. Let $m, n \ge 2$ be integers. Write $m^k$ in base $n$, as $m^k = a_0 + a_1 n + \dots + a_r n^r$ with $0 \le a_i < n$ and $r \le k \log m / \log n$. Then
$$|m|^k \le \sum_{i=0}^r |a_i| \, |n|^i \le (1 + k \log m / \log n) \, n \, \max(1, |n|)^{k \log m / \log n}.$$
Take the $k$-th root and let $k \to \infty$. This gives $|m| \le \max(1, |n|)^{\log m / \log n}$. By assumption some $|m| > 1$, so $|n| > 1$ for all $n \ge 2$, by this inequality. Then the inequality reads $|m|^{1/\log m} \le |n|^{1/\log n}$, and by symmetry the two are equal. Thus $|n| = n^s$ for all $n \ge 2$, with a fixed $s > 0$, and $|\cdot|$ is equivalent to $|\cdot|_\infty$ by Proposition 2.1.5.

Now assume that $|n| \le 1$ for all integers $n$. The set $\mathfrak{a} = \{n \in \mathbb{Z} : |n| < 1\}$ is an ideal of $\mathbb{Z}$, because the absolute value is nonarchimedean by Lemma 2.1.3. It is not the unit ideal, since $|1| = 1$. It is not zero, because otherwise $|n| = 1$ for all nonzero integers, and the absolute value would be trivial. It is prime, because $|ab| = |a| \, |b| < 1$ implies $|a| < 1$ or $|b| < 1$. Thus $\mathfrak{a} = p\mathbb{Z}$ for a prime $p$. An integer $a$ prime to $p$ has $|a| = 1$. Write $x \in \mathbb{Q}^\times$ as $x = p^v a / b$ with $a, b$ prime to $p$. Then $|x| = |p|^v = |x|_p^s$ with $s = -\log |p| / \log p > 0$. The absolute values $|\cdot|_p$ for different $p$ are not equivalent, because $|p|_p < 1$ and $|p|_\ell = 1$ for $\ell \ne p$. $\square$

**Proposition 2.1.7 (the product formula for $\mathbb{Q}$).** For each $x \in \mathbb{Q}^\times$, we have $|x|_p = 1$ for almost all primes $p$, and
$$|x|_\infty \prod_p |x|_p = 1.$$

Lean: `NumberField.prod_abs_eq_one`, from Mathlib, for all number fields

*Proof.* Both sides are multiplicative in $x$, so it suffices to treat $x = -1$ and $x = \ell$ a prime. For $x = -1$ all factors are 1. For $x = \ell$ we have $|\ell|_\infty = \ell$, $|\ell|_\ell = \ell^{-1}$, and $|\ell|_p = 1$ for $p \ne \ell$. $\square$

### The approximation theorem

The Chinese remainder theorem finds an integer with given residues modulo finitely many primes. The approximation theorem is the analogue for finitely many inequivalent absolute values.

**Theorem 2.1.8 (weak approximation).** Let $|\cdot|_1, \dots, |\cdot|_n$ be nontrivial absolute values on $F$ that are pairwise inequivalent. Let $a_1, \dots, a_n \in F$ and $\varepsilon > 0$. Then there is $x \in F$ with $|x - a_i|_i < \varepsilon$ for $i = 1, \dots, n$. Equivalently, $F$ is dense in $\prod_i F_i$, where $F_i$ is $F$ with the topology of $|\cdot|_i$.

Lean: `AbsoluteValue.denseRange_algebraMap_pi`, from Mathlib

*Proof.* We first find $z \in F$ with $|z|_1 > 1$ and $|z|_i < 1$ for $i \ge 2$, by induction on $n$. For $n = 2$, Proposition 2.1.5 gives $\alpha$ with $|\alpha|_1 < 1$ and $|\alpha|_2 \ge 1$, and $\beta$ with $|\beta|_2 < 1$ and $|\beta|_1 \ge 1$. Then $z = \beta / \alpha$ works. For $n > 2$, the induction hypothesis gives $y$ with $|y|_1 > 1$ and $|y|_i < 1$ for $2 \le i \le n - 1$, and the case $n = 2$ gives $w$ with $|w|_1 > 1$ and $|w|_n < 1$. If $|y|_n < 1$, then $z = y$ works. If $|y|_n = 1$, then $z = y^m w$ works for $m$ large. If $|y|_n > 1$, then $z = w y^m / (1 + y^m)$ works for $m$ large, because $y^m / (1 + y^m)$ tends to 1 for $|\cdot|_1$ and $|\cdot|_n$, and to 0 for $|\cdot|_i$ with $2 \le i \le n - 1$.

The elements $z^m / (1 + z^m)$ tend to 1 for $|\cdot|_1$ and to 0 for $|\cdot|_i$ with $i \ge 2$, as $m \to \infty$. Thus for each $i$ there is $z_i \in F$ that is close to 1 for $|\cdot|_i$ and close to 0 for the others. The element $x = \sum_i a_i z_i$ has the required property if the $z_i$ are chosen close enough. $\square$

For $F = \mathbb{Q}$ and the absolute values $|\cdot|_p$ for finitely many $p$, the theorem is a weak form of the Chinese remainder theorem. It does not control the denominators at the other primes. Chapter 3 proves the stronger statement for number fields, in which all the other places are controlled as well.
