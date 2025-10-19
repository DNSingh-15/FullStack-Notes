# 🟨 JavaScript Notes

js is an object-oriented programming language that is having a lot of applications. 

---

## 🚀 Advantages of JavaScript
- Less server interaction  
- Immediate feedback  
- Richer user interfaces  
- High performance  
- Cross-platform compatibility  

---

It can be used for both client-side as well as server-side

## 🧩 1. Data Types

### 🟢 a. Primitive Data Types
Primitive data types are **immutable** and store **single values**.  
They **do not have methods** and are **copied by value**.

**Examples:**  
`string`, `number`, `boolean`, `null`, `undefined`, `bigint`, `symbol`

### 🟢 b. Non-Primitive Data Types
Non-primitive types are **mutable** and store **multiple values**.  
They are **copied by reference**.

**Examples:**  
`object`, `array`, `function`

---


## 🔠 2. String Methods
Commonly used string manipulation methods:
  * str.toUpperCase( )
  * str.toLowerCase( )
  * str.trim( ) // removes whitespaces
  * str.slice(start, end?) // returns part of string
  * str1.concat( str2 ) // joins str2 with str1
  * str.replace( searchVal, newVal )
  * str.charAt( idx )


---

## 🧮 3. Array Methods
| Method | Description |
|--------|--------------|
| `push()` | Add to end |
| `pop()` | Remove from end |
| `unshift()` | Add to start |
| `shift()` | Remove from start |
| `toString()` | Converts array to string |
| `concat()` | Joins multiple arrays |
| `slice(start, end)` | Returns a shallow copy |
| `splice(start, deleteCount, ...items)` | Modifies array by adding/removing elements |

### 🔹 Higher-Order Methods
```js
// map
let doubled = arr.map(val => val * 2);

// filter
let evens = arr.filter(val => val % 2 === 0);

// reduce
let sum = arr.reduce((acc, val) => acc + val, 0);

// forEach
arr.forEach(val => console.log(val));
```

---



## ⚙️ 4. Functions
A function is a block of reusable code that performs a specific task.

```js
// Function Declaration
function greet() {
  console.log("Hello");
}

// Arrow Function
const greet = () => console.log("Hello");
```

### 🔸 Callback Function
A **callback** is a function passed into another function to be executed later.

```js
function fetchData(callback) {
  setTimeout(() => {
    callback("Data received");
  }, 1000);
}
```

---

## 🧠 5. Important JavaScript Concepts

### 🔹 var, let, const
| Keyword | Reassign | Redeclare | Scope |
|----------|-----------|------------|--------|
| var | ✅ | ✅ | Function |
| let | ✅ | ❌ | Block |
| const | ❌ | ❌ | Block |

---

### 🔹 == vs ===
```js
==   // compares only value
===  // compares value + type
```

---

### 🔹 Hoisting
Hoisting is JavaScript's behavior of moving **declarations to the top** of their scope.
```js
console.log(x); // undefined
var x = 10;
```
> Only declarations are hoisted, not initializations.

---

### 🔹 Closures
closure is a function where an ***inner function*** has access to the ***outer function's*** variables and arguments, even after the outer function has executed.

```js
function greeting() {
  let message = 'Hi';
  return function sayHi() {
    console.log(message);
  };
}
const hi = greeting();
hi(); // Hi
```

---

### 🔹 Prototype
Every JavaScript object has a hidden property called **[[Prototype]]**, which points to another object — the **prototype**.

It enables **inheritance** and **method sharing**.

```js
function Person(name) {
  this.name = name;
}
Person.prototype.sayHi = function() {
  console.log(`Hi, I'm ${this.name}`);
};

const user = new Person('John');
user.sayHi(); // Hi, I'm John
```

---

### 🔹 Currying
**Currying** transforms a function with multiple arguments into a sequence of functions, each taking one argument.

```js
function add(a) {
  return function(b) {
    return function(c) {
      return a + b + c;
    };
  };
}

console.log(add(1)(2)(3)); // 6
```

---

### 🔹 Callback, Promise & Async/Await

#### ✅ Callback
Old way to handle async operations.
```js
setTimeout(() => console.log("Task done"), 1000);
```

#### ✅ Promise
More elegant way to handle async logic.
```js
const promise = new Promise((resolve, reject) => {
  resolve("Success");
});
promise.then(console.log).catch(console.error);
```

#### ✅ Async/Await
Cleaner syntax built on Promises.
```js
async function getData() {
  const res = await fetch("url");
  console.log(await res.json());
}
```

---

### 🔹 Callback Hell
Nested callbacks cause unreadable code.
Avoid using **Promises** or **Async/Await** instead.

---

### 🔹 Generator Function
Functions that can be **paused and resumed** using the `yield` keyword.
```js
function* generator() {
  yield 1;
  yield 2;
  yield 3;
}
for (let val of generator()) console.log(val);
```

---

### 🔹 Event Loop
The **Event Loop** allows JavaScript to perform **asynchronous operations** — by managing the **call stack** and **callback queue**.

---

### 🔹 Execution Context
When JavaScript code runs, an **Execution Context** is created which contains:
1. **Variable Environment**
2. **Scope Chain**
3. **This Binding**

---

### 🔹 Event Delegation
Instead of attaching event listeners to multiple elements, we attach it to a **parent element** and use **event bubbling** to catch events.

```js
document.getElementById("list").addEventListener("click", (e) => {
  if (e.target.tagName === "LI") console.log("Item clicked");
});
```

---

## 💾 6. Storage & Cookies

### 🍪 Cookies
Small pieces of user data stored in the browser.
```js
document.cookie = "username=John Doe";
```

### 🗂️ Local Storage
Persistent storage in the browser (no expiration).
```js
localStorage.setItem("name", "John");
```

### 📁 Session Storage
Temporary storage, cleared when browser closes.
```js
sessionStorage.setItem("token", "abc123");
```

--- 

## 🔒 7. Strict Mode
Enables stricter parsing and error handling.

```js
"use strict";
x = 10; // ❌ Error (variable not declared)
```

---

## 📤 8. Copy Types

- **Shallow Copy:** Copies only top-level properties.
- **Deep Copy:** Copies nested objects too.
```js
const obj = { a: 1, b: { c: 2 } };

// Shallow Copy
const shallow = { ...obj };
shallow.b.c = 100; // affects original

// Deep Copy
const deep = structuredClone(obj);
deep.b.c = 200; // independent
```

---


## 🆕 9. ES6 Features
1. `let` and `const`  
2. Arrow Functions  
3. Template Literals  
4. Default Parameters  
5. Destructuring  
6. Spread & Rest Operators  
7. Classes  
8. Promises  
9. Modules (`import` / `export`)  
10. Map & Set objects  

---


---

### 10. Debouncing & Throttling

- **Debouncing:** Ensures a function runs **only after a delay** since the last event call.
- **Throttling:** Limits how often a function can be executed in a given time.

```js
function debounce(fn, delay) {
  let timeout;
  return (...args) => {
    clearTimeout(timeout);
    timeout = setTimeout(() => fn(...args), delay);
  };
}
```
```js
function throttle(fn, limit) {
  let lastCall = 0;
  return (...args) => {
    const now = Date.now();
    if (now - lastCall >= limit) {
      lastCall = now;
      fn(...args);
    }
  };
}
```

---

### 11. Higher-Order Functions
Functions that **take other functions as arguments or return functions**.

```js
function higherOrder(fn) {
  fn();
}
```

---

### 12. Composition vs Inheritance
- **Composition:** Combining simple functions or objects to build complex ones.
- **Inheritance:** Acquiring properties/methods from another object.