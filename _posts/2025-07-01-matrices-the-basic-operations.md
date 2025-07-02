---
layout: post
title: basic matrix operations (artin 1.1)
date: 2025-07-01
description: yay artin
tags: mathematics
---

This blog post, as well as the upcoming posts, will generally follow the format of the book (Artin Algebra e2) itself. This is an exposition on Chapter 1, 1.1 on the basic operations of Matrices.

## Notes on Chapter

A $m \times n$ _matrix_ for $m, n \in \mathbb{Z}^+$ is simply a rectangular array of $mn$ integers:

$$
\begin{array}{cc}
                 & n \text{ columns} \\
    m \text{ rows} & \begin{bmatrix} a_{11} & \ldots & a_{1n} \\ \vdots &        & \vdots \\ a_{m1} & \ldots & a_{mn} \end{bmatrix}
\end{array}
$$

---

Some definitions about matrices:

- The numbers $a_{ij}$ are called the _matrix entries_
  - The index $i$ is the _row index_ and j is defined similarly as the _column index_ where $i \in [1,m]$ and $j \in [1,n].$
- A $n\times n$ matrix is called a _square matrix_.
- A $1\times n$ matrix is called a _row vector_, represented as

$$[a_1 \dots a_n],$$

and a $n\times 1$ matrix is called a _column vector_, represented as

$$
\begin{bmatrix}
           a_1 \\ 
           \vdots \\
           a_n
\end{bmatrix}.
$$

-----

We can _add matrices_. For two matrices with the same dimensions (the only case in which we can add matrices), say $A = (a_{ij}), B= (b_{ij})$, we can just add each element in the vectors. Formally, for each element $s_{ij} \in X$, where $X = A+B$, $s_{ij} = a_{ij} + b_{ij}$.

We can also do _scalar multiplication_, where we multiply a matrix $A$ by a scalar $b$. This is also similarly easy to do: for the new matrix $C$, $C_{ij} = A_{ij}b.$

_Matrix multiplication_ is less trivial than the above two operations. There are a couple of cases for matrix multiplication.

Case 1: Multiplying a column and row vector with the same dimension. This is fairly straightforward, just take $\sum_{n=1}^m a_n b_n.$ For example (courtesy of Artin),

$$\begin{bmatrix} 1 & 3 & 5 \end{bmatrix} \begin{bmatrix} 1 \\ -1 \\ 4 \end{bmatrix} = 1 - 3 + 20 = 18.$$

This type of matrix multiplication is useful for dimensional analysis used in science classes. For example, $(\text{grams}/\text{bar}) \cdot (\text{cost} / \text{gram}) = (\text{cost} / \text{gram}).$

Case 2: Multiplying matrices with one having $n$ rows, and another having $n$ columns. First, note that if matrix $A$ has dimensions $l \times m$ and matrix $B$ has dimensions $m \times n$, then the product $A \times B$ will have dimensions $l \times n$.
We can denote the product $A\times B$ as $P=(p_{ij})$. Then, $p_{ij}:= a_{i1}b_{1j} + a_{i2}b_{2j} + \cdots + a_{im}b_{mj}.$

One useful application of matrix multiplication is to write linear equations nicely. For example, the system of equations:

$$
\begin{array}{ccccccc}
a_{11}x_1 & + & \cdots & + & a_{1n}x_n & = & b_1 \\
a_{21}x_1 & + & \cdots & + & a_{2n}x_n & = & b_2 \\
\vdots    &   &        &   & \vdots    &   & \vdots \\
a_{m1}x_1 & + & \cdots & + & a_{mn}x_n & = & b_m
\end{array}
$$

can be written as $AX = B$, where $A$ is the matrix of the coefficients of the equations, $X$ are the solutions and $B$ are the constants on the right side of the equations. For example (from Artin),

$$
\begin{bmatrix} 2 & 1 & 0 \\ 1 & 3 & 5 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix} = \begin{bmatrix} 1 \\ 18 \end{bmatrix}
$$

is:

$$
\begin{align*}
2x_1 + x_2 &= 1 \\
x_1 + 3x_2 + 5x_3 &= 18.
\end{align*}
$$

Note that matrix multiplication is only defined when the number of columns of matrix $A$ is equal to the number of rows of matrix $B$.

---

Some identities of matrices include (for matrices $A$ and $B$):

- The _distributive law_: $A(B + B') = AB + AB',$ and $(A+A')B = AB+A'B$. 
- The _associative law_: $(AB)C = A(BC)$. Sizes should be $A = l \times m$, $B=m\times n$, and $C = n\times p$ for some $l,m,n,p$. This implies that scalar multiplication can be represented as $c(AB) = (cA)B = A(cB)$.
- The _commutative law_ does not hold for matrix multiplication, so $AB \ne BA$ (usually).
  - Even when both matrices are square, commutativity does not hold.
  - When it occurs that $AB=BC$, $A$ and $C$ are said to _commute_

Some additional definitions

- Matrices with all elements $0$ are a _zero matrix_.
- The diagonal $a_{ii}$ are its _diagonal entries_. 
  - A matrix with its only nonzero entries being on the diagonal is called a _diagonal matrix_.
- A $n\times n$ matrix with its diagonal elements being $1$ are called a _identity matrix_ denoted $I_n,$ and satisfy $AI_n=A$ and $I_mA = A$. These are usually just denoted as $I$ in standard texts.
- A matrix in which the upper triangle is undetermined, while all other elements are $0$ is called a _upper triangular_ matrix. Undetermined values in a matrix are denoted with * (an asterisk).
- Let $A$ be a square matrix with dimensions $n \times n$. If there exists a matrix $B$ such that

$$AB = I_n, BC = I_n,$$

then $B$ is the _inverse_ of $A$, denoted $A^{-1}.$ A matrix $A$ that has a inverse is called a _invertible matrix_. Note that $AA^{-1} = I = A^{-1}A.$ 

**Lemma (left and right inverse).** Let $A$ be a square matrix that has a _right inverse_, a matrix $R$ such that $AR=I$, and also a _left inverse_, a matrix $L$ such that $LA = I$. Then $R=L$. So $A$ is invertible and $R$ is its inverse.

_Proof._ By definition, $R = IR$. Then, $R = LA(R) = L(AR)= LI= L$, as desired. $\square$

**Proposition.** Let $A$ and $B$ be invertible matrices. The product $AB$ and the inverse $A^{-1}$ are invertible, $(AB)^{-1}=B^{-1}A^{-1}$ and $(A^{-1})^{-1}=A$. If $A_1, \dots, A_m$ are invertible $n\times n$ matrices, the product $A_1\dots A_m$ is invertible, and its inverse is $A^{-1}_m\dots A^{-1}_1$.

For a $2 \times 2$ matrix, its inverse is useful to memorize:

$$\begin{bmatrix} a & b \\ c & d \end{bmatrix}^{-1} = \frac{1}{ad-bc} \begin{bmatrix} d & -b \\ -c & a \end{bmatrix}.$$

Note that the denominator $ad-bc$ is the _determinant_ of the matrix; if the determinant is $0$, the matrix is not invertible.

The set of all invertible $n\times n$ matrices is called the $n$-dimensional _general linear group_.

**Lemma.** A square matrix that has either a row of zeros of a column of zeros is not invertible.

_Proof._ It suffices to check the two cases separately:

Case 1: row of zeros. We claim that the matrix does not have a right inverse. If a row of $A$, a $n\times n$ matrix, is zero, and a similarly defined $B$, then the row of the product $AB$ is zero as well, as desired.

Case 2: column of zeros. We claim that the matrix does not have a left inverse. A similar argument to the above case works here. $\square$

---

We can simplify matrix multiplication using various tricks. One of these tricks is called _block multiplication_. It allows us to simplify the multiplication by partitioning the matrices into smaller sub-matrices called "blocks". Then, you can treak these blocks as numbers, and do the multiplication easily.

There are two key cases for this technique:

Case 1: The row + column structure. We first take a matrix $M$ and split it vertically into two blocks $A$ and $B$ as such: $M = [A \mid B].$ We can then take another matrix $M'$ and split it horizontally into two blocks $A'$ and $B'$ (the author is too lazy to draw this out).
Then, to multiply, you can use $MM' = AA'+BB'$, just like multiplying a column and row vector.

Case 2: The 2x2 block structure. We can decompose into two different blocks, and multiply the same way as normal $2 \times 2$ matrices.

---

_Matrix units_ are the simplest nonzero matrices. The matrix unit $e_{ij}$ only has one nonzero element: a one in the position $i, j$. Matrices are usually denoted using uppercase letters, but a special exception for matrix units are given.

$$
e_{ij} = 
\begin{array}{cc}
                 & j \\
    i & \left[ \begin{array}{ccc}
                 & \vdots & \\
               \cdots & 1 & \cdots \\
                 & \vdots & 
              \end{array} \right]
\end{array}
$$

The set of matrix units is called a _basis_ for the space of $m \times n$ matrices, because every $m\times n$ matrix $A = (a_{ij})$ is a _linear combination_ of the matrices $e_{ij}$:

$$A = a_{11}e_{11} + a_{12}e_{12} + \dots = \sum_{i,j} a_{ij}e_{ij}.$$

To multiply a $m \times n$ matrix unit $e_{ij}$ and a $n\times p$ matrix unit $e_{jl}$, we can use the following formulas:

$$e_{ij}e_{jl} = e_{il}, e_{ij}e_{kl}=0 \quad \text{if} \quad j \ne k.$$

The column vector $e_i$, which has a single $1$ in its only nonzero position $i$ is a matrix unit, and the set $\{e_1, \dots, e_n\}$ is the _standard basis_ of the $n$-dimensional vector space $\mathbb{R}^n.$
Multiplying these by column vectors is also well known. For a column vector $X = (x_1,\dots,x_n)$, 

$$X = x_1e_1+\dots + x_ne_n = \sum_i x_ie_i.$$

To multiply matrix units and standard basis vectors, you can use the formulas:

$$e_{ij}e_{j} = e_{i}, e_{ij}e_{k} = 0 \quad \text{if} \quad j \ne k.$$

---

## Exercises

**1.1.** What are the entries $a_{21}$ and $a_{23}$ of the matrix:

$$A = \begin{bmatrix} 1 & 2 & 5 \\ 2 & 7 & 8 \\ 0 & 9 & 4 \end{bmatrix}?$$

_Solution._ The entry $a_{21}$ is just the value in 2nd row and 1st column, or $\boxed{2}$. Similarly, the value in the 2nd row and 3rd column is $\boxed{8}.$ $\square$

---

**1.2.** Determine the products $AB$ and $BA$ for the following values of $A$ and $B$: (a) 

$$A = \begin{bmatrix} 1 & 2 & 3 \\ 3 & 1 & 1 \end{bmatrix}, B = \begin{bmatrix} -8 & -4 \\ 9 & 5 \\ -3 & -2 \end{bmatrix}$$

(b) 

$$A = \begin{bmatrix} 1 & 4 \end{bmatrix}, B = \begin{bmatrix} 6 & -4 \\ 3 & 2 \end{bmatrix}$$ 

_Solution._ (a) The product will be a $2 \times 2$ matrix.

$$
    AB = \begin{bmatrix} 1 & 2 & 3 \\ 3 & 1 & 1 \end{bmatrix} \begin{bmatrix} -8 & -4 \\ 9 & 5 \\ -3 & -2 \end{bmatrix}
    = \begin{bmatrix} -8+18-9 & -4+10-6 \\ -24+9-3 & -12+5-2 \end{bmatrix}
    = \boxed{\begin{bmatrix} 1 & 0 \\ -18 & -9 \end{bmatrix}}
$$

The product $BA$ will be a $3 \times 3$ matrix.

$$
    BA = \begin{bmatrix} -8 & -4 \\ 9 & 5 \\ -3 & -2 \end{bmatrix} \begin{bmatrix} 1 & 2 & 3 \\ 3 & 1 & 1 \end{bmatrix}
    = \begin{bmatrix} -8-12 & -16-4 & -24-4 \\ 9+15 & 18+5 & 27+5 \\ -3-6 & -6-2 & -9-2 \end{bmatrix}
    = \boxed{\begin{bmatrix} -20 & -20 & -28 \\ 24 & 23 & 32 \\ -9 & -8 & -11 \end{bmatrix}}
$$

(b) The product $AB$ will be a $1 \times 2$ matrix.

$$
    AB = \begin{bmatrix} 1 & 4 \end{bmatrix} \begin{bmatrix} 6 & -4 \\ 3 & 2 \end{bmatrix}
    = \begin{bmatrix} 6+12 & -4+8 \end{bmatrix} = \boxed{\begin{bmatrix} 18 & 4 \end{bmatrix}}
$$

The product $BA$ is $\boxed{\text{undefined}}$ as the dimensions don't match. $\square$

---

**1.3.** Let 

$$A = \begin{bmatrix} a_1 & \cdots & a_n \end{bmatrix}$$

be a row vector, and let 

$$B = \begin{bmatrix} b_1 \\ \vdots \\ b_n \end{bmatrix}$$

be a column vector. Compute the products $AB$ and $BA$.

_Solution._ We have that

$$
AB = \begin{bmatrix} a_1 & \cdots & a_n \end{bmatrix} \begin{bmatrix} b_1 \\ \vdots \\ b_n \end{bmatrix} = a_1b_1 + a_2b_2 + \cdots + a_nb_n = \sum_{k=1}^{n} a_k b_k
$$ 

Also,

$$
BA = \begin{bmatrix} b_1 \\ b_2 \\ \vdots \\ b_n \end{bmatrix} \begin{bmatrix} a_1 & a_2 & \cdots & a_n \end{bmatrix}
    = \begin{bmatrix}
    b_1 a_1 & b_1 a_2 & \cdots & b_1 a_n \\
    b_2 a_1 & b_2 a_2 & \cdots & b_2 a_n \\
    \vdots & \vdots & \ddots & \vdots \\
    b_n a_1 & b_n a_2 & \cdots & b_n a_n
    \end{bmatrix} \square
$$

---

**1.7.** Find a formula for 

$$\begin{bmatrix} 1 & 1 & 1 \\ 0 & 1 & 1 \\ 0 & 0 & 1 \end{bmatrix}^n,$$

and prove it by induction.

_Solution._ Let 

$$M = \begin{bmatrix} 1 & 1 & 1 \\ 0 & 1 & 1 \\ 0 & 0 & 1 \end{bmatrix}.$$

The formula is 

$$M^n = \begin{bmatrix} 1 & n & \frac{n(n+1)}{2} \\ 0 & 1 & n \\ 0 & 0 & 1 \end{bmatrix}.$$

For the base case $n=1$, we get 

$$\begin{bmatrix} 1 & 1 & \frac{1(2)}{2} \\ 0 & 1 & 1 \\ 0 & 0 & 1 \end{bmatrix} = M,$$

which is obviously true. For the inductive step, assume the formula holds for an integer $k \ge 1$. Then 

$$M^{k+1} = M^k M = \begin{bmatrix} 1 & k & \frac{k(k+1)}{2} \\ 0 & 1 & k \\ 0 & 0 & 1 \end{bmatrix} \begin{bmatrix} 1 & 1 & 1 \\ 0 & 1 & 1 \\ 0 & 0 & 1 \end{bmatrix} = \begin{bmatrix} 1 & 1+k & 1+k+\frac{k(k+1)}{2} \\ 0 & 1 & 1+k \\ 0 & 0 & 1 \end{bmatrix}.$$

The entry at position (1,3) simplifies to $\frac{2+2k+k^2+k}{2} = \frac{k^2+3k+2}{2} = \frac{(k+1)(k+2)}{2}$. Thus, 

$$M^{k+1} = \begin{bmatrix} 1 & k+1 & \frac{(k+1)(k+2)}{2} \\ 0 & 1 & k+1 \\ 0 & 0 & 1 \end{bmatrix},$$

as desired. $\square$

---

**1.13.** A square matrix $A$ is _nilpotent_ if $A^k=0$ for some $k>0$. Prove that if $A$ is nilpotent, then $I+A$ is invertible. Do this by finding the inverse.

_Solution._ Consider the matrix $B = I - A + A^2 - \cdots + (-1)^{k-1}A^{k-1}$. It follows that the product 

$$(I+A)B = (I+A)(I - A + A^2 - \cdots + (-1)^{k-1}A^{k-1}).$$

This telescopes nicely into $I - (-A)^k = I - (-1)^k A^k$. By the nilpotent condition, $A^k=0$, and so this simplifies to $I - 0 = I$; thus, $I+A$ is invertible and its inverse is $B,$ as desired. $\square$
