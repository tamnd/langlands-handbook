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

Lean: `ModularForm.trace` and `ModularForm.translate`, from Mathlib, for part 2 with $\Gamma = \Gamma_0(N)$ and $\beta_j = \alpha\gamma_j$, see Definition 1.5.14 and Proposition 1.5.15

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

Lean: not stated yet for $\Gamma_1(N)$; for the cosets of $\Gamma_0(N)$, `Langlands.Modular.bijective_cosetMk_tRep` and `Langlands.Modular.bijective_cosetRep`, see Lemma 1.5.16

*Proof.* Let $\beta \in \Delta_p$ have first column $(a, c)$, and let $g = \gcd(a, c)$. Then $g$ divides $\det\beta = p$. Left multiplication by $SL_2(\mathbb{Z})$ does not change $g$, so $\beta_j$ and $\beta_\infty$ are in different cosets, since their values of $g$ are 1 and $p$.

Let $g = 1$. The vectors $(a, c)$ and $(1, 0)$ are primitive and congruent modulo $N$. By Lemma 1.1.7 there is $\gamma \in \Gamma(N) \subset \Gamma_1$ with $\gamma(a, c)^t = (1, 0)^t$. Then $\gamma\beta = \begin{pmatrix} 1 & b' \\ 0 & p \end{pmatrix}$, and multiplication on the left by $\begin{pmatrix} 1 & t \\ 0 & 1 \end{pmatrix} \in \Gamma_1$ changes $b'$ to $b' + tp$. So $\beta \in \Gamma_1\beta_j$ with $j \equiv b' \bmod p$. If $\Gamma_1\beta_j = \Gamma_1\beta_{j'}$, then $\beta_{j'}\beta_j^{-1} = \begin{pmatrix} 1 & (j'-j)/p \\ 0 & 1 \end{pmatrix}$ has integer entries, so $j = j'$.

Let $g = p$. Then $p \mid a$, so $p \nmid N$ because $a \equiv 1 \bmod N$. The vectors $(a/p, c/p)$ and $(m, N)$ are primitive, and both are congruent to $(p^{-1}, 0)$ modulo $N$, because $mp \equiv 1$. By Lemma 1.1.7 there is $\gamma \in \Gamma(N)$ with $\gamma\beta = \begin{pmatrix} mp & b'' \\ Np & d'' \end{pmatrix}$. The determinant gives $md'' - Nb'' = 1 = mp - Nn$, so $(d'', b'') = (p + Ns, n + ms)$ for some $s \in \mathbb{Z}$. A direct computation gives
$$\gamma\beta\beta_\infty^{-1} = \begin{pmatrix} 1 - Nms & m^2 s \\ -N^2 s & 1 + Nms \end{pmatrix} \in \Gamma_1,$$
so $\beta \in \Gamma_1\beta_\infty$.

Finally, $\Gamma_1\alpha\Gamma_1 \subset \Delta_p$, and the representatives are in $\Gamma_1\alpha\Gamma_1$: we have $\beta_j = \alpha\begin{pmatrix} 1 & j \\ 0 & 1 \end{pmatrix}$ and $\beta_\infty = \alpha\begin{pmatrix} mp & n \\ N & 1 \end{pmatrix}$, and the second factors are in $\Gamma_1$. So $\Delta_p = \Gamma_1\alpha\Gamma_1$. $\square$

**Definition 1.5.6 (the Hecke operator $T_p$).** For $f \in M_k(\Gamma_1(N))$ let
$$T_p f = f|_k[\Gamma_1\alpha\Gamma_1] = \sum_{\beta \in \Gamma_1\backslash\Delta_p} f|_k\beta.$$
If $p \mid N$, we also write $U_p$ for $T_p$.

Lean: `Langlands.Modular.heckeT` and `Langlands.Modular.cuspHeckeT`, on $M_k(\Gamma_0(N))$ and $S_k(\Gamma_0(N))$ only, see Definition 1.5.14

By Lemma 1.5.1, $T_p$ is a linear operator on $M_k(\Gamma_1)$ that preserves $S_k(\Gamma_1)$.

**Proposition 1.5.7 (the formula for $T_p$).** For $f \in M_k(\Gamma_1(N))$,
$$T_p f = \sum_{j=0}^{p-1} f|_k\begin{pmatrix} 1 & j \\ 0 & p \end{pmatrix} + (\langle p \rangle f)|_k\begin{pmatrix} p & 0 \\ 0 & 1 \end{pmatrix},$$
where the last term is 0 if $p \mid N$. The operator $T_p$ commutes with each $\langle d \rangle$, so it preserves each space $M_k(N, \chi)$.

Lean: `Langlands.Modular.heckeT_apply_of_not_dvd` and `Langlands.Modular.heckeT_apply_of_dvd`, for the formula on $M_k(\Gamma_0(N))$, where $\langle p \rangle f = f$, see Proposition 1.5.17; the diamond operators are not defined

*Proof.* The formula follows from Lemma 1.5.5 and $\beta_\infty = \begin{pmatrix} m & n \\ N & p \end{pmatrix}\begin{pmatrix} p & 0 \\ 0 & 1 \end{pmatrix}$, where the first factor is in $\Gamma_0$ with lower right entry $p$. Let $\gamma \in \Gamma_0$. Modulo $N$, conjugation by $\gamma$ preserves the upper triangular matrices and their upper left entries, so $\gamma^{-1}\Delta_p\gamma = \Delta_p$. Since $\Gamma_1$ is normal in $\Gamma_0$, the map $\Gamma_1\beta \mapsto \Gamma_1\gamma^{-1}\beta\gamma$ is a bijection of $\Gamma_1\backslash\Delta_p$. So
$$(T_p f)|\gamma = \sum_\beta f|\beta\gamma = \sum_\beta (f|\gamma)|(\gamma^{-1}\beta\gamma) = T_p(f|\gamma). \qquad \square$$

**Theorem 1.5.8 ($T_p$ on $q$-expansions).** Let $f \in M_k(N, \chi)$ with $q$-expansion $\sum_{n \ge 0} a_n(f) q^n$. Then
$$a_n(T_p f) = a_{np}(f) + \chi(p) p^{k-1} a_{n/p}(f) \qquad (n \ge 0),$$
where $a_{n/p}(f) = 0$ if $p \nmid n$, and $\chi(p) = 0$ if $p \mid N$. In particular $a_n(U_p f) = a_{np}(f)$ for $p \mid N$.

Lean: `Langlands.Modular.coeff_heckeT`, with the two cases `Langlands.Modular.coeff_heckeT_of_not_dvd` and `Langlands.Modular.coeff_heckeT_of_dvd`, for the trivial character, see Theorem 1.5.18

*Proof.* We have $(f|\beta_j)(\tau) = p^{k-1} p^{-k} f((\tau + j)/p)$. So
$$\sum_{j=0}^{p-1} (f|\beta_j)(\tau) = \frac{1}{p} \sum_{n \ge 0} a_n(f) e^{2\pi i n\tau/p} \sum_{j=0}^{p-1} e^{2\pi i nj/p} = \sum_{p \mid n} a_n(f) q^{n/p} = \sum_{n \ge 0} a_{np}(f) q^n,$$
because the inner sum is $p$ if $p \mid n$ and 0 otherwise. If $p \nmid N$, then $\langle p\rangle f = \chi(p) f$ and $(f|\begin{pmatrix} p & 0 \\ 0 & 1\end{pmatrix})(\tau) = p^{k-1} f(p\tau) = p^{k-1}\sum_n a_n(f) q^{pn}$. $\square$

**Theorem 1.5.9 (commutativity).** The operators $T_p$, for all primes $p$, and $\langle d \rangle$, for all $d$, on $M_k(\Gamma_1(N))$ commute with each other.

Lean: `Langlands.Modular.heckeT_comm`, for $T_pT_q = T_qT_p$ on $M_k(\Gamma_0(N))$, see Theorem 1.5.19

*Proof.* The diamond operators commute with each other because $(\mathbb{Z}/N\mathbb{Z})^\times$ is abelian, and with each $T_p$ by Proposition 1.5.7. By Propositions 1.5.3 and 1.5.7 it suffices to prove $T_pT_q f = T_qT_p f$ for $f \in M_k(N, \chi)$ and primes $p \ne q$. A form is determined by its $q$-expansion. By Theorem 1.5.8, applied twice,
$$a_n(T_pT_q f) = a_{npq}(f) + \chi(q)q^{k-1} a_{np/q}(f) + \chi(p)p^{k-1} a_{nq/p}(f) + \chi(pq)(pq)^{k-1} a_{n/pq}(f).$$
This is symmetric in $p$ and $q$. $\square$

### The operators $T_n$

**Definition 1.5.10 (the operators $T_n$).** Define $T_n$ for $n \ge 1$ by $T_1 = 1$, by $T_{p^r} = T_pT_{p^{r-1}} - p^{k-1}\langle p\rangle T_{p^{r-2}}$ for primes $p$ and $r \ge 2$, and by $T_{mn} = T_mT_n$ for coprime $m$ and $n$. The *Hecke algebra* $\mathbb{T}$ is the subalgebra of $\mathrm{End}(S_k(\Gamma_1(N)))$ generated by all $T_n$ and $\langle d \rangle$.

Lean: not defined on forms; `Langlands.Modular.heckeSeq` is the formula of Proposition 1.5.11 on coefficient sequences, see Definition 2.1.17

By Theorem 1.5.9 the definition is consistent, and $\mathbb{T}$ is commutative. On $M_k(N, \chi)$ the recursion reads $T_{p^r} = T_pT_{p^{r-1}} - \chi(p)p^{k-1}T_{p^{r-2}}$. For $p \mid N$ it gives $T_{p^r} = U_p^r$.

**Proposition 1.5.11 ($T_n$ on $q$-expansions).** Let $f \in M_k(N, \chi)$ and $n \ge 1$. Then
$$a_m(T_n f) = \sum_{d \mid \gcd(m, n)} \chi(d) d^{k-1} a_{mn/d^2}(f) \qquad (m \ge 0),$$
where for $m = 0$ the sum runs over all $d \mid n$. In particular $a_1(T_n f) = a_n(f)$.

Lean: not stated yet for all $f$; for the coefficients of a normalized eigenform on $\Gamma_0(N)$, `Langlands.Modular.IsNormalizedHeckeEigenform.heckeSeq_qCoeff`, see Corollary 2.1.19

*Proof.* First let $n = p^r$, and write $v = v_p(m)$. The claim is $a_m(T_{p^r}f) = \sum_{j=0}^{\min(r, v)} c_{r,j}$ with $c_{r,j} = \chi(p)^j p^{j(k-1)} a_{mp^{r-2j}}(f)$. It holds for $r = 0$, and for $r = 1$ it is Theorem 1.5.8. Assume it for $r$ and $r - 1$, and let $g = T_{p^r}f$. By Theorem 1.5.8 and the recursion,
$$a_m(T_{p^{r+1}}f) = a_{mp}(g) + \chi(p)p^{k-1}a_{m/p}(g) - \chi(p)p^{k-1}a_m(T_{p^{r-1}}f).$$
By the induction hypothesis the three terms are $\sum_{0 \le j \le \min(r, v+1)} c_{r+1, j}$, then $\sum_{1 \le j \le \min(r+1, v)} c_{r+1,j}$, and minus $\sum_{1 \le j \le \min(r, v+1)} c_{r+1,j}$. The sum is $\sum_{0 \le j \le \min(r+1, v)} c_{r+1,j}$, as claimed. For $m = 0$ the same computation holds with $v = \infty$.

Now let $n = n_1n_2$ with $\gcd(n_1, n_2) = 1$, and assume the formula for $n_1$ and $n_2$. Then
$$a_m(T_{n_1}T_{n_2}f) = \sum_{d_1 \mid (m, n_1)} \chi(d_1)d_1^{k-1} \sum_{d_2 \mid (mn_1/d_1^2,\, n_2)} \chi(d_2)d_2^{k-1} a_{mn/(d_1d_2)^2}(f).$$
Since $n_2$ is coprime to $n_1$, the condition $d_2 \mid (mn_1/d_1^2, n_2)$ is equivalent to $d_2 \mid (m, n_2)$. The products $d = d_1d_2$ run once over the divisors of $\gcd(m, n)$, and $\chi(d_1)\chi(d_2) = \chi(d)$. $\square$

**Example 1.5.12 (Eisenstein series are eigenforms).** Let $N = 1$ and $k \ge 4$ even. Then $T_n E_k = \sigma_{k-1}(n) E_k$ for each $n$. By Proposition 1.5.11 and multiplicativity it suffices to check that $a_m(T_p E_k) = \sigma_{k-1}(p) a_m(E_k)$ for primes $p$. For $m = 0$ this is $a_0(T_pE_k) = 1 + p^{k-1}$. For $m \ge 1$ with $v = v_p(m)$ and $m = p^v m'$, we need $\sigma_{k-1}(p^{v+1}) + p^{k-1}\sigma_{k-1}(p^{v-1}) = (1 + p^{k-1})\sigma_{k-1}(p^v)$, with $\sigma_{k-1}(p^{-1}) = 0$. Both sides equal $\sum_{i=0}^{v} p^{i(k-1)} + \sum_{i=1}^{v+1} p^{i(k-1)}$.

**Remark 1.5.13 (Hecke operators in Mathlib and in the Lean project).** Mathlib does not define the Hecke operators, but it has the trace and the translate of Definition 1.5.14. The Lean project uses them to define $T_p$ and $U_p$ on $M_k(\Gamma_0(N))$ and on $S_k(\Gamma_0(N))$, and it proves Proposition 1.5.7 and Theorems 1.5.8 and 1.5.9 for these spaces. The last subsection of this section gives the proofs in the form that the project uses, and Remark 1.5.21 lists the Lean names. The project has no diamond operators and no operators on $M_k(\Gamma_1(N))$. It also has no operators $T_n$ on forms for composite $n$, so Definition 1.5.10 and the Hecke algebra $\mathbb{T}$ are not in Lean. For this reason the predicates of the project for eigenforms, which Section 2.1 describes, are still conditions on the $q$-expansion. For forms on $\Gamma_0(N)$ the project proves that an eigenform of all the operators $T_p$ and $U_p$ with $a_1 = 1$ satisfies them, see Corollary 2.1.15. The operators $U_p$ for $p \mid N$ need not be diagonalizable on $S_k(\Gamma_1(N))$, see Remark 1.6.7. Example 2.1.9 shows that they can have eigenforms that are not newforms.

### $T_p$ on $\Gamma_0(N)$ as the trace of a translate

On $M_k(\Gamma_0(N))$ there is a second way to write the operator $T_p$, and the Lean project uses it. We first translate $f$ by $\alpha$, which gives a form for a smaller group, and then we take the trace back to $\Gamma_0(N)$. This subsection explains this definition, shows that it is the double coset operator of $\Gamma_0\alpha\Gamma_0$, and derives from it the formula for $T_p$, the formula for its $q$-expansion and the commutativity of the operators. The proofs use the group $\Gamma_0$ only, and they do not need the diamond operators. We keep the prime $p$ and $\alpha = \begin{pmatrix} 1 & 0 \\ 0 & p \end{pmatrix}$, and we put $\varepsilon_p = 1$ if $p \nmid N$ and $\varepsilon_p = 0$ if $p \mid N$.

**Definition 1.5.14 (translate and trace).** Let $\Gamma' \subset \Gamma$ be congruence subgroups and $g \in M_k(\Gamma')$. The *trace* of $g$ is
$$\mathrm{Tr}_{\Gamma'}^{\Gamma}\, g = \sum_{\gamma \in \Gamma'\backslash\Gamma} g|_k\gamma.$$
Let $H = \Gamma_0 \cap \alpha^{-1}\Gamma_0\alpha$. For $f \in M_k(\Gamma_0)$ the *translate* of $f$ by $\alpha$ is $f|_k\alpha$, and we put
$$T_p f = \mathrm{Tr}_{H}^{\Gamma_0}(f|_k\alpha) = \sum_{\gamma \in H\backslash\Gamma_0} f|_k\alpha\gamma.$$

Lean: `Langlands.Modular.heckeT` and `Langlands.Modular.cuspHeckeT`, built from `ModularForm.trace` and `ModularForm.translate` of Mathlib

The definition makes sense. The term $g|\gamma$ depends only on the coset $\Gamma'\gamma$, because $g|\gamma'\gamma = g|\gamma$ for $\gamma' \in \Gamma'$. For $\delta \in \Gamma$, right multiplication by $\delta$ permutes the cosets $\Gamma'\backslash\Gamma$, so $(\mathrm{Tr}\, g)|\delta = \mathrm{Tr}\, g$. Each $g|\gamma$ is holomorphic at the cusps, and it vanishes at the cusps if $g$ is a cusp form, because $\gamma \in SL_2(\mathbb{Z})$. So the trace is a linear map from $M_k(\Gamma')$ to $M_k(\Gamma)$, and from $S_k(\Gamma')$ to $S_k(\Gamma)$. By Lemma 1.2.7, $f|\alpha$ is a modular form for $\alpha^{-1}\Gamma_0\alpha \cap SL_2(\mathbb{Z})$, so also for $H$, and $H$ is a congruence subgroup. Thus $T_p$ is a linear operator on $M_k(\Gamma_0)$ that preserves $S_k(\Gamma_0)$. The two steps are the two halves of the proof of Lemma 1.5.1: the translate leaves the group $\Gamma_0$, and the trace returns to it.

**Proposition 1.5.15 (the trace is the double coset operator).** Let $\gamma_1, \dots, \gamma_n$ be representatives of $H\backslash\Gamma_0$. Then $\Gamma_0\alpha\Gamma_0 = \bigsqcup_{i} \Gamma_0\alpha\gamma_i$, and $T_pf = f|_k[\Gamma_0\alpha\Gamma_0]$ for $f \in M_k(\Gamma_0)$.

Lean: `Langlands.Modular.quotientFunc_cosetMk`, for the term of the trace at a coset

*Proof.* The proof of Lemma 1.5.1 shows that $\gamma \mapsto \Gamma_0\alpha\gamma$ induces a bijection from $H\backslash\Gamma_0$ to the set of right cosets of $\Gamma_0$ in $\Gamma_0\alpha\Gamma_0$. So the matrices $\beta_i = \alpha\gamma_i$ are representatives as in Lemma 1.5.1, and the two sums are the same sum. $\square$

**Lemma 1.5.16 (the cosets of $H$).** Let $\gamma = \begin{pmatrix} a & b \\ c & d \end{pmatrix} \in \Gamma_0$.
1. The matrix $\gamma$ is in $H$ if and only if $p \mid b$.
2. Two elements $\gamma_1, \gamma_2$ of $\Gamma_0$ with first rows $(a_1, b_1)$ and $(a_2, b_2)$ have $H\gamma_1 = H\gamma_2$ if and only if $a_2b_1 \equiv a_1b_2 \pmod p$.
3. The matrices $T^j = \begin{pmatrix} 1 & j \\ 0 & 1 \end{pmatrix}$ for $0 \le j < p$ are representatives of $H\backslash\Gamma_0$ if $p \mid N$. If $p \nmid N$, choose $b, d \in \mathbb{Z}$ with $pd - Nb = 1$ and let $\delta = \begin{pmatrix} p & b \\ N & d \end{pmatrix}$. Then the $T^j$ for $0 \le j < p$ and $\delta$ are representatives. So $[\Gamma_0 : H] = p + \varepsilon_p$.

Lean: `Langlands.Modular.mapGL_mem_conj_iff`, `Langlands.Modular.cosetMk_eq_iff`, `Langlands.Modular.bijective_cosetMk_tRep` and `Langlands.Modular.bijective_cosetRep`, for left cosets and the inverse representatives

*Proof.* For part 1 we compute
$$\alpha\gamma\alpha^{-1} = \begin{pmatrix} a & b/p \\ pc & d \end{pmatrix}.$$
The lower left entry $pc$ is divisible by $N$. So $\alpha\gamma\alpha^{-1} \in \Gamma_0$ if and only if $b/p \in \mathbb{Z}$, and $\gamma \in \alpha^{-1}\Gamma_0\alpha$ if and only if $\alpha\gamma\alpha^{-1} \in \Gamma_0$. For part 2, $H\gamma_1 = H\gamma_2$ if and only if $\gamma_1\gamma_2^{-1} \in H$. The upper right entry of $\gamma_1\gamma_2^{-1}$ is $a_2b_1 - a_1b_2$, because the second column of $\gamma_2^{-1}$ is $(-b_2, a_2)^t$. Part 1 gives the claim.

For part 3, the first row $(a, b)$ of $\gamma$ is not zero modulo $p$, because $ad - bc = 1$. By part 2 the map that sends $H\gamma$ to the point $(a : b)$ of the projective line $\mathbb{P}^1(\mathbb{F}_p)$ is well defined and injective. The matrix $T^j$ goes to $(1 : j)$, so the images of the $T^j$ are the $p$ points $(1 : j)$ with $j \in \mathbb{F}_p$. The only other point is $(0 : 1)$, and it is the image of $\gamma$ if and only if $p \mid a$. If $p \mid N$, then $p \mid c$, so $ad \equiv 1 \pmod p$ and $p \nmid a$. In this case the point $(0 : 1)$ is not in the image. If $p \nmid N$, integers $b, d$ with $pd - Nb = 1$ exist, $\delta \in \Gamma_0$, and $\delta$ goes to $(p : b) = (0 : 1)$, since $p \nmid b$. $\square$

**Proposition 1.5.17 ($T_p$ on $\Gamma_0(N)$).** For $f \in M_k(\Gamma_0(N))$ and $\tau \in \mathbb{H}$,
$$(T_pf)(\tau) = \frac{1}{p}\sum_{j=0}^{p-1} f\left(\frac{\tau + j}{p}\right) + \varepsilon_p\, p^{k-1} f(p\tau).$$
On $M_k(\Gamma_0(N)) \subset M_k(\Gamma_1(N))$ the operator $T_p$ of Definition 1.5.14 is the operator $T_p$ of Definition 1.5.6.

Lean: `Langlands.Modular.heckeT_apply_of_not_dvd` and `Langlands.Modular.heckeT_apply_of_dvd`

*Proof.* By Lemma 1.5.16, $T_pf = \sum_{j} f|\alpha T^j + \varepsilon_p\, f|\alpha\delta$. First, $\alpha T^j = \begin{pmatrix} 1 & j \\ 0 & p \end{pmatrix}$ has determinant $p$ and $j(\alpha T^j, \tau) = p$, so $(f|\alpha T^j)(\tau) = p^{k-1}p^{-k} f((\tau + j)/p) = p^{-1} f((\tau + j)/p)$. Next, let $p \nmid N$. Then
$$\alpha\delta = \begin{pmatrix} p & b \\ Np & pd \end{pmatrix} = \gamma'\begin{pmatrix} p & 0 \\ 0 & 1 \end{pmatrix}, \qquad \gamma' = \begin{pmatrix} 1 & b \\ N & pd \end{pmatrix}.$$
The matrix $\gamma'$ has determinant $pd - Nb = 1$ and lower left entry $N$, so $\gamma' \in \Gamma_0$. Hence $f|\alpha\delta = (f|\gamma')|\mathrm{diag}(p, 1) = f|\mathrm{diag}(p, 1)$, and $(f|\mathrm{diag}(p, 1))(\tau) = p^{k-1} f(p\tau)$. For the last claim, Proposition 1.5.7 gives the same formula with $\langle p\rangle f$ in place of $f$ in the last term. The operator $\langle p \rangle$ is $f \mapsto f|\gamma$ for some $\gamma \in \Gamma_0$, so $\langle p \rangle f = f$ for $f \in M_k(\Gamma_0)$. $\square$

The choice of $b$ and $d$ does not matter. Another choice changes $\delta$ to $h\delta$ with $h \in H$, by part 2 of Lemma 1.5.16, and this does not change the coset. The matrix $\alpha\delta$ is in the coset $\Gamma_0\,\mathrm{diag}(p, 1)$, and so is the matrix $\beta_\infty$ of Lemma 1.5.5, by the factorization in the proof of Proposition 1.5.7.

**Theorem 1.5.18 (the $q$-expansion of $T_pf$).** Let $f \in M_k(\Gamma_0(N))$ with $q$-expansion $\sum_{n \ge 0} a_n q^n$. Then
$$a_m(T_pf) = a_{mp} + \varepsilon_p\, p^{k-1} a_{m/p} \qquad (m \ge 0),$$
where $a_{m/p} = 0$ if $p \nmid m$.

Lean: `Langlands.Modular.coeff_heckeT`, `Langlands.Modular.coeff_heckeT_of_not_dvd` and `Langlands.Modular.coeff_heckeT_of_dvd`; the convergent series is `Langlands.Modular.hasSum_heckeT`

*Proof.* We compute the two kinds of terms of Proposition 1.5.17 separately and then compare coefficients. The series $\sum a_n q^n$ converges absolutely for $|q| < 1$, so we may rearrange it.

The terms of the upper triangular matrices. Let $\zeta = e^{2\pi i/p}$. For each $j$,
$$f\left(\frac{\tau + j}{p}\right) = \sum_{n \ge 0} a_n e^{2\pi i n(\tau + j)/p} = \sum_{n \ge 0} a_n \zeta^{nj} e^{2\pi i n\tau/p}.$$
This is a series in $e^{2\pi i\tau/p}$, not in $q$. We sum over $j$. If $p \mid n$, then $\sum_{j=0}^{p-1}\zeta^{nj} = p$. If $p \nmid n$, then $\zeta^n \ne 1$ and $\sum_{j=0}^{p-1}\zeta^{nj} = (\zeta^{np} - 1)/(\zeta^n - 1) = 0$. So
$$\frac{1}{p}\sum_{j=0}^{p-1} f\left(\frac{\tau + j}{p}\right) = \sum_{p \mid n} a_n e^{2\pi i (n/p)\tau} = \sum_{m \ge 0} a_{mp}\, q^m.$$
The average over $j$ removes the fractional powers of $q$.

The term of $\mathrm{diag}(p, 1)$. If $p \nmid N$, then
$$p^{k-1} f(p\tau) = \sum_{n \ge 0} p^{k-1} a_n q^{pn} = \sum_{p \mid m} p^{k-1} a_{m/p}\, q^m.$$

Comparison. The sum of the two series is a series $\sum_m b_m q^m$ with $b_m = a_{mp} + \varepsilon_p p^{k-1}a_{m/p}$, and it converges to $(T_pf)(\tau)$ for each $\tau \in \mathbb{H}$. The form $T_pf$ also has its own $q$-expansion $\sum_m a_m(T_pf)q^m$. Both series define holomorphic functions of $q$ on the disc $|q| < 1$ that agree on the punctured disc, so they are the same power series, and $a_m(T_pf) = b_m$. $\square$

This is Theorem 1.5.8 for the trivial character, and the proof is the same. We repeat it because here it is a consequence of the coset representatives of Lemma 1.5.16 alone.

**Theorem 1.5.19 ($T_p$ and $T_q$ commute).** Let $p \ne q$ be primes and $f \in M_k(\Gamma_0(N))$. Then $T_pT_qf = T_qT_pf$. This includes the cases $p \mid N$ or $q \mid N$, so $T_p$ commutes with $U_q$, and $U_p$ with $U_q$.

Lean: `Langlands.Modular.heckeT_comm`, with `Langlands.Modular.heckeCoeff_heckeCoeff` and `Langlands.Modular.heckeCoeff_comm` for the computation on sequences

*Proof.* For a sequence $a = (a_n)_{n \ge 0}$ of complex numbers let $h_pa$ be the sequence
$$(h_pa)_m = a_{mp} + \varepsilon_p\, p^{k-1}a_{m/p},$$
with $a_{m/p} = 0$ for $p \nmid m$. By Theorem 1.5.18 the coefficients of $T_pf$ are $h_p$ of the coefficients of $f$, so the coefficients of $T_pT_qf$ are $h_ph_q$ of the coefficients of $f$. We compute $(h_ph_qa)_m = (h_qa)_{mp} + \varepsilon_pp^{k-1}(h_qa)_{m/p}$, where the second term is present only if $p \mid m$. First, $(h_qa)_{mp} = a_{mpq} + \varepsilon_qq^{k-1}a_{mp/q}$. The second term is present if and only if $q \mid mp$, that is, $q \mid m$, because $q \nmid p$. Next, if $p \mid m$, then $(h_qa)_{m/p} = a_{mq/p} + \varepsilon_qq^{k-1}a_{m/pq}$, where the second term is present if and only if $q \mid m/p$, that is, $q \mid m$. With $[P]$ equal to 1 if $P$ holds and 0 otherwise, we get
$$(h_ph_qa)_m = a_{mpq} + [q \mid m]\,\varepsilon_q q^{k-1}a_{mp/q} + [p \mid m]\,\varepsilon_p p^{k-1}a_{mq/p} + [pq \mid m]\,\varepsilon_p\varepsilon_q (pq)^{k-1}a_{m/pq}.$$
This expression is symmetric in $p$ and $q$. So $T_pT_qf$ and $T_qT_pf$ have the same $q$-expansion, and they are equal by Remark 1.2.5. $\square$

The proof only uses the $q$-expansion at $\infty$. Shimura, Chapter 3, proves the commutativity in the ring of double cosets, without $q$-expansions. In level one his argument is short: the transpose map induces an anti-automorphism of the ring, and it fixes each double coset $SL_2(\mathbb{Z})\beta SL_2(\mathbb{Z})$ by the elementary divisor theorem, so the ring is commutative. The proof above is shorter, and it is the proof in Lean.

**Example 1.5.20 ($T_2$ on $\Delta$).** Let $N = 1$, $k = 12$ and $p = 2$. The first coefficients of $\Delta$ are
$$\Delta = q - 24q^2 + 252q^3 - 1472q^4 + 4830q^5 - 6048q^6 - 16744q^7 + 84480q^8 + O(q^9).$$
In Lemma 1.5.16 we may take $b = -1$ and $d = 0$, so the three cosets of $H$ in $SL_2(\mathbb{Z})$ are those of $I$, $T$ and $\delta = \begin{pmatrix} 2 & -1 \\ 1 & 0 \end{pmatrix}$, and $\gamma' = \begin{pmatrix} 1 & -1 \\ 1 & 0 \end{pmatrix}$. Proposition 1.5.17 gives
$$(T_2\Delta)(\tau) = \frac{1}{2}\left(\Delta\left(\frac{\tau}{2}\right) + \Delta\left(\frac{\tau + 1}{2}\right)\right) + 2^{11}\Delta(2\tau).$$
With $q^{1/2} = e^{\pi i\tau}$ we have $\Delta(\tau/2) = \sum \tau(n)q^{n/2}$ and $\Delta((\tau + 1)/2) = \sum (-1)^n\tau(n)q^{n/2}$. The average keeps the even $n$:
$$\frac{1}{2}\left(\Delta\left(\frac{\tau}{2}\right) + \Delta\left(\frac{\tau + 1}{2}\right)\right) = \sum_{m \ge 1}\tau(2m)q^m = -24q - 1472q^2 - 6048q^3 + 84480q^4 + O(q^5).$$
Also $2^{11}\Delta(2\tau) = 2048q^2 - 49152q^4 + O(q^6)$. So
$$T_2\Delta = -24q + 576q^2 - 6048q^3 + 35328q^4 + O(q^5) = -24\left(q - 24q^2 + 252q^3 - 1472q^4\right) + O(q^5).$$
The space $S_{12}(SL_2(\mathbb{Z}))$ is $\mathbb{C}\Delta$ by Corollary 1.3.5, and $T_2$ preserves it, so $T_2\Delta = c\Delta$. The coefficient of $q$ gives $c = a_1(T_2\Delta) = \tau(2) = -24$. The coefficients of $q^2$, $q^3$ and $q^4$ then give
$$\tau(4) + 2^{11} = \tau(2)^2, \qquad \tau(6) = \tau(2)\tau(3), \qquad \tau(8) + 2^{11}\tau(2) = \tau(2)\tau(4).$$
The first relation gives $\tau(4) = 576 - 2048 = -1472$, which agrees with the expansion. These are the first cases of Ramanujan's relations, and Section 2.1 proves them all in this way. On the line $\mathbb{C}\Delta$ any two operators commute, so Theorem 1.5.19 says nothing new here. It says something in $S_{24}(SL_2(\mathbb{Z}))$, which has dimension 2, see Example 1.6.6.

**Remark 1.5.21 (the operators in Lean).** The file `Langlands/Modular/Hecke.lean` of the Lean project follows this subsection. The matrix $\alpha$ is `Langlands.Modular.heckeMat p`, and `Langlands.Modular.heckeT p N f` is `ModularForm.trace` applied to `ModularForm.translate f α`. The slash action of Mathlib has the factor $\det(\gamma)^{k-1}$ of Definition 1.2.1, so the operator is the $T_p$ of this section and of Diamond and Shurman, with no extra power of $p$. Lean sums over the left cosets $\gamma H$ in $\Gamma_0$, and the term at $\gamma H$ is $f|\alpha\gamma^{-1}$. So the representatives in Lean are the inverses of ours, $T^{-j}$, which is `Langlands.Modular.tRep j`, and $\delta^{-1}$, where $\delta$ is `Langlands.Modular.deltaRep`. The identity $\alpha\delta = \gamma'\,\mathrm{diag}(p, 1)$ is `Langlands.Modular.heckeMat_mul_deltaRep`, the orthogonality of the $p$th roots of unity is `Langlands.Modular.sum_exp_pow`, and the map $h_p$ of the proof of Theorem 1.5.19 is `Langlands.Modular.heckeCoeff`. The uniqueness of $q$-expansions is `ModularForm.qExpansion_injective` of Mathlib. The file `Langlands/Modular/HeckeMul.lean` proves that $T_p$ is linear on cusp forms, as `Langlands.Modular.cuspHeckeT_add` and `Langlands.Modular.cuspHeckeT_smul`. The project does not define the diamond operators, the operators on $M_k(\Gamma_1(N))$ or on $M_k(N, \chi)$, the operators $T_n$ on forms for composite $n$, or the Hecke algebra. Remark 2.1.21 says what the project proves about eigenforms with these operators.
