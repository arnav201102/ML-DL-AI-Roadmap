# 1. What “Sampling” Really Means (Mathematics First)

### Formal definition

Let:

* Population / distribution: ( P(X) )
* Sample: $( x_1, x_2, \dots, x_n \sim P(X) )$

**Sampling** means drawing random variables from a probability distribution such that:

$
x_i \sim P(X)
$

Each ( $x_i$ ) is a realization of the same random process.

> Sampling is how you **observe reality through randomness**.

---

## Why sampling exists at all

Because:

* Full population is unknown or infinite
* Computing exact expectations is impossible
* Data arrives stochastically

Sampling is not a hack — it’s **the only way to do inference in the real world**.

---

# 2. Sampling vs Population (Critical Distinction)

| Population         | Sample             |
| ------------------ | ------------------ |
| True distribution  | Finite realization |
| Unknown parameters | Estimators         |
| Theoretical        | Observable         |

Mathematically:

$
\theta = \mathbb{E}_P[X] \quad \text{(unknown)}
$

We estimate using samples:

$
\hat{\theta} = \frac{1}{n}\sum_{i=1}^{n} x_i
$

---

# 3. Sampling as Approximation of Expectation

This is the heart of ML.

### True expectation

$
\mathbb{E}_P[f(X)] = \int f(x) P(x),dx
$

### Sample-based approximation

$
\boxed{
\mathbb{E}*P[f(X)] \approx \frac{1}{n}\sum*{i=1}^{n} f(x_i)
}
$

This is **Monte Carlo estimation**.

Everything else is decoration.

---

# 4. Law of Large Numbers (Why Sampling Works)

$
\frac{1}{n}\sum_{i=1}^{n} x_i \xrightarrow{n \to \infty} \mathbb{E}[X]
$

Meaning:

* More samples → closer to truth
* Variance shrinks as ( $\frac{1}{n}$ )

Sampling works because math guarantees convergence — not because of optimism.

---

# 5. Types of Sampling (Mathematical View)

## 5.1 Uniform / Random Sampling

Each element has equal probability:

$
P(x_i) = \frac{1}{N}
$

Used when population is homogeneous.

---

## 5.2 Stratified Sampling

Population divided into strata ( $S_1, S_2, \dots$ ).

$
x_i \sim P(X \mid X \in S_k)
$

Reduces variance. Extremely important for imbalanced ML datasets.

---

## 5.3 Importance Sampling

Sample from an easier distribution ( Q(x) ), reweight:

$
\mathbb{E}_P[f(X)] =
\mathbb{E}_Q\left[
f(X)\frac{P(X)}{Q(X)}
\right]
$

Used in:

* Reinforcement Learning
* Off-policy evaluation
* Variational inference

---

# 6. Sampling in Machine Learning (Where It Actually Matters)

## 6.1 Dataset = Sample from Reality

Your training data:
$
(x_i, y_i) \sim P_{\text{real}}(X, Y)
$

Your model learns:
$
P_\theta(y \mid x)
$

**If the sample is biased, the model is biased.**
No amount of architecture will save you.

---

## 6.2 Mini-Batch Sampling (SGD)

Full gradient:
$
\nabla L = \mathbb{E}_{(x,y)}[\nabla \ell(x,y)]
$

Approximation via sampling:

$
\nabla L \approx \frac{1}{B}\sum_{i=1}^{B} \nabla \ell(x_i,y_i)
$

This is why SGD works:

* Cheap
* Noisy
* Unbiased

Noise is not a bug — it helps generalization.

---

## 6.3 Sampling vs Shuffling (Important)

* **Shuffling** randomizes order
* **Sampling** selects subsets

No shuffle → correlated batches → bad convergence.

---

# 7. Sampling in Probabilistic Models

## 7.1 Sampling from a Distribution

Example: Gaussian

$
x = \mu + \sigma \epsilon, \quad \epsilon \sim \mathcal{N}(0,1)
$

This is how:

* VAEs generate data
* Diffusion models reverse noise

---

## 7.2 Ancestral Sampling (Autoregressive)

$
x_1 \sim P(x_1)
$
$
x_2 \sim P(x_2 \mid x_1)
$
$
\vdots
$

Used in:

* Language models
* Time-series generation

---

# 8. Sampling vs Optimization (People Confuse This)

| Optimization    | Sampling             |
| --------------- | -------------------- |
| Find best point | Explore distribution |
| Deterministic   | Stochastic           |
| MAP estimate    | Full posterior       |

ML training = optimization
ML generation = sampling

Confusing the two leads to:

* Mode collapse
* Overconfident models
* Boring outputs

---

# 9. Sampling Methods in ML (Practical)

## 9.1 Rejection Sampling

Accept sample if:
$
u < \frac{P(x)}{M Q(x)}
$

Simple, inefficient in high dimensions.

---

## 9.2 Markov Chain Monte Carlo (MCMC)

Construct a chain:
$
x_{t+1} \sim P(x_{t+1} \mid x_t)
$

Eventually samples from target distribution.

Used in:

* Bayesian inference
* Probabilistic programming

---

## 9.3 Gibbs Sampling

Sample one variable at a time:
$
x_i \sim P(x_i \mid x_{-i})
$

Used in:

* Topic models
* Graphical models

---

# 10. Sampling Mistakes That Kill ML Systems

### Mistake 1: Training ≠ Production sampling

$
P_{\text{train}}(x) \neq P_{\text{prod}}(x)
$

Silent model failure.

---

### Mistake 2: Class imbalance ignored

Uniform sampling hides minority classes.

---

### Mistake 3: Evaluation on sampled data

You evaluate the sampler, not the model.

---

# 11. Concrete Example (End-to-End)

### Problem

Estimate mean height of adults in India.

* Population unknown
* Sample 1,000 people randomly
* Compute:
$
\hat{\mu} = \frac{1}{1000}\sum x_i
$

This estimator:

* Unbiased
* Variance ( $\propto 1/1000$ )

Now imagine sampling only gym-goers.

Your estimator is mathematically correct — and practically useless.

---

# 12. Final Truth (No Sugar-Coating)

* Sampling is **how probability touches reality**
* ML models don’t learn truth — they learn from samples
* Bad sampling = confident nonsense
* Good sampling beats fancy models