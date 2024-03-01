---
layout: distill
title: when will an endomorphism ring be a field?
date: 2023-11-22
description: an interesting result from the course on rings and modules
tags: 
categories: math rings-and-modules
giscus_comments: false
related_posts: false
related_publications: 

toc:
  - name: "Isomorphisms between rings of endomorphisms"
  - name: "Endomorphisms of commutative rings"
  - name: "Putting it all together"
  - name: "Comments"


---
I'm currently taking a course on Rings and Modules at UFMG, and this week I came across an interesting result that I've decided to share here.

Let $$R$$ be a ring with unity. We wish to show that if $$R$$ is commutative and if $$M$$ is a simple $$R$$-module, then the ring of $$R$$-endomorphisms $$\text{End}_R(M)$$ is a field.
## Isomorphisms between rings of endomorphisms
We will first prove an auxiliary result that turns out to be quite useful.

**Lemma 1:** Let $$R$$ be a unitary ring, and let $$M,N$$ be two isomorphic $$R$$-modules. Then $$\text{End}_R(M)$$ and $$\text{End}_R(N)$$ are isomorphic as rings.

**Proof:**

  Let $$\phi:M\mapsto N$$ be the $$R$$-isomorphism between $$M$$ and $$N$$. Define $$\psi:\text{End}_R(M)\mapsto \text{End}_R(N)$$, where $$\psi(f)(n) = \phi(f(\phi^{-1}(n)))$$, for all $$f \in \text{End}_R(M),n \in N$$. We claim that $$\psi$$ is a ring isomorphism.

If $$f,g \in \text{End}_R(M)$$, then

$$\psi(f+g)(n)=\phi((f+g)(\phi^{-1}(n)))$$

$$=\phi(f(\phi^{-1}(n))+g(\phi^{-1}(n)))$$

$$= \phi(f(\phi^{-1}(n)))+\phi(g(\phi^{-1}(n)))$$

$$= \psi(f)(n) + \psi(g)(n),\forall n \in N$$ 

since $$\phi$$ is itself an endomorphism, and thus additive over $$M$$.

Also

$$\psi(f\circ g)(n) = \phi(f(g(\phi^{-1}(n))))$$

$$=\phi(f(\phi^{-1}(\phi(g(\phi^{-1}(n))))))$$

$$=\phi(f(\phi^{-1}(\psi(g)(n))))$$

$$=\psi(f)(\psi(g)(n)) = (\psi(f) \circ \psi(g))(n),\forall n \in N$$

therefore $$\psi$$ is a ring homomorphism.

If $$f \in \ker(\psi)$$, we have that $$\forall n \in N: \psi(f)(n) = 0 \Rightarrow \phi(f(\phi^{-1}(n))) = 0$$. Since $$\phi$$ is a $$R$$-module isomorphism, this implies that $$\forall n \in N: f(\phi^{-1}(n)) = 0$$, but again $$\phi$$ is an isomorphism, thus its inverse is also surjective, which implies that $$\forall m \in M: f(m) = 0$$, and so $$f = 0 \Rightarrow \ker(\psi)=\{0\}$$, i.e., $$\psi$$ is injective.

Given $$g \in \text{End}_R(N)$$, define $$f(m) = \phi^{-1}(g(\phi(m)))$$. Note that $$f$$ is an endomorphism, since $$\phi$$ and $$g$$ both are. Also, note that

$$\psi(f)(n) = \phi(\phi^{-1}(g(\phi(\phi^{-1}(n))))) = g(n),\forall n \in N$$

thus $$\psi(f) = g$$, and so $$\psi$$ is surjective.

The previous points show that $$\psi$$ is indeed a ring isomorphism, which concludes the proof.
## Endomorphisms of commutative rings
We now look at the ring of $$R$$-homomorphisms of a commutative unitary ring $$R$$.

**Lemma 2:** Let $$R$$ be a commutative ring with unity. The following statements hold:
1. The rings $$R$$ and $$\text{End}_R(R)$$ are isomorphic via $$\phi:\text{End}_R(R)\mapsto R,\phi(f)=f(1),\forall f \in \text{End}_R(R)$$.
2. If $$I$$ is an ideal of $$R$$, then $$R/I$$ is isomorphic to $$\text{End}_R(R/I)$$.

**Proof:**

For the first statement, let $$f,g \in \text{End}_R(R)$$, and note that

$$\phi(f+g)=(f+g)(1)=f(1)+g(1)=\phi(f)+\phi(g)$$

$$\phi(f\circ g) = f(g(1)) = f(1\cdot g(1))=f(1)g(1)=\phi(f)\cdot\phi(g)$$

thus $$\phi$$ is a ring homomorphism. If $$f \in \ker(\phi)$$, we have that $$f(1) = 0$$, but note that $$\forall a \in R:f(a) = a\cdot f(1)$$, since $$f$$ is a $$R$$-homomorphism, thus if $$f(1)=0$$, this implies that $$f = 0$$, and so $$\phi$$ is injective. Moreover, given any $$a \in R$$, we can define $$f(1)=a$$, and $$f(b)=b\cdot a$$, which yields that $$\phi(f)=a$$ and that $$f$$ is a $$R$$-homomorphism. Therefore $$\phi$$ is a ring isomorphism.

For the second statement, note that since $$R$$ is commutative and $$I$$ is a bilateral ideal of $$R$$, $$R/I$$ is a ring, and thus $$R/I$$ can be viewed as an $$R/I$$-module. On the other hand, since $$I$$ is an ideal and $$I$$ is an $$R$$-module, $$R/I$$ is also an $$R$$-module. Thus, if $$f \in \text{End}_{R/I}(R/I)$$, note that 

$$f(a \cdot (b+I))=f((a+I)(b+I)) = (a+I)f(b+I)=a\cdot f(b+I)$$

thus $$f \in \text{End}_{R}(R/I)$$. Conversely, if $$f \in \text{End}_{R}(R/I)$$, we have that

$$f((a+I)(b+I))=f(ab+I)=f(a(b+I))=af(b+I)=(a+I)f(b+I)$$

and so $$f \in \text{End}_{R}(R/I)$$, implying that $$\text{End}_{R/I}(R/I) = \text{End}_{R}(R/I)$$. Using this fact and the previous result, we conclude that $$R/I$$ and $$\text{End}_{R}(R/I)$$ are isomorphic rings.

## Putting it all together
Recall that an $$R$$-module $$M$$ is called simple if it has no proper non-trivial submodules, i.e., its only submodules are $$\{0\}$$ and $$M$$. We know that this is equivalent to two things: first that $$M$$ must be cyclic, and every non-zero element of $$M$$ must be a generator, and second that $$M$$ is $$R$$-isomorphic to $$R/I$$, where $$I$$ is some maximal left-ideal of $$R$$. We are now ready to prove our main result.

**Theorem:** Let $$R$$ be a commutative ring with unity, and $$M$$ be a simple $$R$$-module. Then $$\text{End}_{R}(M)$$ is a field.

**Proof:**

Since $$M$$ is simple, it follows that it is $$R$$-isomorphic to $$R/I$$, where $$I$$ is a maximal left-ideal of $$R$$, but since $$R$$ is commutative, this implies that $$I$$ is a maximal bilateral ideal. From Lemma 1, it follows that $$\text{End}_{R}(M)$$ and $$\text{End}_{R}(R/I)$$ are isomorphic rings, and from Lemma 2 it follows that $$\text{End}_{R}(R/I)$$ is isomorphic to $$R/I$$ as rings, so $$\text{End}_{R}(M)$$ is isomorphic to $$R/I$$ as rings. However, note that since $$I$$ is a maximal bilateral ideal, $$R/I$$ is a field, and thus $$\text{End}_{R}(M)$$ is itself a field.

## Comments
The proof of this result is quite simple due to it being mainly a series of straightforward algebraic manipulations. However, I still think that it portrays some interesting techniques.

Lemma 1 essentially provides a way of converting a module homomorphism between two modules to a ring homomorphism between two rings that are closely related to the original modules. This surely has limited applications, however in our case it is precisely what we needed: we start by assuming that $$M$$ is simple, and thus it is isomorphic to $$R/I$$ as a module, however due to the fact that $$I$$ is maximal we also know that $$R/I$$ is a field. We then need a way of connecting this module isomorphism to a ring isomorphism, and this is precisely what Lemma 1 does. Lemma 2 on the other hand is just a bundle of simple observations that follow from basic properties of unitary commutative rings, and so it itself isn't of much interest, however combined with Lemma 1 it yields the desired result. As for the main theorem itself, it yields a more powerful version of Schur's Lemma: function composition for simple modules over commutative rings is itself commutative.