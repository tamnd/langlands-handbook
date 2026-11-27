---
title: Automorphic forms
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Automorphic forms

This section defines automorphic forms on $GL_2(\mathbb{A})$ as in [Bum97], Chapter 3, and [GH24]: smooth functions on $GL_2(\mathbb{Q})\backslash GL_2(\mathbb{A})$ that are $K$-finite, $Z(\mathfrak{g})$-finite and of moderate growth. The first examples are the functions $\phi_f$ of Chapter 1. The others are the adelic Maass forms, the characters $\chi \circ \det$ and the Eisenstein series. The main result is that the automorphic forms are a module for $\mathfrak{g}$, for $K_\infty$ and for $GL_2(\mathbb{A}_f)$, though not for $GL_2(\mathbb{R})$. For the action of $\mathfrak{g}$ one needs a theorem of Harish-Chandra, which says that each automorphic form is a convolution of itself with a test function.

### Heights and moderate growth

Let $\mathbb{A} = \mathbb{A}_\mathbb{Q} = \mathbb{R} \times \mathbb{A}_f$ be the adele ring of Volume 3. For a prime $p$ let $K_p = GL_2(\mathbb{Z}_p)$, and put
$$K_f = \prod_p K_p = GL_2(\widehat{\mathbb{Z}}), \qquad K = K_\infty K_f, \qquad K_\infty = O(2).$$
The group $G(\mathbb{Q})$ is embedded in $G(\mathbb{A})$ on the diagonal. We use the notation of Definition 2.1.1 at the real place, and the same letters $u(x)$, $a(y)$ for $x \in \mathbb{A}$, $y \in \mathbb{A}^\times$. For $f \in M_k(\Gamma_0(N))$ we write $\phi_f$ for the function of Chapter 1, normalized by
$$\phi_f(\gamma g_\infty k) = f(g_\infty i)\, j(g_\infty, i)^{-k} (\det g_\infty)^{k/2}, \qquad \gamma \in G(\mathbb{Q}),\ g_\infty \in G(\mathbb{R})^+,\ k \in K_0(N), \tag{2.2.1}$$
where $K_0(N)$ is the group of the $\left(\begin{smallmatrix} a & b \\ c & d \end{smallmatrix}\right) \in K_f$ with $c \in N\widehat{\mathbb{Z}}$. Chapter 1 proves that $G(\mathbb{A}) = G(\mathbb{Q})G(\mathbb{R})^+K_0(N)$ and that (2.2.1) is well defined. In the notation of Example 2.1.8, $\phi_f(g_\infty) = F_f(g_\infty)$ for $g_\infty \in G(\mathbb{R})^+$.

**Definition 2.2.1 (height).** For a place $v$ and $g \in G(\mathbb{Q}_v)$ let $\|g\|_v$ be the largest of the numbers $|g_{ij}|_v$ and $|(g^{-1})_{ij}|_v$. For $g = (g_v) \in G(\mathbb{A})$ the *height* of $g$ is $\|g\| = \prod_v \|g_v\|_v$.

Lean: not formalized

For almost all $p$ the entries of $g_p$ and $g_p^{-1}$ lie in $\mathbb{Z}_p$, and one of them is a unit, so $\|g_p\|_p = 1$ and the product is finite. This is the height of Volume 7, Chapter 1, for $n = 2$.

**Lemma 2.2.2 (properties of the height).** For $g, h \in G(\mathbb{A})$ we have $\|g^{-1}\| = \|g\|$, $\|gh\| \le 2\|g\|\,\|h\|$ and $\|g\| \ge 2^{-1/2}$. For $k \in K$, $\|k\| \le 1$. For $x \in \mathbb{R}$ with $|x| \le 1$ and $t \ge 1$, the element $u(x)a(t)$ of $G(\mathbb{R})$ has height $t$.

Lean: not formalized

*Proof.* The first claim holds by definition. At a prime $p$ the ultrametric inequality gives $|(gh)_{ij}|_p \le \|g\|_p\|h\|_p$, and at the real place each entry of $gh$ is a sum of two products, so $|(gh)_{ij}| \le 2\|g\|_\infty\|h\|_\infty$; the same holds for $(gh)^{-1} = h^{-1}g^{-1}$. From $g g^{-1} = 1$ the same estimates give $1 \le \|g_p\|_p^2$ and $1 \le 2\|g_\infty\|_\infty^2$. The entries of an element of $K$ and of its inverse have absolute value at most $1$ at each place. Finally $u(x)a(t)$ has the entries $t, x, 1$ and its inverse has the entries $t^{-1}, -x t^{-1}, 1$, and the largest of these absolute values is $t$. $\square$

**Definition 2.2.3 (moderate growth).** A function $\varphi : G(\mathbb{A}) \to \mathbb{C}$ has *moderate growth* if there are constants $C$ and $r$ with $|\varphi(g)| \le C\|g\|^r$ for all $g \in G(\mathbb{A})$.

Lean: not formalized

### Automorphic forms

**Definition 2.2.4 (automorphic form).** An *automorphic form* on $G(\mathbb{A})$ is a function $\varphi : G(\mathbb{A}) \to \mathbb{C}$ with these properties.
1. It is left invariant under $G(\mathbb{Q})$: $\varphi(\gamma g) = \varphi(g)$.
2. It is smooth: there is an open compact subgroup $K' \subseteq G(\mathbb{A}_f)$ with $\varphi(gk) = \varphi(g)$ for $k \in K'$, and for each $g_f \in G(\mathbb{A}_f)$ the function $g_\infty \mapsto \varphi(g_\infty g_f)$ is smooth on $G(\mathbb{R})$.
3. It is $K$-finite: the right translates $\rho(k)\varphi$, $k \in K$, span a finite-dimensional space.
4. It is $Z(\mathfrak{g})$-finite: the functions $D\varphi$, $D \in Z(\mathfrak{g})$, span a finite-dimensional space.
5. It has moderate growth.

We write $\mathcal{A}(G)$ for the space of automorphic forms. For a character $\omega$ of $\mathbb{Q}^\times\backslash\mathbb{A}^\times$ we write $\mathcal{A}(G, \omega)$ for the subspace of the $\varphi$ with $\varphi(zg) = \omega(z)\varphi(g)$ for all scalar matrices $z \in Z(\mathbb{A}) = \mathbb{A}^\times$, and call $\omega$ the *central character*.

Lean: `Langlands.Fidelity.IsAutomorphicFormGL`, a weaker structure, see Remark 2.2.5

In condition 3, $K_f$-finiteness follows from condition 2, since $K' \cap K_f$ has finite index in $K_f$. So condition 3 is a condition at the real place: the translates under $O(2)$ span a finite-dimensional space. Condition 4 is equivalent to the existence of an ideal $J$ of finite codimension in $Z(\mathfrak{g})$ with $J\varphi = 0$. If $\varphi$ has a central character, then $Z$ acts on it by a scalar, so by Proposition 2.1.6 condition 4 says that $\varphi$ is killed by a nonzero polynomial in $\Delta$.

**Remark 2.2.5 (the Lean structure).** The structure `Langlands.Fidelity.IsAutomorphicFormGL K n N φ` of the Lean project is the structure `Langlands.IsCuspForm` without its cuspidal condition. It asks that $\varphi$ be continuous, left invariant under $GL_n(K)$, right invariant under the principal congruence subgroup $K(N)$, with a central character, and that $|\varphi(g)| \le C|\det g|^s$. It has no condition of $K_\infty$-finiteness or of $Z(\mathfrak{g})$-finiteness, and its growth condition is a bound by a constant on the group of the $g$ with $|\det g| = 1$. This bound holds for cusp forms with a unitary central character (Corollary 2.3.11), and it fails for the Eisenstein series of Example 2.2.9. Volume 7, Remark 1.2.6, compares the Lean cusp forms with the cusp forms of this chapter.

### Examples

**Example 2.2.6 (modular forms).** Let $f \in M_k(\Gamma_0(N))$. Chapter 1 proves that $\phi_f$ is left invariant under $G(\mathbb{Q})$, right invariant under $K_0(N)$, invariant under $Z(\mathbb{A})$ and of moderate growth. By Example 2.1.8, $\phi_f(g\kappa_\theta) = e^{ik\theta}\phi_f(g)$, $L\phi_f = 0$ and $\Delta\phi_f = \frac{k}{2}(1 - \frac{k}{2})\phi_f$. The element $\varepsilon_\infty \in K_\infty$ is $\varepsilon \cdot \varepsilon_f^{-1}$ with $\varepsilon \in G(\mathbb{Q})$ and $\varepsilon_f \in K_0(N)$, so
$$\phi_f(g\varepsilon_\infty) = \phi_f(g \varepsilon \varepsilon_f^{-1}) = \phi_f(g\varepsilon) = \phi_f(\varepsilon g \varepsilon),$$
and $\rho(\varepsilon_\infty)\phi_f$ is the function $g \mapsto \phi_f(\varepsilon g \varepsilon)$, of weight $-k$. So the translates of $\phi_f$ under $O(2)$ span the plane of $\phi_f$ and $\rho(\varepsilon_\infty)\phi_f$, and $\phi_f \in \mathcal{A}(G, 1)$. Chapter 1 also proves the converse: each $\varphi \in \mathcal{A}(G, 1)$ that is right invariant under $K_0(N)$, of weight $k$ and killed by $L$ is $\phi_f$ for a unique $f \in M_k(\Gamma_0(N))$.

**Example 2.2.7 (Maass forms).** Let $u$ be a Maass cusp form of level $N$, trivial character and eigenvalue $\lambda$, as in Volume 4, Definition 2.6.7. Put $\phi_u(\gamma g_\infty k) = u(g_\infty i)$ for $\gamma \in G(\mathbb{Q})$, $g_\infty \in G(\mathbb{R})^+$ and $k \in K_0(N)$. The same proof as for $\phi_f$ shows that $\phi_u$ is well defined. It has weight $0$, and by Example 2.1.9, $\Delta\phi_u = \lambda\phi_u$. A Maass form need not be invariant under $z \mapsto -\bar z$, so $\phi_u$ need not be invariant under $\varepsilon_\infty$, but the argument of Example 2.2.6 shows that $\rho(\varepsilon_\infty)\phi_u = \phi_{\check u}$ with $\check u(z) = u(-\bar z)$. So $\phi_u \in \mathcal{A}(G, 1)$, and the decomposition $u = \frac{1}{2}(u + \check u) + \frac{1}{2}(u - \check u)$ into even and odd forms is the decomposition of $\phi_u$ under $\varepsilon_\infty$.

**Example 2.2.8 (characters).** Let $\chi$ be a character of $\mathbb{Q}^\times\backslash\mathbb{A}^\times$. Since $\mathbb{A}^\times = \mathbb{Q}^\times \times \mathbb{R}_{>0} \times \widehat{\mathbb{Z}}^\times$, it is $\chi = \chi_0|\cdot|_\mathbb{A}^\sigma$ with $\sigma \in \mathbb{C}$ and $\chi_0$ of finite order, and $\chi_\infty(t) = |t|^\sigma\mathrm{sgn}(t)^\delta$ with $\delta \in \{0, 1\}$. Then $\varphi(g) = \chi(\det g)$ is an automorphic form with central character $\chi^2$. It is right invariant under an open compact subgroup, it transforms under $O(2)$ by the character $\mathrm{sgn}(\det)^\delta$, and $H$, $R$, $L$ kill it, since it is invariant under right translation by $SL_2(\mathbb{R})$; so $\Delta\varphi = 0$. Finally $|\varphi(g)| = |\det g|_\mathbb{A}^{\mathrm{Re}(\sigma)}$, and the estimates of Lemma 2.2.2 give $|\det g|_\mathbb{A} \le 2\|g\|^2$ and $|\det g|_\mathbb{A}^{-1} \le 2\|g\|^2$, so $\varphi$ has moderate growth.

**Example 2.2.9 (Eisenstein series).** For $s \in \mathbb{C}$ let $f_s : G(\mathbb{A}) \to \mathbb{C}$ be the function with
$$f_s\left(\begin{pmatrix} a & b \\ 0 & d \end{pmatrix} k\right) = \left|\frac{a}{d}\right|_\mathbb{A}^s, \qquad k \in K.$$
It is well defined, since $|a/d|_\mathbb{A} = 1$ for an upper triangular element of $K$. It is left invariant under $B(\mathbb{Q})$ by the product formula, and right invariant under $K$. For $\mathrm{Re}(s) > 1$ the series
$$E(g, s) = \sum_{\gamma \in B(\mathbb{Q})\backslash G(\mathbb{Q})} f_s(\gamma g)$$
converges absolutely and uniformly on compact sets. Since $G(\mathbb{Q}) = B(\mathbb{Q})SL_2(\mathbb{Z})$ and $B(\mathbb{Q}) \cap SL_2(\mathbb{Z}) = \{\pm u(n) : n \in \mathbb{Z}\}$, the set $B(\mathbb{Q})\backslash G(\mathbb{Q})$ is $\Gamma_\infty\backslash SL_2(\mathbb{Z})$ with $\Gamma_\infty = \{\pm u(n)\}$. For $g_\infty \in SL_2(\mathbb{R})$ with $g_\infty i = z$ and $\gamma \in SL_2(\mathbb{Z})$, the finite part of $\gamma g_\infty$ is in $K_f$, so $f_s(\gamma g_\infty) = \mathrm{Im}(\gamma z)^s$, and
$$E(g_\infty, s) = \sum_{\gamma \in \Gamma_\infty\backslash SL_2(\mathbb{Z})} \mathrm{Im}(\gamma z)^s = E(z, s)$$
is the Eisenstein series of Volume 4, Example 2.6.4. The function $E(g, s)$ is $K$-invariant, satisfies $\Delta E = s(1 - s)E$ by Lemma 2.1.7, and has moderate growth ([Bum97], Chapter 3). So $E(\cdot, s) \in \mathcal{A}(G, 1)$. Its meromorphic continuation in $s$, and the fact that the continuation is still automorphic, are proved in [Bum97], Chapter 3.

### The module structure

The group $G(\mathbb{A})$ acts on functions on $G(\mathbb{Q})\backslash G(\mathbb{A})$ by right translation. The group $G(\mathbb{A}_f)$ and the group $K_\infty$ preserve $\mathcal{A}(G)$, but $G(\mathbb{R})$ does not: the translate of $\phi_f$ by $a(2)$ is no longer of finite type under $O(2)$. The Lie algebra acts by Lemma 2.1.7, and we must show that the derivatives of an automorphic form still have moderate growth. This needs the following theorem.

**Theorem 2.2.10 (Harish-Chandra).** Let $\varphi \in \mathcal{A}(G)$. Then there is a smooth function $\alpha$ with compact support on $G(\mathbb{R})$ with
$$\varphi(g) = (\varphi * \alpha)(g) = \int_{G(\mathbb{R})} \varphi(g h^{-1})\alpha(h)\,dh \qquad \text{for all } g \in G(\mathbb{A}).$$
One may take $\alpha$ invariant under conjugation by $K_\infty$, and $\alpha$ depends only on the $K_\infty$-types of $\varphi$ and on an ideal of finite codimension in $Z(\mathfrak{g})$ that kills $\varphi$.

Lean: not formalized

*Outline of the proof.* The proof is in Harish-Chandra, *Automorphic Forms on Semisimple Lie Groups*, Lecture Notes in Mathematics 62 (Springer 1968), Chapter I, and [Bum97], Chapter 3, gives it for $GL_2$. Let $J$ be an ideal of finite codimension in $Z(\mathfrak{g})$ that kills $\varphi$, and let $\tau$ be the finite set of $K_\infty$-types of $\varphi$. Let $\mathcal{S}$ be the space of smooth functions $F$ on $G(\mathbb{R})$ that are killed by $J$ and whose $K_\infty$-translates have types in $\tau$. For each $g_f$ the function $g_\infty \mapsto \varphi(g_\infty g_f)$ lies in $\mathcal{S}$, and $\mathcal{S}$ is stable under left translations. First, the elements of $\mathcal{S}$ satisfy an elliptic system, since $\Delta + \frac{1}{2}H^2$ is elliptic by Lemma 2.1.7. So they are real analytic, and their germs at $1$ form a finite-dimensional space $\mathcal{V}$. Second, let $\alpha_n$ be an approximate identity of functions invariant under conjugation by $K_\infty$. Convolution with $\alpha_n$ preserves $\mathcal{S}$ and induces an operator $T_n$ on $\mathcal{V}$, with $T_n \to 1$. The span of the $T_n$ is a finite-dimensional, hence closed, subspace of $\mathrm{End}(\mathcal{V})$, so it contains the identity, and some finite linear combination $\alpha$ of the $\alpha_n$ gives $T = 1$. Then $F * \alpha$ and $F$ have the same germ at $1$ for each $F \in \mathcal{S}$, and, applied to the left translates of $F$, the same germ at each point. So $F * \alpha = F$ for all $F \in \mathcal{S}$, and in particular $\varphi * \alpha = \varphi$. $\square$

**Corollary 2.2.11 (derivatives).** Let $\varphi \in \mathcal{A}(G)$ satisfy $|\varphi(g)| \le C\|g\|^r$. For each $X \in U(\mathfrak{g}_\mathbb{C})$ there is $C_X$ with $|X\varphi(g)| \le C_X\|g\|^r$, with the same exponent $r$.

Lean: not formalized

*Proof.* Write $\varphi = \varphi * \alpha$ by Theorem 2.2.10. The substitution $h \mapsto g_\infty^{-1}h$ shows that right derivatives of $\varphi * \alpha$ fall on $\alpha$: $X(\varphi * \alpha) = \varphi * (X\alpha)$, where $X\alpha$ is the right derivative of $\alpha$. Let $S$ be the support of $\alpha$, a compact set. By Lemma 2.2.2,
$$|X\varphi(g)| \le \int_S |\varphi(gh^{-1})|\,|X\alpha(h)|\,dh \le C 2^r \|g\|^r \sup_{h \in S}\|h\|^r \int_S |X\alpha(h)|\,dh. \qquad \square$$

**Proposition 2.2.12 (the automorphic forms are a module).** The space $\mathcal{A}(G)$ is stable under the action of $\mathfrak{g}_\mathbb{C}$ by right derivatives, and under right translation by $K_\infty$ and by $G(\mathbb{A}_f)$. With these actions it is a $(\mathfrak{g}, K_\infty)$-module and a smooth representation of $G(\mathbb{A}_f)$, and the two structures commute. The same holds for $\mathcal{A}(G, \omega)$.

Lean: not formalized

*Proof.* Left invariance and smoothness are preserved by all these operations; for $h \in G(\mathbb{A}_f)$ the function $\rho(h)\varphi$ is invariant under $h^{-1}K'h$. Right translation by $h \in G(\mathbb{A}_f)$ commutes with $\rho(K_\infty)$ and with $\mathfrak{g}$, so it preserves $K_\infty$-finiteness and $Z(\mathfrak{g})$-finiteness, and $\|gh\| \le 2\|g\|\|h\|$ preserves moderate growth. For $k \in K_\infty$, $\rho(k)\varphi$ has the same span of $K_\infty$-translates, and $Z(\mathfrak{g})$ commutes with $\rho(k)$; since $\|gk\| \le 2\|g\|$, moderate growth is preserved. For $X \in \mathfrak{g}_\mathbb{C}$, the identity $\rho(k)X\varphi = (\mathrm{Ad}(k)X)\rho(k)\varphi$ shows that the $K_\infty$-translates of $X\varphi$ lie in the image of $\mathfrak{g}_\mathbb{C} \otimes V$, where $V$ is the span of the $K_\infty$-translates of $\varphi$, so they span a finite-dimensional space. The center $Z(\mathfrak{g})$ commutes with $X$, and $X\varphi$ has moderate growth by Corollary 2.2.11. The axioms of Definition 2.1.10 hold since they hold for the action of $G(\mathbb{R})$ on smooth functions. A vector of $\mathcal{A}(G)$ is invariant under an open compact subgroup of $G(\mathbb{A}_f)$, which is the definition of a smooth representation. The central character is preserved by all these operations. $\square$

**Proposition 2.2.13 (finiteness, Harish-Chandra).** Let $K' \subseteq G(\mathbb{A}_f)$ be an open compact subgroup, $\tau$ a finite set of irreducible representations of $K_\infty$, and $J$ an ideal of finite codimension in $Z(\mathfrak{g})$. Then the space of the $\varphi \in \mathcal{A}(G)$ that are right invariant under $K'$, killed by $J$ and of $K_\infty$-types in $\tau$ is finite-dimensional.

Lean: not formalized

*Outline of the proof.* This is the finiteness theorem of Harish-Chandra, LNM 62, Chapter I. For cusp forms we give a proof in Corollary 2.3.15. For the whole space one subtracts suitable Eisenstein series to reduce to cusp forms, and the Eisenstein series of a given type form a finite-dimensional family. $\square$
