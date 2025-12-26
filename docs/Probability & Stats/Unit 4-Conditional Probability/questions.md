# Section A — Core Conceptual Questions (1–10)

1. What does ( $P(A \mid B)$ ) mean **in words**? How is it different from ( P(A) )?

2. Why must ( P(B) > 0 ) for conditional probability to be defined?

3. Explain conditional probability as a **change of sample space**.

4. Is ( $P(A \mid B) = P(B \mid A)$ )? If not, why do people confuse them?

5. If ( $P(A \mid B) = P(A)$ ), what does that say about A and B?

6. Can ( $P(A \mid B) > P(A)$ )? Give an intuitive explanation.

7. If two events are mutually exclusive, what is ( $P(A \mid B)$ )?

8. Explain the difference between:

  * $( P(A \cap B) )$
  * $( P(A \mid B) )$

9. Does conditional probability imply causation? Why or why not?

10. Why is conditional probability called “conditional” and not “dependent” probability?

---

# Section B — Mathematical & Derivation Questions (11–20)

11. Derive the conditional probability formula from the definition of joint probability.

12. Prove that:
   $
   P(A \cap B) = P(A \mid B)P(B)
   $

13. Show how Bayes’ theorem follows directly from conditional probability.

14. If ( A $\subseteq B$ ), compute ($ P(A \mid B) $).

15. If ( A $\subseteq B $), compute ($ P(B \mid A) $).

16. Let ( P(A)=0.6 ), ( P(B)=0.5 ), ($ P(A \cap B)=0.3 $).
   Are A and B independent? Justify mathematically.

17. Show that conditional probability is itself a valid probability measure.

18. If events A, B, C are such that:
   $
   P(A \mid B \cap C) = P(A)
   $
   What does this imply about the relationship between A and ($ B \cap C $)?

19. Explain mathematically why:
   $
   P(A \mid B) + P(\neg A \mid B) = 1
   $

20. For random variables X and Y, write the conditional probability in terms of joint and marginal distributions.

---

# Section C — Applied & Word Problems (21–25)

21. A factory has two machines.  
   Machine A produces 60% of items with a 2% defect rate.  
   Machine B produces 40% of items with a 5% defect rate.  
   If an item is defective, what is the probability it came from Machine B?  

22. In a class, 70% students like math, 50% like physics, and 40% like both.
   Find:

* $( P(\text{Math} \mid \text{Physics}) )$
* $( P(\text{Physics} \mid \text{Math}) )$

23. Two dice are rolled.
   Given that the sum is even, what is the probability that both dice show even numbers?

24. A card is drawn from a deck.
   Given that it is a face card, what is the probability it is a king?

25. A test has 95% sensitivity and 90% specificity.
   The disease prevalence is 2%.
   If a person tests positive, compute ($ P(\text{disease} \mid \text{positive}) $).

---

# Section D — HOTS / Higher-Order Thinking Questions (26–30)

These are **conceptual stress tests**. Expect to think, not calculate.

---

26. A model predicts:
   $
   P(\text{fraud} \mid x) = 0.2
   $
   If the base fraud rate is 0.1%, explain why this prediction is **extremely strong**, even though 0.2 looks small.

---

27. Two ML models output probabilities.
   Model A is more accurate.
   Model B has lower cross-entropy loss.
   Which one better estimates conditional probability ( $P(y \mid x)$ )? Why?

---

28. Explain why dataset shift breaks the assumption:
   $
   P_{\text{train}}(y \mid x) = P_{\text{production}}(y \mid x)
   $
   Give a real-world example.

---

29. A classifier always predicts the majority class with 99% accuracy.
   Explain why this model has learned almost nothing about conditional probability.

---

30. In Naive Bayes, why is the assumption:
   $
   P(x_1, x_2, \dots, x_n \mid y) = \prod_i P(x_i \mid y)
   $
   often false — and why does the model still work reasonably well?

---
# Solutions
---

# Section A — Core Conceptual (1–10)

### 1. Meaning of ($ P(A \mid B)$ )

Probability that **A occurs given B has already occurred**.
Unlike ( P(A) ), it is computed in a **restricted sample space** where B is true.

---

### 2. Why ( P(B) > 0 )?

Because:
$
P(A \mid B) = \frac{P(A \cap B)}{P(B)}
$
Division by zero is undefined → conditioning on an impossible event is meaningless.

---

### 3. Conditional probability as change of sample space

Original sample space → reduced to only outcomes where **B occurs**.
Probabilities are **renormalized** inside this smaller space.

---

### 4. Is ($ P(A \mid B) = P(B \mid A) $)?

No.
$
P(A \mid B) = \frac{P(A \cap B)}{P(B)}, \quad
P(B \mid A) = \frac{P(A \cap B)}{P(A)}
$
Different denominators → different values.

---

### 5. If ($ P(A \mid B) = P(A) $)?

A and B are **independent**.
Knowing B gives no information about A.

---

### 6. Can ($ P(A \mid B) > P(A) $)?

Yes.
B can increase the likelihood of A (positive dependence).

---

### 7. If A and B are mutually exclusive

$
P(A \cap B) = 0 \Rightarrow P(A \mid B) = 0
$

---

### 8. Difference between ( $P(A \cap B) ) and ( P(A \mid B)$ )

* $( P(A \cap B) )$: probability both occur
* $( P(A \mid B) )$: probability A occurs **assuming B already occurred**

---

### 9. Does conditional probability imply causation?

No.
It captures **association**, not cause–effect.

---

### 10. Why “conditional” and not “dependent”?

Because probability is **computed under a condition**, not necessarily implying dependence.

---

# Section B — Mathematical (11–20)

### 11. Derivation of conditional probability

From joint probability:
$
P(A \cap B) = P(A \mid B)P(B)
\Rightarrow P(A \mid B) = \frac{P(A \cap B)}{P(B)}
$

---

### 12. Proof of multiplication rule

Directly from definition (above).

---

### 13. Bayes’ theorem derivation

$
P(A \cap B) = P(A \mid B)P(B) = P(B \mid A)P(A)
$
$
\Rightarrow P(A \mid B) = \frac{P(B \mid A)P(A)}{P(B)}
$

---

### 14. If ( $A \subseteq B$ ), find ( $P(A \mid B) $)

$
P(A \mid B) = \frac{P(A)}{P(B)}
$

---

### 15. If ( $A \subseteq B$ ), find ( $P(B \mid A)$ )

$
P(B \mid A) = 1
$

---

### 16. Given:

* ( P(A)=0.6 )
* ( P(B)=0.5 )
* ( $P(A \cap B)$=0.3 )

Check independence:
$
P(A)P(B)=0.3 = P(A \cap B)
$
✅ Independent.

---

### 17. Show conditional probability is valid

For fixed B:

* Non-negative
* Sums to 1
* Additive over disjoint events
Hence, a valid probability measure.

---

### 18. If ( $P(A \mid B \cap C)$ = P(A) )

A is **independent of the combined event ( $B \cap C$ )**.

---

### 19. Why ( $P(A \mid B) + P(\neg A \mid B)$ = 1 )

Because ( $A \cup \neg A$ ) exhausts the conditional sample space.

---

### 20. Conditional probability for random variables

$
P(Y=y \mid X=x) = \frac{P(X=x, Y=y)}{P(X=x)}
$

---

# Section C — Applied Problems (21–25)

### 21. Factory machines

Defective probability:
$
P(D) = 0.6(0.02) + 0.4(0.05) = 0.032
$

Probability from B given defective:
$
P(B \mid D) = \frac{0.4 \cdot 0.05}{0.032} = 0.625
$

---

### 22. Class preferences

$
P(M \mid P) = \frac{0.4}{0.5} = 0.8
$
$
P(P \mid M) = \frac{0.4}{0.7} \approx 0.571
$

---

### 23. Dice problem

Even sum outcomes = 18
Both dice even outcomes = 9

$
P = \frac{9}{18} = 0.5
$

---

### 24. Face card → king

Face cards = 12
Kings = 4

$
P = \frac{4}{12} = \frac{1}{3}
$

---

### 25. Medical test

$
P(+)=0.95(0.02)+0.10(0.98)=0.117
$

$
P(D \mid +)=\frac{0.95 \cdot 0.02}{0.117} \approx 0.162
$

Only **16.2%** actually have the disease.

---

# Section D — HOTS (26–30)

### 26. Why 0.2 is extremely strong

Base rate = 0.1%
Prediction = 20%
That’s **200× the base probability** → massive signal.

---

### 27. Accuracy vs cross-entropy

Model B.
Lower cross-entropy means **better estimation of ( $P(y \mid x)$ )**.
Accuracy ignores probability quality.

---

### 28. Dataset shift explanation

The relationship between x and y changed.
Example:
Fraud patterns pre- and post-UPI adoption.

---

### 29. Why 99% accuracy is meaningless

Model learned:
$
P(y=\text{majority} \mid x) \approx 1
$
No discrimination, no conditional learning.

---

### 30. Why Naive Bayes works despite false assumption

Independence is false, but:

* Errors often cancel
* Decision boundaries remain useful
* Relative likelihoods still informative

It’s **wrong but useful**.

---

## Final reality check

If you truly understand these solutions:

* You understand Bayes
* You understand ML loss functions
* You won’t misuse “confidence scores”