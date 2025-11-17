# Lesson 1: JSX - JavaScript XML

> **"JSX looks like HTML, but it's actually JavaScript. That's the magic of React."**

---

## 🎯 What is JSX?

**JSX = JavaScript XML** (HTML-like syntax in JavaScript)

**Regular JavaScript:**
```javascript
const heading = React.createElement('h1', null, 'Hello, World!');
```

**JSX (much easier!):**
```javascript
const heading = <h1>Hello, World!</h1>;
```

**Same result, way cleaner!**

---

## 🎨 JSX vs HTML - Key Differences

### 1. **className instead of class**

```javascript
// HTML
<div class="container"></div>

// JSX
<div className="container"></div>
```

**Why?** `class` is a reserved word in JavaScript.

---

### 2. **Self-closing tags must have /**

```javascript
// HTML (works)
<img src="photo.jpg">
<br>
<input type="text">

// JSX (must close)
<img src="photo.jpg" />
<br />
<input type="text" />
```

---

### 3. **camelCase for attributes**

```javascript
// HTML
<button onclick="handleClick()">Click</button>
<label for="name">Name</label>

// JSX
<button onClick={handleClick}>Click</button>
<label htmlFor="name">Name</label>
```

**Common JSX attributes:**
- `onClick` (not onclick)
- `onChange` (not onchange)
- `className` (not class)
- `htmlFor` (not for)

---

## 🎯 Embedding JavaScript in JSX

**Use curly braces `{}` to embed JavaScript:**

```javascript
const name = "Alice";
const age = 25;

const element = (
  <div>
    <h1>Hello, {name}!</h1>
    <p>You are {age} years old.</p>
    <p>Next year you'll be {age + 1}!</p>
  </div>
);
```

**You can put ANY JavaScript expression inside `{}`:**

```javascript
const element = (
  <div>
    <p>{2 + 2}</p>                    {/* 4 */}
    <p>{name.toUpperCase()}</p>       {/* ALICE */}
    <p>{age >= 18 ? "Adult" : "Minor"}</p>  {/* Adult */}
    <p>{[1, 2, 3].map(n => n * 2)}</p>  {/* 2,4,6 */}
  </div>
);
```

---

## 🎯 JSX Must Have ONE Parent Element

```javascript
// ❌ WRONG - Multiple parent elements
return (
  <h1>Title</h1>
  <p>Paragraph</p>
);

// ✅ RIGHT - Wrapped in div
return (
  <div>
    <h1>Title</h1>
    <p>Paragraph</p>
  </div>
);

// ✅ ALSO RIGHT - React Fragment (no extra div)
return (
  <>
    <h1>Title</h1>
    <p>Paragraph</p>
  </>
);
```

**Use `<>...</>` (Fragment) when you don't want extra div in DOM.**

---

## 🎨 Conditional Rendering in JSX

### Method 1: Ternary Operator

```javascript
const isLoggedIn = true;

return (
  <div>
    {isLoggedIn ? <p>Welcome back!</p> : <p>Please log in</p>}
  </div>
);
```

### Method 2: && Operator (for simple cases)

```javascript
const hasMessages = true;

return (
  <div>
    {hasMessages && <p>You have new messages!</p>}
  </div>
);
```

**If `hasMessages` is false, nothing renders.**

### Method 3: Variable

```javascript
const isLoggedIn = true;
let content;

if (isLoggedIn) {
  content = <p>Welcome back!</p>;
} else {
  content = <p>Please log in</p>;
}

return <div>{content}</div>;
```

---

## 🎨 Rendering Lists

**Use `.map()` to render arrays:**

```javascript
const fruits = ["Apple", "Banana", "Orange"];

return (
  <ul>
    {fruits.map((fruit, index) => (
      <li key={index}>{fruit}</li>
    ))}
  </ul>
);
```

**Always include `key` prop!** (helps React track items)

**Better key (use unique ID if available):**

```javascript
const users = [
  { id: 1, name: "Alice" },
  { id: 2, name: "Bob" },
  { id: 3, name: "Charlie" }
];

return (
  <ul>
    {users.map(user => (
      <li key={user.id}>{user.name}</li>
    ))}
  </ul>
);
```

---

## 🎨 Inline Styles in JSX

```javascript
const divStyle = {
  color: 'blue',
  backgroundColor: 'lightgray',  // camelCase!
  padding: '20px'
};

return <div style={divStyle}>Styled content</div>;

// Or inline:
return (
  <div style={{ color: 'blue', padding: '20px' }}>
    Styled content
  </div>
);
```

**Note:** Double curly braces `{{}}` - outer for JSX, inner for object.

---

## 🎨 Complete Working Example

```javascript
// App.jsx
import React from 'react';

function App() {
  const user = {
    name: "Alice",
    age: 25,
    isLoggedIn: true
  };

  const hobbies = ["Reading", "Coding", "Gaming"];

  const todos = [
    { id: 1, text: "Learn React", completed: true },
    { id: 2, text: "Build project", completed: false },
    { id: 3, text: "Deploy app", completed: false }
  ];

  return (
    <div className="container">
      {/* Conditional rendering */}
      {user.isLoggedIn ? (
        <h1>Welcome back, {user.name}!</h1>
      ) : (
        <h1>Please log in</h1>
      )}

      {/* Expressions in JSX */}
      <p>Age: {user.age}</p>
      <p>Status: {user.age >= 18 ? "Adult" : "Minor"}</p>

      {/* Rendering list */}
      <h2>Hobbies</h2>
      <ul>
        {hobbies.map((hobby, index) => (
          <li key={index}>{hobby}</li>
        ))}
      </ul>

      {/* Rendering objects array */}
      <h2>Todo List</h2>
      <ul>
        {todos.map(todo => (
          <li
            key={todo.id}
            style={{
              textDecoration: todo.completed ? 'line-through' : 'none'
            }}
          >
            {todo.text}
          </li>
        ))}
      </ul>

      {/* Conditional with && */}
      {todos.filter(t => !t.completed).length > 0 && (
        <p>You have {todos.filter(t => !t.completed).length} tasks remaining!</p>
      )}
    </div>
  );
}

export default App;
```

---

## ✏️ Practice Exercise

Create a component that:
1. Displays your name and age using variables
2. Shows "Adult" or "Minor" based on age
3. Renders a list of 3 favorite foods
4. Shows a message only if age is over 21
5. Styles a div with inline styles

<details>
<summary>Solution</summary>

```javascript
function MyProfile() {
  const name = "John";
  const age = 25;
  const favoriteFoods = ["Pizza", "Sushi", "Tacos"];

  return (
    <div style={{ padding: '20px', backgroundColor: '#f0f0f0' }}>
      <h1>My Profile</h1>

      {/* 1 & 2 */}
      <p>Name: {name}</p>
      <p>Age: {age}</p>
      <p>Status: {age >= 18 ? "Adult" : "Minor"}</p>

      {/* 3 */}
      <h2>Favorite Foods</h2>
      <ul>
        {favoriteFoods.map((food, index) => (
          <li key={index}>{food}</li>
        ))}
      </ul>

      {/* 4 */}
      {age > 21 && <p>🎉 You can drink (in the US)!</p>}

      {/* 5 - Already done with outer div */}
    </div>
  );
}

export default MyProfile;
```

</details>

---

## 🎯 JSX Rules Summary

1. **Use `className` not `class`**
2. **Close all tags** (`<img />`, `<br />`)
3. **camelCase** for event handlers (`onClick`, `onChange`)
4. **One parent element** (or use Fragment `<>`)
5. **Curly braces `{}`** for JavaScript expressions
6. **`key` prop** when mapping arrays
7. **Inline styles** use objects with camelCase properties

---

## 🎯 Key Takeaways

1. **JSX** = HTML-like syntax in JavaScript
2. **`{}`** embeds JavaScript expressions
3. **`className`** instead of `class`
4. **Must return one parent** element (or Fragment)
5. **`.map()`** for lists (don't forget `key`)
6. **Conditional rendering:** ternary `? :` or `&&`
7. **Looks like HTML, acts like JavaScript**

---

## 🚀 Next Lesson

Now you understand JSX. Next, learn **Components** - the building blocks of React!

**Next:** [Lesson 2: Components →](./02-components.md)

---

**JSX is the language of React. Master it, and React becomes easy.** ⚛️
