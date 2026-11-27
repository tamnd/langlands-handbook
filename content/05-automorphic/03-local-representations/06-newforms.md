---
title: The conductor and local newforms
nodes: []
sources: [BH06, JL70]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## The conductor and local newforms

The theory of Atkin and Lehner (Volume 4) says that the cusp forms of level $N$ are spanned by the forms $f(d z)$ for newforms $f$ of level $M$ with $d M \mid N$. Casselman found its local form (W. Casselman, *On some results of Atkin and Lehner*, Math. Ann. 201, 1973): each generic irreducible $\pi$ has a conductor $c(\pi) \ge 0$, and its vectors fixed by $K_1(\mathfrak{p}^n)$ form a space of dimension $n - c(\pi) + 1$ for $n \ge c(\pi)$. We prove this for the non-supercuspidal $\pi$, compute the conductors and the eigenvalue of the local operator $U$ on the newvector, and read off the classical facts about $a_p$ for $p \mid N$.

Throughout, $\pi$ is irreducible, admissible and infinite-dimensional, $\psi$ is unramified, $a(\chi)$ is the conductor exponent of Section 3.1, and $K_0(\mathfrak{p}^n)$, $K_1(\mathfrak{p}^n)$ are the groups of Section 3.2.

### Fixed vectors and the central character

**Lemma 3.6.1 (the action of $K_0(\mathfrak{p}^n)$).** Let $n \ge 0$.
1. The map $\left(\begin{smallmatrix} a & b \\ c & d \end{smallmatrix}\right) \mapsto d \bmod \mathfrak{p}^n$ is a homomorphism $K_0(\mathfrak{p}^n) \to (\mathcal{O} / \mathfrak{p}^n)^\times$ with kernel $K_1(\mathfrak{p}^n)$, and $K_0(\mathfrak{p}^n) = \mathcal{O}^\times K_1(\mathfrak{p}^n)$, with $\mathcal{O}^\times$ the scalar matrices.
2. If $\pi^{K_1(\mathfrak{p}^n)} \ne 0$, then $a(\omega_\pi) \le n$, and $k \in K_0(\mathfrak{p}^n)$ acts on $\pi^{K_1(\mathfrak{p}^n)}$ by the scalar $\omega_\pi(d)$.
3. If $v \in \pi^{K_1(\mathfrak{p}^n)}$, then $\pi(\mathrm{diag}(\varpi^{-1}, 1)) v \in \pi^{K_1(\mathfrak{p}^{n + 1})}$.

Lean: not stated yet.

*Proof.* For part 1, the lower right entry of a product in $K_0(\mathfrak{p}^n)$ is $c b' + d d' \equiv d d' \pmod{\mathfrak{p}^n}$, and the scalar $u$ maps to $u \bmod \mathfrak{p}^n$. For part 2, the scalars in $1 + \mathfrak{p}^n$ lie in $K_1(\mathfrak{p}^n)$, and $k = u k_1$ with $u \equiv d$ acts by $\omega_\pi(u)$. For part 3, with $g = \mathrm{diag}(\varpi^{-1}, 1)$, the matrix $g k g^{-1}$ has entries $a, \varpi^{-1} b, \varpi c, d$, so $g K_1(\mathfrak{p}^n) g^{-1} \supset K_1(\mathfrak{p}^{n + 1})$, and $\pi(g) v$ is fixed by $g K_1(\mathfrak{p}^n) g^{-1}$. $\square$

**Theorem 3.6.2 (Casselman).** There is an integer $c = c(\pi) \ge 0$ such that $\pi^{K_1(\mathfrak{p}^n)} = 0$ for $n < c$ and
$$\dim \pi^{K_1(\mathfrak{p}^n)} = n - c + 1 \quad \text{for } n \ge c.$$
If $v_0$ spans $\pi^{K_1(\mathfrak{p}^c)}$, then the vectors $\pi(\mathrm{diag}(\varpi^{-j}, 1)) v_0$, $0 \le j \le n - c$, form a basis of $\pi^{K_1(\mathfrak{p}^n)}$.

Lean: not stated yet. The classical counterpart, the oldspace spanned by the forms $f(d z)$, is `Langlands.Modular.oldSpace`, built from the maps `Langlands.Modular.levelRaise`.

**Definition 3.6.3 (conductor and newvector).** The integer $c(\pi)$ is the *conductor exponent* of $\pi$, and $\mathfrak{p}^{c(\pi)}$ is its *conductor*. A nonzero vector of the line $\pi^{K_1(\mathfrak{p}^{c(\pi)})}$ is a *newvector* of $\pi$.

The vectors of Lemma 3.6.1, part 3 are the local *oldvectors*: at $p$, $\pi(\mathrm{diag}(\varpi^{-1}, 1))$ corresponds to $f(z) \mapsto f(p z)$ up to a constant. So Theorem 3.6.2 at all primes gives the theorem of Atkin and Lehner. Casselman's proof uses the Kirillov model and the $\varepsilon$-factor: $c(\pi)$ is the exponent $a$ in $\varepsilon(s, \pi, \psi) = \varepsilon(1/2, \pi, \psi) q^{-a(s - 1/2)}$. R. Schmidt gives a short account in *Some remarks on local newforms for GL(2)* (J. Ramanujan Math. Soc. 17, 2002). For non-supercuspidal $\pi$ the proof is a count of double cosets.

### The principal series and the special representations

Let $\gamma_i = \left(\begin{smallmatrix} 1 & 0 \\ \varpi^i & 1 \end{smallmatrix}\right)$ for $0 \le i \le n$. In terms of Example 3.1.5, the coset $B \gamma_i$ corresponds to the point $[\varpi^i : 1]$ of $\mathbb{P}^1(K)$.

**Proposition 3.6.4 (fixed vectors of the principal series).** Let $n \ge 0$.
1. $G = \bigsqcup_{i = 0}^n B \gamma_i K_1(\mathfrak{p}^n)$, and $B \gamma_i K_1(\mathfrak{p}^n) = B \gamma_i K_0(\mathfrak{p}^n)$.
2. The diagonal parts of the elements of $B \cap \gamma_i K_1(\mathfrak{p}^n) \gamma_i^{-1}$ are the $\mathrm{diag}(a, d)$ with $a \in 1 + \mathfrak{p}^{n - i}$ and $d \in 1 + \mathfrak{p}^i$, where $1 + \mathfrak{p}^0 = \mathcal{O}^\times$.
3. For all $\chi_1, \chi_2$,
$$\dim (\chi_1 \times \chi_2)^{K_1(\mathfrak{p}^n)} = \max(0, \, n - a(\chi_1) - a(\chi_2) + 1).$$
A basis is given by the functions $f_i$ supported on $B \gamma_i K_1(\mathfrak{p}^n)$ with $f_i(\gamma_i) = 1$, for $a(\chi_2) \le i \le n - a(\chi_1)$.

Lean: not stated yet.

*Proof.* For part 1, the double cosets $B \backslash G / J$ are the orbits of $J$ on $B \backslash G = \mathbb{P}^1(K)$, where $B g$ corresponds to the bottom row of $g$, as in Example 3.1.5. Example 3.2.6 found $n + 1$ orbits for $J = K_1(\mathfrak{p}^n)$ and the same orbits for $J = K_0(\mathfrak{p}^n)$, represented by $[1 : 0]$ and $[\varpi^i : 1]$ for $1 \le i \le n$. The bottom row of $\gamma_i$ is $[\varpi^i : 1]$, and $[1 : 1]$ is in the orbit of $[1 : 0]$. So the $\gamma_i$ represent the orbits.

For part 2, let $b = \left(\begin{smallmatrix} a & x \\ 0 & d \end{smallmatrix}\right)$ and $t = \varpi^i$. A computation gives
$$\gamma_i^{-1} b \gamma_i = \begin{pmatrix} a + x t & x \\ t(d - a - x t) & d - x t \end{pmatrix}.$$
This lies in $K_1(\mathfrak{p}^n)$ if and only if $a, d \in \mathcal{O}^\times$, $x \in \mathcal{O}$, $d - x t \in 1 + \mathfrak{p}^n$ and $d - a - x t \in \mathfrak{p}^{n - i}$. The third condition gives $d \in 1 + \mathfrak{p}^i$, and then the fourth gives $a \equiv d - x t \equiv 1 \pmod{\mathfrak{p}^{n - i}}$. Conversely, for $a \in 1 + \mathfrak{p}^{n - i}$ and $d \in 1 + \mathfrak{p}^i$ the choice $x = (d - 1) / t$ satisfies all the conditions.

For part 3, a function $f \in (\chi_1 \times \chi_2)^{K_1(\mathfrak{p}^n)}$ is determined by its values $f(\gamma_i)$, by part 1. A value $f(\gamma_i) = 1$ extends to a function on $B \gamma_i K_1(\mathfrak{p}^n)$ by $f(b \gamma_i k) = \chi_1(a) \chi_2(d) \delta^{1/2}(b)$ if and only if this is well defined, that is, if $\chi_1(a) \chi_2(d) \delta^{1/2}(b) = 1$ for $b \in B \cap \gamma_i K_1(\mathfrak{p}^n) \gamma_i^{-1}$. These $b$ have unit diagonal entries, so $\delta(b) = 1$, and by part 2 the condition is that $\chi_1$ is trivial on $1 + \mathfrak{p}^{n - i}$ and $\chi_2$ is trivial on $1 + \mathfrak{p}^i$. That is, $a(\chi_1) \le n - i$ and $a(\chi_2) \le i$. The resulting function is right invariant under $K_1(\mathfrak{p}^n)$, so it is smooth. The number of such $i$ is $\max(0, n - a(\chi_1) - a(\chi_2) + 1)$. $\square$

**Corollary 3.6.5 (conductors of the non-supercuspidal representations).**
1. $c(\pi(\chi_1, \chi_2)) = a(\chi_1) + a(\chi_2)$.
2. $c(\eta \mathrm{St}) = 1$ if $\eta$ is unramified, and $c(\eta \mathrm{St}) = 2 a(\eta)$ if $\eta$ is ramified.
3. Theorem 3.6.2 holds for $\pi(\chi_1, \chi_2)$ and for $\eta \mathrm{St}$.

Lean: not stated yet.

*Proof.* Part 1 and the dimension formula for $\pi(\chi_1, \chi_2)$ are Proposition 3.6.4. For $\eta \mathrm{St}$, use the exact sequence $0 \to \eta \mathrm{St} \to \eta |\cdot|^{1/2} \times \eta |\cdot|^{-1/2} \to \eta \circ \det \to 0$ of Proposition 3.2.5. The functor of $K_1(\mathfrak{p}^n)$-fixed vectors is exact (Volume 6, Proposition 1.2.3). Since $\det K_1(\mathfrak{p}^n) = \mathcal{O}^\times$, the character $\eta \circ \det$ has a fixed vector if and only if $\eta$ is unramified. If $\eta$ is unramified, the principal series has $\dim = n + 1$, so $\dim (\eta \mathrm{St})^{K_1(\mathfrak{p}^n)} = n = n - 1 + 1$. If $\eta$ is ramified, then $a(\eta |\cdot|^{\pm 1/2}) = a(\eta)$, and $\dim (\eta \mathrm{St})^{K_1(\mathfrak{p}^n)} = \max(0, n - 2 a(\eta) + 1)$.

It remains to check the basis statement. The vectors $v_j = \pi(\mathrm{diag}(\varpi^{-j}, 1)) v_0$ for $0 \le j \le n - c$ lie in $\pi^{K_1(\mathfrak{p}^n)}$ by Lemma 3.6.1. Their Kirillov functions are $\xi_0(\varpi^{-j} y)$. By Proposition 3.6.7 below, for $c \ge 1$, and by Theorem 3.5.5, for $c = 0$, we have $\xi_0(y) \ne 0$ for $y \in \mathcal{O}^\times$, and $\xi_0$ is supported in $\mathcal{O}$. So $\xi_0(\varpi^{-j} y)$ is supported in $\mathfrak{p}^j$ and is nonzero on $\varpi^j \mathcal{O}^\times$. These functions are linearly independent, and there are $n - c + 1$ of them. $\square$

So $c(\mathrm{St}) = 1$, as Example 3.2.6 showed, and an unramified twist does not change the conductor.

**Theorem 3.6.6 (supercuspidal conductors).** If $\pi$ is supercuspidal, then $c(\pi) \ge 2$, and Theorem 3.6.2 holds for $\pi$.

Lean: not stated yet.

*Main steps.* By Corollary 3.4.7, $c(\pi) \ne 0$. A vector $v \ne 0$ fixed by $K_1(\mathfrak{p})$ is fixed by the pro-$p$ radical $I_1$ of the Iwahori subgroup (the matrices of $K_0(\mathfrak{p})$ with diagonal entries in $1 + \mathfrak{p}$), so $\pi$ has depth zero. By the structure theory of depth zero, $\pi$ is then as in Example 3.3.7, and its vectors fixed by $K(1) = 1 + \varpi M_2(\mathcal{O})$ form a sum of cuspidal representations of $GL_2(\mathbb{F}_q)$. These have no vector fixed by the upper unipotent group, but $v$ is one. So $c(\pi) \ge 2$. The dimension formula is Casselman's theorem, proved with the Kirillov model $C_c^\infty(K^\times)$ and the $\varepsilon$-factor. [BH06], Chapter 4 treats depth zero. $\square$

The depth zero representations of Example 3.3.7 have conductor exactly $2$. One way to see this is the local Langlands correspondence of Volume 6, Chapter 3, which preserves conductors: the parameter is induced from a tame character $\xi$ of the unramified quadratic extension, with conductor $f(E/K) a(\xi) + d(E/K) = 2$.

### The operator U and the newvector

Let $n \ge 1$ and $z = \mathrm{diag}(\varpi, 1)$. The double coset $K_1(\mathfrak{p}^n) z K_1(\mathfrak{p}^n)$ is the disjoint union of the $q$ cosets $n(b) z K_1(\mathfrak{p}^n)$, $b \in \mathcal{O} / \mathfrak{p}$. Indeed, these cosets are indexed by $K_1(\mathfrak{p}^n) / (K_1(\mathfrak{p}^n) \cap z K_1(\mathfrak{p}^n) z^{-1})$, and $z K_1(\mathfrak{p}^n) z^{-1}$ consists of the matrices $\left(\begin{smallmatrix} a & \varpi b \\ \varpi^{-1} c & d \end{smallmatrix}\right)$, so the intersection is the set of $k \in K_1(\mathfrak{p}^n)$ with upper right entry in $\mathfrak{p}$. Its index is $q$, with the representatives $n(b)$. The operator
$$U = \sum_{b \in \mathcal{O} / \mathfrak{p}} \pi\begin{pmatrix} \varpi & b \\ 0 & 1 \end{pmatrix}$$
is therefore well defined on $\pi^{K_1(\mathfrak{p}^n)}$ and preserves it. For $K = \mathbb{Q}_p$ and $p \mid N$ it is the local form of the classical operator $U_p$.

**Proposition 3.6.7 (the newvector in the Kirillov model).** Let $n \ge 0$ and $\xi \in \mathcal{K}(\pi, \psi)$ be fixed by $K_1(\mathfrak{p}^n)$.
1. $\xi(u y) = \xi(y)$ for $u \in \mathcal{O}^\times$, and $\xi$ is supported in $\mathcal{O}$.
2. If $n \ge 1$, then $U \xi(y) = q \, 1_{\mathcal{O}}(y) \, \xi(\varpi y)$.
3. Let $c = c(\pi) \ge 1$ and let $\xi_0$ be the Kirillov function of a newvector. Then $U \xi_0 = \lambda_U \xi_0$ for a scalar $\lambda_U$, and
$$\xi_0(\varpi^m u) = \xi_0(1) \, (\lambda_U / q)^m \quad (m \ge 0, \ u \in \mathcal{O}^\times), \qquad \xi_0(1) \ne 0.$$
4. With $\xi_0(1) = 1$, we have $Z(s, \xi_0) = (1 - \lambda_U q^{-1/2} q^{-s})^{-1}$.

Lean: not stated yet.

*Proof.* The group $K_1(\mathfrak{p}^n)$ contains $\left(\begin{smallmatrix} u & x \\ 0 & 1 \end{smallmatrix}\right)$ for $u \in \mathcal{O}^\times$ and $x \in \mathcal{O}$. By Theorem 3.5.3 this matrix maps $\xi$ to $y \mapsto \psi(x y) \xi(u y)$. With $x = 0$ we get the invariance under $\mathcal{O}^\times$. With $u = 1$ we get $\psi(x y) \xi(y) = \xi(y)$ for all $x \in \mathcal{O}$. If $y \notin \mathcal{O}$, there is $x \in \mathcal{O}$ with $\psi(x y) \ne 1$, since $\psi$ is unramified, so $\xi(y) = 0$. For part 2,
$$U \xi(y) = \sum_{b \in \mathcal{O} / \mathfrak{p}} \psi(b y) \, \xi(\varpi y).$$
The term vanishes unless $\varpi y \in \mathcal{O}$, by part 1. For $y \in \mathfrak{p}^{-1}$ the map $b \mapsto \psi(b y)$ is a character of $\mathcal{O} / \mathfrak{p}$. It is trivial if $y \in \mathcal{O}$, and nontrivial if $v(y) = -1$, since $\psi$ is unramified. So the sum is $q \, \xi(\varpi y)$ for $y \in \mathcal{O}$, and $0$ otherwise.

For part 3, $U$ preserves the line $\pi^{K_1(\mathfrak{p}^c)}$, so it acts by a scalar $\lambda_U$. Part 2 at $y = \varpi^m u$ gives $\lambda_U \xi_0(\varpi^m) = q \xi_0(\varpi^{m + 1})$ for $m \ge 0$, and induction gives the formula. If $\xi_0(1) = 0$, then $\xi_0 = 0$, which contradicts the injectivity of the Kirillov map. Part 4 is the sum $\sum_{m \ge 0} (\lambda_U / q)^m q^{-m(s - 1/2)}$. $\square$

**Theorem 3.6.8 (eigenvalues of U and the L-factor).** Let $c = c(\pi) \ge 1$. The eigenvalue $\lambda_U$ of $U$ on the newvector is:
1. $q^{1/2} \chi_1(\varpi)$ if $\pi = \pi(\chi_1, \chi_2)$ with $\chi_1$ unramified and $\chi_2$ ramified;
2. $\eta(\varpi)$ if $\pi = \eta \mathrm{St}$ with $\eta$ unramified;
3. $0$ in all other cases: $\pi(\chi_1, \chi_2)$ with both $\chi_i$ ramified, $\eta \mathrm{St}$ with $\eta$ ramified, and $\pi$ supercuspidal.

In all cases, including $c = 0$, the newvector with $\xi_0(1) = 1$ satisfies $Z(s, \xi_0) = L(s, \pi)$.

Lean: not stated yet.

*Proof.* Case 1. By Proposition 3.2.3 we may order the characters so that $\chi_1$ is the unramified one. Here $c = a(\chi_2)$, and by Proposition 3.6.4 the only $i$ with $a(\chi_2) \le i \le c - a(\chi_1) = c$ is $i = c$. So the newvector $f_0$ is supported on $B K_1(\mathfrak{p}^c)$, and $f_0(1) = 1$. Then
$$(U f_0)(1) = \sum_{b \in \mathcal{O} / \mathfrak{p}} f_0\begin{pmatrix} \varpi & b \\ 0 & 1 \end{pmatrix} = q \cdot \chi_1(\varpi) |\varpi|^{1/2} = q^{1/2} \chi_1(\varpi).$$

Case 3. Suppose that $\lambda_U \ne 0$. By Proposition 3.6.7, near $0$ the function $\xi_0$ is $\xi_0(1) \mu(y) |y|^{1/2}$, where $\mu$ is the unramified character with $\mu(\varpi) = \lambda_U q^{-1/2}$, so $\int_{\mathcal{O}^\times} \xi_0(\varpi^m u) \, du \ne 0$ for all $m \ge 0$. In each case of part 3, Proposition 3.5.4 shows that for $m$ large the function $u \mapsto \xi_0(\varpi^m u)$ is a combination of ramified characters of $\mathcal{O}^\times$ (or zero, for supercuspidal $\pi$), so its integral over $\mathcal{O}^\times$ is $0$. This is a contradiction, so $\lambda_U = 0$.

Case 2. Here $c = 1$. Let $V = \eta |\cdot|^{1/2} \times \eta |\cdot|^{-1/2}$, with $z_1 = \eta(\varpi) q^{-1/2}$ and $z_2 = \eta(\varpi) q^{1/2}$. By Proposition 3.6.4, $V^{K_1(\mathfrak{p})}$ has the basis $f_1, f_0$, supported on $B K_1(\mathfrak{p})$ and $B w K_1(\mathfrak{p})$, with $f_1(1) = f_0(w) = 1$. As in case 1, $(U f_1)(1) = q^{1/2} z_1$. The matrix $w \left(\begin{smallmatrix} \varpi & b \\ 0 & 1 \end{smallmatrix}\right)$ has bottom row $[\varpi : b]$, which is in the orbit of $[1 : 0]$ only for $b = 0$, and then it is $\mathrm{diag}(1, \varpi) w$. So $(U f_0)(w) = \chi_2(\varpi) q^{1/2} = q^{1/2} z_2$, and the trace of $U$ is $q^{1/2}(z_1 + z_2) = (1 + q) \eta(\varpi)$. On the quotient $\eta \circ \det$, $U$ acts by $\sum_b \eta(\det(n(b) z)) = q \eta(\varpi)$. So on the line $(\eta \mathrm{St})^{K_1(\mathfrak{p})}$, $\lambda_U = (1 + q) \eta(\varpi) - q \eta(\varpi) = \eta(\varpi)$.

For the last statement, Proposition 3.6.7 gives $Z(s, \xi_0) = (1 - \lambda_U q^{-1/2} q^{-s})^{-1}$. In case 1 this is $(1 - \chi_1(\varpi) q^{-s})^{-1} = L(s, \chi_1) L(s, \chi_2)$. In case 2 it is $(1 - \eta(\varpi) q^{-s - 1/2})^{-1} = L(s, \eta \mathrm{St})$. In case 3 it is $1 = L(s, \pi)$. These agree with Proposition 3.5.8, and the case $c = 0$ is Proposition 3.5.8, part 4. $\square$

So the newvector is a test vector: its zeta integral is the $L$-factor.

### Consequences for modular forms

Let $f$ be a newform of weight $k$ and level $N$, and $\pi$ its automorphic representation. Chapter 4 shows that $c(\pi_p) = v_p(N)$, and that the eigenvalue of $U$ on the newvector at $p \mid N$ is $p^{1 - k/2} a_p$ in the normalizations of Section 3.4.

**Corollary 3.6.9 (Fourier coefficients at bad primes).** Let $f$ be a newform of weight $k$, level $N$ and trivial character, and let $p \mid N$.
1. If $p \parallel N$, then $\pi_p = \eta \mathrm{St}$ with $\eta$ unramified and $\eta(p) = \pm 1$, and $a_p = \eta(p) p^{k/2 - 1}$.
2. If $p^2 \mid N$, then $a_p = 0$.
3. If $v_p(N)$ is odd and at least $3$, then $\pi_p$ is supercuspidal.

Lean: not stated yet.

*Proof.* The central character of $\pi_p$ is trivial. For part 1, $c(\pi_p) = 1$. By Corollary 3.6.5 and Theorem 3.6.6, $\pi_p$ is $\eta \mathrm{St}$ with $\eta$ unramified, or $\pi(\chi_1, \chi_2)$ with $a(\chi_1) + a(\chi_2) = 1$. In the second case $\chi_1 \chi_2 = 1$ forces $a(\chi_1) = a(\chi_2)$, which is impossible. So $\pi_p = \eta \mathrm{St}$, with $\eta^2 = 1$ and $\eta$ unramified, so $\eta(p) = \pm 1$. Theorem 3.6.8 gives $p^{1 - k/2} a_p = \eta(p)$. For part 2, $c(\pi_p) \ge 2$. If $\pi_p = \pi(\chi_1, \chi_2)$, then $a(\chi_1) = a(\chi_2) \ge 1$, so both are ramified. If $\pi_p = \eta \mathrm{St}$, then $\eta$ is ramified. In all cases Theorem 3.6.8 gives $\lambda_U = 0$. For part 3, $c(\pi(\chi_1, \chi_2)) = 2 a(\chi_1)$ and $c(\eta \mathrm{St}) \in \{1, 2 a(\eta)\}$. An odd value at least $3$ excludes both. $\square$

**Example 3.6.10 (the curves of conductor 11 and 27).** The curve $y^2 + y = x^3 - x^2 - 10 x - 20$ has conductor $11$ and $a_{11} = 1$. Corollary 3.6.9 with $k = 2$ gives $\eta(11) = 1$, so $\pi_{11} = \mathrm{St}$. Its newvector has the Kirillov function $|y| 1_{\mathbb{Z}_{11}}(y)$ and the zeta integral $(1 - 11^{-s - 1/2})^{-1}$, which becomes the Euler factor $(1 - 11^{-s})^{-1}$ of $L(E, s)$ after the shift of Volume 0. The curve $y^2 + y = x^3$ has conductor $27 = 3^3$. By Corollary 3.6.9, part 3, its local component at $3$ is supercuspidal, $a_3 = 0$, and the Euler factor at $3$ is $1$. By Remark 3.3.10 it is dihedral. Since the curve has complex multiplication by $\mathbb{Z}[\zeta_3]$, it comes from a character of $\mathbb{Q}_3(\sqrt{-3})$.

### Summary of the local invariants

The following table collects the invariants of the generic irreducible representations. Here $\chi_1, \chi_2, \eta$ are characters of $K^\times$, $L(s, \chi)$ is as in Proposition 3.5.8, and $\lambda_U$ is the eigenvalue of $U$ on the newvector when $c \ge 1$.

| $\pi$ | $\omega_\pi$ | $\dim r_B(\pi)$ | $c(\pi)$ | $L(s, \pi)$ | $\lambda_U$ |
| --- | --- | --- | --- | --- | --- |
| $\pi(\chi_1, \chi_2)$ | $\chi_1 \chi_2$ | $2$ | $a(\chi_1) + a(\chi_2)$ | $L(s, \chi_1) L(s, \chi_2)$ | $q^{1/2} \chi_1(\varpi)$ if only $\chi_1$ is unramified, $0$ if both are ramified |
| $\eta \mathrm{St}$, $\eta$ unramified | $\eta^2$ | $1$ | $1$ | $(1 - \eta(\varpi) q^{-s - 1/2})^{-1}$ | $\eta(\varpi)$ |
| $\eta \mathrm{St}$, $\eta$ ramified | $\eta^2$ | $1$ | $2 a(\eta)$ | $1$ | $0$ |
| supercuspidal | $\omega_\pi$ | $0$ | $\ge 2$ | $1$ | $0$ |
