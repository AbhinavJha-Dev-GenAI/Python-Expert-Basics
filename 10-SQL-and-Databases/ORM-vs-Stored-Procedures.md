# ORM vs Stored Procedures ⚖️

While ORMs are powerful, professional systems often require interacting with legacy or performance-critical Stored Procedures (SPs).

## 1. Why use Stored Procedures?
- **Performance**: Pre-compiled and executed on the DB server.
- **Security**: Can restrict access to raw tables and only allow execution of specific SPs.
- **Consistency**: Complex business logic remains in the DB, accessible by multiple applications (C#, Python, Java).

## 2. Calling SPs via Raw Drivers
Each driver has a specific way to call SPs.
```python
# Psycopg2 (Postgres)
cur.callproc('calculate_total', [5, 10])
result = cur.fetchone()

# Mysql-connector
cur.callproc('get_user_by_id', (1,))
for result in cur.stored_results():
    print(result.fetchall())
```

## 3. Calling SPs via SQLAlchemy
You can use `session.execute()` with the SQL `CALL` or `EXEC` command.
```python
from sqlalchemy import text

with Session(engine) as session:
    # Postgres/MySQL
    result = session.execute(text("CALL my_stored_procedure(:param)"), {"param": 100})
    
    # Returning results
    rows = result.fetchall()
```

## 4. ORM vs SP: The Trade-offs

| Feature | ORM (SQLAlchemy/EF) | Stored Procedure |
|---------|---------------------|------------------|
| **Version Control** | Easy (Python code) | Hard (DB side) |
| **Logic Location** | App code | DB code |
| **Performance** | Good for CRUD | Better for massive batch Ops|
| **DB Portability** | High | Low (Dialect specific) |

## 5. Best Practice: The Hybrid Approach
Use the **ORM** for 90% of standard operations (CRUD, simple filters) and **Stored Procedures** for the 10% of high-performance complex logic. This gives you the maintainability of an ORM with the power of the database engine.
