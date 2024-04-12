---
layout: distill
title: completion of a metric space
date: 2024-03-28
description: how to complete a metric space
tags: 
categories: math topology
giscus_comments: false
related_posts: false
related_publications: 

toc:
  - name: "Some basic concepts"
  - name: "The space of Cauchy sequences"
  - name: "Constructing an Isometry"
  - name: "The main result"
  - name: "Comments"


---
I'm taking a course in Topology this semester, and I came across this interesting exercise about completions of metric spaces. We will show that any metric space can be extended to a complete metric space, i.e., a space where all Cauchy sequences converge.

## Some basic concepts

Let $$(E,d)$$ be a metric space, i.e., a set with a function $$d:E\times E\mapsto \mathbb{R}$$ such that

(i) $$d(x,y)= 0$$ iff $$x =y$$ 

(ii) $$d(x,y) = d(y,x)$$ (Symmetry)

(iii) $$d(x,y) \leq d(x,z) + d(z,x)$$ (Triangle Inequality)

We'll denote a sequence of elements of $$E$$ by $$(x_n) \subset E$$, and we recall that a sequence is Cauchy if for every $$\epsilon > 0$$, there exists some natural $$K$$ such that

$$ i,j > K \Rightarrow d(x_i,x_j) < \epsilon$$

It is immediate that any convergent sequence in $$E$$ is Cauchy, however the converse is not true in general. Cauchy sequences are sequences that really want to converge to something, but that something may not be in $$E$$, e.g., the sequence $$((1+1/n)^n) \subset \mathbb{Q}$$ is Cauchy, however we know that it converges to Euler's constant $$e$$, which is irrational. Our goal here is to show that we can build a larger space where every Cauchy sequence converges to a point in that space, and in the case of $$\mathbb{Q}$$ this will yield one of the possible constructions for the real numbers.

Now recall that if $$(E_1,d_1),(E_2,d_2)$$ are metric spaces, a function $$f:E_1\mapsto E_2$$ is called an isometry if

$$\forall x,y \in E_1: d_1(x,y) = d_2(f(x),f(y))$$

Note that from this definition it follows that an isometry is always injective and continuous, more specifically it is Lipschitz continuous with constant 1. Sometimes isometries are also required to be bijective, but we will make no such requirement. The main point here is that an isometry is a distance-preserving injective map, and thus in some it preserves the metric structure of the domain in its image. Our goal is not only to construct a complete space from $$E$$, but do this in a way that guarantees that $$E$$ is contained in this larger space via an isometry.

## The space of Cauchy sequences
I think that the hardest part of this exercise is probably thinking about a good candidate for the space to complete $$E$$. We'll consider the following set

$$C[E] = \{(x_n) \subset E|(x_n)\text{  is Cauchy}\}$$

We'll equip this set with the following function

$$D((x_n),(y_n)) = \lim_{n\rightarrow \infty}d(x_n,y_n)$$

After seeing this construction, it is not hard to believe that something related to this set will be our completion, however thinking about this construction in the first place is something that I found to be quite challenging. The intuition here is that $$D$$ is measuring how close the sequences are getting as $$n$$ gets arbitrarily large. We first note that $$D$$ is almost a metric, since it follows by definition that $$D$$ is symmetric and respects the triangle inequality. However, it is not true that if $$D((x_n),(y_n)) = 0$$ then $$(x_n),(y_n)$$ are the same, since any pair of distinct sequences that "want" to converge to the same point will have distance zero. For example, we can consider $$C[\mathbb{Q}]$$ and note that the sequences $$(1/n)$$ and $$(-1/n)$$ both converge to zero, and thus

$$\lim_{n\rightarrow \infty}|1/n-1/n| = 0$$

however they are clearly distinct. Formally, $$D$$ is a pseudo-metric, and one classical basic exercise in analysis shows that any space with a pseudo-metric can be naturally transformed into a metric space. In order for us to do that, we define the equivalence relation $$\sim$$ on $$C[E]$$ given by

 $$(x_n) \sim (y_n) \Longleftrightarrow D((x_n),(y_n)) = 0$$

Thus, we can consider the space

$$\overline{E} := C[E]/\sim = \{[(x_n)]|(x_n) \in C[E]\}$$

where $$[(x_n)]$$ denotes the equivalence class of $$(x_n)$$ w.r.t. $$\sim$$. Intuitively, this means that we've aggregated all Cauchy sequences that "want" to converge to the same point into a single set, and now we are treating this set as a point in itself. From now on, we'll denote $$(x_n) \in C[E]$$ by $$\overline{x}$$, and we note that the function

$$\overline{D}([\overline{x}],[\overline{y}]) := D(\overline{x},\overline{y}),\overline{x} \in [\overline{x}],\overline{y} \in [\overline{y}]$$

is well-defined (follows from the triangle inequality), i.e., we can evaluate the distance between $$[\overline{x}]$$ and $$[\overline{y}]$$ by evaluating the distance between any representative of the respective equivalence classes w.r.t. $$D$$.

## Constructing an Isometry

Now we'll explicitly build an isometry between $$E$$ and $$\overline{E}$$. Consider the following map

$$
\begin{split}
\iota:E&\mapsto\overline{E}\\
\iota(x) &= [(x,x,...,x,...)]
\end{split}
$$

That is, we map each point $$x \in E$$ to the equivalence class of the constant sequence with each element equal to $$x$$. Such sequence is clerly Cauchy, and it converges to $$x$$, thus $$\iota(x)$$ is the set of all sequences that converge to $$x$$. Now, we note that

$$
\begin{split}
\overline{D}(\iota(x),\iota(y)) &= D((x,x,...,x,...),(y,y,...,y,...))\\
&= \lim_{n\rightarrow \infty}d(x,y) = d(x,y)
\end{split}
$$

hence $$\iota$$ is indeed an isometry, i.e., it is injective, continuous, and preserves the distances in $$E$$. This means that, in a very concrete and well-defined sense, $$E$$ is contained in $$\overline{E}$$, and so our construction so far makes some sense in the context of metric spaces. We now prove an additional important result.

**Lemma:** $$\iota(E)$$ is a dense subset of $$\overline{E}$$. In other words, every point on $$\overline{E}$$ can be approximated by a sequence of points in $$\iota(E)$$.

**Proof:** Let $$[\overline{x}] \in \overline{E}$$ be an element of $$\overline{E}$$, and note that by definition $$\overline{x}$$ is a Cauchy sequence in $$E$$, hence for every $$N \in \mathbb{N}$$, we can find some $$K_N \in \mathbb{N}$$ such that

$$i,j \geq K_N \Rightarrow d(x_i,x_j) < 1/2N$$

In particular, we have that $$d(x_i,x_{K_N}) < 1/2N$$ for every $$i > K$$, which yields

$$\lim_{n\rightarrow \infty} d(x_n,x_{K_N}) \leq 1/2N < 1/N \Rightarrow \overline{D}([\overline{x}],\iota(x_{K_N})) < 1/N$$

Thus, we consider the sequence $$(\iota(x_{N_K}))_{K \in \mathbb{N}} \subset \overline{E}$$. If we fix $$\epsilon > 0$$, we can always find some natural $$N$$ such that $$1/N < \epsilon$$, and so

$$i > K_N \Rightarrow \overline{D}([\overline{x}],\iota(x_{K_N})) < 1/N < \epsilon$$

which shows that $$(\iota(x_{N_K}))$$ converges to $$[\overline{x}]$$ in $$\overline{E}$$, implying that $$\iota(E)$$ is dense in $$\overline{E}$$.

$$\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\blacksquare$$ 

This means that, not only is $$E$$ contained in $$\overline{E}$$ in a way that preserves distances, but also that we can approximate any element of $$\overline{E}$$ by some sequence of elements of $$E$$.

## The main result

We are now ready to show that $$\overline{E}$$ is complete, i.e., if we have a Cauchy sequence $$([\overline{x}^{(k)}])_{k \in \mathbb{N}}$$ in $$\overline{E}$$, then it must converge to some $$[\overline{x}]$$ in $$\overline{E}$$. Concretely, this means that as $$k$$ gets arbitrarily large, the point to which the Cauchy sequences in $$[\overline{x}^{(k)}]$$ "want" to converge to gets arbitrarily close to the point that $$[\overline{x}]$$ "wants" to converge to.

**Theorem:** If $$(E,d)$$ is a metric space, than the space $$(\overline{E},\overline{D})$$ is a complete metric space. Moreover, there is an isometry $$\iota$$ between $$E$$ and $$\overline{E}$$ such that $$\iota(E)$$ is dense in $$\overline{E}$$.

**Proof:** The trickiest part of this proof is finding a candidate for the convergent point of the sequence $$([\overline{x}^{(k)}])$$. First, we note that $$([\overline{x}^{(k)}])$$ converges to $$[\overline{x}]$$ iff $$(\overline{x}^{(k)})$$ converges to $$\overline{x}$$ w.r.t. $$D$$, for some elements $$\overline{x}^{(k)},\overline{x}$$ of the respective equivalence classes, thus we only need to construct a Cauchy sequence $$\overline{x}$$ in $$E$$ such that for any $$\epsilon > 0$$ there exists some $$k \in \mathbb{N}$$ such that

$$i > k \Rightarrow \lim_{n\rightarrow \infty} d(x^{(i)}_n,x_n) < \epsilon$$

where $$\overline{x}^{(i)} = (x_n^{(i)})$$. In order to do this, we first use that each $$\overline{x}^{(k)}$$ is itself a Cauchy sequence, i.e., for every $$k \in \mathbb{N}$$, we can find some $$n_k \in \mathbb{N}$$ such that

$$i,j \geq n_k \Rightarrow d(x^{(k)}_i,x^{(k)}_j) < 1/k$$

hence our candidate will be the sequence

$$\overline{x} = (x^{(1)}_{n_1},x^{(2)}_{n_2},...,x^{(k)}_{n_k},...) =  (x^{(k)}_{n_k})_{k \in \mathbb{N}}$$
 
We now need to show that this sequence is Cauchy, and also that $$\overline{x}^{(k)}$$ converges to it. First, let $$\delta > 0$$, and thus we can find some $$k_1 \in \mathbb{N}$$ such that $$1/k_1 < \delta/6$$, and we can also find some $$k_2 \in \mathbb{N}$$ such that

$$i,j > k_2 \Rightarrow D(\overline{x}^{(i)},\overline{x}^{(j)}) = \lim_{n\rightarrow \infty} d(x^{(i)}_n,x^{(j)}_n) < \delta/6$$

since $$(\overline{x}^{(k)})$$ is also a Cauchy sequence. Now let $$k =\max(k_1,k_2)$$, thus if $$i,j > k$$ we have

$$d(x^{(i)}_{n_i},x^{(j)}_{n_j}) \leq d(x^{(i)}_{n_i},x^{(i)}_{n}) + d(x^{(i)}_{n},x^{(j)}_{n}) + d(x^{(j)}_{n},x^{(j)}_{n_j})$$

thus if we take $$n > \max(n_i,n_j)$$, we get that 

$$
\begin{split}
d(x^{(i)}_{n_i},x^{(i)}_{n}) &< 1/i < 1/k < \delta/6\\
d(x^{(j)}_{n_j},x^{(j)}_{n}) &< 1/j < 1/k < \delta/6\\
\end{split}
$$

Hence if $$n > \max(n_i,n_j)$$, this implies that

$$
\begin{split}
d(x^{(i)}_{n_i},x^{(j)}_{n_j}) &< \delta/3 + d(x^{(i)}_{n},x^{(j)}_{n})\\
\Rightarrow d(x^{(i)}_{n_i},x^{(j)}_{n_j}) &= \lim_{n\rightarrow \infty} d(x^{(i)}_{n_i},x^{(j)}_{n_j}) \leq \delta/3 + \lim_{n\rightarrow \infty}d(x^{(i)}_{n},x^{(j)}_{n})\\
&\leq \delta/3 + \delta/6 < \delta
\end{split}
$$

and since $$\delta$$ was arbitrary, this shows that $$\overline{x}$$ is Cauchy. Now fix $$\epsilon > 0$$, and let $$k_1 \in \mathbb{N}$$ be such that $$1/k_1 < \epsilon/4$$, thus 

$$n > n_{k_1} \Rightarrow d(x^{(k_1)}_n,x^{(k_1)}_{n_{k_1}}) < 1/k_1 < \epsilon/4$$

Since $$\overline{x}$$ is itself Cauchy, there exists some $$k_2 \in \mathbb{N}$$ such that

$$i > k_2 \Rightarrow d(x^{(i)}_{n_i},x^{(k_2)}_{n_{k_2}}) < \epsilon/4$$

Let $$k = \max(k_1,k_2)$$, thus we obtain

$$
\begin{split}
n > n_k &\Rightarrow d(x^{(k)}_n,x^{(k)}_{n_k}) < \epsilon/4\\
i > k &\Rightarrow d(x^{(i)}_{n_i},x^{(k)}_{n_k}) < \epsilon/4
\end{split}
$$

Combining these two inequalities, if $$j > \max(k,n_k)$$, we get that

$$
\begin{split}
d(x^{(k)}_j,x^{(j)}_{n_j}) &\leq d(x^{(k)}_j,x^{(k)}_{n_k}) + d(x^{(j)}_{n_j},x^{(k)}_{n_k}) < \epsilon/2\\
\Rightarrow D(\overline{x}^{(k)},\overline{x}) &= \lim_{j \rightarrow \infty} d(x^{(k)}_j,x^{(j)}_{n_j}) \leq \epsilon/2 < \epsilon
\end{split}
$$

and thus we can conclude that $$([\overline{x}^{(k)}])$$ converges to $$[\overline{x}]$$, i.e., $$\overline{E}$$ is complete.

$$\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\blacksquare$$

## Comments
This result shows that we can indeed build a new space from $$E$$ that is a complete metric space that "contains" $$E$$ in a meaningful way, i.e., there is a dense subset of this new space that is isometric to $$E$$. It is also easy to check that $$\iota(E) = \overline{E}$$ iff $$E$$ is complete, and through some extra work it can also be shown that $$\overline{E}$$ is unique up to isometry, i.e., any other space $$\overline{E}'$$ that contains a dense subset that is isometric to $$E$$ is itself isometric to $$\overline{E}$$. 

This gives an interesting way of thinking about the real numbers: an irrational number such as $$\pi$$ can be viewed as the set of sequences of rational numbers that are getting arbitrarily close together and converging to something that isn't rational, namely $$\pi$$ itself. From the "perspective" of the rational numbers, the real numbers are nothing more than bundles of sequences that are getting really close together and "wanting" to converge to something. Sometimes this something turns out to be a rational number, but sometimes it turns out not to be, and when this is the case we simply identify this "thing" that isn't rational with the set of sequences that are getting arbitrarily close to it.