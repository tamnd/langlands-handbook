---
title: Galois representations of eigenforms
nodes: [LGG3ZW59RX]
sources: [Del69]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Galois representations of eigenforms

This section attaches to each normalized eigenform of weight $k \ge 2$ a representation of $G_\mathbb{Q}$ of dimension 2 over $\bar{\mathbb{Q}}_\ell$. The statement uses Frobenius elements, and there are two normalizations of them. We fix them first, and then we show that in dimension 2 the two normalizations give equivalent statements. Let $\bar{\mathbb{Q}}$ be an algebraic closure of $\mathbb{Q}$, let $\bar{\mathbb{Z}}$ be the ring of algebraic integers in it, and let $G_\mathbb{Q} = \mathrm{Gal}(\bar{\mathbb{Q}}/\mathbb{Q})$ with its profinite topology.

### Frobenius elements

Let $p$ be a prime and $\mathfrak{P}$ a maximal ideal of $\bar{\mathbb{Z}}$ that contains $p$. The residue field $\bar{\mathbb{Z}}/\mathfrak{P}$ is an algebraic closure of $\mathbb{F}_p$. The *decomposition group* $D_\mathfrak{P}$ is the stabilizer of $\mathfrak{P}$ in $G_\mathbb{Q}$, and the *inertia group* $I_\mathfrak{P}$ is the group of the $\sigma \in D_\mathfrak{P}$ with $\sigma(x) \equiv x \bmod \mathfrak{P}$ for all $x \in \bar{\mathbb{Z}}$. The map $D_\mathfrak{P} \to \mathrm{Gal}(\bar{\mathbb{F}}_p/\mathbb{F}_p)$ is surjective with kernel $I_\mathfrak{P}$, as in algebraic number theory for each finite Galois extension, by a limit argument.

**Definition 2.4.1 (Frobenius elements).** An element $\sigma \in G_\mathbb{Q}$ is an *arithmetic Frobenius at $\mathfrak{P}$* if $\sigma(x) \equiv x^p \bmod \mathfrak{P}$ for all $x \in \bar{\mathbb{Z}}$. It is an *arithmetic Frobenius at $p$* if it is an arithmetic Frobenius at some maximal ideal $\mathfrak{P}$ over $p$. The inverse of an arithmetic Frobenius is a *geometric Frobenius*. We write $\mathrm{Frob}_p$ for an arithmetic Frobenius at $p$ and $\Phi_p$ for a geometric one.

Lean: `Langlands.IsFrobeniusAt`

An arithmetic Frobenius at $\mathfrak{P}$ lies in $D_\mathfrak{P}$: if $x \in \mathfrak{P}$ then $\sigma(x) \equiv x^p \equiv 0$, so $\sigma(\mathfrak{P}) \subset \mathfrak{P}$. The Lean predicate `Langlands.IsFrobeniusAt p σ` says that there is a maximal ideal $Q$ of $\bar{\mathbb{Z}}$ over $p$ with `IsArithFrobAt ℤ σ Q`, the predicate of Mathlib for $\sigma(x) - x^p \in Q$ for all $x$. So it is the arithmetic Frobenius. The fidelity theorem `Langlands.Fidelity.exists_isFrobeniusAt` proves that an arithmetic Frobenius exists at each prime. The handbook writes $\Phi$ for a geometric Frobenius and $\mathrm{Frob}$ for an arithmetic one, as in Volume 0, Definition 3.1.2. The reciprocity map of Volume 3 sends uniformizers to geometric Frobenius elements.

**Definition 2.4.2 (unramified homomorphisms).** A homomorphism $\rho$ from $G_\mathbb{Q}$ to a group $H$ is *unramified at $p$* if $\rho(I_\mathfrak{P}) = 1$ for each maximal ideal $\mathfrak{P}$ of $\bar{\mathbb{Z}}$ over $p$.

Lean: `Langlands.IsUnramifiedAt`

**Lemma 2.4.3 (the Frobenius class).** Let $\rho : G_\mathbb{Q} \to H$ be unramified at $p$. Then the elements $\rho(\sigma)$, for $\sigma$ an arithmetic Frobenius at $p$, form one conjugacy class of $H$. If $H = GL_n(F)$ for a field $F$, the characteristic polynomial of $\rho(\mathrm{Frob}_p)$ depends only on $p$.

Lean: not stated yet

*Proof.* Let $\sigma$ and $\sigma'$ be arithmetic Frobenius elements at the same $\mathfrak{P}$. Then $\sigma^{-1}\sigma' \in D_\mathfrak{P}$ acts trivially on $\bar{\mathbb{Z}}/\mathfrak{P}$, so it is in $I_\mathfrak{P}$, and $\rho(\sigma) = \rho(\sigma')$. Let $\mathfrak{P}'$ be another maximal ideal over $p$. The group $G_\mathbb{Q}$ acts transitively on these ideals, so $\mathfrak{P}' = \tau\mathfrak{P}$ for some $\tau$. If $\sigma$ is an arithmetic Frobenius at $\mathfrak{P}$, then $\tau\sigma\tau^{-1}(x) = \tau(\sigma(\tau^{-1}x)) \equiv \tau((\tau^{-1}x)^p) = x^p \bmod \tau\mathfrak{P}$, so $\tau\sigma\tau^{-1}$ is an arithmetic Frobenius at $\mathfrak{P}'$. Conversely every element of the class of $\rho(\sigma)$ is $\rho(\tau\sigma\tau^{-1})$ for some $\tau$. $\square$

We need two more facts on Galois representations. Let $\ell$ be a prime and let $F$ be $\bar{\mathbb{Q}}_\ell$ or a finite extension of $\mathbb{Q}_\ell$. A continuous representation $\rho : G_\mathbb{Q} \to GL_n(\bar{\mathbb{Q}}_\ell)$ takes values in $GL_n(E)$ for a finite extension $E$ of $\mathbb{Q}_\ell$, by a Baire category argument, and it is unramified outside a finite set of primes when it comes from geometry, as all the representations of this section do. The *Chebotarev density theorem* says that for a finite set $S$ of primes the conjugates of the arithmetic Frobenius elements at the primes $p \notin S$ are dense in $G_\mathbb{Q}$. With the theorem of Brauer and Nesbitt it gives: two semisimple continuous representations $\rho, \rho' : G_\mathbb{Q} \to GL_n(\bar{\mathbb{Q}}_\ell)$, unramified outside $S$, with $\mathrm{tr}\,\rho(\mathrm{Frob}_p) = \mathrm{tr}\,\rho'(\mathrm{Frob}_p)$ for all $p \notin S$, are isomorphic. In particular continuous characters are determined by their values at the $\mathrm{Frob}_p$ with $p \notin S$.

The *$\ell$-adic cyclotomic character* $\varepsilon_\ell : G_\mathbb{Q} \to \mathbb{Z}_\ell^\times$ is defined by $\sigma(\zeta) = \zeta^{\varepsilon_\ell(\sigma)}$ for all roots of unity $\zeta$ of $\ell$-power order. It is unramified at $p \ne \ell$, with $\varepsilon_\ell(\mathrm{Frob}_p) = p$, because $\mathrm{Frob}_p(\zeta) \equiv \zeta^p$ modulo $\mathfrak{P}$ and the roots of unity of order prime to $p$ are distinct modulo $\mathfrak{P}$. A Dirichlet character $\chi$ modulo $N$ is a character of $G_\mathbb{Q}$ through $G_\mathbb{Q} \to \mathrm{Gal}(\mathbb{Q}(\zeta_N)/\mathbb{Q}) \cong (\mathbb{Z}/N\mathbb{Z})^\times$, where $\sigma \mapsto a$ if $\sigma(\zeta_N) = \zeta_N^a$. In the same way $\chi(\mathrm{Frob}_p) = \chi(p)$ for $p \nmid N$. A complex conjugation $c$ has $\varepsilon_\ell(c) = -1$ and $\chi(c) = \chi(-1)$.

### The theorem of Eichler, Shimura and Deligne

**Theorem 2.4.4 (Eichler-Shimura, Deligne).** Let $N \ge 1$, $k \ge 2$, let $\chi$ be a Dirichlet character modulo $N$ and let $f \in S_k(N, \chi)$ be a normalized eigenform. Let $\ell$ be a prime and $\iota : \bar{\mathbb{Q}}_\ell \to \mathbb{C}$ an isomorphism of fields. There is a continuous representation
$$\rho_{f,\iota} : G_\mathbb{Q} \to GL_2(\bar{\mathbb{Q}}_\ell)$$
such that for each prime $p \nmid N\ell$, $\rho_{f,\iota}$ is unramified at $p$ and
$$\iota\bigl(\mathrm{tr}\,\rho_{f,\iota}(\mathrm{Frob}_p)\bigr) = a_p(f), \qquad \iota\bigl(\det\rho_{f,\iota}(\mathrm{Frob}_p)\bigr) = \chi(p) p^{k-1}.$$

Node: LGG3ZW59RX · Lean: `Langlands.EichlerShimuraDeligne`

The case $k = 2$ is due to Eichler and Shimura, and the case $k \ge 3$ to Deligne, [Del69, Theorem 6.1]. The outline of the proof for $k = 2$ is below. By Chebotarev and Brauer-Nesbitt the semisimplification of $\rho_{f,\iota}$ is unique up to isomorphism. Ribet proved that $\rho_{f,\iota}$ is irreducible when $f$ is a newform.

**Remark 2.4.5 (the Lean form).** The statement `Langlands.EichlerShimuraDeligne` takes $N > 0$, $k \ge 2$, a Dirichlet character $\chi$ modulo $N$ and a cusp form $f$ on $\Gamma_1(N)$ of weight $k$ with `IsNormalizedEigenformWithCharacter f χ` of Definition 2.1.4. For each prime $\ell$ and each ring isomorphism $\iota$ from `PadicAlgCl ℓ`, the algebraic closure of $\mathbb{Q}_\ell$ in Mathlib, to $\mathbb{C}$, it asks for a continuous homomorphism $\rho$ from $G_\mathbb{Q}$ to $GL_2$ of `PadicAlgCl ℓ`, with `IsUnramifiedAt ρ p` for each prime $p \nmid N\ell$, and with $\iota(\mathrm{tr}\,\rho(\sigma)) = a_p(f)$ and $\iota(\det\rho(\sigma)) = \chi(p)p^{k-1}$ for every $\sigma$ with `IsFrobeniusAt p σ`. Such an $\iota$ exists by the axiom of choice, since both fields are algebraically closed of characteristic 0 and of the cardinality of the continuum; it is not continuous. By Remark 2.1.11 the statement for all normalized eigenforms is equivalent to the statement for newforms. The textbook form has values in a finite extension $E_\lambda$ of $\mathbb{Q}_\ell$ that contains the coefficients; as noted above, a continuous $\rho$ with values in $GL_2(\bar{\mathbb{Q}}_\ell)$ has values in such a field. The Lean statement uses arithmetic Frobenius elements, as Theorem 2.4.4 does.

**Proposition 2.4.6 (the determinant).** Let $\rho = \rho_{f,\iota}$ be as in Theorem 2.4.4, and view $\chi$ as a character of $G_\mathbb{Q}$ with values in $\bar{\mathbb{Q}}_\ell$ through $\iota^{-1}$. Then $\det \rho = \chi\,\varepsilon_\ell^{k-1}$. In particular $\rho$ is *odd*: $\det\rho(c) = -1$ for each complex conjugation $c$.

Lean: not stated yet

*Proof.* Both sides are continuous characters of $G_\mathbb{Q}$, unramified outside $N\ell$, and at $\mathrm{Frob}_p$ for $p \nmid N\ell$ both take the value $\iota^{-1}(\chi(p))p^{k-1}$. By Chebotarev they are equal. For the oddness, $-I \in \Gamma_0(N)$ acts on $M_k(\Gamma_1(N))$ by $f|_k(-I) = (-1)^k f$, and also by $\langle -1 \rangle f = \chi(-1)f$. Since $f \ne 0$, $\chi(-1) = (-1)^k$. So $\det\rho(c) = \chi(-1)\varepsilon_\ell(c)^{k-1} = (-1)^k(-1)^{k-1} = -1$. $\square$

### The construction in weight 2

We outline the construction of Eichler and Shimura, following Diamond and Shurman, Chapters 6 to 9, and Shimura, Chapter 7. Let $X = X_1(N)$ be the modular curve of Remark 1.1.11, a smooth projective curve over $\mathbb{Q}$ of genus $g = \dim S_2(\Gamma_1(N))$, and let $J = J_1(N)$ be its Jacobian, an abelian variety over $\mathbb{Q}$ of dimension $g$.

1. Over $\mathbb{C}$, the map $f \mapsto f(\tau)\,d\tau$ identifies $S_2(\Gamma_1(N))$ with the space of holomorphic differentials on $X(\mathbb{C})$, and $J(\mathbb{C}) = S_2(\Gamma_1(N))^\vee / H_1(X(\mathbb{C}), \mathbb{Z})$ by the theorem of Abel and Jacobi.
2. A double coset $\Gamma_1\alpha\Gamma_1$ defines a correspondence on $X$, so an endomorphism of $J$, and this endomorphism is defined over $\mathbb{Q}$. So the Hecke algebra $\mathbb{T}$ acts on $J$, and on its Tate module $T_\ell J = \varprojlim J[\ell^n]$, compatibly with the action of $G_\mathbb{Q}$.
3. The module $V_\ell J = T_\ell J \otimes \mathbb{Q}_\ell$ has dimension $2g$, and it is free of rank 2 over $\mathbb{T} \otimes \mathbb{Q}_\ell$, because $H_1(X(\mathbb{C}), \mathbb{Q})$ is free of rank 2 over $\mathbb{T} \otimes \mathbb{Q}$.
4. The eigenvalues of $f$ give a ring homomorphism $\theta_f : \mathbb{T} \to \mathbb{C}$, and $\iota^{-1}\circ\theta_f$ extends to $\mathbb{T} \otimes \mathbb{Q}_\ell \to \bar{\mathbb{Q}}_\ell$. The space $V_f = V_\ell J \otimes_{\mathbb{T} \otimes \mathbb{Q}_\ell} \bar{\mathbb{Q}}_\ell$ has dimension 2, with an action of $G_\mathbb{Q}$. This is $\rho_{f,\iota}$.
5. For $p \nmid N$ the curve $X$ has good reduction at $p$, a theorem of Igusa, so $J$ has good reduction at $p$, and by the criterion of Néron, Ogg and Shafarevich $V_\ell J$ is unramified at $p \nmid N\ell$.
6. On the reduction $\tilde{J}$ of $J$ modulo $p$, with Frobenius endomorphism $F$ and Verschiebung $V$, $FV = p$, the *Eichler-Shimura relation* $T_p = F + \langle p \rangle V$ holds. Multiplying by $F$ gives $F^2 - T_pF + p\langle p\rangle = 0$.
7. The reduction map identifies $T_\ell J$ with $T_\ell\tilde{J}$ for $p \ne \ell$, and an arithmetic Frobenius at $p$ acts on $\tilde{J}(\bar{\mathbb{F}}_p)$ as $F$, since both raise the coordinates of the points to the power $p$. So $\mathrm{Frob}_p$ satisfies $X^2 - a_p X + \chi(p)p$ on $V_f$, and a further argument with the Weil pairing shows that this is its characteristic polynomial.

For $k \ge 3$, Deligne replaces $J$ by the étale cohomology $H^1$ of $X_1(N)$ with coefficients in the sheaf $\mathrm{Sym}^{k-2}$ of the Tate module of the universal elliptic curve, or $H^{k-1}$ of the Kuga-Sato variety, and he proves the analogue of the Eichler-Shimura relation. For $k = 1$, Deligne and Serre construct $\rho$ by congruences with forms of higher weight, and its image is finite; Section 2.5 returns to this case.

### Arithmetic and geometric normalizations

For a representation $\rho : G \to GL_n(F)$, the *dual* (or contragredient) representation is $\rho^\vee(g) = {}^t\rho(g)^{-1}$, the action on the dual space.

**Proposition 2.4.7 (duals and the two normalizations).** Let $\rho : G_\mathbb{Q} \to GL_n(F)$ be a representation over a field $F$, unramified at $p$.
1. The characteristic polynomial of $\rho^\vee(\Phi_p)$ is that of $\rho(\mathrm{Frob}_p)$. So $\rho$ has trace $a$ and determinant $d$ at the arithmetic Frobenius elements at $p$ if and only if $\rho^\vee$ has trace $a$ and determinant $d$ at the geometric Frobenius elements at $p$.
2. If $n = 2$, then $\rho^\vee \cong \rho \otimes (\det\rho)^{-1}$.

Lean: not stated yet

*Proof.* For part 1, $\rho^\vee(\mathrm{Frob}_p^{-1}) = {}^t\rho(\mathrm{Frob}_p)$, and a matrix and its transpose have the same characteristic polynomial. For part 2, let $J = \begin{pmatrix} 0 & 1 \\ -1 & 0 \end{pmatrix}$. For $A = \begin{pmatrix} a & b \\ c & d \end{pmatrix} \in GL_2(F)$ a direct computation gives
$$J A J^{-1} = \begin{pmatrix} d & -c \\ -b & a \end{pmatrix} = \det(A)\, {}^tA^{-1}.$$
So $\rho^\vee(g) = \det\rho(g)^{-1}\, J\rho(g)J^{-1}$ for all $g$, and $J$ is an isomorphism from $\rho \otimes (\det\rho)^{-1}$ to $\rho^\vee$. $\square$

Let $\rho = \rho_{f,\iota}$ be as in Theorem 2.4.4. By Proposition 2.4.7 and Proposition 2.4.6, the representation
$$\rho' = \rho^\vee \cong \rho \otimes \chi^{-1}\varepsilon_\ell^{1-k}$$
is continuous, unramified outside $N\ell$, and has $\iota(\mathrm{tr}\,\rho'(\Phi_p)) = a_p(f)$ and $\iota(\det\rho'(\Phi_p)) = \chi(p)p^{k-1}$ at the geometric Frobenius elements. Conversely, a representation with these properties at the geometric Frobenius elements has a dual with the properties of Theorem 2.4.4. So the theorem with arithmetic Frobenius and the theorem with geometric Frobenius are equivalent statements, and in dimension 2 the two representations differ only by the twist by the character $\chi^{-1}\varepsilon_\ell^{1-k}$. They have the same image in $PGL_2(\bar{\mathbb{Q}}_\ell)$, and one is irreducible if and only if the other is. Constructions in étale cohomology, as in [Del69], give the geometric normalization in a natural way, since $\Phi_p$ acts on $H^1$ with trace $a_p$. The Tate module of item 7 above is dual to $H^1$, and on it the arithmetic normalization is natural.

For a fixed $\rho$, the two normalizations are not interchangeable. By Lemma 2.3.1 the geometric trace of $\rho_{f,\iota}$ is
$$\mathrm{tr}\,\rho(\Phi_p) = \mathrm{tr}\,\rho(\mathrm{Frob}_p)^{-1} = \frac{\mathrm{tr}\,\rho(\mathrm{Frob}_p)}{\det\rho(\mathrm{Frob}_p)} = \iota^{-1}\bigl(\overline{a_p(f)}\,p^{1-k}\bigr),$$
which is not $a_p(f)$ unless $a_p(f) = 0$, since $|p^{1-k}\overline{a_p}| < |a_p|$ otherwise. So Theorem 2.4.4 with $\Phi_p$ in place of $\mathrm{Frob}_p$ is false for the same $\rho$; it is true for $\rho^\vee$. For an elliptic curve $E$ the representation on $V_\ell E = T_\ell E \otimes \mathbb{Q}_\ell$ has $\mathrm{tr}(\mathrm{Frob}_p) = a_p(E)$ and $\det = \varepsilon_\ell$, by the argument of item 7 and the Weil pairing. So by Theorem 2.2.11 and Chebotarev, $V_\ell E$ and $\rho_{f_E,\iota}$ have the same characteristic polynomials at Frobenius, and they are isomorphic after semisimplification. The space $H^1_{et}(E_{\bar{\mathbb{Q}}}, \mathbb{Q}_\ell) = V_\ell E^\vee$ is the geometric form.
