---
title: The theorem of Kronecker and Weber
nodes: [LG06WS8A1Y]
sources: [CF67, Mil20, Neu99]
status: checked
drafted_by: writer
checked_by: checker@claude-opus-5-5
reviewed_by: []
---
## The theorem of Kronecker and Weber

Over $\mathbb{Q}$ everything in the theory is explicit. The idele class group is $\mathbb{R}_{>0} \times \hat{\mathbb{Z}}^\times$, the class fields are the cyclotomic fields and their subfields, and the global norm residue map is the cyclotomic character. This section works out these facts. It proves the Kronecker-Weber theorem in two ways: from class field theory, and by the local route that the Lean port follows.

### Explicit reciprocity over the rationals

**Proposition 7.5.1 (explicit reciprocity for $\mathbb{Q}$).** Identify $C_\mathbb{Q}$ with $\mathbb{R}_{>0} \times \hat{\mathbb{Z}}^\times$ as in Volume 1, Example 3.4.8. For $(t, u) \in \mathbb{R}_{>0} \times \hat{\mathbb{Z}}^\times$ and a root of unity $\zeta$,
$$\mathrm{art}_\mathbb{Q}(t, u)(\zeta) = \zeta^u.$$
For a prime $p \nmid N$, the class of the idele $\varpi_p = p$ at $p$ is the class of $(p^{-1}, u_p)$, where $u_p \in \hat{\mathbb{Z}}^\times$ has component $p^{-1}$ at each prime $\ell \ne p$ and $1$ at $p$. It acts on $\mathbb{Q}(\zeta_N)$ as $\zeta \mapsto \zeta^{p^{-1}}$, which is $\mathrm{Frob}_p^{-1}$.

Lean: not stated yet

*Proof.* The first formula was shown after Proposition 7.2.6. For the second, the idele with $p$ at $p$ and $1$ elsewhere equals $p \cdot x$ in $J_\mathbb{Q}$, where $p \in \mathbb{Q}^\times$ is principal and $x$ has component $1$ at $p$, $p^{-1}$ at every other finite prime, and $p^{-1}$ at $\infty$. The class of $x$ in $\mathbb{R}_{>0} \times \hat{\mathbb{Z}}^\times$ is $(p^{-1}, u_p)$. Its image acts on $\mu_N$ as $\zeta \mapsto \zeta^{p^{-1}}$, since $p \nmid N$. The Frobenius of $p$ is $\zeta \mapsto \zeta^p$ (Volume 1, Theorem 1.5.5). $\square$

The port has this computation at each finite level, in the files `RationalRayClassFieldCyclotomic` and `RationalCyclotomicArithmeticReciprocity` of its `KroneckerWeber` folder. There the arithmetic Frobenius at $q \nmid m$ acts on the cyclotomic field of level $m$ by $\zeta \mapsto \zeta^q$, as it should.

**Proposition 7.5.2 (the cyclotomic class fields of $\mathbb{Q}$).** Let $N \ge 1$.
1. The norm group of $\mathbb{Q}(\zeta_N)$ in $C_\mathbb{Q}$ is the image of $\mathbb{R}_{>0} \times \prod_p (1 + N\mathbb{Z}_p)^\times$, where $(1 + N\mathbb{Z}_p)^\times = \mathbb{Z}_p^\times$ for $p \nmid N$. Thus $\mathbb{Q}(\zeta_N)$ is the ray class field of $\mathbb{Q}$ of modulus $N\infty$, and $\mathrm{Gal}(\mathbb{Q}(\zeta_N)/\mathbb{Q}) \cong \mathrm{Cl}_{N\infty} \cong (\mathbb{Z}/N\mathbb{Z})^\times$.
2. The ray class field of modulus $N$ is the maximal real subfield $\mathbb{Q}(\zeta_N)^+ = \mathbb{Q}(\zeta_N + \zeta_N^{-1})$.
3. The Hilbert class field of $\mathbb{Q}$ is $\mathbb{Q}$.

Lean: not stated yet

*Proof.* By Proposition 7.5.1 the kernel of $\mathrm{art}_\mathbb{Q}$ on $\mathbb{Q}(\zeta_N)$ is the set of $(t, u)$ with $u \equiv 1 \bmod N$. This is the group of part 1, and its quotient is $\mathrm{Cl}_{N\infty}$ by Example 7.1.5. For part 2, the ray class group of modulus $N$ is the quotient of $\mathrm{Cl}_{N\infty}$ by the image of $\mathbb{R}^\times$, that is by the class of $-1$. Under $\mathrm{art}_\mathbb{Q}$, the class of $-1 \in \mathbb{R}^\times$ is complex conjugation, so its fixed field is $\mathbb{Q}(\zeta_N)^+$. Part 3 is the case $N = 1$ of part 2, or Volume 1, Corollary 1.3.6. $\square$

This explains the motivating example of Volume 1, Chapter 1. A prime $p \nmid N$ splits completely in $\mathbb{Q}(\zeta_N)$ if and only if $p \equiv 1 \bmod N$, and the ray class of $p$ is its residue class.

### The theorem

**Theorem 7.5.3 (Kronecker-Weber).** Every finite abelian extension of $\mathbb{Q}$ is contained in a cyclotomic field $\mathbb{Q}(\zeta_n)$. Equivalently, $\mathbb{Q}^{ab} = \mathbb{Q}(\mu_\infty)$.

Node: LG06WS8A1Y · Lean: `Langlands.KroneckerWeber`

The Lean statement says: for each intermediate field $L$ of an algebraic closure of $\mathbb{Q}$, finite and abelian over $\mathbb{Q}$, there are $n > 0$ and a primitive $n$-th root of unity $\zeta$ in the same algebraic closure with $L \subset \mathbb{Q}(\zeta)$. This is the textbook statement. The theorem `Langlands.Bridge.kroneckerWeber` proves it from the theorem `ClassFieldTheory.kroneckerWeber` of the port. The port gives an embedding of $L$ into the concrete model `CyclotomicField n ℚ` of $\mathbb{Q}(\zeta_n)$. The bridge moves the image into the algebraic closure, and uses that $L/\mathbb{Q}$ is normal to see that the image is $L$ itself.

*First proof, from class field theory.* Let $L/\mathbb{Q}$ be finite abelian. Its norm group $U = N_{L/\mathbb{Q}}(C_L)$ is open of finite index. By Proposition 7.1.3 it contains the image of $\mathbb{R}_{>0} \times \prod_p (1 + N\mathbb{Z}_p)^\times$ for some $N$. By Proposition 7.5.2 this is the norm group of $\mathbb{Q}(\zeta_N)$. By Corollary 7.4.4, $L \subset \mathbb{Q}(\zeta_N)$. $\square$

This proof is short, but it uses all of global class field theory. Historically the theorem came first, with the proofs of Weber and Hilbert. The second proof, due to Hilbert in its global part, uses only local class field theory and the theorem of Minkowski. It is the proof of the port.

*Second proof, by the local route.* Let $L/\mathbb{Q}$ be finite abelian with group $G$. Let $S$ be the set of primes that ramify in $L$.

Step 1 (local Kronecker-Weber). For $p \in S$, let $L_p$ be the completion of $L$ at a prime above $p$. It is abelian over $\mathbb{Q}_p$. By local class field theory, $\mathbb{Q}_p^{ab} = \mathbb{Q}_p(\mu_{p^\infty}) \cdot \mathbb{Q}_p^{ur}$ (Theorem 3.5.4 and Example 3.5.6). So $L_p \subset \mathbb{Q}_p(\zeta_{p^{e_p}}) \cdot \mathbb{Q}_p^{ur}$ for some $e_p \ge 0$. The port proves this as `KroneckerWeber.exists_localCyclotomicEmbedding`.

Step 2 (the inertia bound). Let $n = \prod_{p \in S} p^{e_p}$ and $M = L(\zeta_n)$. It is abelian over $\mathbb{Q}$ and ramified only at the primes of $S$. For $p \in S$, the completion $M_p$ is contained in $\mathbb{Q}_p(\zeta_{p^{e_p}}) \cdot \mathbb{Q}_p^{ur}$. So the inertia group $I_p(M) \subset \mathrm{Gal}(M/\mathbb{Q})$ is a quotient of the inertia group of $\mathbb{Q}_p(\zeta_{p^{e_p}})\mathbb{Q}_p^{ur} / \mathbb{Q}_p$, which is $(\mathbb{Z}/p^{e_p}\mathbb{Z})^\times$. Hence $|I_p(M)| \le \varphi(p^{e_p})$.

Step 3 (Minkowski). Let $I \subset \mathrm{Gal}(M/\mathbb{Q})$ be the subgroup generated by the $I_p(M)$ for $p \in S$. The fixed field $M^I$ is unramified over $\mathbb{Q}$ at every prime. By Volume 1, Corollary 1.3.6 and Theorem 1.4.3, every number field other than $\mathbb{Q}$ has a ramified prime. So $M^I = \mathbb{Q}$ and $I = \mathrm{Gal}(M/\mathbb{Q})$. Since the group is abelian,
$$[M : \mathbb{Q}] = |I| \le \prod_{p \in S} |I_p(M)| \le \prod_{p \in S} \varphi(p^{e_p}) = \varphi(n).$$
The port proves this bound as `KroneckerWeber.kroneckerWeberCompositum_finrank_le_totient`.

Step 4. Since $\mathbb{Q}(\zeta_n) \subset M$ has degree $\varphi(n)$, we get $M = \mathbb{Q}(\zeta_n)$, and $L \subset \mathbb{Q}(\zeta_n)$. $\square$

The port states the conclusion as `KroneckerWeber.exists_cyclotomicEmbedding`, and `ClassFieldTheory.kroneckerWeber` is a wrapper around it. The proof in the file `KroneckerWeber/Final.lean` uses local class field theory and Hilbert's ramification theory, but not global reciprocity. So the Lean proof of Theorem 7.5.3 does not depend on Theorem 7.3.1.

**Example 7.5.4 (quadratic fields).** Let $F = \mathbb{Q}(\sqrt d)$ with discriminant $D$. Then $F \subset \mathbb{Q}(\zeta_{|D|})$. For an odd prime $p$ and $p^* = (-1)^{(p-1)/2} p$, the Gauss sum $g = \sum_{a \bmod p} \left(\frac{a}{p}\right) \zeta_p^a$ satisfies $g^2 = p^*$, so $\sqrt{p^*} \in \mathbb{Q}(\zeta_p)$. Volume 1, Lemma 1.5.7, proves this last fact in another way. Also $i \in \mathbb{Q}(\zeta_4)$ and $\sqrt{2} = \zeta_8 + \zeta_8^{-1}$. Since $D$ is a product of the factors $p^*$, $-4$, $8$ and $-8$, the claim follows. The character of $\mathrm{Gal}(\mathbb{Q}(\zeta_{|D|})/\mathbb{Q}) \cong (\mathbb{Z}/|D|\mathbb{Z})^\times$ with kernel $\mathrm{Gal}(\mathbb{Q}(\zeta_{|D|})/F)$ is the Kronecker symbol $\left(\frac{D}{\cdot}\right)$. So for $p \nmid D$, $p$ splits in $F$ if and only if $\left(\frac{D}{p}\right) = 1$. This is quadratic reciprocity in the form "the splitting of $p$ depends only on $p$ modulo $|D|$".

**Proposition 7.5.5 (the cyclotomic case over any field).** Let $F$ be a number field and $m \ge 1$. The norm group of $F(\zeta_m)$ in $C_F$ is the inverse image under $N_{F/\mathbb{Q}}$ of the norm group of $\mathbb{Q}(\zeta_m)$ in $C_\mathbb{Q}$. A prime $\mathfrak{p} \nmid m$ of $F$ splits completely in $F(\zeta_m)$ if and only if $N\mathfrak{p} \equiv 1 \bmod m$.

Lean: not stated yet

*Proof.* By Proposition 7.2.2, part 4, $\mathrm{art}_{F(\zeta_m)/F}(x)$ restricts to $\mathrm{art}_{\mathbb{Q}(\zeta_m)/\mathbb{Q}}(N_{F/\mathbb{Q}} x)$, and restriction is injective. For the second claim, $\mathrm{Frob}_\mathfrak{p}$ acts on $\mu_m$ as $\zeta \mapsto \zeta^{N\mathfrak{p}}$. $\square$

**Remark 7.5.6 (Hilbert's twelfth problem).** Theorem 7.5.3 says that the values of $e^{2\pi i x}$ at $x \in \mathbb{Q}$ generate $\mathbb{Q}^{ab}$. Kronecker's "Jugendtraum" was the analogue for an imaginary quadratic field $K$. There the theory of complex multiplication shows that $K^{ab}$ is generated by the $j$-invariants of the elliptic curves with complex multiplication by orders of $K$ and by the values of Weber functions at their torsion points. In particular the Hilbert class field of $K$ is $K(j(\mathcal{O}_K))$. Volume 4 treats this. For other fields, Hilbert's twelfth problem asks for such explicit generators. It is open in general. There is recent progress for totally real fields by Dasgupta and Kakde, with Brumer-Stark units. The Lean project states none of this yet.
