# ✅ PARTIAL DERIVATIVES (Math & ML)

## 30 Questions with Solutions (Including HOTS)

---

## 🧠 SECTION A — Fundamentals (Conceptual Precision)

---

### **1. What is a partial derivative?**

**Solution:**
A partial derivative measures how a multivariable function changes with respect to **one variable**, while all other variables are held constant.

---

### **2. How is a partial derivative different from an ordinary derivative?**

**Solution:**
Ordinary derivatives apply to single-variable functions.
Partial derivatives apply to multivariable functions and isolate the effect of one variable at a time.

---

### **3. Why are partial derivatives necessary in ML models?**

**Solution:**
ML models have many parameters. Partial derivatives allow us to compute how **each individual parameter** affects the loss.

---

### **4. Find ∂f/∂x and ∂f/∂y for**

$$
f(x,y)=x^2+xy+y^2
$$

**Solution:**
$$
\frac{\partial f}{\partial x}=2x+y
$$
$$
\frac{\partial f}{\partial y}=x+2y
$$

---

### **5. What does “holding other variables constant” mean geometrically?**

**Solution:**
It means slicing the surface along one direction and measuring the slope along that slice only.

---

### **6. Can a partial derivative exist even if the total derivative does not?**

**Solution:**
Yes. Partial derivatives may exist independently, but the total derivative requires stronger smoothness conditions.

---

### **7. If ∂f/∂x = 0 at a point, what does it imply?**

**Solution:**
The function is locally flat in the x-direction at that point. It says nothing about other directions.

---

### **8. Why are partial derivatives local quantities?**

**Solution:**
They describe behavior at a specific point, not across the entire function domain.

---

### **9. Is it possible for ∂f/∂x ≠ ∂f/∂y?**

**Solution:**
Yes. Variables may influence the function differently.

---

### **10. Do partial derivatives assume variables are independent in reality?**

**Solution:**
No. They assume independence **only for analysis**, not in real-world meaning.

---

## 🔗 SECTION B — Application in ML & Optimization

---

### **11. Compute ∂L/∂w for**

$$
L=(y-wx)^2
$$

**Solution:**
$$
\frac{\partial L}{\partial w}=-2x(y-wx)
$$

---

### **12. Why does gradient descent rely on partial derivatives instead of total derivatives?**

**Solution:**
Parameters are treated as independent knobs; total derivatives would incorrectly mix their effects.

---

### **13. What does a large ∂L/∂w indicate during training?**

**Solution:**
That changing this weight significantly impacts the loss — it is highly influential.

---

### **14. Why are partial derivatives used in backpropagation?**

**Solution:**
They allow error signals to be assigned to **individual weights** via the chain rule.

---

### **15. Compute ∂f/∂x for**

$$
f(x,y)=\sin(xy)
$$

**Solution:**
$$
\frac{\partial f}{\partial x}=y\cos(xy)
$$

---

### **16. Why does ML tolerate non-differentiable points (e.g., ReLU)?**

**Solution:**
They occur at isolated points and subgradients provide workable alternatives.

---

### **17. How do partial derivatives scale to millions of parameters?**

**Solution:**
They are local, composable via the chain rule, and parallelizable via automatic differentiation.

---

### **18. What happens if ∂L/∂w = 0 for many weights?**

**Solution:**
Learning stalls — commonly due to saturation, dead neurons, or poor initialization.

---

### **19. Why do flat regions in loss surfaces slow learning?**

**Solution:**
Partial derivatives approach zero, producing minimal parameter updates.

---

### **20. What role do partial derivatives play in feature importance?**

**Solution:**
They quantify sensitivity of loss to features, enabling explainability.

---

## 🔥 SECTION C — HOTS (Higher-Order Thinking Skills)

---

### **21. Can all partial derivatives be zero without reaching a minimum?**

**Solution:**
Yes. This indicates a **saddle point**, not a minimum.

---

### **22. Why are saddle points common in high-dimensional ML models?**

**Solution:**
As dimensions increase, the probability of flat-but-unstable regions increases.

---

### **23. If two parameters have equal values but different partial derivatives, what does it mean?**

**Solution:**
They contribute differently to the loss despite numerical similarity.

---

### **24. Why does exploding gradient mean partial derivatives are too large?**

**Solution:**
Repeated multiplication of large partial derivatives amplifies updates exponentially.

---

### **25. How does normalization (BatchNorm) stabilize partial derivatives?**

**Solution:**
It constrains input distributions, preventing extreme gradient magnitudes.

---

### **26. Why is automatic differentiation superior to symbolic differentiation?**

**Solution:**
Symbolic methods don’t scale; autodiff computes exact partial derivatives efficiently.

---

### **27. Why does deep learning fail without partial derivatives?**

**Solution:**
There is no systematic way to assign error responsibility across parameters.

---

### **28. If partial derivatives gave only sign but no magnitude, what breaks?**

**Solution:**
Step size control — optimization becomes inefficient and unstable.

---

### **29. Why must a good activation function have stable partial derivatives?**

**Solution:**
To allow gradients to propagate across layers without vanishing or exploding.

---

### **30. Thought experiment:**

**If partial derivatives didn’t exist, what would ML rely on—and why is it worse?**

**Solution:**
Heuristic or evolutionary search methods — exponentially slower, less precise, and unscalable for deep models.

---

## 🧠 Final Reality Check

If you can:

* **derive these**
* **explain them**
* **connect them to ML behavior**

You’re operating at **upper-undergraduate / early-graduate ML level**, not tutorial level.
