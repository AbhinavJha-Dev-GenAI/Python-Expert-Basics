# 10. Data Structures & Algorithms (DSA) 🧬🔢

Algorithms are the logic of your system. Understanding complexity (Big-O) ensures your code doesn't become a bottleneck as your data grows.

## 1. Complexity (Big-O Notation) ⏳⚖️

*   **O(1)**: Constant (e.g., Accessing a list by index).
*   **O(log N)**: Logarithmic (e.g., Binary Search).
*   **O(N)**: Linear (e.g., Simple loop over a list).
*   **O(N log N)**: Standard Sorting (e.g., Quicksort, Mergesort).
*   **O(N²)**: Quadratic (e.g., Nested loops).

---

## 2. Pythonic Data Structures 🧱

| Structure | Best Use Case | Search Complexity |
| :--- | :--- | :--- |
| **List** | Ordered items, stack/queue. | $O(N)$ |
| **Set** | Unique items, fast membership. | **$O(1)$** |
| **Dict** | Key-Value mapping. | **$O(1)$** |
| **Deque** | Fast append/pop from both ends. | $O(1)$ |

---

## 3. Essential Algorithms for ML 🏎️

*   **Sorting**: Efficiently organizing your data points.
*   **Binary Search**: Finding a value in an ordered list in $O(log N)$ time.
*   **Recursion**: Necessary for processing Tree-based models (Random Forest, XGBoost).
*   **Dynamic Programming**: Breaking complex problems (like sequence alignment) into sub-problems.

---

## 🛠️ Essential Snippet (Dictionary for Performance)

```python
# SLOW (Linear Search)
names = ["Alice", "Bob", "Charlie", ...]
if "Bob" in names: # Takes O(N)
    pass

# FAST (Hash-based Search)
name_set = {"Alice", "Bob", "Charlie", ...}
if "Bob" in name_set: # Takes O(1)! Even with 1 million names.
    pass
```

---

## 📊 Summary
Python provides high-level tools, but a Senior Engineer knows how they work under the hood. choosing a **Set** over a **List** can literally make your code 1,000x faster for searching tasks.
