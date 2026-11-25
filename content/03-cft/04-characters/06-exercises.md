---
title: Exercises and notes
nodes: []
sources: [Tat79, Ser79]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Exercises

1. Show that the number of characters of $\mathcal{O}_K^\times$ with conductor exponent exactly $n$ is 1 for $n = 0$, $q - 2$ for $n = 1$, and $(q-1)^2 q^{n-2}$ for $n \ge 2$.
2. Show that a character $\chi$ of $K^\times$ is unitary if and only if its exponent is 0, and that it has finite order if and only if $\chi(\varpi)$ is a root of unity for one, or every, uniformizer $\varpi$.
3. Let $K = \mathbb{Q}_2$. Use the norm groups of Remark 2.5.6 and Exercise 9 of Chapter 2 to show that $a(\chi_{-1}) = 2$, $a(\chi_2) = a(\chi_{-2}) = 3$ and $a(\chi_5) = 0$.
4. (Theorem 4.2.2 for Lubin-Tate fields.) Let $L = K_{\varpi,m}$, let $f = \varpi X + X^q$ and let $\lambda$ be a uniformizer of $L$ in $\Lambda_{f,m}$. For $u \in U^{(k)} \smallsetminus U^{(k+1)}$ with $0 \le k < m$, show that $v_L([u]_f(\lambda) - \lambda) = q^k$. Deduce that the lower ramification group $\mathrm{Gal}(L/K)_i$ corresponds to $U^{(k)}/U^{(m)}$ for $q^{k-1} \le i \le q^k - 1$. Use the Herbrand function to show that $\mathrm{Gal}(L/K)^n$ corresponds to $U^{(n)}/U^{(m)}$, as Theorem 4.2.2 and Theorem 3.5.5 predict.
5. Let $\chi$ be a unitary ramified character with $a(\chi) = n$. Show directly that $|G(\chi^{-1}, \psi)|^2 = q^n$. Hint: expand the product $G \bar G$ and use that $\sum_{u} \psi(tu/\varpi^n)$ over $u \in \mathcal{O}_K/\varpi^n$ vanishes unless $t \in \varpi^n \mathcal{O}_K$.
6. Show that the formula of Proposition 4.3.3 does not depend on the choice of the uniformizer $\varpi$.
7. Let $\eta$ be a primitive Dirichlet character modulo $p^n$, and let $\psi(x) = e^{2\pi i\{x\}_p}$. Show that $\varepsilon(\chi_\eta, s, \psi) = p^{-ns} \tau(\bar\eta)$, where $\tau(\bar\eta) = \sum_{a \bmod p^n} \bar\eta(a) e^{2\pi i a/p^n}$ is the classical Gauss sum.
8. (The arithmetic normalization.) Let $\phi$ be an unramified character of $W_K$ and let $\chi' = \phi \circ \mathrm{Art}_K$. Show that $L(\phi, s) = L(\chi'^{-1}, s)$. Which formula of Theorem 4.2.3 changes in the same way?
9. Let $T = \mathbb{G}_m^2$. Write the bijection of Theorem 4.5.2 in coordinates, and check that an automorphism of $T$ given by a matrix in $GL_2(\mathbb{Z})$ acts compatibly on the two sides.
10. Let $L / K$ be a separable quadratic extension with Galois group $\{1, \sigma\}$, and let $T^1$ be the kernel of the norm $\mathrm{Res}_{L/K} \mathbb{G}_m \to \mathbb{G}_m$. Show that $X^*(T^1) \cong \mathbb{Z}$ with $\sigma$ acting by $-1$, so that $\hat{T^1} = \mathbb{C}^\times$ with $\sigma$ acting by inversion. Use Hilbert's Theorem 90 to show that $x \mapsto x / \sigma(x)$ induces an isomorphism $L^\times / K^\times \cong T^1(K)$, so that the characters of $T^1(K)$ are the characters of $L^\times$ that are trivial on $K^\times$.

## Notes and history

The local zeta integral and its functional equation are in Tate's thesis, "Fourier analysis in number fields and Hecke's zeta-functions", written in 1950 and printed in the volume of Cassels and Frohlich in 1967. Iwasawa found the same theory at about the same time. Tate's article [Tat79], Section 3, gives the local constants in the normalization of this chapter and states Theorem 4.3.8. Serre's book [Ser79], Chapters IV, V and XV, gives the ramification groups, the theorem of Hasse and Arf, and Theorem 4.2.2.

Langlands found the existence of the local constants of Theorem 4.3.8 in a long manuscript of about 1970, which was not published. Deligne gave a proof with global methods in "Les constantes des equations fonctionnelles des fonctions L" (Modular functions of one variable II, Lecture Notes in Mathematics 349, 1973). Deligne also fixed the geometric normalization of Remark 4.3.7. The general correspondence for tori, Theorem 4.5.6, is in Langlands' manuscript "Representations of abelian algebraic groups" of 1968, published in the Pacific Journal of Mathematics in 1997. Jiu-Kang Yu wrote a modern account in "On the local Langlands correspondence for tori" (2009).

Exercise 4 is a standard complement to Lubin-Tate theory. Every finite abelian extension of $K$ lies in a field $K_{\varpi,m} K_r$ by Theorem 3.5.4, and the upper numbering is compatible with quotients, so the exercise gives a second proof of Theorem 4.2.2. Exercise 10 is the simplest torus that is not induced and not split. Its characters appear in the theory of the dihedral representations of $GL_2$.

The Lean statement of Theorem 4.2.3 is `Langlands.LocalReciprocityGL1`, as in Chapter 2. It is stated and not proved. The other statements of this chapter are not stated in the Lean project yet.
