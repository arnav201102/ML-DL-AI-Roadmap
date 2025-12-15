# Python Foundations – Complete Markup Notes

These notes consolidate **everything covered so far** in a clean, structured, exam‑ready + industry‑ready format.

Use this as:

* 📘 Study notes
* 🧠 Interview revision
* 🛠️ Reference while coding ML / backend projects

---

## PART 1: OBJECT‑ORIENTED PROGRAMMING (OOP)

---

## 1. OOP – Core Idea

OOP models software using **objects** that combine:

* **Data** (attributes)
* **Behavior** (methods)

### Why OOP?

* Organizes complex systems
* Improves reusability
* Makes large codebases maintainable
* Backbone of ML pipelines & backend services

---

## 2. Class

A **class** is a blueprint for creating objects.

### Syntax

```python
class ClassName:
    def __init__(self, args):
        self.attribute = args

    def method(self):
        pass
```

### Example

```python
class Car:
    def __init__(self, brand, speed):
        self.brand = brand
        self.speed = speed

    def drive(self):
        print(f"{self.brand} driving at {self.speed} km/h")
```

### Key Points

* `__init__` → constructor
* `self` → current object reference
* Attributes live inside objects

---

## 3. Object

An **object** is an instance of a class.

```python
car1 = Car("Tesla", 120)
car2 = Car("BMW", 150)

car1.drive()
car2.drive()
```

Each object:

* Has its own data
* Uses the same class logic

---

## 4. Inheritance

Inheritance allows one class to **reuse and extend** another.

### Parent Class

```python
class Vehicle:
    def start(self):
        print("Vehicle started")
```

### Child Class

```python
class Car(Vehicle):
    def drive(self):
        print("Car driving")
```

```python
c = Car()
c.start()
c.drive()
```

### `super()`

Used to call parent methods.

```python
class Car(Vehicle):
    def __init__(self, brand):
        super().__init__()
        self.brand = brand
```

---

## 5. Method Overriding

Child class modifies parent behavior.

```python
class Bike(Vehicle):
    def start(self):
        print("Bike kick‑started")
```

---

## 6. IS‑A Rule (Critical)

Inheritance should satisfy **is‑a** relationship.

✔ Car **is a** Vehicle
❌ Engine **is a** Car

If not IS‑A → use **composition**, not inheritance.

---

## 7. Encapsulation

Encapsulation = **data protection + controlled access**

### Access Levels (Python Convention)

| Type      | Syntax     | Meaning      |
| --------- | ---------- | ------------ |
| Public    | `self.x`   | Free access  |
| Protected | `self._x`  | Internal use |
| Private   | `self.__x` | Name‑mangled |

---

### Example

```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance

    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount

    def get_balance(self):
        return self.__balance
```

```python
acc = BankAccount(1000)
print(acc.get_balance())
```

---

## 8. Properties (Pythonic Encapsulation)

```python
class Person:
    def __init__(self, age):
        self._age = age

    @property
    def age(self):
        return self._age

    @age.setter
    def age(self, value):
        if value < 0:
            raise ValueError("Invalid age")
        self._age = value
```

Usage:

```python
p = Person(25)
p.age = 30
```

---

## 9. Abstraction

Abstraction = defining **WHAT** a class must do, not **HOW**.

Used when:

* Multiple implementations
* Common interface needed

---

### Abstract Base Class

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass
```

---

### Implementations

```python
class Rectangle(Shape):
    def __init__(self, w, h):
        self.w = w
        self.h = h

    def area(self):
        return self.w * self.h
```

```python
class Circle(Shape):
    def __init__(self, r):
        self.r = r

    def area(self):
        return 3.14 * self.r * self.r
```

---

## 10. Polymorphism

Polymorphism = **same interface, different behavior**.

### Inheritance‑based

```python
class Dog:
    def speak(self):
        return "Bark"

class Cat:
    def speak(self):
        return "Meow"
```

```python
animals = [Dog(), Cat()]
for a in animals:
    print(a.speak())
```

---

### Duck Typing

```python
class FileLogger:
    def log(self, msg):
        print(msg)

class DBLogger:
    def log(self, msg):
        print(msg)
```

```python
def write_log(logger):
    logger.log("Error")
```

---

## 11. OOP in Machine Learning

### Abstract Model

```python
class MLModel(ABC):
    @abstractmethod
    def train(self, X, y): pass

    @abstractmethod
    def predict(self, X): pass
```

### Concrete Models

```python
class LinearRegressionModel(MLModel):
    def train(self, X, y):
        print("Training LR")

    def predict(self, X):
        return "LR Predictions"
```

### Polymorphic Pipeline

```python
def run_pipeline(model: MLModel, X, y):
    model.train(X, y)
    return model.predict(X)
```

---

## PART 2: EXCEPTION HANDLING

---

## 12. What is an Exception?

Runtime error that interrupts normal execution.

```python
10 / 0  # ZeroDivisionError
```

---

## 13. try‑except

```python
try:
    x = int(input())
    print(10 / x)
except ZeroDivisionError:
    print("Cannot divide by zero")
except ValueError:
    print("Invalid input")
```

---

## 14. else & finally

```python
try:
    f = open("data.txt")
except FileNotFoundError:
    print("Missing file")
else:
    print("Read success")
finally:
    f.close()
```

---

## 15. Raising Exceptions

```python
def withdraw(balance, amount):
    if amount > balance:
        raise ValueError("Insufficient funds")
```

---

## 16. Custom Exceptions

```python
class InvalidAgeError(Exception):
    pass
```

```python
if age < 18:
    raise InvalidAgeError("Too young")
```

---

## 17. Best Practices

✔ Catch specific exceptions
✔ Never use bare `except:`
✔ Fail fast on programmer errors
✔ Validate early in ML pipelines

---

## PART 3: VIRTUAL ENVIRONMENTS

---

## 18. What is a Virtual Environment?

An isolated Python setup per project.

Each venv has:

* Own Python
* Own pip
* Own packages

---

## 19. Creating a venv

```bash
python -m venv venv
```

Activate:

Windows:

```bash
venv\Scripts\activate
```

macOS/Linux:

```bash
source venv/bin/activate
```

---

## 20. Installing Packages

```bash
pip install numpy pandas scikit-learn
```

---

## 21. requirements.txt

```bash
pip freeze > requirements.txt
pip install -r requirements.txt
```

---

## 22. venv + VS Code

* Select interpreter: `venv/bin/python`
* VS Code auto‑uses venv

---

## 23. venv + Jupyter

```bash
pip install ipykernel
python -m ipykernel install --user --name venv
```

---

## 24. Common Mistakes

❌ Global installs
❌ Committing venv folder
❌ One venv for all projects

---

## FINAL HOTS (Higher Order Thinking Skills)

### Q1: Why abstraction over inheritance in ML?

→ Swappable models without pipeline change

### Q2: Why encapsulation in ML?

→ Protect trained state & parameters

### Q3: Why venv per project?

→ Reproducibility & dependency safety

---

## FINAL CHECKLIST

✔ Understand OOP pillars
✔ Can design ML pipelines using OOP
✔ Can handle runtime errors properly
✔ Can manage environments professionally

