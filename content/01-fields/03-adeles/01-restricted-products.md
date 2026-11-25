---
title: Restricted products
nodes: []
sources: [CF67]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Restricted products

The adeles and the ideles are restricted products. This section gives the definition and the topological facts that the later sections use. We follow [CF67], Chapter II, Section 13, and Chapter XV (Tate's thesis), Section 3.1.

### Definition

Let $V$ be a set of indices, and let $V_\infty \subset V$ be a finite subset. For each $v \in V$ let $G_v$ be a locally compact Hausdorff abelian group, and for each $v \notin V_\infty$ let $H_v \subset G_v$ be a compact open subgroup.

**Definition 3.1.1 (restricted product).** The *restricted product* of the $G_v$ with respect to the $H_v$ is the group
$$G = \prod_{v}{}' (G_v, H_v) = \{(x_v)_v \in \prod_v G_v : x_v \in H_v \text{ for almost all } v\}.$$
For each finite set $S \supset V_\infty$, let $G_S = \prod_{v \in S} G_v \times \prod_{v \notin S} H_v$, with the product topology. The topology of $G$ is the topology for which a set $U \subset G$ is open if and only if $U \cap G_S$ is open in $G_S$ for each $S$.

Lean: `RestrictedProduct`, from Mathlib

A basis of open sets of $G$ is given by the sets $\prod_{v \in S} U_v \times \prod_{v \notin S} H_v$, where $S \supset V_\infty$ is finite and $U_v \subset G_v$ is open. In each such set almost all factors are the compact groups $H_v$. This is the difference with the product topology, in which almost all factors of a basic open set are the whole groups $G_v$.

**Proposition 3.1.2 (the topology of a restricted product).** Each $G_S$ is an open subgroup of $G$, and it carries the product topology. The group $G$ is a locally compact Hausdorff topological group, and $G = \bigcup_S G_S$.

Lean: not stated yet

*Proof.* The set $G_S$ is a union of basic open sets, so it is open. For $S \subset S'$, the topology of $G_{S'}$ induces the product topology on $G_S$, because $H_v$ is open in $G_v$. Thus the topology of $G$ induces the product topology on each $G_S$. The group $G_S$ is locally compact, because a product of finitely many locally compact groups and of compact groups is locally compact by Tychonoff's theorem. Since $G_S$ is open in $G$, the group $G$ is locally compact. The group operations are continuous on each $G_S$, and each pair of elements of $G$ lies in some $G_S$, so they are continuous on $G$. Two distinct points lie in a common $G_S$, which is Hausdorff. $\square$

**Proposition 3.1.3 (compact subsets).** A subset of $G$ has compact closure if and only if it is contained in a set $\prod_v C_v$, where $C_v \subset G_v$ is compact for all $v$ and $C_v = H_v$ for almost all $v$.

Lean: not stated yet

*Proof.* A set $\prod_v C_v$ of this form is compact in some $G_S$ by Tychonoff's theorem, so it is compact in $G$. Conversely let $C \subset G$ be compact. The open sets $G_S$ cover $C$ and form an increasing family, so $C \subset G_S$ for one $S$. The projections $C_v$ of $C$ to $G_v$ are compact, and $C \subset \prod_{v \in S} C_v \times \prod_{v \notin S} H_v$. $\square$

The proposition shows that a sequence $x^{(n)}$ converges in $G$ if and only if it lies in some $G_S$ for $n$ large and converges there. For example, in the restricted product $\prod'(\mathbb{Q}_p, \mathbb{Z}_p)$ the sequence $x^{(n)}$ with $x^{(n)}_p = 1/p$ for the $n$-th prime $p$ and $x^{(n)}_\ell = 0$ for $\ell \ne p$ tends to 0 in the product topology, but it does not converge in the restricted product.

### Characters

Let $\hat G_v$ be the Pontryagin dual of $G_v$, the group of continuous homomorphisms $G_v \to S^1$, with the compact open topology. For $v \notin V_\infty$, let $H_v^\perp \subset \hat G_v$ be the subgroup of characters that are trivial on $H_v$. It is compact and open, because $H_v$ is open and compact.

**Proposition 3.1.4 (characters of a restricted product).** Let $\chi$ be a continuous character of $G$. Then the restriction $\chi_v$ of $\chi$ to $G_v$ is trivial on $H_v$ for almost all $v$, and $\chi(x) = \prod_v \chi_v(x_v)$, where almost all factors are 1. The map $\chi \mapsto (\chi_v)_v$ is an isomorphism of topological groups
$$\hat G \cong \prod_v{}' (\hat G_v, H_v^\perp).$$

Lean: not stated yet

*Proof sketch.* Let $N$ be a neighbourhood of 1 in $S^1$ that contains no nontrivial subgroup. The set $\chi^{-1}(N)$ contains a basic open set, so it contains $H_v$ for all $v$ outside a finite set $S$. Then $\chi(H_v)$ is a subgroup of $S^1$ contained in $N$, so it is trivial. For $x \in G$, write $x = x_S \cdot x^S$ with $x_S \in \prod_{v \in S} G_v$ and $x^S \in \prod_{v \notin S} H_v$. Then $\chi(x^S) = 1$ by the continuity of $\chi$ on the compact group $\prod_{v \notin S} H_v$, since $\chi$ is trivial on the dense subgroup of elements with almost all components 1. Thus $\chi(x) = \prod_{v \in S} \chi_v(x_v)$. Conversely each element of the restricted product of the duals defines a character in this way. For the topology see [CF67], Chapter XV, Lemma 3.2.1. $\square$

This proposition is the source of the factorization of Hecke characters and of automorphic representations into local components. If each $G_v$ is self-dual, with $H_v^\perp$ corresponding to $H_v$ for almost all $v$, then $G$ is self-dual. Tate's thesis, which is Chapter XV of [CF67], uses this for $G = \mathbb{A}_F$. Volume 3, Chapter 4, uses the local part of the thesis.
