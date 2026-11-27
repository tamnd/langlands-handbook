---
title: Adjoints and eigenforms
nodes: []
sources: []
status: checked
drafted_by: writer
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## Adjoints and eigenforms

This section computes the adjoints of the diamond and Hecke operators for the Petersson inner product. The operators $T_p$ with $p \nmid N$ are normal, so the space of cusp forms has an orthogonal basis of common eigenforms. In level one the basis consists of forms with $a_1 = 1$, and their coefficients are the eigenvalues. Mordell's theorem on $\tau(n)$ follows.

**Proposition 1.6.1 (the adjoint of a double coset).** Let $\Gamma$ be a congruence subgroup, $\alpha \in GL_2^+(\mathbb{Q})$ and $\alpha' = \det(\alpha)\alpha^{-1}$. Let $f, g \in M_k(\Gamma)$, and let at least one of them be a cusp form. Then
$$\langle f|[\Gamma\alpha\Gamma], g \rangle = \langle f, g|[\Gamma\alpha'\Gamma] \rangle.$$

Lean: not stated yet

*Proof.* For $\gamma \in SL_2(\mathbb{Z})$ and forms $F, G$, Proposition 1.4.5 gives $\langle F|\gamma, G|\gamma\rangle = \langle F, G|\gamma\gamma^{-1}\rangle = \langle F, G\rangle$. Let $\beta = \gamma_1\alpha\gamma_2 \in \Gamma\alpha\Gamma$. Then
$$\langle f|\beta, g\rangle = \langle (f|\alpha)|\gamma_2, g|\gamma_2 \rangle = \langle f|\alpha, g \rangle,$$
because $f|\gamma_1 = f$ and $g|\gamma_2 = g$. So $\langle f|[\Gamma\alpha\Gamma], g\rangle = n\langle f|\alpha, g\rangle$, where $n$ is the number of right cosets in $\Gamma\alpha\Gamma$. In the same way $\langle f, g|[\Gamma\alpha'\Gamma]\rangle = n'\langle f, g|\alpha'\rangle$, where $n'$ is the number of right cosets in $\Gamma\alpha'\Gamma$. By Proposition 1.4.5, $\langle f|\alpha, g\rangle = \langle f, g|\alpha'\rangle$. By Lemma 1.5.1, $n = [\Gamma : \Gamma \cap \alpha^{-1}\Gamma\alpha]$ and $n' = [\Gamma : \Gamma\cap\alpha\Gamma\alpha^{-1}]$, since $\alpha'$ is a scalar multiple of $\alpha^{-1}$. These indices are equal by Proposition 1.4.5. That proposition compares the images in $PSL_2(\mathbb{Z})$, but the indices do not change: if $-I \in \Gamma$, then $-I$ is in both subgroups, and if $-I \notin \Gamma$, then $\Gamma$ maps isomorphically onto its image. $\square$

**Theorem 1.6.2 (adjoints of the Hecke operators).** On $S_k(\Gamma_1(N))$, for all $d \in (\mathbb{Z}/N\mathbb{Z})^\times$ and all primes $p \nmid N$,
$$\langle d \rangle^* = \langle d \rangle^{-1}, \qquad T_p^* = \langle p \rangle^{-1} T_p.$$

Lean: not stated yet

*Proof.* Let $\gamma \in \Gamma_0$ have lower right entry $d$. Then $\Gamma_1\gamma\Gamma_1 = \Gamma_1\gamma$, since $\Gamma_1$ is normal in $\Gamma_0$, and $\gamma' = \gamma^{-1}$. So Proposition 1.6.1 gives $\langle d\rangle^* = \langle d^{-1}\rangle$.

For $T_p$, we have $T_p = [\Gamma_1\alpha\Gamma_1]$ with $\alpha = \begin{pmatrix} 1 & 0 \\ 0 & p\end{pmatrix}$ and $\alpha' = \begin{pmatrix} p & 0 \\ 0 & 1\end{pmatrix}$. For $\beta = \begin{pmatrix} a & b \\ c & d\end{pmatrix}$ we have $p\beta^{-1} = \begin{pmatrix} d & -b \\ -c & a\end{pmatrix}$ if $\det\beta = p$. Since $\Delta_p = \Gamma_1\alpha\Gamma_1$ by Lemma 1.5.5, the double coset $\Gamma_1\alpha'\Gamma_1$ is
$$\Delta_p' = \{p\beta^{-1} : \beta \in \Delta_p\} = \left\{ \begin{pmatrix} a & b \\ c & d\end{pmatrix} \in M_2(\mathbb{Z}) : ad - bc = p,\ d \equiv 1 \text{ and } c \equiv 0 \bmod N \right\}.$$
Let $\delta \in \Gamma_0$ have lower right entry congruent to $p^{-1}$ modulo $N$, so its upper left entry is congruent to $p$. Each $\beta \in \Delta_p$ is congruent to $\begin{pmatrix} 1 & * \\ 0 & p \end{pmatrix}$ modulo $N$, so $\delta\beta \equiv \begin{pmatrix} p & * \\ 0 & 1\end{pmatrix}$ and $\delta\beta \in \Delta_p'$. The same argument for $\delta^{-1}$ shows $\delta\Delta_p = \Delta_p'$. Since $\Gamma_1\delta\beta = \delta\Gamma_1\beta$, the matrices $\delta\beta$, for $\beta$ in a set of representatives of $\Gamma_1\backslash\Delta_p$, represent $\Gamma_1\backslash\Delta_p'$. So $f|[\Gamma_1\alpha'\Gamma_1] = \sum_\beta (f|\delta)|\beta = T_p\langle p^{-1}\rangle f$, and $T_p^* = \langle p\rangle^{-1}T_p$ by Theorem 1.5.9. $\square$

On $S_k(N, \chi)$ the theorem says $T_p^* = \overline{\chi(p)}\, T_p$ for $p \nmid N$. For $\chi = \mathbf{1}$ the operators $T_p$ with $p \nmid N$ are self-adjoint.

**Corollary 1.6.3 (bases of eigenforms).** The operators $T_n$ with $\gcd(n, N) = 1$ and the operators $\langle d\rangle$ are normal on $S_k(\Gamma_1(N))$. The space $S_k(\Gamma_1(N))$ has an orthogonal basis of forms that are eigenvectors of all of them. Each such form lies in $S_k(N, \chi)$ for some $\chi$.

Lean: not stated yet

*Proof.* By Theorem 1.6.2, $\langle d\rangle$ is unitary, and $T_p^*$ is a polynomial in $T_p$ and the diamond operators, so it commutes with $T_p$ by Theorem 1.5.9. For $\gcd(n, N) = 1$, $T_n$ is a polynomial in these operators by Definition 1.5.10, so $T_n$ and $T_n^*$ commute. A commuting family of normal operators on a finite dimensional inner product space has an orthonormal basis of common eigenvectors, by the spectral theorem. A common eigenvector of the $\langle d\rangle$ lies in $S_k(N,\chi)$, where $\chi(d)$ is the eigenvalue of $\langle d\rangle$. $\square$

The operators $U_p$ with $p \mid N$ are not covered by the corollary. Section 2.1 treats them with the theory of newforms. In level one there is no such prime, and the result is complete.

**Proposition 1.6.4 (eigenforms in level one).** Let $k \in \mathbb{Z}$.
1. Let $f \in S_k(SL_2(\mathbb{Z}))$ be nonzero with $T_n f = \lambda_n f$ for all $n \ge 1$. Then $a_1(f) \ne 0$, and if $a_1(f) = 1$, then $a_n(f) = \lambda_n$ for all $n$.
2. The space $S_k(SL_2(\mathbb{Z}))$ has a unique basis of eigenforms of all $T_n$ with $a_1 = 1$. The basis is orthogonal, the coefficients of the basis forms are real, and two different basis forms have different eigenvalues for some $T_p$.

Lean: not stated yet

*Proof.* By Proposition 1.5.11, $a_n(f) = a_1(T_nf) = \lambda_n a_1(f)$ for all $n \ge 1$. If $a_1(f) = 0$, then all $a_n(f)$ with $n \ge 1$ vanish, and $a_0(f) = 0$ because $f$ is a cusp form, so $f = 0$. This proves part 1.

By part 1, a form with given eigenvalues $(\lambda_n)$ is $a_1(f)\sum_n \lambda_n q^n$. So each common eigenspace has dimension 1 and contains exactly one form with $a_1 = 1$. By Corollary 1.6.3 the space is the direct sum of these eigenspaces, which gives the existence and the uniqueness of the basis. The operators $T_n$ are self-adjoint in level one, by Theorem 1.6.2, because $\langle p \rangle = 1$. So their eigenvalues are real, and the coefficients of the basis forms are real. If $f$ and $g$ are basis forms with eigenvalues $\lambda_n$ and $\mu_n$, then $\lambda_n\langle f, g\rangle = \langle T_nf, g\rangle = \langle f, T_ng\rangle = \mu_n\langle f, g\rangle$. If $f \ne g$, then $\lambda_n \ne \mu_n$ for some $n$, and then $\langle f, g\rangle = 0$. Since the $T_n$ are polynomials in the $T_p$, the two forms also have different eigenvalues for some $T_p$. $\square$

**Corollary 1.6.5 (Mordell).** The coefficients $\tau(n)$ of $\Delta$ satisfy
$$\tau(mn) = \tau(m)\tau(n) \text{ for } \gcd(m, n) = 1, \qquad \tau(p^{r+1}) = \tau(p)\tau(p^r) - p^{11}\tau(p^{r-1})$$
for all primes $p$ and $r \ge 1$.

Lean: not stated yet

*Proof.* The space $S_{12}(SL_2(\mathbb{Z}))$ is $\mathbb{C}\Delta$ by Corollary 1.3.5, and $T_n$ preserves it. So $\Delta$ is an eigenform of all $T_n$, and $a_1(\Delta) = 1$. By Proposition 1.6.4, $T_n\Delta = \tau(n)\Delta$. The relations $T_{mn} = T_mT_n$ and $T_{p^{r+1}} = T_pT_{p^r} - p^{11}T_{p^{r-1}}$ of Definition 1.5.10 give the relations for the eigenvalues. $\square$

The same argument applies to each normalized eigenform of level one. For $k = 16, 18, 20, 22, 26$ the space $S_k$ has dimension 1, and it is spanned by $\Delta E_{k-12}$, which is therefore an eigenform. In weight 24 the eigenvalues are not rational.

**Example 1.6.6 (weight 24).** The space $S_{24}$ has the basis $f_1 = \Delta E_4^3$ and $f_2 = \Delta^2$, by Theorem 1.3.4 and Corollary 1.3.6. Their expansions begin
$$f_1 = q + 696q^2 + 162252q^3 + \cdots, \qquad f_2 = q^2 - 48q^3 + 1080q^4 - 15040q^5 + \cdots.$$
Proposition 1.5.11 gives the first coefficients of $T_2f_1$ and $T_2f_2$, and since a form in $S_{24}$ is determined by $a_1$ and $a_2$, we get
$$T_2 f_1 = 696 f_1 + 20736000 f_2, \qquad T_2 f_2 = f_1 + 384 f_2.$$
The characteristic polynomial of $T_2$ is $X^2 - 1080X - 20468736$, with roots $540 \pm 12\sqrt{144169}$. The number $144169$ is not a square, so the two normalized eigenforms have coefficients in the real quadratic field $\mathbb{Q}(\sqrt{144169})$, and they are conjugate under its Galois group. Maeda's conjecture predicts that for every $k$ the characteristic polynomial of $T_2$ on $S_k(SL_2(\mathbb{Z}))$ is irreducible over $\mathbb{Q}$ with Galois group the full symmetric group.

**Remark 1.6.7 (the operators $U_p$).** At the primes $p \mid N$ the operator $U_p$ need not be diagonalizable. Let $g \in S_k(SL_2(\mathbb{Z}))$ be a normalized eigenform with $T_pg = a_pg$, and let $g_i(\tau) = g(p^i\tau)$, a form of level $p^i$ by Example 1.2.8. By Theorem 1.5.8 at level 1 we have $a_pg = U g + p^{k-1}g_1$, where $U$ is the map $\sum a_nq^n \mapsto \sum a_{np}q^n$, and $U$ is the operator $U_p$ at level $p^3$. So $U_p g_0 = a_pg_0 - p^{k-1}g_1$ and $U_pg_i = g_{i-1}$ for $i = 1, 2, 3$. The forms $g_0, \ldots, g_3$ are linearly independent, because their first nonzero coefficients are at $q, q^p, q^{p^2}, q^{p^3}$. On their span, $U_p$ has the characteristic polynomial $X^2(X^2 - a_pX + p^{k-1})$. Its kernel consists of the vectors $\sum x_ig_i$ with $x_3 = 0$, $x_1 = -a_px_0$ and $x_2 = p^{k-1}x_0$, so it has dimension 1, and the eigenvalue 0 has algebraic multiplicity 2. So $U_p$ is not diagonalizable on $S_k(\Gamma_0(p^3))$.

**Proposition 1.6.8 (integrality in level one).** Let $f$ be a normalized eigenform in $S_k(SL_2(\mathbb{Z}))$. Then each $a_n(f)$ is an algebraic integer, and the field $\mathbb{Q}(a_n(f) : n \ge 1)$ is a totally real number field of degree at most $\dim S_k$.

Lean: not stated yet

*Proof.* Let $L$ be the set of forms in $S_k$ with all coefficients in $\mathbb{Z}$, and $d = \dim S_k$. By Theorem 1.3.4 and Corollary 1.3.6 the forms $\Delta E_4^aE_6^b$ with $4a + 6b = k - 12$ form a basis of $S_k$, and they are in $L$ by Theorem 1.2.11 and Proposition 1.2.13. Choose indices $n_1, \ldots, n_d$ such that the matrix of the coefficients $a_{n_j}$ of these basis forms is invertible, and let $D$ be its determinant. The coordinates of a form in $L$ in this basis are rational with denominators dividing $D$. So $L$ is a free $\mathbb{Z}$-module of rank $d$ that spans $S_k$. By Proposition 1.5.11 with $N = 1$, each $T_n$ maps $L$ into $L$. So the characteristic polynomial of $T_n$ is monic with integer coefficients, and the eigenvalue $a_n(f)$ is an algebraic integer. The automorphisms of $\mathbb{C}$ act on $L \otimes \mathbb{C} = S_k$ through the coefficients and commute with each $T_n$. So they permute the $d$ normalized eigenforms, and the field generated by the coefficients of $f$ has at most $d$ embeddings into $\mathbb{C}$. All of them are real, by Proposition 1.6.4. $\square$

At a general level the coefficients of a normalized eigenform are also algebraic integers. Diamond and Shurman prove it for weight 2 in Section 6.5, from the integral structure of the Jacobian of $X_1(N)$. Shimura proves it for all weights in Chapter 3.
