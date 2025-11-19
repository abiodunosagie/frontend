# CSS Lesson 15 - Responsive Patterns

> **"Common responsive design patterns that work everywhere."**

---

## 🎯 Pattern 1: Responsive Navigation

```css
/* Mobile: Stacked vertical menu */
.nav {
  display: flex;
  flex-direction: column;
}

/* Desktop: Horizontal menu */
@media (min-width: 768px) {
  .nav {
    flex-direction: row;
    justify-content: space-between;
  }
}
```

---

## 🎯 Pattern 2: Responsive Typography

```css
/* Mobile */
h1 { font-size: 1.5rem; }
p { font-size: 1rem; }

/* Tablet */
@media (min-width: 768px) {
  h1 { font-size: 2rem; }
  p { font-size: 1.125rem; }
}

/* Desktop */
@media (min-width: 1024px) {
  h1 { font-size: 2.5rem; }
  p { font-size: 1.25rem; }
}

/* OR use fluid typography */
h1 {
  font-size: clamp(1.5rem, 5vw, 3rem);
  /* min, preferred, max */
}
```

---

## 🎯 Pattern 3: Container Widths

```css
.container {
  width: 100%;
  padding: 0 1rem;
}

@media (min-width: 640px) {
  .container { max-width: 640px; margin: 0 auto; }
}

@media (min-width: 768px) {
  .container { max-width: 768px; }
}

@media (min-width: 1024px) {
  .container { max-width: 1024px; }
}
```

---

## 🎯 Pattern 4: Hide/Show Elements

```css
/* Mobile: Hide sidebar */
.sidebar { display: none; }

/* Desktop: Show sidebar */
@media (min-width: 1024px) {
  .sidebar { display: block; }
}

/* Mobile menu icon (show on mobile, hide on desktop) */
.menu-icon { display: block; }

@media (min-width: 768px) {
  .menu-icon { display: none; }
}
```

---

## 🎯 Pattern 5: Responsive Images

```css
img {
  max-width: 100%;
  height: auto;
}

/* Art direction with picture element */
```

```html
<picture>
  <source media="(min-width: 1024px)" srcset="large.jpg">
  <source media="(min-width: 768px)" srcset="medium.jpg">
  <img src="small.jpg" alt="">
</picture>
```

---

## 🎯 Pattern 6: Responsive Grid Columns

```css
.grid {
  display: grid;
  gap: 1rem;
  grid-template-columns: 1fr; /* Mobile: 1 column */
}

@media (min-width: 640px) {
  .grid { grid-template-columns: repeat(2, 1fr); } /* Tablet: 2 columns */
}

@media (min-width: 1024px) {
  .grid { grid-template-columns: repeat(4, 1fr); } /* Desktop: 4 columns */
}
```

---

## 🎯 Complete Responsive Page Example

```html
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      font-family: system-ui, sans-serif;
      line-height: 1.6;
    }

    /* Container */
    .container {
      width: 100%;
      padding: 0 1rem;
      margin: 0 auto;
    }

    @media (min-width: 768px) {
      .container { max-width: 1200px; padding: 0 2rem; }
    }

    /* Navigation */
    nav {
      background: #333;
      color: white;
      padding: 1rem 0;
    }

    .nav-content {
      display: flex;
      flex-direction: column;
      gap: 1rem;
    }

    @media (min-width: 768px) {
      .nav-content {
        flex-direction: row;
        justify-content: space-between;
        align-items: center;
      }
    }

    /* Grid */
    .grid {
      display: grid;
      gap: 1.5rem;
      margin: 2rem 0;
      grid-template-columns: 1fr;
    }

    @media (min-width: 640px) {
      .grid { grid-template-columns: repeat(2, 1fr); }
    }

    @media (min-width: 1024px) {
      .grid { grid-template-columns: repeat(3, 1fr); }
    }

    .card {
      background: white;
      padding: 1.5rem;
      border-radius: 8px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    }

    /* Typography */
    h1 { font-size: clamp(1.5rem, 4vw, 2.5rem); }
    p { font-size: clamp(1rem, 2vw, 1.125rem); }
  </style>
</head>
<body>
  <nav>
    <div class="container">
      <div class="nav-content">
        <div class="logo">Brand</div>
        <div class="nav-links">Home | About | Contact</div>
      </div>
    </div>
  </nav>

  <div class="container">
    <h1>Responsive Layout</h1>
    <div class="grid">
      <div class="card">Card 1</div>
      <div class="card">Card 2</div>
      <div class="card">Card 3</div>
    </div>
  </div>
</body>
</html>
```

---

## 🎯 Key Takeaways

✅ Mobile-first: Start with mobile styles, enhance for larger screens
✅ Use `clamp()` for fluid typography
✅ `max-width: 100%` for responsive images
✅ Grid/Flexbox adapt naturally to different screen sizes
✅ Hide/show elements strategically

---

**Next:** [17 - Transitions & Animations](./17-transitions-animations.md)
