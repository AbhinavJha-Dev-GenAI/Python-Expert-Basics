# Pythonic I/O and Input 📥

Handling input efficiently is vital for competitive programming and data processing pipelines.

## 1. Standard Input (`input()`)
`input()` reads a line from `sys.stdin` and strips the trailing newline. It is relatively slow for huge amounts of data.

```python
# Multiple integers on one line
x, y = map(int, input().split())

# List of integers
data = list(map(int, input().split()))
```

## 2. Fast I/O with `sys.stdin`
When reading millions of lines, `input()` becomes a bottleneck. Use `sys.stdin.readline` or read everything at once.

```python
import sys

# Fast line read
line = sys.stdin.readline()

# Read all lines into a list
all_data = sys.stdin.read().splitlines()
```

## 3. Formatted Output (f-strings)
F-strings (3.6+) are the fastest and most readable way to format strings.
```python
print(f"Result: {val:.2f}") # 2 decimal places
```

## 4. Working with Large Files
Never use `.readlines()` on a 10GB file (it loads it all into RAM). Iterate over the file object instead.
```python
with open("massive_data.txt", "r") as f:
    for line in f:
        process(line) # Reads one line at a time (Memory efficient)
```

## 5. Summary of I/O Patterns

| Goal | Best Pattern |
|------|--------------|
| Small Input | `input()` |
| Thousands of integers | `map(int, sys.stdin.read().split())` |
| Large Line-by-line| `for line in sys.stdin:` |
| Formatted Prints | `f"{var}"` |
