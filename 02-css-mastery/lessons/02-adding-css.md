# Lesson 2: How to Add CSS

> **"There are three ways to add CSS. One is bad, one is good, one is best."**

---

## 🎯 The Three Ways to Add CSS

1. **Inline CSS** - Style attribute on individual elements (❌ Don't use often)
2. **Internal CSS** - `<style>` tag in the HTML file (✅ OK for small projects)
3. **External CSS** - Separate `.css` file (⭐ BEST - professional way)

Let's learn all three.

---

## 1️⃣ Inline CSS (Style Attribute)

**Syntax:**
```html
<element style="property: value; property: value;">
```

**Example:**
```html
<h1 style="color: blue; font-size: 32px;">Hello World</h1>
<p style="color: gray; margin: 20px;">This is a paragraph.</p>
```

### **Pros:**
- Quick to test one thing
- Highest specificity (overrides other CSS)

### **Cons:**
- ❌ Repeats code (have to style each element individually)
- ❌ Hard to maintain (change one color? Edit 100 places!)
- ❌ Mixes content (HTML) with presentation (CSS)
- ❌ Not professional

### **When to use:**
- Testing something quickly
- Email HTML (email clients require inline styles)
- **Never for real websites**

---

## 2️⃣ Internal CSS (`<style>` Tag)

**Syntax:**
```html
<head>
  <style>
    selector {
      property: value;
    }
  </style>
</head>
```

**Example:**
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Internal CSS</title>
  <style>
    h1 {
      color: blue;
      font-size: 32px;
    }

    p {
      color: gray;
      margin: 20px;
    }

    .highlight {
      background-color: yellow;
      padding: 10px;
    }
  </style>
</head>
<body>
  <h1>Hello World</h1>
  <p>This is a paragraph.</p>
  <p class="highlight">This is highlighted!</p>
</body>
</html>
```

### **Pros:**
- ✅ Write styles once, apply to many elements
- ✅ Everything in one file (easy for small projects)
- ✅ Good for learning

### **Cons:**
- ❌ Styles only apply to THIS page (not reusable across pages)
- ❌ Makes HTML file longer
- ❌ Can't cache styles separately

### **When to use:**
- Single-page projects
- Quick prototypes
- Learning CSS

---

## 3️⃣ External CSS (Separate File) ⭐ BEST

**Step 1: Create a CSS file** (`style.css`)

```css
/* style.css */
h1 {
  color: blue;
  font-size: 32px;
}

p {
  color: gray;
  margin: 20px;
}

.highlight {
  background-color: yellow;
  padding: 10px;
}
```

**Step 2: Link it in your HTML**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>External CSS</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1>Hello World</h1>
  <p>This is a paragraph.</p>
  <p class="highlight">This is highlighted!</p>
</body>
</html>
```

### **The `<link>` Tag:**

```html
<link rel="stylesheet" href="style.css">
```

- `rel="stylesheet"` - Tells browser this is a stylesheet
- `href="style.css"` - Path to your CSS file

### **Pros:**
- ✅ **Reusable** - One CSS file for entire website
- ✅ **Maintainable** - Change one file, updates whole site
- ✅ **Organized** - Separate concerns (HTML = content, CSS = style)
- ✅ **Cacheable** - Browser caches CSS, faster load times
- ✅ **Professional** - This is how real websites are built

### **Cons:**
- Requires two files (HTML + CSS)
- Need to understand file paths

### **When to use:**
- **ALWAYS** for real projects
- Multi-page websites
- Professional development

---

## 📁 File Structure for External CSS

```
my-project/
  ├── index.html
  ├── about.html
  ├── contact.html
  └── style.css        ← One CSS file for all pages
```

**index.html:**
```html
<link rel="stylesheet" href="style.css">
```

**about.html:**
```html
<link rel="stylesheet" href="style.css">
```

**contact.html:**
```html
<link rel="stylesheet" href="style.css">
```

**Same styles across all pages!** Change `style.css` once, updates everywhere.

---

## 📂 Understanding File Paths

### **Same Folder:**
```
my-project/
  ├── index.html
  └── style.css
```
```html
<link rel="stylesheet" href="style.css">
```

### **CSS in Subfolder:**
```
my-project/
  ├── index.html
  └── css/
      └── style.css
```
```html
<link rel="stylesheet" href="css/style.css">
```

### **HTML in Subfolder:**
```
my-project/
  ├── style.css
  └── pages/
      └── about.html
```
```html
<!-- In about.html -->
<link rel="stylesheet" href="../style.css">
```
(`../` means "go up one folder")

---

## 🎨 Real-World Example

**File: `index.html`**
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Website</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <h1>Welcome to My Website</h1>
    <nav>
      <a href="index.html">Home</a>
      <a href="about.html">About</a>
      <a href="contact.html">Contact</a>
    </nav>
  </header>

  <main>
    <h2>About Me</h2>
    <p>I'm learning frontend development!</p>
  </main>

  <footer>
    <p>&copy; 2024 My Website</p>
  </footer>
</body>
</html>
```

**File: `style.css`**
```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: Arial, sans-serif;
  line-height: 1.6;
}

header {
  background-color: #333;
  color: white;
  padding: 20px;
  text-align: center;
}

nav a {
  color: white;
  margin: 0 15px;
  text-decoration: none;
}

nav a:hover {
  color: #ddd;
}

main {
  max-width: 800px;
  margin: 40px auto;
  padding: 0 20px;
}

h2 {
  color: #333;
  margin-bottom: 20px;
}

footer {
  background-color: #f4f4f4;
  text-align: center;
  padding: 20px;
  margin-top: 40px;
}
```

**Create these two files and open `index.html` in your browser!**

---

## 🎯 Which Method Should You Use?

| Method | When to Use |
|--------|-------------|
| **Inline** | Almost never (only for testing) |
| **Internal** | Single-page projects, learning |
| **External** | ⭐ ALWAYS for real projects |

**Professional rule:** Use external CSS unless you have a very good reason not to.

---

## 💡 Comments in CSS

```css
/* This is a comment */
/* Comments help you remember what code does */

h1 {
  color: blue;  /* Make headings blue */
}

/*
  Multi-line comment
  You can write notes here
  Very useful!
*/

p {
  font-size: 16px;
}
```

**Use comments to:**
- Explain complex code
- Organize sections
- Leave notes for future you (or teammates)

---

## ✏️ Practice Exercise

Create a project with external CSS:

1. Create folder `my-site`
2. Inside, create `index.html`
3. Inside, create `style.css`
4. In `index.html`:
   - Add basic HTML structure
   - Add heading, paragraph, link
   - Link to `style.css`
5. In `style.css`:
   - Style the heading (color, size)
   - Style the paragraph (color, line-height)
   - Style the link (color, remove underline)

<details>
<summary>Solution</summary>

**index.html:**
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Site</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1>Welcome to My Site</h1>
  <p>This is a paragraph with some text. I'm learning CSS!</p>
  <a href="#">Click this link</a>
</body>
</html>
```

**style.css:**
```css
body {
  font-family: Arial, sans-serif;
  padding: 20px;
}

h1 {
  color: #2c3e50;
  font-size: 36px;
}

p {
  color: #555;
  line-height: 1.8;
  font-size: 18px;
}

a {
  color: #3498db;
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}
```

</details>

---

## 🐛 Common Mistakes

### **1. Forgetting the `<link>` tag**
```html
<!-- Wrong - forgot to link CSS -->
<head>
  <title>My Page</title>
</head>

<!-- Right -->
<head>
  <title>My Page</title>
  <link rel="stylesheet" href="style.css">
</head>
```

### **2. Wrong file path**
```html
<!-- Wrong - file is in css/ folder -->
<link rel="stylesheet" href="style.css">

<!-- Right -->
<link rel="stylesheet" href="css/style.css">
```

### **3. Typo in filename**
```
Files:
  - index.html
  - styles.css  ← Note the 's'

HTML:
<link rel="stylesheet" href="style.css">  ← Wrong! Missing 's'
```

**File names are case-sensitive! `style.css` ≠ `Style.css`**

---

## 🎯 Key Takeaways

1. **Three ways to add CSS:** Inline, Internal, External
2. **Use external CSS** for real projects (professional standard)
3. **`<link rel="stylesheet" href="style.css">`** in the `<head>`
4. **File paths matter** - make sure they're correct
5. **One CSS file** can style multiple HTML pages
6. **Comments help** - use `/* comment */`

---

## 🚀 Next Lesson

Now you know how to add CSS. Next, you'll learn **selectors** - how to target specific elements to style.

**Next:** [Lesson 3: Selectors Deep Dive →](./03-selectors.md)

---

**Always use external CSS. It's the professional way.** 📁
