# Python Interview Preparation 💼

This section focuses on the "Deep Python" concepts that separate junior developers from senior ML engineers. These topics frequently appear in technical interviews for AI/ML roles.

---

- [Memory Management Deep Dive](Memory-Management-Deep-Dive.md): Reference counting and GC.
- [Common Interview Q&A](Common-Interview-QnA.md): Theoretical bank.
- [Coding Challenges & Solutions](Coding-Challenges-Solutions.md): Hands-on implementation.

### 2. The GIL (Global Interpreter Lock) revisited
*   **Question**: Why doesn't Python have true multithreading?
*   **Answer**: The GIL protects access to Python objects, preventing multiple threads from executing Python bytecodes at once. This simplifies memory management but limits CPU-bound parallelism.

### 3. Iterators vs Generators
*   **Iterator**: An object that implements `__next__` and `__iter__`.
*   **Generator**: A function that uses `yield` to return values on demand. It is more memory-efficient as it doesn't store the entire list in memory.

### 4. Closures & Decorators
*   **Closure**: A function that remembers the scope in which it was created even after that scope has finished executing.
*   **Decorator**: A higher-order function that takes another function and extends its behavior without explicitly modifying it.

---

## 🎯 Top Interview Questions

| Topic | Question | Key Concept |
|-------|----------|-------------|
| **Core** | What is the MRO (Method Resolution Order)? | C3 Linearization |
| **Data Types** | Difference between `copy()` and `deepcopy()`? | Shallow vs. Recursive copy |
| **Methods** | `@staticmethod` vs `@classmethod`? | Instance-independent vs Class-aware |
| **Async** | How does the event loop work? | Task scheduling & cooperative multitasking |
| **Meta** | What are Metaclasses? | "Classes of classes" (e.g., `type`) |

---

## 📝 Coding Challenges (Common AI/ML Variations)
1. **LRU Cache Implementation**: Use `collections.OrderedDict` to build an efficient cache.
2. **Flatten a Nested List**: Use recursion or a generator.
3. **Custom Iterator**: Build a class that iterates over a custom data structure (e.g., a tree).

---

## 📖 Essential Resources
- [Python Inner Workings (Official Docs)](https://docs.python.org/3/c-api/intro.html)
- [Real Python: Python Interview Questions](https://realpython.com/python-interview-questions/)
