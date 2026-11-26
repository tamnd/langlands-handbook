---
title: L-factors, conductors and epsilon-factors
nodes: []
sources: [Tat79, Ser79, BH06]
status: checked
drafted_by: writer@claude-opus-5-5
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## L-factors, conductors and epsilon-factors

This section attaches to a Weil-Deligne representation $V = (r, N)$ its local $L$-factor $L(s, V)$, its conductor $a(V)$ and its $\varepsilon$-factor $\varepsilon(s, V, \psi)$. The $L$-factor and the conductor are elementary. The $\varepsilon$-factor rests on a deep theorem of Langlands and Deligne, which extends Tate's local constants of characters to all representations of $W_K$. The example is $\mathrm{Sp}(2)$: its factors are those of the Steinberg representation, and the operator $N$ is what makes them right. We follow [Tat79, Sections 3 and 4]. Throughout, $\psi$ is a nontrivial additive character of $K$, and when we need a normalization we take $\psi$ of conductor $\mathcal{O}_K$, as in Volume 3, Section 4.3.

### The $L$-factor

For a Weil-Deligne representation $(r, N)$ on $V$, let $V^{I} = V^{r(I_K)}$ and let $V^{I}_N = \ker N \cap V^{I}$.

**Definition 2.4.1 ($L$-factor).** The *$L$-factor* of $V = (r, N)$ is
$$L(s, V) = \det\big(1 - q^{-s} r(\Phi) \mid V^{I}_N\big)^{-1}.$$

Lean: `Langlands.WeilDeligneRep.lFactor` (with `Langlands.WeilDeligneRep.lSpace` for $V^I_N$ and `Langlands.WeilDeligneRep.frobOnLSpace` for $r(\Phi)$ on it)

**Lemma 2.4.2.** The subspace $V^{I}_N$ is stable under $r(W_K)$. The action of $r(\Phi)$ on it does not depend on the choice of $\Phi$.

Lean: `Langlands.WeilDeligneRep.lSpace_stable`

*Proof.* The subspace $V^{I}$ is stable under $r(W_K)$ because $I_K$ is normal in $W_K$. If $Nv = 0$, then $N r(w) v = \|w\|^{-1} r(w) N v = 0$. Two geometric Frobenius elements differ by an element of $I_K$, which acts trivially on $V^{I}$. $\square$

So $L(s, V) = P(q^{-s})^{-1}$ for a polynomial $P$ with $P(0) = 1$ and $\deg P = \dim V^{I}_N$. For a character $\chi$ of $K^\times$, viewed as $(\chi, 0)$, we get $L(s, \chi) = (1 - \chi(\varpi) q^{-s})^{-1}$ if $\chi$ is unramified and $L(s, \chi) = 1$ otherwise. This is the local factor of Tate's thesis (Volume 3, Section 4.3). With Artin's normalization one uses the arithmetic Frobenius on $V^{I}$. Since ${}^t r(\Phi)^{-1}$ has the inverse eigenvalues, Artin's factor of $V$ is our $L(s, V^\vee)$. This is Remark 6.1.6 of Volume 3, and it is the reason why the cohomology $H^1 = V_\ell^\vee$, and not the Tate module, appears in the $L$-function of an elliptic curve.

**Proposition 2.4.3 (properties of the $L$-factor).** Let $V$ and $V'$ be Weil-Deligne representations.
1. $L(s, V \oplus V') = L(s, V) L(s, V')$.
2. $L(s, V) = L(s, V^{ss})$, where $V^{ss}$ is the Frobenius-semisimplification of Proposition 2.2.6.
3. $L(s, V \otimes \omega_t) = L(s + t, V)$ for $t \in \mathbb{C}$.
4. If $N = 0$ and $L / K$ is finite separable, then $L(s, \mathrm{Ind}_{W_L}^{W_K} V') = L(s, V')$ for each representation $V'$ of $W_L$, where the right side is the $L$-factor over $L$.

Lean: not stated yet

*Proof.* Parts 1 and 3 are clear. For part 2, the subspace $V^I_N$ is the same for $r$ and $r^{ss}$, since $r^{ss} = r$ on $I_K$, and $r^{ss}(\Phi) = s$ has the same characteristic polynomial as $r(\Phi)$ on each subspace stable under both. For part 4, both sides are additive in $V'$, so we may assume that $V'$ is irreducible. By Proposition 2.1.12, $V' = V'_0 \otimes \omega_t$ with $V'_0$ of finite image, and $\mathrm{Ind}(V'_0 \otimes \omega_t) = (\mathrm{Ind}\, V'_0) \otimes \omega_t$, since $\omega_t$ restricts to $\omega_t$ on $W_L$ (Proposition 2.1.5). By part 3 we may assume that $t = 0$. Then $V'$ and $\mathrm{Ind}\, V'$ factor through $\mathrm{Gal}(M / K)$ for a finite Galois extension $M / K$ that contains $L$. The claim is Volume 3, Lemma 6.3.2, with $D = \mathrm{Gal}(M / K)$, $D' = \mathrm{Gal}(M / L)$, $\varphi$ the image of $\Phi$, $\varphi'$ the image of a geometric Frobenius of $L$ and $T = q^{-s}$, since $q_L^{-s} = T^f$. $\square$

The $L$-factor is not additive in short exact sequences. This is the first difference between $L$-factors of Weil-Deligne representations and of representations of $W_K$.

**Example 2.4.4 (special representations).** Let $\rho$ be an irreducible representation of $W_K$. The kernel of $N$ on $\mathrm{Sp}(n) \otimes \rho$ is $\rho \|\cdot\|^{n-1}$, so
$$L(s, \mathrm{Sp}(n) \otimes \rho) = L(s + n - 1, \rho).$$
If $\dim \rho \ge 2$, then $\rho^{I} = 0$. Indeed $\rho^{I}$ is stable under $W_K$, so it is $0$ or $\rho$. In the second case $\rho$ factors through $W_K / I_K \cong \mathbb{Z}$, which is abelian, and an irreducible representation of an abelian group has dimension $1$. So $L(s, \mathrm{Sp}(n) \otimes \rho) = 1$ unless $\rho$ is an unramified character $\chi$, and then $L(s, \mathrm{Sp}(n) \otimes \chi) = (1 - \chi(\varpi) q^{1 - n - s})^{-1}$. For $n = 2$ there is an exact sequence $0 \to \|\cdot\| \to \mathrm{Sp}(2) \to 1 \to 0$, but $L(s, \mathrm{Sp}(2)) = (1 - q^{-1-s})^{-1}$ while $L(s, \|\cdot\|) L(s, 1) = (1 - q^{-1-s})^{-1} (1 - q^{-s})^{-1}$.

**Example 2.4.5 (elliptic curves).** Let $A$ be an elliptic curve over $K$ and $H^1 = V_\ell(A)^\vee$, with its Weil-Deligne representation through $\iota$ (Remark 2.3.6). The $L$-factor $L(s, H^1)$ is the classical Euler factor of $A$.
1. Good reduction: $H^1$ is unramified, $N = 0$, and $r(\Phi)$ has the characteristic polynomial $X^2 - aX + q$ (Example 2.3.8). So $L(s, H^1) = (1 - a q^{-s} + q^{1 - 2s})^{-1}$.
2. Split multiplicative reduction: $H^1 \cong \mathrm{Sp}(2) \otimes \|\cdot\|^{-1}$ by Example 2.3.7. So $L(s, H^1) = L(s + 1, \|\cdot\|^{-1}) = (1 - q^{-s})^{-1}$.
3. Nonsplit multiplicative reduction: $L(s, H^1) = (1 + q^{-s})^{-1}$, by Exercise 6.
4. Additive and potentially good reduction: $N = 0$ and $L(s, H^1) = \det(1 - q^{-s} r(\Phi) \mid (H^1)^{I})^{-1}$. If $\rho(I_K)$ acts on $H^1$ without fixed vectors, then $L = 1$.

### The conductor

Let $r$ be a representation of $W_K$. By Proposition 2.1.10 the group $r(I_K)$ is finite, and $r|_{I_K}$ factors through the inertia group of a finite Galois extension. So $r$ has an Artin conductor $a(r)$, defined with the ramification groups by the formula of Volume 3, Definition 6.4.1. It is additive, it is $0$ exactly when $r$ is unramified, and for a character it is the conductor $a(\chi)$ of Volume 3, Definition 4.1.3 [Ser79, Chapter VI].

**Definition 2.4.6 (conductor).** The *conductor* of a Weil-Deligne representation $V = (r, N)$ is
$$a(V) = a(r) + \dim V^{I} - \dim V^{I}_N.$$

Lean: not stated yet

The correction term $\dim V^I - \dim V^I_N$ is the rank of $N$ on $V^I$. It is $0$ when $N = 0$, and it is additive on direct sums, so $a$ is additive.

**Example 2.4.7 (conductors of special representations).** Let $\chi$ be a character. If $\chi$ is unramified, then $a(r) = 0$, $\dim V^I = n$ and $\dim V^I_N = 1$, so $a(\mathrm{Sp}(n) \otimes \chi) = n - 1$. If $\chi$ is ramified, then $V^I = 0$ and $a(\mathrm{Sp}(n) \otimes \chi) = n \, a(\chi)$. For the elliptic curves of Example 2.4.5 the conductor is $0$ in case 1, and $1$ in cases 2 and 3. In case 4 it is $2 + \delta$, where $\delta \ge 0$ is the Swan conductor, which vanishes when $p \ge 5$. These are the exponents of the conductor of an elliptic curve, as defined by Ogg and Serre. On the side of $GL_n(K)$, the conductor of the Steinberg representation is $1$, the level of its newforms. This is the first check of the correspondence of Example 2.2.11 beyond the $L$-factor.

### The $\varepsilon$-factor

Let $\chi$ be a character of $K^\times$. Tate's thesis gives the local constant $\varepsilon(s, \chi, \psi)$ through the local functional equation (Volume 3, Theorem 4.3.1). For $\psi$ of conductor $\mathcal{O}_K$ it is $1$ for unramified $\chi$, and for $\chi$ of conductor $m \ge 1$ it is
$$\varepsilon(s, \chi, \psi) = \chi(\varpi)^m q^{-ms} \, G(\chi^{-1}, \psi), \qquad G(\chi^{-1}, \psi) = \sum_{u \in (\mathcal{O}_K / \varpi^m)^\times} \chi^{-1}(u) \, \psi(u / \varpi^m),$$
with the Haar measure that gives $\mathcal{O}_K$ volume $1$. The problem is to extend this to representations of higher dimension. Artin's conductor suggests the answer: it is additive and, in degree $0$, it is compatible with induction. The extension rests on the following consequence of Brauer's theorem.

**Lemma 2.4.8 (Brauer).** Let $G$ be a finite group. Each virtual character of $G$ of dimension $0$ is an integral combination of the virtual characters $\mathrm{Ind}_H^G(\chi - 1_H)$, where $H$ runs over the subgroups of $G$ and $\chi$ over the characters of dimension $1$ of $H$.

Lean: not stated yet

*Proof.* Let $x$ have dimension $0$, and let $S$ be the span of the $\mathrm{Ind}_H^G(\chi - 1_H)$. By Brauer's theorem (Volume 3, Theorem 6.6.3) we have $1_G = \sum_j m_j \mathrm{Ind}_{H_j}^G \theta_j$ with $H_j$ elementary and $\theta_j$ of dimension $1$. Then $x = \sum_j m_j \mathrm{Ind}_{H_j}^G(\theta_j \cdot x|_{H_j})$, and $\theta_j \cdot x|_{H_j}$ has dimension $0$. Induction is transitive, so it suffices to prove the lemma for an elementary group $G$. An elementary group is nilpotent, so each irreducible representation of $G$ is induced from a character of a subgroup. Hence $x = \sum_i n_i \mathrm{Ind}_{H_i}^G \chi_i$ with $\sum_i n_i [G : H_i] = 0$, and $x \equiv \sum_i n_i \mathrm{Ind}_{H_i}^G 1$ modulo $S$. In a nilpotent group each subgroup $H$ is the start of a chain $H = H_0 \subset H_1 \subset \dots \subset H_k = G$ with $H_{i}$ normal of prime index in $H_{i+1}$. For such a step, $\mathrm{Ind}_{H_i}^{H_{i+1}} 1$ is the sum of the characters of the cyclic group $H_{i+1} / H_i$, so it is $[H_{i+1} : H_i] \cdot 1$ modulo $S$. By induction $\mathrm{Ind}_H^G 1 \equiv [G : H] \cdot 1$ modulo $S$. So $x \equiv (\sum_i n_i [G : H_i]) \cdot 1 = 0$ modulo $S$. $\square$

**Theorem 2.4.9 (Langlands, Deligne).** There is a unique function $\varepsilon(s, r, \psi)$ of a nonarchimedean local field $K$, a representation $r$ of $W_K$ and a nontrivial character $\psi$ of $K$, with these properties.
1. $\varepsilon(s, r \oplus r', \psi) = \varepsilon(s, r, \psi) \, \varepsilon(s, r', \psi)$.
2. For $\dim r = 1$, $\varepsilon(s, r, \psi)$ is Tate's local constant of the corresponding character of $K^\times$.
3. For a finite separable extension $L / K$ and a virtual representation $r'$ of $W_L$ of dimension $0$, $\varepsilon(s, \mathrm{Ind}_{W_L}^{W_K} r', \psi) = \varepsilon(s, r', \psi \circ \mathrm{Tr}_{L/K})$.

Lean: not stated yet

This is Theorem 4.3.8 of Volume 3. By part 1, $\varepsilon$ extends to virtual representations. *Uniqueness.* Let $r$ be irreducible. By Proposition 2.1.12, $r = r_0 \otimes \omega_t$ with $r_0$ trivial on $W_M$ for a finite Galois extension $M / K$. Lemma 2.4.8, applied to $G = \mathrm{Gal}(M / K)$, writes $r_0 - \dim r_0 \cdot 1$ as a combination of virtual representations $\mathrm{Ind}_{W_{L}}^{W_K}(\chi - 1)$. Since $\mathrm{Ind}(y) \otimes \omega_t = \mathrm{Ind}(y \otimes \omega_t|_{W_L})$, and $\omega_t|_{W_L}$ is the character $\omega_t$ of $W_L$ by Proposition 2.1.5, parts 1 to 3 express $\varepsilon(s, r, \psi)$ through the constants of characters. *Existence.* This is the hard part, since the expression of $r$ through induced characters is far from unique, and one must show that all choices give the same value. Langlands proved it by a long local argument, which he did not publish. Deligne gave a global proof in "Les constantes des équations fonctionnelles des fonctions L" (1973). He embeds the local situation in a global one, and he uses the functional equations of Hecke $L$-functions together with Brauer's theorem to show that the local constants are well defined. A summary is in [Tat79, Section 3]. The constant $\lambda(L / K, \psi) = \varepsilon(s, \mathrm{Ind}\, 1_L, \psi) / \varepsilon(s, 1_L, \psi \circ \mathrm{Tr})$ is called the *Langlands constant*. It does not depend on $s$.

**Definition 2.4.10 ($\varepsilon$-factor and $\gamma$-factor).** Let $V = (r, N)$ be a Weil-Deligne representation. Its *$\varepsilon$-factor* and *$\gamma$-factor* are
$$\varepsilon(s, V, \psi) = \varepsilon(s, r, \psi) \, \det\big(-q^{-s} r(\Phi) \mid V^{I} / V^{I}_N\big), \qquad \gamma(s, V, \psi) = \varepsilon(s, V, \psi) \frac{L(1 - s, V^\vee)}{L(s, V)}.$$
Here $\varepsilon(s, r, \psi)$ is extended to nonsemisimple $r$ through the semisimplification.

Lean: not stated yet

**Proposition 2.4.11 (properties of the $\varepsilon$-factor).** Let $V = (r, N)$ be a Weil-Deligne representation, and let $\psi_b(x) = \psi(bx)$ for $b \in K^\times$.
1. If $\psi$ has conductor $\mathcal{O}_K$, then $\varepsilon(s, V, \psi) = \varepsilon(0, V, \psi) \, q^{-a(V) s}$.
2. $\varepsilon(s, V \otimes \omega_t, \psi) = \varepsilon(s + t, V, \psi)$.
3. $\varepsilon(s, V, \psi_b) = \det V(b) \, |b|^{\dim V (s - 1/2)} \, \varepsilon(s, V, \psi)$, where $\det V$ is viewed as a character of $K^\times$.
4. $\varepsilon(s, V, \psi) \, \varepsilon(1 - s, V^\vee, \psi) = \det V(-1)$.

Lean: not stated yet

*Proof.* All four statements hold for characters by Tate's theory (Volume 3, Section 4.3, and Volume 0, Remark 3.2.1 for the change of $\psi$). For representations $r$ of $W_K$ they follow from the case of characters by the uniqueness argument above, since each side is multiplicative and compatible with induction in degree $0$. The case of part 1 also needs the behaviour of the conductor under induction (Volume 3, Section 6.4). It remains to treat the correction factor. It does not depend on $\psi$. Its degree in $q^{-s}$ is $\dim V^I - \dim V^I_N$, which gives part 1, and part 2 is clear. For part 4, by Proposition 2.2.6 and Theorem 2.2.8 we may assume that $V = \mathrm{Sp}(n) \otimes \rho$ with $\rho$ irreducible. If $\rho$ is not an unramified character, then $V^I = 0$ and $(V^\vee)^I = 0$, so the correction factors are $1$. If $\rho = \chi$ is unramified, Exercise 7 shows that the two correction factors multiply to $1$. $\square$

**Example 2.4.12 (the Steinberg representation).** Let $\chi$ be unramified and let $\psi$ have conductor $\mathcal{O}_K$. Then $\varepsilon(s, \chi \oplus \chi\|\cdot\|, \psi) = 1$. On $V = \mathrm{Sp}(n) \otimes \chi$ the quotient $V^I / V^I_N$ has the basis $e_0, \dots, e_{n-2}$, on which $r(\Phi)$ has the eigenvalues $\chi(\varpi) q^{-i}$. So
$$\varepsilon(s, \mathrm{Sp}(n) \otimes \chi, \psi) = \prod_{i=0}^{n-2} \big(-\chi(\varpi) q^{-i-s}\big).$$
For $n = 2$ and $\chi = \eta |\cdot|^{-1/2}$, which corresponds to $\eta \mathrm{St}$ by Example 2.2.11, this gives $\varepsilon(s, \mathrm{Sp}(2) \otimes \eta|\cdot|^{-1/2}, \psi) = -\eta(\varpi) q^{1/2 - s}$. For $\eta = 1$ the root number $\varepsilon(1/2, \mathrm{St}, \psi) = -1$ is the sign that appears in the functional equation of an elliptic curve with split multiplicative reduction at $p$. For nonsplit reduction it is $+1$.

**Example 2.4.13 (a dihedral representation).** Let $L / K$ be the unramified quadratic extension, and let $\theta$ be a character of $L^\times$ of conductor $m \ge 1$ with $\theta^\tau \ne \theta$. Then $\rho = \mathrm{Ind}_{W_L}^{W_K} \theta$ is irreducible (Example 2.1.13). Here $\mathrm{Ind}\, 1_L = 1 \oplus \eta$ with $\eta$ the unramified quadratic character, so $\lambda(L / K, \psi) = \varepsilon(s, \eta, \psi) = 1$. Theorem 2.4.9 gives
$$\varepsilon(s, \rho, \psi) = \varepsilon(s, \theta, \psi \circ \mathrm{Tr}_{L/K}) = \theta(\varpi)^m \, q^{-2ms} \, G(\theta^{-1}, \psi \circ \mathrm{Tr}_{L/K}),$$
since $\psi \circ \mathrm{Tr}_{L/K}$ has conductor $\mathcal{O}_L$ and the residue field of $L$ has $q^2$ elements. So $a(\rho) = 2m$, in agreement with the formula $a(\mathrm{Ind}\, \theta) = f \, a(\theta)$ for an unramified extension of degree $f$. For $m = 1$ the sum is a Gauss sum over the field with $q^2$ elements, and $\rho$ is one of the tame representations of Example 2.1.14. Its $L$-factor is $1$ by Example 2.4.4.
