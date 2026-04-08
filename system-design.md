# 🏗️ System Design 

# 🧠 1. What is System Design?

👉 Designing systems that are:

* Scalable
* Reliable
* Performant
* Fault-tolerant

> “System design is about handling real-world scale and failures.”


---

# 🎯 2. SOLID Principles

👉 Interviewers LOVE this for LLD

| Principle                     | Meaning                                     |
| ----------------------------- | ------------------------------------------- |
| **S** — Single Responsibility | One class = one responsibility              |
| **O** — Open/Closed           | Open for extension, closed for modification |
| **L** — Liskov Substitution   | Child should replace parent safely          |
| **I** — Interface Segregation | Small, specific interfaces                  |
| **D** — Dependency Inversion  | Depend on abstractions, not concrete        |


> “follow SOLID to ensure maintainable and scalable low-level design.”

---


# 🏗️ 3. HLD vs LLD

| Type | Focus                           |
| ---- | ------------------------------- |
| HLD  | Architecture, services, scaling |
| LLD  | Classes, DB schema, APIs        |

💬 Tip:

* Start with **HLD → then go deeper if asked**

---

# 🧩 4. Core Architecture (ALWAYS USE THIS FLOW)

```text
Client → CDN → API Gateway → Load Balancer → App Servers
                                      ↓
                                Cache (Redis)
                                      ↓
                                Database
                                      ↓
                                  Queue
```

---

# ⚡ 5. Scalability

## 🔹 Horizontal Scaling (Preferred)

* Add more servers
* Use Load Balancer

## 🔹 Vertical Scaling

* Increase CPU/RAM (limited)

💬 Say:

> “I prefer horizontal scaling for high availability.”

---

# 🧊 6. Caching Strategy

Levels:

1. CDN
2. API cache
3. DB cache (Redis)

💬 Say:

> “Caching reduces DB load and improves latency.”

---

# 🔄 7. Load Balancing

* Round Robin
* Least Connections

💬 Say:

> “Load balancer distributes traffic and prevents overload.”

---

# 🗄️ 8. Database Design (CRITICAL)

## 🔹 SQL vs NoSQL

| SQL (Relational) | NoSQL |
|-----------------|-------|
| ACID            | Eventual Consistency |
| Structured      | Flexible schema |

---

### 🔹 ACID (SQL Transactions)

- **Atomicity** → All or nothing  
- **Consistency** → Data remains valid  
- **Isolation** → No interference between transactions  
- **Durability** → Data persists after commit  

💬 One-liner:
ACID ensures reliable and consistent database transactions.

---

## 🔹 Scaling DB

* Read replicas
* Partitioning
* Sharding

💬 Say:

> “I scale reads using replicas and large data using partitioning.”

---

# 📬 9. Messaging / Queue 

“Queues decouple services and handle asynchronous processing and traffic spikes.”

## 🔹 Example: Kafka

- **Producer** → Sends messages  
- **Consumer** → Reads messages  
- **Topic** → Category of messages  
- **Partition** → Splits topic for scalability  
> “Queues decouple services and handle spikes.”

---

# ⚖️ 10. CAP Theorem

| C           | A            | P                   |
| ----------- | ------------ | ------------------- |
| Consistency | Availability | Partition tolerance |

👉 Pick 2

💬 Say:

> “In distributed systems, trade-offs are unavoidable.”

---

# 🧯 11. Fault Tolerance

* Retry mechanism
* Circuit breaker
* Multi-AZ deployment

💬 Say:

> “System should handle failures gracefully.”

---

# 🔐 12. Security

* JWT / OAuth
* HTTPS
* Rate limiting
* IAM roles

💬 Say:

> “Security is critical, especially for sensitive systems.”

---

# 📊 13. Monitoring

* Logs
* Metrics
* Alerts

💬 Say:

> “Without monitoring, system reliability cannot be ensured.”

---

# 🚦 14. Rate Limiting

* Prevent abuse
* Protect backend

💬 Say:

> “Rate limiting protects system from overload.”

---

# 🚀 15. Deployment Strategies

* Blue-Green
* Rolling
* Canary

💬 Say:

> “I prefer zero-downtime deployment strategies.”

---

# 🧱 16. Microservices vs Monolith

| Monolith       | Microservices  |
| -------------- | -------------- |
| Simple         | Scalable       |
| Tight coupling | Loose coupling |

💬 Say:

> “Microservices improve scalability but add complexity.”

---

# 🧮 17. Capacity Estimation (MUST DO)

Example:

```text
10M requests/day ≈ 115 req/sec
```

💬 Say:

> “I always estimate scale before designing.”

---

# ⚡ 18. Performance Optimization

* Caching
* Indexing
* Async processing
* CDN

---

# 🧠 19. How to Answer in Interview (IMPORTANT)

👉 Always structure:

1. Requirements
2. High-Level Design
3. Scaling
4. Trade-offs
5. Bottlenecks

---

# 🎯 20. Common Questions

### Q: Design scalable system

👉 Load balancer + cache + DB scaling

### Q: Handle high traffic

👉 CDN + auto scaling + queue

### Q: Avoid DB bottleneck

👉 Cache + replicas

---

# 🏁 Final Golden Rule

👉 Don’t say:

* “Use Redis”

👉 Say:

* “Use Redis to reduce DB load and improve latency under high read traffic”

---

# 🚀 One-Line Summary

👉 **System design = scalability + reliability + trade-offs + real-world thinking**

---
