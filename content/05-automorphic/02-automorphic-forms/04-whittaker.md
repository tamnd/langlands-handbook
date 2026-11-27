---
title: The Fourier-Whittaker expansion and Whittaker models
nodes: []
sources: [JL70]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## The Fourier-Whittaker expansion and Whittaker models

The Fourier coefficients $\varphi_\xi$ of Section 2.3 are not independent: the diagonal matrix $a(\xi)$ moves the character $\psi(\xi x)$ to $\psi(x)$, so all of them are values of one function $W_\varphi$, the Whittaker function of $\varphi$. This section proves the expansion $\varphi(g) = \sum_{\xi \in \mathbb{Q}^\times}W_\varphi(a(\xi)g)$ of a cusp form. For $\phi_f$ it is the $q$-expansion of $f$. The function $W_\varphi$ transforms on the left by the character $\psi$ of $U(\mathbb{A})$, and the theory of local Whittaker models says that, for an irreducible representation, there is at most one such function up to a scalar at each place. We state this theorem at the finite places and prove it at the real place, where it reduces to an ordinary differential equation.

### The Whittaker function of a cusp form

**Definition 2.4.1 (Whittaker function).** The *Whittaker function* of a continuous function $\varphi$ on $G(\mathbb{Q})\backslash G(\mathbb{A})$ is
$$W_\varphi(g) = \varphi_1(g) = \int_{\mathbb{Q}\backslash\mathbb{A}}\varphi(u(x)g)\,\psi(-x)\,dx,$$
with the character $\psi$ of Definition 2.3.8.

Lean: not formalized

It satisfies $W_\varphi(u(x)g) = \psi(x)W_\varphi(g)$ for $x \in \mathbb{A}$, and $\varphi \mapsto W_\varphi$ commutes with right translations and right derivatives.

**Lemma 2.4.2 (all coefficients from one).** For $\xi \in \mathbb{Q}^\times$ we have $\varphi_\xi(g) = W_\varphi(a(\xi)g)$.

Lean: not formalized

*Proof.* Since $a(\xi)u(x) = u(\xi x)a(\xi)$ and $\varphi$ is left invariant under $a(\xi) \in G(\mathbb{Q})$,
$$W_\varphi(a(\xi)g) = \int\varphi(a(\xi)u(\xi^{-1}x)g)\,\psi(-x)\,dx = \int\varphi(u(\xi^{-1}x)g)\,\psi(-x)\,dx.$$
The substitution $x \mapsto \xi x$ preserves $\mathbb{Q}$ and the measure $dx$, by the product formula, and gives $\varphi_\xi(g)$. $\square$

**Theorem 2.4.3 (Fourier-Whittaker expansion).** Let $\varphi \in \mathcal{A}_0(G)$. Then
$$\varphi(g) = \sum_{\xi \in \mathbb{Q}^\times}W_\varphi(a(\xi)g)$$
for all $g \in G(\mathbb{A})$. The series converges absolutely and uniformly on compact sets. In particular $\varphi = 0$ if and only if $W_\varphi = 0$.

Lean: not formalized

*Proof.* By Lemma 2.3.9, $\varphi(g) = \sum_{\xi}\varphi_\xi(g)$, and $\varphi_0 = \varphi_U = 0$. Lemma 2.4.2 turns the sum into the claimed one. On a compact set $C$ the finite components of $g \in C$ lie in finitely many cosets $g_fK'$, so one integer $M$ works for all $g \in C$. For the uniform bound, let $X_g = \mathrm{Ad}(g_\infty^{-1})E$ with $E$ as in the proof of Theorem 2.3.10. Then $\varphi_\xi(u(s)g)$ has derivative $(X_g\varphi)_\xi(g) = 2\pi i\xi\,\varphi_\xi(g)$ at $s = 0$, and $X_g$ depends continuously on $g$. The argument of that proof, with $X_g^2$ in place of $E^2$, gives $|\varphi_\xi(g)| \le C_C|\xi|^{-2}$ for $g \in C$. If $W_\varphi = 0$, the expansion gives $\varphi = 0$. $\square$

So a cusp form is determined by its Whittaker function, and the Whittaker function is determined by its values on the elements $a(y)g$ with $y \in \mathbb{A}^\times$ and $g \in K$. This is the adelic form of the statement that a cusp form is determined by its Fourier coefficients.

**Example 2.4.4 (the Whittaker function of $\phi_f$).** Let $f = \sum_{n \ge 1}a_nq^n \in S_k(\Gamma_0(N))$ and $\varphi = \phi_f$. For $t > 0$ and $\xi \in \mathbb{Q}$, take the fundamental domain $[0, 1) \times \widehat{\mathbb{Z}}$ of $\mathbb{Q}\backslash\mathbb{A}$. Since $u(\widehat{\mathbb{Z}}) \subseteq K_0(N)$ and $\phi_f(u(x)a(t)) = t^{k/2}f(x + it)$ for $x \in \mathbb{R}$,
$$\varphi_\xi(a(t)) = t^{k/2}\int_0^1 f(x + it)e^{-2\pi i\xi x}\,dx \cdot \int_{\widehat{\mathbb{Z}}}\psi_f(-\xi x_f)\,dx_f.$$
The second integral is $1$ if $\psi_f$ is trivial on $\xi\widehat{\mathbb{Z}}$, that is if $\xi \in \mathbb{Z}$, and $0$ otherwise. The first is $a_\xi e^{-2\pi\xi t}$ for $\xi \in \mathbb{Z}$, with $a_\xi = 0$ for $\xi \le 0$. Now let $y \in \mathbb{A}^\times$. Since $\mathbb{A}^\times = \mathbb{Q}^\times\mathbb{R}_{>0}\widehat{\mathbb{Z}}^\times$, we can write $y = \xi(t, u)$ with $\xi \in \mathbb{Q}^\times$, $t > 0$ and $u \in \widehat{\mathbb{Z}}^\times$, and $a(u) \in K_0(N)$. By Lemma 2.4.2, $W_\varphi(a(y)) = \varphi_\xi(a(t))$. Here $\xi > 0$ if and only if $y_\infty > 0$, and $\xi$ is a positive integer $n$ if and only if also $y_f\widehat{\mathbb{Z}} = n\widehat{\mathbb{Z}}$. Hence
$$W_{\phi_f}(a(y)) = \begin{cases} a_n n^{-k/2}y_\infty^{k/2}e^{-2\pi y_\infty} & \text{if } y_\infty > 0 \text{ and } y_f \in n\widehat{\mathbb{Z}}^\times \text{ with } n \in \mathbb{Z}_{\ge 1}, \\ 0 & \text{otherwise.} \end{cases}$$
For $g_\infty \in G(\mathbb{R})^+$ the expansion of Theorem 2.4.3 reads $\phi_f(g_\infty) = \sum_{n \ge 1}\phi_{f,n}(g_\infty)$, and for $g_\infty = u(x)a(t)$ it is $t^{k/2}\sum_n a_n e^{2\pi i n(x + it)} = t^{k/2}f(x + it)$. So the Fourier-Whittaker expansion of $\phi_f$ is the $q$-expansion of $f$.

Suppose now that $f$ is a normalized eigenform of all the $T_n$. Then $n \mapsto a_n$ is multiplicative, and the formula factors as $W_{\phi_f}(a(y)) = W_\infty(a(y_\infty))\prod_p W_p(a(y_p))$ with
$$W_\infty(a(y)) = y^{k/2}e^{-2\pi y}\ (y > 0), \qquad W_p(a(y)) = a_{p^m}p^{-mk/2} \text{ for } m = v_p(y) \ge 0,$$
and $W_\infty(a(y)) = 0$ for $y < 0$, $W_p(a(y)) = 0$ for $v_p(y) < 0$. For $p \nmid N$, write $a_p = p^{(k-1)/2}(\alpha_p + \beta_p)$ with $\alpha_p\beta_p = 1$. The recursion $a_{p^{m+1}} = a_pa_{p^m} - p^{k-1}a_{p^{m-1}}$ gives
$$W_p(a(p^m)) = p^{-m/2}\,\frac{\alpha_p^{m+1} - \beta_p^{m+1}}{\alpha_p - \beta_p}, \tag{2.4.1}$$
for $\alpha_p \ne \beta_p$, and $p^{-m/2}(m + 1)\alpha_p^m$ for $\alpha_p = \beta_p$. So the global Whittaker function is a product of local functions, and at $p \nmid N$ the local function depends only on $\{\alpha_p, \beta_p\}$.

### Local Whittaker models at the finite places

**Definition 2.4.5 (local Whittaker functional).** Let $p$ be a prime and $(\pi, V)$ a smooth representation of $G(\mathbb{Q}_p)$. A *Whittaker functional* on $\pi$ is a linear form $\Lambda : V \to \mathbb{C}$ with $\Lambda(\pi(u(x))v) = \psi_p(x)\Lambda(v)$ for $x \in \mathbb{Q}_p$ and $v \in V$. If $\Lambda \ne 0$, the map $v \mapsto W_v$, $W_v(g) = \Lambda(\pi(g)v)$, is a nonzero intertwining map from $\pi$ to the space of smooth functions $W$ on $G(\mathbb{Q}_p)$ with $W(u(x)g) = \psi_p(x)W(g)$, on which $G(\mathbb{Q}_p)$ acts by right translation. Its image is a *Whittaker model* of $\pi$. The representation is *generic* if it has a nonzero Whittaker functional.

Lean: `Langlands.IsWhittakerFunctional` and `Langlands.IsGeneric`

This is Volume 6, Definition 1.7.1, for $n = 2$ and the character $\psi_p$. The Whittaker functionals on $\pi$ form the dual of the space $V_{U, \psi_p}$ of twisted coinvariants, the quotient of $V$ by the span of the vectors $\pi(u(x))v - \psi_p(x)v$.

**Theorem 2.4.6 (local uniqueness of Whittaker models).** Let $\pi$ be an irreducible admissible representation of $G(\mathbb{Q}_p)$. Then the space of Whittaker functionals on $\pi$ has dimension at most $1$. It has dimension $1$ if and only if $\pi$ is infinite-dimensional.

Lean: not proved; `Langlands.IsGeneric` states the existence part

*Outline of the proof.* The theorem is Volume 6, Theorems 1.7.2 and 1.7.4, and the proof for $GL_2$ is in [JL70], Chapter I. A finite-dimensional irreducible representation is $\chi \circ \det$, and a Whittaker functional $\Lambda$ on it satisfies $\Lambda(v) = \Lambda(\pi(u(x))v) = \psi_p(x)\Lambda(v)$, so $\Lambda = 0$. For uniqueness there are two proofs. The first, of Gelfand and Kazhdan, uses the anti-involution $\iota(g) = w\,{}^tg\,w^{-1}$, which fixes $U$ and the character $\psi_p$. One shows that each distribution on $G(\mathbb{Q}_p)$ that transforms under $U \times U$ on the left and the right by $\psi_p \otimes \psi_p^{-1}$ is invariant under $\iota$, by the Bruhat decomposition, and that this implies $\dim\mathrm{Hom}_U(\pi, \psi_p) \cdot \dim\mathrm{Hom}_U(\tilde\pi, \psi_p^{-1}) \le 1$; then one uses $\tilde\pi \cong \pi \circ \iota$. The second, of Jacquet and Langlands, restricts $\pi$ to the mirabolic group $P = \{\left(\begin{smallmatrix} a & b \\ 0 & 1 \end{smallmatrix}\right)\}$, shows that the restriction contains the compactly induced representation $\mathrm{ind}_U^P\psi_p$ with multiplicity one, and deduces the Kirillov model of Volume 6, Theorem 1.7.5. Chapter 3 gives the second proof. $\square$

**Example 2.4.7 (the unramified Whittaker function).** Let $\pi_p$ be an irreducible unramified principal series of $G(\mathbb{Q}_p)$ with Satake parameters $\alpha, \beta$, and let $v^0$ be a nonzero vector fixed by $K_p$. Let $W^0$ be the Whittaker function of $v^0$ for a nonzero Whittaker functional. For $x \in \mathbb{Z}_p$ the element $u(x)$ lies in $K_p$ and $a(y)u(x) = u(yx)a(y)$, so
$$W^0(a(y)) = W^0(a(y)u(x)) = \psi_p(yx)W^0(a(y)).$$
If $v_p(y) < 0$ there is $x \in \mathbb{Z}_p$ with $\psi_p(yx) \ne 1$, so $W^0(a(y)) = 0$. Shintani's formula, proved in Chapter 3, says that $W^0(1) \ne 0$ and, normalized by $W^0(1) = 1$,
$$W^0(a(p^m)) = p^{-m/2}\,\frac{\alpha^{m+1} - \beta^{m+1}}{\alpha - \beta}, \qquad m \ge 0.$$
This is (2.4.1). By local uniqueness, the local factor $W_p$ of Example 2.4.4 at $p \nmid N$ had to be a multiple of $W^0$, and it is $W^0$ for the local component of $\phi_f$ at $p$, with the Satake parameters $\alpha_p, \beta_p$.

### Whittaker models at the real place

At the real place we work with $(\mathfrak{g}, K_\infty)$-modules, and the growth condition is essential.

**Definition 2.4.8 (Whittaker functions at the real place).** Let $\mathcal{W}(\psi_\infty)$ be the space of the smooth functions $W$ on $G(\mathbb{R})$ with $W(u(x)g) = e^{2\pi ix}W(g)$, which are $K_\infty$-finite on the right, $Z(\mathfrak{g})$-finite, and of moderate growth: $|W(g)| \le C\|g\|_\infty^r$ for some $C$ and $r$. It is a $(\mathfrak{g}, K_\infty)$-module under right derivatives and right translations. A *Whittaker model* of a $(\mathfrak{g}, K_\infty)$-module $V$ is an injective map of $(\mathfrak{g}, K_\infty)$-modules from $V$ to $\mathcal{W}(\psi_\infty)$.

Lean: not formalized

Let $W_{\kappa, \mu}(t)$ be the Whittaker function of Whittaker and Watson, *A Course of Modern Analysis*, Chapter XVI. It is the solution of Whittaker's equation
$$\frac{d^2w}{dt^2} + \left(-\frac{1}{4} + \frac{\kappa}{t} + \frac{1/4 - \mu^2}{t^2}\right)w = 0$$
with $W_{\kappa, \mu}(t) \sim t^\kappa e^{-t/2}$ as $t \to \infty$. Each solution that is not a multiple of $W_{\kappa, \mu}$ grows like a nonzero multiple of $t^{-\kappa}e^{t/2}$. Two special cases are $W_{\kappa, \kappa - 1/2}(t) = t^\kappa e^{-t/2}$ and $W_{0, \mu}(t) = (t/\pi)^{1/2}K_\mu(t/2)$, where $K_\mu$ is the modified Bessel function.

**Proposition 2.4.9 (Whittaker functions of a given weight).** Let $W \in \mathcal{W}(\psi_\infty)$ have weight $m$, be invariant under $Z(\mathbb{R})^+$, and satisfy $\Delta W = \lambda W$ with $\lambda = s(1 - s)$. Then there is $c \in \mathbb{C}$ with
$$W\left(u(x)\,\mathrm{diag}(y^{1/2}, y^{-1/2})\,\kappa_\theta\right) = c\,e^{2\pi ix}\,W_{m/2,\, s - 1/2}(4\pi y)\,e^{im\theta}, \qquad y > 0.$$
If also $LW = 0$, then $m = k$ with $\lambda = \frac{k}{2}(1 - \frac{k}{2})$ and $W = c'e^{2\pi ix}y^{k/2}e^{-2\pi y}e^{ik\theta}$. If $RW = 0$, then $W = 0$ on $G(\mathbb{R})^+$.

Lean: not formalized

*Proof.* By the transformation laws, $W = e^{2\pi ix}w(y)e^{im\theta}$ on $G(\mathbb{R})^+$ for a smooth function $w$ on $(0, \infty)$. By Lemma 2.1.7,
$$\Delta W = e^{2\pi ix}e^{im\theta}\left(-y^2(w'' - 4\pi^2w) - 2\pi m\,y\,w\right),$$
so $\Delta W = \lambda W$ says $w'' = (4\pi^2 - 2\pi m/y - \lambda/y^2)w$. In the variable $t = 4\pi y$ this is Whittaker's equation with $\kappa = m/2$ and $\frac{1}{4} - \mu^2 = \lambda = \frac{1}{4} - (s - \frac{1}{2})^2$, so $\mu = s - \frac{1}{2}$. By Lemma 2.2.2 the height of $u(x)\mathrm{diag}(y^{1/2}, y^{-1/2})$ is at most a power of $y$ for $y \ge 1$ and bounded $x$, so moderate growth forbids the growing solution, and $w = cW_{m/2, s - 1/2}(4\pi y)$. If $LW = 0$, Lemma 2.1.7 gives $2\pi yw + yw' - \frac{m}{2}w = 0$, so $w = c'y^{m/2}e^{-2\pi y}$, and then $\lambda = \frac{m}{2}(1 - \frac{m}{2})$ by (2.1.1). If $RW = 0$, the same lemma gives $-2\pi yw + yw' + \frac{m}{2}w = 0$, so $w = c'y^{-m/2}e^{2\pi y}$, which grows exponentially; so $c' = 0$. $\square$

For a holomorphic form the function $W_\infty(a(y)) = y^{k/2}e^{-2\pi y}$ of Example 2.4.4 is the case $LW = 0$; note that $a(y) = y^{1/2}\mathrm{diag}(y^{1/2}, y^{-1/2})$ and $\phi_f$ is invariant under $Z(\mathbb{R})^+$. For a Maass form of eigenvalue $\frac{1}{4} + r^2$ with $s = \frac{1}{2} + ir$, the case $m = 0$ gives $W_{0, ir}(4\pi y) = 2y^{1/2}K_{ir}(2\pi y)$, and the Fourier-Whittaker expansion becomes the classical expansion $u(z) = \sum_{n \ne 0}\rho(n)\sqrt{y}K_{ir}(2\pi|n|y)e^{2\pi inx}$.

**Theorem 2.4.10 (uniqueness of Whittaker models at the real place).** Let $V$ be an irreducible admissible $(\mathfrak{g}, K_\infty)$-module. Then the space of maps of $(\mathfrak{g}, K_\infty)$-modules from $V$ to $\mathcal{W}(\psi_\infty)$ has dimension at most $1$, and it is $0$ if $V$ is finite-dimensional.

Lean: not formalized

*Proof.* By Schur's lemma $Z$ and $\Delta$ act on $V$ by scalars, and after a twist by a power of $|\det|$ we may assume that $Z$ acts by $0$, so that the image of $V$ consists of functions invariant under $Z(\mathbb{R})^+$. Let $\Phi : V \to \mathcal{W}(\psi_\infty)$ be a map of $(\mathfrak{g}, K_\infty)$-modules. For $g \in G(\mathbb{R})^+$ we have $\Phi(v)(g\varepsilon) = \Phi(\varepsilon v)(g)$, and $G(\mathbb{R}) = G(\mathbb{R})^+ \sqcup G(\mathbb{R})^+\varepsilon$. So $\Phi$ is determined by the map $\Phi^+$ that sends $v$ to the restriction of $\Phi(v)$ to the open set $G(\mathbb{R})^+$, and $\Phi^+$ commutes with $\mathfrak{g}$ and $SO(2)$. We use Proposition 2.1.13.

Suppose first that $V$ is irreducible under $(\mathfrak{g}, SO(2))$, and let $v \in V_m$ be nonzero. Then $V = U(\mathfrak{g}_\mathbb{C})v$, so $\Phi^+$ is determined by $\Phi^+(v)$, and by Proposition 2.4.9 $\Phi^+(v)$ is $c$ times a fixed function. So $\Phi \mapsto c$ is an injective linear map, and the dimension is at most $1$. If $V$ is finite-dimensional, it has a vector $v$ of highest weight, with $Rv = 0$, so $\Phi^+(v) = 0$ by Proposition 2.4.9, and $\Phi = 0$.

Otherwise $V = V^+ \oplus \varepsilon V^+$ with $V^+ \cong D_k^+$ and $\varepsilon V^+ \cong D_k^-$. Let $u$ be a nonzero vector of weight $-k$ in $\varepsilon V^+$, so that $Ru = 0$. By Proposition 2.4.9, $\Phi^+(u) = 0$, so $\Phi^+$ vanishes on $\varepsilon V^+ = U(\mathfrak{g}_\mathbb{C})u$. On $V^+ = U(\mathfrak{g}_\mathbb{C})v_k$, with $v_k$ of weight $k$, the map $\Phi^+$ is determined by $\Phi^+(v_k)$, which is $c$ times a fixed function. So again $\Phi$ is determined by one scalar. $\square$

**Remark 2.4.11 (the growth condition).** Without the growth condition the theorem is false. On a module of type 1 of Theorem 2.1.12 both solutions of Whittaker's equation give maps into functions with $W(u(x)g) = e^{2\pi ix}W(g)$, so the space of algebraic Whittaker functionals has dimension $2$. For smooth representations of $G(\mathbb{R})$, uniqueness holds for continuous Whittaker functionals, by Shalika's theorem, and continuity corresponds to moderate growth.
