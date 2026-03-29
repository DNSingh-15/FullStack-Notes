# 🏗️ System Design Notes

---

## 📌 1. What is System Design?

System Design is the process of designing **scalable, reliable, maintainable systems** that can handle real-world production workloads.

👉 Focus areas:

* Scalability
* Availability
* Performance
* Fault tolerance
* Cost optimization

---

## 🧠 2. High-Level vs Low-Level Design

| Type                    | Description                            |
| ----------------------- | -------------------------------------- |
| HLD (High-Level Design) | Architecture, components, interactions |
| LLD (Low-Level Design)  | Classes, DB schema, APIs               |

---

## 🏛️ 3. Core System Design Components

### 🔹 Client Layer

* Web (React)
* Mobile apps

### 🔹 API Layer

* REST / GraphQL
* API Gateway (AWS API Gateway)

### 🔹 Service Layer

* Microservices (Node.js, Java, Python)
* Business logic

### 🔹 Data Layer

* SQL (PostgreSQL, MySQL)
* NoSQL (DynamoDB, MongoDB)

### 🔹 Cache Layer

* Redis (AWS ElastiCache)

### 🔹 Messaging Layer

* Kafka / AWS SQS / SNS

---

## ☁️ 4. AWS Core Services Mapping

| Layer         | AWS Service                |
| ------------- | -------------------------- |
| CDN           | CloudFront                 |
| DNS           | Route 53                   |
| Load Balancer | ALB / NLB                  |
| Compute       | EC2 / Lambda / ECS / EKS   |
| API Gateway   | API Gateway                |
| Storage       | S3                         |
| Database      | RDS (PostgreSQL), DynamoDB |
| Cache         | ElastiCache (Redis)        |
| Queue         | SQS                        |
| Pub/Sub       | SNS                        |
| Monitoring    | CloudWatch                 |
| Secrets       | Secrets Manager            |

---

## 🌍 5. Basic Scalable Architecture (Step-by-Step)

### 🧱 Flow:

```id="flow1"
User → CloudFront → API Gateway → Load Balancer → EC2 (App Servers)
                                    ↓
                                  Cache (Redis)
                                    ↓
                               Database (RDS)
```

---

## ⚡ 6. Scalability Concepts

### 🔹 Vertical Scaling

* Increase CPU/RAM
* Limited

### 🔹 Horizontal Scaling

* Add more servers
* Use Load Balancer

---

### 🔹 Auto Scaling (AWS)

* Automatically adds/removes instances
* Based on CPU, traffic

---

## 🧊 7. Caching Strategy

### Levels:

1. CDN (CloudFront)
2. API Cache
3. Database Cache (Redis)

```id="cache-flow"
Request → Cache hit → return data
       → Cache miss → DB → store in cache
```

---

## 🔄 8. Load Balancing

### Types:

* Round Robin
* Least Connections

👉 AWS:

* Application Load Balancer (ALB)
* Network Load Balancer (NLB)

---

## 🧵 9. Database Design

### 🔹 SQL vs NoSQL

| SQL        | NoSQL                 |
| ---------- | --------------------- |
| Structured | Flexible              |
| ACID       | Eventually consistent |
| PostgreSQL | DynamoDB              |

---

### 🔹 Scaling DB

* Read Replicas (RDS)
* Partitioning / Sharding
* Connection Pooling

---

## 🔁 10. CAP Theorem

| Property            | Meaning                      |
| ------------------- | ---------------------------- |
| Consistency         | Same data everywhere         |
| Availability        | Always responds              |
| Partition Tolerance | Works despite network issues |

👉 You can pick only 2

---

## 📬 11. Messaging & Queues

### Why?

* Decouple services
* Handle spikes

### AWS:

* SQS → Queue
* SNS → Pub/Sub

```id="queue-flow"
User → API → SQS → Worker → DB
```

---

## 🧯 12. Fault Tolerance & Reliability

* Multi-AZ deployment (RDS)
* Health checks
* Retry mechanisms
* Circuit breaker pattern

---

## 🔐 13. Security Best Practices

* IAM roles (least privilege)
* HTTPS everywhere
* JWT / OAuth
* WAF (Web Application Firewall)
* VPC (private subnet for DB)

---

## 📊 14. Monitoring & Logging

* CloudWatch (metrics, logs)
* ELK Stack (optional)
* Alerts on CPU, errors

---

## 🧪 15. Rate Limiting & Throttling

* Prevent abuse
* API Gateway throttling

---

## 📦 16. Deployment Strategies

* Blue-Green deployment
* Rolling updates
* Canary deployment

---

## 🧱 17. Microservices vs Monolith

| Monolith      | Microservices        |
| ------------- | -------------------- |
| Simple        | Scalable             |
| Hard to scale | Independent services |

---

## 🧠 18. Real System Design Example

### 🔥 Design: URL Shortener (like bit.ly)

### Requirements:

* Shorten URL
* Redirect fast
* High read traffic

---

### Architecture:

```id="url-short"
User → API Gateway → App Server → DB
                        ↓
                      Cache (Redis)
```

---

### Key Points:

* Use hash (Base62)
* Cache frequently accessed URLs
* Use read replicas

---

## 🧮 19. Capacity Estimation (Important)

### Example:

* 1M users/day
* 10 requests/user

👉 Total = 10M requests/day

👉 Per second:

```id="calc1"
10M / (24*60*60) ≈ 115 req/sec
```

---

## 🚀 20. Performance Optimization

* Use CDN
* Optimize queries
* Use indexes
* Async processing
* Compression (gzip)

---

## 🎯 21. Interview Questions (Senior)

### 1. How do you design a scalable system?

👉 Load balancing + caching + DB scaling

---

### 2. How do you handle high traffic?

👉 Auto scaling + CDN + queue

---

### 3. How to avoid DB bottleneck?

👉 Cache + read replicas + sharding

---

### 4. How do you design fault-tolerant systems?

👉 Multi-AZ + retries + circuit breaker

---

### 5. Difference between SQS and SNS?

* SQS → queue
* SNS → pub/sub

---

## 🏗️ 22. AWS Architecture Best Practices

* Stateless services
* Use managed services (RDS, S3)
* Avoid single point of failure
* Design for failure
* Cost optimization (spot instances)

---

## 🧠 23. One-Line Summary

👉 **System design is about building scalable, fault-tolerant, and efficient systems using proper architecture patterns and cloud services like AWS.**

