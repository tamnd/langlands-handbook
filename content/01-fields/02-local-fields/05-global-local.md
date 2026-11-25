---
title: Global and local fields, the different
nodes: []
sources: [Ser79]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Global and local fields, the different

This section compares an extension of number fields with the extensions of its completions. The decomposition group of Section 1.4 becomes the Galois group of a local extension. The section then defines the different and the discriminant, and it computes them for tame extensions. We follow [Neu99], Chapter II, Section 8, and Chapter III, Section 2, and [Ser79], Chapter III.

### Extensions of places

Let $L / F$ be a finite extension of number fields of degree $n$, and let $v$ be a place of $F$. A place $w$ of $L$ *lies over* $v$, written $w \mid v$, if the restriction of $w$ to $F$ is $v$. Then $F_v \subset L_w$, and $L_w = L F_v$ is a finite extension of $F_v$.

**Theorem 2.5.1 (the completions of an extension).** The natural map
$$L \otimes_F F_v \to \prod_{w \mid v} L_w$$
is an isomorphism of $F_v$-algebras. Thus $\sum_{w \mid v} [L_w : F_v] = n$, and for $x \in L$,
$$N_{L/F}(x) = \prod_{w \mid v} N_{L_w / F_v}(x), \qquad \mathrm{Tr}_{L/F}(x) = \sum_{w \mid v} \mathrm{Tr}_{L_w / F_v}(x).$$

Lean: not stated yet

*Proof.* Write $L = F(\alpha)$ and let $g$ be the minimal polynomial of $\alpha$ over $F$. Over $F_v$, $g = g_1 \cdots g_r$ with distinct monic irreducible $g_i$, because $g$ is separable. By the Chinese remainder theorem,
$$L \otimes_F F_v \cong F_v[X] / (g) \cong \prod_{i=1}^r F_v[X] / (g_i).$$
Each factor $E_i = F_v[X]/(g_i)$ is a finite extension of $F_v$. By Theorem 2.2.7, the absolute value of $F_v$ extends uniquely to $E_i$, and $E_i$ is complete. The map $L \to E_i$ is an embedding over $F$ with dense image, because its image contains $F$ and the image of $\alpha$, and $F$ is dense in $F_v$. Thus the restriction to $L$ of the absolute value of $E_i$ is a place $w_i$ over $v$, and $E_i \cong L_{w_i}$. Conversely, let $w$ be a place over $v$. The closure of $L$ in $L_w$ is $F_v(\alpha)$, and the minimal polynomial of $\alpha$ over $F_v$ is one of the $g_i$. This gives an isomorphism $L_w \cong E_i$ over $L$, so $w = w_i$. Different $i$ give different places: an isomorphism $E_i \cong E_j$ over $L$ maps the image of $\alpha$ to the image of $\alpha$, so $g_i = g_j$. The formulas for the norm and the trace hold because the characteristic polynomial of multiplication by $x$ on $L \otimes_F F_v$ is the product of the ones on the factors. $\square$

**Proposition 2.5.2 (finite places).** Let $v = \mathfrak{p}$ be a finite place. The places $w \mid v$ correspond to the primes $\mathfrak{P}$ of $L$ above $\mathfrak{p}$, and
$$e(L_\mathfrak{P} / F_\mathfrak{p}) = e(\mathfrak{P} / \mathfrak{p}), \qquad f(L_\mathfrak{P} / F_\mathfrak{p}) = f(\mathfrak{P} / \mathfrak{p}).$$

Lean: not stated yet

*Proof.* By Theorem 2.2.8, the nonarchimedean places of $L$ are the absolute values $|\cdot|_\mathfrak{P}$, and $|\cdot|_\mathfrak{P}$ restricts to a power of $|\cdot|_\mathfrak{p}$ exactly when $\mathfrak{P} \cap \mathcal{O}_F = \mathfrak{p}$. For $x \in F$, $v_\mathfrak{P}(x) = e(\mathfrak{P}/\mathfrak{p}) v_\mathfrak{p}(x)$, so the two ramification indices agree. The residue field of a completion is the residue field of the field, by Proposition 2.2.1. $\square$

Thus Theorem 2.5.1 gives a second proof of Theorem 1.4.1, since $[L_\mathfrak{P} : F_\mathfrak{p}] = e f$ by Theorem 2.4.1. At an infinite place $v$, the places $w \mid v$ are real or complex. A complex place $w$ over a real place $v$ is called *ramified*, by analogy, and then $[L_w : F_v] = 2$.

### Decomposition groups as local Galois groups

Let $L / F$ be Galois with group $G$. The group $G$ acts on the places of $L$ over $v$ by $|x|_{\sigma w} = |\sigma^{-1} x|_w$. This action is transitive, by Theorem 1.4.4 at the finite places and by the transitivity of $G$ on the embeddings of $L$ in $\mathbb{C}$ at the infinite places. The *decomposition group* of $w$ is $D_w = \{\sigma \in G : \sigma w = w\}$.

**Theorem 2.5.3 (decomposition groups are local Galois groups).** Let $L / F$ be Galois, and $w \mid v$. Then $L_w / F_v$ is Galois, and restriction gives an isomorphism
$$\mathrm{Gal}(L_w / F_v) \xrightarrow{\sim} D_w.$$
If $v = \mathfrak{p}$ is finite and $w = \mathfrak{P}$, this isomorphism maps the inertia group of $L_\mathfrak{P} / F_\mathfrak{p}$ onto $I_\mathfrak{P}$. If $\mathfrak{p}$ is unramified, it maps the Frobenius of the unramified extension $L_\mathfrak{P} / F_\mathfrak{p}$ to $\mathrm{Frob}_\mathfrak{P}$.

Lean: not stated yet

*Proof.* An element $\sigma \in D_w$ is an isometry of $L$ for $|\cdot|_w$, so it extends by continuity to an automorphism of $L_w$ over $F_v$. This gives an injective map $D_w \to \mathrm{Aut}(L_w / F_v)$, since $L$ is dense in $L_w$. Conversely an automorphism $\tau$ of $L_w$ over $F_v$ preserves the absolute value, by Theorem 2.2.7. It maps $L$ to $L$, because $L$ is normal over $F$, and its restriction lies in $D_w$. Thus $D_w \cong \mathrm{Aut}(L_w/F_v)$. The group $D_w$ has order $n / g$, where $g$ is the number of places over $v$, and $[L_w : F_v] = n/g$ by Theorem 2.5.1 and transitivity. So $L_w / F_v$ is Galois. The residue fields of $L_\mathfrak{P}$ and $F_\mathfrak{p}$ are $\kappa(\mathfrak{P})$ and $\kappa(\mathfrak{p})$, and the action on them is the same. This identifies the inertia groups and the Frobenius elements. $\square$

At an infinite place, $D_w$ is trivial if $w$ and $v$ are both real or both complex. If $w$ is complex and $v$ is real, then $D_w$ has order 2, and its nontrivial element is the complex conjugation $c_w$ defined by the embedding of $L$ that gives $w$. For $F = \mathbb{Q}$ and $L$ inside $\mathbb{C}$, it is the usual complex conjugation.

The Galois group of the local extension $L_\mathfrak{P} / F_\mathfrak{p}$ has the inertia subgroup $I$, and the quotient $D/I$ is cyclic, generated by the Frobenius. Thus the decomposition group of a prime is an extension of a cyclic group by the inertia group, and the inertia group is cyclic in the tame case, by the end of Section 2.4. These local facts are the reason for the definitions of Section 1.4.

### The different

Let $A$ be a Dedekind domain with fraction field $K$, let $L / K$ be finite separable, and let $B$ be the integral closure of $A$ in $L$. In this handbook $A$ is $\mathcal{O}_F$ or the ring of integers of a local field.

**Definition 2.5.4 (the different).** The *inverse different* is the fractional ideal
$$\mathfrak{D}_{B/A}^{-1} = \{x \in L : \mathrm{Tr}_{L/K}(x B) \subset A\}$$
of $B$. It contains $B$. The *different* $\mathfrak{D}_{B/A}$ is its inverse, an integral ideal of $B$. The *discriminant* of $B/A$ is the ideal $\mathfrak{d}_{B/A} = N_{L/K}(\mathfrak{D}_{B/A})$ of $A$.

Lean: `differentIdeal`, from Mathlib

For $A = \mathbb{Z}$ and $B = \mathcal{O}_F$, the index of $\mathcal{O}_F$ in the dual lattice $\mathfrak{D}^{-1}$ is $|d_F|$. Indeed the dual lattice has the dual basis of an integral basis, and the matrix of the trace form in this basis has determinant $d_F$. Thus $N(\mathfrak{D}_{F/\mathbb{Q}}) = |d_F|$, and $\mathfrak{d}_{\mathcal{O}_F / \mathbb{Z}} = d_F \mathbb{Z}$. The different is compatible with localization and completion. If $\mathfrak{P}$ lies over $\mathfrak{p}$, then the exponent of $\mathfrak{P}$ in $\mathfrak{D}_{L/F}$ is the exponent of the maximal ideal in the different of $L_\mathfrak{P} / F_\mathfrak{p}$ ([Neu99], Chapter III, Proposition 2.2). The different is multiplicative in towers: $\mathfrak{D}_{M/K} = \mathfrak{D}_{M/L} \mathfrak{D}_{L/K}$.

**Lemma 2.5.5 (Euler's formula).** Let $L = K(\alpha)$, let $g$ be the minimal polynomial of $\alpha$, of degree $n$, and write $g(X) / (X - \alpha) = b_0 + b_1 X + \dots + b_{n-1} X^{n-1}$. Then the dual basis of $1, \alpha, \dots, \alpha^{n-1}$ for the trace form is $b_0 / g'(\alpha), \dots, b_{n-1} / g'(\alpha)$.

Lean: not stated yet

*Proof.* Let $\alpha_1, \dots, \alpha_n$ be the roots of $g$. Lagrange interpolation gives, for $0 \le r < n$,
$$\sum_{i=1}^n \frac{g(X)}{X - \alpha_i} \frac{\alpha_i^r}{g'(\alpha_i)} = X^r,$$
because both sides are polynomials of degree less than $n$ that agree at the $n$ points $\alpha_i$. The left side is $\mathrm{Tr}_{L/K}\big(\frac{g(X)}{X - \alpha} \frac{\alpha^r}{g'(\alpha)}\big)$, with the trace applied to the coefficients. Comparing the coefficients of $X^j$ gives $\mathrm{Tr}(\alpha^r b_j / g'(\alpha)) = \delta_{rj}$. $\square$

**Proposition 2.5.6 (the different of a monogenic ring).** If $B = A[\alpha]$, and $g$ is the minimal polynomial of $\alpha$, then $\mathfrak{D}_{B/A} = g'(\alpha) B$.

Lean: `conductor_mul_differentIdeal`, from Mathlib, in a more general form

*Proof.* The coefficients of $g(X)/(X - \alpha)$ are $b_{n-1} = 1$ and $b_{j-1} = b_j \alpha + a_j$, where $g = \sum a_j X^j$. By induction, $b_j \in \alpha^{n-1-j} + A[\alpha]_{< n-1-j}$, where the second term is a combination of lower powers of $\alpha$. Thus the $b_j$ form a basis of $A[\alpha]$ over $A$. By Lemma 2.5.5, the dual of the basis $1, \alpha, \dots, \alpha^{n-1}$ of $B$ is $b_0 / g'(\alpha), \dots, b_{n-1}/g'(\alpha)$, which is a basis of $g'(\alpha)^{-1} B$. Thus $\mathfrak{D}^{-1} = g'(\alpha)^{-1} B$. $\square$

**Theorem 2.5.7 (the different and ramification).** Let $L / K$ be a finite extension of nonarchimedean local fields, with ramification index $e$, and let $p$ be the residue characteristic. Then $\mathfrak{p}_L^{e-1}$ divides $\mathfrak{D}_{L/K}$, and $\mathfrak{D}_{L/K} = \mathfrak{p}_L^{e-1}$ if and only if $p \nmid e$. In particular $L / K$ is unramified if and only if $\mathfrak{D}_{L/K} = \mathcal{O}_L$.

Lean: `pow_sub_one_dvd_differentIdeal` and `dvd_differentIdeal_iff`, from Mathlib

*Proof.* Let $T$ be the maximal unramified subextension. By Theorem 2.4.2, $\mathcal{O}_T = \mathcal{O}_K[\zeta]$ for a root of unity $\zeta$ of order $m$ prime to $p$. The minimal polynomial $g$ of $\zeta$ divides $X^m - 1$, and $g'(\zeta)$ divides $m \zeta^{m-1}$ in $\mathcal{O}_T$, so it is a unit. Thus $\mathfrak{D}_{T/K} = \mathcal{O}_T$ by Proposition 2.5.6, and $\mathfrak{D}_{L/K} = \mathfrak{D}_{L/T}$. Now $L/T$ is totally ramified, and $\mathcal{O}_L = \mathcal{O}_T[\pi]$ for a root $\pi$ of an Eisenstein polynomial $g = X^e + a_{e-1}X^{e-1} + \dots + a_0$, by Theorem 2.4.4. Then
$$g'(\pi) = e \pi^{e-1} + \sum_{i=1}^{e-1} i a_i \pi^{i-1}.$$
We have $v_L(e \pi^{e-1}) = e\, v_T(e) + e - 1$, and $v_L(i a_i \pi^{i-1}) \ge e + i - 1$ for $1 \le i \le e - 1$, since $v_L(a_i) \ge e$. If $p \nmid e$, then $v_T(e) = 0$, the first term has valuation $e - 1$, and the others have valuation at least $e$. So $v_L(g'(\pi)) = e - 1$. If $p \mid e$, all terms have valuation at least $e$, so $v_L(g'(\pi)) \ge e$. $\square$

**Corollary 2.5.8 (ramified primes and the different).** Let $L / F$ be an extension of number fields. A prime $\mathfrak{P}$ of $L$ is ramified over $F$ if and only if $\mathfrak{P}$ divides $\mathfrak{D}_{L/F}$. A prime $\mathfrak{p}$ of $F$ is ramified in $L$ if and only if $\mathfrak{p}$ divides $\mathfrak{d}_{L/F}$.

Lean: `dvd_differentIdeal_iff`, from Mathlib

*Proof.* The first claim follows from Theorem 2.5.7 and the compatibility of the different with completion. The second follows from the first, because $\mathfrak{d}_{L/F} = N_{L/F}(\mathfrak{D}_{L/F})$ and $N_{L/F}(\mathfrak{P}) = \mathfrak{p}^{f(\mathfrak{P}/\mathfrak{p})}$. $\square$

For $F = \mathbb{Q}$ this is Theorem 1.4.3 again. The different gives more: the exponent of $p$ in $d_L$ is $\sum_{\mathfrak{P} \mid p} f(\mathfrak{P}/p)\, d(\mathfrak{P})$, where $d(\mathfrak{P})$ is the exponent of $\mathfrak{P}$ in the different. It equals $\sum (e_\mathfrak{P} - 1) f_\mathfrak{P}$ when all the ramification over $p$ is tame.

**Example 2.5.9 (the different of $\mathbb{Q}_p(\zeta_p)$).** Let $p$ be odd, $K = \mathbb{Q}_p(\zeta_p)$ and $\pi = 1 - \zeta_p$. The extension is totally and tamely ramified of degree $p - 1$, by Example 2.4.6. Thus $\mathfrak{D}_{K/\mathbb{Q}_p} = (\pi)^{p-2}$, and the discriminant is $p^{p-2}\mathbb{Z}_p$. This agrees with Theorem 1.5.4, which gives $|d_F| = p^{p-2}$ for $F = \mathbb{Q}(\zeta_p)$. For $K = \mathbb{Q}_p(\zeta_{p^k})$ with $k \ge 2$ the extension is wild, and the exponent of the different is $k p^{k-1}(p-1) - p^{k-1}$, which is larger than $e - 1 = p^{k-1}(p-1) - 1$.
