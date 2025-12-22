# 📘 UNIT 3 — 50 QUESTIONS + HOTS

## Bases, Coordinates, Orthogonality & ML

*(With Examples, Detailed Answers, Math + ML Insight)*

---

## 🟢 SECTION A — BASICS OF BASES & COORDINATES (1–12)

---

### **Q1. (Example)**

Vector ( v = (4,2) ) is written as:

```math
v = 4(1,0) + 2(0,1)
```

**What does this mean geometrically?**

**Answer:**
The vector is expressed using the **standard basis**. The numbers (4,2) are **coordinates**, not the vector itself. They describe how much of each basis direction is needed.

**ML meaning:**
Raw features are coordinates in a chosen feature basis.

---

### **Q2. (Example)**

Given basis:

```math
b_1=(1,1), \; b_2=(1,-1)
```

Write ( v=(2,0) ) in this basis.

**Answer:**

```math
(2,0)=c_1(1,1)+c_2(1,-1)
```

Solving gives:

```math
c_1=1, \; c_2=1
```

**ML meaning:**
Same data point, different feature representation.

---

### **Q3.**

Why must basis vectors be linearly independent?

**Answer:**
If they are dependent, coordinates are not unique. ML models would learn **redundant features**, harming interpretability and optimization.

---

### **Q4. (Example)**

Why is ( (1,0),(2,0) ) not a valid basis for ( \mathbb{R}^2 )?

**Answer:**
Both vectors lie on the same line, so they cannot span the plane.

**ML meaning:**
Rank-deficient feature matrix → loss of information.

---

### **Q5.**

Why do different bases describe the same vector differently?

**Answer:**
Coordinates depend on measurement axes, not on the vector itself.

---

### **Q6.**

In ML terms, what is a “bad basis”?

**Answer:**
A basis with high correlation, redundancy, and poor numerical conditioning.

---

### **Q7. (Example)**

Why is pixel space a bad basis for images?

**Answer:**
Pixels are highly correlated. Meaningful patterns (edges, textures) appear in rotated and combined directions.

---

### **Q8.**

Why does ML try to *learn* bases instead of fixing them?

**Answer:**
Because meaningful structure depends on the data distribution and task.

---

### **Q9. (Example)**

Why are word embeddings a change of basis?

**Answer:**
Words move from sparse one-hot coordinates to dense semantic coordinates.

---

### **Q10.**

What happens if the basis size is smaller than the space?

**Answer:**
Information loss due to projection.

---

### **Q11.**

What happens if the basis size is larger than needed?

**Answer:**
Redundancy and overparameterization.

---

### **Q12.**

Why is basis choice a modeling decision?

**Answer:**
It determines which patterns are easy or hard for the model to learn.

---

## 🟡 SECTION B — ORTHOGONALITY & PROJECTIONS (13–28)

---

### **Q13. (Example)**

Check if ( u=(1,2) ) and ( v=(2,-1) ) are orthogonal.

**Answer:**

```math
u \cdot v = 2 - 2 = 0
```

Vectors are orthogonal.

---

### **Q14.**

Why does orthogonality imply independence?

**Answer:**
Orthogonal vectors share no directional information.

---

### **Q15. (Example)**

Let ( S=\text{span}{(1,1)} ). Find ( S^\perp ).

**Answer:**
Vectors satisfying ( x+y=0 ).

```math
S^\perp=\text{span}\{(1,-1)\}
```

---

### **Q16.**

Why is ( S \oplus S^\perp = \mathbb{R}^n )?

**Answer:**
Every vector decomposes into parallel and perpendicular components.

---

### **Q17. (Example)**

Project ( x=(3,1) ) onto ( u=(1,1) ).

**Answer:**

```math
\text{proj}_u(x)=\frac{4}{2}(1,1)=(2,2)
```

---

### **Q18.**

What does projection minimize?

**Answer:**
Squared distance to the subspace.

---

### **Q19. (Example)**

In linear regression, what is the prediction geometrically?

**Answer:**
Projection of the target vector onto the column space of features.

---

### **Q20.**

Why is regression error orthogonal to feature space?

**Answer:**
Because projection leaves residuals in the orthogonal complement.

---

### **Q21.**

Why does PCA use orthogonal directions?

**Answer:**
To prevent overlapping and redundant information.

---

### **Q22. (Example)**

Why does removing orthogonal noise improve learning?

**Answer:**
Noise lies in low-variance orthogonal directions.

---

### **Q23.**

Why are orthogonal features easier to optimize?

**Answer:**
Gradients do not interfere with each other.

---

### **Q24.**

Why does Gram–Schmidt remove correlation?

**Answer:**
Each step subtracts projections onto previous directions.

---

### **Q25.**

Why is orthogonality numerically stable?

**Answer:**
It avoids amplification or suppression of values.

---

### **Q26. (Example)**

Why does whitening help gradient descent?

**Answer:**
All directions become equally scaled.

---

### **Q27.**

Why is cosine similarity related to orthogonality?

**Answer:**
Cosine measures angle, not magnitude.

---

### **Q28.**

Why do attention models normalize dot products?

**Answer:**
To control projection magnitude and stabilize gradients.

---

## 🔴 SECTION C — CHANGE OF BASIS, ORTHONORMALITY & EIGENS (29–50)

---

### **Q29. (Example)**

Why is PCA a change of basis?

**Answer:**
It rotates axes toward directions of maximum variance.

---

### **Q30.**

Why does diagonalizing a matrix simplify analysis?

**Answer:**
Each coordinate evolves independently.

---

### **Q31. (Example)**

Why are eigenvectors called “natural axes”?

**Answer:**
The transformation does not rotate them.

---

### **Q32.**

Why do eigenvalues measure importance?

**Answer:**
They scale variance or curvature along directions.

---

### **Q33. (Example)**

Why do small eigenvalues slow training?

**Answer:**
Flat directions produce tiny gradients.

---

### **Q34.**

Why do large eigenvalues cause instability?

**Answer:**
Gradients explode along steep directions.

---

### **Q35.**

Why do orthonormal bases avoid matrix inversion?

**Answer:**
Coordinates reduce to dot products.

---

### **Q36. (Example)**

Why does QR decomposition appear in optimization?

**Answer:**
It constructs stable orthonormal directions.

---

### **Q37.**

Why is covariance symmetric?

**Answer:**
Correlation is mutual between variables.

---

### **Q38. (Example)**

Why are covariance eigenvectors orthogonal?

**Answer:**
Symmetric matrices guarantee orthogonal eigenvectors.

---

### **Q39.**

Why does SVD generalize PCA?

**Answer:**
It works for non-square matrices.

---

### **Q40.**

Why does low-rank approximation help generalization?

**Answer:**
It removes noise and redundancy.

---

### **Q41.**

Why are embeddings learned instead of fixed?

**Answer:**
Meaning depends on the task and data.

---

### **Q42.**

Why is attention a dynamic basis?

**Answer:**
Basis weights change per input.

---

### **Q43.**

Why does spectral normalization stabilize GANs?

**Answer:**
It controls the largest eigenvalue.

---

### **Q44.**

Why is the Hessian important in optimization?

**Answer:**
Its eigenvalues describe curvature.

---

### **Q45.**

Why does second-order optimization use eigen-directions?

**Answer:**
They give fastest descent directions.

---

### **Q46.**

Why do transformers rely heavily on linear algebra?

**Answer:**
They repeatedly change coordinate systems.

---

### **Q47.**

Why does deep learning equal repeated basis refinement?

**Answer:**
Each layer re-expresses data more meaningfully.

---

### **Q48.**

Why is orthogonality linked to disentanglement?

**Answer:**
Independent factors lie in independent directions.

---

### **Q49.**

Why is an overcomplete basis sometimes useful?

**Answer:**
It allows multiple representations of the same signal.

---

### **Q50. (MASTER HOTS)**

**Explain ML using bases in one paragraph.**

**Answer:**
Machine learning is the process of discovering coordinate systems in which complex data becomes simple. By rotating, projecting, scaling, and reweighting bases, models isolate meaningful directions, suppress noise, stabilize optimization, and make patterns easier to learn.
