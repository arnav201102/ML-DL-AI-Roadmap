# 🔥 30 HOTS QUESTIONS

## Mean • Median • Variance • Standard Deviation • ML

---

## 🧠 PART A — Conceptual & Proof-Based (1–10)

---

### **Q1.**

Why does the mean minimize
[
\sum (x_i - c)^2
]
but the median minimizes
[
\sum |x_i - c|?
]

**Answer:**
Squared error is differentiable → derivative gives (c = \mu).
Absolute error penalizes large deviations linearly → median balances points on both sides.

---

### **Q2.**

Can variance ever be negative? Prove your answer.

**Answer:**
No.
[
(x_i-\mu)^2 \ge 0 \Rightarrow \sigma^2 \ge 0
]

---

### **Q3.**

If all data points are increased by a constant (k), what happens to mean and variance?

**Answer:**
Mean → (\mu + k)
Variance → unchanged

---

### **Q4.**

If all data points are multiplied by (k), what happens to variance and std dev?

**Answer:**
Variance → (k^2\sigma^2)
Std dev → (|k|\sigma)

---

### **Q5.**

Why is standard deviation preferred over variance for interpretation?

**Answer:**
Std dev has same units as data; variance has squared units.

---

### **Q6.**

Can two datasets have the same mean and variance but different distributions?

**Answer:**
Yes. Mean and variance do not uniquely define a distribution.

---

### **Q7.**

Why do we divide by (n-1) in sample variance?

**Answer:**
One degree of freedom is lost due to estimation of the mean → unbiased estimator.

---

### **Q8.**

What does zero variance imply geometrically?

**Answer:**
All points lie at the same location → identical values.

---

### **Q9.**

Why does variance amplify outliers?

**Answer:**
Squaring increases influence of large deviations.

---

### **Q10.**

Is standard deviation a measure of central tendency?

**Answer:**
No. It measures spread around the center.

---

## 📊 PART B — Numerical & Reasoning (11–20)

---

### **Q11.**

Dataset A: ([2,4,6])
Dataset B: ([1,4,7])
Which has higher variance?

**Answer:**
Dataset B.

---

### **Q12.**

If mean = median, is the data necessarily symmetric?

**Answer:**
No. It may be coincidental.

---

### **Q13.**

Can median be outside the range ([min, max])?

**Answer:**
No.

---

### **Q14.**

If variance is large, what can you say about standard deviation?

**Answer:**
It is also large (square root relation).

---

### **Q15.**

For which dataset is median a better measure than mean?

**Answer:**
Skewed data with outliers (e.g., income).

---

### **Q16.**

If one extreme outlier is added, which changes more: mean or median?

**Answer:**
Mean.

---

### **Q17.**

If all deviations from mean double, what happens to variance?

**Answer:**
Variance becomes 4 times larger.

---

### **Q18.**

Why is variance preferred over mean absolute deviation mathematically?

**Answer:**
Differentiable → easier optimization.

---

### **Q19.**

Which dataset has larger spread?

A: (\sigma=2)
B: (\sigma=5)

**Answer:**
Dataset B.

---

### **Q20.**

If (\sigma=0), what is the dataset?

**Answer:**
All values are equal.

---

## 🤖 PART C — ML & Applied HOTS (21–30)

---

### **Q21.**

Why is mean squared error used in linear regression?

**Answer:**
Smooth, convex, differentiable → closed-form solution.

---

### **Q22.**

What happens if we replace MSE with MAE in regression?

**Answer:**
Prediction shifts from mean to median; optimization becomes harder.

---

### **Q23.**

What does high variance in a model indicate?

**Answer:**
Overfitting; sensitivity to noise.

---

### **Q24.**

How does standard deviation relate to Gaussian distribution width?

**Answer:**
Larger σ → wider, flatter curve.

---

### **Q25.**

Why is data often standardized before ML training?

**Answer:**
To make variance uniform and speed convergence.

---

### **Q26.**

What does it mean if residual errors have high variance?

**Answer:**
Model predictions are inconsistent.

---

### **Q27.**

Why are squared errors more sensitive to outliers than absolute errors?

**Answer:**
Errors grow quadratically.

---

### **Q28.**

In anomaly detection, why are points far from mean important?

**Answer:**
They have large deviations (high z-score).

---

### **Q29.**

Explain bias–variance tradeoff using variance.

**Answer:**
Low bias → complex model → high variance
High bias → simple model → low variance

---

### **Q30.**

Why does minimizing variance improve model stability?

**Answer:**
Predictions fluctuate less with new data.
