# Lesson 3: Props

> **"Props make components reusable with different data. They're like function parameters for components."**

---

## 🎯 What are Props?

**Props (properties) = Data passed to components**

Like function parameters:
```javascript
// Function with parameters
function greet(name) {
  return `Hello, ${name}!`;
}

// Component with props
function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}
```

---

## 📝 Passing Props

```javascript
// Parent component
function App() {
  return (
    <div>
      <Greeting name="Alice" />
      <Greeting name="Bob" />
      <Greeting name="Charlie" />
    </div>
  );
}

// Child component
function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}
```

**Same component, different data!**

---

## 🎨 Multiple Props

```javascript
function UserCard({ name, age, email }) {
  return (
    <div style={{ border: '1px solid #ddd', padding: '20px', borderRadius: '8px' }}>
      <h2>{name}</h2>
      <p>Age: {age}</p>
      <p>Email: {email}</p>
    </div>
  );
}

// Usage
<UserCard name="Alice" age={25} email="alice@example.com" />
<UserCard name="Bob" age={30} email="bob@example.com" />
```

**Note:** Numbers and booleans use `{curly braces}`, strings can use quotes.

---

## 🎯 Props Syntax (Two Ways)

### Method 1: Destructuring (Modern, Preferred)

```javascript
function Button({ text, color }) {
  return <button style={{ backgroundColor: color }}>{text}</button>;
}
```

### Method 2: Props Object

```javascript
function Button(props) {
  return <button style={{ backgroundColor: props.color }}>{props.text}</button>;
}
```

**Use destructuring - it's cleaner!**

---

## 🎨 All Types of Props

```javascript
function Demo({
  // String
  name,

  // Number
  age,

  // Boolean
  isActive,

  // Array
  hobbies,

  // Object
  address,

  // Function
  onClick
}) {
  return (
    <div>
      <p>{name}</p>
      <p>{age}</p>
      <p>{isActive ? "Active" : "Inactive"}</p>
      <ul>
        {hobbies.map((hobby, i) => <li key={i}>{hobby}</li>)}
      </ul>
      <p>{address.city}</p>
      <button onClick={onClick}>Click</button>
    </div>
  );
}

// Usage
<Demo
  name="Alice"
  age={25}
  isActive={true}
  hobbies={["reading", "coding"]}
  address={{ city: "New York", zip: "10001" }}
  onClick={() => alert("Clicked!")}
/>
```

---

## 🎯 Default Props

```javascript
function Button({ text = "Click Me", color = "blue" }) {
  return <button style={{ backgroundColor: color }}>{text}</button>;
}

// If no props provided, uses defaults
<Button />  // Uses "Click Me" and "blue"
<Button text="Submit" />  // Uses "Submit" and "blue"
<Button text="Cancel" color="red" />  // Uses both custom values
```

---

## 🎯 Children Prop (Special)

**`children` = Content between opening/closing tags:**

```javascript
function Card({ children }) {
  return (
    <div style={{ border: '1px solid #ddd', padding: '20px', borderRadius: '8px' }}>
      {children}
    </div>
  );
}

// Usage
<Card>
  <h2>Title</h2>
  <p>This is the card content!</p>
</Card>

<Card>
  <img src="photo.jpg" alt="Photo" />
  <p>Photo caption</p>
</Card>
```

**`children` can be anything** - text, elements, other components!

---

## 🎨 Real-World Example: Product Card

```javascript
function ProductCard({ name, price, image, inStock, onAddToCart }) {
  return (
    <div style={{
      border: '1px solid #ddd',
      borderRadius: '8px',
      padding: '15px',
      backgroundColor: 'white'
    }}>
      <img
        src={image}
        alt={name}
        style={{
          width: '100%',
          height: '200px',
          objectFit: 'cover',
          borderRadius: '4px'
        }}
      />
      <h3>{name}</h3>
      <p style={{ fontSize: '24px', color: '#007bff', fontWeight: 'bold' }}>
        ${price}
      </p>

      {inStock ? (
        <button
          onClick={onAddToCart}
          style={{
            width: '100%',
            padding: '10px',
            backgroundColor: '#28a745',
            color: 'white',
            border: 'none',
            borderRadius: '4px',
            cursor: 'pointer'
          }}
        >
          Add to Cart
        </button>
      ) : (
        <button
          disabled
          style={{
            width: '100%',
            padding: '10px',
            backgroundColor: '#ccc',
            color: '#666',
            border: 'none',
            borderRadius: '4px'
          }}
        >
          Out of Stock
        </button>
      )}
    </div>
  );
}

// Usage
function App() {
  const handleAddToCart = (productName) => {
    alert(`Added ${productName} to cart!`);
  };

  return (
    <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(250px, 1fr))', gap: '20px', padding: '20px' }}>
      <ProductCard
        name="Laptop"
        price={999}
        image="https://via.placeholder.com/300x200"
        inStock={true}
        onAddToCart={() => handleAddToCart("Laptop")}
      />

      <ProductCard
        name="Mouse"
        price={29}
        image="https://via.placeholder.com/300x200"
        inStock={true}
        onAddToCart={() => handleAddToCart("Mouse")}
      />

      <ProductCard
        name="Keyboard"
        price={79}
        image="https://via.placeholder.com/300x200"
        inStock={false}
        onAddToCart={() => handleAddToCart("Keyboard")}
      />
    </div>
  );
}
```

---

## 🎯 Props are Read-Only!

**You CANNOT modify props:**

```javascript
function Button({ text }) {
  text = "Different";  // ❌ ERROR! Props are read-only
  return <button>{text}</button>;
}
```

**Why?** Props flow down from parent. Only parent can change them.

---

## 🎨 Spreading Props

```javascript
const user = {
  name: "Alice",
  age: 25,
  email: "alice@example.com"
};

// Instead of:
<UserCard name={user.name} age={user.age} email={user.email} />

// Use spread:
<UserCard {...user} />
```

---

## ✏️ Practice Exercise

Create a `BlogPost` component that accepts:
1. `title` (string)
2. `author` (string)
3. `date` (string)
4. `content` (string)
5. `likes` (number)
6. Make it reusable - use it 3 times with different data

<details>
<summary>Solution</summary>

```javascript
// BlogPost.jsx
function BlogPost({ title, author, date, content, likes }) {
  return (
    <article style={{
      border: '1px solid #ddd',
      borderRadius: '8px',
      padding: '20px',
      marginBottom: '20px',
      backgroundColor: 'white'
    }}>
      <h2>{title}</h2>
      <div style={{ color: '#666', marginBottom: '10px' }}>
        <span>By {author}</span> | <span>{date}</span>
      </div>
      <p style={{ lineHeight: 1.6 }}>{content}</p>
      <div style={{ marginTop: '15px', color: '#007bff' }}>
        👍 {likes} likes
      </div>
    </article>
  );
}

// App.jsx
function App() {
  return (
    <div style={{ maxWidth: '800px', margin: '0 auto', padding: '20px' }}>
      <h1>My Blog</h1>

      <BlogPost
        title="Getting Started with React"
        author="Alice"
        date="2024-01-15"
        content="React is a JavaScript library for building user interfaces. In this post, we'll explore the basics of React components and props."
        likes={42}
      />

      <BlogPost
        title="Understanding JavaScript Arrays"
        author="Bob"
        date="2024-01-20"
        content="Arrays are one of the most important data structures in JavaScript. Let's learn about map, filter, and reduce methods."
        likes={38}
      />

      <BlogPost
        title="CSS Flexbox Guide"
        author="Charlie"
        date="2024-01-25"
        content="Flexbox makes creating layouts much easier. This guide will show you everything you need to know about Flexbox."
        likes={56}
      />
    </div>
  );
}
```

</details>

---

## 🎯 Key Takeaways

1. **Props** = Data passed to components
2. **Destructure in parameters:** `function Component({ prop1, prop2 })`
3. **Strings:** `text="value"` or `text={"value"}`
4. **Numbers/Booleans/Objects:** `age={25}` `isActive={true}`
5. **Functions as props:** `onClick={handleClick}`
6. **`children`** = Content between tags
7. **Props are read-only** (can't modify them)
8. **Default values:** `function Component({ name = "Guest" })`

---

## 🚀 Next Lesson

Now you can pass data to components. Next, learn **State** - making components interactive and dynamic!

**Next:** [Lesson 4: useState →](./04-useState.md)

---

**Props make components reusable. Master them, and you can build flexible, dynamic UIs.** 🎁
