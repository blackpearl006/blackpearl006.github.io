---
layout: distill
title: Understanding Linear Algebra - Determinants and Their Properties
description: A detailed exploration of the 8 fundamental properties of determinants with examples and visualizations.
tags: linear-algebra determinants distill
date: 2025-05-11
featured: true
chart:
  chartjs: true
  vega_lite: true
  echarts: true
tikzjax: true
typograms: true
authors:
  - name: Ninad
    url: "https://github.com/blackpearl006"
toc:
  - name: Introduction
  - name: Property 1: Determinant of Identity Matrix
  - name: Property 2: Row Exchange and Sign Reversal
  - name: Property 3: Linear Transformations
  - name: Property 4: Equal Rows or Columns
  - name: Property 5: Row Operations and Elimination
  - name: Property 6: Row of Zeroes
  - name: Property 7: Upper Triangular Matrices
  - name: Property 8: Singular Matrices
---

Determinants are a fundamental concept in linear algebra, providing insights into matrix properties, linear transformations, and system solvability. In this post, we will explore the **8 key properties of determinants**, their significance, and examples to illustrate each property.

---

## Property 1: Determinant of the Identity Matrix

The determinant of the identity matrix \( I \) is always 1, regardless of its size.

### Example

For a 3x3 identity matrix:

$$
I = \begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
$$

The determinant is:

$$
\text{det}(I) = 1
$$

This property reflects that the identity matrix does not scale or distort space.

---

## Property 2: Row Exchange and Sign Reversal

If two rows (or columns) of a matrix are exchanged, the determinant changes its sign.

### Example

Consider the matrix:

$$
A = \begin{bmatrix}
1 & 2 \\
3 & 4
\end{bmatrix}
$$

The determinant is:

$$
\text{det}(A) = (1)(4) - (2)(3) = -2
$$

If we exchange the rows:

$$
A' = \begin{bmatrix}
3 & 4 \\
1 & 2
\end{bmatrix}
$$

The determinant becomes:

$$
\text{det}(A') = (3)(2) - (4)(1) = 2
$$

The sign has reversed.

---

## Property 3: Linear Transformations

If a row (or column) of a matrix is multiplied by a constant \( k \), the determinant is also multiplied by \( k \). However, adding a multiple of one row to another does not change the determinant.

### Example 1: Multiplying a Row by a Constant

For the matrix:

$$
A = \begin{bmatrix}
1 & 2 \\
3 & 4
\end{bmatrix}
$$

If we multiply the first row by 2:

$$
A' = \begin{bmatrix}
2 & 4 \\
3 & 4
\end{bmatrix}
$$

The determinant becomes:

$$
\text{det}(A') = 2 \cdot \text{det}(A) = 2 \cdot (-2) = -4
$$

### Example 2: Adding a Multiple of One Row to Another

If we add 3 times the first row to the second row:

$$
A'' = \begin{bmatrix}
1 & 2 \\
6 & 10
\end{bmatrix}
$$

The determinant remains unchanged:

$$
\text{det}(A'') = \text{det}(A) = -2
$$

---

## Property 4: Equal Rows or Columns

If two rows (or columns) of a matrix are identical, the determinant is 0.

### Example

For the matrix:

$$
A = \begin{bmatrix}
1 & 2 \\
1 & 2
\end{bmatrix}
$$

The determinant is:

$$
\text{det}(A) = (1)(2) - (2)(1) = 0
$$

This property reflects that the matrix is singular and does not represent a valid transformation.

---

## Property 5: Row Operations and Elimination

Subtracting a multiple of one row from another (as in Gaussian elimination) does not change the determinant.

### Example

For the matrix:

$$
A = \begin{bmatrix}
1 & 2 \\
3 & 4
\end{bmatrix}
$$

If we subtract 3 times the first row from the second row:

$$
A' = \begin{bmatrix}
1 & 2 \\
0 & -2
\end{bmatrix}
$$

The determinant remains:

$$
\text{det}(A') = \text{det}(A) = -2
$$

This property is crucial in solving systems of equations.

---

## Property 6: Row of Zeroes

If a matrix has a row (or column) of zeroes, its determinant is 0.

### Example

For the matrix:

$$
A = \begin{bmatrix}
1 & 2 \\
0 & 0
\end{bmatrix}
$$

The determinant is:

$$
\text{det}(A) = (1)(0) - (2)(0) = 0
$$

This property indicates that the matrix is singular.

---

## Property 7: Upper Triangular Matrices

For an upper triangular matrix, the determinant is the product of its diagonal elements.

### Example

For the matrix:

$$
A = \begin{bmatrix}
1 & 2 & 3 \\
0 & 4 & 5 \\
0 & 0 & 6
\end{bmatrix}
$$

The determinant is:

$$
\text{det}(A) = (1)(4)(6) = 24
$$

This property simplifies determinant calculations for triangular matrices.

---

## Property 8: Singular Matrices

If the determinant of a matrix is 0, the matrix is singular and non-invertible.

### Example

For the matrix:

$$
A = \begin{bmatrix}
1 & 2 \\
2 & 4
\end{bmatrix}
$$

The determinant is:

$$
\text{det}(A) = (1)(4) - (2)(2) = 0
$$

Since the determinant is 0, \( A \) is singular and does not have an inverse.

---

## Visualizing Determinants

The determinant can be visualized as the scaling factor of the area (2D) or volume (3D) of the space transformed by the matrix. Below is an interactive plot showing how the determinant changes with row operations:

```chartjs
{
  "type": "scatter",
  "data": {
    "datasets": [
      {
        "label": "Original Matrix",
        "data": [{ "x": 1, "y": 2 }, { "x": 3, "y": 4 }],
        "backgroundColor": "rgba(75,192,192,1)"
      },
      {
        "label": "Transformed Matrix",
        "data": [{ "x": 1, "y": 2 }, { "x": 3, "y": 6 }],
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

Determinants are a powerful tool in linear algebra, providing insights into matrix properties, transformations, and system solvability. In the next post, we will explore **eigenvalues**, **eigenvectors**, and their applications in understanding linear transformations.