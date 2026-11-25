---
title: Exercises and notes
nodes: []
sources: [Ser67, Tat79, Wil95, BCDT01, Del74, BLGHT11]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Exercises

1. Let $p$ be an odd prime. Use the example of the first section to show that the composite map $\mathbb{Q}_p^\times \to \mathrm{Gal}(\mathbb{Q}_p(\zeta_p) / \mathbb{Q}_p) \cong (\mathbb{Z}/p\mathbb{Z})^\times$ sends $p^n u$ to $u \bmod p$. Conclude that the norm group of $\mathbb{Q}_p(\zeta_p)$ is $p^{\mathbb{Z}} \times (1 + p\mathbb{Z}_p)$.
2. Show that the norm group of the unramified extension of degree $f$ of a local field $K$ is the set of $x \in K^\times$ whose valuation is divisible by $f$.
3. Show that the idele class group $C_{\mathbb{Q}}$ is isomorphic to $\hat{\mathbb{Z}}^\times \times \mathbb{R}_{>0}$ as a topological group.
4. Count the points of the curve $y^2 + y = x^3 - x^2 - 10x - 20$ over $\mathbb{F}_2$ and over $\mathbb{F}_3$, and check the first two columns of the table of the second section.
5. Let $E$ be the curve $y^2 = x^3 - x$ and let $p \equiv 3 \pmod 4$ be a prime. Show that $a_p(E) = 0$. (Use the map $x \mapsto -x$ and the fact that $-1$ is not a square modulo $p$.)
6. Show that the measure $\frac{2}{\pi} \sin^2 \theta \, d\theta$ on $[0, \pi]$ has total mass 1. Show that it gives the interval $[0, \pi/4]$ the mass $\frac14 - \frac{1}{2\pi}$, and compare this number with the mass $\frac14$ of the uniform measure.
7. Let $k \ge 1$ and $a \in \mathbb{R}$. Show that $|a| \le 2 p^{(k-1)/2}$ if and only if both roots of $X^2 - a X + p^{k-1}$ have absolute value $p^{(k-1)/2}$.
8. Let $\chi$ be a character of $K^\times$ and let $\pi = \chi \circ \det$, a representation of $GL_n(K)$ of dimension 1. Show that the central character of $\pi$ is $\chi^n$. Use the properties of the local correspondence to find the determinant of $\mathrm{rec}_n(\pi)$.
9. Let $G = H = GL_1$ over a number field $F$, and let $u$ be the L-homomorphism that is $z \mapsto z^2$ on the factor $\mathbb{C}^\times$ of the L-group. Show that the conjecture of functoriality holds for $u$, with $\Pi = \pi^2$.

## Notes and history

Takagi proved the existence theorem of global class field theory in 1920, and Artin proved the reciprocity law in 1927. Hasse found the local theory in 1930, and Chevalley introduced the ideles in the 1930s. Lubin and Tate gave the explicit local theory in 1965. Serre's chapter in Cassels and Fröhlich [Ser67] gives the cohomological proof, and Tate's article [Tat79] gives the Weil groups and the normalizations of the handbook.

Langlands described the program in a letter to Weil in January 1967 and in the article "Problems in the theory of automorphic forms" (1970). The correspondence for $GL_2$ over $\mathbb{Q}$ goes back to Eichler and Shimura. The modularity theorem is due to Wiles and Taylor-Wiles in the semistable case [Wil95] and to Breuil, Conrad, Diamond and Taylor in general [BCDT01]. Deligne proved the bound of Ramanujan and Petersson in [Del74]. The Sato-Tate theorem is the work of Clozel, Harris, Shepherd-Barron and Taylor, completed in [BLGHT11].

Three surveys are good companions to this chapter: Gelbart's "An elementary introduction to the Langlands program" (Bull. Amer. Math. Soc., 1984), Arthur's "The principle of functoriality" (Bull. Amer. Math. Soc., 2003) and Calegari's survey of reciprocity since Fermat's last theorem (2021). The first one is the most elementary. The last one describes the results on reciprocity since the proof of Wiles.
