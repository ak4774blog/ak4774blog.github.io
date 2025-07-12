---
layout: post
title: determinants (artin 1.4)
date: 2025-07-12
description: yay artin
tags: mathematics
---

This is an exposition on Sections 1.4 on the determinant from Artin Algebra.

## Notes on Chapter

Every square matrix has a _determinant_, denoted $\det{A}.$ There are some cases.

* $1 \times 1$ matrix. $\det{[a]}=a.$

* $2 \times 2$ matrix.

$$\begin{bmatrix} a & b \\ c & d \end{bmatrix} = ad - bc.$$ 

Note that $|\det{A}|$ is the area of a parallelogram, and if $|\det{A}|=0,$ then the parallelogram degenerates to a line or point.

This generalizes to any $n\times n$ matrix, so the determinant is a fuction from this space to the real numbers: $\det{}: \mathbb{R}^{n\times n} \rightarrow \mathbb{R}.$

----

We can recursively calculuate determinants using _expansion by minors_, which is a technique that finds $\det{n\times n}$ using $(n-1)\times(n-1)$ submatrices. The equation is:

$$\det{A} = \sum_{\nu} \pm a_{\nu 1}\det{A_{\nu 1}}.$$

__Theorem.__ There is a function $\delta$ on the space of $n\times n$ matrices with the properties below (called the determinant):

(i) $I$ is the identity matrix, $\delta(I)=I$.

(ii) $\delta$ is linear in the rows of the matrix $A$.

(iii) If a pair of adjacent rows of a matrix $A$ are equal, then $\delta(A)=0$.

__Theorem.__ For matrices $A$ and $B$, $\det AB = (\det A)(\det B)$.

__Theorem.__ Let $\delta$ be a function that satisfies the above properties. Then, 

(a) If $A'$ is obtained from $A$ by adding a multiple of row $j$ of $A$ to row $i$ and $i\ne j$, then their determinants are the same.

(b) If $A'$ is obtained from $A$ by interchanging row $i$ and row $j$ of $A$ and $i\ne j$, then their determinants satisfy $\delta(A')=-\delta(A).$

(c) If $A'$ is $A$ but row $i$ is multiplied by a scalar $c$, then $\delta A'= c \delta(A)$. If a row of matrix $A$ is equal to zero, then $\delta(A)=0$

(d) If row $i$ of $A$ is equal to a multiple of row $j$, and $i\ne j$, then $\delta(A)=0.$

__Corollary.__ (a) A square matric $A$ is invertible if and only if its determinant is nonzero. If $A$ is invertible, then $\det(A^{-1}) = (\det(A))^{-1}.$

(b) The determinant of a matrix $A$ is equal to the determinant of its transpose $A^{\text{t}}.$

(c) The properties above hold if you replace row with column.

----

## Exercises

__4.1__ Evaluate the following determinants: 

(a) 

$$\begin{pmatrix} 1 & i \\ 2-i & 3 \end{pmatrix}$$

(b) 

$$\begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}$$

(c) 

$$\begin{pmatrix} 2 & 0 & 1 \\ 0 & 1 & 0 \\ 1 & 0 & 2 \end{pmatrix}$$

(d) 

$$\begin{pmatrix} 1 & 0 & 0 & 0 \\ 5 & 2 & 0 & 0 \\ 8 & 6 & 3 & 0 \\ 0 & 9 & 7 & 4 \end{pmatrix}$$

_Solution._
(a) The determinant is $(1)(3) - (i)(2-i) = 3 - 2i + i^2 = 3 - 2i - 1 = \boxed{2-2i}$.
(b) The determinant is $(1)(-1) - (1)(1) = \boxed{-2}$.
(c) Expanding along the second row gives 

$$1 \cdot (-1)^{2+2} \det\begin{pmatrix} 2 & 1 \\ 1 & 2 \end{pmatrix} = (2)(2) - (1)(1) = \boxed{3}$$.

(d) This is a lower triangular matrix, so the answer is $1 \cdot 2 \cdot 3 \cdot 4 = \boxed{24}$.

__4.2__ Verify the rule $\det(AB) = (\det A)(\det B)$ for the matrices $A = \begin{pmatrix} 2 & 3 \\ 1 & 4 \end{pmatrix}$ and $B = \begin{pmatrix} 1 & 1 \\ 5 & -2 \end{pmatrix}$.

_Solution._ First, $\det A = (2)(4) - (3)(1) = 8 - 3 = 5$, $\det B = (1)(-2) - (1)(5) = -2 - 5 = -7$.
So, $(\det A)(\det B) = (5)(-7) = -35$.
Next, 

$$AB = \begin{pmatrix} 2 & 3 \\ 1 & 4 \end{pmatrix} \begin{pmatrix} 1 & 1 \\ 5 & -2 \end{pmatrix} = \begin{pmatrix} 2(1)+3(5) & 2(1)+3(-2) \\ 1(1)+4(5) & 1(1)+4(-2) \end{pmatrix} = \begin{pmatrix} 17 & -4 \\ 21 & -7 \end{pmatrix}$$


So,
$\det(AB) = (17)(-7) - (-4)(21) = -119 + 84 = -35$. Thus the claim holds.

__4.3__ Compute the determinant of the following $n \times n$ matrix using induction on $n$: a tridiagonal matrix with 2s on the main diagonal and -1s on the superdiagonal and subdiagonal.

_Proof._ Let $d_n$ be the determinant of the $n \times n$ matrix. We get $d_n = 2 d_{n-1} - d_{n-2}$ for $n \ge 3$ using expansion by minors. Let's induct. For $n=1$, $d_1 = \det(2) = 2$, works. For $n=2$, $d_2 = \det\begin{pmatrix} 2 & -1 \\ -1 & 2 \end{pmatrix} = 4-1=3$, works. Assume $d_k = k+1$ holds for all positive integers $k < n$. Using the recurrence relation:

$$d_n = 2d_{n-1} - d_{n-2} = 2((n-1)+1) - ((n-2)+1) = 2n - (n-1) = n+1$$

Thus, the determinant is $\boxed{n+1}$, as desired. $\square$
