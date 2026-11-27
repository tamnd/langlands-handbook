---
title: The statement for GL(n)
nodes: [LG2E74SP8W]
sources: [HT01, Hen00, BH06, JL70, Kut80, Tat79]
status: checked
drafted_by: writer@claude-opus-5-5
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## The statement for GL(n)

This section states the local Langlands correspondence for $GL_n$ and the theorem of Henniart that characterizes it. The two sides are sets of isomorphism classes, and the correspondence is a family of bijections, one for each $n$, that matches the operations and the invariants of the two sides. The example to keep in mind is the Steinberg representation of the introduction: the representation $\mathrm{St}$ of $GL_2(K)$ goes to the parameter $(|\cdot|^{1/2} \oplus |\cdot|^{-1/2}, N)$ with $N \ne 0$, and the $L$-factors and $\varepsilon$-factors of the two sides agree.

### The two sides

**Definition 3.1.1 (the two sides).** Let $n \ge 1$.
1. $\mathcal{A}_n(K) = \mathrm{Irr}(GL_n(K))$ is the set of isomorphism classes of irreducible smooth representations of $GL_n(K)$, as in Definition 1.1.9. Each of them is admissible by Theorem 1.1.11. We write $\mathcal{A}^0_n(K)$ for the subset of the supercuspidal classes and $\mathcal{A}^2_n(K)$ for the subset of the essentially square integrable classes, the discrete series of Theorem 1.6.4.
2. $\mathcal{G}_n(K)$ is the set of isomorphism classes of Frobenius semisimple Weil-Deligne representations $(r, N)$ of $W_K$ of dimension $n$, as in Chapter 2. We write $\mathcal{G}^0_n(K)$ for the subset of the classes with $N = 0$ and $r$ irreducible, and $\mathcal{G}^2_n(K)$ for the subset of the indecomposable classes.

Both sides have the same operations. A character $\chi$ of $K^\times$ acts on $\mathcal{A}_n(K)$ by $\pi \mapsto \pi \otimes \chi \circ \det$ and on $\mathcal{G}_n(K)$ by $(r, N) \mapsto (r \otimes \varphi_\chi, N)$. Each side has a duality: the contragredient $\pi \mapsto \pi^\vee$ of Definition 1.1.5, and the dual $(r, N) \mapsto ({}^t r^{-1}, -{}^t N)$. Each element has a determinant character: the central character $\omega_\pi$ of Corollary 1.1.8, and $\det r$. Each pair of elements has local factors. For $\pi \in \mathcal{A}_n(K)$ and $\pi' \in \mathcal{A}_{n'}(K)$, Jacquet, Piatetski-Shapiro and Shalika defined $L(s, \pi \times \pi')$ and $\varepsilon(s, \pi \times \pi', \psi)$ by the zeta integrals of Remark 1.7.7. For $n' = 1$ and $\pi' = \chi$ these are the factors of Godement and Jacquet of $\pi \otimes \chi \circ \det$, see Chapter 2. For $\sigma \in \mathcal{G}_n(K)$ and $\sigma' \in \mathcal{G}_{n'}(K)$ the factors $L(s, \sigma \otimes \sigma')$ and $\varepsilon(s, \sigma \otimes \sigma', \psi)$ are those of Langlands and Deligne for the tensor product, see Chapter 2, [Tat79], and Deligne's paper of 1973 on the constants of the functional equations. Here $\psi$ is a fixed nontrivial character of $K$. A change of $\psi$ changes both sides by the same rule, see Volume 0, Remark 3.2.1, so the statement below does not depend on $\psi$.

The factors of pairs are needed for the uniqueness, and they are harder than the standard factors. On the automorphic side they need the Whittaker models of Section 1.7. On the Galois side the $\varepsilon$-factors of representations of dimension at least 2 need the theorem of Langlands and Deligne (Volume 3, Theorem 4.3.8), which builds them from the $\varepsilon$-factors of characters of the Weil groups of finite extensions of $K$ by induction in degree 0.

### The theorem

**Theorem 3.1.2 (the local Langlands correspondence for $GL_n$).** There is a unique family of bijections $\mathrm{rec}_n : \mathcal{A}_n(K) \to \mathcal{G}_n(K)$, for $n \ge 1$, with the following properties.
1. $\mathrm{rec}_1(\chi) = \chi \circ \mathrm{art}_K^{-1}$ for each character $\chi$ of $K^\times = GL_1(K)$.
2. $\det \mathrm{rec}_n(\pi) = \mathrm{rec}_1(\omega_\pi)$.
3. $\mathrm{rec}_n(\pi \otimes \chi \circ \det) = \mathrm{rec}_n(\pi) \otimes \mathrm{rec}_1(\chi)$.
4. $\mathrm{rec}_n(\pi^\vee) = \mathrm{rec}_n(\pi)^\vee$.
5. $L(s, \pi \times \pi') = L(s, \mathrm{rec}_n(\pi) \otimes \mathrm{rec}_{n'}(\pi'))$ and $\varepsilon(s, \pi \times \pi', \psi) = \varepsilon(s, \mathrm{rec}_n(\pi) \otimes \mathrm{rec}_{n'}(\pi'), \psi)$ for all $\pi \in \mathcal{A}_n(K)$ and $\pi' \in \mathcal{A}_{n'}(K)$.

Also $\mathrm{rec}_n(\mathcal{A}^0_n(K)) = \mathcal{G}^0_n(K)$ and $\mathrm{rec}_n(\mathcal{A}^2_n(K)) = \mathcal{G}^2_n(K)$, and the conductor of $\pi$ is the Artin conductor of $\mathrm{rec}_n(\pi)$.

Node: LG2E74SP8W · Lean: `Langlands.LocalLanglandsGL`

The uniqueness is the theorem of Henniart of 1993 on the $\varepsilon$-factors of pairs, Theorem 3.1.4 below. The existence for $K$ of characteristic 0 is the theorem of Harris and Taylor [HT01]. They construct $\mathrm{rec}_n$ in the cohomology of some simple Shimura varieties and the Lubin-Tate tower, and Volume 10 explains their proof. Henniart [Hen00] gave a shorter proof of the existence. It combines global results of Harris on Shimura varieties with Henniart's numerical correspondence, a count of the two sides with a fixed conductor. Scholze gave a third proof in 2013, with the cohomology of Shimura varieties and a characterization of the correspondence by identities between traces. For $K$ of positive characteristic the theorem is due to Laumon, Rapoport and Stuhler (1993), from the cohomology of the moduli spaces of $\mathcal{D}$-elliptic sheaves. For $n = 1$ the theorem is local class field theory, see Section 3.2. For $n = 2$ it is due to Kutzko [Kut80] and is treated in [BH06], see Section 3.3. Condition 1 fixes the normalization of the whole family: with the arithmetic normalization of Volume 3, Remark 2.3.4, the family $\pi \mapsto \mathrm{rec}_n(\pi^\vee)$ satisfies the conditions on central characters, twists and duals, and for $n = 1$ it matches the $L$-factors once these are defined with the arithmetic Frobenius, see Exercise 1.

**Remark 3.1.3 (the conditions are consistent).** The conditions are compatible with each other on the parts that can be checked by hand. Condition 2 for $n = 1$ is condition 1, because the central character of $\chi$ is $\chi$. Condition 5 for $\pi' = 1$ and condition 3 give the factors of all the twists by characters. By condition 4 the factors of $\pi^\vee$ are those of $\mathrm{rec}_n(\pi)^\vee$. So the local functional equations on the two sides, which relate the factors of $\pi$ at $s$ to those of $\pi^\vee$ at $1 - s$, have the same shape. The two sides change in the same way under a change of $\psi$: on the automorphic side by Volume 0, Remark 3.2.1, and on the Galois side by the rule $\varepsilon(s, \sigma, \psi_a) = \det \sigma(a) |a|^{n(s - 1/2)} \varepsilon(s, \sigma, \psi)$, which agrees with it by condition 2.

### Henniart's characterization

A family that satisfies conditions 1 to 5 is unique. The proof rests on a converse theorem: a supercuspidal representation is determined by the factors of its twists by representations of smaller groups. For $GL_2$ this is the converse theorem of Jacquet and Langlands, which uses only the twists by characters, see [BH06], Chapter 6.

**Theorem 3.1.4 (Henniart's local converse theorem).** Let $n \ge 2$, and let $\pi$ and $\pi'$ be irreducible generic representations of $GL_n(K)$ with the same central character. Suppose that $\gamma(s, \pi \times \tau, \psi) = \gamma(s, \pi' \times \tau, \psi)$ for each $r$ with $1 \le r \le n - 1$ and each irreducible supercuspidal representation $\tau$ of $GL_r(K)$, where $\gamma(s, \pi \times \tau, \psi) = \varepsilon(s, \pi \times \tau, \psi) L(1 - s, \pi^\vee \times \tau^\vee) / L(s, \pi \times \tau)$. Then $\pi \cong \pi'$.

Lean: not stated yet

The proof is in Henniart's paper "Caractérisation de la correspondance de Langlands locale par les facteurs $\varepsilon$ de paires" (Invent. Math. 113, 1993). It works with the restrictions of the Whittaker functions of $\pi$ and $\pi'$ to the mirabolic subgroup, as in the Kirillov model of Theorem 1.7.5 for $n = 2$, and uses the functional equations of the zeta integrals of Remark 1.7.7 for all $\tau$ to show that the two Whittaker models agree. Later work of Chen showed that the twists with $r \le n - 2$ suffice, and Chai, and Jacquet and Liu, showed that the twists with $r \le n/2$ suffice. For $n = 2$ the twists by characters suffice, and this is the classical converse theorem of [JL70].

**Corollary 3.1.5 (uniqueness).** Let $(\mathrm{rec}_n)$ and $(\mathrm{rec}'_n)$ be two families of bijections that satisfy conditions 1 to 5 of Theorem 3.1.2. Then $\mathrm{rec}_n = \mathrm{rec}'_n$ for each $n$.

Lean: not stated for $n \ge 2$. The case of the families $(\mathrm{rec}_0, \mathrm{rec}_1)$ is `Langlands.Fidelity.recFamily_unique`, see Proposition 3.1.29.

*Proof.* We argue by induction on $n$. For $n = 1$ both families are given by condition 1. Let $n \ge 2$ and suppose that $\mathrm{rec}_m = \mathrm{rec}'_m$ for $m < n$. Let $\sigma \in \mathcal{G}_n(K)$, and let $\pi = \mathrm{rec}_n^{-1}(\sigma)$ and $\pi' = \mathrm{rec}_n'^{-1}(\sigma)$. By condition 2 both have the central character $\det \sigma \circ \mathrm{art}_K$. For each $r < n$ and each $\tau \in \mathcal{A}_r(K)$, condition 5 and the induction hypothesis give
$$\varepsilon(s, \pi \times \tau, \psi) = \varepsilon(s, \sigma \otimes \mathrm{rec}_r(\tau), \psi) = \varepsilon(s, \sigma \otimes \mathrm{rec}'_r(\tau), \psi) = \varepsilon(s, \pi' \times \tau, \psi),$$
and in the same way the $L$-factors of $\pi \times \tau$ and $\pi' \times \tau$ agree, and also those of $\pi^\vee \times \tau^\vee$ and $\pi'^\vee \times \tau^\vee$, by condition 4. So $\pi$ and $\pi'$ have the same $\gamma$-factors of pairs with all $\tau$ of smaller rank. If $\pi$ and $\pi'$ are generic, Theorem 3.1.4 gives $\pi \cong \pi'$. In general one uses the Langlands classification of Theorem 1.6.5. Each $\pi$ is the Langlands quotient $L(\Delta_1, \ldots, \Delta_k)$ of a standard module $\delta_1 \times \cdots \times \delta_k$ with $\delta_i = L(\Delta_i)$ built from discrete series $\delta_i$ of smaller groups, and the factors of pairs are multiplicative in the standard module. The $L$-factors $L(s, \pi \times \tau)$ for all $\tau$ then determine the multiset of the $L$-factors of the pieces, and one shows that $\mathrm{rec}_n(\pi)$ and $\mathrm{rec}'_n(\pi)$ are the direct sums of the images of the $\delta_i$. This reduces the claim to the discrete series, and by Theorem 1.6.4 to the supercuspidal representations, which are generic by Theorem 1.7.6. $\square$

The proof shows what the $\varepsilon$-factors do. Let $n \ge 2$. The standard $L$-factor of each $\sigma \in \mathcal{G}^0_n(K)$ is 1, because $V^{I_K}$ is stable under $W_K$ and is not all of $V$. The Godement-Jacquet factor of each supercuspidal $\pi$ is also 1. So condition 5 for the standard $L$-factors gives no information on the supercuspidal part. The $L$-factors of pairs give a little: for supercuspidal $\pi$ and $\pi'$, $L(s, \pi \times \pi')$ has a pole exactly when $\pi'$ is an unramified twist of $\pi^\vee$, and the same holds on the Galois side. The $\varepsilon$-factors of pairs carry the rest.

### The reduction to the supercuspidal representations

The correspondence respects the classification of Bernstein and Zelevinsky of Section 1.6. On the Galois side the classification is elementary. For a character $\chi$ of $W_K$ and $a \ge 1$ let $\mathrm{Sp}(a)$ be the Weil-Deligne representation on $\mathbb{C}^a$ with basis $e_0, \ldots, e_{a-1}$, with $r(w) e_i = |w|^{(a-1)/2 - i} e_i$ and $N e_i = e_{i-1}$, $N e_0 = 0$. The relation $r(w) N r(w)^{-1} = |w| N$ holds, because $N$ lowers the index by one and raises the exponent by one.

**Proposition 3.1.6 (the Galois side).** Each element of $\mathcal{G}_n(K)$ is a direct sum of indecomposable ones, unique up to order. Each indecomposable element is $\mathrm{Sp}(a) \otimes \rho$ for a unique $a \ge 1$ and a unique irreducible representation $\rho$ of $W_K$, and the dimension is $a \dim \rho$.

Lean: not stated yet

*Proof.* We give the main steps. Let $(r, N)$ be Frobenius semisimple. The kernel of $N$ is stable under $r$, because $r(w) N v = |w| N r(w) v$. By the theorem of Jacobson and Morozov, the pair is equivalent to a representation of $W_K \times SL_2(\mathbb{C})$ whose restriction to $W_K$ is semisimple, with $N$ the image of the standard nilpotent element and $r(w)$ twisted by $\mathrm{diag}(|w|^{1/2}, |w|^{-1/2})$. A representation of $W_K \times SL_2(\mathbb{C})$ with semisimple restriction to $W_K$ is a sum of $\rho \boxtimes \mathrm{Sym}^{a-1}$ with $\rho$ irreducible, and $\rho \boxtimes \mathrm{Sym}^{a-1}$ corresponds to $\mathrm{Sp}(a) \otimes \rho$. The unique decomposition follows from the theorem of Krull and Schmidt for the semisimple category of these representations. $\square$

The automorphic side has the same shape. By Theorem 1.6.4 each discrete series representation of $GL_n(K)$ is the unique irreducible quotient $L(\Delta)$ of the induced representation $\rho \times \rho\nu \times \cdots \times \rho\nu^{a-1}$ of a segment $\Delta = [\rho, \rho \nu^{a-1}]$, with $\rho$ supercuspidal of $GL_m(K)$, $n = am$ and $\nu = |\det|$. The correspondence sends this discrete series representation to $\mathrm{Sp}(a) \otimes \mathrm{rec}_m(\rho \nu^{(a-1)/2})$. With the Langlands classification of Theorem 1.6.5, the whole map is then determined by its restriction to the supercuspidal representations:
$$\mathrm{rec}_n(L(\Delta_1, \ldots, \Delta_k)) = \bigoplus_{i=1}^k \mathrm{rec}_{n_i}(L(\Delta_i)).$$
The theorem of Bernstein and Zelevinsky is the automorphic form of Proposition 3.1.6. This reduction is in [HT01], Introduction, and it is a consequence of conditions 1 to 5 by the argument of Corollary 3.1.5. Conversely, if a family of bijections $\mathcal{A}^0_m(K) \to \mathcal{G}^0_m(K)$ for $m \le n$ satisfies conditions 1 to 5 on the supercuspidal representations, then the formula above extends it to a family on all of $\mathcal{A}_m(K)$ that satisfies conditions 1 to 5. The case $n = 2$ of this extension is worked out in Section 3.3.

**Example 3.1.7 (the parameter of the Steinberg representation of $GL_n$).** The Steinberg representation $\mathrm{St}_n$ of $GL_n(K)$ is the unique irreducible quotient of the segment $[\nu^{(1-n)/2}, \nu^{(n-1)/2}]$ of characters of $GL_1(K)$. Its parameter is $\mathrm{Sp}(n)$. Then $(\ker N)^{I_K}$ is the line of $e_0$, on which $\Phi$ acts by $|\Phi|^{(n-1)/2} = q^{-(n-1)/2}$. So
$$L(s, \mathrm{St}_n) = (1 - q^{-s - (n-1)/2})^{-1},$$
which is the Godement-Jacquet factor of $\mathrm{St}_n$. The trivial representation of $GL_n(K)$ is the Langlands quotient of the same induced representation in the opposite order. Its parameter is $\bigoplus_{i=0}^{n-1} |\cdot|^{(n-1)/2 - i}$ with $N = 0$, and its $L$-factor is $\prod_{i=0}^{n-1} (1 - q^{-s - (n-1)/2 + i})^{-1}$.

**Example 3.1.8 (unramified representations).** Let $\pi$ be an irreducible unramified representation of $GL_n(K)$. By Corollary 1.2.6 and Theorem 1.2.5 it is the unramified constituent of a principal series $\chi_1 \times \cdots \times \chi_n$ with $\chi_i$ unramified, and its Satake parameter is the conjugacy class of $\mathrm{diag}(\chi_1(\varpi), \ldots, \chi_n(\varpi))$. In the unitary normalization of Volume 0, Section 3.2, $\mathrm{rec}_n(\pi)$ is the unramified representation $r = \chi_1 \oplus \cdots \oplus \chi_n$ with $N = 0$, so $r(\Phi)$ has the eigenvalues $\chi_i(\varpi)$. The $L$-factor is $\prod_i (1 - \chi_i(\varpi) q^{-s})^{-1}$. So on the unramified representations the correspondence is the Satake isomorphism, read through the geometric Frobenius.

### What the Lean statement leaves out

**Remark 3.1.9 (the Lean statement `LocalLanglandsGL`).** The proposition `Langlands.LocalLanglandsGL n` says the following. For each nonarchimedean local field $K$ and each topological isomorphism $\mathrm{art} : K^\times \to W_K^{ab}$ with the properties of `Langlands.IsLocalArtinMap` (uniformizers go to geometric Frobenius elements, and the norm groups are the kernels on the finite abelian extensions), there are bijections $\mathrm{rec}_m : \mathrm{Irr}(GL_m(K)) \to \mathcal{G}_m(K)$ for $m \le n$ with the properties of `Langlands.IsLanglandsFamily`. These are condition 1, and for each $m$ the conditions of `Langlands.IsLanglandsMap`: condition 2, condition 3, condition 4, and condition 5 for $\pi' = 1$, in the form that the $L$-factor of the Weil-Deligne representation is the Godement-Jacquet factor of `Langlands.IsGJLFactor`. The statement leaves out the following.
1. The $\varepsilon$-factors, for all $n'$, including $n' = 1$.
2. The $L$-factors of pairs with $n' \ge 2$. With condition 3, the statement does give the $L$-factors of the twists by characters.
3. The uniqueness. The statement is an existence statement, and for $n \ge 2$ its conditions do not determine the family. By the remark after Corollary 3.1.5 the conditions say nothing on the supercuspidal part beyond the central characters, the twists and the duality.
4. The links between different $m$, such as the compatibility with parabolic induction and the description of the discrete series, and the statements $\mathrm{rec}_n(\mathcal{A}^0_n) = \mathcal{G}^0_n$ and $\mathrm{rec}_n(\mathcal{A}^2_n) = \mathcal{G}^2_n$ and on conductors.

The statement holds for all $K$, of any characteristic. The Artin map is a hypothesis and not a construction, but `Langlands.LocalReciprocityGL1` of Section 3.2 shows that exactly one such map exists. The theorem `Langlands.charRep_hasCentralChar` shows that the central character of the representation $\chi$ of $GL_1(K)$ is $\chi$, so for $m = 1$ condition 2 is condition 1. For $n = 1$ the file `Langlands/Local/GL1.lean` constructs the family $(\mathrm{rec}_0, \mathrm{rec}_1)$ and the file `Langlands/Local/GL1LFactor.lean` proves `LocalLanglandsGL 1` with no hypothesis as `Langlands.LocalGL1.localLanglandsGL_one`, see Theorem 3.2.14.

The rest of this section treats the stronger Lean statement `Langlands.LocalLanglandsGLFull`, which adds the $\varepsilon$-factors and the factors of pairs to `LocalLanglandsGL`, see Definition 3.1.21.

### Factors of pairs

We now define the factors of pairs of Theorem 3.1.2, condition 5, for generic representations, in the form of the Lean file `Langlands/Local/LanglandsFamilyPairs.lean`. Fix a nontrivial character $\psi$ of $K$, and let $N_n$ be the group of upper triangular unipotent matrices in $GL_n(K)$, with the character $\psi_N(u) = \psi(u_{12} + u_{23} + \dots + u_{n-1, n})$. Whittaker functionals, generic representations and the Whittaker model $\mathcal{W}(\pi, \psi)$ are as in Definition 1.7.1, and $\mathcal{W}(\pi, \psi)$ is the space of the functions $W(g) = \lambda(\pi(g) v)$. Let $w_n$ be the antidiagonal matrix with entries $1$, let $w_{n, m} = \mathrm{diag}(1_m, w_{n-m})$ for $m < n$, and let $e_n = (0, \dots, 0, 1) \in K^n$. For a function $W$ on $GL_n(K)$ put $\tilde W(g) = W(w_n \, {}^t g^{-1})$. If $W \in \mathcal{W}(\pi, \psi)$, then $\tilde W \in \mathcal{W}(\tilde \pi, \psi^{-1})$. For a Schwartz-Bruhat function $\Phi$ on $K^n$ put $\hat \Phi(y) = \int_{K^n} \Phi(x) \psi(x_1 y_1 + \dots + x_n y_n) \, dx$.

**Definition 3.1.10 (the zeta integrals of Jacquet, Piatetski-Shapiro and Shalika).** Let $\pi$ and $\pi'$ be smooth representations of $GL_n(K)$ and $GL_m(K)$, and let $W \in \mathcal{W}(\pi, \psi)$ and $W' \in \mathcal{W}(\pi', \psi^{-1})$.
1. If $m < n$ and $0 \le j < n - m$, then
$$\Psi(s, W, W'; j) = \int_{N_m \backslash GL_m(K)} \int_{M_{j \times m}(K)} W\begin{pmatrix} g & 0 & 0 \\ x & 1_j & 0 \\ 0 & 0 & 1_{n - m - j} \end{pmatrix} W'(g) \, |\det g|^{s - (n - m)/2} \, dx \, dg.$$
2. If $m = n$ and $\Phi$ is a Schwartz-Bruhat function on $K^n$, then
$$\Psi(s, W, W', \Phi) = \int_{N_n \backslash GL_n(K)} W(g) W'(g) \Phi(e_n g) |\det g|^s \, dg.$$
3. The *zeta integrals* of $(\pi, \pi', \psi)$ are the functions $\Psi(s, W, W'; 0)$ if $m < n$ and $\Psi(s, W, W', \Phi)$ if $m = n$. The *pairs of the functional equation* are the pairs $\big(\Psi(s, W, W'; j), \Psi(s, \pi(w_{n,m}) \tilde W, \tilde W'; n - m - 1 - j)\big)$ for $m < n$ and $0 \le j < n - m$, and the pairs $\big(\Psi(s, W, W', \Phi), \Psi(s, \tilde W, \tilde W', \hat \Phi)\big)$ for $m = n$.

Lean: `Langlands.IsUpperUnipotent`, `Langlands.unipChar`, `Langlands.IsWhittakerFunctional`, `Langlands.IsGeneric`, `Langlands.whittakerModel`, `Langlands.rsZeta`, `Langlands.rsZetaPhi`, `Langlands.rsZetaSet`, `Langlands.rsFEPairs`

The measure on $N_m \backslash GL_m(K)$ is the right invariant one. The products $N_m \bar N_m T_m$, with $\bar N_m$ the lower unipotent group and $T_m$ the diagonal torus, form an open subset of $GL_m(K)$ with a complement of measure $0$. In the coordinates $g = \bar u t$ the invariant measure is $d\bar u \, d^\times t$, with $d^\times t = \prod_i |t_i|^{-1} dt_i$, because right translation by $t_0$ fixes $\bar u$ and right translation by $\bar u_0$ sends $\bar u t$ to $\bar u (t \bar u_0 t^{-1}) t$. This is the Lean integral `Langlands.quotIntegral`. In Lean a function $W$ on $GL_n(K)$ is extended by $0$ to $M_n(K)$ by `Langlands.extGL`, and the matrices of part 1 are `Langlands.embedMat`.

Write $X = q^{-s}$. The following definition puts the statement "the zeta integrals span the fractional ideal $L(s) \mathbb{C}[X, X^{-1}]$" in a form that needs no analytic continuation. It is the form of `Langlands.IsGJLFactor` of Section 2.5.

**Definition 3.1.11 (generator, $L$-factor and $\varepsilon$-factor of pairs).** Let $Z$ be a set of functions of $s \in \mathbb{C}$. A function $L$ *generates* $Z$ if the following hold.
1. $L(s) = P(X)^{-1}$ for a polynomial $P$ with $P(0) = 1$.
2. For each $f \in Z$ there are a polynomial $A$, an integer $k \ge 0$ and $s_0 \in \mathbb{R}$ with $f(s) = A(X) X^{-k} L(s)$ for $\mathrm{Re}(s) > s_0$.
3. There are $f_1, \dots, f_r \in Z$, polynomials $A_1, \dots, A_r$, $k \ge 0$ and $s_0$ with $L(s) = \sum_i A_i(X) X^{-k} f_i(s)$ for $\mathrm{Re}(s) > s_0$.

A function $L$ is an *$L$-factor of pairs* for $(\pi, \pi', \psi)$ if it generates the zeta integrals of Definition 3.1.10. Let $\omega'$ be the central character of $\pi'$. A function $\varepsilon$ is an *$\varepsilon$-factor of pairs* for $(\pi, \pi', \psi)$ if $\varepsilon(s) = c X^k$ with $c \ne 0$ and $k \in \mathbb{Z}$, and there are $L$-factors of pairs $L$ for $(\pi, \pi', \psi)$ and $\tilde L$ for $(\tilde \pi, \tilde \pi', \psi^{-1})$ with the following property. For each pair $(\Psi, \Psi^\sim)$ of the functional equation there are $A, A', k, k'$ with $\Psi(s) = A(X) X^{-k} L(s)$ and $\Psi^\sim(s) = A'(X) X^{-k'} \tilde L(s)$ for $\mathrm{Re}(s)$ large, and
$$A'(q^{s - 1}) \, q^{(1 - s) k'} = \omega'(-1)^{n - 1} \varepsilon(s) \, A(q^{-s}) \, q^{s k} \quad \text{for all } s \in \mathbb{C}.$$

Lean: `Langlands.IsZetaGenerator`, `Langlands.IsRSLFactor`, `Langlands.IsMonomialFactor`, `Langlands.IsRSEpsilonFactor`

The last identity is the functional equation $\Psi^\sim(1 - s) / \tilde L(1 - s) = \omega'(-1)^{n-1} \varepsilon(s) \Psi(s) / L(s)$ after the analytic continuation. Both sides are Laurent polynomials in $q^{-s}$, so the identity makes sense for all $s$, even where the integrals do not converge.

**Proposition 3.1.12 (the generator is unique).** Let $L$ and $L'$ generate the same set $Z$. Then $L = L'$.

Lean: `Langlands.IsZetaGenerator.unique`, with `Langlands.IsZetaGenerator.exists_ratio` and `Langlands.eq_of_eval_qpow`

*Proof.* Write $L = P(X)^{-1}$ and $L' = P'(X)^{-1}$. By condition 3 for $L'$, $L'$ is a finite sum $\sum_i A_i(X) X^{-k} f_i$ with $f_i \in Z$. By condition 2 for $L$, each $f_i$ is $B_i(X) X^{-k_i} L$ for $\mathrm{Re}(s)$ large. So there are a polynomial $R$ and $N \ge 0$ with $L' = R(X) X^{-N} L$ for $\mathrm{Re}(s) > s_0$, that is, $X^N P(X) = R(X) P'(X)$ for these $s$. The values $q^{-s}$ for real $s > s_0$ form an infinite set, so $X^N P = R P'$ in $\mathbb{C}[X]$. Since $P'(0) = 1$, the polynomial $P'$ is prime to $X^N$, so $P'$ divides $P$. In the same way $P$ divides $P'$. Both have constant term $1$, so $P = P'$. $\square$

So $L(s, \pi \times \pi')$ is well defined when a generator exists. The $\varepsilon$-factor of pairs is then unique too. Take a pair $(\Psi, \Psi^\sim)$ with $A \ne 0$. Such a pair exists by condition 3. Two $\varepsilon$-factors agree at each $s$ with $A(q^{-s}) \ne 0$, and they are entire, so they are equal. The next theorem is the theory of Jacquet, Piatetski-Shapiro and Shalika, in their paper "Rankin-Selberg convolutions", Amer. J. Math. 105 (1983). A survey with proofs of the main steps is in the lectures of Cogdell on $L$-functions and converse theorems for $GL_n$ (2004).

**Theorem 3.1.13 (Jacquet, Piatetski-Shapiro, Shalika).** Let $\pi$ and $\pi'$ be irreducible generic representations of $GL_n(K)$ and $GL_m(K)$ with $1 \le m \le n$, and let $\psi$ be nontrivial.
1. The zeta integrals converge absolutely for $\mathrm{Re}(s)$ large. They extend to rational functions of $q^{-s}$, and they have a generator $L(s, \pi \times \pi')$.
2. There is an $\varepsilon$-factor of pairs $\varepsilon(s, \pi \times \pi', \psi)$. For $m < n$ the identity of Definition 3.1.11 holds for each $j$ with $0 \le j < n - m$.
3. If $\pi$ and $\pi'$ are unramified and $\psi$ has conductor $\mathcal{O}_K$, with Satake parameters $\{\alpha_i\}$ and $\{\beta_j\}$, then $L(s, \pi \times \pi') = \prod_{i, j} (1 - \alpha_i \beta_j q^{-s})^{-1}$ and $\varepsilon(s, \pi \times \pi', \psi) = 1$.

Lean: not stated. The Lean project has the conditions of Definition 3.1.11 as predicates, but it does not prove that an $L$-factor or an $\varepsilon$-factor of pairs exists for $n \ge 2$.

For $n = m = 1$ the theorem is Tate's thesis, see Proposition 3.1.24 and Theorem 3.1.25 below. For $m = 1$ and $\pi'$ trivial, the factors are those of Godement and Jacquet of Section 2.5 when $\pi$ is generic. The factors of pairs extend to all irreducible representations through the Langlands classification and the results of Bernstein and Zelevinsky, as in Remark 1.7.7.

**Remark 3.1.14 (Lean).** The file `Langlands/Local/LanglandsFamilyPairs.lean` has Definitions 3.1.10 and 3.1.11, and the file `Langlands/Local/LanglandsFamilyPairsEps.lean` has Proposition 3.1.12. The following is not in Lean. Theorem 3.1.13 is not stated. The zeta integrals are Bochner integrals. A Bochner integral is $0$ when the integrand is not integrable, so the definitions give a value for each $s$, and only the identities for $\mathrm{Re}(s)$ large carry information. The convergence of the integrals for $\mathrm{Re}(s)$ large is not stated. The Whittaker model is defined for each smooth representation, but the uniqueness of Theorem 1.7.2 is not in Lean. The definitions apply only to generic representations, and the extension to the other representations is not formalized. The uniqueness of the $\varepsilon$-factor of pairs is not stated.

### Deligne's $\varepsilon$-factor as a parameter

Condition 5 of Theorem 3.1.2 compares the factors of pairs with factors of the tensor product $\mathrm{rec}_n(\pi) \otimes \mathrm{rec}_m(\pi')$. So we need the tensor product of Weil-Deligne representations and an $\varepsilon$-factor on the Galois side.

**Definition 3.1.15 (tensor product, and the representation $(r, 0)$).** Let $\rho = (r, N)$ and $\rho' = (r', N')$ be Weil-Deligne representations of dimensions $m$ and $m'$. Their *tensor product* is $\rho \otimes \rho' = (r \otimes r', N \otimes 1 + 1 \otimes N')$, of dimension $m m'$. Put $\rho^0 = (r, 0)$.

Lean: `Langlands.WeilDeligneRep.tensor`, `Langlands.WeilDeligneRep.forgetN`, with `Langlands.kronMat` for the Kronecker product of matrices

**Lemma 3.1.16 (the tensor product is a Weil-Deligne representation).** In Definition 3.1.15, $N \otimes 1 + 1 \otimes N'$ is nilpotent, $r(w) \otimes r'(w)$ is semisimple for each $w \in W_K$, the kernel of $r \otimes r'$ is open, and $(r \otimes r')(w) (N \otimes 1 + 1 \otimes N') (r \otimes r')(w)^{-1} = \|w\| (N \otimes 1 + 1 \otimes N')$.

Lean: `Langlands.WeilDeligneRep.tensor`, with `Langlands.isSemisimple_kronMat` and `Langlands.kronMat_mul_comm`

*Proof.* The matrices $N \otimes 1$ and $1 \otimes N'$ commute, since both products are $N \otimes N'$. Each one is nilpotent, so their sum is nilpotent by the binomial formula (Exercise 15). The matrices $r(w)$ and $r'(w)$ are diagonalizable over $\mathbb{C}$. If $r(w) e_i = a_i e_i$ and $r'(w) f_j = b_j f_j$ for bases $(e_i)$ and $(f_j)$, then $r(w) \otimes r'(w)$ has the eigenbasis $(e_i \otimes f_j)$. The kernel of $r \otimes r'$ contains $\ker r \cap \ker r'$, which is open. Finally $(r(w) \otimes r'(w))(N \otimes 1)(r(w)^{-1} \otimes r'(w)^{-1}) = r(w) N r(w)^{-1} \otimes 1 = \|w\| N \otimes 1$, and the same holds for $1 \otimes N'$. $\square$

Let $V^I$ be the space of the inertia invariants of $\rho = (r, N)$, and let $V^I_N = V^I \cap \ker N$. The relation $r(w) N r(w)^{-1} = \|w\| N$ shows that $V^I_N$ is stable under a Frobenius element $\Phi$. The $L$-factor of $\rho$ is $\det(1 - q^{-s} \Phi \mid V^I_N)^{-1}$, as in Section 2.4. For a character $\chi$ of $K^\times$, a Haar measure $\mu$ on $K$, a nontrivial $\psi$ and a function $e$ of $s$, we say that *$e$ is the Tate factor of $(\chi, \mu, \psi)$* if for each Schwartz-Bruhat function $\varphi$ on $K$ and each $s$ with $|\chi(\varpi) q^{-s}| < 1$ and $|\chi(\varpi)^{-1} q^{s - 1}| < 1$,
$$Z(\hat \varphi, \chi^{-1}, 1 - s) \, L(1 - s, \chi^{-1})^{-1} = e(s) \, Z(\varphi, \chi, s) \, L(s, \chi)^{-1}.$$
Here $Z$ is the additive zeta integral of Section 3.2 and $\hat \varphi$ is the Fourier transform for $\mu$ and $\psi$. The condition on $s$ defines a vertical strip of width $1$. By Tate's local functional equation, Tate's $\varepsilon(s, \chi, \psi)$ for the measure $\mu$ is the Tate factor of $(\chi, \mu, \psi)$.

**Definition 3.1.17 (Galois $\varepsilon$-factors in the sense of Lean).** A *Galois $\varepsilon$-function* assigns a number $\varepsilon(s, \rho, \psi, \mu)$ to each measure $\mu$ on $K$, each Weil-Deligne representation $\rho$, each additive character $\psi$ and each $s \in \mathbb{C}$. It *satisfies the conditions of Deligne* if the following hold.
1. (*Isomorphism.*) $\varepsilon(s, \rho, \psi, \mu)$ depends only on the isomorphism class of $\rho$.
2. (*Monomial.*) For fixed $\mu, \rho, \psi$ there are $c \ne 0$ and $k \in \mathbb{Z}$ with $\varepsilon(s, \rho, \psi, \mu) = c q^{-ks}$ for all $s$.
3. (*Dimension one.*) For each Haar measure $\mu$, each $\psi$ with a conductor exponent and each $\rho$ of dimension $1$, the function $\varepsilon(\cdot, \rho, \psi, \mu)$ is the Tate factor of $(\chi_\rho, \mu, \psi)$, where $\chi_\rho = \det r \circ \mathrm{art}_K$.
4. (*Monodromy.*) For each $\rho$, $\varepsilon(s, \rho, \psi, \mu) \det(-q^{-s} \Phi \mid V^I_N) = \varepsilon(s, \rho^0, \psi, \mu) \det(-q^{-s} \Phi \mid V^I)$.

Lean: `Langlands.WDEpsilonFn`, `Langlands.IsTateEpsilon`, `Langlands.IsWDEpsilon`

Here $\psi$ has *conductor exponent* $k$ if $\psi$ is trivial on $\varpi^{-k} \mathcal{O}_K$ and not on $\varpi^{-k-1} \mathcal{O}_K$. This is `Langlands.LocalGL1.IsConductor`. The space $V^I$ of $\rho^0$ is the same as for $\rho$, and since the monodromy of $\rho^0$ is $0$, its space $V^I_N$ is all of $V^I$.

**Proposition 3.1.18 (condition 4 is Deligne's formula).** Let $\varepsilon$ be a Galois $\varepsilon$-function. Then condition 4 of Definition 3.1.17 holds if and only if, for each $\rho = (r, N)$,
$$\varepsilon(s, \rho, \psi, \mu) = \varepsilon(s, \rho^0, \psi, \mu) \, \det\big(-q^{-s} \Phi \mid V^I / V^I_N\big).$$
So if $\varepsilon(s, \rho^0, \psi, \mu)$ is the $\varepsilon$-factor $\varepsilon(s, r, \psi)$ of Theorem 2.4.9 for the measure $\mu$, then $\varepsilon(s, \rho, \psi, \mu)$ is the $\varepsilon$-factor of Definition 2.4.10.

Lean: the condition `monodromy` of `Langlands.IsWDEpsilon`. The equivalence is not stated in Lean.

*Proof.* The spaces $V^I_N \subset V^I$ are stable under $\Phi$, so the determinant of $-q^{-s} \Phi$ is multiplicative in the exact sequence $0 \to V^I_N \to V^I \to V^I / V^I_N \to 0$:
$$\det(-q^{-s} \Phi \mid V^I) = \det(-q^{-s} \Phi \mid V^I_N) \, \det(-q^{-s} \Phi \mid V^I / V^I_N).$$
The operator $-q^{-s} \Phi$ is invertible, so $\det(-q^{-s} \Phi \mid V^I_N) \ne 0$. Divide condition 4 by it. $\square$

The determinant $\det(-q^{-s} \Phi \mid V^I_N)$ is $(-1)^d \det(\Phi \mid V^I_N) q^{-ds}$ with $d = \dim V^I_N$. This is `Langlands.Fidelity.detFrob_eq`, for the function `Langlands.Fidelity.detFrob`. So the correction factor is a monomial in $q^{-s}$ of degree $\dim V^I - \dim V^I_N$.

**Remark 3.1.19 (what the conditions of Deligne leave out).** Theorem 2.4.9 characterizes $\varepsilon(s, r, \psi)$ by three properties: additivity, the case of dimension $1$, and inductivity in degree $0$. Definition 3.1.17 has only the second one. The Lean structure `Langlands.IsWDEpsilonAdditive` adds the additivity $\varepsilon(\rho \oplus \rho') = \varepsilon(\rho) \varepsilon(\rho')$ for the direct sum `Langlands.WeilDeligneRep.directSum`, but `LocalLanglandsGLFull` does not use it. The inductivity is not in Lean, because the induction of Weil-Deligne representations from $W_L$ to $W_K$ is not in the library. Even with additivity, the value on an irreducible $r$ of dimension $m \ge 2$ with $N = 0$ is fixed only by conditions 1 and 2. Theorem 3.1.27 below shows that the conditions of Definition 3.1.17 do not fix $\varepsilon$ in dimension $2$.

### The full statement

**Definition 3.1.20 (families with the factors of pairs).** Let $\mathrm{art}$ be as in Remark 3.1.9, let $\varepsilon$ be a Galois $\varepsilon$-function and let $(\mathrm{rec}_m)_{m \le n}$ be a family with the properties of `Langlands.IsLanglandsFamily`. The family *has the factors of pairs for $\varepsilon$* if the following holds for $1 \le m' \le m \le n$, each $\pi \in \mathrm{Irr}(GL_m(K))$ and $\pi' \in \mathrm{Irr}(GL_{m'}(K))$, representatives $\rho$ of $\mathrm{rec}_m(\pi)$ and $\rho'$ of $\mathrm{rec}_{m'}(\pi')$, and each $\psi$ with a conductor exponent $k$ such that $\pi$ is $\psi$-generic and $\pi'$ is $\psi^{-1}$-generic.
1. For each Haar measure $\mu$, the $L$-factor $L(s, \rho \otimes \rho')$ is an $L$-factor of pairs for $(\pi, \pi', \psi)$.
2. For each Haar measure $\mu$ with $\mu(\mathcal{O}_K)^2 q^k = 1$, the function $\varepsilon(\cdot, \rho \otimes \rho', \psi, \mu)$ is an $\varepsilon$-factor of pairs for $(\pi, \pi', \psi)$.

Lean: `Langlands.IsSelfDual`, `Langlands.IsLanglandsFamilyPairs`

The measures of part 2 are the self dual measures for $\psi$. For $k = 0$ the self dual measure gives $\mathcal{O}_K$ volume $1$. The zeta integrals of pairs are computed with the measure $\mu$, so part 1 is a condition for each $\mu$. It does not depend on $\mu$, since a change of $\mu$ multiplies each zeta integral by a positive constant.

**Definition 3.1.21 (the statement `LocalLanglandsGLFull`).** Let $n \ge 0$. The statement $\mathrm{LLC}^{\mathrm{full}}_n$ says the following. For each nonarchimedean local field $K$, with the Borel $\sigma$-algebra, and each local Artin map $\mathrm{art}$, there are a Galois $\varepsilon$-function $\varepsilon$ that satisfies the conditions of Deligne and a family $(\mathrm{rec}_m)_{m \le n}$ with the properties of `Langlands.IsLanglandsFamily` that has the factors of pairs for $\varepsilon$.

Lean: `Langlands.LocalLanglandsGLFull`

**Proposition 3.1.22 (the full statement implies the Lean statement).** $\mathrm{LLC}^{\mathrm{full}}_n$ implies the statement `Langlands.LocalLanglandsGL n` of Remark 3.1.9.

Lean: `Langlands.LocalLanglandsGLFull.localLanglandsGL`, with `Langlands.IsLanglandsFamilyPairs.isLanglandsFamily`

*Proof.* Forget $\varepsilon$ and the factors of pairs. $\square$

**Remark 3.1.23 (comparison with Theorem 3.1.2).** The statement $\mathrm{LLC}^{\mathrm{full}}_n$ adds to `LocalLanglandsGL n` condition 5 of Theorem 3.1.2 for $n' \ge 1$, and the $\varepsilon$-factors. It differs from Theorem 3.1.2 in four ways. First, the conditions on pairs are stated only for generic $\pi$ and $\pi'$, and only for $m' \le m$. Second, the $\varepsilon$-function is chosen together with the family, and it is not the $\varepsilon$-factor of Deligne and Langlands, see Theorem 3.1.27. Third, the statement does not say that the family is unique. Fourth, it gives no statement on conductors or on $\mathcal{A}^0_n$ and $\mathcal{A}^2_n$. Theorem 3.1.2, Theorem 3.1.13 and the factor of Definition 2.4.10, extended to all Haar measures $\mu$ by the factor $c^{\dim \rho}$ for $c\mu$, should give $\mathrm{LLC}^{\mathrm{full}}_n$, by Proposition 3.1.18. The Lean project does not state this deduction.

### The case $GL_1 \times GL_1$

For $n = 1$ the group $N_1$ is trivial, so each linear form is a Whittaker functional and each representation with nonzero space is generic. Let $\pi$ act by $\chi(\det g)$ on a nonzero space $V$, and $\pi'$ by $\chi'(\det g)$ on a nonzero space $V'$. Then each $W \in \mathcal{W}(\pi, \psi)$ is $W(g) = \lambda(v) \chi(g)$, and each $W' \in \mathcal{W}(\pi', \psi^{-1})$ is $W'(g) = \lambda'(v') \chi'(g)$. Here $Z(\varphi, \chi, s) = \int_K \varphi(y) \chi(y) |y|^{s-1} d\mu(y)$ is the additive zeta integral of Section 3.2.

**Proposition 3.1.24 (the zeta integrals of pairs for $GL_1$).** Let $W = a \chi$ and $W' = b \chi'$, let $\Phi$ be a Schwartz-Bruhat function on $K$, and put $\eta = \chi \chi'$.
1. $\Psi(s, W, W', \Phi) = a b \, Z(\Phi, \eta, s)$.
2. $\tilde W = a \chi^{-1}$ and $\tilde W' = b \chi'^{-1}$. So each pair of the functional equation is $\big(c Z(\varphi, \eta, s), c Z(\hat \varphi, \eta^{-1}, s)\big)$ for a constant $c$ and a Schwartz-Bruhat function $\varphi$.
3. $L(s, \eta)$ is the $L$-factor of pairs for $(\pi, \pi', \psi)$, and $L(s, \eta^{-1})$ is the one for $(\tilde \pi, \tilde \pi', \psi^{-1})$.

Lean: `Langlands.rsZetaPhi_one`, `Langlands.mem_rsFEPairs_one`, `Langlands.zeta_pair_mem_rsFEPairs_one`, `Langlands.isRSLFactor_one`, `Langlands.isZetaGenerator_of_zeta`, `Langlands.contragredient_one_apply`

*Proof.* For $m = 1$ the group $\bar N_1$ is trivial, and the integral over $N_1 \backslash GL_1(K) = K^\times$ is $\int_K F(t) |t|^{-1} d\mu(t)$. So
$$\Psi(s, W, W', \Phi) = \int_K a \chi(t) \, b \chi'(t) \, \Phi(t) \, |t|^s \, |t|^{-1} \, d\mu(t) = a b \, Z(\Phi, \eta, s).$$
This is part 1. For part 2, $w_1 = 1$ and ${}^t g^{-1} = g^{-1}$, so $\tilde W(g) = a \chi(g)^{-1}$. Part 1 for $\chi^{-1}, \chi'^{-1}$ and $\hat \Phi$ gives the second member of the pair, with the same constant $c = ab$. For part 3, the zeta integrals are the functions $ab \, Z(\Phi, \eta, s)$. Since $V \ne 0$ and $V' \ne 0$, there are $\lambda, v$ with $\lambda(v) = 1$, and the same for $\pi'$, so each $Z(\Phi, \eta, s)$ is a zeta integral. Corollary 3.2.19 shows that $L(s, \eta)$ generates the set of the multiples $c Z(\varphi, \eta, s)$ that contains each $Z(\varphi, \eta, s)$. This is `Langlands.isZetaGenerator_of_zeta`. The contragredient of $\pi$ acts by $\chi^{-1}(\det g)$ on a nonzero space, which gives the second statement. $\square$

**Theorem 3.1.25 (the $\varepsilon$-factor of pairs for $GL_1$).** In Proposition 3.1.24, let $\psi$ have conductor exponent $k$, and let $\mu$ be a Haar measure. Then Tate's factor $\varepsilon(s, \eta, \psi)$ for $\mu$ is the $\varepsilon$-factor of pairs for $(\pi, \pi', \psi)$. This holds for each Haar measure, self dual or not.

Lean: `Langlands.isRSEpsilonFactor_one`, with `Langlands.LocalGL1.zeta_eq_laurent_of_lt`, `Langlands.LocalGL1.fourier_isSchwartzBruhat`, `Langlands.LocalGL1.isTateEpsilon_tateEpsilon`, `Langlands.LocalGL1.tateEpsilon_monomial`, `Langlands.eq_of_differentiable_of_eqOn_strip`, `Langlands.differentiable_laurent`

*Proof.* Tate's factor is a monomial $c q^{-ks}$ with $c \ne 0$. By Proposition 3.1.24 the two $L$-factors are $L(s, \eta)$ and $L(s, \eta^{-1})$, and the sign $\omega'(-1)^{n-1}$ is $1$ for $n = 1$. Take a pair $(c Z(\varphi, \eta, s), c Z(\hat \varphi, \eta^{-1}, s))$. The function $\hat \varphi$ is Schwartz-Bruhat. Corollary 3.2.19, part 1, holds for $|\eta(\varpi) q^{1-s}| \le 1$. The same recursions over the shells give it on the larger half plane $|\eta(\varpi) q^{-s}| < 1$, which is `Langlands.LocalGL1.zeta_eq_laurent_of_lt`. So $Z(\varphi, \eta, s) = A(X) X^{-j} L(s, \eta)$ for $\mathrm{Re}(s) > \log_q |\eta(\varpi)|$, and $Z(\hat \varphi, \eta^{-1}, s) = A'(X) X^{-j'} L(s, \eta^{-1})$ for $\mathrm{Re}(s) > -\log_q |\eta(\varpi)|$. Put $F(s) = c A'(q^{s-1}) q^{(1-s) j'}$ and $G(s) = \varepsilon(s, \eta, \psi) \, c A(q^{-s}) q^{s j}$. On the strip $\log_q |\eta(\varpi)| < \mathrm{Re}(s) < 1 + \log_q |\eta(\varpi)|$ both expansions hold, at $s$ and at $1 - s$, and the functional equation of Tate gives $F(s) = G(s)$. Both $F$ and $G$ are entire functions, and the strip is open and not empty. By the identity theorem $F = G$ on $\mathbb{C}$. $\square$

To get $\mathrm{LLC}^{\mathrm{full}}_1$ we need a Galois $\varepsilon$-function. Let $E(s, \rho, \psi, \mu)$ be Tate's factor $\varepsilon(s, \chi_\rho, \psi)$ for $\mu$ if $\dim \rho = 1$, $\mu$ is a Haar measure and $\psi$ has a conductor exponent, and $E = 1$ in all other cases. Put
$$\varepsilon_{\mathrm{gal}}(s, \rho, \psi, \mu) = E(s, \rho^0, \psi, \mu) \, \frac{\det(-q^{-s} \Phi \mid V^I)}{\det(-q^{-s} \Phi \mid V^I_N)}.$$
By Proposition 3.1.18 this is the only form that condition 4 allows once the values on the representations $\rho^0$ are fixed.

**Theorem 3.1.26 ($\mathrm{LLC}^{\mathrm{full}}_1$).**
1. The function $\varepsilon_{\mathrm{gal}}$ satisfies the conditions of Deligne.
2. The family $(\mathrm{rec}_0, \mathrm{rec}_1)$ of Theorem 3.2.14 has the factors of pairs for $\varepsilon_{\mathrm{gal}}$.
3. So $\mathrm{LLC}^{\mathrm{full}}_1$ holds, with no hypothesis.

Lean: `Langlands.Fidelity.galEps`, `Langlands.Fidelity.epsTate`, `Langlands.Fidelity.isWDEpsilon_galEps`, `Langlands.Fidelity.isLanglandsFamilyPairs_recFamily`, `Langlands.Fidelity.localLanglandsGLFull_one`

*Proof.* Part 1. Let $g$ be an isomorphism from $\rho$ to $\rho'$. Then $g$ maps $V^I$ onto $V'^I$ and $V^I_N$ onto $V'^I_{N'}$, and it carries $\Phi$ to $\Phi$, so the two determinants do not change. Also $\det r' = \det r$, so $\chi_{\rho'} = \chi_\rho$. This gives condition 1. Tate's factor and $1$ are monomials with nonzero coefficient, and each determinant is a nonzero monomial in $q^{-s}$ by the remark after Proposition 3.1.18. This gives condition 2. In dimension $1$, $N = 0$ and $\rho^0 = \rho$, so the two determinants cancel, and $\varepsilon_{\mathrm{gal}}$ is Tate's factor, which is the Tate factor of $(\chi_\rho, \mu, \psi)$ by Tate's functional equation. This gives condition 3. Since $(\rho^0)^0 = \rho^0$ and the space $V^I_N$ of $\rho^0$ is $V^I$, we get $\varepsilon_{\mathrm{gal}}(\rho^0) = E(\rho^0)$. Then $\varepsilon_{\mathrm{gal}}(\rho) \det(-q^{-s}\Phi \mid V^I_N) = E(\rho^0) \det(-q^{-s}\Phi \mid V^I) = \varepsilon_{\mathrm{gal}}(\rho^0) \det(-q^{-s}\Phi \mid V^I)$. This is condition 4.

Part 2. The conditions of `IsLanglandsFamily` are Theorem 3.2.14. For pairs, $m = m' = 1$. Let $\pi$ and $\pi'$ be irreducible with characters $\chi$ and $\chi'$. By the proof of Theorem 3.2.14, $\rho = (\chi \circ \mathrm{art}^{-1}, 0)$ and $\rho' = (\chi' \circ \mathrm{art}^{-1}, 0)$, so $\rho \otimes \rho' = (\eta \circ \mathrm{art}^{-1}, 0)$ with $\eta = \chi\chi'$. Its $L$-factor is $L(s, \eta)$, and condition 1 of Definition 3.1.20 is Proposition 3.1.24, part 3. By part 1, $\varepsilon_{\mathrm{gal}}(\rho \otimes \rho')$ is Tate's factor $\varepsilon(s, \eta, \psi)$ for $\mu$, and condition 2 is Theorem 3.1.25.

Part 3 follows from parts 1 and 2. $\square$

The proof of part 1 has one point that needs care. In Lean the condition of isomorphism asks that $\varepsilon_{\mathrm{gal}}$ be invariant under isomorphism, so the invariance of $\det(c\Phi \mid V^I_N)$ must be proved. This is `Langlands.Fidelity.det_smul_frob_eq_of_iso`. The factor $E$ uses a conductor exponent of $\psi$ chosen by `Classical.choose`. The value of Tate's factor does not depend on this choice, and the proof does not need the uniqueness of the exponent.

### What the conditions on $\varepsilon$ do not fix

**Theorem 3.1.27 (a second Galois $\varepsilon$-function).** Let $\varepsilon_{\mathrm{sgn}}(s, \rho, \psi, \mu) = -\varepsilon_{\mathrm{gal}}(s, \rho, \psi, \mu)$ if $\dim \rho = 2$, and $\varepsilon_{\mathrm{sgn}} = \varepsilon_{\mathrm{gal}}$ in the other dimensions.
1. $\varepsilon_{\mathrm{sgn}}$ satisfies the conditions of Deligne.
2. $\varepsilon_{\mathrm{sgn}} \ne \varepsilon_{\mathrm{gal}}$.
3. The family $(\mathrm{rec}_0, \mathrm{rec}_1)$ has the factors of pairs for $\varepsilon_{\mathrm{sgn}}$ and for $\varepsilon_{\mathrm{gal}}$. So the $\varepsilon$-function in a witness of $\mathrm{LLC}^{\mathrm{full}}_1$ is not unique.

Lean: `Langlands.Fidelity.galEpsSign`, `Langlands.Fidelity.trivWD`, `Langlands.Fidelity.isWDEpsilon_galEpsSign`, `Langlands.Fidelity.galEps_ne_galEpsSign`, `Langlands.Fidelity.not_unique_epsilon_one`

*Proof.* Part 1. Multiplication by a constant that depends only on the dimension keeps conditions 1 and 2. Condition 3 concerns dimension $1$, where nothing changes. In condition 4 the representations $\rho$ and $\rho^0$ have the same dimension, so both sides are multiplied by the same sign. Part 2. Let $\rho = (1, 0)$ be the trivial representation of dimension $2$. Then $V^I_N = V^I = \mathbb{C}^2$, so $\varepsilon_{\mathrm{gal}}(s, \rho, \psi, \mu) = E(s, \rho, \psi, \mu) = 1$ and $\varepsilon_{\mathrm{sgn}}(s, \rho, \psi, \mu) = -1$, for all $s, \psi, \mu$. Lean checks this at $\mu = 0$, $\psi = 1$ and $s = 0$. Part 3. For $n = 1$ the conditions on pairs concern only $\rho \otimes \rho'$ of dimension $1$, where the two functions agree. Theorem 3.1.26 gives the rest. $\square$

**Remark 3.1.28 (the meaning of Theorem 3.1.27).** Condition 4 fixes $\varepsilon(\rho)$ from $\varepsilon(\rho^0)$. In dimension $m \ge 2$, on the representations $\rho^0$ with $N = 0$, only conditions 1 and 2 constrain $\varepsilon$, since there is no additivity and no inductivity. So for $n \ge 2$ the factor $\varepsilon(\rho \otimes \rho')$ of dimension $m m' \ge 2$ in condition 2 of Definition 3.1.20 is a function that the statement chooses. Condition 2 then compares the $\varepsilon$-factor of pairs of $\pi \times \pi'$ with this chosen function, and not with the factor of Deligne and Langlands. The function $\varepsilon_{\mathrm{gal}}$ itself is not the factor of Definition 2.4.10 (Exercise 17), and it is not additive (Exercise 16). A Galois $\varepsilon$-function that its conditions fix needs the inductivity in degree $0$, so the induction of Weil-Deligne representations. Henniart's Corollary 3.1.5 cannot be applied to $\mathrm{LLC}^{\mathrm{full}}_n$ before that.

**Proposition 3.1.29 (the family is unique for $n = 1$).** Any two families $(\mathrm{rec}_0, \mathrm{rec}_1)$ with the properties of `Langlands.IsLanglandsFamily` are equal.

Lean: `Langlands.Fidelity.recFamily_unique`, with `Langlands.Fidelity.subsingleton_wdIso_zero`

*Proof.* All Weil-Deligne representations of dimension $0$ are isomorphic, so $\mathcal{G}_0(K)$ has one element and $\mathrm{rec}_0$ is unique. Condition 1 fixes $\mathrm{rec}_1$. $\square$

So for $n = 1$ the conditions on pairs add no information on the family. A test of the conditions on pairs with a second family, for example the twist of $\mathrm{rec}_2$ by an unramified quadratic character on part of $\mathcal{A}_2(K)$, needs a correspondence for $GL_2$, which is not in Lean.

**Remark 3.1.30 (Lean, and what is still open).** The file `Langlands/Fidelity/LocalLanglandsFull.lean` has Theorems 3.1.26 and 3.1.27 and Proposition 3.1.29. It also checks that the statement is not true for a trivial reason: the types are not empty, by `Langlands.Fidelity.isSmoothChar_one`, `Langlands.Fidelity.nonempty_irrSmooth_one` and `Langlands.Fidelity.nonempty_wdIso`, and the monomial condition asks for $c \ne 0$, so $\varepsilon = 0$ is not allowed. The proof of Theorem 3.1.26 shows three weak points of the statement. Condition 3 of Definition 3.1.17 asks for the Tate factor for each conductor exponent $k$ of $\psi$, although the factor does not depend on $k$. The self dual measure of Definition 3.1.20 is not needed for $GL_1$, by Theorem 3.1.25. The condition of isomorphism forces the proof of `Langlands.Fidelity.det_smul_frob_eq_of_iso`. The following is not in Lean: $\mathrm{LLC}^{\mathrm{full}}_n$ for $n \ge 2$; Theorem 3.1.13; a Galois $\varepsilon$-function with additivity and inductivity, and the comparison with Definition 2.4.10; a second family for $n = 2$; the factors of pairs of non generic representations; the convergence of the zeta integrals; and the uniqueness of the family for $n \ge 2$.
