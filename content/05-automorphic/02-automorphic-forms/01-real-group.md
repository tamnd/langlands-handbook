---
title: The group at infinity and its Lie algebra
nodes: []
sources: []
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## The group at infinity and its Lie algebra

An automorphic form is a function on $GL_2(\mathbb{A})$, and its behaviour at the real place is controlled by two finiteness conditions: it is finite under a maximal compact subgroup of $GL_2(\mathbb{R})$, and it is finite under the center of the universal enveloping algebra. This section fixes the notation for $GL_2(\mathbb{R})$, writes the Lie algebra in the basis $H, R, L$ of raising and lowering operators, computes the Casimir operator in coordinates, and classifies the irreducible $(\mathfrak{g}, K)$-modules by their weights. The example to keep in mind is the function $g \mapsto f(g i) j(g, i)^{-k} (\det g)^{k/2}$ for a holomorphic function $f$ on $\mathbb{H}$: the operator $L$ kills it exactly when $f$ is holomorphic, and the Casimir operator then acts on it by $\frac{k}{2}(1 - \frac{k}{2})$.

### Notation

**Definition 2.1.1 (the standard elements).** Let $G = GL_2$. For $x \in \mathbb{R}$, $y \in \mathbb{R}^\times$ and $\theta \in \mathbb{R}$ put
$$u(x) = \begin{pmatrix} 1 & x \\ 0 & 1 \end{pmatrix}, \quad a(y) = \begin{pmatrix} y & 0 \\ 0 & 1 \end{pmatrix}, \quad \kappa_\theta = \begin{pmatrix} \cos\theta & \sin\theta \\ -\sin\theta & \cos\theta \end{pmatrix}, \quad \varepsilon = \begin{pmatrix} -1 & 0 \\ 0 & 1 \end{pmatrix}, \quad w = \begin{pmatrix} 0 & -1 \\ 1 & 0 \end{pmatrix}.$$
Let $U$ be the group of the matrices $u(x)$, $B$ the group of upper triangular matrices and $Z$ the center of $G$. Let $G(\mathbb{R})^+$ be the subgroup of the $g \in G(\mathbb{R})$ with $\det g > 0$, let $Z(\mathbb{R})^+$ be the group of the scalar matrices $r \cdot 1$ with $r > 0$, and let $K_\infty = O(2)$. Then $SO(2) = \{\kappa_\theta\}$ and $O(2) = SO(2) \sqcup SO(2)\varepsilon$. For $g = \left(\begin{smallmatrix} a & b \\ c & d \end{smallmatrix}\right) \in G(\mathbb{R})^+$ and $z \in \mathbb{H}$ put $g z = (az + b)/(cz + d)$ and $j(g, z) = cz + d$.

We use the letter $U$ for the unipotent group, and keep $N$ for the level. The rotation $\kappa_\theta$ fixes $i$, and $j(\kappa_\theta, i) = \cos\theta - i\sin\theta = e^{-i\theta}$.

**Lemma 2.1.2 (Iwasawa decomposition).** Each $g \in G(\mathbb{R})^+$ is uniquely a product
$$g = u(x) \begin{pmatrix} y^{1/2} & 0 \\ 0 & y^{-1/2} \end{pmatrix} z \, \kappa_\theta$$
with $x \in \mathbb{R}$, $y > 0$, $z \in Z(\mathbb{R})^+$ and $\theta \in \mathbb{R}/2\pi\mathbb{Z}$. In this decomposition $g i = x + iy$ and $\det g = z^2$. Also $G(\mathbb{R}) = G(\mathbb{R})^+ \sqcup G(\mathbb{R})^+\varepsilon$.

Lean: not formalized

*Proof.* Let $x + iy = g i$ and let $b$ be the product of the first two factors, so that $b i = x + iy$. Then $b^{-1}g$ fixes $i$ and has positive determinant. The stabilizer of $i$ in $SL_2(\mathbb{R})$ is $SO(2)$, so $b^{-1}g (\det g)^{-1/2} \in SO(2)$, and $b^{-1}g = z\kappa_\theta$ with $z = (\det g)^{1/2}$. The numbers $x, y$ are determined by $g i$, and then $z$ and $\kappa_\theta$ are determined. The last claim holds since $\det \varepsilon = -1$. $\square$

We call $(x, y, z, \theta)$ the Iwasawa coordinates of $g \in G(\mathbb{R})^+$. A function on $G(\mathbb{R})^+$ that is invariant under $Z(\mathbb{R})^+$ is a function of $(x, y, \theta)$.

### The Lie algebra and the raising and lowering operators

Let $\mathfrak{g} = \mathfrak{gl}_2(\mathbb{R})$ and $\mathfrak{g}_\mathbb{C} = \mathfrak{gl}_2(\mathbb{C})$. The group $G(\mathbb{R})$ acts on smooth functions on $G(\mathbb{R})$, or on $G(\mathbb{A})$, by right translation, $(\rho(h)F)(g) = F(gh)$. The derivative of this action is the action of $\mathfrak{g}$ by
$$(XF)(g) = \frac{d}{dt}\Big|_{t = 0} F(g \exp(tX)),$$
and it extends to a $\mathbb{C}$-linear action of $\mathfrak{g}_\mathbb{C}$ and to an action of the universal enveloping algebra $U(\mathfrak{g}_\mathbb{C})$. These operators commute with left translations.

**Definition 2.1.3 (the operators $H$, $R$, $L$, $Z$).** In $\mathfrak{g}_\mathbb{C}$ put
$$H = \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}, \quad R = \frac{1}{2}\begin{pmatrix} 1 & i \\ i & -1 \end{pmatrix}, \quad L = \frac{1}{2}\begin{pmatrix} 1 & -i \\ -i & -1 \end{pmatrix}, \quad Z = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}.$$
The operator $R$ is the *raising operator* and $L$ the *lowering operator*.

Lean: not formalized

The four elements are a basis of $\mathfrak{g}_\mathbb{C}$. Put $W = \left(\begin{smallmatrix} 0 & 1 \\ -1 & 0 \end{smallmatrix}\right)$, so that $\kappa_\theta = \exp(\theta W)$ and $H = -iW$. If $F(g\kappa_\theta) = e^{im\theta}F(g)$ for all $\theta$, then $HF = -i \frac{d}{d\theta}e^{im\theta}F = mF$. Such an $F$ has *weight* $m$.

**Lemma 2.1.4 (commutation relations).** The operators satisfy
$$[H, R] = 2R, \quad [H, L] = -2L, \quad [R, L] = H,$$
and $Z$ is central. Conjugation by $\varepsilon$ acts by $\mathrm{Ad}(\varepsilon)H = -H$, $\mathrm{Ad}(\varepsilon)R = L$, $\mathrm{Ad}(\varepsilon)L = R$ and $\mathrm{Ad}(\varepsilon)Z = Z$. Complex conjugation of the entries, which fixes $\mathfrak{g}$, sends $H$ to $-H$ and $R$ to $L$.

Lean: not formalized

*Proof.* Matrix multiplication gives $HR = R$ and $RH = -R$, so $[H, R] = 2R$. In the same way $HL = -L$ and $LH = L$. Next
$$RL = \frac{1}{2}\begin{pmatrix} 1 & -i \\ i & 1 \end{pmatrix}, \quad LR = \frac{1}{2}\begin{pmatrix} 1 & i \\ -i & 1 \end{pmatrix},$$
so $[R, L] = \left(\begin{smallmatrix} 0 & -i \\ i & 0 \end{smallmatrix}\right) = H$. Conjugation by $\varepsilon$ changes the sign of the two entries off the diagonal, and this sends $H$ to $-H$ and $R$ to $L$. Complex conjugation of the entries does the same. $\square$

So $H, R, L$ span a copy of $\mathfrak{sl}_2(\mathbb{C})$ in which $R$ raises the weight by $2$ and $L$ lowers it by $2$: if $F$ has weight $m$, then $H(RF) = RHF + 2RF = (m + 2)RF$.

**Definition 2.1.5 (Casimir operator).** The *Casimir operator* is the element
$$\Delta = -\frac{1}{4}\left(H^2 + 2RL + 2LR\right)$$
of $U(\mathfrak{g}_\mathbb{C})$.

Lean: not formalized

With $[R, L] = H$ the definition gives the two forms
$$\Delta = -RL - \frac{H^2}{4} + \frac{H}{2} = -LR - \frac{H^2}{4} - \frac{H}{2}. \tag{2.1.1}$$

**Proposition 2.1.6 (the center of the enveloping algebra).** The elements $Z$ and $\Delta$ lie in the center $Z(\mathfrak{g})$ of $U(\mathfrak{g}_\mathbb{C})$, and $Z(\mathfrak{g}) = \mathbb{C}[Z, \Delta]$ is a polynomial ring in them.

Lean: not formalized

*Proof.* The element $Z$ is central in $\mathfrak{g}_\mathbb{C}$. For $\Delta$ it suffices to check $[H, \Delta] = [R, \Delta] = 0$, since $[L, \Delta] = 0$ follows by conjugation with $\varepsilon$. The element $\Delta$ is a sum of products of weight $0$ for $\mathrm{ad}\,H$, so $[H, \Delta] = 0$. Next $[R, H^2] = -2RH - 2HR$, $[R, RL] = RH$ and $[R, LR] = HR$, so
$$[R, H^2 + 2RL + 2LR] = -2RH - 2HR + 2RH + 2HR = 0.$$
The equality $Z(\mathfrak{g}) = \mathbb{C}[Z, \Delta]$ is the case $n = 2$ of the Harish-Chandra isomorphism $Z(\mathfrak{g}) \cong S(\mathfrak{h})^{S_n}$ of Volume 7, Theorem 1.7.1: the image of $Z$ is $h_1 + h_2$ and the image of $\Delta$ is a polynomial of degree 2 in which $(h_1 - h_2)^2$ occurs, and these generate the symmetric polynomials in $h_1, h_2$. $\square$

### The operators in coordinates

Let $F$ be a smooth function on $G(\mathbb{R})^+$ that is invariant under $Z(\mathbb{R})^+$, written in the Iwasawa coordinates $(x, y, \theta)$ of Lemma 2.1.2.

**Lemma 2.1.7 (the operators as differential operators).** On such functions
$$R = e^{2i\theta}\left(iy\frac{\partial}{\partial x} + y\frac{\partial}{\partial y} - \frac{i}{2}\frac{\partial}{\partial\theta}\right), \qquad L = e^{-2i\theta}\left(-iy\frac{\partial}{\partial x} + y\frac{\partial}{\partial y} + \frac{i}{2}\frac{\partial}{\partial\theta}\right),$$
$H = -i\,\partial/\partial\theta$, and
$$\Delta = -y^2\left(\frac{\partial^2}{\partial x^2} + \frac{\partial^2}{\partial y^2}\right) + y\frac{\partial^2}{\partial x\,\partial\theta}.$$

Lean: not formalized

*Proof.* The formula for $H$ was proved after Definition 2.1.3. For the others it suffices to compute the right derivatives along the real elements $E = \left(\begin{smallmatrix} 0 & 1 \\ 0 & 0 \end{smallmatrix}\right)$ and $A = \frac{1}{2}\left(\begin{smallmatrix} 1 & 0 \\ 0 & -1 \end{smallmatrix}\right)$, since $R = A + \frac{i}{2}(E + E^t)$, $L = A - \frac{i}{2}(E + E^t)$ and $E + E^t = 2E - W$. Since $\kappa_\theta \exp(tX) = \exp(t\,\mathrm{Ad}(\kappa_\theta)X)\kappa_\theta$, one writes $\mathrm{Ad}(\kappa_\theta)X$ in the basis $E, A, W, Z$, and the derivatives along $E$ and $A$ of a function of $u(x)\mathrm{diag}(y^{1/2}, y^{-1/2})$ are $y\,\partial_x$ and $y\,\partial_y$. This is a calculation with $2 \times 2$ matrices, and [Bum97], Chapter 2, carries it out in the same coordinates. As a check, for $F = y^s e^{im\theta}$ the formulas give $RF = (s + \frac{m}{2})y^s e^{i(m+2)\theta}$ and $LF = (s - \frac{m}{2})y^s e^{i(m-2)\theta}$, so by (2.1.1)
$$\Delta F = \left(-\left(s - \tfrac{m}{2}\right)\left(s + \tfrac{m}{2} - 1\right) - \tfrac{m^2}{4} + \tfrac{m}{2}\right)F = s(1 - s)F,$$
which agrees with the last formula: $-y^2\partial_y^2 y^s = s(1 - s)y^s$ and the other terms vanish. $\square$

The term $y\,\partial^2/\partial x\partial\theta$ vanishes on functions of weight $0$, and on these $\Delta$ is the hyperbolic Laplacian of Volume 4, Definition 2.6.1, in the variable $z = x + iy$.

**Example 2.1.8 (holomorphic functions give lowest weight vectors).** Let $k \in \mathbb{Z}$, let $f$ be a smooth function on $\mathbb{H}$, and let
$$F_f(g) = f(g i)\, j(g, i)^{-k} (\det g)^{k/2}, \qquad g \in G(\mathbb{R})^+.$$
In the Iwasawa coordinates $j(g, i) = y^{-1/2} z e^{-i\theta}$ and $\det g = z^2$, so $F_f(g) = y^{k/2} f(x + iy) e^{ik\theta}$. The function $F_f$ has weight $k$ and is invariant under $Z(\mathbb{R})^+$. Lemma 2.1.7 gives
$$LF_f = -2i\,y^{k/2 + 1} \frac{\partial f}{\partial \bar z} e^{i(k - 2)\theta}, \qquad RF_f = y^{k/2}\left(iy\frac{\partial f}{\partial x} + y\frac{\partial f}{\partial y} + kf\right)e^{i(k+2)\theta}.$$
So $LF_f = 0$ exactly when $f$ is holomorphic. In that case $RF_f = y^{k/2}(2iyf' + kf)e^{i(k+2)\theta}$, and (2.1.1) gives
$$\Delta F_f = \left(-RL - \frac{H^2}{4} + \frac{H}{2}\right)F_f = \frac{k}{2}\left(1 - \frac{k}{2}\right)F_f.$$
The operator $R$ applied to $F_f$ corresponds to the Maass-Shimura operator $\frac{1}{2\pi i}\left(\frac{d}{dz} + \frac{k}{2iy}\right)$ up to a constant, which sends forms of weight $k$ to nonholomorphic forms of weight $k + 2$.

**Example 2.1.9 (Maass forms give weight $0$ vectors).** Let $u$ be a smooth function on $\mathbb{H}$ and $F(g) = u(g i)$. Then $F$ has weight $0$, $LF$ and $RF$ have weights $-2$ and $2$, and $\Delta F(g) = (\Delta_{\mathbb{H}} u)(g i)$, where $\Delta_{\mathbb{H}}$ is the hyperbolic Laplacian. If $\Delta_{\mathbb{H}} u = \lambda u$ with $\lambda = s(1 - s)$, then (2.1.1) gives $RLF = LRF = -\lambda F$.

### $(\mathfrak{g}, K)$-modules

The space of automorphic forms is not stable under right translation by $G(\mathbb{R})$, since a translate of a $K_\infty$-finite function need not be $K_\infty$-finite. It is stable under $\mathfrak{g}$ and $K_\infty$, and this structure is a $(\mathfrak{g}, K)$-module.

**Definition 2.1.10 ($(\mathfrak{g}, K)$-module).** Let $K$ be $O(2)$ or $SO(2)$. A $(\mathfrak{g}, K)$-*module* is a complex vector space $V$ with an action of $\mathfrak{g}_\mathbb{C}$ and an action of $K$ with these properties.
1. Each $v \in V$ lies in a finite-dimensional $K$-stable subspace on which $K$ acts continuously.
2. For $X$ in the Lie algebra of $K$, the derivative of the action of $K$ along $X$ is the action of $X \in \mathfrak{g}$.
3. For $k \in K$ and $X \in \mathfrak{g}_\mathbb{C}$, $k X k^{-1} v = (\mathrm{Ad}(k)X) v$.

The module is *admissible* if each irreducible representation of $K$ occurs in $V$ with finite multiplicity.

Lean: not formalized

For $K = SO(2)$ the first two conditions say that $V = \bigoplus_{m \in \mathbb{Z}} V_m$, where $\kappa_\theta$ acts on the *weight space* $V_m$ by $e^{im\theta}$ and $H$ acts on it by $m$. Admissibility says that each $V_m$ is finite-dimensional. An admissible module has countable dimension, so Schur's lemma holds for it: if it is irreducible, then $Z(\mathfrak{g})$ acts on it by scalars. The scalar of $Z$ gives the central character of the derivative of $Z(\mathbb{R})^+$, and we write $\lambda$ for the scalar of $\Delta$.

**Lemma 2.1.11 (weight vectors).** Let $V$ be a $(\mathfrak{g}, SO(2))$-module on which $\Delta$ acts by $\lambda$ and $Z$ by a scalar. Then $R V_m \subseteq V_{m+2}$ and $L V_m \subseteq V_{m-2}$, and on $V_m$
$$RL = -\lambda - \frac{m(m - 2)}{4}, \qquad LR = -\lambda - \frac{m(m + 2)}{4}.$$
For $v \in V_m$ the space $U(\mathfrak{g}_\mathbb{C})v$ has weight spaces of dimension at most $1$: its weight space of weight $m + 2j$ is spanned by $R^j v$ for $j \ge 0$ and by $L^{-j}v$ for $j < 0$.

Lean: not formalized

*Proof.* The first claim follows from $[H, R] = 2R$ and $[H, L] = -2L$, and the formulas follow from (2.1.1). By the Poincare-Birkhoff-Witt theorem $U(\mathfrak{g}_\mathbb{C})$ is spanned by the monomials $Z^a H^b R^c L^d$. On $v$ the factors $Z$ and $H$ act by scalars after $L^d$, and $R^c L^d v$ is a multiple of $R^{c-d}v$ or $L^{d-c}v$: by the formulas the operator $RL$ acts by a scalar on each weight space, so $R^c L^d v = R^{c-1}(RL)L^{d-1}v$ is a multiple of $R^{c-1}L^{d-1}v$, and induction on $\min(c, d)$ ends the proof. $\square$

The formulas say when $R$ or $L$ can kill a weight vector. Write $\lambda = s(1 - s)$ with $s \in \mathbb{C}$. Then on $V_m$
$$RL\big|_{V_m} = \left(s - \tfrac{m}{2}\right)\left(s + \tfrac{m}{2} - 1\right), \qquad LR\big|_{V_m} = \left(s + \tfrac{m}{2}\right)\left(s - \tfrac{m}{2} - 1\right). \tag{2.1.2}$$
So $L$ is injective on $V_m$ unless $m = 2s$ or $m = 2 - 2s$, and $R$ is injective on $V_m$ unless $m = -2s$ or $m = 2s - 2$.

**Theorem 2.1.12 (irreducible $(\mathfrak{g}, SO(2))$-modules).** Let $V$ be an irreducible $(\mathfrak{g}, SO(2))$-module on which $Z(\mathfrak{g})$ acts by scalars, with $\Delta = s(1 - s)$. Then the weights of $V$ lie in one class modulo $2$, each weight space has dimension at most $1$, and $V$ is of exactly one of these types.
1. The weights are all $m$ of one parity, and $2s$ is not an integer of that parity.
2. *Lowest weight $k$*: the weights are $k, k + 2, k + 4, \dots$ for an integer $k \ge 1$, and $\lambda = \frac{k}{2}(1 - \frac{k}{2})$. We write $D_k^+$ for this module.
3. *Highest weight $-k$*: the weights are $-k, -k - 2, \dots$ for an integer $k \ge 1$, and $\lambda = \frac{k}{2}(1 - \frac{k}{2})$. We write $D_k^-$ for this module.
4. *Finite-dimensional*: the weights are $1 - d, 3 - d, \dots, d - 1$ for an integer $d \ge 1$, and $\lambda = \frac{1 - d^2}{4}$.

Two irreducible modules with the same scalars of $Z(\mathfrak{g})$ and the same weights are isomorphic.

Lean: not formalized

*Proof.* Let $v \in V_m$ be nonzero. Since $V$ is irreducible, $V = U(\mathfrak{g}_\mathbb{C})v$, and Lemma 2.1.11 gives the first two claims. The set of weights is an interval $I$ in $m + 2\mathbb{Z}$, since $V_{m'} = 0$ implies $V_{m''} = 0$ for all $m''$ beyond $m'$ on the side away from $m$. Suppose that $I$ has a smallest element $n$. Then $L$ kills $V_n$, so $n = 2s$ or $n = 2 - 2s$ by (2.1.2), and in both cases $\lambda = s(1 - s) = \frac{n}{2}(1 - \frac{n}{2})$. Replace $s$ by $1 - s$ so that $n = 2s$. By (2.1.2) the operator $L$ also kills $V_{2 - n}$. If $n \le 0$, then $2 - n > n$, and either $2 - n \notin I$, so $I$ is finite with largest element $n' < 2 - n$, or the vector of weight $2 - n$ generates a proper submodule, which is impossible. In the first case $R$ kills $V_{n'}$, so $n' = -2s = -n$ or $n' = 2s - 2 = n - 2$; the second is less than $n$, so $n' = -n$ and $V$ is finite-dimensional with $d = 1 - n$, which is type 4. If $n \ge 1$, then $R$ is injective on $V_j$ for all $j \ge n$ by (2.1.2), so $I = \{n, n + 2, \dots\}$, which is type 2 with $k = n$. The case where $I$ has a largest element and no smallest one is symmetric and gives type 3. If $I$ is unbounded in both directions, then $R$ and $L$ are injective on all weight spaces, since a nonzero vector killed by $R$ or by $L$ would generate a proper submodule, and (2.1.2) says that no weight of $V$ is $\pm 2s$ or $2 \pm 2s$; this is type 1. For the last claim choose a nonzero $v_m$ in one weight space and put $v_{m + 2j} = R^j v_m$ and $v_{m - 2j} = L^j v_m$. By Lemma 2.1.11 the action of $R$, $L$, $H$, $Z$ in this basis depends only on the scalars and the weights, so two such modules are isomorphic. $\square$

The modules of type 1 and the modules $D_k^\pm$ are all infinite-dimensional. Section 2.6 realizes all four types inside principal series representations of $GL_2(\mathbb{R})$. For the group $O(2)$ we need one more step, since $\varepsilon$ exchanges the weights $m$ and $-m$.

**Proposition 2.1.13 (irreducible $(\mathfrak{g}, O(2))$-modules).** Let $V$ be an irreducible admissible $(\mathfrak{g}, O(2))$-module. Then either $V$ is irreducible as a $(\mathfrak{g}, SO(2))$-module, of type 1 or 4 of Theorem 2.1.12, or $V = V^+ \oplus \varepsilon V^+$ with $V^+ \cong D_k^+$ and $\varepsilon V^+ \cong D_k^-$ for some $k \ge 1$. In all cases each weight space of $V$ has dimension at most $1$.

Lean: not formalized

*Proof.* Let $v \in V_m$ be nonzero. By Lemma 2.1.11 the module $U(\mathfrak{g}_\mathbb{C})v$ has weight spaces of dimension at most $1$, and by (2.1.2) $R$ and $L$ fail to be injective on at most four weight spaces. So it has finitely many $(\mathfrak{g}, SO(2))$-submodules, and it contains an irreducible one, $W$. By Lemma 2.1.4 the space $\varepsilon W$ is a $(\mathfrak{g}, SO(2))$-submodule, with the weights of $W$ multiplied by $-1$. The sum $W + \varepsilon W$ and the intersection $W \cap \varepsilon W$ are stable under $\mathfrak{g}$ and $O(2)$, so $W + \varepsilon W = V$, and $W \cap \varepsilon W$ is $0$ or $V$. If it is $V$, then $V = W$ is irreducible under $(\mathfrak{g}, SO(2))$, and since $\varepsilon$ negates the weights, the set of weights is symmetric, which excludes the types 2 and 3. Otherwise $V = W \oplus \varepsilon W$. Suppose that $W$ is of type 1 or 4. Then the weights of $W$ and $\varepsilon W$ are the same, and the scalars of $Z(\mathfrak{g})$ agree since $\mathrm{Ad}(\varepsilon)$ fixes $Z$ and $\Delta$. By Theorem 2.1.12 there is an isomorphism $\psi : W \to \varepsilon W$ of $(\mathfrak{g}, SO(2))$-modules. The map $T = \varepsilon \circ \psi$ of $W$ to itself satisfies $T X = \mathrm{Ad}(\varepsilon)(X) T$, so $T^2$ commutes with $\mathfrak{g}$ and $SO(2)$ and is a scalar $c \ne 0$ by the last part of the proof of Theorem 2.1.12. Replace $\psi$ by $c^{-1/2}\psi$, so that $T^2 = 1$, that is $\psi\varepsilon\psi = \varepsilon$ on $W$. Then the graph $Y = \{w + \psi(w) : w \in W\}$ is stable under $\mathfrak{g}$ and $SO(2)$, and
$$\varepsilon(w + \psi(w)) = \psi(T w) + T w \in Y.$$
So $Y$ is a $(\mathfrak{g}, O(2))$-submodule with $0 \ne Y \ne V$, a contradiction. Hence $W$ is $D_k^+$ or $D_k^-$, and we may take $V^+$ to be the one of type 2. The weight spaces of $D_k^+$ and $D_k^-$ do not meet, so the last claim holds in all cases. $\square$
