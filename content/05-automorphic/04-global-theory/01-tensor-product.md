---
title: The tensor product theorem
nodes: []
sources: [JL70]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## The tensor product theorem

An irreducible representation of a finite product of groups is a tensor product of irreducible representations of the factors. The adele group $G(\mathbb{A})$ is a restricted product of the local groups $G_v$, and the analogue of this fact for $G(\mathbb{A})$ is the tensor product theorem. It is due to Flath, and to Jacquet and Langlands for the main case. This section defines the restricted tensor product, proves that the spherical Hecke algebra of $G_p$ is commutative, and deduces the part of the theorem that concerns the unramified places.

### Restricted tensor products

Let $\{V_v\}$ be a family of complex vector spaces indexed by the places $v$ of $\mathbb{Q}$. For almost all $v$ fix a nonzero vector $\xi_v^\circ \in V_v$. For each finite set $S$ of places, put $V_S = \bigotimes_{v \in S} V_v$. If $S \subset S'$ and $\xi_v^\circ$ is defined for $v \in S' \smallsetminus S$, then the map $x \mapsto x \otimes \bigotimes_{v \in S' \smallsetminus S}\xi_v^\circ$ is an injection $V_S \to V_{S'}$.

**Definition 4.1.1 (restricted tensor product).** The *restricted tensor product* $\bigotimes'_v V_v$ of the spaces $V_v$ with respect to the vectors $\xi_v^\circ$ is the direct limit of the spaces $V_S$ over the finite sets $S$ that contain all the places where $\xi_v^\circ$ is not defined, with the injections above.

A *pure tensor* is the image of an element $\bigotimes_{v \in S}x_v$ of some $V_S$. We write it $\bigotimes_v x_v$, with $x_v = \xi_v^\circ$ for $v \notin S$. The pure tensors span $\bigotimes'_v V_v$. Suppose that each $V_v$ carries a representation $\pi_v$ of $G_v$, and that for almost all $p$ the vector $\xi_p^\circ$ is fixed by $K_p$. Then $G(\mathbb{A})$ acts on the pure tensors by $g \cdot \bigotimes_v x_v = \bigotimes_v \pi_v(g_v)x_v$. This is well defined, because $g_p \in K_p$ for almost all $p$, and it gives a representation $\pi = \bigotimes'_v \pi_v$ of $G(\mathbb{A})$. At the real place we use $(\mathfrak{g}, K_\infty)$-modules, as in Chapter 2.

The isomorphism class of $\pi$ does not depend on the choice of the vectors $\xi_p^\circ$, provided that each $\pi_p^{K_p}$ is a line for almost all $p$. Two choices differ by nonzero scalars at almost all places, and the map that rescales each pure tensor is an isomorphism. This is the situation of Corollary 4.1.5 below.

**Definition 4.1.2 (admissible representations of the adele group).** A $(\mathfrak{g}, K_\infty) \times G(\mathbb{A}_f)$-module $(\pi, V)$ is *smooth* if each vector is fixed by an open subgroup of $G(\mathbb{A}_f)$ and is $K_\infty$-finite. It is *admissible* if, in addition, for each open compact subgroup $K' \subset G(\mathbb{A}_f)$ and each irreducible representation $\tau$ of $K_\infty$, the $\tau$-isotypic part of $V^{K'}$ is finite-dimensional.

An open compact subgroup of $G(\mathbb{A}_f)$ contains a group $K_S' \times K^S$, where $S$ is a finite set of primes, $K_S'$ is open compact in $\prod_{p \in S}G_p$ and $K^S = \prod_{p \notin S}K_p$. So in Definition 4.1.2 it suffices to take $K'$ of this form.

### The spherical Hecke algebra

Let $p$ be a prime. Fix the Haar measure on $G_p$ with $\mathrm{vol}(K_p) = 1$. The *Hecke algebra* $\mathcal{H}(G_p)$ is the space of locally constant functions with compact support on $G_p$, with the convolution
$$(f_1 * f_2)(g) = \int_{G_p} f_1(h)f_2(h^{-1}g)\,dh.$$
For an open compact subgroup $K \subset G_p$, $\mathcal{H}(G_p, K)$ is the subalgebra of the functions that are left and right invariant under $K$. Its unit is $e_K = \mathrm{vol}(K)^{-1}1_K$. A smooth representation $\pi$ of $G_p$ gives the operators $\pi(f) = \int_{G_p} f(g)\pi(g)\,dg$, and $\pi(f_1 * f_2) = \pi(f_1)\pi(f_2)$. The operator $\pi(e_K)$ is a projection of $\pi$ onto $\pi^K$, and $\mathcal{H}(G_p, K)$ acts on $\pi^K$.

**Lemma 4.1.3 (Gelfand).** The algebra $\mathcal{H}(G_p, K_p)$ is commutative.

Lean: not formalized

*Proof.* Let $\iota(g) = {}^tg$ be the transpose. It is an anti-automorphism of $G_p$, it maps $K_p$ to $K_p$, and it preserves the Haar measure, since $G_p$ is unimodular and $\iota$ maps $K_p$ onto itself. For $f \in \mathcal{H}(G_p, K_p)$ put $f^\iota = f \circ \iota$. The change of variables $h \mapsto \iota(h^{-1}g)$ in the convolution gives
$$(f_1 * f_2)^\iota(g) = \int f_1(h)f_2(h^{-1}\,{}^tg)\,dh = \int f_2^\iota(h')f_1^\iota(h'^{-1}g)\,dh' = (f_2^\iota * f_1^\iota)(g).$$
So $f \mapsto f^\iota$ is an anti-automorphism of $\mathcal{H}(G_p, K_p)$. By the Cartan decomposition (Chapter 3), each double coset $K_pgK_p$ contains a diagonal matrix $\mathrm{diag}(p^a, p^b)$. A diagonal matrix is its own transpose, so $\iota$ maps each double coset onto itself. A function in $\mathcal{H}(G_p, K_p)$ is constant on the double cosets, so $f^\iota = f$ for all $f$. Then $f_1 * f_2 = (f_1 * f_2)^\iota = f_2^\iota * f_1^\iota = f_2 * f_1$. $\square$

Chapter 3 describes this algebra completely: by the Satake isomorphism it is the polynomial algebra $\mathbb{C}[T_p, R_p, R_p^{-1}]$, where $T_p$ is the characteristic function of $K_p a(p) K_p$ and $R_p$ is the characteristic function of $pK_p$. For the global theory we only need commutativity, and then the classification of the characters of this algebra.

**Lemma 4.1.4 (irreducibility of the fixed vectors).** Let $\pi$ be an irreducible smooth representation of $G_p$ and let $K \subset G_p$ be an open compact subgroup with $\pi^K \ne 0$. Then $\pi^K$ is an irreducible $\mathcal{H}(G_p, K)$-module.

Lean: not formalized

*Proof.* Let $W \subset \pi^K$ be a nonzero submodule and let $w \in W$ be nonzero. Let $v \in \pi^K$. Since $\pi$ is irreducible, $v = \sum_i c_i \pi(g_i)w$ for some $c_i \in \mathbb{C}$ and $g_i \in G_p$. Apply $\pi(e_K)$. Since $v$ and $w$ are fixed by $K$,
$$v = \pi(e_K)v = \sum_i c_i \pi(e_K)\pi(g_i)\pi(e_K)w = \sum_i c_i \pi(e_K * \delta_{g_i} * e_K)w,$$
where $\delta_g$ is the point mass at $g$. The function $e_K * \delta_g * e_K$ is locally constant, supported on $KgK$ and invariant under $K$ on both sides, so it lies in $\mathcal{H}(G_p, K)$. So $v \in W$, and $W = \pi^K$. $\square$

**Corollary 4.1.5 (spherical vectors are unique).** Let $\pi$ be an irreducible admissible representation of $G_p$. Then $\dim \pi^{K_p} \le 1$.

Lean: not formalized

*Proof.* The space $\pi^{K_p}$ is finite-dimensional by admissibility. If it is nonzero, it is an irreducible module over the commutative algebra $\mathcal{H}(G_p, K_p)$ by Lemma 4.1.3 and Lemma 4.1.4. The operators of a commutative algebra on a nonzero finite-dimensional complex space have a common eigenvector. Its line is a submodule, so it is all of $\pi^{K_p}$. $\square$

An irreducible admissible representation $\pi_p$ with $\pi_p^{K_p} \ne 0$ is *unramified*, or *spherical*. Then $\mathcal{H}(G_p, K_p)$ acts on the line $\pi_p^{K_p}$ by a character $\lambda_{\pi_p}$. By Chapter 3, $\pi_p$ is then an irreducible subquotient of an unramified principal series $\chi_1 \times \chi_2$, and the pair $\{\chi_1(p), \chi_2(p)\}$ determines $\lambda_{\pi_p}$ and is determined by it. So an unramified representation is determined by its character of the spherical Hecke algebra, and each character of $\mathcal{H}(G_p, K_p)$ is $\lambda_{\pi_p}$ for exactly one unramified $\pi_p$. We compute this character in Section 4.2.

### The theorem

**Theorem 4.1.6 (tensor product theorem, Flath).** Let $\pi$ be an irreducible admissible $(\mathfrak{g}, K_\infty) \times G(\mathbb{A}_f)$-module. Then there are an irreducible admissible $(\mathfrak{g}, K_\infty)$-module $\pi_\infty$ and irreducible admissible representations $\pi_p$ of $G_p$, with $\pi_p$ unramified for almost all $p$, such that
$$\pi \cong \textstyle\bigotimes'_v \pi_v,$$
where the restricted tensor product is taken with respect to nonzero vectors $\xi_p^\circ \in \pi_p^{K_p}$. The representations $\pi_v$ are unique up to isomorphism. Conversely, each such restricted tensor product is irreducible and admissible.

Lean: not formalized

The components $\pi_v$ are the *local components* of $\pi$. The proof has two parts of different nature. At the unramified places the commutative Hecke algebra does the work, and the proof is short. At the finitely many other places one needs a tensor product lemma for modules over a tensor product of algebras that are not commutative. We give the first part in full and the second in outline.

**Proposition 4.1.7 (the unramified places).** Let $\pi$ be an irreducible admissible $(\mathfrak{g}, K_\infty) \times G(\mathbb{A}_f)$-module on a space $V$. There is a finite set $S$ of primes with $V^{K^S} \ne 0$, where $K^S = \prod_{p \notin S}K_p$. For such $S$ and each $p \notin S$, the algebra $\mathcal{H}(G_p, K_p)$ acts on $V^{K^S}$ by a character $\lambda_p$. So there is a unique unramified representation $\pi_p$ of $G_p$ with $\lambda_{\pi_p} = \lambda_p$, and $\pi_p$ depends only on $\pi$ and $p$.

Lean: not formalized

*Proof.* A nonzero vector of $V$ is fixed by an open compact subgroup of $G(\mathbb{A}_f)$, and this subgroup contains some $K_S' \times K^S$. So $V^{K^S} \ne 0$. Put $G_S = \prod_{p \in S}G_p$. The space $V^{K^S}$ is a module over the $(\mathfrak{g}, K_\infty)$-action, over $G_S$, and over the algebra $\mathcal{H}^S$ generated by the algebras $\mathcal{H}(G_p, K_p)$ for $p \notin S$. These three actions commute, since they live at different places, and $\mathcal{H}^S$ is commutative by Lemma 4.1.3.

First, $V^{K^S}$ is irreducible under these three actions together. The proof is the proof of Lemma 4.1.4, with the projection $e_{K^S}$ in place of $e_K$.

Next, choose a compact open subgroup $K_S'$ of $G_S$ and an irreducible representation $\tau$ of $K_\infty$ with $V_0 = V^{K_S' \times K^S}[\tau] \ne 0$. This space is finite-dimensional by admissibility, and $\mathcal{H}^S$ preserves it, since $\mathcal{H}^S$ commutes with $K_S'$ and $K_\infty$. So the commuting operators of $\mathcal{H}^S$ have a common eigenvector $v_0 \in V_0$, with a character $\lambda = (\lambda_p)_{p \notin S}$. Let $V_\lambda$ be the subspace of $V^{K^S}$ where each $f \in \mathcal{H}(G_p, K_p)$, $p \notin S$, acts by $\lambda_p(f)$. It contains $v_0$, and it is stable under $(\mathfrak{g}, K_\infty)$, under $G_S$ and under $\mathcal{H}^S$, since these actions commute with $\mathcal{H}^S$. By irreducibility $V_\lambda = V^{K^S}$. This proves the claim on $\lambda_p$.

If $S \subset S'$, then $V^{K^S} \subset V^{K^{S'}}$, and the character for $S'$ at $p \notin S'$ is the restriction of the character for $S$, since both act on $V^{K^S}$. So $\lambda_p$ does not depend on $S$. The last statement follows from the classification of the characters of $\mathcal{H}(G_p, K_p)$ above. $\square$

*Outline of the proof of Theorem 4.1.6.* Fix $S$ as in Proposition 4.1.7, and fix $K_S'$ and $\tau$. The space $V_0 = V^{K_S' \times K^S}[\tau]$ is a finite-dimensional module over $\mathcal{H}(G_S, K_S') \otimes \mathcal{H}(\mathfrak{g}, K_\infty)[\tau] \otimes \mathcal{H}^S$, and the argument of Lemma 4.1.4 shows that it is irreducible when it is nonzero. A finite-dimensional irreducible module over a tensor product $A \otimes B$ of complex algebras is $M_A \otimes M_B$ with $M_A$ and $M_B$ irreducible, by the theorem of Burnside on the density of the image (Exercise 1). Over the commutative algebra $\mathcal{H}^S$ the factor is the character $\lambda$ of Proposition 4.1.7. Over $\mathcal{H}(G_S, K_S') = \bigotimes_{p \in S}\mathcal{H}(G_p, K_p')$ one applies the same lemma again, place by place. One obtains for each $p \in S$ an irreducible module $M_p$ of $\mathcal{H}(G_p, K_p')$, and an irreducible admissible representation $\pi_p$ of $G_p$ with $\pi_p^{K_p'} \cong M_p$ is unique up to isomorphism, by a converse of Lemma 4.1.4 that is proved in Flath's paper cited below. One does the same at $\infty$, lets $K_S'$ shrink, and compares fixed vectors to show that $\bigotimes'_v \pi_v \to V$ is an isomorphism. The details are in Flath, "Decomposition of representations into tensor products", Proc. Sympos. Pure Math. 33, part 1 (1979), and in [Bum97], Chapter 3. $\square$

**Example 4.1.8 (the representation of $\Delta$).** Let $\Delta \in S_{12}(SL_2(\mathbb{Z}))$ be the discriminant form, and let $\pi_\Delta$ be the representation generated by $\phi_\Delta$; Section 4.3 shows that it is irreducible. The function $\phi_\Delta$ is invariant under $K_f$, so $V^{K^S} \ne 0$ with $S = \emptyset$, and Proposition 4.1.7 gives an unramified component $\pi_p$ at every prime $p$. By the dictionary of Chapter 1 and Proposition 4.2.6 below, the character $\lambda_p$ sends $T_p$ to $p^{-5}\tau(p)$. The component at infinity is the discrete series $D_{12}$, by Section 4.3.

**Remark 4.1.9 (sources).** Jacquet and Langlands prove the decomposition for the representations of $GL_2(\mathbb{A})$ that occur in the space of cusp forms in [JL70], Chapter II. Flath's paper treats all reductive groups over global fields, and [Bum97], Chapter 3, and [GH24] prove the theorem for $GL_2$. Volume 7, Theorem 1.3.4 states the theorem for $GL_n$.
