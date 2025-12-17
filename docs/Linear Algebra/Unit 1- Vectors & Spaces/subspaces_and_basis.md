# Subspaces and the Basis for a Subspace

## 1. What is a Subspace?
A **subspace** is a subset of a vector space that is itself a vector space.

### Subspace Test (Must ALL hold)
1. Zero vector is in the set  
2. Closed under addition  
3. Closed under scalar multiplication  

---

## 2. Example: Checking a Subspace

### Example 1
S = {(x, 0) | x ∈ ℝ}

1. Zero vector (0,0) ∈ S ✔  
2. (x₁,0) + (x₂,0) = (x₁+x₂,0) ∈ S ✔  
3. c(x,0) = (cx,0) ∈ S ✔  

✅ **S is a subspace**

---

### Example 2 (Not a Subspace)
S = {(x, 1) | x ∈ ℝ}

Zero vector (0,0) ∉ S ❌  
So S is **not** a subspace.

---

## 3. Basis of a Subspace
A **basis** is a set of vectors that:
- Spans the subspace
- Is linearly independent

---

## 4. Example: Basis of a Subspace

### Example
Subspace:
S = {(x, y, 0) | x,y ∈ ℝ}

A basis is:
{(1,0,0), (0,1,0)}

Dimension = 2

---

## 5. Key Insight
Every vector in the subspace can be written **uniquely** using the basis.

---

## 6. Why This Matters
- Solution spaces are subspaces
- ML feature spaces are subspaces
- Simplifies infinite vectors into finite directions
