---
title: The Artin L-function
nodes: []
sources: [Neu99]
status: drafted
drafted_by: writer
reviewed_by: []
---
## The Artin L-function

We keep the notation of Section 6.1: $L/F$ is a finite Galois extension of number fields with group $G$, and $\rho : G \to GL(V)$ is a representation of dimension $n$ with character $\chi$. This section defines $L(s, \rho)$ as the product of the local factors over the finite primes, proves that the product converges absolutely for $\mathrm{Re}(s) > 1$, and compares the definition with the one in the Lean project.

**Definition 6.2.1 (the Artin $L$-function).** The *Artin $L$-function* of $\rho$ is
$$L(s, \rho) = \prod_\mathfrak{p} L_\mathfrak{p}(s, \rho) = \prod_\mathfrak{p} \det\big(1 - \rho(\mathrm{Frob}_\mathfrak{P}) N(\mathfrak{p})^{-s} \mid V^{I_\mathfrak{P}}\big)^{-1}, \qquad \mathrm{Re}(s) > 1,$$
the product over the nonzero primes $\mathfrak{p}$ of $\mathcal{O}_F$, with a prime $\mathfrak{P} \mid \mathfrak{p}$ for each $\mathfrak{p}$. We also write $L(s, \chi)$ or $L(s, \rho, L/F)$ for it.

Lean: `Langlands.artinLFunction`, a definition of the project

By Lemma 6.1.4 the product depends only on $\chi$. The factors at the archimedean places are gamma factors, and Section 6.4 defines them.

### Convergence

Let $\sigma = \mathrm{Re}(s)$. We compare $L(s, \rho)$ with the Dedekind zeta function. Recall that for $\sigma > 1$ the product $\zeta_F(\sigma) = \prod_\mathfrak{p} (1 - N(\mathfrak{p})^{-\sigma})^{-1}$ converges. Indeed, at most $[F : \mathbb{Q}]$ primes of $F$ lie above a rational prime $p$, and each has norm at least $p$. So
$$\sum_\mathfrak{p} \sum_{m \ge 1} \frac{N(\mathfrak{p})^{-m\sigma}}{m} \le [F : \mathbb{Q}] \sum_p \sum_{m \ge 1} \frac{p^{-m\sigma}}{m} = [F : \mathbb{Q}] \log \zeta(\sigma) < \infty.$$

**Theorem 6.2.2 (convergence of the Euler product).** The series $\sum_\mathfrak{p} \log L_\mathfrak{p}(s, \rho)$, with the logarithms of Lemma 6.1.4, converges absolutely and uniformly on each half plane $\mathrm{Re}(s) \ge \sigma_0 > 1$. Hence the product $L(s, \rho)$ converges absolutely on $\mathrm{Re}(s) > 1$ to a holomorphic function without zeros, and
$$|\log L(s, \rho)| \le n \log \zeta_F(\sigma).$$
Also $L(s, \rho) = \sum_\mathfrak{a} c_\rho(\mathfrak{a}) N(\mathfrak{a})^{-s}$, a Dirichlet series over the nonzero ideals $\mathfrak{a}$ of $\mathcal{O}_F$, with $|c_\rho(\mathfrak{a})| \le c_n(\mathfrak{a})$, where $\zeta_F(s)^n = \sum_\mathfrak{a} c_n(\mathfrak{a}) N(\mathfrak{a})^{-s}$.

Lean: not stated yet

*Proof.* Fix $\mathfrak{p}$, let $d = \dim V^{I_\mathfrak{P}} \le n$, and let $\alpha_1, \dots, \alpha_d$ be the eigenvalues of $\rho(\mathrm{Frob}_\mathfrak{P})$ on $V^{I_\mathfrak{P}}$. They are roots of unity. By Lemma 6.1.4,
$$\log L_\mathfrak{p}(s, \rho) = \sum_{j=1}^{d} \sum_{m \ge 1} \frac{\alpha_j^m}{m} N(\mathfrak{p})^{-ms}, \qquad |\log L_\mathfrak{p}(s, \rho)| \le n \sum_{m \ge 1} \frac{N(\mathfrak{p})^{-m\sigma}}{m}.$$
The right side is $n \log (1 - N(\mathfrak{p})^{-\sigma})^{-1}$. For $\sigma \ge \sigma_0$ it is bounded by its value at $\sigma_0$, and the sum of these values over $\mathfrak{p}$ is $n \log \zeta_F(\sigma_0) < \infty$. By the Weierstrass test the series of logarithms converges absolutely and uniformly for $\mathrm{Re}(s) \ge \sigma_0$. Its sum is holomorphic, and $L(s, \rho)$ is its exponential, so $L(s, \rho)$ is holomorphic and has no zeros. The product converges absolutely, so it does not depend on the order of the primes. For the Dirichlet series, write $T = N(\mathfrak{p})^{-s}$. Then $L_\mathfrak{p}(s, \rho) = \prod_j (1 - \alpha_j T)^{-1} = \sum_k h_k(\alpha) T^k$, where $h_k$ is the complete homogeneous symmetric polynomial of degree $k$ in $d$ variables. It has nonnegative coefficients, so $|h_k(\alpha)| \le h_k(1, \dots, 1) = \binom{k + d - 1}{d - 1} \le \binom{k + n - 1}{n - 1}$, and the right side is the coefficient of $T^k$ in $(1 - T)^{-n}$. Multiplying out the absolutely convergent product gives the Dirichlet series and the bound. $\square$

The bound is attained by the trivial representation of dimension $n$, whose $L$-function is $\zeta_F^n$.

**Proposition 6.2.3 (the trivial representation).** For the trivial representation $\mathbf{1}$ of $G$, $L(s, \mathbf{1}) = \zeta_F(s)$. In particular $L(s, \mathbf{1})$ does not depend on $L$.

Lean: `Langlands.Fidelity.artinLFunction_one`, proved in the project

*Proof.* By Example 6.1.5, part 1, the factor at every prime is $(1 - N(\mathfrak{p})^{-s})^{-1}$. $\square$

The Lean theorem is an identity of the two products over the height one spectrum of $\mathcal{O}_F$, for every $s \in \mathbb{C}$. It holds at the ramified primes too, because the projector $e_I$ of the trivial representation is the identity matrix. This is a check that the definition in the project treats the ramified primes correctly.

**Example 6.2.4 (the Gaussian field).** Let $F = \mathbb{Q}$, $L = \mathbb{Q}(i)$ and let $\chi$ be the nontrivial character of $G = \mathrm{Gal}(L/\mathbb{Q})$. The prime $2$ is ramified with $I = G$, so $L_2(s, \chi) = 1$. An odd prime $p$ is unramified, and $\mathrm{Frob}_p$ is trivial exactly when $p$ splits, that is, when $p \equiv 1 \pmod 4$. So $\chi(\mathrm{Frob}_p) = \chi_{-4}(p)$, the Dirichlet character modulo 4, and $L(s, \chi) = L(s, \chi_{-4})$. The regular representation is $\mathbf{1} + \chi$. The factors of $\zeta(s) L(s, \chi)$ are $(1 - p^{-s})^{-2}$ for $p \equiv 1 \pmod 4$, $(1 - p^{-2s})^{-1}$ for $p \equiv 3 \pmod 4$ and $(1 - 2^{-s})^{-1}$ at $2$. These are the factors of $\zeta_{\mathbb{Q}(i)}(s)$, because $p \equiv 1$ splits, $p \equiv 3$ is inert, and $2 = -i(1+i)^2$ is ramified with residue degree $1$. So $\zeta_{\mathbb{Q}(i)}(s) = \zeta(s) L(s, \chi_{-4})$.

### The Lean definition

**Remark 6.2.5 (the Lean form of the local factors).** The file `Langlands/Statements/Galois.lean` of the Lean project defines the Artin $L$-function in the section `Artin`. It writes $K$ for the base field $F$. The extension $L$ is an intermediate field of $\bar K / K$, with $\bar K$ the algebraic closure `AlgebraicClosure K`, and a representation is a homomorphism `ρ : Gal(L/K) →* GL (Fin n) ℂ`. So $V = \mathbb{C}^n$, and the linear maps are matrices. The definitions do not assume that $L/K$ is finite or Galois. The statements that use them, such as `Langlands.ArtinConjecture` in Section 6.7, assume both. The definitions differ from Definition 6.1.3 and Definition 6.2.1 in five points.
1. The prime above $v$. A finite prime $v$ of $K$ is an element of `HeightOneSpectrum (𝓞 K)`, a nonzero prime of $\mathcal{O}_K$. The definition `primeAbove L v` is `Classical.epsilon` applied to the property of being a maximal ideal of $\mathcal{O}_L$ that lies over $v$. Such an ideal exists, because $\mathcal{O}_L$ is integral over $\mathcal{O}_K$. So the choice operator returns some prime $\mathfrak{P} \mid v$. The choice is not explicit, and Lemma 6.1.4 shows that it does not matter.
2. The Frobenius. The definition `frobeniusAbove L v` is `Classical.epsilon` applied to the property `IsArithFrobAt (𝓞 K) σ P` of Mathlib, for $P = $ `primeAbove L v`. This property says that $\sigma(x) - x^q \in P$ for all $x \in \mathcal{O}_L$, where $q = N(v)$ is the cardinality of $\mathcal{O}_K / v$. It is the arithmetic Frobenius, not the geometric one. When $L/K$ is finite and Galois such an element exists by Volume 1, Theorem 1.4.6, and by Section 6.1 the elements with this property form exactly the Frobenius coset at $P$. At a ramified prime the coset has more than one element, and the choice operator picks one. Lemma 6.1.2, part 4, shows that the factor does not depend on it.
3. The inertia invariants. The project does not form the subspace $V^I$. It uses the matrix `inertiaProjector ρ P`, which is $(\mathrm{Nat.card}\, I)^{-1} \sum_{\tau \in I} \rho(\tau)$, with $I$ = `P.inertia Gal(L/K)`, the subgroup of the $\sigma$ with $\sigma(x) - x \in P$ for all $x$. This is the projector $e_I$ of Lemma 6.1.2. The sum is a `finsum`, which is the ordinary sum for a finite group. If $I$ were infinite, `Nat.card I` would be $0$, and the inverse of $0$ is $0$ in Lean. This value is never used, because the statements assume that $L/K$ is finite.
4. The determinant. The local factor `artinLocalFactor ρ v s` is the inverse of the determinant of the $n \times n$ matrix $1 - N(v)^{-s} \rho(\sigma) e_I$, where $\sigma$ = `frobeniusAbove L v`. By Lemma 6.1.2, part 3, this is $\det(1 - N(v)^{-s} \rho(\sigma) \mid V^I)$. So the project does not need a basis of $V^I$. In Lean the inverse of $0$ is $0$, but the determinant is never $0$ for $\mathrm{Re}(s) > 0$. Indeed, the eigenvalues of $\rho(\sigma) e_I$ are $0$ and roots of unity, and $|N(v)^{-s}| < 1$.
5. The product. The function `artinLFunction ρ s` is the unconditional product `∏'` over `HeightOneSpectrum (𝓞 K)`. In Mathlib this product is defined as the limit over the finite sets of primes when the product is multipliable, and as $1$ otherwise. By Theorem 6.2.2 the product is multipliable for $\mathrm{Re}(s) > 1$, with the value $L(s, \rho)$. For $\mathrm{Re}(s) \le 1$ the Lean value carries no meaning. For this reason every statement of the project about $L(s, \rho)$ compares it with another function only on the half plane $\mathrm{Re}(s) > 1$.

The Lean definition contains no archimedean factors. It is the function $L(s, \rho)$ of Definition 6.2.1, not the completed function $\Lambda(s, \rho)$ of Section 6.4.
