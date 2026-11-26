---
title: Exercises and notes
nodes: []
sources: [Tat79, Ser79, BH06, JL70, HT01, Hen00]
status: checked
drafted_by: writer@claude-opus-5-5
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## Exercises

1. Let $U$ be an open subgroup of finite index of $W_K$. Show that there is a unique finite separable extension $L / K$ in $\bar K$ with $U = W_K \cap G_L$, and that $U$ is normal if and only if $L / K$ is Galois. (Hint: show that the closure of $U$ in $G_K$ is open and that its intersection with $W_K$ is $U$.)
2. Let $r$ be the unramified representation of $W_K$ on $\mathbb{C}^2$ with $r(\Phi) = \left(\begin{smallmatrix} 1 & 1 \\ 0 & 1 \end{smallmatrix}\right)$. Show that $r$ does not extend to a continuous representation of $G_K$. Show that the same formula with values in $GL_2(\mathbb{Q}_\ell)$ does extend to $G_K$. Give an $\ell$-adic character of $W_K$ that does not extend to $G_K$.
3. Show that $\mathrm{Sp}(n)^\vee \cong \mathrm{Sp}(n) \otimes \|\cdot\|^{1-n}$. For $n \ge m \ge 1$ show that $\mathrm{Sp}(n) \otimes \mathrm{Sp}(m) \cong \bigoplus_{j=0}^{m-1} \mathrm{Sp}(n + m - 1 - 2j) \otimes \|\cdot\|^j$.
4. Let $(r, N)$ be a Weil-Deligne representation over an algebraically closed field $\Omega$ of characteristic $0$, and let $c \in \Omega^\times$. Show that $(r, N) \cong (r, cN)$. (Hint: use the generalized eigenspaces of $r(\Phi)^m$ for $m$ as in Proposition 2.1.11.)
5. Let $\rho$ be an $\ell$-adic representation of $W_K$ with monodromy operator $N$. Show that $\rho(I_K)$ is finite if and only if $N = 0$.
6. Let $A$ be an elliptic curve over $K$ with nonsplit multiplicative reduction. It is the twist of a Tate curve by the unramified quadratic character $\eta$. Show that $\mathrm{WD}(H^1) \cong \mathrm{Sp}(2) \otimes \eta \|\cdot\|^{-1}$, that $L(s, H^1) = (1 + q^{-s})^{-1}$, that $a(H^1) = 1$, and that $\varepsilon(1, H^1, \psi) = 1$ for $\psi$ of conductor $\mathcal{O}_K$.
7. Let $\chi$ be unramified and $V = \mathrm{Sp}(n) \otimes \chi$. Let $c(s, V) = \det(-q^{-s} r(\Phi) \mid V^I / V^I_N)$ be the correction factor of Definition 2.4.10. Show that $c(s, V) \, c(1 - s, V^\vee) = 1$.
8. Show that $a(V^\vee) = a(V)$ for each Weil-Deligne representation $V$.
9. Let $\pi$ be the trivial representation of $GL_2(K)$ and $\Phi_0$ the characteristic function of $M_2(\mathcal{O}_K)$. Show that $Z(\Phi_0, s, 1) = (1 - q^{-s-1/2})^{-1} (1 - q^{1/2-s})^{-1}$. Compare with the $L$-factor of $(\|\cdot\|^{1/2} \oplus \|\cdot\|^{-1/2}, 0)$ and with that of $\mathrm{St}$.
10. Let $\pi$ be an irreducible admissible representation of $GL_n(K)$ with central character $\omega_\pi$. Use Fourier inversion to show that $\gamma(s, \pi, \psi) \, \gamma(1 - s, \pi^\vee, \psi) = \omega_\pi(-1)$, and deduce that $\varepsilon(s, \pi, \psi) \, \varepsilon(1 - s, \pi^\vee, \psi) = \omega_\pi(-1)$.

## Notes and history

Weil introduced his group in 1951, in "Sur la théorie du corps de classes", to give a group whose representations carry the Hecke characters, which are not of finite order. Grothendieck proved the monodromy theorem in the 1960s in his work on the Néron models of abelian varieties, and Serre and Tate published it in the appendix of "Good reduction of abelian varieties" (1968). Deligne defined Weil-Deligne representations, their $L$-factors and $\varepsilon$-factors, and proved the existence of local constants, in "Les constantes des équations fonctionnelles des fonctions L" (Antwerp II, Lecture Notes in Math. 349, 1973). Langlands had found the local constants first, by a local proof that he did not publish. Tate's survey [Tat79] is still the best introduction, and Sections 1 to 4 of it cover this chapter. Godement and Jacquet defined the standard $L$-factor in "Zeta functions of simple algebras" (Lecture Notes in Math. 260, 1972), after the work of Jacquet and Langlands for $GL_2$ [JL70]. Jacquet computed the factors of all irreducible representations in "Principal $L$-functions of the linear group" (1979). The book [BH06] gives complete proofs for $GL_2$, with the Weil-Deligne side in Chapter 7. The theorems of Harris and Taylor [HT01] and of Henniart [Hen00] show that the factors of pairs determine the local Langlands correspondence. Fontaine's theory gives the analogue of the monodromy theorem for $\ell = p$. In the Lean project, the Weil group is in the folder `WeilGroup` and the Weil-Deligne representations and their $L$-factors are in `Statements/WeilDeligne.lean`. The $\varepsilon$-factors of Deligne and Langlands are not formalized yet.
