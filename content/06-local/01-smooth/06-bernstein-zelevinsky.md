---
title: The classification of Bernstein and Zelevinsky
nodes: []
sources: [BH06, HT01]
status: drafted
drafted_by: writer
reviewed_by: []
---
## The classification of Bernstein and Zelevinsky

For $GL_2$ the classification of Theorem 1.5.5 came from one reducibility criterion, Theorem 1.5.1. Bernstein and Zelevinsky found the general pattern for $GL_n$ in their papers of 1976 and 1977, and Zelevinsky completed it in 1980. The pattern is combinatorial. Its building blocks are the segments of supercuspidal representations, and the reducibility of the induced representations depends only on whether two segments are linked. This section gives the classification in outline, with the proofs of the main steps sketched. Complete proofs are in the papers of Bernstein and Zelevinsky and of Zelevinsky, which have no key in the map. The local Langlands correspondence of Chapter 3 reduces to the supercuspidal case through this classification.

Throughout, $\nu$ denotes the character $|\det|$ of $GL_m(K)$ for every $m$. For representations $\pi_i$ of $GL_{n_i}(K)$, the product $\pi_1 \times \dots \times \pi_r$ is the representation of $GL_n(K)$, $n = \sum n_i$, induced from the standard parabolic subgroup of type $(n_1, \dots, n_r)$, as in Definition 1.3.1.

### Segments

**Theorem 1.6.1 (Bernstein-Zelevinsky reducibility).** Let $\rho$ and $\rho'$ be irreducible supercuspidal representations of $GL_m(K)$ and $GL_{m'}(K)$. Then $\rho \times \rho'$ is reducible if and only if $m = m'$ and $\rho' \cong \rho \nu^{\pm 1}$.

Lean: not stated yet

*Sketch of proof.* By Theorem 1.3.8, the Jacquet module of $\rho \times \rho'$ for the parabolic of type $(m, m')$ has the constituents $\rho \otimes \rho'$ and, if $m = m'$, $\rho' \otimes \rho$; for the type $(m', m)$ the roles are reversed. As in the proof of Theorem 1.5.1, the length of $\rho \times \rho'$ is at most two, and when $m \ne m'$ or $\rho \not\cong \rho'$ an argument with Frobenius reciprocity and second adjointness shows that a proper subrepresentation would force a nonzero map $\rho \times \rho' \to \rho' \times \rho$ that is not an isomorphism. Such a map exists exactly when the normalized intertwining operator has a pole or a zero. The intertwining operator is controlled by the Plancherel measure, and Harish-Chandra's theory, or for $GL_n$ the Rankin-Selberg $\gamma$-factors $\gamma(s, \rho \times \rho'^\vee, \psi)$, shows that the singular points are at $\rho' \cong \rho \nu^{\pm 1}$. When $\rho' \cong \rho$ the representation $\rho \times \rho$ is irreducible because the intertwining operator is scalar. For $m = m' = 1$ this is Theorem 1.5.1. $\square$

The theorem singles out the following objects.

**Definition 1.6.2 (segment).** A *segment* is a set of supercuspidal representations of the form
$$\Delta = [\rho, \rho \nu^{k-1}] = \{\rho, \rho \nu, \dots, \rho \nu^{k-1}\},$$
for an irreducible supercuspidal representation $\rho$ of some $GL_m(K)$ and an integer $k \ge 1$. Its *length* is $k$, its *degree* is $mk$, its *beginning* is $\rho$ and its *end* is $\rho \nu^{k-1}$. Two segments $\Delta_1$ and $\Delta_2$ are *linked* if $\Delta_1 \cup \Delta_2$ is a segment and neither contains the other. If they are linked and $\Delta_2$ begins with $\rho_1 \nu^j$ for some $j \ge 1$, where $\rho_1$ is the beginning of $\Delta_1$, then $\Delta_1$ *precedes* $\Delta_2$.

Lean: not stated yet

For example, let $\rho = 1$ be the trivial character of $GL_1(K)$. The segments $[1, \nu]$ and $[\nu, \nu^2]$ are linked, since their union is the segment $[1, \nu^2]$ and neither contains the other. The first precedes the second. The segments $[1]$ and $[\nu]$ are linked too. The segments $[1]$ and $[\nu^2]$ are not linked, since $\{1, \nu^2\}$ is not a segment. The segments $[1, \nu^2]$ and $[\nu]$ are not linked, since one contains the other.

**Theorem 1.6.3 (the representations of a segment).** Let $\Delta = [\rho, \rho \nu^{k-1}]$ be a segment of degree $n$. The representation $\rho \times \rho \nu \times \dots \times \rho \nu^{k-1}$ of $GL_n(K)$ has a unique irreducible subrepresentation $Z(\Delta)$ and a unique irreducible quotient $L(\Delta)$.
1. $L(\Delta)$ is essentially square integrable. It is the unique irreducible subrepresentation of $\rho \nu^{k-1} \times \dots \times \rho \nu \times \rho$.
2. For $\rho$ a character $\chi$ of $GL_1(K)$, $Z(\Delta)$ is the character $\chi \nu^{(k-1)/2} \circ \det$ and $L(\Delta)$ is the *generalized Steinberg representation* $\mathrm{St}_k \otimes \chi \nu^{(k-1)/2}$.
3. The Jacquet module of $L(\Delta)$ for the parabolic subgroup of type $(m, \dots, m)$ is irreducible, equal to $\rho \nu^{k-1} \otimes \dots \otimes \rho \nu \otimes \rho$.

Lean: not stated yet

For $k = 2$ and $\rho = |\cdot|^{-1/2}$ this is Theorem 1.5.1: $Z([\nu^{-1/2}, \nu^{1/2}])$ is the trivial representation and $L([\nu^{-1/2}, \nu^{1/2}]) = \mathrm{St}$. The generalized Steinberg representation $\mathrm{St}_k$ of $GL_k(K)$ is the space of the locally constant functions on the flag variety $B \backslash GL_k(K)$, modulo the sum of the subspaces of the functions pulled back from the partial flag varieties. Its central character is trivial.

### Essentially square integrable representations

**Theorem 1.6.4 (Bernstein-Zelevinsky, the discrete series of $GL_n$).** The map $\Delta \mapsto L(\Delta)$ is a bijection from the set of segments of degree $n$ to the set of isomorphism classes of essentially square integrable irreducible representations of $GL_n(K)$.

Lean: not stated yet

The supercuspidal representations are the $L(\Delta)$ of the segments of length one. The essentially square integrable representations of $GL_2(K)$ are the supercuspidal ones and the $L([\chi \nu^{-1/2}, \chi \nu^{1/2}]) = \chi \mathrm{St}$. This agrees with Section 1.5. An irreducible representation is *tempered* if it is a twist by a character of a representation whose matrix coefficients lie in $L^{2 + \epsilon}(G / Z)$ for each $\epsilon > 0$. For $GL_n$ the tempered representations are the products $L(\Delta_1) \times \dots \times L(\Delta_r)$ with each $L(\Delta_i)$ unitary after twisting by the same character. These products are irreducible, by Theorem 1.6.6 below. Indeed, if $L(\Delta)$ and $L(\Delta')$ are unitary, the segments are centered: $\Delta = [\rho \nu^{(1-k)/2}, \rho \nu^{(k-1)/2}]$ with $\rho$ unitary. Two centered segments with the same $\rho$ are never linked, since either one contains the other or their union is not a segment.

### The classification

**Theorem 1.6.5 (Langlands classification for $GL_n$, Zelevinsky).** Let $\Delta_1, \dots, \Delta_r$ be segments, ordered so that $\Delta_i$ does not precede $\Delta_j$ for $i < j$.
1. The representation $L(\Delta_1) \times \dots \times L(\Delta_r)$ has a unique irreducible quotient $L(\Delta_1, \dots, \Delta_r)$. It does not depend on the ordering, among the orderings with this property.
2. Each irreducible representation of $GL_n(K)$ is isomorphic to some $L(\Delta_1, \dots, \Delta_r)$.
3. $L(\Delta_1, \dots, \Delta_r) \cong L(\Delta'_1, \dots, \Delta'_s)$ if and only if the multisets $\{\Delta_i\}$ and $\{\Delta'_j\}$ are equal.
4. The same statements hold with $Z$ in place of $L$ and subrepresentation in place of quotient. This gives a second bijection $\{\Delta_i\} \mapsto Z(\Delta_1, \dots, \Delta_r)$.

Lean: not stated yet

*Sketch of proof.* Part 2 starts from Theorem 1.4.5: an irreducible $\pi$ embeds in a product of supercuspidal representations, and by Theorem 1.4.6 the multiset of these representations is determined by $\pi$. Group this multiset into segments in the way prescribed by the Jacquet module of $\pi$. The main tool is the geometric lemma, Theorem 1.3.8, applied to products of segments. It shows that the Jacquet module of $L(\Delta_1) \times \dots \times L(\Delta_r)$ for the minimal parabolic of its supercuspidal support contains the representation $\otimes_i r(L(\Delta_i))$ with multiplicity one, as an extreme exponent. This gives the uniqueness of the quotient in part 1, and it identifies the multiset in part 3. Part 1 for $L$ is the Langlands classification, with the Langlands quotient taken for the order of decreasing real parts of the central exponents. Zelevinsky proved part 4 directly, with the representations $Z(\Delta)$. $\square$

The bijections of parts 1 and 4 are related by the *Zelevinsky involution*, an involution of the set of multisegments that sends $Z(\mathbf{a})$ to $L(\mathbf{a}^t)$. Mœglin and Waldspurger computed it combinatorially. On a single segment it sends $\Delta$ to the multisegment of the singletons of $\Delta$: $Z(\Delta) = L(\{\rho\}, \{\rho \nu\}, \dots, \{\rho \nu^{k-1}\})$.

**Theorem 1.6.6 (Zelevinsky's irreducibility criterion).** Let $\Delta_1, \dots, \Delta_r$ be segments. The representation $L(\Delta_1) \times \dots \times L(\Delta_r)$ is irreducible if and only if no two of the segments $\Delta_i$ are linked. The same holds for $Z(\Delta_1) \times \dots \times Z(\Delta_r)$.

Lean: not stated yet

For $r = 2$ and segments of length one this is Theorem 1.6.1. The criterion is the reason why the local Langlands correspondence for $GL_n$ is determined by its restriction to the supercuspidal representations.

**Example 1.6.7 (the irreducible subquotients of $\nu^{-1} \times 1 \times \nu$).** Let $n = 3$ and let the supercuspidal support be $\{\nu^{-1}, 1, \nu\}$, characters of $GL_1(K)$. The multisegments with this support are $\{[\nu^{-1}, \nu]\}$, $\{[\nu^{-1}, 1], [\nu]\}$, $\{[\nu^{-1}], [1, \nu]\}$ and $\{[\nu^{-1}], [1], [\nu]\}$. So $\nu^{-1} \times 1 \times \nu$ has four distinct irreducible subquotients. By Theorem 1.6.3, $L([\nu^{-1}, \nu]) = \mathrm{St}_3$ is the Steinberg representation of $GL_3(K)$, and $Z([\nu^{-1}, \nu])$ is the trivial representation, which is $L(\{\nu\}, \{1\}, \{\nu^{-1}\})$. The two others are $L([1, \nu], [\nu^{-1}])$ and $L([\nu^{-1}, 1], [\nu])$, the Langlands quotients of $(\mathrm{St}_2 \otimes \nu^{1/2}) \times \nu^{-1}$ and $\nu \times (\mathrm{St}_2 \otimes \nu^{-1/2})$. Their Langlands parameters, in the sense of Chapter 3, have $r = |\cdot|^{-1} \oplus 1 \oplus |\cdot|$ in a suitable normalization, and the monodromy $N$ has rank $2$, $1$, $1$ and $0$ for the four multisegments. The possible monodromy operators $N$ for this $r$ form a plane, and the centralizer of $r$ in $GL_3(\mathbb{C})$ has four orbits on it. The four representations correspond to the four orbits.

### The Bernstein decomposition

The supercuspidal support also decomposes the category of all smooth representations. Two pairs $(M, \sigma)$ and $(M', \sigma')$ of a Levi subgroup and a supercuspidal representation are *inertially equivalent* if there is $g \in G$ with $g M g^{-1} = M'$ and $g \sigma \cong \sigma' \otimes \chi$ for an unramified character $\chi$ of $M'$, that is, a character trivial on the elements of $M'$ whose determinants are units. The classes are the *inertial classes* $\mathfrak{s} = [M, \sigma]$.

**Theorem 1.6.8 (Bernstein decomposition).** The category of smooth representations of $GL_n(K)$ is the product of the full subcategories $\mathcal{R}^{\mathfrak{s}}$, over the inertial classes $\mathfrak{s}$. Here $\mathcal{R}^{\mathfrak{s}}$ consists of the representations each irreducible subquotient of which has supercuspidal support in $\mathfrak{s}$. Each $\mathcal{R}^{\mathfrak{s}}$ is equivalent to the category of modules over a Noetherian algebra, and its center is the ring of regular functions on the variety of supercuspidal supports in $\mathfrak{s}$.

Lean: not stated yet

For $\mathfrak{s} = [T, 1]$ in $GL_n$, the block $\mathcal{R}^{\mathfrak{s}}$ is the category of representations generated by their Iwahori-fixed vectors, and it is equivalent to the category of modules over the Iwahori-Hecke algebra of Section 1.2. This theorem of Borel and Casselman is the first case. The theory of types of Bushnell and Kutzko gives a similar description of each block of $GL_n$, as modules over a Hecke algebra of a pair $(J, \lambda)$. On the Galois side, the inertial class corresponds to the restriction of the parameter to the inertia group $I_K$. The decomposition is one reason to expect that the local correspondence respects inertia, and [HT01] and [Hen00] prove that it does.
