---
title: Exercises
nodes: []
sources: [CF67]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Exercises

The exercises use the notation of Chapter 3. Some of them give facts that later volumes use.

**Exercise 1.** Show that the restricted product $\prod'(\mathbb{Q}_p, \mathbb{Z}_p)$ is not compact, and that its topology is strictly finer than the topology of a subspace of $\prod_p \mathbb{Q}_p$. Show that it is not locally compact for the subspace topology.

**Exercise 2.** Show that $\mathbb{A}_{\mathbb{Q},f} = \hat{\mathbb{Z}} \otimes_\mathbb{Z} \mathbb{Q} = \bigcup_{n \ge 1} \frac{1}{n} \hat{\mathbb{Z}}$, and that $\mathbb{A}_{\mathbb{Q},f} / \hat{\mathbb{Z}} \cong \mathbb{Q}/\mathbb{Z}$. Deduce that $\mathbb{A}_{\mathbb{Q},f} = \mathbb{Q} + \hat{\mathbb{Z}}$, which is a part of Proposition 3.2.2.

**Exercise 3.** Show that the solenoid $\mathbb{A}_\mathbb{Q} / \mathbb{Q}$ is connected but not path connected. Show that its Pontryagin dual is isomorphic to $\mathbb{Q}$, with the discrete topology. (Hint: use Proposition 3.1.4 and the character $\psi$ of Section 3.3.)

**Exercise 4.** Let $\psi = \prod_v \psi_v$ be the character of $\mathbb{A}_\mathbb{Q}$ of Section 3.3. Show that $\psi$ is trivial on $\mathbb{Q}$. Show that each continuous character of $\mathbb{A}_\mathbb{Q}$ that is trivial on $\mathbb{Q}$ has the form $x \mapsto \psi(ax)$ for exactly one $a \in \mathbb{Q}$.

**Exercise 5.** Show that $J_F^1$ is closed in $\mathbb{A}_F$, and that on $J_F^1$ the topology of a subspace of $\mathbb{A}_F$ agrees with the topology of a subspace of $J_F$. (Hint: the product formula prevents the behaviour of the sequence in the proof of Proposition 3.4.2.) Compare with Proposition 3.4.2, which shows that the two topologies differ on $J_F$.

**Exercise 6.** Assume that $\mathrm{Cl}_F$ is finite and that $\lambda(\mathcal{O}_F^\times)$ is a complete lattice in the hyperplane $H$ of Section 3.5. Use the exact sequence of Theorem 3.4.7 to prove that $C_F^1$ is compact. This is the converse of Corollaries 3.5.3 and 3.5.4.

**Exercise 7.** Show that $C_F$ is not compact, and that its connected component of 1 is not open. Describe the connected component of 1 in $C_\mathbb{Q}$, using Example 3.4.8.

**Exercise 8.** Let $L / F$ be a finite extension. Define the norm map $N_{L/F} : J_L \to J_F$ by $N_{L/F}(x)_v = \prod_{w \mid v} N_{L_w / F_v}(x_w)$. Show that it is continuous, that it extends the norm $L^\times \to F^\times$, and that $|N_{L/F}(x)|_{\mathbb{A}_F} = |x|_{\mathbb{A}_L}$. Deduce that it induces a map $C_L \to C_F$.

**Exercise 9.** Let $S$ be a finite set of places of $F$ that contains the infinite places. Use the method of Corollary 3.5.4 to prove that the group $\mathcal{O}_{F,S}^\times$ of $S$-units is the product of $\mu(F)$ and a free abelian group of rank $|S| - 1$.

**Exercise 10.** Compute $\mathrm{vol}(\mathcal{O}_K^\times)$ and $\mathrm{vol}(U_K^{(1)})$ for the measure $dx / |x|_K$ on $K^\times$, where $K$ is a nonarchimedean local field with residue field of order $q$. Compute the volume of $\hat{\mathbb{Z}}^\times$ for the product of the standard multiplicative measures, and explain the normalization factor $q / (q - 1)$ of Section 3.3.

**Exercise 11.** Let $F = \mathbb{Q}(i)$. Use Theorem 3.5.5 with $v_0 = \infty$ to show that, for each finite set of primes $\mathfrak{p}_1, \dots, \mathfrak{p}_k$ of $\mathbb{Z}[i]$ and each choice of residues, there is a Gaussian integer with these residues modulo $\mathfrak{p}_1^{n}, \dots, \mathfrak{p}_k^{n}$. Compare with Proposition 1.2.5.

**Exercise 12.** Show that Theorem 3.5.5 fails for the multiplicative group: for $F = \mathbb{Q}$, the subgroup $\mathbb{Q}^\times$ is not dense in the finite ideles $J_{\mathbb{Q},f} = \prod'(\mathbb{Q}_p^\times, \mathbb{Z}_p^\times)$. (Hint: let $N \ge 7$ and let $V$ be the kernel of the map $\hat{\mathbb{Z}}^\times \to (\mathbb{Z}/N\mathbb{Z})^\times$. Use $\mathbb{Q}^\times \cap \hat{\mathbb{Z}}^\times = \{\pm 1\}$ to show that the image of $\mathbb{Q}^\times$ in $J_{\mathbb{Q},f} / V$ is a proper subgroup.)

## Notes and history

Chevalley introduced the ideles between 1936 and 1940 to give global class field theory a form without analysis. He called them "éléments idéaux", and Hasse shortened the name. Weil introduced the adeles, first as "valuation vectors", in his work on the Riemann hypothesis for curves and on the zeta functions of number fields. Artin and Whaples characterized global fields in 1945 by the product formula for their absolute values, which is the axiomatic form of Theorem 3.3.4. Tate's thesis of 1950, published as Chapter XV of [CF67], used harmonic analysis on $\mathbb{A}_F$ and $J_F$ to prove the analytic continuation and the functional equation of Hecke L-functions. Iwasawa found the same proof independently. The proofs of Section 3.5 follow Chapter II of [CF67]. Weil's *Basic number theory* treats all global fields in this way, and it proves the same theorems for function fields with the same arguments.
