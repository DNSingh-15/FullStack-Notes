# 🐘 PostgreSQL — Advanced Notes

---

# 📌 Overview

**PostgreSQL** is an advanced open-source **object-relational database (ORDBMS)** known for:

* ACID compliance
* MVCC-based concurrency
* Extensibility (custom types, extensions)
* Advanced indexing & query planner
* Strong consistency guarantees

---

# 🧠 Internal Architecture (DEEP UNDERSTANDING)

## 🔹 Process Model

* PostgreSQL uses a **process-based architecture (NOT threads)**
* Each connection → **dedicated backend process**

### Core Processes:

* **Postmaster** → main server process
* **Backend processes** → handle queries
* **Background Writer**
* **Checkpointer**
* **WAL Writer**
* **Autovacuum daemon**

---

## 🔹 Memory Architecture

| Component            | Purpose                          |
| -------------------- | -------------------------------- |
| shared_buffers       | Cache frequently accessed pages  |
| work_mem             | Per-operation memory (sort/hash) |
| maintenance_work_mem | Vacuum, index creation           |
| wal_buffers          | WAL buffering                    |

---

## 🔹 Storage Internals

* Data stored in **8KB pages**
* Tables = collection of pages
* Each row = tuple

### Files:

* `base/` → actual table data
* `pg_wal/` → Write-Ahead Logs

---

## 🔥 WAL (Write-Ahead Logging) — VERY IMPORTANT

👉 Core for **durability & crash recovery**

### Flow:

1. Write change to WAL
2. Flush WAL to disk
3. Apply change to data file

### Key Insight:

> "WAL ensures durability before actual data write"

---

# ⚙️ MVCC (Multi-Version Concurrency Control)

## 🔹 How It Works

* Each row has versions (tuples)
* No read locks
* Readers don’t block writers

### System Columns:

* `xmin` → created transaction
* `xmax` → deleted transaction

---

## 🔹 Visibility Rules

* Transaction sees only committed data
* Snapshot-based isolation

---

## 🔥 Problem: Dead Tuples

* Old versions remain → **bloat**

👉 Solved by:

* VACUUM
* Autovacuum

---

# 🔥 Indexing (ADVANCED + INTERVIEW CRITICAL)

## 🔹 Index Types

| Index Type | Use Case                  |
| ---------- | ------------------------- |
| B-Tree     | Default, range + equality |
| Hash       | Equality                  |
| GIN        | JSONB, arrays, full-text  |
| GiST       | Geospatial, ranges        |
| BRIN       | Huge tables               |

---

## 🔹 Advanced Indexing

### Partial Index

```sql
CREATE INDEX idx_active_users
ON users(email)
WHERE is_active = true;
```

### Composite Index

```sql
CREATE INDEX idx_user_email_status
ON users(email, status);
```

### Expression Index

```sql
CREATE INDEX idx_lower_email
ON users(LOWER(email));
```

---

## 🔥 Index Trade-offs (IMPORTANT)

| Benefit             | Cost          |
| ------------------- | ------------- |
| Faster reads        | Slower writes |
| Efficient filtering | Extra storage |

---

## 🔥 When Index NOT Used

* Function on column
* Leading wildcard (`%abc`)
* Low selectivity

---

# 🚀 Query Execution & Planner (VERY IMPORTANT)

## 🔹 Query Lifecycle

1. Parsing
2. Planning (optimizer)
3. Execution

---

## 🔹 EXPLAIN ANALYZE

```sql
EXPLAIN ANALYZE SELECT * FROM users WHERE email = 'test@mail.com';
```

### Look for:

* Seq Scan ❌
* Index Scan ✅
* Cost vs Actual time

---

## 🔥 Join Algorithms

| Type        | Use Case        |
| ----------- | --------------- |
| Nested Loop | Small datasets  |
| Hash Join   | Large, no index |
| Merge Join  | Sorted data     |

---

# 🔄 Transactions & Isolation

## 🔹 Isolation Levels

| Level           | Behavior |
| --------------- | -------- |
| Read Committed  | Default  |
| Repeatable Read | Snapshot |
| Serializable    | Strict   |

---

## 🔥 Phenomena

| Issue          | Description        |
| -------------- | ------------------ |
| Dirty Read     | Not possible in PG |
| Non-repeatable | Possible           |
| Phantom        | Possible           |

---

# 🔐 Locking & Concurrency

## 🔹 Locks

* Row-level
* Table-level
* Advisory locks

```sql
SELECT * FROM users FOR UPDATE;
```

---

## 🔥 Deadlocks

👉 Occurs when transactions wait cyclically

### Prevention:

* Consistent lock order
* Short transactions

---

# 🧹 VACUUM Internals

## 🔹 Types

| Type        | Behavior       |
| ----------- | -------------- |
| VACUUM      | Cleanup        |
| VACUUM FULL | Rewrites table |
| AUTOVACUUM  | Automatic      |

---

## 🔥 Important

> PostgreSQL does NOT auto-delete old rows → VACUUM required

---

# 📦 Partitioning (HIGHLY IMPORTANT)

## 🔹 Types

* Range
* List
* Hash

---

## 🔹 Why Partition?

* Faster queries
* Manage large datasets
* Efficient archiving

---

# 🔗 Replication & High Availability

## 🔹 Streaming Replication

* Primary → Replica
* WAL-based

---

## 🔹 Logical Replication

* Table-level replication

---

## 🔥 Failover Strategy

* Primary crash → promote replica

---

# 🧾 JSONB & Advanced Features

```sql
SELECT data->>'name' FROM users;
```

### Features:

* JSONB indexing (GIN)
* Full-text search
* Extensions:

  * PostGIS
  * pg_stat_statements

---

# ⚡ Performance Tuning (REAL-WORLD)

## 🔹 Key Parameters

* shared_buffers (~25% RAM)
* work_mem
* effective_cache_size

---

## 🔹 Techniques

* Connection pooling (PgBouncer)
* Caching (Redis)
* Avoid N+1 queries
* Use prepared statements

---

# 🔥 Handling Large Scale Systems

## 🔹 Strategies

* Read replicas
* Partitioning
* Sharding (application-level)
* Archiving old data

---

# 🔧 Connection Pooling

Tools:

* PgBouncer
* PgPool

👉 Prevents:

* Too many connections (process overhead)

---

# 🧪 Observability & Monitoring

* pg_stat_statements
* Slow query logs
* Auto explain

---

# 💾 Backup & Recovery (VERY IMPORTANT)

## 🔹 Types

* Logical backup → pg_dump
* Physical backup → base backup

---

## 🔹 Point-In-Time Recovery (PITR)

👉 Restore using WAL logs

---

# 🚨 Common Production Issues

| Issue                 | Solution           |
| --------------------- | ------------------ |
| Slow queries          | Index + tuning     |
| Deadlocks             | Order locks        |
| Bloat                 | VACUUM             |
| High CPU              | Query optimization |
| Connection exhaustion | Pooling            |

---

# 🎯 Senior-Level Interview Questions

## 1. Explain MVCC internally

👉 Versioning + snapshots → no read locks

---

## 2. How WAL works?

👉 Write log first → ensures durability

---

## 3. Why autovacuum is critical?

👉 Prevents table bloat

---

## 4. When index is not used?

👉 Functions, low selectivity, wildcards

---

## 5. How to scale PostgreSQL?

* Read replicas
* Partitioning
* Sharding
* Caching
