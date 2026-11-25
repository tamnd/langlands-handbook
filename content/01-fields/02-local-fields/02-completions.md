---
title: Completions and Hensel's lemma
nodes: []
sources: [Ser79]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Completions and Hensel's lemma

This section constructs the completion of a field for an absolute value, proves Hensel's lemma, and determines the absolute values of a number field. It also shows that an absolute value of a complete field extends uniquely to each finite extension. We follow [Neu99], Chapter II, Sections 1, 2, 4 and 8.

### Completions

A field $F$ with an absolute value is *complete* if each Cauchy sequence in $F$ converges.

**Proposition 2.2.1 (the completion).** Let $F$ be a field with an absolute value $|\cdot|$. There is a complete field $\hat F$ with an absolute value that extends $|\cdot|$, such that $F$ is dense in $\hat F$. It is unique up to a unique isomorphism over $F$ that preserves the absolute values. If $|\cdot|$ is nonarchimedean, then $|\hat F^\times| = |F^\times|$, and the residue fields of $F$ and $\hat F$ are equal.

Lean: `AbsoluteValue.Completion`, from Mathlib

*Proof.* Let $R$ be the ring of Cauchy sequences in $F$ and $\mathfrak{m}$ the ideal of sequences that tend to 0. A Cauchy sequence $(a_n)$ that does not tend to 0 has $|a_n| \ge c > 0$ for $n$ large, so it is invertible modulo $\mathfrak{m}$. Thus $\mathfrak{m}$ is maximal, and $\hat F = R / \mathfrak{m}$ is a field. The absolute value $|(a_n)| = \lim |a_n|$ is well defined, because $||a_n| - |a_m|| \le |a_n - a_m|$. The constant sequences embed $F$ in $\hat F$ with dense image, and a diagonal argument shows that $\hat F$ is complete. Uniqueness holds because a uniformly continuous map from $F$ to a complete field extends uniquely to $\hat F$. If $|\cdot|$ is nonarchimedean and $x = \lim a_n \ne 0$, then $|a_n| = |x|$ for $n$ large, because $|a_n - x| < |x|$. This gives $|\hat F^\times| = |F^\times|$. The same argument shows that each element of the valuation ring of $\hat F$ is congruent to an element of $F$ modulo the maximal ideal. $\square$

Let $|\cdot|$ be nonarchimedean. The *valuation ring* is $\mathcal{O} = \{x : |x| \le 1\}$. It is a local ring with the maximal ideal $\mathfrak{p} = \{x : |x| < 1\}$ and the unit group $\mathcal{O}^\times = \{x : |x| = 1\}$. The field $\kappa = \mathcal{O} / \mathfrak{p}$ is the *residue field*. The absolute value is *discrete* if $|F^\times|$ is a discrete subgroup of $\mathbb{R}_{>0}$. Then $|F^\times| = c^\mathbb{Z}$ for some $c < 1$, the function $v(x) = \log |x| / \log c$ is a surjective homomorphism $v : F^\times \to \mathbb{Z}$, and $v$ is the *normalized valuation*. An element $\varpi$ with $v(\varpi) = 1$ is a *uniformizer*. Each $x \in F^\times$ is $x = \varpi^{v(x)} u$ with $u \in \mathcal{O}^\times$, and each nonzero ideal of $\mathcal{O}$ is $\mathfrak{p}^n = \varpi^n \mathcal{O}$ for some $n \ge 0$. Thus $\mathcal{O}$ is a discrete valuation ring.

**Example 2.2.2 (the $p$-adic numbers).** The completion of $\mathbb{Q}$ for $|\cdot|_p$ is the field $\mathbb{Q}_p$ of $p$-adic numbers. Its valuation ring is the ring $\mathbb{Z}_p$ of $p$-adic integers, with maximal ideal $p\mathbb{Z}_p$ and residue field $\mathbb{F}_p$. The map $\mathbb{Z}_p \to \varprojlim \mathbb{Z} / p^n \mathbb{Z}$ is an isomorphism, because $\mathbb{Z}$ is dense in $\mathbb{Z}_p$ and $p^n \mathbb{Z}_p \cap \mathbb{Z} = p^n \mathbb{Z}$. Each $x \in \mathbb{Z}_p$ has a unique expansion
$$x = a_0 + a_1 p + a_2 p^2 + \cdots, \qquad a_i \in \{0, 1, \dots, p - 1\},$$
and each $x \in \mathbb{Q}_p^\times$ is $x = p^n u$ with $n = v_p(x) \in \mathbb{Z}$ and $u \in \mathbb{Z}_p^\times$. For example $-1 = \sum_{i \ge 0} (p-1) p^i$ in $\mathbb{Z}_p$. In the same way, for a prime $\mathfrak{p}$ of a number field $F$, the completion $F_\mathfrak{p}$ of $F$ for $|\cdot|_\mathfrak{p}$ has the valuation ring $\mathcal{O}_\mathfrak{p} = \varprojlim \mathcal{O}_F / \mathfrak{p}^n$ and the residue field $\mathcal{O}_F / \mathfrak{p}$.

### Hensel's lemma

Let $K$ be a field that is complete for a nonarchimedean absolute value, with valuation ring $\mathcal{O}$ and residue field $\kappa$. For $f \in \mathcal{O}[X]$, let $\bar f \in \kappa[X]$ be its reduction.

**Theorem 2.2.3 (Hensel's lemma, Newton form).** Let $f \in \mathcal{O}[X]$ and $a_0 \in \mathcal{O}$ with $|f(a_0)| < |f'(a_0)|^2$. Then there is a unique $a \in \mathcal{O}$ with $f(a) = 0$ and $|a - a_0| < |f'(a_0)|$. In particular a simple root of $\bar f$ in $\kappa$ lifts to a unique root of $f$ in $\mathcal{O}$.

Lean: `hensels_lemma`, from Mathlib, for $\mathbb{Z}_p$

*Proof.* Let $c = |f'(a_0)|$ and $t = |f(a_0)| / c^2 < 1$. Define $a_{n+1} = a_n - f(a_n) / f'(a_n)$. We show by induction that $a_n \in \mathcal{O}$, $|f'(a_n)| = c$ and $|f(a_n)| \le c^2 t^{2^n}$. Write the Taylor expansion
$$f(x + h) = f(x) + f'(x) h + h^2 g(x, h)$$
with $g \in \mathcal{O}[X, H]$. Let $h_n = -f(a_n) / f'(a_n)$. Then $|h_n| \le c t^{2^n} < c \le 1$, so $a_{n+1} \in \mathcal{O}$. Next $f'(a_{n+1}) = f'(a_n) + h_n \cdot (\text{an element of } \mathcal{O})$, and $|h_n| < c$, so $|f'(a_{n+1})| = c$. Finally $f(a_{n+1}) = h_n^2 g(a_n, h_n)$, so $|f(a_{n+1})| \le |h_n|^2 \le c^2 t^{2^{n+1}}$. Since $|a_{n+1} - a_n| = |h_n| \to 0$, the sequence is Cauchy, and it has a limit $a \in \mathcal{O}$ with $f(a) = 0$. Also $|a - a_0| \le \max_n |h_n| \le ct < c$. For uniqueness, let $b$ be a second root with $|b - a_0| < c$, and put $h = b - a$. Then $|h| < c$ and $0 = f(b) = h(f'(a) + h g(a, h))$. Here $|f'(a)| = c > |h g(a, h)|$, so the second factor is not zero, and $h = 0$. For the last claim, a simple root $\bar a_0$ of $\bar f$ has $|f(a_0)| < 1 = |f'(a_0)|$ for each lift $a_0$. $\square$

**Theorem 2.2.4 (Hensel's lemma, factorization form).** Let $f \in \mathcal{O}[X]$ be a polynomial with $\bar f \ne 0$, and let $\bar f = \bar g \bar h$ with coprime $\bar g, \bar h \in \kappa[X]$. Then there are $g, h \in \mathcal{O}[X]$ with $f = g h$, with reductions $\bar g$ and $\bar h$, and with $\deg g = \deg \bar g$.

Lean: `HenselianLocalRing`, from Mathlib, for the form with one simple root

*Proof sketch.* One constructs $g_n, h_n$ with $f \equiv g_n h_n \pmod{\varpi^n}$ step by step, where $\varpi$ is an element of $\mathfrak{p}$ that is large enough. The correction at each step solves a linear equation $a g_n + b h_n \equiv r$, which is possible because $\bar g$ and $\bar h$ are coprime. The limits $g$ and $h$ exist by completeness. See [Neu99], Chapter II, Lemma 4.6. $\square$

**Corollary 2.2.5 (coefficients of irreducible polynomials).** Let $f = a_n X^n + \dots + a_0 \in K[X]$ be irreducible with $a_0 a_n \ne 0$. Then $\max_i |a_i| = \max(|a_0|, |a_n|)$. In particular, if $f$ is monic and $f(0) \in \mathcal{O}$, then $f \in \mathcal{O}[X]$.

Lean: not stated yet

*Proof.* Multiply $f$ by a constant so that $\max_i |a_i| = 1$. Let $r$ be the least index with $|a_r| = 1$. Then $\bar f = X^r (\bar a_r + \dots + \bar a_n X^{n-r})$. If $0 < r < n$, this is a product of two coprime polynomials of positive degree, and Theorem 2.2.4 factors $f$, a contradiction. Thus $r = 0$ or $r = n$, and $\max(|a_0|, |a_n|) = 1$. $\square$

**Example 2.2.6 (roots of unity and squares in $\mathbb{Q}_p$).** The polynomial $X^{p-1} - 1$ has $p - 1$ simple roots in $\mathbb{F}_p$. By Theorem 2.2.3 it has $p - 1$ roots in $\mathbb{Z}_p$, so $\mathbb{Q}_p$ contains the group $\mu_{p-1}$ of $(p-1)$-th roots of unity, and reduction maps it isomorphically onto $\mathbb{F}_p^\times$. Let $p$ be odd and $u \in \mathbb{Z}_p^\times$. Then $u$ is a square in $\mathbb{Z}_p$ if and only if $u \bmod p$ is a square in $\mathbb{F}_p$, by Theorem 2.2.3 applied to $X^2 - u$. For $p = 2$, apply Theorem 2.2.3 to $f = X^2 - u$ and $a_0 = 1$, with $|f'(1)|^2 = 1/4$. This shows that $u \in \mathbb{Z}_2^\times$ is a square if $u \equiv 1 \pmod 8$, and the converse is easy.

### Extension of absolute values

**Theorem 2.2.7 (extension to a finite extension).** Let $K$ be complete for an absolute value $|\cdot|$, and let $L / K$ be a finite extension of degree $n$. Then $|\cdot|$ has exactly one extension to an absolute value on $L$, namely
$$|x|_L = |N_{L/K}(x)|^{1/n},$$
and $L$ is complete for it. If $|\cdot|$ is nonarchimedean, the valuation ring of $L$ is the integral closure of $\mathcal{O}$ in $L$.

Lean: `spectralNorm_unique`, from Mathlib, for the uniqueness

*Proof.* Uniqueness. Two norms on a finite dimensional vector space over a complete field are equivalent, in the sense that each is bounded by a constant times the other ([Neu99], Chapter II, Proposition 4.9). Let $|\cdot|_1$ and $|\cdot|_2$ be two extensions. They define the same topology on $L$. By Proposition 2.1.5, $|\cdot|_2 = |\cdot|_1^s$, and $s = 1$ because they agree on $K$.

Existence in the archimedean case. By Ostrowski's theorem on complete archimedean fields, $K$ is $\mathbb{R}$ or $\mathbb{C}$, up to a power of the absolute value ([Neu99], Chapter II, Theorem 4.2). Then $L$ is $\mathbb{R}$ or $\mathbb{C}$, and the formula gives the usual absolute value.

Existence in the nonarchimedean case. Let $\mathcal{O}_L$ be the integral closure of $\mathcal{O}$ in $L$. For $x \in L^\times$ with minimal polynomial $f$ of degree $d$ over $K$, we have $N_{L/K}(x) = \pm f(0)^{n/d}$. By Corollary 2.2.5, $x \in \mathcal{O}_L$ if and only if $f(0) \in \mathcal{O}$, that is, if and only if $|x|_L \le 1$. The formula is multiplicative and $|x|_L = 0$ only for $x = 0$. For the ultrametric inequality it suffices to show that $|x|_L \le 1$ implies $|1 + x|_L \le 1$, after dividing by the larger of the two terms. This holds because $x \in \mathcal{O}_L$ implies $1 + x \in \mathcal{O}_L$. Completeness follows from the equivalence of norms, because $L \cong K^n$ as a normed vector space. $\square$

Let $K$ be complete for a discrete nonarchimedean absolute value, and $L / K$ finite. The absolute value of $L$ is again discrete. Let $\varpi_L$ be a uniformizer of $L$ and $\kappa_L$ the residue field. The *ramification index* is $e = e(L/K) = v_L(\varpi_K)$, so that $|L^\times| / |K^\times|$ has order $e$. The *residue degree* is $f = f(L/K) = [\kappa_L : \kappa]$. Section 2.4 proves that $ef = n$ when $K$ is a local field.

### The places of a number field

Let $F$ be a number field. For a prime $\mathfrak{p}$ of $\mathcal{O}_F$, the absolute value $|\cdot|_\mathfrak{p}$ of Example 2.1.2 is nonarchimedean. For an embedding $\sigma : F \to \mathbb{C}$, the map $x \mapsto |\sigma(x)|$ is an archimedean absolute value. Conjugate embeddings give the same absolute value.

**Theorem 2.2.8 (the places of a number field).** Each nontrivial absolute value on $F$ is equivalent to exactly one of the following: $|\cdot|_\mathfrak{p}$ for a prime $\mathfrak{p}$ of $\mathcal{O}_F$, or $|\sigma(\cdot)|$ for a real embedding $\sigma$ or a pair $\{\sigma, \bar\sigma\}$ of complex embeddings.

Lean: `NormedAlgebra.Real.nonempty_algEquiv_or`, from Mathlib, for the archimedean step

*Proof.* Let $|\cdot|$ be nonarchimedean. Then $|n| \le 1$ for $n \in \mathbb{Z}$. Each $x \in \mathcal{O}_F$ satisfies a monic equation $x^m = -(c_{m-1} x^{m-1} + \dots + c_0)$ with $c_i \in \mathbb{Z}$. If $|x| > 1$, the right side has absolute value at most $|x|^{m-1} < |x|^m$, a contradiction. Thus $\mathcal{O}_F$ is contained in the valuation ring, and $\mathfrak{p} = \{x \in \mathcal{O}_F : |x| < 1\}$ is a prime ideal. It is not zero, because otherwise $|x| = 1$ for all $x \in \mathcal{O}_F \setminus \{0\}$, and then for all $x \in F^\times$. Elements of $\mathcal{O}_F \setminus \mathfrak{p}$ have absolute value 1. Thus the valuation ring of $|\cdot|$ contains the localization $\mathcal{O}_{F,\mathfrak{p}}$. This ring is a discrete valuation ring by Exercise 4 of Section 1.6. Let $\varpi$ be a generator of its maximal ideal. Each $x \in F^\times$ is $x = \varpi^k u$ with $k = v_\mathfrak{p}(x)$ and $u \in \mathcal{O}_{F,\mathfrak{p}}^\times$, so $|x| = |\varpi|^k$. Thus $|\cdot| = |\cdot|_\mathfrak{p}^s$ with $s = -\log|\varpi| / \log N(\mathfrak{p}) > 0$.

Let $|\cdot|$ be archimedean. By Ostrowski's theorem for $\mathbb{Q}$, the restriction to $\mathbb{Q}$ is a power of $|\cdot|_\infty$, and the closure of $\mathbb{Q}$ in the completion $\hat F$ is $\mathbb{R}$. The field $\hat F$ is generated over $\mathbb{R}$ by $F$, so it is a finite extension of $\mathbb{R}$. Thus $\hat F \cong \mathbb{R}$ or $\hat F \cong \mathbb{C}$, and the map $F \to \hat F$ is an embedding $\sigma$. By Theorem 2.2.7, the absolute value of $\hat F$ is a power of the usual one, so $|\cdot|$ is equivalent to $|\sigma(\cdot)|$. Two embeddings give equivalent absolute values only if they are equal or conjugate, by Proposition 2.1.5 and the density of $F$ in its completion. $\square$

**Definition 2.2.9 (places and normalized absolute values).** A *place* of $F$ is an equivalence class of nontrivial absolute values on $F$. The places are the *finite places* $\mathfrak{p}$ and the *infinite places*, which are real or complex. We write $v \mid \infty$ for an infinite place, $F_v$ for the completion, and we use these *normalized absolute values*:
$$|x|_v = N(\mathfrak{p})^{-v_\mathfrak{p}(x)} \text{ for } v = \mathfrak{p}, \qquad |x|_v = |\sigma(x)| \text{ for } v \text{ real}, \qquad |x|_v = |\sigma(x)|^2 \text{ for } v \text{ complex}.$$

Lean: `NumberField.InfinitePlace`, from Mathlib, for the infinite places

**Theorem 2.2.10 (the product formula).** For $x \in F^\times$, we have $|x|_v = 1$ for almost all places $v$, and
$$\prod_v |x|_v = 1.$$

Lean: `NumberField.prod_abs_eq_one`, from Mathlib

*Proof.* The ideal $x \mathcal{O}_F$ has only finitely many prime factors, so $|x|_\mathfrak{p} = 1$ for almost all $\mathfrak{p}$. By the definitions, $\prod_{\mathfrak{p}} |x|_\mathfrak{p} = \prod_\mathfrak{p} N(\mathfrak{p})^{-v_\mathfrak{p}(x)} = N(x\mathcal{O}_F)^{-1}$. By Proposition 1.2.9, $N(x\mathcal{O}_F) = |N_{F/\mathbb{Q}}(x)|$. On the other hand, $\prod_{v \mid \infty} |x|_v = \prod_\sigma |\sigma(x)| = |N_{F/\mathbb{Q}}(x)|$, where $\sigma$ runs over all embeddings, because a complex place counts two conjugate embeddings. The two products are inverse to each other. $\square$

A second proof of the product formula, through Haar measures, is in Section 3.3. For a finite place $v = \mathfrak{p}$ the normalized absolute value has a meaning in terms of measure: multiplication by $x$ multiplies the Haar measure of $F_v$ by $|x|_v$. The same holds at the complex places, because multiplication by $z$ on $\mathbb{C} \cong \mathbb{R}^2$ has determinant $|z|^2$.
