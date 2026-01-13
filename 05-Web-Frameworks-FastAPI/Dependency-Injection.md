# Dependency Injection 💉

FastAPI's Dependency Injection system is one of its most powerful and unique features.

## 1. What is Dependency Injection (DI)?
DI is a design pattern where an object receives other objects that it depends on. In FastAPI, this is done via the `Depends()` function in route parameters.

## 2. Basic Usage
Shared logic can be extracted into a function and "injected" into any route.
```python
from fastapi import Depends

def common_parameters(q: str | None = None, skip: int = 0, limit: int = 100):
    return {"q": q, "skip": skip, "limit": limit}

@app.get("/items/")
async def read_items(params: dict = Depends(common_parameters)):
    return params
```

## 3. Database Sessions (The standard pattern)
DI is the correct way to handle database connections, ensuring they are opened and closed for every request.
```python
def get_db():
    db = SessionLocal()
    try:
        yield db
    finally:
        db.close()

@app.get("/users/")
def get_users(db: Session = Depends(get_db)):
    # Use db here
```

## 4. Sub-dependencies
Dependencies can depend on other dependencies, creating a tree.
```python
def get_current_user(token: str = Depends(get_token)):
    # logic to get user from token
    return user

def get_admin_user(user: User = Depends(get_current_user)):
    if not user.is_admin:
        raise HTTPException(status_code=400, detail="Not admin")
    return user
```

## 5. Why use DI?
- **Code Reuse**: Write authentication or DB logic once.
- **Testability**: Easily "override" dependencies in unit tests.
- **Maintainability**: Centralized logic for security and data handling.
