---
title: Exercises and notes
nodes: []
sources: [Ser79]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Exercises

1. Let $\alpha = \sqrt[3]{2}$ and $F = \mathbb{Q}(\alpha)$. Show that the discriminant of $1, \alpha, \alpha^2$ is $-108$. The polynomial $X^3 - 2$ is Eisenstein at 2, and $(X + 1)^3 - 2$ is Eisenstein at 3. Use these facts to show that the index of $\mathbb{Z}[\alpha]$ in $\mathcal{O}_F$ is prime to 2 and to 3. Deduce that $\mathcal{O}_F = \mathbb{Z}[\alpha]$ and $d_F = -108$.
2. Show that a Dedekind domain is a unique factorization domain if and only if it is a principal ideal domain.
3. Let $\mathcal{O}$ be a Dedekind domain, $\mathfrak{a}$ a nonzero ideal and $a \in \mathfrak{a}$ a nonzero element. Show that there is $b \in \mathfrak{a}$ with $\mathfrak{a} = (a, b)$. (Hint: use Proposition 1.2.5 for the primes that divide $a$.)
4. Let $\mathcal{O}$ be a Dedekind domain and $\mathfrak{p}$ a nonzero prime. Show that the localization $\mathcal{O}_\mathfrak{p}$ is a Dedekind domain with exactly one nonzero prime. Show that it is a principal ideal domain, and that each nonzero ideal is a power of $\mathfrak{p}\mathcal{O}_\mathfrak{p}$. Such a ring is a *discrete valuation ring*.
5. Show that the class number of $\mathbb{Q}(\sqrt{-6})$ is 2 and that the class number of $\mathbb{Q}(\sqrt{-14})$ is 4. For the second field, show that the class of a prime above 3 has order 4.
6. Show that $1 + \sqrt 2$ is a fundamental unit of $\mathbb{Q}(\sqrt 2)$. (Hint: a unit $a + b\sqrt 2 > 1$ with $a, b \in \mathbb{Z}$ has $a, b > 0$.) Find a fundamental unit of $\mathbb{Q}(\sqrt{3})$ and of $\mathbb{Q}(\sqrt{7})$.
7. Let $F$ be a number field of degree $n \ge 2$. Show that $|d_F| \ge (\pi/4)^{n} (n^n/n!)^2$, and deduce that $n / \log |d_F|$ is bounded. Thus the degree of $F$ is bounded in terms of $|d_F|$.
8. Factor 2, 3, 5 and 7 in the ring of integers of $\mathbb{Q}(\sqrt[3]{2})$ with Theorem 1.4.2 and Exercise 1. Check the fundamental identity in each case.
9. Let $L / F$ be Galois, $\mathfrak{P}$ a prime of $L$ and $Z$ the decomposition field of $\mathfrak{P}$. Show that $\mathfrak{P}$ is the only prime of $L$ above $\mathfrak{P} \cap Z$. Show that $e(\mathfrak{P} \cap Z / \mathfrak{p}) = f(\mathfrak{P} \cap Z / \mathfrak{p}) = 1$.
10. Let $L / F$ be Galois with group $G$, and let $\mathfrak{p}$ be a prime that is unramified in $L$. Assume that $\mathfrak{p}$ is inert. Show that $G$ is cyclic. Deduce that in $\mathbb{Q}(\zeta_8)$ no prime is inert.
11. Show that $\zeta_8 + \zeta_8^{-1} = \sqrt 2$ for a suitable choice of $\zeta_8$. Show that the subgroup of $(\mathbb{Z}/8\mathbb{Z})^\times$ that fixes $\sqrt 2$ is $\{\pm 1\}$. Deduce the second supplementary law $(2/p) = (-1)^{(p^2-1)/8}$ for odd primes $p$, with the method of Theorem 1.5.8.
12. Let $m \ge 2$. Show that a prime $p \nmid m$ divides $\Phi_m(a)$ for some integer $a$ if and only if $p \equiv 1 \pmod m$. Deduce that there are infinitely many primes $p \equiv 1 \pmod m$. (Hint: consider $\Phi_m(m N)$ for large $N$.)
13. Let $F = \mathbb{Q}(\sqrt{-5})$ and $L = F(i)$. Show that no prime of $F$ ramifies in $L$, although some prime ramifies in each extension of $\mathbb{Q}$ other than $\mathbb{Q}$ by Corollary 1.3.6 and Theorem 1.4.3. (Hint: $L$ contains $\mathbb{Q}(i)$ and $\mathbb{Q}(\sqrt 5)$. Compute the ramification indices of 2 and 5 in these fields.)
14. Let $p$ be an odd prime. Show that the Gauss sum $g = \sum_{a \in \mathbb{F}_p^\times} (a/p) \zeta_p^a$ satisfies $g^2 = p^*$. Use it to give a second proof of Lemma 1.5.7.

## Notes and history

Kummer introduced ideal numbers in the 1840s for the fields $\mathbb{Q}(\zeta_p)$, in his work on Fermat's last theorem. Dedekind replaced them by ideals in the supplements to Dirichlet's lectures on number theory, from 1871 to 1894, and proved the unique factorization of ideals in all rings of integers. Kronecker gave a different theory of divisors at the same time. Dirichlet proved the unit theorem in 1846. Minkowski's geometry of numbers appeared in 1896, and Minkowski proved in 1891 that $|d_F| > 1$ for $F \ne \mathbb{Q}$. Hilbert's report on algebraic number fields of 1897 contains the theory of the decomposition and inertia groups. Frobenius defined his substitution in 1896, and Chebotarev proved his density theorem in 1922. Quadratic reciprocity was proved first by Gauss in 1796, and the cyclotomic proof of Section 1.5 goes back to Gauss's work on cyclotomy.

The exposition follows [Neu99], Chapter I. The proof of the integrality of $\mathbb{Z}[\zeta_p]$ in Theorem 1.5.4 is a standard one, and the proof of Lemma 1.5.7 through ramification avoids the Gauss sums of Exercise 14. Serre's book [Ser79], Chapter I, gives a short account of Dedekind domains and of the decomposition of primes, with the same notation for the decomposition and inertia groups. Exercise 12 is a special case of Dirichlet's theorem on primes in arithmetic progressions. The general case needs the L-functions of Volume 3.
