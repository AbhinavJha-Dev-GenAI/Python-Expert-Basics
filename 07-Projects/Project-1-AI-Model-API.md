# Project 1: AI Model Serving API 🚀

This project involves building a production-ready FastAPI service that serves a machine learning model.

## 1. Objectives
- Load a pre-trained model (e.g., Scikit-learn, XGBoost).
- Create a `POST` endpoint for predictions.
- Validate inputs using Pydantic.
- Implement background logging to a database.

## 2. Directory Structure
```text
ai_api/
├── main.py
├── models/
│   └── iris_model.joblib
├── schemas.py
├── database.py
└── requirements.txt
```

## 3. Implementation Steps

### Step 1: Pydantic Schema
```python
from pydantic import BaseModel

class IrisRequest(BaseModel):
    sepal_length: float
    sepal_width: float
    petal_length: float
    petal_width: float
```

### Step 2: The API Endpoint
```python
from fastapi import FastAPI, BackgroundTasks
import joblib

app = FastAPI()
model = joblib.load("models/iris_model.joblib")

@app.post("/predict")
async def predict(data: IrisRequest, bg: BackgroundTasks):
    prediction = model.predict([[
        data.sepal_length, data.sepal_width, 
        data.petal_length, data.petal_width
    ]])
    bg.add_task(log_to_db, data, prediction[0])
    return {"class": int(prediction[0])}
```

## 4. Challenges for You
- Add **OAuth2** authentication.
- Add **Prometheus** metrics to track number of requests and latency.
- Containerize the app using **Docker**.
