# FastAPI Architecture 🏗️

FastAPI is built on a high-performance stack that enables asynchronous web serving.

## 1. The Underpinnings: Starlette & Pydantic
- **Starlette**: The lightning-fast ASGI framework that handles all the web routing, middleware, and request/response logic.
- **Pydantic**: The data validation library that handles the conversion between JSON and Python objects based on type hints.

## 2. ASGI (Asynchronous Server Gateway Interface)
FastAPI is an ASGI framework. Unlike WSGI (like Flask/Django), ASGI supports asynchronous communication, allowing long-lived connections (WebSockets) and efficient handling of I/O-bound tasks.

## 3. Request Lifecycle
1. **Request Received**: Handled by the ASGI server (Uvicorn).
2. **Parsing**: FastAPI matches the URL to a route.
3. **Pydantic Validation**: Input JSON is validated against the specified Pydantic model.
4. **Dependency Resolution**: `Depends()` objects are resolved.
5. **Execution**: Your `async def` function is called.
6. **Serialization**: The response is converted back to JSON via Pydantic.

## 4. Key Performance Features
- **Native Async**: No need for extra libraries to handle async requests.
- **Background Tasks**: Offload heavy work (like logging or sending emails) to run after the response is sent.
```python
from fastapi import BackgroundTasks

@app.post("/process/")
async def create_item(background_tasks: BackgroundTasks):
    background_tasks.add_task(send_email, "user@example.com")
    return {"message": "Processing started"}
```

## 5. Middleware
Middleware allows you to intercept every request and response. Common uses:
- CORS (Cross-Origin Resource Sharing).
- GZip compression.
- Custom authentication headers.
