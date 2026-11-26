---
title: The global Weil group
nodes: []
sources: [Tat79, CF67]
status: checked
drafted_by: writer
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## The global Weil group

Theorem 7.7.1 matches only the Hecke characters of finite order with Galois characters. The reason is that $\mathrm{art}_F$ kills the connected component $D_F$ of $C_F$, so the abelianized Galois group $\mathrm{Gal}(F^{ab}/F) \cong C_F / D_F$ is too small. Weil found in 1951 a group $W_F$ with a map to $\mathrm{Gal}(\bar F/F)$ and with $W_F^{ab} \cong C_F$. It is the global analogue of the local Weil group of Chapter 1. This section gives its definition and its main properties without proofs. We follow [Tat79], Section 1.

For a topological group $W$, let $W^c$ be the closure of its commutator subgroup and $W^{ab} = W / W^c$. Let $G_F = \mathrm{Gal}(\bar F/F)$, and for a finite extension $E/F$ in $\bar F$ let $G_E = \mathrm{Gal}(\bar F/E)$.

**Definition 7.8.1 (Weil groups).** A *Weil group* of $F$ is a triple $(W_F, \varphi, \{r_E\})$. Here $W_F$ is a topological group and $\varphi : W_F \to G_F$ is a continuous homomorphism with dense image. For each finite extension $E/F$ in $\bar F$, let $W_E = \varphi^{-1}(G_E)$. Then $r_E : C_E \to W_E^{ab}$ is an isomorphism of topological groups. The following conditions must hold.
1. For each $E$, the composite of $r_E$ and the map $W_E^{ab} \to G_E^{ab}$ that $\varphi$ induces is the global reciprocity map $\mathrm{art}_E$.
2. For $w \in W_F$, $\sigma = \varphi(w)$ and $x \in C_E$, we have $r_{\sigma E}(\sigma x) = w \, r_E(x) \, w^{-1}$.
3. For $E \subset E'$, the inclusion $C_E \to C_{E'}$ corresponds under $r_E$ and $r_{E'}$ to the transfer $W_E^{ab} \to W_{E'}^{ab}$.
4. The natural map $W_F \to \varprojlim_E W_F / W_E^c$ is an isomorphism of topological groups.

The quotient $W_{E/F} = W_F / W_E^c$ for a finite Galois extension $E/F$ is the *relative Weil group*. Conditions 1 and 2 give an exact sequence
$$1 \to C_E \to W_{E/F} \to \mathrm{Gal}(E/F) \to 1,$$
in which $\mathrm{Gal}(E/F)$ acts on $C_E$ through its natural action. Condition 4 says that $W_F$ is determined by the groups $W_{E/F}$.

**Theorem 7.8.2 (Weil).** A Weil group of $F$ exists, and it is unique up to an isomorphism that is compatible with the maps $\varphi$ and $r_E$. For a finite Galois extension $E/F$, the class of the extension $W_{E/F}$ in $H^2(\mathrm{Gal}(E/F), C_E)$ is the fundamental class of Remark 7.3.8. For a number field $F$, the map $\varphi$ is surjective, and its kernel is the connected component of $W_F$.

Lean: not stated yet

The theorem shows how to construct $W_{E/F}$: it is the extension of $\mathrm{Gal}(E/F)$ by $C_E$ with the fundamental class. Then $W_F$ is the limit of these groups. So the existence of $W_F$ is a consequence of the cohomological form of global class field theory. In contrast to the local case of Chapter 1, the map $\varphi$ is not injective, and $W_F$ is not a subgroup of $G_F$. No explicit construction of $W_F$ is known, even for $F = \mathbb{Q}$.

**Proposition 7.8.3 (characters of the Weil group).** The map $r_F$ gives a bijection between the continuous characters of $W_F$ and the Hecke characters of $F$. A character of $W_F$ factors through $\varphi$ if and only if the Hecke character has finite order, and on these characters the bijection is the bijection of Theorem 7.7.1.

Lean: not stated yet

*Proof.* A continuous character of $W_F$ is trivial on $W_F^c$, so it is a character of $W_F^{ab} \cong C_F$. For the second claim, a character that factors through $\varphi$ has finite image, because $G_F$ is profinite. Conversely, a Hecke character of finite order is $\phi \circ \mathrm{art}_F$ by Theorem 7.7.1, and $\phi \circ \varphi$ is the character of $W_F$ that corresponds to it by condition 1. $\square$

This is the global Langlands correspondence for $GL_1$: the automorphic representations of $GL_1(\mathbb{A}_F)$ are the Hecke characters, and the Langlands parameters are the characters of $W_F$. Theorem 4.5.6 is the local form of this correspondence for tori. Langlands also proved the global form for all tori over $F$.

**Remark 7.8.4 (local and global Weil groups).** For each place $v$ of $F$ there is a continuous homomorphism $\theta_v : W_{F_v} \to W_F$ from the local Weil group of Chapter 1, or the group $W_\mathbb{R}$ or $W_\mathbb{C} = \mathbb{C}^\times$ at an infinite place. It is unique up to conjugation by an element of $W_F$. It is compatible with the inclusion $F_v^\times \to C_F$ and the isomorphisms $r_{F_v}$ and $r_F$ on abelianizations, and with the map $\mathrm{Gal}(\bar F_v/F_v) \to G_F$ of a choice of a place of $\bar F$ above $v$. Thus a representation $\rho$ of $W_F$ gives a representation $\rho \circ \theta_v$ of each $W_{F_v}$, defined up to isomorphism. The $L$-function of $\rho$ is the product of the local $L$-factors of these local representations. For a character this is the $L$-function of the Hecke character, and the local and global correspondences are compatible.

**Example 7.8.5 (two-dimensional representations from quadratic fields).** Let $E/F$ be a quadratic extension and let $\chi$ be a Hecke character of $E$. By Proposition 7.8.3, $\chi$ is a character of $W_E$, which has index 2 in $W_F$. So $\rho = \mathrm{Ind}_{W_E}^{W_F} \chi$ is a representation of dimension 2 of $W_F$. It is irreducible if $\chi$ is not equal to its conjugate $\chi^\sigma$, by Mackey's criterion. Its $L$-function is $L(s, \rho) = L(s, \chi)$, by the inductivity of $L$-functions. For $F = \mathbb{Q}$, $E$ imaginary quadratic and $\chi$ an algebraic Hecke character whose type at the complex place has weight $k - 1$, Hecke showed that $L(s, \chi)$ is the $L$-function of a modular form of weight $k$ with complex multiplication by $E$. Volume 4 treats these forms. The modular form of an elliptic curve with complex multiplication by $E$ is the case $k = 2$.

**Remark 7.8.6 (beyond the Weil group).** The representations of $W_F$ do not give all the Langlands parameters for $GL_n$ with $n \ge 2$. The image of the connected component of $W_F$ in each $W_{E/F}$ lies in the connected component of $C_E$, so the connected component of $W_F$ is abelian. From this one can show that every irreducible representation of $W_F$ is made from a Hecke character of a finite extension $E/F$ and a representation of a finite group. So the automorphic representations that come from $W_F$ are of a special kind. For example, the modular form of an elliptic curve over $\mathbb{Q}$ without complex multiplication does not come from a representation of $W_\mathbb{Q}$. Langlands conjectured the existence of a larger group $\mathcal{L}_F$, now called the Langlands group, whose representations of dimension $n$ should parametrize the automorphic representations of $GL_n(\mathbb{A}_F)$. This group is not known to exist. The statements of later volumes use $\ell$-adic Galois representations instead, as in the conjecture `Langlands.ReciprocityGL` of Volume 7.
