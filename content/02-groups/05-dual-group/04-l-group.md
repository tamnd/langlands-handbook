---
title: The L-group
nodes: []
sources: [Lan70]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## The L-group

The dual group of Section 5.2 does not see the field of definition. Two groups over $F$ with the same root datum over $F_s$, for example the split group $SL_2$ and the norm-one group of a quaternion algebra, have the same dual group $PGL_2(\mathbb{C})$. The unitary group $U(n)$ and $GL_n$ have the same dual group $GL_n(\mathbb{C})$. Langlands repaired this in [Lan70] by adding the Galois group, or the Weil group, to the dual group. The result is the L-group ${}^L G = G^\vee \rtimes W_F$. The action of $W_F$ on $G^\vee$ comes from the action of the Galois group on the based root datum of $G$, transported to $G^\vee$ by the pinning. We follow [Bor79], Sections 1 and 2.

### The action of the Galois group on the dual group

Let $F$ be a field with separable closure $F_s$ and Galois group $\Gamma_F$, and let $G$ be a connected reductive group over $F$. Section 5.2 gives the homomorphism $\mu_G : \Gamma_F \to \mathrm{Aut}(\Psi_0(G))$. Fix a dual group $G^\vee$ with a pinning $(B^\vee, T^\vee, \{x_{\alpha^\vee}\})$ and an isomorphism $\Psi_0(G^\vee) \cong \Psi_0(G)^\vee$. By Proposition 5.1.12, the map $f \mapsto f^\vee = (f^{-1})^t$ is an isomorphism $\mathrm{Aut}(\Psi_0(G)) \to \mathrm{Aut}(\Psi_0(G)^\vee)$. By Theorem 5.2.3 part 1, the group $\mathrm{Aut}(\Psi_0(G^\vee))$ is the group of automorphisms of $G^\vee$ that preserve the pinning. The composite is a homomorphism
$$\mu^\vee : \Gamma_F \to \mathrm{Aut}(G^\vee, B^\vee, T^\vee, \{x_{\alpha^\vee}\}).$$
The kernel of $\mu_G$ is open, because $G$ splits over a finite extension of $F$ and the based root datum is constant over it. Let $E/F$ be the finite Galois extension that the kernel defines. If $G$ is quasi-split, $E$ is the smallest Galois extension over which $G$ splits. The action $\mu^\vee$ factors through $\mathrm{Gal}(E/F)$.

### The definition

Let $F$ be a local field or a global field, and let $W_F$ be its Weil group, as in Volume 0, Definition 3.1.1 in the local case and Volume 3, Chapter 7 in the global case. It comes with a continuous homomorphism $W_F \to \Gamma_F$ with dense image.

**Definition 5.4.1 (L-group).** The *L-group* of $G$ is the semidirect product
$${}^L G = G^\vee \rtimes W_F,$$
where $w \in W_F$ acts on $G^\vee$ by $\mu^\vee$ of its image in $\Gamma_F$. The multiplication is $(g_1, w_1)(g_2, w_2) = (g_1 \, \mu^\vee(w_1)(g_2), w_1 w_2)$. The *Galois form* of the L-group is $G^\vee \rtimes \mathrm{Gal}(E/F)$, for a finite Galois extension $E/F$ such that $\mu^\vee$ factors through $\mathrm{Gal}(E/F)$. We give ${}^L G$ the product topology, with the complex topology on $G^\vee(\mathbb{C})$.

Lean: `Langlands.Groups.QuasiSplitDatum` and `Langlands.Groups.QuasiSplitDatum.dual`, for the datum of the L-group, `Langlands.Groups.QuasiSplitDatum.dual_split` for a split group, `Langlands.Groups.QuasiSplitDatum.dual_split_sl2` for $SL_2$, and `SemidirectProduct`, from Mathlib, for the underlying abstract group. For concrete dual groups: `Langlands.Groups.LGroup.PinnedLGroup` (Definition 5.4.14), `Langlands.Groups.LGroup.TorusLGroup` for a torus and `Langlands.Groups.LGroup.GLLGroup` for split $GL_n$ (Definition 5.4.12), and `Langlands.Groups.Unitary.UnitaryLGroup` for $U(n)$ (Proposition 5.4.19)

Borel uses the Galois form in [Bor79], Section 2, and the Weil form for the parameters. The Galois form is a complex algebraic group whose identity component is $G^\vee$. The Weil form is not algebraic, but the parameters of representations of $G(F)$ take values in it. For many statements the choice does not matter, because the Weil form maps onto the Galois form with kernel $W_E$. If $G$ is split, $\mu^\vee$ is trivial, and ${}^L G = G^\vee \times W_F$. In that case one often uses $G^\vee$ alone.

**Proposition 5.4.2 (independence of the choices).** Let $(G^\vee_1, \mathcal{P}_1)$ and $(G^\vee_2, \mathcal{P}_2)$ be two dual groups of $G$ with pinnings and with identifications of their based root data with $\Psi_0(G)^\vee$. Then there is a unique isomorphism ${}^L G_1 \to {}^L G_2$ of the two L-groups that is the identity on $W_F$ and restricts to an isomorphism of pinned groups $G^\vee_1 \to G^\vee_2$ compatible with the identifications. If $\mathcal{P}' = \mathrm{Int}(g)(\mathcal{P})$ is another pinning of $G^\vee_1$, with $g \in G^\vee_1$, then the map $(h, w) \mapsto (g h g^{-1}, w)$ is an isomorphism from the L-group of $\mathcal{P}$ to the L-group of $\mathcal{P}'$.

Lean: not stated yet

*Proof.* By Theorem 5.2.3 part 1, there is a unique isomorphism of pinned groups $\phi : G_1^\vee \to G_2^\vee$ that induces the given map on based root data. Uniqueness shows that $\phi$ intertwines the two actions $\mu_1^\vee$ and $\mu_2^\vee$, since both $\phi \circ \mu_1^\vee(\sigma) \circ \phi^{-1}$ and $\mu_2^\vee(\sigma)$ preserve $\mathcal{P}_2$ and induce the same automorphism of $\Psi_0(G)^\vee$. So $(h, w) \mapsto (\phi(h), w)$ is an isomorphism. For the second statement, the action for $\mathcal{P}'$ is $\mu'(\sigma) = \mathrm{Int}(g) \circ \mu^\vee(\sigma) \circ \mathrm{Int}(g)^{-1}$, by the same uniqueness. Then
$$(g h_1 g^{-1}) \, \mu'(w_1)(g h_2 g^{-1}) = g \, h_1 \, \mu^\vee(w_1)(h_2) \, g^{-1},$$
which shows that the map is a homomorphism. $\square$

So the L-group is well defined up to an isomorphism that is unique up to conjugation by $G^\vee$. Statements on conjugacy classes of homomorphisms into ${}^L G$, such as the local Langlands conjecture of Section 5.6, do not depend on any choice.

**Proposition 5.4.3 (inner forms).** If $G$ and $G'$ are inner forms of each other over $F$, then $\mu_G = \mu_{G'}$ under an isomorphism $\Psi_0(G) \cong \Psi_0(G')$, and ${}^L G \cong {}^L G'$. Every connected reductive group $G$ has a unique quasi-split inner form $G^*$, and ${}^L G = {}^L G^*$.

Lean: not stated yet

*Outline of the proof.* An inner twist $\psi : G_{F_s} \to G'_{F_s}$ satisfies $\psi^{-1} \circ \sigma(\psi) = \mathrm{Int}(g_\sigma)$ for each $\sigma \in \Gamma_F$. Inner automorphisms act trivially on the canonical based root datum, by Proposition 5.2.4. So the map $\Psi_0(G) \to \Psi_0(G')$ induced by $\psi$ commutes with the Galois actions. The existence and uniqueness of the quasi-split inner form are in Chapter 3, and in [Spr98], Chapter 16. $\square$

For this reason the L-group carries only the information of the quasi-split inner form. The difference between $G$ and $G^*$ enters the local Langlands conjecture through the condition of relevance in Section 5.6, and through the refinements of Remark 5.6.8.

### Tori

Let $T$ be a torus over $F$. Then $\Psi_0(T) = (X^*(T), \emptyset, X_*(T), \emptyset)$, and $\Gamma_F$ acts on $X^*(T)$ as in Theorem 1.4.10. The dual torus $T^\vee = X^*(T) \otimes \mathbb{C}^\times$ has character group $X_*(T)$, and $\Gamma_F$ acts on it through the action on $X^*(T)$. A torus has no roots, so every automorphism preserves the pinning, and $\mu^\vee(\sigma) = \sigma \otimes 1$ on $X^*(T) \otimes \mathbb{C}^\times$. Thus
$${}^L T = T^\vee \rtimes W_F, \qquad T^\vee = X^*(T) \otimes \mathbb{C}^\times,$$
and $T^\vee$ is the dual torus of Volume 3, Definition 4.5.1.

**Example 5.4.4 (the norm-one torus).** Let $E/F$ be a separable quadratic extension with Galois group $\{1, \sigma\}$, and let $T = U(1) = \ker(N : R_{E/F} \mathbb{G}_m \to \mathbb{G}_m)$, so that $T(F) = \{ z \in E^\times : z \bar z = 1 \}$. Over $E$, $T$ becomes $\mathbb{G}_m$, and $X^*(T) = \mathbb{Z}$ with $\sigma$ acting by $-1$, as in Example 1.4.11 for $\mathbb{R}$. So $T^\vee = \mathbb{C}^\times$, and $W_F$ acts through $\mathrm{Gal}(E/F)$ by $\sigma(z) = z^{-1}$. The L-group is ${}^L U(1) = \mathbb{C}^\times \rtimes W_F$. Its Galois form is $\mathbb{C}^\times \rtimes \mathbb{Z}/2 \cong O_2(\mathbb{C})$. For the induced torus $R_{E/F} \mathbb{G}_m$, the character group is $\mathbb{Z}^2$ with $\sigma$ exchanging the coordinates, so the dual torus is $(\mathbb{C}^\times)^2$ with $\sigma$ exchanging the factors.

Lean: `Langlands.Groups.QuasiSplitDatum.torus` and `Langlands.Groups.QuasiSplitDatum.torus_dual_action_weightMap`, for the action on $X^*(T^\vee)$

### Unitary groups

Let $E/F$ be a separable quadratic extension with Galois group $\{1, \sigma\}$, write $\bar x = \sigma(x)$, and let $n \ge 2$. Let $\Phi_n$ be the $n \times n$ antidiagonal matrix with entries $(\Phi_n)_{i, n+1-i} = (-1)^{i+1}$. Then ${}^t \bar\Phi_n = (-1)^{n+1} \Phi_n$, and after multiplying by a suitable element of $E^\times$ we get a hermitian or skew-hermitian form $h$ on $E^n$. Let $U(n) = \{ g \in R_{E/F} GL_n : {}^t \bar g h g = h \}$. This is the quasi-split unitary group in $n$ variables. Its diagonal torus consists of the matrices $\mathrm{diag}(t_1, \dots, t_n)$ with $t_i \bar t_{n+1-i} = 1$, and the upper triangular matrices form a Borel subgroup over $F$.

Over $E$, the map $U(n)_E \to GL_{n, E}$ that sends $g$ to its first component in $R_{E/F} GL_n \times_F E \cong GL_n \times GL_n$ is an isomorphism. The Galois action that it induces on $GL_n(F_s)$ is $g \mapsto h^{-1} \, {}^t \sigma(g)^{-1} h$. On the diagonal torus this sends $\mathrm{diag}(t_1, \dots, t_n)$ to $\mathrm{diag}(\sigma(t_n)^{-1}, \dots, \sigma(t_1)^{-1})$. So on $X^*(T) = \mathbb{Z}^n$ the element $\sigma$ acts by $e_i \mapsto -e_{n+1-i}$, which preserves the base $\{e_i - e_{i+1}\}$ and is the nontrivial automorphism of the Dynkin diagram $A_{n-1}$.

**Proposition 5.4.5 (the L-group of a unitary group).** Let $U(n)$ be the quasi-split unitary group of $E/F$. Then $U(n)^\vee = GL_n(\mathbb{C})$ with its standard pinning, and $w \in W_F$ acts trivially if $w \in W_E$ and by
$$\theta(g) = \Phi_n \, {}^t g^{-1} \, \Phi_n^{-1}$$
if $w \notin W_E$. So ${}^L U(n) = GL_n(\mathbb{C}) \rtimes W_F$, with $W_F$ acting through $\mathrm{Gal}(E/F)$ by $\theta$.

Lean: `Langlands.Groups.Unitary.theta`, `Langlands.Groups.Unitary.theta_theta`, `Langlands.Groups.Unitary.theta_torusHom`, `Langlands.Groups.Unitary.theta_rootElement_of_mem`, `Langlands.Groups.Unitary.map_theta_upperBorel` and `Langlands.Groups.Unitary.LUnitary`, for the group $GL_n(\mathbb{C}) \rtimes \Gamma$ and the properties of $\theta$ (Propositions 5.4.18 and 5.4.19). The identification of $U(n)^\vee$ with $GL_n(\mathbb{C})$ is not stated

*Proof.* By Example 5.3.1 the dual group is $GL_n(\mathbb{C})$, with $e_i^\vee$ in $X_*(T) = X^*(T^\vee)$ the $i$-th diagonal character. The element $\sigma$ acts on $X^*(T)$ by $e_i \mapsto -e_{n+1-i}$, so its inverse transpose acts on $X_*(T)$ by $e_i^\vee \mapsto -e_{n+1-i}^\vee$. The automorphism $\theta$ preserves the diagonal torus and acts on it by $\mathrm{diag}(t_1, \dots, t_n) \mapsto \mathrm{diag}(t_n^{-1}, \dots, t_1^{-1})$, which is this map. Exercise 6 shows that $\theta$ preserves the upper triangular Borel subgroup and the standard pinning $x_{\alpha_i}(a) = 1 + a E_{i, i+1}$. By Theorem 5.2.3 part 1, $\theta$ is the pinned automorphism of $GL_n(\mathbb{C})$ attached to $\sigma$. $\square$

The group $GL_n(\mathbb{C}) \rtimes \mathrm{Gal}(E/F)$ is the Galois form. The restriction of an L-parameter of $U(n)$ to $W_E$ is a homomorphism $W_E \to GL_n(\mathbb{C})$, that is, an $n$-dimensional representation of $W_E$. This is the starting point of the base change from $U(n)$ to $GL_n$ over $E$, which is one of the main tools in the work of Harris and Taylor on the local Langlands conjecture for $GL_n$.

### Even orthogonal groups

Let $n \ge 2$ and let $q$ be a nondegenerate quadratic form on $F^{2n}$, in characteristic not $2$, whose orthogonal group is quasi-split. Let $d \in F^\times / F^{\times 2}$ be the discriminant of $q$, normalized so that $d = 1$ for the split form, and let $E = F(\sqrt d)$. If $E = F$, then $SO(q)$ is the split group $SO_{2n}$. If $E \ne F$, then $SO(q)$ is quasi-split and not split, it splits over $E$, and $\sigma \in \mathrm{Gal}(E/F)$ acts on $\Psi_0$ by the automorphism of $D_n$ that exchanges the two simple roots $e_{n-1} - e_n$ and $e_{n-1} + e_n$, that is, by $e_n \mapsto -e_n$. The dual automorphism of $SO_{2n}(\mathbb{C})$ is conjugation by an element of $O_{2n}(\mathbb{C})$ of determinant $-1$ that preserves the pinning. So the Galois form of the L-group is
$$SO_{2n}(\mathbb{C}) \rtimes \mathrm{Gal}(E/F) \cong O_{2n}(\mathbb{C}).$$
This is why the parameters of the quasi-split even orthogonal groups are orthogonal representations of $W_F \times SL_2(\mathbb{C})$ of dimension $2n$ whose determinant is the quadratic character of $E/F$.

### Restriction of scalars

Let $E/F$ be a finite separable extension of degree $d$ and let $H$ be a connected reductive group over $E$. Let $G = R_{E/F} H$ be the restriction of scalars. Over $F_s$ we have $G_{F_s} \cong \prod_\tau H \times_{E, \tau} F_s$, where $\tau$ runs over the $d$ embeddings $E \to F_s$ over $F$. So $G^\vee = \prod_\tau H^\vee$ is a product of $d$ copies of $H^\vee$, and $\Gamma_F$ permutes the factors through its action on the embeddings, combined with the action of $\Gamma_E$ on $H^\vee$. In other words, ${}^L G$ is induced from ${}^L H$:
$$G^\vee = \mathrm{Ind}_{W_E}^{W_F} H^\vee, \qquad {}^L G = (\mathrm{Ind}_{W_E}^{W_F} H^\vee) \rtimes W_F.$$
*Shapiro's lemma* for L-parameters says that restriction to $W_E$ and projection to one factor give a bijection between the $G^\vee$-conjugacy classes of L-parameters of $G$ over $F$ and the $H^\vee$-conjugacy classes of L-parameters of $H$ over $E$. This matches $G(F) = H(E)$. Borel proves it in [Bor79]. For $H = \mathbb{G}_m$, this is Volume 3, Theorem 4.5.4 for induced tori.

### L-homomorphisms

**Definition 5.4.6 (L-homomorphism).** Let $G$ and $H$ be connected reductive groups over $F$. An *L-homomorphism* is a continuous homomorphism $\eta : {}^L H \to {}^L G$ that commutes with the projections to $W_F$ and whose restriction to $H^\vee$ is a homomorphism of complex algebraic groups $H^\vee \to G^\vee$.

The principle of functoriality, stated in Volume 0, Conjecture 2.3.3, says that each L-homomorphism should give a transfer of automorphic representations from $H$ to $G$, compatible with L-functions. Here are the basic examples.

**Example 5.4.7 (L-homomorphisms).**
1. *Representations of the L-group.* An L-homomorphism ${}^L G \to {}^L GL_m = GL_m(\mathbb{C}) \times W_F$ is a representation $r : {}^L G \to GL_m(\mathbb{C})$ whose restriction to $G^\vee$ is algebraic. These representations define the automorphic L-functions $L(s, \pi, r)$, see Section 5.5.
2. *Symmetric powers.* $PGL_2^\vee = SL_2(\mathbb{C})$, and the symmetric power $\mathrm{Sym}^{m-1} : SL_2(\mathbb{C}) \to GL_m(\mathbb{C})$ gives an L-homomorphism ${}^L PGL_2 \to {}^L GL_m$. The transfer it predicts is the symmetric power lift from $GL_2$ to $GL_m$. It is known for $m = 3$ by Gelbart and Jacquet, for $m = 4$ by Kim and Shahidi, and for $m = 5$ by Kim. For the cusp forms attached to holomorphic newforms over $\mathbb{Q}$, Newton and Thorne proved it for all $m$.
3. *Classical groups.* $SO_{2n+1}^\vee = Sp_{2n}(\mathbb{C}) \subset GL_{2n}(\mathbb{C})$ and $Sp_{2n}^\vee = SO_{2n+1}(\mathbb{C}) \subset GL_{2n+1}(\mathbb{C})$. These inclusions give L-homomorphisms ${}^L SO_{2n+1} \to {}^L GL_{2n}$ and ${}^L Sp_{2n} \to {}^L GL_{2n+1}$. The transfers along them are the basis of Arthur's classification of the representations of the quasi-split classical groups.
4. *Base change.* For a finite separable extension $E/F$, the diagonal map $G^\vee \to \prod_\tau G^\vee$ gives an L-homomorphism ${}^L G \to {}^L R_{E/F} G_E$. By Shapiro's lemma it corresponds to the restriction of parameters from $W_F$ to $W_E$.
5. *Central isogenies.* A central isogeny $G_1 \to G_2$ defined over $F$ gives a dual isogeny $G_2^\vee \to G_1^\vee$ by Proposition 5.2.7, and it commutes with the Galois actions. So it gives an L-homomorphism ${}^L G_2 \to {}^L G_1$. For $SL_2 \to PGL_2$, this is ${}^L PGL_2 = SL_2(\mathbb{C}) \times W_F \to PGL_2(\mathbb{C}) \times W_F = {}^L SL_2$. It corresponds to the restriction of representations from $PGL_2(F)$, or from $GL_2(F)$, to the image of $SL_2(F)$.

**Remark 5.4.8 (the L-group in Lean).** The Lean file `Langlands/Groups/RootDatum.lean` gives the datum of the L-group as `Langlands.Groups.QuasiSplitDatum.dual`. This is the dual based root datum, with the action $\gamma \mapsto \mu_G(\gamma)^\vee = (\mu_G(\gamma)^{-1})^t$ of Proposition 5.1.12. The datum is formal and combinatorial. For a general $G$, the complex group $G^\vee$ and the semidirect product ${}^L G$ need the existence part of Theorem 5.2.1 over $\mathbb{C}$, and Mathlib does not have it. The project builds ${}^L G$ in three special cases: for a torus, for $G$ simply connected with $G^\vee$ the adjoint Chevalley group, and for $U(n)$. The rest of this section gives these constructions, and Remarks 5.4.16 and 5.4.21 say what they cover.

### Pinned automorphisms of the adjoint Chevalley group

The rest of this section makes Definition 5.4.1 concrete in the cases where the dual group can be written down by hand. The first case is the adjoint group. We use the adjoint Chevalley group $E_{ad}(\Phi, k)$ of Section 3.6 and its realization by Geck's construction, and we make the automorphisms of the based root system act on it. This is part 1 of Theorem 5.2.3 for adjoint groups, proved by an explicit formula.

Let $k$ be a field of characteristic $0$, and let $P$ be a reduced crystallographic root pairing over $k$, with roots $\alpha_j \in M$ and coroots $\alpha_j^\vee \in N$ indexed by a finite set $I$, and with a base $\Delta \subset I$. An *automorphism* of $P$ is a triple $g = (g_M, g_N, \sigma_g)$ of a linear automorphism $g_M$ of $M$, a linear automorphism $g_N$ of $N$ and a permutation $\sigma_g$ of $I$ with $g_M(\alpha_j) = \alpha_{\sigma_g(j)}$, $g_N(\alpha_j^\vee) = \alpha_{\sigma_g(j)}^\vee$ and $\langle g_M m, g_N n \rangle = \langle m, n \rangle$. We write $g(j) = \sigma_g(j)$.

**Definition 5.4.9 (automorphisms that keep a base).** The group $\mathrm{Aut}(P, \Delta)$ is the subgroup of the automorphisms $g$ of $P$ with $g(\Delta) = \Delta$. An element $g$ of $\mathrm{Aut}(P, \Delta)$ gives a permutation of $\Delta$, and a permutation $\tilde g$ of the disjoint union $\Delta \sqcup I$ that is $g$ on each part.

Lean: `Langlands.Groups.Pinned.baseAut`, `Langlands.Groups.Pinned.supportEquiv`, `Langlands.Groups.Pinned.blockEquiv`

**Lemma 5.4.10 (invariants of an automorphism).** Let $g$ be an automorphism of $P$ and let $i, j \in I$.
1. $\langle \alpha_{g(i)}, \alpha_{g(j)}^\vee \rangle = \langle \alpha_i, \alpha_j^\vee \rangle$.
2. $\alpha_{g(i)} + \alpha_{g(j)}$ is a root if and only if $\alpha_i + \alpha_j$ is a root, and the same holds for the difference. The $\alpha_{g(i)}$-string through $\alpha_{g(j)}$ has the same lengths above and below $\alpha_{g(j)}$ as the $\alpha_i$-string through $\alpha_j$.
3. If the roots span $M$ and $g(j) = j$ for all $j \in I$, then $g = 1$.

Lean: `Langlands.Groups.Pinned.pairingIn_indexEquiv`, `Langlands.Groups.Pinned.root_indexEquiv_eq_add_iff`, `Langlands.Groups.Pinned.root_indexEquiv_eq_sub_iff`, `Langlands.Groups.Pinned.chainTopCoeff_indexEquiv`, `Langlands.Groups.Pinned.chainBotCoeff_indexEquiv`, `Langlands.Groups.Pinned.eq_one_of_indexEquiv`

*Proof.* Part 1 is the invariance of the pairing: $\langle g_M \alpha_i, g_N \alpha_j^\vee \rangle = \langle \alpha_i, \alpha_j^\vee \rangle$. For part 2, $g_M$ is linear and permutes the roots, so $\alpha_i + \alpha_j = \alpha_l$ if and only if $\alpha_{g(i)} + \alpha_{g(j)} = \alpha_{g(l)}$. The same argument applies to $\alpha_j + r \alpha_i$ for each integer $r$, so $g_M$ maps the $\alpha_i$-string through $\alpha_j$ bijectively onto the $\alpha_{g(i)}$-string through $\alpha_{g(j)}$ and keeps the position of each term. For part 3, $g_M$ fixes each root, so it is the identity on the span of the roots, which is $M$. The pairing is perfect, and $\langle m, g_N n \rangle = \langle g_M^{-1} m, n \rangle = \langle m, n \rangle$ for all $m$, so $g_N = 1$. $\square$

Recall from Remark 3.6.19 how the Lean project realizes the adjoint Chevalley group. Geck's construction [Geck, *Proc. Amer. Math. Soc.* 145 (2017)] gives the Lie algebra $\mathfrak{g}$ of $P$ as a Lie algebra of square matrices with rows and columns indexed by $\Delta \sqcup I$. It is the Lie subalgebra generated by three families of matrices $e_i$, $f_i$, $h_i$ for $i \in \Delta$. The matrix $h_i$ is diagonal, with the entry $\langle \alpha_j, \alpha_i^\vee \rangle$ at $j \in I$ and $0$ on $\Delta$. The entries of $e_i$ and $f_i$ depend only on the Cartan integers, on whether $\alpha_j \pm \alpha_i$ is a root and on the lengths of the $\alpha_i$-strings through the roots. The elementary group $E(k)$ is generated by $x_{\alpha_i}(t) = \exp(t \, \mathrm{ad}\, e_i)$ and $x_{-\alpha_i}(t) = \exp(t \, \mathrm{ad}\, f_i)$. The torus element $h(\chi)$, for $\chi \in \mathrm{Hom}(\mathbb{Z}\Phi, k^\times)$, is conjugation by the diagonal matrix with the entry $1$ on $\Delta$ and $\chi(\alpha_j)$ at $j \in I$. The *adjoint Chevalley group* $G(k)$ is the subgroup of $\mathrm{Aut}(\mathfrak{g})$ generated by the elements $h(\chi)$ and the root elements $x_\beta(t)$ for all $\beta \in \Phi$.

**Proposition 5.4.11 (pinned automorphisms).** Let $g \in \mathrm{Aut}(P, \Delta)$, and let $\varphi_g$ be the reindexing of the matrices by $\tilde g$, that is, $\varphi_g(A)_{\tilde g(x), \tilde g(y)} = A_{x, y}$.
1. $\varphi_g(e_i) = e_{g(i)}$, $\varphi_g(f_i) = f_{g(i)}$ and $\varphi_g(h_i) = h_{g(i)}$ for $i \in \Delta$. So $\varphi_g$ is an automorphism of $\mathfrak{g}$, and $g \mapsto \varphi_g$ is a group homomorphism $\mathrm{Aut}(P, \Delta) \to \mathrm{Aut}(\mathfrak{g})$.
2. For $i \in \Delta$ and $t \in k$, $\varphi_g \, x_{\alpha_i}(t) \, \varphi_g^{-1} = x_{\alpha_{g(i)}}(t)$ and $\varphi_g \, x_{-\alpha_i}(t) \, \varphi_g^{-1} = x_{-\alpha_{g(i)}}(t)$.
3. For $\chi \in \mathrm{Hom}(\mathbb{Z}\Phi, k^\times)$, $\varphi_g \, h(\chi) \, \varphi_g^{-1} = h(\chi \circ g_M^{-1})$.
4. Conjugation by $\varphi_g$ maps $E(k)$ onto $E(k)$ and $G(k)$ onto $G(k)$. So $\mathrm{Aut}(P, \Delta)$ acts on $G(k)$ and on $E(k)$ by group automorphisms, and the action keeps the pinning $\{x_{\alpha_i}\}_{i \in \Delta}$.

Lean: `Langlands.Groups.Pinned.pinnedAut`, `Langlands.Groups.Pinned.pinnedAut_geckE`, `Langlands.Groups.Pinned.pinnedAut_geckF`, `Langlands.Groups.Pinned.pinnedAut_geckH`, `Langlands.Groups.Pinned.map_reindex_lieAlgebra`, `Langlands.Groups.Pinned.pinnedAut_mul_simpleRootElement_mul_inv`, `Langlands.Groups.Pinned.pinnedAut_mul_negSimpleRootElement_mul_inv`, `Langlands.Groups.Pinned.pinnedAut_mul_torusHom_mul_inv`, `Langlands.Groups.Pinned.pinnedAut_conj_mem_elementary`, `Langlands.Groups.Pinned.pinnedAut_conj_mem_adjoint`, `Langlands.Groups.Pinned.adjointAction`, `Langlands.Groups.Pinned.elementaryAction`

*Proof.* 1. Reindexing by a permutation is conjugation by a permutation matrix, so it is an automorphism of the Lie algebra of all matrices. The entry of $\varphi_g(e_i)$ at $(\tilde g(x), \tilde g(y))$ is the entry of $e_i$ at $(x, y)$. By Lemma 5.4.10 the data that define this entry (the Cartan integers, the root conditions and the string lengths) are the same for $(i, x, y)$ and for $(g(i), \tilde g(x), \tilde g(y))$. So $\varphi_g(e_i) = e_{g(i)}$, and the same argument works for $f_i$ and $h_i$. Hence $\varphi_g$ permutes the generators of $\mathfrak{g}$, and it maps $\mathfrak{g}$ onto $\mathfrak{g}$. Since $\widetilde{gg'} = \tilde g \tilde g'$, the map $g \mapsto \varphi_g$ is a homomorphism.

2. For an automorphism $\varphi$ of $\mathfrak{g}$ we have $\varphi \circ \mathrm{ad}(e) \circ \varphi^{-1} = \mathrm{ad}(\varphi(e))$. If $\mathrm{ad}(e)$ is nilpotent, then $\varphi \exp(t\, \mathrm{ad}\, e) \varphi^{-1} = \exp(t \, \mathrm{ad}\, \varphi(e))$, because both sides are the same finite sum. Apply this with $e = e_i$ and with $e = f_i$, and use part 1.

3. The element $h(\chi)$ is conjugation by the diagonal matrix $D_\chi$. Reindexing by $\tilde g$ takes $D_\chi$ to the diagonal matrix with the entry $\chi(\alpha_{g^{-1}(j)}) = \chi(g_M^{-1} \alpha_j)$ at $j \in I$ and $1$ on $\Delta$, which is $D_{\chi \circ g_M^{-1}}$. Here $g_M$ maps the root lattice $\mathbb{Z}\Phi$ onto itself. Conjugation by $\varphi_g$ on $\mathrm{Aut}(\mathfrak{g})$ is induced by reindexing, so the formula follows.

4. By part 2, conjugation by $\varphi_g$ permutes the generators of $E(k)$, so it maps $E(k)$ onto $E(k)$. By Proposition 5.4.13 part 2 below, $G(k) = T(k) E(k)$ with $T(k)$ the group of the elements $h(\chi)$. By part 3 conjugation by $\varphi_g$ maps $T(k)$ onto $T(k)$. So it maps $G(k)$ onto $G(k)$. $\square$

For the root system $A_2$, the group $\mathrm{Aut}(P, \Delta)$ has two elements, and the nontrivial element exchanges $\alpha_1$ and $\alpha_2$ and maps $\alpha_1 + \alpha_2$ to itself. The automorphism $\varphi_g$ exchanges $e_1$ and $e_2$, and the induced automorphism of $E(k) = PGL_3(k)$ is the outer automorphism of Proposition 5.4.18 below. This is Exercise 15.

### Split tori, root subgroups and the L-group of a torus

For a lattice $X$ and a commutative ring $R$, the *split torus* with the character lattice $X$ is $T_X(R) = \mathrm{Hom}(X, R^\times)$. An element $x \in X$ gives the character $t \mapsto t(x)$, and for a pairing $\langle \cdot, \cdot \rangle : X \times Y \to \mathbb{Z}$, an element $y \in Y$ gives the cocharacter $c \mapsto (x \mapsto c^{\langle x, y \rangle})$. So $T_X(\mathbb{C})$ is the group of complex points of the torus with the character group $X$, as in Section 1.4. The dual torus of a torus with the character lattice $X$ and the cocharacter lattice $Y$ is $T^\vee(\mathbb{C}) = T_Y(\mathbb{C}) = \mathrm{Hom}(Y, \mathbb{C}^\times)$, as in Proposition 5.1.12.

**Definition 5.4.12 (the L-group of the torus of a quasi-split datum).** Let $D$ be a quasi-split datum for a group $\Gamma$, with the root datum $(X, \Phi, Y, \Phi^\vee)$, and let $\gamma \mapsto \mu^\vee(\gamma)$ be the dual action of $\Gamma$ on $Y$ (Proposition 5.1.12). The group $\Gamma$ acts on $T_Y(R)$ by $(\gamma \cdot t)(y) = t(\mu^\vee(\gamma)^{-1} y)$. The *L-group of the torus* is the semidirect product $T_Y(R) \rtimes \Gamma$ for this action. For $R = \mathbb{C}$ and $\Gamma = W_F$ this is ${}^L T$ for the maximal torus $T$ of the quasi-split group of $D$. The *split L-group* of $GL_n$ is $GL_n(R) \rtimes \Gamma = GL_n(R) \times \Gamma$, with the trivial action.

Lean: `Langlands.Groups.SplitTorus`, `Langlands.Groups.SplitTorus.character`, `Langlands.Groups.SplitTorus.cocharacter`, `Langlands.Groups.SplitTorus.torusAction`, `Langlands.Groups.LGroup.dualTorusAction`, `Langlands.Groups.LGroup.TorusLGroup`, `Langlands.Groups.LGroup.GLLGroup`

**Proposition 5.4.13 (tori and root subgroups).**
1. Let $D$ be split, that is, $\Gamma$ acts trivially on $X$. Then $\Gamma$ acts trivially on $T_Y(R)$, and the L-group of the torus is the direct product $T_Y(R) \times \Gamma$. For $D$ the split datum of $GL_n$, the diagonal embedding $T_{\mathbb{Z}^n}(R) \to GL_n(R)$ gives an injective homomorphism from the L-group of the torus to the split L-group of $GL_n$.
2. In the adjoint Chevalley group $G(k)$ of a reduced crystallographic root system over a field of characteristic $0$, with $T(k) = \mathrm{Hom}(\mathbb{Z}\Phi, k^\times)$, the following hold. The map $T(k) \to G(k)$, $\chi \mapsto h(\chi)$, is injective. For each root $\beta$, the map $t \mapsto x_\beta(t)$ is an isomorphism from $(k, +)$ onto the root subgroup $U_\beta$, and $h(\chi) \, x_\beta(s) \, h(\chi)^{-1} = x_\beta(\chi(\beta) s)$. Each element of $G(k)$ is a product $h e$ with $h \in T(k)$ and $e \in E(k)$, and $E(k)$ is a normal subgroup of $G(k)$.
3. In $GL_n(R)$, with $x_{ij}(s) = 1 + s E_{ij}$ for $i \ne j$ and the diagonal torus $\mathrm{diag}(t_1, \dots, t_n)$, the following hold. $\mathrm{diag}(t) \, x_{ij}(s) \, \mathrm{diag}(t)^{-1} = x_{ij}(t_i t_j^{-1} s)$. If $i$, $j$, $l$ are distinct, then $x_{ij}(s) x_{jl}(t) x_{ij}(s)^{-1} x_{jl}(t)^{-1} = x_{il}(st)$. If $R$ is a field, then the diagonal torus and the elements $x_{ij}(s)$ generate $GL_n(R)$.

Lean: `Langlands.Groups.LGroup.dualTorusAction_eq_one`, `Langlands.Groups.LGroup.torusLGroupEquivProd`, `Langlands.Groups.LGroup.torusLGroupToGL_injective`, `Langlands.Groups.SplitAdjoint.torusHom_injective`, `Langlands.Groups.SplitAdjoint.rootSubgroupEquiv`, `Langlands.Groups.SplitAdjoint.torusHom_mul_rootElement_mul_inv`, `Langlands.Groups.SplitAdjoint.mem_adjointChevalleyGroup_iff`, `Langlands.Groups.SplitAdjoint.elementary_normal`, `Langlands.Groups.SplitGL.torusHom_mul_rootElement_mul_inv`, `Langlands.Groups.SplitGL.rootElement_commutator`, `Langlands.Groups.SplitGL.closure_torus_rootElement`

*Proof.* 1. If $\Gamma$ acts trivially on $X$, then the dual action on $Y$ is trivial, because it is the inverse transpose. So the action on $T_Y(R)$ is trivial, and a semidirect product with the trivial action is the direct product. For $GL_n$ the action on both sides is trivial, and the map $(t, \gamma) \mapsto (\mathrm{diag}(t), \gamma)$ is an injective homomorphism.

2. If $h(\chi) = 1$, then $\chi(\beta) = 1$ for every root $\beta$, because $h(\chi)$ acts on the root space of $\beta$ by $\chi(\beta)$. So $\chi = 1$ on $\mathbb{Z}\Phi$. The map $t \mapsto x_\beta(t) = \exp(t \, \mathrm{ad}\, e_\beta)$ is a homomorphism because $\mathrm{ad}(se_\beta)$ and $\mathrm{ad}(te_\beta)$ commute. It is injective because $x_\beta(t) e_{-\beta} = e_{-\beta} + t h_\beta + \cdots$ and $h_\beta \ne 0$. The conjugation formula is the argument of Proposition 5.4.11 part 2 with $h(\chi) e_\beta = \chi(\beta) e_\beta$. For the decomposition, the formula shows that $T(k)$ normalizes $E(k)$, so $T(k) E(k)$ is a subgroup. It contains the generators of $G(k)$, because $E(k)$ is generated by the simple root elements and contains every root subgroup, by Definition 3.6.11 and Corollary 3.6.14. So $G(k) = T(k) E(k)$, and $E(k)$ is normal because both $T(k)$ and $E(k)$ normalize it.

3. The first formula is the computation $\mathrm{diag}(t) E_{ij} \mathrm{diag}(t)^{-1} = t_i t_j^{-1} E_{ij}$. For the second, $E_{ij} E_{jl} = E_{il}$ and the other products of $E_{ij}$, $E_{jl}$, $E_{il}$ are $0$, so the product of the four factors is $1 + st E_{il}$. The last statement is Gaussian elimination: row and column operations with the matrices $x_{ij}(s)$ reduce each invertible matrix to a diagonal matrix. $\square$

Lean proves part 2 by a different route for the root subgroups that are not simple. It defines $x_\beta(t)$ for each root, with the root vector $e_\beta$ of the Geck construction, and $G(k)$ as the subgroup generated by $T(k)$ and all $x_\beta(t)$. The decomposition $G(k) = T(k) E(k)$ is the theorem `Langlands.Groups.SplitAdjoint.adjointChevalleyGroup_eq_sup`.

### The pinned L-group

Now let $k = \mathbb{C}$. Let $P$ be a reduced crystallographic root system over $\mathbb{C}$ with a base $\Delta$, and let $G(\mathbb{C})$ be its adjoint Chevalley group.

**Definition 5.4.14 (the pinned L-group).** Let $\Gamma$ be a group and let $\rho : \Gamma \to \mathrm{Aut}(P, \Delta)$ be a homomorphism. The group $\Gamma$ acts on $G(\mathbb{C})$ by $\gamma \cdot x = \varphi_{\rho(\gamma)} \, x \, \varphi_{\rho(\gamma)}^{-1}$ (Proposition 5.4.11). The *pinned L-group* of $\rho$ is the semidirect product $G(\mathbb{C}) \rtimes_\rho \Gamma$. Let $D$ be a quasi-split datum for $\Gamma$ with the same index set $I$. We say that $(P, \Delta, \rho)$ is a *dual pinning* for $D$ if the following hold.
1. $\Delta$ is the set of simple roots of the dual datum $D^\vee$.
2. $\langle \alpha_i, \alpha_j^\vee \rangle_P$ is the pairing of $\alpha_i$ and $\alpha_j^\vee$ in $D^\vee$, for all $i, j \in I$.
3. For each $\gamma \in \Gamma$, $\rho(\gamma)$ permutes $I$ as the dual action $\mu^\vee(\gamma)$ does.

Lean: `Langlands.Groups.LGroup.dualGroupAction`, `Langlands.Groups.LGroup.PinnedLGroup`, `Langlands.Groups.LGroup.IsDualPinning`

If $G$ is simply connected, then $G^\vee$ is adjoint, and over $\mathbb{C}$ it is the adjoint Chevalley group by Theorem 3.6.18. Then a dual pinning gives the L-group of Definition 5.4.1: the action of $\gamma$ is the pinned automorphism attached to $\mu^\vee(\gamma)$, as in Theorem 5.2.3 part 1.

**Proposition 5.4.15 (uniqueness and the split case).** Let $D$ be a quasi-split datum for $\Gamma$.
1. If $(P, \Delta, \rho)$ and $(P, \Delta, \rho')$ are dual pinnings for $D$, then $\rho = \rho'$.
2. If $(P, \Delta, \rho)$ is a dual pinning for $D$, then for $\gamma \in \Gamma$ and $i \in \Delta$, the element $\gamma$ maps $x_{\alpha_i}(t)$ to $x_{\alpha_j}(t)$, where $j$ is the image of $i$ under $\mu^\vee(\gamma)$.
3. If $D$ is split and $(P, \Delta, \rho)$ is a dual pinning, then $\rho = 1$ and the pinned L-group is the direct product $G(\mathbb{C}) \times \Gamma$.

Lean: `Langlands.Groups.LGroup.IsDualPinning.unique`, `Langlands.Groups.LGroup.IsDualPinning.dualGroupAction_simpleRootElement`, `Langlands.Groups.LGroup.IsDualPinning.eq_one`, `Langlands.Groups.LGroup.pinnedLGroupEquivProd`, `Langlands.Groups.LGroup.lGroupEquivProdOfIsSplit`

*Proof.* 1. Let $\gamma \in \Gamma$. By condition 3, $\rho(\gamma)$ and $\rho'(\gamma)$ permute $I$ in the same way, so $\rho(\gamma)^{-1} \rho'(\gamma)$ fixes each $j \in I$. The roots of a root system span $M$, so $\rho(\gamma)^{-1} \rho'(\gamma) = 1$ by Lemma 5.4.10 part 3. 2. This is Proposition 5.4.11 part 2 with condition 3. 3. If $D$ is split, the dual action is trivial, so each $\rho(\gamma)$ fixes each $j \in I$, and $\rho(\gamma) = 1$ by Lemma 5.4.10 part 3. With the trivial action the semidirect product is the direct product. $\square$

Part 1 is the uniqueness in Theorem 5.2.3 part 1, in this concrete form: a pinned automorphism is fixed by its permutation of the simple roots. Part 1 fails for root pairings whose roots do not span $M$, see Exercise 14.

**Remark 5.4.16 (the pinned L-group in Lean).** The file `Langlands/Groups/LGroup.lean` constructs the pinned automorphisms and the pinned L-group of Definitions 5.4.9 and 5.4.14. Mathlib's Geck construction has no functoriality, so the file defines $\varphi_g$ by reindexing and proves Proposition 5.4.11 by hand, with the invariance results of Lemma 5.4.10 in the section `Invariance` of the file. The file `Langlands/Groups/SplitReductive.lean` gives Definition 5.4.12 and Proposition 5.4.13. The following is not in Lean. (a) Mathlib has no extension of scalars for root pairings, so the root system over $\mathbb{C}$ of the dual datum $D^\vee$ is not built from $D$. The pinned L-group takes $(P, \Delta, \rho)$ as input, and `IsDualPinning` only compares it with $D^\vee$. (b) `IsDualPinning` compares the root systems and not the lattices. It does not check that $Y$ is the coroot lattice, that is, that $G$ is simply connected. For other $G$ the pinned L-group is the L-group of the simply connected cover of $G$, and not of $G$. (c) The identification of the adjoint Chevalley group with the group of complex points of the adjoint group, Theorem 3.6.18, is not in Lean, and the topology of ${}^L G$ is not considered. (d) For a general root datum there is no group $G(k)$ in the project. Only the torus and $GL_n$ are built. A Steinberg presentation would need the structure constants of the commutator relations.

### The unitary group in coordinates

We return to Proposition 5.4.5 and give its matrix computations in full. Let $n \ge 1$ and let $R$ be a commutative ring. We write $i' = n + 1 - i$ for $1 \le i \le n$, and $\varepsilon_i = (-1)^{i+1}$. Let $J = \Phi_n$ be the antidiagonal matrix with $J_{i, i'} = \varepsilon_i$, and define $\theta : GL_n(R) \to GL_n(R)$ by $\theta(g) = J \, ({}^t g)^{-1} J^{-1}$. Let $\sigma$ be the map $x \mapsto -(x_n, \dots, x_1)$ of $\mathbb{Z}^n$, so that $\sigma(e_i) = -e_{i'}$.

**Lemma 5.4.17 (the matrix $J$ and the involution $\theta$).**
1. $J \, {}^t J = {}^t J \, J = 1$, so $J^{-1} = {}^t J$.
2. $J^2 = (-1)^{n+1} \cdot 1$, and $\varepsilon_{i'} = (-1)^{n+1} \varepsilon_i$.
3. $\theta(g)_{ac} = \varepsilon_a \varepsilon_c \, (g^{-1})_{c', a'}$ for all $a, c$.
4. $\theta$ is a group automorphism of $GL_n(R)$ with $\theta \circ \theta = 1$.

Lean: `Langlands.Groups.Unitary.antiDiag`, `Langlands.Groups.Unitary.antiDiag_mul_transpose`, `Langlands.Groups.Unitary.antiDiag_transpose_mul`, `Langlands.Groups.Unitary.sign_rev`, `Langlands.Groups.Unitary.coe_theta`, `Langlands.Groups.Unitary.theta_apply`, `Langlands.Groups.Unitary.theta_theta`, `Langlands.Groups.Unitary.thetaAut_mul_self`

*Proof.* 1. $(J \, {}^t J)_{ac} = \sum_b J_{ab} J_{cb} = J_{a a'} J_{c a'}$, which is $0$ for $a \ne c$ and $\varepsilon_a^2 = 1$ for $a = c$. 2. $(J^2)_{aa} = J_{aa'} J_{a'a} = \varepsilon_a \varepsilon_{a'}$, and $\varepsilon_a \varepsilon_{a'} = (-1)^{a + 1 + n + 2 - a} = (-1)^{n+1}$. 3. For a matrix $B$, $(J B)_{ac} = \varepsilon_a B_{a', c}$ and $(B \, {}^t J)_{ac} = B_{a, c'} \varepsilon_c$. Apply this to $B = {}^t (g^{-1})$ and use part 1. 4. The map $g \mapsto ({}^t g)^{-1}$ is an automorphism, and so is conjugation by $J$. We have $\theta(\theta(g)) = J \, {}^t J^{-1} \, g \, {}^t J \, J^{-1} = J^2 g J^{-2}$ by part 1, and $J^2$ is central by part 2. $\square$

**Proposition 5.4.18 ($\theta$ is a pinned automorphism).**
1. $\theta(\mathrm{diag}(t_1, \dots, t_n)) = \mathrm{diag}(t_n^{-1}, \dots, t_1^{-1})$. So $\theta$ maps the diagonal torus onto itself, and on $\mathrm{Hom}(\mathbb{Z}^n, R^\times)$ it is $t \mapsto t \circ \sigma$.
2. For $i \ne j$, $\theta(x_{ij}(t)) = x_{j' i'}(-\varepsilon_i \varepsilon_j t)$. In particular $\theta(x_{i, i+1}(t)) = x_{n-i, n+1-i}(t)$ for $1 \le i < n$, so $\theta$ permutes the simple root elements as $\sigma$ permutes the simple roots.
3. $\theta$ maps the group of invertible upper triangular matrices onto itself.

Lean: `Langlands.Groups.Unitary.theta_torusHom`, `Langlands.Groups.Unitary.map_theta_range_torusHom`, `Langlands.Groups.Unitary.theta_rootElement`, `Langlands.Groups.Unitary.theta_rootElement_of_mem`, `Langlands.Groups.Unitary.outerIndex_mem_glSimple_iff`, `Langlands.Groups.Unitary.map_theta_upperBorel`

*Proof.* All three parts follow from Lemma 5.4.17 part 3. 1. For $g = \mathrm{diag}(t)$, $(g^{-1})_{c'a'}$ is $0$ unless $a = c$, and $\theta(g)_{aa} = t_{a'}^{-1}$. 2. For $g = x_{ij}(t)$, $g^{-1} = x_{ij}(-t)$. Its entry at $(c', a')$ off the diagonal is $-t$ if $c' = i$ and $a' = j$, that is $a = j'$ and $c = i'$, and $0$ otherwise. So $\theta(g) = 1 - \varepsilon_{j'} \varepsilon_{i'} t E_{j' i'}$, and $\varepsilon_{i'} \varepsilon_{j'} = \varepsilon_i \varepsilon_j$ by Lemma 5.4.17 part 2. For $j = i + 1$, $\varepsilon_i \varepsilon_j = -1$ and $(j', i') = (n - i, n + 1 - i)$. 3. If $g$ is upper triangular, so is $g^{-1}$, and $(g^{-1})_{c'a'} = 0$ for $c' > a'$, that is for $a > c$. So $\theta(g)$ is upper triangular. Since $\theta^2 = 1$, $\theta$ maps the group onto itself. $\square$

Part 2 gives the sign in the proof of Proposition 5.4.5: the signs $\varepsilon_i$ in $J$ are chosen so that $\theta$ maps $x_{\alpha_i}(t)$ to $x_{\alpha_{n-i}}(t)$ and not to $x_{\alpha_{n-i}}(-t)$. With the plain antidiagonal matrix of ones in place of $J$, $\theta$ is still an involution that keeps the torus and the Borel subgroup, but it does not keep the pinning. For $n = 2$, $J = \begin{pmatrix} 0 & 1 \\ -1 & 0 \end{pmatrix}$ and $\theta(g) = \det(g)^{-1} g$, so $\theta$ is trivial on $SL_2(\mathbb{C})$ (Exercise 6). This matches the fact that the quasi-split group $SU(2)$ is isomorphic to $SL_2$ over $F$, while $U(2)$ is not split, because its center $U(1)$ is anisotropic.

To state the L-group, let $\Gamma$ be a group with a homomorphism $\chi : \Gamma \to \mathbb{Z}/2$. For $\Gamma = W_F$ or $\Gamma = \Gamma_F$, the character $\chi$ has the kernel $W_E$ or $\Gamma_E$. The *quasi-split datum of $U(n)$* is the based root datum of $GL_n$, with $X = Y = \mathbb{Z}^n$, the roots $e_i - e_j$ and the base $\{e_i - e_{i+1}\}$, and with $\gamma$ acting by $\sigma$ if $\chi(\gamma) \ne 0$ and trivially otherwise. The map $\sigma$ keeps the base, because it maps $e_i - e_{i+1}$ to $e_{n-i} - e_{n+1-i}$, and $\sigma^2 = 1$.

**Proposition 5.4.19 (the L-group of $U(n)$).** Let $\Gamma$ act on $GL_n(R)$ by $\theta$ through $\chi$, and let ${}^L U(n) = GL_n(R) \rtimes \Gamma$.
1. On the diagonal torus, the action of $\gamma$ is the dual action of the datum of $U(n)$ of Definition 5.4.12. On the simple root elements, $\gamma$ maps $x_{i, i+1}(t)$ to $x_p(t)$, where $p$ is the image of $(i, i+1)$ under the dual action of $\gamma$ on the roots.
2. The diagonal embedding gives an injective homomorphism from the L-group of the torus of $U(n)$ to ${}^L U(n)$.
3. For $n \ge 1$, the datum of $U(n)$ is split if and only if $\chi = 1$. If $\chi = 1$, then ${}^L U(n) = GL_n(R) \times \Gamma$.

Lean: `Langlands.Groups.Unitary.glOuter`, `Langlands.Groups.Unitary.glOuter_mul_self`, `Langlands.Groups.Unitary.unitaryDatum`, `Langlands.Groups.Unitary.unitaryAction`, `Langlands.Groups.Unitary.UnitaryLGroup`, `Langlands.Groups.Unitary.LUnitary`, `Langlands.Groups.Unitary.unitaryAction_torusHom`, `Langlands.Groups.Unitary.unitaryAction_rootElement`, `Langlands.Groups.Unitary.torusLGroupToUnitary_injective`, `Langlands.Groups.Unitary.unitaryDatum_isSplit_iff`, `Langlands.Groups.Unitary.unitaryLGroupEquivProd`

*Proof.* 1. If $\chi(\gamma) = 0$, both actions are trivial. Otherwise $\gamma$ acts on $X$ by $\sigma$. The map $\sigma$ is its own inverse transpose, so $\gamma$ acts on $Y = \mathbb{Z}^n$ by $\sigma$, and on $\mathrm{Hom}(Y, R^\times)$ by $t \mapsto t \circ \sigma^{-1} = t \circ \sigma$. This is the action of $\theta$ by Proposition 5.4.18 part 1. On the roots, $\sigma$ maps $e_i - e_j$ to $e_{j'} - e_{i'}$, and Proposition 5.4.18 part 2 gives the claim for the simple roots. 2. By part 1 the diagonal embedding commutes with the actions of $\Gamma$, so $(t, \gamma) \mapsto (\mathrm{diag}(t), \gamma)$ is a homomorphism, and it is injective. 3. If $\chi(\gamma) \ne 0$ for some $\gamma$, then $\gamma$ maps $e_1$ to $-e_n \ne e_1$, so the action is not trivial. If $\chi = 1$, the action on $GL_n(R)$ is trivial and the semidirect product is the direct product. $\square$

**Example 5.4.20 ($n = 3$).** For $n = 3$, $J = \begin{pmatrix} 0 & 0 & 1 \\ 0 & -1 & 0 \\ 1 & 0 & 0 \end{pmatrix}$, and $J^2 = 1$. The root elements of the simple roots satisfy $\theta(x_{12}(t)) = x_{23}(t)$ and $\theta(x_{23}(t)) = x_{12}(t)$. For the highest root, $\varepsilon_1 \varepsilon_3 = 1$, so $\theta(x_{13}(t)) = x_{13}(-t)$. This sign is forced: $x_{13}(t)$ is the commutator of $x_{12}(t)$ and $x_{23}(1)$ by Proposition 5.4.13 part 3, and $\theta$ maps it to the commutator of $x_{23}(t)$ and $x_{12}(1)$, which is $x_{13}(-t)$. On the torus, $\theta(\mathrm{diag}(a, b, c)) = \mathrm{diag}(c^{-1}, b^{-1}, a^{-1})$. The fixed points of $\theta$ on the torus are the elements $\mathrm{diag}(a, \pm 1, a^{-1})$.

**Remark 5.4.21 (the unitary L-group in Lean).** The file `Langlands/Groups/LGroup.lean` proves Lemma 5.4.17 and Propositions 5.4.18 and 5.4.19 with the indices $0, \dots, n - 1$. There the sign is $\varepsilon_a = (-1)^a$ and $i'$ is $n - 1 - i$, which agrees with the text after the shift by one. The group $\Gamma$ and the character $\chi$ are general, so the file does not mention $E/F$. The following is not in Lean. The unitary group $U(n)$ is not defined as an algebraic group over $F$, and there is no hermitian form. So the computation of the Galois action on the root datum of $U(n)$ in the text before Proposition 5.4.5 is not in Lean, and `unitaryDatum` is a definition and not a theorem about $U(n)$. The Weil group is not used, and the L-homomorphisms of Definition 5.4.6, such as base change from $U(n)$ to $R_{E/F} GL_n$, are not stated.
