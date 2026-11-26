---
title: The global norm residue map
nodes: []
sources: [CF67, Mil20, Neu99, Ser79]
status: drafted
drafted_by: writer
reviewed_by: []
---
## The global norm residue map

This section builds the global map from the local ones. For a finite abelian extension $L/F$ we multiply the local reciprocity maps of all the places of $F$. The result is a continuous surjective homomorphism $J_F \to \mathrm{Gal}(L/F)$. The main theorem of global class field theory says that it is trivial on $F^\times$. For cyclotomic extensions this is a direct computation, which we do here. It has the same form as the product formula $\prod_v |x|_v = 1$, and with the Hilbert symbol it gives the law of quadratic reciprocity.

### The local maps

Let $v$ be a place of $F$. If $v$ is finite, let $r_v = r_{F_v} : F_v^\times \to \mathrm{Gal}(F_v^{ab}/F_v)$ be the local reciprocity map of Theorem 2.1.3. It sends a uniformizer to an element that acts on the maximal unramified extension as the geometric Frobenius. If $v$ is real, let $r_v : \mathbb{R}^\times \to \mathrm{Gal}(\mathbb{C}/\mathbb{R})$ send $x$ to $1$ if $x > 0$ and to complex conjugation if $x < 0$. Its kernel is $\mathbb{R}_{>0} = N_{\mathbb{C}/\mathbb{R}}(\mathbb{C}^\times)$, so it has the properties of Theorem 2.1.2. If $v$ is complex, $r_v$ is trivial. At the infinite places the geometric and the arithmetic normalizations agree, because $\mathrm{Gal}(\mathbb{C}/\mathbb{R})$ has order 2.

Let $L/F$ be a finite abelian extension with group $G$. For a place $v$ and a place $w \mid v$ of $L$, the decomposition group $D_w \subset G$ is the image of $\mathrm{Gal}(L_w/F_v)$. Since $G$ is abelian and the places over $v$ are conjugate, $D_w$ does not depend on $w$, and neither does the composite map
$$r_{L/F, v} : F_v^\times \xrightarrow{r_v} \mathrm{Gal}(L_w / F_v) = D_w \subset G.$$
Indeed, for $\sigma \in G$ the isomorphism $\sigma : L_w \to L_{\sigma w}$ transports the local map at $w$ to the local map at $\sigma w$, by the naturality of $r_v$ under isomorphisms of local fields, and conjugation by $\sigma$ is trivial on $G$. The kernel of $r_{L/F,v}$ is the local norm group $N_{L_w/F_v}(L_w^\times)$. If $v$ is finite and unramified in $L$, then $r_{L/F,v}$ is trivial on $\mathcal{O}_v^\times$ by Proposition 2.1.8, and it sends each uniformizer to $\mathrm{Frob}_v^{-1}$, by Theorem 2.1.3, part 1.

**Definition 7.2.1 (the global norm residue map).** For $x \in J_F$, let
$$\mathrm{art}_{L/F}(x) = \prod_v r_{L/F, v}(x_v) \in G.$$

The product is finite. For almost all $v$, the place $v$ is finite and unramified in $L$ and $x_v \in \mathcal{O}_v^\times$, so the factor is $1$.

**Proposition 7.2.2 (first properties).** Let $L/F$ be finite abelian with group $G$.
1. The map $\mathrm{art}_{L/F} : J_F \to G$ is a continuous homomorphism. Its restriction to $F_v^\times$ is $r_{L/F,v}$.
2. For a finite place $v$ unramified in $L$ and a uniformizer $\varpi_v$ of $F_v$, $\mathrm{art}_{L/F}(\varpi_v) = \mathrm{Frob}_v^{-1}$.
3. If $L' \subset L$ is a subextension, then $\mathrm{art}_{L/F}(x)|_{L'} = \mathrm{art}_{L'/F}(x)$. Thus the maps $\mathrm{art}_{L/F}$ define a continuous homomorphism $\mathrm{art}_F : J_F \to \mathrm{Gal}(F^{ab}/F)$.
4. Let $E/F$ be a finite extension. Then $\mathrm{art}_{LE/E}(y)|_L = \mathrm{art}_{L/F}(N_{E/F}(y))$ for $y \in J_E$.
5. The map $\mathrm{art}_{L/F}$ is trivial on $N_{L/F}(J_L)$.

Lean: `GlobalClassFieldTheory.Reciprocity.globalArtinMonoidHom_continuous`

*Proof.* Part 1. Let $S$ be the set of places that are infinite or ramified in $L$. On the open subgroup $\prod_{v \in S} N_{L_w/F_v}(L_w^\times) \times \prod_{v \notin S} \mathcal{O}_v^\times$ the map is trivial. The local norm groups are open by Proposition 2.1.6, and at the real places the norm group is $\mathbb{R}_{>0}$ or $\mathbb{R}^\times$. So the kernel is open and the map is continuous. It is a homomorphism because $G$ is abelian. Part 2 was shown above. Part 3 holds because each local map is compatible with restriction, by Theorem 2.1.3. Part 4 is the local statement of Corollary 2.4.3 and Theorem 2.4.2 at each place: for $u \mid v$ a place of $E$, $r_{E_u}(y_u)$ restricted to $F_v^{ab}$ is $r_{F_v}(N_{E_u/F_v}(y_u))$. Multiply over all $u \mid v$ and then over all $v$. At the real places this is the fact that the norm from $\mathbb{C}$ is positive. Part 5 is part 4 with $E = L$, since $\mathrm{art}_{L/L}$ is trivial. $\square$

The Lean theorem is part 1 for the map `GlobalClassFieldTheory.Reciprocity.globalArtinMonoidHom` of the port, which is defined as the product of the local maps (see the remark on the Lean proof in Section 7.3). The theorems `GlobalClassFieldTheory.Reciprocity.globalArtinMonoidHom_finitePlaceIdele` and `GlobalClassFieldTheory.Reciprocity.globalArtinMonoidHom_norm_restriction` are the restriction to $F_v^\times$ at the finite places and part 4.

**Lemma 7.2.3 (extensions with almost all primes split).** Let $E/F$ be a finite Galois extension in which all but finitely many primes of $F$ split completely. Then $E = F$.

Lean: `GlobalClassFieldTheory.Cohomology.finrank_eq_one_of_finite_nonSplittingPlaces`

*Proof.* Let $n = [E : F]$. For real $s > 1$, the Euler product of the Dedekind zeta function gives $\log \zeta_F(s) = \sum_\mathfrak{p} N\mathfrak{p}^{-s} + g_F(s)$, where $g_F$ is bounded as $s \to 1^+$, because $\sum_\mathfrak{p} \sum_{k \ge 2} N\mathfrak{p}^{-ks}/k$ converges for $s > 1/2$. The same holds for $E$. In the sum for $E$ only the primes $\mathfrak{P}$ of degree 1 over $F$ matter, since $\sum N\mathfrak{P}^{-s}$ over the other primes is bounded by a sum of the form $\sum_p n p^{-2s}$. A prime $\mathfrak{p}$ that splits completely has $n$ primes of degree 1 above it, of norm $N\mathfrak{p}$, and a prime that does not split completely and is unramified has none. So
$$\log \zeta_E(s) = n \sum_{\mathfrak{p} \text{ split}} N\mathfrak{p}^{-s} + O(1) = n \log \zeta_F(s) + O(1),$$
because almost all primes split. By Corollary 5.4.8, both $\zeta_E$ and $\zeta_F$ have a simple pole at $s = 1$, so $\log \zeta_E(s)$ and $\log \zeta_F(s)$ are both $\log(1/(s-1)) + O(1)$. Hence $n = 1$. $\square$

The Lean theorem is a little more general: $E/F$ is any finite extension, and the proof passes to the Galois closure. The port proves the lemma without $L$-functions. It uses the fact that a cyclic extension of prime degree has infinitely many primes that do not split, which comes from the first inequality of Section 7.3, as in [Neu99], Chapter VI.

**Proposition 7.2.4 (surjectivity).** The map $\mathrm{art}_{L/F} : J_F \to G$ is surjective. For a finite place $v$, the image of $\mathcal{O}_v^\times$ is the inertia group $I_v$.

Lean: `GlobalClassFieldTheory.Reciprocity.globalArtinMonoidHom_surjective`

*Proof.* Let $H$ be the image, and $E = L^H$. For each finite $v$ unramified in $L$, $\mathrm{Frob}_v^{-1} \in H$ by Proposition 7.2.2, part 2. So $\mathrm{Frob}_v$ is trivial on $E$, and $v$ splits completely in $E$. By Lemma 7.2.3, $E = F$ and $H = G$. The second claim is Proposition 2.1.8. $\square$

### The reciprocity law

**Theorem 7.2.5 (Artin's reciprocity law).** Let $L/F$ be a finite abelian extension. For $a \in F^\times$,
$$\prod_v r_{L/F, v}(a) = 1.$$
Thus $\mathrm{art}_{L/F}$ factors through $C_F$, and $\mathrm{art}_F$ induces a continuous surjective homomorphism $C_F \to \mathrm{Gal}(F^{ab}/F)$.

Lean: `GlobalClassFieldTheory.Reciprocity.chosenLocalArtin_product_principalIdele`

The formula is a multiplicative analogue of the product formula $\prod_v |a|_v = 1$ (Volume 1, Theorem 3.3.4). The analogy is exact for the maximal unramified quotients. Let $v$ be finite. The image of $r_v(a)$ in $\mathrm{Gal}(F_v^{ur}/F_v) \cong \hat{\mathbb{Z}}$ is $-v(a)$, and $|a|_v = N\mathfrak{p}_v^{-v(a)}$. So the absolute value is the unramified part of the local reciprocity map, read through $\Phi \mapsto N\mathfrak{p}_v$. The product formula says that the "unramified parts" multiply to 1, and the reciprocity law says the same for the full local symbols. Section 7.8 makes this precise. There the idelic absolute value $|\cdot| : C_F \to \mathbb{R}_{>0}$ becomes the norm map of the global Weil group.

Section 7.3 proves the theorem. The proof reduces it to cyclotomic extensions, where it is a computation.

**Proposition 7.2.6 (the cyclotomic case).** Let $m \ge 1$ and let $L \subset F(\zeta_m)$, where $\zeta_m$ is a primitive $m$-th root of unity. Then Theorem 7.2.5 holds for $L/F$.

Lean: not stated yet

*Proof.* First let $F = \mathbb{Q}$ and $L = \mathbb{Q}(\zeta_m)$, and let $\sigma_c \in G$ be the automorphism $\zeta \mapsto \zeta^c$ for $c \in (\mathbb{Z}/m\mathbb{Z})^\times$ (Volume 1, Theorem 1.5.3). We compute the local maps with Example 3.5.6. Let $x = u p^k \in \mathbb{Q}_p^\times$ with $u \in \mathbb{Z}_p^\times$, and write $m = p^n m'$ with $p \nmid m'$. Then $r_p(x)$ acts on the roots of unity of order $p^n$ as $\zeta \mapsto \zeta^u$, and on the roots of unity of order $m'$ as $\zeta \mapsto \zeta^{p^{-k}}$. At the real place, $r_\infty(x) = \sigma_{\mathrm{sgn}(x)}$, since complex conjugation is $\sigma_{-1}$.

Let $a \in \mathbb{Q}^\times$, and write $a = \mathrm{sgn}(a) \prod_p p^{k_p}$. Fix a prime $\ell$ with $\ell^n \| m$, and let $\zeta$ be a root of unity of order $\ell^n$. The factor at $p = \ell$ sends $\zeta$ to $\zeta^{u_\ell}$, with $u_\ell = a \ell^{-k_\ell}$. The factor at a prime $p \ne \ell$ sends $\zeta$ to $\zeta^{p^{-k_p}}$. The factor at $\infty$ sends it to $\zeta^{\mathrm{sgn}(a)}$. So the product sends $\zeta$ to $\zeta^c$ with
$$c = a \ell^{-k_\ell} \cdot \prod_{p \ne \ell} p^{-k_p} \cdot \mathrm{sgn}(a) = a \cdot \mathrm{sgn}(a) \prod_p p^{-k_p} = 1.$$
This holds for every $\ell \mid m$, so the product is trivial on $\mathbb{Q}(\zeta_m)$. For $L \subset \mathbb{Q}(\zeta_m)$ use Proposition 7.2.2, part 3.

Now let $F$ be arbitrary and $a \in F^\times$. Restriction to $\mathbb{Q}(\zeta_m)$ is an injective map $\mathrm{Gal}(F(\zeta_m)/F) \to \mathrm{Gal}(\mathbb{Q}(\zeta_m)/\mathbb{Q})$. By Proposition 7.2.2, part 4, with $E = F$ over $\mathbb{Q}$,
$$\mathrm{art}_{F(\zeta_m)/F}(a)|_{\mathbb{Q}(\zeta_m)} = \mathrm{art}_{\mathbb{Q}(\zeta_m)/\mathbb{Q}}(N_{F/\mathbb{Q}}(a)) = 1,$$
by the first case, since $N_{F/\mathbb{Q}}(a) \in \mathbb{Q}^\times$. So $\mathrm{art}_{F(\zeta_m)/F}(a) = 1$, and the claim for $L \subset F(\zeta_m)$ follows by restriction. $\square$

The computation also identifies the global map of $\mathbb{Q}$. With $C_\mathbb{Q} \cong \mathbb{R}_{>0} \times \hat{\mathbb{Z}}^\times$ (Volume 1, Example 3.4.8), the map $\mathrm{art}_\mathbb{Q}$ sends the class of $(t, u)$ to the automorphism $\zeta \mapsto \zeta^u$ of $\mathbb{Q}(\mu_\infty)$. Indeed, the idele $u \in \hat{\mathbb{Z}}^\times$ has the factor $\zeta \mapsto \zeta^{u_\ell}$ on $\mu_{\ell^\infty}$ at $\ell$, and the other factors are trivial on $\mu_{\ell^\infty}$. Section 7.5 uses this.

### The Hilbert symbol and its product formula

Let $n \ge 1$, and assume that $F$ contains the group $\mu_n$ of $n$-th roots of unity. For a place $v$ and $a, b \in F_v^\times$, choose $\beta \in \bar F_v$ with $\beta^n = b$. The extension $F_v(\beta)/F_v$ is abelian, by Kummer theory, and we define the *Hilbert symbol*
$$(a, b)_v = \frac{r_v(a)(\beta)}{\beta} \in \mu_n.$$
It does not depend on the choice of $\beta$, because another choice is $\zeta \beta$ with $\zeta \in \mu_n \subset F_v$. It is bimultiplicative, and $(a, b)_v = 1$ if and only if $a$ is a norm from $F_v(\beta)$, by Theorem 2.1.3. If $v$ is finite, $v \nmid n$, and $a$ and $b$ are units, then $F_v(\beta)/F_v$ is unramified and $(a, b)_v = 1$. In the arithmetic normalization one gets the inverse symbol. This sign is invisible for $n = 2$, which is the case of Example 2.5.5.

**Corollary 7.2.7 (Hilbert's product formula).** Let $\mu_n \subset F$ and $a, b \in F^\times$. Then $(a, b)_v = 1$ for almost all $v$, and
$$\prod_v (a, b)_v = 1.$$

Lean: not stated yet

*Proof.* The first claim was shown above. Let $\beta^n = b$ with $\beta \in \bar F$, and $L = F(\beta)$, which is abelian over $F$. For each $v$ fix an embedding of $L$ in $\bar F_v$. Then $r_{L/F, v}(a)$ is the restriction of $r_v(a)$ to $L$, so $r_{L/F,v}(a)(\beta) = (a, b)_v \beta$. The elements $r_{L/F,v}(a)$ commute and fix $\mu_n$. So $\big(\prod_v r_{L/F,v}(a)\big)(\beta) = \big(\prod_v (a,b)_v\big) \beta$. By Theorem 7.2.5 the left side is $\beta$. $\square$

**Example 7.2.8 (quadratic reciprocity).** Let $F = \mathbb{Q}$, $n = 2$, and let $p \ne q$ be odd primes. We compute $(p, q)_v$. At $v = \infty$ it is $1$, since $p > 0$ is a norm from $\mathbb{C}$. At a prime $\ell \nmid 2pq$ it is 1, since $p$ and $q$ are units. At $v = p$ the field $\mathbb{Q}_p(\sqrt q)$ is unramified or trivial, so $(p, q)_p = 1$ if and only if $q$ is a square modulo $p$, that is, $(p, q)_p = \left(\frac{q}{p}\right)$. At $v = q$ the field $\mathbb{Q}_q(\sqrt q)$ is ramified, and its norm character on the units is the Legendre symbol modulo $q$ by Example 2.5.5 and Example 3.5.6. So $(p, q)_q = \left(\frac{p}{q}\right)$. At $v = 2$ both are units, and $(u, u')_2 = (-1)^{(u-1)(u'-1)/4}$ for odd $u, u'$, see Exercise 9 of Chapter 2 and [Ser79], Chapter XIV. Corollary 7.2.7 gives
$$\left(\frac{p}{q}\right) \left(\frac{q}{p}\right) = (-1)^{\frac{p-1}{2} \frac{q-1}{2}}.$$
The supplementary laws come from $(-1, p)_v$ and $(2, p)_v$ in the same way. The law of quadratic reciprocity is thus a product formula, and Theorem 1.5.8 of Volume 1 is its classical proof with Gauss sums. In this form it extends to the $n$-th power reciprocity laws of Hilbert, Furtwängler and Artin.
