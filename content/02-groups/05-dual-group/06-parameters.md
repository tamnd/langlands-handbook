---
title: L-parameters and the local Langlands conjecture
nodes: []
sources: [Tat79]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## L-parameters and the local Langlands conjecture

Section 5.5 shows that the unramified representations of an unramified group $G(F)$ correspond to the semisimple classes in $G^\vee \rtimes \Phi$. Such a class is the same as a homomorphism $W_F / I_F \to {}^L G$ over $W_F$, up to conjugation. The local Langlands conjecture extends this to all irreducible representations: they should be classified, in finite packets, by homomorphisms from the Weil-Deligne group to ${}^L G$. This section defines these homomorphisms and states the conjecture. It is motivation for the rest of the handbook and is not used in later proofs of this volume. We follow [Bor79] for the parameters and the conjecture, and [Tat79], Section 4, for the Weil-Deligne group.

### L-parameters

Let $F$ be a non-archimedean local field, with Weil group $W_F$, inertia group $I_F$, geometric Frobenius $\Phi$, and the norm $\|\ \| : W_F \to q^{\mathbb{Z}}$ with $\|\Phi\| = q^{-1}$, as in Volume 0, Chapter 3. Let $G$ be a connected reductive group over $F$, with L-group ${}^L G = G^\vee \rtimes W_F$.

**Definition 5.6.1 (Weil-Deligne group).** The *Weil-Deligne group* of $F$ is the topological group $W_F' = W_F \times SL_2(\mathbb{C})$.

Deligne defined the Weil-Deligne group as a group scheme $\mathbb{G}_a \rtimes W_F$, and its representations are the Weil-Deligne representations $(r, N)$ of Volume 0, Definition 3.1.4. The form $W_F \times SL_2(\mathbb{C})$ is more convenient for groups other than $GL_n$, and Proposition 5.6.3 compares the two.

**Definition 5.6.2 (L-parameter).** An *L-parameter* for $G$ is a homomorphism $\varphi : W_F \times SL_2(\mathbb{C}) \to {}^L G$ such that:
1. $\varphi$ commutes with the projections to $W_F$;
2. $\varphi$ is continuous, and $\varphi(w)$ is semisimple for each $w \in W_F$, that is, its image in a Galois form $G^\vee \rtimes \mathrm{Gal}(E/F)$ is semisimple;
3. the restriction of $\varphi$ to $SL_2(\mathbb{C})$ is a homomorphism of algebraic groups into $G^\vee$;
4. $\varphi$ is *relevant*: if the image of $\varphi$ is contained in a Levi subgroup of a parabolic subgroup $\mathcal{P}$ of ${}^L G$, then $\mathcal{P}$ corresponds to a parabolic subgroup of $G$ defined over $F$.

Two L-parameters are *equivalent* if they are conjugate under $G^\vee$. Let $\Phi(G)$ be the set of equivalence classes.

The parabolic subgroups of ${}^L G$ and the notion of relevance are in [Bor79], Section 3. A parabolic subgroup of ${}^L G$ is the normalizer in ${}^L G$ of a parabolic subgroup of $G^\vee$ that it meets in a subgroup that maps onto $W_F$. For a quasi-split group, every parameter is relevant. For an inner form of a quasi-split group, relevance removes the parameters that only fit the quasi-split form. For example, if $D$ is the quaternion division algebra over $F$ and $G = D^\times$, then ${}^L G = GL_2(\mathbb{C}) \times W_F$, and the relevant parameters are those whose image is not contained in a proper Levi subgroup, since $D^\times$ has no proper parabolic subgroup over $F$.

**Proposition 5.6.3 (parameters of GL_n).** Let $G = GL_n$, so that $L$-parameters are homomorphisms $\varphi : W_F \times SL_2(\mathbb{C}) \to GL_n(\mathbb{C})$. The map $\varphi \mapsto (r, N)$ with
$$r(w) = \varphi\big(w, \mathrm{diag}(\|w\|^{1/2}, \|w\|^{-1/2})\big), \qquad N = d\varphi \begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix},$$
induces a bijection from the set of equivalence classes of $L$-parameters onto the set of isomorphism classes of Frobenius-semisimple Weil-Deligne representations of dimension $n$.

Lean: not stated yet

*Outline of the proof.* The element $\varphi(w, 1)$ commutes with $\varphi(SL_2(\mathbb{C}))$, and $\mathrm{Ad}(\mathrm{diag}(a^{1/2}, a^{-1/2}))$ multiplies the nilpotent matrix $\begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix}$ by $a$. So $r(w) N r(w)^{-1} = \|w\| N$, and $(r, N)$ is a Weil-Deligne representation. It is Frobenius-semisimple because $r(\Phi)$ is the product of the commuting semisimple elements $\varphi(\Phi, 1)$ and $\varphi(1, \mathrm{diag}(q^{-1/2}, q^{1/2}))$. For the inverse, let $(r, N)$ be given. By the Jacobson-Morozov theorem, $N$ lies in an $\mathfrak{sl}_2$-triple, and by Kostant's theorem all such triples are conjugate under the centralizer of $N$, see Bourbaki, *Groupes et algèbres de Lie*, Chapter VIII. One chooses the triple to be normalized by $r(W_F)$ in a compatible way and defines $\varphi$ on $W_F$ by dividing $r(w)$ by the image of $\mathrm{diag}(\|w\|^{1/2}, \|w\|^{-1/2})$. The details are in the paper of Gross and Reeder, "Arithmetic invariants of discrete Langlands parameters" (Duke Math. J. 2010). $\square$

So for $GL_n$ the L-parameters are the objects on the Galois side of the local Langlands correspondence of Volume 0, Theorem 2.3.1. In general, an L-parameter $\varphi$ and a representation $r : {}^L G \to GL_m(\mathbb{C})$ give an $m$-dimensional Weil-Deligne representation $r \circ \varphi$, and its local factors $L(s, r \circ \varphi)$ and $\varepsilon(s, r \circ \varphi, \psi)$ are defined in [Tat79], Section 4. These are the factors that the conjecture attaches to the representations in the packet of $\varphi$.

### Unramified parameters and tori

An L-parameter $\varphi$ is *unramified* if it is trivial on $I_F$ and on $SL_2(\mathbb{C})$. Such a $\varphi$ factors through $W_F / I_F = \Phi^{\mathbb{Z}}$, so it is determined by $\varphi(\Phi) = s \rtimes \Phi$, a semisimple element of the coset $G^\vee \rtimes \Phi$. Conjugation by $g \in G^\vee$ changes $s \rtimes \Phi$ into $g s \vartheta(g)^{-1} \rtimes \Phi$. So:

**Proposition 5.6.4 (unramified parameters).** Let $G$ be unramified. The map $\varphi \mapsto \varphi(\Phi)$ is a bijection from the set of equivalence classes of unramified L-parameters onto the set of semisimple $G^\vee$-conjugacy classes in $G^\vee \rtimes \Phi$. Composed with Theorem 5.5.11, it gives a bijection between unramified L-parameters and unramified irreducible representations of $G(F)$ for a hyperspecial $K$.

Lean: not stated yet

*Proof.* A homomorphism from $\Phi^{\mathbb{Z}}$ is determined by the image of $\Phi$, and any element $s \rtimes \Phi$ is the image of $\Phi$ for a unique homomorphism over $W_F$. The parameter is semisimple if and only if $s \rtimes \Phi$ is semisimple. An unramified parameter is relevant, since $G$ is quasi-split. The rest is the formula for the conjugation. $\square$

For tori, every parameter is relevant and $SL_2(\mathbb{C})$ maps trivially to a torus. The equivalence classes of L-parameters $W_F \to {}^L T$ over $W_F$ are the continuous cohomology classes in $H^1(W_F, T^\vee)$, because a homomorphism $w \mapsto (a(w), w)$ is a cocycle $a$, and conjugation by $T^\vee$ changes $a$ by a coboundary.

**Theorem 5.6.5 (Langlands, tori).** Let $T$ be a torus over a local field $F$. There is a canonical isomorphism
$$\mathrm{Hom}_{\mathrm{cont}}(T(F), \mathbb{C}^\times) \cong H^1_{\mathrm{cont}}(W_F, T^\vee),$$
functorial in $T$, which for $T = \mathbb{G}_m$ is local class field theory.

Lean: `Langlands.LocalLanglandsTorusSplit`, in the project library, for split tori, with the proof `Langlands.localLanglandsTorusSplit`

*Outline of the proof.* For split tori, this is Volume 3, Theorem 4.5.2, and for induced tori it is Volume 3, Theorem 4.5.4 with Shapiro's lemma. For a general torus, choose a resolution by induced tori and use the functoriality. The proof is in Langlands, "Representations of abelian algebraic groups" (Pacific J. Math. 1997). $\square$

For an unramified character $\chi$ of a split torus, the parameter is the unramified one with $\varphi(\Phi) = t_\chi$, as in Proposition 5.5.2. Exercise 8 treats the norm-one torus.

### An example: packets for SL_2

Let $G = SL_2$, so that ${}^L G = PGL_2(\mathbb{C}) \times W_F$. Let $\varphi : W_F \to PGL_2(\mathbb{C})$ be a parameter that is trivial on $SL_2(\mathbb{C})$. By a theorem of Tate, every continuous projective representation of $W_F$ lifts to $GL_2(\mathbb{C})$. Let $\tilde\varphi : W_F \to GL_2(\mathbb{C})$ be a lift. By the local Langlands correspondence for $GL_2$, $\tilde\varphi$ corresponds to an irreducible representation $\tilde\pi$ of $GL_2(F)$. Two lifts differ by a character $\eta$ of $W_F$, which changes $\tilde\pi$ into $\tilde\pi \otimes (\eta \circ \det)$. The restriction of $\tilde\pi$ to $SL_2(F)$ is a finite direct sum of irreducible representations, and it does not depend on the lift. Labesse and Langlands, "L-indistinguishability for SL(2)" (Canad. J. Math. 1979), define the L-packet $\Pi_\varphi$ as the set of irreducible constituents of this restriction. In general $\Pi_\varphi$ has more than one element.

**Example 5.6.6 (a packet of size four).** Let $p$ be odd. Then $F^\times / F^{\times 2}$ has order $4$, and there is a biquadratic extension $E/F$ with $\mathrm{Gal}(E/F) \cong (\mathbb{Z}/2)^2$. Let $V \subset PGL_2(\mathbb{C})$ be the image of the group of the four matrices
$$1, \quad \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}, \quad \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}, \quad \begin{pmatrix} 0 & 1 \\ -1 & 0 \end{pmatrix}.$$
It is a Klein four group. Let $\varphi : W_F \to \mathrm{Gal}(E/F) \cong V$. The image of $\varphi$ is not contained in a torus of $PGL_2(\mathbb{C})$, so the lift $\tilde\varphi$ is irreducible, and $\tilde\pi$ is supercuspidal. The centralizer of $V$ in $PGL_2(\mathbb{C})$ is $V$ itself, by Exercise 10. The packet $\Pi_\varphi$ has four elements, one for each character of $V$, as Remark 5.6.8 predicts.

### The local Langlands conjecture

**Conjecture 5.6.7 (local Langlands conjecture).** Let $F$ be a local field and let $G$ be a connected reductive group over $F$. There is a partition of the set $\mathrm{Irr}(G(F))$ of isomorphism classes of irreducible smooth representations (Volume 6, Definition 1.1.9) into finite sets $\Pi_\varphi$, the *L-packets*, indexed by $\varphi \in \Phi(G)$, with the following properties.
1. For $G = GL_n$, each $\Pi_\varphi$ has one element, and $\varphi \mapsto \Pi_\varphi$ is the correspondence $\mathrm{rec}_n$ of Volume 0, Theorem 2.3.1, through Proposition 5.6.3.
2. For a torus $T$, each $\Pi_\varphi$ has one element, and the correspondence is Theorem 5.6.5.
3. If $G$ is unramified and $K$ is hyperspecial, then the packet of an unramified parameter $\varphi$ contains exactly one representation with a nonzero $K$-fixed vector, the one with Satake parameter $\varphi(\Phi)$. No other packet contains a $K$-spherical representation.
4. The representations in $\Pi_\varphi$ have the same central character $\omega_\varphi$, which Langlands constructs from $\varphi$.
5. A character $\chi$ of $G(F)$ attached to a class $a \in H^1(W_F, Z(G^\vee))$ satisfies $\Pi_{a\varphi} = \Pi_\varphi \otimes \chi$.
6. One element of $\Pi_\varphi$ is tempered if and only if all are, if and only if $\varphi(W_F)$ is bounded in $G^\vee$. One element of $\Pi_\varphi$ is square-integrable modulo the centre if and only if all are, if and only if the image of $\varphi$ is not contained in a Levi subgroup of a proper parabolic subgroup of ${}^L G$.
7. The correspondence is compatible with L-homomorphisms (Definition 5.4.6) for the cases where the transfer is defined, and it preserves the local factors attached to $r \circ \varphi$.

Lean: `Langlands.Shapes.LocalLanglands`, as a shape for quasi-split $G$, with property 6 and the refined form of Remark 5.6.8

The conjecture is in [Bor79], with the central character and the twists of properties 4 and 5. The properties do not characterize the packets in general. For $GL_n$ the preservation of the local factors of pairs does characterize them, by Henniart's work. For other groups, the expected characterization is through the endoscopic character identities of Arthur.

**Remark 5.6.8 (the refined conjecture).** Let $S_\varphi = \pi_0\big(C_{G^\vee}(\mathrm{im}\,\varphi) / Z(G^\vee)^{\Gamma_F}\big)$. For quasi-split $G$ with a fixed Whittaker datum, the refined conjecture predicts a bijection between $\Pi_\varphi$ and the set of irreducible characters of $S_\varphi$, under which the generic member corresponds to the trivial character. For inner forms, Vogan and Kottwitz replaced $G$ by all pure or extended inner forms together, and $Z(G^\vee)^{\Gamma_F}$ by a smaller group. In Example 5.6.6, $C_{PGL_2(\mathbb{C})}(V) = V$, so $S_\varphi = V$ has four characters, which matches the four elements of $\Pi_\varphi$.

The Lean shape of the conjecture needs the notions of this volume for a general group, and the library does not construct them yet. Thus `Langlands.Shapes.ReductiveGroupData` takes the group $G(F)$, the set $\Phi(G)$, the groups $S_\varphi$ with their irreducible representations, and the tempered, discrete and generic conditions as data. The shape then asks for a map $L : \mathrm{Irr}(G(F)) \to \Phi(G)$ with finite and nonempty fibres and property 6, and for each $\varphi$ an injective map $\Pi_\varphi \to \mathrm{Irr}(S_\varphi)$ that sends the generic members of a tempered packet to the trivial representation. The map is only injective, because for $G$ alone the packet is in general smaller than $\mathrm{Irr}(S_\varphi)$. The bijection of Remark 5.6.8 holds for the union of the packets over the pure inner forms. Since the data are free, the shape does not fix the packets. It records the form of the conjecture, and a later construction of the data will make it a statement.

### Known cases

For $F = \mathbb{R}$ or $\mathbb{C}$, Langlands proved the conjecture in 1973, in "On the classification of irreducible representations of real algebraic groups" (published 1989), with the Weil group $W_{\mathbb{R}}$ and without the factor $SL_2(\mathbb{C})$. For non-archimedean $F$:
1. $GL_n$: Harris and Taylor (2001), Henniart (2000), and Scholze (2013) with a new proof. This is Volume 0, Theorem 2.3.1.
2. Quasi-split symplectic and orthogonal groups in characteristic $0$: Arthur, *The endoscopic classification of representations* (2013).
3. Quasi-split unitary groups: Mok (2015), and inner forms by Kaletha, Minguez, Shin and White.
4. $GSp_4$: Gan and Takeda (2011). $G_2$: Gan and Savin (2023).
5. For all $G$, Fargues and Scholze (2021) construct a map $\pi \mapsto \varphi_\pi$ to semisimple parameters, that is, parameters trivial on $SL_2(\mathbb{C})$ up to semisimplification. It is compatible with the correspondence for $GL_n$ and with several of the other known cases.

### The global picture

Let $F$ be a number field and let $\pi = \otimes_v \pi_v$ be an automorphic representation of $G(\mathbb{A}_F)$. For almost all places $v$, $\pi_v$ is unramified and has a Satake parameter $s(\pi_v) \rtimes \Phi_v$ in ${}^L G_{F_v}$. The global conjecture predicts that these classes come from one homomorphism from a hypothetical Langlands group $L_F$ to ${}^L G$. Without $L_F$, the classes still give the partial L-functions $L^S(s, \pi, r)$ of Section 5.5, and the principle of functoriality of Volume 0, Conjecture 2.3.3 is stated with them.
