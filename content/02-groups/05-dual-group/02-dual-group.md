---
title: The dual group
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## The dual group

The isomorphism and existence theorems of Chapter 3 say that a split reductive group is determined by its root datum, and that every reduced root datum occurs. So the dual root datum of Section 5.1 defines a new reductive group, the dual group $G^\vee$. We take it over $\mathbb{C}$, because the representations of $G^\vee(\mathbb{C})$ and the semisimple conjugacy classes in it are the objects that the Langlands program attaches to automorphic data. The definition needs some care. The root datum depends on a choice of maximal torus, and to make $G^\vee$ depend only on $G$ we use the based root datum and pinnings. The pinnings also give a splitting of the group of automorphisms, which Section 5.4 needs to define the L-group. We follow [Bor79], Sections 1 and 2, and [Spr98], Chapters 9 and 10.

### The isomorphism and existence theorems

Let $k$ be a field. A *split reductive group* over $k$ is a pair $(G, T)$ of a connected reductive group $G$ over $k$ and a split maximal torus $T \subset G$. Chapter 3 attaches to it the reduced root datum $\Psi(G, T)$. An isomorphism $f : (G, T) \to (G', T')$ induces an isomorphism $\Psi(G', T') \to \Psi(G, T)$ by restriction of characters.

**Theorem 5.2.1 (isomorphism and existence).** Let $k$ be a field.
1. Let $(G, T)$ and $(G', T')$ be split reductive groups over $k$, and let $f : \Psi(G', T') \to \Psi(G, T)$ be an isomorphism of root data. Then there is an isomorphism $\phi : (G, T) \to (G', T')$ that induces $f$. If $\phi_1$ is another one, then $\phi_1 = \phi \circ \mathrm{Int}(t)$ for a unique $t \in T_{\mathrm{ad}}(k)$, where $T_{\mathrm{ad}} = T/Z(G)$ acts on $G$ by conjugation.
2. For each reduced root datum $\Psi$ there is a split reductive group $(G, T)$ over $k$ with $\Psi(G, T) \cong \Psi$.

Lean: not stated yet

*Outline of the proof.* Chapter 3 states this theorem. The proofs are in [Spr98], Chapter 9 for the isomorphism theorem, and Chapter 10 for the existence theorem. For $k$ algebraically closed, the existence theorem goes back to Chevalley, who built the groups from a Chevalley basis of the complex Lie algebra. For semisimple root data, one first builds the simply connected group and then takes the quotient by the subgroup of the centre that matches $X$. A reductive group is then a quotient of the product of a semisimple group and a torus by a finite central subgroup. See also [Mil17], Chapter 23. $\square$

The uniqueness in part 1 holds only up to $T/Z(G)$. To remove this ambiguity we fix more data.

### Pinnings

**Definition 5.2.2 (pinning).** Let $G$ be a connected reductive group over $k$. A *pinning* (French *épinglage*) of $G$ is a triple $(B, T, \{x_\alpha\}_{\alpha \in \Delta})$, where $T$ is a split maximal torus, $B \supset T$ is a Borel subgroup defined over $k$, $\Delta$ is the base of $\Psi(G, T)$ that $B$ defines, and for each $\alpha \in \Delta$, $x_\alpha : \mathbb{G}_a \to U_\alpha$ is an isomorphism onto the root subgroup of $\alpha$. A group with a pinning is *pinned*.

Lean: not stated yet

For $GL_n$ the *standard pinning* is the upper triangular Borel subgroup $B$, the diagonal torus $T$, and the maps $x_{\alpha_i}(a) = 1 + a E_{i, i+1}$ for the simple roots $\alpha_i = e_i - e_{i+1}$, where $E_{i,j}$ is the elementary matrix. Its restriction to $SL_n$ is the standard pinning of $SL_n$, and its image in $PGL_n$ is the standard pinning of $PGL_n$.

Each choice $x_\alpha$ of the isomorphism is unique up to the action of $\mathbb{G}_m$ by $a \mapsto ca$. The torus $T$ acts on $U_\alpha$ by $\alpha$, so $\mathrm{Int}(t) \circ x_\alpha = x_\alpha(\alpha(t) \, \cdot)$. If $G$ is split, any two pinnings are conjugate under $G(k)$, by the conjugacy of split maximal tori and of Borel subgroups over $k$, and since the simple roots are linearly independent in $X^*(T/Z(G))$. More precisely, the group $G_{\mathrm{ad}}(k) = (G/Z(G))(k)$ acts simply transitively on the set of pinnings.

**Theorem 5.2.3 (automorphisms of a pinned group).** Let $G$ be a split reductive group with a pinning $(B, T, \{x_\alpha\})$, and let $\Psi_0 = \Psi_0(G, B, T)$ be its based root datum.
1. Restriction to $T$ gives an isomorphism from the group of automorphisms of $G$ that preserve the pinning onto $\mathrm{Aut}(\Psi_0)$.
2. There is a split exact sequence
$$1 \to G_{\mathrm{ad}}(k) \to \mathrm{Aut}(G) \to \mathrm{Aut}(\Psi_0) \to 1,$$
where the first map is $g \mapsto \mathrm{Int}(g)$, and the splitting is the subgroup of automorphisms that preserve the pinning.

Lean: not stated yet

*Outline of the proof.* An automorphism that preserves the pinning induces an automorphism of $\Psi(G, T)$ that preserves $\Delta$. Conversely, by Theorem 5.2.1 part 1 an element $f \in \mathrm{Aut}(\Psi_0)$ lifts to an automorphism $\phi$ of $(G, T)$, which is unique up to $\mathrm{Int}(t)$ with $t \in T_{\mathrm{ad}}(k)$. The automorphism $\phi$ maps $B$ to the Borel subgroup of the base $f^{-1}(\Delta) = \Delta$, so $\phi(B) = B$. Then $\phi \circ x_\alpha = x_{f^{-1}\alpha}(c_\alpha \, \cdot)$ with $c_\alpha \in k^\times$. The simple roots form a basis of $X^*(T_{\mathrm{ad}})$, so there is a unique $t \in T_{\mathrm{ad}}(k)$ with $\alpha(t) = c_\alpha^{-1}$ for each $\alpha$, after we re-index. So $\phi \circ \mathrm{Int}(t)$ preserves the pinning, and it is the only lift that does. This proves part 1. For part 2, an automorphism $\phi$ of $G$ maps the pinning to another pinning, which is the image of the first under a unique $\mathrm{Int}(g)$ with $g \in G_{\mathrm{ad}}(k)$. Then $\mathrm{Int}(g)^{-1} \circ \phi$ preserves the pinning. An inner automorphism that preserves the pinning is trivial, so the kernel of the map to $\mathrm{Aut}(\Psi_0)$ is $G_{\mathrm{ad}}(k)$. The details are in [Spr98], Chapter 16, and [Mil17], Chapter 23. $\square$

The group $\mathrm{Out}(G) = \mathrm{Aut}(G) / G_{\mathrm{ad}}(k)$ is thus $\mathrm{Aut}(\Psi_0)$. For $G = SL_n$ with $n \ge 3$, the pinned automorphism of order two is $\theta(g) = J \, {}^t g^{-1} J^{-1}$, where $J$ is the antidiagonal matrix with entries $J_{i, n+1-i} = (-1)^{i+1}$. Exercise 6 checks that $\theta$ preserves the standard pinning.

### The canonical based root datum

Let $G$ be a connected reductive group over an algebraically closed field. For each pair $T \subset B$ of a maximal torus and a Borel subgroup we have the based root datum $\Psi_0(G, B, T)$. If $(B', T')$ is another pair, then by Theorem 1.6.8 there is $g \in G$ with $g B g^{-1} = B'$ and $g T g^{-1} = T'$, and $\mathrm{Int}(g)$ gives an isomorphism $\Psi_0(G, B', T') \to \Psi_0(G, B, T)$.

**Proposition 5.2.4 (the canonical based root datum).** The isomorphism $\Psi_0(G, B', T') \to \Psi_0(G, B, T)$ induced by $\mathrm{Int}(g)$ does not depend on the choice of $g$. So the based root data of the pairs $(B, T)$ form a system of isomorphic objects with unique transition isomorphisms, and they define one based root datum $\Psi_0(G)$, the *canonical based root datum* of $G$.

Lean: not stated yet

*Proof.* Let $g_1$ be another element with the same property. Then $n = g^{-1} g_1$ normalizes $B$ and $T$. By Theorem 1.6.8, $N_G(B) = B$, so $n \in B \cap N_G(T)$. An element of $N_G(T) \cap B$ acts on $T$ by an element of the Weyl group that preserves the positive roots, and only the identity does that. So $n \in C_G(T) = T$, and $\mathrm{Int}(n)$ acts trivially on $X^*(T)$. $\square$

If $G$ is defined over a field $F$ with separable closure $F_s$, and we compute $\Psi_0(G)$ over $F_s$, then the Galois group $\Gamma_F = \mathrm{Gal}(F_s/F)$ acts on $\Psi_0(G)$. For $\sigma \in \Gamma_F$ the pair $(\sigma B, \sigma T)$ has the based root datum transported by $\sigma$, and Proposition 5.2.4 identifies it with $\Psi_0(G)$. This gives a homomorphism
$$\mu_G : \Gamma_F \to \mathrm{Aut}(\Psi_0(G)).$$
Chapter 3 shows that $\mu_G$ is continuous, that it is trivial if and only if $G$ is an inner form of a split group, and that it depends only on the inner class of $G$. If $G$ is quasi-split and $B \supset T$ are defined over $F$, then $\mu_G(\sigma)$ is the action of $\sigma$ on $X^*(T)$ itself. Section 5.4 uses $\mu_G$ to define the L-group.

### The dual group

**Definition 5.2.5 (dual group).** Let $G$ be a connected reductive group over a field $F$. A *dual group* of $G$ is a connected reductive group $G^\vee$ over $\mathbb{C}$ with a pinning $(B^\vee, T^\vee, \{x_{\alpha^\vee}\})$ and an isomorphism of based root data
$$\Psi_0(G^\vee, B^\vee, T^\vee) \cong \Psi_0(G)^\vee.$$
Some authors write $\hat G$ for $G^\vee$.

Lean: not stated yet

By Theorem 5.2.1 part 2 a dual group exists, because $\Psi_0(G)^\vee$ is reduced by Proposition 5.1.5. By Theorem 5.2.3 it is unique up to a unique isomorphism of pinned groups. Concretely, if $G$ is split with $T \subset B$, then $T^\vee$ is the complex torus with $X^*(T^\vee) = X_*(T)$ and $X_*(T^\vee) = X^*(T)$, that is,
$$T^\vee = X^*(T) \otimes_{\mathbb{Z}} \mathbb{C}^\times = \mathrm{Hom}(X_*(T), \mathbb{C}^\times).$$
The roots of $T^\vee$ in $G^\vee$ are the coroots $\alpha^\vee$ of $G$, and the simple roots for $B^\vee$ are the simple coroots. This is the torus that Volume 3, Definition 4.5.1 calls the dual torus $\hat T$. The dual group depends only on $G$ over $F_s$, and even only on the root datum. So it does not see the field $F$. The field enters in Section 5.4 through $\mu_G$.

**Proposition 5.2.6 (first properties).** Let $G$ be connected reductive with dual group $G^\vee$.
1. $(G^\vee)^\vee \cong G_{\mathbb{C}}$ if $G$ is split, and $(G_1 \times G_2)^\vee = G_1^\vee \times G_2^\vee$.
2. If $G = T$ is a torus, then $G^\vee = T^\vee$ is the torus with character group $X_*(T)$.
3. The Weyl groups $W(G, T)$ and $W(G^\vee, T^\vee)$ are isomorphic, by $w \mapsto (w^{-1})^t$ on $X_*(T) = X^*(T^\vee)$.
4. $X^*(Z(G^\vee)) = X_*(T) / \mathbb{Z} R^\vee$, so $Z(G^\vee)$ has character group $\pi_1(G)$. Also $\pi_1(G^\vee) = X^*(T)/\mathbb{Z}R$, the character group of $Z(G)$ when $G$ is split.
5. $G$ is semisimple if and only if $G^\vee$ is semisimple, and then $G$ is simply connected if and only if $G^\vee$ is adjoint.
6. If $G$ is simple of type $B_n$, then $G^\vee$ is simple of type $C_n$, and the reverse holds. The other types do not change.

Lean: `Langlands.Groups.RootDatum.dual_dual` for the root data in (1), and `Langlands.Groups.RootDatum.torusDualEquiv` for (2)

*Proof.* Part 1 is Proposition 5.1.5 part 1 with Theorem 5.2.1. Part 2 holds because a torus has no roots. Part 3 is Proposition 5.1.5 part 3, with the identification $W(G, T) = N(T)/T$ of Chapter 3. Part 4 is the computation of the centre after Proposition 5.1.9, applied to $G^\vee$. Part 5 follows from Proposition 5.1.7 and Proposition 5.1.9. Part 6 follows from Proposition 5.1.13. $\square$

Part 4 gives the first sign that the dual group mixes the arithmetic and the geometry. The centre of $G^\vee$ comes from the fundamental group of $G$, and the fundamental group of $G^\vee$ is dual to the centre of $G$. For example, Kottwitz proved in "Stable trace formula: elliptic singular terms" (Math. Ann. 1986) that for a $p$-adic field $F$ the Galois cohomology set $H^1(F, G)$ is in bijection with the group of characters of $\pi_0(Z(G^\vee)^{\Gamma_F})$, where $\Gamma_F$ acts on $Z(G^\vee)$ through $\mu_G$ as in Section 5.4.

### Central isogenies

A *central isogeny* is a surjective homomorphism $f : G_1 \to G_2$ of connected reductive groups whose kernel is finite and central. If $T_1 \subset G_1$ is a maximal torus, then $T_2 = f(T_1)$ is a maximal torus of $G_2$, and $f$ induces a map $f^* : X^*(T_2) \to X^*(T_1)$ with finite cokernel. Its transpose is $f_* : X_*(T_1) \to X_*(T_2)$. Both maps are injective, and $f^*$ maps roots to roots. Since the kernel is central, $f_*$ maps coroots to coroots.

**Proposition 5.2.7 (dual isogenies).** Let $f : G_1 \to G_2$ be a central isogeny of split reductive groups. Then there is a central isogeny $f^\vee : G_2^\vee \to G_1^\vee$ of the dual groups that induces $f^*$ on the cocharacter groups $X_*(T_2^\vee) = X^*(T_2)$ and $X_*(T_1^\vee) = X^*(T_1)$. Its kernel is isomorphic to $X^*(T_1) / f^* X^*(T_2)$, which is the character group of $\ker f$.

Lean: not stated yet

*Proof.* The map $f^* : X^*(T_2) \to X^*(T_1)$ is a homomorphism of root data in the sense of Chapter 3: it maps $R_2$ bijectively onto $R_1$, and its transpose maps $R_1^\vee$ onto $R_2^\vee$. Read in the dual root data, $f^*$ is a map $X_*(T_2^\vee) \to X_*(T_1^\vee)$ that maps coroots to coroots, and it has finite cokernel. The isogeny theorem ([Spr98], Chapter 9) gives a central isogeny $f^\vee : G_2^\vee \to G_1^\vee$ that induces it on cocharacters. The kernel of $f^\vee$ lies in $T_2^\vee$, since it is central. Put $Q = X^*(T_1) / f^* X^*(T_2)$. Tensor the exact sequence $0 \to X^*(T_2) \to X^*(T_1) \to Q \to 0$ with $\mathbb{C}^\times$. Since $T_i^\vee = X^*(T_i) \otimes \mathbb{C}^\times$ and $X^*(T_1)$ is free, the kernel of $T_2^\vee \to T_1^\vee$ is $\mathrm{Tor}_1(Q, \mathbb{C}^\times)$, which is isomorphic to $Q$ because $Q$ is finite and the torsion of $\mathbb{C}^\times$ is $\mathbb{Q}/\mathbb{Z}$. $\square$

**Example 5.2.8 (SL_2 and PGL_2).** The quotient $f : SL_2 \to PGL_2$ has kernel $\mu_2$. On tori, $f^* : X^*(T_{PGL}) = \mathbb{Z} \to X^*(T_{SL}) = \mathbb{Z}$ is multiplication by $2$, because the root generates $X^*(T_{PGL})$ and the root is twice the generator of $X^*(T_{SL})$. By Example 5.1.6, $SL_2^\vee = PGL_2(\mathbb{C})$ and $PGL_2^\vee = SL_2(\mathbb{C})$. The dual isogeny is the quotient map $SL_2(\mathbb{C}) \to PGL_2(\mathbb{C})$, with kernel $\mu_2$. The source of $f^\vee$ is the dual of the target of $f$, so the direction of the isogeny is reversed.

**Remark 5.2.9 (the derived group and the dual).** Let $G$ be split reductive with derived group $G_{\mathrm{der}}$ and identity component of the centre $Z(G)^\circ$. The two maps $G_{\mathrm{der}} \hookrightarrow G$ and $G \to G / Z(G)^\circ$ dualize as follows. The dual of the torus $G/G_{\mathrm{der}}$ is the central torus $Z(G^\vee)^\circ$ of $G^\vee$. The dual of $G_{\mathrm{der}}$ is $G^\vee / Z(G^\vee)^\circ$. The dual of $G_{\mathrm{ad}} = G / Z(G)$ is the simply connected cover $G^\vee_{\mathrm{sc}}$ of the derived group of $G^\vee$. For example, for $G = GL_n$ we get $G_{\mathrm{der}} = SL_n$ and $G^\vee / Z(G^\vee)^\circ = PGL_n(\mathbb{C})$. Exercise 5 asks for the proof. On the level of the root datum, the passage from $G$ to $G_{\mathrm{der}}$ replaces $X^\vee$ by its saturated sublattice $X^\vee \cap \mathbb{Q} R^\vee$, and $X$ by the quotient $X / (X \cap (\mathbb{Q} R^\vee)^\perp)$. Duality exchanges the sublattice with the quotient.
