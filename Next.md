# ⚡ Next.js Notes

## 🚀 What is Next.js?
Next.js is a **React framework** for building **fast, SEO-friendly, and production-ready** web applications.  


---

## ⚙️ Key Features
- **SSR (Server-Side Rendering)** → Render pages on server for SEO & speed  
- **SSG (Static Site Generation)** → Pre-build pages at build time  
- **ISR (Incremental Static Regeneration)** → Auto-updates static pages after deployment  
- **API Routes** → Create backend endpoints easily  
- **Image Optimization** → `next/image` auto-optimizes images  
- **File-based Routing** → Each file in `/pages` = route

---

## 🧱 Rendering Types

| Type | When It Runs | Example |
|------|---------------|----------|
| **CSR** | On browser | `useEffect` |
| **SSR** | On request | `getServerSideProps` |
| **SSG** | At build time | `getStaticProps` |
| **ISR** | After deploy | `revalidate` option |

---

## 🧩 Data Fetching

### 🔹 `getStaticProps()` (SSG)
```tsx
export async function getStaticProps() {
  const res = await fetch("https://api.example.com/posts");
  const posts = await res.json();
  return { props: { posts } };
}
```

### 🔹 `getServerSideProps()` (SSR)
```tsx
export async function getServerSideProps() {
  const res = await fetch("https://api.example.com/data");
  const data = await res.json();
  return { props: { data } };
}
```

### 🔹 `getStaticPaths()` (Dynamic SSG)
```tsx
export async function getStaticPaths() {
  const res = await fetch("https://api.example.com/posts");
  const posts = await res.json();
  const paths = posts.map(p => ({ params: { id: p.id.toString() } }));
  return { paths, fallback: false };
}
```

---

## 🧠 Routing
- Auto routing from `pages/`  
- Dynamic routes: `[id].js` → `/post/1`  
- Catch-all: `[...params].js`  
- Nested routes supported  

**Navigation Example**
```tsx
import Link from "next/link";
<Link href="/about">About</Link>
```

**Programmatic Navigation**
```tsx
import { useRouter } from "next/router";
const router = useRouter();
router.push("/dashboard");
```

---

## 🧰 API Routes
```tsx
export default function handler(req, res) {
  res.status(200).json({ message: "Hello from Next.js API" });
}
```

---

## ⚡ Image Optimization
```tsx
import Image from "next/image";
<Image src="/hero.png" alt="Hero" width={500} height={300} />
```
✅ Auto-optimized, lazy-loaded, modern format support.

---

## 🧩 Middleware (Next 12+)
```tsx
// middleware.ts
import { NextResponse } from "next/server";
export function middleware(req) {
  if (!req.cookies.token) return NextResponse.redirect("/login");
}
```

---

## 🔐 NextAuth.js

NextAuth.js is a complete authentication solution for **Next.js applications**, supporting **OAuth**, **Credentials**, and **Email** providers out of the box.

### ⚙️ How NextAuth Works

1. **User signs in** using credentials (or any provider).
2. NextAuth validates credentials and returns a **JWT** (JSON Web Token).
3. The JWT is stored in an **HTTP-only cookie**.
4. Every request to protected routes checks for this cookie to verify authentication.
5. The session can be accessed globally using the `useSession()` hook.

---

## ⚙️ Performance Tips
- Use `Image` and `Script` components  
- Lazy load with `next/dynamic`  
- Cache API responses  
- Use ISR for real-time updates  
- Analyze bundles using `next-bundle-analyzer`  

---

## 🔍 SEO Optimization
```tsx
import Head from "next/head";
<Head>
  <title>My Page</title>
  <meta name="description" content="SEO optimized page" />
</Head>
```

---

## 🧠 getServerSideProps vs getStaticProps

| Feature | getServerSideProps | getStaticProps |
|----------|--------------------|----------------|
| When | Every request | Build time |
| Freshness | Always updated | Static (can use ISR) |
| Use case | Dashboard, user data | Blogs, marketing pages |
