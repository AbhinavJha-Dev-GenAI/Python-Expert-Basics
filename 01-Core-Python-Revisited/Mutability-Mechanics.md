# Mutability Mechanics 🧠

Understanding mutability is the difference between writing predictable code and hunting "ghost" bugs in production.

## 1. The Identity of Objects
Every object in Python has a unique ID (memory address). Use `id(obj)` to see it.
- **Immutable**: When you "change" it, Python creates a *new* object.
- **Mutable**: When you change it, Python modifies the *existing* object (ID stays the same).

```python
x = 10
print(id(x))
x += 1
print(id(x)) # Different ID!

l = [1, 2]
print(id(l))
l.append(3)
print(id(l)) # Same ID!
```

## 2. The Mutable Default Argument Pitfall ⚠️
This is one of the most common senior-level interview questions.
```python
def add_item(item, basket=[]):
    basket.append(item)
    return basket

print(add_item("Apple")) # ["Apple"]
print(add_item("Banana")) # ["Apple", "Banana"] <- Oops!
```
**Why?** The default list is created once at definition time, not every time the function is called.
**Fix**: Use `None`.

```python
def add_item(item, basket=None):
    if basket is None:
        basket = []
    basket.append(item)
    return basket
```

## 3. Copying: Shallow vs Deep
- **Shallow Copy**: (`list.copy()`) Copies the container but references the same items.
- **Deep Copy**: (`copy.deepcopy()`) Recursively copies everything.

```python
import copy
original = [[1, 2], [3, 4]]
shallow = original.copy()
deep = copy.deepcopy(original)

original[0][0] = 99
# shallow[0][0] is now 99
# deep[0][0] is still 1
```

## 4. Key Takeaway
Mutables are passed by **assignment** (which behaves like pass-by-reference for the content). Immuntables behave like pass-by-value because any change creates a new object anyway.
