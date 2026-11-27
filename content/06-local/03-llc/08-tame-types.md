---
title: Cuspidal types and the tame parametrization
nodes: []
sources: [BH06, Kut80]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Cuspidal types and the tame parametrization

Section 3.3 attaches to each admissible pair $(E/K, \xi)$ a supercuspidal representation $\pi_\xi$ of $G = GL_2(K)$, and it states the tame parametrization theorem, Theorem 3.3.19, without the construction. This section gives the construction for $p \ne 2$. Let $(E/K, \xi)$ be a minimal pair of level $n \ge 1$. We find an element $\alpha \in E$ that describes $\xi$ on $U_E^{[n/2]+1}$. With a basis of $E$ over $K$ we embed $E$ in $M_2(K)$. The basis fixes an order $\mathfrak{A}$ of $M_2(K)$ that $E^\times$ normalizes, and $(\mathfrak{A}, n, \alpha)$ is a simple stratum. The stratum gives a character $\psi_\alpha$ of an open compact subgroup, an open subgroup $J_\alpha$ of $G$ that is compact modulo the centre, and a character $\Lambda$ of $J_\alpha$ that is $\xi$ on $E^\times$ and $\psi_\alpha$ on the compact part. The main result is that the intertwining of $\Lambda$ is $J_\alpha$. Then $\pi_\xi = \mathrm{c\text{-}Ind}_{J_\alpha}^G \Lambda$ is irreducible and supercuspidal, by the criterion of Theorem 1.4.8. At the end we explain how the Lean project reduces the correspondence for $GL_2$, $p \ne 2$, to six published theorems, and we list what is still open.

The section follows [BH06], Chapter 4, sections 11 to 15, Chapter 5, sections 18 to 20, and Chapter 8, section 34. It uses the notation of Section 3.3: $K$ is the base field (the book writes $F$), $\varpi$ is a uniformizer, $k$ is the residue field with $q$ elements, $U_E^n$ is the unit filtration of $E$, and $\tau$ is the nontrivial automorphism of $E/K$. We write $[x]$ for the integer part of a real number $x$, and $v_K$, $v_E$ for the normalized valuations. Throughout, $\psi$ is an additive character of $K$ of *level one*: it is trivial on $\mathfrak{p}_K$ and not trivial on $\mathcal{O}_K$. This is the convention of [BH06], and it differs from the character of conductor $\mathcal{O}_K$ of Section 3.3. We write $\mathrm{tr}$ for the trace of $M_2(K)$ and $\mathrm{tr}_{E/K}$ for the trace of $E/K$. For a fixed $n \ge 1$ we put
$$m = [n/2] + 1, \qquad r = [(n+1)/2].$$
Then $m + r = n + 1$, $r \ge 1$, $m \le n$, and $1 - m = r - n$. If $n$ is odd, then $m = r$.

The Lean files of this section are `Langlands/Local/ChainOrders.lean`, `Langlands/Local/AdaptedUnramified.lean`, `Langlands/Local/CuspidalTypes.lean`, `Langlands/Local/CIndIrreducible.lean`, `Langlands/Local/JGroupCompact.lean`, `Langlands/Local/StrataIntertwining.lean`, `Langlands/Local/IntertwiningNormalizer.lean` and `Langlands/Local/GL2Reduction.lean`. They contain no `sorry`. Most declarations are in the namespace `Langlands.LocalGL2`. The files on compact induction put their declarations in `Langlands`. The files write $F$ for $K$. This section replaces item 8 of Remark 3.3.24: the stratum of a minimal pair, the pair $(J_\alpha, \Lambda)$ and the irreducibility of $\mathrm{c\text{-}Ind}\, \Lambda$ are now formalized, with the exceptions of Remark 3.9.25.

### Chain orders and their filtrations

The orders of $M_2(K)$ that we need are the stabilizers of the lattice chains in $K^2$. Up to conjugation there are two of them.

**Definition 3.9.1 (chain orders).** The *maximal order* is $\mathfrak{M} = M_2(\mathcal{O}_K)$. The *Iwahori order* is
$$\mathfrak{J} = \begin{pmatrix} \mathcal{O}_K & \mathcal{O}_K \\ \mathfrak{p}_K & \mathcal{O}_K \end{pmatrix}.$$
The *period* is $e_{\mathfrak{M}} = 1$ and $e_{\mathfrak{J}} = 2$, and the *weights* are $(w_1, w_2) = (0, 0)$ for $\mathfrak{M}$ and $(0, 1)$ for $\mathfrak{J}$. For a chain order $\mathfrak{A}$ of period $e$ and $n \in \mathbb{Z}$, let $b_n(i, j)$ be the least integer $t$ with $n \le e t + w_j - w_i$, and let $\mathfrak{P}^n_{\mathfrak{A}}$ be the set of matrices $X$ with $v_K(X_{ij}) \ge b_n(i, j)$ for all $i, j$. Put $U^0_{\mathfrak{A}} = \mathfrak{A}^\times$ and $U^n_{\mathfrak{A}} = 1 + \mathfrak{P}^n_{\mathfrak{A}}$ for $n \ge 1$. Let $\mathfrak{K}_{\mathfrak{A}}$ be the normalizer of $\mathfrak{A}$ in $G$. Let $\Pi_{\mathfrak{M}} = \varpi$ and
$$\Pi_{\mathfrak{J}} = \begin{pmatrix} 0 & 1 \\ \varpi & 0 \end{pmatrix}.$$

Lean: `Langlands.LocalGL2.ChainOrder`, `Langlands.LocalGL2.ChainOrder.e`, `Langlands.LocalGL2.radPow`, `Langlands.LocalGL2.order`, `Langlands.LocalGL2.unitsFilt`, `Langlands.LocalGL2.normalizer`, `Langlands.LocalGL2.piGL`

So $\mathfrak{P}^0_{\mathfrak{A}} = \mathfrak{A}$, and $\mathfrak{P}^n_{\mathfrak{M}} = \varpi^n \mathfrak{M}$. For $\mathfrak{J}$ the radical is
$$\mathfrak{P}_{\mathfrak{J}} = \mathfrak{P}^1_{\mathfrak{J}} = \begin{pmatrix} \mathfrak{p}_K & \mathcal{O}_K \\ \mathfrak{p}_K & \mathfrak{p}_K \end{pmatrix},$$
and the reduction of $\mathfrak{J}$ modulo $\mathfrak{p}_K$ is the algebra of upper triangular matrices over $k$. The bounds have two simple rules. They grow by one when $n$ grows by $e$, so $\mathfrak{P}^{n+e}_{\mathfrak{A}} = \varpi \mathfrak{P}^n_{\mathfrak{A}}$. And they satisfy the duality $b_{1-n}(j, i) = 1 - b_n(i, j)$, which Exercise 23 checks.

**Proposition 3.9.2 (first properties).** Let $\mathfrak{A}$ be a chain order and $\Pi = \Pi_{\mathfrak{A}}$.
1. $\mathfrak{P}^n_{\mathfrak{A}} = \Pi^n \mathfrak{A} = \mathfrak{A} \Pi^n$ for all $n \in \mathbb{Z}$, and $\mathfrak{P}^a_{\mathfrak{A}} \mathfrak{P}^b_{\mathfrak{A}} \subseteq \mathfrak{P}^{a+b}_{\mathfrak{A}}$.
2. The groups $U^n_{\mathfrak{A}}$ form a decreasing sequence of open compact subgroups of $G$, each normal in $\mathfrak{K}_{\mathfrak{A}}$, with trivial intersection.
3. $\mathfrak{K}_{\mathfrak{A}} = \Pi^{\mathbb{Z}} \mathfrak{A}^\times$, and $g \mathfrak{P}^n_{\mathfrak{A}} g^{-1} = \mathfrak{P}^n_{\mathfrak{A}}$ for $g \in \mathfrak{K}_{\mathfrak{A}}$.
4. (Trace duality.) Let $k \in \mathbb{Z}$ and $Y \in M_2(K)$. Then $\psi(\mathrm{tr}(Y X)) = 1$ for all $X \in \mathfrak{P}^k_{\mathfrak{A}}$ if and only if $Y \in \mathfrak{P}^{1-k}_{\mathfrak{A}}$.

Lean: `Langlands.LocalGL2.mem_radPow_iff_zpow_mul`, `Langlands.LocalGL2.mem_radPow_iff_mul_zpow`, `Langlands.LocalGL2.mul_mem_radPow`, `Langlands.LocalGL2.unitsFilt_anti`, `Langlands.LocalGL2.isOpen_unitsFilt`, `Langlands.LocalGL2.isCompact_unitsFilt`, `Langlands.LocalGL2.normal_unitsFilt`, `Langlands.LocalGL2.mem_normalizer_iff`, `Langlands.LocalGL2.mem_radPow_of_forall_psi_trace`

*Proof.* Part 1 is a computation of entries. For $\mathfrak{M}$ it is clear. For $\mathfrak{J}$, left multiplication by $\Pi$ moves the second row to the first and $\varpi$ times the first row to the second, and the bounds of $\mathfrak{P}^{n+1}_{\mathfrak{J}}$ are those of $\mathfrak{P}^n_{\mathfrak{J}}$ with the two rows exchanged and the new second row raised by one. The product rule follows: $\Pi^a \mathfrak{A} \Pi^b \mathfrak{A} = \Pi^{a+b} \mathfrak{A}$. For part 2, $U^n_{\mathfrak{A}}$ is a group for $n \ge 1$, since $(1 + X)(1 + Y) = 1 + X + Y + XY$ and $(1 + X)^{-1} = \sum_k (-X)^k$ converges, as $X^k \in \mathfrak{P}^{kn}_{\mathfrak{A}}$. It is open and compact, since $\mathfrak{P}^n_{\mathfrak{A}}$ is an open compact lattice. For part 3, part 1 shows that $\Pi$ normalizes $\mathfrak{A}$, so $\Pi^{\mathbb{Z}} \mathfrak{A}^\times \subseteq \mathfrak{K}_{\mathfrak{A}}$. Conversely, let $g \in \mathfrak{K}_{\mathfrak{A}}$ and let $k$ be the largest integer with $g \in \mathfrak{P}^k_{\mathfrak{A}}$. Then $h = \Pi^{-k} g$ lies in $\mathfrak{A} \smallsetminus \mathfrak{P}_{\mathfrak{A}}$ and normalizes $\mathfrak{A}$, so $h \mathfrak{A} = \mathfrak{A} h$ is a two-sided ideal of $\mathfrak{A}$ that is not in $\mathfrak{P}_{\mathfrak{A}}$. The two-sided ideals of $\mathfrak{A}$ are the $\mathfrak{P}^j_{\mathfrak{A}}$, so $h \mathfrak{A} = \mathfrak{A}$ and $h \in \mathfrak{A}^\times$. The Lean proof shows instead that $\det h$ is a unit. Conjugation by $g$ fixes $\mathfrak{A}$, hence each $\mathfrak{P}^n_{\mathfrak{A}} = \Pi^n \mathfrak{A}$, since $\Pi$ normalizes $\mathfrak{A}$. So $g$ normalizes $U^n_{\mathfrak{A}}$. For part 4, $\mathrm{tr}(Y X) = \sum_{i, j} Y_{ji} X_{ij}$. Take $X = c E_{ij}$, the matrix with the single entry $c$ at $(i, j)$, with $v_K(c) \ge b_k(i, j)$. Since $\psi$ has level one, $\psi(c Y_{ji}) = 1$ for all such $c$ if and only if $v_K(Y_{ji}) \ge 1 - b_k(i, j) = b_{1-k}(j, i)$. This gives one direction, and the same bound shows that $\mathrm{tr}(Y X) \in \mathfrak{p}_K$ when $Y \in \mathfrak{P}^{1-k}_{\mathfrak{A}}$ and $X \in \mathfrak{P}^k_{\mathfrak{A}}$. $\square$

### Strata and the character $\psi_\alpha$

**Definition 3.9.3 (stratum and $\psi_\alpha$).** A *stratum* is a triple $(\mathfrak{A}, n, \alpha)$ with $\mathfrak{A}$ a chain order, $n \ge 1$ and $\alpha \in \mathfrak{P}^{-n}_{\mathfrak{A}}$. Its character is
$$\psi_\alpha(x) = \psi(\mathrm{tr}(\alpha(x - 1))), \qquad x \in U^m_{\mathfrak{A}}, \quad m = [n/2] + 1.$$

Lean: `Langlands.LocalGL2.psiAlphaFun`, `Langlands.LocalGL2.psiAlpha`

**Lemma 3.9.4 (the character of a stratum).** Let $(\mathfrak{A}, n, \alpha)$ be a stratum.
1. $\psi_\alpha$ is a character of $U^m_{\mathfrak{A}}$, trivial on $U^{n+1}_{\mathfrak{A}}$.
2. It depends only on $\alpha$ modulo $\mathfrak{P}^{1-m}_{\mathfrak{A}} = \mathfrak{P}^{-[n/2]}_{\mathfrak{A}}$.
3. For $g \in G$ and $x \in U^m_{\mathfrak{A}}$ with $g x g^{-1} \in U^m_{\mathfrak{A}}$, $\psi_\alpha(g x g^{-1}) = \psi(\mathrm{tr}(g^{-1} \alpha g (x - 1)))$.

Lean: `Langlands.LocalGL2.psiAlpha`, `Langlands.LocalGL2.psiAlpha_eq_one`, `Langlands.LocalGL2.psiAlpha_congr`, `Langlands.LocalGL2.psiAlphaFun_conj_eq_conj`

*Proof.* Let $x = 1 + X$ and $y = 1 + Y$ with $X, Y \in \mathfrak{P}^m_{\mathfrak{A}}$. Then $xy - 1 = X + Y + XY$, and $\alpha X Y \in \mathfrak{P}^{2m - n}_{\mathfrak{A}} \subseteq \mathfrak{P}^1_{\mathfrak{A}}$ since $2m \ge n + 1$. By Proposition 3.9.2, part 4 with $k = 0$, the trace of an element of $\mathfrak{P}^1_{\mathfrak{A}}$ lies in $\mathfrak{p}_K$, where $\psi$ is trivial. So $\psi_\alpha(xy) = \psi_\alpha(x) \psi_\alpha(y)$. If $X \in \mathfrak{P}^{n+1}_{\mathfrak{A}}$, then $\alpha X \in \mathfrak{P}^1_{\mathfrak{A}}$ and $\psi_\alpha(x) = 1$. Part 2 is the same argument: if $\alpha' - \alpha \in \mathfrak{P}^{1-m}_{\mathfrak{A}}$, then $(\alpha' - \alpha) X \in \mathfrak{P}^1_{\mathfrak{A}}$. Part 3 holds since $\mathrm{tr}(\alpha g X g^{-1}) = \mathrm{tr}(g^{-1} \alpha g X)$. $\square$

**Definition 3.9.5 (simple stratum).** A stratum $(\mathfrak{A}, n, \alpha)$ is *simple* if $\alpha \notin \mathfrak{P}^{1-n}_{\mathfrak{A}}$, $n$ is prime to $e_{\mathfrak{A}}$, the algebra $E = K[\alpha]$ is a field of degree 2 over $K$, and $E^\times \subseteq \mathfrak{K}_{\mathfrak{A}}$.

Lean: `Langlands.LocalGL2.IsSimpleStratum`

The simple strata come from the quadratic extensions $E/K$ through suitable bases. A $K$-basis $(v_1, v_2)$ of $E$ gives an embedding $E \to M_2(K)$, $y \mapsto L_y$, where $L_y$ is the matrix of multiplication by $y$. We use the same letter for $y$ and $L_y$.

**Definition 3.9.6 (adapted basis).** A $K$-basis $(v_1, v_2)$ of $E$ is *adapted* to the chain order $\mathfrak{A}$ if $e(E|K) = e_{\mathfrak{A}}$, if $v_E(v_i) = s - w_i$ for some $s \in \mathbb{Z}$, and if it is orthogonal: $c_1 v_1 + c_2 v_2 \in \mathfrak{p}_E^N$ if and only if $c_1 v_1 \in \mathfrak{p}_E^N$ and $c_2 v_2 \in \mathfrak{p}_E^N$, for all $N$.

Lean: `Langlands.LocalGL2.IsAdapted`

**Proposition 3.9.7 (adapted bases).** Let $(v_1, v_2)$ be a basis of $E$ adapted to $\mathfrak{A}$.
1. $\mathfrak{P}^n_{\mathfrak{A}}$ is the set of $Y \in M_2(K)$ with $Y \mathfrak{p}_E^N \subseteq \mathfrak{p}_E^{N+n}$ for all $N$. In particular $\mathfrak{P}^n_{\mathfrak{A}} \cap E = \mathfrak{p}_E^n$, $U^n_{\mathfrak{A}} \cap E^\times = U^n_E$ and $E^\times \subseteq \mathfrak{K}_{\mathfrak{A}}$.
2. If $E/K$ is unramified, let $u \in \mathcal{O}_E^\times$ be a unit whose residue class is not in $k$. Then $(1, u)$ is adapted to $\mathfrak{M}$.
3. If $E/K$ is ramified with uniformizer $\varpi_E$, then $(\varpi_E, 1)$ is adapted to $\mathfrak{J}$, and $\varpi_E$ maps to an element of $\Pi_{\mathfrak{J}} \mathfrak{J}^\times$.
4. Let $\alpha \in E \smallsetminus K$ with $v_E(\alpha) = -n$, $n \ge 1$ and $n$ prime to $e_{\mathfrak{A}}$. Then $(\mathfrak{A}, n, \alpha)$ is a simple stratum.

Lean: `Langlands.LocalGL2.IsAdapted.mem_radPow_iff`, `Langlands.LocalGL2.IsAdapted.leftMulMatrix_mem_radPow_iff`, `Langlands.LocalGL2.IsAdapted.embGL_mem_unitsFilt_iff`, `Langlands.LocalGL2.IsAdapted.embGL_mem_normalizer`, `Langlands.LocalGL2.unramBasis`, `Langlands.LocalGL2.isAdapted_unramBasis`, `Langlands.LocalGL2.ramBasis`, `Langlands.LocalGL2.isAdapted_ramBasis`, `Langlands.LocalGL2.IsAdapted.isSimpleStratum`, `Langlands.LocalGL2.isSimpleStratum_ramBasis`

*Proof.* Part 1. Write $e = e_{\mathfrak{A}}$. By orthogonality, $\mathfrak{p}_E^N$ is the set of $c_1 v_1 + c_2 v_2$ with $e v_K(c_i) + s - w_i \ge N$ for both $i$. The image of the basis vector $v_j$ under $Y$ is $Y_{1j} v_1 + Y_{2j} v_2$. So $Y \mathfrak{p}_E^N \subseteq \mathfrak{p}_E^{N+n}$ for all $N$ if and only if $e v_K(Y_{ij}) - w_i + w_j \ge n$ for all $i, j$, which is the definition of $\mathfrak{P}^n_{\mathfrak{A}}$. For $y \in E$ with $v_E(y) = n$, multiplication by $y$ maps $\mathfrak{p}_E^N$ onto $\mathfrak{p}_E^{N+n}$, so $y \in \mathfrak{P}^n_{\mathfrak{A}} \smallsetminus \mathfrak{P}^{n+1}_{\mathfrak{A}}$. The other claims follow, and $y \mathfrak{A} y^{-1} = \mathfrak{A}$ because $y$ and $y^{-1}$ shift the chain $\{\mathfrak{p}_E^N\}$ by opposite amounts. Part 2. Here $e = 1$ and both vectors are units. For $c_1, c_2 \in K$ with $v_K(c_1) = v_K(c_2) = t$, the element $\varpi^{-t}(c_1 + c_2 u)$ is a unit, since the residue of $u$ is not in $k$. This gives orthogonality. Part 3. Here $v_E(\varpi_E) = 1 = s - 0$ and $v_E(1) = 0 = s - 1$ with $s = 1$. Orthogonality holds since $v_E(c_1 \varpi_E)$ is odd and $v_E(c_2)$ is even. The matrix of $\varpi_E$ is $\left(\begin{smallmatrix} 0 & 1 \\ \varpi_0 & 0 \end{smallmatrix}\right)$ with $\varpi_0 = \varpi_E^2 \in K$, a uniformizer of $K$, and it lies in $\Pi_{\mathfrak{J}} \mathfrak{J}^\times$. Part 4. Since $\alpha \notin K$, $K[\alpha] = E$, which is a field of degree 2. By part 1, $\alpha \in \mathfrak{P}^{-n}_{\mathfrak{A}} \smallsetminus \mathfrak{P}^{1-n}_{\mathfrak{A}}$ and $E^\times \subseteq \mathfrak{K}_{\mathfrak{A}}$. $\square$

### The element of a minimal pair

**Proposition 3.9.8 (the element $\alpha$ of an admissible pair).** Let $p \ne 2$, and let $(E/K, \xi)$ be an admissible pair of level $n \ge 1$. There is $\alpha \in E$ with $v_E(\alpha) = -n$ and
$$\xi(1 + y) = \psi(\mathrm{tr}_{E/K}(\alpha y)) \qquad \text{for all } y \in \mathfrak{p}_E^{m}.$$
The class of $\alpha$ modulo $\mathfrak{p}_E^{1-m}$ is unique.

Lean: `Langlands.LocalGL2.exists_eq_psi_trace`, `Langlands.LocalGL2.IsAdmissible.exists_alpha`; the uniqueness is not formalized

*Proof.* Since $2m \ge n + 1$, the map $y \mapsto \xi(1 + y)$ is a character of the additive group $\mathfrak{p}_E^m / \mathfrak{p}_E^{n+1}$, by the argument of Lemma 3.9.4. The pairing $(z, y) \mapsto \psi(\mathrm{tr}_{E/K}(z y))$ identifies $\mathfrak{p}_E^{-n} / \mathfrak{p}_E^{1-m}$ with the dual of $\mathfrak{p}_E^m / \mathfrak{p}_E^{n+1}$. Indeed, since $E/K$ is tamely ramified, $\mathrm{tr}_{E/K}(\mathfrak{p}_E^j) = \mathfrak{p}_K^{\lceil j/e \rceil}$ with $e = e(E|K)$, so $z \mathfrak{p}_E^{n+1}$ has trace in $\mathfrak{p}_K$ if and only if $z \in \mathfrak{p}_E^{-n}$. The map $z \mapsto \psi(\mathrm{tr}_{E/K}(z \,\cdot\,))$ is then injective on the finite group $\mathfrak{p}_E^{-n}/\mathfrak{p}_E^{1-m}$, and the two finite groups have the same order. This gives $\alpha \in \mathfrak{p}_E^{-n}$, unique modulo $\mathfrak{p}_E^{1-m}$. If $\alpha \in \mathfrak{p}_E^{1-n}$, then $\xi$ is trivial on $1 + \mathfrak{p}_E^n = U_E^n$, which contradicts the level. So $v_E(\alpha) = -n$. $\square$

**Definition 3.9.9 (minimal element).** An element $\alpha \in E$ is *minimal of level $n$* over $K$ if $\alpha \in \mathfrak{p}_E^{-n}$ and $\alpha \notin K + \mathfrak{p}_E^{1-n}$.

Lean: `Langlands.LocalGL2.IsMinimalElt`

**Proposition 3.9.10 (minimal pairs give minimal elements).** Let $p \ne 2$, let $(E/K, \xi)$ be a minimal pair of level $n \ge 1$, and let $\alpha$ be as in Proposition 3.9.8.
1. If $E/K$ is ramified, then $n$ is odd, $\alpha$ is minimal of level $n$, and $(\mathfrak{J}, n, \alpha)$ is a simple stratum for the basis $(\varpi_E, 1)$.
2. If $E/K$ is unramified, then $\alpha$ is minimal of level $n$, and $(\mathfrak{M}, n, \alpha)$ is a simple stratum for the basis $(1, u)$.
3. Let $\alpha \in E$ be minimal of level $n$. For each $a \in K$, $v_E(\alpha - a) \le -n$, with equality when $a \in \mathfrak{p}_E^{-n}$.

Lean: part 1, `Langlands.LocalGL2.IsMinimal.exists_isSimpleStratum_ram` and `Langlands.LocalGL2.isMinimalElt_of_ramified`; part 2, the stratum `Langlands.LocalGL2.IsMinimal.exists_isSimpleStratum_unram` and $\alpha \notin K$, `Langlands.LocalGL2.IsMinimal.alpha_not_mem`; the minimality of $\alpha$ in part 2 is not formalized; part 3, `Langlands.LocalGL2.IsMinimalElt.sub_ne_zero_and`

*Proof.* Part 1. By Proposition 3.3.13, $n$ is odd. Each $a \in K^\times$ has even valuation $v_E(a)$, so $v_E(\alpha - a) = \min(-n, v_E(a)) \le -n$, and $\alpha \notin K + \mathfrak{p}_E^{1-n}$. In particular $\alpha \notin K$, and Proposition 3.9.7, parts 3 and 4, give the stratum, since $n$ is prime to $e_{\mathfrak{J}} = 2$. Part 2. Suppose that $\alpha = a + \beta$ with $a \in K$ and $\beta \in \mathfrak{p}_E^{1-n}$. For $y \in \mathfrak{p}_E^n$ we have $\beta y \in \mathfrak{p}_E$, so $\mathrm{tr}_{E/K}(\beta y) \in \mathfrak{p}_K$ and $\xi(1 + y) = \psi(a \, \mathrm{tr}_{E/K}(y))$. Also $v_K(a) \ge -n$, since $v_E(a) \ge \min(v_E(\alpha), v_E(\beta)) \ge -n$. Now $N_{E/K}(1 + y) = 1 + \mathrm{tr}_{E/K}(y) + N_{E/K}(y)$, and $a N_{E/K}(y) \in \mathfrak{p}_K^{n}$. So $\xi(u) = \psi(a(N_{E/K}(u) - 1))$ for $u \in U_E^n$. The right side is a character of $U_K^n$, by the argument of Lemma 3.9.4, composed with the norm. So $\xi|_{U_E^n}$ factors through $N_{E/K}$, and the pair is not minimal. This contradiction shows that $\alpha$ is minimal. In particular $\alpha \notin K$, and Proposition 3.9.7, parts 2 and 4, gives the stratum. Part 3. If $v_E(\alpha - a) > -n$, then $\alpha \in a + \mathfrak{p}_E^{1-n}$. If $a \in \mathfrak{p}_E^{-n}$, then also $\alpha - a \in \mathfrak{p}_E^{-n}$. $\square$

The Lean file proves part 2 only in the case $\beta = 0$: if $\alpha \in K$, then $\xi$ factors through the norm on $U_E^n$. The general case is the same computation, but it is not in the library yet.

**Lemma 3.9.11 (orthogonality of $1$ and $\alpha$).** Let $\alpha$ be minimal of level $n$ with $v_E(\alpha) = -n$. For $c_1, c_2 \in K$, $v_E(c_1 + c_2 \alpha) = \min(v_E(c_1), v_E(c_2) - n)$.

Lean: `Langlands.LocalGL2.IsMinimalElt.smul_mem_ordBall`

*Proof.* If the two valuations differ, this is the strict triangle inequality. Suppose that $v_E(c_1) = v_E(c_2) - n$, so $c_2 \ne 0$. Then $c_1 + c_2 \alpha = c_2(\alpha + c_1 / c_2)$ and $c_1 / c_2 \in \mathfrak{p}_E^{-n}$. By Proposition 3.9.10, part 3, $v_E(\alpha + c_1/c_2) = -n$. $\square$

### Cuspidal types

From now on, $(v_1, v_2)$ is a basis of $E$ adapted to $\mathfrak{A}$, and $\alpha \in E$ is minimal of level $n \ge 1$ with $v_E(\alpha) = -n$ and $n$ prime to $e_{\mathfrak{A}}$. By Propositions 3.9.7 and 3.9.10, $(\mathfrak{A}, n, \alpha)$ is a simple stratum.

**Definition 3.9.12 (the group $J_\alpha$ and the cuspidal types).** Let $J_\alpha = E^\times U^r_{\mathfrak{A}}$ with $r = [(n+1)/2]$. Let $\xi$ be a smooth character of $E^\times$. The pair $(\alpha, \xi)$ is *compatible* if $\xi(y) = \psi(\mathrm{tr}_{E/K}(\alpha(y - 1)))$ for $y \in U_E^m$. A *cuspidal type* for $(\alpha, \xi)$ is a character $\Lambda$ of $J_\alpha$ with $\Lambda|_{E^\times} = \xi$ and $\Lambda|_{U^m_{\mathfrak{A}}} = \psi_\alpha$.

Lean: `Langlands.LocalGL2.jGroup`, `Langlands.LocalGL2.IsCompatible`, `Langlands.LocalGL2.IsTypeChar`, `Langlands.LocalGL2.cuspTypes`

The set $J_\alpha$ is a group, since $E^\times \subseteq \mathfrak{K}_{\mathfrak{A}}$ normalizes $U^r_{\mathfrak{A}}$. It is open, it lies in $\mathfrak{K}_{\mathfrak{A}}$, and it contains the scalars $K^\times$. For $y \in E^\times$, the matrix $L_{\alpha(y-1)}$ has trace $\mathrm{tr}_{E/K}(\alpha(y - 1))$, so the compatibility says that $\xi$ and $\psi_\alpha$ agree on $E^\times \cap U^m_{\mathfrak{A}} = U_E^m$. A pair $(\alpha, \xi)$ is compatible exactly when $\alpha$ is the element of $\xi$ given by Proposition 3.9.8.

**Proposition 3.9.13 (existence and uniqueness of the type).** Let $n$ be odd. There is a cuspidal type for $(\alpha, \xi)$ if and only if $(\alpha, \xi)$ is compatible, and then it is unique. It is
$$\Lambda(y x) = \xi(y) \psi_\alpha(x), \qquad y \in E^\times, \ x \in U^m_{\mathfrak{A}}.$$

Lean: `Langlands.LocalGL2.existsUnique_mem_cuspTypes_iff`, `Langlands.LocalGL2.isCompatible_of_mem_cuspTypes`, `Langlands.LocalGL2.psiAlphaUnits_conj`, `Langlands.LocalGL2.psiAlpha_embGL_eq`

*Proof.* For odd $n$, $r = m$, so $J_\alpha = E^\times U^m_{\mathfrak{A}}$. A type restricts to $\xi$ and to $\psi_\alpha$, so these agree on $E^\times \cap U^m_{\mathfrak{A}} = U_E^m$, which is the compatibility. Each element of $J_\alpha$ is a product $y x$, so the type is unique. Conversely, let $(\alpha, \xi)$ be compatible. The formula is well defined: if $y x = y' x'$, then $y'^{-1} y = x' x^{-1} \in U_E^m$, and $\xi(y'^{-1} y) = \psi_\alpha(x' x^{-1})$. For $y \in E^\times$ and $x \in U^m_{\mathfrak{A}}$, Lemma 3.9.4, part 3, gives $\psi_\alpha(y^{-1} x y) = \psi(\mathrm{tr}(y \alpha y^{-1}(x - 1))) = \psi_\alpha(x)$, since $y$ and $\alpha$ commute. Then
$$\Lambda(y x \cdot y' x') = \Lambda(y y' \cdot (y'^{-1} x y') x') = \xi(y) \xi(y') \psi_\alpha(x) \psi_\alpha(x'),$$
so $\Lambda$ is a character. $\square$

**Remark 3.9.14 (even level).** Let $n = 2l$ be even. Then $\mathfrak{A} = \mathfrak{M}$ and $E/K$ is unramified, since $n$ is prime to $e_{\mathfrak{A}}$. Now $r = l < m = l + 1$, and the group $J_\alpha = E^\times U^l_{\mathfrak{M}}$ is larger than $H = E^\times U^{l+1}_{\mathfrak{M}}$. The formula of Proposition 3.9.13 defines a character $\theta$ of $H$, but no character of $J_\alpha$ extends it. The reason is the commutator form $(x, y) \mapsto \theta([x, y])$ on $U^l_{\mathfrak{M}}$, which is not trivial by Exercise 24. [BH06], Chapter 4, section 15, replaces $\Lambda$ by an irreducible representation of $J_\alpha$ of dimension $q$. It contains $\theta$, and it is built from the unique irreducible representation of $U_E^1 U^l_{\mathfrak{M}}$ that contains $\theta$ on $U_E^1 U^{l+1}_{\mathfrak{M}}$, a Heisenberg representation for a quotient of order $q^2$. The Lean definition `Langlands.LocalGL2.cuspTypes` asks for a character, so for even $n$ it is empty, and the even case is open in the library.

### Compact induction and the irreducibility criterion

In this subsection $G$ is any topological group in which the open subgroups form a basis of neighbourhoods of $1$. Let $J$ be an open subgroup and $\Lambda$ a character of $J$ with open kernel. The space $\mathrm{c\text{-}Ind}_J^G \Lambda$ of Definition 1.4.7 consists of the functions $f : G \to \mathbb{C}$ with $f(j g) = \Lambda(j) f(g)$ for $j \in J$, that are invariant on the right under some open subgroup, and whose support lies in finitely many cosets $J s$. The group acts by $(\pi(g) f)(x) = f(x g)$. An element $g \in G$ *intertwines* $\Lambda$ if $\Lambda(g x g^{-1}) = \Lambda(x)$ for all $x \in J$ with $g x g^{-1} \in J$. For a character this agrees with the definition before Theorem 1.4.8. Let $\varphi_0$ be the function that is $\Lambda$ on $J$ and $0$ outside $J$. It lies in $\mathrm{c\text{-}Ind}_J^G \Lambda$, and $\pi(j) \varphi_0 = \Lambda(j) \varphi_0$ for $j \in J$.

In the Lean library the representation is `Langlands.SmoothRep.cInd`, its space is `Langlands.cIndSpace`, the vector $\varphi_0$ is `Langlands.cIndBasic`, and the intertwining is `Langlands.Intertwines`.

**Lemma 3.9.15 (bi-equivariant functions, [BH06] 11.1).** Let $\varphi : G \to \mathbb{C}$ satisfy $\varphi(j g j') = \Lambda(j) \varphi(g) \Lambda(j')$ for $j, j' \in J$ and $g \in G$. If $\varphi(g) \ne 0$, then $g$ intertwines $\Lambda$. If the intertwining of $\Lambda$ is $J$, then $\varphi = \varphi(1) \varphi_0$.

Lean: `Langlands.IsBiEquivariant`, `Langlands.IsBiEquivariant.intertwines`, `Langlands.IsBiEquivariant.eq_smul_cIndBasicFun`

*Proof.* Let $x \in J$ with $g x g^{-1} \in J$. Then $\varphi(g) \Lambda(x) = \varphi(g x) = \varphi((g x g^{-1}) g) = \Lambda(g x g^{-1}) \varphi(g)$. If $\varphi(g) \ne 0$, then $\Lambda(g x g^{-1}) = \Lambda(x)$. So $\varphi$ vanishes outside the intertwining. If that is $J$, then $\varphi(j) = \Lambda(j) \varphi(1)$ on $J$ and $\varphi = 0$ outside $J$. $\square$

We say that $J$ is *compact modulo* a subgroup $Z$ of the centre of $G$ if $(Z \cap J) U$ has finite index in $J$ for each open subgroup $U$ of $J$. If $J$ is open and $J / Z$ is compact, this holds, since the image of $U$ in $J/Z$ is open. In the Lean library this is `Langlands.IsCompactModCenter`.

**Theorem 3.9.16 (the irreducibility criterion, [BH06] 11.4).** Let $J$ be an open subgroup of $G$ and $\Lambda$ a character of $J$ with open kernel. Let $Z$ be a subgroup of the centre of $G$ such that $J$ is compact modulo $Z$. If each element of $G$ that intertwines $\Lambda$ lies in $J$, then $\mathrm{c\text{-}Ind}_J^G \Lambda$ is irreducible.

Lean: `Langlands.isIrreducible_cInd`, with the steps `Langlands.exists_isotypic_of_ne_zero`, `Langlands.eq_smul_cIndBasic_of_isotypic`, `Langlands.eq_sum_translate_cIndBasic` and `Langlands.span_translate_cIndBasic`

Theorem 1.4.8 proves this, for a representation $\Lambda$ of any finite dimension, with the semisimplicity of $\pi|_J$. The proof here is for a character and needs no semisimplicity. It is the proof of the Lean library.

*Proof.* Put $\pi = \mathrm{c\text{-}Ind}_J^G \Lambda$. It is not zero, since $\varphi_0 \ne 0$. Let $W \ne 0$ be a $G$-stable subspace.

Step 1: $W$ contains a vector $\varphi \ne 0$ with $\pi(j) \varphi = \Lambda(j) \varphi$ for all $j \in J$. Choose $f \in W$ and $g \in G$ with $f(g) \ne 0$, and replace $f$ by $\pi(g) f$, so that $f(1) \ne 0$. Let $U$ be the intersection of $\ker \Lambda$ with an open subgroup that fixes $f$. It is an open subgroup of $J$. For $z \in Z \cap J$, $(\pi(z) f)(x) = f(x z) = f(z x) = \Lambda(z) f(x)$. So the vector $\Lambda(j)^{-1} \pi(j) f$ depends only on the coset $j (Z \cap J) U$. These cosets are finite in number, and we put
$$\varphi = \sum_{j \in J / (Z \cap J) U} \Lambda(j)^{-1} \pi(j) f \in W.$$
A change of the summation variable gives $\pi(j') \varphi = \Lambda(j') \varphi$ for $j' \in J$. And $\varphi(1) = \sum_j \Lambda(j)^{-1} f(j) = [J : (Z \cap J) U] \, f(1) \ne 0$.

Step 2: $\varphi_0 \in W$. The function $\varphi$ of step 1 satisfies $\varphi(j x j') = \Lambda(j) \varphi(x) \Lambda(j')$, by the definition of the induced space and by step 1. By Lemma 3.9.15, $\varphi = \varphi(1) \varphi_0$, so $\varphi_0 \in W$.

Step 3: $\varphi_0$ generates $\pi$. Let $f \in \pi$, with support in the distinct cosets $J s_1, \dots, J s_k$. The function $\pi(s_i^{-1}) \varphi_0$ is supported on $J s_i$, with value $\Lambda(j)$ at $j s_i$. Since $f(j s_i) = \Lambda(j) f(s_i)$,
$$f = \sum_{i=1}^k f(s_i) \, \pi(s_i^{-1}) \varphi_0.$$
So $W = \pi$. $\square$

**Proposition 3.9.17 ($J_\alpha$ is compact modulo the centre).** Let $(v_1, v_2)$ be adapted to $\mathfrak{A}$ and $j \ge 0$. The group $J = E^\times U^j_{\mathfrak{A}}$ is open and compact modulo $K^\times$. The subgroup $K^\times (U^0_{\mathfrak{A}} \cap J)$ has index at most $e(E|K)$ in $J$.

Lean: `Langlands.LocalGL2.isOpen_jGroup`, `Langlands.LocalGL2.finiteIndex_jGroup`, `Langlands.LocalGL2.isCompactModCenter_jGroup`, `Langlands.isCompactModCenter_of_isCompact`

*Proof.* $J$ contains the open group $U^j_{\mathfrak{A}}$, so it is open. Let $e = e(E|K)$ and let $\varpi_E$ be a uniformizer of $E$. Then $E^\times = \varpi_E^{\mathbb{Z}} \mathcal{O}_E^\times$ and $\varpi_E^e \in \varpi \mathcal{O}_E^\times$. By Proposition 3.9.7, $\mathcal{O}_E^\times \subseteq U^0_{\mathfrak{A}}$. So each element of $J$ lies in $\varpi_E^t K^\times (U^0_{\mathfrak{A}} \cap J)$ for some $0 \le t < e$, which gives the index. The group $C = U^0_{\mathfrak{A}} \cap J$ is compact, since $J$ is open, hence closed, and $U^0_{\mathfrak{A}}$ is compact. Let $U$ be an open subgroup of $J$. Then $U \cap C$ has finite index in the compact group $C$, so $K^\times U$ has finite index in $K^\times C$, and hence in $J$. $\square$

### The intertwining of $\psi_\alpha$ and of $\Lambda$

This subsection computes the intertwining. We keep the adapted basis and the minimal element $\alpha$ of level $n$. Let $a_\alpha(X) = \alpha X - X \alpha$ for $X \in M_2(K)$. Its kernel is the centralizer of $\alpha$, which is $E$, since $K[\alpha] = E$ is a maximal commutative subalgebra of $M_2(K)$.

**Proposition 3.9.18 (the exact sequence, [BH06] 13.4).** For each $j \in \mathbb{Z}$ and $X \in M_2(K)$, $a_\alpha(X) \in \mathfrak{P}^j_{\mathfrak{A}}$ if and only if $X \in E + \mathfrak{P}^{j+n}_{\mathfrak{A}}$.

Lean: `Langlands.LocalGL2.adjointMap`, `Langlands.LocalGL2.adjointMap_eq_zero_iff`, `Langlands.LocalGL2.IsAdapted.adjointMap_mem_radPow_iff`

*Proof.* If $X = y + X'$ with $y \in E$ and $X' \in \mathfrak{P}^{j+n}_{\mathfrak{A}}$, then $a_\alpha(X) = a_\alpha(X') \in \mathfrak{P}^j_{\mathfrak{A}}$, since $\alpha \in \mathfrak{P}^{-n}_{\mathfrak{A}}$. Conversely, let $a_\alpha(X) \in \mathfrak{P}^j_{\mathfrak{A}}$. View $X$ as a $K$-linear map $E \to E$, and put $y = X(1) \in E$ and $X' = X - y$. Then $X'(1) = 0$ and $a_\alpha(X') = a_\alpha(X)$. Evaluate at $1$: $a_\alpha(X)(1) = \alpha X'(1) - X'(\alpha) = -X'(\alpha)$. By Proposition 3.9.7, part 1, it suffices to show $X'(\mathfrak{p}_E^N) \subseteq \mathfrak{p}_E^{N + j + n}$. Let $x = c_1 + c_2 \alpha \in \mathfrak{p}_E^N$ with $c_1, c_2 \in K$. By Lemma 3.9.11, $v_E(c_2) \ge N + n$. Then $X'(x) = c_2 X'(\alpha) = -c_2 \, a_\alpha(X)(1)$, and $a_\alpha(X)(1) \in \mathfrak{p}_E^j$ since $1 \in \mathfrak{p}_E^0$. So $v_E(X'(x)) \ge N + n + j$. $\square$

**Lemma 3.9.19 (the conjugation criterion).** Let $g \in \mathfrak{K}_{\mathfrak{A}}$ and $s \ge 1$. Then $g \in E^\times U^s_{\mathfrak{A}}$ if and only if $g^{-1} \alpha g - \alpha \in \mathfrak{P}^{s-n}_{\mathfrak{A}}$.

Lean: `Langlands.LocalGL2.IsAdapted.mem_jGroup_iff_conj_sub_mem`

*Proof.* Let $g = y x$ with $y \in E^\times$ and $x = 1 + X \in U^s_{\mathfrak{A}}$. Then $g^{-1} \alpha g - \alpha = x^{-1} \alpha x - \alpha = x^{-1} a_\alpha(X)$, which lies in $\mathfrak{P}^{s-n}_{\mathfrak{A}}$. Conversely, write $g = \Pi^k u$ with $u \in \mathfrak{A}^\times$, by Proposition 3.9.2. Then $a_\alpha(g) = g(g^{-1} \alpha g - \alpha) \in \mathfrak{P}^{k + s - n}_{\mathfrak{A}}$. By Proposition 3.9.18, $g = y + X$ with $y \in E$ and $X \in \mathfrak{P}^{k+s}_{\mathfrak{A}}$. So $y = g(1 - g^{-1} X)$ with $g^{-1} X \in \mathfrak{P}^s_{\mathfrak{A}}$. The factor $1 - g^{-1} X$ lies in $U^s_{\mathfrak{A}}$, so $y$ is invertible, $y \in E^\times$, and $g = y (1 - g^{-1} X)^{-1} \in E^\times U^s_{\mathfrak{A}}$. $\square$

**Proposition 3.9.20 (the intertwining in $\mathfrak{K}_{\mathfrak{A}}$).** An element $g \in \mathfrak{K}_{\mathfrak{A}}$ intertwines $\psi_\alpha$ if and only if $g \in J_\alpha$.

Lean: `Langlands.LocalGL2.intertwines_psiAlpha_iff`

*Proof.* Since $g$ normalizes $U^m_{\mathfrak{A}}$, it intertwines $\psi_\alpha$ if and only if $\psi_\alpha(g x g^{-1}) = \psi_\alpha(x)$ for all $x \in U^m_{\mathfrak{A}}$. By Lemma 3.9.4, part 3, this says $\psi(\mathrm{tr}((g^{-1} \alpha g - \alpha) X)) = 1$ for all $X \in \mathfrak{P}^m_{\mathfrak{A}}$. By trace duality this holds if and only if $g^{-1} \alpha g - \alpha \in \mathfrak{P}^{1-m}_{\mathfrak{A}} = \mathfrak{P}^{r - n}_{\mathfrak{A}}$. Lemma 3.9.19 with $s = r \ge 1$ gives the claim. $\square$

Outside $\mathfrak{K}_{\mathfrak{A}}$ we use a double coset decomposition. Write $D(d) = \mathrm{diag}(1, d)$.

**Lemma 3.9.21 (the decomposition $G = \mathfrak{K}_{\mathfrak{A}} D \mathfrak{K}_{\mathfrak{A}}$).** Each $g \in G$ has the form $g = a \, D(d) \, b$ with $a, b \in \mathfrak{K}_{\mathfrak{A}}$ and $d \in K^\times$ with $v_K(d) \ge 0$.

Lean: `Langlands.LocalGL2.exists_normalizer_mul_diag_mul`, `Langlands.LocalGL2.diagGL`

*Proof.* Let $k$ be the largest integer with $g \in \mathfrak{P}^k_{\mathfrak{A}}$ and put $h = \Pi^{-k} g$. Then $h \in \mathfrak{A} \smallsetminus \mathfrak{P}_{\mathfrak{A}}$, so some entry $h_{ij}$ has valuation below the bound of $\mathfrak{P}_{\mathfrak{A}}$ at $(i, j)$. We move it to the place $(1, 1)$. For $\mathfrak{M}$ that entry is a unit, and we multiply $h$ on the left and on the right by permutation matrices in $GL_2(\mathcal{O}_K)$. For $\mathfrak{J}$ the bounds of $\mathfrak{J}$ and of $\mathfrak{P}_{\mathfrak{J}}$ differ only on the diagonal, so $h_{11}$ or $h_{22}$ is a unit. If $h_{11}$ is not a unit, we replace $h$ by $\Pi h \Pi^{-1}$, which exchanges the two diagonal entries. So we may assume that $x = h_{11}$ is a unit. Write $h = \left(\begin{smallmatrix} x & y \\ z & w \end{smallmatrix}\right)$. Then
$$h = \begin{pmatrix} 1 & 0 \\ z/x & 1 \end{pmatrix} \begin{pmatrix} x & 0 \\ 0 & 1 \end{pmatrix} \begin{pmatrix} 1 & 0 \\ 0 & d \end{pmatrix} \begin{pmatrix} 1 & y/x \\ 0 & 1 \end{pmatrix}, \qquad d = \det(h)/x.$$
The first, second and fourth factors lie in $\mathfrak{A}^\times$, since $z \in \mathfrak{p}_K$ for $\mathfrak{A} = \mathfrak{J}$. And $v_K(d) = v_K(\det h) \ge 0$ since $h \in \mathfrak{A}$. $\square$

For $\mathfrak{M}$ this is a weak form of the Cartan decomposition, and for $\mathfrak{J}$ of the Iwahori decomposition. Exercise 27 shows that the double cosets of the $D(\varpi^t)$, $t \ge 0$, are distinct.

**Theorem 3.9.22 (the intertwining of $\psi_\alpha$, [BH06] 15.1).** Let $(v_1, v_2)$ be adapted to $\mathfrak{A}$ and let $\alpha \in E$ be minimal of level $n \ge 1$. An element $g \in G$ intertwines the character $\psi_\alpha$ of $U^m_{\mathfrak{A}}$ if and only if $g \in J_\alpha$.

Lean: `Langlands.LocalGL2.intertwines_psiAlpha_iff_mem_jGroup`, with the steps `Langlands.LocalGL2.psi_trace_eq_one_of_intertwines`, `Langlands.LocalGL2.false_of_forall_psi_trace` and `Langlands.LocalGL2.mem_normalizer_of_intertwines_psiAlpha`

*Proof.* Elements of $J_\alpha$ intertwine $\psi_\alpha$ by Proposition 3.9.20. Let $g$ intertwine $\psi_\alpha$. By Proposition 3.9.20 it suffices to show $g \in \mathfrak{K}_{\mathfrak{A}}$. Write $g = a D b$ with $D = D(d)$ as in Lemma 3.9.21. If $v_K(d) = 0$, then $D \in \mathfrak{A}^\times$ and $g \in \mathfrak{K}_{\mathfrak{A}}$. So assume $v_K(d) \ge 1$, and we derive a contradiction.

Put $\gamma = a^{-1} \alpha a$ and $\beta = b \alpha b^{-1}$. Both lie in $\mathfrak{P}^{-n}_{\mathfrak{A}}$, by Proposition 3.9.2, part 3. Let $X \in \mathfrak{P}^m_{\mathfrak{A}}$ with $D X D^{-1} \in \mathfrak{P}^m_{\mathfrak{A}}$. Put $x = b^{-1}(1 + X) b \in U^m_{\mathfrak{A}}$. Then $g x g^{-1} = a (1 + D X D^{-1}) a^{-1} \in U^m_{\mathfrak{A}}$. The intertwining gives $\psi_\alpha(g x g^{-1}) = \psi_\alpha(x)$, that is,
$$\psi(\mathrm{tr}(D^{-1} \gamma D X)) = \psi(\mathrm{tr}(\beta X)), \quad \text{so} \quad \psi(\mathrm{tr}(Y X)) = 1, \qquad Y = D^{-1} \gamma D - \beta.$$
Take $X = c E_{12}$. Then $D X D^{-1} = c d^{-1} E_{12}$, so both conditions on $X$ hold when $v_K(c) \ge b_m(1, 2) + v_K(d)$. And $\mathrm{tr}(Y X) = c Y_{21}$. Since $\psi$ has level one, $v_K(Y_{21}) \ge 1 - b_m(1, 2) - v_K(d)$. Now $Y_{21} = d^{-1} \gamma_{21} - \beta_{21}$, so $\gamma_{21} = d Y_{21} + d \beta_{21}$. The first term has valuation at least $1 - b_m(1, 2) = b_{1-m}(2, 1) \ge b_{1-n}(2, 1)$, by the duality of the bounds and since $m \le n$. The second term has valuation at least $1 + b_{-n}(2, 1) = b_{e - n}(2, 1) \ge b_{1-n}(2, 1)$. So $v_K(\gamma_{21}) \ge b_{1-n}(2, 1)$.

Now we use the minimality of $\alpha$. The scalar $\gamma_{11}$ satisfies $v_K(\gamma_{11}) \ge b_{-n}(1, 1) = b_{-n}(2, 2)$, so $\gamma_{11} \in \mathfrak{P}^{-n}_{\mathfrak{A}} \cap E = \mathfrak{p}_E^{-n}$. By Proposition 3.9.10, part 3, $v_E(\alpha - \gamma_{11}) = -n$, so $(\alpha - \gamma_{11})^{-1} \in \mathfrak{p}_E^n \subseteq \mathfrak{P}^n_{\mathfrak{A}}$. Put $\delta = \gamma - \gamma_{11} = a^{-1}(\alpha - \gamma_{11}) a$. Then $\delta^{-1} = a^{-1} (\alpha - \gamma_{11})^{-1} a \in \mathfrak{P}^n_{\mathfrak{A}}$, $\delta_{11} = 0$ and $\delta_{21} = \gamma_{21}$. So
$$1 = (\delta^{-1} \delta)_{11} = (\delta^{-1})_{12} \, \gamma_{21},$$
and the valuation of the right side is at least $b_n(1, 2) + b_{1-n}(2, 1) = 1$. This is a contradiction. $\square$

**Corollary 3.9.23 (the intertwining of a cuspidal type, [BH06] 15.1).** Let $\Lambda$ be a cuspidal type for $(\alpha, \xi)$. An element $g \in G$ intertwines $\Lambda$ if and only if $g \in J_\alpha$.

Lean: `Langlands.LocalGL2.intertwines_cuspType_iff_mem_jGroup`, `Langlands.LocalGL2.intertwines_cuspType_iff`, `Langlands.LocalGL2.intertwines_psiAlpha_of_mem_cuspTypes`, `Langlands.LocalGL2.mem_jGroup_of_intertwines_cuspType_of_isMinimalElt`, `Langlands.LocalGL2.mem_jGroup_of_intertwines_cuspType_ramBasis`

*Proof.* Elements of $J_\alpha$ intertwine $\Lambda$. If $g$ intertwines $\Lambda$, then it intertwines the restriction $\psi_\alpha$ of $\Lambda$ to $U^m_{\mathfrak{A}}$, since $U^m_{\mathfrak{A}} \cap g^{-1} U^m_{\mathfrak{A}} g \subseteq J_\alpha \cap g^{-1} J_\alpha g$. Theorem 3.9.22 gives $g \in J_\alpha$. $\square$

The Lean library first proved the corollary with the part outside $\mathfrak{K}_{\mathfrak{A}}$ as a hypothesis, `Langlands.LocalGL2.mem_jGroup_of_intertwines_cuspType`, and then proved that hypothesis with Theorem 3.9.22. The theorem `mem_jGroup_of_intertwines_cuspType_ramBasis` is the ramified case with no hypothesis on $\alpha$ other than $v_E(\alpha) = -n$ with $n$ odd.

### The representation $\pi_\xi$

**Theorem 3.9.24 (the cuspidal types induce supercuspidal representations).** Let $(v_1, v_2)$ be adapted to $\mathfrak{A}$, let $\alpha \in E$ be minimal of level $n \ge 1$ with $v_E(\alpha) = -n$ and $n$ prime to $e_{\mathfrak{A}}$, let $n$ be odd, and let $\Lambda$ be a cuspidal type for a compatible pair $(\alpha, \xi)$. Then $\mathrm{c\text{-}Ind}_{J_\alpha}^G \Lambda$ is irreducible and supercuspidal, with central character $\xi|_{K^\times}$.

Lean: `Langlands.LocalGL2.cuspInd`, `Langlands.LocalGL2.nontrivial_cuspInd`, `Langlands.LocalGL2.isIrreducible_cuspInd`; supercuspidality is not formalized

*Proof.* The kernel of $\Lambda$ is open, since $\Lambda$ is trivial on $U^{n+1}_{\mathfrak{A}}$ and on an open subgroup of $E^\times$. By Proposition 3.9.17, $J_\alpha$ is open and compact modulo $K^\times$, and by Corollary 3.9.23 its intertwining is $J_\alpha$. Theorem 3.9.16 gives irreducibility. The last part of the proof of Theorem 1.4.8 shows that the matrix coefficients have compact support modulo the centre, so the representation is supercuspidal by Theorem 1.4.3. The centre $K^\times$ lies in $J_\alpha$ and acts on $\varphi_0$ by $\Lambda|_{K^\times} = \xi|_{K^\times}$. Since $\varphi_0$ generates the representation and $K^\times$ is central, it acts by this character on all of it. $\square$

For even $n$ the same holds for the representation of dimension $q$ of Remark 3.9.14, by Theorem 1.4.8 and [BH06], Chapter 4, section 15.

**Remark 3.9.25 (what the library proves for a minimal pair).** Let $p \ne 2$ and let $(E/K, \xi)$ be a minimal pair of level $n \ge 1$.
1. If $E/K$ is ramified, the chain is complete. `IsMinimal.exists_isSimpleStratum_ram` gives $\alpha$ and the simple stratum for $\mathfrak{J}$, the compatibility holds by construction, `existsUnique_mem_cuspTypes_iff` gives the unique type, `mem_jGroup_of_intertwines_cuspType_ramBasis` gives the intertwining, and `isIrreducible_cuspInd` gives the irreducibility of $\mathrm{c\text{-}Ind}_{J_\alpha}^G \Lambda$.
2. If $E/K$ is unramified and $n$ is odd, the chain needs one more input: that $\alpha$ is minimal in the sense of Definition 3.9.9. This is Proposition 3.9.10, part 2, and the library has only $\alpha \notin K$. With this input, `mem_jGroup_of_intertwines_cuspType_of_isMinimalElt` applies. Example 3.9.26 checks the input by hand.
3. If $E/K$ is unramified and $n$ is even, the type of Remark 3.9.14 is not in the library.
4. Supercuspidality, the central character, and the level zero case of Example 1.4.9 are not in the library.

### Two examples

**Example 3.9.26 (an unramified pair of level 1).** Let $E/K$ be unramified, so that $\varpi$ is a uniformizer of $E$ and the residue field of $E$ is $k_2$. Let $\psi_k$ be the character of $k$ given by $\psi$ on $\mathcal{O}_K$. It is not trivial, since $\psi$ has level one. Let $\beta \in \mathcal{O}_E^\times$ with residue class $\bar\beta \notin k$, and let $\xi$ be a smooth character of $E^\times$, trivial on $U_E^2$, with
$$\xi(1 + \varpi z) = \psi_k(\mathrm{tr}_{k_2/k}(\bar\beta \bar z)), \qquad z \in \mathcal{O}_E.$$
By Exercise 21, $(E/K, \xi)$ is a minimal pair of level $n = 1$. Then $m = r = 1$. Put $\alpha = \varpi^{-1} \beta$. Since $\mathrm{tr}_{E/K}(\alpha \varpi z) = \mathrm{tr}_{E/K}(\beta z)$ reduces to $\mathrm{tr}_{k_2/k}(\bar\beta \bar z)$, the pair $(\alpha, \xi)$ is compatible. The element $\alpha$ is minimal of level 1. Indeed, for $a \in K$, either $v_K(a) \ge 0$ and $v_E(\alpha - a) = -1$, or $v_K(a) = -1$ and $\varpi(\alpha - a)$ has residue $\bar\beta - \overline{\varpi a} \ne 0$, or $v_K(a) \le -2$ and $v_E(\alpha - a) = v_K(a)$. In each case $\alpha - a \notin \mathfrak{p}_E^0$. Here $\mathfrak{A} = \mathfrak{M}$ in the basis $(1, u)$, and
$$J_\alpha = E^\times U^1_{\mathfrak{M}} = \varpi^{\mathbb{Z}} \mathcal{O}_E^\times U^1_{\mathfrak{M}}, \qquad \Lambda(y (1 + \varpi X)) = \xi(y) \, \psi_k(\mathrm{tr}(\bar\beta \bar X)), \quad X \in M_2(\mathcal{O}_K),$$
where $\bar X$ and $\bar\beta$ are the reductions in $M_2(k)$. The image of $J_\alpha \cap GL_2(\mathcal{O}_K) = \mathcal{O}_E^\times U^1_{\mathfrak{M}}$ in $GL_2(k)$ is the nonsplit torus $k_2^\times = k[\bar\beta]^\times$, and its index in $GL_2(\mathcal{O}_K)$ is $q(q-1)$. In this example Proposition 3.9.20 is a statement about $GL_2(k)$: an element $g \in GL_2(\mathcal{O}_K)$ intertwines $\psi_\alpha$ if and only if $\bar g$ commutes with $\bar\beta$, and the centralizer of $\bar\beta$ is $k_2$. Exercise 25 gives the details. By Theorem 3.9.24, $\pi_\xi = \mathrm{c\text{-}Ind}_{J_\alpha}^G \Lambda$ is an irreducible supercuspidal representation with central character $\xi|_{K^\times}$. Compare Example 3.3.21. In level zero the group is $K^\times GL_2(\mathcal{O}_K)$ and the type has dimension $q - 1$. In level one the group is smaller and the type is a character. In the Lean library the inputs are `unramBasis`, `IsMinimal.exists_isSimpleStratum_unram` and `existsUnique_mem_cuspTypes_iff`, and the minimality of $\alpha$ checked above is the hypothesis of `mem_jGroup_of_intertwines_cuspType_of_isMinimalElt`.

**Example 3.9.27 (a ramified pair of level 1).** Let $p$ be odd, $K = \mathbb{Q}_p$, $E = \mathbb{Q}_p(\sqrt p)$, $\varpi_E = \sqrt p$, and let $\xi$ be the character of Example 3.3.18: trivial on $\varpi_E$, on $\mu_{p-1}$ and on $U_E^2$, with $\xi(1 + x \varpi_E) = e^{2\pi i x/p}$ for $x \in \mathbb{Z}$. Take $\psi(x) = e^{2 \pi i \{x/p\}}$, where $\{\cdot\}$ is the fractional part of a $p$-adic number. It has level one. The level is $n = 1$, so $m = r = 1$. Put $\alpha = 1/(2\varpi_E)$. For $y = a \varpi_E + b$ with $a \in \mathbb{Z}_p$ and $b \in p\mathbb{Z}_p$, we have $1 + y \equiv (1 + b)(1 + a\varpi_E)$ modulo $U_E^2$, so $\xi(1 + y) = e^{2\pi i a/p}$. And $\mathrm{tr}_{E/K}(\alpha y) = \mathrm{tr}_{E/K}(a/2 + b/(2\varpi_E)) = a$, so $\psi(\mathrm{tr}_{E/K}(\alpha y)) = e^{2\pi i a/p}$. So $(\alpha, \xi)$ is compatible. In the basis $(\varpi_E, 1)$, which is adapted to $\mathfrak{J}$,
$$\varpi_E = \begin{pmatrix} 0 & 1 \\ p & 0 \end{pmatrix} = \Pi_{\mathfrak{J}}, \qquad \alpha = \tfrac12 \Pi_{\mathfrak{J}}^{-1} = \begin{pmatrix} 0 & 1/(2p) \\ 1/2 & 0 \end{pmatrix}.$$
For $X = \left(\begin{smallmatrix} p a & b \\ p c & p d \end{smallmatrix}\right) \in \mathfrak{P}_{\mathfrak{J}}$ we get $\mathrm{tr}(\alpha X) = (b + c)/2$, so
$$\psi_\alpha(1 + X) = \psi\left(\tfrac{b + c}{2}\right), \qquad J_\alpha = E^\times U^1_{\mathfrak{J}} = \Pi_{\mathfrak{J}}^{\mathbb{Z}} \mu_{p-1} U^1_{\mathfrak{J}}.$$
The type is $\Lambda(\Pi_{\mathfrak{J}}^t \zeta x) = \psi_\alpha(x)$ for $\zeta \in \mu_{p-1}$ and $x \in U^1_{\mathfrak{J}}$. Its value on $p = \Pi_{\mathfrak{J}}^2$ is $1$, so the central character is trivial. The element $\alpha$ is minimal by Proposition 3.9.10, part 1. Here the whole chain of Remark 3.9.25, part 1, is in the Lean library. Exercise 26 checks by hand that $\mathrm{diag}(1, p)$ does not intertwine $\psi_\alpha$. By Theorem 3.9.24, $\pi_\xi = \mathrm{c\text{-}Ind}_{J_\alpha}^G \Lambda$ is an irreducible supercuspidal representation with trivial central character. By Theorem 3.3.20 its parameter is $\sigma(E, \Delta_\xi \xi)$, and by Exercise 22 its restriction to $SL_2(\mathbb{Q}_p)$ has two summands.

### The tame parametrization

**Definition 3.9.28 (the representation $\pi_\xi$).** Let $p \ne 2$ and let $(E/K, \xi)$ be an admissible pair.
1. If $(E/K, \xi)$ is minimal of level $n \ge 1$, fix an adapted basis, let $\alpha$ be as in Proposition 3.9.8, and let $\Lambda_\xi$ be the cuspidal type of Proposition 3.9.13, or of Remark 3.9.14 for even $n$. Put $\pi_\xi = \mathrm{c\text{-}Ind}_{J_\alpha}^G \Lambda_\xi$.
2. If $\xi$ has level 0, then $E/K$ is unramified, and $\pi_\xi$ is the representation of Example 1.4.9 for the character $\theta$ of $k_2^\times$ given by $\xi$, with $\varpi$ acting by $\xi(\varpi)$.
3. In general, write $\xi = \xi' \chi_E$ with $(E/K, \xi')$ minimal or of level 0, by Proposition 3.3.14, and put $\pi_\xi = \pi_{\xi'} \otimes \chi \circ \det$.

Lean: the construction of part 1 is `Langlands.LocalGL2.cuspInd` with `Langlands.LocalGL2.cuspTypes`; the map $\xi \mapsto \pi_\xi$ on all pairs is not defined

The class of $\pi_\xi$ does not depend on the choices. Lemma 3.9.4, part 2, and Proposition 3.9.8 show that $\psi_\alpha$ and $\Lambda_\xi$ depend only on $\xi$ and the embedding. Two embeddings of $E$ in $M_2(K)$ are conjugate by the theorem of Skolem and Noether, and conjugate types induce isomorphic representations. A change of $\psi$ to $x \mapsto \psi(c x)$ with $c \in \mathcal{O}_K^\times$ replaces $\alpha$ by $c^{-1}\alpha$ and gives the same $\Lambda_\xi$. The independence of the decomposition $\xi = \xi' \chi_E$ is [BH06], Chapter 5, section 20.

With this definition, Theorem 3.3.19 says that $\xi \mapsto \pi_\xi$ is a bijection from $\mathbb{P}_2(K)$ onto the supercuspidal classes. Theorem 3.9.24 proves that each $\pi_\xi$ is irreducible and supercuspidal, and it gives the central character. The twist formula holds by definition for the twists of minimal pairs, and in general by the independence above. Two further steps are needed. Injectivity: if $\pi_\xi \cong \pi_{\xi'}$, then the pairs are isomorphic. This follows from the intertwining of two types, by the method of Theorem 3.9.22, and it is [BH06], Chapter 5, section 20. Surjectivity: each irreducible supercuspidal representation contains a type of this list. This uses the theorem of Kutzko [Kut80], Theorem 1.4.10, and the classification of the strata that occur in a supercuspidal representation, [BH06], Chapter 4, sections 12 to 15. Neither step is in the Lean library.

### The reduction of the correspondence to six inputs

The file `Langlands/Local/GL2Reduction.lean` states the local Langlands correspondence for $GL_2$, $p \ne 2$, and proves it from six published theorems. Each of them is a hypothesis of type `Prop` with a citation. No hypothesis is the correspondence itself, so the file reduces the theorem to its known parts.

**Definition 3.9.29 (the statement).** The proposition `Langlands.LocalLanglandsGL2Odd` says: for each nonarchimedean local field $K$ with $2 \ne 0$ in $k$ and each local Artin map $\mathrm{art}_K$, there is a family of bijections $\mathrm{rec}_m : \mathrm{Irr}(GL_m(K)) \to \mathcal{G}_m(K)$ for $m \le 2$ with the conditions of `Langlands.IsLanglandsFamily`.

Lean: `Langlands.LocalLanglandsGL2Odd`

This is the statement `Langlands.LocalLanglandsGL` of Section 3.1 for $n = 2$, restricted to $p \ne 2$. It has the central characters, the twists, the contragredients and the $L$-factors, and it has no $\varepsilon$-factors and no uniqueness. It does not contain the explicit form on the principal series of the statement `Langlands.LocalLanglandsGL2` of Remark 3.3.26.

**Definition 3.9.30 (the six inputs).** Let $p \ne 2$. A *pair* is a pair $(L/K, \xi)$ with $L$ a separable quadratic extension of $K$ inside $\bar K$ and $\xi$ an admissible character of $L^\times$, and $\sigma(L, \xi)$ is its parameter, for a fixed Artin map of $L$. The inputs for one field $K$ and one Artin map $\mathrm{art}_K$ are the following.
1. `ArtinCompat`. For each $L$, the local Artin maps are compatible with conjugation, with the norm and with the transfer, the three properties of Remark 3.3.23 ([Ser79], Chapter XI).
2. `TameParametrizationGL2`. There is a map $P \mapsto \pi_P$ from the pairs to $\mathrm{Irr}(GL_2(K))$ onto the supercuspidal classes, with $\pi_P \cong \pi_Q$ exactly when $P$ and $Q$ are isomorphic, with central character $\xi|_{K^\times}$, and compatible with twists and contragredients. This is Theorem 3.3.19 with the contragredients added ([BH06], 19.1 and 20.2).
3. `GaloisTameParametrization`. Each irreducible Weil-Deligne representation of dimension 2 is isomorphic to some $\sigma(L, \xi)$, and $\sigma(L, \xi) \cong \sigma(L', \xi')$ implies $L = L'$. This is part of Theorem 3.3.16 ([BH06], 34.1).
4. `Rectifier`. There is a family of tamely ramified characters $\Delta_\xi$ with $(L/K, \Delta_\xi \xi)$ admissible and $\Delta_\xi|_{K^\times} = \kappa_{L/K}$, such that $\xi \mapsto \Delta_\xi \xi$ is a bijection on the isomorphism classes of pairs that commutes with twists and with $\xi \mapsto \xi^{-1}$ ([BH06], 34.4).
5. `SupercuspidalLFactor`. $L(s, \pi) = 1$ for each supercuspidal $\pi$ (Godement and Jacquet; [BH06], 24.2).
6. `NonSupercuspidalLLC`. There is a bijection from the classes that are not supercuspidal onto the parameters that are not irreducible, with the conditions on central characters, twists, contragredients and $L$-factors, and the classes that are not supercuspidal are stable under twists and contragredients ([JL70]; [BH06], Chapter 2 and section 33).

Lean: `Langlands.LocalGL2.TamePair`, `Langlands.LocalGL2.TamePair.param`, `Langlands.LocalGL2.ArtinCompat`, `Langlands.LocalGL2.TameParametrizationGL2`, `Langlands.LocalGL2.GaloisTameParametrization`, `Langlands.LocalGL2.Rectifier`, `Langlands.LocalGL2.SupercuspidalLFactor`, `Langlands.LocalGL2.NonSupercuspidalLLC`, `Langlands.LocalGL2.GL2OddInputs`

The statement of input 4 does not fix $\Delta_\xi$. Since `Langlands.LocalLanglandsGL` has no $\varepsilon$-factors, the reduction only needs the restriction $\Delta_\xi|_{K^\times} = \kappa_{L/K}$, which fixes the central character. Input 6 is coarse: it contains the whole correspondence off the supercuspidal classes, and the file does not reduce it to the principal series and the Steinberg representation of Proposition 3.3.3.

**Proposition 3.9.31 (the $L$-factor of an irreducible parameter).** Let $\rho = (r, N)$ be an irreducible Weil-Deligne representation of dimension 2. Then $L(s, \rho) = 1$.

Lean: `Langlands.LocalGL2.lFactor_eq_one_of_isIrreducible`

*Proof.* The space $V' = (\ker N)^{I_K}$ is stable under $W_K$ and $N$, since $I_K$ is normal and $r(w) N r(w)^{-1} = |w| N$. So $V' = 0$ or $V' = V$. If $V' = V$, then $N = 0$ and $r$ factors through the abelian group $W_K / I_K$, which is generated by the image of $\Phi$. An eigenvector of $r(\Phi)$ spans a stable line, which is a contradiction. So $V' = 0$ and $L(s, \rho) = \det(1 - q^{-s} \Phi \mid V')^{-1} = 1$. $\square$

**Proposition 3.9.32 (duals of the parameters).** For a pair $(L/K, \xi)$, $(L/K, \xi^{-1})$ is a pair, and $\sigma(L, \xi^{-1})$ is the dual of $\sigma(L, \xi)$.

Lean: `Langlands.LocalGL2.IsAdmissible.inv`, `Langlands.LocalGL2.tameParam_isDual`

*Proof.* The conditions of Definition 3.3.9 for $\xi^{-1}$ follow from those for $\xi$, since $(\xi^{-1})^\tau = (\xi^\tau)^{-1}$ and $\xi^{-1}$ factors through the norm on a subgroup exactly when $\xi$ does. The character of $W_L$ attached to $\xi^{-1}$ is the inverse of the one attached to $\xi$. The dual of an induced representation is the representation induced from the dual, for a subgroup of finite index. $\square$

**Theorem 3.9.33 (the reduction).** Let $K$ be a nonarchimedean local field with $p \ne 2$ and $\mathrm{art}_K$ a local Artin map. If the six inputs of Definition 3.9.30 hold for $K$ and $\mathrm{art}_K$, then there is a bijection $\mathrm{rec}_2 : \mathrm{Irr}(GL_2(K)) \to \mathcal{G}_2(K)$ with the conditions of `Langlands.IsLanglandsMap`. On the supercuspidal classes it is $\pi_{\Delta_\xi \xi} \mapsto \sigma(L, \xi)$. If the inputs hold for all such $K$ and $\mathrm{art}_K$, then `Langlands.LocalLanglandsGL2Odd` holds.

Lean: `Langlands.LocalGL2.exists_isLanglandsMap_two`, `Langlands.localLanglandsGL2_odd_of_inputs`, with `Langlands.LocalGL2.mk_param_eq_iff`, `Langlands.LocalGL2.isIrreducible_of_iso` and `Langlands.LocalGL2.exists_equiv_glue`

*Proof.* The supercuspidal part comes first. Let $T$ be the set of isomorphism classes of pairs. Input 2 and the bijectivity in input 4 give an injective map $g : T \to \mathrm{Irr}(GL_2(K))$, $[P] \mapsto \pi_{\Delta P}$, with image the supercuspidal classes, where $\Delta P = (L/K, \Delta_\xi \xi)$. The parameter gives a map $f : T \to \mathcal{G}_2(K)$, $[P] \mapsto \sigma(P)$. It is injective by input 3, part 2, and by part 6 of Proposition 3.3.15 under the conjugation compatibility of input 1. This is `mk_param_eq_iff`. Its image is the set of irreducible classes, by part 2 of Proposition 3.3.15 and input 3, part 1. Input 6 gives a bijection between the complements. A general lemma on sets, `exists_equiv_glue`, glues the two parts into one bijection $\mathrm{rec}_2$ with $\mathrm{rec}_2(g(t)) = f(t)$.

Then we check the conditions on the supercuspidal classes. Central characters: $\pi_{\Delta_\xi \xi}$ has central character $\Delta_\xi \xi|_{K^\times} = \kappa_{L/K} \, \xi|_{K^\times}$, by inputs 2 and 4, and $\det \sigma(L, \xi)$ corresponds to $\kappa_{L/K} \, \xi|_{K^\times}$ by part 4 of Proposition 3.3.15 under the transfer compatibility. Twists: inputs 2 and 4 and part 5 of Proposition 3.3.15, under the norm compatibility. Contragredients: inputs 2 and 4 and Proposition 3.9.32. $L$-factors: input 5 and Proposition 3.9.31. Off the supercuspidal classes the conditions are input 6, and the stability statements of input 6 show that a twist or a contragredient does not move a class between the two parts. For the family, the maps for $m = 0, 1$ are those of Section 3.2, `Langlands.LocalGL1.localLanglandsGL_one`. $\square$

**Remark 3.9.34 (what is still open).** The reduction has no `sorry`, so the correspondence for $GL_2$, $p \ne 2$, in the form of `Langlands.LocalLanglandsGL2Odd`, is now equivalent in the library to the six inputs. The following parts are open.
1. Input 1, the three compatibilities of local class field theory, as in Remark 3.3.24, part 5.
2. Input 2 from the types of this section. The library has the types and the irreducibility of Theorem 3.9.24, with the gaps of Remark 3.9.25. It does not have supercuspidality, the level zero case, the map $\xi \mapsto \pi_\xi$ on all pairs, the bridge between the abstract field $E$ of this section and the subfield $L$ of $\bar K$ of `TamePair`, the injectivity and surjectivity of the last subsection, and the contragredients.
3. Input 3, which needs Proposition 3.3.7 and the comparison of two fields, as in Remark 3.3.24, part 7.
4. Input 4. The construction of $\Delta_\xi$ in [BH06], section 34, uses the $\varepsilon$-factors of pairs and the Langlands constant $\lambda(E/K, \psi)$, as explained after Theorem 3.3.20.
5. Input 5, the computation of Godement and Jacquet.
6. Input 6, from the classification of the principal series of Section 1.5 and the $L$-factors of Godement and Jacquet.
7. The case $p = 2$, where Proposition 3.3.7 fails and primitive parameters occur, and the $\varepsilon$-factors and the uniqueness in Theorem 3.3.1.
