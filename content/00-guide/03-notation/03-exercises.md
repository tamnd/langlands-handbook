---
title: Exercises and notes
nodes: []
sources: [Tat79, Ser79]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Exercises

1. Prove the product formula $\prod_v |x|_v = 1$ for $x \in \mathbb{Q}^\times$. Show that it fails if $|\cdot|_p$ is replaced by $|\cdot|_p^{2}$ at one prime $p$.
2. Let $\ell \ne p$. Show that $\chi_\ell \circ \mathrm{rec}_K = |\cdot|_K$. Show that with the arithmetic normalization of the reciprocity map the composite is $|\cdot|_K^{-1}$.
3. Let $(V, r, N)$ be a Weil-Deligne representation and $\Phi$ a geometric Frobenius. Show that $N$ maps the eigenspace of $r(\Phi)$ for the eigenvalue $\lambda$ into the eigenspace for $q^{-1}\lambda$. Conclude that an endomorphism $N$ with $r(w) N r(w)^{-1} = \|w\| N$ for all $w$ is nilpotent.
4. Let $\mathrm{Sp}(n)$ be the space $\mathbb{C}^n$ with basis $e_0, \dots, e_{n-1}$, with $r(w) e_i = \|w\|^i e_i$ and $N e_i = e_{i+1}$ for $i < n - 1$ and $N e_{n-1} = 0$. Show that $\mathrm{Sp}(n)$ is a Weil-Deligne representation, and that it is indecomposable.
5. Show that $\psi_p$ is a continuous character of $\mathbb{Q}_p$, trivial on $\mathbb{Z}_p$ and not on $p^{-1}\mathbb{Z}_p$. Show that $\psi_\infty(x) \prod_p \psi_p(x) = 1$ for $x \in \mathbb{Q}$.
6. Let $\chi$ be an unramified character of $K^\times$ and $\psi$ a character that is trivial on $\mathcal{O}_K$ and not on $\mathfrak{p}_K^{-1}$. Use Tate's local functional equation with $f$ the characteristic function of $\mathcal{O}_K$ to show that $\varepsilon(\chi, s, \psi) = 1$. Then prove the rule for $\varepsilon(\chi, s, \psi_a)$ of the second section in this case.
7. Show that the cusp $0$ of $\Gamma_0(p)$ has width $p$, for a prime $p$.
8. Let $f$ be a newform of weight $k$ on $\Gamma_0(N)$ and $p \nmid N$. Show that the Euler factor $(1 - a_p(f) p^{-s} + p^{k - 1 - 2s})^{-1}$ of $L(f, s)$ equals $\left((1 - \alpha_p p^{-s'})(1 - \beta_p p^{-s'})\right)^{-1}$ with $s' = s - (k-1)/2$, where $\alpha_p$ and $\beta_p$ are the unitary Satake parameters.

## Notes and history

Deligne introduced the geometric normalization of the reciprocity map in "Les constantes des équations fonctionnelles des fonctions L" (1973). With it the norm of the Weil group is the absolute value, and the action of Frobenius on the cohomology of a variety over a finite field has no inverse in the formulas. Tate's article [Tat79] uses the same conventions, and it is the reference for the definitions of this chapter: the Weil group, the $\varepsilon$-factors and the Weil-Deligne representations. Grothendieck's monodromy theorem is in the appendix of the paper of Serre and Tate on good reduction of abelian varieties (1968).

The standard additive characters and the self-dual measures are those of Tate's thesis (1950). The facts on local fields are in Serre's book [Ser79].

A reader who compares two sources must check five conventions first: the Frobenius, the normalization of the reciprocity map, the additive character, the normalization of the Satake parameters, and the variable of the $q$-expansions. The table of the first section lists the choices of the handbook.
