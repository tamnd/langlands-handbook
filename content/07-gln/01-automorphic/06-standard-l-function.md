---
title: The standard L-function
nodes: [LG6NN4B43V, LG2E74SP8W]
sources: [CF67, BH06, Lan70]
status: drafted
drafted_by: writer
reviewed_by: []
---
## The standard L-function

The Satake parameters of a cuspidal representation $\pi$ define an Euler product $L(s, \pi)$. Godement and Jacquet proved that it has an analytic continuation and a functional equation, by a direct generalization of Tate's thesis: the additive group of $F$ is replaced by the algebra $M_n(F)$ and the character by a matrix coefficient. This section gives the local theory, the unramified computation in full and the global theorem in outline. It ends with the converse theorem, which goes the other way and is the main tool for the cases of functoriality of Chapter 2. The example to keep in mind is $L(s, \pi_\Delta) = \sum_m \tau(m) m^{-11/2} m^{-s}$.

### The partial L-function

**Definition 1.6.1 (unramified L-factor).** Let $\pi_v$ be an unramified representation of $GL_n(F_v)$ with Satake parameters $\alpha_{1}, \ldots, \alpha_{n}$. Its *standard L-factor* is
$$L(s, \pi_v) = \prod_{j=1}^n (1 - \alpha_{j} q_v^{-s})^{-1} = \det(1 - A_v q_v^{-s})^{-1},$$
where $A_v = \mathrm{diag}(\alpha_{1}, \ldots, \alpha_{n})$ is the Satake parameter. For a cuspidal automorphic representation $\pi$ and a finite set $S$ of places that contains the infinite places and the places where $\pi$ is ramified, the *partial L-function* is $L^S(s, \pi) = \prod_{v \notin S} L(s, \pi_v)$.

Lean: not stated yet

**Proposition 1.6.2 (Jacquet and Shalika).** Let $\pi$ be a cuspidal automorphic representation of $GL_n(\mathbb{A})$ with unitary central character. Then $q_v^{-1/2} < |\alpha_{j}| < q_v^{1/2}$ for each unramified place $v$ and each $j$. Hence $L^S(s, \pi)$ converges absolutely for $\mathrm{Re}(s) > 3/2$.

Lean: not stated yet

*Proof sketch.* The contragredient $\tilde \pi$ is the complex conjugate $\bar \pi$, because the central character is unitary and the Petersson product is invariant. At an unramified place the Satake parameters of $\tilde \pi_v$ are the $\alpha_{j}^{-1}$ and those of $\bar \pi_v$ are the $\bar \alpha_{j}$, so the multiset $\{\alpha_j\}$ is stable under $\alpha \mapsto \bar \alpha^{-1}$. The Rankin-Selberg $L$-function $L^S(s, \pi \times \tilde \pi) = \prod_{v \notin S} \prod_{j,k} (1 - \alpha_{j} \bar \alpha_{k} q_v^{-s})^{-1}$ is the Mellin transform of $|\varphi|^2$ against an Eisenstein series, and its Euler product converges absolutely for $\mathrm{Re}(s) > 1$ by the theory of Jacquet, Piatetski-Shapiro and Shalika. The proof of the convergence uses that the logarithm is a Dirichlet series with the nonnegative coefficients $|\sum_j \alpha_{j}^m|^2 / m$ at $q_v^{-ms}$, together with Landau's lemma. So no local factor has a pole with $\mathrm{Re}(s) > 1$. The local factor at $v$ has a pole at the real point $s$ with $q_v^{s} = |\alpha_j|^2$, for each $j$. So $|\alpha_j|^2 \le q_v$. A finer argument of Jacquet and Shalika, which uses the simple pole of $L^S(s, \pi \times \tilde \pi)$ at $s = 1$, excludes equality. The lower bound follows from the symmetry $\alpha \mapsto \bar \alpha^{-1}$. $\square$

The Ramanujan conjecture of Chapter 2 says $|\alpha_{j}| = 1$. The exponent $1/2$ of the proposition is the *trivial bound*. The best bounds known for all $n$ are $1/2 - 1/(n^2 + 1)$, by Luo, Rudnick and Sarnak, and for $n = 2$ the bound $7/64$ of Kim and Sarnak.

### The local zeta integrals

Let $v$ be a finite place, $G_v = GL_n(F_v)$ and $\pi_v$ an irreducible admissible representation on $V$. A *matrix coefficient* of $\pi_v$ is a function $f(g) = \lambda(\pi_v(g) x)$ with $x \in V$ and $\lambda$ in the smooth dual $\tilde V$. A *Schwartz-Bruhat function* on $M_n(F_v)$ is a locally constant function with compact support.

**Definition 1.6.3 (Godement-Jacquet zeta integral).** For a Schwartz-Bruhat function $\Phi$ on $M_n(F_v)$ and a matrix coefficient $f$ of $\pi_v$,
$$Z(\Phi, s, f) = \int_{G_v} \Phi(g) f(g) |\det g|^{s + (n-1)/2} \, d^\times g,$$
where $d^\times g = |\det g|^{-n} dg$ for an additive Haar measure $dg$ on $M_n(F_v)$.

Lean: `Langlands.gjZeta`, a definition of the project

The Lean definition writes the integral over $M_n(F_v)$ with the density $|\det x|^{s + (n-1)/2 - n}$ and the additive Haar measure of Mathlib, and it puts the integrand equal to $0$ off $GL_n(F_v)$, a set of measure zero. Another Haar measure multiplies every zeta integral by one constant.

**Proposition 1.6.4 (the unramified computation).** Let $\pi_v$ be unramified with Satake parameters $\alpha_1, \ldots, \alpha_n$, let $\Phi_0$ be the characteristic function of $M_n(\mathcal{O}_v)$, let $f_0(g) = \tilde x_0(\pi_v(g) x_0)$ be the zonal spherical function with $f_0(1) = 1$, and let $\mathrm{vol}(K_v) = 1$. Then for $\mathrm{Re}(s)$ large
$$Z(\Phi_0, s, f_0) = L(s, \pi_v).$$

Lean: not stated yet

*Proof.* We follow Tamagawa. Realize $\pi_v$ as the unramified subquotient of $I(\chi)$ with $\chi_j(\varpi) = \alpha_j$, and let $\phi_\chi$ be the spherical vector of Section 1.4. For a function $h$ of the spherical Hecke algebra, $\int_{G_v} h(g) f_0(g) \, d^\times g$ is the eigenvalue of $h$ on the spherical vector, and in the model $I(\chi)$ this eigenvalue is $\int h(g) \phi_\chi(g) \, d^\times g$. The set $M_n(\mathcal{O}_v) \cap G_v$ is the disjoint union of the sets $D_k = \{g : v(\det g) = k\}$ for $k \ge 0$, and these sets are bi-invariant under $K_v$. So
$$Z(\Phi_0, s, f_0) = \sum_{k \ge 0} q_v^{-k(s + (n-1)/2)} \sum_{h \in D_k / K_v} \phi_\chi(h).$$
The right cosets $hK_v$ in $D_k$ correspond to the lattices $h\mathcal{O}_v^n \subseteq \mathcal{O}_v^n$ of index $q_v^k$. Column operations bring $h$ to a unique upper triangular form: the diagonal is $\varpi^\mu$ with $\mu_j \ge 0$ and $|\mu| = \sum_j \mu_j = k$, and the entry at the position $(i, j)$ with $i < j$ is taken from a set of representatives of $\mathcal{O}_v / \varpi^{\mu_i}$. So there are $q_v^{\sum_i (n - i) \mu_i}$ cosets with the diagonal $\mu$, and $\phi_\chi(h) = \delta_B^{1/2}(\varpi^\mu) \alpha^\mu$ for each of them, with $\alpha^\mu = \prod_j \alpha_j^{\mu_j}$. Now $\delta_B^{1/2}(\varpi^\mu) = q_v^{-\sum_i (n + 1 - 2i) \mu_i / 2}$, and $(n - i) - (n + 1 - 2i)/2 = (n - 1)/2$ for every $i$. Hence
$$\sum_{h \in D_k / K_v} \phi_\chi(h) = q_v^{k(n-1)/2} \sum_{|\mu| = k} \alpha^\mu = q_v^{k(n-1)/2} h_k(\alpha),$$
where $h_k$ is the complete symmetric function of degree $k$. The factors $q_v^{\pm k(n-1)/2}$ cancel, and
$$Z(\Phi_0, s, f_0) = \sum_{k \ge 0} h_k(\alpha) q_v^{-ks} = \prod_{j=1}^n (1 - \alpha_j q_v^{-s})^{-1}. \qquad \square$$

For $n = 1$ this is the computation of Tate's thesis in Volume 3, Chapter 5. The shift $(n-1)/2$ in the exponent of the zeta integral is there to make the answer the $L$-factor with the unitary normalization.

**Theorem 1.6.5 (Godement and Jacquet, local theory).** Let $\pi_v$ be an irreducible admissible representation of $GL_n(F_v)$, $v$ finite.
1. Each $Z(\Phi, s, f)$ converges absolutely for $\mathrm{Re}(s)$ large, and it is a rational function of $q_v^{-s}$.
2. The span of the $Z(\Phi, s, f)$ over $\mathbb{C}[q_v^{s}, q_v^{-s}]$ is a fractional ideal of this ring. It has a unique generator of the form $L(s, \pi_v) = P(q_v^{-s})^{-1}$ with $P \in \mathbb{C}[X]$ and $P(0) = 1$.
3. Let $\psi_v$ be a nontrivial additive character, $\hat \Phi(x) = \int \Phi(y) \psi_v(\mathrm{tr}(xy)) dy$ with the self-dual measure, and $\check f(g) = f(g^{-1})$. There is a function $\gamma(s, \pi_v, \psi_v)$, independent of $\Phi$ and $f$, with
$$Z(\hat \Phi, 1 - s, \check f) = \gamma(s, \pi_v, \psi_v) Z(\Phi, s, f).$$
Then $\varepsilon(s, \pi_v, \psi_v) = \gamma(s, \pi_v, \psi_v) L(s, \pi_v) / L(1 - s, \tilde \pi_v)$ is of the form $c q_v^{-ms}$.

Lean: not stated yet

*Proof sketch.* The proof of Godement and Jacquet reduces the first two claims to the supercuspidal case and the principal series. For $\pi_v$ supercuspidal the matrix coefficients have compact support modulo the center, so $Z(\Phi, s, f)$ is a Laurent polynomial in $q_v^{-s}$ and $L(s, \pi_v) = 1$ for $n \ge 2$. For a subquotient of an induced representation, the zeta integral is computed by the Iwasawa decomposition as a zeta integral of the inducing data, and part 2 for $GL_1$ is Tate's thesis. For part 3, the space of the trilinear forms $(\Phi, x, \lambda) \mapsto Z(\hat \Phi, 1 - s, \check f)$ with the right invariance under $G_v \times G_v$ acting on $M_n(F_v)$ by left and right multiplication is of dimension at most one for generic $s$. Both sides of the identity are such forms, so they are proportional. The full proof is in Godement and Jacquet, Theorem 3.3, and for $n = 2$ in Bushnell and Henniart, Chapter 6. $\square$

The theorem has no Lean statement of its own. The project uses the characterization of part 2 as a definition: `Langlands.IsGJLFactor π L` says that $L(s) = P(q_v^{-s})^{-1}$ with $P(0) = 1$, that each zeta integral is a Laurent polynomial in $q_v^{-s}$ times $L(s)$ for $\mathrm{Re}(s)$ large, and that $L(s)$ is a finite combination of zeta integrals with Laurent polynomial coefficients for $\mathrm{Re}(s)$ large. These properties determine $L$, and parts 1 and 2 say that such an $L$ exists.

**Remark 1.6.6 (the L-factors and the local Langlands correspondence).** The local Langlands correspondence of Volume 6 is a bijection $\mathrm{rec}_n$ from the irreducible admissible representations of $GL_n(F_v)$ to the Frobenius semisimple Weil-Deligne representations of dimension $n$. It takes the Godement-Jacquet factor $L(s, \pi_v)$ to the Artin factor $L(s, \mathrm{rec}_n(\pi_v))$. For $\pi_v$ unramified with Satake parameter $A_v$, $\mathrm{rec}_n(\pi_v)$ is unramified and sends a geometric Frobenius to $A_v$, and the two factors are $\det(1 - A_v q_v^{-s})^{-1}$.

Node: LG2E74SP8W · Lean: `Langlands.LocalLanglandsGL`

The correspondence is a theorem of Harris and Taylor and of Henniart. The project states it and does not prove it. Its Lean statement asks that $\mathrm{rec}_n$ preserve the Godement-Jacquet factor in the sense of `Langlands.IsGJLFactor`. It leaves out the $\varepsilon$-factors and the $L$-factors of pairs, so it does not determine the correspondence for $n \ge 2$.

**Example 1.6.7 (the principal series).** Let $\pi_v$ be the irreducible representation $I(\chi)$ for unitary characters $\chi_1, \ldots, \chi_n$, ramified or not. Then $L(s, \pi_v) = \prod_j L(s, \chi_j)$, the product of the Tate factors. If $\pi_v$ is a twist $\mathrm{St} \otimes \chi$ of the Steinberg representation of $GL_2$, then $L(s, \pi_v) = L(s + 1/2, \chi)$. For the new vector of the Steinberg representation at $p$ in a newform $f$ of level $p$, this is the factor $(1 - a_p p^{-s - (k-1)/2})^{-1}$ with $a_p = \pm p^{k/2 - 1}$.

### The global theorem

At an infinite place $v$ there are archimedean zeta integrals with Schwartz functions $\Phi$, and Godement and Jacquet define $L(s, \pi_v)$ as a product of the Gamma factors $\Gamma_\mathbb{R}(s) = \pi^{-s/2} \Gamma(s/2)$ and $\Gamma_\mathbb{C}(s) = 2 (2\pi)^{-s} \Gamma(s)$ attached to the Langlands parameter of $\pi_v$. For a cuspidal automorphic representation $\pi$ put $L(s, \pi) = \prod_{v < \infty} L(s, \pi_v)$ and $\Lambda(s, \pi) = \prod_v L(s, \pi_v)$, and $\varepsilon(s, \pi) = \prod_v \varepsilon(s, \pi_v, \psi_v)$, which does not depend on $\psi$.

**Theorem 1.6.8 (Godement and Jacquet).** Let $\pi$ be a cuspidal automorphic representation of $GL_n(\mathbb{A})$ with $n \ge 2$. Then $\Lambda(s, \pi)$ converges for $\mathrm{Re}(s)$ large and has an analytic continuation to an entire function of $s$, bounded in vertical strips of finite width, with
$$\Lambda(s, \pi) = \varepsilon(s, \pi) \Lambda(1 - s, \tilde \pi).$$

Lean: not stated yet

*Proof sketch.* For a Schwartz-Bruhat function $\Phi = \otimes_v \Phi_v$ on $M_n(\mathbb{A})$ and a cusp form $\varphi \in \pi$, $\tilde \varphi \in \tilde \pi$, the global zeta integral is
$$Z(\Phi, s, \varphi, \tilde \varphi) = \int_{GL_n(\mathbb{A})} \Phi(g) f(g) |\det g|^{s + (n-1)/2} \, dg, \qquad f(g) = \int_{Z(\mathbb{A}) GL_n(F) \backslash GL_n(\mathbb{A})} \varphi(hg) \tilde \varphi(h) \, dh.$$
For pure tensors, $f$ is a product of local matrix coefficients, so $Z$ is a product of local zeta integrals. With Proposition 1.6.4 at almost all places, $Z = \prod_{v \in S} Z(\Phi_v, s, f_v) \cdot L^S(s, \pi)$, and by part 2 of Theorem 1.6.5 and its archimedean analogue a finite sum of such integrals is $\Lambda(s, \pi)$. Unfold $f$ to write $Z$ as the integral over $GL_n(F) \backslash GL_n(\mathbb{A})$ of $\varphi(g)$ times the theta series $\sum_{\xi \in M_n(F)} \Phi(\xi g)$, up to the integration over $\tilde \varphi$. Split the integral at $|\det g| = 1$ as in Tate's thesis. The part with $|\det g| \ge 1$ is entire. On the other part apply the Poisson summation formula on $M_n(F) \backslash M_n(\mathbb{A})$, and replace $g$ by $g^{-1}$. The terms of the theta series with $\xi$ of rank less than $n$ are integrals of $\varphi$ over unipotent radicals of parabolic subgroups, and they vanish because $\varphi$ is cuspidal. This is the only place where cuspidality is used, and it is the reason why no poles appear: in Tate's thesis the rank $0$ term $\xi = 0$ gave the poles. What remains is the integral for $(\hat \Phi, 1 - s, \tilde \varphi, \varphi)$ over $|\det g| \ge 1$, which is entire, and the functional equation follows by symmetry together with the local functional equations. The boundedness in vertical strips comes from the rapid decay of $\varphi$. $\square$

For $n = 1$ the same proof is Tate's thesis, and the rank $0$ term gives the poles of $\Lambda(s, \chi)$ when $\chi$ is a power of the norm. This is Hecke's theorem.

**Example 1.6.9 (Hecke's theorem).** Let $\chi$ be a Hecke character of a number field $K$ with $|\chi| = \|\cdot\|^\sigma$. Then $\Lambda(s, \chi)$ has a meromorphic continuation to $\mathbb{C}$ and satisfies $\Lambda(s, \chi) = W (|d_K| N(\mathfrak{f}_\chi))^{1/2 - s - \sigma} \Lambda(1 - s, \chi^{-1})$ with $|W| = 1$. It is entire unless $\chi = \|\cdot\|^{s_0}$.

Node: LG6NN4B43V · Lean: `Langlands.HeckeFunctionalEquation`

This is the theorem of Volume 3, Chapter 5. The project states it and does not prove it. In the Lean statement the archimedean parameters of $\chi$ are hypotheses. Their existence is the separate statement `Langlands.ArchimedeanParametersExist`.

**Example 1.6.10 (modular forms).** For a newform $f \in S_k(\Gamma_0(N))$ and $\pi = \pi_f$, the finite part is $L(s, \pi_f) = L(f, s + (k-1)/2) = \sum_m a_m(f) m^{-(k-1)/2} m^{-s}$, by Example 1.4.9 at the primes $p \nmid N$ and by the Steinberg factor of Example 1.6.7 at $p \| N$. The archimedean factor is $\Gamma_\mathbb{C}(s + (k-1)/2)$, and the theorem gives Hecke's functional equation of Volume 4 with the center at $s = 1/2$. For $\Delta$ this is $\Lambda(s, \pi_\Delta) = \Lambda(1 - s, \pi_\Delta)$, the sign is $\varepsilon = (-1)^{k/2} = 1$ for $k = 12$.

### The converse theorem

The theorem of Godement and Jacquet attaches to $\pi$ an entire $L$-function with a functional equation. The converse theorem says that the twisted $L$-functions characterize the automorphic representations. Let $\Pi = \otimes'_v \Pi_v$ be an irreducible admissible representation of $GL_n(\mathbb{A})$ with central character trivial on $F^\times$, whose $L$-function $L(s, \Pi) = \prod_v L(s, \Pi_v)$ converges in a right half plane. For a cuspidal representation $\tau$ of $GL_m(\mathbb{A})$, $L(s, \Pi \times \tau)$ is the product of the local Rankin-Selberg factors, which are defined by the local Langlands correspondence or by the local integrals of Jacquet, Piatetski-Shapiro and Shalika.

**Theorem 1.6.11 (converse theorem, Cogdell and Piatetski-Shapiro).** Let $n \ge 3$ and let $S$ be a finite set of finite places. Suppose that for every $m$ with $1 \le m \le n - 2$ and every cuspidal representation $\tau$ of $GL_m(\mathbb{A})$ that is unramified at all $v \in S$, the function $L(s, \Pi \times \tau)$ is nice: it has an analytic continuation to an entire function, bounded in vertical strips, with the functional equation $L(s, \Pi \times \tau) = \varepsilon(s, \Pi \times \tau) L(1 - s, \tilde \Pi \times \tilde \tau)$. Then there is an automorphic representation $\Pi'$ of $GL_n(\mathbb{A})$ with $\Pi'_v \simeq \Pi_v$ for all $v \notin S$.

Lean: not stated yet

*Proof sketch.* Fix a Whittaker function $W = \prod_v W_v$ in the Whittaker model of $\Pi$, which exists because each $\Pi_v$ is generic, and define $U(g) = \sum_\gamma W(\mathrm{diag}(\gamma, 1) g)$ with the sum of Theorem 1.5.2 over $N_{n-1}(F) \backslash GL_{n-1}(F)$. This function is left invariant under $P_n(F)$ by construction. The function $V(g) = \sum_\gamma W(\alpha_n \mathrm{diag}(1, \gamma) g)$, for a suitable permutation $\alpha_n$, is left invariant under the transpose of the mirabolic group. The global Rankin-Selberg integral of $U$ against a cusp form on $GL_m$ is the $L$-function $L(s, \Pi \times \tau)$ times local integrals. The functional equations and the boundedness give $\int U \varphi_\tau = \int V \varphi_\tau$ for all $\tau$ with $m \le n - 2$. A Fourier argument on $GL_n$ then shows $U = V$. The groups $P_n(F)$ and its transpose generate $GL_n(F)$, so $U$ is left invariant under $GL_n(F)$ and is an automorphic form. The set $S$ enters through the choice of $W_v$ at $v \in S$, which must make $U$ independent of the local data. $\square$

For $n = 2$ the theorem with $m = 1$ is the converse theorem of Weil, and Jacquet and Langlands, in Volume 5. For $n = 3$ the twists by $GL_1$ suffice, by Jacquet, Piatetski-Shapiro and Shalika. The cases of functoriality of Chapter 2 that are proved by the converse theorem follow one pattern. One defines $\Pi$ locally by the local Langlands correspondence, and one proves that its twisted $L$-functions are nice by an integral representation or by the Langlands-Shahidi method. The theorem then gives $\Pi$ at almost all places.
