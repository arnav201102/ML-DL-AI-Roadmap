# 🔥 30 OPTIMIZATION HOTS QUESTIONS WITH SOLUTIONS

*(Maths + Machine Learning)*

---

## **Q1.**

Why does gradient descent slow down near the minimum even if the learning rate is constant?

### **Solution**

Because gradients become smaller near minima.
Update size = learning rate × gradient magnitude.
As slope → 0, steps → 0.

This is **mathematical inevitability**, not bad tuning.

---

## **Q2.**

Why can a larger learning rate cause divergence?

### **Solution**

Large steps overshoot the minimum, bouncing back and forth across steep slopes.
In convex functions, this causes oscillation; in non-convex ones, explosion.

---

## **Q3.**

Why does SGD often outperform full-batch gradient descent?

### **Solution**

SGD introduces noise that:

* Escapes saddle points
* Avoids sharp minima
* Improves generalization

Exact gradients are often **too stable**.

---

## **Q4.**

Why are saddle points more common than local minima in deep learning?

### **Solution**

In high dimensions:

* Probability of all eigenvalues > 0 (minimum) is low
* Mixed signs (saddle) dominate

Hence deep nets stall at saddles, not minima.

---

## **Q5.**

Why does momentum speed up convergence in narrow valleys?

### **Solution**

Momentum accumulates velocity in consistent directions, damping oscillations across steep sides while accelerating along flat directions.

---

## **Q6.**

Why does Adam sometimes generalize worse than SGD?

### **Solution**

Adam converges to **sharp minima** due to adaptive step scaling.
SGD noise biases toward **flat minima**, which generalize better.

---

## **Q7.**

Why is optimization harder for deep networks than shallow ones?

### **Solution**

* More non-linear compositions
* Vanishing/exploding gradients
* Ill-conditioned Hessians

Depth amplifies curvature issues.

---

## **Q8.**

Why does bad initialization break optimization?

### **Solution**

Poor initialization:

* Kills gradients (vanishing)
* Explodes activations
* Pushes parameters into flat or chaotic regions

Optimization never recovers.

---

## **Q9.**

Why does normalization improve optimization speed?

### **Solution**

Normalization:

* Reduces ill-conditioning
* Makes gradients uniform across dimensions
* Smooths the loss surface

Optimization becomes stable.

---

## **Q10.**

Why can loss temporarily increase during training?

### **Solution**

Because:

* Momentum overshoots
* Noise from SGD
* Learning rate too high

Temporary increase ≠ failure.

---

## **Q11.**

Why is convex optimization easier than non-convex?

### **Solution**

Convex functions have:

* One global minimum
* No saddle points
* Predictable convergence

Non-convex optimization has no such guarantees.

---

## **Q12.**

Why does reducing learning rate help convergence?

### **Solution**

Smaller learning rate allows fine-grained movement near minima, preventing oscillation.

This mimics **second-order behavior** cheaply.

---

## **Q13.**

Why is second-order optimization rarely used in deep learning?

### **Solution**

Hessian:

* Huge (millions × millions)
* Expensive to compute/invert
* Sensitive to noise

First-order methods scale better.

---

## **Q14.**

Why does over-parameterization help optimization?

### **Solution**

More parameters:

* Create smoother loss surfaces
* Increase number of flat minima
* Reduce bad local traps

Counterintuitive but proven.

---

## **Q15.**

Why does L2 regularization help optimization?

### **Solution**

It:

* Penalizes large weights
* Smooths curvature
* Prevents extreme gradients

Loss landscape becomes friendlier.

---

## **Q16.**

Why does optimization succeed even without finding the global minimum?

### **Solution**

Many minima yield similar loss values.
Generalization matters more than optimality.

---

## **Q17.**

Why do exploding gradients cause NaNs?

### **Solution**

Gradients grow exponentially → weight updates overflow → numerical instability.

This is math, not framework bugs.

---

## **Q18.**

Why do plateaus stall learning?

### **Solution**

Flat regions have near-zero gradients, giving no direction signal.

Optimizers need momentum or noise to escape.

---

## **Q19.**

Why does learning rate scheduling work?

### **Solution**

* Large LR explores
* Small LR exploits

This balances speed and precision.

---

## **Q20.**

Why does batch size affect optimization dynamics?

### **Solution**

Small batch:

* Noisy gradients
* Better generalization

Large batch:

* Stable gradients
* Risk of sharp minima

---

## **Q21.**

Why does gradient descent fail on poorly scaled features?

### **Solution**

Different scales → zig-zag paths → slow convergence.

Feature scaling fixes geometry.

---

## **Q22.**

Why do early layers learn slower than later layers?

### **Solution**

Gradients weaken as they backpropagate through layers (chain rule effect).

---

## **Q23.**

Why does loss landscape shape matter more than optimizer choice?

### **Solution**

Optimizer only follows gradients; landscape defines difficulty.

Bad geometry defeats any optimizer.

---

## **Q24.**

Why is zero gradient not always optimal?

### **Solution**

Zero gradient occurs at:

* Minima
* Maxima
* Saddle points

Second-order info distinguishes them.

---

## **Q25.**

Why does noise improve robustness?

### **Solution**

Noise forces exploration and avoids fragile solutions sensitive to perturbations.

---

## **Q26.**

Why do sharp minima overfit?

### **Solution**

Small parameter changes cause large loss changes → model is brittle.

---

## **Q27.**

Why does ReLU improve optimization over sigmoid?

### **Solution**

ReLU:

* Avoids vanishing gradients
* Preserves gradient flow

Sigmoid saturates quickly.

---

## **Q28.**

Why does optimization sometimes converge but accuracy remains poor?

### **Solution**

The model optimized the wrong objective or learned poor representations.

Optimization ≠ intelligence.

---

## **Q29.**

Why is loss surface visualization misleading in high dimensions?

### **Solution**

2D projections hide:

* Saddle structure
* Curvature anisotropy
* Flat directions

Visual intuition breaks down.

---

## **Q30.**

Why is optimization the *engineering* heart of ML?

### **Solution**

Because:

* Models don’t reason
* Data doesn’t self-organize
* Gradients drive everything

ML succeeds or fails at optimization.

---

## 🚀 FINAL TAKEAWAY

> **Deep learning is 20% models, 80% optimization behavior.**

If you understand:

* Landscapes
* Gradients
* Noise
* Geometry

You stop guessing and start **controlling training**.