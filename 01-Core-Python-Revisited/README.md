# 01. Core Python Revisited 🐍💎

Mastering the advanced features of Python that separate a "script writer" from a "software engineer."

## 1. Decorators: Function Meta-Programming 🎭

Decorators allow you to "wrap" another function to extend its behavior without permanently modifying it.
- **Use Case**: Logging, Timing execution, Access control, Caching results.

```python
import functools
import time

def timer_decorator(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        start_time = time.perf_counter()
        result = func(*args, **kwargs)
        end_time = time.perf_counter()
        print(f"Finished {func.__name__} in {end_time - start_time:.4f}s")
        return result
    return wrapper
```

---

## 2. Generators & Iterators 🔄📦

Generators use the `yield` keyword to produce a sequence of values lazily. They are **memory-efficient** because they don't store the entire list in RAM.
- **Use Case**: Processing massive datasets (e.g., streaming 100GB of logs).

```python
def log_reader(file_path):
    with open(file_path) as f:
        for line in f:
            if "ERROR" in line:
                yield line
```

---

## 3. Context Managers (The `with` Statement) 🛡️

Ensures resources (files, DB connections) are properly cleaned up, even if an error occurs.
- **The Protocol**: Implementing `__enter__` and `__exit__` in a class, or using `@contextmanager`.

---

## 4. `*args` and `**kwargs`: Flexibility 🏗️

- `*args`: Passes a variable number of non-keyword arguments (as a tuple).
- `**kwargs`: Passes a variable number of keyword arguments (as a dictionary).
- **In ML**: Crucial for wrapping libraries where you want to pass parameters down to an underlying model (e.g., `model.train(**config)`).

---

## 🛠️ Essential Snippet (Advanced List Comprehensions)

```python
# Filtering and Mapping in one line
squared_evens = [x**2 for x in range(10) if x % 2 == 0]

# Dict Comprehensions for mapping IDs
user_map = {u.id: u.name for u in users if u.is_active}
```

---

## 📊 Summary
Core Python mastery is about **Efficiency and Readability**. Tools like decorators and generators reduce boilerplate and prevent your ML pipelines from crashing due to memory issues.
