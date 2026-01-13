# Scikit-Learn Basics 🤖

Scikit-learn is the gold standard for traditional machine learning algorithms.

## 1. The Estimator API
All algorithms in sklearn share the same interface:
- `fit(X, y)`: Train the model.
- `predict(X)`: Make predictions.
- `score(X, y)`: Evaluate the model.

## 2. Transformers & Pipelines
Data often needs processing (scaling, encoding) before modeling.
- **Transformers**: `fit_transform()`.
- **Pipelines**: Combine steps into one object.

```python
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.svm import SVC

pipe = Pipeline([
    ('scaler', StandardScaler()),
    ('svc', SVC())
])

pipe.fit(X_train, y_train)
```

## 3. Model Evaluation
- **Cross-Validation**: `cross_val_score`.
- **Metrics**: `mean_squared_error`, `f1_score`, `confusion_matrix`.

## 4. Hyperparameter Tuning
- **GridSearchCV**: Exhaustive search over specified parameter values.
- **RandomizedSearchCV**: Sampling from parameter distributions.

## 5. The "Swiss Army Knife" of ML
Sklearn is not just for models; it's for the entire workflow:
- `train_test_split`.
- `OneHotEncoder` / `LabelEncoder`.
- `PCA` (Dimensionality Reduction).
