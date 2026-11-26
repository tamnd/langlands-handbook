---
title: Tori
nodes: [LG5YHMSJZM, LG4S7A4G1F]
sources: [Tat79, Mil20]
status: checked
drafted_by: writer
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## Tori

The group $GL_1$ is the simplest torus. For a general torus the local Langlands correspondence needs the dual group and the action of $W_K$ on it. This section shows the shape of the general statement in two cases, where it follows from Theorem 4.2.3.

Let $K^s$ be the separable closure of $K$ in $\bar K$. A *torus* over $K$ is a linear algebraic group $T$ over $K$ such that $T_{K^s} \cong \mathbb{G}_m^r$ for some $r$. Its *character group* is $X^*(T) = \mathrm{Hom}_{K^s}(T, \mathbb{G}_m)$, and its *cocharacter group* is $X_*(T) = \mathrm{Hom}_{K^s}(\mathbb{G}_m, T)$. Both are free abelian groups of rank $r$, and $G_K$ acts on them through a finite quotient. The composite of a cocharacter and a character is a power map of $\mathbb{G}_m$, and this gives a perfect pairing $\langle \cdot, \cdot \rangle : X^*(T) \times X_*(T) \to \mathbb{Z}$. The torus is *split* if $G_K$ acts trivially, and then $T \cong \mathbb{G}_m^r$ over $K$.

**Definition 4.5.1 (dual torus and parameters).** The *dual torus* of $T$ is $\hat T = X^*(T) \otimes \mathbb{C}^\times$, with the action of $W_K$ through $W_K \to G_K$ on the first factor. A *Langlands parameter* for $T$ is a continuous 1-cocycle $W_K \to \hat T$, and two parameters are equivalent if they differ by a coboundary. The set of classes is $H^1(W_K, \hat T)$.

The dual torus is a complex torus whose cocharacter group is $X^*(T)$. It can also be written $\hat T = \mathrm{Hom}(X_*(T), \mathbb{C}^\times)$, by the pairing. In the general theory the parameters take values in the $L$-group $\hat T \rtimes W_K$, and a 1-cocycle is the same as a section of the projection to $W_K$ up to conjugation by $\hat T$. For $T = GL_1$ the dual torus is $\mathbb{C}^\times$ with the trivial action, and $H^1(W_K, \mathbb{C}^\times)$ is the group of characters of $W_K$.

### Split tori

**Theorem 4.5.2 (split tori).** Let $T$ be a split torus over $K$. For a character $\chi$ of $T(K)$, define $\phi_\chi : W_K \to \hat T = \mathrm{Hom}(X_*(T), \mathbb{C}^\times)$ by
$$\phi_\chi(w)(\mu) = \chi\big(\mu(\mathrm{rec}_K^{-1}(\bar w))\big), \qquad \mu \in X_*(T),$$
where $\bar w$ is the image of $w$ in $W_K^{ab}$. Then $\chi \mapsto \phi_\chi$ is a bijection from the characters of $T(K)$ to $\mathrm{Hom}(W_K, \hat T) = H^1(W_K, \hat T)$. It does not depend on a choice of isomorphism $T \cong \mathbb{G}_m^r$.

Node: LG5YHMSJZM · Lean: `Langlands.LocalLanglandsTorusSplit`

*Proof.* As $T$ is split, the map $X_*(T) \otimes K^\times \to T(K)$, $\mu \otimes x \mapsto \mu(x)$, is an isomorphism of topological groups, where the left side is $(K^\times)^r$ after a choice of basis. Thus
$$\mathrm{Hom}(T(K), \mathbb{C}^\times) = \mathrm{Hom}(X_*(T), \mathrm{Hom}(K^\times, \mathbb{C}^\times)) \cong \mathrm{Hom}(X_*(T), \mathrm{Hom}(W_K, \mathbb{C}^\times)) = \mathrm{Hom}(W_K, \hat T),$$
where the middle isomorphism is Theorem 4.2.3, and all groups of homomorphisms are groups of continuous homomorphisms. The composite is $\chi \mapsto \phi_\chi$. The action of $W_K$ on $\hat T$ is trivial, so a 1-cocycle is a homomorphism and every coboundary is trivial. Each step is defined without a basis of $X_*(T)$. $\square$

### Induced tori

Let $L$ be a finite separable extension of $K$ in $K^s$ of degree $n$. The torus $T = \mathrm{Res}_{L/K} \mathbb{G}_m$ is the Weil restriction: $T(A) = (A \otimes_K L)^\times$ for each $K$-algebra $A$. Thus $T(K) = L^\times$. Over $K^s$,
$$K^s \otimes_K L \cong \prod_{\tau} K^s, \qquad \tau \in \mathrm{Hom}_K(L, K^s),$$
so $T_{K^s} \cong \mathbb{G}_m^n$. The characters are the projections $e_\tau$, and $\sigma \in G_K$ acts by $\sigma(e_\tau) = e_{\sigma\tau}$. The map $\sigma \mapsto \sigma|_L$ identifies $G_K / G_L$ with $\mathrm{Hom}_K(L, K^s)$. Thus $X^*(T) = \mathbb{Z}[G_K/G_L]$ is a permutation module, and $\hat T$ is the group of functions $a : G_K / G_L \to \mathbb{C}^\times$, with $(\sigma a)(\tau) = a(\sigma^{-1}\tau)$.

The group $W_K$ maps onto $G_K / G_L$, because $W_K$ is dense in $G_K$ and $G_L$ is open, and the kernel is $W_L = W_K \cap G_L$. Let $\mathrm{Ind}_{W_L}^{W_K} \mathbb{C}^\times$ be the group of functions $F : W_K \to \mathbb{C}^\times$ with $F(hx) = F(x)$ for $h \in W_L$, with the action $(wF)(x) = F(xw)$. The map $a \mapsto F_a$, $F_a(x) = a(x^{-1} G_L)$, is an isomorphism of $W_K$-modules $\hat T \cong \mathrm{Ind}_{W_L}^{W_K} \mathbb{C}^\times$. Indeed $F_{\sigma a}(x) = a(\sigma^{-1} x^{-1} G_L) = F_a(x\sigma)$.

**Lemma 4.5.3 (Shapiro's lemma in degree 1).** Let $A$ be an abelian topological group with the trivial action of $W_L$, written additively. The map $z \mapsto S(z)$, $S(z)(h) = z(h)(1)$, induces an isomorphism
$$H^1(W_K, \mathrm{Ind}_{W_L}^{W_K} A) \cong H^1(W_L, A) = \mathrm{Hom}(W_L, A).$$

Lean: not stated yet

*Proof.* Let $z$ be a continuous 1-cocycle, so $z(ww') = z(w) + w z(w')$. For $h, h' \in W_L$,
$$z(hh')(1) = z(h)(1) + z(h')(h) = z(h)(1) + z(h')(1),$$
because $z(h')$ is invariant under left translation by $W_L$. So $S(z)$ is a homomorphism. If $z(w) = wF - F$, then $S(z)(h) = F(h) - F(1) = 0$. Thus $S$ is defined on $H^1$.

Injectivity. Assume $S(z) = 0$ and put $F(x) = z(x)(1)$. Then $F(hx) = z(h)(1) + z(x)(h) = F(x)$, so $F$ lies in the induced module. The cocycle identity gives $F(xw) = z(x)(1) + z(w)(x)$, that is, $z(w) = wF - F$. So $z$ is a coboundary.

Surjectivity. Let $\chi : W_L \to A$ be a homomorphism. Choose representatives $s_1 = 1, s_2, \dots, s_n$ of $W_L \backslash W_K$, and write each $x \in W_K$ as $x = h(x) s_{i(x)}$ with $h(x) \in W_L$. Put $c(x) = \chi(h(x))$, so $c(hx) = \chi(h) + c(x)$ for $h \in W_L$. Let $z(w)(x) = c(xw) - c(x)$. Then $z(w)$ lies in the induced module, and
$$z(ww')(x) = \big(c(xw) - c(x)\big) + \big(c(xww') - c(xw)\big) = z(w)(x) + (w z(w'))(x).$$
So $z$ is a cocycle, and $S(z)(h) = c(h) - c(1) = \chi(h)$. The cosets $W_L s_i$ are open, and on $W_L s_i$ the function $c$ is $x \mapsto \chi(x s_i^{-1})$. So $c$ and $z$ are continuous. $\square$

**Theorem 4.5.4 (induced tori).** Let $T = \mathrm{Res}_{L/K} \mathbb{G}_m$. There is a bijection between the characters of $T(K) = L^\times$ and $H^1(W_K, \hat T)$. It is the composite
$$H^1(W_K, \hat T) \cong H^1(W_K, \mathrm{Ind}_{W_L}^{W_K} \mathbb{C}^\times) \cong \mathrm{Hom}(W_L, \mathbb{C}^\times) \cong \mathrm{Hom}(L^\times, \mathbb{C}^\times),$$
of the isomorphism $a \mapsto F_a$, Lemma 4.5.3, and Theorem 4.2.3 for $L$.

Node: LG4S7A4G1F · Lean: `Langlands.LocalLanglandsTorusInduced`

*Proof.* The first map is induced by the isomorphism of $W_K$-modules $a \mapsto F_a$, so it is a bijection on cocycles and on coboundaries. The second map is Lemma 4.5.3. For the third map, Theorem 4.2.3 for $L$ gives an isomorphism of topological groups $\mathrm{rec}_L : L^\times \to W_L^{ab}$, and a continuous character of $W_L$ factors through $W_L^{ab}$ because $\mathbb{C}^\times$ is commutative and Hausdorff. Thus $\psi \mapsto \psi \circ \mathrm{rec}_L$ is a bijection from $\mathrm{Hom}(W_L, \mathbb{C}^\times)$ to $\mathrm{Hom}(L^\times, \mathbb{C}^\times)$.

One point needs care. In Lemma 4.5.3 the group $W_L$ is the subgroup $W_K \cap G_L$ of $W_K$ with the subspace topology. In Theorem 4.2.3 for $L$ the group $W_L$ has its own topology, in which the inertia subgroup $I_L$ is open. The two topologies are equal. The inclusion $W_L \to W_K$ is continuous and injective. Its restriction to $I_L$ is a homeomorphism onto its image, because $I_L$ is compact and $W_K$ is Hausdorff. An element of $W_L$ has degree $0$ over $L$ if and only if it has degree $0$ over $K$, because the degree over $K$ is $f$ times the degree over $L$, where $f$ is the residue degree of $L/K$. Thus the image of $I_L$ is $I_K \cap W_L$, which is open in $W_K$. A homomorphism of topological groups that is a homeomorphism near the identity onto an open subset is a homeomorphism onto its image. $\square$

*Remark.* The Lean statement fixes the bijection in the same way as Theorem 4.5.2. A class $c$ corresponds to $\chi$ if the homomorphism $S(c)$ on $W_L$ takes the value $\chi(x)$ at each $w \in W_L$ whose image in $W_L^{ab}$ is $\mathrm{rec}_L(x)$. As Lemma 4.5.3 is injective, the relation determines $c$. The proof in Lean is the argument above, and the equality of the two topologies on $W_L$ is `Langlands.WeilGroup.weilEquiv`.

The content of the theorem is in its compatibility with maps of tori. The norm $N : T \to \mathbb{G}_m$ is a map of tori over $K$, and on $K$-points it is $N_{L/K} : L^\times \to K^\times$. On characters it is $1 \mapsto \sum_\tau e_\tau$. On dual tori it gives the map $\mathbb{C}^\times \to \hat T$ that sends $c$ to the constant function $c$.

**Proposition 4.5.5 (the norm).** Let $\phi$ be a character of $W_K$, and let $z$ be its image under $H^1(W_K, \mathbb{C}^\times) \to H^1(W_K, \hat T)$. The character of $L^\times$ attached to $z$ by Theorem 4.5.4 is $\chi_\phi \circ N_{L/K}$.

Lean: not stated yet

*Proof.* The cocycle $z$ sends $w$ to the constant function $\phi(w)$, and $F_a$ is constant when $a$ is constant. Thus $S(z)(h) = \phi(h)$ for $h \in W_L$, and $S(z) = \phi|_{W_L}$. By Theorem 4.2.3, part 5, the character of $L^\times$ attached to $\phi|_{W_L}$ is $\chi_\phi \circ N_{L/K}$. $\square$

So the correspondence for tori is compatible with the norm map, and on the Galois side the norm is the restriction to $W_L$. This is functoriality for the map of dual groups $\mathbb{C}^\times \to \hat T$, in the simplest case.

**Theorem 4.5.6 (Langlands).** For each torus $T$ over $K$ there is a bijection between the characters of $T(K)$ and $H^1(W_K, \hat T)$. The bijections for all tori are functorial for maps of tori over $K$. They are given by Theorem 4.2.3 for $T = \mathbb{G}_m$, and they are compatible with Weil restriction.

Lean: not stated yet

Langlands proved this theorem in 1968. The handbook does not give the proof. The split tori of Theorem 4.5.2 and the induced tori of Theorem 4.5.4 are its first cases, and every torus splits over a finite Galois extension of $K$.
