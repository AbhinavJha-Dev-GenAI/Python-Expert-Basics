# Memory Management Deep Dive 🧠

Python automates memory management, but senior engineers must understand how it works to resolve memory leaks and optimize large-scale AI applications.

## 1. Reference Counting
Every Python object has a "reference count".
- When an object is assigned to a variable, the count increases.
- When `del` is called or a variable goes out of scope, the count decreases.
- When count reaches 0, the memory is immediately deallocated.

## 2. Cyclic Garbage Collection (GC)
Reference counting fails for "cycles" (e.g., A references B, and B references A). Python has a `gc` module that runs a cyclic collector to find and clean these up.
- **Generational GC**: Python categorizes objects into three generations (0, 1, 2). New objects are in Gen 0. If they survive a GC cycle, they move to Gen 1, then Gen 2.

## 3. The `__slots__` Optimization
By default, Python objects store their attributes in a dictionary (`__dict__`). This is flexible but memory-heavy.
Using `__slots__` tells Python to use a fixed, efficient array instead.

```python
class Point:
    __slots__ = ('x', 'y') # Saves significant RAM
    def __init__(self, x, y):
        self.x = x
        self.y = y
```

## 4. Interning
Python "interns" (reuses) common objects like small integers (-5 to 256) and short strings to save memory.
```python
a = 256
b = 256
print(a is b) # True (Same object)
```

## 5. Identifying Memory Leaks
- **Tools**: `objgraph`, `memory_profiler`, and the `tracemalloc` standard library.
- **Common Cause**: Global lists or dictionaries that keep growing over time without being cleared.
- **Common Cause**: Circular references involving `__del__` methods (older Python versions).
