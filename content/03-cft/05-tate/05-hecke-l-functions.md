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

**Remark 5.5.4 (the Lean statement).** The Lean project states Theorem 5.5.3 as `Langlands.HeckeFunctionalEquation`, in the file `Langlands/Statements/Hecke.lean`. It is stated and not proved. The file writes $K$ for the number field and `ideleNorm`, or $\|x\|$, for $|x|_\mathbb{A}$. A Hecke character is a continuous homomorphism from the idele class group to $\mathbb{C}^\times$, as in Definition 5.4.1. The finite $L$-function is the product over all finite places of the local factors $(1 - \chi_v(\varpi_v) N(v)^{-s})^{-1}$ at the unramified places and $1$ at the other places, with a uniformizer $\varpi_v \in F$ chosen once. The archimedean factor is the product of $\Gamma_\mathbb{R}(s + t_v + n_v)$ over the real places and $\Gamma_\mathbb{C}(s + t_v + |n_v|/2)$ over the complex places, as in Definition 5.2.2. The Lean statement asserts that there is a real $\sigma$ with $|\chi(x)| = \|x\|^\sigma$, as in Proposition 5.4.2. It differs from Theorem 5.5.3 in these points.
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
