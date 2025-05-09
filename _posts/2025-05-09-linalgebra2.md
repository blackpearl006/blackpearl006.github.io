---
layout: post
title: Understanding Linear Algebra - Part 2
date: 2025-05-10
description: Exploring the power of determinants and inverse matrices in solving systems of equations.
tags: linear-algebra charts
categories: mathematics
chart:
  chartjs: true
---

In the first part of this series, we explored the **row picture**, **column picture**, and **matrix form** of a system of equations, along with the **elimination method**. In this post, we will dive into **determinants**, **inverse matrices**, and their applications in solving systems of equations.

---

## Determinants

The determinant is a scalar value that can be computed from the elements of a square matrix. It provides important information about the matrix, such as whether it is invertible.

### Determinant of a 2x2 Matrix

For a 2x2 matrix:

$$
A = \begin{bmatrix}
a & b \\
c & d
\end{bmatrix}
$$

The determinant is calculated as:

$$
\text{det}(A) = ad - bc
$$

### Example: Determinant of a Matrix

Consider the matrix:

$$
A = \begin{bmatrix}
1 & 2 \\
3 & 4
\end{bmatrix}
$$

The determinant is:

$$
\text{det}(A) = (1)(4) - (2)(3) = 4 - 6 = -2
$$

Since the determinant is non-zero, the matrix is invertible.

---

## Inverse Matrices

The inverse of a square matrix \( A \) is a matrix \( A^{-1} \) such that:

$$
A A^{-1} = A^{-1} A = I
$$

Where \( I \) is the identity matrix.

### Formula for the Inverse of a 2x2 Matrix

For a 2x2 matrix:

$$
A = \begin{bmatrix}
a & b \\
c & d
\end{bmatrix}
$$

If \( \text{det}(A) \neq 0 \), the inverse is given by:

$$
A^{-1} = \frac{1}{\text{det}(A)} \begin{bmatrix}
d & -b \\
-c & a
\end{bmatrix}
$$

### Example: Inverse of a Matrix

Using the matrix \( A \) from the previous example:

$$
A = \begin{bmatrix}
1 & 2 \\
3 & 4
\end{bmatrix}
$$

The determinant is \( -2 \). The inverse is:

$$
A^{-1} = \frac{1}{-2} \begin{bmatrix}
4 & -2 \\
-3 & 1
\end{bmatrix}
= \begin{bmatrix}
-2 & 1 \\
1.5 & -0.5
\end{bmatrix}
$$

---

## Solving Systems of Equations Using Inverse Matrices

A system of equations can be written in matrix form as:

$$
AX = B
$$

Where \( A \) is the coefficient matrix, \( X \) is the column vector of variables, and \( B \) is the column vector of constants. If \( A \) is invertible, the solution is:

$$
X = A^{-1}B
$$

### Example: Solving a System Using the Inverse

Consider the system:

$$
\begin{aligned}
x + 2y &= 5 \\
3x + 4y &= 6
\end{aligned}
$$

In matrix form:

$$
\begin{bmatrix}
1 & 2 \\
3 & 4
\end{bmatrix}
\begin{bmatrix}
x \\
y
\end{bmatrix}
=
\begin{bmatrix}
5 \\
6
\end{bmatrix}
$$

The inverse of \( A \) is:

$$
A^{-1} = \begin{bmatrix}
-2 & 1 \\
1.5 & -0.5
\end{bmatrix}
$$

Multiply \( A^{-1} \) by \( B \):

$$
X = A^{-1}B = \begin{bmatrix}
-2 & 1 \\
1.5 & -0.5
\end{bmatrix}
\begin{bmatrix}
5 \\
6
\end{bmatrix}
= \begin{bmatrix}
-4 \\
4.5
\end{bmatrix}
$$

The solution is \( x = -4, y = 4.5 \).

---

## Visualizing Determinants with Chart.js

The determinant of a 2x2 matrix can be visualized as the area of a parallelogram formed by its column vectors.

```chartjs
{
  "type": "scatter",
  "data": {
    "datasets": [
      {
        "label": "Vector 1",
        "data": [{ "x": 1, "y": 3 }],
        "backgroundColor": "rgba(75,192,192,1)"
      },
      {
        "label": "Vector 2",
        "data": [{ "x": 2, "y": 4 }],
        "backgroundColor": "rgba(255,99,132,1)"
      }
    ]
  },
  "options": {
    "scales": {
      "x": { "type": "linear", "position": "bottom" },
      "y": { "type": "linear" }
    }
  }
}
```

---

In the next part, we will explore **eigenvalues**, **eigenvectors**, and their significance in linear transformations.