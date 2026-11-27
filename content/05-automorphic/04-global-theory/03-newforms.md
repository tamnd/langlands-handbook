---
title: Newforms and cuspidal representations
nodes: []
sources: [JL70, BH06]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Newforms and cuspidal representations

This section proves that the newforms of Volume 4 are the same objects as the cuspidal automorphic representations whose component at infinity is a holomorphic discrete series. The level of the newform is the conductor of the representation, and the theory of Atkin and Lehner becomes the local theory of newforms of Casselman. We treat the trivial character and even weight $k \ge 2$. The case of a nontrivial character is the same, with $K_1(N)$ in place of $K_0(N)$.

### Local newforms and the discrete series

For a prime $p$ and $c \ge 0$ let
$$K_0(p^c) = \left\{\begin{pmatrix} a & b \\ c' & d \end{pmatrix} \in K_p : c' \equiv 0 \bmod p^c\right\}.$$
So $K_0(1) = K_p$, and $K_0(N) = \prod_p K_0(p^{v_p(N)})$ is the adelic group of Chapter 1, with $GL_2(\mathbb{Q}) \cap GL_2(\mathbb{R})^+K_0(N) = \Gamma_0(N)$ up to the centre.

**Theorem 4.3.1 (Casselman).** Let $\pi_p$ be an irreducible admissible infinite-dimensional representation of $G_p$ with trivial central character. There is a least integer $c(\pi_p) \ge 0$ with $\pi_p^{K_0(p^{c(\pi_p)})} \ne 0$, and for each $m \ge 0$
$$\dim \pi_p^{K_0(p^m)} = \max(0, m - c(\pi_p) + 1).$$

Lean: not formalized

The integer $c(\pi_p)$ is the *conductor exponent* of $\pi_p$, and a nonzero vector of $\pi_p^{K_0(p^{c(\pi_p)})}$ is a *local newform*. Chapter 3 proves this theorem. For an unramified principal series $c = 0$, and for every other representation $c \ge 1$. For $\chi_1 \times \chi_2$ the conductor exponent is $c(\chi_1) + c(\chi_2)$. For $\mu\mathrm{St}$ it is $1$ if $\mu$ is unramified and $2c(\mu)$ if $\mu$ is ramified. For a supercuspidal representation it is at least 2. These values are in Chapter 3 and in [BH06], Chapter 6. For a cuspidal automorphic representation $\pi$ with trivial central character the *conductor* is $N(\pi) = \prod_p p^{c(\pi_p)}$. It is an integer by Proposition 4.2.3, part 3.

At infinity we use the discrete series of Chapter 2. For an integer $k \ge 2$ the $(\mathfrak{g}, K_\infty)$-module $D_k$ is the unique irreducible module in which $SO(2)$ acts with the weights $\pm k, \pm(k + 2), \pm(k + 4), \ldots$, each with multiplicity one, and with central character $\mathrm{sgn}^k$. The vectors of weight $k$ form a line, and they are killed by the lowering operator $L$. Conversely, a nonzero vector of weight $k$ killed by $L$ in an irreducible unitary module with central character $\mathrm{sgn}^k$ generates $D_k$. Chapter 2 proves these facts.

### The correspondence

Let $f \in S_k(\Gamma_0(N))$ and let $\phi_f$ be the cusp form of Chapter 1, defined by $\phi_f(\gamma g_\infty k_f) = (f|_kg_\infty)(i)$. The dictionary of Chapter 1 says that $f \mapsto \phi_f$ is an isomorphism of $S_k(\Gamma_0(N))$ onto the space of $\phi \in \mathcal{A}_0(1)$ that are right invariant under $K_0(N)$, of weight $k$ under $SO(2)$ and killed by $L$. It is compatible with the operators $T_p$ for $p \nmid N$ by Remark 4.2.7.

**Lemma 4.3.2 (old forms are translates).** Let $g \in S_k(\Gamma_0(M))$ and $d \ge 1$, and let $\delta_d \in GL_2(\mathbb{A}_f)$ be the image of $\mathrm{diag}(d, 1)$ in the finite adeles. Then $\phi_{g(d\tau)} = d^{-k/2}\pi(\delta_d^{-1})\phi_g$, where $\pi$ is right translation.

Lean: not formalized

*Proof.* We have $g(d\tau) = d^{-k/2}(g|_k\alpha)(\tau)$ with $\alpha = \mathrm{diag}(d, 1) \in GL_2(\mathbb{Q})^+$. For $g_\infty \in GL_2(\mathbb{R})^+$, the left invariance of $\phi_g$ under $\alpha^{-1} \in GL_2(\mathbb{Q})$ gives
$$\phi_{g|_k\alpha}(g_\infty) = (g|_k\alpha g_\infty)(i) = \phi_g(\alpha g_\infty, 1) = \phi_g(g_\infty, \alpha^{-1}) = (\pi(\delta_d^{-1})\phi_g)(g_\infty, 1).$$
Both sides are left invariant under $GL_2(\mathbb{Q})$ and right invariant under the group $K_0(Md)$, which contains $\delta_d^{-1}K_0(M)\delta_d \cap K_0(M)$. By the decomposition $GL_2(\mathbb{A}) = GL_2(\mathbb{Q})GL_2(\mathbb{R})^+K_0(Md)$ of Chapter 1 they are equal. $\square$

**Theorem 4.3.3 (newforms and cuspidal representations).** Let $k \ge 2$ be even and $N \ge 1$. For a newform $f$ of weight $k$ and level $N$, the function $\phi_f$ lies in a single irreducible subspace $V_{\pi_f}$ of $\mathcal{A}_0(1)$. The map $f \mapsto \pi_f$ is a bijection from the set of newforms of weight $k$ and level $N$ onto the set of cuspidal automorphic representations $\pi$ with trivial central character, with $\pi_\infty \cong D_k$ and with conductor $N(\pi) = N$. For $p \nmid N$ the component $\pi_{f,p}$ is the unramified principal series with Satake parameters the roots of $X^2 - a_p(f)p^{-(k-1)/2}X + 1$.

Lean: not formalized

*Proof.* We use Theorem 2.1.8 of Volume 4 for $\Gamma_0(N)$. By its part 4, $S_k(\Gamma_0(N))$ is the direct sum of the lines spanned by the forms $g(d\tau)$, where $g$ runs over the newforms of the levels $M \mid N$ and $d$ over the divisors of $N/M$. The form $g(d\tau)$ is an eigenvector of $T_p$ with eigenvalue $a_p(g)$ for $p \nmid N$, and by part 3 (strong multiplicity one for newforms) two different newforms $g$ have different eigenvalues for infinitely many $p$. So for each newform $g$ of level $M \mid N$, the joint eigenspace of the operators $T_p$, $p \nmid N$, with the eigenvalues $a_p(g)$ is the span of the forms $g(d\tau)$ with $d \mid N/M$. For a newform $f$ of level $N$ it is the line of $f$.

*Step 1: $\phi_f$ lies in one $V_\pi$.* By Theorem 4.2.2 write $\phi_f = \sum_\pi \phi_\pi$, a finite sum with $\phi_\pi \in V_\pi$ and the $\pi$ distinct. Each $\phi_\pi$ is the image of $\phi_f$ under a projection that commutes with the action of $(\mathfrak{g}, K_\infty) \times GL_2(\mathbb{A}_f)$. So $\phi_\pi$ is invariant under $K_0(N)$, of weight $k$ and killed by $L$, and $\phi_\pi = \phi_{f_\pi}$ for some $f_\pi \in S_k(\Gamma_0(N))$. For $p \nmid N$ the projection commutes with $\pi(T_p)$, so $T_pf_\pi = a_p(f)f_\pi$ by Remark 4.2.7. By the description above, $f_\pi = c_\pi f$ for a scalar $c_\pi$. If two components were nonzero, then $\phi_f$ would lie in $V_\pi \cap V_{\pi'} = 0$ for $\pi \ne \pi'$. So $\phi_f \in V_\pi$ for exactly one $\pi$, which we call $\pi_f$.

*Step 2: the local components.* The function $\phi_f$ is a vector of weight $k$ killed by $L$ in $\pi_f$, and $\pi_{f,\infty}$ is unitary with central character $\mathrm{sgn}^k$ (the element $-1 \in Z(\mathbb{R})$ acts on $\phi_f$ by $(-1)^k = 1$). So $\pi_{f,\infty} \cong D_k$. For $p \nmid N$ the vector $\phi_f$ is fixed by $K_p$, so $\pi_{f,p}$ is unramified, and its Satake parameters are given by Remark 4.2.7.

*Step 3: the conductor is $N$.* Since $\phi_f$ is fixed by $K_0(p^{v_p(N)})$ at each $p$, we have $c(\pi_{f,p}) \le v_p(N)$, so $M = N(\pi_f)$ divides $N$. By Theorem 4.1.6 and Theorem 4.3.1, the space of vectors in $V_{\pi_f}$ that are fixed by $K_0(N)$ and have weight $k$ has dimension
$$1 \cdot \prod_{p \mid N}(v_p(N) - c(\pi_{f,p}) + 1) = d(N/M),$$
the number of divisors of $N/M$. By the dictionary these vectors are $\phi_h$ for $h$ in a subspace of $S_k(\Gamma_0(N))$ of dimension $d(N/M)$. Each such $h$ satisfies $T_ph = a_p(f)h$ for $p \nmid N$, since $\mathcal{H}(G_p, K_p)$ acts on $V_{\pi_f}^{K_p}$ by the character of $\pi_{f,p}$. This eigenspace is the line of $f$. So $d(N/M) = 1$ and $M = N$.

*Step 4: injectivity.* If $\pi_f = \pi_{f'}$ for newforms $f, f'$ of level $N$, then $a_p(f) = a_p(f')$ for all $p \nmid N$ by Step 2, and $f = f'$ by part 3 of Theorem 2.1.8 of Volume 4.

*Step 5: surjectivity.* Let $\pi$ be cuspidal with trivial central character, $\pi_\infty \cong D_k$ and $N(\pi) = N$. By Theorem 4.3.1 the space of vectors of $V_\pi$ that are fixed by $K_0(N)$ and of weight $k$ is a line, spanned by the tensor product of the local newforms and of a vector of weight $k$ in $D_k$. A vector $\phi$ in this line is killed by $L$, so $\phi = \phi_h$ for some $h \in S_k(\Gamma_0(N))$, and $T_ph = \lambda_ph$ for $p \nmid N$, with $\lambda_p$ given by the Satake parameters of $\pi_p$. Then $h$ lies in a joint eigenspace of these operators, so by the description above $h = \sum_{d \mid N/M}c_d\,g(d\tau)$ for one newform $g$ of a level $M \mid N$, as in Proposition 2.1.10 of Volume 4. By Lemma 4.3.2 each function $\phi_{g(d\tau)}$ is a right translate of $\phi_g$, so it lies in $V_{\pi_g}$, and $\phi_h \in V_{\pi_g}$. So $V_\pi \cap V_{\pi_g} \ne 0$ and $\pi = \pi_g$ by Theorem 4.2.2. By Step 3 applied to $g$, $N(\pi) = M$, so $M = N$, $h$ is a multiple of $g$, and $\pi = \pi_g$ with $g$ a newform of level $N$. $\square$

Step 3 is the adelic form of the Atkin-Lehner theory: the old space of $\pi$ at level $N$ has dimension $d(N/N(\pi))$, the number of forms $g(d\tau)$ in Volume 4, and the local theory writes this count as a product of local counts.

**Remark 4.3.4 (other weights and characters).** For a newform with character $\chi$ the same proof works with $K_1(N)$, the group of matrices in $K_0(N)$ with $d \equiv 1 \bmod N$, and the central character of $\pi_f$ is the idele class character attached to $\chi$. For weight $k = 1$, $\pi_\infty$ is the limit of discrete series $D_1$. For a Maass form of eigenvalue $1/4 + r^2$ (Volume 4, Section 2.6), $\pi_\infty$ is a principal series, or a complementary series if $r$ is imaginary. Every cuspidal representation is of one of these kinds at infinity.

### The components at the primes that divide the level

The components at $p \mid N$ are among the infinite-dimensional representations with trivial central character and conductor exponent $v_p(N)$. The values of $c$ listed after Theorem 4.3.1 give the following description.

**Proposition 4.3.5 (local components of a newform).** Let $f$ be a newform of even weight $k$ and level $N$ with trivial character, and let $p \mid N$.
1. If $p \parallel N$, then $\pi_{f,p} \cong \mu\mathrm{St}$ with $\mu$ unramified and $\mu(p) = \pm 1$, and $a_p(f) = \mu(p)p^{k/2 - 1}$.
2. If $p^2 \mid N$, then $L(s, \pi_{f,p}) = 1$ and $a_p(f) = 0$.
3. If $v_p(N)$ is odd and at least 3, then $\pi_{f,p}$ is supercuspidal.

Lean: not formalized

*Proof.* For part 1, $c(\pi_{f,p}) = 1$. A principal series $\chi_1 \times \chi_2$ with $\chi_1\chi_2 = 1$ has $c(\chi_1) = c(\chi_2)$, so its conductor exponent is even. A supercuspidal has $c \ge 2$. A twist $\mu\mathrm{St}$ with $\mu$ ramified has $c = 2c(\mu) \ge 2$. So $\pi_{f,p} = \mu\mathrm{St}$ with $\mu$ unramified, and its central character $\mu^2$ is trivial, so $\mu(p) = \pm 1$. The value of $a_p$ comes from the operator $U_p = \sum_{b \bmod p}\pi\left(\begin{smallmatrix} p & b \\ 0 & 1 \end{smallmatrix}\right)$ on the line $\pi_{f,p}^{K_0(p)}$. On $(\chi_1 \times \chi_2)^{K_0(p)}$, with $\chi_1, \chi_2$ unramified, $U_p$ has the eigenvalues $p^{1/2}\chi_1(p)$ and $p^{1/2}\chi_2(p)$ (Exercise 3). For $\mu\mathrm{St} \subset \mu|\cdot|^{1/2} \times \mu|\cdot|^{-1/2}$ these are $\mu(p)$ and $\mu(p)p$. The quotient $\mu \circ \det$ is a line on which $U_p$ acts by $p\mu(p)$, the number of cosets times $\mu(p)$. So $U_p$ acts on the newform of $\mu\mathrm{St}$ by $\mu(p)$. The comparison with the classical operator is the same as in Remark 4.2.7, and the classical $U_p$ eigenvalue is $a_p(f) = p^{k/2 - 1}\mu(p)$.

For part 2, $c(\pi_{f,p}) \ge 2$, so by the list $\pi_{f,p}$ is $\chi \times \chi^{-1}$ with $\chi$ ramified, or $\mu\mathrm{St}$ with $\mu$ ramified, or supercuspidal. In all three cases $L(s, \pi_{f,p}) = 1$ (Chapter 3, Volume 6, Section 2.4). By Volume 4, Proposition 2.2.3, the Euler factor of $L(f, s)$ at a prime $p \mid N$ is $(1 - a_p(f)p^{-s})^{-1}$, and by Proposition 4.5.6 below it is $L(s - (k-1)/2, \pi_{f,p})$. So $a_p(f) = 0$. The proof of Proposition 4.5.6 uses only the local newforms in the Whittaker model and not the present statement. For part 3, the conductor exponents of the principal series and of the twists of Steinberg by ramified characters are even. $\square$

Part 2 is the classical fact that $a_p(f) = 0$ when $p^2$ divides the level and the character is trivial, which Atkin and Lehner proved. The sign $\mu(p)$ in part 1 is related to the Atkin-Lehner eigenvalue $w_p$ of $f$ by $w_p = -\mu(p)$. Section 4.5 explains this sign as the local root number.

**Example 4.3.6 (the components of $f_{11}$).** The newform $f_{11}$ has level 11 and $a_{11} = 1$. By Proposition 4.3.5, part 1, $\pi_{f_{11}, 11} = \mu\mathrm{St}$ with $\mu(11) = a_{11}\cdot 11^{0} = 1$, so $\mu$ is trivial and $\pi_{11}$ is the Steinberg representation $\mathrm{St}$. The Atkin-Lehner sign is $w_{11} = -1$, as in Volume 4, Example 2.2.15. For $p \ne 11$ the components are unramified with the parameters of Example 4.2.8, and $\pi_\infty = D_2$. The elliptic curve $X_0(11)$ has split multiplicative reduction at 11, since $a_{11} = 1$.

**Example 4.3.7 (a supercuspidal component).** The newform $f_{27} = \eta(3\tau)^2\eta(9\tau)^2 \in S_2(\Gamma_0(27))$ is attached to the elliptic curve $y^2 + y = x^3 - 7$, which has complex multiplication by $\mathbb{Z}[(1 + \sqrt{-3})/2]$. Here $v_3(27) = 3$ is odd, so $\pi_{f_{27}, 3}$ is supercuspidal by Proposition 4.3.5, part 3. In particular $a_3(f_{27}) = 0$.
