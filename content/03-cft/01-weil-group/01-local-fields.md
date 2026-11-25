---
title: Local fields and unramified extensions
nodes: []
sources: [Ser79]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Local fields and unramified extensions

In this chapter $K$ is a nonarchimedean local field. Thus $K$ is a field with a nontrivial discrete valuation, $K$ is complete, and the residue field is finite. Examples are the field $\mathbb{Q}_p$ of $p$-adic numbers, its finite extensions, and the field $\mathbb{F}_q((t))$ of Laurent series over a finite field.

**Definition.** The *ring of integers* of $K$ is $\mathcal{O}_K = \{x \in K : |x| \le 1\}$. It is a discrete valuation ring with maximal ideal $\mathfrak{m}_K = \{x \in K : |x| < 1\}$. The *residue field* is $k = \mathcal{O}_K / \mathfrak{m}_K$, and $q$ is the number of elements of $k$. A *uniformizer* is a generator $\varpi$ of $\mathfrak{m}_K$.

Lean: `IsNonarchimedeanLocalField`, from Mathlib

Each element of $K^\times$ is $u \varpi^n$ for a unique unit $u \in \mathcal{O}_K^\times$ and a unique integer $n$. Thus the choice of $\varpi$ gives an isomorphism of topological groups $K^\times \cong \mathcal{O}_K^\times \times \mathbb{Z}$, where $\mathbb{Z}$ has the discrete topology and $\mathcal{O}_K^\times$ is compact. This decomposition is the first sign of the Weil group: a group that is compact up to a discrete factor $\mathbb{Z}$.

Let $L$ be a finite extension of $K$ of degree $n$. Then $L$ is also a nonarchimedean local field. Its ring of integers $\mathcal{O}_L$ is the integral closure of $\mathcal{O}_K$ in $L$, and it has a unique maximal ideal $\mathfrak{m}_L$. Let $\ell$ be the residue field of $L$. The *residue degree* is $f = [\ell : k]$, and the *ramification index* $e$ is defined by $\mathfrak{m}_K \mathcal{O}_L = \mathfrak{m}_L^e$. Then $n = ef$.

**Definition.** A finite extension $L$ of $K$ is *unramified* if $e = 1$ and the residue extension $\ell / k$ is separable.

Because $k$ is finite, the second condition is always true here. The next theorem says that the unramified extensions of $K$ are the same as the extensions of $k$.

**Theorem (unramified extensions).** Fix an algebraic closure $\bar K$ of $K$. For each $n \ge 1$ there is exactly one unramified extension $K_n$ of $K$ of degree $n$ in $\bar K$. It is the field $K(\zeta)$, where $\zeta$ is a primitive root of unity of order $q^n - 1$. The extension $K_n / K$ is Galois, and the map $\mathrm{Gal}(K_n / K) \to \mathrm{Gal}(k_n / k)$ to the Galois group of the residue extension is an isomorphism.

Lean: not stated yet, planned for milestone S1

*Proof.* Let $k_n$ be the extension of $k$ of degree $n$, and let $\bar\alpha$ be a generator of the cyclic group $k_n^\times$. Its minimal polynomial $\bar g$ over $k$ has degree $n$ and divides $X^{q^n - 1} - 1$. By Hensel's lemma the root $\bar\alpha$ of $X^{q^n-1} - 1$ lifts to a root $\zeta \in \bar K$ of order $q^n - 1$, and a monic lift $g$ of $\bar g$ is irreducible because its reduction is irreducible. Thus $[K(\zeta) : K] = n$ and the residue field of $K(\zeta)$ contains $k_n$. As $n = ef$, it follows that $f = n$ and $e = 1$.

The extension $K(\zeta) / K$ is the splitting field of $X^{q^n - 1} - 1$, because the powers of $\zeta$ are all the roots of this polynomial. Thus it is Galois. An automorphism that is trivial on $k_n$ fixes $\zeta$, because the roots of $X^{q^n-1} - 1$ have distinct reductions. Thus the map to $\mathrm{Gal}(k_n / k)$ is injective, and both groups have order $n$.

Let $L$ be an unramified extension of degree $n$ in $\bar K$. Its residue field is $k_n$, so by Hensel's lemma $L$ contains a root of unity of order $q^n - 1$, and thus $L$ contains $K(\zeta)$. The degrees are equal, so $L = K(\zeta)$. $\square$

The union $K^{ur}$ of the fields $K_n$ is the *maximal unramified extension* of $K$ in $\bar K$. The theorem gives an isomorphism of profinite groups $\mathrm{Gal}(K^{ur} / K) \cong \mathrm{Gal}(\bar k / k)$.

**Example.** For $K = \mathbb{Q}_p$ the unramified extension of degree $n$ is $\mathbb{Q}_p(\zeta_{p^n - 1})$. The extension $\mathbb{Q}_p(\zeta_p)$ has degree $p - 1$ and is totally ramified: its residue field is $\mathbb{F}_p$ and $e = p - 1$.
