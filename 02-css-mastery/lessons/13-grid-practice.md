# CSS Lesson 13 - Grid Practice

> **"Real-world Grid layouts that you'll use constantly."**

---

## 🎯 Pattern 1: Photo Gallery

```html
<style>
  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1rem;
  }

  .gallery img {
    width: 100%;
    height: 250px;
    object-fit: cover;
    border-radius: 8px;
  }
</style>

<div class="gallery">
  <img src="photo1.jpg" alt="">
  <img src="photo2.jpg" alt="">
  <img src="photo3.jpg" alt="">
  <img src="photo4.jpg" alt="">
</div>
```

---

## 🎯 Pattern 2: Dashboard Layout

```html
<style>
  .dashboard {
    display: grid;
    grid-template-areas:
      "header header header"
      "sidebar main main"
      "footer footer footer";
    grid-template-columns: 200px 1fr 1fr;
    grid-template-rows: auto 1fr auto;
    min-height: 100vh;
    gap: 1rem;
  }

  .header { grid-area: header; background: #333; color: white; padding: 1rem; }
  .sidebar { grid-area: sidebar; background: #f4f4f4; padding: 1rem; }
  .main { grid-area: main; padding: 1rem; }
  .footer { grid-area: footer; background: #333; color: white; padding: 1rem; text-align: center; }
</style>

<div class="dashboard">
  <header class="header">Header</header>
  <aside class="sidebar">Sidebar</aside>
  <main class="main">Main Content</main>
  <footer class="footer">Footer</footer>
</div>
```

---

## 🎯 Pattern 3: Card Grid with Featured Item

```html
<style>
  .cards {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1rem;
  }

  .card { background: white; padding: 1.5rem; border-radius: 8px; }
  .featured { grid-column: span 2; grid-row: span 2; }
</style>

<div class="cards">
  <div class="card featured">Featured (2x2)</div>
  <div class="card">Card 1</div>
  <div class="card">Card 2</div>
  <div class="card">Card 3</div>
  <div class="card">Card 4</div>
</div>
```

---

## 🎯 Pattern 4: Magazine Layout

```html
<style>
  .magazine {
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    gap: 1rem;
  }

  .hero { grid-column: 1 / -1; }
  .main-article { grid-column: 1 / 9; }
  .sidebar { grid-column: 9 / -1; }
</style>
```

---

## 🎯 Pattern 5: Responsive Grid (Mobile → Desktop)

```html
<style>
  .responsive-grid {
    display: grid;
    gap: 1rem;
  }

  /* Mobile: 1 column */
  @media (min-width: 640px) {
    .responsive-grid { grid-template-columns: repeat(2, 1fr); }
  }

  @media (min-width: 1024px) {
    .responsive-grid { grid-template-columns: repeat(4, 1fr); }
  }
</style>
```

---

**Next:** [14 - Media Queries](./14-media-queries.md) (already complete!)
