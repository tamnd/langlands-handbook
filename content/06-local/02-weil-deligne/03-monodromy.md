---
title: The monodromy theorem
nodes: []
sources: [Tat79, Ser79]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## The monodromy theorem

The Galois representations of arithmetic geometry are $\ell$-adic: they are continuous homomorphisms $G_K \to GL_n(E)$ for a finite extension $E$ of $\mathbb{Q}_\ell$. When $\ell \ne p$, Grothendieck's monodromy theorem says that inertia acts on such a representation through unipotent matrices on an open subgroup, and that the logarithm of this action is a nilpotent $N$ that Frobenius scales by $q^{-1}$. This section proves the theorem and uses it to turn each $\ell$-adic representation into a Weil-Deligne representation. The construction is an equivalence of categories, and the Weil-Deligne representation no longer sees the $\ell$-adic topology. The example is again the Tate curve, whose Tate module gives $\mathrm{Sp}(2)$. The theorem is due to Grothendieck. It appears in the appendix of Serre and Tate, "Good reduction of abelian varieties" (Annals of Math. 88, 1968), and in [Tat79, Section 4]. Throughout this section $\ell$ is a prime different from $p$.

### The theorem of Grothendieck

**Definition 2.3.1 ($\ell$-adic representation).** Let $E$ be a finite extension of $\mathbb{Q}_\ell$. An *$\ell$-adic representation* of $W_K$ is a continuous homomorphism $\rho : W_K \to GL(V)$, where $V$ is a vector space of finite dimension over $E$ with its $\ell$-adic topology. An $\ell$-adic representation of $G_K$ is defined in the same way.

Lean: not stated yet

The group $GL(V)$ now has small subgroups, such as $1 + \lambda^k \mathrm{End}(T)$ for a lattice $T$ and a uniformizer $\lambda$ of $E$. So Proposition 2.1.10 fails, and the image of inertia can be infinite. The point of the monodromy theorem is that the infinite part of $\rho(I_K)$ is very small: it is a quotient of $\mathbb{Z}_\ell$, and it acts unipotently. Recall the tame character $t_\ell : I_K \to \mathbb{Z}_\ell$ of Definition 2.1.7, for a fixed generator of $\mathbb{Z}_\ell(1)$. For a nilpotent $N$ and $t \in \mathbb{Z}_\ell$ the series $\exp(tN) = \sum_{j \ge 0} t^j N^j / j!$ is a finite sum, and it is continuous in $t$.

**Theorem 2.3.2 (Grothendieck's monodromy theorem).** Let $\rho : W_K \to GL(V)$ be an $\ell$-adic representation. There are an open subgroup $H$ of $I_K$ and a unique nilpotent $N \in \mathrm{End}(V)$ such that
$$\rho(\sigma) = \exp(t_\ell(\sigma) N) \quad \text{for all } \sigma \in H.$$
The endomorphism $N$ does not depend on $H$, and it satisfies $\rho(w) N \rho(w)^{-1} = \|w\| \, N$ for all $w \in W_K$.

Lean: not stated yet

*Proof.* Let $\mathcal{O}_E$ be the ring of integers of $E$ and $\lambda$ a uniformizer. First we find a lattice stable under inertia. Let $T_0$ be any $\mathcal{O}_E$-lattice in $V$. Its stabilizer in $GL(V)$ is open, so its stabilizer $J$ in $I_K$ is open and has finite index. Then $T = \sum_{\sigma \in I_K / J} \rho(\sigma) T_0$ is a lattice stable under $\rho(I_K)$. Let $\Gamma = 1 + \lambda \mathrm{End}_{\mathcal{O}_E}(T)$. It is a pro-$\ell$ group, since the quotients $(1 + \lambda^j \mathrm{End}(T)) / (1 + \lambda^{j+1} \mathrm{End}(T))$ for $j \ge 1$ are isomorphic to the additive group of $\mathrm{End}(T / \lambda T)$, which is an $\ell$-group. It is normalized by $\rho(I_K)$. So $H_1 = I_K \cap \rho^{-1}(\Gamma)$ is an open normal subgroup of $I_K$. By Lemma 2.1.8, part 3, there are $a \ge 0$ and a continuous homomorphism $u : \ell^a \mathbb{Z}_\ell \to \Gamma$ with $t_\ell(H_1) = \ell^a \mathbb{Z}_\ell$ and $\rho(\sigma) = u(t_\ell(\sigma))$ for $\sigma \in H_1$.

Next we show that the eigenvalues of $g = u(\ell^a)$ are roots of unity. Let $e = [I_K : H_1]$, so that $x^e \in H_1$ for each $x \in I_K$. Choose $\sigma_1 \in H_1$ with $t_\ell(\sigma_1) = \ell^a$, and let $x = \Phi^{-1} \sigma_1 \Phi \in I_K$. By Lemma 2.1.8, part 2, $t_\ell(x) = \|\Phi^{-1}\| \ell^a = q \ell^a$, so $t_\ell(x^e) = e q \ell^a$, and $\rho(x^e) = u(eq\ell^a) = g^{eq}$. On the other hand $\rho(x^e) = \rho(\Phi)^{-1} g^e \rho(\Phi)$. So $g^e$ and $g^{eq}$ are conjugate. The finite set of eigenvalues of $g^e$, in an algebraic closure of $E$, is therefore stable under $\alpha \mapsto \alpha^q$. So each eigenvalue $\alpha$ satisfies $\alpha^{q^k} = \alpha$ for some $k \ge 1$, and it is a root of unity. Choose $M \ge 1$ such that $h = g^{eM}$ has all its eigenvalues equal to $1$. Then $h$ is unipotent.

Now let $b = eM\ell^a$ and $H = H_1 \cap t_\ell^{-1}(b \mathbb{Z}_\ell)$, an open subgroup of $I_K$. Put $N = b^{-1} \log h$, which is nilpotent. The two maps $c \mapsto u(bc)$ and $c \mapsto \exp(cbN) = \exp(c \log h)$ are continuous homomorphisms $\mathbb{Z}_\ell \to GL(V)$. They agree on $\mathbb{Z}$, since both send $1$ to $h$, and $\mathbb{Z}$ is dense in $\mathbb{Z}_\ell$. So they are equal. For $\sigma \in H$ write $t_\ell(\sigma) = bc$. Then $\rho(\sigma) = u(bc) = \exp(t_\ell(\sigma) N)$.

For the uniqueness, suppose that $(H', N')$ is another such pair. The group $t_\ell(H \cap H')$ is open in $\mathbb{Z}_\ell$, so it contains some $t \ne 0$. Then $\exp(tN) = \exp(tN')$, and taking logarithms of these unipotent elements gives $N = N'$. Finally let $w \in W_K$. Conjugation by $w$ is a homeomorphism of $I_K$, so $H \cap w^{-1} H w$ is open in $I_K$. Choose $\sigma$ in it with $t = t_\ell(\sigma) \ne 0$. By Lemma 2.1.8, part 2,
$$\exp(\|w\| t N) = \rho(w \sigma w^{-1}) = \rho(w) \exp(tN) \rho(w)^{-1} = \exp\big(t \, \rho(w) N \rho(w)^{-1}\big).$$
Taking logarithms and dividing by $t$ gives the relation. $\square$

The proof uses only two facts about $K$: the tame quotient of $I_K$ has pro-$\ell$ part $\mathbb{Z}_\ell(1)$, and Frobenius acts on it by a power different from $1$. This explains the hypothesis $\ell \ne p$. The endomorphism $N$ is the *monodromy operator* of $\rho$. The name comes from geometry: for a family of varieties over a disc, $N$ is the logarithm of the monodromy around the special fibre.

**Corollary 2.3.3 (quasi-unipotence).** Let $\rho$ be an $\ell$-adic representation of $W_K$. There is an open subgroup $H$ of $I_K$ such that $\rho(\sigma)$ is unipotent for each $\sigma \in H$. The image $\rho(I_K)$ is finite if and only if $N = 0$.

Lean: not stated yet

*Proof.* The first claim is Theorem 2.3.2, since $\exp(tN)$ is unipotent. The second claim is Exercise 5. $\square$

### The Weil-Deligne representation of an $\ell$-adic representation

Fix a geometric Frobenius $\Phi$ and a generator of $\mathbb{Z}_\ell(1)$. Each $w \in W_K$ is $w = \Phi^m \sigma$ with $m \in \mathbb{Z}$ and $\sigma \in I_K$, in a unique way. A Weil-Deligne representation over a field $\Omega$ of characteristic $0$ is defined as in Definition 2.2.1, with $r$ a homomorphism with open kernel and $\Omega$ in place of $\mathbb{C}$. Proposition 2.1.10 shows that over $\mathbb{C}$ this is the same as Definition 2.2.1.

**Theorem 2.3.4 (the Weil-Deligne representation of $\rho$).** Let $\rho : W_K \to GL(V)$ be an $\ell$-adic representation, and let $N$ be its monodromy operator. Define
$$r(\Phi^m \sigma) = \rho(\Phi^m \sigma) \exp(-t_\ell(\sigma) N).$$
1. The map $r$ is a homomorphism $W_K \to GL(V)$ with open kernel, and $(r, N)$ is a Weil-Deligne representation over $E$.
2. If $\Phi$ is replaced by $\Phi' = \Phi \sigma_0$, the new representation is $r' = \exp(xN) \, r \, \exp(-xN)$ with $x = t_\ell(\sigma_0) / (q - 1)$. So $(r', N) \cong (r, N)$.
3. If the generator of $\mathbb{Z}_\ell(1)$ is multiplied by $c^{-1}$ with $c \in \mathbb{Z}_\ell^\times$, the new pair is $(r, cN)$. It is isomorphic to $(r, N)$ over an algebraic closure of $E$.
4. The functor $\rho \mapsto (r, N)$ is an equivalence between the category of $\ell$-adic representations of $W_K$ over $E$ and the category of Weil-Deligne representations over $E$. The inverse is $(r, N) \mapsto \rho$ with $\rho(\Phi^m \sigma) = r(\Phi^m \sigma) \exp(t_\ell(\sigma) N)$.

Lean: not stated yet

*Proof.* For part 1, let $w = \Phi^m \sigma$ and $w' = \Phi^{m'} \sigma'$. Then $w w' = \Phi^{m + m'} (\Phi^{-m'} \sigma \Phi^{m'}) \sigma'$, and by Lemma 2.1.8 the inertia part has $t_\ell = q^{m'} t_\ell(\sigma) + t_\ell(\sigma')$. Write $t = t_\ell(\sigma)$ and $t' = t_\ell(\sigma')$. The relation of Theorem 2.3.2 gives $\rho(w') \exp(-q^{m'} t N) \rho(w')^{-1} = \exp(-tN)$, since $\|w'\| = q^{-m'}$. Hence
$$r(ww') = \rho(w) \rho(w') \exp(-q^{m'} t N) \exp(-t'N) = \rho(w) \exp(-tN) \rho(w') \exp(-t'N) = r(w) r(w').$$
The kernel of $r$ contains the open subgroup $H$ of Theorem 2.3.2. Since $\exp(tN)$ commutes with $N$, we have $r(w) N r(w)^{-1} = \rho(w) N \rho(w)^{-1} = \|w\| N$.

For part 2, note that $r'$ and $r$ agree on $I_K$, and that $\exp(xN)$ commutes with $r(I_K)$. So it suffices to compare the two homomorphisms on $\Phi'$, since $\Phi'$ and $I_K$ generate $W_K$. We have $r'(\Phi') = \rho(\Phi') = r(\Phi) r(\sigma_0) \exp(t_0 N)$ with $t_0 = t_\ell(\sigma_0)$. From $r(\Phi)^{-1} N r(\Phi) = qN$ we get $\exp(xN) r(\Phi) = r(\Phi) \exp(qxN)$, so
$$\exp(xN) \, r(\Phi') \, \exp(-xN) = r(\Phi) \exp(qxN) r(\sigma_0) \exp(-xN) = r(\Phi) r(\sigma_0) \exp\big((q - 1) x N\big).$$
This is $r'(\Phi')$ for $x = t_0 / (q - 1)$. The element $\exp(xN)$ commutes with $N$, so it is an isomorphism $(r, N) \to (r', N)$.

For part 3, the new tame character is $c^{-1} t_\ell$, the new monodromy operator is $cN$ by uniqueness, and the product $\exp(-t_\ell(\sigma) N)$ does not change. Exercise 4 constructs an isomorphism $(r, N) \cong (r, cN)$.

For part 4, the computation of part 1, read backwards, shows that the inverse formula defines a homomorphism. It is continuous, because it is continuous on the open subgroup $I_K$. The two constructions are inverse to each other, because the monodromy operator of the inverse $\rho$ is $N$, by the uniqueness in Theorem 2.3.2. Let $f : V \to V'$ be a morphism of $\ell$-adic representations. For $\sigma$ in a small open subgroup and $t = t_\ell(\sigma) \ne 0$ we have $f \exp(tN) = \exp(tN') f$. The logarithm of a unipotent $g$ is a fixed polynomial in $g - 1$, so $f N = N' f$. Then $f$ commutes with $r$ and $r'$. Conversely, a linear map that commutes with $r$ and $N$ commutes with $\rho$. So the functor is fully faithful, and the inverse formula shows that it is essentially surjective. $\square$

**Remark 2.3.5 (representations of $G_K$).** An $\ell$-adic representation of $G_K$ restricts to one of $W_K$. By Proposition 2.1.3 the restriction is fully faithful, since a linear map that commutes with $\rho(W_K)$ commutes with its closure $\rho(G_K)$. So each $\ell$-adic representation of $G_K$ has a Weil-Deligne representation. Not every $\ell$-adic representation of $W_K$ comes from $G_K$. The group $\rho(G_K)$ is compact, so it stabilizes a lattice, and the eigenvalues of $\rho(\Phi)$ are units of the ring of integers of an algebraic closure of $E$. Exercise 2 gives an example where this fails, and it shows that over $E$, unlike over $\mathbb{C}$, a representation of $W_K$ with a unipotent Frobenius can extend to $G_K$.

**Remark 2.3.6 (from $\bar{\mathbb{Q}}_\ell$ to $\mathbb{C}$).** Choose a field isomorphism $\iota : \bar{\mathbb{Q}}_\ell \to \mathbb{C}$. It is not continuous, but this does not matter: the representation $r$ has open kernel, and a Weil-Deligne representation over $\bar{\mathbb{Q}}_\ell$ is a purely algebraic object. So $\iota$ carries it to a complex Weil-Deligne representation $\iota \mathrm{WD}(\rho)$. In general the result depends on $\iota$. For the representations that come from geometry, the characteristic polynomials of the $r(w)$ often have coefficients in $\mathbb{Q}$, and then the Frobenius-semisimplification of $\iota \mathrm{WD}(\rho)$ does not depend on $\iota$ or on $\ell$. For the cohomology of a variety with good reduction this follows from the Weil conjectures. For semistable reduction and $N$ it is a conjecture in general. In this way one compares the restriction to $G_K$ of a global $\ell$-adic Galois representation with the local component of an automorphic representation, through $\iota$ and the local Langlands correspondence of Chapter 3. This is the setting of [HT01].

### Examples

**Example 2.3.7 (the Tate curve).** Let $E_q$ be the Tate curve over $K$ with parameter $q_E \in K^\times$, $v(q_E) > 0$. So $E_q(\bar K) \cong \bar K^\times / q_E^{\mathbb{Z}}$ as $G_K$-modules (Volume 0, Example 3.1.5). The $\ell^n$-torsion is generated by the classes of $\zeta_{\ell^n}$ and $Q_n$, where $(\zeta_{\ell^n})$ is our generator of $\mathbb{Z}_\ell(1)$ and $Q_n$ is a root of $X^{\ell^n} = q_E$ with $Q_{n+1}^\ell = Q_n$. Let $e_1$ and $e_2$ be the corresponding elements of the Tate module $T_\ell(E_q)$, and $V = T_\ell(E_q) \otimes \mathbb{Q}_\ell$. Write $q_E = u \varpi^{v}$ with $u \in \mathcal{O}_K^\times$ and $v = v(q_E)$. Choose compatible roots $\varpi^{1/\ell^n}$ and $u^{1/\ell^n}$, and take $Q_n = u^{1/\ell^n} (\varpi^{1/\ell^n})^v$. For $\sigma \in I_K$ the root $u^{1/\ell^n}$ lies in $K^{ur}$ and is fixed, so $\sigma(Q_n) = t_{\ell^n}(\sigma)^v Q_n$. In additive notation on $V$ this reads
$$\rho(\sigma) e_1 = e_1, \qquad \rho(\sigma) e_2 = e_2 + v \, t_\ell(\sigma) \, e_1.$$
So $\rho(\sigma) = \exp(t_\ell(\sigma) N)$ on all of $I_K$, with $N e_1 = 0$ and $N e_2 = v e_1$. The Frobenius acts by $\rho(\Phi) e_1 = \chi_\ell(\Phi) e_1 = q^{-1} e_1$ and $\rho(\Phi) e_2 = e_2 + c e_1$ for some $c \in \mathbb{Q}_\ell$, since $\Phi(Q_n)/Q_n$ is a root of unity of order dividing $\ell^n$. The Weil-Deligne representation has $r(\sigma) = 1$ for $\sigma \in I_K$ and $r(\Phi) = \rho(\Phi)$. Its eigenvalues are $1$ and $q^{-1}$, so it is semisimple, with eigenvectors $f_0 = e_2 + \frac{c}{1 - q^{-1}} e_1$ and $f_1 = e_1$. Then $N f_0 = v f_1$. In the basis $f_0, v f_1$ we find exactly $\mathrm{Sp}(2)$ of Example 2.2.4. So
$$\mathrm{WD}(V_\ell(E_q)) \cong \mathrm{Sp}(2), \qquad \mathrm{WD}(H^1_{et}(E_q, \mathbb{Q}_\ell)) \cong \mathrm{Sp}(2)^\vee \cong \mathrm{Sp}(2) \otimes \|\cdot\|^{-1},$$
where $H^1 = V^\vee$, and the last isomorphism is Exercise 3. By Example 2.2.11 the representation $\mathrm{Sp}(2) \otimes \|\cdot\|^{-1}$ corresponds to $|\cdot|^{-1/2} \mathrm{St}$, a twist of the Steinberg representation. The power of $|\cdot|$ depends on the normalization that one uses to compare Galois and automorphic representations. With the unitary normalization one gets $\mathrm{St}$ itself. An elliptic curve over $K$ with split multiplicative reduction is a Tate curve, and the computation applies to it. Exercise 6 treats nonsplit multiplicative reduction.

**Example 2.3.8 (potentially good reduction).** Let $A$ be an abelian variety over $K$ and $V = V_\ell(A)$. The criterion of Néron, Ogg and Shafarevich, in the form of Serre and Tate (1968), says that $A$ has good reduction if and only if $V$ is unramified. Then $N = 0$ and $r = \rho|_{W_K}$. For an elliptic curve with good reduction, the arithmetic Frobenius acts on $V$ with characteristic polynomial $X^2 - aX + q$, where $q + 1 - a$ is the number of points of the reduction over $k$. So the geometric Frobenius acts on $H^1 = V^\vee$ with the same characteristic polynomial. Serre and Tate also show that $A$ has potentially good reduction if and only if $\rho(I_K)$ is finite. By Corollary 2.3.3 this means $N = 0$. If $A$ has semistable reduction, then $N^2 = 0$, by the results of Grothendieck in SGA 7, Exposé IX.

**Remark 2.3.9 (the case $\ell = p$).** For $\ell = p$ the monodromy theorem fails: the wild inertia group is pro-$p$, and a representation can have a large image of inertia. An example is the cyclotomic character $\chi_p$ of $\mathbb{Q}_p$, which is infinitely ramified. The replacement is $p$-adic Hodge theory, which is the subject of Volume 12. Fontaine attached a Weil-Deligne representation to each potentially semistable $p$-adic representation, and Berger's $p$-adic monodromy theorem says that each de Rham representation is potentially semistable. For a smooth proper variety over $K$, the Frobenius-semisimple Weil-Deligne representation of $H^i_{et}$ is expected not to depend on $\ell$, including $\ell = p$. The weight-monodromy conjecture of Deligne says how $N$ interacts with the weights of Frobenius. Scholze proved it for complete intersections in toric varieties.
