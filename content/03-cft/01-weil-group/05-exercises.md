---
title: Exercises and notes
nodes: []
sources: [Tat79, Ser67, Ser79]
status: checked
drafted_by: writer
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## Exercises

1. Show that $\mathbb{Q}_p$ has exactly three quadratic extensions if $p$ is odd. Which of them is unramified? Find a generator of each one.
2. Let $K = \mathbb{Q}_p$ and let $L = \mathbb{Q}_p(\zeta_{p^n - 1})$. Show that $\mathcal{O}_L = \mathbb{Z}_p[\zeta_{p^n-1}]$.
3. Show that the map $\mathbb{Z} \to \mathrm{Gal}(\bar k / k)$, $n \mapsto \mathrm{Frob}_k^n$, is injective and that its image is dense. Show that it is not surjective.
4. Show that a subset $U$ of $W_K$ is open if and only if $U \cap d^{-1}(n)$ is open in $d^{-1}(n)$, with the topology of a subspace of $G_K$, for each $n$.
5. Show that the Weil group, with the subspace topology of $G_K$, is not locally compact.
6. Let $\Phi$ be a geometric Frobenius. Show that the map $I_K \rtimes \mathbb{Z} \to W_K$, $(\sigma, n) \mapsto \sigma \Phi^n$, is an isomorphism of topological groups, where $\mathbb{Z}$ acts on $I_K$ by conjugation with $\Phi$.
7. Let $L$ be a finite extension of $K$ in $\bar K$. Show that $W_L = W_K \cap G_L$, and that $W_L$ is an open subgroup of $W_K$ of finite index $[L : K]$.
8. (The wrong normalization.) Suppose that a map $r : K^\times \to W_K^{ab}$ sends each uniformizer to the class of an arithmetic Frobenius. Show that $x \mapsto r(x^{-1})$ sends each uniformizer to the class of a geometric Frobenius. Conclude that the two normalizations give the same set of theorems, but that each statement must say which one it uses.

## Notes and history

Weil defined the global Weil group in 1951, in "Sur la theorie du corps de classes", J. Math. Soc. Japan 3. He wanted a group whose representations give the Hecke L-functions with Grossencharacters, and the Galois group was too small for this purpose. The local Weil group is the local part of his construction.

The standard reference for the definitions of this chapter is Tate's article "Number theoretic background" [Tat79]. Tate defines a Weil group as a topological group with a map to $G_K$ and an isomorphism of its abelianization with $K^\times$, and he shows that the subgroup of $G_K$ of this chapter has these properties. The handbook and the Lean code use the subgroup, because it needs no choice. The facts on unramified extensions are in Serre's book [Ser79], Chapter III.

Deligne introduced the geometric normalization in "Les constantes des equations fonctionnelles des fonctions L" (1973). Most texts on the local Langlands correspondence use it, but many texts on class field theory use the arithmetic normalization. Thus a reader who compares two sources must check the normalization first.

The Lean definition of $W_K$ is in the file `Langlands/Statements/Basic.lean` of tamnd/langlands-lean. It uses the absolute Galois group, the integral closure and the residue map of Mathlib, and it has no unproved step.
