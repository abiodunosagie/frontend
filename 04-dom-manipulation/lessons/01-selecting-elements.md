# DOM Manipulation 01 - Selecting Elements

> **"You can't change what you can't find. This is how JavaScript finds HTML elements."**

---

## 🎯 What You'll Learn

- What the DOM actually is (explained simply)
- How to select single elements
- How to select multiple elements
- Different selection methods and when to use each
- Common mistakes and how to avoid them

**Time to complete:** 20-30 minutes

---

## 🤔 What is the DOM? (Explained Like You're 5)

### The Library Analogy

Imagine the DOM as a **library with organized shelves**:

- **Books** = HTML elements (`<div>`, `<p>`, `<button>`)
- **Library catalog** = The DOM (how JavaScript sees your HTML)
- **You** = JavaScript
- **Finding a book** = Selecting an element

**You can't change a book's content until you find it on the shelf.**

Similarly, JavaScript can't change HTML until it **selects (finds) the element**.

---

## 📖 DOM = Document Object Model

**What does that mean?**

- **Document** = Your HTML page
- **Object** = JavaScript represents everything as objects
- **Model** = A structured representation of your HTML

**When your HTML loads, the browser creates a DOM tree:**

```
document
  └── html
      ├── head
      │   ├── title
      │   └── meta
      └── body
          ├── header
          │   ├── h1
          │   └── nav
          │       └── ul
          │           ├── li
          │           ├── li
          │           └── li
          ├── main
          │   ├── p
          │   └── button
          └── footer
```

JavaScript can navigate this tree and select any element!

---

## 🔍 Method 1: querySelector (Most Common)

### What It Does
Finds the **first element** that matches a CSS selector.

### Syntax
```javascript
document.querySelector('selector');
```

### Examples

**Select by tag name:**
```javascript
const heading = document.querySelector('h1');
console.log(heading); // <h1>Welcome</h1>
```

**Select by class:**
```javascript
const card = document.querySelector('.card');
console.log(card); // <div class="card">...</div>
```

**Select by ID:**
```javascript
const header = document.querySelector('#header');
console.log(header); // <header id="header">...</header>
```

**Select nested elements:**
```javascript
const navLink = document.querySelector('nav a');
// Finds first <a> inside <nav>
```

**Select with multiple classes:**
```javascript
const activeCard = document.querySelector('.card.active');
// Finds element with BOTH classes
```

### Real Example

```html
<!DOCTYPE html>
<html>
<body>
  <h1>Welcome</h1>
  <p class="intro">This is the introduction.</p>
  <button id="myBtn">Click Me</button>

  <script>
    const title = document.querySelector('h1');
    console.log(title.textContent); // "Welcome"

    const intro = document.querySelector('.intro');
    console.log(intro.textContent); // "This is the introduction."

    const button = document.querySelector('#myBtn');
    console.log(button.textContent); // "Click Me"
  </script>
</body>
</html>
```

### Important Notes

✅ Returns **one element** (the first match)
✅ Returns `null` if no match found
✅ Uses **CSS selector syntax**
✅ Most flexible and modern method

---

## 🔍 Method 2: querySelectorAll (Select Multiple)

### What It Does
Finds **all elements** that match a CSS selector.

### Syntax
```javascript
document.querySelectorAll('selector');
```

### Examples

**Select all paragraphs:**
```javascript
const paragraphs = document.querySelectorAll('p');
console.log(paragraphs); // NodeList [p, p, p]
```

**Select all elements with a class:**
```javascript
const cards = document.querySelectorAll('.card');
console.log(cards.length); // 3 (if there are 3 cards)
```

**Select all links inside nav:**
```javascript
const navLinks = document.querySelectorAll('nav a');
// NodeList of all <a> inside <nav>
```

### Real Example

```html
<!DOCTYPE html>
<html>
<body>
  <ul>
    <li class="item">Apple</li>
    <li class="item">Banana</li>
    <li class="item">Cherry</li>
  </ul>

  <script>
    const items = document.querySelectorAll('.item');
    console.log(items); // NodeList [li.item, li.item, li.item]
    console.log(items.length); // 3

    // Loop through all items
    items.forEach(item => {
      console.log(item.textContent);
    });
    // Output:
    // Apple
    // Banana
    // Cherry
  </script>
</body>
</html>
```

### Working with NodeLists

**A NodeList looks like an array but isn't exactly an array.**

```javascript
const items = document.querySelectorAll('.item');

// ✅ You CAN do this:
items.forEach(item => {
  console.log(item);
});

// ✅ Access by index:
const firstItem = items[0];
const secondItem = items[1];

// ✅ Check length:
console.log(items.length);

// ❌ You CAN'T use array methods like map, filter (need to convert first):
const array = Array.from(items); // Convert to real array
const texts = array.map(item => item.textContent);
```

---

## 🔍 Method 3: getElementById (Old but Fast)

### What It Does
Finds element by its `id` attribute.

### Syntax
```javascript
document.getElementById('idName'); // NO # symbol!
```

### Example

```html
<!DOCTYPE html>
<html>
<body>
  <div id="container">
    <h1>Hello World</h1>
  </div>

  <script>
    const container = document.getElementById('container');
    console.log(container); // <div id="container">...</div>

    // Note: NO # symbol (different from querySelector)
    // ❌ document.getElementById('#container') - WRONG
    // ✅ document.getElementById('container') - CORRECT
  </script>
</body>
</html>
```

### querySelector vs getElementById

```javascript
// These are equivalent:
const el1 = document.getElementById('myId');
const el2 = document.querySelector('#myId');

// getElementById is slightly faster but less flexible
```

**When to use:**
- `getElementById`: When you know the exact ID and want maximum performance
- `querySelector`: When you want flexibility (modern approach)

---

## 🔍 Method 4: getElementsByClassName (Old Method)

### What It Does
Finds all elements with a specific class.

### Syntax
```javascript
document.getElementsByClassName('className'); // NO . symbol!
```

### Example

```html
<!DOCTYPE html>
<html>
<body>
  <div class="card">Card 1</div>
  <div class="card">Card 2</div>
  <div class="card">Card 3</div>

  <script>
    const cards = document.getElementsByClassName('card');
    console.log(cards); // HTMLCollection [div.card, div.card, div.card]

    // Loop through (must convert to array or use old-style for loop)
    Array.from(cards).forEach(card => {
      console.log(card.textContent);
    });
  </script>
</body>
</html>
```

### querySelectorAll vs getElementsByClassName

```javascript
// These are similar:
const cards1 = document.getElementsByClassName('card');
const cards2 = document.querySelectorAll('.card');

// Differences:
// - getElementsByClassName returns HTMLCollection (LIVE)
// - querySelectorAll returns NodeList (STATIC)
```

**Modern approach:** Use `querySelectorAll` instead.

---

## 🔍 Method 5: getElementsByTagName (Old Method)

### What It Does
Finds all elements with a specific tag name.

### Syntax
```javascript
document.getElementsByTagName('tagName');
```

### Example

```html
<!DOCTYPE html>
<html>
<body>
  <p>Paragraph 1</p>
  <p>Paragraph 2</p>
  <p>Paragraph 3</p>

  <script>
    const paragraphs = document.getElementsByTagName('p');
    console.log(paragraphs); // HTMLCollection [p, p, p]
  </script>
</body>
</html>
```

**Modern approach:** Use `querySelectorAll('p')` instead.

---

## 📊 Method Comparison

| Method | Returns | Syntax | Use Case |
|--------|---------|--------|----------|
| `querySelector` | First match | CSS selector | **Use this (modern)** |
| `querySelectorAll` | All matches | CSS selector | **Use this (modern)** |
| `getElementById` | One element | ID (no #) | Fast, single ID |
| `getElementsByClassName` | Live collection | Class (no .) | Older code |
| `getElementsByTagName` | Live collection | Tag name | Older code |

**Recommendation:** Stick with `querySelector` and `querySelectorAll` - they're modern, flexible, and easy to remember!

---

## 🎯 Practical Examples

### Example 1: Selecting Navigation Links

```html
<nav>
  <ul>
    <li><a href="#home">Home</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<script>
  // Select all nav links
  const navLinks = document.querySelectorAll('nav a');

  console.log(`Found ${navLinks.length} links`); // Found 3 links

  // Loop through and log each href
  navLinks.forEach(link => {
    console.log(link.href);
  });
</script>
```

### Example 2: Selecting Form Elements

```html
<form id="contactForm">
  <input type="text" name="name" placeholder="Name">
  <input type="email" name="email" placeholder="Email">
  <textarea name="message" placeholder="Message"></textarea>
  <button type="submit">Send</button>
</form>

<script>
  // Select the form
  const form = document.querySelector('#contactForm');

  // Select all inputs
  const inputs = form.querySelectorAll('input, textarea');

  console.log(`Form has ${inputs.length} input fields`); // 3

  // Select specific input
  const emailInput = form.querySelector('input[type="email"]');
  console.log(emailInput);
</script>
```

### Example 3: Selecting with Complex Selectors

```html
<div class="container">
  <div class="card active">
    <h2>Active Card</h2>
  </div>
  <div class="card">
    <h2>Regular Card</h2>
  </div>
</div>

<script>
  // Select active card
  const activeCard = document.querySelector('.card.active');

  // Select h2 inside active card
  const activeTitle = document.querySelector('.card.active h2');

  // Select all h2 elements inside cards
  const cardTitles = document.querySelectorAll('.card h2');

  // Select first card's title
  const firstTitle = document.querySelector('.card:first-child h2');
</script>
```

---

## ⚠️ Common Mistakes

### Mistake 1: Using # or . with getElementById/getElementsByClassName

```javascript
// ❌ WRONG
document.getElementById('#myId');
document.getElementsByClassName('.myClass');

// ✅ CORRECT
document.getElementById('myId');
document.getElementsByClassName('myClass');

// ✅ OR use querySelector (with # or .)
document.querySelector('#myId');
document.querySelector('.myClass');
```

### Mistake 2: Not Checking if Element Exists

```javascript
// ❌ WRONG - Can cause errors
const button = document.querySelector('.btn');
button.textContent = 'Click'; // ERROR if button doesn't exist!

// ✅ CORRECT - Check first
const button = document.querySelector('.btn');
if (button) {
  button.textContent = 'Click';
} else {
  console.log('Button not found');
}
```

### Mistake 3: Using querySelectorAll Like an Array

```javascript
const items = document.querySelectorAll('.item');

// ❌ WRONG - map doesn't work on NodeList
const texts = items.map(item => item.textContent);

// ✅ CORRECT - Convert to array first
const texts = Array.from(items).map(item => item.textContent);

// ✅ OR use forEach (works on NodeList)
items.forEach(item => {
  console.log(item.textContent);
});
```

### Mistake 4: Selecting Before DOM Loads

```javascript
// ❌ WRONG - Script runs before HTML loads
const button = document.querySelector('.btn');
console.log(button); // null

<button class="btn">Click</button>
```

**Solution: Put script at end of body, or use DOMContentLoaded:**

```javascript
// ✅ CORRECT
document.addEventListener('DOMContentLoaded', () => {
  const button = document.querySelector('.btn');
  console.log(button); // Works!
});
```

---

## 🎯 Practice Exercises

### Exercise 1: Basic Selection

Create an HTML file with:
- A heading with id "title"
- Three paragraphs with class "text"
- A button with id "btn"

Then use JavaScript to:
1. Select the title and log its content
2. Select all paragraphs and log how many there are
3. Select the button and log it

<details>
<summary>Solution</summary>

```html
<!DOCTYPE html>
<html>
<body>
  <h1 id="title">Welcome</h1>
  <p class="text">Paragraph 1</p>
  <p class="text">Paragraph 2</p>
  <p class="text">Paragraph 3</p>
  <button id="btn">Click Me</button>

  <script>
    // 1. Select title
    const title = document.querySelector('#title');
    console.log(title.textContent); // "Welcome"

    // 2. Select all paragraphs
    const paragraphs = document.querySelectorAll('.text');
    console.log(`Found ${paragraphs.length} paragraphs`); // Found 3 paragraphs

    // 3. Select button
    const button = document.querySelector('#btn');
    console.log(button); // <button id="btn">Click Me</button>
  </script>
</body>
</html>
```
</details>

### Exercise 2: Navigation Links

Create a navigation with 5 links. Use JavaScript to:
1. Select all navigation links
2. Log the href of each link
3. Count how many links there are

<details>
<summary>Solution</summary>

```html
<!DOCTYPE html>
<html>
<body>
  <nav>
    <a href="#home">Home</a>
    <a href="#about">About</a>
    <a href="#services">Services</a>
    <a href="#portfolio">Portfolio</a>
    <a href="#contact">Contact</a>
  </nav>

  <script>
    // 1. Select all nav links
    const links = document.querySelectorAll('nav a');

    // 2. Log href of each
    links.forEach(link => {
      console.log(link.href);
    });

    // 3. Count links
    console.log(`Total links: ${links.length}`); // Total links: 5
  </script>
</body>
</html>
```
</details>

### Exercise 3: Complex Selectors

Create cards with titles and buttons. Use JavaScript to:
1. Select only the first card
2. Select all card titles
3. Select the button inside the second card

<details>
<summary>Solution</summary>

```html
<!DOCTYPE html>
<html>
<body>
  <div class="card">
    <h2 class="card-title">Card 1</h2>
    <button>Learn More</button>
  </div>
  <div class="card">
    <h2 class="card-title">Card 2</h2>
    <button>Learn More</button>
  </div>
  <div class="card">
    <h2 class="card-title">Card 3</h2>
    <button>Learn More</button>
  </div>

  <script>
    // 1. First card
    const firstCard = document.querySelector('.card');
    console.log(firstCard);

    // 2. All card titles
    const titles = document.querySelectorAll('.card-title');
    titles.forEach(title => {
      console.log(title.textContent);
    });

    // 3. Button in second card
    const cards = document.querySelectorAll('.card');
    const secondCardButton = cards[1].querySelector('button');
    console.log(secondCardButton);
  </script>
</body>
</html>
```
</details>

---

## 🎯 Key Takeaways

✅ **querySelector** - Select first match with CSS selector (use this most)
✅ **querySelectorAll** - Select all matches with CSS selector (use this most)
✅ **getElementById** - Select by ID (faster but less flexible)
✅ **Always check if element exists** before using it
✅ **querySelectorAll returns a NodeList**, not an array
✅ **Put scripts at end of body** or use DOMContentLoaded

---

## 🔗 What's Next?

Now that you can select elements, the next lesson covers **changing their content**:
- Changing text
- Changing HTML
- Changing attributes
- Changing values in forms

**Next:** [02 - Changing Content](./02-changing-content.md)

---

**You can now find any element on the page. That's huge! 🎯**
