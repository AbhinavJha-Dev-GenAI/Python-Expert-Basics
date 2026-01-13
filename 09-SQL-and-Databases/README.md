# SQL and Databases in Python 🗄️

This section focuses on how Python interacts with various database systems, from raw drivers to high-level ORMs.

---

## 🛠️ How Python Interacts with Databases

Python follows the **DB-API 2.0 (PEP 249)** standard for database drivers. This ensures consistency across different database systems.

- [Python DB Drivers](Python-DB-Drivers.md): Raw drivers for every major DB.
- [SQLAlchemy Deep Dive](SQLAlchemy-Deep-Dive.md): Core and ORM patterns.
- [ORM vs Stored Procedures](ORM-vs-Stored-Procedures.md): When and how to use SPs in Python.

---

## 🏗️ Python ORMs (The "Entity Framework" equivalent)

Object-Relational Mappers (ORMs) allow you to interact with databases using Python classes instead of raw SQL.

### 1. SQLAlchemy (The Industry Standard)
*   **SQLAlchemy Core**: Similar to Dapper (close to SQL).
*   **SQLAlchemy ORM**: Similar to Entity Framework.

```python
from sqlalchemy import Column, Integer, String, create_engine
from sqlalchemy.ext.declarative import declarative_base

Base = declarative_base()

class User(Base):
    __tablename__ = 'users'
    id = Column(Integer, primary_key=True)
    name = Column(String)

# Interaction looks like EF
engine = create_engine('sqlite:///test.db')
# session.add(user), session.commit(), etc.
```

### 2. Django ORM
Built into the Django framework. Highly productive but tightly coupled to Django.

### 3. Peewee
A small, expressive ORM. Great for smaller projects and SQLite/MySQL/PostgreSQL.

---

## ⚙️ Stored Procedures in Python
Interacting with SPs depends on the driver/ORM:

*   **Raw Driver**:
    ```python
    cursor.callproc('my_stored_procedure', [arg1, arg2])
    ```
*   **SQLAlchemy**:
    ```python
    result = session.execute("CALL my_stored_procedure(:val)", {'val': 5})
    ```

---

## 🗺️ Mapping concepts from C#/.NET

| Feature | .NET Entity Framework / Dapper | Python Equivalent |
|---------|--------------------------------|-------------------|
| **ORM** | Entity Framework | SQLAlchemy ORM, Django ORM |
| **Micro-ORM**| Dapper | SQLAlchemy Core, Peewee |
| **Raw SQL** | ADO.NET (`SqlCommand`) | DB-API Drivers (`psycopg2`, `sqlite3`) |
| **Async** | `async/await` | `asyncio` + `asyncpg`/`motor` |

---

## 🛠️ Best Practices
- **Connection Pooling**: Always use a connection pool (SQLAlchemy handles this by default).
- **Migrations**: Use **Alembic** (the standard for SQLAlchemy migrations) similar to EF Migrations.
- **Security**: Never use string formatting for queries; always use **Parameterized Queries** to prevent SQL Injection.
