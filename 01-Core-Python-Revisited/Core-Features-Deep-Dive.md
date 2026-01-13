# Core Features Deep Dive 🔍

This guide covers the power-tools of Python: Generators, Decorators, and Comprehensions.

## 1. Generators & `yield`
Generators are functions that return an iterator that yields one value at a time.
- **Memory Efficiency**: Doesn't load 1 million items in memory; only one.
- **State Preservation**: The function "pauses" and remembers its state.

```python
def count_to_mil():
    for i in range(1000000):
        yield i

for val in count_to_mil():
    if val > 5: break
    print(val)
```

## 2. Decorators
A decorator "wraps" a function to add functionality.
```python
def debug(func):
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__}")
        return func(*args, **kwargs)
    return wrapper

@debug
def say_hello():
    print("Hello!")
```

### The `wraps` utility
Always use `functools.wraps` to preserve metadata like function names and docstrings.

## 3. Context Managers (`with`)
Used for resource management (files, db connections).
- **Class-based**: `__enter__` and `__exit__`.
- **Generator-based**: `@contextlib.contextmanager`.

```python
from contextlib import contextmanager

@contextmanager
def simple_resource():
    print("Setup")
    yield "Resource"
    print("Teardown")

with simple_resource() as r:
    print(f"Using {r}")
```

## 4. Comprehensions
The most concise way to form collections.
- **List**: `[x for x in data]`
- **Set**: `{x for x in data}`
- **Dict**: `{k:v for k,v in data}`
- **Generator Expr**: `(x for x in data)` <- This is lazy evaluation!

```python
# Create a dictionary of even squares
even_squares = {x: x**2 for x in range(10) if x % 2 == 0}
```
