# 04. Asyncio & Concurrency⏳🚦

Python's **GIL (Global Interpreter Lock)** prevents multiple threads from running Python code at the same time. Understanding how to bypass this is crucial for performance.

## 1. Multithreading vs. Multiprocessing ⚖️

*   **Multithreading**: Good for **I/O-Bound** tasks (e.g., waiting for an API response, reading a file). It shares memory between threads.
*   **Multiprocessing**: Good for **CPU-Bound** tasks (e.g., heavy math, image processing). It bypasses the GIL by starting a new Python process for each task.

---

## 2. Asyncio: Concurrent I/O 🚀

Asyncio uses a single thread but "jumps" between tasks while they are waiting for I/O.
- **`async`**: Marks a function as a "Coroutine."
- **`await`**: Tells Python to pause here and do something else while waiting for this result.

```python
import asyncio

async def fetch_data():
    print("Start fetching...")
    await asyncio.sleep(2) # Non-blocking sleep
    print("Done!")

asyncio.run(fetch_data())
```

---

## 3. The GIL Explained 🔒

The GIL is a mutex that protects access to Python objects, preventing multiple threads from executing Python bytecodes at once.
- **Consequence**: Even on a 64-core CPU, a standard Python script with `threading` only uses **one core** for CPU-bound math.
- **Solution**: Use NumPy (which runs in C outside the GIL) or the `multiprocessing` module.

---

## 🛠️ Essential Snippet (Concurrent API Calls)

```python
import asyncio
import aiohttp

async def call_api(url):
    async with aiohttp.ClientSession() as session:
        async with session.get(url) as response:
            return await response.json()

async def main():
    urls = ["https://api1.com", "https://api2.com"]
    # Run both simultaneously!
    results = await asyncio.gather(*(call_api(u) for u in urls))
    print(results)

asyncio.run(main())
```

---

## 📊 Summary
Concurrency is about **Throughput**. Use `asyncio` for web/API integration and `multiprocessing` for data preprocessing pipelines to fully utilize your hardware.
