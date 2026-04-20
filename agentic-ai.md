# 🔗 Agentic-AI Notes

Generate + Action. = Agents that can -

- Understand goals
- Plan steps
- Make decisions
- Use tools (APIs, DB, code)
- Iterate until completion

👉 **Agentic AI = Goal → Plan → Act → Evaluate → Repeat**

---

# Example 
In Qmentis-AI, I worked specifically on the **Test Automation feature**, where I designed and implemented a **multi-agent AI system** to:

```text
┌──────────────────────────────┐
│        Client (React UI)     │
│  - User submits code / req   │
└───────────────┬──────────────┘
                ↓
┌──────────────────────────────┐
│     Backend API (Node.js)    │
│  - Validates input           │
│  - Sends request to AI flow  │
└───────────────┬──────────────┘
                ↓
┌──────────────────────────────┐
│   AWS Step Functions         │
│  - Manages workflow state    │
│  - Controls execution flow   │
└───────────────┬──────────────┘
                ↓
┌──────────────────────────────┐
│     AWS Lambda               │
│  - Invokes AI agent system   │
└───────────────┬──────────────┘
                ↓
┌──────────────────────────────────────────────┐
│     Agentic AI Engine (Python - LangGraph)   │
│                                              │
│   ┌──────────────────────────────────────┐   │
│   │     Orchestrator Agent              │   │
│   │  - Controls agent execution         │   │
│   └───────────────┬─────────────────────┘   │
│                   ↓                         │
│   ┌──────────────────────────────────────┐  │
│   │        Planner Agent                │  │
│   │  - Breaks task into steps           │  │
│   └───────────────┬─────────────────────┘  │
│                   ↓                         │
│   ┌───────────────┬───────────────┬───────────────┐
│   ↓               ↓               ↓               ↓
│ Pattern        Code           Code           Validator
│ Extractor      Analyzer       Generator       Agent
│ Agent          Agent          Agent           │
│   ↓               ↓               ↓           │
│   └───────────────┴───────────────┴───────────┘
│                   ↓
│        Aggregation / Refinement Layer
│                   ↓
│              Final Test Output
└───────────────┬──────────────────────────────┘
                ↓
┌──────────────────────────────┐
│        PostgreSQL            │
│  - Stores test cases         │
│  - Stores execution logs     │
└───────────────┬──────────────┘
                ↓
┌──────────────────────────────┐
│     Response to Client       │
│  - Generated test scripts    │
└──────────────────────────────┘
```

---

## 🧠 What is LangChain?

LangChain is a framework to **build LLM-powered applications** using:

* Prompts
* Chains
* Memory
* Tools

👉 Helps connect LLM with **data, APIs, and workflows**

---

### ⚡ One-line

👉 **LangChain = glue between LLM + data + logic**

---

## 🔧 Core Concepts (LangChain)

### 🔹 1. Prompt Templates

Reusable prompts with variables

```python
from langchain.prompts import PromptTemplate

template = PromptTemplate.from_template("Hello {name}")
```

---

### 🔹 2. Chains

Combine multiple steps together

```text
Input → Prompt → LLM → Output
```

👉 Sequential execution

---

### 🔹 3. Memory

Stores conversation history

* Buffer memory
* Summary memory

👉 Used in chat applications

---

### 🔹 4. Tools

External functions used by LLM

Examples:

* API calls
* DB queries
* Calculations

---

### 🔹 5. Agents (LangChain)

LLM decides:

* Which tool to use
* What action to take

👉 Dynamic execution

---

## ⚡ LangChain Flow

```text
User Input
   ↓
Prompt Template
   ↓
LLM
   ↓
Tool (if needed)
   ↓
Response
```

---

## 🚀 What is LangGraph?

LangGraph is used to build **stateful, multi-agent workflows**

👉 Advanced version of LangChain

---

### ⚡ One-line

👉 **LangGraph = workflow engine for agent systems**

---

## 🔄 Why LangGraph?

* Multi-agent orchestration
* State management
* Looping & branching
* Better control than chains

---

## 🧠 LangGraph vs LangChain

| Feature  | LangChain   | LangGraph            |
| -------- | ----------- | -------------------- |
| Type     | Linear flow | Graph-based          |
| Use case | Simple apps | Complex workflows    |
| Agents   | Basic       | Advanced multi-agent |
| State    | Limited     | Strong               |

---

## 🔄 LangGraph Flow Example

```text
User Input
   ↓
Planner Agent
   ↓
Executor Agent
   ↓
Tool Call
   ↓
Decision Node
   ↓
Loop / Next Step
   ↓
Final Output
```

---

## 🧩 When to Use

### Use LangChain

👉 Simple applications

* Chatbot
* Q&A system

---

### Use LangGraph

👉 Complex systems

* Multi-agent workflows
* Decision-based flows
* AI pipelines

---

## ⚡ Real Use Case

👉 Resume Analyzer (Agentic AI)

* Planner → decide steps
* Retriever → fetch data
* LLM → generate output
* Validator → guardrails

---

## ⚡ Quick Memory

👉 **LangChain = simple pipeline**
👉 **LangGraph = complex workflow**
👉 **Agents = decision makers**
👉 **Tools = external actions**

---

## 🎯 Interview Points

* LangChain → chaining LLM calls
* LangGraph → graph-based orchestration
* Agents → dynamic decision making
* Tools → external integrations