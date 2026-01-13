# Common Interview Q&A 🎯

Consolidated list of high-level Python questions frequently asked in senior engineering interviews.

## 1. The Language Internals
**Q: How does the GIL affect Multithreading?**
A: It ensures only one thread executes Python bytecode at a time. I/O-bound threads release the GIL, while CPU-bound threads fight for it, making threading inefficient for heavy computation.

**Q: Explain the Method Resolution Order (MRO).**
A: Python uses the C3 Linearization algorithm. It searches the class itself, then its parents from left to right, then grandparents, ensuring no parent is searched before its children.

## 2. Advanced Features
**Q: Decorators vs Monkey Patching?**
A: Decorators are a structured way to extend behavior at definition time using `@`. Monkey patching is the dynamic replacement of attributes/methods at runtime.

**Q: When to use a Generator?**
A: When dealing with large datasets that don't fit in memory. It uses "lazy evaluation" to yield items one at a time.

## 3. Architecture & Data
**Q: Explain the difference between `@staticmethod` and `@classmethod`.**
A: `@staticmethod` is essentially a regular function that lives in a class for organization. `@classmethod` receives the class itself (`cls`) as an argument, allowing it to act as a factory or modify class state.

**Q: Shallow Copy vs Deep Copy?**
A: Shallow copies the top-level container; internal objects are still shared references. Deep copy recursively creates new copies of everything.

## 4. Web & Async
**Q: How does `asyncio` handle context switching?**
A: It uses cooperative multitasking. Context switching only happens at `await` points, where a task voluntarily yields control.

**Q: FastAPI vs Flask?**
A: FastAPI is async native, uses Pydantic for validation, and automatically generates Swagger docs. Flask is synchronous (traditionally) and more minimalist/extensible but requires more manual boilerplate.
