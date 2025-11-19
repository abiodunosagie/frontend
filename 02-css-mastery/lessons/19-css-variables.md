# CSS Lesson 19 - CSS Variables (Custom Properties)

> **"Reusable values that make your CSS maintainable and themeable."**

---

## 🎯 What Are CSS Variables?

CSS Variables (Custom Properties) let you store values and reuse them throughout your stylesheet.

### Basic Syntax
```css
:root {
  --variable-name: value;
}

element {
  property: var(--variable-name);
}
```

---

## 🎯 Defining Variables

### Global Variables (Most Common)
```css
:root {
  --primary-color: #3498db;
  --secondary-color: #2c3e50;
  --text-color: #333;
  --spacing: 1rem;
  --border-radius: 8px;
}
```

### Local Variables (Scoped)
```css
.card {
  --card-padding: 2rem;
  padding: var(--card-padding);
}
```

---

## 🎯 Using Variables

```css
button {
  background: var(--primary-color);
  color: var(--text-color);
  padding: var(--spacing);
  border-radius: var(--border-radius);
}

.card {
  background: var(--card-bg, white); /* Fallback value */
}
```

---

## 🎯 Common Use Cases

### Color Scheme
```css
:root {
  --color-primary: #3498db;
  --color-secondary: #2ecc71;
  --color-danger: #e74c3c;
  --color-warning: #f39c12;
  --color-success: #27ae60;
  
  --text-primary: #333;
  --text-secondary: #666;
  --text-light: #999;
  
  --bg-primary: #ffffff;
  --bg-secondary: #f8f9fa;
}
```

### Spacing Scale
```css
:root {
  --space-xs: 0.25rem;  /* 4px */
  --space-sm: 0.5rem;   /* 8px */
  --space-md: 1rem;     /* 16px */
  --space-lg: 1.5rem;   /* 24px */
  --space-xl: 2rem;     /* 32px */
}

.card {
  padding: var(--space-lg);
  margin-bottom: var(--space-md);
}
```

### Typography System
```css
:root {
  --font-base: 16px;
  --font-sm: 0.875rem;
  --font-md: 1rem;
  --font-lg: 1.25rem;
  --font-xl: 1.5rem;
  
  --font-weight-normal: 400;
  --font-weight-bold: 700;
  
  --line-height-tight: 1.2;
  --line-height-normal: 1.6;
}
```

---

## 🎯 Dark Mode with Variables

```css
:root {
  --bg: white;
  --text: #333;
}

:root.dark {
  --bg: #1a1a1a;
  --text: #f0f0f0;
}

body {
  background: var(--bg);
  color: var(--text);
  transition: all 0.3s;
}
```

```javascript
// Toggle dark mode
document.documentElement.classList.toggle('dark');
```

---

## 🎯 Complete Design System Example

```css
:root {
  /* Colors */
  --primary: #3498db;
  --secondary: #2c3e50;
  --success: #27ae60;
  --danger: #e74c3c;
  
  /* Spacing */
  --space-1: 0.25rem;
  --space-2: 0.5rem;
  --space-3: 1rem;
  --space-4: 1.5rem;
  --space-5: 2rem;
  
  /* Typography */
  --font-sans: system-ui, sans-serif;
  --font-mono: 'Courier New', monospace;
  
  /* Borders */
  --border-radius-sm: 4px;
  --border-radius-md: 8px;
  --border-radius-lg: 12px;
  
  /* Shadows */
  --shadow-sm: 0 1px 3px rgba(0,0,0,0.1);
  --shadow-md: 0 4px 6px rgba(0,0,0,0.1);
  --shadow-lg: 0 10px 25px rgba(0,0,0,0.15);
}

/* Usage */
.card {
  background: white;
  padding: var(--space-4);
  border-radius: var(--border-radius-md);
  box-shadow: var(--shadow-md);
}

.btn-primary {
  background: var(--primary);
  padding: var(--space-2) var(--space-4);
  border-radius: var(--border-radius-sm);
}
```

---

## 🎯 Dynamic Changes with JavaScript

```javascript
// Change variable value
document.documentElement.style.setProperty('--primary-color', '#e74c3c');

// Get variable value
const primary = getComputedStyle(document.documentElement)
  .getPropertyValue('--primary-color');
```

---

## 🎯 Key Takeaways

✅ Define in `:root` for global access
✅ Use meaningful names (--primary-color, not --blue)
✅ Create spacing/typography scales
✅ Perfect for theming and dark mode
✅ Can be changed with JavaScript

---

**You've completed all CSS lessons! 🎉**

**Next:** Time to practice and build real projects!
