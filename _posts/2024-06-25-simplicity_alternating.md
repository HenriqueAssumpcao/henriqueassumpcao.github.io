---
layout: distill
title: simplicity of the alternating group
date: 2024-06-25
description: proof that the alternating group is simple on 5 or more elements, and some interesting consequences
tags: 
categories: math group-theory
giscus_comments: false
related_posts: false
related_publications: 

toc:
  - name: "Transitive groups"
  - name: "Conjugacy classes and simplicity"
  - name: "Simplicity and solvability"


---
This post has a few objectives: prove that the alternating group $$A_n$$ is simple, and then conclude that $$S_n$$ is not solvable, both for when $$n \geq 5$$. In order to do this, we'll first discuss some facts about $$2$$-transitive groups, and then see a few examples when $$n < 5$$. After this post, I'll hopefully start to talk about some basic results of Galois Theory (as soon as I figure out a good way of plotting tikzcd diagrams on this blog).

## Transitive groups
If $$G$$ is a group that acts on a set $$X$$, i.e., if there is a homomorphism from $$G$$ to $$\text{Sym}(X)$$, then we say that $$G$$ acts transitively on $$X$$ if for every $$\alpha,\beta \in X$$, there exists some $$g \in G$$ such that $$\alpha g = \beta$$. In other words, for every element $$\alpha \in G$$, its orbit $$\alpha G$$ is the entire set $$X$$. A group is said to be $$2$$-transitive on $$X$$ if, for every $$\alpha,\beta,\gamma,\delta \in X,\alpha \neq \beta, \gamma \neq \delta$$, there exists some $$g \in G$$ such that

$$
(\alpha,\beta)g = (\alpha g,\beta g) = (\gamma,\delta)
$$

Equivalently, a group is $$2$$-transitive on $$X$$ if it is transitive on the set of distinct ordered pairs $$\{(\alpha,\beta)\vert \alpha,\beta \in X,\alpha \neq \beta\}$$. From this definition, it follows that any $$2$$-transitive group is also transitive, and we can also prove the following characterization.

**Proposition 1:** A group $$G$$ is $$2$$-transitive on $$X$$ if, and only if, the stabilizer $$G_\alpha$$ of any element $$\alpha \in X$$ acts transitively on $$X\setminus\{\alpha\}$$.

**Proof:** First, assume that $$G$$ is $$2$$-transitive, and let $$G_\alpha$$ be the stabilizer of some $$\alpha \in G$$. By definition, we know that for any $$\beta,\delta \in X\setminus\{\alpha\}$$, there exists some $$g \in G$$ such that

$$
(\alpha,\beta)g = (\alpha,\delta)
$$

hence $$\beta g = \delta$$ and $$\alpha g = \alpha$$, and thus $$g \in G_\alpha$$, implying that this stabilizer indeed acts transitively on $$X\setminus\{\alpha\}$$.

Now if $$\alpha,\beta,\gamma,\delta \in X$$, with $$\alpha \neq \beta, \gamma \neq \delta$$, we can find elements $$g_1,g_2 \in G$$ such that

$$
\begin{split}
(\alpha,\beta)g_1 &= (\alpha,\delta)\\
(\alpha,\delta)g_2 &= (\gamma,\delta)
\end{split}
$$

by simply using the transitivity of $$G_\alpha,G_\delta$$, hence

$$
(\alpha,\beta)g_1g_2 = (\gamma,\delta)
$$

and thus $$G$$ is $$2$$-transitive, as desired.

$$\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\blacksquare$$

Using this result, we can prove an auxiliary lemma that will be quite useful.

**Lemma 1:** If $$G \neq 1$$ is a $$2$$-transitive group acting on $$X$$, then the stabilizer $$G_\alpha$$ of any element $$\alpha \in X$$ is a maximal subgroup of $$G$$.

**Proof:** Let $$g \in G \setminus G_\alpha$$ be an element of the group that is not in the stabilizer, i.e., $$\alpha g = \beta \neq \alpha$$, and let $$H = \langle G_\alpha,g \rangle$$. We will show that $$H = G$$, and since this will be true for any $$g \in G \setminus G_\alpha$$, it will follow that $$G_\alpha$$ is maximal. We know that the lateral classes of $$G_\alpha$$ partition $$G$$, hence let $$h \in G$$ be an element of the group, and consider the lateral class $$G_\alpha h$$. Let $$\beta h = \gamma$$, and note that since $$G_\alpha$$ is transitive on $$X \setminus \{\alpha\}$$, we can find some $$g_\gamma \in G_\alpha$$ s.t. $$\beta g_\gamma = \gamma$$, hence $$\alpha gg_\gamma = \beta$$. We claim that $$G_\alpha gg_\gamma = G_\alpha h$$. Indeed, note that

$$
\begin{split}
(fgg_\gamma h^{-1})h &\in G_\alpha h\\
(fhg_\gamma^{-1}g^{-1})gg_\gamma &\in G_\alpha gg_\gamma
\end{split}
$$

for any $$f \in G_\alpha$$, and thus the claim follows. This shows that any lateral class of $$G_\alpha$$ is contained in $$H$$, implying that $$G \subseteq H$$, and hence $$H = G$$, as desired.

$$\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\blacksquare$$

We can use the previous Lemma to show that $$S_n$$ is a maximal subgroup of $$S_{n+1}$$, and similarly that $$A_n$$ is a maximal subgroup of $$A_{n+1}$$. First, note that $$S_n$$ acts transitively on $$\{1,...,n\}$$, since we can take any element $$i$$ to some other element $$j$$ via the transposition $$(i,j)$$, and similarly $$A_n$$ is also transitive since we can take $$i$$ to $$j$$ via $$(i,k)(k,j)$$. Now if we consider any fixed element $$i \in \{1,...,n+1\}$$, then the stabilizer of this element in $$S_{n+1}$$ is a copy of $$S_n$$, hence it is transitive on $$\{1,...,n+1\} \setminus \{i\}$$, implying that $$S_{n+1}$$ is $$2$$-transitive, and thus $$S_n \leq S_{n+1}$$ is maximal. A similar argument shows that $$A_n$$ is maximal in $$A_{n+1}$$.

## Conjugacy classes and simplicity
We are now ready to prove that $$A_n$$ is simple if $$n \geq 5$$. The strategy will be as follows: we start with showing that $$A_5$$ is simple, by analyzing its conjugacy classes and finding a contradiction with the existence of a normal proper non-trivial subgroup. We then proceed inductively on $$n$$, and use the previous results about transitivity to complete the proof.

First, [recall from the previous post](https://henriqueassumpcao.github.io/blog/2024/symmetric_group/) that the conjugacy classes of $$S_n$$ are completely determined by the integer partitions of $$n$$, and in turn we can completely determine the conjugacy classes of $$A_n$$ by analyzing the centralizers of these classes. Below is a table of the conjugacy classes of $$S_5$$, where each row is indexed by the respective partition, $$x$$ denotes a representative of the conjugacy class, $$C_{S_5}(x)$$ denotes its centralizer, and $$x^{S_5}$$ denotes its orbit.

| Partition | $$x$$ |$$C_{S_5}(x)$$ | $$\vert x^{S_5}\vert$$ |$$\vert C_{S_5}(x) \vert$$ |
| :----------- | :------------: | :------------: | ------------: | ------------: |
| $$(1,1,1,1,1)$$      | $$1$$       |$$S_5$$ | $$1$$       | $$120$$ |
| $$(2,1,1,1)$$       | $$(1,2)$$       |$$\langle (1,2),(3,4),(3,4,5)\rangle$$ | $$10$$       | $$12$$ |
| $$(2,2,1)$$       | $$(1,2)(3,4)$$       |$$\langle (1,2),(1,3,2,4)\rangle$$ | $$15$$       | $$8$$ |
| $$(3,1,1)$$       | $$(1,2,3)$$       |$$\langle (1,2,3),(4,5)\rangle$$ | $$20$$       | $$6$$|
| $$(3,2)$$       | $$(1,2,3)(4,5)$$       |$$\langle (1,2,3),(4,5)\rangle$$ | $$20$$       | $$6$$|
| $$(4,1)$$       | $$(1,2,3,4)$$       |$$\langle (1,2,3,4)\rangle$$ | $$30$$       | $$4$$|
| $$(5)$$       | $$(1,2,3,4,5)$$       |$$\langle (1,2,3,4,5)\rangle$$ | $$24$$       | $$5$$|

Now recall that $$A_5$$ contains only even permutations, hence the conjugacy classes corresponding to the partitions $$(2,1,1,1),(3,2),(4,1)$$ will have empty intersections with $$A_5$$. The centralizer of the class corresponding to $$(2,2,1)$$ is not contained in $$A_5$$, and thus the conjugacy class is also a class in $$A_5$$, and the same is true for $$(3,1,1)$$. The centralizer of $$(5)$$ on the other hand is contained in $$A_5$$, thus the class splits into two disjoint conjugacy classes in $$A_5$$. With these observations, we obtain the following table of the conjugacy classes of $$A_5$$:

| $$x$$ |$$C_{A_5}(x)$$ | $$\vert x^{A_5}\vert$$ |$$\vert C_{A_5}(x) \vert$$ |
| :------------: | :------------: | ------------: | ------------: |
| $$1$$       |$$A_5$$ | $$1$$       | $$60$$ |
| $$(1,2)(3,4)$$       |$$\langle (1,2)(3,4),(1,3)(2,4)\rangle$$ | $$15$$       | $$4$$ |
| $$(1,2,3)$$       |$$\langle (1,2,3)\rangle$$ | $$20$$       | $$3$$|
| $$(1,2,3,4,5)$$       |$$\langle (1,2,3,4,5)\rangle$$ | $$12$$       | $$5$$|
| $$(1,2,3,5,4)$$       |$$\langle (1,2,3,5,4)\rangle$$ | $$12$$       | $$5$$|

Now assume that $$N \trianglelefteq A_5$$ is a normal subgroup, thus it must be the disjoint union of conjugacy classes in $$A_5$$, hence $$\vert N \vert \mid 60$$, and on the other hand there must be integers $$x_1,x_2,x_3$$ such that

$$
\vert N \vert = 15x_1 + 20x_2 + 12x_3
$$

where $$x_1,x_2 \in \{0,1\},x_3 \in \{0,1,2\}$$ correspond to the possible choices of conjugacy classes. These two facts together with a simple inspection show that either $$N = A_5$$ or $$N = 1$$, and thus $$A_5$$ is indeed simple. This will serve as the base case of our induction in the following theorem.

**Theorem 1:** The alternating group $$A_n$$ is simple for $$n \geq 5$$.

**Proof:** We proceed via induction on $$n$$. The base case of $$n = 5$$ was already verified, so assume that the claim holds for values less than $$n+1$$ and consider $$A_{n+1}$$. Let $$i \in \{1,2,...,n+1\}$$, and note that the stabilizer $$G_i$$ is isomorphic to $$A_n$$, and since $$A_{n+1}$$ is transitive, it follows that all $$G_i$$'s are conjugate.

 Let $$N \trianglelefteq A_{n+1}$$ be a normal subgroup, and consider $$N \cap G_1 \trianglelefteq G_1$$, and since $$G_1$$ is isomorphic to $$A_n$$, we know by the inductive hypothesis that either $$N \cap G_1 = G_1$$ or $$N \cap G_1 = 1$$. If $$N \cap G_1 = G_1$$, since the $$G_i$$'s are conjugate and $$N$$ is normal, it follows that $$G_i \subseteq N$$ for all $$i$$. However, note that $$N$$ is normal but $$G_1$$ isn't, hence $$N$$ properly contains each $$G_1$$, and since each $$G_i$$ is a maximal subgroup of $$A_{n+1}$$, this implies that $$N = A_{n+1}$$. Now assume that for all $$i$$, we have $$N \cap G_i = 1$$, and assume that $$N \neq 1$$. Since $$G_1$$ is maximal, it follows that $$NG_1 = A_{n+1}$$, hence

$$
\vert NG_1 \vert = \frac{\vert N \vert\vert G_1 \vert}{\vert N \cap G_1 \vert} = \frac{\vert N \vert}{\vert A_n\vert}
$$

hence $$\vert N \vert = n+1$$. Let $$\sigma \in N \setminus\{1\}$$, and write its decomposition as a product of disjoint cycles as follows:

$$
\sigma = \sigma_1\ldots\sigma_k
$$

where each cycle has length $$c_i$$, with $$c_1 \geq \ldots \geq c_k$$. If $$c_1 \geq 3$$, we may assume WLOG that $$\sigma_1 = (1,2,3,...,m)$$, for some $$m \geq 3$$, thus if we take $$\rho = (3,4,5)$$, we get that $$\sigma^\rho\sigma^{-1}$$ is an element of $$G_1 \cap N \setminus \{1\}$$, which is a contradiction. If $$c_1 = 2$$, then we may assume WLOG that $$\sigma_1 = (1,2)(3,4)$$, and thus if we take $$\rho = (4,5,6)$$ we again get that $$\sigma^\rho\sigma^{-1}$$ is an element of $$G_1 \cap N \setminus \{1\}$$, which is also a contradiction. This implies that $$A_{n+1}$$ is simple, as desired.

$$\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\blacksquare$$

## Simplicity and solvability

The simplicity of $$A_n$$ for $$n \geq 5$$ also implies that $$A_n$$ is the only proper non-trivial normal subgroup of $$S_n$$ in these cases. 

**Theorem 2:** If $$n \geq 5$$, then $$A_n$$ is the only proper non-trivial normal subgroup of $$S_n$$.

**Proof:** Suppose that $$N \trianglelefteq S_n$$ is a proper normal subgroup of $$S_n$$ that is not equal to $$1$$. Since $$A_n$$ is also a normal subgroup, it follows that $$A_n \cap N$$ is also normal and proper in $$S_n$$. If $$A_n \cap N = 1$$, then $$N$$ must be composed only of odd permutations, however the product of two odd permutations is even, and thus $$A_n \cap N \neq 1$$, i.e., $$A_n \cap N$$ is a non-trivial normal subgroup of both $$A_n$$ and $$N$$, but since $$A_n$$ is simple if $$n \geq 5$$, it follows that $$A_n \cap N = A_n$$, and thus $$A_n \subseteq N$$. On the other hand, $$A_n$$ is a maximal subgroup of $$S_n$$, thus it follows that $$N = A_n$$, as desired.

$$\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\blacksquare$$

Now it is actually fairly straightforward to check that $$S_n$$ is not solvable for $$n \geq 5$$. Recall that a group $$G$$ is solvable iff there exists some normal series

$$
G = G_0 \trianglerighteq G_1 \ldots \trianglerighteq G_k = 1
$$

where each $$G_i \trianglelefteq G$$, and $$G_i/G_{i+1}$$ is abelian. If $$n \geq 5$$, since neither $$S_n$$ nor $$A_n$$ are abelian, and since the only normal subgroup of $$S_n$$ is $$A_n$$, any normal series is of the form

$$
S_n \trianglerighteq A_n \trianglerighteq 1
$$

hence the series does not satisfy the solvability conditions, implying that $$S_n$$ is not solvable if $$n \geq 5$$.

On the other hand, the groups $$S_1,S_2,S_3,S_4$$ are all solvable. This is immediately true for $$S_1$$ and $$S_2$$, as they are abelian. The solvability of $$S_3$$ follows from a more general fact: the dihedral group $$D_n$$ is actually solvable for all $$n$$, since if we consider the subgroup of all rotations $$C_n$$, it has order $$n$$, and since $$D_n$$ has order $$2n$$ it follows that the index of $$C_n$$ is two, and thus it is normal, hence the series

$$
D_n \trianglerighteq C_n \trianglerighteq 1
$$

is normal, and $$D_n/C_n$$ is abelian as it is a group of order two, and since $$S_3 = D_3$$, the result follows. Now in order to see that $$S_4$$ is solvable, it will require some more effort. We first consider the set 

$$
\begin{split}
X &= \{X_1,X_2,X_3\},\\
X_1 &= \{\{1,2\},\{3,4\}\},\\
X_2 &= \{\{1,3\},\{2,4\}\},\\
X_3 &= \{\{1,4\},\{2,3\}\}
\end{split}
$$

and note that $$S_4$$ acts on $$X$$ as follows by permuting the elements of the sets, e.g., 

$$
\begin{split}
\{1,2\}(1,2,3) &= \{1(1,2,3),2(1,2,3)\} = \{2,3\}\\
X_1(1,2,3) &= X_3
\end{split}
$$

Since an action is nothing more than an homomorphism from the group to the group of symmetries of the set, it follows that we obtain an homomorphism $$\varphi:S_4 \mapsto S_3$$, since $$\text{Sym}(X) = S_3$$. It follows by a simple computation that

$$
\text{ker}(\varphi) = \{1,(1,2)(3,4),(1,3)(2,4),(1,4)(2,3)\}
$$

and the set $$\text{ker}(\varphi)$$ is often called the *Klein group* $$K_4$$ on $$4$$ elements. From this, we have that $$S_4/K_4$$ is isomorphic to some subgroup of $$S_3$$, but on the other hand $$S_4/K_4$$ has order $$6$$, thus

$$
S_4/K_4 \cong S_3
$$

Now note that $$K_4$$ has $$4$$ elements, and thus it is abelian, and in particular it is solvable, and since it is the kernel of an homomorphism it follows that $$K_4$$ is a normal solvable subgroup of $$S_4$$. [Recall](https://henriqueassumpcao.github.io/blog/2024/solvable_groups/) that if $$N$$ is a normal solvable subgroup of $$G$$, and if $$G/N$$ is solvable, then $$G$$ is also solvable, thus this implies that $$S_4$$ is solvable.





