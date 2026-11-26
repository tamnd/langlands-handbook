---
title: Diagonalizable groups and tori
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Diagonalizable groups and tori

The diagonalizable groups are the groups that are isomorphic to closed subgroups of the diagonal torus $D_n$. They are determined by their characters: the functor $G \mapsto X^*(G)$ is an anti-equivalence between diagonalizable groups and finitely generated abelian groups. The connected smooth ones are the split tori $\mathbb{G}_m^r$. Over a general field, a torus becomes split over the separable closure, and it is determined by its character lattice with the action of the Galois group. The character lattice $X^*(T)$ and the cocharacter lattice $X_*(T)$ are the first half of a root datum, and the exchange of the two lattices is the first step of the construction of the dual group. This section follows [Mil17], Chapter 12, and [Spr98], Chapters 3 and 13.

### Characters

**Definition 1.4.1 (character).** A *character* of an affine group $G$ is a homomorphism $\chi : G \to \mathbb{G}_m$. The characters form an abelian group $X^*(G)$ under pointwise multiplication. We write this group additively when $G$ is a torus.

By Theorem 1.1.4, a character is a Hopf algebra map $k[t, t^{-1}] \to \mathcal{O}(G)$, that is, an element $a = \chi^*(t)$ of $\mathcal{O}(G)$ with
$$\Delta(a) = a \otimes a, \qquad \varepsilon(a) = 1.$$
Such an element is called *group-like*. It is a unit, with inverse $S(a)$, by the antipode identity. So $X^*(G)$ is the set of group-like elements of $\mathcal{O}(G)$, with the multiplication of $\mathcal{O}(G)$. Mathlib has the predicate `IsGroupLikeElem` for this condition.

**Lemma 1.4.2 (Dedekind).** Distinct characters of $G$ are linearly independent in $\mathcal{O}(G)$.

Lean: `linearIndepOn_isGroupLikeElem`, from Mathlib

*Proof.* Suppose not, and choose a relation $\sum_{i=1}^n c_i a_i = 0$ with distinct group-like elements $a_i$, with all $c_i \ne 0$, and with $n$ minimal. Since $\varepsilon(a_1) = 1$, we have $n \ge 2$. Apply $\Delta$ to the relation, and subtract the relation tensored with $a_1$ on the right:
$$\sum_{i=1}^n c_i \, a_i \otimes a_i - \sum_{i=1}^n c_i \, a_i \otimes a_1 = \sum_{i=2}^n c_i \, a_i \otimes (a_i - a_1) = 0.$$
By minimality, $a_2, \dots, a_n$ are linearly independent. So $c_i (a_i - a_1) = 0$ for $i \ge 2$, and $a_2 = a_1$, which is a contradiction. $\square$

**Definition 1.4.3 (the group $D(M)$).** Let $M$ be a finitely generated abelian group. The group algebra $k[M]$, with basis the elements $m \in M$ and with $\Delta(m) = m \otimes m$, $\varepsilon(m) = 1$ and $S(m) = m^{-1}$, is a Hopf algebra. The affine group that it represents is $D(M)$. Its points are $D(M)(R) = \mathrm{Hom}(M, R^\times)$.

Lean: `AddMonoidAlgebra.instHopfAlgebra` and `LaurentPolynomial.instHopfAlgebra`, from Mathlib

**Example 1.4.4 (the first cases).** We have $D(\mathbb{Z}) = \mathbb{G}_m$, $D(\mathbb{Z}/n\mathbb{Z}) = \mu_n$ and $D(\mathbb{Z}^n) = \mathbb{G}_m^n \cong D_n$. Also $D(M \oplus N) = D(M) \times D(N)$. The group-like elements of $k[M]$ are the elements of $M$. Indeed, let $a = \sum_m c_m m$ be group-like. Then $\sum_m c_m \, m \otimes m = \sum_{m, m'} c_m c_{m'} \, m \otimes m'$. So $c_m c_{m'} = 0$ for $m \ne m'$ and $c_m^2 = c_m$, and $\varepsilon(a) = \sum c_m = 1$. Thus exactly one $c_m$ is $1$, and the others are $0$. So $X^*(D(M)) = M$.

### Diagonalizable groups

**Theorem 1.4.5 (diagonalizable groups).** For an algebraic group $G$ over $k$, the following conditions are equivalent:
1. $G$ is isomorphic to $D(M)$ for a finitely generated abelian group $M$;
2. the characters of $G$ form a basis of $\mathcal{O}(G)$;
3. every representation of $G$ is a direct sum of representations of dimension $1$;
4. $G$ is isomorphic to a closed subgroup of $D_n$ for some $n$.

Then $G$ is called *diagonalizable*.

Lean: not stated yet

*Proof.* Condition 1 implies condition 2 by Example 1.4.4. Assume condition 2, and let $\rho : V \to V \otimes \mathcal{O}(G)$ be a comodule. For $v \in V$ write $\rho(v) = \sum_\chi v_\chi \otimes \chi$, a finite sum over $\chi \in X^*(G)$. The first comodule identity gives
$$\sum_\chi \rho(v_\chi) \otimes \chi = \sum_\chi v_\chi \otimes \chi \otimes \chi.$$
Since the $\chi$ are a basis, $\rho(v_\chi) = v_\chi \otimes \chi$. So $v_\chi$ lies in the *weight space* $V_\chi = \{w \in V : \rho(w) = w \otimes \chi\}$, on which $g \in G(R)$ acts by the scalar $\chi(g)$. The counit identity gives $v = \sum_\chi v_\chi$. So $V = \sum_\chi V_\chi$, and the sum is direct because the $\chi$ are linearly independent. Each $V_\chi$ is a direct sum of lines, each of which is a subrepresentation. This gives condition 3. Assume condition 3. By Theorem 1.2.3, $G$ has a faithful finite-dimensional representation, and in a basis of lines it maps $G$ into $D_n$ by a closed embedding. This gives condition 4. Assume condition 4. Then $\mathcal{O}(D_n) = k[\mathbb{Z}^n]$ maps onto $\mathcal{O}(G)$, by a map of Hopf algebras. It sends group-like elements to group-like elements, so the characters of $G$ span $\mathcal{O}(G)$. By Lemma 1.4.2 they form a basis, which is condition 2. Finally assume condition 2, and put $M = X^*(G)$. The inclusion $M \subset \mathcal{O}(G)$ extends to a map $k[M] \to \mathcal{O}(G)$. It is an isomorphism of vector spaces by condition 2, and it respects the products and the comultiplications, so it is an isomorphism of Hopf algebras. Finitely many characters generate the algebra $\mathcal{O}(G)$. They generate a subgroup $M'$ of $M$ with $k[M'] = k[M]$, so $M' = M$, and $M$ is finitely generated. Thus $G \cong D(M)$. $\square$

**Corollary 1.4.6 (anti-equivalence).** The functors $M \mapsto D(M)$ and $G \mapsto X^*(G)$ are inverse anti-equivalences between the category of finitely generated abelian groups and the category of diagonalizable groups over $k$. In particular $\mathrm{Hom}(D(M), D(N)) = \mathrm{Hom}(N, M)$. A sequence $1 \to D(M'') \to D(M) \to D(M') \to 1$ is exact, that is, the first map is a closed embedding onto the kernel of the second, and the second is a quotient map, if and only if $0 \to M' \to M \to M'' \to 0$ is exact.

Lean: not stated yet

*Proof.* A homomorphism $D(M) \to D(N)$ is a Hopf algebra map $k[N] \to k[M]$. It maps the group-like elements $N$ to the group-like elements $M$, by a group homomorphism, and it is determined by this map. Conversely each group homomorphism $N \to M$ extends linearly to a Hopf algebra map. Theorem 1.4.5 shows that each diagonalizable group is of the form $D(M)$. For the exactness, a closed embedding corresponds to a surjection $k[M] \to k[M'']$, that is, to a surjection $M \to M''$. A quotient map corresponds to an injection $k[M'] \to k[M]$, that is, to an injection $M' \to M$. The kernel of $D(M) \to D(M')$ is represented by $k[M]$ modulo the ideal generated by $m' - 1$ for $m' \in M'$, which is $k[M/M']$. $\square$

In particular every closed subgroup and every quotient of a diagonalizable group is diagonalizable. For example, the closed subgroups of $\mathbb{G}_m$ are $\mathbb{G}_m$ and the groups $\mu_n$, which correspond to the quotients $\mathbb{Z}$ and $\mathbb{Z}/n\mathbb{Z}$ of $\mathbb{Z}$.

**Proposition 1.4.7 (smooth and connected diagonalizable groups).** Let $p \ge 0$ be the characteristic of $k$, and let $M$ be a finitely generated abelian group.
1. $D(M)$ is smooth if and only if $p = 0$ or $M$ has no element of order $p$.
2. $D(M)$ is smooth and connected if and only if $M$ is free, that is, if and only if $D(M) \cong \mathbb{G}_m^r$.

Lean: not stated yet

*Proof.* Write $M \cong \mathbb{Z}^r \oplus \bigoplus_i \mathbb{Z}/n_i\mathbb{Z}$, so that $D(M) \cong \mathbb{G}_m^r \times \prod_i \mu_{n_i}$. The coordinate ring is $k[t_1^{\pm 1}, \dots, t_r^{\pm 1}] \otimes \bigotimes_i k[s_i]/(s_i^{n_i} - 1)$. Over $\bar k$ the factor $k[s]/(s^n - 1)$ is reduced if and only if $s^n - 1$ has distinct roots, that is, if and only if $p \nmid n$. This gives part 1. If $p \nmid n$, then $\mu_n$ over $\bar k$ is the constant group with $n$ points, which is not connected for $n > 1$. So if $D(M)$ is smooth and connected, each $n_i$ is $1$ and $M = \mathbb{Z}^r$. The converse holds because $\bar k[t_1^{\pm 1}, \dots, t_r^{\pm 1}]$ is an integral domain. $\square$

In characteristic $p$ the group $\mu_{p^e}$ is connected but not smooth. Its only point in $\bar k$ is $1$.

### Tori

**Definition 1.4.8 (torus).** A *torus* over $k$ is an algebraic group $T$ such that $T_{\bar k} \cong \mathbb{G}_m^r$ over $\bar k$. Then $r$ is its *rank*. It is *split* if $T \cong \mathbb{G}_m^r$ over $k$. The *character group* of $T$ is $X^*(T) = \mathrm{Hom}(T_{k^s}, \mathbb{G}_m)$ and the *cocharacter group* is $X_*(T) = \mathrm{Hom}(\mathbb{G}_m, T_{k^s})$, both computed over $k^s$. The *pairing* $\langle \chi, \lambda \rangle \in \mathbb{Z}$ is defined by $\chi(\lambda(t)) = t^{\langle \chi, \lambda \rangle}$.

The pairing makes sense because $\mathrm{End}(\mathbb{G}_m) = \mathrm{Hom}(\mathbb{Z}, \mathbb{Z}) = \mathbb{Z}$ by Corollary 1.4.6. For $T = \mathbb{G}_m^r$ we have $X^*(T) = \mathbb{Z}^r$, where $\chi = (a_1, \dots, a_r)$ is the character $t \mapsto t_1^{a_1} \cdots t_r^{a_r}$, and $X_*(T) = \mathbb{Z}^r$, where $\lambda = (b_1, \dots, b_r)$ is the cocharacter $s \mapsto (s^{b_1}, \dots, s^{b_r})$. Then $\chi(\lambda(s)) = s^{\sum a_i b_i}$, so the pairing is the standard dot product. Thus $X^*(T)$ and $X_*(T)$ are free of rank $r$, and the pairing between them is perfect, that is, it identifies each lattice with the dual of the other. The Galois group $\Gamma_k$ acts on both lattices by $\sigma \chi = \sigma \circ \chi \circ \sigma^{-1}$, and the pairing is invariant.

**Example 1.4.9 (the tori of $GL_n$, $SL_n$ and $PGL_n$).** Let $e_1, \dots, e_n$ be the standard basis of $X^*(D_n) = \mathbb{Z}^n$, so that $e_i(\mathrm{diag}(t_1, \dots, t_n)) = t_i$, and let $e_1^\vee, \dots, e_n^\vee$ be the dual basis of $X_*(D_n) = \mathbb{Z}^n$, so that $e_i^\vee(s)$ is the diagonal matrix with $s$ in place $i$ and $1$ elsewhere. The diagonal torus $T_1$ of $SL_n$ is the kernel of $\det = e_1 + \dots + e_n$ on $D_n$. By Corollary 1.4.6,
$$X^*(T_1) = \mathbb{Z}^n / \mathbb{Z}(e_1 + \dots + e_n), \qquad X_*(T_1) = \{ \textstyle\sum b_i e_i^\vee : \sum b_i = 0 \}.$$
The diagonal torus $T_2$ of $PGL_n$ is the image $D_n / \mathbb{G}_m$ of $D_n$, where $\mathbb{G}_m$ is embedded by the cocharacter $e_1^\vee + \dots + e_n^\vee$. Its characters are the characters of $D_n$ that are trivial on the scalars, so
$$X^*(T_2) = \{ \textstyle\sum a_i e_i : \sum a_i = 0 \}, \qquad X_*(T_2) = \mathbb{Z}^n / \mathbb{Z}(e_1^\vee + \dots + e_n^\vee).$$
So the character lattice of the torus of $SL_n$ is the cocharacter lattice of the torus of $PGL_n$, and the reverse also holds. Chapter 5 shows that this exchange makes $PGL_n(\mathbb{C})$ the dual group of $SL_n$, and $SL_n(\mathbb{C})$ the dual group of $PGL_n$. The torus $D_n$ of $GL_n$ is self-dual in the same way. The elements $e_i - e_j$ lie in $X^*$ of all three tori, and Example 1.4.14 shows that they are the roots.

**Theorem 1.4.10 (tori and Galois lattices).** Every torus over $k$ splits over a finite separable extension of $k$. The functor $T \mapsto X^*(T)$ is an anti-equivalence between the category of tori over $k$ and the category of free finitely generated abelian groups with a continuous action of $\Gamma_k$, that is, an action through a finite quotient. Under it, $T(k) = \mathrm{Hom}_{\Gamma_k}(X^*(T), (k^s)^\times)$ and $X_*(T)$ is the dual lattice of $X^*(T)$ with the dual action. More generally, the groups of multiplicative type over $k$, the groups that become diagonalizable over $k^s$, correspond to the finitely generated abelian groups with a continuous action of $\Gamma_k$.

Lean: not stated yet

*Outline of the proof.* The first statement is the main point. One shows that a group which is diagonalizable over $\bar k$ is already diagonalizable over $k^s$, because its characters are defined over a finite separable extension ([Mil17], Chapter 12). Then the functor is Galois descent. If $T$ is split by $k^s$, then $\mathcal{O}(T) \otimes k^s = k^s[M]$ with $M = X^*(T)$, and $\Gamma_k$ acts on $k^s[M]$ through both factors. The algebra $\mathcal{O}(T)$ is the ring of invariants $(k^s[M])^{\Gamma_k}$. Conversely each lattice $M$ with a continuous action defines the Hopf algebra $(k^s[M])^{\Gamma_k}$ over $k$. See [Mil17], Chapter 12, and [Spr98], Chapter 13. $\square$

A torus $T$ is *anisotropic* if $X^*(T)^{\Gamma_k} = 0$, that is, if $T$ has no nontrivial character over $k$. The torus $T$ is split if and only if $\Gamma_k$ acts trivially on $X^*(T)$.

**Example 1.4.11 (tori over $\mathbb{R}$).** Here $\Gamma = \mathrm{Gal}(\mathbb{C}/\mathbb{R}) = \{1, c\}$. There are three basic lattices:
1. $\mathbb{Z}$ with the trivial action, which corresponds to $\mathbb{G}_m$, with $\mathbb{G}_m(\mathbb{R}) = \mathbb{R}^\times$;
2. $\mathbb{Z}$ with $c$ acting by $-1$, which corresponds to the circle $S = SO_2$, with $\mathcal{O}(S) = \mathbb{R}[x, y]/(x^2 + y^2 - 1)$ and $S(\mathbb{R}) = \{z \in \mathbb{C} : |z| = 1\}$;
3. $\mathbb{Z}^2$ with $c$ exchanging the two basis vectors, which corresponds to the Weil restriction $R_{\mathbb{C}/\mathbb{R}} \mathbb{G}_m$, the group with $R$-points $(R \otimes_{\mathbb{R}} \mathbb{C})^\times$, with $\mathcal{O} = \mathbb{R}[x, y, 1/(x^2 + y^2)]$ and real points $\mathbb{C}^\times$.

Over $\mathbb{C}$, the circle becomes $\mathbb{G}_m$ by $(x, y) \mapsto x + iy$, with inverse $t \mapsto ((t + t^{-1})/2, (t - t^{-1})/(2i))$. Complex conjugation maps the character $x + iy$ to $x - iy = (x + iy)^{-1}$, so it acts on $X^*(S) = \mathbb{Z}$ by $-1$. Thus $S$ is anisotropic, and $S(\mathbb{R})$ is compact. For $R_{\mathbb{C}/\mathbb{R}} \mathbb{G}_m$, the two characters over $\mathbb{C}$ are $z \mapsto z$ and $z \mapsto \bar z$, and $c$ exchanges them. The invariant character $e_1 + e_2$ is the norm $N(z) = z \bar z$, a homomorphism $R_{\mathbb{C}/\mathbb{R}} \mathbb{G}_m \to \mathbb{G}_m$. Its kernel is $S$, and the exact sequence of lattices $0 \to \mathbb{Z}(e_1 + e_2) \to \mathbb{Z}^2 \to \mathbb{Z}^2 / \mathbb{Z}(e_1 + e_2) \to 0$ matches $1 \to S \to R_{\mathbb{C}/\mathbb{R}} \mathbb{G}_m \to \mathbb{G}_m \to 1$. The norm is a quotient map, but on real points its image is $\mathbb{R}_{>0}$, of index $2$ in $\mathbb{R}^\times$. A classical result on the integral representations of a group of order $2$ says that every lattice with an action of $\Gamma$ is a direct sum of copies of the three basic lattices. So every real torus is a product of copies of $\mathbb{G}_m$, $S$ and $R_{\mathbb{C}/\mathbb{R}} \mathbb{G}_m$.

### Rigidity

**Theorem 1.4.12 (rigidity).** Let $k$ be algebraically closed, let $G$ be a smooth connected algebraic group, and let $T$ be a torus that is a normal closed subgroup of $G$. Then $T$ is central in $G$.

Lean: not stated yet

*Proof.* Let $p \ge 0$ be the characteristic, and let $n \ge 1$ be prime to $p$. The $n$-torsion $T[n]$ of $T(k) \cong (k^\times)^r$ is $\mu_n(k)^r$, a finite set. Conjugation by elements of $G$ preserves $T[n]$, since $T$ is normal. For $t \in T[n]$, the map $G(k) \to T[n]$, $g \mapsto g t g^{-1}$, is a morphism from an irreducible variety to a finite set. Its image is irreducible, so it is one point, and $g t g^{-1} = t$. Thus $G(k)$ centralizes the union $T_\infty$ of the groups $T[n]$ with $p \nmid n$. This union is dense in $T(k)$. Indeed, the set $\mu_\infty$ of roots of unity of order prime to $p$ is infinite, so it is dense in $k^\times$, and a polynomial in $r$ variables that vanishes on $\mu_\infty^r$ vanishes identically, by induction on $r$. For $g \in G(k)$, the set of $t \in T(k)$ with $g t g^{-1} = t$ is closed and contains $T_\infty$, so it is all of $T(k)$. $\square$

The theorem holds over any field and without smoothness ([Mil17], Chapter 12). The same argument proves the general form of rigidity: a family of homomorphisms of a torus that depends on a connected variety is constant.

**Corollary 1.4.13 (the Weyl group of a torus).** Let $k$ be algebraically closed, let $G$ be smooth and connected, and let $T$ be a torus in $G$. Then $N_G(T)^\circ = C_G(T)^\circ$, and the group $W(G, T) = N_G(T)/C_G(T)$ is finite.

Lean: not stated yet

*Proof.* The normalizer $N = N_G(T)$ and the centralizer $C = C_G(T)$ are closed subgroups, with $C \subset N$. The torus $T$ is connected, so $T \subset N^\circ$, and $T$ is normal in $N^\circ$. By Theorem 1.4.12, $N^\circ$ centralizes $T$, so $N^\circ \subset C$ and $N^\circ = C^\circ$. Then $W$ is a quotient of the finite group $N / N^\circ$. $\square$

The group $W(G, T)$ acts faithfully on $X^*(T)$, by $(w \chi)(t) = \chi(n^{-1} t n)$ for a representative $n$ of $w$. When $T$ is a maximal torus of a reductive group, $W(G, T)$ is the Weyl group of the root datum.

**Example 1.4.14 (the weights of the adjoint action).** The torus $D_n$ acts on the space $M_n$ of matrices by conjugation. For $t = \mathrm{diag}(t_1, \dots, t_n)$ we have $t E_{ij} t^{-1} = t_i t_j^{-1} E_{ij}$. So the weight spaces are the lines $k E_{ij}$ for $i \ne j$, with weight $e_i - e_j$, and the space of diagonal matrices, with weight $0$. The nonzero weights $e_i - e_j$ are the *roots* of $GL_n$ with respect to $D_n$. The same computation for $SL_n$ and $PGL_n$ gives the same elements $e_i - e_j$, read in the lattices of Example 1.4.9. The normalizer of $D_n$ in $GL_n$ is the group of monomial matrices, and $W(GL_n, D_n) \cong S_n$ acts on $X^*(D_n)$ by permuting the $e_i$ (Exercise 7). It permutes the roots. The roots $e_i - e_j$ with $i < j$ are the weights of $D_n$ on the strictly upper triangular matrices, which form the tangent space of $U_n$. They are the positive roots for the Borel subgroup $B_n$ of Section 1.6, and Chapter 2 shows that the roots $e_i - e_{i+1}$ form a basis of the root system.
