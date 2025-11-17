# Lesson 4: useState Hook

> **"useState makes components interactive. Click a button → update the UI. That's React's magic."**

---

## 🎯 What is State?

**State = Data that changes over time**

Examples:
- Counter value (starts at 0, increases when clicked)
- Form input text (changes as user types)
- Is menu open or closed?
- Shopping cart items

**When state changes, React re-renders the component automatically!**

---

## 📝 useState Basics

```javascript
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  //     ↑      ↑            ↑
  //   value  setter    initial value

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>
    </div>
  );
}
```

**Click button → `count` updates → component re-renders → UI updates!**

---

## 🎯 useState Syntax Explained

```javascript
const [value, setValue] = useState(initialValue);
```

1. **Import:** `import { useState } from 'react'`
2. **Destructuring:** Gets two things back - current value and setter function
3. **Naming convention:** `value` and `setValue` (or `count`/`setCount`, `name`/`setName`)
4. **Initial value:** What the state starts as

---

## 🎨 Multiple State Variables

```javascript
function UserForm() {
  const [name, setName] = useState("");
  const [age, setAge] = useState(0);
  const [email, setEmail] = useState("");

  return (
    <div>
      <input
        value={name}
        onChange={(e) => setName(e.target.value)}
        placeholder="Name"
      />

      <input
        type="number"
        value={age}
        onChange={(e) => setAge(e.target.value)}
        placeholder="Age"
      />

      <input
        value={email}
        onChange={(e) => setEmail(e.target.value)}
        placeholder="Email"
      />

      <p>Name: {name}</p>
      <p>Age: {age}</p>
      <p>Email: {email}</p>
    </div>
  );
}
```

---

## 🎯 Updating State

### ❌ WRONG - Don't Mutate State Directly

```javascript
const [count, setCount] = useState(0);

// ❌ WRONG
count = count + 1;  // Doesn't work!
count++;  // Doesn't work!

// ✅ RIGHT
setCount(count + 1);
```

### Previous State Pattern

```javascript
// When new state depends on old state
setCount(prevCount => prevCount + 1);
```

**This is safer for rapid updates!**

---

## 🎯 Different State Types

### Number

```javascript
const [score, setScore] = useState(0);

<button onClick={() => setScore(score + 10)}>
  Add 10 Points
</button>
```

### String

```javascript
const [message, setMessage] = useState("Hello");

<input
  value={message}
  onChange={(e) => setMessage(e.target.value)}
/>
```

### Boolean

```javascript
const [isVisible, setIsVisible] = useState(false);

<button onClick={() => setIsVisible(!isVisible)}>
  Toggle
</button>

{isVisible && <p>I'm visible!</p>}
```

### Array

```javascript
const [items, setItems] = useState([]);

// Add item
const addItem = (newItem) => {
  setItems([...items, newItem]);
};

// Remove item
const removeItem = (index) => {
  setItems(items.filter((_, i) => i !== index));
};
```

### Object

```javascript
const [user, setUser] = useState({
  name: "",
  age: 0,
  email: ""
});

// Update one property
setUser({
  ...user,
  name: "Alice"
});
```

---

## 🎨 Real-World Examples

### Example 1: Counter

```javascript
function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div style={{ textAlign: 'center', padding: '20px' }}>
      <h1>Count: {count}</h1>
      <button onClick={() => setCount(count + 1)}>+1</button>
      <button onClick={() => setCount(count - 1)}>-1</button>
      <button onClick={() => setCount(0)}>Reset</button>
    </div>
  );
}
```

### Example 2: Toggle

```javascript
function Toggle() {
  const [isOn, setIsOn] = useState(false);

  return (
    <div>
      <button onClick={() => setIsOn(!isOn)}>
        {isOn ? "ON" : "OFF"}
      </button>

      {isOn && <p>The toggle is ON!</p>}
    </div>
  );
}
```

### Example 3: Todo List

```javascript
function TodoList() {
  const [todos, setTodos] = useState([]);
  const [input, setInput] = useState("");

  const addTodo = () => {
    if (input.trim()) {
      setTodos([...todos, { id: Date.now(), text: input }]);
      setInput("");
    }
  };

  const removeTodo = (id) => {
    setTodos(todos.filter(todo => todo.id !== id));
  };

  return (
    <div style={{ maxWidth: '500px', margin: '0 auto', padding: '20px' }}>
      <h1>Todo List</h1>

      <div style={{ display: 'flex', gap: '10px', marginBottom: '20px' }}>
        <input
          value={input}
          onChange={(e) => setInput(e.target.value)}
          placeholder="Add todo..."
          style={{ flex: 1, padding: '10px' }}
        />
        <button onClick={addTodo} style={{ padding: '10px 20px' }}>
          Add
        </button>
      </div>

      <ul style={{ listStyle: 'none', padding: 0 }}>
        {todos.map(todo => (
          <li
            key={todo.id}
            style={{
              display: 'flex',
              justifyContent: 'space-between',
              padding: '10px',
              marginBottom: '5px',
              backgroundColor: '#f0f0f0',
              borderRadius: '4px'
            }}
          >
            <span>{todo.text}</span>
            <button onClick={() => removeTodo(todo.id)}>Delete</button>
          </li>
        ))}
      </ul>
    </div>
  );
}
```

### Example 4: Form

```javascript
function ContactForm() {
  const [formData, setFormData] = useState({
    name: "",
    email: "",
    message: ""
  });

  const [submitted, setSubmitted] = useState(false);

  const handleChange = (e) => {
    setFormData({
      ...formData,
      [e.target.name]: e.target.value
    });
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log("Form submitted:", formData);
    setSubmitted(true);
  };

  if (submitted) {
    return <h2>Thank you for your message!</h2>;
  }

  return (
    <form onSubmit={handleSubmit} style={{ maxWidth: '500px', margin: '0 auto' }}>
      <div style={{ marginBottom: '15px' }}>
        <input
          name="name"
          value={formData.name}
          onChange={handleChange}
          placeholder="Your name"
          style={{ width: '100%', padding: '10px' }}
        />
      </div>

      <div style={{ marginBottom: '15px' }}>
        <input
          name="email"
          type="email"
          value={formData.email}
          onChange={handleChange}
          placeholder="Your email"
          style={{ width: '100%', padding: '10px' }}
        />
      </div>

      <div style={{ marginBottom: '15px' }}>
        <textarea
          name="message"
          value={formData.message}
          onChange={handleChange}
          placeholder="Your message"
          style={{ width: '100%', padding: '10px', minHeight: '100px' }}
        />
      </div>

      <button type="submit" style={{ padding: '10px 20px' }}>
        Submit
      </button>
    </form>
  );
}
```

---

## 🎯 Common Patterns

### Toggle Pattern

```javascript
const [isOpen, setIsOpen] = useState(false);

// Toggle
<button onClick={() => setIsOpen(!isOpen)}>Toggle</button>

// Or using previous state
<button onClick={() => setIsOpen(prev => !prev)}>Toggle</button>
```

### Increment/Decrement Pattern

```javascript
const [count, setCount] = useState(0);

<button onClick={() => setCount(c => c + 1)}>+</button>
<button onClick={() => setCount(c => c - 1)}>-</button>
```

### Form Input Pattern

```javascript
const [value, setValue] = useState("");

<input
  value={value}
  onChange={(e) => setValue(e.target.value)}
/>
```

---

## ✏️ Practice Exercise

Create a simple app with:
1. A counter (starts at 0)
2. Buttons to increment, decrement, and reset
3. Show "Even" or "Odd" based on count
4. Change background color based on count (red if negative, green if positive, gray if zero)

<details>
<summary>Solution</summary>

```javascript
import { useState } from 'react';

function CounterApp() {
  const [count, setCount] = useState(0);

  const getBackgroundColor = () => {
    if (count < 0) return '#ffcccc';  // Light red
    if (count > 0) return '#ccffcc';  // Light green
    return '#f0f0f0';  // Gray
  };

  return (
    <div style={{
      textAlign: 'center',
      padding: '40px',
      backgroundColor: getBackgroundColor(),
      minHeight: '100vh',
      transition: 'background-color 0.3s'
    }}>
      <h1>Counter App</h1>

      <h2 style={{ fontSize: '60px', margin: '20px 0' }}>
        {count}
      </h2>

      <p style={{ fontSize: '24px', marginBottom: '20px' }}>
        {count % 2 === 0 ? "Even" : "Odd"}
      </p>

      <div style={{ display: 'flex', gap: '10px', justifyContent: 'center' }}>
        <button
          onClick={() => setCount(count + 1)}
          style={{
            padding: '15px 30px',
            fontSize: '18px',
            cursor: 'pointer',
            backgroundColor: '#28a745',
            color: 'white',
            border: 'none',
            borderRadius: '5px'
          }}
        >
          Increment (+1)
        </button>

        <button
          onClick={() => setCount(count - 1)}
          style={{
            padding: '15px 30px',
            fontSize: '18px',
            cursor: 'pointer',
            backgroundColor: '#dc3545',
            color: 'white',
            border: 'none',
            borderRadius: '5px'
          }}
        >
          Decrement (-1)
        </button>

        <button
          onClick={() => setCount(0)}
          style={{
            padding: '15px 30px',
            fontSize: '18px',
            cursor: 'pointer',
            backgroundColor: '#6c757d',
            color: 'white',
            border: 'none',
            borderRadius: '5px'
          }}
        >
          Reset
        </button>
      </div>
    </div>
  );
}

export default CounterApp;
```

</details>

---

## 🎯 Key Takeaways

1. **`useState`** creates reactive state
2. **`const [value, setValue] = useState(initial)`** syntax
3. **Always use setter function** (`setValue()`), never mutate directly
4. **Component re-renders** when state changes
5. **Multiple state variables** with multiple `useState` calls
6. **Update based on previous state:** `setValue(prev => prev + 1)`
7. **State is local** to the component

---

## 🚀 Next Steps

You now know:
- ✅ JSX - The syntax of React
- ✅ Components - Building blocks
- ✅ Props - Passing data down
- ✅ useState - Making components interactive

**You're ready to build React apps!**

Continue learning:
- useEffect (side effects, data fetching)
- Custom hooks
- Context API (global state)
- Next.js (React framework)

---

**useState is the key to interactive UIs. Master it, and you can build anything in React.** ⚛️
