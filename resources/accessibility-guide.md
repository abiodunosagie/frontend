# Web Accessibility (a11y) - Essential Guide

> **"Accessibility is not a feature. It's a fundamental right."**

Building accessible websites means **everyone** can use them - including people with disabilities.

---

## 🎯 Why Accessibility Matters

### The Reality:
- **1 in 4 adults** has some type of disability
- **71 million people** use screen readers
- **Lawsuits happen** for inaccessible websites (ADA compliance)
- **Better UX** for everyone (not just disabled users)
- **Better SEO** (search engines love semantic HTML)

**Plus, it's the right thing to do.**

---

## ♿ Types of Disabilities to Consider

1. **Visual** - Blind, low vision, color blind
2. **Hearing** - Deaf or hard of hearing
3. **Motor** - Can't use a mouse, limited dexterity
4. **Cognitive** - Learning disabilities, memory issues

**Your website should work for all of them.**

---

## 🎯 The Four Principles (POUR)

### 1. **Perceivable**
Information must be presented in ways users can perceive.
- Images need alt text
- Videos need captions
- Good color contrast

### 2. **Operable**
Users must be able to operate the interface.
- Keyboard navigation works
- Enough time to read/use content
- No seizure-inducing flashes

### 3. **Understandable**
Information and operation must be understandable.
- Clear, simple language
- Predictable navigation
- Error messages make sense

### 4. **Robust**
Content works with current and future technologies.
- Valid HTML
- Works with assistive technologies
- Progressive enhancement

---

## 🎨 Essential Accessibility Practices

### 1. **Semantic HTML** (Foundation of Accessibility)

```html
<!-- Bad: No meaning -->
<div class="header">
  <div class="nav">
    <div class="link">Home</div>
  </div>
</div>

<!-- Good: Semantic meaning -->
<header>
  <nav>
    <a href="/">Home</a>
  </nav>
</header>
```

**Screen readers understand semantic HTML!**

**Semantic elements:**
- `<header>` - Page/section header
- `<nav>` - Navigation links
- `<main>` - Main content (only one per page!)
- `<article>` - Self-contained content
- `<section>` - Thematic grouping
- `<aside>` - Sidebar content
- `<footer>` - Page/section footer
- `<button>` - Clickable button
- `<form>` - User input form

---

### 2. **Alt Text for Images**

```html
<!-- Bad: No alt text -->
<img src="dog.jpg">

<!-- Bad: Meaningless alt text -->
<img src="dog.jpg" alt="image">

<!-- Good: Descriptive alt text -->
<img src="dog.jpg" alt="Golden retriever playing fetch in a park">

<!-- Decorative images: Empty alt -->
<img src="decorative-line.png" alt="">
```

**Rules:**
- Describe what's in the image
- Keep it concise (< 125 characters)
- Don't say "image of" (screen readers already say "image")
- Decorative images get empty alt (`alt=""`)

---

### 3. **Keyboard Navigation**

**All functionality must work with keyboard only** (no mouse).

**Standard keyboard controls:**
- `Tab` - Move to next interactive element
- `Shift + Tab` - Move to previous element
- `Enter` - Activate buttons/links
- `Space` - Activate buttons, scroll page
- `Arrow keys` - Navigate menus, radio buttons

```html
<!-- Bad: Div with click handler (not keyboard accessible) -->
<div onclick="doSomething()">Click me</div>

<!-- Good: Button (keyboard accessible) -->
<button onclick="doSomething()">Click me</button>
```

**Test it yourself:** Try using your website with Tab key only!

---

### 4. **Color Contrast**

**Text must be readable against its background.**

**WCAG Standards:**
- **Normal text:** 4.5:1 contrast ratio minimum
- **Large text (18px+ or bold 14px+):** 3:1 minimum

```css
/* Bad: Poor contrast */
.text {
  color: #ccc;  /* Light gray */
  background: white;
}

/* Good: High contrast */
.text {
  color: #333;  /* Dark gray */
  background: white;
}
```

**Tools to check:**
- https://webaim.org/resources/contrastchecker/
- Chrome DevTools (Inspect element → Accessibility panel)

---

### 5. **Form Labels**

```html
<!-- Bad: No label -->
<input type="text" placeholder="Name">

<!-- Good: Proper label -->
<label for="name">Name</label>
<input type="text" id="name">

<!-- Also good: Wrapped label -->
<label>
  Name
  <input type="text">
</label>
```

**Every form input needs a label!** (Not just placeholder)

---

### 6. **Focus Indicators**

```css
/* Bad: Removing focus outline */
button:focus {
  outline: none;  /* DON'T DO THIS! */
}

/* Good: Custom focus style */
button:focus {
  outline: 2px solid blue;
  outline-offset: 2px;
}

/* Better: Modern focus-visible */
button:focus-visible {
  outline: 2px solid blue;
  outline-offset: 2px;
}
```

**Users need to see what's focused!**

---

### 7. **Link Text**

```html
<!-- Bad: Non-descriptive -->
<a href="/about">Click here</a>
<a href="/products">Read more</a>

<!-- Good: Descriptive -->
<a href="/about">About our company</a>
<a href="/products">View our products</a>
```

**Link text should make sense out of context.**

---

### 8. **Headings Hierarchy**

```html
<!-- Bad: Skipping levels -->
<h1>Page Title</h1>
<h3>Section</h3>  <!-- Skipped h2! -->

<!-- Good: Logical order -->
<h1>Page Title</h1>
<h2>Main Section</h2>
<h3>Subsection</h3>
<h3>Another Subsection</h3>
<h2>Another Main Section</h2>
```

**Rules:**
- Only one `<h1>` per page
- Don't skip heading levels
- Use headings for structure, not styling

---

### 9. **ARIA Labels** (When Semantic HTML Isn't Enough)

**ARIA = Accessible Rich Internet Applications**

```html
<!-- Icon button needs label -->
<button aria-label="Close menu">
  <span>✕</span>
</button>

<!-- Loading state -->
<div aria-live="polite" aria-busy="true">
  Loading...
</div>

<!-- Hidden content that screen readers should read -->
<span class="visually-hidden">
  Navigate to home page
</span>
```

**Common ARIA attributes:**
- `aria-label` - Label for elements without text
- `aria-labelledby` - Points to element that labels this one
- `aria-describedby` - Points to element that describes this one
- `aria-hidden` - Hide from screen readers
- `aria-live` - Announce dynamic content changes

---

### 10. **Skip Links** (For Keyboard Users)

```html
<body>
  <!-- Skip link (visually hidden until focused) -->
  <a href="#main-content" class="skip-link">
    Skip to main content
  </a>

  <header>
    <nav>
      <!-- Long navigation menu -->
    </nav>
  </header>

  <main id="main-content">
    <!-- Main content -->
  </main>
</body>
```

```css
.skip-link {
  position: absolute;
  top: -40px;
  left: 0;
  background: #000;
  color: #fff;
  padding: 8px;
  z-index: 100;
}

.skip-link:focus {
  top: 0;  /* Shows when focused */
}
```

**Keyboard users can skip long navigation!**

---

## ✏️ Quick Accessibility Checklist

Before launching any website:

### Basics
- [ ] All images have alt text
- [ ] All form inputs have labels
- [ ] Headings are in logical order (h1 → h2 → h3)
- [ ] Links have descriptive text (not "click here")
- [ ] Semantic HTML used (header, nav, main, etc.)

### Interaction
- [ ] Everything works with keyboard only
- [ ] Focus indicators visible
- [ ] Skip link for keyboard users
- [ ] No keyboard traps (can Tab away from all elements)

### Visual
- [ ] Text has sufficient color contrast
- [ ] Font size at least 16px
- [ ] Don't rely on color alone to convey information
- [ ] Content doesn't flash more than 3 times per second

### Testing
- [ ] Test with keyboard only (no mouse)
- [ ] Test with screen reader (NVDA on Windows, VoiceOver on Mac)
- [ ] Run automated tests (Lighthouse, axe DevTools)
- [ ] Zoom to 200% - still usable?

---

## 🛠️ Testing Tools

### 1. **Chrome Lighthouse**
Press F12 → Lighthouse tab → Run audit → Check Accessibility score

### 2. **Screen Readers**
- **Windows:** NVDA (free) - https://www.nvaccess.org/
- **Mac:** VoiceOver (built-in) - Cmd + F5
- **Test your site with one!**

### 3. **Browser Extensions**
- **axe DevTools** - Automated accessibility testing
- **WAVE** - Visual feedback about accessibility

### 4. **Keyboard Testing**
Just use Tab key and see if you can use your entire site!

---

## 🎨 Practical Example: Accessible Card Component

```html
<article class="card">
  <img src="product.jpg" alt="Blue ceramic coffee mug with white handle">

  <div class="card-content">
    <h2>Ceramic Coffee Mug</h2>

    <p>
      Handcrafted ceramic mug with a smooth glaze finish.
      Perfect for your morning coffee.
    </p>

    <div class="price" aria-label="Price">
      <span aria-hidden="true">$</span>
      <span>24.99</span>
    </div>

    <button aria-label="Add Ceramic Coffee Mug to cart">
      Add to Cart
    </button>
  </div>
</article>
```

```css
.card {
  /* Visual styles */
  border: 1px solid #ddd;
  border-radius: 8px;
  overflow: hidden;
}

.card:focus-within {
  outline: 2px solid blue;  /* Show focus when card has focus */
}

.card img {
  width: 100%;
  height: auto;  /* Maintains aspect ratio */
}

.card button:focus-visible {
  outline: 2px solid #007bff;
  outline-offset: 2px;
}

/* Utility class for visually hidden but screen-reader accessible text */
.visually-hidden {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border-width: 0;
}
```

---

## 🎯 Key Takeaways

1. **Use semantic HTML** (foundation of accessibility)
2. **Alt text for all images** (descriptive, concise)
3. **Keyboard navigation must work** (test with Tab!)
4. **Color contrast matters** (4.5:1 minimum)
5. **Label all form inputs** (not just placeholders)
6. **Test with screen readers** (at least once!)
7. **Focus indicators are required** (don't remove them!)
8. **Accessibility benefits everyone** (better UX for all)

---

## 📚 Learn More

- **WCAG Guidelines:** https://www.w3.org/WAI/WCAG21/quickref/
- **WebAIM:** https://webaim.org/
- **A11y Project:** https://www.a11yproject.com/
- **MDN Accessibility:** https://developer.mozilla.org/en-US/docs/Web/Accessibility

---

**Accessibility isn't optional. It's professional responsibility. Build for everyone.** ♿
