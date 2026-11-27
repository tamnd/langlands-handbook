---
title: Hecke operators and the adelic dictionary
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Hecke operators and the adelic dictionary

The Hecke operator $T_p$ of Volume 4 is a sum over $p + 1$ matrices of determinant $p$. On the adelic side it becomes a convolution operator at the single place $p$. In this section we prove this and collect the results of the chapter in a dictionary. We follow [Bum97], Sections 3.6 and 4.6, and [Gel75], Chapter 3. Let $p$ be a prime, $G_p = GL_2(\mathbb{Q}_p)$ and $K_p = GL_2(\mathbb{Z}_p)$. Let $dg$ be the Haar measure on $G_p$ with $\mathrm{vol}(K_p) = 1$. The group $G_p$ is unimodular, so $dg$ is also right invariant and invariant under $g \mapsto g^{-1}$.

### The spherical Hecke algebra

**Definition 1.6.1 (the spherical Hecke algebra).** The *spherical Hecke algebra* $\mathcal{H}_p$ is the space of the functions $F : G_p \to \mathbb{C}$ with compact support and $F(k_1gk_2) = F(g)$ for $k_1, k_2 \in K_p$, with the convolution
$$(F_1 * F_2)(g) = \int_{G_p}F_1(h)F_2(h^{-1}g)\,dh.$$

A function in $\mathcal{H}_p$ is a finite linear combination of characteristic functions of double cosets $K_p g K_p$, since such a double coset is open and its support is compact. The unit of $\mathcal{H}_p$ is $1_{K_p}$.

**Lemma 1.6.2 (the Cartan decomposition).** The group $G_p$ is the disjoint union of the double cosets $K_p\,\mathrm{diag}(p^a, p^b)\,K_p$ with integers $a \ge b$.

Lean: not formalized

*Proof.* Let $g \in G_p$. Multiply $g$ by a power of $p$ to get a matrix with entries in $\mathbb{Z}_p$. Choose an entry of minimal valuation $c$ and move it to the upper left corner by permutation matrices, which are in $K_p$. Elementary row and column operations with coefficients in $\mathbb{Z}_p$ clear the rest of the first row and column, because the corner entry divides the other entries. The remaining entry has valuation at least $c$. Multiplication by a diagonal matrix of units gives $\mathrm{diag}(p^b, p^a)$ with $a \ge b = c$, and the Weyl element $\begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} \in K_p$ exchanges the two entries. At the end we undo the scaling by the power of $p$. For the uniqueness, $b$ is the minimal valuation of the entries of $g$, and this number does not change under left and right multiplication by $K_p$. Also $a + b$ is the valuation of $\det g$. $\square$

**Proposition 1.6.3 (commutativity).** The algebra $\mathcal{H}_p$ is commutative.

Lean: not formalized

*Proof.* We use the trick of Gelfand. Let $F^t(g) = F(g^t)$. The transpose maps $K_p$ to $K_p$ and fixes the diagonal matrices, so it maps each double coset of Lemma 1.6.2 to itself, and $F^t = F$ for $F \in \mathcal{H}_p$. The map $g \mapsto (g^t)^{-1}$ is an automorphism of $G_p$ that preserves $K_p$, so it preserves $dg$, and so does $g \mapsto g^t$. Now substitute $h = u^t$:
$$(F_1 * F_2)(g^t) = \int F_1(u^t)F_2((gu^{-1})^t)\,du = \int F_1^t(u)F_2^t(gu^{-1})\,du = (F_2^t * F_1^t)(g),$$
where the last step is the substitution $v = gu^{-1}$. So $F_1 * F_2 = (F_1 * F_2)^t = F_2^t * F_1^t = F_2 * F_1$. $\square$

Lemma 1.6.2 shows that $\mathcal{H}_p$ has the basis of the functions $1_{K_p\mathrm{diag}(p^a, p^b)K_p}$ with $a \ge b$. Chapter 3 proves the Satake isomorphism, which identifies $\mathcal{H}_p$ with the algebra of symmetric Laurent polynomials in two variables. Here we need only two elements.

**Definition 1.6.4 (the operators $T_p$ and $R_p$).** Let $T_p = 1_{K_p\mathrm{diag}(p, 1)K_p}$ and $R_p = 1_{pK_p}$ in $\mathcal{H}_p$. For $F \in \mathcal{H}_p$ and a function $\phi$ on $GL_2(\mathbb{A})$ that is right invariant under $\iota_p(K_p)$, let
$$(F \cdot \phi)(g) = \int_{G_p}F(h)\,\phi(g\,\iota_p(h))\,dh.$$

The integral is a finite sum: if $K_p g K_p = \bigsqcup_i h_i K_p$, then $(1_{K_pgK_p}\cdot\phi)(g') = \sum_i\phi(g'\iota_p(h_i))$. So $R_p\cdot\phi(g) = \phi(g\,\iota_p(p))$. The map $F \mapsto (\phi \mapsto F\cdot\phi)$ respects the products: by Fubini and the substitution $u = hh'$,
$$(F_1\cdot(F_2\cdot\phi))(g) = \int\int F_1(h)F_2(h')\phi(g\,\iota_p(hh'))\,dh'\,dh = \int\int F_1(h)F_2(h^{-1}u)\phi(g\,\iota_p(u))\,du\,dh = ((F_1 * F_2)\cdot\phi)(g).$$
In the following we write $T_p\phi$ for $T_p\cdot\phi$.

**Lemma 1.6.5 (the cosets of $T_p$).** We have
$$K_p\,\mathrm{diag}(p, 1)\,K_p = \bigsqcup_{j = 0}^{p - 1}\begin{pmatrix} p & j \\ 0 & 1 \end{pmatrix}K_p \ \sqcup\ \begin{pmatrix} 1 & 0 \\ 0 & p \end{pmatrix}K_p.$$
In particular $\mathrm{vol}(K_p\,\mathrm{diag}(p, 1)\,K_p) = p + 1$.

Lean: `Langlands.heckeCosetGL` gives these representatives, for $n = 2$ and $i = 1$, with a uniformizer in place of $p$; the decomposition is not proved

*Proof.* By Lemma 1.6.2 the double coset is the set of the matrices $g \in M_2(\mathbb{Z}_p)$ with $v_p(\det g) = 1$: such a matrix lies in $K_p\,\mathrm{diag}(p^a, p^b)\,K_p$ with $b \ge 0$ and $a + b = 1$, so $(a, b) = (1, 0)$. Let $g$ be such a matrix. Right multiplication by $K_p$ performs column operations. They bring the lower row of $g$ to the form $(0, p^m)$, where $p^m$ is the greatest common divisor of its entries, and they make the upper left entry a power of $p$. So $gk = \begin{pmatrix} p^{1-m} & \beta \\ 0 & p^m \end{pmatrix}$ for some $k \in K_p$, with $m \in \{0, 1\}$. If $m = 0$, then $\begin{pmatrix} p & \beta \\ 0 & 1 \end{pmatrix}n(t) = \begin{pmatrix} p & \beta + pt \\ 0 & 1 \end{pmatrix}$, so only $j = \beta \bmod p$ matters. If $m = 1$, then right multiplication by $n(-\beta)$ gives $\mathrm{diag}(1, p)$. The cosets are distinct, because $\begin{pmatrix} p & j \\ 0 & 1 \end{pmatrix}^{-1}\begin{pmatrix} p & j' \\ 0 & 1 \end{pmatrix} = n((j' - j)/p)$ is in $K_p$ only for $j = j'$, and $\begin{pmatrix} p & j \\ 0 & 1 \end{pmatrix}^{-1}\mathrm{diag}(1, p)$ has the entry $p^{-1}$. $\square$

For the representatives $\beta$ of the lemma, the matrices $p\beta^{-1}$ are $\begin{pmatrix} 1 & -j \\ 0 & p \end{pmatrix}$ and $\mathrm{diag}(p, 1)$. Up to the sign of $j$, these are the matrices of the formula of Volume 4, Proposition 1.5.7, and the proof of Theorem 1.6.8 explains the inversion. Example 1.1.8 found the coset of $\begin{pmatrix} p & 1 \\ 0 & 1 \end{pmatrix}$.

**Lemma 1.6.6 (the operators preserve the spaces).** Let $p \nmid N$. Then $T_p$ and $R_p$ map $\mathcal{A}_k(N, \chi)$ to itself and $\mathcal{A}^0_k(N, \chi)$ to itself, and they commute.

Lean: not formalized

*Proof.* Since $p \nmid N$, the $p$-component of $K_0(N)$ is $K_p$, and $\lambda$ is trivial on $\iota_p(K_p)$: the lower right entry of $\iota_p(k_p)$ is 1 at the primes dividing $N$. So $\phi \in \mathcal{A}_k(N, \chi)$ is right invariant under $\iota_p(K_p)$, and $F\cdot\phi$ is defined. Conditions 1, 3, 4 and 5 of Definition 1.5.1 hold for $F\cdot\phi$, because left translations and right translations at the infinite place commute with right translations at $p$. For condition 2 write $k \in K_0(N)$ as $k = k^{(p)}\iota_p(k_p)$. The element $k^{(p)}$ commutes with $\iota_p(h)$, and the substitution $h \mapsto k_p^{-1}h$ uses $F(k_p^{-1}h) = F(h)$. So $(F\cdot\phi)(gk) = \lambda(k^{(p)})(F\cdot\phi)(g) = \lambda(k)(F\cdot\phi)(g)$. For condition 6, the ultrametric inequality at $p$ gives $\|g\,\iota_p(h)\| \le \|g\|\,\|h\|_p$, and $\|h\|_p \le p^{a - b}$ on the support. The constant term of $F\cdot\phi$ is $F\cdot\phi_N$ by part 3 of Lemma 1.4.12, so cuspidality is preserved. The operators commute by Proposition 1.6.3. $\square$

**Example 1.6.7 (the prime 2).** For $p = 2$ the three cosets are those of $\mathrm{diag}(2, 1)$, $\begin{pmatrix} 2 & 1 \\ 0 & 1 \end{pmatrix}$ and $\mathrm{diag}(1, 2)$. So for $\phi$ right invariant under $\iota_2(K_2)$,
$$(T_2\phi)(g) = \phi(g\,\iota_2(\mathrm{diag}(2, 1))) + \phi\Big(g\,\iota_2\begin{pmatrix} 2 & 1 \\ 0 & 1 \end{pmatrix}\Big) + \phi(g\,\iota_2(\mathrm{diag}(1, 2))).$$
The values of $\phi_\Delta$ at the first and the last element for $g = 1$ are in Example 1.3.9.

### The comparison

**Theorem 1.6.8 ($T_p$ and $R_p$ on $\phi_f$).** Let $f \in M_k(N, \chi)$ and $p \nmid N$. Then
$$T_p\phi_f = p^{1 - k/2}\,\phi_{T_pf}, \qquad R_p\phi_f = \chi(p)\,\phi_f,$$
where $T_pf$ is the Hecke operator of Volume 4, Definition 1.5.6.

Lean: not formalized

*Proof.* The second claim is part 4 of Proposition 1.3.6 and part 2 of Lemma 1.3.2: $\phi_f(g\,\iota_p(p)) = \omega_p(p)\phi_f(g) = \chi(p)\phi_f(g)$. For the first claim, both sides are in $\mathcal{A}_k(N, \chi)$ by Lemma 1.6.6 and Section 1.5. By Theorem 1.2.5 and conditions 1 and 2 it is enough to compare them at the elements $\iota_\infty(g_\infty)$ with $g_\infty \in GL_2^+(\mathbb{R})$. Let $\beta$ be one of the representatives of Lemma 1.6.5. The rational matrix $\beta$ is $\iota_\infty(\beta)\,\iota_p(\beta)\,k'$, where $k'$ has the component $\beta$ at the primes $q \ne p$ and 1 at $p$. Since $\det\beta = p$ is a unit at $q \ne p$ and $\beta$ is upper triangular, $k'^{-1} \in K_0(N)$. Hence
$$\iota_\infty(g_\infty)\,\iota_p(\beta) = \beta\,\iota_\infty(\beta^{-1}g_\infty)\,k'^{-1}, \qquad \phi_f(\iota_\infty(g_\infty)\iota_p(\beta)) = \lambda(k'^{-1})\,((f\|_k\beta^{-1})\|_k g_\infty)(i),$$
where $\beta^{-1}g_\infty$ has positive determinant. For $\beta = \begin{pmatrix} p & j \\ 0 & 1 \end{pmatrix}$ the lower right entry of $k'^{-1}$ is 1 at every prime, so $\lambda(k'^{-1}) = 1$, and $(f\|_k\beta^{-1})(\tau) = p^{-k/2}f((\tau - j)/p)$. For $\beta = \mathrm{diag}(1, p)$ the lower right entry of $k'^{-1}$ is $p^{-1}$ at $q \ne p$ and 1 at $p$, which is $p^{-1}$ modulo $N$. So $\lambda(k'^{-1}) = \chi(p^{-1})^{-1} = \chi(p)$, and $(f\|_k\beta^{-1})(\tau) = p^{-k/2}p^kf(p\tau)$. The sum over the $p + 1$ representatives is
$$(T_p\phi_f)(\iota_\infty(g_\infty)) = (F\|_k g_\infty)(i), \qquad F(\tau) = p^{-k/2}\sum_{j = 0}^{p-1}f\Big(\frac{\tau + j}{p}\Big) + \chi(p)\,p^{k/2}f(p\tau),$$
where we replaced $j$ by $-j$ and used $f(\tau + 1) = f(\tau)$. By Volume 4, Proposition 1.5.7, with $\langle p\rangle f = \chi(p)f$ and the computation in the proof of Volume 4, Theorem 1.5.8,
$$(T_pf)(\tau) = \frac{1}{p}\sum_{j = 0}^{p-1}f\Big(\frac{\tau + j}{p}\Big) + \chi(p)\,p^{k-1}f(p\tau).$$
So $F = p^{1 - k/2}T_pf$, and the right side is $p^{1-k/2}\phi_{T_pf}(\iota_\infty(g_\infty))$. $\square$

The factor $p^{1 - k/2}$ comes from the two slash operators: $|_k$ has the factor $\det^{k-1}$ and $\|_k$ has $\det^{k/2}$. With it the eigenvalues of $T_p$ on the adelic side are normalized as in Volume 0, see Remark 1.6.13.

For $p \mid N$ the function $\phi_f$ is not right invariant under $\iota_p(K_p)$. The operator $U_p$ of Volume 4 corresponds to a double coset of the $p$-component $K_0(N)_p$ of $K_0(N)$.

**Proposition 1.6.9 (the operator $U_p$).** Let $p \mid N$ with $e = v_p(N)$, and let $K_0(N)_p$ be the group of the matrices in $K_p$ with lower left entry in $p^e\mathbb{Z}_p$. Then $K_0(N)_p\,\mathrm{diag}(p, 1)\,K_0(N)_p = \bigsqcup_{j = 0}^{p-1}\begin{pmatrix} p & j \\ 0 & 1 \end{pmatrix}K_0(N)_p$. Let
$$(U_p\phi)(g) = \sum_{j = 0}^{p-1}\phi\Big(g\,\iota_p\begin{pmatrix} p & j \\ 0 & 1 \end{pmatrix}\Big).$$
Then $U_p$ maps $\mathcal{A}_k(N, \chi)$ to itself, and $U_p\phi_f = p^{1 - k/2}\phi_{U_pf}$ for $f \in M_k(N, \chi)$.

Lean: not formalized

*Proof.* Let $k = \begin{pmatrix} a & b \\ c & d \end{pmatrix} \in K_0(N)_p$. Then $d \in \mathbb{Z}_p^\times$, since $c \in p\mathbb{Z}_p$. Choose $j$ with $j \equiv bd^{-1} \bmod p$. Then
$$\begin{pmatrix} p & j \\ 0 & 1 \end{pmatrix}^{-1}k\,\mathrm{diag}(p, 1) = \begin{pmatrix} a - jc & (b - jd)/p \\ pc & d \end{pmatrix} \in K_0(N)_p.$$
This proves the decomposition, and the cosets are distinct as in Lemma 1.6.5. It also shows that the new element of $K_0(N)_p$ has the same lower right entry $d$. Now let $k_0 \in K_0(N)$. Its $p$-component permutes the cosets by left multiplication: $k_{0,p}\begin{pmatrix} p & j \\ 0 & 1 \end{pmatrix} = k_{0,p}\,n(j)\,\mathrm{diag}(p, 1) = \begin{pmatrix} p & j' \\ 0 & 1 \end{pmatrix}k''$, and the lower right entry of $k''$ is that of $k_{0,p}n(j)$, which is $cj + d \equiv d \bmod p^e$. So $\lambda(k'') = \lambda(k_{0,p})$, where we view $k''$ and $k_{0,p}$ in $K_0(N)$ through $\iota_p$. This gives $(U_p\phi)(gk_0) = \lambda(k_0)(U_p\phi)(g)$. The other conditions of Definition 1.5.1 follow as in Lemma 1.6.6. The comparison with $U_pf = \sum_j f|_k\begin{pmatrix} 1 & j \\ 0 & p \end{pmatrix}$ is the computation of the terms $\beta = \begin{pmatrix} p & j \\ 0 & 1 \end{pmatrix}$ in the proof of Theorem 1.6.8. The element $k'^{-1}$ there is upper triangular with lower right entry 1, so it is in $K_0(N)$ with $\lambda(k'^{-1}) = 1$ also at the primes dividing $N$. $\square$

**Corollary 1.6.10 (eigenforms).** Let $f \in M_k(N, \chi)$ be nonzero, and let $p \nmid N$. Then $f$ is an eigenvector of $T_p$ with eigenvalue $a_p$ if and only if $\phi_f$ is an eigenvector of $T_p$ with eigenvalue $p^{1 - k/2}a_p$. If $f$ is a normalized eigenform, then $a_p$ is the $p$-th coefficient of $f$, and $\phi_f$ is an eigenvector of $T_p$ and $R_p$ with the eigenvalues $p^{1 - k/2}a_p(f)$ and $\chi(p)$. The same holds for $U_p$ with $p \mid N$.

Lean: not formalized

*Proof.* The map $f \mapsto \phi_f$ is linear and injective by Corollary 1.5.3, and Theorem 1.6.8 and Proposition 1.6.9 give the intertwining. For a normalized eigenform the eigenvalue of $T_p$ is $a_1(T_pf) = a_p(f)$ by Volume 4, Theorem 1.5.8. $\square$

**Example 1.6.11 (eigenvalues).** For $\Delta$ and $p = 2$, $T_2\phi_\Delta = 2^{-5}\tau(2)\phi_\Delta = -\frac{3}{4}\phi_\Delta$, since $\tau(2) = -24$. At $g = 1$, Example 1.6.7 and the computation in the proof of Theorem 1.6.8 turn this into the classical identity
$$2^{-6}\left(\Delta(i/2) + \Delta((i + 1)/2)\right) + 2^6\Delta(2i) = -\tfrac{3}{4}\Delta(i).$$
For the normalized Eisenstein series $E_k$ of level 1, Volume 4, Theorem 1.5.8 gives $T_pE_k = (1 + p^{k-1})E_k$, so $T_p\phi_{E_k} = (p^{1 - k/2} + p^{k/2})\phi_{E_k}$. For the newform $f_{11} = q\prod_{n \ge 1}(1 - q^n)^2(1 - q^{11n})^2$ of weight 2 and level 11, $a_2 = -2$, so $T_2\phi_{f_{11}} = -2\phi_{f_{11}}$: in weight 2 the factor $p^{1 - k/2}$ is 1.

### The dictionary

**Theorem 1.6.12 (the adelic dictionary).** Let $N \ge 1$, let $\chi$ be a Dirichlet character modulo $N$ and let $k$ be an integer with $\chi(-1) = (-1)^k$. The map $f \mapsto \phi_f$ of Proposition 1.3.5 has these properties.
1. It is an isomorphism from $M_k(N, \chi)$ onto the space $\mathcal{A}_k(N, \chi)$ of Definition 1.5.1, and it maps $S_k(N, \chi)$ onto $\mathcal{A}^0_k(N, \chi)$.
2. The level $\Gamma_0(N)$ and the character $\chi$ correspond to the character $\lambda$ of $K_0(N)$, and the diamond operators to the right translations by $K_0(N)/K_1(N)$. The nebentypus becomes the central character $\omega$, with $\omega_\infty = \mathrm{sgn}^k$ and $\omega_p(p) = \chi(p)$ for $p \nmid N$.
3. The weight $k$ corresponds to the character $\kappa_\theta \mapsto e^{ik\theta}$ of $SO(2)$, the holomorphy to $L\phi = 0$, and $\phi_f$ has the Casimir eigenvalue $\frac{k}{2}(1 - \frac{k}{2})$.
4. The condition at the cusps corresponds to moderate growth, and the vanishing at the cusps to the vanishing of the constant term.
5. For $p \nmid N$, $\phi_{T_pf} = p^{k/2 - 1}T_p\phi_f$ and $\phi_{\langle p\rangle f} = R_p\phi_f$. For $p \mid N$, $\phi_{U_pf} = p^{k/2 - 1}U_p\phi_f$.

Lean: not formalized

*Proof.* Part 1 is Corollary 1.5.3 and Theorem 1.4.14. Part 2 is Propositions 1.3.5 and 1.3.6, Lemma 1.3.2 and Remark 1.5.6. Part 3 is Theorem 1.4.6 and the holomorphy step in the proof of Theorem 1.5.2. Part 4 is Proposition 1.4.10, the cusp step in the proof of Theorem 1.5.2, and Theorem 1.4.14. Part 5 is Theorem 1.6.8 and Proposition 1.6.9, with $\langle p\rangle f = \chi(p)f$. $\square$

**Remark 1.6.13 (Satake parameters and $L$-functions).** Let $f$ be a normalized eigenform in $S_k(N, \chi)$ and $p \nmid N$. The eigenvalues of $T_p$ and $R_p$ on $\phi_f$ are $\lambda_1 = p^{1 - k/2}a_p$ and $\lambda_2 = \chi(p)$. The Satake parameters $\{\alpha, \beta\}$ of $\phi_f$ at $p$ are the roots of $X^2 - p^{-1/2}\lambda_1X + \lambda_2$. So
$$\alpha + \beta = p^{(1 - k)/2}a_p, \qquad \alpha\beta = \chi(p).$$
Classically $1 - a_pp^{-s} + \chi(p)p^{k - 1 - 2s} = (1 - \alpha'p^{-s})(1 - \beta'p^{-s})$ with $\alpha' = p^{(k-1)/2}\alpha$ and $\beta' = p^{(k-1)/2}\beta$. Hence the local factor $(1 - \alpha p^{-s})^{-1}(1 - \beta p^{-s})^{-1}$ of $L(\pi_f, s)$ is the local factor of $L(f, s + \frac{k-1}{2})$, which is the normalization $L(f, s) = L(\pi_f, s - \frac{k-1}{2})$ of Volume 0, Chapter 3. Deligne's theorem gives $|\alpha| = |\beta| = 1$, which is the Ramanujan conjecture for $\phi_f$ at $p$, see Chapter 4. For $\Delta$ and $p = 2$, $\alpha + \beta = 2^{-11/2}\tau(2) = -3/(4\sqrt{2})$ and $\alpha\beta = 1$. For $f_{11}$ and $p = 2$, $\alpha + \beta = -\sqrt{2}$ and $\alpha\beta = 1$, so $\{\alpha, \beta\} = \{e^{3\pi i/4}, e^{-3\pi i/4}\}$. For $E_k$ the parameters are $p^{\pm(k-1)/2}$, which are not unitary: $E_k$ is not a cusp form, and Chapter 2 identifies it with an induced representation. The Satake isomorphism of Chapter 3 explains why the roots of this polynomial are the right parameters.

**Remark 1.6.14 (the Hecke operators in the Lean project).** The Lean project defines `Langlands.adelicHeckeOperator v i` for $GL_n$ over a number field, as the sum over explicit representatives `Langlands.heckeCosetGL` of $GL_n(\mathcal{O}_v)\,\mathrm{diag}(\varpi_v^{(i)}, 1^{(n-i)})\,GL_n(\mathcal{O}_v)/GL_n(\mathcal{O}_v)$. For $n = 2$, $K = \mathbb{Q}$ and the place $p$, the operator with $i = 1$ is $T_p$ of Definition 1.6.4 and the operator with $i = 2$ is $R_p$, if the uniformizer $\varpi_v$ is $p$ times a unit. The predicate `Langlands.IsHeckeEigenAt φ v λ` says that $\phi$ is spherical at $v$ with these eigenvalues, and `Langlands.IsHeckeEigenform` asks this at almost all places. The Satake parameters `Langlands.satake` are the roots of `Langlands.satakePolynomial`, which for $n = 2$ is the polynomial $X^2 - p^{-1/2}\lambda_1X + \lambda_2$ of Remark 1.6.13. The project does not prove Theorem 1.6.8.
