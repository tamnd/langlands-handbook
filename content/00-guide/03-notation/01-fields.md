---
title: Fields, Frobenius and Weil-Deligne representations
nodes: [LGBPNG162F, LGQVB4Z4KN]
sources: [Tat79, Ser79]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Fields, Frobenius and Weil-Deligne representations

### Local fields

The letter $K$ denotes a nonarchimedean local field. Its ring of integers is $\mathcal{O}_K$, its maximal ideal is $\mathfrak{p}_K$, a uniformizer is $\varpi$ or $\varpi_K$, and its residue field is $k$, with $q$ elements and characteristic $p$. The valuation $v_K : K^\times \to \mathbb{Z}$ has $v_K(\varpi) = 1$. The absolute value is normalized by $|x|_K = q^{-v_K(x)}$. With this normalization, $d(ax) = |a|_K \, dx$ for each Haar measure $dx$ on $K$.

An algebraic closure $\bar K$ is fixed, with $G_K = \mathrm{Gal}(\bar K / K)$, the inertia group $I_K$, and the Weil group $W_K$.

**Definition 3.1.1 (Weil group).** The *Weil group* $W_K$ is the subgroup of $G_K$ of the elements that act on the residue field $\bar k$ of $\bar K$ as an integral power of the Frobenius $x \mapsto x^q$. Its topology is the coarsest topology for which the inclusion into $G_K$ is continuous and the residue map $W_K \to \mathrm{Gal}(\bar k / k)$ is locally constant. Thus $I_K$ is open in $W_K$.

Node: LGBPNG162F · Lean: `Langlands.WeilGroup`

The *arithmetic Frobenius* of $k$ is $\mathrm{Frob}_k : x \mapsto x^q$. For $w \in W_K$, the *degree* $d(w) \in \mathbb{Z}$ is the integer with $w|_{\bar k} = \mathrm{Frob}_k^{d(w)}$.

**Definition 3.1.2 (geometric Frobenius).** An element $\Phi \in W_K$ is a *geometric Frobenius* if it acts on $\bar k$ as $x \mapsto x^{1/q}$, that is, if $d(\Phi) = -1$.

Node: LGQVB4Z4KN · Lean: `Langlands.WeilGroup.IsGeometricFrobenius`

The handbook writes $\Phi$ for a geometric Frobenius and $\mathrm{Frob}$ for an arithmetic one. A geometric Frobenius is unique up to multiplication by an element of $I_K$.

The reciprocity map $\mathrm{rec}_K : K^\times \to W_K^{ab}$ of Chapter 2 sends each uniformizer to the class of a geometric Frobenius. The *norm* of $w \in W_K$ is $\|w\| = q^{d(w)}$.

**Remark 3.1.3 (the norm and the absolute value).** For $x \in K^\times$, $\|\mathrm{rec}_K(x)\| = |x|_K$. Indeed both sides are homomorphisms of $K^\times$ that are trivial on $\mathcal{O}_K^\times$, because $\mathrm{rec}_K(\mathcal{O}_K^\times)$ is the image of $I_K$, and both sides send $\varpi$ to $q^{-1}$. In the arithmetic normalization one gets $|x|_K^{-1}$ instead. This is one of the reasons for the geometric normalization: the norm of the Weil group is the absolute value, without an inverse.

Let $\ell$ be a prime different from $p$, and let $\chi_\ell : G_K \to \mathbb{Z}_\ell^\times$ be the cyclotomic character, so that $\sigma(\zeta) = \zeta^{\chi_\ell(\sigma)}$ for each root of unity $\zeta$ of $\ell$-power order. The extension of $K$ by these roots of unity is unramified, and a geometric Frobenius acts on them by $\zeta \mapsto \zeta^{1/q}$. Thus $\chi_\ell(w) = \|w\|$ for $w \in W_K$, and $\chi_\ell \circ \mathrm{rec}_K = |\cdot|_K$.

### Weil-Deligne representations

**Definition 3.1.4 (Weil-Deligne representation).** A *Weil-Deligne representation* of $W_K$ over $\mathbb{C}$ is a triple $(V, r, N)$, where $V$ is a complex vector space of finite dimension, $r : W_K \to GL(V)$ is a homomorphism that is trivial on an open subgroup of $W_K$, and $N \in \mathrm{End}(V)$ is a nilpotent endomorphism with
$$r(w) \, N \, r(w)^{-1} = \|w\| \, N \quad \text{for all } w \in W_K.$$
It is *Frobenius-semisimple* if $r(\Phi)$ is semisimple for a geometric Frobenius $\Phi$.

Lean: not stated yet, planned for milestone S3

For a geometric Frobenius the relation reads $\Phi N \Phi^{-1} = q^{-1} N$, and for an arithmetic Frobenius it reads $\mathrm{Frob} \, N \, \mathrm{Frob}^{-1} = q N$. The relation is not a convention. Grothendieck's monodromy theorem attaches a Weil-Deligne representation to each continuous representation $\rho : G_K \to GL_n(\bar{\mathbb{Q}}_\ell)$ with $\ell \ne p$. On an open subgroup of $I_K$ one has $\rho(\sigma) = \exp(t_\ell(\sigma) N)$, where $t_\ell : I_K \to \mathbb{Z}_\ell$ comes from the tame quotient. Since $t_\ell(w \sigma w^{-1}) = \chi_\ell(w) t_\ell(\sigma)$, the endomorphism $N$ satisfies $\rho(w) N \rho(w)^{-1} = \chi_\ell(w) N$. The last subsection showed that $\chi_\ell(w) = \|w\|$.

**Example 3.1.5 (the Tate curve).** Let $E$ be an elliptic curve over $K$ with split multiplicative reduction. Its Tate module sits in an exact sequence $0 \to \mathbb{Z}_\ell(1) \to T_\ell(E) \to \mathbb{Z}_\ell \to 0$. Fix an arithmetic Frobenius $\mathrm{Frob}$. Its eigenvalues on $V_\ell(E)$ are $q$ and $1$, which are distinct, so there is a basis $e_1, e_2$ of $V_\ell(E)$ with $e_1$ in the image of $\mathbb{Q}_\ell(1)$ and $\mathrm{Frob} = \mathrm{diag}(q, 1)$. The monodromy is $N e_1 = 0$ and $N e_2 = c e_1$ for some $c \ne 0$. Then $\mathrm{Frob} \, N \, \mathrm{Frob}^{-1} e_2 = \mathrm{Frob} \, N e_2 = q c e_1 = q N e_2$, as the relation predicts.

### Global fields

The letter $F$ denotes a number field. Its places are $v$, its completions are $F_v$, and for a finite place $v$ the residue field has $q_v = N(v)$ elements. The absolute values $|\cdot|_v$ are normalized as above at the finite places. At a real place $|\cdot|_v$ is the usual absolute value, and at a complex place it is its square. With this normalization the product formula $\prod_v |x|_v = 1$ holds for $x \in F^\times$. The adeles are $\mathbb{A}_F$, the ideles are $\mathbb{A}_F^\times$, and $C_F = \mathbb{A}_F^\times / F^\times$ is the idele class group. The global Artin map sends a uniformizer at an unramified place $v$ to $\mathrm{Frob}_v^{-1} = \Phi_v$.

A Galois representation is a continuous representation of $G_F$ on a finite-dimensional vector space over $\bar{\mathbb{Q}}_\ell$. A statement that compares Galois representations with automorphic representations fixes an isomorphism of fields $\iota : \bar{\mathbb{Q}}_\ell \to \mathbb{C}$. Some statements depend on $\iota$, and the handbook says so when they do.

### The table of conventions

| Object | Convention of the handbook |
|---|---|
| Frobenius | $\Phi$ is geometric, $x \mapsto x^{1/q}$; $\mathrm{Frob}$ is arithmetic, $x \mapsto x^q$ |
| local reciprocity | $\mathrm{rec}_K(\varpi)$ is the class of a geometric Frobenius |
| global reciprocity | a uniformizer at an unramified place $v$ goes to $\Phi_v = \mathrm{Frob}_v^{-1}$ |
| absolute value | $|\varpi|_K = q^{-1}$ |
| norm on $W_K$ | $\|w\| = q^{d(w)}$, so $\|\Phi\| = q^{-1}$ and $\|\mathrm{rec}_K(x)\| = |x|_K$ |
| Weil-Deligne representations | $r(w) N r(w)^{-1} = \|w\| N$ |
| L-factor of $(V, r, N)$ | $\det(1 - q^{-s} r(\Phi) \mid V_N^{I_K})^{-1}$, where $V_N = \ker N$ |
| additive character | fixed in each statement; the standard one is in Section 2 |
| Haar measure | the measure that is self-dual for the additive character |
| Satake parameters | unitary, unless a statement says arithmetic |
| $q$-expansion | $q = e^{2\pi i \tau}$, for a cusp of width 1 |
| centre of the functional equation | $s = 1/2$ for automorphic L-functions, $s = 1$ for $L(E, s)$, $s = k/2$ for $L(f, s)$ in weight $k$ |
