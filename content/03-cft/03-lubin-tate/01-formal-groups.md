---
title: Formal groups
nodes: []
sources: [Ser67, Mil20]
status: checked
drafted_by: writer
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## Formal groups

A formal group is a group law given by a power series. It is the analogue of a Lie group in which the analytic functions are replaced by formal power series. Let $A$ be a commutative ring. In this section, "modulo degree $r$" means modulo the ideal of power series whose terms all have total degree at least $r$.

**Definition 3.1.1 (formal group law).** A *commutative formal group law* of dimension 1 over $A$ is a power series $F(X, Y) \in A[[X, Y]]$ with the following three properties.
1. $F(X, Y) \equiv X + Y$ modulo degree 2.
2. $F(X, F(Y, Z)) = F(F(X, Y), Z)$.
3. $F(X, Y) = F(Y, X)$.

Lean: not stated yet

The composites in property 2 make sense, because $F$ has no constant term. From the axioms one can show that $F(X, 0) = X$, and that there is a unique $i(X) \in X A[[X]]$ with $F(X, i(X)) = 0$. These are Exercises 2 and 1. Thus $F$ behaves like the addition of a group.

**Example 3.1.2.** The *additive formal group* is $\mathbb{G}_a(X, Y) = X + Y$. The *multiplicative formal group* is $\mathbb{G}_m(X, Y) = X + Y + XY$. The second one comes from the multiplication of the group of units: $(1 + X)(1 + Y) = 1 + \mathbb{G}_m(X, Y)$.

**Definition 3.1.3 (homomorphisms and formal modules).** Let $F$ and $G$ be formal group laws over $A$. A *homomorphism* $F \to G$ is a power series $h \in X A[[X]]$ with $h(F(X, Y)) = G(h(X), h(Y))$. It is an isomorphism if it has an inverse for composition that is also a homomorphism. The endomorphisms of $F$ form a ring $\mathrm{End}_A(F)$, with the sum $F(h_1(X), h_2(X))$ and the product $h_1 \circ h_2$. Let $\mathcal{O}$ be a subring of $A$. A *formal $\mathcal{O}$-module* is a formal group law $F$ with a ring homomorphism $\mathcal{O} \to \mathrm{End}_A(F)$, $a \mapsto [a]_F$, such that $[a]_F(X) \equiv aX$ modulo degree 2.

A power series $h \in XA[[X]]$ has an inverse for composition if and only if its coefficient of $X$ is a unit of $A$. In that case the inverse of a homomorphism is again a homomorphism.

From now on $A = \mathcal{O}_K$, or $A$ is the ring of integers of a complete subfield of the completion of $\bar K$. Let $F$ be a formal group law over $\mathcal{O}_K$. Let $L$ be a finite extension of $K$ in $\bar K$. For $x, y \in \mathfrak{m}_L$ the series $F(x, y)$ converges in $\mathcal{O}_L$, because its terms of degree $r$ have absolute value at most $\max(|x|, |y|)^r$. Its value is in $\mathfrak{m}_L$, because $F$ has no constant term.

**Proposition 3.1.4 (points of a formal group).** Let $F$ be a formal $\mathcal{O}_K$-module. The set $\bar{\mathfrak{m}}$, with the operation $x +_F y = F(x, y)$ and the action $a \cdot x = [a]_F(x)$, is an $\mathcal{O}_K$-module. The group $G_K$ acts on it by $\mathcal{O}_K$-linear automorphisms.

Lean: not stated yet

*Proof.* Any two elements of $\bar{\mathfrak{m}}$ lie in $\mathfrak{m}_L$ for some finite extension $L$. The identities of power series in Definition 3.1.1 and Definition 3.1.3 give identities of their values, because evaluation at elements of $\mathfrak{m}_L$ is a continuous ring homomorphism $\mathcal{O}_L[[X, Y]] \to \mathcal{O}_L$. The neutral element is 0 and the inverse is $i(x)$. For $\sigma \in G_K$ one has $\sigma(F(x, y)) = F(\sigma(x), \sigma(y))$ and $\sigma([a]_F(x)) = [a]_F(\sigma(x))$, because $\sigma$ is continuous and fixes the coefficients, which lie in $\mathcal{O}_K$. $\square$

The text writes $F(\bar{\mathfrak{m}})$ for this module. For example, $\mathbb{G}_m(\bar{\mathfrak{m}})$ is isomorphic to the group of principal units of $\bar K$ by $x \mapsto 1 + x$. Its torsion is the set of $\zeta - 1$, where $\zeta$ is a root of unity of $p$-power order. The next section constructs formal groups whose torsion plays the same role for an arbitrary local field.
