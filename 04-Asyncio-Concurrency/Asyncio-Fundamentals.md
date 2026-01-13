# Asyncio Fundamentals 🔄

`asyncio` is the foundation of modern, high-concurrency Python web servers (like FastAPI).

## 1. Cooperative Multitasking
Unlike threads (where the OS interrupts them), `asyncio` uses **Cooperative Multitasking**. Tasks must explicitly "yield" control back to the event loop using `await`.

## 2. Coroutines & Tasks
- **Coroutine**: A function defined with `async def`. Calling it returns a coroutine object but doesn't execute it yet.
- **Task**: A wrapper around a coroutine that schedules it to run on the event loop.

```python
import asyncio

async def say_hello():
    await asyncio.sleep(1) # Yields control
    print("Hello")

# Run the coroutine
asyncio.run(say_hello())
```

## 3. The Event Loop
The heart of `asyncio`. It runs in a single thread and manages all scheduled tasks.
- It polls for events (I/O) and switches between tasks when they are "ready".

## 4. Running Parallel Tasks
To run multiple tasks "simultaneously" without waiting for each sequentially:
```python
# Modern way (3.11+)
async with asyncio.TaskGroup() as tg:
    tg.create_task(job1())
    tg.create_task(job2())

# Older way
await asyncio.gather(job1(), job2())
```

## 5. Blocking the Event Loop ⚠️
**Never use blocking calls** (like `time.sleep()` or heavy `for` loops) in a coroutine. This stops the entire event loop, freezing all other tasks.
- **Fix**: Use `await asyncio.sleep()` or run blocking code in a thread using `loop.run_in_executor()`.
