## PART A — Fundamentals (1–10)

### 1. What is hypothesis testing?

**Answer:**
Hypothesis testing is a statistical procedure to decide whether observed data is compatible with an assumed hypothesis about a population parameter.

---

### 2. What is the null hypothesis ( $H_0$ )?

**Answer:**
The null hypothesis represents the default assumption or “no effect” scenario that the data is tested against.

---

### 3. What is the alternative hypothesis ( $H_1$ )?

**Answer:**
The alternative hypothesis represents the competing claim that contradicts the null hypothesis and reflects the effect or difference being tested.

---

### 4. Why do we test ( $H_0$ ) instead of ( $H_1$ )?

**Answer:**
Because ( $H_0$ ) is mathematically precise and easier to model. We reject or fail to reject ( $H_0$ ); we never directly prove ( $H_1$ ).

---

### 5. What is a test statistic?

**Answer:**
A test statistic is a function of sample data that quantifies deviation from what is expected under ( $H_0$ ).

---

### 6. What is the sampling distribution?

**Answer:**
It is the probability distribution of the test statistic assuming the null hypothesis is true.

---

### 7. What is a p-value?

**Answer:**
The p-value is the probability of observing data as extreme as (or more extreme than) the sample, assuming ( $H_0$ ) is true.

---

### 8. What does a small p-value indicate?

**Answer:**
That the observed data is unlikely under ( $H_0$ ), providing evidence against the null hypothesis.

---

### 9. What is the significance level ( $\alpha$ )?

**Answer:**
It is the maximum allowed probability of committing a Type I error, commonly set at 0.05.

---

### 10. What does “fail to reject ( $H_0$ )” mean?

**Answer:**
It means there is insufficient evidence against ( $H_0$ ); it does **not** mean ( $H_0$ ) is true.

---

## PART B — Errors & Interpretation (11–20)

### 11. What is a Type I error?

**Answer:**
Rejecting a true null hypothesis (false positive). Probability = ( $\alpha$ ).

---

### 12. What is a Type II error?

**Answer:**
Failing to reject a false null hypothesis (false negative). Probability = ( $\beta$ ).

---

### 13. What is statistical power?

**Answer:**
Power is the probability of correctly rejecting a false null hypothesis:
$
\text{Power} = 1 - \beta
$

---

### 14. How does sample size affect hypothesis testing?

**Answer:**
Larger samples reduce variance, increase power, and make it easier to detect small effects.

---

### 15. Why can very large datasets produce misleadingly small p-values?

**Answer:**
Because even trivial effects become statistically detectable with enough data, regardless of practical importance.

---

### 16. What is a one-tailed test?

**Answer:**
A test where the alternative hypothesis specifies a direction (e.g., $( \mu > \mu_0 )$).

---

### 17. What is a two-tailed test?

**Answer:**
A test where deviations in both directions are considered (e.g., $( \mu \neq \mu_0 )$).

---

### 18. When should a one-tailed test be avoided?

**Answer:**
When effects in the opposite direction are possible or meaningful.

---

### 19. What is multiple hypothesis testing?

**Answer:**
Testing many hypotheses simultaneously, which increases the chance of false positives.

---

### 20. Why are corrections (Bonferroni, FDR) needed?

**Answer:**
To control the overall Type I error rate when performing multiple tests.

---

## PART C — ML & Applied Testing (21–25)

### 21. How is A/B testing an example of hypothesis testing?

**Answer:**
It tests whether observed performance differences between two models or systems could be due to random chance.

---

### 22. Why is hypothesis testing necessary for model comparison?

**Answer:**
Because observed performance differences may arise from sampling noise, not real improvement.

---

### 23. What hypothesis is tested when evaluating a new ML feature?

**Answer:**
$
H_0: \text{Performance improvement} = 0
$

---

### 24. Why is accuracy alone insufficient for hypothesis testing?

**Answer:**
Accuracy ignores variability, uncertainty, and class imbalance; it provides no statistical confidence.

---

### 25. What is a permutation test and why is it useful in ML?

**Answer:**
It randomly shuffles labels to estimate performance under no relationship, avoiding distributional assumptions.

---

## PART D — HOTS (Higher Order Thinking Skills) (26–30)

### 26. Why does hypothesis testing not “prove” anything?

**Answer:**
Because it relies on probabilistic reasoning and controls error rates rather than establishing absolute truth.

---

### 27. Why is “p < 0.05” a policy choice rather than a scientific law?

**Answer:**
Because the threshold balances false positives and false negatives and depends on risk tolerance, not mathematics.

---

### 28. Why is repeated testing until significance unethical?

**Answer:**
Because it inflates Type I error and guarantees false discoveries (p-hacking).

---

### 29. Why can two models have different p-values but similar performance?

**Answer:**
Because p-values depend on sample size and variance, not just effect magnitude.

---

### 30. In ML systems, what is the biggest danger of ignoring hypothesis testing?

**Answer:**
Shipping models that appear improved but are actually indistinguishable from noise, leading to silent failures.

---

## Final straight truth

* Hypothesis testing is about **error control**, not truth discovery
* ML without testing is **guessing with confidence**
* Bigger data doesn’t replace statistical thinking — it amplifies mistakes