
# **A️- Build Naive Bayes in Python (from scratch)**

### 📌 Classification Problem

Classify SMS as **Spam / Not Spam** based on words.

We'll implement:
1. Tokenizing
2. Counting word frequencies  
3. Calculating probabilities with Bayes
4. Predicting class

---

### **Python Code**



```python
import math
from collections import defaultdict

class NaiveBayesClassifier:
    def __init__(self):
        self.word_counts = {"spam": defaultdict(int), "ham": defaultdict(int)}
        self.class_counts = {"spam": 0, "ham": 0}
        self.vocab = set()

    def fit(self, data):
        for text, label in data:
            self.class_counts[label] += 1
            for word in text.lower().split():
                self.word_counts[label][word] += 1
                self.vocab.add(word)

    def predict(self, text):
        words = text.lower().split()
        total_docs = sum(self.class_counts.values())

        # priors
        p_spam = math.log(self.class_counts["spam"] / total_docs)
        p_ham = math.log(self.class_counts["ham"] / total_docs)

        for word in words:
            # Likelihood + Laplace smoothing
            p_spam += math.log((self.word_counts["spam"][word] + 1) /
                               (sum(self.word_counts["spam"].values()) + len(self.vocab)))
            p_ham += math.log((self.word_counts["ham"][word] + 1) /
                              (sum(self.word_counts["ham"].values()) + len(self.vocab)))

        return "spam" if p_spam > p_ham else "ham"


# TRAINING DATA
dataset = [
    ("win cash prize now", "spam"),
    ("limited time offer claim prize", "spam"),
    ("hello how are you", "ham"),
    ("let us meet tomorrow", "ham"),
]

model = NaiveBayesClassifier()
model.fit(dataset)

# TEST
print(model.predict("claim your prize now"))   # → spam
print(model.predict("meet tomorrow morning"))  # → ham
```

---

### ✔️ Output

```
spam
ham
```

### 🤖 Intuition

Every word **pushes the probability** toward spam or ham.
More “spammy” words = stronger belief in spam.

---

# **B️- Visualize Bayes Using Probability Charts**

Imagine seeing the word **"FREE"**.

| Event       | Probability | 
| ----------- | ----------- | 
| P(Spam)     | 0.3         | 
| P(Free/Spam)       | 0.8 |
| P(Free /Not Spam)   | 0.1 |
| P(Not Spam) | 0.7         |

---

### **Bayes Update Chart**

```
                       ┌───────────────┐
                30%    │   SPAM        │
               ───────▶│ P(S)=0.3      │
               │       └─────┬─────────┘
               │             │ 0.8
               │             ▼
   "FREE"──────┤         P(Free|Spam)=0.8
               │             ▲
               │             │
               │       ┌─────┴─────────┐
                70%    │ NOT SPAM      │
               ───────▶│ P(NS)=0.7     │
                       └───────────────┘
                             0.1
```

Now normalize:
$$
P(\text{Spam|FREE}) = \frac{0.8 \cdot 0.3}{(0.8\cdot0.3) + (0.1\cdot0.7)}=0.774
$$

📌 **Final Effect**

> Before evidence: 30% spam
> After evidence: 77% spam

---

# **C️- 20 Exam-Level Questions + Answers**

### (with deeper reasoning explanations)

| #  | Question                                 | Answer (detailed)                                                                |                                                        |     |
| -- | ---------------------------------------- | -------------------------------------------------------------------------------- | ------------------------------------------------------ | --- |
| 1  | Define Bayes theorem.                    | Posterior = Prior × Likelihood / Evidence. It updates beliefs after seeing data. |                                                        |     |
| 2  | What is a posterior probability?         | (P(A/B)) — probability of A after incorporating evidence B. |     |
| 3  | Why is (P(B)) needed? (denominator)      | It normalizes to ensure probabilities sum to 1. Makes it a valid distribution.   |                                                        |     |
| 4  | Difference: prior vs posterior.          | Prior: before data. Posterior: after data.                                       |                                                        |     |
| 5  | What does Naive mean in NB?              | Assumes feature independence → simplifies likelihood calc.                       |                                                        |     |
| 6  | Why Naive Bayes is fast?                 | Counts frequencies; no optimization; closed-form probability update.             |                                                        |     |
| 7  | What happens if feature never appears?   | Probability becomes 0 → fixed by Laplace smoothing (+1).                         |                                                        |     |
| 8  | Why use log probabilities?               | Avoids underflow; addition is easier than multiplying tiny values.               |                                                        |     |
| 9  | When does NB fail?                       | When features are dependent (e.g., “very good” sentiment phrase).                |                                                        |     |
| 10 | When is NB better than Neural Nets?      | Small data, fast training, text data, simple interpretability.                   |                                                        |     |
| 11 | Is NB generative or discriminative?      | Generative — models joint distribution (P(X, Y)).                                |                                                        |     |
| 12 | Log-likelihood formula for NB?           | (\log P(Y/ X)=\log P(Y)+\sum\log P(x_i/ Y)) |
| 13 | In spam filtering, what is Y and X?      | Y = class (spam/ham), X = words.                                                 |                                                        |     |
| 14 | Role of Laplace smoothing?               | Prevents zero probability; stabilizes results.                                   |                                                        |     |
| 15 | Compute posterior if P(A)=0.4, P(B/A)=0.5, P(B)=0.2                                                                 | = 1.0 (A and B fully correlated here).                 |     |
| 16 | Why NB is robust to irrelevant features? | Irrelevant features cancel across classes; don't bias strongly.                  |                                                        |     |
| 17 | What is evidence?                        | Total probability of observing data across all classes.                          |                                                        |     |
| 18 | Why NB good for text?                    | Bag of words fits independence assumption well.                                  |                                                        |     |
| 19 | Define conditional independence.         | Features independent given the class.                                            |                                                        |     |
| 20 | ML model type of NB?                     | Probabilistic classifier based on Bayes’ rule.                                   |                                                        |     |

---

# **D️⃣ Connect Bayes to Deep Learning**

### **Where Bayes appears in DL**

| DL Concept                 | Bayesian Interpretation                                  |         |
| -------------------------- | -------------------------------------------------------- | ------- |
| Dropout                    | Approximate Bayesian inference (random networks sampled) |         |
| Softmax outputs            | Posterior probabilities (P(Class                         / Input)) |
| Uncertainty Quantification | Bayesian neural networks                                 |         |
| Loss Functions             | Negative log-likelihood = maximizing posterior           |         |
| Variational Autoencoders   | Bayes + latent variable modeling                         |         |
| Bayesian Optimization      | Hyperparameter tuning via posterior updates              |         |

---

### **Bayesian Neural Networks**

Weights aren’t fixed numbers — they’re **distributions**:

$$
W \sim \mathcal{N}(\mu, \sigma^2)
$$

Prediction becomes:

$$
P(Y|X) = \int P(Y|X,W)P(W)dW
$$

📌 We’re integrating over uncertainty.

Used in:

* medical AI
* self-driving vehicles
* safety-critical applications

---

### **Dropout as Bayesian Inference**

Running dropout at inference time = Monte-Carlo sampling.

$$
\hat{y} = \frac{1}{N}\sum_{i=1}^N f(X;W_i)
$$

Each pass gives a different (W_i).

**Variation = uncertainty measure**.

---

# 🎯 FINAL CHEAT SHEET

| Term        | Meaning                              |
| ----------- | ------------------------------------ |
| Prior       | Belief before data                   |
| Likelihood  | Fit of data to assumption            |
| Evidence    | Normalizer                           |
| Posterior   | Belief after data                    |
| Bayes in ML | Core of probabilistic classification |
| Naive Bayes | Fast baseline classifier             |
| Bayes + DL  | Uncertainty + better decision making |