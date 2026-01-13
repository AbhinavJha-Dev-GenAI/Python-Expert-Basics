# Python Database Drivers 🔌

Drivers are the low-level libraries that allow Python to speak to specific database engines. They all follow the standard **DB-API 2.0 (PEP 249)**.

## 1. Relational Database Drivers (RDBMS)

### PostgreSQL
- **psycopg2**: The most popular and stable driver. High-performance but uses C-extensions.
- **asyncpg**: Built specifically for `asyncio`. Extremely fast, but doesn't follow DP-API 2.0 (it has its own API).

### MySQL
- **mysql-connector-python**: The official Oracle-maintained driver.
- **PyMySQL**: A pure-python implementation. Easier to install on some environments but slightly slower.

### SQLite
- **sqlite3**: Built into the Python standard library. No installation required. Perfect for testing and small local tools.

## 2. NoSQL Drivers

### MongoDB
- **PyMongo**: The standard synchronous driver.
- **Motor**: An asynchronous driver built on top of PyMongo for use with `asyncio`.

### Redis
- **redis-py**: Simple, easy-to-use driver for the Redis in-memory store.

## 3. Basic Usage Pattern (DB-API 2.0)
Most synchronous drivers follow this identical pattern:
```python
import sqlite3 # or psycopg2, etc.

# 1. Connect
conn = sqlite3.connect("database.db")

# 2. Get a cursor
cur = conn.cursor()

# 3. Execute with parameters (to avoid SQL Injection!)
cur.execute("SELECT * FROM users WHERE id = %s", (user_id,))

# 4. Fetch
results = cur.fetchall()

# 5. Close
conn.close()
```

## 4. Parameterized Queries 🛡️
Never use f-strings or `.format()` for queries:
- *Bad*: `f"SELECT * FROM users WHERE id = {user_id}"` -> **SQL Injection Vulnerable!**
- *Good*: `cur.execute("... WHERE id = %s", (user_id,))` -> **Safe!**

## 5. Summary Table

| Database | Recommended Driver | Async Support |
|----------|-------------------|---------------|
| **PostgreSQL**| `psycopg2` | `asyncpg` |
| **MySQL** | `mysql-connector` | `aiomysql` |
| **SQLite** | `sqlite3` | `aiosqlite` |
| **MongoDB** | `pymongo` | `motor` |
