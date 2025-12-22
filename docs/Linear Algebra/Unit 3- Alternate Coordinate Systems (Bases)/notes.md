# 📘 LINEAR ALGEBRA — UNIT 3

## Alternate Coordinate Systems (Bases)

### (Fully Explained with Examples + ML Interpretation)

---

## 1. Coordinate Systems & Bases (FROM ZERO)

---

### 1.1 What Is a Coordinate System?

A **coordinate system** is simply a way to **describe a vector using numbers**.

Example in 2D:

* Vector ( v = (3, 2) )
* Means:

* Move 3 units along x-axis
* Move 2 units along y-axis

This description depends entirely on the **axes you chose**.

---

### 1.2 What Is a Basis? (Very Important)

A **basis** is a set of vectors that:

1. Can build **every vector** in the space
2. Do so **uniquely**

Mathematically, a basis:

* Must be **linearly independent**
* Must **span the space**

---

### 1.3 Standard Basis (Default Coordinates)

In ( \mathbb{R}^2 ):

[
e_1 = (1,0), \quad e_2 = (0,1)
]

Any vector:
[
v = (x,y) = x e_1 + y e_2
]

---

### 1.4 Alternate Basis (Key Idea)

Now choose a **different basis**:

[
b_1 = (1,1), \quad b_2 = (1,-1)
]

Same vector ( v = (2,0) )

Solve:
[
v = c_1 b_1 + c_2 b_2
]

[
(2,0) = c_1(1,1) + c_2(1,-1)
]

Solution:
[
c_1 = 1,; c_2 = 1
]

➡ Same vector
➡ Different coordinates
➡ Different meaning

---

### 1.5 ML Interpretation (CRITICAL)

* **Features are coordinates**
* Changing basis = redefining features
* ML tries to **discover a basis where patterns are simple**

> PCA, embeddings, attention = basis changes

---

## 2. Orthogonality (Explained Properly)

---

### 2.1 Dot Product (Why Orthogonality Exists)

Dot product:
[
u \cdot v = |u||v|\cos\theta
]

If:
[
u \cdot v = 0
\Rightarrow \cos\theta = 0
\Rightarrow \theta = 90^\circ
]

➡ Vectors are **orthogonal**

---

### 2.2 Why Orthogonality Matters

Orthogonal directions:

* Do not interfere
* Carry independent information
* Are numerically stable

---

### 2.3 Example

[
u = (1,1),\quad v = (1,-1)
]

[
u \cdot v = 1 - 1 = 0
]

They measure **different aspects** of space.

---

### 2.4 ML Interpretation

* Uncorrelated features
* Independent signals
* Easier optimization

---

## 3. Orthogonal Complement (Fully Explained)

---

### 3.1 Definition

Given a subspace ( S ), its **orthogonal complement** ( S^\perp ) contains **all vectors perpendicular to S**.

---

### 3.2 Example

Let:
[
S = \text{span}{(1,1)}
]

Any vector perpendicular satisfies:
[
(x,y)\cdot(1,1)=0
\Rightarrow x+y=0
]

So:
[
S^\perp = \text{span}{(1,-1)}
]

---

### 3.3 Decomposition Theorem

Every vector ( v ) can be written uniquely as:

[
v = v_S + v_{S^\perp}
]

Signal + noise
Relevant + irrelevant
Explained + unexplained

---

### 3.4 ML Interpretation

* PCA splits variance into:

* principal components
* orthogonal residuals
* Regression error lies in orthogonal complement

---

## 4. Orthogonal Projections (Step-by-Step)

---

### 4.1 Projection Onto a Vector

Project ( x ) onto ( u ):

[
\text{proj}_u(x) = \frac{x \cdot u}{u \cdot u} u
]

---

### 4.2 Example

[
x = (3,1),\quad u = (1,1)
]

[
x \cdot u = 4,\quad u \cdot u = 2
]

[
\text{proj}_u(x) = 2(1,1) = (2,2)
]

---

### 4.3 Meaning

* Closest point to ( x ) on the line
* Minimizes distance

---

### 4.4 Projection Onto a Subspace (Matrix Form)

Given basis matrix ( A ):

[
P = A(A^TA)^{-1}A^T
]

[
\hat{x} = Px
]

---

### 4.5 ML Example (Linear Regression)

[
\hat{y} = X(X^TX)^{-1}X^Ty
]

➡ Prediction is **projection**
➡ Error is orthogonal to features

---

## 5. Change of Basis (EXPLICIT)

---

### 5.1 Basis Matrix

Let:
[
B = [b_1; b_2]
]

Then:
[
v = B[v]_B
]

---

### 5.2 Coordinate Conversion

[
[v]_B = B^{-1}v
]

---

### 5.3 Example

[
B =
\begin{bmatrix}
1 & 1 \
1 & -1
\end{bmatrix}
,\quad
v =
\begin{bmatrix}
2\0
\end{bmatrix}
]

[
[v]_B =
\begin{bmatrix}
1\1
\end{bmatrix}
]

---

### 5.4 ML Interpretation

| Technique  | Meaning              |
| ---------- | -------------------- |
| PCA        | Rotate axes          |
| Whitening  | Rescale axes         |
| Embeddings | Semantic coordinates |

---

## 6. Orthonormal Bases (Why ML Loves Them)

---

### 6.1 Definition

[
q_i \cdot q_j =
\begin{cases}
1 & i=j \
0 & i\neq j
\end{cases}
]

---

### 6.2 Coordinate Extraction Becomes Easy

[
c_i = v \cdot q_i
]

No inverse
No instability

---

### 6.3 ML Meaning

* Stable gradients
* Fast computation
* Better conditioning

---

## 7. Gram–Schmidt (Fully Worked)

---

### 7.1 Input Vectors

[
v_1=(1,1),\quad v_2=(1,0)
]

---

### 7.2 Step 1

[
u_1 = v_1
]

---

### 7.3 Step 2

[
u_2 = v_2 - \text{proj}_{u_1}(v_2)
]

Compute:
[
\text{proj}_{u_1}(v_2)=\frac{1}{2}(1,1)
]

[
u_2 = (1,0)-(0.5,0.5)=(0.5,-0.5)
]

---

### 7.4 Normalize

[
q_1=\frac{1}{\sqrt2}(1,1),\quad q_2=\frac{1}{\sqrt2}(1,-1)
]

---

### 7.5 ML Interpretation

* QR decomposition
* Used in PCA, optimization
* Removes correlation stepwise

---

## 8. Eigen-Everything (DETAILED)

---

### 8.1 Eigen Definition

[
Av = \lambda v
]

Direction unchanged
Only scaled

---

### 8.2 Example

[
A =
\begin{bmatrix}
2 & 0\
0 & 1
\end{bmatrix}
]

Eigenvectors:
[
(1,0),\ (0,1)
]

Eigenvalues:
[
2,\ 1
]

---

### 8.3 PCA Explained Cleanly

1. Compute covariance:
  [
  \Sigma=\frac1n X^TX
  ]

2. Eigenvectors → directions of max variance

3. Eigenvalues → amount of variance

---

### 8.4 ML Stability

| Eigenvalue | Effect              |
| ---------- | ------------------- |
| >1         | Exploding gradients |
| <1         | Vanishing gradients |
| =1         | Stable              |

---

## FINAL ML INSIGHT

> **Machine learning = choosing and refining coordinate systems where data becomes simple**
