# Lesson 4: Objects

> **"Objects store structured data. They're the foundation of everything in JavaScript."**

---

## 🎯 What are Objects?

**Objects store data as key-value pairs.**

Think of an object like a **person's profile** or **product information**:
- **Key** = Property name (like "name", "age", "email")
- **Value** = The actual data

```javascript
const person = {
  name: "Alice",
  age: 25,
  email: "alice@example.com"
};
```

---

## 📝 Creating Objects

```javascript
// Object literal (most common)
const user = {
  name: "John",
  age: 30,
  isAdmin: true
};

// Empty object
const empty = {};
```

---

## 📊 Accessing Object Properties

### Dot Notation (most common)

```javascript
const user = {
  name: "Alice",
  age: 25
};

console.log(user.name);  // "Alice"
console.log(user.age);   // 25
```

### Bracket Notation

```javascript
const user = {
  name: "Alice",
  age: 25
};

console.log(user["name"]);  // "Alice"
console.log(user["age"]);   // 25
```

**When to use brackets:**
- Property name has spaces
- Property name is in a variable

```javascript
const user = {
  "first name": "Alice",  // Has space
  age: 25
};

console.log(user["first name"]);  // Must use brackets

const property = "age";
console.log(user[property]);  // 25 (using variable)
```

---

## ✏️ Modifying Objects

### Add/Update Properties

```javascript
const user = {
  name: "Alice"
};

user.age = 25;          // Add new property
user.name = "Alicia";   // Update existing property

console.log(user);  // { name: "Alicia", age: 25 }
```

### Delete Properties

```javascript
const user = {
  name: "Alice",
  age: 25,
  temp: "remove this"
};

delete user.temp;

console.log(user);  // { name: "Alice", age: 25 }
```

---

## 🎨 Objects with Methods

**Methods are functions inside objects:**

```javascript
const person = {
  name: "Alice",
  age: 25,
  greet: function() {
    console.log(`Hello, I'm ${this.name}!`);
  }
};

person.greet();  // "Hello, I'm Alice!"
```

**Shorthand syntax (modern):**

```javascript
const person = {
  name: "Alice",
  age: 25,
  greet() {
    console.log(`Hello, I'm ${this.name}!`);
  },
  celebrateBirthday() {
    this.age++;
    console.log(`I'm now ${this.age}!`);
  }
};

person.greet();  // "Hello, I'm Alice!"
person.celebrateBirthday();  // "I'm now 26!"
```

**`this` refers to the object itself.**

---

## 🔄 Nested Objects

**Objects can contain other objects:**

```javascript
const user = {
  name: "Alice",
  age: 25,
  address: {
    street: "123 Main St",
    city: "New York",
    zip: "10001"
  },
  social: {
    twitter: "@alice",
    github: "alice-dev"
  }
};

console.log(user.address.city);  // "New York"
console.log(user.social.twitter);  // "@alice"
```

---

## 🎯 Object Destructuring

**Extract properties into variables:**

```javascript
const user = {
  name: "Alice",
  age: 25,
  email: "alice@example.com"
};

// Old way
const name = user.name;
const age = user.age;

// Destructuring (modern)
const { name, age, email } = user;

console.log(name);   // "Alice"
console.log(age);    // 25
console.log(email);  // "alice@example.com"
```

**With different variable names:**

```javascript
const { name: userName, age: userAge } = user;
console.log(userName);  // "Alice"
console.log(userAge);   // 25
```

---

## 🔧 Useful Object Methods

### Object.keys()

```javascript
const user = { name: "Alice", age: 25, email: "alice@example.com" };

const keys = Object.keys(user);
console.log(keys);  // ["name", "age", "email"]
```

### Object.values()

```javascript
const user = { name: "Alice", age: 25, email: "alice@example.com" };

const values = Object.values(user);
console.log(values);  // ["Alice", 25, "alice@example.com"]
```

### Object.entries()

```javascript
const user = { name: "Alice", age: 25 };

const entries = Object.entries(user);
console.log(entries);
// [["name", "Alice"], ["age", 25]]

// Loop through
entries.forEach(([key, value]) => {
  console.log(`${key}: ${value}`);
});
// name: Alice
// age: 25
```

---

## 🎨 Real-World Examples

### Example 1: User Profile

```javascript
const user = {
  id: 1,
  username: "alice_dev",
  email: "alice@example.com",
  isVerified: true,
  posts: 42,
  followers: 1250,
  getDisplayName() {
    return `@${this.username}`;
  },
  isPopular() {
    return this.followers > 1000;
  }
};

console.log(user.getDisplayName());  // "@alice_dev"
console.log(user.isPopular());       // true
```

### Example 2: Shopping Cart

```javascript
const cart = {
  items: [],
  total: 0,
  addItem(item) {
    this.items.push(item);
    this.total += item.price;
  },
  removeItem(itemId) {
    const index = this.items.findIndex(item => item.id === itemId);
    if (index !== -1) {
      this.total -= this.items[index].price;
      this.items.splice(index, 1);
    }
  },
  getItemCount() {
    return this.items.length;
  }
};

cart.addItem({ id: 1, name: "Shirt", price: 20 });
cart.addItem({ id: 2, name: "Pants", price: 40 });

console.log(cart.total);  // 60
console.log(cart.getItemCount());  // 2
```

### Example 3: Product

```javascript
const product = {
  id: 101,
  name: "Wireless Mouse",
  price: 29.99,
  inStock: true,
  ratings: [5, 4, 5, 4, 5],
  getAverageRating() {
    const sum = this.ratings.reduce((total, rating) => total + rating, 0);
    return sum / this.ratings.length;
  },
  applyDiscount(percent) {
    this.price = this.price * (1 - percent / 100);
    return this.price;
  }
};

console.log(product.getAverageRating());  // 4.6
console.log(product.applyDiscount(20));   // 23.992
```

---

## 🎨 Complete Working Example

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Objects Demo</title>
</head>
<body>
  <h1>Product Dashboard</h1>
  <div id="output"></div>

  <script>
    const products = [
      {
        id: 1,
        name: "Laptop",
        price: 999,
        category: "Electronics",
        inStock: true
      },
      {
        id: 2,
        name: "Mouse",
        price: 29,
        category: "Electronics",
        inStock: true
      },
      {
        id: 3,
        name: "Desk",
        price: 199,
        category: "Furniture",
        inStock: false
      }
    ];

    // Display products
    const output = document.getElementById('output');

    products.forEach(product => {
      const div = document.createElement('div');
      div.style.padding = "10px";
      div.style.margin = "10px 0";
      div.style.border = "1px solid #ddd";
      div.style.borderRadius = "5px";

      div.innerHTML = `
        <h3>${product.name}</h3>
        <p>Price: $${product.price}</p>
        <p>Category: ${product.category}</p>
        <p>Status: ${product.inStock ? '✓ In Stock' : '✗ Out of Stock'}</p>
      `;

      output.appendChild(div);
    });

    // Filter electronics
    const electronics = products.filter(p => p.category === "Electronics");
    console.log("Electronics:", electronics);

    // Calculate total value
    const totalValue = products.reduce((sum, p) => sum + p.price, 0);
    console.log("Total value:", totalValue);

    // Get product names
    const names = products.map(p => p.name);
    console.log("Product names:", names);
  </script>
</body>
</html>
```

---

## ✏️ Practice Exercise

Create an object representing a book with:
1. Properties: title, author, pages, isRead
2. Method: getSummary() that returns a string description
3. Method: markAsRead() that sets isRead to true
4. Create an array of 3 books
5. Filter to get only read books
6. Map to get array of titles

<details>
<summary>Solution</summary>

```javascript
// 1-3. Book object with methods
const book1 = {
  title: "The Great Gatsby",
  author: "F. Scott Fitzgerald",
  pages: 180,
  isRead: false,
  getSummary() {
    return `${this.title} by ${this.author}, ${this.pages} pages`;
  },
  markAsRead() {
    this.isRead = true;
  }
};

const book2 = {
  title: "1984",
  author: "George Orwell",
  pages: 328,
  isRead: true,
  getSummary() {
    return `${this.title} by ${this.author}, ${this.pages} pages`;
  },
  markAsRead() {
    this.isRead = true;
  }
};

const book3 = {
  title: "To Kill a Mockingbird",
  author: "Harper Lee",
  pages: 324,
  isRead: true,
  getSummary() {
    return `${this.title} by ${this.author}, ${this.pages} pages`;
  },
  markAsRead() {
    this.isRead = true;
  }
};

// 4. Array of books
const books = [book1, book2, book3];

// 5. Filter read books
const readBooks = books.filter(book => book.isRead);
console.log("Read books:", readBooks);

// 6. Get titles
const titles = books.map(book => book.title);
console.log("Titles:", titles);

// Test methods
console.log(book1.getSummary());
book1.markAsRead();
console.log("Book 1 read status:", book1.isRead);  // true
```

</details>

---

## 🎯 Key Takeaways

1. **Objects** store data as key-value pairs
2. **Dot notation** `object.property` (most common)
3. **Bracket notation** `object["property"]` (when needed)
4. **Methods** are functions inside objects
5. **`this`** refers to the object itself
6. **Destructuring** extracts properties: `const { name } = user`
7. **Objects can be nested** (objects inside objects)
8. **Use `Object.keys()`, `Object.values()`, `Object.entries()`** for iteration

---

## 🚀 Next Lesson

Now you can structure data. Next, learn **loops** - repeating code efficiently!

**Next:** [Lesson 5: Loops & Conditionals →](./05-loops-conditionals.md)

---

**Objects are the foundation of JavaScript. Master them, and you'll understand how everything works.** 🎯
