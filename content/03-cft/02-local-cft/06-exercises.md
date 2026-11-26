---
title: Exercises and notes
nodes: []
sources: [Ser67, Ser79, Mil20, Tat79]
status: checked
drafted_by: writer
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## Exercises

1. Let $L$ be a finite abelian extension of $K$ with ramification index $e$ and residue degree $f$. Show that $[\mathcal{O}_K^\times : N_{L/K}(\mathcal{O}_L^\times)] = e$. Deduce that a unit is a norm from a totally ramified extension of degree $n$ only for a subgroup of index $n$ of $\mathcal{O}_K^\times$.
2. Let $p$ be odd and let $\zeta$ be a primitive $p$-th root of unity. Show that $(1 - \zeta)^{p-1} / p$ is a unit of $\mathbb{Z}_p[\zeta]$ that is congruent to $-1$ modulo $1 - \zeta$. Deduce that $\mathbb{Q}_p(\zeta) = \mathbb{Q}_p(\sqrt[p-1]{-p})$, and check Proposition 2.5.3 for $n = 1$ with this description.
3. Let $K = \mathbb{Q}_p$ and $L = K_2$. Write the map $r_{L/K}$ explicitly and show that the corresponding character of $\mathbb{Q}_p^\times$ is $x \mapsto (-1)^{v_p(x)}$. Show that it is the character $\chi_\varepsilon$ of Example 2.5.5.
4. Let $L$ and $L'$ be finite abelian extensions of $K$. Show that the norm group of $L \cap L'$ is the product of the norm groups of $L$ and $L'$. Use this to show that $[L L' : K] \, [L \cap L' : K] = [L : K] \, [L' : K]$. Give a proof of the same formula with Galois theory alone.
5. (Kummer theory.) Assume that $K$ has characteristic 0 and contains the group $\mu_m$ of $m$-th roots of unity. Let $M$ be the compositum of all abelian extensions of $K$ of exponent dividing $m$. Show that $N_{M/K}(M^\times) = (K^\times)^m$ and that $[M : K] = [K^\times : (K^\times)^m]$. Compute this index for $K = \mathbb{Q}_p(\zeta_p)$ and $m = p$.
6. (Norm limitation.) Assume that $K$ has characteristic 0. Let $L$ be a finite separable extension of $K$, not necessarily Galois, and let $L_0$ be the largest subextension of $L$ that is abelian over $K$. Show that $N_{L/K}(L^\times) = N_{L_0/K}(L_0^\times)$. (Hint: the norm group contains the open subgroup $(K^\times)^{[L:K]}$. Use part 1 of Theorem 2.4.2 and the existence theorem.)
7. Show that the transfer $W_K^{ab} \to W_L^{ab}$ is continuous. Show that the composite $j \circ \mathrm{Ver} : W_K^{ab} \to W_K^{ab}$ of the transfer with the map $j$ induced by the inclusion is $g \mapsto g^{[L:K]}$.
8. Show that the characters of $K^\times$ that are trivial on $\mathcal{O}_K^\times$ are the maps $x \mapsto z^{v(x)}$ for $z \in \mathbb{C}^\times$. Show that under Corollary 2.3.6 such a character corresponds to the unramified character of $W_K$ that sends a geometric Frobenius to $z$. What changes in the arithmetic normalization?
9. (The prime 2.) Show that the norm group of $\mathbb{Q}_2(\sqrt{-1})$ is $2^{\mathbb{Z}} \times (1 + 4 \mathbb{Z}_2)$. For each of the other six quadratic extensions of $\mathbb{Q}_2$ in Remark 2.5.6, find two generators of the norm group modulo squares. Check that the seven groups are the seven subgroups of index 2 of $\mathbb{Q}_2^\times$ that contain the squares.
10. Show that the image of $W_K^{ab}$ in $\mathrm{Gal}(K^{ab}/K)$ is dense and not closed. Show that the map $W_K^{ab} \to \mathrm{Gal}(K^{ab}/K)$ is not a homeomorphism onto its image.
11. Let $L$ be a finite abelian extension of $K$ of degree $m$, and let $\varpi$ be a uniformizer. Let $E \subset L K_m$ be the fixed field of $r_K(\varpi)$. Show that $E$ is totally ramified over $K$ and that $L \subset E K_m$. Deduce that every finite abelian extension of $K$ lies in the compositum of a totally ramified abelian extension and an unramified extension.

## Notes and history

Local class field theory was first obtained by Hasse in 1930 as a consequence of global class field theory. Chevalley gave the first purely local proof in 1933, and he introduced the idele group shortly after. The cohomological proof of Remark 2.1.4 is due to Hochschild, Nakayama, Weil, Artin and Tate in the years around 1950, and Tate proved the theorem of Remark 2.1.4 in 1952, in a form that Nakayama later extended. The standard expositions are Serre's book [Ser79], Chapters XII to XV, his chapter [Ser67] in the volume of Cassels and Frohlich, and Milne's notes [Mil20], Chapters I to III. These sources use the arithmetic normalization. Lubin and Tate gave the explicit construction of Chapter 3 in 1965. Hazewinkel and Neukirch later gave proofs of the reciprocity law without cohomology, and Neukirch's book "Class field theory" follows this route.

The Weil group form of Theorem 2.3.3 and the geometric normalization follow Tate's article [Tat79] and Deligne's article on local constants of 1973. The proof of Section 2.3 shows that the Weil group form adds nothing to the classical theorem and the existence theorem, except the bookkeeping of the topology. The uniqueness argument of Theorem 2.1.3 is from [Mil20], Chapter I.

Exercise 6 is the norm limitation theorem. The theorem is also true in characteristic $p$, but the hint fails there, because $(K^\times)^p$ is not open. Exercise 9 is the classical computation of the Hilbert symbol at 2.

In the Lean project tamnd/langlands-lean, Theorem 2.1.2 is the theorem `Langlands.Bridge.finiteAbelianLocalReciprocity`, and the existence theorem is `Langlands.Bridge.localExistence`. Both come from the port of n-yamaguchi-0729/ClassFieldTheory in the folder `Langlands/Ported/NYLL`, which proves finite abelian local reciprocity and the existence theorem through Lubin-Tate theory. Theorem 2.3.3 is stated as `Langlands.LocalReciprocityGL1` and proved as `Langlands.localReciprocityGL1` in the file `Langlands/Reciprocity/GL1.lean`. The proof follows Section 2.3. For existence, it composes the absolute local Artin map of the port with the inverse of the injection $W_K^{ab} \to \mathrm{Gal}(K^{ab}/K)$ of Proposition 2.3.1. For uniqueness, it uses the uniqueness of coherent families of finite Artin maps in the port. The fidelity check `Langlands.Fidelity.finiteAbelian_of_localReciprocityGL1` proves that the Lean statement of Theorem 2.3.3 implies the finite form.
