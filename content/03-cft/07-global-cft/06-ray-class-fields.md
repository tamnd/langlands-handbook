---
title: Ray class fields and the Hilbert class field
nodes: []
sources: [CF67, Mil20, Neu99]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Ray class fields and the Hilbert class field

The existence theorem gives one abelian extension for each open subgroup of finite index of $C_F$. The congruence subgroups $C_F^\mathfrak{m}$ of Definition 7.1.2 are cofinal among these subgroups, by Proposition 7.1.3. So the extensions that belong to them contain all the others. This section studies these extensions, the conductor of an abelian extension and the most important special case, the Hilbert class field.

**Definition 7.6.1 (ray class fields).** Let $\mathfrak{m}$ be a modulus of $F$. The *ray class field* $F_\mathfrak{m}$ of $\mathfrak{m}$ is the finite abelian extension of $F$ with $N_{F_\mathfrak{m}/F}(C_{F_\mathfrak{m}}) = C_F^\mathfrak{m}$. It exists and is unique by Theorem 7.4.3, and $\mathrm{art}_F$ induces an isomorphism $\mathrm{Cl}_\mathfrak{m} = C_F / C_F^\mathfrak{m} \cong \mathrm{Gal}(F_\mathfrak{m}/F)$.

Lean: `GlobalClassFieldTheory.GlobalClassFields.rayClassFieldGaloisEquivRayClassGroup`

If $\mathfrak{m} \mid \mathfrak{n}$, then $C_F^\mathfrak{n} \subset C_F^\mathfrak{m}$, and so $F_\mathfrak{m} \subset F_\mathfrak{n}$ by Corollary 7.4.4. The port defines $F_\mathfrak{m}$ as a subfield of a fixed separable closure of $F$, as the class field of the closed subgroup $C_F^\mathfrak{m}$, and the isomorphism above is the reciprocity isomorphism for this subgroup.

**Proposition 7.6.2 (ramification and splitting in ray class fields).** Let $\mathfrak{m} = \mathfrak{m}_0 \mathfrak{m}_\infty$ be a modulus of $F$.
1. A finite place $v$ with $v \nmid \mathfrak{m}_0$ is unramified in $F_\mathfrak{m}$. A real place $v \notin \mathfrak{m}_\infty$ stays real in $F_\mathfrak{m}$.
2. Let $\mathfrak{p}$ be a prime of $F$ with $\mathfrak{p} \nmid \mathfrak{m}_0$. Then $\mathfrak{p}$ splits completely in $F_\mathfrak{m}$ if and only if $\mathfrak{p} \in P_{\mathfrak{m},1}$, that is, if and only if $\mathfrak{p} = (\alpha)$ with $\alpha \equiv 1 \bmod^\times \mathfrak{m}$.
3. Every finite abelian extension $L/F$ is contained in $F_\mathfrak{m}$ for some $\mathfrak{m}$.

Lean: not stated yet

*Proof.* Part 1. If $v$ is finite and $v \nmid \mathfrak{m}_0$, then $U_v^{(m_v)} = \mathcal{O}_v^\times$, so the image of $\mathcal{O}_v^\times$ in $C_F$ lies in $C_F^\mathfrak{m}$. Corollary 7.4.4, part 1, shows that $v$ is unramified. If $v$ is real and $v \notin \mathfrak{m}_\infty$, then $U_v^{(0)} = F_v^\times$ lies in $W_\mathfrak{m}$. So $\mathrm{art}_{F_\mathfrak{m}/F}(F_v^\times) = 1$. By Proposition 7.2.2, part 1, this image is the image of the local map at $v$, which is the decomposition group at $v$. So the decomposition group is trivial, and $v$ stays real.

Part 2. By part 1 the prime $\mathfrak{p}$ is unramified, and $\mathfrak{p}$ splits completely if and only if $\mathrm{Frob}_\mathfrak{p} = 1$ in $\mathrm{Gal}(F_\mathfrak{m}/F)$. By Proposition 7.2.2, part 2, $\mathrm{Frob}_\mathfrak{p}^{-1}$ is the image of the idele $\varpi_\mathfrak{p}$ with a uniformizer at $\mathfrak{p}$ and $1$ at the other places. So $\mathfrak{p}$ splits completely if and only if the class of $\varpi_\mathfrak{p}$ in $\mathrm{Cl}_\mathfrak{m}$ is trivial. The isomorphism $\mathrm{Cl}_\mathfrak{m} \cong I^\mathfrak{m} / P_{\mathfrak{m},1}$ of Proposition 7.1.4 sends this class to the class of $\mathfrak{p}$. So the condition is $\mathfrak{p} \in P_{\mathfrak{m},1}$.

Part 3. The norm group $N_{L/F}(C_L)$ is open of finite index. By Proposition 7.1.3 it contains $C_F^\mathfrak{m}$ for some $\mathfrak{m}$. Then $L \subset F_\mathfrak{m}$ by Corollary 7.4.4. $\square$

Part 2 is the reason for the name. The primes of $F$ that split completely in $F_\mathfrak{m}$ are, up to finitely many, the prime ideals in the "ray" $P_{\mathfrak{m},1}$ of principal ideals with a generator near 1 at the places of $\mathfrak{m}$. By the theorem of Chebotarev, the extension $F_\mathfrak{m}$ is determined by this set of primes, so part 2 characterizes the ray class field.

**Example 7.6.3 (the ray class fields of $\mathbb{Q}$).** Let $N \ge 1$ and let $\infty$ be the real place. By Example 7.1.5, $\mathrm{Cl}_{N\infty} \cong (\mathbb{Z}/N\mathbb{Z})^\times$ and $\mathrm{Cl}_N \cong (\mathbb{Z}/N\mathbb{Z})^\times / \{\pm 1\}$. By Proposition 7.5.2, $\mathbb{Q}_{N\infty} = \mathbb{Q}(\zeta_N)$ and $\mathbb{Q}_N = \mathbb{Q}(\zeta_N)^+ = \mathbb{Q}(\zeta_N + \zeta_N^{-1})$, the maximal real subfield. For $p \nmid N$, part 2 of Proposition 7.6.2 for $\mathfrak{m} = N\infty$ says that $p$ splits completely in $\mathbb{Q}(\zeta_N)$ if and only if $p \equiv 1 \bmod N$. This is the classical result on cyclotomic fields. For $\mathfrak{m} = N$ it says that $p$ splits completely in $\mathbb{Q}(\zeta_N)^+$ if and only if $p \equiv \pm 1 \bmod N$.

### The conductor

**Definition 7.6.4 (the conductor).** Let $L/F$ be a finite abelian extension and $U = N_{L/F}(C_L)$. The *conductor* $\mathfrak{f}(L/F)$ is the smallest modulus $\mathfrak{f}$ with $C_F^\mathfrak{f} \subset U$, for the order $\mathfrak{m} \mid \mathfrak{n}$.

Lean: `ClassFieldTheory.IsAbelianConductor`

The conductor exists. By Proposition 7.1.3 there is a modulus $\mathfrak{m}$ with $C_F^\mathfrak{m} \subset U$. For two moduli $\mathfrak{m}$ and $\mathfrak{n}$, let $\mathfrak{d} = \gcd(\mathfrak{m}, \mathfrak{n})$, with exponent $\min(m_v, n_v)$ at $v$. The groups $U_v^{(m)}$ decrease with $m$, so $U_v^{(\min(m_v, n_v))} = U_v^{(m_v)} U_v^{(n_v)}$ for every $v$. Thus $W_\mathfrak{d} = W_\mathfrak{m} W_\mathfrak{n}$ and $C_F^\mathfrak{d} = C_F^\mathfrak{m} C_F^\mathfrak{n}$. So if $C_F^\mathfrak{m}$ and $C_F^\mathfrak{n}$ lie in $U$, then $C_F^\mathfrak{d}$ lies in $U$. Hence the set of moduli $\mathfrak{m}$ with $C_F^\mathfrak{m} \subset U$ has a smallest element. By Corollary 7.4.4, $C_F^\mathfrak{m} \subset U$ if and only if $L \subset F_\mathfrak{m}$. So $\mathfrak{f}(L/F)$ is the smallest modulus whose ray class field contains $L$. This is the form of the Lean definition: a modulus $\mathfrak{c}$ is the conductor of $L$ if, for every modulus $\mathfrak{m}$, $L$ embeds in $F_\mathfrak{m}$ if and only if $\mathfrak{c} \mid \mathfrak{m}$.

**Proposition 7.6.5 (the conductor is local).** Let $L/F$ be a finite abelian extension. For a place $v$ of $F$, choose a place $w$ of $L$ above $v$.
1. For a finite place $v$, the exponent of $v$ in $\mathfrak{f}(L/F)$ is the conductor exponent $f_v$ of the local extension $L_w/F_v$: the smallest $n \ge 0$ with $U_v^{(n)} \subset N_{L_w/F_v}(L_w^\times)$.
2. For a real place $v$, the exponent of $v$ in $\mathfrak{f}(L/F)$ is $1$ if $L_w = \mathbb{C}$, and $0$ if $L_w = \mathbb{R}$.
3. A place $v$ divides $\mathfrak{f}(L/F)$ if and only if $v$ is ramified in $L$. Here a real place is ramified if it becomes complex.

Lean: `ClassFieldTheory.abelianFullConductor_finiteExponent_eq_zero_iff_unramified`

*Proof.* Let $U = N_{L/F}(C_L)$ and let $U' \subset J_F$ be its preimage. By Proposition 7.2.2, part 1, and the local theory of Chapter 2, $U' \cap F_v^\times = N_{L_w/F_v}(L_w^\times)$ for every place $v$. Let $S$ be a finite set of places that contains the infinite places and the places that ramify in $L$. For $v \notin S$ the group $\mathcal{O}_v^\times$ lies in $U'$, by Corollary 7.4.4, part 1. Now let $\mathfrak{m}$ be a modulus with support in $S$. Then $W_\mathfrak{m} = \prod_{v \in S} U_v^{(m_v)} \times \prod_{v \notin S} \mathcal{O}_v^\times$. The second factor lies in $U'$. Since $U'$ is a group, $W_\mathfrak{m} \subset U'$ if and only if $U_v^{(m_v)} \subset N_{L_w/F_v}(L_w^\times)$ for each $v \in S$. Also $C_F^\mathfrak{m} \subset U$ if and only if $W_\mathfrak{m} \subset U'$. So the smallest such $\mathfrak{m}$ has the local exponents of parts 1 and 2. At a real place, $N_{\mathbb{C}/\mathbb{R}}(\mathbb{C}^\times) = \mathbb{R}_{>0} = U_v^{(1)}$, and this is all of $\mathbb{R}^\times$ only for $L_w = \mathbb{R}$. A modulus whose support is not in $S$ is never the smallest, because $\mathcal{O}_v^\times \subset U'$ for $v \notin S$. Part 3 follows: by local class field theory, $f_v = 0$ if and only if $\mathcal{O}_v^\times$ consists of norms, if and only if $L_w/F_v$ is unramified, see Theorem 4.2.2. $\square$

In particular the conductor and the discriminant of $L/F$ have the same prime divisors. The conductor-discriminant formula makes this precise. Corollary 6.4.3 gives $\mathfrak{d}_{L/F} = \prod_\chi \mathfrak{f}(\chi)$, where $\chi$ runs over the characters of $\mathrm{Gal}(L/F)$ and $\mathfrak{f}(\chi)$ is the Artin conductor. By Exercise 4, $\mathfrak{f}(\chi)$ is the finite part of the conductor of the fixed field of $\ker \chi$.

**Example 7.6.6 (quadratic fields).** Let $L = \mathbb{Q}(\sqrt{d})$ with discriminant $D$. The primes that ramify in $L$ are the primes that divide $D$. Then $\mathfrak{f}(L/\mathbb{Q}) = |D|$ if $D > 0$, and $\mathfrak{f}(L/\mathbb{Q}) = |D| \infty$ if $D < 0$. For an odd prime $p \mid D$ the extension is tamely ramified at $p$, and the local exponent is 1. At $p = 2$ the local exponent is 2 if $D \equiv 4 \bmod 8$ and 3 if $8 \mid D$, see Exercise 5. So $L \subset \mathbb{Q}(\zeta_{|D|})$, and $|D|$ is the smallest such $N$. For example $\mathbb{Q}(i)$ has conductor $4 \infty$ and $\mathbb{Q}(\sqrt{5})$ has conductor $5$.

### The Hilbert class field

**Definition 7.6.7 (Hilbert class fields).** The *Hilbert class field* of $F$ is the ray class field $H_F = F_1$ of the trivial modulus. The *narrow Hilbert class field* is $H_F^+ = F_{\mathfrak{m}_\infty}$, where $\mathfrak{m}_\infty$ is the set of all real places.

**Theorem 7.6.8 (the Hilbert class field).**
1. The field $H_F$ is the maximal abelian extension of $F$ that is unramified at all places, the infinite places included. The Artin map gives $\mathrm{Cl}_F \cong \mathrm{Gal}(H_F/F)$, and $[H_F : F] = h_F$.
2. A prime $\mathfrak{p}$ of $F$ splits completely in $H_F$ if and only if $\mathfrak{p}$ is principal.
3. The field $H_F^+$ is the maximal abelian extension of $F$ that is unramified at all finite places, and $\mathrm{Gal}(H_F^+/F) \cong \mathrm{Cl}_F^+$.

Lean: `GlobalClassFieldTheory.GlobalClassFields.smallHilbertClassFieldGaloisEquivClassGroup`

*Proof.* Part 1. By Proposition 7.6.5, part 3, a finite abelian extension $L/F$ is unramified at all places if and only if $\mathfrak{f}(L/F) = 1$, that is, if and only if $L \subset F_1$. The isomorphism is Definition 7.6.1 for $\mathfrak{m} = 1$, with $\mathrm{Cl}_1 = \mathrm{Cl}_F$ as in Section 7.1. Part 2 is Proposition 7.6.2, part 2, for $\mathfrak{m} = 1$, since $P_{1,1}$ is the group of all principal ideals. Part 3 is the same argument for $\mathfrak{m} = \mathfrak{m}_\infty$. A finite abelian extension is unramified at all finite places if and only if its conductor divides $\mathfrak{m}_\infty$. Example 7.1.6 gives $\mathrm{Cl}_{\mathfrak{m}_\infty} = \mathrm{Cl}_F^+$. $\square$

The port has the two fields under the names `smallHilbertClassField` and `bigHilbertClassField`. The theorem `GlobalClassFieldTheory.GlobalClassFields.smallHilbertClassField_everywhereUnramified` says that the first is unramified at every place, and `GlobalClassFieldTheory.GlobalClassFields.bigHilbertClassFieldQuotientEquivNarrowClassGroup` identifies the reciprocity quotient of the second with the narrow class group.

**Example 7.6.9 ($x^2 + 5y^2$).** Let $F = \mathbb{Q}(\sqrt{-5})$. Then $h_F = 2$, and we show that $H_F = F(i)$. The field $E = F(i) = \mathbb{Q}(\sqrt{-5}, i)$ contains $\mathbb{Q}(\sqrt{5})$, and $[E : F] = 2$. Only the primes $2$ and $5$ can ramify in $E/\mathbb{Q}$. The prime $5$ is unramified in $\mathbb{Q}(i)$, so its ramification index in $E$ is at most 2. It is ramified in $F$, so its index in $E$ is 2, and the primes of $F$ above $5$ are unramified in $E$. In the same way $2$ is unramified in $\mathbb{Q}(\sqrt{5})$ and ramified in $F$, so the primes of $F$ above $2$ are unramified in $E$. The field $F$ has no real place. So $E/F$ is unramified at all places, and $E \subset H_F$ by Theorem 7.6.8. Both fields have degree 2 over $F$, so $E = H_F$. Now let $p \ne 2, 5$ be a prime. If $p = x^2 + 5y^2$, then $p = \mathfrak{p}\bar{\mathfrak{p}}$ with $\mathfrak{p} = (x + y\sqrt{-5})$ principal. Conversely, if $p$ splits in $F$ and $\mathfrak{p}$ is principal, then $\mathfrak{p} = (x + y\sqrt{-5})$ and $p = N\mathfrak{p} = x^2 + 5y^2$. So $p = x^2 + 5y^2$ if and only if $p$ splits completely in $E$, by part 2. This holds if and only if $p$ splits completely in both $\mathbb{Q}(i)$ and $\mathbb{Q}(\sqrt{-5})$. By quadratic reciprocity, this is the condition $p \equiv 1 \bmod 4$ and $\left(\frac{-5}{p}\right) = 1$, that is, $p \equiv 1, 9 \bmod 20$. This is the answer of the introduction.

**Theorem 7.6.10 (the principal ideal theorem).** Every ideal of $\mathcal{O}_F$ becomes principal in $H_F$. That is, for every fractional ideal $\mathfrak{a}$ of $F$, the ideal $\mathfrak{a} \mathcal{O}_{H_F}$ is principal.

Lean: not stated yet

*Proof (sketch).* Let $H_2$ be the Hilbert class field of $H = H_F$. It is unramified over $F$, and it is Galois over $F$, because it is unique. Let $G = \mathrm{Gal}(H_2/F)$. Then $G' = \mathrm{Gal}(H_2/H)$ is the commutator subgroup of $G$, since $H$ is the maximal abelian subextension of $H_2/F$ that is unramified, and every abelian subextension of $H_2/F$ is unramified. Also $G'$ is abelian. Artin showed that the extension of ideals $\mathrm{Cl}_F \to \mathrm{Cl}_H$ corresponds, under the Artin maps $\mathrm{Cl}_F \cong G / G'$ and $\mathrm{Cl}_H \cong G'$, to the transfer $G/G' \to G'$. This is the compatibility of the Artin map with the inclusion $C_F \to C_H$, see [Neu99], Chapter VI. So the theorem reduces to a statement of group theory: for a finite group $G$ whose commutator subgroup $G'$ is abelian, the transfer from $G$ to $G'$ is trivial. Furtwängler proved this statement in 1930. Short proofs are due to Witt and to Iwasawa. $\square$

The ideals of $F$ become principal in $H_F$, but $H_F$ can have a nontrivial class group. Then the tower $F \subset H_F \subset H_{H_F} \subset \cdots$ does not stop at once. Golod and Shafarevich showed in 1964 that it can be infinite. For example it is infinite for $F = \mathbb{Q}(\sqrt{-2 \cdot 3 \cdot 5 \cdot 7 \cdot 11 \cdot 13})$, an example of Roquette. So it is not always possible to embed a number field in a field of class number one.
