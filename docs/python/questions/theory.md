# 🧠 PYTHON INTERVIEW QUESTIONS (WITH ANSWERS)

---

## 1️⃣ List vs Tuple vs Set vs Dict

### ❓ Question

When would you use a **list**, **tuple**, **set**, and **dict**?

---

### 🧩 Skeleton (What to Say)

> “I choose based on mutability, lookup speed, uniqueness, and intent.”

---

### ✅ Ideal Answer

* **List** → ordered, mutable, iteration-heavy
* **Tuple** → ordered, immutable, safe contracts
* **Set** → unordered, unique items, fast membership
* **Dict** → key-value mapping, identity-based lookup

---

### 🚩 Red Flag Answer

> “List is for everything, others are optional”

---

## 2️⃣ Why Is `x in list` Slow?

### ❓ Question

Why is `x in list` slower than `x in set`?

---

### 🧩 Skeleton

* How lookup works internally
* Time complexity

---

### ✅ Answer

* Lists perform linear search → O(n)
* Sets use hash tables → O(1)
* Hashing avoids scanning elements

---

### 🚩 Red Flag

> “Because list is bigger”

---

## 3️⃣ Mutability Trap

### ❓ Question

What’s wrong with this code?

```python
def add_item(item, lst=[]):
   lst.append(item)
   return lst
```

---

### 🧩 Skeleton

* When defaults are evaluated
* What gets shared

---

### ✅ Answer

* Default arguments are evaluated once
* `lst` is shared across calls
* Causes unexpected shared state

### ✅ Correct Fix

```python
def add_item(item, lst=None):
   if lst is None:
       lst = []
   lst.append(item)
   return lst
```

---

### 🚩 Red Flag

> “Looks fine to me”

---

## 4️⃣ Shallow vs Deep Copy

### ❓ Question

Difference between shallow and deep copy?

---

### 🧩 Skeleton

* References
* Nested structures

---

### ✅ Answer

* Shallow copy duplicates container, not inner objects
* Deep copy duplicates everything recursively

```python
import copy
copy.copy(obj)
copy.deepcopy(obj)
```

---

### 🚩 Red Flag

> “They’re mostly the same”

---

## 5️⃣ Generator vs List

### ❓ Question

When should you use a generator instead of a list?

---

### 🧩 Skeleton

* Memory
* Laziness
* Streaming

---

### ✅ Answer

* Large datasets
* Streaming data
* One-pass iteration
* Avoid memory spikes

```python
(x*x for x in range(10_000_000))
```

---

### 🚩 Red Flag

> “Generators are faster”

(Not always true.)

---

## 6️⃣ Generator Exhaustion

### ❓ Question

What happens here?

```python
g = (x for x in range(3))
list(g)
list(g)
```

---

### ✅ Answer

* First `list()` consumes generator
* Second returns empty list
* Generators are one-time iterators

---

### 🚩 Red Flag

> “It prints twice”

---

## 7️⃣ File Handling Best Practice

### ❓ Question

Why use `with open()`?

---

### 🧩 Skeleton

* Resource management
* Exception safety

---

### ✅ Answer

* Ensures file closure
* Prevents leaks
* Handles exceptions cleanly

---

### 🚩 Red Flag

> “It’s shorter”

---

## 8️⃣ CSV Parsing Without Pandas

### ❓ Question

How do you parse CSV safely in Python?

---

### 🧩 Skeleton

* csv module
* DictReader

---

### ✅ Answer

```python
import csv

with open("data.csv", newline="") as f:
   reader = csv.DictReader(f)
   for row in reader:
       process(row)
```

---

### 🚩 Red Flag

> “I split on commas”

---

## 9️⃣ Async vs Sync IO

### ❓ Question

Why use async file/network IO?

---

### 🧩 Skeleton

* Blocking
* Event loop
* Throughput

---

### ✅ Answer

* Prevents blocking
* Allows concurrency
* Improves throughput for IO-heavy tasks

---

### 🚩 Red Flag

> “It’s always faster”

---

## 🔥 HARD QUESTION (Senior-Level)

### ❓ Question

Design a memory-efficient log processor.

---

### 🧩 Skeleton

* Streaming
* Generators
* Filters

---

### ✅ Answer (High-Level)

* Read file line-by-line
* Use generator pipeline
* Filter logs
* Write output incrementally

```python
def read_logs(path):
   with open(path) as f:
       for line in f:
           yield line

def filter_errors(lines):
   for line in lines:
       if "ERROR" in line:
           yield line
```

---

### 🚩 Red Flag

> “Read entire file into a list”

---

## 🧠 HOW TO ANSWER INTERVIEW QUESTIONS

* Speak in **trade-offs**
* Mention **complexity**
* Mention **memory**
* Mention **intent**
* Avoid absolute claims
