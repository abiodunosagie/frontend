# CSS Lesson 06 - Typography

> **"Typography is 95% of web design. Master it, and your sites will look professional."**

---

## 🎯 What You'll Learn

- Font families and web-safe fonts
- Font size, weight, and style
- Line height and letter spacing
- Text alignment and decoration
- Google Fonts and custom fonts

---

## 🔤 Font Family

### Syntax
```css
font-family: "Font Name", fallback, generic;
```

### Web-Safe Fonts
```css
body {
  font-family: Arial, Helvetica, sans-serif;
}

h1 {
  font-family: Georgia, "Times New Roman", serif;
}

code {
  font-family: "Courier New", Courier, monospace;
}
```

### Font Stacks
```css
body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
}
/* System fonts - looks native on each OS */
```

---

## 📏 Font Size

### Methods
```css
/* Pixels (fixed) */
p { font-size: 16px; }

/* Relative to parent */
p { font-size: 1.2em; }

/* Relative to root (recommended) */
p { font-size: 1rem; }

/* Percentage */
p { font-size: 100%; }
```

### Recommended Sizes
```css
body { font-size: 16px; } /* Base */
h1 { font-size: 2.5rem; }  /* 40px */
h2 { font-size: 2rem; }    /* 32px */
h3 { font-size: 1.75rem; } /* 28px */
p { font-size: 1rem; }     /* 16px */
small { font-size: 0.875rem; } /* 14px */
```

---

## 💪 Font Weight

```css
p { font-weight: 400; }     /* normal */
strong { font-weight: 700; } /* bold */

/* Values: 100, 200, 300, 400, 500, 600, 700, 800, 900 */
h1 { font-weight: 300; } /* Light */
h2 { font-weight: 600; } /* Semi-bold */
```

---

## 📐 Line Height

```css
/* Unitless (recommended) - multiplies font-size */
p {
  font-size: 16px;
  line-height: 1.6; /* 16px × 1.6 = 25.6px */
}

/* Ideal for readability: 1.5 - 1.8 */
body { line-height: 1.6; }
```

---

## ✉️ Letter Spacing & Word Spacing

```css
h1 {
  letter-spacing: 2px;  /* Space between letters */
  word-spacing: 5px;    /* Space between words */
}

/* Negative values work too */
.tight {
  letter-spacing: -1px;
}
```

---

## 🎯 Text Alignment

```css
.left { text-align: left; }
.center { text-align: center; }
.right { text-align: right; }
.justify { text-align: justify; }
```

---

## 🎨 Text Decoration

```css
a {
  text-decoration: none; /* Remove underline */
}

.underline { text-decoration: underline; }
.line-through { text-decoration: line-through; }
.overline { text-decoration: overline; }
```

---

## 🌐 Google Fonts

### Step 1: Choose Font
Go to [fonts.google.com](https://fonts.google.com)

### Step 2: Add to HTML
```html
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;700&display=swap" rel="stylesheet">
```

### Step 3: Use in CSS
```css
body {
  font-family: 'Roboto', sans-serif;
}
```

---

## 🎯 Complete Example

```html
<!DOCTYPE html>
<html>
<head>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Inter', sans-serif;
      font-size: 16px;
      line-height: 1.6;
      color: #333;
      max-width: 800px;
      margin: 40px auto;
      padding: 20px;
    }

    h1 {
      font-size: 2.5rem;
      font-weight: 700;
      line-height: 1.2;
      margin-bottom: 0.5rem;
    }

    h2 {
      font-size: 2rem;
      font-weight: 600;
      margin-top: 2rem;
      margin-bottom: 1rem;
    }

    p {
      font-size: 1rem;
      margin-bottom: 1rem;
    }

    .lead {
      font-size: 1.25rem;
      font-weight: 300;
      color: #666;
    }

    code {
      font-family: 'Courier New', monospace;
      background: #f4f4f4;
      padding: 2px 6px;
      border-radius: 3px;
    }
  </style>
</head>
<body>
  <h1>Beautiful Typography</h1>
  <p class="lead">This is a lead paragraph with larger, lighter text.</p>
  <p>This is regular body text with proper spacing and readability.</p>
  <p>Use <code>code</code> tags for inline code.</p>
</body>
</html>
```

---

## 🎯 Key Takeaways

✅ Use `rem` for font sizes (scales better)
✅ Line height: 1.5-1.8 for readability
✅ Google Fonts for custom typography
✅ System fonts for best performance
✅ Font weight: 400 (normal), 700 (bold)

---

**Next:** [07 - Spacing](./07-spacing.md)
