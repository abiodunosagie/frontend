# DOM Manipulation 05 - Classes and Styles

> **"The final piece: changing how elements look with JavaScript."**

---

## 🎯 What You'll Learn

- How to add/remove/toggle CSS classes
- How to change inline styles
- When to use classes vs inline styles
- Real-world examples

---

## 🎨 Working with Classes

### classList.add() - Add a Class

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

### classList.remove() - Remove a Class

```javascript
element.classList.remove('className');
```

### classList.toggle() - Add if Missing, Remove if Present

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

### classList.contains() - Check if Has Class

```javascript
if (element.classList.contains('active')) {
  console.log('Element is active');
}
```

---

## 🎨 Working with Inline Styles

### element.style.property = value

```javascript
element.style.color = 'red';
element.style.backgroundColor = 'blue';
element.style.fontSize = '20px';
```

### Example: Hover Effect

```html
<div id="card">Hover me</div>

<script>
  const card = document.querySelector('#card');
  
  card.addEventListener('mouseenter', () => {
    card.style.backgroundColor = 'lightblue';
    card.style.transform = 'scale(1.1)';
  });
  
  card.addEventListener('mouseleave', () => {
    card.style.backgroundColor = '';
    card.style.transform = '';
  });
</script>
```

---

## ✅ Classes vs Inline Styles

**Use Classes (Preferred):**
- Reusable styles
- Easier to maintain
- Better performance
- Can be styled in CSS

**Use Inline Styles:**
- Dynamic values (coordinates, dimensions)
- Temporary changes
- Values calculated in JavaScript

---

## 🎯 Real Example: Dark Mode Toggle

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      background: white;
      color: black;
      transition: all 0.3s;
    }
    body.dark {
      background: #222;
      color: white;
    }
  </style>
</head>
<body>
  <button id="toggle">Toggle Dark Mode</button>
  
  <script>
    const toggle = document.querySelector('#toggle');
    
    toggle.addEventListener('click', () => {
      document.body.classList.toggle('dark');
    });
  </script>
</body>
</html>
```

---

## 🎯 Key Takeaways

✅ **classList.add/remove/toggle** - Manage classes
✅ **Prefer classes** over inline styles
✅ **Use inline styles** for dynamic values
✅ **toggle()** is perfect for show/hide patterns

---

**You've completed DOM Manipulation! Ready for React? 🚀**
