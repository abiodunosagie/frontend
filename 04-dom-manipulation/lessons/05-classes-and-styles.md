# DOM Manipulation 05 - Classes and Styles

> **"The final piece: changing how elements look dynamically with JavaScript."**

---

## 🎯 What You'll Learn

- How to add/remove/toggle CSS classes
- How to check if element has a class
- How to change inline styles
- How to read computed styles
- When to use classes vs inline styles
- Real-world patterns and complete examples
- Common mistakes and performance tips

**Time to complete:** 30-40 minutes

---

## 🎨 Working with Classes

### classList API

**The modern way to manipulate classes**

```javascript
element.classList.add('className');
element.classList.remove('className');
element.classList.toggle('className');
element.classList.contains('className');
element.classList.replace('oldClass', 'newClass');
```

---

### classList.add() - Add a Class

**Add one or more classes**

```javascript
element.classList.add('className');
```

```html
<div id="box">Box</div>

<script>
  const box = document.querySelector('#box');
  box.classList.add('active');
  // Result: <div id="box" class="active">Box</div>
</script>
```

**Add multiple classes at once:**

```javascript
element.classList.add('class1', 'class2', 'class3');
```

```javascript
const card = document.querySelector('.card');
card.classList.add('highlighted', 'large', 'shadow');
// <div class="card highlighted large shadow">
```

---

### classList.remove() - Remove a Class

**Remove one or more classes**

```javascript
element.classList.remove('className');
```

```javascript
const button = document.querySelector('#btn');
button.classList.remove('disabled');
```

**Remove multiple:**

```javascript
element.classList.remove('class1', 'class2');
```

---

### classList.toggle() - Toggle a Class

**Add if missing, remove if present**

```javascript
element.classList.toggle('className');
```

```html
<button id="btn">Toggle Dark Mode</button>

<script>
  const btn = document.querySelector('#btn');

  btn.addEventListener('click', () => {
    document.body.classList.toggle('dark-mode');
  });
</script>
```

**Toggle with condition (force add/remove):**

```javascript
// Force add (like classList.add)
element.classList.toggle('active', true);

// Force remove (like classList.remove)
element.classList.toggle('active', false);
```

**Practical example:**

```javascript
const checkbox = document.querySelector('#agree');
const submitBtn = document.querySelector('#submit');

checkbox.addEventListener('change', () => {
  // Disable submit button if checkbox not checked
  submitBtn.classList.toggle('disabled', !checkbox.checked);
});
```

---

### classList.contains() - Check if Has Class

**Returns true/false**

```javascript
if (element.classList.contains('active')) {
  console.log('Element is active');
}
```

**Real example:**

```javascript
const card = document.querySelector('.card');

if (card.classList.contains('highlighted')) {
  console.log('Already highlighted');
} else {
  card.classList.add('highlighted');
}
```

---

### classList.replace() - Replace Class

**Replace one class with another**

```javascript
element.classList.replace('oldClass', 'newClass');
```

```javascript
const btn = document.querySelector('#btn');
btn.classList.replace('btn-primary', 'btn-success');
// Changes from blue button to green button
```

---

## 🎨 Working with Inline Styles

### element.style.property = value

**Change CSS properties directly via JavaScript**

```javascript
element.style.color = 'red';
element.style.backgroundColor = 'blue';
element.style.fontSize = '20px';
```

**Important notes:**
- CSS property names use camelCase: `background-color` → `backgroundColor`
- Values must be strings with units: `'20px'` not `20`
- Multiple words: `font-size` → `fontSize`

### Example: Dynamic Positioning

```javascript
const box = document.querySelector('#box');

box.style.position = 'absolute';
box.style.top = '100px';
box.style.left = '200px';
box.style.width = '150px';
box.style.height = '150px';
box.style.backgroundColor = '#3498db';
```

### Example: Hover Effect with JavaScript

```html
<div id="card">Hover me</div>

<script>
  const card = document.querySelector('#card');

  card.addEventListener('mouseenter', () => {
    card.style.backgroundColor = 'lightblue';
    card.style.transform = 'scale(1.1)';
    card.style.transition = 'all 0.3s ease';
  });

  card.addEventListener('mouseleave', () => {
    card.style.backgroundColor = '';
    card.style.transform = '';
  });
</script>
```

### Setting Multiple Styles

**Method 1: One by one**
```javascript
element.style.color = 'white';
element.style.backgroundColor = 'black';
element.style.padding = '20px';
```

**Method 2: cssText (overwrites all styles)**
```javascript
element.style.cssText = 'color: white; background: black; padding: 20px;';
```

**Method 3: setAttribute**
```javascript
element.setAttribute('style', 'color: white; background: black; padding: 20px;');
```

⚠️ **Methods 2 and 3 overwrite ALL inline styles!**

---

## 📊 Reading Styles

### element.style (Only Inline Styles)

```javascript
const div = document.querySelector('div');
console.log(div.style.color); // Only shows inline style!
```

**This only returns inline styles, NOT CSS from stylesheets!**

### getComputedStyle() - Get Actual Applied Styles

**Get all computed styles (including from CSS files)**

```javascript
const styles = getComputedStyle(element);
const color = styles.color;
const fontSize = styles.fontSize;
```

```html
<style>
  .box {
    width: 200px;
    height: 200px;
    background: blue;
  }
</style>

<div class="box"></div>

<script>
  const box = document.querySelector('.box');

  // ❌ This returns nothing (no inline style)
  console.log(box.style.width); // ""

  // ✅ This returns actual computed width
  const styles = getComputedStyle(box);
  console.log(styles.width); // "200px"
  console.log(styles.backgroundColor); // "rgb(0, 0, 255)"
</script>
```

**Get specific property:**

```javascript
const element = document.querySelector('.card');
const bgColor = getComputedStyle(element).backgroundColor;
const padding = getComputedStyle(element).padding;
```

---

## ✅ Classes vs Inline Styles - When to Use Each

### Use Classes (Recommended 95% of the Time)

**Advantages:**
- ✅ Reusable across multiple elements
- ✅ Easier to maintain
- ✅ Better performance
- ✅ Styled in CSS where it belongs
- ✅ Can use pseudo-classes (:hover, :focus)
- ✅ Can use media queries
- ✅ Easier to animate with CSS transitions

```css
/* Define once in CSS */
.highlighted {
  background: yellow;
  font-weight: bold;
  border: 2px solid orange;
}

.error {
  color: red;
  border: 1px solid red;
}
```

```javascript
// Use anywhere
element.classList.add('highlighted');
input.classList.add('error');
```

### Use Inline Styles

**Only for dynamic values that can't be predefined:**
- ✅ Dynamic positions (calculated coordinates)
- ✅ Dynamic dimensions (calculated sizes)
- ✅ Progress bars (width percentage)
- ✅ Values from user input
- ✅ Animation frame-by-frame changes

```javascript
// Good use of inline styles
element.style.top = mouseY + 'px';
element.style.left = mouseX + 'px';
element.style.width = percentage + '%';
```

---

## 🎯 Real-World Examples

### Example 1: Dark Mode Toggle (Complete)

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      background: white;
      color: #333;
      transition: all 0.3s;
      font-family: Arial, sans-serif;
      padding: 40px;
    }

    body.dark {
      background: #1a1a1a;
      color: #f0f0f0;
    }

    .card {
      background: white;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
      margin: 20px 0;
    }

    body.dark .card {
      background: #2a2a2a;
      box-shadow: 0 2px 8px rgba(0,0,0,0.5);
    }

    button {
      padding: 10px 20px;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      font-size: 16px;
    }

    .theme-toggle {
      background: #3498db;
      color: white;
    }
  </style>
</head>
<body>
  <button class="theme-toggle" id="toggleTheme">Toggle Dark Mode</button>

  <div class="card">
    <h2>Card Title</h2>
    <p>This is some card content that adapts to dark mode.</p>
  </div>

  <script>
    const toggleBtn = document.querySelector('#toggleTheme');

    toggleBtn.addEventListener('click', () => {
      document.body.classList.toggle('dark');

      // Update button text
      if (document.body.classList.contains('dark')) {
        toggleBtn.textContent = 'Toggle Light Mode';
      } else {
        toggleBtn.textContent = 'Toggle Dark Mode';
      }
    });
  </script>
</body>
</html>
```

### Example 2: Tab Navigation

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .tabs {
      display: flex;
      gap: 10px;
      border-bottom: 2px solid #ddd;
    }

    .tab {
      padding: 10px 20px;
      cursor: pointer;
      border: none;
      background: none;
      font-size: 16px;
    }

    .tab.active {
      background: #3498db;
      color: white;
      border-radius: 4px 4px 0 0;
    }

    .tab-content {
      display: none;
      padding: 20px;
    }

    .tab-content.active {
      display: block;
    }
  </style>
</head>
<body>
  <div class="tabs">
    <button class="tab active" data-tab="home">Home</button>
    <button class="tab" data-tab="profile">Profile</button>
    <button class="tab" data-tab="settings">Settings</button>
  </div>

  <div class="tab-content active" id="home">
    <h2>Home</h2>
    <p>Welcome to the home tab!</p>
  </div>

  <div class="tab-content" id="profile">
    <h2>Profile</h2>
    <p>Your profile information.</p>
  </div>

  <div class="tab-content" id="settings">
    <h2>Settings</h2>
    <p>Adjust your settings here.</p>
  </div>

  <script>
    const tabs = document.querySelectorAll('.tab');
    const contents = document.querySelectorAll('.tab-content');

    tabs.forEach(tab => {
      tab.addEventListener('click', () => {
        // Remove active from all tabs
        tabs.forEach(t => t.classList.remove('active'));

        // Remove active from all contents
        contents.forEach(c => c.classList.remove('active'));

        // Add active to clicked tab
        tab.classList.add('active');

        // Show corresponding content
        const tabId = tab.dataset.tab;
        document.querySelector(`#${tabId}`).classList.add('active');
      });
    });
  </script>
</body>
</html>
```

### Example 3: Dropdown Menu

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .dropdown {
      position: relative;
      display: inline-block;
    }

    .dropdown-button {
      padding: 10px 20px;
      background: #3498db;
      color: white;
      border: none;
      cursor: pointer;
      border-radius: 4px;
    }

    .dropdown-content {
      display: none;
      position: absolute;
      background: white;
      min-width: 200px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.2);
      border-radius: 4px;
      margin-top: 5px;
      z-index: 1;
    }

    .dropdown-content.show {
      display: block;
    }

    .dropdown-content a {
      display: block;
      padding: 12px 16px;
      text-decoration: none;
      color: #333;
    }

    .dropdown-content a:hover {
      background: #f0f0f0;
    }
  </style>
</head>
<body>
  <div class="dropdown">
    <button class="dropdown-button" id="dropdownBtn">Menu ▼</button>
    <div class="dropdown-content" id="dropdownContent">
      <a href="#">Option 1</a>
      <a href="#">Option 2</a>
      <a href="#">Option 3</a>
    </div>
  </div>

  <script>
    const btn = document.querySelector('#dropdownBtn');
    const content = document.querySelector('#dropdownContent');

    btn.addEventListener('click', (e) => {
      e.stopPropagation();
      content.classList.toggle('show');
    });

    // Close dropdown when clicking outside
    document.addEventListener('click', () => {
      content.classList.remove('show');
    });
  </script>
</body>
</html>
```

### Example 4: Progress Bar

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .progress-container {
      width: 100%;
      background: #f0f0f0;
      border-radius: 10px;
      overflow: hidden;
    }

    .progress-bar {
      height: 30px;
      background: linear-gradient(90deg, #3498db, #2ecc71);
      width: 0%;
      transition: width 0.3s ease;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="progress-container">
    <div class="progress-bar" id="progress">0%</div>
  </div>

  <button onclick="increaseProgress()">+10%</button>
  <button onclick="decreaseProgress()">-10%</button>
  <button onclick="resetProgress()">Reset</button>

  <script>
    let currentProgress = 0;
    const progressBar = document.querySelector('#progress');

    function updateProgress(value) {
      currentProgress = Math.max(0, Math.min(100, value));
      progressBar.style.width = currentProgress + '%';
      progressBar.textContent = currentProgress + '%';
    }

    function increaseProgress() {
      updateProgress(currentProgress + 10);
    }

    function decreaseProgress() {
      updateProgress(currentProgress - 10);
    }

    function resetProgress() {
      updateProgress(0);
    }
  </script>
</body>
</html>
```

### Example 5: Modal Dialog

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.5);
      z-index: 1000;
      justify-content: center;
      align-items: center;
    }

    .modal.show {
      display: flex;
    }

    .modal-content {
      background: white;
      padding: 30px;
      border-radius: 8px;
      max-width: 500px;
      width: 90%;
      position: relative;
    }

    .close-btn {
      position: absolute;
      top: 10px;
      right: 10px;
      background: none;
      border: none;
      font-size: 24px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <button onclick="openModal()">Open Modal</button>

  <div class="modal" id="modal">
    <div class="modal-content">
      <button class="close-btn" onclick="closeModal()">×</button>
      <h2>Modal Title</h2>
      <p>This is a modal dialog. Click outside or press Escape to close.</p>
    </div>
  </div>

  <script>
    const modal = document.querySelector('#modal');

    function openModal() {
      modal.classList.add('show');
    }

    function closeModal() {
      modal.classList.remove('show');
    }

    // Close on background click
    modal.addEventListener('click', (e) => {
      if (e.target === modal) {
        closeModal();
      }
    });

    // Close on Escape key
    document.addEventListener('keydown', (e) => {
      if (e.key === 'Escape' && modal.classList.contains('show')) {
        closeModal();
      }
    });
  </script>
</body>
</html>
```

### Example 6: Tooltip

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .tooltip-trigger {
      position: relative;
      display: inline-block;
      padding: 10px;
      background: #3498db;
      color: white;
      cursor: pointer;
      border-radius: 4px;
    }

    .tooltip {
      display: none;
      position: absolute;
      bottom: 100%;
      left: 50%;
      transform: translateX(-50%);
      margin-bottom: 10px;
      padding: 8px 12px;
      background: #333;
      color: white;
      border-radius: 4px;
      white-space: nowrap;
      font-size: 14px;
    }

    .tooltip.show {
      display: block;
    }

    .tooltip::after {
      content: '';
      position: absolute;
      top: 100%;
      left: 50%;
      transform: translateX(-50%);
      border: 5px solid transparent;
      border-top-color: #333;
    }
  </style>
</head>
<body>
  <div class="tooltip-trigger" id="trigger">
    Hover me
    <div class="tooltip" id="tooltip">This is a tooltip!</div>
  </div>

  <script>
    const trigger = document.querySelector('#trigger');
    const tooltip = document.querySelector('#tooltip');

    trigger.addEventListener('mouseenter', () => {
      tooltip.classList.add('show');
    });

    trigger.addEventListener('mouseleave', () => {
      tooltip.classList.remove('show');
    });
  </script>
</body>
</html>
```

---

## ⚠️ Common Mistakes

### Mistake 1: Forgetting className vs classList

```javascript
// ❌ WRONG - Overwrites all classes!
element.className = 'new-class';
// Previous classes are lost!

// ✅ CORRECT - Adds to existing classes
element.classList.add('new-class');
```

### Mistake 2: Missing Units in Inline Styles

```javascript
// ❌ WRONG
element.style.width = 100; // No effect!
element.style.fontSize = 20; // No effect!

// ✅ CORRECT
element.style.width = '100px';
element.style.fontSize = '20px';
```

### Mistake 3: Wrong Property Names

```javascript
// ❌ WRONG - CSS syntax
element.style['background-color'] = 'red'; // Works but not recommended

// ✅ CORRECT - camelCase
element.style.backgroundColor = 'red';
```

### Mistake 4: Trying to Read Stylesheet Styles with element.style

```javascript
// ❌ WRONG - Returns empty string
const width = element.style.width;

// ✅ CORRECT - Use getComputedStyle
const width = getComputedStyle(element).width;
```

### Mistake 5: classList on Elements Without className

```javascript
// ❌ Some elements don't have classList (SVG in old browsers)
svgElement.classList.add('class'); // Might error

// ✅ Check first or use className
if (svgElement.classList) {
  svgElement.classList.add('class');
} else {
  svgElement.className += ' class';
}
```

---

## 🎯 Practice Exercises

### Exercise 1: Accordion Component

Create an accordion where clicking a header toggles the content visibility.

<details>
<summary>Solution</summary>

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .accordion-item {
      border: 1px solid #ddd;
      margin-bottom: 5px;
    }

    .accordion-header {
      padding: 15px;
      background: #f0f0f0;
      cursor: pointer;
      user-select: none;
    }

    .accordion-header:hover {
      background: #e0e0e0;
    }

    .accordion-content {
      max-height: 0;
      overflow: hidden;
      transition: max-height 0.3s ease;
    }

    .accordion-content.open {
      max-height: 500px;
      padding: 15px;
    }
  </style>
</head>
<body>
  <div class="accordion">
    <div class="accordion-item">
      <div class="accordion-header">Section 1</div>
      <div class="accordion-content">Content for section 1...</div>
    </div>
    <div class="accordion-item">
      <div class="accordion-header">Section 2</div>
      <div class="accordion-content">Content for section 2...</div>
    </div>
    <div class="accordion-item">
      <div class="accordion-header">Section 3</div>
      <div class="accordion-content">Content for section 3...</div>
    </div>
  </div>

  <script>
    const headers = document.querySelectorAll('.accordion-header');

    headers.forEach(header => {
      header.addEventListener('click', () => {
        const content = header.nextElementSibling;
        content.classList.toggle('open');
      });
    });
  </script>
</body>
</html>
```
</details>

### Exercise 2: Image Gallery with Lightbox

Create a gallery where clicking an image opens it in a modal/lightbox.

<details>
<summary>Solution</summary>

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .gallery {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
      gap: 10px;
    }

    .gallery img {
      width: 100%;
      height: 200px;
      object-fit: cover;
      cursor: pointer;
      border-radius: 4px;
    }

    .lightbox {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.9);
      z-index: 1000;
      justify-content: center;
      align-items: center;
    }

    .lightbox.show {
      display: flex;
    }

    .lightbox img {
      max-width: 90%;
      max-height: 90%;
    }

    .close-lightbox {
      position: absolute;
      top: 20px;
      right: 20px;
      color: white;
      font-size: 30px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div class="gallery">
    <img src="https://via.placeholder.com/300/FF0000" alt="">
    <img src="https://via.placeholder.com/300/00FF00" alt="">
    <img src="https://via.placeholder.com/300/0000FF" alt="">
    <img src="https://via.placeholder.com/300/FFFF00" alt="">
  </div>

  <div class="lightbox" id="lightbox">
    <span class="close-lightbox">&times;</span>
    <img id="lightboxImg" src="" alt="">
  </div>

  <script>
    const galleryImages = document.querySelectorAll('.gallery img');
    const lightbox = document.querySelector('#lightbox');
    const lightboxImg = document.querySelector('#lightboxImg');
    const closeBtn = document.querySelector('.close-lightbox');

    galleryImages.forEach(img => {
      img.addEventListener('click', () => {
        lightboxImg.src = img.src;
        lightbox.classList.add('show');
      });
    });

    closeBtn.addEventListener('click', () => {
      lightbox.classList.remove('show');
    });

    lightbox.addEventListener('click', (e) => {
      if (e.target === lightbox) {
        lightbox.classList.remove('show');
      }
    });
  </script>
</body>
</html>
```
</details>

### Exercise 3: Theme Switcher (3 Themes)

Create a theme switcher with Light, Dark, and Blue themes.

<details>
<summary>Solution</summary>

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      transition: all 0.3s;
      padding: 40px;
      font-family: Arial, sans-serif;
    }

    /* Light theme (default) */
    body {
      background: white;
      color: #333;
    }

    /* Dark theme */
    body.theme-dark {
      background: #1a1a1a;
      color: #f0f0f0;
    }

    /* Blue theme */
    body.theme-blue {
      background: #1e3a5f;
      color: #e3f2fd;
    }

    .theme-switcher {
      display: flex;
      gap: 10px;
      margin-bottom: 30px;
    }

    button {
      padding: 10px 20px;
      border: 2px solid currentColor;
      background: transparent;
      color: inherit;
      cursor: pointer;
      border-radius: 4px;
    }

    button.active {
      background: currentColor;
      color: white;
    }
  </style>
</head>
<body>
  <div class="theme-switcher">
    <button class="active" data-theme="light">Light</button>
    <button data-theme="dark">Dark</button>
    <button data-theme="blue">Blue</button>
  </div>

  <h1>Theme Switcher Demo</h1>
  <p>Click the buttons above to switch themes.</p>

  <script>
    const buttons = document.querySelectorAll('[data-theme]');

    buttons.forEach(button => {
      button.addEventListener('click', () => {
        const theme = button.dataset.theme;

        // Remove all theme classes
        document.body.classList.remove('theme-dark', 'theme-blue');

        // Add new theme class (if not light)
        if (theme !== 'light') {
          document.body.classList.add(`theme-${theme}`);
        }

        // Update active button
        buttons.forEach(btn => btn.classList.remove('active'));
        button.classList.add('active');
      });
    });
  </script>
</body>
</html>
```
</details>

---

## 🎯 Key Takeaways

✅ **classList.add/remove/toggle** - Manage classes dynamically
✅ **classList.contains** - Check if element has a class
✅ **Prefer classes over inline styles** (reusable, maintainable)
✅ **Use inline styles for dynamic values** (positions, dimensions)
✅ **element.style** only reads inline styles
✅ **getComputedStyle** reads actual computed styles
✅ **toggle()** is perfect for show/hide patterns
✅ **CSS property names use camelCase** in JavaScript
✅ **Always include units** in inline style values

---

## 🔗 What's Next?

**You've completed DOM Manipulation!** 🎉

You now know how to:
- Select elements
- Change their content
- Listen for events
- Create and remove elements
- Change their appearance

**Next step:** Apply these skills in **React**, where you'll learn how React abstracts DOM manipulation into a simpler component model.

**Ready for:** [05 - React Basics](../../05-react-basics/)

---

**You can now build fully interactive web applications from scratch! 🚀**
