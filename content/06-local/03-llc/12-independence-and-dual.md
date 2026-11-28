---
title: Independence of the type and the dual of the principal series
nodes: []
sources: [BH06, JL70]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Independence of the type and the dual of the principal series

Remark 3.12.36 lists what is still open for $GL_2$ with $p \ne 2$. This section removes four statements from that list. The first is input 3 of Definition 3.10.27, `TypeRepIndependent`: the representation $\pi_D$ of a tame datum depends only on the isomorphism class of the pair, and not on the choices of $\psi$, $\alpha$, the basis or the factorization $\xi = \xi_0 \chi_L$. The other three are facts 1, 2 and 3 of Definition 3.11.31: a supercuspidal representation has zero Jacquet module (`PSSupercuspidalJacquet`), the contragredient of $\chi_1 \times \chi_2$ is $\chi_1^{-1} \times \chi_2^{-1}$ (`PSContragredientIso`), and a smooth linear form on a subrepresentation extends to the whole representation (`SmoothDualExtends`). We prove all four in full. The Lean files are `Langlands/Local/TypeIndependent.lean`, `Langlands/Local/TypeCharAgree.lean`, `Langlands/Local/PSInputPropsProof.lean` and `Langlands/Local/PSContragredient.lean`.

The two halves of the section use different tools. The independence of the type is a statement on open compact subgroups of $GL_2(K)$. Its proof has two parts. A formal part moves any two data for isomorphic pairs to data with the same field, the same chain order and the same basis. A group theoretic part, the descent of Theorem 3.13.19, then shows that the two characters agree. The descent uses only three properties of the quotient of the two characters, and it does not compare the two elements $\alpha$, the two characters $\psi$ or the two characters $\chi$. The principal series half uses integration over compact groups. The main new object is the integral $\mathcal{I}(\varphi) = \int_{GL_2(\mathcal{O}_K)} \varphi(k) \, dk$ on the functions with $\varphi(bg) = |a/d| \varphi(g)$, and the main computation is the proof that $\mathcal{I}$ is invariant under right translation. We prove it with the $q + 1$ cosets of the Iwahori subgroup and the element $\eta = \left(\begin{smallmatrix} 0 & 1 \\ \varpi & 0 \end{smallmatrix}\right)$ that normalizes it.

We keep the notation of Sections 3.9 to 3.12. The field $K$ is a nonarchimedean local field with residue field $k$ of $q$ elements and characteristic $p$, uniformizer $\varpi$ and $|\varpi| = q^{-1}$. We write $G = GL_2(K)$, $K_0 = GL_2(\mathcal{O}_K)$, $B$ for the upper triangular Borel subgroup, $T$ for the diagonal torus, $Z$ for the centre, $n(x) = \left(\begin{smallmatrix} 1 & x \\ 0 & 1 \end{smallmatrix}\right)$ and $\bar n(y) = \left(\begin{smallmatrix} 1 & 0 \\ y & 1 \end{smallmatrix}\right)$. For a basis $v$ of a quadratic extension $L/K$, $\iota_v : L^\times \to G$ sends $y$ to the matrix of multiplication by $y$ in the basis $v$. This is `embGL v` in the library. The chain orders are $\mathfrak{M}$ and $\mathfrak{J}$ of Definition 3.9.1, with the filtrations $\mathfrak{P}^n_{\mathfrak{A}}$ and $U^n_{\mathfrak{A}}$ and the normalizer $\mathfrak{K}_{\mathfrak{A}}$.

### Conjugation and transport

A tame datum $D = (\psi, \mathfrak{A}, v, \xi_0, \alpha, \Lambda_0, \chi)$ for $(L/K, \xi)$, as in Definition 3.10.22, has many choices in it. Two of them are formal: the field $L$ inside $\bar K$ up to $K$-isomorphism, and the basis $v$. We first remove these two. The tool is the conjugation of a compact induction.

**Lemma 3.13.1 (conjugation of compact induction).** Let $H$ be a topological group, $J$ an open subgroup, $\Lambda$ a character of $J$ with open kernel, and $g \in H$. Put $J' = g J g^{-1}$ and $\Lambda^g(x) = \Lambda(g^{-1} x g)$ for $x \in J'$. Then $f \mapsto (x \mapsto f(g^{-1} x))$ is an isomorphism of representations
$$\mathrm{c\text{-}Ind}_J^H \Lambda \cong \mathrm{c\text{-}Ind}_{J'}^H \Lambda^g.$$
In particular, if $J = J'$ as subgroups and $\Lambda = \Lambda'$ as functions on this subgroup, the two compact inductions are isomorphic.

Lean: `Langlands.LocalGL2.cIndConjMap`, `Langlands.LocalGL2.cInd.toFun_cIndConjMap`, `Langlands.LocalGL2.cInd_conj_iso`, `Langlands.LocalGL2.cInd_congr_iso`

*Proof.* Put $(\Phi f)(x) = f(g^{-1} x)$. For $j' = g j g^{-1} \in J'$, $(\Phi f)(j' x) = f(j g^{-1} x) = \Lambda(j) f(g^{-1} x) = \Lambda^g(j') (\Phi f)(x)$. If $f$ is invariant on the right under an open subgroup $U$, so is $\Phi f$. If the support of $f$ is $\bigcup_i J x_i$, then the support of $\Phi f$ is $\bigcup_i g J x_i = \bigcup_i J' g x_i$, a finite union of cosets of $J'$. So $\Phi f \in \mathrm{c\text{-}Ind}_{J'}^H \Lambda^g$. The map $\Phi$ commutes with right translation, since it acts by left translation. The same construction with $g^{-1}$ gives the inverse map. The last claim is the case $g = 1$. In the library the hypothesis is stated as $x \in J'$ if and only if $g^{-1} x g \in J$, so that $J'$ need not be the subgroup $g J g^{-1}$ by definition. $\square$

Now let $j : L \to L'$ be an isomorphism of $K$-algebras. A basis $v$ of $L'$ gives the basis $j^{-1} v$ of $L$, and a character $\xi'$ of $L'^\times$ gives the character $\xi' \circ j$ of $L^\times$.

**Lemma 3.13.2 (field isomorphisms preserve the pieces).** Let $j : L \to L'$ be a $K$-isomorphism, $v$ a basis of $L'$, and $x \in L$.
1. The matrix of multiplication by $x$ in the basis $j^{-1} v$ is the matrix of multiplication by $j(x)$ in the basis $v$. So $\iota_{j^{-1} v}(y) = \iota_v(j(y))$ for $y \in L^\times$.
2. If $v$ is adapted to $\mathfrak{A}$, then $j^{-1} v$ is adapted to $\mathfrak{A}$.
3. If $\xi'$ is admissible, then $\xi' \circ j$ has the same level. If $\xi'$ is minimal, then so is $\xi' \circ j$.
4. If $\alpha \in L'$ is minimal of level $n$, then so is $j^{-1}(\alpha)$.
5. For a character $\chi$ of $K^\times$, $(\xi' \chi_{L'}) \circ j = (\xi' \circ j) \chi_L$.

Lean: `Langlands.LocalGL2.leftMulMatrix_basis_map`, `Langlands.LocalGL2.embGL_basis_map`, `Langlands.LocalGL2.IsAdapted.basis_map`, `Langlands.LocalGL2.unitFilt_le_ker_comp_iff`, `Langlands.LocalGL2.level_comp_unitsMap`, `Langlands.LocalGL2.IsMinimal.comp_unitsMap`, `Langlands.LocalGL2.IsMinimalElt.algEquiv_symm`, `Langlands.LocalGL2.twistChar_comp_unitsMap`

*Proof.* Part 1. Write $w = j^{-1} v$. If $j(x) v_k = \sum_i a_{ik} v_i$, then applying $j^{-1}$ gives $x w_k = \sum_i a_{ik} w_i$. Part 2. The map $j$ preserves the valuation, since the valuation of a finite extension is unique. So $v_L(w_i) = v_{L'}(v_i)$, the ramification indices agree, and orthogonality transfers. Part 3. The map $j$ sends $U^n_L$ onto $U^n_{L'}$, so $\xi' \circ j$ is trivial on $U^n_L$ exactly when $\xi'$ is trivial on $U^n_{L'}$. Also $N_{L'/K} \circ j = N_{L/K}$, so a restriction to $U^n$ factors through the norm for one character exactly when it does for the other. Part 4. The conditions of Definition 3.9.9 are on valuations and on membership in $K + \mathfrak{p}^{1-n}$, and $j^{-1}$ preserves both. Part 5 follows from $N_{L'/K} \circ j = N_{L/K}$. $\square$

**Proposition 3.13.3 (the transported datum).** Let $j : L \to L'$ be a $K$-isomorphism and $D = (\psi, \mathfrak{A}, v, \xi_0, \alpha, \Lambda_0, \chi)$ a tame datum for $(L'/K, \xi')$. Then
$$D^j = (\psi, \mathfrak{A}, j^{-1} v, \xi_0 \circ j, j^{-1}(\alpha), \Lambda_0, \chi)$$
is a tame datum for $(L/K, \xi' \circ j)$. Its group $J$ and its character $\Lambda$ are those of $D$, and $\pi_D \cong \pi_{D^j}$. If $\xi = \xi' \circ j$, then $D^j$ is a datum for $(L/K, \xi)$.

Lean: `Langlands.LocalGL2.TameDatum.transport`, `Langlands.LocalGL2.TameDatum.transport_jGroup_le`, `Langlands.LocalGL2.TameDatum.transport_rep_iso`, `Langlands.LocalGL2.TameDatum.congrChar`, `Langlands.LocalGL2.TameDatum.congrChar_rep`

*Proof.* By Lemma 3.13.2, parts 2 to 5, the pieces of $D^j$ satisfy conditions 2, 3, 4 and 6 of Definition 3.10.22, and the level is still $n$. By part 1, the matrix of $j^{-1}(\alpha)$ in the basis $j^{-1} v$ is the matrix of $\alpha$ in the basis $v$, so it lies in $\mathfrak{P}^{-n}_{\mathfrak{A}}$ and the character $\psi_{j^{-1}(\alpha)}$ on $U^m_{\mathfrak{A}}$ is $\psi_\alpha$. Also $\iota_{j^{-1} v}(L^\times) = \iota_v(L'^\times)$. So the group $J = \iota(L^\times) U^m_{\mathfrak{A}}$ is the same subgroup of $G$ for both data. On it, $\Lambda_0$ is a cuspidal type for $(j^{-1}(\alpha), \xi_0 \circ j)$: on $\iota_{j^{-1} v}(y) = \iota_v(j(y))$ it takes the value $\xi_0(j(y))$, and on $U^m_{\mathfrak{A}}$ it is $\psi_\alpha$. The two characters $\Lambda$ are then equal functions on one group, and Lemma 3.13.1 with $g = 1$ gives $\pi_D \cong \pi_{D^j}$. The last claim only replaces the character by an equal one. $\square$

### Change of basis

The second formal choice is the basis. Let $v$ and $v'$ be two bases of $L$ over $K$, and let $g \in GL_2(K)$ be the change of basis matrix, whose columns are the coordinates of the vectors $v'_k$ in the basis $v$. This is `basisChangeGL v v'`.

**Lemma 3.13.4 (change of basis).** Let $v$ and $v'$ be bases of $L$ and $g$ the change of basis from $v$ to $v'$.
1. For $x \in L$, the matrix of $x$ in the basis $v'$ is $g^{-1} M_v(x) g$. So $\iota_{v'}(y) = g^{-1} \iota_v(y) g$ for $y \in L^\times$.
2. For $X \in M_2(K)$, $\mathrm{tr}(g^{-1} X g) = \mathrm{tr}(X)$.
3. Assume that $v$ and $v'$ are both adapted to $\mathfrak{A}$. Then for each $n$, $Y \in \mathfrak{P}^n_{\mathfrak{A}}$ if and only if $g Y g^{-1} \in \mathfrak{P}^n_{\mathfrak{A}}$, and $u \in U^n_{\mathfrak{A}}$ if and only if $g u g^{-1} \in U^n_{\mathfrak{A}}$.
4. In the situation of part 3, let $J_v = \iota_v(L^\times) U^m_{\mathfrak{A}}$ and $J_{v'} = \iota_{v'}(L^\times) U^m_{\mathfrak{A}}$. Then $x \in J_v$ if and only if $g^{-1} x g \in J_{v'}$.

Lean: `Langlands.LocalGL2.basisChangeGL`, `Langlands.LocalGL2.val_basisChangeGL`, `Langlands.LocalGL2.leftMulMatrix_basisChange`, `Langlands.LocalGL2.embGL_basisChange`, `Langlands.LocalGL2.act_basisChange`, `Langlands.LocalGL2.trace_basisChange`, `Langlands.LocalGL2.mem_radPow_basisChange_iff`, `Langlands.LocalGL2.mem_unitsFilt_basisChange_iff`, `Langlands.LocalGL2.mem_jGroup_basisChange_iff`, `Langlands.LocalGL2.jGroupBasisChange`

*Proof.* Part 1 is the usual change of basis formula for the matrix of a linear map. Part 2 is $\mathrm{tr}(AB) = \mathrm{tr}(BA)$. Part 3. A matrix $Y$ acts on $L$ through a basis: identify $L$ with $K^2$ by the coordinates and apply $Y$. Write $Y_v$ for this endomorphism of $L$. By Proposition 3.9.7, part 1, for an adapted basis $v$, $Y \in \mathfrak{P}^n_{\mathfrak{A}}$ if and only if $Y_v \mathfrak{p}_L^N \subseteq \mathfrak{p}_L^{N+n}$ for all $N$. This condition is on the endomorphism $Y_v$ of $L$ alone. Now $Y_{v'} = (g Y g^{-1})_v$, because $g$ converts coordinates in $v'$ into coordinates in $v$. So $Y \in \mathfrak{P}^n_{\mathfrak{A}}$, which is a condition on $Y_{v'}$, is equivalent to $g Y g^{-1} \in \mathfrak{P}^n_{\mathfrak{A}}$, which is the same condition on $(g Y g^{-1})_v$. For the units, $u \in U^n_{\mathfrak{A}}$ means that $u$ and $u^{-1}$ lie in $\mathfrak{A} = \mathfrak{P}^0_{\mathfrak{A}}$ and $u - 1 \in \mathfrak{P}^n_{\mathfrak{A}}$, and the conjugation by $g$ commutes with inverses and with subtracting $1$. Part 4. By part 1, $\iota_v(y)^{-1} x \in U^m_{\mathfrak{A}}$ if and only if $g^{-1}(\iota_v(y)^{-1} x) g = \iota_{v'}(y)^{-1} (g^{-1} x g)$ lies in $g^{-1} U^m_{\mathfrak{A}} g = U^m_{\mathfrak{A}}$, by part 3. $\square$

Part 3 says that $g$ normalizes $\mathfrak{A}$, so $g \in \mathfrak{K}_{\mathfrak{A}}$. The change of basis between two adapted bases is not arbitrary, but we do not need its form.

**Proposition 3.13.5 (the rebased datum).** Let $D$ be a tame datum for $(L/K, \xi)$ with basis $v'$, and let $v$ be a second basis adapted to the chain order of $D$. Let $g$ be the change of basis from $v$ to $v'$. Keep $\psi$, $\mathfrak{A}$, $\xi_0$, $\alpha$ and $\chi$, replace $v'$ by $v$, and replace $\Lambda_0$ by $x \mapsto \Lambda_0(g^{-1} x g)$ on $J_v$. This is a tame datum $D_v$ for $(L/K, \xi)$, and $\pi_D \cong \pi_{D_v}$.

Lean: `Langlands.LocalGL2.TameDatum.rebase`, `Langlands.LocalGL2.TameDatum.rebase_rep_iso`

*Proof.* By Lemma 3.13.4, part 4, conjugation by $g$ maps $J_v$ onto $J_{v'}$, so the new $\Lambda_0$ is a character of $J_v$ with open kernel. It is a cuspidal type for $(\alpha, \xi_0)$ in the basis $v$. On $\iota_v(y)$ it takes the value $\Lambda_0(\iota_{v'}(y)) = \xi_0(y)$, by Lemma 3.13.4, part 1. For $u \in U^m_{\mathfrak{A}}$ it takes the value
$$\psi(\mathrm{tr}(M_{v'}(\alpha)(g^{-1} u g - 1))) = \psi(\mathrm{tr}(g^{-1} M_v(\alpha) g \, g^{-1}(u - 1) g)) = \psi(\mathrm{tr}(M_v(\alpha)(u - 1))),$$
which is $\psi_\alpha(u)$ in the basis $v$, by parts 1 and 2. The matrix of $\alpha$ in the basis $v$ lies in $\mathfrak{P}^{-n}_{\mathfrak{A}}$ by part 3. The determinant does not change under conjugation, so the new $\Lambda$ is $x \mapsto \Lambda(g^{-1} x g)$. Lemma 3.13.1 with the element $g$ and $J' = J_v = g J_{v'} g^{-1}$ gives $\pi_D \cong \pi_{D_v}$. $\square$

### Two data for one pair

We now compare two data $D$ and $D'$ for the same pair $(L/K, \xi)$. Write $\Lambda$, $\Lambda'$ for their characters, $n$, $n'$ for their levels and $\mathfrak{A}$, $\mathfrak{A}'$ for their chain orders.

**Lemma 3.13.6 (chain order and level).** Let $D$ and $D'$ be tame data for $(L/K, \xi)$.
1. $\mathfrak{A} = \mathfrak{A}'$. It is $\mathfrak{M}$ if $L/K$ is unramified and $\mathfrak{J}$ if $L/K$ is ramified.
2. Let $\xi_0$ be admissible and $\xi_0'$ minimal, with $\xi_0 \chi_L = \xi_0' \chi'_L$ for characters $\chi, \chi'$ of $K^\times$. Then $\ell(\xi_0') \le \ell(\xi_0)$.
3. $n = n'$.

Lean: `Langlands.LocalGL2.ChainOrder.eq_of_e_eq`, `Langlands.LocalGL2.TameDatum.A_eq`, `Langlands.LocalGL2.level_le_of_twistChar_eq`, `Langlands.LocalGL2.TameDatum.level_eq`

*Proof.* Part 1. An adapted basis requires $e(L|K) = e_{\mathfrak{A}}$, by Definition 3.9.6, so both chain orders have period $e(L|K)$. There are two chain orders, with periods 1 and 2. Part 2. Write $\ell = \ell(\xi_0)$ and $\ell' = \ell(\xi_0')$, and suppose that $\ell' > \ell$. Then $\xi_0$ is trivial on $U^{\ell + 1}_L \supseteq U^{\ell'}_L$. On $U^{\ell'}_L$ the identity $\xi_0' = \xi_0 (\chi \chi'^{-1})_L$ gives $\xi_0' = (\chi \chi'^{-1}) \circ N_{L/K}$. So the restriction of $\xi_0'$ to $U^{\ell'}_L$ factors through the norm, and $\xi_0'$ is not minimal, by Definition 3.3.12. This is a contradiction. Part 3. Both $\xi_0$ and $\xi_0'$ are minimal, so part 2 applies in both directions. $\square$

Part 2 says that a minimal character has the least level in its class under twists by characters $\chi_L$. With part 1 and Proposition 3.13.5, we may give $D$ and $D'$ the same basis. Then the groups agree: $J = \iota_v(L^\times) U^m_{\mathfrak{A}}$ with $m = (n + 1)/2$ is the same for both. The characters agree on half of $J$ for a simple reason.

**Lemma 3.13.7 (the character on $L^\times$).** Let $D$ be a tame datum for $(L/K, \xi)$ with basis $v$. Then $\Lambda(\iota_v(y)) = \xi(y)$ for each $y \in L^\times$.

Lean: `Langlands.LocalGL2.TameDatum.Λ_embGL`

*Proof.* The determinant of the matrix of multiplication by $y$ is $N_{L/K}(y)$. So $\Lambda(\iota_v(y)) = \Lambda_0(\iota_v(y)) \chi(\det \iota_v(y)) = \xi_0(y) \chi(N_{L/K}(y)) = \xi_0(y) \chi_L(y) = \xi(y)$. $\square$

**Proposition 3.13.8 (data with the same basis).** Let $D$ and $D'$ be tame data for $(L/K, \xi)$ with the same chain order $\mathfrak{A}$ and the same basis $v$. If $\Lambda$ and $\Lambda'$ agree on $U^m_{\mathfrak{A}}$, then $\Lambda = \Lambda'$ and $\pi_D \cong \pi_{D'}$.

Lean: `Langlands.LocalGL2.TameDatum.rep_iso_of_eq_basis`

*Proof.* By Lemma 3.13.6, part 3, the two data have the same $m$, so they have the same group $J$. Each $x \in J$ is $\iota_v(y) u$ with $y \in L^\times$ and $u \in U^m_{\mathfrak{A}}$. By Lemma 3.13.7 and the hypothesis, $\Lambda'(x) = \xi(y) \Lambda'(u) = \xi(y) \Lambda(u) = \Lambda(x)$. Lemma 3.13.1 with $g = 1$ concludes. $\square$

This isolates the one statement that is not formal.

**Definition 3.13.9 (agreement on the units).** The statement `TypeCharUnitsAgree` for $K$ says: if $p \ne 2$, $(L/K, \xi)$ is a pair, and $D$, $D'$ are tame data for it with the same chain order $\mathfrak{A}$ and the same basis, then $\Lambda$ and $\Lambda'$ agree on $U^m_{\mathfrak{A}}$.

Lean: `Langlands.LocalGL2.TypeCharUnitsAgree`

On $U^m_{\mathfrak{A}}$ we have $\Lambda(u) = \psi(\mathrm{tr}(\alpha(u - 1))) \chi(\det u)$, so the statement compares $\psi_\alpha \cdot (\chi \circ \det)$ with $\psi'_{\alpha'} \cdot (\chi' \circ \det)$. Here the matrix of $\alpha$ in the basis $v$ is written $\alpha$.

**Proposition 3.13.10 (reduction to the units).** Assume `TypeCharUnitsAgree` for $K$. Then `TypeRepIndependent` holds for $K$: if $P = (L/K, \xi)$ and $Q = (L'/K, \xi')$ are isomorphic pairs with data $D$ and $D'$, then $\pi_D \cong \pi_{D'}$.

Lean: `Langlands.LocalGL2.rep_iso_of_typeCharUnitsAgree`, `Langlands.LocalGL2.typeRepIndependent_of_typeCharUnitsAgree`

*Proof.* An isomorphism $P \cong Q$ is a $K$-isomorphism $j : L \to L'$ with $\xi = \xi' \circ j$. By Proposition 3.13.3, $D'^j$ is a datum for $(L/K, \xi)$ with $\pi_{D'} \cong \pi_{D'^j}$. By Lemma 3.13.6, part 1, $D$ and $D'^j$ have the same chain order, so the basis $v$ of $D$ is adapted to the chain order of $D'^j$. By Proposition 3.13.5, the rebased datum $(D'^j)_v$ has basis $v$ and $\pi_{D'^j} \cong \pi_{(D'^j)_v}$. Now $D$ and $(D'^j)_v$ are data for one pair with the same chain order and basis, so `TypeCharUnitsAgree` and Proposition 3.13.8 give $\pi_D \cong \pi_{(D'^j)_v}$. Compose the three isomorphisms. $\square$

Before the general proof we treat the case of equal $\psi$ and $\chi$, where a direct computation works. It needs the duality of the trace form.

**Lemma 3.13.11 (trace duality).** Let $p \ne 2$, let $L/K$ be separable quadratic, and let $\psi$ be a character of $K$ of level one. If $\delta \in L$ and $\psi(\mathrm{tr}_{L/K}(\delta y)) = 1$ for all $y \in \mathfrak{p}_L^k$, then $\delta \in \mathfrak{p}_L^{1-k}$.

Lean: `Langlands.LocalGL2.mem_ordBall_of_forall_psi_trace`

*Proof.* The set $\mathrm{tr}_{L/K}(\delta \mathfrak{p}_L^k)$ is an $\mathcal{O}_K$-submodule of $K$ on which $\psi$ is trivial. A nonzero submodule of this kind is a fractional ideal $\mathfrak{p}_K^a$. Since $\psi$ is not trivial on $\mathcal{O}_K$, we get $a \ge 1$, so $\mathrm{tr}_{L/K}(\delta \mathfrak{p}_L^k) \subseteq \mathfrak{p}_K$. Since $p \ne 2$, $L/K$ is tamely ramified, and the different of $L/K$ is $\mathfrak{p}_L^{e - 1}$ with $e = e(L|K)$. So $\mathrm{tr}_{L/K}(\mathfrak{p}_L^j) \subseteq \mathfrak{p}_K$ holds exactly when $\mathfrak{p}_L^j \subseteq \mathfrak{p}_K \mathfrak{p}_L^{1-e} = \mathfrak{p}_L^1$, that is when $j \ge 1$. With $\delta \mathfrak{p}_L^k = \mathfrak{p}_L^{v_L(\delta) + k}$ this gives $v_L(\delta) + k \ge 1$. $\square$

**Proposition 3.13.12 (data with the same $\psi$ and $\chi$).** Let $p \ne 2$. Let $D$ and $D'$ be tame data for $(L/K, \xi)$ with the same $\psi$ and the same $\chi$. Then $\pi_D \cong \pi_{D'}$.

Lean: `Langlands.LocalGL2.TameDatum.Λ_unitsFilt_eq`, `Langlands.LocalGL2.TameDatum.rep_iso_of_ψ_eq_of_χ_eq`

*Proof.* Rebase $D'$ to the basis of $D$ by Proposition 3.13.5. This changes neither $\psi$, $\chi$, $\xi_0'$ nor $\alpha'$. By Proposition 3.13.8 it is enough to show that $\Lambda = \Lambda'$ on $U^m_{\mathfrak{A}}$. From $\xi_0 \chi_L = \xi = \xi_0' \chi_L$ we get $\xi_0 = \xi_0'$. Both $\alpha$ and $\alpha'$ are compatible with $\xi_0$, so for $y \in \mathfrak{p}_L^m$,
$$\psi(\mathrm{tr}_{L/K}(\alpha y)) = \xi_0(1 + y) = \psi(\mathrm{tr}_{L/K}(\alpha' y)).$$
So $\psi(\mathrm{tr}_{L/K}((\alpha' - \alpha) y)) = 1$ on $\mathfrak{p}_L^m$, and Lemma 3.13.11 gives $\alpha' - \alpha \in \mathfrak{p}_L^{1-m}$. By Proposition 3.9.7, part 1, the matrix of $\alpha' - \alpha$ lies in $\mathfrak{P}^{1-m}_{\mathfrak{A}}$. For $u \in U^m_{\mathfrak{A}}$ the product $(\alpha' - \alpha)(u - 1)$ lies in $\mathfrak{P}^{1}_{\mathfrak{A}}$, and the trace of an element of $\mathfrak{P}^1_{\mathfrak{A}}$ lies in $\mathfrak{p}_K$. So
$$\frac{\Lambda'(u)}{\Lambda(u)} = \frac{\psi(\mathrm{tr}(\alpha'(u - 1)))}{\psi(\mathrm{tr}(\alpha(u - 1)))} = \psi(\mathrm{tr}((\alpha' - \alpha)(u - 1))) = 1,$$
since $\psi$ has level one and the factors $\chi(\det u)$ cancel. $\square$

The proof uses $m = [n/2] + 1$ for the compatibility, which is Definition 3.9.12, and $m = [(n+1)/2]$ for the group $J$. These agree because $n$ is odd.

**Example 3.13.13 (changing $\psi$ by a unit).** Let $D$ be a datum, let $c \in \mathcal{O}_K^\times$, and put $\psi'(x) = \psi(c x)$. Then $\psi'$ has level one, and $\alpha' = c^{-1} \alpha$ is minimal of level $n$ and compatible with $\xi_0$ for $\psi'$, since $\psi'(\mathrm{tr}(\alpha' y)) = \psi(\mathrm{tr}(\alpha y))$. The data $D$ and $D' = (\psi', \mathfrak{A}, v, \xi_0, c^{-1}\alpha, \Lambda_0, \chi)$ have $\psi'_{\alpha'} = \psi_\alpha$ on $U^m_{\mathfrak{A}}$, so the same character, and Proposition 3.13.8 applies at once. This is the easy direction. If instead $\chi$ changes to $\chi \phi$, then $\xi_0$ changes to $\xi_0 \phi_L^{-1}$. When $\phi$ has positive level, the element $\alpha$ of $\xi_0 \phi_L^{-1}$ is $\alpha - \beta$ with $\beta \in K$ the element of $\phi \circ N_{L/K}$, and the term $\psi_{-\beta}$ must cancel against $\phi \circ \det$ on $U^m_{\mathfrak{A}}$. Such a cancellation can be checked by hand, but the next subsection avoids it altogether.

### The descent

Let $D$ and $D'$ be data for one pair with the same chain order $\mathfrak{A}$ and the same basis $v$, and let $J = \iota_v(L^\times) U^m_{\mathfrak{A}}$ be their common group. Put $\theta = \Lambda' \Lambda^{-1}$, a character of $J$, and let $H \le G$ be its kernel. We must show $U^m_{\mathfrak{A}} \le H$. We know three things about $H$.
1. $\iota_v(L^\times) \le H$, by Lemma 3.13.7.
2. $H$ contains each commutator $y b y^{-1} b^{-1}$ with $y \in \iota_v(L^\times)$ and $b \in U^m_{\mathfrak{A}}$, because $\theta$ takes values in the commutative group $\mathbb{C}^\times$.
3. $U^N_{\mathfrak{A}} \le H$ for some $N$, by Lemma 3.13.16 below.

The descent shows that these three properties force $U^m_{\mathfrak{A}} \le H$ when $p \ne 2$. It uses one element of $L$ with a central square.

**Lemma 3.13.14 (an element with central square).** Let $L/K$ be a quadratic extension of fields with $2 \ne 0$ in $K$. There is $y \in L \smallsetminus K$ with $y^2 \in K$.

Lean: `Langlands.LocalGL2.exists_not_mem_range_mul_self_mem_range`

*Proof.* Let $z \in L \smallsetminus K$ and let $X^2 + bX + c$ be its minimal polynomial. Put $y = z + b/2$. Then $y \notin K$ and $y^2 = z^2 + bz + b^2/4 = b^2/4 - c \in K$. $\square$

**Lemma 3.13.15 (the centralizer).** Let $y \in L \smallsetminus K$ and let $q \in GL_2(K)$ commute with the matrix $M_v(y)$. Then $q = \iota_v(e)$ for some $e \in L^\times$.

Lean: `Langlands.LocalGL2.exists_embGL_eq_of_commute`

*Proof.* Identify $K^2$ with $L$ by the basis $v$. Then $q$ is a $K$-linear map of $L$ that commutes with multiplication by $y$. Since $L = K[y]$, it commutes with multiplication by each element of $L$, so it is $L$-linear. An $L$-linear map of the one dimensional $L$-space $L$ is multiplication by $e = q(1)$, and $e \ne 0$ since $q$ is invertible. $\square$

**Lemma 3.13.16 (deep units are in the kernel).** Let $D$ be a tame datum with chain order $\mathfrak{A}$, level $n$ and character $\chi$, and let $k \ge 1$ be such that $\chi$ is trivial on $U^k_K$.
1. For $j \ge 0$, $\mathfrak{P}^{2j}_{\mathfrak{A}} \subseteq \varpi^j M_2(\mathcal{O}_K)$. So $\det(U^{2k}_{\mathfrak{A}}) \subseteq U^k_K$.
2. $\Lambda$ is trivial on $U^N_{\mathfrak{A}}$ for $N = \max(n + 1, 2k)$.

Lean: `Langlands.LocalGL2.ChainOrder.le_bd_two_mul`, `Langlands.LocalGL2.det_sub_one_mem_ordBall_of_two_mul`, `Langlands.LocalGL2.det_mem_unitFilt_of_two_mul`, `Langlands.LocalGL2.TameDatum.exists_Λ_eq_one`

*Proof.* Part 1. For $\mathfrak{M}$, $\mathfrak{P}^{2j}_{\mathfrak{M}} = \varpi^{2j} M_2(\mathcal{O}_K)$. For $\mathfrak{J}$, $\mathfrak{P}^2_{\mathfrak{J}} = \Pi^2 \mathfrak{J} = \varpi \mathfrak{J}$, so $\mathfrak{P}^{2j}_{\mathfrak{J}} = \varpi^j \mathfrak{J} \subseteq \varpi^j M_2(\mathcal{O}_K)$. For $u = 1 + X$ with $X \in \varpi^k M_2(\mathcal{O}_K)$, $\det u = 1 + \mathrm{tr}(X) + \det X \in 1 + \mathfrak{p}_K^k$. Part 2. Let $u \in U^N_{\mathfrak{A}}$. Since $N \ge n + 1$, the element $\alpha(u - 1)$ lies in $\mathfrak{P}^{-n}_{\mathfrak{A}} \mathfrak{P}^{n+1}_{\mathfrak{A}} = \mathfrak{P}^1_{\mathfrak{A}}$, its trace lies in $\mathfrak{p}_K$, and $\psi_\alpha(u) = 1$. Since $N \ge 2k$, part 1 gives $\det u \in U^k_K$ and $\chi(\det u) = 1$. So $\Lambda(u) = \psi_\alpha(u) \chi(\det u) = 1$. $\square$

The heart of the matter is one step of the descent, from $U^{2j}_{\mathfrak{A}}$ to $U^j_{\mathfrak{A}}$.

**Proposition 3.13.17 (one step of the descent).** Let $p \ne 2$, let $v$ be adapted to $\mathfrak{A}$, and let $H \le GL_2(K)$ be a subgroup that contains $\iota_v(L^\times)$ and the commutators $y b y^{-1} b^{-1}$ for $y \in \iota_v(L^\times)$ and $b \in U^m_{\mathfrak{A}}$. Let $j \ge 1$ with $j \ge m$. If $U^{2j}_{\mathfrak{A}} \le H$, then $U^j_{\mathfrak{A}} \le H$.

Lean: `Langlands.LocalGL2.unitsFilt_le_of_two_mul_le`

*Proof.* Lemma 3.13.14 gives $y \in L \smallsetminus K$ with $y^2 = c \in K^\times$. Let $g = \iota_v(y)$. Then $g^2 = c$ is a scalar matrix, so $g^{-1} = c^{-1} g$, and $g$ lies in $\mathfrak{K}_{\mathfrak{A}}$ by Proposition 3.9.7, part 1. So conjugation by $g$ preserves each $\mathfrak{P}^i_{\mathfrak{A}}$ and each $U^i_{\mathfrak{A}}$, and $g (g X g^{-1}) g^{-1} = X$ for each matrix $X$. Since $p \ne 2$, $1/2 \in \mathcal{O}_K$. Let $u \in U^j_{\mathfrak{A}}$.

Step 1: the part that commutes with $g$. Put $u' = g u g^{-1} \in U^j_{\mathfrak{A}}$ and $p = (u + u')/2$. Then $p - 1 = ((u - 1) + (u' - 1))/2 \in \mathfrak{P}^j_{\mathfrak{A}}$, and since $j \ge 1$, $p \in U^j_{\mathfrak{A}}$. Also $g p g^{-1} = (u' + u)/2 = p$. By Lemma 3.13.15, $p \in \iota_v(L^\times) \le H$.

Step 2: the part that anticommutes. Put $w = p^{-1} u \in U^j_{\mathfrak{A}}$. Since $p$ commutes with $g$, $g w g^{-1} = p^{-1} u'$, so $w + g w g^{-1} = p^{-1}(u + u') = 2$. Put $V = (w - 1)/2 \in \mathfrak{P}^j_{\mathfrak{A}}$. Then $g V g^{-1} = (g w g^{-1} - 1)/2 = (1 - w)/2 = -V$.

Step 3: the square of $h = 1 + V$. We have $h \in U^j_{\mathfrak{A}} \subseteq U^m_{\mathfrak{A}}$, and $t = g h g^{-1} = 1 - V$. The elements $h$ and $t$ commute, and $h t = 1 - V^2$ commutes with $g$, since $g V^2 g^{-1} = (-V)^2 = V^2$. By Lemma 3.13.15, $h t \in H$. Next,
$$h^2 = (h t)(t^{-1} h) = (h t) \cdot g h^{-1} g^{-1} (h^{-1})^{-1},$$
and the second factor is a commutator $y b y^{-1} b^{-1}$ with $y = g$ and $b = h^{-1} \in U^m_{\mathfrak{A}}$. So $h^2 \in H$.

Step 4: the rest is deep. We have $w = 1 + 2V$ and $h^2 = 1 + 2V + V^2$, so $w = h^2 - V^2$ and $h^{-2} w - 1 = -h^{-2} V^2 \in \mathfrak{A} \mathfrak{P}^{2j}_{\mathfrak{A}} = \mathfrak{P}^{2j}_{\mathfrak{A}}$. So $h^{-2} w \in U^{2j}_{\mathfrak{A}} \le H$. Finally
$$u = p w = p \cdot h^2 \cdot (h^{-2} w),$$
a product of three elements of $H$. $\square$

The proof is the multiplicative form of a linear algebra fact. Conjugation by $g$ is an involution of $M_2(K)$. Its $+1$ eigenspace is the centralizer $L$ of $g$, and its $-1$ eigenspace $L^\perp$ is a complement, since 2 is invertible. Modulo $\mathfrak{P}^{2j}_{\mathfrak{A}}$, the group $U^j_{\mathfrak{A}}$ is the additive group $\mathfrak{P}^j_{\mathfrak{A}}$, and the decomposition $X = X_+ + X_-$ corresponds to $u \equiv p \cdot h^2$. The commutator $g(1 + V)g^{-1}(1 + V)^{-1}$ is congruent to $1 - 2V$, so the commutators fill the $-1$ part. Exercise 43 makes this explicit.

**Corollary 3.13.18 (the descent).** Let $p \ne 2$, let $m \ge 1$, and let $H$ be as in Proposition 3.13.17. If $U^N_{\mathfrak{A}} \le H$ for some $N$, then $U^m_{\mathfrak{A}} \le H$.

Lean: `Langlands.LocalGL2.unitsFilt_le_of_commutator_mem`

*Proof.* Since $2^N m \ge 2^N > N$, $U^{2^N m}_{\mathfrak{A}} \le U^N_{\mathfrak{A}} \le H$. For $i = N, N - 1, \dots, 1$, Proposition 3.13.17 with $j = 2^{i-1} m$, which satisfies $j \ge 1$ and $j \ge m$, takes $U^{2^i m}_{\mathfrak{A}} \le H$ to $U^{2^{i-1} m}_{\mathfrak{A}} \le H$. After $N$ steps, $U^m_{\mathfrak{A}} \le H$. $\square$

**Theorem 3.13.19 (independence of the type).** Let $K$ be a nonarchimedean local field. Then `TypeCharUnitsAgree` and `TypeRepIndependent` hold for $K$. So for $p \ne 2$ the class of $\pi_D$ depends only on the isomorphism class of the pair of $D$, and input 3 of Definition 3.10.27 holds with no hypothesis.

Lean: `Langlands.LocalGL2.typeCharUnitsAgree`, `Langlands.LocalGL2.typeRepIndependent`

This is the form of [BH06], 15.6 and section 19, that the correspondence needs.

*Proof.* Let $D$ and $D'$ be data for one pair with the same $\mathfrak{A}$ and $v$. By Lemma 3.13.6, part 3, they have the same level $n$, hence the same $m = (n + 1)/2 \ge 1$ and the same group $J$. Let $\theta = \Lambda' \Lambda^{-1}$ on $J$ and let $H$ be its kernel, a subgroup of $G$. Property 1 of $H$ is Lemma 3.13.7 for $D$ and $D'$. For property 2, let $y \in \iota_v(L^\times)$ and $b \in U^m_{\mathfrak{A}}$. Both lie in $J$, and $\theta(y b y^{-1} b^{-1}) = \theta(y) \theta(b) \theta(y)^{-1} \theta(b)^{-1} = 1$. For property 3, Lemma 3.13.16 gives $N_1$ and $N_2$ with $\Lambda$ trivial on $U^{N_1}_{\mathfrak{A}}$ and $\Lambda'$ trivial on $U^{N_2}_{\mathfrak{A}}$. Put $N = \max(N_1, N_2, m)$. Then $U^N_{\mathfrak{A}} \subseteq J$ and $\theta$ is trivial on it. Corollary 3.13.18 gives $U^m_{\mathfrak{A}} \le H$, which is `TypeCharUnitsAgree`. Proposition 3.13.10 gives `TypeRepIndependent`. $\square$

The proof does not use the irreducibility of $\pi_D$, the intertwining of the types or any property of $\psi$ beyond Lemma 3.13.16. The hypothesis $p \ne 2$ enters at Lemma 3.13.14 and at the division by 2 in Steps 1 and 2.

**Example 3.13.20 (the descent for an unramified extension).** Let $\varepsilon \in \mathcal{O}_K^\times$ be a unit that is not a square, with $p \ne 2$, and let $L = K(\sqrt{\varepsilon})$, which is unramified. The basis $v = (1, \sqrt{\varepsilon})$ is adapted to $\mathfrak{M}$ by Proposition 3.9.7, part 2. Take $y = \sqrt{\varepsilon}$, so
$$g = \iota_v(\sqrt\varepsilon) = \begin{pmatrix} 0 & \varepsilon \\ 1 & 0 \end{pmatrix}, \qquad g \begin{pmatrix} a & b \\ c & d \end{pmatrix} g^{-1} = \begin{pmatrix} d & \varepsilon c \\ \varepsilon^{-1} b & a \end{pmatrix}.$$
The centralizer of $g$ is $\{\left(\begin{smallmatrix} x & \varepsilon z \\ z & x \end{smallmatrix}\right)\}$, the image of $x + z\sqrt{\varepsilon}$, and the $-1$ eigenspace is $\{\left(\begin{smallmatrix} x & \varepsilon z \\ -z & -x \end{smallmatrix}\right)\}$. Take $j = 1$ and $u = 1 + \varpi E_{11}$, with $E_{11}$ the matrix unit. Then $u' = g u g^{-1} = 1 + \varpi E_{22}$, and $p = 1 + \frac{\varpi}{2} \cdot 1$ is the scalar $1 + \varpi/2$, an element of $U^1_L$. Next $w = p^{-1} u = \mathrm{diag}((1 + \varpi)/(1 + \varpi/2), 1/(1 + \varpi/2))$, and $V = (w - 1)/2 = \mathrm{diag}(\beta, -\beta)$ with $\beta = \varpi/(4 + 2\varpi)$. Indeed $g V g^{-1} = \mathrm{diag}(-\beta, \beta) = -V$. Then $h = \mathrm{diag}(1 + \beta, 1 - \beta)$, $h t = (1 - \beta^2) \cdot 1$ is a scalar, and $h^{-2} w - 1 = -h^{-2} \beta^2$ has valuation at least $2$. So $u$ is a product of the scalar $p$, the element $h^2 = (h t) [g, h^{-1}]$ and an element of $U^2_{\mathfrak{M}}$.

### Extension of smooth linear forms

We now turn to the principal series facts. The first is a general statement about smooth representations of $G$. Recall from Definition 3.11.31 that `SmoothDualExtends` says: for each injective map $f : \sigma \to \pi$ of smooth representations of $G$ and each smooth linear form $\lambda$ on $\sigma$, there is a smooth linear form $\lambda'$ on $\pi$ with $\lambda' \circ f = \lambda$. Remark 3.11.33 sketched a proof with the finite averages $e_U$. The library uses the Haar integral instead, which needs no choice of a subgroup that fixes the vector.

**Lemma 3.13.21 (averaging a linear form).** Let $(\pi, V)$ be a smooth representation of a topological group $H$, let $U$ be a compact subgroup with its Haar measure $du$ of mass 1, and let $L$ be any linear form on $V$.
1. For $v \in V$, the function $u \mapsto L(\pi(u)^{-1} v)$ on $U$ is locally constant, so continuous.
2. The form $\lambda'(v) = \int_U L(\pi(u)^{-1} v) \, du$ is linear and fixed by $U$ under the contragredient action.
3. If $L(\pi(u)^{-1} v) = c$ for all $u \in U$, then $\lambda'(v) = c$.

Lean: `Langlands.LocalGL2.psContinuous_form_inv`, `Langlands.LocalGL2.psAvgForm`, `Langlands.LocalGL2.psAvgForm_ρ`, `Langlands.LocalGL2.psAvgForm_eq_of_forall`

*Proof.* Part 1. The stabilizer $S$ of $v$ is open, and $L(\pi(u s)^{-1} v) = L(\pi(s)^{-1}\pi(u)^{-1} v)$ need not be constant in $s$, so we use the left cosets: $L(\pi(s u)^{-1} v) = L(\pi(u)^{-1} \pi(s)^{-1} v) = L(\pi(u)^{-1} v)$ for $s \in S$, and $(U \cap S) u$ is an open neighbourhood of $u$ in $U$. Part 2. Linearity is clear. For $u_0 \in U$,
$$(\pi^\vee(u_0) \lambda')(v) = \lambda'(\pi(u_0)^{-1} v) = \int_U L(\pi(u_0 u)^{-1} v) \, du = \int_U L(\pi(u)^{-1} v) \, du = \lambda'(v),$$
by the left invariance of $du$. Part 3. The integral of the constant $c$ against a measure of mass 1 is $c$. $\square$

**Theorem 3.13.22 (extension of smooth forms).** `SmoothDualExtends` holds for each $K$.

Lean: `Langlands.LocalGL2.psExists_compact_open_le`, `Langlands.LocalGL2.smoothDualExtends_holds`

This is a standard fact of [BH06], Chapter 1, and it is one way to state that the contragredient functor is exact.

*Proof.* Let $f : \sigma \to \pi$ be injective and $\lambda$ a smooth form on $\sigma$. Its stabilizer is open. It contains a compact open subgroup $U$, for example its intersection with the principal congruence subgroup $1 + \varpi M_2(\mathcal{O}_K)$. Since $f$ is an injective linear map, it has a linear left inverse $r : \pi \to \sigma$ with $r \circ f = \mathrm{id}$. Put $L = \lambda \circ r$ and let $\lambda'$ be the average of $L$ over $U$, as in Lemma 3.13.21. By part 2 of that lemma, $\lambda'$ is fixed by the open subgroup $U$, so it is smooth. For $x \in \sigma$ and $u \in U$,
$$L(\pi(u)^{-1} f(x)) = \lambda(r(f(\sigma(u)^{-1} x))) = \lambda(\sigma(u)^{-1} x) = \lambda(x),$$
since $f$ is a map of representations and $U$ fixes $\lambda$. By part 3, $\lambda'(f(x)) = \lambda(x)$. $\square$

The left inverse $r$ is not a map of representations, and it need not be. The average repairs the lack of equivariance on the side of $\lambda'$, and the equivariance of $f$ is used only to move $\pi(u)^{-1}$ past $f$. The extension $\lambda'$ is not unique (Exercise 46 has a related point).

### Supercuspidal representations have zero Jacquet module

Recall from Theorem 1.4.3 and Remark 1.4.4 the two notions of cuspidality. The library defines $\pi$ to be supercuspidal (`IsSupercuspidal`) if each matrix coefficient $c_{v, \lambda}(g) = \lambda(\pi(g) v)$, with $\lambda$ smooth, has support in $C Z$ for a compact set $C$. It defines $\pi$ to be Jacquet cuspidal (`IsJacquetCuspidal`) if its Jacquet module for $B$ is zero. The direction from Jacquet cuspidal to supercuspidal is `isSupercuspidal_of_isJacquetCuspidal`. Fact 1 of Definition 3.11.31, `PSSupercuspidalJacquet`, is the converse for irreducible admissible representations. We prove it by producing a coefficient whose support is not compact modulo the centre. The obstruction is measured by one function.

**Lemma 3.13.23 (a function that sees the torus).** Let $\kappa(g) = g_{22} (g^{-1})_{11}$ for $g \in G$, where the indices refer to the rows and columns of the matrices.
1. $\kappa$ is continuous, and $\kappa(g z) = \kappa(g)$ for each scalar $z$.
2. $\kappa(\mathrm{diag}(x, 1)) = x^{-1}$.
3. Let $C \subseteq G$ be compact. Then there is $k \ge 0$ with $\mathrm{diag}(\varpi^k, 1) \notin C Z$.

Lean: `Langlands.LocalGL2.psCenterInv`, `Langlands.LocalGL2.psContinuous_centerInv`, `Langlands.LocalGL2.psCenterInv_mul_scalar`, `Langlands.LocalGL2.psCenterInv_diag`, `Langlands.LocalGL2.psNot_forall_diag_mem`

*Proof.* Part 1. The entries of $g$ and $g^{-1}$ are continuous on $G$. For a scalar $z$, $(gz)_{22} = z g_{22}$ and $((gz)^{-1})_{11} = z^{-1} (g^{-1})_{11}$. Part 2 is direct. Part 3. The image $\kappa(C)$ is compact in $K$, so it lies in $\mathfrak{p}_K^{-n}$ for some $n$. If $\mathrm{diag}(\varpi^{n+1}, 1) = c z$ with $c \in C$ and $z \in Z$, then by parts 1 and 2, $\varpi^{-n-1} = \kappa(c) \in \mathfrak{p}_K^{-n}$, which is false. $\square$

Exercise 45 shows that $\kappa(g) = g_{22}^2 / \det g$, which explains part 1.

**Lemma 3.13.24 (the form at the identity).** Let $\alpha_1, \alpha_2$ be smooth characters of $K^\times$ and $\chi(b) = \alpha_1(a) \alpha_2(d)$ for $b = \left(\begin{smallmatrix} a & * \\ 0 & d \end{smallmatrix}\right) \in B$. Let $\Phi : \pi \to \mathrm{Ind}_B^G \chi$ be a map of representations into the unnormalized induction, and put $\mu(v) = \Phi(v)(1)$. Then $\mu$ is linear, $\mu(\pi(g) v) = \Phi(v)(g)$, and $\mu(\pi(b) v) = \chi(b) \mu(v)$ for $b \in B$.

Lean: `Langlands.LocalGL2.psEvalOne`, `Langlands.LocalGL2.psEvalOne_ρ`, `Langlands.LocalGL2.psEvalOne_borel`

*Proof.* $\Phi(\pi(g) v)(1) = (\rho(g) \Phi(v))(1) = \Phi(v)(g)$, and $\Phi(v)(b) = \chi(b) \Phi(v)(1)$ by the transformation law of the induced space. $\square$

**Theorem 3.13.25 (supercuspidal implies Jacquet cuspidal).** Let $\pi$ be an irreducible admissible representation of $G$ that is supercuspidal. Then $\pi$ is Jacquet cuspidal. So `PSSupercuspidalJacquet` holds for each $K$.

Lean: `Langlands.LocalGL2.psSupercuspidalJacquet_holds`

The statement is half of Theorem 1.4.3, see [BH06], Chapter 2, section 10, and [JL70], section 2. The proof below is short because it uses the embedding of Corollary 1.5.9.

*Proof.* Suppose that the Jacquet module of $\pi$ is not zero. By Corollary 1.5.9 (`exists_injective_principalSeriesInd_of_isAdmissible`) there are smooth characters $\alpha_1, \alpha_2$ and an injective map $\Phi : \pi \to \mathrm{Ind}_B^G \chi$, with $\chi$ as in Lemma 3.13.24. Since $\pi \ne 0$, there are $v_0$ and $x$ with $\Phi(v_0)(x) \ne 0$, and then $v = \pi(x) v_0$ has $\mu(v) \ne 0$.

Choose a level. The character $\chi$ is smooth, so it is trivial on $B \cap K_{r_0}$ for some $r_0 \ge 1$, where $K_r = 1 + \varpi^r M_2(\mathcal{O}_K)$ (`exists_congruence_borelChar`). The map $y \mapsto \bar n(y)$ is continuous and the stabilizer of $v$ is open, so there is $r_1$ with $\pi(\bar n(y)) v = v$ for $y \in \mathfrak{p}^{r_1}$. Let $r = \max(r_0, r_1)$ and $U = K_r$, a compact open subgroup. Let $\lambda$ be the average of $\mu$ over $U$, as in Lemma 3.13.21. It is fixed by $U$, so it is smooth.

Compute the coefficient at $t_k = \mathrm{diag}(\varpi^k, 1)$ for $k \ge 0$. Let $u \in U$. By Lemma 1.5.7, $u^{-1} = n(x) s \bar n(y)$ with $s \in T \cap U$, $x \in \mathfrak{p}^r$ and $y \in \mathfrak{p}^r$. Then
$$u^{-1} t_k = n(x) s \, t_k \, (t_k^{-1} \bar n(y) t_k) = (n(x) s) \, t_k \, \bar n(\varpi^k y).$$
Here $n(x) s \in B \cap U$, so $\chi(n(x) s) = 1$, and $\varpi^k y \in \mathfrak{p}^{r_1}$, so $\bar n(\varpi^k y)$ fixes $v$. By Lemma 3.13.24,
$$\mu(\pi(u)^{-1} \pi(t_k) v) = \mu(\pi(n(x) s)\pi(t_k) v) = \chi(t_k) \mu(v) = \alpha_1(\varpi)^k \mu(v).$$
This does not depend on $u$, so Lemma 3.13.21, part 3, gives $\lambda(\pi(t_k) v) = \alpha_1(\varpi)^k \mu(v) \ne 0$.

Now use that $\pi$ is supercuspidal. There is a compact set $C$ such that $\lambda(\pi(g) v) \ne 0$ implies $g \in C Z$. So $t_k \in C Z$ for all $k \ge 0$, which contradicts Lemma 3.13.23, part 3. $\square$

The proof uses $k \ge 0$ in one place: $t_k^{-1} \bar n(y) t_k = \bar n(\varpi^k y)$ shrinks $y$ only for $k \ge 0$. For $k < 0$ the conjugate leaves the stabilizer of $v$. The same contraction is the engine of Jacquet's lemma, Theorem 1.5.8.

**Corollary 3.13.26 (two inputs on the principal series).** `PSSubNotSupercuspidal` holds for each $K$, and `PSSubContragredient` follows from `PSContragredientIso` alone.

Lean: `Langlands.LocalGL2.psSubNotSupercuspidal_holds`, `Langlands.LocalGL2.psSubContragredient_of_contragredientIso`

*Proof.* Theorem 3.11.32, parts 1 and 2, with Theorems 3.13.25 and 3.13.22. $\square$

### Perfect pairings and the contragredient

The last fact, `PSContragredientIso`, says that $(\chi_1 \times \chi_2)^\vee \cong \chi_1^{-1} \times \chi_2^{-1}$ for the normalized principal series `principalSeries`, whose vectors satisfy $f(bg) = \chi_1(a) \chi_2(d) |a/d|^{1/2} f(g)$. The strategy is that of Remark 3.11.33: pair the two representations by integration over $K_0$. We first prove that a perfect pairing of admissible representations gives the contragredient. Let $H$ be a topological group in which each open subgroup contains a compact open subgroup, and let $\mathrm{Haar}_U$ denote the Haar measure of mass 1 on a compact group $U$.

**Lemma 3.13.27 (fixed averages).** Let $(\pi, V)$ be a smooth representation of $H$, $U$ a compact open subgroup and $v \in V$. There is $w \in V^U$ with $D(w) = D(v)$ for each linear form $D$ that satisfies $D(\pi(u) x) = D(x)$ for all $u \in U$ and $x \in V$.

Lean: `Langlands.LocalGL2.pcHaar`, `Langlands.LocalGL2.pcHaar_unique`, `Langlands.LocalGL2.integral_pcHaar_mul_right`, `Langlands.LocalGL2.integral_pcHaar_mul_left`, `Langlands.LocalGL2.pcExists_fixed_avg`

*Proof.* The stabilizer $S$ of $v$ in $U$ is open, so it has finite index in $U$. Let $w = [U : S]^{-1} \sum_{u \in U/S} \pi(u) v$. This does not depend on the representatives, and it is fixed by $U$, since $U$ permutes the cosets. For an invariant $D$, $D(w) = [U : S]^{-1} \sum D(\pi(u) v) = D(v)$. $\square$

**Proposition 3.13.28 (a perfect pairing gives the contragredient).** Let $\pi$ and $\pi'$ be admissible representations of $H$ on $V$ and $V'$, and let $P : V \times V' \to \mathbb{C}$ be a bilinear form with $P(\pi(g) v, \pi'(g) w) = P(v, w)$ for all $g$. Assume that $P$ is nondegenerate on both sides: for $w \ne 0$ there is $v$ with $P(v, w) \ne 0$, and for $v \ne 0$ there is $w$ with $P(v, w) \ne 0$. Then $w \mapsto P(\cdot, w)$ is an isomorphism of $\pi'$ onto $\pi^\vee$.

Lean: `Langlands.LocalGL2.pcIso_contragredient_of_pairing`

*Proof.* Put $\Psi(w) = P(\cdot, w)$. If $U$ fixes $w$, then $P(\pi(u) v, w) = P(v, \pi'(u)^{-1} w) = P(v, w)$, so $\Psi(w)$ is fixed by $U$ and is smooth. The invariance of $P$ gives $\Psi(\pi'(g) w) = \pi^\vee(g) \Psi(w)$. The map is injective by the nondegeneracy in $w$.

Surjectivity. Let $\lambda \in V^\vee$, and choose a compact open subgroup $U$ that fixes $\lambda$. The spaces $V^U$ and $V'^U$ have finite dimension. The restriction of $P$ to $V^U \times V'^U$ is nondegenerate on both sides. Indeed, let $0 \ne v \in V^U$, and choose $w \in V'$ with $P(v, w) \ne 0$. The form $D = P(v, \cdot)$ is invariant under $U$, since $P(v, \pi'(u) x) = P(\pi(u)^{-1} v, x) = P(v, x)$. Lemma 3.13.27 gives $\bar w \in V'^U$ with $P(v, \bar w) = P(v, w) \ne 0$. The other side is the same. A bilinear form on two finite dimensional spaces that is nondegenerate on both sides is perfect. So there is $w \in V'^U$ with $P(x, w) = \lambda(x)$ for all $x \in V^U$. For an arbitrary $x \in V$, Lemma 3.13.27 gives $\bar x \in V^U$ with $D(\bar x) = D(x)$ for the two $U$-invariant forms $D = \lambda$ and $D = P(\cdot, w)$. So $P(x, w) = P(\bar x, w) = \lambda(\bar x) = \lambda(x)$, and $\Psi(w) = \lambda$. $\square$

Admissibility is needed for the step "nondegenerate implies perfect". Exercise 46 shows that the statement fails without it.

Now we set up the pairing for $GL_2$. Let $dk$ be the Haar measure of mass 1 on $K_0$.

**Definition 3.13.29 (the integral and the functions of modulus type).** For a function $\varphi$ on $G$ let
$$\mathcal{I}(\varphi) = \int_{K_0} \varphi(k) \, dk.$$
A function $\varphi : G \to \mathbb{C}$ is of *modulus type* if $\varphi(bg) = |a/d| \varphi(g)$ for $b = \left(\begin{smallmatrix} a & * \\ 0 & d \end{smallmatrix}\right) \in B$ and $g \in G$, and $\varphi$ is invariant on the right under an open subgroup. The statement `PcIntInvariant` for $K$ says that $\mathcal{I}(R_g \varphi) = \mathcal{I}(\varphi)$ for each $\varphi$ of modulus type and each $g \in G$, where $(R_g \varphi)(x) = \varphi(xg)$.

Lean: `Langlands.LocalGL2.pcInt`, `Langlands.LocalGL2.PcIsDelta`, `Langlands.LocalGL2.PcIntInvariant`, `Langlands.LocalGL2.pcContinuous_of_right`, `Langlands.LocalGL2.pcInt_add`, `Langlands.LocalGL2.pcInt_smul`

The library writes $\Lambda$ for $\mathcal{I}$. We use another letter to avoid a clash with the characters of types. The functions of modulus type form the space $\mathrm{Ind}_B^G \delta_B$ with $\delta_B(b) = |a/d|$, and `PcIntInvariant` says that $\mathcal{I}$ is a $G$-invariant linear form on it. This is the invariant integral over $B \backslash G$ that Remark 3.11.33 says the library lacked ([BH06], Chapter 1, section 3).

**Lemma 3.13.30 (products are of modulus type).** Let $\alpha_i \beta_i = 1$ for $i = 1, 2$, let $f$ be a vector of the normalized $\alpha_1 \times \alpha_2$ and $f'$ a vector of $\beta_1 \times \beta_2$. Then $f f'$ is of modulus type. Also $|a/d| = 1$ for $b \in B \cap K_0$.

Lean: `Langlands.LocalGL2.pcIsDelta_mul`, `Langlands.LocalGL2.pcNormAbs_of_mem`, `Langlands.LocalGL2.pcContinuous_ps`

*Proof.* $(f f')(bg) = \alpha_1\beta_1(a) \alpha_2\beta_2(d) |a/d|^{1/2} |a/d|^{1/2} f(g) f'(g) = |a/d| (f f')(g)$. The intersection of the two open subgroups of right invariance is open. For $b \in B \cap K_0$, $a$ and $d$ are in $\mathcal{O}_K$ and $ad = \det b$ is a unit, so $a$ and $d$ are units. $\square$

**Proposition 3.13.31 (nondegeneracy).** Assume `PcIntInvariant`. Let $\alpha_1, \alpha_2$ be smooth, $\alpha_i \beta_i = 1$, and $0 \ne f \in \beta_1 \times \beta_2$. There is $F \in \alpha_1 \times \alpha_2$ with $\mathcal{I}(F f) \ne 0$.

Lean: `Langlands.LocalGL2.pcNondeg`

*Proof.* Choose $g_0$ with $f(g_0) \ne 0$, and put $f_1 = R_{g_0} f$, so that $f_1(1) \ne 0$. Choose a compact open subgroup $U \subseteq K_0$ such that $f_1$ is invariant on the right under $U$ and $\alpha_1(a) \alpha_2(d) = 1$ for $b \in B \cap U$. Define $F$ on $G$ by
$$F(bu) = \alpha_1(a) \alpha_2(d) |a/d|^{1/2} \quad (b \in B, u \in U), \qquad F = 0 \text{ outside } BU.$$
This is well defined: if $bu = b'u'$, then $b'^{-1} b = u' u^{-1} \in B \cap U$, on which the character is $1$ and $|a/d| = 1$ by Lemma 3.13.30. The set $BU$ is open and closed, $F$ has the transformation law of $\alpha_1 \times \alpha_2$, and $F$ is invariant on the right under $U$. Let $k \in K_0$. If $k = bu \in BU$, then $b = k u^{-1} \in B \cap K_0$, and
$$F(k) f_1(k) = \alpha_1(a)\alpha_2(d) |a/d|^{1/2} \cdot f_1(b) = |a/d| f_1(1) = f_1(1).$$
If $k \notin BU$, then $F(k) = 0$. So $F f_1$ restricted to $K_0$ is $f_1(1)$ times the indicator function of the open set $S = BU \cap K_0$, which contains $1$. A nonempty open set has positive Haar measure, so $\mathcal{I}(F f_1) = f_1(1) \, \mathrm{vol}(S) \ne 0$. Now $F f_1 = R_{g_0}((R_{g_0^{-1}} F) f)$, and $(R_{g_0^{-1}} F) f$ is of modulus type by Lemma 3.13.30. By `PcIntInvariant`, $\mathcal{I}((R_{g_0^{-1}} F) f) = \mathcal{I}(F f_1) \ne 0$. $\square$

**Proposition 3.13.32 (the contragredient from the invariance).** Assume `PcIntInvariant`. Then for smooth $\chi_1, \chi_2$ the pairing $\langle f, f' \rangle = \mathcal{I}(f f')$ of $\chi_1 \times \chi_2$ and $\chi_1^{-1} \times \chi_2^{-1}$ gives an isomorphism $(\chi_1 \times \chi_2)^\vee \cong \chi_1^{-1} \times \chi_2^{-1}$. So `PSContragredientIso` holds.

Lean: `Langlands.LocalGL2.pcPair`, `Langlands.LocalGL2.pcPair_apply`, `Langlands.LocalGL2.pcExists_compact_open_le`, `Langlands.LocalGL2.pcContragredientIso_of_invariant`

*Proof.* The pairing is bilinear, since the functions are continuous and $\mathcal{I}$ is linear. It is invariant: $\langle R_g f, R_g f' \rangle = \mathcal{I}(R_g(f f')) = \mathcal{I}(f f')$, by Lemma 3.13.30 and `PcIntInvariant`. It is nondegenerate on both sides by Proposition 3.13.31, applied once with $(\alpha, \beta) = (\chi, \chi^{-1})$ and once with $(\alpha, \beta) = (\chi^{-1}, \chi)$. Both representations are admissible (`principalSeries_isAdmissible`, Section 1.5), and each open subgroup of $G$ contains a compact open subgroup. Proposition 3.13.28 concludes. $\square$

### The invariant integral

It remains to prove `PcIntInvariant`. The set of $g$ with $\mathcal{I}(R_g \varphi) = \mathcal{I}(\varphi)$ for all $\varphi$ of modulus type is a subgroup, and it contains $K_0$. By the Iwasawa decomposition $G = B K_0$, it is enough to put $B$ into it. The diagonal element $\mathrm{diag}(\varpi, 1)$ is the hard case, and we reach it through the Iwahori subgroup.

Let $I \subseteq K_0$ be the Iwahori subgroup, the group of the $k \in K_0$ with $k_{21} \in \mathfrak{p}_K$. It is $\mathfrak{J}^\times$, it is open, so it is compact and has a Haar measure $di$ of mass 1. Let $c = \mathrm{vol}(I)$ for $dk$. Let
$$w = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}, \qquad \eta = \begin{pmatrix} 0 & 1 \\ \varpi & 0 \end{pmatrix}.$$
Then $w^2 = 1$, $w \in K_0$, and $\eta^2 = \varpi$ is central.

**Lemma 3.13.33 (the element $\eta$).**
1. For $k = \left(\begin{smallmatrix} a & b \\ c & d \end{smallmatrix}\right)$, $\eta k \eta^{-1} = \left(\begin{smallmatrix} d & \varpi^{-1} c \\ \varpi b & a \end{smallmatrix}\right)$. So $\eta I \eta^{-1} = I$, and $i \mapsto \eta i \eta^{-1}$ is a continuous automorphism of $I$ of order 2.
2. For each function $\phi$ on $G$ that is continuous on $x I$, $\int_I \phi(x \eta i \eta^{-1}) \, di = \int_I \phi(x i) \, di$.
3. $\eta w = \mathrm{diag}(1, \varpi)$ and $w \eta = \mathrm{diag}(\varpi, 1)$.

Lean: `Langlands.LocalGL2.pcIwahori`, `Langlands.LocalGL2.pcMem_iwahori`, `Langlands.LocalGL2.pcIsOpen_iwahori`, `Langlands.LocalGL2.pcEta`, `Langlands.LocalGL2.pcEta_conj_val`, `Langlands.LocalGL2.pcEtaInv_conj`, `Langlands.LocalGL2.pcEta_conj_mem`, `Langlands.LocalGL2.pcConj`, `Langlands.LocalGL2.pcConjFun_conjFun`, `Langlands.LocalGL2.pcIwInt`, `Langlands.LocalGL2.pcIwInt_eta`, `Langlands.LocalGL2.pcEta_weyl_val`, `Langlands.LocalGL2.pcWeyl_eta_val`

*Proof.* Part 1. With $\eta^{-1} = \left(\begin{smallmatrix} 0 & \varpi^{-1} \\ 1 & 0 \end{smallmatrix}\right)$ the product is a direct computation. If $k \in I$, then $c \in \mathfrak{p}_K$, so $\varpi^{-1} c \in \mathcal{O}_K$, the lower left entry $\varpi b$ lies in $\mathfrak{p}_K$, and the determinant is unchanged. So $\eta I \eta^{-1} \subseteq I$, and the same holds for $\eta^{-1}$, since $\eta^{-1} = \varpi^{-1}\eta$ and scalars act trivially by conjugation. The square of the automorphism is conjugation by the central element $\varpi$. Part 2. The image of $di$ under a continuous automorphism of $I$ is a left invariant measure of mass 1, so it is $di$ by uniqueness of Haar measure (`pcHaar_unique`). Part 3 is a direct computation. $\square$

The next lemma divides $K_0$ into $q + 1$ cosets of $I$. Choose a map $s : k \to \mathcal{O}_K$ that lifts the residue map, with $s(0) = 0$.

**Lemma 3.13.34 (the cells).** For $k \in K_0$ write $k = \left(\begin{smallmatrix} k_{11} & k_{12} \\ k_{21} & k_{22} \end{smallmatrix}\right)$. The $q + 1$ sets
$$C_\infty = \{ k : k_{11} \in \mathfrak{p}_K \} = wI, \qquad C_r = \{ k : k_{21} - s(r) k_{11} \in \mathfrak{p}_K \} = \bar n(s(r)) I \quad (r \in k)$$
are open and disjoint, and they cover $K_0$. So for each continuous $\phi$ on $K_0$,
$$\int_{K_0} \phi(k) \, dk = c \int_I \phi(w i) \, di + c \sum_{r \in k} \int_I \phi(\bar n(s(r)) i) \, di.$$

Lean: `Langlands.LocalGL2.pcLift`, `Langlands.LocalGL2.pcLift_zero`, `Langlands.LocalGL2.pcCell`, `Langlands.LocalGL2.pcIsOpen_cell`, `Langlands.LocalGL2.pcCell_none_iff`, `Langlands.LocalGL2.pcCell_some_iff`, `Langlands.LocalGL2.pcCell_sum`, `Langlands.LocalGL2.pcInt_cell`

*Proof.* The cells are the fibres of the map $K_0 \to \mathbb{P}^1(k)$ that sends $k$ to the line spanned by the reduction of its first column $(k_{11}, k_{21})$. This column is not zero modulo $\mathfrak{p}_K$, since $\det k$ is a unit. If $k_{11} \in \mathfrak{p}_K$, the line is $[0 : 1]$, which is the cell $C_\infty$. Otherwise $k_{11}$ is a unit, and the line is $[1 : r]$ with $r$ the residue of $k_{21}/k_{11}$, and $k_{21} - s(r) k_{11} \in \mathfrak{p}_K$ exactly for this $r$. So the cells are disjoint and cover $K_0$, and each is open because the residue map is locally constant. For the cosets: $wk$ has lower left entry $k_{11}$, so $k \in C_\infty$ if and only if $wk \in I$, that is $k \in wI$. Also $\bar n(-s) k$ has lower left entry $k_{21} - s k_{11}$, so $k \in C_r$ if and only if $\bar n(s(r))^{-1} k \in I$. The left translate $x I$ of $I$ by $x \in K_0$ carries the measure $c \cdot (i \mapsto x i)_* di$, by the uniqueness of Haar measure on $I$. Summing over the cells gives the formula. $\square$

**Proposition 3.13.35 (the decomposition formula).** Let $\varphi$ be of modulus type. Then
$$\mathcal{I}(\varphi) = c \left( \int_I \varphi(i) \, di + q \int_I \varphi(w i) \, di \right).$$

Lean: `Langlands.LocalGL2.pcWeyl_mem`, `Langlands.LocalGL2.pcUnip_mem`, `Langlands.LocalGL2.pcIwInt_mul_left`, `Langlands.LocalGL2.pcIwInt_lower`, `Langlands.LocalGL2.pcInt_decomp`, `Langlands.LocalGL2.pcIsDelta_continuous`

*Proof.* Apply Lemma 3.13.34. The cell $C_0$ gives $\int_I \varphi(i) \, di$, since $s(0) = 0$. Let $r \ne 0$ and $y = s(r)$, a unit. Then
$$\bar n(y) = \begin{pmatrix} -y^{-1} & 1 \\ 0 & y \end{pmatrix} w \, n(y^{-1}),$$
as one checks by multiplying out. The first factor lies in $B$ with $|a/d| = |y^{-2}| = 1$. So $\varphi(\bar n(y) i) = \varphi(w n(y^{-1}) i)$, and since $n(y^{-1}) \in I$ and $di$ is left invariant, $\int_I \varphi(\bar n(y) i) \, di = \int_I \varphi(w i) \, di$. There are $q - 1$ such cells, and the cell $C_\infty$ gives one more copy of $\int_I \varphi(wi)\, di$. $\square$

**Proposition 3.13.36 (invariance under $\eta$).** Let $\varphi$ be of modulus type. Then $\mathcal{I}(R_\eta \varphi) = \mathcal{I}(\varphi)$.

Lean: `Langlands.LocalGL2.pcNormAbs_unif`, `Langlands.LocalGL2.pcNormAbs_inv_unif`, `Langlands.LocalGL2.pcIsDelta_right`, `Langlands.LocalGL2.pcInt_eta`

*Proof.* The function $R_\eta \varphi$ is again of modulus type, so Proposition 3.13.35 applies to it:
$$\mathcal{I}(R_\eta \varphi) = c \left( \int_I \varphi(i \eta) \, di + q \int_I \varphi(w i \eta) \, di \right).$$
For the first term write $i \eta = \eta (\eta^{-1} i \eta)$. By Lemma 3.13.33, part 2, applied to the automorphism $i \mapsto \eta^{-1} i \eta$, which is the same as $i \mapsto \eta i \eta^{-1}$, we get $\int_I \varphi(i \eta) \, di = \int_I \varphi(\eta i) \, di$. Now $\eta i = (\eta w)(w i) = \mathrm{diag}(1, \varpi) \, w i$, and $|1/\varpi| = q$, so $\int_I \varphi(\eta i) \, di = q \int_I \varphi(w i) \, di$. For the second term, in the same way, $\int_I \varphi(w i \eta) \, di = \int_I \varphi(w \eta i) \, di$, and $w \eta = \mathrm{diag}(\varpi, 1)$ with $|\varpi| = q^{-1}$, so it equals $q^{-1} \int_I \varphi(i) \, di$. Thus
$$\mathcal{I}(R_\eta \varphi) = c \left( q \int_I \varphi(w i) \, di + q \cdot q^{-1} \int_I \varphi(i) \, di \right) = \mathcal{I}(\varphi). \qquad \square$$

The two cells of Proposition 3.13.35 trade places under $\eta$, and the factors $q$ and $q^{-1}$ from the modulus character exactly undo the weight $q$ of the big cell. Exercise 47 shows that no other power of $|a/d|$ has this property.

**Theorem 3.13.37 (the invariant integral and the contragredient).** `PcIntInvariant` holds for each $K$. So `PSContragredientIso` holds: for smooth characters $\chi_1, \chi_2$ of $K^\times$, $(\chi_1 \times \chi_2)^\vee \cong \chi_1^{-1} \times \chi_2^{-1}$, by the pairing $\langle f, f' \rangle = \int_{K_0} f(k) f'(k) \, dk$.

Lean: `Langlands.LocalGL2.pcInvSubgroup`, `Langlands.LocalGL2.pcMaxCompact_le`, `Langlands.LocalGL2.pcEta_mem`, `Langlands.LocalGL2.pcScalar_mem`, `Langlands.LocalGL2.pcDiag`, `Langlands.LocalGL2.pcDiag_mem_maxCompact`, `Langlands.LocalGL2.pcDiag_mem`, `Langlands.LocalGL2.pcDiag_conj_unip`, `Langlands.LocalGL2.pcUnip_mem_inv`, `Langlands.LocalGL2.pcBorel_mem`, `Langlands.LocalGL2.pcIntInvariant_holds`, `Langlands.LocalGL2.psContragredientIso_holds`, `Langlands.GL2.iwasawa`

*Proof.* Let $H_{\mathcal{I}}$ be the set of $g \in G$ with $\mathcal{I}(R_g \varphi) = \mathcal{I}(\varphi)$ for all $\varphi$ of modulus type. Since $R_g \varphi$ is of modulus type when $\varphi$ is, and $R_{gh} = R_h R_g$, the set $H_{\mathcal{I}}$ is a subgroup: if $g, h \in H_{\mathcal{I}}$, then $\mathcal{I}(R_h R_g \varphi) = \mathcal{I}(R_g \varphi) = \mathcal{I}(\varphi)$, and $\mathcal{I}(R_{g^{-1}} \varphi) = \mathcal{I}(R_g R_{g^{-1}} \varphi) = \mathcal{I}(\varphi)$. It contains:
1. $K_0$, by the right invariance of $dk$ on the compact group $K_0$;
2. the centre, since $\varphi(xz) = \varphi(zx) = |z/z| \varphi(x) = \varphi(x)$;
3. $\eta$, by Proposition 3.13.36;
4. $\mathrm{diag}(\varpi, 1) = w \eta$, by 1 and 3, hence $\mathrm{diag}(x, 1) = \mathrm{diag}(u, 1) \mathrm{diag}(\varpi, 1)^k$ for each $x = u \varpi^k \in K^\times$, since $\mathrm{diag}(u, 1) \in K_0$ for a unit $u$;
5. $n(y)$ for each $y \in K$: choose $k$ with $\varpi^k y \in \mathcal{O}_K$; then $n(y) = \mathrm{diag}(\varpi^{-k}, 1) \, n(\varpi^k y) \, \mathrm{diag}(\varpi^k, 1)$, a product of elements of $H_{\mathcal{I}}$ by 1 and 4;
6. $B$: each $b = \left(\begin{smallmatrix} a & \beta \\ 0 & d \end{smallmatrix}\right)$ is $\mathrm{diag}(d, d) \, n(\beta/d) \, \mathrm{diag}(a/d, 1)$, a product of elements of $H_{\mathcal{I}}$ by 2, 5 and 4.

By the Iwasawa decomposition $G = B K_0$, $H_{\mathcal{I}} = G$. This is `PcIntInvariant`, and Proposition 3.13.32 gives `PSContragredientIso`. $\square$

The theorem is Proposition 1.3.4, part 3, for $GL_2$, and the argument is the standard construction of the invariant form on $\mathrm{Ind}_B^G \delta_B$ ([BH06], Chapter 1, section 3). The usual proof identifies $\mathcal{I}$ with an integral over $B \backslash G$. The proof above avoids quotient measures: it uses only the Haar measures of the compact groups $K_0$ and $I$ and the explicit element $\eta$.

**Example 3.13.38 (the cells for $K = \mathbb{Q}_3$).** Here $q = 3$, and we take $s(0) = 0$, $s(1) = 1$, $s(2) = 2$. The four cells are $wI$, $I$, $\bar n(1) I$ and $\bar n(2) I$. The element $k = \left(\begin{smallmatrix} 2 & 1 \\ 1 & 1 \end{smallmatrix}\right)$ has determinant 1, and $k_{21}/k_{11} = 1/2 \equiv 2$ modulo 3, so $k \in C_2$. Indeed $\bar n(2)^{-1} k = \left(\begin{smallmatrix} 2 & 1 \\ -3 & -1 \end{smallmatrix}\right) \in I$. The element $k' = \left(\begin{smallmatrix} 3 & 1 \\ 1 & 0 \end{smallmatrix}\right)$ has determinant $-1$ and $k'_{11} \in 3\mathbb{Z}_3$, so $k' \in C_\infty$, and $w k' = \left(\begin{smallmatrix} 1 & 0 \\ 3 & 1 \end{smallmatrix}\right) \in I$. The four cells have the same volume $c$, so $c = 1/4$ and $[K_0 : I] = 4 = |\mathbb{P}^1(\mathbb{F}_3)|$. For the function $\varphi_0(bk) = |a/d|$, which is well defined by Lemma 3.13.30, the decomposition formula reads $\mathcal{I}(\varphi_0) = \frac14(1 + 3 \cdot 1) = 1$, and the proof of Proposition 3.13.36 gives $\mathcal{I}(R_\eta \varphi_0) = \frac14(3 \cdot 1 + 3 \cdot \frac13 \cdot 1) = 1$.

### What is open for $GL_2$, $p \ne 2$

**Corollary 3.13.39 (the reduction as it stands).** Let $p \ne 2$. The statement `Langlands.LocalLanglandsGL2Odd` follows, for all $K$, from:
1. `ArtinCompat` and `Rectifier`, inputs 1 and 4 of Definition 3.9.30;
2. the five facts of `GaloisTameOpenInputs`, Corollary 3.12.34;
3. `SupercuspidalZetaLaurent`, Definition 3.11.19;
4. `PSLFactorIrreducible`, `PSLFactorDetChar` and `PSLFactorSteinberg`, facts 4 to 6 of Definition 3.11.31;
5. `TypeRepInjective` and `UncoveredParametrization`, inputs 2 and 5 of Definition 3.10.27.

Lean: `Langlands.LocalGL2.psInputProps_of_open`, `Langlands.LocalGL2.nonSupercuspidalInputs_of_contragredient_lFactor`, `Langlands.LocalGL2.psContragredientIso_holds`, `Langlands.LocalGL2.typeRepIndependent`, `Langlands.LocalGL2.GL2OddFineInputs`, `Langlands.localLanglandsGL2_odd_of_fineInputs` (the joining step is not yet in the library)

*Proof.* By `psInputProps_of_open`, the structure `PSInputProps` follows from `PSContragredientIso` and the three facts of item 4. The first holds by Theorem 3.13.37, and `psInputProps_of_open` also supplies Theorems 3.13.22 and 3.13.25. So item 4 gives the six facts of Definition 3.11.31. Theorem 3.13.19 gives `TypeRepIndependent`. With these, the items are the hypotheses of Corollary 3.12.35, which concludes. $\square$

**Remark 3.13.40 (what is still open for $GL_2$, $p \ne 2$).** This list replaces Remark 3.12.36.
1. `ArtinCompat` ([Ser79], Chapter XI).
2. The five facts `ArtinConjCompat`, `WildInertiaProP`, `TameInertiaProcyclic`, `OpenIndexTwoQuad` and `WildArtinUnits` of Corollary 3.12.34.
3. `Rectifier`, with the characters $\Delta_\xi$ of [BH06], section 34.
4. `SupercuspidalZetaLaurent`, the analytic half of Proposition 2.5.6.
5. The three $L$-factor facts `PSLFactorIrreducible`, `PSLFactorDetChar` and `PSLFactorSteinberg` of Definition 3.11.31.
6. `TypeRepInjective` and `UncoveredParametrization`.
7. The structure that joins the results of Sections 3.11 to 3.13 into `GL2OddFineInputs`.
8. The case $p = 2$, the $\varepsilon$-factors, and the uniqueness of Theorem 3.3.1.

Item 5 has lost `PSSupercuspidalJacquet`, `PSContragredientIso` and `SmoothDualExtends`, and item 6 has lost `TypeRepIndependent`. The open inputs on the principal series are now all computations of Godement-Jacquet zeta integrals, of the kind done for the trivial representation in Example 3.11.22 and Exercise 35. The open inputs on the cuspidal types are `TypeRepInjective`, which needs the intertwining of two types of different pairs ([BH06], section 15), and the construction for the pairs that are not covered, which needs the depth zero representations and the Heisenberg representations of Remark 3.9.14.
