# CSS Lesson 09 - Display & Positioning

> **"Understanding how elements flow and position is crucial for layouts."**

---

## 🎯 Display Property

### block
```css
div { display: block; }
/* Takes full width, starts on new line */
/* Examples: div, p, h1, section */
```

### inline
```css
span { display: inline; }
/* Takes only needed width, stays on same line */
/* Cannot set width/height */
/* Examples: span, a, strong, em */
```

### inline-block
```css
button { display: inline-block; }
/* Inline but can have width/height */
/* Best of both worlds */
```

### none
```css
.hidden { display: none; }
/* Completely removes from page */
```

### Example
```html
<style>
  .block { display: block; background: lightblue; }
  .inline { display: inline; background: lightgreen; }
  .inline-block { display: inline-block; background: lightcoral; width: 100px; height: 50px; }
</style>

<div class="block">Block</div>
<span class="inline">Inline</span>
<span class="inline-block">Inline-Block</span>
```

---

## 🎯 Position Property

### static (default)
```css
div { position: static; }
/* Normal document flow */
```

### relative
```css
div {
  position: relative;
  top: 20px;    /* Moves down from original position */
  left: 10px;   /* Moves right from original position */
}
/* Element still takes up original space */
```

### absolute
```css
div {
  position: absolute;
  top: 0;
  right: 0;
}
/* Removed from flow, positioned relative to nearest positioned ancestor */
```

### fixed
```css
nav {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
}
/* Stays in place when scrolling */
```

### sticky
```css
.sidebar {
  position: sticky;
  top: 20px;
}
/* Scrolls normally until reaching specified position, then sticks */
```

---

## 🎯 Z-Index (Stacking Order)

```css
.modal {
  position: fixed;
  z-index: 100; /* Higher = on top */
}

.overlay {
  position: fixed;
  z-index: 50;
}
```

**Note:** Only works on positioned elements (not static)

---

## 🎯 Common Patterns

### Centered Modal
```css
.modal {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 1000;
}
```

### Sticky Header
```css
header {
  position: sticky;
  top: 0;
  background: white;
  z-index: 100;
}
```

### Badge on Corner
```css
.card {
  position: relative;
}

.badge {
  position: absolute;
  top: 10px;
  right: 10px;
}
```

---

## 🎯 Complete Example

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body { margin: 0; padding-top: 60px; }

    nav {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      background: #333;
      color: white;
      padding: 20px;
      z-index: 100;
    }

    .container {
      max-width: 800px;
      margin: 0 auto;
      padding: 20px;
    }

    .card {
      position: relative;
      background: white;
      padding: 20px;
      margin-bottom: 20px;
      border: 1px solid #ddd;
    }

    .new-badge {
      position: absolute;
      top: -10px;
      right: -10px;
      background: red;
      color: white;
      padding: 5px 10px;
      border-radius: 20px;
      font-size: 12px;
    }
  </style>
</head>
<body>
  <nav>Fixed Navigation</nav>

  <div class="container">
    <div class="card">
      <span class="new-badge">NEW</span>
      <h2>Card Title</h2>
      <p>Content here...</p>
    </div>
  </div>
</body>
</html>
```

---

## 🎯 Key Takeaways

✅ **block** - Full width, new line
✅ **inline-block** - Inline but can have dimensions
✅ **position: relative** - Move from original position
✅ **position: absolute** - Remove from flow
✅ **position: fixed** - Stays on screen when scrolling
✅ **position: sticky** - Scrolls then sticks

---

**Next:** [10 - Flexbox](./10-flexbox.md) (already complete!)
