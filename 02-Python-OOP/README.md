# Python Object-Oriented Programming (OOP) 🏗️

Python’s OOP implementation is flexible and powerful. This section covers advanced concepts specific to Python, design patterns, and SOLID principles.

---

## 🧬 Specifics of Python OOP

- [MRO and Inheritance](MRO-and-Inheritance.md): How Python resolves methods in complex trees.
- [Abstract Classes and Interfaces](Abstract-Classes-and-Interfaces.md): Enforcing contracts.
- [SOLID Principles in Python](SOLID-Principles-In-Python.md): Architectural best practices.
- [Common Design Patterns](Common-Design-Patterns.md): Singleton, Factory, Strategy, etc.

---

## 💎 SOLID Principles with Pythonic Examples

1.  **S - Single Responsibility**: A class should have one reason to change.
2.  **O - Open/Closed**: Open for extension, closed for modification (use Inheritance/ABCs).
3.  **L - Liskov Substitution**: Subtypes must be substitutable for their base types.
4.  **I - Interface Segregation**: Clients shouldn't depend on methods they don't use (don't create "fat" interfaces).
5.  **D - Dependency Inversion**: Depend on abstractions, not concretions.

```python
# Dependency Inversion Example
class Logger(ABC):
    @abstractmethod
    def log(self, message): pass

class ConsoleLogger(Logger):
    def log(self, message): print(f"Logging: {message}")

class App:
    def __init__(self, logger: Logger): # Depends on abstraction
        self.logger = logger
```

---

## 🎨 Frequently Used Design Patterns

### 1. Singleton (Ensure only one instance)
```python
class Singleton:
    _instance = None
    def __new__(cls):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
        return cls._instance
```

### 2. Factory Pattern (Decouple creation logic)
```python
class Dog:
    def speak(self): return "Woof!"
class Cat:
    def speak(self): return "Meow!"

def get_pet(pet="dog"):
    pets = dict(dog=Dog(), cat=Cat())
    return pets[pet]
```

### 3. Decorator Pattern
Using `@property`, `@classmethod`, and custom decorators to extend behavior.

---

## 🛠️ Practice
- Implement a `PaymentGateWay` ABC and create `Paypal` and `Stripe` implementations.
- Verify MRO in a diamond inheritance scenario.
