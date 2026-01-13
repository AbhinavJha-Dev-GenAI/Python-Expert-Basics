# Data Structures and Algorithms in Python 🧠

This section covers the core data structures used in Python and how to implement standard algorithms in a "Pythonic" way.

---

## 🐍 Python-Specific Data Structures

Python’s built-in collections are highly optimized and should be your first choice.

- [Python Built-in Collections](Python-Builtin-Collections.md): Lists, Dicts, and their internals.
- [Pythonic I/O and Input](Pythonic-IO-and-Input.md): Handling data efficiently.
- [Standard Algorithms (Pythonic)](Standard-Algorithms-Pythonic.md): BFS, DFS, and DP with Python tools.

### 3. Sets (Unique Collections)
*   **Initialization**: `my_set = {1, 2, 3}` or `set()`
*   **Usage**: Membership testing (`item in my_set`) and removing duplicates.
*   **Time Complexity**: O(1) for membership check.

---

## 🛠️ Basic Operations & I/O

### Taking Input in Python
```python
# Multiple integers on one line
a, b, c = map(int, input().split())

# Reading a list of integers
nums = list(map(int, input().split()))

# Reading multiple lines until EOF
import sys
data = sys.stdin.read().splitlines()
```

### Initializing Complex Structures
- **2D List**: `grid = [[0]*cols for _ in range(rows)]` (Avoid `[[0]*cols]*rows`)
- **DefaultDict**: `from collections import defaultdict; d = defaultdict(list)`

---

## 📈 Standard Algorithms (Pythonic Implementation)

### 1. Sorting
Python uses **Timsort** (hybrid of Merge Sort and Insertion Sort).
```python
nums.sort() # In-place
sorted_nums = sorted(nums, key=lambda x: -x) # Custom key (Reverse)
```

### 2. Heaps (Priority Queues)
```python
import heapq
heap = []
heapq.heappush(heap, 4)
heapq.heappop(heap) # Returns the smallest element
```

### 3. Binary Search
```python
import bisect
pos = bisect.bisect_left(sorted_list, target)
```

---

## 🛠️ Summary of Complexity

| Data Structure | Access | Search | Insert | Delete |
|----------------|--------|--------|--------|--------|
| **List** | O(1) | O(n) | O(n) | O(n) |
| **Dict** | O(1) | O(1) | O(1) | O(1) |
| **Set** | N/A | O(1) | O(1) | O(1) |
| **Deque** | O(n) | O(n) | O(1) | O(1) |

---

## 📖 Best Practices
- Use **List Comprehensions** for simple transformations.
- Use `collections.deque` for double-ended queues (faster than list pops from front).
- Use `itertools` for efficient looping and permutations/combinations.
- Prefer `enumerate()` over `range(len())`.
