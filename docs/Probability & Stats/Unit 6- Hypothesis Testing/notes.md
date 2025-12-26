# 1. What Hypothesis Testing Really Is (Math First)

### Core idea (one sentence)

> **Hypothesis testing is a formal procedure to decide whether observed data is compatible with an assumed probability model.**

That’s it.
Not “proving truth”, not “finding facts” — **testing compatibility**.

---

## 1.1 The Ingredients (Always the Same)

Every hypothesis test has **five components**:

1. **Null hypothesis** ( H_0 )
2. **Alternative hypothesis** ( H_1 )
3. **Test statistic** ( T(X) )
4. **Sampling distribution** of ( T ) under ( H_0 )
5. **Decision rule** (p-value or rejection region)

If any of these are fuzzy, the test is invalid.

---

## 1.2 Null and Alternative Hypotheses

### Null hypothesis ( H_0 )

* Default assumption
* Represents “no effect”, “status quo”, or “random chance”

Example:
$
H_0: \mu = 50
$

### Alternative hypothesis ( H_1 )

* What you suspect might be true

Examples:

* Two-sided: ( \mu \neq 50 )
* One-sided: ( \mu > 50 )

**Important:**
You do **not** prove ( H_1 ).
You only decide whether to **reject ( H_0 )**.

---

## 1.3 Test Statistic (Turning Data into a Number)

A test statistic is a function of the sample:

$
T = T(X_1, X_2, \dots, X_n)
$

Example (Z-statistic):
$
Z = \frac{\bar{X} - \mu_0}{\sigma/\sqrt{n}}
$

It measures **how far the data deviates from what ( H_0 ) predicts**.

---

## 1.4 Sampling Distribution (The Forgotten Part)

Under ( H_0 ), the test statistic has a known distribution.

Examples:

* Z-test → Normal distribution
* t-test → t-distribution
* Chi-square test → ( \chi^2 )

This is where probability theory enters.

---

## 1.5 p-value (Most Abused Concept in Statistics)

### Definition (precise)

$
\boxed{
\text{p-value} = P(\text{data as extreme as observed} \mid H_0)
}
$

### What it is NOT

* ❌ Probability that ( H_0 ) is true
* ❌ Probability that results are due to chance
* ❌ Strength of effect

### What it IS

* A **compatibility score** between data and ( H_0 )

Small p-value → data looks weird if ( H_0 ) were true.

---

## 1.6 Decision Rule

Choose a significance level ( \alpha ) (usually 0.05).

* If p-value ( \le \alpha ) → reject ( H_0 )
* Else → fail to reject ( H_0 )

This is a **policy decision**, not a law of nature.

---

# 2. Errors in Hypothesis Testing (Non-Negotiable)

| Reality       | Decision       | Error         |
| ------------- | -------------- | ------------- |
| ( H_0 ) true  | Reject ( H_0 ) | Type I error  |
| ( H_0 ) false | Fail to reject | Type II error |

* Type I error rate = ( \alpha )
* Type II error = ( \beta )
* Power = ( 1 - \beta )

ML people ignore this at their own risk.

---

# 3. Concrete Mathematical Example

### Problem

A factory claims mean battery life = 100 hours.
Sample of 25 batteries gives:

* ( \bar{x} = 96 )
* ( \sigma = 10 )

### Step 1: Hypotheses

$
H_0: \mu = 100
\quad
H_1: \mu < 100
$

### Step 2: Test statistic

$
Z = \frac{96 - 100}{10/\sqrt{25}} = \frac{-4}{2} = -2
$

### Step 3: p-value

$
P(Z \le -2) \approx 0.0228
$

### Step 4: Decision

At ( \alpha = 0.05 ), reject ( H_0 ).

### Interpretation

Data is unlikely if mean were truly 100 hours.

---

# 4. Hypothesis Testing in Machine Learning (Reality Check)

Here’s the truth:

> **ML rarely uses classical hypothesis tests directly — but the logic is everywhere.**

---

## 4.1 A/B Testing (ML’s Most Common Hypothesis Test)

### Example: Two recommendation models

* Model A CTR = 4.8%
* Model B CTR = 5.1%

### Hypotheses

$
H_0: \text{CTR}_A = \text{CTR}_B
$
$
H_1: \text{CTR}_A \neq \text{CTR}_B
$

Data → test statistic → p-value → decision.

**If you ship models without this, you’re gambling.**

---

## 4.2 Feature Significance in Models

In linear/logistic regression:

$
H_0: \beta_j = 0
$

A low p-value means:

> Feature contributes signal beyond noise

But:

* Correlation ≠ causation
* Multicollinearity can lie to you

---

## 4.3 Model Comparison (Often Done Wrong)

People say:

> “Model B accuracy is higher”

Wrong question.

Correct question:
$
H_0: \text{Performance difference} = 0
$

Use:

* Paired t-test
* Bootstrap tests
* McNemar’s test

Otherwise you’re reacting to sampling noise.

---

## 4.4 Permutation Tests (ML-Friendly)

### Idea

Break the relationship between X and y deliberately.

Steps:

1. Shuffle labels
2. Train model
3. Measure performance
4. Repeat

p-value = fraction of shuffled runs outperforming real data.

This avoids distributional assumptions — perfect for ML.

---

# 5. Hypothesis Testing vs Bayesian Thinking (Important)

| Frequentist Testing | Bayesian Inference                 |
| ------------------- | ---------------------------------- |
| Tests ( H_0 )       | Computes ( P(H \mid \text{data}) ) |
| p-value             | Posterior probability              |
| Long-run guarantees | Direct probability statements      |

ML increasingly prefers Bayesian reasoning — but testing logic still matters.

---

# 6. Common ML-Specific Mistakes (Brutal but True)

### Mistake 1: “p < 0.05 means important”

No. It means **detectable**, not **useful**.

---

### Mistake 2: Multiple testing ignored

Testing 100 features guarantees false positives unless corrected.

---

### Mistake 3: Large data = tiny p-values

With enough data, **everything becomes significant**.

Effect size matters more.

---

### Mistake 4: Testing after peeking

Repeated testing until significance = statistical fraud.

---

# 7. ML-Flavored Example (End-to-End)

### Problem

You add a new feature to a fraud model.

Observed improvement:

* AUC increases from 0.842 → 0.846

Question:

> Is this real or noise?

### Hypothesis test

$
H_0: \Delta \text{AUC} = 0
$

Use bootstrap resampling → confidence interval.

If CI excludes 0 → reject ( H_0 ).

That’s hypothesis testing, even if nobody says the name.

---

# 8. Final Truth (No Sugar-Coating)

* Hypothesis testing does **not** discover truth
* It controls how often you fool yourself
* In ML, it protects you from shipping noise

If you don’t explicitly ask:

> “Could this result happen by chance?”

You are not doing science. You’re doing numerology.

---

---

# 1. What exactly is a “test” in hypothesis testing?

A **statistical test** is a **decision rule**.

> Given data + assumptions → compute a statistic → compare it to a reference distribution → make a decision with controlled error.

Formally, a test consists of:

1. A **null hypothesis** ( H_0 )
2. A **test statistic** ( T(X) )
3. A **sampling distribution of ( T )** under ( H_0 )
4. A **decision rule** (critical value or p-value)

---

# 2. General structure of ANY hypothesis test

No matter the test name (t-test, z-test, chi-square…), the pipeline is always:

### Step 1: Define hypotheses

Example:
$
H_0: \mu = \mu_0 \quad,\quad H_1: \mu \neq \mu_0
$

---

### Step 2: Choose a test statistic

Something that measures deviation from ( H_0 ):
$
T = \frac{\text{Observed} - \text{Expected}}{\text{Standard Error}}
$

---

### Step 3: Know its distribution under ( H_0 )

* Normal
* t
* Chi-square
* F
* Empirical (resampling)

---

### Step 4: Compute p-value OR compare with critical value

---

### Step 5: Decision

* Reject ( H_0 )
* Fail to reject ( H_0 )

That’s it. Every test is a variation of this.

---

# 3. Classification of hypothesis tests (BIG PICTURE)

Tests can be classified along **multiple dimensions**.

---

## A. Based on distribution assumptions

### 1. Parametric tests

Assume a specific population distribution.

Examples:

* z-test
* t-test
* ANOVA
* F-test

✅ Powerful
❌ Sensitive to assumption violations

---

### 2. Non-parametric tests

Do **not** assume population distribution.

Examples:

* Mann–Whitney U
* Wilcoxon signed-rank
* Kruskal–Wallis
* Permutation tests

✅ Robust
❌ Less powerful if parametric assumptions hold

---

## B. Based on number of samples

### 1. One-sample tests

Compare sample to a known value.

Example:

* One-sample t-test

---

### 2. Two-sample tests

Compare two groups.

Example:

* Independent t-test
* Mann–Whitney U

---

### 3. Paired tests

Same subjects measured twice.

Example:

* Paired t-test
* Wilcoxon signed-rank

---

## C. Based on directionality

### 1. One-tailed tests

Directional hypothesis:
$
H_1: \mu > \mu_0
$

Used only when direction is pre-justified.

---

### 2. Two-tailed tests

Non-directional:
$
H_1: \mu \neq \mu_0
$

Default and safer choice.

---

## D. Based on what is being tested

| Goal             | Typical Test       |
| ---------------- | ------------------ |
| Mean             | z, t               |
| Variance         | Chi-square         |
| Proportion       | z-test             |
| Association      | Chi-square         |
| Correlation      | Pearson / Spearman |
| Model comparison | Likelihood ratio   |

---

# 4. Core tests you MUST know (with intuition)

---

## 1. z-test

### When to use

* Population variance known
* Large sample (rare in practice)

### Statistic

$
z = \frac{\bar{x} - \mu_0}{\sigma / \sqrt{n}}
$

### Interpretation

“How many standard errors away from expectation?”

---

## 2. t-test (MOST IMPORTANT)

Used when population variance is unknown.

### Types:

* One-sample t-test
* Independent two-sample t-test
* Paired t-test

### Why t-distribution?

Because estimating variance introduces extra uncertainty.

---

### Independent t-test assumptions

1. Independence
2. Normality (or large ( n ))
3. Equal variances (or use Welch’s t-test)

---

### Welch’s t-test (IMPORTANT)

Used when variances differ.
**Default choice in practice.**

---

## 3. Chi-square tests

### A. Chi-square goodness-of-fit

Checks if observed frequencies match expected frequencies.

$
\chi^2 = \sum \frac{(O - E)^2}{E}
$

---

### B. Chi-square test of independence

Tests association between categorical variables.

Example:

* Gender vs purchase decision

---

## 4. ANOVA (Analysis of Variance)

Used to compare **means of 3+ groups**.

Key idea:

> Compare **between-group variance** to **within-group variance**

$
F = \frac{\text{Between variance}}{\text{Within variance}}
$

---

### IMPORTANT

ANOVA tests:
$
H_0: \mu_1 = \mu_2 = \mu_3 = ...
$

It does NOT tell which groups differ — needs **post-hoc tests**.

---

## 5. Correlation tests

### Pearson correlation

* Linear relationship
* Assumes normality

### Spearman correlation

* Rank-based
* Non-parametric

---

# 5. Assumptions (and why they matter)

| Assumption      | Why it matters                     |
| --------------- | ---------------------------------- |
| Independence    | Violations inflate false positives |
| Normality       | Affects tail probabilities         |
| Equal variance  | Biases standard errors             |
| Random sampling | Otherwise inference is meaningless |

Violating assumptions ≠ test invalid, but **interpretation weakens**.

---

# 6. Effect size (CRIMINALLY IMPORTANT)

Statistical significance ≠ practical importance.

### Examples:

* Cohen’s d (means)
* Odds ratio
* Correlation magnitude

Large datasets make **tiny effects significant**.

> Always report effect size + CI.

---

# 7. Confidence intervals vs hypothesis testing

They are two sides of the same coin.

If:

* CI excludes null value → reject ( H_0 )
* CI includes null → fail to reject

CI is usually **more informative**.

---

# 8. Hypothesis testing in ML (REALITY)

---

## A. Model comparison

$
H_0: \text{Model A performance} = \text{Model B performance}
$

Used in:

* A/B testing
* Feature validation
* Architecture selection

---

## B. Why CV scores alone are not enough

Because:

* CV splits introduce randomness
* Metrics have variance

Use:

* Paired t-test on CV folds
* Bootstrap CI
* Permutation tests

---

## C. Permutation tests (ML gold standard)

Steps:

1. Shuffle labels
2. Compute metric
3. Repeat
4. Compare observed metric to null distribution

No assumptions. Extremely powerful.

---

# 9. Common mistakes (be ruthless)

❌ Interpreting p-value as probability that ( H_0 ) is true
❌ Treating 0.05 as magic
❌ Ignoring effect size
❌ Multiple testing without correction
❌ Testing after looking at data (p-hacking)
❌ Using parametric tests blindly

---

# 10. Mental model to remember forever

> **Hypothesis testing is a controlled gambling system**
> You decide how much error you tolerate **before seeing data**, then stick to the rules.