---
title: The abelian case
nodes: [LGVAKJJD8Y]
sources: [CF67, Mil20, Neu99]
status: drafted
drafted_by: writer
reviewed_by: []
---
## The abelian case

Artin introduced his $L$-functions in 1923 with a conjecture: the $L$-function of a character of an abelian Galois group should be a Hecke $L$-function. He proved this in 1927, and the statement he proved is his reciprocity law. This section deduces the identity of the two $L$-functions from class field theory, with the conductors and the gamma factors. With Hecke's theorem from Chapter 5 it gives the continuation and the functional equation of every abelian Artin $L$-function. Section 6.6 extends these results to all representations.

### Global reciprocity

Let $J_F$ be the idele group of $F$ and $C_F = J_F / F^\times$ the idele class group, as in Volume 1, Chapter 3. For each place $v$ the group $F_v^\times$ embeds in $J_F$ as the ideles that are $1$ outside $v$. For a finite place $v$, let $\mathcal{O}_v^\times$ be the unit group of $F_v$.

**Theorem 6.5.1 (global reciprocity).** Let $L/F$ be a finite abelian extension with group $G$. There is a continuous surjective homomorphism $\mathrm{art}_{L/F} : C_F \to G$ with the following properties.
1. For each finite place $v$ of $F$ unramified in $L$ and each uniformizer $\varpi_v$ of $F_v$, the image of $\varpi_v$ is $\mathrm{Frob}_v^{-1}$.
2. The kernel of $\mathrm{art}_{L/F}$ is the image of the norm map $N_{L/F} : C_L \to C_F$.
3. For each place $v$ and each place $w \mid v$ of $L$, the restriction of $\mathrm{art}_{L/F}$ to $F_v^\times$ takes values in $D_w = \mathrm{Gal}(L_w/F_v)$. At a finite place it is the local reciprocity map $r_{L_w/F_v}$ of Theorem 2.1.3, so it maps $\mathcal{O}_v^\times$ onto the inertia group $I_w$ by Proposition 2.1.8. At a real place it maps $-1$ to the complex conjugation $c_w$, and $\mathbb{R}_{>0}$ to $1$. At a complex place it is trivial.

Node: LGVAKJJD8Y · Lean: `Langlands.GlobalReciprocity`

This is Theorem 2.1.6 of Volume 0, with the classical complements. The Lean statement `Langlands.GlobalReciprocity` asserts part 1 only. Parts 2 and 3 are in [CF67], Chapter VII, and in [Mil20], Chapter V. Part 1 is the geometric normalization of the handbook: the map sends a uniformizer to the inverse of the arithmetic Frobenius. At a finite place $v$, the image of a uniformizer $\varpi_v$ under part 3 acts on the residue field of $L_w$ as the geometric Frobenius, by Theorem 2.1.3, part 1. So $\mathrm{art}_{L/F}(\varpi_v)$ lies in the coset $\mathrm{Frob}_w^{-1} I_w$, also at the ramified places.

### Abelian Artin L-functions are Hecke L-functions

Let $L/F$ be abelian with group $G$, and let $\chi : G \to \mathbb{C}^\times$ be a character. Define
$$\omega_\chi = \chi^{-1} \circ \mathrm{art}_{L/F} : C_F \to \mathbb{C}^\times.$$
It is a Hecke character of finite order, in the sense of Definition 5.4.1. Its local components are $\omega_{\chi, v} = \chi^{-1} \circ \mathrm{art}_{L/F}|_{F_v^\times}$.

**Theorem 6.5.2 (abelian Artin $L$-functions).** Let $\chi$ be a character of $G$.
1. For each finite place $v$, $L_v(s, \chi) = L(\omega_{\chi, v}, s)$, the factor of Definition 5.2.2. Hence $L(s, \chi) = L(s, \omega_\chi)$.
2. $\mathfrak{f}(\chi) = \mathfrak{f}_{\omega_\chi}$, and $\Gamma_v(s, \chi) = L(\omega_{\chi, v}, s)$ at each infinite place $v$. Hence $A(\chi) = |d_F| N(\mathfrak{f}_{\omega_\chi})$ and $\Lambda(s, \chi) = \Lambda(s, \omega_\chi)$.
3. Theorem 6.4.6 holds for $\chi$, with $W(\chi) = W(\omega_\chi)$.
4. The map $\chi \mapsto \omega_\chi$ is a bijection from the characters of $G$ onto the Hecke characters of finite order that are trivial on $N_{L/F}(C_L)$. Every Hecke character of finite order is $\omega_\chi$ for some finite abelian $L/F$ and some $\chi$.

Lean: not stated yet

*Proof.* Part 1. Let $v$ be finite, $q = N(v)$, and let $I = I_w$ and $D = D_w$. They do not depend on $w$, since $G$ is abelian. By Theorem 6.5.1, part 3, $\omega_{\chi, v}$ is trivial on $\mathcal{O}_v^\times$ if and only if $\chi$ is trivial on $I$. So $\omega_{\chi, v}$ is unramified exactly when $\chi$ is unramified at $v$. In that case $\mathrm{art}_{L/F}(\varpi_v) \in \mathrm{Frob}_w^{-1} I$ gives $\omega_{\chi, v}(\varpi_v) = \chi(\mathrm{Frob}_w)$. So $L(\omega_{\chi, v}, s) = (1 - \chi(\mathrm{Frob}_w) q^{-s})^{-1} = L_v(s, \chi)$, by Definition 5.2.2 and Example 6.1.5, part 2. If $\chi$ is ramified at $v$, both factors are $1$.

Part 2. Let $v$ be finite. By Proposition 6.4.2, part 5, $f(\chi, v)$ is the conductor $a(\phi)$ of the character $\phi = \chi|_D$ of the Weil group of $F_v$. A character and its inverse have the same kernel, so $a(\phi) = a(\phi^{-1})$. By Theorem 6.5.1, part 3, $\omega_{\chi, v} = \phi^{-1} \circ r_{L_w/F_v}$ is the character $\chi_{\phi^{-1}}$ of Theorem 4.2.3. Part 4 of that theorem gives $a(\phi^{-1}) = a(\omega_{\chi, v})$. So $f(\chi, v) = a(\omega_{\chi, v})$ for all $v$, and the conductors agree. Let $v$ be real. Then $\omega_{\chi, v}$ is trivial on $\mathbb{R}_{>0}$ and $\omega_{\chi, v}(-1) = \chi(c_w)^{-1} = \chi(c_w)$. So $\omega_{\chi, v} = \mathrm{sgn}^a$, with $a = 0$ if $\chi(c_w) = 1$ and $a = 1$ if $\chi(c_w) = -1$. Definition 5.2.2 gives $L(\omega_{\chi, v}, s) = \Gamma_\mathbb{R}(s + a)$, which is $\Gamma_v(s, \chi)$. At a complex place $\omega_{\chi, v}$ is trivial, and both factors are $\Gamma_\mathbb{C}(s)$.

Part 3. We have $\omega_{\chi^{-1}} = \omega_\chi^{-1}$, and $\chi^\vee = \chi^{-1}$. The character $\omega_\chi$ is unitary, so its exponent is $\sigma = 0$. Theorem 5.5.3 and part 2 give the continuation and
$$\Lambda(s, \chi) = \Lambda(s, \omega_\chi) = W(\omega_\chi) \big(|d_F| N(\mathfrak{f}_{\omega_\chi})\big)^{1/2 - s} \Lambda(1 - s, \omega_\chi^{-1}) = W(\omega_\chi) A(\chi)^{1/2 - s} \Lambda(1 - s, \chi^\vee),$$
with $|W(\omega_\chi)| = 1$.

Part 4. The map is injective, because $\mathrm{art}_{L/F}$ is surjective, and its image is the set of characters of $C_F$ trivial on $\ker \mathrm{art}_{L/F}$. By Theorem 6.5.1, part 2, this kernel is $N_{L/F}(C_L)$. A Hecke character $\omega$ of finite order has an open kernel of finite index in $C_F$. By the existence theorem, Volume 0, Theorem 2.1.7, there is a finite abelian $L/F$ with $\ker \mathrm{art}_{L/F} = \ker \omega$. Then $\omega = \omega_\chi$ for the character $\chi = \omega^{-1} \circ \mathrm{art}_{L/F}^{-1}$ of $G \cong C_F / \ker \omega$. $\square$

The inverse in the definition of $\omega_\chi$ comes from the two normalizations. The Euler factors of Artin use the arithmetic Frobenius, and the reciprocity map of the handbook sends a uniformizer to a geometric Frobenius. With the Artin map $x \mapsto \mathrm{art}_{L/F}(x)^{-1}$ of the arithmetic normalization, the Hecke character is $\chi \circ \mathrm{Art}_{L/F}$, with no inverse. This agrees with the statement in Volume 0, Section 2.1, that with the arithmetic Frobenius in the Euler factors the Hecke $L$-function of $\chi \circ \mathrm{art}$ is the Artin $L$-function of $\chi^{-1}$.

**Corollary 6.5.3 (abelian extensions).** Let $L/F$ be a finite abelian extension with group $G$.
1. For $\chi \ne \mathbf{1}$, the functions $L(s, \chi)$ and $\Lambda(s, \chi)$ extend to entire functions.
2. $\zeta_L(s) = \zeta_F(s) \prod_{\chi \ne \mathbf{1}} L(s, \chi)$. In particular $\zeta_L(s) / \zeta_F(s)$ is entire.
3. For $\chi \ne \mathbf{1}$, $L(1, \chi) \ne 0$. Hence $L(1, \omega) \ne 0$ for every nontrivial Hecke character $\omega$ of finite order.

Lean: not stated yet

*Proof.* For part 1, the character $\omega_\chi$ is not trivial. It has finite order, so it is not of the form $|\cdot|_\mathbb{A}^{s_0}$ unless $s_0 = 0$, since $|\cdot|_\mathbb{A}$ takes every positive real value. By Theorem 5.5.3, part 3, $\Lambda(s, \omega_\chi)$ is entire. Since $1/\Gamma$ is entire, $L(s, \chi) = \Lambda(s, \chi)/\Gamma_\infty(s, \chi)$ is entire. Part 2 is Corollary 6.3.4, part 2, since all the irreducible representations of $G$ are characters. For part 3, $\zeta_L$ and $\zeta_F$ have simple poles at $s = 1$ by Corollary 5.4.8. By parts 1 and 2, $\prod_{\chi \ne \mathbf{1}} L(1, \chi)$ is the quotient of the two residues, which is not $0$. The last claim follows from Theorem 6.5.2, part 4. $\square$

Part 3 is the key step in Dirichlet's theorem on primes in arithmetic progressions and its generalization to ray classes. For $\omega$ of infinite order and for the line $\mathrm{Re}(s) = 1$ one needs a separate argument, see [Neu99], Chapter VII.

**Example 6.5.4 (cyclotomic fields).** Let $F = \mathbb{Q}$ and $L = \mathbb{Q}(\zeta_N)$. The group $G$ is $(\mathbb{Z}/N)^\times$, with $a$ acting as $\sigma_a(\zeta_N) = \zeta_N^a$, and $\mathrm{Frob}_p = \sigma_p$ for $p \nmid N$. A character $\chi$ of $G$ gives the Dirichlet character $\eta(a) = \chi(\sigma_a)$ modulo $N$. Let $\eta^*$ be the primitive character modulo $m \mid N$ that induces $\eta$. Then $\chi$ is trivial on $\mathrm{Gal}(L/\mathbb{Q}(\zeta_m))$, so by Theorem 6.3.3, part 2, we may replace $N$ by $m$. For $p \nmid m$ the factor is $(1 - \eta^*(p) p^{-s})^{-1}$. For $p \mid m$, let $p^k$ be the exact power of $p$ in $m$. The inertia group at $p$ in $\mathrm{Gal}(\mathbb{Q}(\zeta_m)/\mathbb{Q})$ is the group of $a$ with $a \equiv 1 \pmod{m/p^k}$. The character $\eta^*$ is not trivial on it, since $\eta^*$ is primitive, so the factor is $1$. Hence $L(s, \chi) = L(s, \eta^*)$, and Corollary 6.5.3 gives
$$\zeta_{\mathbb{Q}(\zeta_N)}(s) = \prod_\eta L(s, \eta^*),$$
the product over all Dirichlet characters modulo $N$. For $N = p$ prime, $p$ is tamely and totally ramified, and $f(\chi, p) = 1$ for $\chi \ne \mathbf{1}$ by Proposition 6.4.2, part 1. Corollary 6.4.3 then gives $|d_{\mathbb{Q}(\zeta_p)}| = p^{p-2}$.
