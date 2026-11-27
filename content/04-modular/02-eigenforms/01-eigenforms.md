---
title: Normalized eigenforms and newforms
nodes: []
sources: []
status: checked
drafted_by: writer
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## Normalized eigenforms and newforms

This section characterizes the eigenforms of all the Hecke operators by their $q$-expansions, and it states the theory of newforms of Atkin, Lehner and Li. The last three subsections prove the multiplicativity of the coefficients and the formula for $T_n$ from the relations of the single operators $T_p$, as the Lean project does. We fix $N \ge 1$, $k \in \mathbb{Z}$ and a Dirichlet character $\chi$ modulo $N$, and we use the operators $T_n$ of Definition 1.5.10 on $S_k(N, \chi)$. For $p \mid N$ the operator $T_p$ is the operator $U_p$ of Definition 1.5.6, and $T_{p^r} = U_p^r$. We put $\chi(n) = 0$ when $\gcd(n, N) > 1$.

### Eigenforms and their coefficients

**Definition 2.1.1 (eigenforms).** A nonzero $f \in S_k(N, \chi)$ is an *eigenform* if $T_n f \in \mathbb{C} f$ for every $n \ge 1$. We write $T_n f = \lambda_n(f) f$. An eigenform is *normalized* if $a_1(f) = 1$.

By Definition 1.5.10 the operators $T_n$ are polynomials in the operators $T_p$ and $\langle d \rangle$, and $\langle d \rangle$ acts on $S_k(N, \chi)$ by the scalar $\chi(d)$. So $f$ is an eigenform if and only if $T_p f \in \mathbb{C} f$ for every prime $p$. Corollary 1.6.3 gives a basis of $S_k(\Gamma_1(N))$ of forms that are eigenvectors of the $T_n$ with $\gcd(n, N) = 1$. These forms need not be eigenvectors of the $U_p$, and this is the subject of the second part of the section.

**Proposition 2.1.2 (the first coefficient).** Let $f \in S_k(N, \chi)$ be an eigenform. Then $a_n(f) = \lambda_n(f) a_1(f)$ for all $n \ge 1$, and $a_1(f) \ne 0$. So $f / a_1(f)$ is a normalized eigenform, and the coefficients of a normalized eigenform are its eigenvalues: $a_n(f) = \lambda_n(f)$.

Lean: `Langlands.Modular.eigenvalue_eq_qCoeff`, for the operators $T_p$ on $S_k(\Gamma_0(N))$ and an eigenvector with $a_1 = 1$; the claim $a_1(f) \ne 0$ is not stated

*Proof.* By Proposition 1.5.11, $a_1(T_n f) = a_n(f)$. Also $a_1(T_n f) = \lambda_n(f) a_1(f)$. So $a_n(f) = \lambda_n(f) a_1(f)$. If $a_1(f) = 0$, then $a_n(f) = 0$ for all $n \ge 1$. Since $f$ is a cusp form, $a_0(f) = 0$ too, so $f = 0$ by Remark 1.2.5, a contradiction. $\square$

The proposition shows that two normalized eigenforms with the same eigenvalues for all $T_n$ are equal. This is the first form of multiplicity one. It also shows that the eigenvalues determine the form, so that the theory of eigenforms is a theory of their coefficients. The next theorem makes this precise.

**Theorem 2.1.3 (eigenforms by their $q$-expansions).** Let $f \in S_k(N, \chi)$ with $q$-expansion $\sum_{n \ge 1} a_n q^n$. Then $f$ is a normalized eigenform if and only if the coefficients satisfy these three conditions.
1. $a_1 = 1$.
2. $a_{mn} = a_m a_n$ for all coprime $m, n \ge 1$.
3. $a_{p^{r+1}} = a_p a_{p^r} - \chi(p) p^{k-1} a_{p^{r-1}}$ for all primes $p$ and all $r \ge 1$.

For $p \mid N$ condition 3 reads $a_{p^{r+1}} = a_p a_{p^r}$, so $a_{p^r} = a_p^r$.

Lean: `Langlands.Modular.IsNormalizedHeckeEigenform.toIsNormalizedEigenform`, for the direct implication on $S_k(\Gamma_0(N))$, see Corollary 2.1.15; the converse is not stated

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

**Remark 2.1.5 (why the Lean project uses $q$-expansions).** The Lean project defines the operators $T_p$ and $U_p$ on $S_k(\Gamma_0(N))$, see Remark 1.5.21. It defines the operators $T_n$ on $S_k(\Gamma_0(N))$ from these, see Definition 1.5.24, but it has no operators on $S_k(\Gamma_1(N))$. So the eigenform condition of Definition 2.1.1 cannot be stated in Lean for a character $\chi$. For $\Gamma_0(N)$ it is stated with the operators $T_p$ and $U_p$, and Corollary 1.5.30 gives it for all the $T_n$. The project does this with the predicate `Langlands.Modular.IsNormalizedHeckeEigenform` of Corollary 2.1.15. Theorem 2.1.3 shows that the eigenform condition can be stated without the operators, as a condition on the coefficients `qCoeff f n`. All the statements of the project that involve eigenforms only use the coefficients of the forms, so this is no loss. For $\Gamma_0(N)$ the project also proves one direction of the equivalence: a normalized eigenform of all the $T_p$ and $U_p$ satisfies `Langlands.IsNormalizedEigenform`, by Corollary 2.1.15. There are two points to watch. First, the coefficients are those of the expansion in $q = e^{2\pi i\tau}$ at the cusp $\infty$, as Remark 1.2.5 explains; with the expansion in $q_N$ the conditions would say something else. Second, the predicates do not say that $f$ is a newform. The rest of this section shows that this changes nothing in the statements, because a normalized eigenform has the coefficients of a newform at the primes $p \nmid N$.

**Example 2.1.6 (the first eigenforms).** By Corollary 1.6.5, $\Delta$ is a normalized eigenform in $S_{12}(SL_2(\mathbb{Z})) = S_{12}(\Gamma_0(1))$, so `Langlands.IsNormalizedEigenform` holds for it. The Lean project states this fact, Mordell's theorem, as the proposition `Langlands.Bridge.DeltaIsEigenform`, see Remark 2.3.5. By Remark 1.3.11 the space $S_2(\Gamma_0(11))$ is $\mathbb{C}f_{11}$. Each $T_n$ preserves it, so $f_{11}$ is an eigenform, and it is normalized. Its coefficients satisfy the conditions of Definition 2.1.4 with $N = 11$ and $k = 2$. For example $a_4 = a_2^2 - 2 = 2$, $a_8 = a_2a_4 - 2a_2 = 0$, $a_9 = a_3^2 - 3 = -2$, and $a_{121} = a_{11}^2 = 1$.

### Oldforms and newforms

If $M \mid N$ and $g \in S_k(\Gamma_1(M))$, then $g \in S_k(\Gamma_1(N))$, since $\Gamma_1(N) \subset \Gamma_1(M)$. Also $g(d\tau) \in S_k(\Gamma_1(N))$ for each $d \mid N/M$. Indeed, $g(d\tau) = d^{1-k}(g|_k \delta_d)(\tau)$ with $\delta_d = \mathrm{diag}(d, 1)$, and $\delta_d \gamma \delta_d^{-1} \in \Gamma_1(M)$ for $\gamma \in \Gamma_1(N)$, as in Example 1.2.8. If $g$ has nebentypus $\chi$ modulo $M$, then $g(d\tau)$ has nebentypus the character modulo $N$ induced by $\chi$.

**Definition 2.1.7 (oldforms and newforms).** The *space of oldforms* $S_k(\Gamma_1(N))^{\mathrm{old}}$ is the subspace of $S_k(\Gamma_1(N))$ spanned by the forms $g(d\tau)$, where $M$ is a divisor of $N$ with $M \ne N$, $g \in S_k(\Gamma_1(M))$ and $d \mid N/M$. The *space of newforms* $S_k(\Gamma_1(N))^{\mathrm{new}}$ is its orthogonal complement for the Petersson inner product. A *newform of level $N$* is a normalized eigenform in $S_k(\Gamma_1(N))^{\mathrm{new}}$ that lies in some $S_k(N, \chi)$.

Lean: `Langlands.Modular.oldSpace`, for the space of oldforms of $S_k(\Gamma_0(N))$, see Definition 1.5.36; the space of newforms and the newforms are not defined

For $\Gamma_0(N)$ the Lean project has the first half of this definition. Definition 1.5.34 gives the maps $B_d$, with $(B_dg)(\tau) = g(d\tau)$, Proposition 1.5.35 computes their $q$-expansions, and Definition 1.5.36 defines the space of oldforms of $S_k(\Gamma_0(N))$ as the span of the images of the maps $B_d$ from the levels $M < N$ with $dM \mid N$. Example 1.5.37 shows that $S_2(\Gamma_0(22))$ is old. The Petersson inner product on $S_k(\Gamma_0(N))$ is not in Lean, so the orthogonal complement is not available there, and Remark 1.5.38 lists what else is missing.

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

### Multiplicativity from the operators $T_p$

The proof of Theorem 2.1.3 used the operators $T_n$ of Definition 1.5.10 and the relation $T_{mn} = T_mT_n$ for coprime $m$ and $n$. This relation is part of the definition, and its consistency rests on Theorem 1.5.9. This subsection proves the same consequences from the operators $T_p$ alone, through their action on $q$-expansions. The proof works with the coefficients only, and it is the proof in the Lean project. For a prime $p$ we put $c_p = \chi(p)p^{k-1}$, so $c_p = 0$ for $p \mid N$. For a form on $\Gamma_0(N)$, that is, for the trivial character, $c_p = \varepsilon_p\, p^{k-1}$ with $\varepsilon_p$ as in Section 1.5. As before, $a_{m/p} = 0$ when $p \nmid m$.

**Definition 2.1.12 (Hecke relations).** A sequence $a = (a_n)_{n \ge 0}$ of complex numbers satisfies the *Hecke relations* of weight $k$ and character $\chi$ if
$$a_{mp} + c_p\, a_{m/p} = a_p\, a_m$$
for every prime $p$ and every $m \ge 0$. We call the relation for $p$ and $m$ the relation $(E_{p,m})$.

Lean: `Langlands.Modular.IsHeckeEigenSeq`, for the trivial character modulo $N$

**Lemma 2.1.13 (eigenforms satisfy the Hecke relations).** Let $f \in S_k(N, \chi)$ with $a_1(f) = 1$, and let $p$ be a prime with $T_pf = \lambda f$. Then $\lambda = a_p(f)$, and the coefficients of $f$ satisfy the relations $(E_{p,m})$ for all $m$. So if $f$ is an eigenvector of every $T_p$, its coefficients satisfy the Hecke relations.

Lean: `Langlands.Modular.heckeCoeff_qCoeff_of_eigenvector`, `Langlands.Modular.eigenvalue_eq_qCoeff` and `Langlands.Modular.IsNormalizedHeckeEigenform.isHeckeEigenSeq`, on $S_k(\Gamma_0(N))$

*Proof.* By Theorem 1.5.8, $a_m(T_pf) = a_{mp} + c_p a_{m/p}$, and $a_m(T_pf) = \lambda a_m$. For $m = 1$ the term $a_{1/p}$ is 0, so $\lambda = \lambda a_1 = a_p$. Then the equation for general $m$ is $(E_{p,m})$. $\square$

**Theorem 2.1.14 (multiplicativity).** Let $a$ satisfy the Hecke relations, with $a_1 = 1$.
1. For each prime $p$ and $r \ge 0$, $a_{p^{r+2}} = a_pa_{p^{r+1}} - c_pa_{p^r}$.
2. For each prime $p$, each $m \ge 1$ with $p \nmid m$ and each $r \ge 0$, $a_{p^rm} = a_{p^r}a_m$.
3. For all coprime $m, n \ge 1$, $a_{mn} = a_ma_n$.

Lean: `Langlands.Modular.IsHeckeEigenSeq.pow_succ_succ`, `Langlands.Modular.IsHeckeEigenSeq.pow_mul` and `Langlands.Modular.IsHeckeEigenSeq.mul`

*Proof.* Part 1 is the relation $(E_{p, p^{r+1}})$, since $p^{r+1}/p = p^r$.

Part 2 is the $p$-part induction. We prove it by induction on $r$, using the two previous cases at each step. For $r = 0$ it says $a_m = a_1a_m$. For $r = 1$ it is the relation $(E_{p,m})$, whose second term vanishes because $p \nmid m$: $a_{pm} = a_pa_m$. Let $r \ge 0$ and assume part 2 for $r$ and $r + 1$. The relation $(E_{p, p^{r+1}m})$ reads
$$a_{p^{r+2}m} + c_p\, a_{p^rm} = a_p\, a_{p^{r+1}m}.$$
By the induction hypothesis, $a_{p^rm} = a_{p^r}a_m$ and $a_{p^{r+1}m} = a_{p^{r+1}}a_m$. So
$$a_{p^{r+2}m} = \left(a_pa_{p^{r+1}} - c_pa_{p^r}\right)a_m = a_{p^{r+2}}a_m,$$
by part 1. This is part 2 for $r + 2$.

Part 3 follows by induction on the number $s$ of distinct primes that divide $n$. If $s = 0$, then $n = 1$ and the claim is $a_m = a_ma_1$. Let $s \ge 1$. Choose a prime $p \mid n$ and write $n = p^rn'$ with $r \ge 1$ and $p \nmid n'$. Then $n'$ has $s - 1$ prime divisors, and $\gcd(m, n') = 1$. Since $p \nmid m$, we have $p \nmid mn'$. By part 2, then by the induction hypothesis, then by part 2 again,
$$a_{mn} = a_{p^r \cdot mn'} = a_{p^r}a_{mn'} = a_{p^r}a_ma_{n'} = a_m\,a_{p^rn'} = a_ma_n. \qquad \square$$

The proof uses only the relations $(E_{p,m})$ at single primes. Each relation is the equation $T_pf = a_pf$ read at one coefficient, so the theorem needs no relation between different operators. In particular it does not use Theorem 1.5.9.

**Corollary 2.1.15 (normalized eigenforms of the $T_p$).** Let $f \in S_k(\Gamma_0(N))$ be nonzero, with $a_1(f) = 1$, and let $f$ be an eigenvector of $T_p$ for every prime $p$, where $T_p = U_p$ for $p \mid N$. Then `Langlands.IsNormalizedEigenform f` holds. More generally, if $f \in S_k(N, \chi)$ is an eigenvector of every $T_p$ with $a_1(f) = 1$, then its coefficients satisfy the three conditions of Theorem 2.1.3.

Lean: `Langlands.Modular.IsNormalizedHeckeEigenform.toIsNormalizedEigenform`, with `Langlands.Modular.IsNormalizedHeckeEigenform.mul`, `Langlands.Modular.IsNormalizedHeckeEigenform.good` and `Langlands.Modular.IsNormalizedHeckeEigenform.bad` for the fields

*Proof.* By Lemma 2.1.13 the coefficients satisfy the Hecke relations. Theorem 2.1.14 gives the fields `mul` and, with $c_p = p^{k-1}$ for $p \nmid N$ and $c_p = 0$ for $p \mid N$, the fields `good` and `bad` of Definition 2.1.4. The field `one` is the hypothesis. $\square$

In Lean the hypothesis is the predicate `Langlands.Modular.IsNormalizedHeckeEigenform f`. It asks that $f \ne 0$, that for each prime $\ell$ there is $c \in \mathbb{C}$ with $T_\ell f = cf$, and that $a_1(f) = 1$. The condition $f \ne 0$ follows from $a_1(f) = 1$, and the proof does not use it.

### The Hecke recursion at prime powers

The relation of part 1 of Theorem 2.1.14 computes $a_{p^r}$ from $a_p$. The next proposition gives the product of two coefficients at powers of $p$. It is the identity behind the formula for $T_n$ on $q$-expansions.

**Proposition 2.1.16 (products at prime powers).** Let $a$ satisfy the Hecke relations, with $a_1 = 1$, and let $p$ be a prime. For all $\alpha, \beta \ge 0$,
$$a_{p^{\alpha+1}}a_{p^{\beta+1}} = a_{p^{\alpha+\beta+2}} + c_p\, a_{p^\alpha}a_{p^\beta}, \qquad a_{p^\alpha}a_{p^\beta} = \sum_{j=0}^{\min(\alpha, \beta)} c_p^j\, a_{p^{\alpha+\beta-2j}}.$$

Lean: `Langlands.Modular.IsHeckeEigenSeq.pow_succ_mul_pow_succ` and `Langlands.Modular.IsHeckeEigenSeq.sum_range_min`

*Proof.* Write $b_r = a_{p^r}$ and $c = c_p$. So $b_0 = 1$ and $b_{r+2} = b_1b_{r+1} - cb_r$ by Theorem 2.1.14. We prove the first identity for all $\alpha$ by induction on $\beta$. For $\beta = 0$ it reads $b_{\alpha+1}b_1 = b_{\alpha+2} + cb_\alpha$, which is the recursion. Assume the identity for $\beta$ and all $\alpha$. With the recursion for $b_{\beta+2}$, then for $b_1b_{\alpha+1}$, and then the induction hypothesis for $\alpha + 1$ and $\beta$, we get
$$b_{\alpha+1}b_{\beta+2} = b_1b_{\alpha+1}b_{\beta+1} - cb_{\alpha+1}b_\beta = b_{\alpha+2}b_{\beta+1} + cb_\alpha b_{\beta+1} - cb_{\alpha+1}b_\beta = b_{\alpha+\beta+3} + cb_\alpha b_{\beta+1}.$$
This is the identity for $\beta + 1$.

The second identity follows by induction on $\min(\alpha, \beta)$. If $\alpha = 0$ or $\beta = 0$ it reads $b_\alpha b_\beta = b_{\alpha+\beta}$, which is true since $b_0 = 1$. Otherwise the first identity and the induction hypothesis give
$$b_{\alpha+1}b_{\beta+1} = b_{\alpha+\beta+2} + c\sum_{j=0}^{\min(\alpha,\beta)} c^j b_{\alpha+\beta-2j} = \sum_{j=0}^{\min(\alpha,\beta)+1} c^j b_{\alpha+\beta+2-2j}. \qquad \square$$

For $p \mid N$ we have $c_p = 0$, and the proposition reduces to $a_{p^\alpha}a_{p^\beta} = a_{p^{\alpha+\beta}}$. For $p \nmid N$ let $\alpha_p, \beta_p$ be the roots of $X^2 - a_pX + c_p$. The recursion gives $a_{p^r} = \sum_{i=0}^{r}\alpha_p^i\beta_p^{r-i}$, so $a_{p^r}$ is the value of the character of $\mathrm{Sym}^r$ of the standard representation of $GL_2$ at a matrix with eigenvalues $\alpha_p, \beta_p$. The second identity of the proposition is then the decomposition $\mathrm{Sym}^\alpha \otimes \mathrm{Sym}^\beta = \bigoplus_j \det^j \otimes \mathrm{Sym}^{\alpha+\beta-2j}$, the Clebsch-Gordan rule. Exercise 18 proves it in this form.

### $T_n$ on $q$-expansions

**Definition 2.1.17 ($T_n$ on sequences).** For $n \ge 1$ and a sequence $a = (a_m)_{m \ge 0}$ let $T_na$ be the sequence
$$(T_na)_m = \sum_{d \mid \gcd(m, n)} \chi(d)\, d^{k-1}\, a_{mn/d^2},$$
where for $m = 0$ the sum runs over all $d \mid n$.

Lean: `Langlands.Modular.heckeSeq`, for the trivial character, where $d$ runs over the divisors of $n$ that are prime to $N$ and divide $m$

By Proposition 1.5.11, $a(T_nf) = T_n\,a(f)$ for $f \in S_k(N, \chi)$. For the trivial character modulo $N$ the factor $\chi(d)$ is 1 if $\gcd(d, N) = 1$ and 0 otherwise, so the definition agrees with the Lean definition. For $n = p$ the sequence $T_pa$ is the sequence $h_pa$ of the proof of Theorem 1.5.19, with $\chi(p)$ in place of $\varepsilon_p$.

**Theorem 2.1.18 ($T_n$ on the coefficients of an eigenform).** Let $a$ satisfy the Hecke relations, with $a_1 = 1$. Then $(T_na)_m = a_na_m$ for all $m, n \ge 1$, that is,
$$a_ma_n = \sum_{d \mid \gcd(m, n)} \chi(d)\, d^{k-1}\, a_{mn/d^2}.$$

Lean: `Langlands.Modular.IsHeckeEigenSeq.heckeSeq_eq`, with `Langlands.Modular.IsHeckeEigenSeq.heckeSeq_prime_pow` and `Langlands.Modular.IsHeckeEigenSeq.heckeSeq_mul` for the two steps

*Proof.* First let $n = p^\beta$ for a prime $p$. Write $m = p^\alpha m'$ with $p \nmid m'$. The common divisors of $m$ and $n$ are the $p^j$ with $0 \le j \le \min(\alpha, \beta)$. For such $j$ we have $\chi(p^j)p^{j(k-1)} = c_p^j$ and $mn/p^{2j} = p^{\alpha+\beta-2j}m'$. By Theorem 2.1.14 and Proposition 2.1.16,
$$(T_{p^\beta}a)_m = \sum_{j=0}^{\min(\alpha,\beta)} c_p^j\, a_{p^{\alpha+\beta-2j}}\, a_{m'} = a_{p^\alpha}a_{p^\beta}a_{m'} = a_{p^\beta}a_m.$$

Now let $n = xy$ with coprime $x, y \ge 1$, and assume the claim for $x$ and for $y$ and all $m \ge 1$. The map $(d_1, d_2) \mapsto d_1d_2$ is a bijection from the pairs of divisors of $x$ and of $y$ to the divisors of $xy$. Let $d_1 \mid x$ and $d_2 \mid y$. Then $d_2$ is prime to $d_1$ and to $x/d_1$. So $d_1d_2 \mid m$ if and only if $d_1 \mid m$ and $d_2 \mid (m/d_1)(x/d_1)$, that is, $d_2 \mid mx/d_1^2$. Also $\chi(d_1d_2)(d_1d_2)^{k-1} = \chi(d_1)d_1^{k-1}\chi(d_2)d_2^{k-1}$ and $mxy/(d_1d_2)^2 = (mx/d_1^2)\,y/d_2^2$. Hence
$$(T_{xy}a)_m = \sum_{d_1 \mid \gcd(m, x)} \chi(d_1)d_1^{k-1}\,(T_ya)_{mx/d_1^2} = \sum_{d_1 \mid \gcd(m, x)} \chi(d_1)d_1^{k-1}\,a_y\,a_{mx/d_1^2} = a_y\,(T_xa)_m = a_ya_xa_m.$$
Here we used the claim for $y$ at $mx/d_1^2 \ge 1$ and then for $x$ at $m$. By Theorem 2.1.14, $a_ya_x = a_{xy}$. Every $n \ge 1$ is a product of prime powers for distinct primes, so the two steps prove the theorem. $\square$

**Corollary 2.1.19 (eigenforms of the $T_p$ are eigenforms of the $T_n$).** Let $f \in S_k(N, \chi)$ be an eigenvector of $T_p$ for every prime $p$, with $a_1(f) = 1$. Then $T_nf = a_n(f)f$ for every $n \ge 1$. Equivalently, $a_m(f)a_n(f) = \sum_{d \mid \gcd(m, n)}\chi(d)d^{k-1}a_{mn/d^2}(f)$ for all $m \ge 0$ and $n \ge 1$.

Lean: `Langlands.Modular.IsNormalizedHeckeEigenform.heckeSeq_qCoeff`, for the identity of coefficients on $S_k(\Gamma_0(N))$

*Proof.* By Lemma 2.1.13 the coefficients satisfy the Hecke relations, and Theorem 2.1.18 gives the identity for $m \ge 1$. For $m = 0$ both sides are 0, because $a_0(f) = 0$ for a cusp form. By Proposition 1.5.11 the right side is $a_m(T_nf)$. So $T_nf$ and $a_n(f)f$ have the same $q$-expansion, and they are equal. $\square$

The corollary proves again that an eigenvector of all the $T_p$ is an eigenvector of all the $T_n$, as was said after Definition 2.1.1. In Lean the identity of coefficients is proved here, and the identity $T_nf = a_n(f)f$ of operators on $S_k(\Gamma_0(N))$ is Corollary 1.5.30, which combines it with Theorem 1.5.28.

**Example 2.1.20 (the relations for $\tau$).** Let $f = \Delta$, with $N = 1$, $k = 12$ and $c_p = p^{11}$. By Example 1.5.20, $\tau(2) = -24$ and $\tau(4) = -1472$. Theorem 2.1.14 gives $\tau(6) = \tau(2)\tau(3) = -24 \cdot 252 = -6048$, and part 1 gives
$$\tau(8) = \tau(2)\tau(4) - 2^{11}\tau(2) = 35328 + 49152 = 84480, \qquad \tau(16) = \tau(2)\tau(8) - 2^{11}\tau(4) = -2027520 + 3014656 = 987136.$$
Theorem 2.1.18 for $m = n = 4$ gives three terms, for $d = 1, 2, 4$:
$$\tau(4)^2 = \tau(16) + 2^{11}\tau(4) + 2^{22}\tau(1).$$
Both sides are $2166784$, since $987136 - 3014656 + 4194304 = 2166784$. For $m = 2$ and $n = 6$ the common divisors are 1 and 2, and the theorem gives $\tau(2)\tau(6) = \tau(12) + 2^{11}\tau(3)$. With $\tau(12) = \tau(3)\tau(4) = -370944$ both sides are $145152$.

**Remark 2.1.21 (what Lean proves about eigenforms, and what is open).** The file `Langlands/Modular/HeckeMul.lean` proves Lemma 2.1.13, Theorem 2.1.14, Proposition 2.1.16, Theorem 2.1.18 and Corollaries 2.1.15 and 2.1.19 for $S_k(\Gamma_0(N))$, that is, for the trivial character. With `Langlands.Modular.IsNormalizedHeckeEigenform.good` and `Langlands.Modular.IsNormalizedHeckeEigenform.bad` of `Langlands/Modular/Hecke.lean`, the theorem `Langlands.Modular.IsNormalizedHeckeEigenform.toIsNormalizedEigenform` gives all the fields of `Langlands.IsNormalizedEigenform`. So the predicate of Definition 2.1.4 is now a consequence of the definition of an eigenform by operators, and it is not only a definition by coefficients. The following parts of the theory of this section and of Section 1.5 are still open in Lean.
1. The operators $T_n$ by double cosets. The file `Langlands/Modular/HeckeTn.lean` defines $T_n$ on $S_k(\Gamma_0(N))$ from the $T_p$, proves $T_{mn} = T_mT_n$ for coprime $m$ and $n$ and the recursion of Definition 1.5.10, and computes the coefficients of $T_nf$, see Theorems 1.5.25 and 1.5.28. It does not define $T_n$ by the double coset of the matrices of determinant $n$.
2. The operators $T_n$ on $M_k(\Gamma_0(N))$. They are defined only on cusp forms.
3. The converse direction of Theorem 2.1.3: a cusp form whose coefficients satisfy `Langlands.IsNormalizedEigenform` is an eigenvector of each $T_p$. The proof above needs only Theorem 1.5.18 and the uniqueness of $q$-expansions, but it is not written in Lean.
4. The case of a character. There are no diamond operators and no operators on $S_k(\Gamma_1(N))$, so `Langlands.IsNormalizedEigenformWithCharacter` is not connected to any operator.
5. Newforms. The forms $g(d\tau)$ of lower level and the space of oldforms are defined for $\Gamma_0(N)$, see Definitions 1.5.34 and 1.5.36. The newforms need the Petersson inner product on $S_k(\Gamma_1(N))$, and Theorem 2.1.8 and Proposition 2.1.10 are not stated.
6. The Sturm bound. Sturm proved that a form $f \in M_k(\Gamma_0(N))$ with $a_n(f) = 0$ for all $n \le km/12$, where $m = [SL_2(\mathbb{Z}) : \Gamma_0(N)]$, is zero. Exercise 7 of Chapter 1 is the case $N = 1$. With this bound one can check that a given form is an eigenform from finitely many coefficients. It is not in Lean, and the project still has no proof of `Langlands.Bridge.DeltaIsEigenform` of Remark 2.3.5.
