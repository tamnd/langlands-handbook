---
title: The conductor and the functional equation
nodes: []
sources: [Neu99, Ser79, Tat79]
status: drafted
drafted_by: writer
reviewed_by: []
---
## The conductor and the functional equation

The functional equation of $L(s, \rho)$ needs two more invariants of $\rho$. The first is the Artin conductor, an ideal of $\mathcal{O}_F$ built from the ramification groups at the ramified primes. The second is the gamma factor, built from the action of the complex conjugations at the real places. This section defines both, proves that they have the same formal properties as the $L$-function, and states the functional equation. Section 6.6 proves it.

### The Artin conductor

Let $\mathfrak{p}$ be a prime of $F$ and $\mathfrak{P} \mid \mathfrak{p}$ a prime of $L$. The group $D = D_\mathfrak{P}$ is the Galois group of $L_\mathfrak{P}/F_\mathfrak{p}$. Let $G_i \subset D$, for $i \ge 0$, be its ramification groups in the lower numbering, as in [Ser79], Chapter IV. So $G_0 = I_\mathfrak{P}$, the $G_i$ decrease, and $G_i = 1$ for $i$ large. Let $D^u$, for $u \ge -1$, be the ramification groups in the upper numbering. They are defined by $D^{\phi(u)} = G_u$, where $\phi(u) = \int_0^u dt / [G_0 : G_t]$ is the Herbrand function and $G_u = G_{\lceil u \rceil}$ for real $u \ge -1$.

**Definition 6.4.1 (the Artin conductor).** Let $\rho : G \to GL(V)$ be a representation. Its *local conductor* at $\mathfrak{p}$ is
$$f(\rho, \mathfrak{p}) = \sum_{i \ge 0} \frac{|G_i|}{|G_0|} \, \mathrm{codim}\, V^{G_i}.$$
The *Artin conductor* of $\rho$ is the ideal $\mathfrak{f}(\rho) = \prod_\mathfrak{p} \mathfrak{p}^{f(\rho, \mathfrak{p})}$ of $\mathcal{O}_F$. Since $\mathrm{codim}\, V^{G_i} = \chi(1) - \langle \mathrm{Res}_{G_i} \chi, \mathbf{1} \rangle$ is linear in the character $\chi$, the same formula defines $f(\chi, \mathfrak{p})$ and $\mathfrak{f}(\chi)$ for a virtual character $\chi$, as a fractional ideal.

Changing $\mathfrak{P}$ to $\tau\mathfrak{P}$ conjugates all the $G_i$ by $\tau$, and $\rho(\tau)$ maps $V^{G_i}$ onto $V^{\tau G_i \tau^{-1}}$. So $f(\rho, \mathfrak{p})$ does not depend on $\mathfrak{P}$. Since $V^{G_0} \subset V^{G_i}$, all the terms vanish when $\rho$ is unramified at $\mathfrak{p}$. So $\mathfrak{f}(\rho)$ is divisible exactly by the primes at which $\rho$ is ramified. On the interval $(i - 1, i)$ the derivative of $\phi$ is $|G_i| / |G_0|$, and on $(-1, 0)$ it is $1$. So the substitution $v = \phi(u)$ gives
$$f(\rho, \mathfrak{p}) = \int_{-1}^\infty \mathrm{codim}\, V^{G_u} \, \phi'(u) \, du = \int_{-1}^\infty \mathrm{codim}\, V^{D^v} \, dv. \tag{6.4.1}$$

**Proposition 6.4.2 (properties of the conductor).** Let $\rho$ be a representation of $G$ and $\mathfrak{p}$ a prime of $F$.
1. (Artin) $f(\rho, \mathfrak{p})$ is a nonnegative integer. If $\mathfrak{p}$ is at most tamely ramified in $L$, then $f(\rho, \mathfrak{p}) = \mathrm{codim}\, V^{I_\mathfrak{P}}$.
2. $\mathfrak{f}(\rho \oplus \rho') = \mathfrak{f}(\rho) \mathfrak{f}(\rho')$ and $\mathfrak{f}(\rho^\vee) = \mathfrak{f}(\rho)$.
3. With the notation of Theorem 6.3.3, part 2, $\mathfrak{f}(\mathrm{Inf}\, \rho) = \mathfrak{f}(\rho)$, where the right side is computed for $L'/F$.
4. With the notation of Theorem 6.3.3, part 3, $\mathfrak{f}(\mathrm{Ind}_H^G \psi) = \mathfrak{d}_{M/F}^{\dim \psi} \, N_{M/F}(\mathfrak{f}(\psi))$, where $\mathfrak{d}_{M/F}$ is the relative discriminant.
5. Let $\chi$ be a character of $G$ of dimension one. Then $f(\chi, \mathfrak{p})$ is the smallest integer $n \ge 0$ such that $\chi$ is trivial on $D^n$. It is the conductor $a(\chi_\mathfrak{p})$ of Definition 4.2.1, where $\chi_\mathfrak{p}$ is $\chi|_D$ viewed as a character of the Weil group of $F_\mathfrak{p}$.

Lean: not stated yet

*Proof.* The integrality in part 1 is a theorem of Artin. Its proof constructs a representation of $D$, the Artin representation, whose inner product with $\chi$ is $f(\chi, \mathfrak{p})$. See [Ser79], Chapter VI, Section 2. If $\mathfrak{p}$ is tame, then $G_1 = 1$ and only the term $i = 0$ remains. In part 2 the first claim is clear. For the second, the argument of Remark 6.1.6 gives $(V^\vee)^{G_i} \cong (V^{G_i})^\vee$, so the codimensions agree. For part 3, let $N' = D \cap N$. By Lemma 6.3.1 the decomposition group of $\mathfrak{P}' = \mathfrak{P} \cap L'$ is $D/N'$. Herbrand's theorem, [Ser79], Chapter IV, Section 3, says $(D/N')^v = D^v N'/N'$ for all $v$. So $\mathrm{Inf}\, \rho$ and $\rho$ have the same spaces $V^{D^v}$, and (6.4.1) gives the claim. Part 4 is in [Ser79], Chapter VI, Section 2, and in [Neu99], Chapter VII, Section 11. Its proof combines a local form of Mackey's formula with the formula for the different in a tower. For part 5, by part 3 we may replace $D$ by $D / \ker \chi$, which is abelian. By the theorem of Hasse and Arf, [Ser79], Chapter V, the jumps of the upper filtration of an abelian group are integers. If $\chi$ is unramified, both sides are $0$. Otherwise there is a largest $t$ with $\chi(D^t) \ne 1$. It is an integer, $\chi$ is nontrivial on $D^v$ for $-1 \le v \le t$, and $\chi$ is trivial on $D^v$ for $v > t$. By (6.4.1), $f(\chi, \mathfrak{p}) = t + 1$, and $t + 1$ is the smallest integer $n$ with $\chi(D^n) = 1$. The upper ramification groups of the Weil group map onto the $D^n$, again by Herbrand's theorem, so this is $a(\chi_\mathfrak{p})$. $\square$

**Corollary 6.4.3 (the conductor-discriminant formula).** Let $H \subset G$ and $M = L^H$. Then $\mathfrak{d}_{M/F} = \mathfrak{f}(\mathrm{Ind}_H^G \mathbf{1}_H)$. If $G$ is abelian, then $\mathfrak{d}_{L/F} = \prod_\chi \mathfrak{f}(\chi)$, the product over the characters of $G$.

Lean: not stated yet

*Proof.* Apply Proposition 6.4.2, part 4, to $\psi = \mathbf{1}_H$, whose conductor is $\mathcal{O}_M$. If $G$ is abelian, then $\mathrm{Ind}_1^G \mathbf{1} = r_G$ is the sum of all the characters of $G$, each once, and part 2 gives the product formula. $\square$

For a quadratic field $M = \mathbb{Q}(\sqrt{D})$ with discriminant $D$, the corollary says that the nontrivial character of $\mathrm{Gal}(M/\mathbb{Q})$ has conductor $|D|\mathbb{Z}$. For the field $K = \mathbb{Q}(\sqrt[3]{2})$ of Example 6.3.5 it gives $\mathfrak{f}(\rho) = \mathfrak{d}_{K/\mathbb{Q}} = 108\mathbb{Z}$, because $d_K = -108$.

### Gamma factors

Let $v$ be an infinite place of $F$ and $w$ a place of $L$ above $v$. Its decomposition group $D_w = \{\sigma \in G : \sigma w = w\}$ is $\mathrm{Gal}(L_w/F_v)$, a group of order 1 or 2. If $v$ is real and $w$ is complex, $D_w$ is generated by the complex conjugation $c_w$. In the other cases we put $c_w = 1$. For $\tau \in G$, $c_{\tau w} = \tau c_w \tau^{-1}$. Recall $\Gamma_\mathbb{R}(s) = \pi^{-s/2} \Gamma(s/2)$ and $\Gamma_\mathbb{C}(s) = 2(2\pi)^{-s} \Gamma(s) = \Gamma_\mathbb{R}(s) \Gamma_\mathbb{R}(s + 1)$, as in Chapter 5.

**Definition 6.4.4 (gamma factors and the completed $L$-function).** Let $\rho : G \to GL(V)$ have dimension $n$. For a real place $v$, let $n_v^+$ and $n_v^-$ be the dimensions of the eigenspaces of $\rho(c_w)$ for the eigenvalues $+1$ and $-1$. The *gamma factor* of $\rho$ at an infinite place $v$ is
$$\Gamma_v(s, \rho) = \Gamma_\mathbb{R}(s)^{n_v^+} \Gamma_\mathbb{R}(s + 1)^{n_v^-} \text{ if } v \text{ is real}, \qquad \Gamma_v(s, \rho) = \Gamma_\mathbb{C}(s)^n \text{ if } v \text{ is complex}.$$
Let $\Gamma_\infty(s, \rho) = \prod_{v \mid \infty} \Gamma_v(s, \rho)$. The *completed $L$-function* is $\Lambda(s, \rho) = \Gamma_\infty(s, \rho) L(s, \rho)$, and we put $A(\rho) = |d_F|^n N(\mathfrak{f}(\rho))$.

The numbers $n_v^\pm$ do not depend on $w$, because the complex conjugations above $v$ are conjugate. In terms of the character, $n_v^\pm = (\chi(1) \pm \chi(c_w))/2$. So the definitions extend to virtual characters, and $\Gamma_\infty$ and $A$ are multiplicative in $\chi$. For the trivial representation, $\Gamma_\infty(s, \mathbf{1}) = \Gamma_\mathbb{R}(s)^{r_1} \Gamma_\mathbb{C}(s)^{r_2}$ and $A(\mathbf{1}) = |d_F|$, where $r_1$ and $r_2$ are the numbers of real and complex places of $F$. So $\Lambda(s, \mathbf{1})$ is the function $\Lambda_F(s)$ of Corollary 5.4.8. The function $\Gamma_\infty(s, \rho)$ has no zeros. Its poles are at the integers $s \le 0$.

**Proposition 6.4.5 (the formal properties of $\Gamma_\infty$ and $A$).** The functions $\rho \mapsto \Gamma_\infty(s, \rho)$ and $\rho \mapsto A(\rho)$ are multiplicative in direct sums and invariant under inflation. In the situation of Theorem 6.3.3, part 3,
$$\Gamma_\infty(s, \mathrm{Ind}_H^G \psi) = \Gamma_\infty(s, \psi), \qquad A(\mathrm{Ind}_H^G \psi) = A(\psi),$$
where the right sides are computed for $L/M$. Hence $\Lambda(s, \mathrm{Ind}_H^G \psi) = \Lambda(s, \psi)$.

Lean: not stated yet

*Proof.* Multiplicativity is clear. Under inflation from $L' = L^N$, the image of $c_w$ in $G/N$ is the complex conjugation $c_{w'}$ of the place $w'$ of $L'$ below $w$, or $1$ if $w'$ is real. So the numbers $n_v^\pm$ agree. Proposition 6.4.2, part 3, treats $A$.

For induction let $v$ be an infinite place of $F$, $w \mid v$, and $D = D_w$. The argument in the proof of Theorem 6.3.3 shows that $g \mapsto u = g^{-1} w \cap M$ is a bijection from $D \backslash G / H$ onto the set of places $u$ of $M$ above $v$. Let $D_g = D \cap gHg^{-1}$. Conjugation by $g$ maps the decomposition group of $g^{-1}w$ in $L/M$ onto $D_g$. If $D_g = D$, then $u$ is real or $v$ is complex. The summand $\mathrm{Ind}_{D_g}^D W_g = W_g$ of Mackey's formula then contributes the gamma factor of $\psi$ at $u$. If $D_g \ne D$, then $D$ has order $2$, $D_g = 1$, and $u$ is complex. The summand is $W_g \otimes \mathbb{C}[D]$, on which $c_w$ has the eigenvalues $+1$ and $-1$ with multiplicity $\dim \psi$ each. It contributes $(\Gamma_\mathbb{R}(s) \Gamma_\mathbb{R}(s + 1))^{\dim \psi} = \Gamma_\mathbb{C}(s)^{\dim \psi} = \Gamma_u(s, \psi)$. This proves the identity for $\Gamma_\infty$.

For $A$ we use Proposition 6.4.2, part 4, and the formula $|d_M| = |d_F|^{[M : F]} N_{F/\mathbb{Q}}(\mathfrak{d}_{M/F})$ for the discriminant in a tower, [Neu99], Chapter III, Section 2. With $m = \dim \psi$, so that $\dim \mathrm{Ind}_H^G \psi = [M : F] m$,
$$A(\mathrm{Ind}_H^G \psi) = |d_F|^{[M : F] m} N_{F/\mathbb{Q}}\big(\mathfrak{d}_{M/F}^m N_{M/F} \mathfrak{f}(\psi)\big) = \big(|d_F|^{[M:F]} N_{F/\mathbb{Q}} \mathfrak{d}_{M/F}\big)^m N_{M/\mathbb{Q}} \mathfrak{f}(\psi) = |d_M|^m N(\mathfrak{f}(\psi)) = A(\psi).$$
The last claim follows from Theorem 6.3.3, part 3. $\square$

### The functional equation

**Theorem 6.4.6 (the functional equation of Artin $L$-functions).** Let $\rho$ be a representation of $G$, or more generally a virtual character.
1. The function $L(s, \rho)$ extends to a meromorphic function on $\mathbb{C}$.
2. There is a constant $W(\rho)$, the *Artin root number*, such that
$$\Lambda(s, \rho) = \varepsilon(s, \rho) \Lambda(1 - s, \rho^\vee), \qquad \varepsilon(s, \rho) = W(\rho) A(\rho)^{1/2 - s}.$$
3. $W(\rho^\vee) = \overline{W(\rho)}$ and $|W(\rho)| = 1$. If the character of $\rho$ is real, then $W(\rho) = \pm 1$.

Lean: not stated yet

Section 6.6 proves the theorem with Brauer's induction theorem. For a character of dimension one it is Hecke's theorem, by Section 6.5. For $\rho = \mathbf{1}$ it is Corollary 5.4.8 with $W(\mathbf{1}) = 1$. The root number is determined by the functional equation, because $\Lambda(s, \rho)$ is not identically zero. By Proposition 6.4.5 and Theorem 6.3.3 the functional equation is compatible with sums, inflation and induction. So $W$ is multiplicative, invariant under inflation, and $W(\mathrm{Ind}_H^G \psi) = W(\psi)$.

**Remark 6.4.7 (local root numbers).** The root number of Theorem 6.4.6 is a product of local factors. The theorem of Langlands and Deligne, Theorem 4.3.8, attaches an $\varepsilon$-factor to every representation of the Weil group of a local field. It is multiplicative and compatible with induction in dimension zero, like the global root number. The global factor $\varepsilon(s, \rho)$ is the product over all places $v$ of the local factors $\varepsilon(\rho_v^\vee, s, \psi_v)$ of Theorem 4.3.8, see [Tat79], Section 3. Here $\rho_v^\vee$ is the restriction of $\rho^\vee$ to the decomposition group at $v$, viewed as a representation of the Weil group of $F_v$, and $\psi = \prod_v \psi_v$ is the additive character of Chapter 5. The dual appears because of Remark 6.1.6: the arithmetic factors of $\rho$ are the geometric factors of $\rho^\vee$. The global theorem does not need the local constants: the proof in Section 6.6 obtains $W(\rho)$ as a product of Hecke root numbers. The local constants are needed to compute $W(\rho)$ from local data and to state the local Langlands correspondence for $GL_n$.
