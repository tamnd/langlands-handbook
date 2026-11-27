---
title: Principal series and the special representations
nodes: []
sources: [BH06, JL70]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Principal series and the special representations

This section finds the constituents of each principal series $\chi_1 \times \chi_2$. If $\chi_1 \chi_2^{-1} \ne |\cdot|^{\pm 1}$, it is irreducible. Otherwise it has length two, with a character and a twist of the Steinberg representation as constituents, the special representations of Jacquet and Langlands.

### The irreducibility criterion

**Theorem 3.2.1 (irreducibility of the principal series).** Let $\chi_1, \chi_2$ be characters of $K^\times$ and $V = \chi_1 \times \chi_2$.
1. $V$ is irreducible if and only if $\chi_1 \chi_2^{-1} \ne |\cdot|^{\pm 1}$.
2. If $\chi_1 \chi_2^{-1} = |\cdot|^{-1}$, write $\chi_1 = \eta |\cdot|^{-1/2}$ and $\chi_2 = \eta |\cdot|^{1/2}$. Then the line of the function $\eta \circ \det$ is the only $G$-stable subspace of $V$ other than $0$ and $V$, and the quotient is irreducible and infinite-dimensional.
3. If $\chi_1 \chi_2^{-1} = |\cdot|$, write $\chi_1 = \eta |\cdot|^{1/2}$ and $\chi_2 = \eta |\cdot|^{-1/2}$. Then $V$ has a unique $G$-stable subspace other than $0$ and $V$. It has codimension one, it is irreducible and infinite-dimensional, and the quotient is $\eta \circ \det$.

Lean: `Langlands.normPrincipalSeries_isIrreducible_iff` for part 1. For the uniqueness in parts 2 and 3, `Langlands.normPrincipalSeries_existsUnique_stable_of_eq_mul` and `Langlands.normPrincipalSeries_existsUnique_stable`. The irreducible constituents are `Langlands.steinbergQuotient`, with `Langlands.steinbergQuotient_isIrreducible`, and `Langlands.steinbergSub`, with `Langlands.steinbergSub_isIrreducible`. In Lean the hypotheses read $\chi_2 = \chi_1 |\cdot|$ for part 2 and $\chi_1 = \chi_2 |\cdot|$ for part 3.

*Proof.* We first show that $V$ is reducible in the two cases of parts 2 and 3. In part 2, the function $f = \eta \circ \det$ lies in $V$. Indeed, for $b = \left(\begin{smallmatrix} a & x \\ 0 & d \end{smallmatrix}\right)$,
$$\chi_1(a) \chi_2(d) \left|\frac{a}{d}\right|^{1/2} = \eta(a) |a|^{-1/2} \eta(d) |d|^{1/2} |a|^{1/2} |d|^{-1/2} = \eta(a d),$$
so $f(b g) = \eta(\det b) f(g)$ has the right transformation law. Since $(g \cdot f)(h) = \eta(\det h g) = \eta(\det g) f(h)$, the line of $f$ is $G$-stable. For $\eta = 1$ this is the line of the constants in Example 3.1.5. In part 3, the contragredient of $V$ is $\chi_1^{-1} \times \chi_2^{-1}$ by Proposition 3.1.4, and $\chi_1^{-1} = \eta^{-1} |\cdot|^{-1/2}$, $\chi_2^{-1} = \eta^{-1} |\cdot|^{1/2}$. So the contragredient is in the case of part 2, and it contains the line of $\eta^{-1} \circ \det$. The annihilator of this line in $V$ is a $G$-stable subspace of codimension one, and $G$ acts on the quotient by $\eta \circ \det$. So $V$ is reducible.

For the converse and the uniqueness statements we give the main steps. They are Steps 1 to 9 of the proof of Volume 6, Theorem 1.5.1, and [BH06], Chapter 3 has another proof. Let $W \ne 0$ be a $G$-stable subspace and $V_w$ the subspace of Theorem 3.1.8, which is $C_c^\infty(K)$ as a representation of $N$. If $W \cap V_w \ne 0$, a Fourier argument shows that $W$ contains $V(N)$, so $SL_2(K)$ acts trivially on $V / W$, and the action of $\mathrm{diag}(a, a^{-1})$ on $r_B(V)$ shows that $W = V$ unless $\chi_1 \chi_2^{-1} = |\cdot|$. If $W \cap V_w = 0$, then $N$, hence $SL_2(K)$, fixes $W$ pointwise, $W$ is the line of a character, and $\chi_1 \chi_2^{-1} = |\cdot|^{-1}$. $\square$

The Lean proof follows these steps, with sums over the cosets of $\mathfrak{p}^m / \mathfrak{p}^{m+1}$ in place of the Fourier transform.

**Example 3.2.2 (unramified principal series).** Let $\chi_1, \chi_2$ be unramified with $z_i = \chi_i(\varpi)$. Then $\chi_1 \chi_2^{-1} = |\cdot|^{\pm 1}$ if and only if $z_1 / z_2 = q^{\mp 1}$. So the unramified principal series is irreducible unless $z_1 / z_2 \in \{q, q^{-1}\}$. If $z_1, z_2$ have absolute value one, as the Ramanujan conjecture predicts for the local components of a cusp form, then $|z_1 / z_2| = 1 \ne q^{\pm 1}$, and $\chi_1 \times \chi_2$ is irreducible.

### Isomorphisms between principal series

**Proposition 3.2.3 (isomorphism classes).** Let $\chi_1 \times \chi_2$ be irreducible. Then $\chi_1 \times \chi_2 \cong \chi_1' \times \chi_2'$ if and only if $(\chi_1', \chi_2')$ is $(\chi_1, \chi_2)$ or $(\chi_2, \chi_1)$. In particular $\chi_1 \times \chi_2 \cong \chi_2 \times \chi_1$.

Lean: `Langlands.normPrincipalSeries_iso_iff`.

*Proof.* The "only if" is Corollary 3.1.9. For the "if", we may assume $\chi_1 \ne \chi_2$. By Theorem 3.1.8, $r_B(\chi_1 \times \chi_2) \cong \chi \oplus \chi^w$, so there is a nonzero map of representations of $T$ from $r_B(\chi_1 \times \chi_2)$ onto $\chi^w$. By Theorem 3.1.7 it gives a nonzero map $\Phi : \chi_1 \times \chi_2 \to \chi_2 \times \chi_1$. The criterion of Theorem 3.2.1 is symmetric in $\chi_1$ and $\chi_2$, so $\chi_2 \times \chi_1$ is irreducible too. The kernel and the image of $\Phi$ are $G$-stable, so $\Phi$ is injective and onto. $\square$

The map $\Phi$ is the *intertwining operator* $M(w) f(g) = \int_K f(w \, n(x) \, g) \, dx$, which converges for $|\chi_1 \chi_2^{-1}(\varpi)| < 1$ and continues analytically ([Bum97], Chapter 4, and Volume 6, Proposition 1.5.2). When $\chi_1 \times \chi_2$ is reducible, $\chi_2 \times \chi_1$ has the same two constituents in the opposite order.

### The Steinberg representation and the special representations

**Definition 3.2.4 (Steinberg and special representations).** The *Steinberg representation* $\mathrm{St}$ is the quotient of $|\cdot|^{-1/2} \times |\cdot|^{1/2} = C^\infty(\mathbb{P}^1(K))$ by the constant functions. For a character $\eta$ of $K^\times$ the *twisted Steinberg representation* is $\eta \mathrm{St} = \mathrm{St} \otimes \eta$. These representations are the *special representations* of Jacquet and Langlands. We write $\pi(\chi_1, \chi_2)$ for $\chi_1 \times \chi_2$ when it is irreducible.

Lean: `Langlands.steinbergQuotient` and `Langlands.steinbergSub`, for the quotient of part 2 and the subrepresentation of part 3 of Theorem 3.2.1, and `Langlands.normSteinbergSub` for the subspace of part 3.

Jacquet and Langlands write $\sigma(\chi_1, \chi_2)$ for a special representation. The order of the pair varies between sources, so we use only $\eta \mathrm{St}$.

**Proposition 3.2.5 (properties of the special representations).** Let $\eta$ be a character of $K^\times$.
1. $\eta \mathrm{St}$ is irreducible and infinite-dimensional, and its central character is $\eta^2$.
2. $\eta \mathrm{St}$ is isomorphic to the irreducible subrepresentation of $\eta |\cdot|^{1/2} \times \eta |\cdot|^{-1/2}$ of Theorem 3.2.1, part 3.
3. $r_B(\eta \mathrm{St}) \cong \eta |\cdot|^{1/2} \otimes \eta |\cdot|^{-1/2}$.
4. $\eta \mathrm{St} \cong \eta' \mathrm{St}$ if and only if $\eta = \eta'$.
5. $\eta \mathrm{St}$ is not isomorphic to a character or to a principal series.
6. The contragredient of $\eta \mathrm{St}$ is $\eta^{-1} \mathrm{St}$.

Lean: `Langlands.steinbergQuotient_isIrreducible`, `Langlands.two_le_rank_steinbergQuotient` and `Langlands.steinbergQuotient_not_iso_charRep`. These give part 1 without the central character, and the part of part 5 about characters. Lean does not prove part 2, that is, that `Langlands.steinbergQuotient` and `Langlands.steinbergSub` are isomorphic. The other parts are not stated yet.

*Proof.* Part 1 is Theorem 3.2.1, part 2, for $\eta = 1$, twisted by $\eta$. The center acts trivially on $C^\infty(\mathbb{P}^1(K))$, so $\mathrm{St}$ has trivial central character, and the twist by $\eta$ multiplies it by $\eta^2$.

For part 2, let $V' = \eta |\cdot|^{-1/2} \times \eta |\cdot|^{1/2}$, with the line $L$ of $\eta \circ \det$ and $V'/L \cong \eta \mathrm{St}$, and let $V = \eta |\cdot|^{1/2} \times \eta |\cdot|^{-1/2}$, with its subrepresentation $S$ of codimension one. By Theorems 3.1.8 and 3.1.7 there is a nonzero map $\Phi : V' \to V$. Its image is $S$ or $V$, and neither has a $G$-stable line, so $\Phi$ is not injective and its kernel is $L$. So $\Phi$ maps $V'/L$ onto an irreducible infinite-dimensional subspace, which is $S$.

For part 3, apply $r_B$ to $0 \to S \to V \to \eta \circ \det \to 0$. The torus acts on $r_B(\eta \circ \det)$ by $\eta(a d) |a / d|^{-1/2}$, the character $\eta |\cdot|^{-1/2} \otimes \eta |\cdot|^{1/2}$, so by Theorem 3.1.8, $r_B(S)$ is the other one. Part 4 follows. For part 5, characters have finite dimension, and irreducible principal series have $\dim r_B = 2$. For part 6, the contragredient sequence is $0 \to \eta^{-1} \circ \det \to \eta^{-1} |\cdot|^{-1/2} \times \eta^{-1} |\cdot|^{1/2} \to S^\vee \to 0$ by Proposition 3.1.4. $\square$

By Volume 6, Proposition 1.5.4, the matrix coefficients of $\mathrm{St}$ are square integrable modulo the center but not compactly supported modulo the center, so $\eta \mathrm{St}$ is essentially square integrable and not supercuspidal. For fixed vectors we need the congruence subgroups. For $n \ge 0$ let
$$K_0(\mathfrak{p}^n) = \left\{ \begin{pmatrix} a & b \\ c & d \end{pmatrix} \in K_0 : c \in \mathfrak{p}^n \right\}, \qquad K_1(\mathfrak{p}^n) = \left\{ \begin{pmatrix} a & b \\ c & d \end{pmatrix} \in K_0(\mathfrak{p}^n) : d \in 1 + \mathfrak{p}^n \right\},$$
with $K_0(\mathfrak{p}^0) = K_1(\mathfrak{p}^0) = K_0$. The group $K_0(\mathfrak{p})$ is the Iwahori subgroup $I$. For $K = \mathbb{Q}_p$ these are the local components at $p$ of the adelic groups $K_0(N)$ and $K_1(N)$ of Chapter 1, for $p^n \parallel N$.

**Example 3.2.6 (fixed vectors of the Steinberg representation).** We show that $\dim \mathrm{St}^{K_0(\mathfrak{p}^n)} = \dim \mathrm{St}^{K_1(\mathfrak{p}^n)} = n$ for $n \ge 0$. By Example 3.1.5, a $J$-fixed vector of $C^\infty(\mathbb{P}^1(K))$ is a function constant on the $J$-orbits of the row vectors $[c : d]$, normalized with $c, d \in \mathcal{O}$ and one of them a unit. For $n \ge 1$ and $k \in K_1(\mathfrak{p}^n)$, $[c : d] k = [c \alpha + d \gamma : c \beta + d \delta]$ with $\alpha \in \mathcal{O}^\times$ and $\gamma \in \mathfrak{p}^n$, so $i = \min(v(c), n)$ is constant on orbits. Each value $0 \le i \le n$ is one orbit: $n(-d)$ moves $[1 : d]$ to $[1 : 0]$, $\mathrm{diag}(u^{-1}, 1)$ moves $[u \varpi^i : 1]$ to $[\varpi^i : 1]$, and $\bar n(-c)$ moves $[c : 1]$ to $[0 : 1]$ if $v(c) \ge n$. The same holds for $K_0(\mathfrak{p}^n)$. The $n + 1$ orbits are open, so $\dim C^\infty(\mathbb{P}^1(K))^{J} = n + 1$, and the exactness of $J$-invariants (Volume 6, Proposition 1.2.3) gives $\dim \mathrm{St}^J = n$. For $n = 0$, $K_0$ is transitive and $\mathrm{St}^{K_0} = 0$. In Section 3.6 this is $n - c + 1$ with $c = 1$.

### Unitary representations and the local Ramanujan conjecture

A representation is *unitary* if it has a positive definite $G$-invariant Hermitian form. The local components of a cuspidal automorphic representation are unitary, by the Petersson inner product (Chapter 2).

**Remark 3.2.7 (the unitary irreducible representations).** The principal series $\chi_1 \times \chi_2$ with $\chi_1, \chi_2$ unitary are unitary (Volume 6, Proposition 1.3.4), and they are the *tempered* principal series. The *complementary series* $\chi |\cdot|^s \times \chi |\cdot|^{-s}$ with $\chi$ unitary and $0 < s < 1/2$ are unitary for an inner product built from $M(w)$. With the $\eta \mathrm{St}$ for unitary $\eta$, the supercuspidal representations with unitary central character and the unitary characters, these are all the irreducible unitary representations ([Bum97], Chapter 4). The local Ramanujan conjecture for a cuspidal $\pi$ says that no $\pi_p$ is in the complementary series. For unramified $\pi_p$ it says $|z_1| = |z_2| = 1$. For holomorphic newforms this is Deligne's theorem (Volume 4).

**Example 3.2.8 (elliptic curves).** Let $E / \mathbb{Q}$ have conductor $N$ and let $\pi$ be the automorphic representation of its newform (Chapter 4). If $p \nmid N$, then $\pi_p$ is an unramified principal series with $\chi_1(p) + \chi_2(p) = a_p(E) / \sqrt p$. If $p \parallel N$, then $\pi_p = \eta \mathrm{St}$ with $\eta$ unramified and $\eta(p) = a_p(E) = \pm 1$, the sign of split or nonsplit reduction. Section 3.6 proves the local half of the second statement.
