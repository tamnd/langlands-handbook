---
title: Exercises and notes
nodes: []
sources: [Ser79]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Exercises

1. Show that $\mathbb{Q}$ is not complete for $|\cdot|_p$. (Hint: for $p$ odd, choose an integer $a$ that is not a square in $\mathbb{Q}$ but is a nonzero square modulo $p$, and use Theorem 2.2.3.) Show that $\mathbb{Q}$ is dense in $\mathbb{R} \times \mathbb{Q}_2 \times \mathbb{Q}_3$.
2. Compute the first four digits of the $5$-adic expansions of $1/3$, of $-1/4$, and of the two square roots of $-1$ in $\mathbb{Z}_5$.
3. Let $p$ be a prime. Show that $\Phi_p(X + 1)$ is an Eisenstein polynomial over $\mathbb{Z}_p$, and deduce that $[\mathbb{Q}_p(\zeta_p) : \mathbb{Q}_p] = p - 1$. Deduce that the group of roots of unity of $\mathbb{Q}_p$ is $\mu_{p-1}$ for $p$ odd and $\{\pm 1\}$ for $p = 2$.
4. Let $p$ be odd and $u \in \mathbb{Z}_p^\times$ a unit that is not a square. Show that $\mathbb{Q}_p$ has exactly three quadratic extensions, namely $\mathbb{Q}_p(\sqrt u)$, $\mathbb{Q}_p(\sqrt p)$ and $\mathbb{Q}_p(\sqrt{up})$. Show that the first is unramified and the other two are totally ramified.
5. Show that $\mathbb{Z}_p$ is totally disconnected and has no isolated points. Show that the map $\sum a_i p^i \mapsto \sum 2 a_i \, 3^{-i-1}$ is a homeomorphism from $\mathbb{Z}_2$ onto the Cantor set.
6. (Krasner's lemma.) Let $K$ be complete for a nonarchimedean absolute value, and let $\alpha, \beta \in \bar K$, with $\alpha$ separable over $K$. Assume that $|\beta - \alpha| < |\alpha - \alpha'|$ for all conjugates $\alpha' \ne \alpha$ of $\alpha$. Show that $K(\alpha) \subset K(\beta)$. Deduce that each finite extension of $\mathbb{Q}_p$ is $F_v$ for some number field $F$ and some place $v$ of $F$.
7. Show that $\mathbb{Q}_2(\sqrt{-1}) / \mathbb{Q}_2$ is totally ramified, with uniformizer $1 + \sqrt{-1}$. Compute its different, and check that the exponent is larger than $e - 1$.
8. Let $L = \mathbb{Q}(\sqrt{-1}, \sqrt 2)$. Show that the decomposition group of the prime above 2 is the whole Galois group, and that it is not cyclic. Explain why this does not contradict Section 2.5.
9. Let $L / K$ be an unramified extension of nonarchimedean local fields. Show that $N_{L/K}(\mathcal{O}_L^\times) = \mathcal{O}_K^\times$. (Hint: the norm and the trace of the residue field extension are surjective. Show that the norm maps $U_L^{(i)}$ onto $U_K^{(i)}$ modulo $U_K^{(i+1)}$, and use completeness.)
10. Let $K$ be a nonarchimedean local field of characteristic 0. Show that $K$ contains only finitely many roots of unity. Compute the group of roots of unity of $\mathbb{Q}_3(\zeta_3)$ and of $\mathbb{Q}_5(\zeta_5)$.
11. Let $F = \mathbb{Q}(\sqrt[3]{2})$. With Theorem 2.5.1, determine the places of $F$ above $\infty$, $5$ and $7$, and their local degrees. (Hint: decide whether $X^3 - 2$ has a root in $\mathbb{Q}_5$ and in $\mathbb{Q}_7$.)
12. Let $K$ be a nonarchimedean local field of characteristic $p$. Show that the group $U_K^{(1)}$ is not finitely generated as a $\mathbb{Z}_p$-module. Deduce that $K$ has infinitely many cyclic extensions of degree $p$ (use Volume 3, Chapter 2).

## Notes and history

Hensel introduced the $p$-adic numbers in 1897, by analogy with the expansion of a function in power series at a point. Kürschák defined general absolute values in 1913, and Ostrowski proved his two theorems in 1916. Hasse used the $p$-adic numbers to prove the local-global principle for quadratic forms in 1921, and this made the local methods part of number theory. The approximation theorem is due to Artin and Whaples, in 1945. The Teichmüller representatives are from 1936. Dedekind defined the different in 1882 and proved the relation with ramification.

The exposition follows [Neu99], Chapter II. Neukirch treats valuations before he treats local fields, as here. Serre's book [Ser79] starts from discrete valuation rings, and its Chapters I to IV give the theory of the different and of the higher ramification groups in more detail. Fröhlich's chapter in [CF67] gives the classification of local fields and the structure of the unit group. Exercise 6 is the standard tool to compare local and global extensions, see [Neu99], Chapter II, Section 6. Exercise 9 is the first step of local class field theory, see Volume 3, Chapter 2.
