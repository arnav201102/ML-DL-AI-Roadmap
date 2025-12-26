## 1. What is sampling in probability?

**Answer:**
Sampling is the process of drawing random observations
$
x_1, x_2, \dots, x_n
$
from a population or probability distribution ( P(X) ), written as:
$
x_i \sim P(X)
$
Each sample is a realization of a random variable. Sampling allows us to study an unknown population using finite data.

---

## 2. Why is sampling necessary in real-world problems?

**Answer:**
Because:

* Populations are often infinite or inaccessible
* Exact distributions are unknown
* Computing true expectations is infeasible

Sampling is the only practical way to perform statistical inference and machine learning.

---

## 3. What is the difference between a population and a sample?

**Answer:**

* **Population:** Entire distribution or dataset (usually unknown)
* **Sample:** Finite subset drawn from the population

Mathematically, population parameters are estimated using sample statistics.

---

## 4. What does it mean to say a sample is “random”?

**Answer:**
Each observation has a known, non-zero probability of being selected, and selection does not depend on other observations.

Randomness ensures unbiased estimation.

---

## 5. Explain sampling as an approximation of expectation.

**Answer:**
True expectation:
$
\mathbb{E}[f(X)] = \int f(x)P(x),dx
$

Sample approximation:
$
\mathbb{E}[f(X)] \approx \frac{1}{n}\sum_{i=1}^{n} f(x_i)
$

This is **Monte Carlo estimation**, the mathematical foundation of ML training.

---

## 6. What is the Law of Large Numbers and how does it relate to sampling?

**Answer:**
It states that as sample size increases, the sample mean converges to the true mean:
$
\frac{1}{n}\sum_{i=1}^{n} x_i \to \mathbb{E}[X]
$
This guarantees that sampling-based estimates become accurate with enough data.

---

## 7. What is sampling bias?

**Answer:**
Sampling bias occurs when the sampling process systematically favors certain outcomes, making the sample unrepresentative of the population.

Biased samples produce biased models.

---

## 8. What is uniform (simple random) sampling?

**Answer:**
Every element in the population has equal probability of being selected:
$
P(x_i) = \frac{1}{N}
$
It works well when the population is homogeneous.

---

## 9. What is stratified sampling and why is it useful?

**Answer:**
The population is divided into strata (groups), and samples are drawn from each stratum.

It reduces variance and ensures minority groups are represented—critical for imbalanced ML datasets.

---

## 10. What is importance sampling?

**Answer:**
Instead of sampling from a hard distribution ( P(x) ), sample from an easier one ( Q(x) ) and reweight:
$
\mathbb{E}_P[f(X)] = \mathbb{E}_Q\left[f(X)\frac{P(X)}{Q(X)}\right]
$
Used in reinforcement learning and Bayesian inference.

---

## 11. What is sampling with replacement vs without replacement?

**Answer:**

* **With replacement:** Same element can be selected multiple times
* **Without replacement:** Each element selected once

With replacement simplifies mathematical analysis.

---

## 12. What is bootstrap sampling?

**Answer:**
Sampling **with replacement** from an existing dataset to estimate uncertainty (variance, confidence intervals).

Widely used when theoretical distributions are unknown.

---

## 13. How is sampling used in stochastic gradient descent (SGD)?

**Answer:**
Gradients are estimated using randomly sampled mini-batches:
$
\nabla L \approx \frac{1}{B}\sum_{i=1}^{B} \nabla \ell(x_i,y_i)
$
This makes optimization efficient and introduces helpful noise.

---

## 14. Why does mini-batch sampling improve generalization?

**Answer:**
The noise introduced by sampling prevents the model from settling into sharp minima, improving robustness and generalization.

---

## 15. What is the difference between shuffling and sampling?

**Answer:**

* **Shuffling:** Randomizes order
* **Sampling:** Selects a subset

Shuffling prevents correlated batches; sampling controls which data is used.

---

## 16. What is rejection sampling?

**Answer:**
Samples are drawn from a proposal distribution and accepted with probability proportional to the target distribution.

Simple but inefficient in high dimensions.

---

## 17. What is Markov Chain Monte Carlo (MCMC)?

**Answer:**
A method that constructs a Markov chain whose stationary distribution is the target distribution.

Used for sampling from complex posterior distributions.

---

## 18. What is Gibbs sampling?

**Answer:**
A special case of MCMC where one variable is sampled at a time from its conditional distribution:
$
x_i \sim P(x_i \mid x_{-i})
$

---

## 19. How is sampling used in generative models?

**Answer:**
Models learn a distribution ( P(x) ) and generate new data by sampling from it.

Examples:

* VAEs
* Diffusion models
* Language models

---

## 20. What is ancestral sampling?

**Answer:**
Sampling sequentially from conditional distributions:
$
x_1 \sim P(x_1),\quad x_2 \sim P(x_2 \mid x_1)
$
Used in autoregressive models like GPT.

---

# HOTS (Higher Order Thinking Skills)

---

## 21. Why does biased sampling lead to confident but wrong ML models?

**Answer:**
The model correctly learns patterns in the sample distribution, but the sample does not represent reality. The math is right; the data is wrong.

---

## 22. Why can increasing data size not fix bad sampling?

**Answer:**
More data from the **same biased process** only increases confidence in the wrong estimate.

Bias does not vanish with sample size.

---

## 23. Explain how class imbalance is a sampling problem.

**Answer:**
Minority classes are under-sampled, causing the model to learn majority behavior. The issue is data distribution, not algorithm choice.

---

## 24. Why is evaluating a model on sampled data dangerous?

**Answer:**
You may end up measuring the quality of the sampler instead of the model’s true performance on real-world data.

---

## 25. Why does dataset shift break trained models?

**Answer:**
The model learns:
$
P_{\text{train}}(y \mid x)
$
but deployment follows:
$
P_{\text{prod}}(y \mid x)
$
Different distributions → invalid predictions.

---

## 26. Sampling vs optimization: why are they not the same?

**Answer:**
Optimization finds the best point (MAP).
Sampling explores the entire distribution.

Generation requires sampling, not optimization.

---

## 27. Why does temperature affect sampling in language models?

**Answer:**
Temperature rescales probabilities:

* Low temperature → deterministic outputs
* High temperature → diverse but risky outputs

It controls exploration vs exploitation.

---

## 28. Why does top-k or top-p sampling improve text generation?

**Answer:**
They restrict sampling to plausible tokens, avoiding low-probability nonsense while preserving diversity.

---

## 29. Why is sampling noise beneficial in ML?

**Answer:**
Noise prevents overfitting, improves exploration, and enables escaping poor local minima.

---

## 30. What is the single most important rule about sampling in ML?

**Answer:**
**Your model can only learn what your sampling process allows it to see.**
Bad sampling guarantees failure, regardless of model quality.

---

### Final takeaway (straight talk)

* Sampling is not preprocessing — it **defines your reality**
* ML is learning from samples, not truth
* Every model failure can be traced back to bad sampling assumptions