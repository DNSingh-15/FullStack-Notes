# 🐘 PostgreSQL — Advanced Notes

## 📌 Overview

**PostgreSQL** is an advanced, open-source **object-relational database system (ORDBMS)** known for:

* ACID compliance
* Extensibility
* Strong concurrency handling
* Advanced indexing and query optimization

---

## 🧠 Core Architecture

### 🔹 Process-Based Architecture

* Each connection = separate backend process
* Managed by **postmaster (server process)**

### 🔹 Memory Structure

| Component            | Description                                   |
| -------------------- | --------------------------------------------- |
| Shared Buffers       | Cache for data pages                          |
| Work_mem             | Memory per query operation (sorting, hashing) |
| Maintenance_work_mem | Used for VACUUM, CREATE INDEX                 |
| WAL Buffers          | Write-Ahead Logging buffer                    |

---

### 🔹 Storage Structure

* **Data Files** → stored in `base/` directory
* **WAL (Write Ahead Log)** → ensures durability
* **Tablespaces** → logical storage management

---

## ⚙️ MVCC (Multi-Version Concurrency Control)

👉 PostgreSQL uses **MVCC** instead of locks

### Key Idea:

* Each row has multiple versions
* Readers don’t block writers

### Columns:

* `xmin` → transaction that created row
* `xmax` → transaction that deleted row

### Benefits:

* High concurrency
* No read locks

---

## 🔥 Indexing (Advanced)

### Types of Indexes

| Type   | Use Case                          |
| ------ | --------------------------------- |
| B-Tree | Default, equality + range queries |
| Hash   | Equality only                     |
| GIN    | JSONB, arrays, full-text search   |
| GiST   | Geospatial, ranges                |
| BRIN   | Large tables, low memory          |

---

### Example

```sql
CREATE INDEX idx_user_email ON users(email);

-- Partial Index
CREATE INDEX idx_active_users 
ON users(email) 
WHERE is_active = true;

-- GIN Index for JSONB
CREATE INDEX idx_metadata 
ON users USING GIN(metadata);
```

---

## 🚀 Query Optimization

### 🔹 EXPLAIN & ANALYZE

```sql
EXPLAIN ANALYZE SELECT * FROM users WHERE email = 'test@mail.com';
```

👉 Look for:

* Seq Scan (bad for large tables)
* Index Scan (good)
* Cost & actual time

---

### 🔹 Common Optimizations

* Use **indexes on WHERE/JOIN columns**
* Avoid `SELECT *`
* Use **LIMIT**
* Normalize vs denormalize wisely
* Use **CTE carefully (can materialize)**

---

## 🔄 Transactions & Isolation Levels

| Level           | Behavior            |
| --------------- | ------------------- |
| Read Committed  | Default             |
| Repeatable Read | Consistent snapshot |
| Serializable    | Strictest           |

```sql
BEGIN;
SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
COMMIT;
```

---

## 🔐 Locking Mechanism

* Row-level locks
* Table-level locks
* Advisory locks

```sql
SELECT * FROM users FOR UPDATE;
```

---

## 🧹 VACUUM & ANALYZE

### Why Needed?

* MVCC creates dead tuples

### Commands:

```sql
VACUUM;
VACUUM FULL;
ANALYZE;
```

👉 Autovacuum handles this automatically

---

## 📦 Partitioning

### Types:

* Range
* List
* Hash

```sql
CREATE TABLE orders (
  id INT,
  created_at DATE
) PARTITION BY RANGE (created_at);
```

---

## 🔗 Replication & Scaling

### 🔹 Replication Types

* Streaming Replication (Primary → Replica)
* Logical Replication (table-level)

### 🔹 Scaling Strategies

| Strategy         | Description             |
| ---------------- | ----------------------- |
| Vertical Scaling | Increase CPU/RAM        |
| Read Replicas    | Scale reads             |
| Sharding         | Horizontal partitioning |

---

## 🧾 JSON & Advanced Features

```sql
SELECT data->>'name' FROM users;
```

* JSONB indexing (GIN)
* Full-text search
* Custom functions
* Extensions (PostGIS)

---

## ⚡ Performance Tuning Checklist

* Tune `shared_buffers` (~25% RAM)
* Optimize `work_mem`
* Use connection pooling (PgBouncer)
* Monitor slow queries
* Proper indexing strategy
* Avoid over-indexing

---

## 🔧 Connection Pooling

👉 Important for Node.js / Backend systems

Tools:

* PgBouncer
* PgPool

---

## 🧪 Common Production Issues

| Issue        | Solution                 |
| ------------ | ------------------------ |
| Slow queries | Indexing, EXPLAIN        |
| Deadlocks    | Proper transaction order |
| Bloat        | VACUUM                   |
| High CPU     | Query tuning             |

---

## 🎯 Interview Questions (Senior Level)

### 1. What is MVCC and why PostgreSQL uses it?

👉 Enables high concurrency without locking reads

---

### 2. Difference between VACUUM and VACUUM FULL?

* VACUUM → cleanup
* VACUUM FULL → rebuild + locks table

---

### 3. B-Tree vs GIN?

* B-Tree → simple queries
* GIN → JSON/array/full-text

---

### 4. How do you debug slow queries?

* EXPLAIN ANALYZE
* Index optimization
* Query rewrite

---

### 5. How to scale PostgreSQL?

* Read replicas
* Partitioning
* Sharding
* Caching (Redis)

---

## 🏗️ Best Practices for Lead Developers

* Design schema with scalability in mind
* Avoid premature optimization
* Use migrations (Liquibase, Flyway)
* Monitor using pg_stat_statements
* Implement backup strategy (WAL archiving)
