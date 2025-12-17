# Matrices for Solving Systems by Elimination

## 1. Linear System
Example:
x + y = 5  
2x + y = 7

---

## 2. Augmented Matrix

[ 1  1 | 5 ]  
[ 2  1 | 7 ]

---

## 3. Row Operations Example

R₂ → R₂ − 2R₁

[ 1  1 | 5 ]  
[ 0 -1 | -3 ]

R₂ → -R₂

[ 1  1 | 5 ]  
[ 0  1 | 3 ]

R₁ → R₁ − R₂

[ 1  0 | 2 ]  
[ 0  1 | 3 ]

Solution:
x = 2, y = 3

---

## 4. Solution Types

- Unique → one pivot per variable
- Infinite → free variables
- None → inconsistent row like [0 0 | 1]

---

## 5. Why Elimination Works
Row operations preserve the solution set.
