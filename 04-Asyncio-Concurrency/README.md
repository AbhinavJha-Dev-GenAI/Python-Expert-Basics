# Asyncio & Concurrency in Python ⚡

Python provides several ways to handle concurrent execution. Understanding when to use which is critical for building performance-critical applications (like model serving APIs).

---

- [GIL Mechanics](GIL-Mechanics.md): Why Python is (mostly) single-threaded.
- [Asyncio Fundamentals](Asyncio-Fundamentals.md): Event loops and coroutines.
- [Threading vs Processing](Threading-vs-Processing.md): Choosing the right tool for the job.

---

## 🧵 Multithreading vs Multiprocessing

| Feature | Multithreading | Multiprocessing |
|---------|----------------|-----------------|
| **Mechanism** | Shared memory | Separate memory space |
| **GIL Check** | Subject to GIL | Bypasses GIL |
| **Best For** | I/O-bound tasks | CPU-bound tasks |
| **Communication**| Easy (Shared variables)| Complex (IPC, Queues)|

### Example: Multiprocessing (CPU-Bound)
```python
from multiprocessing import Process

def heavy_computation():
    sum(i*i for i in range(10**7))

if __name__ == "__main__":
    p = Process(target=heavy_computation)
    p.start()
    p.join()
```

---

## 🚦 When to use what?
1.  **Web Scraping / API calls**: `asyncio` (High scalability for I/O).
2.  **Database Operations**: `asyncio` (if using an async driver) or `threading`.
3.  **Image Processing / Heavy Math**: `multiprocessing`.
4.  **Simple backgrounds tasks**: `threading`.

---

## 🛠️ Performance Tuning
- **Profiling**: Use `cProfile` to find bottlenecks.
- **Task Groups**: In Python 3.11+, use `asyncio.TaskGroup` for managing multiple coroutines.
