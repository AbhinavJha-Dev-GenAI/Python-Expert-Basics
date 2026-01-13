# SOLID Principles in Python 💎

Applying SOLID principles makes your Python code maintainable, scalable, and testable.

## 1. Single Responsibility Principle (SRP)
**Goal**: A class should have one, and only one, reason to change.
- *Bad*: a `User` class that handles both data storage and sending emails.
- *Good*: Split into `User` (data) and `EmailService` (logic).

## 2. Open/Closed Principle (OCP)
**Goal**: Software entities should be open for extension but closed for modification.
- Use **Inheritance** or **Composition** to add behavior without changing existing code.

## 3. Liskov Substitution Principle (LSP)
**Goal**: Subtypes must be substitutable for their base types.
- If a function takes a `Bird` class, it should work with a `Penguin` subclass even if penguins can't fly (don't break the base class contract).

## 4. Interface Segregation Principle (ISP)
**Goal**: Clients should not be forced to depend on methods they do not use.
- Pythonic approach: Use many small **Mixins** or **Protocols** instead of one giant Base class.

## 5. Dependency Inversion Principle (DIP)
**Goal**: Depend on abstractions, not concretions.
- Use **Dependency Injection**.

```python
# DIP in Python
class DataSource(ABC):
    @abstractmethod
    def get_data(self): pass

class ApiSource(DataSource):
    def get_data(self): return {"source": "API"}

class DataProcessor:
    def __init__(self, source: DataSource): # Inject abstraction
        self.source = source
```

## 💡 Summary Table

| Principle | Meaning | Python Implementation |
|-----------|---------|-----------------------|
| **SRP** | One Job | Decoupled Classes |
| **OCP** | Extend, don't break | Inheritance/Decorators |
| **LSP** | Behavior match | ABCs / Protocols |
| **ISP** | Small Interfaces | Mixins |
| **DIP** | Abstract Deps | Dependency Injection |
