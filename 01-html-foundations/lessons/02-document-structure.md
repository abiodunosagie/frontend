# Lesson 2: HTML Document Structure

> **"A house without a foundation is just a pile of bricks."**

## 🎯 What You'll Learn

Every HTML document follows the same basic structure. Like how every house has a foundation, walls, and a roof - every webpage has certain required elements.

Let's learn **why** each part exists and **when** to use different elements.

---

## 🏗️ The Complete HTML Skeleton

Here's the structure EVERY webpage needs:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Page Title</title>
  </head>
  <body>
    <!-- Your content goes here -->
  </body>
</html>
```

Let's break down **every single line**.

---

## 📋 Line-by-Line Explanation

### `<!DOCTYPE html>`

**What it means:** "This is an HTML5 document"

**Why it's needed:** Browsers need to know what version of HTML you're using. HTML5 is the current standard (and will be for a long time).

**Do I need to understand it?** Not really. Just put it at the top. Every time. First line. Always.

**Fun fact:** In old HTML (before HTML5), this line was MUCH longer:
```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
```
HTML5 simplified it to just `<!DOCTYPE html>`. Thank goodness.

---

### `<html lang="en">`

**What it means:** "Everything inside here is HTML, and it's in English"

**Why it's needed:**
- Wraps your entire document
- The `lang="en"` attribute tells browsers and screen readers what language your content is in
  - `en` = English
  - `es` = Spanish
  - `fr` = French
  - etc.

**Why it matters:**
- Screen readers (for blind users) pronounce words correctly
- Translation tools work better
- Search engines can categorize your content by language

---

### `<head>` Section

The `<head>` is **invisible to users**. It contains information **about** the page, not content **on** the page.

Think of it like the **packaging label** on a product - users don't see it, but it's important for how the product works.

#### `<meta charset="UTF-8">`

**What it means:** "Use the UTF-8 character encoding"

**In plain English:** UTF-8 is a system that tells the browser how to display characters.

**Why it matters:**
- Without it, special characters might look broken (é, ñ, 中文, emoji 😊)
- UTF-8 supports every language and symbol in the world

**Example of what breaks without it:**
```
Without UTF-8: "CafÃ©" (broken)
With UTF-8: "Café" (correct)
```

**Just include it. Always.**

---

#### `<meta name="viewport" content="width=device-width, initial-scale=1.0">`

**What it means:** "Make the page responsive on mobile devices"

**In plain English:** Without this line, your website would look zoomed-out and tiny on phones.

**What it does:**
- `width=device-width` → Make the page width match the device's screen width
- `initial-scale=1.0` → Start at 100% zoom (not zoomed in or out)

**Try this experiment:**
1. Create a page WITHOUT this line
2. Open it on your phone (or use Chrome's device simulator: F12 → Toggle device toolbar)
3. See how it's zoomed out and hard to read?
4. Add this meta tag
5. Now it looks normal!

**Mobile-first web design starts with this one line.**

---

#### `<title>Page Title</title>`

**What it means:** The text that appears in:
- The browser tab
- Search engine results
- Bookmarks
- When you share the link on social media

**Example:**
```html
<title>John Doe - Frontend Developer Portfolio</title>
```

Now look at your browser tab. See it? That's the title.

**Best practices:**
- Keep it under 60 characters (or it gets cut off in search results)
- Make it descriptive
- Include keywords (for SEO)

**Bad title:** `<title>Home</title>` (too generic)
**Good title:** `<title>Sarah Chen - UX Designer | Portfolio</title>`

---

### `<body>` Section

Everything inside `<body>` is **visible** to users.

This is where all your content goes:
- Text
- Images
- Videos
- Buttons
- Forms
- Everything you can see on a webpage

**Simple rule:** If users can see it, it goes in `<body>`. If they can't, it goes in `<head>`.

---

## 🧩 The Complete Picture

```html
<!DOCTYPE html>              ← "This is HTML5"
<html lang="en">             ← "All content is in English"
  <head>                     ← "Information ABOUT the page"
    <meta charset="UTF-8">   ← "Support all characters"
    <meta name="viewport"    ← "Work on mobile devices"
          content="width=device-width, initial-scale=1.0">
    <title>...</title>       ← "What shows in the browser tab"
  </head>
  <body>                     ← "What users actually see"
    ...content here...
  </body>
</html>
```

---

## 📝 Comments in HTML

Notice this line earlier?
```html
<!-- Your content goes here -->
```

That's a **comment**. Comments:
- Are invisible to users
- Help YOU remember what code does
- Help OTHER developers understand your code

**Syntax:**
```html
<!-- This is a comment -->

<!--
  This is a
  multi-line comment
-->
```

**Use comments to:**
- Explain complex sections
- Leave notes for yourself
- Temporarily "turn off" code without deleting it

```html
<!-- Navigation Section -->
<nav>
  <!-- Links will go here -->
</nav>

<!-- This code is disabled for now
<p>I'll add this later</p>
-->
```

---

## 🎯 Practice Exercise

Create a new file: `structure-practice.html`

Build a complete HTML skeleton from memory. Include:
- DOCTYPE declaration
- html tag with language attribute
- head section with:
  - charset meta tag
  - viewport meta tag
  - title
- body section with a comment saying "content will go here"

**Don't copy-paste. Type it out.** Your fingers need to learn the pattern.

---

## ✅ Solution (Don't peek until you try!)

<details>
<summary>Click to see solution</summary>

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Structure Practice</title>
  </head>
  <body>
    <!-- Content will go here -->
  </body>
</html>
```

</details>

---

## 🔥 Pro Tips

### 1. Use Emmet in VS Code

Type `!` and press `Tab` in an HTML file. Watch what happens.

**It generates the entire skeleton for you!** 🤯

This is an **Emmet** shortcut. VS Code has Emmet built-in. We'll learn more Emmet shortcuts later.

### 2. Indentation Matters

Notice how everything is indented?
- Head and body are indented inside html
- Meta tags and title are indented inside head

**Why?** Readability. You can see the structure at a glance.

**Bad (but works):**
```html
<html><head><title>Bad</title></head><body><p>Ugly!</p></body></html>
```

**Good:**
```html
<html>
  <head>
    <title>Good</title>
  </head>
  <body>
    <p>Beautiful!</p>
  </body>
</html>
```

Both work. One is professional. One is chaos.

**Your code is read more often than it's written.** Make it readable.

### 3. Use 2-Space Indentation

Standard in frontend development:
- Each nesting level = 2 spaces
- Not tabs (they can look different on different computers)
- Prettier (the extension you installed) handles this automatically

---

## 🧠 Mental Model

Think of HTML structure like **nesting Russian dolls**:

```
<!DOCTYPE html>             ← The declaration (not a doll)
<html>                      ← Biggest doll
  <head>                    ← Doll inside html
    <meta ... />            ← Doll inside head
    <title>...</title>      ← Another doll inside head
  </head>
  <body>                    ← Another doll inside html
    <h1>...</h1>            ← Doll inside body
  </body>
</html>
```

**Rules:**
1. What opens last, closes first
2. You can't close the outer doll before closing the inner ones

**Valid:**
```html
<html>
  <body>
    <p>Text</p>
  </body>
</html>
```

**Invalid (broken nesting):**
```html
<html>
  <body>
    <p>Text
  </body>
</html>
    </p>  ← WRONG! Can't close p after body is already closed
```

---

## 📊 Quick Reference

| Element | Purpose | Required? |
|---------|---------|-----------|
| `<!DOCTYPE html>` | Declares HTML5 | ✅ Yes |
| `<html>` | Root element | ✅ Yes |
| `<head>` | Metadata container | ✅ Yes |
| `<meta charset>` | Character encoding | ⚠️ Highly recommended |
| `<meta viewport>` | Mobile responsiveness | ⚠️ Highly recommended |
| `<title>` | Page title | ✅ Yes |
| `<body>` | Visible content | ✅ Yes |

---

## 🎯 Key Takeaways

1. **Every HTML page has the same basic structure** (DOCTYPE, html, head, body)
2. **`<head>` = invisible metadata** (for browsers, search engines, devices)
3. **`<body>` = visible content** (for users)
4. **Always include charset and viewport** (for special characters and mobile)
5. **Indentation makes code readable** (2 spaces per level)
6. **Comments are your friend** (explain your code)

---

## 🚀 Next Lesson

Now that you understand the structure, let's fill the body with actual content!

**Next:** [Lesson 3: Text Elements →](./03-text-elements.md)

We'll learn headings, paragraphs, bold, italic, and more.

---

## 💭 Self-Check

Before moving on:
1. Can you write the HTML skeleton from memory?
2. Do you know the difference between `<head>` and `<body>`?
3. Do you understand why we need the viewport meta tag?
4. Can you explain what UTF-8 is (in simple terms)?

If yes to all → proceed!
If no to any → re-read that section. **Foundation is everything.**

---

**You're building your foundation brick by brick. This structure will be muscle memory soon.** 🧱
