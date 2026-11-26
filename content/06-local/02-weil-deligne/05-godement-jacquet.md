---
title: The standard L-factor of Godement and Jacquet
nodes: []
sources: [BH06, JL70, HT01, Hen00]
status: checked
drafted_by: writer@claude-opus-5-5
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## The standard L-factor of Godement and Jacquet

This section defines the $L$-factor and the $\varepsilon$-factor of an irreducible admissible representation $\pi$ of $GL_n(K)$, following Godement and Jacquet, "Zeta functions of simple algebras" (Lecture Notes in Math. 260, 1972). Their method generalizes Tate's thesis: one integrates a matrix coefficient of $\pi$ against a Schwartz-Bruhat function on the matrix algebra $M_n(K)$. We compute the factors of unramified, Steinberg and supercuspidal representations, and we compare them with the factors of Section 2.4. The example to keep in mind is the unramified case, where the integral is a generating series of Hecke operators. Let $G = GL_n(K)$ and $K_0 = GL_n(\mathcal{O}_K)$, as in Section 1.2.

### Zeta integrals

**Definition 2.5.1 (Schwartz-Bruhat functions).** A *Schwartz-Bruhat function* on $M_n(K)$ is a locally constant function with compact support. They form a space $\mathcal{S}(M_n(K))$. For a nontrivial character $\psi$ of $K$, the *Fourier transform* of $\Phi$ is $\hat\Phi(y) = \int_{M_n(K)} \Phi(x) \psi(\mathrm{tr}(xy)) \, dx$, where $dx$ is the self-dual Haar measure.

Lean: `Langlands.IsSchwartzBruhat`

For $\psi$ of conductor $\mathcal{O}_K$, the self-dual measure gives $M_n(\mathcal{O}_K)$ volume $1$, and the characteristic function $\Phi_0$ of $M_n(\mathcal{O}_K)$ satisfies $\hat\Phi_0 = \Phi_0$. Fourier inversion reads $\hat{\hat\Phi}(x) = \Phi(-x)$. Let $d^\times g$ be the Haar measure on $G$ with $\mathrm{vol}(K_0) = 1$. It is $c \, |\det g|^{-n} dg$ for a constant $c$.

**Definition 2.5.2 (zeta integral).** Let $(\pi, V)$ be an irreducible admissible representation of $G$. A *matrix coefficient* of $\pi$ is a function $f(g) = \lambda(\pi(g) v)$ with $v \in V$ and $\lambda \in V^\vee$. For $\Phi \in \mathcal{S}(M_n(K))$, the *zeta integral* is
$$Z(\Phi, s, f) = \int_G \Phi(g) \, f(g) \, |\det g|^{s + (n-1)/2} \, d^\times g.$$

Lean: `Langlands.gjZeta` (with `Langlands.matrixHaar` for the additive measure)

The shift $(n-1)/2$ makes the functional equation relate $s$ and $1 - s$. For $n = 1$ a matrix coefficient is a multiple of the character $\pi$, and $Z(\Phi, s, f)$ is a multiple of Tate's zeta integral of Volume 3, Section 4.3. Let $f^\vee(g) = f(g^{-1})$. It is a matrix coefficient of $\pi^\vee$, by Proposition 1.1.6.

**Theorem 2.5.3 (Godement-Jacquet).** Let $\pi$ be an irreducible admissible representation of $G$.
1. Each $Z(\Phi, s, f)$ converges absolutely for $\mathrm{Re}(s)$ large, and it is a rational function of $q^{-s}$.
2. The span of the $Z(\Phi, s, f)$ is a fractional ideal of $\mathbb{C}[q^s, q^{-s}]$ that contains $1$. It has a unique generator of the form $L(s, \pi) = P(q^{-s})^{-1}$, where $P$ is a polynomial with $P(0) = 1$.
3. There is a rational function $\gamma(s, \pi, \psi)$ of $q^{-s}$ such that $Z(\hat\Phi, 1 - s, f^\vee) = \gamma(s, \pi, \psi) \, Z(\Phi, s, f)$ for all $\Phi$ and $f$.
4. The function $\varepsilon(s, \pi, \psi) = \gamma(s, \pi, \psi) L(s, \pi) / L(1 - s, \pi^\vee)$ is a unit $c \, q^{-ks}$ of $\mathbb{C}[q^s, q^{-s}]$.

Lean: not stated yet (`Langlands.IsGJLFactor` characterizes $L(s, \pi)$ by part 2)

*Sketch of proof.* This is Theorem 3.3 of Godement and Jacquet. For $n = 2$ a complete proof is in [BH06, Chapter 6]. We give the main steps. The span is stable under multiplication by $q^{\pm s}$: with $t = \mathrm{diag}(\varpi, 1, \dots, 1)$, the change of variables $g = th$ gives $Z(\Phi(t^{-1} \cdot), s, f) = q^{-s-(n-1)/2} Z(\Phi, s, f(t \cdot))$, and $f(t \cdot)$ is again a matrix coefficient. It contains $1$: for $k$ large, let $\Phi$ be the characteristic function of $1 + \varpi^k M_n(\mathcal{O}_K)$, which is a compact open subgroup, and take $f$ invariant under it with $f(1) = 1$. Then $Z(\Phi, s, f)$ is a nonzero constant. Convergence and rationality come from the asymptotics of matrix coefficients. By the Cartan decomposition $G = K_0 \{\varpi^\mu\} K_0$, it suffices to know $f$ on the diagonal matrices $\varpi^\mu$ with $\mu$ dominant, and there $f$ is a finite sum of characters of $\mu$ times polynomials, determined by the Jacquet modules of $\pi$ (Section 1.3). For supercuspidal $\pi$ the argument is Proposition 2.5.6 below. The functional equation comes from a uniqueness statement. For generic $s$, the space of bilinear forms on $\mathcal{S}(M_n(K)) \times \mathcal{C}(\pi)$, where $\mathcal{C}(\pi)$ is the space of matrix coefficients, with the invariance of $(\Phi, f) \mapsto Z(\Phi, s, f)$ under $G \times G$ acting by left and right translation, has dimension at most $1$. Both sides of part 3 are such forms. Part 4 follows from part 3 for $\pi$ and for $\pi^\vee$, since both sides of the functional equation span the ideals of $L(1 - s, \pi^\vee)$ and $L(s, \pi)$. $\square$

**Definition 2.5.4 (standard factors).** The functions $L(s, \pi)$, $\varepsilon(s, \pi, \psi)$ and $\gamma(s, \pi, \psi)$ of Theorem 2.5.3 are the *standard $L$-factor*, *$\varepsilon$-factor* and *$\gamma$-factor* of $\pi$.

Lean: `Langlands.IsGJLFactor` (for $L(s, \pi)$)

For $n = 1$ they are Tate's factors. Exercise 10 shows that $\varepsilon(s, \pi, \psi) \varepsilon(1 - s, \pi^\vee, \psi) = \omega_\pi(-1)$, where $\omega_\pi$ is the central character. This is part 4 of Proposition 2.4.11 for $\det = \omega_\pi$.

### Three computations

**Theorem 2.5.5 (unramified representations).** Let $\pi$ be irreducible and unramified, with parameter $\{z_1, \dots, z_n\}$ as in Corollary 1.2.6. Then
$$L(s, \pi) = \prod_{i=1}^n (1 - z_i q^{-s})^{-1},$$
and $\varepsilon(s, \pi, \psi) = 1$ for $\psi$ of conductor $\mathcal{O}_K$.

Lean: not stated yet

*Proof.* Let $v_0 \in V^{K_0}$ and $\lambda_0 \in (V^\vee)^{K_0}$ with $\lambda_0(v_0) = 1$, and let $f_0(g) = \lambda_0(\pi(g) v_0)$. The set $G \cap M_n(\mathcal{O}_K)$ is the disjoint union of the sets $T_m$ of the $g \in M_n(\mathcal{O}_K)$ with $v(\det g) = m$, for $m \ge 0$. Each $T_m$ is a finite union of double cosets of $K_0$. Let $1_{T_m}$ be its characteristic function, an element of $\mathcal{H}(G, K_0)$. Then
$$Z(\Phi_0, s, f_0) = \sum_{m \ge 0} q^{-m(s + (n-1)/2)} \lambda_0\big(\pi(1_{T_m}) v_0\big) = \sum_{m \ge 0} q^{-m(s + (n-1)/2)} \, \mathcal{S}(1_{T_m})(z_1, \dots, z_n),$$
by Corollary 1.2.6. A theorem of Tamagawa says that $\mathcal{S}(1_{T_m}) = q^{m(n-1)/2} h_m$, where $h_m$ is the complete symmetric polynomial of degree $m$. For $n = 2$ this follows from Exercise 5 of Chapter 1 and the values $\mathcal{S}(T_\varpi) = q^{1/2}(X_1 + X_2)$, $\mathcal{S}(R_\varpi) = X_1 X_2$: with $X = q^{-s - 1/2}$,
$$\sum_{m \ge 0} \mathcal{S}(T_{\varpi^m}) X^m = \big(1 - q^{1/2}(X_1 + X_2) X + q X_1 X_2 X^2\big)^{-1} = \prod_{i=1}^2 (1 - X_i q^{-s})^{-1}.$$
In general $\sum_m h_m(z) Y^m = \prod_i (1 - z_i Y)^{-1}$, so $Z(\Phi_0, s, f_0) = \prod_i (1 - z_i q^{-s})^{-1}$. This shows that the ideal contains $\prod_i (1 - z_i q^{-s})^{-1}$. The opposite inclusion needs more work. One embeds $\pi$ in the unramified principal series of Section 1.3 and computes all its zeta integrals with the Iwasawa decomposition, as products of Tate integrals. This is done by Godement and Jacquet, and for $n = 2$ in [BH06, Chapter 6]. For the $\varepsilon$-factor, $\hat\Phi_0 = \Phi_0$, and $f_0^\vee$ is the spherical matrix coefficient of $\pi^\vee$, whose parameter is $\{z_i^{-1}\}$. So $Z(\hat\Phi_0, 1 - s, f_0^\vee) = \prod_i (1 - z_i^{-1} q^{s-1})^{-1} = L(1 - s, \pi^\vee)$, and $\gamma(s, \pi, \psi) = L(1 - s, \pi^\vee) / L(s, \pi)$. Hence $\varepsilon = 1$. $\square$

Compare with Section 2.4. The Weil-Deligne representation $(\chi_1 \oplus \dots \oplus \chi_n, 0)$ with $\chi_i$ unramified and $\chi_i(\Phi) = z_i$ has $L$-factor $\prod_i (1 - z_i q^{-s})^{-1}$ and $\varepsilon$-factor $1$. So the factors match for the unramified correspondence $\pi \mapsto \oplus \chi_i$.

**Proposition 2.5.6 (supercuspidal representations).** Let $\pi$ be an irreducible supercuspidal representation of $G$ with $n \ge 2$. Then every zeta integral $Z(\Phi, s, f)$ is a Laurent polynomial in $q^{-s}$, and $L(s, \pi) = 1$.

Lean: not stated yet

*Proof.* By Theorem 1.4.3 the support of $f$ is contained in $CZ$ for a compact set $C$, where $Z$ is the center of $G$. For $m \in \mathbb{Z}$ let $G_m = \{g : v(\det g) = m\}$, so that
$$Z(\Phi, s, f) = \sum_{m \in \mathbb{Z}} q^{-m(s + (n-1)/2)} c_m, \qquad c_m = \int_{G_m} \Phi(g) f(g) \, d^\times g.$$
The set $CZ \cap G_m$ is compact, since $v(\det(c \varpi^k)) = v(\det c) + nk$ bounds $k$. So each $c_m$ is finite. The entries of the elements of $\mathrm{supp}\, \Phi$ are bounded, so $v(\det g)$ is bounded below on it, and $c_m = 0$ for $m$ very negative. If $g = c \varpi^k \in CZ \cap G_m$ and $m \to \infty$, then $k \to \infty$ and $g \to 0$. Since $\Phi$ is constant near $0$, for $m$ large we get $c_m = \Phi(0) \int_{G_m} f(g) \, d^\times g$. We show that this integral is $0$. Fix $g_m \in G_m$, so that $G_m = g_m G_0$. For $\lambda' \in V^\vee$ consider $\mu(v) = \int_{G_0} \lambda'(\pi(h) v) \, dh$. The integrand has compact support, as above, so $\mu$ is a linear form on $V$. It is invariant under $G_0$, which contains $K_0$, so $\mu$ is smooth and fixed by $G_0 \supseteq SL_n(K)$. The space $(V^\vee)^{SL_n(K)}$ is stable under $G$, since $SL_n(K)$ is normal. The contragredient $\pi^\vee$ is irreducible by Proposition 1.1.6. If $(V^\vee)^{SL_n(K)}$ were nonzero, it would be $V^\vee$, and $\pi^\vee$ would factor through the abelian group $G / SL_n(K)$. By Theorem 1.1.7 it would be a character, and then $\pi$ would be a character, which is not supercuspidal by Proposition 1.4.2. So $\mu = 0$. Apply this to $\lambda' = \pi^\vee(g_m^{-1}) \lambda$ to get $\int_{G_m} f = 0$. Hence the sum is finite. The ideal contains $1$ by Theorem 2.5.3, so it is $\mathbb{C}[q^s, q^{-s}]$ and $L(s, \pi) = 1$. $\square$

This matches Example 2.4.4: an irreducible representation of $W_K$ of dimension $n \ge 2$ has $L$-factor $1$. The $\varepsilon$-factor of a supercuspidal representation is not trivial. For the depth zero representations of $GL_2$ of Example 1.4.9 it is a Gauss sum over the field with $q^2$ elements, as in Example 2.4.13. This agreement is one of the checks in the proof of the local Langlands correspondence for $GL_2$ [BH06, Chapter 8].

**Proposition 2.5.7 (the Steinberg representation).** Let $\eta$ be a character of $K^\times$ and $\psi$ of conductor $\mathcal{O}_K$. If $\eta$ is unramified, then
$$L(s, \eta \mathrm{St}) = (1 - \eta(\varpi) q^{-s-1/2})^{-1}, \qquad \varepsilon(s, \eta\mathrm{St}, \psi) = -\eta(\varpi) q^{1/2 - s}.$$
If $\eta$ is ramified, then $L(s, \eta\mathrm{St}) = 1$ and $\varepsilon(s, \eta\mathrm{St}, \psi) = \varepsilon(s, \eta |\cdot|^{1/2}, \psi) \varepsilon(s, \eta |\cdot|^{-1/2}, \psi)$.

Lean: not stated yet

*Sketch of proof.* The representation $\eta\mathrm{St}$ is a subrepresentation of $\eta|\cdot|^{1/2} \times \eta|\cdot|^{-1/2}$, with quotient $\eta \circ \det$ (Definition 1.5.3). The zeta integrals of the principal series are products of two Tate integrals, and they span the ideal of $L(s, \eta|\cdot|^{1/2}) L(s, \eta|\cdot|^{-1/2})$. The zeta integrals of the character $\eta \circ \det$ span the ideal of $L(s + 1/2, \eta) L(s - 1/2, \eta)$, and Exercise 9 computes one of them for $\eta = 1$. For unramified $\eta$ the subrepresentation loses the factor $L(s - 1/2, \eta) = L(s, \eta|\cdot|^{-1/2})$. The details, including the $\varepsilon$-factor, are in [BH06, Chapter 6]. $\square$

Compare with Example 2.4.12: the Weil-Deligne representation $\mathrm{Sp}(2) \otimes \eta|\cdot|^{-1/2}$ has the $L$-factor $L(s + 1, \eta |\cdot|^{-1/2}) = (1 - \eta(\varpi) q^{-s-1/2})^{-1}$ and the $\varepsilon$-factor $-\eta(\varpi) q^{1/2 - s}$. The representation $(\eta|\cdot|^{1/2} \oplus \eta|\cdot|^{-1/2}, 0)$, which has the same $r$, has the $L$-factor of $\eta \circ \det$. So the factors detect the operator $N$.

### The general case

**Theorem 2.5.8 (Godement-Jacquet, Jacquet).** Let $\Delta = [\rho, \rho\nu^{k-1}]$ be a segment and $L(\Delta)$ the essentially square-integrable representation of Theorem 1.6.3.
1. $L(s, L(\Delta)) = L(s, \rho\nu^{k-1})$. In particular $L(s, \mathrm{St}_k \otimes \chi) = L(s + (k - 1)/2, \chi)$ for a character $\chi$.
2. For the Langlands quotient of Theorem 1.6.5, $L(s, L(\Delta_1, \dots, \Delta_r)) = \prod_i L(s, L(\Delta_i))$, and the same holds for the $\varepsilon$-factors.

Lean: not stated yet

Godement and Jacquet treated the supercuspidal and the unramified representations. The general statement, in terms of the classification of Section 1.6, is in Jacquet, "Principal $L$-functions of the linear group" (Proc. Sympos. Pure Math. 33, part 2, 1979). On the side of $W_K$, Example 2.4.4 gives $L(s, \mathrm{Sp}(k) \otimes \sigma) = L(s + k - 1, \sigma)$. So if $\rho$ corresponds to the irreducible $\sigma$ with $L(s, \rho) = L(s, \sigma)$, then $L(\Delta)$ and $\mathrm{Sp}(k) \otimes \sigma$ have the same $L$-factor, since $L(s, \rho \nu^{k-1}) = L(s + k - 1, \rho)$.

**Remark 2.5.9 (the dictionary).** The table summarizes the matching of factors for $GL_n$. Here $\rho$ is supercuspidal and corresponds to the irreducible $\sigma$, and $\chi$ is a character.

| $GL_n(K)$ | Weil-Deligne | $L$-factor |
|---|---|---|
| $\chi$ ($n = 1$) | $(\chi, 0)$ | Tate's $L(s, \chi)$ |
| unramified, parameter $\{z_i\}$ | $\oplus \chi_i$, $\chi_i(\Phi) = z_i$ | $\prod (1 - z_i q^{-s})^{-1}$ |
| $\rho$ supercuspidal, $n \ge 2$ | $(\sigma, 0)$ | $1$ |
| $L([\rho, \rho\nu^{k-1}])$ | $\mathrm{Sp}(k) \otimes \sigma$ | $L(s, \rho \nu^{k-1})$ |
| $\eta \mathrm{St}$ | $\mathrm{Sp}(2) \otimes \eta|\cdot|^{-1/2}$ | $L(s + 1/2, \eta)$ |
| $L(\Delta_1, \dots, \Delta_r)$, $\Delta_i = [\rho_i, \rho_i \nu^{k_i - 1}]$ | $\oplus_i \mathrm{Sp}(k_i) \otimes \sigma_i$ | $\prod_i L(s, L(\Delta_i))$ |

By Theorem 1.6.5 and Theorem 2.2.8, a correspondence that matches $L(\Delta)$ with $\mathrm{Sp}(k) \otimes \sigma$ is determined by its values on supercuspidal representations, and there the $L$-factors carry no information. So the $\varepsilon$-factors are needed, and in fact the factors of pairs $\pi \times \pi'$ of Remark 1.7.7. Harris and Taylor [HT01] and Henniart [Hen00] proved that there is a unique correspondence that preserves the $L$-factors and $\varepsilon$-factors of pairs. The Lean statement `Langlands.LocalLanglandsGL` uses the factors `Langlands.IsGJLFactor` and `Langlands.WeilDeligneRep.lFactor` of this chapter, and it leaves out the $\varepsilon$-factors and the pairs. So it states the existence of a correspondence, but not its uniqueness. For $n = 2$, Godement and Jacquet show that their factors agree with those that Jacquet and Langlands defined with the Kirillov model [JL70], which Chapter 1 promised to compare.
