---
layout: post
title: Understanding Linear Algebra - Part 1
date: 2025-05-09
description: A deep dive into the fundamentals of linear algebra using advanced visualization techniques.
tags: linear-algebra charts
categories: mathematics
chart:
  chartjs: true
---

Linear algebra is the foundation of many fields, from computer graphics to machine learning. In this post, we will explore the **row picture**, **column picture**, and **matrix form** of a system of equations. We'll also dive into the **elimination method** with detailed examples.

---

## Row Picture, Column Picture, and Matrix Form

A system of linear equations can be visualized in three ways:

1. **Row Picture**: Each equation is represented as a line in a 2D plane.
2. **Column Picture**: The system is expressed as a combination of column vectors.
3. **Matrix Form**: The system is written compactly as a matrix equation.

### Example System of Equations

Consider the system:

$$
\begin{aligned}
x + 2y &= 5 \\
3x + 4y &= 6
\end{aligned}
$$

---

### Row Picture

In the row picture, each equation is a line in the 2D plane. The solution is the intersection of these lines.

```chartjs
{
  "type": "line",
  "data": {
    "labels": [-10, -5, 0, 5, 10],
    "datasets": [
      {
        "label": "x + 2y = 5",
        "data": [
          { "x": -10, "y": 7.5 },
          { "x": 10, "y": -2.5 }
        ],
        "borderColor": "rgba(75,192,192,1)",
        "fill": false
      },
      {
        "label": "3x + 4y = 6",
        "data": [
          { "x": -10, "y": 9 },
          { "x": 10, "y": -6 }
        ],
        "borderColor": "rgba(255,99,132,1)",
        "fill": false
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

### Column Picture

In the column picture, the system is written as:

$$
x \begin{bmatrix} 1 \\ 3 \end{bmatrix} + y \begin{bmatrix} 2 \\ 4 \end{bmatrix} = \begin{bmatrix} 5 \\ 6 \end{bmatrix}
$$

This means we are looking for a linear combination of the column vectors that equals the right-hand side vector.

---

### Matrix Form

The system can also be written compactly as:

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

---

## Elimination Method

The elimination method transforms the system into an equivalent one that is easier to solve. The goal is to eliminate one variable to solve for the other.

### Example 1: Solving the System

1. Start with the system:
   $$
   \begin{aligned}
   x + 2y &= 5 \\
   3x + 4y &= 6
   \end{aligned}
   $$

2. Multiply the first equation by 3:
   $$
   3x + 6y = 15
   $$

3. Subtract the second equation:
   $$
   (3x + 6y) - (3x + 4y) = 15 - 6 \\
   2y = 9 \implies y = 4.5
   $$

4. Substitute \( y = 4.5 \) into the first equation:
   $$
   x + 2(4.5) = 5 \implies x = -4
   $$

The solution is \( x = -4, y = 4.5 \).

---

### Example 2: Another System

Solve the system:

$$
\begin{aligned}
2x + y &= 8 \\
x - y &= 2
\end{aligned}
$$

1. Add the equations:
   $$
   (2x + y) + (x - y) = 8 + 2 \\
   3x = 10 \implies x = \frac{10}{3}
   $$

2. Substitute \( x = \frac{10}{3} \) into the second equation:
   $$
   \frac{10}{3} - y = 2 \implies y = \frac{4}{3}
   $$

The solution is \( x = \frac{10}{3}, y = \frac{4}{3} \).

---

In the next part, we will explore **determinants**, **inverse matrices**, and their applications in solving systems of equations.