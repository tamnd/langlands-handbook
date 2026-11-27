---
title: Induced representations and the Jacquet module
nodes: []
sources: [BH06, JL70]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Induced representations and the Jacquet module

This section fixes the notation, recalls the basic notions of Volume 6, Chapter 1, and studies the principal series through its Jacquet module. Frobenius reciprocity and the Jacquet module of a principal series reduce the comparison of principal series to linear algebra over the torus.

### Notation

Let $K$ be a nonarchimedean local field, with ring of integers $\mathcal{O}$, maximal ideal $\mathfrak{p}$, uniformizer $\varpi$ and residue field $k = \mathcal{O} / \mathfrak{p}$ with $q$ elements. The absolute value is normalized by $|\varpi| = q^{-1}$, and $v$ is the valuation. For $K = \mathbb{Q}_p$ we take $\varpi = p$. Let $G = GL_2(K)$, and let $B$, $T$, $N$ and $Z$ be the upper triangular matrices, the diagonal matrices, the upper unipotent matrices and the center. We write
$$n(x) = \begin{pmatrix} 1 & x \\ 0 & 1 \end{pmatrix}, \qquad \bar n(y) = \begin{pmatrix} 1 & 0 \\ y & 1 \end{pmatrix}, \qquad w = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}, \qquad K_0 = GL_2(\mathcal{O}).$$
The group $K_0$ is a maximal compact open subgroup of $G$. The modulus character of $B$ is $\delta_B\left(\begin{smallmatrix} a & x \\ 0 & d \end{smallmatrix}\right) = |a/d|$. We take the Haar measure $dx$ on $K$ with $\mathrm{vol}(\mathcal{O}) = 1$, the measure $d^\times x$ on $K^\times$ with $\mathrm{vol}(\mathcal{O}^\times) = 1$, and the Haar measure on $G$ with $\mathrm{vol}(K_0) = 1$, as in Volume 0, Section 3.2.

A *character* of $K^\times$ is a continuous homomorphism $\chi : K^\times \to \mathbb{C}^\times$. It is *unramified* if it is trivial on $\mathcal{O}^\times$. Then $\chi = |\cdot|^s$ for some $s \in \mathbb{C}$, and $\chi$ is determined by $\chi(\varpi)$. The *conductor exponent* $a(\chi)$ is $0$ if $\chi$ is unramified, and otherwise it is the least $a \ge 1$ such that $\chi$ is trivial on $1 + \mathfrak{p}^a$. A character $\chi_1 \otimes \chi_2$ of $T$ is the character $\mathrm{diag}(a, d) \mapsto \chi_1(a) \chi_2(d)$. We write $\chi = \chi_1 \otimes \chi_2$ and $\chi^w = \chi_2 \otimes \chi_1$. We extend a character of $T$ to $B$ through the projection $B \to T$.

### Smooth and admissible representations

We recall the definitions of Volume 6, Section 1.1.

**Definition 3.1.1 (smooth and admissible representations).** A representation $(\pi, V)$ of $G$ on a complex vector space $V$ is *smooth* if the stabilizer of each vector is open. It is *admissible* if it is smooth and the space $V^J$ of the vectors fixed by $J$ has finite dimension for each compact open subgroup $J$ of $G$. It is *irreducible* if $V \ne 0$ and $V$ has no $G$-stable subspace other than $0$ and $V$.

Lean: `Langlands.SmoothRep`, `Langlands.SmoothRep.IsAdmissible`, `Langlands.SmoothRep.IsIrreducible`, and `Langlands.IrrRep` for the irreducible admissible representations.

Jacquet proved that each irreducible smooth representation of $GL_n(K)$ is admissible (Volume 6, Theorem 1.1.11), and the local components of an automorphic representation are admissible by construction. By Schur's lemma (Volume 6, Theorem 1.1.7), the center $Z = K^\times$ acts on an irreducible admissible $\pi$ by a character $\omega_\pi$, the *central character*. For a character $\eta$ of $K^\times$, the *twist* $\pi \otimes \eta$ is $g \mapsto \eta(\det g) \pi(g)$. Its central character is $\omega_\pi \eta^2$.

Three decompositions of $G$ are used all the time. We collect them in a lemma.

**Lemma 3.1.2 (Iwasawa, Bruhat and Cartan decompositions).**
1. $G = B K_0$.
2. $G = B \sqcup B w N$.
3. $G$ is the disjoint union of the double cosets $K_0 \, \mathrm{diag}(\varpi^{m_1}, \varpi^{m_2}) \, K_0$ with $m_1 \ge m_2$ in $\mathbb{Z}$. A matrix $g$ lies in the double coset of $(m_1, m_2)$ if and only if $v(\det g) = m_1 + m_2$ and the least valuation of an entry of $g$ is $m_2$.

Lean: `Langlands.GL2.iwasawa`, `Langlands.GL2.bruhat`, `Langlands.GL2.mem_bigCell_iff` and `Langlands.GL2.cartan`. The Lean form of part 3 is the existence of the decomposition. The disjointness and the criterion are not in Lean.

*Proof.* Let $g = \left(\begin{smallmatrix} a & b \\ c & d \end{smallmatrix}\right)$. For part 1, if $|c| \le |d|$, then $k = \bar n(c/d) \in K_0$ and $g k^{-1}$ has bottom row $(0, d)$, so $g k^{-1} \in B$. If $|c| > |d|$, apply this to $g w$. For part 2, if $c \ne 0$ then $g = \left(\begin{smallmatrix} -\det g / c & a \\ 0 & c \end{smallmatrix}\right) w \, n(d/c)$. For part 3, the least valuation of an entry and the valuation of the determinant do not change under multiplication by $K_0$ on either side, and for $\mathrm{diag}(\varpi^{m_1}, \varpi^{m_2})$ they are $m_2$ and $m_1 + m_2$. This gives the disjointness and the criterion. For the existence, move an entry of least valuation to the upper left corner and clear its row and column by elementary matrices in $K_0$. $\square$

### The normalized principal series

**Definition 3.1.3 (principal series).** Let $\chi_1, \chi_2$ be characters of $K^\times$. The *normalized principal series* $\chi_1 \times \chi_2$ is the space of the locally constant functions $f : G \to \mathbb{C}$ with
$$f(b g) = \chi_1(a) \chi_2(d) \left| \frac{a}{d} \right|^{1/2} f(g), \qquad b = \begin{pmatrix} a & x \\ 0 & d \end{pmatrix} \in B,$$
on which $G$ acts by right translation, $(g \cdot f)(h) = f(h g)$. In the notation of Volume 6, Definition 1.3.1, this is $\mathrm{Ind}_B^G \chi$ with the normalization $\chi \delta_B^{1/2}$. Jacquet and Langlands write $\mathcal{B}(\chi_1, \chi_2)$ for this space.

Lean: `Langlands.normPrincipalSeries` and `Langlands.principalSeries`. The first is built from `Langlands.SmoothRep.ind` and `Langlands.GL2.sqrtModulus`. By `Langlands.normPrincipalSeries_iso` the two are isomorphic. The unnormalized form is `Langlands.principalSeriesInd`, and `Langlands.normPrincipalSeries_eq` identifies $\chi_1 \times \chi_2$ with the unnormalized induction of $\chi_1 |\cdot|^{1/2} \otimes \chi_2 |\cdot|^{-1/2}$.

The factor $\delta_B^{1/2}$ makes the theory symmetric in $\chi_1$ and $\chi_2$, and it makes the Satake parameters of tempered representations unitary, as Volume 0, Section 3.2 requires.

**Proposition 3.1.4 (first properties).** Let $V = \chi_1 \times \chi_2$.
1. Restriction to $K_0$ is an isomorphism of $V$ onto the space of the locally constant functions $\phi$ on $K_0$ with $\phi(b k) = \chi_1(a) \chi_2(d) \phi(k)$ for $b \in B \cap K_0$. In particular $V$ is admissible, and $\dim V^J \le [K_0 : J]$ for each open normal subgroup $J$ of $K_0$.
2. The central character of $V$ is $\chi_1 \chi_2$, and $V \otimes \eta \cong \chi_1 \eta \times \chi_2 \eta$ for each character $\eta$.
3. The contragredient of $V$ is isomorphic to $\chi_1^{-1} \times \chi_2^{-1}$.
4. $V^{K_0} \ne 0$ if and only if $\chi_1$ and $\chi_2$ are unramified. Then $V^{K_0}$ is the line spanned by the function $f_0(b k) = \chi_1(a) \chi_2(d) |a/d|^{1/2}$.

Lean: `Langlands.normPrincipalSeries_isAdmissible` and `Langlands.principalSeries_isAdmissible`, for the admissibility in part 1. The other parts are not stated yet.

*Proof.* Part 1 follows from $G = B K_0$, since $|a/d| = 1$ on $B \cap K_0$, so $f(b k) = \chi \delta_B^{1/2}(b) \phi(k)$ is well defined. For part 2, a central $z$ lies in $B$, so $(z \cdot f)(h) = f(z h) = \chi_1 \chi_2(z) f(h)$, and $f \mapsto (\eta \circ \det) f$ maps $V \otimes \eta$ onto $\chi_1 \eta \times \chi_2 \eta$. For part 3, the pairing $\langle f, f' \rangle = \int_{K_0} f(k) f'(k) \, dk$ of $\chi_1 \times \chi_2$ and $\chi_1^{-1} \times \chi_2^{-1}$ is $G$-invariant by part 3 of Volume 6, Proposition 1.3.4, since $f f'$ lies in the unnormalized induction of $\delta_B$. By part 1 it is perfect on the $J$-fixed vectors for each open normal $J \subset K_0$. For part 4, a $K_0$-fixed $f$ is determined by $f(1)$, and $f(b) = f(1)$ for $b \in B \cap K_0$ forces $\chi_1(a) \chi_2(d) f(1) = f(1)$ for all $a, d \in \mathcal{O}^\times$. $\square$

**Example 3.1.5 (functions on the projective line).** Take $\chi_1 = |\cdot|^{-1/2}$ and $\chi_2 = |\cdot|^{1/2}$. Then $\chi_1(a) \chi_2(d) |a/d|^{1/2} = 1$ for every $b \in B$, so $|\cdot|^{-1/2} \times |\cdot|^{1/2}$ is the space of the locally constant functions on $B \backslash G$. The map $B g \mapsto [c : d]$, where $(c, d)$ is the bottom row of $g$, is a bijection $B \backslash G \to \mathbb{P}^1(K)$, because the stabilizer of the line $[0 : 1]$ under right multiplication is $B$. So $|\cdot|^{-1/2} \times |\cdot|^{1/2} = C^\infty(\mathbb{P}^1(K))$, with $G$ acting by $(g \cdot f)(x) = f(x g)$ on row vectors. It contains the constant functions, a $G$-stable line on which $G$ acts trivially. So this principal series is reducible. The quotient is the Steinberg representation of Section 3.2.

### The Jacquet module and Frobenius reciprocity

**Definition 3.1.6 (Jacquet module).** Let $(\pi, V)$ be a smooth representation of $G$. Let $V(N)$ be the span of the vectors $\pi(n) v - v$ with $n \in N$ and $v \in V$, and let $V_N = V / V(N)$. The torus $T$ acts on $V_N$, since $T$ normalizes $N$. The *normalized Jacquet module* is $r_B(\pi) = V_N \otimes \delta_B^{-1/2}$, that is, $V_N$ with the action $t \cdot \bar v = \delta_B(t)^{-1/2} \overline{\pi(t) v}$.

Lean: `Langlands.SmoothRep.jacquet`, with the kernel `Langlands.SmoothRep.jacquetKer`. The unnormalized module for $GL_2$ is `Langlands.SmoothRep.jacquetN`.

The functor $\pi \mapsto r_B(\pi)$ is exact (Volume 6, Proposition 1.3.5). If $\pi$ is admissible and irreducible, then $r_B(\pi)$ has finite dimension (Volume 6, Theorem 1.5.8). The next theorem is the reason for the normalization.

**Theorem 3.1.7 (Frobenius reciprocity).** Let $(\pi, V)$ be a smooth representation of $G$ and let $\chi_1, \chi_2$ be characters of $K^\times$. The map $\Phi \mapsto (\bar v \mapsto \Phi(v)(1))$ is a bijection
$$\mathrm{Hom}_G(\pi, \chi_1 \times \chi_2) \xrightarrow{\ \sim\ } \mathrm{Hom}_T(r_B(\pi), \chi_1 \otimes \chi_2).$$

Lean: `Langlands.SmoothRep.frobenius`, for the unnormalized induction from any subgroup, and `Langlands.SmoothRep.jacquetFrobenius`, for the unnormalized principal series with the unnormalized Jacquet module.

*Proof.* Let $\Phi$ be a map of representations and $\lambda(v) = \Phi(v)(1)$. For $n \in N$ we have $\lambda(\pi(n) v) = \Phi(v)(n) = \Phi(v)(1)$, so $\lambda$ vanishes on $V(N)$. For $t \in T$ we have $\lambda(\pi(t) v) = \Phi(v)(t) = \chi \delta_B^{1/2}(t) \lambda(v)$, so $\lambda$ is a map $r_B(\pi) \to \chi$. Conversely, a linear form $\lambda$ with these two properties gives $\Phi(v)(g) = \lambda(\pi(g) v)$, which lies in $\chi_1 \times \chi_2$ and is locally constant since $v$ is smooth. The two constructions are inverse to each other. This is Volume 6, Theorem 1.3.3. $\square$

The Jacquet module of a principal series comes from the Bruhat decomposition. Let $V_w \subset \chi_1 \times \chi_2$ be the space of the functions with compact support modulo $B$ in the open cell $B w N$. The map $f \mapsto (x \mapsto f(w n(x)))$ identifies $V_w$ with $C_c^\infty(K)$, with $N$ acting by translations. The quotient $V / V_w$ is the line of the values $f(1)$.

**Theorem 3.1.8 (Jacquet module of the principal series).** Let $V = \chi_1 \times \chi_2$. There is an exact sequence of representations of $T$
$$0 \to \chi^w \to r_B(V) \to \chi \to 0,$$
where the map to $\chi$ is induced by $f \mapsto f(1)$ and the line $\chi^w$ is the image of $V_w$. In particular $\dim r_B(V) = 2$. If $\chi_1 \ne \chi_2$, then $r_B(V) \cong \chi \oplus \chi^w$.

Lean: `Langlands.principalSeriesJacquet_shortExact` and `Langlands.finrank_principalSeriesJacquet`, for the unnormalized Jacquet module of the unnormalized induction, and `Langlands.bigCellJacquet_iso` for the line of the open cell.

*Proof sketch.* Restriction to $w N$ identifies $V_w$ with $C_c^\infty(K)$, and the sequence $0 \to V_w \to V \to \mathbb{C} \to 0$, with $f \mapsto f(1)$, is $B$-equivariant. The coinvariants of $C_c^\infty(K)$ under translations are the line of $\phi \mapsto \int_K \phi$, and the relation $w n(x) t = \mathrm{diag}(d, a) \, w \, n(x d / a)$ for $t = \mathrm{diag}(a, d)$ shows that $T$ acts there by $\chi^w \delta_B^{1/2}$. Exactness of the Jacquet functor and the twist by $\delta_B^{-1/2}$ give the sequence. If $\chi_1 \ne \chi_2$, the eigenspaces of a $t$ with $\chi(t) \ne \chi^w(t)$ split it. See Volume 6, Theorem 1.3.11. $\square$

**Corollary 3.1.9 (maps between principal series).**
1. If $\mathrm{Hom}_G(\chi_1 \times \chi_2, \chi_1' \times \chi_2') \ne 0$, then $(\chi_1', \chi_2')$ is $(\chi_1, \chi_2)$ or $(\chi_2, \chi_1)$.
2. Each nonzero $G$-stable subspace $W$ of a principal series has $r_B(W) \ne 0$.

Lean: `Langlands.normPrincipalSeries_hom_eq` and `Langlands.normPrincipalSeries_sub_jacquet_nontrivial`, for parts 1 and 2. The form of part 2 for the unnormalized induction is `Langlands.principalSeriesInd_sub_jacquet_nontrivial`.

*Proof.* By Theorem 3.1.7 a nonzero map gives a nonzero map $r_B(\chi_1 \times \chi_2) \to \chi'$ of representations of $T$. By Theorem 3.1.8 the representation $r_B(\chi_1 \times \chi_2)$ has a composition series with factors $\chi^w$ and $\chi$. A nonzero map onto the character $\chi'$ kills a subspace of codimension one, so $\chi'$ is one of the two factors. For part 2, the inclusion of $W$ in $\chi_1 \times \chi_2$ is a nonzero map, so by Theorem 3.1.7 there is a nonzero map $r_B(W) \to \chi$. $\square$
