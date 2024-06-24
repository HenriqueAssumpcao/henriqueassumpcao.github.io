---
layout: distill
title: symmetric and alternating groups
date: 2024-06-24
description: basics about the symmetric group and the alternating group
tags: 
categories: math group-theory
giscus_comments: false
related_posts: false
related_publications: 

toc:
  - name: "Basic facts about the symmetric group"
  - name: "The Alternating Group"


---
This is the first amongst two posts about the symmetric group and the alternating group, which in turn are part of a series of posts that will hopefully culminate in a self-contained proof of the fundamental theorem of Galois Theory. Here I will discuss some basic facts, and set the stage for the proofs regarding the simplicity of the alternating group and the solvability of the symmetric group.

## Basic facts about the symmetric group
If $$X$$ is a set, we denote by $$\text{Sym}(X)$$ as the set of all bijections from $$X$$ to $$X$$, and this set together with the operation of function composition forms a group called the *symmetric group* of $$X$$. When $$X$$ is a finite set, say with $$n$$ elements, we denote this group simply by $$\text{Sym}(n)$$, or more commonly by $$S_n$$, and we usually omit the reference to $$X$$. The symmetric group is extremely relevant in group theory, and its structure implies many different nontrivial results from many differents areas in mathematics.

When working with elements of the symmetric group, the cyclic notation for permutations is quite useful. We denote by $$(i_1,i_2)$$ the permutations -- which is often called a transposition -- that simply maps $$i_1$$ to $$i_2$$ and vice-versa, i.e., it simply switches $$i_1$$ with $$i_2$$, and by analogy we can also consider $$(i_1,...,i_k)$$ and the permutation -- called a cycle -- that maps $$i_1$$ to $$i_{2}$$, and so on, noting that $$i_k$$ gets mapped to $$i_1$$. Two cycles are called disjoint if they don't permute any common elements, and it is immediate to check that two disjoint permutations commute, and also that the order of a given cycle $$\sigma = (i_1,...,i_k)$$, i.e., the minimum exponent $$l$$ such that $$\sigma^l = 1$$, is precisely equal to its length $$k$$.

We highlight that, when working with permutations, we denote the image of an element $$x$$ by a permutation $$\sigma$$ as $$x\sigma$$, i.e., we apply the permutations on the right-hand side. We now show that all elements in $$S_n$$ can be expressed in terms of cycles and permutations.

**Proposition 1:** If $$\sigma \in S_n$$ is a permutation, then the following hold:

 * The permutation can be decomposed as a product of disjoint cycles $$\sigma = \sigma_1\cdot\ldots\sigma_k$$, and the decomposition is unique up to the order of the cycles.
 * The permutation can be decomposed as a product of transpositions $$\sigma = \tau_1 \cdot \ldots \tau_l$$, and the parity of the number of such transpositions is uniquely determined by $$\sigma$$, i.e., if $$\sigma = \tau'_1 \cdot \ldots \tau'_r$$, then $$l$$ and $$r$$ have the same parity.

**Proof:**

For the first item, we can proceed inductively: start with an element $$i \in \{1,...,n\}$$ that is not fixed by $$\sigma$$, and consider the set $$\{i,i\sigma,i\sigma^2,...\}$$. This set must be finite, and thus we obtain a cycle $$(i,i\sigma,...,i\sigma^{k_i-1})$$ where $$i\sigma^{i_k} = i$$, and hence we can consider the permutation $$\sigma'$$ that is obtained from sigma by simply fixing all elements in the aforementioned cycle, i.e., we obtain a cycle that fixes more elements than $$\sigma$$. We can repeat this process inductively, and since our base set is finite, we eventually obtain the trivial permutation, and if we consider the product of all cycles obtained in this process we get the desired decomposition. Another way of visualizing this is by simply considering the directed graph on the set $$\{1,...,n\}$$ induced by $$\sigma$$, where two nodes $$i,j$$ are connected via a directed edge if $$i\sigma = j$$, and hence we are simply finding the connected components of this graph -- and since each note has only one outgoing and incoming edges, these components are cycles. From this, uniqueness also follows immediately.

Now for the second item, we can use the previous item to see that we only need to prove this result for cycles. Let $$\sigma = (i_1,...,i_k)$$ be a cycle, and thus we can simply consider the product $$(i_1,i_2)(i_1,i_3)\ldots(i_1,i_k)$$ of $$k-1$$ transpositions, and note that this product is precisely equal to $$\sigma$$. We now need to check that the parity of this decomposition is in fact unique, and in order for us to do this we'll have to consider the action of $$S_n$$ on the polynomial ring $$\mathbb{Q}[x_1,...,x_n]$$ on $$n$$ variables, where the action simply permutes the indices of the variables. This is clearly a faithful action, i.e., if a permutation fixes all indices, then it must be the trivial permutation. We can now consider the following polynomial:

$$
F = \prod_{1\leq i< j \leq n}(x_i - x_j)
$$

Note that if $$\tau = (i,j)$$ is a transposition, then $$\tau(F) = -F$$, hence if $$\sigma = \tau_1\ldots\tau_k=\tau'_1\ldots\tau'_l$$ is written as two products of transpositions, then $$\sigma(F) = (-1)^kF = (-1)^lF$$, and thus $$l$$ and $$k$$ must have the same parity.


$$\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\blacksquare$$

If $$\sigma = (i_1,...,i_k)$$ is a cycle, and if $$\pi \in S_n$$ is an arbitrary permutation, we can obtain a nice expression for the conjugation of $$\sigma$$ by $$\pi$$:

$$
\sigma^\pi = (i_1\pi,...,i_k\pi)
$$

Indeed, this follows by simply noting that if $$j \in \{1,...,n\}$$, then either:

 * The permutation $$\pi^{-1}$$ maps $$j$$ to some $$i_l$$ in $$\{i_1,...,i_k\}$$, and in this case we get that $$j\sigma^\pi = i_{l+1}\pi$$.
 * If $$\pi^{-1}$$ does not belong to $$\{i_1,...,i_k\}$$, then $$j\sigma^\pi = j$$.

From these observations, the claim follows. We can now prove that $$S_n$$ is generated by some subsets of permutations that will be rather useful in future results.

**Proposition 2:** The symmetric group $$S_n$$  on $$n$$ elements can be written as:
$$
\begin{split}
S_n &= \langle\{(i,j)|1 \leq i,j \leq n\}\rangle\\
&= \langle\{(1,2),(2,3),...,(n-1,n)\}\rangle\\
&= \langle\{(1,2),(1,2,\ldots,n)\}\rangle
\end{split}
$$

**Proof:** 

The first equation simply follows from the previous proposition, as any element can be written as a product of transpositions.

For the second equation, note that if $$\tau = (i,j)$$ is a transposition, with $$i < j$$, then

$$
(1,2)^{(2,3)(3,4)...(j-1,j)} = (1,j)
$$

and analogously

$$
(1,j)^{(1,2)(2,3)...(i-1,i)} = (i,j)
$$

hence the set $$\langle\{(1,2),(2,3),...,(n-1,n)\}\rangle$$ contains all transpositions, and thus it must be equal to $$S_n$$.

For the third equation, we let $$\sigma = (1,2,...,n),\tau = (1,2)$$ and $$\sigma^{-1} = (1,n,n-1,...,3,2)$$, and we note that given a transposition $$(k,k+1)$$, we have

$$
(k,k+1) = \sigma^{-(k-1)}\tau\sigma^{k-1}
$$

hence the set $$\langle\{(1,2),(1,2,\ldots,n)\}\rangle$$ contains all elements of $$\langle\{(1,2),(2,3),...,(n-1,n)\}\rangle$$, and thus by the previous item it must be equal to $$S_n$$.

$$\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\blacksquare$$

The symmetric group also has a pretty interesting structure when it comes to its action on itself by conjugation. If we consider a permutation $$\sigma,\sigma \in S_n$$, and look at the orbit of $$\sigma$$ w.r.t. conjugation by elements of $$S_n$$, i.e., the set

$$
\sigma^{S_n} = \{\sigma^\pi|\pi \in S_n\}
$$

which is often called the *conjugacy class* of $$\sigma$$ in $$S_n$$, and we can actually characterize this set in terms of $$\sigma$$. We know that $$\sigma$$ can be uniquely written as $$\sigma = \sigma_{1}\ldots\sigma_{k}$$, where the $$\sigma_{j}$$'s are disjoint cycles of length $$c_j$$, and we assume WLOG that $$c_1 \geq \ldots \geq c_k$$ and that $$c_1 + ... + c_k = n$$ -- that is, we add length $$1$$ cycles for each element fixed by $$\sigma$$ if needed. The tuple $$(c_1,...,c_k)$$ is called the *partition* of $$n$$ associated with $$\sigma$$, and note that since conjugating a given cycle by $$\pi$$ doesn't alter its length, it follows that $$\sigma^{\pi}$$ and $$\sigma$$ have the same partition w.r.t. $$n$$, and hence $$\sigma' \in \sigma^{S_n}$$ if, and only if, $$\sigma$$ and $$\sigma'$$ have the same partition, i.e., iff they both have cycles of same length when ordered in a non-increasing manner.

## The Alternating Group

The symmetric group has many subgroups in general, but a rather important one is the *alternating group* $$A_n$$. From the Proposition 1, we have a well-defined notion of parity of a permutation: we say that a permutation is *odd* if it can be decomposed as an odd number of transpositions, and *even* if it can be decomposed as an even number of transpositions. Equivalently, a permutation $$\sigma$$ is odd if $$\sigma(F) = -F$$ -- where $$F$$ is the polynomial defined in the proof of Proposition 1 --, and even if $$\sigma(F) = F$$. The set $$A_n$$ is then simply the set of all even permutations, which can be immediately verified to form a subgroup of $$S_n$$.

When considering the action of $$S_n$$ on the polynomial ring $$\mathbb{Q}[x_1,...,x_n]$$, we can look at the orbit of the polynomial $$F$$, which by the previous arguments contains only two elements: $$F$$ and $$-F$$. On the other hand, we note that the even permutations are precisely those that fix $$F$$, i.e., we can look at $$A_n$$ as the stabilizer of $$F$$ w.r.t. this action. By the Orbit-Stabilizer Theorem we thus obtain:

$$
|A_n| = \frac{|S_n|}{2} = \frac{n!}{2}
$$

This means that the index of $$A_n$$ as a subgroup of $$S_n$$ -- i.e., the size of the set $$\{A_n\sigma\mid\sigma \in S_n\}$$ -- is precisely two, and thus $$A_n$$ is a normal subgroup of $$S_n$$. Note that this also implies that $$A_n$$ is a maximal subgroup of $$S_n$$, since any group that properly contains it must have order between $$n!/2$$ and $$n!$$, and also be a divisor of $$n!$$, hence it must be the entire $$S_n$$ -- this is actually true for any subgroup of a finite group with prime index.

If $$\sigma = (i_1,...,i_k)$$ is a cycle of length $$k$$, we've observed before that $$\sigma$$ can be decomposed as a product of $$k-1$$ transpositions, hence $$\sigma \in A_n$$ if, and only if, $$k$$ is odd. Also, if $$n \geq 3$$, then $$A_n$$ is in fact generated by the cycles of length $$3$$. Indeed, if $$\sigma \in A_n$$, then $$\sigma$$ can be written as a product of an even number of transpositions, and since the product of two transpositions is always a product of cycles of length $$3$$, the claim follows.

We end this post with a description of the relationship between the conjugacy classes of $$S_n$$ and $$A_n$$. We are considering the action of $$S_n$$ on itself via conjugation, hence the centralizer of any element $$\sigma \in S_n$$ is given by:

$$
C_{S_n}(\sigma) = \{\pi \in S_n|\sigma^\pi = \sigma\}
$$

Now if $$C$$ is a conjugacy class in $$S_n$$, and if $$C \cap A_n \neq \emptyset$$, then $$C \subseteq A_n$$ since $$A_n$$ is normal. Thus the conjugacy classes of $$S_n$$ are either entirely contained in $$A_n$$ or disjoint from it. If $$C \subseteq A_n$$, again since $$A_n$$ is normal, then $$A_n$$ acts on $$C$$ via conjugation, and thus we can indeed partition $$C$$ as a disjoint union of conjugacy classes in $$A_n$$. This means that we can obtain the conjugacy classes of $$A_n$$ by studying the conjugacy classes of $$S_n$$, and the next result will give us a particularly useful way of doing this.

**Proposition 3:** Let $$C$$ be a conjugacy class of $$S_n$$ with corresponding partition $$(r_1,...,r_m)$$ such that $$C \subseteq A_n$$. Then the following are equivalent:

  1. The class $$C$$ is a union of two conjugacy classes of $$A_n$$;
  2. For every element $$c \in C$$, its centralizer $$C_{S_n}(c)$$ w.r.t. $$S_n$$ is contained in $$A_n$$;
  3. The numbers $$r_1,...,r_m$$ are all odd and distinct.

**Proof:**

(1 $$\Rightarrow$$ 2) We'll show this by contrapositive. Assume that $$c \in C$$ is an element such that $$H = C_{S_n}(c) \not\subseteq A_n$$, hence we obtain the following chain of subgroups:

$$
A_n \lneq A_nH \leq S_n
$$

and since $$A_n$$ is maximal, it follows that $$A_nH = S_n$$, thus

$$
|S_n| = \frac{|A_n||H|}{|A_n\cap H|} = \frac{|A_n||H|}{|C_{A_n}(c)|}
$$

since $$C_{A_n}(c) = H \cap A_n$$, and from the previous equation we obtain:

$$
|C_{A_n}(c)| = \frac{H}{2}
$$

Now, if we let $$C'$$ be the conjugacy class of w.r.t. $$A_n$$, and using the Orbit-Stabilizer theorem, we conclude that:

$$
|C||H| = 2|C'||C_{A_n}(c)|
$$

hence $$\vert C\vert = \vert C'\vert$$, implying that $$C$$ is a conjugacy class of $$A_n$$.

(2 $$\Rightarrow$$ 1) Noting that $$C_{A_n}(c) = C_{S_n}(c) \cap A_n$$, the hypothesis implies that $$C_{A_n}(c) = C_{S_n}(c)$$, hence by the Orbit-Stabilizer Theorem, any conjugacy class $$C_i$$ of $$c$$ in $$A_n$$ will satisfy:

$$
\frac{|A_n|}{|C_i|} = \frac{|S_n|}{|C|}
$$

thus $$\vert C_i\vert = \vert C\vert/2$$, and since the conjugacy classes are disjoint, this implies that $$C = C_1 \cup C_2$$, where $$C_1,C_2$$ are conjugacy classes of $$A_n$$.

(2 $$\Rightarrow$$ 3) Let $$\sigma \in C$$, and let 

$$
\sigma = \sigma_1\ldots\sigma_m
$$

be its decomposition into disjoint cycles. If there exists some even $$r_i$$, then the corresponding cycle $$\sigma_i$$ does not belong to $$A_n$$. On the other hand, note that

$$
\sigma^{\sigma_i^{-1}} = \sigma
$$

since the cycles are disjoint, hence $$\sigma_i^{-1} \in C_{S_n}(\sigma)$$, but $$\sigma_i^{-1} \not\in A_n$$, which contradicts item 2, thus all $$r_i$$'s must indeed be odd. Now if WLOG $$r_1 = r_2$$, then let

$$
\sigma_1 = (x_1,...,x_{r_1}),\sigma_2 = (y_1,...,y_{r_2})
$$

and define

$$
\sigma' = (x_1,y_1)(x_2,y_2)\ldots(x_{r_1},y_{r_2})
$$

and since $$r_1$$ is odd, it follows that $$\sigma' \not\in A_n$$. On the other hand, we have

$$
(\sigma_1\sigma_2)^{\sigma'} = \sigma_1\sigma_2
$$

thus $$\sigma' \in C_{S_n}(\sigma)$$, which again contradicts item 2, and so the $$r_i$$'s are all distinct.

(3 $$\Rightarrow$$ 2) Assume that all $$r_i$$'s are odd and distinct, and assume that $$\pi \in S_n$$ is an element of the centralizer of some $$\sigma \in C$$, i.e., $$\sigma^\pi = \sigma$$. Let 
$$
\sigma = \sigma_1\ldots\sigma_m
$$

be its decomposition into disjoint cycles. Since the cycles are all distinct, we have

$$
\sigma^\pi = \sigma_1^\pi\ldots\sigma_m^\pi
$$

hence $$\pi \in C_{S_n}(\sigma_i)$$ for all $$i$$. On the other hand, the centralizer of any cycle in $$S_n$$ is generated by the powers of the cycle together with other disjoint cycles. Since $$\pi$$ lies in the centralizer of each $$\sigma_i$$, this means that it is of the form:

$$
\pi = \sigma_1^{a_1}\ldots\sigma_m^{a_m}
$$

for some integers $$a_1,...,a_m$$, and hence $$\pi \in A_n$$, implying that $$C_{S_n}(\sigma) \leq A_n$$, as desired.

$$\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\blacksquare$$

From this result, we know now the following about the conjugacy classes of $$S_n$$ and $$A_n$$:

 * The conjugacy classes of $$S_n$$ are uniquely determined by the integer partitions of $$n$$, i.e., for every tuple $$(r_1,...,r_k)$$, where $$r_1 + ... + r_k = n$$ are integers, and $$r_1 \geq ... \geq r_k$$, we obtain a unique conjugacy class of $$S_n$$, and these are all conjugacy classes.
 * If we start with some conjugacy class $$C$$ of $$S_n$$, then either $$C \subseteq A_n$$ or $$C \cap A_n = \emptyset$$.
 * If $$C \subseteq A_n$$, one of two possible scenarios may happen: if the centralizer of any element of $$C$$ w.r.t. $$S_n$$ is contained in $$A_n$$, then $$C$$ is the disjoint union of two conjugacy classes in $$A_n$$, otherwise $$C$$ is itself a conjugacy class in $$A_n$$.

These facts will be quite useful in proving that $$A_n$$ is simple when $$n \geq 5$$, and this in turn will lead us to conclude that $$S_n$$ is unsolvable, again when $$n \geq 5$$.




