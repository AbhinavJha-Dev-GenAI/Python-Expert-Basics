# Major Python Libraries for AI/ML 📚

This section covers the "Big Five" libraries that form the backbone of data science and machine learning in Python.

---

- [NumPy Deep Dive](NumPy-Deep-Dive.md): Memory, Broadcasting, and Performance.
- [Pandas Manipulation](Pandas-Manipulation.md): Multi-Indexing, Reshaping, and ETL.
- [Visualization Best Practices](Visualization-Best-Practices.md): Matplotlib and Seaborn.
- [Scikit-Learn Basics](Scikit-Learn-Basics.md): Estimators, Transformers, and Pipelines.

---

## 📊 3. Matplotlib & Seaborn (Visualization)
*   **Matplotlib**: The "standard" for 2D plots. Highly customizable but verbose.
*   **Seaborn**: Built on top of Matplotlib. Provides a high-level interface for drawing attractive statistical graphics.

```python
import matplotlib.pyplot as plt
import seaborn as sns

sns.scatterplot(data=df, x='weight', y='height', hue='species')
plt.title("Weight vs Height Analysis")
plt.show()
```

---

## 🤖 4. Scikit-learn (Machine Learning)
The most popular library for traditional ML (regression, classification, clustering).

*   **API Consistency**: `fit()`, `transform()`, `predict()`.
*   **Pipelines**: Chain multiple steps together (e.g., scaling + PCA + SVC).

```python
from sklearn.linear_model import LogisticRegression
model = LogisticRegression()
model.fit(X_train, y_train)
predictions = model.predict(X_test)
```

---

## 🕸️ 5. SciPy (Scientific Python)
Used for scientific and technical computing (integration, optimization, signal processing).

---

## 🛠️ Summary Table

| Library | Primary Use Case | Key Object |
|---------|------------------|------------|
| **NumPy** | Linear Algebra, Arrays | `ndarray` |
| **Pandas** | Tabular Data, ETL | `DataFrame` |
| **Matplotlib**| Basic Plotting | `Figure` |
| **Seaborn** | Statistical Viz | `Axes` |
| **Scikit-learn**| Machine Learning | `Estimator` |

---

## 📖 Recommended Reading
- [NumPy Documentation](https://numpy.org/doc/)
- [Pandas Documentation](https://pandas.pydata.org/docs/)
