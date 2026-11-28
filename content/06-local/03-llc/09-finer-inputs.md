---
title: Finer inputs for the correspondence for GL(2)
nodes: []
sources: [BH06, JL70, Ser79]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Finer inputs for the correspondence for GL(2)

Theorem 3.9.33 reduces the Lean statement `Langlands.LocalLanglandsGL2Odd` to the six inputs of Definition 3.9.30. Two of these inputs are large. Input 6 contains the whole correspondence off the supercuspidal representations, and input 2 contains the whole tame parametrization theorem. This section replaces them with smaller statements, and it proves everything between these statements and the two inputs. There are three parts. First we classify the Weil-Deligne representations of dimension 2 that are not irreducible, with complete proofs in linear algebra, and we reduce input 6 to eight statements on the principal series. Then we attach a representation to each cuspidal type datum of a pair, we prove its first properties, and we reduce input 2 to five statements on cuspidal types. Last, we prove that an admissible compact induction from a subgroup that is compact modulo the centre is supercuspidal, and that an additive character of level one exists. The section ends with a precise list of what is still open for $GL_2$, $p \ne 2$.

We use the notation of Section 3.9. In particular $K$ is a nonarchimedean local field with residue field $k$ of order $q$, $\varpi$ is a uniformizer, $G = GL_2(K)$, $\mathrm{art}_K$ is a local Artin map, $\Phi$ is a geometric Frobenius element of $W_K$, and $|w|$ is the norm of $w \in W_K$, so that $|\Phi| = q^{-1}$. A *character* of $W_K$ is a homomorphism $W_K \to \mathbb{C}^\times$ with open kernel. For a character $\chi$ of $K^\times$ we write $\chi \times \chi'$ for the normalized principal series of Section 1.5, and $\chi_L = \chi \circ N_{L/K}$ for a quadratic extension $L/K$. We write $E_{12}$ for the matrix of size 2 that sends the second basis vector to the first, and $\mathrm{diag}(a, b)$ for the diagonal matrix.

The Lean files are `Langlands/Local/GL2NonSupercuspidal.lean`, `Langlands/Local/GL2TameTypes.lean` and `Langlands/Local/CIndSupercuspidal.lean`. They contain no `sorry`. The declarations are in the namespace `Langlands.LocalGL2`, except for the general facts on compact induction, which are in `Langlands`, and the additive character, which is in `Langlands.LocalGL1`.

### Models of the parameters that are not irreducible

We prove Proposition 3.3.2 again in coordinates, with the exact isomorphism conditions. The library needs the coordinates, because Example 3.3.5 fixes the matrices.

**Definition 3.10.1 (Steinberg pairs and models).** Let $\varphi_1, \varphi_2$ be characters of $W_K$.
1. The pair $(\varphi_1, \varphi_2)$ is a *Steinberg pair* if $\varphi_1(w) = \varphi_2(w) |w|$ for each $w \in W_K$.
2. The *model* $M(\varphi_1, \varphi_2)$ is the pair $(r, N)$ on $\mathbb{C}^2$ with $r(w) = \mathrm{diag}(\varphi_1(w), \varphi_2(w))$, and with $N = E_{12}$ if $(\varphi_1, \varphi_2)$ is a Steinberg pair and $N = 0$ otherwise.

Lean: `Langlands.LocalGL2.IsStW`, `Langlands.LocalGL2.wdModel`, `Langlands.LocalGL2.diagHom`

**Lemma 3.10.2 (the two Steinberg conditions exclude each other).** The pairs $(\varphi_1, \varphi_2)$ and $(\varphi_2, \varphi_1)$ are not both Steinberg pairs.

Lean: `Langlands.LocalGL2.weilNorm_geomFrob`, `Langlands.LocalGL2.weilNorm_geomFrob_ne_one`, `Langlands.LocalGL2.not_isStW_and`

*Proof.* If both are Steinberg pairs, then $\varphi_1(\Phi) = \varphi_2(\Phi) |\Phi| = \varphi_1(\Phi) |\Phi|^2$. Since $\varphi_1(\Phi) \ne 0$, we get $q^{-2} = 1$, which is false. $\square$

**Lemma 3.10.3 (models are Weil-Deligne representations).** The model $M(\varphi_1, \varphi_2)$ is a Weil-Deligne representation of dimension 2, and it is not irreducible.

Lean: `Langlands.LocalGL2.wdModel_r`, `Langlands.LocalGL2.wdModel_N`, `Langlands.LocalGL2.isSemisimple_diagonal`, `Langlands.LocalGL2.not_isIrreducible_wdModel`

*Proof.* The kernel of $r$ contains $\ker \varphi_1 \cap \ker \varphi_2$, which is open. Each $r(w)$ is diagonal, so it is semisimple. The matrix $N$ is nilpotent, since $E_{12}^2 = 0$. For the relation $r(w) N r(w)^{-1} = |w| N$ we can assume $N = E_{12}$. Then
$$\mathrm{diag}(a, b) \, E_{12} \, \mathrm{diag}(a, b)^{-1} = a b^{-1} E_{12},$$
and $\varphi_1(w) \varphi_2(w)^{-1} = |w|$ for a Steinberg pair. The line $\mathbb{C} e_1$ is stable under each $r(w)$ and under $N$, because $N e_1 = 0$. So the representation is not irreducible. $\square$

The next lemma collects the two facts on matrices of size 2 that the classification uses.

**Lemma 3.10.4 (two facts on upper triangular matrices).** Let $M$ be an upper triangular complex matrix of size 2.
1. If $M$ is semisimple and its two diagonal entries are equal, then $M$ is a scalar matrix.
2. If $M$ is nilpotent, then $M = c E_{12}$ for some $c \in \mathbb{C}$.

Lean: `Langlands.LocalGL2.upper_eq_zero_of_isSemisimple`, `Langlands.LocalGL2.eq_smul_single_of_isNilpotent`

*Proof.* Part 1. Let $a$ be the diagonal entry. Then $M - a$ is upper triangular with zero diagonal, so $(M - a)^2 = 0$. It is also semisimple, since $M$ is semisimple and $a$ is a scalar. A semisimple nilpotent matrix is zero. Part 2. The diagonal entries of $M$ are its eigenvalues, and a nilpotent matrix has only the eigenvalue $0$. Equivalently, $\mathrm{tr}(M) = 0$ and $\mathrm{tr}(M^2) = 0$, and for an upper triangular $M$ these are $m_{11} + m_{22} = 0$ and $m_{11}^2 + m_{22}^2 = 0$, so $m_{11} = m_{22} = 0$. $\square$

**Lemma 3.10.5 (upper triangular form).** Let $\rho = (r, N)$ be a Weil-Deligne representation of dimension 2 that is not irreducible. Then $\rho$ is isomorphic to a representation $(r', N')$ in which each $r'(w)$ and $N'$ are upper triangular. The diagonal entries of $r'$ are two characters $\alpha$ and $\delta$ of $W_K$, and $N' = c E_{12}$ for some $c \in \mathbb{C}$.

Lean: `Langlands.LocalGL2.exists_iso_upper`, `Langlands.LocalGL2.upperChar`, `Langlands.LocalGL2.isOpen_ker_upperChar`, `Langlands.LocalGL2.iso_conjBy`

*Proof.* Since $\rho$ is not irreducible, there is a line $\mathbb{C} v$ that is stable under each $r(w)$ and under $N$. Choose $P \in GL_2(\mathbb{C})$ with $P v = e_1$ and conjugate $\rho$ by $P$. In the new basis the line is $\mathbb{C} e_1$, so the matrices of $r'(w)$ and $N'$ have zero entry in position $(2, 1)$. The map $w \mapsto r'(w)_{11}$ is a homomorphism, because the product of two upper triangular matrices has as diagonal the product of the diagonals. The same holds for $r'(w)_{22}$. Both are trivial on $\ker r'$, which is open, so $\alpha$ and $\delta$ have open kernels. By part 2 of Lemma 3.10.4, $N' = c E_{12}$. $\square$

**Lemma 3.10.6 (upper triangular images are commutative).** Let $(r, N)$ be a Weil-Deligne representation of dimension 2 in which each $r(w)$ is upper triangular. Then $r(w) r(w') = r(w') r(w)$ for all $w, w' \in W_K$.

Lean: `Langlands.LocalGL2.commute_of_upper`

*Proof.* Let $c = w w' w^{-1} w'^{-1}$. The matrix $r(c)$ is upper triangular. Its diagonal entries are $\alpha(c) = 1$ and $\delta(c) = 1$, since $\alpha$ and $\delta$ take values in a commutative group. The matrix $r(c)$ is semisimple, because each $r(w)$ is semisimple. By part 1 of Lemma 3.10.4, $r(c) = 1$. $\square$

**Lemma 3.10.7 (diagonal form).** Let $(r, N)$ be as in Lemma 3.10.5, with $r$ upper triangular and $N = c E_{12}$. Then $(r, N)$ is isomorphic to a representation $(r', N)$ with the same $N$ and with $r'(w) = \mathrm{diag}(\alpha(w), \delta(w))$ for each $w$.

Lean: `Langlands.LocalGL2.exists_iso_diag`, `Langlands.LocalGL2.upperGL`, `Langlands.LocalGL2.conj_upperGL_apply`

*Proof.* Suppose first that $\alpha = \delta$. Then each $r(w)$ is upper triangular and semisimple with equal diagonal entries, so it is the scalar $\alpha(w)$ by part 1 of Lemma 3.10.4, and $r$ is already diagonal. Suppose next that $\alpha(w_0) \ne \delta(w_0)$ for some $w_0$. Write $r(w_0) = \begin{pmatrix} a & b \\ 0 & d \end{pmatrix}$ with $a \ne d$, and put $t = b / (d - a)$ and $u = \begin{pmatrix} 1 & t \\ 0 & 1 \end{pmatrix}$. A direct computation gives
$$u^{-1} r(w_0) u = \begin{pmatrix} a & b + t(a - d) \\ 0 & d \end{pmatrix} = \mathrm{diag}(a, d).$$
Conjugation by $u$ keeps each $r(w)$ upper triangular with the same diagonal, and $u^{-1} E_{12} u = E_{12}$, so it does not change $N$. After this conjugation, $r(w_0)$ is diagonal with distinct entries. By Lemma 3.10.6 each $r(w)$ commutes with $r(w_0)$. A matrix that commutes with a diagonal matrix with distinct entries is diagonal. So each $r(w)$ is $\mathrm{diag}(\alpha(w), \delta(w))$. $\square$

**Theorem 3.10.8 (classification).** Each Weil-Deligne representation of dimension 2 that is not irreducible is isomorphic to a model $M(\varphi_1, \varphi_2)$.

Lean: `Langlands.LocalGL2.exists_iso_wdModel_of_diag`, `Langlands.LocalGL2.exists_iso_wdModel`, `Langlands.LocalGL2.swapGL`

*Proof.* By Lemmas 3.10.5 and 3.10.7 we can assume that $r = \mathrm{diag}(\alpha, \delta)$ and $N = c E_{12}$. There are three cases.
1. If $c \ne 0$, then the relation $r(w) N r(w)^{-1} = |w| N$ reads $\alpha(w) \delta(w)^{-1} c = |w| c$, so $(\alpha, \delta)$ is a Steinberg pair. Conjugation by $\mathrm{diag}(1, c^{-1})$ does not change $r$ and sends $c E_{12}$ to $E_{12}$. The result is $M(\alpha, \delta)$.
2. If $c = 0$ and $(\alpha, \delta)$ is not a Steinberg pair, then $\rho$ is $M(\alpha, \delta)$ itself.
3. If $c = 0$ and $(\alpha, \delta)$ is a Steinberg pair, then $(\delta, \alpha)$ is not a Steinberg pair by Lemma 3.10.2. Conjugation by the matrix that exchanges $e_1$ and $e_2$ sends $\rho$ to $(\mathrm{diag}(\delta, \alpha), 0) = M(\delta, \alpha)$. $\square$

Case 3 shows that the order of the characters carries information. The pair $(\alpha, \delta)$ with $N = 0$ and $\alpha = \delta |\cdot|$ is not the model $M(\alpha, \delta)$, which has $N = E_{12}$. The next theorem says exactly when two models are isomorphic.

**Theorem 3.10.9 (isomorphisms of models).** The models $M(\varphi_1, \varphi_2)$ and $M(\psi_1, \psi_2)$ are isomorphic if and only if one of the following holds.
1. $(\psi_1, \psi_2) = (\varphi_1, \varphi_2)$.
2. $(\psi_1, \psi_2) = (\varphi_2, \varphi_1)$, and neither $(\varphi_1, \varphi_2)$ nor $(\varphi_2, \varphi_1)$ is a Steinberg pair.

Lean: `Langlands.LocalGL2.iso_wdModel_iff`, `Langlands.LocalGL2.iso_wdModel_swap`, `Langlands.LocalGL2.mul_eq_of_iso`, `Langlands.LocalGL2.char_eq_of_mul_eq`

*Proof.* In case 1 there is nothing to prove. In case 2 both models have $N = 0$, and the swap matrix conjugates one into the other. Conversely, let $g = (g_{ij}) \in GL_2(\mathbb{C})$ be an isomorphism. Then $g \, \mathrm{diag}(\varphi_1, \varphi_2)(w) = \mathrm{diag}(\psi_1, \psi_2)(w) \, g$ and $g N = N' g$, where $N$ and $N'$ are the two nilpotent parts. In entries, the first relation is
$$\psi_i(w) \, g_{ij} = g_{ij} \, \varphi_j(w) \quad \text{for all } i, j, w. \tag{1}$$
So $g_{ij} \ne 0$ implies $\psi_i = \varphi_j$. We use $\det g = g_{11} g_{22} - g_{12} g_{21} \ne 0$.

Suppose that both models have $N = E_{12}$. The entry $(2, 1)$ of $g E_{12} = E_{12} g$ gives $0 = 0$, and the entry $(1, 1)$ gives $0 = g_{21}$. So $g$ is upper triangular, $g_{11} g_{22} \ne 0$, and (1) gives case 1. Suppose that exactly one model has $N = E_{12}$. If $N = E_{12}$ and $N' = 0$, then $g E_{12} = 0$, so the first column of $g$ is zero. If $N = 0$ and $N' = E_{12}$, then $E_{12} g = 0$, so the second row of $g$ is zero. Both contradict $\det g \ne 0$. Suppose that both models have $N = 0$. If $g_{11} g_{22} \ne 0$, then (1) gives case 1. Otherwise $g_{12} g_{21} \ne 0$, and (1) gives $\psi_1 = \varphi_2$ and $\psi_2 = \varphi_1$. Since $N = 0$, the pair $(\varphi_1, \varphi_2)$ is not a Steinberg pair, and since $N' = 0$, the pair $(\psi_1, \psi_2) = (\varphi_2, \varphi_1)$ is not one either. This is case 2. $\square$

So $\eta |\cdot|^{1/2} \oplus \eta |\cdot|^{-1/2}$ with $N = 0$ is the model $M(\eta |\cdot|^{-1/2}, \eta |\cdot|^{1/2})$, and it is not isomorphic to $\mathrm{Sp}(2) \otimes \eta = M(\eta |\cdot|^{1/2}, \eta |\cdot|^{-1/2})$. This agrees with Proposition 3.3.2.

**Proposition 3.10.10 (duals, twists and determinants of models).** Let $\varphi_1, \varphi_2, \varphi$ be characters of $W_K$.
1. $(\varphi_2^{-1}, \varphi_1^{-1})$ is a Steinberg pair if and only if $(\varphi_1, \varphi_2)$ is one, and the dual of $M(\varphi_1, \varphi_2)$ is isomorphic to $M(\varphi_2^{-1}, \varphi_1^{-1})$.
2. $(\varphi_1 \varphi, \varphi_2 \varphi)$ is a Steinberg pair if and only if $(\varphi_1, \varphi_2)$ is one, and $M(\varphi_1, \varphi_2) \otimes \varphi = M(\varphi_1 \varphi, \varphi_2 \varphi)$.
3. $\det M(\varphi_1, \varphi_2) = \varphi_1 \varphi_2$.

Lean: `Langlands.LocalGL2.isStW_inv_iff`, `Langlands.LocalGL2.dualGL`, `Langlands.LocalGL2.isDual_wdModel`, `Langlands.LocalGL2.isStW_mul_iff`, `Langlands.LocalGL2.isTwist_wdModel`, `Langlands.LocalGL2.det_wdModel`

*Proof.* Part 1. The relation $\varphi_2^{-1} = \varphi_1^{-1} |\cdot|$ is the relation $\varphi_1 = \varphi_2 |\cdot|$ multiplied by $\varphi_1^{-1} \varphi_2^{-1}$. The dual of $(r, N)$ is $(r^\vee, N^\vee)$ with $r^\vee(w) = {}^t r(w)^{-1}$ and $N^\vee = -{}^t N$. For the model this is $r^\vee = \mathrm{diag}(\varphi_1^{-1}, \varphi_2^{-1})$, with $N^\vee = -E_{21}$ in the Steinberg case. Let $h = \begin{pmatrix} 0 & 1 \\ -1 & 0 \end{pmatrix}$. Then $h \, \mathrm{diag}(a, b) \, h^{-1} = \mathrm{diag}(b, a)$ and $h (-E_{21}) h^{-1} = E_{12}$. So $h$ conjugates the dual to $M(\varphi_2^{-1}, \varphi_1^{-1})$. Part 2. The relation $\varphi_1 \varphi = \varphi_2 \varphi |\cdot|$ is equivalent to $\varphi_1 = \varphi_2 |\cdot|$. The twist multiplies $r$ by $\varphi$ and keeps $N$, so the two sides are equal. Part 3 is clear. $\square$

The $L$-factor of a Weil-Deligne representation $\rho = (r, N)$ is $L(s, \rho) = \det(1 - q^{-s} r(\Phi) \mid V_N^{I_K})^{-1}$, where $V_N = \ker N$. For a character $\varphi$ of $W_K$ we put $L(s, \varphi) = (1 - \varphi(\Phi) q^{-s})^{-1}$ if $\varphi$ is trivial on $I_K$, and $L(s, \varphi) = 1$ otherwise.

**Proposition 3.10.11 ($L$-factors of models).** We have $L(s, M(\varphi_1, \varphi_2)) = L(s, \varphi_1)$ if $(\varphi_1, \varphi_2)$ is a Steinberg pair, and $L(s, M(\varphi_1, \varphi_2)) = L(s, \varphi_1) L(s, \varphi_2)$ otherwise. Isomorphic representations have the same $L$-factor.

Lean: `Langlands.LocalGL2.charLFactorW`, `Langlands.LocalGL2.lFactor_wdModel`, `Langlands.LocalGL2.lFactor_eq_of_iso`, `Langlands.LocalGL2.mulVec_diagonal_eq_iff`

*Proof.* If $N = 0$, then $V_N = \mathbb{C}^2$. A vector $x$ is fixed by $I_K$ if and only if $x_i = 0$ for each $i$ with $\varphi_i$ not trivial on $I_K$. So $V_N^{I_K}$ is the sum of the lines $\mathbb{C} e_i$ with $\varphi_i$ unramified, and $r(\Phi)$ acts on $\mathbb{C} e_i$ by $\varphi_i(\Phi)$. The determinant splits into the two factors. If $N = E_{12}$, then $V_N = \mathbb{C} e_1$, which is fixed by $I_K$ exactly when $\varphi_1$ is unramified, and $\Phi$ acts on it by $\varphi_1(\Phi)$. An isomorphism $g$ maps $V_N^{I_K}$ onto $V'^{I_K}_{N'}$ and conjugates the action of $r(\Phi)$, so the determinants agree. $\square$

The last step on the Galois side passes from $K^\times$ to $W_K$. For a smooth character $\chi$ of $K^\times$ put $\varphi_\chi = \chi \circ \mathrm{art}_K^{-1}$, a character of $W_K$ through $W_K^{\mathrm{ab}}$. A pair $(\chi_1, \chi_2)$ of characters of $K^\times$ is a *Steinberg pair* if $\chi_1(x) = \chi_2(x) |x|$ for all $x \in K^\times$.

**Proposition 3.10.12 (the Steinberg condition through the Artin map).** Let $\mathrm{art}_K$ be a local Artin map.
1. $|w| = |\mathrm{art}_K^{-1}(w)|$ for each $w \in W_K$, where $\mathrm{art}_K^{-1}$ means the inverse on $W_K^{\mathrm{ab}}$.
2. $(\varphi_{\chi_1}, \varphi_{\chi_2})$ is a Steinberg pair if and only if $(\chi_1, \chi_2)$ is one.
3. $L(s, \varphi_\chi) = L(s, \chi)$.
4. The map $\chi \mapsto \varphi_\chi$ is a bijection from the smooth characters of $K^\times$ onto the characters of $W_K$, and $\varphi_{\chi \chi'} = \varphi_\chi \varphi_{\chi'}$.

Lean: `Langlands.LocalGL2.weilNorm_eq`, `Langlands.LocalGL2.IsSt`, `Langlands.LocalGL2.isStW_weilChar_iff`, `Langlands.LocalGL2.charLFactorW_weilChar`, `Langlands.LocalGL2.charOfWeil`, `Langlands.LocalGL2.weilChar_charOfWeil`, `Langlands.LocalGL2.isSmoothChar_charOfWeil`, `Langlands.LocalGL2.weilChar_injective`, `Langlands.LocalGL2.weilChar_mul`, `Langlands.LocalGL2.weilChar_inv`

*Proof.* Part 1. The norm $|w|$ is $q^{-d(w)}$, where $w$ acts on the residue field as the $d(w)$-th power of the inverse of the Frobenius. By Theorem 3.2.1, part 1, $\mathrm{art}_K(\varpi')$ is a geometric Frobenius for each uniformizer $\varpi'$, so $d = 1$ on it. A unit $u$ is the quotient of the uniformizers $u \varpi$ and $\varpi$, so $d(\mathrm{art}_K(u)) = 0$. So $\mathrm{art}_K(x)$ has $d = v_K(x)$, and $|\mathrm{art}_K(x)| = q^{-v_K(x)} = |x|$. Part 2 follows from part 1 by evaluation at $\mathrm{art}_K(x)$. Part 3. $\varphi_\chi$ is trivial on $I_K$ if and only if $\chi$ is trivial on $\mathcal{O}_K^\times$, and then $\varphi_\chi(\Phi) = \chi(\varpi)$. Part 4. $\mathrm{art}_K$ is a topological isomorphism $K^\times \to W_K^{\mathrm{ab}}$, and a character of $W_K$ with open kernel factors through $W_K^{\mathrm{ab}}$. $\square$

### The principal series and the eight inputs

We now turn to $G$. A representation $\pi$ is *in* $\chi_1 \times \chi_2$ if there is a nonzero map of representations $\pi \to \chi_1 \times \chi_2$. In Lean this is `HasHom` with target `Langlands.principalSeries`, the normalized induction from the upper triangular Borel subgroup $B$. So $f(b g) = \chi_1(a) \chi_2(d) |a/d|^{1/2} f(g)$ for $b$ with diagonal $(a, d)$.

**Proposition 3.10.13 (central characters and twists in the principal series).** Let $\pi$ be irreducible and in $\chi_1 \times \chi_2$.
1. Each nonzero map $\pi \to \chi_1 \times \chi_2$ is injective.
2. The central character of $\pi$ is $\chi_1 \chi_2$.
3. For a smooth character $\chi$ of $K^\times$, $\pi \otimes (\chi \circ \det)$ is in $\chi_1 \chi \times \chi_2 \chi$.

Lean: `Langlands.LocalGL2.injective_of_isIrreducible`, `Langlands.LocalGL2.hasCentralChar_of_hasHom`, `Langlands.LocalGL2.mulDetChar`, `Langlands.LocalGL2.hasHom_twist`

*Proof.* Part 1. The kernel of the map is a subrepresentation of $\pi$, and it is not $\pi$. Part 2. Let $T : \pi \to \chi_1 \times \chi_2$ be nonzero and let $z = c \cdot 1$ be scalar. Then $z$ is central and lies in $B$ with $a = d = c$, so
$$T(\pi(z) v)(g) = (T v)(g z) = (T v)(z g) = \chi_1(c) \chi_2(c) \, (T v)(g).$$
So $T(\pi(z) v - \chi_1 \chi_2(c) v) = 0$, and part 1 gives $\pi(z) v = \chi_1 \chi_2(c) v$. Part 3. The map $f \mapsto (\chi \circ \det) f$ sends $\chi_1 \times \chi_2$ to $\chi_1 \chi \times \chi_2 \chi$, because $\chi(\det(b g)) = \chi(a) \chi(d) \chi(\det g)$. It commutes with the actions of $G$ on $(\chi_1 \times \chi_2) \otimes (\chi \circ \det)$ and on $\chi_1 \chi \times \chi_2 \chi$. Compose it with $T \otimes 1$. $\square$

**Definition 3.10.14 (the eight inputs on the principal series).** Let $\chi_1, \chi_2, \psi_1, \psi_2$ be smooth characters of $K^\times$, and let $\pi, \pi'$ be irreducible admissible representations of $G$. The inputs for $K$ are the following statements, for all such data.
1. `PSSubExists`. Some $\pi$ is in $\chi_1 \times \chi_2$ ([BH06], Chapter 2, section 9; [JL70], section 3).
2. `PSSubUnique`. If $\pi$ and $\pi'$ are both in $\chi_1 \times \chi_2$, then $\pi \cong \pi'$ (same sources).
3. `PSSubRigid`. If $\pi$ is in $\chi_1 \times \chi_2$ and in $\psi_1 \times \psi_2$, then $(\psi_1, \psi_2) = (\chi_1, \chi_2)$, or $(\psi_1, \psi_2) = (\chi_2, \chi_1)$ and neither $(\chi_1, \chi_2)$ nor $(\chi_2, \chi_1)$ is a Steinberg pair. The proof in [BH06], Chapter 2, section 9, uses the Jacquet module and Frobenius reciprocity.
4. `PSSubSwap`. If neither $(\chi_1, \chi_2)$ nor $(\chi_2, \chi_1)$ is a Steinberg pair and $\pi$ is in $\chi_1 \times \chi_2$, then $\pi$ is in $\chi_2 \times \chi_1$. This follows from the irreducibility criterion and $\chi_1 \times \chi_2 \cong \chi_2 \times \chi_1$ ([BH06], Chapter 2, section 9).
5. `NonSupercuspidalExhaustion`. If $\pi$ is not supercuspidal, then $\pi$ is in some $\chi_1 \times \chi_2$ ([BH06], Chapter 2, sections 9 and 10).
6. `PSSubNotSupercuspidal`. If $\pi$ is in $\chi_1 \times \chi_2$, then $\pi$ is not supercuspidal (same sources).
7. `PSSubContragredient`. If $\pi$ is in $\chi_1 \times \chi_2$ and $\pi' \cong \pi^\vee$, then $\pi'$ is in $\chi_2^{-1} \times \chi_1^{-1}$ ([BH06], Chapter 2, section 9; [JL70], section 3).
8. `PSSubLFactor`. If $\pi$ is in $\chi_1 \times \chi_2$, then the Godement-Jacquet $L$-factor of $\pi$ is $L(s, \chi_1)$ if $(\chi_1, \chi_2)$ is a Steinberg pair and $L(s, \chi_1) L(s, \chi_2)$ otherwise ([BH06], Chapter 6, section 26; Godement and Jacquet, *Zeta functions of simple algebras*, Theorem 3.3).

Lean: `Langlands.LocalGL2.PSSubExists`, `Langlands.LocalGL2.PSSubUnique`, `Langlands.LocalGL2.PSSubRigid`, `Langlands.LocalGL2.PSSubSwap`, `Langlands.LocalGL2.NonSupercuspidalExhaustion`, `Langlands.LocalGL2.PSSubNotSupercuspidal`, `Langlands.LocalGL2.PSSubContragredient`, `Langlands.LocalGL2.PSSubLFactor`, `Langlands.LocalGL2.NonSupercuspidalInputs`

**Remark 3.10.15 (where the inputs are proved).** Inputs 1 to 4 are the content of Theorem 1.5.1 with the Jacquet modules of Theorem 1.3.11. The irreducible subrepresentation of $\chi_1 \times \chi_2$ is $\eta \circ \det$ with $\chi_1 = \eta |\cdot|^{-1/2}$ when $\chi_1 \chi_2^{-1} = |\cdot|^{-1}$, the Steinberg kernel $\eta \mathrm{St}$ with $\chi_1 = \eta |\cdot|^{1/2}$ when $\chi_1 \chi_2^{-1} = |\cdot|$, and the whole space otherwise. Its Jacquet module is $\chi_1 \otimes \chi_2$ alone in the reducible cases, and it contains both $\chi_1 \otimes \chi_2$ and $\chi_2 \otimes \chi_1$ otherwise, up to the normalization. By Frobenius reciprocity, Theorem 1.3.3, these are the pairs $(\psi_1, \psi_2)$ with $\pi$ in $\psi_1 \times \psi_2$, which is input 3. Inputs 5 and 6 are Jacquet's criterion, Theorem 1.4.3, and Frobenius reciprocity. Input 7 holds since $(\chi_1 \times \chi_2)^\vee \cong \chi_1^{-1} \times \chi_2^{-1}$, so $\pi^\vee$ is a quotient of $\chi_1^{-1} \times \chi_2^{-1}$, hence a subrepresentation of $\chi_2^{-1} \times \chi_1^{-1}$ by Theorem 1.5.1. Input 8 is the computation of the zeta integrals of the principal series in [BH06], Chapter 6. Inputs 1 to 7 are therefore theorems of this handbook. They are not yet theorems of the library, because the Smooth folder of the library builds its own model of the principal series, and the comparison with `Langlands.principalSeries` is not formalized.

For a pair of smooth characters put $\mathrm{par}(\chi_1, \chi_2) = [M(\varphi_{\chi_1}, \varphi_{\chi_2})]$. This is the parameter of Example 3.3.5: $r = \varphi_{\chi_1} \oplus \varphi_{\chi_2}$, with $N = E_{12}$ exactly when $(\chi_1, \chi_2)$ is a Steinberg pair, by Proposition 3.10.12. Let $\mathcal{A}^{\mathrm{ns}}$ be the set of classes of irreducible admissible representations of $G$ that are not supercuspidal, and let $\mathcal{G}^{\mathrm{ni}}$ be the set of classes of Weil-Deligne representations of dimension 2 that are not irreducible.

**Theorem 3.10.16 (the correspondence off the supercuspidal representations).** Assume the eight inputs of Definition 3.10.14. For $[\pi] \in \mathcal{A}^{\mathrm{ns}}$ choose $(\chi_1, \chi_2)$ with $\pi$ in $\chi_1 \times \chi_2$, and put $\mathrm{rec}^{\mathrm{ns}}[\pi] = \mathrm{par}(\chi_1, \chi_2)$. Then:
1. $\mathrm{rec}^{\mathrm{ns}}$ is well defined, and it is a bijection $\mathcal{A}^{\mathrm{ns}} \to \mathcal{G}^{\mathrm{ni}}$;
2. the central character of $\pi$ corresponds to $\det \mathrm{rec}^{\mathrm{ns}}[\pi]$ under $\mathrm{art}_K$;
3. $\mathrm{rec}^{\mathrm{ns}}[\pi \otimes (\chi \circ \det)] = \mathrm{rec}^{\mathrm{ns}}[\pi] \otimes \varphi_\chi$, and $\mathrm{rec}^{\mathrm{ns}}[\pi^\vee] = \mathrm{rec}^{\mathrm{ns}}[\pi]^\vee$;
4. $L(s, \pi) = L(s, \mathrm{rec}^{\mathrm{ns}}[\pi])$;
5. $\mathcal{A}^{\mathrm{ns}}$ is stable under twists and contragredients.

So input 6 of Definition 3.9.30 holds.

Lean: `Langlands.LocalGL2.psParam`, `Langlands.LocalGL2.psParam_notMem`, `Langlands.LocalGL2.psParam_eq_of_hasHom`, `Langlands.LocalGL2.nsMap`, `Langlands.LocalGL2.nsMap_eq`, `Langlands.LocalGL2.nsMap_injective`, `Langlands.LocalGL2.nsMap_surjective`, `Langlands.LocalGL2.nsEquiv`, `Langlands.LocalGL2.lFactor_of_mk_eq_psParam`, `Langlands.LocalGL2.nonSupercuspidalLLC_of_inputs`

*Proof.* A pair $(\chi_1, \chi_2)$ exists by input 5. Well defined: if $\pi$ is also in $\psi_1 \times \psi_2$, input 3 gives $(\psi_1, \psi_2) = (\chi_1, \chi_2)$, or the swap with no Steinberg pair. In the second case Theorem 3.10.9, case 2, and Proposition 3.10.12, part 2, give $\mathrm{par}(\psi_1, \psi_2) = \mathrm{par}(\chi_1, \chi_2)$. An isomorphic $\pi'$ is in the same principal series. The value lies in $\mathcal{G}^{\mathrm{ni}}$ by Lemma 3.10.3.

Injective: let $\pi$ be in $\chi_1 \times \chi_2$, $\pi'$ in $\chi'_1 \times \chi'_2$, with equal parameters. By Theorem 3.10.9, $(\varphi_{\chi'_1}, \varphi_{\chi'_2})$ is $(\varphi_{\chi_1}, \varphi_{\chi_2})$ or its swap with no Steinberg pair. By Proposition 3.10.12, part 4, the same holds for the characters of $K^\times$. In the first case input 2 gives $\pi \cong \pi'$. In the second case input 4 puts $\pi$ in $\chi_2 \times \chi_1 = \chi'_1 \times \chi'_2$, and input 2 gives $\pi \cong \pi'$.

Surjective: let $\rho$ be not irreducible. By Theorem 3.10.8, $\rho \cong M(\varphi_1, \varphi_2)$. By Proposition 3.10.12, part 4, $\varphi_i = \varphi_{\chi_i}$ for smooth characters $\chi_i$. Input 1 gives $\pi$ in $\chi_1 \times \chi_2$, and input 6 says that $[\pi] \in \mathcal{A}^{\mathrm{ns}}$. Then $\mathrm{rec}^{\mathrm{ns}}[\pi] = [\rho]$.

Part 2. By Proposition 3.10.13 the central character is $\chi_1 \chi_2$, and by Proposition 3.10.10, part 3, $\det M = \varphi_{\chi_1} \varphi_{\chi_2} = \varphi_{\chi_1 \chi_2}$. Part 3. By Proposition 3.10.13, part 3, $\pi \otimes (\chi \circ \det)$ is in $\chi_1 \chi \times \chi_2 \chi$, so its parameter is $M(\varphi_{\chi_1} \varphi_\chi, \varphi_{\chi_2} \varphi_\chi)$, which is the twist by Proposition 3.10.10, part 2. By input 7, $\pi^\vee$ is in $\chi_2^{-1} \times \chi_1^{-1}$, and Proposition 3.10.10, part 1, identifies $M(\varphi_{\chi_2}^{-1}, \varphi_{\chi_1}^{-1})$ with the dual. Part 4 is input 8 with Propositions 3.10.11 and 3.10.12, part 3. Part 5. The twist is in $\chi_1 \chi \times \chi_2 \chi$ and the contragredient is in $\chi_2^{-1} \times \chi_1^{-1}$, so input 6 applies to both. $\square$

**Example 3.10.17 (an unramified principal series).** Let $\chi_1, \chi_2$ be unramified with $\chi_i(\varpi) = a_i$, and assume that $a_1 a_2^{-1} \ne q^{\pm 1}$. Then $\pi = \chi_1 \times \chi_2$ is irreducible by Theorem 1.5.1, and neither $(\chi_1, \chi_2)$ nor $(\chi_2, \chi_1)$ is a Steinberg pair, since $|\varpi| = q^{-1}$. The parameter is $M(\varphi_{\chi_1}, \varphi_{\chi_2})$ with $N = 0$, where $\varphi_{\chi_i}$ is unramified with $\varphi_{\chi_i}(\Phi) = a_i$. The representation is also in $\chi_2 \times \chi_1$, and Theorem 3.10.9, case 2, says that the parameter does not see the order. The central character is $\chi_1 \chi_2$, unramified with value $a_1 a_2$ at $\varpi$, and $\det r(\Phi) = a_1 a_2$. The $L$-factor is $(1 - a_1 q^{-s})^{-1} (1 - a_2 q^{-s})^{-1}$. The contragredient is in $\chi_2^{-1} \times \chi_1^{-1}$, with parameter $\mathrm{diag}(a_2^{-1}, a_1^{-1})$ at $\Phi$.

**Example 3.10.18 (the Steinberg representation).** Let $\chi_1 = |\cdot|^{1/2}$ and $\chi_2 = |\cdot|^{-1/2}$. Then $(\chi_1, \chi_2)$ is a Steinberg pair, and by Theorem 1.5.1, part 3, with $\eta = 1$, the irreducible subrepresentation of $\chi_1 \times \chi_2$ is $\mathrm{St}$. Its parameter is $M(|\cdot|^{1/2}, |\cdot|^{-1/2})$ with $N = E_{12}$. At $\Phi$ we get $r(\Phi) = \mathrm{diag}(q^{-1/2}, q^{1/2})$, and $\ker N = \mathbb{C} e_1$. So $L(s, \mathrm{St}) = (1 - q^{-1/2 - s})^{-1}$, by input 8 and Proposition 3.10.11. The central character is trivial, and $\det r = 1$. By input 7, $\mathrm{St}^\vee$ is in $\chi_2^{-1} \times \chi_1^{-1} = |\cdot|^{1/2} \times |\cdot|^{-1/2}$, so $\mathrm{St}^\vee \cong \mathrm{St}$ by input 2. On the Galois side, Proposition 3.10.10, part 1, gives the dual $M(|\cdot|^{1/2}, |\cdot|^{-1/2})$ again.

**Example 3.10.19 (the trivial representation).** Let $\chi_1 = |\cdot|^{-1/2}$ and $\chi_2 = |\cdot|^{1/2}$. Then $\chi_1 \chi_2^{-1} = |\cdot|^{-1}$, and by Theorem 1.5.1, part 2, with $\eta = 1$, the irreducible subrepresentation of $\chi_1 \times \chi_2$ is the trivial representation $1_G$. The pair $(\chi_1, \chi_2)$ is not a Steinberg pair, so the parameter is $M(|\cdot|^{-1/2}, |\cdot|^{1/2})$ with $N = 0$. At $\Phi$, $r(\Phi) = \mathrm{diag}(q^{1/2}, q^{-1/2})$, and
$$L(s, 1_G) = (1 - q^{1/2 - s})^{-1} (1 - q^{-1/2 - s})^{-1}.$$
The pair $(\chi_2, \chi_1)$ is a Steinberg pair, so input 3 says that $1_G$ is not in $\chi_2 \times \chi_1$. This is correct: the subrepresentation of $\chi_2 \times \chi_1$ is $\mathrm{St}$. The parameters of $1_G$ and $\mathrm{St}$ have the same semisimple part $|\cdot|^{1/2} \oplus |\cdot|^{-1/2}$, and Theorem 3.10.9 separates them by $N$.

### Tame data and the five inputs

We turn to input 2. Section 3.9 builds the type $\Lambda$ on $J_\alpha$ for a minimal pair of odd level $n$ and an abstract quadratic field $E$. The statement of input 2 uses pairs $(L/K, \xi)$ with $L$ inside $\bar K$, as in `Langlands.LocalGL2.TamePair`. The datum below works with $L$ directly, so there is no comparison of fields. We first need a lemma on compact induction and the minimality of $\alpha$ in the unramified case.

**Lemma 3.10.20 (twists of compact induction).** Let $J$ be an open subgroup of a locally profinite group $H$, $\Lambda$ a character of $J$ with open kernel, and $\theta$ a character of $H$ with open kernel. Put $\Lambda'(j) = \Lambda(j) \theta(j)$.
1. $(\mathrm{c\text{-}Ind}_J^H \Lambda) \otimes \theta \cong \mathrm{c\text{-}Ind}_J^H \Lambda'$, by $f \mapsto \theta f$.
2. Each $h \in H$ that intertwines $\Lambda'$ intertwines $\Lambda$.

Lean: `Langlands.cIndMulChar`, `Langlands.iso_twist_cInd`, `Langlands.Intertwines.of_mul_char`, `Langlands.isOpen_ker_of_mul_char`

*Proof.* Part 1. For $f$ in $\mathrm{c\text{-}Ind}\, \Lambda$ we have $(\theta f)(j x) = \theta(j) \theta(x) \Lambda(j) f(x) = \Lambda'(j) (\theta f)(x)$. The support does not change, and $\theta f$ is smooth because $\theta$ is trivial on an open subgroup. The group acts on the twist by $h \cdot f = \theta(h) \rho(h) f$, and $\theta(x) \theta(h) f(x h) = (\theta f)(x h)$, so the map is $H$-equivariant. Its inverse is $f \mapsto \theta^{-1} f$. Part 2. On $J \cap h^{-1} J h$ we have $\theta(h x h^{-1}) = \theta(x)$, since $\theta$ takes values in a commutative group. So the intertwining condition $\Lambda'(h x h^{-1}) = \Lambda'(x)$ becomes $\Lambda(h x h^{-1}) = \Lambda(x)$. $\square$

**Proposition 3.10.21 (minimal elements for unramified pairs).** Let $p \ne 2$, let $\psi$ have level one, and let $(E/K, \xi)$ be an unramified minimal pair of level $n \ge 1$. Let $\alpha \in E$ have $v_E(\alpha) = -n$ and $\xi(1 + y) = \psi(\mathrm{tr}_{E/K}(\alpha y))$ for $y \in \mathfrak{p}_E^m$. Then $\alpha$ is minimal of level $n$ in the sense of Definition 3.9.9.

Lean: `Langlands.LocalGL2.IsMinimal.isMinimalElt_unram`

*Proof.* Suppose that $\alpha - a \in \mathfrak{p}_E^{1-n}$ with $a \in K$. Then $v_K(a) = -n$, since $E/K$ is unramified. Let $u = 1 + y \in U_E^n$. Since $n \ge m$, the hypothesis applies to $y$, and
$$\xi(u) = \psi(\mathrm{tr}_{E/K}(a y)) \, \psi(\mathrm{tr}_{E/K}((\alpha - a) y)) = \psi(a \, \mathrm{tr}_{E/K}(y)).$$
The second factor is $1$, because $(\alpha - a) y \in \mathfrak{p}_E$, so its trace is in $\mathfrak{p}_K$, where $\psi$ is trivial. Now $N_{E/K}(u) - 1 = \mathrm{tr}_{E/K}(y) + N_{E/K}(y)$, and $a N_{E/K}(y) \in \mathfrak{p}_K^{-n + 2n} \subseteq \mathfrak{p}_K$. So $\xi(u) = \psi(a (N_{E/K}(u) - 1))$ on $U_E^n$. Then $\xi|_{U_E^n}$ factors through $N_{E/K}$, and the pair is not minimal. This is a contradiction. $\square$

This is part 2 of Proposition 3.9.10 in full. It removes the gap of Remark 3.9.25, part 2. So for odd $n$ the chain of Remark 3.9.25 now runs in the library for unramified pairs as well as for ramified pairs.

**Definition 3.10.22 (tame datum).** Let $(L/K, \xi)$ be a pair with $L \subseteq \bar K$. A *tame datum* $D$ for $(L/K, \xi)$ consists of:
1. a character $\psi$ of $K$ of level one;
2. a chain order $\mathfrak{A}$ and a basis $v$ of $L$ over $K$ adapted to $\mathfrak{A}$, as in Definition 3.9.6;
3. a minimal character $\xi_0$ of $L^\times$ of odd level $n$;
4. an element $\alpha \in L$ that is minimal of level $n$, with matrix in $\mathfrak{P}_{\mathfrak{A}}^{-n}$;
5. the cuspidal type $\Lambda_0$ of $J_\alpha$ for $(\alpha, \xi_0)$, as in Definition 3.9.12;
6. a smooth character $\chi$ of $K^\times$ with $\xi = \xi_0 \chi_L$.

The character of $D$ is $\Lambda = \Lambda_0 \cdot (\chi \circ \det)$ on $J_\alpha$, and the representation of $D$ is $\pi_D = \mathrm{c\text{-}Ind}_{J_\alpha}^G \Lambda$.

Lean: `Langlands.LocalGL2.TameDatum`, `Langlands.LocalGL2.TameDatum.J`, `Langlands.LocalGL2.TameDatum.rep`

**Proposition 3.10.23 (the representation of a datum).** Let $D$ be a tame datum for $(L/K, \xi)$.
1. Each element of $G$ that intertwines $\Lambda$ lies in $J_\alpha$, and $\pi_D$ is irreducible.
2. $\pi_D$ has central character $\xi|_{K^\times}$.
3. For a smooth character $\chi'$ of $K^\times$, the same data with $\chi \chi'$ in place of $\chi$ form a tame datum $D \otimes \chi'$ for $(L/K, \xi \chi'_L)$, and $\pi_D \otimes (\chi' \circ \det) \cong \pi_{D \otimes \chi'}$.

Lean: `Langlands.LocalGL2.TameDatum.mem_of_intertwines`, `Langlands.LocalGL2.TameDatum.isIrreducible`, `Langlands.LocalGL2.TameDatum.det_scalarGL_eq_normUnits`, `Langlands.LocalGL2.TameDatum.hasCentralChar`, `Langlands.LocalGL2.TameDatum.twist`, `Langlands.LocalGL2.TameDatum.iso_twist`

*Proof.* Part 1. Let $g$ intertwine $\Lambda$. By Lemma 3.10.20, part 2, with $\theta = \chi \circ \det$, $g$ intertwines $\Lambda_0$. By Corollary 3.9.23, which applies because $\alpha$ is minimal, $g \in J_\alpha$. By Proposition 3.9.17, $J_\alpha$ is open and compact modulo the centre, so Theorem 3.9.16 gives the irreducibility. Part 2. Let $c \in K^\times$. The scalar matrix $c$ lies in $L^\times \subseteq J_\alpha$, and $\Lambda_0(c) = \xi_0(c)$ by the definition of a type. Since $\det(c \cdot 1) = c^2 = N_{L/K}(c)$,
$$\Lambda(c) = \xi_0(c) \, \chi(N_{L/K}(c)) = \xi_0(c) \chi_L(c) = \xi(c).$$
A central element of $J_\alpha$ acts on $\mathrm{c\text{-}Ind}\, \Lambda$ by $\Lambda$. Part 3. The conditions 1 to 5 do not involve $\chi$, and $\xi \chi'_L = \xi_0 (\chi \chi')_L$. The new character is $\Lambda \cdot (\chi' \circ \det)$, and Lemma 3.10.20, part 1, with $\theta = \chi' \circ \det$ gives the isomorphism. $\square$

**Definition 3.10.24 (covered pairs).** A pair $P$ is *covered* if it is isomorphic to a pair $Q$ that has a tame datum.

Lean: `Langlands.LocalGL2.Covered`, `Langlands.LocalGL2.covered_of_datum`, `Langlands.LocalGL2.Covered.of_iso`

**Proposition 3.10.25 (which pairs are covered).** Let $p \ne 2$.
1. If $\xi_0$ is a minimal character of $L^\times$ of odd level, then $(L/K, \xi_0)$ has a tame datum with $\chi = 1$.
2. If $\xi = \xi_0 \chi_L$ with $\xi_0$ minimal of odd level and $\chi$ smooth, then $(L/K, \xi)$ is covered.
3. If $L/K$ is ramified, then $(L/K, \xi)$ is covered.
4. If $P$ is not covered, then no twist of $P$ is covered.

Lean: `Langlands.LocalGL2.nonempty_tameDatum_of_isMinimal`, `Langlands.LocalGL2.covered_of_isMinimal`, `Langlands.LocalGL2.covered_of_isTotallyRamifiedExt`, `Langlands.LocalGL2.covered_of_odd_level`, `Langlands.LocalGL2.not_covered_twist`, `Langlands.LocalGL2.TamePair.twist_twist_inv`

*Proof.* A character $\psi$ of level one exists by Proposition 3.10.35 below. Part 1. Proposition 3.9.8 gives $\alpha$ with $v_L(\alpha) = -n$ and the compatibility with $\xi_0$. In the ramified case Proposition 3.9.10, part 1, gives the minimality of $\alpha$ and the simple stratum for the basis $(\varpi_L, 1)$. In the unramified case Proposition 3.10.21 gives the minimality, and Proposition 3.9.10, part 2, the stratum for the basis $(1, u)$. Proposition 3.9.13 gives the type, since $n$ is odd. Part 2. Twist the datum of part 1 by $\chi$, as in Proposition 3.10.23, part 3. Part 3. By Proposition 3.3.14, part 1, $\xi = \xi_0 \chi_L$ with $\xi_0$ minimal, and by Proposition 3.3.13, part 3, the level of $\xi_0$ is odd. Apply part 2. Part 4. If $P \otimes \chi$ were isomorphic to a pair $Q$ with a datum $D$, then $P \cong (P \otimes \chi) \otimes \chi^{-1} \cong Q \otimes \chi^{-1}$, and $D \otimes \chi^{-1}$ is a datum for $Q \otimes \chi^{-1}$. $\square$

So the pairs that are not covered are unramified, and their minimal part has level zero or even level. These are the pairs of Example 1.4.9 (depth zero) and of Remark 3.9.14 (the Heisenberg representation of dimension $q$).

**Example 3.10.26 (covered and uncovered pairs over $\mathbb{Q}_p$).** Let $p$ be odd and $K = \mathbb{Q}_p$.
1. Let $L = \mathbb{Q}_p(\sqrt{p})$, and let $\xi$ be any admissible character of $L^\times$. By Proposition 3.10.25, part 3, the pair is covered. For the pair of level one of Example 3.9.27, the datum has $\chi = 1$, $\xi_0 = \xi$, and $\pi_D$ is the representation of that example, with trivial central character.
2. Let $L$ be the unramified quadratic extension, and let $\xi$ be trivial on $U_L^1$ with $\xi|_{\mathcal{O}_L^\times}$ given by a character $\theta$ of $k_2^\times$ with $\theta \ne \theta^p$. The pair is minimal of level zero by Proposition 3.3.13, part 1. If $\xi \chi_L^{-1}$ is minimal, then its level is $0$ by Proposition 3.3.14, part 2, so it is not odd. So the pair is not covered, and its representation is the depth zero representation of Example 1.4.9, which the library does not build.

**Definition 3.10.27 (the five inputs on cuspidal types).** Let $p \ne 2$. The inputs for $K$ are the following.
1. `CIndSupercuspidal`. Let $J$ be an open subgroup of $G$ that is compact modulo the centre, and $\Lambda$ a character of $J$ with open kernel whose intertwining lies in $J$. Then $\mathrm{c\text{-}Ind}_J^G \Lambda$ is admissible and supercuspidal ([BH06], 11.4, with 10.1 for admissibility).
2. `TypeRepInjective`. If $\pi_D \cong \pi_{D'}$ for data $D$ of $P$ and $D'$ of $Q$, then $P \cong Q$ ([BH06], 15.6 and 20.2).
3. `TypeRepIndependent`. If $P \cong Q$, then $\pi_D \cong \pi_{D'}$ for any data $D$ of $P$ and $D'$ of $Q$. So $\pi_D$ does not depend on $\psi$, $\alpha$, the basis, or the factorization $\xi = \xi_0 \chi_L$ ([BH06], section 19, with 15.6).
4. `TypeRepContragredient`. If $\pi \cong \pi_D$ for a datum of $(L/K, \xi)$ and $\pi' \cong \pi^\vee$, then $\pi' \cong \pi_{D'}$ for a datum $D'$ of $(L/K, \xi^{-1})$ ([BH06], 19.4).
5. `UncoveredParametrization`. There is a map $\sigma$ from the pairs to the classes of irreducible admissible representations with three properties. On the pairs that are not covered, $\sigma(P)$ is supercuspidal with central character $\xi|_{K^\times}$ and with the twist and contragredient rules of input 2 of Definition 3.9.30. Also, $\sigma(P) = \sigma(Q)$ if and only if $P \cong Q$, and no $\sigma(P)$ contains a $\pi_D$. Last, each supercuspidal $\pi$ is a $\pi_D$ or lies in some $\sigma(P)$ with $P$ not covered ([BH06], 15.5, 15.8, 19.1, 19.3 and 20.2).

Lean: `Langlands.LocalGL2.CIndSupercuspidal`, `Langlands.LocalGL2.TypeRepInjective`, `Langlands.LocalGL2.TypeRepIndependent`, `Langlands.LocalGL2.TypeRepContragredient`, `Langlands.LocalGL2.UncoveredConstruction`, `Langlands.LocalGL2.UncoveredInjective`, `Langlands.LocalGL2.Exhaustion`, `Langlands.LocalGL2.UncoveredParametrization`, `Langlands.LocalGL2.TameTypeInputs`

In [BH06] the map $\sigma$ is $P \mapsto \pi_\xi$ of Definition 3.9.28.

**Theorem 3.10.28 (the tame parametrization from types).** Let $p \ne 2$ and assume the five inputs of Definition 3.10.27. Put $\pi_P = [\pi_D]$ for a chosen datum $D$ of a chosen pair isomorphic to $P$ if $P$ is covered, and $\pi_P = \sigma(P)$ otherwise. Then $P \mapsto \pi_P$ has the properties of input 2 of Definition 3.9.30. So input 2 holds.

Lean: `Langlands.LocalGL2.typeParam`, `Langlands.LocalGL2.typeParam_of_covered`, `Langlands.LocalGL2.typeParam_of_not_covered`, `Langlands.LocalGL2.mk_eq_typeParam_iff`, `Langlands.LocalGL2.not_covered_inv`, `Langlands.LocalGL2.TameDatum.isAdmissible_and_isSupercuspidal`, `Langlands.LocalGL2.TameDatum.irrRep`, `Langlands.LocalGL2.tameParametrizationGL2_of_inputs`, `Langlands.LocalGL2.gl2OddInputs_of_tameTypeInputs`

*Proof.* For a covered $P$, input 3 shows that $\pi \in \pi_P$ if and only if $\pi \cong \pi_D$ for some datum $D$ of some pair isomorphic to $P$. We call this the key property. By input 1 and Proposition 3.10.23, part 1, each $\pi_D$ is irreducible, admissible and supercuspidal, so $\pi_P$ is a class of supercuspidal representations. For $P$ not covered this is input 5.

Onto the supercuspidal classes: by input 5, a supercuspidal $\pi$ is a $\pi_D$, and then $[\pi] = \pi_Q$ for the pair $Q$ of $D$ by the key property, or $[\pi] = \sigma(P) = \pi_P$ with $P$ not covered.

Injectivity: there are four cases. If $P$ and $Q$ are covered and $\pi_P = \pi_Q$, the key property and input 2 give $P \cong Q$. If $P$ is covered and $Q$ is not, then $\pi_P = \pi_Q$ would put a $\pi_D$ into $\sigma(Q)$, which input 5 excludes, and $P \cong Q$ is impossible, since covered pairs are closed under isomorphism. The case with $P$ not covered and $Q$ covered is the same. If neither is covered, this is input 5. Conversely $P \cong Q$ gives $\pi_P = \pi_Q$ by the key property.

Central characters: for covered $P$, Proposition 3.10.23, part 2, for the pair $Q \cong P$ of the datum, since the restriction of $\xi$ to $K^\times$ is invariant under isomorphism of pairs. Otherwise, input 5. Twists: for covered $P$, a representative is $\pi_D$, and Proposition 3.10.23, part 3, gives $\pi_D \otimes (\chi \circ \det) \cong \pi_{D \otimes \chi}$, a datum of $Q \otimes \chi \cong P \otimes \chi$. For $P$ not covered, $P \otimes \chi$ is not covered by Proposition 3.10.25, part 4, and input 5 applies. Contragredients: for covered $P$, input 4 gives a datum of $Q^{-1} \cong P^{-1}$, where $P^{-1} = (L/K, \xi^{-1})$. If $P$ is not covered, neither is $P^{-1}$: a datum for a pair isomorphic to $P^{-1}$ would give, by input 4 applied to $\pi_D$ and its contragredient, a datum for a pair isomorphic to $P$. Then input 5 applies. $\square$

Input 1 is used only for admissibility and supercuspidality. The next subsection proves its supercuspidal half and reduces its admissible half to one statement.

### Supercuspidality of compact induction

Let $H$ be a locally profinite group, $Z$ a closed subgroup of its centre, $J$ an open subgroup that contains $Z$ and is compact modulo $Z$, and $\Lambda$ a character of $J$ with open kernel. Let $V = \mathrm{c\text{-}Ind}_J^H \Lambda$ as in Definition 1.4.7. Let $f_0 \in V$ be the function with support $J$ and $f_0(j) = \Lambda(j)$, and let $\epsilon : V \to \mathbb{C}$ be the evaluation $f \mapsto f(1)$.

**Lemma 3.10.29 (the basic vector).**
1. $\rho(j) f_0 = \Lambda(j) f_0$ for $j \in J$.
2. The linear form $\epsilon$ is smooth, and its matrix coefficient with $f_0$ is $g \mapsto \epsilon(\rho(g) f_0) = f_0(g)$. Its support is $J$.
3. Each $f \in V$ is a finite sum $\sum_s c_s \rho(s^{-1}) f_0$.

Lean: `Langlands.cIndBasic`, `Langlands.ρ_cIndBasic_of_mem`, `Langlands.toFunLin_one_mem_smoothVectors`, `Langlands.cIndEvalOne`, `Langlands.coeff_cIndBasic_cIndEvalOne`, `Langlands.eq_sum_translate_cIndBasic`

*Proof.* Part 1. $(\rho(j) f_0)(x) = f_0(x j)$, and $x j \in J$ if and only if $x \in J$. On $J$ the value is $\Lambda(x j) = \Lambda(x) \Lambda(j)$. Part 2. The form $\epsilon$ is fixed by the open subgroup $\ker \Lambda$, since $(\rho(k) f)(1) = f(k) = \Lambda(k) f(1)$ for $k \in J$. The formula for the coefficient is the definition of $\rho$. Part 3. If $f$ has support $\bigcup_s J s$, a finite union, then $f = \sum_s f(s) \, \rho(s^{-1}) f_0$, since $\rho(s^{-1}) f_0$ has support $J s$ and value $\Lambda(j)$ at $j s$. $\square$

**Lemma 3.10.30 (compact modulo the centre).** There is a compact set $C_J \subseteq H$ with $J \subseteq C_J Z$.

Lean: `Langlands.exists_isCompact_of_isCompactModCenter`, `Langlands.le_of_forall_intertwines`

*Proof.* Let $K_0$ be a compact open subgroup of $H$. The image of $J$ in $H / Z$ is compact, and the images of the cosets $x K_0$ cover it by open sets. Choose finitely many, $x_1 K_0, \dots, x_k K_0$. Then $J \subseteq C_J Z$ with $C_J = \{x_1, \dots, x_k\} K_0$, which is compact. $\square$

For a compact open subgroup $K'$ and $h \in H$, say that $h$ is *admissible for $K'$* if $\Lambda(j) = 1$ for each $j \in J \cap h K' h^{-1}$.

**Lemma 3.10.31 (fixed vectors and double cosets).** Let $K'$ be a compact open subgroup of $H$.
1. If $h$ is admissible for $K'$, there is a unique $f_h \in V^{K'}$ with support $J h K'$ and $f_h(h) = 1$.
2. If $V^{K'}$ has finite dimension, there is a finite set $T \subseteq H$ such that each $h$ admissible for $K'$ lies in $J t K'$ for some $t \in T$.

Lean: `Langlands.TrivialOnConj`, `Langlands.dcFun`, `Langlands.dcFun_eq`, `Langlands.dcFun_of_not_mem`, `Langlands.dcVec`, `Langlands.dcVec_mem_fixedVectors`, `Langlands.exists_finset_of_finiteDimensional`

*Proof.* Part 1. Put $f_h(j h k) = \Lambda(j)$ for $j \in J$, $k \in K'$, and $f_h = 0$ off $J h K'$. This is well defined: if $j h k = j' h k'$, then $j'^{-1} j = h k' k^{-1} h^{-1} \in J \cap h K' h^{-1}$, so $\Lambda(j) = \Lambda(j')$. The function is left $(J, \Lambda)$-equivariant and right $K'$-invariant. Its support $J h K'$ is a finite union of cosets $J x$, because $K'$ is compact and $J$ is open. Uniqueness is clear. Part 2. The vectors $f_h$ for distinct double cosets have disjoint supports, so they are linearly independent. So there are at most $\dim V^{K'}$ distinct double cosets $J h K'$ with $h$ admissible. Let $T$ be a set of representatives. $\square$

**Theorem 3.10.32 (admissible compact inductions are supercuspidal).** Assume that each open subgroup of $H$ contains a compact open subgroup. If $V = \mathrm{c\text{-}Ind}_J^H \Lambda$ is admissible, then for each $v \in V$ and each smooth linear form $l$ on $V$ there is a compact set $C$ with $l(\rho(g) v) \ne 0 \Rightarrow g \in C Z$. In particular, for $H = G$ and $Z = K^\times$, $V$ is supercuspidal in the sense of Remark 1.4.4.

Lean: `Langlands.apply_ρ_of_inv_mem_vecStabilizer`, `Langlands.trivialOnConj_of_ne_zero`, `Langlands.isSupercuspidal_cInd_of_isAdmissible`, `Langlands.LocalGL2.isOpen_maxCompact`, `Langlands.LocalGL2.exists_isCompact_isOpen_le`, `Langlands.LocalGL2.isSupercuspidal_cInd_of_isAdmissible`

*Proof.* Let $K'$ be a compact open subgroup that fixes $l$. Such a subgroup exists, since the stabilizer of $l$ is open. Take $T$ as in Lemma 3.10.31, part 2, which applies because $V$ is admissible, and $C_J$ as in Lemma 3.10.30.

First let $v = f_0$, and suppose that $l(\rho(g) f_0) \ne 0$. Let $j \in J$ with $k = g j g^{-1} \in K'$. Then by Lemma 3.10.29, part 1,
$$l(\rho(g) f_0) = l(\rho(k) \rho(g) f_0) = l(\rho(g) \rho(j) f_0) = \Lambda(j) \, l(\rho(g) f_0).$$
So $\Lambda(j) = 1$. The elements $j$ in question are those of $J \cap g^{-1} K' g$, so $g^{-1}$ is admissible for $K'$. By Lemma 3.10.31, $g^{-1} = j t k$ with $j \in J$, $t \in T$, $k \in K'$. Then $g = k^{-1} t^{-1} j^{-1}$, and $j^{-1} \in C_J Z$. So
$$g \in C_1 Z, \qquad C_1 = K' \, T^{-1} \, C_J,$$
and $C_1$ is compact, as a product of compact sets.

For a general $v$, write $v = \sum_{s \in S} c_s \rho(s^{-1}) f_0$ by Lemma 3.10.29, part 3. If $l(\rho(g) v) \ne 0$, then $l(\rho(g s^{-1}) f_0) \ne 0$ for some $s \in S$. By the first step $g s^{-1} = c z$ with $c \in C_1$, $z \in Z$, and $g = c s z$ since $z$ is central. So $C = C_1 S$ works.

For $G$, the subgroup $GL_2(\mathcal{O}_K)$ is compact and open, and each open subgroup $U$ contains the compact open subgroup $U \cap GL_2(\mathcal{O}_K)$. So the hypothesis holds. $\square$

The proof does not use the intertwining condition.

**Definition 3.10.33 (compact coefficients give admissibility).** The statement `CompactCoeffAdmissible` for $K$ says: if $\pi$ is an irreducible smooth representation of $G$ with a matrix coefficient $g \mapsto l(\pi(g) v)$, for a smooth linear form $l$, that is not zero and has support in $C K^\times$ for a compact set $C$, then $\pi$ is admissible ([BH06], 10.1 and 10.2).

Lean: `Langlands.LocalGL2.CompactCoeffAdmissible`

**Proposition 3.10.34 (admissibility of compact induction).** Assume `CompactCoeffAdmissible` for $K$. Let $J$ be an open subgroup of $G$ that is compact modulo the centre, and $\Lambda$ a character of $J$ with open kernel whose intertwining lies in $J$. Then $\mathrm{c\text{-}Ind}_J^G \Lambda$ is admissible and supercuspidal. So input 1 of Definition 3.10.27 follows from `CompactCoeffAdmissible`.

Lean: `Langlands.LocalGL2.exists_compact_coeff_cInd`, `Langlands.LocalGL2.isAdmissible_cInd`, `Langlands.LocalGL2.cIndSupercuspidal_of_compactCoeffAdmissible`

*Proof.* The representation is irreducible by Theorem 3.9.16. By Lemma 3.10.29, part 2, the coefficient of $f_0$ and $\epsilon$ is $f_0$. It is not zero, since $f_0(1) = 1$, and its support $J$ lies in $C_J K^\times$ by Lemma 3.10.30. So `CompactCoeffAdmissible` gives admissibility, and Theorem 3.10.32 gives supercuspidality. $\square$

For $GL_n$, `CompactCoeffAdmissible` is a special case of the theorem of Jacquet and Bernstein that each irreducible smooth representation is admissible.

The datum of Definition 3.10.22 needs an additive character of level one. Section 3.9 assumes one. The library now proves that one exists.

**Proposition 3.10.35 (a character of level one).** There is a character $\psi$ of $K$ that is trivial on $\mathfrak{p}_K$ and not trivial on $\mathcal{O}_K$.

Lean: `Langlands.LocalGL1.ratCircleExp`, `Langlands.LocalGL1.ratCircleExp_eq_zero`, `Langlands.LocalGL1.exists_isConductor_neg_one`

*Proof.* The class of $1$ in the group $K / \mathfrak{p}_K$ is not zero, since $1 \notin \mathfrak{p}_K$. The group $\mathbb{Q} / \mathbb{Z}$ is divisible, so it is an injective $\mathbb{Z}$-module, and each nonzero element of an abelian group has a homomorphism to $\mathbb{Q} / \mathbb{Z}$ that does not vanish on it. So there is $c : K / \mathfrak{p}_K \to \mathbb{Q} / \mathbb{Z}$ with $c(1) \ne 0$. The map $e : \mathbb{Q} / \mathbb{Z} \to \mathbb{C}^\times$, $x \mapsto e^{2 \pi i x}$, is an injective homomorphism. Put $\psi(x) = e(c(x \bmod \mathfrak{p}_K))$. It is trivial on $\mathfrak{p}_K$, and $\psi(1) = e(c(1)) \ne 1$. Since it is trivial on the open subgroup $\mathfrak{p}_K$, it is locally constant, hence continuous. $\square$

**Example 3.10.36 (explicit characters of level one).**
1. For $K = \mathbb{Q}_p$, let $\{y\}_p \in \mathbb{Z}[1/p]$ be the $p$-adic fractional part, with $y - \{y\}_p \in \mathbb{Z}_p$. Then $\psi(x) = e^{2 \pi i \{x / p\}_p}$ is trivial on $p \mathbb{Z}_p$, and $\psi(1) = e^{2 \pi i / p} \ne 1$.
2. For $K = \mathbb{F}_q((t))$, let $\psi_0$ be a nontrivial character of $\mathbb{F}_q$, and put $\psi(\sum_i a_i t^i) = \psi_0(a_0)$. It is trivial on $t \mathbb{F}_q[[t]]$ and not trivial on $\mathbb{F}_q[[t]]$.

The character of conductor $\mathcal{O}_K$ of Section 3.3 is $x \mapsto \psi(\varpi x)$ for a character $\psi$ of level one.

### The finer reduction and what is open

**Theorem 3.10.37 (the finer reduction).** Let $p \ne 2$.
1. If inputs 1 to 5 of Definition 3.9.30 and the eight inputs of Definition 3.10.14 hold for $K$, then the six inputs of Definition 3.9.30 hold for $K$ and each local Artin map. If they hold for all such $K$, then `Langlands.LocalLanglandsGL2Odd` holds.
2. Input 2 of Definition 3.9.30 follows from `CompactCoeffAdmissible` and inputs 2 to 5 of Definition 3.10.27.

Lean: `Langlands.LocalGL2.GL2OddFineInputs`, `Langlands.LocalGL2.GL2OddFineInputs.toInputs`, `Langlands.localLanglandsGL2_odd_of_fineInputs`, `Langlands.LocalGL2.tameParametrizationGL2_of_inputs`, `Langlands.LocalGL2.cIndSupercuspidal_of_compactCoeffAdmissible`

*Proof.* Part 1. Theorem 3.10.16 gives input 6 from the eight inputs, and Theorem 3.9.33 gives the rest. Part 2. Proposition 3.10.34 gives input 1 of Definition 3.10.27, and Theorem 3.10.28 gives input 2 of Definition 3.9.30. $\square$

The library bundles part 1 as `GL2OddFineInputs`, whose field `tame` is still the whole of input 2. Part 2 is proved, but no structure in the library yet puts the inputs of Definition 3.10.27, with `CompactCoeffAdmissible` in place of `CIndSupercuspidal`, into `GL2OddFineInputs`.

**Remark 3.10.38 (what is still open for $GL_2$, $p \ne 2$).** This list replaces Remark 3.9.34. The open statements are the following.
1. `ArtinCompat`, input 1 of Definition 3.9.30: conjugation, norm and transfer for the local Artin maps of quadratic extensions ([Ser79], Chapter XI).
2. `GaloisTameParametrization`, input 3 of Definition 3.9.30: Proposition 3.3.7 and the fact that $\sigma(L, \xi)$ determines $L$.
3. `Rectifier`, input 4 of Definition 3.9.30: the characters $\Delta_\xi$ of [BH06], section 34, which need $\varepsilon$-factors and the Langlands constant.
4. `SupercuspidalLFactor`, input 5 of Definition 3.9.30: $L(s, \pi) = 1$ for supercuspidal $\pi$ (Godement and Jacquet).
5. The eight inputs of Definition 3.10.14. Inputs 1 to 7 are in Sections 1.3 to 1.5 of this handbook, but the library first needs a comparison of its two models of the principal series. Input 8 needs the zeta integrals of Godement and Jacquet for $GL_2$.
6. `CompactCoeffAdmissible`, Definition 3.10.33, or a direct finiteness statement for the double cosets $J h K'$.
7. `TypeRepInjective`, `TypeRepIndependent` and `TypeRepContragredient`, inputs 2 to 4 of Definition 3.10.27.
8. `UncoveredParametrization`, input 5 of Definition 3.10.27: the representations of the unramified pairs whose minimal part has level zero (Example 1.4.9) or even level (Remark 3.9.14), with their injectivity, and the exhaustion of [BH06], 15.5 and 15.8.
9. A structure that joins `GL2OddFineInputs` with the inputs of item 6 to 8, as in Theorem 3.10.37, part 2. This is a formal step with no new mathematics.
10. The case $p = 2$, the $\varepsilon$-factors, and the uniqueness of Theorem 3.3.1, which the Lean statement does not contain.

Input 6 of Definition 3.9.30 is no longer open as a whole. Only the eight statements of item 5 remain.
