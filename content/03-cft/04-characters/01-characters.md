---
title: Characters of the multiplicative group
nodes: []
sources: [Tat79, Ser79]
status: drafted
drafted_by: writer
reviewed_by: []
---
## Characters of the multiplicative group

The group $K^\times$ is locally compact and totally disconnected. Its characters have a simple structure, because $\mathbb{C}^\times$ has no small subgroups.

**Definition 4.1.1 (characters).** A *character* of $K^\times$ is a continuous homomorphism $\chi : K^\times \to \mathbb{C}^\times$. It is *unitary* if $|\chi(x)| = 1$ for all $x$. It is *unramified* if it is trivial on $\mathcal{O}_K^\times$, and *ramified* otherwise.

**Lemma 4.1.2 (no small subgroups).** Let $\chi$ be a character of $K^\times$. Then $\chi$ is trivial on $U^{(n)}$ for some $n \ge 0$. In particular $\chi$ is locally constant, and $\chi(\mathcal{O}_K^\times)$ is a finite group of roots of unity.

Lean: not stated yet

*Proof.* Let $V = \{z \in \mathbb{C}^\times : |z - 1| < 1\}$. The only subgroup of $\mathbb{C}^\times$ inside $V$ is $\{1\}$. Indeed, let $z \ne 1$ be in such a subgroup. If $|z| \ne 1$, then $|z^m|$ is unbounded or tends to 0 for $m \to \pm\infty$, so some power leaves $V$. If $|z| = 1$, write $z = e^{i\alpha}$ with $0 < |\alpha| \le \pi$. Some multiple $m\alpha$ lies in $[\pi/2, 3\pi/2]$ modulo $2\pi$, and then $|z^m - 1| \ge \sqrt 2$. The set $\chi^{-1}(V)$ is an open neighbourhood of 1, so it contains $U^{(n)}$ for some $n$. Then $\chi(U^{(n)})$ is a subgroup inside $V$, so it is trivial. The quotient $\mathcal{O}_K^\times / U^{(n)}$ is finite, so $\chi(\mathcal{O}_K^\times)$ is a finite subgroup of $\mathbb{C}^\times$. $\square$

The same argument shows that a character of any profinite group has open kernel and finite image. In the language of representation theory, every character of $K^\times$ is *smooth*.

**Definition 4.1.3 (conductor).** The *conductor exponent* $a(\chi)$ of a character $\chi$ of $K^\times$ is the smallest $n \ge 0$ with $\chi(U^{(n)}) = 1$. The ideal $\varpi^{a(\chi)} \mathcal{O}_K$ is the *conductor* of $\chi$. The character is *tamely ramified* if $a(\chi) \le 1$.

Thus $a(\chi) = 0$ if and only if $\chi$ is unramified. A character with $a(\chi) = 1$ restricts on $\mathcal{O}_K^\times$ to a character of $(\mathcal{O}_K/\varpi)^\times = k^\times$. A character with $a(\chi) = n \ge 1$ restricts to a character of $(\mathcal{O}_K/\varpi^n)^\times$ that is not trivial on $U^{(n-1)}/U^{(n)}$.

**Proposition 4.1.4 (unramified characters).** The map $\chi \mapsto \chi(\varpi)$ is an isomorphism from the group of unramified characters of $K^\times$ onto $\mathbb{C}^\times$. It does not depend on the uniformizer $\varpi$. Each unramified character is $x \mapsto |x|^s$ for some $s \in \mathbb{C}$, and $s$ is unique modulo $2\pi i / \log q$.

Lean: not stated yet

*Proof.* An unramified character factors through $v : K^\times / \mathcal{O}_K^\times \cong \mathbb{Z}$, and a homomorphism $\mathbb{Z} \to \mathbb{C}^\times$ is determined by the image $z$ of 1. Every $z$ occurs, and the character $x \mapsto z^{v(x)}$ is continuous because $\mathcal{O}_K^\times$ is open. Two uniformizers differ by a unit, so $\chi(\varpi)$ does not depend on $\varpi$. Finally $|x|^s = q^{-s v(x)}$, and $q^{-s}$ takes each value in $\mathbb{C}^\times$, with $q^{-s} = q^{-s'}$ if and only if $s - s' \in (2\pi i/\log q)\mathbb{Z}$. $\square$

**Proposition 4.1.5 (structure of characters).** Fix a uniformizer $\varpi$.
1. The map $\chi \mapsto (\chi|_{\mathcal{O}_K^\times}, \chi(\varpi))$ is a bijection from the characters of $K^\times$ to the pairs of a character of $\mathcal{O}_K^\times$ and an element of $\mathbb{C}^\times$.
2. For each character $\chi$ there is a unique real number $\sigma$ such that $\chi = \chi_0 |\cdot|^\sigma$ with $\chi_0$ unitary.

Lean: not stated yet

*Proof.* Part 1 holds because $K^\times = \varpi^{\mathbb{Z}} \times \mathcal{O}_K^\times$ as a topological group. For part 2, the character $|\chi|$ takes values in $\mathbb{R}_{>0}$. By Lemma 4.1.2 it is trivial on $\mathcal{O}_K^\times$, since $\mathbb{R}_{>0}$ has no nontrivial finite subgroup. So $|\chi|$ is unramified and positive, and $|\chi(\varpi)| = q^{-\sigma}$ for a unique real $\sigma$. Then $\chi_0 = \chi |\cdot|^{-\sigma}$ is unitary. $\square$

The decomposition in part 1 depends on $\varpi$. The decomposition in part 2 does not. The number $\sigma$ is the *exponent* of $\chi$. A character has finite order if and only if $\chi(\varpi)$ is a root of unity, because $\chi(\mathcal{O}_K^\times)$ is always finite.

**Example 4.1.6 (Dirichlet characters).** Let $K = \mathbb{Q}_p$, and let $\eta$ be a character of $(\mathbb{Z}/p^n\mathbb{Z})^\times$, a Dirichlet character modulo $p^n$. There is a unique character $\chi_\eta$ of $\mathbb{Q}_p^\times$ with $\chi_\eta(p) = 1$ and $\chi_\eta(u) = \eta(u \bmod p^n)$ for $u \in \mathbb{Z}_p^\times$. If $\eta$ is primitive, with conductor $p^n$, then $a(\chi_\eta) = n$. Each character of finite order of $\mathbb{Q}_p^\times$ is $\chi_\eta \cdot \mu$ for a Dirichlet character $\eta$ of $p$-power conductor and an unramified character $\mu$ of finite order.

**Example 4.1.7 (quadratic characters).** Let $p$ be odd. The quadratic characters $\chi_d$ of Example 2.5.5 have the following conductors. The character $\chi_\varepsilon$ of the unramified extension has $a = 0$. The characters $\chi_p$ and $\chi_{\varepsilon p}$ are nontrivial on $\mathbb{Z}_p^\times$ and trivial on $1 + p\mathbb{Z}_p$, since their kernels contain the squares, so $a = 1$. For $p = 2$ the conductors are larger. Exercise 3 shows that $a(\chi_{-1}) = 2$ and $a(\chi_2) = 3$.
