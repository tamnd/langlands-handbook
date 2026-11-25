---
title: The correspondence and its properties
nodes: []
sources: [Ser79, Tat79]
status: drafted
drafted_by: writer
reviewed_by: []
---
## The correspondence and its properties

On the Galois side the objects are the characters of $W_K$. Each character of $W_K$ restricts to a character of the compact group $I_K$. As in Lemma 4.1.2, its kernel on $I_K$ is open, so the restriction has finite image.

The conductor on the Galois side uses the upper numbering filtration of Serre [Ser79], Chapter IV. For a finite Galois extension $L / K$, the group $\mathrm{Gal}(L/K)$ has subgroups $\mathrm{Gal}(L/K)^u$ for real $u \ge -1$, with $\mathrm{Gal}(L/K)^0 = I(L/K)$. They are compatible with quotients. Thus they define closed subgroups $G_K^u$ of $G_K$, with $G_K^0 = I_K$, and $G_K^u \subset W_K$ for $u \ge 0$.

**Definition 4.2.1 (Artin conductor of a character).** Let $\phi$ be a character of $W_K$. Its *Artin conductor* $a(\phi)$ is the smallest integer $n \ge 0$ such that $\phi$ is trivial on $G_K^n$. The character $\phi$ is *unramified* if $a(\phi) = 0$, that is, if it is trivial on $I_K$.

Such an $n$ exists, because the kernel of $\phi$ on $I_K$ is open and the groups $G_K^u$ shrink to $\{1\}$. For a representation of higher dimension the Artin conductor has a more complicated definition, and for a character it reduces to Definition 4.2.1. This uses the theorem of Hasse and Arf, which says that the jumps of the upper filtration of an abelian extension are integers [Ser79, Chapter V].

**Theorem 4.2.2 (the conductor and the units).** Let $n \ge 0$ and let $L$ be a finite abelian extension of $K$. Then $r_{L/K}(U^{(n)}) = \mathrm{Gal}(L/K)^n$.

Lean: not stated yet

The case $n = 0$ is Proposition 2.1.8. The general case is in [Ser79], Chapter XV, Section 2, and its proof uses the computation of the norm on the filtration $U^{(n)}$. Serre uses the arithmetic normalization. The theorem is the same in both normalizations, because $U^{(n)}$ is a group and so $r_K(U^{(n)}) = r_K((U^{(n)})^{-1})$. For the fields $K_{\varpi, m}$ of Chapter 3 one can check the theorem directly, see Exercise 4.

**Theorem 4.2.3 (local Langlands for $GL_1$).** For a character $\phi$ of $W_K$, let $\chi_\phi = \phi \circ \mathrm{rec}_K$. The map $\phi \mapsto \chi_\phi$ is a bijection from the characters of $W_K$ to the characters of $K^\times$, with the following properties.
1. It is an isomorphism of groups: $\chi_{\phi\phi'} = \chi_\phi \chi_{\phi'}$.
2. It maps $\|\cdot\|^s$ to $|\cdot|^s$ for $s \in \mathbb{C}$.
3. The character $\phi$ is unramified if and only if $\chi_\phi$ is unramified. In that case $\chi_\phi(\varpi) = \phi(\Phi)$ for each uniformizer $\varpi$ and each geometric Frobenius $\Phi$.
4. $a(\phi) = a(\chi_\phi)$.
5. Let $L$ be a finite separable extension of $K$. Then $\chi_{\phi|_{W_L}} = \chi_\phi \circ N_{L/K}$.
6. The character $\phi$ has finite image if and only if $\chi_\phi$ has finite order. In that case $\phi$ factors through $\mathrm{Gal}(L/K)$, where $L$ is the finite abelian extension with norm group $\ker \chi_\phi$.

Lean: not stated yet

*Proof.* The bijection and part 1 hold because $\mathrm{rec}_K$ is an isomorphism of topological groups by Theorem 2.3.3. Parts 2 and 3 are Corollary 2.3.6, and $\phi(\Phi)$ does not depend on the choice of $\Phi$ when $\phi$ is unramified. For part 4, by Proposition 2.3.1 and the proof of Theorem 2.3.3, $\mathrm{rec}_K(U^{(n)})$ is a closed subgroup of the image of $I_K$ in $W_K^{ab}$. By Theorem 4.2.2 its image in each finite quotient $\mathrm{Gal}(L/K)$ is $\mathrm{Gal}(L/K)^n$, so it is the image of $G_K^n$. Thus $\chi_\phi$ is trivial on $U^{(n)}$ if and only if $\phi$ is trivial on $G_K^n$. Part 5 follows from Theorem 2.4.2, part 1: for $y \in L^\times$, the image of $\mathrm{rec}_L(y)$ in $W_K^{ab}$ is $\mathrm{rec}_K(N_{L/K}(y))$. For part 6, a character of finite order has a kernel of finite index, and the kernel is open because it contains some $U^{(n)}$. By Theorem 2.3.2 the kernel is the norm group of a finite abelian $L$, and then $\phi$ is trivial on the image of $W_L$, which has finite index. The converse is clear. $\square$

The Lean statement `Langlands.LocalReciprocityGL1` is the input of this theorem. Parts 1, 2, 3 and 6 are formal consequences of it and of the existence theorem. Parts 4 and 5 need Theorem 4.2.2 and Theorem 2.4.2.

**Example 4.2.4 (Dirichlet characters).** Let $\eta$ be a primitive Dirichlet character modulo $p^n$. Let $\sigma_a$ denote the automorphism of $\mathbb{Q}_p(\zeta_{p^n})$ with $\sigma_a(\zeta) = \zeta^a$. Let $\phi_\eta$ be the character of $W_{\mathbb{Q}_p}$ given by $\phi_\eta(w) = \eta(a)$ when $w$ acts on $\zeta_{p^n}$ as $\sigma_a$. By Example 3.5.6, $\mathrm{rec}(u)$ acts as $\sigma_u$ for $u \in \mathbb{Z}_p^\times$, and $\mathrm{rec}(p)$ acts trivially. Thus
$$\chi_{\phi_\eta} = \chi_\eta,$$
the character of Example 4.1.6. There is no inverse in the geometric normalization. With the Artin map $\mathrm{Art}$ one gets $\phi_\eta \circ \mathrm{Art} = \chi_\eta^{-1}$, because $\mathrm{Art}(u)$ acts as $\sigma_{u^{-1}}$. Both sides of part 4 equal $n$.

**Example 4.2.5 (tame characters).** Let $f = \varpi X + X^q$ and let $\alpha$ be a root of $X^{q-1} = -\varpi$, as in Example 3.3.5. For $\sigma \in I_K$ the element $\sigma(\alpha)/\alpha$ is a root of unity of order dividing $q-1$, and it does not depend on $\alpha$. This gives a character $\theta : I_K \to \mu_{q-1}(K)$, the *tame character*. By Example 3.3.5 and Theorem 3.5.5, $\theta(\mathrm{rec}_K(u)) = \omega(u)$, the Teichmuller representative of $u$. Thus a character $\chi$ with $a(\chi) \le 1$ and $\chi(u) = \eta(\omega(u))$, for a character $\eta$ of $\mu_{q-1}(K)$, corresponds to a character $\phi$ with $\phi|_{I_K} = \eta \circ \theta$.
