---
title: Lubin-Tate formal groups
nodes: []
sources: [Ser67, Mil20]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Lubin-Tate formal groups

Fix a uniformizer $\varpi$ of $K$. The construction starts with a power series that plays the role of $(1 + X)^p - 1$ for $\mathbb{Q}_p$.

**Definition 3.2.1 (Lubin-Tate series).** Let $\mathcal{F}_\varpi$ be the set of power series $f \in \mathcal{O}_K[[X]]$ with $f(X) \equiv \varpi X$ modulo degree 2 and $f(X) \equiv X^q$ modulo $\varpi$.

Lean: not stated yet

The polynomial $\varpi X + X^q$ is in $\mathcal{F}_\varpi$. For $K = \mathbb{Q}_p$ and $\varpi = p$, the polynomial $(1 + X)^p - 1 = pX + \dots + X^p$ is in $\mathcal{F}_p$, because the binomial coefficients $\binom{p}{i}$ with $0 < i < p$ are divisible by $p$.

The main tool is the following lemma. It says that a power series that commutes with two Lubin-Tate series is determined by its linear term.

**Lemma 3.2.2 (Lubin-Tate lemma).** Let $f, g \in \mathcal{F}_\varpi$ and let $\varphi_1(X_1, \dots, X_m) = \sum_i a_i X_i$ be a linear form with coefficients in $\mathcal{O}_K$. There is a unique power series $\varphi \in \mathcal{O}_K[[X_1, \dots, X_m]]$ with $\varphi \equiv \varphi_1$ modulo degree 2 and
$$f(\varphi(X_1, \dots, X_m)) = \varphi(g(X_1), \dots, g(X_m)).$$

Lean: not stated yet

*Proof.* Write $X$ for $(X_1, \dots, X_m)$ and $g(X)$ for $(g(X_1), \dots, g(X_m))$. We show by induction on $r \ge 1$ that there is a unique polynomial $\varphi_r$ of degree at most $r$ with $\varphi_r \equiv \varphi_1$ modulo degree 2 and
$$f(\varphi_r(X)) \equiv \varphi_r(g(X)) \pmod{\deg r + 1}.$$
For $r = 1$, both sides are $\varpi \varphi_1(X)$ modulo degree 2, since $f$ and $g$ are $\varpi X$ modulo degree 2. Assume that $\varphi_r$ exists and is unique. Each solution of degree at most $r+1$ modulo degree $r+2$ is then $\varphi_{r+1} = \varphi_r + h$, with $h$ homogeneous of degree $r + 1$. We compute both sides modulo degree $r + 2$. The derivative of $f$ is $\varpi$ modulo degree 1, so $f(\varphi_r + h) \equiv f(\varphi_r) + \varpi h$. Since $g(X_i) \equiv \varpi X_i$ modulo degree 2 and $h$ is homogeneous of degree $r+1$, we get $h(g(X)) \equiv \varpi^{r+1} h(X)$. Let $E$ be the homogeneous part of degree $r + 1$ of $\varphi_r(g(X)) - f(\varphi_r(X))$. The condition on $h$ becomes
$$(\varpi - \varpi^{r+1}) \, h = E.$$
Now $\varpi - \varpi^{r+1} = \varpi (1 - \varpi^r)$, and $1 - \varpi^r$ is a unit. Thus there is a unique solution $h$ with coefficients in $K$, and it has coefficients in $\mathcal{O}_K$ if and only if $E \equiv 0$ modulo $\varpi$. Modulo $\varpi$ we have $f(Y) \equiv Y^q$ and $g(Y) \equiv Y^q$, so
$$\varphi_r(g(X)) - f(\varphi_r(X)) \equiv \varphi_r(X_1^q, \dots, X_m^q) - \varphi_r(X)^q \pmod \varpi.$$
The ring $\mathcal{O}_K / \varpi$ is the field $k$ with $q$ elements. In a ring of characteristic $p$, the map $y \mapsto y^q$ is additive, and $a^q = a$ for $a \in k$. Thus $\varphi_r(X)^q \equiv \varphi_r(X_1^q, \dots, X_m^q)$ modulo $\varpi$, and $E \equiv 0$ modulo $\varpi$. This completes the induction. The polynomials $\varphi_r$ agree modulo degree $r + 1$, by uniqueness, so they define a power series $\varphi$. It satisfies the identity in every degree. Uniqueness of $\varphi$ follows from uniqueness of each $\varphi_r$. $\square$

The proof uses the two conditions on $f$ in two places. The linear term $\varpi X$ makes the coefficient $\varpi - \varpi^{r+1}$ nonzero. The congruence $f \equiv X^q$ makes the error term divisible by $\varpi$.

**Theorem 3.2.3 (Lubin-Tate formal groups).** Let $f, g \in \mathcal{F}_\varpi$.
1. There is a unique formal group law $F_f$ over $\mathcal{O}_K$ with $f(F_f(X, Y)) = F_f(f(X), f(Y))$.
2. For each $a \in \mathcal{O}_K$ there is a unique $[a]_{g,f} \in \mathcal{O}_K[[X]]$ with $[a]_{g,f}(X) \equiv aX$ modulo degree 2 and $g \circ [a]_{g,f} = [a]_{g,f} \circ f$. It is a homomorphism $F_f \to F_g$.
3. With $[a]_f = [a]_{f,f}$, the map $a \mapsto [a]_f$ makes $F_f$ a formal $\mathcal{O}_K$-module, and $[\varpi]_f = f$.
4. The homomorphism $[1]_{g,f}$ is an isomorphism $F_f \to F_g$ with inverse $[1]_{f,g}$. It satisfies $[1]_{g,f} \circ [a]_f = [a]_g \circ [1]_{g,f}$.

Lean: not stated yet

*Proof.* All parts follow from the uniqueness in Lemma 3.2.2. For part 1, let $F_f$ be the series given by the lemma with $m = 2$, $\varphi_1 = X + Y$ and $g = f$. Both $F_f(X, F_f(Y, Z))$ and $F_f(F_f(X, Y), Z)$ are congruent to $X + Y + Z$ modulo degree 2, and both commute with $f$ in the sense of the lemma. For example,
$$f(F_f(X, F_f(Y, Z))) = F_f(f(X), f(F_f(Y, Z))) = F_f(f(X), F_f(f(Y), f(Z))).$$
By uniqueness they are equal. The same argument with $F_f(Y, X)$ gives commutativity. Uniqueness of $F_f$ is part of the lemma.

For part 2, the lemma with $m = 1$ gives $[a]_{g,f}$. The two series $[a]_{g,f}(F_f(X, Y))$ and $F_g([a]_{g,f}(X), [a]_{g,f}(Y))$ are congruent to $aX + aY$ modulo degree 2. Both satisfy $g \circ \varphi = \varphi(f(X), f(Y))$, by the defining properties of $F_f$, $F_g$ and $[a]_{g,f}$. So they are equal.

For part 3, the series $[a + b]_f$ and $F_f([a]_f, [b]_f)$ are both congruent to $(a + b) X$ and both commute with $f$. So they are equal. In the same way $[ab]_f = [a]_f \circ [b]_f$ and $[1]_f = X$. Thus $a \mapsto [a]_f$ is a ring homomorphism to $\mathrm{End}(F_f)$. The series $f$ itself is congruent to $\varpi X$ and commutes with $f$, so $[\varpi]_f = f$.

For part 4, the composite $[1]_{f,g} \circ [1]_{g,f}$ is congruent to $X$ and commutes with $f$, so it is $[1]_f = X$. In the same way $[1]_{g,f} \circ [1]_{f,g} = X$. The last identity holds because both sides are congruent to $aX$ and both intertwine $f$ with $g$. $\square$

The formal group $F_f$ is the *Lubin-Tate formal group* of $f$. By part 4, its isomorphism class over $\mathcal{O}_K$, with its $\mathcal{O}_K$-module structure, depends only on $\varpi$.

**Example 3.2.4 ($\mathbb{Q}_p$ and the multiplicative group).** Let $K = \mathbb{Q}_p$, $\varpi = p$ and $f(X) = (1 + X)^p - 1$. Then
$$f(\mathbb{G}_m(X, Y)) = (1 + X)^p (1 + Y)^p - 1 = \mathbb{G}_m(f(X), f(Y)),$$
so $F_f = \mathbb{G}_m$ by uniqueness. For $a \in \mathbb{Z}_p$, the series $(1 + X)^a - 1 = \sum_{n \ge 1} \binom{a}{n} X^n$ has coefficients in $\mathbb{Z}_p$, it is congruent to $aX$, and it commutes with $f$. Thus $[a]_f(X) = (1 + X)^a - 1$. The formal $\mathbb{Z}_p$-module $F_f$ is the multiplicative group with its natural action of $\mathbb{Z}_p$ by powers.

**Example 3.2.5 (the polynomial $\varpi X + X^q$).** Let $f = \varpi X + X^q$. For a root of unity $\zeta$ of order $q - 1$ in $K$, the series $\zeta X$ commutes with $f$, because $\zeta^q = \zeta$. Thus $[\zeta]_f(X) = \zeta X$. The group law $F_f$ is congruent to $X + Y$ modulo degree $q$, see Exercise 3. If $K = \mathbb{F}_q((t))$ and $\varpi = t$, then $X + Y$ itself commutes with $f$, so $F_f = \mathbb{G}_a$, and $[a]_f$ is an additive polynomial for $a \in \mathbb{F}_q[t]$. This is the Carlitz module.
