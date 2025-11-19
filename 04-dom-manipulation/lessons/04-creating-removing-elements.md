# DOM Manipulation 04 - Creating and Removing Elements

> **"Sometimes you need to build HTML on the fly. Here's how to do it efficiently."**

---

## 🎯 What You'll Learn

- How to create new elements with JavaScript
- How to add elements to the page (4 different methods)
- How to remove elements (safely and efficiently)
- How to clone elements
- How to replace elements
- DocumentFragment for performance
- Real-world patterns and examples
- Common mistakes and how to avoid them

**Time to complete:** 35-45 minutes

---

## ✨ Creating New Elements

### createElement()

```javascript
const newElement = document.createElement('tagName');
```

### Example: Create a Paragraph

```javascript
const paragraph = document.createElement('p');
paragraph.textContent = 'This is a new paragraph';
console.log(paragraph); // <p>This is a new paragraph</p>

// IMPORTANT: It's created but NOT yet on the page!
// You must add it to the DOM to see it
```

### Example: Create a Button with Attributes

```javascript
const button = document.createElement('button');
button.textContent = 'Click Me';
button.className = 'btn btn-primary';
button.id = 'myBtn';
button.setAttribute('data-action', 'submit');

// Add event listener before adding to page
button.addEventListener('click', () => {
  console.log('Button clicked!');
});
```

### Example: Create Complex Element

```javascript
const card = document.createElement('div');
card.className = 'card';

// Set inline styles
card.style.padding = '20px';
card.style.border = '1px solid #ccc';
card.style.borderRadius = '8px';

// Set attributes
card.setAttribute('data-id', '123');
card.setAttribute('role', 'article');
```

---

## ➕ Adding Elements to the Page

### Method 1: appendChild() - Add to End

**Most common method - works everywhere**

```javascript
parentElement.appendChild(childElement);
```

```html
<div id="container"></div>

<script>
  const container = document.querySelector('#container');

  const paragraph = document.createElement('p');
  paragraph.textContent = 'Hello!';

  container.appendChild(paragraph);
  // Result: <div id="container"><p>Hello!</p></div>
</script>
```

**Returns:** The appended element

```javascript
const addedElement = container.appendChild(paragraph);
console.log(addedElement === paragraph); // true
```

### Method 2: append() - Add Multiple (Modern)

**Can add multiple elements and text at once**

```javascript
parent.append(child1, child2, 'text', child3);
```

```javascript
const container = document.querySelector('#container');

const p1 = document.createElement('p');
p1.textContent = 'First';

const p2 = document.createElement('p');
p2.textContent = 'Second';

// Add all at once!
container.append(p1, p2, 'Some text', document.createElement('hr'));
```

**Differences from appendChild:**
- `append()` can add multiple items
- `append()` can add text directly
- `append()` doesn't return anything
- `append()` is newer (IE doesn't support it)

```javascript
// appendChild only takes one element
parent.appendChild(child1); // ✅ Works
parent.appendChild(child1, child2); // ❌ Only adds child1

// append takes multiple
parent.append(child1, child2, 'text'); // ✅ Adds all
```

### Method 3: prepend() - Add to Beginning

**Add elements to the start instead of the end**

```javascript
parent.prepend(child);
```

```javascript
const list = document.querySelector('ul');
const newItem = document.createElement('li');
newItem.textContent = 'First item';

list.prepend(newItem); // Adds to top of list
```

**Real Example: Adding "Back to Top" Button**

```html
<body>
  <h1>Page Title</h1>
  <p>Content...</p>

  <script>
    const button = document.createElement('button');
    button.textContent = '↑ Back to Top';
    button.onclick = () => window.scrollTo(0, 0);

    document.body.prepend(button); // Adds at very top
  </script>
</body>
```

### Method 4: insertBefore() - Insert at Specific Position

**Insert element before a reference element**

```javascript
parent.insertBefore(newElement, referenceElement);
```

```html
<ul id="list">
  <li id="item2">Item 2</li>
  <li>Item 3</li>
</ul>

<script>
  const list = document.querySelector('#list');
  const item2 = document.querySelector('#item2');

  const item1 = document.createElement('li');
  item1.textContent = 'Item 1';

  list.insertBefore(item1, item2);
  // Now: Item 1, Item 2, Item 3
</script>
```

**Insert at end using insertBefore:**

```javascript
// Insert at end (before null = at end)
parent.insertBefore(newElement, null);
// Same as appendChild(newElement)
```

### Method 5: insertAdjacentHTML() - Insert HTML String

**Powerful method for inserting HTML directly**

```javascript
element.insertAdjacentHTML(position, htmlString);
```

**Positions:**
- `'beforebegin'` - Before the element itself
- `'afterbegin'` - Inside, before first child
- `'beforeend'` - Inside, after last child
- `'afterend'` - After the element itself

```html
<!-- beforebegin -->
<div id="target">
  <!-- afterbegin -->
  existing content
  <!-- beforeend -->
</div>
<!-- afterend -->
```

**Example:**

```javascript
const container = document.querySelector('#container');

container.insertAdjacentHTML('beforeend', '<p>New paragraph</p>');
// Adds <p> as last child

container.insertAdjacentHTML('afterbegin', '<h2>Title</h2>');
// Adds <h2> as first child
```

**When to use:**
- ✅ Quick insertion of simple HTML
- ✅ When you have HTML strings from server
- ❌ When you need event listeners (use createElement instead)
- ❌ With user input (XSS vulnerability!)

---

## 🗑️ Removing Elements

### Method 1: remove() (Modern & Simple)

**Recommended method - clean and simple**

```javascript
element.remove();
```

```html
<div id="message">This will be removed</div>
<button onclick="removeMessage()">Remove</button>

<script>
  function removeMessage() {
    const message = document.querySelector('#message');
    message.remove();
  }
</script>
```

### Method 2: removeChild() (Older Method)

**Required if supporting old browsers**

```javascript
parent.removeChild(child);
```

```javascript
const list = document.querySelector('ul');
const firstItem = list.querySelector('li');

list.removeChild(firstItem);
```

**Remove using parent:**

```javascript
// Remove element if you don't have parent reference
const element = document.querySelector('.item');
element.parentElement.removeChild(element);

// Modern way is simpler:
element.remove();
```

### Remove All Children

**Method 1: innerHTML (Fast but loses event listeners)**

```javascript
element.innerHTML = '';
```

⚠️ **Warning:** This removes event listeners and can cause memory leaks!

**Method 2: While Loop (Safe)**

```javascript
while (element.firstChild) {
  element.removeChild(element.firstChild);
}
```

**Method 3: Modern replaceChildren (Best)**

```javascript
element.replaceChildren(); // Removes all children
```

### Remove Multiple Elements

```javascript
const items = document.querySelectorAll('.item');

items.forEach(item => item.remove());
```

---

## 🔄 Replacing Elements

### replaceChild()

```javascript
parent.replaceChild(newChild, oldChild);
```

```html
<div id="container">
  <p id="old">Old paragraph</p>
</div>

<script>
  const container = document.querySelector('#container');
  const oldP = document.querySelector('#old');

  const newP = document.createElement('p');
  newP.textContent = 'New paragraph';
  newP.className = 'highlight';

  container.replaceChild(newP, oldP);
</script>
```

### replaceWith() (Modern)

```javascript
oldElement.replaceWith(newElement);
```

```javascript
const old = document.querySelector('#old');
const newEl = document.createElement('div');
newEl.textContent = 'Replaced!';

old.replaceWith(newEl); // Much simpler!
```

---

## 📋 Cloning Elements

### cloneNode()

**Clone an element and optionally its children**

```javascript
const clone = element.cloneNode(deep);
// deep = true: clone element and all descendants
// deep = false: clone only element (no children)
```

### Example: Shallow Clone

```javascript
const original = document.querySelector('#card');
const clone = original.cloneNode(false); // Only clones <div id="card">
// Children are NOT cloned
```

### Example: Deep Clone

```javascript
const original = document.querySelector('#card');
const clone = original.cloneNode(true); // Clones everything inside too
```

### Real Example: Duplicate Card

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .card {
      border: 1px solid #ccc;
      padding: 20px;
      margin: 10px;
    }
  </style>
</head>
<body>
  <div id="original" class="card">
    <h3>Original Card</h3>
    <p>This is the original content</p>
    <button onclick="duplicateCard()">Duplicate Me</button>
  </div>

  <div id="container"></div>

  <script>
    function duplicateCard() {
      const original = document.querySelector('#original');
      const clone = original.cloneNode(true); // Deep clone

      // Modify clone
      clone.id = ''; // Remove ID to avoid duplicates
      clone.querySelector('h3').textContent = 'Cloned Card';

      // Add to page
      document.querySelector('#container').appendChild(clone);
    }
  </script>
</body>
</html>
```

**Important Notes:**
- ID attributes are cloned too (can cause duplicate IDs!)
- Event listeners added with `addEventListener` are NOT cloned
- Event listeners in HTML attributes (onclick) ARE cloned

```javascript
const original = document.querySelector('#btn');
original.addEventListener('click', () => console.log('Clicked'));

const clone = original.cloneNode(true);
// clone does NOT have the click listener!
// You must add it again
clone.addEventListener('click', () => console.log('Clicked'));
```

---

## ⚡ DocumentFragment (Performance Optimization)

### What is DocumentFragment?

A lightweight container to build DOM structures off-screen, then add all at once.

**Why use it?**
- Adding elements one by one = multiple reflows (slow)
- Adding all at once with DocumentFragment = one reflow (fast)

### Without DocumentFragment (Slow)

```javascript
const list = document.querySelector('ul');

for (let i = 0; i < 1000; i++) {
  const li = document.createElement('li');
  li.textContent = `Item ${i}`;
  list.appendChild(li); // Reflows 1000 times! 😱
}
```

### With DocumentFragment (Fast)

```javascript
const list = document.querySelector('ul');
const fragment = document.createDocumentFragment();

for (let i = 0; i < 1000; i++) {
  const li = document.createElement('li');
  li.textContent = `Item ${i}`;
  fragment.appendChild(li); // Builds off-screen
}

list.appendChild(fragment); // One reflow! 🚀
```

**Performance gain:** Can be 10x-100x faster for many elements!

### Real Example: Building a Large List

```html
<!DOCTYPE html>
<html>
<body>
  <button onclick="buildList()">Build 500 Items</button>
  <ul id="list"></ul>

  <script>
    function buildList() {
      const start = performance.now();

      const list = document.querySelector('#list');
      const fragment = document.createDocumentFragment();

      for (let i = 1; i <= 500; i++) {
        const li = document.createElement('li');
        li.textContent = `Item ${i}`;
        li.className = i % 2 === 0 ? 'even' : 'odd';
        fragment.appendChild(li);
      }

      list.appendChild(fragment);

      const end = performance.now();
      console.log(`Built in ${end - start}ms`);
    }
  </script>
</body>
</html>
```

---

## 🎯 Real-World Examples

### Example 1: Todo List (Complete)

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .todo-item {
      display: flex;
      align-items: center;
      gap: 10px;
      padding: 10px;
      border-bottom: 1px solid #ddd;
    }
    .todo-item.completed {
      text-decoration: line-through;
      opacity: 0.6;
    }
  </style>
</head>
<body>
  <input type="text" id="todoInput" placeholder="Enter task">
  <button onclick="addTodo()">Add</button>
  <ul id="todoList"></ul>

  <script>
    function addTodo() {
      const input = document.querySelector('#todoInput');
      const list = document.querySelector('#todoList');

      if (input.value.trim() === '') return;

      // Create list item
      const li = document.createElement('li');
      li.className = 'todo-item';

      // Create checkbox
      const checkbox = document.createElement('input');
      checkbox.type = 'checkbox';
      checkbox.onchange = () => {
        li.classList.toggle('completed');
      };

      // Create text span
      const text = document.createElement('span');
      text.textContent = input.value;

      // Create delete button
      const deleteBtn = document.createElement('button');
      deleteBtn.textContent = '×';
      deleteBtn.onclick = () => li.remove();

      // Assemble
      li.append(checkbox, text, deleteBtn);
      list.appendChild(li);

      input.value = '';
    }

    // Enter key to add
    document.querySelector('#todoInput').addEventListener('keypress', (e) => {
      if (e.key === 'Enter') addTodo();
    });
  </script>
</body>
</html>
```

### Example 2: Dynamic User Cards

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .card-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
      gap: 1rem;
      padding: 1rem;
    }
    .card {
      border: 1px solid #ddd;
      padding: 1.5rem;
      border-radius: 8px;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    }
    .card-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 1rem;
    }
    .remove-btn {
      background: #e74c3c;
      color: white;
      border: none;
      padding: 0.5rem 1rem;
      border-radius: 4px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <button onclick="addCard()">Add User Card</button>
  <div id="container" class="card-grid"></div>

  <script>
    const users = ['Alice', 'Bob', 'Charlie', 'Diana', 'Eve', 'Frank'];
    let userIndex = 0;

    function addCard() {
      const container = document.querySelector('#container');

      // Create card
      const card = document.createElement('div');
      card.className = 'card';

      // Create header
      const header = document.createElement('div');
      header.className = 'card-header';

      // Create title
      const title = document.createElement('h3');
      const username = users[userIndex % users.length];
      title.textContent = username;
      userIndex++;

      // Create remove button
      const removeBtn = document.createElement('button');
      removeBtn.className = 'remove-btn';
      removeBtn.textContent = '×';
      removeBtn.onclick = () => {
        // Fade out animation before removing
        card.style.opacity = '0';
        card.style.transition = 'opacity 0.3s';
        setTimeout(() => card.remove(), 300);
      };

      // Create content
      const content = document.createElement('p');
      content.textContent = `Email: ${username.toLowerCase()}@example.com`;

      const role = document.createElement('p');
      role.textContent = 'Role: Developer';
      role.style.color = '#666';
      role.style.fontSize = '0.9rem';

      // Assemble
      header.append(title, removeBtn);
      card.append(header, content, role);
      container.appendChild(card);
    }
  </script>
</body>
</html>
```

### Example 3: Notification System

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .notification-container {
      position: fixed;
      top: 20px;
      right: 20px;
      width: 300px;
      z-index: 1000;
    }
    .notification {
      background: white;
      padding: 1rem;
      margin-bottom: 0.5rem;
      border-radius: 4px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.2);
      animation: slideIn 0.3s ease;
    }
    .notification.success { border-left: 4px solid #27ae60; }
    .notification.error { border-left: 4px solid #e74c3c; }
    .notification.info { border-left: 4px solid #3498db; }

    @keyframes slideIn {
      from {
        transform: translateX(400px);
        opacity: 0;
      }
      to {
        transform: translateX(0);
        opacity: 1;
      }
    }
  </style>
</head>
<body>
  <button onclick="showNotification('Success!', 'success')">Success</button>
  <button onclick="showNotification('Error occurred', 'error')">Error</button>
  <button onclick="showNotification('Info message', 'info')">Info</button>

  <div class="notification-container" id="notifications"></div>

  <script>
    function showNotification(message, type = 'info') {
      const container = document.querySelector('#notifications');

      // Create notification
      const notification = document.createElement('div');
      notification.className = `notification ${type}`;
      notification.textContent = message;

      // Add to page
      container.appendChild(notification);

      // Auto remove after 3 seconds
      setTimeout(() => {
        notification.style.opacity = '0';
        notification.style.transition = 'opacity 0.3s';
        setTimeout(() => notification.remove(), 300);
      }, 3000);
    }
  </script>
</body>
</html>
```

---

## ⚠️ Common Mistakes

### Mistake 1: Not Adding Element to DOM

```javascript
// ❌ Created but never added!
const p = document.createElement('p');
p.textContent = 'Hello';
// Element exists in memory but NOT on page!

// ✅ Must add to DOM
document.body.appendChild(p);
```

### Mistake 2: Duplicate IDs When Cloning

```javascript
// ❌ Creates duplicate IDs
const original = document.querySelector('#card');
const clone = original.cloneNode(true);
document.body.appendChild(clone);
// Now two elements with id="card"!

// ✅ Remove or change ID
const clone = original.cloneNode(true);
clone.id = ''; // Remove ID
// Or give unique ID
clone.id = 'card-' + Date.now();
document.body.appendChild(clone);
```

### Mistake 3: Removing While Iterating

```javascript
// ❌ WRONG - Skips elements!
const items = document.querySelectorAll('.item');
items.forEach(item => {
  item.remove(); // Changes NodeList while iterating!
});

// ✅ CORRECT - Convert to array first
const items = Array.from(document.querySelectorAll('.item'));
items.forEach(item => item.remove());

// ✅ OR iterate backwards
const items = document.querySelectorAll('.item');
for (let i = items.length - 1; i >= 0; i--) {
  items[i].remove();
}
```

### Mistake 4: Using innerHTML with Event Listeners

```javascript
// ❌ Loses event listeners
const btn = document.querySelector('#btn');
btn.addEventListener('click', () => console.log('Clicked'));

container.innerHTML = ''; // Event listener is lost!

// ✅ Use removeChild or remove()
while (container.firstChild) {
  container.removeChild(container.firstChild);
}
```

### Mistake 5: insertAdjacentHTML with User Input

```javascript
// ❌ DANGEROUS - XSS vulnerability
const userInput = prompt('Enter name');
div.insertAdjacentHTML('beforeend', `<p>${userInput}</p>`);
// If user enters: <img src=x onerror="alert('hacked')">

// ✅ SAFE - Use createElement + textContent
const p = document.createElement('p');
p.textContent = userInput; // Treated as text, not HTML
div.appendChild(p);
```

---

## 🎯 Practice Exercises

### Exercise 1: Shopping Cart

Create a shopping cart where users can:
- Add items with name and price
- Remove individual items
- See total price

<details>
<summary>Solution</summary>

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .cart-item { display: flex; justify-content: space-between; padding: 10px; border-bottom: 1px solid #ddd; }
    .total { font-size: 1.5rem; font-weight: bold; margin-top: 20px; }
  </style>
</head>
<body>
  <input type="text" id="itemName" placeholder="Item name">
  <input type="number" id="itemPrice" placeholder="Price">
  <button onclick="addItem()">Add to Cart</button>

  <div id="cart"></div>
  <div class="total">Total: $<span id="total">0.00</span></div>

  <script>
    function addItem() {
      const name = document.querySelector('#itemName').value;
      const price = parseFloat(document.querySelector('#itemPrice').value);

      if (!name || !price) return;

      const cart = document.querySelector('#cart');

      const item = document.createElement('div');
      item.className = 'cart-item';
      item.dataset.price = price;

      const itemText = document.createElement('span');
      itemText.textContent = `${name} - $${price.toFixed(2)}`;

      const removeBtn = document.createElement('button');
      removeBtn.textContent = 'Remove';
      removeBtn.onclick = () => {
        item.remove();
        updateTotal();
      };

      item.append(itemText, removeBtn);
      cart.appendChild(item);

      document.querySelector('#itemName').value = '';
      document.querySelector('#itemPrice').value = '';

      updateTotal();
    }

    function updateTotal() {
      const items = document.querySelectorAll('.cart-item');
      let total = 0;
      items.forEach(item => {
        total += parseFloat(item.dataset.price);
      });
      document.querySelector('#total').textContent = total.toFixed(2);
    }
  </script>
</body>
</html>
```
</details>

### Exercise 2: Table Generator

Create a function that generates an HTML table with specified rows and columns.

<details>
<summary>Solution</summary>

```javascript
function createTable(rows, cols) {
  const table = document.createElement('table');
  table.style.borderCollapse = 'collapse';

  for (let i = 0; i < rows; i++) {
    const tr = document.createElement('tr');

    for (let j = 0; j < cols; j++) {
      const td = document.createElement('td');
      td.textContent = `R${i+1}C${j+1}`;
      td.style.border = '1px solid black';
      td.style.padding = '10px';
      tr.appendChild(td);
    }

    table.appendChild(tr);
  }

  return table;
}

// Usage
const myTable = createTable(5, 3);
document.body.appendChild(myTable);
```
</details>

### Exercise 3: Star Rating Component

Build a 5-star rating system where clicking a star fills it and all stars before it.

<details>
<summary>Solution</summary>

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .star {
      font-size: 2rem;
      cursor: pointer;
      color: #ddd;
    }
    .star.filled {
      color: #ffd700;
    }
  </style>
</head>
<body>
  <div id="rating"></div>
  <p>Rating: <span id="ratingValue">0</span>/5</p>

  <script>
    function createStarRating() {
      const container = document.querySelector('#rating');

      for (let i = 1; i <= 5; i++) {
        const star = document.createElement('span');
        star.className = 'star';
        star.textContent = '★';
        star.dataset.value = i;

        star.addEventListener('click', function() {
          const value = parseInt(this.dataset.value);

          // Update all stars
          const stars = document.querySelectorAll('.star');
          stars.forEach((s, index) => {
            if (index < value) {
              s.classList.add('filled');
            } else {
              s.classList.remove('filled');
            }
          });

          // Update rating value
          document.querySelector('#ratingValue').textContent = value;
        });

        container.appendChild(star);
      }
    }

    createStarRating();
  </script>
</body>
</html>
```
</details>

---

## 🎯 Key Takeaways

✅ **createElement()** - Create new elements
✅ **appendChild()/append()** - Add to page (append can add multiple)
✅ **prepend()** - Add to beginning
✅ **insertBefore()** - Insert at specific position
✅ **insertAdjacentHTML()** - Insert HTML strings (careful with XSS!)
✅ **remove()** - Delete element (modern method)
✅ **cloneNode(true)** - Deep clone with children
✅ **DocumentFragment** - Optimize performance when adding many elements
✅ **replaceWith()** - Replace elements easily
✅ **Always set properties BEFORE adding to DOM** for better performance

---

## 🔗 What's Next?

Now you can create, modify, and remove elements dynamically. Next up: **Classes and Styles** - learn how to change how elements look!

**Next:** [05 - Classes and Styles](./05-classes-and-styles.md)

---

**You can now build dynamic interfaces from scratch! 🎨**
