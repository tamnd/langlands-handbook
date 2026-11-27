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

### Chevalley's construction of the adjoint group

Chevalley's paper of 1955 builds the adjoint groups of Theorem 3.6.3 directly from a complex semisimple Lie algebra, with no algebraic geometry. The idea is to choose a basis of the Lie algebra in which all the structure constants are integers. The exponentials $\exp(t\, \mathrm{ad}\, e_\alpha)$ of the root vectors then have matrices whose entries are polynomials in $t$ with integer coefficients. So they make sense over every field $k$, and the group that they generate is a group of automorphisms of a Lie algebra over $k$. We follow Steinberg, *Lectures on Chevalley Groups* (Yale University, 1967), cited as [Ste67]. Its Chapter 1 constructs the Chevalley basis, and its Chapters 2 and 3 define the groups and prove their first relations. A second account is [Hum72], Section 25.

Throughout the subsection, $\mathfrak{g}$ is a semisimple Lie algebra over $\mathbb{C}$, $\mathfrak{h}$ is a Cartan subalgebra, $\Phi \subset \mathfrak{h}^*$ is the root system and $\Delta = \{\alpha_1, \dots, \alpha_\ell\}$ is a base, as in Sections 2.4 and 2.5. For $\alpha \in \Phi$ let $h_\alpha \in \mathfrak{h}$ be the coroot of Proposition 2.4.9. Then $\alpha(h_\alpha) = 2$, and for $\beta \in \Phi$ the number $\beta(h_\alpha) = \langle \beta, \alpha^\vee \rangle$ is the Cartan integer, which Chapter 2 writes $\langle \beta, \alpha \rangle$. We put $h_i = h_{\alpha_i}$. An $\mathfrak{sl}_2$-triple is a triple $(h, e, f)$ with $[h, e] = 2e$, $[h, f] = -2f$ and $[e, f] = h$.

**Theorem 3.6.9 (Chevalley basis).** There are elements $e_\alpha \in \mathfrak{g}_\alpha$, one for each $\alpha \in \Phi$, with the following properties.
1. $[e_\alpha, e_{-\alpha}] = h_\alpha$ for each $\alpha \in \Phi$.
2. If $\alpha, \beta, \alpha + \beta \in \Phi$, then $[e_\alpha, e_\beta] = N_{\alpha, \beta}\, e_{\alpha + \beta}$ with $N_{\alpha, \beta} = \pm (r + 1)$, where $r$ is the largest integer with $\beta - r\alpha \in \Phi$.
3. If $\alpha, \beta \in \Phi$, $\beta \ne -\alpha$ and $\alpha + \beta \notin \Phi$, then $[e_\alpha, e_\beta] = 0$.

The elements $h_1, \dots, h_\ell$ and $e_\alpha$, $\alpha \in \Phi$, form a basis of $\mathfrak{g}$, and all the structure constants of $\mathfrak{g}$ in this basis are integers. Such a basis is a *Chevalley basis*.

Lean: not stated yet

*Proof sketch.* Part 3 holds for all root vectors, because $\mathfrak{g}_{\alpha + \beta} = 0$ when $\alpha + \beta$ is neither a root nor $0$. By Theorem 2.6.12, applied to the automorphism $-1$ of $\Phi$, there is an automorphism $\sigma$ of $\mathfrak{g}$ that acts on $\mathfrak{h}$ by $-1$, so that $\sigma(\mathfrak{g}_\alpha) = \mathfrak{g}_{-\alpha}$. One chooses the $e_\alpha$ with $\sigma(e_\alpha) = -e_{-\alpha}$ and $[e_\alpha, e_{-\alpha}] = h_\alpha$. Applying $\sigma$ to $[e_\alpha, e_\beta] = N_{\alpha, \beta} e_{\alpha + \beta}$ gives $N_{-\alpha, -\beta} = -N_{\alpha, \beta}$. A computation in the $\mathfrak{sl}_2$-module $\bigoplus_i \mathfrak{g}_{\beta + i\alpha}$ of Theorem 2.4.10 gives $N_{\alpha, \beta} N_{-\alpha, -\beta} = -(r + 1)^2$. So $N_{\alpha, \beta} = \pm (r + 1)$. For the last statement, $[h_i, e_\beta] = \beta(h_i) e_\beta$ with $\beta(h_i) \in \mathbb{Z}$, and $h_\alpha$ is an integer combination of $h_1, \dots, h_\ell$, because $h_\alpha$ corresponds to $\alpha^\vee$ under the Killing form and the simple coroots form a base of the dual root system $\Phi^\vee$ (Proposition 2.6.9). See [Hum72], Section 25, and [Ste67], Chapter 1. $\square$

Let $\mathfrak{g}_\mathbb{Z}$ be the subgroup of $\mathfrak{g}$ spanned over $\mathbb{Z}$ by a Chevalley basis. It is a lattice in $\mathfrak{g}$ and a Lie ring. For a field $k$, put $\mathfrak{g}_k = \mathfrak{g}_\mathbb{Z} \otimes_\mathbb{Z} k$. It is a Lie algebra over $k$ with the basis $h_i \otimes 1$, $e_\alpha \otimes 1$, which we still write $h_i$ and $e_\alpha$, and with the same structure constants, read in $k$. In characteristic 0 it is the split semisimple Lie algebra of type $\Phi$ over $k$. In small characteristic it need not be semisimple. For $\mathfrak{sl}_2$ in characteristic 2, for example, $[h, e] = 2e = 0$, and $h$ is central. Write $\mathfrak{h}_\mathbb{Z}$ for the span of the $h_i$, and $\mathfrak{h}_k = \mathfrak{h}_\mathbb{Z} \otimes k$. Each root $\beta$ takes integer values on $\mathfrak{h}_\mathbb{Z}$, and we extend it $k$-linearly to $\mathfrak{h}_k$.

**Proposition 3.6.10 (divided powers).** Let $\alpha \in \Phi$, and for $n \ge 0$ let $D_n = (\mathrm{ad}\, e_\alpha)^n / n!$, an endomorphism of $\mathfrak{g}$.
1. $D_n(\mathfrak{g}_\mathbb{Z}) \subset \mathfrak{g}_\mathbb{Z}$ for all $n$.
2. $D_n = 0$ for $n \ge 4$.
3. $D_n [u, v] = \sum_{i + j = n} [D_i u, D_j v]$ for $u, v \in \mathfrak{g}$, and $D_i D_j = \binom{i + j}{i} D_{i + j}$.

Lean: not stated yet

*Proof.* We compute $D_n$ on the Chevalley basis. First, $D_n e_\alpha = 0$ for $n \ge 1$. For $h \in \mathfrak{h}_\mathbb{Z}$ we have $D_1 h = [e_\alpha, h] = -\alpha(h) e_\alpha$, with $\alpha(h) \in \mathbb{Z}$, and $D_n h = 0$ for $n \ge 2$. Next, $D_1 e_{-\alpha} = h_\alpha$ and $D_2 e_{-\alpha} = \frac{1}{2}[e_\alpha, h_\alpha] = \frac{1}{2}(-2 e_\alpha) = -e_\alpha$, and $D_3 e_{-\alpha} = 0$. Now let $\beta \ne \pm\alpha$, and let $\beta - r\alpha, \dots, \beta + q\alpha$ be the $\alpha$-string through $\beta$ (Theorem 2.4.10). For $0 \le j < q$, the $\alpha$-string through $\beta + j\alpha$ is the same set of roots, and the largest integer $s$ with $\beta + j\alpha - s\alpha \in \Phi$ is $s = r + j$. So $|N_{\alpha, \beta + j\alpha}| = r + j + 1$ by Theorem 3.6.9. For $1 \le n \le q$ this gives
$$(\mathrm{ad}\, e_\alpha)^n e_\beta = \Big( \prod_{j = 0}^{n - 1} N_{\alpha, \beta + j\alpha} \Big) e_{\beta + n\alpha} = \pm (r + 1)(r + 2) \cdots (r + n)\, e_{\beta + n\alpha},$$
so that $D_n e_\beta = \pm \binom{r + n}{n} e_{\beta + n\alpha} \in \mathfrak{g}_\mathbb{Z}$. For $n > q$, $\beta + n\alpha$ is not a root, and it is not $0$, so $D_n e_\beta = 0$. This proves part 1. A string has at most 4 roots (Proposition 2.5.6), so $q \le 3$, and part 2 follows from the list. For part 3, $\mathrm{ad}\, e_\alpha$ is a derivation, so the Leibniz rule gives $(\mathrm{ad}\, e_\alpha)^n [u, v] = \sum_{i + j = n} \binom{n}{i} [(\mathrm{ad}\, e_\alpha)^i u, (\mathrm{ad}\, e_\alpha)^j v]$. Divide by $n!$. The second formula is the identity $\frac{1}{i!\, j!} = \binom{i+j}{i} \frac{1}{(i + j)!}$. $\square$

The case $\beta = -\alpha$ shows why the divided powers are needed: $(\mathrm{ad}\, e_\alpha)^2 e_{-\alpha} = -2 e_\alpha$ is divisible by 2 in $\mathfrak{g}_\mathbb{Z}$, but the factor 2 would kill the term in characteristic 2. The identities of part 3 hold between endomorphisms of the free abelian group $\mathfrak{g}_\mathbb{Z}$, so they also hold for the endomorphisms $D_n \otimes 1$ of $\mathfrak{g}_k$, for every field $k$. We write $D_n$ for these too.

**Definition 3.6.11 (root elements and the elementary adjoint group).** Let $k$ be a field, $\alpha \in \Phi$ and $t \in k$. The *root element* $x_\alpha(t)$ is the endomorphism
$$x_\alpha(t) = \sum_{n = 0}^{3} t^n D_n$$
of $\mathfrak{g}_k$. The *elementary adjoint Chevalley group* $E_{ad}(\Phi, k)$ is the subgroup of $\mathrm{Aut}(\mathfrak{g}_k)$ generated by the elements $x_\alpha(t)$ for all $\alpha \in \Phi$ and $t \in k$.

Lean: `Langlands.Groups.Chevalley.simpleRootElement`, `Langlands.Groups.Chevalley.negSimpleRootElement` and `Langlands.Groups.Chevalley.ElementaryAdjointChevalleyGroup`, for the simple roots and in characteristic 0 (Remark 3.6.19)

The definition makes sense, because each $x_\alpha(t)$ is an automorphism. Indeed, by part 3 of Proposition 3.6.10,
$$x_\alpha(t)[u, v] = \sum_n t^n \sum_{i + j = n} [D_i u, D_j v] = [x_\alpha(t) u, x_\alpha(t) v],$$
and $x_\alpha(s) x_\alpha(t) = \sum_{i, j} s^i t^j \binom{i + j}{i} D_{i + j} = \sum_n (s + t)^n D_n = x_\alpha(s + t)$. Since $x_\alpha(0) = D_0 = 1$, the map $t \mapsto x_\alpha(t)$ is a homomorphism from the additive group of $k$ to $\mathrm{Aut}(\mathfrak{g}_k)$, and $x_\alpha(t)^{-1} = x_\alpha(-t)$. It is injective, since $x_\alpha(t) e_{-\alpha} = e_{-\alpha} + t h_\alpha - t^2 e_\alpha$ by the proof of Proposition 3.6.10. Its image $X_\alpha$ is the *root subgroup* of $\alpha$. For $k = \mathbb{C}$ we have $x_\alpha(t) = \exp(t\, \mathrm{ad}\, e_\alpha)$, the exponential of a nilpotent derivation. Steinberg calls $E_{ad}(\Phi, k)$ the Chevalley group of $\mathfrak{g}$ over $k$. We use a longer name to separate it from the groups $G(k)$ of the earlier sections.

The first computation takes place in the copy of $\mathfrak{sl}_2$ attached to a root.

**Proposition 3.6.12 (root elements on an $\mathfrak{sl}_2$-triple).** Let $\alpha \in \Phi$ and put $e = e_\alpha$, $f = e_{-\alpha}$ and $h = h_\alpha$. Then $(h, e, f)$ is an $\mathfrak{sl}_2$-triple in $\mathfrak{g}_\mathbb{Z}$. For every field $k$ and every $t \in k$,
$$x_\alpha(t) e = e, \qquad x_\alpha(t) h = h - 2te, \qquad x_\alpha(t) f = f + th - t^2 e,$$
$$x_{-\alpha}(t) f = f, \qquad x_{-\alpha}(t) h = h + 2tf, \qquad x_{-\alpha}(t) e = e - th - t^2 f.$$
For $h' \in \mathfrak{h}_k$ we have $x_\alpha(t) h' = h' - \alpha(h') t e$ and $x_{-\alpha}(t) h' = h' + \alpha(h') t f$.

Lean: `Langlands.Groups.Chevalley.expAd_apply_sl2_h` and `Langlands.Groups.Chevalley.expAd_apply_sl2_f`, for an $\mathfrak{sl}_2$-triple with $\mathrm{ad}\, e$ nilpotent over a field of characteristic 0

*Proof.* We have $[h, e] = \alpha(h_\alpha) e = 2e$ and $[h, f] = -\alpha(h_\alpha) f = -2f$, and $[e, f] = h$ by Theorem 3.6.9. So $(h, e, f)$ is an $\mathfrak{sl}_2$-triple. We compute the divided powers $D_n = (\mathrm{ad}\, e)^n / n!$ in $\mathfrak{g}_\mathbb{Z}$, using only these three relations. First $D_1 e = [e, e] = 0$, so $x_\alpha(t) e = e$. Next $D_1 h = [e, h] = -[h, e] = -2e$ and $(\mathrm{ad}\, e)^2 h = [e, -2e] = 0$, so $x_\alpha(t) h = h - 2te$. Finally $D_1 f = [e, f] = h$, then $(\mathrm{ad}\, e)^2 f = [e, h] = -2e$, so $D_2 f = -e$ in the torsion free group $\mathfrak{g}_\mathbb{Z}$, and $(\mathrm{ad}\, e)^3 f = [e, -2e] = 0$. Thus $x_\alpha(t) f = f + th - t^2 e$. These are identities in $\mathfrak{g}_\mathbb{Z}[t]$, so they hold in $\mathfrak{g}_k$ for every field $k$ and every $t \in k$.

The triple $(-h, f, e)$ is again an $\mathfrak{sl}_2$-triple: $[-h, f] = 2f$, $[-h, e] = -2e$ and $[f, e] = -h$. The element $x_{-\alpha}(t)$ is built from $\mathrm{ad}\, f$ in the same way, so the first part, applied to this triple, gives $x_{-\alpha}(t) f = f$, $x_{-\alpha}(t)(-h) = -h - 2tf$ and $x_{-\alpha}(t) e = e + t(-h) - t^2 f$. These are the formulas of the second line. For $h' \in \mathfrak{h}_\mathbb{Z}$, $D_1 h' = [e, h'] = -\alpha(h') e$ and $D_2 h' = 0$. In the same way $[f, h'] = \alpha(h') f$ and $[f, [f, h']] = 0$. Extend by linearity to $\mathfrak{h}_k$. $\square$

For $\mathfrak{g} = \mathfrak{sl}_2$ and $k = \mathbb{C}$ these are the formulas for the conjugation by the matrix $\left(\begin{smallmatrix} 1 & t \\ 0 & 1 \end{smallmatrix}\right)$, as Example 3.6.16 shows. The coefficient $-t^2$ in $x_\alpha(t) f$ comes from the divided power $D_2$.

**Proposition 3.6.13 (Weyl elements).** Let $\alpha \in \Phi$, let $(h, e, f)$ be as in Proposition 3.6.12, and for $t \in k^\times$ put
$$w_\alpha(t) = x_\alpha(t)\, x_{-\alpha}(-t^{-1})\, x_\alpha(t) \in E_{ad}(\Phi, k).$$
1. $w_\alpha(t) e = -t^{-2} f$, $w_\alpha(t) h = -h$ and $w_\alpha(t) f = -t^2 e$. In particular $w_\alpha(1)$ maps $e$, $h$, $f$ to $-f$, $-h$, $-e$.
2. $w_\alpha(t) h' = h' - \alpha(h') h_\alpha$ for all $h' \in \mathfrak{h}_k$.
3. For each $\beta \in \Phi$ there is a sign $\eta_{\alpha, \beta} \in \{\pm 1\}$, which does not depend on $k$, such that $w_\alpha(1) e_\beta = \eta_{\alpha, \beta}\, e_{s_\alpha \beta}$ and
$$w_\alpha(1)\, x_\beta(u)\, w_\alpha(1)^{-1} = x_{s_\alpha \beta}(\eta_{\alpha, \beta}\, u) \qquad (u \in k).$$

Lean: `Langlands.Groups.Chevalley.weylElement_one_apply_geckE`, `Langlands.Groups.Chevalley.weylElement_one_apply_geckF` and `Langlands.Groups.Chevalley.weylElement_one_apply_geckH`, for part 1 with $t = 1$ and $\alpha$ simple, in characteristic 0

*Proof.* Put $s = -t^{-1}$. We apply the three factors from right to left and use Proposition 3.6.12 at each step. For part 1, $x_\alpha(t) e = e$, then $x_{-\alpha}(s) e = e - sh - s^2 f = e + t^{-1} h - t^{-2} f$, and
$$x_\alpha(t)\big(e + t^{-1} h - t^{-2} f\big) = e + t^{-1}(h - 2te) - t^{-2}(f + th - t^2 e) = -t^{-2} f.$$
Next, $x_\alpha(t) f = f + th - t^2 e$, and
$$x_{-\alpha}(s)(f + th - t^2 e) = f + t(h + 2sf) - t^2(e - sh - s^2 f) = f + th - 2f - t^2 e - th + f = -t^2 e,$$
which $x_\alpha(t)$ fixes. Finally, $x_\alpha(t) h = h - 2te$, and $x_{-\alpha}(s)(h - 2te) = h - 2t^{-1} f - 2t(e + t^{-1} h - t^{-2} f) = -h - 2te$. Then $x_\alpha(t)(-h - 2te) = -(h - 2te) - 2te = -h$.

For part 2, let $h' \in \mathfrak{h}_k$ and $a = \alpha(h')$. Then $x_\alpha(t) h' = h' - ate$, and
$$x_{-\alpha}(s)(h' - ate) = h' + asf - at(e - sh - s^2 f) = h' - at^{-1} f - ate - ah + at^{-1} f = h' - ah - ate.$$
Applying $x_\alpha(t)$ gives $(h' - ate) - a(h - 2te) - ate = h' - ah$.

For part 3, work first in $\mathfrak{g}_\mathbb{Q} = \mathfrak{g}_\mathbb{Z} \otimes \mathbb{Q}$, and let $w = w_\alpha(1)$. By part 2, $w$ acts on $\mathfrak{h}_\mathbb{Q}$ by the involution $\tau(h') = h' - \alpha(h') h_\alpha$, and $\beta(\tau h') = \beta(h') - \alpha(h') \beta(h_\alpha) = (s_\alpha \beta)(h')$. Let $v \in \mathfrak{g}_\beta$. Since $w$ is an automorphism,
$$[h', wv] = w[w^{-1} h', v] = \beta(\tau h')\, wv = (s_\alpha\beta)(h')\, wv.$$
So $w$ maps the root space $\mathbb{Q} e_\beta$ to the root space $\mathbb{Q} e_{s_\alpha \beta}$, and $w e_\beta = c\, e_{s_\alpha \beta}$ with $c \in \mathbb{Q}$. The matrices of $w$ and of $w^{-1} = x_\alpha(-1) x_{-\alpha}(1) x_\alpha(-1)$ in the Chevalley basis have integer entries, by Proposition 3.6.10. So $c$ and $c^{-1}$ are integers, and $c = \pm 1$. Put $\eta_{\alpha, \beta} = c$. For an automorphism $\varphi$ we have $\varphi\, (\mathrm{ad}\, x)\, \varphi^{-1} = \mathrm{ad}(\varphi x)$. So $w (\mathrm{ad}\, e_\beta)^n w^{-1} = \eta_{\alpha, \beta}^n (\mathrm{ad}\, e_{s_\alpha \beta})^n$, and after division by $n!$ and summation, $w x_\beta(u) w^{-1} = x_{s_\alpha \beta}(\eta_{\alpha, \beta} u)$. These are identities between matrices with entries in $\mathbb{Z}[u]$, so they hold over every field. $\square$

Part 2 says that $w_\alpha(t)$ acts on $\mathfrak{h}_k$ as the reflection $s_\alpha$, in its form on coroots. So the elements $w_\alpha(t)$ play the role of the elements $n_\alpha$ of Theorem 3.2.5. Example 3.6.16 shows that for $\mathfrak{sl}_2$ the element $w_\alpha(1)$ is the conjugation by $\left(\begin{smallmatrix} 0 & 1 \\ -1 & 0 \end{smallmatrix}\right)$. The signs $\eta_{\alpha, \beta}$ depend on the signs of the structure constants $N_{\alpha, \beta}$, and Exercise 13 computes some of them for $A_2$.

**Corollary 3.6.14 (simple root elements generate).** The group $E_{ad}(\Phi, k)$ is generated by the elements $x_\alpha(t)$ and $x_{-\alpha}(t)$ for $\alpha \in \Delta$ and $t \in k$. Each root subgroup $X_\beta$ is conjugate in $E_{ad}(\Phi, k)$ to a root subgroup $X_\alpha$ with $\alpha \in \Delta$.

Lean: not stated yet

*Proof.* Let $E'$ be the subgroup generated by the $x_{\pm\alpha}(t)$ with $\alpha \in \Delta$. It contains $w_\alpha(1)$ for $\alpha \in \Delta$. Let $S$ be the set of roots $\beta$ with $X_\beta \subset E'$. Then $\pm\Delta \subset S$, and by part 3 of Proposition 3.6.13, $s_\alpha(S) \subset S$ for $\alpha \in \Delta$. The simple reflections generate $W$, and each root is the image of a simple root under $W$ (Theorem 2.5.14). So $S = \Phi$ and $E' = E_{ad}(\Phi, k)$. The same argument, with $w = w_{\alpha_{i_1}}(1) \cdots w_{\alpha_{i_m}}(1)$, conjugates $X_\beta$ to a simple root subgroup. $\square$

Now we add the torus. By Proposition 3.3.7, the split adjoint group of type $\Phi$ has a maximal torus $T_{ad}$ with character group $\mathbb{Z}\Phi$, so $T_{ad}(k) = \mathrm{Hom}(\mathbb{Z}\Phi, k^\times)$. This group acts on $\mathfrak{g}_k$ through the grading of $\mathfrak{g}_\mathbb{Z}$ by the root lattice.

**Proposition 3.6.15 (torus elements).** Let $\chi \in \mathrm{Hom}(\mathbb{Z}\Phi, k^\times)$. Let $h(\chi)$ be the $k$-linear map of $\mathfrak{g}_k$ with $h(\chi) h' = h'$ for $h' \in \mathfrak{h}_k$ and $h(\chi) e_\beta = \chi(\beta) e_\beta$ for $\beta \in \Phi$.
1. $h(\chi)$ is an automorphism of $\mathfrak{g}_k$, and $\chi \mapsto h(\chi)$ is an injective homomorphism $\mathrm{Hom}(\mathbb{Z}\Phi, k^\times) \to \mathrm{Aut}(\mathfrak{g}_k)$. We write $H$ for its image.
2. For $\alpha \in \Phi$ and $t \in k$,
$$h(\chi)\, x_\alpha(t)\, h(\chi)^{-1} = x_\alpha(\chi(\alpha) t).$$
3. The group $H$ normalizes $E_{ad}(\Phi, k)$, so $H \cdot E_{ad}(\Phi, k)$ is a subgroup of $\mathrm{Aut}(\mathfrak{g}_k)$.

Lean: `Langlands.Groups.Chevalley.torusElement_mul_simpleRootElement_mul_inv`, `Langlands.Groups.Chevalley.torusElement_mul_negSimpleRootElement_mul_inv` and `Langlands.Groups.Chevalley.torusElement_conj_mem`, for the roots $\pm\alpha_i$ with $\alpha_i$ simple, in characteristic 0

*Proof.* For $\gamma \in \mathbb{Z}\Phi$ let $\mathfrak{g}_{\mathbb{Z}, \gamma}$ be $\mathfrak{h}_\mathbb{Z}$ if $\gamma = 0$, $\mathbb{Z} e_\gamma$ if $\gamma \in \Phi$, and $0$ otherwise. Then $\mathfrak{g}_\mathbb{Z} = \bigoplus_\gamma \mathfrak{g}_{\mathbb{Z}, \gamma}$, and $[\mathfrak{g}_{\mathbb{Z}, \gamma}, \mathfrak{g}_{\mathbb{Z}, \delta}] \subset \mathfrak{g}_{\mathbb{Z}, \gamma + \delta}$ by Theorem 3.6.9. The same holds for the subspaces $\mathfrak{g}_{k, \gamma} = \mathfrak{g}_{\mathbb{Z}, \gamma} \otimes k$, and $h(\chi)$ acts on $\mathfrak{g}_{k, \gamma}$ by the scalar $\chi(\gamma)$. For $u \in \mathfrak{g}_{k, \gamma}$ and $v \in \mathfrak{g}_{k, \delta}$,
$$h(\chi)[u, v] = \chi(\gamma + \delta)[u, v] = [\chi(\gamma) u, \chi(\delta) v] = [h(\chi) u, h(\chi) v].$$
So $h(\chi)$ is an automorphism, with inverse $h(\chi^{-1})$, and $h(\chi\psi) = h(\chi) h(\psi)$. If $h(\chi) = 1$, then $\chi(\beta) = 1$ for all $\beta \in \Phi$, and $\chi = 1$ because $\Phi$ generates $\mathbb{Z}\Phi$. This proves part 1.

For part 2, $\mathrm{ad}\, e_\alpha$ maps $\mathfrak{g}_{\mathbb{Z}, \gamma}$ into $\mathfrak{g}_{\mathbb{Z}, \gamma + \alpha}$, so $D_n$ maps $\mathfrak{g}_{k, \gamma}$ into $\mathfrak{g}_{k, \gamma + n\alpha}$. For $v \in \mathfrak{g}_{k, \gamma}$,
$$h(\chi) D_n h(\chi)^{-1} v = \chi(\gamma)^{-1} h(\chi) D_n v = \chi(\gamma)^{-1} \chi(\gamma + n\alpha) D_n v = \chi(\alpha)^n D_n v.$$
So $h(\chi) D_n h(\chi)^{-1} = \chi(\alpha)^n D_n$, and summing over $n$ with the factors $t^n$ gives the formula. Part 3 follows, because conjugation by $h(\chi)$ maps each generator $x_\alpha(t)$ of $E_{ad}(\Phi, k)$ to the generator $x_\alpha(\chi(\alpha) t)$. $\square$

The proof does not divide by any integer, so it works in every characteristic. Over $\mathbb{C}$ there is a shorter proof: $h(\chi) (\mathrm{ad}\, e_\alpha) h(\chi)^{-1} = \mathrm{ad}(h(\chi) e_\alpha) = \chi(\alpha)\, \mathrm{ad}\, e_\alpha$, and one exponentiates. The group $H$ need not lie in $E_{ad}(\Phi, k)$. Steinberg shows that the elements $h_\alpha(c) = w_\alpha(c) w_\alpha(1)^{-1}$, for $c \in k^\times$, are the elements $h(\chi)$ with $\chi(\beta) = c^{\langle \beta, \alpha^\vee \rangle}$ ([Ste67], Chapter 3). Exercise 12 checks this on the $\mathfrak{sl}_2$-triple. Write $P$ for the weight lattice. Since $\beta = \sum_i \langle \beta, \alpha_i^\vee \rangle \varpi_i$ in terms of the fundamental weights $\varpi_i$, the products of the $h_{\alpha_i}(c_i)$ are exactly the $h(\chi)$ for which $\chi$ extends to a homomorphism $P \to k^\times$. So $H \cap E_{ad}(\Phi, k)$ contains the image of $\mathrm{Hom}(P, k^\times)$ in $\mathrm{Hom}(\mathbb{Z}\Phi, k^\times)$, which is the image of $T_{sc}(k)$ in $T_{ad}(k)$. When $k$ is algebraically closed, $k^\times$ is divisible, every $\chi$ extends to $P$, and $H \subset E_{ad}(\Phi, k)$.

**Example 3.6.16 (the group $PSL_2(k)$).** Let $\mathfrak{g} = \mathfrak{sl}_2$ with $e = E_{12}$, $f = E_{21}$, $h = E_{11} - E_{22}$ and $\Phi = \{\pm\alpha\}$. This is a Chevalley basis: $[e, f] = h = h_\alpha$, and conditions 2 and 3 of Theorem 3.6.9 are empty. So $\mathfrak{g}_\mathbb{Z} = \mathfrak{sl}_2(\mathbb{Z})$ and $\mathfrak{g}_k = \mathfrak{sl}_2(k)$ for every field $k$. In the basis $(e, h, f)$, Proposition 3.6.12 gives the matrix of $x_\alpha(t)$:
$$x_\alpha(t) = \begin{pmatrix} 1 & -2t & -t^2 \\ 0 & 1 & t \\ 0 & 0 & 1 \end{pmatrix}.$$
Let $u(t) = \left(\begin{smallmatrix} 1 & t \\ 0 & 1 \end{smallmatrix}\right)$ and $v(t) = \left(\begin{smallmatrix} 1 & 0 \\ t & 1 \end{smallmatrix}\right)$, and let $\mathrm{Ad}(g) y = g y g^{-1}$ for $g \in GL_2(k)$ and $y \in \mathfrak{sl}_2(k)$. A direct multiplication gives $u(t) e u(t)^{-1} = e$, $u(t) h u(t)^{-1} = \left(\begin{smallmatrix} 1 & -2t \\ 0 & -1 \end{smallmatrix}\right) = h - 2te$ and $u(t) f u(t)^{-1} = \left(\begin{smallmatrix} t & -t^2 \\ 1 & -t \end{smallmatrix}\right) = f + th - t^2 e$. So $x_\alpha(t) = \mathrm{Ad}(u(t))$, and in the same way $x_{-\alpha}(t) = \mathrm{Ad}(v(t))$. The matrices $u(t)$ and $v(t)$ generate $SL_2(k)$, by row reduction. Thus $E_{ad}(A_1, k) = \mathrm{Ad}(SL_2(k))$. Let $g = \left(\begin{smallmatrix} a & b \\ c & d \end{smallmatrix}\right) \in GL_2(k)$ with $\mathrm{Ad}(g) = 1$. Then $g e = e g$ gives $c = 0$ and $a = d$, and $g f = f g$ gives $b = 0$. So the kernel of $\mathrm{Ad}$ on $GL_2(k)$ is the group of scalar matrices, and its kernel on $SL_2(k)$ is $\{\pm 1\}$. Therefore
$$E_{ad}(A_1, k) \cong SL_2(k) / \{\pm 1\} = PSL_2(k).$$
The Weyl element is $w_\alpha(1) = \mathrm{Ad}(u(1) v(-1) u(1))$, and $u(1) v(-1) u(1) = \left(\begin{smallmatrix} 0 & 1 \\ -1 & 0 \end{smallmatrix}\right)$, the element $n_\alpha$ of Theorem 3.2.5. For $\chi \in \mathrm{Hom}(\mathbb{Z}\alpha, k^\times)$ with $\chi(\alpha) = c$ we have $h(\chi) = \mathrm{Ad}(\mathrm{diag}(c, 1))$, since $\mathrm{diag}(c, 1)\, e\, \mathrm{diag}(c, 1)^{-1} = ce$. So $H \cdot E_{ad}(A_1, k) = \mathrm{Ad}(GL_2(k)) \cong PGL_2(k)$, and $h(\chi) \in E_{ad}(A_1, k)$ if and only if $c$ is a square (Exercise 12). For $k = \mathbb{R}$ or $k = \mathbb{F}_q$ with $q$ odd, $PSL_2(k)$ has index 2 in $PGL_2(k)$. For $k$ algebraically closed the two groups are equal, and both are $PGL_2(k) = G_{ad}(k)$.

**Example 3.6.17 (type $A_2$).** Let $\mathfrak{g} = \mathfrak{sl}_3$, with $\mathfrak{h}$ the diagonal matrices of trace 0 and the roots $\varepsilon_i - \varepsilon_j$ of Example 2.4.12. Put $e_{\varepsilon_i - \varepsilon_j} = E_{ij}$ for $i \ne j$, $h_1 = E_{11} - E_{22}$ and $h_2 = E_{22} - E_{33}$. This is a Chevalley basis. Indeed $[E_{ij}, E_{ji}] = E_{ii} - E_{jj}$ is the coroot of $\varepsilon_i - \varepsilon_j$ (Example 2.4.12). For distinct $i, j, l$ we have $[E_{ij}, E_{jl}] = E_{il}$ and $[E_{ij}, E_{li}] = -E_{lj}$. In $A_2$ no root string has more than two roots, so $r = 0$ in Theorem 3.6.9 for every pair of roots whose sum is a root, and the structure constants $\pm 1$ are the right ones. So $\mathfrak{g}_\mathbb{Z} = \mathfrak{sl}_3(\mathbb{Z})$ and $\mathfrak{g}_k = \mathfrak{sl}_3(k)$. For $E = E_{ij}$ with $i \ne j$ we have $E^2 = 0$, so $(\mathrm{ad}\, E)^2 y = -2 EyE$, $D_2 y = -EyE$ and $D_3 = 0$. Thus
$$x_{\varepsilon_i - \varepsilon_j}(t)\, y = y + t[E_{ij}, y] - t^2 E_{ij}\, y\, E_{ij} = (1 + tE_{ij})\, y\, (1 - tE_{ij}),$$
that is, $x_{\varepsilon_i - \varepsilon_j}(t) = \mathrm{Ad}(1 + tE_{ij})$. For example, with $\alpha = \varepsilon_1 - \varepsilon_2$, the element $x_\alpha(t)$ fixes $E_{12}$, $E_{13}$ and $E_{32}$, and
$$E_{23} \mapsto E_{23} + tE_{13}, \quad E_{31} \mapsto E_{31} - tE_{32}, \quad h_1 \mapsto h_1 - 2tE_{12}, \quad h_2 \mapsto h_2 + tE_{12}, \quad E_{21} \mapsto E_{21} + th_1 - t^2 E_{12}.$$
The last three agree with Proposition 3.6.12, since $\alpha(h_1) = 2$ and $\alpha(h_2) = -1$. The elementary matrices $1 + tE_{ij}$ generate $SL_3(k)$, and the kernel of $\mathrm{Ad}$ on $SL_3(k)$ is the group $\mu_3(k)$ of scalar matrices in $SL_3(k)$, by the argument of Example 3.6.16. So $E_{ad}(A_2, k) \cong PSL_3(k) = SL_3(k)/\mu_3(k)$. Example 3.2.8 now gives a relation in $E_{ad}(A_2, k)$. For $\beta = \varepsilon_2 - \varepsilon_3$,
$$x_\alpha(s)\, x_\beta(u)\, x_\alpha(s)^{-1}\, x_\beta(u)^{-1} = x_{\alpha + \beta}(su),$$
because $\mathrm{Ad}$ is a homomorphism. This is the commutator formula of Proposition 3.2.7 with $c_{11} = N_{\alpha, \beta} = 1$. It also shows directly that $X_{\alpha + \beta}$ lies in the group generated by the simple root subgroups, as Corollary 3.6.14 predicts. For $\chi \in \mathrm{Hom}(\mathbb{Z}\Phi, k^\times)$ with $\chi(\alpha) = c_1$ and $\chi(\beta) = c_2$, the element $h(\chi)$ is $\mathrm{Ad}(\mathrm{diag}(c_1 c_2, c_2, 1))$. It lies in $E_{ad}(A_2, k)$ if and only if $\mathrm{diag}(c_1 c_2, c_2, 1)$ is a scalar multiple of an element of $SL_3(k)$, that is, if and only if $c_1 c_2^2$ is a cube in $k^\times$.

The two examples suggest the general statement. The group $E_{ad}(\Phi, k)$ is always a group of $k$-points of the adjoint group, up to the difference between the full torus and the image of the simply connected torus. Over an algebraically closed field this difference disappears.

**Theorem 3.6.18 (Chevalley).** Let $k$ be algebraically closed, and let $G_{ad}$ be the split adjoint semisimple group over $k$ with root system $\Phi$, with maximal torus $T_{ad}$ (Theorem 3.6.3 and Corollary 3.6.4). There is an isomorphism of groups $G_{ad}(k) \to E_{ad}(\Phi, k)$ that maps $T_{ad}(k) = \mathrm{Hom}(\mathbb{Z}\Phi, k^\times)$ onto $H$ by $\chi \mapsto h(\chi)$, and maps each root subgroup $U_\alpha(k)$ onto $X_\alpha$. In particular $H \subset E_{ad}(\Phi, k)$.

Lean: not stated yet

*Proof sketch in characteristic 0.* Let $G = G_{ad}$, $T = T_{ad}$ and $\mathfrak{g}_k = \mathrm{Lie}(G)$. In characteristic 0 this is a semisimple Lie algebra of type $\Phi$, with Cartan subalgebra $\mathrm{Lie}(T)$, so it has a Chevalley basis adapted to $T$, by Theorem 3.6.9 and Theorem 2.6.12. In characteristic 0 the kernel of $\mathrm{Ad} \colon G \to GL(\mathfrak{g}_k)$ is the center of the connected group $G$, which is trivial by Corollary 3.3.8. So $\mathrm{Ad}$ is injective on $G(k)$, and its image lies in $\mathrm{Aut}(\mathfrak{g}_k)$. For $t \in T(k)$, $\mathrm{Ad}(t) e_\beta = \beta(t) e_\beta$, so $\mathrm{Ad}(t) = h(\chi)$ with $\chi(\beta) = \beta(t)$. Choose $u_\alpha$ as in Theorem 3.2.5 with differential $e_\alpha$ at 0. Then $t \mapsto \mathrm{Ad}(u_\alpha(t))$ is a homomorphism from $\mathbb{G}_a$ to $GL(\mathfrak{g}_k)$ with differential $\mathrm{ad}\, e_\alpha$, and in characteristic 0 such a homomorphism is $t \mapsto \exp(t\, \mathrm{ad}\, e_\alpha) = x_\alpha(t)$. By Theorem 3.2.5, $G(k)$ is generated by $T(k)$ and the groups $U_\alpha(k)$. The coroots span a subgroup of finite index of $X_*(T)$, and $k^\times$ is divisible, so $T(k) = X_*(T) \otimes k^\times$ is generated by the groups $\alpha^\vee(k^\times)$. Each $\alpha^\vee(c)$ is the image under $\varphi_\alpha$ of $\mathrm{diag}(c, c^{-1}) \in SL_2(k)$, which is a product of elementary matrices. So $G(k)$ is generated by the $U_\alpha(k)$, and $\mathrm{Ad}(G(k)) = E_{ad}(\Phi, k)$. $\square$

In positive characteristic the Lie algebra of $G_{ad}$ need not be $\mathfrak{g}_k$, and the argument above fails. Chevalley's proof instead shows directly, for $k$ algebraically closed, that $E_{ad}(\Phi, k)$ is the group of $k$-points of a connected algebraic subgroup of $GL(\mathfrak{g}_k)$. This subgroup is semisimple and adjoint, with maximal torus $H$, Borel subgroup $H \cdot \prod_{\alpha > 0} X_\alpha$ and root system $\Phi$, and Corollary 3.6.4 identifies it with $G_{ad}$. See Chevalley's Tôhoku paper and the chapter of [Ste67] on Chevalley groups as algebraic groups. Over a field that is not algebraically closed the theorem fails. For type $A_{n-1}$, $G_{ad} = PGL_n$ and $G_{ad}(k) = GL_n(k)/k^\times$ by Hilbert's Theorem 90, while $E_{ad}(A_{n-1}, k) = PSL_n(k)$ by the argument of Example 3.6.17. The quotient is $k^\times / k^{\times n}$, through the determinant. The aim of Chevalley's paper was the group $E_{ad}(\Phi, k)$ itself: for $\Phi$ irreducible it is a simple group, except for $A_1$ over $\mathbb{F}_2$ and $\mathbb{F}_3$, $B_2$ over $\mathbb{F}_2$ and $G_2$ over $\mathbb{F}_2$. Over finite fields this gave new families of finite simple groups.

**Remark 3.6.19 (Lean status).** The file `Langlands/Groups/Chevalley.lean` of the Lean project defines `Langlands.Groups.Chevalley.ElementaryAdjointChevalleyGroup` over a field $k$ of characteristic 0. The Lie algebra is `RootPairing.GeckConstruction.lieAlgebra` from Mathlib, the Lie algebra of Geck's construction for a reduced crystallographic root system over $k$ with a base, realized as a Lie algebra of matrices indexed by $\Delta \sqcup \Phi$ (Section 2.6). The group is the subgroup of the Lie algebra automorphisms generated by the simple root elements $x_{\pm\alpha_i}(t) = \exp(t\, \mathrm{ad}\, e_i)$ and $\exp(t\, \mathrm{ad}\, f_i)$, `Langlands.Groups.Chevalley.simpleRootElement` and `Langlands.Groups.Chevalley.negSimpleRootElement`, where the exponential is Mathlib's exponential of a nilpotent derivation. The file proves the one parameter group law, the formulas of Proposition 3.6.12 (`Langlands.Groups.Chevalley.expAd_apply_sl2_h`, `Langlands.Groups.Chevalley.expAd_apply_sl2_f` and their forms for $e_i$, $h_i$, $f_i$), and part 1 of Proposition 3.6.13 for $t = 1$ (`Langlands.Groups.Chevalley.weylElement_one_apply_geckE` and the analogues for $f_i$ and $h_i$). It defines $h(\chi)$ for $\chi \colon \mathbb{Z}\Phi \to k^\times$ as the conjugation by a diagonal matrix, `Langlands.Groups.Chevalley.torusElement`, and proves part 2 of Proposition 3.6.15 for the roots $\pm\alpha_i$ (`Langlands.Groups.Chevalley.torusElement_mul_simpleRootElement_mul_inv`) and part 3 (`Langlands.Groups.Chevalley.torusElement_conj_mem`). The file does not do the following. It has no root elements $x_\beta(t)$ for the roots $\beta$ that are not $\pm$ simple, so neither Corollary 3.6.14 nor the equality of its group with the group generated by all root elements is stated. It has no Chevalley basis and no integrality, so it says nothing in positive characteristic. It does not prove the Steinberg relations: the commutator formula, the relation of part 3 of Proposition 3.6.13 and the relations of the elements $h_\alpha(c)$. It does not construct the Chevalley group scheme over $\mathbb{Z}$, and it does not identify its group with $G_{ad}(k)$ as in Theorem 3.6.18.
