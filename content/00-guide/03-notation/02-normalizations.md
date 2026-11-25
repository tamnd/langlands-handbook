---
title: Characters, measures and parameters
nodes: []
sources: [Tat79]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Characters, measures and parameters

### Additive characters and Haar measures

An $\varepsilon$-factor depends on a nontrivial continuous character $\psi : K \to \mathbb{C}^\times$, and so do the Whittaker models of Volume 6. Each statement that uses $\psi$ names it. For $\mathbb{Q}_p$ the standard character is
$$\psi_p(x) = e^{2 \pi i \{x\}_p},$$
where $\{x\}_p \in \mathbb{Z}[1/p]$ is the fractional part of $x$, so that $0 \le \{x\}_p < 1$ and $x - \{x\}_p \in \mathbb{Z}_p$. It is trivial on $\mathbb{Z}_p$ and not on $p^{-1}\mathbb{Z}_p$. For $\mathbb{R}$ the standard character is $\psi_\infty(x) = e^{-2 \pi i x}$. The sign in $\psi_\infty$ makes the product $\psi = \prod_v \psi_v$ a character of $\mathbb{A}_{\mathbb{Q}}$ that is trivial on $\mathbb{Q}$. For a number field $F$ the standard character is $\psi \circ \mathrm{Tr}_{F/\mathbb{Q}}$, Its local component at a place $v$ over a prime $p$ is $\psi_p \circ \mathrm{Tr}_{F_v / \mathbb{Q}_p}$, and at an infinite place it is $\psi_\infty \circ \mathrm{Tr}_{F_v / \mathbb{R}}$.

The Fourier transform of a Schwartz function $f$ on $K$ is $\hat f(y) = \int_K f(x) \psi(xy) \, dx$. A Haar measure $dx$ is *self-dual* for $\psi$ if $\hat{\hat f}(x) = f(-x)$ for all $f$. For $\psi_p$ the self-dual measure gives $\mathbb{Z}_p$ the volume 1, and for $\psi_\infty$ it is the Lebesgue measure. The handbook always takes the self-dual measure. With these measures the quotient $\mathbb{A}_{\mathbb{Q}} / \mathbb{Q}$ has volume 1. On $K^\times$ the handbook takes the measure $d^\times x$ that gives $\mathcal{O}_K^\times$ the volume 1, unless a statement says otherwise.

### The dependence of the epsilon factor on the character

For $a \in K^\times$ let $\psi_a(x) = \psi(ax)$. Each nontrivial character of $K$ is $\psi_a$ for a unique $a$. Thus a change of $\psi$ is a change of $a$, and the $\varepsilon$-factor changes by a simple rule.

**Remark 3.2.1 (change of the additive character).** Let $\chi$ be a character of $K^\times$, and let the $\varepsilon$-factors be defined by Tate's local functional equation with the self-dual measures. Then
$$\varepsilon(\chi, s, \psi_a) = \chi(a) \, |a|_K^{s - 1/2} \, \varepsilon(\chi, s, \psi).$$
For a representation $\pi$ of $GL_n(K)$ with central character $\omega_\pi$ the rule becomes $\varepsilon(\pi, s, \psi_a) = \omega_\pi(a) |a|_K^{n(s - 1/2)} \varepsilon(\pi, s, \psi)$. Thus the $\varepsilon$-factors of a statement are well defined only after $\psi$ is fixed, and two sources with different $\psi$ give factors that differ by this rule. If $\chi$ is unramified and $\psi$ is trivial on $\mathcal{O}_K$ and not on $\mathfrak{p}_K^{-1}$, then $\varepsilon(\chi, s, \psi) = 1$.

### Satake parameters

Let $\pi$ be an irreducible smooth representation of $GL_n(K)$ that is unramified, that is, it has a nonzero vector fixed by $GL_n(\mathcal{O}_K)$. Then $\pi$ is a subquotient of the representation induced from unramified characters $\chi_1, \dots, \chi_n$ of $K^\times$, with the normalized induction. The *Satake parameter* of $\pi$ is the conjugacy class of $\mathrm{diag}(\chi_1(\varpi), \dots, \chi_n(\varpi))$ in $GL_n(\mathbb{C})$. The normalized induction contains the factor $\delta^{1/2}$ of the modulus character. With it, $\pi$ is tempered if and only if each $\chi_i(\varpi)$ has absolute value 1. This is the *unitary normalization*, and the handbook uses it unless a statement says otherwise. Under the local correspondence the representation $\mathrm{rec}_n(\pi)$ is unramified with $N = 0$, and $r(\Phi)$ has the eigenvalues $\chi_1(\varpi), \dots, \chi_n(\varpi)$. The geometric normalization gives this formula without an inverse.

For a newform $f$ of weight $k$ on $\Gamma_0(N)$ and a prime $p \nmid N$, the two normalizations are explicit. The unitary Satake parameters of $\pi_f$ at $p$ are the numbers $\alpha_p, \beta_p$ with
$$\alpha_p + \beta_p = a_p(f) \, p^{-(k-1)/2}, \qquad \alpha_p \beta_p = 1.$$
The *arithmetic* parameters are $p^{(k-1)/2} \alpha_p$ and $p^{(k-1)/2} \beta_p$. They are the roots of $X^2 - a_p(f) X + p^{k-1}$, and they are algebraic numbers. For $k = 2$ and a form with rational coefficients they are the eigenvalues of a geometric Frobenius on $H^1$ of the elliptic curve of $f$. In the unitary normalization the bound of Ramanujan and Petersson reads $|\alpha_p| = |\beta_p| = 1$.

The papers on the Galois representations of automorphic representations of $GL_n$ pass from the unitary to the arithmetic normalization by a twist by a power of $|\det|$, often $|\det|^{(1-n)/2}$, and some of them also take a contragredient. Each statement of the handbook that compares the two sides gives the twist explicitly.

### q-expansions and the width of a cusp

Let $\Gamma$ be a congruence subgroup of $SL_2(\mathbb{Z})$. The *width* of the cusp $\infty$ is the least $h \ge 1$ such that $\begin{pmatrix} 1 & h \\ 0 & 1 \end{pmatrix} \in \pm \Gamma$. A modular form $f$ of even weight on $\Gamma$ has an expansion in $q_h = e^{2 \pi i \tau / h}$. For $\Gamma_0(N)$ and $\Gamma_1(N)$ the width is 1, and the expansion is in $q = e^{2\pi i \tau}$. For $\Gamma(N)$ the width is $N$.

**Example 3.2.2 (the wrong variable).** Let $f = \sum_{n \ge 1} a_n q^n$ be a cusp form on $\Gamma_0(N)$. In the variable $q_N = e^{2\pi i \tau / N}$ one has $q = q_N^N$, so $f = \sum_{n \ge 1} a_n q_N^{nN}$. For $N \ge 2$ the coefficient of $q_N^1$ is 0. A statement that reads the coefficients of $f$ in $q_N$ instead of $q$ finds 0 where it expects $a_1$. For a curve $E$ the number $a_1(E)$ is 1, so such a statement asks for $1 = 0$. Chapter 4 shows that a published Lean statement of the modularity theorem has this error.

### Centres of functional equations

An automorphic L-function in the unitary normalization has its functional equation under $s \mapsto 1 - s$. The L-function of an elliptic curve has it under $s \mapsto 2 - s$, and the L-function $L(f, s) = \sum a_n(f) n^{-s}$ of a form of weight $k$ has it under $s \mapsto k - s$. The two are related by $L(f, s) = L(\pi_f, s - (k-1)/2)$. Thus the centre $s = 1$ of $L(E, s)$ is the centre $s = 1/2$ of $L(\pi_f, s)$.
