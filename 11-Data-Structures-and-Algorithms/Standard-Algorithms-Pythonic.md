# Standard Algorithms (Pythonic Implementation) 📈

Implementing classic algorithms using Python's high-level features leads to cleaner and more efficient code.

## 1. Searching & Sorting
- **Sorting**: Use `sort()` or `sorted()`. Use the `key` parameter for custom logic.
- **Binary Search**: Use the `bisect` module.

```python
import bisect
arr = [1, 3, 4, 4, 6]
# Find where 4 starts
start = bisect.bisect_left(arr, 4) # Index 2
```

## 2. Graph Traversals (BFS & DFS)
Python's `list` works as a stack for DFS (`append`/`pop`). Use `collections.deque` for BFS (`append`/`popleft`).

### BFS Template
```python
from collections import deque

def bfs(graph, start):
    visited = {start}
    queue = deque([start])
    while queue:
        node = queue.popleft()
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
```

## 3. Dynamic Programming (DP)
Python's `functools.lru_cache` is a cheat code for top-down DP (recursion with memoization).

```python
from functools import lru_cache

@lru_cache(None) # Infinite cache
def fib(n):
    if n < 2: return n
    return fib(n-1) + fib(n-2)
```

## 4. Heap / Priority Queue
Standard implementation for problems requiring the "K largest/smallest" items.
```python
import heapq
heap = [1, 5, 2, 8]
heapq.heapify(heap) # O(n)
heapq.heappop(heap) # Returns 1
```

## 5. Itertools (Algorithm Powerhouse)
The `itertools` library provides "iterative building blocks" that are implemented in C for extreme speed.
- `itertools.permutations`
- `itertools.combinations`
- `itertools.product` (Cartesian product)
- `itertools.chain` (Join multiple iterables)
