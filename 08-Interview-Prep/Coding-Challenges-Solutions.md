# Coding Challenges & Solutions 📝

Common coding problems for Python roles, with "Pythonic" solutions.

## 1. Flatten a Nested List
**Requirement**: Convert `[[1, 2], [3], [[4, 5], 6]]` to `[1, 2, 3, 4, 5, 6]`.
```python
def flatten(nested):
    for item in nested:
        if isinstance(item, list):
            yield from flatten(item)
        else:
            yield item

result = list(flatten([[1, 2], [3], [[4, 5], 6]]))
```

## 2. LRU Cache (Least Recently Used)
**Requirement**: Implement a cache that removes the oldest item when it reaches capacity.
```python
from collections import OrderedDict

class LRUCache:
    def __init__(self, capacity):
        self.cache = OrderedDict()
        self.capacity = capacity

    def get(self, key):
        if key not in self.cache: return -1
        self.cache.move_to_end(key)
        return self.cache[key]

    def put(self, key, value):
        if key in self.cache:
            self.cache.move_to_end(key)
        self.cache[key] = value
        if len(self.cache) > self.capacity:
            self.cache.popitem(last=False)
```

## 3. Group Anagrams
**Requirement**: Group words that share the same letters.
```python
from collections import defaultdict

def group_anagrams(words):
    groups = defaultdict(list)
    for word in words:
        key = "".join(sorted(word))
        groups[key].append(word)
    return list(groups.values())
```

## 4. Balanced Parentheses
```python
def is_balanced(s):
    mapping = {")": "(", "}": "{", "]": "["}
    stack = []
    for char in s:
        if char in mapping:
            top = stack.pop() if stack else '#'
            if mapping[char] != top: return False
        else:
            stack.append(char)
    return not stack
```
