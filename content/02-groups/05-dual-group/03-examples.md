---
title: Examples of dual groups
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Examples of dual groups

This section computes the dual groups of the split classical groups. In each case we write down a maximal torus, its characters and cocharacters, the roots and the coroots, and then we read off the dual root datum. The computations of the root data are in Chapter 3. We repeat the parts that we need, because the coroots matter here and the coroots of the short and long roots are where the errors come from. The answer is the table at the end: $GL_n$ is self-dual, $SL_n$ and $PGL_n$ are exchanged, $Sp_{2n}$ and $SO_{2n+1}$ are exchanged, and $SO_{2n}$ is self-dual. Throughout, $X = X^*(T)$ and $X^\vee = X_*(T)$, and we write $e_1, \dots, e_n$ for the standard basis of $\mathbb{Z}^n$ in $X$ and $e_1^\vee, \dots, e_n^\vee$ for the dual basis in $X^\vee$.

### The general linear group

Let $G = GL_n$ and let $T$ be the diagonal torus. The character $e_i$ sends $\mathrm{diag}(t_1, \dots, t_n)$ to $t_i$, and the cocharacter $e_i^\vee$ sends $s$ to the diagonal matrix with $s$ in place $i$ and $1$ elsewhere. So $X = X^\vee = \mathbb{Z}^n$ with the standard pairing. The roots are $e_i - e_j$ for $i \ne j$, with root subgroups $1 + a E_{i,j}$, by Example 1.4.14. The root $e_i - e_j$ lives in the copy of $GL_2$ in the rows and columns $i, j$, and its coroot is $s \mapsto$ the diagonal matrix with $s$ in place $i$ and $s^{-1}$ in place $j$. That is, $(e_i - e_j)^\vee = e_i^\vee - e_j^\vee$. The upper triangular Borel subgroup gives the base $\alpha_i = e_i - e_{i+1}$, $1 \le i \le n-1$.

**Example 5.3.1 (the dual of GL_n).** The map $e_i \mapsto e_i^\vee$ is an isomorphism of based root data $\Psi_0(GL_n) \to \Psi_0(GL_n)^\vee$. So $GL_n^\vee = GL_n(\mathbb{C})$, with its standard pinning. The dual torus $T^\vee$ is the diagonal torus of $GL_n(\mathbb{C})$, and the identification $T^\vee = X^*(T) \otimes \mathbb{C}^\times$ sends $e_i \otimes z$ to the diagonal matrix with $z$ in place $i$.

Lean: `Langlands.Groups.RootDatum.gl`, `Langlands.Groups.RootDatum.glBase`, `Langlands.Groups.RootDatum.dual_gl` and `Langlands.Groups.RootDatum.glDualEquiv`

The isomorphism $\Psi_0(GL_n) \cong \Psi_0(GL_n)^\vee$ is not canonical in a strong sense. The map $e_i \mapsto -e_{n+1-i}^\vee$ is another isomorphism, and it differs from the first by the automorphism $x \mapsto -w_0 x$ of $\Psi_0$, which is not the identity for $n \ge 2$. On the group side, this automorphism is $g \mapsto J \, {}^t g^{-1} J^{-1}$, and it sends a representation of $GL_n(\mathbb{C})$ to its contragredient. Any statement that uses $GL_n^\vee = GL_n(\mathbb{C})$ must fix the isomorphism. The convention of this handbook is the first one, $e_i \mapsto e_i^\vee$. With this convention the local Langlands correspondence for $GL_1$ is local class field theory, normalized as in Volume 0, Chapter 3.

### The special and projective linear groups

Let $G = SL_n$, with diagonal torus $T = \{\mathrm{diag}(t_1, \dots, t_n) : t_1 \cdots t_n = 1\}$. Restriction of characters from the diagonal torus of $GL_n$ gives
$$X = \mathbb{Z}^n / \mathbb{Z}(e_1 + \dots + e_n), \qquad X^\vee = \{ a \in \mathbb{Z}^n : a_1 + \dots + a_n = 0 \},$$
by Example 1.4.9. The roots are the images of $e_i - e_j$ and the coroots are $e_i^\vee - e_j^\vee$. For $G = PGL_n$ with the image $T$ of the diagonal torus, the same example gives
$$X = \{ a \in \mathbb{Z}^n : a_1 + \dots + a_n = 0 \}, \qquad X^\vee = \mathbb{Z}^n / \mathbb{Z}(e_1^\vee + \dots + e_n^\vee),$$
with roots $e_i - e_j$ and coroots the images of $e_i^\vee - e_j^\vee$.

**Proposition 5.3.2 (SL_n and PGL_n).** The map $e_i \mapsto e_i^\vee$ induces an isomorphism $\Psi_0(SL_n)^\vee \cong \Psi_0(PGL_n)$. So $SL_n^\vee = PGL_n(\mathbb{C})$ and $PGL_n^\vee = SL_n(\mathbb{C})$. The centre of $SL_n$ is $\mu_n$, and $\pi_1(SL_n) = 0$. The centre of $PGL_n$ is trivial, and $\pi_1(PGL_n) = \mathbb{Z}/n$.

Lean: `Langlands.Groups.RootDatum.dual_sl2` and `Langlands.Groups.RootDatum.dual_pgl2`, for the root data with $n = 2$

*Proof.* The dual of $\Psi(SL_n)$ is $(\{a : \sum a_i = 0\}, \{e_i^\vee - e_j^\vee\}, \mathbb{Z}^n/\mathbb{Z}(\sum e_i), \{e_i - e_j\})$. Under $e_i^\vee \mapsto e_i$ this is $\Psi(PGL_n)$, and the base $\{\alpha_i^\vee\}$ goes to $\{\alpha_i\}$. For the centre, $X/Q$ for $SL_n$ is $\mathbb{Z}^n / (\mathbb{Z}(\sum e_i) + \{a : \sum a_i = 0\})$, and $a \mapsto \sum a_i \bmod n$ identifies it with $\mathbb{Z}/n$. A finite diagonalizable group with character group $\mathbb{Z}/n$ is $\mu_n$, by Corollary 1.4.6. For $SL_n$, the coroots $e_i^\vee - e_{i+1}^\vee$ span the lattice $X^\vee$, so $\pi_1(SL_n) = 0$. The statements for $PGL_n$ follow from Proposition 5.1.9 by duality. $\square$

For $n = 2$ this is Example 5.1.6. The two groups $SL_n$ and $PGL_n$ have isomorphic Lie algebras in characteristic $0$, the same Weyl group $S_n$, and the same quotient $PGL_n(\mathbb{C})$ of their groups of complex points by the centres. Only the lattice $X$ tells them apart, and the dual group sees exactly that lattice. The irreducible representations of $SL_n^\vee = PGL_n(\mathbb{C})$ are the irreducible representations of $GL_n(\mathbb{C})$ on which the scalars act trivially. So the standard representation of $GL_n(\mathbb{C})$ does not descend to $SL_n^\vee$, and a representation of $SL_n$ has no standard L-function of degree $n$. One gets L-functions for $SL_n$ from representations of $PGL_n(\mathbb{C})$, such as the adjoint representation of dimension $n^2 - 1$, or by a lift to $GL_n$.

### The symplectic and odd orthogonal groups

Let $n \ge 1$. We use the symplectic form of Example 1.1.10, with matrix $J = \begin{pmatrix} 0 & I_n \\ -I_n & 0 \end{pmatrix}$ on $k^{2n}$, and $Sp_{2n} = \{ g : {}^t g J g = J \}$. The diagonal torus is
$$T = \{ \mathrm{diag}(t_1, \dots, t_n, t_1^{-1}, \dots, t_n^{-1}) \}.$$
It is a split maximal torus of rank $n$, with $X = \mathbb{Z}^n$ and $X^\vee = \mathbb{Z}^n$, where $e_i$ is $t \mapsto t_i$ and $e_i^\vee$ is $s \mapsto \mathrm{diag}(1, \dots, s, \dots, 1, 1, \dots, s^{-1}, \dots, 1)$ with $s$ in place $i$ and $s^{-1}$ in place $n+i$. The Lie algebra consists of the block matrices $\begin{pmatrix} A & B \\ C & -{}^t A \end{pmatrix}$ with $B$ and $C$ symmetric. The roots are the weights of $T$ on it:
1. $e_i - e_j$ for $i \ne j$, on the entries of $A$;
2. $e_i + e_j$ for $i < j$, and $2 e_i$, on the entries of $B$;
3. $-e_i - e_j$ for $i < j$, and $-2 e_i$, on the entries of $C$.

So the roots form a root system of type $C_n$. The coroots are computed in the subgroups $SL_2$ that the root subgroups generate. For $\pm e_i \pm e_j$ with $i \ne j$, the root lies in a subgroup $SL_2$ that acts on two planes at the same time, and the coroot is $\pm e_i^\vee \pm e_j^\vee$, with the same signs. For the long root $2e_i$, the subgroup $SL_2$ is $Sp_2 = SL_2$ acting on the plane spanned by the basis vectors $i$ and $n+i$. Its diagonal torus is $s \mapsto \mathrm{diag}(s, s^{-1})$ in that plane, which is $e_i^\vee$. So
$$(2 e_i)^\vee = e_i^\vee,$$
and indeed $\langle 2 e_i, e_i^\vee \rangle = 2$. In short: the roots of $Sp_{2n}$ are $\pm e_i \pm e_j$ and $\pm 2 e_i$, and the coroots are $\pm e_i^\vee \pm e_j^\vee$ and $\pm e_i^\vee$.

Now let $SO_{2n+1}$ be the special orthogonal group of the quadratic form $Q(x) = x_0^2 + \sum_{i=1}^n x_i x_{n+i}$ on $k^{2n+1}$, with coordinates $x_0, x_1, \dots, x_{2n}$, over a field of characteristic not $2$. The torus
$$T = \{ \mathrm{diag}(1, t_1, \dots, t_n, t_1^{-1}, \dots, t_n^{-1}) \}$$
preserves $Q$, and it is a split maximal torus. Again $X = X^\vee = \mathbb{Z}^n$. The Lie algebra is the space of $A$ with ${}^t A M + M A = 0$, where $M$ is the matrix of the bilinear form of $Q$, and a computation of the weights gives the roots
$$\pm e_i \pm e_j \ (i < j), \qquad \pm e_i,$$
a root system of type $B_n$. The roots $\pm e_i$ have root spaces in the entries that join $x_0$ with $x_i$ and $x_{n+i}$. The subgroup $SL_2$ of the short root $e_i$ acts on the three-dimensional space with coordinates $x_i, x_0, x_{n+i}$, and on it the form is $x_0^2 + x_i x_{n+i}$. This is the adjoint representation of $SL_2$ on $\mathfrak{sl}_2$ with the determinant form, up to a scalar, so the map $SL_2 \to SO_3$ is the quotient by $\mu_2$. The diagonal element $\mathrm{diag}(s, s^{-1})$ of $SL_2$ acts on $\mathfrak{sl}_2$ with eigenvalues $s^2, 1, s^{-2}$. So the coroot of $e_i$ is $s \mapsto \mathrm{diag}(1, \dots, s^2, \dots, s^{-2}, \dots)$, that is,
$$(e_i)^\vee = 2 e_i^\vee.$$
The long roots $\pm e_i \pm e_j$ have coroots $\pm e_i^\vee \pm e_j^\vee$ as before.

**Proposition 5.3.3 (Sp_2n and SO_2n+1).** The map $e_i \mapsto e_i^\vee$ induces an isomorphism $\Psi(Sp_{2n})^\vee \cong \Psi(SO_{2n+1})$ of root data, and it matches the standard bases. So
$$Sp_{2n}^\vee = SO_{2n+1}(\mathbb{C}), \qquad SO_{2n+1}^\vee = Sp_{2n}(\mathbb{C}).$$
The group $Sp_{2n}$ is simply connected with centre $\mu_2$, and $SO_{2n+1}$ is adjoint with $\pi_1(SO_{2n+1}) = \mathbb{Z}/2$.

Lean: not stated yet

*Proof.* The dual root datum of $Sp_{2n}$ has roots $\pm e_i^\vee \pm e_j^\vee$ and $\pm e_i^\vee$ in $X^\vee = \mathbb{Z}^n$, and the coroot of $e_i^\vee$ in it is $2 e_i$, since $(2e_i)^\vee = e_i^\vee$. Under $e_i^\vee \mapsto e_i$, this is the root datum of $SO_{2n+1}$, where the coroot of $e_i$ is $2 e_i^\vee$. The standard base of $Sp_{2n}$ is $e_1 - e_2, \dots, e_{n-1} - e_n, 2 e_n$, and its dual base is $e_1^\vee - e_2^\vee, \dots, e_{n-1}^\vee - e_n^\vee, e_n^\vee$, which goes to the standard base $e_1 - e_2, \dots, e_{n-1} - e_n, e_n$ of $SO_{2n+1}$. For $Sp_{2n}$, the root lattice is $Q = \{ a \in \mathbb{Z}^n : \sum a_i \text{ even} \}$, so $X/Q = \mathbb{Z}/2$ and the centre is $\mu_2 = \{\pm 1\}$. The coroots include all $e_i^\vee$, so $Q^\vee = X^\vee$ and $\pi_1 = 0$. The statements for $SO_{2n+1}$ follow by duality. $\square$

**Example 5.3.4 (rank two).** For $n = 2$ the root systems $B_2$ and $C_2$ are isomorphic, by a rotation by $\pi/4$ and a rescaling. So $Sp_4$ and $SO_5$ have isomorphic root systems, and the difference between them is the lattice. The groups are related by the isogeny $Sp_4 \to SO_5$ with kernel $\mu_2$, which comes from the action of $Sp_4$ on the five-dimensional space of $\wedge^2 k^4$ orthogonal to the symplectic form. So $Sp_4^\vee = SO_5(\mathbb{C}) \cong PSp_4(\mathbb{C})$, and $SO_5^\vee = Sp_4(\mathbb{C})$. With the base $\alpha_1 = e_1 - e_2$ and $\alpha_2 = 2 e_2$ of $Sp_4$, the Cartan matrix $\langle \alpha_i, \alpha_j^\vee \rangle$ is
$$A(C_2) = \begin{pmatrix} 2 & -1 \\ -2 & 2 \end{pmatrix}, \qquad A(B_2) = {}^t A(C_2) = \begin{pmatrix} 2 & -2 \\ -1 & 2 \end{pmatrix},$$
as in Proposition 5.1.13. The group $GSp_4$ of symplectic similitudes is self-dual, $GSp_4^\vee \cong GSp_4(\mathbb{C})$, and the inclusion $GSp_4(\mathbb{C}) \subset GL_4(\mathbb{C})$ is the spin representation of the dual group. This is the starting point of the local Langlands correspondence for $GSp_4$ of Gan and Takeda.

### The even orthogonal groups

Let $n \ge 2$ and let $SO_{2n}$ be the special orthogonal group of the split form $Q(x) = \sum_{i=1}^n x_i x_{n+i}$ on $k^{2n}$, in characteristic not $2$. The torus $T = \{\mathrm{diag}(t_1, \dots, t_n, t_1^{-1}, \dots, t_n^{-1})\}$ is a split maximal torus with $X = X^\vee = \mathbb{Z}^n$. The roots are $\pm e_i \pm e_j$ for $i < j$, and the coroots are $\pm e_i^\vee \pm e_j^\vee$. This is a root system of type $D_n$.

**Proposition 5.3.5 (SO_2n).** The map $e_i \mapsto e_i^\vee$ is an isomorphism of based root data $\Psi_0(SO_{2n}) \cong \Psi_0(SO_{2n})^\vee$. So $SO_{2n}^\vee = SO_{2n}(\mathbb{C})$. The centre of $SO_{2n}$ is $\mu_2$ and $\pi_1(SO_{2n}) = \mathbb{Z}/2$. The simply connected group $\mathrm{Spin}_{2n}$ and the adjoint group $PSO_{2n}$ are dual to each other.

Lean: not stated yet

*Proof.* The first statement is clear from the formulas. The root lattice is $Q = \{ a : \sum a_i \text{ even} \}$, so $X/Q \cong \mathbb{Z}/2$, and in the same way $X^\vee / Q^\vee \cong \mathbb{Z}/2$. The last statement follows from Proposition 5.1.9, since $X = P$ for $\mathrm{Spin}_{2n}$ and $X = Q$ for $PSO_{2n}$. $\square$

The group $SO_{2n}$ is neither simply connected nor adjoint. The full orthogonal group $O_{2n}$ is not connected, and the theory of this chapter does not cover it. Its role in the Langlands program is played by the quasi-split forms of $SO_{2n}$, whose L-groups contain the outer automorphism of the Dynkin diagram, see Section 5.4.

### Summary and the exceptional groups

**Proposition 5.3.6 (table of dual groups).** For the split groups in the first column, the centre $Z(G)$ has the character group $X/Q$ of the second column, the fundamental group $X^\vee/Q^\vee$ is in the third column, and the dual group is in the last column.

| $G$ | $X/Q$ | $X^\vee/Q^\vee$ | $G^\vee$ |
|---|---|---|---|
| $GL_n$ | $\mathbb{Z}$ | $\mathbb{Z}$ | $GL_n(\mathbb{C})$ |
| $SL_n$ | $\mathbb{Z}/n$ | $0$ | $PGL_n(\mathbb{C})$ |
| $PGL_n$ | $0$ | $\mathbb{Z}/n$ | $SL_n(\mathbb{C})$ |
| $Sp_{2n}$ | $\mathbb{Z}/2$ | $0$ | $SO_{2n+1}(\mathbb{C})$ |
| $SO_{2n+1}$ | $0$ | $\mathbb{Z}/2$ | $Sp_{2n}(\mathbb{C})$ |
| $SO_{2n}$ | $\mathbb{Z}/2$ | $\mathbb{Z}/2$ | $SO_{2n}(\mathbb{C})$ |
| $\mathrm{Spin}_{2n+1}$ | $\mathbb{Z}/2$ | $0$ | $PSp_{2n}(\mathbb{C})$ |
| $G_2$ | $0$ | $0$ | $G_2(\mathbb{C})$ |

Lean: not stated yet

*Proof.* The first six rows are Example 5.3.1 and Propositions 5.3.2, 5.3.3 and 5.3.5. For $\mathrm{Spin}_{2n+1}$, the lattice $X$ is the weight lattice of $B_n$, so the dual lattice $X^\vee$ is the coroot lattice, which is the root lattice of $C_n$ under $e_i^\vee \mapsto e_i$. So the dual group is the simply connected group of type $C_n$ divided by its full centre, which is $PSp_{2n}(\mathbb{C})$. For $G_2$, the root lattice and the weight lattice agree, so $X = Q = P$ and $X^\vee = Q^\vee = P^\vee$. The dual root system of $G_2$ is again of type $G_2$ by Proposition 5.1.13, and the dual group is the unique group of type $G_2$ over $\mathbb{C}$. $\square$

The same argument applies to the other exceptional types. For $F_4$ and $E_8$, again $P = Q$, there is only one group of each type, and the group is self-dual. The groups of type $E_6$ have $P/Q = \mathbb{Z}/3$, and the groups of type $E_7$ have $P/Q = \mathbb{Z}/2$. In both cases there are two groups, the simply connected one and the adjoint one, and duality exchanges them. Since $G_2$ and $F_4$ have two root lengths, their self-duality exchanges the long and the short roots. For example, the coroots of the long roots of $G_2$ are the short coroots. Exercise 4 makes this explicit.

The Weyl group of $G^\vee$ is the Weyl group of $G$ in each row of the table, by Proposition 5.2.6. So the Weyl group of $Sp_{2n}$ and of $SO_{2n+1}$ is the group $(\mathbb{Z}/2)^n \rtimes S_n$ of signed permutations, which acts on $X = \mathbb{Z}^n$ and on $X^\vee = \mathbb{Z}^n$ in the same way. The Weyl group of $SO_{2n}$ is the subgroup of index two of signed permutations with an even number of sign changes.
