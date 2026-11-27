---
title: Strong multiplicity one
nodes: []
sources: [JL70]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Strong multiplicity one

Multiplicity one says that a cuspidal automorphic representation occurs only once in the space of cusp forms. Strong multiplicity one says much more: the representation is determined by its local components at almost all places. For newforms this is part 3 of Theorem 2.1.8 of Volume 4, a theorem of Atkin and Lehner. In the adelic setting it is a consequence of the Fourier-Whittaker expansion and of an approximation argument, and the proof is short when the finite set of exceptional places does not contain the real place.

### The statement

**Theorem 4.4.1 (strong multiplicity one).** Let $\pi$ and $\pi'$ be cuspidal automorphic representations of $GL_2(\mathbb{A})$, and let $S$ be a finite set of places. If $\pi_v \cong \pi'_v$ for all $v \notin S$, then $V_\pi = V_{\pi'}$. In particular $\pi_v \cong \pi'_v$ for all $v$.

Lean: not formalized

The theorem is due to Jacquet and Langlands for $GL_2$, in [JL70], Chapter II, and to Piatetski-Shapiro and to Jacquet and Shalika for $GL_n$ (Volume 7, Theorem 1.5.6). We prove it when $S$ contains only finite places. This is the case that we use for the newforms, where $\pi_\infty \cong \pi'_\infty \cong D_k$. The idea is simple: the global Whittaker function of a cusp form is a product of local Whittaker functions, and at the places of $S$ we can choose these local functions to agree on the mirabolic subgroup even if the representations differ.

We need three facts from the earlier chapters. First, the Fourier-Whittaker expansion of Chapter 2. Let $\psi$ be the standard character of $\mathbb{A}/\mathbb{Q}$. For $\phi \in \mathcal{A}_0(\omega)$ put
$$W_\phi(g) = \int_{\mathbb{Q} \backslash \mathbb{A}}\phi(n(x)g)\psi(-x)\,dx.$$
Then $W_\phi(n(x)g) = \psi(x)W_\phi(g)$, and
$$\phi(g) = \sum_{\xi \in \mathbb{Q}^\times}W_\phi(a(\xi)g).$$
Second, the uniqueness of local Whittaker models. Each infinite-dimensional irreducible admissible $\pi_v$ has a unique Whittaker model $\mathcal{W}(\pi_v, \psi_v)$, a space of functions $W$ on $G_v$ with $W(n(x)g) = \psi_v(x)W(g)$ on which $G_v$ acts by right translation. For a cuspidal $\pi$, the map $\phi \mapsto W_\phi$ is injective on $V_\pi$ by the expansion, and its image is $\bigotimes'_v\mathcal{W}(\pi_v, \psi_v)$: a pure tensor $\bigotimes_v\phi_v$ goes to $\prod_vW_v$, with $W_p$ the normalized spherical vector at almost all $p$. Third, the Kirillov model of Chapter 3.

**Theorem 4.4.2 (the Kirillov model).** Let $\pi_p$ be an irreducible admissible infinite-dimensional representation of $G_p$. The map $W \mapsto (y \mapsto W(a(y)))$ is injective on $\mathcal{W}(\pi_p, \psi_p)$, and its image contains the space $\mathcal{S}(\mathbb{Q}_p^\times)$ of locally constant functions with compact support on $\mathbb{Q}_p^\times$.

Lean: not formalized

This is in Chapter 3, in Volume 6, Theorem 1.7.5, and in [JL70], Chapter I. The image is equal to $\mathcal{S}(\mathbb{Q}_p^\times)$ when $\pi_p$ is supercuspidal, and in the other cases it is larger by a space of dimension 1 or 2 of functions with a prescribed behaviour near $0$.

### Two approximation lemmas

**Lemma 4.4.3 (central characters).** Let $\omega, \omega'$ be characters of $\mathbb{Q}^\times \backslash \mathbb{A}^\times$, let $S$ be a finite set of places, and suppose that $\omega_v = \omega'_v$ for all $v \notin S$. Then $\omega = \omega'$.

Lean: not formalized

*Proof.* Put $\eta = \omega\omega'^{-1}$ and $\mathbb{Q}_S = \prod_{v \in S}\mathbb{Q}_v$. Then $\eta$ is continuous, trivial on $\mathbb{Q}^\times$, and trivial on the factor $\mathbb{A}^{S,\times}$ of the ideles outside $S$. Let $x = (x_S, x^S) \in \mathbb{A}^\times$. By weak approximation, $\mathbb{Q}^\times$ is dense in $\mathbb{Q}_S^\times$, so there are $\xi_j \in \mathbb{Q}^\times$ with $\xi_j \to x_S$ in $\mathbb{Q}_S^\times$. Then
$$\eta(x) = \eta(\xi_j^{-1}x) = \eta(\xi_j^{-1}x_S, 1)\,\eta(1, \xi_j^{-1}x^S) = \eta(\xi_j^{-1}x_S, 1),$$
and the right side tends to $\eta(1) = 1$ by continuity. $\square$

**Lemma 4.4.4 (density).** Let $S$ be a finite set of primes and $G_S = \prod_{p \in S}G_p$, $B_S = \prod_{p \in S}B(\mathbb{Q}_p)$. Let $G(\mathbb{A}^S)$ be the product of the groups $G_v$, $v \notin S$, restricted with respect to the $K_p$. Then the set $GL_2(\mathbb{Q})\cdot(B_S \times G(\mathbb{A}^S))$ is dense in $GL_2(\mathbb{A})$.

Lean: not formalized

*Proof.* Let $g = (g_S, g^S) \in GL_2(\mathbb{A})$ and let $U$ be an open neighbourhood of $1$ in $G_S$. We look for $\gamma \in GL_2(\mathbb{Q})$ and $h = (b, h^S) \in B_S \times G(\mathbb{A}^S)$ with $\gamma h \in g_SU \times \{g^S\}$. Put $h^S = \gamma^{-1}g^S$. Then the condition is $\gamma b \in g_SU$, that is, $\gamma \in g_SUB_S$. The set $g_SUB_S$ is open in $G_S$ and right invariant under $B_S$, so it is the preimage of an open set of $G_S/B_S = \prod_{p \in S}\mathbb{P}^1(\mathbb{Q}_p)$. The image of $GL_2(\mathbb{Q})$ in this product is $\mathbb{P}^1(\mathbb{Q})$, embedded diagonally. It is dense: the affine line $\mathbb{Q}$ is dense in $\prod_{p \in S}\mathbb{Q}_p$ by weak approximation, and the affine line is dense in $\mathbb{P}^1(\mathbb{Q}_p)$. So $\gamma$ exists. $\square$

### The proof

*Proof of Theorem 4.4.1 when $S$ contains only finite places.* We may enlarge $S$ and assume that it contains the primes where $\pi$ or $\pi'$ is ramified. Let $\omega, \omega'$ be the central characters. By Proposition 4.2.3, part 1, $\omega_v = \omega'_v$ for $v \notin S$, so $\omega = \omega'$ by Lemma 4.4.3.

For $v \notin S$ the Whittaker models $\mathcal{W}(\pi_v, \psi_v)$ and $\mathcal{W}(\pi'_v, \psi_v)$ are the same space of functions, since the Whittaker model depends only on the isomorphism class. For $v \notin S$ choose the same function $W_v$ in both, equal to the normalized spherical function for $v \notin S \cup \{\infty\}$ and to any nonzero function at $\infty$. For $p \in S$, Theorem 4.4.2 gives $W_p \in \mathcal{W}(\pi_p, \psi_p)$ and $W'_p \in \mathcal{W}(\pi'_p, \psi_p)$ with
$$W_p(a(y)) = W'_p(a(y)) = 1_{\mathbb{Z}_p^\times}(y) \quad \text{for } y \in \mathbb{Q}_p^\times.$$
Then $W_p(n(x)a(y)) = \psi_p(x)W_p(a(y)) = W'_p(n(x)a(y))$, so $W_p = W'_p$ on the mirabolic group $P(\mathbb{Q}_p)$. Both functions transform under the centre by the same character $\omega_p = \omega'_p$, so $W_p = W'_p$ on $Z(\mathbb{Q}_p)P(\mathbb{Q}_p) = B(\mathbb{Q}_p)$.

Let $\phi \in V_\pi$ and $\phi' \in V_{\pi'}$ be the cusp forms with $W_\phi = \prod_vW_v$ and $W_{\phi'} = \prod_vW'_v$, where $W'_v = W_v$ for $v \notin S$. They are nonzero. For $b \in B_S$ and $h \in G(\mathbb{A}^S)$ we have $W_\phi(bh) = W_{\phi'}(bh)$. Since $a(\xi)$ lies in $B_S \times G(\mathbb{A}^S)$ for $\xi \in \mathbb{Q}^\times$, the Fourier-Whittaker expansion gives
$$\phi(bh) = \sum_{\xi \in \mathbb{Q}^\times}W_\phi(a(\xi)bh) = \sum_{\xi \in \mathbb{Q}^\times}W_{\phi'}(a(\xi)bh) = \phi'(bh).$$
So the continuous function $\phi - \phi'$ vanishes on $B_S \times G(\mathbb{A}^S)$. It is left invariant under $GL_2(\mathbb{Q})$, so it vanishes on $GL_2(\mathbb{Q})(B_S \times G(\mathbb{A}^S))$, and by Lemma 4.4.4 it vanishes everywhere. So $\phi = \phi' \in V_\pi \cap V_{\pi'}$. Since $V_\pi$ and $V_{\pi'}$ are irreducible and $\phi \ne 0$, $V_\pi = V_{\pi'}$. $\square$

The proof uses the same function $W_\infty$ in both Whittaker models, so it needs $\infty \notin S$. When $\infty \in S$ the argument fails, because the Kirillov model of a $(\mathfrak{g}, K_\infty)$-module does not contain a function with small support that we can match. The general case follows from the theory of $L$-functions: by the Rankin-Selberg method, the partial $L$-function $L^S(s, \pi \times \tilde{\pi}')$ has a pole at $s = 1$ if and only if $\pi \cong \pi'$. This is the theorem of Jacquet and Shalika, Volume 7, Theorem 1.5.10, and it gives Theorem 4.4.1 for all finite $S$.

### Consequences

**Corollary 4.4.5 (eigenforms lie in one representation).** Let $\pi$ be a cuspidal automorphic representation with central character $\omega$, let $S$ be a finite set of places that contains $\infty$ and the primes where $\pi$ ramifies, and let $\phi \in \mathcal{A}_0(\omega)$ be nonzero. Suppose that for each $p \notin S$, $\phi$ is fixed by $K_p$ and $\mathcal{H}(G_p, K_p)$ acts on $\phi$ by the character $\lambda_{\pi_p}$. Then $\phi \in V_\pi$.

Lean: not formalized

*Proof.* Write $\phi = \sum_\sigma\phi_\sigma$ with $\phi_\sigma \in V_\sigma$ as in Theorem 4.2.2. The projections onto the $V_\sigma$ commute with the action, so each nonzero $\phi_\sigma$ is fixed by $K_p$ and has the character $\lambda_{\pi_p}$ for $p \notin S$. So $\sigma_p$ is unramified with $\lambda_{\sigma_p} = \lambda_{\pi_p}$, and $\sigma_p \cong \pi_p$ for $p \notin S$ by Proposition 4.1.7. The set $S$ contains the real place, so we need Theorem 4.4.1 in general here. It gives $V_\sigma = V_\pi$. $\square$

If one knows a priori that $\sigma_\infty \cong \pi_\infty$, for example when $\phi$ has weight $k$ and is killed by $L$ and $\pi_\infty = D_k$, the proof needs only the case of Theorem 4.4.1 that we proved. This gives a second proof of Step 1 of Theorem 4.3.3, and the adelic form of part 3 of Theorem 2.1.8 of Volume 4.

**Remark 4.4.6 (the Lean form).** The Lean project does not state Theorem 4.4.1; it uses it as a definition. `Langlands.NumberFieldGL.CuspEigenform` is the type of nonzero cuspidal Hecke eigenforms on $GL_n$ over a number field $K$, and `Langlands.NumberFieldGL.CuspEigenform.Equiv` relates two of them with the same eigenvalues at almost all finite places. With `Langlands.NumberFieldGL.heckeEigenvalue_unique`, `Langlands.NumberFieldGL.cuspSetoid` proves that this is an equivalence relation. The quotient `Langlands.NumberFieldGL.AutomorphicClass` stands for the set of cuspidal automorphic representations of $GL_n(\mathbb{A}_K)$. This identification is Corollary 4.4.5 and Theorem 4.4.1: a class of eigenforms is the set of eigenforms in one $V_\pi$.

**Remark 4.4.7 (refinements and failures).** Ramakrishnan proved that for $GL_2$ it suffices that $\pi_p \cong \pi'_p$ for a set of primes of density greater than $7/8$ (Invent. Math. 116, 1994), and the constant $7/8$ is sharp. If $\chi$ is the quadratic character attached to $\mathbb{Q}(i)$, then $\pi$ and $\pi \otimes (\chi \circ \det)$ agree at the primes $p \equiv 1 \bmod 4$ (Exercise 4). Strong multiplicity one fails for $SL_2$: Labesse and Langlands found cuspidal representations of $SL_2(\mathbb{A})$ that are isomorphic at almost all places and not equal. For $SL_n$ with $n \ge 3$ Blasius showed that even multiplicity one fails.
