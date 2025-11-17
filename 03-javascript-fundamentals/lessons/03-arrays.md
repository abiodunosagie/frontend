# Lesson 3: Arrays & Array Methods

> **"Arrays store lists of data. Array methods let you manipulate that data like a pro."**

---

## 📋 What are Arrays?

**Arrays are ordered lists of values.**

Think of an array like a **shopping list** or **todo list**:
```javascript
const shoppingList = ["apples", "bread", "milk"];
const numbers = [1, 2, 3, 4, 5];
const mixed = ["text", 42, true, null];
```

---

## 🎯 Creating Arrays

```javascript
// Array literal (most common)
const fruits = ["apple", "banana", "orange"];

// Empty array
const empty = [];

// Array with different types
const mixed = ["text", 42, true, null, undefined];
```

---

## 📊 Accessing Array Elements

**Arrays are zero-indexed** (first item is at index 0):

```javascript
const fruits = ["apple", "banana", "orange"];

console.log(fruits[0]);  // "apple"
console.log(fruits[1]);  // "banana"
console.log(fruits[2]);  // "orange"
console.log(fruits[3]);  // undefined (doesn't exist)
```

---

## 🔧 Array Properties & Basic Methods

### Length

```javascript
const fruits = ["apple", "banana", "orange"];
console.log(fruits.length);  // 3
```

### Add to End

```javascript
const fruits = ["apple", "banana"];
fruits.push("orange");
console.log(fruits);  // ["apple", "banana", "orange"]
```

### Remove from End

```javascript
const fruits = ["apple", "banana", "orange"];
const last = fruits.pop();
console.log(last);    // "orange"
console.log(fruits);  // ["apple", "banana"]
```

### Add to Beginning

```javascript
const fruits = ["banana", "orange"];
fruits.unshift("apple");
console.log(fruits);  // ["apple", "banana", "orange"]
```

### Remove from Beginning

```javascript
const fruits = ["apple", "banana", "orange"];
const first = fruits.shift();
console.log(first);   // "apple"
console.log(fruits);  // ["banana", "orange"]
```

---

## 🎨 Essential Array Methods

### 1. **map()** - Transform every item

```javascript
const numbers = [1, 2, 3, 4, 5];

const doubled = numbers.map(num => num * 2);
console.log(doubled);  // [2, 4, 6, 8, 10]

const squared = numbers.map(num => num * num);
console.log(squared);  // [1, 4, 9, 16, 25]
```

**Real example:**

```javascript
const prices = [19.99, 29.99, 9.99];
const formatted = prices.map(price => `$${price}`);
console.log(formatted);  // ["$19.99", "$29.99", "$9.99"]
```

---

### 2. **filter()** - Keep items that match condition

```javascript
const numbers = [1, 2, 3, 4, 5, 6];

const evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers);  // [2, 4, 6]

const greaterThanThree = numbers.filter(num => num > 3);
console.log(greaterThanThree);  // [4, 5, 6]
```

**Real example:**

```javascript
const users = [
  { name: "Alice", age: 25 },
  { name: "Bob", age: 17 },
  { name: "Charlie", age: 30 }
];

const adults = users.filter(user => user.age >= 18);
console.log(adults);
// [{ name: "Alice", age: 25 }, { name: "Charlie", age: 30 }]
```

---

### 3. **find()** - Find first matching item

```javascript
const numbers = [1, 2, 3, 4, 5];

const found = numbers.find(num => num > 3);
console.log(found);  // 4 (first one that matches)
```

**Real example:**

```javascript
const users = [
  { id: 1, name: "Alice" },
  { id: 2, name: "Bob" },
  { id: 3, name: "Charlie" }
];

const user = users.find(u => u.id === 2);
console.log(user);  // { id: 2, name: "Bob" }
```

---

### 4. **reduce()** - Reduce array to single value

```javascript
const numbers = [1, 2, 3, 4, 5];

const sum = numbers.reduce((total, num) => total + num, 0);
console.log(sum);  // 15
```

**Breaking it down:**
- `total` = Accumulator (running total)
- `num` = Current item
- `0` = Starting value

**Real example:**

```javascript
const cart = [
  { item: "Shirt", price: 20 },
  { item: "Pants", price: 40 },
  { item: "Shoes", price: 60 }
];

const total = cart.reduce((sum, item) => sum + item.price, 0);
console.log(total);  // 120
```

---

### 5. **forEach()** - Loop through array

```javascript
const fruits = ["apple", "banana", "orange"];

fruits.forEach(fruit => {
  console.log(fruit);
});
// apple
// banana
// orange
```

**With index:**

```javascript
fruits.forEach((fruit, index) => {
  console.log(`${index}: ${fruit}`);
});
// 0: apple
// 1: banana
// 2: orange
```

---

## 🎯 Other Useful Methods

### includes()

```javascript
const fruits = ["apple", "banana", "orange"];
console.log(fruits.includes("banana"));  // true
console.log(fruits.includes("grape"));   // false
```

### indexOf()

```javascript
const fruits = ["apple", "banana", "orange"];
console.log(fruits.indexOf("banana"));  // 1
console.log(fruits.indexOf("grape"));   // -1 (not found)
```

### join()

```javascript
const fruits = ["apple", "banana", "orange"];
const result = fruits.join(", ");
console.log(result);  // "apple, banana, orange"
```

### slice()

```javascript
const fruits = ["apple", "banana", "orange", "grape", "melon"];
const some = fruits.slice(1, 3);
console.log(some);  // ["banana", "orange"] (index 1 to 3, not including 3)
```

### concat()

```javascript
const fruits = ["apple", "banana"];
const veggies = ["carrot", "broccoli"];
const combined = fruits.concat(veggies);
console.log(combined);  // ["apple", "banana", "carrot", "broccoli"]
```

---

## 🎨 Chaining Methods

**You can chain methods together:**

```javascript
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

const result = numbers
  .filter(num => num % 2 === 0)   // Get even numbers: [2, 4, 6, 8, 10]
  .map(num => num * 2)             // Double them: [4, 8, 12, 16, 20]
  .reduce((sum, num) => sum + num, 0);  // Sum them up: 60

console.log(result);  // 60
```

---

## 🎨 Real-World Example

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Arrays Demo</title>
</head>
<body>
  <h1>Product List</h1>
  <div id="products"></div>
  <p>Total: $<span id="total">0</span></p>

  <script>
    const products = [
      { id: 1, name: "Laptop", price: 999 },
      { id: 2, name: "Mouse", price: 29 },
      { id: 3, name: "Keyboard", price: 79 },
      { id: 4, name: "Monitor", price: 299 }
    ];

    // Display products
    const productsDiv = document.getElementById('products');
    products.forEach(product => {
      const div = document.createElement('div');
      div.textContent = `${product.name}: $${product.price}`;
      productsDiv.appendChild(div);
    });

    // Calculate total
    const total = products.reduce((sum, p) => sum + p.price, 0);
    document.getElementById('total').textContent = total;

    // Filter expensive products (>$100)
    const expensive = products.filter(p => p.price > 100);
    console.log("Expensive products:", expensive);

    // Get product names
    const names = products.map(p => p.name);
    console.log("Product names:", names);

    // Find specific product
    const keyboard = products.find(p => p.name === "Keyboard");
    console.log("Found:", keyboard);
  </script>
</body>
</html>
```

---

## ✏️ Practice Exercise

Given this array:
```javascript
const users = [
  { name: "Alice", age: 25, premium: true },
  { name: "Bob", age: 17, premium: false },
  { name: "Charlie", age: 30, premium: true },
  { name: "David", age: 22, premium: false }
];
```

Write code to:
1. Get all premium users
2. Get all adult users (age >= 18)
3. Get array of just names
4. Calculate average age
5. Check if any user is named "Bob"

<details>
<summary>Solution</summary>

```javascript
const users = [
  { name: "Alice", age: 25, premium: true },
  { name: "Bob", age: 17, premium: false },
  { name: "Charlie", age: 30, premium: true },
  { name: "David", age: 22, premium: false }
];

// 1. Premium users
const premiumUsers = users.filter(user => user.premium);
console.log("Premium users:", premiumUsers);

// 2. Adult users
const adults = users.filter(user => user.age >= 18);
console.log("Adults:", adults);

// 3. Just names
const names = users.map(user => user.name);
console.log("Names:", names);

// 4. Average age
const totalAge = users.reduce((sum, user) => sum + user.age, 0);
const averageAge = totalAge / users.length;
console.log("Average age:", averageAge);  // 23.5

// 5. Check if Bob exists
const hasBob = users.some(user => user.name === "Bob");
console.log("Has Bob:", hasBob);  // true
```

</details>

---

## 🎯 Array Method Cheat Sheet

| Method | Purpose | Returns | Changes Original? |
|--------|---------|---------|------------------|
| `push()` | Add to end | New length | Yes |
| `pop()` | Remove from end | Removed item | Yes |
| `unshift()` | Add to start | New length | Yes |
| `shift()` | Remove from start | Removed item | Yes |
| `map()` | Transform items | New array | No |
| `filter()` | Keep matching items | New array | No |
| `find()` | Find first match | One item | No |
| `reduce()` | Reduce to single value | Any value | No |
| `forEach()` | Loop through | undefined | No |
| `includes()` | Check if exists | Boolean | No |

---

## 🎯 Key Takeaways

1. **Arrays store lists** of values
2. **Index starts at 0** (first item is [0])
3. **`.map()`** transforms every item
4. **`.filter()`** keeps items that match
5. **`.reduce()`** combines into single value
6. **`.forEach()`** loops through items
7. **Chain methods** for powerful transformations
8. **Most methods don't modify original array** (they return new one)

---

## 🚀 Next Lesson

Now you can work with lists. Next, learn **objects** - structured data with key-value pairs!

**Next:** [Lesson 4: Objects →](./04-objects.md)

---

**Arrays are everywhere in programming. Master these methods, and you'll write cleaner, more powerful code.** 📋
