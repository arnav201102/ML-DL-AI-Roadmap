# 1. What does “testing” really mean? (with example)

**Testing = asking whether an observed pattern is real or just noise.**

### Example (simple)

You flip a coin 100 times → 62 heads.

Question:

> Is this coin biased, or is 62 just random fluctuation?

This is a **hypothesis test**.

* ( $H_0$ ): Coin is fair (p = 0.5)
* ( $H_1$ ): Coin is biased (p ≠ 0.5)

A **test** tells you whether 62 is “too extreme” to be explained by randomness alone.

---

# 2. Universal testing workflow (applies to ALL tests)

Every test follows this pipeline:

1. Define hypotheses
2. Choose test statistic
3. Know its distribution under ( $H_0$ )
4. Compute statistic from data
5. Compute p-value / critical region
6. Decide

Different tests = different statistics + distributions.

---

# 3. Classification of ALL tests (big picture)

## A. Based on **data type**

| Data                 | Typical Tests          |
| -------------------- | ---------------------- |
| Numerical (mean)     | z-test, t-test, ANOVA  |
| Categorical (counts) | Chi-square, Fisher     |
| Ranks                | Wilcoxon, Mann–Whitney |
| Correlation          | Pearson, Spearman      |
| Model metrics        | Permutation, bootstrap |

---

## B. Based on **number of groups**

| Groups | Tests                  |
| ------ | ---------------------- |
| 1      | One-sample tests       |
| 2      | Two-sample tests       |
| ≥3     | ANOVA / Kruskal–Wallis |

---

## C. Based on **assumptions**

| Assumptions                | Tests          |
| -------------------------- | -------------- |
| Normality assumed          | Parametric     |
| No distribution assumption | Non-parametric |

---

# 4. PARAMETRIC TESTS (assume distributions)

---

## 4.1 One-Sample z-Test (rare but foundational)

### Use when

* Population variance known
* Large sample

### Example

A factory claims bulb lifetime = **1000 hours**
Sample: mean = 970, σ = 100, n = 100

$
z = \frac{970 - 1000}{100/\sqrt{100}} = -3
$

p-value ≈ 0.003 → Reject ( $H_0$ )

**Interpretation:** Average life is significantly lower.

---

## 4.2 One-Sample t-Test (VERY common)

### Use when

* Population variance unknown

### Example

Average exam score historically = 70
New teaching method → sample mean = 75 (n = 20)

$
t = \frac{75 - 70}{s/\sqrt{20}}
$

Compare to t-distribution.

**Why t?**
Because estimating variance adds uncertainty → heavier tails.

---

## 4.3 Two-Sample Independent t-Test

### Question

Are two groups different?

### Example

Drug A vs Drug B blood pressure reduction

* Group A mean = 12
* Group B mean = 8

$
H_0: \mu_A = \mu_B
$

If variances unequal → **Welch’s t-test (default in practice)**

---

## 4.4 Paired t-Test

### Use when

Same subjects measured twice.

### Example

Weight before and after diet program

Test is applied to **differences**, not raw values.

Why powerful?
→ Removes individual variability.

---

## 4.5 ANOVA (3+ means)

### Question

Do at least **one** group differ?

### Example

Test scores from 4 different teaching methods

$
H_0: \mu_1 = \mu_2 = \mu_3 = \mu_4
$

ANOVA compares:

* Variance between groups
* Variance within groups

Big ratio → real difference.

⚠ ANOVA doesn’t say *which* groups differ → post-hoc tests needed.

---

# 5. TESTS FOR CATEGORICAL DATA

---

## 5.1 Chi-Square Test of Independence

### Example

Is **gender** related to **purchase decision**?

|        | Buy | Not Buy |
| ------ | --- | ------- |
| Male   | 40  | 60      |
| Female | 70  | 30      |

$
\chi^2 = \sum \frac{(O - E)^2}{E}
$

Large χ² → reject independence.

---

## 5.2 Chi-Square Goodness-of-Fit

### Example

Are dice outcomes uniform?

Expected: each face = 1/6
Observed: frequencies differ

Tests whether observed distribution matches theoretical.

---

## 5.3 Fisher’s Exact Test

Used instead of chi-square when:

* Sample size is small
* Expected counts < 5

Exact, not approximate.

---

# 6. NON-PARAMETRIC TESTS (robust)

Used when:

* Non-normal data
* Outliers
* Ordinal/rank data

---

## 6.1 Mann–Whitney U Test

(Non-parametric alternative to two-sample t-test)

### Example

Compare salaries between two companies (skewed data)

Works on **ranks**, not raw values.

---

## 6.2 Wilcoxon Signed-Rank Test

(Non-parametric paired test)

### Example

Customer satisfaction before vs after policy change

---

## 6.3 Kruskal–Wallis Test

(Non-parametric ANOVA)

### Example

Compare median delivery times across 5 regions

---

# 7. CORRELATION TESTS

---

## 7.1 Pearson Correlation Test

Tests:
$
H_0: \rho = 0
$

Assumes:

* Linear relationship
* Normality

---

## 7.2 Spearman Rank Correlation

Used when:

* Nonlinear but monotonic relationship
* Ordinal data

Example: Rank vs income.

---

# 8. RESAMPLING-BASED TESTS (ML-friendly)

---

## 8.1 Permutation Test (ML GOLD)

### Example (model comparison)

Model A accuracy = 82%
Model B accuracy = 84%

Is 2% real?

Steps:

1. Shuffle labels
2. Recompute difference
3. Build null distribution
4. Check where observed difference lies

No assumptions. Extremely reliable.

---

## 8.2 Bootstrap Tests

Used to:

* Estimate confidence intervals
* Compare metrics

Heavy use in ML & production systems.

---

# 9. ONE-TAILED vs TWO-TAILED (with example)

### Two-tailed

“Different in any direction”

$
H_1: \mu \neq \mu_0
$

Default.

---

### One-tailed

“Better only”

$
H_1: \mu > \mu_0
$

⚠ Must be justified **before** seeing data.

---

# 10. HYPOTHESIS TESTING IN ML (REAL USE)

---

## Example 1: A/B testing

* $( H_0 ): Conversion_A = Conversion_B$
* Use z-test / permutation test

---

## Example 2: Feature validation

Does adding feature X improve F1 score?

Use:

* Paired test on CV folds
* Bootstrap CI

---

## Example 3: Monitoring drift

Test whether feature distribution changed:

* KS test
* Chi-square

---

# 11. Which test should I use? (decision logic)

Ask in order:

1. Data type? (numeric / categorical)
2. How many groups?
3. Paired or independent?
4. Normality reasonable?
5. Sample size large?

If unsure → **permutation test**.

---

# 12. Brutal truths (important)

* p-value ≠ probability null is true
* Statistical significance ≠ business significance
* Large data makes tiny effects “significant”
* No test fixes biased data
* Wrong test → confident nonsense

---

## Bottom line

> A test is not a formula — it’s a **decision under uncertainty with controlled error**.