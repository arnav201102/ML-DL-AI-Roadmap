# 🧠 PRACTICE SET: Python Core + Files + CSV + Automation

---

## 1️⃣ FILE HANDLING + DICTS

### ❓ Question 1: Word Frequency Counter

**Task:**
Read a text file and count how many times each word appears.

**Rules:**

* Read file line by line
* Convert words to lowercase
* Use a dictionary

---

### 🧩 Skeleton

```python
counts = {}

with open("sample.txt") as f:
   for line in f:
       # split line into words
       # update counts
       pass

print(counts)
```

---

### ✅ Answer

```python
counts = {}

with open("sample.txt") as f:
   for line in f:
       words = line.lower().split()
       for word in words:
           counts[word] = counts.get(word, 0) + 1

print(counts)
```

---

### 🧠 Why This Works

* `split()` tokenizes
* `get()` avoids key errors
* Dict gives O(1) updates

🔥 **Interview tip:** `dict.get()` shows Python fluency.

---

## 2️⃣ SETS + FILES

### ❓ Question 2: Remove Duplicate Lines

**Task:**
Read a file and write only unique lines to another file.

---

### 🧩 Skeleton

```python
unique = set()

with open("input.txt") as f:
   for line in f:
       pass

with open("output.txt", "w") as f:
   pass
```

---

### ✅ Answer

```python
unique = set()

with open("input.txt") as f:
   for line in f:
       unique.add(line.strip())

with open("output.txt", "w") as f:
   for line in unique:
       f.write(line + "\n")
```

---

### 🧠 Why This Works

* Sets remove duplicates automatically
* `.strip()` avoids newline duplication

🔥 **Tradeoff:** Order is lost — acceptable by design.

---

## 3️⃣ CSV PARSING (REAL-WORLD)

### ❓ Question 3: Count Users per Role

**CSV**

```
id,name,role
1,Alice,admin
2,Bob,user
3,Charlie,admin
```

---

### 🧩 Skeleton

```python
import csv

role_count = {}

with open("users.csv", newline="") as f:
   reader = csv.DictReader(f)
   for row in reader:
       pass

print(role_count)
```

---

### ✅ Answer

```python
import csv

role_count = {}

with open("users.csv", newline="") as f:
   reader = csv.DictReader(f)
   for row in reader:
       role = row["role"]
       role_count[role] = role_count.get(role, 0) + 1

print(role_count)
```

---

### 🧠 Why This Works

* `DictReader` gives readable column access
* Dict aggregation is scalable

🔥 **Never** parse CSV manually unless forced.

---

## 4️⃣ GENERATORS (STREAMING)

### ❓ Question 4: Filter Admins Using Generator

**Task:**
Yield only admin users from a CSV file.

---

### 🧩 Skeleton

```python
import csv

def admins_only(path):
   pass

for admin in admins_only("users.csv"):
   print(admin)
```

---

### ✅ Answer

```python
import csv

def admins_only(path):
   with open(path, newline="") as f:
       reader = csv.DictReader(f)
       for row in reader:
           if row["role"] == "admin":
               yield row

for admin in admins_only("users.csv"):
   print(admin)
```

---

### 🧠 Why This Works

* Generator avoids loading full CSV
* Yields one row at a time

🔥 This pattern scales to millions of rows.

---

## 5️⃣ FILE AUTOMATION

### ❓ Question 5: Extract ERROR Logs

**Input (`app.log`)**

```
INFO started
ERROR failed
INFO retry
ERROR timeout
```

---

### 🧩 Skeleton

```python
with open("app.log") as src, open("errors.log", "w") as dest:
   for line in src:
       pass
```

---

### ✅ Answer

```python
with open("app.log") as src, open("errors.log", "w") as dest:
   for line in src:
       if line.startswith("ERROR"):
           dest.write(line)
```

---

### 🧠 Why This Works

* Line-by-line streaming
* No memory overhead

🔥 This is exactly how log processors work.

---

## 6️⃣ OS AUTOMATION

### ❓ Question 6: List `.txt` Files with Size

---

### 🧩 Skeleton

```python
import os

for file in os.listdir("."):
   pass
```

---

### ✅ Answer

```python
import os

for file in os.listdir("."):
   if file.endswith(".txt"):
       size = os.path.getsize(file)
       print(f"{file}: {size} bytes")
```

---

### 🧠 Why This Works

* `os.listdir()` gives filenames
* `getsize()` reads metadata only

🔥 Never open files just to check size.

---

## 7️⃣ GENERATOR PIPELINE (IMPORTANT)

### ❓ Question 7: Clean Text Pipeline

**Steps:**

1. Read file
2. Strip whitespace
3. Remove empty lines
4. Uppercase

---

### 🧩 Skeleton

```python
def read_lines(path):
   pass

def clean(lines):
   pass

def upper(lines):
   pass

for line in upper(clean(read_lines("data.txt"))):
   print(line)
```

---

### ✅ Answer

```python
def read_lines(path):
   with open(path) as f:
       for line in f:
           yield line

def clean(lines):
   for line in lines:
       line = line.strip()
       if line:
           yield line

def upper(lines):
   for line in lines:
       yield line.upper()

for line in upper(clean(read_lines("data.txt"))):
   print(line)
```

---

### 🧠 Why This Works

* Each function does one thing
* Fully streaming
* Extremely testable

🔥 This is senior-level Python.

---

## 🧪 FINAL MINI-CHALLENGE

### ❓ Question: CSV Aggregation

**Input**

```
product,amount
A,100
B,200
A,150
```

---

### 🧩 Skeleton

```python
import csv

totals = {}

with open("sales.csv", newline="") as f:
   reader = csv.DictReader(f)
   for row in reader:
       pass

print(totals)
```

---

### ✅ Answer

```python
import csv

totals = {}

with open("sales.csv", newline="") as f:
   reader = csv.DictReader(f)
   for row in reader:
       product = row["product"]
       amount = int(row["amount"])
       totals[product] = totals.get(product, 0) + amount

print(totals)
```

---

## 🔥 HOW TO USE THIS PROPERLY

1. Hide the answers
2. Write code from skeleton
3. Run it
4. Compare
5. Refactor once
