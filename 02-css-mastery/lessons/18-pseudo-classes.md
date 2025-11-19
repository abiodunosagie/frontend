# CSS Lesson 18 - Pseudo-classes & Pseudo-elements

> **"Special selectors for specific states and content."**

---

## 🎯 Pseudo-classes (Element States)

### :hover
```css
a:hover {
  color: blue;
}

button:hover {
  background: darkblue;
}
```

### :focus (Form Inputs)
```css
input:focus {
  border-color: blue;
  outline: 2px solid blue;
}
```

### :active (While Clicking)
```css
button:active {
  transform: scale(0.98);
}
```

### :first-child, :last-child
```css
li:first-child {
  font-weight: bold;
}

li:last-child {
  border-bottom: none;
}
```

### :nth-child()
```css
/* Odd rows */
tr:nth-child(odd) {
  background: #f9f9f9;
}

/* Even rows */
tr:nth-child(even) {
  background: white;
}

/* Every 3rd element */
div:nth-child(3n) {
  background: lightblue;
}

/* Specific element */
li:nth-child(2) {
  color: red; /* 2nd li */
}
```

### :not()
```css
/* All buttons except .cancel */
button:not(.cancel) {
  background: blue;
}

/* All list items except first */
li:not(:first-child) {
  border-top: 1px solid #ddd;
}
```

### :disabled, :enabled
```css
input:disabled {
  background: #f0f0f0;
  cursor: not-allowed;
}
```

### :checked (Checkboxes/Radio)
```css
input[type="checkbox"]:checked {
  background: blue;
}
```

---

## 🎯 Pseudo-elements (Style Parts of Content)

### ::before and ::after
```css
.quote::before {
  content: '"';
  font-size: 2rem;
  color: gray;
}

.quote::after {
  content: '"';
  font-size: 2rem;
  color: gray;
}
```

### Icon Before Links
```css
a[href^="http"]::before {
  content: "🔗 ";
}

a[href$=".pdf"]::after {
  content: " (PDF)";
  font-size: 0.8em;
  color: gray;
}
```

### Custom Checkboxes
```css
.checkbox {
  position: relative;
  padding-left: 30px;
  cursor: pointer;
}

.checkbox::before {
  content: "";
  position: absolute;
  left: 0;
  width: 20px;
  height: 20px;
  border: 2px solid #ddd;
  border-radius: 3px;
}

.checkbox input:checked + ::before {
  background: blue;
}
```

### ::first-letter, ::first-line
```css
p::first-letter {
  font-size: 3rem;
  font-weight: bold;
  float: left;
  margin-right: 5px;
}

p::first-line {
  font-weight: bold;
  color: blue;
}
```

### ::placeholder
```css
input::placeholder {
  color: #999;
  font-style: italic;
}
```

### ::selection (Text Selection)
```css
::selection {
  background: yellow;
  color: black;
}
```

---

## 🎯 Complete Example: Styled List

```html
<style>
  ul {
    list-style: none;
    padding: 0;
  }

  li {
    padding: 10px;
    border-bottom: 1px solid #ddd;
  }

  li:first-child {
    border-top: 1px solid #ddd;
  }

  li:hover {
    background: #f0f0f0;
  }

  li::before {
    content: "✓ ";
    color: green;
    font-weight: bold;
    margin-right: 8px;
  }

  li:nth-child(even) {
    background: #f9f9f9;
  }
</style>

<ul>
  <li>First item</li>
  <li>Second item</li>
  <li>Third item</li>
</ul>
```

---

## 🎯 Key Takeaways

✅ **Pseudo-classes** target element states (:hover, :focus, :nth-child)
✅ **Pseudo-elements** create/style parts of elements (::before, ::after)
✅ ::before and ::after require `content` property
✅ Use :nth-child() for zebra striping
✅ ::selection for custom text highlight

---

**Next:** [19 - CSS Variables](./19-css-variables.md)
