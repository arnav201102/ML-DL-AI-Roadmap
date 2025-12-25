
# 📌 1️⃣ — 30 HOTS Questions (Math + ML)

### **A. Mathematical HOTS (1–15)**

(Answer immediately after each question for active learning)

1. **If X is uniform over {1,2,3,4,5}, find E[X].**
   → 3

2. **Find Var(X) for the same distribution.**
   → 2

3. **If P(X=3)=0.5 and sum of all probabilities is 1, and values 1,2,4,5 are equally likely — find each.**
   → Remaining prob = 0.5; each = 0.125

4. **For a Normal(μ=50, σ=10) distribution, what % of values lie in [40,60]?**
   → 68% (Empirical Rule: μ ± 1σ)

5. **If Z is standard normal, P(Z > 0) = ?**
   → 0.5

6. **If two dice are rolled, distribution of their sum is symmetric or skewed? Why?**
   → Symmetric (triangular PMF, symmetry around 7)

7. **Mean of Poisson(λ=7)?**
   → 7

8. **Variance of Poisson(λ=7)?**
   → 7

9. **For a Bernoulli(p) variable, find mean.**
   → p

10. **For Bernoulli(p), find variance.**
    → p(1-p)

11. **Which distribution models waiting time between events?**
    → Exponential

12. **Which distribution models number of events in a time interval?**
    → Poisson

13. **If a dataset has extreme outliers, which central tendency metric is better?**
    → Median

14. **Define CDF in 1 line.**
    → ( F(x) = P(X \le x) )

15. **Relationship between PDF and CDF?**
    → ( f(x) = \frac{d}{dx}F(x) )

---

### **B. Machine Learning HOTS (16–30)**

16. **Why do we assume normal distribution in Linear Regression?**
    → Residuals must be normal for valid inference, confidence intervals, p-values

17. **Which distribution fits classification probabilities?**
    → Bernoulli / Categorical / Softmax outputs

18. **Softmax layer outputs what type of distribution?**
    → Categorical probability distribution

19. **Why does Naive Bayes rely on distributions?**
    → It multiplies likelihoods using assumed PDFs

20. **In Bayesian learning, what does the prior represent?**
    → Our belief distribution before seeing data

21. **What distribution does dropout noise in neural networks resemble?**
    → Bernoulli

22. **ReLU outputs follow what kind of distribution trend?**
    → Right-skewed / positively skewed

23. **Which distribution helps detect anomalies?**
    → Normal (values >3σ flagged)

24. **What does variance in data distribution indicate?**
    → Spread → higher model complexity required

25. **Why is standard scaling effective?**
    → It normalizes data to N(0,1), stabilizing gradients

26. **Which loss function assumes Gaussian errors?**
    → MSE

27. **Which loss function assumes Laplace distribution (heavy tail)?**
    → MAE

28. **Cross entropy loss assumes what distribution?**
    → Probability distribution across classes (Categorical)

29. **In mixture models, each cluster corresponds to what?**
    → A component distribution

30. **GANs: generator tries to match what?**
    → True data distribution

---

# 📌 2️⃣ — Graphical Cheat Sheet (Mental Visuals)

| Distribution | Shape               | When Used            | Key Params |
| ------------ | ------------------- | -------------------- | ---------- |
| Uniform      | Flat                | Equal chance         | a,b        |
| Normal       | Bell Curve          | Natural data, errors | μ,σ        |
| Bernoulli    | Binary              | Yes/No output        | p          |
| Binomial     | Repeated Bernoulli  | Count of successes   | n,p        |
| Poisson      | Spike at low values | Rare events count    | λ          |
| Exponential  | Decays downwards    | Time between events  | λ          |
| Categorical  | Bars                | Classification probs | p₁,p₂,...  |

---

# 📌 3️⃣ — Python Examples (NumPy, Scikit)

```python
import numpy as np
from scipy.stats import norm, poisson, uniform

# Uniform distribution (1-5)
data = np.array([1,2,3,4,5])
print("Mean:", np.mean(data))
print("Std Dev:", np.std(data))

# Generate from Normal
normal_samples = norm.rvs(loc=0, scale=1, size=1000)

# Poisson sample
poisson_samples = poisson.rvs(mu=4, size=1000)

# Prob of value 7 in Poisson(4)
print(poisson.pmf(7, 4))
```

---

# 📌 4️⃣ — Real-World ML Case Studies

| Application                         | Distribution            | Why                     |
| ----------------------------------- | ----------------------- | ----------------------- |
| Spam vs Ham classification          | Bernoulli & Multinomial | Word presence/absence   |
| Predicting defects in manufacturing | Poisson                 | Rare event counts       |
| Height/Weight data preprocessing    | Normal                  | Natural biological data |
| Customer waiting time prediction    | Exponential             | Time until next arrival |
| Image pixel intensity modeling      | Gaussian mixture        | Complex multimodal data |

---

# 📌 5️⃣ — Deep Learning Interpretation

### 🔥 Key Takeaways

* Neural network weights initialize from **Normal** or **Xavier Uniform** distributions → avoids exploding gradients
* Dropout → **Bernoulli**, controlling co-adaptation
* Cross-entropy → assumes **Categorical** predicted distribution
* Generative models → learn entire **data distribution**

### GANs Equation (Distribution Matching)

[
G(z) \rightarrow p_g(x) \approx p_{data}(x)
]

Discriminator objective:

[
\max_D ; \mathbb{E}*{x\sim p*{data}}\log D(x)

* \mathbb{E}_{z\sim p_z}\log (1 - D(G(z)))
  ]

---

# 🎯 Final Summary (Your Brain Should Store This)

| Concept            | In 5 Secs                                     |
| ------------------ | --------------------------------------------- |
| Mean               | Center                                        |
| Variance           | Spread                                        |
| Std Dev            | Square root of variance                       |
| Distribution       | Pattern of data                               |
| ML Goal            | Approximate + use distributions to generalize |
| Deep Learning Goal | Learn data distribution itself                |


---
# Questions in Detail
# 📌 PART A — MATHEMATICS (1–15)

### Mean / Variance / Probability / Distributions

---

### **1️⃣ If X is uniform over {1,2,3,4,5}, find E[X]**

A **uniform distribution** means each value has equal probability.
Mean formula:

[
E[X] = \frac{1+2+3+4+5}{5}=3
]

📍**Meaning:**
If you randomly pick from 1–5 thousands of times, the **average** result will be **around 3**.

---

### **2️⃣ Find Var(X) for the same distribution**

Variance measures how *spread out* values are from the mean.

[
\mu = 3
]

[
Var(X)=\frac{(1-3)^2+(2-3)^2+(3-3)^2+(4-3)^2+(5-3)^2}{5}
]

[
= \frac{4+1+0+1+4}{5}=2
]

📍**Interpretation:**
Data is not tightly clustered, but spread evenly around the mean.

---

### **3️⃣ P(X=3)=0.5; others equal. Find probability of each.**

Total probability must equal 1:

[
P(1)+P(2)+P(4)+P(5) = 0.5
]

There are 4 equal-probability values, so:

[
P(\text{each}) = 0.5/4 = 0.125
]

📍**Intuition:**
Model is **biased toward 3** — the dataset has many 3s.

---

### **4️⃣ Normal(μ=50, σ=10). What % lie in [40,60]?**

Apply **68–95–99.7 Rule** (Empirical Rule):

* μ ± 1σ → 68% of data

So,

[
50 - 10 = 40, \quad 50 + 10 = 60
]

➡️ **68% of values fall within 40–60**

📍**Why ML cares:**
Normality assumption is required for statistical inference in regression.

---

### **5️⃣ If Z is standard normal, P(Z > 0) = ?**

Standard normal is symmetric around 0:

[
P(Z=0) = 0.5
]

📍**Interpretation:**
Half values are above average; half below.

---

### **6️⃣ Two dice rolled — is the sum symmetric?**

Possible sums: 2 to 12
Distribution peaks at **7**.

| Sum | # Combos |
| --- | -------- |
| 2   | 1        |
| 3   | 2        |
| 4   | 3        |
| 5   | 4        |
| 6   | 5        |
| 7   | 6        |
| 8   | 5        |
| 9   | 4        |
| 10  | 3        |
| 11  | 2        |
| 12  | 1        |

Symmetric triangle → **Yes**.

📍**Why important:**
ML often checks **symmetry / skewness** to pick models (e.g. normal vs skewed).

---

### **7️⃣ Mean of Poisson(λ=7)**

[
E[X] = λ = 7
]

📍**Used for:**
Count of events (calls per hour, customer arrivals, machine faults).

---

### **8️⃣ Variance of Poisson(λ=7)**

[
Var(X) = λ = 7
]

📍**Interpretation:**
If average events are 7, expect variation ≈7.

---

### **9️⃣ Mean of Bernoulli(p)**

Bernoulli: outcomes **0 or 1**

[
E[X] = p
]

📍If p = 0.8 → 80% chance success.

---

### **🔟 Variance of Bernoulli(p)**

[
Var(X) = p(1-p)
]

Max variance when p = 0.5
📍Meaning: Most uncertainty when outcome is **unpredictable**.

---

### **1️⃣1️⃣ Distribution for waiting time between events? — Exponential**

Example:
Time until next bus arrives.

📍Relation:

If events per hour follow Poisson → waiting times follow **Exponential**.

---

### **1️⃣2️⃣ Distribution for # of events per interval? — Poisson**

Example:
Number of errors on a machine per day.

📍Poisson & Exponential are siblings.

---

### **1️⃣3️⃣ Best average when data has outliers?**

✔️ **Median**

Example dataset:
1, 2, 3, 4, 1000

Mean = 202
Median = 3

📍Median resists outliers → **robust**.

---

### **1️⃣4️⃣ Define CDF**

[
F(x)=P(X \le x)
]

Shows **cumulative probability up to x**.

📍Used for probability comparisons.

---

### **1️⃣5️⃣ Relationship between PDF and CDF**

For continuous variables:

[
f(x)=\frac{d}{dx}F(x)
]

PDF is the **rate of change** of the CDF.

📍In ML → determines likelihoods used in models.

---

# 📌 PART B — MACHINE LEARNING (16–30)

---

### **1️⃣6️⃣ Why assume normal residuals in Linear Regression?**

Residuals = errors between predictions & true values.

Normal residuals → good properties:

* unbiased coefficients
* valid hypothesis tests
* reliable confidence intervals

📍If residuals are NOT normal → model is unreliable.

---

### **1️⃣7️⃣ Classification outputs match which distribution?**

* **Binary → Bernoulli**
* **Multi-class → Categorical**

Example:
Dog vs Cat → Bernoulli(0.8)

---

### **1️⃣8️⃣ Softmax outputs what?**

A **probability distribution** where:

[
\sum p_i = 1
]

Example:
Softmax([2,4,6]) → [0.01, 0.09, 0.90]

📍Model believes class 3 with 90% confidence.

---

### **1️⃣9️⃣ Why Naive Bayes needs distributions?**

Computes:

[
P(Y|X) \propto P(X|Y)P(Y)
]

It uses **probability of features given class**.
Assumes independence → Naive.

📍Simplifies computation → fast classification.

---

### **2️⃣0️⃣ Bayesian Learning — What is a Prior?**

Before seeing data:

[
P(\theta) = \text{prior belief}
]

Example:
A new doctor assumes patients usually recover — **prior belief**.

---

### **2️⃣1️⃣ Dropout Noise Distribution → Bernoulli**

Neurons **randomly removed** during training:

* keep(1) with p
* drop(0) with 1-p

📍Prevents overfitting.

---

### **2️⃣2️⃣ ReLU output distribution — Right skewed**

Because:

[
ReLU(x)=\max(0,x)
]

Most outputs become **0s**, rest positive.

📍Gradient issues → solved by Leaky ReLU / GELU.

---

### **2️⃣3️⃣ Which distribution helps detect anomalies?**

**Normal distribution** thresholds:

[
|x - \mu| > 3\sigma
]

→ Outlier / anomaly

---

### **2️⃣4️⃣ Variance in data → ML meaning**

High variance → data is **spread** → complex model needed.
Low variance → **simpler** model may be enough.

📍Ties to **Bias–Variance Tradeoff**.

---

### **2️⃣5️⃣ Why Standard Scaling works?**

Transforms to:

[
z = \frac{x - \mu}{\sigma}
]

→ **N(0,1)**

📍Neural networks & kNN behave better.

---

### **2️⃣6️⃣ MSE assumes Gaussian noise**

Why?

[
(y - \hat{y})^2
]

Comes from maximizing likelihood of normal distribution.

📍Suitable when **errors are normally distributed**.

---

### **2️⃣7️⃣ MAE assumes Laplace distribution**

[
|y - \hat{y}|
]

Better when data has **outliers**, heavy-tailed distribution.

---

### **2️⃣8️⃣ Cross Entropy assumes Categorical**

Penalty for wrong probability:

[
-\log(P(\text{correct class}))
]

📍Used in neural networks.

---

### **2️⃣9️⃣ In mixture models, each cluster is a distribution**

Example: GMM

[
p(x)=\sum_{k} \pi_k \mathcal{N}(x|\mu_k,\sigma_k)
]

Each cluster → its own Normal.

---

### **3️⃣0️⃣ GANs — What does generator learn?**

Goal:

[
p_g(x) \approx p_{data}(x)
]

Generator tries to create data indistinguishable from real.
Discriminator tries to catch it.

📍They **compete → improve**.

---

# 🎯 FINAL SUMMARY TABLE

| Topic        | Core Idea                              |
| ------------ | -------------------------------------- |
| Mean         | Expected value                         |
| Variance     | Spread of data                         |
| Std Dev      | Natural scale of deviation             |
| Distribution | Shape of data + probabilities          |
| In ML        | Drives model choice, assumptions, loss |
| In DL        | Target is to learn data distribution   |
