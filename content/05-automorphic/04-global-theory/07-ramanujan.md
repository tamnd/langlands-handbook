---
title: The Ramanujan conjecture
nodes: [LGAGRC05KF, LGV8B6TVWZ, LG75ERTV5K, LG0S1WN9ND]
sources: [Del74, DS74, Kim03]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## The Ramanujan conjecture

Ramanujan conjectured $|\tau(p)| \le 2p^{11/2}$. In the language of this chapter the conjecture says that the local components of $\pi_\Delta$ are tempered. This section states the conjecture for all cuspidal representations of $GL_2(\mathbb{A})$, proves the trivial bound, and deduces the conjecture for holomorphic newforms of weight $k \ge 2$ at all places from Deligne's theorem.

### Tempered representations

**Definition 4.7.1 (tempered representations).** An irreducible unitary representation $\pi_v$ of $G_v$ with unitary central character is *tempered* if its matrix coefficients lie in $L^{2+\epsilon}(Z(\mathbb{Q}_v) \backslash G_v)$ for every $\epsilon > 0$.

For $G_p$ the tempered representations with unitary central character are the principal series $\chi_1 \times \chi_2$ with $\chi_1, \chi_2$ unitary, the twists $\mu\mathrm{St}$ with $\mu$ unitary, and the supercuspidal representations. The complementary series and the one-dimensional representations are not tempered. For $G_\infty$ the tempered ones are the discrete series $D_k$, $k \ge 2$, the limits of discrete series and the unitary principal series. See [Bum97], Chapter 4, and Chapter 2. For an unramified $\pi_p$ with unitary central character, $\pi_p$ is tempered if and only if $|\alpha_p| = |\beta_p| = 1$.

**Conjecture 4.7.2 (Ramanujan conjecture for $GL_2$).** Let $\pi$ be a cuspidal automorphic representation of $GL_2(\mathbb{A})$ with unitary central character. Then $\pi_v$ is tempered for every place $v$. In particular $|\alpha_p| = |\beta_p| = 1$ at every prime $p$ where $\pi$ is unramified.

Node: LGAGRC05KF · Lean: `Langlands.RamanujanGL`

The Lean statement `Langlands.RamanujanGL n K` is the form at the unramified finite places, for $GL_n$ over a number field $K$. It says: for every nonzero bounded function $\phi$ that satisfies `Langlands.IsCuspForm` for some level, and every finite place $v$ where $\phi$ is a Hecke eigenvector with a system of eigenvalues (`Langlands.IsHeckeEigenAt`), each root $\alpha$ of `Langlands.satake` has $|\alpha| = 1$. For $n = 1$ it is the theorem `Langlands.ramanujanGL_one`. In `Langlands/Fidelity/GlobalGL.lean`, `Langlands.Fidelity.not_ramanujanGLWithoutCuspidal_two` shows that the statement is false for $n = 2$ without the cuspidal condition, since the constant function $1$ has parameters $q_v^{\pm 1/2}$. Two further theorems show that the conditions $\phi \ne 0$ and the invariant measure are needed and not empty.

### The trivial bound

**Proposition 4.7.3 (the trivial bound).** Let $\pi$ be a cuspidal automorphic representation with unitary central character $\omega$, and let $p$ be a prime where $\pi$ is unramified. Then $p^{-1/2} < |\alpha_p| < p^{1/2}$, and the same holds for $\beta_p$.

Lean: not formalized

*Proof.* By Proposition 4.2.3, $\pi_p$ is unitary. Let $v$ be a unit spherical vector. By Proposition 4.2.6, $\pi_p(T_p)v = \lambda v$ with $\lambda = p^{1/2}(\alpha + \beta)$, where $\alpha = \alpha_p, \beta = \beta_p$. Since $\pi_p$ is unitary and $T_p$ is the characteristic function of a set of volume $p + 1$ (Lemma 4.2.5), $\|\pi_p(T_p)\| \le p + 1$, so $|\lambda| \le p + 1$. The adjoint of $\pi_p(T_p)$ is $\pi_p(T_p^*)$ with $T_p^*(g) = \overline{T_p(g^{-1})}$, the characteristic function of $K_pa(p)^{-1}K_p = p^{-1}K_pa(p)K_p$. So $\pi_p(T_p)^* = \omega_p(p)^{-1}\pi_p(T_p)$, and $\bar\lambda = \omega_p(p)^{-1}\lambda$. Let $u$ be a square root of $\omega_p(p) = \alpha\beta$; then $|u| = 1$. The number $b = \lambda p^{-1/2}u^{-1}$ is real, since $\bar b = \bar\lambda p^{-1/2}u = \omega_p(p)^{-1}\lambda p^{-1/2}u = b$, and $|b| \le p^{1/2} + p^{-1/2}$. The numbers $\alpha/u$ and $\beta/u$ are the roots of $X^2 - bX + 1$. If $|b| \le 2$ they have absolute value 1. If $|b| > 2$ they are real, equal to $r$ and $1/r$ with $|r + 1/r| = |b| \le p^{1/2} + p^{-1/2}$, so $p^{-1/2} \le |r| \le p^{1/2}$. Equality $|r| = p^{\pm 1/2}$ would give the parameters of the one-dimensional representation $\chi \circ \det$ with $\chi(p) = u$, which is excluded by Proposition 4.2.3, part 4. $\square$

For a holomorphic form this is the bound $|a_p| < p^{k/2} + p^{k/2 - 1}$, an explicit form of the trivial bound $|a_p| = O(p^{k/2})$ of Volume 4. The best known bound for all cuspidal representations of $GL_2$ over $\mathbb{Q}$ is $|\alpha_p| \le p^{7/64}$, due to Kim and Sarnak in the appendix to [Kim03]. It comes from the symmetric fourth power lift and the Rankin-Selberg method.

### Deligne's theorem

**Theorem 4.7.4 (Ramanujan conjecture for holomorphic newforms).** Let $f$ be a newform of even weight $k \ge 2$, level $N$ and trivial character. Then $\pi_{f,v}$ is tempered for every place $v$.

Node: LGV8B6TVWZ · Lean: `Langlands.RamanujanPeterssonHolomorphic`

*Proof.* At $v = \infty$, $\pi_{f,\infty} = D_k$ with $k \ge 2$ is a discrete series, so its matrix coefficients are square integrable modulo the centre, and it is tempered. At $p \nmid N$, Deligne's theorem, Volume 4, Theorem 2.3.2, gives $|a_p(f)| \le 2p^{(k-1)/2}$. By Volume 4, Lemma 2.3.1, the arithmetic parameters have absolute value $p^{(k-1)/2}$. By Remark 4.2.7, $|\alpha_p| = |\beta_p| = 1$, and $\pi_{f,p}$ is a unitary principal series.

Let $p \mid N$. By the list after Proposition 4.2.3 and part 4 of that proposition, $\pi_{f,p}$ is a unitary principal series, a complementary series, a twist $\mu\mathrm{St}$ with $\mu$ unitary or a supercuspidal representation, and only the complementary series is not tempered. Suppose that $\pi_{f,p} = \chi|\cdot|^\sigma \times \chi|\cdot|^{-\sigma}$ with $\chi$ unitary and $0 < \sigma < 1/2$. The central character $\chi^2$ is trivial, so $\chi$ is quadratic, and $\chi$ is ramified since $\pi_{f,p}$ is ramified. The restriction of $\chi$ to $\mathbb{Z}_p^\times$ factors through $(\mathbb{Z}/p^m\mathbb{Z})^\times$ for some $m$, and it defines a quadratic Dirichlet character of conductor $p^m$. Let $\eta$ be the corresponding character of $\mathbb{Q}^\times \backslash \mathbb{A}^\times$, normalized so that $\eta_p$ and $\chi$ agree on $\mathbb{Z}_p^\times$. Then $\eta_p = \chi\nu$ with $\nu$ unramified and $\nu^2 = 1$. The representation $\pi' = \pi_f \otimes (\eta \circ \det)$, realized on the functions $\phi(g)\eta(\det g)$, is cuspidal automorphic with trivial central character $\eta^2 = 1$. Its component at infinity is $D_k \otimes \eta_\infty \cong D_k$, and its component at $p$ is
$$\chi\eta_p|\cdot|^\sigma \times \chi\eta_p|\cdot|^{-\sigma} = \nu|\cdot|^\sigma \times \nu|\cdot|^{-\sigma},$$
which is unramified with parameters $\nu(p)p^{\mp\sigma}$. By Theorem 4.3.3, $\pi' = \pi_g$ for a newform $g$ of weight $k$ whose level is prime to $p$. The case $p \nmid N$ applied to $g$ gives $|\nu(p)p^{-\sigma}| = 1$, so $\sigma = 0$, a contradiction. $\square$

The idea of the last step is general. A local component that is a twist of an unramified representation becomes unramified after a global twist, and then the unramified case applies. For $p \parallel N$ the theorem is simple: $\pi_{f,p} = \mu\mathrm{St}$ with $\mu(p) = \pm 1$, and $|a_p(f)| = p^{k/2-1}$. This is the classical value, smaller than the bound $2p^{(k-1)/2}$ at a good prime.

**Remark 4.7.5 (the Lean form of Deligne's theorem).** The statement `Langlands.RamanujanPeterssonHolomorphic` is the classical bound $|a_p(f)| \le 2p^{(k-1)/2}$ for normalized eigenforms on $\Gamma_0(N)$ and $p \nmid N$, see Volume 4, Remark 2.3.3. It is the case of Conjecture 4.7.2 at the unramified places for the representations $\pi_f$. There is no Lean bridge from it to `Langlands.RamanujanGL` for $n = 2$; such a bridge would need the adelic dictionary of Chapter 1.

### Weight one and Maass forms

For weight $k = 1$ the bound $|a_p| \le 2$ is a theorem of Deligne and Serre [DS74]. They attach to a newform of weight 1 an Artin representation $\rho : \mathrm{Gal}(\bar{\mathbb{Q}}/\mathbb{Q}) \to GL_2(\mathbb{C})$ with finite image, and $\alpha_p, \beta_p$ are the eigenvalues of $\rho(\mathrm{Frob}_p)$, so they are roots of unity. The component at infinity $D_1$ is a limit of discrete series, which is tempered.

For Maass forms the conjecture is open, both at the finite places and at infinity. At infinity it is Selberg's eigenvalue conjecture.

**Conjecture 4.7.6 (Ramanujan conjecture for Maass forms).** Let $u \ne 0$ be a Maass cusp form on $\Gamma_1(N)$ with character $\chi$, and let $p \nmid N$ be a prime. If $T_pu = cu$ for the Hecke operator in the unitary normalization, then $|c| \le 2$.

Node: LG75ERTV5K · Lean: `Langlands.RamanujanMaass`

**Conjecture 4.7.7 (Selberg's eigenvalue conjecture).** Let $\Gamma$ be a congruence subgroup of $SL_2(\mathbb{Z})$. Each eigenvalue $\lambda \ne 0$ of the hyperbolic Laplacian on $L^2(\Gamma \backslash \mathbb{H})$ satisfies $\lambda \ge 1/4$.

Node: LG0S1WN9ND · Lean: `Langlands.SelbergEigenvalue`

The eigenvalue $\lambda = 1/4 + r^2$ of a Maass cusp form $u$ corresponds to the component $\pi_{u,\infty}$, which is a unitary principal series for $r$ real and a complementary series for $r$ imaginary with $0 < |r| < 1/2$. So Conjecture 4.7.7 is the statement that $\pi_{u,\infty}$ is tempered, and in Conjecture 4.7.6 the bound $|c| \le 2$ says that the Satake parameters at $p$ have absolute value 1. Selberg proved $\lambda \ge 3/16$, and the bound of Kim and Sarnak gives $\lambda \ge 1/4 - (7/64)^2 = 975/4096$. For other reductive groups the naive analogue of Conjecture 4.7.2 is false: Howe and Piatetski-Shapiro found cuspidal representations of $Sp_4$ that are not tempered at almost all places. The correct form uses Arthur's classification, and for $GL_n$ it predicts that all cuspidal representations are tempered.
