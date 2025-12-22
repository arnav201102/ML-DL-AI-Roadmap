# 📘 LINEAR ALGEBRA – UNIT 2

## Matrix Transformations (Math + ML Perspective)

---

## 1. Functions & Linear Transformations

### 1.1 Functions (Math)

A **function** maps inputs to outputs:

[
f: \mathbb{R}^n \rightarrow \mathbb{R}^m
]

Example:
[
f(x, y) = (x+y, 2y)
]

---

### 1.2 Linear Transformations (Formal Definition)

A function ( T: \mathbb{R}^n \rightarrow \mathbb{R}^m ) is **linear** if:

1. **Additivity**
  [
  T(u+v) = T(u) + T(v)
  ]

2. **Homogeneity**
  [
  T(cu) = cT(u)
  ]

⚠️ **Critical Rule**
[
T(0) = 0
]

If violated → **not linear**

---

### 1.3 Why Linearity Matters in ML

* Gradient descent assumes proportional change
* Backprop relies on linear approximations
* Optimization breaks if linearity assumptions fail

---

### 1.4 Non-Linear Example (NOT Linear)

[
T(x, y) = (x+1, y)
]

Fails:
[
T(0,0) \neq (0,0)
]

➡ Bias terms are added **explicitly**, not inside linear transforms.

---

## 2. Matrix Transformations

### 2.1 Every Linear Transformation = Matrix

**Theorem:**
Every linear transformation can be written as:

[
T(x) = Ax
]

Where:

* (A) is a matrix
* (x) is a vector

---

### 2.2 Columns = Where Basis Goes

For matrix:
[
A =
\begin{bmatrix}
a & b \
c & d
\end{bmatrix}
]

* Column 1 = where ((1,0)) goes
* Column 2 = where ((0,1)) goes

Every vector is built from these.

---

### 2.3 Example

[
A =
\begin{bmatrix}
2 & 1 \
1 & 3
\end{bmatrix}
]

[
x = \begin{bmatrix} 1 \ 2 \end{bmatrix}
]

[
Ax =
\begin{bmatrix}
4 \
7
\end{bmatrix}
]

---

### 2.4 ML Interpretation

* **Rows** → learned features (neurons)
* **Columns** → input feature influence
* Matrix multiplication = **feature mixing**

---

## 3. Transformations & Matrix Multiplication

### 3.1 Composition of Transformations

If:
[
T_1(x) = A x,\quad T_2(x) = B x
]

Then:
[
T_2(T_1(x)) = B(Ax) = (BA)x
]

⚠️ **Order matters**
[
BA \neq AB
]

---

### 3.2 ML Interpretation

Multiple linear layers without activation:

[
y = W_3(W_2(W_1x)) = (W_3W_2W_1)x
]

➡ Collapses into **one matrix**
➡ Depth useless without nonlinearity

---

## 4. Inverse Transformations

### 4.1 Inverse Definition

Matrix (A) is invertible if:

[
A^{-1}A = I
]

---

### 4.2 When Inverse Exists

✔ Square matrix
✔ Determinant ≠ 0
✔ Full rank

---

### 4.3 ML Meaning

* Invertible = no information loss
* Used in:

* Normalizing flows
* Reversible networks
* Change of variables in probability

---

### 4.4 Non-Invertible Example

[
A =
\begin{bmatrix}
1 & 1 \
2 & 2
\end{bmatrix}
]

Rows dependent → infinite inputs map to same output.

---

## 5. Determinant (EXTREMELY IMPORTANT)

### 5.1 Mathematical Meaning

For 2×2 matrix:
[
\det(A) = ad - bc
]

---

### 5.2 Geometric Meaning

| Determinant | Meaning          |
| ----------- | ---------------- |
| > 1         | Volume expands   |
| = 1         | Volume preserved |
| < 1         | Volume shrinks   |
| = 0         | Space collapses  |
| < 0         | Reflection       |

---

### 5.3 ML Meaning

* Measures **information survival**
* Used in:

* Probability density transformation
* Flow models
* Jacobians

---

### 5.4 Change of Variables Formula

[
p_Y(y) = p_X(x)\left|\det\left(\frac{dx}{dy}\right)\right|
]

---

## 6. Rank (Model Capacity)

### 6.1 Definition

Rank = number of **independent directions**

---

### 6.2 Example

[
A =
\begin{bmatrix}
1 & 1 \
2 & 2
\end{bmatrix}
]

Rank = 1 (not 2)

---

### 6.3 ML Meaning

* Rank = expressive power
* Low rank = feature collapse
* High rank = richer representations

---

## 7. Transpose

### 7.1 Definition

[
(A^T)*{ij} = A*{ji}
]

---

### 7.2 Why Transpose Appears in Backprop

Forward:
[
y = Wx
]

Backward:
[
\frac{\partial L}{\partial x} = W^T \frac{\partial L}{\partial y}
]

Transpose routes gradients correctly.

---

## 8. Why Linear Algebra is ML’s Backbone

| Concept     | ML Role          |
| ----------- | ---------------- |
| Matrix      | Feature mixing   |
| Determinant | Information flow |
| Rank        | Capacity         |
| Inverse     | Recoverability   |
| Transpose   | Gradient routing |
| Eigenvalues | Stability        |

---

# ❓ QUESTIONS + HOTS (WITH EXAMPLES & ANSWERS)

---

## Q1

Why does `T(x)=Ax+b` break linearity but still used in ML?

**Answer:**
Bias breaks linearity mathematically but adds flexibility. ML separates linear part and bias explicitly.

---

## Q2

Why do two linear layers without activation behave as one?

**Answer:**
Matrix multiplication merges them.

---

## Q3

If determinant = 0, what ML failure occurs?

**Answer:**
Information loss → features collapse → poor learning.

---

## Q4

Why does PCA rotate data?

**Answer:**
To align axes with maximum variance.

---

## Q5

Why does backprop use transpose, not inverse?

**Answer:**
Inverse rescales; transpose redistributes gradients correctly.

---

## HOTS 1

Two neurons learn proportional weights. Effect?

**Answer:**
Rank collapse → wasted neurons.

---

## HOTS 2

Why do exploding gradients relate to eigenvalues > 1?

**Answer:**
Repeated multiplication amplifies values exponentially.

---

## HOTS 3

Why are orthogonal matrices used in deep nets?

**Answer:**
They preserve vector norms → stable gradients.

---

## HOTS 4

Why does low-rank approximation help generalization?

**Answer:**
Removes noise and redundant directions.

---

## HOTS 5 (MASTER)

Explain deep learning in one sentence using linear algebra.

**Answer:**
Deep learning is repeated, learned reshaping of data space to make patterns linearly separable.

---

## FINAL TRUTH

If you truly understand:

* determinant = information survival
* rank = capacity
* transpose = gradient flow
