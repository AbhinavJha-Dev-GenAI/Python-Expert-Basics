# Abstract Classes and Interfaces 🏗️

Python achieves strict class structures using the `abc` module and flexible interfaces via Duck Typing.

## 1. Abstract Base Classes (ABCs)
An ABC cannot be instantiated. It defines a template that subclasses *must* follow.
```python
from abc import ABC, abstractmethod

class Database(ABC):
    @abstractmethod
    def connect(self):
        """Must be implemented by child"""
        pass

class MySQL(Database):
    def connect(self):
        print("Connected to MySQL")
```

## 2. Interfaces vs ABCs
- **Java/C# Style Interfaces**: Python doesn't have a specific `interface` keyword. We use ABCs with only abstract methods to act as interfaces.
- **Protocol (Structural Subtyping)**: Introduced in Python 3.8, `typing.Protocol` allows you to define interfaces that don't require explicit inheritance (Duck Typing at static check time).

```python
from typing import Protocol

class Drawable(Protocol):
    def draw(self) -> None: ...

def render_item(item: Drawable):
    item.draw()
```

## 3. Duck Typing 🦆
"If it walks like a duck and quacks like a duck, it's a duck."
Python focuses on **behavior** rather than **type**. If an object has the required methods, it can be used, regardless of its inheritance tree.

## 4. Properties in Abstract Classes
You can also define required properties.
```python
class Base(ABC):
    @property
    @abstractmethod
    def name(self): pass
```

## 5. Why use them?
- **Enforcement**: Ensure plugin developers implement required methods.
- **Documentation**: Act as a contract for what a class should do.
- **Type Checking**: Help tools like `mypy` identify bugs early.
