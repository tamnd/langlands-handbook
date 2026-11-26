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

Lean: `SemidirectProduct`, from Mathlib, for the underlying abstract group

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

### Unitary groups

Let $E/F$ be a separable quadratic extension with Galois group $\{1, \sigma\}$, write $\bar x = \sigma(x)$, and let $n \ge 2$. Let $\Phi_n$ be the $n \times n$ antidiagonal matrix with entries $(\Phi_n)_{i, n+1-i} = (-1)^{i+1}$. Then ${}^t \bar\Phi_n = (-1)^{n+1} \Phi_n$, and after multiplying by a suitable element of $E^\times$ we get a hermitian or skew-hermitian form $h$ on $E^n$. Let $U(n) = \{ g \in R_{E/F} GL_n : {}^t \bar g h g = h \}$. This is the quasi-split unitary group in $n$ variables. Its diagonal torus consists of the matrices $\mathrm{diag}(t_1, \dots, t_n)$ with $t_i \bar t_{n+1-i} = 1$, and the upper triangular matrices form a Borel subgroup over $F$.

Over $E$, the map $U(n)_E \to GL_{n, E}$ that sends $g$ to its first component in $R_{E/F} GL_n \times_F E \cong GL_n \times GL_n$ is an isomorphism. The Galois action that it induces on $GL_n(F_s)$ is $g \mapsto h^{-1} \, {}^t \sigma(g)^{-1} h$. On the diagonal torus this sends $\mathrm{diag}(t_1, \dots, t_n)$ to $\mathrm{diag}(\sigma(t_n)^{-1}, \dots, \sigma(t_1)^{-1})$. So on $X^*(T) = \mathbb{Z}^n$ the element $\sigma$ acts by $e_i \mapsto -e_{n+1-i}$, which preserves the base $\{e_i - e_{i+1}\}$ and is the nontrivial automorphism of the Dynkin diagram $A_{n-1}$.

**Proposition 5.4.5 (the L-group of a unitary group).** Let $U(n)$ be the quasi-split unitary group of $E/F$. Then $U(n)^\vee = GL_n(\mathbb{C})$ with its standard pinning, and $w \in W_F$ acts trivially if $w \in W_E$ and by
$$\theta(g) = \Phi_n \, {}^t g^{-1} \, \Phi_n^{-1}$$
if $w \notin W_E$. So ${}^L U(n) = GL_n(\mathbb{C}) \rtimes W_F$, with $W_F$ acting through $\mathrm{Gal}(E/F)$ by $\theta$.

Lean: not stated yet

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
