# DOM Manipulation 03 - Event Listeners

> **"Events are how users interact with your website. This is where magic happens."**

---

## 🎯 What You'll Learn

- What events are and why they matter
- How to listen for events (clicks, typing, scrolling, etc.)
- The event object and useful properties
- Common events and when to use them
- Best practices and common mistakes

**Time to complete:** 30-40 minutes

---

## 🤔 What Are Events?

### The Doorbell Analogy

Imagine your website is a house:
- **Event** = Someone rings the doorbell
- **Event Listener** = You listening for the doorbell
- **Event Handler** = What you do when you hear it (answer the door)

**In web development:**
- **Event** = User action (click, type, scroll, hover, etc.)
- **Event Listener** = JavaScript waiting for that action
- **Event Handler** = Function that runs when the event happens

---

## 🎯 The addEventListener Method

### Syntax
```javascript
element.addEventListener('event', function);
```

### Basic Example

```html
<button id="btn">Click Me</button>

<script>
  const button = document.querySelector('#btn');

  button.addEventListener('click', () => {
    alert('Button was clicked!');
  });
</script>
```

**What happens:**
1. User clicks button
2. Browser detects the 'click' event
3. Your function runs

---

## 🖱️ Common Mouse Events

### 1. click

```html
<button id="btn">Click Me</button>

<script>
  const btn = document.querySelector('#btn');

  btn.addEventListener('click', () => {
    console.log('Button clicked!');
  });
</script>
```

### 2. dblclick (double-click)

```html
<div id="box">Double-click me</div>

<script>
  const box = document.querySelector('#box');

  box.addEventListener('dblclick', () => {
    console.log('Double clicked!');
  });
</script>
```

### 3. mouseenter and mouseleave (hover)

```html
<div id="card">Hover over me</div>

<script>
  const card = document.querySelector('#card');

  card.addEventListener('mouseenter', () => {
    card.style.backgroundColor = 'lightblue';
  });

  card.addEventListener('mouseleave', () => {
    card.style.backgroundColor = 'white';
  });
</script>
```

### 4. mousemove

```html
<div id="tracker" style="width: 300px; height: 300px; border: 1px solid black;"></div>
<p id="coords"></p>

<script>
  const tracker = document.querySelector('#tracker');
  const coords = document.querySelector('#coords');

  tracker.addEventListener('mousemove', (e) => {
    coords.textContent = `X: ${e.offsetX}, Y: ${e.offsetY}`;
  });
</script>
```

---

## ⌨️ Keyboard Events

### 1. keydown (when key is pressed)

```html
<input type="text" id="field" placeholder="Type something">

<script>
  const field = document.querySelector('#field');

  field.addEventListener('keydown', (e) => {
    console.log(`Key pressed: ${e.key}`);
  });
</script>
```

### 2. keyup (when key is released)

```html
<input type="text" id="search" placeholder="Search...">
<p id="result"></p>

<script>
  const search = document.querySelector('#search');
  const result = document.querySelector('#result');

  search.addEventListener('keyup', () => {
    result.textContent = `You typed: ${search.value}`;
  });
</script>
```

### 3. Key Detection

```html
<p>Press any key...</p>

<script>
  document.addEventListener('keydown', (e) => {
    console.log(`Key: ${e.key}`);
    console.log(`Code: ${e.code}`);

    if (e.key === 'Enter') {
      console.log('Enter key pressed!');
    }

    if (e.key === 'Escape') {
      console.log('Escape key pressed!');
    }
  });
</script>
```

---

## 📝 Form Events

### 1. submit (form submission)

```html
<form id="myForm">
  <input type="text" name="username" required>
  <button type="submit">Submit</button>
</form>

<script>
  const form = document.querySelector('#myForm');

  form.addEventListener('submit', (e) => {
    e.preventDefault(); // Prevent page reload

    const formData = new FormData(form);
    const username = formData.get('username');

    console.log(`Submitted: ${username}`);
  });
</script>
```

### 2. input (value changes)

```html
<input type="text" id="field">
<p id="live"></p>

<script>
  const field = document.querySelector('#field');
  const live = document.querySelector('#live');

  field.addEventListener('input', () => {
    live.textContent = field.value;
  });
</script>
```

### 3. change (value changes and loses focus)

```html
<select id="country">
  <option>USA</option>
  <option>UK</option>
  <option>Canada</option>
</select>

<script>
  const select = document.querySelector('#country');

  select.addEventListener('change', () => {
    console.log(`Selected: ${select.value}`);
  });
</script>
```

### 4. focus and blur

```html
<input type="text" id="email" placeholder="Email">

<script>
  const email = document.querySelector('#email');

  email.addEventListener('focus', () => {
    email.style.borderColor = 'blue';
  });

  email.addEventListener('blur', () => {
    email.style.borderColor = 'gray';
  });
</script>
```

---

## 🌐 Window Events

### 1. load (page fully loaded)

```javascript
window.addEventListener('load', () => {
  console.log('Page fully loaded!');
});
```

### 2. DOMContentLoaded (HTML parsed, before images load)

```javascript
document.addEventListener('DOMContentLoaded', () => {
  console.log('DOM is ready!');
});
```

### 3. resize (window resized)

```javascript
window.addEventListener('resize', () => {
  console.log(`Window size: ${window.innerWidth} x ${window.innerHeight}`);
});
```

### 4. scroll

```javascript
window.addEventListener('scroll', () => {
  console.log(`Scrolled: ${window.scrollY}px`);
});
```

---

## 📦 The Event Object

When an event occurs, JavaScript passes an **event object** to your function with useful information.

### Basic Usage

```javascript
element.addEventListener('click', (event) => {
  console.log(event);
});
```

### Common Properties

```javascript
button.addEventListener('click', (e) => {
  console.log(e.type);        // 'click'
  console.log(e.target);      // The clicked element
  console.log(e.clientX);     // Mouse X position
  console.log(e.clientY);     // Mouse Y position
  console.log(e.key);         // Key pressed (keyboard events)
  console.log(e.shiftKey);    // Was Shift held?
  console.log(e.ctrlKey);     // Was Ctrl held?
});
```

### Practical Example: Click Coordinates

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    #box {
      width: 400px;
      height: 400px;
      background: lightgray;
      position: relative;
    }
    .dot {
      width: 10px;
      height: 10px;
      background: red;
      border-radius: 50%;
      position: absolute;
    }
  </style>
</head>
<body>
  <div id="box"></div>

  <script>
    const box = document.querySelector('#box');

    box.addEventListener('click', (e) => {
      const dot = document.createElement('div');
      dot.className = 'dot';
      dot.style.left = e.offsetX + 'px';
      dot.style.top = e.offsetY + 'px';
      box.appendChild(dot);
    });
  </script>
</body>
</html>
```

---

## 🎯 Real-World Examples

### Example 1: Toggle Visibility

```html
<!DOCTYPE html>
<html>
<body>
  <button id="toggleBtn">Show Details</button>
  <div id="details" style="display: none;">
    <p>Here are the details...</p>
  </div>

  <script>
    const btn = document.querySelector('#toggleBtn');
    const details = document.querySelector('#details');

    btn.addEventListener('click', () => {
      if (details.style.display === 'none') {
        details.style.display = 'block';
        btn.textContent = 'Hide Details';
      } else {
        details.style.display = 'none';
        btn.textContent = 'Show Details';
      }
    });
  </script>
</body>
</html>
```

### Example 2: Live Search Filter

```html
<!DOCTYPE html>
<html>
<body>
  <input type="text" id="searchBox" placeholder="Search names...">
  <ul id="nameList">
    <li>Alice</li>
    <li>Bob</li>
    <li>Charlie</li>
    <li>David</li>
    <li>Eve</li>
  </ul>

  <script>
    const searchBox = document.querySelector('#searchBox');
    const names = document.querySelectorAll('#nameList li');

    searchBox.addEventListener('input', () => {
      const searchTerm = searchBox.value.toLowerCase();

      names.forEach(name => {
        const text = name.textContent.toLowerCase();

        if (text.includes(searchTerm)) {
          name.style.display = 'block';
        } else {
          name.style.display = 'none';
        }
      });
    });
  </script>
</body>
</html>
```

### Example 3: Form Validation

```html
<!DOCTYPE html>
<html>
<body>
  <form id="signupForm">
    <input type="email" id="email" placeholder="Email" required>
    <p id="error" style="color: red;"></p>
    <button type="submit">Sign Up</button>
  </form>

  <script>
    const form = document.querySelector('#signupForm');
    const emailInput = document.querySelector('#email');
    const error = document.querySelector('#error');

    form.addEventListener('submit', (e) => {
      e.preventDefault();

      const email = emailInput.value;

      if (!email.includes('@')) {
        error.textContent = 'Please enter a valid email';
        return;
      }

      error.textContent = '';
      console.log(`Email submitted: ${email}`);
    });
  </script>
</body>
</html>
```

---

## ⚠️ Common Mistakes

### Mistake 1: Forgetting Parentheses

```javascript
// ❌ WRONG - Calls function immediately
button.addEventListener('click', myFunction());

// ✅ CORRECT - Passes function reference
button.addEventListener('click', myFunction);

// ✅ OR use arrow function
button.addEventListener('click', () => myFunction());
```

### Mistake 2: Not Preventing Default

```javascript
// ❌ Form will reload page
form.addEventListener('submit', () => {
  console.log('Submitted');
});

// ✅ Prevent page reload
form.addEventListener('submit', (e) => {
  e.preventDefault();
  console.log('Submitted');
});
```

### Mistake 3: Forgetting Event Parameter

```javascript
// ❌ Can't access event properties
button.addEventListener('click', () => {
  console.log(e.target); // ERROR: e is not defined
});

// ✅ Include event parameter
button.addEventListener('click', (e) => {
  console.log(e.target); // Works!
});
```

---

## 🎯 Practice Exercises

### Exercise 1: Color Changer

Create 3 buttons (Red, Green, Blue) that change the background color of the page.

<details>
<summary>Solution</summary>

```html
<!DOCTYPE html>
<html>
<body>
  <button id="red">Red</button>
  <button id="green">Green</button>
  <button id="blue">Blue</button>

  <script>
    document.querySelector('#red').addEventListener('click', () => {
      document.body.style.backgroundColor = 'red';
    });

    document.querySelector('#green').addEventListener('click', () => {
      document.body.style.backgroundColor = 'green';
    });

    document.querySelector('#blue').addEventListener('click', () => {
      document.body.style.backgroundColor = 'blue';
    });
  </script>
</body>
</html>
```
</details>

### Exercise 2: Escape Key to Close

Create a modal that closes when you press the Escape key.

<details>
<summary>Solution</summary>

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .modal {
      display: block;
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background: white;
      padding: 40px;
      border: 2px solid black;
    }
    .hidden { display: none; }
  </style>
</head>
<body>
  <div class="modal" id="modal">
    <h2>Press Escape to close</h2>
  </div>

  <script>
    const modal = document.querySelector('#modal');

    document.addEventListener('keydown', (e) => {
      if (e.key === 'Escape') {
        modal.classList.add('hidden');
      }
    });
  </script>
</body>
</html>
```
</details>

---

## 🎯 Key Takeaways

✅ **addEventListener** - Modern way to handle events
✅ **e.preventDefault()** - Stop default behavior (essential for forms)
✅ **Event object (e)** - Contains useful information
✅ **Common events**: click, input, submit, keydown, mouseenter
✅ **Always check if element exists** before adding listener

---

**Next:** [04 - Creating and Removing Elements](./04-creating-removing-elements.md)

---

**You can now make websites interactive! 🎉**
