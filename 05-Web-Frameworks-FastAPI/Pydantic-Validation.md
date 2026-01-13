# Pydantic Validation 🛡️

Pydantic is the "secret sauce" of FastAPI, providing robust data validation and serialization using Python Type Hints.

## 1. Defining Models
Models are simply classes that inherit from `pydantic.BaseModel`.
```python
from pydantic import BaseModel, Field, EmailStr

class Item(BaseModel):
    name: str
    price: float = Field(gt=0, description="Price must be positive")
    email: EmailStr
```

## 2. Automatic Coercion
Pydantic doesn't just check types; it **converts** them if possible.
- If you pass `"123"` to an `int` field, Pydantic converts it to `123`.

## 3. Validation Logic
You can add custom logic using the `@validator` (old) or `@field_validator` (Pydantic V2) decorator.
```python
from pydantic import field_validator

class User(BaseModel):
    username: str

    @field_validator('username')
    @classmethod
    def username_must_be_alphanumeric(cls, v: str):
        if not v.isalnum():
            raise ValueError('must be alphanumeric')
        return v
```

## 4. Serialization (`.model_dump()`)
Converting a Pydantic object to a dictionary or JSON is simple.
- `model.model_dump()` -> returns a `dict`.
- `model.model_dump_json()` -> returns a `str`.

## 5. Nested Models
Perfect for complex API payloads.
```python
class Tag(BaseModel):
    id: int
    label: str

class Article(BaseModel):
    title: str
    tags: list[Tag]
```

## 6. Settings Management
Pydantic's `BaseSettings` is the industry standard for managing environment variables.
```python
from pydantic_settings import BaseSettings

class Settings(BaseSettings):
    db_url: str
    api_key: str

    class Config:
        env_file = ".env"
```
