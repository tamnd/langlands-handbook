---
title: Compactness of the norm one idele classes
nodes: []
sources: [CF67]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Compactness of the norm one idele classes

This section proves that $C_F^1$ is compact. It deduces the finiteness of the class number, the unit theorem and the strong approximation theorem. We follow [CF67], Chapter II, Sections 15 to 18. The inputs are Theorem 3.3.3 and Lemma 1.3.8. The proofs do not use the geometry of numbers of Section 1.3 beyond these two facts.

### The adelic Minkowski lemma

**Theorem 3.5.1 (the adelic Minkowski lemma).** Let $c_F = (2/\pi)^{r_2} |d_F|^{1/2}$. For each idele $a$ with $|a|_\mathbb{A} > c_F$, there is $x \in F^\times$ with $|x|_v \le |a_v|_v$ for all places $v$.

Lean: not stated yet

*Proof.* We use the standard measure $\mu$ on $\mathbb{A}_F$. Let $W$ be the set of adeles $y$ with $|y_v| \le 1/2$ in the usual absolute value at the infinite places $v$, and $y_v \in \mathcal{O}_v$ at the finite places. A real factor of $W$ is an interval of length 1. A complex factor is a disc of radius $1/2$, with measure $2 \cdot \pi/4 = \pi/2$ for $2\,dx\,dy$. The finite factors have measure 1. Thus $\mu(W) = (\pi/2)^{r_2}$. Multiplication by $a$ multiplies $\mu$ by $|a|_\mathbb{A}$, so
$$\mu(aW) = |a|_\mathbb{A} (\pi/2)^{r_2} > |d_F|^{1/2} = \mathrm{vol}(\mathbb{A}_F / F),$$
by Theorem 3.3.3. Thus the projection $aW \to \mathbb{A}_F / F$ is not injective, by the argument of Theorem 1.3.2: if it were injective, $\mu(aW)$ would be at most the volume of the quotient. So there are $w_1 \ne w_2$ in $W$ with $x = a w_1 - a w_2 \in F$, and $x \ne 0$. At an infinite place $v$, $|w_1 - w_2| \le 1$ in the usual absolute value, so $|x|_v \le |a_v|_v$, also for complex $v$ where both sides are squared. At a finite place, $w_1 - w_2 \in \mathcal{O}_v$, so $|x|_v \le |a_v|_v$. $\square$

The constant $c_F$ is the Minkowski bound $M_F$ of Theorem 1.3.5. This is not a coincidence: for an idele with $a_v = 1$ at the infinite places, the lemma is the statement of Theorem 1.3.4 with a weaker constant.

### Compactness

**Theorem 3.5.2 (compactness of the norm one idele classes).** The group $C_F^1 = J_F^1 / F^\times$ is compact.

Lean: not stated yet

*Proof.* Fix an idele $b$ with $|b|_\mathbb{A} > c_F$. Let $a \in J_F^1$. Then $|a^{-1} b|_\mathbb{A} = |b|_\mathbb{A} > c_F$, so Theorem 3.5.1 gives $x \in F^\times$ with $|x|_v \le |a_v^{-1} b_v|_v$ for all $v$. The idele $y = x a$ lies in $J_F^1$ and satisfies $|y_v|_v \le |b_v|_v$ for all $v$. Thus each class of $C_F^1$ has a representative in
$$B = \{y \in J_F^1 : |y_v|_v \le |b_v|_v \text{ for all } v\}.$$
It suffices to show that $B$ is compact in $J_F$. Let $y \in B$. For each $v$,
$$|y_v|_v = \prod_{w \ne v} |y_w|_w^{-1} \ge \prod_{w \ne v} |b_w|_w^{-1} = |b_v|_v / |b|_\mathbb{A}.$$
Let $S$ be the finite set of places that are infinite, or have $|b_v|_v \ne 1$, or have $N(\mathfrak{p}_v) \le |b|_\mathbb{A}$. For finite $v \notin S$, we have $1 \ge |y_v|_v \ge 1/|b|_\mathbb{A} > 1/N(\mathfrak{p}_v)$, and $|y_v|_v$ is a power of $N(\mathfrak{p}_v)$, so $|y_v|_v = 1$. For $v \in S$, $y_v$ lies in the set $\{|b_v|_v / |b|_\mathbb{A} \le |y_v|_v \le |b_v|_v\}$, which is compact in $F_v^\times$. Thus $B$ is a closed subset of the set
$$\prod_{v \in S} \{|b_v|_v / |b|_\mathbb{A} \le |y_v|_v \le |b_v|_v\} \times \prod_{v \notin S} \mathcal{O}_v^\times,$$
which is compact in $J_F$ by Proposition 3.1.3. The set $B$ is closed, because $J_F^1$ is closed and the conditions $|y_v|_v \le |b_v|_v$ are closed. So $B$ is compact, and $C_F^1$ is the image of $B$ under the continuous projection. $\square$

The converse also holds. If $\mathrm{Cl}_F$ is finite and $\mathcal{O}_F^\times$ has the rank of the unit theorem, then the exact sequence of Theorem 3.4.7 shows that $C_F^1$ is compact (Exercise 6 of Section 3.6). Thus Theorem 3.5.2 is equivalent to the two finiteness theorems of Chapter 1 together.

### The finiteness theorems again

**Corollary 3.5.3 (finiteness of the class number).** The class group $\mathrm{Cl}_F$ is finite.

Lean: `NumberField.RingOfIntegers.instFintypeClassGroup`, from Mathlib

*Proof.* The map $\iota$ of Theorem 3.4.7 is surjective on $J_F^1$: an idele with given finite components can be multiplied at one infinite place by a positive real number so that its norm is 1, and this does not change $\iota$. Thus $\mathrm{Cl}_F$ is a quotient of $C_F^1$ by the image of $J_F^1 \cap U_F$. This subgroup is open, because $U_F$ is open in $J_F$. A compact group has only finitely many cosets of an open subgroup. $\square$

**Corollary 3.5.4 (the unit theorem).** The group $\mathcal{O}_F^\times$ is the product of the finite group $\mu(F)$ and a free abelian group of rank $r_1 + r_2 - 1$.

Lean: `NumberField.Units.exist_unique_eq_mul_prod`, from Mathlib

*Proof.* Let $U_F^1 = U_F \cap J_F^1$. The image of $U_F^1$ in $C_F^1$ is $U_F^1 F^\times / F^\times \cong U_F^1 / \mathcal{O}_F^\times$, by Theorem 3.4.7. The subgroup $U_F^1 F^\times$ of $J_F^1$ is open, so it is closed, and its image in $C_F^1$ is compact. Thus $U_F^1 / \mathcal{O}_F^\times$ is compact. Let $H = \{t \in \mathbb{R}^{r_1 + r_2} : \sum_v t_v = 0\}$, and define
$$\lambda : U_F^1 \to H, \qquad \lambda(y) = (\log |y_v|_v)_{v \mid \infty}.$$
The sum of the coordinates is $\log |y|_\mathbb{A} = 0$, because $|y_v|_v = 1$ at the finite places. The map is a continuous surjective homomorphism, and it is open, because it has continuous local sections. Its kernel is compact: it is the product of the groups $\{|z|_v = 1\}$ at the infinite places and of the $\mathcal{O}_v^\times$. Thus $H / \lambda(\mathcal{O}_F^\times)$ is a continuous image of the compact group $U_F^1 / \mathcal{O}_F^\times$, so it is compact. The group $\lambda(\mathcal{O}_F^\times)$ is discrete in $H$, because only finitely many units have $|\log|\varepsilon|_v| \le 1$ for all $v \mid \infty$, by Lemma 1.3.8. A discrete subgroup of $H$ with compact quotient is a complete lattice, so $\lambda(\mathcal{O}_F^\times) \cong \mathbb{Z}^{r_1 + r_2 - 1}$. The kernel of $\lambda$ on $\mathcal{O}_F^\times$ is finite by Lemma 1.3.8, so it is $\mu(F)$. A finitely generated abelian group with torsion $\mu(F)$ and free quotient of rank $r$ is the product of $\mu(F)$ and $\mathbb{Z}^r$. $\square$

The proofs of this section give no bound for the class number and no information on the regulator. Section 1.3 gives the bound. The adelic proofs have another advantage: they work for the $S$-units and the $S$-class groups, and for global function fields, with the same arguments.

### Strong approximation

**Theorem 3.5.5 (strong approximation).** Let $v_0$ be a place of $F$, and let $\mathbb{A}_F^{v_0} = \prod'_{v \ne v_0} (F_v, \mathcal{O}_v)$ be the adeles without the component at $v_0$. Then $F$ is dense in $\mathbb{A}_F^{v_0}$. That is, for each finite set $S$ of places not containing $v_0$, each family $a_v \in F_v$ for $v \in S$, and each $\varepsilon > 0$, there is $x \in F$ with $|x - a_v|_v < \varepsilon$ for $v \in S$ and $|x|_v \le 1$ for all finite $v \notin S \cup \{v_0\}$.

Lean: not stated yet

*Proof.* Let $P \subset F_\infty$ be a bounded fundamental domain for the lattice $\mathcal{O}_F$, for example a fundamental parallelotope. By Theorem 3.2.5, $\mathbb{A}_F = F + (P \times \hat{\mathcal{O}}_F)$. Thus there is $C \ge 1$ with $\mathbb{A}_F = F + W_C$, where $W_C$ is the set of adeles with $|w_v|_v \le C$ at the infinite places and $w_v \in \mathcal{O}_v$ at the finite places.

Let $a \in \mathbb{A}_F$ have the components $a_v$ for $v \in S$, and the component 0 elsewhere. Let $\delta > 0$ be small. Choose an idele $b$ with $|b_v|_v \le \delta$ for $v \in S$, $b_v = 1$ for $v \notin S \cup \{v_0\}$, and $|b_{v_0}|_{v_0}$ so large that $|b|_\mathbb{A} > c_F$. By Theorem 3.5.1 there is $y \in F^\times$ with $|y|_v \le |b_v|_v$ for all $v$. Write $y^{-1} a = z + w$ with $z \in F$ and $w \in W_C$. Then $x = y z \in F$ and $a - x = y w$. For $v \in S$ finite, $|a_v - x|_v \le |y|_v \le \delta$. For $v \in S$ infinite, $|a_v - x|_v \le C \delta$. For finite $v \notin S \cup \{v_0\}$, $|x|_v = |y w_v|_v \le 1$. With $\delta < \varepsilon / C$ this gives the claim. $\square$

For $F = \mathbb{Q}$ and $v_0 = \infty$, the theorem is the Chinese remainder theorem. For $v_0 = p$, it says that $\mathbb{Z}[1/p]$ is dense in $\mathbb{R} \times \prod_{\ell \ne p} \mathbb{Z}_\ell$. The theorem fails if no place is omitted, because $F$ is discrete in $\mathbb{A}_F$. The same statement holds for the adelic points of simply connected semisimple groups, by a theorem of Kneser and Platonov. For $GL_n$ it fails, because of the determinant, and this failure is one reason why the class group appears in the theory of automorphic forms on $GL_n$.
