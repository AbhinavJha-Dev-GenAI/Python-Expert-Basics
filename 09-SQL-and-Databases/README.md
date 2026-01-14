# 09. SQL & Databases 🗄️📜

As an ML Engineer, data is your supply. Most enterprise data lives in SQL databases.

## 1. SQL Fundamentals 🔍

*   **SELECT & WHERE**: Filtering your data.
*   **JOINs**: Combining tables (Inner, Left, Right, Outer).
*   **AGGREGATIONS**: `GROUP BY`, `COUNT`, `SUM`, `AVG`.
*   **WINDOW FUNCTIONS**: `ROW_NUMBER()`, `RANK()`, `LEAD/LAG`. (Crucial for time-series features).

---

## 2. SQLAlchemy (The ORM) 🐍🏗️

Instead of writing raw strings of SQL, we use an **Object-Relational Mapper (ORM)**.
- **Benefit**: Keeps your code Pythonic and prevents SQL Injection attacks.
- **Components**: `Engine` (The connection), `Base` (The schema), `Session` (The interaction).

```python
from sqlalchemy import Column, Integer, String
from sqlalchemy.ext.declarative import declarative_base

Base = declarative_base()

class User(Base):
    __tablename__ = 'users'
    id = Column(Integer, primary_key=True)
    name = Column(String)
```

---

## 3. Database Types for AI 🎭

*   **Postgres**: The "Standard" for structured relational data.
*   **SQLite**: Great for local development and edge devices.
*   **NoSQL (MongoDB)**: For unstructured JSON data.
*   **Vector DBs (Pinecone/Chroma)**: For high-dimensional AI embeddings.

---

## 🛠️ Essential Snippet (Complex Join Concept)

```sql
-- Find total sales per user for the year 2023
SELECT u.name, SUM(o.total_price) as total_sales
FROM users u
JOIN orders o ON u.id = o.user_id
WHERE o.order_date >= '2023-01-01'
GROUP BY u.name
HAVING SUM(o.total_price) > 1000;
```

---

## 🌎 Summary
A professional engineer doesn't export CSVs and then filter them in Pandas. They do as much filtering and aggregation as possible **inside the database** using SQL, as it is far more efficient.
