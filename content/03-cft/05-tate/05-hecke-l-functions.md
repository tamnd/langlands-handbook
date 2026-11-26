---
title: Hecke L-functions
nodes: [LG6NN4B43V]
sources: [CF67, Neu99, Tat79]
status: checked
drafted_by: writer
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## Hecke L-functions

This section combines the local theory of Section 5.2 with the global theory of Section 5.4. A factorizable function made of the standard local functions turns the global zeta integral into the completed $L$-function, up to a constant. Theorem 5.4.7 then gives Hecke's theorem, with the $\varepsilon$-factor as a product of local factors. The proof is that of [CF67], Chapter XV. We keep the notation of Sections 5.3 and 5.4. Let $\chi$ be a Hecke character, $\chi = \chi_0 |\cdot|_\mathbb{A}^\sigma$ with $\chi_0$ unitary, as in Proposition 5.4.2.

### The $L$-function and the $\varepsilon$-factor

**Definition 5.5.1 (Hecke $L$-functions).** Let $\chi$ be a Hecke character.
1. The *conductor* of $\chi$ is the ideal $\mathfrak{f}_\chi = \prod_{v \nmid \infty} \mathfrak{p}_v^{a(\chi_v)}$ of $\mathcal{O}_F$. Its norm is $N(\mathfrak{f}_\chi) = \prod_v q_v^{a(\chi_v)}$.
2. The *$L$-function* of $\chi$ is $L(s, \chi) = \prod_{v \nmid \infty} L(\chi_v, s)$ for $\mathrm{Re}(s) > 1 - \sigma$. The *archimedean factor* is $L_\infty(s, \chi) = \prod_{v \mid \infty} L(\chi_v, s)$, and the *completed $L$-function* is $\Lambda(s, \chi) = L_\infty(s, \chi) L(s, \chi)$.
3. The *$\varepsilon$-factor* of $\chi$ is $\varepsilon(s, \chi) = \prod_v \varepsilon(\chi_v, s, \psi_v)$, with the standard characters $\psi_v$ of Section 5.3. For a unitary $\chi$ the *root number* is $W(\chi) = \varepsilon(1/2, \chi)$.

The product in part 1 is finite by Proposition 5.4.2. The product in part 2 converges by Proposition 5.4.6. The product in part 3 is finite, because $\varepsilon(\chi_v, s, \psi_v) = 1$ when $v$ is finite, $\chi_v$ is unramified and $d_v = 0$, by Proposition 5.2.3. The factors $L(\chi_v, s)$ are those of Definition 5.2.2. At a finite place $v$ where $\chi$ is unramified, the number $\chi_v(\varpi_v)$ does not depend on the choice of $\varpi_v$. So $\mathfrak{p}_v \mapsto \chi_v(\varpi_v)$ extends to a character $\chi^*$ of the group of fractional ideals prime to $\mathfrak{f}_\chi$, and
$$L(s, \chi) = \prod_{\mathfrak{p} \nmid \mathfrak{f}_\chi} \big(1 - \chi^*(\mathfrak{p}) N(\mathfrak{p})^{-s}\big)^{-1} = \sum_{(\mathfrak{a}, \mathfrak{f}_\chi) = 1} \chi^*(\mathfrak{a}) N(\mathfrak{a})^{-s}.$$
This is the $L$-series of Hecke. For $\chi = 1$ we get $L(s, 1) = \zeta_F(s)$ and $\Lambda(s, 1) = \Lambda_F(s)$. Since $a(\chi_v) = a(\chi_{0,v})$, the conductors of $\chi$ and $\chi_0$ are equal.

**Proposition 5.5.2 (the global $\varepsilon$-factor).** Let $\chi = \chi_0 |\cdot|_\mathbb{A}^\sigma$ be a Hecke character.
1. $\varepsilon(s, \chi) = W(\chi_0) \big(|d_F| \, N(\mathfrak{f}_\chi)\big)^{1/2 - s - \sigma}$.
2. $|W(\chi_0)| = 1$.
3. $\varepsilon(s, \chi) \, \varepsilon(1 - s, \chi^{-1}) = 1$.
4. If $\psi$ is replaced by $\psi_a$ with $a \in F^\times$, and the self-dual measures are changed accordingly, then $\varepsilon(s, \chi)$ does not change.

Lean: not stated yet

*Proof.* By Corollary 5.2.9, $\varepsilon(\chi_v, s, \psi_v) = \varepsilon(\chi_{0,v}, s + \sigma, \psi_v)$ at each place. At a finite place, part 3 of Theorem 5.2.7 gives
$$\varepsilon(\chi_{0,v}, s + \sigma, \psi_v) = \varepsilon(\chi_{0,v}, 1/2, \psi_v) \, q_v^{(a(\chi_v) + d_v)(1/2 - s - \sigma)}.$$
At an infinite place the factor does not depend on $s$. The product of the factors $q_v^{a(\chi_v) + d_v}$ is $N(\mathfrak{f}_\chi) \, |d_F|$, by Section 5.3. The product of the values at $1/2$ is $W(\chi_0)$. This proves part 1. Part 2 follows from Corollary 5.2.9. Part 3 follows from part 4 of Theorem 5.2.7, because $\prod_v \chi_v(-1) = \chi(-1) = 1$. For part 4, Proposition 5.2.10 at each place gives the factor $\prod_v \chi_v(a) |a|_v^{s - 1/2} = \chi(a) |a|_\mathbb{A}^{s - 1/2}$. It is 1, because $\chi$ is trivial on $F^\times$ and $|a|_\mathbb{A} = 1$ by the product formula. $\square$

By Proposition 5.3.2, every nontrivial character of $\mathbb{A}_F / F$ is $\psi_a$ with $a \in F^\times$. So part 4 says that $\varepsilon(s, \chi)$ does not depend on the choice of a nontrivial character of $\mathbb{A}_F / F$. The local factors depend on this choice, but their product does not.

### Hecke's theorem

**Theorem 5.5.3 (Hecke's functional equation).** Let $F$ be a number field and let $\chi = \chi_0 |\cdot|_\mathbb{A}^\sigma$ be a Hecke character of $F$, with $\chi_0$ unitary.
1. The function $\Lambda(s, \chi)$ on $\mathrm{Re}(s) > 1 - \sigma$ extends to a meromorphic function on $\mathbb{C}$.
2. As meromorphic functions,
$$\Lambda(s, \chi) = \varepsilon(s, \chi) \, \Lambda(1 - s, \chi^{-1}), \qquad \varepsilon(s, \chi) = W(\chi_0) \big(|d_F| \, N(\mathfrak{f}_\chi)\big)^{1/2 - s - \sigma},$$
and $|W(\chi_0)| = 1$.
3. If $\chi$ is not of the form $|\cdot|_\mathbb{A}^{s_0}$, then $\Lambda(s, \chi)$ is entire. If $\chi = |\cdot|_\mathbb{A}^{s_0}$ with $s_0 \in \mathbb{C}$, then $\Lambda(s, \chi)$ is holomorphic except for simple poles at $s = -s_0$ and $s = 1 - s_0$.

Node: LG6NN4B43V · Lean: `Langlands.HeckeFunctionalEquation`

*Proof.* For each place $v$ let $f_v = f_{\chi_v}$ and $c_v = c_{\chi_v}$ be the standard function and the constant of Propositions 5.2.3 to 5.2.6. At a finite place where $\chi_v$ is unramified, $f_v = 1_{\mathcal{O}_v}$, and $c_v = 1$ if also $d_v = 0$. So $f = \otimes_v f_v$ lies in $\mathcal{S}(\mathbb{A}_F)$, and $c = \prod_v c_v$ is a finite product of nonzero numbers. By Proposition 5.4.6 and (5.2.1),
$$Z(f, \chi, s) = c \, \Lambda(s, \chi), \qquad \mathrm{Re}(s) > 1 - \sigma.$$
The transform is $\hat f = \otimes_v \hat f_v$. Proposition 5.4.6 for $\chi^{-1}$, whose exponent is $-\sigma$, and (5.2.1) give
$$Z(\hat f, \chi^{-1}, 1 - s) = c \, \varepsilon(s, \chi) \, \Lambda(1 - s, \chi^{-1}), \qquad \mathrm{Re}(s) < -\sigma.$$
Here we used that $\hat f_v = 1_{\mathcal{O}_v}$ and $\varepsilon(\chi_v, s, \psi_v) = 1$ at almost all places.

By Theorem 5.4.7, $Z(f, \chi, s)$ is meromorphic on $\mathbb{C}$. So $\Lambda(s, \chi) = c^{-1} Z(f, \chi, s)$ is the continuation of $\Lambda(s, \chi)$, which proves part 1. The function $\varepsilon(s, \chi)$ is entire and has no zeros. So $c^{-1} \varepsilon(s, \chi)^{-1} Z(\hat f, \chi^{-1}, 1 - s)$ is a meromorphic function on $\mathbb{C}$ that equals $\Lambda(1 - s, \chi^{-1})$ for $\mathrm{Re}(s) < -\sigma$. It is the continuation of $\Lambda(1 - s, \chi^{-1})$, and it agrees with the continuation given by part 1 for $\chi^{-1}$, by uniqueness. Part 2 of Theorem 5.4.7 now gives
$$c \, \Lambda(s, \chi) = Z(f, \chi, s) = Z(\hat f, \chi^{-1}, 1 - s) = c \, \varepsilon(s, \chi) \, \Lambda(1 - s, \chi^{-1}).$$
Proposition 5.5.2 gives the formula for $\varepsilon(s, \chi)$ and $|W(\chi_0)| = 1$. This proves part 2.

For part 3, if $\chi$ is not trivial on $J_F^1$, then $Z(f, \chi, s)$ is entire by Theorem 5.4.7, and so is $\Lambda(s, \chi)$. By part 3 of Proposition 5.4.2 this is the case exactly when $\chi$ is not a power of $|\cdot|_\mathbb{A}$. Now let $\chi = |\cdot|_\mathbb{A}^{s_0}$. Then $\chi_v = |\cdot|_v^{s_0}$ at every place. So $\chi_v$ is unramified at every finite place, its parameters are $a_v = 0$ or $n_v = 0$ at the infinite places, and $f_v$ is $1_{\mathcal{O}_v}$, $e^{-\pi x^2}$ or $e^{-2\pi z \bar z}$. Thus $f(0) = 1$ and $\hat f(0) = \prod_v q_v^{-d_v/2} = |d_F|^{-1/2}$. By Theorem 5.4.7, $Z(f, \chi, s)$ is holomorphic outside $\{-s_0, 1 - s_0\}$, and its residues there are $-\kappa$ and $\kappa |d_F|^{-1/2}$. Both are nonzero by Proposition 5.4.4. So $\Lambda(s, \chi)$ has simple poles at both points. $\square$

For $\chi = |\cdot|_\mathbb{A}^{s_0}$ we have $\Lambda(s, \chi) = \Lambda_F(s + s_0)$, and the theorem is Corollary 5.4.8 shifted by $s_0$. The root number is then $W(|\cdot|_\mathbb{A}^{i\tau}) = |d_F|^{-i\tau}$ for $s_0 = \sigma + i\tau$, by Proposition 5.2.3. So $W(\chi_0)$ need not be 1 when $\chi_0$ is a power of the norm. For a unitary $\chi$ we have $\sigma = 0$ and $\chi^{-1} = \bar\chi$, and the theorem reads $\Lambda(s, \chi) = W(\chi) (|d_F| \, N(\mathfrak{f}_\chi))^{1/2 - s} \Lambda(1 - s, \bar\chi)$. This is the form of [Neu99], Chapter VII, Theorem 8.5, up to the normalization of the completed $L$-function.

**Remark 5.5.4 (the Lean statement).** The Lean project states Theorem 5.5.3 as `Langlands.HeckeFunctionalEquation`, in the file `Langlands/Statements/Hecke.lean`. It is stated and not proved. Theorem 5.5.10 proves its conclusion for the trivial character, and Theorem 5.5.14 proves it for the characters $|\cdot|_\mathbb{A}^{s_0}$. Theorem 5.5.33 proves it for the characters of class group type. Theorems 5.5.40 and 5.5.42 prove it for the twists of these characters by a power of the norm. The file writes $K$ for the number field and `ideleNorm`, or $\|x\|$, for $|x|_\mathbb{A}$. A Hecke character is a continuous homomorphism from the idele class group to $\mathbb{C}^\times$, as in Definition 5.4.1. The finite $L$-function is the product over all finite places of the local factors $(1 - \chi_v(\varpi_v) N(v)^{-s})^{-1}$ at the unramified places and $1$ at the other places, with a uniformizer $\varpi_v \in F$ chosen once. The archimedean factor is the product of $\Gamma_\mathbb{R}(s + t_v + n_v)$ over the real places and $\Gamma_\mathbb{C}(s + t_v + |n_v|/2)$ over the complex places, as in Definition 5.2.2. The Lean statement asserts that there is a real $\sigma$ with $|\chi(x)| = \|x\|^\sigma$, as in Proposition 5.4.2. It differs from Theorem 5.5.3 in these points.
1. The archimedean parameters are hypotheses. The statement takes integers $n_v$ and complex numbers $t_v$ with $\chi_v(x) = (\iota(x)/|\iota(x)|)^{n_v} |\iota(x)|^{m_v t_v}$, where $\iota : F_v \to \mathbb{C}$ is the embedding, $m_v$ is 1 at a real place and 2 at a complex place, and $n_v \in \{0, 1\}$ at a real place. It takes a second family $(n'_v, t'_v)$ of parameters for $\chi^{-1}$. These are the parameters of Proposition 5.1.7. Their existence is the separate statement `Langlands.ArchimedeanParametersExist`, which is also stated and not proved. Without it, the theorem would say nothing about a character for which no parameters are given.
2. The continuation is a meromorphic function that is equal to the Euler product on a half plane. The statement asserts that there are functions $\Lambda$ and $\Lambda'$, meromorphic on $\mathbb{C}$, with $\Lambda(s) = \Lambda(s, \chi)$ for $\mathrm{Re}(s) > 1 - \sigma$ and $\Lambda'(s) = \Lambda(s, \chi^{-1})$ for $\mathrm{Re}(s) > 1 + \sigma$. It does not define the continuation. By the identity theorem these functions are unique outside a discrete set. The functional equation is asserted for every $s \in \mathbb{C}$. A Lean function has a value at a pole too, and at a pole the identity is a condition on these values.
3. The root number is not identified with the product of the local root numbers. The statement asserts that there is $W \in \mathbb{C}$ with $|W| = 1$ and $\Lambda(s) = W (|d_F| N(\mathfrak{f}_\chi))^{1/2 - s - \sigma} \Lambda'(1 - s)$. It does not say that $W = W(\chi_0) = \prod_v \varepsilon(\chi_{0,v}, 1/2, \psi_v)$. The number $W$ is determined by $\Lambda$ and $\Lambda'$, because $\Lambda'$ is not identically 0. So Theorem 5.5.3 identifies it, but the Lean statement does not give a way to compute it.
4. The statement on the poles is a disjunction. Either $\Lambda$ is analytic at every point, or $\chi = \|\cdot\|^{s_0}$ for some $s_0$, $\Lambda$ is analytic outside $\{-s_0, 1 - s_0\}$, and $\Lambda$ has order $-1$ at both points. The disjunction by itself does not exclude the first case when $\chi$ is a power of the norm. Part 3 of Theorem 5.5.3 and the uniqueness of the continuation exclude it.

The local factors at the finite places, the conductor $\mathfrak{f}_\chi$ and the condition $\mathrm{Re}(s) > 1 - \sigma$ agree with Definition 5.5.1. The Lean file also notes that the theorem in the form of [Neu99], Chapter VII, Theorem 8.5, is the case of a unitary $\chi$, where $\sigma = 0$ and $\chi^{-1} = \bar\chi$.

### Examples

**Example 5.5.5 (the Riemann zeta function).** Let $F = \mathbb{Q}$ and $\chi = 1$. Then $d_\mathbb{Q} = 1$, $\mathfrak{f}_\chi = \mathbb{Z}$, and every local $\varepsilon$-factor is 1, so $W(1) = 1$. Theorem 5.5.3 gives $\Lambda(s) = \Lambda(1 - s)$ for $\Lambda(s) = \Gamma_\mathbb{R}(s) \zeta(s) = \pi^{-s/2} \Gamma(s/2) \zeta(s)$. This is Riemann's functional equation. Here $h = 1$, $R = 1$, $w = 2$ and $r_1 = 1$, so $\kappa = 1$ by Proposition 5.4.4. In the proof of Corollary 5.4.8 we have $Z(f, 1, s) = \Lambda(s)$, so the residues of $\Lambda$ are $1$ at $s = 1$ and $-1$ at $s = 0$. Near $s = 0$ we have $\Gamma_\mathbb{R}(s) = 2/s + O(1)$, so $\zeta(0) = -1/2$.

**Example 5.5.6 (Dirichlet $L$-functions).** Let $\eta$ be a primitive Dirichlet character modulo $N \ge 1$, and let $a \in \{0, 1\}$ with $\eta(-1) = (-1)^a$. Write $N = \prod_\ell \ell^{n_\ell}$ and $\eta = \prod_\ell \eta_\ell$, where $\eta_\ell$ is a character of $(\mathbb{Z}/\ell^{n_\ell})^\times$. Each $\eta_\ell$ is primitive. By Example 3.4.8 of Volume 1, each idele of $\mathbb{Q}$ is in a unique way the product of an element of $\mathbb{Q}^\times$ and an element of $\mathbb{R}_{>0} \times \hat{\mathbb{Z}}^\times$. Let $\chi$ be the Hecke character that is trivial on $\mathbb{Q}^\times$ and on $\mathbb{R}_{>0}$, and that is $u \mapsto \eta(u \bmod N)^{-1}$ on $\hat{\mathbb{Z}}^\times$. We compute its components.
1. Let $p \nmid N$. The group $\mathbb{Z}_p^\times$ maps to 1 in $(\mathbb{Z}/N)^\times$, so $\chi_p$ is unramified. The idele with $p$ at the place $p$ and 1 elsewhere is the product of the principal idele $p$ and the idele with $p^{-1}$ at $\infty$ and at all $\ell \ne p$, and 1 at $p$. The second factor is in $\mathbb{R}_{>0} \times \hat{\mathbb{Z}}^\times$, and its image in $(\mathbb{Z}/N)^\times$ is $p^{-1}$. So $\chi_p(p) = \eta(p^{-1})^{-1} = \eta(p)$.
2. In the same way, $-1$ at $\infty$ is the product of the principal idele $-1$ and the idele with $-1$ at every finite place. So $\chi_\infty(-1) = \eta(-1)^{-1} = (-1)^a$, and $\chi_\infty = \mathrm{sgn}^a$.
3. Let $\ell \mid N$. On $\mathbb{Z}_\ell^\times$ the character $\chi_\ell$ is $\eta_\ell^{-1}$, so $a(\chi_\ell) = n_\ell$ by Example 4.1.6. As in item 1, $\chi_\ell(\ell) = \prod_{p \ne \ell} \eta_p(\ell)$, where $p$ runs over the primes dividing $N$.

Thus $\mathfrak{f}_\chi = N\mathbb{Z}$, $L(s, \chi) = \prod_{p \nmid N} (1 - \eta(p) p^{-s})^{-1} = L(s, \eta)$, and $\Lambda(s, \chi) = \Gamma_\mathbb{R}(s + a) L(s, \eta)$. The character $\chi^{-1}$ is the character of $\bar\eta$. Theorem 5.5.3 gives
$$\Gamma_\mathbb{R}(s + a) L(s, \eta) = W(\chi) N^{1/2 - s} \, \Gamma_\mathbb{R}(1 - s + a) L(1 - s, \bar\eta).$$
We compute $W(\chi)$. At $p \nmid N$ the local factor is 1. At $\infty$ it is $(-i)^a$, by Proposition 5.2.5. At $\ell \mid N$, Proposition 5.2.4 with $d = 0$ and $\varpi = \ell$ gives $\varepsilon(\chi_\ell, 1/2, \psi_\ell) = \chi_\ell(\ell)^{n_\ell} \ell^{-n_\ell/2} \tau(\eta_\ell)$, where $\tau(\eta_\ell) = \sum_{u \bmod \ell^{n_\ell}} \eta_\ell(u) e^{2\pi i u / \ell^{n_\ell}}$ is the classical Gauss sum. By item 3,
$$\prod_{\ell \mid N} \chi_\ell(\ell)^{n_\ell} = \prod_{\ell} \prod_{p \ne \ell} \eta_p(\ell^{n_\ell}) = \prod_p \eta_p(N / p^{n_p}).$$
The Chinese remainder theorem gives $\tau(\eta) = \prod_p \eta_p(N / p^{n_p}) \tau(\eta_p)$ for $\tau(\eta) = \sum_{u \bmod N} \eta(u) e^{2\pi i u / N}$, see Exercise 9. Thus
$$W(\chi) = \frac{(-i)^a \tau(\eta)}{\sqrt N} = \frac{\tau(\eta)}{i^a \sqrt N}.$$
This is the classical root number of $L(s, \eta)$. The local component $\chi_\ell$ is not the character $\chi_{\eta_\ell}$ of Example 4.1.6. On $\mathbb{Z}_\ell^\times$ it is $\chi_{\bar\eta_\ell}$. For $N = \ell^n$ we have $\chi_\ell(\ell) = 1$, so $\chi_\ell = \chi_{\bar\eta}$, and the factor at $\ell$ agrees with Exercise 7 of Chapter 4.

**Remark 5.5.7 (finite order and the Galois side).** A Hecke character of finite order is trivial on the connected component of $C_F$, so it factors through a ray class group. Through global class field theory it then becomes a character of a Galois group, and $L(s, \chi)$ becomes an Artin $L$-function of dimension one. The factorization $\varepsilon(s, \chi) = \prod_v \varepsilon(\chi_v, s, \psi_v)$ is the model for the general theory of local constants. Langlands and Deligne proved that the global $\varepsilon$-factor of every Artin $L$-function is a product of local factors with the properties of Section 5.2, see [Tat79], Section 3. For the functional equation of Hecke with theta series, see [Neu99], Chapter VII, Sections 6 to 8.

### The trivial character in Lean

The Lean project proves the conclusion of `Langlands.HeckeFunctionalEquationAt` for the trivial character of each number field. The proof does not use Theorem 5.4.7. It uses the theta functions of Section 5.3, as Hecke did, and Theorem 5.3.34 and Proposition 5.3.36 do most of the work. This subsection gives the remaining steps. They join the function $\xi_F$ to the objects of the Lean statement. Let $\mathbf{1}$ be the trivial Hecke character of $F$.

**Lemma 5.5.8 (the data of the trivial character).** Let $F$ be a number field.
1. Let $v$ be an infinite place of $F$. The pair $(n_v, t_v)$ is a pair of parameters of $\mathbf{1}$ at $v$, in the sense of item 1 of Remark 5.5.4, if and only if $n_v = 0$ and $t_v = 0$.
2. For these parameters the archimedean factor of $\mathbf{1}$ is $L_\infty(s, \mathbf{1}) = 2^{r_2} \, \Gamma_F(s)$, with $\Gamma_F$ as in Remark 5.3.13.
3. The conductor of $\mathbf{1}$ is $\mathcal{O}_F$, and the local factor of $\mathbf{1}$ at a finite place $v$ is $(1 - N(\mathfrak{p}_v)^{-s})^{-1}$.

Lean: `Langlands.Tate.isArchimedeanParameter_one_iff`, `Langlands.Tate.gammaFactor_zero`, `Langlands.HeckeCharacter.conductor_one`, `Langlands.Tate.localFactor_one`

*Proof.* (1) The parameters $n_v = 0$ and $t_v = 0$ give the trivial character of $F_v^\times$. For the converse, let $\iota$ be the embedding of item 1 of Remark 5.5.4. For a real number $y > 0$ the formula gives $1 = \mathbf{1}_v(y) = y^{m_v t_v} = e^{m_v t_v \log y}$. Since $\log y$ takes all real values, the function $x \mapsto e^{m_v t_v x}$ is the constant $1$ on $\mathbb{R}$, so $t_v = 0$. Then $(\iota(x)/|\iota(x)|)^{n_v} = 1$ for each $x \in F_v^\times$. At a real place $\iota(-1) = -1$, so $(-1)^{n_v} = 1$, and $n_v = 0$ because $n_v \in \{0, 1\}$. At a complex place $\iota(x)/|\iota(x)|$ takes each value $z$ with $|z| = 1$. The character $z \mapsto z^{n_v}$ of the circle is trivial only for $n_v = 0$.

(2) With $n_v = t_v = 0$, the factors of Remark 5.5.4 are $\Gamma_\mathbb{R}(s)$ at the real places and $\Gamma_\mathbb{C}(s)$ at the complex places. Their product is $\Gamma_\mathbb{R}(s)^{r_1} \Gamma_\mathbb{C}(s)^{r_2} = 2^{r_2} \Gamma_\mathbb{R}(s)^{r_1} (\Gamma_\mathbb{C}(s)/2)^{r_2} = 2^{r_2} \Gamma_F(s)$.

(3) The character $\mathbf{1}_v$ is trivial on $\mathcal{O}_v^\times$ at each finite place, so $a(\mathbf{1}_v) = 0$, and the conductor is the product of the ideals $\mathfrak{p}_v^0$. At each finite place $\mathbf{1}_v$ is unramified and $\mathbf{1}_v(\varpi_v) = 1$, so the local factor is $(1 - N(\mathfrak{p}_v)^{-s})^{-1}$. $\square$

**Proposition 5.5.9 (the Euler product of $\zeta_F$).** Let $\mathrm{Re}(s) > 1$. The product of the factors $(1 - N(\mathfrak{p})^{-s})^{-1}$ over the nonzero prime ideals $\mathfrak{p}$ of $\mathcal{O}_F$ converges unconditionally, and its value is $\zeta_F(s)$. So $L(s, \mathbf{1}) = \zeta_F(s)$.

Lean: `Langlands.Tate.hasProd_dedekindZeta`, `Langlands.Tate.finiteLFunction_one`

*Proof.* Put $\sigma = \mathrm{Re}(s)$. For a finite set $S$ of nonzero prime ideals, let $I(S)$ be the set of the nonzero ideals of $\mathcal{O}_F$ whose prime factors are all in $S$. For $\mathfrak{p} \in S$ we have $|N(\mathfrak{p})^{-s}| = N(\mathfrak{p})^{-\sigma} < 1$, so the geometric series $\sum_k N(\mathfrak{p})^{-ks}$ converges absolutely to $(1 - N(\mathfrak{p})^{-s})^{-1}$. The product of these series over $S$ is a sum over the families $(k_\mathfrak{p})_{\mathfrak{p} \in S}$. By the unique factorization of ideals, the map $(k_\mathfrak{p}) \mapsto \prod_\mathfrak{p} \mathfrak{p}^{k_\mathfrak{p}}$ is a bijection onto $I(S)$, and the norm is multiplicative. So
$$\prod_{\mathfrak{p} \in S} \big(1 - N(\mathfrak{p})^{-s}\big)^{-1} = \sum_{\mathfrak{a} \in I(S)} N(\mathfrak{a})^{-s}.$$
The series of $\zeta_F(\sigma)$ converges, and each nonzero ideal is in $I(S)$ for all $S$ that contain its prime factors. So the difference between $\zeta_F(s)$ and the sum over $I(S)$ is the sum over the ideals that are not in $I(S)$. Its absolute value is at most $\sum_{\mathfrak{a} \notin I(S)} N(\mathfrak{a})^{-\sigma}$, and this tends to $0$ along the directed set of the finite sets $S$. This is the unconditional convergence of the product. The last statement follows from part 3 of Lemma 5.5.8. $\square$

**Theorem 5.5.10 (Hecke's theorem for the trivial character).** Let $F$ be a number field, and put
$$\Lambda(s) = 2^{r_2} \, |d_F|^{-s/2} \, \xi_F(s), \qquad \Lambda'(u) = |d_F|^{1/2 - u} \, \Lambda(1 - u),$$
with $\xi_F$ as in Theorem 5.3.34.
1. The functions $\Lambda$ and $\Lambda'$ are meromorphic on $\mathbb{C}$.
2. For $\mathrm{Re}(s) > 1$, $\Lambda(s) = \Lambda'(s) = 2^{r_2} \, \Gamma_F(s) \, \zeta_F(s) = \Lambda(s, \mathbf{1})$.
3. For each $s \in \mathbb{C}$, $\Lambda(s) = |d_F|^{1/2 - s} \, \Lambda'(1 - s)$.
4. The function $\Lambda$ is holomorphic outside $\{0, 1\}$, and it has simple poles at $s = 0$ and $s = 1$.

So the conclusion of `Langlands.HeckeFunctionalEquationAt` holds for $\chi = \mathbf{1}$, with $\sigma = 0$, $W = 1$ and $s_0 = 0$.

Lean: `Langlands.Tate.heckeFunctionalEquationAt_one`

*Proof.* Let $h(s) = 2^{r_2} |d_F|^{-s/2}$. It is an entire function with no zeros. By Proposition 5.3.36, $\Lambda(s) = h E(s) + h F_0(s)/s + h F_1(s)/(s - 1)$, with entire numerators, $(h F_0)(0) \ne 0$ and $(h F_1)(1) \ne 0$. This gives part 4 and the part of part 1 for $\Lambda$. For $\Lambda'$ we substitute $1 - u$. Since $(1 - u) - 1 = -u$,
$$\Lambda(1 - u) = h E(1 - u) + \frac{-(h F_1)(1 - u)}{u} + \frac{-(h F_0)(1 - u)}{u - 1}.$$
The numerators are again entire, and we multiply by the entire function $|d_F|^{1/2 - u}$. So $\Lambda'$ is meromorphic on $\mathbb{C}$.

For part 2, let $\mathrm{Re}(s) > 1$. Part (2) of Theorem 5.3.34 gives $\Lambda(s) = 2^{r_2} |d_F|^{-s/2} |d_F|^{s/2} \Gamma_F(s) \zeta_F(s) = 2^{r_2} \Gamma_F(s) \zeta_F(s)$. Then $s \ne 0, 1$, and part (3) of Theorem 5.3.34 gives $\xi_F(1 - s) = \xi_F(s)$. So
$$\Lambda'(s) = 2^{r_2} \, |d_F|^{1/2 - s} \, |d_F|^{-(1 - s)/2} \, \xi_F(s) = 2^{r_2} \, |d_F|^{-s/2} \, \xi_F(s) = \Lambda(s).$$
By Lemma 5.5.8 and Proposition 5.5.9, $2^{r_2} \Gamma_F(s) \zeta_F(s) = L_\infty(s, \mathbf{1}) L(s, \mathbf{1}) = \Lambda(s, \mathbf{1})$.

For part 3, $|d_F|^{1/2 - s} \Lambda'(1 - s) = |d_F|^{1/2 - s} |d_F|^{s - 1/2} \Lambda(s) = \Lambda(s)$, because $|d_F| \ne 0$.

For the last statement, we compare with the Lean statement in Remark 5.5.4. The character $\mathbf{1}$ has $|\mathbf{1}(x)| = 1 = |x|_\mathbb{A}^0$, so $\sigma = 0$. The character $\mathbf{1}^{-1}$ is $\mathbf{1}$, and by part 1 of Lemma 5.5.8 both families of parameters are $0$. Part 2 gives the two identities on the half plane $\mathrm{Re}(s) > 1$. The conductor is $\mathcal{O}_F$ and $N(\mathcal{O}_F) = 1$, so part 3 is the functional equation with $W = 1$. For the poles we take the second case of the disjunction, with $s_0 = 0$, because $\mathbf{1}(x) = |x|_\mathbb{A}^0$. Part 4 gives the analyticity outside $\{0, 1\}$ and the order $-1$ at both points. $\square$

Part 3 holds for each $s$ by the definition of $\Lambda'$. The arithmetic content of the theorem is in part 2 for $\Lambda'$. It says that $\Lambda'$ is also the continuation of $\Lambda(s, \mathbf{1})$, and its proof needs the functional equation $\xi_F(1 - s) = \xi_F(s)$. Without part 2 for $\Lambda'$, the functional equation of the Lean statement would be true for each $\chi$ with a trivial choice of $\Lambda'$. This is why the Lean statement asks for both identities on half planes.

**Remark 5.5.11 (the Lean proof).** The files `Langlands/Tate/HeckeOne.lean`, `Langlands/Tate/DedekindEuler.lean` and `Langlands/Tate/HeckeTrivial.lean` prove Lemma 5.5.8, Proposition 5.5.9 and Theorem 5.5.10. The functions $\Lambda$ and $\Lambda'$ are `Langlands.Tate.heckeLambdaOne` and `Langlands.Tate.heckeLambdaOne'`. Part 2 is `Langlands.Tate.heckeLambdaOne_eq` and `Langlands.Tate.heckeLambdaOne'_eq`, and part 3 is `Langlands.Tate.heckeLambdaOne_eq_discr_cpow_mul`. In Proposition 5.5.9 the product is a `HasProd` of Mathlib over `IsDedekindDomain.HeightOneSpectrum`, which is the unconditional convergence of the proposition. The identity for a finite set $S$ is `Langlands.Tate.hasSum_supportedIn`, and the limit along the finite sets is the theorem of Tannery, `tendsto_tsum_of_dominated_convergence` of Mathlib, with the dominating series $\sum_\mathfrak{a} N(\mathfrak{a})^{-\sigma}$. The proof of part 1 of Lemma 5.5.8 is `Langlands.Tate.eq_zero_of_exp_mul_eq_one` and the two lemmas after it. All these theorems use only the standard axioms of Lean. The next subsection extends the proof to the characters $|\cdot|_\mathbb{A}^{s_0}$.

### The characters $|\cdot|_\mathbb{A}^{s_0}$ in Lean

Let $s_0 \in \mathbb{C}$. By the product formula the idele norm is trivial on $F^\times$, and it is continuous, so $\chi(x) = |x|_\mathbb{A}^{s_0}$ is a Hecke character. By part 3 of Theorem 5.5.3 these are the characters for which $\Lambda(s, \chi)$ has poles. This subsection proves the conclusion of `Langlands.HeckeFunctionalEquationAt` for each of them. The method is a translation by $s_0$ of the case $\chi = \mathbf{1}$. We first compute the norm of the ideles that have only one component different from $1$.

**Lemma 5.5.12 (the norm of a local idele).** Let $F$ be a number field, let $v$ be a place of $F$ and let $x \in F_v^\times$. Let $x^{(v)}$ be the idele with the component $x$ at $v$ and the component $1$ at each other place.
1. If $v$ is infinite, then $|x^{(v)}|_\mathbb{A} = |\iota(x)|^{m_v}$, with $\iota$ and $m_v$ as in item 1 of Remark 5.5.4.
2. If $v$ is finite, then $|x^{(v)}|_\mathbb{A} = |x|_v$, the normalized absolute value of $x$. In particular $|\varpi_v|_v = N(\mathfrak{p}_v)^{-1}$.
3. For each idele $x$, $|x|_\mathbb{A} > 0$.

Lean: `Langlands.Tate.ideleNorm_ofCompletion`, `Langlands.Tate.ideleNorm_ofAdicCompletion`, `Langlands.Tate.norm_localUniformizer`, `Langlands.Tate.ideleNorm_pos`

*Proof.* The idele norm is the product of the normalized absolute values of the components. For $x^{(v)}$ each factor at a place $w \ne v$ is $|1|_w = 1$, and this gives parts 1 and 2. The element $\varpi_v$ has valuation $1$ at $v$, so its normalized absolute value is $N(\mathfrak{p}_v)^{-1}$. For part 3, each component of an idele is not zero, and almost all components are units. So $|x|_\mathbb{A}$ is a finite product of positive numbers. $\square$

**Lemma 5.5.13 (the data of $|\cdot|_\mathbb{A}^{s_0}$).** Let $s_0 \in \mathbb{C}$ and let $\chi(x) = |x|_\mathbb{A}^{s_0}$.
1. Let $v$ be an infinite place. Then $\chi_v(x) = |\iota(x)|^{m_v s_0}$, and the pair $(n_v, t_v)$ is a pair of parameters of $\chi$ at $v$ if and only if $n_v = 0$ and $t_v = s_0$.
2. The character $\chi$ is unramified at each finite place, and its conductor is $\mathcal{O}_F$. The local factor of $\chi$ at a finite place $v$ is $(1 - N(\mathfrak{p}_v)^{-(s + s_0)})^{-1}$. So $L(s, \chi) = \zeta_F(s + s_0)$ for $\mathrm{Re}(s + s_0) > 1$.
3. For the parameters of part 1, $L_\infty(s, \chi) = L_\infty(s + s_0, \mathbf{1})$. So $\Lambda(s, \chi) = \Lambda(s + s_0, \mathbf{1})$ for $\mathrm{Re}(s + s_0) > 1$.
4. The character $\chi^{-1}$ is $|\cdot|_\mathbb{A}^{-s_0}$.

Lean: `Langlands.Tate.isArchimedeanParameter_of_normPower`, `Langlands.Tate.conductor_of_normPower`, `Langlands.Tate.localFactor_of_normPower`, `Langlands.Tate.finiteLFunction_of_normPower`, `Langlands.Tate.completedLFunction_of_normPower`, `Langlands.Tate.inv_of_normPower`

*Proof.* (1) By part 1 of Lemma 5.5.12, $\chi_v(x) = (|\iota(x)|^{m_v})^{s_0}$. For a real number $r > 0$ and $m \in \mathbb{N}$ we have $(r^m)^{s_0} = e^{s_0 m \log r} = r^{m s_0}$, and this gives the formula. Let $(n_v, t_v)$ be a pair of parameters. We divide the formula of Remark 5.5.4 by the formula for $\chi_v$, and we get $(\iota(x)/|\iota(x)|)^{n_v} |\iota(x)|^{m_v (t_v - s_0)} = 1$ for each $x \in F_v^\times$. The proof of part 1 of Lemma 5.5.8 uses only this identity, with $t_v - s_0$ in place of $t_v$. So $n_v = 0$ and $t_v = s_0$. The converse is the formula for $\chi_v$.

(2) Let $v$ be a finite place and let $x \in \mathcal{O}_v^\times$. Then $|x|_v = 1$, so $\chi_v(x) = 1$ by part 2 of Lemma 5.5.12. Thus $\chi_v$ is trivial on $\mathcal{O}_v^\times$ and on each subgroup $1 + \mathfrak{p}_v^m$. So $a(\chi_v) = 0$ and the conductor is $\mathcal{O}_F$. By part 2 of Lemma 5.5.12, $\chi_v(\varpi_v) = N(\mathfrak{p}_v)^{-s_0}$. So the local factor is
$$\big(1 - N(\mathfrak{p}_v)^{-s_0} N(\mathfrak{p}_v)^{-s}\big)^{-1} = \big(1 - N(\mathfrak{p}_v)^{-(s + s_0)}\big)^{-1}.$$
This is the local factor of $\mathbf{1}$ at $s + s_0$, by part 3 of Lemma 5.5.8. The two Euler products are equal factor by factor, so $L(s, \chi) = L(s + s_0, \mathbf{1}) = \zeta_F(s + s_0)$ by Proposition 5.5.9.

(3) With $n_v = 0$ and $t_v = s_0$, the factors of Remark 5.5.4 are $\Gamma_\mathbb{R}(s + s_0)$ at the real places and $\Gamma_\mathbb{C}(s + s_0)$ at the complex places. These are the factors of $\mathbf{1}$ at $s + s_0$. With part 2, this gives the formula for $\Lambda(s, \chi)$.

(4) For each idele $x$, $\chi^{-1}(x) = (|x|_\mathbb{A}^{s_0})^{-1} = |x|_\mathbb{A}^{-s_0}$. $\square$

**Theorem 5.5.14 (Hecke's theorem for $|\cdot|_\mathbb{A}^{s_0}$).** Let $F$ be a number field, let $s_0 \in \mathbb{C}$ and let $\chi = |\cdot|_\mathbb{A}^{s_0}$. Put $\sigma = \mathrm{Re}(s_0)$. With $\Lambda$ and $\Lambda'$ as in Theorem 5.5.10, put
$$\Lambda_\chi(s) = \Lambda(s + s_0), \qquad \Lambda'_\chi(u) = \Lambda'(u - s_0), \qquad W = |d_F|^{\sigma - s_0}.$$
1. The functions $\Lambda_\chi$ and $\Lambda'_\chi$ are meromorphic on $\mathbb{C}$.
2. For $\mathrm{Re}(s) > 1 - \sigma$, $\Lambda_\chi(s) = \Lambda(s, \chi)$. For $\mathrm{Re}(u) > 1 + \sigma$, $\Lambda'_\chi(u) = \Lambda(u, \chi^{-1})$.
3. We have $|W| = 1$, and $\Lambda_\chi(s) = W \, |d_F|^{1/2 - s - \sigma} \, \Lambda'_\chi(1 - s)$ for each $s \in \mathbb{C}$.
4. The function $\Lambda_\chi$ is holomorphic outside $\{-s_0, 1 - s_0\}$, and it has simple poles at $s = -s_0$ and $s = 1 - s_0$.

So the conclusion of `Langlands.HeckeFunctionalEquationAt` holds for $\chi$, with $\sigma = \mathrm{Re}(s_0)$, $W = |d_F|^{\sigma - s_0}$ and the exponent $s_0$.

Lean: `Langlands.Tate.heckeFunctionalEquationAt_normPower`

*Proof.* (1) A translate of a meromorphic function on $\mathbb{C}$ is meromorphic on $\mathbb{C}$. Apply this to part 1 of Theorem 5.5.10.

(2) Let $\mathrm{Re}(s) > 1 - \sigma$. Then $\mathrm{Re}(s + s_0) > 1$. By part 3 of Lemma 5.5.13 and part 2 of Theorem 5.5.10, $\Lambda(s, \chi) = \Lambda(s + s_0, \mathbf{1}) = \Lambda(s + s_0) = \Lambda_\chi(s)$. Let $\mathrm{Re}(u) > 1 + \sigma$. By part 4 of Lemma 5.5.13 we can apply part 3 of Lemma 5.5.13 to $\chi^{-1}$, with $-s_0$ in place of $s_0$. Then $\mathrm{Re}(u - s_0) > 1$, and part 2 of Theorem 5.5.10 gives $\Lambda(u, \chi^{-1}) = \Lambda(u - s_0, \mathbf{1}) = \Lambda'(u - s_0) = \Lambda'_\chi(u)$.

(3) Since $|d_F| > 0$, $|W| = |d_F|^{\mathrm{Re}(\sigma - s_0)} = |d_F|^0 = 1$. By part 3 of Theorem 5.5.10 at the point $s + s_0$,
$$\Lambda_\chi(s) = |d_F|^{1/2 - s - s_0} \, \Lambda'(1 - s - s_0) = |d_F|^{\sigma - s_0} \, |d_F|^{1/2 - s - \sigma} \, \Lambda'_\chi(1 - s).$$

(4) The function $\Lambda_\chi$ is holomorphic at $s$ if and only if $\Lambda$ is holomorphic at $s + s_0$, and the order of $\Lambda_\chi$ at $s$ is the order of $\Lambda$ at $s + s_0$. Apply this to part 4 of Theorem 5.5.10, with $s + s_0 \in \{0, 1\}$.

For the last statement, we compare with the Lean statement in Remark 5.5.4. By part 3 of Lemma 5.5.12, $|x|_\mathbb{A} > 0$, so $|\chi(x)| = |x|_\mathbb{A}^{\mathrm{Re}(s_0)} = |x|_\mathbb{A}^\sigma$. By part 1 of Lemma 5.5.13 the parameters of $\chi$ are $n = 0$ and $t = s_0$, and by part 4 the parameters of $\chi^{-1}$ are $n = 0$ and $t = -s_0$. By part 2 of Lemma 5.5.13 the conductor is $\mathcal{O}_F$, so $N(\mathfrak{f}_\chi) = 1$ and part 3 is the functional equation of the statement. For the poles we take the second case of the disjunction, with the exponent $s_0$. $\square$

**Remark 5.5.15 (the root number).** The root number $W = |d_F|^{\sigma - s_0} = |d_F|^{-i \, \mathrm{Im}(s_0)}$ is not $1$ when $\mathrm{Im}(s_0) \ne 0$ and $|d_F| > 1$. This is not a defect of the normalization. Write $\chi = \chi_0 |\cdot|_\mathbb{A}^\sigma$ with $\chi_0 = |\cdot|_\mathbb{A}^{i \, \mathrm{Im}(s_0)}$ unitary. In the notation of Theorem 5.5.3, $\varepsilon(s, \chi) = \varepsilon(s + s_0, \mathbf{1}) = |d_F|^{1/2 - s - s_0}$, so $W(\chi_0) = |d_F|^{-i \, \mathrm{Im}(s_0)}$. The local factors $\varepsilon(\chi_v, s, \psi_v)$ of Section 5.2 depend on the conductor of $\psi_v$, which is the local different, and this is the source of the power of $|d_F|$.

**Remark 5.5.16 (the Lean proof).** The file `Langlands/Tate/HeckeNormPower.lean` proves Lemma 5.5.12, Lemma 5.5.13 and Theorem 5.5.14. The functions $\Lambda_\chi$ and $\Lambda'_\chi$ are `fun s => heckeLambdaOne K (s + s₀)` and `fun u => heckeLambdaOne' K (u - s₀)`. Part 4 uses the invariance of the order under translation, `meromorphicOrderAt_comp_add_const_eq_meromorphicOrderAt` of Mathlib. In part 1 of Lemma 5.5.13 the Lean proof repeats the argument of Lemma 5.5.8 with a general hypothesis, as `Langlands.Tate.eq_zero_of_forall_param_eq_one`. All these theorems use only the standard axioms of Lean. By part 3 of Theorem 5.5.3, the Hecke characters that remain are the characters with $\Lambda(s, \chi)$ entire. This case is still open in Lean. It needs the local theory of Section 5.2 at the ramified places, or a theta function with a character for each ray class, and the identification of the root number with a product of Gauss sums. The next subsection proves the continuation and the functional equation for the characters of the class group, which are unramified at every place. The subsection after it joins them to the Lean statement.

### Class group characters in Lean

By Remark 5.5.16, the Hecke characters with an entire $\Lambda(s, \chi)$ are still open in Lean. The simplest of them come from the class group, and this subsection treats them with the theta functions of Section 5.3, as Hecke did. In this subsection $\psi$ is a character of the class group $\mathrm{Cl}_F$, and not an additive character. The proof is the proof of Theorem 5.3.34 with the weights $\psi(C^{-1})$. The new point is that the poles cancel when $\psi \ne 1$. We keep the notation of Lemma 5.3.33, Theorem 5.3.34 and Proposition 5.3.36. So $n = [F : \mathbb{Q}]$, $h_F$ is the class number, $c_F = 2^{r - r_2} n R_F / w_F$, $\mathfrak{a}_C$ is a nonzero fractional ideal in the class $C$, and $C^* = (C [\mathfrak{D}])^{-1}$ is the class of $\mathfrak{a}_C^\vee = \mathfrak{a}_C^{-1} \mathfrak{D}^{-1}$.

**Definition 5.5.17 (class group characters).** Let $F$ be a number field.
1. A *class group character* of $F$ is a homomorphism $\psi : \mathrm{Cl}_F \to \mathbb{C}^\times$. Its inverse $\psi^{-1}$ is the character $C \mapsto \psi(C)^{-1}$, and $1$ is the trivial character.
2. The *$L$-series* of $\psi$ is $L(u, \psi) = \sum_{I \ne 0} \psi([I]) \, N(I)^{-u}$ for $\mathrm{Re}(u) > 1$. Here $I$ runs over the nonzero integral ideals of $\mathcal{O}_F$, and $[I]$ is the class of $I$.
3. The *completed function* of $\psi$ is $\xi_F(u, \psi) = c_F \sum_C \psi(C^{-1}) \, \varphi_{\mathfrak{a}_C}(u)$ for $u \ne 0, 1$, where $C$ runs over $\mathrm{Cl}_F$.

Lean: `Langlands.Tate.classCharL`, `Langlands.Tate.classCharXi`

The function $\xi_F(u, \psi)$ is holomorphic on $\mathbb{C} \setminus \{0, 1\}$ by part (1) of Lemma 5.3.33, and it does not depend on the choice of the ideals $\mathfrak{a}_C$ by part (3). The weight of $\varphi_{\mathfrak{a}_C}$ is $\psi(C^{-1})$ and not $\psi(C)$, because $\varphi_{\mathfrak{a}_C}$ is a multiple of the partial zeta function $\zeta(u, C^{-1})$ for $\mathrm{Re}(u) > 1$, by part (2) of Lemma 5.3.33. Proposition 5.5.19 below shows that the series of part 2 converges.

**Lemma 5.5.18 (the values of a class group character).** Let $\psi$ be a class group character of $F$.
1. For each class $C$, $|\psi(C)| = 1$ and $\psi^{-1}(C) = \overline{\psi(C)}$.
2. If $\psi \ne 1$, then $\sum_C \psi(C) = \sum_C \psi(C^{-1}) = 0$.
3. For each class $C$, $\psi(C^{-1}) = \psi([\mathfrak{D}]) \, \psi^{-1}\big((C^*)^{-1}\big)$.

Lean: `Langlands.Tate.sum_classChar_inv`, `Langlands.Tate.classChar_inv_eq`

*Proof.* (1) The class group is a finite group of order $h_F$. So $C^{h_F} = 1$ and $\psi(C)^{h_F} = \psi(C^{h_F}) = 1$. Thus $\psi(C)$ is a root of unity, and $|\psi(C)| = 1$. For a complex number $z$ with $|z| = 1$ we have $z^{-1} = \bar z$.

(2) Since $\psi \ne 1$, there is a class $D$ with $\psi(D) \ne 1$. Put $S = \sum_C \psi(C)$. The map $C \mapsto D C$ is a bijection of $\mathrm{Cl}_F$, so $S = \sum_C \psi(D C) = \psi(D) S$. Thus $(1 - \psi(D)) S = 0$, and $S = 0$. The map $C \mapsto C^{-1}$ is also a bijection of $\mathrm{Cl}_F$, and this gives the second sum.

(3) By the definition of $C^*$, we have $C^{-1} = [\mathfrak{D}] \, C^*$. So $\psi(C^{-1}) = \psi([\mathfrak{D}]) \, \psi(C^*)$, and $\psi(C^*) = \psi\big((C^*)^{-1}\big)^{-1} = \psi^{-1}\big((C^*)^{-1}\big)$. $\square$

Part 2 is the orthogonality of the characters of a finite abelian group, in the form that we need. Part 3 is the step where the different enters, and it gives the root number of Theorem 5.5.20.

**Proposition 5.5.19 (the Dirichlet series).** Let $\psi$ be a class group character of $F$.
1. For $\mathrm{Re}(u) > 1$, the series $L(u, \psi)$ converges absolutely.
2. For $\mathrm{Re}(u) > 1$, $\xi_F(u, \psi) = |d_F|^{u/2} \, \Gamma_F(u) \, L(u, \psi)$.
3. For $u \ne 0, 1$, $\xi_F(u, 1) = \xi_F(u)$, and for $\mathrm{Re}(u) > 1$, $L(u, 1) = \zeta_F(u)$.

Lean: `Langlands.Tate.summable_classCharL`, `Langlands.Tate.classCharXi_eq`, `Langlands.Tate.classCharXi_one`

*Proof.* Let $\sigma = \mathrm{Re}(u) > 1$. (1) By part 1 of Lemma 5.5.18, the term of $I$ has the absolute value $N(I)^{-\sigma}$. The series $\sum_{I \ne 0} N(I)^{-\sigma}$ is the series of $\zeta_F(\sigma)$, and it converges because $\sigma > 1$.

(2) Since $[\mathfrak{a}_C] = C$, part (2) of Lemma 5.3.33 gives $c_F \, \varphi_{\mathfrak{a}_C}(u) = |d_F|^{u/2} \, \Gamma_F(u) \, \zeta(u, C^{-1})$. The map $C \mapsto C^{-1}$ is a bijection of $\mathrm{Cl}_F$. So
$$\xi_F(u, \psi) = |d_F|^{u/2} \, \Gamma_F(u) \sum_C \psi(C^{-1}) \, \zeta(u, C^{-1}) = |d_F|^{u/2} \, \Gamma_F(u) \sum_C \psi(C) \, \zeta(u, C).$$
For an integral ideal $I$ in the class $C$ we have $\psi([I]) = \psi(C)$. So $\psi(C) \, \zeta(u, C)$ is the part of the series $L(u, \psi)$ over the ideals in $C$. Each nonzero integral ideal is in exactly one class, and the series converges absolutely by (1). So the sum of these parts over the classes is $L(u, \psi)$.

(3) For $\psi = 1$ all the weights are $1$. So $\xi_F(u, 1)$ is the function $\xi_F(u)$ of Theorem 5.3.34, and $L(u, 1)$ is the series of $\zeta_F(u)$. $\square$

**Theorem 5.5.20 (the functional equation).** Let $\psi$ be a class group character of $F$. For $u \ne 0, 1$,
$$\xi_F(1 - u, \psi) = \psi([\mathfrak{D}]) \, \xi_F(u, \psi^{-1}).$$

Lean: `Langlands.Tate.classCharXi_one_sub`

*Proof.* Let $u \ne 0, 1$. Part (1) of Lemma 5.3.33 gives $\varphi_{\mathfrak{a}_C}(1 - u) = \varphi_{\mathfrak{a}_C^\vee}(u)$. The ideal $\mathfrak{a}_C^\vee$ is in the class $C^*$, so $\varphi_{\mathfrak{a}_C^\vee}(u) = \varphi_{\mathfrak{a}_{C^*}}(u)$ by part (3) of the lemma. With part 3 of Lemma 5.5.18 this gives
$$\xi_F(1 - u, \psi) = c_F \sum_C \psi(C^{-1}) \, \varphi_{\mathfrak{a}_{C^*}}(u) = \psi([\mathfrak{D}]) \, c_F \sum_C \psi^{-1}\big((C^*)^{-1}\big) \, \varphi_{\mathfrak{a}_{C^*}}(u).$$
The map $C \mapsto C^*$ is a bijection of $\mathrm{Cl}_F$, because $(C^*)^* = C$. We put $D = C^*$. Then the last sum is $\sum_D \psi^{-1}(D^{-1}) \, \varphi_{\mathfrak{a}_D}(u)$, and $c_F$ times this sum is $\xi_F(u, \psi^{-1})$. $\square$

For $\psi = 1$ we have $\psi([\mathfrak{D}]) = 1$, and the theorem is part (3) of Theorem 5.3.34. In that case $\xi_F(u, 1)$ has simple poles at $u = 0$ and $u = 1$, by Proposition 5.3.36. We now show that the poles cancel when $\psi \ne 1$. For a class $C$ put $g_C = g_{\mathfrak{a}_C}$ and $\varepsilon_C = \varepsilon_{\mathfrak{a}_C}$, as in Proposition 5.3.36, and put
$$E_\psi(u) = c_F \sum_C \psi(C^{-1}) \, g_C(u) \, \Lambda_0(\Theta_{\mathfrak{a}_C}, n u / 2), \qquad F_{0, \psi}(u) = -\frac{2 c_F}{n} \sum_C \psi(C^{-1}) \, g_C(u), \qquad F_{1, \psi}(u) = \frac{2 c_F}{n} \sum_C \psi(C^{-1}) \, \varepsilon_C \, g_C(u).$$
These are entire functions, because they are finite sums of entire functions. The proof of Proposition 5.3.36 writes $\varphi_{\mathfrak{a}_C}$ in the form $g_C(u) \Lambda_0(\Theta_{\mathfrak{a}_C}, n u / 2) - (2/n) g_C(u)/u + (2 \varepsilon_C / n) g_C(u)/(u - 1)$. We multiply by $c_F \, \psi(C^{-1})$ and sum over $C$. This gives
$$\xi_F(u, \psi) = E_\psi(u) + \frac{F_{0, \psi}(u)}{u} + \frac{F_{1, \psi}(u)}{u - 1}, \qquad u \ne 0, 1. \tag{5.5.1}$$
For an entire function $G$ and a point $a \in \mathbb{C}$, let $\delta_a G(u) = (G(u) - G(a))/(u - a)$ for $u \ne a$, and $\delta_a G(a) = G'(a)$.

**Theorem 5.5.21 (Hecke's theorem for class group characters).** Let $\psi \ne 1$ be a class group character of $F$, and put $\Lambda_\psi = E_\psi + \delta_0 F_{0, \psi} + \delta_1 F_{1, \psi}$.
1. The function $\Lambda_\psi$ is entire.
2. For $u \ne 0, 1$, $\Lambda_\psi(u) = \xi_F(u, \psi)$.
3. For $\mathrm{Re}(u) > 1$, $\Lambda_\psi(u) = |d_F|^{u/2} \, \Gamma_F(u) \, L(u, \psi)$.
4. For each $u \in \mathbb{C}$, $\Lambda_\psi(1 - u) = \psi([\mathfrak{D}]) \, \Lambda_{\psi^{-1}}(u)$.

Lean: `Langlands.Tate.differentiable_classCharLambda`, `Langlands.Tate.classCharLambda_eq`, `Langlands.Tate.classCharLambda_eq_classCharL`, `Langlands.Tate.classCharLambda_one_sub`

*Proof.* We first compute the numerators at the poles. By the proof of Proposition 5.3.36, $g_C(0) = 1$ and $\varepsilon_C \, g_C(1) = 1$ for each class $C$. So
$$F_{0, \psi}(0) = -\frac{2 c_F}{n} \sum_C \psi(C^{-1}), \qquad F_{1, \psi}(1) = \frac{2 c_F}{n} \sum_C \psi(C^{-1}).$$
The terms of these sums do not depend on the ideals $\mathfrak{a}_C$. Both sums are $0$ by part 2 of Lemma 5.5.18.

(1) Let $G$ be entire and let $a \in \mathbb{C}$. Then $G(u) = \sum_{k \ge 0} b_k (u - a)^k$ for all $u \in \mathbb{C}$, with $b_0 = G(a)$ and $b_1 = G'(a)$. So $G(u) - G(a) = (u - a) \sum_{k \ge 1} b_k (u - a)^{k - 1}$. The power series $\sum_{k \ge 1} b_k (u - a)^{k - 1}$ has the same radius of convergence, so it converges on $\mathbb{C}$. Its sum is $\delta_a G(u)$ for $u \ne a$, and $b_1 = \delta_a G(a)$ for $u = a$. So $\delta_a G$ is entire. Thus $\Lambda_\psi$ is a sum of three entire functions.

(2) Let $u \ne 0, 1$. Since $F_{0, \psi}(0) = 0$ and $F_{1, \psi}(1) = 0$, we have $\delta_0 F_{0, \psi}(u) = F_{0, \psi}(u)/u$ and $\delta_1 F_{1, \psi}(u) = F_{1, \psi}(u)/(u - 1)$. So $\Lambda_\psi(u) = \xi_F(u, \psi)$ by (5.5.1).

(3) If $\mathrm{Re}(u) > 1$, then $u \ne 0, 1$. Apply (2) and part 2 of Proposition 5.5.19.

(4) The character $\psi^{-1}$ is not trivial, because $\psi = (\psi^{-1})^{-1}$. So $\Lambda_{\psi^{-1}}$ is defined, and (1) and (2) hold for it. Let $u \notin \{0, 1\}$. Then $1 - u \notin \{0, 1\}$, and (2) and Theorem 5.5.20 give
$$\Lambda_\psi(1 - u) = \xi_F(1 - u, \psi) = \psi([\mathfrak{D}]) \, \xi_F(u, \psi^{-1}) = \psi([\mathfrak{D}]) \, \Lambda_{\psi^{-1}}(u).$$
By (1), both sides are continuous functions of $u$ on $\mathbb{C}$. The set $\mathbb{C} \setminus \{0, 1\}$ is dense in $\mathbb{C}$, because each disc around $0$ or $1$ contains points outside $\{0, 1\}$. Two continuous functions that agree on a dense set are equal. So the identity also holds at $u = 0$ and $u = 1$. $\square$

So $\xi_F(u, \psi)$ has removable singularities at $u = 0$ and $u = 1$, and $\Lambda_\psi$ is its continuation. The residues of $\xi_F(u, \psi)$ at these points are $F_{0, \psi}(0)$ and $F_{1, \psi}(1)$. For $\psi = 1$ they are $\mp 2 c_F h_F / n$, and for $\psi \ne 1$ they vanish by the orthogonality of characters. The function $1/\Gamma$ is entire, so $\Gamma_F$ has no zeros, and $L(u, \psi) = |d_F|^{-u/2} \Lambda_\psi(u) / \Gamma_F(u)$ extends to an entire function. Each of the $r_1 + r_2 = r + 1$ factors of $\Gamma_F$ has a simple pole at $u = 0$, so this continuation of $L(u, \psi)$ has a zero of order at least $r + 1$ at $u = 0$. These two consequences are not in Lean.

**Remark 5.5.22 (the root number).** The root number of Theorem 5.5.21 is $\psi([\mathfrak{D}])$. By part 1 of Lemma 5.5.18 it has absolute value $1$, and $\psi^{-1} = \bar\psi$ is the complex conjugate character. So part 4 reads $\Lambda_\psi(1 - u) = \psi([\mathfrak{D}]) \Lambda_{\bar\psi}(u)$, which is the shape of Theorem 5.5.3 for a unitary character. The root number is $1$ if and only if $\psi$ is trivial on the class of the different. It agrees with the product of the local root numbers. Under the dictionary of Remark 5.5.23, $\chi_v(\varpi_v) = \psi([\mathfrak{p}_v])$ at each finite place $v$, and $\chi_v$ is trivial at each infinite place. So Proposition 5.2.3 gives $\varepsilon(\chi_v, 1/2, \psi_v) = \psi([\mathfrak{p}_v])^{d_v}$ at a finite place, and Propositions 5.2.5 and 5.2.6 give $1$ at an infinite place. Since $d_v = v(\mathfrak{D})$, as in Section 5.3, the product is $\psi\big(\prod_v [\mathfrak{p}_v]^{d_v}\big) = \psi([\mathfrak{D}])$. If $\psi^2 = 1$, then $\bar\psi = \psi$ and $\psi([\mathfrak{D}]) = \pm 1$. A theorem of Hecke, which we do not prove, says that $[\mathfrak{D}]$ is a square in $\mathrm{Cl}_F$. So the root number of a quadratic class group character is $1$.

**Remark 5.5.23 (class group characters as Hecke characters).** At an infinite place $v$, call a character of $F_v^\times$ unramified if it is trivial on the maximal compact subgroup, which is $\{\pm 1\}$ or the unit circle. The class group characters are then exactly the Hecke characters that are unramified at every place and trivial on the connected component of $F_\infty^\times = \prod_{v \mid \infty} F_v^\times$. Indeed, at an infinite place the maximal compact subgroup and the connected component generate $F_v^\times$. So such a $\chi$ is trivial on $F_\infty^\times$ and on $\prod_{v \nmid \infty} \mathcal{O}_v^\times$. The map $x \mapsto \prod_{v \nmid \infty} \mathfrak{p}_v^{v(x_v)}$ from $J_F$ onto the group of fractional ideals has the kernel $F_\infty^\times \prod_{v \nmid \infty} \mathcal{O}_v^\times$, which is open, and it maps $F^\times$ onto the principal ideals. So it induces an isomorphism of $J_F / F^\times F_\infty^\times \prod_{v \nmid \infty} \mathcal{O}_v^\times$ with $\mathrm{Cl}_F$, and $\psi \mapsto \chi = \psi \circ [\cdot]$, where $[x]$ is the class of the ideal of $x$, is a bijection from the class group characters onto these Hecke characters. For this $\chi$ we have $\chi_v(\varpi_v) = \psi([\mathfrak{p}_v])$, the conductor is $\mathcal{O}_F$, and the archimedean parameters are $0$. As in Definition 5.5.1 and Lemma 5.5.8, $L(s, \chi) = L(s, \psi)$ and $\Lambda(s, \chi) = 2^{r_2} \Gamma_F(s) L(s, \psi) = 2^{r_2} |d_F|^{-s/2} \Lambda_\psi(s)$ for $\mathrm{Re}(s) > 1$. With these identities, Theorem 5.5.21 would give the conclusion of `Langlands.HeckeFunctionalEquationAt` for $\chi$, with $\sigma = 0$, $W = \psi([\mathfrak{D}])$ and an entire $\Lambda$. Theorem 5.5.33 proves this link in Lean in the direction from $\chi$ to $\psi$. It starts from a Hecke character of class group type, constructs its class group character, computes its local data and proves the Euler product of $L(u, \psi)$. The Lean project does not yet construct the Hecke character of $\psi$ as a term of `Langlands.HeckeCharacter`. If we only ask that $\chi$ is trivial on the connected component, we get the characters of the narrow class group. At a real place such a character can be $\mathrm{sgn}$, with the factor $\Gamma_\mathbb{R}(s + 1)$, and Theorem 5.5.21 does not cover these characters.

**Remark 5.5.24 (the Lean proof).** The file `Langlands/Tate/ClassCharacter.lean` proves parts 2 and 3 of Lemma 5.5.18, Proposition 5.5.19, Theorem 5.5.20 and Theorem 5.5.21. It writes $K$ for the number field, and a class group character is a homomorphism `ClassGroup (𝓞 K) →* ℂˣ`. As in Remark 5.3.35, the ideal $\mathfrak{a}_C$ is `Langlands.Tate.classRepUnit` and the bijection $C \mapsto C^*$ is `Langlands.Tate.dualClass`. The class $[\mathfrak{D}]$ is the class of `Langlands.Tate.differentUnit`, and $c_F$ is `Langlands.Tate.xiConst`. The Lean proof of part 1 of Proposition 5.5.19 does not use part 1 of Lemma 5.5.18. It writes $\sum_C \psi(C^{-1}) \varphi_{\mathfrak{a}_C}(u)$ as one series over all the nonzero integral ideals, as `Langlands.Tate.hasSum_classCharXi`, with the series of Remark 5.3.35, and it gets the convergence of $L(u, \psi)$ from this series. This file does not use part 1 of Lemma 5.5.18. Its first half is `Langlands.Tate.norm_classGroupChar` of Remark 5.5.35. The orthogonality in part 2 is `sum_hom_units_eq_zero` of Mathlib. The functions $E_\psi$, $F_{0, \psi}$ and $F_{1, \psi}$ are `Langlands.Tate.classCharE`, `Langlands.Tate.classCharF₀` and `Langlands.Tate.classCharF₁`, and (5.5.1) is `Langlands.Tate.classCharXi_eq_poleShape`. The values at the poles are `Langlands.Tate.classCharF₀_zero` and `Langlands.Tate.classCharF₁_one`, with `Langlands.Tate.ε_mul_classFactor_one` for $\varepsilon_C \, g_C(1) = 1$. The function $\delta_a G$ is `dslope G a` of Mathlib, and its holomorphy is `Complex.differentiableOn_dslope`. The function $\Lambda_\psi$ is `Langlands.Tate.classCharLambda`. In part 4 of Theorem 5.5.21, the step with the dense set is `Continuous.ext_on`, and the density holds because the complement of a countable set in $\mathbb{C}$ is dense. All these theorems use only the standard axioms of Lean. The link of Remark 5.5.23 is the subject of the next subsection. One question remains open. It is the analogue of Dirichlet's theorem, $L(1, \psi) \ne 0$ for $\psi \ne 1$, which is not proved here and not in Lean. Dirichlet's argument studies the product of the functions $L(u, \psi)$ over all $\psi$, and it needs a separate argument for the characters with $\psi^2 = 1$.

### Hecke characters of class group type

Remark 5.5.23 describes the Hecke characters that come from the class group, and Theorem 5.5.21 proves the functional equation of the $L$-functions of the class group characters. This subsection joins the two results in Lean. It goes from the Hecke character to the class group, as the Lean file does. We start from a Hecke character $\chi$ that is trivial on each local unit group and at each infinite place. We construct a class group character $\psi$ with $\chi(x) = \psi([I(x)])$, where $I(x)$ is the ideal of the idele $x$. Then we compute the data of $\chi$ that occur in the Lean statement of Remark 5.5.4, and Theorem 5.5.21 gives the conclusion of `Langlands.HeckeFunctionalEquationAt` for $\chi$. As in the preceding subsection, $\psi$ is a character of $\mathrm{Cl}_F$ and not an additive character. For a place $v$ and $y \in F_v^\times$, $y^{(v)}$ is the idele of Lemma 5.5.12, so that $\chi_v(y) = \chi(y^{(v)})$. At a finite place $v$, $v(y)$ is the normalized valuation of $y$, and $\varpi_v \in F$ is the uniformizer of Remark 5.5.4. We write $\chi(x)$ for the value of $\chi$ at the class of an idele $x$ in $C_F$.

**Definition 5.5.25 (characters of class group type).** Let $F$ be a number field. A Hecke character $\chi$ of $F$ is *of class group type* if it has these two properties.
1. At each finite place $v$, the local component $\chi_v$ is trivial on $\mathcal{O}_v^\times$.
2. At each infinite place $v$, the local component $\chi_v$ is trivial on $F_v^\times$.

Lean: `Langlands.Tate.IsClassType`

By Remark 5.5.23, these are the Hecke characters that are unramified at every place and trivial on the connected component of $F_\infty^\times$. The trivial character is of class group type. A character of the narrow class group can be $\mathrm{sgn}$ at a real place. Then it is not of class group type.

**Lemma 5.5.26 (the reduction to finitely many places).** Let $\chi$ be a Hecke character of $F$.
1. There are a finite set $T$ of finite places and an integer $k \ge 0$ with this property. Let $z$ be an idele with $z_v = 1$ at each infinite place, $z_v \in \mathcal{O}_v^\times$ at each finite place, and $z_v \in 1 + \mathfrak{p}_v^k$ at each $v \in T$. Then $\chi(z) = 1$.
2. Let $\chi$ be of class group type. Then $\chi$ is trivial on the group $U_F = \prod_{v \mid \infty} F_v^\times \times \prod_{v \nmid \infty} \mathcal{O}_v^\times$.
3. Let $\chi$ be of class group type, let $x$ be an idele, and let $S$ be a finite set of finite places with $x_v \in \mathcal{O}_v^\times$ for each finite place $v \notin S$. Then $\chi(x) = \prod_{v \in S} \chi_v(x_v)$.
4. Let $\chi$ be of class group type and let $v$ be a finite place. Then $\chi_v(y) = \chi_v(\varpi_v)^{v(y)}$ for each $y \in F_v^\times$.

Lean: `Langlands.HeckeRat.Top.exists_trivial_on_units`, `Langlands.Tate.IsClassType.ideleChar_eq_prod`, `Langlands.Tate.IsClassType.finiteComponent_eq_zpow`

In part 1 we read $1 + \mathfrak{p}_v^0$ as $\mathcal{O}_v^\times$.

*Proof.* (1) The map $z \mapsto \chi(z)$ on $J_F$ is the composite of the continuous maps $J_F \to C_F$ and $\chi$. So the set $N = \{z \in J_F : |\chi(z) - 1| < 1/2\}$ is an open neighbourhood of $1$. By the definition of the restricted product topology, $N$ contains a set $\prod_{v \in \Sigma} W_v \times \prod_{v \notin \Sigma} \mathcal{O}_v^\times$. Here $\Sigma$ is a finite set of places that contains the infinite places, and $W_v$ is an open neighbourhood of $1$ in $F_v^\times$. For each finite place $v \in \Sigma$ there is $k_v \ge 1$ with $1 + \mathfrak{p}_v^{k_v} \subset W_v$. Let $T$ be the set of the finite places in $\Sigma$, and let $k$ be the largest $k_v$, or $0$ if $T$ is empty. Let $G$ be the set of the ideles $z$ of part 1. Then $G \subset N$, and $G$ is a subgroup of $J_F$. Let $z \in G$ and put $w = \chi(z)$. For each $m \ge 0$ we have $z^{2^m} \in G$, so $|w^{2^m} - 1| < 1/2$. Then $|w^{2^m} + 1| \ge 2 - |w^{2^m} - 1| > 3/2$, and
$$|w^{2^{m+1}} - 1| = |w^{2^m} - 1| \, |w^{2^m} + 1| \ge \tfrac32 \, |w^{2^m} - 1|.$$
By induction, $(3/2)^m |w - 1| \le |w^{2^m} - 1| < 1/2$ for each $m \ge 0$. So $w = 1$.

(2) Let $z \in U_F$. Let $z_\infty$ be the idele with the components of $z$ at the infinite places and the component $1$ at the finite places. Let $z'$ be the idele with the component $1$ at the infinite places and at the places in $T$, and the component $z_v$ at each other finite place $v$. Then
$$z = z_\infty \, z' \prod_{v \in T} z_v^{(v)}.$$
Since $\chi$ is trivial at the infinite places, $\chi(z_\infty) = \prod_{v \mid \infty} \chi_v(z_v) = 1$. For $v \in T$, $\chi(z_v^{(v)}) = \chi_v(z_v) = 1$, because $z_v \in \mathcal{O}_v^\times$. The idele $z'$ has the properties of part 1, so $\chi(z') = 1$. Thus $\chi(z) = 1$.

(3) Let $u$ be the idele with the component $1$ at the places in $S$ and the component $x_v$ at each other place $v$. Then $u \in U_F$ and $x = u \prod_{v \in S} x_v^{(v)}$. By part 2, $\chi(x) = \prod_{v \in S} \chi(x_v^{(v)}) = \prod_{v \in S} \chi_v(x_v)$.

(4) Put $m = v(y)$. The element $y \varpi_v^{-m}$ has valuation $0$, so it is in $\mathcal{O}_v^\times$, and $\chi_v(y \varpi_v^{-m}) = 1$. So $\chi_v(y) = \chi_v(\varpi_v)^m$. $\square$

Part 3 has the shape of the arguments with strong approximation. We split off the components at finitely many places, and the rest of the idele is in a subgroup on which $\chi$ is trivial. Here no approximation theorem is necessary, because $\chi$ is trivial at the infinite places and on each local unit group. For a general Hecke character, part 1 still holds, but $\chi$ need not be trivial on $U_F$. By part 4, $\chi_v(\varpi_v)$ does not depend on the choice of the uniformizer.

**Definition 5.5.27 (the ideal of an idele).** Let $F$ be a number field.
1. The *ideal* of an idele $x$ is the fractional ideal $I(x) = \prod_{v \nmid \infty} \mathfrak{p}_v^{v(x_v)}$.
2. Let $\chi$ be a Hecke character of $F$. The *ideal character* of $\chi$ is the map $\lambda_\chi(I) = \prod_{v \nmid \infty} \chi_v(\varpi_v)^{v(I)}$ from the group of nonzero fractional ideals of $F$ to $\mathbb{C}^\times$. Here $v(I)$ is the exponent of $\mathfrak{p}_v$ in $I$.

Lean: `Langlands.Tate.ideleIdeal`, `Langlands.Tate.idealChar`

Both products are finite, because $x_v \in \mathcal{O}_v^\times$ and $v(I) = 0$ for almost all $v$. The map $x \mapsto I(x)$ is a homomorphism, and it is the map of Remark 5.5.23. The map $\lambda_\chi$ is a homomorphism, because $v(IJ) = v(I) + v(J)$. Let $a \in F^\times$. The valuation of $a$ in $F_v$ is the exponent of $\mathfrak{p}_v$ in the principal ideal $(a)$. So the principal idele $a$ has the ideal $I(a) = (a)$.

**Proposition 5.5.28 (the class group character of $\chi$).** Let $\chi$ be a Hecke character of $F$ of class group type.
1. For each $a \in F^\times$, $\lambda_\chi((a)) = 1$. So there is a unique class group character $\psi_\chi$ with $\psi_\chi([I]) = \lambda_\chi(I)$ for each nonzero fractional ideal $I$.
2. For each finite place $v$, $\psi_\chi([\mathfrak{p}_v]) = \chi_v(\varpi_v) = \chi(\varpi_v^{(v)})$.

Lean: `Langlands.Tate.IsClassType.idealChar_toPrincipalIdeal`, `Langlands.Tate.classChar`, `Langlands.Tate.IsClassType.classChar_mk0_primeNZ`, `Langlands.Tate.IsClassType.apply_ofAdicCompletion_localUniformizer`

*Proof.* (1) Let $a \in F^\times$, and let $S$ be the finite set of the finite places $v$ with $v(a) \ne 0$. The principal idele $a$ has the component $a$ at each place, and this component is a unit at each finite place outside $S$. The character $\chi$ is trivial on $F^\times$. So parts 3 and 4 of Lemma 5.5.26 give
$$1 = \chi(a) = \prod_{v \in S} \chi_v(a) = \prod_{v \in S} \chi_v(\varpi_v)^{v(a)} = \lambda_\chi((a)).$$
In the last step we use that $v((a)) = v(a)$, and that the factors for $v \notin S$ are $1$. So $\lambda_\chi$ is trivial on the group of principal ideals, and it factors through the quotient $\mathrm{Cl}_F$ in a unique way.

(2) We have $v(\mathfrak{p}_v) = 1$ and $w(\mathfrak{p}_v) = 0$ for each finite place $w \ne v$. So $\psi_\chi([\mathfrak{p}_v]) = \lambda_\chi(\mathfrak{p}_v) = \chi_v(\varpi_v)$. The last equality of part 2 is the definition of the local component $\chi_v$. $\square$

**Theorem 5.5.29 (characters of class group type come from the class group).** Let $\chi$ be a Hecke character of $F$ of class group type, and put $\psi = \psi_\chi$.
1. For each idele $x$, $\chi(x) = \psi([I(x)])$.
2. For each idele $x$, $|\chi(x)| = 1$.
3. If $\psi = 1$, then $\chi = 1$.
4. The character $\chi^{-1}$ is of class group type, and $\psi_{\chi^{-1}} = \psi^{-1}$.

Lean: `Langlands.Tate.IsClassType.apply_eq_classChar`, `Langlands.Tate.IsClassType.norm_apply`, `Langlands.Tate.IsClassType.eq_one_of_classChar_eq_one`, `Langlands.Tate.IsClassType.inv`

*Proof.* (1) The proof has three steps. First, the continuity of $\chi$ makes $\chi$ trivial on the subgroup of part 1 of Lemma 5.5.26. With the local unit groups at the finitely many places of $T$, $\chi$ is then trivial on $U_F$, by part 2 of the lemma. Second, the reduction of part 3 of the lemma removes all but finitely many components of $x$. Third, part 4 of the lemma and Proposition 5.5.28 write the remaining local values with $\psi$. In detail, let $S$ be the set of the finite places $v$ with $x_v \notin \mathcal{O}_v^\times$. It is a finite set. By parts 3 and 4 of Lemma 5.5.26 and part 2 of Proposition 5.5.28,
$$\chi(x) = \prod_{v \in S} \chi_v(x_v) = \prod_{v \in S} \chi_v(\varpi_v)^{v(x_v)} = \prod_{v \in S} \psi([\mathfrak{p}_v])^{v(x_v)} = \psi\Big(\Big[\prod_{v \in S} \mathfrak{p}_v^{v(x_v)}\Big]\Big).$$
The ideal in the last term is $I(x)$, because $v(x_v) = 0$ for each finite place $v \notin S$.

(2) This follows from part 1 and part 1 of Lemma 5.5.18.

(3) If $\psi = 1$, then part 1 gives $\chi(x) = 1$ for each idele $x$. Each element of $C_F$ is the class of an idele, so $\chi = 1$.

(4) At each place $v$, the local component of $\chi^{-1}$ is $\chi_v^{-1}$. So it is trivial on $\mathcal{O}_v^\times$ at the finite places and on $F_v^\times$ at the infinite places. Also $\lambda_{\chi^{-1}}(I) = \prod_v \chi_v(\varpi_v)^{-v(I)} = \lambda_\chi(I)^{-1}$ for each $I$. So $\psi_{\chi^{-1}}([I]) = \psi([I])^{-1}$. $\square$

With Remark 5.5.23, Theorem 5.5.29 shows that $\chi \mapsto \psi_\chi$ is a bijection from the Hecke characters of class group type onto the class group characters. Part 1 gives the injectivity. Let $\psi$ be a class group character. Remark 5.5.23 gives a Hecke character $\chi$ of class group type with $\chi_v(\varpi_v) = \psi([\mathfrak{p}_v])$ at each finite place $v$. So $\psi_\chi$ and $\psi$ agree on the classes of the prime ideals. These classes generate $\mathrm{Cl}_F$. Indeed, each class contains an integral ideal, because $d \, \mathfrak{a}$ is integral for a fractional ideal $\mathfrak{a}$ and a suitable integer $d \ge 1$, and each nonzero integral ideal is a product of prime ideals. So $\psi_\chi = \psi$. The Lean project has part 1, but it does not construct $\chi$ from $\psi$, see Remark 5.5.35.

**Proposition 5.5.30 (the local data).** Let $\chi$ be a Hecke character of $F$ of class group type, and put $\psi = \psi_\chi$.
1. Let $v$ be an infinite place. If $(n_v, t_v)$ is a pair of parameters of $\chi$ at $v$, in the sense of item 1 of Remark 5.5.4, then $n_v = 0$ and $t_v = 0$. The pair $(0, 0)$ is a pair of parameters of $\chi$ at $v$.
2. The conductor of $\chi$ is $\mathcal{O}_F$.
3. The character $\chi$ is unramified at each finite place $v$, and its local factor at $v$ is $\big(1 - \psi([\mathfrak{p}_v]) N(\mathfrak{p}_v)^{-s}\big)^{-1}$.

Lean: `Langlands.Tate.IsClassType.isArchimedeanParameter`, `Langlands.Tate.IsClassType.conductor_eq_one`, `Langlands.Tate.IsClassType.localFactor_eq`

*Proof.* (1) The character $\chi_v$ is trivial. So the formula of item 1 of Remark 5.5.4 reads $(\iota(x)/|\iota(x)|)^{n_v} |\iota(x)|^{m_v t_v} = 1$ for each $x \in F_v^\times$. This is the identity of the proof of part 1 of Lemma 5.5.8, and that proof gives $n_v = 0$ and $t_v = 0$. Conversely, $n_v = t_v = 0$ give the trivial character of $F_v^\times$, and $n_v = 0$ is allowed at a real place.

(2) At each finite place $v$, $\chi_v$ is trivial on $\mathcal{O}_v^\times = 1 + \mathfrak{p}_v^0$. So $a(\chi_v) = 0$, and the conductor is the product of the ideals $\mathfrak{p}_v^0 = \mathcal{O}_F$.

(3) The character $\chi_v$ is trivial on $\mathcal{O}_v^\times$, so $\chi$ is unramified at $v$. Then the local factor of Remark 5.5.4 is $(1 - \chi_v(\varpi_v) N(\mathfrak{p}_v)^{-s})^{-1}$, and part 2 of Proposition 5.5.28 gives $\chi_v(\varpi_v) = \psi([\mathfrak{p}_v])$. $\square$

**Proposition 5.5.31 (the Euler product).** Let $\psi$ be a class group character of $F$, and let $\mathrm{Re}(s) > 1$.
1. The product of the factors $\big(1 - \psi([\mathfrak{p}]) N(\mathfrak{p})^{-s}\big)^{-1}$ over the nonzero prime ideals $\mathfrak{p}$ of $\mathcal{O}_F$ converges unconditionally, and its value is $L(s, \psi)$.
2. Let $\chi$ be a Hecke character of class group type with $\psi_\chi = \psi$. Then $L(s, \chi) = L(s, \psi)$.

Lean: `Langlands.Tate.hasProd_classCharL`, `Langlands.Tate.IsClassType.finiteLFunction_eq`

*Proof.* (1) Put $\sigma = \mathrm{Re}(s)$, and put $f(I) = \psi([I]) \, N(I)^{-s}$ for a nonzero integral ideal $I$. Since $[IJ] = [I][J]$ and $N(IJ) = N(I) N(J)$, we have $f(IJ) = f(I) f(J)$, and $f(\mathcal{O}_F) = 1$. By part 1 of Lemma 5.5.18, $|f(I)| = N(I)^{-\sigma}$. The proof of Proposition 5.5.9 uses only these properties of the function $I \mapsto N(I)^{-s}$. So we repeat it with $f$. Let $S$ be a finite set of nonzero prime ideals, and let $\mathcal{I}_S$ be the set of the nonzero ideals whose prime factors are all in $S$. For $\mathfrak{p} \in S$ we have $|f(\mathfrak{p})| = N(\mathfrak{p})^{-\sigma} < 1$. The product of the geometric series and the unique factorization of ideals give
$$\prod_{\mathfrak{p} \in S} \big(1 - f(\mathfrak{p})\big)^{-1} = \sum_{I \in \mathcal{I}_S} f(I).$$
The difference between $L(s, \psi)$ and this sum has absolute value at most $\sum_{I \notin \mathcal{I}_S} N(I)^{-\sigma}$. This tends to $0$ along the directed set of the finite sets $S$, because the series of $\zeta_F(\sigma)$ converges.

(2) By Remark 5.5.4, $L(s, \chi)$ is the product over the finite places $v$ of the local factors of $\chi$. By part 3 of Proposition 5.5.30, these are the factors of part 1, with $\mathfrak{p} = \mathfrak{p}_v$. The map $v \mapsto \mathfrak{p}_v$ is a bijection from the finite places onto the nonzero prime ideals. So part 1 gives $L(s, \chi) = L(s, \psi)$. $\square$

For a class group character $\psi$, we write $\Lambda(s, \psi) = \Lambda_\psi(s)$ if $\psi \ne 1$, with $\Lambda_\psi$ as in Theorem 5.5.21, and $\Lambda(s, 1) = \xi_F(s)$ for $s \ne 0, 1$. For $\mathrm{Re}(s) > 1$, part 3 of Theorem 5.5.21, part 3 of Proposition 5.5.19 and part (2) of Theorem 5.3.34 give
$$\Lambda(s, \psi) = |d_F|^{s/2} \, \Gamma_F(s) \, L(s, \psi)$$
in both cases. The function $\Lambda(s, \psi)$ is entire for $\psi \ne 1$, and it has simple poles at $s = 0$ and $s = 1$ for $\psi = 1$.

**Proposition 5.5.32 (the completed $L$-function).** Let $\chi$ be a Hecke character of $F$ of class group type, put $\psi = \psi_\chi$, and let $(n_v, t_v)$ be parameters of $\chi$ at the infinite places. For $\mathrm{Re}(s) > 1$,
$$\Lambda(s, \chi) = 2^{r_2} \, \Gamma_F(s) \, L(s, \psi) = 2^{r_2} \, |d_F|^{-s/2} \, \Lambda(s, \psi).$$

Lean: `Langlands.Tate.IsClassType.completedLFunction_eq`, `Langlands.Tate.IsClassType.completedLFunction_eq_classCharLambda`

*Proof.* By part 1 of Proposition 5.5.30, $n_v = 0$ and $t_v = 0$ for each infinite place $v$. So the archimedean factor of $\chi$ is the archimedean factor of the trivial character, and part 2 of Lemma 5.5.8 gives $L_\infty(s, \chi) = 2^{r_2} \Gamma_F(s)$. With part 2 of Proposition 5.5.31, $\Lambda(s, \chi) = L_\infty(s, \chi) L(s, \chi) = 2^{r_2} \Gamma_F(s) L(s, \psi)$. The second equality follows from the formula for $\Lambda(s, \psi)$ above, because $|d_F|^{-s/2} |d_F|^{s/2} = 1$. $\square$

**Theorem 5.5.33 (Hecke's theorem for characters of class group type).** Let $\chi$ be a Hecke character of $F$ of class group type, and put $\psi = \psi_\chi$. Assume that $\psi \ne 1$, and put
$$\Lambda_\chi(s) = 2^{r_2} \, |d_F|^{-s/2} \, \Lambda(s, \psi), \qquad \Lambda'_\chi(u) = 2^{r_2} \, |d_F|^{-u/2} \, \Lambda(u, \psi^{-1}), \qquad W = \psi([\mathfrak{D}]).$$
1. The functions $\Lambda_\chi$ and $\Lambda'_\chi$ are entire.
2. For $\mathrm{Re}(s) > 1$, $\Lambda_\chi(s) = \Lambda(s, \chi)$ and $\Lambda'_\chi(s) = \Lambda(s, \chi^{-1})$.
3. We have $|W| = 1$, and $\Lambda_\chi(s) = W \, |d_F|^{1/2 - s} \, \Lambda'_\chi(1 - s)$ for each $s \in \mathbb{C}$.

So the conclusion of `Langlands.HeckeFunctionalEquationAt` holds for $\chi$, with $\sigma = 0$, the root number $W = \psi([\mathfrak{D}])$ and an entire $\Lambda$. If $\psi = 1$, then $\chi = 1$, and the conclusion holds by Theorem 5.5.10. Thus the conclusion holds for each Hecke character of class group type.

Lean: `Langlands.Tate.IsClassType.heckeFunctionalEquation_of_ne_one`, `Langlands.Tate.IsClassType.heckeFunctionalEquation`

*Proof.* The character $\psi^{-1}$ is not trivial, so $\Lambda(u, \psi^{-1}) = \Lambda_{\psi^{-1}}(u)$ is defined for each $u$.

(1) The function $s \mapsto |d_F|^{-s/2} = e^{-(s/2) \log |d_F|}$ is entire. By part 1 of Theorem 5.5.21 for $\psi$ and for $\psi^{-1}$, the functions $\Lambda_\chi$ and $\Lambda'_\chi$ are products of entire functions.

(2) Let $\mathrm{Re}(s) > 1$. The first identity is Proposition 5.5.32. By part 4 of Theorem 5.5.29, $\chi^{-1}$ is of class group type, and $\psi_{\chi^{-1}} = \psi^{-1}$. So Proposition 5.5.32 for $\chi^{-1}$ gives $\Lambda(s, \chi^{-1}) = 2^{r_2} |d_F|^{-s/2} \Lambda(s, \psi^{-1}) = \Lambda'_\chi(s)$.

(3) By part 1 of Lemma 5.5.18, $|W| = 1$. Let $s \in \mathbb{C}$. Part 4 of Theorem 5.5.21 at the point $u = 1 - s$ gives $\Lambda_\psi(s) = W \, \Lambda_{\psi^{-1}}(1 - s)$. Since $|d_F| > 0$ and $-s/2 = (1/2 - s) - (1 - s)/2$, we have $|d_F|^{-s/2} = |d_F|^{1/2 - s} |d_F|^{-(1 - s)/2}$. So
$$\Lambda_\chi(s) = 2^{r_2} \, |d_F|^{-s/2} \, W \, \Lambda_{\psi^{-1}}(1 - s) = W \, |d_F|^{1/2 - s} \cdot 2^{r_2} \, |d_F|^{-(1 - s)/2} \, \Lambda_{\psi^{-1}}(1 - s) = W \, |d_F|^{1/2 - s} \, \Lambda'_\chi(1 - s).$$

For the last statements, we compare with the Lean statement in Remark 5.5.4. By part 2 of Theorem 5.5.29, $|\chi(x)| = 1 = |x|_\mathbb{A}^0$, so $\sigma = 0$. The statement takes parameters $(n_v, t_v)$ of $\chi$ and $(n'_v, t'_v)$ of $\chi^{-1}$. Proposition 5.5.32 holds for any parameters, so part 2 gives the two identities on the half planes $\mathrm{Re}(s) > 1 - \sigma$ and $\mathrm{Re}(s) > 1 + \sigma$. By part 2 of Proposition 5.5.30, $N(\mathfrak{f}_\chi) = 1$, so part 3 is the functional equation of the statement. Part 1 gives the meromorphy of both functions, and for the poles we take the first case of the disjunction. Now let $\psi = 1$. By part 3 of Theorem 5.5.29, $\chi = 1$. Then Theorem 5.5.10 gives the conclusion, with $W = 1 = \psi([\mathfrak{D}])$ and the second case of the disjunction. $\square$

The theorem agrees with part 3 of Theorem 5.5.3. The characters of class group type and the characters $|\cdot|_\mathbb{A}^{s_0}$ have only the trivial character in common. Indeed, if $|\cdot|_\mathbb{A}^{s_0}$ is of class group type, then part 1 of Lemma 5.5.13 gives $|\iota(y)|^{m_v s_0} = 1$ for each $y \in F_v^\times$ at an infinite place $v$, and so $s_0 = 0$. So $\Lambda(s, \chi)$ is entire for each $\chi \ne 1$ of class group type. The root number $\psi([\mathfrak{D}])$ is the product of the local root numbers, by Remark 5.5.22.

**Example 5.5.34 (the field $\mathbb{Q}(\sqrt{-5})$).** Let $F = \mathbb{Q}(\sqrt{-5})$. Then $\mathcal{O}_F = \mathbb{Z}[\sqrt{-5}]$, $d_F = -20$, $r_2 = 1$ and $h_F = 2$. By Exercise 13, the ideal $\mathfrak{p}_2 = (2, 1 + \sqrt{-5}) = \mathbb{Z} \cdot 2 + \mathbb{Z} (1 + \sqrt{-5})$ is not principal. Let $\psi$ be the nontrivial class group character. Then $\psi([\mathfrak{p}]) = 1$ if $\mathfrak{p}$ is principal, and $\psi([\mathfrak{p}]) = -1$ otherwise. By Remark 5.5.23 there is a Hecke character $\chi$ of class group type with $\psi_\chi = \psi$, and $\chi_v(\varpi_v) = \psi([\mathfrak{p}_v])$ by Proposition 5.5.28. We compute these values. Let $p$ be a prime number.
1. The prime $2$ ramifies, $(2) = \mathfrak{p}_2^2$, and $\psi([\mathfrak{p}_2]) = -1$.
2. The prime $5$ ramifies, $(5) = (\sqrt{-5})^2$, and $\psi([(\sqrt{-5})]) = 1$.
3. Let $p \ne 2, 5$, and assume that $-5$ is not a square modulo $p$. Then $p$ is inert. The prime ideal $(p)$ is principal, so $\psi([(p)]) = 1$, and $N((p)) = p^2$.
4. Let $p \ne 2, 5$, and assume that $-5$ is a square modulo $p$. Then $(p) = \mathfrak{p} \bar{\mathfrak{p}}$ with $\mathfrak{p} \ne \bar{\mathfrak{p}}$ and $N(\mathfrak{p}) = p$. We show that $\psi([\mathfrak{p}]) = \psi([\bar{\mathfrak{p}}]) = (-1)^{(p - 1)/2}$. Since $\mathfrak{p} \bar{\mathfrak{p}}$ is principal, $[\bar{\mathfrak{p}}] = [\mathfrak{p}]^{-1}$, and so $\psi([\bar{\mathfrak{p}}]) = \psi([\mathfrak{p}])$. If $\mathfrak{p} = (\alpha)$ with $\alpha = x + y \sqrt{-5}$, then $p = N(\alpha) = x^2 + 5y^2$. Since $p$ is odd, exactly one of $x$ and $y$ is odd, and $p \equiv x^2 + y^2 \equiv 1 \pmod 4$. If $\mathfrak{p}$ is not principal, then $\mathfrak{p} \mathfrak{p}_2$ is principal, because $\mathrm{Cl}_F$ has order $2$. So $\mathfrak{p} \mathfrak{p}_2 = (\alpha)$ with $\alpha = 2x + y(1 + \sqrt{-5}) \in \mathfrak{p}_2$, and $2p = N(\alpha) = (2x + y)^2 + 5y^2$. Thus $p = 2x^2 + 2xy + 3y^2 = 2x(x + y) + 3y^2$. Since $p$ is odd, $y$ is odd. Then $x$ or $x + y$ is even, and $p \equiv 3 \pmod 4$.

For instance, $3 = 2 \cdot 0^2 + 2 \cdot 0 \cdot 1 + 3 \cdot 1^2$ and $7 = 2 + 2 + 3$, so $\psi = -1$ on the primes above $3$ and $7$, while $29 = 3^2 + 5 \cdot 2^2$ and $41 = 6^2 + 5 \cdot 1^2$, so $\psi = 1$ on the primes above $29$ and $41$. By Theorem 5.5.29, $\chi(\varpi_v^{(v)}) = -1$ at the place $v$ of $\mathfrak{p}_3 = (3, 1 + \sqrt{-5})$. Let $x$ be the idele with the component $3$ at the two places above $3$ and the component $1$ at each other place. Then $I(x) = \mathfrak{p}_3 \bar{\mathfrak{p}}_3 = (3)$, and $\chi(x) = \psi([(3)]) = 1$. Proposition 5.5.31 gives, for $\mathrm{Re}(s) > 1$,
$$L(s, \chi) = L(s, \psi) = \frac{1}{(1 + 2^{-s})(1 - 5^{-s})} \prod_{p \text{ split}} \frac{1}{\big(1 - (-1)^{(p-1)/2} p^{-s}\big)^2} \prod_{p \text{ inert}} \frac{1}{1 - p^{-2s}}.$$
The coefficient of $n^{-s}$ in $L(s, \psi)$ is the sum of $\psi([I])$ over the ideals $I$ of norm $n$. For example, the ideals of norm $6$ are $\mathfrak{p}_2 \mathfrak{p}_3$ and $\mathfrak{p}_2 \bar{\mathfrak{p}}_3$, and $\psi$ is $(-1)(-1) = 1$ on both. This gives
$$L(s, \psi) = 1 - 2^{-s} - 2 \cdot 3^{-s} + 4^{-s} + 5^{-s} + 2 \cdot 6^{-s} - 2 \cdot 7^{-s} - 8^{-s} + 3 \cdot 9^{-s} + \cdots.$$
Here $\psi^{-1} = \psi$ and $\chi^{-1} = \chi$. By Exercise 13, $\mathfrak{D} = (2\sqrt{-5})$ is principal, so $W = 1$. Since $\Gamma_F(s) = \Gamma_\mathbb{C}(s)/2 = (2\pi)^{-s} \Gamma(s)$, Proposition 5.5.32 gives $\Lambda(s, \chi) = 2 (2\pi)^{-s} \Gamma(s) L(s, \psi) = \Gamma_\mathbb{C}(s) L(s, \psi)$ for $\mathrm{Re}(s) > 1$. Theorem 5.5.33 says that this function extends to the entire function $\Lambda_\chi$, with $\Lambda_\chi(s) = 20^{1/2 - s} \Lambda_\chi(1 - s)$. In the form of Theorem 5.5.21, the function $20^{s/2} (2\pi)^{-s} \Gamma(s) L(s, \psi)$ extends to an entire function that is invariant under $s \mapsto 1 - s$. Since $\Gamma$ has a pole at $s = 0$, the continuation of $L(s, \psi)$ vanishes at $s = 0$. Exercise 14 writes $L(s, \psi)$ as a product of two Dirichlet $L$-functions.

**Remark 5.5.35 (the Lean proof).** The file `Langlands/Tate/HeckeUnramified.lean` proves parts 2 to 4 of Lemma 5.5.26, Proposition 5.5.28, Theorem 5.5.29, Propositions 5.5.30 to 5.5.32 and Theorem 5.5.33. Part 1 of Lemma 5.5.26 is `Langlands.HeckeRat.Top.exists_trivial_on_units` in the file `Langlands/Hecke/Rational.lean`. It is stated for each number field, and its step with the powers $w^{2^m}$ is `Langlands.HeckeRat.Top.eq_one_of_forall_pow_two_pow`. Mathlib has no map from the ideles to the fractional ideals. So the file computes with the components of an idele, `Langlands.Tate.ideleInf` and `Langlands.Tate.ideleFin`, and the idele $z_\infty$ of the proof of Lemma 5.5.26 is `Langlands.Tate.infinitePart`. The Lean proof does parts 2 and 3 of the lemma in one step. It puts $U = S \cup T$ and writes $x = z \, x_\infty \, P$ with $P = \prod_{v \in U} x_v^{(v)}$, where $z$ has the properties of part 1. This is `Langlands.Tate.IsClassType.ideleChar_eq_prod`, where `Langlands.Tate.ideleChar` is the composite of $J_F \to C_F$ and $\chi$, and part 2 is its case $S = \emptyset$. The value $\chi_v(\varpi_v)$ is `Langlands.Tate.primeValue`. The valuation of Mathlib on $F_v$ is multiplicative, with the value $\exp(-v(y))$ at $y$, so the exponent $v(y)$ is `-WithZero.log (Valued.v y)`. The ideal $I(x)$ is a finite product over the places where $x_v$ is not a unit, and the finiteness of this set is `Langlands.Tate.finite_valued_ne_one`. The equality of $v(a)$ with the exponent of $\mathfrak{p}_v$ in $(a)$ is `Langlands.Tate.valuation_eq_exp_neg_count`. The character $\psi_\chi$ is `Langlands.Tate.classChar χ hχ`. It comes from $\lambda_\chi$ by `QuotientGroup.lift` and the isomorphism `ClassGroup.equiv` of Mathlib. The first half of part 1 of Lemma 5.5.18 is `Langlands.Tate.norm_classGroupChar`, and part 2 of Theorem 5.5.29 uses it. In part 1 of Proposition 5.5.30, the Lean theorem is the first statement, with `Langlands.Tate.eq_zero_of_forall_param_eq_one` of Remark 5.5.16. The second statement is immediate, and it is not stated in Lean. The Euler product is a case of `Langlands.Tate.hasProd_of_norm`, which is the proof of Proposition 5.5.9 for each multiplicative function $f$ on the nonzero ideals with $|f(I)| = |N(I)^{-s}|$. Its identity for a finite set $S$ is `Langlands.Tate.hasSum_supportedIn_of_norm`, and the function $f$ of the proof of Proposition 5.5.31 is `Langlands.Tate.classCharWeight ψ s`. In Lean the second identity of Proposition 5.5.32 is stated only for $\psi \ne 1$. For $\psi = 1$ it is part 2 of Theorem 5.5.10. In Theorem 5.5.33, $|d_F|^{-s/2}$ is written $(\sqrt{|d_F|})^{-s}$, $\Lambda(s, \psi)$ is `Langlands.Tate.classCharLambda ψ s`, and the identity of the exponents in part 3 is `Langlands.Tate.discr_cpow_mul_sqrt_cpow`. The case $\psi = 1$ is `Langlands.Tate.heckeFunctionalEquationAt_one`. All these theorems use only the standard axioms of Lean. Four questions remain open in Lean. The first is the construction of the Hecke character of a class group character, so the existence of $\chi$ in Example 5.5.34 is not in Lean. The second is the case of the characters of the narrow class group, which can be $\mathrm{sgn}$ at a real place. The third is the case of the ramified Hecke characters. The fourth is the identification of $W$ with the product of the local root numbers in Remark 5.5.22.

### Twists by a power of the norm

Let $\chi$ be a Hecke character of $F$ and let $s_0 \in \mathbb{C}$. The *twist* of $\chi$ by $|\cdot|_\mathbb{A}^{s_0}$ is the Hecke character $\chi |\cdot|_\mathbb{A}^{s_0}$, with the value $\chi(x) |x|_\mathbb{A}^{s_0}$ at an idele $x$. Theorem 5.5.14 is the case $\chi = \mathbf{1}$. This subsection extends its method to each $\chi$ for which the conclusion of `Langlands.HeckeFunctionalEquationAt` is known. A twist moves the variable $s$ by $s_0$ and the exponent $\sigma$ by $\mathrm{Re}(s_0)$, and it multiplies the root number by a number of absolute value $1$. We apply this to the characters of class group type. Then we show that their twists are exactly the Hecke characters that are unramified at each finite place and equal to $|\cdot|_w^{s_0}$ at each infinite place $w$, for one $s_0$. Here $|\cdot|_w$ is the normalized absolute value of $F_w$, so $|y|_w = |\iota(y)|^{m_w}$, with $\iota$ and $m_w$ as in item 1 of Remark 5.5.4.

**Lemma 5.5.36 (the characters $|\cdot|_\mathbb{A}^{s}$).** Let $F$ be a number field and let $s \in \mathbb{C}$.
1. For ideles $x$ and $y$, $|xy|_\mathbb{A} = |x|_\mathbb{A} |y|_\mathbb{A}$. For $a \in F^\times$, $|a|_\mathbb{A} = 1$.
2. The map $x \mapsto |x|_\mathbb{A}$ from $J_F$ to $\mathbb{R}_{>0}$ is continuous.
3. The map $x \mapsto |x|_\mathbb{A}^{s}$ defines a Hecke character $|\cdot|_\mathbb{A}^{s}$. For each Hecke character $\chi$, the product $\chi |\cdot|_\mathbb{A}^{s}$ is a Hecke character with the value $\chi(x) |x|_\mathbb{A}^{s}$ at each idele $x$.

Lean: `Langlands.Tate.ideleNorm_mul`, `Langlands.Tate.ideleNorm_unitEmbedding`, `Langlands.Tate.continuous_ideleNorm`, `Langlands.Tate.continuous_ideleNormPow`, `Langlands.Tate.normPowerChar`, `Langlands.Tate.mul_normPowerChar_apply`

*Proof.* (1) The norm $|x|_\mathbb{A}$ is the product of the numbers $|x_v|_v$, and almost all of them are $1$. Each $|\cdot|_v$ is multiplicative, so the product is multiplicative. The second statement is the product formula, Volume 1, Theorem 3.3.4.

(2) By part 1 the norm is a homomorphism of topological groups $J_F \to \mathbb{R}_{>0}$. So it is enough to prove that it is continuous at $1$. Let $U$ be the set of the ideles $x$ with $x_v \in \mathcal{O}_v^\times$ at each finite place $v$. By the definition of the restricted product topology, $U$ is an open neighbourhood of $1$. For $x \in U$ each factor at a finite place is $1$, so $|x|_\mathbb{A} = \prod_{v \mid \infty} |x_v|_v$. This is a finite product of continuous functions of $x$. So the norm is continuous on $U$, and in particular at $1$.

(3) For real numbers $r, r' > 0$ we have $(r r')^{s} = r^{s} r'^{s}$, because $r^{s} = e^{s \log r}$. With part 1, the map $x \mapsto |x|_\mathbb{A}^{s}$ is a homomorphism $J_F \to \mathbb{C}^\times$ that is trivial on $F^\times$. It is the composite of the norm and the continuous map $r \mapsto r^{s}$, so it is continuous by part 2. Thus it induces a continuous character of $C_F$. A product of two Hecke characters is a Hecke character. $\square$

The subsection on the characters $|\cdot|_\mathbb{A}^{s_0}$ used part 3 without a proof. Its Lean theorem takes a Hecke character $\chi$ with $\chi(x) = |x|_\mathbb{A}^{s_0}$ as a hypothesis, and part 3 gives such a character. For the rest of this subsection, $\chi$ is a Hecke character of $F$, $s_0 \in \mathbb{C}$, and $\xi$ is a Hecke character with $\xi(x) = \chi(x) |x|_\mathbb{A}^{s_0}$ for each idele $x$. So $\xi = \chi |\cdot|_\mathbb{A}^{s_0}$.

**Lemma 5.5.37 (the local data of a twist).** Let $\chi$, $s_0$ and $\xi$ be as above.
1. Let $v$ be an infinite place. Then $\xi_v(y) = \chi_v(y) |\iota(y)|^{m_v s_0}$ for each $y \in F_v^\times$. Let $v$ be a finite place. Then $\xi_v(y) = \chi_v(y) |y|_v^{s_0}$ for each $y \in F_v^\times$.
2. Let $v$ be a finite place and let $m \ge 0$, where $1 + \mathfrak{p}_v^0$ means $\mathcal{O}_v^\times$. Then $\xi_v$ is trivial on $1 + \mathfrak{p}_v^m$ if and only if $\chi_v$ is trivial on $1 + \mathfrak{p}_v^m$. So $\xi$ is unramified at $v$ if and only if $\chi$ is unramified at $v$, and $\mathfrak{f}_\xi = \mathfrak{f}_\chi$.
3. At each finite place $v$, the local factor of $\xi$ at $s$ is the local factor of $\chi$ at $s + s_0$. So the Euler products of $L(s, \xi)$ and $L(s + s_0, \chi)$ are equal factor by factor.
4. Let $v$ be an infinite place. If $(n_v, t_v)$ is a pair of parameters of $\xi$ at $v$, then $(n_v, t_v - s_0)$ is a pair of parameters of $\chi$ at $v$. Let $(n_v, t_v)$ be parameters of $\xi$ at all the infinite places, and form the factors of $\chi$ with the parameters $(n_v, t_v - s_0)$. Then $L_\infty(s, \xi) = L_\infty(s + s_0, \chi)$ and $\Lambda(s, \xi) = \Lambda(s + s_0, \chi)$.
5. For each idele $x$, $\xi^{-1}(x) = \chi^{-1}(x) |x|_\mathbb{A}^{-s_0}$.

Lean: `Langlands.Tate.infiniteComponent_of_twist`, `Langlands.Tate.finiteComponent_of_twist`, `Langlands.Tate.isTrivialOnHigherUnits_twist_iff`, `Langlands.Tate.isUnramifiedAt_twist_iff`, `Langlands.Tate.conductor_of_twist`, `Langlands.Tate.localFactor_of_twist`, `Langlands.Tate.finiteLFunction_of_twist`, `Langlands.Tate.isArchimedeanParameter_of_twist`, `Langlands.Tate.gammaFactor_shift`, `Langlands.Tate.completedLFunction_of_twist`, `Langlands.Tate.inv_of_twist`

*Proof.* (1) Let $y \in F_v^\times$, and let $y^{(v)}$ be the idele of Lemma 5.5.12. Then $\xi_v(y) = \xi(y^{(v)}) = \chi_v(y) |y^{(v)}|_\mathbb{A}^{s_0}$. If $v$ is infinite, then $|y^{(v)}|_\mathbb{A}^{s_0} = (|\iota(y)|^{m_v})^{s_0} = |\iota(y)|^{m_v s_0}$ by part 1 of Lemma 5.5.12, as in the proof of part 1 of Lemma 5.5.13. If $v$ is finite, then $|y^{(v)}|_\mathbb{A} = |y|_v$ by part 2 of Lemma 5.5.12.

(2) Each subgroup $1 + \mathfrak{p}_v^m$ lies in $\mathcal{O}_v^\times$, and $|y|_v = 1$ for $y \in \mathcal{O}_v^\times$. So $\xi_v$ and $\chi_v$ agree on $1 + \mathfrak{p}_v^m$ by part 1. This gives the first statement, and its case $m = 0$ is the statement on ramification. The exponent $a(\chi_v)$ is the smallest $m$ such that $\chi_v$ is trivial on $1 + \mathfrak{p}_v^m$. So $a(\xi_v) = a(\chi_v)$ at each finite place, and the two conductors are equal.

(3) If $\chi$ is ramified at $v$, then $\xi$ is ramified at $v$ by part 2, and both local factors are $1$. Let $\chi$ be unramified at $v$. By part 1 and part 2 of Lemma 5.5.12, $\xi_v(\varpi_v) = \chi_v(\varpi_v) N(\mathfrak{p}_v)^{-s_0}$. Since $N(\mathfrak{p}_v)$ is a positive real number, $N(\mathfrak{p}_v)^{-s_0} N(\mathfrak{p}_v)^{-s} = N(\mathfrak{p}_v)^{-(s + s_0)}$. So
$$\big(1 - \xi_v(\varpi_v) N(\mathfrak{p}_v)^{-s}\big)^{-1} = \big(1 - \chi_v(\varpi_v) N(\mathfrak{p}_v)^{-(s + s_0)}\big)^{-1}.$$

(4) Let $x \in F_v^\times$. We divide the formula of item 1 of Remark 5.5.4 for $\xi_v$ by $|\iota(x)|^{m_v s_0}$, which is not $0$. With part 1 this gives
$$\chi_v(x) = \big(\iota(x)/|\iota(x)|\big)^{n_v} \, |\iota(x)|^{m_v (t_v - s_0)}.$$
The condition $n_v \in \{0, 1\}$ at a real place does not change. So $(n_v, t_v - s_0)$ is a pair of parameters of $\chi$ at $v$. At a real place, the factor of $\chi$ at $s + s_0$ is $\Gamma_\mathbb{R}(s + s_0 + (t_v - s_0) + n_v) = \Gamma_\mathbb{R}(s + t_v + n_v)$, and this is the factor of $\xi$ at $s$. The same computation holds at a complex place, with $\Gamma_\mathbb{C}$ and $|n_v|/2$. This gives the identity of the archimedean factors, and part 3 gives the identity of the completed $L$-functions.

(5) We have $\xi^{-1}(x) = \chi(x)^{-1} (|x|_\mathbb{A}^{s_0})^{-1}$, and $(|x|_\mathbb{A}^{s_0})^{-1} = |x|_\mathbb{A}^{-s_0}$. $\square$

Part 2 says that a twist does not change the ramification. Part 4 says that a twist moves the parameters $t_v$ and keeps the parameters $n_v$. By part 5 the lemma also applies to $\chi^{-1}$ and $\xi^{-1}$, with $-s_0$ in place of $s_0$. So parameters $(n'_v, t'_v)$ of $\xi^{-1}$ give the parameters $(n'_v, t'_v + s_0)$ of $\chi^{-1}$.

**Lemma 5.5.38 (the shift lemma).** Let $\chi$, $s_0$ and $\xi$ be as above. Let $(n_v, t_v)$ and $(n'_v, t'_v)$ be parameters of $\xi$ and of $\xi^{-1}$ at the infinite places. Assume that the conclusion of `Langlands.HeckeFunctionalEquationAt` holds for $\chi$ with the parameters $(n_v, t_v - s_0)$ of $\chi$ and $(n'_v, t'_v + s_0)$ of $\chi^{-1}$, with the exponent $\sigma$, the functions $\Lambda$ and $\Lambda'$, and the root number $W$. Put $D = |d_F| \, N(\mathfrak{f}_\chi)$ and
$$\sigma_\xi = \sigma + \mathrm{Re}(s_0), \qquad \Lambda_\xi(s) = \Lambda(s + s_0), \qquad \Lambda'_\xi(u) = \Lambda'(u - s_0), \qquad W_\xi = W \, D^{\mathrm{Re}(s_0) - s_0}.$$
1. For each idele $x$, $|\xi(x)| = |x|_\mathbb{A}^{\sigma_\xi}$.
2. The functions $\Lambda_\xi$ and $\Lambda'_\xi$ are meromorphic on $\mathbb{C}$.
3. For $\mathrm{Re}(s) > 1 - \sigma_\xi$, $\Lambda_\xi(s) = \Lambda(s, \xi)$. For $\mathrm{Re}(u) > 1 + \sigma_\xi$, $\Lambda'_\xi(u) = \Lambda(u, \xi^{-1})$.
4. We have $|W_\xi| = 1$, and $\Lambda_\xi(s) = W_\xi \, \big(|d_F| \, N(\mathfrak{f}_\xi)\big)^{1/2 - s - \sigma_\xi} \, \Lambda'_\xi(1 - s)$ for each $s \in \mathbb{C}$.
5. If $\Lambda$ is entire, then $\Lambda_\xi$ is entire. Let $s_1 \in \mathbb{C}$ with $\chi = |\cdot|_\mathbb{A}^{s_1}$, and assume that $\Lambda$ is holomorphic outside $\{-s_1, 1 - s_1\}$, with simple poles at both points. Then $\xi = |\cdot|_\mathbb{A}^{s_1 + s_0}$, and $\Lambda_\xi$ is holomorphic outside $\{-(s_1 + s_0), 1 - (s_1 + s_0)\}$, with simple poles at both points.

So the conclusion of `Langlands.HeckeFunctionalEquationAt` holds for $\xi$, with the exponent $\sigma_\xi$, the functions $\Lambda_\xi$ and $\Lambda'_\xi$, and the root number $W_\xi$.

Lean: `Langlands.Tate.heckeFunctionalEquation_of_twist`

*Proof.* (1) By part 3 of Lemma 5.5.12, $|x|_\mathbb{A} > 0$, so the absolute value of $|x|_\mathbb{A}^{s_0}$ is $|x|_\mathbb{A}^{\mathrm{Re}(s_0)}$. Thus $|\xi(x)| = |x|_\mathbb{A}^{\sigma} |x|_\mathbb{A}^{\mathrm{Re}(s_0)} = |x|_\mathbb{A}^{\sigma_\xi}$.

(2) A translate of a meromorphic function on $\mathbb{C}$ is meromorphic on $\mathbb{C}$.

(3) Let $\mathrm{Re}(s) > 1 - \sigma_\xi$. Then $\mathrm{Re}(s + s_0) > 1 - \sigma$. By part 4 of Lemma 5.5.37 and the hypothesis on $\Lambda$, $\Lambda(s, \xi) = \Lambda(s + s_0, \chi) = \Lambda(s + s_0) = \Lambda_\xi(s)$. Let $\mathrm{Re}(u) > 1 + \sigma_\xi$. Then $\mathrm{Re}(u - s_0) > 1 + \sigma$. By part 5 of Lemma 5.5.37, part 4 of the lemma applies to $\chi^{-1}$ and $\xi^{-1}$, with $-s_0$ in place of $s_0$. It gives $\Lambda(u, \xi^{-1}) = \Lambda(u - s_0, \chi^{-1}) = \Lambda'(u - s_0) = \Lambda'_\xi(u)$.

(4) The discriminant $d_F$ is not $0$, and $\mathfrak{f}_\chi$ is a nonzero ideal. So $D \ge 1$. Then $|D^{\mathrm{Re}(s_0) - s_0}| = D^{\mathrm{Re}(\mathrm{Re}(s_0) - s_0)} = D^0 = 1$, and $|W_\xi| = |W| = 1$. By part 2 of Lemma 5.5.37, $|d_F| \, N(\mathfrak{f}_\xi) = D$. Let $s \in \mathbb{C}$. The functional equation of $\chi$ at the point $s + s_0$ gives
$$\Lambda_\xi(s) = W \, D^{1/2 - s - s_0 - \sigma} \, \Lambda'(1 - s - s_0) = W \, D^{\mathrm{Re}(s_0) - s_0} \, D^{1/2 - s - \sigma_\xi} \, \Lambda'_\xi(1 - s).$$
In the second step we use $1/2 - s - s_0 - \sigma = (\mathrm{Re}(s_0) - s_0) + (1/2 - s - \sigma_\xi)$, and that $D$ is a positive real number.

(5) The function $\Lambda_\xi$ is holomorphic at $s$ if and only if $\Lambda$ is holomorphic at $s + s_0$, and the order of $\Lambda_\xi$ at $s$ is the order of $\Lambda$ at $s + s_0$. This gives the first statement. In the second statement, $\xi(x) = |x|_\mathbb{A}^{s_1} |x|_\mathbb{A}^{s_0} = |x|_\mathbb{A}^{s_1 + s_0}$ for each idele $x$. The point $s + s_0$ is $-s_1$ or $1 - s_1$ if and only if $s$ is $-(s_1 + s_0)$ or $1 - (s_1 + s_0)$.

Parts 1 to 5 are the clauses of the Lean statement of Remark 5.5.4 for $\xi$. This proves the last statement. $\square$

For $\chi = \mathbf{1}$ the lemma gives Theorem 5.5.14 again. Then $\sigma = 0$, $W = 1$ and $D = |d_F|$, so $W_\xi = |d_F|^{\mathrm{Re}(s_0) - s_0}$ is the root number of Remark 5.5.15. In general the factor $D^{\mathrm{Re}(s_0) - s_0} = D^{-i \, \mathrm{Im}(s_0)}$ has the same source as in Remark 5.5.15. The Lean statement has the real exponent $\sigma_\xi$ in the factor $D^{1/2 - s - \sigma_\xi}$, so the imaginary part of $s_0$ goes into the root number. The lemma does not use the arithmetic of $\chi$. It moves a known functional equation along the variable $s$.

**Proposition 5.5.39 (the twists of characters of class group type).** Let $\chi$ be a Hecke character of $F$ of class group type, put $\psi = \psi_\chi$, and let $s_0$ and $\xi$ be as above.
1. The character $\xi$ is unramified at each finite place $v$, its conductor is $\mathcal{O}_F$, and its local factor at $v$ is $\big(1 - \psi([\mathfrak{p}_v]) N(\mathfrak{p}_v)^{-s - s_0}\big)^{-1}$.
2. Let $v$ be an infinite place. If $(n_v, t_v)$ is a pair of parameters of $\xi$ at $v$, then $n_v = 0$ and $t_v = s_0$.
3. Let $(n_v, t_v)$ be parameters of $\xi$ at the infinite places. Then $\Lambda(s, \xi) = \Lambda(s + s_0, \chi)$, where the factors of $\chi$ are formed with the parameters $(0, 0)$. For $\mathrm{Re}(s + s_0) > 1$,
$$\Lambda(s, \xi) = 2^{r_2} \, |d_F|^{-(s + s_0)/2} \, \Lambda(s + s_0, \psi).$$

Lean: `Langlands.Tate.IsClassType.isUnramifiedAt_twist`, `Langlands.Tate.IsClassType.localFactor_twist`, `Langlands.Tate.IsClassType.isArchimedeanParameter_twist`, `Langlands.Tate.IsClassType.completedLFunction_twist`, `Langlands.Tate.IsClassType.completedLFunction_twist_eq_classCharLambda`

*Proof.* (1) By parts 2 and 3 of Proposition 5.5.30, $\chi$ is unramified at each finite place, its conductor is $\mathcal{O}_F$, and its local factor at $v$ is $\big(1 - \psi([\mathfrak{p}_v]) N(\mathfrak{p}_v)^{-s}\big)^{-1}$. Parts 2 and 3 of Lemma 5.5.37 give the same facts for $\xi$, with $s + s_0$ in place of $s$ in the local factor.

(2) By part 4 of Lemma 5.5.37, $(n_v, t_v - s_0)$ is a pair of parameters of $\chi$ at $v$. By part 1 of Proposition 5.5.30, $n_v = 0$ and $t_v - s_0 = 0$.

(3) By part 2, the parameters of $\chi$ in part 4 of Lemma 5.5.37 are $(0, s_0 - s_0) = (0, 0)$, and that lemma gives the first identity. Let $\mathrm{Re}(s + s_0) > 1$. Then Proposition 5.5.32 at the point $s + s_0$ gives the second identity. $\square$

**Theorem 5.5.40 (Hecke's theorem for the twists of characters of class group type).** Let $\chi$ be a Hecke character of $F$ of class group type, put $\psi = \psi_\chi$, and let $s_0$ and $\xi = \chi |\cdot|_\mathbb{A}^{s_0}$ be as above. Then the conclusion of `Langlands.HeckeFunctionalEquationAt` holds for $\xi$, with the exponent $\mathrm{Re}(s_0)$ and the root number $\psi([\mathfrak{D}]) \, |d_F|^{\mathrm{Re}(s_0) - s_0}$.
1. If $\psi \ne 1$, then the function of the conclusion is the entire function $\Lambda_\xi(s) = 2^{r_2} \, |d_F|^{-(s + s_0)/2} \, \Lambda(s + s_0, \psi)$.
2. If $\psi = 1$, then $\xi = |\cdot|_\mathbb{A}^{s_0}$, and the function of the conclusion is holomorphic outside $\{-s_0, 1 - s_0\}$, with simple poles at both points.

Lean: `Langlands.Tate.IsClassType.heckeFunctionalEquation_twist`, `Langlands.Tate.IsClassType.heckeFunctionalEquation_mul_normPowerChar`

*Proof.* Let $(n_v, t_v)$ and $(n'_v, t'_v)$ be parameters of $\xi$ and of $\xi^{-1}$. By part 4 of Lemma 5.5.37 and the remark after it, $(n_v, t_v - s_0)$ and $(n'_v, t'_v + s_0)$ are parameters of $\chi$ and of $\chi^{-1}$. Theorem 5.5.33 holds for all parameters. So it gives the conclusion for $\chi$ with these parameters, with $\sigma = 0$ and $W = \psi([\mathfrak{D}])$. By part 2 of Proposition 5.5.30, $N(\mathfrak{f}_\chi) = 1$, so $D = |d_F|$ in Lemma 5.5.38. That lemma gives the conclusion for $\xi$, with $\sigma_\xi = \mathrm{Re}(s_0)$ and $W_\xi = \psi([\mathfrak{D}]) \, |d_F|^{\mathrm{Re}(s_0) - s_0}$.

(1) Let $\psi \ne 1$. The function of Theorem 5.5.33 is the entire function $\Lambda_\chi(s) = 2^{r_2} |d_F|^{-s/2} \Lambda(s, \psi)$. The function for $\xi$ is $\Lambda_\chi(s + s_0)$, and it is entire by part 5 of Lemma 5.5.38.

(2) Let $\psi = 1$. Then $\chi = \mathbf{1}$ by part 3 of Theorem 5.5.29, and $\xi = |\cdot|_\mathbb{A}^{s_0}$. In this case Theorem 5.5.33 uses the function $\Lambda$ of Theorem 5.5.10, which has simple poles at $0$ and $1$ and no other poles. This is the case $s_1 = 0$ of part 5 of Lemma 5.5.38, and the lemma gives the poles at $-s_0$ and $1 - s_0$. $\square$

For $\psi = 1$ the theorem is Theorem 5.5.14, with the same root number, because $\psi([\mathfrak{D}]) = 1$. For an example with $\psi \ne 1$, let $F = \mathbb{Q}(\sqrt{-5})$ and let $\chi$ be the character of Example 5.5.34. By Proposition 5.5.39 and the computation of Example 5.5.34, $\Lambda(s, \xi) = \Gamma_\mathbb{C}(s + s_0) \, L(s + s_0, \psi)$ for $\mathrm{Re}(s + s_0) > 1$. This function extends to an entire function, and its root number is $20^{\mathrm{Re}(s_0) - s_0}$.

**Proposition 5.5.41 (the characterization of the twists).** Let $\xi$ be a Hecke character of $F$ and let $s_0 \in \mathbb{C}$. These two conditions are equivalent.
1. The character $\xi$ is unramified at each finite place, and $\xi_w(y) = |y|_w^{s_0} = |\iota(y)|^{m_w s_0}$ for each infinite place $w$ and each $y \in F_w^\times$.
2. There is a Hecke character $\chi$ of class group type with $\xi(x) = \chi(x) |x|_\mathbb{A}^{s_0}$ for each idele $x$.

Lean: `Langlands.Tate.exists_isClassType_twist_iff`

*Proof.* Assume condition 2. By part 1 of Proposition 5.5.39, $\xi$ is unramified at each finite place. Let $w$ be an infinite place and let $y \in F_w^\times$. The character $\chi_w$ is trivial by Definition 5.5.25, so part 1 of Lemma 5.5.37 gives $\xi_w(y) = |\iota(y)|^{m_w s_0}$. Also $|y|_w^{s_0} = (|\iota(y)|^{m_w})^{s_0} = |\iota(y)|^{m_w s_0}$.

Assume condition 1. By part 3 of Lemma 5.5.36, $\chi = \xi |\cdot|_\mathbb{A}^{-s_0}$ is a Hecke character. For each idele $x$, $\chi(x) |x|_\mathbb{A}^{s_0} = \xi(x) |x|_\mathbb{A}^{-s_0} |x|_\mathbb{A}^{s_0} = \xi(x)$. So Lemma 5.5.37 applies to $\chi$, $s_0$ and $\xi$. By part 2 of Lemma 5.5.37, $\chi$ is unramified at each finite place $v$, that is, $\chi_v$ is trivial on $\mathcal{O}_v^\times$. Let $w$ be an infinite place and let $y \in F_w^\times$. By part 1 of Lemma 5.5.37 and condition 1, $\chi_w(y) \, |\iota(y)|^{m_w s_0} = |\iota(y)|^{m_w s_0}$. The number $|\iota(y)|^{m_w s_0} = e^{m_w s_0 \log |\iota(y)|}$ is not $0$, so $\chi_w(y) = 1$. Thus $\chi$ is of class group type. $\square$

By part 1 of Theorem 5.5.29, the characters of the proposition are the characters $x \mapsto \psi([I(x)]) \, |x|_\mathbb{A}^{s_0}$, with a class group character $\psi$. By condition 1 and item 1 of Remark 5.5.4, $(0, s_0)$ is a pair of parameters of $\xi$ at each infinite place, and by part 2 of Proposition 5.5.39 it is the only one. In the same way $(0, -s_0)$ is the only pair of parameters of $\xi^{-1}$. So the hypotheses on the parameters in the next theorem can be met, and the theorem is not empty.

**Theorem 5.5.42 (Hecke's theorem for the unramified characters with one infinite exponent).** Let $\xi$ be a Hecke character of $F$ and let $s_0 \in \mathbb{C}$. Assume that $\xi$ is unramified at each finite place and that $\xi_w = |\cdot|_w^{s_0}$ at each infinite place $w$. Let $\psi$ be the class group character of the character $\xi |\cdot|_\mathbb{A}^{-s_0}$ of class group type. Then the conclusion of `Langlands.HeckeFunctionalEquationAt` holds for $\xi$, with the exponent $\mathrm{Re}(s_0)$ and the root number $\psi([\mathfrak{D}]) \, |d_F|^{\mathrm{Re}(s_0) - s_0}$. If $\xi \ne |\cdot|_\mathbb{A}^{s_0}$, then the function of the conclusion is entire. If $\xi = |\cdot|_\mathbb{A}^{s_0}$, then it is holomorphic outside $\{-s_0, 1 - s_0\}$, with simple poles at both points.

Lean: `Langlands.Tate.heckeFunctionalEquation_of_unramified`

*Proof.* By the proof of Proposition 5.5.41, $\chi = \xi |\cdot|_\mathbb{A}^{-s_0}$ is of class group type, and $\xi = \chi |\cdot|_\mathbb{A}^{s_0}$. So Theorem 5.5.40 applies to $\chi$. By part 3 of Theorem 5.5.29, $\psi = 1$ implies $\chi = \mathbf{1}$. Conversely, $\chi = \mathbf{1}$ gives $\lambda_\chi = 1$ and $\psi = 1$. So $\psi = 1$ if and only if $\xi = |\cdot|_\mathbb{A}^{s_0}$, and the two cases of Theorem 5.5.40 give the last two statements. $\square$

**Remark 5.5.43 (the Lean proof).** The file `Langlands/Tate/HeckeClassTwist.lean` proves Lemmas 5.5.36 to 5.5.38, Proposition 5.5.39, Theorem 5.5.40, Proposition 5.5.41 and Theorem 5.5.42. The Hecke character $|\cdot|_\mathbb{A}^{s}$ is `Langlands.Tate.normPowerChar K s`. It comes from the homomorphism `Langlands.Tate.ideleNormPow K s` on the ideles by `QuotientGroup.lift`, and the norm as a homomorphism is `Langlands.Tate.ideleNormHom`. The product formula is `AdeleRing.norm_algebraMap_eq_one_of_ne_zero` of Mathlib. In part 2 of Lemma 5.5.36 the Lean proof takes for $U$ the ideles $x$ with $x_v \in \mathcal{O}_v$ and $(x^{-1})_v \in \mathcal{O}_v$ at each finite place $v$. This set is open by `RestrictedProduct.isOpen_forall_mem` of Mathlib, and `continuous_of_continuousAt_one` of Mathlib gives the continuity from the continuity at $1$. In Lemmas 5.5.37 and 5.5.38 and in Proposition 5.5.39, the twist is not a product of characters. It is a hypothesis on two Hecke characters $\chi$ and $\xi$, that $\xi(x) = \chi(x) \|x\|^{s_0}$ for each idele $x$. The product `χ * normPowerChar K s₀` satisfies this hypothesis by `Langlands.Tate.mul_normPowerChar_apply`. In Lemma 5.5.38 the root number is `W * (r : ℂ) ^ ((s₀.re : ℂ) - s₀)`, where the real number $r$ is $D$, and the proof of $D > 0$ uses `Langlands.Tate.conductor_ne_bot`. The translations in parts 2 and 5 use `meromorphicAt_fun_comp_add_const_iff_meromorphicAt`, `meromorphicAt_fun_comp_sub_const_iff_meromorphicAt` and `meromorphicOrderAt_fun_comp_add_const_eq_meromorphicOrderAt` of Mathlib. As in Proposition 5.5.32, Lean states the second identity of part 3 of Proposition 5.5.39 only for $\psi \ne 1$. The Lean statements of Theorems 5.5.40 and 5.5.42 are the conclusion of `Langlands.HeckeFunctionalEquationAt`. The root number and the function of part 1 of Theorem 5.5.40 are in the Lean proof, through `Langlands.Tate.IsClassType.heckeFunctionalEquation` and Lemma 5.5.38, and not in the statement. The uniqueness of the parameters $(0, s_0)$ after Proposition 5.5.41 is part 2 of Proposition 5.5.39, and their existence is not stated in Lean. All these theorems use only the standard axioms of Lean.

**Remark 5.5.44 (what remains).** With Theorem 5.5.42, the Lean project proves the conclusion of `Langlands.HeckeFunctionalEquationAt` for each Hecke character that is unramified at each finite place and has the parameters $n_v = 0$ and $t_v = s_0$ at each infinite place $v$, with one $s_0$. Two classes of Hecke characters remain.
1. *Other infinite types.* These characters can be unramified at each finite place, but they have $n_v \ne 0$ at some infinite place, or parameters $t_v$ that are not all equal. A character of the narrow class group with $\mathrm{sgn}$ at a real place has $n_v = 1$ there, as in Remark 5.5.23. For $F = \mathbb{Q}(i)$ the units are the fourth roots of unity and $\mathcal{O}_F$ is a principal ideal domain. So $(\alpha) \mapsto (\alpha / |\alpha|)^4$ is well defined on the nonzero ideals, and it gives an unramified Hecke character with $|n_v| = 4$ at the complex place. The Hecke characters of an imaginary quadratic field that come from elliptic curves with complex multiplication are of this kind. For the curve $E : y^2 = x^3 - x$, which has complex multiplication by $\mathbb{Z}[i]$, Deuring proved that $L(E, s)$ is the $L$-function of a Hecke character $\psi_E$ of $\mathbb{Q}(i)$. This character has $|n_v| = 1$ at the complex place. The proof of Theorem 5.5.3 treats these characters with the local functions of Propositions 5.2.5 and 5.2.6, which contain the factors $x^a$, $\bar z^n$ and $z^{|n|}$. A proof in Lean needs these functions, or Hecke's theta series with a harmonic polynomial.
2. *Ramified characters.* The Dirichlet characters of Example 5.5.6 with $N > 1$ are ramified, and so is $\psi_E$, whose conductor is $(1 + i)^3$. A proof needs the local theory of Proposition 5.2.4 at the ramified places, or a theta function with a character of a ray class group, and the identification of the root number with a product of Gauss sums. The subsection below proves in Lean the results on the characters of ray class type that do not need the functional equation, and it states the functional equation without a Lean proof.

The other open questions of Remark 5.5.35 also remain. These are the construction of the Hecke character of a class group character and the identification of the root number with the product of the local root numbers.

### Hecke characters of ray class type

This subsection treats the ramified characters of item 2 of Remark 5.5.44 in the simplest case: characters that are trivial at each infinite place. They are the characters of the ray class groups of $F$. The file `Langlands/Tate/HeckeRamified.lean` proves in Lean the numbered results 5.5.45 to 5.5.49 of this subsection. It does not prove formula (5.5.2) or the functional equation. For a finite place $v$ we write $a_v = a(\chi_v)$ for the conductor exponent of Definition 4.1.3, which exists by Proposition 5.2.13, and $U_v^{(m)} = 1 + \mathfrak{p}_v^m$, with $U_v^{(0)} = \mathcal{O}_v^\times$.

**Definition 5.5.45 (characters of ray class type).** Let $F$ be a number field. A Hecke character $\chi$ of $F$ is *of ray class type* if, at each infinite place $v$, the local component $\chi_v$ is trivial on $F_v^\times$.

Lean: `Langlands.Tate.IsRayClassType`, `Langlands.Tate.IsClassType.isRayClassType`, `Langlands.Tate.IsRayClassType.isClassType`, `Langlands.Tate.IsRayClassType.inv`

So a character of class group type, in the sense of Definition 5.5.25, is a character of ray class type that is unramified at every finite place. If $\chi$ is of ray class type, then so is $\chi^{-1}$. In Example 5.5.6 the component at the real place is $\mathrm{sgn}^a$, with $\eta(-1) = (-1)^a$. So the character of an even Dirichlet character is of ray class type, and the character of an odd one is not. The odd characters belong to the narrow ray class groups, which we leave aside, as in item 1 of Remark 5.5.44.

**Proposition 5.5.46 (the ramified places and the conductor).** Let $\chi$ be a Hecke character of $F$, and let $R(\chi)$ be the set of the finite places at which $\chi$ is ramified.
1. The set $R(\chi)$ is finite.
2. For each finite place $v$, $a_v = 0$ if and only if $\chi$ is unramified at $v$. So $a_v \ge 1$ for $v \in R(\chi)$.
3. The conductor is $\mathfrak{f}_\chi = \prod_{v \in R(\chi)} \mathfrak{p}_v^{a_v}$.
4. For each finite place $v$, $a(\chi_v^{-1}) = a_v$. So $\mathfrak{f}_{\chi^{-1}} = \mathfrak{f}_\chi$.
5. For each finite place $v$ and each $u \in \mathcal{O}_v^\times$, $\chi_v(u)$ is a root of unity, and $|\chi_v(u)| = 1$.

Lean: `Langlands.Tate.finite_setOf_not_isUnramifiedAt`, `Langlands.Tate.ramifiedSet`, `Langlands.Tate.conductorExponent_eq_zero_iff`, `Langlands.Tate.conductor_eq_prod`, `Langlands.Tate.conductorExponent_inv`, `Langlands.Tate.conductor_inv`, `Langlands.Tate.norm_finiteComponent_of_valued_eq_one`

The proposition holds for every Hecke character, not only for those of ray class type. Part 1 comes directly from the continuity of $\chi$, through Lemma 5.5.26.

*Proof.* (1) Let $T$ be as in part 1 of Lemma 5.5.26, let $v \notin T$ be finite and let $u \in \mathcal{O}_v^\times$. The idele $u^{(v)}$ has the properties of part 1 of Lemma 5.5.26, so $\chi_v(u) = \chi(u^{(v)}) = 1$. Thus $R(\chi) \subset T$.

(2) By definition, $a_v$ is the smallest $m \ge 0$ such that $\chi_v$ is trivial on $U_v^{(m)}$. Since $U_v^{(0)} = \mathcal{O}_v^\times$, we have $a_v = 0$ exactly when $\chi_v$ is trivial on $\mathcal{O}_v^\times$, which is the definition of an unramified place.

(3) In the product of part 1 of Definition 5.5.1, the factor at $v$ is $\mathfrak{p}_v^0 = \mathcal{O}_F$ for each $v \notin R(\chi)$, by part 2. We remove these factors.

(4) The local component of $\chi^{-1}$ at $v$ is $\chi_v^{-1}$. It is trivial on a subgroup exactly when $\chi_v$ is.

(5) Let $m = a_v$. If $m = 0$, then $\chi_v(u) = 1$. Let $m \ge 1$. By Lemma 5.2.14 the group $(\mathcal{O}_v / \mathfrak{p}_v^m)^\times$ is finite. Let $N$ be its order. Then $u^N \equiv 1$ modulo $\mathfrak{p}_v^m$, so $u^N \in U_v^{(m)}$, and $\chi_v(u)^N = \chi_v(u^N) = 1$. $\square$

**Lemma 5.5.47 (the values of a character of ray class type).** Let $\chi$ be a Hecke character of $F$ of ray class type.
1. Let $S$ be a finite set of finite places with $R(\chi) \subset S$, and let $x$ be an idele with $x_v \in \mathcal{O}_v^\times$ for each finite place $v \notin S$. Then $\chi(x) = \prod_{v \in S} \chi_v(x_v)$.
2. For each idele $x$, $|\chi(x)| = 1$. So $\chi$ is unitary, its exponent in Proposition 5.4.2 is $\sigma = 0$, and $\chi^{-1} = \bar\chi$.
3. Let $v$ be an infinite place. The only pair of parameters of $\chi$ at $v$, in the sense of item 1 of Remark 5.5.4, is $(0, 0)$.

Lean: `Langlands.Tate.IsRayClassType.ideleChar_eq_prod`, `Langlands.Tate.IsRayClassType.norm_apply`, `Langlands.Tate.IsRayClassType.norm_eq_ideleNorm_rpow`, `Langlands.Tate.IsRayClassType.isArchimedeanParameter`

*Proof.* (1) Let $T$ and $k$ be as in part 1 of Lemma 5.5.26, and put $U = S \cup T$. Let $x_\infty$ be the idele with the components of $x$ at the infinite places and $1$ at the finite places. Let $z$ be the idele with the component $1$ at the infinite places and at the places of $U$, and the component $x_v$ at each other finite place $v$. Then
$$x = x_\infty \, z \prod_{v \in U} x_v^{(v)}.$$
Here $\chi(x_\infty) = 1$ because $\chi$ is trivial at the infinite places, and $\chi(z) = 1$ by part 1 of Lemma 5.5.26. For $v \in U \smallsetminus S$, $x_v$ is a unit and $\chi$ is unramified at $v$, so $\chi(x_v^{(v)}) = 1$. The factors at the places of $S$ remain.

(2) The map $|\chi| : x \mapsto |\chi(x)|$ is a Hecke character. Its local components $|\chi_v|$ are trivial at the infinite places, and trivial on $\mathcal{O}_v^\times$ at the finite places by part 5 of Proposition 5.5.46. So $|\chi|$ is of class group type, and part 2 of Theorem 5.5.29 gives $\big| |\chi(x)| \big| = 1$. Since $|\chi(x)| > 0$, it is $1$.

(3) The character $\chi_v$ is trivial, and the proof of part 1 of Proposition 5.5.30 applies without change. $\square$

**Theorem 5.5.48 (reciprocity on principal ideals).** Let $\chi$ be a Hecke character of $F$ of ray class type, with conductor $\mathfrak{f} = \prod_{v \in R(\chi)} \mathfrak{p}_v^{a_v}$, and let $\lambda_\chi$ be its ideal character, as in Definition 5.5.27. Let $x \in F^\times$, and assume that $x \in U_v^{(a_v)}$, that is $v(x - 1) \ge a_v$, at each place $v \in R(\chi)$. Then $\lambda_\chi((x)) = 1$.

Lean: `Langlands.Tate.IsRayClassType.idealChar_toPrincipalIdeal`

*Proof.* Let $v \in R(\chi)$. Then $a_v \ge 1$, so $v(x - 1) > 0 = v(1)$, and the strict triangle inequality gives $v(x) = 0$. Let $S$ be the union of $R(\chi)$ and the finite set of the finite places $v$ with $v(x) \ne 0$. The principal idele $x$ has unit components outside $S$. Since $\chi$ is trivial on $F^\times$, part 1 of Lemma 5.5.47 gives
$$1 = \chi(x) = \prod_{v \in S} \chi_v(x) = \prod_{v \in S \smallsetminus R(\chi)} \chi_v(x) = \prod_{v \in S \smallsetminus R(\chi)} \chi_v(\varpi_v)^{v(x)} = \lambda_\chi((x)).$$
In the third step we use that $\chi_v$ is trivial on $U_v^{(a_v)}$ for $v \in R(\chi)$. In the fourth step we use that $x \varpi_v^{-v(x)}$ is a unit at the unramified places, as in part 4 of Lemma 5.5.26. In the last step we use that $v(x) = 0$ for $v \notin S$ and for $v \in R(\chi)$. $\square$

We put the theorem in the classical language. Let $I^{\mathfrak{f}}$ be the group of the fractional ideals prime to $\mathfrak{f}$, and let $P^{\mathfrak{f}}_1$ be its subgroup of the ideals $(x)$ with $x \in U_v^{(a_v)}$ for each $v \mid \mathfrak{f}$. The quotient $\mathrm{Cl}_\mathfrak{f} = I^{\mathfrak{f}} / P^{\mathfrak{f}}_1$ is the ray class group modulo $\mathfrak{f}$, see [Neu99], Chapter VI, Section 1. On $I^{\mathfrak{f}}$ the character $\lambda_\chi$ uses only the unramified places, so it is the character $\chi^*$ of Definition 5.5.1. Theorem 5.5.48 says that $\chi^*$ is trivial on $P^{\mathfrak{f}}_1$, so it is a character of the finite group $\mathrm{Cl}_\mathfrak{f}$, see Exercise 21. Conversely, each character of $\mathrm{Cl}_\mathfrak{f}$ is $\chi^*$ for a unique Hecke character $\chi$ of ray class type with $\mathfrak{f}_\chi \mid \mathfrak{f}$, by the isomorphism $J_F / F^\times W_\mathfrak{f} \cong \mathrm{Cl}_\mathfrak{f}$ of Exercise 21. The Lean project does not construct $\chi$ from a character of $\mathrm{Cl}_\mathfrak{f}$.

The proof of Theorem 5.5.48 gives more. Let $x \in F^\times$ with $v(x) = 0$ for each $v \in R(\chi)$, so that $(x) \in I^{\mathfrak{f}}$, but with no congruence condition. The same computation, without the third step, gives
$$\chi^*((x)) = \prod_{v \in R(\chi)} \chi_v(x)^{-1}. \tag{5.5.2}$$
So the values of $\chi^*$ on the principal ideals are fixed by the restrictions of the $\chi_v$ to $\mathcal{O}_v^\times$ at the ramified places. Example 5.5.6 shows the inverse in (5.5.2): there $\chi_\ell = \eta_\ell^{-1}$ on $\mathbb{Z}_\ell^\times$, while $\chi^*((p)) = \eta(p)$.

**Proposition 5.5.49 (the Dirichlet series).** Let $\chi$ be a Hecke character of $F$ of ray class type, with conductor $\mathfrak{f}$, and let $\mathrm{Re}(s) > 1$. For a nonzero ideal $I$ of $\mathcal{O}_F$, put $w_s(I) = \lambda_\chi(I) N(I)^{-s}$ if $I$ is prime to $\mathfrak{f}$, and $w_s(I) = 0$ otherwise.
1. We have $w_s(IJ) = w_s(I) w_s(J)$, $w_s(\mathcal{O}_F) = 1$ and $|w_s(I)| \le N(I)^{-\mathrm{Re}(s)}$.
2. The product of the local factors of $\chi$ over the finite places converges unconditionally, and
$$L(s, \chi) = \prod_{\mathfrak{p} \nmid \mathfrak{f}} \big(1 - \chi^*(\mathfrak{p}) N(\mathfrak{p})^{-s}\big)^{-1} = \sum_{(I, \mathfrak{f}) = 1} \chi^*(I) N(I)^{-s},$$
where $I$ runs over the nonzero ideals of $\mathcal{O}_F$ prime to $\mathfrak{f}$.

Lean: `Langlands.Tate.rayWeight`, `Langlands.Tate.IsRayClassType.norm_rayWeight_le`, `Langlands.Tate.IsRayClassType.hasProd_localFactor`, `Langlands.Tate.IsRayClassType.finiteLFunction_eq`

*Proof.* (1) The product $IJ$ is prime to $\mathfrak{f}$ if and only if both $I$ and $J$ are, and $\lambda_\chi$ and $N$ are multiplicative. For the bound, $\lambda_\chi(I)$ is a product of powers of the numbers $\chi_v(\varpi_v) = \chi(\varpi_v^{(v)})$, which have absolute value $1$ by Lemma 5.5.47.

(2) The proof of part 1 of Proposition 5.5.31 uses only the properties of part 1, and it works with the inequality in place of an equality. So the product of the factors $(1 - w_s(\mathfrak{p}))^{-1}$ converges unconditionally to $\sum_I w_s(I)$. Let $\mathfrak{p} = \mathfrak{p}_v$. If $v \in R(\chi)$, then $w_s(\mathfrak{p}) = 0$, and the factor is $1$, which is the local factor of $\chi$ at $v$ by Corollary 5.2.21. If $v \notin R(\chi)$, the factor is the local factor of Remark 5.5.4. $\square$

The ideals that are not prime to $\mathfrak{f}$ get the weight $0$, because at a ramified place the value $\chi_v(\varpi_v)$ depends on the choice of $\varpi_v$. In Lean the indicator function `Langlands.Tate.coprimeIndicator` removes these ideals.

### The functional equation for ramified characters

For a character of ray class type the new feature of the functional equation is the root number. At a ramified place the local $\varepsilon$-factor is a normalized Gauss sum, by Theorem 5.2.22. For a finite place $v$ let $\psi_v$ be the standard character and $d_v = d(\psi_v)$, so that $\mathfrak{D} = \prod_v \mathfrak{p}_v^{d_v}$ is the different and $N(\mathfrak{D}) = |d_F|$. Let $\mathfrak{D}^{(\mathfrak{f})} = \prod_{v \notin R(\chi)} \mathfrak{p}_v^{d_v}$ be the part of $\mathfrak{D}$ prime to $\mathfrak{f}$, and let $\tau$ be the finite Gauss sum of Definition 5.2.16.

**Theorem 5.5.50 (Hecke's theorem for characters of ray class type).** Let $\chi$ be a Hecke character of $F$ of ray class type, with conductor $\mathfrak{f} = \prod_{v \in R(\chi)} \mathfrak{p}_v^{a_v}$. For each $v \in R(\chi)$ choose $c_v \in F_v$ with $|c_v|_v = q_v^{a_v + d_v}$, and put
$$W(\chi) = \chi^*\big(\mathfrak{D}^{(\mathfrak{f})}\big) \prod_{v \in R(\chi)} \chi_v(c_v)^{-1} \, \frac{\tau(\chi_v^{-1}, \psi_v, c_v)}{q_v^{a_v/2}}.$$
1. The function $\Lambda(s, \chi) = L_\infty(s, \chi) L(s, \chi)$, with $L_\infty(s, \chi) = \Gamma_\mathbb{R}(s)^{r_1} \Gamma_\mathbb{C}(s)^{r_2}$, extends to a meromorphic function on $\mathbb{C}$. If $\chi \ne 1$, it is entire.
2. As meromorphic functions, $\Lambda(s, \chi) = W(\chi) \big(|d_F| \, N(\mathfrak{f})\big)^{1/2 - s} \Lambda(1 - s, \bar\chi)$.
3. Each factor of the product in $W(\chi)$ has absolute value $1$ and does not depend on the choice of $c_v$. So $|W(\chi)| = 1$, and $W(\chi)$ is the root number $\prod_v \varepsilon(\chi_v, 1/2, \psi_v)$ of Definition 5.5.1.
4. If $\mathfrak{f} = \mathcal{O}_F$, then $W(\chi) = \psi_\chi([\mathfrak{D}])$, the root number of Theorem 5.5.33.

Lean: not yet formalized

*Proof.* By Lemma 5.5.47, $\chi$ is unitary, $\sigma = 0$, $\chi^{-1} = \bar\chi$, and the parameters at the infinite places are $n_v = t_v = 0$. So parts 1 and 2 of Theorem 5.5.3 give the continuation and the functional equation with the root number $\prod_v \varepsilon(\chi_v, 1/2, \psi_v)$. If $\chi = |\cdot|_\mathbb{A}^{s_0}$, then $\chi_v$ is trivial at an infinite place only for $s_0 = 0$, so $\chi = 1$. Thus part 3 of Theorem 5.5.3 shows that $\Lambda(s, \chi)$ is entire for $\chi \ne 1$.

It remains to compute the local root numbers. At an infinite place $\chi_v$ is trivial, and Propositions 5.2.5 and 5.2.6 with $a = 0$ or $n = 0$ give $\varepsilon(\chi_v, 1/2, \psi_v) = 1$. At a finite place $v \notin R(\chi)$, Proposition 5.2.3 gives $\varepsilon(\chi_v, 1/2, \psi_v) = \chi_v(\varpi_v)^{d_v}$. The product of these numbers is $\lambda_\chi(\mathfrak{D}^{(\mathfrak{f})}) = \chi^*(\mathfrak{D}^{(\mathfrak{f})})$, a finite product since $d_v = 0$ for almost all $v$. At $v \in R(\chi)$, part 3 of Theorem 5.2.22 at $s = 1/2$ gives
$$\varepsilon(\chi_v, 1/2, \psi_v) = \chi_v(c_v)^{-1} \, \frac{\tau(\chi_v^{-1}, \psi_v, c_v)}{q_v^{a_v/2}},$$
and it says that this number does not depend on $c_v$. By Theorem 5.2.19 for $\chi_v^{-1}$, which has conductor exponent $a_v$ by part 4 of Proposition 5.5.46, the quotient $\tau / q_v^{a_v/2}$ has absolute value $1$. Also $|\chi_v(c_v)| = |\chi(c_v^{(v)})| = 1$ by part 2 of Lemma 5.5.47. This proves part 3. For part 4, $R(\chi)$ is empty and $\chi$ is of class group type, so $W(\chi) = \lambda_\chi(\mathfrak{D}) = \psi_\chi([\mathfrak{D}])$ by Proposition 5.5.28. $\square$

We now give the outline of Tate's proof in this case, from [CF67], Chapter XV, Section 4.4 for the global part and Section 2.5 for the local computations. Tate writes the local factors with his function $\rho$ of Remark 5.2.8, but the steps are the same.
1. *The test function.* Put $f = \otimes_v f_v$ with $f_v = 1_{U_v^{(a_v)}}$ at $v \in R(\chi)$, $f_v = 1_{\mathcal{O}_v}$ at the other finite places and the Gaussian at the infinite places. At $v \in R(\chi)$, $Z(f_v, \chi_v, s) = \mathrm{vol}(U_v^{(a_v)}, d^\times x)$ is a nonzero constant, which matches $L(\chi_v, s) = 1$. So $Z(f, \chi, s) = c \, \Lambda(s, \chi)$ with $c \ne 0$, by Proposition 5.4.6.
2. *The global functional equation.* Theorem 5.4.7, Tate's Main Theorem in Section 4.4, gives $Z(f, \chi, s) = Z(\hat f, \bar\chi, 1 - s)$ and shows that $Z(f, \chi, s)$ is entire for $\chi \ne 1$. Its only input is the Riemann-Roch theorem of Section 5.3. The global step does not see the ramification.
3. *The local computation at a ramified place.* By part 1 of Theorem 5.2.22, $\hat f_v$ is a multiple of $\psi_v \, 1_{\mathfrak{p}_v^{-a_v - d_v}}$. In $Z(\hat f_v, \chi_v^{-1}, 1 - s)$ the shells with $|y|_v < q_v^{a_v + d_v}$ give $0$, by Lemma 5.2.18 and Exercise 16. The outer shell gives the Gauss integral, which is a multiple of $\tau(\chi_v^{-1}, \psi_v, c_v)$ by Proposition 5.2.17. This is the factor of part 3 of Theorem 5.2.22. Tate's own test function at a ramified place is, up to a constant, the transform of ours, so his computation runs in the other direction and gives the same factor.
4. *Assembly.* Multiply the local functional equations (5.2.2) over all places. The powers of $q_v$ multiply to $\prod_v q_v^{(a_v + d_v)(1/2 - s)} = (|d_F| N(\mathfrak{f}))^{1/2 - s}$, and the values at $s = 1/2$ multiply to $W(\chi)$. With step 2 this gives part 2 of Theorem 5.5.50.

The proof in [Neu99], Chapter VII, Sections 6 to 8, follows Hecke. There $\Lambda(s, \chi)$ is a finite sum over $\mathrm{Cl}_\mathfrak{f}$ of Mellin transforms of theta series, each twisted by the values of $\chi$ on $(\mathcal{O}_F / \mathfrak{f})^\times$. Poisson summation turns the twist by $\chi$ into a twist by $\bar\chi$ times a global Gauss sum of $\chi$ modulo $\mathfrak{f}$. The Chinese remainder theorem splits this sum into the local sums $\tau(\chi_v^{-1}, \psi_v, c_v)$, as in Exercise 9. In Tate's proof this factorization is automatic.

The Lean library does not yet prove Theorem 5.5.50, nor the functional equation of any ramified Hecke character. It has the local functional equation at a ramified place, `Langlands.Tate.NonArchimedean.localFunctionalEquation_ramified_gaussSumFinite`, and the global results 5.5.46 to 5.5.49. Tate's route for the global analytic step needs Theorem 5.4.7 in Lean for a Schwartz function with the local components $1_{U_v^{(a_v)}}$, and this is not available. For an imaginary quadratic field $F$ and a $\chi$ that is ramified at one place at least, the Lean project follows Hecke's route instead. It writes $\Gamma_\mathbb{R}(2s) L(s, \chi)$ as a finite sum of shifted Epstein zeta functions of the lattices $\mathfrak{f} J$, proves the functional equation of each partial sum, and writes the dual side as a Dirichlet series whose coefficients are finite Gauss sums. The evaluation of these Gauss sums, the vanishing that removes the poles and the assembly into $\Lambda(1 - s, \bar\chi)$ with the root number are open. Remark 5.5.52 gives the details.

**Example 5.5.51 (a ray class character of $\mathbb{Q}(i)$ modulo $3$).** Let $F = \mathbb{Q}(i)$, so $\mathcal{O}_F = \mathbb{Z}[i]$, $d_F = -4$, $r_2 = 1$ and $h_F = 1$. The prime $3$ is inert, and $\mathcal{O}_F / (3) = \mathbb{F}_9$. Let $\eta$ be the character of order $2$ of the cyclic group $\mathbb{F}_9^\times$. The units $\pm 1, \pm i$ map onto the subgroup of order $4$, which is the subgroup of the squares, so $\eta$ is trivial on them. The norm $\mathbb{F}_9^\times \to \mathbb{F}_3^\times$ is onto with kernel the squares, so $\eta(u)$ is the Legendre symbol of $N(u)$ modulo $3$.

We construct $\chi$. Let $v_3$ be the place of $3$ and let $U_F = \mathbb{C}^\times \times \prod_v \mathcal{O}_v^\times$. Since $h_F = 1$, each idele is $\alpha u$ with $\alpha \in F^\times$ and $u \in U_F$. Put $\chi(\alpha u) = \eta(u_{v_3} \bmod 3)$. This is well defined, because $F^\times \cap U_F = \mathcal{O}_F^\times$ and $\eta$ is trivial on the units. It is a Hecke character of ray class type, with $R(\chi) = \{v_3\}$ and $a_{v_3} = 1$. So $\mathfrak{f} = (3)$ and $N(\mathfrak{f}) = 9$. By (5.5.2), for $\alpha \in \mathcal{O}_F$ prime to $3$,
$$\chi^*((\alpha)) = \eta(\alpha \bmod 3)^{-1} = \eta(\alpha \bmod 3) = \Big(\frac{N(\alpha)}{3}\Big).$$
Each ideal is principal, so $\chi^*(I) = (N(I)/3)$ for each ideal $I$ prime to $3$. The ideals of small norm prime to $3$ are $(1)$, $(1 + i)$ of norm $2$, $(2)$ of norm $4$, $(2 \pm i)$ of norm $5$, $(1 + i)^3$ of norm $8$, $(1 + i)(2 \pm i)$ of norm $10$ and $(3 \pm 2i)$ of norm $13$. Proposition 5.5.49 gives
$$L(s, \chi) = 1 - 2^{-s} + 4^{-s} - 2 \cdot 5^{-s} - 8^{-s} + 2 \cdot 10^{-s} + 2 \cdot 13^{-s} + \cdots.$$

Now the root number. The place $v_3$ is unramified over $3$, so $d_{v_3} = 0$, $q_{v_3} = 9$, and $\psi_{v_3}(x) = \psi_{\mathbb{Q}_3}(\mathrm{Tr}\, x)$. Take $c = 1/3$. For $u = x + yi$ with $x, y \in \mathbb{F}_3$ we have $\mathrm{Tr}(u) = 2x$, so $\psi_{v_3}(u/3) = \zeta^{2x}$ with $\zeta = e^{2\pi i/3}$. The squares are $\pm 1, \pm i$, with the values $\zeta^2, \zeta, 1, 1$, and the sum $1$. The nonsquares are $\pm 1 \pm i$, with the values $\zeta^2, \zeta^2, \zeta, \zeta$, and the sum $-2$. Since $\eta^{-1} = \eta$,
$$\tau(\chi_{v_3}^{-1}, \psi_{v_3}, 1/3) = 1 - (-2) = 3,$$
which agrees with Theorem 5.2.19. Next, $\chi_{v_3}(1/3)^{-1} = \chi_{v_3}(3) = \chi(3) = 1$, by part 1 of Lemma 5.5.47 with $S = \{v_3\}$. The different of $\mathbb{Z}[i]$ is $(2)$, so $\chi^*(\mathfrak{D}^{(\mathfrak{f})}) = (4/3) = 1$. Theorem 5.5.50 gives $W(\chi) = 3/3 = 1$. Since $\bar\chi = \chi$ and $|d_F| N(\mathfrak{f}) = 36$, the function $\Lambda(s, \chi) = \Gamma_\mathbb{C}(s) L(s, \chi)$ is entire and satisfies
$$\Lambda(s, \chi) = 36^{1/2 - s} \Lambda(1 - s, \chi).$$
Exercise 19 checks this against Dirichlet $L$-functions.

**Remark 5.5.52 (the Lean proof).** The file `Langlands/Tate/HeckeRamified.lean` proves Propositions 5.5.46 and 5.5.49, Lemma 5.5.47 and Theorem 5.5.48, with the local results of `Langlands/Tate/LocalRamified.lean`. The conductor is a `finprod` over all finite places, and `conductor_eq_prod` writes it over the `Finset` `Langlands.Tate.ramifiedSet χ`. Part 2 of Lemma 5.5.47 uses the character `Langlands.Tate.normChar χ`, which is $|\chi|$. In Theorem 5.5.48 the hypothesis is $\|x - 1\|_v \le \exp(-a_v)$, with the multiplicative valuation of Mathlib. The Euler product is `Langlands.Tate.hasProd_of_norm_le`, the form of `Langlands.Tate.hasProd_of_norm` of Remark 5.5.35 with an inequality. The group $\mathrm{Cl}_\mathfrak{f}$, formula (5.5.2) and Theorem 5.5.50 are not in Lean.

The files `Langlands/Tate/RayClassQuadratic.lean` and `Langlands/Tate/RayClassFE.lean` prove the first steps of Hecke's proof of Theorem 5.5.50, in the form of [Neu99], Chapter VII, for an imaginary quadratic field $F$ with $w$ roots of unity and a character $\chi$ of ray class type that is ramified at one place at least. Let $J$ be a nonzero integral ideal, and let $\varphi : F \to \mathbb{R}^2$ be the embedding with $|\varphi(\beta)|^2 = 2 N(\beta)$. For $x \in J$ put $c_J(x) = \chi^*((x) J^{-1})$ if $(x) J^{-1}$ is prime to $\mathfrak{f}$, and $c_J(x) = 0$ otherwise.
1. For a lattice $M$ in a Euclidean space of dimension $n$ and $x, y$ in this space, let $Z_M(x, y; s) = \sum_{\mu \in M, \, x + \mu \ne 0} e^{2\pi i \langle x + \mu, y \rangle} |x + \mu|^{-s}$ be the shifted Epstein zeta function. The function $\Lambda_M(x, y; s) = \Gamma_\mathbb{R}(s) Z_M(x, y; s)$ has a meromorphic continuation and satisfies $\Lambda_M(x, y; n - s) = \mathrm{covol}(M)^{-1} e^{2\pi i \langle x, y \rangle} \Lambda_{M^\vee}(-y, x; s)$. This is `Langlands.Tate.completedShiftEpsteinZeta_sub`. The proof is Poisson summation on $x + M$, as in Remark 5.3.18.
2. The coefficient $c_J$ is periodic modulo $\mathfrak{f} J$. The key input is `Langlands.Tate.IsRayClassType.idealChar_toPrincipalIdeal_eq`, which is Theorem 5.5.48 applied to $y / x$: if $y/x \in U_v^{(a_v)}$ at each $v \in R(\chi)$, then $\lambda_\chi((y)) = \lambda_\chi((x))$.
3. For $\mathrm{Re}(u) > 1$, the partial $L$-series of the class $[J]^{-1}$ is $w^{-1} (2 N(J))^u \sum_{x \in J / \mathfrak{f} J} c_J(x) Z_{\varphi(\mathfrak{f} J)}(\varphi(x), 0; 2u)$. This is `Langlands.Tate.IsRayClassType.hasSum_partialLSeries`. Put $\Lambda_J(s) = \sum_{x} c_J(x) \Lambda_{\varphi(\mathfrak{f} J)}(\varphi(x), 0; s)$. Then `Langlands.Tate.IsRayClassType.gammaℝ_mul_finiteLFunction` gives $\Gamma_\mathbb{R}(2u) L(u, \chi) = w^{-1} \sum_C (2 N(J_C))^u \Lambda_{J_C}(2u)$, where $C$ runs over $\mathrm{Cl}_F$ and $J_C$ is an integral ideal in $C$.
4. The functional equation of $\Lambda_J$ is `Langlands.Tate.rayClassCompleted_two_sub`: $\Lambda_J(2 - s)$ is $\mathrm{covol}(\varphi(\mathfrak{f} J))^{-1} = (N(\mathfrak{f}) N(J) |d_F|^{1/2})^{-1}$ times $\sum_x c_J(x) \Lambda_{\varphi(\mathfrak{f} J)^\vee}(0, \varphi(x); s)$. The dual lattice is $\varphi((\mathfrak{f} J \mathfrak{D})^{-1})$. By `Langlands.Tate.hasSum_rayClass_dual`, for $\mathrm{Re}(s) > 2$ this sum is a Dirichlet series over the nonzero $\beta \in (\mathfrak{f} J \mathfrak{D})^{-1}$, with the finite Gauss sums $G_J(\beta) = \sum_{x \in J / \mathfrak{f} J} c_J(x) e^{2\pi i \mathrm{Tr}(\beta x)}$ as coefficients.
5. If $\sum_{x \in J / \mathfrak{f} J} c_J(x) = 0$, then $\Lambda_J$ is entire. This is `Langlands.Tate.IsRayClassType.differentiable_rayClassCompleted`.

Three steps are open, so Theorem 5.5.50 is not yet formalized, even for imaginary quadratic fields. First, the vanishing $\sum_x c_J(x) = 0$. It follows from (5.5.2) and the construction of Exercise 20, which show that $\chi^*$ gives a nontrivial character of $(\mathcal{O}_F / \mathfrak{f})^\times$, but (5.5.2) is not in Lean. Second, the evaluation $G_J(\beta) = \tau(\chi) \, \bar\chi^*((\beta) \mathfrak{f} J \mathfrak{D})$, with $G_J(\beta) = 0$ if this ideal is not prime to $\mathfrak{f}$, for a global Gauss sum $\tau(\chi)$ with $|\tau(\chi)|^2 = N(\mathfrak{f})$. Third, the assembly of the dual series into the partial $L$-series of $\bar\chi$ and the sum over the classes, with the root number $\tau(\chi) / N(\mathfrak{f})^{1/2}$, its comparison with $W(\chi)$, and the comparison of $\Gamma_\mathbb{R}(2u)$ with $\Gamma_\mathbb{C}(u) = 2^{1-u} \Gamma_\mathbb{R}(2u)$. Fields of degree greater than $2$ are not treated. All the theorems of this remark use only the standard axioms of Lean.
