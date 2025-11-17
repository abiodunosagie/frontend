# 05 - React Basics

> **"React changes everything. Once you learn to think in components, you can't go back."**

Welcome to React - the library that revolutionized frontend development.

---

## 🎯 What is React?

**Simple explanation:** React lets you build websites using **reusable components** instead of writing the same HTML over and over.

### Without React:
```html
<!-- Page 1 -->
<nav>
  <a href="/">Home</a>
  <a href="/about">About</a>
</nav>

<!-- Page 2 (copy-paste the same nav) -->
<nav>
  <a href="/">Home</a>
  <a href="/about">About</a>
</nav>

<!-- Page 3 (copy-paste AGAIN) -->
<nav>
  <a href="/">Home</a>
  <a href="/about">About</a>
</nav>
```

**Problem:** If you need to change the nav, you have to change it everywhere.

### With React:
```javascript
// Navigation.js (write once)
function Navigation() {
  return (
    <nav>
      <a href="/">Home</a>
      <a href="/about">About</a>
    </nav>
  );
}

// Use it everywhere
<Navigation />
<Navigation />
<Navigation />
```

**Change the component once, it updates everywhere!** 🎉

---

## 📚 Lessons

1. **[What is React?](./lessons/01-what-is-react.md)** - The big picture
2. **[JSX](./lessons/02-jsx.md)** - HTML in JavaScript
3. **[Components](./lessons/03-components.md)** - Building blocks
4. **[Props](./lessons/04-props.md)** - Passing data to components
5. **[State](./lessons/05-state.md)** - Making components interactive
6. **[Events](./lessons/06-events.md)** - Handling clicks, inputs, etc.
7. **[Conditional Rendering](./lessons/07-conditional-rendering.md)** - Show/hide elements
8. **[Lists](./lessons/08-lists.md)** - Rendering arrays
9. **[Forms](./lessons/09-forms.md)** - Handling user input
10. **[useEffect](./lessons/10-useEffect.md)** - Side effects and lifecycle

---

## 🎯 Your First React Component

```javascript
function Greeting() {
  return <h1>Hello, World!</h1>;
}
```

**That's it.** A function that returns JSX (HTML-like syntax).

---

## 🎨 Props (Passing Data)

```javascript
function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}

// Usage
<Greeting name="Alice" />  // Hello, Alice!
<Greeting name="Bob" />    // Hello, Bob!
```

**Props make components reusable with different data.**

---

## 🔥 State (Making Components Interactive)

```javascript
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>
    </div>
  );
}
```

**Click the button → count updates → UI re-renders automatically!**

This is the magic of React.

---

## 🎯 Projects You'll Build

1. **Todo List** - Add, complete, delete tasks
2. **Counter App** - Increment, decrement, reset
3. **Form Handler** - Controlled inputs
4. **Card Component** - Reusable UI element
5. **Product List** - Display and filter products

---

**React is your gateway to modern frontend development. Let's master it.** ⚛️
