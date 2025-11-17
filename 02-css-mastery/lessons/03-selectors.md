# Lesson 3: CSS Selectors - Targeting Elements

> **"Selectors are how you tell CSS: 'Style THIS element, not that one.'"**

---

## 🎯 What are Selectors?

**Selectors choose which HTML elements get styled.**

Think of it like a spotlight at a concert:
- The spotlight (selector) points at specific performers (elements)
- Only the performers in the spotlight get lit up (styled)

```css
h1 {  ← SELECTOR (which elements?)
  color: blue;  ← What happens to them
}
```

---

## 🎨 The Five Essential Selectors

### 1. **Element Selector** - Style ALL elements of a type

```css
p {
  color: gray;
}
```

**Targets:** Every `<p>` element on the page

```html
<p>This will be gray</p>
<p>This will also be gray</p>
<p>And this too!</p>
```

### 2. **Class Selector** - Style elements with a specific class

```css
.highlight {
  background-color: yellow;
}
```

**Targets:** Any element with `class="highlight"`

```html
<p class="highlight">This has yellow background</p>
<div class="highlight">This too!</div>
<p>This doesn't (no class)</p>
```

**Class selector starts with a dot (`.`)**

### 3. **ID Selector** - Style ONE specific element

```css
#header {
  background-color: navy;
}
```

**Targets:** The ONE element with `id="header"`

```html
<div id="header">Only this element</div>
```

**ID selector starts with a hash (`#`)**

**Rule:** IDs must be unique on a page. Only ONE element can have `id="header"`.

### 4. **Universal Selector** - Style EVERYTHING

```css
* {
  margin: 0;
  padding: 0;
}
```

**Targets:** Every single element on the page

### 5. **Grouping Selector** - Style multiple elements the same way

```css
h1, h2, h3 {
  color: navy;
  font-family: Arial;
}
```

**Targets:** All `<h1>`, `<h2>`, and `<h3>` elements

---

## 🎯 Class vs ID - When to Use Which?

| Class | ID |
|-------|-----|
| Reusable (many elements) | Unique (one element) |
| Starts with `.` | Starts with `#` |
| `class="button"` | `id="submit-btn"` |
| **Use 95% of the time** | Use rarely |

**Example:**

```html
<!-- Classes (reusable) -->
<button class="btn">Save</button>
<button class="btn">Cancel</button>
<button class="btn">Delete</button>

<!-- ID (unique) -->
<header id="main-header">Only one header</header>
```

```css
/* Style all buttons the same */
.btn {
  padding: 10px 20px;
  background-color: blue;
  color: white;
  border: none;
}

/* Style one specific element */
#main-header {
  position: sticky;
  top: 0;
}
```

**Pro tip:** Use classes for almost everything. IDs for unique page elements (header, footer, main navigation).

---

## 🎨 Advanced Selectors

### **Descendant Selector** - Elements inside other elements

```css
div p {
  color: gray;
}
```

**Targets:** `<p>` elements inside `<div>` elements

```html
<div>
  <p>This will be gray (inside div)</p>
</div>

<p>This won't be gray (not inside div)</p>
```

### **Child Selector** - Direct children only

```css
div > p {
  color: gray;
}
```

**Targets:** `<p>` elements that are DIRECT children of `<div>`

```html
<div>
  <p>Gray (direct child)</p>
  <section>
    <p>NOT gray (not direct child, nested deeper)</p>
  </section>
</div>
```

### **Multiple Classes** - Element has ALL these classes

```css
.btn.primary {
  background-color: blue;
}
```

**Targets:** Elements with BOTH `class="btn"` AND `class="primary"`

```html
<button class="btn primary">Styled (has both)</button>
<button class="btn">Not styled (only has btn)</button>
<button class="primary">Not styled (only has primary)</button>
```

### **Attribute Selector** - Elements with specific attributes

```css
input[type="text"] {
  border: 1px solid gray;
}

a[href^="https"] {
  color: green;
}
```

**Targets:**
- First rule: `<input type="text">`
- Second rule: Links starting with "https"

---

## 🎯 Pseudo-Classes - Style based on state

```css
a:hover {
  color: red;  /* When mouse hovers over link */
}

button:active {
  transform: scale(0.95);  /* When button is clicked */
}

input:focus {
  border-color: blue;  /* When input is selected */
}

li:first-child {
  font-weight: bold;  /* First list item */
}

li:last-child {
  border-bottom: none;  /* Last list item */
}

p:nth-child(2) {
  color: blue;  /* Second paragraph */
}
```

**Common pseudo-classes:**
- `:hover` - Mouse is over element
- `:active` - Element is being clicked
- `:focus` - Element is selected (for inputs, buttons)
- `:first-child` - First child of parent
- `:last-child` - Last child of parent
- `:nth-child(n)` - Nth child of parent

---

## 🎨 Pseudo-Elements - Style part of an element

```css
p::first-line {
  font-weight: bold;  /* Only first line of paragraph */
}

p::first-letter {
  font-size: 2em;  /* Drop cap effect */
  float: left;
}

p::before {
  content: "→ ";  /* Add content before paragraph */
  color: blue;
}

p::after {
  content: " ←";  /* Add content after paragraph */
  color: blue;
}
```

**Notice: Double colon (`::`) for pseudo-elements**

---

## 🎯 Specificity - Which Style Wins?

When multiple rules target the same element, **specificity** decides which wins.

### **Specificity Hierarchy (Strongest to Weakest):**

1. **Inline styles** (highest)
2. **IDs**
3. **Classes, attributes, pseudo-classes**
4. **Elements, pseudo-elements**
5. **Universal selector** (lowest)

### **Examples:**

```html
<p id="intro" class="highlight" style="color: purple;">Text</p>
```

```css
p { color: blue; }              /* Weakest */
.highlight { color: yellow; }   /* Stronger */
#intro { color: green; }        /* Even stronger */
/* style="color: purple;" */    /* WINS - inline is strongest */
```

**Result:** Text is purple (inline style wins)

### **Calculating Specificity:**

Think of it as a point system:
- Inline style = 1000 points
- ID = 100 points
- Class/attribute/pseudo-class = 10 points
- Element/pseudo-element = 1 point

```css
p { ... }                    /* 1 point */
.intro { ... }               /* 10 points */
#header { ... }              /* 100 points */
div p { ... }                /* 2 points (1 + 1) */
div .intro { ... }           /* 11 points (1 + 10) */
div#header p.intro { ... }   /* 112 points (1 + 100 + 1 + 10) */
```

**Higher points = wins**

---

## ✏️ Practice Exercise

Create `selectors-practice.html`:

**Requirements:**
1. Style all `<h2>` elements blue
2. Create a class `.card` with padding and border
3. Create a class `.highlight` with yellow background
4. Style links to change color on hover
5. Make the first paragraph bold using `:first-child`

<details>
<summary>Solution</summary>

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Selectors Practice</title>
  <style>
    /* 1. All h2 elements */
    h2 {
      color: blue;
    }

    /* 2. Card class */
    .card {
      padding: 20px;
      border: 1px solid #ddd;
      margin-bottom: 20px;
    }

    /* 3. Highlight class */
    .highlight {
      background-color: yellow;
    }

    /* 4. Link hover */
    a {
      color: blue;
      text-decoration: none;
    }

    a:hover {
      color: red;
      text-decoration: underline;
    }

    /* 5. First paragraph */
    p:first-child {
      font-weight: bold;
    }
  </style>
</head>
<body>
  <h2>Section 1</h2>
  <p>This is the first paragraph (should be bold).</p>
  <p class="highlight">This is highlighted.</p>

  <div class="card">
    <h2>Card Title</h2>
    <p>Card content goes here.</p>
    <a href="#">Hover over this link</a>
  </div>

  <div class="card highlight">
    <h2>Another Card</h2>
    <p>This card is also highlighted!</p>
  </div>
</body>
</html>
```

</details>

---

## 🎯 Selector Best Practices

### ✅ **DO:**
- Use classes for styling (most flexible)
- Use meaningful class names (`.button-primary`, not `.blue-button`)
- Keep selectors simple
- Use descendant selectors sparingly

### ❌ **DON'T:**
- Over-use IDs for styling (use classes instead)
- Make selectors too specific (`div > ul > li > a` is overkill)
- Use inline styles (except for JavaScript manipulation)
- Use `!important` (it breaks specificity - only use as last resort)

---

## 🎨 Real-World Example

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Card Layout</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: Arial, sans-serif;
      padding: 20px;
      background-color: #f5f5f5;
    }

    .container {
      max-width: 1200px;
      margin: 0 auto;
    }

    .card {
      background: white;
      border-radius: 8px;
      padding: 20px;
      margin-bottom: 20px;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    }

    .card h2 {
      color: #333;
      margin-bottom: 10px;
    }

    .card p {
      color: #666;
      line-height: 1.6;
    }

    .card-primary {
      border-left: 4px solid #3498db;
    }

    .card-success {
      border-left: 4px solid #2ecc71;
    }

    .btn {
      display: inline-block;
      padding: 10px 20px;
      background-color: #3498db;
      color: white;
      text-decoration: none;
      border-radius: 4px;
      margin-top: 10px;
    }

    .btn:hover {
      background-color: #2980b9;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="card card-primary">
      <h2>Primary Card</h2>
      <p>This is a primary card with important information.</p>
      <a href="#" class="btn">Learn More</a>
    </div>

    <div class="card card-success">
      <h2>Success Card</h2>
      <p>This card shows a successful action or status.</p>
      <a href="#" class="btn">Continue</a>
    </div>

    <div class="card">
      <h2>Regular Card</h2>
      <p>This is a standard card without special styling.</p>
    </div>
  </div>
</body>
</html>
```

**Notice:**
- Classes are reusable (`.card`, `.btn`)
- Multiple classes on one element (`.card.card-primary`)
- Descendant selectors (`.card h2`, `.card p`)
- Pseudo-class for interaction (`.btn:hover`)

---

## 🎯 Key Takeaways

1. **Selectors choose which elements to style**
2. **Five main types:** Element, Class, ID, Universal, Grouping
3. **Use classes for most styling** (most flexible)
4. **IDs are unique** (use sparingly)
5. **Specificity determines which style wins**
6. **Pseudo-classes style states** (`:hover`, `:focus`, etc.)
7. **Keep selectors simple** (easier to maintain)

---

## 🚀 Next Lesson

Now you know how to target elements. Next, you'll learn the **Box Model** - the most important concept in CSS layout.

**Next:** [Lesson 4: The Box Model →](./04-box-model.md)

---

**Selectors are your targeting system. Master them, and you can style anything.** 🎯
