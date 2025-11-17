# Lesson 12: CSS Grid - Master 2D Layouts

> **"CSS Grid is the most powerful layout system in CSS. Period."**

Flexbox is great for rows OR columns. Grid is for rows AND columns simultaneously.

---

## 🎯 What is CSS Grid?

**Grid lets you create two-dimensional layouts** - rows and columns at the same time.

Think of it like a **spreadsheet**:

```
┌─────────┬─────────┬─────────┐
│  Header │  Header │  Header │
├─────────┼─────────┼─────────┤
│ Content │ Content │ Content │
├─────────┼─────────┼─────────┤
│ Footer  │ Footer  │ Footer  │
└─────────┴─────────┴─────────┘
```

Or a **newspaper layout**:

```
┌───────────────────┬─────────┐
│                   │ Sidebar │
│   Main Article    │         │
│                   │         │
├─────────┬─────────┤         │
│ Image 1 │ Image 2 │         │
└─────────┴─────────┴─────────┘
```

**Grid makes complex layouts trivial.**

---

## 🏗️ Grid Basics

### 1. Create a Grid Container

```css
.container {
  display: grid;
}
```

### 2. Define Columns

```css
.container {
  display: grid;
  grid-template-columns: 200px 200px 200px;  /* 3 columns, 200px each */
}
```

### 3. Define Rows (Optional, auto by default)

```css
.container {
  display: grid;
  grid-template-columns: 200px 200px 200px;
  grid-template-rows: 100px 100px;  /* 2 rows, 100px each */
}
```

---

## 🎨 Your First Grid

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CSS Grid Demo</title>
  <style>
    * {
      box-sizing: border-box;
    }

    .grid {
      display: grid;
      grid-template-columns: 200px 200px 200px;
      gap: 20px;  /* Space between grid items */
      padding: 20px;
      background: #f0f0f0;
    }

    .item {
      background: #007bff;
      color: white;
      padding: 20px;
      text-align: center;
    }
  </style>
</head>
<body>
  <div class="grid">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
    <div class="item">4</div>
    <div class="item">5</div>
    <div class="item">6</div>
  </div>
</body>
</html>
```

**3 columns, automatic rows!** 🎉

---

## 🔧 Defining Columns and Rows

### Fixed Sizes

```css
.grid {
  grid-template-columns: 200px 300px 100px;  /* 3 columns: 200px, 300px, 100px */
}
```

### Fractions (`fr` units) - THE BEST WAY

```css
.grid {
  grid-template-columns: 1fr 2fr 1fr;  /* 3 columns: 1 part, 2 parts, 1 part */
}
```

**`1fr` = 1 fraction of available space**

Example: If container is 800px wide:
- Column 1: 200px (1/4)
- Column 2: 400px (2/4)
- Column 3: 200px (1/4)

### Mix Fixed and Flexible

```css
.grid {
  grid-template-columns: 200px 1fr 1fr;  /* Fixed 200px, then 2 equal flexible columns */
}
```

### Repeat Function

```css
.grid {
  grid-template-columns: repeat(3, 1fr);  /* Same as: 1fr 1fr 1fr */
}
```

### Auto-fit and Auto-fill (Responsive!)

```css
.grid {
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
}
```

**This creates as many columns as fit, minimum 250px each!** (Responsive without media queries)

---

## 🎯 Grid Container Properties

### 1. **gap** - Space between grid items

```css
.grid {
  gap: 20px;  /* 20px gap everywhere */
}

/* Or separate: */
.grid {
  row-gap: 20px;
  column-gap: 30px;
}
```

### 2. **grid-template-areas** - Name grid areas (POWERFUL!)

```css
.grid {
  display: grid;
  grid-template-columns: 1fr 3fr 1fr;
  grid-template-rows: auto 1fr auto;
  grid-template-areas:
    "header header header"
    "sidebar main aside"
    "footer footer footer";
  gap: 20px;
}

.header  { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main    { grid-area: main; }
.aside   { grid-area: aside; }
.footer  { grid-area: footer; }
```

```html
<div class="grid">
  <header class="header">Header</header>
  <aside class="sidebar">Sidebar</aside>
  <main class="main">Main Content</main>
  <aside class="aside">Aside</aside>
  <footer class="footer">Footer</footer>
</div>
```

**Visual layout in your CSS!** 🤯

### 3. **justify-items** - Align items horizontally

```css
.grid {
  justify-items: center;  /* start | end | center | stretch */
}
```

### 4. **align-items** - Align items vertically

```css
.grid {
  align-items: center;  /* start | end | center | stretch */
}
```

---

## 🎯 Grid Item Properties

### 1. **grid-column** - Span columns

```css
.item1 {
  grid-column: 1 / 3;  /* Start at line 1, end at line 3 (spans 2 columns) */
}

/* Shorthand: */
.item1 {
  grid-column: span 2;  /* Span 2 columns */
}
```

### 2. **grid-row** - Span rows

```css
.item1 {
  grid-row: 1 / 3;  /* Spans 2 rows */
}
```

### 3. **grid-area** - Span both (shorthand)

```css
.item1 {
  grid-area: 1 / 1 / 3 / 3;  /* row-start / col-start / row-end / col-end */
}
```

---

## 🎨 Common Grid Patterns

### Pattern 1: Holy Grail Layout

```css
.layout {
  display: grid;
  grid-template-columns: 200px 1fr 200px;
  grid-template-rows: auto 1fr auto;
  grid-template-areas:
    "header header header"
    "sidebar main aside"
    "footer footer footer";
  min-height: 100vh;
  gap: 20px;
}

.header  { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main    { grid-area: main; }
.aside   { grid-area: aside; }
.footer  { grid-area: footer; }
```

```html
<div class="layout">
  <header class="header">Header</header>
  <aside class="sidebar">Sidebar</aside>
  <main class="main">Main</main>
  <aside class="aside">Aside</aside>
  <footer class="footer">Footer</footer>
</div>
```

**The classic layout, done in minutes!**

---

### Pattern 2: Responsive Card Grid

```css
.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}

.card {
  background: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}
```

**Automatically responsive!** Adds/removes columns based on screen width.

---

### Pattern 3: Image Gallery

```css
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 10px;
}

.gallery img {
  width: 100%;
  height: 200px;
  object-fit: cover;
  border-radius: 8px;
}
```

---

### Pattern 4: Dashboard Layout

```css
.dashboard {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(3, 200px);
  gap: 20px;
}

.widget1 {
  grid-column: span 2;
  grid-row: span 2;
}

.widget2 {
  grid-column: span 2;
}

.widget3 {
  grid-row: span 3;
}
```

**Complex layouts with simple rules!**

---

### Pattern 5: Magazine Layout

```css
.magazine {
  display: grid;
  grid-template-columns: repeat(6, 1fr);
  gap: 20px;
}

.featured {
  grid-column: span 4;
  grid-row: span 2;
}

.article {
  grid-column: span 2;
}

.sidebar {
  grid-column: span 2;
  grid-row: span 3;
}
```

---

## 🎯 Flexbox vs Grid - When to Use Which?

### Use **Flexbox** when:
- One-dimensional layout (row OR column)
- Navigation menu
- Centering items
- Distributing space evenly
- Components where content size varies

### Use **Grid** when:
- Two-dimensional layout (rows AND columns)
- Page layouts
- Card grids
- Galleries
- Dashboard layouts
- Complex, structured layouts

### Use **Both** together!

```css
.page {
  display: grid;  /* Overall page layout */
  grid-template-columns: 200px 1fr;
}

.nav {
  display: flex;  /* Nav items in a row */
  gap: 20px;
}
```

**Grid for layout, Flexbox for components!**

---

## ✏️ Practice Exercise

Create a **responsive blog layout**:

Requirements:
- Header spanning full width
- Sidebar (250px wide) on left
- Main content area
- Footer spanning full width
- On mobile (< 768px), sidebar goes below content
- 20px gap between all elements

<details>
<summary>Solution</summary>

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Grid Blog Layout</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: Arial, sans-serif;
    }

    .layout {
      display: grid;
      grid-template-columns: 250px 1fr;
      grid-template-rows: auto 1fr auto;
      grid-template-areas:
        "header header"
        "sidebar main"
        "footer footer";
      min-height: 100vh;
      gap: 20px;
      padding: 20px;
    }

    .header {
      grid-area: header;
      background: #333;
      color: white;
      padding: 20px;
      border-radius: 8px;
    }

    .sidebar {
      grid-area: sidebar;
      background: #f0f0f0;
      padding: 20px;
      border-radius: 8px;
    }

    .main {
      grid-area: main;
      background: white;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    }

    .footer {
      grid-area: footer;
      background: #333;
      color: white;
      padding: 20px;
      text-align: center;
      border-radius: 8px;
    }

    /* Mobile responsiveness */
    @media (max-width: 768px) {
      .layout {
        grid-template-columns: 1fr;
        grid-template-areas:
          "header"
          "main"
          "sidebar"
          "footer";
      }
    }
  </style>
</head>
<body>
  <div class="layout">
    <header class="header">
      <h1>My Blog</h1>
    </header>

    <aside class="sidebar">
      <h3>Sidebar</h3>
      <ul>
        <li>Category 1</li>
        <li>Category 2</li>
        <li>Category 3</li>
      </ul>
    </aside>

    <main class="main">
      <article>
        <h2>Blog Post Title</h2>
        <p>This is the main content area. Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
      </article>
    </main>

    <footer class="footer">
      <p>&copy; 2024 My Blog</p>
    </footer>
  </div>
</body>
</html>
```

</details>

---

## 🎯 Grid Cheat Sheet

```css
/* CONTAINER */
display: grid;
grid-template-columns: 200px 1fr 1fr;
grid-template-rows: auto 1fr auto;
grid-template-areas: "header header" "sidebar main";
gap: 20px;
justify-items: center | start | end | stretch;
align-items: center | start | end | stretch;

/* ITEMS */
grid-column: 1 / 3;  /* or span 2 */
grid-row: 1 / 3;     /* or span 2 */
grid-area: header;   /* or 1 / 1 / 3 / 3 */

/* RESPONSIVE MAGIC */
grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
```

---

## 🎯 Key Takeaways

1. **Grid = 2D layouts** (rows AND columns)
2. **Use `fr` units** for flexible layouts
3. **`repeat()` and `auto-fit`** for responsive grids
4. **`grid-template-areas`** for visual layouts
5. **Grid + Flexbox** = unstoppable combination

---

## 🚀 Next Lesson

Now you can create any layout. Let's make them **responsive**!

**Next:** [Lesson 14: Media Queries →](./14-media-queries.md)

---

**CSS Grid is your superpower for complex layouts. Master this, and you can build anything.** 💪
