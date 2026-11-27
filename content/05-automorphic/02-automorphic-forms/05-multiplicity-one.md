---
title: Multiplicity one
nodes: []
sources: [JL70]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Multiplicity one

By Proposition 2.3.17 the space $\mathcal{A}_0(G, \omega)$ is a direct sum of irreducible $(\mathfrak{g}, K_\infty) \times G(\mathbb{A}_f)$-modules, each with finite multiplicity. This section proves that each multiplicity is $0$ or $1$. The proof combines the Fourier-Whittaker expansion with local uniqueness at every place. The expansion says that a cusp form is determined by its Whittaker function, so an embedding of $\pi$ into the cusp forms gives a global Whittaker functional on $\pi$. Local uniqueness says that such functionals form a space of dimension at most $1$.

**Lemma 2.5.1 (Whittaker functions have moderate growth).** Let $\varphi \in \mathcal{A}_0(G)$ and $g_f \in G(\mathbb{A}_f)$. Then $g_\infty \mapsto W_\varphi(g_\infty g_f)$ lies in $\mathcal{W}(\psi_\infty)$.

Lean: not formalized

*Proof.* The transformation law under $u(x)$, $x \in \mathbb{R}$, holds since $\psi$ restricts to $\psi_\infty$ on $\mathbb{R}$. $K_\infty$-finiteness and $Z(\mathfrak{g})$-finiteness pass from $\varphi$ to $W_\varphi$, since $\varphi \mapsto W_\varphi$ commutes with right translations and derivatives. For the growth, take the fundamental domain $D = [0, 1) \times \widehat{\mathbb{Z}}$ for $\mathbb{Q}\backslash\mathbb{A}$. Then $|W_\varphi(g)| \le \sup_{x \in D}|\varphi(u(x)g)|$, and $\|u(x)g\| \le C\|g\|$ for $x \in D$ by Lemma 2.2.2. Moderate growth of $\varphi$ gives the bound. $\square$

**Lemma 2.5.2 (twisted coinvariants of a tensor product).** Let $V_1$ be a smooth representation of $G(\mathbb{Q}_p)$ and $V_2$ a vector space. Then $(V_1 \otimes V_2)_{U, \psi_p} = (V_1)_{U, \psi_p} \otimes V_2$, where $U(\mathbb{Q}_p)$ acts on $V_1 \otimes V_2$ through $V_1$.

Lean: not formalized

*Proof.* The functor $V \mapsto V_{U, \psi_p}$ is the cokernel of the map $\bigoplus_{x}V \to V$, $(v_x) \mapsto \sum_x(\pi(u(x))v_x - \psi_p(x)v_x)$. Tensoring with $V_2$ over $\mathbb{C}$ is exact and commutes with direct sums and cokernels. $\square$

**Proposition 2.5.3 (global uniqueness at the finite places).** Let $\pi_f = \bigotimes'_p\pi_p$ be a restricted tensor product of irreducible admissible representations $\pi_p$ of $G(\mathbb{Q}_p)$, with respect to vectors $v_p^0$ fixed by $K_p$ for almost all $p$. Then the space of linear forms $\Lambda$ on $\pi_f$ with $\Lambda(\pi_f(u(x))v) = \psi_f(x)\Lambda(v)$ for $x \in \mathbb{A}_f$ has dimension at most $1$.

Lean: not formalized

*Proof.* For a finite set $S$ of primes let $V_S = \bigotimes_{p \in S}\pi_p$, embedded in $\pi_f$ by $v \mapsto v \otimes \bigotimes_{p \notin S}v_p^0$. Then $\pi_f$ is the union of the $V_S$. Let $\Lambda \ne 0$ be such a form and let $S_0$ be a set with $\Lambda|_{V_{S_0}} \ne 0$. For $S \supseteq S_0$ the restriction $\Lambda|_{V_S}$ is a functional on $V_S$ for the character $\prod_{p \in S}\psi_p$ of $\prod_{p \in S}U(\mathbb{Q}_p)$, since $\psi_p$ is trivial on $\mathbb{Z}_p$ and $u(\mathbb{Z}_p)$ fixes $v_p^0$. By Lemma 2.5.2 applied one prime at a time, the space of these functionals is $\bigotimes_{p \in S}\mathrm{Hom}_U(\pi_p, \psi_p)$, which has dimension at most $1$ by Theorem 2.4.6. So if $\Lambda'$ is a second form, there is $c_S$ with $\Lambda' = c_S\Lambda$ on $V_S$. Since $\Lambda|_{V_{S_0}} \ne 0$, the scalar $c_S$ equals $c_{S_0}$ for all $S \supseteq S_0$, and $\Lambda' = c_{S_0}\Lambda$. $\square$

**Theorem 2.5.4 (multiplicity one).** Let $\pi$ be an irreducible admissible $(\mathfrak{g}, K_\infty) \times G(\mathbb{A}_f)$-module. Then $\dim\mathrm{Hom}(\pi, \mathcal{A}_0(G)) \le 1$. In particular each cuspidal automorphic representation occurs with multiplicity one in $\mathcal{A}_0(G, \omega)$.

Lean: not formalized

*Proof.* By the tensor product theorem of Flath, [Bum97] Chapter 3, there is an isomorphism $\pi \cong \pi_\infty \otimes \pi_f$, with $\pi_\infty$ an irreducible admissible $(\mathfrak{g}, K_\infty)$-module and $\pi_f = \bigotimes'_p\pi_p$ as in Proposition 2.5.3. Let $j : \pi \to \mathcal{A}_0(G)$ be a nonzero map. It is injective, since $\pi$ is irreducible. For $v_f \in \pi_f$ consider the map
$$\Phi_{v_f} : v_\infty \mapsto \left(g_\infty \mapsto W_{j(v_\infty \otimes v_f)}(g_\infty)\right).$$
By Lemma 2.5.1 it is a map of $(\mathfrak{g}, K_\infty)$-modules from $\pi_\infty$ to $\mathcal{W}(\psi_\infty)$. By Theorem 2.4.10 we can fix such a map $\Phi_0$, and then $\Phi_{v_f} = c(v_f)\Phi_0$ for a unique scalar $c(v_f)$. If $\Phi_0$ does not exist, every $\Phi_{v_f}$ is $0$, and then $W_{j(v)}(g_\infty g_f) = W_{j(\pi(g_f)v)}(g_\infty) = 0$ for all $v$, so $j = 0$ by Theorem 2.4.3. So $\Phi_0$ exists, and $c$ is linear in $v_f$. Let $v = v_\infty \otimes v_f$ and $x \in \mathbb{A}_f$. Since $u(x) \in G(\mathbb{A}_f)$ commutes with $g_\infty$,
$$c(\pi_f(u(x))v_f)\,\Phi_0(v_\infty)(g_\infty) = W_{j(v)}(u(x)g_\infty) = \psi_f(x)\,c(v_f)\,\Phi_0(v_\infty)(g_\infty).$$
Choose $v_\infty$ and $g_\infty$ with $\Phi_0(v_\infty)(g_\infty) \ne 0$. Then $c$ is a Whittaker functional on $\pi_f$. We get
$$W_{j(v_\infty \otimes v_f)}(g_\infty g_f) = c(\pi_f(g_f)v_f)\,\Phi_0(v_\infty)(g_\infty).$$
Let $j'$ be a second map, with functional $c'$. By Proposition 2.5.3, $c' = ac$ for a scalar $a$. Then $W_{j'(v)} = aW_{j(v)}$ for all $v$, so $j' = aj$ by Theorem 2.4.3. $\square$

This is in [JL70], Chapter II, in the form of the theory of automorphic forms; see also [Bum97] Chapter 3 and [Gel75]. For $GL_n$ the same proof works, with the Fourier-Whittaker expansion of Piatetski-Shapiro and Shalika in place of Theorem 2.4.3, and Volume 7, Theorem 1.5.5, states the result.

**Corollary 2.5.5 (local components are generic).** Let $\pi = \bigotimes'_v\pi_v$ be a cuspidal automorphic representation of $G(\mathbb{A})$. Then each $\pi_v$ is generic. In particular each $\pi_p$ is infinite-dimensional, and $\pi_\infty$ is not finite-dimensional.

Lean: not formalized

*Proof.* The proof of Theorem 2.5.4 gives a nonzero map $\Phi_0$ into $\mathcal{W}(\psi_\infty)$ and a nonzero Whittaker functional $c$ on $\pi_f$. Choose $v_f = v_p \otimes v^{(p)}$ with $c(v_f) \ne 0$. Then $v \mapsto c(v \otimes v^{(p)})$ is a nonzero Whittaker functional on $\pi_p$. By Theorem 2.4.6, $\pi_p$ is infinite-dimensional, and by Theorem 2.4.10, $\pi_\infty$ is too. $\square$

**Example 2.5.6 (the newform).** Let $f \in S_k(\Gamma_0(N))$ be a normalized newform and $\pi$ the representation generated by $\phi_f$. The local newform theory of Chapter 3 shows that the vectors of $\pi$ that have weight $k$, are killed by $L$ and are fixed by $K_0(N)$ form a space of dimension $1$. By Theorem 2.5.4, $\pi$ has only one image in $\mathcal{A}_0(G)$. So the isomorphism class of $\pi$ determines $\phi_f$, and hence $f$, up to a scalar. The classical statement that a newform is determined by its Hecke eigenvalues for almost all $p$ needs one more fact: the strong multiplicity one theorem of Chapter 4, which says that $\pi$ is determined by its components $\pi_p$ for almost all $p$.
