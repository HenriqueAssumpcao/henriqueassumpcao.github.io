---
layout: distill
title: matrix decompositions and commuting matrices
date: 2024-02-28
description: a few cool results from linear algebra
tags: 
categories: math linear-algebra
giscus_comments: false
related_posts: false
related_publications: 

toc:
  - name: "Triangular, Normal and Nilpotent matrices"
  - name: "Invariant subspaces and commuting matrices"
  - name: "Final remarks"


---
A few months ago I was studying Bhatia's Matrix Analysis book while I stumbled upon a pretty basic result that, for some reason, I've never proven before in any of my linear algebra classes: that every matrix over the complex numbers has an orthogonal basis such that it is in an upper triangular form (called the Schur basis). In this post I'll prove this result, and then use it to prove that an arbitrary family of commuting matrices has a commom Schur basis, and also talk a bit a bout other interesting related results.

## Triangular, Normal and Nilpotent matrices

Let $$V$$ be a $$n$$-dimensional vector space over the complex numbers, and assume we have a matrix $$T$$ in upper-triangular form, where we denote the $$ij$$-th element of $$T$$ by $$T_{ij}$$. The determinant of a triangular matrix is just the product of its diagonal elements, since any permutation other than the identity results in at least one zero appearing in the product of elements given by the determinant formula. Now note that

$$\varphi(T,\lambda) = \det(\lambda I - T)$$

where $$\varphi$$ denotes the characteristic polynomial of $$T$$, and since $$\lambda I - T$$ is also upper triangular, we get that

$$\varphi(T,\lambda) = (\lambda - T_{11})\cdot...\cdot(\lambda - T_{nn})$$

and hence all of the eigenvalues of $$T$$ are in its diagonal entries.

We now prove that for any linear function $$f$$ on $$V$$ there exists an orthogonal basis in which the matrix of such function is upper triangular. Note that this is equivalent to saying that there is an orthogonal basis $$\{v_1,...,v_n\}$$ of $$V$$ such that $$f(v_i) \in \text{span}_{\mathbb{C}}(v_1,...,v_i)$$, and we can prove this via a simple induction on the dimension $$n$$ of $$V$$. If $$n = 1$$ then any normalized non-zero vector satisfies the desired property. For an arbitrary $$n$$, note that since $$\mathbb{C}$$ is algebraically closed we can always find an eigenvalue $$\lambda$$ with a non-zero eigenvector $$v_1$$, and thus decompose the space as

$$ V = \mathbb{C}v_1 \oplus (\mathbb{C}v_1)^\perp$$ 

where $$W = (\mathbb{C}v_1)^\perp$$ is the $$(n-1)$$-dimensional orthogonal complement of the span of $$v_1$$. If we consider the orthogonal projection $$p$$ onto $$W$$, the function $$p \circ f$$ is an endomorphism on $$W$$, and thus by the inductive hypothesis we can find a basis $$\{v_2,...,v_n\}$$ for $$W$$ such that $$(p \circ f)(v_i) \in \text{span}_{\mathbb{C}}(v_2,...,v_i)$$. Now if we consider $$\{v_1,...,v_n\}$$, it is an orthogonal basis for $$V$$, and since we can decompose the identity function $$\text{id} = p' + p$$, where $$p'$$ is the projection onto the span of $$v_1$$, we have that for every $$v_k$$

$$f(v_k) = ((p'+p)\circ f)(v_k) = (p'\circ f)(v_k) + (p \circ f)(v_k)$$

By definition, $$(p'\circ f)(v_k)$$ is in the span of $$v_1$$, and by the induction hypothesis $$(p \circ f)(v_k)$$ is in the span of $$v_2,...,v_k$$, hence $$f(v_k)$$ belongs to the span of $$v_1,...,v_k$$, as desired. This basis is called the *Schur basis* of a linear function, and from this it follows that for any matrix $$A$$ there is an orthogonal matrix $$Q$$ such that $$Q^*AQ$$ is upper triangular.

Recall that a matrix $$A$$ is called *normal* if it commutes with its adjoint, which in our case is nothing more than its conjugate transpose. The spectral theorem states that an operator on a finite dimensional vector space over $$\mathbb{C}$$ can be orthogonally diagonalized, i.e., written as $$Q\Lambda Q^*$$ with $$Q$$ orthogonal matrix, and $$\Lambda$$ diagonal matrix of eigenvalues, if and only if, it is normal. This theorem can actually be regarded as a corollary of the existence of the Schur Basis. If we write $$A$$ w.r.t. its Schur basis, we get that

$$
\begin{split}
A &= 
\begin{bmatrix}
a_{11} & a_{12} & ... & a_{1n}\\
0 & a_{22} & ... & a_{2n}\\
\vdots & \vdots & \vdots & \vdots\\
0 & 0 & ... & a_{nn}\\
\end{bmatrix}\\
A^* &= 
\begin{bmatrix}
\overline{a_{11}} & 0 & ... & 0\\
\overline{a_{12}} & \overline{a_{22}} & ... & 0\\
\vdots & \vdots & \vdots & \vdots\\
\overline{a_{1n}} & \overline{a_{2n}} & ... & \overline{a_{nn}}\\
\end{bmatrix}
\end{split}
$$

since the matrices commute, if we look at the result of their diagonal products, it follows that any off-diagonal entry must be zero, and thus $$A$$ and $$A^*$$ must be diagonal matrices, and hence $$A$$ can be orthogonally diagonalized.

An endomorphism $$f$$ on $$V$$ is called *nilpotent* if there exists a non-negative integer $$r$$ such that $$f^r = 0$$, i.e., f composed with itself $$r$$ times is equal to the zero map. From this definition it follows that any eigenvalue of $$f$$ must be zero, and since we've observed that any endomorphism on $$V$$ has a Schur basis, it follows that there is a basis in which $$f$$ is strictly upper triangular, i.e., all of its diagonal elements are zero. Conversely, any strictly upper triangular $$n \times n$$ matrix satisfies $$N^n = 0$$, and thus we get that an endomorphism over a finite-dimensional vector space is nilpotent iff there is a basis in which its matrix is strictly upper triangular. From these facts and the Schur decomposition, it follows that for any matrix $$A$$, there is an orthogonal matrix $$Q$$ such that

$$Q^*AQ = D + N$$

where $$D$$ is a diagonal matrix containing the eigenvalues of $$A$$, and $$N$$ is a nilpotent matrix.

## Invariant subspaces and commuting matrices

If $$V$$ is a vector space over $$\mathbb{C}$$ of dimension $$n$$, and $$A$$ is a linear operator on $$V$$, we can show that any $$A$$-invariant subspace of $$V$$ contains an eigenvector of $$A$$. Indeed, let $$W = \text{span}_{\mathbb{C}}(v_1,...,v_k)$$ be a $$k$$-dimensional subspace of $$V$$ such that $$AW \subset W$$, let $$B = [v_1 \quad ... \quad v_k]$$ be the $$n \times k$$ matrix containing the basis of $$W$$ in its columns. Since $$W$$ is $$A$$-invariant, it follows that there must exist a $$k \times k$$ matrix $$C$$ such that

$$AB = BC$$

since $$AB = A[v_1\quad ... \quad v_k] = [Av_1 \quad ... \quad Av_k]$$, and each $$Av_i$$ can be expressed as a linear combination of $$v_1,...,v_k$$. Since $$\mathbb{C}$$ is algebraically closed (this argument works for any algebraically closed field), it follows that the matrix $$C$$ itself has an eigenvector $$x$$ with some eigenvalue $$\lambda$$, hence

$$ABx = BCx = \lambda Bx$$

and thus $$Bx$$ is an eigenvector of $$A$$ (note that $$Bx$$ must be non-zero since the vectors in $$B$$ are linearly independent).

This is quite useful because, now, if we consider two commuting linear operators $$A$$ and $$B$$, we can show that they have a common eigenvector, and, moreover, we can show that they have a common Schur basis. Let $$v$$ be an eigenvector of $$A$$ with eigenvalue $$\lambda$$, and note that for any non-negative integer $$k$$, we have that

$$B^kAv = \lambda B^kv \Rightarrow A(B^kv) = \lambda (B^kv)$$

hence $$B^kv$$ is an eigenvector of $$A$$ for every $$k \geq 0$$. We can thus consider the space

$$W = \text{span}(v,Bv,B^2v,...)$$

and note that $$W$$ is $$B$$-invariant, so there is some $$k$$ for which $$B^kv$$ is an eigenvector of $$B$$, and thus a common eigenvector for $$A$$ and $$B$$ (not necessarily with the same eigenvalue). This can serve as a base case for showing that the result is true for any finite set of commuting matrices. Indeed, if we consider $$A_1,...,A_n$$ as a set of commuting matrices, we can assume that there exists a common eigenvector $$v$$ for $$A_1,...,A_{n-1}$$, and using the same argument as before, we see that for any non-negative $$k$$ that $$A_n^kv$$ is a common eigenvector for all $$A_i$$ with $$i < n$$. Again, we can consider the subspace

$$W = \text{span}(v,A_n^kv,A_n^{2k}v,...)$$
 
and note that it is $$A_n$$-invariant, and thus it also has an eigenvector of $$A_n$$, which by definition must be an eigenvector for all $$A_1,...,A_{n-1}$$, hence we have a common eigenvector of $$A_1,...,A_n$$.

Now, if $$A_1,...,A_n$$ are a set of commuting matrices, we can show that they have a common Schur basis. Again, we proceed via induction on the dimension $$n$$ of the space, and recall that we wish to show that there is a basis $$\{v_1,...,v_n\}$$ of $$V$$ such that

$$\forall i,j \in \{1,...,n\}:A_iv_j \in \text{span}_\mathbb{C}(v_1,...,v_j)$$

The base case of $$n=1$$ is immediate. For the general case, we start with a common eigenvector $$v_1$$ of $$A_1,...,A_n$$ with respective eigenvalue $$\lambda_i$$ for each $$A_i$$, and decompose the space as

$$V = \mathbb{C}v_1 \oplus (\mathbb{C}v_1)^\perp$$

Note that if we consider a basis for $$V$$ composed by a union of a basis for $$\mathbb{C}v_1$$ and $$(\mathbb{C}v_1)^\perp$$, the matrices $$A_i$$ will have the form

$$
A_i = 
\begin{bmatrix}
\lambda_i & a_i\\
0 & A_{i}'\\
\end{bmatrix}
$$

where $$a_i$$ is a $$n-1$$ dimensional line vector, $$0$$ is the $$n-1$$ dimensional zero vector, and $$A_i'$$ is a $$n-1\times n-1$$ block of $$A$$. Now for two matrices $$A_i,A_j$$, we have that

$$
\begin{split}
A_iA_j &=
\begin{bmatrix}
\lambda_i\lambda_j & c_{ij}\\
0 & A_{i}'A_{j}'\\
\end{bmatrix}\\
A_jA_i &=
\begin{bmatrix}
\lambda_j\lambda_i & d_{ji}\\
0 & A_{j}'A_{i}'\\
\end{bmatrix}\\
\end{split}
$$

where $$c_{ij},d_{ji}$$ are $$n-1$$ dimensional line vectors (we can compute these explicitly, but we don't really need that here). Since $$A_i,A_j$$ commute, it follows that so do $$A_{i}',A_{j}'$$, and thus $$A_1',...,A_n'$$ are a finite set of commuting matrices operators on a $$(n-1)$$-dimensional subspace of $$V$$ (namely $$(\mathbb{C}v_1)^\perp$$), and thus we obtain an orthogonal basis $$\{v_1,...,v_n\}$$ for $$V$$, and the same argument used to prove the existence of a Schur basis for a single matrix yields the desired result.

## Final remarks

We've seen that any finite commuting set of matrices has a common Schur basis over the complex numbers, however this same result also implies that this set doesn't need to be finite at all. This follows from the fact that, if $$\{A_i\}_{i \in \mathcal{I}}$$ is an arbitrary family of commuting matrix with entries on $$\mathbb{C}$$, then we can consider the *algebra* generated by such set. Recall that an algebra is just a ring which is also a module over some other ring, and in our case, an algebra is just a vector space that is closed w.r.t. matrix multiplication. Thus, the algebra generated by some set of matrices is nothing more than the set of all finite linear combinations of finite products between such matrices. For example, the algebra generated by some matrix $$A$$ is just the set of all finite linear combinations of powers of $$A$$. We say that an algebra is finite dimensional if it is so as a vector space, and hence the set of all $$n \times n$$ matrices over $$\mathbb{C}$$ is a finite dimensional algebra with dimension $$n^2$$ (just take the matrices $$E_{ij}$$ with only the $$ij$$-th entry non-zero and equal to one). Thus, any subalgebra of the full matrix algebra is also finite dimensional, and so the algebra generated by $$\{A_i\}_{i \in \mathcal{I}}$$ must have a finite basis of matrices, and since the generating set is commutative, the entire algebra also is. Hence, we can find a common Schur basis for the matrices that form a basis of such algebra, and then any matrix in this algebra will also be in an upper triangular form. It also follows as a corollary that any family $$\{A_i\}_{i \in \mathcal{I}}$$ of commuting normal matrices has a common orthogonal eigenbasis, i.e., there exists an orthogonal matrix $$Q$$ such that $$Q^*A_iQ$$ is diagonal for each $$i$$.

I'm currently studying matrix algebras and the Wedderburn-Artin theorems for my undergraduate thesis, so I intend on making more posts on connections between results in linear algebra and the study of matrix algebras and ring theory.



<!-- Now for proving that there is a common Schur basis, we again use induction on $$n$$. The base case is immediate, and in general we now know that if $$A$$ and $$B$$ commute, there is a common eigenvector $$v_1$$ for both of them, and thus we can decompose

$$ V = \mathbb{C}v_1 \oplus (\mathbb{C}v_1)^\perp$$  -->