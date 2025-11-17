# 09 - Next.js Fundamentals

> **"Next.js is React on steroids. It's what professionals use to build production applications."**

You've learned React. Now it's time to learn **Next.js** - the framework that takes React to the next level.

---

## 🎯 What is Next.js?

**Next.js is a React framework** that adds:
- **File-based routing** (no need for React Router)
- **Server-side rendering** (faster page loads, better SEO)
- **API routes** (build backend endpoints in the same project)
- **Image optimization** (automatic image optimization)
- **Built-in CSS support** (and Tailwind!)
- **Production optimizations** (out of the box)

**React = Library** (just UI)
**Next.js = Framework** (full application solution)

---

## 📚 What You'll Learn

### Week 1: Basics
1. **[What is Next.js?](./lessons/01-what-is-nextjs.md)**
2. **[File-based Routing](./lessons/02-routing.md)** - Pages from folders
3. **[Layouts](./lessons/03-layouts.md)** - Shared UI
4. **[Navigation](./lessons/04-navigation.md)** - Link component
5. **[Dynamic Routes](./lessons/05-dynamic-routes.md)** - `[id]` pages

### Week 2: Data Fetching
6. **[Server Components](./lessons/06-server-components.md)** - Fetch on server
7. **[Client Components](./lessons/07-client-components.md)** - 'use client'
8. **[Data Fetching Patterns](./lessons/08-data-fetching.md)**
9. **[Loading & Error States](./lessons/09-loading-error.md)**
10. **[Metadata & SEO](./lessons/10-metadata.md)**

### Week 3: Advanced
11. **[API Routes](./lessons/11-api-routes.md)** - Build your own APIs
12. **[Server Actions](./lessons/12-server-actions.md)** - Modern data mutations
13. **[Middleware](./lessons/13-middleware.md)** - Request interception
14. **[Deployment](./lessons/14-deployment.md)** - Deploy to Vercel

---

## 🎯 File-Based Routing (Game Changer)

### In React Router:
```javascript
// You manually define routes
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/about" element={<About />} />
  <Route path="/blog/:id" element={<BlogPost />} />
</Routes>
```

### In Next.js:
```
app/
  page.js          → /
  about/
    page.js        → /about
  blog/
    [id]/
      page.js      → /blog/123
```

**Folders = URLs!** So much simpler.

---

## 🔥 Server vs Client Components

### Server Components (Default)
```javascript
// app/users/page.js
async function getUsers() {
  const res = await fetch('https://api.example.com/users');
  return res.json();
}

export default async function UsersPage() {
  const users = await getUsers();

  return (
    <div>
      {users.map(user => <div key={user.id}>{user.name}</div>)}
    </div>
  );
}
```

**Benefits:**
- Fetches on server (faster initial load)
- SEO-friendly
- No loading spinner needed

### Client Components (When You Need Interactivity)
```javascript
'use client';  // Add this at the top

import { useState } from 'react';

export default function Counter() {
  const [count, setCount] = useState(0);

  return (
    <button onClick={() => setCount(count + 1)}>
      Count: {count}
    </button>
  );
}
```

**Use client components when you need:**
- useState, useEffect, hooks
- Event handlers (onClick, onChange)
- Browser APIs (window, localStorage)

---

## 🎨 Your First Next.js App

### Create a new Next.js app:
```bash
npx create-next-app@latest my-app
cd my-app
npm run dev
```

Open http://localhost:3000 🎉

---

## 🚀 Projects You'll Build

1. **Personal Portfolio** - Multi-page site with routing
2. **Blog** - Dynamic routes, markdown posts
3. **Product Catalog** - Server-side rendering
4. **Dashboard** - API routes, data fetching
5. **Full-stack App** - Frontend + backend in one project

---

**Next.js is how professionals build React apps. This is your upgrade.** ⚡
