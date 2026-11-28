---
title: The normalizer statements, the principal series and wild inertia
nodes: []
sources: [BH06, JL70, Ser79]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## The normalizer statements, the principal series and wild inertia

Remark 3.14.45 lists what is still open for $GL_2$ with $p \ne 2$. This section removes three items from that list and reduces a fourth. First, we prove the two statements `TypeNormalizerRamifiedField` and `TypeNormalizerSameBasisIso` of Definition 3.14.26. With Theorem 3.14.29 this proves input 2 of Definition 3.10.27, `TypeRepInjective`: isomorphic type representations come from isomorphic pairs. Second, we compute the integrals $\int \Phi(x) f(x) |\det x|^{s - 3/2} \, dx$ for the functions $f$ of the principal series, and we reduce `PSLFactorIrreducible` to three statements that relate these integrals to the zeta integrals of the matrix coefficients. Third, we prove `WildInertiaProP`, fact 2 of Definition 3.12.18: the wild inertia group is a pro-$p$ group.

The first part follows the plan of Remarks 3.14.30 and 3.14.31, with two changes. The library needed two small facts: two characters of $K$ of level one differ by a unit, and trace duality holds on the elements of determinant $1$. We prove both. The second change is in the comparison of the fields. In place of the element $\alpha_0 = \alpha - \mathrm{tr}(\alpha)/2$, we use the discriminant $\mathrm{tr}(Y)^2 - 4 \det(Y)$ of a $2 \times 2$ matrix $Y$. It does not change under conjugation, it changes by a square under $Y \mapsto u Y - c$, and it is continuous for the filtration $\mathfrak{P}^k_{\mathfrak{A}}$. The same algebra shows that an intertwining element moves $\alpha$ close to $\alpha$ or close to its conjugate, and this decides the comparison of the characters.

The second part is the computation of Section 3.14 for a character of the determinant, with the function $f$ in place of the character. The Iwasawa decomposition on the big cell writes $f(x)$ as a product of two characters and a value of $f$ on the lower unipotent group. After the change of variables of Proposition 3.14.36, the integral is again a sum of products of two of Tate's zeta integrals. The third part is a lemma on a local ring: an automorphism that is close to the identity and has a power of order prime to $p$ that fixes an element also fixes that element.

We keep the notation of Section 3.14. In particular $\psi_Y(x) = \psi(\mathrm{tr}(Y(x - 1)))$ for a matrix $Y$, a tame datum is $D = (\psi, \mathfrak{A}, v, \xi_0, \alpha, \Lambda_0, \chi)$ for a pair $(L/K, \xi)$, its level $n$ is odd, $m = (n + 1)/2$, $J = \iota_v(L^\times) U^m_{\mathfrak{A}}$, and we number the rows and columns of a matrix by $1$ and $2$. We write $M_v(x)$ for the matrix of $x \in L$ in the basis $v$, so that $\iota_v(y) = M_v(y)$ for $y \in L^\times$, and $\sigma$ for the nontrivial $K$-automorphism of $L$. The discriminant of $Y \in M_2(K)$ is $\mathrm{disc}(Y) = \mathrm{tr}(Y)^2 - 4 \det(Y)$. A character of $K$ has *level one* if it is trivial on $\mathfrak{p}_K$ and not on $\mathcal{O}_K$. The Lean files of this section are `Langlands/Local/TypeNormalizerProps.lean`, `Langlands/Local/PSLFactorInduced.lean` and `Langlands/Local/WeilGroupOpen.lean`.

### Two characters of level one

The proofs of Section 3.14 compare the two data $D$ and $D'$ through their characters $\psi$ and $\psi'$ of $K$. Lemma 3.14.12 did this one element at a time. The next proposition does it once for all.

**Lemma 3.15.1 (two characters on a ball).** Let $\psi$ and $\psi'$ be characters of $K$ of level one, and let $N \ge 0$. There is $a \in \mathcal{O}_K$ with $\psi'(x) = \psi(a x)$ for each $x \in \mathfrak{p}_K^{-N}$. Each $x \in K$ lies in some ball $\mathfrak{p}_K^{-N}$ with $N \ge 0$.

Lean: `Langlands.LocalGL2.exists_eq_psi_mul_on_ordBall`, `Langlands.LocalGL2.exists_nat_mem_ordBall_neg`

*Proof.* The last claim is clear: take $N = \max(0, -v_K(x))$. Let $G = \mathfrak{p}_K^{-N}$ and $H = \mathfrak{p}_K$. The quotient $G/H$ is a finite group of order $q^{N+1}$. For $z \in G$, the character $y \mapsto \psi(\varpi^N z y)$ of $G$ is trivial on $H$, since $\varpi^N z \in \mathcal{O}_K$ and $\psi$ is trivial on $\mathfrak{p}_K$. It depends only on $z + H$: for $h \in H$ and $y \in G$ we have $\varpi^N h y \in \mathfrak{p}_K$. So we get a homomorphism $\theta$ from $G/H$ to the character group of $G/H$. It is injective. Suppose that $\psi(\varpi^N w y) = 1$ for all $y \in \mathfrak{p}_K^{-N}$. Since $\psi$ has level one, the set of $b$ with $\psi(b y) = 1$ for all $y \in \mathfrak{p}_K^{-N}$ is $\mathfrak{p}_K^{1+N}$. So $\varpi^N w \in \mathfrak{p}_K^{1+N}$ and $w \in H$. A finite abelian group and its character group have the same order, so $\theta$ is bijective. The character $\psi'$ is trivial on $H$, so its restriction to $G$ is a character of $G/H$, and it is $\theta(z + H)$ for some $z \in G$. Then $a = \varpi^N z$ lies in $\mathcal{O}_K$ and works. $\square$

**Proposition 3.15.2 (two characters of level one differ by a unit, [BH06] 1.7).** Let $\psi$ and $\psi'$ be characters of $K$ of level one. There is a unit $u \in \mathcal{O}_K^\times$ with $\psi'(x) = \psi(u x)$ for each $x \in K$.

Lean: `Langlands.LocalGL2.exists_eq_psi_mul`

*Proof.* For $N \ge 0$ let $S_N$ be the set of $a \in \mathcal{O}_K$ with $\psi'(x) = \psi(a x)$ for all $x \in \mathfrak{p}_K^{-N}$. By Lemma 3.15.1, $S_N$ is not empty. It is closed in $\mathcal{O}_K$: for each $x$ the set of $a$ with $\psi(a x) = \psi'(x)$ is closed, since $\psi$ is continuous, and $S_N$ is an intersection of such sets. The sets decrease, since the balls increase. The ring $\mathcal{O}_K$ is compact, so the intersection of the $S_N$ contains an element $u$. By the last claim of Lemma 3.15.1, $\psi'(x) = \psi(u x)$ for all $x \in K$. If $v_K(u) \ge 1$, then $u x \in \mathfrak{p}_K$ for all $x \in \mathcal{O}_K$, so $\psi'$ is trivial on $\mathcal{O}_K$. This is false, since $\psi'$ has level one. So $u$ is a unit. $\square$

In fact $S_N$ is a coset of $\mathfrak{p}_K^{N+1}$, by the injectivity in the proof of Lemma 3.15.1. So the element $u$ is unique. Exercise 53 does this count.

**Example 3.15.3 (the characters of level one of $\mathbb{Q}_p$).** Let $\psi(x) = e^{2 \pi i \{x / p\}}$, the character of Example 3.9.27. It is trivial on $p\mathbb{Z}_p$, and $\psi(1) = e^{2 \pi i/p} \ne 1$, so it has level one. By Proposition 3.15.2, the characters of level one of $\mathbb{Q}_p$ are exactly the characters $x \mapsto e^{2 \pi i \{u x/p\}}$ with $u \in \mathbb{Z}_p^\times$. The character $x \mapsto e^{2 \pi i \{x\}}$ is trivial on $\mathbb{Z}_p$ and not on $p^{-1}\mathbb{Z}_p$. It is $\psi(p x)$, and $p$ is not a unit. So the hypothesis on the level of $\psi'$ is needed.

### Trace duality on the elements of determinant 1

Proposition 3.9.2, part 4, says that $\psi_Y$ is trivial on $U^k_{\mathfrak{A}}$ exactly when $Y \in \mathfrak{P}^{1-k}_{\mathfrak{A}}$. The intertwining test of Section 3.14 only sees the elements of determinant $1$, since the character $\chi \circ \det$ of a datum is unknown. The test on these elements loses the scalar part of $Y$, and nothing more. The proof uses three kinds of test elements: $x_+(c)$, $x_-(c)$ and the diagonal elements $\mathrm{diag}(t, t^{-1})$.

**Lemma 3.15.4 (the bound for the diagonal test).** For each chain order $\mathfrak{A}$ and each $k \in \mathbb{Z}$, $b_{1-2k}(2, 2) + 2 b_k(1, 1) \ge 1$.

Lean: `Langlands.LocalGL2.ChainOrder.one_le_bd_add_two_mul`

*Proof.* The diagonal bounds do not see the weights: $b_j(i, i)$ is the least $t$ with $j \le e t$. For $\mathfrak{M}$, $e = 1$ and $b_j(i, i) = j$, so the sum is $(1 - 2k) + 2k = 1$. For $\mathfrak{J}$, $e = 2$ and $b_j(i, i) = \lceil j/2 \rceil$. Then $b_{1-2k}(2, 2) = \lceil 1/2 - k \rceil = 1 - k$ and $2 b_k(1, 1) = 2 \lceil k/2 \rceil \ge k$. The sum is at least $1$. $\square$

**Proposition 3.15.5 (trace duality on the elements of determinant 1, [BH06] 12.8 and 13.2).** Let $\psi$ have level one, let $k \ge 1$ and let $Y \in \mathfrak{P}^{1-2k}_{\mathfrak{A}}$. Suppose that $\psi_Y(x) = 1$ for each $x \in U^k_{\mathfrak{A}}$ with $\det x = 1$. Then $Y - Y_{22} \cdot 1 \in \mathfrak{P}^{1-k}_{\mathfrak{A}}$.

Lean: `Langlands.LocalGL2.sub_smul_one_mem_radPow_of_forall_psiAlphaFun`

*Proof.* We check the four entries of $Y - Y_{22} \cdot 1$. The entry at $(2, 2)$ is $0$. For the entry at $(2, 1)$, let $c \in \mathfrak{p}_K^{b_k(1, 2)}$. Then $x_+(c) - 1 = c E_{12} \in \mathfrak{P}^k_{\mathfrak{A}}$, so $x_+(c) \in U^k_{\mathfrak{A}}$, and $\det x_+(c) = 1$. Now $\mathrm{tr}(Y c E_{12}) = c Y_{21}$. So $\psi(c Y_{21}) = 1$ for all $c \in \mathfrak{p}_K^{b_k(1, 2)}$. Since $\psi$ has level one, $Y_{21} \in \mathfrak{p}_K^{1 - b_k(1, 2)} = \mathfrak{p}_K^{b_{1-k}(2, 1)}$, by the duality of the bounds. In the same way $x_-(c)$ with $c \in \mathfrak{p}_K^{b_k(2, 1)}$ gives $Y_{12} \in \mathfrak{p}_K^{b_{1-k}(1, 2)}$.

For the entry at $(1, 1)$, let $s \in \mathfrak{p}_K^{b_k(1, 1)}$ and $t = 1 + s$. Since $k \ge 1$, $b_k(1, 1) \ge 1$, so $t$ is a unit and $t^{-1} - 1 = -s t^{-1} \in \mathfrak{p}_K^{b_k(2, 2)}$, as $b_k(2, 2) = b_k(1, 1)$. So $x = \mathrm{diag}(t, t^{-1})$ lies in $U^k_{\mathfrak{A}}$, and $\det x = 1$. We compute
$$\mathrm{tr}(Y(x - 1)) = Y_{11} s - Y_{22} s t^{-1} = (Y_{11} - Y_{22}) s + Y_{22} s^2 t^{-1},$$
because $s - s t^{-1} = s (t - 1) t^{-1} = s^2 t^{-1}$. The valuation of the last term is at least $b_{1-2k}(2, 2) + 2 b_k(1, 1)$, which is at least $1$ by Lemma 3.15.4. So $\psi$ is trivial on it, and $\psi((Y_{11} - Y_{22}) s) = 1$ for all $s \in \mathfrak{p}_K^{b_k(1, 1)}$. As before, $Y_{11} - Y_{22} \in \mathfrak{p}_K^{1 - b_k(1,1)} = \mathfrak{p}_K^{b_{1-k}(1, 1)}$. The four bounds are the bounds of $\mathfrak{P}^{1-k}_{\mathfrak{A}}$. $\square$

**Remark 3.15.6 (the scalars pass the test).** The conclusion cannot say more. Let $c \in K$ with $c \cdot 1 \in \mathfrak{P}^{1-2k}_{\mathfrak{A}}$, and let $x = 1 + X \in U^k_{\mathfrak{A}}$ with $\det x = 1$. Since $\det(1 + X) = 1 + \mathrm{tr}(X) + \det(X)$, we get $\mathrm{tr}(X) = -\det(X)$, so $\psi_{c}(x) = \psi(-c \det X)$. For $\mathfrak{M}$, $\det X \in \mathfrak{p}_K^{2k}$ and $c \in \mathfrak{p}_K^{1-2k}$. For $\mathfrak{J}$, $X = \Pi_{\mathfrak{J}}^k X'$ with $X' \in \mathfrak{J}$ by Proposition 3.9.2, part 1, so $v_K(\det X) \ge k$, and $v_K(c) \ge b_{1-2k}(1, 1) = 1 - k$. In both cases $c \det X \in \mathfrak{p}_K$, and $\psi_{c}(x) = 1$. So the set of $Y \in \mathfrak{P}^{1-2k}_{\mathfrak{A}}$ that pass the test is $(K \cdot 1 \cap \mathfrak{P}^{1-2k}_{\mathfrak{A}}) + \mathfrak{P}^{1-k}_{\mathfrak{A}}$. Exercise 54 checks this.

We now apply the two facts to two data.

**Theorem 3.15.7 (the congruence of two intertwining strata, [BH06] 15.7).** Let $D$ and $D'$ be data with the same chain order $\mathfrak{A}$ and the same level $n = 2m - 1$, and let $g \in \mathfrak{K}_{\mathfrak{A}}$ intertwine $\Lambda$ with $\Lambda'$. Let $Y$ and $Y'$ be the matrices of $\alpha$ and $\alpha'$. There are a unit $u \in \mathcal{O}_K^\times$ and $c \in K$ with
$$u \, g^{-1} Y' g - Y - c \in \mathfrak{P}^{1-m}_{\mathfrak{A}}.$$

Lean: `Langlands.LocalGL2.TameDatum.level_eq_two_mul_sub_one`, `Langlands.LocalGL2.TameDatum.exists_smul_conj_sub_mem`

*Proof.* By Proposition 3.15.2, $\psi'(x) = \psi(u x)$ for a unit $u$. Put $C = g^{-1} Y' g$. Let $x \in U^m_{\mathfrak{A}}$ with $\det x = 1$. Then $x \in J$, and $g x g^{-1} \in U^m_{\mathfrak{A}} \subseteq J'$, since $U^m_{\mathfrak{A}}$ is normal in $\mathfrak{K}_{\mathfrak{A}}$ (Proposition 3.9.2, part 2). Both elements have determinant $1$. By Lemma 3.14.15, part 2, and the intertwining,
$$\psi(\mathrm{tr}(Y(x - 1))) = \Lambda(x) = \Lambda'(g x g^{-1}) = \psi'(\mathrm{tr}(Y'(g x g^{-1} - 1))) = \psi(u \, \mathrm{tr}(C (x - 1))).$$
So $\psi_{u C - Y}(x) = 1$. Now $Y$ and $Y'$ lie in $\mathfrak{P}^{-n}_{\mathfrak{A}}$, and so does $C$, by Proposition 3.9.2, part 3. So $u C - Y \in \mathfrak{P}^{-n}_{\mathfrak{A}} = \mathfrak{P}^{1-2m}_{\mathfrak{A}}$. Proposition 3.15.5 with $k = m \ge 1$ gives the claim with $c = (u C - Y)_{22}$. $\square$

**Example 3.15.8 (the unit is needed).** Let $D$ be a datum, let $u \in \mathcal{O}_K^\times$, and let $D'$ have $\psi' = \psi(u^{-1} \cdot)$ and $\alpha' = u \alpha$, with the rest of $D$ unchanged. Then $\psi'_{\alpha'} = \psi_\alpha$, and the compatibility of $(\alpha', \xi)$ for $\psi'$ is the compatibility of $(\alpha, \xi)$ for $\psi$. So $D'$ is a datum for the same pair, with $\Lambda' = \Lambda$, and $g = 1$ intertwines. Here Proposition 3.15.2 gives the unit $u^{-1}$, and the congruence holds with $c = 0$: $u^{-1} Y' - Y = 0$. Without the factor $u$, the matrix $Y' - Y = (u - 1) Y$ need not lie in $K + \mathfrak{P}^{1-m}_{\mathfrak{A}}$.

### The discriminant and the conjugate of $\alpha$

The congruence of Theorem 3.15.7 compares $u g^{-1} Y' g - c$ with $Y$. We study the discriminant of both sides. The following identities hold over any field.

**Lemma 3.15.9 (identities for $2 \times 2$ matrices).** Let $Y, Z \in M_2(K)$, $g \in GL_2(K)$ and $u, c \in K$.
1. (Cayley-Hamilton.) $Y^2 - \mathrm{tr}(Y) Y + \det(Y) = 0$.
2. $\mathrm{tr}(Y) \cdot 1 = Y + \mathrm{adj}(Y)$, and $\mathrm{adj}(Y + Z) = \mathrm{adj}(Y) + \mathrm{adj}(Z)$.
3. $(Y - \mathrm{adj}(Y))^2 = \mathrm{disc}(Y) \cdot 1$.
4. $\mathrm{disc}(g^{-1} Y g) = \mathrm{disc}(Y)$.
5. $\mathrm{disc}(u Y - c) = u^2 \, \mathrm{disc}(Y)$.

Lean: `Langlands.LocalGL2.mul_self_sub_trace_smul_add_det_smul`, `Langlands.LocalGL2.trace_smul_one_eq_add_adjugate`, `Langlands.LocalGL2.adjugate_add_fin_two`, `Langlands.LocalGL2.sub_adjugate_mul_self`, `Langlands.LocalGL2.disc_conj`, `Langlands.LocalGL2.disc_smul_sub_smul_one`

*Proof.* Parts 1 and 2 are computations with the entries: $\mathrm{adj}(Y)$ has the entries $Y_{22}, -Y_{12}, -Y_{21}, Y_{11}$, which are linear in $Y$. Part 3: by part 2, $Y - \mathrm{adj}(Y) = 2Y - \mathrm{tr}(Y)$, and by part 1,
$$(2Y - \mathrm{tr}(Y))^2 = 4 Y^2 - 4 \mathrm{tr}(Y) Y + \mathrm{tr}(Y)^2 = \mathrm{tr}(Y)^2 - 4 \det(Y).$$
Part 4: conjugation does not change the trace and the determinant. Part 5: $\mathrm{tr}(u Y - c) = u \, \mathrm{tr}(Y) - 2c$ and $\det(u Y - c) = u^2 \det(Y) - u c \, \mathrm{tr}(Y) + c^2$. So $\mathrm{disc}(u Y - c) = u^2 \mathrm{tr}(Y)^2 - 4 u c \, \mathrm{tr}(Y) + 4 c^2 - 4 u^2 \det(Y) + 4 u c \, \mathrm{tr}(Y) - 4 c^2 = u^2 \mathrm{disc}(Y)$. $\square$

**Lemma 3.15.10 (the discriminant is continuous).** Let $a \le b$ be integers, $X \in \mathfrak{P}^a_{\mathfrak{A}}$ and $Z \in \mathfrak{P}^b_{\mathfrak{A}}$. Then $\mathrm{disc}(X + Z) - \mathrm{disc}(X) \in \mathfrak{p}_K^{b_{a+b}(1, 1)}$.

Lean: `Langlands.LocalGL2.disc_add_sub_disc_mem`, `Langlands.LocalGL2.adjugate_mem_radPow`

*Proof.* The adjugate maps $\mathfrak{P}^k_{\mathfrak{A}}$ into itself, since it exchanges the two diagonal entries, whose bounds are equal, and changes only the signs of the other two. Put $W = X - \mathrm{adj}(X) \in \mathfrak{P}^a_{\mathfrak{A}}$ and $V = Z - \mathrm{adj}(Z) \in \mathfrak{P}^b_{\mathfrak{A}}$. By Lemma 3.15.9, parts 2 and 3, $\mathrm{disc}(X + Z) \cdot 1 = (W + V)^2$ and $\mathrm{disc}(X) \cdot 1 = W^2$. The difference is $W V + V W + V^2$. By Proposition 3.9.2, part 1, $W V$ and $V W$ lie in $\mathfrak{P}^{a+b}_{\mathfrak{A}}$, and $V^2 \in \mathfrak{P}^{2b}_{\mathfrak{A}} \subseteq \mathfrak{P}^{a+b}_{\mathfrak{A}}$. A scalar matrix $d \cdot 1$ lies in $\mathfrak{P}^{a+b}_{\mathfrak{A}}$ exactly when $v_K(d) \ge b_{a+b}(1, 1)$. $\square$

For an element of $L$, the discriminant of its matrix is a square in $L$.

**Lemma 3.15.11 (a minimal element is far from its conjugate).** Let $p \ne 2$, let $v$ be a basis of $L$ adapted to $\mathfrak{A}$, and let $\alpha \in L$ be minimal of level $n$.
1. For each $x \in L$, $\mathrm{disc}(M_v(x)) = (x - \sigma x)^2$.
2. $\alpha - \sigma\alpha \notin \mathfrak{p}_L^{1-n}$.
3. $\delta = \mathrm{disc}(M_v(\alpha))$ is not $0$, and $e_{\mathfrak{A}} \, v_K(\delta) \le -2n$.

Lean: `Langlands.LocalGL2.algebraMap_disc_leftMulMatrix`, `Langlands.LocalGL2.IsMinimalElt.sub_galConj_not_mem`, `Langlands.LocalGL2.algebraMap_mem_ordBall_zero`, `Langlands.LocalGL2.disc_ne_zero_and_ord_le`

*Proof.* Part 1. The trace and the determinant of $M_v(x)$ are $\mathrm{tr}_{L/K}(x) = x + \sigma x$ and $N_{L/K}(x) = x \sigma x$. So the discriminant is $(x + \sigma x)^2 - 4 x \sigma x = (x - \sigma x)^2$. Part 2. Put $c = \mathrm{tr}_{L/K}(\alpha)/2 \in K$. Then $\alpha - c = (\alpha - \sigma\alpha)/2$, and $1/2 \in \mathcal{O}_L$ since $p \ne 2$. If $\alpha - \sigma \alpha \in \mathfrak{p}_L^{1-n}$, then $\alpha \in K + \mathfrak{p}_L^{1-n}$, which contradicts Definition 3.9.9. Part 3. By part 2, $\alpha - \sigma\alpha \ne 0$ and $v_L(\alpha - \sigma\alpha) \le -n$. By part 1, $v_L(\delta) \le -2n$. On $K$, $v_L = e(L|K) \, v_K$, and $e(L|K) = e_{\mathfrak{A}}$ by Definition 3.9.6. $\square$

The next proposition is the key step for both statements. The matrix $g^{-1} M_v(\beta) g$ has the characteristic polynomial of $\beta$. If it is close to $M_v(\alpha)$, then the polynomial of $\beta$ nearly vanishes at $\alpha$, so $\beta$ is close to $\alpha$ or to $\sigma\alpha$.

**Proposition 3.15.12 (near $\alpha$ or near its conjugate).** Let $p \ne 2$, let $v$ be adapted to $\mathfrak{A}$, let $\alpha \in L$ be minimal of level $n$, and let $m \le n + 1$. Let $g \in G$ and $\beta \in L$ with $g^{-1} M_v(\beta) g - M_v(\alpha) \in \mathfrak{P}^{1-m}_{\mathfrak{A}}$. Then $\beta - \alpha \in \mathfrak{p}_L^{1-m}$ or $\beta - \sigma\alpha \in \mathfrak{p}_L^{1-m}$.

Lean: `Langlands.LocalGL2.sub_mem_or_sub_galConj_mem`, `Langlands.LocalGL2.mem_ordBall_of_mul_mem_of_not_mem`, `Langlands.LocalGL2.IsAdapted.leftMulMatrix_mem_radPow_iff`

*Proof.* Put $X = M_v(\alpha)$, $B = g^{-1} M_v(\beta) g$ and $Z = B - X \in \mathfrak{P}^{1-m}_{\mathfrak{A}}$. By Proposition 3.9.7, part 1, $X \in \mathfrak{P}^{-n}_{\mathfrak{A}}$. Since $1 - m \ge -n$, also $Z$ and $B = X + Z$ lie in $\mathfrak{P}^{-n}_{\mathfrak{A}}$. The matrix $B$ has trace $\mathrm{tr}_{L/K}(\beta)$ and determinant $N_{L/K}(\beta)$. In $L$,
$$(\alpha - \beta)(\alpha - \sigma\beta) = \alpha^2 - \mathrm{tr}_{L/K}(\beta) \alpha + N_{L/K}(\beta).$$
Since $M_v$ is a homomorphism of $K$-algebras, the matrix of this element is $X^2 - \mathrm{tr}(B) X + \det(B)$. Substitute $X = B - Z$ and use Lemma 3.15.9, part 1, for $B$:
$$X^2 - \mathrm{tr}(B) X + \det(B) = -B Z - Z B + Z^2 + \mathrm{tr}(B) Z.$$
By Lemma 3.15.9, part 2, $\mathrm{tr}(B) Z = (B + \mathrm{adj}(B)) Z$. Each of the four terms lies in $\mathfrak{P}^{1-m-n}_{\mathfrak{A}}$, by Proposition 3.9.2, part 1. By Proposition 3.9.7, part 1, $(\alpha - \beta)(\alpha - \sigma\beta) \in \mathfrak{p}_L^{1-m-n}$.

Suppose that neither conclusion holds. Then $\alpha - \beta \notin \mathfrak{p}_L^{1-m}$, and $\alpha - \sigma\beta = -\sigma(\beta - \sigma\alpha) \notin \mathfrak{p}_L^{1-m}$, since $\sigma$ preserves $v_L$. If $x y \in \mathfrak{p}_L^{N}$ and $x \notin \mathfrak{p}_L^{M}$, then $v_L(x) \le M - 1$ and $y \in \mathfrak{p}_L^{N - M + 1}$. With $N = 1 - m - n$ and $M = 1 - m$ this gives $\alpha - \sigma\beta \in \mathfrak{p}_L^{1-n}$ and $\alpha - \beta \in \mathfrak{p}_L^{1-n}$. Now
$$\alpha - \sigma\alpha = (\alpha - \beta) - \sigma(\alpha - \sigma\beta) \in \mathfrak{p}_L^{1-n},$$
which contradicts Lemma 3.15.11, part 2. $\square$

**Example 3.15.13 (the second case occurs).** Let $p$ be odd, and let $D$ be the datum of Example 3.9.27, with $L = \mathbb{Q}_p(\sqrt p)$, $n = m = 1$, the basis $v = (\sqrt p, 1)$ and $\alpha = 1/(2\sqrt p)$. Then $\sigma\alpha = -\alpha$. Let $g = \mathrm{diag}(1, -1)$, which is the matrix of $\sigma$ in the basis $v$. The matrix of $\alpha$ is $Y = \left(\begin{smallmatrix} 0 & 1/(2p) \\ 1/2 & 0 \end{smallmatrix}\right)$, and $g^{-1} Y g = -Y$. Take $\beta = -\alpha = \sigma\alpha$. Then $g^{-1} M_v(\beta) g = Y$, so the hypothesis of Proposition 3.15.12 holds with difference $0$. Here $\beta - \sigma\alpha = 0$, but $\beta - \alpha = -2\alpha$ has valuation $-1$ and does not lie in $\mathfrak{p}_L^{0}$. So only the second case holds. The element $g$ is in $\mathfrak{K}_{\mathfrak{J}}$ but not in $J$: by Lemma 3.9.19, $g \in J$ would need $g^{-1} Y g - Y = -2Y \in \mathfrak{P}^{0}_{\mathfrak{J}}$, and the entry $-1/p$ of $-2Y$ at $(1, 2)$ does not lie in $\mathfrak{p}_K^{b_0(1, 2)} = \mathcal{O}_K$.

### The proofs of the two statements

In the second case of Proposition 3.15.12 the intertwining element does not lie in $J$, but a change of basis by $\sigma$ moves it into $J$. The next lemma extends Lemma 3.14.25 to this situation.

**Lemma 3.15.14 (conjugate characters from an intertwining element).** Let $D$ and $D'$ be data for $(L/K, \xi)$ and $(L/K, \xi')$ with the same chain order and the same basis $v$. Let $\tau$ be a $K$-automorphism of $L$, and let $b \in G$ satisfy $b^{-1} \iota_v(y) b = \iota_v(\tau y)$ for each $y \in L^\times$. If $g$ intertwines $\Lambda$ with $\Lambda'$ and $b g \in J$, then $\xi = \xi' \circ \tau$.

Lean: `Langlands.LocalGL2.TameDatum.eq_comp_of_intertwinesWith_of_mul_mem_J`

*Proof.* Put $h = b g \in J$. Let $y \in L^\times$ and $x = h^{-1} \iota_v(y) h$. Then $x \in J$, and
$$g x g^{-1} = g g^{-1} b^{-1} \iota_v(y) b g g^{-1} = \iota_v(\tau y) \in J'.$$
The intertwining gives $\Lambda'(\iota_v(\tau y)) = \Lambda(x) = \Lambda(h)^{-1} \Lambda(\iota_v(y)) \Lambda(h) = \Lambda(\iota_v(y))$. By Lemma 3.13.7, $\xi'(\tau y) = \xi(y)$. $\square$

For $b = 1$ and $\tau = 1$ this is Lemma 3.14.25.

**Theorem 3.15.15 (`TypeNormalizerSameBasisIso`, [BH06] 15.7 and 20.2).** Let $p \ne 2$. Let $D$ and $D'$ be data for $(L/K, \xi)$ and $(L/K, \xi')$ with the same chain order $\mathfrak{A}$, the same basis $v$ and the same level $n$, and let $g \in \mathfrak{K}_{\mathfrak{A}}$ intertwine $\Lambda$ with $\Lambda'$. Then $\xi = \xi'$ or $\xi = \xi' \circ \sigma$. So `TypeNormalizerSameBasisIso` holds for every $K$.

Lean: `Langlands.LocalGL2.leftMulMatrix_smul_sub`, `Langlands.LocalGL2.inv_conj_mem_radPow_of_mem_normalizer`, `Langlands.LocalGL2.typeNormalizerSameBasisIso_holds`

*Proof.* Let $Y = M_v(\alpha)$ and $Y' = M_v(\alpha')$. Theorem 3.15.7 gives a unit $u$ and $c \in K$ with $u g^{-1} Y' g - Y - c \in \mathfrak{P}^{1-m}_{\mathfrak{A}}$. Put $\beta = u \alpha' - c \in L$. Its matrix is $u Y' - c$, and $g^{-1}(u Y' - c) g = u g^{-1} Y' g - c$. So $g^{-1} M_v(\beta) g - Y \in \mathfrak{P}^{1-m}_{\mathfrak{A}}$. Since $m \le n + 1$, Proposition 3.15.12 applies. Recall that $1 - m = m - n$, since $n = 2m - 1$, and that conjugation by an element of $\mathfrak{K}_{\mathfrak{A}}$ preserves each $\mathfrak{P}^k_{\mathfrak{A}}$.

Case 1: $\beta - \alpha \in \mathfrak{p}_L^{1-m}$. Then $M_v(\alpha - \beta) \in \mathfrak{P}^{1-m}_{\mathfrak{A}}$ by Proposition 3.9.7, part 1, and
$$g^{-1} Y g - Y = g^{-1} M_v(\alpha - \beta) g + (g^{-1} M_v(\beta) g - Y) \in \mathfrak{P}^{1-m}_{\mathfrak{A}} = \mathfrak{P}^{m-n}_{\mathfrak{A}}.$$
By Lemma 3.9.19 with $s = m$, $g \in L^\times U^m_{\mathfrak{A}} = J$. Lemma 3.14.25 gives $\xi = \xi'$.

Case 2: $\beta - \sigma\alpha \in \mathfrak{p}_L^{1-m}$. Let $w = (\sigma v_1, \sigma v_2)$. Since $\sigma$ preserves $v_L$, this basis is again adapted to $\mathfrak{A}$. Let $b$ be the change of basis from $v$ to $w$. By Lemma 3.14.23, $b \in \mathfrak{K}_{\mathfrak{A}}$. For $x \in L$ we have $x \sigma(v_j) = \sigma(\sigma(x) v_j)$, so the matrix of $x$ in the basis $w$ is $M_v(\sigma x)$. By Lemma 3.13.4, part 1, $b^{-1} M_v(x) b = M_v(\sigma x)$. Then $b g \in \mathfrak{K}_{\mathfrak{A}}$ and
$$(b g)^{-1} Y (b g) - Y = g^{-1} M_v(\sigma\alpha - \beta) g + (g^{-1} M_v(\beta) g - Y) \in \mathfrak{P}^{m-n}_{\mathfrak{A}}.$$
By Lemma 3.9.19, $b g \in J$. Lemma 3.15.14 with $\tau = \sigma$ gives $\xi = \xi' \circ \sigma$. $\square$

In Example 3.15.13 the element $b$ is $\mathrm{diag}(1, -1) = g$, and $b g = 1 \in J$.

The field step for the Iwahori order uses the discriminant. For $p \ne 2$ there are two ramified quadratic extensions of $K$ up to isomorphism, and the discriminant of $\alpha$ tells them apart modulo squares.

**Theorem 3.15.16 (`TypeNormalizerRamifiedField`, [BH06] 15.7 and 20.2).** Let $p \ne 2$. Let $D$ and $D'$ be data for $(L/K, \xi)$ and $(L'/K, \xi')$, both for $\mathfrak{J}$ and with the same level $n$, and let $g \in \mathfrak{K}_{\mathfrak{J}}$ intertwine $\Lambda$ with $\Lambda'$. Then $L = L'$ as subfields of $\bar K$. So `TypeNormalizerRamifiedField` holds for every $K$.

Lean: `Langlands.LocalGL2.exists_sq_eq_of_mem_unitFilt`, `Langlands.LocalGL2.eq_of_mem_of_mem_of_not_mem_range`, `Langlands.LocalGL2.typeNormalizerRamifiedField_holds`

*Proof.* Let $Y = M_v(\alpha)$ and $Y' = M_{v'}(\alpha')$, and let $\sigma'$ be the conjugation of $L'$. Theorem 3.15.7 gives a unit $u$ and $c \in K$ such that $Z = u g^{-1} Y' g - c - Y$ lies in $\mathfrak{P}^{1-m}_{\mathfrak{J}}$. Put $\delta = \mathrm{disc}(Y)$ and $d = \mathrm{disc}(Y + Z)$. By Lemma 3.15.9, parts 4 and 5, $d = \mathrm{disc}(u g^{-1} Y' g - c) = u^2 \, \mathrm{disc}(Y')$. By Lemma 3.15.11, $\delta = (\alpha - \sigma\alpha)^2 \ne 0$ and $\mathrm{disc}(Y') = (\alpha' - \sigma'\alpha')^2$. Since $e_{\mathfrak{J}} = 2$, part 3 of that lemma gives $v_K(\delta) \le -n$.

By Lemma 3.15.10 with $a = -n \le b = 1 - m$, $d - \delta \in \mathfrak{p}_K^{b}$ with $b = b_{1-m-n}(1, 1) = \lceil (1 - m - n)/2 \rceil$. Since $n = 2m - 1$, $(1 - m - n)/2 = (2 - 3m)/2 > 1 - 2m = -n$, as $m > 0$. So $b \ge 1 - n$, and $d/\delta - 1 = (d - \delta)/\delta$ has valuation at least $1 - n - v_K(\delta) \ge 1$. So $d/\delta \in 1 + \mathfrak{p}_K$. Since $p \ne 2$, Hensel's lemma gives $b_0 \in K^\times$ with $d/\delta = b_0^2$ (Exercise 52). Put $x_P = \alpha - \sigma\alpha \in L$ and $x_Q = \alpha' - \sigma'\alpha' \in L'$. In $\bar K$,
$$(u \, x_Q)^2 = d = b_0^2 \delta = (b_0 \, x_P)^2,$$
so $u x_Q = \pm b_0 x_P$, and $x_Q \in L$. The element $x_Q$ is not in $K$: otherwise $x_Q = \sigma' x_Q = -x_Q$, so $x_Q = 0$, which contradicts Lemma 3.15.11, part 2, for $\alpha'$. So $K(x_Q)$ is a quadratic extension of $K$ inside both $L$ and $L'$, and $L = K(x_Q) = L'$. $\square$

**Remark 3.15.17 (comparison with Remarks 3.14.30 and 3.14.31).** The proofs follow the plans of the two remarks. Step 1 of Remark 3.14.30 is Proposition 3.15.2, and step 3 is Proposition 3.15.5 in the form of Theorem 3.15.7. In steps 4 and 5, the discriminant of the whole matrix $Y + Z$ replaces the element $\alpha_0$, and Lemma 3.15.10 replaces the expansion $Y_0 Z + Z Y_0 + Z^2$. The closeness of $\beta$ to $\alpha$ or to $\bar\alpha$ in Remark 3.14.31 is Proposition 3.15.12. In case 2 the library does not transport $D'$. It changes the basis by $\sigma$ and uses Lemma 3.15.14, which needs no new datum. The argument of Theorem 3.15.16 also works for $\mathfrak{M}$: there $v_K(\delta) \le -2n$ and $b_{1-m-n}(1, 1) = 1 - m - n$, and $1 - m - n - v_K(\delta) \ge 1 + n - m \ge 1$. This gives a second proof of Proposition 3.14.24 in the presence of an intertwining element. The library does not need it.

**Theorem 3.15.18 (`TypeRepInjective`, [BH06] 15.6, 15.7 and 20.2).** For each $K$, the statements `TypeIntertwiningNormalizerIso`, `TypeIntertwiningIso` and `TypeRepInjective` hold. So if $\pi_D \cong \pi_{D'}$ for two tame data $D$ and $D'$, then the pairs of $D$ and $D'$ are $K$-isomorphic.

Lean: `Langlands.LocalGL2.typeIntertwiningNormalizerIso_holds`, `Langlands.LocalGL2.typeIntertwiningIso_holds`, `Langlands.LocalGL2.typeRepInjective_holds`

*Proof.* Theorems 3.15.15 and 3.15.16 are the two statements of Definition 3.14.26. Theorem 3.14.29 gives `TypeIntertwiningNormalizerIso` and `TypeRepInjective`, and Corollary 3.14.21 gives `TypeIntertwiningIso`. $\square$

So the inputs on cuspidal types in Definition 3.10.27 are now all proved except input 5, `UncoveredParametrization`.

### The zeta integrals of the principal series

We turn to fact 4 of Definition 3.11.31, `PSLFactorIrreducible`. Let $\chi_1$ and $\chi_2$ be smooth characters of $K^\times$. The principal series of $(\chi_1, \chi_2)$ is the space of functions $f : G \to \mathbb{C}$ that are invariant on the right under an open subgroup and satisfy
$$f(b x) = \chi_1(\alpha) \chi_2(\delta) |\alpha/\delta|^{1/2} f(x), \qquad b = \begin{pmatrix} \alpha & \beta \\ 0 & \delta \end{pmatrix},$$
with $G$ acting by right translation, $(\pi(g) f)(x) = f(x g)$. This is `Langlands.principalSeriesSpace`. For $f$ in this space and a Schwartz-Bruhat function $\Phi$ on $M_2(K)$ we study
$$I(\Phi, f, s) = \int_{M_2(K)} \Phi(x) f(x) |\det x|^{s - 3/2} \, dx,$$
where the integrand is $0$ on the singular matrices. If $f$ were a matrix coefficient, this would be the zeta integral of Section 3.11, whose integrand is $\Phi(x) f(x) |\det x|^{s + 1/2 - 2}$. We write $n^-(t) = x_-(t)$ for the lower unipotent matrices, $w = \left(\begin{smallmatrix} 0 & 1 \\ 1 & 0 \end{smallmatrix}\right)$, and we keep the notation $X = q^{-s}$, $Z(\varphi, \chi, s)$ and $L(s, \chi)$ of Section 3.14.

**Lemma 3.15.19 (coordinates).** Let $e : M_2(K) \to K^4$ send $x$ to $(a, b, c, d) = (x_{22}, x_{12}, x_{21}, x_{11})$, so that
$$e^{-1}(a, b, c, d) = \begin{pmatrix} d & b \\ c & a \end{pmatrix}, \qquad \det e^{-1}(a, b, c, d) = a d - b c.$$
It is a homeomorphism and an isomorphism of additive groups, and there is $c_0 > 0$ with $\int_{M_2(K)} h \, dx = c_0 \int_{K^4} h \circ e^{-1} \, d\mu^{\otimes 4}$ for each integrable $h$.

Lean: `Langlands.LocalGL2.psiE`, `Langlands.LocalGL2.psiEAdd`, `Langlands.LocalGL2.psi_symm_apply`, `Langlands.LocalGL2.psi_det_symm`, `Langlands.LocalGL2.psi_exists_scalar`

*Proof.* This is Lemma 3.14.33 with the coordinates in another order. The determinant is the function `plDet` of Section 3.14. $\square$

The order of the coordinates puts the bottom row $(c, a)$ of the matrix first. The Iwasawa decomposition on the big cell divides by the entry $a = x_{22}$.

**Lemma 3.15.20 (the integrand on the big cell).** Let $f$ be in the principal series of $(\chi_1, \chi_2)$, and let $x = e^{-1}(a, b, c, d)$ with $a \ne 0$ and $\det x \ne 0$. Put $\alpha = \det x / a$.
1. $x = \begin{pmatrix} \alpha & b \\ 0 & a \end{pmatrix} n^-(c/a)$, and
$$f(x) |\det x|^{s - 3/2} = f(n^-(c/a)) \, \chi_1(\alpha) |\alpha|^{s-1} \, \chi_2(a) |a|^{s-2}.$$
2. For $t \in K$ and $a d \ne 0$, the value of $f(x)|\det x|^{s - 3/2}$ at the point $(a, b, a t, d + t b)$ is $f(n^-(t)) \, \chi_1(d) |d|^{s-1} \, \chi_2(a) |a|^{s-2}$.

Lean: `Langlands.LocalGL2.psiMat`, `Langlands.LocalGL2.psiFn`, `Langlands.LocalGL2.psiUpper`, `Langlands.LocalGL2.psi_cpow`, `Langlands.LocalGL2.psi_fn_eq`, `Langlands.LocalGL2.psi_fn_sub`

*Proof.* Part 1. The product is
$$\begin{pmatrix} \alpha & b \\ 0 & a \end{pmatrix} \begin{pmatrix} 1 & 0 \\ c/a & 1 \end{pmatrix} = \begin{pmatrix} \alpha + b c/a & b \\ c & a \end{pmatrix},$$
and $\alpha + bc/a = (a d - b c)/a + b c/a = d$. So $f(x) = \chi_1(\alpha) \chi_2(a) |\alpha/a|^{1/2} f(n^-(c/a))$. Also $|\det x| = |\alpha| |a|$, and for $r_1, r_2 > 0$,
$$(r_1/r_2)^{1/2} (r_1 r_2)^{s - 3/2} = r_1^{s - 1} r_2^{s - 2}.$$
Part 2. At the point $(a, b, a t, d + t b)$ the determinant is $(d + t b) a - b a t = a d$, so $\alpha = d$ and $c/a = t$. Part 1 concludes. $\square$

The factor $\chi_2(a)|a|^{s-2}$ is not Tate's integrand. The Jacobian $|a|$ of the substitution $c = a t$ makes it one: $|a| \chi_2(a) |a|^{s-2} = \chi_2(a) |a|^{s-1}$ (`Langlands.LocalGL2.psi_abs_zetaFn`). This is the same mechanism as in Proposition 3.14.36. The function $t \mapsto f(n^-(t))$ remains, and it is locally constant.

**Lemma 3.15.21 (two facts on the principal series).** Let $f$ be in the principal series of $(\chi_1, \chi_2)$.
1. $f$ is locally constant on $G$, and $t \mapsto f(n^-(t))$ is locally constant on $K$.
2. The function $f_w : x \mapsto f(x w)$ is again in the principal series of $(\chi_1, \chi_2)$. For each matrix $x$, $f(x w) |\det(x w)|^{s - 3/2} = f_w(x) |\det x|^{s - 3/2}$, and in the coordinates of Lemma 3.15.19 right multiplication by $w$ is the map $\sigma(a, b, c, d) = (c, d, a, b)$.

Lean: `Langlands.LocalGL2.psi_isLocallyConstant`, `Langlands.LocalGL2.psi_lowerUnip_add`, `Langlands.LocalGL2.psi_isLocallyConstant_lower`, `Langlands.LocalGL2.psiW`, `Langlands.LocalGL2.psi_mem_w`, `Langlands.LocalGL2.psi_mat_of_det`, `Langlands.LocalGL2.psi_normAbs_neg_one`, `Langlands.LocalGL2.psi_mat_mul_w`, `Langlands.LocalGL2.psi_fn_swap`

*Proof.* Part 1. Let $U$ be open with $f(x u) = f(x)$ for $u \in U$. Then $f$ is constant on each coset $x U$, which is open. Since $n^-(t + h) = n^-(t) n^-(h)$ and $n^-(h) \in U$ for $h$ small, $f(n^-(t + h)) = f(n^-(t))$ for $h$ small. Part 2. Right translation commutes with left multiplication by $b$, so $f_w$ satisfies the same rule, and it is invariant under $w^{-1} U w$. Also $|\det(x w)| = |-\det x| = |\det x|$, and the integrand is $0$ on both sides when $\det x = 0$. For $x = e^{-1}(a, b, c, d)$, $x w$ has the two columns of $x$ exchanged, that is $x w = \left(\begin{smallmatrix} b & d \\ a & c \end{smallmatrix}\right)$, whose coordinates are $(c, d, a, b)$. $\square$

In Section 3.14 the exchange of the two rows gave a sign $\chi(-1)$. Here we exchange the two columns, and the sign is absorbed: the function $f_w$ replaces $f$, and $|\det|$ does not see the sign. The map $\sigma$ is the map `plSwap` of Lemma 3.14.35, so the regions $R_m$ of that lemma serve again.

**Proposition 3.15.22 (the change of variables on a region).** Let $m \ge 0$, let $F$ be locally constant with compact support on $K^4$, and let $f$ be in the principal series of $(\chi_1, \chi_2)$. Put
$$G_m(a, b, t, d) = \mathbf{1}_{\mathfrak{p}_K^m}(t) \, F(a, b, a t, d + t b) \, f(n^-(t)).$$
Then $G_m$ is locally constant with compact support. Let $s_0 = \max(s_0(\chi_1), s_0(\chi_2) + 1)$, where $s_0(\chi)$ is the bound of Section 3.14 for Tate's integral of $\chi$. For $\mathrm{Re}(s) > s_0$,
$$\int_{R_m} F(p) \, f(x_p) |\det x_p|^{s - 3/2} \, dp = \int_{K^4} G_m(a, b, t, d) \, \chi_2(a) |a|^{s-1} \, \chi_1(d) |d|^{s-1} \, d\mu^{\otimes 4},$$
where $x_p = e^{-1}(p)$, and both integrands are integrable.

Lean: `Langlands.LocalGL2.psiReg`, `Langlands.LocalGL2.psi_reg_eq`, `Langlands.LocalGL2.psiSub`, `Langlands.LocalGL2.psi_isLocallyConstant_sub`, `Langlands.LocalGL2.psi_hasCompactSupport_sub`, `Langlands.LocalGL2.psi_region_iter`, `Langlands.LocalGL2.psi_integrable_reg`, `Langlands.LocalGL2.psi_region_eq`, `Langlands.LocalGL2.psiBound`, `Langlands.LocalGL2.psi_norm_le_of_bound`

*Proof.* On $R_m$ we have $a \ne 0$, and Lemma 3.15.20, part 1, gives the integrand in closed form. Fix $a \ne 0$ and $b$, and integrate over $c$ and $d$. Substitute $c = a t$, so that $dc = |a| \, dt$ and the condition $c/a \in \mathfrak{p}_K^m$ becomes $t \in \mathfrak{p}_K^m$. Then substitute $d \mapsto d + t b$, a translation. By Lemma 3.15.20, part 2, the integrand becomes
$$\mathbf{1}_{\mathfrak{p}_K^m}(t) F(a, b, a t, d + t b) f(n^-(t)) \, |a| \chi_2(a) |a|^{s-2} \chi_1(d) |d|^{s-1},$$
and $|a| \chi_2(a) |a|^{s-2} = \chi_2(a) |a|^{s-1}$. The line $a = 0$ has measure $0$. The function $G_m$ is locally constant by Lemma 3.15.21, part 1, since $F$, the indicator of $\mathfrak{p}_K^m$ and the maps are locally constant or continuous. If $F$ vanishes outside $(\mathfrak{p}_K^M)^4$ with $M \le 0$, then $G_m$ vanishes outside the same box, as in Proposition 3.14.36, since $t \in \mathfrak{p}_K^m \subseteq \mathcal{O}_K$. For integrability: for $\mathrm{Re}(s) > s_0$ the numbers $|\chi_1(\varpi) q^{1-s}|$, $|\chi_2(\varpi) q^{1-s}|$ and $|\chi_2(\varpi) q^{2-s}|$ are at most $1$, so the functions $\chi_1(d)|d|^{s-1}$, $\chi_2(a)|a|^{s-1}$ and $\chi_2(a)|a|^{s-2}$ are bounded on each ball. On the region and on the support of $F$, $|\alpha| = |d - b c/a|$ is bounded, so the integrand on the left is bounded there, and it vanishes outside a box. The right side is bounded and has compact support. $\square$

**Theorem 3.15.23 (the integrals of the principal series).** Let $f$ be in the principal series of $(\chi_1, \chi_2)$ and let $\Phi$ be a Schwartz-Bruhat function on $M_2(K)$. Then $I(\Phi, f, s)$ is good for $L(s, \chi_1) L(s, \chi_2)$ in the sense of Definition 3.14.37: there are a polynomial $A$, an integer $k \ge 0$ and $s_1$ with $I(\Phi, f, s) = A(X) X^{-k} L(s, \chi_1) L(s, \chi_2)$ for $\mathrm{Re}(s) > s_1$.

Lean: `Langlands.LocalGL2.psi_fn_zero_zero`, `Langlands.LocalGL2.psi_split_pt`, `Langlands.LocalGL2.psi_swap_reg_eq`, `Langlands.LocalGL2.psi_split`, `Langlands.LocalGL2.psi_rhs`, `Langlands.LocalGL2.psi_good_rhs`, `Langlands.LocalGL2.psi_good_four`, `Langlands.LocalGL2.psi_good_mat`

*Proof.* By Lemma 3.15.19, $I(\Phi, f, s) = c_0 \int_{K^4} F(p) f(x_p) |\det x_p|^{s - 3/2} \, dp$ with $F = \Phi \circ e^{-1}$, which is locally constant with compact support. At the points with $a = c = 0$ the determinant is $0$, so the integrand vanishes. By Lemma 3.14.35, part 1, the other points lie in exactly one of $R_0$ and $\sigma^{-1}(R_1)$. On $\sigma^{-1}(R_1)$ substitute $p = \sigma(p')$, which preserves the measure. By Lemma 3.15.21, part 2, the integrand at $\sigma(p')$ is $F(\sigma p') f_w(x_{p'}) |\det x_{p'}|^{s - 3/2}$. So for $\mathrm{Re}(s) > s_0$,
$$\int_{K^4} F \, f \, |\det|^{s - 3/2} = \int_{R_0} F \, f \, |\det|^{s - 3/2} + \int_{R_1} (F \circ \sigma) \, f_w \, |\det|^{s - 3/2}.$$
Apply Proposition 3.15.22 to $(F, f)$ with $m = 0$ and to $(F \circ \sigma, f_w)$ with $m = 1$. Each term becomes an integral of a locally constant function $G$ with compact support against $\chi_2(a)|a|^{s-1} \chi_1(d)|d|^{s-1}$. By Lemma 3.14.34, $G$ is a finite sum of constants times products of indicators of balls in the four coordinates. By Fubini's theorem, the integral of one such product is
$$Z(\mathbf{1}_{t_1 + \mathfrak{p}_K^N}, \chi_2, s) \cdot \mu(t_2 + \mathfrak{p}_K^N) \cdot \mu(t_3 + \mathfrak{p}_K^N) \cdot Z(\mathbf{1}_{t_4 + \mathfrak{p}_K^N}, \chi_1, s).$$
By Lemma 3.14.38, part 4, the two zeta integrals are good for $L(s, \chi_2)$ and $L(s, \chi_1)$. By parts 1 and 2 of that lemma, the sum is good for $L(s, \chi_1) L(s, \chi_2)$. $\square$

The proof does not use any condition on $(\chi_1, \chi_2)$. It holds for the Steinberg pairs too. For $\chi_1 = \chi$ and $\chi_2 = \chi |\cdot|$ the character $\theta = (\chi |\cdot|^{1/2}) \circ \det$ lies in the principal series, and the theorem gives Theorem 3.14.39 again (Exercise 56).

**Example 3.15.24 (the spherical vector).** Let $\chi_1$ and $\chi_2$ be unramified, and let $f_0$ be the spherical function: $f_0(b k) = \chi_1(\alpha) \chi_2(\delta) |\alpha/\delta|^{1/2}$ for $b$ as above and $k \in GL_2(\mathcal{O}_K)$. It is well defined, since $\chi_1$ and $\chi_2$ are trivial on $\mathcal{O}_K^\times$. Let $\Phi = \mathbf{1}_{M_2(\mathcal{O}_K)}$, so $F = \mathbf{1}_{\mathcal{O}_K^4}$, and let $\mu(\mathcal{O}_K) = 1$. Then $F \circ \sigma = F$ and $f_{0, w} = f_0$, since $w \in GL_2(\mathcal{O}_K)$. For $t \in \mathcal{O}_K$, $n^-(t) \in GL_2(\mathcal{O}_K)$ and $f_0(n^-(t)) = 1$. As in Proposition 3.14.40, $G_m$ is the indicator of $\mathcal{O}_K \times \mathcal{O}_K \times \mathfrak{p}_K^m \times \mathcal{O}_K$. By Theorem 3.2.18, part 3, $Z(\mathbf{1}_{\mathcal{O}_K}, \chi, s) = \mu(\mathcal{O}_K^\times) L(s, \chi)$ for unramified $\chi$. So
$$I(\Phi, f_0, s) = c_0 \, (1 + q^{-1}) (1 - q^{-1})^2 \, L(s, \chi_1) L(s, \chi_2) = c_0 \, (1 - q^{-1})(1 - q^{-2}) \, L(s, \chi_1) L(s, \chi_2).$$
The constant is the one of Proposition 3.14.40, and it is not $0$. So in the unramified case one integral already gives the whole product $L(s, \chi_1) L(s, \chi_2)$. This is clause 3 of `IsGJLFactor` in its simplest form, once the integral is known to be a zeta integral.

The integrals $I(\Phi, f, s)$ are not yet the zeta integrals of Section 3.11. Those use a matrix coefficient $x \mapsto \lambda(\pi(x) v)$ with a smooth linear form $\lambda$ on the principal series. Three statements connect the two kinds of integral.

**Definition 3.15.25 (the three statements on the zeta integrals).** Let $\chi_1$ and $\chi_2$ run over the smooth characters of $K^\times$, and let $\pi$ be the principal series of $(\chi_1, \chi_2)$.
1. `PSZetaCoeffSpan` for $K$ says: for each Schwartz-Bruhat $\Phi$, each $v$ in the principal series and each smooth linear form $\lambda$, there are Schwartz-Bruhat functions $\Psi_1, \ldots, \Psi_j$ and constants $c_i$ with $Z(\Phi, s, \lambda(\pi(\cdot) v)) = \sum_i c_i \, I(\Psi_i, v, s)$ for $\mathrm{Re}(s)$ large.
2. `PSZetaRealize` for $K$ says: for each Schwartz-Bruhat $\Phi$ and each $v$ there is a smooth linear form $\lambda$ with $Z(\Phi, s, \lambda(\pi(\cdot) v)) = I(\Phi, v, s)$ for $\mathrm{Re}(s)$ large.
3. `PSZetaGenerates` for $K$ says: there are Schwartz-Bruhat functions $\Phi_i$, vectors $v_i$, polynomials $A_i$ and $k \ge 0$ with $L(s, \chi_1) L(s, \chi_2) = \sum_i A_i(X) X^{-k} \, I(\Phi_i, v_i, s)$ for $\mathrm{Re}(s)$ large.

Lean: `Langlands.LocalGL2.PSZetaCoeffSpan`, `Langlands.LocalGL2.PSZetaRealize`, `Langlands.LocalGL2.PSZetaGenerates`

**Theorem 3.15.26 (the $L$-factor of the principal series).** Assume `PSZetaCoeffSpan`, `PSZetaRealize` and `PSZetaGenerates` for $K$. For all smooth characters $\chi_1, \chi_2$ of $K^\times$, the Godement-Jacquet $L$-factor of the principal series of $(\chi_1, \chi_2)$ is $L(s, \chi_1) L(s, \chi_2)$. In particular `PSLFactorIrreducible` holds for $K$.

Lean: `Langlands.LocalGL2.psi_exists_poly`, `Langlands.LocalGL2.psi_isGJLFactor`, `Langlands.LocalGL2.psLFactorIrreducible_of`

*Proof.* We check the three clauses of `IsGJLFactor`. Clause 1: $L(s, \chi_i) = P_i(X)^{-1}$ with $P_i(0) = 1$, where $P_i = 1 - \chi_i(\varpi) X$ for unramified $\chi_i$ and $P_i = 1$ otherwise. So the product is $(P_1 P_2)(X)^{-1}$ and $(P_1 P_2)(0) = 1$. Clause 2: by `PSZetaCoeffSpan`, each zeta integral is a finite combination of integrals $I(\Psi_i, v, s)$ for $\mathrm{Re}(s)$ large. Each of these is good for $L(s, \chi_1) L(s, \chi_2)$ by Theorem 3.15.23, and Lemma 3.14.38, part 1, concludes. Clause 3: `PSZetaGenerates` gives $L(s, \chi_1) L(s, \chi_2) = \sum_i A_i(X) X^{-k} I(\Phi_i, v_i, s)$ for $\mathrm{Re}(s) > s_0$. For each $i$, `PSZetaRealize` gives $\lambda_i$ and $s_{1,i}$ with $I(\Phi_i, v_i, s) = Z(\Phi_i, s, \lambda_i(\pi(\cdot) v_i))$ for $\mathrm{Re}(s) > s_{1,i}$. For $\mathrm{Re}(s) > \max(s_0, \sum_i |s_{1,i}|)$ all these equations hold, so $L(s, \chi_1) L(s, \chi_2)$ is a combination of zeta integrals with the Laurent polynomials $A_i(X) X^{-k}$ as coefficients. Finally `PSLFactorIrreducible` is the special case where neither pair is a Steinberg pair. $\square$

**Remark 3.15.27 (the intended proofs of the three statements).** The Lean file gives the intended proofs, after Godement and Jacquet, section 3, [JL70], section 3, and [BH06], Chapter 6, section 26.
1. `PSZetaCoeffSpan`. By the duality of induced representations ([BH06], Chapter 1), a smooth linear form is $\lambda(f) = \int_{GL_2(\mathcal{O}_K)} \varphi(k) f(k) \, dk$ for a function $\varphi$ in the principal series of $(\chi_1^{-1}, \chi_2^{-1})$. Then $\lambda(\pi(x) v) = \int \varphi(k) v(k x) \, dk$. Substitute $x \mapsto k^{-1} x$ in the integral over $M_2(K)$, which preserves $dx$ and $|\det x|$. This gives $Z = \int \varphi(k) \, I(\Phi(k^{-1} \cdot), v, s) \, dk$. The functions $\varphi$ and $k \mapsto \Phi(k^{-1} \cdot)$ are locally constant on the compact group $GL_2(\mathcal{O}_K)$, so the integral over $k$ is a finite sum.
2. `PSZetaRealize`. Take an open compact subgroup $U$ of $GL_2(\mathcal{O}_K)$ with $\Phi(u x) = \Phi(x)$ for $u \in U$, and let $\lambda(f)$ be the mean of $f$ over $U$. It is fixed by $U$, so it is smooth, and the same substitution gives $Z(\Phi, s, \lambda(\pi(\cdot) v)) = I(\Phi, v, s)$.
3. `PSZetaGenerates`. Take $v$ supported on $B \, n^-(\varpi^r \mathcal{O}_K)$ with $v(n^-(t)) = 1$ there, for $r$ large, and $\Phi$ a product of indicators of balls in the coordinates of Lemma 3.15.20. Then $I(\Phi, v, s)$ is a nonzero constant times $Z(\varphi_1, \chi_1, s) Z(\varphi_2, \chi_2, s)$ for two Schwartz-Bruhat functions on $K$, and Corollary 3.2.19 gives $L(s, \chi_1)$ and $L(s, \chi_2)$ from such integrals. Example 3.15.24 is the case of unramified characters, with $r = 0$ and the spherical vector.

The three statements need the duality between the principal series and its contragredient in an explicit form, and Fubini's theorem on $GL_2(\mathcal{O}_K) \times M_2(K)$. The library has neither yet.

### Wild inertia is pro-$p$

Let $\bar{\mathcal{O}}$ be the integral closure of $\mathcal{O}_K$ in $\bar K$. It is a local ring, with maximal ideal $\bar{\mathfrak{m}}$, the elements of positive valuation for the unique extension of $v_K$. Recall from Section 3.12 that $P_K$ is the normal subgroup of $W_K$ generated by the $w \in I_K$ with $w(x) - x \in \bar{\mathfrak{m}} x$ for each $x \in \bar{\mathcal{O}}$. The proof that $P_K$ is pro-$p$ rests on a lemma about a group acting on a local ring.

**Lemma 3.15.28 (elements close to the identity).** Let $R$ be a local ring with maximal ideal $\mathfrak{m}_R$, and let $g$ be a ring automorphism of $R$ with $g(x) - x \in \mathfrak{m}_R x$ for each $x \in R$.
1. $g(\mathfrak{m}_R) \subseteq \mathfrak{m}_R$.
2. Let $N \ge 1$ be an integer that is a unit in $R$, and let $y \in R$ with $g^N(y) = y$. Then $g(y) = y$.

Lean: `Langlands.LocalGL2.wgo_smul_mem_maximalIdeal`, `Langlands.LocalGL2.wgo_smul_eq_of_pow_smul_eq`

*Proof.* Part 1. For $x \in \mathfrak{m}_R$, $g(x) = x + a x$ with $a \in \mathfrak{m}_R$, and this lies in $\mathfrak{m}_R$. Part 2. Put $d = g(y) - y$. By hypothesis $g(d) = (1 + b) d$ with $b \in \mathfrak{m}_R$. We show by induction that $g^k(y) - y = (k + c_k) d$ with $c_k \in \mathfrak{m}_R$, for each $k \ge 0$. For $k = 0$ take $c_0 = 0$. If it holds for $k$, then
$$g^{k+1}(y) - y = g(g^k(y) - y) + (g(y) - y) = (k + g(c_k))(1 + b) d + d = (k + 1 + c_{k+1}) d,$$
with $c_{k+1} = g(c_k) + b(k + g(c_k))$. By part 1, $g(c_k) \in \mathfrak{m}_R$, so $c_{k+1} \in \mathfrak{m}_R$. For $k = N$ we get $0 = (N + c_N) d$. Since $N$ is a unit and $c_N \in \mathfrak{m}_R$, the element $N + c_N$ is a unit. So $d = 0$. $\square$

**Lemma 3.15.29 (the subgroup near the identity).** Let a group $H$ act on a local ring $R$ by ring automorphisms. The elements $h \in H$ with $h(x) - x \in \mathfrak{m}_R x$ for each $x \in R$ form a normal subgroup of $H$.

Lean: `Langlands.LocalGL2.wgoNearId`, `Langlands.LocalGL2.wgo_smul_mem_maximalIdeal_of_group`, `Langlands.LocalGL2.wgoNearId_normal`

*Proof.* Let $g$ and $h$ be in the set, and $x \in R$. Write $h(x) = (1 + a) x$ and $g(x) = (1 + a') x$ with $a, a' \in \mathfrak{m}_R$. Then $g h(x) - x = g(a) g(x) + (g(x) - x) = (g(a)(1 + a') + a') x$, and $g(a) \in \mathfrak{m}_R$ by Lemma 3.15.28, part 1. For the inverse, put $y = h^{-1}(x)$. Then $x = h(y) = (1 + a) y$ with $a \in \mathfrak{m}_R$, so $y = (1 + a)^{-1} x$ and $h^{-1}(x) - x = y - x = -a y = -a(1 + a)^{-1} x$. For normality, let $k \in H$ and $y = k^{-1}(x)$. Then $k h k^{-1}(x) - x = k(h(y) - y) = k(a y) = k(a) x$ with $h(y) = (1+a) y$. A ring automorphism of a local ring maps the maximal ideal onto a maximal ideal, so $k(a) \in \mathfrak{m}_R$. $\square$

**Theorem 3.15.30 (`WildInertiaProP`).** For each open normal subgroup $U$ of $W_K$ and each $x \in P_K$, there is $k \ge 0$ with $x^{p^k} \in U$. So fact 2 of Definition 3.12.18 holds for every $K$.

Lean: `Langlands.LocalGL2.wgo_toGalois_mem_nearId`, `Langlands.LocalGL2.wgo_isUnit_natCast`, `Langlands.LocalGL2.wildInertiaProP_holds`

*Proof.* Let $H$ be the subgroup of the $w \in W_K$ that act on $\bar{\mathcal{O}}$ in the subgroup of Lemma 3.15.29. It is normal and it contains the generators of $P_K$, so it contains $P_K$. By Definition 2.1.1, $I_K$ is open in $W_K$ with its profinite topology. So $U \cap I_K$ is an open subgroup of the profinite group $I_K$, and it contains $I_K \cap G_E$ for a finite extension $E$ of $K$ in $\bar K$. The subgroup $W_E = W_K \cap G_E$ has finite index in $W_K$, so $x^N \in W_E$ for some $N \ge 1$. Write $N = p^e N'$ with $p \nmid N'$, and put $\tau = x^{p^e}$. Then $\tau \in P_K \subseteq H$ and $\tau^{N'} = x^N$ fixes $E$. Let $z \in E$. Since $z$ is algebraic over $K$, there is $c \in \mathcal{O}_K \smallsetminus \{0\}$ with $c z \in \bar{\mathcal{O}}$, and $c z \in E$. The integer $N'$ is a unit in $\bar{\mathcal{O}}$, since its image in the residue field, of characteristic $p$, is not $0$. By Lemma 3.15.28, part 2, applied to $\tau$ and $y = c z$, we get $\tau(c z) = c z$. Since $\tau$ fixes $c \in K$ and $c \ne 0$, $\tau(z) = z$. So $\tau \in W_E$. Also $\tau \in P_K \subseteq I_K$. So $\tau \in I_K \cap G_E \subseteq U$. $\square$

The proof does not use the normality of $U$. It is a proof of [Ser79], Chapter IV, section 2, Corollary 3 to Proposition 7, in the form that the definitions of Section 3.12 need. Serre proves that the ramification group $G_1$ of a finite Galois extension is a $p$-group by the injection $G_1/G_2 \to U^1_E/U^2_E$ and its analogues. The lemma above gives a shorter route for the statement on orders (Exercise 57).

**Example 3.15.31 (a tame element is not near the identity).** Let $\ell \ne p$ be a prime, $\zeta \in \bar K$ a primitive $\ell$-th root of unity and $y = \varpi^{1/\ell}$ a root of $X^\ell - \varpi$. The field $K^{ur}$ contains $\zeta$, and $X^\ell - \varpi$ is irreducible over $K^{ur}$ by Eisenstein's criterion. So there is $w \in I_K$ with $w(y) = \zeta y$. Then $w(y) - y = (\zeta - 1) y$, and $\zeta - 1$ is a unit of $\bar{\mathcal{O}}$, since $\prod_{i=1}^{\ell-1} (1 - \zeta^i) = \ell$. So $w$ is not a generator of $P_K$. More: $w$ is not in $P_K$. Otherwise Lemma 3.15.28, part 2, with $N = \ell$ and $w^\ell(y) = y$ would give $w(y) = y$. This agrees with Proposition 2.1.6: the tame character $t_\ell$ is trivial on $P_K$ and $t_\ell(w) = \zeta \ne 1$.

**Corollary 3.15.32 (the Galois side from four inputs).** Let `GaloisTameRemainingInputs` be the conjunction of `ArtinConjCompat` for each separable quadratic $L/K$, `TameInertiaProcyclic`, `OpenIndexTwoQuad` and `WildArtinUnits`. If it holds for $K$, then `GaloisTameOpenInputs` holds for $K$, and so does `GaloisTameParametrization`.

Lean: `Langlands.LocalGL2.GaloisTameRemainingInputs`, `Langlands.LocalGL2.GaloisTameRemainingInputs.toGaloisTameOpenInputs`, `Langlands.LocalGL2.galoisTameParametrization_of_remainingInputs`

*Proof.* `GaloisTameOpenInputs` is the conjunction of facts 1, 2, 3, 4 and 7 of Definition 3.12.18. Fact 2 is Theorem 3.15.30. Corollary 3.12.34 concludes. $\square$

### What is open for $GL_2$, $p \ne 2$

**Corollary 3.15.33 (the reduction as it stands).** Let $p \ne 2$. The statement `Langlands.LocalLanglandsGL2Odd` follows, for all $K$, from:
1. `ArtinCompat` and `Rectifier`, inputs 1 and 4 of Definition 3.9.30;
2. the four facts of `GaloisTameRemainingInputs`, Corollary 3.15.32;
3. `SupercuspidalZetaLaurent`, Definition 3.11.19;
4. `PSZetaCoeffSpan`, `PSZetaRealize` and `PSZetaGenerates`, Definition 3.15.25, and `PSLFactorSteinberg`, fact 6 of Definition 3.11.31;
5. `UncoveredParametrization`, input 5 of Definition 3.10.27.

Lean: `Langlands.LocalGL2.galoisTameParametrization_of_remainingInputs`, `Langlands.LocalGL2.psLFactorIrreducible_of`, `Langlands.LocalGL2.typeRepInjective_holds`, `Langlands.LocalGL2.GL2OddFineInputs`, `Langlands.localLanglandsGL2_odd_of_fineInputs` (the joining step is not yet in the library)

*Proof.* We check the items of Corollary 3.14.44. Item 1 is the same. Corollary 3.15.32 turns item 2 here into item 2 there. Item 3 is the same. Theorem 3.15.26 gives `PSLFactorIrreducible` from the three statements of item 4, so item 4 here gives item 4 there. Theorems 3.15.15 and 3.15.16 are the two statements of item 5 there. Corollary 3.14.44 concludes. $\square$

The fact `ArtinConjCompat` in item 2 is also the first part of `ArtinCompat` in item 1. In the library, `ArtinCompat` for $K$ is the conjunction of `ArtinConjCompat`, `ArtinNormCompat` and `ArtinTransferCompat` for each separable quadratic $L/K$. The structure `GaloisTameRemainingInputs` keeps `ArtinConjCompat` as a separate field, so that the Galois side does not depend on the norm and the transfer.

**Remark 3.15.34 (what is still open for $GL_2$, $p \ne 2$).** This list replaces Remark 3.14.45.
1. `ArtinCompat` ([Ser79], Chapter XI), with its three parts `ArtinConjCompat`, `ArtinNormCompat` and `ArtinTransferCompat`.
2. The three facts `TameInertiaProcyclic`, `OpenIndexTwoQuad` and `WildArtinUnits` of `GaloisTameRemainingInputs`. Its fourth fact, `ArtinConjCompat`, is part of item 1.
3. `Rectifier`, with the characters $\Delta_\xi$ of [BH06], section 34.
4. `SupercuspidalZetaLaurent`, the analytic half of Proposition 2.5.6.
5. The three statements `PSZetaCoeffSpan`, `PSZetaRealize` and `PSZetaGenerates` of Definition 3.15.25, which replace `PSLFactorIrreducible`, and the fact `PSLFactorSteinberg` of Definition 3.11.31.
6. `UncoveredParametrization`, input 5 of Definition 3.10.27.
7. The structure that joins the results of Sections 3.11 to 3.15 into `GL2OddFineInputs`.
8. The case $p = 2$, the $\varepsilon$-factors, and the uniqueness of Theorem 3.3.1.

Compared with Remark 3.14.45, item 2 has lost `WildInertiaProP`, by Theorem 3.15.30. Item 6 has lost the two statements `TypeNormalizerRamifiedField` and `TypeNormalizerSameBasisIso`, by Theorems 3.15.15 and 3.15.16, so `TypeRepInjective` is proved. In item 5, `PSLFactorIrreducible` is now reduced to three statements that compare two kinds of integral: the computation of the integrals $I(\Phi, f, s)$ themselves is done in Theorem 3.15.23. What is missing there is the explicit duality of the principal series and Fubini's theorem over $GL_2(\mathcal{O}_K)$, as in Remark 3.15.27. The fact `PSLFactorSteinberg` needs in addition the Steinberg subspace and its matrix coefficients. Theorem 3.15.23 applies to each function of the principal series, and so to the functions in the Steinberg subspace, but it only gives the bound $L(s, \chi_1) L(s, \chi_2)$ and not the smaller factor $L(s, \chi_1)$. Exercises 53 to 57 work through the main lemmas of this section.
