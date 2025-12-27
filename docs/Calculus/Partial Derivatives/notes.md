## 1. What is a Partial Derivative (Math first, no ML yet)

### Formal definition

For a multivariable function:

$$
f(x, y, z, \dots)
$$

The **partial derivative w.r.t. x** is:

$$
\frac{\partial f}{\partial x}
=

\lim_{h \to 0}
\frac{f(x+h, y, z) - f(x, y, z)}{h}
$$

Key idea:

> **Change only one variable. Freeze the rest.**

---

### Simple example

$$
f(x, y) = x^2 + 3xy + y^2
$$

$$
\frac{\partial f}{\partial x} = 2x + 3y
$$
$$
\frac{\partial f}{\partial y} = 3x + 2y
$$

Interpretation:

* `x` and `y` both influence `f`
* Partial derivatives isolate *individual influence*

---

## 2. Geometric intuition (this matters)

Think of `f(x, y)` as a **surface**.

* `∂f/∂x` → slope in the **x direction**
* `∂f/∂y` → slope in the **y direction**

At a point:

* You’re standing on a hill
* Partial derivatives tell you how steep the hill is if you walk **only east or north**

ML optimizers use these slopes to decide how to move.

---

## 3. Why partial derivatives exist at all

Total derivative answers:

> “If everything changes, what happens?”

Partial derivative answers:

> “If **this one thing** changes, what happens?”

ML needs the second question—because models have **millions of parameters**, and we must update them **independently**.

---

## 4. Partial derivatives vs total derivative (important distinction)

Let:

$$
f(x, y) = x^2 + y^2
$$

If `y = y(x)`:

$$
\frac{df}{dx} = 2x + 2y \frac{dy}{dx}
$$

But:

$$
\frac{\partial f}{\partial x} = 2x
$$

ML almost never cares about total derivatives—parameters are **independent knobs**.

---

## 5. Partial derivatives in optimization (core ML usage)

Loss function:
$$
L(w_1, w_2, \dots, w_n)
$$

Each parameter update:
$$
w_i \leftarrow w_i - \eta \frac{\partial L}{\partial w_i}
$$

Translation:

> “How much is *this* weight hurting performance?”

Without partial derivatives:

* No targeted updates
* No scalable learning

---

## 6. Concrete ML example (linear regression)

Model:
$$
\hat{y} = w_1 x_1 + w_2 x_2 + b
$$

Loss:
$$
L = (y - \hat{y})^2
$$

Partial derivatives:
$$
\frac{\partial L}{\partial w_1} = -2x_1(y - \hat{y})
$$
$$
\frac{\partial L}{\partial w_2} = -2x_2(y - \hat{y})
$$
$$
\frac{\partial L}{\partial b} = -2(y - \hat{y})
$$

Each parameter gets **its own blame score**.

---

## 7. Gradient = vector of partial derivatives

$$
\nabla L =
\begin{bmatrix}
\frac{\partial L}{\partial w_1} \
\frac{\partial L}{\partial w_2} \
\vdots
\end{bmatrix}
$$

This vector:

* Points in steepest ascent
* Drives gradient descent
* Exists **only because of partial derivatives**

---

## 8. Partial derivatives in neural networks (real deal)

Single neuron:
$$
z = w_1x_1 + w_2x_2 + b
$$
$$
\hat{y} = \sigma(z)
$$

Loss:
$$
L(\hat{y}, y)
$$

Backprop computes:

$$
\frac{\partial L}{\partial w_1}
=

\frac{\partial L}{\partial \hat{y}}
\cdot
\frac{\partial \hat{y}}{\partial z}
\cdot
\frac{\partial z}{\partial w_1}
$$

This is:

* Partial derivative
* Applied repeatedly
* At massive scale

---

## 9. Chain rule + partial derivatives = backpropagation

Neural nets are:
$$
L(f(g(h(x))))
$$

Partial derivatives allow:

* Isolating each weight’s effect
* Propagating error backward
* Updating millions of parameters independently

Backprop is **nothing more** than structured partial differentiation.

---

## 10. Partial derivatives & feature importance

Large ($\partial L / \partial w_i$) means:

* Model is sensitive to this parameter
* Feature is influential

Small values mean:

* Feature is redundant or ignored

This underpins:

* Sensitivity analysis
* Saliency maps
* Explainability tools

---

## 11. Non-smooth functions (practical ML reality)

ReLU:
$$
f(x) = \max(0, x)
$$

Partial derivative:
$$
\frac{\partial f}{\partial x} =
\begin{cases}
1 & x > 0 \
0 & x < 0
\end{cases}
$$

At `x = 0`: undefined → **subgradient**

ML tolerates this because:

* Happens rarely
* Optimization still works

---

## 12. Higher dimensions (why ML scales)

Modern models:
$$
L(w_1, w_2, \dots, w_{10^9})
$$

Partial derivatives scale because:

* Each is local
* Computable via chain rule
* Parallelizable

This is why deep learning is computationally feasible.

---

## 13. Partial derivatives vs Jacobians (bridge concept)

If output is vector-valued:
$$
\mathbf{y} = f(\mathbf{x})
$$

Then:

* Each entry is a partial derivative
* Stacked together → **Jacobian matrix**

This shows up in:

* Backprop
* Normalizing flows
* Physics-informed ML

---

## 14. Common misconceptions (be honest)

❌ “Partial derivatives mean variables are independent in reality”
✔ No—only treated as independent *for analysis*

❌ “Partial derivatives are approximate”
✔ They are exact (when differentiable)

❌ “ML uses numerical gradients”
✔ It uses automatic differentiation (exact)

---

## TL;DR (no sugar-coating)

* Partial derivatives isolate **responsibility**
* ML training = minimizing loss via partial derivatives
* Backprop = chain rule over partial derivatives
* Without them, deep learning collapses
* If derivatives explain *change*, partial derivatives explain *credit assignment*
