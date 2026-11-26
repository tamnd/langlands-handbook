---
title: Hecke characters of finite order and Galois characters
nodes: [LGVAKJJD8Y]
sources: [CF67, Neu99, Tat79]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Hecke characters of finite order and Galois characters

Chapter 5 attached an $L$-function to each Hecke character, and Chapter 6 attached an $L$-function to each representation of a Galois group. This section shows that the two constructions agree in dimension one. It is the global Langlands correspondence for $GL_1$ in the case of finite order. The general case needs the global Weil group of Section 7.8.

**Theorem 7.7.1 (Hecke characters of finite order).** The map $\phi \mapsto \chi_\phi = \phi \circ \mathrm{art}_F$ is a bijection from the set of continuous characters $\phi : \mathrm{Gal}(\bar F/F) \to \mathbb{C}^\times$ to the set of Hecke characters of $F$ of finite order. Here $\mathrm{art}_F$ is composed with the restriction to $F^{ab}$. For each place $v$ of $F$:
1. $\phi$ is unramified at a finite place $v$ if and only if $\chi_\phi$ is unramified at $v$. Then $\chi_{\phi, v}(\varpi_v) = \phi(\mathrm{Frob}_v)^{-1}$.
2. The conductor of $\chi_\phi$ is the finite part of the conductor $\mathfrak{f}(L/F)$, where $L$ is the fixed field of $\ker \phi$.
3. $L(s, \chi_\phi) = L(s, \phi^{-1})$, where the right side is the Artin $L$-function of Chapter 6.

Node: LGVAKJJD8Y · Lean: `Langlands.GlobalReciprocity`

*Proof.* A continuous character $\phi$ of a profinite group has finite image, because $\mathbb{C}^\times$ has no small subgroups. So $\phi$ factors through $\mathrm{Gal}(L/F)$ for a finite abelian extension $L/F$. Then $\chi_\phi = \phi \circ \mathrm{art}_{L/F}$ is continuous, of finite order and trivial on $F^\times$ by Theorem 7.2.5. So $\chi_\phi$ is a Hecke character of finite order.

The map is injective, because $\mathrm{art}_F$ is surjective by Theorem 7.4.5. For surjectivity, let $\chi$ be a Hecke character of finite order $n$. Its image is the finite group $\mu_n$, which is discrete, so $\ker \chi$ is an open subgroup of finite index of $C_F$. An open subgroup contains the connected component $D_F$. By Theorem 7.4.5, $\mathrm{art}_F$ induces an isomorphism of topological groups $C_F / D_F \cong \mathrm{Gal}(F^{ab}/F)$. So $\chi = \phi \circ \mathrm{art}_F$ for a unique continuous character $\phi$ of $\mathrm{Gal}(F^{ab}/F)$, and $\phi$ extends to $\mathrm{Gal}(\bar F/F)$.

Part 1. By Proposition 7.2.4 the image of $\mathcal{O}_v^\times$ under $\mathrm{art}_{L/F}$ is the inertia group $I_v$. So $\chi_\phi$ is trivial on $\mathcal{O}_v^\times$ if and only if $\phi$ is trivial on $I_v$. The formula for $\chi_{\phi,v}(\varpi_v)$ is Proposition 7.2.2, part 2.

Part 2. The local component $\chi_{\phi, v}$ is $\phi \circ r_{L/F, v}$, by Proposition 7.2.2, part 1. By Theorem 4.2.2 its conductor exponent is the smallest $n$ with $U_v^{(n)} \subset N_{L_w/F_v}(L_w^\times)$, which is the local exponent of $\mathfrak{f}(L/F)$ by Proposition 7.6.5.

Part 3. At a finite place $v$ where $\phi$ is unramified, the Artin factor of $\phi^{-1}$ is $(1 - \phi^{-1}(\mathrm{Frob}_v) N(v)^{-s})^{-1}$, and the Hecke factor is $(1 - \chi_{\phi,v}(\varpi_v) N(v)^{-s})^{-1}$. These agree by part 1. At a ramified finite place both factors are 1, by part 1 and Definition 6.1.3. $\square$

The sign in part 1 comes from the geometric normalization of Volume 0, Chapter 3. With the classical map $\mathrm{Art}_F = \mathrm{art}_F^{-1}$ of the introduction, $\phi \mapsto \phi \circ \mathrm{Art}_F$ has $\chi(\varpi_v) = \phi(\mathrm{Frob}_v)$ and $L(s, \chi) = L(s, \phi)$. Both normalizations are common, and the formulas differ only by $\phi \leftrightarrow \phi^{-1}$.

The Lean statement `Langlands.GlobalReciprocity` asks, for each finite abelian extension $L$ of $K$ in an algebraic closure, for a homomorphism $C_K \to \mathrm{Gal}(L/K)$ that satisfies `Langlands.IsArtinMap`. By the proof above, such a map is all that is needed to move characters between the two sides. The theorem `Langlands.Bridge.globalReciprocity` proves the statement. The Lean project has no declaration yet for the bijection of Theorem 7.7.1 in the form of characters, and it has none for part 3.

**Example 7.7.2 (Dirichlet characters).** Let $F = \mathbb{Q}$ and let $\eta$ be a primitive Dirichlet character modulo $N$. Example 5.5.6 attached to $\eta$ a Hecke character $\chi_\eta$ of finite order and conductor $N$, with $\chi_\eta(\varpi_p) = \eta(p)$ for $p \nmid N$. By Proposition 7.5.2, $\mathrm{Gal}(\mathbb{Q}(\zeta_N)/\mathbb{Q}) \cong (\mathbb{Z}/N\mathbb{Z})^\times$, with $\sigma_a(\zeta_N) = \zeta_N^a$, and $\mathrm{Frob}_p = \sigma_p$. The Galois character $\phi$ with $\chi_\phi = \chi_\eta$ thus has $\phi(\sigma_p) = \eta(p)^{-1}$, and so $\phi(\sigma_a) = \bar\eta(a)$. Part 3 of the theorem gives $L(s, \eta) = L(s, \bar\phi)$, the classical identification of Dirichlet $L$-functions with abelian Artin $L$-functions.

**Remark 7.7.3 (characters of infinite order).** A Hecke character of infinite order is not of the form $\phi \circ \mathrm{art}_F$ for a character $\phi$ of the Galois group with values in $\mathbb{C}^\times$, because $\mathrm{art}_F$ kills $D_F$ and the character does not. For example, $|\cdot|_\mathbb{A}^{it}$ with $t \ne 0$ is not trivial on $D_F$. There are two ways to include such characters. The first is the global Weil group of the next section, whose abelianization is $C_F$ itself. The second is for the algebraic Hecke characters, which Weil called characters of type $A_0$, such as the character of an elliptic curve with complex multiplication. These correspond to $\ell$-adic characters of the Galois group, and the values are in a finite extension of $\mathbb{Q}_\ell$, not in $\mathbb{C}$. See Serre, *Abelian $\ell$-adic representations and elliptic curves*, Chapter II. The Lean project states neither of these yet.
