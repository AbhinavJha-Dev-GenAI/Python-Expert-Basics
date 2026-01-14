# 08. Python Expert Interview Preparation 🧠🧱

Technical and design questions for Senior ML Engineer or Backend roles.

## 1. Core Mechanics 📖

*   **Q: What is the GIL (Global Interpreter Lock)?**
    - *A:* A mutex that prevents multiple native threads from executing Python bytecodes at once. This makes Python "slow" for CPU-bound multi-threading. Solution: Use `multiprocessing` or C-extensions like NumPy.
*   **Q: Explain the difference between `@staticmethod` and `@classmethod`.**
    - *A:* `@classmethod` receives the class itself as the first argument (`cls`), useful for factory methods. `@staticmethod` receives no special first argument and acts like a regular function that lives inside the class's namespace.
*   **Q: How do `async` and `await` work under the hood?**
    - *A:* They are built on **Generators**. When you `await`, the function pauses and yields control back to the event loop, which can then run other tasks while the first one waits for I/O.

---

## 2. Advanced Features 🏎️

*   **Q: What are Dunder (Magic) methods?**
    - *A:* Methods like `__init__`, `__str__`, `__call__` that allow custom objects to interact with Python's built-in operators (e.g., `+`, `len()`, `()`).
*   **Q: Mutable vs. Immutable: Why does it matter?**
    - *A:* Lists are mutable; Tuples are immutable. Using mutable objects as default arguments in functions is a common bug: `def add(val, list=[])` will reuse the *same* list object across all calls!
*   **Q: What is Method Resolution Order (MRO)?**
    - *A:* The order in which Python looks for a method in a hierarchy of classes, especially important for **Multiple Inheritance**. You can check it with `Class.mro()`.

---

## 3. Engineering Scenarios 🧪

*   **Scenario: Your Pandas code is too slow and uses 10GB of RAM for a 2GB CSV. How do you optimize?**
    - *A:* 1. Use `chunksize` to read data in pieces. 2. Downcast numeric types (e.g., `float64` to `float32`). 3. Convert string columns with low cardinality to `category` type.
*   **Scenario: You have to process 1 million images. Do you use Threading or Multiprocessing?**
    - *A:* **Multiprocessing**. Image processing is CPU-bound. Threading would be throttled by the GIL.

---

## 🎯 Python Expert Cheat Sheet
1. **Best for I/O**: `asyncio`.
2. **Best for CPU**: `multiprocessing`.
3. **Best for memory**: Generators (`yield`).
4. **Best for API**: FastAPI + Pydantic.
