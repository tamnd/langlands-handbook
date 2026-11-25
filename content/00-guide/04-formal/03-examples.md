---
title: Two errors that the checks find
nodes: [LGAV7YV6K6, LGDD6VVKSR]
sources: [Ser67]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Two errors that the checks find

### The uniformizer in local reciprocity

The statement of local reciprocity in Chapter 2 has two conditions: a uniformizer goes to a geometric Frobenius, and the map has the right kernel on each finite abelian extension. A first attempt at the statement can omit the first condition, because the second one looks like the content of the theorem. The check F3 shows that the first condition is needed for the uniqueness.

**Proposition 4.3.1 (the uniformizer condition is needed).** Let $K$ be a nonarchimedean local field. Call an isomorphism of topological groups $r : K^\times \to W_K^{ab}$ an *unnormalized Artin map* if, for each finite abelian extension $L$ of $K$, the composite $K^\times \to \mathrm{Gal}(L/K)$ is surjective with kernel $N_{L/K}(L^\times)$. Then there is not exactly one unnormalized Artin map.

Lean: `Langlands.Fidelity.not_existsUnique_unnormalized`

*Proof.* Suppose that $r$ is the only unnormalized Artin map. The map $r'(x) = r(x)^{-1}$ is an isomorphism of topological groups, because $W_K^{ab}$ is abelian. Its composite with $W_K^{ab} \to \mathrm{Gal}(L/K)$ is surjective, and it has the same kernel as the composite for $r$. Thus $r'$ is an unnormalized Artin map, and $r' = r$. Then $r(x)^2 = 1$ for all $x$, and since $r$ is injective, $x^2 = 1$ for all $x \in K^\times$. This is false for a uniformizer $\varpi$, since $\varpi^2$ has valuation 2. $\square$

The proof does not use the existence of an Artin map. If one exists, then the inverse map is a second one. The condition on the uniformizer removes the second map, because $r'(\varpi)$ is the class of an arithmetic Frobenius. Thus the condition does more than fix a convention: without it the statement $\exists!$ is false. The statement of the project keeps the condition, and the Lean statement `Langlands.LocalReciprocityGL1` asserts the uniqueness with it.

Node: LGAV7YV6K6 · Lean: `Langlands.LocalReciprocityGL1`

### A false statement of the modularity theorem

The repository formal-conjectures of Google DeepMind collects Lean statements of open and solved problems. It contains a statement of the modularity theorem for elliptic curves over $\mathbb{Q}$. The project ports it word for word into `Langlands/Ported/FormalConjectures/`, with the source commit, and compares it with its own statement. The comparison showed that the statement is false.

The statement asks, for each elliptic curve $E$ over $\mathbb{Q}$, for an $N \ge 1$ and a cusp form $f$ of weight 2 on $\Gamma_0(N)$ that is a normalized eigenform and whose coefficients $a_p$ agree with those of $E$ for $p \nmid N$. The coefficients of $f$ are defined by the $q$-expansion with period $N$, that is, in the variable $q_N = e^{2 \pi i \tau / N}$. But the cusp $\infty$ of $\Gamma_0(N)$ has width 1 (Chapter 3). The form $f$ is a series in $q = q_N^N$, so its coefficient of $q_N^1$ is 0 for $N \ge 2$. For $N = 1$ there is no nonzero cusp form of weight 2. Thus the condition $a_1(f) = 1$ in the definition of a normalized eigenform fails for every $f$.

**Counterexample 4.3.2 (the modularity statement of formal-conjectures).** The statement `modularity_conjecture` of formal-conjectures is false. Its negation is a Lean theorem.

Node: LGDD6VVKSR · Lean: `Langlands.Ported.FormalConjectures.ModularityConjecture.modularity_conjecture`

The node has the kind counterexample. The Lean name in its line is the name of the false statement, and the status in the line is the status that the tool computes for that name. The refutation is the theorem of the next paragraph.

The proof of the negation is the Lean theorem `Langlands.Bridge.not_modularity_conjecture`. It applies the statement to the curve $y^2 = x^3 - x$ and uses two lemmas: the coefficient of $q_N^1$ is 0 for $N \ge 2$ (Lean: `Langlands.Bridge.coeff_one_qExpansion_eq_zero`), and a cusp form of weight 2 for $SL_2(\mathbb{Z})$ is zero (Lean: `Langlands.Bridge.cuspForm_weight_two_eq_zero_of_eq`). In fact the proof shows more: no elliptic curve over $\mathbb{Q}$ satisfies the condition of the statement (Lean: `Langlands.Bridge.not_modularityConjecture`).

The error is one of normalization, not of mathematics. A proof of the theorem of Breuil, Conrad, Diamond and Taylor in Lean would not prove this statement, because the statement is false. The statement of the project reads the coefficients with width 1 (Lean: `Langlands.qCoeff`), and it is the one that Chapter 2 gives. The check F2 for the curve $X_0(11)$ compares it with the expansion $q - 2q^2 - q^3 + \cdots$ of Chapter 2.

Two lessons follow. The first one is that a statement that nobody has tried to prove or to refute can be false without anybody noticing it. The second one is that a check with a known instance, here the curve $X_0(11)$ or the coefficient $a_1 = 1$, finds such errors at once.
