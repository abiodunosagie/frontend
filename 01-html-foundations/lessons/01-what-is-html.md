# Lesson 1: What is HTML?

> **"Every expert was once a beginner."**

## 🤔 The Big Question

What is HTML, and why does it exist?

---

## 📖 The Simple Explanation

**HTML stands for HyperText Markup Language.**

Let's break that down like you're 5:

### HyperText
"Hyper" means **super** or **beyond**.
"Text" is just... text.

**HyperText** = Text that can **link to other text**. That's it!

When you click a link on a webpage and it takes you somewhere else? That's hypertext. Revolutionary in 1991, normal today.

### Markup
Think of a teacher **marking up** a paper with a red pen:
- "This is the title" ← writes at the top
- "This is important!" ← circles a paragraph
- "This connects to Chapter 5" ← draws an arrow

HTML does the same thing, but for computers:
```html
<h1>This is the title</h1>
<p>This is a paragraph</p>
<strong>This is important!</strong>
```

You're **marking** what each piece of text **is**.

### Language
A set of rules that browsers understand.

Just like English has grammar (noun, verb, adjective), HTML has **elements** (h1, p, div, etc.).

---

## 🌍 Why HTML Exists

### The Problem (Before HTML)

In the early days, computers could only show **plain text**. No formatting. No images. No links.

Imagine if every webpage looked like a .txt file. Boring. Impossible to organize.

### The Solution (HTML)

Tim Berners-Lee (the inventor of the World Wide Web) created HTML in 1991 to:
1. **Structure** information (this is a heading, this is a paragraph)
2. **Link** documents together (click here to go there)
3. **Make the web navigable** (hence "web" - everything connected)

---

## 🏗️ What HTML Does (and Doesn't Do)

### HTML DOES:
✅ **Structure content** - Define what things are
✅ **Create links** - Connect pages
✅ **Embed images/videos** - Add media
✅ **Create forms** - Get user input
✅ **Organize information** - Headers, lists, tables

### HTML DOESN'T:
❌ **Make things pretty** - That's CSS's job
❌ **Make things interactive** - That's JavaScript's job
❌ **Store data** - That's a database's job
❌ **Do calculations** - That's programming's job

**HTML is the foundation. Everything else builds on top of it.**

---

## 🧱 HTML is Like Building Blocks

Imagine you're building a house:

| Building a House | Building a Webpage |
|------------------|-------------------|
| **Foundation** | HTML (structure) |
| **Paint & decorations** | CSS (styling) |
| **Electricity & plumbing** | JavaScript (functionality) |

You can't paint a house before building it. Same with web development:
1. **HTML first** (structure)
2. **CSS second** (make it pretty)
3. **JavaScript third** (make it interactive)

---

## 💡 Your First HTML

Let's write some HTML right now. Don't worry about understanding it perfectly yet.

### Create a file:

1. Open VS Code
2. In your `frontend-learning` folder, create a new file: `first.html`
3. Type this **exactly**:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My First Page</title>
  </head>
  <body>
    <h1>Hello, World!</h1>
    <p>This is my first webpage. I am learning HTML.</p>
  </body>
</html>
```

### Open it in a browser:

1. **Right-click** the file in VS Code
2. Select **"Open with Live Server"** (if you installed the extension)
3. Or just drag the file into Chrome/Firefox

**You just built a webpage.** 🎉

---

## 🔍 Let's Decode What You Wrote

```html
<!DOCTYPE html>
```
**Translation:** "Hey browser, this is an HTML5 document."
(You put this at the top of every HTML file. Just do it.)

```html
<html>
```
**Translation:** "Everything inside here is HTML."
(This wraps your entire page.)

```html
<head>
```
**Translation:** "This section has information ABOUT the page, but won't show on the page."
(Think of it as metadata - data about data.)

```html
<title>My First Page</title>
```
**Translation:** "This is what shows in the browser tab."
(Look at your browser tab - see the title?)

```html
<body>
```
**Translation:** "This is what actually shows on the page."
(Everything users see goes in here.)

```html
<h1>Hello, World!</h1>
```
**Translation:** "This is a top-level heading (the biggest one)."
(h1 = heading level 1)

```html
<p>This is my first webpage. I am learning HTML.</p>
```
**Translation:** "This is a paragraph of text."
(p = paragraph)

---

## 🎯 Key Takeaways

1. **HTML = Structure** (not styling, not functionality)
2. **Tags = Labels** (you're just labeling what things are)
3. **Every page needs the same basic skeleton** (DOCTYPE, html, head, body)
4. **Content goes in `<body>`** (what users see)
5. **Metadata goes in `<head>`** (what browsers/search engines need)

---

## ✏️ Practice Exercise

Edit your `first.html` file:

1. Change the title to your name
2. Change the h1 to say "Welcome to [Your Name]'s Page"
3. Add another paragraph about why you're learning HTML

Save it and refresh the browser. See your changes? **That's the feedback loop.**

Edit → Save → Refresh → See changes. You'll do this thousands of times.

---

## 🚀 Next Lesson

Now that you know **what** HTML is, let's learn the **proper structure** every HTML document needs.

**Next:** [Lesson 2: HTML Document Structure →](./02-document-structure.md)

---

## 💭 Reflection Questions

Before moving on, make sure you can answer:
1. What does HTML stand for?
2. What is HTML's primary job?
3. What's the difference between `<head>` and `<body>`?
4. What does "markup" mean in "Markup Language"?

If you're fuzzy on any of these, re-read this lesson. **Foundation matters.**

---

**You're doing great. HTML is just the beginning, but it's the most important beginning.** 🌱
