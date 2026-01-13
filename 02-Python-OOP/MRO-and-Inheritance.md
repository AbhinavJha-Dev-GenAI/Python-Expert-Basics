# MRO and Inheritance Details 🧬

Python's power in multiple inheritance comes from its predictable Method Resolution Order (MRO).

## 1. Multiple Inheritance
Python allows a class to inherit from multiple parent classes.
```python
class Swimmer:
    def move(self): print("Swimming")

class Flyer:
    def move(self): print("Flying")

class Duck(Swimmer, Flyer):
    pass
```

## 2. C3 Linearization (The MRO Algorithm)
How does Python decide which `move()` to call for `Duck`? It uses the C3 Linearization algorithm.
- Rules:
  - Subclasses before parents.
  - Left-to-right ordering of parents.
  - Consistency in the hierarchy.

Use `Duck.mro()` to see the order: `[Duck, Swimmer, Flyer, object]`.

## 3. The `super()` Function
`super()` does NOT necessarily call the parent class; it calls the **next class in the MRO**.
```python
class A:
    def __init__(self):
        print("A")
        super().__init__()

class B(A):
    def __init__(self):
        print("B")
        super().__init__()

class C(A):
    def __init__(self):
        print("C")
        super().__init__()

class D(B, C):
    def __init__(self):
        print("D")
        super().__init__()

# Order: D -> B -> C -> A -> object
D() # Outputs: D, B, C, A
```

## 4. The Diamond Problem 💎
Because of C3 Linearization, Python handles the "Diamond Problem" (where two parents share a common grandparent) gracefully by ensuring the grandparent (`A` in the example above) is only called once.

## 5. Mixins
Mixins are classes designed to provide specific functionality to other classes via multiple inheritance, without being a "base" class themselves.
```python
class JsonMixin:
    def to_json(self):
        import json
        return json.dumps(self.__dict__)

class User(JsonMixin):
    def __init__(self, name):
        self.name = name
```
