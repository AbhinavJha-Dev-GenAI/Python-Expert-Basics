# SQLAlchemy Deep Dive 🏗️

SQLAlchemy is the definitive SQL toolkit and ORM for Python. It consists of two major components: **Core** and **ORM**.

## 1. SQLAlchemy Core (Logic Layer)
Similar to **Dapper** in .NET, Core is for developers who want full control over their SQL. It uses a "Schema-centric" approach.
```python
from sqlalchemy import Table, Column, Integer, String, MetaData

metadata = MetaData()
users = Table('users', metadata,
    Column('id', Integer, primary_key=True),
    Column('name', String),
)
```

## 2. SQLAlchemy ORM (Object Layer)
Similar to **Entity Framework**, the ORM maps Python classes directly to database tables. It uses a "Domain-centric" approach.
```python
from sqlalchemy.orm import DeclarativeBase, Mapped, mapped_column

class Base(DeclarativeBase):
    pass

class User(Base):
    __tablename__ = "users"
    id: Mapped[int] = mapped_column(primary_key=True)
    name: Mapped[str]
```

## 3. The Engine & Connection Pool
The **Engine** is the source of database connectivity. It handles a **Connection Pool** automatically.
```python
from sqlalchemy import create_engine
engine = create_engine("postgresql://user:pass@localhost/db", pool_size=10)
```

## 4. The Session (Unit of Work)
The `Session` manages database transactions.
```python
from sqlalchemy.orm import Session

with Session(engine) as session:
    new_user = User(name="John")
    session.add(new_user)
    session.commit() # Unit of Work pattern
```

## 5. Relationships
SQLAlchemy allows complex relationships (1-many, many-many) with ease.
```python
class Post(Base):
    __tablename__ = "posts"
    user_id: Mapped[int] = mapped_column(ForeignKey("users.id"))
    author: Mapped["User"] = relationship("User", back_populates="posts")
```

## 6. Alembic: The Migration Tool
Alembic is to SQLAlchemy what EF Migrations is to Entity Framework. It tracks changes to your models and generates SQL scripts to update your database schema.
