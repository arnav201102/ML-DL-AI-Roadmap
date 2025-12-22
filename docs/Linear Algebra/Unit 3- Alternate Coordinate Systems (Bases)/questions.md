# 📘 UNIT 3 — 50 QUESTIONS + HOTS

## (With Examples, Detailed Answers, Math + ML)

---

## 🟢 SECTION A — BASICS OF BASES & COORDINATES (1–12)

---

### **Q1. (Example)**

Vector ( v = (4,2) ) is written as
[
v = 4(1,0) + 2(0,1)
]
What does this mean geometrically?

**Answer:**
It means the vector is described using the **standard basis**. The numbers (4,2) are not the vector itself, but its **coordinates relative to the chosen basis**.

**ML meaning:**
Raw features are coordinates in a chosen basis.

---

### **Q2. (Example)**

Given basis
[
b_1=(1,1),; b_2=(1,-1)
]
Write ( v=(2,0) ) in this basis.

**Answer:**
Solve:
[
(2,0)=c_1(1,1)+c_2(1,-1)
\Rightarrow c_1=1,;c_2=1
]

**ML meaning:**
Same data point, different feature representation.

---

### **Q3.**

Why must basis vectors be linearly independent?

**Answer:**
If dependent, coordinates are not unique. ML models would learn redundant features.

---

### **Q4. (Example)**

Why is ((1,0),(2,0)) not a valid basis for (\mathbb{R}^2)?

**Answer:**
They lie on the same line and cannot span the plane.

**ML meaning:**
Features are redundant → rank deficiency.

---

### **Q5.**

Why do different bases describe the same vector differently?

**Answer:**
Coordinates depend on measurement axes, not the vector itself.

---

### **Q6.**

In ML terms, what is a “bad basis”?

**Answer:**
A basis with:

* High correlation
* Redundancy
* Poor conditioning

---

### **Q7. (Example)**

Why is pixel space a bad basis for images?

**Answer:**
Pixels are highly correlated. Meaningful patterns live in rotated/combined directions (edges, textures).

---

### **Q8.**

Why does ML try to *learn* bases instead of fixing them?

**Answer:**
Because meaningful structure depends on data distribution.

---

### **Q9. (Example)**

Why are word embeddings a change of basis?

**Answer:**
Words move from one-hot coordinates to semantic coordinates.

---

### **Q10.**

What happens if the basis size is smaller than the space?

**Answer:**
Information loss (projection).

---

### **Q11.**

What happens if the basis size is larger than needed?

**Answer:**
Redundancy, overparameterization.

---

### **Q12.**

Why is basis choice a modeling decision?

**Answer:**
It determines what patterns become easy or hard to learn.

---

## 🟡 SECTION B — ORTHOGONALITY & PROJECTIONS (13–28)

---

### **Q13. (Example)**

Check if (u=(1,2)) and (v=(2,-1)) are orthogonal.

**Answer:**
[
u\cdot v=2-2=0
\Rightarrow \text{orthogonal}
]

---

### **Q14.**

Why does orthogonality imply independence?

**Answer:**
Orthogonal vectors share no directional information.

---

### **Q15. (Example)**

Let (S=\text{span}{(1,1)}).
Find (S^\perp).

**Answer:**
Vectors satisfying (x+y=0).
So (S^\perp=\text{span}{(1,-1)}).

---

### **Q16.**

Why is (S \oplus S^\perp = \mathbb{R}^n)?

**Answer:**
Every vector decomposes into parallel + perpendicular components.

---

### **Q17. (Example)**

Project (x=(3,1)) onto (u=(1,1)).

**Answer:**
[
\text{proj}_u(x)=\frac{4}{2}(1,1)=(2,2)
]

---

### **Q18.**

What does projection minimize?

**Answer:**
Squared distance to the subspace.

---

### **Q19. (Example)**

In linear regression, what is the prediction geometrically?

**Answer:**
Projection of target vector onto column space of features.

---

### **Q20.**

Why is regression error orthogonal to feature space?

**Answer:**
Because projection leaves residual in the orthogonal complement.

---

### **Q21.**

Why does PCA use orthogonal directions?

**Answer:**
To avoid overlapping information.

---

### **Q22. (Example)**

Why does removing orthogonal noise improve learning?

**Answer:**
Noise lies in low-variance orthogonal directions.

---

### **Q23.**

Why are orthogonal features easier to optimize?

**Answer:**
Gradients don’t interfere.

---

### **Q24.**

Why does Gram–Schmidt remove correlation?

**Answer:**
Each step subtracts projections onto previous directions.

---

### **Q25.**

Why is orthogonality numerically stable?

**Answer:**
No amplification or suppression of values.

---

### **Q26. (Example)**

Why does whitening help gradient descent?

**Answer:**
Makes all directions equally scaled.

---

### **Q27.**

Why is cosine similarity related to orthogonality?

**Answer:**
Cosine measures angle, not magnitude.

---

### **Q28.**

Why do attention models normalize dot products?

**Answer:**
To control projection magnitude.

---

## 🔴 SECTION C — CHANGE OF BASIS, ORTHONORMALITY, EIGENS (29–50)

---

### **Q29. (Example)**

Why is PCA a change of basis?

**Answer:**
It rotates axes to variance directions.

---

### **Q30.**

Why does diagonalizing a matrix simplify analysis?

**Answer:**
Each coordinate evolves independently.

---

### **Q31. (Example)**

Why are eigenvectors “natural axes”?

**Answer:**
Transformation does not rotate them.

---

### **Q32.**

Why do eigenvalues measure importance?

**Answer:**
They scale variance or curvature.

---

### **Q33. (Example)**

Why do small eigenvalues slow training?

**Answer:**
Flat directions → tiny gradients.

---

### **Q34.**

Why do large eigenvalues cause instability?

**Answer:**
Gradients explode along those directions.

---

### **Q35.**

Why do orthonormal bases avoid matrix inversion?

**Answer:**
Coordinates are dot products.

---

### **Q36. (Example)**

Why does QR decomposition appear in optimization?

**Answer:**
It creates orthonormal directions for stability.

---

### **Q37.**

Why is covariance symmetric?

**Answer:**
Correlation is mutual.

---

### **Q38. (Example)**

Why are covariance eigenvectors orthogonal?

**Answer:**
Symmetric matrices guarantee orthogonal eigenvectors.

---

### **Q39.**

Why does SVD generalize PCA?

**Answer:**
Works even when matrix isn’t square.

---

### **Q40.**

Why does low-rank approximation help generalization?

**Answer:**
Removes noise and redundancy.

---

### **Q41.**

Why are embeddings learned instead of fixed?

**Answer:**
Meaning depends on task.

---

### **Q42.**

Why is attention a dynamic basis?

**Answer:**
Basis weights change per input.

---

### **Q43.**

Why does spectral normalization stabilize GANs?

**Answer:**
Controls largest eigenvalue.

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

Why is overcomplete basis sometimes useful?

**Answer:**
Multiple ways to represent same signal.

---

### **Q50. (MASTER HOTS)**

Explain ML using bases in one paragraph.

**Answer:**
Machine learning is the process of discovering coordinate systems in which complex data becomes simple. By rotating, projecting, scaling, and reweighting bases, models isolate meaningful directions, suppress noise, stabilize optimization, and make patterns linearly separable.
