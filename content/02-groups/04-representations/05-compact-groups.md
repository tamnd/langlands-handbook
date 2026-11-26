---
title: Compact groups and the theorem of Peter and Weyl
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Compact groups and the theorem of Peter and Weyl

We now leave algebraic groups and turn to topological groups. A compact group has an invariant probability measure. With it we average inner products and linear maps, and this gives complete reducibility, the orthogonality relations and the theorem of Peter and Weyl. The model is the circle group $\mathbb{R}/\mathbb{Z}$, whose irreducible representations are the characters $e^{2\pi i n \theta}$ and for which the theorem of Peter and Weyl is the completeness of Fourier series. We follow [Kna02], Chapter 4. In this section a *representation* of a topological group $K$ on a finite-dimensional complex vector space $V$ is a continuous homomorphism $\pi : K \to GL(V)$. A *unitary representation* on a Hilbert space $H$ is a homomorphism $\pi : K \to U(H)$ such that $g \mapsto \pi(g) v$ is continuous for each $v \in H$.

### Haar measure

**Theorem 4.5.1 (Haar measure).** Let $G$ be a locally compact Hausdorff group. There is a nonzero Radon measure $\mu$ on $G$ with $\mu(g E) = \mu(E)$ for all $g \in G$ and all Borel sets $E$. It is unique up to a positive scalar. It is a *left Haar measure*.

Lean: `MeasureTheory.Measure.haarMeasure`, from Mathlib, with uniqueness `MeasureTheory.Measure.isMulLeftInvariant_eq_smul`

For the proof see any text on abstract harmonic analysis, and for Lie groups [Kna02], Chapter 8. Volume 1, Section 3.3, uses Haar measures on local fields and adeles. Mathlib has the class `MeasureTheory.Measure.IsHaarMeasure`, and its uniqueness statement assumes that the group is second countable, which holds for Lie groups. For a Lie group of dimension $d$ there is a direct construction: choose a nonzero alternating $d$-form $\omega_e$ on $\mathfrak{g} = T_e G$, extend it to a left-invariant $d$-form $\omega$ on $G$ by $\omega_g = (l_{g^{-1}})^* \omega_e$, where $l_h(x) = hx$, and integrate $|\omega|$.

For $g \in G$ the measure $E \mapsto \mu(E g)$ is again a left Haar measure, so it equals $\Delta(g) \mu$ for a number $\Delta(g) > 0$. The function $\Delta : G \to \mathbb{R}_{>0}$ is the *modular function*. The group $G$ is *unimodular* if $\Delta = 1$, that is, if $\mu$ is also right invariant. Mathlib has the modular function as `MeasureTheory.Measure.modularCharacter`.

**Proposition 4.5.2 (the modular function).** Let $G$ be a locally compact group.
1. $\Delta$ is a continuous homomorphism $G \to \mathbb{R}_{>0}$.
2. If $G$ is compact, then $G$ is unimodular, and there is a unique Haar measure with $\mu(G) = 1$.
3. If $G$ is a Lie group, then $\Delta(g) = |\det \mathrm{Ad}(g)|^{-1}$.

Lean: `MeasureTheory.Measure.isHaarMeasure_eq_of_isProbabilityMeasure`, from Mathlib, for the uniqueness of the probability measure

*Proof.* For part 1, $\mu(E g h) = \Delta(h) \mu(E g) = \Delta(g) \Delta(h) \mu(E)$, so $\Delta$ is a homomorphism. For continuity see [Kna02], Chapter 8. For part 2, the image $\Delta(G)$ is a compact subgroup of $\mathbb{R}_{>0}$, so it is $\{1\}$. A compact group has finite Haar measure, because compact sets have finite measure, and we normalize it to $1$. For part 3, let $\omega$ be a left-invariant volume form as above, and let $r_g(x) = x g$. The form $r_g^* \omega$ is left invariant, because left and right translations commute, so $r_g^* \omega = c(g) \omega$ for a scalar $c(g)$. At $e$ we have, for $Y \in \mathfrak{g}$,
$$(r_g^* \omega)_e(Y) = \omega_g(d r_g Y) = \omega_e(d l_{g^{-1}} \, d r_g \, Y) = \omega_e(\mathrm{Ad}(g^{-1}) Y),$$
so $c(g) = \det \mathrm{Ad}(g^{-1})$. By the change of variables formula, $\mu(E g) = \int_E |r_g^* \omega| = |\det \mathrm{Ad}(g)|^{-1} \mu(E)$. $\square$

Part 3 shows that a connected Lie group whose adjoint representation has image in $SL^\pm(\mathfrak{g})$ is unimodular. This holds for connected reductive groups and for nilpotent groups, but not for the group of the matrices $\left( \begin{smallmatrix} a & b \\ 0 & 1 \end{smallmatrix} \right)$, by Exercise 8.

**Example 4.5.3 (Haar measures).** On $\mathbb{R}/\mathbb{Z}$ the Haar probability measure is $d\theta$. On $\mathbb{R}^n$ it is Lebesgue measure, and on $\mathbb{R}^\times$ it is $dx/|x|$. On $GL_n(\mathbb{R})$, which is an open subset of $M_n(\mathbb{R})$, the measure $|\det g|^{-n} \prod_{i,j} d g_{ij}$ is a left and right Haar measure, by Exercise 8. The group $SU(2)$ is the group of quaternions of norm $1$, by $\left(\begin{smallmatrix} a & -\bar b \\ b & \bar a \end{smallmatrix}\right) \mapsto a + b j$. So it is the sphere $S^3 \subset \mathbb{H} = \mathbb{R}^4$. Left and right multiplication by a unit quaternion are isometries of $\mathbb{R}^4$, so the rotation-invariant probability measure on $S^3$ is the Haar measure of $SU(2)$. For a nonarchimedean local field $F$, the group $GL_n(\mathcal{O}_F)$ is compact and open in $GL_n(F)$, and the Haar measure of $GL_n(F)$ is normalized by $\mu(GL_n(\mathcal{O}_F)) = 1$ in Volume 6.

### Complete reducibility and orthogonality

From now on $K$ is a compact Hausdorff group and $dg$ is its Haar probability measure.

**Proposition 4.5.4 (unitarity and complete reducibility).** Let $\pi : K \to GL(V)$ be a finite-dimensional representation. There is a Hermitian inner product on $V$ for which every $\pi(g)$ is unitary. Every subrepresentation of $V$ has a complement that is a subrepresentation, and $V$ is a direct sum of irreducible representations.

Lean: not stated yet

*Proof.* Let $\langle\ ,\ \rangle_0$ be any Hermitian inner product on $V$, and put $\langle v, w \rangle = \int_K \langle \pi(g) v, \pi(g) w \rangle_0 \, dg$. The integrand is continuous, so the integral exists. It is a Hermitian inner product, positive because the integrand of $\langle v, v \rangle$ is positive and continuous for $v \neq 0$. It is invariant because $dg$ is right invariant: $\langle \pi(h) v, \pi(h) w \rangle = \int_K \langle \pi(gh)v, \pi(gh) w \rangle_0 \, dg = \langle v, w \rangle$. If $M$ is a subrepresentation, its orthogonal complement for this inner product is a subrepresentation, since the $\pi(g)$ are unitary. The last statement follows by induction on $\dim V$. $\square$

For finite groups this is the theorem of Maschke, which Mathlib has as `MonoidAlgebra.Submodule.exists_isCompl`.

**Lemma 4.5.5 (Schur's lemma).** Let $V$ and $W$ be irreducible finite-dimensional representations of $K$. Every $K$-equivariant linear map $V \to W$ is $0$ or an isomorphism, and every $K$-equivariant endomorphism of $V$ is a scalar.

Lean: `FDRep.finrank_hom_simple_simple`, from Mathlib

*Proof.* The kernel and the image of an equivariant map are subrepresentations, which gives the first statement. An equivariant endomorphism $A$ of $V$ has an eigenvalue $c \in \mathbb{C}$, and $A - c$ is equivariant and not invertible, so it is $0$. $\square$

For a finite-dimensional unitary representation $(\pi, V)$ and $v, w \in V$, the function $f_{v, w}(g) = \langle \pi(g) v, w \rangle$ is a *matrix coefficient* of $\pi$. It is a continuous function on $K$. If $e_1, \dots, e_d$ is an orthonormal basis, the functions $f_{e_j, e_i}$ are the entries $\pi_{ij}(g)$ of the matrix of $\pi(g)$.

**Theorem 4.5.6 (Schur orthogonality).** Let $(\pi, V)$ and $(\pi', V')$ be irreducible unitary representations of $K$ of finite dimension. Let $v_1, v_2 \in V$ and $v'_1, v'_2 \in V'$.
1. If $\pi \not\cong \pi'$, then $\int_K \langle \pi(g) v_1, v_2 \rangle \, \overline{\langle \pi'(g) v'_1, v'_2 \rangle} \, dg = 0$.
2. $\int_K \langle \pi(g) v_1, v_2 \rangle \, \overline{\langle \pi(g) w_1, w_2 \rangle} \, dg = \frac{1}{\dim V} \langle v_1, w_1 \rangle \overline{\langle v_2, w_2 \rangle}$ for $w_1, w_2 \in V$.

Lean: not stated yet

*Proof.* For a linear map $A : V' \to V$, put $\tilde A = \int_K \pi(g) A \pi'(g)^{-1} \, dg$. The invariance of $dg$ shows that $\pi(h) \tilde A \pi'(h)^{-1} = \tilde A$, so $\tilde A$ is equivariant. Take $A = \langle \cdot, v'_1 \rangle v_1$, that is, $A(x) = \langle x, v'_1 \rangle v_1$. Since $\pi'(g)^{-1} = \pi'(g)^*$, we get
$$\langle \tilde A v'_2, v_2 \rangle = \int_K \langle \pi'(g)^{-1} v'_2, v'_1 \rangle \langle \pi(g) v_1, v_2 \rangle \, dg = \int_K \langle \pi(g) v_1, v_2 \rangle \overline{\langle \pi'(g) v'_1, v'_2 \rangle} \, dg.$$
In case 1, $\tilde A = 0$ by Lemma 4.5.5, and the integral vanishes. In case 2, take $V' = V$ with $v'_i = w_i$. Then $\tilde A = c \cdot 1$ by Lemma 4.5.5, and taking traces gives $c \dim V = \mathrm{tr} \tilde A = \mathrm{tr} A = \langle v_1, w_1 \rangle$. So the integral is $c \langle w_2, v_2 \rangle$, which is the formula. $\square$

The *character* of a finite-dimensional representation is $\chi_\pi(g) = \mathrm{tr}\, \pi(g)$. It is a continuous class function, $\chi_{\pi \oplus \pi'} = \chi_\pi + \chi_{\pi'}$, $\chi_{\pi \otimes \pi'} = \chi_\pi \chi_{\pi'}$, and $\chi_{\pi^*} = \overline{\chi_\pi}$, since the eigenvalues of the unitary $\pi(g)$ have absolute value $1$.

**Corollary 4.5.7 (orthogonality of characters).** The characters of the irreducible representations of $K$ form an orthonormal set in $L^2(K)$. A finite-dimensional representation $\pi$ contains the irreducible representation $\sigma$ with multiplicity $\langle \chi_\pi, \chi_\sigma \rangle$, so $\pi$ is determined up to isomorphism by $\chi_\pi$. The representation $\pi$ is irreducible if and only if $\int_K |\chi_\pi(g)|^2 \, dg = 1$.

Lean: `FDRep.char_orthonormal`, from Mathlib, for finite groups

*Proof.* Write $\chi_\pi = \sum_i f_{e_i, e_i}$ for an orthonormal basis and apply Theorem 4.5.6: for irreducible $\pi$ we get $\| \chi_\pi \|^2 = \sum_{i,j} \frac{1}{\dim V} |\langle e_i, e_j \rangle|^2 = 1$. The other statements follow from Proposition 4.5.4: if $\pi = \bigoplus \sigma_j^{n_j}$, then $\langle \chi_\pi, \chi_{\sigma_j} \rangle = n_j$ and $\| \chi_\pi \|^2 = \sum n_j^2$. $\square$

### The theorem of Peter and Weyl

Let $\widehat K$ be the set of isomorphism classes of irreducible finite-dimensional representations of $K$. For each class choose a unitary representative $(\pi, V_\pi)$ and an orthonormal basis, with matrix entries $\pi_{ij}$. The group $K \times K$ acts on $L^2(K)$ by $((g, h) f)(x) = f(g^{-1} x h)$.

**Theorem 4.5.8 (Peter and Weyl).** Let $K$ be a compact group.
1. The span of the matrix coefficients of the finite-dimensional representations is dense in $C(K)$ for the uniform norm.
2. The functions $\sqrt{\dim \pi} \, \pi_{ij}$, for $\pi \in \widehat K$ and $1 \le i, j \le \dim \pi$, form an orthonormal basis of $L^2(K)$. Equivalently, as a representation of $K \times K$,
$$L^2(K) \cong \widehat{\bigoplus_{\pi \in \widehat K}} \ \overline{V_\pi} \otimes V_\pi,$$
a Hilbert direct sum.
3. For every $g \neq e$ in $K$ there is a finite-dimensional representation $\pi$ with $\pi(g) \neq 1$.
4. The characters $\chi_\pi$, for $\pi \in \widehat K$, form an orthonormal basis of the space of class functions in $L^2(K)$.

Lean: `span_fourier_closure_eq_top` and `hasSum_fourier_series_L2`, from Mathlib, for the circle only

*Outline of the proof.* We follow [Kna02], Chapter 4.
1. Let $\varphi$ be a continuous function on $K$ with $\varphi(x^{-1}) = \overline{\varphi(x)}$. The convolution operator $T_\varphi f = \varphi * f$, $(\varphi * f)(x) = \int_K \varphi(x y^{-1}) f(y) \, dy$, is a self-adjoint Hilbert and Schmidt operator on $L^2(K)$, so it is compact. It commutes with the right translations.
2. By the spectral theorem for compact self-adjoint operators, $L^2(K)$ is the Hilbert sum of the kernel of $T_\varphi$ and of the eigenspaces $E_c$ with $c \neq 0$, and each $E_c$ is finite-dimensional. Each $E_c$ is stable under right translation, so it is a finite-dimensional representation of $K$. Its elements are continuous, since they lie in the image of $T_\varphi$.
3. A continuous function $f$ in a finite-dimensional space stable under right translation is a matrix coefficient. Indeed, if $f_1, \dots, f_d$ is a basis, then $f(xg) = \sum_i c_i(g) f_i(x)$ with continuous $c_i$, and $f(g) = \sum_i c_i(g) f_i(e)$.
4. Let $f$ be continuous, and write $f = f_0 + \sum_c f_c$ with $T_\varphi f_0 = 0$ and $f_c \in E_c$. Then $\varphi * f = \sum_c c f_c$. This series converges uniformly, because $\| \varphi * h \|_\infty \le \| \varphi \|_2 \| h \|_2$ for $h \in L^2(K)$. Each $f_c$ is a matrix coefficient by step 3. Now let $\varphi$ run over an approximate identity, a sequence of such functions that are $\ge 0$, have integral $1$ and have support shrinking to $e$. Then $\varphi * f \to f$ uniformly, by the uniform continuity of $f$. This proves part 1. Since $C(K)$ is dense in $L^2(K)$, the matrix coefficients are also dense in $L^2(K)$.
5. Theorem 4.5.6 shows that the functions $\sqrt{\dim \pi} \, \pi_{ij}$ are orthonormal, and every matrix coefficient is a linear combination of them by Proposition 4.5.4. With step 4 this gives part 2.
6. For part 3, if $\pi(g) = 1$ for all $\pi$, then $f(g) = f(e)$ for all matrix coefficients, hence for all continuous functions by part 1, and $g = e$ by the theorem of Urysohn. For part 4, project a class function onto the span of the $\pi_{ij}$ for one $\pi$. The projection commutes with conjugation, and the conjugation invariant elements of $\mathrm{span}(\pi_{ij}) \cong \overline{V_\pi} \otimes V_\pi$ form the line spanned by $\chi_\pi$, by Lemma 4.5.5. $\square$

**Example 4.5.9 (the circle).** For $K = \mathbb{R}/\mathbb{Z}$, each irreducible representation is a character, by Lemma 4.5.5, since $K$ is abelian. A continuous homomorphism $\mathbb{R}/\mathbb{Z} \to \mathbb{C}^\times$ has image in the unit circle, by compactness, and it lifts to a continuous homomorphism $\mathbb{R} \to \mathbb{R}$, which is linear. So it is $\theta \mapsto e^{2\pi i n \theta}$ for some $n \in \mathbb{Z}$. Part 2 of Theorem 4.5.8 says that these functions form an orthonormal basis of $L^2(\mathbb{R}/\mathbb{Z})$, which is the theorem of Riesz and Fischer for Fourier series. Mathlib has this basis as `fourierBasis`. For the torus $(\mathbb{R}/\mathbb{Z})^r$ the characters are $\theta \mapsto e^{2\pi i (n, \theta)}$ for $n \in \mathbb{Z}^r$, so the character group of a compact torus of dimension $r$ is a lattice $\mathbb{Z}^r$, just as for a split algebraic torus.

**Corollary 4.5.10 (compact Lie groups are linear).** Every compact Lie group $K$ has a faithful finite-dimensional representation. So $K$ is isomorphic to a closed subgroup of $U(n)$ for some $n$.

Lean: not stated yet

*Proof.* The kernels of the finite-dimensional representations are closed subgroups of $K$, hence Lie subgroups. A strictly decreasing sequence of closed subgroups of a compact Lie group is finite, because at each step either the dimension drops or the dimension stays the same and the number of connected components, which is finite by compactness, drops. So there are finitely many representations $\pi_1, \dots, \pi_m$ such that $\bigcap_i \ker \pi_i$ is the smallest kernel of a representation. By part 3 of Theorem 4.5.8, it is $\{e\}$, so $\pi = \pi_1 \oplus \dots \oplus \pi_m$ is faithful. By Proposition 4.5.4 we may take $\pi$ unitary. Its image is compact, so closed, and a continuous injective map from a compact space is a homeomorphism onto its image. $\square$

For a compact group that is not a Lie group, no finite-dimensional representation is faithful, because a closed subgroup of $GL_n(\mathbb{C})$ is a Lie group. For profinite groups, such as the Galois group of a number field, the situation is extreme: every finite-dimensional complex representation has finite image. This is the starting point for the Artin representations of Volume 3.

**Proposition 4.5.11 (no small subgroups).** There is a neighborhood $N$ of $1$ in $GL_n(\mathbb{C})$ that contains no subgroup except $\{1\}$. Consequently every continuous homomorphism $\pi$ from a profinite group $\Gamma$ to $GL_n(\mathbb{C})$ factors through a finite quotient $\Gamma / \Gamma'$ by an open normal subgroup $\Gamma'$.

Lean: `ProfiniteGrp.exist_openNormalSubgroup_sub_open_nhds_of_one`, from Mathlib, for the open normal subgroup

*Proof.* The exponential map $M_n(\mathbb{C}) \to GL_n(\mathbb{C})$ is a diffeomorphism from a ball $B_{2r} = \{ \|X\| < 2r \}$ onto an open neighborhood of $1$, for some $r > 0$. Put $N = \exp(B_r)$. Let $g \in N$ with $g \neq 1$, so $g = \exp(X)$ with $0 < \|X\| < r$. There is an integer $m \ge 1$ with $r \le \|m X\| < 2r$. Then $g^m = \exp(mX)$, and $g^m \notin N$ because $\exp$ is injective on $B_{2r}$ and $mX \notin B_r$. So no subgroup contained in $N$ contains $g$. For the second statement, $\pi^{-1}(N)$ is an open neighborhood of $e$ in $\Gamma$. A profinite group has a basis of neighborhoods of $e$ consisting of open normal subgroups, so $\pi^{-1}(N)$ contains an open normal subgroup $\Gamma'$. Then $\pi(\Gamma')$ is a subgroup contained in $N$, so it is trivial. $\square$

The statement is false for $p$-adic coefficients. For $p$ odd, the character $\mathbb{Z}_p \to \mathbb{Q}_p^\times$, $a \mapsto (1 + p)^a$, is continuous and injective, by Exercise 10. This is why the $\ell$-adic Galois representations of Volume 3 have infinite image, while the complex ones have finite image.
