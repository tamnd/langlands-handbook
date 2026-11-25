---
title: The reciprocity map of a uniformizer
nodes: []
sources: [Ser67, Mil20]
status: drafted
drafted_by: writer
reviewed_by: []
---
## The reciprocity map of a uniformizer

The field $K_\varpi$ is totally ramified and $K^{ur}$ is unramified, so $K_\varpi \cap K^{ur} = K$. Both fields are Galois over $K$. Thus the restrictions give an isomorphism
$$\mathrm{Gal}(K_\varpi K^{ur} / K) \cong \mathrm{Gal}(K_\varpi / K) \times \mathrm{Gal}(K^{ur} / K) \cong \mathcal{O}_K^\times \times \hat{\mathbb{Z}},$$
where the second isomorphism is $\chi_\varpi$ on the first factor and $\Phi^a \mapsto a$ on the second factor.

**Definition 3.4.1 (the map $\mathrm{rec}_\varpi$).** For $x = u \varpi^m$ with $u \in \mathcal{O}_K^\times$ and $m \in \mathbb{Z}$, let $\mathrm{rec}_\varpi(x)$ be the element of $\mathrm{Gal}(K_\varpi K^{ur} / K)$ that acts on $K^{ur}$ as $\Phi^m$ and on each $\Lambda_{f,n}$ as $[u]_f$.

Lean: not stated yet

Thus $\mathrm{rec}_\varpi(\varpi)$ is trivial on $K_\varpi$ and is the geometric Frobenius on $K^{ur}$. A unit $u$ acts trivially on $K^{ur}$, and on $K_\varpi$ it acts by $\chi_\varpi^{-1}(u)$. The definition does not depend on $f \in \mathcal{F}_\varpi$, because $[1]_{g,f}$ commutes with $[u]$. In the arithmetic normalization of [Mil20], the map is $x \mapsto \mathrm{rec}_\varpi(x^{-1})$: it acts on $K^{ur}$ as $\mathrm{Frob}^m$ and on $K_\varpi$ as $[u^{-1}]_f$.

The map $\mathrm{rec}_\varpi$ is defined with a choice of $\varpi$. The main theorem of this section says that neither the field $K_\varpi K^{ur}$ nor the map depends on this choice. The proof needs the completion of $K^{ur}$.

Let $\hat K^{ur}$ be the completion of $K^{ur}$, and let $B$ be its ring of integers. The residue field of $B$ is $\bar k$, and $\varpi$ is a uniformizer of $B$. The arithmetic Frobenius of $K^{ur}$ is an isometry, so it extends to a continuous automorphism $\sigma$ of $\hat K^{ur}$ and of $B$. It acts on $\bar k$ as $x \mapsto x^q$. For a power series $\theta$ with coefficients in $B$, let $\theta^\sigma$ be the series obtained by applying $\sigma$ to the coefficients.

**Lemma 3.4.2.** The automorphism $\sigma$ of $B$ has the following properties.
1. The fixed ring $B^{\sigma = 1}$ is $\mathcal{O}_K$.
2. The map $b \mapsto \sigma(b) - b$ from $B$ to $B$ is surjective.
3. For each $u \in \mathcal{O}_K^\times$ there is $\varepsilon \in B^\times$ with $\sigma(\varepsilon) = u \varepsilon$.

Lean: not stated yet

*Proof.* On the residue field $\bar k$, the map $\sigma$ is $x \mapsto x^q$. Its fixed field is $k$. The map $x \mapsto x^q - x$ is surjective on $\bar k$, and the map $x \mapsto x^{q-1}$ is surjective on $\bar k^\times$, because $\bar k$ is algebraically closed.

For part 1, let $b \in B$ with $\sigma(b) = b$. Its reduction is in $k$, so there is $a_0 \in \mathcal{O}_K$ with $b \equiv a_0$ modulo $\varpi$. Then $(b - a_0)/\varpi$ is again fixed by $\sigma$. By induction $b \equiv a_0 + a_1 \varpi + \dots + a_r \varpi^r$ modulo $\varpi^{r+1}$ for all $r$, with $a_i \in \mathcal{O}_K$. Thus $b \in \mathcal{O}_K$, because $\mathcal{O}_K$ is complete.

For part 2, let $c \in B$. Choose $b_0 \in B$ with $\sigma(b_0) - b_0 \equiv c$ modulo $\varpi$, by the surjectivity on $\bar k$. Then $c - (\sigma(b_0) - b_0) = \varpi c_1$ with $c_1 \in B$. Repeat with $c_1$ to get $b_1$, and so on. The series $b = \sum_i b_i \varpi^i$ converges, and $\sigma(b) - b = c$ because $\sigma$ is continuous and fixes $\varpi$.

For part 3, we solve $\sigma(\varepsilon)/\varepsilon = u$ in the same way. Choose $\varepsilon_0 \in B^\times$ whose reduction $x$ satisfies $x^{q-1} = \bar u$. Then $\sigma(\varepsilon_0) / \varepsilon_0 \equiv u$ modulo $\varpi$. Suppose that $\varepsilon_r$ is a unit with $u_r = u \, \varepsilon_r / \sigma(\varepsilon_r) \in 1 + \varpi^{r+1} B$. Write $u_r = 1 + \varpi^{r+1} c$. By part 2 there is $b$ with $\sigma(b) - b \equiv c$ modulo $\varpi$. Let $\varepsilon_{r+1} = \varepsilon_r (1 + \varpi^{r+1} b)$. Then
$$\frac{\sigma(\varepsilon_{r+1})}{\varepsilon_{r+1}} = \frac{\sigma(\varepsilon_r)}{\varepsilon_r} \cdot \frac{1 + \varpi^{r+1} \sigma(b)}{1 + \varpi^{r+1} b} \equiv \frac{u}{u_r} (1 + \varpi^{r+1} c) \equiv u \pmod{\varpi^{r+2}}.$$
The units $\varepsilon_r$ converge to a unit $\varepsilon$, and $\sigma(\varepsilon) = u \varepsilon$ by continuity. $\square$

**Theorem 3.4.3 (independence of the uniformizer).** Let $\varpi$ and $\varpi'$ be two uniformizers of $K$. Then $K_{\varpi'} K^{ur} = K_\varpi K^{ur}$, and $\mathrm{rec}_{\varpi'} = \mathrm{rec}_\varpi$ on this field.

Lean: not stated yet

*Proof.* Write $\varpi' = u \varpi$ with $u \in \mathcal{O}_K^\times$, and let $f \in \mathcal{F}_\varpi$. Choose $\varepsilon$ as in Lemma 3.4.2, part 3.

Step 1. There is $\theta \in B[[X]]$ with $\theta(X) \equiv \varepsilon X$ modulo degree 2 and $\theta^\sigma = \theta \circ [u]_f$. We build polynomials $\theta_r$ of degree at most $r$ with $\theta_r^\sigma \equiv \theta_r \circ [u]_f$ modulo degree $r + 1$. Let $\theta_1 = \varepsilon X$. Then $\theta_1^\sigma = \sigma(\varepsilon) X = u \varepsilon X$, and $\theta_1 \circ [u]_f \equiv \varepsilon u X$ modulo degree 2. Given $\theta_r$, let $b \in B$ be the coefficient of $X^{r+1}$ in $\theta_r^\sigma - \theta_r \circ [u]_f$, and put $\theta_{r+1} = \theta_r + c X^{r+1}$. Since $[u]_f \equiv uX$, the condition modulo degree $r+2$ is
$$\sigma(c) - u^{r+1} c = -b.$$
Write $c = \varepsilon^{r+1} c'$. Then $\sigma(c) = u^{r+1} \varepsilon^{r+1} \sigma(c')$, so the condition is $\sigma(c') - c' = -b / (u\varepsilon)^{r+1}$. By Lemma 3.4.2, part 2, it has a solution $c' \in B$. The limit of the $\theta_r$ is $\theta$.

Step 2. Let $h = \theta^\sigma \circ f \circ \theta^{-1}$, where $\theta^{-1}$ is the inverse of $\theta$ for composition. It exists because $\varepsilon$ is a unit. We claim that $h \in \mathcal{F}_{\varpi'}$. First, $h$ has coefficients in $\mathcal{O}_K$. Indeed, $[u]_f$ and $f$ have coefficients in $\mathcal{O}_K$ and commute, so
$$h^\sigma = \theta^{\sigma^2} \circ f \circ (\theta^\sigma)^{-1} = \theta^\sigma \circ [u]_f \circ f \circ [u]_f^{-1} \circ \theta^{-1} = \theta^\sigma \circ f \circ \theta^{-1} = h,$$
and Lemma 3.4.2, part 1, applies to each coefficient. Second, the linear term of $h$ is $\sigma(\varepsilon) \varpi \varepsilon^{-1} X = u \varpi X = \varpi' X$. Third, modulo $\varpi$ the series $f$ is $X^q$, and for a power series $\psi$ over $\bar k$ one has $\psi(X)^q = \psi^\sigma(X^q)$, because $\sigma$ is the $q$-th power on $\bar k$. Thus modulo $\varpi$,
$$h(X) \equiv \theta^\sigma\big((\theta^{-1}(X))^q\big) = \theta^\sigma \big( (\theta^{-1})^\sigma (X^q) \big) = (\theta \circ \theta^{-1})^\sigma (X^q) = X^q.$$

Step 3. The series $\theta$ is an isomorphism from $F_f$ to $F_h$ over $B$, and $\theta \circ [a]_f \circ \theta^{-1} = [a]_h$ for $a \in \mathcal{O}_K$. Let $H(X, Y) = \theta(F_f(\theta^{-1}(X), \theta^{-1}(Y)))$. Using $\theta^\sigma = \theta \circ [u]_f$ and the fact that $[u]_f$ is an endomorphism of $F_f$, one gets $H^\sigma = H$, so $H$ has coefficients in $\mathcal{O}_K$. It is congruent to $X + Y$. Using $\theta^{-1} \circ \theta^\sigma = [u]_f$, one checks that $h(H(X, Y)) = H(h(X), h(Y))$: both sides equal $\theta^\sigma(F_f(f(\theta^{-1} X), f(\theta^{-1} Y)))$. By Theorem 3.2.3, $H = F_h$. The same argument applies to $\theta \circ [a]_f \circ \theta^{-1}$.

Step 4. The fields. Let $n \ge 1$, and let $M_n = \hat K^{ur} K_{\varpi,n}$, a complete field. For $\lambda \in \Lambda_{f,n}$ the series $\theta(\lambda)$ converges in $M_n$, and by Step 3 it is a $\varpi^n$-torsion point of $F_h$. The map $\theta$ is injective, since it has an inverse. By the Weierstrass preparation theorem, the zeros of $h^{(n)}$ of positive valuation in an algebraic closure of $M_n$ are the roots of a polynomial over $\mathcal{O}_K$ of degree $q^n$. Thus they are the $q^n$ elements of $\Lambda_{h,n}$, and $\theta(\Lambda_{f,n}) = \Lambda_{h,n}$. So $K_{\varpi',n} \subset M_n$. An element of $M_n$ that is separable algebraic over $K$ lies in the dense subfield $E_n = K^{ur} K_{\varpi,n}$, by Krasner's lemma: an element of $E_n$ close enough to it generates a field that contains it. Hence $K_{\varpi',n} \subset K^{ur} K_{\varpi,n}$ for all $n$.

Step 5. The action. Let $\tau = \mathrm{rec}_\varpi(\varpi')$. It is an isometry of $K_\varpi K^{ur}$, so it extends continuously to each $M_n$, and on $\hat K^{ur}$ it is $\sigma^{-1}$. For $\lambda \in \Lambda_{f,n}$,
$$\tau(\theta(\lambda)) = \theta^{\sigma^{-1}}(\tau(\lambda)) = \theta^{\sigma^{-1}}([u]_f(\lambda)) = \theta(\lambda),$$
where the last step is the identity $\theta^\sigma = \theta \circ [u]_f$ with $\sigma^{-1}$ applied to its coefficients. Thus $\tau$ fixes $\Lambda_{h,n}$ and is trivial on $K_{\varpi'}$. It acts as $\Phi$ on $K^{ur}$. So $\tau$ agrees with $\mathrm{rec}_{\varpi'}(\varpi')$ on $K_{\varpi'} K^{ur}$. Next let $v$ be a unit, and $\tau_v = \mathrm{rec}_\varpi(v)$. It is trivial on $\hat K^{ur}$, so it fixes the coefficients of $\theta$, and by Step 3
$$\tau_v(\theta(\lambda)) = \theta([v]_f(\lambda)) = [v]_h(\theta(\lambda)).$$
So $\tau_v$ agrees with $\mathrm{rec}_{\varpi'}(v)$ on $K_{\varpi'} K^{ur}$. The group $K^\times$ is generated by $\varpi'$ and the units, so $\mathrm{rec}_\varpi(x)$ restricts to $\mathrm{rec}_{\varpi'}(x)$ for all $x$. By symmetry $K_\varpi K^{ur} \subset K_{\varpi'} K^{ur}$, so the two fields are equal and the two maps are equal. $\square$

**Corollary 3.4.4.** Let $n \ge 1$ and $u \in U^{(n)}$. Then $K_{u \varpi, n} = K_{\varpi, n}$.

Lean: not stated yet

*Proof.* Let $\varpi' = u\varpi$. In the group $\mathrm{Gal}(K_\varpi K^{ur}/K) \cong \mathcal{O}_K^\times \times \hat{\mathbb{Z}}$, the subgroup that fixes $K_{\varpi,n}$ is $U^{(n)} \times \hat{\mathbb{Z}}$. It is the closure of $\mathrm{rec}_\varpi(\langle \varpi \rangle \times U^{(n)})$. In the same way, the subgroup that fixes $K_{\varpi',n}$ is the closure of $\mathrm{rec}_{\varpi'}(\langle \varpi' \rangle \times U^{(n)})$, which is the closure of $\mathrm{rec}_\varpi(\langle \varpi' \rangle \times U^{(n)})$ by Theorem 3.4.3. As $u \in U^{(n)}$, the subgroups $\langle \varpi \rangle \times U^{(n)}$ and $\langle u\varpi \rangle \times U^{(n)}$ of $K^\times$ are equal. Thus the two fields have the same fixing subgroup, and they are equal. $\square$
