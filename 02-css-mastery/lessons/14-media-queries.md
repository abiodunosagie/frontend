# Lesson 14: Media Queries - Responsive Design Mastery

> **"Your website should look great on a phone, tablet, and desktop. Media queries make that possible."**

---

## 🎯 What are Media Queries?

**Media queries let you apply different CSS based on screen size** (and other factors).

Think of it like **clothing for different weather**:
- Winter → Wear a coat (large screens → desktop layout)
- Summer → Wear shorts (small screens → mobile layout)

**Same person, different outfit. Same website, different layout.**

---

## 📱 Why Responsiveness Matters

### The Reality:
- **Over 60% of web traffic** is mobile
- **Google ranks mobile-friendly sites** higher
- **Users leave** if site doesn't work on their device

### What Responsive Means:
```
Desktop (1200px+):   [Nav] [Content         ] [Sidebar]
Tablet (768-1199px): [Nav] [Content    ] [Sidebar]
Mobile (< 768px):    [Nav]
                     [Content]
                     [Sidebar]
```

**Same content, different layouts!**

---

## 🔧 Media Query Syntax

```css
/* Default styles (mobile first) */
.container {
  padding: 10px;
}

/* Tablet and up */
@media (min-width: 768px) {
  .container {
    padding: 20px;
  }
}

/* Desktop and up */
@media (min-width: 1024px) {
  .container {
    padding: 40px;
  }
}
```

---

## 📏 Standard Breakpoints

```css
/* Mobile first approach (recommended) */

/* Extra small devices (phones, less than 576px) */
/* Default styles go here - no media query needed */

/* Small devices (landscape phones, 576px and up) */
@media (min-width: 576px) {
  /* ... */
}

/* Medium devices (tablets, 768px and up) */
@media (min-width: 768px) {
  /* ... */
}

/* Large devices (desktops, 992px and up) */
@media (min-width: 992px) {
  /* ... */
}

/* Extra large devices (large desktops, 1200px and up) */
@media (min-width: 1200px) {
  /* ... */
}
```

**These are Bootstrap's breakpoints** - industry standard!

---

## 🎨 Your First Responsive Layout

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Responsive Demo</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: Arial, sans-serif;
    }

    .container {
      padding: 20px;
    }

    .grid {
      display: grid;
      grid-template-columns: 1fr;  /* Mobile: 1 column */
      gap: 20px;
    }

    .box {
      background: #007bff;
      color: white;
      padding: 40px;
      text-align: center;
      border-radius: 8px;
    }

    /* Tablet: 2 columns */
    @media (min-width: 768px) {
      .grid {
        grid-template-columns: repeat(2, 1fr);
      }
    }

    /* Desktop: 3 columns */
    @media (min-width: 1024px) {
      .grid {
        grid-template-columns: repeat(3, 1fr);
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Responsive Grid</h1>
    <p>Resize your browser window to see the magic!</p>
    <div class="grid">
      <div class="box">Box 1</div>
      <div class="box">Box 2</div>
      <div class="box">Box 3</div>
      <div class="box">Box 4</div>
      <div class="box">Box 5</div>
      <div class="box">Box 6</div>
    </div>
  </div>
</body>
</html>
```

**Open this and resize your browser!** 🎉

---

## 🎯 Media Query Features

### 1. **Width** (Most Common)

```css
/* Minimum width */
@media (min-width: 768px) {
  /* Applies when viewport is 768px or wider */
}

/* Maximum width */
@media (max-width: 767px) {
  /* Applies when viewport is 767px or narrower */
}

/* Range */
@media (min-width: 768px) and (max-width: 1023px) {
  /* Applies only between 768px and 1023px */
}
```

### 2. **Orientation**

```css
/* Portrait (height > width) */
@media (orientation: portrait) {
  /* Phone held vertically */
}

/* Landscape (width > height) */
@media (orientation: landscape) {
  /* Phone held horizontally */
}
```

### 3. **Hover Capability** (Detects touch vs mouse)

```css
/* Has hover (desktop/laptop with mouse) */
@media (hover: hover) {
  .button:hover {
    background: blue;
  }
}

/* No hover (touch devices) */
@media (hover: none) {
  .button:active {
    background: blue;
  }
}
```

### 4. **Prefer Color Scheme** (Dark mode!)

```css
/* Light mode (default) */
@media (prefers-color-scheme: light) {
  body {
    background: white;
    color: black;
  }
}

/* Dark mode */
@media (prefers-color-scheme: dark) {
  body {
    background: #1a1a1a;
    color: white;
  }
}
```

---

## 🎨 Common Responsive Patterns

### Pattern 1: Responsive Navigation

```html
<style>
  .nav {
    display: flex;
    flex-direction: column;  /* Mobile: vertical menu */
    gap: 10px;
  }

  /* Desktop: horizontal menu */
  @media (min-width: 768px) {
    .nav {
      flex-direction: row;
      justify-content: space-between;
      align-items: center;
    }
  }
</style>

<nav class="nav">
  <a href="#">Home</a>
  <a href="#">About</a>
  <a href="#">Services</a>
  <a href="#">Contact</a>
</nav>
```

---

### Pattern 2: Sidebar Layout

```html
<style>
  .layout {
    display: grid;
    grid-template-columns: 1fr;  /* Mobile: stacked */
    gap: 20px;
  }

  /* Desktop: sidebar + content */
  @media (min-width: 992px) {
    .layout {
      grid-template-columns: 250px 1fr;
    }
  }
</style>

<div class="layout">
  <aside class="sidebar">Sidebar</aside>
  <main class="content">Main Content</main>
</div>
```

---

### Pattern 3: Responsive Typography

```css
h1 {
  font-size: 24px;  /* Mobile */
}

@media (min-width: 768px) {
  h1 {
    font-size: 32px;  /* Tablet */
  }
}

@media (min-width: 1024px) {
  h1 {
    font-size: 48px;  /* Desktop */
  }
}
```

---

### Pattern 4: Hide/Show Elements

```css
.mobile-only {
  display: block;
}

.desktop-only {
  display: none;
}

@media (min-width: 768px) {
  .mobile-only {
    display: none;
  }

  .desktop-only {
    display: block;
  }
}
```

```html
<div class="mobile-only">
  <button>☰ Menu</button>
</div>

<nav class="desktop-only">
  <a href="#">Home</a>
  <a href="#">About</a>
  <a href="#">Contact</a>
</nav>
```

---

### Pattern 5: Responsive Images

```css
img {
  max-width: 100%;  /* Never wider than container */
  height: auto;     /* Maintain aspect ratio */
}

.hero-image {
  width: 100%;
  height: 200px;  /* Mobile: shorter */
  object-fit: cover;
}

@media (min-width: 768px) {
  .hero-image {
    height: 400px;  /* Desktop: taller */
  }
}
```

---

## 🎯 Mobile-First vs Desktop-First

### Mobile-First (RECOMMENDED) ⭐

Start with mobile styles, add complexity for larger screens.

```css
/* Mobile styles (default) */
.container {
  padding: 10px;
}

/* Add styles for larger screens */
@media (min-width: 768px) {
  .container {
    padding: 20px;
  }
}

@media (min-width: 1024px) {
  .container {
    padding: 40px;
  }
}
```

**Why mobile-first?**
- Most users are on mobile
- Easier to add features than remove them
- Better performance on mobile
- Forces you to prioritize content

### Desktop-First (Old Way)

Start with desktop, remove features for mobile.

```css
/* Desktop styles (default) */
.container {
  padding: 40px;
}

/* Remove complexity for smaller screens */
@media (max-width: 1023px) {
  .container {
    padding: 20px;
  }
}

@media (max-width: 767px) {
  .container {
    padding: 10px;
  }
}
```

**Use mobile-first unless you have a good reason not to.**

---

## 🐛 Common Responsive Mistakes

### 1. Forgetting the Viewport Meta Tag

```html
<!-- Without this, mobile browsers render at desktop width! -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

**ALWAYS include this in your `<head>`!**

### 2. Using Fixed Widths

```css
/* Bad */
.container {
  width: 1200px;  /* Breaks on smaller screens! */
}

/* Good */
.container {
  max-width: 1200px;  /* Never wider than 1200px */
  width: 100%;        /* But can be narrower */
  padding: 0 20px;    /* Add padding for small screens */
}
```

### 3. Not Testing on Real Devices

Chrome DevTools is great, but test on real phones and tablets too!

**How to test:**
1. Press `F12` in Chrome
2. Click "Toggle device toolbar" (phone/tablet icon)
3. Select different devices

---

## ✏️ Practice Exercise

Create a **responsive card layout**:

Requirements:
- Mobile (< 768px): 1 card per row
- Tablet (768-1023px): 2 cards per row
- Desktop (1024px+): 3 cards per row
- Cards should have:
  - Image at top
  - Title
  - Description
  - Button at bottom
- Proper spacing
- Responsive images

<details>
<summary>Solution</summary>

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Responsive Cards</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: Arial, sans-serif;
      background: #f5f5f5;
      padding: 20px;
    }

    h1 {
      text-align: center;
      margin-bottom: 30px;
      font-size: 24px;
    }

    .cards {
      display: grid;
      grid-template-columns: 1fr;  /* Mobile: 1 column */
      gap: 20px;
      max-width: 1200px;
      margin: 0 auto;
    }

    .card {
      background: white;
      border-radius: 8px;
      overflow: hidden;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
      display: flex;
      flex-direction: column;
    }

    .card img {
      width: 100%;
      height: 200px;
      object-fit: cover;
    }

    .card-content {
      padding: 20px;
      flex: 1;
      display: flex;
      flex-direction: column;
    }

    .card h2 {
      font-size: 20px;
      margin-bottom: 10px;
    }

    .card p {
      color: #666;
      line-height: 1.6;
      margin-bottom: 20px;
      flex: 1;
    }

    .card button {
      padding: 10px 20px;
      background: #007bff;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      align-self: flex-start;
    }

    .card button:hover {
      background: #0056b3;
    }

    /* Tablet: 2 columns */
    @media (min-width: 768px) {
      h1 {
        font-size: 32px;
      }

      .cards {
        grid-template-columns: repeat(2, 1fr);
      }
    }

    /* Desktop: 3 columns */
    @media (min-width: 1024px) {
      h1 {
        font-size: 40px;
      }

      .cards {
        grid-template-columns: repeat(3, 1fr);
      }
    }
  </style>
</head>
<body>
  <h1>Responsive Card Layout</h1>
  <div class="cards">
    <div class="card">
      <img src="https://picsum.photos/400/200?random=1" alt="Card image">
      <div class="card-content">
        <h2>Card Title 1</h2>
        <p>This is a description of the card. Resize your browser to see how the layout adapts!</p>
        <button>Learn More</button>
      </div>
    </div>

    <div class="card">
      <img src="https://picsum.photos/400/200?random=2" alt="Card image">
      <div class="card-content">
        <h2>Card Title 2</h2>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
        <button>Learn More</button>
      </div>
    </div>

    <div class="card">
      <img src="https://picsum.photos/400/200?random=3" alt="Card image">
      <div class="card-content">
        <h2>Card Title 3</h2>
        <p>Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
        <button>Learn More</button>
      </div>
    </div>

    <div class="card">
      <img src="https://picsum.photos/400/200?random=4" alt="Card image">
      <div class="card-content">
        <h2>Card Title 4</h2>
        <p>Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris.</p>
        <button>Learn More</button>
      </div>
    </div>

    <div class="card">
      <img src="https://picsum.photos/400/200?random=5" alt="Card image">
      <div class="card-content">
        <h2>Card Title 5</h2>
        <p>Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore.</p>
        <button>Learn More</button>
      </div>
    </div>

    <div class="card">
      <img src="https://picsum.photos/400/200?random=6" alt="Card image">
      <div class="card-content">
        <h2>Card Title 6</h2>
        <p>Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia.</p>
        <button>Learn More</button>
      </div>
    </div>
  </div>
</body>
</html>
```

</details>

---

## 🎯 Responsive Design Checklist

Before launching any website:

- [ ] Viewport meta tag in `<head>`
- [ ] Mobile-first CSS approach
- [ ] Test on Chrome DevTools (all device sizes)
- [ ] Test on real phone/tablet
- [ ] Responsive images (`max-width: 100%`)
- [ ] Readable font sizes on mobile (minimum 16px)
- [ ] Touch targets at least 44x44px
- [ ] No horizontal scrolling on mobile
- [ ] Content readable without zooming

---

## 🎯 Key Takeaways

1. **Media queries adapt layouts to screen size**
2. **Mobile-first is the modern approach**
3. **Standard breakpoints:** 576px, 768px, 992px, 1200px
4. **Always include viewport meta tag**
5. **Test on real devices, not just DevTools**
6. **Grid and Flexbox make responsive design easy**

---

## 🚀 Next Lesson

You now know how to make sites responsive. Let's make them **accessible**!

**Next:** Accessibility Basics (coming next)

---

**Every website you build from now on should be responsive. No excuses.** 📱💻
