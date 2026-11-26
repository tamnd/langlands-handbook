---
title: Automorphic forms and cusp forms
nodes: []
sources: [Lan70]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Automorphic forms and cusp forms

This section defines automorphic forms and cusp forms on $GL_n(\mathbb{A})$, compares the definition with the one of the Lean project, and proves that cusp forms are bounded when their central character is unitary. The example to keep in mind is the function $\varphi_\Delta$ of the introduction. Its constant term is the constant coefficient of the $q$-expansion of $\Delta$, which is zero.

### Automorphic forms

Let $\mathfrak{g} = \mathfrak{gl}_n(F_\infty) \otimes_\mathbb{R} \mathbb{C}$ be the complexified Lie algebra of $GL_n(F_\infty)$ and $Z(\mathfrak{g})$ the center of its universal enveloping algebra. A function $\varphi$ on $GL_n(\mathbb{A})$ is *smooth* if it is locally constant in the finite component and smooth in the infinite component. It has *moderate growth* if there are constants $C$ and $r$ with $|\varphi(g)| \le C \|g\|^r$, where $\|g\| = \prod_v \max_{i,j} \{|g_{ij}|_v, |(g^{-1})_{ij}|_v\}$ is the adelic height.

**Definition 1.2.1 (automorphic form).** An *automorphic form* on $GL_n(\mathbb{A})$ is a smooth function $\varphi : GL_n(\mathbb{A}) \to \mathbb{C}$ with these properties.
1. $\varphi(\gamma g) = \varphi(g)$ for $\gamma \in GL_n(F)$.
2. $\varphi$ is right invariant under a compact open subgroup of $GL_n(\mathbb{A}_f)$.
3. $\varphi$ is $K_\infty$-finite: its right translates under $K_\infty$ span a space of finite dimension.
4. $\varphi$ is $Z(\mathfrak{g})$-finite: its images under $Z(\mathfrak{g})$ span a space of finite dimension.
5. $\varphi$ has moderate growth.

Lean: not stated yet

The space $\mathcal{A}$ of automorphic forms is not a representation of $GL_n(\mathbb{A})$, because a right translate by $GL_n(F_\infty)$ of a $K_\infty$-finite function need not be $K_\infty$-finite. It is a $(\mathfrak{g}, K_\infty) \times GL_n(\mathbb{A}_f)$-module. This is the reason for the phrase "automorphic representation" in the sense of Borel and Jacquet: an irreducible subquotient of $\mathcal{A}$ as a $(\mathfrak{g}, K_\infty) \times GL_n(\mathbb{A}_f)$-module.

**Example 1.2.2 ($n = 1$).** For $n = 1$, $\mathfrak{g}$ is commutative and $K_\infty$-finiteness and $Z(\mathfrak{g})$-finiteness say that $\varphi$ is a finite sum of eigenfunctions of the derivatives in $F_\infty^\times$ and of the action of $K_\infty$. An automorphic form that is an eigenfunction of everything is a Hecke character $\chi : F^\times \backslash \mathbb{A}^\times \to \mathbb{C}^\times$, in the sense of Volume 3, Chapter 5. The general automorphic form is a finite linear combination of functions $\chi(x) (\log |x|_\mathbb{A})^m$.

**Example 1.2.3 (modular forms).** Let $f \in S_k(\Gamma_0(N))$ be a cusp form of Volume 4, and let $K_0(N) \subseteq GL_2(\widehat{\mathbb{Z}})$ be the group of Example 1.1.6. By Example 1.1.6, each $g \in GL_2(\mathbb{A}_\mathbb{Q})$ is $\gamma g_\infty k$ with $\gamma \in GL_2(\mathbb{Q})$, $g_\infty \in GL_2(\mathbb{R})^+$ and $k \in K_0(N)$. Put
$$\varphi_f(g) = f(g_\infty i) \, j(g_\infty, i)^{-k} (\det g_\infty)^{k/2}, \qquad j\Big(\begin{pmatrix} a & b \\ c & d \end{pmatrix}, \tau\Big) = c\tau + d.$$
The cocycle relation $j(gh, \tau) = j(g, h\tau) j(h, \tau)$ and the modularity of $f$ show that the right side does not depend on the decomposition. The function $\varphi_f$ is an automorphic form. It transforms under $K_\infty = O(2)$ by the character $\kappa_\theta \mapsto e^{ik\theta}$ of $SO(2)$, it is killed by the lowering operator because $f$ is holomorphic, and the Casimir operator acts by the scalar $\frac{k}{2}(1 - \frac{k}{2})$. Volume 5 proves these facts. For $f$ with a character $\chi$ modulo $N$, the same formula on $K_1(N)$ works, and $\varphi_f$ has the central character of the Hecke character of $\chi$.

### Constant terms and cusp forms

A parabolic subgroup $P$ of $GL_n$ defined over $F$ is the stabilizer of a flag of subspaces of $F^n$. It is *standard* if it contains $B$. The standard parabolic subgroups correspond to the ordered partitions $n = n_1 + \cdots + n_k$, and $P_{(n_1, \ldots, n_k)}$ is the group of block upper triangular matrices with diagonal blocks of sizes $n_1, \ldots, n_k$. Its unipotent radical $U_P$ is the group of the block upper triangular matrices with identity blocks on the diagonal. The maximal ones are $P_r = P_{(r, n-r)}$ for $0 < r < n$, with $U_{P_r} = \{ \begin{pmatrix} 1_r & X \\ 0 & 1_{n-r} \end{pmatrix} \}$. The quotient $U_P(F) \backslash U_P(\mathbb{A})$ is compact, by Volume 1, Theorem 3.2.4, applied to each entry in a sequence of normal subgroups with abelian quotients. We give it the invariant probability measure.

**Definition 1.2.4 (constant term, cusp form).** The *constant term* of a continuous function $\varphi$ on $GL_n(F) \backslash GL_n(\mathbb{A})$ along a parabolic subgroup $P$ is
$$\varphi_P(g) = \int_{U_P(F) \backslash U_P(\mathbb{A})} \varphi(ug) \, du.$$
An automorphic form $\varphi$ is a *cusp form* if $\varphi_P = 0$ for each parabolic subgroup $P \ne GL_n$ defined over $F$. We write $\mathcal{A}_0$ for the space of cusp forms.

Lean: `Langlands.IsCuspForm`, a definition of the project, with the differences of Remark 1.2.6

**Lemma 1.2.5 (maximal parabolics suffice).** A continuous function $\varphi$ on $GL_n(F) \backslash GL_n(\mathbb{A})$ with $\varphi_{P_r} = 0$ for $0 < r < n$ has $\varphi_P = 0$ for every proper parabolic subgroup $P$ defined over $F$.

Lean: not stated yet

*Proof.* Each parabolic subgroup defined over $F$ is $\gamma P' \gamma^{-1}$ for a standard $P'$ and some $\gamma \in GL_n(F)$, because $GL_n(F)$ acts transitively on the flags of a given type. Then $U_P = \gamma U_{P'} \gamma^{-1}$, and the substitution $u = \gamma u' \gamma^{-1}$ gives $\varphi_P(g) = \varphi_{P'}(\gamma^{-1} g)$, by the left invariance of $\varphi$. So we may take $P$ standard. A proper standard parabolic $P$ lies in some $P_r$, and then $U_P \supseteq U_{P_r}$. The group $U_{P_r}$ is normal in $U_P$, because $U_{P_r}$ is normal in $P_r$. So the integral over $U_P(F) \backslash U_P(\mathbb{A})$ can be done in two steps, first over $U_{P_r}(F) \backslash U_{P_r}(\mathbb{A})$ and then over the quotient:
$$\varphi_P(g) = \int_{U_P(F) U_{P_r}(\mathbb{A}) \backslash U_P(\mathbb{A})} \varphi_{P_r}(ug) \, du = 0. \qquad \square$$

In the proof we used that the measure on $U_P(F) \backslash U_P(\mathbb{A})$ is the product of the measures on the two quotients. This holds because all three are invariant probability measures on compact groups or homogeneous spaces.

**Remark 1.2.6 (the cusp forms of the Lean project).** A cusp form in the sense of `Langlands.IsCuspForm N φ` is a continuous function $\varphi$ with these properties: it is left invariant under $GL_n(K)$, right invariant under $K(N)$, it has a central character $\omega$, it satisfies $|\varphi(g)| \le C |\det g|_\mathbb{A}^s$ for constants $C$ and $s$, and $\varphi_{P_r} = 0$ for $0 < r < n$. It differs from Definition 1.2.4 in four ways.
1. It is continuous, not smooth. There is no $K_\infty$-finiteness and no $Z(\mathfrak{g})$-finiteness.
2. The growth condition is in terms of $|\det g|_\mathbb{A}$ and not of the height $\|g\|$. The norm on the adele ring of Mathlib is the product of the local norms, so $\|\det g\|$ in Lean is the idelic absolute value.
3. The constant term is an integral over $(\mathbb{A}_K / K)^{n \times n}$, of which only the block of $X$ enters, for every invariant probability measure. There is one such measure, the Haar measure, but Mathlib does not yet know that $\mathbb{A}_K / K$ is compact.
4. Only the maximal standard parabolics are used, which is enough by Lemma 1.2.5.

The second point is harmless for cusp forms: a cusp form with a central character is bounded on $GL_n(\mathbb{A})^1$, by Proposition 1.2.7 below, and so it satisfies $|\varphi(g)| = |\omega(a_t)| |\varphi(g^1)| \le C |\det g|^s$ for $g = g^1 a_t$, with the notation of Section 1.1. The first point does not change the eigenvalues of the Hecke operators at the unramified places. A continuous form in the sense of Lean, after a twist by a power of $|\det|$, lies in the space $L^2_0$ of Section 1.3. That space is a Hilbert direct sum of cuspidal automorphic representations, and the projections to the summands commute with the Hecke operators. So each Hecke eigensystem of a Lean cusp form at almost all places is the eigensystem of the smooth $K_\infty$-finite vectors of a cuspidal automorphic representation. The converse is clear. This is the argument of the implementation notes of `Langlands/Statements/Automorphic.lean`.

**Example 1.2.7 ($n = 1$).** For $n = 1$ there is no proper parabolic subgroup, so every automorphic form is cuspidal. The constant function $1$ on $GL_1(\mathbb{A}_K) = \mathbb{A}_K^\times$ is a cusp form of level 1.

Lean: `Langlands.isCuspForm_one`, proved in the project

### Cusp forms are bounded

For $n \ge 2$ the constant function $1$ is an automorphic form and not a cusp form: its constant term along every $P$ is $1$. So are the Eisenstein series of Volume 5 and of Langlands. The cusp forms are the forms that decay at the cusps, and this is the content of the next proposition.

**Proposition 1.2.8 (rapid decay).** Let $\varphi$ be a cusp form and let $\mathfrak{S} = \Omega A_c K$ be a Siegel set as in Theorem 1.1.7. For each $m > 0$ there is a constant $C_m$ with $|\varphi(\omega a k)| \le C_m \prod_{i < n} (t_i / t_{i+1})^{-m}$ for $\omega a k \in \mathfrak{S}$ and $a = \mathrm{diag}(t_1, \ldots, t_n)$. In particular, if the central character of $\varphi$ is unitary, then $\varphi$ is bounded on $GL_n(\mathbb{A})$.

Lean: not stated yet

*Proof for $n = 2$ and $F = \mathbb{Q}$.* Write $u(x) = \begin{pmatrix} 1 & x \\ 0 & 1 \end{pmatrix}$ and fix the character $\psi$ of $\mathbb{Q} \backslash \mathbb{A}$ of Volume 0, Section 3.2. The right translates $R(k)\varphi$, $k \in K$, lie in a space of finite dimension of cusp forms, by the $K_\infty$-finiteness and because $K$ normalizes a level $K(N)$ of $\varphi$. So it is enough to bound $\varphi$ at $u(x) a$ with $x$ in a compact set and $a = \mathrm{diag}(t, 1)$, $t \ge c$, at the infinite place. The function $x \mapsto \varphi(u(x) g)$ on the compact group $\mathbb{Q} \backslash \mathbb{A}$ has the Fourier expansion
$$\varphi(u(x) g) = \sum_{\xi \in \mathbb{Q}} \psi(\xi x) W_\xi(g), \qquad W_\xi(g) = \int_{\mathbb{Q} \backslash \mathbb{A}} \varphi(u(y) g) \psi(-\xi y) \, dy.$$
The term $W_0$ is the constant term, so it vanishes. The invariance under $u(y) \in K(N)$ for $y \in N\widehat{\mathbb{Z}}$ shows $W_\xi(a) = 0$ unless $\xi \in N^{-1} \mathbb{Z}$, and the invariance under $\mathrm{diag}(\xi, 1)$ gives $W_\xi(a) = W_1(\mathrm{diag}(\xi t, 1))$, with $t$ at the infinite place only. Let $X = \begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix}$ at the infinite place and $R(X)$ the derivative of the right translation. From $\mathrm{diag}(y, 1) u(s) = u(ys) \mathrm{diag}(y, 1)$ one gets $W_1(R(X)^m \varphi; \mathrm{diag}(y,1)) = (2\pi i y_\infty)^m W_1(\varphi; \mathrm{diag}(y,1))$ up to a sign. The form $R(X)^m \varphi$ has moderate growth, so its coefficient is at most $C |\xi t|^r$ for some $r$ independent of $m$. Hence $|W_\xi(a)| \le C_m |\xi t|^{r - m}$, and the sum over $0 \ne \xi \in N^{-1}\mathbb{Z}$ gives $|\varphi(u(x) a)| \le C'_m t^{r-m}$ for $m > r + 1$. So $\varphi$ decreases rapidly on the Siegel set, and it is bounded on $GL_2(\mathbb{Q}) Z(\mathbb{A}) \mathfrak{S} = GL_2(\mathbb{A})$ when $|\omega| = 1$. $\square$

For a general number field the proof is the same, with a derivative at each infinite place. For $n \ge 3$ one uses the constant terms along all the maximal parabolics and an induction on $n$, see Getz and Hahn, or Moeglin and Waldspurger, Chapter I.2. So a cusp form with a unitary central character lies in $L^2(Z(\mathbb{A}) GL_n(F) \backslash GL_n(\mathbb{A}), \omega)$, which has finite volume by Theorem 1.1.7. The Lean statement `Langlands.RamanujanGL` of Chapter 2 asks for a bounded cusp form, and its docstring notes that this is the same as a unitary central character.

**Corollary 1.2.9 (growth in the Lean sense).** A cusp form $\varphi$ with central character $\omega$ satisfies $|\varphi(g)| \le C |\det g|_\mathbb{A}^s$ with $s = \mathrm{Re}(\sigma)/n$, where $|\omega(z)| = |z|_\mathbb{A}^{\sigma}$. So it is a cusp form in the sense of `Langlands.IsCuspForm`.

Lean: not stated yet

*Proof.* Every quasi-character of $F^\times \backslash \mathbb{A}^\times$ is a unitary character times $|\cdot|_\mathbb{A}^\sigma$, by Volume 3, Chapter 5. Then $\varphi \otimes |\det|^{-\sigma/n}$ has a unitary central character, so it is bounded by Proposition 1.2.7. $\square$
