---
title: The reciprocity law
nodes: [LGVAKJJD8Y]
sources: [CF67, Mil20, Neu99]
status: checked
drafted_by: writer
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## The reciprocity law

This section states and proves the main theorem of global class field theory. There are two classical routes. The first one, in [Mil20], Chapters V to VII, and in Tate's chapter of [CF67], proves two inequalities for the norm index of a cyclic extension and then deduces the reciprocity law from the cyclotomic case. The second one, in [Neu99], Chapters IV and VI, puts the two inequalities into an abstract theory with a degree map onto $\hat{\mathbb{Z}}$ and builds the reciprocity map from Frobenius lifts. The Lean port follows the second route. We give both, with the second one in outline.

**Theorem 7.3.1 (global reciprocity).** Let $L/F$ be a finite abelian extension with group $G$.
1. The map $\mathrm{art}_{L/F}$ of Definition 7.2.1 is trivial on $F^\times$. It induces an isomorphism $C_F / N_{L/F}(C_L) \cong G$.
2. For each place $v$, the restriction of $\mathrm{art}_{L/F}$ to $F_v^\times$ is the local map $r_{L/F,v}$.
3. The map $\mathrm{art}_{L/F}$ is the only continuous homomorphism $C_F \to G$ that sends $\varpi_v$ to $\mathrm{Frob}_v^{-1}$ for almost all finite places $v$ unramified in $L$.

Node: LGVAKJJD8Y · Lean: `Langlands.GlobalReciprocity`

The Lean statement is weaker than the theorem as written here. It says that for $L$ an intermediate field of an algebraic closure of $F$, finite and abelian over $F$, there is a homomorphism $\mathrm{art} : C_F \to \mathrm{Gal}(L/F)$ that is continuous and surjective and such that $\mathrm{art}(\varpi_v)^{-1}$ is an arithmetic Frobenius at every prime $w$ of $L$ over a finite place $v$ unramified in $L$. This is the structure `Langlands.IsArtinMap`. The kernel $N_{L/F}(C_L)$ and the compatibility with the local maps are not part of the statement. Part 3 shows that the Frobenius condition determines the map, so the Lean statement pins down $\mathrm{art}_{L/F}$, but the identification of its kernel is a separate theorem of the port (Theorem 7.4.1). The theorem `Langlands.Bridge.globalReciprocity` proves the Lean statement, and the map in the proof is the geometric global norm residue map of the port.

*Proof of part 3.* Let $\psi, \psi'$ be two such maps, and let $\chi = \psi' \psi^{-1}$. Let $S$ be a finite set of places, containing the infinite places, outside which $\psi$ and $\psi'$ both have the Frobenius property. For $v \notin S$ and $u \in \mathcal{O}_v^\times$, both $\varpi_v$ and $u \varpi_v$ are uniformizers, so $\chi(u) = 1$ and $\chi$ is trivial on $F_v^\times$. Let $J^S \subset J_F$ be the group of ideles with component $1$ at all $v \in S$. Then $\chi$ is trivial on $F^\times J^S$. By weak approximation (Volume 1, Theorem 2.1.8), $F^\times$ is dense in $\prod_{v \in S} F_v^\times$, so $F^\times J^S$ is dense in $J_F$. Since $\chi$ is continuous with values in a finite discrete group, $\chi = 1$. $\square$

Part 2 holds by the definition of $\mathrm{art}_{L/F}$, once part 1 is known. Part 1 is the hard part. We first reduce it. An abelian group $G$ embeds in a product of cyclic quotients, so $L$ is the compositum of cyclic subextensions $L_i$. If $\mathrm{art}_{L_i/F}(a) = 1$ for all $i$, then $\mathrm{art}_{L/F}(a) = 1$, by Proposition 7.2.2, part 3. So it suffices to show that $\mathrm{art}_{L/F}(F^\times) = 1$ for $L/F$ cyclic. Given this, $\mathrm{art}_{L/F}$ is a surjection $C_F \to G$ (Proposition 7.2.4) that is trivial on $N_{L/F}(C_L)$ (Proposition 7.2.2, part 5). The isomorphism then follows from the inequality $[C_F : N_{L/F}(C_L)] \le [L : F]$, which is Theorem 7.3.3 below.

### The first inequality

Let $G$ be a finite cyclic group with generator $\sigma$, and let $A$ be a $G$-module. Let $N = \sum_{g \in G} g$. The Tate cohomology groups of $A$ in degrees $0$ and $-1$ are
$$\hat H^0(G, A) = A^G / N A, \qquad \hat H^{-1}(G, A) = \ker(N) / (\sigma - 1) A.$$
For cyclic $G$ the Tate groups are periodic of period 2, so these two groups give all of them. If both are finite, the Herbrand quotient is $h(A) = |\hat H^0(G, A)| / |\hat H^{-1}(G, A)|$. It is multiplicative in short exact sequences, and it is $1$ for finite modules. See [CF67], Chapter IV, Section 8, or [Mil20], Chapter II.

**Theorem 7.3.2 (the first inequality).** Let $L/F$ be cyclic of degree $n$. Then $h(C_L) = n$. In particular $[C_F : N_{L/F}(C_L)] \ge n$.

Lean: `GlobalClassFieldTheory.Cohomology.finrank_le_ideleClassNorm_index`

*Proof.* We have $C_L^G = C_F$ by Proposition 7.1.1, so $\hat H^0(G, C_L) = C_F / N C_L$. Thus the second claim follows from the first. Choose a finite set $S$ of places of $F$ that contains the infinite places and the places that ramify in $L$, and such that the primes of $L$ above $S$ generate the class group of $L$. Let $T$ be the set of places of $L$ above $S$. Then $J_L = L^\times J_{L,T}$, where $J_{L,T} = \prod_{w \in T} L_w^\times \times \prod_{w \notin T} \mathcal{O}_w^\times$, and $L^\times \cap J_{L,T} = \mathcal{O}_{L,T}^\times$, the group of $T$-units. So
$$C_L = J_{L,T} / \mathcal{O}_{L,T}^\times, \qquad h(C_L) = h(J_{L,T}) / h(\mathcal{O}_{L,T}^\times).$$

The idele part is local. For $v \in S$, the module $\prod_{w \mid v} L_w^\times$ is induced from the module $L_w^\times$ of the decomposition group $G_v$. By Shapiro's lemma and local class field theory its Herbrand quotient is $h(G_v, L_w^\times) = n_v = [L_w : F_v]$. For $v \notin S$, the module $\prod_{w \mid v} \mathcal{O}_w^\times$ is induced from the module $\mathcal{O}_w^\times$ of an unramified extension, which is cohomologically trivial. A limit argument over finite sets of such $v$ shows that the product has trivial cohomology. So $h(J_{L,T}) = \prod_{v \in S} n_v$.

The unit part is a lattice computation. By Dirichlet's $S$-unit theorem, $\mathcal{O}_{L,T}^\times$ modulo its torsion is a lattice in the hyperplane of sum zero in $\mathbb{R}^T$, and the log map is equivariant. The module $\mathbb{R}^T$ is $\bigoplus_{v \in S} \mathrm{Ind}_{G_v}^G \mathbb{R}$. Herbrand's lemma says that two $G$-stable lattices in the same real representation have the same Herbrand quotient. So $h(\mathcal{O}_{L,T}^\times) = h(\Lambda_0)$ for a lattice $\Lambda_0$ of sum zero in $\bigoplus_{v \in S} \mathbb{Z}[G/G_v]$. One computes $h(\mathbb{Z}[G/G_v]) = n_v$ and $h(\mathbb{Z}) = n$, so $h(\mathcal{O}_{L,T}^\times) = \big(\prod_{v \in S} n_v\big) / n$. Hence $h(C_L) = n$. $\square$

The Lean theorem has the form of the second claim. For a finite Galois extension whose group is generated by one element $\sigma$, it says that $[L : F]$ is at most the index of the norm subgroup of the idele class group. The port proves it with the decomposition above, through the files `IdeleClassHerbrandOutsideSupport` and `IdeleClassHerbrandSupportedFinal`.

### The second inequality

**Theorem 7.3.3 (the second inequality).** Let $L/F$ be a finite Galois extension of degree $n$. Then $[J_F : F^\times N_{L/F}(J_L)] \le n$. If $L/F$ is cyclic, then $[C_F : N_{L/F}(C_L)] = n$ and $\hat H^{-1}(G, C_L) = 1$.

Lean: `GlobalClassFieldTheory.ClassFieldAxiom.ideleClassNorm_index_le_prime_of_finrank_eq`

*Analytic proof.* Let $H = F^\times N_{L/F}(J_L)$. It is open, because it contains the open subgroup $N_{L/F}(J_L)$. Its image in $C_F$ is open, so it has finite index $h$ by Proposition 7.1.3. Each character $\chi$ of $J_F / H$ is a Hecke character of finite order. Let $S$ be the set of places that are infinite or ramified in $L$, and let $L(s, \chi) = \prod_{v \notin S} (1 - \chi(\varpi_v) N\mathfrak{p}_v^{-s})^{-1}$ be its partial $L$-function, for real $s > 1$. As in the proof of Lemma 7.2.3,
$$\sum_\chi \log L(s, \chi) = \sum_{v \notin S} \sum_\chi \chi(\varpi_v) N\mathfrak{p}_v^{-s} + O(1) = h \sum_{v \notin S,\ \varpi_v \in H} N\mathfrak{p}_v^{-s} + O(1)$$
as $s \to 1^+$. If $v$ splits completely in $L$, then $L_w = F_v$ and $\varpi_v$ is a local norm, so $\varpi_v \in H$. The primes that split completely in $L$ have Dirichlet density $1/n$, by the argument of Lemma 7.2.3 applied to $\zeta_L$. All the terms on the right are positive, so the right side is at least $(h/n) \log \frac{1}{s-1} + O(1)$.

On the left, the trivial character gives $\log \zeta_F(s) = \log \frac{1}{s-1} + O(1)$ by Corollary 5.4.8. For $\chi \ne 1$, $L(s, \chi)$ is holomorphic at $s = 1$, by Theorem 5.5.3. Let $m_\chi \ge 0$ be the order of its zero at $s = 1$. Then $\log L(s, \chi) = -m_\chi \log \frac{1}{s-1} + O(1)$. Comparing the two sides,
$$\frac{h}{n} \le 1 - \sum_{\chi \ne 1} m_\chi.$$
So $h \le n$, and in addition $L(1, \chi) \ne 0$ for all $\chi \ne 1$.

For $L/F$ cyclic, $N_{L/F}(C_L)$ is the image of $N_{L/F}(J_L)$ in $C_F$, so $[C_F : N_{L/F}(C_L)] = [J_F : H] \le n$. With Theorem 7.3.2 this gives equality, and $|\hat H^{-1}(G, C_L)| = |\hat H^0(G, C_L)| / h(C_L) = 1$. $\square$

The analytic proof gives the nonvanishing $L(1, \chi) \ne 0$ for free. This is the analytic core of Dirichlet's theorem. The algebraic proof avoids $L$-functions, and the port follows it.

*Algebraic proof, in outline.* We treat $L/F$ cyclic, which is all that the abstract route below needs. The general Galois case then follows from the norm limitation theorem, Theorem 7.4.2. The index is submultiplicative in towers: if $F \subset L' \subset L$, then $[C_F : N_{L/F} C_L] \le [C_F : N_{L'/F} C_{L'}] \cdot [C_{L'} : N_{L/L'} C_L]$. A cyclic group has a chain of subgroups with quotients of prime order. So it suffices to treat cyclic extensions of prime degree. Now let $L/F$ be cyclic of degree $p$. Let $F' = F(\mu_p)$ and $L' = L F'$. The degree $d = [F' : F]$ divides $p - 1$. The composite of the inclusion $C_F / N C_L \to C_{F'} / N C_{L'}$ and of the norm $N_{F'/F}$ back to $C_F / N C_L$ is $x \mapsto x^d$. This map is bijective, because $C_F / N C_L$ is killed by $p$. So we may assume $\mu_p \subset F$, and then $L = F(\sqrt[p]{a})$ by Kummer theory. Choose a finite set $S$ of places of $F$ that contains the infinite places, the places above $p$, the places where $a$ is not a unit, and enough primes to generate the class group. Kummer theory and the $S$-unit theorem give an explicit subgroup $E$ of $N_{L/F}(J_L)$, of the form $\prod_{v \in S} F_v^{\times p} \times \prod_{v \in S'} F_v^\times \times \prod_{v \notin S \cup S'} \mathcal{O}_v^\times$ for a second finite set $S'$. A count with the $S$-unit theorem gives $[J_F : F^\times E] = p$. See [CF67], Chapter VII, and [Neu99], Chapter VI, Section 4. $\square$

The Lean theorem is the prime degree case. For $L/F$ Galois of prime degree $p$ it says that the index of the norm subgroup of the idele class group is at most $p$. Its docstring calls it the prime degree bound that comes from the Kummer argument.

**Corollary 7.3.4 (the class field axiom).** Let $L/F$ be cyclic of degree $n$. Then $|\hat H^0(G, C_L)| = n$ and $\hat H^{-1}(G, C_L) = 1$.

Lean: `GlobalClassFieldTheory.ClassFieldAxiom.ideleClassNorm_index_eq_finrank_cyclic`

*Proof.* This is Theorem 7.3.3 for cyclic extensions. $\square$

The Lean theorem gives the first equality, the index of the norm subgroup of $C_F$ equals $[L : F]$, for every finite cyclic extension. The second equality is in the port as the triviality of the Tate group of degree $-1$, which the next proof uses.

**Corollary 7.3.5 (Hasse's norm theorem).** Let $L/F$ be cyclic. An element $a \in F^\times$ is a norm from $L^\times$ if and only if it is a norm from $L_w^\times$ at every place $v$ of $F$, with $w \mid v$.

Lean: `GlobalClassFieldTheory.ClassFieldAxiom.hasseNormPrinciple_cyclic`

*Proof.* The exact sequence $1 \to L^\times \to J_L \to C_L \to 1$ gives the exact sequence of Tate groups
$$\hat H^{-1}(G, C_L) \to \hat H^0(G, L^\times) \to \hat H^0(G, J_L).$$
The first group is trivial by Corollary 7.3.4. The middle group is $F^\times / N L^\times$. The last group is $J_F / N J_L = \bigoplus_v F_v^\times / N L_w^\times$, by Shapiro's lemma at each place. So the map $F^\times / N L^\times \to \bigoplus_v F_v^\times / N L_w^\times$ is injective. $\square$

The theorem fails for some noncyclic abelian extensions. The standard example is $L = \mathbb{Q}(\sqrt{13}, \sqrt{17})$ and $a = 5^2$, see the exercises at the end of [CF67].

### The abstract route

Neukirch's abstract class field theory isolates what the proof uses. Let $G$ be a profinite group and $A$ a discrete $G$-module. For a closed subgroup of finite index we write $G_K$ and $A_K = A^{G_K}$, as if it were the Galois group of a field $K$. The data are:
1. a continuous surjection $d : G \to \hat{\mathbb{Z}}$, whose kernel defines the "maximal unramified extension" $\tilde K$ of each $K$, with $f_K = [\hat{\mathbb{Z}} : d(G_K)]$;
2. a homomorphism $v : A_{k} \to \hat{\mathbb{Z}}$ on the base, whose image $Z$ contains $\mathbb{Z}$ and satisfies $Z / nZ \cong \mathbb{Z}/n\mathbb{Z}$ for all $n$, with $v(N_{K/k} A_K) = f_K Z$ for each $K$, which gives $v_K = f_K^{-1} \, v \circ N_{K/k} : A_K \to Z$;
3. the class field axiom: for each cyclic extension $L/K$, $|\hat H^0(G(L/K), A_L)| = [L : K]$ and $\hat H^{-1}(G(L/K), A_L) = 1$.

An element $\pi_K \in A_K$ with $v_K(\pi_K) = 1$ is a prime element. For a finite Galois extension $L/K$ and $\sigma \in G(L/K)$, choose a lift $\tilde\sigma \in G(\tilde L / K)$ whose degree $d_K(\tilde\sigma)$ is a positive integer, and let $\Sigma$ be the fixed field of $\tilde\sigma$. Then $\Sigma/K$ is finite. The Neukirch symbol is
$$r_{L/K}(\sigma) = N_{\Sigma/K}(\pi_\Sigma) \bmod N_{L/K} A_L.$$

**Theorem 7.3.6 (Neukirch).** Under the three conditions, $r_{L/K}$ is a well defined homomorphism. It induces an isomorphism $G(L/K)^{ab} \cong A_K / N_{L/K} A_L$, and these isomorphisms are compatible with restriction, norms and conjugation.

Lean: not stated yet

*Proof, in outline.* For $L/K$ unramified, $r_{L/K}$ sends the Frobenius to $\pi_K$, and the class field axiom for the cyclic group $G(L/K)$ shows that this is an isomorphism, with kernel $N A_L = \{a : v_K(a) \in f_{L/K} Z\}$. For $L/K$ cyclic and totally ramified, a computation with Hilbert 90 in the form $\hat H^{-1} = 1$ shows that $r_{L/K}$ is well defined and injective, and the class field axiom gives surjectivity. For a general Galois $L/K$, one reduces to Sylow subgroups, then to solvable towers, then to the maximal unramified subextension and a cyclic totally ramified extension, using the functoriality of the symbol. This is [Neu99], Chapter IV, Sections 4 to 6. $\square$

For a local field, $d$ is the Frobenius degree and $v$ is the normalized valuation. This gives local class field theory, and the symbol is the arithmetic map $\mathrm{Art}_K$ of Remark 2.1.5. For a number field $k = \mathbb{Q}$, let $\tilde{\mathbb{Q}}$ be the cyclotomic $\hat{\mathbb{Z}}$-extension, the unique subfield of $\mathbb{Q}(\mu_\infty)$ with group $\hat{\mathbb{Z}}$. Let $d : G_\mathbb{Q} \to \mathrm{Gal}(\tilde{\mathbb{Q}}/\mathbb{Q}) \cong \hat{\mathbb{Z}}$, and let $A = \varinjlim C_L$. Define $v_\mathbb{Q}$ as the composite
$$C_\mathbb{Q} \cong \mathbb{R}_{>0} \times \hat{\mathbb{Z}}^\times \to \hat{\mathbb{Z}}^\times \cong \mathrm{Gal}(\mathbb{Q}(\mu_\infty)/\mathbb{Q}) \to \mathrm{Gal}(\tilde{\mathbb{Q}}/\mathbb{Q}) \cong \hat{\mathbb{Z}},$$
which is the cyclotomic map of Section 7.2 followed by the projection. One checks condition 2 from the explicit formula, and condition 3 is Corollary 7.3.4. Theorem 7.3.6 then gives, for each finite Galois $L/F$, an isomorphism
$$r_{L/F} : \mathrm{Gal}(L/F)^{ab} \to C_F / N_{L/F} C_L.$$
Its target is $C_F$, so the reciprocity law is built in: the corresponding map from $J_F$ is trivial on $F^\times$ by construction. What remains is to compare it with $\mathrm{art}_{L/F}$. Let $L/F$ be abelian, and let $\mathrm{art}'_{L/F} : J_F \to G$ be the map $x \mapsto r_{L/F}^{-1}(x)^{-1}$. At a place $v$ unramified in $L$, one takes $\tilde\sigma$ to be a lift of the arithmetic Frobenius, and finds $r_{L/F}(\mathrm{Frob}_v) = \varpi_v$ in $C_F / N C_L$. So $\mathrm{art}'_{L/F}(\varpi_v) = \mathrm{Frob}_v^{-1}$, and $\mathrm{art}'_{L/F}$ is trivial on $\mathcal{O}_v^\times$, as in the proof of part 3. At the other places one shows that the restriction of $\mathrm{art}'_{L/F}$ to $F_v^\times$ is the local map $r_{L/F,v}$. The proof compares the global degree map on the decomposition group with the local degree map, and uses that local class field theory is the same abstract theory for the local data. So $\mathrm{art}'_{L/F}$ and $\mathrm{art}_{L/F}$ agree on each $F_v^\times$. These subgroups generate a dense subgroup of $J_F$, so the two maps are equal. Since $\mathrm{art}'_{L/F}$ is trivial on $F^\times$, this proves part 1 of Theorem 7.3.1. It also proves Theorem 7.4.1 below. See [Neu99], Chapter VI, Sections 4 to 6.

**Remark 7.3.7 (the Lean proof).** The theorems `Langlands.Bridge.globalReciprocity`, `Langlands.Bridge.globalExistence` and `Langlands.Bridge.kroneckerWeber` in `Langlands/Bridge/NYLLGlobal.lean` prove the three statements of `Langlands/Statements/ClassField.lean`. They are short. They move the theorems of the port under `Langlands/Ported/NYLL/ClassFieldTheory` into the form of the statements, which uses intermediate fields of an algebraic closure. The port is organized as follows.
1. `AbstractClassFieldTheory` is Neukirch's theory. The folder `Degree` has the degree map, the valuation, the prime elements and the Frobenius lifts. The folder `Reciprocity` has the symbol and the proof of Theorem 7.3.6, with files for the Sylow reduction, the maximal unramified case and the totally ramified case.
2. `GlobalClassFieldTheory/Reciprocity`, in the files whose names begin with `Cyclotomic` and `RationalCyclotomic`, builds the valuation $v_\mathbb{Q}$ from the cyclotomic extension and does the explicit computation of Proposition 7.2.6.
3. `GlobalClassFieldTheory/Cohomology` proves the first inequality (Theorem 7.3.2) with Herbrand quotients and Lemma 7.2.3.
4. `GlobalClassFieldTheory/ClassFieldAxiom` proves the second inequality by Kummer theory and $S$-units, the class field axiom (Corollary 7.3.4) and Hasse's norm theorem (Corollary 7.3.5).
5. The files `GlobalNormResidue`, `GlobalArtin`, `GlobalArtinCompatibility`, `LocalGlobalArtinCompatibility` and `ArithmeticNormalization` in `GlobalClassFieldTheory/Reciprocity` define the global norm residue map, compare it with the product of the local maps, and prove the product formula $\prod_v r_v(a) = 1$. The port's sign convention makes the field-facing map geometric. The arithmetic map is its inverse.
6. `GlobalClassFieldTheory/GlobalClassFields` proves the existence theorem and the classification (Section 7.4), and builds the ray class fields and the Hilbert class fields (Section 7.6).
7. `KroneckerWeber` proves the Kronecker-Weber theorem by a local route (Section 7.5).

The map `records/lean.json` lists the three bridge theorems with their axioms. The port names cited in this chapter are not in that record. Their status here comes from the sources of the Lean project, where they have no `sorry`.

**Remark 7.3.8 (the cohomological route).** Tate's chapter of [CF67] and [Mil20], Chapter VII, use the Brauer group instead. The two inequalities give $H^2(G, C_L) \cong \frac{1}{n}\mathbb{Z}/\mathbb{Z}$ with a canonical generator, the fundamental class, and Tate's theorem gives the reciprocity isomorphism as a cup product, as in the local case of Chapter 2. The invariant maps fit into the exact sequence
$$0 \to \mathrm{Br}(F) \to \bigoplus_v \mathrm{Br}(F_v) \xrightarrow{\sum \mathrm{inv}_v} \mathbb{Q}/\mathbb{Z} \to 0.$$
The fact that the invariants of a global class sum to zero is another product formula. It is equivalent to the reciprocity law. This route gives the global Weil group of Section 7.8 directly. The Lean project does not state the Brauer group sequence yet.
