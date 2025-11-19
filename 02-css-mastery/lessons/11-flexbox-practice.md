# CSS Lesson 11 - Flexbox Practice

> **"Learn by building. Here are real-world Flexbox patterns."**

---

## 🎯 Pattern 1: Navigation Bar

```html
<style>
  nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 2rem;
    background: #333;
    color: white;
  }

  .nav-links {
    display: flex;
    gap: 2rem;
    list-style: none;
  }
</style>

<nav>
  <div class="logo">MyBrand</div>
  <ul class="nav-links">
    <li><a href="#">Home</a></li>
    <li><a href="#">About</a></li>
    <li><a href="#">Contact</a></li>
  </ul>
</nav>
```

---

## 🎯 Pattern 2: Card Grid

```html
<style>
  .card-container {
    display: flex;
    flex-wrap: wrap;
    gap: 1.5rem;
  }

  .card {
    flex: 1 1 300px; /* Grow, shrink, base-width */
    background: white;
    padding: 1.5rem;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  }
</style>

<div class="card-container">
  <div class="card">Card 1</div>
  <div class="card">Card 2</div>
  <div class="card">Card 3</div>
</div>
```

---

## 🎯 Pattern 3: Sidebar Layout

```html
<style>
  .layout {
    display: flex;
    min-height: 100vh;
  }

  .sidebar {
    flex: 0 0 250px; /* Don't grow, don't shrink, 250px width */
    background: #f4f4f4;
    padding: 2rem;
  }

  .main {
    flex: 1; /* Take remaining space */
    padding: 2rem;
  }
</style>

<div class="layout">
  <aside class="sidebar">Sidebar</aside>
  <main class="main">Main Content</main>
</div>
```

---

## 🎯 Pattern 4: Perfect Centering

```html
<style>
  .center-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }

  .box {
    padding: 2rem;
    background: lightblue;
  }
</style>

<div class="center-container">
  <div class="box">Perfectly Centered!</div>
</div>
```

---

## 🎯 Pattern 5: Holy Grail Layout

```html
<style>
  body {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    margin: 0;
  }

  header, footer {
    background: #333;
    color: white;
    padding: 1rem;
  }

  .content {
    display: flex;
    flex: 1;
  }

  .sidebar-left, .sidebar-right {
    flex: 0 0 200px;
    background: #f4f4f4;
    padding: 1rem;
  }

  main {
    flex: 1;
    padding: 1rem;
  }
</style>

<body>
  <header>Header</header>
  <div class="content">
    <aside class="sidebar-left">Left Sidebar</aside>
    <main>Main Content</main>
    <aside class="sidebar-right">Right Sidebar</aside>
  </div>
  <footer>Footer</footer>
</body>
```

---

## 🎯 Practice Exercise

Build a responsive pricing table with 3 columns that stack on mobile.

<details>
<summary>Solution</summary>

```css
.pricing {
  display: flex;
  gap: 2rem;
  flex-wrap: wrap;
}

.plan {
  flex: 1 1 250px;
  background: white;
  padding: 2rem;
  border: 1px solid #ddd;
  border-radius: 8px;
  text-align: center;
}

@media (max-width: 768px) {
  .pricing {
    flex-direction: column;
  }
}
```
</details>

---

**Next:** [12 - Grid](./12-grid.md) (already complete!)
