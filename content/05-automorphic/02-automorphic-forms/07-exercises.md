---
title: Exercises and notes
nodes: []
sources: [JL70]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Exercises

1. Let $\chi$ be a character of $\mathbb{Q}^\times\backslash\mathbb{A}^\times$ and $\varphi = \chi \circ \det$. Show that $\varphi_U = \varphi$ and $W_\varphi = 0$. Deduce that Theorem 2.4.3 fails for automorphic forms that are not cuspidal.
2. Show that $\mathcal{A}_0(G)$ is stable under right translation by $G(\mathbb{A}_f)$ and $K_\infty$ and under right derivatives.
3. Derive (2.1.2) from (2.1.1).
4. Let $F$ be a smooth function of weight $k$ on $G(\mathbb{R})^+$, invariant under $Z(\mathbb{R})^+$, with $LF = 0$. Show that $F = F_f$ for a holomorphic function $f$ on $\mathbb{H}$, in the notation of Example 2.1.8.
5. Derive (2.4.1) from the recursion $a_{p^{m+1}} = a_pa_{p^m} - p^{k-1}a_{p^{m-1}}$.
6. Show that $W_{0,\mu}(t) = (t/\pi)^{1/2}K_\mu(t/2)$ satisfies Whittaker's equation with $\kappa = 0$, given that $K_\mu$ satisfies $K'' + u^{-1}K' - (1 + \mu^2u^{-2})K = 0$.
7. Let $f \in S_k(\Gamma_0(N))$. Use Lemma 2.1.4, Lemma 2.5.1 and Proposition 2.4.9, not Example 2.4.4, to show that $W_{\phi_f}(a(y)) = 0$ when $y_\infty < 0$.
8. Let $\varphi \in \mathcal{A}_0(G)$ be fixed by $K_0(N)$. Show that $W_\varphi(a(y)) = 0$ unless $y_f \in \widehat{\mathbb{Z}}$.
9. Let $s \in \mathbb{R}$ and $\epsilon_1 = \epsilon_2 = 0$. Show that $I(\chi_1, \chi_2)$ has a positive definite inner product with orthogonal weight spaces, $R^* = -L$ and $\rho(\varepsilon)$ unitary if and only if $0 < s < 1$.
10. Show that an irreducible $(\mathfrak{g}, K_\infty)$-module of finite dimension $d \ge 2$ has no positive definite inner product with $R^* = -L$.

## Notes and history

The adelic theory of automorphic forms on $GL_2$ is due to Gelfand, Graev and Piatetski-Shapiro and to Jacquet and Langlands [JL70]; Godement and Harish-Chandra gave the analytic foundations. The classification of Section 2.1 goes back to Bargmann (1947). Multiplicity one for $GL_2$ is in [JL70], Chapter II, and Shalika and Piatetski-Shapiro proved it for $GL_n$. [Bum97] Chapters 2 and 3, [Gel75] and [GH24] give full accounts. The Lean project has `Langlands.AdelicGL`, `Langlands.AdeleQuotient`, `Langlands.IsCuspForm`, `Langlands.HasVanishingConstantTerm`, `Langlands.Fidelity.IsAutomorphicFormGL`, `Langlands.IsWhittakerFunctional`, `Langlands.IsGeneric`, `Langlands.SmoothRep.IsJacquetCuspidal`, `Langlands.IsDiscreteSeries`, `Langlands.IsMaassCuspForm`, `Langlands.hyperbolicLaplacian` and `Langlands.SelbergEigenvalue`. It has no $(\mathfrak{g}, K)$-modules, and none of the theorems of this chapter is proved there.
