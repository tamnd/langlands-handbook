---
title: Hecke operators
nodes: []
sources: []
status: drafted
drafted_by: writer
reviewed_by: []
---
## Hecke operators

This section defines the diamond operators and the Hecke operators $T_p$ on $M_k(\Gamma_1(N))$. Both come from double cosets. We compute the action of $T_p$ on $q$-expansions and deduce that all these operators commute. We follow Diamond and Shurman, Chapter 5, and we fix the level $N \ge 1$. We write $\Gamma_1$ for $\Gamma_1(N)$ and $\Gamma_0$ for $\Gamma_0(N)$.

### Double cosets

**Lemma 1.5.1 (double cosets).** Let $\Gamma$ be a congruence subgroup and $\alpha \in GL_2^+(\mathbb{Q})$.
1. The double coset $\Gamma\alpha\Gamma$ is a finite disjoint union $\bigsqcup_{j=1}^n \Gamma\beta_j$ of right cosets, and $n = [\Gamma : \Gamma \cap \alpha^{-1}\Gamma\alpha]$.
2. For $f \in M_k(\Gamma)$ the function $f|_k[\Gamma\alpha\Gamma] = \sum_{j} f|_k \beta_j$ does not depend on the choice of the $\beta_j$. It is in $M_k(\Gamma)$, and it is in $S_k(\Gamma)$ if $f$ is.

Lean: not stated yet

*Proof.* The map $\gamma \mapsto \Gamma\alpha\gamma$ from $\Gamma$ to the set of right cosets in $\Gamma\alpha\Gamma$ is surjective. Two elements $\gamma, \gamma'$ have the same image if and only if $\alpha\gamma'\gamma^{-1}\alpha^{-1} \in \Gamma$, that is, $\gamma'\gamma^{-1} \in \Gamma \cap \alpha^{-1}\Gamma\alpha$. So the cosets correspond to $(\Gamma \cap \alpha^{-1}\Gamma\alpha)\backslash\Gamma$. This group is a congruence subgroup by Lemma 1.2.7, so it contains some $\Gamma(M)$ and has finite index. For part 2, $f|\gamma\beta_j = f|\beta_j$ for $\gamma \in \Gamma$, so the sum does not depend on the representatives. For $\gamma \in \Gamma$, right multiplication by $\gamma$ permutes the cosets $\Gamma\beta_j$, so the $\beta_j\gamma$ are again representatives and $f|[\Gamma\alpha\Gamma]|\gamma = f|[\Gamma\alpha\Gamma]$. Each $f|\beta_j$ is holomorphic at the cusps, and vanishes at the cusps if $f$ does, by Lemma 1.2.7. $\square$

### Diamond operators and characters

By Definition 1.1.6, $\Gamma_1$ is the kernel of the homomorphism $\Gamma_0 \to (\mathbb{Z}/N\mathbb{Z})^\times$ that sends $\begin{pmatrix} a & b \\ c & d \end{pmatrix}$ to $d \bmod N$. The homomorphism is surjective: by Lemma 1.1.7, the matrix $\begin{pmatrix} d^{-1} & 0 \\ 0 & d \end{pmatrix}$ modulo $N$ lifts to $SL_2(\mathbb{Z})$, and the lift is in $\Gamma_0$.

**Definition 1.5.2 (diamond operators and nebentypus).** Let $d \in (\mathbb{Z}/N\mathbb{Z})^\times$. The *diamond operator* $\langle d \rangle$ on $M_k(\Gamma_1)$ is $\langle d \rangle f = f|_k\gamma$, for any $\gamma \in \Gamma_0$ with lower right entry congruent to $d$ modulo $N$. We put $\langle d \rangle = 0$ if $\gcd(d, N) > 1$. Let $\chi$ be a Dirichlet character modulo $N$. The space of modular forms of *nebentypus* $\chi$ is
$$M_k(N, \chi) = \{ f \in M_k(\Gamma_1) : \langle d \rangle f = \chi(d) f \text{ for all } d \in (\mathbb{Z}/N\mathbb{Z})^\times \},$$
and $S_k(N, \chi) = M_k(N, \chi) \cap S_k(\Gamma_1)$.

The operator is well defined. Since $\Gamma_1$ is normal in $\Gamma_0$, $f|\gamma$ is modular for $\gamma^{-1}\Gamma_1\gamma = \Gamma_1$, and two choices of $\gamma$ differ by an element of $\Gamma_1$. The map $d \mapsto \langle d\rangle$ is an action of the group $(\mathbb{Z}/N\mathbb{Z})^\times$. A form $f$ is in $M_k(N, \chi)$ if and only if $f|_k \gamma = \chi(d) f$ for all $\gamma \in \Gamma_0$ with lower right entry $d$. In particular $M_k(N, \mathbf{1}) = M_k(\Gamma_0(N))$ for the trivial character $\mathbf{1}$.

**Proposition 1.5.3 (decomposition by characters).** We have
$$M_k(\Gamma_1(N)) = \bigoplus_{\chi} M_k(N, \chi), \qquad S_k(\Gamma_1(N)) = \bigoplus_{\chi} S_k(N, \chi),$$
where $\chi$ runs over the Dirichlet characters modulo $N$. If $\chi(-1) \ne (-1)^k$, then $M_k(N, \chi) = 0$.

Lean: not stated yet

*Proof.* The group $G = (\mathbb{Z}/N\mathbb{Z})^\times$ is finite and abelian, and it acts linearly on the space $M_k(\Gamma_1)$. The operators $e_\chi = |G|^{-1} \sum_{d \in G} \overline{\chi(d)} \langle d \rangle$ satisfy $\sum_\chi e_\chi = 1$ and $\langle d \rangle e_\chi = \chi(d) e_\chi$, by the orthogonality relations for characters. So $e_\chi$ is a projection onto $M_k(N, \chi)$, and the sum is direct. The operators preserve $S_k(\Gamma_1)$. For the last claim, $-I \in \Gamma_0$ has lower right entry $-1$, and $f|(-I) = (-1)^k f$ by Lemma 1.2.2. $\square$

**Remark 1.5.4 (nebentypus in Lean).** The Lean project defines `Langlands.HasNebentypus f χ`, for a cusp form `f : CuspForm (Gamma1 N) k` and `χ : DirichletCharacter ℂ N`, by the condition $f|_k\gamma = \chi(d) f$ for all $\gamma \in \Gamma_0(N)$, where $d$ is the lower right entry of $\gamma$. This is the condition $f \in S_k(N, \chi)$ of Definition 1.5.2. A Lean `DirichletCharacter` takes the value 0 at the residues that are not units, as our convention does.

### The operators $T_p$

Let $p$ be a prime. Let
$$\Delta_p = \left\{ \beta = \begin{pmatrix} a & b \\ c & d \end{pmatrix} \in M_2(\mathbb{Z}) : \det\beta = p,\ a \equiv 1 \text{ and } c \equiv 0 \bmod N \right\}.$$
A product of an element of $\Gamma_1$ and an element of $\Delta_p$, in either order, is in $\Delta_p$, because modulo $N$ all these matrices are upper triangular and their upper left entries multiply. So $\Gamma_1$ acts on $\Delta_p$ on the left and on the right. Let $\alpha = \begin{pmatrix} 1 & 0 \\ 0 & p \end{pmatrix} \in \Delta_p$. If $p \nmid N$, fix integers $m, n$ with $mp - nN = 1$.

**Lemma 1.5.5 (representatives).** The set $\Delta_p$ is the double coset $\Gamma_1\alpha\Gamma_1$. A set of representatives of $\Gamma_1\backslash\Delta_p$ is given by the matrices
$$\beta_j = \begin{pmatrix} 1 & j \\ 0 & p \end{pmatrix} \text{ for } 0 \le j < p, \qquad \text{and, if } p \nmid N, \qquad \beta_\infty = \begin{pmatrix} mp & n \\ Np & p \end{pmatrix}.$$

Lean: not stated yet

*Proof.* Let $\beta \in \Delta_p$ have first column $(a, c)$, and let $g = \gcd(a, c)$. Then $g$ divides $\det\beta = p$. Left multiplication by $SL_2(\mathbb{Z})$ does not change $g$, so $\beta_j$ and $\beta_\infty$ are in different cosets, since their values of $g$ are 1 and $p$.

Let $g = 1$. The vectors $(a, c)$ and $(1, 0)$ are primitive and congruent modulo $N$. By Lemma 1.1.7 there is $\gamma \in \Gamma(N) \subset \Gamma_1$ with $\gamma(a, c)^t = (1, 0)^t$. Then $\gamma\beta = \begin{pmatrix} 1 & b' \\ 0 & p \end{pmatrix}$, and multiplication on the left by $\begin{pmatrix} 1 & t \\ 0 & 1 \end{pmatrix} \in \Gamma_1$ changes $b'$ to $b' + tp$. So $\beta \in \Gamma_1\beta_j$ with $j \equiv b' \bmod p$. If $\Gamma_1\beta_j = \Gamma_1\beta_{j'}$, then $\beta_{j'}\beta_j^{-1} = \begin{pmatrix} 1 & (j'-j)/p \\ 0 & 1 \end{pmatrix}$ has integer entries, so $j = j'$.

Let $g = p$. Then $p \mid a$, so $p \nmid N$ because $a \equiv 1 \bmod N$. The vectors $(a/p, c/p)$ and $(m, N)$ are primitive, and both are congruent to $(p^{-1}, 0)$ modulo $N$, because $mp \equiv 1$. By Lemma 1.1.7 there is $\gamma \in \Gamma(N)$ with $\gamma\beta = \begin{pmatrix} mp & b'' \\ Np & d'' \end{pmatrix}$. The determinant gives $md'' - Nb'' = 1 = mp - Nn$, so $(d'', b'') = (p + Ns, n + ms)$ for some $s \in \mathbb{Z}$. A direct computation gives
$$\gamma\beta\beta_\infty^{-1} = \begin{pmatrix} 1 - Nms & m^2 s \\ -N^2 s & 1 + Nms \end{pmatrix} \in \Gamma_1,$$
so $\beta \in \Gamma_1\beta_\infty$.

Finally, $\Gamma_1\alpha\Gamma_1 \subset \Delta_p$, and the representatives are in $\Gamma_1\alpha\Gamma_1$: we have $\beta_j = \alpha\begin{pmatrix} 1 & j \\ 0 & 1 \end{pmatrix}$ and $\beta_\infty = \alpha\begin{pmatrix} mp & n \\ N & 1 \end{pmatrix}$, and the second factors are in $\Gamma_1$. So $\Delta_p = \Gamma_1\alpha\Gamma_1$. $\square$

**Definition 1.5.6 (the Hecke operator $T_p$).** For $f \in M_k(\Gamma_1(N))$ let
$$T_p f = f|_k[\Gamma_1\alpha\Gamma_1] = \sum_{\beta \in \Gamma_1\backslash\Delta_p} f|_k\beta.$$
If $p \mid N$, we also write $U_p$ for $T_p$.

By Lemma 1.5.1, $T_p$ is a linear operator on $M_k(\Gamma_1)$ that preserves $S_k(\Gamma_1)$.

**Proposition 1.5.7 (the formula for $T_p$).** For $f \in M_k(\Gamma_1(N))$,
$$T_p f = \sum_{j=0}^{p-1} f|_k\begin{pmatrix} 1 & j \\ 0 & p \end{pmatrix} + (\langle p \rangle f)|_k\begin{pmatrix} p & 0 \\ 0 & 1 \end{pmatrix},$$
where the last term is 0 if $p \mid N$. The operator $T_p$ commutes with each $\langle d \rangle$, so it preserves each space $M_k(N, \chi)$.

Lean: not stated yet

*Proof.* The formula follows from Lemma 1.5.5 and $\beta_\infty = \begin{pmatrix} m & n \\ N & p \end{pmatrix}\begin{pmatrix} p & 0 \\ 0 & 1 \end{pmatrix}$, where the first factor is in $\Gamma_0$ with lower right entry $p$. Let $\gamma \in \Gamma_0$. Modulo $N$, conjugation by $\gamma$ preserves the upper triangular matrices and their upper left entries, so $\gamma^{-1}\Delta_p\gamma = \Delta_p$. Since $\Gamma_1$ is normal in $\Gamma_0$, the map $\Gamma_1\beta \mapsto \Gamma_1\gamma^{-1}\beta\gamma$ is a bijection of $\Gamma_1\backslash\Delta_p$. So
$$(T_p f)|\gamma = \sum_\beta f|\beta\gamma = \sum_\beta (f|\gamma)|(\gamma^{-1}\beta\gamma) = T_p(f|\gamma). \qquad \square$$

**Theorem 1.5.8 ($T_p$ on $q$-expansions).** Let $f \in M_k(N, \chi)$ with $q$-expansion $\sum_{n \ge 0} a_n(f) q^n$. Then
$$a_n(T_p f) = a_{np}(f) + \chi(p) p^{k-1} a_{n/p}(f) \qquad (n \ge 0),$$
where $a_{n/p}(f) = 0$ if $p \nmid n$, and $\chi(p) = 0$ if $p \mid N$. In particular $a_n(U_p f) = a_{np}(f)$ for $p \mid N$.

Lean: not stated yet

*Proof.* We have $(f|\beta_j)(\tau) = p^{k-1} p^{-k} f((\tau + j)/p)$. So
$$\sum_{j=0}^{p-1} (f|\beta_j)(\tau) = \frac{1}{p} \sum_{n \ge 0} a_n(f) e^{2\pi i n\tau/p} \sum_{j=0}^{p-1} e^{2\pi i nj/p} = \sum_{p \mid n} a_n(f) q^{n/p} = \sum_{n \ge 0} a_{np}(f) q^n,$$
because the inner sum is $p$ if $p \mid n$ and 0 otherwise. If $p \nmid N$, then $\langle p\rangle f = \chi(p) f$ and $(f|\begin{pmatrix} p & 0 \\ 0 & 1\end{pmatrix})(\tau) = p^{k-1} f(p\tau) = p^{k-1}\sum_n a_n(f) q^{pn}$. $\square$

**Theorem 1.5.9 (commutativity).** The operators $T_p$, for all primes $p$, and $\langle d \rangle$, for all $d$, on $M_k(\Gamma_1(N))$ commute with each other.

Lean: not stated yet

*Proof.* The diamond operators commute with each other because $(\mathbb{Z}/N\mathbb{Z})^\times$ is abelian, and with each $T_p$ by Proposition 1.5.7. By Propositions 1.5.3 and 1.5.7 it suffices to prove $T_pT_q f = T_qT_p f$ for $f \in M_k(N, \chi)$ and primes $p \ne q$. A form is determined by its $q$-expansion. By Theorem 1.5.8, applied twice,
$$a_n(T_pT_q f) = a_{npq}(f) + \chi(q)q^{k-1} a_{np/q}(f) + \chi(p)p^{k-1} a_{nq/p}(f) + \chi(pq)(pq)^{k-1} a_{n/pq}(f).$$
This is symmetric in $p$ and $q$. $\square$

### The operators $T_n$

**Definition 1.5.10 (the operators $T_n$).** Define $T_n$ for $n \ge 1$ by $T_1 = 1$, by $T_{p^r} = T_pT_{p^{r-1}} - p^{k-1}\langle p\rangle T_{p^{r-2}}$ for primes $p$ and $r \ge 2$, and by $T_{mn} = T_mT_n$ for coprime $m$ and $n$. The *Hecke algebra* $\mathbb{T}$ is the subalgebra of $\mathrm{End}(S_k(\Gamma_1(N)))$ generated by all $T_n$ and $\langle d \rangle$.

By Theorem 1.5.9 the definition is consistent, and $\mathbb{T}$ is commutative. On $M_k(N, \chi)$ the recursion reads $T_{p^r} = T_pT_{p^{r-1}} - \chi(p)p^{k-1}T_{p^{r-2}}$. For $p \mid N$ it gives $T_{p^r} = U_p^r$.

**Proposition 1.5.11 ($T_n$ on $q$-expansions).** Let $f \in M_k(N, \chi)$ and $n \ge 1$. Then
$$a_m(T_n f) = \sum_{d \mid \gcd(m, n)} \chi(d) d^{k-1} a_{mn/d^2}(f) \qquad (m \ge 0),$$
where for $m = 0$ the sum runs over all $d \mid n$. In particular $a_1(T_n f) = a_n(f)$.

Lean: not stated yet

*Proof.* First let $n = p^r$, and write $v = v_p(m)$. The claim is $a_m(T_{p^r}f) = \sum_{j=0}^{\min(r, v)} c_{r,j}$ with $c_{r,j} = \chi(p)^j p^{j(k-1)} a_{mp^{r-2j}}(f)$. It holds for $r = 0$, and for $r = 1$ it is Theorem 1.5.8. Assume it for $r$ and $r - 1$, and let $g = T_{p^r}f$. By Theorem 1.5.8 and the recursion,
$$a_m(T_{p^{r+1}}f) = a_{mp}(g) + \chi(p)p^{k-1}a_{m/p}(g) - \chi(p)p^{k-1}a_m(T_{p^{r-1}}f).$$
By the induction hypothesis the three terms are $\sum_{0 \le j \le \min(r, v+1)} c_{r+1, j}$, then $\sum_{1 \le j \le \min(r+1, v)} c_{r+1,j}$, and minus $\sum_{1 \le j \le \min(r, v+1)} c_{r+1,j}$. The sum is $\sum_{0 \le j \le \min(r+1, v)} c_{r+1,j}$, as claimed. For $m = 0$ the same computation holds with $v = \infty$.

Now let $n = n_1n_2$ with $\gcd(n_1, n_2) = 1$, and assume the formula for $n_1$ and $n_2$. Then
$$a_m(T_{n_1}T_{n_2}f) = \sum_{d_1 \mid (m, n_1)} \chi(d_1)d_1^{k-1} \sum_{d_2 \mid (mn_1/d_1^2,\, n_2)} \chi(d_2)d_2^{k-1} a_{mn/(d_1d_2)^2}(f).$$
Since $n_2$ is coprime to $n_1$, the condition $d_2 \mid (mn_1/d_1^2, n_2)$ is equivalent to $d_2 \mid (m, n_2)$. The products $d = d_1d_2$ run once over the divisors of $\gcd(m, n)$, and $\chi(d_1)\chi(d_2) = \chi(d)$. $\square$

**Example 1.5.12 (Eisenstein series are eigenforms).** Let $N = 1$ and $k \ge 4$ even. Then $T_n E_k = \sigma_{k-1}(n) E_k$ for each $n$. By Proposition 1.5.11 and multiplicativity it suffices to check that $a_m(T_p E_k) = \sigma_{k-1}(p) a_m(E_k)$ for primes $p$. For $m = 0$ this is $a_0(T_pE_k) = 1 + p^{k-1}$. For $m \ge 1$ with $v = v_p(m)$ and $m = p^v m'$, we need $\sigma_{k-1}(p^{v+1}) + p^{k-1}\sigma_{k-1}(p^{v-1}) = (1 + p^{k-1})\sigma_{k-1}(p^v)$, with $\sigma_{k-1}(p^{-1}) = 0$. Both sides equal $\sum_{i=0}^{v} p^{i(k-1)} + \sum_{i=1}^{v+1} p^{i(k-1)}$.

**Remark 1.5.13 (Hecke operators in Mathlib and in the Lean project).** Mathlib does not yet define Hecke operators. For this reason the Lean project does not state "$f$ is an eigenvector of $T_n$". It states the consequences of this property for the $q$-expansion, which Section 2.1 proves to be equivalent. The operators $U_p$ for $p \mid N$ need not be diagonalizable on $S_k(\Gamma_1(N))$, see Remark 1.6.7. Example 2.1.9 shows that they can have eigenforms that are not newforms.
