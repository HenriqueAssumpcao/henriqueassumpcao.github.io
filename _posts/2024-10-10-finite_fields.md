---
layout: distill
title: finite fields
date: 2024-10-10
description: some basic facts about finite fields
tags: 
categories: math galois-theory
giscus_comments: false
related_posts: false
related_publications: 

toc:
  - name: "Finite fields and multiplicative groups"
  - name: "Some facts about field extensions"
  - name: "Fundamental Theorem of Finite Fields"


---
This post will contain some basic facts about finite fields. It will be quite useful for some future posts I plan to make on Galois theory, but these are facts that are useful in general for anyone interested in combinatorics and algebra.

## Finite fields and multiplicative groups
Let $$\mathbb{F}$$ be a field, and define its **characteristic** $$\text{char}(\mathbb{F})$$ as the smallest number $$n$$ such that $$\sum_{i=1}^n 1 = 0$$. If there is no such $$n$$, we say that $$\text{char}(\mathbb{F}) = 0$$. The first observation we must make is that $$\text{char}(\mathbb{F})$$ is a prime number if $$\mathbb{F}$$ is finite. Indeed, the characteristic of $$\mathbb{F}$$ is certainly positive as the field is finite, and if it is a composite number $$n = ab$$, then

$$
(\sum_{i=1}^a 1)(\sum_{i=1}^b 1) = \sum_{i=1}^n 1 = 0,
$$

hence either $$\sum_{i=1}^a 1 = 0$$ or $$\sum_{i=1}^b 1 = 0$$, and thus $$\text{char}(\mathbb{F})$$ must indeed be prime. This will also imply that the size of $$\mathbb{F}$$ must be a power of a prime. To see this, if $$\text{char}(\mathbb{F}) = p$$ where $$p$$ is prime, we consider the set $$\{1,2,...,p\} \subseteq \mathbb{F}$$, hence we may identify a copy of $$\mathbb{Z}_p$$ in $$\mathbb{F}$$, and this copy is the **prime subfield** of $$\mathbb{F}$$ -- that is, the intersection of all subfields of $$\mathbb{F}$$. This implies that $$\mathbb{F}$$ can be seen as a vector space over $$\mathbb{Z}_p$$, hence if $$a_1,...,a_k$$ is a basis of this space, we have $$p^k$$ possible linear combinations of these vectors, hence $$\mathbb{F} = p^k$$. From this, we may always denote a finite field by $$\mathbb{F}_q$$, where $$q$$ is its size and $$q = p^k$$, for some prime $$p$$ and integer $$k$$, with $$\text{char}(\mathbb{F}) = p$$.

If $$\mathbb{F}$$ is a field, we denote by $$\mathbb{F}^*$$ the set of invertible elements of the field -- which in this case are all non-zero elements --, and it is immediate to note that this set is a group with multiplication, called the **multiplicative group**. We will soon see that the multiplicative group of a finite group is cyclic, but first we will lay out some basic facts about cyclic groups.

All cyclic groups of a fixed order $$n$$ are isomorphic, hence we denote by $$C_n$$ the cyclic group of order $$n$$. We first note that if $$g$$ is a generator for $$C_n$$, then ther order of any element $$g^i$$ is given by

$$
\text{ord}(g^i) = \frac{n}{\gcd(n,i)},
$$

hence $$\text{ord}(g^i) = n$$ iff $$\gcd(n,i) = 1$$, and thus the number of generators of $$C_n$$ is precisely given by $$\varphi(n)$$, where

$$
\varphi(n) = \{k \in \{1,...,n\}|\gcd(n,k) = 1\}
$$

is the Euler totient function, i.e., $$\varphi(n) = \vert \mathbb{Z}_n^* \vert $$. It is easy to see that any subgroup of $$C_n$$ must also be cyclic, hence by Lagrange's theorem it follows that any subgruop of $$C_n$$ is a copy of $$C_d$$, for some divisor $$d$$ of $$n$$. Now if $$d \vert n$$, then the element $$g^{n/d}$$ has order $$d$$, hence its generated cyclic subgroup $$\langle g^{n/d} \rangle$$ is a copy of $$C_d$$. On the other hand, if $$g^i$$ is some element in $$C_n$$ of order $$d$$, then $$n/d$$ must be a divisor of $$i$$, hence $$g^i \in \langle g^{n/d} \rangle$$. This shows that for each divisor $$d$$ of $$n$$, there exists a unique subgroup $$C_d$$ of $$C_n$$, and we can express this subgroup as

$$
C_d = \{x \in C_n|x^d = 1\}.
$$

It is also worth noting that the previous observations imply that the set of elements of order $$d$$ in $$C_n$$ are all contained in the unique copy of $$C_d$$ in $$C_n$$, for some divisor $$d$$, hence

$$
\vert\{x \in C_n|\text{ord}(x) = d\}\vert = \vert\{x \in C_d|\text{ord}(x) = d\}\vert.
$$

These facts imply the following useful equality:

$$
\begin{split}
n = |C_n| &= \sum_{d \vert n} \vert\{x \in C_n|\text{ord}(x) = d\}\vert\\
&= \sum_{d \vert n} \vert\{x \in C_d|\text{ord}(x) = d\}\vert\\
&= \sum_{d \vert n} \varphi(d).
\end{split}
$$




We are now ready to prove the desired result.

**Theorem 1:** The multiplicative group $$\mathbb{F}_q^*$$ of a finite field $$\mathbb{F}_q$$ is cyclic.

**Proof:** Let $$n \geq 1$$ be the size of $$\mathbb{F}_q^*$$, and let $$m_d$$ denote the number of elements of order $$d$$ in $$\mathbb{F}_q^*$$, and of course, if $$d$$ doesn't divide $$n$$ then $$m_d = 0$$. Our goal here is to show that $$m_n = \varphi(n) \geq 1$$, and thus conclude that there is an element of order $$n$$, which must necessarily be a generator for $$\mathbb{F}_q^*$$.

 First, we note that any element of order $$d$$ in our group must be a root of the polynomial $$t^d - 1$$, but on the other hand, if $$x$$ is an element of order $$d$$, then all elements in the cyclic subgroup $$C_d$$ it generates are also roots of $$t^d - 1$$. Since this polynomial has at most $$d$$ roots in $$\mathbb{F}_q$$, it follows that $$C_d$$ is precisely this set of roots, that is,

$$
C_d = \{x \in \mathbb{F}_q|x^d = 1\}.
$$

This shows that if $$m_d > 0$$, then $$m_d = \varphi(d)$$, since in this case all of the $$m_d$$ elements of order $$d$$ in $$\mathbb{F}_q$$ would be precisely the $$\varphi(d)$$ generators of $$C_d$$. Hence, for any $$d$$ that divides $$n$$, it follows that $$m_d \leq \varphi(d)$$. We thus obtain the following:

$$
n = |\mathbb{F}_q^*| = \sum_{d \vert n}m_d \leq \sum_{d \vert n}\varphi(d) = n,
$$

which implies that $$m_d = \varphi(d)$$, and in particular, $$m_n = \varphi(n) \geq 1$$, which concludes the proof.


$$\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\blacksquare$$

## Some facts about field extensions

Before moving forward, we'll need some results about field extensions. If $$\mathbb{E}$$ is a field that contains a field $$\mathbb{F}$$, we say that $$\mathbb{E}:\mathbb{F}$$ is a **field extension**, and the **degree** of this extension is the dimension of $$\mathbb{E}$$ as a vector space over $$\mathbb{F}$$. We then note the following:

**Lemma 1:** Let $$\mathbb{F}$$ be a field, $$f(x) \in \mathbb{F}[x]$$ a polynomial with coefficients on the field. Then the following hold:

* If $$f'(x)$$ denotes the formal derivative of $$f$$, then $$\gcd(f,f') \neq 1$$ iff $$f$$ has multiple roots in some extension of $$\mathbb{F}$$;

* If $$g \in \mathbb{F}[x]$$, then $$\gcd(f,g)$$ is invariant w.r.t. extensions of $$\mathbb{F}$$.

**Proof:** For the first claim, if $$d = \gcd(f,f') \neq 1$$, then it has degree at least $$1$$, which implies that there is some root $$\alpha$$ of $$d$$ is some extension $$\mathbb{E}$$ of $$\mathbb{F}$$. Hence, we have that $$(x-\alpha)$$ divides $$f$$, and thus

$$
f = q(x-\alpha) \Rightarrow f' = q'(x-\alpha) + q,
$$

thus $$q = f-q'(x-\alpha) = (x-\alpha)(q-q')$$, thus $$x-\alpha$$ divides $$q$$, which implies that $$(x-\alpha)^2$$ divides $$f$$, hence it has multiple roots. Now if $$(x-\alpha)^2$$ divides $$f$$ for some $$\alpha$$ in an extension of $$\mathbb{F}$$, then

$$
f = q(x-\alpha)^2 \Rightarrow f' = q'(x-\alpha)^2 + 2q(x-\alpha),
$$

thus $$(x-\alpha)$$ divides $$f'$$, hence $$\gcd(f,f') \neq 1$$.

For the second claim, if $$d$$ is the gcd of $$f,g$$ in $$\mathbb{F}$$, and $$D$$ is the gcd in $$\mathbb{E}$$, then we know that there are polynomials $$r,s \in \mathbb{F}[x]$$ such that

$$
d = rf + sg,
$$

and since $$D$$ divides both $$r$$ and $$s$$, it follows that $$D$$ divides $$d$$, but on the other hand, $$D$$ is defined as the gcd over $$\mathbb{E}$$, hence any polynomial that divides both $$f,g$$ must divide $$D$$, and so $$D = d$$, as desired.

$$\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\blacksquare$$

If $$f(x)$$ is a polynomial over $$\mathbb{F}$$, and if $$\mathbb{E}$$ is an extension such that we can write

$$
f(x) = \alpha_0(x-\alpha_1)\ldots(x-\alpha_n),
$$

where $$n = \text{deg}(f)$$ and $$\alpha_i \in \mathbb{E}$$, then we say that the smallest extension of $$\mathbb{F}$$ containing each $$\alpha_i$$ is a **splitting field** of $$f$$. We will discuss such fields in more detail in a later post, but for now we only need to know that we can decompose $$f$$ as a product of irreducibles in the splitting field, that is, such field contains all roots of our polynomial.

## Fundamental Theorem of Finite Fields

We can now prove the basic theorem about finit fields: we can always create a finite field of order $$p^k$$ for any fixed prime $$p$$ and integer $$k$$, and all finite fields of the same order are isomorphic. For this reason, it is usual to see authors denote a finite field of order $$q$$ simply by $$\mathbb{F}_q$$ or $$\text{GF}(q)$$, as they are unique up to isomorphism. 

First, we introduce a rather useful function of finite fields. Define

$$
\begin{split}
\Phi:\mathbb{F}_q &\mapsto \mathbb{F}_q,\\
\Phi(x) &= x^p,
\end{split}
$$
where $$p$$ is the characteristic of our finite field $$\mathbb{F}_q$$. Our claim is that this map is a field automorphism. Indeed, we first note that $$\Phi(xy) = \Phi(x)\Phi(y),\Phi(1) = 1$$ and that

$$
\Phi(x+y) = x^p + (\sum_{k=1}^{p-1}{p \choose k}x^ky^{p-k}) + y^p,
$$

but since $$p$$ is prime, the coefficients $${p \choose k}$$ are all multiples of $$p$$, hence $$\Phi(x+y) = \Phi(x)+\Phi(y)$$, and so $$\Phi$$ is a field homomorphism. It is certainly injective, since if $$x^p = 1$$ then $$x = 1$$. Since $$\mathbb{F}_q$$ has finite size $$p^k$$, its multiplicative group has size $$q-1$$ and so $$x^q = x$$ for any $$x \in \mathbb{F}_q$$, hence $$\Phi(x^{p^{k-1}}) = x$$, and thus $$\Phi$$ is surjective.

With this, we can prove the following:

**Theorem 2:** Let $$p$$ be a prime number, and let $$k$$ be some nonnegative integer, with $$q = p^k$$. Then the following hold:

* There exists some finite field of size $$q$$;
* Every finite field with $$q$$ elements is a splitting field for the polynomial $$t^q - t$$;

**Proof:** For the first claim, we let $$\mathbb{K}$$ be a splitting field of $$f(t) = t^q - t$$ over $$\mathbb{Z}_p$$, and we consider the set of all roots of this polynomial:

$$
\mathbb{F} = \{\alpha \in \mathbb{K}|f(\alpha) = 0\}.
$$

This set has size at most $$q$$, however note that

$$
(f)' = qt^{q-1} - 1 = 1,
$$

since $$q = p^k = 0$$ in $$\mathbb{Z}_p$$, hence $$\gcd(f,f') = 1$$, which shows that $$f$$ has no multiple roots, hence $$\mathbb{F}$$ has size $$q$$. It is easy to check that $$\mathbb{F}$$ is indeed a field, which proves the claim.

For the second claim, let $$\mathbb{K}$$ be field of size $$q$$, and note for any element $$\alpha$$ in the field, it follows that $$\alpha^{q-1} = 1$$, hence if we write

$$
f(t) = t^q - t = t(t^{q-1} - 1),
$$

we get that $$f(\alpha) = 0$$, thus all elements of $$\mathbb{K}$$ are roots of $$f$$, and so $$\mathbb{K}$$ is a splitting field.

$$\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\blacksquare$$

We can also prove that if $$\mathbb{F}_1,\mathbb{F}_2$$ are fields of size $$q$$, then they are isomorphic, but in order to do this we need some results about splitting fields that I will introduce in a later post.

To end this post, we prove the following:

**Proposition 1:** If $\mathbb{F}_q$ is a finite field, with $q = p^k$ for some prime $p$, then the subfields of $\mathbb{F}_q$ are uniquely determined by the divisors of $k$, i.e., $\mathbb{K} \subseteq \mathbb{F}_q$ is a subfield if and only if $|\mathbb{K}| = p^e$ and $e \vert d$, and these subfields are unique.

**Proof:** First, we note that since any subfield of $\mathbb{F}_q$ is also an abelian subgroup, it follows that its order must be some power of $p$ -- simply by Lagrange's Theorem. Now if $\mathbb{K}$ is a subfield of $\mathbb{F}_q$ of order $p^d$, then $\mathbb{K}^* \leq \mathbb{F}_q^*$, hence again by Lagrange's Theorem it follows that 

$$
p^d - 1 = \vert \mathbb{K}^*\vert\vert \vert \mathbb{F}_q^* \vert = p^k - 1
$$

and since $p$ is a prime this implies that $d \vert k$. Now assume that $d \vert k$, and thus $p^d - 1 \vert p^k - 1$, since $\mathbb{F}_q^*$ is a cyclic group, there exists a unique subgroup $H$ of order $p^d - 1$, where of course $H$ is also cyclic, and since $H$ can be identified as

$$
H = \{x \in \mathbb{F}_q^*|x^{p^d} = x\}
$$

it follows that $\mathbb{K} = \{0\} \cup H$ is a subfield of $\mathbb{F}_q$ with order $p^k$, where $d \vert k$, and the uniqueness of the subgroup implies that $\mathbb{K}$ is also unique. The facts together show that there are unique subfields of $\mathbb{F}_q$ for every $d \vert k$, and these are all of the possible subfields.


$$\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\blacksquare$$