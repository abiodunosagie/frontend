# Lesson 4: Links - Connecting the Web

> **"Links are what make it a 'web'. Without links, it's just isolated documents."**

---

## 🌐 What are Links?

**Links (hyperlinks) connect pages together.**

Click a link → go to another page. That's the foundation of the World Wide Web.

---

## 🔗 The `<a>` Tag (Anchor)

**Syntax:**
```html
<a href="destination">Link Text</a>
```

**Example:**
```html
<a href="https://google.com">Go to Google</a>
```

**Parts:**
- `<a>` = Anchor tag
- `href` = "Hypertext reference" (where to go)
- `Link Text` = What user clicks on

---

## 🎯 Types of Links

### 1. **External Links** (Other websites)

```html
<a href="https://google.com">Google</a>
<a href="https://github.com">GitHub</a>
```

**Always include `https://` for external links!**

---

### 2. **Internal Links** (Your own pages)

```html
<!-- Same folder -->
<a href="about.html">About Us</a>
<a href="contact.html">Contact</a>

<!-- Subfolder -->
<a href="pages/blog.html">Blog</a>

<!-- Parent folder -->
<a href="../index.html">Home</a>
```

**File structure:**
```
my-site/
  ├── index.html
  ├── about.html
  └── pages/
      └── blog.html
```

---

### 3. **Anchor Links** (Same page, different section)

```html
<a href="#section1">Jump to Section 1</a>
<a href="#footer">Jump to Footer</a>

<!-- Later on the page: -->
<section id="section1">
  <h2>Section 1</h2>
  <p>Content here...</p>
</section>

<footer id="footer">
  <p>Footer content</p>
</footer>
```

**Use `#` + the element's `id`**

---

### 4. **Email Links** (Opens email client)

```html
<a href="mailto:hello@example.com">Email Us</a>
```

**With subject and body:**
```html
<a href="mailto:hello@example.com?subject=Question&body=Hello!">Email with Subject</a>
```

---

### 5. **Phone Links** (Calls on mobile)

```html
<a href="tel:+1234567890">Call Us</a>
```

---

## 🎨 Link Attributes

### **target** - Where to open link

```html
<!-- Same tab (default) -->
<a href="https://google.com">Google</a>

<!-- New tab -->
<a href="https://google.com" target="_blank">Google (new tab)</a>
```

**Options:**
- `_self` - Same tab (default)
- `_blank` - New tab
- `_parent` - Parent frame
- `_top` - Full window

**Security note:** When using `target="_blank"`, add `rel="noopener noreferrer"`:

```html
<a href="https://external-site.com" target="_blank" rel="noopener noreferrer">
  External Site
</a>
```

---

### **title** - Tooltip on hover

```html
<a href="about.html" title="Learn more about us">About</a>
```

Hover over the link → see "Learn more about us" tooltip.

---

### **download** - Download file instead of navigating

```html
<a href="resume.pdf" download>Download Resume</a>
```

---

## 🎨 Styling Links with CSS

**Default link styles:**
- Blue and underlined (unvisited)
- Purple and underlined (visited)

**Custom styling:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Styled Links</title>
  <style>
    /* Default state */
    a {
      color: #3498db;
      text-decoration: none;  /* Remove underline */
      font-weight: bold;
    }

    /* Hover state */
    a:hover {
      color: #2980b9;
      text-decoration: underline;
    }

    /* Visited state */
    a:visited {
      color: #9b59b6;
    }

    /* Active (being clicked) */
    a:active {
      color: #e74c3c;
    }

    /* Focus (keyboard navigation) */
    a:focus {
      outline: 2px solid #3498db;
    }
  </style>
</head>
<body>
  <a href="https://google.com">Click me!</a>
</body>
</html>
```

---

## 🎯 Link States (Pseudo-classes)

```css
a:link      { }  /* Unvisited link */
a:visited   { }  /* Visited link */
a:hover     { }  /* Mouse over */
a:active    { }  /* Being clicked */
a:focus     { }  /* Keyboard focus */
```

**Order matters! Remember: LVHFA**
- **L**ink
- **V**isited
- **H**over
- **F**ocus
- **A**ctive

---

## 🎨 Button-Style Links

```html
<style>
  .btn {
    display: inline-block;
    padding: 12px 24px;
    background-color: #3498db;
    color: white;
    text-decoration: none;
    border-radius: 5px;
    font-weight: bold;
  }

  .btn:hover {
    background-color: #2980b9;
  }
</style>

<a href="signup.html" class="btn">Sign Up Now</a>
```

---

## 📱 Navigation Menu Example

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Navigation Demo</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    nav {
      background-color: #333;
      padding: 1rem;
    }

    nav ul {
      list-style: none;
      display: flex;
      gap: 2rem;
    }

    nav a {
      color: white;
      text-decoration: none;
      font-size: 1.1rem;
    }

    nav a:hover {
      color: #3498db;
    }
  </style>
</head>
<body>
  <nav>
    <ul>
      <li><a href="index.html">Home</a></li>
      <li><a href="about.html">About</a></li>
      <li><a href="services.html">Services</a></li>
      <li><a href="contact.html">Contact</a></li>
    </ul>
  </nav>

  <main>
    <h1>Welcome to Our Site</h1>
    <p>Use the navigation above to explore.</p>
  </main>
</body>
</html>
```

---

## ✏️ Practice Exercise

Create `links-practice.html`:

1. External link to your favorite website (opens in new tab)
2. Email link with your email
3. Three internal links (create dummy pages if needed)
4. An anchor link that jumps to the bottom of the page
5. Style all links (remove underline, change color, add hover effect)

<details>
<summary>Solution</summary>

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Links Practice</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      line-height: 1.6;
      padding: 20px;
      max-width: 800px;
      margin: 0 auto;
    }

    a {
      color: #2c3e50;
      text-decoration: none;
      font-weight: bold;
      border-bottom: 2px solid transparent;
      transition: border-color 0.3s;
    }

    a:hover {
      border-bottom-color: #3498db;
    }

    section {
      margin-bottom: 40px;
    }

    #bottom {
      margin-top: 100vh;
      padding: 20px;
      background-color: #f0f0f0;
    }
  </style>
</head>
<body>
  <h1>Links Practice Page</h1>

  <section>
    <h2>External Link</h2>
    <p>
      Visit
      <a href="https://developer.mozilla.org" target="_blank" rel="noopener noreferrer">
        MDN Web Docs
      </a>
      for web development resources.
    </p>
  </section>

  <section>
    <h2>Email Link</h2>
    <p>
      Contact me at
      <a href="mailto:your.email@example.com">your.email@example.com</a>
    </p>
  </section>

  <section>
    <h2>Internal Links</h2>
    <nav>
      <ul>
        <li><a href="index.html">Home</a></li>
        <li><a href="about.html">About</a></li>
        <li><a href="contact.html">Contact</a></li>
      </ul>
    </nav>
  </section>

  <section>
    <h2>Anchor Link</h2>
    <p><a href="#bottom">Jump to bottom of page</a></p>
  </section>

  <div id="bottom">
    <h2>Bottom of Page</h2>
    <p>You jumped here! <a href="#top">Back to top</a></p>
  </div>
</body>
</html>
```

</details>

---

## 🐛 Common Mistakes

### 1. **Forgetting `href`**
```html
<!-- Wrong -->
<a>Click here</a>

<!-- Right -->
<a href="page.html">Click here</a>
```

### 2. **Wrong file paths**
```html
<!-- Wrong (file is in subfolder) -->
<a href="about.html">About</a>

<!-- Right -->
<a href="pages/about.html">About</a>
```

### 3. **Using "click here" as link text**
```html
<!-- Bad -->
<a href="article.html">Click here</a> to read more.

<!-- Good -->
<a href="article.html">Read the full article</a>.
```

**Accessibility tip:** Link text should make sense out of context!

---

## 🎯 Key Takeaways

1. **Links use `<a>` tag** with `href` attribute
2. **External links** need full URL with `https://`
3. **Internal links** use relative paths
4. **Anchor links** use `#id` to jump to sections
5. **`target="_blank"`** opens in new tab (add `rel="noopener noreferrer"`)
6. **Style links** with `:hover`, `:visited`, `:active`, `:focus`
7. **Link text should be descriptive** (not "click here")

---

## 🚀 Next Lesson

Now you can connect pages. Next, learn how to add **images** to make pages visual!

**Next:** [Lesson 5: Images & Media →](./05-images-media.md)

---

**Links connect the web. Master them, and you understand the foundation of the internet.** 🔗
