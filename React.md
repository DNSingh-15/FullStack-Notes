# React Notes

## ⚛️ What is React?
React is a **JavaScript library** for building dynamic user interfaces.  
It follows a **unidirectional data flow** — data moves from parent → child components.

---

## 🧱 Components
Components are **reusable UI blocks**.
### Types
- **Functional Components** → Modern, with hooks.
- **Class Components** → Legacy, uses lifecycle methods.

---

## 📦 Props
Props are **inputs** passed from parent to child.  
They are **immutable** (cannot be changed inside the component).

```tsx
function Greeting({ name }) {
  return <h1>Hello {name}</h1>;
}
```

---

## 🧠 Hooks

hooks are life cycle methods in functional component

### 🔹 useState
Stores and updates local state.
```tsx
const [count, setCount] = useState(0);
setCount(count + 1);
```

### 🔹 useEffect
* UseEffect is a hook it's just like a function it runs on any render.
* Handles side effects like API calls, DOM updates.

```tsx
useEffect(() => {
  console.log("Component mounted");
}, []); // runs once
```

### 🔹 useRef
* UseRef is a hook it allows to continue values between renders. ( alternative useState is not working then we have to go with useRef )
* Used for **DOM manipulation** or storing mutable values.

```tsx
const inputRef = useRef();
useEffect(() => inputRef.current.focus(), []);
```

### 🔹 useContext
Share global data without prop drilling.
```tsx
const ThemeContext = createContext("dark");
const theme = useContext(ThemeContext);
```

### 🔹 useMemo & useCallback
these are hooks and Used for **performance optimization**.
* useMemo Hook returns a memoized value.
* useCallback Hook returns a memoized funtion.
```tsx
const memoValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
const handleClick = useCallback(() => setCount(c => c + 1), []);
```

---

## 🔁 Prop Drilling
Passing data through multiple nested components.  
✅ Avoid it using **Context API** or **Redux**.

---

## 🧩 Virtualization

**Virtualization** is a performance optimization technique that **renders only the visible portion** of a large list instead of loading the entire list.

> 🧠 Ideal when rendering hundreds or thousands of elements — helps reduce memory usage and improves scroll performance.

---

### ⚙️ Popular Libraries
1. **react-window** 🪟  
2. **react-virtualized** ⚡

---

### 💻 Example (Using `react-window`)
```tsx
import { FixedSizeList as List } from "react-window";

<List
  height={300}
  itemCount={1000}
  itemSize={35}
  width={300}
>
  {Row}
</List>
```

---

## 🌿 Virtual DOM vs Real DOM

| Virtual DOM | Real DOM |
|--------------|-----------|
| Lightweight copy of DOM | Actual DOM |
| Fast updates | Slow updates |
| No direct manipulation | Can manipulate HTML |

---

## 🧾 JSX
JSX allows you to write **HTML inside JavaScript**.  
Browsers don’t understand JSX — it’s compiled by Babel to JS.

---

## 🚀 Why React?
- Fast (Virtual DOM)
- Easy to learn & test
- Huge community
- Component reusability
- Can integrate with Next.js for SSR

---

## ⚡ Events
React uses **synthetic events** (cross-browser wrappers).  
Example: `onClick`, `onChange`, `onSubmit`.

---

## 📊 Stateful vs Stateless Components

| Type | Description |
|-------|--------------|
| Stateful | Has internal state (uses useState) |
| Stateless | Only depends on props |

---

## ⚙️ Performance Optimization

- Use **React.memo()**
- Split code using **lazy() + Suspense**
- Use **useMemo / useCallback**
- Avoid unnecessary re-renders
- Virtualize long lists (e.g., react-window)

---

## 🧠 Controlled vs Uncontrolled Components

| Type | Description |
|-------|--------------|
| Controlled | React manages the input state |
| Uncontrolled | DOM manages the input value |

---

## 🧷 Refs
Used to directly access or modify DOM elements.

```tsx
const inputRef = useRef();
<input ref={inputRef} />
```

---

## 🧩 React Fragment
Used to group multiple elements without adding extra DOM nodes.

```tsx
<>
  <ChildA />
  <ChildB />
</>
```
