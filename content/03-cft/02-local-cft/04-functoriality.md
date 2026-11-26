---
title: Functoriality
nodes: []
sources: [Ser67, Mil20, Tat79]
status: checked
drafted_by: writer
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## Functoriality

Let $L$ be a finite separable extension of $K$ in $\bar K$. Then $L$ is a local field, and it has its own reciprocity map $\mathrm{rec}_L : L^\times \to W_L^{ab}$. By Exercise 7 of Chapter 1, $W_L = W_K \cap G_L$ is an open subgroup of $W_K$ of index $[L : K]$. This section compares $\mathrm{rec}_L$ with $\mathrm{rec}_K$. There are two maps between $L^\times$ and $K^\times$, the norm and the inclusion. There are also two maps between $W_L^{ab}$ and $W_K^{ab}$: the map induced by the inclusion $W_L \subset W_K$, and the transfer.

**Definition 2.4.1 (transfer).** Let $G$ be a group and $H$ a subgroup of finite index $n$. Choose representatives $s_1, \dots, s_n$ of the left cosets $G / H$. For $g \in G$ and each $i$ there is a unique $j$ with $g s_i = s_j h_i(g)$ and $h_i(g) \in H$. The *transfer* is the map $\mathrm{Ver} : G^{ab} \to H^{ab}$ that sends the class of $g$ to the class of $h_1(g) h_2(g) \cdots h_n(g)$.

The transfer is a homomorphism, and it does not depend on the choice of the representatives. A proof is in [Ser79], Chapter VII, or in any text on group theory. For the Weil groups, $\mathrm{Ver}$ is continuous and defines a homomorphism $W_K^{ab} \to W_L^{ab}$ of topological groups. The composite of the transfer with the map $H^{ab} \to G^{ab}$ induced by the inclusion is the map $g \mapsto g^n$.

**Theorem 2.4.2 (functoriality).** Let $L$ be a finite separable extension of $K$. Let $j : W_L^{ab} \to W_K^{ab}$ be induced by the inclusion, and let $\mathrm{Ver} : W_K^{ab} \to W_L^{ab}$ be the transfer.
1. For all $y \in L^\times$ one has $\mathrm{rec}_K(N_{L/K}(y)) = j(\mathrm{rec}_L(y))$.
2. For all $x \in K^\times$ one has $\mathrm{rec}_L(x) = \mathrm{Ver}(\mathrm{rec}_K(x))$.
3. For all $\sigma \in W_K$ and $y \in L^\times$ one has $\mathrm{rec}_{\sigma L}(\sigma(y)) = \sigma \, \mathrm{rec}_L(y) \, \sigma^{-1}$.

Lean: not stated yet

The formulas do not depend on the normalization. If $\mathrm{rec}$ is replaced by $x \mapsto \mathrm{rec}(x^{-1})$ on both sides, each formula stays true, because the norm, the inclusion, the transfer and the conjugation are homomorphisms.

*Proof of part 3.* The conjugation by $\sigma$ maps $W_L$ onto $W_{\sigma L}$. Let $\mathrm{rec}'(z) = \sigma^{-1} \, \mathrm{rec}_{\sigma L}(\sigma(z)) \, \sigma$ for $z \in L^\times$. This is an isomorphism of topological groups $L^\times \to W_L^{ab}$. The map $\sigma$ sends uniformizers of $L$ to uniformizers of $\sigma L$, abelian extensions $M$ of $L$ to abelian extensions $\sigma M$ of $\sigma L$, and norm groups to norm groups, since $N_{\sigma M / \sigma L}(\sigma(z)) = \sigma(N_{M/L}(z))$. The conjugate of a geometric Frobenius of $\sigma L$ by $\sigma^{-1}$ is a geometric Frobenius of $L$, because $\mathrm{Gal}(\bar k / k)$ is abelian. Thus $\mathrm{rec}'$ has properties 1 and 2 of Theorem 2.3.3 for $L$. By uniqueness, $\mathrm{rec}' = \mathrm{rec}_L$. $\square$

Parts 1 and 2 are proved with the cohomological construction. In Remark 2.1.4, the norm corresponds to the corestriction on $\hat H^0$ and the inclusion $j$ to the corestriction on $\hat H^{-2}$. The inclusion $K^\times \to L^\times$ corresponds to the restriction on $\hat H^0$, and the transfer to the restriction on $\hat H^{-2}$. The fundamental classes are compatible with restriction, and the cup product is compatible with restriction and corestriction. The details are in [Ser67], Section 2, and in [Mil20], Chapter III.

Here is the finite form of part 1, which is often used.

**Corollary 2.4.3 (towers).** Let $K \subset L \subset M$, where $M$ is a finite abelian extension of $K$. For $y \in L^\times$, the element $r_{M/L}(y) \in \mathrm{Gal}(M/L)$ equals $r_{M/K}(N_{L/K}(y))$. In particular $r_{M/K}(N_{L/K}(L^\times)) = \mathrm{Gal}(M/L)$, and
$$N_{L/K}(L^\times) = \{x \in K^\times : r_{M/K}(x) \in \mathrm{Gal}(M/L)\}.$$

Lean: not stated yet

*Proof.* Restrict both sides of part 1 of Theorem 2.4.2 to $M$. The restriction of $j(w)$ to $M$ is the restriction of $w$ to $M$, viewed as an element of $\mathrm{Gal}(M/K)$. This gives the first claim. The map $r_{M/L}$ is surjective onto $\mathrm{Gal}(M/L)$, so the image of $N_{L/K}(L^\times)$ is $\mathrm{Gal}(M/L)$. The fixed field of $\mathrm{Gal}(M/L)$ is $L$, so the set on the right is the kernel of $r_{L/K}$, which is $N_{L/K}(L^\times)$. $\square$

**Example 2.4.4 (the unramified case).** Let $L = K_n$. The formulas of Theorem 2.4.2 can be checked after projection to the maximal unramified quotients. The degree map of $W_K$ restricts on $W_L$ to $n$ times the degree map of $W_L$, because the residue field of $L$ has $q^n$ elements. For part 1, let $y \in L^\times$. Then $d_K(j(\mathrm{rec}_L(y))) = n \, d_L(\mathrm{rec}_L(y)) = -n \, v_L(y)$, and $d_K(\mathrm{rec}_K(N_{L/K}(y))) = -v_K(N_{L/K}(y)) = -n \, v_L(y)$. For part 2, the group $W_L$ is normal in $W_K$ with cyclic quotient of order $n$, and the powers $1, \Phi, \dots, \Phi^{n-1}$ of a geometric Frobenius $\Phi$ of $K$ are representatives of the cosets. The definition gives $\Phi \cdot \Phi^i = \Phi^{i+1}$ for $i < n - 1$ and $\Phi \cdot \Phi^{n-1} = 1 \cdot \Phi^n$. Thus $\mathrm{Ver}(\Phi) = \Phi^n$. The element $\Phi^n$ acts on $\bar k$ as $x \mapsto x^{q^{-n}}$, so it is a geometric Frobenius of $L$. The uniformizer $\varpi$ of $K$ is also a uniformizer of $L$, so $\mathrm{rec}_L(\varpi)$ is the class of a geometric Frobenius of $L$. Thus both sides of part 2 for $x = \varpi$ have degree $-1$ in $W_L$.

**Remark 2.4.5 (a consistency check).** Parts 1 and 2 agree with each other. For $x \in K^\times$, part 2 and the relation $j \circ \mathrm{Ver} = (g \mapsto g^n)$ give $j(\mathrm{rec}_L(x)) = \mathrm{rec}_K(x)^n$. Part 1 gives $j(\mathrm{rec}_L(x)) = \mathrm{rec}_K(N_{L/K}(x)) = \mathrm{rec}_K(x^n)$. The two results are equal.

Part 1 shows that the image of $W_L$ in $W_K^{ab}$ is $\mathrm{rec}_K(N_{L/K}(L^\times))$. In the language of the Langlands program, part 1 says that the restriction of a character of $W_K$ to $W_L$ corresponds to the composite of a character of $K^\times$ with the norm. Chapter 4 uses this fact for base change of characters and for induced tori.
