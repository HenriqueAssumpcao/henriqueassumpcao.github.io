---
layout: distill
title: free modules over principal ideal domains
date: 2023-11-25
description: another interesting result from the course on rings and modules
tags: 
categories: rings-and-modules
giscus_comments: false
related_posts: false
related_publications: 

toc:
  - name: "Lemma 1: A characterization of split exact sequences"
  - name: "Lemma 2: Sufficient condition for split exact sequence"
  - name: "The main result"
  - name: "Comments"


---
We are interested in showing that free modules over principal ideal domains (PIDs) with finite basis behave in a similar fashion to vector spaces over fields: we wish to show that every submodule will also be free with a smaller basis. For this, we first tackle the notion of exact sequences of modules. Throughout this proof, $$R$$ will denote a commutative ring with unity, and $$D$$ will denote a PID. Consider the following diagram:

$$0 \mapsto M_1 \mapsto^f M_2 \mapsto^g M_3 \mapsto 0$$

where $$M_1,M_2,M_3$$ are $$R$$-modules, and $$f,g$$ are $$R$$-homomorphisms. We call this sequence exact if $$\ker(g)=\text{Im}(f)$$. Given an exact sequence, we say that it is split exact if there exists some $$N\leq M_2: M_2 = \ker(g)\oplus N$$, which also implies that $$M_2 = \text{Im}(f)\oplus N$$. We will first prove two results related to split exact sequences, and then proceed to prove our main result.

## Lemma 1: A characterization of split exact sequences
**Lemma 1:** Given an exact sequence of the form given in the previous diagram, TFAE:
  * The sequence is split exact.
  * There exists $$\psi \in \text{Hom}_{R}(M_2,M_1)$$ such that $$\psi \circ f = \text{id}_{M1}$$.
  * There exists $$\phi \in \text{Hom}_{R}(M_3,M_2)$$ such that $$g \circ \phi = \text{id}_{M3}$$.

  Under these conditions, we have that $$M_2 \cong M_1 \oplus M_3$$.

**Proof:**

**(i)**$$\Rightarrow$$**(ii)** Note that by the definition of our sequence, $$f$$ is injective and $$g$$ is surjective. Assume that $$M_2 = \text{Im}(f)\oplus N$$, thus given any $$m_2 \in M_2$$, we can write it uniquely as $$m_2 = f(m_1) + y$$, where $$m_1 \in M_1,y \in N$$, and note that $$m_1$$ must be unique since $$f$$ is injective. Thus, define $$\psi$$ such that $$\psi(m_2) = \psi(f(m_1)+y)=m_1$$. This function is well defined due to the above remarks, and note that the restriction of $$\psi$$ onto $$\text{Im}(f)$$ is a bijection, and also that $$\psi$$ is an $$R$$-homomorphism: given $$m_2,m_2' \in M_2,\alpha \in R:$$

$$m_2+m_2' = f(m_1)+y+f(m_1')+y' = f(m_1+m_1') + y+y' \Rightarrow \psi(m_2+m_2')=\psi(m_2)+\psi(m_2')$$

and also that $$\psi(\alpha m_2) = \alpha \psi(m_2)$$. Given any $$m_1 \in M_1$$, note that $$\psi(f(m_1)) = m_1$$ by definition, thus $$\psi \circ f = \text{id}_{M1}$$.

**(ii)**$$\Rightarrow$$**(i)** Now assume the existence of a function $$\psi$$ as described in (ii). Let $$h:M_2 \mapsto M_2, h = f \circ \psi$$. It is clearly an $$R$$-endomorphism on $$M_2$$, and note that $$\text{Im}(h) \subset \text{Im}(f)$$ by definition. On the other hand, given any $$m_1 \in M_1$$, we have that $$f(m_1) = f(\psi(f(m_1))) = h(f(m_1)) \in \text{Im}(h)$$, thus $$\text{Im}(h) = \text{Im}(f)$$. Also, note that $$h$$ is idempotent: $$f \circ \psi \circ f \circ \psi = f\circ \psi$$, and so we can write $$M_2 = \text{Im}(h)\oplus\ker(h)=\text{Im}(f)\oplus\ker(n)$$, and so the sequence is split exact.

**(i)**$$\Rightarrow$$**(iii)** Assume that $$M_2 = \ker(g)\oplus N$$, and note that since $$g$$ is surjective, given any $$m_3 \in M_3$$, we can write it as $$m_3 = g(m_2)$$, where $$m_2 \in M_2$$. On the other hand, we can write each $$m_2$$ uniquely as $$m_2 = x + y$$, where $$x \in \ker(g),y \in N$$, thus $$m_3 = g(y)$$. We claim that this $$y$$ is unique. Indeed, if there were another $$y' \in N$$ s.t. $$m_3 = g(y')$$, this would imply that $$g(y-y') = 0$$, and so $$y-y' \in \ker(g)\cap N \Rightarrow y = y'$$, since $$M_2$$ is a direct sum. Thus, define $$\phi$$ as $$\phi(m_3)=\phi(g(m_2))=\phi(g(y))=y$$. This function is well defined due to the above remarks, it is injective, and it follows that it is an $$R$$-homomorphism and that $$g(\phi(m_3))=g(y)=m_3$$, thus $$g \circ \phi = \text{id}_{M3}$$.

**(iii)**$$\Rightarrow$$**(i)** Assume the existence of a function $$\psi$$ as described in (iii). Let $$h:M_2 \mapsto M_2, h = \phi \circ g$$. It is clearly an $$R$$-endomorphism on $$M_2$$, and it is idempotent: $$\phi \circ g \circ \phi \circ g = \phi \circ g$$. Note that $$\ker(g) \subset \ker(h)$$, and if $$h(m_2) = 0$$ this implies that $$\phi(g(m_2)) = 0$$, however recall that $$\phi$$ is injective, and so $$g(m_2) = 0$$ thus $$m_2 \in \ker(g)$$, implying that $$\ker(g)=\ker(h)$$. We can then write $$M_2 = \text{Im}(h)\oplus\ker(h)=\text{Im}(h)\oplus\ker(g)$$, and so the sequence is split exact.

Now, assume that we have a split exact sequence. We wish to show that $$M_2 \cong M_1 \oplus M_3$$. Define $$\tau:M_1 \oplus M_3 \mapsto M_2,\tau((m_1,m_3))=\tau((m_1,(g \circ \phi)(m_3))) = f(m_1) + \phi(m_3)$$. We claim that $$\tau$$ is an $$R$$-isomorphism. Indeed, it is easy to see that $$\tau$$ is an $$R$$-homomorphism, as it is defined in terms of the sum of two $$R$$-homomorphisms. If $$\tau((m_1,m_3)) = 0$$, this implies that

$$f(m_1) + \phi(m_3) = 0 \Rightarrow g(f(m_1) + \phi(m_3)) = 0 \Rightarrow m_3 = 0$$

since $$\ker(g) = \text{Im}(f)$$ and $$g \circ \phi = \text{id}_{M_3}$$. Since $$f$$ is injective, this implies that $$m_1 = 0$$, and so $$\ker(\tau) = \{0\}$$, i.e., it is injective. Given any $$m_2 \in M_2$$, we know that we can write it uniquely as $$m_2 = f(m_1) + y = x + y$$, where $$m_1 \in M_1,y \in N,x \in \ker(g)$$. Let $$(m_1,g(y)) \in M_1 \oplus M_3$$, and note that $$\tau((m_1,g(y))) = f(m_1) + \phi(g(y)) = f(m_1) + y = m_2$$, since $$\phi(g(y))=y$$ by definition as $$y \in N$$. Thus $$\tau$$ is surjective, implying that it is an $$R$$-isomorphism and that $$M_2 \cong M_1 \oplus M_3$$.

## Lemma 2: Sufficient condition for split exact sequence
**Lemma 2:** Given an exact sequence of the form given in the previous diagram, if $$M_3$$ is a free $$R$$-module, then the sequence is split exact.

**Proof:**
If $$M_3$$ is free, then there exists a basis $$B = \{x_i\}_{i \in \mathcal{I}}$$ for some arbitrary set of indices $$\mathcal{I}$$. Since $$g$$ is surjective, for every $$x_i$$ there exists an $$m_i \in M_2$$ such that $$g(m_i) = x_i$$, thus define $$h:M_3\mapsto M_2$$ such that $$\forall i \in \mathcal{I}:h(x_i) = m_i$$, and since for every $$x \in M_3$$ can be written as $$x = \sum_j \alpha_{i_j}x_{i_j}$$, define $$h(x) = \sum_j \alpha_{i_j}h(x_{i_j})$$. It follows that $$h$$ is indeed an $$R$$-homomorphism by construction, and that
    
$$g(h(x)) = g(\sum_j \alpha_{i_j}h(x_{i_j}))=\sum_j \alpha_{i_j}g(h(x_{i_j}))=\sum_j \alpha_{i_j}x_{i_j} = x$$

thus $$g \circ h = \text{id}_{M_3}$$, and by the previous Lemma we conclude that the sequence is split exact.

## The main result
Our strategy here is relatively simple: we will proceed via induction on the rank of the $$R$$-module. We will try to express any submodule as a direct sum of free modules with limited rank, and then conclude that it also must have limited rank. This is where the exact sequences will come into play: we will build a natural exact sequence from the fact that our module is free with finite rank, and from this we'll use the previous lemmas together with induction to conclude the desired result.

Recall that any $$R$$-module over a unitary commutative ring with finite basis has the rank invariant property, i.e., any basis must have the same size. We now prove our main result.

**Theorem**: Let $$D$$ be a principal ideal domain and let $$M$$ be a free $$D$$-module with finite basis and rank $$n$$, then any $$D$$-submodule is also free with rank at most $$n$$.

**Proof:**
The proof will be by induction on $$n$$. If $$n = 1$$, then $$M \cong D$$, and since $$D$$ is a PID, it means that any $$D$$-submodule of $$D$$ is an ideal of $$D$$, thus being generated by at most one element, i.e., each $$D$$-submodule is free and with rank at most $$1$$. Now assume that if the rank of $$M$$ is strictly smaller than $$n$$, then any $$D$$-submodule is also free with rank at most the rank of $$M$$.

Let the rank of $$M$$ be $$n$$. It follows that $$M \cong D^{(n)}$$, i.e., $$M$$ is isomorphic to the direct sum of $$D$$ with itself $$n$$ times. Let such isomorphism be denoted by $$\phi$$, and let $$\pi_1:D^{(n)} \mapsto D,\pi_1((r_1,...,r_n))=r_1$$ be the projection onto $$D$$ w.r.t. the first element of the $$n$$-tuple. Let $$\{x_1,...,x_n\}$$ be a basis for $$M$$, and assume without loss of generality that $$\phi(x_i)=e_i$$, where $$e_i$$ denotes the $$n$$-tuple with $$1$$ on the $$i$$-th position and $$0$$ elsewhere. Define $$\psi:M\mapsto D,\psi = \pi_1 \circ \phi$$, and let $$N \leq M$$ be a $$D$$-submodule and $$L = \langle x_2,...,x_n\rangle$$ be the $$D$$-submodule of $$M$$ generated by the elements $$x_2,...,x_n$$.

Let $$\tau$$ denote the restriction of $$\psi$$ onto $$N$$, and note that $$\text{Im}(\tau)\leq D$$ by definition, thus by the induction hypothesis $$\text{Im}(\tau)$$ is a free $$D$$-submodule of $$D$$ with rank at most $$1$$ (since $$D$$ has rank $$1$$). Also, note that $$\ker(\tau)\leq L$$, since $$\ker(\psi) = L$$, and since $$L$$ is a free $$D$$-module of rank $$n-1$$, it follows that the rank of $$\ker(\tau)$$ is at most $$n-1$$. Now consider the following diagram:

$$0 \mapsto \ker(\tau) \mapsto N \mapsto_{\tau} \text{Im}(\tau) \mapsto 0$$

Note that the diagram is clearly an exact sequence, where the mapping between $$\ker(\tau)$$ and $$N$$ is merely the identity in $$N$$. Also, we've concluded that $$\text{Im}(\tau)$$ is a free $$D$$-module, thus by Lemma $$2$$ it follows that the sequence is split exact, and then by Lemma $$1$$ it follows that $$N \cong \ker(\tau) \oplus \text{Im}(\tau)$$. However $$\ker(\tau) \oplus \text{Im}(\tau)$$ is a free $$D$$-module of rank at most $$n$$, and thus $$N$$ is a free $$D$$-module of rank at most $$n$$, which concludes the proof.

## Comments
I found the proof of the main theorem to be extremely interesting: although the exact sequence that we create arises naturally, having the idea of building such sequence in the first place is really clever, and in first sight the properties of split exact sequences given by Lemmas 1 and 2 are not at all obvious. However, after trying to prove the theorem by myself, I believe that the meaning of these results becomes much more clear and natural.

This result also shows how much more complicated things can become once one generalizes the notion of a vector space. When dealing with finite dimensional vector spaces over a field, the main theorem is way simpler to prove: it is easy to show that any linearly independent set of vectors can either be extended to a bigger linearly independent set of vectors or it already is a basis (in order to prove this one needs invertibility, i.e., the ring must be a division ring). From this, given any subspace, any set of linearly independent vectors must be smaller than the dimension of the entire space, and thus we can choose an arbitrary non-zero vector of the subspace and extend it to a basis of the subspace, hence concluding that the rank of the subspace is at most the rank of the space.