# 🔹 LESSON 3: LINEAR DEPENDENCE & INDEPENDENCE (COMPLETE)

## 1. Linear Dependence

Vectors are dependent if:
[
c_1v_1+\dots+c_nv_n=0
]
has a **non-zero solution**.

Meaning:

* Redundancy
* No new direction

---

## 2. Linear Independence

Only solution is:
[
c_1=c_2=\dots=c_n=0
]

Meaning:

* Every vector adds something new

---

## 3. Zero Vector Rule

Any set containing **0** is dependent.

---

## 4. Dimension Rule

In ℝⁿ:

* Maximum independent vectors = n

---

## Practice Questions (WITH SOLUTIONS)

### Q1. Are (1,1,1),(2,2,2),(3,3,3) independent?

No — scalar multiples.

---

### Q2. Is {(1,0),(0,1),(1,1)} independent?

No:
[
(1,1)=(1,0)+(0,1)
]

---

### Q3. Can two vectors in ℝ³ be dependent?

Yes:
[
(1,2,3),(2,4,6)
]

---

### Q4. How many independent vectors needed for ℝ⁴?

4

---

## HOTS (ADVANCED) WITH SOLUTIONS

### HOTS 1

**Why does dependence imply loss of information?**
Because one vector adds no new direction.

---

### HOTS 2

**Why are independent columns required for matrix invertibility?**
Dependent columns collapse dimensions → no unique inverse.

---

### HOTS 3 (Hard)

**Can a set be independent but not span the space?**
Yes. Example: one vector in ℝ².

---

---

# 🔚 FINAL MASTER SUMMARY (FOR REVISION)

* Vector → magnitude + direction
* Linear combination → scaling + adding
* Span → reachability
* Independence → uniqueness
* Dependence → redundancy

> These ideas power **matrices, systems, PCA, neural networks, embeddings, ML models**.


## Key Concepts
Vectors are dependent if one can be written as a combination of others.

---

## Practice Questions with Solutions

### Basic

**Q1. Are (1,2) and (2,4) independent?**  
**Solution:**  
No, (2,4)=2(1,2)

**Q2. Is the zero vector independent?**  
**Solution:**  
No, any set containing zero vector is dependent.

---

### Intermediate

**Q3. Can three vectors be independent in R²?**  
**Solution:**  
No, max two independent vectors.

**Q4. Check independence of (1,2,3), (2,4,6).**  
**Solution:**  
Dependent, second is multiple of first.

---

### Advanced

**Q5. Why does dependence imply redundancy?**  
**Solution:**  
One vector adds no new direction.

**Q6. Relation between independence and invertibility?**  
**Solution:**  
Independent columns imply invertible matrix.

---
