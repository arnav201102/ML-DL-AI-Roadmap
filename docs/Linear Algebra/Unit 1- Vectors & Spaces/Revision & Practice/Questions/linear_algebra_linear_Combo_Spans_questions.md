# 📘 Practice Questions – Linear Combinations & Span

*(With Detailed Answers)*

---

## 🔹 BASIC

---

### **1. What is a linear combination?**

A **linear combination** of vectors ( v_1, v_2, \dots, v_k ) is any vector of the form:
[
a_1 v_1 + a_2 v_2 + \dots + a_k v_k
]
where ( a_1, a_2, \dots, a_k ) are scalars.

**Key idea:**
Only **addition and scalar multiplication** are allowed.

---

### **2. Give one linear combination of vectors (1,0) and (0,1).**

Example:
[
3(1,0) + 5(0,1) = (3,5)
]

This shows that **any vector in ( \mathbb{R}^2 )** can be formed using these two vectors.

---

### **3. What is meant by the span of a set of vectors?**

The **span** of a set of vectors is the set of **all possible linear combinations** of those vectors.

Formally:
[
\text{span}{v_1, v_2, \dots, v_k}
]

**Intuition:**
Span answers: *“What vectors can I build using these?”*

---

### **4. Does the span of any set always include the zero vector? Why?**

✅ **Yes.**

By choosing all scalars as zero:
[
0v_1 + 0v_2 + \dots + 0v_k = \vec{0}
]

So the zero vector is **always** in the span.

---

### **5. What does the span of a single non-zero vector look like geometrically?**

It is a **line through the origin** in the direction of the vector.

Example:
[
\text{span}{(2,3)} = {(2t,3t)}
]

---

## 🔹 INTERMEDIATE

---

### **6. Find the span of vectors (1,0) and (0,1).**

[
\text{span}{(1,0),(0,1)} = \mathbb{R}^2
]

**Reason:**
Any vector ( (x,y) ) can be written as:
[
x(1,0) + y(0,1)
]

---

### **7. Are vectors (1,2) and (2,4) enough to span ( \mathbb{R}^2 )?**

❌ **No.**

Because:
[
(2,4) = 2(1,2)
]

They lie on the same line, so their span is only a **line**, not the whole plane.

---

### **8. Can two vectors span the same space even if they are different?**

✅ **Yes.**

Example:
[
\text{span}{(1,0),(0,1)} = \text{span}{(1,1),(1,-1)}
]

Different vectors, same span → same space.

---

### **9. What happens to the span if a vector is removed from a dependent set?**

**Nothing changes.**

Dependent vectors are **redundant**, so removing them does not reduce the span.

---

### **10. Explain why span always passes through the origin.**

Linear combinations do not include constant terms.

Setting all scalars to zero gives the origin:
[
\vec{0} \in \text{span}
]

So the span **must pass through the origin**.

---

## 🔹 ADVANCED

---

### **11. Show that span(v₁, v₂) = span(v₁, v₂, v₁+v₂).**

Since:
[
v_1 + v_2 \in \text{span}(v_1, v_2)
]

Adding ( v_1 + v_2 ) introduces **no new direction**.

Thus both spans are equal.

---

### **12. Can a vector lie in the span of others but still be useful?**

Yes, but it is **not necessary**.

Such vectors:

* Do not increase dimension
* Can be removed without loss of span

They may still be used for **convenience**, but not for minimal representation.

---

### **13. How is span related to solutions of linear equations?**

A system:
[
Ax = b
]
has a solution **iff** ( b ) lies in the span of the columns of ( A ).

If ( b ) is outside the span → **no solution**.

---

### **14. Can a finite set of vectors span an infinite set? Explain.**

✅ **Yes.**

Example:
[
\text{span}{(1,0),(0,1)} = \mathbb{R}^2
]

Infinite vectors generated from just two vectors.

---

### **15. Why does span define the “capability” of a system?**

Because it describes **all achievable outputs** using allowed operations.

* In physics → reachable forces
* In ML → reachable predictions
* In CS → reachable states

---