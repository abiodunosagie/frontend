# CSS Lesson 17 - Transitions & Animations

> **"Bring your designs to life with smooth, professional motion."**

---

## 🎯 Transitions (Simple Animations)

### Basic Syntax
```css
element {
  transition: property duration timing-function delay;
}
```

### Example: Button Hover
```css
.btn {
  background: #3498db;
  color: white;
  padding: 12px 24px;
  transition: all 0.3s ease;
}

.btn:hover {
  background: #2980b9;
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(0,0,0,0.2);
}
```

### Transition Properties
```css
/* Specific property */
transition: background-color 0.3s ease;

/* Multiple properties */
transition: background 0.3s, transform 0.2s, box-shadow 0.3s;

/* All properties (use sparingly) */
transition: all 0.3s ease;
```

### Timing Functions
```css
transition: all 0.3s linear;      /* Constant speed */
transition: all 0.3s ease;        /* Slow start/end */
transition: all 0.3s ease-in;     /* Slow start */
transition: all 0.3s ease-out;    /* Slow end */
transition: all 0.3s ease-in-out; /* Slow start/end (smoother) */
```

---

## 🎯 Transforms

### Translate (Move)
```css
.card:hover {
  transform: translateY(-10px); /* Move up */
}
```

### Scale (Resize)
```css
.img:hover {
  transform: scale(1.1); /* 110% size */
}
```

### Rotate
```css
.icon:hover {
  transform: rotate(45deg);
}
```

### Combine Multiple
```css
.card:hover {
  transform: translateY(-5px) scale(1.05) rotate(2deg);
}
```

---

## 🎯 Keyframe Animations

### Basic Syntax
```css
@keyframes animationName {
  from { /* starting state */ }
  to { /* ending state */ }
}

/* OR */

@keyframes animationName {
  0% { /* start */ }
  50% { /* middle */ }
  100% { /* end */ }
}
```

### Apply Animation
```css
element {
  animation: animationName duration timing-function delay iteration-count direction;
}
```

### Example: Fade In
```css
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.card {
  animation: fadeIn 0.5s ease;
}
```

### Example: Pulse
```css
@keyframes pulse {
  0%, 100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.05);
  }
}

.notification {
  animation: pulse 2s infinite;
}
```

### Example: Loading Spinner
```css
@keyframes spin {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

.spinner {
  width: 40px;
  height: 40px;
  border: 4px solid #f3f3f3;
  border-top: 4px solid #3498db;
  border-radius: 50%;
  animation: spin 1s linear infinite;
}
```

---

## 🎯 Complete Examples

### Smooth Card Hover
```css
.card {
  background: white;
  padding: 2rem;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  transition: all 0.3s ease;
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(0,0,0,0.15);
}
```

### Animated Modal
```css
@keyframes modalSlideIn {
  from {
    opacity: 0;
    transform: translateY(-50px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.modal {
  animation: modalSlideIn 0.3s ease;
}
```

---

## 🎯 Key Takeaways

✅ **Transitions** for simple hover effects
✅ **Animations** for complex, multi-step effects
✅ Use `ease` or `ease-in-out` for natural motion
✅ Keep durations short (0.2s - 0.5s) for UI
✅ Use `transform` instead of `top/left` (better performance)

---

**Next:** [18 - Pseudo-classes & Pseudo-elements](./18-pseudo-classes.md)
