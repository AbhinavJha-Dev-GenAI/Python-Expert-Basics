# 02. Python OOP (Object-Oriented Programming) 🏛️🧬

OOP is the standard for building complex, maintainable AI systems. It allows you to model real-world concepts (Models, Datasets, Pipelines) as "Objects."

## 1. Classes & Instances 🏗️

- **Class**: The blueprint (e.g., `NeuralNetwork`).
- **Instance**: The specific object in memory (e.g., `my_model = NeuralNetwork()`).
- **`__init__`**: The constructor method for initializing state.

---

## 2. The 4 Pillars of OOP 🛡️

1.  **Encapsulation**: Hiding internal data and exposing only what is necessary (using `_protected` or `__private` attributes).
2.  **Inheritance**: Reusing code by creating a sub-class (e.g., `CNN` inherits from `NeuralNetwork`).
3.  **Polymorphism**: Different classes using the same method name (e.g., both `VisionModel` and `TextModel` having a `.predict()` method).
4.  **Abstraction**: Hiding complex logic behind simple interfaces.

---

## 3. Dunder (Magic) Methods 🪄

Methods with double-underscores that control how objects behave with standard Python operators.
- `__str__`: Human-readable string representation.
- `__len__`: What happens when you call `len(obj)`.
- `__getitem__`: Allows indexing like `obj[index]` (Used in PyTorch Datasets).

---

## 4. `@classmethod` vs. `@staticmethod` ⚖️

*   **Instance Method**: Takes `self`. Accesses instance-specific data.
*   **Class Method**: Takes `cls`. Used for "Factory methods" (creating an instance from a file/config).
*   **Static Method**: Takes no special first argument. Just a utility function that lives inside the class.

---

## 🛠️ Essential Snippet (A Pythonic Dataset Class)

```python
class ImageDataset:
    def __init__(self, images, labels):
        self.images = images
        self.labels = labels
        
    def __len__(self):
        return len(self.images)
        
    def __getitem__(self, idx):
        return self.images[idx], self.labels[idx]

# Usage
dataset = ImageDataset(imgs, lbls)
print(f"Dataset Size: {len(dataset)}")
img, lbl = dataset[0]
```

---

## 🧩 Pro-Tip: Composition over Inheritance
In ML, instead of deep inheritance trees, use **Composition**. Give your `Model` class an `Optimizer` object and a `LossFunction` object. This makes your code much more flexible and easier to test.
