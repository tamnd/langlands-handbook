---
title: The existence theorem
nodes: [LGX8K4ZEGW]
sources: [CF67, Mil20, Neu99]
status: checked
drafted_by: writer
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## The existence theorem

The reciprocity law attaches to each finite abelian extension $L/F$ an open subgroup $N_{L/F}(C_L)$ of finite index in $C_F$. The existence theorem says that every open subgroup of finite index arises in this way. Together they give a bijection between the finite abelian extensions of $F$ and the open subgroups of finite index of $C_F$, which reverses inclusions. This is the global form of the classification of Chapter 2, and the proof follows the local one: Kummer theory produces enough extensions when $F$ has enough roots of unity, and the norm limitation theorem removes this assumption.

### Norm limitation

**Theorem 7.4.1 (reciprocity for Galois extensions).** Let $L/F$ be a finite Galois extension with group $G$. The global norm residue map induces an isomorphism
$$C_F / N_{L/F}(C_L) \cong G^{ab}.$$

Lean: `GlobalClassFieldTheory.Reciprocity.globalNormResidueAbelianizationEquiv`

*Proof.* This is the output of Neukirch's Theorem 7.3.6 for the idele class formation, read through the comparison at the end of Section 7.3. $\square$

The Lean declaration is a definition of an equivalence of additive groups between $C_F / N_{L/F}(C_L)$ and the abelianization of $\mathrm{Gal}(L/F)$, for $L/F$ finite Galois. It is built from the abstract norm residue symbol of the port and the cyclotomic valuation of Section 7.3. The port also defines the geometric map `GlobalClassFieldTheory.Reciprocity.globalNormResidueMonoidHom` from $C_F$ to $\mathrm{Gal}(L/F)$ for $L/F$ abelian, and its inverse normalization `GlobalClassFieldTheory.Reciprocity.arithmeticGlobalNormResidueMonoidHom`. The theorem `GlobalClassFieldTheory.Reciprocity.globalNormResidueMonoidHom_mk` says that the geometric map on the class of an idele is the product of the local maps of Definition 7.2.1.

**Theorem 7.4.2 (norm limitation).** Let $L/F$ be a finite Galois extension and let $E$ be the maximal abelian subextension of $L/F$. Then $N_{L/F}(C_L) = N_{E/F}(C_E)$.

Lean: not stated yet

*Proof.* We have $N_{L/F}(C_L) = N_{E/F}(N_{L/E}(C_L)) \subset N_{E/F}(C_E)$. By Theorem 7.4.1 the index of the first group is $|G^{ab}| = [E : F]$. By Theorem 7.3.1 the index of the second group is $[E : F]$. So the two groups are equal. $\square$

The theorem says that norm groups see only abelian extensions. The same holds with $L/F$ any finite extension, not necessarily Galois, with $E$ the maximal abelian subextension of $L/F$; see Exercise 13. In Lean, Theorem 7.4.2 follows at once from the equivalence of Theorem 7.4.1, but the port does not state it in this form.

### The existence theorem

**Theorem 7.4.3 (the existence theorem).** Let $U \subset C_F$ be an open subgroup of finite index. There is a unique finite abelian extension $L/F$, inside a fixed algebraic closure, with $N_{L/F}(C_L) = U$. The map $\mathrm{art}_{L/F}$ induces $C_F / U \cong \mathrm{Gal}(L/F)$.

Node: LGX8K4ZEGW · Lean: `Langlands.GlobalExistence`

The Lean statement asks for an intermediate field $L$ of an algebraic closure of $F$, finite and abelian over $F$, and a map $\mathrm{art} : C_F \to \mathrm{Gal}(L/F)$ with the properties of `Langlands.IsArtinMap` and with kernel $U$. By Theorem 7.3.1, part 3, this map is $\mathrm{art}_{L/F}$, so its kernel is $N_{L/F}(C_L)$. The Lean statement does not include the uniqueness of $L$. The theorem `Langlands.Bridge.globalExistence` proves it. The class field of the port is `GlobalClassFieldTheory.GlobalClassFields.closedFiniteIndexClassField`, which lives in a separable closure of $F$. The bridge embeds it into the algebraic closure. Isomorphic extensions have the same norm group, so the kernel does not change.

*Proof.* Uniqueness. If $N_{L/F}(C_L) = N_{L'/F}(C_{L'}) = U$, then $N_{LL'/F}(C_{LL'})$ has the same index $[C_F : U]$. Indeed, an element of $\mathrm{Gal}(LL'/F)$ is trivial if and only if its restrictions to $L$ and $L'$ are trivial, so by Proposition 7.2.2, part 3, and Theorem 7.3.1 the norm group of $LL'$ is the intersection of the two norm groups. So $[LL' : F] = [L : F] = [L' : F]$ and $L = LL' = L'$.

Existence. Let $n = [C_F : U]$.

Step 1. Assume that $U$ contains $N_{L/F}(C_L)$ for some finite extension $L/F$. The Galois closure $\tilde L$ of $L/F$ satisfies $N_{\tilde L/F}(C_{\tilde L}) \subset N_{L/F}(C_L)$, so we may take $L$ Galois. By Theorem 7.4.2 we may then take $L$ abelian. Let $M \subset L$ be the fixed field of $\mathrm{art}_{L/F}(U)$. By Proposition 7.2.2, part 3, and Theorem 7.3.1, $N_{M/F}(C_M)$ is the inverse image of $\mathrm{Gal}(L/M)$ under $\mathrm{art}_{L/F}$, and this is $U$.

Step 2. Let $F' = F(\mu_n)$ and $U' = N_{F'/F}^{-1}(U) \subset C_{F'}$. Then $U'$ is open of finite index. Assume that $U' \supset N_{L'/F'}(C_{L'})$ for a finite extension $L'/F'$. Then $U \supset N_{F'/F}(U') \supset N_{L'/F}(C_{L'})$, and Step 1 applies. So we may assume that $\mu_n \subset F$.

Step 3. Let $\mu_n \subset F$. Then $U \supset C_F^n$, since $C_F/U$ has order $n$. By Proposition 7.1.3, the inverse image of $U$ in $J_F$ contains $\prod_{v \notin S} \mathcal{O}_v^\times$ for a finite set $S$ of places. Enlarge $S$ so that it contains the infinite places and the places above $n$, and so that $J_F = F^\times J_{F,S}$, where $J_{F,S} = \prod_{v \in S} F_v^\times \times \prod_{v \notin S} \mathcal{O}_v^\times$. Let $\mathcal{O}_S^\times$ be the $S$-units and $s = |S|$. By the $S$-unit theorem, $\mathcal{O}_S^\times \cong \mu(F) \times \mathbb{Z}^{s-1}$, and since $\mu_n \subset \mu(F)$ we get $\mathcal{O}_S^\times / \mathcal{O}_S^{\times n} \cong (\mathbb{Z}/n\mathbb{Z})^s$.

Let $L = F(\sqrt[n]{\mathcal{O}_S^\times})$. By Kummer theory $L/F$ is abelian with group $\mathrm{Hom}(\mathcal{O}_S^\times / \mathcal{O}_S^{\times n}, \mu_n)$, so $[L : F] = n^s$. It is unramified outside $S$, because $x^n - a$ is separable modulo $\mathfrak{p}_v$ for $a$ a unit at $v$ and $v \nmid n$. Let
$$E = \prod_{v \in S} F_v^{\times n} \times \prod_{v \notin S} \mathcal{O}_v^\times \subset J_F.$$
Its image in $C_F$ lies in $U$. We show that $F^\times E = F^\times N_{L/F}(J_L)$. Then $U \supset N_{L/F}(C_L)$ and Step 1 applies.

The group $E$ lies in the kernel of $\mathrm{art}_{L/F}$. At $v \in S$, the group $\mathrm{Gal}(L/F)$ has exponent $n$, so $r_{L/F,v}$ kills $F_v^{\times n}$. At $v \notin S$, the extension is unramified, so $r_{L/F,v}$ kills $\mathcal{O}_v^\times$. By Theorem 7.3.1, $F^\times E \subset F^\times N_{L/F}(J_L)$, and the second group has index $n^s$ in $J_F$. It remains to show that $[J_F : F^\times E] \le n^s$. Since $J_F = F^\times J_{F,S}$ and $F^\times \cap J_{F,S} = \mathcal{O}_S^\times$,
$$[J_F : F^\times E] = \frac{[J_{F,S} : E]}{[\mathcal{O}_S^\times : \mathcal{O}_S^\times \cap E]}.$$
For each place $v$ with $\mu_n \subset F_v$, one has $[F_v^\times : F_v^{\times n}] = n^2 / |n|_v$. This is the local index formula of [Neu99], Chapter II, Section 5, at the finite places, and a direct check at the infinite places. By the product formula, $\prod_{v \in S} |n|_v = 1$, so $[J_{F,S} : E] = n^{2s}$.

The last step is to show that $\mathcal{O}_S^\times \cap E = \mathcal{O}_S^{\times n}$. Let $a \in \mathcal{O}_S^\times \cap E$ and $M = F(\sqrt[n]{a})$. At each $v \in S$, $a$ is an $n$-th power in $F_v$, so $v$ splits completely in $M$ and $r_{M/F,v}$ is trivial. At each $v \notin S$, $M$ is unramified, so $r_{M/F,v}$ is trivial on $\mathcal{O}_v^\times$. So $\mathrm{art}_{M/F}$ is trivial on $J_{F,S}$, and by Theorem 7.3.1 also on $F^\times$. Thus it is trivial on $J_F = F^\times J_{F,S}$. By Proposition 7.2.4 it is surjective, so $M = F$ and $a \in F^{\times n} \cap \mathcal{O}_S^\times = \mathcal{O}_S^{\times n}$. Hence $[\mathcal{O}_S^\times : \mathcal{O}_S^\times \cap E] = n^s$ and $[J_F : F^\times E] = n^s$. $\square$

This is the proof in [Mil20], Chapter VII, and in [CF67], Chapter VII, written with the reciprocity law of Theorem 7.3.1. The port follows the same plan. The files `KummerNormDescent` and `CyclotomicKummerNormDescent` of `GlobalClassFieldTheory/GlobalClassFields` do Steps 2 and 3, and `ClosedFiniteIndexClassFieldConstruction` builds the class field.

### The classification

**Corollary 7.4.4 (the classification of abelian extensions).** The map $L \mapsto N_{L/F}(C_L)$ is a bijection from the set of finite abelian extensions of $F$ in $\bar F$ to the set of open subgroups of finite index of $C_F$. It reverses inclusions, and it sends composites to intersections and intersections to products. For a finite place $v$ and $U = N_{L/F}(C_L)$:
1. $v$ is unramified in $L$ if and only if the image of $\mathcal{O}_v^\times$ in $C_F$ lies in $U$;
2. $v$ splits completely in $L$ if and only if the image of $F_v^\times$ lies in $U$.

Lean: `GlobalClassFieldTheory.GlobalClassFields.infiniteAbelianClassFieldCorrespondence`

*Proof.* The bijection is Theorems 7.3.1 and 7.4.3. The order properties follow from Proposition 7.2.2, part 3. For parts 1 and 2, the image of $\mathcal{O}_v^\times$ under $\mathrm{art}_{L/F}$ is the inertia group $I_v$, and the image of $F_v^\times$ is the decomposition group $D_v$, by Proposition 7.2.4 and the local theory. The place $v$ is unramified if and only if $I_v = 1$, and splits completely if and only if $D_v = 1$. $\square$

The Lean declaration is a stronger form. It is an isomorphism of ordered sets between the closed subgroups of $C_F / D_F$, with the order reversed, and all the intermediate fields of the maximal abelian extension $F^{ab}$, finite or not. The open subgroups of finite index of $C_F$ are the open subgroups of the profinite group $C_F / D_F$, by Proposition 7.1.3, and they correspond to the finite extensions. The parts on ramification and splitting are separate theorems of the port, for example in the files `HilbertClassFieldPrimeSplitting` and `ConductorSupport`.

**Theorem 7.4.5 (the topological form).** The map $\mathrm{art}_F : C_F \to \mathrm{Gal}(F^{ab}/F)$ is surjective, with kernel the connected component $D_F$ of $C_F$. It induces an isomorphism of topological groups $C_F / D_F \cong \mathrm{Gal}(F^{ab}/F)$.

Lean: `ClassFieldTheory.topologicalGlobalReciprocity`

*Proof.* The kernel of $\mathrm{art}_F$ is the intersection of all the open subgroups of finite index, by Corollary 7.4.4. By Proposition 7.1.3 this intersection is $D_F$, since $C_F / D_F$ is profinite. The induced map $C_F / D_F \to \mathrm{Gal}(F^{ab}/F)$ is continuous and injective. Its image is dense by Proposition 7.2.4, and it is closed because $C_F / D_F$ is compact. So the map is a continuous bijection of compact groups, and thus a homeomorphism. $\square$

The Lean theorem says that there is an isomorphism of topological groups from the quotient of $C_F$ by its identity component to the abelianization of the absolute Galois group. It does not say in its type that the isomorphism is the norm residue map. The definition in its proof is.

**Example 7.4.6.** For $F = \mathbb{Q}$ we have $C_\mathbb{Q} \cong \mathbb{R}_{>0} \times \hat{\mathbb{Z}}^\times$ and $D_\mathbb{Q} = \mathbb{R}_{>0}$. So Theorem 7.4.5 gives $\mathrm{Gal}(\mathbb{Q}^{ab}/\mathbb{Q}) \cong \hat{\mathbb{Z}}^\times$. The cyclotomic computation of Section 7.2 shows that this isomorphism is the cyclotomic character on $\mathbb{Q}(\mu_\infty)$. So $\mathbb{Q}^{ab} = \mathbb{Q}(\mu_\infty)$, which is the Kronecker-Weber theorem. Section 7.5 gives the details. For an imaginary quadratic field $F$, the group $D_F$ is the image of $\mathbb{C}^\times$, and $\mathrm{Gal}(F^{ab}/F) \cong \hat{F}^\times / F^\times$ where $\hat F = F \otimes \hat{\mathbb{Z}}$. For a real quadratic field, $D_F$ contains a solenoid, and the description of $F^{ab}$ is Hilbert's twelfth problem, still open in general.
