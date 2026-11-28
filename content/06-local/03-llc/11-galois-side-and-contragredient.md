---
title: The Galois side of the tame parametrization and the contragredient of a type
nodes: []
sources: [BH06, Ser79, Tat79]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## The Galois side of the tame parametrization and the contragredient of a type

Remark 3.11.36 lists what is still open for $GL_2$ with $p \ne 2$. This section removes two items from that list. The first is input 4 of Definition 3.10.27, `TypeRepContragredient`: the contragredient of the representation of a tame datum is the representation of a tame datum for the inverse character. We prove it in full. The second is input 3 of Definition 3.9.30, `GaloisTameParametrization`: each irreducible Weil-Deligne representation of dimension 2 is $\sigma(L, \xi)$ for an admissible pair, and the field $L$ is determined by the parameter. We prove it from eight named facts on the Weil group, and we prove three of these facts. Five facts remain open, and they are standard results of [Ser79] and [Tat79]. The Lean files are `Langlands/Local/TypeContragredient.lean`, `Langlands/Local/GaloisTameParam.lean` and `Langlands/Local/WeilGroupFacts.lean`.

The two halves are independent. The contragredient is a statement on the representation side, and its proof uses only compact induction, the intertwining of a type and admissibility. The parametrization is a statement on the Galois side, and its proof uses Clifford theory in dimension 2 and the structure of the inertia group. The condition $p \ne 2$ enters only on the Galois side, at two places: a finite $p$-group in $GL_2(\mathbb{C})$ has a common eigenvector, and each principal unit of a quadratic extension has a unique principal square root. Example 3.12.14 and Exercise 41 show that both statements fail for $p = 2$.

We keep the notation of Sections 3.9 to 3.11. The field $K$ is a nonarchimedean local field with residue field of characteristic $p$ and $q$ elements. For a separable quadratic extension $L/K$ inside $\bar K$, $\tau$ is the nontrivial automorphism of $L/K$, $N = N_{L/K}$ is the norm, and $U^m_L$ is the filtration of $\mathcal{O}_L^\times$. The Weil group of $K$ is $W_K$, the inertia subgroup is $I_K$, and $d : W_K \to \mathbb{Z}$ is the degree map, so that $I_K = \ker d$ and a Frobenius element has degree 1. The Weil group $W_L$ is the subgroup of the elements of $W_K$ that fix $L$. It has index 2, so it is normal. We fix an element $s \in W_K$ outside $W_L$, the element `outElt` of the library. For a character $\xi$ of $L^\times$ we write $\xi_W = \xi \circ \mathrm{art}_L^{-1}$ for the character of $W_L$ that it defines, and $\sigma(L, \xi) = \mathrm{Ind}_{W_L}^{W_K} \xi_W$ with $N = 0$, the parameter `tameParam` of Section 3.9.

### The contragredient of a compact induction

Let $G$ be a locally profinite group. For a smooth representation $(\pi, V)$ of $G$ the contragredient $(\pi^\vee, V^\vee)$ is the space of the linear forms $\lambda$ on $V$ whose stabilizer is open, with $(\pi^\vee(g)\lambda)(f) = \lambda(\pi(g^{-1}) f)$. The first lemma says that this construction respects isomorphisms. It is formal, but we need it to transport the theorem from one model of a representation to another.

**Lemma 3.12.1 (contragredients of isomorphic representations).** Let $\phi : V \to V'$ be a linear map with $\phi \circ \pi(g) = \pi'(g) \circ \phi$ for all $g$. If $\lambda \in V'^\vee$, then $\lambda \circ \phi \in V^\vee$. If $\phi$ is an isomorphism of representations, then $\lambda \mapsto \lambda \circ \phi$ is an isomorphism $\pi'^\vee \to \pi^\vee$.

Lean: `Langlands.LocalGL2.comp_mem_smoothVectors`, `Langlands.LocalGL2.iso_contragredient_of_iso`

*Proof.* Let $U$ be an open subgroup that fixes $\lambda$. For $u \in U$ and $f \in V$, $(\lambda \circ \phi)(\pi(u^{-1}) f) = \lambda(\pi'(u^{-1}) \phi(f)) = \lambda(\phi(f))$, so $U$ fixes $\lambda \circ \phi$. The same computation shows that $\lambda \mapsto \lambda \circ \phi$ commutes with the actions. If $\phi$ is invertible, then $\mu \mapsto \mu \circ \phi^{-1}$ is the inverse map, and it preserves smooth vectors by the first part applied to $\phi^{-1}$. $\square$

Now let $J$ be an open subgroup of $G$ and $\Lambda$ a character of $J$ with open kernel. As in Section 3.10, $V = \mathrm{c\text{-}Ind}_J^G \Lambda$ is the space of the functions $f : G \to \mathbb{C}$ with $f(jx) = \Lambda(j) f(x)$, invariant on the right under an open subgroup, and with support a finite union of cosets $Jx$. The group acts by $(\rho(g) f)(x) = f(xg)$. The basic vector $f_0$ has support $J$ and $f_0(j) = \Lambda(j)$. By Lemma 3.10.29, $\rho(j) f_0 = \Lambda(j) f_0$ for $j \in J$, the translates $\rho(g) f_0$ span $V$, and the form $f \mapsto f(1)$ is smooth.

The natural candidate for an isomorphism $V^\vee \to \mathrm{c\text{-}Ind}_J^G \Lambda^{-1}$ is the matrix coefficient against $f_0$.

**Definition 3.12.2 (the function of a smooth form).** For $\lambda \in V^\vee$ let $f_\lambda : G \to \mathbb{C}$ be the function
$$f_\lambda(x) = \lambda(\rho(x^{-1}) f_0).$$

Lean: `Langlands.LocalGL2.contraFun`, `Langlands.LocalGL2.contraVec`, `Langlands.LocalGL2.contraMap`

**Lemma 3.12.3 (the two transformation laws).** Let $\lambda \in V^\vee$.
1. For $j \in J$ and $x \in G$, $f_\lambda(jx) = \Lambda(j)^{-1} f_\lambda(x)$.
2. For $u, x \in G$, $f_\lambda(xu) = f_{\pi^\vee(u) \lambda}(x)$, where $\pi^\vee$ is the contragredient action on $V^\vee$. In particular $f_\lambda$ is invariant on the right under the stabilizer of $\lambda$, which is open.

Lean: `Langlands.LocalGL2.contraFun_mul_left`, `Langlands.LocalGL2.contraFun_mul_right`

*Proof.* For part 1, $f_\lambda(jx) = \lambda(\rho(x^{-1}) \rho(j^{-1}) f_0) = \Lambda(j^{-1}) \lambda(\rho(x^{-1}) f_0)$, by the eigenvector property of $f_0$. For part 2, $f_\lambda(xu) = \lambda(\rho(u^{-1}) \rho(x^{-1}) f_0) = (\pi^\vee(u)\lambda)(\rho(x^{-1}) f_0)$. $\square$

So $f_\lambda$ has the left transformation law of $\mathrm{c\text{-}Ind}_J^G \Lambda^{-1}$ and is smooth. The real point is the support. In general a matrix coefficient of a compactly induced representation need not have compact support modulo $J$. Admissibility gives it.

**Lemma 3.12.4 (the support of $f_\lambda$).** Assume that each open subgroup of $G$ contains a compact open subgroup and that $V$ is admissible. Then for each $\lambda \in V^\vee$ the support of $f_\lambda$ is a finite union of cosets $Js$. So $f_\lambda \in \mathrm{c\text{-}Ind}_J^G \Lambda^{-1}$.

Lean: `Langlands.LocalGL2.exists_finset_contraFun`

*Proof.* Choose a compact open subgroup $K'$ inside the stabilizer of $\lambda$. Suppose that $f_\lambda(x) \ne 0$, and let $k \in K'$ with $j = x k x^{-1} \in J$. By Lemma 3.12.3,
$$f_\lambda(x) = f_\lambda(xk) = f_\lambda(jx) = \Lambda(j)^{-1} f_\lambda(x),$$
so $\Lambda(j) = 1$. Thus $\Lambda$ is trivial on $J \cap x K' x^{-1}$, which is the condition "$x$ is admissible for $K'$" of Lemma 3.10.31. Since $V$ is admissible, $V^{K'}$ has finite dimension, and Lemma 3.10.31, part 2, gives a finite set $T$ with $x \in J t K'$ for some $t \in T$. So the support of $f_\lambda$ lies in the finite union of the double cosets $J t K'$, $t \in T$.

It remains to see that each double coset $J t K'$ is a finite union of cosets of $J$. The cosets $J t k$ and $J t k'$ with $k, k' \in K'$ agree exactly when $k' k^{-1} \in K' \cap t^{-1} J t$. This group is open in $K'$, because $J$ is open, and an open subgroup of a compact group has finite index. So $J t K'$ is the union of the finitely many cosets $J t k$, with $k$ in a set of representatives of $(K' \cap t^{-1} J t) \backslash K'$. $\square$

**Theorem 3.12.5 (the contragredient of a compact induction).** Let $Z$ be a central subgroup of $G$ and let $J$ be an open subgroup that contains $Z$ and is compact modulo $Z$. Let $\Lambda$ be a character of $J$ with open kernel whose intertwining is $J$: if $g \in G$ intertwines $\Lambda$, then $g \in J$. Assume that each open subgroup of $G$ contains a compact open subgroup and that $V = \mathrm{c\text{-}Ind}_J^G \Lambda$ is admissible. Then $\lambda \mapsto f_\lambda$ is an isomorphism
$$(\mathrm{c\text{-}Ind}_J^G \Lambda)^\vee \cong \mathrm{c\text{-}Ind}_J^G \Lambda^{-1}.$$

Lean: `Langlands.LocalGL2.contragredient_cInd_iso`

This is the form of [BH06], 11.4 and 19.4, that the correspondence needs. The proof below uses only Lemma 3.12.4 and the irreducibility criterion.

*Proof.* Let $\Psi(\lambda) = f_\lambda$. By Lemma 3.12.4, $\Psi$ is a linear map $V^\vee \to V' = \mathrm{c\text{-}Ind}_J^G \Lambda^{-1}$. By Lemma 3.12.3, part 2, $\Psi(\pi^\vee(g)\lambda)(x) = f_\lambda(xg) = (\rho'(g) f_\lambda)(x)$, where $\rho'$ is the action on $V'$. So $\Psi$ is a map of representations.

The map $\Psi$ is injective. If $f_\lambda = 0$, then $\lambda$ vanishes on all the translates $\rho(x^{-1}) f_0$. These span $V$ by Lemma 3.10.29, so $\lambda = 0$.

The map $\Psi$ is not zero. Let $\lambda_1(f) = f(1)$. This form is smooth: for $u \in \ker \Lambda$, $(\pi^\vee(u)\lambda_1)(f) = f(u^{-1}) = \Lambda(u^{-1}) f(1) = f(1)$, and $\ker \Lambda$ is open. Then $f_{\lambda_1}(1) = f_0(1) = 1$.

The target $V'$ is irreducible. An element $g$ intertwines $\Lambda^{-1}$ exactly when $\Lambda^{-1}$ and $(\Lambda^{-1})^g$ agree on $J \cap g^{-1} J g$, that is when $\Lambda$ and $\Lambda^g$ agree there, that is when $g$ intertwines $\Lambda$. So the intertwining of $\Lambda^{-1}$ is also $J$, and Theorem 3.9.16 shows that $V'$ is irreducible. The image of $\Psi$ is a nonzero subrepresentation of $V'$, so it is $V'$. Thus $\Psi$ is bijective, and it is an isomorphism of representations. $\square$

The proof does not use the irreducibility of $V$ or of $V^\vee$, and it does not use any formal degree. The library proves the irreducibility of $V'$ by `isIrreducible_cInd` and the spanning property by `span_translate_cIndBasic`. For $GL_2(K)$ the extra hypotheses hold automatically.

**Corollary 3.12.6 (the case of $GL_2(K)$).** Let $G = GL_2(K)$ and let $J$ be an open subgroup that contains $K^\times$ and is compact modulo $K^\times$. Let $\Lambda$ be a character of $J$ with open kernel and intertwining $J$. Then $(\mathrm{c\text{-}Ind}_J^G \Lambda)^\vee \cong \mathrm{c\text{-}Ind}_J^G \Lambda^{-1}$.

Lean: `Langlands.LocalGL2.contragredient_cInd_iso_GL2`

*Proof.* The scalar matrices are central (`range_scalarGL_le_center`). Each open subgroup of $GL_2(K)$ contains a principal congruence subgroup $1 + \varpi^m M_2(\mathcal{O}_K)$, which is compact and open (`exists_isCompact_isOpen_le`). The representation $\mathrm{c\text{-}Ind}_J^G \Lambda$ is admissible by Theorem 3.11.12 (`isAdmissible_cInd_of_intertwining`). Theorem 3.12.5 applies. $\square$

**Example 3.12.7 (central characters).** In the situation of Corollary 3.12.6, the centre $K^\times$ acts on $\mathrm{c\text{-}Ind}_J^G \Lambda$ by $\Lambda|_{K^\times}$, since $(\rho(z) f)(x) = f(xz) = f(zx) = \Lambda(z) f(x)$. On the contragredient the centre then acts by $\Lambda|_{K^\times}^{-1}$, since $(\pi^\vee(z)\lambda)(f) = \lambda(\rho(z^{-1}) f) = \Lambda(z)^{-1}\lambda(f)$. This agrees with the central character $\Lambda^{-1}|_{K^\times}$ of $\mathrm{c\text{-}Ind}_J^G \Lambda^{-1}$, as Theorem 3.12.5 requires. For the representation $\pi_D$ of a tame datum $D$ for $(L/K, \xi)$, Proposition 3.10.23 gives central character $\xi|_{K^\times}$, and so $\pi_D^\vee$ has central character $\xi^{-1}|_{K^\times}$. This is the central character of a representation attached to $(L/K, \xi^{-1})$, and the next construction gives such a representation.

### The inverse tame datum

Recall Definition 3.10.22. A tame datum $D$ for a pair $(L/K, \xi)$ consists of a character $\psi$ of $K$ of level one, a chain order $\mathfrak{A}$ with a basis $v$ of $L$ adapted to it, a minimal character $\xi_0$ of $L^\times$ of odd level $n$, a minimal element $\alpha$ of level $n$ whose matrix lies in $\mathfrak{P}^{-n}$, a cuspidal type $\Lambda_0$ on $J_\alpha$ for $(\alpha, \xi_0)$, and a smooth character $\chi$ of $K^\times$ with $\xi = \xi_0 \chi_L$, where $\chi_L = \chi \circ N$. The representation is $\pi_D = \mathrm{c\text{-}Ind}_{J_\alpha}^G \Lambda$ with $\Lambda = \Lambda_0 \cdot (\chi \circ \det)$. We replace each character by its inverse and $\alpha$ by $-\alpha$.

**Lemma 3.12.8 (inverses of the pieces).** Let $E/F$ be a quadratic extension, as in Section 3.9.
1. A character $\xi$ of $E^\times$ and its inverse have the same level, and $\xi^{-1}$ is minimal when $\xi$ is minimal.
2. If $\alpha$ is a minimal element of level $n$, so is $-\alpha$. If the matrix of $\alpha$ in an adapted basis lies in $\mathfrak{P}^{-n}$, so does the matrix of $-\alpha$.
3. If $\Lambda_0$ is a cuspidal type for $(\alpha, \xi_0)$ on $J_\alpha$, then $\Lambda_0^{-1}$ is a cuspidal type for $(-\alpha, \xi_0^{-1})$ on $J_{-\alpha} = J_\alpha$.

Lean: `Langlands.LocalGL2.level_inv_char`, `Langlands.LocalGL2.IsMinimal.inv`, `Langlands.LocalGL2.IsMinimalElt.neg`, `Langlands.LocalGL2.inv_mem_cuspTypes`, `Langlands.LocalGL2.comp_inclusion_mem_cuspTypes`

*Proof.* Part 1. The level of $\xi$ is the integer $n$ with $\xi$ trivial on $U^{n+1}_E$ and not on $U^n_E$, and $\xi$ and $\xi^{-1}$ have the same kernel. By Definition 3.3.12, $\xi$ is minimal when $\xi|_{U^n_E}$ does not factor through the norm. If $\xi^{-1}|_{U^n_E} = \varphi \circ N$, then $\xi|_{U^n_E} = \varphi^{-1} \circ N$. So $\xi^{-1}$ is minimal when $\xi$ is. Part 2. By Definition 3.9.9, $\alpha$ is minimal of level $n$ when $\alpha \in \mathfrak{p}_E^{-n}$ and $\alpha \notin K + \mathfrak{p}_E^{1-n}$. Both sets are closed under negation, so the conditions hold for $-\alpha$. The lattice $\mathfrak{P}^{-n}$ is also closed under negation. Part 3. The group $J_\alpha = E^\times U^{m}_{\mathfrak{A}}$ depends only on $E$, $\mathfrak{A}$ and the level, so $J_{-\alpha} = J_\alpha$; the library identifies the two groups through `cInd_comp_inclusion_iso`. On $E^\times$ the character $\Lambda_0^{-1}$ is $\xi_0^{-1}$. On the group $U^m_{\mathfrak{A}}$ of Definition 3.9.12,
$$\psi_{-\alpha}(x) = \psi(\mathrm{tr}(-\alpha(x - 1))) = \psi(\mathrm{tr}(\alpha(x - 1)))^{-1} = \psi_\alpha(x)^{-1} = \Lambda_0(x)^{-1},$$
because the trace is linear. So $\Lambda_0^{-1}$ satisfies both conditions of Definition 3.9.12 for $(-\alpha, \xi_0^{-1})$. $\square$

**Definition 3.12.9 (the inverse datum).** Let $D = (\psi, \mathfrak{A}, v, \xi_0, \alpha, \Lambda_0, \chi)$ be a tame datum for $(L/K, \xi)$. Its inverse is
$$D^{-1} = (\psi, \mathfrak{A}, v, \xi_0^{-1}, -\alpha, \Lambda_0^{-1}, \chi^{-1}).$$
It is a tame datum for $(L/K, \xi^{-1})$: Lemma 3.12.8 gives the conditions on $\xi_0^{-1}$, $-\alpha$ and $\Lambda_0^{-1}$, the character $\chi^{-1}$ is smooth, and $\xi^{-1} = \xi_0^{-1} (\chi^{-1})_L$. The character of $J_{-\alpha} = J_\alpha$ is $\Lambda_0^{-1} \cdot (\chi^{-1} \circ \det) = \Lambda^{-1}$.

Lean: `Langlands.LocalGL2.TameDatum.inv`, `Langlands.LocalGL2.TameDatum.jGroup_inv_le`

The pair $(L/K, \xi^{-1})$ is admissible by Proposition 3.9.32. The additive character, the order and the basis stay the same. Only the characters and the sign of $\alpha$ change.

**Theorem 3.12.10 (the contragredient of a type).** Let $D$ be a tame datum for $(L/K, \xi)$. Then $\pi_{D^{-1}} \cong \mathrm{c\text{-}Ind}_{J_\alpha}^G \Lambda^{-1}$ and $\pi_D^\vee \cong \pi_{D^{-1}}$.

Lean: `Langlands.LocalGL2.TameDatum.inv_rep_iso`, `Langlands.LocalGL2.TameDatum.contragredient_rep_iso`

*Proof.* The first isomorphism is Definition 3.12.9 with the identification $J_{-\alpha} = J_\alpha$. For the second, $J_\alpha$ contains $K^\times$ and is compact modulo $K^\times$, and the intertwining of $\Lambda$ is $J_\alpha$, by Proposition 3.10.23. Corollary 3.12.6 gives $\pi_D^\vee \cong \mathrm{c\text{-}Ind}_{J_\alpha}^G \Lambda^{-1}$, and the first isomorphism concludes. $\square$

**Corollary 3.12.11 (input 4 of Definition 3.10.27).** The statement `TypeRepContragredient` holds for every $K$: if $\pi \cong \pi_D$ for a tame datum $D$ for $(L/K, \xi)$ and $\pi' \cong \pi^\vee$, then $\pi' \cong \pi_{D'}$ for a tame datum $D'$ for $(L/K, \xi^{-1})$.

Lean: `Langlands.LocalGL2.typeRepContragredient`

*Proof.* Take $D' = D^{-1}$. Then $\pi' \cong \pi^\vee \cong \pi_D^\vee \cong \pi_{D^{-1}}$, by Lemma 3.12.1 and Theorem 3.12.10. $\square$

The proof uses no hypothesis on $p$. The condition $p \ne 2$ is in the definition of a tame datum only through the existence of the data, which is input 5 of Definition 3.10.27 and is not used here.

### Linear algebra in dimension 2

The Galois side starts with elementary facts on $\mathbb{C}^2$. We write vectors as columns $x = (x_0, x_1)$ and put
$$\det(x, y) = x_0 y_1 - x_1 y_0,$$
the determinant of the matrix with columns $x$ and $y$. A matrix is *scalar* if it is $c \cdot 1$ for some $c \in \mathbb{C}$.

**Lemma 3.12.12 (the determinant identities).** Let $x, y, z \in \mathbb{C}^2$ and $M \in M_2(\mathbb{C})$.
1. If $x \ne 0$ and $\det(x, y) = 0$, then $y = c x$ for some $c \in \mathbb{C}$.
2. $\det(x, y)\, z = \det(z, y)\, x + \det(x, z)\, y$.
3. $\det(Mx, y) + \det(x, My) = \mathrm{tr}(M) \det(x, y)$.
4. If $\det(x, y) \ne 0$, $Mx = ax$ and $My = ay$, then $M = a \cdot 1$.
5. If $M$ is not scalar, then each eigenvalue of $M$ is a root of $t^2 - \mathrm{tr}(M) t + \det M$, so $M$ has at most two eigenvalues, and the eigenspace of each eigenvalue is a line.
6. If $Mx = ax$ and $My = by$ with $x, y \ne 0$ and $a \ne b$, and $Mz = cz$ with $z \ne 0$, then $z$ is a multiple of $x$ or of $y$.

Lean: `Langlands.LocalGL2.gtpDet`, `Langlands.LocalGL2.IsScalarMat`, `Langlands.LocalGL2.exists_eq_smul_of_gtpDet_eq_zero`, `Langlands.LocalGL2.gtpDet_smul_eq`, `Langlands.LocalGL2.gtpDet_mulVec_add`, `Langlands.LocalGL2.mulVec_eq_smul_of_gtpDet_ne_zero`, `Langlands.LocalGL2.charQ_eq_zero`, `Langlands.LocalGL2.eq_or_eq_of_charQ`, `Langlands.LocalGL2.gtpDet_eq_zero_or_of_eigen`, `Langlands.LocalGL2.exists_eigen`

*Proof.* Part 1. If $x_0 \ne 0$, put $c = y_0 / x_0$; then $y_1 x_0 = x_1 y_0$ gives $y_1 = c x_1$. The case $x_1 \ne 0$ is symmetric. Parts 2 and 3 are polynomial identities in the entries and are checked by expanding both sides. Part 4. By part 2, each $z$ is $\det(x,y)^{-1}(\det(z, y) x + \det(x, z) y)$, so $Mz = a z$. Part 5. If $Mx = ax$ with $x \ne 0$, then by the Cayley-Hamilton theorem $0 = (M^2 - \mathrm{tr}(M) M + \det M)x = (a^2 - \mathrm{tr}(M) a + \det M) x$. A quadratic polynomial has at most two roots. If an eigenspace had dimension 2, $M$ would be scalar. Part 6. The vectors $x$ and $y$ are independent, since otherwise $a = b$. So $M$ is not scalar and has exactly the eigenvalues $a$ and $b$, by part 5. Then $c = a$ or $c = b$, and $z$ lies in the line of eigenvectors for $c$, which is $\mathbb{C}x$ or $\mathbb{C}y$. $\square$

**Proposition 3.12.13 (a common eigenvector for a $p$-group).** Let $p$ be an odd prime and let $G$ be a finite $p$-subgroup of $GL_2(\mathbb{C})$. Then the elements of $G$ have a common eigenvector.

Lean: `Langlands.LocalGL2.exists_common_eigen_of_isPGroup`

*Proof.* If each element of $G$ is scalar, any nonzero vector works. Assume not. Let $Z$ be the group of scalar matrices. The quotient $G/(G \cap Z)$ is a nontrivial finite $p$-group, so its centre is nontrivial. Choose $y \in G$ whose image is central and not trivial. Then $y$ is not scalar, and for each $h \in G$ the commutator $y h y^{-1} h^{-1}$ is scalar, say $e_h \cdot 1$. So $y h = e_h h y$.

Fix $h \in G$ and put $e = e_h$. Let $v$ be an eigenvector of $y$, with $yv = av$. The eigenvalue $a$ is not zero, since $y$ is invertible. By induction on $m$, $y h^m = e^m h^m y$, so
$$y (h^m v) = e^m a \, (h^m v), \qquad m \ge 0,$$
and $h^m v \ne 0$. Thus $a$, $ea$ and $e^2 a$ are eigenvalues of $y$. By Lemma 3.12.12, part 5, they take at most two values. If $e \ne 1$, then $a \ne ea$, and $e^2 a$ equals $a$ or $ea$, which gives $e^2 = 1$. So in all cases $e^2 = 1$. On the other hand $h^{p^k} = 1$ for some $k$, and then $y = y h^{p^k} = e^{p^k} h^{p^k} y = e^{p^k} y$, so $e^{p^k} = 1$. Since $p^k$ is odd and $e^2 = 1$, we get $e = 1$.

So $y$ commutes with each $h \in G$. Then $y(hv) = h(yv) = a \, hv$, so $hv$ is in the eigenspace of $y$ for $a$. That eigenspace is the line $\mathbb{C}v$, by Lemma 3.12.12, part 5, because $y$ is not scalar. So $hv$ is a multiple of $v$ for each $h \in G$. $\square$

**Example 3.12.14 (the quaternion group).** The statement fails for $p = 2$. Let $Q_8 \subseteq GL_2(\mathbb{C})$ be generated by
$$\mathbf{i} = \begin{pmatrix} i & 0 \\ 0 & -i \end{pmatrix}, \qquad \mathbf{j} = \begin{pmatrix} 0 & -1 \\ 1 & 0 \end{pmatrix}.$$
The eigenvectors of $\mathbf{i}$ are the multiples of $(1, 0)$ and of $(0, 1)$, and $\mathbf{j}$ swaps these two lines. So there is no common eigenvector. In the proof above, $y = \mathbf{i}$ has central image in $Q_8/\{\pm 1\}$, and $\mathbf{i}\mathbf{j} = -\mathbf{j}\mathbf{i}$, so $e_{\mathbf{j}} = -1$. The condition $e^2 = 1$ holds, but $e^{2^k} = 1$ does not force $e = 1$. For $p = 2$ the wild inertia group can act on an irreducible parameter with no common eigenvector, and there are irreducible parameters that are not induced from any quadratic extension, the primitive parameters. The argument of this section cannot reach them.

### Clifford theory with the line stabilizer

Let $W$ be a group and $r : W \to GL_2(\mathbb{C})$ an irreducible representation: no line of $\mathbb{C}^2$ is stable under all $r(w)$. For a nonzero vector $v$ we use the stabilizer of the line $\mathbb{C} v$.

**Definition 3.12.15 (line stabilizer and line character).** For $v \ne 0$, let
$$\mathrm{Stab}(v) = \{ g \in W : r(g) v \in \mathbb{C} v \}.$$
It is a subgroup of $W$. The *line character* $\chi_v : \mathrm{Stab}(v) \to \mathbb{C}^\times$ is defined by $r(h) v = \chi_v(h) v$.

Lean: `Langlands.LocalGL2.lineStab`, `Langlands.LocalGL2.mem_lineStab_iff`, `Langlands.LocalGL2.lineChar`, `Langlands.LocalGL2.lineChar_spec`

The kernel of $r$ lies in $\mathrm{Stab}(v)$, and $\chi_v$ is trivial on it (`ker_le_lineStab`). If $r$ is irreducible, then $\mathrm{Stab}(v) \ne W$ (`exists_notMem_lineStab`). If $r(g)$ is scalar, then $g \in \mathrm{Stab}(v)$ for every $v$ (`mem_lineStab_of_isScalarMat`). If $r'(w) = A r(w) A^{-1}$ for all $w$, then the stabilizer of $Av$ for $r'$ is the stabilizer of $v$ for $r$ (`lineStab_conj`), since $r'(g) Av = A r(g) v$.

**Proposition 3.12.16 (index 2).** Let $r : W \to GL_2(\mathbb{C})$ be irreducible. Let $Q$ be a normal subgroup of $W$ and $v$ a common eigenvector of $r(Q)$. Assume that $r(n_0)$ is not scalar for some $n_0 \in Q$. Then $Q \subseteq \mathrm{Stab}(v)$ and $\mathrm{Stab}(v)$ has index 2 in $W$. If $s \notin \mathrm{Stab}(v)$, then $\chi_v(s^{-1} n_0 s) \ne \chi_v(n_0)$.

Lean: `Langlands.LocalGL2.le_lineStab`, `Langlands.LocalGL2.index_lineStab`, `Langlands.LocalGL2.eigen_translate`, `Langlands.LocalGL2.conj_eigen`, `Langlands.LocalGL2.eigen_conj_ne`

*Proof.* The inclusion $Q \subseteq \mathrm{Stab}(v)$ is the hypothesis. Let $H = \mathrm{Stab}(v)$. Since $r$ is irreducible, there is $s \notin H$. Put $w = r(s) v$. Then $w \notin \mathbb{C} v$, so $\det(v, w) \ne 0$ by Lemma 3.12.12, part 1.

For each $g \in W$ the vector $r(g) v$ is an eigenvector of $r(n_0)$: indeed $g^{-1} n_0 g \in Q$, so $r(g^{-1} n_0 g) v = c v$ for some $c$, and then $r(n_0) r(g) v = r(g) r(g^{-1} n_0 g) v = c \, r(g) v$. In particular $r(n_0) v = a v$ with $a = \chi_v(n_0)$, and $r(n_0) w = b w$ with $b = \chi_v(s^{-1} n_0 s)$. If $a = b$, then $r(n_0)$ is scalar by Lemma 3.12.12, part 4, which is excluded. So $a \ne b$. This is the last statement.

Now let $g \in W$. The vector $r(g) v$ is an eigenvector of $r(n_0)$, so by Lemma 3.12.12, part 6, it is a multiple of $v$ or of $w = r(s) v$. In the first case $g \in H$. In the second case $r(s^{-1} g) v \in \mathbb{C} v$, so $s^{-1} g \in H$. Thus $W = H \cup sH$, and $H \ne W$, so $H$ has index 2. $\square$

When $H = \mathrm{Stab}(v)$ has index 2, the vectors $v$ and $r(s) v$ form a basis, and in this basis $r$ is the induced representation $\mathrm{Ind}_H^W \chi_v$. This is the classical Clifford theory, and the library proves it in the form `iso_indWD_of_eigenvector` of the file `WeilInduction.lean`. The proposition says more: the inducing subgroup is the stabilizer of an eigenline of one non-scalar element of $Q$. The converse statement identifies the subgroup from the induced representation.

**Lemma 3.12.17 (the stabilizer of an induced representation).** Let $H$ be a subgroup of index 2 of $W$, $s \notin H$, and $\phi$ a character of $H$. Let $r = \mathrm{Ind}_H^W \phi$ be irreducible. Let $n_0 \in H$ with $\phi(s^{-1} n_0 s) \ne \phi(n_0)$. Then for each eigenvector $u$ of $r(n_0)$, $\mathrm{Stab}(u) = H$.

Lean: `Langlands.LocalGL2.lineStab_ind_eq`, `Langlands.LocalGL2.lineStab_eq_of_le`, `Langlands.LocalGL2.isScalarMat_diagonal_iff`

*Proof.* In the standard basis $e_0, e_1 = r(s) e_0$ of the induced representation, each $h \in H$ acts by the diagonal matrix with entries $\phi(h)$ and $\phi(s^{-1} h s)$. For $h = n_0$ the two entries differ, so the eigenvectors of $r(n_0)$ are the multiples of $e_0$ and of $e_1$, by Lemma 3.12.12, part 6. Each of these lines is stable under the diagonal matrices $r(h)$, $h \in H$, so $H \subseteq \mathrm{Stab}(u)$. Since $r$ is irreducible, $\mathrm{Stab}(u) \ne W$. A subgroup between a subgroup of index 2 and $W$ is one of the two, so $\mathrm{Stab}(u) = H$. $\square$

### The Weil group facts

The wild inertia group $P_K$ is the subgroup of $W_K$ generated by the elements $w \in I_K$ with $w(x) - x \in \bar{\mathfrak{m}} x$ for each $x$ in the integral closure $\bar{\mathcal{O}}$ of $\mathcal{O}_K$ in $\bar K$, where $\bar{\mathfrak{m}}$ is its maximal ideal. It is normal, as a normal closure. In each finite Galois extension $M/K$ its image is the first ramification group $G_1(M/K)$ ([Ser79], Chapter IV, section 2, Proposition 7).

Lean: `Langlands.LocalGL2.wildInertia`, `Langlands.LocalGL2.wildInertia_le_inertia`

**Definition 3.12.18 (the named facts).** Let $K$ be a nonarchimedean local field with residue characteristic $p$. The following statements on $K$ are the inputs of the parametrization.
1. `ArtinConjCompat`. For each separable quadratic $L/K$ and each local Artin map $\mathrm{art}_L$, $\mathrm{art}_L(\tau x) = s \, \mathrm{art}_L(x) \, s^{-1}$ in $W_L^{ab}$ for $x \in L^\times$ ([Ser79], Chapter XI, section 3).
2. `WildInertiaProP`. For each open normal subgroup $U$ of $W_K$ and each $x \in P_K$, some power $x^{p^k}$ lies in $U$. This says that $P_K$ is a pro-$p$ group ([Ser79], Chapter IV, section 2, Corollary 3 to Proposition 7).
3. `TameInertiaProcyclic`. There is $t \in I_K$ such that for each open subgroup $U$ and each $i \in I_K$, $i \in n t^k U$ for some $n \in P_K$ and $k \in \mathbb{Z}$. This says that $I_K/P_K$ is procyclic ([Ser79], Chapter IV, section 2, Corollary 1 to Proposition 7, and Iwasawa).
4. `OpenIndexTwoQuad`. Each open subgroup of index 2 of $W_K$ is $W_L$ for a separable quadratic extension $L$ of $K$ inside $\bar K$ ([Tat79], section 1.4).
5. `InertiaUnramified`. If $L/K$ is separable quadratic and $I_K \subseteq W_L$, then $L/K$ is unramified ([Ser79], Chapter IV, section 1, and Chapter III, section 5).
6. `UniqueUnramifiedQuad`. Two unramified separable quadratic extensions of $K$ inside $\bar K$ are equal ([Ser79], Chapter III, section 5, Theorem 2 and its corollary).
7. `WildArtinUnits`. For each separable quadratic $L/K$ and each local Artin map $\mathrm{art}_L$, an element $x \in L^\times$ lies in $U^1_L$ exactly when $x = \mathrm{art}_L^{-1}(h)$ for the image of some $h \in W_L \cap P_K$ in $W_L^{ab}$ ([Ser79], Chapter XV, section 2, Theorem 2, with the Hasse-Arf theorem of Chapter V, section 7).
8. `NormFactorU1`. If $p \ne 2$, $L/K$ is separable quadratic, and $\xi$ is a character of $L^\times$ with $\xi(\tau u) = \xi(u)$ for $u \in U^1_L$, then there is a character $\varphi$ of $K^\times$ with $\xi(u) = \varphi(N u)$ for $u \in U^1_L$.

The structure `GaloisTameInputs` collects the eight facts.

Lean: `Langlands.LocalGL2.ArtinConjCompat`, `Langlands.LocalGL2.WildInertiaProP`, `Langlands.LocalGL2.TameInertiaProcyclic`, `Langlands.LocalGL2.OpenIndexTwoQuad`, `Langlands.LocalGL2.InertiaUnramified`, `Langlands.LocalGL2.UniqueUnramifiedQuad`, `Langlands.LocalGL2.WildArtinUnits`, `Langlands.LocalGL2.NormFactorU1`, `Langlands.LocalGL2.GaloisTameInputs`

Facts 2 and 3 are the classical structure of the inertia group: in a finite Galois extension $G_0/G_1$ is cyclic of order prime to $p$ and $G_1$ is a $p$-group. In the form above they concern $W_K$ through its open subgroups, so they are statements on all finite extensions at once. Fact 7 is the statement $\mathrm{art}_L(U^1_L) = P_L^{ab}$, where $P_L = W_L \cap P_K$ is the wild inertia group of $L$: the reciprocity map sends $U^v_L$ onto the upper ramification group $G^v$, and the Hasse-Arf theorem makes the upper numbering integral for abelian extensions. Fact 1 is one of the three compatibilities of input 1 of Definition 3.9.30, stated for one field. The library keeps it separate from `ArtinCompat` because it is the only compatibility the Galois side uses. We prove facts 5, 6 and 8 at the end of this section.

The facts have consequences that we use repeatedly. The first two need $p \ne 2$.

**Lemma 3.12.19 (consequences of the facts).** Assume fact 2. Let $r : W_K \to GL_2(\mathbb{C})$ be a homomorphism with open kernel.
1. The image $r(I_K)$ is finite.
2. If $p \ne 2$ and $L/K$ is separable quadratic, then $P_K \subseteq W_L$.
3. The image $r(P_K)$ is a finite $p$-group, and if $p \ne 2$ the matrices $r(n)$, $n \in P_K$, have a common eigenvector.

Lean: `Langlands.LocalGL2.finite_map_inertia`, `Langlands.LocalGL2.mem_of_pow_mem_of_index_two`, `Langlands.LocalGL2.wildInertia_le_restrictSubgroup`, `Langlands.LocalGL2.exists_wildInertia_eigen`

*Proof.* Part 1. The inertia group is compact and $\ker r$ is open, so $I_K$ is covered by finitely many cosets of $I_K \cap \ker r$. The image $r(I_K)$ is in bijection with these cosets. Part 2. The subgroup $W_L$ is open and normal of index 2. For $x \in P_K$, fact 2 gives $x^{p^k} \in W_L$. Also $x^2 \in W_L$, since $W_K/W_L$ has order 2. Since $p^k$ is odd, $x = (x^{p^k})^a (x^2)^b$ for integers $a, b$ with $a p^k + 2b = 1$, so $x \in W_L$. Part 3. For $x \in P_K$, fact 2 with $U = \ker r$ gives $r(x)^{p^k} = 1$. So each element of the finite group $r(P_K)$ has order a power of $p$, and by Cauchy's theorem $r(P_K)$ is a $p$-group. Proposition 3.12.13 gives the eigenvector. $\square$

**Lemma 3.12.20 (irreducible Weil-Deligne representations).** Let $\rho = (r, N)$ be an irreducible Weil-Deligne representation of dimension 2. Then $N = 0$ and $r$ is irreducible.

Lean: `Langlands.LocalGL2.WeilDeligneRep.N_eq_zero_and_of_isIrreducible`

*Proof.* The relation $r(w) N r(w)^{-1} = \|w\| N$ shows that $\ker N$ is stable under $r$. It is also stable under $N$. Since $N$ is nilpotent, $\ker N \ne 0$. So $\ker N$ is a nonzero subspace stable under $\rho$, hence $\ker N = \mathbb{C}^2$ and $N = 0$. Then a line stable under $r$ would be stable under $\rho$, so $r$ is irreducible. $\square$

This is the argument of Proposition 3.9.31, which used $(\ker N)^{I_K}$; here the space $\ker N$ is enough.

Two more facts come from class field theory and Galois theory, and the library proves them. A character of $W_L$ with open kernel factors through $W_L^{ab}$, so it is $\xi_W$ for a unique smooth character $\xi$ of $L^\times$ (`exists_charW_eq`). If $L$ and $L'$ are separable quadratic and $W_L = W_{L'}$, then $L = L'$ (`eq_of_restrictSubgroup_eq`): otherwise the compositum $LL'$ has degree 4 over $K$, and $W_{LL'} = W_L \cap W_{L'}$ would have index 4, while it equals $W_L$, of index 2. Finally, by fact 1, $(\xi_W)^s = (\xi \circ \tau)_W$, where $(\xi_W)^s(h) = \xi_W(s^{-1} h s)$ (`conjChar_charW`).

### Irreducible parameters come from tame pairs

The next proposition is the Clifford step for $W_K$. It turns a common eigenvector of a normal subgroup into an admissible pair. The second condition of admissibility, Definition 3.3.9, part 2, is a statement on the field, and we keep it as a hypothesis.

**Proposition 3.12.21 (a pair from an eigenline).** Assume facts 1 and 4. Let $\rho = (r, 0)$ be a Weil-Deligne representation of dimension 2 with $r$ irreducible. Let $Q$ be a normal subgroup of $W_K$, let $v$ be a common eigenvector of $r(Q)$, and let $n_0 \in Q$ with $r(n_0)$ not scalar. Assume the following condition (U): if $W_L = \mathrm{Stab}(v)$, $\xi_W = \chi_v$, and $\xi|_{U^1_L}$ factors through $N_{L/K}$, then $L/K$ is unramified. Then there is an admissible pair $(L/K, \xi)$ with $W_L = \mathrm{Stab}(v)$ and $\rho \cong \sigma(L, \xi)$, for every choice of the Artin map of $L$.

Lean: `Langlands.LocalGL2.exists_tamePair_of_line`

*Proof.* By Proposition 3.12.16, $H = \mathrm{Stab}(v)$ has index 2. It contains $\ker r$, which is open, so $H$ is open. Fact 4 gives a separable quadratic $L$ with $W_L = H$. The line character $\chi_v$ has open kernel, because it is trivial on $\ker r$, so $\chi_v = \xi_W$ for a smooth character $\xi$ of $L^\times$.

We check that $(L/K, \xi)$ is admissible. For part 1 of Definition 3.3.9, recall that $\xi$ factors through the norm exactly when $\xi = \xi \circ \tau$, by Hilbert's theorem 90 (Section 3.3). By Proposition 3.12.16, $\xi_W(s^{-1} n_0 s) \ne \xi_W(n_0)$, and by fact 1 the left side is $(\xi \circ \tau)_W(n_0)$. So $\xi \circ \tau \ne \xi$. Part 2 of Definition 3.3.9 is the condition (U).

The vector $v$ is an eigenvector for $W_L$ with character $\xi_W$, so $\rho \cong \mathrm{Ind}_{W_L}^{W_K} \xi_W = \sigma(L, \xi)$ by Clifford theory (`iso_indWD_of_eigenvector`); both have $N = 0$. A local Artin map of $L$ is unique (`isLocalArtinMap_unique`), so the statement holds for every choice. $\square$

To find $Q$, $v$ and $n_0$ we look first at the wild inertia group and then at the inertia group. The inertia group cannot act by scalars.

**Lemma 3.12.22 (inertia is not scalar).** Let $r : W_K \to GL_2(\mathbb{C})$ be irreducible. Then $r(i)$ is not scalar for some $i \in I_K$.

Lean: `Langlands.LocalGL2.not_forall_isScalarMat_inertia`

*Proof.* Assume that $r(i)$ is scalar for all $i \in I_K$. Let $\Phi$ be a Frobenius element and $u$ an eigenvector of $r(\Phi)$. Each $w \in W_K$ is $\Phi^m i$ with $m = d(w)$ and $i \in I_K$, so $r(w) u \in \mathbb{C} u$. The line $\mathbb{C} u$ is stable, which contradicts irreducibility. $\square$

**Theorem 3.12.23 (part 1 of the parametrization).** Let $p \ne 2$ and assume the eight facts of Definition 3.12.18. Then each irreducible Weil-Deligne representation $\rho$ of $W_K$ of dimension 2 is isomorphic to $\sigma(L, \xi)$ for an admissible pair $(L/K, \xi)$.

Lean: `Langlands.LocalGL2.exists_tamePair_of_isIrreducible`

*Proof.* By Lemma 3.12.20, $\rho = (r, 0)$ with $r$ irreducible. By Lemma 3.12.19, part 3, $r(P_K)$ has a common eigenvector $v$. There are two cases.

Case A: $r(n_0)$ is not scalar for some $n_0 \in P_K$. We apply Proposition 3.12.21 with $Q = P_K$, and we check that the condition (U) holds because its hypothesis never holds. Suppose that $W_L = \mathrm{Stab}(v)$, $\xi_W = \chi_v$, and $\xi(u) = \varphi(N u)$ for $u \in U^1_L$. Since $N \circ \tau = N$, $\xi(\tau u) = \xi(u)$ for $u \in U^1_L$. Let $n \in P_K$. By Lemma 3.12.19, part 2, $n \in W_L$, and $s^{-1} n s \in P_K$ since $P_K$ is normal. By fact 7, $u = \mathrm{art}_L^{-1}(n)$ lies in $U^1_L$. By fact 1,
$$\xi_W(s^{-1} n s) = (\xi \circ \tau)_W(n) = \xi(\tau u) = \xi(u) = \xi_W(n).$$
For $n = n_0$ this contradicts the last statement of Proposition 3.12.16. So Proposition 3.12.21 applies.

Case B: $r(n)$ is scalar for each $n \in P_K$. Let $t$ be as in fact 3, and let $v$ now be an eigenvector of $r(t)$. Take $U = \ker r$ in fact 3: each $i \in I_K$ is $n t^k u$ with $n \in P_K$, $k \in \mathbb{Z}$ and $u \in \ker r$, so $r(i) = r(n) r(t)^k$ is a scalar times a power of $r(t)$. So $v$ is a common eigenvector of $r(I_K)$. The inertia group is normal, as the kernel of $d$. By Lemma 3.12.22, $r(i_0)$ is not scalar for some $i_0 \in I_K$. We apply Proposition 3.12.21 with $Q = I_K$. The condition (U) holds: if $W_L = \mathrm{Stab}(v)$, then $I_K \subseteq W_L$, and fact 5 shows that $L/K$ is unramified. $\square$

The two cases match the two kinds of admissible pairs. In Case B the field $L$ is unramified. In Case A the field $L$ can be ramified or unramified, but the character $\xi$ is not invariant under $\tau$ on $U^1_L$. The next lemma makes this precise, and it gives the converse needed for part 2.

**Lemma 3.12.24 (scalar wild inertia).** Let $p \ne 2$ and assume facts 1, 2, 7 and 8. Let $(L/K, \xi)$ be an admissible pair, and assume that $\sigma(L, \xi)(n)$ is scalar for each $n \in P_K$. Then $L/K$ is unramified.

Lean: `Langlands.LocalGL2.isUnramifiedExt_of_isScalarMat`

*Proof.* By Lemma 3.12.19, part 2, $P_K \subseteq W_L$. In the standard basis, $n \in P_K$ acts by the diagonal matrix with entries $\xi_W(n)$ and $\xi_W(s^{-1} n s) = (\xi \circ \tau)_W(n)$, by fact 1. This matrix is scalar, so $\xi_W(n) = (\xi \circ \tau)_W(n)$ for $n \in P_K$. By fact 7, each $u \in U^1_L$ is $\mathrm{art}_L^{-1}(n)$ for some $n \in W_L \cap P_K$, so $\xi(u) = \xi(\tau u)$ for all $u \in U^1_L$. By fact 8, $\xi|_{U^1_L}$ factors through the norm. Part 2 of Definition 3.3.9 gives that $L/K$ is unramified. $\square$

**Theorem 3.12.25 (part 2 of the parametrization).** Let $p \ne 2$ and assume the eight facts. If $(L/K, \xi)$ and $(L'/K, \xi')$ are admissible pairs with $\sigma(L, \xi) \cong \sigma(L', \xi')$, then $L = L'$.

Lean: `Langlands.LocalGL2.eq_of_tameParam_iso`

*Proof.* Write $r = \sigma(L, \xi)$ and $r' = \sigma(L', \xi')$, and let $A \in GL_2(\mathbb{C})$ with $r'(w) = A r(w) A^{-1}$ for all $w$. A matrix is scalar exactly when its conjugate is scalar (`isScalarMat_conj_iff`).

If $r(n)$ is scalar for each $n \in P_K$, then so is $r'(n)$. Lemma 3.12.24 shows that $L$ and $L'$ are unramified, and fact 6 gives $L = L'$.

Otherwise let $n_0 \in P_K$ with $r(n_0)$ not scalar. Then $r'(n_0)$ is not scalar either. By Lemma 3.12.19, part 2, $n_0 \in W_L \cap W_{L'}$. In the standard basis $e_0, r(s) e_0$ of $r$, $r(n_0)$ is diagonal with entries $\xi_W(n_0)$ and $\xi_W(s^{-1} n_0 s)$, and they differ because $r(n_0)$ is not scalar. So Lemma 3.12.17 gives $\mathrm{Stab}_r(e_0) = W_L$. The vector $A e_0$ is an eigenvector of $r'(n_0) = A r(n_0) A^{-1}$. For the same reason, with $s'$ outside $W_{L'}$, Lemma 3.12.17 applies to $r'$ and gives $\mathrm{Stab}_{r'}(A e_0) = W_{L'}$. But $\mathrm{Stab}_{r'}(A e_0) = \mathrm{Stab}_r(e_0)$. So $W_L = W_{L'}$, and $L = L'$. $\square$

**Theorem 3.12.26 (input 3 of Definition 3.9.30 from the facts).** If the eight facts of Definition 3.12.18 hold for $K$, then `GaloisTameParametrization` holds for $K$.

Lean: `Langlands.LocalGL2.galoisTameParametrization_of_inputs`

*Proof.* The statement `GaloisTameParametrization` assumes $p \ne 2$, in the form $2 \ne 0$ in the residue field, and consists of the conclusions of Theorems 3.12.23 and 3.12.25. $\square$

This is the Galois half of [BH06], 34.1. The proof uses only Proposition 3.12.13 and Clifford theory, and not the classification of the finite subgroups of $PGL_2(\mathbb{C})$. The hypothesis $p \ne 2$ is what makes this short argument possible.

**Example 3.12.27 (the unramified case).** Let $p \ne 2$, let $L/K$ be unramified quadratic, and let $\xi$ be a character of $L^\times$ trivial on $U^1_L$ with $\xi \ne \xi \circ \tau$ on $\mathcal{O}_L^\times$. Such a $\xi$ is given by a character $\theta$ of $\mathbb{F}_{q^2}^\times$ with $\theta^q \ne \theta$ and a value $\xi(\varpi)$. The pair is admissible, and it has level 0. Let $r = \sigma(L, \xi)$. For $n \in P_K$, fact 7 gives $\mathrm{art}_L^{-1}(n) \in U^1_L$, so $\xi_W(n) = 1$, and the same holds for $s^{-1} n s$. So $r(P_K)$ is trivial and the proof of Theorem 3.12.23 is in Case B. The element $t$ of fact 3 lies in $I_K \subseteq W_L$, and it acts in the standard basis by the diagonal matrix with entries $\xi_W(t)$ and $\xi_W(s^{-1} t s) = (\xi \circ \tau)_W(t)$. These entries differ: otherwise $r(t)$ is scalar, then $r(I_K)$ is scalar by the argument of Case B, and Lemma 3.12.22 is contradicted. So the eigenlines of $r(t)$ are the two lines of the standard basis, and their stabilizer is $W_L$, by Lemma 3.12.17. The proof recovers the field $L$ from the action of a single element of $I_K$.

**Example 3.12.28 (the ramified case).** Let $p \ne 2$ and let $L/K$ be ramified quadratic, for instance $L = K(\sqrt{\varpi})$. If $(L/K, \xi)$ is admissible, then part 2 of Definition 3.3.9 says that $\xi|_{U^1_L}$ does not factor through the norm. By fact 8, $\xi(\tau u) \ne \xi(u)$ for some $u \in U^1_L$. By fact 7 and fact 1, this means that $r(n)$ is not scalar for some $n \in P_K$, so the proof of Theorem 3.12.23 is in Case A. In particular, no admissible pair over a ramified $L$ has a character trivial on $U^1_L$. This is the Galois form of the fact that the pairs of level 0 all come from the unramified quadratic extension.

### Three facts proved

We prove facts 8, 6 and 5. The first is about units, and it is where $p \ne 2$ enters for the second time.

**Lemma 3.12.29 (square roots in $U^1$).** Let $E$ be a nonarchimedean local field whose residue characteristic is not 2.
1. If $a \in U^1_E$ and $a^2 = 1$, then $a = 1$.
2. Each $u \in U^1_E$ has a square root in $U^1_E$.

Lean: `Langlands.LocalGL2.wf_eq_one_of_sq_eq_one`, `Langlands.LocalGL2.mem_unitFilt_succ_of_sq`, `Langlands.LocalGL2.exists_sq_eq_of_mem_unitFilt`, `Langlands.LocalGL2.wf_two_ne_zero_residue`

*Proof.* Part 1. Write $a = 1 + x$ with $x \in \mathfrak{p}_E$. Then $0 = a^2 - 1 = x(2 + x)$, and $2 + x$ is a unit because $2$ is a unit and $x \in \mathfrak{p}_E$. So $x = 0$. The library proves the same statement by showing $a \in U^m_E$ for all $m$, from $a^2 - 1 = x(2 + x)$. Part 2. The polynomial $X^2 - u$ has the root $1$ modulo $\mathfrak{p}_E$, and its derivative $2X$ is a unit at $X = 1$. Hensel's lemma gives a root $w \equiv 1 \bmod \mathfrak{p}_E$. $\square$

The residue field of a quadratic extension $L/K$ has characteristic $p$, so the lemma applies to $L$ when $p \ne 2$ (`wf_two_ne_zero_residue`).

**Lemma 3.12.30 (norm one principal units).** Let $p \ne 2$ and let $L/K$ be separable quadratic. If $u \in U^1_L$ and $u \, \tau(u) = 1$, then $u = w / \tau(w)$ for some $w \in U^1_L$.

Lean: `Langlands.LocalGL2.wf_exists_sq_eq_div`

*Proof.* Let $w \in U^1_L$ with $w^2 = u$, by Lemma 3.12.29, part 2. The automorphism $\tau$ preserves $U^1_L$, so $w \tau(w) \in U^1_L$, and $(w \tau(w))^2 = u \tau(u) = 1$. By Lemma 3.12.29, part 1, $w \tau(w) = 1$. So $\tau(w) = w^{-1}$ and $w/\tau(w) = w^2 = u$. $\square$

Hilbert's theorem 90 gives $u = w/\tau(w)$ with $w \in L^\times$. The point of the lemma is that $w$ can be chosen in $U^1_L$. Exercise 41 shows that this fails for $p = 2$.

**Theorem 3.12.31 (fact 8).** The statement `NormFactorU1` holds for every $K$.

Lean: `Langlands.LocalGL2.normFactorU1_holds`

*Proof.* Let $p \ne 2$, $L/K$ separable quadratic, and $\xi$ a character of $L^\times$ with $\xi(\tau u) = \xi(u)$ for $u \in U^1_L$. Let $u \in U^1_L$ with $N u = 1$. By Lemma 3.12.30, $u = w/\tau(w)$ with $w \in U^1_L$, so $\xi(u) = \xi(w) \xi(\tau w)^{-1} = 1$. Thus $\xi|_{U^1_L}$ is trivial on the kernel of $N : U^1_L \to K^\times$, and there is a homomorphism $\varphi_0 : N(U^1_L) \to \mathbb{C}^\times$ with $\xi(u) = \varphi_0(N u)$. The group $\mathbb{C}^\times$ is divisible, so it is an injective abelian group, and $\varphi_0$ extends to a homomorphism $\varphi : K^\times \to \mathbb{C}^\times$ (`exists_factor_iff`). $\square$

The fact asks only for a homomorphism $\varphi$, and the proof does not use the continuity of $\xi$. If $\xi$ is smooth, one can choose $\varphi$ smooth, because $N(U^1_L)$ is open in $K^\times$; the library does not need this.

For facts 5 and 6 we use the residue degree. Let $L/K$ be separable quadratic with residue degree $f$ and ramification index $e$, so $ef = 2$. The degree map sends $W_L$ onto $f \mathbb{Z}$, since a Frobenius element of $L$ acts on the residue field of $\bar K$ as the $q^f$-th power. The library takes this as the definition of the residue degree of $L$ in terms of the Weil group: `residueDegree` is the index of $d(W_L)$ in $\mathbb{Z}$, and `residueDegree_dvd_index` and `map_degree_restrictSubgroup` relate it to the residue fields.

**Lemma 3.12.32 (residue degree 2).** Let $L/K$ be separable quadratic. Then $f = 2$ exactly when $L/K$ is unramified, and $f = 1$ exactly when $L/K$ is totally ramified. Let $W_K^{ev} = d^{-1}(2\mathbb{Z})$. It has index 2 in $W_K$, and if $L/K$ is unramified, then $W_L = W_K^{ev}$.

Lean: `Langlands.LocalGL2.wf_residueFinrank_ne_one`, `Langlands.LocalGL2.wf_residueFinrank_eq_one`, `Langlands.LocalGL2.wf_residueDegree_eq_two_iff`, `Langlands.LocalGL2.wfEvenDegree`, `Langlands.LocalGL2.index_wfEvenDegree`, `Langlands.LocalGL2.restrictSubgroup_eq_wfEvenDegree`

*Proof.* Since $ef = 2$, either $e = 1$ and $f = 2$, or $e = 2$ and $f = 1$. If $L/K$ is unramified, then $L = K(\zeta)$ for a root of unity $\zeta$ of order prime to $p$ whose residue class generates $\mathbb{F}_{q^2}$ (`unramUnit`), so the residue extension is not trivial and $f \ne 1$. If $L/K$ is totally ramified, $f = 1$ by definition. The degree map is onto $\mathbb{Z}$, so $W_K^{ev}$ has index 2. If $L/K$ is unramified, then $d(W_L) = 2\mathbb{Z}$, so $W_L \subseteq W_K^{ev}$. Both subgroups have index 2, so they are equal. $\square$

**Theorem 3.12.33 (facts 6 and 5).** The statements `UniqueUnramifiedQuad` and `InertiaUnramified` hold for every $K$.

Lean: `Langlands.LocalGL2.uniqueUnramifiedQuad_holds`, `Langlands.LocalGL2.inertiaUnramified_holds`

*Proof.* Fact 6. If $L$ and $L'$ are unramified, then $W_L = W_K^{ev} = W_{L'}$ by Lemma 3.12.32, and $L = L'$ (`eq_of_restrictSubgroup_eq`). Fact 5. Assume $I_K \subseteq W_L$. Since $I_K = \ker d$, $W_L = d^{-1}(d(W_L))$, and since $d$ is onto, the index of $W_L$ in $W_K$ equals the index of $d(W_L) = f\mathbb{Z}$ in $\mathbb{Z}$, which is $f$. The index of $W_L$ is 2, so $f = 2$, and $L/K$ is unramified by Lemma 3.12.32. $\square$

**Corollary 3.12.34 (the open Weil group facts).** Let `GaloisTameOpenInputs` be the conjunction of facts 1, 2, 3, 4 and 7 of Definition 3.12.18. If it holds for $K$, then `GaloisTameParametrization` holds for $K$.

Lean: `Langlands.LocalGL2.GaloisTameOpenInputs`, `Langlands.LocalGL2.GaloisTameOpenInputs.toGaloisTameInputs`, `Langlands.LocalGL2.galoisTameParametrization_of_openInputs`

*Proof.* Theorems 3.12.31 and 3.12.33 give facts 5, 6 and 8. Theorem 3.12.26 concludes. $\square$

The five open facts need two pieces of theory that the library does not have yet. Facts 2 and 3 need the ramification groups $G_i(M/K)$ of finite Galois extensions and their quotients ([Ser79], Chapter IV). Fact 4 needs the existence of an unramified extension of each degree inside $\bar K$ and the infinite Galois correspondence for the closure of a subgroup of $W_K$ in $G_K$. Fact 7 needs the upper numbering and the Hasse-Arf theorem, and fact 1 is a functoriality of local class field theory.

### What is open for $GL_2$, $p \ne 2$

**Corollary 3.12.35 (the reduction as it stands).** Let $p \ne 2$. The statement `Langlands.LocalLanglandsGL2Odd` follows, for all $K$, from:
1. `ArtinCompat` and `Rectifier`, inputs 1 and 4 of Definition 3.9.30;
2. the five facts of `GaloisTameOpenInputs`, Corollary 3.12.34;
3. `SupercuspidalZetaLaurent`, Definition 3.11.19;
4. the six facts of Definition 3.11.31;
5. `TypeRepInjective`, `TypeRepIndependent` and `UncoveredParametrization`, inputs 2, 3 and 5 of Definition 3.10.27.

Lean: `Langlands.LocalGL2.GL2OddFineInputs`, `Langlands.localLanglandsGL2_odd_of_fineInputs`, `Langlands.LocalGL2.galoisTameParametrization_of_openInputs`, `Langlands.LocalGL2.typeRepContragredient` (the joining step is not yet in the library)

*Proof.* Item 2 gives `GaloisTameParametrization` by Corollary 3.12.34. Corollary 3.12.11 gives `TypeRepContragredient` with no hypothesis. With these two statements, the items are the hypotheses of Corollary 3.11.35, which concludes. $\square$

**Remark 3.12.36 (what is still open for $GL_2$, $p \ne 2$).** This list replaces Remark 3.11.36.
1. `ArtinCompat` ([Ser79], Chapter XI).
2. The five facts `ArtinConjCompat`, `WildInertiaProP`, `TameInertiaProcyclic`, `OpenIndexTwoQuad` and `WildArtinUnits` of Corollary 3.12.34 ([Ser79], Chapters IV, XI and XV; [Tat79], section 1.4). They replace `GaloisTameParametrization`.
3. `Rectifier`, with the characters $\Delta_\xi$ of [BH06], section 34.
4. `SupercuspidalZetaLaurent`, the analytic half of Proposition 2.5.6.
5. The six facts of Definition 3.11.31.
6. `TypeRepInjective`, `TypeRepIndependent` and `UncoveredParametrization`.
7. The structure that joins the results of Sections 3.11 and 3.12 into `GL2OddFineInputs`.
8. The case $p = 2$, the $\varepsilon$-factors, and the uniqueness of Theorem 3.3.1.

Item 2 of Remark 3.11.36 is now reduced to classical facts on the Weil group, and `TypeRepContragredient` is removed from item 6. Items 1 and 2 overlap: `ArtinConjCompat` is the conjugation part of `ArtinCompat` for one quadratic extension, and a proof of `ArtinCompat` would give it. The facts in item 2 are all statements of local class field theory and ramification theory, not of the representation theory of $GL_2$. So after this section the open inputs on the Galois side are textbook results, and the open inputs on the representation side are items 3 to 6.
