---
title: Unramified groups and the Satake isomorphism
nodes: []
sources: [Lan70]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Unramified groups and the Satake isomorphism

This section gives the first and most direct reason for the dual group. Let $F$ be a non-archimedean local field and let $G$ be a split reductive group over $F$ with a good model over the ring of integers. The irreducible representations of $G(F)$ with a vector fixed by $K = G(\mathcal{O})$ are classified by the semisimple conjugacy classes of the complex group $G^\vee$. The bridge is the Satake isomorphism between the spherical Hecke algebra of $G(F)$ and the ring of class functions on $G^\vee$. For $GL_n$ this is the theorem of Volume 6, Theorem 1.2.5. Here we explain how the general case comes out of the dual root datum, and we prove the parts that are short. We follow [Bor79], Section 6, and the survey of Cartier, "Representations of $p$-adic groups: a survey" (Corvallis 1979).

### Unramified groups

Let $F$ be a non-archimedean local field with ring of integers $\mathcal{O}$, uniformizer $\varpi$ and residue field of order $q$. Let $|\ |$ be the absolute value with $|\varpi| = q^{-1}$. Let $\Phi \in W_F$ be a geometric Frobenius element, as in Volume 0, Definition 3.1.2, and let $I_F$ be the inertia subgroup.

A connected reductive group $G$ over $F$ is *unramified* if it is quasi-split and splits over an unramified extension of $F$. Equivalently, the inertia group $I_F$ acts trivially on $\Psi_0(G)$. Then the action $\mu^\vee$ of Section 5.4 factors through $W_F / I_F = \Phi^{\mathbb{Z}}$, and it is determined by the pinned automorphism $\vartheta = \mu^\vee(\Phi)$ of $G^\vee$. So ${}^L G$ has the quotient $G^\vee \rtimes \langle \Phi \rangle$, where $\Phi$ acts by $\vartheta$. By a theorem of Bruhat and Tits, an unramified group has a reductive model $\mathcal{G}$ over $\mathcal{O}$, and $K = \mathcal{G}(\mathcal{O})$ is a *hyperspecial* maximal compact subgroup of $G(F)$. See Tits, "Reductive groups over local fields" (Corvallis 1979). If $G$ is split, one can take for $\mathcal{G}$ the Chevalley group scheme of the root datum, and for example $K = GL_n(\mathcal{O})$ for $G = GL_n$.

For the proofs we assume that $G$ is split, with a model over $\mathcal{O}$ such that $K = G(\mathcal{O})$, a split maximal torus $T$ and a Borel subgroup $B = TN$, all defined over $\mathcal{O}$. We write $G$, $T$, $N$ for $G(F)$, $T(F)$, $N(F)$ when no confusion is possible.

**Lemma 5.5.1 (the lattice of a split torus).** The map $\lambda \mapsto \lambda(\varpi)$ induces an isomorphism $X_*(T) \to T(F)/T(\mathcal{O})$, and it does not depend on the choice of $\varpi$.

Lean: not stated yet

*Proof.* Choose an isomorphism $T \cong \mathbb{G}_m^r$. Then $X_*(T) = \mathbb{Z}^r$, $T(F)/T(\mathcal{O}) = (F^\times/\mathcal{O}^\times)^r$, and the map is $(a_i) \mapsto (\varpi^{a_i})$. It is an isomorphism because $F^\times = \varpi^{\mathbb{Z}} \times \mathcal{O}^\times$. Another uniformizer is $u \varpi$ with $u \in \mathcal{O}^\times$, and $\lambda(u\varpi) = \lambda(u)\lambda(\varpi)$ with $\lambda(u) \in T(\mathcal{O})$. $\square$

A character $\chi : T(F) \to \mathbb{C}^\times$ is *unramified* if it is trivial on $T(\mathcal{O})$.

**Proposition 5.5.2 (unramified characters and the dual torus).** The map $\chi \mapsto t_\chi$, where $t_\chi \in T^\vee = \mathrm{Hom}(X_*(T), \mathbb{C}^\times)$ is defined by
$$\lambda(t_\chi) = \chi(\lambda(\varpi)) \qquad (\lambda \in X_*(T) = X^*(T^\vee)),$$
is a bijection from the group of unramified characters of $T(F)$ onto $T^\vee$. It is an isomorphism of groups, and it commutes with the actions of the Weyl group $W = W(G, T) = W(G^\vee, T^\vee)$.

Lean: not stated yet

*Proof.* By Lemma 5.5.1, unramified characters are the homomorphisms $X_*(T) \to \mathbb{C}^\times$, and these are the points of $T^\vee$ by Section 5.2. The map is a homomorphism. The Weyl group acts on $X_*(T)$, and the identification of $W(G, T)$ with $W(G^\vee, T^\vee)$ in Proposition 5.1.5 is the one under which the two actions on $X_*(T) = X^*(T^\vee)$ agree. $\square$

This is the simplest case of the local Langlands correspondence for tori, Volume 3, Theorem 4.5.2: unramified characters of $T(F)$ are the homomorphisms $W_F / I_F \to T^\vee$, and such a homomorphism is determined by the image $t_\chi$ of $\Phi$. Proposition 5.5.2 is also the place where the sign conventions are fixed. With a geometric Frobenius $\Phi$ and the map $\lambda \mapsto \lambda(\varpi)$ the formulas agree with Volume 0, Chapter 3. With an arithmetic Frobenius one would use $\lambda(\varpi)^{-1}$.

### The spherical Hecke algebra and the Satake transform

Fix the Haar measure $dg$ on $G(F)$ with $\mathrm{vol}(K) = 1$. The *spherical Hecke algebra* $\mathcal{H}(G, K)$ is the space of compactly supported functions $f : G(F) \to \mathbb{C}$ with $f(k_1 g k_2) = f(g)$ for $k_1, k_2 \in K$, with the convolution
$$(f_1 * f_2)(x) = \int_{G(F)} f_1(g) f_2(g^{-1} x) \, dg.$$
Let $X_*(T)^+$ be the set of dominant cocharacters, those with $\langle \alpha, \lambda \rangle \ge 0$ for all $\alpha \in \Delta$.

**Theorem 5.5.3 (Cartan and Iwasawa decompositions).**
1. $G(F) = \bigsqcup_{\lambda \in X_*(T)^+} K \lambda(\varpi) K$.
2. $G(F) = B(F) K = T(F) N(F) K$.

Lean: not stated yet

*Outline of the proof.* For $GL_n$, part 1 is the theory of elementary divisors over the principal ideal domain $\mathcal{O}$, see Volume 7, Proposition 1.4.1, and part 2 follows from column reduction. In general both parts follow from the Bruhat-Tits theory of the building, or, for split groups, from the Bruhat decomposition of $G$ over the residue field and the theory of Chevalley groups. See Cartier's survey and the paper of Tits. $\square$

By part 1, the characteristic functions $c_\lambda = \mathbf{1}_{K \lambda(\varpi) K}$ for $\lambda \in X_*(T)^+$ form a basis of $\mathcal{H}(G, K)$. Let $\delta_B(t) = |\det(\mathrm{Ad}(t) |_{\mathrm{Lie}\, N})|$ be the modulus character of $B(F)$, and let $dn$ be the Haar measure on $N(F)$ with $\mathrm{vol}(N(\mathcal{O})) = 1$. For $\lambda \in X_*(T)$ we have $\delta_B(\lambda(\varpi)) = q^{-\langle 2\rho, \lambda \rangle}$, where $2\rho$ is the sum of the positive roots.

**Definition 5.5.4 (Satake transform).** For $f \in \mathcal{H}(G, K)$ and $t \in T(F)$ put
$$\mathcal{S} f(t) = \delta_B(t)^{1/2} \int_{N(F)} f(tn) \, dn.$$
The function $\mathcal{S} f$ is invariant under $T(\mathcal{O})$ and has finite support in $T(F)/T(\mathcal{O}) = X_*(T)$. We identify it with the element $\sum_\lambda \mathcal{S}f(\lambda(\varpi)) \, e^\lambda$ of the group algebra $\mathbb{C}[X_*(T)]$, and then with a regular function on $T^\vee$, where $e^\lambda$ is the character $\lambda$ of $T^\vee$.

Let $\chi$ be an unramified character of $T(F)$, extended to $B(F)$ trivially on $N(F)$. The *unramified principal series* $I(\chi)$ is the space of locally constant functions $\varphi : G(F) \to \mathbb{C}$ with $\varphi(b g) = \delta_B(b)^{1/2} \chi(b) \varphi(g)$ for $b \in B(F)$, with $G(F)$ acting by right translation. By Theorem 5.5.3 part 2 and since $B(F) \cap K = B(\mathcal{O})$, on which $\delta_B^{1/2}\chi$ is trivial, there is a unique $\varphi_0 \in I(\chi)^K$ with $\varphi_0(1) = 1$, and $I(\chi)^K = \mathbb{C} \varphi_0$.

**Proposition 5.5.5 (action on the spherical vector).** For $f \in \mathcal{H}(G, K)$,
$$\pi(f) \varphi_0 = \mathcal{S} f(t_\chi) \, \varphi_0, \qquad \pi(f)\varphi = \int_{G(F)} f(g) \, \pi(g) \varphi \, dg,$$
where $\pi$ is the action of $G(F)$ on $I(\chi)$ and $\mathcal{S}f(t_\chi)$ is the value of the regular function $\mathcal{S} f$ at $t_\chi \in T^\vee$.

Lean: not stated yet

*Proof.* The vector $\pi(f)\varphi_0$ is fixed by $K$, so it is $c \varphi_0$ with $c = (\pi(f)\varphi_0)(1) = \int_G f(g) \varphi_0(g) \, dg$. By the Iwasawa decomposition, and since $G(F)$ is unimodular, $\int_G h(g) \, dg = \int_{B} \int_K h(bk) \, d_l b \, dk$ for a left Haar measure $d_l b$ on $B(F)$, normalized so that $B(\mathcal{O})$ has volume $1$. The measure $d_l(tn) = dt \, dn$ is left invariant on $B(F) = T(F) N(F)$, because left translation by $n' \in N(F)$ changes $n$ into $(t^{-1} n' t) n$. Both $f$ and $\varphi_0$ are right $K$-invariant, so
$$c = \int_{T(F)} \int_{N(F)} f(tn) \varphi_0(tn) \, dn \, dt = \int_{T(F)} \chi(t) \, \delta_B(t)^{1/2} \int_{N(F)} f(tn) \, dn \, dt = \int_{T(F)} \chi(t) \, \mathcal{S}f(t) \, dt.$$
With $\mathrm{vol}(T(\mathcal{O})) = 1$ the last integral is $\sum_\lambda \chi(\lambda(\varpi)) \mathcal{S}f(\lambda(\varpi)) = \sum_\lambda \mathcal{S}f(\lambda(\varpi)) \lambda(t_\chi)$, which is the value of $\mathcal{S} f$ at $t_\chi$. $\square$

### The Satake isomorphism

**Theorem 5.5.6 (Satake isomorphism, split case).** The Satake transform is an isomorphism of $\mathbb{C}$-algebras
$$\mathcal{S} : \mathcal{H}(G, K) \to \mathbb{C}[X_*(T)]^W = \mathcal{O}(T^\vee)^W.$$
For $\lambda \in X_*(T)^+$, let $m_\lambda = \sum_{\mu \in W\lambda} e^\mu$. Then
$$\mathcal{S}(c_\lambda) = q^{\langle \rho, \lambda \rangle} m_\lambda + \sum_{\mu \in X_*(T)^+, \, \mu < \lambda} a_{\lambda\mu} m_\mu,$$
where $\mu < \lambda$ means that $\lambda - \mu$ is a nonzero sum of positive coroots.

Lean: not stated yet

*Outline of the proof.* The map $\mathcal{S}$ is a homomorphism of algebras. One can see this from Proposition 5.5.5: $f \mapsto \mathcal{S}f(t_\chi)$ is the character by which $\mathcal{H}(G,K)$ acts on the line $I(\chi)^K$, so it is multiplicative for every $t_\chi \in T^\vee$, and a regular function on $T^\vee$ is determined by its values. The image is invariant under $W$, because $I(\chi)$ and $I(w\chi)$ have the same irreducible subquotients, and only one of them has a vector fixed by $K$. The triangular formula comes from the computation of $K\lambda(\varpi)K \cap \mu(\varpi) N(F)$. The leading coefficient is $\delta_B^{1/2}(\lambda(\varpi)) = q^{-\langle \rho, \lambda \rangle}$ times the volume $q^{\langle 2\rho, \lambda\rangle}$ of the set of $n \in N(F)$ with $\lambda(\varpi) n \in K \lambda(\varpi) K$. Since the $m_\mu$ for $\mu \in X_*(T)^+$ form a basis of $\mathbb{C}[X_*(T)]^W$, the triangular formula gives the bijectivity. The details are in Cartier's survey and in Gross, "On the Satake isomorphism" (1998). $\square$

The theorem has no reference to $G^\vee$ in its statement, but the ring $\mathcal{O}(T^\vee)^W$ is a ring of functions on the dual group, as follows.

**Proposition 5.5.7 (semisimple classes in the dual group).** Let $H$ be a connected reductive group over $\mathbb{C}$ with maximal torus $S$ and Weyl group $W = N_H(S)/S$. The inclusion $S \subset H$ induces a bijection $S/W \to \{\text{semisimple conjugacy classes of } H\}$.

Lean: not stated yet

*Proof.* Every semisimple element lies in a maximal torus, by Theorem 1.5.10 part 4, and all maximal tori are conjugate, by Theorem 1.6.8. So the map is surjective. Two elements of $S$ in the same $W$-orbit are conjugate under $N_H(S)$. Conversely, let $s, s' \in S$ with $s' = g s g^{-1}$ for some $g \in H$. The tori $S$ and $g S g^{-1}$ both centralize $s'$, and they are connected, so they are maximal tori of the connected group $C_H(s')^\circ$. By Theorem 1.6.8 for this group, there is $c \in C_H(s')^\circ$ with $c g S g^{-1} c^{-1} = S$. Then $n = cg \in N_H(S)$ and $n s n^{-1} = c s' c^{-1} = s'$. So $s' = w(s)$ for the image $w$ of $n$ in $W$. $\square$

The restriction of class functions gives an isomorphism $\mathcal{O}(H)^H \to \mathcal{O}(S)^W$ (Chevalley's restriction theorem), and the characters of the irreducible representations of $H$ form a basis of $\mathcal{O}(H)^H$, by the theory of highest weights of Chapter 4. So for $H = G^\vee$ and $S = T^\vee$,
$$\mathcal{H}(G, K) \cong \mathcal{O}(T^\vee)^W \cong \mathcal{O}(G^\vee)^{G^\vee} \cong R(G^\vee) \otimes_{\mathbb{Z}} \mathbb{C},$$
where $R(G^\vee)$ is the representation ring. The characters of $\mathcal{H}(G, K)$ are the points of $T^\vee / W$, that is, the semisimple conjugacy classes of $G^\vee$.

### Unramified representations

An irreducible smooth representation $\pi$ of $G(F)$ is *unramified* (or *spherical*) if $\pi^K \ne 0$. Then $\mathcal{H}(G, K)$ is commutative by Theorem 5.5.6, and $\pi^K$ is a one-dimensional simple module over it, by Volume 6, Proposition 1.2.4 and its proof. So $\pi$ defines a character of $\mathcal{H}(G, K)$.

**Corollary 5.5.8 (Satake parameters).** The map that sends an unramified irreducible representation $\pi$ to the character of $\mathcal{H}(G, K)$ on $\pi^K$ is a bijection onto the set of characters. So there is a bijection
$$\pi \mapsto s(\pi), \qquad \{\text{unramified irreducible } \pi\}/\cong \ \longrightarrow \ \{\text{semisimple conjugacy classes in } G^\vee\},$$
characterized by $\mathrm{tr}\, \pi(f) = \mathcal{S}f(s(\pi))$ for $f \in \mathcal{H}(G, K)$. The class $s(\pi)$ is the *Satake parameter* of $\pi$. If $\pi$ is a subquotient of $I(\chi)$, then $s(\pi)$ is the class of $t_\chi$.

Lean: not stated yet

*Outline of the proof.* Injectivity is the general fact that an irreducible representation generated by its $K$-fixed vectors is determined by the action of $\mathcal{H}(G, K)$ on them. For surjectivity, let $t \in T^\vee$ and let $\chi$ be the unramified character with $t_\chi = t$. The representation $I(\chi)$ has finite length, and by Proposition 5.5.5 the line $I(\chi)^K$ carries the character $f \mapsto \mathcal{S}f(t)$. Since taking $K$-invariants is exact, exactly one irreducible subquotient of $I(\chi)$ has a nonzero $K$-fixed vector. The fact that every unramified $\pi$ is a subquotient of some $I(\chi)$ is a theorem of Borel and Matsumoto, see Cartier's survey. $\square$

**Example 5.5.9 (GL_n).** For $G = GL_n$ and $\chi(\mathrm{diag}(t_1, \dots, t_n)) = \prod_i \chi_i(t_i)$, Proposition 5.5.2 gives $t_\chi = \mathrm{diag}(\chi_1(\varpi), \dots, \chi_n(\varpi)) \in GL_n(\mathbb{C})$. The Satake parameter of the unramified subquotient of $I(\chi)$ is the conjugacy class of this matrix. This agrees with Volume 6, Theorem 1.2.5 and Volume 7, Theorem 1.4.5. If $\pi$ is tempered, the eigenvalues have absolute value $1$, which is the unitary normalization of Volume 0, Section 3.2. The project library has `Langlands.satake`, which gives the multiset of Satake parameters of an unramified representation of $GL_n$ from its Hecke eigenvalues.

**Example 5.5.10 (PGL_2 and SL_2).** Let $G = PGL_2$. Then $X_*(T) = \mathbb{Z}\lambda$, where $\lambda(s)$ is the image of $\mathrm{diag}(s, 1)$, and $T^\vee = \{\mathrm{diag}(z, z^{-1})\} \subset SL_2(\mathbb{C})$, with $e^\lambda$ the function $z$. The Weyl group exchanges $z$ and $z^{-1}$, so $\mathcal{O}(T^\vee)^W = \mathbb{C}[z + z^{-1}]$. The Hecke operator $c_\lambda = \mathbf{1}_{K \lambda(\varpi) K}$ has
$$\mathcal{S}(c_\lambda) = q^{1/2}(z + z^{-1}),$$
which is Exercise 7. The Satake parameter of an unramified representation $\pi$ of $PGL_2(F)$ is the class of $\mathrm{diag}(z, z^{-1})$ in $SL_2(\mathbb{C})$, where $q^{1/2}(z + z^{-1})$ is the eigenvalue of $c_\lambda$ on $\pi^K$. For $G = SL_2$, we have $X_*(T) = \mathbb{Z}\mu$ with $\mu(s) = \mathrm{diag}(s, s^{-1})$, and $T^\vee$ is the image of the diagonal torus in $PGL_2(\mathbb{C})$. If $\pi$ is an unramified representation of $GL_2(F)$ with Satake parameter $\mathrm{diag}(a, b)$, then the unramified constituent of its restriction to $SL_2(F)$ has Satake parameter the image of $\mathrm{diag}(a, b)$ in $PGL_2(\mathbb{C})$. This is the dual isogeny of Example 5.2.8 at work.

### The unramified case in general

Let $G$ be unramified, with hyperspecial $K$, and let $\vartheta$ be the pinned automorphism of $G^\vee$ given by $\Phi$. Let $A \subset T$ be a maximal split torus in a maximal torus $T$ of a Borel subgroup over $F$, and let $W_0 = W(G, A)$ be the relative Weyl group.

**Theorem 5.5.11 (Satake isomorphism, unramified case).** There is an isomorphism of algebras $\mathcal{H}(G, K) \cong \mathbb{C}[X_*(A)]^{W_0}$. The algebra $\mathbb{C}[X_*(A)]^{W_0}$ is the ring of regular functions on the set of semisimple $G^\vee$-conjugacy classes in the coset $G^\vee \rtimes \Phi$ of ${}^L G$, and also the ring of functions on $(T^\vee)_\vartheta / W^\vartheta$. So the unramified irreducible representations of $G(F)$ correspond to the semisimple $G^\vee$-conjugacy classes in $G^\vee \rtimes \Phi$.

Lean: not stated yet

*Outline of the proof.* The Satake transform is defined as above with $A$ in place of $T$, and the proof of Theorem 5.5.6 applies with the relative root system. The identification of the image with functions on $G^\vee \rtimes \Phi$ is [Bor79], Section 6: every semisimple element of $G^\vee \rtimes \Phi$ is conjugate to an element $t \rtimes \Phi$ with $t \in T^\vee$, and two such elements are conjugate if and only if their images in the coinvariants $(T^\vee)_\vartheta$ are conjugate under $W^\vartheta$. The torus $(T^\vee)_\vartheta$ has character group $X_*(T)^\vartheta = X_*(A)$, and $W^\vartheta = W_0$. $\square$

For split $G$, the coset $G^\vee \rtimes \Phi$ is $G^\vee \times \{\Phi\}$, and we get Corollary 5.5.8 back.

### Unramified L-factors

The Satake parameter gives L-functions. Let $r : {}^L G \to GL_m(\mathbb{C})$ be a representation whose restriction to $G^\vee$ is algebraic, and whose restriction to $W_F$ is trivial on $I_F$ and continuous.

**Definition 5.5.12 (unramified L-factor).** For an unramified irreducible representation $\pi$ of $G(F)$ with Satake parameter $s(\pi) \rtimes \Phi$, the *local L-factor* is
$$L(s, \pi, r) = \det\big(1 - r(s(\pi) \rtimes \Phi) \, q^{-s}\big)^{-1}.$$

The determinant depends only on the conjugacy class of $s(\pi) \rtimes \Phi$, so the factor is well defined. For $G = GL_n$, $r$ the standard representation and $s(\pi) = \mathrm{diag}(\alpha_1, \dots, \alpha_n)$, we get $L(s, \pi, r) = \prod_i (1 - \alpha_i q^{-s})^{-1}$, the factor of the standard L-function of Volume 6, Chapter 1. For a global field and an automorphic representation $\pi = \otimes_v \pi_v$, unramified outside a finite set $S$, Langlands defined in [Lan70] the partial L-function $L^S(s, \pi, r) = \prod_{v \notin S} L(s, \pi_v, r_v)$. He conjectured its meromorphic continuation and functional equation. Exercise 11 computes the factor for $\mathrm{Sym}^2$ on $GL_2$.
