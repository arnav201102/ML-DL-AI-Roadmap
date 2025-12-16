# 🔹 LESSON 1: VECTORS (COMPLETE)

## 1. Definition of a Vector

A **vector** is a quantity with:

* **Magnitude** (size)
* **Direction**

This is the defining idea.

### Scalars vs Vectors

| Quantity    | Type   |
| ----------- | ------ |
| Mass        | Scalar |
| Temperature | Scalar |
| Velocity    | Vector |
| Force       | Vector |

Mathematically:

* 2D → (x, y)
* 3D → (x, y, z)

---

## 2. Geometric Interpretation

A vector is an **arrow from the origin**.

* Length = magnitude
* Orientation = direction

Example:

* (3,4): move 3 right, 4 up

---

## 3. Vector Operations

### A. Addition

[
(x_1,y_1)+(x_2,y_2)=(x_1+x_2,y_1+y_2)
]

Example:
[
(1,2)+(3,4)=(4,6)
]

**Meaning:** Net movement.

---

### B. Scalar Multiplication

[
k(x,y)=(kx,ky)
]

Effects:

* |k| > 1 → stretch
* 0 < |k| < 1 → shrink
* k < 0 → reverse direction
* k = 0 → zero vector

---

## 4. Zero Vector

[
(0,0)
]

Properties:

* Magnitude = 0
* No direction
* Identity element: (v+0=v)

---

## 5. Magnitude

[
||v||=\sqrt{x^2+y^2}
]

Example:
[
||(6,8)||=10
]

---

## 6. Unit Vector

A vector of magnitude 1:
[
\hat{v}=\frac{v}{||v||}
]

Example:

* v = (3,4)
* Unit vector = (3/5, 4/5)

**Used in:** physics, ML normalization, graphics.

---

## 7. Important Properties

* Commutative: v + w = w + v
* Associative
* Distributive

These allow vectors to form **vector spaces** later.

---

## 8. Vector Spaces

A **vector space** is a set of vectors that satisfies:
1. Closure under addition
2. Closure under scalar multiplication
3. Additive identity exists
4. Additive inverses exist

### Examples
- \( \mathbb{R}^2, \mathbb{R}^3 \)
- Polynomials
- Matrices

### Non-examples
- Only positive vectors (not closed under scalar multiplication)
- Integers (not closed under division by scalars)

---

## 9. Common Mistakes

❌ Ignoring direction
❌ Treating vectors like numbers
❌ Mixing dimensions
❌ Trying to normalize zero vector

---

## Practice Questions (WITH SOLUTIONS)

### Q1. Find magnitude of (6,8)

[
\sqrt{36+64}=10
]

---

### Q2. Find unit vector of (3,4)

[
(3/5,4/5)
]

---

### Q3. Are (2,−3) and (−4,6) same or opposite direction?

[
(-4,6)=-2(2,-3)
]
Opposite direction.

---

### Q4. Is (0,0) a scalar multiple of every vector?

Yes:
[
0·v=(0,0)
]

---

### Q5. Can two vectors have same direction but not be equal?

Yes:

* (1,1) and (2,2)

---

## HOTS (ADVANCED) WITH SOLUTIONS

### HOTS 1

**Why can’t the zero vector represent direction?**
Because direction requires a nonzero magnitude.

---

### HOTS 2

**Why is normalization critical in ML?**
Because models depend on direction in feature space, not scale.

---

### HOTS 3 (Hard)

**Can two different vectors have same unit vector?**
Yes. Any scalar multiples share the same unit vector.

---