# Common Design Patterns in Python 🎨

Design patterns are reusable solutions to common problems in software design.

## 1. Creational Patterns

### Singleton (One Instance)
Used for things like Database connection pools or Configuration managers.
```python
class Database:
    _instance = None
    def __new__(cls):
        if not cls._instance:
            cls._instance = super().__new__(cls)
        return cls._instance
```

### Factory (Decouple Creation)
Useful when the exact type of object isn't known until runtime.
```python
class SimpleFactory:
    @staticmethod
    def get_connector(db_type):
        if db_type == "mysql": return MySqlConnector()
        if db_type == "postgres": return PostgresConnector()
```

## 2. Structural Patterns

### Decorator Pattern
Extend object behavior dynamically. Python has native support for this at the method/function level.
```python
@logging_decorator
def save_data(): ...
```

### Adapter Pattern
Convert the interface of a class into another interface clients expect. Use this when integrating legacy code or third-party libraries.

## 3. Behavioral Patterns

### Strategy Pattern
Define a family of algorithms, encapsulate each one, and make them interchangeable.
```python
class PaymentContext:
    def __init__(self, strategy: PaymentStrategy):
        self.strategy = strategy
    
    def pay(self, amount):
        self.strategy.execute(amount)
```

### Observer Pattern
A "one-to-many" dependency between objects. When one object changes state, its dependents are notified (Common in Event-driven systems).

## 💡 When to avoid?
Don't use patterns just for the sake of it. Python's dynamic nature often makes some classic patterns (like the "Visitor" or "Command" patterns) unnecessary or solvable with simple functions/dictionaries.
