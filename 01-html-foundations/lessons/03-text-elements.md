# Lesson 3: Text Elements - Headings, Paragraphs, and Formatting

> **"Most of the web is text. Learn to structure it properly."**

---

## 🎯 Text is the Foundation of the Web

Before images, videos, and fancy animations, the web was (and still is) mostly **text**.

Learning to structure text properly is essential.

---

## 📝 Headings (`<h1>` to `<h6>`)

### What are Headings?

Headings create a **hierarchy** of importance - like an outline.

```html
<h1>Main Title</h1>
<h2>Section Title</h2>
<h3>Subsection Title</h3>
<h4>Sub-subsection</h4>
<h5>Smaller heading</h5>
<h6>Smallest heading</h6>
```

**Visual result:**
# Main Title
## Section Title
### Subsection Title
#### Sub-subsection
##### Smaller heading
###### Smallest heading

---

### Rules for Headings:

1. **Only ONE `<h1>` per page** (the main title)
2. **Don't skip levels** (don't jump from h1 to h3)
3. **Use for structure, not styling** (don't use h1 just because it's big)

**Good:**
```html
<h1>My Blog Post</h1>
<h2>Introduction</h2>
<p>...</p>
<h2>Main Content</h2>
<h3>First Point</h3>
<p>...</p>
<h3>Second Point</h3>
<p>...</p>
```

**Bad:**
```html
<h1>Page Title</h1>
<h1>Another Title</h1>  ← BAD! Only one h1
<h4>Skipped h2 and h3!</h4>  ← BAD! Don't skip levels
```

---

## 📄 Paragraphs (`<p>`)

Paragraphs are blocks of text.

```html
<p>This is a paragraph of text.</p>
<p>This is another paragraph.</p>
```

**Browsers automatically add space between paragraphs.**

---

## 💪 Text Formatting (Semantic Meaning)

### **Strong Importance** (`<strong>`)

```html
<p>This is <strong>very important</strong> text.</p>
```

**Result:** This is **very important** text.

**Default styling:** Bold
**Meaning:** Important, serious, urgent

---

### **Emphasis** (`<em>`)

```html
<p>This is <em>emphasized</em> text.</p>
```

**Result:** This is *emphasized* text.

**Default styling:** Italic
**Meaning:** Stress emphasis

---

### **Bold** (`<b>`) vs **Strong** (`<strong>`)

```html
<p><b>Bold text</b> - just looks bold</p>
<p><strong>Strong text</strong> - semantically important</p>
```

**Both look the same, but:**
- `<strong>` tells screen readers "this is important"
- `<b>` just makes it look bold

**Use `<strong>` for important content.**

---

### **Italic** (`<i>`) vs **Emphasis** (`<em>`)

```html
<p><i>Italic text</i> - just looks italic</p>
<p><em>Emphasized text</em> - semantically emphasized</p>
```

**Use `<em>` for actual emphasis.**

---

### **Underline** (`<u>`)

```html
<p>This is <u>underlined</u> text.</p>
```

**Caution:** Underlined text looks like links. Use sparingly!

---

### **Strikethrough** (`<s>` or `<del>`)

```html
<p>Price: <s>$100</s> $75!</p>
<p>This sentence was <del>deleted</del>.</p>
```

**Result:** Price: ~~$100~~ $75!

---

### **Mark/Highlight** (`<mark>`)

```html
<p>Search results for "CSS": Learn <mark>CSS</mark> today!</p>
```

**Result:** Text with yellow highlight (like a marker pen)

---

### **Small Text** (`<small>`)

```html
<p>Price: $99.99 <small>per month</small></p>
<p>Copyright © 2024 <small>All rights reserved</small></p>
```

**Use for:** Fine print, disclaimers, copyright

---

### **Subscript** (`<sub>`) and **Superscript** (`<sup>`)

```html
<p>H<sub>2</sub>O</p>  <!-- Water -->
<p>E = mc<sup>2</sup></p>  <!-- Einstein's equation -->
<p>5<sup>th</sup> Avenue</p>  <!-- Ordinal -->
```

**Result:**
- H₂O
- E = mc²
- 5ᵗʰ Avenue

---

## 📏 Line Breaks and Horizontal Rules

### **Line Break** (`<br>`)

```html
<p>
  First line<br>
  Second line<br>
  Third line
</p>
```

**Result:**
First line
Second line
Third line

**Note:** `<br>` is self-closing (no closing tag needed)

---

### **Horizontal Rule** (`<hr>`)

```html
<p>Section one content</p>
<hr>
<p>Section two content</p>
```

**Result:** A horizontal line separating content

**Use for:** Thematic breaks between sections

---

## 📝 Quotations

### **Inline Quote** (`<q>`)

```html
<p>As Einstein said, <q>Imagination is more important than knowledge.</q></p>
```

**Result:** As Einstein said, "Imagination is more important than knowledge."

**Browsers automatically add quotation marks.**

---

### **Block Quote** (`<blockquote>`)

```html
<blockquote>
  <p>
    The only way to do great work is to love what you do.
    If you haven't found it yet, keep looking. Don't settle.
  </p>
  <cite>— Steve Jobs</cite>
</blockquote>
```

**Result:** Indented quote block

**Use for:** Long quotes, testimonials

---

### **Citation** (`<cite>`)

```html
<p>My favorite book is <cite>The Great Gatsby</cite>.</p>
```

**Use for:** Book titles, article titles, creative works

---

## 💻 Code and Technical Text

### **Inline Code** (`<code>`)

```html
<p>Use the <code>console.log()</code> function to debug.</p>
```

**Result:** Use the `console.log()` function to debug.

**Default styling:** Monospace font

---

### **Code Block** (`<pre>`)

```html
<pre>
function greet() {
  console.log("Hello!");
}
</pre>
```

**Result:** Preserves whitespace and line breaks (monospace font)

```
function greet() {
  console.log("Hello!");
}
```

**Use for:** Code examples, ASCII art

---

### **Keyboard Input** (`<kbd>`)

```html
<p>Press <kbd>Ctrl</kbd> + <kbd>C</kbd> to copy.</p>
```

**Result:** Press Ctrl + C to copy.

---

### **Sample Output** (`<samp>`)

```html
<p>The program output: <samp>Error: File not found</samp></p>
```

---

## 🎨 Working Example

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Text Elements Demo</title>
</head>
<body>
  <h1>Complete Guide to Text Elements</h1>

  <h2>Introduction</h2>
  <p>
    This guide covers <strong>all the essential</strong> text elements
    you need to know. Pay <em>special attention</em> to semantic elements!
  </p>

  <h2>Formatting Examples</h2>
  <p>
    You can make text <strong>bold (important)</strong>,
    <em>italic (emphasized)</em>,
    <u>underlined</u>,
    <mark>highlighted</mark>,
    or <s>strikethrough</s>.
  </p>

  <h3>Mathematical Notation</h3>
  <p>
    Water is H<sub>2</sub>O.<br>
    Einstein's equation: E = mc<sup>2</sup>
  </p>

  <hr>

  <h2>Quotations</h2>
  <blockquote>
    <p>The only limit to our realization of tomorrow will be our doubts of today.</p>
    <cite>— Franklin D. Roosevelt</cite>
  </blockquote>

  <h2>Code Example</h2>
  <p>To print in JavaScript, use <code>console.log()</code>:</p>
  <pre>
function sayHello() {
  console.log("Hello, World!");
}
  </pre>

  <p><small>© 2024 Text Elements Tutorial</small></p>
</body>
</html>
```

---

## ✏️ Practice Exercise

Create `text-practice.html` with:

1. Main heading (h1)
2. Two section headings (h2)
3. Paragraphs with strong and em elements
4. A blockquote
5. A code example using `<code>` or `<pre>`
6. Some subscript or superscript text

<details>
<summary>Solution</summary>

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Text Practice</title>
</head>
<body>
  <h1>My Learning Journey</h1>

  <h2>Why I'm Learning HTML</h2>
  <p>
    I'm learning HTML because it's the <strong>foundation</strong>
    of web development. Understanding HTML is <em>essential</em>
    for anyone who wants to build websites.
  </p>

  <h2>Favorite Quote</h2>
  <blockquote>
    <p>
      The best time to plant a tree was 20 years ago.
      The second best time is now.
    </p>
    <cite>— Chinese Proverb</cite>
  </blockquote>

  <h2>What I've Learned</h2>
  <p>
    Today I learned how to use the <code>&lt;blockquote&gt;</code>
    element for quotations.
  </p>

  <p>Chemical formula for glucose: C<sub>6</sub>H<sub>12</sub>O<sub>6</sub></p>

  <p><small>Created as part of my HTML practice</small></p>
</body>
</html>
```

</details>

---

## 🎯 Key Takeaways

1. **Headings (`<h1>` to `<h6>`)** create structure
   - Only one `<h1>` per page
   - Don't skip levels

2. **Semantic elements matter:**
   - Use `<strong>` not `<b>` for importance
   - Use `<em>` not `<i>` for emphasis

3. **Special text elements:**
   - `<mark>` for highlighting
   - `<code>` for code
   - `<blockquote>` for long quotes
   - `<sub>` and `<sup>` for subscript/superscript

4. **Accessibility:** Semantic HTML helps screen readers understand content

---

## 🚀 Next Lesson

Now you can format text. Next, learn how to **link pages together** - the foundation of the "web"!

**Next:** [Lesson 4: Links & Navigation →](./04-links.md)

---

**Text is 90% of the web. Master these elements, and you're well on your way.** ✍️
