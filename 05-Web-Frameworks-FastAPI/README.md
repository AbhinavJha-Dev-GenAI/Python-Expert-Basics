# 05. Web Frameworks: FastAPI ⚡🛡️

FastAPI is a modern, high-performance web framework for building APIs with Python 3.8+ based on standard Python type hints.

## 1. Why FastAPI? ❓

*   **Fast**: On par with **NodeJS** and **Go** (thanks to Starlette and Pydantic).
*   **Auto-Documentation**: Generates interactive Swagger UI (`/docs`) and ReDoc (`/redoc`) automatically.
*   **Type Safety**: Uses Pydantic for data validation. If you send a string where an integer is expected, FastAPI returns a clear error.
*   **Async Support**: Native support for `async` and `await`, making it perfect for model inference.

---

## 2. Pydantic Models: Data Validation 🏗️

Pydantic handles the "Schema" of your requests and responses. It ensures that the data entering your AI model is clean.

```python
from pydantic import BaseModel

class PredictionRequest(BaseModel):
    feature_1: float
    feature_2: float
    model_version: str = "v1" # Default value
```

---

## 3. Endpoints & Parameters 📡

*   **Path Parameters**: `/items/{item_id}`
*   **Query Parameters**: `/items/?limit=10`
*   **Request Body**: Using Pydantic models in a `POST` request.

---

## 🛠️ Essential Snippet (A Basic Model API)

```python
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()

class InputData(BaseModel):
    text: str

@app.post("/predict")
async def predict_sentiment(data: InputData):
    # Imagine calling your model here...
    result = "Positive" if "good" in data.text else "Negative"
    return {"sentiment": result}

# Run with: uvicorn main:app --reload
```

---

## 🧩 Pro-Tip: Dependency Injection
FastAPI has a powerful **Dependency Injection** system. Use it to manage database connections or to load your ML model weights into memory **once** when the server starts, rather than loading them for every request.
