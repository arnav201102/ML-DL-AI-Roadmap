
# Practice Questions – Vectors & Spaces

---

## Basic

1. Define a vector.
2. What is a zero vector?
3. Write a linear combination of (1,2) and (2,1).
4. Is (0,0) linearly independent?
5. What does span mean?

---

## Intermediate

6. Do vectors (1,2) and (2,4) form an independent set?
7. Find the span of vector (1,0).
8. Can three vectors be independent in \( \mathbb{R}^2 \)?
9. Write a dependent equation using vectors.
10. Explain closure under addition.

---

## Advanced

11. Prove that a set containing the zero vector is dependent.
12. Determine if vectors (1,2,3), (2,4,6), (3,6,9) are independent.
13. Can two vectors span \( \mathbb{R}^3 \)? Justify.
14. Explain how span relates to solution spaces.
15. Give a real-world example of linear combination.

---

## Challenge

16. If span(v1, v2) = span(v1, v3), what can you infer?
17. Design a dependent set of 3 vectors in \( \mathbb{R}^3 \).
18. How many vectors are needed to span \( \mathbb{R}^n \)?


## **Detailed Answers**

---

## 🔵 Basic

---

### **1. Define a vector.**

A **vector** is a mathematical object that has:

* **Magnitude** (length)
* **Direction**

It is commonly represented as an ordered tuple, e.g. ( (x, y) ) or ( (x, y, z) ).

**Geometric meaning:** displacement in space
**Algebraic meaning:** element of a vector space

---

### **2. What is a zero vector?**

The **zero vector** is a vector whose all components are zero.

Examples:

* ( (0,0) ) in ( \mathbb{R}^2 )
* ( (0,0,0) ) in ( \mathbb{R}^3 )

**Properties:**

* Magnitude = 0
* No direction
* Acts as the additive identity:
  [
  \vec{v} + \vec{0} = \vec{v}
  ]

---

### **3. Write a linear combination of (1,2) and (2,1).**

A linear combination is:
[
a(1,2) + b(2,1)
]

Example:
[
2(1,2) + 3(2,1) = (2,4) + (6,3) = (8,7)
]

**General form:**
[
(a + 2b,; 2a + b)
]

---

### **4. Is (0,0) linearly independent?**

❌ **No.**

A single vector is independent **only if it is non-zero**.

Because:
[
1 \cdot (0,0) = (0,0)
]
with a **non-zero coefficient**, violating independence.

**Rule:**

> Any set containing the zero vector is linearly dependent.

---

### **5. What does span mean?**

The **span** of vectors is the set of **all linear combinations** of those vectors.

Example:
[
\text{span}{(1,0)} = {(t,0) \mid t \in \mathbb{R}}
]

**Intuition:**
Span tells you **what positions you can reach** using given directions.

---

## 🔵 Intermediate

---

### **6. Do vectors (1,2) and (2,4) form an independent set?**

❌ **No, they are dependent.**

Because:
[
(2,4) = 2(1,2)
]

One vector is a scalar multiple of the other → **same direction**.

---

### **7. Find the span of vector (1,0).**

[
\text{span}{(1,0)} = {(t,0) \mid t \in \mathbb{R}}
]

This is the **x-axis**.

**Conclusion:**
One non-zero vector spans a **line through the origin**.

---

### **8. Can three vectors be independent in ( \mathbb{R}^2 )?**

❌ **No.**

Maximum number of independent vectors in ( \mathbb{R}^n ) is **n**.

So in ( \mathbb{R}^2 ), at most **2 independent vectors**.

---

### **9. Write a dependent equation using vectors.**

Example:
[
(2,4) - 2(1,2) = (0,0)
]

Here, coefficients are **not all zero**, but result is zero → dependence.

---

### **10. Explain closure under addition.**

Closure under addition means:
[
\vec{u}, \vec{v} \in V \Rightarrow \vec{u} + \vec{v} \in V
]

Example:
If ( (1,2) ) and ( (3,4) ) are in ( \mathbb{R}^2 ),
[
(1,2) + (3,4) = (4,6) \in \mathbb{R}^2
]

This is a **key vector space property**.

---

## 🔵 Advanced

---

### **11. Prove that a set containing the zero vector is dependent.**

Let the set contain ( \vec{0} ).

Consider:
[
1 \cdot \vec{0} = \vec{0}
]

This is a linear combination equaling zero with a **non-zero coefficient**.

Therefore, the set is **linearly dependent**.

---

### **12. Determine if vectors (1,2,3), (2,4,6), (3,6,9) are independent.**

Check relationships:
[
(2,4,6) = 2(1,2,3)
]
[
(3,6,9) = 3(1,2,3)
]

All are scalar multiples of one vector.

❌ **They are linearly dependent.**

---

### **13. Can two vectors span ( \mathbb{R}^3 )? Justify.**

❌ **No.**

To span ( \mathbb{R}^3 ), you need **three independent vectors**.

Two vectors at best span:

* A plane (if independent)
* A line (if dependent)

---

### **14. Explain how span relates to solution spaces.**

In systems of equations:

* Solutions exist **only if the target vector lies in the span** of column vectors.

**Geometric meaning:**
You can solve the system only if you can *reach* the output using inputs.

---

### **15. Give a real-world example of linear combination.**

**Physics:**
Net force = sum of forces acting on an object

[
\vec{F}_{net} = a\vec{F}_1 + b\vec{F}_2
]

**ML:**
Predictions are weighted sums of features.

---

## 🔵 Challenge

---

### **16. If span(v₁, v₂) = span(v₁, v₃), what can you infer?**

( v_3 ) lies in the span of ( v_1 ) and ( v_2 ), and vice versa.

This implies **no new direction is added**.

**Conclusion:**
The vectors are **linearly dependent or equivalent in span power**.

---

### **17. Design a dependent set of 3 vectors in ( \mathbb{R}^3 ).**

Example:
[
(1,0,0),; (0,1,0),; (1,1,0)
]

Because:
[
(1,1,0) = (1,0,0) + (0,1,0)
]

---

### **18. How many vectors are needed to span ( \mathbb{R}^n )?**

Minimum required: **n linearly independent vectors**.

This set is called a **basis** of ( \mathbb{R}^n ).

---

## 🧠 Final Revision Line

> **Independence removes redundancy, span defines reach, and dimension limits freedom.**
