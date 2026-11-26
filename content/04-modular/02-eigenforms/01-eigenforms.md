---
title: Normalized eigenforms and newforms
nodes: []
sources: []
status: drafted
drafted_by: writer
reviewed_by: []
---
## Normalized eigenforms and newforms

This section characterizes the eigenforms of all the Hecke operators by their $q$-expansions, and it states the theory of newforms of Atkin, Lehner and Li. We fix $N \ge 1$, $k \in \mathbb{Z}$ and a Dirichlet character $\chi$ modulo $N$, and we use the operators $T_n$ of Definition 1.5.10 on $S_k(N, \chi)$. For $p \mid N$ the operator $T_p$ is the operator $U_p$ of Definition 1.5.6, and $T_{p^r} = U_p^r$. We put $\chi(n) = 0$ when $\gcd(n, N) > 1$.

### Eigenforms and their coefficients

**Definition 2.1.1 (eigenforms).** A nonzero $f \in S_k(N, \chi)$ is an *eigenform* if $T_n f \in \mathbb{C} f$ for every $n \ge 1$. We write $T_n f = \lambda_n(f) f$. An eigenform is *normalized* if $a_1(f) = 1$.

By Definition 1.5.10 the operators $T_n$ are polynomials in the operators $T_p$ and $\langle d \rangle$, and $\langle d \rangle$ acts on $S_k(N, \chi)$ by the scalar $\chi(d)$. So $f$ is an eigenform if and only if $T_p f \in \mathbb{C} f$ for every prime $p$. Corollary 1.6.3 gives a basis of $S_k(\Gamma_1(N))$ of forms that are eigenvectors of the $T_n$ with $\gcd(n, N) = 1$. These forms need not be eigenvectors of the $U_p$, and this is the subject of the second part of the section.

**Proposition 2.1.2 (the first coefficient).** Let $f \in S_k(N, \chi)$ be an eigenform. Then $a_n(f) = \lambda_n(f) a_1(f)$ for all $n \ge 1$, and $a_1(f) \ne 0$. So $f / a_1(f)$ is a normalized eigenform, and the coefficients of a normalized eigenform are its eigenvalues: $a_n(f) = \lambda_n(f)$.

Lean: not stated yet

*Proof.* By Proposition 1.5.11, $a_1(T_n f) = a_n(f)$. Also $a_1(T_n f) = \lambda_n(f) a_1(f)$. So $a_n(f) = \lambda_n(f) a_1(f)$. If $a_1(f) = 0$, then $a_n(f) = 0$ for all $n \ge 1$. Since $f$ is a cusp form, $a_0(f) = 0$ too, so $f = 0$ by Remark 1.2.5, a contradiction. $\square$

The proposition shows that two normalized eigenforms with the same eigenvalues for all $T_n$ are equal. This is the first form of multiplicity one. It also shows that the eigenvalues determine the form, so that the theory of eigenforms is a theory of their coefficients. The next theorem makes this precise.

**Theorem 2.1.3 (eigenforms by their $q$-expansions).** Let $f \in S_k(N, \chi)$ with $q$-expansion $\sum_{n \ge 1} a_n q^n$. Then $f$ is a normalized eigenform if and only if the coefficients satisfy these three conditions.
1. $a_1 = 1$.
2. $a_{mn} = a_m a_n$ for all coprime $m, n \ge 1$.
3. $a_{p^{r+1}} = a_p a_{p^r} - \chi(p) p^{k-1} a_{p^{r-1}}$ for all primes $p$ and all $r \ge 1$.

For $p \mid N$ condition 3 reads $a_{p^{r+1}} = a_p a_{p^r}$, so $a_{p^r} = a_p^r$.

Lean: not stated yet

*Proof.* Let $f$ be a normalized eigenform. By Proposition 2.1.2, $a_n = \lambda_n(f)$. By Definition 1.5.10, $T_{mn} = T_m T_n$ for coprime $m$ and $n$, so $\lambda_{mn}(f) = \lambda_m(f)\lambda_n(f)$. Also $T_{p^{r+1}} = T_p T_{p^r} - p^{k-1}\langle p \rangle T_{p^{r-1}}$, and $\langle p \rangle$ acts by $\chi(p)$ on $S_k(N, \chi)$. This gives condition 3.

Conversely, let the coefficients satisfy the three conditions, and let $p$ be a prime. We show that $T_p f = a_p f$. By Theorem 1.5.8, $a_m(T_p f) = a_{mp} + \chi(p)p^{k-1}a_{m/p}$, where $a_{m/p} = 0$ if $p \nmid m$. Write $m = p^r m'$ with $p \nmid m'$. If $r = 0$, conditions 1 and 2 give $a_{mp} = a_p a_{m'} = a_p a_m$. If $r \ge 1$, condition 2 gives $a_{mp} = a_{p^{r+1}}a_{m'}$ and $a_{m/p} = a_{p^{r-1}}a_{m'}$, and condition 3 gives
$$a_{mp} + \chi(p)p^{k-1}a_{m/p} = \bigl(a_{p^{r+1}} + \chi(p)p^{k-1}a_{p^{r-1}}\bigr)a_{m'} = a_p a_{p^r} a_{m'} = a_p a_m.$$
The constant terms of $T_p f$ and $a_p f$ are both 0, because $T_p f$ is a cusp form. So $T_p f$ and $a_p f$ have the same $q$-expansion, and they are equal. Thus $f$ is an eigenvector of each $T_p$, so of each $T_n$, and $a_1(f) = 1$. $\square$

The conditions of the theorem are Ramanujan's first two properties of $\tau(n)$, generalized to level $N$ and character $\chi$. Condition 3 is a linear recursion of order 2 for the sequence $(a_{p^r})_{r \ge 0}$, with the initial values $a_1 = 1$ and $a_p$. Its solution is
$$\sum_{r \ge 0} a_{p^r} X^r = \frac{1}{1 - a_p X + \chi(p)p^{k-1}X^2},$$
because the coefficient of $X^{r+1}$ in the product of the series with $1 - a_pX + \chi(p)p^{k-1}X^2$ is $a_{p^{r+1}} - a_pa_{p^r} + \chi(p)p^{k-1}a_{p^{r-1}}$ for $r \ge 1$, and $a_p - a_p a_1$ for $r = 0$. So a normalized eigenform is determined by its coefficients $a_p$ at the primes. This identity of power series is the local form of the Euler product of Section 2.2.

### The definitions in the Lean project

**Definition 2.1.4 (the Lean predicates).** Let $f$ be a cusp form of weight $k$ on $\Gamma_0(N)$, with coefficients $a_n = $ `Langlands.qCoeff f n`. The predicate `Langlands.IsNormalizedEigenform f` is the conjunction of four conditions.
1. `one`: $a_1 = 1$.
2. `mul`: $a_{mn} = a_m a_n$ for all coprime $m$ and $n$.
3. `good`: $a_{p^{r+2}} = a_p a_{p^{r+1}} - p^{k-1} a_{p^r}$ for all primes $p \nmid N$ and all $r \ge 0$.
4. `bad`: $a_{p^{r+1}} = a_p a_{p^r}$ for all primes $p \mid N$ and all $r \ge 0$.

Let $f$ be a cusp form of weight $k$ on $\Gamma_1(N)$, with coefficients $a_n = $ `Langlands.qCoeffGamma1 f n`, and let $\chi$ be a Dirichlet character modulo $N$. The predicate `Langlands.IsNormalizedEigenformWithCharacter f χ` is the conjunction of four conditions: `nebentypus`, which is `Langlands.HasNebentypus f χ` of Remark 1.5.4, then `one` and `mul` as above, and `prime_pow`: $a_{p^{r+2}} = a_p a_{p^{r+1}} - \chi(p) p^{k-1} a_{p^r}$ for all primes $p$ and all $r \ge 0$.

Lean: `Langlands.IsNormalizedEigenform`, `Langlands.IsNormalizedEigenformWithCharacter`

A cusp form on $\Gamma_0(N)$ is a form in $S_k(N, \mathbf{1})$, where $\mathbf{1}$ is the trivial character modulo $N$, whose value at $p$ is 0 for $p \mid N$. So for $f$ on $\Gamma_0(N)$ the condition `good` is condition 3 of Theorem 2.1.3 at $p \nmid N$, and `bad` is condition 3 at $p \mid N$; the index $r$ is shifted by one, and the case $r = 0$ of `bad` is trivial. In the same way, `prime_pow` is condition 3 for all $p$, and for $p \mid N$ it reads $a_{p^{r+2}} = a_p a_{p^{r+1}}$ because $\chi(p) = 0$. By Theorem 2.1.3, `Langlands.IsNormalizedEigenform f` holds if and only if $f$ is a normalized eigenform of all the $T_n$ on $S_k(\Gamma_0(N))$, and `Langlands.IsNormalizedEigenformWithCharacter f χ` holds if and only if $f \in S_k(N, \chi)$ and $f$ is a normalized eigenform. For $r = 0$, `prime_pow` gives $a_{p^2} = a_p^2 - \chi(p)p^{k-1}$, and together with `one` this is the case $r = 1$ of condition 3.

**Remark 2.1.5 (why the Lean project uses $q$-expansions).** Mathlib has no Hecke operators, see Remark 1.5.13. A definition of $T_p$ on $S_k(\Gamma_1(N))$ needs the double cosets of Section 1.5, the proof that $f|[\Gamma_1\alpha\Gamma_1]$ is again a modular form, including at the cusps, and the formula of Theorem 1.5.8. Theorem 2.1.3 shows that the eigenform condition can be stated without the operators, as a condition on the coefficients `qCoeff f n`. All the statements of the project that involve eigenforms only use the coefficients of the forms, so this is no loss. There are two points to watch. First, the coefficients are those of the expansion in $q = e^{2\pi i\tau}$ at the cusp $\infty$, as Remark 1.2.5 explains; with the expansion in $q_N$ the conditions would say something else. Second, the predicates do not say that $f$ is a newform. The rest of this section shows that this changes nothing in the statements, because a normalized eigenform has the coefficients of a newform at the primes $p \nmid N$.

**Example 2.1.6 (the first eigenforms).** By Corollary 1.6.5, $\Delta$ is a normalized eigenform in $S_{12}(SL_2(\mathbb{Z})) = S_{12}(\Gamma_0(1))$, so `Langlands.IsNormalizedEigenform` holds for it. The Lean project states this fact, Mordell's theorem, as the proposition `Langlands.Bridge.DeltaIsEigenform`, see Remark 2.3.5. By Remark 1.3.11 the space $S_2(\Gamma_0(11))$ is $\mathbb{C}f_{11}$. Each $T_n$ preserves it, so $f_{11}$ is an eigenform, and it is normalized. Its coefficients satisfy the conditions of Definition 2.1.4 with $N = 11$ and $k = 2$. For example $a_4 = a_2^2 - 2 = 2$, $a_8 = a_2a_4 - 2a_2 = 0$, $a_9 = a_3^2 - 3 = -2$, and $a_{121} = a_{11}^2 = 1$.

### Oldforms and newforms

If $M \mid N$ and $g \in S_k(\Gamma_1(M))$, then $g \in S_k(\Gamma_1(N))$, since $\Gamma_1(N) \subset \Gamma_1(M)$. Also $g(d\tau) \in S_k(\Gamma_1(N))$ for each $d \mid N/M$. Indeed, $g(d\tau) = d^{1-k}(g|_k \delta_d)(\tau)$ with $\delta_d = \mathrm{diag}(d, 1)$, and $\delta_d \gamma \delta_d^{-1} \in \Gamma_1(M)$ for $\gamma \in \Gamma_1(N)$, as in Example 1.2.8. If $g$ has nebentypus $\chi$ modulo $M$, then $g(d\tau)$ has nebentypus the character modulo $N$ induced by $\chi$.

**Definition 2.1.7 (oldforms and newforms).** The *space of oldforms* $S_k(\Gamma_1(N))^{\mathrm{old}}$ is the subspace of $S_k(\Gamma_1(N))$ spanned by the forms $g(d\tau)$, where $M$ is a divisor of $N$ with $M \ne N$, $g \in S_k(\Gamma_1(M))$ and $d \mid N/M$. The *space of newforms* $S_k(\Gamma_1(N))^{\mathrm{new}}$ is its orthogonal complement for the Petersson inner product. A *newform of level $N$* is a normalized eigenform in $S_k(\Gamma_1(N))^{\mathrm{new}}$ that lies in some $S_k(N, \chi)$.

It suffices to take $M = N/p$ for the primes $p \mid N$ and $d \in \{1, p\}$, since the other forms $g(d\tau)$ are in the span of these. For $N = 1$ there are no oldforms, and the newforms of level 1 are the normalized eigenforms of Proposition 1.6.4. The forms $g(d\tau)$ with $d > 1$ have $a_1 = 0$, so they are never normalized. The following theorem is due to Atkin and Lehner for $\Gamma_0(N)$ and to Li in general.

**Theorem 2.1.8 (Atkin, Lehner and Li).** Let $N \ge 1$ and $k \in \mathbb{Z}$.
1. The spaces $S_k(\Gamma_1(N))^{\mathrm{old}}$ and $S_k(\Gamma_1(N))^{\mathrm{new}}$ are stable under all the operators $T_n$ and $\langle d \rangle$.
2. Let $f \in S_k(\Gamma_1(N))^{\mathrm{new}}$ be nonzero, with $T_p f = \lambda_p f$ and $\langle d \rangle f = \chi(d) f$ for all primes $p \nmid N$ and all $d$. Then $f$ is a scalar multiple of a newform. The newforms of level $N$ form a basis of $S_k(\Gamma_1(N))^{\mathrm{new}}$.
3. (strong multiplicity one) Let $f$ be a newform of level $N$ and $g$ a newform of level $M$. If $a_p(f) = a_p(g)$ for all but finitely many primes $p$, then $M = N$ and $f = g$.
4. The space $S_k(\Gamma_1(N))$ is the direct sum of the lines $\mathbb{C}\,g(d\tau)$, where $M$ runs over the divisors of $N$, $g$ over the newforms of level $M$, and $d$ over the divisors of $N/M$.

Lean: not stated yet

*Outline of the proof.* The proof is in Diamond and Shurman, Section 5.8, and in the paper of Atkin and Lehner. Part 1 follows from Theorem 1.6.2 for the $T_n$ with $\gcd(n, N) = 1$; the stability of the old space under $U_p$ is a computation like the one in Remark 1.6.7, and the stability of the new space uses the adjoint of $U_p$, which is conjugate to $U_p$ by the Atkin-Lehner operator $w_N$ of Section 2.2. The key to the other parts is the main lemma: if $f \in S_k(\Gamma_1(N))$ has $a_n(f) = 0$ for all $n$ with $\gcd(n, N) = 1$, then $f = \sum_{p \mid N} f_p(p\tau)$ with $f_p \in S_k(\Gamma_1(N/p))$, so $f$ is old. For part 2, let $f$ be as there. The computation of Proposition 2.1.2 gives $a_n(f) = \lambda_n a_1(f)$ for $n$ coprime to $N$. If $a_1(f) = 0$, the main lemma shows that $f$ is old, so $f = 0$, since the old and the new space meet in 0. So we may assume $a_1(f) = 1$. For $p \mid N$ the form $h = U_pf - a_p(f)f$ is new by part 1, it is an eigenvector of the $T_q$ with $q \nmid N$ with the same eigenvalues as $f$, and $a_1(h) = a_p(f) - a_p(f) = 0$. By the same argument $h = 0$. So $f$ is an eigenvector of all the $T_n$, and it is a newform. Two newforms with the same $\lambda_p$ differ by a form with $a_1 = 0$, which is 0 by the same argument. Parts 3 and 4 follow from part 2 and the main lemma by induction on the level, and we refer to Diamond and Shurman for the details. $\square$

The proof of part 2 also shows that a form in the new space that is an eigenvector of the $T_p$ with $p \nmid N$ is an eigenvector of $U_p$ for $p \mid N$. On the new space the operators $U_p$ are therefore diagonalizable. On the old space they need not be, as Remark 1.6.7 shows.

### Eigenforms of level $N$ that are not newforms

**Example 2.1.9 (a normalized eigenform that is old).** Let $g \in S_k(\Gamma_0(M))$ be a newform, let $p \nmid M$ be a prime, and let $a_p = a_p(g)$. Let $\alpha$ and $\beta$ be the roots of $X^2 - a_p X + p^{k-1}$, so $\alpha + \beta = a_p$ and $\alpha\beta = p^{k-1}$. Put
$$f_\alpha(\tau) = g(\tau) - \beta\, g(p\tau) \in S_k(\Gamma_0(Mp)).$$
Then $f_\alpha$ is old, and `Langlands.IsNormalizedEigenform` $f_\alpha$ holds at level $Mp$. Indeed, $a_n(f_\alpha) = a_n(g) - \beta a_{n/p}(g)$. The operator $U_p$ at level $Mp$ sends $\sum a_n q^n$ to $\sum a_{np}q^n$, and $T_pg = a_pg$ gives $a_{np}(g) = a_pa_n(g) - p^{k-1}a_{n/p}(g)$ by Theorem 1.5.8. So
$$a_{np}(f_\alpha) = a_pa_n(g) - p^{k-1}a_{n/p}(g) - \beta a_n(g) = \alpha a_n(g) - \alpha\beta\, a_{n/p}(g) = \alpha\, a_n(f_\alpha),$$
and $U_p f_\alpha = \alpha f_\alpha$. For a prime $q \nmid Mp$ the operator $T_q$ of level $Mp$ commutes with $h \mapsto h(p\tau)$, by the formula of Theorem 1.5.8, so $T_q f_\alpha = a_q(g) f_\alpha$. For a prime $q \mid M$ the same formula shows that $U_q$ commutes with $h \mapsto h(p\tau)$, so $U_q f_\alpha = a_q(g) f_\alpha$. Thus $f_\alpha$ is a normalized eigenform, and Theorem 2.1.3 gives the claim. Its coefficients are $a_n(f_\alpha) = a_n(g)$ for $p \nmid n$, and $a_{p^r}(f_\alpha) = \alpha^r$. If $\alpha \ne \beta$, then $f_\alpha$ and $f_\beta$ are a basis of the span of $g$ and $g(p\tau)$, and $U_p$ is diagonalizable on it. If $\alpha = \beta$, then $U_p$ is not diagonalizable on this span. Coleman and Edixhoven proved that this case does not occur for $k = 2$, and that for $k \ge 3$ it does not occur if the Tate conjecture holds for certain varieties over finite fields.

For $f_{11}$ and $p = 2$ the roots of $X^2 + 2X + 2$ are $\alpha, \beta = -1 \pm i$, and $f_{11}(\tau) - \beta f_{11}(2\tau)$ is a normalized eigenform in $S_2(\Gamma_0(22))$ that is not a newform. Its coefficient at $q^2$ is $\alpha$, which is not a rational number.

**Proposition 2.1.10 (eigenforms have the eigenvalues of a newform).** Let $f \in S_k(N, \chi)$ be a normalized eigenform. Then there are a divisor $M$ of $N$ and a newform $g$ of level $M$ such that $a_n(f) = a_n(g)$ for every $n$ with $\gcd(n, N) = 1$. In particular $a_p(f) = a_p(g)$ for all primes $p \nmid N$.

Lean: not stated yet

*Proof.* By part 4 of Theorem 2.1.8, $f = \sum_{(M, g, d)} c_{M,g,d}\, g(d\tau)$, a finite sum over the triples there. For a prime $p \nmid N$ the operator $T_p$ of level $N$ commutes with $h \mapsto h(d\tau)$ for $d \mid N$, and on a form of level $M \mid N$ it is the operator $T_p$ of level $M$, by Theorem 1.5.8. So each $g(d\tau)$ is an eigenvector of $T_p$ with eigenvalue $a_p(g)$. The vectors $g(d\tau)$ are linearly independent, and $T_p f = a_p(f) f$, so $c_{M,g,d} \ne 0$ implies $a_p(g) = a_p(f)$ for all $p \nmid N$. By part 3 of Theorem 2.1.8, at most one newform $g$ has this property. So $f = \sum_{d \mid N/M} c_d\, g(d\tau)$ for one newform $g$ of a level $M$. For $n$ coprime to $N$, the coefficient $a_n(g(d\tau))$ is $a_{n/d}(g)$, which is 0 for $d > 1$. So $a_n(f) = c_1 a_n(g)$, and $n = 1$ gives $c_1 = 1$. $\square$

**Remark 2.1.11 (statements for all normalized eigenforms).** A newform satisfies the predicates of Definition 2.1.4, by Theorem 2.1.3 and the remark after Theorem 2.1.8. So a statement about all the normalized eigenforms of all levels implies the same statement for newforms. Conversely, let a statement concern only the coefficients $a_p(f)$ at primes $p \nmid N$, or at primes outside a finite set that contains the primes dividing $N$. By Proposition 2.1.10 it holds for every normalized eigenform $f$ of level $N$ if it holds for every newform, because $f$ has the same $a_p$ as a newform $g$ of a level $M \mid N$, and each prime that divides $M$ divides $N$. This is why the Lean statements of Sections 2.3 and 2.4 quantify over all the normalized eigenforms, as in the docstring of `Langlands.EichlerShimuraDeligne`, and need no definition of newforms. The statements of Sections 2.2 and 2.5 that ask for all the coefficients of a form, at the primes that divide the level too, are different, and Remarks 2.2.12 and 2.5.10 discuss them.
