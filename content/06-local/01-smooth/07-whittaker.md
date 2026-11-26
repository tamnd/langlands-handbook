---
title: Whittaker models
nodes: []
sources: [BH06, JL70]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Whittaker models

A cusp form $f = \sum a_n q^n$ of Volume 4 is determined by its Fourier coefficients. The analogue for a representation of $GL_n(K)$ is its Whittaker model, a space of functions on $G$ that transform by a character of the unipotent group. For $GL_n$ the Whittaker model is unique when it exists, and it exists for almost all irreducible representations. It is the starting point of the local theory of $L$-functions of Jacquet, Piatetski-Shapiro and Shalika, which Chapter 3 uses to characterize the local Langlands correspondence. For $GL_2$ the Whittaker model gives the Kirillov model of [JL70], which describes every infinite-dimensional irreducible representation as a space of functions on $K^\times$.

### Whittaker functionals

Fix a nontrivial character $\psi$ of $K$. Let $N_n$ be the group of the upper triangular unipotent matrices of $GL_n(K)$, and let
$$\psi_N(u) = \psi(u_{12} + u_{23} + \dots + u_{n-1, n}), \quad u \in N_n.$$
This is a character of $N_n$, since the map $u \mapsto \sum_i u_{i, i+1}$ is a homomorphism. It is *generic*: its stabilizer in the diagonal torus is the center. Each character of $N_n$ that is nontrivial on each simple root group is conjugate to $\psi_N$ under the diagonal torus.

**Definition 1.7.1 (Whittaker functional and model).** Let $(\pi, V)$ be a smooth representation of $GL_n(K)$. A *Whittaker functional* is a linear form $\lambda : V \to \mathbb{C}$ with $\lambda(\pi(u) v) = \psi_N(u) \lambda(v)$ for $u \in N_n$. The representation $\pi$ is *generic* if it has a nonzero Whittaker functional. For a nonzero Whittaker functional $\lambda$, the *Whittaker model* of $\pi$ is the image of the map $v \mapsto W_v$, $W_v(g) = \lambda(\pi(g) v)$, into the space $\mathcal{W}(\psi)$ of the functions $W$ on $G$ with $W(u g) = \psi_N(u) W(g)$.

Lean: not stated yet

The map $v \mapsto W_v$ is $G$-equivariant for the right translation on $\mathcal{W}(\psi)$, so for irreducible $\pi$ it is injective. The Lean project has no Whittaker functionals for $GL_n$. The file `GSp4.lean` defines the analogue for $GSp_4$, `Langlands.SmoothRep.IsGSpGeneric`: a nonzero linear form $l$ with $l(\pi(u) v) = \psi(u_{12} + u_{23}) l(v)$ for $u$ in the unipotent radical of the Borel subgroup. Section 3.6 uses it.

Let $V(N_n, \psi)$ be the span of the vectors $\pi(u) v - \psi_N(u) v$, and $V_{N, \psi} = V / V(N_n, \psi)$. The Whittaker functionals are the linear forms on $V_{N, \psi}$. The argument of Proposition 1.3.5 shows that the functor $V \mapsto V_{N, \psi}$ is exact: a vector lies in $V(N_n, \psi)$ if and only if $\int_{N_0} \psi_N(u)^{-1} \pi(u) v \, du = 0$ for a large compact open subgroup $N_0$ of $N_n$.

### Uniqueness

**Theorem 1.7.2 (uniqueness of Whittaker models, Gelfand-Kazhdan, Shalika).** Let $\pi$ be an irreducible smooth representation of $GL_n(K)$. The space of Whittaker functionals of $\pi$ has dimension at most one.

Lean: not stated yet

*Sketch of proof.* This is the method of Gelfand and Kazhdan. Let $\sigma(g) = w_0 \, {}^t g^{-1} w_0^{-1}$, where $w_0$ is the antidiagonal permutation matrix. It is an automorphism of $G$ with $\sigma(N_n) = N_n$ and $\psi_N \circ \sigma = \psi_N^{-1}$ on $N_n$, up to a sign that can be absorbed. The main step is a statement on distributions: each distribution $D$ on $G$ with $D(\lambda(u_1) \rho(u_2) f) = \psi_N(u_1) \psi_N(u_2)^{-1} D(f)$, for left and right translations by $u_1, u_2 \in N_n$, is invariant under $f \mapsto f \circ \sigma \circ \iota$, where $\iota(g) = g^{-1}$. The proof uses the Bruhat decomposition and Bernstein's localization principle, which reduces it to each double coset $N_n \, w t \, N_n$. On the cosets that do not support such a distribution, the character $\psi_N$ forces it to vanish. On the remaining cosets, the monomial matrices $w t$ are fixed by $\sigma \circ \iota$.

The distribution statement implies, by a formal argument with the Bessel distributions $f \mapsto \mu(\pi(f) v)$, that $\dim \mathrm{Hom}_{N_n}(\pi, \psi_N) \cdot \dim \mathrm{Hom}_{N_n}(\pi^\vee, \psi_N^{-1}) \le 1$. The same method, applied to the distributions on $G$ that are invariant under conjugation, gives the theorem of Gelfand and Kazhdan that $\pi^\vee \cong \pi \circ \sigma$. The representation $\pi \circ \sigma$ has as many Whittaker functionals for $\psi_N^{-1}$ as $\pi$ has for $\psi_N$. So the two dimensions are equal, and each is at most one. $\square$

For $n = 2$ the theorem also follows from the Kirillov model below. The same method gives the multiplicity one theorem for $GL_n$ in the global theory: a cuspidal automorphic representation of $GL_n(\mathbb{A}_F)$ occurs in the space of cusp forms with multiplicity one. This is Shalika's theorem.

### The Kirillov model of GL(2)

Let $n = 2$, $N = N_2$, and identify $N$ with $K$ by $x \mapsto \left(\begin{smallmatrix} 1 & x \\ 0 & 1 \end{smallmatrix}\right)$. The *mirabolic subgroup* $P_2 = \left\{ \left(\begin{smallmatrix} a & x \\ 0 & 1 \end{smallmatrix}\right) \right\}$ is the semidirect product of $A = \{\mathrm{diag}(a, 1)\} \cong K^\times$ and $N$. The group $A$ acts on the characters of $N$ by $\psi_b \mapsto \psi_{ab}$, where $\psi_b(x) = \psi(bx)$, and it acts simply transitively on the nontrivial characters.

**Theorem 1.7.3 (the structure of representations of the mirabolic group).** Let $(\tau, V)$ be a smooth representation of $P_2$, and let $V(N)$ be the kernel of $V \to V_N$. There is an isomorphism of representations of $P_2$
$$V(N) \cong \mathrm{c\text{-}Ind}_N^{P_2} (\psi) \otimes V_{N, \psi},$$
where $N$ acts on $V_{N, \psi}$ by $\psi$ and $P_2$ acts on the space $\mathrm{c\text{-}Ind}_N^{P_2} \psi \cong C_c^\infty(K^\times)$ by $(\tau(a, x) \xi)(y) = \psi(xy) \xi(ay)$. In particular $V(N) = 0$ if and only if $V_{N, \psi} = 0$.

Lean: not stated yet

*Sketch of proof.* The Fourier transform identifies $C_c^\infty(N) = C_c^\infty(K)$, with convolution, with $C_c^\infty(\hat K)$, with pointwise product, where $\hat K \cong K$ by $b \mapsto \psi_b$. So $V$ becomes a nondegenerate module over $C_c^\infty(K)$ under pointwise multiplication, that is, $V$ is the space of compactly supported sections of a sheaf $\mathcal{F}$ on $K$. The stalk of $\mathcal{F}$ at $b$ is $V_{N, \psi_b}$, and the stalk at $0$ is $V_N$. The sections that vanish at $0$ are those supported on $K^\times$, and they form $V(N)$. The action of $A$ makes $\mathcal{F}|_{K^\times}$ an equivariant sheaf for a simply transitive action. So it is the constant sheaf with fiber $V_{N, \psi}$, twisted by the action, and its compactly supported sections are $C_c^\infty(K^\times) \otimes V_{N, \psi}$. The formula for the action of $N$ is the meaning of the stalks. $\square$

**Theorem 1.7.4 (Whittaker functionals of $GL_2$).** Let $\pi$ be an irreducible smooth representation of $GL_2(K)$. If $\pi$ is a character, then $\pi_{N, \psi} = 0$. If $\pi$ is infinite-dimensional, then $\dim \pi_{N, \psi} = 1$.

Lean: not stated yet

*Proof.* A character is trivial on $N$, so $\pi(u) v - \psi(u) v = (1 - \psi(u)) v$ and $\pi_{N, \psi} = 0$. Conversely, suppose that $\pi_{N, \psi} = 0$. By Theorem 1.7.3 applied to $\pi|_{P_2}$, the group $N$ acts trivially on $V$. Then the kernel of $\pi$ contains $N$, so it contains the normal subgroup generated by $N$, which is $SL_2(K)$. So $\pi$ factors through $\det$, and it is a character by Theorem 1.1.7. So an infinite-dimensional $\pi$ has $\pi_{N, \psi} \ne 0$. Its dimension is at most one, by Theorem 1.7.2. For $GL_2$, Jacquet and Langlands gave a direct proof of this bound with the Kirillov model, in [JL70], Section 2. $\square$

This theorem was used in the proof of Theorem 1.5.1. By Theorem 1.7.4, each irreducible infinite-dimensional representation of $GL_2(K)$ has a unique Whittaker model $\mathcal{W}(\pi, \psi)$.

**Theorem 1.7.5 (the Kirillov model).** Let $\pi$ be an irreducible infinite-dimensional representation of $GL_2(K)$, and let $W_v$ be the Whittaker function of $v$. The map $v \mapsto \xi_v$, $\xi_v(a) = W_v(\mathrm{diag}(a, 1))$, is an injective linear map from $V$ to the locally constant functions on $K^\times$. Its image $\mathcal{K}(\pi, \psi)$ contains $C_c^\infty(K^\times)$, and
$$\pi\begin{pmatrix} a & x \\ 0 & 1 \end{pmatrix} \xi(y) = \psi(xy) \xi(ay).$$
The quotient $\mathcal{K}(\pi, \psi) / C_c^\infty(K^\times)$ is isomorphic to the Jacquet module $\pi_N$, which has dimension $0$, $1$ or $2$.
1. $\pi$ is supercuspidal if and only if $\mathcal{K}(\pi, \psi) = C_c^\infty(K^\times)$.
2. For $\pi = \eta \mathrm{St}$ the space $\mathcal{K}(\pi, \psi)$ is spanned by $C_c^\infty(K^\times)$ and the function $\eta(y) |y| 1_{\mathcal{O}_K}(y)$.
3. For $\pi = \chi_1 \times \chi_2$ irreducible with $\chi_1 \ne \chi_2$, it is spanned by $C_c^\infty(K^\times)$ and the functions $\chi_i(y) |y|^{1/2} 1_{\mathcal{O}_K}(y)$ for $i = 1, 2$.

Lean: not stated yet

*Proof.* The formula for the action of $P_2$ follows from the definition of $W_v$ and from $\lambda(\pi(u) v) = \psi(x) \lambda(v)$ for $u = \left(\begin{smallmatrix} 1 & x \\ 0 & 1 \end{smallmatrix}\right)$. By Theorem 1.7.3 and $\dim \pi_{N, \psi} = 1$, the restriction of $v \mapsto \xi_v$ to $V(N)$ is an isomorphism onto $C_c^\infty(K^\times)$. Let $U$ be the kernel of $v \mapsto \xi_v$. It is stable under $P_2$ and under the center $Z$, and $U \cap V(N) = 0$. So $U$ embeds in $V_N$, and it has finite dimension. For $u \in U$ and $n \in N$, the vector $\pi(n) u - u$ lies in $U \cap V(N) = 0$, so $N$ fixes $U$. Suppose $U \ne 0$. Since $A Z$ is abelian and $U$ is finite-dimensional, there is $0 \ne u \in U$ that is an eigenvector of $A Z$: $\pi(t) u = c(t) u$ for $t$ in the diagonal torus. The vector $u$ is fixed by the lower unipotent matrices $\bar n_y$ with $|y|$ small, since it is smooth. For $t = \mathrm{diag}(a, 1)$ we have $t \bar n_y t^{-1} = \bar n_{y / a}$ and $\pi(t \bar n_y t^{-1}) u = c(t) c(t)^{-1} u = u$. So $u$ is fixed by all the lower unipotent matrices and by $N$, so by $SL_2(K)$. Then the $G$-span of $u$ is a nonzero subrepresentation on which $SL_2(K)$ acts trivially. It is $V$, since $\pi$ is irreducible, and then $\pi$ is a character. This is a contradiction, so $U = 0$. The quotient $\mathcal{K}(\pi, \psi) / C_c^\infty(K^\times)$ is the image of $V / V(N) = \pi_N$, and its dimension is given by Section 1.5. The asymptotic functions in parts 2 and 3 come from the exponents of the Jacquet module: the action of $\mathrm{diag}(a, 1)$ on $\pi_N$ is by $\chi_1(a) |a|^{1/2}$ and $\chi_2(a) |a|^{1/2}$ in the unnormalized form, and the Kirillov functions near $0$ follow these characters. Part 1 is the case $\pi_N = 0$. $\square$

The Kirillov model makes the local theory of $GL_2$ very explicit. Jacquet and Langlands defined the local $L$-factors and $\varepsilon$-factors of $GL_2$ with it, and Chapter 2 compares their factors with those of Godement and Jacquet. For example, the local zeta integral $\int_{K^\times} \xi(a) |a|^{s - 1/2} \, d^\times a$ is a sum of a polynomial in $q^{\pm s}$ and of the contributions of the asymptotic functions. So the $L$-factor is $1$ for a supercuspidal representation, $(1 - \eta(\varpi) q^{-s - 1/2})^{-1}$ for $\eta \mathrm{St}$ with $\eta$ unramified, and $\prod_i (1 - \chi_i(\varpi) q^{-s})^{-1}$ for $\chi_1 \times \chi_2$ with $\chi_1$, $\chi_2$ unramified.

### Generic representations of GL(n)

**Theorem 1.7.6 (generic representations, Gelfand-Kazhdan, Bernstein-Zelevinsky, Zelevinsky).** Let $\pi$ be an irreducible representation of $GL_n(K)$.
1. If $\pi$ is supercuspidal, then $\pi$ is generic.
2. Each essentially square integrable representation $L(\Delta)$ is generic.
3. $L(\Delta_1, \dots, \Delta_r)$ is generic if and only if no two of the segments $\Delta_i$ are linked, that is, if and only if $L(\Delta_1) \times \dots \times L(\Delta_r)$ is irreducible.
4. Each product $\pi_1 \times \dots \times \pi_r$ of generic representations has a unique generic irreducible subquotient.

Lean: not stated yet

*Sketch of proof.* Part 4 comes from Theorem 1.3.8 for the twisted coinvariants: only the open Bruhat cell contributes, and it contributes the tensor product of the twisted coinvariants of the $\pi_i$, which has dimension one. By exactness, exactly one irreducible subquotient has nonzero twisted coinvariants. For part 1, the theory of derivatives of Bernstein and Zelevinsky restricts $\pi$ to the mirabolic subgroup $P_n$ and filters it, as in Theorem 1.7.3 for $n = 2$. For a supercuspidal $\pi$, the restriction to $P_n$ is $\mathrm{c\text{-}Ind}_{N_n}^{P_n} \psi_N$, the highest derivative, since all the other derivatives are Jacquet modules of $\pi$ and vanish. So $\pi$ is generic. Parts 2 and 3 are due to Zelevinsky, who computed the highest derivatives of the representations $Z(\Delta)$ and of their products. $\square$

So the generic irreducible representations of $GL_2(K)$ are the infinite-dimensional ones. For $GL_3(K)$ in Example 1.6.7, only $\mathrm{St}_3 = L([\nu^{-1}, \nu])$ is generic among the four subquotients of $\nu^{-1} \times 1 \times \nu$. In the local Langlands correspondence, the generic representations correspond to the Weil-Deligne representations whose $L$-factor of the adjoint representation has no pole at $s = 1$. This was conjectured by Gross, Prasad and Rallis, and it is a theorem for $GL_n$.

**Remark 1.7.7 (Whittaker models and the local factors of pairs).** Let $\pi$ and $\pi'$ be generic irreducible representations of $GL_n(K)$ and $GL_m(K)$ with $m < n$. Jacquet, Piatetski-Shapiro and Shalika defined the zeta integrals
$$Z(s, W, W') = \int_{N_m \backslash GL_m(K)} W\begin{pmatrix} g & 0 \\ 0 & 1_{n - m} \end{pmatrix} W'(g) |\det g|^{s - (n - m)/2} \, dg,$$
for $W \in \mathcal{W}(\pi, \psi)$ and $W' \in \mathcal{W}(\pi', \psi^{-1})$. For $m = n$ a Schwartz-Bruhat function on $K^n$ is added. They proved that these integrals span a fractional ideal $L(s, \pi \times \pi') \mathbb{C}[q^{s}, q^{-s}]$, and that a functional equation relates $Z$ to the integral for $\tilde W(g) = W(w_n {}^t g^{-1})$ through a factor $\varepsilon(s, \pi \times \pi', \psi)$. This defines the $L$-factors and $\varepsilon$-factors of pairs. By the theorem of Bernstein and Zelevinsky and the inductivity of the factors, they extend to all irreducible representations. The local Langlands correspondence of Chapter 3 is characterized by these factors. The Lean project has no Whittaker models and no factors of pairs. Its file `GodementJacquet.lean` has the factors of Godement and Jacquet for $m = 0$, which do not need a Whittaker model, see Section 2.5.
