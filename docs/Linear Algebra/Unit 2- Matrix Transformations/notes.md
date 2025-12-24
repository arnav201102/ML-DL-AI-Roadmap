# 📘 Linear Algebra — Unit 2: Matrix Transformations

## (Mathematics + Machine Learning Perspective)

---

## 0️⃣ Why This Unit Is Non-Negotiable for ML

In ML / DL:

* Every **dense layer** is a matrix transformation
* Every **convolution** is a structured matrix transformation
* Backpropagation = repeated application of **transposes**
* Feature collapse, dead neurons, vanishing gradients = **linear algebra failures**

So this unit answers one question:

> **How does a model reshape information space so learning becomes possible?**

---

## 1️⃣ Functions → Transformations → Linear Transformations

---

### 🔹 Function (Mathematical View)

A function maps elements from one set to another:

```
f: X → Y
```

In linear algebra:

```
f: ℝⁿ → ℝᵐ
```

---

### Example

```
f(x, y) = (2x + y, x − y)
```

---

### 🔹 Transformation (Geometric View)

A **transformation** maps vectors to vectors:

```
T(x⃗) = y⃗
```

Think:

* Input vector = point in space
* Output vector = new position

---

### 🔹 Linear Transformation (Formal Definition)

A transformation `T` is **linear** iff:

#### 1. Additivity

```
T(u⃗ + v⃗) = T(u⃗) + T(v⃗)
```

#### 2. Homogeneity

```
T(cu⃗) = cT(u⃗)
```

---

### Immediate Consequences

* Origin is fixed: `T(0) = 0`
* Lines remain lines
* Planes remain planes
* No bending or warping — only reshaping

---

### 🔹 ML Interpretation

Linearity means:

* Changes in input cause **proportional changes in output**
* Gradients are stable and predictable
* Optimization is tractable

This is **why neural networks are built from linear layers**.

---

## 2️⃣ Linear Transformations as Matrices

---

### 🔹 Fundamental Theorem

Every linear transformation can be written as:

```
T(x) = A x
```

Where:

* `A` is a matrix
* `x` is a vector

---

### 🔹 Why This Is True (Key Insight)

A linear transformation is completely defined by where it sends **basis vectors**.

In ℝ²:

```
e₁ = (1, 0)
e₂ = (0, 1)
```

If:

```
T(e₁) = a⃗
T(e₂) = b⃗
```

Then:

```
A = [ a⃗  b⃗ ]
```

---

### Example

```
T(1, 0) = (2, 1)
T(0, 1) = (−1, 3)
```

```
A = [  2  −1
       1   3 ]
```

```
T(x, y) = A · [x y]ᵀ
```

---

### 🔹 ML Interpretation

* **Columns of A** → how each input feature contributes
* **Rows of A** → what each neuron extracts

This is **feature recombination**, not just multiplication.

---

## 3️⃣ Common Linear Transformations (Math + ML Meaning)

---

### 🔹 Scaling

```
A = [ k  0
      0  k ]
```

**Math**

* Uniform stretch or shrink
* Area scales by `k²`

**ML**

* Feature amplification or attenuation
* Large values → exploding activations
* Small values → vanishing activations

---

### 🔹 Non-Uniform Scaling

```
[ a  0
  0  b ]
```

**ML Meaning**

* Unequal importance given to features
* Learned automatically during training

---

### 🔹 Rotation

```
R(θ) = [ cosθ  −sinθ
         sinθ   cosθ ]
```

**Math**

* Preserves length and angles
* Determinant = 1

**ML**

* Re-expressing data in a better basis
* PCA and whitening rely on rotations

---

### 🔹 Shear

```
[ 1  k
  0  1 ]
```

**ML**

* Mixing correlated features
* Creates interactions without changing volume

---

## 4️⃣ Matrix Multiplication = Composition of Transformations

---

### 🔹 Mathematical Meaning

If:

```
T₁(x) = A x
T₂(x) = B x
```

Then:

```
T₂(T₁(x)) = B A x
```

---

### 🔹 Order Matters

```
AB ≠ BA
```

This is **geometry**, not algebraic annoyance.

---

### 🔹 ML Interpretation

Stacking layers:

```
x → W₁x → W₂
```

Without activation:

```
W₂(W₁x) = (W₂W₁)x
```

➡️ Depth collapses
➡️ No expressive gain

This is why **nonlinearity is essential**.

---

## 5️⃣ Determinant — The Most Underrated ML Concept

---

### 🔹 Mathematical Definition (2×2)

```
det([a b; c d]) = ad − bc
```

---

### 🔹 Geometric Meaning

* |det(A)| = area / volume scaling
* Sign = orientation (reflection)
* Zero = collapse to lower dimension

---

### 🔹 ML Interpretation

| Determinant | ML Meaning            |
| ----------- | --------------------- |
| ≈ 1         | Information preserved |
| > 1         | Feature amplification |
| < 1         | Compression           |
| = 0         | Feature death         |
| < 0         | Sign inversion        |

---

### Example (Rank Collapse)

```
A = [1  1
     2  2]
```

```
det(A) = 0
```

**ML Meaning**

* Rows redundant
* Network loses capacity
* Gradients collapse

---

## 6️⃣ Inverse Transformations = Recoverability

---

### 🔹 Mathematical Definition

```
A⁻¹A = I  ⇔  det(A) ≠ 0
```

---

### 🔹 ML Meaning

> Can we reconstruct the input from this representation?

---

### Where This Matters

* Autoencoders
* Normalizing flows
* Whitening
* Change-of-variables in probability

---

### Example (Information Loss)

```
A = [1  0
     0  0]
```

One dimension erased → unrecoverable.

---

## 7️⃣ Transpose — The Engine of Backpropagation

---

### 🔹 Mathematical Property

```
(Ax) · y = x · (Aᵀy)
```

---

### 🔹 Backpropagation Rule

Forward:

```
y = Wx
```

Backward:

```
∂L/∂x = Wᵀ · ∂L/∂y
```

---

### 🔹 ML Interpretation

* Gradients flow through **transposes**
* Badly conditioned matrices distort gradients
* Orthogonal matrices preserve gradient norms

This explains:

* Vanishing gradients
* Exploding gradients
* Orthogonal initialization

---

## 8️⃣ Conditioning, Rank, and Training Stability

---

### 🔹 Rank

Rank = number of independent directions preserved.

Low rank → feature collapse → poor expressiveness.

---

### 🔹 Conditioning

```
κ(W) = σ_max / σ_min
```

Large κ:

* Unstable training
* Sensitive gradients

---

## 9️⃣ Bias — Breaking Linearity on Purpose

```
y = Wx + b
```

* Not linear (`T(0) ≠ 0`)
* Shifts decision boundaries
* Without bias, models are severely limited

---

## 🧠 Final Unified Mental Model

* **Matrix** = space reshaper
* **Determinant** = information survival score
* **Rank** = expressive capacity
* **Transpose** = gradient router
* **Inverse** = recoverability
* **Multiplication order** = architecture design

---

## 🔥 Core Truth

Linear algebra in ML is not abstract math.

It is:

> **Engineering how information moves, compresses, and survives under optimization pressure.**
