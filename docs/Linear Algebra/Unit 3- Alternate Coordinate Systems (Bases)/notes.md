# 📘 LINEAR ALGEBRA — UNIT 3

## Alternate Coordinate Systems (Bases)

### *Fully Explained with Examples + ML Interpretation*

---

## 1. Coordinate Systems & Bases (FROM ZERO)

---

### 1.1 What Is a Coordinate System?

A **coordinate system** is a way to **describe a vector using numbers relative to chosen axes**.

**Example (2D):**

```text
v = (3, 2)
```

Meaning:

* Move 3 units along the x-axis
* Move 2 units along the y-axis

⚠️ These numbers **depend entirely on the chosen axes**.

---

### 1.2 What Is a Basis? (VERY IMPORTANT)

A **basis** is a set of vectors that:

1. Can build **every vector** in the space
2. Represent vectors **uniquely**

Mathematically, a basis must:

* Be **linearly independent**
* **Span the space**

---

### 1.3 Standard Basis (Default Coordinates)

In ( \mathbb{R}^2 ):

```math
e_1 = (1,0), \quad e_2 = (0,1)
```

Any vector:

```math
v = (x,y) = x e_1 + y e_2
```

---

### 1.4 Alternate Basis (KEY IDEA)

Choose a **different basis**:

```math
b_1 = (1,1), \quad b_2 = (1,-1)
```

Same vector:

```math
v = (2,0)
```

Solve:

```math
v = c_1 b_1 + c_2 b_2
```

```math
(2,0) = c_1(1,1) + c_2(1,-1)
```

Solution:

```math
c_1 = 1, \quad c_2 = 1
```

➡ Same vector
➡ Different coordinates
➡ Different meaning

---

### 1.5 ML Interpretation (CRITICAL)

* **Features = coordinates**
* Changing basis = redefining features
* ML tries to find a basis where **patterns become simple**

> PCA, embeddings, attention = **basis transformations**

---

## 2. Orthogonality (Explained Properly)

---

### 2.1 Dot Product (Why Orthogonality Exists)

```math
u \cdot v = |u||v|\cos\theta
```

If:

```math
u \cdot v = 0 \Rightarrow \theta = 90^\circ
```

➡ Vectors are **orthogonal**

---

### 2.2 Why Orthogonality Matters

Orthogonal directions:

* Do not interfere
* Carry independent information
* Are numerically stable

---

### 2.3 Example

```math
u = (1,1), \quad v = (1,-1)
```

```math
u \cdot v = 1 - 1 = 0
```

They measure **different aspects of space**.

---

### 2.4 ML Interpretation

* Uncorrelated features
* Independent signals
* Easier optimization

---

## 3. Orthogonal Complement (Fully Explained)

---

### 3.1 Definition

For a subspace ( S ), its **orthogonal complement** ( S^\perp ) contains all vectors **perpendicular to S**.

---

### 3.2 Example

```math
S = \text{span}\{(1,1)\}
```

Condition:

```math
(x,y)\cdot(1,1)=0 \Rightarrow x+y=0
```

```math
S^\perp = \text{span}\{(1,-1)\}
```

---

### 3.3 Decomposition Theorem

Every vector ( v ) decomposes uniquely:

```math
v = v_S + v_{S^\perp}
```

Interpretation:

* Signal + noise
* Relevant + irrelevant
* Explained + unexplained

---

### 3.4 ML Interpretation

* PCA splits variance into:

  * principal components
  * orthogonal residuals
* Regression error lies in the orthogonal complement

---

## 4. Orthogonal Projections (Step-by-Step)

---

### 4.1 Projection Onto a Vector

```math
\text{proj}_u(x) = \frac{x \cdot u}{u \cdot u} u
```

---

### 4.2 Example

```math
x = (3,1), \quad u = (1,1)
```

```math
x \cdot u = 4, \quad u \cdot u = 2
```

```math
\text{proj}_u(x) = 2(1,1) = (2,2)
```

---

### 4.3 Meaning

* Closest point to ( x ) on the line
* Minimizes squared distance

---

### 4.4 Projection Onto a Subspace (Matrix Form)

```math
P = A(A^TA)^{-1}A^T
```

```math
\hat{x} = Px
```

---

### 4.5 ML Example (Linear Regression)

```math
\hat{y} = X(X^TX)^{-1}X^Ty
```

➡ Prediction = **projection**
➡ Error ⟂ feature space

---

## 5. Change of Basis (EXPLICIT)

---

### 5.1 Basis Matrix

```math
B = [b_1 \; b_2]
```

```math
v = B[v]_B
```

---

### 5.2 Coordinate Conversion

```math
[v]_B = B^{-1}v
```

---

### 5.3 Example

```math
B = \begin{bmatrix}1 & 1 \\ 1 & -1\end{bmatrix}, \quad v = \begin{bmatrix}2 \\ 0\end{bmatrix}
```

```math
[v]_B = \begin{bmatrix}1 \\ 1\end{bmatrix}
```

---

### 5.4 ML Interpretation

| Technique  | Meaning              |
| ---------- | -------------------- |
| PCA        | Rotate axes          |
| Whitening  | Rescale axes         |
| Embeddings | Semantic coordinates |

---

## 6. Orthonormal Bases (Why ML Loves Them)

---

### 6.1 Definition

```math
q_i \cdot q_j = \begin{cases}1 & i=j \\ 0 & i \neq j\end{cases}
```

---

### 6.2 Coordinate Extraction

```math
c_i = v \cdot q_i
```

No inverse. No instability.

---

### 6.3 ML Meaning

* Stable gradients
* Fast computation
* Better conditioning

---

## 7. Gram–Schmidt (Fully Worked)

---

### 7.1 Input Vectors

```math
v_1=(1,1), \quad v_2=(1,0)
```

---

### 7.2 Step 1

```math
u_1 = v_1
```

---

### 7.3 Step 2

```math
u_2 = v_2 - \text{proj}_{u_1}(v_2)
```

```math
\text{proj}_{u_1}(v_2)=\frac{1}{2}(1,1)
```

```math
u_2=(0.5,-0.5)
```

---

### 7.4 Normalize

```math
q_1=\frac{1}{\sqrt2}(1,1), \quad q_2=\frac{1}{\sqrt2}(1,-1)
```

---

### 7.5 ML Interpretation

* QR decomposition
* Used in PCA & optimization
* Removes correlation stepwise

---

## 8. Eigen-Everything (DETAILED)

---

### 8.1 Eigen Definition

```math
Av = \lambda v
```

Direction unchanged, only scaled.

---

### 8.2 Example

```math
A = \begin{bmatrix}2 & 0 \\ 0 & 1\end{bmatrix}
```

Eigenvectors:

```math
(1,0), (0,1)
```

Eigenvalues:

```math
2, 1
```

---

### 8.3 PCA Explained

1. Covariance:

```math
\Sigma = \frac{1}{n}X^TX
```

2. Eigenvectors → directions of max variance
3. Eigenvalues → variance magnitude

---

### 8.4 ML Stability

| Eigenvalue | Effect              |
| ---------- | ------------------- |
| >1         | Exploding gradients |
| <1         | Vanishing gradients |
| =1         | Stable              |

---

## FINAL ML INSIGHT

> **Machine learning = choosing and refining coordinate systems where data becomes simple**
