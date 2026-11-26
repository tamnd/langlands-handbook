---
title: Ideles, idele classes and ray class groups
nodes: []
sources: [CF67, Mil20, Neu99]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Ideles, idele classes and ray class groups

The idele class group $C_F$ is the group that global class field theory attaches to $F$. This section recalls it from Volume 1, Chapter 3, and adds three things that the theory needs: the maps between idele class groups in an extension $L/F$, the open subgroups of finite index of $C_F$, and the ray class groups, which describe these subgroups in terms of ideals. The example to keep in mind is $F = \mathbb{Q}$, where $C_\mathbb{Q} \cong \mathbb{R}_{>0} \times \hat{\mathbb{Z}}^\times$ by Example 3.4.8 of Volume 1, and where the ray class groups are the groups $(\mathbb{Z}/N\mathbb{Z})^\times$.

### Ideles and idele classes

Recall the objects of Volume 1, Chapter 3. The idele group $J_F$ is the restricted product of the groups $F_v^\times$ with respect to the groups $\mathcal{O}_v^\times$ (Definition 3.4.1). The group $F^\times$ is discrete in $J_F$ (Proposition 3.4.4), and $C_F = J_F / F^\times$ is the idele class group (Definition 3.4.5). By the product formula (Theorem 3.3.4) the norm $|x|_\mathbb{A} = \prod_v |x_v|_v$ is trivial on $F^\times$, so it induces a map $C_F \to \mathbb{R}_{>0}$. Its kernel $C_F^1$ is compact (Theorem 3.5.2), and $C_F \cong C_F^1 \times \mathbb{R}_{>0}$ (Proposition 3.4.6). The map $\iota : J_F \to I_F$ to the group of fractional ideals gives the exact sequence of Theorem 3.4.7,
$$1 \to \mathcal{O}_F^\times \to U_F \to C_F \to \mathrm{Cl}_F \to 1, \qquad U_F = \prod_{v \mid \infty} F_v^\times \times \prod_{v \nmid \infty} \mathcal{O}_v^\times.$$
For each place $v$ we view $F_v^\times$ as the subgroup of $J_F$ of the ideles with component $1$ outside $v$, and also as a subgroup of $C_F$. The map $F_v^\times \to C_F$ is injective, because an element of $F^\times$ with component 1 at all places but one is 1.

Let $L/F$ be a finite extension of degree $n$. For a place $v$ of $F$, the algebra $L \otimes_F F_v$ is the product of the completions $L_w$ for $w \mid v$, and $\sum_{w \mid v} [L_w : F_v] = n$. The inclusions $F_v \to L_w$ give an injective homomorphism $J_F \to J_L$: the idele $x$ goes to the idele with component $x_v$ at every $w \mid v$. The *norm* $N_{L/F} : J_L \to J_F$ is the homomorphism
$$N_{L/F}(y)_v = \prod_{w \mid v} N_{L_w/F_v}(y_w).$$
It is well defined, because $N_{L_w/F_v}(\mathcal{O}_w^\times) \subset \mathcal{O}_v^\times$. It is continuous, and $|N_{L/F}(y)|_\mathbb{A} = |y|_\mathbb{A}$ by the formula $|N_{L_w/F_v}(a)|_v = |a|_w$ of Volume 1.

**Proposition 7.1.1 (ideles in extensions).** Let $L/F$ be a finite extension of degree $n$.
1. The intersection of $J_F$ and $L^\times$ in $J_L$ is $F^\times$. Thus $C_F \to C_L$ is injective.
2. For $a \in L^\times$, the norm of the principal idele $a$ is the principal idele $N_{L/F}(a)$. Thus the norm induces a continuous homomorphism $N_{L/F} : C_L \to C_F$. The composite $C_F \to C_L \to C_F$ is $x \mapsto x^n$.
3. Let $L/F$ be Galois with group $G$. Then $G$ acts on $J_L$ by $(\sigma y)_{\sigma w} = \sigma(y_w)$, where $\sigma : L_w \to L_{\sigma w}$ is the map induced by $\sigma$. We have $J_L^G = J_F$, $C_L^G = C_F$, and $N_{L/F}(y) = \prod_{\sigma \in G} \sigma y$.
4. For $M \supset L \supset F$, $N_{M/F} = N_{L/F} \circ N_{M/L}$ on $J_M$ and on $C_M$.

Lean: not stated yet

*Proof.* Part 2. For $a \in L$, the norm $N_{L/F}(a)$ is the determinant of multiplication by $a$ on $L$. After the base change to $F_v$ it is the determinant on $\prod_{w \mid v} L_w$, which is $\prod_{w \mid v} N_{L_w/F_v}(a)$. The composite in part 2 is $x \mapsto \prod_{w \mid v} x_v^{[L_w : F_v]} = x_v^n$ at each $v$.

Part 3. The group $G$ permutes the places $w$ over $v$ transitively, and the stabilizer of $w$ is the decomposition group $D_w \cong \mathrm{Gal}(L_w/F_v)$. So the $G$-module $\prod_{w \mid v} L_w^\times$ is induced from the $D_w$-module $L_w^\times$, and its invariants are $(L_w^\times)^{D_w} = F_v^\times$. The same holds for the units. Taking the restricted product gives $J_L^G = J_F$. The formula for the norm follows from $N_{L_w/F_v}(y) = \prod_{\tau \in D_w} \tau y$ and the decomposition of $G$ into cosets of $D_w$. Now take the invariants of the exact sequence $1 \to L^\times \to J_L \to C_L \to 1$. This gives the exact sequence
$$1 \to F^\times \to J_F \to C_L^G \to H^1(G, L^\times).$$
The last group is trivial by Hilbert's Theorem 90. So $C_L^G = J_F / F^\times = C_F$.

Part 1. Let $M$ be a Galois closure of $L$ over $F$. By part 3 for $M/F$ and for $M/L$, $J_F \cap M^\times = F^\times$ in $J_M$. Since $J_L \to J_M$ is injective, $J_F \cap L^\times \subset J_F \cap M^\times = F^\times$. Part 4 is the transitivity of the local norms. $\square$

### Open subgroups and moduli

The existence theorem describes the open subgroups of finite index of $C_F$. They have a concrete description.

**Definition 7.1.2 (moduli and ray class groups).** A *modulus* of $F$ is a formal product $\mathfrak{m} = \prod_v v^{m_v}$ over the places of $F$, with integers $m_v \ge 0$, almost all $0$, with $m_v \in \{0, 1\}$ at the real places and $m_v = 0$ at the complex places. We write $\mathfrak{m} = \mathfrak{m}_0 \mathfrak{m}_\infty$, where $\mathfrak{m}_0 = \prod_{v \nmid \infty} \mathfrak{p}_v^{m_v}$ is an ideal of $\mathcal{O}_F$ and $\mathfrak{m}_\infty$ is a set of real places. For a place $v$ and an integer $m \ge 0$ let
$$U_v^{(m)} = \begin{cases} \mathcal{O}_v^\times & v \text{ finite}, \ m = 0, \\ 1 + \mathfrak{p}_v^m & v \text{ finite}, \ m \ge 1, \\ F_v^\times & v \text{ infinite}, \ m = 0, \\ \mathbb{R}_{>0} & v \text{ real}, \ m = 1. \end{cases}$$
The *congruence subgroup* of $\mathfrak{m}$ is the open subgroup $W_\mathfrak{m} = \prod_v U_v^{(m_v)}$ of $J_F$. Its image $C_F^\mathfrak{m} = W_\mathfrak{m} F^\times / F^\times$ is an open subgroup of $C_F$. The *ray class group* of $\mathfrak{m}$ is $\mathrm{Cl}_\mathfrak{m} = C_F / C_F^\mathfrak{m}$.

For $\mathfrak{m} = 1$ we have $W_1 = U_F$, and $\mathrm{Cl}_1 = \mathrm{Cl}_F$ by Theorem 3.4.7 of Volume 1. If $\mathfrak{m} \mid \mathfrak{n}$, that is $m_v \le n_v$ for all $v$, then $W_\mathfrak{n} \subset W_\mathfrak{m}$, and $\mathrm{Cl}_\mathfrak{n}$ maps onto $\mathrm{Cl}_\mathfrak{m}$.

**Proposition 7.1.3 (open subgroups of finite index).**
1. Each open subgroup of finite index of $C_F$ contains $C_F^\mathfrak{m}$ for some modulus $\mathfrak{m}$.
2. Each ray class group is finite.
3. Let $D_F$ be the intersection of all the open subgroups of finite index of $C_F$. Then $D_F$ is the closure of the image of $\prod_{v \mid \infty} (F_v^\times)^0$, where $(F_v^\times)^0$ is $\mathbb{R}_{>0}$ or $\mathbb{C}^\times$. It is the connected component of $1$ in $C_F$, and $C_F / D_F$ is a profinite group.

Lean: not stated yet

*Proof.* Part 1. Let $U \subset C_F$ be open of index $n$, and let $U'$ be its preimage in $J_F$. Then $U'$ is open, and it contains $x^n$ for every $x \in J_F$, since $J_F / U'$ has order $n$. By the definition of the topology, $U'$ contains a set $\prod_{v \in S} V_v \times \prod_{v \notin S} \mathcal{O}_v^\times$, with $S$ finite and $V_v$ a neighbourhood of $1$ in $F_v^\times$. At a finite $v \in S$ the neighbourhood $V_v$ contains $1 + \mathfrak{p}_v^{m_v}$ for some $m_v \ge 1$. At an infinite place every element of $(F_v^\times)^0$ is an $n$-th power, so $(F_v^\times)^0 \subset U'$. These subgroups generate $W_\mathfrak{m}$ for the modulus $\mathfrak{m}$ with these $m_v$ and with all the real places in $\mathfrak{m}_\infty$. So $W_\mathfrak{m} \subset U'$.

Part 2. The group $\mathrm{Cl}_\mathfrak{m}$ maps onto $C_F / C_F^1 = \mathrm{Cl}_F$, which is finite (Corollary 3.5.3 of Volume 1). The kernel is a quotient of $W_1 / W_\mathfrak{m} = \prod_{v \mid \mathfrak{m}_0} \mathcal{O}_v^\times / (1 + \mathfrak{p}_v^{m_v}) \times \prod_{v \in \mathfrak{m}_\infty} \{\pm 1\}$, which is finite.

Part 3. Let $D'$ be the closure of the image of $W_\infty^0 = \prod_{v \mid \infty} (F_v^\times)^0$. Every $W_\mathfrak{m}$ contains $W_\infty^0$, and every open subgroup is closed, so $D' \subset D_F$ by part 1. The group $D'$ is connected, as the closure of the image of a connected group. The group $J_F / W_\infty^0$ is the product of the finite group $\prod_{v \mid \infty} \pi_0(F_v^\times)$ and the group of finite ideles. So it is a locally compact group with a basis of neighbourhoods of $1$ formed by compact open subgroups. The quotient $Q = C_F / D'$ is the quotient of this group by the closed image of $F^\times$. Such a quotient again has a basis of neighbourhoods of $1$ formed by open subgroups, so $Q$ is totally disconnected. It is compact, because $D'$ contains the image of $\mathbb{R}_{>0}$ under the section of Proposition 3.4.6 of Volume 1, and so $C_F^1$ maps onto $Q$. A compact totally disconnected group is profinite, so the open subgroups of finite index of $Q$ have intersection $1$. Their preimages are open subgroups of finite index of $C_F$. Thus $D_F \subset D'$. Since $D'$ is connected and $C_F / D'$ is totally disconnected, $D'$ is the connected component of $1$. $\square$

For a description of $D_F$ as a group, see [CF67], Chapter IX, and [Neu99], Chapter VI. For instance $D_\mathbb{Q} = \mathbb{R}_{>0}$, and $C_\mathbb{Q} / D_\mathbb{Q} \cong \hat{\mathbb{Z}}^\times$. For an imaginary quadratic field, $D_F$ is the image of $\mathbb{C}^\times$, and the map $\mathbb{C}^\times \to D_F$ is an isomorphism. If $F$ has a unit of infinite order, $D_F$ is not the image of $W_\infty^0$: it contains solenoids, the closures of the images of the unit group.

### Ray class groups as groups of ideals

Let $\mathfrak{m}$ be a modulus. Let $I^\mathfrak{m}$ be the group of fractional ideals prime to $\mathfrak{m}_0$. For $a \in F^\times$ write $a \equiv 1 \bmod^\times \mathfrak{m}$ if $a \in U_v^{(m_v)}$ for every $v \mid \mathfrak{m}$. This means that $v_\mathfrak{p}(a - 1) \ge m_\mathfrak{p}$ for $\mathfrak{p} \mid \mathfrak{m}_0$ and that $a$ is positive at the real places in $\mathfrak{m}_\infty$. Let $F_{\mathfrak{m},1}$ be the group of these $a$, and $P_{\mathfrak{m},1} = \{a \mathcal{O}_F : a \in F_{\mathfrak{m},1}\}$, the *ray modulo* $\mathfrak{m}$.

**Proposition 7.1.4 (ray class groups and ideals).** The map $\iota$ induces an isomorphism $\mathrm{Cl}_\mathfrak{m} \cong I^\mathfrak{m} / P_{\mathfrak{m},1}$. There is an exact sequence
$$1 \to \mathcal{O}_F^\times / \mathcal{O}_{\mathfrak{m},1}^\times \to (\mathcal{O}_F / \mathfrak{m}_0)^\times \times \{\pm 1\}^{\mathfrak{m}_\infty} \to \mathrm{Cl}_\mathfrak{m} \to \mathrm{Cl}_F \to 1,$$
where $\mathcal{O}_{\mathfrak{m},1}^\times = \mathcal{O}_F^\times \cap F_{\mathfrak{m},1}$. In particular $|\mathrm{Cl}_\mathfrak{m}| = h_F \, \varphi(\mathfrak{m}_0) \, 2^{|\mathfrak{m}_\infty|} / [\mathcal{O}_F^\times : \mathcal{O}_{\mathfrak{m},1}^\times]$, with $\varphi(\mathfrak{m}_0) = |(\mathcal{O}_F / \mathfrak{m}_0)^\times|$.

Lean: not stated yet

*Proof.* Let $J_F^\mathfrak{m}$ be the group of ideles $x$ with $x_v \in U_v^{(m_v)}$ for all $v \mid \mathfrak{m}$. By weak approximation, for every $x \in J_F$ there is $a \in F^\times$ with $a x_v \in U_v^{(m_v)}$ for the finitely many $v \mid \mathfrak{m}$. So $J_F = F^\times J_F^\mathfrak{m}$, and $F^\times \cap J_F^\mathfrak{m} = F_{\mathfrak{m},1}$. Thus
$$\mathrm{Cl}_\mathfrak{m} = J_F / F^\times W_\mathfrak{m} \cong J_F^\mathfrak{m} / F_{\mathfrak{m},1} W_\mathfrak{m}.$$
The map $\iota : J_F^\mathfrak{m} \to I^\mathfrak{m}$ is surjective, and its kernel is the set of $x \in J_F^\mathfrak{m}$ that are units at all finite places. This kernel is $W_\mathfrak{m}$. Since $\iota(F_{\mathfrak{m},1}) = P_{\mathfrak{m},1}$, we get $\mathrm{Cl}_\mathfrak{m} \cong I^\mathfrak{m} / P_{\mathfrak{m},1}$. For the exact sequence, the kernel of $\mathrm{Cl}_\mathfrak{m} \to \mathrm{Cl}_F$ is the image of $U_F = W_1$, which is $W_1 / W_\mathfrak{m} (W_1 \cap F^\times) = W_1 / W_\mathfrak{m} \mathcal{O}_F^\times$. The group $W_1 / W_\mathfrak{m}$ is $(\mathcal{O}_F / \mathfrak{m}_0)^\times \times \{\pm 1\}^{\mathfrak{m}_\infty}$, and $\mathcal{O}_F^\times$ maps to it with kernel $\mathcal{O}_{\mathfrak{m},1}^\times$. $\square$

**Example 7.1.5 (the ray class groups of $\mathbb{Q}$).** Let $N \ge 1$, and let $\infty$ be the real place of $\mathbb{Q}$. By Example 3.4.8 of Volume 1, $C_\mathbb{Q} \cong \mathbb{R}_{>0} \times \hat{\mathbb{Z}}^\times$, and the image of $W_{N\infty}$ in this group is $\mathbb{R}_{>0} \times \{u \in \hat{\mathbb{Z}}^\times : u \equiv 1 \bmod N\}$. So
$$\mathrm{Cl}_{N\infty} \cong \hat{\mathbb{Z}}^\times / (1 + N \hat{\mathbb{Z}}) \cong (\mathbb{Z}/N\mathbb{Z})^\times.$$
In terms of ideals, the class of $(a)$ with $a > 0$ and $\gcd(a, N) = 1$ goes to $a \bmod N$. For the modulus $N$ without $\infty$ the element $-1$ becomes trivial, and $\mathrm{Cl}_N \cong (\mathbb{Z}/N\mathbb{Z})^\times / \{\pm 1\}$. Proposition 7.1.4 gives the same orders. Here $h_\mathbb{Q} = 1$ and $\mathcal{O}^\times = \{\pm 1\}$. The unit $-1$ is never $\equiv 1 \bmod^\times N\infty$, because it is negative, so $|\mathrm{Cl}_{N\infty}| = 2 \varphi(N) / 2 = \varphi(N)$. For $N > 2$ it is not $\equiv 1 \bmod^\times N$ either, so $|\mathrm{Cl}_N| = \varphi(N)/2$.

**Example 7.1.6 (the narrow class group).** Let $\mathfrak{m}_\infty$ be the set of all real places, and $\mathfrak{m}_0 = 1$. The group $\mathrm{Cl}_F^+ = \mathrm{Cl}_{\mathfrak{m}_\infty}$ is the *narrow class group*: fractional ideals modulo principal ideals with a totally positive generator. The exact sequence gives $|\mathrm{Cl}_F^+| = h_F \, 2^{r_1} / [\mathcal{O}_F^\times : \mathcal{O}_F^{\times, +}]$. For $F = \mathbb{Q}(\sqrt 3)$ we have $h_F = 1$. The fundamental unit $2 + \sqrt 3$ is totally positive, and $-1$ is not. So $[\mathcal{O}_F^\times : \mathcal{O}_F^{\times,+}] = 2$ and $|\mathrm{Cl}_F^+| = 2$. The ideal $(\sqrt 3)$ has no totally positive generator, since all its generators are $\pm \sqrt 3 \, \varepsilon$ with $\varepsilon$ a unit, and $N(\pm \sqrt 3 \, \varepsilon) = -3$.
