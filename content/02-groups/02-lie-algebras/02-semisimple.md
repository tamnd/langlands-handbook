---
title: Solvable, nilpotent and semisimple Lie algebras
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Solvable, nilpotent and semisimple Lie algebras

This section proves the three basic theorems of the structure theory: the theorems of Engel and Lie, and the criterion of Cartan. With them we prove that a Lie algebra in characteristic 0 is semisimple if and only if its Killing form is nondegenerate, that a semisimple Lie algebra is the direct sum of its simple ideals, and that all its derivations are inner. We also state Weyl's theorem on complete reducibility. The example to keep in mind is $\mathfrak{sl}_2$, whose Killing form we compute. We follow [Hum72], Sections 3 to 6.

### Solvable and nilpotent Lie algebras

Let $\mathfrak{g}$ be a Lie algebra over a field $F$. For subspaces $\mathfrak{a}$ and $\mathfrak{b}$ we write $[\mathfrak{a}, \mathfrak{b}]$ for the span of the brackets $[x, y]$ with $x \in \mathfrak{a}$ and $y \in \mathfrak{b}$. If $\mathfrak{a}$ and $\mathfrak{b}$ are ideals, then $[\mathfrak{a}, \mathfrak{b}]$ is an ideal, by the Jacobi identity.

**Definition 2.2.1 (solvable and nilpotent).** The *derived series* of $\mathfrak{g}$ is $\mathfrak{g}^{(0)} = \mathfrak{g}$, $\mathfrak{g}^{(i+1)} = [\mathfrak{g}^{(i)}, \mathfrak{g}^{(i)}]$. The *lower central series* is $\mathcal{C}^0 \mathfrak{g} = \mathfrak{g}$, $\mathcal{C}^{i+1} \mathfrak{g} = [\mathfrak{g}, \mathcal{C}^i \mathfrak{g}]$. The Lie algebra $\mathfrak{g}$ is *solvable* if $\mathfrak{g}^{(n)} = 0$ for some $n$, and *nilpotent* if $\mathcal{C}^n \mathfrak{g} = 0$ for some $n$.

Lean: `LieAlgebra.derivedSeries`, `LieAlgebra.IsSolvable`, `LieModule.lowerCentralSeries` and `LieRing.IsNilpotent`, from Mathlib

All terms of both series are ideals, and $\mathfrak{g}^{(i)} \subset \mathcal{C}^i \mathfrak{g}$ by induction on $i$. So a nilpotent Lie algebra is solvable. The Lie algebra $\mathfrak{g}$ is nilpotent if and only if there is an $n$ with $\mathrm{ad}\, x_1 \circ \cdots \circ \mathrm{ad}\, x_n = 0$ for all $x_1, \dots, x_n \in \mathfrak{g}$.

**Proposition 2.2.2 (closure properties).** Let $\mathfrak{g}$ be a Lie algebra.
1. Subalgebras and quotients of a solvable Lie algebra are solvable. If $\mathfrak{a}$ is a solvable ideal and $\mathfrak{g} / \mathfrak{a}$ is solvable, then $\mathfrak{g}$ is solvable.
2. If $\mathfrak{a}$ and $\mathfrak{b}$ are solvable ideals of $\mathfrak{g}$, then $\mathfrak{a} + \mathfrak{b}$ is a solvable ideal.
3. Subalgebras and quotients of a nilpotent Lie algebra are nilpotent. If $\mathfrak{g} / Z(\mathfrak{g})$ is nilpotent, then $\mathfrak{g}$ is nilpotent.

Lean: not stated yet in this form; Mathlib has instances for each part

*Proof.* A surjective homomorphism $\varphi : \mathfrak{g} \to \mathfrak{q}$ maps $\mathfrak{g}^{(i)}$ onto $\mathfrak{q}^{(i)}$ and $\mathcal{C}^i \mathfrak{g}$ onto $\mathcal{C}^i \mathfrak{q}$, and for a subalgebra $\mathfrak{s}$ we have $\mathfrak{s}^{(i)} \subset \mathfrak{g}^{(i)}$ and $\mathcal{C}^i \mathfrak{s} \subset \mathcal{C}^i \mathfrak{g}$. This gives the first statements of parts 1 and 3. If $(\mathfrak{g} / \mathfrak{a})^{(n)} = 0$, then $\mathfrak{g}^{(n)} \subset \mathfrak{a}$, and $\mathfrak{g}^{(n+m)} \subset \mathfrak{a}^{(m)}$, which is $0$ for large $m$. For part 2, the quotient $(\mathfrak{a} + \mathfrak{b}) / \mathfrak{b} \cong \mathfrak{a} / (\mathfrak{a} \cap \mathfrak{b})$ is solvable, so part 1 applies. For the end of part 3, if $\mathcal{C}^n \mathfrak{g} \subset Z(\mathfrak{g})$, then $\mathcal{C}^{n+1} \mathfrak{g} = 0$. $\square$

By part 2, a finite dimensional Lie algebra $\mathfrak{g}$ has a unique maximal solvable ideal, the sum of all solvable ideals.

**Definition 2.2.3 (radical, semisimple, simple).** The *radical* $\mathrm{rad}\, \mathfrak{g}$ is the maximal solvable ideal of $\mathfrak{g}$. The Lie algebra $\mathfrak{g}$ is *semisimple* if $\mathrm{rad}\, \mathfrak{g} = 0$. It is *simple* if it is not abelian and its only ideals are $0$ and $\mathfrak{g}$.

Lean: `LieAlgebra.radical`, `LieAlgebra.HasTrivialRadical` and `LieAlgebra.IsSimple`, from Mathlib

A simple Lie algebra is semisimple: its radical is $0$ or $\mathfrak{g}$, and it is not $\mathfrak{g}$, because $[\mathfrak{g}, \mathfrak{g}]$ is a nonzero ideal, so $[\mathfrak{g}, \mathfrak{g}] = \mathfrak{g}$. The quotient $\mathfrak{g} / \mathrm{rad}\, \mathfrak{g}$ is semisimple, by part 1 of Proposition 2.2.2. Mathlib defines `LieAlgebra.IsSemisimple` in a different way, as a Lie algebra that is the direct sum of simple ideals. Theorem 2.2.18 below shows that the two definitions agree in characteristic 0.

**Example 2.2.4.** The algebra $\mathfrak{b}_n$ of upper triangular matrices is solvable, and the algebra $\mathfrak{n}_n$ of strictly upper triangular matrices is nilpotent. Indeed, $[\mathfrak{b}_n, \mathfrak{b}_n] \subset \mathfrak{n}_n$, and $\mathcal{C}^i \mathfrak{n}_n$ consists of matrices that vanish on the diagonal and on the first $i$ diagonals above it. The algebra $\mathfrak{b}_n$ is not nilpotent for $n \ge 2$: with $h = \mathrm{diag}(1, -1, 0, \dots, 0)$ and $e = E_{12}$, we have $(\mathrm{ad}\, h)^m e = 2^m e \neq 0$ for all $m$. The algebra $\mathfrak{gl}_n$ is not semisimple, because the scalar matrices form an abelian ideal. Its radical is the space of scalar matrices in characteristic 0.

### Engel's theorem

**Lemma 2.2.5.** Let $V$ be a finite dimensional vector space, and let $x \in \mathfrak{gl}(V)$ be nilpotent. Then $\mathrm{ad}\, x \in \mathfrak{gl}(\mathfrak{gl}(V))$ is nilpotent.

Lean: not stated yet

*Proof.* Let $\lambda_x$ and $\rho_x$ be the left and right multiplications by $x$ on $\mathrm{End}(V)$. They commute, they are nilpotent, and $\mathrm{ad}\, x = \lambda_x - \rho_x$. The difference of two commuting nilpotent maps is nilpotent, by the binomial formula. $\square$

**Theorem 2.2.6 (Engel, linear form).** Let $V \neq 0$ be a finite dimensional vector space, and let $\mathfrak{g} \subset \mathfrak{gl}(V)$ be a subalgebra of nilpotent endomorphisms. Then there is $v \in V$, $v \neq 0$, with $x v = 0$ for all $x \in \mathfrak{g}$.

Lean: `LieModule.isNilpotent_iff_forall`, from Mathlib, is the module form

*Proof.* We use induction on $\dim \mathfrak{g}$. The cases $\dim \mathfrak{g} \le 1$ are clear, because a nilpotent endomorphism has a nonzero kernel. Let $\mathfrak{k} \neq \mathfrak{g}$ be a maximal proper subalgebra. The algebra $\mathfrak{k}$ acts on the vector space $\mathfrak{g} / \mathfrak{k}$ by $\mathrm{ad}$, and each element acts nilpotently, by Lemma 2.2.5. Since $\dim \mathfrak{k} < \dim \mathfrak{g}$, the induction hypothesis gives $y \in \mathfrak{g} \setminus \mathfrak{k}$ with $[\mathfrak{k}, y] \subset \mathfrak{k}$. Then $\mathfrak{k} + F y$ is a subalgebra that contains $\mathfrak{k}$ properly. So $\mathfrak{g} = \mathfrak{k} + F y$, and $\mathfrak{k}$ is an ideal of codimension 1.

Let $W = \{v \in V : \mathfrak{k} v = 0\}$. By the induction hypothesis, $W \neq 0$. The space $W$ is stable under $\mathfrak{g}$: for $x \in \mathfrak{g}$, $z \in \mathfrak{k}$ and $w \in W$, we have $z x w = x z w - [x, z] w = 0$, because $[x, z] \in \mathfrak{k}$. The nilpotent endomorphism $y$ of $W$ has a nonzero vector $v$ in its kernel. Then $\mathfrak{k} v = 0$ and $y v = 0$, so $\mathfrak{g} v = 0$. $\square$

By induction on $\dim V$, the theorem gives a flag $0 = V_0 \subset V_1 \subset \cdots \subset V_n = V$ with $\dim V_i = i$ and $\mathfrak{g} V_i \subset V_{i-1}$. So in a suitable basis $\mathfrak{g} \subset \mathfrak{n}_n$.

**Corollary 2.2.7 (Engel's theorem).** A finite dimensional Lie algebra $\mathfrak{g}$ is nilpotent if and only if $\mathrm{ad}\, x$ is nilpotent for each $x \in \mathfrak{g}$.

Lean: `LieAlgebra.isNilpotent_iff_forall`, from Mathlib

*Proof.* If $\mathcal{C}^n \mathfrak{g} = 0$, then $(\mathrm{ad}\, x)^n = 0$. Conversely, assume that each $\mathrm{ad}\, x$ is nilpotent. We use induction on $\dim \mathfrak{g}$. Theorem 2.2.6, applied to $\mathrm{ad}\, \mathfrak{g} \subset \mathfrak{gl}(\mathfrak{g})$, gives $x \neq 0$ with $[\mathfrak{g}, x] = 0$. So $Z(\mathfrak{g}) \neq 0$. The quotient $\mathfrak{g} / Z(\mathfrak{g})$ has smaller dimension, and its elements act nilpotently by $\mathrm{ad}$. By induction it is nilpotent, so $\mathfrak{g}$ is nilpotent by Proposition 2.2.2. $\square$

### Lie's theorem

From now on in this section, $F$ is algebraically closed of characteristic 0.

**Lemma 2.2.8 (invariance lemma).** Let $\mathfrak{g}$ be a Lie algebra, let $\mathfrak{k}$ be an ideal of $\mathfrak{g}$, and let $V$ be a finite dimensional $\mathfrak{g}$-module. For a linear form $\lambda$ on $\mathfrak{k}$, the subspace
$$W = \{v \in V : y v = \lambda(y) v \text{ for all } y \in \mathfrak{k}\}$$
is stable under $\mathfrak{g}$.

Lean: not stated yet

*Proof.* Let $x \in \mathfrak{g}$ and $w \in W$, $w \neq 0$. For $y \in \mathfrak{k}$ we have $y x w = x y w - [x, y] w = \lambda(y) x w - \lambda([x, y]) w$, so it suffices to show that $\lambda([x, y]) = 0$. Let $n \ge 1$ be the least integer such that $w, xw, \dots, x^n w$ are linearly dependent, and let $W_i$ be the span of $w, xw, \dots, x^{i-1} w$. Then $W_n$ is stable under $x$. We claim that for each $y \in \mathfrak{k}$ and $i \ge 0$,
$$y x^i w \equiv \lambda(y) x^i w \mod W_i.$$
This holds for $i = 0$. For $i \ge 1$, write $y x^i w = x (y x^{i-1} w) - [x, y] x^{i-1} w$. By induction, $y x^{i-1} w = \lambda(y) x^{i-1} w + u$ with $u \in W_{i-1}$, and $x u \in W_i$. Also $[x, y] \in \mathfrak{k}$, so $[x, y] x^{i-1} w \in W_i$, again by induction. This proves the claim. Thus each $y \in \mathfrak{k}$ stabilizes $W_n$, and in the basis $w, xw, \dots, x^{n-1} w$ it is upper triangular with all diagonal entries $\lambda(y)$. So $\mathrm{tr}_{W_n}(y) = n \lambda(y)$. Apply this to $[x, y] \in \mathfrak{k}$. Both $x$ and $y$ stabilize $W_n$, so $\mathrm{tr}_{W_n}([x, y]) = 0$ as the trace of a commutator. Thus $n \lambda([x, y]) = 0$, and $\lambda([x, y]) = 0$, because $F$ has characteristic 0. $\square$

**Theorem 2.2.9 (Lie).** Let $\mathfrak{g}$ be a solvable Lie algebra, and let $V \neq 0$ be a finite dimensional $\mathfrak{g}$-module. Then $V$ has a common eigenvector for all elements of $\mathfrak{g}$.

Lean: `LieModule.exists_nontrivial_weightSpace_of_isSolvable`, from Mathlib

*Proof.* We use induction on $\dim \mathfrak{g}$, and the case $\mathfrak{g} = 0$ is trivial. Since $\mathfrak{g}$ is solvable and nonzero, $[\mathfrak{g}, \mathfrak{g}] \neq \mathfrak{g}$. Each subspace of $\mathfrak{g}$ that contains $[\mathfrak{g}, \mathfrak{g}]$ is an ideal. Choose such an ideal $\mathfrak{k}$ of codimension 1, and choose $z \in \mathfrak{g} \setminus \mathfrak{k}$. The ideal $\mathfrak{k}$ is solvable, so by induction it has a common eigenvector in $V$. This means that there is a linear form $\lambda$ on $\mathfrak{k}$ with $W \neq 0$ in the notation of Lemma 2.2.8. By Lemma 2.2.8, $W$ is stable under $z$. Since $F$ is algebraically closed, $z$ has an eigenvector $v \in W$. Then $v$ is an eigenvector for $\mathfrak{k} + F z = \mathfrak{g}$. $\square$

**Corollary 2.2.10.** Let $\mathfrak{g}$ be a solvable Lie algebra.
1. Each finite dimensional $\mathfrak{g}$-module $V$ has a basis in which all elements of $\mathfrak{g}$ act by upper triangular matrices.
2. The derived algebra $[\mathfrak{g}, \mathfrak{g}]$ is nilpotent.

Lean: not stated yet

*Proof.* Part 1 follows from Theorem 2.2.9 by induction on $\dim V$, applied to $V / F v$. For part 2, apply part 1 to the adjoint representation. In the resulting basis $\mathrm{ad}\, x$ is upper triangular for each $x$, so $\mathrm{ad}\, [x, y] = [\mathrm{ad}\, x, \mathrm{ad}\, y]$ is strictly upper triangular. Thus $\mathrm{ad}_\mathfrak{g}\, z$ is nilpotent for $z \in [\mathfrak{g}, \mathfrak{g}]$, and so is its restriction $\mathrm{ad}_{[\mathfrak{g}, \mathfrak{g}]}\, z$. Engel's theorem (Corollary 2.2.7) applies. $\square$

### Cartan's criterion

**Theorem 2.2.11 (Jordan-Chevalley decomposition).** Let $V$ be a finite dimensional vector space and $x \in \mathrm{End}(V)$. There are unique $x_s, x_n \in \mathrm{End}(V)$ with $x = x_s + x_n$, $x_s$ semisimple (diagonalizable), $x_n$ nilpotent and $x_s x_n = x_n x_s$. In addition, $x_s$ and $x_n$ are polynomials in $x$ without constant term. If $x = x_s + x_n$ is this decomposition, then $\mathrm{ad}\, x = \mathrm{ad}\, x_s + \mathrm{ad}\, x_n$ is the Jordan-Chevalley decomposition of $\mathrm{ad}\, x$ in $\mathrm{End}(\mathrm{End}(V))$.

Lean: `Module.End.exists_isNilpotent_isSemisimple`, from Mathlib, gives the existence

*Proof sketch.* The decomposition comes from the Chinese remainder theorem applied to the characteristic polynomial of $x$. For the last claim, $\mathrm{ad}\, x_s$ is semisimple, because $x_s$ is diagonal in some basis $(v_i)$ and then $\mathrm{ad}\, x_s$ is diagonal in the basis $(E_{ij})$. Also $\mathrm{ad}\, x_n$ is nilpotent by Lemma 2.2.5, and $\mathrm{ad}\, x_s$ and $\mathrm{ad}\, x_n$ commute. See [Hum72], Section 4.2. $\square$

**Lemma 2.2.12.** Let $A \subset B$ be subspaces of $\mathfrak{gl}(V)$, and let $M = \{x \in \mathfrak{gl}(V) : [x, B] \subset A\}$. Assume that $x \in M$ satisfies $\mathrm{tr}(x y) = 0$ for all $y \in M$. Then $x$ is nilpotent.

Lean: not stated yet

*Proof sketch.* Let $x = s + n$ be the Jordan-Chevalley decomposition, and choose a basis in which $s = \mathrm{diag}(a_1, \dots, a_m)$. Let $E \subset F$ be the $\mathbb{Q}$-subspace spanned by $a_1, \dots, a_m$. We show that $E = 0$, so $s = 0$. Let $f : E \to \mathbb{Q}$ be $\mathbb{Q}$-linear, and let $y = \mathrm{diag}(f(a_1), \dots, f(a_m))$. Then $\mathrm{ad}\, y$ acts on $E_{ij}$ by $f(a_i) - f(a_j) = f(a_i - a_j)$, and Lagrange interpolation gives a polynomial $r$ without constant term with $\mathrm{ad}\, y = r(\mathrm{ad}\, s)$. By Theorem 2.2.11, $\mathrm{ad}\, s$ is a polynomial in $\mathrm{ad}\, x$ without constant term, so $\mathrm{ad}\, y$ maps $B$ into $A$, and $y \in M$. Thus $0 = \mathrm{tr}(x y) = \sum_i a_i f(a_i)$. Apply $f$: $\sum_i f(a_i)^2 = 0$, so all $f(a_i) = 0$, and $f = 0$. See [Hum72], Section 4.3. $\square$

**Theorem 2.2.13 (Cartan's criterion).** Let $\mathfrak{g} \subset \mathfrak{gl}(V)$ be a subalgebra, with $V$ finite dimensional. If $\mathrm{tr}(x y) = 0$ for all $x \in [\mathfrak{g}, \mathfrak{g}]$ and $y \in \mathfrak{g}$, then $\mathfrak{g}$ is solvable.

Lean: `LieAlgebra.isSolvable_of_killingForm_apply_lie_eq_zero`, from Mathlib, for the adjoint form

*Proof.* By Proposition 2.2.2 it suffices to show that $[\mathfrak{g}, \mathfrak{g}]$ is nilpotent. By Lemma 2.2.5 and Engel's theorem it suffices to show that each $x \in [\mathfrak{g}, \mathfrak{g}]$ is a nilpotent endomorphism of $V$. Apply Lemma 2.2.12 with $A = [\mathfrak{g}, \mathfrak{g}]$ and $B = \mathfrak{g}$. Then $\mathfrak{g} \subset M$. For $x = [a, b]$ with $a, b \in \mathfrak{g}$ and for $z \in M$, the identity $\mathrm{tr}([a, b] z) = \mathrm{tr}(a [b, z])$ holds, and $[b, z] \in [\mathfrak{g}, \mathfrak{g}]$ by the definition of $M$. So $\mathrm{tr}([a, b] z) = 0$ by hypothesis. By linearity $\mathrm{tr}(x z) = 0$ for all $x \in [\mathfrak{g}, \mathfrak{g}]$ and $z \in M$. Lemma 2.2.12 shows that $x$ is nilpotent. $\square$

### The Killing form

**Definition 2.2.14 (Killing form).** The *Killing form* of a finite dimensional Lie algebra $\mathfrak{g}$ is the bilinear form
$$\kappa(x, y) = \mathrm{tr}(\mathrm{ad}\, x \circ \mathrm{ad}\, y).$$
More generally, a representation $\rho : \mathfrak{g} \to \mathfrak{gl}(V)$ gives the *trace form* $\beta_\rho(x, y) = \mathrm{tr}(\rho(x) \rho(y))$.

Lean: `LieModule.traceForm` and `killingForm`, from Mathlib

**Lemma 2.2.15.** Let $\mathfrak{g}$ be a finite dimensional Lie algebra.
1. The Killing form is symmetric and *invariant*: $\kappa([x, y], z) = \kappa(x, [y, z])$.
2. The orthogonal $\mathfrak{a}^\perp$ of an ideal $\mathfrak{a}$ for $\kappa$ is an ideal.
3. If $\mathfrak{a}$ is an ideal, then the Killing form of $\mathfrak{a}$ is the restriction of $\kappa$ to $\mathfrak{a} \times \mathfrak{a}$.

Lean: `LieModule.traceForm_comm` and `LieModule.traceForm_apply_lie_apply`, from Mathlib, for part 1

*Proof.* Part 1 follows from $\mathrm{tr}(ab) = \mathrm{tr}(ba)$ and from $\mathrm{tr}([a, b] c) = \mathrm{tr}(a [b, c])$, applied to $a = \mathrm{ad}\, x$, $b = \mathrm{ad}\, y$, $c = \mathrm{ad}\, z$. For part 2, let $x \in \mathfrak{a}^\perp$, $y \in \mathfrak{g}$ and $z \in \mathfrak{a}$. Then $\kappa([y, x], z) = -\kappa(x, [y, z]) = 0$, because $[y, z] \in \mathfrak{a}$. For part 3, if an endomorphism $\varphi$ of a vector space $U$ maps $U$ into a subspace $W$, then $\mathrm{tr}(\varphi) = \mathrm{tr}(\varphi|_W)$, as we see in a basis of $U$ that extends a basis of $W$. For $x, y \in \mathfrak{a}$ the map $\mathrm{ad}\, x \circ \mathrm{ad}\, y$ maps $\mathfrak{g}$ into $\mathfrak{a}$. $\square$

**Example 2.2.16 (the Killing form of $\mathfrak{sl}_2$).** In the basis $(e, h, f)$ of Example 2.1.4 the adjoint matrices are
$$\mathrm{ad}\, h = \begin{pmatrix} 2 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & -2 \end{pmatrix}, \quad \mathrm{ad}\, e = \begin{pmatrix} 0 & -2 & 0 \\ 0 & 0 & 1 \\ 0 & 0 & 0 \end{pmatrix}, \quad \mathrm{ad}\, f = \begin{pmatrix} 0 & 0 & 0 \\ -1 & 0 & 0 \\ 0 & 2 & 0 \end{pmatrix}.$$
For example $\mathrm{ad}\, e$ maps $e \mapsto 0$, $h \mapsto -2e$ and $f \mapsto h$. Matrix products give $\kappa(h, h) = 8$, $\kappa(e, f) = 4$, and $\kappa(e, e) = \kappa(f, f) = \kappa(e, h) = \kappa(f, h) = 0$. So the matrix of $\kappa$ in the basis $(e, h, f)$ is
$$\begin{pmatrix} 0 & 0 & 4 \\ 0 & 8 & 0 \\ 4 & 0 & 0 \end{pmatrix},$$
with determinant $-128 \neq 0$. In other words $\kappa(x, y) = 4\, \mathrm{tr}(xy)$ on $\mathfrak{sl}_2$. Exercise 3 of Section 2.8 shows that $\kappa(x, y) = 2n\, \mathrm{tr}(xy)$ on $\mathfrak{sl}_n$.

**Theorem 2.2.17 (semisimplicity criterion).** A finite dimensional Lie algebra $\mathfrak{g}$ is semisimple if and only if its Killing form is nondegenerate.

Lean: `LieAlgebra.hasTrivialRadical_iff_isKilling`, from Mathlib

*Proof.* Let $\mathfrak{s} = \mathfrak{g}^\perp$ be the radical of the form $\kappa$. It is an ideal by Lemma 2.2.15. Assume first that $\mathrm{rad}\, \mathfrak{g} = 0$. For $x \in \mathfrak{s}$ and $y \in \mathfrak{g}$, we have $\mathrm{tr}(\mathrm{ad}\, x \circ \mathrm{ad}\, y) = 0$. In particular this holds for $x \in [\mathfrak{s}, \mathfrak{s}]$ and $y \in \mathfrak{s}$. Cartan's criterion (Theorem 2.2.13), applied to $\mathrm{ad}\, \mathfrak{s} \subset \mathfrak{gl}(\mathfrak{g})$, shows that $\mathrm{ad}\, \mathfrak{s}$ is solvable. The kernel of $\mathrm{ad}$ on $\mathfrak{s}$ is $\mathfrak{s} \cap Z(\mathfrak{g})$, which is abelian. So $\mathfrak{s}$ is solvable by Proposition 2.2.2, and $\mathfrak{s} \subset \mathrm{rad}\, \mathfrak{g} = 0$.

Conversely, assume that $\mathfrak{s} = 0$. If $\mathrm{rad}\, \mathfrak{g} \neq 0$, then the last nonzero term of its derived series is a nonzero abelian ideal $\mathfrak{a}$ of $\mathfrak{g}$, because the terms of the derived series of an ideal are ideals. We show that $\mathfrak{a} \subset \mathfrak{s}$, which is a contradiction. Let $x \in \mathfrak{a}$ and $y \in \mathfrak{g}$. The map $\mathrm{ad}\, x \circ \mathrm{ad}\, y$ maps $\mathfrak{g}$ into $\mathfrak{a}$, so $(\mathrm{ad}\, x \circ \mathrm{ad}\, y)^2$ maps $\mathfrak{g}$ into $[\mathfrak{a}, \mathfrak{a}] = 0$. A nilpotent map has trace 0, so $\kappa(x, y) = 0$. $\square$

By Example 2.2.16, $\mathfrak{sl}_2$ is semisimple in characteristic 0. It is also simple, by the next theorem, because a simple Lie algebra has dimension at least 3.

### Simple ideals and derivations

**Theorem 2.2.18 (simple ideals).** Let $\mathfrak{g}$ be a semisimple Lie algebra. There are ideals $\mathfrak{g}_1, \dots, \mathfrak{g}_t$ of $\mathfrak{g}$, each simple as a Lie algebra, with $\mathfrak{g} = \mathfrak{g}_1 \oplus \cdots \oplus \mathfrak{g}_t$. Every simple ideal of $\mathfrak{g}$ is one of the $\mathfrak{g}_i$, and the Killing form of $\mathfrak{g}_i$ is the restriction of $\kappa$.

Lean: `LieAlgebra.IsKilling.instSemisimple`, from Mathlib, gives the decomposition for a Lie algebra with nondegenerate Killing form

*Proof.* Let $\mathfrak{a}$ be an ideal. Then $\mathfrak{a}^\perp$ is an ideal, and the restriction of $\kappa$ to $\mathfrak{a} \cap \mathfrak{a}^\perp$ is $0$. By Lemma 2.2.15 and Cartan's criterion applied to $\mathrm{ad}(\mathfrak{a} \cap \mathfrak{a}^\perp)$, the ideal $\mathfrak{a} \cap \mathfrak{a}^\perp$ is solvable, as in the proof of Theorem 2.2.17. So $\mathfrak{a} \cap \mathfrak{a}^\perp = 0$. Since $\kappa$ is nondegenerate, $\dim \mathfrak{a} + \dim \mathfrak{a}^\perp = \dim \mathfrak{g}$, and $\mathfrak{g} = \mathfrak{a} \oplus \mathfrak{a}^\perp$.

We prove the existence by induction on $\dim \mathfrak{g}$. Let $\mathfrak{g}_1$ be a minimal nonzero ideal. Then $\mathfrak{g} = \mathfrak{g}_1 \oplus \mathfrak{g}_1^\perp$, and $[\mathfrak{g}_1, \mathfrak{g}_1^\perp] \subset \mathfrak{g}_1 \cap \mathfrak{g}_1^\perp = 0$. So an ideal of $\mathfrak{g}_1$ is an ideal of $\mathfrak{g}$, and the same holds for $\mathfrak{g}_1^\perp$. Thus $\mathfrak{g}_1$ has no ideals other than $0$ and $\mathfrak{g}_1$. It is not abelian, because $\mathrm{rad}\, \mathfrak{g} = 0$, so it is simple. The radical of $\mathfrak{g}_1^\perp$ is a solvable ideal of $\mathfrak{g}$, so it is $0$, and $\mathfrak{g}_1^\perp$ is semisimple. The induction hypothesis applies to $\mathfrak{g}_1^\perp$.

For the uniqueness, let $\mathfrak{a}$ be a simple ideal of $\mathfrak{g}$. Then $[\mathfrak{g}, \mathfrak{a}]$ is an ideal of $\mathfrak{a}$. It is nonzero, because $Z(\mathfrak{g})$ is an abelian ideal and so it is $0$. So $\mathfrak{a} = [\mathfrak{g}, \mathfrak{a}] = [\mathfrak{g}_1, \mathfrak{a}] \oplus \cdots \oplus [\mathfrak{g}_t, \mathfrak{a}]$. Each $[\mathfrak{g}_i, \mathfrak{a}]$ is an ideal of $\mathfrak{a}$, so exactly one of them is nonzero, say for $i$, and it is $\mathfrak{a}$. Then $\mathfrak{a} = [\mathfrak{g}_i, \mathfrak{a}] \subset \mathfrak{g}_i$, and $\mathfrak{a} = \mathfrak{g}_i$ because $\mathfrak{g}_i$ is simple. The last claim is part 3 of Lemma 2.2.15. $\square$

**Corollary 2.2.19.** If $\mathfrak{g}$ is semisimple, then $\mathfrak{g} = [\mathfrak{g}, \mathfrak{g}]$, and all ideals and all quotients of $\mathfrak{g}$ are semisimple. Each ideal of $\mathfrak{g}$ is the sum of some of the $\mathfrak{g}_i$.

Lean: not stated yet

*Proof.* Each $\mathfrak{g}_i$ is simple, so $[\mathfrak{g}_i, \mathfrak{g}_i] = \mathfrak{g}_i$, and $\mathfrak{g} = [\mathfrak{g}, \mathfrak{g}]$. Let $\mathfrak{a}$ be an ideal. The first paragraph of the proof of Theorem 2.2.18 gives $\mathfrak{g} = \mathfrak{a} \oplus \mathfrak{a}^\perp$ with $[\mathfrak{a}, \mathfrak{a}^\perp] = 0$. So each ideal of $\mathfrak{a}$ is an ideal of $\mathfrak{g}$. In particular $\mathrm{rad}\, \mathfrak{a} = 0$, and $\mathfrak{a}$ is semisimple. The simple ideals of $\mathfrak{a}$ are simple ideals of $\mathfrak{g}$, so they are some of the $\mathfrak{g}_i$, and $\mathfrak{a}$ is their sum by Theorem 2.2.18 for $\mathfrak{a}$. Finally $\mathfrak{g} / \mathfrak{a} \cong \mathfrak{a}^\perp$, which is semisimple by the same argument. $\square$

**Theorem 2.2.20 (derivations are inner).** If $\mathfrak{g}$ is semisimple, then $\mathrm{ad} : \mathfrak{g} \to \mathrm{Der}\, \mathfrak{g}$ is an isomorphism.

Lean: `LieDerivation.IsKilling.exists_eq_ad`, from Mathlib

*Proof.* The map $\mathrm{ad}$ is injective, since $Z(\mathfrak{g}) = 0$. Let $\mathfrak{m} = \mathrm{ad}\, \mathfrak{g}$ and $\mathfrak{d} = \mathrm{Der}\, \mathfrak{g}$. For $\delta \in \mathfrak{d}$ and $x \in \mathfrak{g}$, the derivation rule gives $[\delta, \mathrm{ad}\, x] = \mathrm{ad}(\delta x)$. So $\mathfrak{m}$ is an ideal of $\mathfrak{d}$. Let $\kappa_\mathfrak{d}$ be the Killing form of $\mathfrak{d}$. Its restriction to $\mathfrak{m}$ is the Killing form of $\mathfrak{m} \cong \mathfrak{g}$, by Lemma 2.2.15, and that form is nondegenerate. So $\mathfrak{m} \cap \mathfrak{m}^\perp = 0$, where $\mathfrak{m}^\perp$ is the orthogonal for $\kappa_\mathfrak{d}$. Both are ideals of $\mathfrak{d}$, so $[\mathfrak{m}^\perp, \mathfrak{m}] = 0$. For $\delta \in \mathfrak{m}^\perp$ and $x \in \mathfrak{g}$, we get $\mathrm{ad}(\delta x) = [\delta, \mathrm{ad}\, x] = 0$, so $\delta x \in Z(\mathfrak{g}) = 0$, and $\delta = 0$. Thus $\mathfrak{m}^\perp = 0$. Since $\dim \mathfrak{m}^\perp \ge \dim \mathfrak{d} - \dim \mathfrak{m}$, we get $\mathfrak{m} = \mathfrak{d}$. $\square$

**Theorem 2.2.21 (abstract Jordan decomposition).** Let $\mathfrak{g}$ be semisimple. Each $x \in \mathfrak{g}$ has a unique decomposition $x = x_s + x_n$ with $\mathrm{ad}\, x_s$ semisimple, $\mathrm{ad}\, x_n$ nilpotent and $[x_s, x_n] = 0$. If $\rho : \mathfrak{g} \to \mathfrak{gl}(V)$ is a finite dimensional representation, then $\rho(x_s)$ and $\rho(x_n)$ are the semisimple and the nilpotent parts of $\rho(x)$. In particular, for $\mathfrak{g} \subset \mathfrak{gl}(V)$ the two decompositions agree.

Lean: not stated yet

*Proof sketch.* The semisimple and the nilpotent parts of a derivation are derivations. This follows from the formula $(\delta - a - b)^n [x, y] = \sum_i \binom{n}{i} [(\delta - a)^{n-i} x, (\delta - b)^i y]$ for the generalized eigenspaces of $\delta$. By Theorem 2.2.20 they are $\mathrm{ad}\, x_s$ and $\mathrm{ad}\, x_n$ for unique $x_s$ and $x_n$. See [Hum72], Section 5.4. The statement about representations uses Weyl's theorem below, and it is [Hum72], Section 6.4. $\square$

An element $x$ of a semisimple Lie algebra is *semisimple* if $x = x_s$, that is, if $\mathrm{ad}\, x$ is diagonalizable, and *nilpotent* if $x = x_n$. In $\mathfrak{sl}_2$, the element $h$ is semisimple, and $e$ and $f$ are nilpotent.

### Weyl's theorem

A module $V$ is *irreducible* if $V \neq 0$ and $0$ and $V$ are its only submodules. It is *completely reducible* if it is a direct sum of irreducible submodules, or, in an equivalent form, if each submodule has a complementary submodule.

**Theorem 2.2.22 (Weyl).** Let $\mathfrak{g}$ be a semisimple Lie algebra. Every finite dimensional $\mathfrak{g}$-module is completely reducible.

Lean: not in Mathlib

*Proof sketch.* Let $\rho : \mathfrak{g} \to \mathfrak{gl}(V)$ be a representation. We may replace $\mathfrak{g}$ by $\rho(\mathfrak{g})$, which is semisimple by Corollary 2.2.19, so we may assume that $\rho$ is faithful. The trace form $\beta(x, y) = \mathrm{tr}(\rho(x) \rho(y))$ is invariant, and it is nondegenerate by Cartan's criterion, as in the proof of Theorem 2.2.17. Let $(x_i)$ be a basis of $\mathfrak{g}$, and let $(y_i)$ be the dual basis for $\beta$. The *Casimir element* $c_\rho = \sum_i \rho(x_i) \rho(y_i)$ commutes with $\rho(\mathfrak{g})$ and has trace $\dim \mathfrak{g}$. So it acts on an irreducible $V$ by the nonzero scalar $\dim \mathfrak{g} / \dim V$.

Consider first a submodule $W$ of codimension 1 that is irreducible. The algebra $\mathfrak{g} = [\mathfrak{g}, \mathfrak{g}]$ acts trivially on the one dimensional module $V / W$, so $c_\rho$ maps $V$ into $W$. It acts on $W$ by a nonzero scalar. So $\ker c_\rho$ is a submodule of dimension 1 and a complement of $W$. Induction on $\dim W$ removes the condition that $W$ is irreducible. For an arbitrary submodule $W$, let $\mathcal{V}$ be the space of linear maps $V \to W$ that are scalar on $W$, and let $\mathcal{W} \subset \mathcal{V}$ be the subspace of maps that vanish on $W$. These are $\mathfrak{g}$-modules for the action $(x \varphi)(v) = x \varphi(v) - \varphi(x v)$, and $\mathcal{W}$ has codimension 1 in $\mathcal{V}$. A complement of $\mathcal{W}$ is spanned by a module map $\varphi : V \to W$ that is the identity on $W$, and $\ker \varphi$ is a complement of $W$. See [Hum72], Sections 6.2 and 6.3. $\square$

Weyl's own proof uses the compact form of $\mathfrak{g}$ and the integration over a compact group. This is the *unitary trick*, and Chapter 4 explains it. Theorem 2.2.22 fails for solvable Lie algebras: the module $F^2$ of $\mathfrak{b}_2$ has the invariant line $F e_1$ and no invariant complement. It also fails in characteristic $p$.

**Remark 2.2.23 (characteristic $p$).** Lie's theorem and Weyl's theorem need characteristic 0. Let $F$ have characteristic $p > 0$ and let $V = F[t]/(t^p)$. The maps $x = d/dt$ and $y = $ (multiplication by $t$) are well defined on $V$, because $d(t^p)/dt = p t^{p-1} = 0$, and $[x, y] = 1$. So $x$, $y$ and $1$ span a nilpotent, hence solvable, Lie algebra of endomorphisms of $V$. A common eigenvector $v$ would satisfy $v = [x, y] v = 0$, so there is none. The proof of Lemma 2.2.8 breaks at the division by $n$, which is $p$ here. The Killing form of $\mathfrak{sl}_2$ is $4\, \mathrm{tr}(xy)$ in any characteristic, so it vanishes in characteristic 2, and $\mathfrak{sl}_2$ is nilpotent there. For these reasons the rest of the chapter works over a field of characteristic 0.
