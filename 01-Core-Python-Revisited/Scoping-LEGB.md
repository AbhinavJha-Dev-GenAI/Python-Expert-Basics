# Scoping and the LEGB Rule 🔭

Python uses a specific hierarchy to resolve names (variables). Understanding this prevents "Variable not defined" or "Shadowing" bugs.

## 1. The LEGB Hierarchy
Search order for a name:
1. **L (Local)**: Defined inside the current function.
2. **E (Enclosing)**: Defined in an outer function (for nested functions).
3. **G (Global)**: Defined at the top level of the module/file.
4. **B (Built-in)**: Pre-defined by Python (e.g., `len`, `int`, `print`).

## 2. Examples of Shadowing
Shadowing occurs when a narrower scope redefines a name from an outer scope.
```python
x = "Global"

def outer():
    x = "Enclosing"
    def inner():
        x = "Local"
        print(x) # Resolves to "Local"
    inner()

outer()
```

## 3. Modifying Scopes: `global` and `nonlocal`

### The `global` Keyword
Used to tell Python that a variable inside a function refers to the global scope.
```python
count = 0
def increment():
    global count
    count += 1
```

### The `nonlocal` Keyword
Used in nested functions to modify a variable in the enclosing (outer) scope, but not the global scope.
```python
def counter():
    c = 0
    def inc():
        nonlocal c
        c += 1
        return c
    return inc
```

## 4. Common Pitfalls
- **UnboundLocalError**: Happens when you try to access a local variable before it's assigned, often when Python mistakenly flags it as local due to an assignment later in the function.
- **Modifying Built-ins**: Never name variables `list`, `dict`, or `str` as it shadows the built-in constructors.
