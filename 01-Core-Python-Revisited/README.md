# Core Python Revisited 🐍

Welcome to the internal mechanics of Python! This section focuses on how Python works under the hood, moving beyond simple syntax to understand the "why" and "how".

---

## 🏗️ Internal Mechanics of Functions

In Python, functions are **first-class objects**. This means they can be passed as arguments, returned from other functions, and assigned to variables.

- [Functions and Frames](Functions-and-Frames.md): Execution context and stack.
- [Scoping (LEGB)](Scoping-LEGB.md): Variable resolution rules.
- [Mutability Mechanics](Mutability-Mechanics.md): Object identity and pitfalls.
- [Core Features Deep Dive](Core-Features-Deep-Dive.md): Generators, Decorators, and Context Managers.

---

## 📊 Data Types: Mutable vs Immutable

Understanding memory management starts with knowing which objects can change.

| Data Type | Mutability | Examples |
|-----------|------------|----------|
| `int`, `float`, `bool` | **Immutable** | `x = 5; x = 6` (creates a new object) |
| `str` | **Immutable** | `s[0] = 'a'` (Raises TypeError) |
| `tuple` | **Immutable** | Fixed sequence |
| `list` | **Mutable** | `my_list.append(1)` |
| `dict` | **Mutable** | `my_dict['key'] = 'value'` |
| `set` | **Mutable** | `my_set.add(1)` |

> [!IMPORTANT]
> **Default Arguments Warning**: Never use mutable objects (like `list`) as default arguments in functions. Use `None` instead.

---

## 🔑 Advanced Revisit topics

### 1. Comprehensions (List, Dict, Set)
Fast, readable way to create collections.
```python
squares = [x**2 for x in range(10) if x % 2 == 0]
```

### 2. Args and Kwargs (`*args`, `**kwargs`)
- `*args`: Collects positional arguments as a tuple.
- `**kwargs`: Collects keyword arguments as a dictionary.

### 3. Lambdas (Anonymous Functions)
Small, one-line functions.
```python
multiply = lambda x, y: x * y
```

### 4. Global vs Nonlocal
- `global`: Used to modify a variable in the global scope from within a function.
- `nonlocal`: Used in nested functions to modify a variable in the outer (but non-global) scope.

---

## 🛠️ Practice Exercises
1. Implement a function that tracks how many times it has been called using a closure.
2. Create a list comprehension that filters a list of strings for those containing 'a' and converts them to uppercase.
