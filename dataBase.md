# 🐘 PostgreSQL

---

# 🎯 Mindset

👉 Think like:

* Performance
* Consistency
* Scalability
* Trade-offs

---

# 🧠 1. Data Modeling

* Start **normalized**, denormalize for performance
* Avoid heavy joins in high-traffic systems

💬 Say:

> “Schema design depends on query patterns.”

---

# 🚀 2. Query Optimization

```sql
EXPLAIN ANALYZE SELECT * FROM users WHERE email = 'x';
```

✔ Avoid Seq Scan
✔ Use indexes
✔ Use pagination

💬 Say:

> “I analyze query plan and optimize with indexing or query rewrite.”

---

# 🔥 3. Indexing

* B-Tree → default
* GIN → JSONB
* Composite → multi-column queries

```sql
CREATE INDEX idx_user_created ON users(user_id, created_at);
```

💬 Say:

> “Indexes are based on access patterns, not blindly added.”

---

# 🔄 4. Transactions

* Use for critical operations (payments, orders)

```sql
BEGIN; ... COMMIT;
```

💬 Say:

> “Transactions ensure atomicity and consistency.”

---

# ⚙️ 5. Concurrency (MVCC)

* Reads don’t block writes
* Snapshot-based

💬 Say:

> “PostgreSQL uses MVCC for high concurrency.”

---

# 🔐 6. Locking

```sql
SELECT * FROM orders FOR UPDATE;
```

✔ Prevent race conditions

💬 Say:

> “Row-level locking avoids concurrent conflicts.”

---

# 🚨 7. Deadlocks

✔ Caused by circular waits
✔ Fix:

* Same lock order
* Short transactions

---

# 📦 8. Scaling

* Read replicas → scale reads
* Partitioning → large data
* Sharding → very large scale

💬 Say:

> “I scale reads via replicas and large datasets via partitioning.”

---

# 📊 9. Large Data Handling

```sql
PARTITION BY RANGE (created_at);
```

✔ Archive old data
✔ Avoid full scans

---

# ⚡ 10. Performance

✔ Indexing
✔ Redis caching
✔ Avoid N+1 queries

---

# 🔧 11. Connection Pooling

* Use PgBouncer

💬 Say:

> “Pooling prevents connection overhead in Node.js apps.”

---

# 💾 12. Backup

* pg_dump
* WAL → PITR

