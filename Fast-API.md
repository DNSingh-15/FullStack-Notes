# ⚡ FastAPI Quick Notes

---

## 🚀 What is FastAPI?

FastAPI is a **modern, high-performance Python web framework** for building APIs.

👉 Built on:

* **Starlette** (web handling)
* **Pydantic** (data validation)

👉 Supports **async/await** natively

---

## ⚡ Why FastAPI?

* Very fast (comparable to Node.js & Go)
* Automatic validation
* Auto API docs (Swagger & ReDoc)
* Type hints support
* Easy to learn

---

## ⚙️ Basic Example

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello FastAPI"}
```

---

## 🔁 Path & Query Parameters

```python
@app.get("/users/{id}")
def get_user(id: int):
    return {"id": id}

@app.get("/items/")
def get_items(skip: int = 0):
    return {"skip": skip}
```

---

## 📦 Request Body (Pydantic)

```python
from pydantic import BaseModel

class User(BaseModel):
    name: str
    age: int

@app.post("/users/")
def create_user(user: User):
    return user
```

👉 Automatic validation

---

## 🔐 Validation (Important)

* Type checking
* Required fields
* Custom validation

```python
from pydantic import Field

class User(BaseModel):
    age: int = Field(gt=0)
```

---

## 🔁 Dependency Injection

👉 Reusable logic (like middleware)

```python
from fastapi import Depends

def get_db():
    return "db_connection"

@app.get("/")
def read(db=Depends(get_db)):
    return {"db": db}
```

---

## ⚡ Async vs Sync

```python
@app.get("/sync")
def sync_fn():
    return {"msg": "sync"}

@app.get("/async")
async def async_fn():
    return {"msg": "async"}
```

👉 Use **async** for I/O operations

---

## 🧠 Middleware

```python
@app.middleware("http")
async def log_requests(request, call_next):
    response = await call_next(request)
    return response
```

👉 Runs before & after request

---

## ⚠️ Exception Handling

```python
from fastapi import HTTPException

@app.get("/error")
def error():
    raise HTTPException(status_code=404, detail="Not found")
```

---

## 🔐 Authentication (JWT)

```python
from jose import jwt

token = jwt.encode({"user_id": 1}, "secret", algorithm="HS256")
```

---

## 🔐 Security

* OAuth2
* JWT
* Password hashing (bcrypt)

---

## 🧠 Database Integration

👉 Use ORMs like:

* SQLAlchemy
* Tortoise ORM

```python
# Example (concept)
db.query(User).all()
```

---

## 🔄 Background Tasks

```python
from fastapi import BackgroundTasks

def send_email():
    print("Email sent")

@app.get("/")
def main(bg: BackgroundTasks):
    bg.add_task(send_email)
    return {"msg": "Task running"}
```

👉 Runs tasks after response

---

## ⚡ Caching

* Redis
* In-memory cache

👉 Improves performance

---

## 📊 API Docs (Auto Generated)

* Swagger UI → `/docs`
* ReDoc → `/redoc`

---

## 🧪 Testing

```python
from fastapi.testclient import TestClient

client = TestClient(app)

def test_root():
    response = client.get("/")
    assert response.status_code == 200
```

---

## 🌐 Environment Variables

```python
import os

PORT = os.getenv("PORT")
```

---

## 🔥 API Best Practices

* Use proper status codes
* Validate input
* Use response models
* Handle errors properly
* Version APIs (`/v1`)

---

## 🚀 Deployment

* Uvicorn / Gunicorn
* Docker
* Nginx

```bash
uvicorn main:app --reload
```

---

## ⚡ Performance Tips

* Use async functions
* Use caching (Redis)
* Use connection pooling
* Avoid blocking code

---

## 🔥 Microservices

👉 Build small independent services

---

## ✅ Summary

| Concept         | Description                    |
| --------------- | ------------------------------ |
| FastAPI         | High-performance API framework |
| Async           | Non-blocking execution         |
| Pydantic        | Data validation                |
| Depends         | Dependency injection           |
| JWT             | Authentication                 |
| BackgroundTasks | Async jobs                     |


