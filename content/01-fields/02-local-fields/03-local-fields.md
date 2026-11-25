---
title: Local fields
nodes: []
sources: [Ser79]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Local fields

This section defines local fields and describes the multiplicative group of a nonarchimedean local field. We follow [Neu99], Chapter II, Section 5, and [Ser79], Chapters II and XIV.

### Definition and classification

**Definition 2.3.1 (local field).** A *local field* is a field $K$ with a nondiscrete topology for which $K$ is a locally compact topological field.

Lean: `IsNonarchimedeanLocalField`, from Mathlib, for the nonarchimedean case

**Theorem 2.3.2 (classification of local fields).** Each local field is isomorphic, as a topological field, to one of the following:
1. $\mathbb{R}$ or $\mathbb{C}$;
2. a finite extension of $\mathbb{Q}_p$ for a prime $p$;
3. the field $\mathbb{F}_q((t))$ of Laurent series over a finite field.

Conversely each of these fields is a local field. The topology of a local field is defined by an absolute value, and in cases 2 and 3 the absolute value is discrete and the residue field is finite.

Lean: not stated yet

*Proof sketch.* The converse follows from Proposition 2.3.3 below. For the main statement, a Haar measure $\mu$ on $K$ gives the function $|a| = \mu(aU) / \mu(U)$, where $U$ is a compact neighbourhood of 0. This function is an absolute value, or a power of one, and it defines the topology. If it is archimedean, $K$ contains $\mathbb{R}$ and is $\mathbb{R}$ or $\mathbb{C}$. If it is nonarchimedean, local compactness forces the valuation to be discrete and the residue field to be finite. If $K$ has characteristic 0, it contains $\mathbb{Q}$, the closure of $\mathbb{Q}$ is $\mathbb{Q}_p$ for some $p$ by Theorem 2.1.6, and $K$ is finite over $\mathbb{Q}_p$ by local compactness. If $K$ has characteristic $p$, the Teichmüller lift of Theorem 2.3.4 gives a copy of the residue field $\mathbb{F}_q$ in $K$, and a uniformizer $t$ gives $K = \mathbb{F}_q((t))$. See [Neu99], Chapter II, Proposition 5.2, and [CF67], Chapter II, Section 10. $\square$

From now on in this section, $K$ is a nonarchimedean local field. We use the notation of Volume 0, Chapter 3: the ring of integers $\mathcal{O}_K$, its maximal ideal $\mathfrak{p}_K$, a uniformizer $\varpi$, the residue field $k = \mathcal{O}_K / \mathfrak{p}_K$ with $q$ elements, the normalized valuation $v_K : K^\times \to \mathbb{Z}$, and the normalized absolute value $|x|_K = q^{-v_K(x)}$. The characteristic of $k$ is a prime $p$, and $q$ is a power of $p$.

**Proposition 2.3.3 (compactness).** Let $K$ be a field that is complete for a discrete nonarchimedean absolute value. Then $\mathcal{O}_K$ is compact if and only if the residue field is finite. In that case $\mathcal{O}_K \cong \varprojlim \mathcal{O}_K / \mathfrak{p}_K^n$ as a topological ring, the ideals $\mathfrak{p}_K^n$ form a basis of open neighbourhoods of 0, and $K$ is locally compact.

Lean: `IsNonarchimedeanLocalField`, from Mathlib, which provides `CompactSpace 𝒪[K]`

*Proof.* Each quotient $\mathcal{O}_K / \mathfrak{p}_K^n$ has a filtration with $n$ quotients $\mathfrak{p}_K^i / \mathfrak{p}_K^{i+1} \cong k$, so it is finite if $k$ is finite. The map $\mathcal{O}_K \to \varprojlim \mathcal{O}_K / \mathfrak{p}_K^n$ is injective because $\bigcap_n \mathfrak{p}_K^n = 0$, and surjective because $\mathcal{O}_K$ is complete. It is a homeomorphism, because the sets $\mathfrak{p}_K^n$ are the balls of radius $q^{-n}$ around 0. A projective limit of finite discrete sets is compact. Thus $\mathcal{O}_K$ is compact, and it is an open neighbourhood of 0 in $K$. Conversely, if $\mathcal{O}_K$ is compact, it is covered by the disjoint open sets $a + \mathfrak{p}_K$, so $k$ is finite. $\square$

Each $x \in \mathcal{O}_K$ has a unique expansion $x = \sum_{i \ge 0} a_i \varpi^i$ with $a_i$ in a fixed set $R$ of representatives of $k$ in $\mathcal{O}_K$ that contains 0. Each $x \in K^\times$ has such an expansion starting at $i = v_K(x)$. The next theorem gives a canonical set of representatives.

### Roots of unity

**Theorem 2.3.4 (Teichmüller representatives).** The field $K$ contains the group $\mu_{q-1}$ of $(q-1)$-th roots of unity, and reduction is an isomorphism $\mu_{q-1} \to k^\times$. For each $a \in k$ there is a unique $\omega(a) \in \mathcal{O}_K$ with $\omega(a)^q = \omega(a)$ and $\omega(a) \bmod \mathfrak{p}_K = a$. The map $\omega$ is multiplicative.

Lean: not stated yet

*Proof.* The polynomial $X^q - X$ has $q$ distinct roots in $k$, and each root is simple, because the derivative is $-1$ in $k$. By Theorem 2.2.3, each root $a$ lifts to a unique root $\omega(a)$ of $X^q - X$ in $\mathcal{O}_K$. Distinct elements of $k$ have distinct lifts, so $X^q - X$ has $q$ roots in $\mathcal{O}_K$, and these are $0$ and the group $\mu_{q-1}$. Multiplicativity follows from uniqueness, because $\omega(a)\omega(b)$ is a root of $X^q - X$ that lifts $ab$. $\square$

A second construction is $\omega(a) = \lim_{n} \tilde a^{q^n}$ for any lift $\tilde a$ of $a$. The sequence converges because $x \equiv y \pmod{\mathfrak{p}^m}$ implies $x^q \equiv y^q \pmod{\mathfrak{p}^{m+1}}$. This construction works also when $K$ has characteristic $p$.

### The unit filtration

**Definition 2.3.5 (the unit filtration).** The *group of units* is $U_K = U_K^{(0)} = \mathcal{O}_K^\times$. For $i \ge 1$, the group of *principal units of level $i$* is
$$U_K^{(i)} = 1 + \mathfrak{p}_K^i = \{x \in \mathcal{O}_K^\times : x \equiv 1 \pmod{\mathfrak{p}_K^i}\}.$$
The groups $U_K^{(i)}$ are open and compact, and they form a basis of neighbourhoods of 1 in $K^\times$.

**Proposition 2.3.6 (the quotients of the filtration).** Reduction modulo $\mathfrak{p}_K$ gives an isomorphism $U_K^{(0)} / U_K^{(1)} \cong k^\times$. For $i \ge 1$, the map $1 + \varpi^i x \mapsto x \bmod \mathfrak{p}_K$ gives an isomorphism $U_K^{(i)} / U_K^{(i+1)} \cong k$, where $k$ is the additive group.

Lean: not stated yet

*Proof.* The map $\mathcal{O}_K^\times \to k^\times$ is a surjective homomorphism with kernel $U_K^{(1)}$. For $i \ge 1$, $(1 + \varpi^i x)(1 + \varpi^i y) = 1 + \varpi^i (x + y + \varpi^i x y)$, and $\varpi^i x y \in \mathfrak{p}_K$. Thus the map $U_K^{(i)} \to k$ is a homomorphism. It is surjective, and its kernel is $U_K^{(i+1)}$. $\square$

Thus $[U_K : U_K^{(i)}] = (q - 1) q^{i-1}$ for $i \ge 1$. The group $U_K^{(1)}$ is the projective limit of the finite $p$-groups $U_K^{(1)} / U_K^{(i)}$, so it is a pro-$p$ group. In particular it is a $\mathbb{Z}_p$-module: for $u \in U_K^{(1)}$ and $a \in \mathbb{Z}_p$, the power $u^a = \lim u^{a_n}$ is defined for integers $a_n \to a$.

**Theorem 2.3.7 (the structure of $K^\times$).** The choice of a uniformizer $\varpi$ gives an isomorphism of topological groups
$$K^\times \cong \varpi^\mathbb{Z} \times \mu_{q-1} \times U_K^{(1)}, \qquad x = \varpi^{v_K(x)} \, \omega(\bar u) \, \frac{u}{\omega(\bar u)},$$
where $u = x \varpi^{-v_K(x)}$ and $\bar u$ is the image of $u$ in $k^\times$.

Lean: not stated yet

*Proof.* The valuation $v_K : K^\times \to \mathbb{Z}$ is surjective with kernel $\mathcal{O}_K^\times$, and $n \mapsto \varpi^n$ is a section. Thus $K^\times = \varpi^\mathbb{Z} \times \mathcal{O}_K^\times$. By Theorem 2.3.4, the map $\omega : k^\times \to \mu_{q-1}$ is a section of $\mathcal{O}_K^\times \to k^\times$, so $\mathcal{O}_K^\times = \mu_{q-1} \times U_K^{(1)}$ by Proposition 2.3.6. All maps are continuous, and $\varpi^\mathbb{Z}$ is discrete in $K^\times$. $\square$

**Proposition 2.3.8 (roots of principal units).** Let $m$ be an integer prime to $p$. Then each element of $U_K^{(1)}$ has a unique $m$-th root in $U_K^{(1)}$. Thus
$$K^\times / (K^\times)^m \cong \mathbb{Z}/m\mathbb{Z} \times \mu_{q-1} / \mu_{q-1}^m,$$
a group of order $m \cdot \gcd(m, q - 1)$.

Lean: not stated yet

*Proof.* Let $u \in U_K^{(1)}$ and $f = X^m - u$. Then $f(1) = 1 - u \in \mathfrak{p}_K$ and $f'(1) = m$ is a unit. By Theorem 2.2.3, $f$ has a unique root $y$ with $|y - 1| < 1$, that is, a unique root in $U_K^{(1)}$. The second claim follows from Theorem 2.3.7: the factor $\varpi^\mathbb{Z}$ contributes $\mathbb{Z}/m$, the cyclic factor $\mu_{q-1}$ contributes a group of order $\gcd(m, q-1)$, and $U_K^{(1)}$ contributes nothing. $\square$

### The case of characteristic zero

Let $K$ have characteristic 0, so that $K$ is a finite extension of $\mathbb{Q}_p$ of some degree $d$. Let $e = v_K(p)$ be its absolute ramification index. The logarithm
$$\log(1 + x) = \sum_{n \ge 1} (-1)^{n+1} \frac{x^n}{n}$$
converges on $\mathfrak{p}_K$, and the exponential $\exp(x) = \sum_{n \ge 0} x^n / n!$ converges on $\mathfrak{p}_K^i$ for $i > e/(p-1)$.

**Theorem 2.3.9 (the principal units in characteristic 0).** For $i > e/(p-1)$, the logarithm and the exponential are inverse isomorphisms of topological groups $U_K^{(i)} \cong \mathfrak{p}_K^i$. Thus $U_K^{(1)} \cong \mu_{p^a} \times \mathbb{Z}_p^d$, where $\mu_{p^a}$ is the group of roots of unity of $p$-power order in $K$, and
$$K^\times \cong \mathbb{Z} \times \mathbb{Z}/(q-1)\mathbb{Z} \times \mathbb{Z}/p^a\mathbb{Z} \times \mathbb{Z}_p^d.$$

Lean: not stated yet

*Proof sketch.* The estimate $v_p(n!) = (n - s_p(n))/(p - 1)$, where $s_p(n)$ is the sum of the digits of $n$ in base $p$, shows that $v_K(x^n / n!) - v_K(x) \ge (n - 1)(i - e/(p-1)) > 0$ for $v_K(x) = i$ and $n \ge 2$. Thus both series converge on $\mathfrak{p}_K^i$, they preserve the valuation, and the usual identities of power series show that they are inverse homomorphisms. The ideal $\mathfrak{p}_K^i$ is a free $\mathbb{Z}_p$-module of rank $d$, so $U_K^{(i)} \cong \mathbb{Z}_p^d$. The group $U_K^{(1)}$ is a finitely generated $\mathbb{Z}_p$-module, because $U_K^{(i)}$ has finite index in it. Its torsion is $\mu_{p^a}$, and its rank is $d$. See [Neu99], Chapter II, Proposition 5.5 and Proposition 5.7. $\square$

**Example 2.3.10 (the units of $\mathbb{Q}_p$).** Let $K = \mathbb{Q}_p$. Then $e = 1$, $d = 1$ and $q = p$. For odd $p$, there are no $p$-th roots of unity in $\mathbb{Q}_p$, since $\mathbb{Q}_p(\zeta_p)$ has degree $p - 1$ over $\mathbb{Q}_p$ by Exercise 3 of Section 2.6, and $1 + p\mathbb{Z}_p \cong \mathbb{Z}_p$ through the logarithm. Thus $\mathbb{Q}_p^\times \cong \mathbb{Z} \times \mathbb{Z}/(p-1) \times \mathbb{Z}_p$, and $\mathbb{Q}_p^\times / (\mathbb{Q}_p^\times)^2$ has order 4. For $p = 2$, we have $1 + 2 \mathbb{Z}_2 = \{\pm 1\} \times (1 + 4 \mathbb{Z}_2)$ and $1 + 4\mathbb{Z}_2 \cong \mathbb{Z}_2$. Thus $\mathbb{Q}_2^\times \cong \mathbb{Z} \times \mathbb{Z}/2 \times \mathbb{Z}_2$, and $\mathbb{Q}_2^\times / (\mathbb{Q}_2^\times)^2$ has order 8, with representatives $\pm 1, \pm 5, \pm 2, \pm 10$.

In characteristic $p$ the logarithm does not exist, and $U_K^{(1)}$ is a product of countably many copies of $\mathbb{Z}_p$ ([Neu99], Chapter II, Proposition 5.3). Thus $K^\times / (K^\times)^p$ is infinite. This is one reason why some arguments of Volume 3 need a separate treatment in characteristic $p$.
