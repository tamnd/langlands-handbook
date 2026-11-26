---
title: Hecke operators and the Satake isomorphism
nodes: []
sources: [Lan70]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Hecke operators and the Satake isomorphism

At a finite place $v$ where a cuspidal representation $\pi$ is unramified, the local component $\pi_v$ is determined by $n$ complex numbers, its Satake parameters. This section defines the Hecke operators $T_{v,1}, \ldots, T_{v,n}$, computes their action on the spherical vector of an unramified principal series, and proves the part of the Satake isomorphism that we need. It also fixes the normalization, which is the same as in the Lean project. The example is $\varphi_\Delta$: we compute its eigenvalues $\tau(p) p^{-5}$ and $1$ from the classical operator $T_p$.

In this section $v$ is a finite place, $G_v = GL_n(F_v)$, $K_v = GL_n(\mathcal{O}_v)$, $\varpi = \varpi_v$ and $q = q_v$. For $\lambda \in \mathbb{Z}^n$ we write $\varpi^\lambda = \mathrm{diag}(\varpi^{\lambda_1}, \ldots, \varpi^{\lambda_n})$, and we call $\lambda$ *dominant* if $\lambda_1 \ge \cdots \ge \lambda_n$.

### The spherical Hecke algebra

**Proposition 1.4.1 (Cartan decomposition).** The group $G_v$ is the disjoint union of the double cosets $K_v \varpi^\lambda K_v$ for $\lambda$ dominant.

Lean: not stated yet

*Proof.* This is the theory of elementary divisors over the principal ideal domain $\mathcal{O}_v$. Row and column operations bring $g$ to the form $\varpi^\lambda$. The numbers $\lambda_n$, $\lambda_n + \lambda_{n-1}, \ldots$ are the minimal valuations of the minors of size $1, 2, \ldots$ of $g$, which do not change under $K_v$ on both sides. $\square$

**Definition 1.4.2 (the Hecke operators $T_{v,i}$).** The *spherical Hecke algebra* $\mathcal{H}_v = \mathcal{H}(G_v, K_v)$ is the algebra of the compactly supported functions $G_v \to \mathbb{C}$ that are invariant under $K_v$ on both sides, with the convolution for the Haar measure with $\mathrm{vol}(K_v) = 1$. For $1 \le i \le n$ let $t_i = \varpi^{(1, \ldots, 1, 0, \ldots, 0)}$, with $i$ entries $1$, and let $T_{v,i}$ be the characteristic function of $K_v t_i K_v$. It acts on functions on $GL_n(\mathbb{A})$ that are right invariant under $K_v$ by
$$(T_{v,i} \varphi)(g) = \int_{G_v} T_{v,i}(h) \varphi(gh) \, dh = \sum_{h \in K_v t_i K_v / K_v} \varphi(gh).$$

Lean: `Langlands.adelicHeckeOperator`, a definition of the project

The sum is finite because $K_v t_i K_v$ is compact and $K_v$ is open. The operators commute with the right translations at the other places and with each other, by the next theorem. The operator $T_{v,n}$ is the right translation by the central element $\varpi I_n$, so on a form with central character $\omega$ it acts by $\omega_v(\varpi)$.

**Lemma 1.4.3 (coset representatives).** For $1 \le i \le n$ the right cosets $h K_v$ in $K_v t_i K_v$ have these representatives: for each subset $s \subseteq \{1, \ldots, n\}$ of size $i$, the upper triangular matrices with diagonal entry $\varpi$ at the positions $j \in s$ and $1$ at the others, with an entry from a fixed set $R$ of representatives of $\mathcal{O}_v / \varpi$ at each position $(j, k)$ with $j < k$, $j \in s$ and $k \notin s$, and with $0$ at the other positions above the diagonal. Their number is the Gaussian binomial coefficient $\binom{n}{i}_q$.

Lean: `Langlands.HeckeCoset`, a definition of the project

*Proof.* A right coset $hK_v$ in $K_v t_i K_v$ is the same as a lattice $L = h \mathcal{O}_v^n$ with $\varpi \mathcal{O}_v^n \subseteq L \subseteq \mathcal{O}_v^n$ and $\dim_{k_v} \mathcal{O}_v^n / L = i$, so the cosets correspond to the subspaces $\bar L$ of dimension $n - i$ of $k_v^n$. Gaussian elimination gives $\bar L$ a unique basis in reduced column echelon form. Let $s$ be the complement of the set of its pivot positions. The column with the pivot $k \notin s$ has free entries exactly at the positions $j < k$ with $j \in s$. These columns, together with the vectors $\varpi e_j$ for $j \in s$, form the matrix of the lemma. $\square$

For $n = 2$ and $i = 1$ the representatives are $\begin{pmatrix} \varpi & b \\ 0 & 1 \end{pmatrix}$ for $b \in R$ and $\begin{pmatrix} 1 & 0 \\ 0 & \varpi \end{pmatrix}$, so there are $q + 1$ of them. These are the matrices of the classical operator $T_p$ of Volume 4.

### The unramified principal series

Let $\chi_1, \ldots, \chi_n$ be unramified characters of $F_v^\times$ and $\chi = \chi_1 \otimes \cdots \otimes \chi_n$, a character of $T(F_v)$ and of $B(F_v)$. The *unramified principal series* $I(\chi)$ is the space of the smooth functions $f : G_v \to \mathbb{C}$ with $f(bg) = \delta_B^{1/2}(b) \chi(b) f(g)$ for $b \in B(F_v)$, where $\delta_B(b) = \prod_{j < k} |b_{jj} / b_{kk}|$, with $G_v$ acting by right translation. This is the normalized induction of Volume 0, Section 3.2. By the Iwasawa decomposition, Proposition 1.1.3, there is a unique $f_0 \in I(\chi)$ that is fixed by $K_v$ with $f_0(1) = 1$, namely $f_0(bk) = \delta_B^{1/2}(b) \chi(b)$. Put $\alpha_j = \chi_j(\varpi)$.

**Proposition 1.4.4 (the eigenvalues on the spherical vector).** For $1 \le i \le n$,
$$T_{v,i} f_0 = q^{i(n-i)/2} \, e_i(\alpha_1, \ldots, \alpha_n) \, f_0,$$
where $e_i$ is the $i$-th elementary symmetric function.

Lean: not stated yet

*Proof.* The function $T_{v,i} f_0$ is fixed by $K_v$, so it is a multiple of $f_0$, and the multiple is $(T_{v,i} f_0)(1) = \sum_h f_0(h)$ over the representatives $h$ of Lemma 1.4.3. Each $h$ lies in $B(F_v)$, so $f_0(h) = \delta_B^{1/2}(h) \chi(h)$. For the representatives with the diagonal set $s$, $\chi(h) = \prod_{j \in s} \alpha_j$. The factor $|h_{jj} / h_{kk}|$ for $j < k$ is $q^{-1}$ if $j \in s$ and $k \notin s$, it is $q$ if $j \notin s$ and $k \in s$, and it is $1$ otherwise. Let $a(s)$ and $b(s)$ be the numbers of the pairs $j < k$ of the first and of the second kind. There are $q^{a(s)}$ representatives with the set $s$, so their contribution is
$$q^{a(s)} \cdot q^{(b(s) - a(s))/2} \prod_{j \in s} \alpha_j = q^{(a(s) + b(s))/2} \prod_{j \in s} \alpha_j.$$
Now $a(s) + b(s)$ is the number of the pairs $\{j, k\}$ with one element in $s$ and the other outside, which is $i(n - i)$ for every $s$. Summing over $s$ gives the claim. $\square$

The same computation for the left translation, or for the double coset of $t_i^{-1}$, gives the inverse parameters $\alpha_j^{-1}$. This is the other convention of the implementation notes of `Langlands/Statements/Automorphic.lean`. The statements of Chapter 2 have the same meaning in both conventions, because the contragredient of a cuspidal automorphic representation is again cuspidal and has the inverse parameters.

**Theorem 1.4.5 (Satake isomorphism).** The map $\mathcal{S} : \mathcal{H}_v \to \mathbb{C}[X_1^{\pm 1}, \ldots, X_n^{\pm 1}]$,
$$\mathcal{S}f(\varpi^\mu) = \delta_B^{1/2}(\varpi^\mu) \int_{N(F_v)} f(\varpi^\mu u) \, du, \qquad \mathcal{S}f = \sum_\mu \mathcal{S}f(\varpi^\mu) X^\mu,$$
is an isomorphism of algebras onto the polynomials that are invariant under the permutations of the variables. It sends $T_{v,i}$ to $q^{i(n-i)/2} e_i(X_1, \ldots, X_n)$. Hence $\mathcal{H}_v$ is commutative, and it is the polynomial algebra in $T_{v,1}, \ldots, T_{v,n}$ and $T_{v,n}^{-1}$.

Lean: not stated yet

*Proof sketch.* We follow Getz and Hahn. The Iwasawa decomposition shows that $\mathcal{S}$ is an algebra homomorphism and that $f$ acts on the spherical vector of $I(\chi)$ by the value $\chi(\mathcal{S} f)$ of $\mathcal{S} f$ at $X_j = \alpha_j$. Proposition 1.4.4 is the case $f = T_{v,i}$. The representations $I(\chi)$ and $I(\chi^w)$, $w \in S_n$, have the same unramified constituent, so $\mathcal{S} f$ is invariant. The image of the characteristic function of $K_v \varpi^\lambda K_v$, $\lambda$ dominant, is $q^{\langle \rho, \lambda \rangle} m_\lambda$ plus a combination of monomial symmetric functions $m_\mu$ with $\mu < \lambda$ in the dominance order. A triangular map from the basis of Proposition 1.4.1 to the basis $m_\lambda$ is bijective. $\square$

### Satake parameters

**Theorem 1.4.6 (unramified representations).** Let $\pi_v$ be an irreducible admissible unramified representation of $G_v$. Then $\dim \pi_v^{K_v} = 1$, and $\mathcal{H}_v$ acts on this line by a character. There are unramified characters $\chi_1, \ldots, \chi_n$, unique up to order, such that $\pi_v$ is the unique unramified subquotient of $I(\chi)$. The representation $\pi_v$ is determined by the eigenvalues of $T_{v,1}, \ldots, T_{v,n}$ on $\pi_v^{K_v}$.

Lean: not stated yet

*Proof sketch.* The space $\pi_v^{K_v}$ is a simple module of finite dimension of the commutative algebra $\mathcal{H}_v$, so it is a line. By Theorem 1.4.5 its character is $f \mapsto \chi(\mathcal{S} f)$ for some $\alpha \in (\mathbb{C}^\times)^n$, unique up to permutation. The functor $\pi \mapsto \pi^{K_v}$ is a bijection from the irreducible representations with $\pi^{K_v} \ne 0$ to the simple $\mathcal{H}_v$-modules, which gives the last claim. The embedding into some $I(\chi)$ uses the Jacquet module and is proved in Volume 6. $\square$

**Definition 1.4.7 (Satake parameters).** Let $\varphi$ be a function on $GL_n(\mathbb{A})$ that is right invariant under $K_v$ and an eigenvector of $T_{v,1}, \ldots, T_{v,n}$ with the eigenvalues $\lambda_1, \ldots, \lambda_n$, with $\lambda_n \ne 0$. Its *Satake parameters* at $v$ are the roots $\alpha_1, \ldots, \alpha_n$, with multiplicity, of the *Satake polynomial*
$$X^n + \sum_{i=1}^n (-1)^i q^{-i(n-i)/2} \lambda_i X^{n-i}.$$
For an unramified representation $\pi_v$ they are the Satake parameters of a nonzero vector of $\pi_v^{K_v}$. The *Satake parameter* of $\pi_v$ is the conjugacy class of $\mathrm{diag}(\alpha_1, \ldots, \alpha_n)$ in $GL_n(\mathbb{C})$.

Lean: `Langlands.satake`, a definition of the project, the roots of `Langlands.satakePolynomial`

By Proposition 1.4.4 the coefficient of $X^{n-i}$ is $(-1)^i e_i(\alpha)$, so the roots of the polynomial are the numbers $\chi_j(\varpi)$ of Theorem 1.4.6. This is the definition of Volume 0, Section 3.2. In this normalization $\pi_v$ is tempered if and only if $|\alpha_j| = 1$ for all $j$, and the central character satisfies $\omega_v(\varpi) = \lambda_n = \alpha_1 \cdots \alpha_n$. In the Lean code, `Langlands.satake n v ev` is the multiset of roots of `Langlands.satakePolynomial n q ev` with $q = |\mathcal{O}_K / \mathfrak{p}_v|$, and `Langlands.IsHeckeEigenAt φ v ev` says that $\varphi$ is right invariant under $GL_n(\mathcal{O}_v)$ and that $T_{v,i} \varphi = \lambda_i \varphi$ for $1 \le i \le n$.

**Example 1.4.8 ($n = 1$).** For $n = 1$ the only representative of Lemma 1.4.3 is $\varpi_v$ itself, so $T_{v,1}$ is the right translation by the idele $\varpi_v$ at $v$. For a Hecke character $\chi$ unramified at $v$, the eigenvalue is $\chi_v(\varpi_v)$, and the Satake polynomial is $X - \lambda_1$. So the Satake parameter is $\chi_v(\varpi_v)$, as in Volume 3, Chapter 4.

Lean: `Langlands.satake_one` and `Langlands.exists_adelicHeckeOperator_one_eq`, proved in the project

**Example 1.4.9 (modular forms).** Let $f \in S_k(\Gamma_0(N))$ be a normalized eigenform, $p \nmid N$ a prime and $\varphi_f$ the form of Example 1.2.3. Then $\varphi_f$ is right invariant under $GL_2(\mathbb{Z}_p)$, and
$$T_{p,1} \varphi_f = p^{1 - k/2} a_p(f) \, \varphi_f, \qquad T_{p,2} \varphi_f = \varphi_f.$$
The Satake polynomial is $X^2 - a_p(f) p^{-(k-1)/2} X + 1$, and its roots are the unitary Satake parameters $\alpha_p, \beta_p$ of Volume 0, Section 3.2. For $\Delta$ the eigenvalues are $\tau(p) p^{-5}$ and $1$, as the introduction said.

*Proof.* Evaluate at $g = g_\infty$ with $g_\infty i = \tau$. For the representative $h = \begin{pmatrix} p & b \\ 0 & 1 \end{pmatrix}$ at $p$, write $g_\infty h = \gamma \cdot \gamma_\infty^{-1} g_\infty \cdot k$ with $\gamma = h \in GL_2(\mathbb{Q})$ and $k \in K_0(N)$. This term is $p^{-k/2} f((\tau - b)/p)$ times the factor $j(g_\infty, i)^{-k} (\det g_\infty)^{k/2}$. The representative $\mathrm{diag}(1, p)$ gives $p^{k/2} f(p\tau)$ times the same factor. The sum is $p^{1 - k/2} (T_p f)(\tau)$ times the factor, with $T_p f(\tau) = p^{k-1} f(p\tau) + p^{-1} \sum_b f((\tau + b)/p)$ as in Volume 4. For $T_{p,2}$ use $\gamma = p I_2$, which gives the factor $p^{k} p^{-k} = 1$. $\square$

**Remark 1.4.10 (normalizations).** The *arithmetic* normalization multiplies the parameters by a power of $q$. For $GL_2$ and weight $k$ the arithmetic parameters $p^{(k-1)/2} \alpha_p$ are the roots of $X^2 - a_p X + p^{k-1}$. For the comparison with Galois representations, Clozel twists $\pi$ by $|\det|^{(1-n)/2}$. The Satake parameters of the twist are the numbers $q^{(n-1)/2} \alpha_j$, the roots of the Hecke polynomial of Section 1.7, which has only integral powers of $q$.
