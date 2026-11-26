---
title: The root space decomposition
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## The root space decomposition

This section decomposes a semisimple Lie algebra $\mathfrak{g}$ under a maximal toral subalgebra $\mathfrak{h}$. The nonzero weights of $\mathfrak{h}$ on $\mathfrak{g}$ are the roots. Each root space has dimension 1, each root $\alpha$ gives a copy of $\mathfrak{sl}_2$ in $\mathfrak{g}$, and the representation theory of Section 2.3 applied to these copies shows that the roots form a root system in a real Euclidean space. The example to keep in mind is $\mathfrak{sl}_n$ with the diagonal matrices of trace 0. We follow [Hum72], Section 8.

In this section $F$ is algebraically closed of characteristic 0, and $\mathfrak{g} \neq 0$ is a semisimple Lie algebra over $F$ with Killing form $\kappa$.

### Toral subalgebras

**Definition 2.4.1 (toral subalgebra).** A subalgebra $\mathfrak{t}$ of $\mathfrak{g}$ is *toral* if all its elements are semisimple, that is, if $\mathrm{ad}\, x$ is diagonalizable for each $x \in \mathfrak{t}$.

Lean: not stated yet; Mathlib works with Cartan subalgebras instead, see Remark 2.4.8

**Lemma 2.4.2.** A toral subalgebra is abelian. The Lie algebra $\mathfrak{g}$ has nonzero toral subalgebras.

Lean: not stated yet

*Proof.* Let $\mathfrak{t}$ be toral and $x \in \mathfrak{t}$. Since $\mathrm{ad}_\mathfrak{t}\, x$ is diagonalizable, it suffices to show that it has no nonzero eigenvalue. Assume that $[x, y] = a y$ with $y \in \mathfrak{t}$, $y \neq 0$ and $a \neq 0$. Then $\mathrm{ad}_\mathfrak{t}\, y (x) = -a y$ is an eigenvector of $\mathrm{ad}_\mathfrak{t}\, y$ for the eigenvalue $0$. On the other hand, write $x = \sum_i v_i$ with $v_i$ eigenvectors of the diagonalizable map $\mathrm{ad}_\mathfrak{t}\, y$, for distinct eigenvalues $\lambda_i$. Then $\mathrm{ad}_\mathfrak{t}\, y(x) = \sum_i \lambda_i v_i$ is a sum of eigenvectors for nonzero eigenvalues. It is nonzero and lies in the eigenspace for $0$, which is a contradiction.

If all elements of $\mathfrak{g}$ were nilpotent, then $\mathfrak{g}$ would be nilpotent by Engel's theorem (Corollary 2.2.7), hence solvable, which is impossible. So some $x \in \mathfrak{g}$ has $x_s \neq 0$ in Theorem 2.2.21, and $F x_s$ is a nonzero toral subalgebra. $\square$

A toral subalgebra of maximal dimension is maximal for inclusion. We fix a *maximal toral subalgebra* $\mathfrak{h}$ of $\mathfrak{g}$, that is, one that is not properly contained in a toral subalgebra. Its dimension $\ell = \dim \mathfrak{h}$ is the *rank* of $\mathfrak{g}$. Theorem 2.4.7 below shows that it does not depend on the choice of $\mathfrak{h}$.

### The root space decomposition

By Lemma 2.4.2, $\mathrm{ad}\, \mathfrak{h}$ is a commuting family of diagonalizable endomorphisms of $\mathfrak{g}$. So it is simultaneously diagonalizable, and $\mathfrak{g}$ is the direct sum of the subspaces
$$\mathfrak{g}_\alpha = \{x \in \mathfrak{g} : [h, x] = \alpha(h) x \text{ for all } h \in \mathfrak{h}\}, \qquad \alpha \in \mathfrak{h}^*.$$

**Definition 2.4.3 (roots).** A *root* of $\mathfrak{g}$ with respect to $\mathfrak{h}$ is a nonzero $\alpha \in \mathfrak{h}^*$ with $\mathfrak{g}_\alpha \neq 0$. We write $\Phi$ for the set of roots, and call $\mathfrak{g}_\alpha$ the *root space* of $\alpha$. The decomposition
$$\mathfrak{g} = \mathfrak{g}_0 \oplus \bigoplus_{\alpha \in \Phi} \mathfrak{g}_\alpha$$
is the *root space decomposition*. The space $\mathfrak{g}_0 = C_\mathfrak{g}(\mathfrak{h})$ is the centralizer of $\mathfrak{h}$, and it contains $\mathfrak{h}$.

Lean: `LieAlgebra.rootSpace` and `LieModule.Weight`, from Mathlib

The set $\Phi$ is finite, because $\mathfrak{g}$ is finite dimensional.

**Proposition 2.4.4.** Let $\alpha, \beta \in \mathfrak{h}^*$.
1. $[\mathfrak{g}_\alpha, \mathfrak{g}_\beta] \subset \mathfrak{g}_{\alpha + \beta}$.
2. If $\alpha \neq 0$ and $x \in \mathfrak{g}_\alpha$, then $\mathrm{ad}\, x$ is nilpotent.
3. If $\alpha + \beta \neq 0$, then $\kappa(\mathfrak{g}_\alpha, \mathfrak{g}_\beta) = 0$.
4. The restriction of $\kappa$ to $\mathfrak{g}_0 = C_\mathfrak{g}(\mathfrak{h})$ is nondegenerate.

Lean: `LieAlgebra.killingForm_apply_eq_zero_of_mem_rootSpace_of_add_ne_zero`, from Mathlib, is part 3

*Proof.* For $x \in \mathfrak{g}_\alpha$, $y \in \mathfrak{g}_\beta$ and $h \in \mathfrak{h}$, the Jacobi identity gives $[h, [x, y]] = [[h, x], y] + [x, [h, y]] = (\alpha + \beta)(h) [x, y]$. This is part 1. By part 1, $\mathrm{ad}\, x$ maps $\mathfrak{g}_\beta$ into $\mathfrak{g}_{\beta + \alpha}$, so $(\mathrm{ad}\, x)^n$ maps $\mathfrak{g}_\beta$ into $\mathfrak{g}_{\beta + n\alpha}$. Only finitely many of these spaces are nonzero, which gives part 2. For part 3, choose $h \in \mathfrak{h}$ with $(\alpha + \beta)(h) \neq 0$. For $x \in \mathfrak{g}_\alpha$ and $y \in \mathfrak{g}_\beta$, invariance gives $\alpha(h) \kappa(x, y) = \kappa([h, x], y) = -\kappa(x, [h, y]) = -\beta(h) \kappa(x, y)$. So $\kappa(x, y) = 0$. Part 4 follows from part 3: $\mathfrak{g}_0$ is orthogonal to all $\mathfrak{g}_\alpha$ with $\alpha \neq 0$, and $\kappa$ is nondegenerate on $\mathfrak{g}$. $\square$

**Theorem 2.4.5 (the centralizer of $\mathfrak{h}$).** $C_\mathfrak{g}(\mathfrak{h}) = \mathfrak{h}$.

Lean: not stated yet in this form

*Proof.* Write $C = C_\mathfrak{g}(\mathfrak{h})$. We follow the seven steps of [Hum72], Section 8.2.
1. If $x \in C$, then $x_s, x_n \in C$. Indeed, $\mathrm{ad}\, x_s$ and $\mathrm{ad}\, x_n$ are polynomials in $\mathrm{ad}\, x$, so they map $\mathfrak{h}$ to $0$ when $\mathrm{ad}\, x$ does.
2. Every semisimple $x \in C$ lies in $\mathfrak{h}$. Indeed, $x$ commutes with $\mathfrak{h}$, and the sum of commuting diagonalizable maps is diagonalizable. So $\mathfrak{h} + F x$ is toral, and it equals $\mathfrak{h}$ by maximality.
3. The restriction of $\kappa$ to $\mathfrak{h}$ is nondegenerate. Let $h \in \mathfrak{h}$ with $\kappa(h, \mathfrak{h}) = 0$. For a nilpotent $x \in C$, the maps $\mathrm{ad}\, x$ and $\mathrm{ad}\, h$ commute, so $\mathrm{ad}\, x \circ \mathrm{ad}\, h$ is nilpotent and $\kappa(x, h) = 0$. By steps 1 and 2, each $x \in C$ is the sum of an element of $\mathfrak{h}$ and a nilpotent element of $C$. So $\kappa(h, C) = 0$, and $h = 0$ by part 4 of Proposition 2.4.4.
4. $C$ is nilpotent. For $x \in C$, write $x = x_s + x_n$. Then $x_s \in \mathfrak{h}$ by step 2, so $\mathrm{ad}_C\, x_s = 0$, and $\mathrm{ad}_C\, x_n$ is nilpotent. These maps commute, so $\mathrm{ad}_C\, x$ is nilpotent. Engel's theorem applies.
5. $\mathfrak{h} \cap [C, C] = 0$. Indeed, $\kappa(\mathfrak{h}, [C, C]) = \kappa([\mathfrak{h}, C], C) = 0$, and step 3 applies.
6. $C$ is abelian. Otherwise $[C, C] \neq 0$. A nonzero ideal of a nilpotent Lie algebra meets its center nontrivially, by Theorem 2.2.6 applied to the adjoint action on the ideal. So there is $z \neq 0$ in $Z(C) \cap [C, C]$. By steps 2 and 5, $z$ is not semisimple, so $z_n \neq 0$. The element $z_n$ lies in $C$ by step 1, and it commutes with all of $C$: if $x \in C$, then $\mathrm{ad}\, x$ commutes with $\mathrm{ad}\, z$, hence with the polynomial $\mathrm{ad}\, z_n$ in $\mathrm{ad}\, z$, so $\mathrm{ad}[x, z_n] = 0$ and $[x, z_n] = 0$. Then $\mathrm{ad}\, x \circ \mathrm{ad}\, z_n$ is nilpotent for $x \in C$, and $\kappa(C, z_n) = 0$. This contradicts part 4 of Proposition 2.4.4.
7. $C = \mathfrak{h}$. Otherwise, by steps 1 and 2, $C$ contains a nilpotent element $x \neq 0$. For $y \in C$ the maps $\mathrm{ad}\, x$ and $\mathrm{ad}\, y$ commute, because $C$ is abelian, so $\kappa(x, y) = 0$. Again this contradicts part 4 of Proposition 2.4.4. $\square$

By step 3, the restriction of $\kappa$ to $\mathfrak{h}$ is nondegenerate. So for each $\varphi \in \mathfrak{h}^*$ there is a unique $t_\varphi \in \mathfrak{h}$ with
$$\kappa(t_\varphi, h) = \varphi(h) \quad \text{for all } h \in \mathfrak{h}.$$
The map $\varphi \mapsto t_\varphi$ is a linear isomorphism $\mathfrak{h}^* \to \mathfrak{h}$.

### Cartan subalgebras

**Definition 2.4.6 (Cartan subalgebra).** A *Cartan subalgebra* of a Lie algebra $\mathfrak{l}$ is a nilpotent subalgebra $\mathfrak{c}$ that is its own normalizer: if $[x, \mathfrak{c}] \subset \mathfrak{c}$, then $x \in \mathfrak{c}$.

Lean: `LieSubalgebra.IsCartanSubalgebra`, from Mathlib

**Theorem 2.4.7 (Cartan subalgebras of a semisimple Lie algebra).** Let $\mathfrak{g}$ be semisimple.
1. The Cartan subalgebras of $\mathfrak{g}$ are exactly the maximal toral subalgebras.
2. Any two Cartan subalgebras are conjugate under the group $\mathrm{Int}(\mathfrak{g})$ of automorphisms of $\mathfrak{g}$ generated by the $\exp(\mathrm{ad}\, x)$ with $x$ nilpotent.

Lean: `LieAlgebra.exists_isCartanSubalgebra_engel`, from Mathlib, gives the existence of a Cartan subalgebra over an infinite field; the conjugacy is not in Mathlib

*Proof sketch.* A maximal toral subalgebra $\mathfrak{h}$ is abelian, hence nilpotent. If $[x, \mathfrak{h}] \subset \mathfrak{h}$, write $x = x_0 + \sum_\alpha x_\alpha$ in the root space decomposition. Then $[h, x] = \sum_\alpha \alpha(h) x_\alpha \in \mathfrak{h}$ for all $h \in \mathfrak{h}$, so all $x_\alpha = 0$, and $x \in \mathfrak{g}_0 = \mathfrak{h}$ by Theorem 2.4.5. So $\mathfrak{h}$ is a Cartan subalgebra. The converse and part 2 are harder. See [Hum72], Sections 15 and 16. Part 2 uses the conjugacy of the Borel subalgebras, that is, of the maximal solvable subalgebras. $\square$

By part 2, the rank $\ell$ does not depend on the choice of $\mathfrak{h}$, and neither does the root system that we construct below, up to isomorphism.

**Remark 2.4.8 (Mathlib).** Mathlib works with a Cartan subalgebra $H$ of a Lie algebra $L$ with nondegenerate Killing form over a field of characteristic 0, under the assumption that $H$ splits $L$ (the class `LieModule.IsTriangularizable`). Over an algebraically closed field this assumption always holds. Mathlib proves that $H$ is abelian (`LieAlgebra.IsKilling.instIsLieAbelianOfIsCartanSubalgebra`) and that its elements are semisimple (`LieAlgebra.IsKilling.isSemisimple_ad_of_mem_isCartanSubalgebra`). So by part 1 of Theorem 2.4.7, it works with the same objects as this section.

### Orthogonality properties

**Proposition 2.4.9 (orthogonality).** Let $\alpha \in \Phi$.
1. $\Phi$ spans $\mathfrak{h}^*$.
2. $-\alpha \in \Phi$.
3. If $x \in \mathfrak{g}_\alpha$ and $y \in \mathfrak{g}_{-\alpha}$, then $[x, y] = \kappa(x, y)\, t_\alpha$.
4. $\alpha(t_\alpha) = \kappa(t_\alpha, t_\alpha) \neq 0$.
5. For each $x_\alpha \in \mathfrak{g}_\alpha$, $x_\alpha \neq 0$, there is $y_\alpha \in \mathfrak{g}_{-\alpha}$ such that $(x_\alpha, y_\alpha, h_\alpha)$ is an $\mathfrak{sl}_2$-triple, with
$$h_\alpha = [x_\alpha, y_\alpha] = \frac{2 t_\alpha}{\kappa(t_\alpha, t_\alpha)}.$$
In particular $\alpha(h_\alpha) = 2$ and $h_{-\alpha} = -h_\alpha$.

Lean: `LieAlgebra.IsKilling.lie_eq_killingForm_smul_of_mem_rootSpace_of_mem_rootSpace_neg` for part 3, `LieAlgebra.IsKilling.root_apply_coroot` and `LieAlgebra.IsKilling.exists_isSl2Triple_of_weight_isNonZero` for part 5, from Mathlib; there $h_\alpha$ is `LieAlgebra.IsKilling.coroot`

*Proof.* For part 1, assume that $\Phi$ does not span $\mathfrak{h}^*$. Then there is $h \in \mathfrak{h}$, $h \neq 0$, with $\alpha(h) = 0$ for all $\alpha \in \Phi$. Then $[h, \mathfrak{g}_\alpha] = 0$ for all $\alpha$, and $[h, \mathfrak{h}] = 0$, so $h \in Z(\mathfrak{g}) = 0$. This is a contradiction. For part 2, if $-\alpha \notin \Phi$, then $\kappa(\mathfrak{g}_\alpha, \mathfrak{g}) = 0$ by part 3 of Proposition 2.4.4, which contradicts the nondegeneracy of $\kappa$.

For part 3, $[x, y] \in \mathfrak{g}_0 = \mathfrak{h}$ by Theorem 2.4.5. For $h \in \mathfrak{h}$,
$$\kappa(h, [x, y]) = \kappa([h, x], y) = \alpha(h) \kappa(x, y) = \kappa(h, \kappa(x, y) t_\alpha).$$
Since $\kappa$ is nondegenerate on $\mathfrak{h}$, $[x, y] = \kappa(x, y) t_\alpha$.

For part 4, assume that $\alpha(t_\alpha) = 0$. By the nondegeneracy of $\kappa$ and part 3 of Proposition 2.4.4, the pairing $\kappa : \mathfrak{g}_\alpha \times \mathfrak{g}_{-\alpha} \to F$ is nondegenerate. So there are $x \in \mathfrak{g}_\alpha$ and $y \in \mathfrak{g}_{-\alpha}$ with $\kappa(x, y) = 1$, and then $[x, y] = t_\alpha$. Also $[t_\alpha, x] = \alpha(t_\alpha) x = 0$ and $[t_\alpha, y] = 0$. So $S = F x + F y + F t_\alpha$ is a solvable subalgebra. By Corollary 2.2.10, applied to the module $\mathfrak{g}$ of $S$, the map $\mathrm{ad}\, t_\alpha = [\mathrm{ad}\, x, \mathrm{ad}\, y]$ is nilpotent. It is also semisimple, so $\mathrm{ad}\, t_\alpha = 0$ and $t_\alpha = 0$. This contradicts $\alpha \neq 0$.

For part 5, choose $y_\alpha \in \mathfrak{g}_{-\alpha}$ with $\kappa(x_\alpha, y_\alpha) = 2 / \kappa(t_\alpha, t_\alpha)$, which is possible by the nondegeneracy of the pairing. Then $h_\alpha = [x_\alpha, y_\alpha] = 2 t_\alpha / \kappa(t_\alpha, t_\alpha)$ by part 3. Thus $\alpha(h_\alpha) = 2$, and $[h_\alpha, x_\alpha] = 2 x_\alpha$ and $[h_\alpha, y_\alpha] = -2 y_\alpha$. Finally $t_{-\alpha} = -t_\alpha$, so $h_{-\alpha} = -h_\alpha$. $\square$

We write $S_\alpha = F x_\alpha + F y_\alpha + F h_\alpha$. It is a subalgebra isomorphic to $\mathfrak{sl}_2$. The element $h_\alpha$ is the *coroot* of $\alpha$.

### Integrality properties

**Theorem 2.4.10 (integrality).** Let $\alpha, \beta \in \Phi$.
1. $\dim \mathfrak{g}_\alpha = 1$. So $S_\alpha = \mathfrak{g}_\alpha + \mathfrak{g}_{-\alpha} + [\mathfrak{g}_\alpha, \mathfrak{g}_{-\alpha}]$, and $h_\alpha$ depends only on $\alpha$.
2. If $c \alpha \in \Phi$ for some $c \in F$, then $c = \pm 1$.
3. $\beta(h_\alpha) \in \mathbb{Z}$, and $\beta - \beta(h_\alpha) \alpha \in \Phi$.
4. Assume $\beta \neq \pm \alpha$. Let $r$ and $q$ be the largest integers with $\beta - r \alpha \in \Phi$ and $\beta + q \alpha \in \Phi$. Then $\beta + i \alpha \in \Phi$ for all $-r \le i \le q$, and $\beta(h_\alpha) = r - q$.
5. If $\alpha + \beta \in \Phi$, then $[\mathfrak{g}_\alpha, \mathfrak{g}_\beta] = \mathfrak{g}_{\alpha + \beta}$.
6. $\mathfrak{g}$ is generated as a Lie algebra by the root spaces $\mathfrak{g}_\alpha$, $\alpha \in \Phi$.

Lean: `LieAlgebra.IsKilling.finrank_rootSpace_eq_one` and `LieAlgebra.IsKilling.eq_neg_or_eq_of_eq_smul`, from Mathlib, for parts 1 and 2; `LieAlgebra.IsKilling.chainLength` for the root strings

*Proof.* For parts 1 and 2, consider the subspace
$$M = \mathfrak{h} \oplus \bigoplus_{c \in F^\times} \mathfrak{g}_{c \alpha}.$$
It is stable under $S_\alpha$ by part 1 of Proposition 2.4.4, so it is a finite dimensional $\mathfrak{sl}_2$-module. The element $h_\alpha$ acts on $\mathfrak{g}_{c\alpha}$ by $c \alpha(h_\alpha) = 2c$. So $2c \in \mathbb{Z}$ by Corollary 2.3.6, when $\mathfrak{g}_{c\alpha} \neq 0$. The weight space $M_0$ is $\mathfrak{h}$, of dimension $\ell$. The subspace $\ker \alpha \subset \mathfrak{h}$ has dimension $\ell - 1$, and $S_\alpha$ acts on it by $0$, so it is a sum of $\ell - 1$ copies of $V(0)$. Also $S_\alpha \subset M$ is a submodule isomorphic to $V(2)$. Since $\mathfrak{h} = \ker \alpha \oplus F h_\alpha$, by Weyl's theorem we can write $M = \ker \alpha \oplus S_\alpha \oplus M'$, where $M'$ is a submodule with $M'_0 = 0$. By Corollary 2.3.6, $M'$ has no even weights. So $2\alpha$ is not a root, because its weight $4$ would lie in $M'$. This holds for every root. So $\alpha / 2$ is not a root either, since $2 (\alpha/2) = \alpha$ is one. Thus $1$ is not a weight of $M$. By part 3 of Corollary 2.3.6, $M$ has $\dim M_0 + \dim M_1 = \ell$ irreducible summands, so $M' = 0$ and $M = \ker \alpha \oplus S_\alpha$. Hence $\mathfrak{g}_\alpha = F x_\alpha$, and $\mathfrak{g}_{c\alpha} = 0$ unless $c = \pm 1$. The rest of part 1 follows from part 5 of Proposition 2.4.9.

For parts 3 and 4, let $\beta \neq \pm \alpha$ and $K = \bigoplus_{i \in \mathbb{Z}} \mathfrak{g}_{\beta + i \alpha}$. By part 2, no $\beta + i\alpha$ is $0$, so $K$ is a sum of root spaces, each of dimension 1. It is stable under $S_\alpha$, and $h_\alpha$ acts on $\mathfrak{g}_{\beta + i\alpha}$ by $\beta(h_\alpha) + 2i$. These weights are integers by Corollary 2.3.6, and they are distinct and of the same parity, each of multiplicity 1. So at most one of $0$ and $1$ is a weight of $K$, with multiplicity 1, and $K$ is irreducible by part 3 of Corollary 2.3.6. By Theorem 2.3.4 its weights form an unbroken string, symmetric about $0$: the weights are $\beta(h_\alpha) + 2i$ for $-r \le i \le q$, and $\beta(h_\alpha) - 2r = -(\beta(h_\alpha) + 2q)$. This gives $\beta(h_\alpha) = r - q$, and part 4. Then $\beta - \beta(h_\alpha) \alpha = \beta + (q - r) \alpha$, and $-r \le q - r \le q$, so it is a root. For $\beta = \pm\alpha$ part 3 holds because $\pm\alpha(h_\alpha) = \pm 2$ and $\beta - \beta(h_\alpha)\alpha = -\beta$.

For part 5, $\alpha + \beta \in \Phi$ implies $\beta \neq \pm \alpha$ by part 2. In the irreducible module $K$, the element $x_\alpha$ acts as $e$ and maps the weight space of weight $\mu$ onto the weight space of weight $\mu + 2$ whenever the latter is nonzero, by Lemma 2.3.3. So $[x_\alpha, \mathfrak{g}_\beta] = \mathfrak{g}_{\alpha + \beta}$. For part 6, $\mathfrak{h}$ is spanned by the $t_\alpha$, by part 1 of Proposition 2.4.9, hence by the $h_\alpha = [x_\alpha, y_\alpha]$. $\square$

The integers $\beta(h_\alpha)$ are the *Cartan integers*. The set $\{\beta + i \alpha : -r \le i \le q\}$ is the $\alpha$-*string through* $\beta$. Its length $r + q + 1$ is at most 4, by Section 2.5.

### The roots form a root system

Transport the Killing form to $\mathfrak{h}^*$ by $(\lambda, \mu) = \kappa(t_\lambda, t_\mu)$. Then $(\lambda, \mu) = \lambda(t_\mu)$, and part 5 of Proposition 2.4.9 gives
$$\beta(h_\alpha) = \frac{2 \beta(t_\alpha)}{\kappa(t_\alpha, t_\alpha)} = \frac{2 (\beta, \alpha)}{(\alpha, \alpha)}.$$
Let $E_\mathbb{Q}$ be the $\mathbb{Q}$-subspace of $\mathfrak{h}^*$ spanned by $\Phi$.

**Theorem 2.4.11 (rationality).** The form $(\cdot, \cdot)$ takes rational values on $E_\mathbb{Q}$, and it is positive definite there. Any basis of $\mathfrak{h}^*$ that consists of roots is a $\mathbb{Q}$-basis of $E_\mathbb{Q}$, so $\dim_\mathbb{Q} E_\mathbb{Q} = \ell$. Let $E = \mathbb{R} \otimes_\mathbb{Q} E_\mathbb{Q}$ with the extended form. Then $E$ is a Euclidean space of dimension $\ell$, and $\Phi$ is a root system in $E$ in the sense of Definition 2.5.1.

Lean: `LieAlgebra.IsKilling.rootSystem`, from Mathlib, with the instances `IsRootSystem`, `IsCrystallographic` and `IsReduced`; Mathlib builds it as a root pairing over the base field, without the passage to $\mathbb{R}$

*Proof.* For $\lambda, \mu \in \mathfrak{h}^*$, the root space decomposition and part 1 of Theorem 2.4.10 give
$$(\lambda, \mu) = \mathrm{tr}(\mathrm{ad}\, t_\lambda \circ \mathrm{ad}\, t_\mu) = \sum_{\alpha \in \Phi} \alpha(t_\lambda) \alpha(t_\mu) = \sum_{\alpha \in \Phi} (\alpha, \lambda)(\alpha, \mu).$$
For $\beta \in \Phi$, divide the case $\lambda = \mu = \beta$ by $(\beta, \beta)^2$. This gives
$$\frac{1}{(\beta, \beta)} = \sum_{\alpha \in \Phi} \Big(\frac{(\alpha, \beta)}{(\beta, \beta)}\Big)^2 = \frac{1}{4} \sum_{\alpha \in \Phi} \alpha(h_\beta)^2 \in \mathbb{Q},$$
by part 3 of Theorem 2.4.10. So $(\beta, \beta) \in \mathbb{Q}$, and $(\alpha, \beta) = \tfrac12 \alpha(h_\beta) (\beta, \beta) \in \mathbb{Q}$ for all $\alpha, \beta \in \Phi$.

Choose a basis $\alpha_1, \dots, \alpha_\ell$ of $\mathfrak{h}^*$ in $\Phi$, by part 1 of Proposition 2.4.9. For $\beta \in \Phi$, write $\beta = \sum_i c_i \alpha_i$ with $c_i \in F$. Then $(\beta, \alpha_j) = \sum_i c_i (\alpha_i, \alpha_j)$ for all $j$. The matrix $((\alpha_i, \alpha_j))$ has rational entries, and it is invertible, because the form is nondegenerate on $\mathfrak{h}^*$. So the $c_i$ are rational, and $\alpha_1, \dots, \alpha_\ell$ is a $\mathbb{Q}$-basis of $E_\mathbb{Q}$. For $\lambda \in E_\mathbb{Q}$, the formula above gives $(\lambda, \lambda) = \sum_\alpha (\alpha, \lambda)^2$, a sum of squares of rational numbers. It vanishes only if $(\alpha, \lambda) = 0$ for all $\alpha$, that is, only if $\lambda = 0$. So the form is positive definite on $E_\mathbb{Q}$ and on $E$.

The axioms of Definition 2.5.1 now hold. The set $\Phi$ is finite, spans $E$ and does not contain $0$. The only multiples of $\alpha$ in $\Phi$ are $\pm \alpha$, by part 2 of Theorem 2.4.10. The reflection $\sigma_\alpha(\beta) = \beta - \frac{2(\beta, \alpha)}{(\alpha, \alpha)} \alpha = \beta - \beta(h_\alpha) \alpha$ maps $\Phi$ to $\Phi$, and $\frac{2(\beta, \alpha)}{(\alpha, \alpha)} = \beta(h_\alpha) \in \mathbb{Z}$, by part 3 of Theorem 2.4.10. $\square$

The root system $\Phi \subset E$ is the *root system of* $(\mathfrak{g}, \mathfrak{h})$. Under the identification $\mathfrak{h} \cong \mathfrak{h}^*$ by $\kappa$, the coroot $h_\alpha$ corresponds to $2\alpha / (\alpha, \alpha)$, the element $\alpha^\vee$ of Definition 2.5.1. Section 2.6 shows that $\Phi$ determines $\mathfrak{g}$ up to isomorphism.

### Examples

**Example 2.4.12 (the Lie algebra $\mathfrak{sl}_n$).** Let $\mathfrak{g} = \mathfrak{sl}_n$, and let $\mathfrak{h}$ be the space of diagonal matrices of trace 0. It is toral. It is maximal toral, because the computation below shows that $C_\mathfrak{g}(\mathfrak{h}) = \mathfrak{h}$. For $h = \mathrm{diag}(a_1, \dots, a_n) \in \mathfrak{h}$ let $\varepsilon_i(h) = a_i$. Then $[h, E_{ij}] = (a_i - a_j) E_{ij}$. So the roots are
$$\Phi = \{\varepsilon_i - \varepsilon_j : i \neq j\}, \qquad \mathfrak{g}_{\varepsilon_i - \varepsilon_j} = F E_{ij},$$
and $|\Phi| = n(n-1)$. The rank is $n - 1$. For $\alpha = \varepsilon_i - \varepsilon_j$ we may take $x_\alpha = E_{ij}$ and $y_\alpha = E_{ji}$. Then $h_\alpha = E_{ii} - E_{jj}$, as in Example 2.1.4. By Exercise 3 of Section 2.8, $\kappa(x, y) = 2n\, \mathrm{tr}(xy)$, so $t_\alpha = (E_{ii} - E_{jj})/2n$ and $(\alpha, \alpha) = \alpha(t_\alpha) = 1/n$. For two roots $\alpha = \varepsilon_i - \varepsilon_j$ and $\beta = \varepsilon_j - \varepsilon_k$ with $i, j, k$ distinct, $(\alpha, \beta) = -1/2n$ and $\beta(h_\alpha) = -1$. The $\alpha$-string through $\beta$ is $\beta, \beta + \alpha$, so $r = 0$ and $q = 1$, and indeed $\beta(h_\alpha) = r - q$. Up to the factor $1/2n$, the form $(\cdot, \cdot)$ is the restriction of the standard inner product of $\mathbb{R}^n$ to the hyperplane $\sum x_i = 0$, with $\varepsilon_i$ the coordinate functions. This is the root system $A_{n-1}$ of Section 2.6.

**Example 2.4.13 (the Lie algebra $\mathfrak{sl}_2$).** For $\mathfrak{g} = \mathfrak{sl}_2$ and $\mathfrak{h} = F h$, the roots are $\pm \alpha$ with $\alpha(h) = 2$. The root spaces are $F e$ and $F f$, and $h_\alpha = h$. The Killing form gives $t_\alpha = h/4$ and $(\alpha, \alpha) = 1/2$. The root system is $A_1 = \{\pm \alpha\}$ in the line $E = \mathbb{R}\alpha$.

**Remark 2.4.14 (algebraic groups).** Let $G = SL_n$ over $\mathbb{C}$, and let $T$ be the diagonal torus. The adjoint representation of $T$ on $\mathrm{Lie}(G) = \mathfrak{sl}_n$ is $\mathrm{Ad}(t) E_{ij} = t_i t_j^{-1} E_{ij}$. So the characters of $T$ in $\mathfrak{sl}_n$ are $t \mapsto t_i / t_j$, and their differentials are the roots $\varepsilon_i - \varepsilon_j$ of Example 2.4.12. In general, Chapter 3 defines the roots of a reductive group $G$ with respect to a maximal torus $T$ as the nonzero characters of $T$ in $\mathrm{Lie}(G)$. These characters lie in the lattice $X^*(T)$, and this lattice is the extra structure that a root datum adds to a root system.
