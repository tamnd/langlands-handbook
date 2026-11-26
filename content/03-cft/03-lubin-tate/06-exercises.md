---
title: Exercises and notes
nodes: []
sources: [Ser67, Mil20]
status: checked
drafted_by: writer
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## Exercises

1. Let $F$ be a formal group law over $A$. Show that there is a unique $i(X) \in X A[[X]]$ with $F(X, i(X)) = 0$. Hint: build $i$ degree by degree, and use $F(X, Y) \equiv X + Y$ modulo degree 2.
2. Let $F$ be a formal group law over $A$. Show that $F(X, 0) = X$. Hint: let $g(X) = F(X, 0)$, and use associativity to show $g(g(X)) = g(X)$. Then use that $g$ has an inverse for composition.
3. Let $f = \varpi X + X^q$. Show that $F_f(X, Y) \equiv X + Y$ modulo degree $q$, and that the homogeneous part of degree $q$ of $F_f$ is
$$-\frac{(X + Y)^q - X^q - Y^q}{\varpi - \varpi^q}.$$
Check that its coefficients lie in $\mathcal{O}_K$.
4. (The Carlitz module.) Let $K = \mathbb{F}_q((t))$, $\varpi = t$ and $f = tX + X^q$. Show that $[a]_f$ is an $\mathbb{F}_q$-linear polynomial for each $a \in \mathbb{F}_q[t]$, and compute $[t^2]_f$. Show that $\Lambda_{f,1}$ is an $\mathbb{F}_q$-vector space of dimension 1 inside $\bar K$.
5. Let $f, g, h \in \mathcal{F}_\varpi$ and $a, b \in \mathcal{O}_K$. Show that $[a]_{h,g} \circ [b]_{g,f} = [ab]_{h,f}$.
6. Let $f, g \in \mathcal{F}_\varpi$. Show that $[1]_{g,f}$ gives an isomorphism of $\mathcal{O}_K$-modules $\Lambda_{f,n} \to \Lambda_{g,n}$ that commutes with the action of $G_K$. Conclude that the Lubin-Tate character $\chi_\varpi$ does not depend on $f$.
7. Show that $\mathbb{Q}_p(\zeta_p) = \mathbb{Q}_p(\sqrt[p-1]{-p})$. Hint: compare Example 3.3.4 and Example 3.3.5 for the two series $(1+X)^p - 1$ and $pX + X^p$ in $\mathcal{F}_p$.
8. Let $u \in \mathcal{O}_K^\times$. Show that $K_{u\varpi, 1} = K_{\varpi, 1}$ if and only if $u \in U^{(1)}$. Hint: use Example 3.3.5 and Kummer theory, or Theorem 3.5.1 with $n = 1$.
9. Let $\chi_{cyc} : G_{\mathbb{Q}_p} \to \mathbb{Z}_p^\times$ be the $p$-adic cyclotomic character. Show that $\chi_{cyc}(\mathrm{rec}_{\mathbb{Q}_p}(x)) = x |x|_p$ for $x \in \mathbb{Q}_p^\times$. What is the formula in the arithmetic normalization?
10. Let $f = \varpi X + X^q$, $n \ge 2$, and let $\lambda_n \in \Lambda_{f,n} \smallsetminus \Lambda_{f,n-1}$. Put $\lambda_{n-1} = f(\lambda_n)$. Show that $f(X) - \lambda_{n-1}$ is the minimal polynomial of $\lambda_n$ over $K_{\varpi,n-1}$, and that $N_{K_{\varpi,n}/K_{\varpi,n-1}}(\lambda_n) = (-1)^{q+1} \lambda_{n-1}$. Deduce Theorem 3.3.3, part 3, by induction on $n$.

## Notes and history

Lubin and Tate introduced their formal groups in "Formal complex multiplication in local fields", Annals of Mathematics 81 (1965). The title refers to the analogy with the theory of complex multiplication, in which the torsion points of an elliptic curve with complex multiplication generate the abelian extensions of an imaginary quadratic field. The analogy is exact for $\mathbb{Q}_p$, where the formal group is $\mathbb{G}_m$ and the torsion points are the roots of unity. Lazard and Frohlich developed the general theory of formal groups of dimension 1 in the same period.

The exposition of this chapter follows Serre's chapter [Ser67] and Milne's notes [Mil20], Chapter I. Both use the arithmetic normalization, so their formula has $[u^{-1}]_f$ where Theorem 3.5.5 has $[u]_f$. The proof of Theorem 3.4.3 with the completion of $K^{ur}$ is the one of Lubin and Tate. Iwasawa gave a different account of the explicit reciprocity law in his book "Local class field theory" (1986), and Neukirch's book gives a third. Theorem 3.5.5 says that the Lubin-Tate character, read through $\mathrm{rec}_K$, is the projection $K^\times \to \mathcal{O}_K^\times$ attached to $\varpi$. This fact generalizes the classical formula for the cyclotomic character in Exercise 9.

Lubin-Tate formal groups have uses far beyond class field theory. Their deformations give the Lubin-Tate tower, whose cohomology realizes the local Langlands correspondence for $GL_n$ in the proof of Harris and Taylor. The case $n = 1$ of that picture is the content of this chapter.

Exercise 10 gives a proof of the norm formula that avoids the Eisenstein polynomial $g_n$. Exercise 4 is the local version of the Carlitz module, which Carlitz introduced in 1935 for the field $\mathbb{F}_q(t)$.

The Lean proof of the existence theorem uses the port of n-yamaguchi-0729/ClassFieldTheory, which proves finite abelian local reciprocity and existence through Lubin-Tate theory. Remark 3.5.8 gives the names. The other statements of this chapter are not stated in the Lean project yet.
