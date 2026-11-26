---
title: The isomorphism and existence theorems
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## The isomorphism and existence theorems

This section states the two theorems that classify split reductive groups by their root data, and it describes the automorphism group of a split group. The proofs are long, and we only give their structure. The example to keep in mind is the list $SL_n$, $SL_n/\mu_d$, $PGL_n$: these groups have the same root system $A_{n-1}$, and the root datum tells them apart. We follow [Spr98], Chapters 9 and 10, and [Mil17], Chapter 23.

### Isomorphisms of root data

**Definition 3.6.1 (isomorphism of root data).** An *isomorphism* of root data $(X, R, X^\vee, R^\vee) \to (X', R', X'^\vee, R'^\vee)$ is an isomorphism $f \colon X \to X'$ of groups with $f(R) = R'$ such that the transpose $f^\vee \colon X'^\vee \to X^\vee$ satisfies $f^\vee(R'^\vee) = R^\vee$.

Lean: `RootPairing.Equiv`, from Mathlib, for the isomorphisms of root pairings

The condition on the coroots is automatic when $R$ spans $X_\mathbb{Q}$, because then $\alpha^\vee$ is determined by $\alpha$ and $R$. Indeed, $s_\alpha$ is then the only reflection of $X_\mathbb{Q}$ that sends $\alpha$ to $-\alpha$ and preserves the finite spanning set $R$ (Chapter 2), and $s_\alpha$ determines $\alpha^\vee$. In general it is not. For example the root data of $SL_2 \times \mathbb{G}_m$ and $GL_2$ both have $X = \mathbb{Z}^2$ and two roots, but they are not isomorphic (Example 3.3.9).

An isomorphism $\varphi \colon G \to G'$ of split reductive groups with $\varphi(T) = T'$ restricts to an isomorphism $T \to T'$. The induced map $\varphi^* \colon X^*(T') \to X^*(T)$ sends roots to roots and coroots to coroots, because $\varphi$ sends $\mathfrak{g}_\alpha$ to $\mathfrak{g}'_{\alpha'}$ with $\varphi^*\alpha' = \alpha$, and sends $\varphi_\alpha$ to $\varphi_{\alpha'}$ up to conjugation by $T'$. So $\varphi^*$ is an isomorphism of root data $\Psi(G', T') \to \Psi(G, T)$.

### The two theorems

**Theorem 3.6.2 (isomorphism theorem).** Let $(G, T)$ and $(G', T')$ be split reductive groups over $k$, and let $f \colon T \to T'$ be an isomorphism such that $f^* \colon X^*(T') \to X^*(T)$ is an isomorphism of root data $\Psi(G', T') \to \Psi(G, T)$. Then $f$ extends to an isomorphism $\varphi \colon G \to G'$. Two such extensions differ by conjugation by an element of $(T/Z(G))(k)$.

Lean: not stated yet

The proof is in [Spr98], Chapter 9, and [Mil17], Chapter 23. Its main steps are the following. The multiplication of $G$ is determined by its restriction to the big cell $U^- \times T \times U$ (Proposition 3.4.8) and by the elements $n_\alpha$ for $\alpha \in \Delta$. The structure constants are given by the commutator formula (Proposition 3.2.7) and depend only on the root datum and on a choice of isomorphisms $u_\alpha \colon \mathbb{G}_a \to U_\alpha$, up to signs. The signs are matched for $G$ and $G'$ by a reduction to semisimple rank 2. For the uniqueness, an automorphism that is the identity on $T$ acts on each $U_\alpha$ by a scalar, and these scalars come from an element of $T/Z(G)$.

**Theorem 3.6.3 (existence theorem).** For every reduced root datum $\Psi$ and every field $k$ there is a split reductive group $(G, T)$ over $k$ with $\Psi(G, T) \cong \Psi$.

Lean: not stated yet

Chevalley constructed the adjoint groups from a complex semisimple Lie algebra with a basis whose structure constants are integers. Springer gives a construction by generators and relations ([Spr98], Chapter 10). Demazure proved the theorem over $\mathbb{Z}$: for each reduced root datum there is a split reductive group scheme over $\mathbb{Z}$ with that root datum, the *Chevalley group scheme*, and it is unique. So every split reductive group over $k$ is the base change of a group scheme over $\mathbb{Z}$, and it makes sense to speak of $G(\mathbb{Z})$, $G(\mathbb{Z}_p)$ and $G(\mathbb{A})$. The groups $G(\mathbb{Z}_p)$ are the hyperspecial maximal compact subgroups of Volume 6.

**Corollary 3.6.4 (classification of split reductive groups).** The map $(G, T) \mapsto \Psi(G, T)$ is a bijection from the set of isomorphism classes of split reductive groups over $k$ to the set of isomorphism classes of reduced root data. The set of isomorphism classes does not depend on $k$.

Lean: not stated yet

*Proof.* The map is well defined by Section 3.3 and the conjugacy of split maximal tori. It is injective by Theorem 3.6.2 and surjective by Theorem 3.6.3. $\square$

For semisimple groups the classification takes a simpler form. Let $\Phi$ be a reduced root system in a real vector space $V$, let $Q = \mathbb{Z}\Phi$ be the root lattice and let $P = \{x \in V : \langle x, \alpha^\vee \rangle \in \mathbb{Z} \text{ for all } \alpha \in \Phi\}$ be the weight lattice. A semisimple root datum with root system $\Phi$ is determined by its character group $X$, and $X$ can be any lattice with $Q \subset X \subset P$. The quotient $P/Q$ is finite, so there are finitely many semisimple groups with a given root system. The simply connected group has $X = P$, and the adjoint group has $X = Q$. Every other semisimple group with root system $\Phi$ is a quotient of the simply connected one by a subgroup of its center, and its center has character group $X/Q$ (Proposition 3.3.7).

**Example 3.6.5 (the groups of type $A_{n-1}$).** For the root system $A_{n-1}$ the group $P/Q$ is cyclic of order $n$ (Section 3.7). The lattices between $Q$ and $P$ correspond to the subgroups of $\mathbb{Z}/n$, so to the divisors $d$ of $n$. The simply connected group is $SL_n$ and the adjoint group is $PGL_n$. The intermediate groups are the quotients $SL_n / \mu_d$, where $\mu_d$ is the group of scalar matrices $\zeta I$ with $\zeta^d = 1$, a subgroup of the center $\mu_n$. For $n = 4$ and $d = 2$ we get $SL_4/\mu_2$, which is isomorphic to $SO_6$ (Section 3.7).

### Isogenies

An *isogeny* is a surjective homomorphism with finite kernel. An isogeny $\varphi \colon G \to G'$ of split reductive groups with $\varphi(T) = T'$ induces an injective map $\varphi^* \colon X' \to X$ with finite cokernel. If $\varphi$ is *central*, that is, its kernel is central, then $\varphi^*$ maps $R'$ bijectively onto $R$, and the transpose maps $\alpha^\vee$ to $\alpha'^\vee$. The isogeny theorem says that every such map of root data comes from a central isogeny, unique up to conjugation by $T/Z(G)$ ([Mil17], Chapter 23). In characteristic 0 every isogeny is central. In characteristic $p$ there are more, such as the Frobenius map $G \to G^{(p)}$, for which $\varphi^*$ is multiplication by $p$, and, when $p = 2$, an isogeny $SO_{2n+1} \to Sp_{2n}$ that is a bijection on $\bar k$-points. Chevalley's general isogeny theorem treats these *special isogenies* too.

Every split reductive group $G$ has a central isogeny $G^{sc} \times Z(G)^0 \to G$, where $G^{sc}$ is the simply connected group with the root system of $G$ and $Z(G)^0$ is the central torus. For $GL_n$ this is the map $SL_n \times \mathbb{G}_m \to GL_n$, $(g, z) \mapsto zg$, with kernel $\mu_n$ embedded by $\zeta \mapsto (\zeta^{-1} I, \zeta)$.

### Pinnings and automorphisms

**Definition 3.6.6 (based root datum and pinning).** A *based root datum* is a root datum with a base $\Delta$ of $R$. We write it $\Psi_0 = (X, \Delta, X^\vee, \Delta^\vee)$. An isomorphism of based root data is an isomorphism of root data with $f(\Delta) = \Delta'$. A *pinning* of a split reductive group $G$ is a choice of a Borel subgroup $B$, a split maximal torus $T \subset B$, and for each $\alpha \in \Delta$ an isomorphism $u_\alpha \colon \mathbb{G}_a \to U_\alpha$.

Lean: `RootPairing.Aut`, from Mathlib, for the automorphism group of a root pairing, without a base

Each pair $(B, T)$ gives a based root datum $\Psi_0(G, B, T)$, with the base of the positive system $R(B)$ of Theorem 3.4.3. For $GL_n$ with the upper triangular $B$ and the standard pinning $u_{e_i - e_{i+1}}(x) = I + x E_{i, i+1}$, the based root datum has $\Delta = \{e_1 - e_2, \dots, e_{n-1} - e_n\}$.

**Theorem 3.6.7 (automorphisms of a split group).** Let $G$ be a split reductive group over $k$ with a pinning $(B, T, \{u_\alpha\})$, and let $\Psi_0$ be its based root datum. Then each automorphism of $\Psi_0$ comes from a unique automorphism of $G$ that preserves the pinning, and
$$\mathrm{Aut}_k(G) = G_{ad}(k) \rtimes \mathrm{Aut}(\Psi_0),$$
where $G_{ad} = G/Z(G)$ acts by conjugation. In particular the group of outer automorphisms $\mathrm{Aut}_k(G) / G_{ad}(k)$ is isomorphic to $\mathrm{Aut}(\Psi_0)$.

Lean: not stated yet

*Proof sketch.* Let $\sigma$ be an automorphism of $G$. The pair $(\sigma(B), \sigma(T))$ is conjugate to $(B, T)$ under $G(k)$, by the conjugacy of Borel subgroups and of split maximal tori in a split group. So after composition with an inner automorphism, $\sigma$ preserves $B$ and $T$, and it then induces an automorphism of $\Psi_0$. If this automorphism is trivial, then by Theorem 3.6.2 $\sigma$ is conjugation by an element of $(T/Z(G))(k)$. The pinned form of Theorem 3.6.2 gives the splitting: an automorphism of $\Psi_0$ lifts to a unique automorphism of $G$ that sends each $u_\alpha$ to $u_{f(\alpha)}$. See [Spr98], Chapter 9, and [Mil17], Chapter 23. $\square$

If $R$ spans $X_\mathbb{Q}$, that is, if $G$ is semisimple, then $\mathrm{Aut}(\Psi_0)$ is the group of automorphisms of the Dynkin diagram that preserve the lattice $X$. For $X = P$ or $X = Q$ this is the whole automorphism group of the diagram.

**Example 3.6.8 (outer automorphisms).**
1. For $SL_2$ the Dynkin diagram is a point, so $SL_2$ has no outer automorphisms. The automorphism $g \mapsto (g^T)^{-1}$ must be inner, and indeed $(g^T)^{-1} = w g w^{-1}$ for $w = \left(\begin{smallmatrix} 0 & 1 \\ -1 & 0 \end{smallmatrix}\right)$ and $g \in SL_2$.
2. For $n \ge 3$ the diagram $A_{n-1}$ has one nontrivial automorphism, $\alpha_i \mapsto \alpha_{n-i}$. So $\mathrm{Out}(SL_n) \cong \mathbb{Z}/2$, and $g \mapsto (g^T)^{-1}$ is the nontrivial outer automorphism. It acts on the diagonal torus by $t \mapsto t^{-1}$, so on $X$ by $-1$, and $-1$ composed with $w_0$ maps $\Delta$ to $\Delta$.
3. For $GL_2$ the diagram is a point, but $\mathrm{Aut}(\Psi_0)$ has order 2. Its nontrivial element is $e_1 \mapsto -e_2$, $e_2 \mapsto -e_1$, which fixes $\alpha = e_1 - e_2$. It comes from $g \mapsto w (g^T)^{-1} w^{-1} = \det(g)^{-1} g$. This automorphism is not inner, because it acts on the center by $z \mapsto z^{-1}$. Its restriction to $SL_2$ is the identity. Exercise 8 shows that $\mathrm{Out}(GL_n) \cong \mathbb{Z}/2$ for all $n \ge 1$.
4. The diagram $D_4$ has automorphism group $S_3$, which permutes the three outer nodes. So the simply connected group $\mathrm{Spin}_8$ has $\mathrm{Out}(\mathrm{Spin}_8) \cong S_3$. The automorphisms of order 3 are the *triality* automorphisms. They do not preserve the lattice of $SO_8$, and $\mathrm{Out}(SO_8) \cong \mathbb{Z}/2$.

The automorphism group of $\Psi_0$ is the group that the Galois group acts through when we pass to non-split groups in Section 3.8. In Chapter 5 the same group acts on the dual group, and the L-group of a quasi-split group is built from this action.
