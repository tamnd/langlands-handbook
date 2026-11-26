---
title: Reciprocity for the Weil group
nodes: [LG875TDM3B, LGAV7YV6K6]
sources: [Tat79, Ser67, Mil20]
status: checked
drafted_by: writer
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## Reciprocity for the Weil group

The map $r_K$ of Theorem 2.1.3 takes values in the profinite group $\mathrm{Gal}(K^{ab}/K)$. This section shows that it takes values in the image of $W_K$ and that it is an isomorphism onto $W_K^{ab}$. The proof needs one more theorem, the existence theorem, which Chapter 3 proves.

Write $W = W_K$ and $G = G_K$. Let $H = \overline{[G, G]}$ be the closure of the commutator subgroup of $G$. Its fixed field is $K^{ab}$, so $G^{ab} = G / H = \mathrm{Gal}(K^{ab}/K)$. Since $K^{ur} \subset K^{ab}$, the group $H$ is contained in $I_K = \mathrm{Gal}(\bar K / K^{ur})$, and thus $H \subset W$.

**Proposition 2.3.1 ($W_K^{ab}$ inside $G_K^{ab}$).** The inclusion $W_K \to G_K$ induces an injective continuous homomorphism $W_K^{ab} \to \mathrm{Gal}(K^{ab}/K)$. Its image is the set of $\sigma \in \mathrm{Gal}(K^{ab}/K)$ whose restriction to $K^{ur}$ is an integral power of $\Phi$. It maps the image of $I_K$ in $W_K^{ab}$ homeomorphically onto $\mathrm{Gal}(K^{ab}/K^{ur})$.

Lean: not stated yet

*Proof.* The kernel of $W \to G^{ab}$ is $W \cap H = H$. We show that $H$ is the closure $\overline{[W, W]}$ of the commutator subgroup in $W$. Recall from Chapter 1 that $I_K$ is open in $W$ and carries its profinite topology. An open subgroup is also closed. The group $H$ is closed in $I_K$, so it is closed in $W$. It contains $[W, W]$, so $\overline{[W, W]} \subset H$. For the other inclusion, $[W, W]$ lies in $I_K$, because $W / I_K \cong \mathbb{Z}$ is abelian. As the topologies agree on $I_K$ and $I_K$ is closed in both groups, the closure of $[W, W]$ in $W$ equals its closure $C$ in $G$. The group $W$ is dense in $G$, and the commutator map $G \times G \to G$ is continuous. Thus each commutator of $G$ is a limit of commutators of $W$, and $[G, G] \subset C$. Hence $H \subset C = \overline{[W, W]}$. This proves that the map $W^{ab} \to G^{ab}$ is injective. It is continuous because $W \to G$ is continuous.

An element $\sigma \in G^{ab}$ lifts to some $\tilde\sigma \in G$. The restriction of $\sigma$ to $K^{ur}$ is an integral power of $\Phi$ if and only if $\tilde \sigma \in W$, by the definition of $W$. This does not depend on the lift, because $H \subset W$. This gives the image. Finally the image of $I_K$ in $W^{ab}$ is $I_K / H$, which is compact. A continuous bijection from a compact space onto a Hausdorff space is a homeomorphism, and the image of $I_K$ in $G^{ab}$ is $\mathrm{Gal}(K^{ab}/K^{ur})$. $\square$

The injectivity of the reciprocity map needs the following theorem. It says that every candidate subgroup of $K^\times$ is a norm group.

**Theorem 2.3.2 (local existence).** Let $U$ be an open subgroup of finite index of $K^\times$. There is a finite abelian extension $L$ of $K$ with $N_{L/K}(L^\times) = U$. The field $L$ is unique.

Node: LG875TDM3B · Lean: `Langlands.LocalExistence`

The uniqueness of $L$ is Proposition 2.1.7. Chapter 3 proves the existence with Lubin-Tate theory. That proof uses Theorem 2.1.2 and Theorem 2.1.3, so there is no circle. If $K$ has characteristic 0, each subgroup of finite index of $K^\times$ is open, because it contains the open subgroup $(K^\times)^m$ of $m$-th powers for its index $m$. In characteristic $p$ the group $(K^\times)^p$ is not open, and there are subgroups of finite index that are not open. The theorem needs the word open there.

The open subgroups $\langle \varpi^m \rangle \times U^{(n)}$ for $m \ge 1$ and $n \ge 0$ have intersection $\{1\}$. By Theorem 2.3.2 each one is a norm group. Thus the intersection of all norm groups of finite abelian extensions is trivial. This is the input from Theorem 2.3.2 in the next proof.

**Theorem 2.3.3 (local reciprocity).** There is a unique isomorphism of topological groups $\mathrm{rec}_K : K^\times \to W_K^{ab}$ with the following two properties.
1. For each uniformizer $\varpi$ of $K$, the element $\mathrm{rec}_K(\varpi)$ is the class of a geometric Frobenius.
2. For each finite abelian extension $L$ of $K$, the composite of $\mathrm{rec}_K$ with the restriction $W_K^{ab} \to \mathrm{Gal}(L/K)$ is surjective, and its kernel is $N_{L/K}(L^\times)$.

Node: LGAV7YV6K6 · Lean: `Langlands.LocalReciprocityGL1`

*Proof.* Let $\iota : W^{ab} \to G^{ab}$ be the injection of Proposition 2.3.1, and let $r_K$ be the map of Theorem 2.1.3. For each $x$, the restriction of $r_K(x)$ to $K^{ur}$ is $\Phi^{v(x)}$. By Proposition 2.3.1 there is a unique $\mathrm{rec}_K(x) \in W^{ab}$ with $\iota(\mathrm{rec}_K(x)) = r_K(x)$. The map $\mathrm{rec}_K$ is a homomorphism, because $r_K$ is one and $\iota$ is injective.

Property 2 holds because the restriction $W^{ab} \to \mathrm{Gal}(L/K)$ factors through $\iota$, and $r_K$ has property 2 of Theorem 2.1.3. For property 1, let $\varpi$ be a uniformizer and let $w \in W$ be a lift of $\mathrm{rec}_K(\varpi)$. The restriction of $w$ to $K^{ur}$ is $\Phi$, so $w$ acts on $\bar k$ as $x \mapsto x^{1/q}$. Thus $w$ is a geometric Frobenius.

Next, $\mathrm{rec}_K$ is injective. Its kernel is the set of $x$ with $r_K(x) = 1$, which is the intersection of the norm groups of all finite abelian extensions. By Theorem 2.3.2 this intersection is trivial.

Next, $\mathrm{rec}_K$ maps $\mathcal{O}_K^\times$ onto the image $I$ of $I_K$ in $W^{ab}$. A unit acts trivially on $K^{ur}$, so $\mathrm{rec}_K(\mathcal{O}_K^\times) \subset I$. By Proposition 2.3.1 we can view $I$ as the profinite group $\mathrm{Gal}(K^{ab}/K^{ur})$. The map $r_K$ is continuous on $\mathcal{O}_K^\times$, because the kernel of each $r_{L/K}$ is open by Proposition 2.1.6. Thus $\mathrm{rec}_K(\mathcal{O}_K^\times)$ is compact and closed in $I$. The finite quotients of $I$ are the groups $\mathrm{Gal}(L K^{ur} / K^{ur})$ for finite abelian $L$, and the restriction to $L$ identifies such a group with $I(L/K)$. By Proposition 2.1.8 the image of $\mathcal{O}_K^\times$ in each of them is the whole group. A closed subgroup of a profinite group that maps onto each finite quotient is the whole group. Thus $\mathrm{rec}_K(\mathcal{O}_K^\times) = I$.

Now $\mathrm{rec}_K$ is surjective, because its image contains $I$ and an element of degree $-1$, and $W^{ab} / I \cong \mathbb{Z}$ is generated by the class of such an element. The map is continuous, because its restriction to the open subgroup $\mathcal{O}_K^\times$ is continuous. It is open, because $\mathcal{O}_K^\times$ is compact, so $\mathrm{rec}_K$ maps $\mathcal{O}_K^\times$ homeomorphically onto the open subgroup $I$. Thus $\mathrm{rec}_K$ is an isomorphism of topological groups.

Finally, uniqueness. Let $\mathrm{rec}'$ be a second isomorphism with properties 1 and 2. Then $\iota \circ \mathrm{rec}'$ has properties 1 and 2 of Theorem 2.1.3. By the uniqueness in that theorem, $\iota \circ \mathrm{rec}' = r_K = \iota \circ \mathrm{rec}_K$. As $\iota$ is injective, $\mathrm{rec}' = \mathrm{rec}_K$. $\square$

The degree map of Chapter 1 descends to $W_K^{ab}$, and the proof shows that $d(\mathrm{rec}_K(x)) = -v(x)$. With $\|w\| = q^{d(w)}$ this reads $\|\mathrm{rec}_K(x)\| = |x|$.

**Remark 2.3.4 (the arithmetic normalization).** The map $x \mapsto \mathrm{rec}_K(x^{-1})$ is also an isomorphism of topological groups. It sends each uniformizer to the class of an arithmetic Frobenius, and it has property 2. It is the Artin map of [Ser67] and [Mil20], viewed in $W_K^{ab}$. The condition on uniformizers is what makes the map unique. The fidelity test `Langlands.Fidelity.not_existsUnique_unnormalized` of the Lean project shows this: without property 1, the map $x \mapsto \mathrm{rec}_K(x)^{-1}$ is a second solution.

**Corollary 2.3.5 (the classification of abelian extensions).** The map $L \mapsto N_{L/K}(L^\times)$ is a bijection from the set of finite abelian extensions of $K$ in $\bar K$ to the set of open subgroups of finite index of $K^\times$. It reverses inclusions, and it sends a compositum to an intersection. For each such $L$, $\mathrm{rec}_K$ induces an isomorphism $K^\times / N_{L/K}(L^\times) \cong \mathrm{Gal}(L/K)$.

Lean: not stated yet

*Proof.* The map is well defined by Proposition 2.1.6, injective by Proposition 2.1.7, and surjective by Theorem 2.3.2. Proposition 2.1.7 gives the other claims. $\square$

### The local Langlands correspondence for $GL_1$

A *character* of a topological group is a continuous homomorphism to $\mathbb{C}^\times$. Each character of $W_K$ is trivial on $\overline{[W_K, W_K]}$, because $\mathbb{C}^\times$ is abelian and Hausdorff. Thus the characters of $W_K$ are the characters of $W_K^{ab}$.

**Corollary 2.3.6 (local Langlands for $GL_1$).** The map $\phi \mapsto \phi \circ \mathrm{rec}_K$ is a bijection from the set of characters of $W_K$ to the set of characters of $K^\times = GL_1(K)$. It sends the unramified characters of $W_K$, the characters that are trivial on $I_K$, to the unramified characters of $K^\times$, the characters that are trivial on $\mathcal{O}_K^\times$. It sends $\|\cdot\|$ to $|\cdot|$.

Lean: not stated yet

*Proof.* The map $\mathrm{rec}_K$ is an isomorphism of topological groups, so composition with it is a bijection on characters. By the proof of Theorem 2.3.3, $\mathrm{rec}_K(\mathcal{O}_K^\times)$ is the image of $I_K$. This gives the statement on unramified characters. The last claim is the formula $\|\mathrm{rec}_K(x)\| = |x|$. $\square$

This is the first case of the local Langlands correspondence. The characters of $K^\times$ are the irreducible smooth representations of $GL_1(K)$, and the characters of $W_K$ are the representations of $W_K$ of dimension 1. Chapter 4 studies the correspondence in detail. It shows that the bijection preserves conductors, $L$-factors and $\varepsilon$-factors, and it extends the bijection to tori.
