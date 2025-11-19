# CSS Lesson 08 - Backgrounds & Borders

> **"Small visual touches that make big differences."**

---

## 🎯 Background Properties

### Background Color
```css
div {
  background-color: #3498db;
  background-color: rgba(52, 152, 219, 0.5); /* With transparency */
}
```

### Background Image
```css
div {
  background-image: url('image.jpg');
  background-size: cover;      /* Fill entire area */
  background-position: center;
  background-repeat: no-repeat;
}
```

### Background Shorthand
```css
div {
  background: url('image.jpg') center/cover no-repeat;
}
```

### Linear Gradient
```css
div {
  background: linear-gradient(to right, #667eea, #764ba2);
}

/* Diagonal */
div {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}
```

---

## 🎯 Borders

### Border Syntax
```css
div {
  border: 2px solid #333;
  /* width style color */
}
```

### Individual Sides
```css
div {
  border-top: 1px solid #ddd;
  border-right: 2px dashed red;
  border-bottom: 3px dotted blue;
  border-left: 4px double green;
}
```

### Border Radius (Rounded Corners)
```css
div {
  border-radius: 8px; /* All corners */
}

.circle {
  width: 100px;
  height: 100px;
  border-radius: 50%; /* Perfect circle */
}

.fancy {
  border-radius: 20px 10px 20px 10px; /* Each corner */
}
```

---

## 🎯 Box Shadow

```css
div {
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  /* x-offset y-offset blur color */
}

/* Multiple shadows */
div {
  box-shadow: 
    0 2px 4px rgba(0,0,0,0.1),
    0 4px 8px rgba(0,0,0,0.05);
}
```

---

## 🎯 Complete Card Example

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .card {
      background: white;
      border: 1px solid #e0e0e0;
      border-radius: 8px;
      padding: 20px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
      max-width: 300px;
      margin: 20px;
    }

    .card:hover {
      box-shadow: 0 4px 16px rgba(0,0,0,0.15);
      transform: translateY(-2px);
      transition: all 0.3s;
    }

    .card-header {
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      color: white;
      padding: 20px;
      border-radius: 8px 8px 0 0;
      margin: -20px -20px 20px -20px;
    }
  </style>
</head>
<body>
  <div class="card">
    <div class="card-header">
      <h2>Card Title</h2>
    </div>
    <p>Card content goes here...</p>
  </div>
</body>
</html>
```

---

## 🎯 Key Takeaways

✅ `background: url() center/cover no-repeat`
✅ `border-radius: 50%` for circles
✅ `box-shadow` for depth
✅ Gradients for modern look

---

**Next:** [09 - Display & Positioning](./09-display-positioning.md)
