---
layout: distill
title: sylow theorems
date: 2024-05-10
description: proving the famous theorems related to sylow subgroups
tags: 
categories: math group-theory
giscus_comments: false
related_posts: false
related_publications: 

toc:
  - name: "Some basic facts from number theory"
  - name: "The Sylow theorems"
  - name: "Comments"


---
This semester I'm taking a course in Group Theory and Galois Theory at UFMG. This post will be about the famous Sylow theorems, and I plan on making a follow-up post about the fundamental theorem of finite abelian groups.

Let $$G$$ be a finite group of order $$n$$, and let $$\nu_p(n)$$ denote the largest power of $$p$$ that divides $$n$$, where $$p$$ is a prime. Any subgroup $$H \leq G$$ of $$G$$ with order $$\nu_p(n)$$ is called a Sylow $$p$$-subgroup. We'll show that such groups exists for all primes $$p$$, and then proceed to prove some interesting properties related to them.
 
## Some basic facts from number theory

We'll need two basic results from number theory in order to prove the Sylow Theorems.

**Theorem (Legendre's Formula):** If $$n$$ is a natural number and $$p$$ is a prime, then

$$
\nu_p(n!) = \sum_{k \geq 1}\Big\lfloor\frac{n}{p^k}\Big\rfloor
$$

**Proof:** The proof of this result becomes much easier when we get some intuitive feeling for what $$\nu_p(n!)$$ represents. This quantity is precisely the exponent of $$p$$ in the prime factorization of the input $$n!$$, but since $$n!$$ is a product of numbers and $$p$$ is prime, this implies that if $$p$$ divides $$n!$$, then it must divide one of terms in the factorial, i.e., $$p$$ must divide a number that is lesser than or equal to $$n$$. This means that there is a multiple of $$p$$ that is at most $$n$$, and conversely any number $$m \leq n$$ that is a multiple of $$p$$ contributes with at least one factor of $$p$$ in the prime factorization of $$n!$$. Thus, the number of multiples of $$p$$ is a lower bound on $$\nu_p(n!)$$, since each contributes with at least one factor of $$p$$. However, after factoring $$p$$ from each of these, there might still be multiples of $$p$$ left, namely those that are multiples of $$p^2$$, and so we can again factor $$p$$ out of each of these. We can repeat this for each $$p^k$$ ultil $$p^k > n$$, i.e., until $$k > \lfloor\log_p(n)\rfloor$$, and at this point there will be no factors of $$p$$ left in $$n!$$.

Now lets make this precise. Let $$n = qp + r$$, where $$q,r$$ are non-negative integers such that $$0 \leq r < p$$, and note that

$$
\frac{n}{p} = q + \frac{r}{p}
$$

and since $$r/p < 1$$, it follows that

$$
\Big\lfloor\frac{n}{p}\Big\rfloor = q
$$

This means that $$\lfloor\frac{n}{p}\rfloor$$ is precisely the number of multiples of $$p$$ that are lesser than or equal to $$n$$, and also note that $$q > 0$$ iff $$ p \leq n$$. Now consider the following inductive procedure:

  * Each multiple of $$p$$ contributes with at least one factor of $$p$$ in $$n!$$, and there exactly $$\lfloor\frac{n}{p}\rfloor$$ such multiples, so we factor $$p$$ from each of them, that is, we factor out $$p^{\lfloor\frac{n}{p}\rfloor}$$ from $$n!$$
  * If we now look at $$n!/p^{\lfloor\frac{n}{p}\rfloor}$$, any multiples of $$p$$ will again contribute with at least one factor of $$p$$, but any such multiples must also be multiples of $$p^2$$, and there are precisely $$\lfloor\frac{n}{p^2}\rfloor$$ of those, thus we can factor out $$p^{\lfloor\frac{n}{p^2}\rfloor}$$
  * We can repeat this process until $$k > \lfloor\log_p(n)\rfloor$$, and at this point we'll have factored out every possible factor of $$p$$ from each multiple of $$p$$ that is at most $$n$$

After doing this, we'll have factored out

$$
\sum_{k=1}^{\lfloor\log_p(n)\rfloor}\Big\lfloor\frac{n}{p^k}\Big\rfloor = \sum_{k \geq 1}\Big\lfloor\frac{n}{p^k}\Big\rfloor
$$

factors of $$p$$ from $$n!$$, showing that

$$
\nu_p(n!) \geq \sum_{k \geq 1}\Big\lfloor\frac{n}{p^k}\Big\rfloor
$$

On the other hand, by the arguments made before, any factor of $$p$$ in $$n!$$ must come from a multiple of $$p$$ that is at most $$n$$, but by construction the previous procedure factors out all possible factors of $$p$$ from each of these multiples, hence the previous quantity is also an upper bound on $$\nu_p(n!)$$, which proves the desired result.

$$\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\blacksquare$$

We can now use this fact to prove an important Lemma.

**Lemma:** If $$p$$ is a prime and $$n$$ is a non-negative integer, then $$p$$ does not divide

$$
{n \choose p^{\nu_p(n)}}
$$

**Proof:** Let $$\alpha = \nu_p(n)$$, then

$$
{n \choose p^{\alpha}} = \frac{n!}{(p^{\alpha})!(n-p^{\alpha})!}
$$

The idea now is to show that $$p^{\nu_p(n!)}$$ appears in this denominator. By Legendre's formula, we have

$$
\nu_p(p^{\alpha}!) = \sum_{k\geq 1}\Big\lfloor\frac{p^{\alpha}}{p^k}\Big\rfloor\quad\text{and}\quad
\nu_p((n-p^{\alpha})!) = \sum_{k\geq 1}\Big\lfloor\frac{n-p^{\alpha}}{p^k}\Big\rfloor
$$

Now note that if $$a,b$$ are non-negative integers, then the exponent of $$p$$ in the prime factorization of $$ab$$ will be the sum of the exponents of $$p$$ in the factorizations of $$a$$ and $$b$$, i.e., $$\nu_p(ab) = \nu_p(a) + \nu_p(b)$$. This implies that

$$
\nu_p((p^{\alpha})!(n-p^{\alpha})!) =
\sum_{k\geq 1} \Big\lfloor\frac{p^{\alpha}}{p^k}\Big\rfloor + \Big\lfloor\frac{n-p^{\alpha}}{p^k}\Big\rfloor\\
$$

Now fix $$k \geq 1$$ and note that

$$
n = \Big\lfloor\frac{n}{p^k}\Big\rfloor p^k + r
$$

where $$0 \leq r < p^k$$ and $$\Big\lfloor\frac{n}{p^k}\Big\rfloor$$ are unique, on the other hand

$$
\begin{split}
n &= (n-p^{\alpha}) + p^{\alpha}\\
&= (\Big\lfloor\frac{n-p^{\alpha}}{p^k}\Big\rfloor p^k + r') + (\Big\lfloor\frac{p^{\alpha}}{p^k}\Big\rfloor p^k + r'')\\
&= (\Big\lfloor\frac{n-p^{\alpha}}{p^k}\Big\rfloor + \Big\lfloor\frac{p^{\alpha}}{p^k}\Big\rfloor)p^k + (r'+r'')\\
\Rightarrow \Big\lfloor\frac{n}{p^k}\Big\rfloor p^k + r &= (\Big\lfloor\frac{n-p^{\alpha}}{p^k}\Big\rfloor + \Big\lfloor\frac{p^{\alpha}}{p^k}\Big\rfloor)p^k + (r'+r'')
\end{split}
$$

and since $$0 \leq r',r'' < p^k$$, the uniqueness of the euclidean division implies that $$r = r' + r''$$ and 

$$
\Big\lfloor\frac{n}{p^k}\Big\rfloor = \Big\lfloor\frac{n-p^{\alpha}}{p^k}\Big\rfloor + \Big\lfloor\frac{p^{\alpha}}{p^k}\Big\rfloor
$$

for all $$k \geq 1$$, hence

$$
\nu_p(n!) = \nu_p((p^{\alpha})!(n-p^{\alpha})!)
$$

implying that the largest exponent of p in the factorization $$n!$$ already appears in $$(p^{\alpha})!(n-p^{\alpha})!$$, and so $$p$$ does not divide $${n \choose p^{\alpha}}$$.

$$\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\blacksquare$$

## The Sylow theorems

**Theorem (First Sylow theorem):** If $$G$$ is a finite group of order $$n$$, and $$p$$ be a prime, then there exists a Sylow $$p$$-subgroup of $$G$$. 

**Proof:**

Let $$\nu_p(n) = \alpha$$, and consider $$F = \{ X \subseteq G:\vert X\vert = p^\alpha \}$$ as the set of all subsets of $$G$$ with cardinality precisely $$p^\alpha$$, and note that the cardinality of $$F$$ is given by

$$
{n \choose p^\alpha}.
$$

We observe that $$G$$ acts on $$F$$ via right multiplication

$$
g \in G,X \in F:Xg = \{xg:x \in X\}
$$

The orbits form a partition of $$F$$, and since by the previous Lemma we know that $$p$$ does not divide $$\vert F\vert$$, it follows that there must be some orbit $$GX$$ s.t. $$p$$ does not divide $$\vert GX\vert$$. Let $$H = G_X$$ denote the stabilizer of $$X$$ w.r.t. $$G$$, and this subgroup will be our candidate for a Sylow $$p$$-subgroup of $$G$$. By the Orbit-Stabilizer theorem we have

$$
\vert G\vert = \vert GX\vert \vert G_X\vert.
$$

Since by definition $$p^\alpha$$ divides $$\vert G\vert$$ and since $$p$$ does note divide $$\vert GX\vert$$, it follows that $$p^\alpha$$ divides $$\vert H\vert$$, hence $$p^\alpha \leq \vert H\vert$$. Now in order to prove the upper bound, we observe that $$H$$ acts on $$X$$ via right multiplication since $$H \leq G$$, and if $$x \in X$$, the the stabilizer of $$x$$ w.r.t. to $$H$$ is

$$
H_x = \{g \in H:xg = x\} = \{1\},
$$

since both $$x,g \in G$$, hence again by the Orbit-Stabilizer theorem we have

$$
\vert H\vert  = \vert Hx\vert \vert H_x\vert  = \vert Hx\vert 
$$

however note that $$X$$ is partitioned by the orbits $$Hx$$, hence $$\vert Hx\vert  \leq \vert X\vert  = p^\alpha$$, thus

$$
\vert H\vert  = \vert Hx\vert  \leq p^\alpha
$$

implying that $$\vert H\vert  = p^\alpha$$, as desired.

$$\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\blacksquare$$

**Theorem (Second Sylow theorem):** If $$G$$ is a finite group of order $$n$$, and $$p$$ be a prime, then if $$P,Q$$ are Sylow $$p$$-subgroups, then $$P$$ and $$Q$$ are conjugate, i.e., there exists some $$g \in G$$ such that $$Q = P^g = \{gxg^{-1}\vert x \in P\}$$.

**Proof:** Again let $$\nu_p(G) = \alpha$$, and let $$P^G = \{P^g\vert g \in G\}$$ be the orbit of $$P$$ w.r.t. the action of $$G$$ via conjugation on the set of all of its subgroups. $$G$$ acts on $$P^G$$ via conjugation, hence if we fix $$K = P^g$$ for some $$g \in G$$, we get via the Orbit-Stabilizer theorem we have

$$
\vert G\vert  = \vert K^G\vert \vert N_G(K)\vert 
$$

where $$N_G(K) = \{h \in G:(K)^h = K\}$$ is the normalizer of $$K$$ in $$G$$, and clearly $$K \leq N_G(K)$$. Since $$K$$ is conjugate to $$P$$, it follows that it is a Sylow $$p$$-group, and it also is a subgroup of its normalizer, thus by Lagrange's theorem we conclude that $$p^\alpha$$ divides $$\vert N_G(K)\vert $$. Since this is the largest power of $$p$$ that divides $$\vert G\vert $$, it follows that $$p$$ does not divide $$\vert K^G\vert $$. On the other hand, we also know that $$Q$$ acts on $$K^G$$ via conjugation, so let $$C_1,...,C_m$$ be the orbits of such action, hence

$$
K^G = C_1 \sqcup C_2 \sqcup\ldots\sqcup C_m
$$

Again by the Orbit-Stabilizer theorem, we know that $$\vert C_i\vert $$ must divide $$\vert Q\vert  = p^\alpha$$, thus $$\vert C_i\vert  = p^{\beta_I}$$ for some $$\beta_i \geq 0$$, hence

$$
\vert K^G\vert  = p^{\beta_1} + ... + p^{\beta_m}
$$

but since $$p$$ does not divide $$\vert K^G\vert $$, this means that there is some $$i$$ s.t. $$\beta_i = 0$$, i.e., $$\vert C_i\vert  = 1$$, implying that $$C_i = \{K^{f}\}$$ for some $$f \in G$$ such that $$(K^{f})^h = K^{f}$$ for any $$h \in Q$$, i.e., $$Q \leq N_G(K^{f})$$. This means that $$Q$$ normalizes $$K$$, and thus $$KQ$$ is a subgroup of $$G$$ with order

$$
\vert KQ\vert  = \frac{\vert K\vert \vert Q\vert }{\vert K \cap Q\vert } = \frac{p^\alpha p^\alpha}{\vert K \cap Q\vert }
$$

but since $$KQ \leq G$$ and $$\vert KQ\vert $$ divides $$G$$, this means that $$\vert KQ\vert  \leq p^\alpha$$, implying that $$\vert K \cap Q\vert $$ must be a multiple of $$p^\alpha$$, but since both $$K$$ and $$Q$$ are Sylow $$p$$-groups, this implies that $$\vert K \cap Q\vert  = p^\alpha = \vert K\vert  = \vert Q\vert $$, hence $$K=Q$$. Since $$K = P^g$$, this implies that $$Q$$ and $$P$$ are conjugate, which concludes the proof.

$$\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\blacksquare$$

**Theorem (Third Sylow theorem):** The number of Sylow $$p$$-groups of a finite group is congruent to $$1$$ modulo $$p$$.

**Proof:** Let $$P$$ be a $$p$$-Sylow subgroup, thus by the previous theorem we know that $$P^G$$ is the set of all $$p$$-Sylow subgroups, hence we need to show that $$\vert P^G\vert  \equiv 1 \mod p$$ . Note that $$P$$ acts on $$P^G$$ by conjugation, and that $$\{P\}$$ is an orbit of such action, since $$(P^1)^x = P$$ for all $$x \in P$$. Now assume that there is some $$\{R\}$$ that is also an orbit of size $$1$$ in this action, thus $$R^x = R$$ for any $$x \in P$$, implying that $$P \leq N_G(R)$$, i.e., $$P$$ normalizes $$R$$. We've seen in the previous proof that this means that $$PR$$ is a subgroup of $$G$$, but since they are both $$p$$-Sylow subgroups, this implies that $$P = R$$. Hence there is only one orbit of size one in the action of $$P$$ on $$P^G$$, and since the size of the orbits must divide the order of $$P$$, this implies that all other orbits have size equal to some positive power of $$p$$. Now since these same orbits partition $$P^G$$, we get that $$\vert P^G\vert  = 1 + pk$$, where $$k \in \mathbb{N}$$, hence  $$\vert P^G\vert  \equiv 1 \mod p$$, as desired.

$$\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\blacksquare$$

## Comments
There are some some results in mathematics that are really important and yet have quite boring and laborius proofs that don't highligh some specially interesting idea, but this is certainly not the case with the Sylow Theorems. The results in and of themselves are extremely important -- e.g. one of the many proofs of fundamental theorem of algebra requires the first theorem -- however the techniques used to prove them are to me their most interesting aspect. The idea of looking at the action of a subgroup on the orbits of another is something that in retrospect seems like a rather straighforward idea, but is something that I doubt I would have come up with by myself, and I'm quite glad that I've added this technique to my "toolbox".