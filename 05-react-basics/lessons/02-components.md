# Lesson 2: Components

> **"Components are reusable pieces of UI. Write once, use everywhere."**

---

## 🎯 What are Components?

**Components are like LEGO blocks** - small, reusable pieces you combine to build something bigger.

Instead of:
```html
<!-- Copy-paste navigation on every page -->
<nav>...</nav>
<nav>...</nav>
<nav>...</nav>
```

Use a component:
```javascript
<Navigation />
<Navigation />
<Navigation />
```

**Change it once, updates everywhere!**

---

## 📝 Function Components (Modern Way)

```javascript
function Greeting() {
  return <h1>Hello, World!</h1>;
}

// Use it:
<Greeting />
```

**That's it!** A component is just a function that returns JSX.

---

## 🎨 Creating Your First Component

```javascript
// Button.jsx
function Button() {
  return (
    <button style={{
      padding: '10px 20px',
      backgroundColor: '#007bff',
      color: 'white',
      border: 'none',
      borderRadius: '5px',
      cursor: 'pointer'
    }}>
      Click Me
    </button>
  );
}

export default Button;
```

```javascript
// App.jsx
import Button from './Button';

function App() {
  return (
    <div>
      <h1>My App</h1>
      <Button />
      <Button />
      <Button />
    </div>
  );
}
```

**Three buttons with one component!**

---

## 🎯 Component Naming Rules

1. **Must start with capital letter** (not lowercase)
2. **Use PascalCase** (each word capitalized)

```javascript
// ✅ CORRECT
function UserProfile() { }
function NavigationBar() { }
function ProductCard() { }

// ❌ WRONG
function userProfile() { }  // lowercase
function navigation_bar() { }  // snake_case
```

---

## 📁 File Structure

```
src/
  ├── App.jsx
  ├── components/
  │   ├── Header.jsx
  │   ├── Footer.jsx
  │   ├── Button.jsx
  │   └── Card.jsx
```

**Common pattern:** One component per file, named same as component.

---

## 🎨 Composing Components

**Components can use other components:**

```javascript
// Header.jsx
function Header() {
  return (
    <header>
      <h1>My Website</h1>
      <Navigation />
    </header>
  );
}

// Navigation.jsx
function Navigation() {
  return (
    <nav>
      <a href="/">Home</a>
      <a href="/about">About</a>
    </nav>
  );
}

// App.jsx
function App() {
  return (
    <div>
      <Header />
      <main>
        <h2>Welcome!</h2>
      </main>
      <Footer />
    </div>
  );
}
```

---

## 🎯 Exporting & Importing Components

### Default Export (one per file)

```javascript
// Button.jsx
function Button() {
  return <button>Click</button>;
}

export default Button;
```

```javascript
// App.jsx
import Button from './Button';  // Can name it anything

<Button />
```

### Named Export (multiple per file)

```javascript
// components.jsx
export function Button() {
  return <button>Click</button>;
}

export function Input() {
  return <input type="text" />;
}
```

```javascript
// App.jsx
import { Button, Input } from './components';  // Must use exact names

<Button />
<Input />
```

**Most common:** Default export, one component per file.

---

## 🎨 Real-World Example: Card Component

```javascript
// Card.jsx
function Card() {
  return (
    <div style={{
      border: '1px solid #ddd',
      borderRadius: '8px',
      padding: '20px',
      maxWidth: '300px',
      boxShadow: '0 2px 4px rgba(0,0,0,0.1)'
    }}>
      <img
        src="https://via.placeholder.com/300x200"
        alt="Placeholder"
        style={{ width: '100%', borderRadius: '4px' }}
      />
      <h2>Card Title</h2>
      <p>This is some card content.</p>
      <button style={{
        padding: '10px 20px',
        backgroundColor: '#007bff',
        color: 'white',
        border: 'none',
        borderRadius: '4px',
        cursor: 'pointer'
      }}>
        Learn More
      </button>
    </div>
  );
}

export default Card;
```

```javascript
// App.jsx
import Card from './Card';

function App() {
  return (
    <div style={{ display: 'flex', gap: '20px', padding: '20px' }}>
      <Card />
      <Card />
      <Card />
    </div>
  );
}
```

---

## 🎯 Component Best Practices

### 1. **One component = One responsibility**

```javascript
// ❌ BAD - Does too much
function UserDashboard() {
  return (
    <div>
      <header>...</header>
      <nav>...</nav>
      <sidebar>...</sidebar>
      <main>...</main>
      <footer>...</footer>
    </div>
  );
}

// ✅ GOOD - Split into components
function UserDashboard() {
  return (
    <div>
      <Header />
      <Navigation />
      <Sidebar />
      <MainContent />
      <Footer />
    </div>
  );
}
```

### 2. **Keep components small**

If it's getting long (>100 lines), split it!

### 3. **Name components clearly**

```javascript
// ❌ BAD
function Comp1() { }
function Thing() { }

// ✅ GOOD
function UserProfile() { }
function ProductCard() { }
function NavigationMenu() { }
```

---

## 🎨 Complete Working Example

```javascript
// App.jsx
import Header from './components/Header';
import ProductCard from './components/ProductCard';
import Footer from './components/Footer';

function App() {
  return (
    <div style={{ minHeight: '100vh', display: 'flex', flexDirection: 'column' }}>
      <Header />

      <main style={{ flex: 1, padding: '20px' }}>
        <h1>Our Products</h1>
        <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(250px, 1fr))', gap: '20px' }}>
          <ProductCard />
          <ProductCard />
          <ProductCard />
          <ProductCard />
        </div>
      </main>

      <Footer />
    </div>
  );
}

export default App;
```

```javascript
// components/Header.jsx
function Header() {
  return (
    <header style={{
      backgroundColor: '#333',
      color: 'white',
      padding: '20px',
      textAlign: 'center'
    }}>
      <h1>My Store</h1>
      <nav>
        <a href="/" style={{ color: 'white', margin: '0 10px' }}>Home</a>
        <a href="/products" style={{ color: 'white', margin: '0 10px' }}>Products</a>
        <a href="/contact" style={{ color: 'white', margin: '0 10px' }}>Contact</a>
      </nav>
    </header>
  );
}

export default Header;
```

```javascript
// components/ProductCard.jsx
function ProductCard() {
  return (
    <div style={{
      border: '1px solid #ddd',
      borderRadius: '8px',
      padding: '15px',
      backgroundColor: 'white'
    }}>
      <div style={{
        width: '100%',
        height: '150px',
        backgroundColor: '#f0f0f0',
        borderRadius: '4px',
        marginBottom: '10px'
      }} />
      <h3>Product Name</h3>
      <p style={{ color: '#666' }}>$29.99</p>
      <button style={{
        width: '100%',
        padding: '10px',
        backgroundColor: '#007bff',
        color: 'white',
        border: 'none',
        borderRadius: '4px',
        cursor: 'pointer'
      }}>
        Add to Cart
      </button>
    </div>
  );
}

export default ProductCard;
```

```javascript
// components/Footer.jsx
function Footer() {
  return (
    <footer style={{
      backgroundColor: '#f8f9fa',
      padding: '20px',
      textAlign: 'center',
      borderTop: '1px solid #dee2e6'
    }}>
      <p>&copy; 2024 My Store. All rights reserved.</p>
    </footer>
  );
}

export default Footer;
```

---

## ✏️ Practice Exercise

Create these components:

1. **Navbar** - Logo and 3 links
2. **HeroSection** - Large heading and description
3. **FeatureCard** - Icon, title, description
4. **App** - Uses all three components above

<details>
<summary>Solution</summary>

```javascript
// Navbar.jsx
function Navbar() {
  return (
    <nav style={{
      display: 'flex',
      justifyContent: 'space-between',
      alignItems: 'center',
      padding: '20px',
      backgroundColor: '#333',
      color: 'white'
    }}>
      <h2>LOGO</h2>
      <div style={{ display: 'flex', gap: '20px' }}>
        <a href="/" style={{ color: 'white', textDecoration: 'none' }}>Home</a>
        <a href="/about" style={{ color: 'white', textDecoration: 'none' }}>About</a>
        <a href="/contact" style={{ color: 'white', textDecoration: 'none' }}>Contact</a>
      </div>
    </nav>
  );
}

export default Navbar;
```

```javascript
// HeroSection.jsx
function HeroSection() {
  return (
    <section style={{
      textAlign: 'center',
      padding: '80px 20px',
      backgroundColor: '#f8f9fa'
    }}>
      <h1 style={{ fontSize: '48px', marginBottom: '20px' }}>
        Welcome to Our Site
      </h1>
      <p style={{ fontSize: '20px', color: '#666', maxWidth: '600px', margin: '0 auto' }}>
        We build amazing products that help you succeed. Start your journey with us today!
      </p>
    </section>
  );
}

export default HeroSection;
```

```javascript
// FeatureCard.jsx
function FeatureCard() {
  return (
    <div style={{
      textAlign: 'center',
      padding: '30px',
      border: '1px solid #ddd',
      borderRadius: '8px'
    }}>
      <div style={{
        fontSize: '48px',
        marginBottom: '15px'
      }}>⚡</div>
      <h3>Fast Performance</h3>
      <p style={{ color: '#666' }}>
        Lightning-fast load times for the best user experience.
      </p>
    </div>
  );
}

export default FeatureCard;
```

```javascript
// App.jsx
import Navbar from './components/Navbar';
import HeroSection from './components/HeroSection';
import FeatureCard from './components/FeatureCard';

function App() {
  return (
    <div>
      <Navbar />
      <HeroSection />

      <section style={{
        display: 'grid',
        gridTemplateColumns: 'repeat(auto-fit, minmax(250px, 1fr))',
        gap: '20px',
        padding: '40px 20px',
        maxWidth: '1200px',
        margin: '0 auto'
      }}>
        <FeatureCard />
        <FeatureCard />
        <FeatureCard />
      </section>
    </div>
  );
}

export default App;
```

</details>

---

## 🎯 Key Takeaways

1. **Components** = Reusable pieces of UI
2. **Function components** (modern way)
3. **Must start with capital letter** (PascalCase)
4. **Return JSX** from the function
5. **One component per file** (usually)
6. **Components can use other components**
7. **Export/import** to use in other files

---

## 🚀 Next Lesson

Now you can build components. Next, learn **Props** - making components dynamic and reusable!

**Next:** [Lesson 3: Props →](./03-props.md)

---

**Components are the building blocks of React. Master them, and you can build anything.** 🧱
