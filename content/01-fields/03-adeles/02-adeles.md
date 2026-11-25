---
title: Adeles
nodes: []
sources: [CF67, Neu99]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Adeles

This section defines the adele ring of a number field and proves that the field is a discrete cocompact subring. We follow [CF67], Chapter II, Sections 14 and 15, and [Neu99], Chapter VI, Section 1.

### The adele ring

Let $F$ be a number field. For a finite place $v$, let $\mathcal{O}_v$ be the ring of integers of $F_v$. It is a compact open subring of $F_v$ by Proposition 2.3.3.

**Definition 3.2.1 (adeles).** The *adele ring* of $F$ is the restricted product
$$\mathbb{A}_F = \prod_v{}' (F_v, \mathcal{O}_v)$$
over all places $v$ of $F$, with respect to the subrings $\mathcal{O}_v$ at the finite places. The *finite adeles* are $\mathbb{A}_{F,f} = \prod'_{v \nmid \infty} (F_v, \mathcal{O}_v)$, and $\mathbb{A}_F = F_\infty \times \mathbb{A}_{F,f}$, where $F_\infty = \prod_{v \mid \infty} F_v$ is the Minkowski space of Section 1.3. We write $\hat{\mathcal{O}}_F = \prod_{v \nmid \infty} \mathcal{O}_v$.

Lean: `NumberField.AdeleRing` and `IsDedekindDomain.FiniteAdeleRing`, from Mathlib

By Proposition 3.1.2, $\mathbb{A}_F$ is a locally compact topological ring, and $F_\infty \times \hat{\mathcal{O}}_F$ is an open subring. Each $x \in F$ lies in $\mathcal{O}_v$ for almost all $v$, because $x$ has only finitely many primes in its denominator. Thus the diagonal map $F \to \mathbb{A}_F$, $x \mapsto (x)_v$, is an injective ring homomorphism. We identify $F$ with its image, the *principal adeles*.

The ring $\hat{\mathcal{O}}_F$ is the profinite completion of $\mathcal{O}_F$. Indeed, by Proposition 1.2.5,
$$\varprojlim_{\mathfrak{a}} \mathcal{O}_F / \mathfrak{a} = \varprojlim_{\mathfrak{a}} \prod_{\mathfrak{p}} \mathcal{O}_F / \mathfrak{p}^{v_\mathfrak{p}(\mathfrak{a})} = \prod_\mathfrak{p} \mathcal{O}_\mathfrak{p}.$$
For $F = \mathbb{Q}$ this is $\hat{\mathbb{Z}} = \prod_p \mathbb{Z}_p$.

### The rational adeles

**Proposition 3.2.2 (the adeles of $\mathbb{Q}$).** Every $a \in \mathbb{A}_\mathbb{Q}$ can be written uniquely as $a = x + y$ with $x \in \mathbb{Q}$ and $y \in [0, 1) \times \hat{\mathbb{Z}}$. In particular $\mathbb{Q} \cap (\mathbb{R} \times \hat{\mathbb{Z}}) = \mathbb{Z}$, the subring $\mathbb{Q}$ is discrete in $\mathbb{A}_\mathbb{Q}$, and
$$\mathbb{A}_\mathbb{Q} / \mathbb{Q} \cong (\mathbb{R} \times \hat{\mathbb{Z}}) / \mathbb{Z}$$
is compact.

Lean: not stated yet

*Proof.* Let $a = (a_\infty, (a_p)_p)$, and let $S$ be the finite set of primes $p$ with $a_p \notin \mathbb{Z}_p$. For $p \in S$, the expansion of Example 2.2.2 gives $r_p \in \mathbb{Z}[1/p]$ with $a_p - r_p \in \mathbb{Z}_p$: take for $r_p$ the sum of the terms with negative exponents. For a prime $\ell \ne p$, the number $r_p$ lies in $\mathbb{Z}_\ell$. Let $r = \sum_{p \in S} r_p \in \mathbb{Q}$. Then $a_p - r \in \mathbb{Z}_p$ for all $p$. Let $m$ be the integer part of $a_\infty - r$, and put $x = r + m$. Then $y = a - x$ has $y_\infty \in [0, 1)$ and $y_p \in \mathbb{Z}_p$ for all $p$. A rational number in $\mathbb{Z}_p$ for all $p$ is an integer, so $\mathbb{Q} \cap (\mathbb{R} \times \hat{\mathbb{Z}}) = \mathbb{Z}$, and an integer in $[0, 1)$ is 0. This gives uniqueness. The open set $(-1, 1) \times \hat{\mathbb{Z}}$ meets $\mathbb{Q}$ only in $0$, so $\mathbb{Q}$ is discrete. The quotient is the image of the compact set $[0, 1] \times \hat{\mathbb{Z}}$. $\square$

The compact group $\mathbb{A}_\mathbb{Q} / \mathbb{Q}$ is the *solenoid*. It is connected, and it is the projective limit of the circles $\mathbb{R} / n\mathbb{Z}$.

### Discreteness and compactness

**Proposition 3.2.3 (adeles and base change).** Let $L / F$ be a finite extension of degree $n$. Then the natural map $\mathbb{A}_F \otimes_F L \to \mathbb{A}_L$ is an isomorphism of topological rings, where $\mathbb{A}_F \otimes_F L \cong \mathbb{A}_F^n$ through a basis of $L$ over $F$. It maps $F \otimes_F L$ onto $L$.

Lean: not stated yet

*Proof.* Let $\omega_1, \dots, \omega_n$ be a basis of $L$ over $F$ in $\mathcal{O}_L$. By Theorem 2.5.1, $F_v \otimes_F L \cong \prod_{w \mid v} L_w$ for each $v$. For almost all finite $v$, the element $d = d(\omega_1, \dots, \omega_n)$ is a unit at $v$. For such $v$, let $M = \mathcal{O}_v \omega_1 + \dots + \mathcal{O}_v \omega_n$, and let $M' = \prod_{w \mid v} \mathcal{O}_w$, the integral closure of $\mathcal{O}_v$ in $F_v \otimes_F L$. Then $M \subset M'$, and the discriminants satisfy $d \mathcal{O}_v = [M' : M]^2 \, \mathfrak{d}(M')$, where $[M' : M]$ is the index ideal. Since $d$ is a unit at $v$, the index is trivial, and $M = M'$. Thus the isomorphisms at all $v$ respect the restricted products, and they define the isomorphism of topological rings. $\square$

**Theorem 3.2.4 (discreteness and cocompactness).** The subring $F$ is discrete in $\mathbb{A}_F$, and the quotient $\mathbb{A}_F / F$ is compact.

Lean: not stated yet

*Proof.* By Proposition 3.2.3 with $\mathbb{Q}$ in place of $F$, and $F$ in place of $L$, there is an isomorphism $\mathbb{A}_\mathbb{Q}^n \cong \mathbb{A}_F$ that maps $\mathbb{Q}^n$ onto $F$. Thus $\mathbb{A}_F / F \cong (\mathbb{A}_\mathbb{Q} / \mathbb{Q})^n$, and Proposition 3.2.2 gives both claims. $\square$

The next theorem is a finer form of Theorem 3.2.4. It describes a fundamental domain.

**Theorem 3.2.5 (a fundamental domain).** We have
$$\mathbb{A}_F = F + (F_\infty \times \hat{\mathcal{O}}_F), \qquad F \cap (F_\infty \times \hat{\mathcal{O}}_F) = \mathcal{O}_F.$$
Thus $\mathbb{A}_F / F \cong (F_\infty \times \hat{\mathcal{O}}_F) / \mathcal{O}_F$. If $P \subset F_\infty$ is a fundamental domain for the lattice $\mathcal{O}_F$, then $P \times \hat{\mathcal{O}}_F$ is a fundamental domain for $F$ in $\mathbb{A}_F$.

Lean: not stated yet

*Proof.* The second equality holds because an element of $F$ that lies in $\mathcal{O}_v$ for all finite $v$ lies in $\mathcal{O}_F$. For the first, let $a \in \mathbb{A}_F$. There is a positive integer $d$ with $d a_v \in \mathcal{O}_v$ for all finite $v$. Let $T$ be the finite set of finite places $v$ with $v(d) > 0$. By Proposition 1.2.5,
$$\mathcal{O}_F / d\mathcal{O}_F \cong \prod_{v \in T} \mathcal{O}_v / d \mathcal{O}_v,$$
so there is $y \in \mathcal{O}_F$ with $y \equiv d a_v \pmod{d \mathcal{O}_v}$ for all $v \in T$. Put $x = y / d \in F$. For $v \in T$, $a_v - x = (d a_v - y)/d \in \mathcal{O}_v$. For finite $v \notin T$, $d$ is a unit in $\mathcal{O}_v$, so $a_v$ and $x$ are in $\mathcal{O}_v$. Thus $a - x \in F_\infty \times \hat{\mathcal{O}}_F$. The last claim follows from the first two: each class of $\mathbb{A}_F / F$ meets $F_\infty \times \hat{\mathcal{O}}_F$ in exactly one class modulo $\mathcal{O}_F$, and $\mathcal{O}_F$ acts only on the first factor. $\square$

The theorem gives a second proof of Theorem 3.2.4. The set $(F_\infty \times \hat{\mathcal{O}}_F) / \mathcal{O}_F$ fibres over the torus $F_\infty / \mathcal{O}_F$ with the compact fibre $\hat{\mathcal{O}}_F$, so it is compact. And the open neighbourhood $U \times \hat{\mathcal{O}}_F$ of 0, where $U$ is a small ball in $F_\infty$, meets $F$ only in the elements of $\mathcal{O}_F$ that lie in $U$, that is, only in 0.

### Approximation

The approximation theorem of Section 2.1 says that $F$ is dense in $\prod_{v \in S} F_v$ for each finite set $S$ of places. Theorem 3.2.4 says that $F$ is not dense in $\mathbb{A}_F$. Section 3.5 proves the theorem of strong approximation, which lies between the two: $F$ is dense in the adeles with one component omitted.
