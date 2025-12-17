# 📘 Practice Questions – Linear Dependence & Independence

*(With Detailed Answers)*

---

## 🔹 BASIC

---

### **1. What does it mean for a set of vectors to be linearly independent?**

A set of vectors ( {v_1, v_2, \dots, v_k} ) is **linearly independent** if:
[
a_1 v_1 + a_2 v_2 + \dots + a_k v_k = \vec{0}
\Rightarrow a_1 = a_2 = \dots = a_k = 0
]

**Meaning:**
No vector can be written using the others.

---

### **2. Define linear dependence.**

A set of vectors is **linearly dependent** if **at least one vector can be expressed as a linear combination of the others**.

Equivalently:
[
\exists\ \text{non-zero scalars such that } a_1 v_1 + \dots + a_k v_k = \vec{0}
]

---

### **3. Give an example of a linearly independent set in ( \mathbb{R}^2 ).**

[
(1,0),\ (0,1)
]

Neither vector is a scalar multiple of the other.

---

### **4. Give an example of a linearly dependent set in ( \mathbb{R}^2 ).**

[
(1,2),\ (2,4)
]

Because:
[
(2,4) = 2(1,2)
]

---

### **5. What role does the zero vector play in dependence?**

Any set containing the zero vector is **always linearly dependent**.

Reason:
[
1 \cdot \vec{0} = \vec{0}
]

---

## 🔹 INTERMEDIATE

---

### **6. How many linearly independent vectors can exist in ( \mathbb{R}^n )?**

At most **n** linearly independent vectors.

**Why?**
Because ( \mathbb{R}^n ) has only ( n ) independent directions.

---

### **7. Are vectors (1,2,3) and (2,4,6) independent?**

❌ **No.**

[
(2,4,6) = 2(1,2,3)
]

They lie on the same line in ( \mathbb{R}^3 ).

---

### **8. Can two dependent vectors still span a space?**

✅ **Yes**, but with redundancy.

Example:
[
(1,0),(2,0)
]
They span the x-axis, but one is unnecessary.

---

### **9. What happens to span when dependent vectors are removed?**

The **span remains unchanged**.

Removing dependent vectors simplifies the set without losing reach.

---

### **10. How does independence ensure uniqueness of representation?**

If vectors are independent, every vector in the span has a **unique linear combination**.

Dependence causes **multiple representations**.

---

## 🔹 ADVANCED

---

### **11. Prove that a set containing the zero vector is linearly dependent.**

Let ( \vec{0} ) be in the set.

Then:
[
1 \cdot \vec{0} = \vec{0}
]

This is a non-trivial solution → the set is dependent.

---

### **12. Determine if vectors (1,2,3), (0,1,1), (1,3,4) are independent.**

Check:
[
(1,3,4) = (1,2,3) + (0,1,1)
]

Since one vector is a sum of others → ❌ **dependent**.

---

### **13. Why does linear dependence imply infinite solutions to a system?**

Because redundancy allows multiple coefficient combinations to produce the same result.

**Geometric view:**
Overlapping directions collapse constraints.

---

### **14. Explain the relationship between independence and matrix rank.**

Rank equals the number of **independent rows or columns**.

Dependent rows/columns do not increase rank.

---

### **15. Why is independence required for a basis?**

A basis must:

* Span the space
* Have **no redundancy**

Thus, independence is mandatory.
