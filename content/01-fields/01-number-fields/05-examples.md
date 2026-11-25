---
title: Quadratic and cyclotomic fields
nodes: []
sources: [Ser79]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Quadratic and cyclotomic fields

This section computes the objects of Sections 1.1 to 1.4 for two families of fields. The results are used in every later volume. The cyclotomic fields are the first case of class field theory: the Frobenius element of $p$ in $\mathbb{Q}(\zeta_m)$ is the class of $p$ in $(\mathbb{Z}/m\mathbb{Z})^\times$. We follow [Neu99], Chapter I, Sections 8 and 10.

### Quadratic fields

Let $d \ne 0, 1$ be a squarefree integer, $F = \mathbb{Q}(\sqrt d)$, and $d_F$ the discriminant of Example 1.1.8. For an odd prime $p$, the Legendre symbol $(d / p)$ is $0$ if $p \mid d$, $1$ if $d$ is a nonzero square modulo $p$, and $-1$ otherwise.

**Proposition 1.5.1 (primes in quadratic fields).** Let $p$ be a prime number.
1. The prime $p$ is ramified in $F$ if and only if $p \mid d_F$.
2. Let $p$ be odd with $p \nmid d$. Then $p$ splits if $(d/p) = 1$, and $p$ is inert if $(d/p) = -1$.
3. Let $d \equiv 1 \pmod 4$. Then $2$ splits if $d \equiv 1 \pmod 8$, and $2$ is inert if $d \equiv 5 \pmod 8$.

Lean: not stated yet

*Proof.* We use Theorem 1.4.2 with $\mathcal{O}_F = \mathbb{Z}[\omega]$. If $\omega = \sqrt d$, the minimal polynomial is $X^2 - d$. Modulo an odd prime $p$, it is $X^2$ if $p \mid d$, a product of two distinct linear factors if $(d/p) = 1$, and irreducible if $(d/p) = -1$. Modulo $2$, it is $(X - d)^2$, so $2$ is ramified, and $2 \mid d_F = 4d$. If $\omega = (1 + \sqrt d)/2$, the minimal polynomial is $X^2 - X + (1 - d)/4$. For odd $p$ its discriminant is $d$, and the same analysis applies. Modulo $2$ it is $X^2 + X$ if $d \equiv 1 \pmod 8$ and $X^2 + X + 1$ if $d \equiv 5 \pmod 8$. The first polynomial has two distinct roots in $\mathbb{F}_2$, and the second is irreducible. In this case $d_F = d$ is odd. $\square$

The Galois group of $F / \mathbb{Q}$ is $\{\pm 1\}$. For an unramified prime $p$, the Frobenius element is $1$ if $p$ splits and $-1$ if $p$ is inert. Thus $\mathrm{Frob}_p = (d/p)$ for odd $p \nmid d$. The Kronecker symbol $(d_F / \cdot)$ extends this to all $p$. It is a Dirichlet character modulo $|d_F|$, a fact that is equivalent to quadratic reciprocity.

**Example 1.5.2 (sums of two squares).** Let $F = \mathbb{Q}(i)$. Then $d = -1$, $d_F = -4$, and $(-1/p) = (-1)^{(p-1)/2}$ for odd $p$ by Euler's criterion. Thus an odd prime $p$ splits in $\mathbb{Z}[i]$ if and only if $p \equiv 1 \pmod 4$. The ring $\mathbb{Z}[i]$ is a principal ideal domain by Example 1.3.7. If $p \equiv 1 \pmod 4$, then $p \mathbb{Z}[i] = (a + bi)(a - bi)$ for some $a, b \in \mathbb{Z}$, and taking norms gives $p = a^2 + b^2$. Conversely a square is $0$ or $1$ modulo $4$, so a sum of two squares is never $3$ modulo $4$. This is Fermat's theorem on sums of two squares.

### Cyclotomic fields

Let $m \ge 1$ and let $\zeta = \zeta_m$ be a primitive $m$-th root of unity. The field $\mathbb{Q}(\zeta_m)$ is the splitting field of $X^m - 1$, so it is Galois over $\mathbb{Q}$. The cyclotomic polynomial is $\Phi_m(X) = \prod_a (X - \zeta^a)$, where $a$ runs over $(\mathbb{Z}/m\mathbb{Z})^\times$. It has integer coefficients, because $X^m - 1 = \prod_{k \mid m} \Phi_k(X)$ and induction on $m$. If $m$ is odd, then $-\zeta_m$ is a primitive $2m$-th root of unity, and $\mathbb{Q}(\zeta_{2m}) = \mathbb{Q}(\zeta_m)$. Thus we may assume $m \not\equiv 2 \pmod 4$ when this is convenient.

**Theorem 1.5.3 (irreducibility of the cyclotomic polynomial).** The polynomial $\Phi_m$ is irreducible over $\mathbb{Q}$. Thus $[\mathbb{Q}(\zeta_m) : \mathbb{Q}] = \varphi(m)$, and there is an isomorphism
$$(\mathbb{Z}/m\mathbb{Z})^\times \xrightarrow{\sim} \mathrm{Gal}(\mathbb{Q}(\zeta_m) / \mathbb{Q}), \qquad a \mapsto \sigma_a, \quad \sigma_a(\zeta) = \zeta^a.$$

Lean: `Polynomial.cyclotomic.irreducible_rat` and `IsCyclotomicExtension.autEquivPow`, from Mathlib

*Proof.* Let $f$ be the minimal polynomial of $\zeta$ over $\mathbb{Q}$. It is monic and divides $X^m - 1$. Its roots are algebraic integers, so its coefficients are algebraic integers in $\mathbb{Q}$, that is, integers. Let $p$ be a prime with $p \nmid m$. We show that $\zeta^p$ is a root of $f$. Write $X^m - 1 = f g$ with $g \in \mathbb{Z}[X]$ monic, and assume that $f(\zeta^p) \ne 0$. Then $g(\zeta^p) = 0$, so $\zeta$ is a root of $g(X^p)$, and $f$ divides $g(X^p)$ in $\mathbb{Z}[X]$. Reduce modulo $p$. In $\mathbb{F}_p[X]$ we have $\bar g(X^p) = \bar g(X)^p$, so $\bar f$ and $\bar g$ have a common irreducible factor. This factor divides $X^m - 1$ twice. But $X^m - 1$ is separable over $\mathbb{F}_p$, because its derivative $m X^{m-1}$ is prime to it. This is a contradiction. Now let $a$ be prime to $m$, and write $a = p_1 \cdots p_k$ with primes $p_i \nmid m$. Applying the claim $k$ times shows that $\zeta^a$ is a root of $f$. Thus all roots of $\Phi_m$ are roots of $f$, and $f = \Phi_m$. Each $\sigma \in \mathrm{Gal}(\mathbb{Q}(\zeta)/\mathbb{Q})$ maps $\zeta$ to a root $\zeta^a$ of $\Phi_m$, and $\sigma$ is determined by $a$. This gives the isomorphism. $\square$

The next theorem treats the case of a prime $p$ in full. Let $\zeta = \zeta_p$ and $\pi = 1 - \zeta$.

**Theorem 1.5.4 (the field of $p$-th roots of unity).** Let $p$ be an odd prime and $F = \mathbb{Q}(\zeta_p)$.
1. The ideal $\pi \mathcal{O}_F$ is prime, and $p \mathcal{O}_F = (\pi \mathcal{O}_F)^{p-1}$. Thus $p$ is totally ramified in $F$.
2. The discriminant of the basis $1, \zeta, \dots, \zeta^{p-2}$ is $(-1)^{(p-1)/2} p^{p-2}$.
3. $\mathcal{O}_F = \mathbb{Z}[\zeta]$, and $d_F = (-1)^{(p-1)/2} p^{p-2}$.

Lean: `IsCyclotomicExtension.Rat.isIntegralClosure_adjoin_singleton` and `IsCyclotomicExtension.Rat.discr_odd_prime'`, from Mathlib

*Proof.* For part 1, evaluate $\Phi_p(X) = 1 + X + \dots + X^{p-1} = \prod_{a=1}^{p-1} (X - \zeta^a)$ at $X = 1$. This gives $p = \prod_{a=1}^{p-1} (1 - \zeta^a)$. For each $a$, the quotient $(1 - \zeta^a)/(1 - \zeta) = 1 + \zeta + \dots + \zeta^{a-1}$ is in $\mathbb{Z}[\zeta]$. Its inverse $(1 - \zeta)/(1 - \zeta^a)$ is also in $\mathbb{Z}[\zeta]$, because $\zeta = (\zeta^a)^b$ for $ab \equiv 1 \pmod p$. Thus $p = u \pi^{p-1}$ with a unit $u$. The ideal $\pi \mathcal{O}_F$ is not the unit ideal, because $N(\pi) = \Phi_p(1) = p$. By Theorem 1.4.1, the equation $p\mathcal{O}_F = (\pi\mathcal{O}_F)^{p-1}$ with $p - 1 = [F : \mathbb{Q}]$ forces $\pi \mathcal{O}_F$ to be prime, with $f = 1$.

For part 2, the discriminant of the basis $1, \theta, \dots, \theta^{n-1}$, where $\theta$ has minimal polynomial $h$ of degree $n$, is $\prod_{i < j} (\theta_i - \theta_j)^2 = (-1)^{n(n-1)/2} N(h'(\theta))$. Here $n = p - 1$. Differentiate $(X - 1)\Phi_p(X) = X^p - 1$ and put $X = \zeta$. This gives $(\zeta - 1) \Phi_p'(\zeta) = p \zeta^{p-1}$. Take norms. We have $N(p) = p^{p-1}$, $N(\zeta) = 1$, and $N(\zeta - 1) = N(1 - \zeta) = p$, since $p - 1$ is even. Thus $N(\Phi_p'(\zeta)) = p^{p-2}$. Finally $n(n-1)/2 = (p-1)(p-2)/2$ has the parity of $(p-1)/2$, because $p - 2$ is odd.

For part 3, note that $\mathbb{Z}[\zeta] = \mathbb{Z}[\pi]$, and the discriminant $\delta$ of $1, \pi, \dots, \pi^{p-2}$ is the one of part 2. The proof of Theorem 1.1.5, applied to this basis, shows that $\delta \mathcal{O}_F \subset \mathbb{Z}[\pi]$. Thus the index of $\mathbb{Z}[\pi]$ in $\mathcal{O}_F$ is a power of $p$. Assume that the index is not 1. Then there is $x \in \mathcal{O}_F$ with $x \notin \mathbb{Z}[\pi]$ and $px \in \mathbb{Z}[\pi]$. Write $px = b_0 + b_1 \pi + \dots + b_{p-2} \pi^{p-2}$ with $b_j \in \mathbb{Z}$, not all divisible by $p$. Let $i$ be the least index with $p \nmid b_i$. Subtracting the terms with $j < i$, divided by $p$, we may assume that $b_j = 0$ for $j < i$. Then $b_i \pi^i + \dots + b_{p-2} \pi^{p-2} \in p\mathcal{O}_F = \pi^{p-1} \mathcal{O}_F$. Since $i < p - 1$, this gives $b_i \pi^i \in \pi^{i+1} \mathcal{O}_F$, so $b_i \in \pi \mathcal{O}_F \cap \mathbb{Z} = p \mathbb{Z}$. This is a contradiction. $\square$

For general $m$, one proves that $\mathcal{O}_F = \mathbb{Z}[\zeta_m]$ in two steps. The same argument as above treats $m = p^k$. Here $\Phi_{p^k}(1) = p$, the element $\pi = 1 - \zeta_{p^k}$ generates a prime of degree 1, and $p \mathcal{O} = (\pi)^{\varphi(p^k)}$. For $m = m_1 m_2$ with coprime $m_1, m_2$, the fields $\mathbb{Q}(\zeta_{m_1})$ and $\mathbb{Q}(\zeta_{m_2})$ have coprime discriminants, and the ring of integers of their compositum is the product of the two rings ([Neu99], Chapter I, Propositions 2.11 and 10.2). We use this result below.

**Theorem 1.5.5 (primes in cyclotomic fields).** Let $F = \mathbb{Q}(\zeta_m)$ with $m \not\equiv 2 \pmod 4$. Let $p$ be a prime, write $m = p^k m'$ with $p \nmid m'$, and let $f$ be the order of $p$ in $(\mathbb{Z}/m'\mathbb{Z})^\times$. Then
$$p \mathcal{O}_F = (\mathfrak{P}_1 \cdots \mathfrak{P}_g)^{\varphi(p^k)}$$
with distinct primes $\mathfrak{P}_i$ of residue degree $f$, and $g = \varphi(m')/f$. In particular $p$ is ramified in $F$ if and only if $p \mid m$. If $p \nmid m$, then $\mathrm{Frob}_p = \sigma_p$, and $p$ splits completely in $F$ if and only if $p \equiv 1 \pmod m$.

Lean: not stated yet

*Proof.* First let $p \nmid m$, so $m' = m$. We use $\mathcal{O}_F = \mathbb{Z}[\zeta]$ and Theorem 1.4.2. The polynomial $X^m - 1$ is separable modulo $p$, so $\Phi_m$ is separable modulo $p$, and $p$ is unramified. For $x = \sum_i a_i \zeta^i \in \mathbb{Z}[\zeta]$ we have
$$x^p \equiv \sum_i a_i^p \zeta^{ip} \equiv \sum_i a_i \zeta^{ip} = \sigma_p(x) \pmod{p \mathcal{O}_F},$$
by the binomial theorem and Fermat's little theorem. Thus $\sigma_p$ satisfies the defining property of $\mathrm{Frob}_\mathfrak{P}$ for each $\mathfrak{P} \mid p$. The Galois group is abelian, so $\mathrm{Frob}_p = \sigma_p$. By Proposition 1.4.8, the residue degree is the order of $\sigma_p$, which is the order $f$ of $p$ modulo $m$. Then $g = \varphi(m)/f$ by Theorem 1.4.4.

In general, let $F_1 = \mathbb{Q}(\zeta_{p^k})$ and $F_2 = \mathbb{Q}(\zeta_{m'})$, so that $F = F_1 F_2$. Let $\mathfrak{P}$ be a prime of $F$ above $p$. Ramification indices and residue degrees are multiplicative in towers. In $F_1$, the prime $p$ is totally ramified with index $\varphi(p^k)$. In $F_2$, it has residue degree $f$ and splits into $\varphi(m')/f$ primes. Thus $e(\mathfrak{P}/p)$ is divisible by $\varphi(p^k)$, $f(\mathfrak{P}/p)$ is divisible by $f$, and the number $g$ of primes of $F$ above $p$ is at least $\varphi(m')/f$. Since $efg = \varphi(m) = \varphi(p^k) \varphi(m')$, all three are equalities. The prime $p$ is ramified if and only if $\varphi(p^k) > 1$, that is, if and only if $k \ge 1$, since $p^k \ne 2$ by the assumption on $m$. $\square$

**Remark 1.5.6 (the first reciprocity law).** Theorem 1.5.5 says that the map $p \mapsto \mathrm{Frob}_p$ from the primes $p \nmid m$ to $\mathrm{Gal}(\mathbb{Q}(\zeta_m) / \mathbb{Q})$ factors through the reduction $p \mapsto p \bmod m$. The splitting of $p$ is thus determined by a congruence condition. Class field theory characterizes the abelian extensions by this property. The theorem of Kronecker and Weber states that every abelian extension of $\mathbb{Q}$ is contained in some $\mathbb{Q}(\zeta_m)$, see Volume 0, Theorem 2.1.8. Volume 3 proves the general reciprocity law.

### Quadratic reciprocity

Let $p$ be an odd prime and $p^* = (-1)^{(p-1)/2} p$, so that $p^* \equiv 1 \pmod 4$.

**Lemma 1.5.7 (the quadratic subfield).** The field $\mathbb{Q}(\zeta_p)$ contains $\mathbb{Q}(\sqrt{p^*})$, and this is its unique quadratic subfield.

Lean: not stated yet

*Proof.* The Galois group $(\mathbb{Z}/p\mathbb{Z})^\times$ is cyclic of even order $p - 1$. It has exactly one subgroup of index 2, so $\mathbb{Q}(\zeta_p)$ has exactly one quadratic subfield $K = \mathbb{Q}(\sqrt d)$ with $d$ squarefree. By Theorem 1.5.5 only $p$ ramifies in $\mathbb{Q}(\zeta_p)$. Thus only $p$ can ramify in $K$, and $p$ is ramified in $K$ by Corollary 1.3.6 and Theorem 1.4.3. By Proposition 1.5.1, $d_K = \pm p$. A fundamental discriminant that is odd is $1$ modulo $4$ by Example 1.1.8, so $d_K = p^*$, and $K = \mathbb{Q}(\sqrt{p^*})$. $\square$

**Theorem 1.5.8 (quadratic reciprocity).** Let $p$ and $\ell$ be distinct odd primes. Then
$$\left( \frac{\ell}{p} \right) \left( \frac{p}{\ell} \right) = (-1)^{\frac{p-1}{2} \cdot \frac{\ell-1}{2}}.$$

Lean: `legendreSym.quadratic_reciprocity`, from Mathlib

*Proof.* Let $K = \mathbb{Q}(\sqrt{p^*})$. The prime $\ell$ is unramified in $\mathbb{Q}(\zeta_p)$, and its Frobenius element there is $\sigma_\ell$ by Theorem 1.5.5. By Proposition 1.4.8, the Frobenius element of $\ell$ in $K$ is the restriction of $\sigma_\ell$ to $K$. This restriction is trivial if and only if $\sigma_\ell$ lies in the subgroup of index 2 of $(\mathbb{Z}/p\mathbb{Z})^\times$, which is the group of squares. Thus $\mathrm{Frob}_\ell|_K = (\ell/p)$. On the other hand, $\mathrm{Frob}_\ell|_K = (p^*/\ell)$ by Proposition 1.5.1. Thus $(\ell/p) = (p^*/\ell)$. Finally, Euler's criterion gives $(-1/\ell) = (-1)^{(\ell-1)/2}$, so $(p^*/\ell) = (-1)^{\frac{p-1}{2}\cdot\frac{\ell-1}{2}} (p/\ell)$. $\square$

The same method with $\mathbb{Q}(\zeta_8) \supset \mathbb{Q}(\sqrt 2)$ gives the second supplementary law $(2/p) = (-1)^{(p^2-1)/8}$ (Exercise 11 of Section 1.6). This proof of quadratic reciprocity is the model for the later reciprocity laws. A Frobenius element is computed in two ways: through the arithmetic of the larger field, and through the group of the abelian extension.
