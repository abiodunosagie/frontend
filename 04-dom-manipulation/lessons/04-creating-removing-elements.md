# DOM Manipulation 04 - Creating and Removing Elements

> **"Sometimes you need to build HTML on the fly. Here's how."**

---

## 🎯 What You'll Learn

- How to create new elements with JavaScript
- How to add elements to the page
- How to remove elements
- How to clone elements
- Real-world examples

**Time to complete:** 25-30 minutes

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

// Note: It's created but NOT yet on the page!
```

### Example: Create a Button

```javascript
const button = document.createElement('button');
button.textContent = 'Click Me';
button.className = 'btn btn-primary';
button.id = 'myBtn';
```

---

## ➕ Adding Elements to the Page

### Method 1: appendChild() - Add to End

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

### Method 2: append() - Add Multiple (Modern)

```javascript
parent.append(child1, child2, 'text');
```

```javascript
const container = document.querySelector('#container');

const p1 = document.createElement('p');
p1.textContent = 'First';

const p2 = document.createElement('p');
p2.textContent = 'Second';

container.append(p1, p2, 'Some text');
```

### Method 3: prepend() - Add to Beginning

```javascript
parent.prepend(child);
```

```javascript
const list = document.querySelector('ul');
const newItem = document.createElement('li');
newItem.textContent = 'First item';

list.prepend(newItem); // Adds to top of list
```

### Method 4: insertBefore() - Insert at Specific Position

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

---

## 🗑️ Removing Elements

### Method 1: remove() (Modern)

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

### Method 2: removeChild() (Older)

```javascript
parent.removeChild(child);
```

```javascript
const list = document.querySelector('ul');
const firstItem = list.querySelector('li');

list.removeChild(firstItem);
```

### Remove All Children

```javascript
element.innerHTML = ''; // Fast but removes event listeners
```

Or:

```javascript
while (element.firstChild) {
  element.removeChild(element.firstChild);
}
```

---

## 🎯 Real-World Examples

### Example 1: Todo List

```html
<!DOCTYPE html>
<html>
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
      li.textContent = input.value;
      
      // Create delete button
      const deleteBtn = document.createElement('button');
      deleteBtn.textContent = 'Delete';
      deleteBtn.onclick = () => li.remove();
      
      li.appendChild(deleteBtn);
      list.appendChild(li);
      
      input.value = ''; // Clear input
    }
  </script>
</body>
</html>
```

### Example 2: Dynamic Cards

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .card {
      border: 1px solid #ccc;
      padding: 20px;
      margin: 10px;
      border-radius: 8px;
    }
  </style>
</head>
<body>
  <button onclick="addCard()">Add Card</button>
  <div id="container"></div>

  <script>
    let cardCount = 0;

    function addCard() {
      cardCount++;
      
      const container = document.querySelector('#container');
      
      const card = document.createElement('div');
      card.className = 'card';
      
      const title = document.createElement('h3');
      title.textContent = `Card ${cardCount}`;
      
      const text = document.createElement('p');
      text.textContent = 'This is card content';
      
      const removeBtn = document.createElement('button');
      removeBtn.textContent = 'Remove';
      removeBtn.onclick = () => card.remove();
      
      card.append(title, text, removeBtn);
      container.appendChild(card);
    }
  </script>
</body>
</html>
```

---

## 🎯 Key Takeaways

✅ **createElement()** - Create new element
✅ **appendChild()/append()** - Add to page
✅ **remove()** - Delete element
✅ **Set properties before adding** to page
✅ **Chain methods** for efficiency

---

**Next:** [05 - Classes and Styles](./05-classes-and-styles.md)
