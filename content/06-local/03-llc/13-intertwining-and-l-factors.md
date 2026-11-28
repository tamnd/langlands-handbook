---
title: Intertwining of types and the L-factor of a character
nodes: []
sources: [BH06, CF67, JL70]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Intertwining of types and the L-factor of a character

Remark 3.13.40 lists what is still open for $GL_2$ with $p \ne 2$. This section works on two items of that list. The first is input 2 of Definition 3.10.27, `TypeRepInjective`: if the representations $\pi_D$ and $\pi_{D'}$ of two tame data are isomorphic, then the pairs of the data are isomorphic. We do not prove it in full. We reduce it to two statements about two data with the same chain order and an intertwining element in the normalizer of that order, and we prove one half of the field part of these statements. The second item is fact 5 of Definition 3.11.31, `PSLFactorDetChar`: the Godement-Jacquet $L$-factor of the character $\chi |\cdot|^{1/2} \circ \det$ of $GL_2(K)$ is $L(s, \chi) L(s, \chi |\cdot|)$. We prove it in full, by a direct computation of the zeta integrals on $M_2(K) = K^4$.

The two halves use different tools. The first half is a study of intertwining. An isomorphism of compactly induced representations gives an element $g$ that intertwines the two characters, by the easy half of the Mackey formula. We then test the intertwining condition on unipotent elements of determinant $1$. Such elements do not see the characters $\chi$ and $\chi'$ of the two data, so the test works for any two data. The test forces the two chain orders and the two levels to be equal, and it forces $g$ into the normalizer of the chain order. The method is the method of Theorem 3.9.22, applied to two strata in place of one. For the maximal order, the two fields are then equal, since there is only one unramified quadratic extension of $K$. The second half is an integral over $K^4$. We cut $K^4$ into two regions, change variables in each, and reduce the integral to products of two of Tate's zeta integrals on $K$.

We keep the notation of Sections 3.9 to 3.13. The field $K$ is a nonarchimedean local field with residue field of $q$ elements, uniformizer $\varpi$ and $|\varpi| = q^{-1}$. We write $G = GL_2(K)$, $D(d) = \mathrm{diag}(1, d)$, and
$$x_+(c) = \begin{pmatrix} 1 & c \\ 0 & 1 \end{pmatrix}, \qquad x_-(c) = \begin{pmatrix} 1 & 0 \\ c & 1 \end{pmatrix}.$$
The chain orders are $\mathfrak{M}$ and $\mathfrak{J}$ of Definition 3.9.1, with the bounds $b_k(i, j)$, the filtrations $\mathfrak{P}^k_{\mathfrak{A}}$ and $U^k_{\mathfrak{A}}$, and the normalizer $\mathfrak{K}_{\mathfrak{A}}$. We use the two rules of the bounds from Section 3.9: $b_{k+e}(i, j) = b_k(i, j) + 1$ for $e = e_{\mathfrak{A}}$, and the duality $b_{1-k}(j, i) = 1 - b_k(i, j)$. The bounds also increase with $k$. For a matrix $Y \in M_2(K)$ and $x \in G$ we put $\psi_Y(x) = \psi(\mathrm{tr}(Y(x - 1)))$, so that $\psi_\alpha$ of Definition 3.9.3 is $\psi_Y$ for the matrix $Y$ of $\alpha$. A tame datum $D = (\psi, \mathfrak{A}, v, \xi_0, \alpha, \Lambda_0, \chi)$ for a pair $(L/K, \xi)$ is as in Definition 3.10.22. Its level is the level $n$ of $\xi_0$, which is odd, and we put $m = (n+1)/2 = [n/2] + 1$. Its group is $J = \iota_v(L^\times) U^m_{\mathfrak{A}}$, and its character is $\Lambda = \Lambda_0 \cdot (\chi \circ \det)$. A second datum $D'$ for a pair $(L'/K, \xi')$ has the same notation with primes. The Lean library numbers the rows and columns by $0$ and $1$. We number them by $1$ and $2$, as in Section 3.9.

### Intertwining and compact induction

**Definition 3.14.1 (intertwining of two characters).** Let $H$ be a group, $J$ and $J'$ subgroups, and $\Lambda$, $\Lambda'$ characters of $J$ and $J'$. An element $g \in H$ *intertwines $\Lambda$ with $\Lambda'$* if $\Lambda'(g x g^{-1}) = \Lambda(x)$ for each $x \in J$ with $g x g^{-1} \in J'$. For $J' = J$ and $\Lambda' = \Lambda$ this is the intertwining of Section 3.9.

Lean: `Langlands.IntertwinesWith`, `Langlands.intertwinesWith_self_iff`

**Lemma 3.14.2 (the inverse).** If $g$ intertwines $\Lambda$ with $\Lambda'$, then $g^{-1}$ intertwines $\Lambda'$ with $\Lambda$.

Lean: `Langlands.IntertwinesWith.inv`

*Proof.* Let $y \in J'$ with $g^{-1} y g \in J$. Put $x = g^{-1} y g$. Then $x \in J$ and $g x g^{-1} = y \in J'$, so $\Lambda'(y) = \Lambda(x) = \Lambda(g^{-1} y g)$. $\square$

Exercise 49 shows that the set of elements that intertwine $\Lambda$ with $\Lambda'$ is a union of double cosets $J' g J$.

**Proposition 3.14.3 (isomorphic inductions intertwine, [BH06] 11.5).** Let $H$ be a topological group, $J$ an open subgroup, $\Lambda$ a character of $J$ with open kernel, and $J'$, $\Lambda'$ a second such pair. If $\mathrm{c\text{-}Ind}_J^H \Lambda \cong \mathrm{c\text{-}Ind}_{J'}^H \Lambda'$, then some $g \in H$ intertwines $\Lambda$ with $\Lambda'$.

Lean: `Langlands.cIndBasic_ne_zero`, `Langlands.exists_intertwinesWith_of_iso`

*Proof.* Let $e$ be an isomorphism from the first representation to the second. Let $f_0$ be the basic vector of Lemma 3.10.29: it is $\Lambda$ on $J$ and $0$ outside $J$. It is not zero, since $f_0(1) = 1$. So $F = e(f_0)$ is not zero, and there is $g \in H$ with $F(g) \ne 0$. By Lemma 3.10.29, part 1, $\rho(j) f_0 = \Lambda(j) f_0$ for $j \in J$. Since $e$ commutes with the action,
$$F(g j) = (\rho(j) F)(g) = e(\rho(j) f_0)(g) = \Lambda(j) F(g).$$
Now let $j \in J$ with $g j g^{-1} \in J'$. The function $F$ lies in $\mathrm{c\text{-}Ind}_{J'}^H \Lambda'$, so $F(y x) = \Lambda'(y) F(x)$ for $y \in J'$. With $y = g j g^{-1}$ and $x = g$ this gives $F(g j) = \Lambda'(g j g^{-1}) F(g)$. Compare the two formulas and divide by $F(g) \ne 0$. Then $\Lambda'(g j g^{-1}) = \Lambda(j)$. $\square$

**Remark 3.14.4 (the other half of the Mackey formula).** The full statement of [BH06] 11.5 is an equivalence: when $J$ and $J'$ are open and compact modulo the centre, the two inductions are isomorphic if and only if some $g$ intertwines $\Lambda$ with $\Lambda'$. The converse direction builds a nonzero map from the function supported on $J' g J$, and it needs the irreducibility of both inductions. The library does not have it. We do not need it: for `TypeRepInjective` the isomorphism is the hypothesis, and only Proposition 3.14.3 is used. With the converse, the statement `TypeIntertwiningIso` of Definition 3.14.9 below would be equivalent to `TypeRepInjective`, and not only stronger.

### Intertwining data and isomorphic pairs

Recall from Section 3.13 that $\Lambda(\iota_v(y)) = \xi(y)$ for $y \in L^\times$ (Lemma 3.13.7). The scalar matrices $\iota_v(c) = c \cdot 1$ for $c \in K^\times$ lie in $J$ for every basis $v$.

**Lemma 3.14.5 (intertwining data have the same central character).** Let $D$ and $D'$ be data for $(L/K, \xi)$ and $(L'/K, \xi')$. If some $g \in G$ intertwines $\Lambda$ with $\Lambda'$, then $\xi|_{K^\times} = \xi'|_{K^\times}$.

Lean: `Langlands.LocalGL2.TameDatum.comp_algebraMap_eq_of_intertwinesWith`

*Proof.* Let $c \in K^\times$. The scalar matrix $c \cdot 1$ lies in $J$ and in $J'$, and it commutes with $g$. So $g (c \cdot 1) g^{-1} = c \cdot 1 \in J'$, and the intertwining gives $\Lambda'(c \cdot 1) = \Lambda(c \cdot 1)$. By Lemma 3.13.7 the two sides are $\xi'(c)$ and $\xi(c)$. $\square$

The next proposition is the last step of the proof of `TypeRepInjective` in [BH06], 20.2. Its hypothesis is a conjugation of the two embedded fields by an intertwining element.

**Proposition 3.14.6 (a conjugation of the fields gives an isomorphism of pairs).** Let $D$ and $D'$ be data for $(L/K, \xi)$ and $(L'/K, \xi')$, with bases $v$ and $v'$. Let $j : L \to L'$ be a $K$-isomorphism, and let $h \in G$ intertwine $\Lambda$ with $\Lambda'$ and satisfy $h \iota_v(y) h^{-1} = \iota_{v'}(j(y))$ for each $y \in L^\times$. Then $\xi = \xi' \circ j$, so the pairs are isomorphic.

Lean: `Langlands.LocalGL2.TameDatum.iso_of_intertwinesWith_conj`

*Proof.* Let $y \in L^\times$. Then $\iota_v(y) \in J$ and $h \iota_v(y) h^{-1} = \iota_{v'}(j(y)) \in J'$. The intertwining and Lemma 3.13.7 give
$$\xi(y) = \Lambda(\iota_v(y)) = \Lambda'(\iota_{v'}(j(y))) = \xi'(j(y)). \qquad \square$$

The converse also holds. For this we compare two data of one pair with the same chain order and the same basis.

**Lemma 3.14.7 (two data with one basis).** Let $D$ and $D'$ be data for $(L/K, \xi)$ with the same chain order $\mathfrak{A}$ and the same basis $v$. Then $J = J'$. If also $\Lambda$ and $\Lambda'$ agree on $U^m_{\mathfrak{A}}$, then $\Lambda = \Lambda'$.

Lean: `Langlands.LocalGL2.TameDatum.mem_J_iff_of_eq_basis`, `Langlands.LocalGL2.TameDatum.Λ_eq_of_eq_basis`

*Proof.* By Lemma 3.13.6 the two levels are equal, so $m = m'$ and $J = \iota_v(L^\times) U^m_{\mathfrak{A}} = J'$. Each $x \in J$ is a product $\iota_v(y) u$ with $y \in L^\times$ and $u \in U^m_{\mathfrak{A}}$. Then $\Lambda(x) = \xi(y) \Lambda(u)$ and $\Lambda'(x) = \xi(y) \Lambda'(u)$, by Lemma 3.13.7. $\square$

This is Proposition 3.13.8 again, in the form that the Lean proof below uses.

**Proposition 3.14.8 (types of isomorphic pairs are conjugate).** Let $p \ne 2$. Let $D$ and $D'$ be data for $(L/K, \xi)$ and $(L'/K, \xi')$, with bases $v$ and $v'$, and let $j : L \to L'$ be a $K$-isomorphism with $\xi = \xi' \circ j$. Then there is $h \in G$ that intertwines $\Lambda$ with $\Lambda'$ and satisfies $h \iota_v(y) h^{-1} = \iota_{v'}(j(y))$ for each $y \in L^\times$.

Lean: `Langlands.LocalGL2.TameDatum.exists_conj_of_iso`

*Proof.* Let $D_1 = D'^j$ be the transported datum of Proposition 3.13.3. It is a datum for $(L/K, \xi' \circ j) = (L/K, \xi)$, with basis $v_1 = j^{-1} v'$, and its group and character are $J'$ and $\Lambda'$. By Lemma 3.13.6, $D_1$ has the chain order $\mathfrak{A}$ of $D$, so $v$ is adapted to it. Let $D_2$ be the rebase of $D_1$ to the basis $v$, as in Proposition 3.13.5. Let $b$ be the change of basis from $v$ to $v_1$. Then $J_2 = b J' b^{-1}$ and $\Lambda_2(x) = \Lambda'(b^{-1} x b)$. The data $D$ and $D_2$ are data for one pair, with one chain order and one basis. By Theorem 3.13.19, `TypeCharUnitsAgree` holds, so $\Lambda$ and $\Lambda_2$ agree on $U^m_{\mathfrak{A}}$. Lemma 3.14.7 gives $J = J_2$ and $\Lambda = \Lambda_2$.

Put $h = b^{-1}$. Let $x \in J$. Then $x \in J_2$, so $h x h^{-1} = b^{-1} x b \in J'$, and $\Lambda'(h x h^{-1}) = \Lambda_2(x) = \Lambda(x)$. So $h$ intertwines $\Lambda$ with $\Lambda'$. By Lemma 3.13.4, part 1, $\iota_{v_1}(y) = b^{-1} \iota_v(y) b = h \iota_v(y) h^{-1}$. By Lemma 3.13.2, part 1, the matrix of $y$ in the basis $j^{-1} v'$ is the matrix of $j(y)$ in the basis $v'$, so $\iota_{v_1}(y) = \iota_{v'}(j(y))$. $\square$

**Definition 3.14.9 (the intertwining statements).** Let $p \ne 2$.
1. `TypeIntertwiningIso` for $K$ says: if $D$ and $D'$ are data for pairs $P$ and $Q$, and some $g \in G$ intertwines $\Lambda$ with $\Lambda'$, then $P \cong Q$.
2. `TypeIntertwiningConj` for $K$ says: under the same hypothesis, there are a $K$-isomorphism $j : L \to L'$ and an element $h \in G$ that intertwines $\Lambda$ with $\Lambda'$ and satisfies $h \iota_v(y) h^{-1} = \iota_{v'}(j(y))$ for each $y \in L^\times$.

Lean: `Langlands.LocalGL2.TypeIntertwiningIso`, `Langlands.LocalGL2.TypeIntertwiningConj`

The first statement is [BH06] 15.7 together with 20.2. The second says that intertwining types are conjugate, with their fields.

**Theorem 3.14.10 (the first reduction).** The statements `TypeIntertwiningIso` and `TypeIntertwiningConj` are equivalent for each $K$, and each of them implies `TypeRepInjective`.

Lean: `Langlands.LocalGL2.typeIntertwiningIso_iff_typeIntertwiningConj`, `Langlands.LocalGL2.typeRepInjective_of_typeIntertwiningIso`, `Langlands.LocalGL2.typeRepInjective_of_typeIntertwiningConj`

*Proof.* Assume `TypeIntertwiningIso`, and let $g$ intertwine $\Lambda$ with $\Lambda'$. Then the pairs are isomorphic by a $K$-isomorphism $j$ with $\xi = \xi' \circ j$, and Proposition 3.14.8 gives $h$. Conversely, Proposition 3.14.6 turns the $j$ and $h$ of `TypeIntertwiningConj` into an isomorphism of pairs. For the last claim, let $\pi_D \cong \pi_{D'}$. The group $J$ is open and $\Lambda$ has open kernel, so Proposition 3.14.3 gives an element that intertwines $\Lambda$ with $\Lambda'$, and `TypeIntertwiningIso` gives $P \cong Q$. $\square$

### The reduction to the normalizer

We now prove the first half of [BH06] 15.7 for two data: an intertwining element forces the same chain order and the same level, and it lies in the normalizer of the chain order. The two data have their own additive characters $\psi$, $\psi'$ and their own twisting characters $\chi$, $\chi'$. We use only test elements of determinant $1$. On them $\chi \circ \det$ and $\chi' \circ \det$ are trivial, so $\Lambda$ agrees with $\Lambda_0$ there, and $\Lambda_0$ is $\psi_\alpha$ on $U^m_{\mathfrak{A}}$.

**Lemma 3.14.11 (unipotent elements).** Let $c \in K$, $d \in K^\times$, $Y \in M_2(K)$ and $k \ge 1$.
1. $\det x_+(c) = \det x_-(c) = 1$, and $D(d) \, x_+(c) \, D(d)^{-1} = x_+(c d^{-1})$.
2. $\psi_Y(x_+(c)) = \psi(c Y_{21})$ and $\psi_Y(x_-(c)) = \psi(c Y_{12})$.
3. If $v_K(c) \ge b_k(1, 2)$, then $x_+(c) \in U^k_{\mathfrak{A}}$. If $v_K(c) \ge b_k(2, 1)$, then $x_-(c) \in U^k_{\mathfrak{A}}$.
4. $U^{2k}_{\mathfrak{J}} \subseteq U^k_{\mathfrak{M}}$, and $U^{k+1}_{\mathfrak{M}} \subseteq U^{2k+1}_{\mathfrak{J}}$ for each $k \ge 0$.

Lean: `Langlands.LocalGL2.det_upperGL`, `Langlands.LocalGL2.det_lowerGL`, `Langlands.LocalGL2.diagGL_mul_upperGL_mul_inv`, `Langlands.LocalGL2.psiAlphaFun_upperGL`, `Langlands.LocalGL2.psiAlphaFun_lowerGL`, `Langlands.LocalGL2.upperGL_mem_unitsFilt_of_one_le`, `Langlands.LocalGL2.lowerGL_mem_unitsFilt_of_one_le`, `Langlands.LocalGL2.unitsFilt_iwahori_le_maximal`, `Langlands.LocalGL2.unitsFilt_maximal_le_iwahori`

*Proof.* Part 1 is a product of $2 \times 2$ matrices. Part 2: $x_+(c) - 1 = c E_{12}$, and $\mathrm{tr}(Y E_{12}) = Y_{21}$. In the same way $\mathrm{tr}(Y E_{21}) = Y_{12}$. Part 3: the diagonal entries of $x_\pm(c) - 1$ are $0$, which lies in every $\mathfrak{p}_K^t$, and the bounds of $\mathfrak{P}^k_{\mathfrak{A}}$ are $\ge 0$ for $k \ge 1$, so $x_\pm(c) \in \mathfrak{A}^\times$. Part 4: for $\mathfrak{J}$ the bounds are $b_t(1, 1) = b_t(2, 2) = \lceil t/2 \rceil$, $b_t(1, 2) = \lceil (t-1)/2 \rceil$ and $b_t(2, 1) = \lceil (t+1)/2 \rceil$. For $t = 2k$ they are $k, k, k, k + 1$, all at least $k$, which are the bounds of $\mathfrak{P}^k_{\mathfrak{M}}$. For $t = 2k + 1$ they are $k + 1, k + 1, k, k + 1$, all at most $k + 1$, which are the bounds of $\mathfrak{P}^{k+1}_{\mathfrak{M}}$. $\square$

Exercise 48 shows that the two inclusions of part 4 are the best ones.

**Lemma 3.14.12 (a comparison of two characters).** Let $\psi$ and $\psi'$ be characters of $K$ of level one, let $r \in \mathbb{Z}$, $b \in \mathfrak{p}_K^r$ and $a \in K$. If $\psi'(c a) = \psi(c b)$ for each $c \in \mathfrak{p}_K^{1-r}$, then $a \in \mathfrak{p}_K^r$.

Lean: `Langlands.LocalGL2.mem_ordBall_of_forall_psi_mul_eq`

*Proof.* For $c \in \mathfrak{p}_K^{1-r}$ we have $c b \in \mathfrak{p}_K$, so $\psi(c b) = 1$. Thus $\psi'$ is trivial on $a \mathfrak{p}_K^{1-r}$. If $a \ne 0$, this set is the ideal $\mathfrak{p}_K^{v_K(a) + 1 - r}$. A character of level one is trivial on $\mathfrak{p}_K$ and not on $\mathcal{O}_K$, so $v_K(a) + 1 - r \ge 1$. $\square$

The next lemma is the place where the minimality of $\alpha$ enters. It is the last step of the proof of Theorem 3.9.22, for any off-diagonal entry.

**Lemma 3.14.13 (the off-diagonal entries of a conjugate of a minimal element).** Let $v$ be a basis of $E$ adapted to $\mathfrak{A}$, let $\alpha \in E$ be minimal of level $n$ with matrix in $\mathfrak{P}^{-n}_{\mathfrak{A}}$, and let $a \in \mathfrak{K}_{\mathfrak{A}}$. Put $\gamma = a^{-1} \alpha a$. For $i \ne j$, the entry $\gamma_{ij}$ does not lie in $\mathfrak{p}_K^{b_{1-n}(i, j)}$.

Lean: `Langlands.LocalGL2.conj_apply_not_mem_ordBall`, `Langlands.LocalGL2.mul_sub_smul_one_apply_self`

*Proof.* The matrix $\gamma$ lies in $\mathfrak{P}^{-n}_{\mathfrak{A}}$ by Proposition 3.9.2, part 3. So $v_K(\gamma_{jj}) \ge b_{-n}(j, j)$, the least $t$ with $-n \le e t$. Since $e(E|K) = e_{\mathfrak{A}}$, this says $\gamma_{jj} \in \mathfrak{p}_E^{-n}$. By the minimality, $v_E(\alpha - \gamma_{jj}) = -n$ (Proposition 3.9.10, part 3). So $(\alpha - \gamma_{jj})^{-1} \in \mathfrak{p}_E^n$, and its matrix lies in $\mathfrak{P}^n_{\mathfrak{A}}$ by Proposition 3.9.7. Put $\delta = \gamma - \gamma_{jj} = a^{-1}(\alpha - \gamma_{jj}) a$. Then $\delta^{-1} = a^{-1}(\alpha - \gamma_{jj})^{-1} a \in \mathfrak{P}^n_{\mathfrak{A}}$, again by Proposition 3.9.2, part 3. The entry $\delta_{jj}$ is $0$ and $\delta_{ij} = \gamma_{ij}$, so
$$1 = (\delta^{-1} \delta)_{jj} = (\delta^{-1})_{ji} \, \gamma_{ij}.$$
If $v_K(\gamma_{ij}) \ge b_{1-n}(i, j)$, the right side has valuation at least $b_n(j, i) + b_{1-n}(i, j) = 1$, by the duality of the bounds. This is a contradiction. $\square$

Exercise 50 checks the lemma on the datum of Example 3.9.27, shows that the bound is sharp, and shows that the minimality cannot be omitted.

**Proposition 3.14.14 (the core computation).** Let $v$ be adapted to $\mathfrak{A}$, let $\alpha \in E$ be minimal of level $n$, and let $\psi$ have level one. Let $1 \le m \le n$ and $1 \le k_0 \le n + 1$, and let $g \in G$. Assume that $\psi_\alpha(g x g^{-1}) = 1$ for each $x \in U^{k_0}_{\mathfrak{A}}$ with $\det x = 1$ and $g x g^{-1} \in U^m_{\mathfrak{A}}$. Then $k_0 = n + 1$ and $g \in \mathfrak{K}_{\mathfrak{A}}$.

Lean: `Langlands.LocalGL2.eq_and_ord_eq_zero_of_forall_psiAlphaFun`, `Langlands.LocalGL2.eq_and_mem_normalizer_of_forall_psiAlphaFun`

*Proof.* By Lemma 3.9.21, $g = a D(d) b$ with $a, b \in \mathfrak{K}_{\mathfrak{A}}$ and $v_K(d) \ge 0$. We show that $k_0 = n + 1$ and $v_K(d) = 0$. Then $D(d) \in \mathfrak{A}^\times$ and $g \in \mathfrak{K}_{\mathfrak{A}}$.

Put $\gamma = a^{-1} \alpha a$ and $N = \max(b_{k_0}(1, 2), \, b_m(1, 2) + v_K(d))$. Let $c \in \mathfrak{p}_K^N$, and take the test element $x = b^{-1} x_+(c) b$. By Lemma 3.14.11, part 3, $x_+(c) \in U^{k_0}_{\mathfrak{A}}$, and since $b$ normalizes $U^{k_0}_{\mathfrak{A}}$, also $x \in U^{k_0}_{\mathfrak{A}}$. Its determinant is $1$. By Lemma 3.14.11, part 1,
$$g x g^{-1} = a D(d) x_+(c) D(d)^{-1} a^{-1} = a \, x_+(c d^{-1}) \, a^{-1},$$
and $v_K(c d^{-1}) \ge b_m(1, 2)$, so $g x g^{-1} \in U^m_{\mathfrak{A}}$. The hypothesis, Lemma 3.9.4, part 3, and Lemma 3.14.11, part 2, give
$$1 = \psi_\alpha(a \, x_+(c d^{-1}) \, a^{-1}) = \psi_\gamma(x_+(c d^{-1})) = \psi(c \, d^{-1} \gamma_{21}).$$
This holds for every $c \in \mathfrak{p}_K^N$. Since $\psi$ has level one, $d^{-1} \gamma_{21} \in \mathfrak{p}_K^{1-N}$, that is, $v_K(\gamma_{21}) \ge 1 - N + v_K(d)$. By Lemma 3.14.13 with $(i, j) = (2, 1)$,
$$1 - N + v_K(d) < b_{1-n}(2, 1).$$
Now we compare with the bounds. Since $1 - n \le 1 - m$, the duality gives $b_{1-n}(2, 1) \le b_{1-m}(2, 1) = 1 - b_m(1, 2)$. If $N = b_m(1, 2) + v_K(d)$, the inequality reads $1 - b_m(1, 2) < b_{1-n}(2, 1)$, which is false. So $N = b_{k_0}(1, 2)$, and $1 - b_{k_0}(1, 2) + v_K(d) < b_{1-n}(2, 1)$. If $k_0 \le n$, the same argument gives $b_{1-n}(2, 1) \le 1 - b_{k_0}(1, 2)$, so $v_K(d) < 0$, which is false. So $k_0 = n + 1$. Then $1 - n \le 1 - k_0 + e$, and the first rule of the bounds gives $b_{1-n}(2, 1) \le b_{1-k_0}(2, 1) + 1 = 2 - b_{k_0}(1, 2)$. So $v_K(d) < 1$, and $v_K(d) = 0$. $\square$

For $k_0 = m$ and $\psi_\alpha$ in place of the constant $1$, this is the argument of Theorem 3.9.22. The new point is the parameter $k_0$: the hypothesis is only on the deep group $U^{k_0}_{\mathfrak{A}}$, and the conclusion says how deep it can be.

**Lemma 3.14.15 (the character on elements of determinant 1).** Let $D$ be a datum of level $n$, with chain order $\mathfrak{A}$.
1. $[n/2] + 1 = (n + 1)/2 = m$.
2. If $x \in U^m_{\mathfrak{A}}$ and $\det x = 1$, then $\Lambda(x) = \psi_\alpha(x)$.
3. If $x \in U^{n+1}_{\mathfrak{A}}$ and $\det x = 1$, then $\Lambda(x) = 1$.
4. Let $D'$ be a second datum, of level $n'$, with chain order $\mathfrak{A}'$, and let $g$ intertwine $\Lambda$ with $\Lambda'$. Let $k_0$ satisfy $U^{k_0}_{\mathfrak{A}'} \subseteq U^{n+1}_{\mathfrak{A}}$. Then $\psi'_{\alpha'}(g x g^{-1}) = 1$ for each $x \in U^{k_0}_{\mathfrak{A}'}$ with $\det x = 1$ and $g x g^{-1} \in U^{m'}_{\mathfrak{A}'}$.

Lean: `Langlands.LocalGL2.TameDatum.level_div_two_add_one`, `Langlands.LocalGL2.TameDatum.Λ_eq_psiAlphaFun`, `Langlands.LocalGL2.TameDatum.Λ_eq_one_of_mem_unitsFilt`, `Langlands.LocalGL2.TameDatum.psiAlphaFun_eq_one_of_intertwinesWith`

*Proof.* Part 1 holds since $n$ is odd. Part 2: $\Lambda(x) = \Lambda_0(x) \chi(\det x) = \Lambda_0(x)$, and $\Lambda_0 = \psi_\alpha$ on $U^m_{\mathfrak{A}}$ by the definition of a type. Part 3: $U^{n+1}_{\mathfrak{A}} \subseteq U^m_{\mathfrak{A}}$, and $\psi_\alpha$ is trivial on $U^{n+1}_{\mathfrak{A}}$ by Lemma 3.9.4, part 1. Part 4: $x \in U^{n+1}_{\mathfrak{A}} \subseteq J$ and $g x g^{-1} \in U^{m'}_{\mathfrak{A}'} \subseteq J'$, and both have determinant $1$. The intertwining and parts 2 and 3 give $\psi'_{\alpha'}(g x g^{-1}) = \Lambda'(g x g^{-1}) = \Lambda(x) = 1$. $\square$

Part 4 has the form of the hypothesis of Proposition 3.14.14, for the datum $D'$. The proof of the same chain order case is now short.

**Proposition 3.14.16 (one chain order, [BH06] 15.7).** Let $D$ and $D'$ be data with the same chain order $\mathfrak{A}$. If $g$ intertwines $\Lambda$ with $\Lambda'$, then $n' = n$ and $g \in \mathfrak{K}_{\mathfrak{A}}$.

Lean: `Langlands.LocalGL2.TameDatum.level_eq_and_mem_normalizer_of_A_eq`

*Proof.* First let $n \le n'$. Apply Lemma 3.14.15, part 4, with $k_0 = n + 1$. The inclusion $U^{n+1}_{\mathfrak{A}} \subseteq U^{n+1}_{\mathfrak{A}}$ is trivial. So the hypothesis of Proposition 3.14.14 holds for $\alpha'$, of level $n'$, with $m = m'$ and $k_0 = n + 1 \le n' + 1$. It gives $n + 1 = n' + 1$ and $g \in \mathfrak{K}_{\mathfrak{A}}$. Now let $n > n'$. By Lemma 3.14.2, $g^{-1}$ intertwines $\Lambda'$ with $\Lambda$. The same argument with the roles exchanged, and $k_0 = n' + 1 \le n$, gives $n' + 1 = n + 1$, a contradiction. $\square$

Two data with different chain orders need more care, because the filtrations of $\mathfrak{M}$ and $\mathfrak{J}$ are not comparable step by step. Lemma 3.14.11, part 4, compares them up to a factor $2$, and Proposition 3.14.14 then leaves two border cases.

**Lemma 3.14.17 (the two border cases).** Let $D$ be a datum of level $n$ for $\mathfrak{M}$ and $D'$ a datum of level $n'$ for $\mathfrak{J}$, and let $g$ intertwine $\Lambda$ with $\Lambda'$.
1. If $n' = 2n + 1$, then $g \notin \mathfrak{K}_{\mathfrak{J}}$.
2. If $n' = 2n - 1$, then $g^{-1} \notin \mathfrak{K}_{\mathfrak{M}}$.

Lean: `Langlands.LocalGL2.TameDatum.false_of_maximal_iwahori_of_eq_two_mul_add_one`, `Langlands.LocalGL2.TameDatum.false_of_maximal_iwahori_of_add_one_eq_two_mul`

*Proof.* Part 1. Suppose $g \in \mathfrak{K}_{\mathfrak{J}}$. Here $m' = n + 1$. Let $c \in \mathfrak{p}_K^{n+1}$. The test element is $x_-(c)$. Since $b_m(2, 1) = m \le n + 1$ for $\mathfrak{M}$, it lies in $U^m_{\mathfrak{M}}$. Since $b_{n+1}(2, 1) = \lceil (n+2)/2 \rceil \le n + 1$ for $\mathfrak{J}$, it lies in $U^{n+1}_{\mathfrak{J}}$, and so does $g x_-(c) g^{-1}$. Both have determinant $1$. Let $Y$ be the matrix of $\alpha$ and $\gamma' = g^{-1} \alpha' g$. The intertwining, Lemma 3.14.15, part 2, and Lemma 3.14.11, part 2, give
$$\psi'(c \gamma'_{12}) = \Lambda'(g x_-(c) g^{-1}) = \Lambda(x_-(c)) = \psi(c Y_{12}).$$
Here $Y \in \mathfrak{P}^{-n}_{\mathfrak{M}}$, so $Y_{12} \in \mathfrak{p}_K^{-n}$. Lemma 3.14.12 with $r = -n$ gives $\gamma'_{12} \in \mathfrak{p}_K^{-n}$. But Lemma 3.14.13 for $\alpha'$, of level $2n + 1$, and $a = g$ says $\gamma'_{12} \notin \mathfrak{p}_K^{b}$ with $b = b_{-2n}(1, 2)$, the least $t$ with $-2n \le 2t + 1$. So $b = -n$, a contradiction.

Part 2. Suppose $g^{-1} \in \mathfrak{K}_{\mathfrak{M}}$. Here $m' = n$. Let $c \in \mathfrak{p}_K^n$. The test element is $x = g^{-1} x_+(c) g$. Since $x_+(c) \in U^n_{\mathfrak{M}} \subseteq U^m_{\mathfrak{M}}$ and $g^{-1}$ normalizes $\mathfrak{M}$, $x \in U^m_{\mathfrak{M}}$. And $g x g^{-1} = x_+(c)$ lies in $U^n_{\mathfrak{J}}$, since $b_n(1, 2) = \lceil (n-1)/2 \rceil \le n$ for $\mathfrak{J}$. Both have determinant $1$. Let $Y'$ be the matrix of $\alpha'$ and $\gamma = g \alpha g^{-1}$. As in part 1,
$$\psi'(c Y'_{21}) = \Lambda'(x_+(c)) = \Lambda(x) = \psi_\alpha(g^{-1} x_+(c) g) = \psi(c \gamma_{21}).$$
Here $Y' \in \mathfrak{P}^{1 - 2n}_{\mathfrak{J}}$, and $b_{1-2n}(2, 1)$ is the least $t$ with $1 - 2n \le 2t - 1$, that is $1 - n$. So $Y'_{21} \in \mathfrak{p}_K^{1-n}$, and Lemma 3.14.12 with the roles of $\psi$ and $\psi'$ exchanged and $r = 1 - n$ gives $\gamma_{21} \in \mathfrak{p}_K^{1-n}$. But Lemma 3.14.13 for $\alpha$ and $a = g^{-1}$ says $\gamma_{21} \notin \mathfrak{p}_K^{b_{1-n}(2, 1)} = \mathfrak{p}_K^{1-n}$. $\square$

**Proposition 3.14.18 (no intertwining between the two chain orders, [BH06] 15.7).** Let $D$ be a datum for $\mathfrak{M}$ and $D'$ a datum for $\mathfrak{J}$. No $g \in G$ intertwines $\Lambda$ with $\Lambda'$.

Lean: `Langlands.LocalGL2.TameDatum.false_of_maximal_iwahori`

*Proof.* Let $n$ and $n' = 2k' + 1$ be the levels, and suppose that $g$ intertwines $\Lambda$ with $\Lambda'$. First let $n' \ge 2n + 1$. By Lemma 3.14.11, part 4, $U^{2(n+1)}_{\mathfrak{J}} \subseteq U^{n+1}_{\mathfrak{M}}$. Lemma 3.14.15, part 4, with $k_0 = 2n + 2 \le n' + 1$ and Proposition 3.14.14 for $\alpha'$ give $2n + 2 = n' + 1$ and $g \in \mathfrak{K}_{\mathfrak{J}}$. This contradicts Lemma 3.14.17, part 1. Now let $n' < 2n + 1$, so $k' \le n - 1$. By Lemma 3.14.11, part 4, $U^{k'+2}_{\mathfrak{M}} \subseteq U^{2k'+3}_{\mathfrak{J}} \subseteq U^{n'+1}_{\mathfrak{J}}$. The element $g^{-1}$ intertwines $\Lambda'$ with $\Lambda$, so Lemma 3.14.15, part 4, with $k_0 = k' + 2 \le n + 1$ and Proposition 3.14.14 for $\alpha$ give $k' + 2 = n + 1$ and $g^{-1} \in \mathfrak{K}_{\mathfrak{M}}$. Then $n' = 2n - 1$, and this contradicts Lemma 3.14.17, part 2. $\square$

**Theorem 3.14.19 (intertwining data, [BH06] 15.7).** Let $D$ and $D'$ be tame data. If some $g \in G$ intertwines $\Lambda$ with $\Lambda'$, then $\mathfrak{A}' = \mathfrak{A}$, $n' = n$ and $g \in \mathfrak{K}_{\mathfrak{A}}$.

Lean: `Langlands.LocalGL2.TameDatum.A_eq_and_level_eq_of_intertwinesWith`

*Proof.* If the chain orders are equal, this is Proposition 3.14.16. If $\mathfrak{A} = \mathfrak{M}$ and $\mathfrak{A}' = \mathfrak{J}$, Proposition 3.14.18 shows that there is no such $g$. If $\mathfrak{A} = \mathfrak{J}$ and $\mathfrak{A}' = \mathfrak{M}$, apply Proposition 3.14.18 to $g^{-1}$, which intertwines $\Lambda'$ with $\Lambda$ by Lemma 3.14.2. $\square$

In particular the chain order and the level of a datum are invariants of the representation $\pi_D$. By Lemma 3.13.6 the chain order is $\mathfrak{M}$ exactly when $L/K$ is unramified. So the theorem already shows that an isomorphism $\pi_D \cong \pi_{D'}$ forces $L$ and $L'$ to be both unramified or both ramified, and their minimal parts to have the same level.

**Definition 3.14.20 (the statement in the normalizer).** Let $p \ne 2$. The statement `TypeIntertwiningNormalizerIso` for $K$ says: let $D$ and $D'$ be data for pairs $P$ and $Q$ with the same chain order $\mathfrak{A}$ and the same level, and let $g \in \mathfrak{K}_{\mathfrak{A}}$ intertwine $\Lambda$ with $\Lambda'$. Then $P \cong Q$.

Lean: `Langlands.LocalGL2.TypeIntertwiningNormalizerIso`

**Corollary 3.14.21 (the reduction to the normalizer).** The statements `TypeIntertwiningIso` and `TypeIntertwiningNormalizerIso` are equivalent for each $K$. So `TypeIntertwiningNormalizerIso` implies `TypeRepInjective`.

Lean: `Langlands.LocalGL2.typeIntertwiningIso_iff_typeIntertwiningNormalizerIso`, `Langlands.LocalGL2.typeRepInjective_of_typeIntertwiningNormalizerIso`

*Proof.* The statement `TypeIntertwiningNormalizerIso` is `TypeIntertwiningIso` with three more hypotheses, and Theorem 3.14.19 proves these hypotheses from the intertwining. The last claim is Theorem 3.14.10. $\square$

**Example 3.14.22 (the two pairs of level 1).** Let $K = \mathbb{Q}_p$ with $p$ odd. Let $D$ be the datum of the unramified pair of Example 3.9.26, with $\mathfrak{A} = \mathfrak{M}$, the basis $(1, u)$, $n = 1$ and $\alpha = p^{-1} \beta$, and let $D'$ be the datum of the ramified pair of Example 3.9.27, with $\mathfrak{A}' = \mathfrak{J}$, $n' = 1$ and the matrix $\frac12 \Pi_{\mathfrak{J}}^{-1}$ of $\alpha'$. Take $\chi = \chi' = 1$, and the same $\psi$. This is the case $n' = 2n - 1$ of Lemma 3.14.17, part 2. Theorem 3.14.19 says that no $g$ intertwines $\Lambda$ with $\Lambda'$. We check this by hand for $g = 1$. Let $c \in p\mathbb{Z}_p$. Then $x_+(c) \in U^1_{\mathfrak{M}} \cap U^1_{\mathfrak{J}} \subseteq J \cap J'$. The matrix of $\alpha'$ has $(2, 1)$ entry $\frac12$, so $\Lambda'(x_+(c)) = \psi(c/2) = 1$, since $c/2 \in p\mathbb{Z}_p$. Write $\beta = b_1 + b_2 u$ with $b_1, b_2 \in \mathbb{Z}_p$. The first column of the matrix of $\beta$ is $(b_1, b_2)$, so the $(2, 1)$ entry of the matrix of $\alpha$ is $p^{-1} b_2$. The residue class of $\beta$ is not in $\mathbb{F}_p$, so $b_2$ is a unit. Then $\Lambda(x_+(c)) = \psi(c b_2 / p)$. As $c$ runs over $p\mathbb{Z}_p$, $c b_2 / p$ runs over $\mathbb{Z}_p$, where $\psi$ is not trivial. So $\Lambda(x_+(c)) \ne \Lambda'(x_+(c))$ for some $c$, and $g = 1$ does not intertwine. The two representations $\pi_D$ and $\pi_{D'}$ are not isomorphic, by Proposition 3.14.3.

### One field and one basis

After Corollary 3.14.21 we have two data with the same chain order and the same level, and an intertwining element $g \in \mathfrak{K}_{\mathfrak{A}}$. Two things remain: a $K$-isomorphism $L \cong L'$, and the comparison of $\xi$ with $\xi'$. The library proves the first for the maximal order, and it reduces the rest to two statements on one chain order.

**Lemma 3.14.23 (adapted bases).** Let $v$ and $v'$ be bases of $E$ adapted to $\mathfrak{A}$. The change of basis $b$ from $v$ to $v'$ lies in $\mathfrak{K}_{\mathfrak{A}}$. Two data for pairs with the same field $L$ have the same chain order.

Lean: `Langlands.LocalGL2.basisChangeGL_mem_normalizer`, `Langlands.LocalGL2.TameDatum.A_eq_of_field`

*Proof.* By Lemma 3.13.4, part 3, with $n = 0$, $b \mathfrak{A} b^{-1} = \mathfrak{A}$. For the second claim, the period of the chain order of a datum is $e(L|K)$ by Definition 3.9.6, and the period determines the chain order. $\square$

**Proposition 3.14.24 (the maximal order has one field).** Let $D$ and $D'$ be data for $(L/K, \xi)$ and $(L'/K, \xi')$, both for $\mathfrak{M}$. Then $L = L'$ as subfields of $\bar K$.

Lean: `Langlands.LocalGL2.TameDatum.isUnramifiedExt_of_maximal`, `Langlands.LocalGL2.TameDatum.eq_of_maximal`, `Langlands.LocalGL2.uniqueUnramifiedQuad_holds`

*Proof.* The basis $v$ is adapted to $\mathfrak{M}$, so $e(L|K) = e_{\mathfrak{M}} = 1$ by Definition 3.9.6, and $L/K$ is unramified. In the same way $L'/K$ is unramified. By Theorem 3.12.33, `UniqueUnramifiedQuad` holds, so $L = L'$. $\square$

For the comparison of the characters, the easy case is an intertwining element in $J$.

**Lemma 3.14.25 (the final step for one basis).** Let $D$ and $D'$ be data for $(L/K, \xi)$ and $(L/K, \xi')$ with the same basis $v$. If an element $g \in J$ intertwines $\Lambda$ with $\Lambda'$, then $\xi = \xi'$.

Lean: `Langlands.LocalGL2.TameDatum.eq_of_intertwinesWith_of_mem_J`

*Proof.* Let $y \in L^\times$ and put $x = g^{-1} \iota_v(y) g$. Then $x \in J$, since $g$ and $\iota_v(y)$ lie in $J$, and $g x g^{-1} = \iota_v(y) \in J'$. The intertwining gives $\Lambda'(\iota_v(y)) = \Lambda(x)$. Since $\mathbb{C}^\times$ is commutative, $\Lambda(x) = \Lambda(g)^{-1} \Lambda(\iota_v(y)) \Lambda(g) = \Lambda(\iota_v(y))$. By Lemma 3.13.7, $\xi'(y) = \xi(y)$. $\square$

**Definition 3.14.26 (the two remaining statements).** Let $p \ne 2$.
1. `TypeNormalizerRamifiedField` for $K$ says: let $D$ and $D'$ be data for $(L/K, \xi)$ and $(L'/K, \xi')$, both for $\mathfrak{J}$ and with the same level, and let $g \in \mathfrak{K}_{\mathfrak{J}}$ intertwine $\Lambda$ with $\Lambda'$. Then $L$ and $L'$ are $K$-isomorphic.
2. `TypeNormalizerSameBasisIso` for $K$ says: let $L/K$ be separable quadratic, and let $D$ and $D'$ be data for $(L/K, \xi)$ and $(L/K, \xi')$ with the same chain order $\mathfrak{A}$, the same basis and the same level. If some $g \in \mathfrak{K}_{\mathfrak{A}}$ intertwines $\Lambda$ with $\Lambda'$, then $\xi = \xi' \circ \sigma$ for a $K$-automorphism $\sigma$ of $L$.

Lean: `Langlands.LocalGL2.TypeNormalizerRamifiedField`, `Langlands.LocalGL2.TypeNormalizerSameBasisIso`

Both are parts of [BH06] 15.7 and 20.2. The first is the field step for the Iwahori order, where Proposition 3.14.24 does not apply: for $p \ne 2$ there are two ramified quadratic extensions of $K$ up to isomorphism, $K(\sqrt{\varpi})$ and $K(\sqrt{\epsilon \varpi})$ with $\epsilon$ a unit that is not a square. The second is the comparison of the characters.

**Proposition 3.14.27 (the field step).** Assume `TypeNormalizerRamifiedField` for $K$, and let $p \ne 2$. Let $D$ and $D'$ be data for $(L/K, \xi)$ and $(L'/K, \xi')$ with the same chain order and the same level, and let $g \in \mathfrak{K}_{\mathfrak{A}}$ intertwine $\Lambda$ with $\Lambda'$. Then $L$ and $L'$ are $K$-isomorphic.

Lean: `Langlands.LocalGL2.TameDatum.nonempty_algEquiv_of_intertwinesWith`

*Proof.* For $\mathfrak{A} = \mathfrak{M}$, Proposition 3.14.24 gives $L = L'$. For $\mathfrak{A} = \mathfrak{J}$, this is the hypothesis. $\square$

**Proposition 3.14.28 (the rebase step).** Assume `TypeNormalizerSameBasisIso` for $K$, and let $p \ne 2$. Let $D$ and $D'$ be data for $(L/K, \xi)$ and $(L/K, \xi')$ with the same level, and let $g \in \mathfrak{K}_{\mathfrak{A}}$ intertwine $\Lambda$ with $\Lambda'$. Then $\xi = \xi' \circ \sigma$ for a $K$-automorphism $\sigma$ of $L$.

Lean: `Langlands.LocalGL2.TameDatum.exists_eq_comp_of_sameBasisIso`

*Proof.* By Lemma 3.14.23, $\mathfrak{A}' = \mathfrak{A}$, so the basis $v$ of $D$ is adapted to $\mathfrak{A}'$. Let $D_2$ be the rebase of $D'$ to $v$, as in Proposition 3.13.5, and let $b$ be the change of basis from $v$ to $v'$. Then $J_2 = b J' b^{-1}$ and $\Lambda_2(y) = \Lambda'(b^{-1} y b)$, and $b \in \mathfrak{K}_{\mathfrak{A}}$ by Lemma 3.14.23. So $b g \in \mathfrak{K}_{\mathfrak{A}}$. It intertwines $\Lambda$ with $\Lambda_2$: if $x \in J$ and $(b g) x (b g)^{-1} \in J_2$, then $g x g^{-1} \in J'$, and
$$\Lambda_2((b g) x (b g)^{-1}) = \Lambda'(g x g^{-1}) = \Lambda(x).$$
The data $D$ and $D_2$ have the same chain order, the same basis and the same level, and $D_2$ is a datum for $(L/K, \xi')$. `TypeNormalizerSameBasisIso` gives $\sigma$. $\square$

**Theorem 3.14.29 (the reduction of `TypeRepInjective`).** The statements `TypeNormalizerRamifiedField` and `TypeNormalizerSameBasisIso` imply `TypeIntertwiningNormalizerIso`, and so `TypeRepInjective`, for each $K$.

Lean: `Langlands.LocalGL2.typeIntertwiningNormalizerIso_of_ramifiedField_of_sameBasisIso`, `Langlands.LocalGL2.typeRepInjective_of_ramifiedField_of_sameBasisIso`

*Proof.* Let $p \ne 2$, and let $D$, $D'$ and $g$ be as in Definition 3.14.20. Proposition 3.14.27 gives a $K$-isomorphism $j : L \to L'$. Let $D_1 = D'^j$ be the transported datum of Proposition 3.13.3. It is a datum for $(L/K, \xi' \circ j)$ with the group $J'$ and the character $\Lambda'$, and its level is the level of $D'$, which is $n$. So $g$ intertwines $\Lambda$ with $\Lambda_1 = \Lambda'$. Proposition 3.14.28 gives $\sigma$ with $\xi = (\xi' \circ j) \circ \sigma$. So $j \circ \sigma : L \to L'$ is a $K$-isomorphism with $\xi = \xi' \circ (j \circ \sigma)$, and $P \cong Q$. The last claim is Corollary 3.14.21. $\square$

So `TypeRepInjective` now rests on two statements on one chain order, with an intertwining element in $\mathfrak{K}_{\mathfrak{A}}$. The two remarks below give the proofs that the library intends, after [BH06], sections 13, 15 and 20. We give the main steps. Neither proof is formalized.

**Remark 3.14.30 (the intended proof of `TypeNormalizerRamifiedField`).** Let $D$, $D'$ and $g \in \mathfrak{K}_{\mathfrak{J}}$ be as in Definition 3.14.26, part 1, and let $Y$, $Y'$ be the matrices of $\alpha$, $\alpha'$.
1. Two characters of $K$ of level one differ by a unit: $\psi'(x) = \psi(u x)$ with $u \in \mathcal{O}_K^\times$. This holds because the characters of $K$ are the $x \mapsto \psi(a x)$ with $a \in K$, and the level fixes $v_K(a) = 0$.
2. For $x = 1 + X \in U^m_{\mathfrak{J}}$ with $\det x = 1$, the element $g x g^{-1}$ lies in $U^m_{\mathfrak{J}}$, and Lemma 3.14.15, part 2, turns the intertwining into $\psi(\mathrm{tr}((u g^{-1} Y' g - Y) X)) = 1$. Modulo $\mathfrak{P}^{n+1}_{\mathfrak{J}}$, where both characters are trivial, the $X$ that occur are the matrices of trace $0$ in $\mathfrak{P}^m_{\mathfrak{J}}$, since $\det(1 + X) = 1 + \mathrm{tr}(X) + \det(X)$ and $\det(X) \in \mathfrak{p}_K^{m}$.
3. Trace duality for the matrices of trace $0$, a variant of Proposition 3.9.2, part 4, then gives $u g^{-1} Y' g - Y \in K + \mathfrak{P}^{1-m}_{\mathfrak{J}}$.
4. Put $\alpha_0 = \alpha - \mathrm{tr}_{L/K}(\alpha)/2$ and $\delta = \alpha_0^2$. Then $\delta \in K$ and $L = K(\sqrt{\delta})$. The element $\alpha_0$ is again minimal of level $n$, so $v_L(\delta) = -2n$. Define $\alpha'_0$ and $\delta'$ in the same way. Step 3 holds for $\alpha_0$ and $\alpha'_0$, and taking traces removes the scalar: $\beta = u g^{-1} Y'_0 g$ satisfies $\beta = Y_0 + Z$ with $Z \in \mathfrak{P}^{1-m}_{\mathfrak{J}}$. Square both sides: $u^2 \delta' - \delta = Y_0 Z + Z Y_0 + Z^2$ is a scalar in $\mathfrak{P}^{1-m-n}_{\mathfrak{J}}$. Since $1 - m - n > -2n$, the quotient $u^2 \delta' / \delta$ lies in $1 + \mathfrak{p}_K$.
5. For $p \ne 2$, each element of $1 + \mathfrak{p}_K$ is a square, by Hensel's lemma. So $\delta'$ and $\delta$ differ by a square, and $L = K(\sqrt{\delta}) = K(\sqrt{\delta'}) = L'$.

The library lacks step 1, the statement that two characters of level one differ by a unit, and step 3, trace duality on the matrices of trace $0$. The rest is algebra in $M_2(K)$ of the kind done in Section 3.9. Exercise 52 does steps 4 and 5 for the two ramified extensions of $\mathbb{Q}_p$.

**Remark 3.14.31 (the intended proof of `TypeNormalizerSameBasisIso`).** Let $D$, $D'$ and $g$ be as in Definition 3.14.26, part 2, with one field $L$ and one basis $v$. The congruence of Remark 3.14.30, step 3, holds for both chain orders. It gives $c \in K$ such that $\beta = u \alpha' - c \in L$ satisfies $g^{-1} \beta g - \alpha \in \mathfrak{P}^{1-m}_{\mathfrak{A}}$. Let $\bar\alpha$ be the conjugate of $\alpha$ over $K$. Since $\alpha$ is minimal, $v_L(\alpha - \bar\alpha) = -n$. The two elements $\beta$ and $g^{-1} \beta g$ have the same characteristic polynomial, and this polynomial is close to the characteristic polynomial of $\alpha$. So $\beta$ is close to $\alpha$ or to $\bar\alpha$, in the sense $v_L(\beta - \alpha) \ge 1 - m$ or $v_L(\beta - \bar\alpha) \ge 1 - m$. In the first case, $g^{-1} \alpha g - \alpha = g^{-1}(\alpha - \beta) g + (g^{-1} \beta g - \alpha) \in \mathfrak{P}^{1-m}_{\mathfrak{A}} = \mathfrak{P}^{m-n}_{\mathfrak{A}}$, since $2m = n + 1$. Lemma 3.9.19 with $s = m$ (`Langlands.LocalGL2.IsAdapted.mem_jGroup_iff_conj_sub_mem`) gives $g \in L^\times U^m_{\mathfrak{A}} = J$, and Lemma 3.14.25 gives $\xi = \xi'$, so $\sigma = 1$ works. In the second case, transport $D'$ along the conjugation $\tau$ of $L/K$ by Proposition 3.13.3 and rebase it to $v$ by Proposition 3.13.5. The new element is $\tau(\alpha')$, which is close to $\alpha$, and the first case gives $\xi = \xi' \circ \tau$.

The two remarks share their first steps, and the library would prove the congruence of step 3 once. The first case of Remark 3.14.31 is already formal: it is Lemma 3.9.19 followed by Lemma 3.14.25. The data $D$ and $D \otimes \phi$, for an unramified character $\phi$ of $K^\times$, show why the elements of determinant $1$ do not suffice for the second statement. The two characters $\Lambda$ and $\Lambda \cdot (\phi \circ \det)$ agree on all elements of determinant $1$ of $J$, but they differ on $\iota_v(L^\times)$ when $\phi_L \ne 1$. Lemma 3.14.25 uses exactly these elements.

### The zeta integral of a character of the determinant

We now prove fact 5 of Definition 3.11.31. Let $\chi$ be a smooth character of $K^\times$ and let $\theta = (\chi |\cdot|^{1/2}) \circ \det$, a character of $G$ on the space $\mathbb{C}$. Recall the three clauses of `IsGJLFactor` from Section 3.11, and put $X = q^{-s}$. For a function $\varphi$ on $K$ and a character $\chi$ we write $Z(\varphi, \chi, s) = \int_K \varphi(y) \chi(y) |y|^{s-1} \, d\mu(y)$ for Tate's integral of Section 3.2, and $L(s, \chi)$ for `Langlands.LocalGL1.charLFactor`.

**Lemma 3.14.32 (the zeta integral of $\theta$).** Let $\Phi$ be a Schwartz-Bruhat function on $M_2(K)$, $v \in \mathbb{C}$ and $\lambda$ a linear form on $\mathbb{C}$. The zeta integral of $\Phi$ and the coefficient $f(g) = \lambda(\theta(g) v)$ is
$$Z(\Phi, s, f) = \lambda(v) \int_{M_2(K)} \Phi(x) \, \chi(\det x) \, |\det x|^{s-1} \, dx.$$

Lean: `Langlands.LocalGL2.plRep`, `Langlands.LocalGL2.pl_rep_apply`, `Langlands.LocalGL2.pl_sqrt_mul_cpow`, `Langlands.LocalGL2.pl_gjZeta_eq`

*Proof.* The integrand of `Langlands.gjZeta` is $\Phi(x) f(x) |\det x|^{s + 1/2 - 2}$, and $f(x) = \chi(\det x) |\det x|^{1/2} \lambda(v)$. For $r > 0$, $r^{1/2} r^{s + 1/2 - 2} = r^{s-1}$. The set of singular matrices has measure $0$. $\square$

So the whole computation is one integral over $M_2(K)$. We write a matrix by its entries $(a, b, c, d)$, so that $\det = a d - b c$. Let $\mu$ be a Haar measure on $K$.

**Lemma 3.14.33 (coordinates).** The map $e : M_2(K) \to K^4$, $x \mapsto (x_{11}, x_{12}, x_{21}, x_{22})$, is a homeomorphism and an isomorphism of additive groups. There is $c > 0$ with $\int_{M_2(K)} h \, dx = c \int_{K^4} h \circ e^{-1} \, d\mu^{\otimes 4}$ for each integrable $h$. An integral over $K^4$ of a product $h_1(a) h_2(b) h_3(c) h_4(d)$ of integrable functions is the product of the four integrals.

Lean: `Langlands.LocalGL2.plEntries`, `Langlands.LocalGL2.plEntriesAdd`, `Langlands.LocalGL2.pl_det_symm`, `Langlands.LocalGL2.pl_exists_scalar`, `Langlands.LocalGL2.plProd`, `Langlands.LocalGL2.pl_integral_four`, `Langlands.LocalGL2.pl_integral_prod4`

*Proof.* The image of the Haar measure of $M_2(K)$ under $e$ is a Haar measure on $K^4$, and $\mu^{\otimes 4}$ is another one. By the uniqueness of Haar measure they differ by a constant $c > 0$. The last claim is Fubini's theorem. $\square$

So we study $I(F) = \int_{K^4} F(p) \, \chi(\det p) \, |\det p|^{s-1} \, d\mu^{\otimes 4}(p)$ for a locally constant function $F$ with compact support on $K^4$. It converges absolutely when $|\chi(\varpi) q^{1-s}| \le 1$ and $|\chi(\varpi) q^{-s}| \le 1$, since then the function $\chi(y)|y|^{s-1}$ is bounded on each ball (`Langlands.LocalGL2.pl_exists_bound_zetaFn`, `Langlands.LocalGL2.pl_integrable_mul_zetaFn_det`). The bound `Langlands.LocalGL2.plBound` is a real number $s_0$ such that both conditions hold for $\mathrm{Re}(s) > s_0$.

**Lemma 3.14.34 (decomposition into boxes).** Let $F$ be locally constant with compact support on $K^4$. There are $N \in \mathbb{Z}$ and a finite set $T \subseteq K$ such that
$$F(a, b, c, d) = \sum_{t \in T^4} F(t) \, \mathbf{1}_{t_1 + \mathfrak{p}_K^N}(a) \, \mathbf{1}_{t_2 + \mathfrak{p}_K^N}(b) \, \mathbf{1}_{t_3 + \mathfrak{p}_K^N}(c) \, \mathbf{1}_{t_4 + \mathfrak{p}_K^N}(d).$$

Lean: `Langlands.LocalGL2.plBox`, `Langlands.LocalGL2.pl_exists_forall_add_eq`, `Langlands.LocalGL2.pl_exists_partition`, `Langlands.LocalGL2.pl_prod_ballIndicator`, `Langlands.LocalGL2.pl_sum_box_prod`, `Langlands.LocalGL2.pl_exists_eq_sum`

*Proof.* The support of $F$ is compact, so it lies in a box $(\mathfrak{p}_K^M)^4$. The function $F$ is uniformly locally constant: there is $N \ge M$ with $F(p + h) = F(p)$ for each $p$ and each $h \in (\mathfrak{p}_K^N)^4$. Indeed, each point of the box has a neighbourhood $p + (\mathfrak{p}_K^{N_p})^4$ on which $F$ is constant, finitely many of them cover the box, and $N$ is the largest $N_p$. The ball $\mathfrak{p}_K^M$ is the disjoint union of finitely many translates $t + \mathfrak{p}_K^N$. Let $T$ be a set of their centres. Then the boxes $t + (\mathfrak{p}_K^N)^4$ for $t \in T^4$ partition $(\mathfrak{p}_K^M)^4$, and $F$ is the constant $F(t)$ on each of them. The indicator of a box is the product of the four indicators. $\square$

The determinant does not split as a product of functions of the coordinates, so the lemma does not apply at once to $I(F)$. We first change variables. For $m \ge 0$ let $R_m$ be the region $a \ne 0$, $c/a \in \mathfrak{p}_K^m$, and let $\sigma(a, b, c, d) = (c, d, a, b)$ be the exchange of the two rows.

**Lemma 3.14.35 (the two regions).**
1. Each point of $K^4$ with $(a, c) \ne (0, 0)$ lies in exactly one of $R_0$ and $\sigma^{-1}(R_1)$.
2. The map $\sigma$ preserves $\mu^{\otimes 4}$, and $\det \sigma(p) = -\det p$.
3. For $\mathrm{Re}(s) > s_0$,
$$I(F) = \int_{R_0} F \, \chi(\det) |\det|^{s-1} + \chi(-1) \int_{R_1} (F \circ \sigma) \, \chi(\det) |\det|^{s-1}.$$

Lean: `Langlands.LocalGL2.plRegion`, `Langlands.LocalGL2.pl_split_pt`, `Langlands.LocalGL2.plSwap`, `Langlands.LocalGL2.pl_swap_apply`, `Langlands.LocalGL2.pl_det_swap`, `Langlands.LocalGL2.pl_measurePreserving_swap`, `Langlands.LocalGL2.plSign`, `Langlands.LocalGL2.pl_zetaFn_neg`, `Langlands.LocalGL2.pl_split`

*Proof.* Part 1. If $a = 0$, then $c \ne 0$ and $a/c = 0 \in \mathfrak{p}_K$, so the point lies in $\sigma^{-1}(R_1)$ and not in $R_0$. If $c = 0$, it lies in $R_0$ and not in $\sigma^{-1}(R_1)$. If both are nonzero, exactly one of $v_K(c/a) \ge 0$ and $v_K(a/c) \ge 1$ holds, since $v_K(a/c) = -v_K(c/a)$. Part 2. The map permutes the coordinates, so it preserves the product measure. And $\det(c, d, a, b) = c b - d a$. Part 3. The set $a = c = 0$ has measure $0$. By part 1, $I(F)$ is the integral over $R_0$ plus the integral over $\sigma^{-1}(R_1)$. In the second one substitute $p = \sigma(p')$, which is allowed by part 2. Since $\sigma$ is an involution, $p' \in R_1$, and the integrand becomes $F(\sigma p') \chi(-\det p') |\det p'|^{s-1}$. Finally $\chi(-y) = \chi(-1) \chi(y)$. $\square$

**Proposition 3.14.36 (the change of variables on a region).** Let $m \ge 0$ and let $F$ be locally constant with compact support. Put $G_m(a, b, t, d) = \mathbf{1}_{\mathfrak{p}_K^m}(t) \, F(a, b, a t, d + t b)$. Then $G_m$ is locally constant with compact support, and for $\mathrm{Re}(s) > s_0$,
$$\int_{R_m} F \, \chi(\det) |\det|^{s-1} = \int_{K^4} G_m(a, b, t, d) \, \chi(a) |a|^{s} \, \chi(d) |d|^{s-1} \, d\mu^{\otimes 4}.$$

Lean: `Langlands.LocalGL2.plSub`, `Langlands.LocalGL2.pl_zetaFn_mul_abs`, `Langlands.LocalGL2.pl_region_iter`, `Langlands.LocalGL2.pl_isLocallyConstant_sub`, `Langlands.LocalGL2.pl_sub_eq_zero`, `Langlands.LocalGL2.pl_hasCompactSupport_sub`, `Langlands.LocalGL2.pl_region_eq`

*Proof.* Fix $a \ne 0$ and $b$, and integrate first over $c$ and $d$. Substitute $c = a t$. By Lemma 3.2.16, $dc = |a| \, dt$, and the condition $c/a \in \mathfrak{p}_K^m$ becomes $t \in \mathfrak{p}_K^m$. The determinant becomes $a d - a t b = a(d - t b)$. Now substitute $d = d' + t b$, which is a translation and preserves $\mu$. The determinant becomes $a d'$. So the inner integral is
$$\int \int \mathbf{1}_{\mathfrak{p}_K^m}(t) F(a, b, a t, d' + t b) \, |a| \, \chi(a d') |a d'|^{s-1} \, dt \, dd',$$
and $|a| \chi(a d') |a d'|^{s-1} = \chi(a) |a|^s \chi(d') |d'|^{s-1}$. The line $a = 0$ has measure $0$, so we may integrate over all $a$. The function $G_m$ is locally constant, since $F$ is and the maps are continuous, and the indicator of $\mathfrak{p}_K^m$ is locally constant. If $F$ vanishes outside $(\mathfrak{p}_K^M)^4$ with $M \le 0$ and $G_m(a, b, t, d) \ne 0$, then $a, b \in \mathfrak{p}_K^M$ and $t \in \mathfrak{p}_K^m \subseteq \mathcal{O}_K$, so $t b \in \mathfrak{p}_K^M$ and $d = (d + t b) - t b \in \mathfrak{p}_K^M$. So $G_m$ vanishes outside the same box. $\square$

The factor $\chi(a) |a|^s$ is $(\chi |\cdot|)(a) |a|^{s-1}$. So the right side is an integral against Tate's integrand for $\chi |\cdot|$ in $a$ and for $\chi$ in $d$. This is where the second $L$-factor $L(s, \chi |\cdot|)$ comes from: the Jacobian $|a|$ of the substitution $c = a t$ shifts the character.

**Definition 3.14.37 (good functions).** Let $L$ be a function of $s$. A function $f$ of $s$ is *good for $L$* if there are a polynomial $A$, an integer $k \ge 0$ and $s_1$ with $f(s) = A(X) X^{-k} L(s)$ for $\mathrm{Re}(s) > s_1$.

Lean: `Langlands.LocalGL2.PlGood`

This is the form of clause 2 of `IsGJLFactor`. The rules are easy.

**Lemma 3.14.38 (rules for good functions).**
1. Sums, finite sums and constant multiples of functions good for $L$ are good for $L$. A function equal to a good one for $\mathrm{Re}(s)$ large is good.
2. If $f_1$ is good for $L_1$ and $f_2$ is good for $L_2$, then $f_1 f_2$ is good for $L_1 L_2$.
3. If $f$ is good for $L$ and $L = 1$, then $f$ is a Laurent polynomial in $X$ for $\mathrm{Re}(s)$ large.
4. For a Schwartz-Bruhat function $\varphi$ on $K$, $Z(\varphi, \chi, s)$ is good for $L(s, \chi)$.

Lean: `Langlands.LocalGL2.pl_good_of_eq`, `Langlands.LocalGL2.pl_good_congr`, `Langlands.LocalGL2.pl_good_zero`, `Langlands.LocalGL2.pl_good_add`, `Langlands.LocalGL2.pl_good_const_mul`, `Langlands.LocalGL2.pl_good_sum`, `Langlands.LocalGL2.pl_good_mul`, `Langlands.LocalGL2.pl_good_one`, `Langlands.LocalGL2.pl_good_zeta`

*Proof.* Part 1. For a sum, write $A_1 X^{-k_1} + A_2 X^{-k_2} = (A_1 X^{k_2} + A_2 X^{k_1}) X^{-k_1 - k_2}$, and take the larger of the two bounds on $\mathrm{Re}(s)$. Part 2. Multiply the two forms. Part 3 is the definition. Part 4 is Corollary 3.2.19, part 1. $\square$

**Theorem 3.14.39 (the zeta integrals on $K^4$).** Let $F$ be locally constant with compact support on $K^4$. Then $I(F)$ is good for $L(s, \chi) L(s, \chi |\cdot|)$.

Lean: `Langlands.LocalGL2.pl_rhs`, `Langlands.LocalGL2.plBound`, `Langlands.LocalGL2.pl_norm_le_of_bound`, `Langlands.LocalGL2.pl_good_rhs`, `Langlands.LocalGL2.pl_good_det`

*Proof.* By Lemma 3.14.35, part 3, and Proposition 3.14.36, $I(F)$ is a sum of two integrals of the form
$$I'(G) = \int_{K^4} G(a, b, t, d) \, (\chi |\cdot|)(a) |a|^{s-1} \, \chi(d) |d|^{s-1} \, d\mu^{\otimes 4},$$
with $G = G_0$ for $F$ and $G = G_1$ for $F \circ \sigma$, the second one multiplied by the constant $\chi(-1)$. The function $F \circ \sigma$ is again locally constant with compact support. Apply Lemma 3.14.34 to $G$. The integral of one product term is, by Lemma 3.14.33,
$$G(t) \cdot Z(\mathbf{1}_{t_1 + \mathfrak{p}_K^N}, \chi |\cdot|, s) \cdot \mu(t_2 + \mathfrak{p}_K^N) \cdot \mu(t_3 + \mathfrak{p}_K^N) \cdot Z(\mathbf{1}_{t_4 + \mathfrak{p}_K^N}, \chi, s).$$
By Lemma 3.14.38, part 4, the first zeta integral is good for $L(s, \chi |\cdot|)$ and the second for $L(s, \chi)$. By parts 1 and 2 the finite sum is good for the product. $\square$

The decomposition is done after the change of variables, on $G$, and not on $F$. On a box, $F$ is constant, but $\chi(\det)$ is not a product of functions of the four coordinates. After the change of variables it is.

**Proposition 3.14.40 (the unit box).** Let $\chi$ be unramified, and let $F = \mathbf{1}_{\mathcal{O}_K^4}$. For $\mathrm{Re}(s) > s_0$,
$$I(F) = C_\mu \, L(s, \chi) \, L(s, \chi |\cdot|), \qquad C_\mu = \mu(\mathcal{O}_K^\times)^2 \, \mu(\mathcal{O}_K) \, \bigl(\mu(\mathcal{O}_K) + \mu(\mathfrak{p}_K)\bigr) \ne 0.$$

Lean: `Langlands.LocalGL2.pl_unr_abs_iff`, `Langlands.LocalGL2.pl_ord_neg_one`, `Langlands.LocalGL2.pl_sign_unr`, `Langlands.LocalGL2.pl_isLocallyConstant_box`, `Langlands.LocalGL2.pl_hasCompactSupport_box`, `Langlands.LocalGL2.pl_sub_box`, `Langlands.LocalGL2.pl_ballZeta_unr`, `Langlands.LocalGL2.pl_integral_indicator_ordBall`, `Langlands.LocalGL2.pl_integral_sub_box`, `Langlands.LocalGL2.plConst`, `Langlands.LocalGL2.pl_const_ne_zero`, `Langlands.LocalGL2.pl_integral_box`

*Proof.* The function $F$ is invariant under $\sigma$. For $m \ge 0$, $G_m$ is the indicator of $\mathcal{O}_K \times \mathcal{O}_K \times \mathfrak{p}_K^m \times \mathcal{O}_K$: if $a, b \in \mathcal{O}_K$ and $t \in \mathfrak{p}_K^m$, then $a t \in \mathcal{O}_K$, and $d + t b \in \mathcal{O}_K$ exactly when $d \in \mathcal{O}_K$. So
$$I'(G_m) = Z(\mathbf{1}_{\mathcal{O}_K}, \chi |\cdot|, s) \cdot \mu(\mathcal{O}_K) \cdot \mu(\mathfrak{p}_K^m) \cdot Z(\mathbf{1}_{\mathcal{O}_K}, \chi, s).$$
The character $\chi |\cdot|$ is unramified with $\chi$, and $\chi(-1) = 1$, since $-1$ is a unit. By Theorem 3.2.18, part 3, $Z(\mathbf{1}_{\mathcal{O}_K}, \chi, s) = \mu(\mathcal{O}_K^\times) L(s, \chi)$, and the same holds for $\chi |\cdot|$. Add the two regions, $m = 0$ and $m = 1$. The constant is not zero, since the measures of the open sets $\mathcal{O}_K^\times$ and $\mathcal{O}_K$ are positive. $\square$

The two regions give the two terms $\mu(\mathcal{O}_K)$ and $\mu(\mathfrak{p}_K)$ of the constant. With $\mu(\mathcal{O}_K) = 1$ the constant is $(1 - q^{-1})^2 (1 + q^{-1}) = (1 - q^{-1})(1 - q^{-2})$, which is the volume of $GL_2(\mathcal{O}_K)$ in $M_2(\mathcal{O}_K)$, that is $|GL_2(\mathbb{F}_q)| / q^4$. Exercise 51 extracts from the proposition the volume of each set $\{x \in M_2(\mathcal{O}_K) : v_K(\det x) = k\}$.

**Theorem 3.14.41 (`PSLFactorDetChar`).** For each smooth character $\chi$ of $K^\times$, the Godement-Jacquet $L$-factor of $\theta = (\chi |\cdot|^{1/2}) \circ \det$ is $L(s, \chi) L(s, \chi |\cdot|)$. So fact 5 of Definition 3.11.31 holds for every $K$.

Lean: `Langlands.LocalGL2.plForm`, `Langlands.LocalGL2.pl_form_mem`, `Langlands.LocalGL2.psLFactorDetChar_holds`, `Langlands.LocalGL2.isGJLFactor_one_of_zeta`

*Proof.* By Lemmas 3.14.32 and 3.14.33, each zeta integral of $\theta$ is $\lambda(v) \, c \, I(\Phi \circ e^{-1})$, and $\Phi \circ e^{-1}$ is locally constant with compact support. By Theorem 3.14.39 and Lemma 3.14.38, part 1, it is good for $L(s, \chi) L(s, \chi |\cdot|)$. This is clause 2.

First let $\chi$ be unramified. Then $L(s, \chi) L(s, \chi |\cdot|) = P(X)^{-1}$ with $P(X) = (1 - \chi(\varpi) X)(1 - \chi(\varpi) q^{-1} X)$, and $P(0) = 1$. This is clause 1. For clause 3, take $\Phi = \mathbf{1}_{M_2(\mathcal{O}_K)}$, $v = 1$ and $\lambda(z) = z$. The form $\lambda$ is smooth, since it is fixed by the open kernel of $\theta$. By Proposition 3.14.40,
$$L(s, \chi) L(s, \chi |\cdot|) = (c \, C_\mu)^{-1} \, Z(\Phi, s, f),$$
a combination with the constant Laurent polynomial $(c \, C_\mu)^{-1}$.

Now let $\chi$ be ramified. Then $\chi |\cdot|$ is ramified too, and both $L$-factors are $1$. By clause 2 and Lemma 3.14.38, part 3, each zeta integral is a Laurent polynomial in $X$ for $\mathrm{Re}(s)$ large. The space $\mathbb{C}$ is not zero, so Theorem 3.11.20 gives that $L(s, \theta) = 1$. $\square$

For ramified $\chi$ the unit box gives nothing: Theorem 3.2.18, part 3, gives $Z(\mathbf{1}_{\mathcal{O}_K}, \chi, s) = 0$, so $I(\mathbf{1}_{\mathcal{O}_K^4}) = 0$. The function used in Theorem 3.11.20 is the indicator of a small ball $1 + \varpi^k M_2(\mathcal{O}_K)$ on which $\theta$ is trivial. The theorem is the case $n = 2$ of the computation in Godement and Jacquet, *Zeta functions of simple algebras*, Lecture Notes in Mathematics 260, Theorem 3.3, and of [BH06], Chapter 6, section 26. Their proof for $GL_n$ uses the Iwasawa decomposition of $GL_n(K)$ and induction on $n$. The proof above replaces the Iwasawa decomposition by the elementary change of variables of Proposition 3.14.36. The two regions $R_0$ and $\sigma^{-1}(R_1)$ play the role of the two Bruhat cells.

**Example 3.14.42 (the trivial representation).** Take $\chi = |\cdot|^{-1/2}$, so that $\theta = 1_G$ and $\chi(\varpi) = q^{1/2}$. Theorem 3.14.41 gives
$$L(s, 1_G) = L(s, |\cdot|^{-1/2}) \, L(s, |\cdot|^{1/2}) = \frac{1}{(1 - q^{1/2} X)(1 - q^{-1/2} X)},$$
which is the $L$-factor of Example 3.10.19. Proposition 3.14.40 with $\mu(\mathcal{O}_K) = 1$ gives
$$\int_{M_2(\mathcal{O}_K)} |\det x|^{s - 3/2} \, dx = \frac{(1 - q^{-1})(1 - q^{-2})}{(1 - q^{1/2} X)(1 - q^{-1/2} X)}.$$
The measure $|\det x|^{-2} dx$ is a Haar measure on $G$, and it gives $GL_2(\mathcal{O}_K)$ the volume $(1 - q^{-1})(1 - q^{-2})$. Divide by this volume. The result is the zeta integral of Example 3.11.22, which was computed there with the Hermite normal form and the normalization $\mathrm{vol}(K_0) = 1$. The two computations agree.

**Corollary 3.14.43 (the inputs on the principal series).** For each $K$, `PSLFactorIrreducible` and `PSLFactorSteinberg` imply the structure `NonSupercuspidalInputs`, that is, the eight inputs of Definition 3.10.14.

Lean: `Langlands.LocalGL2.nonSupercuspidalInputs_of_lFactor`, `Langlands.LocalGL2.nonSupercuspidalInputs_of_contragredient_lFactor`, `Langlands.LocalGL2.psContragredientIso_holds`

*Proof.* By `nonSupercuspidalInputs_of_contragredient_lFactor`, the structure follows from `PSContragredientIso` and the three $L$-factor facts. The first holds by Theorem 3.13.37, and `PSLFactorDetChar` holds by Theorem 3.14.41. $\square$

### What is open for $GL_2$, $p \ne 2$

**Corollary 3.14.44 (the reduction as it stands).** Let $p \ne 2$. The statement `Langlands.LocalLanglandsGL2Odd` follows, for all $K$, from:
1. `ArtinCompat` and `Rectifier`, inputs 1 and 4 of Definition 3.9.30;
2. the five facts of `GaloisTameOpenInputs`, Corollary 3.12.34;
3. `SupercuspidalZetaLaurent`, Definition 3.11.19;
4. `PSLFactorIrreducible` and `PSLFactorSteinberg`, facts 4 and 6 of Definition 3.11.31;
5. `TypeNormalizerRamifiedField` and `TypeNormalizerSameBasisIso`, Definition 3.14.26, and `UncoveredParametrization`, input 5 of Definition 3.10.27.

Lean: `Langlands.LocalGL2.nonSupercuspidalInputs_of_lFactor`, `Langlands.LocalGL2.psLFactorDetChar_holds`, `Langlands.LocalGL2.typeRepInjective_of_ramifiedField_of_sameBasisIso`, `Langlands.LocalGL2.typeRepIndependent`, `Langlands.LocalGL2.GL2OddFineInputs`, `Langlands.localLanglandsGL2_odd_of_fineInputs` (the joining step is not yet in the library)

*Proof.* Theorem 3.14.41 gives `PSLFactorDetChar`, so item 4 gives item 4 of Corollary 3.13.39. Theorem 3.14.29 gives `TypeRepInjective` from the first two statements of item 5, so item 5 gives item 5 of Corollary 3.13.39. Corollary 3.13.39 concludes. $\square$

**Remark 3.14.45 (what is still open for $GL_2$, $p \ne 2$).** This list replaces Remark 3.13.40.
1. `ArtinCompat` ([Ser79], Chapter XI).
2. The five facts `ArtinConjCompat`, `WildInertiaProP`, `TameInertiaProcyclic`, `OpenIndexTwoQuad` and `WildArtinUnits` of Corollary 3.12.34.
3. `Rectifier`, with the characters $\Delta_\xi$ of [BH06], section 34.
4. `SupercuspidalZetaLaurent`, the analytic half of Proposition 2.5.6.
5. The two $L$-factor facts `PSLFactorIrreducible` and `PSLFactorSteinberg` of Definition 3.11.31.
6. The two statements `TypeNormalizerRamifiedField` and `TypeNormalizerSameBasisIso` of Definition 3.14.26, which replace `TypeRepInjective`, and `UncoveredParametrization`.
7. The structure that joins the results of Sections 3.11 to 3.14 into `GL2OddFineInputs`.
8. The case $p = 2$, the $\varepsilon$-factors, and the uniqueness of Theorem 3.3.1.

Item 5 has lost `PSLFactorDetChar`. The two facts left in it are also computations of zeta integrals on $M_2(K)$, but for the induced representations $\chi_1 \times \chi_2$ and for the Steinberg subspace, whose matrix coefficients are not characters. They need the Iwasawa decomposition and an integral over $B \backslash G$, or the invariant integral $\mathcal{I}$ of Section 3.13 in place of it ([BH06], Chapter 6, section 26; [JL70], section 3). Item 6 has lost the part of `TypeRepInjective` that compares the chain orders, the levels and the position of the intertwining element, and, for the maximal order, the comparison of the fields. What is left is the field step for the Iwahori order and the comparison of the characters on one field. Remarks 3.14.30 and 3.14.31 give the intended proofs. Both need two small facts that the library does not have yet: two characters of $K$ of level one differ by a unit, and trace duality holds on the matrices of trace $0$. The converse half of the Mackey formula, Remark 3.14.4, is not needed for item 6.
