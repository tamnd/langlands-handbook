---
title: Ideles and idele classes
nodes: []
sources: [CF67, Neu99]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Ideles and idele classes

This section defines the idele group and the idele class group, and it relates them to the class group and the unit group of Chapter 1. We follow [CF67], Chapter II, Sections 16 and 17, and [Neu99], Chapter VI, Section 1.

### The idele group

**Definition 3.4.1 (ideles).** The *idele group* of $F$ is the restricted product
$$J_F = \mathbb{A}_F^\times = \prod_v{}' (F_v^\times, \mathcal{O}_v^\times)$$
with respect to the compact open subgroups $\mathcal{O}_v^\times$ at the finite places. As a group, it is the group of units of the ring $\mathbb{A}_F$.

Lean: `NumberField.IdeleGroup`, from Mathlib

An adele $a$ is a unit of $\mathbb{A}_F$ if and only if $a_v \ne 0$ for all $v$ and $a_v \in \mathcal{O}_v^\times$ for almost all $v$. Thus the two descriptions of $J_F$ give the same group. The topology needs care. The topology of the restricted product is not the topology of a subspace of $\mathbb{A}_F$.

**Proposition 3.4.2 (the topology of the ideles).** The topology of the restricted product on $J_F$ is the topology induced by the injective map
$$J_F \to \mathbb{A}_F \times \mathbb{A}_F, \qquad x \mapsto (x, x^{-1}).$$
It is finer than the topology of a subspace of $\mathbb{A}_F$, and the two topologies are different. With it, $J_F$ is a locally compact Hausdorff topological group.

Lean: `Units.embedProduct`, from Mathlib, which induces the topology on a group of units

*Proof.* A basic open set of the restricted product is $\prod_{v \in S} U_v \times \prod_{v \notin S} \mathcal{O}_v^\times$ with $U_v \subset F_v^\times$ open. Its image is the intersection of $J_F$ with the open set $\prod_{v \in S} U_v \times \prod_{v \notin S} \mathcal{O}_v$ of $\mathbb{A}_F$ and with the preimage of $\prod_{v \in S} U_v^{-1} \times \prod_{v \notin S} \mathcal{O}_v$ under inversion. Conversely, a basic open set of $\mathbb{A}_F \times \mathbb{A}_F$ meets the image of $J_F$ in a union of such sets, because $x_v \in \mathcal{O}_v$ and $x_v^{-1} \in \mathcal{O}_v$ mean $x_v \in \mathcal{O}_v^\times$. Proposition 3.1.2 gives the last claim.

To see that the subspace topology is different, let $p_n$ be the $n$-th prime number, and let $x^{(n)} \in J_\mathbb{Q}$ have the component $p_n$ at $p_n$ and the component 1 elsewhere. In $\mathbb{A}_\mathbb{Q}$, the sequence $x^{(n)}$ tends to 1, because every basic neighbourhood of 1 restricts only finitely many components to be close to 1, and requires only $x_p \in \mathbb{Z}_p$ at the others. In $J_\mathbb{Q}$ it does not converge to 1, because $x^{(n)}_{p_n} \notin \mathbb{Z}_{p_n}^\times$. $\square$

**Definition 3.4.3 (the idele norm).** The *norm* of an idele $x$ is
$$|x|_\mathbb{A} = \prod_v |x_v|_v.$$
Almost all factors are 1, so the product is finite. The map $|\cdot|_\mathbb{A} : J_F \to \mathbb{R}_{>0}$ is a continuous homomorphism. Its kernel is the group $J_F^1$ of *norm one ideles*.

Lean: `NumberField.AdeleRing.norm_apply_of_isUnit`, from Mathlib

By Theorem 2.2.10, the diagonal embedding $F^\times \to J_F$ has its image in $J_F^1$.

**Proposition 3.4.4 (the principal ideles).** The subgroup $F^\times$ is discrete in $J_F$, and closed.

Lean: not stated yet

*Proof.* By Theorem 3.2.4, there is a neighbourhood $U$ of 0 in $\mathbb{A}_F$ with $U \cap F = \{0\}$. Then $1 + U$ is a neighbourhood of 1 in $\mathbb{A}_F$, and its preimage in $J_F$ is a neighbourhood of 1 in $J_F$, by Proposition 3.4.2. It meets $F^\times$ only in 1. A discrete subgroup of a Hausdorff topological group is closed. $\square$

**Definition 3.4.5 (the idele class group).** The *idele class group* of $F$ is $C_F = J_F / F^\times$, with the quotient topology. The *norm one idele classes* are $C_F^1 = J_F^1 / F^\times$.

Lean: `NumberField.IdeleClassGroup`, from Mathlib

The idele class group is a locally compact Hausdorff group, because $F^\times$ is closed. It is the central object of global class field theory: Volume 3 constructs a surjective homomorphism $C_F \to \mathrm{Gal}(F^{ab} / F)$ with kernel the connected component of 1.

**Proposition 3.4.6 (splitting off the norm).** The norm $|\cdot|_\mathbb{A}$ induces a continuous surjective homomorphism $C_F \to \mathbb{R}_{>0}$ with kernel $C_F^1$, and
$$C_F \cong C_F^1 \times \mathbb{R}_{>0}$$
as topological groups.

Lean: not stated yet

*Proof.* Let $n = [F : \mathbb{Q}]$. Define $s : \mathbb{R}_{>0} \to J_F$ by $s(t)_v = t^{1/n}$ for $v \mid \infty$ and $s(t)_v = 1$ for $v \nmid \infty$. Then
$$|s(t)|_\mathbb{A} = \prod_{v \text{ real}} t^{1/n} \prod_{v \text{ complex}} t^{2/n} = t^{(r_1 + 2r_2)/n} = t,$$
so $s$ is a continuous section of the norm. Thus $J_F \cong J_F^1 \times \mathbb{R}_{>0}$. Since $F^\times \subset J_F^1$, this gives $C_F \cong C_F^1 \times \mathbb{R}_{>0}$. $\square$

### Ideles and ideals

Let $I_F$ be the group of fractional ideals of $F$ and $P_F$ the subgroup of principal ideals, so that $\mathrm{Cl}_F = I_F / P_F$ as in Definition 1.2.6. Define
$$\iota : J_F \to I_F, \qquad \iota(x) = \prod_{v \nmid \infty} \mathfrak{p}_v^{v(x_v)},$$
where $\mathfrak{p}_v$ is the prime of $v$ and $v(x_v)$ is the normalized valuation. The product is finite, because $v(x_v) = 0$ for almost all $v$. Let
$$U_F = \prod_{v \mid \infty} F_v^\times \times \prod_{v \nmid \infty} \mathcal{O}_v^\times,$$
an open subgroup of $J_F$.

**Theorem 3.4.7 (the class group as a quotient of the ideles).** The map $\iota$ is a surjective homomorphism with kernel $U_F$, and it maps $F^\times$ onto $P_F$. Thus
$$J_F / F^\times U_F \cong \mathrm{Cl}_F,$$
and there is an exact sequence
$$1 \to \mathcal{O}_F^\times \to U_F \to C_F \to \mathrm{Cl}_F \to 1.$$

Lean: not stated yet

*Proof.* The map is a homomorphism. It is surjective, because the idele with component $\varpi_v$ at $v$ and $1$ elsewhere maps to $\mathfrak{p}_v$. Its kernel is the set of ideles with $v(x_v) = 0$ at all finite $v$, which is $U_F$. For $x \in F^\times$, $\iota(x) = x\mathcal{O}_F$ by the definition of $v_\mathfrak{p}$ in Example 2.1.2. Thus $\iota$ induces $J_F / F^\times U_F \cong I_F / P_F$. In the sequence, the map $U_F \to C_F$ is the composite of the inclusion and the projection. Its kernel is $U_F \cap F^\times$, the set of $x \in F^\times$ with $v(x) = 0$ for all finite $v$, which is $\mathcal{O}_F^\times$. Its image is $F^\times U_F / F^\times$, and the cokernel $J_F / F^\times U_F$ is $\mathrm{Cl}_F$. $\square$

The exact sequence shows that the idele class group contains both invariants of Chapter 1: the class group is a quotient of $C_F$, and the unit group appears through the subgroup $U_F / \mathcal{O}_F^\times$. More generally, for a finite set $S$ of places containing the infinite ones, the same proof gives
$$1 \to \mathcal{O}_{F,S}^\times \to \prod_{v \in S} F_v^\times \times \prod_{v \notin S} \mathcal{O}_v^\times \to C_F \to \mathrm{Cl}_{F,S} \to 1,$$
where $\mathcal{O}_{F,S}$ is the ring of $S$-integers and $\mathrm{Cl}_{F,S}$ its class group. Replacing $\mathcal{O}_v^\times$ by the subgroups $U_v^{(i)}$ at finitely many places gives the ray class groups, which Volume 3 uses for the classical form of class field theory.

**Example 3.4.8 (the ideles of $\mathbb{Q}$).** For $F = \mathbb{Q}$ the class group is trivial, and $\mathcal{O}_\mathbb{Q}^\times = \{\pm 1\}$. Thus
$$J_\mathbb{Q} = \mathbb{Q}^\times \cdot (\mathbb{R}_{>0} \times \hat{\mathbb{Z}}^\times), \qquad \mathbb{Q}^\times \cap (\mathbb{R}_{>0} \times \hat{\mathbb{Z}}^\times) = \{1\},$$
and $C_\mathbb{Q} \cong \mathbb{R}_{>0} \times \hat{\mathbb{Z}}^\times$. The norm one part is $C_\mathbb{Q}^1 \cong \hat{\mathbb{Z}}^\times = \varprojlim (\mathbb{Z}/m\mathbb{Z})^\times$, which is the Galois group of $\mathbb{Q}(\zeta_m)$ for all $m$ together, by Theorem 1.5.3. This is the reciprocity law of $\mathbb{Q}$ in adelic form.
