---
title: The general conjectures
nodes: []
sources: [Tat79]
status: drafted
drafted_by: writer
reviewed_by: []
---
## The general conjectures

### The local Langlands correspondence for GL(n)

Let $K$ be a nonarchimedean local field. For $n \ge 1$, let $\mathrm{Irr}_n(K)$ be the set of isomorphism classes of irreducible smooth representations of $GL_n(K)$ on complex vector spaces. Let $\Phi_n(K)$ be the set of isomorphism classes of Frobenius-semisimple Weil-Deligne representations of $W_K$ of dimension $n$ over $\mathbb{C}$ (Chapter 3). Both sides have L-factors and $\varepsilon$-factors. For $\pi \in \mathrm{Irr}_n(K)$ and $\pi' \in \mathrm{Irr}_{n'}(K)$ the factors $L(\pi \times \pi', s)$ and $\varepsilon(\pi \times \pi', s, \psi)$ are those of Jacquet, Piatetski-Shapiro and Shalika, and on the Galois side they are those of Langlands and Deligne [Tat79]. Here $\psi$ is a nontrivial continuous character of $K$.

**Theorem 2.3.1 (local Langlands correspondence for $GL_n$).** There is a unique family of bijections $\mathrm{rec}_n : \mathrm{Irr}_n(K) \to \Phi_n(K)$, for $n \ge 1$, with the following properties.
1. The map $\mathrm{rec}_1$ sends a character $\chi$ of $K^\times$ to $\chi \circ \mathrm{rec}_K^{-1}$, where $\mathrm{rec}_K$ is the reciprocity map of the first section.
2. For $\pi \in \mathrm{Irr}_n(K)$ and $\pi' \in \mathrm{Irr}_{n'}(K)$, $L(\pi \times \pi', s) = L(\mathrm{rec}_n(\pi) \otimes \mathrm{rec}_{n'}(\pi'), s)$, and $\varepsilon(\pi \times \pi', s, \psi) = \varepsilon(\mathrm{rec}_n(\pi) \otimes \mathrm{rec}_{n'}(\pi'), s, \psi)$ for each $\psi$.
3. The determinant of $\mathrm{rec}_n(\pi)$ is $\mathrm{rec}_1(\omega_\pi)$, where $\omega_\pi$ is the central character of $\pi$.
4. For a character $\chi$ of $K^\times$, $\mathrm{rec}_n(\pi \otimes (\chi \circ \det)) = \mathrm{rec}_n(\pi) \otimes \mathrm{rec}_1(\chi)$.
5. The map $\mathrm{rec}_n$ sends the contragredient of $\pi$ to the dual of $\mathrm{rec}_n(\pi)$.

Lean: not stated yet, planned for milestone S3

Laumon, Rapoport and Stuhler proved the theorem when $K$ has characteristic $p$ (1993). Harris and Taylor (2001) and Henniart (2000) proved it when $K$ has characteristic 0. Scholze gave a new proof in 2013. Henniart proved that the properties determine the family, so that the different constructions give the same bijections. Kutzko proved the case $n = 2$ in 1980. Under $\mathrm{rec}_n$ the supercuspidal representations correspond to the irreducible Weil-Deligne representations. Such a representation has $N = 0$, so it is an irreducible representation of $W_K$. Volume 6 proves the case $n = 2$, and Volume 10 explains the proof for general $n$.

For a connected reductive group $G$ over $K$ other than $GL_n$, the correspondence is a conjecture. It predicts a map with finite fibres, the L-packets, from the irreducible smooth representations of $G(K)$ to the L-parameters of $G$, with a list of properties. It is a theorem for many groups, such as the quasi-split classical groups (Arthur, Mok), $GSp_4$ and $G_2$, and for some classes of supercuspidal representations (Kaletha). Fargues and Scholze constructed the semisimple part of an L-parameter for each irreducible smooth representation of each $G$. The full correspondence for general $G$ is open.

### Reciprocity for GL(n) over a number field

Let $F$ be a number field, $\ell$ a prime and $\iota : \bar{\mathbb{Q}}_\ell \to \mathbb{C}$ an isomorphism of fields. A cuspidal automorphic representation $\pi$ of $GL_n(\mathbb{A}_F)$ is *algebraic* if its components at the infinite places satisfy the integrality condition of Clozel. An $\ell$-adic representation of $G_F$ is *geometric* if it is unramified outside a finite set of places and de Rham at the places over $\ell$, in the sense of Fontaine and Mazur.

**Conjecture 2.3.2 (reciprocity for $GL_n$).** The cuspidal algebraic automorphic representations $\pi$ of $GL_n(\mathbb{A}_F)$ correspond to the irreducible geometric representations $\rho : G_F \to GL_n(\bar{\mathbb{Q}}_\ell)$. The correspondence is compatible with the local correspondence at each finite place $v$ that does not divide $\ell$: through $\iota$, the Frobenius semisimplification of the Weil-Deligne representation of $\rho$ at $v$ corresponds to $\pi_v$ by $\mathrm{rec}_n$, after a twist by a power of $|\det|$ that the normalization fixes.

Lean: not stated yet

The conjecture is open. For $n = 1$ it is class field theory with the algebraic Hecke characters. For $n = 2$ and $F = \mathbb{Q}$ much is known: the modularity of elliptic curves, the theorem of Khare and Wintenberger on the conjecture of Serre, and the modularity of many geometric representations of dimension 2. For a regular algebraic $\pi$ over a totally real or a CM field, there is a representation $\rho$ with the right Frobenius eigenvalues at almost all places, by Harris, Lan, Taylor and Thorne (2016) and by Scholze (2015). The converse direction for $n \ge 3$, and the case of algebraic $\pi$ that are not regular, are open in general. Even for $GL_2$ over $\mathbb{Q}$, the Maass forms with Laplace eigenvalue $1/4$ are algebraic and not regular, and the conjecture is open for them.

A related conjecture of Ramanujan type says that each local component of a cuspidal automorphic representation of $GL_n(\mathbb{A}_F)$ is tempered. It is open, even for the Maass forms on $GL_2$ over $\mathbb{Q}$. The best known bound for $GL_2$ over $\mathbb{Q}$ is the exponent $7/64$ of Kim and Sarnak.

### Functoriality

Let $G$ and $H$ be connected reductive groups over a number field $F$, with $H$ quasi-split, and let ${}^L G$ and ${}^L H$ be their L-groups (Volume 2). An L-homomorphism $u : {}^L G \to {}^L H$ is a homomorphism of the L-groups that respects their maps to the Weil group of $F$.

**Conjecture 2.3.3 (functoriality).** For each automorphic representation $\pi$ of $G(\mathbb{A}_F)$ there is an automorphic representation $\Pi$ of $H(\mathbb{A}_F)$ such that, for almost all places $v$ where $\pi_v$ and $\Pi_v$ are unramified, the Satake parameter of $\Pi_v$ is the image under $u$ of the Satake parameter of $\pi_v$.

Lean: not stated yet

Langlands stated the conjecture in 1970. It is open in general. The table lists some known cases. Volumes 7, 8 and 9 prove or explain them.

| Case | Author and year |
|---|---|
| Jacquet-Langlands correspondence, from an inner form of $GL_2$ to $GL_2$ | Jacquet and Langlands, 1970 |
| $\mathrm{Sym}^2$, from $GL_2$ to $GL_3$ | Gelbart and Jacquet, 1978 |
| cyclic base change for $GL_n$ | Arthur and Clozel, 1989 |
| $GL_2 \times GL_2 \to GL_4$ | Ramakrishnan, 2000 |
| $GL_2 \times GL_3 \to GL_6$ and $\mathrm{Sym}^3$ | Kim and Shahidi, 2002 |
| $\wedge^2$, from $GL_4$ to $GL_6$, and $\mathrm{Sym}^4$ | Kim, 2003 |
| $\mathrm{Sym}^n$ for holomorphic newforms of weight at least 2, all $n$ | Newton and Thorne, 2021 |
| from quasi-split classical groups to $GL_N$ | Arthur, 2013 |

The result of Arthur is part of his endoscopic classification. It rests on the stabilization of the twisted trace formula. Volume 9 gives the status of each input of its proof.

### The geometric program

Let $X$ be a smooth projective curve over a finite field, and let $F$ be its field of rational functions. Drinfeld proved the global correspondence for $GL_2$ over $F$. L. Lafforgue proved it for $GL_n$ over $F$, in both directions (2002). V. Lafforgue constructed the Galois parameters of the cuspidal automorphic forms for each reductive group over $F$ (2018). These results use moduli spaces of shtukas, which have no analogue over number fields.

The geometric Langlands conjecture replaces the functions on the automorphic side by sheaves on the moduli stack $\mathrm{Bun}_G$ of $G$-bundles on a curve $X$ over a field of characteristic 0. It predicts an equivalence between a category of D-modules on $\mathrm{Bun}_G$ and a category of coherent sheaves on the stack of local systems for the dual group. Gaitsgory, Raskin and their coauthors proved the unramified form of the conjecture in five papers, the first of which is arXiv:2405.03599. The papers have no journal reference yet. The ramified forms are open. Volume 13 states these results and lists the open problems.

### What is proved and what is open

| Statement | Status in the literature | Volume |
|---|---|---|
| local and global class field theory | theorem | 3 |
| modularity of elliptic curves over $\mathbb{Q}$ | theorem | 4, 11 |
| Ramanujan-Petersson for holomorphic forms | theorem | 4, 10 |
| Sato-Tate for elliptic curves over $\mathbb{Q}$ | theorem | 11 |
| local Langlands for $GL_n$ | theorem | 6, 10 |
| local Langlands for general $G$ | open in general | 6, 12 |
| reciprocity for $GL_n$ over number fields | open in general | 10, 11 |
| Ramanujan for $GL_n$ | open | 7 |
| functoriality | open in general | 7, 8, 9 |
| global Langlands for $GL_n$ over function fields | theorem | 13 |
| unramified geometric Langlands in characteristic 0 | proved in five papers without a journal reference | 13 |

The column on the status in the literature is not the Lean status. The Lean status of each node is on the line under its statement.
