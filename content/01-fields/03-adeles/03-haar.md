---
title: Haar measures
nodes: []
sources: [CF67]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Haar measures

This section fixes the Haar measures on local fields and on the adeles, computes the volume of $\mathbb{A}_F / F$, and gives Artin's proof of the product formula. We follow [CF67], Chapter II, Sections 11 and 14, and Chapter XV, Sections 2.2 and 3.3.

### The modulus

A locally compact Hausdorff abelian group $G$ has a *Haar measure*: a nonzero regular Borel measure $\mu$ that is invariant under translations. It is unique up to a positive constant ([CF67], Chapter II, Section 11). Let $K$ be a local field, and $\mu$ a Haar measure on the additive group of $K$. For $a \in K^\times$, the measure $E \mapsto \mu(aE)$ is again a Haar measure. Thus there is a number $\mathrm{mod}_K(a) > 0$ with $\mu(aE) = \mathrm{mod}_K(a) \mu(E)$ for all Borel sets $E$. It does not depend on the choice of $\mu$. In Mathlib, a Haar measure on an additive group is a measure with the property `MeasureTheory.Measure.IsAddHaarMeasure`.

**Proposition 3.3.1 (the modulus is the normalized absolute value).** For $a \in K^\times$, $\mathrm{mod}_K(a) = |a|_K$, where $|\cdot|_K$ is the normalized absolute value: $|a|_K = q^{-v_K(a)}$ if $K$ is nonarchimedean, the usual absolute value if $K = \mathbb{R}$, and the square of the usual absolute value if $K = \mathbb{C}$.

Lean: not stated yet

*Proof.* Let $K$ be nonarchimedean. A unit $u$ satisfies $u\mathcal{O}_K = \mathcal{O}_K$, so $\mathrm{mod}_K(u) = 1$, and $\mathrm{mod}_K$ is a homomorphism. The ring $\mathcal{O}_K$ is the disjoint union of the $q$ cosets of $\varpi \mathcal{O}_K$, which have the same measure. Thus $\mu(\varpi \mathcal{O}_K) = q^{-1} \mu(\mathcal{O}_K)$, and $\mathrm{mod}_K(\varpi) = q^{-1}$. For $K = \mathbb{R}$, the Lebesgue measure of $a[0,1]$ is $|a|$. For $K = \mathbb{C}$, multiplication by $a$ is a real linear map of $\mathbb{R}^2$ with determinant $|a|^2$. $\square$

This proposition is the reason for the normalization of Definition 2.2.9. The product formula of Theorem 2.2.10 becomes a statement about measures, as in Theorem 3.3.4 below.

### Local measures

On a nonarchimedean local field $K$, the *standard measure* $dx$ is the Haar measure with $\mathrm{vol}(\mathcal{O}_K) = 1$. On $\mathbb{R}$ it is the Lebesgue measure $dx$. On $\mathbb{C}$ it is $2\,dx\,dy$, twice the Lebesgue measure. These are the measures of Section 1.3.

A second normalization depends on an additive character. Fix a nontrivial continuous character $\psi : K \to S^1$. For an integrable function $f$, the Fourier transform is $\hat f(y) = \int_K f(x) \psi(xy) \, dx$. There is exactly one Haar measure, the *self-dual measure* for $\psi$, for which the inversion formula $\hat{\hat f}(x) = f(-x)$ holds. For the standard characters
$$\psi_\mathbb{R}(x) = e^{-2\pi i x}, \qquad \psi_{\mathbb{Q}_p}(x) = e^{2 \pi i \{x\}_p}, \qquad \psi_K = \psi_{\mathbb{Q}_p} \circ \mathrm{Tr}_{K/\mathbb{Q}_p},$$
where $\{x\}_p \in \mathbb{Z}[1/p]$ is the fractional part of $x \in \mathbb{Q}_p$, the self-dual measures are as follows ([CF67], Chapter XV, Section 2.2). On $\mathbb{R}$ it is $dx$, on $\mathbb{C}$ with $\psi_\mathbb{C} = \psi_\mathbb{R} \circ \mathrm{Tr}_{\mathbb{C}/\mathbb{R}}$ it is $2 \, dx \, dy$, and on a finite extension $K$ of $\mathbb{Q}_p$ it gives $\mathcal{O}_K$ the volume $N(\mathfrak{D}_{K/\mathbb{Q}_p})^{-1/2}$, where $\mathfrak{D}$ is the different of Section 2.5. Thus the two normalizations agree except at the finitely many places that are ramified over $\mathbb{Q}$.

On the multiplicative group $K^\times$, the measure $dx / |x|_K$ is a Haar measure, because $d(ax) = |a|_K dx$. For $K$ nonarchimedean, the *standard multiplicative measure* is
$$d^\times x = \frac{q}{q - 1} \frac{dx}{|x|_K},$$
so that $\mathrm{vol}(\mathcal{O}_K^\times) = 1$, since $\mathcal{O}_K^\times = \mathcal{O}_K \setminus \varpi \mathcal{O}_K$ has volume $1 - q^{-1}$ for $dx$. For $K$ archimedean, $d^\times x = dx / |x|_K$.

### Measures on the adeles

**Proposition 3.3.2 (the measure on the adeles).** Let $\mu_v$ be a Haar measure on $F_v$ for each place $v$, with $\mu_v(\mathcal{O}_v) = 1$ for almost all $v$. There is a unique Haar measure $\mu$ on $\mathbb{A}_F$ whose restriction to each open subgroup $\mathbb{A}_{F,S} = \prod_{v \in S} F_v \times \prod_{v \notin S} \mathcal{O}_v$ is the product measure, for each finite set $S$ that contains the infinite places and the places where $\mu_v(\mathcal{O}_v) \ne 1$.

Lean: `MeasureTheory.Measure.addHaar`, from Mathlib, for the existence of some Haar measure

*Proof.* The product measure on $\prod_{v \notin S} \mathcal{O}_v$ exists because all the factors have measure 1. The product measure on $\mathbb{A}_{F,S}$ is a Haar measure. For $S \subset S'$, the measure on $\mathbb{A}_{F,S'}$ restricts to the measure on $\mathbb{A}_{F,S}$, because $\mu_v(\mathcal{O}_v) = 1$ for $v \in S' \setminus S$. The group $\mathbb{A}_F$ is the increasing union of the open subgroups $\mathbb{A}_{F,S}$, and each compact set lies in one of them, so the measures glue. $\square$

The *standard measure* on $\mathbb{A}_F$ is the product of the standard local measures. The *Tamagawa measure* is the product of the self-dual measures for the character $\psi = \prod_v \psi_v$ with $\psi_v = \psi_{\mathbb{Q}_p} \circ \mathrm{Tr}_{F_v / \mathbb{Q}_p}$ for $v \mid p$ and $\psi_v = \psi_\mathbb{R} \circ \mathrm{Tr}_{F_v/\mathbb{R}}$ for $v \mid \infty$. The character $\psi$ is trivial on $F$ ([CF67], Chapter XV, Lemma 4.1.5), and $\mathbb{A}_F$ is self-dual for it.

**Theorem 3.3.3 (the volume of $\mathbb{A}_F / F$).** For the standard measure, $\mathrm{vol}(\mathbb{A}_F / F) = |d_F|^{1/2}$. For the Tamagawa measure, $\mathrm{vol}(\mathbb{A}_F / F) = 1$.

Lean: not stated yet

*Proof.* By Theorem 3.2.5, $P \times \hat{\mathcal{O}}_F$ is a fundamental domain for $F$ in $\mathbb{A}_F$, where $P$ is a fundamental domain for $\mathcal{O}_F$ in $F_\infty$. For the standard measure, $\mathrm{vol}(\hat{\mathcal{O}}_F) = 1$ and $\mathrm{vol}(P) = |d_F|^{1/2}$ by Proposition 1.3.3. For the Tamagawa measure, the infinite factors are the same, and $\mathrm{vol}(\hat{\mathcal{O}}_F) = \prod_v N(\mathfrak{D}_v)^{-1/2}$. The local differents are the components of the global different $\mathfrak{D}_{F/\mathbb{Q}}$, by Section 2.5, and $N(\mathfrak{D}_{F/\mathbb{Q}}) = |d_F|$. Thus $\mathrm{vol}(\hat{\mathcal{O}}_F) = |d_F|^{-1/2}$, and the volume is 1. $\square$

### Artin's proof of the product formula

For an idele $a = (a_v)$, that is, an element of $\prod'(F_v^\times, \mathcal{O}_v^\times)$ as in Section 3.4, multiplication by $a$ is an automorphism of the additive group $\mathbb{A}_F$. It multiplies each Haar measure by $|a|_\mathbb{A} = \prod_v |a_v|_v$, by Proposition 3.3.1 applied to each factor. The product is finite, because $|a_v|_v = 1$ for almost all $v$.

**Theorem 3.3.4 (the product formula, after Artin).** For $x \in F^\times$, $\prod_v |x|_v = 1$.

Lean: `NumberField.prod_abs_eq_one`, from Mathlib

*Proof.* Multiplication by $x$ is an automorphism of $\mathbb{A}_F$ that maps $F$ onto $F$. Thus it induces a homeomorphism of the compact group $\mathbb{A}_F / F$ onto itself, and it maps a fundamental domain $D$ for $F$ to another fundamental domain $xD$. Two fundamental domains have the same measure, because $\mu(xD) = \sum_{\alpha \in F} \mu(xD \cap (D + \alpha)) = \sum_{\alpha} \mu((xD - \alpha) \cap D) = \mu(D)$, by the invariance of $\mu$ under translations and the fact that the translates $xD - \alpha$ cover $\mathbb{A}_F$ without overlap. On the other hand $\mu(xD) = |x|_\mathbb{A} \mu(D)$. The volume $\mu(D) = \mathrm{vol}(\mathbb{A}_F / F)$ is finite and positive by Theorem 3.3.3, so $|x|_\mathbb{A} = 1$. $\square$

This proof uses no factorization of ideals and no norm computation. It is the model for many arguments of Tate's thesis and of the theory of automorphic forms, in which a statement about a global field becomes a statement about the invariance of a measure on a quotient.
