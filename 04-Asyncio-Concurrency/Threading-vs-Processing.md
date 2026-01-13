# Threading vs Multiprocessing 🧵 vs ⚙️

Choosing the right concurrency model depends entirely on your task's bottleneck.

## 1. Multithreading (`threading`)
- **Memory**: Shared between threads (fast communication).
- **Execution**: Concurrent but not parallel (due to GIL).
- **Best For**: I/O-bound tasks (API calls, DB queries).

## 2. Multiprocessing (`multiprocessing`)
- **Memory**: Isolated (each process has its own). Communication requires IPC (Queues, Pipes).
- **Execution**: True parallel execution on multiple CPU cores.
- **Best For**: CPU-bound tasks (Image processing, heavy computation).

## 3. Comparison Summary

| Feature | Threading | Multiprocessing | Asyncio |
|---------|-----------|-----------------|---------|
| **Primary Goal**| I/O concurrency| CPU parallelism | I/O scalability |
| **Overhead** | Low | High (Process creation) | Very Low |
| **GIL** | Blocked | Bypassed | N/A (Single-threaded) |
| **Difficulty** | High (Race conditions)| Medium | Low (Syntax based) |

## 4. Practical Example

### CPU-Bound (Calculate large sum)
```python
# USE MULTIPROCESSING
from multiprocessing import Pool
with Pool() as p:
    results = p.map(heavy_func, [1, 2, 3])
```

### I/O-Bound (Download 100 images)
```python
# USE THREADING OR ASYNCIO
import concurrent.futures
with concurrent.futures.ThreadPoolExecutor() as executor:
    executor.map(download_func, urls)
```

## 5. Common Pitfalls
- **Race Conditions**: Two threads modifying the same variable simultaneously. Use `threading.Lock`.
- **Deadlocks**: Two threads waiting for each other to release a lock.
- **Zombies**: Child processes that finished but weren't "joined" by the parent.
