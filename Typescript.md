# TypeScript Notes (Simplified for 4–5 Years Experience)

## 🧠 Overview

TypeScript = **JavaScript + Static Typing + Better Tooling**  
It helps catch errors early, improves readability, and makes large-scale apps easier to maintain.

---

## ⚙️ Why TypeScript?

- Detects errors before runtime.  
- Provides IntelliSense and autocompletion.  
- Supports modern ES features.  
- Improves scalability and refactoring.  

---

## 🧩 Basic Types

| Type | Example |
|------|----------|
| `string` | `let name: string = "John";` |
| `number` | `let age: number = 25;` |
| `boolean` | `let isActive: boolean = true;` |
| `array` | `let nums: number[] = [1, 2, 3];` |
| `tuple` | `let user: [string, number] = ["John", 25];` |
| `enum` | `enum Direction {Up, Down}` |
| `any` | `let data: any = "anything";` |
| `void` | Used for functions returning nothing |

---

## 🧰 Functions

```ts
function add(a: number, b: number): number {
  return a + b;
}

const greet = (name: string = "Guest"): void => {
  console.log(`Hello, ${name}`);
};
```

---

## 🧱 Interfaces vs Types

### Interface
Used for **object structures** and class contracts.
```ts
interface User {
  id: number;
  name: string;
}
```

### Type Alias
Used for **custom, union, or intersection types**.
```ts
type ID = string | number;
type Status = "active" | "inactive";
```

### Difference Between Interface & Type

| Feature | Interface | Type Alias |
|----------|------------|-------------|
| Extension | Can extend other interfaces | Can combine using `&` |
| Declaration merging | ✅ Yes | ❌ No |
| Usage | Mostly for objects/classes | For any data type |

---

## 🧬 Generics

Used for reusable, type-safe code.

```ts
function identity<T>(value: T): T {
  return value;
}

let num = identity(10);
let str = identity("TS");
```

---

## 🧱 Classes & Access Modifiers

```ts
class Person {
  constructor(public name: string, private age: number) {}

  greet() {
    console.log(`Hi, I'm ${this.name}`);
  }
}
```

| Modifier | Meaning |
|-----------|----------|
| `public` | Accessible anywhere (default) |
| `private` | Accessible only within class |
| `protected` | Accessible in class & subclass |

---

## 🔁 Union & Intersection Types

```ts
let value: string | number;

interface A { a: number }
interface B { b: number }
type AB = A & B;
```

---

## 🧠 Utility Types

| Utility | Description |
|----------|--------------|
| `Partial<T>` | Makes all properties optional |
| `Pick<T, K>` | Picks specific properties |
| `Omit<T, K>` | Removes specific properties |
| `Readonly<T>` | Makes properties read-only |

```ts
interface User { id: number; name: string; email: string; }
type PartialUser = Partial<User>;
type NoEmail = Omit<User, "email">;
```

---

## ⚙️ Type Assertion

```ts
let val: any = "Hello";
let len = (val as string).length;
```

---

## 🔒 Abstract Class & Inheritance

```ts
abstract class Animal {
  abstract sound(): void;
}

class Dog extends Animal {
  sound() {
    console.log("Woof!");
  }
}
```

---

## 🧠 Generics with Interfaces

```ts
interface Box<T> {
  content: T;
}
const box: Box<string> = { content: "Books" };
```

---

## ⚡ Type Narrowing

```ts
function printId(id: string | number) {
  if (typeof id === "string") console.log(id.toUpperCase());
  else console.log(id);
}
```

---

## 💬 Common Interview Topics

- Difference between **TypeScript & JavaScript**
- **Interface vs Type Alias**
- **Generics** and why they are used
- **Access Modifiers** (`public`, `private`, `protected`)
- **Union & Intersection** types
- **Utility Types**
- **Type Narrowing** and **Type Assertion**
- **Abstract Classes** and inheritance
- **Advantages of TypeScript**

---

