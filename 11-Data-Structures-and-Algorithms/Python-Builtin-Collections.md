# Python Built-in Collections 📦

Python's built-in collections are highly optimized, with most being implemented in C. Understanding their "under-the-hood" behavior is critical for performance.

## 1. List (Dynamic Array)
- **Complexity**: O(1) for append/access, O(n) for insert/delete.
- **Behind the scenes**: It's a dynamic array of pointers to objects. When it reaches its capacity, it over-allocates extra space to make future appends O(1) amortized.
- **Advanced**: `list.pop(0)` is O(n). If you need to pop from the front, use `collections.deque`.

## 2. Dict (Hash Map)
- **Complexity**: O(1) average for all operations.
- **Behind the scenes**: Uses a hash table with open addressing for collision resolution. Since Python 3.7, dicts are **ordered** (they remember the insertion order) as an implementation detail that became part of the language spec.
- **Memory**: Dicts are memory-hungry. Use `__slots__` in classes to save space if you have millions of objects.

## 3. Set (Hash Set)
- **Complexity**: O(1) average for membership testing.
- **Mathematics**: Supports union (`|`), intersection (`&`), difference (`-`), and symmetric difference (`^`).

## 4. Tuple (Static Array)
- **Complexity**: O(1) for access.
- **Mutability**: Immutable. Once created, it cannot be changed.
- **Performance**: Tuples are slightly faster to instantiate and take less memory than lists.
- **NamedTuple**: Use `collections.namedtuple` or `typing.NamedTuple` to give elements names (like a lightweight class).

## 5. The `collections` Module (Specialized DS)
- **`deque`**: Double-ended queue for O(1) pops/appends from either end.
- **`defaultdict`**: Returns a default value for non-existent keys.
- **`Counter`**: A dict subclass for counting hashable objects.
- **`OrderedDict`**: Specifically useful in pre-3.7 versions or if you need to reorder elements.
