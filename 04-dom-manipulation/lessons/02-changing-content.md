# DOM Manipulation 02 - Changing Content

> **"Now that you can find elements, let's change them!"**

---

## 🎯 What You'll Learn

- How to change text content
- How to change HTML content
- How to change attributes (src, href, etc.)
- How to change input values
- When to use each method

**Time to complete:** 25-35 minutes

---

## 📝 Method 1: textContent (Change Text Only)

### What It Does
Changes or gets the **text content** of an element (no HTML tags).

### Syntax
```javascript
element.textContent = 'new text';
```

### Examples

**Change a heading:**
```html
<h1 id="title">Old Title</h1>

<script>
  const title = document.querySelector('#title');
  title.textContent = 'New Title';
  // Result: <h1 id="title">New Title</h1>
</script>
```

**Change a paragraph:**
```html
<p class="intro">Welcome to our site.</p>

<script>
  const intro = document.querySelector('.intro');
  intro.textContent = 'Thanks for visiting!';
  // Result: <p class="intro">Thanks for visiting!</p>
</script>
```

**Get text content:**
```html
<p id="message">Hello World</p>

<script>
  const message = document.querySelector('#message');
  console.log(message.textContent); // "Hello World"
</script>
```

### Real Example

```html
<!DOCTYPE html>
<html>
<body>
  <h1 id="greeting">Hello</h1>
  <button onclick="changeGreeting()">Change Greeting</button>

  <script>
    function changeGreeting() {
      const greeting = document.querySelector('#greeting');
      greeting.textContent = 'Welcome!';
    }
  </script>
</body>
</html>
```

### Important Notes

✅ **Safe** - Doesn't execute HTML or scripts
✅ **Fast** - Best for plain text
❌ **Can't use HTML tags** - They'll show as literal text

```javascript
element.textContent = '<strong>Bold</strong>';
// Shows: <strong>Bold</strong> (not bold text)
```

---

## 🎨 Method 2: innerHTML (Change HTML Content)

### What It Does
Changes or gets the **HTML content** inside an element.

### Syntax
```javascript
element.innerHTML = '<p>HTML here</p>';
```

### Examples

**Add HTML formatting:**
```html
<div id="content">Plain text</div>

<script>
  const content = document.querySelector('#content');
  content.innerHTML = '<strong>Bold text</strong>';
  // Result: <div id="content"><strong>Bold text</strong></div>
</script>
```

**Create a list:**
```html
<div id="list"></div>

<script>
  const listDiv = document.querySelector('#list');
  listDiv.innerHTML = `
    <ul>
      <li>Item 1</li>
      <li>Item 2</li>
      <li>Item 3</li>
    </ul>
  `;
</script>
```

**Build dynamic content:**
```html
<div id="users"></div>

<script>
  const users = ['Alice', 'Bob', 'Charlie'];
  const usersDiv = document.querySelector('#users');

  usersDiv.innerHTML = users.map(user => `
    <div class="user-card">
      <h3>${user}</h3>
      <p>User profile</p>
    </div>
  `).join('');
</script>
```

### Real Example

```html
<!DOCTYPE html>
<html>
<body>
  <div id="output"></div>
  <button onclick="showCard()">Show Card</button>

  <script>
    function showCard() {
      const output = document.querySelector('#output');
      output.innerHTML = `
        <div style="border: 1px solid #ccc; padding: 20px; border-radius: 8px;">
          <h2>User Card</h2>
          <p><strong>Name:</strong> Alice</p>
          <p><strong>Email:</strong> alice@example.com</p>
        </div>
      `;
    }
  </script>
</body>
</html>
```

### ⚠️ Security Warning

**Never use innerHTML with user input!**

```javascript
// ❌ DANGEROUS - Can execute malicious scripts
const userInput = '<img src=x onerror="alert(\'Hacked!\')">'; element.innerHTML = userInput; // XSS attack!

// ✅ SAFE - Use textContent for user input
element.textContent = userInput; // Shows as literal text
```

---

## 🔄 textContent vs innerHTML

| Feature | textContent | innerHTML |
|---------|-------------|-----------|
| **Speed** | Faster | Slower |
| **Security** | Safe | Can be dangerous |
| **HTML tags** | Shows as text | Renders as HTML |
| **Use case** | Plain text | HTML content |

### Example Comparison

```html
<div id="test"></div>

<script>
  const div = document.querySelector('#test');

  // textContent
  div.textContent = '<strong>Bold</strong>';
  // Shows: <strong>Bold</strong>

  // innerHTML
  div.innerHTML = '<strong>Bold</strong>';
  // Shows: Bold (actually bold)
</script>
```

**Rule of thumb:**
- User input → `textContent`
- Trusted HTML → `innerHTML`
- Plain text → `textContent`

---

## 🔗 Changing Attributes

### What Are Attributes?
Attributes are properties of HTML elements: `src`, `href`, `alt`, `class`, `id`, etc.

### Method 1: Direct Property Access

```javascript
element.src = 'new-image.jpg';
element.href = 'https://example.com';
element.alt = 'Description';
```

### Examples

**Change image source:**
```html
<img id="photo" src="old.jpg" alt="Old photo">
<button onclick="changeImage()">Change Image</button>

<script>
  function changeImage() {
    const img = document.querySelector('#photo');
    img.src = 'new.jpg';
    img.alt = 'New photo';
  }
</script>
```

**Change link:**
```html
<a id="link" href="https://google.com">Google</a>

<script>
  const link = document.querySelector('#link');
  link.href = 'https://github.com';
  link.textContent = 'GitHub';
</script>
```

### Method 2: getAttribute() and setAttribute()

```javascript
element.getAttribute('attributeName');
element.setAttribute('attributeName', 'value');
element.removeAttribute('attributeName');
```

### Examples

**Get attribute:**
```html
<img id="photo" src="photo.jpg" alt="My photo">

<script>
  const img = document.querySelector('#photo');
  console.log(img.getAttribute('src')); // "photo.jpg"
  console.log(img.getAttribute('alt')); // "My photo"
</script>
```

**Set attribute:**
```html
<button id="btn">Click Me</button>

<script>
  const btn = document.querySelector('#btn');
  btn.setAttribute('disabled', 'true');
  btn.setAttribute('class', 'btn-primary');
</script>
```

**Remove attribute:**
```html
<input id="field" disabled>

<script>
  const field = document.querySelector('#field');
  field.removeAttribute('disabled'); // Now enabled
</script>
```

### Real Example: Image Gallery

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .gallery img {
      width: 200px;
      cursor: pointer;
      margin: 5px;
    }
    #mainImage {
      width: 400px;
      display: block;
      margin: 20px auto;
    }
  </style>
</head>
<body>
  <img id="mainImage" src="https://via.placeholder.com/400/blue" alt="Main">

  <div class="gallery">
    <img src="https://via.placeholder.com/200/red" alt="Red">
    <img src="https://via.placeholder.com/200/green" alt="Green">
    <img src="https://via.placeholder.com/200/blue" alt="Blue">
  </div>

  <script>
    const mainImage = document.querySelector('#mainImage');
    const thumbnails = document.querySelectorAll('.gallery img');

    thumbnails.forEach(thumb => {
      thumb.addEventListener('click', () => {
        mainImage.src = thumb.src.replace('200', '400');
        mainImage.alt = thumb.alt;
      });
    });
  </script>
</body>
</html>
```

---

## 📝 Changing Form Values

### Input Fields

```html
<input type="text" id="username" value="Old name">

<script>
  const input = document.querySelector('#username');

  // Get value
  console.log(input.value); // "Old name"

  // Set value
  input.value = 'New name';
</script>
```

### Textarea

```html
<textarea id="message">Old message</textarea>

<script>
  const textarea = document.querySelector('#message');
  textarea.value = 'New message';
</script>
```

### Checkboxes and Radio Buttons

```html
<input type="checkbox" id="agree">

<script>
  const checkbox = document.querySelector('#agree');

  // Check if checked
  console.log(checkbox.checked); // true or false

  // Check/uncheck
  checkbox.checked = true;  // Checked
  checkbox.checked = false; // Unchecked
</script>
```

### Select Dropdown

```html
<select id="country">
  <option value="us">United States</option>
  <option value="uk">United Kingdom</option>
  <option value="ca">Canada</option>
</select>

<script>
  const select = document.querySelector('#country');

  // Get selected value
  console.log(select.value); // "us"

  // Change selection
  select.value = 'uk';
</script>
```

### Real Example: Form Reset

```html
<!DOCTYPE html>
<html>
<body>
  <form id="contactForm">
    <input type="text" id="name" placeholder="Name">
    <input type="email" id="email" placeholder="Email">
    <textarea id="message" placeholder="Message"></textarea>
    <button type="button" onclick="clearForm()">Clear</button>
  </form>

  <script>
    function clearForm() {
      document.querySelector('#name').value = '';
      document.querySelector('#email').value = '';
      document.querySelector('#message').value = '';
    }
  </script>
</body>
</html>
```

---

## 🎯 Practical Examples

### Example 1: Live Character Counter

```html
<!DOCTYPE html>
<html>
<body>
  <textarea id="text" maxlength="100" placeholder="Type something..."></textarea>
  <p>Characters: <span id="count">0</span> / 100</p>

  <script>
    const textarea = document.querySelector('#text');
    const count = document.querySelector('#count');

    textarea.addEventListener('input', () => {
      count.textContent = textarea.value.length;
    });
  </script>
</body>
</html>
```

### Example 2: Username Availability Checker

```html
<!DOCTYPE html>
<html>
<body>
  <input type="text" id="username" placeholder="Enter username">
  <p id="status"></p>

  <script>
    const input = document.querySelector('#username');
    const status = document.querySelector('#status');

    const takenUsernames = ['admin', 'user', 'test'];

    input.addEventListener('input', () => {
      const username = input.value.toLowerCase();

      if (username === '') {
        status.textContent = '';
        return;
      }

      if (takenUsernames.includes(username)) {
        status.textContent = '❌ Username taken';
        status.style.color = 'red';
      } else {
        status.textContent = '✅ Username available';
        status.style.color = 'green';
      }
    });
  </script>
</body>
</html>
```

### Example 3: Dynamic Profile Card

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .card {
      border: 1px solid #ccc;
      padding: 20px;
      max-width: 300px;
      margin: 20px;
    }
    input { display: block; margin: 10px 0; padding: 5px; width: 100%; }
  </style>
</head>
<body>
  <div>
    <h3>Edit Profile</h3>
    <input type="text" id="nameInput" placeholder="Name">
    <input type="text" id="titleInput" placeholder="Job Title">
    <input type="text" id="bioInput" placeholder="Bio">
    <button onclick="updateCard()">Update Card</button>
  </div>

  <div class="card">
    <h2 id="cardName">Your Name</h2>
    <p id="cardTitle">Your Title</p>
    <p id="cardBio">Your bio goes here...</p>
  </div>

  <script>
    function updateCard() {
      const name = document.querySelector('#nameInput').value;
      const title = document.querySelector('#titleInput').value;
      const bio = document.querySelector('#bioInput').value;

      document.querySelector('#cardName').textContent = name || 'Your Name';
      document.querySelector('#cardTitle').textContent = title || 'Your Title';
      document.querySelector('#cardBio').textContent = bio || 'Your bio goes here...';
    }
  </script>
</body>
</html>
```

---

## ⚠️ Common Mistakes

### Mistake 1: Forgetting to Get the Value

```javascript
// ❌ WRONG - Sets element itself, not value
const input = document.querySelector('#username');
console.log(input); // Logs the element

// ✅ CORRECT - Get the value
console.log(input.value); // Logs the text inside
```

### Mistake 2: Using innerHTML for User Input

```javascript
// ❌ DANGEROUS
const userInput = prompt('Enter your name');
element.innerHTML = userInput; // XSS vulnerability!

// ✅ SAFE
element.textContent = userInput;
```

### Mistake 3: Not Checking if Element Exists

```javascript
// ❌ Can crash if element doesn't exist
const title = document.querySelector('#title');
title.textContent = 'New Title'; // ERROR if null

// ✅ Check first
const title = document.querySelector('#title');
if (title) {
  title.textContent = 'New Title';
}
```

---

## 🎯 Practice Exercises

### Exercise 1: Button Click Counter

Create a button and a counter. Every time the button is clicked, increase the counter and update the display.

<details>
<summary>Solution</summary>

```html
<!DOCTYPE html>
<html>
<body>
  <p>Count: <span id="count">0</span></p>
  <button onclick="increment()">Click Me</button>

  <script>
    let count = 0;

    function increment() {
      count++;
      document.querySelector('#count').textContent = count;
    }
  </script>
</body>
</html>
```
</details>

### Exercise 2: Image Switcher

Create two buttons that change an image source between two different images.

<details>
<summary>Solution</summary>

```html
<!DOCTYPE html>
<html>
<body>
  <img id="photo" src="https://via.placeholder.com/300/blue" alt="Photo">
  <br>
  <button onclick="showRed()">Show Red</button>
  <button onclick="showBlue()">Show Blue</button>

  <script>
    const img = document.querySelector('#photo');

    function showRed() {
      img.src = 'https://via.placeholder.com/300/red';
      img.alt = 'Red photo';
    }

    function showBlue() {
      img.src = 'https://via.placeholder.com/300/blue';
      img.alt = 'Blue photo';
    }
  </script>
</body>
</html>
```
</details>

### Exercise 3: Form Input to Display

Create a form with name and email inputs. When the user types, immediately show their input in a preview card.

<details>
<summary>Solution</summary>

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .card { border: 1px solid #ccc; padding: 20px; margin-top: 20px; }
  </style>
</head>
<body>
  <input type="text" id="name" placeholder="Enter name">
  <input type="email" id="email" placeholder="Enter email">

  <div class="card">
    <h3 id="displayName">Name will appear here</h3>
    <p id="displayEmail">Email will appear here</p>
  </div>

  <script>
    const nameInput = document.querySelector('#name');
    const emailInput = document.querySelector('#email');
    const displayName = document.querySelector('#displayName');
    const displayEmail = document.querySelector('#displayEmail');

    nameInput.addEventListener('input', () => {
      displayName.textContent = nameInput.value || 'Name will appear here';
    });

    emailInput.addEventListener('input', () => {
      displayEmail.textContent = emailInput.value || 'Email will appear here';
    });
  </script>
</body>
</html>
```
</details>

---

## 🎯 Key Takeaways

✅ **textContent** - Change plain text (safe, fast)
✅ **innerHTML** - Change HTML content (powerful but can be dangerous)
✅ **Never use innerHTML with user input** - Use textContent instead
✅ **element.property** - Change attributes (src, href, alt, etc.)
✅ **element.value** - Get/set form input values
✅ **element.checked** - Get/set checkbox state
✅ **Always check if element exists** before changing it

---

## 🔗 What's Next?

You can select elements and change their content. Next up: **Event Listeners** - making things happen when users interact!

**Next:** [03 - Event Listeners](./03-event-listeners.md)

---

**You can now change any element on the page dynamically. Power! ⚡**
