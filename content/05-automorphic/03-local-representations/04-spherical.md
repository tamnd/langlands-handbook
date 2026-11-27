---
title: Unramified representations and the Satake isomorphism
nodes: []
sources: [BH06, JL70]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Unramified representations and the Satake isomorphism

At almost all primes $p$, the local component $\pi_p$ of a cuspidal automorphic representation has a nonzero vector fixed by $GL_2(\mathbb{Z}_p)$. This section classifies these representations by their Satake parameters and relates them to the Hecke operators $T_p$ of Volume 4. Volume 6, Section 1.2 proves the Satake isomorphism for $GL_n$ by the general method. For $GL_2$ every step can be computed by hand, and the explicit formulas are the ones that the global theory uses.

### The spherical Hecke algebra

Fix the Haar measure on $G$ with $\mathrm{vol}(K_0) = 1$. For $\lambda = (m_1, m_2) \in \mathbb{Z}^2$ write $\varpi^\lambda = \mathrm{diag}(\varpi^{m_1}, \varpi^{m_2})$. We call $\lambda$ *dominant* if $m_1 \ge m_2$.

**Definition 3.4.1 (spherical Hecke algebra).** The *spherical Hecke algebra* $\mathcal{H} = \mathcal{H}(G, K_0)$ is the space of the functions $f : G \to \mathbb{C}$ with compact support that satisfy $f(k g k') = f(g)$ for $k, k' \in K_0$, with the convolution product
$$(f_1 * f_2)(g) = \int_G f_1(h) f_2(h^{-1} g) \, dh.$$
For dominant $\lambda$ let $c_\lambda$ be the characteristic function of $K_0 \varpi^\lambda K_0$. We write $T = c_{(1, 0)}$ and $R = c_{(1, 1)}$.

Lean: not stated yet. The Lean project has the global Hecke operators of this kind as `Langlands.adelicHeckeOperator`, defined by a sum over the cosets of $K_0 \, \mathrm{diag}(\varpi, 1) \, K_0 / K_0$.

The unit of $\mathcal{H}$ is $c_{(0, 0)} = 1_{K_0}$. The element $R$ is translation by the central element $\varpi$, so it is invertible with inverse $c_{(-1, -1)}$.

**Lemma 3.4.2 (basis).** The functions $c_\lambda$, for $\lambda$ dominant, form a basis of $\mathcal{H}$. For each $j \in \mathbb{Z}$ we have $c_{(m_1 + j, m_2 + j)} = R^j * c_{(m_1, m_2)}$.

Lean: not stated yet.

*Proof.* By the Cartan decomposition (Lemma 3.1.2), $G$ is the disjoint union of the double cosets $K_0 \varpi^\lambda K_0$ for $\lambda$ dominant. A function in $\mathcal{H}$ is constant on each of them, and it has compact support, so it is nonzero on finitely many of them, since each double coset is open. This gives the basis. The second statement holds because $\varpi^{(j, j)}$ is central and $\varpi^{(j, j)} K_0 \varpi^\lambda K_0 = K_0 \varpi^{\lambda + (j, j)} K_0$. $\square$

**Proposition 3.4.3 (Gelfand).** The algebra $\mathcal{H}$ is commutative.

Lean: not stated yet.

*Proof.* Let $\iota(g) = {}^t g$ be the transpose. It is an anti-automorphism of $G$, it maps $K_0$ to $K_0$, and it preserves the Haar measure. For $f \in \mathcal{H}$ put $f^\iota = f \circ \iota$. A change of variables gives $(f_1 * f_2)^\iota = f_2^\iota * f_1^\iota$. Since $\iota(\varpi^\lambda) = \varpi^\lambda$ and $\iota(K_0) = K_0$, we have $c_\lambda^\iota = c_\lambda$, so $f^\iota = f$ for all $f \in \mathcal{H}$ by Lemma 3.4.2. So $f_1 * f_2 = (f_1 * f_2)^\iota = f_2^\iota * f_1^\iota = f_2 * f_1$. $\square$

This is the case $n = 2$ of Volume 6, Theorem 1.2.4. For a smooth $(\pi, V)$ and $f \in \mathcal{H}$, the operator $\pi(f) v = \int_G f(g) \pi(g) v \, dg$ maps $V$ into $V^{K_0}$, and $\pi(f_1 * f_2) = \pi(f_1) \pi(f_2)$. If $\pi$ is irreducible admissible, $V^{K_0}$ is zero or a simple $\mathcal{H}$-module (Volume 6, Proposition 1.2.3), so $\dim V^{K_0} \le 1$.

### The Satake transform

Let $\delta(\mathrm{diag}(a, d)) = |a / d|$ be the modulus character of $B$, as in Section 3.1. Let $N$ have the Haar measure with $\mathrm{vol}(N(\mathcal{O})) = 1$. We identify a function on $T / T(\mathcal{O}) \cong \mathbb{Z}^2$ with finite support with a Laurent polynomial in $\mathbb{C}[X_1^{\pm 1}, X_2^{\pm 1}]$, by $\varpi^{(a, b)} \mapsto X_1^a X_2^b$.

**Definition 3.4.4 (Satake transform).** For $f \in \mathcal{H}$ and $t \in T$ put
$$\mathcal{S} f(t) = \delta^{1/2}(t) \int_N f(t n) \, dn.$$
This function is invariant under $T(\mathcal{O})$, and has finite support on $T / T(\mathcal{O})$, so we view $\mathcal{S} f$ as an element of $\mathbb{C}[X_1^{\pm 1}, X_2^{\pm 1}]$.

Lean: not stated yet.

The next computation is the basic one. We need the coset decomposition
$$K_0 \, \mathrm{diag}(\varpi, 1) \, K_0 = \bigsqcup_{b \in \mathcal{O} / \mathfrak{p}} \begin{pmatrix} \varpi & b \\ 0 & 1 \end{pmatrix} K_0 \ \sqcup \ \begin{pmatrix} 1 & 0 \\ 0 & \varpi \end{pmatrix} K_0.$$
Both sides are the set of $g \in M_2(\mathcal{O})$ with $v(\det g) = 1$, by Lemma 3.1.2, part 3. Column reduction by $K_0$ brings such a $g$ to an upper triangular $\left(\begin{smallmatrix} \varpi^a & b \\ 0 & \varpi^d \end{smallmatrix}\right)$ with $a + d = 1$ and $b$ defined modulo $\varpi^a$, which gives the $q + 1$ cosets.

**Proposition 3.4.5 (the eigenvalue formula).** Let $\chi_1, \chi_2$ be unramified, $z_i = \chi_i(\varpi)$, and let $f_0 \in \chi_1 \times \chi_2$ be the $K_0$-fixed function with $f_0(1) = 1$. Then for each $f \in \mathcal{H}$,
$$\pi(f) f_0 = \mathcal{S} f(z_1, z_2) \, f_0.$$
In particular $\mathcal{S} T = q^{1/2} (X_1 + X_2)$ and $\mathcal{S} R = X_1 X_2$.

Lean: not stated yet.

*Proof.* The space $(\chi_1 \times \chi_2)^{K_0}$ is the line of $f_0$, so $\pi(f) f_0 = c f_0$ with $c = \int_G f(g) f_0(g) \, dg$. For $g = t n k$ the Haar measure is $dg = dt \, dn \, dk$, since $dt \, dn$ is a left Haar measure on $B$ and $G = B K_0$. With $f_0(t n k) = \chi_1(a) \chi_2(d) \delta^{1/2}(t)$ for $t = \mathrm{diag}(a, d)$, we get
$$c = \int_T \chi_1(a) \chi_2(d) \, \delta^{1/2}(t) \int_N f(t n) \, dn \, dt = \sum_{(a, b) \in \mathbb{Z}^2} z_1^a z_2^b \, \mathcal{S} f(\varpi^{(a, b)}) = \mathcal{S} f(z_1, z_2).$$
For $f = T$ and $t = \varpi^{(a, b)}$, the matrix $t \, n(x)$ is in the double coset of $T$ if and only if $a + b = 1$ and $t \, n(x) \in M_2(\mathcal{O})$. For $(1, 0)$ this means $x \in \mathfrak{p}^{-1}$, of measure $q$, and $\delta^{1/2}(t) = q^{-1/2}$. For $(0, 1)$ it means $x \in \mathcal{O}$, and $\delta^{1/2}(t) = q^{1/2}$. So $\mathcal{S} T = q^{1/2}(X_1 + X_2)$. For $R$, only $t = \varpi^{(1, 1)}$ and $x \in \mathcal{O}$ contribute. $\square$

### The Satake isomorphism

Let $\mathbb{C}[X_1^{\pm 1}, X_2^{\pm 1}]^{S_2}$ be the ring of the symmetric Laurent polynomials. For $\lambda$ dominant, let $m_\lambda$ be the monomial symmetric function $X_1^{m_1} X_2^{m_2} + X_1^{m_2} X_2^{m_1}$ if $m_1 > m_2$, and $X_1^{m_1} X_2^{m_1}$ if $m_1 = m_2$. These form a basis of the symmetric Laurent polynomials.

**Theorem 3.4.6 (Satake isomorphism for $GL_2$).** The Satake transform is an isomorphism of algebras
$$\mathcal{S} : \mathcal{H} \xrightarrow{\ \sim\ } \mathbb{C}[X_1^{\pm 1}, X_2^{\pm 1}]^{S_2}.$$
For $\lambda = (m_1, m_2)$ dominant, $\mathcal{S} c_\lambda = q^{(m_1 - m_2)/2} m_\lambda + \sum_\mu a_\mu m_\mu$, where $\mu = (\mu_1, \mu_2)$ runs over the dominant pairs with $\mu_1 + \mu_2 = m_1 + m_2$ and $\mu_1 < m_1$. In particular $\mathcal{H} = \mathbb{C}[T, R, R^{-1}]$, and $T$ and $R$ are algebraically independent.

Lean: not stated yet. The Lean definition `Langlands.satake` of the global Satake parameters, through `Langlands.satakePolynomial`, takes for $n = 2$ the roots of $X^2 - q^{-1/2} \lambda_1 X + \lambda_2$, where $\lambda_1$ and $\lambda_2$ are the eigenvalues of $T$ and $R$. By Proposition 3.4.5 these roots are $z_1, z_2$, so the Lean normalization agrees with ours.

*Proof.* First the triangular formula. Let $t = \varpi^{(a, b)}$. The determinant of $t \, n(x)$ has valuation $a + b$, and the least valuation of an entry is $\min(a, b, a + v(x))$. By Lemma 3.1.2, $\mathcal{S} c_\lambda(t) \ne 0$ forces $a + b = m_1 + m_2$ and $a, b \ge m_2$. For $(a, b) = (m_1, m_2)$ the condition is $v(x) \ge m_2 - m_1$, of measure $q^{m_1 - m_2}$, and $\delta^{1/2}(t) = q^{-(m_1 - m_2)/2}$. For $(m_2, m_1)$ it is $x \in \mathcal{O}$, and $\delta^{1/2}(t) = q^{(m_1 - m_2)/2}$. Both coefficients are $q^{(m_1 - m_2)/2}$.

Next, Proposition 3.4.5 and $\pi(f_1 * f_2) = \pi(f_1) \pi(f_2)$ give $\mathcal{S}(f_1 * f_2)(z) = \mathcal{S} f_1(z) \mathcal{S} f_2(z)$ for all $z \in (\mathbb{C}^\times)^2$, so $\mathcal{S}$ is multiplicative. If $z_1 / z_2 \notin \{q, q^{-1}\}$, then $\chi_1 \times \chi_2 \cong \chi_2 \times \chi_1$ (Proposition 3.2.3), and the isomorphism maps the $K_0$-fixed line to the $K_0$-fixed line, so $\mathcal{S} f(z_1, z_2) = \mathcal{S} f(z_2, z_1)$. This set is Zariski dense, so $\mathcal{S} f$ is symmetric.

Finally, by the triangular formula $\mathcal{S}$ maps the basis $c_\lambda$ to a family that is triangular with respect to the basis $m_\lambda$, for the order by $m_1 - m_2$ with $m_1 + m_2$ fixed, with nonzero diagonal entries. So $\mathcal{S}$ is bijective. Since $\mathcal{S} T = q^{1/2}(X_1 + X_2)$, $\mathcal{S} R = X_1 X_2$, and the symmetric Laurent polynomials are $\mathbb{C}[X_1 + X_2, X_1 X_2, (X_1 X_2)^{-1}]$, we get $\mathcal{H} = \mathbb{C}[T, R, R^{-1}]$. $\square$

**Corollary 3.4.7 (unramified representations).** An irreducible admissible representation $\pi$ is *unramified* if $\pi^{K_0} \ne 0$.
1. The map $\pi \mapsto$ (the character of $\mathcal{H}$ on the line $\pi^{K_0}$) is a bijection from the isomorphism classes of unramified irreducible representations to the characters of $\mathcal{H}$. By Theorem 3.4.6 the characters of $\mathcal{H}$ are the maps $f \mapsto \mathcal{S} f(z_1, z_2)$, for an unordered pair $\{z_1, z_2\}$ in $\mathbb{C}^\times$.
2. Each unramified irreducible $\pi$ is a subquotient of $\chi_1 \times \chi_2$ for unramified $\chi_i$ with $\chi_i(\varpi) = z_i$. It is $\pi(\chi_1, \chi_2)$ if $z_1 / z_2 \notin \{q, q^{-1}\}$, and it is $\eta \circ \det$ with $\eta$ unramified, $\{z_1, z_2\} = \{\eta(\varpi) q^{1/2}, \eta(\varpi) q^{-1/2}\}$, otherwise.
3. On $\pi^{K_0}$, the operator $T$ acts by $q^{1/2}(z_1 + z_2)$ and $R$ acts by $z_1 z_2 = \omega_\pi(\varpi)$. On $\eta \circ \det$, the operator $T$ acts by $(q + 1) \eta(\varpi)$.

Lean: not stated yet. The Lean project checks the last statement for the constant function $\eta = 1$ on the adelic group, in `Langlands.Fidelity.sqrt_mem_satake_constOne_two`: the eigenvalues are $q + 1$ and $1$, and $q^{1/2}$ is a Satake parameter.

*Proof.* Part 1 is Volume 6, Corollary 1.2.6. By Volume 6, Example 1.5.6, the irreducible unramified representations are the irreducible $\chi_1 \times \chi_2$ with $\chi_1, \chi_2$ unramified and the unramified $\eta \circ \det$. For the first, Proposition 3.4.5 gives the character $f \mapsto \mathcal{S} f(z_1, z_2)$. The function $\eta \circ \det$ is the vector $f_0$ of $\eta |\cdot|^{-1/2} \times \eta |\cdot|^{1/2}$, with $z_1 = \eta(\varpi) q^{1/2}$ and $z_2 = \eta(\varpi) q^{-1/2}$, and the other constituent $\eta \mathrm{St}$ has no $K_0$-fixed vector by Example 3.2.6. This gives part 2, and part 3 follows from Proposition 3.4.5. As a check, $\int_G T(g) \eta(\det g) \, dg = \eta(\varpi) \, \mathrm{vol}(K_0 \, \mathrm{diag}(\varpi, 1) \, K_0) = (q + 1) \eta(\varpi)$. $\square$

The pair $\{z_1, z_2\}$ is the *Satake parameter* of $\pi$, or the conjugacy class of $\mathrm{diag}(z_1, z_2)$ in the dual group $GL_2(\mathbb{C})$.

### Hecke series and the classical operators

**Proposition 3.4.8 (Hecke series).** For $m \ge 0$ let $T_{\varpi^m}$ be the characteristic function of the set of $g \in M_2(\mathcal{O})$ with $v(\det g) = m$. Then:
1. $T_{\varpi^m} = \sum_{0 \le j \le m/2} c_{(m - j, j)}$, and $\mathcal{S} T_{\varpi^m} = q^{m/2} h_m$, where $h_m = \sum_{a + b = m, \, a, b \ge 0} X_1^a X_2^b$.
2. In $\mathcal{H}[[Y]]$,
$$\sum_{m \ge 0} T_{\varpi^m} Y^m = (1 - T Y + q R Y^2)^{-1}.$$
Equivalently $T_{\varpi^{m+1}} = T * T_{\varpi^m} - q R * T_{\varpi^{m - 1}}$ for $m \ge 1$.
3. For $m \ge 2$, $c_{(m, 0)} = T_{\varpi^m} - R * T_{\varpi^{m - 2}}$, so $\mathcal{S} c_{(m, 0)} = q^{m/2} (h_m - q^{-1} X_1 X_2 h_{m - 2})$. For example $T * T = c_{(2, 0)} + (q + 1) R$.

Lean: not stated yet.

*Proof.* A matrix in $M_2(\mathcal{O})$ with $v(\det g) = m$ lies in $K_0 \varpi^{(m - j, j)} K_0$, where $j$ is the smallest valuation of its entries, and $0 \le j \le m / 2$. This gives the first formula of part 1. For the Satake transform, let $t = \varpi^{(a, b)}$. Then $t \, n(x) \in M_2(\mathcal{O})$ with $v(\det) = m$ if and only if $a + b = m$, $a, b \ge 0$ and $x \in \mathfrak{p}^{-a}$, a set of measure $q^a$. With $\delta^{1/2}(t) = q^{-(a - b)/2}$, the coefficient of $X_1^a X_2^b$ is $q^{a - (a - b)/2} = q^{(a + b)/2} = q^{m/2}$. For part 2, the identity $\sum_m h_m Y^m = (1 - X_1 Y)^{-1} (1 - X_2 Y)^{-1}$ gives
$$\sum_m \mathcal{S} T_{\varpi^m} Y^m = \frac{1}{(1 - q^{1/2} X_1 Y)(1 - q^{1/2} X_2 Y)} = \frac{1}{1 - q^{1/2}(X_1 + X_2) Y + q X_1 X_2 Y^2}.$$
By Proposition 3.4.5 the denominator is $\mathcal{S}(1 - T Y + q R Y^2)$, and $\mathcal{S}$ is injective. For part 3, the terms with $j \ge 1$ in part 1 are $c_{(m - j, j)} = R * c_{(m - 2 - (j - 1), j - 1)}$ by Lemma 3.4.2, and their sum is $R * T_{\varpi^{m - 2}}$. For $m = 2$, part 2 gives $T * T = T_{\varpi^2} + q R = c_{(2, 0)} + R + q R$. $\square$

Now compare with Volume 4. Let $f$ be a normalized eigenform of weight $k$ and character $\chi$ with $p \nmid N$, and $\pi_p$ the local component of its automorphic representation (Chapters 1 and 4). In the normalizations of Volume 0, Section 3.2, the unitary Satake parameters satisfy $\alpha_p + \beta_p = a_p p^{-(k - 1)/2}$ and $\alpha_p \beta_p = \chi(p)$, and they are the $z_1, z_2$ of $\pi_p$. So $T$ acts on the spherical vector by $q^{1/2}(z_1 + z_2) = p^{1 - k/2} a_p$, and $T_{\varpi^m}$ by $p^{m(1 - k/2)} a_{p^m}$. With $Y = p^{k/2 - 1 - s}$, part 2 of Proposition 3.4.8 becomes the classical $\sum_m a_{p^m} p^{-ms} = (1 - a_p p^{-s} + \chi(p) p^{k - 1 - 2s})^{-1}$ of Volume 4.
$$q^{1/2}(z_1 + z_2) = p^{1/2} \cdot a_p \, p^{-(k - 1)/2} = p^{1 - k/2} a_p.$$

**Example 3.4.9 (the discriminant at $p = 2$).** Let $f = \Delta$, with $\tau(2) = -24$ and $\tau(4) = -1472$. The local $T$ eigenvalue at $2$ is $2^{-5} \cdot (-24) = -3/4$, so $z_1 + z_2 = -24 / 2^{11/2} \approx -0.5303$ and $z_1 z_2 = 1$. The polynomial $X^2 + 0.5303 X + 1$ has negative discriminant, so $|z_1| = |z_2| = 1$, as Deligne's theorem says. As a check of Proposition 3.4.8, the eigenvalue of $T_{\varpi^2}$ is $2((z_1 + z_2)^2 - z_1 z_2) = 2(576 / 2048 - 1) = -1.4375$, and the classical side gives $2^{-10} \tau(4) = -1.4375$.

**Remark 3.4.10 (the Ramanujan bound).** For a unitary unramified $\pi$, Remark 3.2.7 gives either $|z_1| = |z_2| = 1$, so $|q^{1/2}(z_1 + z_2)| \le 2 q^{1/2}$, or the complementary series, with $|z_i| = q^{\pm s}$ and $0 < s < 1/2$. The Ramanujan conjecture for $\pi_p$ is the first case. For holomorphic newforms it is Deligne's bound $|a_p| \le 2 p^{(k - 1)/2}$ (Volume 4, Chapter 4). In Lean the conjecture for $GL_n$ is `Langlands.RamanujanGL`.
