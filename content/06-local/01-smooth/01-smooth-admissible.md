---
title: Smooth and admissible representations
nodes: []
sources: [BH06]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Smooth and admissible representations

The groups of this chapter are the groups $G = \mathbf{G}(K)$ of points of a connected reductive group $\mathbf{G}$ over $K$. The main examples are $GL_n(K)$, $SL_n(K)$ and $GSp_4(K)$. Such a group is locally compact and totally disconnected. The only property of the topology that we use in this section is the following one.

### Groups with small compact open subgroups

An *$\ell$-group* is a Hausdorff topological group in which the compact open subgroups form a basis of neighbourhoods of the identity. The term is that of Bernstein and Zelevinsky. For $G = GL_n(K)$ the groups $K_0 = GL_n(\mathcal{O}_K)$ and
$$K_r = 1 + \varpi^r M_n(\mathcal{O}_K) \quad (r \ge 1)$$
are compact open subgroups, and they form a basis of neighbourhoods of $1$. Each $K_r$ is normal in $K_0$. The group $K_0$ is a maximal compact subgroup of $G$, and every compact subgroup of $G$ is conjugate to a subgroup of $K_0$. The quotient $G / K_0$ is countable, because $G = \bigsqcup K_0 \varpi^{\lambda} K_0$ (the Cartan decomposition) with $\lambda$ in the countable set of decreasing sequences of integers, and each double coset is a finite union of cosets $g K_0$. So $G$ is countable at infinity. The same holds for each reductive group over $K$.

Each $\ell$-group has a left Haar measure, unique up to a positive scalar. If $J' \subseteq J$ are compact open subgroups, then $\mathrm{vol}(J) = [J : J'] \, \mathrm{vol}(J')$. A reductive group is unimodular: its left and right Haar measures are equal. A parabolic subgroup $P$ is not unimodular, and its modulus character is used in Section 1.3.

### Smooth representations

**Definition 1.1.1 (smooth representation).** Let $G$ be an $\ell$-group. A *representation* $(\pi, V)$ of $G$ is a complex vector space $V$ with a homomorphism $\pi : G \to GL(V)$. A vector $v \in V$ is *smooth* if its stabilizer $\{g \in G : \pi(g) v = v\}$ is open in $G$. The representation is *smooth* if each vector is smooth. A *morphism* of representations is a linear map that commutes with the actions of $G$.

Lean: `Langlands.SmoothRep`. The Lean structure bundles the space, the action and the smoothness, which asks for an open stabilizer of each vector as in the definition, and its space is in the universe of $G$, so that the isomorphism classes form a type.

The definition puts no topology on $V$. The smooth vectors of any representation form a stable subspace, and on this subspace $G$ acts smoothly. A vector $v$ is smooth if and only if $v \in V^J$ for some compact open subgroup $J$, where $V^J$ is the space of $J$-fixed vectors. So $V$ is smooth if and only if $V = \bigcup_J V^J$, with $J$ running over the compact open subgroups. The smooth representations of $G$ form an abelian category. Subrepresentations, quotients, direct sums and tensor products with finite-dimensional smooth representations are smooth.

Lean: `Langlands.smoothVectors`, `Langlands.isGreatest_smoothVectors`, `Langlands.SmoothRep.sub`, `Langlands.SmoothRep.quotient`, `Langlands.SmoothRep.prod`. The Lean theorem `isGreatest_smoothVectors` says a little more than the text: the smooth vectors are the largest stable subspace on which $G$ acts smoothly, and tensor products are not in Lean.

**Definition 1.1.2 (admissible and irreducible representation).** A smooth representation $(\pi, V)$ of $G$ is *admissible* if $V^J$ has finite dimension for each compact open subgroup $J$. It is *irreducible* if $V \ne 0$ and the only stable subspaces of $V$ are $0$ and $V$.

Lean: `Langlands.SmoothRep.IsAdmissible` and `Langlands.SmoothRep.IsIrreducible`. Irreducibility is as in the text, and admissibility is asked for each open subgroup $U$ in place of each compact open subgroup $J$, which is the same condition by the next paragraph.

The Lean definition of admissibility asks that $V^U$ has finite dimension for each open subgroup $U$. An open subgroup contains a compact open subgroup $J$, and $V^U \subseteq V^J$, so this is the same condition. A subrepresentation $W$ of an admissible representation $V$ is admissible, since $W^J = W \cap V^J$.

Lean: `Langlands.SmoothRep.IsAdmissible.sub`. The Lean proof is the one of the text: it maps $W^U$ injectively into $V^U$.

 The isomorphism classes of irreducible admissible representations are `Langlands.IrrSmooth G` in the Lean project. Theorem 1.1.11 below shows that for a reductive group the word admissible can be left out.

**Example 1.1.3 (first examples).**
1. A *smooth character* of $G$ is a homomorphism $\theta : G \to \mathbb{C}^\times$ with open kernel. It is an irreducible admissible representation of dimension one. For $G = K^\times$ the smooth characters are the characters of Volume 3, Chapter 4, since a continuous character of $K^\times$ has open kernel. For $G = GL_n(K)$ each smooth character has the form $\chi \circ \det$ (Exercise 1).
2. The group $G$ acts on the space $C_c^\infty(G)$ of locally constant functions with compact support by $(\rho(h) f)(g) = f(gh)$. This representation is smooth. It is not admissible when $G$ is not compact, since $C_c^\infty(G)^J$ contains the characteristic functions of the cosets $xJ$, which are infinitely many.
3. Let $B$ be the group of upper triangular matrices of $GL_2(K)$. The space $V$ of the introduction, of locally constant functions $f$ on $G$ with $f(bg) = f(g)$, is smooth. Since $G = B K_0$, the restriction to $K_0$ identifies $V$ with the locally constant functions on $(B \cap K_0) \backslash K_0 = \mathbb{P}^1(\mathcal{O}_K)$. So $V^{K_r}$ is the space of functions on the finite set $\mathbb{P}^1(\mathcal{O}_K / \mathfrak{p}^r)$, and $V$ is admissible.
4. A finite-dimensional smooth representation of $GL_n(K)$ is trivial on $SL_n(K)$. Indeed its kernel is an open normal subgroup. It contains each elementary unipotent matrix $1 + x E_{ij}$, since this matrix is conjugate under the diagonal torus to $1 + y E_{ij}$ with $|y|$ as small as we wish. These matrices generate $SL_n(K)$. So the irreducible finite-dimensional smooth representations of $GL_n(K)$ are the characters $\chi \circ \det$. All the other irreducible representations are infinite-dimensional.

### Averaging over a compact open subgroup

Let $J$ be a compact open subgroup of $G$ and let $dj$ be the Haar measure of $J$ with total volume $1$. For a smooth representation $V$ and $v \in V$, the vector $\pi(j) v$ takes only finitely many values as $j$ runs over $J$, because the stabilizer of $v$ is open. So the integral
$$e_J v = \int_J \pi(j) v \, dj$$
is a finite sum. It is a $J$-fixed vector, and $e_J v = v$ when $v \in V^J$.

**Proposition 1.1.4 (the functor of $J$-fixed vectors).** Let $J$ be a compact open subgroup of $G$.
1. The map $e_J$ is a projection of $V$ onto $V^J$. Its kernel $V(J)$ is spanned by the vectors $\pi(j) v - v$ with $j \in J$ and $v \in V$, and $V = V^J \oplus V(J)$.
2. The functor $V \mapsto V^J$ from smooth representations of $G$ to vector spaces is exact.

Lean: not stated yet

*Proof.* The map $e_J$ is the identity on $V^J$, and its image is in $V^J$, so it is a projection. Each vector $\pi(j) v - v$ is in the kernel. Conversely, let $v$ be in the kernel. Choose an open normal subgroup $J'$ of $J$ that fixes $v$. Then $e_J v = [J : J']^{-1} \sum_{j \in J / J'} \pi(j) v$, so $v = v - e_J v = [J : J']^{-1} \sum_j (v - \pi(j) v)$. This proves part 1. For part 2, let $0 \to U \to V \to W \to 0$ be exact. The functor of $J$-fixed vectors is left exact for every group. Let $w \in W^J$ and let $v \in V$ map to $w$. Then $e_J v \in V^J$ maps to $e_J w = w$. So $V^J \to W^J$ is surjective. $\square$

Part 2 fails for a group that is not compact. For example the map $C_c^\infty(K) \to \mathbb{C}$, $f \mapsto \int f$, is surjective and $K$-equivariant for the translation action and the trivial action, but $C_c^\infty(K)^K = 0$.

### The contragredient

**Definition 1.1.5 (contragredient).** Let $(\pi, V)$ be a smooth representation of $G$. The group $G$ acts on the dual space $V^*$ by $(\pi^*(g) \lambda)(v) = \lambda(\pi(g^{-1}) v)$. The *contragredient* $(\pi^\vee, V^\vee)$ is the subrepresentation of the smooth vectors of $V^*$.

Lean: `Langlands.SmoothRep.contragredient`. As in the text, it is the subrepresentation of the dual representation on `Langlands.smoothVectors`.

A linear form $\lambda$ is smooth if and only if it is fixed by some compact open subgroup $J$. By Proposition 1.1.4, such a form vanishes on $V(J)$, and it is determined by its restriction to $V^J$. So $(V^\vee)^J = (V^J)^*$.

**Proposition 1.1.6 (admissible duality).** Let $(\pi, V)$ be admissible. Then $\pi^\vee$ is admissible, the natural map $V \to (V^\vee)^\vee$ is an isomorphism, and $\pi$ is irreducible if and only if $\pi^\vee$ is irreducible.

Lean: not stated yet

*Proof.* The space $(V^\vee)^J = (V^J)^*$ has finite dimension, so $\pi^\vee$ is admissible. Then $((V^\vee)^\vee)^J = ((V^J)^*)^* = V^J$, and the natural map is the canonical map of the finite-dimensional space $V^J$ to its double dual. Take the union over $J$. If $U \subseteq V$ is a stable subspace, its annihilator in $V^\vee$ is stable, and $U$ is the annihilator of the annihilator, since $U^J$ is determined by its annihilator in $(V^J)^*$. So the stable subspaces of $V$ and of $V^\vee$ correspond, and the last claim follows. $\square$

For $G = GL_n(K)$ there is a second description of the contragredient. Gelfand and Kazhdan proved that $\pi^\vee$ is isomorphic to the representation $g \mapsto \pi({}^t g^{-1})$ for each irreducible $\pi$. For $n = 2$ this gives $\pi^\vee \cong \pi \otimes \omega_\pi^{-1}$, where $\omega_\pi$ is the central character of Corollary 1.1.8, since ${}^t g^{-1} = \det(g)^{-1} w g w^{-1}$ with $w = \left(\begin{smallmatrix} 0 & 1 \\ -1 & 0 \end{smallmatrix}\right)$.

### Schur's lemma

**Theorem 1.1.7 (Schur's lemma).** Let $G$ be an $\ell$-group that is countable at infinity, and let $(\pi, V)$ be an irreducible smooth representation of $G$. Then each endomorphism of $\pi$ is a scalar.

Lean: not stated yet

*Proof.* This is the argument of Jacquet. Fix $0 \ne v \in V$. Then $V$ is spanned by the vectors $\pi(g) v$, and these take countably many values, since $g \mapsto \pi(g) v$ is constant on the cosets of the open stabilizer of $v$ and $G$ has countably many such cosets. So $V$ has countable dimension. Let $D = \mathrm{End}_G(V)$. Each nonzero $T \in D$ is injective and surjective, since its kernel and its image are stable. So $D$ is a division algebra over $\mathbb{C}$. The map $T \mapsto T v$ is injective on $D$, so $D$ has countable dimension. Let $T \in D$ and suppose that $T$ is not a scalar. Then $T$ is transcendental over $\mathbb{C}$, since $\mathbb{C}$ is algebraically closed, and $\mathbb{C}(T) \subseteq D$ is a field isomorphic to the field of rational functions. The elements $(T - a)^{-1}$ with $a \in \mathbb{C}$ are linearly independent, by partial fractions, and there are uncountably many of them. This contradicts the countable dimension of $D$. $\square$

For an admissible $\pi$ the proof is simpler. Choose $J$ with $V^J \ne 0$. The space $V^J$ has finite dimension and is stable under $T$, so $T$ has an eigenvalue $c$ on $V^J$. Then $T - c$ is an endomorphism with a nonzero kernel, so $T - c = 0$.

**Corollary 1.1.8 (central character).** Let $(\pi, V)$ be an irreducible smooth representation of $G$, with $G$ countable at infinity, and let $Z$ be the center of $G$. There is a smooth character $\omega_\pi$ of $Z$ with $\pi(z) = \omega_\pi(z)$ for each $z \in Z$. It is the *central character* of $\pi$.

Lean: `Langlands.SmoothRep.HasCentralChar`. This is only the relation $\pi(a \cdot 1) = \omega(a)$ for $G = GL_n(K)$, so the existence of $\omega_\pi$ is not stated in Lean.

*Proof.* Each $\pi(z)$ is an endomorphism of $\pi$, so it is a scalar $\omega_\pi(z)$ by Theorem 1.1.7. The kernel of $\omega_\pi$ is the stabilizer in $Z$ of any nonzero vector, so it is open. $\square$

For $G = GL_n(K)$ the center is $K^\times$, embedded by $a \mapsto a \cdot 1$. The Lean project calls this embedding `Langlands.scalarGL`, and `HasCentralChar π ω` says that $\pi(a \cdot 1) = \omega(a)$ for each $a \in K^\times$. The Lean project proves the case $n = 1$: the representation of $GL_1(K)$ given by a smooth character $\chi$ of $K^\times$ has central character $\chi$. This is `Langlands.charRep_hasCentralChar`, in the file `Langlands/Statements/LocalLanglands.lean`.

### Twists, and the Lean vocabulary

Let $\theta$ be a smooth character of $G$ and $\pi$ a smooth representation. The *twist* $\pi \otimes \theta$ is the representation $g \mapsto \theta(g) \pi(g)$ on the same space. It is smooth, admissible if $\pi$ is, and irreducible if $\pi$ is. For $G = GL_n(K)$ and a character $\chi$ of $K^\times$ we write $\pi \otimes \chi$ for $\pi \otimes (\chi \circ \det)$. Then $\omega_{\pi \otimes \chi} = \omega_\pi \chi^n$.

**Definition 1.1.9 (the irreducible representations).** Let $G$ be an $\ell$-group. Then $\mathrm{Irr}(G)$ is the set of isomorphism classes of irreducible admissible representations of $G$. For $\chi$ a smooth character, $[\pi] \mapsto [\pi \otimes \chi]$ and $[\pi] \mapsto [\pi^\vee]$ are well defined maps of $\mathrm{Irr}(G)$.

Lean: `Langlands.IrrSmooth`. In Lean the two maps of the definition are relations on representatives, see Remark 1.1.10.

**Remark 1.1.10 (the Lean vocabulary).** The file `Langlands/Statements/Smooth.lean` defines a bundled smooth representation `Langlands.SmoothRep G` of a topological group $G$. Its carrier is a complex vector space with no topology, and smoothness says that each vector has an open stabilizer, as in Definition 1.1.1. The twist is `SmoothRep.twist`, by a character with open kernel. The contragredient is `SmoothRep.contragredient`, the smooth vectors of the dual. The relations `IrrSmooth.IsTwist` and `IrrSmooth.IsContragredient` on $\mathrm{Irr}(G)$ are defined on representatives: `IsTwist y x θ` says that $y$ is the class of $\pi \otimes \theta$ for a representative $\pi$ of $x$. The file also defines matrix coefficients (`SmoothRep.coeff`), restriction along a continuous homomorphism (`SmoothRep.restrict`), subrepresentations on stable subspaces (`SmoothRep.sub`), and the relation `SmoothRep.HasHom` of a nonzero morphism. Two small facts are proved: `Langlands.SmoothRep.charRep_isIrreducible` says that the representation of a smooth character is irreducible and admissible, and `Langlands.SmoothRep.charRep_iso_iff` says that two characters give isomorphic representations only if they are equal. None of these declarations is a node of the map. They are the vocabulary of the statements of Chapter 3. The file `Langlands/Smooth/Induction.lean` builds on this vocabulary. It proves the facts on smooth vectors and on subrepresentations stated above, and it defines induction and Jacquet modules, see Section 1.3.

**Theorem 1.1.11 (Jacquet, Bernstein).** Let $G$ be the group of points of a connected reductive group over $K$. Each irreducible smooth representation of $G$ is admissible.

Lean: not stated yet

*Sketch of proof.* For $GL_n(K)$ the theorem is due to Jacquet, and for general $G$ to Bernstein. We give the outline for $GL_n$, which uses Section 1.4. Let $\pi$ be irreducible. If $\pi$ is supercuspidal, its matrix coefficients have compact support modulo the center, by Theorem 1.4.3. Then $\pi$ is a direct summand of a space of functions with compact support modulo the center, and an argument with the Hecke algebra shows that $V^J$ has finite dimension (Theorem 1.4.5). If $\pi$ is not supercuspidal, a Jacquet module of $\pi$ is not zero. A Jacquet module of a finitely generated representation is finitely generated, so it has an irreducible quotient $\sigma$. By Frobenius reciprocity, $\pi$ embeds in a representation induced from $\sigma$, and by induction on $n$ we may take $\sigma$ admissible. Induction preserves admissibility (Proposition 1.3.4), so $\pi$ is admissible. $\square$

By Theorem 1.1.11, the set $\mathrm{Irr}(GL_n(K))$ is the set of isomorphism classes of irreducible smooth representations. The docstring of `Langlands.IrrSmooth` says the same thing.
