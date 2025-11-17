# Lesson 5: Colors & Units

> **"Colors make it beautiful. Units make it precise."**

---

## 🎨 PART 1: COLORS IN CSS

### The Five Ways to Define Colors

#### 1. **Color Names** (Easiest, Limited)

```css
h1 {
  color: red;
  background-color: lightblue;
}
```

**147 named colors available:**
- `red`, `blue`, `green`, `yellow`, `purple`, `orange`
- `lightblue`, `darkgreen`, `hotpink`, `coral`
- `transparent` (special - means invisible)

**Pros:** Easy to remember
**Cons:** Limited options (only 147 colors)

---

#### 2. **Hexadecimal (Hex)** - Most Common ⭐

```css
h1 {
  color: #ff0000;  /* Red */
  background-color: #3498db;  /* Blue */
}
```

**Format:** `#RRGGBB`
- RR = Red (00-FF)
- GG = Green (00-FF)
- BB = Blue (00-FF)

**Examples:**
```css
#000000  /* Black */
#ffffff  /* White */
#ff0000  /* Red */
#00ff00  /* Green */
#0000ff  /* Blue */
#808080  /* Gray */
```

**Shorthand (when digits repeat):**
```css
#ff0000 = #f00  /* Red */
#00ff00 = #0f0  /* Green */
#ffffff = #fff  /* White */
```

---

#### 3. **RGB (Red, Green, Blue)**

```css
h1 {
  color: rgb(255, 0, 0);  /* Red */
  background-color: rgb(52, 152, 219);  /* Blue */
}
```

**Format:** `rgb(red, green, blue)`
- Each value: 0-255
- `rgb(0, 0, 0)` = Black
- `rgb(255, 255, 255)` = White

**Why use RGB?**
- More intuitive than hex for some people
- Easier to adjust (just change numbers)

---

#### 4. **RGBA (RGB + Alpha/Transparency)** - Very Useful!

```css
.overlay {
  background-color: rgba(0, 0, 0, 0.5);  /* Black, 50% transparent */
}

.box {
  background-color: rgba(52, 152, 219, 0.8);  /* Blue, 80% opaque */
}
```

**Format:** `rgba(red, green, blue, alpha)`
- Alpha: 0-1 (0 = fully transparent, 1 = fully opaque)

**Use cases:**
- Overlays (dark transparent background over images)
- Subtle backgrounds
- Layering elements

---

#### 5. **HSL (Hue, Saturation, Lightness)** - Designer-Friendly

```css
h1 {
  color: hsl(200, 70%, 50%);  /* Blue */
}
```

**Format:** `hsl(hue, saturation%, lightness%)`
- **Hue:** 0-360 (color wheel position)
  - 0/360 = Red
  - 120 = Green
  - 240 = Blue
- **Saturation:** 0-100% (color intensity)
  - 0% = Gray
  - 100% = Full color
- **Lightness:** 0-100% (brightness)
  - 0% = Black
  - 50% = Normal
  - 100% = White

**HSLA (with transparency):**
```css
.box {
  background-color: hsla(200, 70%, 50%, 0.5);
}
```

---

### 🎯 Color Examples Side-by-Side

| Color | Name | Hex | RGB | HSL |
|-------|------|-----|-----|-----|
| Red | `red` | `#ff0000` | `rgb(255,0,0)` | `hsl(0,100%,50%)` |
| Blue | `blue` | `#0000ff` | `rgb(0,0,255)` | `hsl(240,100%,50%)` |
| Green | `green` | `#008000` | `rgb(0,128,0)` | `hsl(120,100%,25%)` |
| White | `white` | `#ffffff` | `rgb(255,255,255)` | `hsl(0,0%,100%)` |
| Black | `black` | `#000000` | `rgb(0,0,0)` | `hsl(0,0%,0%)` |
| Gray | `gray` | `#808080` | `rgb(128,128,128)` | `hsl(0,0%,50%)` |

---

### 🎨 Working Example

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Colors Demo</title>
  <style>
    .box {
      width: 200px;
      height: 100px;
      margin: 10px;
      padding: 20px;
      color: white;
      text-align: center;
    }

    .box1 { background-color: red; }
    .box2 { background-color: #3498db; }
    .box3 { background-color: rgb(46, 204, 113); }
    .box4 { background-color: rgba(231, 76, 60, 0.7); }
    .box5 { background-color: hsl(280, 70%, 50%); }
  </style>
</head>
<body>
  <div class="box box1">Color Name: red</div>
  <div class="box box2">Hex: #3498db</div>
  <div class="box box3">RGB: rgb(46,204,113)</div>
  <div class="box box4">RGBA (transparent)</div>
  <div class="box box5">HSL: hsl(280,70%,50%)</div>
</body>
</html>
```

---

### 🎯 Which Color Format to Use?

| Format | When to Use |
|--------|-------------|
| **Hex** | Default choice, most common |
| **RGB/RGBA** | When you need transparency |
| **HSL** | When designing color schemes |
| **Names** | Quick prototypes only |

**Pro tip:** Use hex for solid colors, RGBA for transparency.

---

## 📏 PART 2: UNITS IN CSS

### Absolute Units (Fixed Size)

#### **px (Pixels)** - Most Common

```css
h1 {
  font-size: 32px;
  margin: 20px;
  width: 500px;
}
```

**Pros:**
- ✅ Precise control
- ✅ Predictable

**Cons:**
- ❌ Not responsive
- ❌ Doesn't scale with user preferences

**Use for:** Borders, shadows, small fixed values

---

### Relative Units (Scale with Context) ⭐

#### **% (Percentage)** - Relative to Parent

```css
.container {
  width: 80%;  /* 80% of parent element's width */
}

.half {
  width: 50%;  /* Half of parent's width */
}
```

**Use for:** Responsive widths, fluid layouts

---

#### **em** - Relative to Parent Font Size

```css
body {
  font-size: 16px;  /* Base */
}

h1 {
  font-size: 2em;  /* 2 × 16px = 32px */
  margin: 1em;     /* 1 × 32px = 32px (relative to h1's font size!) */
}

p {
  font-size: 1em;  /* 1 × 16px = 16px */
  margin: 0.5em;   /* 0.5 × 16px = 8px */
}
```

**Tricky:** `em` multiplies, can get confusing with nesting.

```css
div {
  font-size: 16px;
}

div p {
  font-size: 1.5em;  /* 1.5 × 16px = 24px */
}

div p span {
  font-size: 2em;  /* 2 × 24px = 48px (compounds!) */
}
```

---

#### **rem (Root Em)** - Relative to Root Font Size ⭐ BEST

```css
html {
  font-size: 16px;  /* Root */
}

h1 {
  font-size: 2rem;  /* 2 × 16px = 32px */
}

p {
  font-size: 1rem;  /* 1 × 16px = 16px */
  margin: 1.5rem;   /* 1.5 × 16px = 24px */
}
```

**Pros:**
- ✅ Consistent sizing (always relative to root)
- ✅ Easier to reason about than `em`
- ✅ Respects user font size preferences

**This is the modern standard!**

---

#### **vw / vh (Viewport Width / Height)**

```css
.hero {
  width: 100vw;   /* 100% of viewport width */
  height: 100vh;  /* 100% of viewport height */
}

.half-screen {
  height: 50vh;  /* Half of viewport height */
}
```

**Use for:** Full-screen sections, responsive typography

---

### 🎯 Units Comparison Table

| Unit | Type | Relative To | Use For |
|------|------|-------------|---------|
| `px` | Absolute | N/A | Borders, small fixed values |
| `%` | Relative | Parent element | Widths, responsive layouts |
| `em` | Relative | Parent font size | Spacing (if parent changes) |
| `rem` | Relative | Root font size | **Font sizes, spacing** ⭐ |
| `vw` | Relative | Viewport width | Full-width sections |
| `vh` | Relative | Viewport height | Full-height sections |

---

### 🎨 Modern Best Practices

```css
/* ROOT SETUP */
html {
  font-size: 16px;  /* Base size (1rem = 16px) */
}

/* TYPOGRAPHY */
h1 {
  font-size: 2.5rem;  /* 40px */
}

h2 {
  font-size: 2rem;  /* 32px */
}

p {
  font-size: 1rem;  /* 16px */
  line-height: 1.6;  /* Unitless - relative to font size */
}

/* SPACING */
.container {
  max-width: 1200px;  /* Fixed max */
  width: 90%;  /* Responsive */
  margin: 0 auto;  /* Center */
  padding: 2rem;  /* Scales with font size */
}

/* BORDERS (use px) */
.card {
  border: 1px solid #ddd;
  border-radius: 8px;
}

/* FULL-SCREEN SECTION */
.hero {
  height: 100vh;
  width: 100%;
}
```

---

### ✏️ Practice Exercise

Create `colors-units.html` with:

1. Three boxes with different color formats
2. Heading using `rem` units
3. Paragraph using responsive units
4. Container with percentage width
5. A semi-transparent overlay

<details>
<summary>Solution</summary>

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Colors & Units</title>
  <style>
    html {
      font-size: 16px;
    }

    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
    }

    .container {
      width: 80%;  /* Percentage */
      max-width: 1200px;
      margin: 0 auto;
      padding: 2rem;  /* rem */
    }

    h1 {
      font-size: 2.5rem;  /* rem */
      color: #2c3e50;  /* Hex */
      margin-bottom: 1.5rem;
    }

    p {
      font-size: 1rem;  /* rem */
      line-height: 1.6;
      color: rgb(85, 85, 85);  /* RGB */
    }

    .boxes {
      display: flex;
      gap: 1rem;
    }

    .box {
      width: 33.33%;  /* Percentage */
      padding: 2rem;
      color: white;
      text-align: center;
    }

    .box1 { background-color: #e74c3c; }  /* Hex */
    .box2 { background-color: rgb(52, 152, 219); }  /* RGB */
    .box3 { background-color: hsl(142, 71%, 45%); }  /* HSL */

    .overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;  /* Viewport width */
      height: 100vh;  /* Viewport height */
      background-color: rgba(0, 0, 0, 0.5);  /* RGBA */
      display: none;  /* Hidden by default */
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Colors & Units Demo</h1>
    <p>This page demonstrates different color formats and CSS units.</p>

    <div class="boxes">
      <div class="box box1">Hex Color</div>
      <div class="box box2">RGB Color</div>
      <div class="box box3">HSL Color</div>
    </div>
  </div>

  <!-- Overlay (toggle display to see it) -->
  <div class="overlay"></div>
</body>
</html>
```

</details>

---

## 🎯 Key Takeaways

### Colors:
1. **Five formats:** Names, Hex, RGB, RGBA, HSL
2. **Use hex for solid colors** (most common)
3. **Use RGBA for transparency** (overlays, subtle backgrounds)
4. **HSL is designer-friendly** (easy to adjust)

### Units:
1. **Use `rem` for font sizes and spacing** (modern standard)
2. **Use `%` for widths** (responsive)
3. **Use `px` for borders and small fixed values**
4. **Use `vw/vh` for viewport-based sizing**
5. **Avoid `em` unless you understand compounding**

---

## 🚀 Next Lesson

You now understand colors and units. These are essential for working with the Box Model!

**Next:** Already completed! → [Lesson 4: The Box Model](./04-box-model.md)

---

**Colors make it beautiful. Units make it precise. Together, they make it professional.** 🎨📏
