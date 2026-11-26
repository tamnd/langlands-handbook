---
title: Weil-Deligne representations
nodes: []
sources: [Tat79, BH06]
status: checked
drafted_by: writer@claude-opus-5-5
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## Weil-Deligne representations

A Weil-Deligne representation is a representation of $W_K$ together with a nilpotent endomorphism $N$ that Frobenius scales by $q^{-1}$. This section defines these objects, constructs the basic examples $\mathrm{Sp}(n)$, and classifies the Frobenius-semisimple ones: each is a direct sum of representations $\mathrm{Sp}(n) \otimes \rho$ with $\rho$ irreducible. The classification has the same shape as the Langlands classification of Theorem 1.6.5, with $\mathrm{Sp}(n) \otimes \rho$ in the role of a segment. The example to keep in mind is $\mathrm{Sp}(2)$, the Weil-Deligne representation of the Tate module of a Tate curve. It corresponds to a twist of the Steinberg representation. The definitions follow [Tat79, Section 4] and Deligne's paper "Les constantes des équations fonctionnelles des fonctions L" (1973), Section 8.

### The definition

**Definition 2.2.1 (Weil-Deligne representation).** A *Weil-Deligne representation* of $W_K$ is a pair $(r, N)$, where $r : W_K \to GL(V)$ is a representation of $W_K$ on a complex vector space $V$ of finite dimension (Definition 2.1.9), and $N \in \mathrm{End}(V)$ is an endomorphism with
$$r(w) \, N \, r(w)^{-1} = \|w\| \, N \quad \text{for all } w \in W_K.$$
A *morphism* $(r, N) \to (r', N')$ is a linear map $f : V \to V'$ with $f \circ r(w) = r'(w) \circ f$ for all $w$ and $f \circ N = N' \circ f$. A *subrepresentation* is a subspace stable under $r(W_K)$ and $N$.

Lean: `Langlands.WeilDeligneRep` (on $\mathbb{C}^m$, and with Frobenius-semisimplicity built in, Definition 2.2.5)

Since $\|w\| = 1$ for $w \in I_K$, the relation says that $N$ commutes with $r(I_K)$. For $w = \Phi$ it says $r(\Phi) N r(\Phi)^{-1} = q^{-1} N$. Many authors write the relation with the arithmetic Frobenius, and then the factor is $q$. Our convention is that of [Tat79, Section 4] and of the table of Volume 0, Section 3.1. The Lean structure `Langlands.WeilDeligneRep` asks for the relation in the form $r(w) N r(w)^{-1} = \|w\| N$, as here, with `Langlands.weilNorm` for the norm. It also asks that $N$ be nilpotent. The next lemma shows that this is automatic.

**Lemma 2.2.2 ($N$ is nilpotent).** Let $(r, N)$ be a Weil-Deligne representation on $V$. For $\lambda \in \mathbb{C}^\times$, let $V_\lambda$ be the generalized eigenspace of $r(\Phi)$ for $\lambda$. Then $N V_\lambda \subseteq V_{q^{-1} \lambda}$. In particular $N$ is nilpotent, and $N^{n} = 0$ for $n = \dim V$.

Lean: not stated yet (the structure has the field `isNilpotent`)

*Proof.* The relation gives $r(\Phi) N = q^{-1} N r(\Phi)$, so $(r(\Phi) - q^{-1}\lambda)^k N = q^{-k} N (r(\Phi) - \lambda)^k$ for all $k \ge 0$. If $v \in V_\lambda$, then $(r(\Phi) - \lambda)^k v = 0$ for large $k$, so $Nv \in V_{q^{-1}\lambda}$. The operator $r(\Phi)$ has at most $n$ eigenvalues. Since $q > 1$, the $n + 1$ numbers $\lambda, q^{-1}\lambda, \dots, q^{-n}\lambda$ are distinct, so one of them, say $q^{-j}\lambda$, is not an eigenvalue. Then $V_{q^{-j}\lambda} = 0$, and $N^n V_\lambda \subseteq N^{n-j} V_{q^{-j}\lambda} = 0$ for each $\lambda$. $\square$

**Definition 2.2.3 (operations).** Let $(r, N)$ and $(r', N')$ be Weil-Deligne representations on $V$ and $V'$.
1. The *direct sum* is $(r \oplus r', N \oplus N')$ on $V \oplus V'$.
2. The *tensor product* is $(r \otimes r', N \otimes 1 + 1 \otimes N')$ on $V \otimes V'$.
3. The *dual* is $(r^\vee, N^\vee)$ on $V^\vee$, with $r^\vee(w) = {}^t r(w)^{-1}$ and $N^\vee = - {}^t N$.
4. The *twist* by a character $\chi$ of $W_K$ is $(\chi r, N)$. We write it $(r, N) \otimes \chi$.
5. The *determinant* is the character $\det r$ of $W_K$.

Lean: `Langlands.WDIso.IsDual`, `Langlands.WDIso.IsTwist`, `Langlands.WeilDeligneRep.det`

One checks the relation in each case. For the dual, ${}^t r(w)^{-1} \, {}^t N \, {}^t r(w) = {}^t (r(w) N r(w)^{-1}) = \|w\| \, {}^t N$. The minus sign in $N^\vee$ makes the natural pairing $V \otimes V^\vee \to \mathbb{C}$ a morphism to the trivial Weil-Deligne representation $(1, 0)$: for $v \in V$ and $\lambda \in V^\vee$ one has $\lambda(Nv) + (N^\vee \lambda)(v) = 0$. The determinant does not see $N$. It is an invariant of the isomorphism class (`Langlands.WeilDeligneRep.det_eq_of_iso`).

**Example 2.2.4 (the special representations).** Let $n \ge 1$. The Weil-Deligne representation $\mathrm{Sp}(n)$ has the basis $e_0, \dots, e_{n-1}$ and
$$r(w) e_i = \|w\|^i e_i, \qquad N e_i = e_{i+1} \ (0 \le i < n - 1), \qquad N e_{n-1} = 0.$$
The relation holds: $r(w) N r(w)^{-1} e_i = \|w\|^{-i} \|w\|^{i+1} e_{i+1} = \|w\| N e_i$. The representation $r$ is unramified, and $r(\Phi)$ has the eigenvalues $1, q^{-1}, \dots, q^{1-n}$. The subrepresentations are the spaces $V_j = \mathrm{span}(e_j, \dots, e_{n-1})$ for $0 \le j \le n$: a subspace stable under $r(\Phi)$ is a sum of eigenlines, since the eigenvalues are distinct, and a sum of eigenlines stable under $N$ is one of the $V_j$. So $\mathrm{Sp}(n)$ is indecomposable, and it is not irreducible for $n \ge 2$. Its unique irreducible subrepresentation is $\ker N = \mathbb{C} e_{n-1} \cong \|\cdot\|^{n-1}$, and its unique irreducible quotient is $\mathbb{C} e_0 \cong 1$. For a representation $\rho$ of $W_K$ we write $\mathrm{Sp}(n) \otimes \rho$ for the tensor product of $\mathrm{Sp}(n)$ with $(\rho, 0)$. It is $\rho \oplus \rho \|\cdot\| \oplus \dots \oplus \rho \|\cdot\|^{n-1}$, with $N$ mapping each summand isomorphically to the next one. Exercise 3 computes the dual of $\mathrm{Sp}(n)$ and the tensor product $\mathrm{Sp}(n) \otimes \mathrm{Sp}(m)$.

### Frobenius-semisimplicity

**Definition 2.2.5 (Frobenius-semisimple).** A Weil-Deligne representation $(r, N)$ is *Frobenius-semisimple* if $r$ is semisimple. By Proposition 2.1.11 this holds if and only if $r(\Phi)$ is a semisimple endomorphism, and if and only if each $r(w)$ is semisimple.

Lean: `Langlands.WeilDeligneRep` (the field `semisimple`)

The representation $r$ of $\mathrm{Sp}(n) \otimes \rho$ is semisimple when $\rho$ is. The condition does not ask anything of $N$, which is nilpotent and is never semisimple unless it is $0$. The Lean library works only with Frobenius-semisimple representations, and `Langlands.WDIso` is the set of their isomorphism classes. The next proposition explains why one loses little in doing so.

**Proposition 2.2.6 (Frobenius-semisimplification).** Let $(r, N)$ be a Weil-Deligne representation on $V$, and let $r(\Phi) = su$ be the Jordan decomposition, with $s$ semisimple, $u$ unipotent and $su = us$.
1. The unipotent part $u$ commutes with $r(w)$ for every $w \in W_K$, and with $N$.
2. The map $r^{ss}(w) = r(w) \, u^{d(w)}$ is a semisimple representation of $W_K$, and $(r^{ss}, N)$ is a Frobenius-semisimple Weil-Deligne representation with $r^{ss}(\Phi) = s$.
3. The pair $(r^{ss}, N)$ does not depend on the choice of the geometric Frobenius $\Phi$, and an isomorphism $(r, N) \cong (r', N')$ is also an isomorphism $(r^{ss}, N) \cong (r'^{ss}, N')$.

Lean: not stated yet

*Proof.* Let $m$ be as in Proposition 2.1.11, so that $A = r(\Phi)^m$ commutes with $r(W_K)$. The Jordan decomposition of $A$ is $s^m u^m$, and its unipotent part $u^m$ is a polynomial in $A$. So $u^m$ commutes with $r(W_K)$, and so does $u = \exp(\frac{1}{m} \log u^m)$, because $\log u^m$ is a polynomial in $u^m - 1$. Next, consider the operator $\mathrm{Ad}(g) X = g X g^{-1}$ on $\mathrm{End}(V)$. The Jordan decomposition of $\mathrm{Ad}(r(\Phi))$ is $\mathrm{Ad}(s) \mathrm{Ad}(u)$, since $\mathrm{Ad}(s)$ is semisimple, $\mathrm{Ad}(u)$ is unipotent and they commute. The element $N$ is an eigenvector of $\mathrm{Ad}(r(\Phi))$ for the eigenvalue $q^{-1}$. The semisimple part acts on the generalized eigenspace for $q^{-1}$ as the scalar $q^{-1}$, so $\mathrm{Ad}(s) N = q^{-1} N$, and $\mathrm{Ad}(u) N = q \, \mathrm{Ad}(r(\Phi)) N = N$. This proves part 1. For part 2, part 1 gives $r^{ss}(w w') = r(w) r(w') u^{d(w) + d(w')} = r(w) u^{d(w)} r(w') u^{d(w')}$, so $r^{ss}$ is a homomorphism. It agrees with $r$ on $I_K$, so its kernel contains an open subgroup of $I_K$, and $r^{ss}$ is continuous by Proposition 2.1.10. The relation for $N$ holds, since $u$ commutes with $N$. Finally $r^{ss}(\Phi) = r(\Phi) u^{-1} = s$ is semisimple, and $r^{ss}$ is semisimple by Proposition 2.1.11. For part 3, let $\Phi' = \Phi \sigma_0$ with $\sigma_0 \in I_K$, and let $u'$ be the unipotent part of $r(\Phi')$. Then $\Phi'^m = \Phi^m \sigma_1$ for some $\sigma_1 \in I_K$. Since $A$ commutes with $r(\sigma_1)$, and $r(\sigma_1)^e = 1$ for $e = |r(I_K)|$, we get $r(\Phi')^{me} = A^e$. So $u'^{me} = u^{me}$, and $u' = u$, since a unipotent element is determined by its logarithm. The last claim holds because an isomorphism $f$ satisfies $f r(\Phi) f^{-1} = r'(\Phi)$, so it carries the Jordan decomposition of $r(\Phi)$ to that of $r'(\Phi)$. $\square$

**Example 2.2.7 (a representation that is not Frobenius-semisimple).** Let $r$ be the unramified representation of $W_K$ on $\mathbb{C}^2$ with $r(\Phi) = \left(\begin{smallmatrix} 1 & 1 \\ 0 & 1 \end{smallmatrix}\right)$, and let $N = 0$. Then $s = 1$, and $r^{ss}$ is the trivial representation of dimension $2$. The pair $(r, 0)$ has the same Frobenius-semisimplification as $(1 \oplus 1, 0)$, but it is not isomorphic to it. Note that $(r, N)$ with $N \ne 0$ is impossible here: by Lemma 2.2.2, $N$ would map the eigenspace for $1$ into the eigenspace for $q^{-1}$, which is $0$. It is conjectured that the representations that come from the cohomology of varieties over $K$ are Frobenius-semisimple.

### The classification

For an irreducible representation $\rho$ of $W_K$ and $k \in \mathbb{Z}$, the representations $\rho \|\cdot\|^k$ are pairwise nonisomorphic. Indeed $\det(\rho \|\cdot\|^k) = \det(\rho) \|\cdot\|^{k \dim \rho}$, and $\|\cdot\|^{j}$ is a nontrivial character for $j \ne 0$, since $\|\Phi\|^{j} = q^{-j}$. We call the set $\{\rho \|\cdot\|^k : k \in \mathbb{Z}\}$ the *line* of $\rho$. It is the analogue for $W_K$ of the set $\{\rho \nu^k\}$ in which the segments of Section 1.6 live.

**Theorem 2.2.8 (classification of Frobenius-semisimple representations).** Let $(r, N)$ be a Frobenius-semisimple Weil-Deligne representation. There are integers $n_1, \dots, n_t \ge 1$ and irreducible representations $\rho_1, \dots, \rho_t$ of $W_K$ with
$$(r, N) \cong \bigoplus_{i=1}^t \mathrm{Sp}(n_i) \otimes \rho_i.$$
The multiset of the pairs $(n_i, \rho_i)$, with $\rho_i$ up to isomorphism, is uniquely determined. Each $\mathrm{Sp}(n) \otimes \rho$ with $\rho$ irreducible is indecomposable, and its endomorphisms are the scalars.

Lean: not stated yet

*Proof.* Since $r$ is semisimple, $V$ is the direct sum of its isotypic components $V[\rho]$. For $f \in \mathrm{Hom}_{W_K}(\rho, V)$ and $x$ in the space of $\rho$ we have
$$r(w) N f(x) = \|w\| \, N r(w) f(x) = N f\big(\|w\| \rho(w) x\big).$$
So $N \circ f$ lies in $\mathrm{Hom}_{W_K}(\rho \|\cdot\|, V)$, and $N$ maps $V[\rho]$ into $V[\rho \|\cdot\|]$. Hence $V$ is the direct sum of the subrepresentations $V_{L} = \bigoplus_{\rho \in L} V[\rho]$, where $L$ runs over the lines. It suffices to treat one line. Fix $\rho$ and set $M_k = \mathrm{Hom}_{W_K}(\rho \|\cdot\|^k, V)$, which is $0$ for all but finitely many $k$. The maps $x_k : M_k \to M_{k+1}$, $f \mapsto N \circ f$, make $M = \bigoplus_k M_k$ a graded module of finite dimension over $\mathbb{C}[x]$, with $x$ of degree $1$. The evaluation map gives an isomorphism
$$\bigoplus_k \rho \|\cdot\|^k \otimes M_k \to V_L$$
of Weil-Deligne representations, where $N$ acts on the left side by $1 \otimes x$. This construction is an equivalence between Frobenius-semisimple Weil-Deligne representations supported on the line of $\rho$ and graded $\mathbb{C}[x]$-modules of finite dimension, by Schur's lemma and the fact that the $\rho \|\cdot\|^k$ are pairwise nonisomorphic. Under this equivalence $\mathrm{Sp}(n) \otimes \rho \|\cdot\|^a$ corresponds to the cyclic module $C(a, n) = \mathbb{C}[x] / (x^n)$, with its generator in degree $a$.

We show that $M$ is a direct sum of modules $C(a, n)$. We may assume $M \ne 0$. Let $n$ be the largest integer with $x^{n-1} M \ne 0$, and choose a homogeneous $v$ of degree $a$ with $x^{n-1} v \ne 0$. Then $\mathbb{C}[x] v \cong C(a, n)$. Choose a linear form $\lambda$ on $M$ that vanishes on $M_k$ for $k \ne a + n - 1$ and satisfies $\lambda(x^{n-1} v) = 1$. Define
$$\pi(m) = \sum_{j=0}^{n-1} \lambda(x^{n-1-j} m) \, x^j v.$$
Since $x^n M = 0$, a direct computation gives $\pi(xm) = x \pi(m)$. The map $\pi$ preserves the grading, by the choice of $\lambda$, and $\pi(v) = v$, since $\lambda(x^{n-1-j} v) = 0$ for $j \ne 0$. So $\pi$ is a graded projection of $M$ onto $\mathbb{C}[x] v$, and $M = \mathbb{C}[x] v \oplus \ker \pi$. Induction on the dimension gives the decomposition. A graded endomorphism of $C(a, n)$ maps the generator to a homogeneous element of degree $a$, that is, to a multiple of the generator, so its endomorphism ring is $\mathbb{C}$. This gives the last claim of the theorem. The uniqueness follows from the Krull-Schmidt theorem, since the summands have local endomorphism rings. One can also count directly. Let $r_{a,j}$ be the rank of $x^j : M_a \to M_{a+j}$. A summand $C(b, m)$ contributes $1$ to $r_{a,j}$ if $b \le a$ and $a + j \le b + m - 1$, and $0$ otherwise. So the number of summands $C(a, n)$ of $M$ is
$$r_{a, n-1} - r_{a, n} - r_{a-1, n} + r_{a-1, n+1},$$
which depends only on $M$. $\square$

The proof is the classification of the representations of a quiver of type $A$, and it is parallel to the Zelevinsky classification in Section 1.6. For dimension $2$ the classification is in [BH06, Chapter 7].

**Corollary 2.2.9 (irreducible and indecomposable representations).** Let $(r, N)$ be a Weil-Deligne representation.
1. It is irreducible if and only if $N = 0$ and $r$ is irreducible. In particular an irreducible Weil-Deligne representation is Frobenius-semisimple.
2. If it is Frobenius-semisimple, it is indecomposable if and only if it is isomorphic to $\mathrm{Sp}(n) \otimes \rho$ for some $n \ge 1$ and some irreducible $\rho$.

Lean: not stated yet (the predicate is `Langlands.WeilDeligneRep.IsIrreducible`)

*Proof.* The kernel of $N$ is stable under $r(W_K)$, by the relation, and under $N$. It is nonzero by Lemma 2.2.2. So if $(r, N)$ is irreducible, then $\ker N = V$ and $N = 0$, and then $r$ is irreducible. The converse is clear. Part 2 follows from Theorem 2.2.8. $\square$

**Remark 2.2.10 (Weil-Deligne representations and $L$-parameters).** Volume 2, Proposition 5.6.3 gives a second description. A Frobenius-semisimple Weil-Deligne representation of dimension $n$ is the same thing, up to isomorphism, as an $L$-parameter $\varphi : W_K \times SL_2(\mathbb{C}) \to GL_n(\mathbb{C})$, that is, a continuous homomorphism that is semisimple on $W_K$ and algebraic on $SL_2(\mathbb{C})$. The dictionary is
$$r(w) = \varphi\big(w, \mathrm{diag}(\|w\|^{1/2}, \|w\|^{-1/2})\big), \qquad N = d\varphi \begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix}.$$
Under it, $\mathrm{Sp}(n)$ corresponds to $\|\cdot\|^{(n-1)/2} \boxtimes \mathrm{Sym}^{n-1}$, where $\mathrm{Sym}^{n-1}$ is the irreducible algebraic representation of $SL_2(\mathbb{C})$ of dimension $n$. Indeed $\mathrm{Sym}^{n-1}$ of $\mathrm{diag}(t^{1/2}, t^{-1/2})$ has the eigenvalues $t^{(n-1)/2 - i}$ for $0 \le i \le n - 1$. The form with $SL_2(\mathbb{C})$ extends to other groups, and the Weil-Deligne form is the one that comes from Galois representations in Section 2.3.

**Example 2.2.11 (dimension two).** By Theorem 2.2.8 a Frobenius-semisimple Weil-Deligne representation of dimension $2$ is of one of three kinds.
1. $(\chi_1 \oplus \chi_2, 0)$ for two characters $\chi_1, \chi_2$ of $K^\times$.
2. $\mathrm{Sp}(2) \otimes \chi$ for a character $\chi$. Here $r = \chi \oplus \chi \|\cdot\|$ and $N$ maps the line of $\chi$ to the line of $\chi \|\cdot\|$.
3. $(\rho, 0)$ for an irreducible $\rho$ of dimension $2$.

The local Langlands correspondence of Chapter 3 matches these with the list of Theorem 1.5.5. In the first case the representation corresponds to $\chi_1 \times \chi_2$ if $\chi_1 \chi_2^{-1} \ne |\cdot|^{\pm 1}$. If $\chi_1 = \eta |\cdot|^{1/2}$ and $\chi_2 = \eta |\cdot|^{-1/2}$, it corresponds to the character $\eta \circ \det$. The second case gives the twists of the Steinberg representation: $\mathrm{Sp}(2) \otimes \eta |\cdot|^{-1/2}$ corresponds to $\eta \mathrm{St}$. The third case gives the supercuspidal representations. So the reducible principal series $\eta|\cdot|^{1/2} \times \eta|\cdot|^{-1/2}$ has two irreducible subquotients, and they have the same $r$. The operator $N$ distinguishes them. This is the main reason for its presence. Section 2.4 checks that the two sides have the same $L$-factors, and Section 2.5 computes the factors on the side of $GL_2(K)$.
