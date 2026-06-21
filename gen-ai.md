# 🚀 Generative AI

## Overview

GenAI is a system that generates human-like responses

### Core Components

* 📄 Document Processing
* ✂️ Chunking
* 🔍 Embeddings
* 🗂️ Vector Databases
* 🧠 Retrieval-Augmented Generation (RAG)
* ⚡ Agent Orchestration
* 💾 Memory Systems

---

# Part 1: Knowledge Ingestion Step

This stage prepares documents for semantic search by converting them into embeddings and storing them in a vector database.

## End-to-End Flow

```text
Documents ( PDF / DOCX / PPTX / XLSX )
    ↓
Document Processing
    ↓
Chunking
    ↓
Embedding Generation
    ↓
Vector Database Storage
```


## 1. Document Processing

### Definition

The process of collecting and reading enterprise documents before they are used by AI systems.

### Purpose

* Extract business knowledge data
* Prepare data for chunking and embeddings


## 📄 Common Document Type | Chunking Strategy | Purpose

| Document Type      | Chunking Strategy             | Purpose                                      |
| ------------------ | ----------------------------- | -------------------------------------------- |
| PDF                | Semantic / Recursive Chunking | Preserve sections and document hierarchy     |
| Word (.docx)       | Semantic Chunking             | Keep related content and procedures together |
| PowerPoint (.pptx) | Slide-Based Chunking          | Treat each slide as an independent chunk     |
| Excel (.xlsx)      | Table / Row Chunking          | Retrieve structured records efficiently      |

---

## 2. Chunking

### Definition

Chunking is the process of splitting large documents into smaller pieces before generating embeddings.

* Why Chunking? ===>> because LLMs cannot efficiently process very large documents directly.

---

## 3. Embeddings

### Definition

Embeddings convert text into numerical vectors that capture semantic meaning.

### Example

```text
"Pipeline corrosion issue"

↓

[0.34, -0.18, 0.92, ...]
```

### Purpose

Allows machines to understand meaning instead of exact keywords.

---

## Popular Embedding Models

| Model                         | Use                   |
| ----------------------------- | --------------------- |
| OpenAI text-embedding-3-large | High accuracy         |
| OpenAI text-embedding-3-small | Cost efficient        |
| BGE-large                     | Enterprise RAG        |
| E5 Models                     | Open-source retrieval |

---

## 4. Vector Database

### Definition

A database for storing and searching embeddings.

### Purpose

Retrieve semantically similar content.

### Popular Vector Databases

| Vector DB | Use |
|-----------|-----|
| PostgreSQL + pgvector | Vector search + relational database in one system |
| SQL Server + Vector Search | Vector search + enterprise relational database in one system |
| Pinecone | Fully managed vector database for production RAG |
| ChromaDB | Lightweight and developer-friendly for local projects |

---


# Part 2:  User Prompt ( Query ) Processing & Answer Generation Steps

This stage handles user questions and generates intelligent responses.

---

## End-to-End Flow

```text
User Query
    ↓
Query Understanding
    ↓
System Prompt
    ↓
Query Rewriting/building
    ↓
Query Embedding
    ↓
Vector Search
    ↓
Top-N Retrieval
    ↓
Context Building
    ↓
LLM ( Answer Generation )
    ↓
Final Response
```

---

## 1. User Query

### Definition

The question entered by the user.

### Example

```text
Explain the concept of machine learning.
```

---

## 2. Query Understanding

### Definition

Analyze user intent and extract key information.

### Purpose

Identify:

* User intent
* Entities
* Context
* Domain

### Example

```text
Explain the concept of machine learning.
```

Intent:

```text
Concept Explanation
```

Entity:

```text
Machine Learning
```

Context:

```text
Learning
```

Domain:

```text
Artificial Intelligence
```

---

## 3. System Prompt

### Definition

Instructions that guide how the AI should behave and respond.

### Purpose

Ensures consistent, accurate, and safe responses.

### Example

```text
You are an AI tutor.
Provide clear and beginner-friendly explanations.
Answer only using the retrieved context.
```

---

## 4. Query Rewriting / Query Building

### Definition

Convert the user query into a search-friendly query.

### Purpose

Improve retrieval accuracy.

### Example

User Query:

```text
Teach me about ML.
```

Rewritten Query:

```text
Explain the fundamentals of machine learning.
```

---

## 5. Query Embedding

### Definition

Convert the query into a vector representation.

### Purpose

Enable semantic search.

### Example

```text
Explain the fundamentals of machine learning.
```

↓

```text
[0.52, -0.11, 0.78, ...]
```

## 6. Vector Search

### Definition

Search vector database for similar embeddings.

### Purpose

Find relevant knowledge.

### Example

Retrieve:

```text
Machine Learning Basics
Supervised Learning
Algorithms and Examples
```

---

## 7. Top-N Retrieval

### Definition

Select the most relevant chunks.

### Purpose

Reduce noise and improve answer quality.

### Example

```text
Top 5 Chunks
```

or

```text
Top 10 Chunks
```

based on similarity score.

---

## 8. Context Building

### Definition

Combine retrieved information and conversation context for the LLM.

### Purpose

Provide relevant context for answer generation.

### Example

```text id="4dchiy"
Retrieved Chunk 1
Retrieved Chunk 2
Retrieved Chunk 3

+

Previous Chat History

↓

system instructions.
```

---

## 9. Answer Generation

### Definition

The LLM uses the query, instructions, and context to generate an answer.

### Flow

```text id="w9q89d"
LLM
 ↓
Final Response
```

---

## 10. Final Response

### Definition

The final answer returned to the user.

### May Include

* Sources
* References
* Follow-up Suggestions

---
