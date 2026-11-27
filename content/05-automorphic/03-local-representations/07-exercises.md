---
title: Exercises and notes
nodes: []
sources: [BH06, JL70]
status: drafted
drafted_by: writer@claude-opus-5-5
reviewed_by: []
---
## Exercises

1. With $\mathrm{vol}(K_0) = 1$, show by counting cosets that $T * T = c_{(2, 0)} + (q + 1) R$ in $\mathcal{H}$. Check the result with Theorem 3.4.6 and Proposition 3.4.8.
2. Let $f = \Delta$. Use Example 3.4.9, Theorem 3.5.5 and the identity $h_3 = e_1^3 - 2 e_1 e_2$ to compute $\tau(8)$.
3. Let $\chi_1, \chi_2$ be unramified with $z_1 \ne z_2$, and $V = \chi_1 \times \chi_2$. Show that $U$ acts on $V^{K_0(\mathfrak{p})}$ with the eigenvalues $q^{1/2} z_1$ and $q^{1/2} z_2$. Deduce that $U^2 - \lambda_T U + q z_1 z_2 = 0$, where $\lambda_T$ is the eigenvalue of $T$ on $V^{K_0}$. Compare with the $p$-stabilizations of a newform of level prime to $p$.
4. Show that the Kirillov function of the newvector of $\mathrm{St}$ is $\xi_0(y) = |y| \, 1_{\mathcal{O}}(y)$, and that $Z(s, \xi_0) = L(s, \mathrm{St})$. Check that $\xi_0$ has the shape of Proposition 3.5.4.
5. Let $\pi$ be supercuspidal. Show that the Kirillov function of its newvector is $1_{\mathcal{O}^\times}$ and that $Z(s, \xi_0) = 1$.
6. Let $\mu$ be a character of $K^\times$. Show that $c(\mu \pi(\chi_1, \chi_2)) = a(\mu \chi_1) + a(\mu \chi_2)$. If $\mu$ is ramified and $\chi_1, \chi_2$ are unramified, show that $c(\mu \pi(\chi_1, \chi_2)) = c(\mu \mathrm{St}) = 2 a(\mu)$.
7. Let $\eta$ be a character of $K^\times$. Compute the Jacquet module of $\eta \circ \det$. Use Theorem 3.1.7 to show that $\eta \circ \det$ embeds in $\chi_1 \times \chi_2$ if and only if $(\chi_1, \chi_2) = (\eta |\cdot|^{-1/2}, \eta |\cdot|^{1/2})$.
8. Let $p$ be odd. Show that there are $(p^2 - p)/2$ classes of characters $\theta$ of $\mathbb{F}_{p^2}^\times$ with $\theta \ne \theta^p$, up to $\theta \sim \theta^p$. Show that exactly $(p - 1)/2$ depth zero supercuspidal representations of $GL_2(\mathbb{Q}_p)$ have trivial central character. This generalizes Example 3.3.7.
9. Let $E$ be the curve $y^2 + y = x^3 - x^2 - 10 x - 20$ of Example 3.6.10. Count $E(\mathbb{F}_2)$ and $E(\mathbb{F}_3)$. Find the Satake parameters of $\pi_2$ and $\pi_3$, and check that they have absolute value $1$.
10. Let $\pi$ have trivial central character and $c(\pi) = 2$. Show that $\pi$ is $\eta \mathrm{St}$ with $\eta$ quadratic of conductor exponent $1$, or $\pi(\chi, \chi^{-1})$ with $a(\chi) = 1$, or supercuspidal. For $K = \mathbb{Q}_p$ with $p$ odd, show that there are exactly two representations of the first kind.

## Notes and history

The local theory of $GL_2$ was set up by Jacquet and Langlands [JL70], Chapter 1. They proved the irreducibility criterion and the existence and uniqueness of Whittaker models, and they used the Kirillov model throughout. Harish-Chandra and Jacquet related the Jacquet module to the compact support of matrix coefficients. Satake defined his transform in 1963 for all reductive $p$-adic groups. Casselman proved the theorem on newforms in 1973, as a local form of the theory of Atkin and Lehner. Shintani found the formula for the spherical Whittaker function of $GL_n$ in 1976, and Casselman and Shalika extended it to unramified groups in 1980. Kutzko proved that each supercuspidal of $GL_2$ is compactly induced.

The exposition follows [Bum97], Chapter 4, for the principal series, the Kirillov model and the Satake isomorphism, and [BH06], Chapters 2 to 4, for the Jacquet module, compact induction and the classification. Schmidt's survey of local newforms gives the conductors and the $U$ eigenvalues of all types in tables. Volume 6, Chapter 1 proves the general results that this chapter only states, and Volume 6, Chapter 3 attaches Langlands parameters to the supercuspidal representations.
