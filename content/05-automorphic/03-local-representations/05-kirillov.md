---
title: Whittaker and Kirillov models
nodes: []
sources: [BH06, JL70]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Whittaker and Kirillov models

The Fourier expansion of a cusp form becomes, in the adelic language of Chapter 2, a Whittaker expansion. This section recalls the Whittaker and Kirillov models of Volume 6, Section 1.7, and computes the Whittaker function of the spherical vector.

### Whittaker functionals and the Kirillov model

Fix a nontrivial additive character $\psi$ of $K$. It is *unramified* if it is trivial on $\mathcal{O}$ and not on $\mathfrak{p}^{-1}$. The standard character $\psi_p$ of $\mathbb{Q}_p$ of Volume 0, Section 3.2 is unramified. Each nontrivial character is $\psi_b(x) = \psi(b x)$ for a unique $b \in K^\times$.

**Definition 3.5.1 (Whittaker model).** Let $(\pi, V)$ be a smooth representation. A *Whittaker functional* is a linear form $\lambda$ on $V$ with $\lambda(\pi(n(x)) v) = \psi(x) \lambda(v)$ for $x \in K$. If $\lambda \ne 0$, the *Whittaker model* is the space $\mathcal{W}(\pi, \psi)$ of the functions $W_v(g) = \lambda(\pi(g) v)$, with $G$ acting by right translation. The *Kirillov function* of $v$ is $\xi_v(a) = W_v(\mathrm{diag}(a, 1))$ on $K^\times$.

Lean: `Langlands.IsWhittakerFunctional`, `Langlands.IsGeneric` and `Langlands.whittakerModel`, for $GL_n$.

If $\lambda$ is a Whittaker functional for $\psi$, then $\lambda \circ \pi(\mathrm{diag}(b, 1))$ is one for $\psi_b$, so a change of $\psi$ dilates the Kirillov functions.

**Theorem 3.5.2 (existence and uniqueness).** Let $\pi$ be irreducible admissible. If $\pi$ is a character, it has no nonzero Whittaker functional. If $\pi$ is infinite-dimensional, its space of Whittaker functionals has dimension one.

Lean: not stated yet.

This is Volume 6, Theorems 1.7.2 and 1.7.4. [JL70], Chapter 1 proves the uniqueness for $GL_2$ directly.

**Theorem 3.5.3 (Kirillov model).** Let $\pi$ be irreducible and infinite-dimensional. Then $v \mapsto \xi_v$ is injective. Its image $\mathcal{K}(\pi, \psi)$ contains $C_c^\infty(K^\times)$, and the mirabolic group acts by
$$\pi\begin{pmatrix} a & x \\ 0 & 1 \end{pmatrix} \xi(y) = \psi(x y) \, \xi(a y).$$
The center acts by $\omega_\pi$. The quotient $\mathcal{K}(\pi, \psi) / C_c^\infty(K^\times)$ is isomorphic to $r_B(\pi)$.

Lean: not stated yet.

This is Volume 6, Theorem 1.7.5. The action of $w$ is an integral operator with a Bessel kernel ([JL70], Chapter 1, and [Bum97], Chapter 4), which we do not need. Each Kirillov function vanishes for $|y|$ large: if $n(x)$ fixes $\xi$ for $x \in \mathfrak{p}^r$, then $\xi(y) = 0$ unless $\psi_y$ is trivial on $\mathfrak{p}^r$.

The next proposition describes the Kirillov space near $0$, through the exponents of $r_B(\pi)$.

**Proposition 3.5.4 (Kirillov spaces by type).** Let $\pi$ be irreducible and infinite-dimensional. A function $\xi$ on $K^\times$ that vanishes for $|y|$ large lies in $\mathcal{K}(\pi, \psi)$ if and only if, for $|y|$ small:
1. $\pi$ supercuspidal: $\xi(y) = 0$.
2. $\pi = \pi(\chi_1, \chi_2)$ with $\chi_1 \ne \chi_2$: $\xi(y) = |y|^{1/2} (c_1 \chi_1(y) + c_2 \chi_2(y))$ for constants $c_1, c_2$.
3. $\pi = \pi(\chi, \chi)$: $\xi(y) = |y|^{1/2} \chi(y) (c_1 + c_2 v(y))$.
4. $\pi = \eta \mathrm{St}$: $\xi(y) = c \, |y| \eta(y)$.

Lean: not stated yet.

Parts 1, 2 and 4 are Volume 6, Theorem 1.7.5. For part 3, which comes from a Jordan block of $T$ on $r_B(\pi)$, see [JL70], Chapter 1 and [Bum97], Chapter 4. The exponent $|y|$ of $\eta \mathrm{St}$ is the value $\eta(y) |y|^{1/2}$ of the character of Proposition 3.2.5, part 3, on $\mathrm{diag}(y, 1)$, times the factor $|y|^{1/2}$ of the normalization.

### The spherical Whittaker function

Let $\pi = \pi(\chi_1, \chi_2)$ be an irreducible unramified principal series and $\psi$ unramified. Let $v_0 \in \pi^{K_0}$ be nonzero and let $W_0 = W_{v_0}$. Put $z_i = \chi_i(\varpi)$.

**Theorem 3.5.5 (Shintani, Casselman and Shalika, for $GL_2$).** We have $W_0(1) \ne 0$. With the normalization $W_0(1) = 1$, for all $m \in \mathbb{Z}$ and $u \in \mathcal{O}^\times$,
$$W_0\begin{pmatrix} u \varpi^m & 0 \\ 0 & 1 \end{pmatrix} = \begin{cases} q^{-m/2} \dfrac{z_1^{m + 1} - z_2^{m + 1}}{z_1 - z_2} & m \ge 0, \\ 0 & m < 0, \end{cases}$$
where the quotient means $(m + 1) z_1^m$ if $z_1 = z_2$. So $W_0(\mathrm{diag}(\varpi^m, 1)) = q^{-m/2} h_m(z_1, z_2)$. The Iwasawa decomposition and $W_0(n(x) z g k) = \psi(x) \omega_\pi(z) W_0(g)$ determine $W_0$ from these values.

Lean: not stated yet.

*Proof.* Write $a_m = \mathrm{diag}(\varpi^m, 1)$ and $w_m = W_0(a_m)$. The value does not depend on $u$, since $\mathrm{diag}(u, 1) \in K_0$.

First, $w_m = 0$ for $m < 0$. For $x \in \mathcal{O}$ we have $a_m n(x) = n(\varpi^m x) a_m$ and $n(x) \in K_0$, so $w_m = W_0(a_m n(x)) = \psi(\varpi^m x) w_m$. If $m < 0$, then $\varpi^m \mathcal{O} \supset \mathfrak{p}^{-1}$, and there is $x \in \mathcal{O}$ with $\psi(\varpi^m x) \ne 1$. So $w_m = 0$.

Second, the Hecke operator gives a recursion. By Corollary 3.4.7, $\pi(T) v_0 = \lambda v_0$ with $\lambda = q^{1/2}(z_1 + z_2)$. By the coset decomposition before Proposition 3.4.5, $\pi(T) v_0 = \sum_h \pi(h) v_0$, where $h$ runs over the $q + 1$ matrices $\left(\begin{smallmatrix} \varpi & b \\ 0 & 1 \end{smallmatrix}\right)$, $b \in \mathcal{O} / \mathfrak{p}$, and $\mathrm{diag}(1, \varpi)$. Apply $W \mapsto W(a_m)$. Since $a_m \left(\begin{smallmatrix} \varpi & b \\ 0 & 1 \end{smallmatrix}\right) = n(\varpi^m b) \, a_{m + 1}$ and $a_m \, \mathrm{diag}(1, \varpi) = \varpi \, a_{m - 1}$, we get for $m \ge 0$
$$\lambda w_m = \sum_{b \in \mathcal{O} / \mathfrak{p}} \psi(\varpi^m b) \, w_{m + 1} + \omega_\pi(\varpi) w_{m - 1} = q w_{m + 1} + z_1 z_2 w_{m - 1}.$$
Here $\psi(\varpi^m b) = 1$ because $m \ge 0$, and $\omega_\pi(\varpi) = z_1 z_2$.

Put $w_m = q^{-m/2} u_m$. Then $(z_1 + z_2) u_m = u_{m + 1} + z_1 z_2 u_{m - 1}$ for $m \ge 0$ and $u_{-1} = 0$. The complete symmetric functions satisfy the same recursion with $h_{-1} = 0$ and $h_0 = 1$, so $u_m = w_0 h_m(z_1, z_2)$. If $w_0 = 0$, then $W_0$ vanishes on all $\mathrm{diag}(a, 1)$, by $K_0$-invariance, so $\xi_{v_0} = 0$, which contradicts Theorem 3.5.3. $\square$

Shintani's formula for $GL_n$, and the formula of Casselman and Shalika for unramified groups, express $W_0$ on the torus by characters of the dual group. For $GL_2$, $h_m(z_1, z_2)$ is the character of $\mathrm{Sym}^m$ of the standard representation at $\mathrm{diag}(z_1, z_2)$.

**Example 3.5.6 (Fourier coefficients and Whittaker values).** Compare Theorem 3.5.5 with Proposition 3.4.8. The eigenvalue of $T_{\varpi^m}$ on $v_0$ is $q^{m/2} h_m(z_1, z_2) = q^m \, W_0(a_m)$. For a newform $f$ of weight $k$ with $p \nmid N$ this eigenvalue is $p^{m(1 - k/2)} a_{p^m}$, by the discussion after Proposition 3.4.8. So
$$W_{0, p}\begin{pmatrix} p^m & 0 \\ 0 & 1 \end{pmatrix} = p^{-m} \cdot p^{m(1 - k/2)} a_{p^m} = \frac{a_{p^m}}{p^{m k/2}} = p^{-m/2} \cdot \frac{a_{p^m}}{p^{m(k - 1)/2}}.$$
The second factor is the normalized Fourier coefficient $a_n n^{-(k - 1)/2}$ for $n = p^m$, and the factor $p^{-m/2}$ is the factor $q^{-m/2}$ of Theorem 3.5.5. This is the local form of the statement of Chapter 2 that the global Whittaker function of $\varphi_f$ is a product of local Whittaker functions. For $f = \Delta$, $p = 2$ and $m = 1$, the value is $-24 / 2^6 = -3/8$, and $h_1(z_1, z_2) = z_1 + z_2 = -24 / 2^{11/2}$.

### Zeta integrals and local L-factors

For $\xi \in \mathcal{K}(\pi, \psi)$ put
$$Z(s, \xi) = \int_{K^\times} \xi(y) \, |y|^{s - 1/2} \, d^\times y,$$
with $\mathrm{vol}(\mathcal{O}^\times) = 1$ for $d^\times y$. By Proposition 3.5.4 the integral converges for $\mathrm{Re}(s)$ large, and it is a rational function of $q^{-s}$.

**Definition 3.5.7 (local L-factor).** Let $\pi$ be irreducible and infinite-dimensional. The values $Z(s, \xi)$ for $\xi \in \mathcal{K}(\pi, \psi)$ span a fractional ideal of $\mathbb{C}[q^{-s}, q^{s}]$ that contains $1$. It is generated by $1 / P(q^{-s})$ for a unique polynomial $P$ with $P(0) = 1$. The *local L-factor* is $L(s, \pi) = 1 / P(q^{-s})$. For a character, $L(s, \eta \circ \det) = L(s, \eta |\cdot|^{1/2}) L(s, \eta |\cdot|^{-1/2})$, the product of the factors of Tate's thesis.

Lean: not stated yet.

That the span is such an ideal is [JL70], Chapter 1. It is a $\mathbb{C}[q^{\pm s}]$-module because $Z(s, \pi(\mathrm{diag}(\varpi^{-1}, 1)) \xi) = q^{-s + 1/2} Z(s, \xi)$, and it contains $Z(s, 1_{\mathcal{O}^\times}) = 1$.

**Proposition 3.5.8 (L-factors by type).** For $\pi$ irreducible infinite-dimensional:
1. $L(s, \pi) = 1$ if $\pi$ is supercuspidal.
2. $L(s, \pi(\chi_1, \chi_2)) = L(s, \chi_1) L(s, \chi_2)$, where $L(s, \chi) = (1 - \chi(\varpi) q^{-s})^{-1}$ if $\chi$ is unramified and $L(s, \chi) = 1$ if $\chi$ is ramified.
3. $L(s, \eta \mathrm{St}) = L(s, \eta |\cdot|^{1/2}) = (1 - \eta(\varpi) q^{-s - 1/2})^{-1}$ if $\eta$ is unramified, and $1$ if $\eta$ is ramified.
4. If $\pi$ is unramified and $\psi$ is unramified, then $Z(s, \xi_{v_0}) = L(s, \pi)$ for the spherical vector with $\xi_{v_0}(1) = 1$.

Lean: not stated yet.

*Proof.* Each $\xi \in C_c^\infty(K^\times)$ gives a Laurent polynomial in $q^{-s}$. So only the behavior of $\xi$ near $0$ matters, and Proposition 3.5.4 describes it. For part 1 there is nothing near $0$, and the ideal is $\mathbb{C}[q^{\pm s}]$. For a character $\mu$ and $c \in \mathbb{R}$, the function $\mu(y) |y|^c 1_{\mathcal{O}}(y)$ gives
$$\int_{\mathcal{O} \setminus 0} \mu(y) |y|^{c + s - 1/2} \, d^\times y = \sum_{m \ge 0} \mu(\varpi)^m q^{-m(c + s - 1/2)} \int_{\mathcal{O}^\times} \mu(u) \, d^\times u.$$
If $\mu$ is ramified, the last integral is $0$. If $\mu$ is unramified, the sum is $(1 - \mu(\varpi) q^{-(s + c - 1/2)})^{-1}$. With $\mu = \chi_i$ and $c = 1/2$ this is $L(s, \chi_i)$, and with $\mu = \eta$ and $c = 1$ it is $(1 - \eta(\varpi) q^{-s - 1/2})^{-1}$. In part 2 with $\chi_1 \ne \chi_2$ both unramified, the ideal generated by $1$, $L(s, \chi_1)$ and $L(s, \chi_2)$ is generated by $L(s, \chi_1) L(s, \chi_2)$, since the two factors have no common pole. If $\chi_1 = \chi_2 = \chi$, the function $\chi(y) |y|^{1/2} v(y) 1_{\mathcal{O}}(y)$ gives $L(s, \chi)^2$ up to a polynomial. The ramified cases are similar. Part 4 is Theorem 3.5.5:
$$Z(s, \xi_{v_0}) = \sum_{m \ge 0} q^{-m/2} h_m(z_1, z_2) \, q^{-m(s - 1/2)} = \sum_{m \ge 0} h_m(z_1, z_2) q^{-ms} = \frac{1}{(1 - z_1 q^{-s})(1 - z_2 q^{-s})}. \ \square$$

These factors equal the Artin factors of the Langlands parameters of Volume 6, Chapter 3. Section 3.6 extends part 4 to every $\pi$: the newvector has $Z(s, \xi) = L(s, \pi)$.
