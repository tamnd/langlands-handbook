---
title: Maximal tori and roots
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Maximal tori and roots

This section attaches to a split reductive group $(G, T)$ its roots, its root subgroups and its coroots. The roots are the weights of $T$ on the Lie algebra. The coroots come from copies of $SL_2$ in $G$, one for each pair $\pm\alpha$ of roots. The example to keep in mind is $GL_n$ with its diagonal torus, where everything is a computation with elementary matrices. We follow [Mil17], Chapters 20 and 21, and [Spr98], Chapter 7.

Throughout the section, $(G, T)$ is a split reductive group over $k$ of rank $r$, $\mathfrak{g} = \mathrm{Lie}(G)$ and $\mathfrak{t} = \mathrm{Lie}(T)$. We write $X = X^*(T)$ and $X^\vee = X_*(T)$.

### Roots

The torus $T$ acts on $\mathfrak{g}$ by the adjoint representation. Since $T$ is split, $\mathfrak{g}$ is the direct sum of its weight spaces
$$\mathfrak{g}_\chi = \{ v \in \mathfrak{g} : \mathrm{Ad}(t) v = \chi(t) v \text{ for all } t \in T \}, \qquad \chi \in X.$$
The weight space $\mathfrak{g}_0$ is the Lie algebra of $C_G(T)$ (Chapter 1), and $C_G(T) = T$ by Theorem 3.1.10. So $\mathfrak{g}_0 = \mathfrak{t}$, and
$$\mathfrak{g} = \mathfrak{t} \oplus \bigoplus_{\alpha \ne 0} \mathfrak{g}_\alpha.$$

**Definition 3.2.1 (roots).** The *roots* of $(G, T)$ are the nonzero characters $\alpha \in X$ with $\mathfrak{g}_\alpha \ne 0$. We write $R = R(G, T)$ for the set of roots. The space $\mathfrak{g}_\alpha$ is the *root space* of $\alpha$.

The set $R$ is finite, and it is stable under the action of the group $N_G(T)(k)$ on $X$, because this group permutes the weight spaces. Mathlib has the analogous root spaces `LieAlgebra.rootSpace` of a Lie algebra with respect to a Cartan subalgebra, but not the roots of an algebraic group.

**Example 3.2.2 (the roots of $GL_n$).** Let $G = GL_n$ and $T$ the diagonal torus. Let $e_i \in X$ be the character $t \mapsto t_i$, where $t = \mathrm{diag}(t_1, \dots, t_n)$. Then $X = \bigoplus_i \mathbb{Z} e_i$. The Lie algebra is $\mathfrak{gl}_n$, the space of all $n \times n$ matrices, with $\mathrm{Ad}(t) v = t v t^{-1}$. For the elementary matrix $E_{ij}$ we get $t E_{ij} t^{-1} = t_i t_j^{-1} E_{ij}$. Thus
$$R = \{ e_i - e_j : i \ne j \}, \qquad \mathfrak{g}_{e_i - e_j} = k E_{ij},$$
and $\mathfrak{t}$ is the space of diagonal matrices. There are $n(n-1)$ roots, and $\dim GL_n = n + n(n-1)$.

**Example 3.2.3 (the roots of $SL_2$ and of $PGL_2$).** Let $G = SL_2$ and $T = \{\mathrm{diag}(t, t^{-1})\}$. Then $X = \mathbb{Z}\chi$ with $\chi(\mathrm{diag}(t, t^{-1})) = t$. The Lie algebra $\mathfrak{sl}_2$ has the basis $E_{12}$, $E_{21}$, $H = E_{11} - E_{22}$, and $\mathrm{Ad}(\mathrm{diag}(t, t^{-1})) E_{12} = t^2 E_{12}$. So $R = \{2\chi, -2\chi\}$. Now let $G = PGL_2$ and $T$ the image of the diagonal torus of $GL_2$. A character of $T$ is a character $a e_1 + b e_2$ of the diagonal torus of $GL_2$ that is trivial on the scalars, that is, with $a + b = 0$. So $X = \mathbb{Z}(e_1 - e_2)$, and the roots are $\pm(e_1 - e_2)$, which generate $X$. The two groups have the same roots up to a rescaling, but the roots sit differently in the character group. Section 3.3 explains that this difference is what the root datum records.

### Groups of semisimple rank one

The whole structure theory rests on the case of semisimple rank one.

**Theorem 3.2.4 (semisimple rank one).** Let $(G, T)$ be a split reductive group of semisimple rank 1. Then $R = \{\alpha, -\alpha\}$ for some $\alpha$, and $\dim \mathfrak{g}_{\pm \alpha} = 1$. There is a homomorphism $\varphi : SL_2 \to G$ with central kernel and image $DG$, which maps the diagonal torus of $SL_2$ into $T$ and the upper unipotent group of $SL_2$ onto a subgroup $U_\alpha$ with $\mathrm{Lie}(U_\alpha) = \mathfrak{g}_\alpha$. The kernel of $\varphi$ is trivial or $\mu_2$, so $DG$ is isomorphic to $SL_2$ or to $PGL_2$.

Lean: not stated yet

*Proof sketch.* Let $B$ be a Borel subgroup that contains $T$. One shows first that $G/B$ has dimension 1. Since $G/B$ is a smooth projective curve on which $G$ acts with the fixed points of $T$ isolated, it is the projective line. The action of $G$ on $G/B \cong \mathbb{P}^1$ gives a homomorphism $G \to \mathrm{Aut}(\mathbb{P}^1) = PGL_2$, and one shows that its kernel is the center of $G$ and its image is all of $PGL_2$. Then $G / Z(G) \cong PGL_2$, and the derived group of $G$ is a central extension of $PGL_2$ by a finite group. The only connected ones are $SL_2$ and $PGL_2$. See [Mil17], Chapter 20, and [Spr98], Chapter 7. $\square$

### Root subgroups and coroots

**Theorem 3.2.5 (root subgroups and coroots).** Let $(G, T)$ be a split reductive group with roots $R$, and let $\alpha \in R$.
1. The root space $\mathfrak{g}_\alpha$ has dimension 1, and the only roots in $\mathbb{Q}\alpha$ are $\alpha$ and $-\alpha$.
2. There is a unique smooth connected subgroup $U_\alpha$ of $G$ that is normalized by $T$ and has Lie algebra $\mathfrak{g}_\alpha$. There is an isomorphism $u_\alpha : \mathbb{G}_a \to U_\alpha$ with $t \, u_\alpha(x) \, t^{-1} = u_\alpha(\alpha(t) x)$ for $t \in T$.
3. There is a homomorphism $\varphi_\alpha : SL_2 \to G$ with central kernel such that $\varphi_\alpha \left(\begin{smallmatrix} 1 & x \\ 0 & 1 \end{smallmatrix}\right) = u_\alpha(x)$, $\varphi_\alpha$ maps the lower unipotent group onto $U_{-\alpha}$, and $\varphi_\alpha$ maps the diagonal torus into $T$. The cocharacter $\alpha^\vee$ of $T$ defined by $\alpha^\vee(t) = \varphi_\alpha(\mathrm{diag}(t, t^{-1}))$ does not depend on the choice of $\varphi_\alpha$, and $\langle \alpha, \alpha^\vee \rangle = 2$.
4. The element $n_\alpha = \varphi_\alpha \left(\begin{smallmatrix} 0 & 1 \\ -1 & 0 \end{smallmatrix}\right)$ normalizes $T$. It acts on $X$ by $s_\alpha(\chi) = \chi - \langle \chi, \alpha^\vee \rangle \alpha$ and on $X^\vee$ by $s_{\alpha^\vee}(\lambda) = \lambda - \langle \alpha, \lambda \rangle \alpha^\vee$.
5. The group $G$ is generated by $T$ and the subgroups $U_\alpha$ for $\alpha \in R$, and $\dim G = r + |R|$.

The cocharacter $\alpha^\vee$ is the *coroot* of $\alpha$. We write $R^\vee = \{\alpha^\vee : \alpha \in R\}$.

Lean: not stated yet

*Proof sketch.* Let $T_\alpha$ be the reduced connected component of $\ker \alpha$, a subtorus of $T$ of codimension 1, and let $G_\alpha = C_G(T_\alpha)$. The centralizer of a torus in a reductive group is reductive ([Spr98], Chapter 7), so $G_\alpha$ is a reductive group with maximal torus $T$. Its Lie algebra is the subspace of $\mathfrak{g}$ fixed by $T_\alpha$, that is,
$$\mathrm{Lie}(G_\alpha) = \mathfrak{t} \oplus \bigoplus_{\beta \in R \cap \mathbb{Q}\alpha} \mathfrak{g}_\beta,$$
because a character is trivial on $T_\alpha$ if and only if it lies in $\mathbb{Q}\alpha$. The center of $G_\alpha$ contains $T_\alpha$, of dimension $r - 1$, so the semisimple rank of $G_\alpha$ is at most 1. It is not 0, since then $G_\alpha$ would be a torus by Theorem 3.1.6, while $\mathrm{Lie}(G_\alpha) \ne \mathfrak{t}$. Thus $G_\alpha$ has semisimple rank 1, and Theorem 3.2.4 applies to it. Its roots are $R \cap \mathbb{Q} \alpha$, so this set is $\{\pm \alpha\}$, and each root space has dimension 1. This proves 1, and it gives $U_\alpha$ and $\varphi_\alpha$. The uniqueness statements are proved in [Mil17], Chapter 21. For 4, the element $\left(\begin{smallmatrix} 0 & 1 \\ -1 & 0 \end{smallmatrix}\right)$ normalizes the diagonal torus of $SL_2$ and inverts it. So $n_\alpha$ normalizes $T = T_\alpha \cdot \alpha^\vee(\mathbb{G}_m)$, centralizes $T_\alpha$ and inverts $\alpha^\vee$. The map $s_\alpha$ is the only automorphism of $X$ with these two properties: it is the identity on the characters that vanish on $\alpha^\vee$ and sends $\alpha$ to $-\alpha$, and these characters together with $\alpha$ span $X \otimes \mathbb{Q}$. The formula for $s_{\alpha^\vee}$ follows by duality.

For 5, let $H$ be the subgroup generated by $T$ and the $U_\alpha$. It is smooth and connected, because it is generated by smooth connected subgroups (Chapter 1). Its Lie algebra contains $\mathfrak{t}$ and every $\mathfrak{g}_\alpha$, so $\mathrm{Lie}(H) = \mathfrak{g}$ and $\dim H = \dim G$. As $G$ is connected, $H = G$. The dimension formula follows from 1 and the decomposition of $\mathfrak{g}$. $\square$

**Example 3.2.6 (the coroots of $GL_n$).** Let $G = GL_n$, let $\alpha = e_i - e_j$, and let $e_1^*, \dots, e_n^*$ be the basis of $X^\vee$ dual to $e_1, \dots, e_n$, so that $e_i^*(t)$ is the diagonal matrix with $t$ in place $i$ and $1$ elsewhere. Let $\varphi_\alpha : SL_2 \to GL_n$ send $\left(\begin{smallmatrix} a & b \\ c & d \end{smallmatrix}\right)$ to the matrix that equals the identity outside the rows and columns $i, j$ and has entries $a, b, c, d$ in the places $(i,i), (i,j), (j,i), (j,j)$. Then $u_\alpha(x) = 1 + x E_{ij}$, and $t \, u_\alpha(x) \, t^{-1} = 1 + t_i t_j^{-1} x E_{ij}$ as required. The coroot is $\alpha^\vee = e_i^* - e_j^*$, and $\langle \alpha, \alpha^\vee \rangle = 1 + 1 = 2$. The element $n_\alpha$ is the matrix of the linear map $e_i \mapsto -e_j$, $e_j \mapsto e_i$ on the standard basis, a permutation matrix with one sign. Conjugation by $n_\alpha$ exchanges $t_i$ and $t_j$. On characters, $s_\alpha(e_i) = e_i - (e_i - e_j) = e_j$, as the formula of Theorem 3.2.5 predicts.

For $SL_2$ itself, $\varphi_\alpha$ is the identity, and the coroot of $\alpha = 2\chi$ is the cocharacter $\chi^\vee : t \mapsto \mathrm{diag}(t, t^{-1})$, which generates $X^\vee$. For $PGL_2$, $\varphi_\alpha$ is the projection $SL_2 \to PGL_2$, with kernel $\mu_2$. Its coroot is the image of $t \mapsto \mathrm{diag}(t, t^{-1})$. The cocharacter $\lambda : t \mapsto \mathrm{diag}(t, 1)$ generates $X_*(T)$, and $\mathrm{diag}(t, t^{-1}) = t^{-1} \cdot \mathrm{diag}(t^2, 1)$ is equal to $\lambda(t^2)$ modulo scalars. So $\alpha^\vee = 2\lambda$.

### Commutators of root subgroups

The root subgroups do not commute in general, but their commutators are controlled by the roots.

**Proposition 3.2.7 (Chevalley's commutator formula).** Let $\alpha, \beta \in R$ with $\beta \ne \pm \alpha$. There are constants $c_{ij} \in k$, for the pairs of integers $i, j > 0$ with $i\alpha + j\beta \in R$, such that
$$u_\alpha(x) \, u_\beta(y) \, u_\alpha(x)^{-1} \, u_\beta(y)^{-1} = \prod_{i, j > 0, \ i\alpha + j\beta \in R} u_{i\alpha + j\beta}(c_{ij} x^i y^j)$$
for all $x, y$, where the product is taken in a fixed order. In particular $U_\alpha$ and $U_\beta$ commute if $\alpha + \beta$ is not a root and no other combination $i\alpha + j\beta$ with $i, j > 0$ is a root.

Lean: not stated yet

*Proof sketch.* The commutator map $U_\alpha \times U_\beta \to G$ takes values in the subgroup $U_{(\alpha, \beta)}$ generated by the $U_{i\alpha + j\beta}$, which is a unipotent group normalized by $T$ and isomorphic as a variety to the product of its root groups ([Spr98], Chapter 8). Equivariance under $T$ forces the coordinate of the commutator in $U_{i\alpha+j\beta}$ to be a polynomial in $x, y$ of weight $i\alpha + j\beta$, hence a multiple of $x^i y^j$. For the values of the constants with a Chevalley basis, see Steinberg, *Lectures on Chevalley Groups* (Yale, 1967). $\square$

**Example 3.2.8 (commutators in $GL_n$).** Let $i, j, l$ be distinct and $u_{ij}(x) = 1 + x E_{ij}$. A direct computation with $E_{ij} E_{jl} = E_{il}$ and $E_{jl} E_{ij} = 0$ gives
$$u_{ij}(x) \, u_{jl}(y) \, u_{ij}(x)^{-1} \, u_{jl}(y)^{-1} = u_{il}(xy).$$
This is the formula of Proposition 3.2.7 for $\alpha = e_i - e_j$ and $\beta = e_j - e_l$, with $\alpha + \beta = e_i - e_l$ and $c_{11} = 1$. If $j \ne m$ and $i \ne l$, then $u_{ij}(x)$ and $u_{ml}(y)$ commute, and indeed $(e_i - e_j) + (e_m - e_l)$ is not a root.
