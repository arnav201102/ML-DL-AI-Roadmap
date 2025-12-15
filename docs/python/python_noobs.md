# 📘 Python Core Data Handling, Performance, Generators & File Processing

### *Beginner → Production → Advanced*

---

# 0. How to Study This Document

* **First pass** → read everything
* **Second pass** → focus on examples
* **Before interviews** → read HOT 🔥 boxes
* **Before writing real code** → revisit patterns

---

# 1. Python Data Structures (Deep Dive)

---

## 1.1 Lists — Ordered & Mutable

### Concept (What & Why)

A list is a **resizable array of references**.

Python lists:

* Do not store values directly
* Store **references to objects**
* Grow dynamically (amortized resizing)

---

### Syntax & Examples

```python
numbers = [10, 20, 30]

numbers.append(40)      # add
numbers.insert(1, 15)   # insert at index
numbers.pop()           # remove last
numbers.remove(20)      # remove by value
```

Iteration:

```python
for n in numbers:
   print(n)
```

---

### Performance Reality

```python
x in numbers   # O(n)
numbers[i]     # O(1)
```

---

### Real Example (Bad → Good)

❌ Bad (linear search repeatedly)

```python
def is_admin(user_id, admins):
   return user_id in admins  # admins is a list
```

✅ Good

```python
admins = set(admins)

def is_admin(user_id):
   return user_id in admins
```

---

### HOT 🔥

Lists are for **order and iteration**, not rules or identity.

---

## 1.2 Tuples — Fixed & Safe

### Concept

A tuple is an **immutable sequence**.

Why this matters:

* Hashable
* Safer
* Intentional

---

### Examples

```python
point = (5, 10)
x, y = point
```

Tuple as return value:

```python
def bounds(nums):
   return min(nums), max(nums)
```

---

### Tuple as dict key

```python
cache = {}
cache[(10, 20)] = "visited"
```

---

### HOT 🔥

If mutation would be a bug → use tuple.

---

## 1.3 Dictionaries — Identity & Meaning

### Concept

A dict is a **hash table**.

* Keys → hashed
* Values → stored
* Lookup → constant time

---

### Examples

```python
user = {
   "id": 1,
   "name": "Arnav",
   "roles": ["admin"]
}
```

Safe access:

```python
user.get("email")  # None
```

---

### Normalization Pattern (Critical)

❌ Bad

```python
users = [
   {"id": 1, "name": "A"},
   {"id": 2, "name": "B"}
]
```

✅ Good

```python
users_by_id = {
   1: {"name": "A"},
   2: {"name": "B"}
}
```

---

### HOT 🔥

Dicts eliminate loops.

---

## 1.4 Sets — Logic & Rules

### Concept

A set is a **hash table with only keys**.

---

### Examples

```python
roles = {"read", "write"}
roles.add("delete")
```

Membership:

```python
"read" in roles  # O(1)
```

---

### Set Operations

```python
a = {1, 2, 3}
b = {3, 4}

a | b   # union
a & b   # intersection
a - b   # difference
```

---

### HOT 🔥

Use sets for permissions, flags, filters.

---

# 2. Python Memory Model (Expanded)

---

## 2.1 References Explained

```python
a = [1, 2]
b = a
```

Both names point to the **same object**.

```python
id(a) == id(b)  # True
```

---

## 2.2 Shallow Copy (Danger)

```python
import copy

data = {"items": [1, 2]}
shallow = copy.copy(data)

shallow["items"].append(3)
```

`data` is now corrupted.

---

## 2.3 Deep Copy (Safety)

```python
deep = copy.deepcopy(data)
deep["items"].append(4)
```

Original untouched.

---

### HOT 🔥

Mutation + shared reference = future bug.

---

# 3. Performance & Big-O (With Context)

---

### Lookup Cost

```python
x in list_data   # O(n)
x in set_data    # O(1)
x in dict_data   # O(1)
```

---

### Sorting Cost

```python
items.sort()  # O(n log n)
```

Never sort inside loops.

---

### HOT 🔥

Performance problems are usually **data structure problems**, not algorithm problems.

---

# 4. Comprehensions (Expanded)

---

## 4.1 List Comprehensions

```python
squares = [x * x for x in range(10)]
```

With filter:

```python
evens = [x for x in range(10) if x % 2 == 0]
```

Conditional expression:

```python
labels = ["even" if x % 2 == 0 else "odd" for x in range(5)]
```

---

## 4.2 Set Comprehensions

```python
emails = {u.email.lower() for u in users if u.active}
```

---

## 4.3 Dict Comprehensions

```python
users_by_email = {u.email: u for u in users}
```

---

## 4.4 Generator Expressions

```python
(x * x for x in range(1_000_000))
```

Lazy. No memory spike.

---

### HOT 🔥

Comprehensions build data.
Generators stream data.

---

# 5. Generators (Advanced Explanation)

---

## 5.1 Generator Lifecycle

```python
def gen():
   yield 1
   yield 2
```

States:

1. Created
2. Running
3. Paused
4. Exhausted

---

## 5.2 Generator Exhaustion

```python
g = gen()
list(g)
list(g)  # empty
```

Generators are **one-shot**.

---

## 5.3 Generator Pipelines

```python
def read(path):
   with open(path) as f:
       for line in f:
           yield line.strip()

def only_errors(lines):
   for line in lines:
       if "ERROR" in line:
           yield line
```

Usage:

```python
for err in only_errors(read("app.log")):
   handle(err)
```

---

## 5.4 `yield from`

```python
def flatten(data):
   for row in data:
       yield from row
```

Cleaner delegation.

---

### HOT 🔥

Generators separate **what** from **when**.

---

# 6. File Handling (Expanded)

---

## 6.1 Correct File Pattern

```python
with open("data.txt", encoding="utf-8") as f:
   for line in f:
       process(line)
```

---

## 6.2 Writing Files Safely

```python
with open("out.txt", "w") as f:
   f.write("Hello\n")
```

Appending:

```python
with open("out.txt", "a") as f:
   f.write("Next\n")
```

---

## 6.3 Binary Files

```python
with open("image.png", "rb") as f:
   data = f.read()

with open("copy.png", "wb") as f:
   f.write(data)
```

---

### HOT 🔥

Text ≠ Binary. Never mix them.

---

# 7. Advanced: Async + File + Generator Patterns

This is **production-level Python**.

---

## 7.1 Async Generators (`async def` + `yield`)

```python
async def fetch_pages(session, urls):
   for url in urls:
       async with session.get(url) as resp:
           yield await resp.text()
```

Usage:

```python
async for page in fetch_pages(session, urls):
   process(page)
```

---

## 7.2 Async File Streaming (Large Files)

```python
import aiofiles

async def read_large_file(path):
   async with aiofiles.open(path) as f:
       async for line in f:
           yield line
```

This:

* Doesn’t block the event loop
* Scales under load

---

## 7.3 Async Pipeline Pattern

```python
async def parse(lines):
   async for line in lines:
       if "ERROR" in line:
           yield line.split("|")
```

Pipeline:

```python
async for record in parse(read_large_file("app.log")):
   save(record)
```

---

## 7.4 Backpressure-Friendly Streaming

```python
async def stream_data(source):
   async for item in source:
       yield item
       await asyncio.sleep(0)  # allow loop to breathe
```

Used in:

* WebSockets
* Event systems
* Streaming APIs

---

## 7.5 Generator-Based State Machine

```python
def state_machine():
   state = "START"
   while True:
       event = yield state
       if state == "START" and event == "go":
           state = "RUN"
       elif state == "RUN" and event == "stop":
           state = "END"
```

Advanced but powerful.

---

### HOT 🔥

Async generators let you:

* Stream data
* Avoid memory spikes
* Scale IO-heavy systems

---

# 8. Final Mental Model (Expanded)

* Lists → iteration & UI
* Tuples → contracts & safety
* Dicts → identity & lookup
* Sets → logic & rules
* Generators → scale & streams
* Files → always streamed
* Async → never block

---

# 9. Final HOT Sheet 🔥

🔥 Correct structure beats clever code
🔥 Immutability prevents bugs
🔥 Lazy evaluation scales systems
🔥 Files are streams, not blobs
🔥 Generators turn big problems small