---
title: Hecke L-functions
nodes: [LG6NN4B43V]
sources: [CF67, Neu99, Tat79]
status: drafted
drafted_by: writer
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

**Remark 5.5.4 (the Lean statement).** The Lean project states Theorem 5.5.3 as `Langlands.HeckeFunctionalEquation`, in the file `Langlands/Statements/Hecke.lean`. It is stated and not proved. Theorem 5.5.10 proves its conclusion for the trivial character, and Theorem 5.5.14 proves it for the characters $|\cdot|_\mathbb{A}^{s_0}$. The file writes $K$ for the number field and `ideleNorm`, or $\|x\|$, for $|x|_\mathbb{A}$. A Hecke character is a continuous homomorphism from the idele class group to $\mathbb{C}^\times$, as in Definition 5.4.1. The finite $L$-function is the product over all finite places of the local factors $(1 - \chi_v(\varpi_v) N(v)^{-s})^{-1}$ at the unramified places and $1$ at the other places, with a uniformizer $\varpi_v \in F$ chosen once. The archimedean factor is the product of $\Gamma_\mathbb{R}(s + t_v + n_v)$ over the real places and $\Gamma_\mathbb{C}(s + t_v + |n_v|/2)$ over the complex places, as in Definition 5.2.2. The Lean statement asserts that there is a real $\sigma$ with $|\chi(x)| = \|x\|^\sigma$, as in Proposition 5.4.2. It differs from Theorem 5.5.3 in these points.
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

**Remark 5.5.16 (the Lean proof).** The file `Langlands/Tate/HeckeNormPower.lean` proves Lemma 5.5.12, Lemma 5.5.13 and Theorem 5.5.14. The functions $\Lambda_\chi$ and $\Lambda'_\chi$ are `fun s => heckeLambdaOne K (s + s₀)` and `fun u => heckeLambdaOne' K (u - s₀)`. Part 4 uses the invariance of the order under translation, `meromorphicOrderAt_comp_add_const_eq_meromorphicOrderAt` of Mathlib. In part 1 of Lemma 5.5.13 the Lean proof repeats the argument of Lemma 5.5.8 with a general hypothesis, as `Langlands.Tate.eq_zero_of_forall_param_eq_one`. All these theorems use only the standard axioms of Lean. By part 3 of Theorem 5.5.3, the Hecke characters that remain are the characters with $\Lambda(s, \chi)$ entire. This case is still open in Lean. It needs the local theory of Section 5.2 at the ramified places, or a theta function with a character for each ray class, and the identification of the root number with a product of Gauss sums. The next subsection proves the continuation and the functional equation for the characters of the class group, which are unramified at every place, but it does not yet join them to the Lean statement.

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

**Remark 5.5.23 (class group characters as Hecke characters).** At an infinite place $v$, call a character of $F_v^\times$ unramified if it is trivial on the maximal compact subgroup, which is $\{\pm 1\}$ or the unit circle. The class group characters are then exactly the Hecke characters that are unramified at every place and trivial on the connected component of $F_\infty^\times = \prod_{v \mid \infty} F_v^\times$. Indeed, at an infinite place the maximal compact subgroup and the connected component generate $F_v^\times$. So such a $\chi$ is trivial on $F_\infty^\times$ and on $\prod_{v \nmid \infty} \mathcal{O}_v^\times$. The map $x \mapsto \prod_{v \nmid \infty} \mathfrak{p}_v^{v(x_v)}$ from $J_F$ onto the group of fractional ideals has the kernel $F_\infty^\times \prod_{v \nmid \infty} \mathcal{O}_v^\times$, which is open, and it maps $F^\times$ onto the principal ideals. So it induces an isomorphism of $J_F / F^\times F_\infty^\times \prod_{v \nmid \infty} \mathcal{O}_v^\times$ with $\mathrm{Cl}_F$, and $\psi \mapsto \chi = \psi \circ [\cdot]$, where $[x]$ is the class of the ideal of $x$, is a bijection from the class group characters onto these Hecke characters. For this $\chi$ we have $\chi_v(\varpi_v) = \psi([\mathfrak{p}_v])$, the conductor is $\mathcal{O}_F$, and the archimedean parameters are $0$. As in Definition 5.5.1 and Lemma 5.5.8, $L(s, \chi) = L(s, \psi)$ and $\Lambda(s, \chi) = 2^{r_2} \Gamma_F(s) L(s, \psi) = 2^{r_2} |d_F|^{-s/2} \Lambda_\psi(s)$ for $\mathrm{Re}(s) > 1$. With these identities, Theorem 5.5.21 would give the conclusion of `Langlands.HeckeFunctionalEquationAt` for $\chi$, with $\sigma = 0$, $W = \psi([\mathfrak{D}])$ and an entire $\Lambda$. This link is still open in Lean. The Lean project does not yet construct the Hecke character of $\psi$ as a term of `Langlands.HeckeCharacter`, compute its local data, or prove the Euler product of $L(u, \psi)$. If we only ask that $\chi$ is trivial on the connected component, we get the characters of the narrow class group. At a real place such a character can be $\mathrm{sgn}$, with the factor $\Gamma_\mathbb{R}(s + 1)$, and Theorem 5.5.21 does not cover these characters.

**Remark 5.5.24 (the Lean proof).** The file `Langlands/Tate/ClassCharacter.lean` proves parts 2 and 3 of Lemma 5.5.18, Proposition 5.5.19, Theorem 5.5.20 and Theorem 5.5.21. It writes $K$ for the number field, and a class group character is a homomorphism `ClassGroup (𝓞 K) →* ℂˣ`. As in Remark 5.3.35, the ideal $\mathfrak{a}_C$ is `Langlands.Tate.classRepUnit` and the bijection $C \mapsto C^*$ is `Langlands.Tate.dualClass`. The class $[\mathfrak{D}]$ is the class of `Langlands.Tate.differentUnit`, and $c_F$ is `Langlands.Tate.xiConst`. The Lean proof of part 1 of Proposition 5.5.19 does not use part 1 of Lemma 5.5.18. It writes $\sum_C \psi(C^{-1}) \varphi_{\mathfrak{a}_C}(u)$ as one series over all the nonzero integral ideals, as `Langlands.Tate.hasSum_classCharXi`, with the series of Remark 5.3.35, and it gets the convergence of $L(u, \psi)$ from this series. So part 1 of Lemma 5.5.18 is not in Lean. The orthogonality in part 2 is `sum_hom_units_eq_zero` of Mathlib. The functions $E_\psi$, $F_{0, \psi}$ and $F_{1, \psi}$ are `Langlands.Tate.classCharE`, `Langlands.Tate.classCharF₀` and `Langlands.Tate.classCharF₁`, and (5.5.1) is `Langlands.Tate.classCharXi_eq_poleShape`. The values at the poles are `Langlands.Tate.classCharF₀_zero` and `Langlands.Tate.classCharF₁_one`, with `Langlands.Tate.ε_mul_classFactor_one` for $\varepsilon_C \, g_C(1) = 1$. The function $\delta_a G$ is `dslope G a` of Mathlib, and its holomorphy is `Complex.differentiableOn_dslope`. The function $\Lambda_\psi$ is `Langlands.Tate.classCharLambda`. In part 4 of Theorem 5.5.21, the step with the dense set is `Continuous.ext_on`, and the density holds because the complement of a countable set in $\mathbb{C}$ is dense. All these theorems use only the standard axioms of Lean. Two questions remain open. The first is the link of Remark 5.5.23. The second is the analogue of Dirichlet's theorem, $L(1, \psi) \ne 0$ for $\psi \ne 1$, which is not proved here and not in Lean. Dirichlet's argument studies the product of the functions $L(u, \psi)$ over all $\psi$, and it needs a separate argument for the characters with $\psi^2 = 1$.
