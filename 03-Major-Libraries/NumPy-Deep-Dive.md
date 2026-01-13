# NumPy Deep Dive 🔢

NumPy is more than just arrays; it is the performance engine of the Python data ecosystem.

## 1. The `ndarray` Object
- **C-Style Memory**: NumPy arrays are contiguous blocks of memory, unlike Python lists (which are arrays of pointers).
- **Fixed Type**: All elements in an array must be of the same `dtype`.

## 2. Vectorization & Ufuncs
**Universal Functions (ufuncs)** are functions that operate on `ndarray` objects in an element-by-element fashion.
```python
import numpy as np
a = np.random.rand(1000000)
# This is executed in optimized C code:
b = np.sin(a) 
```

## 3. Broadcasting Rules
Broadcasting allows NumPy to perform arithmetic on arrays of different shapes.
- **Rule 1**: If arrays have different rank, prepend 1s to the smaller shape.
- **Rule 2**: Arrays are compatible if dimensions are equal or one of them is 1.

```python
# (3, 3) + (3,) 
# (3,) becomes (1, 3) -> then (3, 3) via tiling
```

## 4. Advanced Indexing & Slicing
- **Views vs Copies**: Most slices return a **view** (changing the slice changes the original). Fancy indexing (using a list of indices) returns a **copy**.
```python
slice_view = arr[0:5] # View
fancy_copy = arr[[0, 1, 4]] # Copy
```

## 5. Performance Tips
- Use `np.where` instead of loops for conditional logic.
- Pre-allocate arrays if you know the size.
- Avoid resizing arrays (`np.append` creates a full copy of the array).
- Utilize `axis` parameter (e.g., `np.sum(arr, axis=0)`) for multi-dimensional operations.
