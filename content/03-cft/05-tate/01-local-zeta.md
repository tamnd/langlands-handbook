---
title: Local zeta integrals
nodes: []
sources: [CF67]
status: checked
drafted_by: writer
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## Local zeta integrals

In this section $K$ is a local field. It is $\mathbb{R}$, $\mathbb{C}$, or a nonarchimedean local field with the notation of Chapter 4. The normalized absolute value is $|x|_K$, or $|x|$ when $K$ is clear. On $\mathbb{R}$ it is the usual absolute value. On $\mathbb{C}$ it is $|z|_\mathbb{C} = z \bar z$, the square of the usual absolute value. By Proposition 3.3.1 of Volume 1, $|a|_K$ is the factor by which multiplication by $a$ changes a Haar measure of $K$. The section sets up the objects of Tate's local theory: additive characters, self-dual measures, Schwartz-Bruhat functions, characters of $K^\times$ and the local zeta integral.

### Additive characters

A character of the additive group $K$ is a continuous homomorphism $K \to \mathbb{C}^\times$. Its image lies in the unit circle. For a character $\psi$ and $a \in K$, let $\psi_a(x) = \psi(ax)$.

**Definition 5.1.1 (the exponent of an additive character).** Let $K$ be nonarchimedean, and let $\psi$ be a nontrivial character of $K$. The *exponent* of $\psi$ is the integer $d(\psi)$ such that $\psi$ is trivial on $\mathfrak{p}^{-d(\psi)}$ and not trivial on $\mathfrak{p}^{-d(\psi)-1}$.

The exponent exists. The kernel of $\psi$ is an open subgroup, so it contains some $\mathfrak{p}^m$. The character is not trivial, and $K$ is the union of the groups $\mathfrak{p}^{-m}$, so $\psi$ is not trivial on some $\mathfrak{p}^{-m}$. In the language of Chapter 4, $\psi$ has conductor $\mathcal{O}_K$ exactly when $d(\psi) = 0$. For $a \in K^\times$ the character $\psi_a$ is trivial on $\mathfrak{p}^m$ if and only if $\psi$ is trivial on $\mathfrak{p}^{m + v(a)}$. Thus $d(\psi_a) = d(\psi) + v(a)$.

The standard characters are those of Volume 1, Section 3.3. On $\mathbb{Q}_p$ it is $\psi_{\mathbb{Q}_p}(x) = e^{2\pi i \{x\}_p}$, where $\{x\}_p \in \mathbb{Z}[1/p]$ is the fractional part. On a finite extension $K$ of $\mathbb{Q}_p$ it is $\psi_K = \psi_{\mathbb{Q}_p} \circ \mathrm{Tr}_{K/\mathbb{Q}_p}$. On $\mathbb{R}$ it is $\psi_\mathbb{R}(x) = e^{-2\pi i x}$, and on $\mathbb{C}$ it is $\psi_\mathbb{C}(z) = \psi_\mathbb{R}(z + \bar z) = e^{-4\pi i \,\mathrm{Re}(z)}$. The character $\psi_{\mathbb{Q}_p}$ has exponent 0. For $K / \mathbb{Q}_p$, the character $\psi_K$ is trivial on $\mathfrak{p}^m$ if and only if $\mathrm{Tr}(\mathfrak{p}^m) \subset \mathbb{Z}_p$, that is, if and only if $\mathfrak{p}^m$ lies in the inverse different. By Definition 2.5.4 of Volume 1, this gives
$$d(\psi_K) = v_K(\mathfrak{D}_{K/\mathbb{Q}_p}).$$
The exponent of $\psi_K$ is 0 exactly when $K / \mathbb{Q}_p$ is unramified.

**Proposition 5.1.2 (self-duality of $K$).** Let $\psi$ be a nontrivial character of $K$. The map $a \mapsto \psi_a$ is an isomorphism of topological groups from $K$ to its Pontryagin dual $\hat K$.

Lean: not stated yet

*Proof.* The map is a homomorphism. It is injective, because $\psi_a = 1$ with $a \ne 0$ gives $\psi(K) = \psi(aK) = 1$. We prove surjectivity for nonarchimedean $K$. Let $d = d(\psi)$, and let $\chi$ be a character of $K$. It is trivial on some $\mathfrak{p}^m$. For $n \ge -m$ consider the finite group $\mathfrak{p}^{-n} / \mathfrak{p}^m$ of order $q^{n+m}$. For $a \in \mathfrak{p}^{-m-d}$ the character $\psi_a$ is trivial on $\mathfrak{p}^m$, and its restriction to $\mathfrak{p}^{-n}$ is trivial if and only if $a \in \mathfrak{p}^{n-d}$. So the elements of $\mathfrak{p}^{-m-d} / \mathfrak{p}^{n-d}$ give $q^{n+m}$ distinct characters of $\mathfrak{p}^{-n} / \mathfrak{p}^m$. This is the number of all its characters. Thus there is $a_n \in \mathfrak{p}^{-m-d}$ with $\chi = \psi_{a_n}$ on $\mathfrak{p}^{-n}$, and $a_n$ is unique modulo $\mathfrak{p}^{n-d}$. Then $a_{n+1} - a_n \in \mathfrak{p}^{n-d}$, so the sequence $(a_n)$ converges to some $a$, and $\chi = \psi_a$ on each $\mathfrak{p}^{-n}$. For $K = \mathbb{R}$ every character has the form $x \mapsto e^{2\pi i b x}$ with $b \in \mathbb{R}$, and this is $\psi_{-b}$. For $K = \mathbb{C}$ the same holds for the real vector space $\mathbb{R}^2$, and the pairing $(z, w) \mapsto \mathrm{Re}(zw)$ is nondegenerate. The statement on the topology is in [CF67], Chapter XV, Section 2.2. $\square$

### Schwartz-Bruhat functions and the Fourier transform

**Definition 5.1.3 (Schwartz-Bruhat functions).** If $K$ is nonarchimedean, a *Schwartz-Bruhat function* on $K$ is a locally constant function $f : K \to \mathbb{C}$ with compact support. If $K = \mathbb{R}$, it is a Schwartz function: a smooth function $f$ such that $x^a f^{(b)}(x)$ is bounded for all $a, b \ge 0$. If $K = \mathbb{C}$, it is a Schwartz function on $\mathbb{R}^2$. The space of these functions is $\mathcal{S}(K)$.

A nonarchimedean Schwartz-Bruhat function is constant on the cosets of some $\mathfrak{p}^m$ and vanishes outside some $\mathfrak{p}^{-n}$. So it is a finite linear combination of functions $1_{b + \mathfrak{p}^m}$. Tate's thesis uses a larger class of functions, defined by conditions of integrability. The class $\mathcal{S}(K)$ is contained in Tate's class, and it is enough for all the results of this chapter.

Fix a nontrivial character $\psi$ of $K$ and a Haar measure $dx$ on $K$. The *Fourier transform* of $f \in \mathcal{S}(K)$ is
$$\hat f(y) = \int_K f(x) \psi(xy) \, dx.$$
For nonarchimedean $K$ the transform of a basic function is easy to compute. The integral of a nontrivial character over a compact group is 0. The character $x \mapsto \psi(xy)$ is trivial on $\mathfrak{p}^m$ if and only if $y \in \mathfrak{p}^{-m-d}$, where $d = d(\psi)$. With the substitution $x = b + t$ this gives
$$\hat 1_{b + \mathfrak{p}^m}(y) = \psi(by) \, \mathrm{vol}(\mathfrak{p}^m) \, 1_{\mathfrak{p}^{-m-d}}(y).$$
Thus the Fourier transform maps $\mathcal{S}(K)$ to itself. For archimedean $K$ this is a classical fact of analysis.

**Proposition 5.1.4 (the self-dual measure).** There is a unique Haar measure $dx$ on $K$ such that $\hat{\hat f}(x) = f(-x)$ for all $f \in \mathcal{S}(K)$. It is the *self-dual measure* for $\psi$.
1. If $K$ is nonarchimedean, the self-dual measure is the Haar measure with $\mathrm{vol}(\mathcal{O}_K) = q^{-d(\psi)/2}$.
2. If $K = \mathbb{R}$ and $\psi = \psi_\mathbb{R}$, it is the Lebesgue measure $dx$.
3. If $K = \mathbb{C}$ and $\psi = \psi_\mathbb{C}$, it is $2 \, dx \, dy$, twice the Lebesgue measure.
4. If $dx$ is self-dual for $\psi$ and $a \in K^\times$, then $|a|^{1/2} dx$ is self-dual for $\psi_a$.

Lean: not stated yet

*Proof.* If the measure $dx$ is replaced by $c \, dx$, then $\hat{\hat f}$ is multiplied by $c^2$. So at most one Haar measure has the property, and it is enough to find one. Let $K$ be nonarchimedean, $d = d(\psi)$ and $c = \mathrm{vol}(\mathcal{O}_K)$. Apply the formula for $\hat 1_{b + \mathfrak{p}^m}$ twice, with $b = 0$:
$$\hat{\hat 1}_{\mathfrak{p}^m} = \mathrm{vol}(\mathfrak{p}^m) \, \mathrm{vol}(\mathfrak{p}^{-m-d}) \, 1_{\mathfrak{p}^m} = c^2 q^{-m} q^{m+d} \, 1_{\mathfrak{p}^m} = c^2 q^d \, 1_{\mathfrak{p}^m}.$$
This is $1_{\mathfrak{p}^m}$ if and only if $c = q^{-d/2}$. Now fix this measure. Let $g(x) = f(x - b)$ and $h(x) = \psi(bx) f(x)$. A substitution gives $\hat g = \psi_b \hat f$ and $\hat h(y) = \hat f(y + b)$. Thus $\hat{\hat g}(x) = \hat{\hat f}(x + b)$. If $\hat{\hat f}(x) = f(-x)$, then $\hat{\hat g}(x) = f(-x - b) = g(-x)$. The functions $1_{b + \mathfrak{p}^m}$ span $\mathcal{S}(K)$, so part 1 follows.

For $K = \mathbb{R}$, the transform with $\psi_\mathbb{R}$ and $dx$ is the classical $\hat f(y) = \int f(x) e^{-2\pi i xy} dx$. The classical inversion formula gives $\hat{\hat f}(x) = f(-x)$. For $K = \mathbb{C}$ write $z = x + iy$ and $w = u + iv$. Then $\psi_\mathbb{C}(zw) = e^{-2\pi i \cdot 2(xu - yv)}$. This is the pairing of $\mathbb{R}^2$ given by the matrix $\mathrm{diag}(2, -2)$. For the pairing $e^{-2\pi i B(x, y)}$ with a matrix $B$, the self-dual measure is $|\det B|^{1/2}$ times the Lebesgue measure, by a linear change of variables in the classical formula. Here $|\det B|^{1/2} = 2$.

For part 4, let $\mathcal{F}_a$ be the transform for $\psi_a$ and the measure $dx$. Then $\mathcal{F}_a f(y) = \hat f(ay)$, and
$$\mathcal{F}_a \mathcal{F}_a f(x) = \int_K \hat f(ay) \psi(axy) \, dy = |a|^{-1} \int_K \hat f(u) \psi(xu) \, du = |a|^{-1} f(-x).$$
So the measure $|a|^{1/2} dx$ is self-dual for $\psi_a$. $\square$

The self-dual measure for the standard character $\psi_K$ of a $p$-adic field gives $\mathrm{vol}(\mathcal{O}_K) = N(\mathfrak{D}_{K/\mathbb{Q}_p})^{-1/2}$. These are the local factors of the Tamagawa measure of Volume 1, Section 3.3. If $d(\psi) = 0$, the self-dual measure gives $\mathrm{vol}(\mathcal{O}_K) = 1$, and $\hat 1_{\mathcal{O}_K} = 1_{\mathcal{O}_K}$. This is the measure of Chapter 4.

For the self-dual measure the transform of a Gaussian is easy to find. On $\mathbb{R}$, the function $e^{-\pi x^2}$ is its own transform. On $\mathbb{C}$, with $\psi_\mathbb{C}$ and $2 \, dx \, dy$, the function $e^{-2\pi z \bar z}$ is its own transform. For the second claim, the substitution $x = x'/\sqrt 2$ gives $\int_\mathbb{R} e^{-2\pi x^2} e^{-4\pi i x u} dx = 2^{-1/2} e^{-2\pi u^2}$. The same holds in $y$, and the factor 2 of the measure cancels the two factors $2^{-1/2}$.

### Characters of $K^\times$ and Tate's measure

**Definition 5.1.5 (Tate's multiplicative measure).** Let $dx$ be the self-dual measure for $\psi$. If $K$ is nonarchimedean, let
$$d^\times x = \frac{q}{q-1} \, \frac{dx}{|x|}.$$
If $K$ is archimedean, let $d^\times x = dx / |x|_K$.

These are Haar measures on $K^\times$, because $d(ax) = |a| dx$. For nonarchimedean $K$,
$$\mathrm{vol}(\mathcal{O}_K^\times, d^\times x) = \frac{q}{q-1} \, \mathrm{vol}(\mathcal{O}_K^\times, dx) = \frac{q}{q-1} \Big(1 - \frac{1}{q}\Big) q^{-d/2} = q^{-d/2},$$
with $d = d(\psi)$. If $d = 0$, then $\mathrm{vol}(\mathcal{O}_K^\times) = 1$, which is the measure of Chapter 4. Tate chose the factor $q/(q-1)$ for this property. It also gives the formula $|x| \, d^\times x = c_K \, dx$, with $c_K = q/(q-1)$ for nonarchimedean $K$ and $c_K = 1$ for archimedean $K$. The proof of the local functional equation uses this formula. The multiplicative measure depends on $\psi$ through $dx$. The $\gamma$-factor and the $\varepsilon$-factor do not depend on it, because they are ratios of two zeta integrals for the same measure.

A *character* of $K^\times$ is a continuous homomorphism $\chi : K^\times \to \mathbb{C}^\times$. Tate calls it a *quasi-character*, and he keeps the word character for the unitary ones. We follow Chapter 4. The *unramified* characters are those that are trivial on the maximal compact subgroup. This subgroup is $\mathcal{O}_K^\times$ if $K$ is nonarchimedean, $\{\pm 1\}$ if $K = \mathbb{R}$, and the unit circle if $K = \mathbb{C}$. The unramified characters are the maps $x \mapsto |x|^s$ with $s \in \mathbb{C}$. For nonarchimedean $K$ the number $s$ is unique modulo $2\pi i / \log q$, and for archimedean $K$ it is unique.

**Proposition 5.1.6 (the exponent of a character).** Let $\chi$ be a character of $K^\times$. There is a unique real number $\sigma = \sigma(\chi)$ with $|\chi(x)| = |x|^\sigma$ for all $x \in K^\times$. Thus $\chi = \chi_0 |\cdot|^\sigma$ with $\chi_0$ unitary.

Lean: not stated yet

*Proof.* The map $x \mapsto |\chi(x)|$ is a continuous homomorphism to $\mathbb{R}_{>0}$. The image of the maximal compact subgroup is a compact subgroup of $\mathbb{R}_{>0}$, so it is $\{1\}$. Thus $|\chi|$ factors through $|\cdot| : K^\times \to \mathbb{R}_{>0}$. The image of this map is $q^\mathbb{Z}$ or $\mathbb{R}_{>0}$, and each continuous homomorphism from it to $\mathbb{R}_{>0}$ is $t \mapsto t^\sigma$ for a unique real $\sigma$. $\square$

The number $\sigma(\chi)$ is the *exponent* of $\chi$ of Chapter 4. We have $\sigma(\chi^{-1}) = -\sigma(\chi)$ and $\sigma(\chi |\cdot|^s) = \sigma(\chi) + \mathrm{Re}(s)$.

**Proposition 5.1.7 (characters of $\mathbb{R}^\times$ and $\mathbb{C}^\times$).**
1. Each character of $\mathbb{R}^\times$ is $\chi(x) = \mathrm{sgn}(x)^a |x|^t$ for a unique $a \in \{0, 1\}$ and a unique $t \in \mathbb{C}$.
2. Each character of $\mathbb{C}^\times$ is $\chi(z) = (z / \sqrt{z \bar z})^n |z|_\mathbb{C}^t$ for a unique $n \in \mathbb{Z}$ and a unique $t \in \mathbb{C}$.

In both cases $\sigma(\chi) = \mathrm{Re}(t)$.

Lean: not stated yet

*Proof.* We have $\mathbb{R}^\times = \{\pm 1\} \times \mathbb{R}_{>0}$ and $\mathbb{C}^\times = U(1) \times \mathbb{R}_{>0}$ as topological groups, where $U(1)$ is the unit circle. The characters of $\{\pm 1\}$ are $\mathrm{sgn}^a$ with $a \in \{0, 1\}$. The characters of $U(1)$ are $u \mapsto u^n$ with $n \in \mathbb{Z}$. A continuous homomorphism $\mathbb{R}_{>0} \to \mathbb{C}^\times$ is $r \mapsto r^c$ for a unique $c \in \mathbb{C}$, because the substitution $r = e^u$ turns it into a continuous homomorphism $\mathbb{R} \to \mathbb{C}^\times$, and each of these is $u \mapsto e^{cu}$. On $\mathbb{C}^\times$ write $c = 2t$, so that $r^c = |z|_\mathbb{C}^t$ for $r = |z|$. The pair is unique because the decomposition of the group is unique. $\square$

In the Lean project these pairs are the *archimedean parameters* of a Hecke character, see Remark 5.5.4.

### The local zeta integral

**Definition 5.1.8 (the local zeta integral).** Let $f \in \mathcal{S}(K)$ and let $\chi$ be a character of $K^\times$. The *local zeta integral* is
$$Z(f, \chi, s) = \int_{K^\times} f(x) \chi(x) |x|^s \, d^\times x, \qquad s \in \mathbb{C}.$$

For nonarchimedean $K$ and $d(\psi) = 0$ this is the integral of Chapter 4. Tate writes $\zeta(f, c)$, where $c = \chi |\cdot|^s$ is a quasi-character. The two variables $\chi$ and $s$ carry the same information, because $Z(f, \chi |\cdot|^t, s) = Z(f, \chi, s + t)$.

**Proposition 5.1.9 (convergence).** Let $\sigma = \sigma(\chi)$ and $f \in \mathcal{S}(K)$. The integral $Z(f, \chi, s)$ converges absolutely for $\mathrm{Re}(s) > -\sigma$. It is a holomorphic function of $s$ on this half plane.

Lean: not stated yet

*Proof.* Let $u = \mathrm{Re}(s) + \sigma$. The absolute value of the integrand is $|f(x)| |x|^u$. Let $K$ be nonarchimedean. Then $|f| \le C \cdot 1_{\mathfrak{p}^{-N}}$ for some $C$ and $N$. The set $\mathfrak{p}^{-N} \smallsetminus \{0\}$ is the disjoint union of the shells $\varpi^k \mathcal{O}_K^\times$ for $k \ge -N$. Each shell has volume $q^{-d/2}$, and $|x|^u = q^{-ku}$ on it. So the integral is at most $C q^{-d/2} \sum_{k \ge -N} q^{-ku}$, which is finite for $u > 0$. Let $K$ be archimedean. Then $|f(x)| \le C$, and $|f(x)| \le C' |x|^{-u-1}$ for $|x| \ge 1$. The integral of $|x|^u d^\times x$ over $0 < |x| \le 1$ is finite for $u > 0$. The integral over $|x| \ge 1$ is finite for all $u$. The bounds are uniform for $s$ in a compact subset of the half plane. So the integral is a locally uniform limit of holomorphic functions, and it is holomorphic. $\square$

For $f = 1_{\mathcal{O}_K}$ and unramified $\chi$ the proof gives the first example:
$$Z(1_{\mathcal{O}_K}, \chi, s) = q^{-d/2} \sum_{k \ge 0} \chi(\varpi)^k q^{-ks} = \frac{q^{-d/2}}{1 - \chi(\varpi) q^{-s}}, \qquad \mathrm{Re}(s) > -\sigma.$$
The right side is a meromorphic function of $s$ on all of $\mathbb{C}$. Section 5.2 proves that every local zeta integral has such a continuation.

**Remark 5.1.10 (the Gamma factor as a local integral).** The integral $Z(f, \chi, s)$ is the Mellin transform of $f$ on the group $K^\times$. For $K = \mathbb{R}$, $f(x) = e^{-\pi x^2}$ and $\chi = 1$ it is
$$\int_{\mathbb{R}^\times} e^{-\pi x^2} |x|^s \frac{dx}{|x|} = 2 \int_0^\infty e^{-\pi x^2} x^s \frac{dx}{x} = \pi^{-s/2} \Gamma(s/2).$$
This is the factor that Riemann put in front of $\zeta(s)$. Tate's observation is that the Euler factors of $\zeta(s)$ are Mellin transforms of the same kind, for $f = 1_{\mathbb{Z}_p}$ on $\mathbb{Q}_p^\times$. The archimedean factor and the Euler factors are then the same object.
