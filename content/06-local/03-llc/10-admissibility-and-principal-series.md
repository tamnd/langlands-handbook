---
title: Admissibility of compact induction and the principal series inputs
nodes: []
sources: [BH06, JL70, Ser79]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Admissibility of compact induction and the principal series inputs

Section 3.10 left three kinds of inputs open on the representation side. Input 1 of Definition 3.10.27 says that compact induction from a cuspidal type is admissible and supercuspidal, and Proposition 3.10.34 proved it only from `CompactCoeffAdmissible`. Input 5 of Definition 3.9.30 says that a supercuspidal representation has $L$-factor $1$. The eight inputs of Definition 3.10.14 describe the irreducible subrepresentations of the principal series. This section proves the first input with no hypothesis, it proves the second from one statement on zeta integrals, and it proves five of the eight inputs outright and the other three from six smaller facts. The three Lean files are `Langlands/Local/CIndAdmissible.lean`, `Langlands/Local/SupercuspidalLFactor.lean` and `Langlands/Local/GL2PrincipalSeriesInputs.lean`.

The proof of admissibility is not the proof of [BH06]. Bushnell and Henniart first prove that an irreducible representation with a compactly supported coefficient is admissible ([BH06], 10.1), and they apply this to the coefficient of the basic vector ([BH06], 11.4). That route needs the projection onto the fixed vectors of a compact open subgroup and some finiteness of the Hecke algebra. The route here is more elementary. It splits into two cases according to the restriction of $\Lambda$ to the conjugates of the unipotent radical. In one case a direct count of double cosets bounds the support of a fixed vector. In the other case the representation embeds into an admissible induced representation. The second case does not occur in the end, but the library cannot yet exclude it, so the proof treats it.

We keep the notation of Section 3.10. Let $K$ be a nonarchimedean local field with ring of integers $\mathcal{O}_K$, maximal ideal $\mathfrak{p}_K$, uniformizer $\varpi$ and residue field $k$ of $q$ elements. Let $v_K$ be the normalized valuation and $|x| = q^{-v_K(x)}$. Let $G = GL_2(K)$, $K_0 = GL_2(\mathcal{O}_K)$, $Z = K^\times$ the centre, $B$ the upper triangular Borel subgroup, $N$ its unipotent radical with elements $n(y) = \begin{pmatrix} 1 & y \\ 0 & 1 \end{pmatrix}$, and $T$ the diagonal torus with elements $\mathrm{diag}(a, d)$. Let $w = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}$. The library writes valuations multiplicatively, so a Lean bound $\varepsilon \le v(x)$ means $|x| \ge \varepsilon$ in the notation here.

### Characters and an equivariant linear form

Let $J$ be an open subgroup of $G$ and $\Lambda$ a character of $J$ with open kernel. The space of $\mathrm{c\text{-}Ind}_J^G \Lambda$ consists of the functions $f : G \to \mathbb{C}$ with $f(j g) = \Lambda(j) f(g)$, with support in finitely many cosets $J s$, and invariant on the right under an open subgroup. The group acts by right translation, $(\rho(g) f)(x) = f(x g)$. Let $f_0$ be the basic vector: $f_0(j) = \Lambda(j)$ on $J$ and $f_0 = 0$ off $J$. These are the conventions of Lemma 3.10.29.

**Lemma 3.11.1 (extension of characters).** Let $A$ be a commutative group and $B$ a subgroup. Each homomorphism $\chi : B \to \mathbb{C}^\times$ extends to a homomorphism $A \to \mathbb{C}^\times$.

Lean: `Langlands.zpow_surjective_units_complex`, `Langlands.exists_monoidHom_extend`

*Proof.* For $n \ne 0$ the map $z \mapsto z^n$ of $\mathbb{C}^\times$ is surjective, since $\exp(\log(x) / n)$ is an $n$-th root of $x$. So $\mathbb{C}^\times$ is a divisible abelian group. A divisible abelian group is an injective $\mathbb{Z}$-module by Baer's criterion, and injectivity says exactly that each homomorphism from the subgroup $B$ extends to $A$. $\square$

The extension is not unique, and it need not be continuous. The proofs below only use it on a group where the kernel is open for another reason.

**Definition 3.11.2 (the form $\ell_\theta$).** Let $H$ be a subgroup of $G$ and $\theta : H \to \mathbb{C}^\times$ a character with $\theta = \Lambda$ on $J \cap H$. For $f$ in $\mathrm{c\text{-}Ind}_J^G \Lambda$ put
$$\ell_\theta(f) = \sum_{h \in H / (J \cap H)} \theta(h) \, f(h^{-1}).$$

Lean: `Langlands.charTerm`, `Langlands.charTermQ`, `Langlands.charForm`

**Lemma 3.11.3 (properties of $\ell_\theta$).** In the setting of Definition 3.11.2:
1. the term $\theta(h) f(h^{-1})$ depends only on the coset $h (J \cap H)$;
2. for each $f$ only finitely many cosets give a nonzero term, so $\ell_\theta$ is a well defined linear form;
3. $\ell_\theta(\rho(h_0) f) = \theta(h_0) \, \ell_\theta(f)$ for $h_0 \in H$;
4. $\ell_\theta(f_0) = 1$.

If $\ker \theta$ is open in $H$, then $\ell_\theta$ is a map of representations of $H$ from $\mathrm{c\text{-}Ind}_J^G \Lambda$ to the character $\theta$.

Lean: `Langlands.charTerm_mul_right`, `Langlands.charTermQ_mk`, `Langlands.charTermQ_finite`, `Langlands.charForm_ρ`, `Langlands.charForm_cIndBasic`, `Langlands.charFormHom`

*Proof.* Part 1. For $l \in J \cap H$,
$$\theta(h l) f(l^{-1} h^{-1}) = \theta(h) \theta(l) \Lambda(l)^{-1} f(h^{-1}) = \theta(h) f(h^{-1}),$$
since $\theta(l) = \Lambda(l)$. Part 2. Let the support of $f$ lie in $J s_1 \cup \dots \cup J s_r$. A nonzero term needs $h^{-1} \in J s_i$ for some $i$. If $h^{-1} = j s_i$ and $h'^{-1} = j' s_i$, then $h'^{-1} h = j' j^{-1} \in J \cap H$, so $h$ and $h'$ have the same coset. So at most $r$ cosets contribute. Part 3. Substitute $h = h_0 h'$:
$$\ell_\theta(\rho(h_0) f) = \sum_h \theta(h) f(h^{-1} h_0) = \sum_{h'} \theta(h_0 h') f(h'^{-1}) = \theta(h_0) \ell_\theta(f).$$
Part 4. The term of $h$ is nonzero only if $h^{-1} \in J$, that is, only for the trivial coset, and there it is $\theta(1) f_0(1) = 1$. The last statement is part 3 together with the smoothness of the character $\theta$. $\square$

**Proposition 3.11.4 (admissibility from an embedding).** Let $J$ be open and compact modulo a central subgroup $Z'$, and let $\Lambda$ be a character of $J$ with open kernel whose intertwining lies in $J$. Let $H \subseteq G$ be a subgroup and $\theta$ a character of $H$ with open kernel and $\theta = \Lambda$ on $J \cap H$. If $\mathrm{Ind}_H^G \theta$ is admissible, then $\mathrm{c\text{-}Ind}_J^G \Lambda$ is admissible.

Lean: `Langlands.isAdmissible_cInd_of_isAdmissible_ind`

*Proof.* Put $\pi = \mathrm{c\text{-}Ind}_J^G \Lambda$. By Lemma 3.11.3, $\ell_\theta$ is a map of representations of $H$ from $\pi$ to $\theta$. Frobenius reciprocity in the form of the Lean note to Theorem 1.3.3, for the unnormalized induction from the subgroup $H$, gives the map of representations $\Phi : \pi \to \mathrm{Ind}_H^G \theta$ with $\Phi(f)(g) = \ell_\theta(\rho(g) f)$. Then $\Phi(f_0)(1) = \ell_\theta(f_0) = 1$, so $\Phi \ne 0$. By Theorem 3.9.16, $\pi$ is irreducible, so $\ker \Phi = 0$. For an open subgroup $U$, $\Phi$ then maps $\pi^U$ injectively into $(\mathrm{Ind}_H^G \theta)^U$, which has finite dimension. $\square$

The next lemma is the source of all the support bounds below.

**Lemma 3.11.5 (the support of a fixed vector).** Let $U$ be a subgroup of $G$ and $f$ a vector of $\mathrm{c\text{-}Ind}_J^G \Lambda$ fixed by $U$. If $f(x) \ne 0$, then $\Lambda$ is trivial on $J \cap x U x^{-1}$.

Lean: `Langlands.trivialOnConj_of_mem_fixedVectors` (the conclusion is `Langlands.TrivialOnConj J Λ U x`)

*Proof.* Let $j \in J$ with $u = x^{-1} j x \in U$. Then $j x = x u$, and
$$\Lambda(j) f(x) = f(j x) = f(x u) = (\rho(u) f)(x) = f(x).$$
Since $f(x) \ne 0$, $\Lambda(j) = 1$. $\square$

### The two cases for $GL_2$

From now on $J$ is an open subgroup of $G$, compact modulo $Z$, and $\Lambda$ is a character of $J$ with open kernel whose intertwining lies in $J$. Each scalar matrix intertwines $\Lambda$, since it is central, so $Z \subseteq J$. In Lean this is `Langlands.le_of_forall_intertwines`. The proof splits according to the following alternative. Either

(A) for each $g \in K_0$ there is $y \in K$ with $g n(y) g^{-1} \in J$ and $\Lambda(g n(y) g^{-1}) \ne 1$, or

(B) there is $g_0 \in K_0$ such that $\Lambda$ is trivial on $J \cap g_0 N g_0^{-1}$.

We treat case (B) first.

**Lemma 3.11.6 (the conjugate Borel subgroup).** Let $g \in G$ and $H = g B g^{-1}$. The map $p : H \to K^\times \times K^\times$ that sends $h$ to the diagonal of $g^{-1} h g$ is a homomorphism, and its kernel is $g N g^{-1}$. More precisely, if $p(h) = (1, 1)$, then $h = g \, n(y) \, g^{-1}$ with $y = (g^{-1} h g)_{12}$.

Lean: `Langlands.LocalGL2.conjBorel`, `Langlands.LocalGL2.mem_conjBorel`, `Langlands.LocalGL2.conjDiag`, `Langlands.LocalGL2.val_conjDiag`, `Langlands.LocalGL2.eq_conj_unip_of_conjDiag_eq_one`

*Proof.* The map $b \mapsto$ (diagonal of $b$) is a homomorphism $B \to K^\times \times K^\times$ with kernel $N$, and $p$ is its composite with the isomorphism $h \mapsto g^{-1} h g$ from $H$ onto $B$. An upper triangular matrix with diagonal $(1, 1)$ is $n(y)$ with $y$ its upper right entry. $\square$

**Proposition 3.11.7 (case B).** Assume (B). Then $\mathrm{c\text{-}Ind}_J^G \Lambda$ is admissible.

Lean: `Langlands.LocalGL2.isAdmissible_cInd_of_conj`

*Proof.* Let $H = g_0 B g_0^{-1}$ and let $p$ be the map of Lemma 3.11.6. On $J \cap H$, the kernel of $p$ is $J \cap g_0 N g_0^{-1}$, and $\Lambda$ is trivial there by (B). So $\Lambda|_{J \cap H} = \lambda \circ p$ for a character $\lambda$ of the subgroup $p(J \cap H)$ of $K^\times \times K^\times$. By Lemma 3.11.1, $\lambda$ extends to a character $\chi$ of $K^\times \times K^\times$. Put $\theta = \chi \circ p$. Then $\theta = \Lambda$ on $J \cap H$. The kernel of $\theta$ contains $\ker \Lambda \cap H$, which is open in $H$ since $\ker \Lambda$ is open in the open group $J$. So $\ker \theta$ is open, as a subgroup with an open subgroup.

It remains to see that $\mathrm{Ind}_H^G \theta$ is admissible. The Iwasawa decomposition $G = B K_0$ gives $G = g_0 B K_0 = H C$ with $C = g_0 K_0$ compact. Let $U$ be open and $F \in (\mathrm{Ind}_H^G \theta)^U$. Then $F(h c) = \theta(h) F(c)$ for $h \in H$, and $F(c u) = F(c)$ for $u \in U$. Cover $C$ by finitely many cosets $t_1 U, \dots, t_m U$. Then $F$ is determined by $F(t_1), \dots, F(t_m)$, so $\dim (\mathrm{Ind}_H^G \theta)^U \le m$. In Lean this is `Langlands.SmoothRep.ind_isAdmissible`. Proposition 3.11.4 now gives the result. $\square$

In case (A) we bound the support of a fixed vector. The first lemma makes a conjugation uniform over $K_0$.

**Lemma 3.11.8 (uniform conjugation).** Let $K'$ be an open subgroup of $G$. There is an open subgroup $K''$ with $\rho^{-1} x \rho \in K'$ for all $\rho \in K_0$ and $x \in K''$.

Lean: `Langlands.LocalGL2.exists_open_conj_le`

*Proof.* The group $K' \cap K_0$ is open in the compact group $K_0$, so it has finite index. Let $\tau_1, \dots, \tau_r$ be representatives of $K_0 / (K' \cap K_0)$, and put $K'' = \bigcap_i \tau_i (K' \cap K_0) \tau_i^{-1}$. This is a finite intersection of open subgroups. For $\rho = \tau_i k$ with $k \in K' \cap K_0$ and $x \in K''$, we have $\tau_i^{-1} x \tau_i \in K' \cap K_0$, so $\rho^{-1} x \rho = k^{-1} (\tau_i^{-1} x \tau_i) k \in K'$. $\square$

If $K'$ is normal in $K_0$, for example $K' = 1 + \varpi^k M_2(\mathcal{O}_K)$, then $K'' = K'$ works.

**Lemma 3.11.9 (a bound on the torus).** Assume (A), and let $K'$ be an open subgroup. There is $\varepsilon > 0$ with the following property. If $h = \sigma \, \mathrm{diag}(a, d) \, \rho$ with $\sigma, \rho \in K_0$ and $\Lambda$ is trivial on $J \cap h K' h^{-1}$, then $|d / a| \ge \varepsilon$.

Lean: `Langlands.LocalGL2.exists_le_valuation_of_trivialOnConj`

*Proof.* Take $K''$ as in Lemma 3.11.8, and $\delta > 0$ with $n(z) \in K''$ whenever $|z| < \delta$. The group $S = \ker \Lambda \cap K_0$ is open in $K_0$, so $K_0 = S \tau_1 \cup \dots \cup S \tau_r$ for finitely many $\tau_i$. By (A) there are $y_i$ with $x_i = \tau_i n(y_i) \tau_i^{-1} \in J$ and $\Lambda(x_i) \ne 1$. Then $y_i \ne 0$, since $\Lambda(1) = 1$. Put $\varepsilon = \min_i \delta / |y_i|$.

Let $h = \sigma \, \mathrm{diag}(a, d) \, \rho$ be as in the statement and write $\sigma = s \tau_i$ with $s \in S$. Put $j = \sigma n(y_i) \sigma^{-1} = s x_i s^{-1}$. Since $s \in \ker \Lambda \subseteq J$, we get $j \in J$ and $\Lambda(j) = \Lambda(x_i) \ne 1$. Now
$$h^{-1} j h = \rho^{-1} \, \mathrm{diag}(a, d)^{-1} \, n(y_i) \, \mathrm{diag}(a, d) \, \rho = \rho^{-1} \, n(d y_i / a) \, \rho.$$
If $|d y_i / a| < \delta$, then $n(d y_i / a) \in K''$, so $h^{-1} j h \in K'$ and $j \in J \cap h K' h^{-1}$. Then $\Lambda(j) = 1$, a contradiction. So $|d / a| \ge \delta / |y_i| \ge \varepsilon$. $\square$

**Lemma 3.11.10 (compact support modulo the centre).** Assume (A), and let $K'$ be an open subgroup. There is a compact set $C \subseteq G$ such that each $h \in G$ for which $\Lambda$ is trivial on $J \cap h K' h^{-1}$ has the form $h = c z$ with $c \in C$ and $z \in Z$.

Lean: `Langlands.LocalGL2.exists_isCompact_of_trivialOnConj`

*Proof.* By the Cartan decomposition, $h = \sigma \, \mathrm{diag}(a, d) \, \rho$ with $\sigma, \rho \in K_0$. Lemma 3.11.9 gives $|d / a| \ge \varepsilon$. Since $w^2 = 1$ and $w \, \mathrm{diag}(d, a) \, w = \mathrm{diag}(a, d)$, we can also write $h = (\sigma w) \, \mathrm{diag}(d, a) \, (w \rho)$ with $\sigma w, w \rho \in K_0$, and Lemma 3.11.9 gives $|a / d| \ge \varepsilon$. Choose $n$ with $q^{-n} \le \varepsilon$. Then $d / a = \varpi^k u$ with $|k| \le n$ and $u \in \mathcal{O}_K^\times$. So
$$h = \sigma \, \mathrm{diag}(1, \varpi^k u) \, \rho \cdot a \in K_0 \, \mathrm{diag}(1, \varpi^k) \, K_0 \cdot Z,$$
because $\mathrm{diag}(1, u) \in K_0$. Put $C = \bigcup_{|k| \le n} K_0 \, \mathrm{diag}(1, \varpi^k) \, K_0$. It is a finite union of compact sets. $\square$

**Proposition 3.11.11 (case A).** Assume (A). Then $(\mathrm{c\text{-}Ind}_J^G \Lambda)^U$ has finite dimension for each open subgroup $U$.

Lean: `Langlands.LocalGL2.finiteDimensional_fixedVectors_of_forall`

*Proof.* Take $C$ as in Lemma 3.11.10 for $K' = U$, and cover $C$ by finitely many cosets $t_1 U, \dots, t_m U$. Let $f$ be fixed by $U$ and suppose $f(x) \ne 0$. By Lemma 3.11.5, $\Lambda$ is trivial on $J \cap x U x^{-1}$, so $x = c z$ with $c \in C$ and $z \in Z$. Write $c = t_i u$. Since $z$ is central and lies in $J$,
$$f(x) = f(z t_i u) = \Lambda(z) f(t_i u) = \Lambda(z) f(t_i).$$
So $f(t_i) \ne 0$, and in all cases $f$ is determined by the values $f(t_1), \dots, f(t_m)$. The map $f \mapsto (f(t_i))_i$ is injective on the fixed vectors, and their dimension is at most $m$. $\square$

**Theorem 3.11.12 (compact induction from a type is admissible).** Let $J$ be an open subgroup of $G$ that is compact modulo the centre, and $\Lambda$ a character of $J$ with open kernel. If each element of $G$ that intertwines $\Lambda$ lies in $J$, then $\mathrm{c\text{-}Ind}_J^G \Lambda$ is admissible and supercuspidal. So the statement `CIndSupercuspidal` holds for each $K$, with no input.

Lean: `Langlands.LocalGL2.isAdmissible_cInd_of_intertwining`, `Langlands.LocalGL2.isSupercuspidal_cInd_of_isAdmissible`, `Langlands.LocalGL2.cIndSupercuspidal`

*Proof.* Either (A) or (B) holds. In case (A) use Proposition 3.11.11 with $Z \subseteq J$, and in case (B) use Proposition 3.11.7. Supercuspidality then follows from Theorem 3.10.32. $\square$

The statement is [BH06], 11.4, where the proof goes through 10.1. The theorem removes `CompactCoeffAdmissible` from Proposition 3.10.34 and from Theorem 3.10.37, part 2.

**Corollary 3.11.13 (input 1 of Definition 3.10.27).** Input 1 of Definition 3.10.27 holds for each $K$. So input 2 of Definition 3.9.30 follows from inputs 2 to 5 of Definition 3.10.27 alone.

Lean: `Langlands.LocalGL2.cIndSupercuspidal`, `Langlands.LocalGL2.tameParametrizationGL2_of_inputs`

*Proof.* Input 1 is `CIndSupercuspidal`, which is Theorem 3.11.12. The rest is Theorem 3.10.28. $\square$

**Remark 3.11.14 (case B in the end).** Case (B) is empty for an irreducible $\mathrm{c\text{-}Ind}_J^G \Lambda$ with $J$ compact modulo the centre. In case (B) the proof of Proposition 3.11.7 embeds $\pi$ into $\mathrm{Ind}_H^G \theta$ with $H = g_0 B g_0^{-1}$. Conjugation by $g_0$ turns this into a nonzero map from $\pi$ to an induced representation from $B$, and Frobenius reciprocity (Theorem 1.3.3) then gives $r_B(\pi) \ne 0$. But $\pi$ is supercuspidal by Theorem 3.10.32, and Theorem 1.4.3 says that a supercuspidal representation has zero Jacquet module. The library proves only one direction of Theorem 1.4.3, from Jacquet cuspidal to supercuspidal (`Langlands.SmoothRep.isSupercuspidal_of_isJacquetCuspidal`). The other direction is the statement `PSSupercuspidalJacquet` below. Without it the case split is needed. Note also that the character $\chi$ in the proof need not be smooth, but $\theta$ is smooth, because it agrees with $\Lambda$ on the open group $J \cap H$.

**Example 3.11.15 (the trivial character).** The hypothesis on the intertwining is needed. Let $J = Z K_0$ and $\Lambda = 1$. Each $g \in G$ intertwines the trivial character. Here (B) holds with $g_0 = 1$, and $H = B$, $\theta = 1$. For $g \in G$ the form gives
$$\Phi(f_0)(g) = \ell_1(\rho(g) f_0) = \sum_{h \in B / (B \cap J)} f_0(h^{-1} g) = \#\{h (B \cap J) : h^{-1} g \in J\}.$$
By the Iwasawa decomposition there is exactly one such coset, so $\Phi(f_0)$ is the constant function $1$. The map $\Phi$ is not injective. The space $(\mathrm{c\text{-}Ind}_J^G 1)^{K_0}$ consists of the finitely supported functions on $J \backslash G / K_0$, and this double coset space is infinite by the Cartan decomposition: it is in bijection with the $k \ge 0$ via $\mathrm{diag}(1, \varpi^k)$. But $(\mathrm{Ind}_B^G 1)^{K_0}$ has dimension $1$, since $G = B K_0$. So $\mathrm{c\text{-}Ind}_J^G 1$ is not admissible, and the argument of Proposition 3.11.4 breaks exactly at the irreducibility.

**Example 3.11.16 (an unramified type of odd level).** Let $E / K$ be unramified quadratic, $\mathfrak{A} = \mathfrak{M} = M_2(\mathcal{O}_K)$, and let $n \ge 1$ be odd. Let $\alpha = \varpi^{-n} \beta$ with $\beta \in \mathcal{O}_E^\times$ such that $\beta \bmod \mathfrak{p}_E$ generates $k_E$ over $k$. This is a minimal element of level $n$. Let $m = (n+1)/2$, so $J_\alpha = E^\times U^m_{\mathfrak{M}}$, and let $\Lambda$ be a cuspidal type of Definition 3.9.12, so $\Lambda(x) = \psi(\mathrm{tr}(\alpha (x - 1)))$ on $U^m_{\mathfrak{M}}$, with $\psi$ of level one. We check (A) and compute the bound of Lemma 3.11.9 by hand. Let $g \in K_0$ and $X = g E_{12} g^{-1}$, so $g n(y) g^{-1} = 1 + y X$. For $v_K(y) \ge m$ this lies in $U^m_{\mathfrak{M}}$, and
$$\Lambda(1 + y X) = \psi(\varpi^{-n} y \, \mathrm{tr}(\beta g E_{12} g^{-1})) = \psi(\varpi^{-n} y \, c_g), \qquad c_g = (g^{-1} \beta g)_{21}.$$
The entry $c_g$ is a unit. Otherwise $g^{-1} \beta g$ is upper triangular modulo $\mathfrak{p}_K$, so its reduction has an eigenvalue in $k$. But its characteristic polynomial is that of $\beta$, which is irreducible over $k$. Choose $t \in \mathcal{O}_K$ with $\psi(t c_g) \ne 1$, which is possible since $\psi$ is not trivial on $\mathcal{O}_K$, and put $y = \varpi^n t$. Then $v_K(y) \ge n \ge m$ and $\Lambda(g n(y) g^{-1}) \ne 1$. So (A) holds, with $|y| \le q^{-n}$ for every $g$.

Now take $K' = U^k_{\mathfrak{M}}$. It is normal in $K_0$, and $n(z) \in K'$ exactly when $v_K(z) \ge k$. The proof of Lemma 3.11.9, run with $\sigma$ in place of $\tau_i$, shows that $\Lambda$ trivial on $J \cap h K' h^{-1}$ forces $v_K(d y / a) < k$, that is $v_K(d / a) < k - n$, since $t$ is a unit. The Weyl element gives $v_K(a / d) < k - n$ too. For $k \le n$ there is no such $h$, so by Lemma 3.11.5 the space of vectors fixed by $U^k_{\mathfrak{M}}$ is $0$. For $k = n + 1$ only $v_K(a/d) = 0$ is allowed, and the support of a fixed vector lies in $J K_0$. The basic vector $f_0$ is fixed by $U^{n+1}_{\mathfrak{M}}$, since $\mathrm{tr}(\alpha(u - 1)) \in \mathfrak{p}_K$ for $u \in U^{n+1}_{\mathfrak{M}}$. So the level of the representation is visible in the proof: $U^{n+1}_{\mathfrak{M}}$ has fixed vectors and $U^n_{\mathfrak{M}}$ has none.

### The $L$-factor of a supercuspidal representation

Recall the Lean definition `Langlands.IsGJLFactor K π L` of Section 2.5. Write $X = q^{-s}$. A function $L$ is the Godement-Jacquet $L$-factor of $\pi$ if:

1. $L(s) = P(X)^{-1}$ for a polynomial $P$ with $P(0) = 1$;
2. each zeta integral $Z(\Phi, s, f)$, with $f(g) = \lambda(\pi(g) v)$ for a vector $v$ and a smooth linear form $\lambda$, is $L(s)$ times a Laurent polynomial in $X$, for $\mathrm{Re}(s)$ large;
3. $L(s)$ is a finite sum $\sum_i Q_i(X) Z(\Phi_i, s, f_i)$ with Laurent polynomials $Q_i$.

The library defines $Z$ with the additive Haar measure `Langlands.matrixHaar` on $M_2(K)$. For $n = 2$ the multiplicative measure is $d^\times g = |\det g|^{-2} dg$, so the integrand of `Langlands.gjZeta` is $\Phi(g) f(g) |\det g|^{s + 1/2 - 2}$, which is Definition 2.5.2. For $L = 1$, clause 1 holds with $P = 1$, clause 2 says that the zeta integrals are Laurent polynomials, and clause 3 asks for a combination equal to $1$. We prove clause 3 for every smooth representation.

**Lemma 3.11.17 (a linear form that does not vanish on a fixed vector).** Let $\pi$ be a smooth representation of $G$ on $V$, let $U$ be a compact open subgroup, and let $v \ne 0$ be fixed by $U$. There is a smooth linear form $\lambda$ on $V$, fixed by $U$, with $\lambda(v) \ne 0$.

Lean: `Langlands.SmoothRep.exists_smoothDual_apply_ne_zero`

*Proof.* Let $V(U)$ be the span of the vectors $\pi(u) x - x$ with $u \in U$ and $x \in V$. We claim $v \notin V(U)$. Suppose $v = \sum_{i=1}^r (\pi(u_i) x_i - x_i)$. Let $U_1$ be an open normal subgroup of $U$ that fixes $x_1, \dots, x_r$. It exists: the intersection $U_2$ of $U$ with the stabilizers of the $x_i$ is open, so it has finite index in the compact group $U$, and the intersection of the finitely many $U$-conjugates of $U_2$ is normal and open. Define $A(x) = \sum_{u \in U / U_1} \pi(u) x$ on the vectors fixed by $U_1$. It is well defined. Since $U_1$ is normal, $\pi(u_i) x_i$ is fixed by $U_1$, and $A(\pi(u_i) x_i) = A(x_i)$ because $u U_1 \mapsto u u_i U_1$ permutes $U / U_1$. So $A$ of the right side is $0$. But $v$ is fixed by $U \supseteq U_1$, and $A(v) = [U : U_1] \, v \ne 0$. This contradiction proves the claim.

Choose a linear form $\lambda$ on $V$ with $\lambda(V(U)) = 0$ and $\lambda(v) = 1$, by linear algebra on $V / V(U)$. Then $\lambda(\pi(u) x) = \lambda(x)$ for $u \in U$, so $\lambda$ is fixed by $U$ under the contragredient action and is smooth. $\square$

For $k \ge 1$ let $K_k = 1 + \varpi^k M_2(\mathcal{O}_K)$. It is an open compact subgroup of $K_0$, and it is also an open compact subset of $M_2(K)$, of positive volume. Each $x \in K_k$ has $\det x \in 1 + \mathfrak{p}_K$, so $|\det x| = 1$. The library describes these sets as `Langlands.LocalGL2.scBall`, the set of matrices $x$ with $|(x - 1)_{ij}| < \gamma$ for each entry, and proves that they are open, closed and compact (`Langlands.LocalGL2.isOpen_scBall`, `Langlands.LocalGL2.isCompact_scBall`) and that they form a basis of neighbourhoods of $1$ (`Langlands.LocalGL2.exists_scBall_subset`, `Langlands.LocalGL2.nonsingInvUnit_mem_nhds`).

**Proposition 3.11.18 (the zeta integral of a small ball).** Let $\pi$ be a smooth representation of $G$ on $V$ and $v \in V$. Let $S \subseteq M_2(K)$ be open, and assume that each $x \in S$ is invertible, fixes $v$ and has $|\det x| = 1$. Then for each linear form $\lambda$ and each $s$,
$$Z(1_S, s, f) = \mathrm{vol}(S) \, \lambda(v), \qquad f(g) = \lambda(\pi(g) v).$$
Such an $S$ with $\mathrm{vol}(S) > 0$ and $1_S$ a Schwartz-Bruhat function exists for each $v$.

Lean: `Langlands.LocalGL2.gjZeta_indicator`, `Langlands.LocalGL2.exists_gjZeta_eq_const`, `Langlands.LocalGL2.matrixHaar_real_scBall_ne_zero`

*Proof.* On $S$ the integrand is $\lambda(\pi(x) v) |\det x|^{s - 3/2} = \lambda(v)$, and off $S$ it is $0$. So the integral is $\lambda(v) \, \mathrm{vol}(S)$. For the existence, the stabilizer of $v$ is open, so it contains $K_k$ for some $k \ge 1$, and $S = K_k$ works. Its indicator function is locally constant with compact support. $\square$

The point is that the integral does not depend on $s$ at all. So it is a constant Laurent polynomial in $X$.

**Definition 3.11.19 (the Laurent form of the zeta integrals).** The statement `SupercuspidalZetaLaurent` for $K$ says: for each irreducible supercuspidal representation $\pi$ of $G$, each Schwartz-Bruhat function $\Phi$, each vector $v$ and each smooth linear form $\lambda$, there are a polynomial $A$, an integer $k \ge 0$ and $s_0$ with $Z(\Phi, s, f) = A(X) X^{-k}$ for $\mathrm{Re}(s) > s_0$.

Lean: `Langlands.LocalGL2.SupercuspidalZetaLaurent`

**Theorem 3.11.20 (the $L$-factor of a supercuspidal representation).** Let $\pi$ be a smooth representation of $G$ on a nonzero space. If each zeta integral of $\pi$ is a Laurent polynomial in $X$ for $\mathrm{Re}(s)$ large, then $L(s, \pi) = 1$ in the sense of `IsGJLFactor`. In particular `SupercuspidalZetaLaurent` implies input 5 of Definition 3.9.30.

Lean: `Langlands.LocalGL2.isGJLFactor_one_of_zeta`, `Langlands.LocalGL2.isGJLFactor_one_of_isSupercuspidal`, `Langlands.LocalGL2.supercuspidalLFactor_of_zetaLaurent`, `Langlands.SmoothRep.isSupercuspidal_of_iso`

*Proof.* Clause 1 holds with $P = 1$, and clause 2 is the hypothesis. For clause 3, choose $v \ne 0$, and let $U$ be the intersection of the stabilizer of $v$ with $K_0$. It is compact and open. Lemma 3.11.17 gives a smooth $\lambda$ with $\lambda(v) \ne 0$, and Proposition 3.11.18 gives $\Phi$ and $c > 0$ with $Z(\Phi, s, f) = c \lambda(v)$ for all $s$. So
$$1 = (c \lambda(v))^{-1} \, Z(\Phi, s, f),$$
with the constant Laurent polynomial $Q = (c \lambda(v))^{-1}$. For input 5, which is stated for the classes of supercuspidal representations, `isSupercuspidal_of_iso` moves supercuspidality from the chosen representative to the given one. $\square$

**Remark 3.11.21 (what is left).** Proposition 2.5.6 proves that the zeta integrals of a supercuspidal representation are Laurent polynomials. The coefficient $f$ has support in $C Z$ for a compact set $C$. If $\Phi$ vanishes near $0$, then $\Phi f$ has compact support in $G$, and $|\det g|$ takes finitely many values on it, so the integral is a finite sum of powers of $X$. A general $\Phi$ differs from one that vanishes near $0$ by a function supported near $0$, and for that part one uses the vanishing of the integrals of $f$ over the unipotent radicals, which is cuspidality. The details are in Godement and Jacquet, *Zeta functions of simple algebras*, Lecture Notes in Mathematics 260, and in [BH06], 24.2. The library lacks the Haar measure on $G$ and the comparison of integrals over $M_2(K)$ with integrals over $G$ that this needs, so `SupercuspidalZetaLaurent` is still a named input. Theorem 3.11.20 is the part of the argument that needs no analysis.

**Example 3.11.22 (a zeta integral that is not a Laurent polynomial).** Clause 2 fails for the trivial representation $1_G$, and we compute why. Take $\Phi = 1_{M_2(\mathcal{O}_K)}$, $f = 1$, and normalize $d^\times g$ so that $\mathrm{vol}(K_0) = 1$. Let $T_m$ be the set of $g \in M_2(\mathcal{O}_K)$ with $v_K(\det g) = m$. It is a union of cosets $g K_0$, and by the Hermite normal form each coset has exactly one representative $\begin{pmatrix} \varpi^a & b \\ 0 & \varpi^c \end{pmatrix}$ with $a + c = m$ and $b$ in a fixed set of representatives of $\mathcal{O}_K / \mathfrak{p}_K^a$. So $T_m$ has $\sum_{i=0}^m q^i$ cosets, and
$$Z(\Phi, s, 1) = \sum_{m \ge 0} \Big( \sum_{i=0}^m q^i \Big) q^{-m(s + 1/2)} = \frac{1}{(1 - q^{-1/2} X)(1 - q^{1/2} X)}.$$
The last step is the product of the two geometric series in $Y = q^{-1/2} X$ and $q Y$. This matches the $L$-factor $L(s, 1_G) = (1 - q^{1/2 - s})^{-1} (1 - q^{-1/2 - s})^{-1}$ of Example 3.10.19. It is also the case $\chi = |\cdot|^{-1/2}$ of the fact `PSLFactorDetChar` below, since $\chi |\cdot|^{1/2} = 1$ and $L(s, \chi) L(s, \chi |\cdot|) = (1 - q^{1/2} X)^{-1} (1 - q^{-1/2} X)^{-1}$.

### The principal series

The library has two models of the principal series. `Langlands.principalSeries K χ₁ χ₂` is the model of Definition 3.10.14. `Langlands.normPrincipalSeries χ₁ χ₂` is the model of the Smooth folder: the unnormalized induction $\mathrm{Ind}_B^G \theta$ of the character $\theta(b) = \chi_1(a) \chi_2(d) |a / d|^{1/2}$ of $B$, on which Theorems 1.5.1 and 1.5.5 are proved.

**Remark 3.11.23 (the comparison of the two models).** Remark 3.10.15 says that the comparison of the two models is not formalized. That is not correct. The isomorphism `Langlands.normPrincipalSeries_iso` between `principalSeries K χ₁ χ₂` and `normPrincipalSeries χ₁ χ₂` is in `Langlands/Smooth/PrincipalSeries.lean`, and it is used throughout this section. What Remark 3.10.15 calls missing is in fact the content of the proofs below, which transport the results of Section 1.5 along this isomorphism.

In the normalized Jacquet module $r_B$ of Section 1.3 the quotient character of $\chi_1 \times \chi_2$ is $\chi_1 \otimes \chi_2$ (Theorem 1.3.11). The library uses the unnormalized Jacquet module $V / V(N)$, on which this character becomes
$$\gamma = \chi_1 |\cdot|^{1/2} \otimes \chi_2 |\cdot|^{-1/2}, \qquad \gamma(\mathrm{diag}(a, d)) = \chi_1(a) \chi_2(d) |a / d|^{1/2}.$$
This is `Langlands.LocalGL2.psGamma χ₁ χ₂`. For a representation $\Pi$ of $G$ let $\Pi_\gamma$ be the subspace of the vectors $v$ with $\Pi(t) v - \gamma(t) v \in V(N)$ for all $t \in T$. In Lean this is `jacquetEigenSub Π γ`. The Steinberg subspace `normSteinbergSub` is defined as $\Pi_\gamma$ for $\Pi = \chi_1 \times \chi_2$ with $\chi_1 = \chi_2 |\cdot|$. Recall that $(\chi_1, \chi_2)$ is a Steinberg pair if $\chi_1 = \chi_2 |\cdot|$ (`Langlands.LocalGL2.psIsSt_iff`).

**Definition 3.11.24 (the socle).** A *socle* of a representation $\Pi$ is a nonzero stable subspace $S$ that is contained in each nonzero stable subspace.

A socle is unique if it exists, since two socles contain each other. The representation on a socle is irreducible: a nonzero stable subspace of $S$ is stable in $\Pi$, so it contains $S$. In Lean this is `Langlands.SmoothRep.sub_isIrreducible_of_le`.

**Lemma 3.11.25 (the socle argument).** Let $S$ be a socle of $\Pi$ and $\sigma$ an irreducible representation with a nonzero map $T : \sigma \to \Pi$. Then $T$ is an isomorphism of $\sigma$ onto the representation on $S$. If $\Pi$ is irreducible, then $\sigma \cong \Pi$.

Lean: `Langlands.LocalGL2.psIso_sub_of_hasHom`, `Langlands.LocalGL2.psIso_of_hasHom`, `Langlands.LocalGL2.psHasHom_sub`, `Langlands.LocalGL2.psHasHom_of_iso`, `Langlands.LocalGL2.psHasHom_of_iso_right`

*Proof.* The image of $T$ is a nonzero stable subspace, so it contains $S$. The preimage $T^{-1}(S)$ is a nonzero stable subspace of $\sigma$, because $S \ne 0$ lies in the image. Since $\sigma$ is irreducible, $T^{-1}(S) = \sigma$, so the image is $S$. The kernel is a stable subspace different from $\sigma$, so it is $0$. If $\Pi$ is irreducible, then $S = \Pi$. $\square$

**Theorem 3.11.26 (the socle of the principal series).** Let $\Pi = \chi_1 \times \chi_2$ in the model `normPrincipalSeries`. Then $\Pi$ has a socle $S$, and either $\Pi$ is irreducible or $S \subseteq \Pi_\gamma$. More precisely:
1. if $\chi_1 = \chi_2 |\cdot|$, then $S$ is the Steinberg subspace $\Pi_\gamma$;
2. if $\chi_2 = \chi_1 |\cdot|$, then $S$ is the line of the function $(\chi_1 |\cdot|^{1/2}) \circ \det$;
3. otherwise $\Pi$ is irreducible and $S = \Pi$.

Each irreducible representation with a nonzero map to `principalSeries K χ₁ χ₂` is isomorphic to the representation on $S$.

Lean: `Langlands.LocalGL2.psExists_socle`, `Langlands.LocalGL2.psIso_socle`, `Langlands.LocalGL2.psρ_of_mem_detLine`, `Langlands.LocalGL2.psGamma`

*Proof.* Case 1. Theorem 1.5.1, part 3, says that the Steinberg subspace is the only stable subspace other than $0$ and $\Pi$, and it is not $0$. So it is a socle (`Langlands.normSteinbergSub_le_of_ne_bot`). Case 2. Theorem 1.5.1, part 2, with $\eta = \chi_1 |\cdot|^{1/2}$, says that the stable subspaces are $0$, the line $D$ of $\eta \circ \det$ and $\Pi$. So $D$ is a socle. The group acts on $D$ by $\eta \circ \det$. For $t = \mathrm{diag}(a, d)$,
$$\eta(\det t) = \chi_1(a) |a|^{1/2} \chi_1(d) |d|^{1/2} = \chi_1(a) |a|^{1/2} \chi_2(d) |d|^{-1/2} = \gamma(t),$$
since $\chi_2 = \chi_1 |\cdot|$. So $\Pi(t) v - \gamma(t) v = 0 \in V(N)$ for $v \in D$, and $D \subseteq \Pi_\gamma$. Case 3. Theorem 1.5.1, part 1, says that $\Pi$ is irreducible. The last statement is Lemma 3.11.25, after composing with `normPrincipalSeries_iso`. $\square$

**Proposition 3.11.27 (the subrepresentation fixes the pair).** Let $S$ be a stable subspace of $\Pi = \chi_1 \times \chi_2$ with $S \subseteq \Pi_\gamma$, and let $\sigma$ be the representation on $S$. If $\sigma$ has a nonzero map to $\psi_1 \times \psi_2$, then $(\psi_1, \psi_2) = (\chi_1, \chi_2)$.

Lean: `Langlands.LocalGL2.psEq_of_hasHom_sub`

*Proof.* The target is $\mathrm{Ind}_B^G \gamma'$ with $\gamma' = \psi_1 |\cdot|^{1/2} \otimes \psi_2 |\cdot|^{-1/2}$, extended trivially on $N$. Frobenius reciprocity (Theorem 1.3.3, in the form `jacquetFrobenius`) turns a nonzero map $\sigma \to \mathrm{Ind}_B^G \gamma'$ into a nonzero $T$-map $\varphi$ from the unnormalized Jacquet module $S / S(N)$ to $\gamma'$. We claim that $T$ acts on $S / S(N)$ by $\gamma$. For $v \in S$ and $t \in T$, the vector $\sigma(t) v - \gamma(t) v$ lies in $S$, and it lies in $V(N)$ by the hypothesis $S \subseteq \Pi_\gamma$. The Jacquet functor is exact (Proposition 1.3.5), so $S / S(N) \to V / V(N)$ is injective, that is $S \cap V(N) = S(N)$ (`Langlands.jacquetMap_unipotent_injective`). So the vector lies in $S(N)$, which proves the claim. Choose $x$ with $\varphi(x) \ne 0$. Then
$$\gamma'(t) \varphi(x) = \varphi(t x) = \gamma(t) \varphi(x),$$
so $\gamma' = \gamma$. A character of $T$ determines its two components (`Langlands.torusChar_inj`), so $\psi_1 |\cdot|^{1/2} = \chi_1 |\cdot|^{1/2}$ and $\psi_2 |\cdot|^{-1/2} = \chi_2 |\cdot|^{-1/2}$. $\square$

**Proposition 3.11.28 (an irreducible quotient lies in the swapped series).** Let $q : \chi_1 \times \chi_2 \to \pi'$ be a surjective map onto an irreducible representation. Then $\pi'$ has a nonzero map to $\chi_2 \times \chi_1$.

Lean: `Langlands.LocalGL2.psHasHom_swap_of_surjective`

*Proof.* Let $W = \ker q$. If $W = 0$, then $q$ is an isomorphism, so $\chi_1 \times \chi_2$ is irreducible, and Theorem 1.5.5 (`Langlands.normPrincipalSeries_iso_iff`) gives $\chi_1 \times \chi_2 \cong \chi_2 \times \chi_1$. Otherwise $W$ is a proper nonzero stable subspace. By Theorem 1.3.11 the Jacquet module of $\chi_1 \times \chi_2$ has dimension $2$, with the character $\chi_2 \otimes \chi_1$ on a line and $\chi_1 \otimes \chi_2$ on the quotient, in the normalized form. By Theorem 1.5.1 the subspace $W$ is the socle, so its Jacquet module is the line on which $T$ acts by the quotient character. By exactness the Jacquet module of $\pi' = (\chi_1 \times \chi_2) / W$ is nonzero and $T$ acts on it by $\chi_2 \otimes \chi_1$ (`Langlands.normPrincipalSeries_quotient_jacquet_nontrivial`). Frobenius reciprocity gives a nonzero map $\Phi : \chi_1 \times \chi_2 \to \chi_2 \times \chi_1$ that vanishes on $W$ (`Langlands.normPrincipalSeries_exists_hom_of_quotient`). It factors through $q$, and the factor is the required map. $\square$

**Lemma 3.11.29 (the $L$-factor is an invariant of the class).** If $\pi \cong \pi'$ and $L$ is the Godement-Jacquet $L$-factor of $\pi$, then $L$ is the $L$-factor of $\pi'$.

Lean: `Langlands.LocalGL2.psComp_mem_smoothVectors`, `Langlands.LocalGL2.psGjZeta_iso`, `Langlands.LocalGL2.psIsGJLFactor_of_iso`

*Proof.* Let $e : \pi \to \pi'$ be an isomorphism. A smooth linear form $\lambda'$ on $\pi'$ gives the smooth form $\lambda' \circ e$ on $\pi$, and $\lambda'(\pi'(g) e(v)) = (\lambda' \circ e)(\pi(g) v)$. So the matrix coefficients of $\pi$ and $\pi'$ are the same functions, and so are their zeta integrals. The three clauses of `IsGJLFactor` only see the set of zeta integrals. $\square$

**Theorem 3.11.30 (five of the eight inputs).** The inputs `PSSubExists`, `PSSubUnique`, `PSSubSwap`, `PSSubRigid` and `NonSupercuspidalExhaustion` of Definition 3.10.14 hold for each $K$.

Lean: `Langlands.LocalGL2.psSubExists`, `Langlands.LocalGL2.psSubUnique`, `Langlands.LocalGL2.psSubSwap`, `Langlands.LocalGL2.psSubRigid`, `Langlands.LocalGL2.psExhaustion`

*Proof.* Let $\Pi = \chi_1 \times \chi_2$ and let $S$ be the socle of Theorem 3.11.26.

`PSSubExists`. The representation on $S$ is irreducible by Definition 3.11.24 and the remark after it. It is admissible as a subrepresentation of the admissible $\Pi$ (Proposition 1.3.4, part 2; `Langlands.normPrincipalSeries_isAdmissible`). The inclusion followed by `normPrincipalSeries_iso` is a nonzero map to `principalSeries K χ₁ χ₂`.

`PSSubUnique`. By Theorem 3.11.26 both representations are isomorphic to the representation on $S$.

`PSSubSwap`. Neither pair is a Steinberg pair, so $\chi_1 \chi_2^{-1} \ne |\cdot|^{\pm 1}$ and $\Pi$ is irreducible. By Lemma 3.11.25, $\pi \cong \Pi$, and by Theorem 1.5.5, $\Pi \cong \chi_2 \times \chi_1$. Compose with `normPrincipalSeries_iso` for $(\chi_2, \chi_1)$.

`PSSubRigid`. Let $\pi$ be in $\chi_1 \times \chi_2$ and in $\psi_1 \times \psi_2$. If $\Pi$ is irreducible, then $\pi \cong \Pi$ by Lemma 3.11.25, so $\Pi$ has a nonzero map to $\psi_1 \times \psi_2$. By Theorem 1.5.5 (`Langlands.normPrincipalSeries_hom_eq`), $(\psi_1, \psi_2)$ is $(\chi_1, \chi_2)$ or $(\chi_2, \chi_1)$. In the second case neither pair is a Steinberg pair, because $\Pi$ is irreducible. If $\Pi$ is reducible, then $\pi$ is isomorphic to the representation on $S$, and $S \subseteq \Pi_\gamma$ by Theorem 3.11.26. Proposition 3.11.27 gives $(\psi_1, \psi_2) = (\chi_1, \chi_2)$.

`NonSupercuspidalExhaustion`. Let $\pi$ be irreducible, admissible and not supercuspidal. Then $\pi$ is not Jacquet cuspidal, since a Jacquet cuspidal representation is supercuspidal (`Langlands.SmoothRep.isSupercuspidal_of_isJacquetCuspidal`). Corollary 1.5.9 (`Langlands.classification_of_isAdmissible`) gives three cases. If $\pi$ is isomorphic to an irreducible $\chi_1 \times \chi_2$, then $\pi$ is in $\chi_1 \times \chi_2$. If $\pi \cong \chi \circ \det$, then $\pi$ is the socle of $\chi |\cdot|^{-1/2} \times \chi |\cdot|^{1/2}$, by Theorem 3.11.26, case 2. If $\pi$ is isomorphic to the Steinberg subspace of $\chi_1 \times \chi_2$ with $\chi_1 = \chi_2 |\cdot|$, then $\pi$ is in $\chi_1 \times \chi_2$. $\square$

The three remaining inputs need facts that the library does not have yet.

**Definition 3.11.31 (the six facts).** The structure `PSInputProps` for $K$ consists of the following statements.
1. `PSSupercuspidalJacquet`. An irreducible supercuspidal representation of $G$ is Jacquet cuspidal ([BH06], Chapter 2, section 10; [JL70], section 2). This is the converse of `isSupercuspidal_of_isJacquetCuspidal`, and with it Theorem 1.4.3.
2. `PSContragredientIso`. The contragredient of `principalSeries K χ₁ χ₂` is isomorphic to `principalSeries K χ₁⁻¹ χ₂⁻¹` (Proposition 1.3.4, part 3; [BH06], Chapter 1).
3. `SmoothDualExtends`. If $f : \sigma \to \pi$ is an injective map of smooth representations of $G$, then each smooth linear form on $\sigma$ is $\lambda' \circ f$ for a smooth linear form $\lambda'$ on $\pi$ ([BH06], Chapter 1).
4. `PSLFactorIrreducible`. If neither $(\chi_1, \chi_2)$ nor $(\chi_2, \chi_1)$ is a Steinberg pair, then $L(s, \chi_1 \times \chi_2) = L(s, \chi_1) L(s, \chi_2)$.
5. `PSLFactorDetChar`. For a smooth $\chi$, $L(s, (\chi |\cdot|^{1/2}) \circ \det) = L(s, \chi) L(s, \chi |\cdot|)$.
6. `PSLFactorSteinberg`. If $\chi_1 = \chi_2 |\cdot|$, then the $L$-factor of the Steinberg subspace of $\chi_1 \times \chi_2$ is $L(s, \chi_1)$.

The sources of items 4 to 6 are [BH06], Chapter 6, section 26, Godement and Jacquet, Theorem 3.3, and [JL70], section 3. Here $L(s, \chi)$ is `Langlands.LocalGL1.charLFactor`, which is $(1 - \chi(\varpi) X)^{-1}$ for unramified $\chi$ and $1$ otherwise.

Lean: `Langlands.LocalGL2.PSSupercuspidalJacquet`, `Langlands.LocalGL2.PSContragredientIso`, `Langlands.LocalGL2.SmoothDualExtends`, `Langlands.LocalGL2.PSLFactorIrreducible`, `Langlands.LocalGL2.PSLFactorDetChar`, `Langlands.LocalGL2.PSLFactorSteinberg`, `Langlands.LocalGL2.PSInputProps`

**Theorem 3.11.32 (the three other inputs).**
1. `PSSupercuspidalJacquet` implies `PSSubNotSupercuspidal`.
2. `PSContragredientIso` and `SmoothDualExtends` imply `PSSubContragredient`.
3. `PSLFactorIrreducible`, `PSLFactorDetChar` and `PSLFactorSteinberg` imply `PSSubLFactor`.

So `PSInputProps` implies the eight inputs of Definition 3.10.14.

Lean: `Langlands.LocalGL2.psSubNotSupercuspidal_of`, `Langlands.LocalGL2.psSubContragredient_of`, `Langlands.LocalGL2.psSubLFactor_of`, `Langlands.LocalGL2.nonSupercuspidalInputs_of_psInputProps`

*Proof.* Part 1. Let $\pi$ be in $\chi_1 \times \chi_2$. Composing with `normPrincipalSeries_iso` gives a nonzero map to $\mathrm{Ind}_B^G \gamma$, and Frobenius reciprocity gives a nonzero map from the Jacquet module of $\pi$ to $\gamma$. So the Jacquet module is not $0$, and $\pi$ is not Jacquet cuspidal. By `PSSupercuspidalJacquet`, $\pi$ is not supercuspidal.

Part 2. Let $\pi$ be irreducible and in $\chi_1 \times \chi_2$ by $f$, and let $\pi' \cong \pi^\vee$ be irreducible. The map $f$ is injective (Proposition 3.10.13, part 1). Restriction $r(\lambda) = \lambda \circ f$ is a map of representations from the contragredient of $\chi_1 \times \chi_2$ to $\pi^\vee$ (`psComp_mem_smoothVectors` checks smoothness), and `SmoothDualExtends` says that it is surjective. Compose with the isomorphism $\chi_1^{-1} \times \chi_2^{-1} \cong (\chi_1 \times \chi_2)^\vee$ of `PSContragredientIso`, with $\pi^\vee \cong \pi'$, and with `normPrincipalSeries_iso`. This gives a surjective map from the normalized $\chi_1^{-1} \times \chi_2^{-1}$ onto $\pi'$. Proposition 3.11.28 puts $\pi'$ in $\chi_2^{-1} \times \chi_1^{-1}$.

Part 3. Let $\pi$ be in $\chi_1 \times \chi_2$. If $\chi_1 = \chi_2 |\cdot|$, then $\pi$ is isomorphic to the Steinberg subspace by Theorem 3.11.26, and `PSLFactorSteinberg` with Lemma 3.11.29 gives $L(s, \pi) = L(s, \chi_1)$. If $\chi_2 = \chi_1 |\cdot|$, then $\pi \cong (\chi_1 |\cdot|^{1/2}) \circ \det$, and `PSLFactorDetChar` with $\chi = \chi_1$ gives $L(s, \chi_1) L(s, \chi_1 |\cdot|) = L(s, \chi_1) L(s, \chi_2)$. In this case $(\chi_1, \chi_2)$ is not a Steinberg pair, as input 8 requires. Otherwise $\pi \cong \chi_1 \times \chi_2$, and `PSLFactorIrreducible` applies. $\square$

**Remark 3.11.33 (where the six facts are proved).** Fact 1 is Theorem 1.4.3, whose proof uses the characterization of cuspidal representations by compactly supported coefficients ([BH06], Chapter 2, section 10). Fact 2 is Proposition 1.3.4, part 3. Its proof pairs $f_1 \in \chi_1 \times \chi_2$ with $f_2 \in \chi_1^{-1} \times \chi_2^{-1}$ by $\langle f_1, f_2 \rangle = \int_{K_0} f_1(k) f_2(k) \, dk$. The product $f_1 f_2$ transforms on the left by $\delta_B$, and the integral is then the invariant integral over $B \backslash G$, which the library does not have. Fact 3 has a short proof that the library cannot yet state, because it needs the projection onto the fixed vectors. Let $\lambda$ be a smooth form on $\sigma$, fixed by a compact open subgroup $U$. For $x$ in a smooth representation let $e_U(x) = [U : U']^{-1} \sum_{u \in U / U'} \pi(u) x$, where $U' \subseteq U$ is any open subgroup that fixes $x$. This does not depend on $U'$, it is linear, its image is the space of $U$-fixed vectors, and it commutes with maps of representations. Choose any linear form $\lambda_1$ on $\pi$ with $\lambda_1 \circ f = \lambda$, which exists since $f$ is injective, and put $\lambda' = \lambda_1 \circ e_U$. Then $\lambda'$ is fixed by $U$, so it is smooth, and
$$\lambda'(f(v)) = \lambda_1(f(e_U v)) = \lambda(e_U v) = \lambda(v),$$
the last step because $\lambda$ is fixed by $U$. Facts 4 to 6 are the computation of the zeta integrals of the principal series and of its subquotients, as in Example 3.11.22 for the trivial representation ([BH06], Chapter 6, section 26).

**Example 3.11.34 (the pair $(\chi, \chi |\cdot|)$).** Let $\chi$ be unramified with $\chi(\varpi) = a$, and let $\Pi = \chi \times \chi |\cdot|$. Then $\chi_2 = \chi_1 |\cdot|$, so we are in case 2 of Theorem 3.11.26, with socle the line of $\eta \circ \det$, $\eta = \chi |\cdot|^{1/2}$. The representation $\eta \circ \det$ is in $\chi \times \chi |\cdot|$, and by Proposition 3.11.27 it is in no other principal series. The quotient of $\Pi$ by the line is $\eta \mathrm{St}$, and by Proposition 3.11.28 it lies in $\chi |\cdot| \times \chi$, where it is the Steinberg subspace. By Theorem 3.11.32, part 3, $L(s, \eta \circ \det) = (1 - a X)^{-1} (1 - a q^{-1} X)^{-1}$ and $L(s, \eta \mathrm{St}) = (1 - a q^{-1} X)^{-1}$, given the six facts. For $a = q^{1/2}$ we get $\eta = 1$ and recover Examples 3.10.18 and 3.10.19.

### What is open for $GL_2$, $p \ne 2$

**Corollary 3.11.35 (the reduction as it stands).** Let $p \ne 2$. The statement `Langlands.LocalLanglandsGL2Odd` follows, for all $K$, from:
1. `ArtinCompat`, `GaloisTameParametrization` and `Rectifier`, inputs 1, 3 and 4 of Definition 3.9.30;
2. `SupercuspidalZetaLaurent`, Definition 3.11.19;
3. the six facts of Definition 3.11.31;
4. `TypeRepInjective`, `TypeRepIndependent`, `TypeRepContragredient` and `UncoveredParametrization`, inputs 2 to 5 of Definition 3.10.27.

Lean: `Langlands.LocalGL2.GL2OddFineInputs`, `Langlands.localLanglandsGL2_odd_of_fineInputs`, `Langlands.LocalGL2.cIndSupercuspidal`, `Langlands.LocalGL2.supercuspidalLFactor_of_zetaLaurent`, `Langlands.LocalGL2.nonSupercuspidalInputs_of_psInputProps` (the joining step is not yet in the library)

*Proof.* Item 2 gives input 5 of Definition 3.9.30 by Theorem 3.11.20. Item 3 gives the eight inputs of Definition 3.10.14 by Theorems 3.11.30 and 3.11.32. Item 4 with Theorem 3.11.12 gives input 2 of Definition 3.9.30 by Corollary 3.11.13. Theorem 3.10.37, part 1, concludes. $\square$

The library has all the pieces of this proof, but no structure yet joins `cIndSupercuspidal`, `supercuspidalLFactor_of_zetaLaurent` and `nonSupercuspidalInputs_of_psInputProps` into `GL2OddFineInputs`. That is a formal step.

**Remark 3.11.36 (what is still open for $GL_2$, $p \ne 2$).** This list replaces Remark 3.10.38.
1. `ArtinCompat` ([Ser79], Chapter XI).
2. `GaloisTameParametrization`.
3. `Rectifier`, with the characters $\Delta_\xi$ of [BH06], section 34.
4. `SupercuspidalZetaLaurent`, the analytic half of Proposition 2.5.6. It replaces `SupercuspidalLFactor`.
5. The six facts of Definition 3.11.31. They replace the eight inputs of Definition 3.10.14.
6. `TypeRepInjective`, `TypeRepIndependent`, `TypeRepContragredient` and `UncoveredParametrization`.
7. The structure that joins the results of this section into `GL2OddFineInputs`.
8. The case $p = 2$, the $\varepsilon$-factors, and the uniqueness of Theorem 3.3.1.

Item 6 of Remark 3.10.38, `CompactCoeffAdmissible`, is no longer needed for the correspondence. It remains true and interesting as a theorem in its own right ([BH06], 10.1), but Theorem 3.11.12 avoids it.
