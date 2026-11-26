---
title: Compact Lie groups and complex reductive groups
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Compact Lie groups and complex reductive groups

A compact connected Lie group has maximal tori, roots and a Weyl group, and its irreducible representations are classified by highest weights, as for split reductive groups. The reason is that every compact Lie group $K$ is the group of real points of a unique complex reductive group $K_\mathbb{C}$, and $K$ and $K_\mathbb{C}$ have the same representations. This section states these facts, proves the integration formula of Weyl in outline, and uses it to give a complete proof of the Weyl character formula for compact groups. We follow [Kna02], Chapters 4 and 5. Throughout, $K$ is a compact connected Lie group with Lie algebra $\mathfrak{k}$, and $dg$ is its Haar probability measure.

### The Lie algebra of a compact group

**Proposition 4.6.1 (compact Lie algebras are reductive).** There is an inner product on $\mathfrak{k}$ that is invariant under $\mathrm{Ad}(K)$. For it, every $\mathrm{ad}\, X$ is skew-symmetric. The Lie algebra is $\mathfrak{k} = \mathfrak{z} \oplus [\mathfrak{k}, \mathfrak{k}]$, where $\mathfrak{z}$ is the center, and the Killing form of $[\mathfrak{k}, \mathfrak{k}]$ is negative definite. In particular $[\mathfrak{k}, \mathfrak{k}]$ is semisimple.

Lean: not stated yet

*Proof.* Proposition 4.5.4, applied to the real representation $\mathrm{Ad}$ with a real inner product in place of a Hermitian one, gives the invariant inner product. Differentiating $\langle \mathrm{Ad}(\exp tX) Y, \mathrm{Ad}(\exp tX) Z \rangle = \langle Y, Z \rangle$ at $t = 0$ gives $\langle [X, Y], Z \rangle + \langle Y, [X, Z] \rangle = 0$. So if $\mathfrak{a}$ is an ideal, its orthogonal complement $\mathfrak{a}^\perp$ is an ideal. By induction on the dimension, $\mathfrak{k}$ is a direct sum of ideals $\mathfrak{a}_i$ that have no nonzero proper ideals. Each $\mathfrak{a}_i$ is either abelian of dimension $1$ or simple. The abelian ones span $\mathfrak{z}$, and the simple ones span $[\mathfrak{k}, \mathfrak{k}]$. Finally, $\mathrm{ad}\, X$ is skew-symmetric, so its eigenvalues are imaginary and $B(X, X) = \mathrm{tr}((\mathrm{ad}\, X)^2) = - \| \mathrm{ad}\, X \|^2 \le 0$, with equality only if $X \in \mathfrak{z}$. $\square$

Conversely, if a real semisimple Lie algebra has a negative definite Killing form, then its adjoint group is compact, since it is a closed subgroup of the orthogonal group of $-B$. Such Lie algebras are called *compact*. The theorem of Weyl says that a compact connected Lie group with semisimple Lie algebra has finite fundamental group, so its universal cover is again compact ([Kna02], Chapter 4).

### Maximal tori and roots

A *torus* in $K$ is a compact connected abelian subgroup. The exponential map identifies a torus of dimension $r$ with $\mathfrak{t} / \Lambda \cong (\mathbb{R}/\mathbb{Z})^r$, where $\Lambda = \ker(\exp|_\mathfrak{t})$ is a lattice. A *maximal torus* is a torus not contained in a larger one. By Example 4.5.9, the group $X^*(T) = \mathrm{Hom}(T, U(1))$ of continuous characters is a lattice of rank $r$, and $X_*(T) = \mathrm{Hom}(U(1), T) = \Lambda$.

**Theorem 4.6.2 (the maximal torus theorem).** Let $T \subset K$ be a maximal torus. Every element of $K$ is conjugate to an element of $T$, and every maximal torus of $K$ is conjugate to $T$. The exponential map $\mathfrak{k} \to K$ is surjective.

Lean: not stated yet

The proof in [Kna02], Chapter 4, shows that the map $K/T \times T \to K$, $(gT, t) \mapsto g t g^{-1}$, has nonzero degree, by the Lefschetz fixed point formula or by the integration formula below. So it is surjective. This is the analogue of the conjugacy of Borel subgroups in Theorem 1.6.6. The difference is that in a compact group every element is semisimple, so every element lies in a torus.

Let $T$ be a maximal torus. The complexified Lie algebra $\mathfrak{k}_\mathbb{C} = \mathfrak{k} \otimes_\mathbb{R} \mathbb{C}$ is a representation of $T$ by $\mathrm{Ad}$, so it is a direct sum of weight spaces $\mathfrak{k}_{\mathbb{C}, \alpha}$ for $\alpha \in X^*(T)$, by Proposition 4.5.4 and Lemma 4.5.5 applied to the abelian group $T$. The weight $0$ gives $\mathfrak{t}_\mathbb{C}$, because $T$ is maximal. The nonzero weights are the *roots* of $(K, T)$, and they form a set $R(K, T)$ with $R = -R$, since $\mathfrak{k}_\mathbb{C}$ has a complex conjugation that commutes with $T$. The group $W(K, T) = N_K(T) / T$ is the *Weyl group*. It is finite, since $N_K(T)$ is compact and $T$ is its identity component.

**Theorem 4.6.3 (the root datum of a compact group).** Each root space is a line. For each root $\alpha$ there is a coroot $\alpha^\vee \in X_*(T)$ such that $(X^*(T), R(K, T), X_*(T), R^\vee)$ is a reduced root datum. The Weyl group $W(K, T)$ acts faithfully on $T$, and it is the Weyl group of this root datum.

Lean: not stated yet

The proof in [Kna02], Chapters 4 and 5, uses the subgroup of $K$ whose Lie algebra is $\mathfrak{t} + \mathfrak{k} \cap (\mathfrak{k}_{\mathbb{C}, \alpha} + \mathfrak{k}_{\mathbb{C}, -\alpha})$. It is a compact group of rank $1$ and has $SU(2)$ or $SO(3)$ as its derived group. The coroot is the cocharacter $U(1) \to T$ given by the diagonal torus of this $SU(2)$, and the reflection $s_\alpha$ is given by the element $\left( \begin{smallmatrix} 0 & 1 \\ -1 & 0 \end{smallmatrix} \right)$ of $SU(2)$. This mirrors the role of the groups of semisimple rank $1$ in Chapter 3.

**Example 4.6.4 (the unitary group).** Let $K = U(n)$, and let $T$ be the diagonal subgroup, the torus of the matrices $\mathrm{diag}(z_1, \dots, z_n)$ with $|z_i| = 1$. Then $X^*(T) = \mathbb{Z}^n$, by $\lambda \mapsto (z \mapsto z_1^{\lambda_1} \cdots z_n^{\lambda_n})$. The Lie algebra $\mathfrak{u}(n)$ is the space of skew-Hermitian matrices, and $\mathfrak{u}(n)_\mathbb{C} = \mathfrak{gl}_n(\mathbb{C})$, because every complex matrix is $A + iB$ with $A$ and $B$ skew-Hermitian in a unique way. So the roots are $e_i - e_j$ for $i \neq j$, with root spaces $\mathbb{C} E_{ij}$, and the coroots are $e_i^* - e_j^*$. The normalizer of $T$ consists of the monomial unitary matrices, so $W = S_n$. This is the root datum of $GL_n$ from Chapter 3. Every unitary matrix is diagonalizable by a unitary matrix, which is Theorem 4.6.2 for $U(n)$. In the same way $SU(n)$ has the root datum of $SL_n$, and $SO(3) \cong SU(2) / \{\pm 1\}$ has the root datum of $PGL_2$.

The theorem of the highest weight holds for $K$ with the same statement as Theorem 4.2.9. Choose a positive system $R^+ \subset R(K, T)$. A weight $\lambda \in X^*(T)$ is dominant if $\langle \lambda, \alpha^\vee \rangle \ge 0$ for all $\alpha > 0$.

**Theorem 4.6.5 (highest weights for compact groups).** For each dominant $\lambda \in X^*(T)$ there is an irreducible representation of $K$ with highest weight $\lambda$, unique up to isomorphism, and every irreducible representation of $K$ arises in this way for exactly one $\lambda$.

Lean: not stated yet

The uniqueness and the dominance of the highest weight follow as in Section 4.2, with $\mathfrak{k}_\mathbb{C}$ in place of the root groups. [Kna02], Chapter 5, gives two proofs of existence. One integrates to $K$ the representation of $[\mathfrak{k}, \mathfrak{k}]_\mathbb{C}$ with highest weight $\lambda$ from Chapter 2. The other, due to Weyl, uses Theorem 4.5.8. The quotient $A_{\lambda+\rho} / A_\rho$ lies in $\mathbb{Z}[X^*(T)]^W$, so by Theorem 4.6.2 it extends to a continuous class function $\varphi$ on $K$. The proof of Theorem 4.6.8 below does not use existence, and it shows that $A_\rho \chi|_T = A_{\mu+\rho}$ for each irreducible character $\chi$ with highest weight $\mu$. If $\lambda$ were missing, $\varphi$ would have norm $1$ and be orthogonal to all characters, by Theorem 4.6.6, which contradicts part 4 of Theorem 4.5.8.

### The integration formula and the character formula

The roots of $K$ are characters of $T$, so we write $e^\alpha$ for the function $t \mapsto \alpha(t)$ on $T$, and we use the notation $A_\mu$ of Section 4.3 for functions on $T$. The function $|\Delta|^2 = \prod_{\alpha \in R} (1 - e^\alpha)$ on $T$ is real and $\ge 0$, because $1 - e^{-\alpha} = \overline{1 - e^\alpha}$ on $T$, so it equals $\prod_{\alpha > 0} |1 - e^{-\alpha}|^2$. By Theorem 4.3.3 we have $|\Delta|^2 = |A_\rho|^2$, and this makes sense even if $\rho \notin X^*(T)$, since $e^{-\rho} A_\rho = \prod_{\alpha>0}(1 - e^{-\alpha})$ is a function on $T$.

**Theorem 4.6.6 (Weyl integration formula).** For every continuous function $f$ on $K$,
$$\int_K f(g) \, dg = \frac{1}{|W|} \int_T |\Delta(t)|^2 \int_K f(g t g^{-1}) \, dg \, dt.$$
In particular, if $f$ is a class function, then $\int_K f \, dg = \frac{1}{|W|} \int_T f(t) |\Delta(t)|^2 \, dt$.

Lean: not stated yet

*Outline of the proof.* We follow [Kna02], Chapter 8. Consider the map $\psi : K/T \times T \to K$, $\psi(gT, t) = g t g^{-1}$. Let $\mathfrak{p}$ be the orthogonal complement of $\mathfrak{t}$ in $\mathfrak{k}$ for an invariant inner product, so that $\mathfrak{p}$ is the tangent space of $K/T$ at $eT$. A computation with left translations shows that the Jacobian of $\psi$ at $(gT, t)$, measured with invariant volume forms, is
$$\det\left( \mathrm{Ad}(t^{-1}) - 1 \right)\big|_{\mathfrak{p}} = \prod_{\alpha \in R} (\alpha(t)^{-1} - 1) = \prod_{\alpha \in R} (1 - \alpha(t)),$$
since $\mathfrak{p}_\mathbb{C} = \bigoplus_{\alpha \in R} \mathfrak{k}_{\mathbb{C}, \alpha}$ and $R = -R$. This is $|\Delta(t)|^2$. The regular elements, those $t$ with $\alpha(t) \neq 1$ for all $\alpha$, form an open dense subset of $T$, and over the regular set $\psi$ is a covering of degree $|W|$, because $g t g^{-1} = g' t' g'^{-1}$ forces $t' = w t$ for some $w \in W$. The change of variables formula then gives the theorem, after a check that the singular set has measure zero. $\square$

**Example 4.6.7 (the group $SU(2)$).** Let $K = SU(2)$, with $T = \{ t_\theta = \mathrm{diag}(e^{i\theta}, e^{-i\theta}) \}$, $W = \{1, s\}$ and $s(t_\theta) = t_{-\theta}$. The roots are $\pm \alpha$ with $\alpha(t_\theta) = e^{2i\theta}$, so
$$|\Delta(t_\theta)|^2 = (1 - e^{2i\theta})(1 - e^{-2i\theta}) = 2 - 2 \cos 2\theta = 4 \sin^2 \theta.$$
Every element of $SU(2)$ is conjugate to $t_\theta$ for exactly one $\theta \in [0, \pi]$. For a class function $f$, Theorem 4.6.6 and the symmetry $\theta \mapsto -\theta$ give
$$\int_{SU(2)} f(g) \, dg = \frac{1}{2} \cdot \frac{1}{2\pi} \int_0^{2\pi} f(t_\theta) \, 4 \sin^2 \theta \, d\theta = \frac{2}{\pi} \int_0^\pi f(t_\theta) \sin^2 \theta \, d\theta.$$
So the image of the Haar measure on the space $[0, \pi]$ of conjugacy classes is $\frac{2}{\pi} \sin^2 \theta \, d\theta$. Exercise 9 derives this measure directly from the sphere $S^3$. The character of $\mathrm{Sym}^n \mathbb{C}^2$ is $\chi_n(t_\theta) = \sin((n+1)\theta) / \sin \theta$, by Theorem 4.4.1, and these functions are orthonormal for this measure, as Corollary 4.5.7 predicts. The Sato and Tate conjecture, now a theorem, says that for an elliptic curve $E$ over $\mathbb{Q}$ without complex multiplication, the angles $\theta_p \in [0, \pi]$ defined by $a_p(E) = 2 \sqrt{p} \cos \theta_p$ are equidistributed for this measure.

**Theorem 4.6.8 (Weyl character formula for compact groups).** Let $V$ be an irreducible representation of $K$ with highest weight $\lambda$. Then $A_\rho \, \chi_V|_T = A_{\lambda + \rho}$.

Lean: not stated yet

*Proof.* Let $f = A_\rho \, \chi_V|_T$, an element of $\mathbb{Z}[X']$. By Proposition 4.1.4, which holds for $K$ with the same proof, the character $\chi_V|_T$ is invariant under $W$, and $A_\rho$ is anti-invariant, so $f$ is anti-invariant. By Lemma 4.3.2, $f = \sum_\nu c_\nu A_\nu$ with integers $c_\nu$ and $\nu$ strictly dominant. The highest weight $\lambda$ has multiplicity $1$, and every other weight is below $\lambda$, as in Theorem 4.2.4. So $e^{\lambda + \rho}$ is the largest term of $f$, it has coefficient $1$, and $c_{\lambda + \rho} = 1$. Now we use the orthogonality relations. The functions $e^{-\rho} A_\nu = \sum_w \varepsilon(w) e^{w \nu - \rho}$ on $T$ are sums of $|W|$ distinct characters of $T$ with coefficients $\pm 1$, and for different strictly dominant $\nu$ the characters involved are different. By Corollary 4.5.7 and Theorem 4.6.6,
$$1 = \int_K |\chi_V|^2 \, dg = \frac{1}{|W|} \int_T |\chi_V(t)|^2 |e^{-\rho} A_\rho(t)|^2 \, dt = \frac{1}{|W|} \int_T \Big| \sum_\nu c_\nu e^{-\rho} A_\nu(t) \Big|^2 dt = \sum_\nu c_\nu^2,$$
where the last step uses the orthonormality of the characters of $T$. Since $c_{\lambda + \rho} = 1$, all other $c_\nu$ vanish. $\square$

This proof is complete except for the integration formula and the existence of the irreducible representation with highest weight $\lambda$. Through the next theorem, it also proves Theorem 4.3.4 over $\mathbb{C}$.

### Complexification

**Theorem 4.6.9 (complexification).** Let $K$ be a compact Lie group.
1. Let $\mathcal{O}(K)$ be the space of matrix coefficients of the finite-dimensional complex representations of $K$, a $\mathbb{C}$-algebra under pointwise multiplication. It is a finitely generated Hopf algebra, and $K_\mathbb{C} = \mathrm{Spec}\, \mathcal{O}(K)$ is a reductive algebraic group over $\mathbb{C}$.
2. Evaluation at points gives an injective map $K \to K_\mathbb{C}(\mathbb{C})$, whose image is a maximal compact subgroup and is Zariski dense. The group $K_\mathbb{C}$ is connected if and only if $K$ is connected.
3. Restriction from $K_\mathbb{C}$ to $K$ is an equivalence between the category of finite-dimensional representations of $K_\mathbb{C}$ and the category of finite-dimensional continuous representations of $K$.
4. If $T$ is a maximal torus of $K$, then $T_\mathbb{C}$ is a maximal torus of $K_\mathbb{C}$, and $K$ and $K_\mathbb{C}$ have the same root datum.
5. Conversely, every connected reductive group $G$ over $\mathbb{C}$ has a maximal compact subgroup $K \subset G(\mathbb{C})$, unique up to conjugacy, and $K_\mathbb{C} \cong G$.

Lean: not stated yet

The theorem is due to Chevalley, and part 3 is a form of the duality of Tannaka. For proofs see Bröcker and tom Dieck, *Representations of Compact Lie Groups*, Chapter III. The algebra $\mathcal{O}(K)$ is finitely generated by Corollary 4.5.10: if $\pi$ is a faithful representation, then the matrix coefficients of $\pi$ and of $\det^{-1} \pi$ generate it. The comultiplication comes from $f(gh) = \sum_i f_i(g) f'_i(h)$. By part 1 of Theorem 4.5.8, $\mathcal{O}(K)$ is dense in $C(K)$. Over $\mathbb{R}$ the same construction gives a real form of $K_\mathbb{C}$ whose group of real points is $K$, so every compact Lie group is the group of real points of an algebraic group over $\mathbb{R}$.

**Example 4.6.10 (compact forms of the classical groups).** The following pairs $(K, K_\mathbb{C})$ correspond under Theorem 4.6.9.
- $U(1)$ and $\mathbb{G}_m$. More generally, the compact torus $(\mathbb{R}/\mathbb{Z})^r$ and the split torus $\mathbb{G}_m^r$, with the same character lattice $\mathbb{Z}^r$.
- $U(n)$ and $GL_n$, and $SU(n)$ and $SL_n$. Here $\mathfrak{u}(n) \otimes \mathbb{C} = \mathfrak{gl}_n(\mathbb{C})$ by Example 4.6.4.
- $SO(n)$, the rotation group of $\mathbb{R}^n$, and $SO_n$ over $\mathbb{C}$.
- The compact symplectic group $Sp(n) = U(2n) \cap Sp_{2n}(\mathbb{C})$, the unitary group of $\mathbb{H}^n$, and $Sp_{2n}$.
- $PU(n) = U(n) / U(1)$ and $PGL_n$, and $SO(3) \cong PU(2)$ and $PGL_2 \cong SO_3$.

In each case the inclusion of $K$ into $K_\mathbb{C}(\mathbb{C})$ is the obvious one, and the polar decomposition $G(\mathbb{C}) = K \cdot \exp(i \mathfrak{k})$ shows that $K$ is a maximal compact subgroup. Mathlib has the groups `Matrix.unitaryGroup`, `Matrix.specialUnitaryGroup`, `Matrix.orthogonalGroup` and `Matrix.symplecticGroup`, but not the theory of this section.

**Corollary 4.6.11 (the unitary trick).** Let $G$ be a connected reductive group over $\mathbb{C}$ with maximal compact subgroup $K$. A subspace of a finite-dimensional representation of $G$ is stable under $G$ if and only if it is stable under $K$. Every finite-dimensional representation of $G$ is a direct sum of irreducible representations, and its restriction to $K$ is irreducible if and only if it is irreducible for $G$.

Lean: not stated yet

*Proof.* The stabilizer of a subspace is a closed algebraic subgroup of $G$. If it contains $K$, it contains the Zariski closure of $K$, which is $G$ by part 2 of Theorem 4.6.9. This gives the first statement, and the others follow from Proposition 4.5.4. $\square$

The Zariski density of $K$ has a direct proof on Lie algebras. Let $H$ be the Zariski closure of $K$, an algebraic subgroup of $G$. Its Lie algebra is a complex subspace of $\mathfrak{g}$ that contains $\mathfrak{k}$, so it contains $\mathfrak{k} + i \mathfrak{k} = \mathfrak{g}$. Thus $\dim H = \dim G$, and $H = G$ since $G$ is connected. This argument is the original unitary trick of Weyl. It gives a proof of Theorem 4.2.11 over $\mathbb{C}$ that does not use the theorem of Weyl on Lie algebras.

**Remark 4.6.12 (real forms and the dual group).** A *real form* of a complex reductive group $G$ is a reductive group $G_0$ over $\mathbb{R}$ with $G_0 \otimes_\mathbb{R} \mathbb{C} \cong G$. By Theorem 4.6.9, every $G$ has a *compact real form*, unique up to isomorphism, whose group of real points is compact. For example, $SL_2$ has the real forms $SL_2$ over $\mathbb{R}$, with $SL_2(\mathbb{R})$ not compact, and the group of quaternions of norm one, with real points $SU(2)$. The connected reductive groups $G_0$ over $\mathbb{R}$ with $G_0(\mathbb{R})$ compact are the anisotropic ones, such as $SO(x^2 + y^2 + z^2)$ of Remark 1.6.12. Chapter 3 describes the forms of a group by the action of Galois on its based root datum. Compact forms of dual groups occur in two places later. A unitary unramified representation of $GL_n(\mathbb{Q}_p)$ is tempered if and only if its Satake parameter, a semisimple conjugacy class in the dual group $GL_n(\mathbb{C})$ of Chapter 5, meets the compact form $U(n)$, and the Ramanujan conjecture predicts this for the local components of cuspidal automorphic representations. The Sato and Tate distribution of Example 4.6.7 is the image of the Haar measure of $SU(2)$, the compact form of the dual group $SL_2(\mathbb{C})$ of $PGL_2$.
