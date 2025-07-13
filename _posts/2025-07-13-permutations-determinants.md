---
layout: post
title: permutations & other determinant formulas (artin 1.5 & 1.6)
date: 2025-07-13
description: yay artin
tags: mathematics
---

This is an exposition on Chapter 1, 1.5 & 1.6 on permutations and other formulas for the determinant.

## Notes on Chapter

A _permutation_ of a set $S$ is a bijective map $p$ from a set $S$ to itself:

$$p: S\rightarrow S.$$

The set of all permutations of the indices $\{1,2,\dots, \}$ is called the _symmetric group_, denoted by $S_n$. 

We can compose permutations using the notation $qp$, called the _product permutation_.

We can use _cycle notation_ to represent permutations. For example, if we have the permutation $\pi(\{1,2,3,4,5\})\rightarrow \{3,5,4,1,2\}$, we can create the cycle $(3 4 1)$ to represent $3\rightarrow 4\rightarrow 1 \rightarrow 3.$ Note that this is a $3$-cycle.

We can also have $(2,5)$, which is a $2$-cycle, also called _transpositions_. 

The compete cycle notation for $p$ is $(341)(25)$. Note that this is not unique.

In cycle notation, every index appears just once, and the order of which the cycles are written does not matter.

To compute the permutation product $qp$, first do $q$, then do $p$, as it is simply the composition $q \circ p.$ 

There is a _permutation matrix_ $P$ associated to any permutation $p$. Left multiply any matrix $X$ by the permutation matrix $P$ to permute $X$. 

------

__Proposition.__ The following are true.

(a) For a permutation matrix $P$, there is a single $1$ in each row and in each column, and the rest of the entries are $0$. Conversely, any such matrix is a permutation matrix.

(b) The determinant of a permutation matrix is $\pm 1$.

(c) Let $p$ and $q$ be two permutations. Let $P$ and $Q$ be the associated permutation matrices associated to $p$ and $q$. Then the permutation matrix for the permutation product $pq$ is the product $PQ$.

_Proof._ We only focus on (c). Note that we can compute directly:

$$PQ = \left(\sum_i e_{pi,i}\right)\left(\sum_j e_{qj,j}\right) = \sum_{i,j} e_{pi,i} e_{qj,j} = \sum_j e_{pqj,qj} e_{qj,j} = \sum_j e_{pqj,j}.$$

The determinant of a permutation matrix associated to permutation $p$ is called the _sign_ of the permutation:

$$\text{sign}(p) = \det{P} = \pm 1.$$

A permutation $p$ is _even_ if its sign is $+1$ and _odd if its sign is $-1$. 

Every permutation can be written as the product of transpositions $\tau_1, \dots \tau_k$, where $k$ is even if $p$ is even and $k$ is odd if $p$ is odd.

-----

The determinant can be calculated by expanding along *any* single row or column. The core idea remains the same: a sum of entries multiplied by the determinants of smaller sub-matrices (minors).

$A_{ij}$ is the matrix formed by deleting the $i$-th row and $j$-th column of matrix A.

The sign of each term in the expansion depends on the position $(i, j)$ of the entry and is given by $(-1)^{i+j}$. This creates a "checkerboard" pattern of signs:

$$\begin{matrix}
    + & - & + & - & \cdots \\
    - & + & - & + & \cdots \\
    + & - & + & - & \cdots \\
    \vdots & \vdots & \vdots & \vdots & \ddots
    \end{matrix}
$$

There are two cases for this:

Case 1: Expansion on the $j$-th column.

$$
\det(A) = \sum_{i=1}^{n} (-1)^{i+j} a_{ij} \det(A_{ij})
$$

Case 2: Expansion on the $i$-th row.

$$
\det(A) = \sum_{j=1}^{n} (-1)^{i+j} a_{ij} \det(A_{ij})
$$

__Remark.__ You can simplify calculations by choosing a row or column with the most zeros to expand along, as this will eliminate terms from the sum.

---

The _Leibniz Formula_ is

$$
\det(A) = \sum_{p \in S_n} (\text{sign } p) a_{1,p_1} a_{2,p_2} \cdots a_{n,p_n}
$$

The sum is over all $n!$ permutations ($p$) of the column indices $\{1, 2, ..., n\}$.

Thus, we can find the determinant. There are a few cases.

2x2 Matrix: $\det(A) = a_{11}a_{22} - a_{12}a_{21}$ (this is just $ad-bc$).

3x3 Matrix: $\det(A) = (a_{11}a_{22}a_{33} + a_{12}a_{23}a_{31} + a_{13}a_{21}a_{32}) - (a_{13}a_{22}a_{31} + a_{11}a_{23}a_{32} + a_{12}a_{21}a_{33})$

If the entries are differentiable functions, the determinant is also differentiable.

---

The $i,j$ _cofactor_ of A is the *signed minor* $C_{ij} = (-1)^{i+j} \det(A_{ij})$.

The Cofactor Matrix $\text{cof}(A)$ is the a matrix where the entry in the *$i$*-th row and *$j$*-th column is $(-1)^{i+j} \det(A_{ji})$.

Notice the transposed indices ($A_{ji}$). The cofactor matrix is the *transpose* of the matrix of cofactors.

To computer $\text{cof}(A)$, we go through a standard algorithm:

1.  Create a matrix of minors (find $\det(A_{ij})$ for all $i,j$).
2.  Apply the checkerboard of signs to get the matrix of cofactors.
3.  Transpose the result.

__Theorem.__ We have that

$$A \cdot \text{cof}(A) = \text{cof}(A) \cdot A = \det(A) \cdot I$$

Where $I$ is the identity matrix. 

This means the product of a matrix and its cofactor matrix is a diagonal matrix where every diagonal entry is $\det(A)$. If $\det(A) \neq 0$, then A is invertible and:

$$A^{-1} = \frac{1}{\det(A)} \text{cof}(A).$$
