---
layout: distill
title: the schur basis and some other decompositions
date: 2024-02-28
description: a few cool results from linear algebra that I realized I had never proven before
tags: 
categories: math linear-algebra
giscus_comments: false
related_posts: false
related_publications: 

toc:
  - name: "Triangular and Normal matrices"
  - name: "Nilpotent matrices"
  - name: "Invariant subspaces and commuting matrices"
  - name: "Final remarks"


---
A few months ago I was studying Bhatia's Matrix Analysis book while I stumbled upon a pretty basic result that, for some reason, I had never proven before in any of my linear algebra classes: that every matrix over the complex numbers has an orthogonal basis such that it is in an upper triangular form (called the Schur basis). In this post I'll prove this result, and then use it to prove that an arbitrary family of commuting matrices has a commom Schur basis, and also talk a bit about other interesting related results.

## Triangular and Normal matrices

Let $$V$$ be a $$n$$-dimensional vector space over the complex numbers, and assume we have a matrix $$T$$ in upper-triangular form, where we denote the $$ij$$-th element of $$T$$ by $$T_{ij}$$. The determinant of a triangular matrix is just the product of its diagonal elements, since any permutation other than the identity results in at least one zero appearing in the product of elements given by the determinant formula. Now note that

$$\varphi(T,\lambda) = \det(T - \lambda I)$$

where $$\varphi$$ denotes the characteristic polynomial of $$T$$, and since $$T - \lambda I$$ is also upper triangular, we get that

$$\varphi(T,\lambda) = (T_{11} - \lambda)\cdot...\cdot(T_{nn} - \lambda)$$

and hence all of the eigenvalues of $$T$$ are in its diagonal entries.

We now prove that for any linear operator $$A$$ on $$V$$ there exists an orthogonal basis in which the matrix of such function is upper triangular. Note that this is equivalent to saying that there is an orthogonal basis $$\{v_1,...,v_n\}$$ of $$V$$ such that $$Av_i \in \text{span}_{\mathbb{C}}(v_1,...,v_i)$$, and we can prove this via a simple induction on the dimension $$n$$ of $$V$$. If $$n = 1$$ then any normalized non-zero vector satisfies the desired property. For an arbitrary $$n$$, note that since $$\mathbb{C}$$ is algebraically closed we can always find an eigenvalue $$\lambda$$ with a non-zero eigenvector $$v_1$$, and thus decompose the space as

$$ V = \mathbb{C}v_1 \oplus (\mathbb{C}v_1)^\perp$$ 

where $$W = (\mathbb{C}v_1)^\perp$$ is the $$(n-1)$$-dimensional orthogonal complement of the span of $$v_1$$. If we consider the orthogonal projection $$P$$ onto $$W$$, the function $$PA$$ is a linear operator on $$W$$, and thus by the inductive hypothesis we can find a basis $$\{v_2,...,v_n\}$$ for $$W$$ such that $$(PA)(v_i) \in \text{span}_{\mathbb{C}}(v_2,...,v_i)$$. Now if we consider $$\{v_1,...,v_n\}$$, it is an orthogonal basis for $$V$$, and since we can decompose the identity $$I = P' + P$$, where $$P'$$ is the projection onto the span of $$v_1$$, we have that for every $$v_k$$

$$Av_k = ((P'+P)A)(v_k) = (P'A)(v_k) + (PA)(v_k)$$

By definition, $$(P'A)(v_k)$$ is in the span of $$v_1$$, and by the induction hypothesis $$(PA)(v_k)$$ is in the span of $$v_2,...,v_k$$, hence $$f(v_k)$$ belongs to the span of $$v_1,...,v_k$$, as desired. This basis is called the *Schur basis* of an operator, and from this it follows that for any matrix $$A$$ there is an orthogonal matrix $$Q$$ such that $$Q^*AQ$$ is upper triangular.

Recall that a linear operator $$A$$ is called *normal* if it commutes with its adjoint, and in our case for any fixed basis the matrix of the adjoint is the conjugate transpose of the operator's matrix. The spectral theorem states that an operator on a finite dimensional vector space over $$\mathbb{C}$$ can be orthogonally diagonalized, i.e., written as $$Q\Lambda Q^*$$ with $$Q$$ orthogonal matrix, and $$\Lambda$$ diagonal matrix of eigenvalues, if and only if, it is normal. This theorem can actually be regarded as a corollary of the existence of the Schur Basis. If we write $$A$$ w.r.t. its Schur basis, we obtain

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

and since the matrices commute, if we look at the result of their diagonal products, it follows that any off-diagonal entry must be zero, and thus $$A$$ and $$A^*$$ must be diagonal matrices, and hence $$A$$ can be orthogonally diagonalized.

## Nilpotent matrices

An operator $$A$$ on $$V$$ is called *nilpotent* if there exists a non-negative integer $$r$$ such that $$A^r = 0$$, i.e., A composed with itself $$r$$ times is equal to the zero map. From this definition it follows that any eigenvalue of $$A$$ must be zero, and since we've observed that any operator on $$V$$ has a Schur basis, it follows that there is a basis in which $$A$$ is strictly upper triangular, i.e., all of its diagonal elements are zero. Conversely, any strictly upper triangular $$n \times n$$ matrix satisfies $$N^n = 0$$, and thus we get that an operator over a finite-dimensional vector space is nilpotent iff there is a basis in which its matrix is strictly upper triangular. From these facts and the Schur decomposition, it follows that for any matrix $$A$$, there is an orthogonal matrix $$Q$$ such that

$$Q^*AQ = D + N$$

where $$D$$ is a diagonal matrix containing the eigenvalues of $$A$$, and $$N$$ is a nilpotent matrix in strict upper triangular form. This decomposition, however, is not unique, since the Schur basis is also not unique. We can, however, prove the uniqueness of the operators associated with $$D$$ and $$N$$, that is, we can prove that any operator $$A$$ can be uniquely written as

$$A = D + N$$

where $$D$$ is a *diagonalizable* operator (not necessarily in diagonal form), and $$N$$ is a operator (again not necessarily in upper triangular form). Moreover, we can show that $$D$$ and $$N$$ are polynomials in $$A$$, and hence they commute.

For this, since we are assuming that $$V$$ is a vector space over the complex numbers, we may assume that the minimal polynomial $$m_A$$ of $$A$$ is of the form

$$m_A(t) = (t-\lambda_1)^{r_1}\cdot\ldots\cdot(t-\lambda_k)^{r_k}$$

where each $$\lambda_i$$ is an eigenvalue, and $$\lambda_i \neq \lambda_j$$ if $$i \neq j$$. From the spectral theorem, it follows that we can decompose $$V$$ as 

$$V = W_1 \oplus\ldots\oplus W_k$$

where $$W_i = \ker((T - \lambda_i I)^{r_i})$$ is the *generalized eigenspace* associated with $$\lambda_i$$, and we can consider the projections $$E_i$$ in these spaces such that $$I = E_1 + ... + E_k$$, and $$E_iE_j = \delta_{ij}E_i$$. We can thus define the operator

$$D = \lambda_1 E_1 + ... + \lambda_k E_k$$

and we claim that $$D$$ is diagonalizable. Indeed, this follows by simply observing that for any $$v \in V$$, $$DE_iv = \lambda v$$, hence $$W_i \subset \ker(D - \lambda I)$$, and thus any basis of $$V$$ given by the union of bases for each $$W_i$$ is a basis of eigenvectors of $$D$$. Now consider the operator

$$N = A - D$$

and note that $$N$$ is a polynomial in $$A$$, and so is $$D$$, and thus they commute. Now since $$A = AE_1 + ... + E_k$$, we have that

$$ N = \sum_{i=1}^k (A-\lambda_i I)E_i $$

however, we recall that each $$E_i$$ is a polynomial in $$A$$, and hence commutes with $$A$$, thus we have

$$
\begin{split}
N^2 &= \sum_{i,j} (A-\lambda_i I)E_i(A-\lambda_j I)E_j \\
&= \sum_{i,j} (A-\lambda_i I)(A-\lambda_j I)E_iE_j = \sum_i (A-\lambda_i I)^2E_i
\end{split}
$$

and in general we have that $$N^r = \sum_i (A-\lambda_i I)^rE_i$$, then if $$r \geq \max(r_1,...,r_k)$$, by definition of the minimal polynomial, we have that $$N^r = 0$$, thus $$N$$ is nilpotent. This shows that we can decompose any operator as a sum of a diagonalizable operator and a nilpotent operator. One way of thinking about this argument is that we are removing the diagonalizable part of $$A$$ and then showing that this new operator is nilpotent, which makes sense since any non-zero nilpotent operator is not diagonalizable (since the only possible eigenvalue is zero).

Now, we need to check that $$N$$ and $$D$$ are indeed unique (as operators, not as matrices). Assume that $$A = N + D = N' + D'$$, and so

$$D - D' = N' - N$$

Since both $$N'$$ and $$N$$ are nilpotent, we can choose a sufficiently large $$r$$ such that

$$(N' - N)^r = \sum_{i=0}^r (-1)^i {r \choose i}(N')^iN^{r-i} = 0$$

and so $$N' - N$$ is also nilpotent. Note, however, that since both $$D$$ and $$D'$$ are diagonalizable and commute, they are simultaneously diagonalizable, and hence $$D-D'$$ is also a diagonalizable operator, and so we have that a nilpotent operator is equal to a diagonalizable operator, however we know that the Schur basis of a nilpotent operator is a strictly upper triangular matrix, and that the schur basis of a diagonalizable operator is an eigenbasis, hence $$D-D' = N'-N = 0$$, and we conclude that the operators are unique.
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
