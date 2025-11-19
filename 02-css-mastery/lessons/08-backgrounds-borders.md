# CSS Lesson 08 - Backgrounds & Borders

> **"Small visual touches that make big differences in design."**

---

## 🎯 What You'll Learn

- Background colors and images
- Background size, position, and repeat
- Linear and radial gradients
- Multiple backgrounds
- Borders (all variations)
- Border radius for rounded corners
- Box shadows for depth
- Outline property
- Text shadows
- Real-world patterns and examples

**Time to complete:** 30-40 minutes

---

## 🎨 Background Color

### Basic Syntax
```css
div {
  background-color: #3498db;
  background-color: rgb(52, 152, 219);
  background-color: rgba(52, 152, 219, 0.5); /* With transparency */
  background-color: hsl(204, 70%, 53%);
}
```

### Transparency

```css
.overlay {
  background-color: rgba(0, 0, 0, 0.7); /* 70% opaque black */
}

.light-overlay {
  background-color: rgba(255, 255, 255, 0.3); /* 30% opaque white */
}
```

---

## 🖼️ Background Images

### Basic Image
```css
div {
  background-image: url('image.jpg');
}
```

### Background Size

```css
/* Cover entire area (may crop) */
.hero {
  background-image: url('hero.jpg');
  background-size: cover; /* Most common */
}

/* Contain (fit without cropping) */
.logo {
  background-image: url('logo.png');
  background-size: contain;
}

/* Specific dimensions */
.pattern {
  background-image: url('pattern.png');
  background-size: 200px 150px;
}

/* Percentage */
.scaled {
  background-size: 100% auto;
}
```

### Background Position

```css
/* Keywords */
background-position: center;
background-position: top right;
background-position: bottom left;

/* Percentages */
background-position: 50% 50%; /* Center */
background-position: 100% 0%; /* Top right */

/* Pixels */
background-position: 20px 30px;

/* Mixed */
background-position: center 20px; /* Horizontally centered, 20px from top */
```

### Background Repeat

```css
background-repeat: repeat;      /* Default: tile */
background-repeat: no-repeat;   /* Show once */
background-repeat: repeat-x;    /* Repeat horizontally only */
background-repeat: repeat-y;    /* Repeat vertically only */
background-repeat: space;       /* Repeat with spacing */
background-repeat: round;       /* Repeat and stretch to fit */
```

### Background Attachment

```css
/* Scrolls with page (default) */
background-attachment: scroll;

/* Fixed (parallax effect) */
background-attachment: fixed;

/* Stays with element */
background-attachment: local;
```

### Background Shorthand

```css
/* Combines all properties */
.hero {
  background: url('hero.jpg') center/cover no-repeat fixed;
  /* image position/size repeat attachment */
}

.card {
  background: #f0f0f0 url('pattern.png') top left/50px repeat-x;
  /* color image position/size repeat */
}
```

---

## 🌈 Gradients

### Linear Gradients

**Basic gradient:**
```css
div {
  background: linear-gradient(to right, #3498db, #2ecc71);
}
```

**Angle gradients:**
```css
/* Top to bottom (default) */
background: linear-gradient(red, blue);

/* Directions */
background: linear-gradient(to right, red, blue);
background: linear-gradient(to bottom right, red, blue);

/* Angles (0deg = to top, 90deg = to right) */
background: linear-gradient(45deg, red, blue);
background: linear-gradient(135deg, #667eea, #764ba2);
```

**Multiple color stops:**
```css
background: linear-gradient(
  to right,
  red,
  orange 25%,
  yellow 50%,
  green 75%,
  blue
);
```

**Hard color stops (no blending):**
```css
/* Stripes */
background: linear-gradient(
  90deg,
  red 0% 33%,
  white 33% 66%,
  blue 66% 100%
);
```

### Radial Gradients

**Basic radial:**
```css
background: radial-gradient(circle, #3498db, #2ecc71);
```

**Ellipse (default):**
```css
background: radial-gradient(ellipse, red, blue);
```

**Positioned radial:**
```css
background: radial-gradient(circle at top left, red, blue);
background: radial-gradient(circle at 75% 25%, yellow, transparent);
```

**Sized radial:**
```css
background: radial-gradient(100px 50px at center, red, blue);
```

### Conic Gradients

```css
/* Pie chart effect */
background: conic-gradient(red, orange, yellow, green, blue, purple, red);

/* With stops */
background: conic-gradient(
  from 0deg at 50% 50%,
  red 0deg 120deg,
  green 120deg 240deg,
  blue 240deg 360deg
);
```

### Popular Gradient Patterns

**Sunset:**
```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

**Ocean:**
```css
background: linear-gradient(to bottom, #00c6ff, #0072ff);
```

**Mesh:**
```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 60%, #f093fb 100%);
```

---

## 🎭 Multiple Backgrounds

**Layer multiple backgrounds:**

```css
div {
  background:
    url('foreground.png') center/contain no-repeat,
    url('background.jpg') center/cover no-repeat,
    linear-gradient(to bottom, rgba(0,0,0,0.5), rgba(0,0,0,0.8));
  /* First listed = top layer */
}
```

**Practical example:**

```css
.hero {
  background:
    url('overlay-pattern.png') repeat,
    linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.4)),
    url('hero-image.jpg') center/cover no-repeat fixed;
}
```

---

## 🔲 Borders

### Basic Border

```css
div {
  border: 2px solid #333;
  /* width style color */
}
```

### Border Styles

```css
border-style: solid;   /* Most common */
border-style: dashed;
border-style: dotted;
border-style: double;
border-style: groove;
border-style: ridge;
border-style: inset;
border-style: outset;
border-style: none;
border-style: hidden;
```

### Individual Sides

```css
div {
  border-top: 1px solid #ddd;
  border-right: 2px dashed red;
  border-bottom: 3px dotted blue;
  border-left: 4px double green;
}

/* Or using shorthand properties */
div {
  border-width: 1px 2px 3px 4px; /* top right bottom left */
  border-style: solid dashed dotted double;
  border-color: red green blue orange;
}
```

### Border Radius (Rounded Corners)

**All corners equal:**
```css
div {
  border-radius: 8px;
}
```

**Perfect circle:**
```css
.circle {
  width: 100px;
  height: 100px;
  border-radius: 50%;
}
```

**Each corner individually:**
```css
div {
  border-radius: 20px 10px 20px 10px;
  /* top-left top-right bottom-right bottom-left */
}
```

**Elliptical corners:**
```css
div {
  border-radius: 50px / 20px; /* horizontal / vertical */
}
```

**Individual corners:**
```css
div {
  border-top-left-radius: 20px;
  border-top-right-radius: 10px;
  border-bottom-right-radius: 5px;
  border-bottom-left-radius: 15px;
}
```

**Pill shape:**
```css
.pill {
  border-radius: 9999px; /* Very large value */
  padding: 10px 30px;
}
```

---

## 💎 Box Shadow

### Basic Syntax

```css
box-shadow: x-offset y-offset blur spread color;
```

### Simple Shadow

```css
.card {
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  /* Subtle shadow below */
}
```

### Shadow Variations

```css
/* No blur */
box-shadow: 2px 2px 0 rgba(0,0,0,0.2);

/* Large spread */
box-shadow: 0 0 0 10px rgba(52,152,219,0.3);

/* Inset shadow (inside element) */
box-shadow: inset 0 2px 4px rgba(0,0,0,0.2);

/* Lifted effect */
box-shadow: 0 10px 25px rgba(0,0,0,0.15);

/* Pressed effect */
box-shadow: inset 0 3px 5px rgba(0,0,0,0.125);
```

### Multiple Shadows

```css
.card {
  box-shadow:
    0 1px 3px rgba(0,0,0,0.12),
    0 1px 2px rgba(0,0,0,0.24);
}

/* Layered depth */
.elevated {
  box-shadow:
    0 2px 4px rgba(0,0,0,0.05),
    0 4px 8px rgba(0,0,0,0.05),
    0 8px 16px rgba(0,0,0,0.05);
}
```

### Colored Shadows

```css
.blue-shadow {
  box-shadow: 0 4px 12px rgba(52, 152, 219, 0.4);
}

.neon {
  box-shadow: 0 0 20px rgba(0, 255, 255, 0.8);
}
```

---

## ✏️ Text Shadow

```css
text-shadow: x-offset y-offset blur color;
```

### Examples

```css
/* Subtle text shadow */
h1 {
  text-shadow: 1px 1px 2px rgba(0,0,0,0.2);
}

/* Glow effect */
h1 {
  color: white;
  text-shadow: 0 0 10px rgba(255,255,255,0.8);
}

/* Multiple text shadows */
h1 {
  text-shadow:
    0 1px 0 #ccc,
    0 2px 0 #c9c9c9,
    0 3px 0 #bbb,
    0 4px 0 #b9b9b9,
    0 5px 10px rgba(0,0,0,0.3);
}

/* Outline effect */
h1 {
  color: white;
  text-shadow:
    -1px -1px 0 #000,
    1px -1px 0 #000,
    -1px 1px 0 #000,
    1px 1px 0 #000;
}
```

---

## 🎨 Outline

**Like border but doesn't affect layout:**

```css
button:focus {
  outline: 2px solid blue;
  outline-offset: 2px;
}

/* Remove default outline (but replace with something!) */
button {
  outline: none; /* Accessibility issue if not replaced */
}

/* Custom focus style */
button:focus {
  outline: 2px dashed orange;
  outline-offset: 4px;
}
```

**Outline vs Border:**
- Outline doesn't take up space
- Outline doesn't affect element size or position
- Outline can't have rounded corners (no outline-radius)
- Outline is drawn outside border

---

## 🎯 Real-World Examples

### Example 1: Modern Card with Gradient

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .card {
      background: white;
      border-radius: 12px;
      padding: 30px;
      max-width: 400px;
      box-shadow:
        0 4px 6px rgba(0,0,0,0.07),
        0 10px 15px rgba(0,0,0,0.05);
      position: relative;
      overflow: hidden;
    }

    .card::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      height: 4px;
      background: linear-gradient(90deg, #667eea 0%, #764ba2 100%);
    }

    .card:hover {
      box-shadow:
        0 6px 12px rgba(0,0,0,0.1),
        0 15px 25px rgba(0,0,0,0.08);
      transform: translateY(-2px);
      transition: all 0.3s ease;
    }
  </style>
</head>
<body>
  <div class="card">
    <h2>Card Title</h2>
    <p>Modern card with gradient top border and elevation on hover.</p>
  </div>
</body>
</html>
```

### Example 2: Parallax Hero Section

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .hero {
      height: 100vh;
      background:
        linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.4)),
        url('https://images.unsplash.com/photo-1506905925346-21bda4d32df4') center/cover fixed;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      text-align: center;
    }

    .hero h1 {
      font-size: 4rem;
      text-shadow: 2px 2px 8px rgba(0,0,0,0.7);
    }

    .content {
      padding: 100px 20px;
      background: white;
    }
  </style>
</head>
<body>
  <div class="hero">
    <div>
      <h1>Parallax Hero</h1>
      <p>Scroll down to see the effect</p>
    </div>
  </div>
  <div class="content">
    <h2>Content Section</h2>
    <p>Background stays fixed while scrolling...</p>
  </div>
</body>
</html>
```

### Example 3: Neumorphism Card

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      background: #e0e5ec;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
    }

    .neu-card {
      background: #e0e5ec;
      border-radius: 20px;
      padding: 40px;
      box-shadow:
        9px 9px 16px rgba(163,177,198,0.6),
        -9px -9px 16px rgba(255,255,255, 0.5);
    }

    .neu-button {
      background: #e0e5ec;
      border: none;
      border-radius: 12px;
      padding: 15px 30px;
      box-shadow:
        4px 4px 8px rgba(163,177,198,0.6),
        -4px -4px 8px rgba(255,255,255, 0.5);
      cursor: pointer;
    }

    .neu-button:active {
      box-shadow:
        inset 4px 4px 8px rgba(163,177,198,0.6),
        inset -4px -4px 8px rgba(255,255,255, 0.5);
    }
  </style>
</head>
<body>
  <div class="neu-card">
    <h2>Neumorphism Card</h2>
    <p>Soft UI design trend</p>
    <button class="neu-button">Click Me</button>
  </div>
</body>
</html>
```

### Example 4: Glassmorphism Effect

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .glass {
      background: rgba(255, 255, 255, 0.1);
      border: 1px solid rgba(255, 255, 255, 0.2);
      border-radius: 16px;
      padding: 40px;
      backdrop-filter: blur(10px);
      box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
      color: white;
    }
  </style>
</head>
<body>
  <div class="glass">
    <h2>Glassmorphism</h2>
    <p>Frosted glass effect</p>
  </div>
</body>
</html>
```

---

## 🎯 Practice Exercises

### Exercise 1: Button with Gradient Background

Create a button with a gradient background that changes on hover.

<details>
<summary>Solution</summary>

```css
.gradient-button {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border: none;
  padding: 15px 30px;
  border-radius: 8px;
  font-size: 16px;
  cursor: pointer;
  box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
  transition: all 0.3s ease;
}

.gradient-button:hover {
  background: linear-gradient(135deg, #764ba2 0%, #667eea 100%);
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(102, 126, 234, 0.6);
}

.gradient-button:active {
  transform: translateY(0);
}
```
</details>

### Exercise 2: Card with Border Gradient

Create a card with a gradient border (hint: use background-clip or pseudo-element).

<details>
<summary>Solution</summary>

```css
.gradient-border-card {
  position: relative;
  background: white;
  border-radius: 12px;
  padding: 30px;
  margin: 20px;
}

.gradient-border-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  border-radius: 12px;
  padding: 2px;
  background: linear-gradient(135deg, #667eea, #764ba2);
  -webkit-mask:
    linear-gradient(#fff 0 0) content-box,
    linear-gradient(#fff 0 0);
  mask:
    linear-gradient(#fff 0 0) content-box,
    linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
}
```
</details>

---

## 🎯 Key Takeaways

✅ **background: url() center/cover no-repeat** - Common image pattern
✅ **linear-gradient** for color transitions
✅ **radial-gradient** for circular effects
✅ **border-radius: 50%** for perfect circles
✅ **box-shadow** for depth and elevation
✅ **Multiple shadows** for realistic depth
✅ **text-shadow** for text effects
✅ **outline** for focus states (accessibility!)
✅ **background: fixed** for parallax effects
✅ **Multiple backgrounds** layer from top to bottom

---

**Next:** [09 - Display & Positioning](./09-display-positioning.md)
