---
title: The representations of SL_2 and GL_n
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## The representations of $SL_2$ and $GL_n$

This section makes the general theory explicit for $SL_2$ and $GL_n$. For $SL_2$ the irreducible representations are the symmetric powers of the standard representation, and their tensor products follow the rule of Clebsch and Gordan. For $GL_n$ the dominant weights are the nonincreasing sequences of integers, the characters are the Schur polynomials, and the dimension formula becomes a product over pairs $i < j$. In this section $k$ has characteristic $0$, except in Example 4.4.2. The groups $GL_n$ and $SL_2$ are the groups that occur most often in the rest of the handbook: $GL_n$ is its own dual group, and $SL_2$ and $PGL_2$ are dual to each other.

### The group $SL_2$

Let $V = k^2$ with basis $e_1, e_2$, and let $\varpi$ be the fundamental weight, $\varpi(\mathrm{diag}(s, s^{-1})) = s$. The positive root is $\alpha = 2 \varpi$, and $\rho = \varpi$. We write $L(n)$ for $L(n \varpi)$. The weights of $\mathrm{Sym}^n V$ are the weights of the monomials $e_1^i e_2^{n-i}$, which are $(2i - n) \varpi$ for $0 \le i \le n$.

**Theorem 4.4.1 (the irreducible representations of $SL_2$).** For each $n \ge 0$ the representation $\mathrm{Sym}^n V$ of $SL_2$ is irreducible of dimension $n + 1$, and it is isomorphic to $L(n)$. Every irreducible representation of $SL_2$ is isomorphic to exactly one $\mathrm{Sym}^n V$. The character of $\mathrm{Sym}^n V$ at $\mathrm{diag}(s, s^{-1})$ is
$$s^n + s^{n-2} + \dots + s^{-n} = \frac{s^{n+1} - s^{-n-1}}{s - s^{-1}}.$$

Lean: not stated yet

*Proof.* The weights of $\mathrm{Sym}^n V$ are $n, n-2, \dots, -n$ times $\varpi$, each with multiplicity $1$, which gives the character. It equals the character of $L(n)$ in Example 4.3.5, so $\mathrm{Sym}^n V \cong L(n)$ by Corollary 4.2.12. The rest is Theorem 4.2.9, since $X^+ = \mathbb{N} \varpi$. We also give a direct proof of irreducibility that does not use Section 4.3. Let $M \subset \mathrm{Sym}^n V$ be a nonzero subrepresentation. It is a sum of weight spaces, which are the lines $k e_1^i e_2^{n-i}$, so it contains some monomial $e_1^i e_2^{n-i}$. The element $u(c) = \left(\begin{smallmatrix} 1 & c \\ 0 & 1 \end{smallmatrix}\right)$ maps $e_2$ to $c e_1 + e_2$, so
$$u(c) \, e_1^i e_2^{n-i} = \sum_{j=0}^{n-i} \binom{n-i}{j} c^j e_1^{i+j} e_2^{n-i-j}.$$
Since $k$ is infinite, each term of this sum lies in $M$, by the argument of Proposition 4.1.3. The binomial coefficients are nonzero in characteristic $0$, so $M$ contains $e_1^n$. In the same way the lower unitriangular matrices move $e_1^n$ to all the monomials. So $M = \mathrm{Sym}^n V$. $\square$

**Example 4.4.2 (characteristic $p$).** Let $k$ have characteristic $p > 0$. The proof above breaks down because $\binom{p}{j} = 0$ in $k$ for $0 < j < p$. Indeed, in $\mathrm{Sym}^p V$ the span $M$ of $e_1^p$ and $e_2^p$ is a subrepresentation, because $(a e_1 + c e_2)^p = a^p e_1^p + c^p e_2^p$. As a representation, $M$ is the standard representation $V$ composed with the Frobenius map $g \mapsto g^{(p)}$ that raises all matrix entries to the $p$-th power. So $\mathrm{Sym}^p V$ is not irreducible. By Example 4.2.10, $H^0(p \varpi)$ is the space of forms of degree $p$ in the second column, and its socle $L(p)$ is the span of $b^p$ and $d^p$, of dimension $2$. This agrees with Steinberg's theorem of Remark 4.2.14: $L(p) \cong L(1)^{[1]}$.

**Proposition 4.4.3 (Clebsch and Gordan).** For $m \ge n \ge 0$,
$$L(m) \otimes L(n) \cong L(m + n) \oplus L(m + n - 2) \oplus \dots \oplus L(m - n).$$

Lean: not stated yet

*Proof.* Write $x = e^\varpi$. By Theorem 4.4.1,
$$(x - x^{-1}) \, \mathrm{ch}\, L(m) \, \mathrm{ch}\, L(n) = (x^{m+1} - x^{-m-1}) \sum_{j=0}^{n} x^{n - 2j} = \sum_{j=0}^n x^{m+n+1-2j} - \sum_{j=0}^n x^{-m-1+n-2j}.$$
In the second sum, put $j' = n - j$. The exponent becomes $-(m + n + 1 - 2j')$. So the right side is $\sum_{j=0}^n (x^{m+n+1-2j} - x^{-(m+n+1-2j)})$. Since $m \ge n$, each exponent $m + n + 1 - 2j$ is positive, and the $j$-th term is $(x - x^{-1}) \, \mathrm{ch}\, L(m + n - 2j)$. Now use Corollary 4.2.12. $\square$

The same computation is an instance of Theorem 4.3.10. The weights of $L(n)$ are $\nu = n - 2j$, and $m + \nu \ge m - n \ge 0$ is dominant for all of them. For $m < n$ some terms $\chi_{m + \nu}$ have $m + \nu < 0$, and they cancel: $\chi_{-1} = 0$, and $\chi_{-r} = -\chi_{r - 2}$ for $r \ge 2$, by the dot action $s \cdot \eta = -\eta - 2$.

**Example 4.4.4 ($PGL_2$, $GL_2$ and the adjoint representation).** The character lattice of $PGL_2$ is $\mathbb{Z} \alpha = 2 \mathbb{Z} \varpi$, so the irreducible representations of $PGL_2$ are the $L(n)$ with $n$ even. The representation $L(2) = \mathrm{Sym}^2 V$ is the adjoint representation of $SL_2$ on $\mathfrak{sl}_2$, of dimension $3$. The group $PGL_2$ acts on $\mathrm{Sym}^{2m} V \otimes \det^{-m}$, and this is $L(2m)$ as a representation of $PGL_2$. For $GL_2$ the character lattice is $\mathbb{Z}^2$, and the dominant weights are the pairs $(\lambda_1, \lambda_2)$ with $\lambda_1 \ge \lambda_2$. The representation with highest weight $(\lambda_1, \lambda_2)$ is $\mathrm{Sym}^{\lambda_1 - \lambda_2} V \otimes \det^{\lambda_2}$, of dimension $\lambda_1 - \lambda_2 + 1$. Its restriction to $SL_2$ is $L(\lambda_1 - \lambda_2)$. In the theory of modular forms, the representation $\mathrm{Sym}^{k-2} V$ of $GL_2$ is the coefficient system of the Eichler and Shimura isomorphism for forms of weight $k$.

### The group $GL_n$

Let $G = GL_n$, with the diagonal torus $T$, the upper triangular Borel subgroup $B$ and $V = k^n$ the standard representation. We identify $X = \mathbb{Z}^n$, where $\lambda = (\lambda_1, \dots, \lambda_n)$ is the character $\mathrm{diag}(x_1, \dots, x_n) \mapsto x_1^{\lambda_1} \cdots x_n^{\lambda_n}$, and $\mathbb{Z}[X] = \mathbb{Z}[x_1^{\pm 1}, \dots, x_n^{\pm 1}]$. The positive roots are $e_i - e_j$ for $i < j$, with coroots $e_i^* - e_j^*$, and $W = S_n$ permutes the coordinates. By Example 4.1.11 the dominant weights are the sequences $\lambda_1 \ge \lambda_2 \ge \dots \ge \lambda_n$. We have $\rho = \frac{1}{2}(n - 1, n - 3, \dots, 1 - n)$. Put $\delta = (n - 1, n - 2, \dots, 1, 0)$. Then $\delta - \rho = \frac{n-1}{2}(1, \dots, 1)$ is fixed by $W$.

**Definition 4.4.5 (Schur polynomial).** For integers $\lambda_1 \ge \dots \ge \lambda_n$, the *Schur polynomial* is
$$s_\lambda(x_1, \dots, x_n) = \frac{\det \left( x_i^{\lambda_j + n - j} \right)_{1 \le i, j \le n}}{\det \left( x_i^{n - j} \right)_{1 \le i, j \le n}}.$$

The denominator is the Vandermonde determinant $\prod_{i < j} (x_i - x_j)$, which Mathlib has as `Matrix.det_vandermonde`, up to the order of the columns. The numerator is an alternating polynomial, so it is divisible by every $x_i - x_j$, and hence by their product. So $s_\lambda$ is a symmetric Laurent polynomial with integer coefficients, and a polynomial if $\lambda_n \ge 0$. If $\lambda_n \ge 0$, then $\lambda$ is a *partition* of $|\lambda| = \sum \lambda_i$ with at most $n$ parts, and $s_\lambda$ is homogeneous of degree $|\lambda|$.

**Theorem 4.4.6 (the irreducible representations of $GL_n$).** The irreducible representations of $GL_n$ are the $L(\lambda)$ for $\lambda_1 \ge \dots \ge \lambda_n$, and the character of $L(\lambda)$ is the Schur polynomial $s_\lambda$. Its dimension is
$$\dim L(\lambda) = \prod_{1 \le i < j \le n} \frac{\lambda_i - \lambda_j + j - i}{j - i}.$$

Lean: not stated yet

*Proof.* For $\mu \in X'$ we have $A_\mu = \sum_{\sigma \in S_n} \mathrm{sgn}(\sigma) \prod_i x_{\sigma(i)}^{\mu_i} = \det(x_i^{\mu_j})$. If $c \in \frac{1}{2}\mathbb{Z}$, then $A_{\mu + c(1, \dots, 1)} = (x_1 \cdots x_n)^c A_\mu$ in $\mathbb{Z}[X']$. So the quotient $A_{\lambda + \rho} / A_\rho$ equals $A_{\lambda + \delta} / A_\delta$, which is $s_\lambda$. Theorem 4.3.4 gives the character. The pairing of $\lambda + \rho$ with the coroot $e_i^* - e_j^*$ is $\lambda_i - \lambda_j + j - i$, and the pairing of $\rho$ with it is $j - i$. Corollary 4.3.6 gives the dimension. $\square$

**Example 4.4.7 (symmetric and exterior powers).** For $\lambda = (k, 0, \dots, 0)$ the representation $\mathrm{Sym}^k V$ has weights all $\mu \in \mathbb{N}^n$ with $|\mu| = k$, each with multiplicity $1$. Its character is the complete symmetric polynomial $h_k$, and it contains the highest weight vector $e_1^k$, so it is $L(k, 0, \dots, 0)$ by Theorem 4.4.6 and Corollary 4.2.12. The dimension formula gives $\prod_{j=2}^n \frac{k + j - 1}{j - 1} = \binom{n + k - 1}{k}$, as it should. For $\lambda = (1, \dots, 1, 0, \dots, 0)$ with $k$ ones, $\wedge^k V$ has character the elementary symmetric polynomial $e_k$, dimension $\binom{n}{k}$, and highest weight vector $e_1 \wedge \dots \wedge e_k$, so $\wedge^k V = L(1^k)$. In particular $\wedge^n V = \det = L(1, \dots, 1)$. The dual $V^*$ is $L(0, \dots, 0, -1)$. The adjoint representation on $\mathfrak{sl}_n$ is $L(1, 0, \dots, 0, -1)$: its highest weight is the highest root $e_1 - e_n$, and the formula gives $\frac{n+1}{n-1} \cdot (n-1) \cdot (n-1) = n^2 - 1$, from the pair $(1, n)$, the pairs $(1, j)$ and the pairs $(i, n)$ with $1 < i, j < n$.

Every dominant weight is $\lambda = \lambda' + \lambda_n(1, \dots, 1)$ with $\lambda'_n = 0$, and $L(\lambda) \cong L(\lambda') \otimes \det^{\lambda_n}$. So every irreducible representation is a polynomial representation twisted by a power of the determinant. The polynomial representations are classified by partitions with at most $n$ parts.

**Theorem 4.4.8 (Schur and Weyl duality).** Let $m \ge 0$. The groups $GL_n$ and $S_m$ act on $V^{\otimes m}$, by $g(v_1 \otimes \dots \otimes v_m) = g v_1 \otimes \dots \otimes g v_m$ and by permutation of the factors, and the two actions commute. As a representation of $GL_n \times S_m$,
$$V^{\otimes m} \cong \bigoplus_{\lambda} L(\lambda) \otimes S^\lambda,$$
where $\lambda$ runs over the partitions of $m$ with at most $n$ parts and $S^\lambda$ is the irreducible representation of $S_m$ (the Specht module) attached to $\lambda$. The images of $k[GL_n(k)]$ and $k[S_m]$ in $\mathrm{End}(V^{\otimes m})$ are the commutants of each other.

Lean: not stated yet

For the proof see Fulton and Harris, *Representation Theory*, Lecture 6. Since every polynomial representation of degree $m$ occurs in $V^{\otimes m}$, Schur and Weyl duality gives a second construction of the $L(\lambda)$, by Young symmetrizers, that does not use the induced modules of Section 4.2.

**Proposition 4.4.9 (the rule of Pieri for $V$).** For every dominant weight $\lambda$ of $GL_n$,
$$L(\lambda) \otimes V \cong \bigoplus_{i} L(\lambda + e_i),$$
where $i$ runs over the indices $1 \le i \le n$ with $i = 1$ or $\lambda_{i-1} > \lambda_i$, that is, over the indices for which $\lambda + e_i$ is dominant.

Lean: not stated yet

*Proof.* The weights of $V$ are $e_1, \dots, e_n$, each with multiplicity $1$. By Theorem 4.3.10, $\mathrm{ch}(L(\lambda) \otimes V) = \sum_i \chi_{\lambda + e_i}$. If $\lambda + e_i$ is dominant, then $\chi_{\lambda + e_i} = \mathrm{ch}\, L(\lambda + e_i)$. Otherwise $i > 1$ and $\lambda_{i-1} = \lambda_i$. Then the coordinates $i - 1$ and $i$ of $\lambda + e_i + \rho$ are equal, because the coordinates of $\rho$ decrease by $1$ at each step. So the transposition of $i-1$ and $i$ fixes $\lambda + e_i + \rho$, and $\chi_{\lambda + e_i} = 0$. Corollary 4.2.12 finishes the proof. $\square$

In terms of Young diagrams, $L(\lambda) \otimes V$ is the sum of the $L(\lambda')$, where $\lambda'$ runs over the diagrams obtained from $\lambda$ by adding one box. For example, for $n \ge 2$, $V \otimes V = L(2, 0, \dots) \oplus L(1, 1, 0, \dots) = \mathrm{Sym}^2 V \oplus \wedge^2 V$.

**Proposition 4.4.10 (restriction to $SL_n$).** Let $\lambda$ be a dominant weight of $GL_n$. The restriction of $L(\lambda)$ to $SL_n$ is irreducible, with highest weight the image of $\lambda$ in $X^*(T \cap SL_n) = \mathbb{Z}^n / \mathbb{Z}(1, \dots, 1)$. Two representations $L(\lambda)$ and $L(\lambda')$ have isomorphic restrictions if and only if $\lambda - \lambda' \in \mathbb{Z}(1, \dots, 1)$. Every irreducible representation of $SL_n$ arises in this way.

Lean: not stated yet

*Proof.* The weights of $L(\lambda)$ differ from $\lambda$ by sums of roots, so they all have the same sum of coordinates $|\lambda|$. Thus the center $\mathbb{G}_m$ of $GL_n$ acts on $L(\lambda)$ by $z \mapsto z^{|\lambda|}$, and every subspace is stable under it. The group $GL_n$ is generated by its center and $SL_n$. So a subspace stable under $SL_n$ is stable under $GL_n$ by Proposition 1.2.12, and the restriction is irreducible. Its highest weight is the restriction of $\lambda$ to $T \cap SL_n$. By Theorem 4.2.9 applied to $SL_n$, the restrictions are isomorphic if and only if $\lambda$ and $\lambda'$ have the same image, that is, $\lambda - \lambda' \in \mathbb{Z}(1, \dots, 1)$. The dominant weights of $SL_n$ are the images of the dominant weights of $GL_n$, by Example 4.1.11. $\square$

For $PGL_n$, the character lattice is the set of $\lambda \in \mathbb{Z}^n$ with $|\lambda| = 0$, so the irreducible representations of $PGL_n$ are the $L(\lambda)$ of $GL_n$ with $|\lambda| = 0$. For example, the adjoint representation $L(1, 0, \dots, 0, -1)$ is one of them, while $V$ is not.
