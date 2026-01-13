# Functions and Frames 🎞️

In Python, understanding how functions execute is key to mastering recursion, closures, and debugging.

## 1. Functions are Objects
In Python, everything is an object. A function is no different. When you define a function:
```python
def my_func(x):
    return x * 2
```
Python creates an object of type `function`. You can inspect its attributes like `__name__`, `__code__`, and `__defaults__`.

## 2. Stack Frames
When a function is called, Python creates a **Frame object** and pushes it onto the call stack.
- **The Frame contains**:
  - Local variables.
  - Arguments passed.
  - Pointer to the previous frame (caller).
  - The return address.

### The Lifecycle
1. **Creation**: Function is called -> Frame pushed.
2. **Execution**: Bytecode is executed within this frame.
3. **Destruction**: Function returns -> Frame popped (and usually garbage collected).

## 3. High-Order Functions
Since functions are objects, they can be:
- Passed as arguments (e.g., `map`, `filter`).
- Returned from other functions (Closures).
- Stored in data structures.

```python
def multiply_by(n):
    def factor(x):
        return x * n
    return factor

double = multiply_by(2)
print(double(5)) # Outputs 10
```

## 4. Introspection
You can use the `inspect` module to look into frames.
```python
import inspect

def who_called_me():
    frame = inspect.currentframe().f_back
    print(f"Called from {frame.f_code.co_name}")

def caller():
    who_called_me()

caller() # Outputs: Called from caller
```
