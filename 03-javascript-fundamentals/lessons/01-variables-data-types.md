# Lesson 1: Variables & Data Types

> **"Variables store data. Data types define what kind of data it is."**

---

## 🎯 What are Variables?

**Variables are containers that store data.**

Think of them like labeled boxes:
- **Box label** = Variable name
- **What's inside** = The value

```javascript
let age = 25;  // Box labeled "age" contains the number 25
let name = "Alice";  // Box labeled "name" contains the text "Alice"
```

---

## 📦 Three Ways to Declare Variables

### 1. `let` - Can change (MODERN - use this!)

```javascript
let score = 0;
score = 10;  // Change it
score = 20;  // Change it again
```

**Use when:** Value will change

---

### 2. `const` - Cannot change (MODERN - use this!)

```javascript
const PI = 3.14159;
PI = 3.14;  // ERROR! Can't change const
```

**Use when:** Value won't change (most of the time!)

---

### 3. `var` - Old way (DON'T USE)

```javascript
var oldWay = "Don't use this";
```

**Why not?** Has confusing scoping rules. Use `let` or `const` instead.

---

## ✅ let vs const - Which to Use?

**Rule of thumb:** Default to `const`, use `let` when you need to change it.

```javascript
const userName = "Alice";  // Won't change
let userScore = 0;         // Will change (as they play the game)

userScore = 100;  // OK
userName = "Bob";  // ERROR!
```

---

## 🎯 Naming Variables

### Rules (must follow):
- Start with letter, `$`, or `_` (not numbers!)
- Can contain letters, numbers, `$`, `_`
- Case-sensitive (`name` ≠ `Name`)
- No spaces (use camelCase)
- Can't use reserved words (`let`, `const`, `if`, etc.)

### Good names:
```javascript
let firstName = "John";
let userAge = 25;
let isLoggedIn = true;
let totalPrice = 99.99;
```

### Bad names:
```javascript
let 1name = "John";  // Starts with number - ERROR!
let first-name = "John";  // Has dash - ERROR!
let let = "value";  // Reserved word - ERROR!
let x = "John";  // Not descriptive
```

**Use camelCase:** `firstName`, `userAge`, `totalPrice`

---

## 🎨 Data Types

### 1. **String** - Text

```javascript
let name = "Alice";
let message = 'Hello, world!';
let greeting = `Hi, ${name}!`;  // Template literal

console.log(greeting);  // "Hi, Alice!"
```

**Three ways to write strings:**
- Double quotes: `"text"`
- Single quotes: `'text'`
- Backticks (template literals): `` `text ${variable}` ``

**Template literals** let you embed variables:
```javascript
let age = 25;
let bio = `I am ${age} years old`;  // "I am 25 years old"
```

---

### 2. **Number** - Integers and decimals

```javascript
let age = 25;
let price = 19.99;
let negative = -10;
```

**No quotes around numbers!**

---

### 3. **Boolean** - true or false

```javascript
let isLoggedIn = true;
let isAdmin = false;
```

Only two values: `true` or `false` (no quotes!)

---

### 4. **undefined** - No value assigned

```javascript
let something;
console.log(something);  // undefined
```

---

### 5. **null** - Intentionally empty

```javascript
let user = null;  // No user logged in
```

---

### 6. **Array** - List of values

```javascript
let fruits = ["apple", "banana", "orange"];
let numbers = [1, 2, 3, 4, 5];
let mixed = ["text", 42, true];
```

**Access items by index (starts at 0):**
```javascript
console.log(fruits[0]);  // "apple"
console.log(fruits[1]);  // "banana"
```

---

### 7. **Object** - Key-value pairs

```javascript
let person = {
  name: "Alice",
  age: 25,
  isStudent: true
};

console.log(person.name);  // "Alice"
console.log(person.age);   // 25
```

---

## 🎯 Checking Data Types

```javascript
typeof "Hello"     // "string"
typeof 42          // "number"
typeof true        // "boolean"
typeof undefined   // "undefined"
typeof null        // "object" (this is a JavaScript quirk!)
typeof []          // "object"
typeof {}          // "object"
```

---

## 🎨 Working Example

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Variables Demo</title>
</head>
<body>
  <h1>Variables & Data Types</h1>
  <p>Open the console (F12) to see the output!</p>

  <script>
    // Strings
    const firstName = "John";
    const lastName = "Doe";
    const fullName = `${firstName} ${lastName}`;
    console.log("Full Name:", fullName);

    // Numbers
    const age = 30;
    const price = 19.99;
    const total = price * 2;
    console.log("Total:", total);

    // Booleans
    const isStudent = true;
    const hasDiscount = age < 25;
    console.log("Has discount:", hasDiscount);

    // Arrays
    const colors = ["red", "green", "blue"];
    console.log("First color:", colors[0]);
    console.log("All colors:", colors);

    // Objects
    const user = {
      name: "Alice",
      age: 25,
      email: "alice@example.com"
    };
    console.log("User:", user);
    console.log("User name:", user.name);

    // Type checking
    console.log("Type of fullName:", typeof fullName);
    console.log("Type of age:", typeof age);
    console.log("Type of isStudent:", typeof isStudent);
  </script>
</body>
</html>
```

**Open this in your browser and press F12 to see the console!**

---

## 🔄 String Methods

```javascript
let text = "Hello, World!";

text.length           // 13 (number of characters)
text.toUpperCase()    // "HELLO, WORLD!"
text.toLowerCase()    // "hello, world!"
text.includes("World") // true
text.replace("World", "JavaScript")  // "Hello, JavaScript!"
text.slice(0, 5)      // "Hello"
```

---

## 🔢 Number Methods

```javascript
let num = 3.14159;

num.toFixed(2)        // "3.14" (2 decimal places)
parseInt("42")        // 42 (string to integer)
parseFloat("3.14")    // 3.14 (string to decimal)
Math.round(3.7)       // 4
Math.floor(3.7)       // 3
Math.ceil(3.1)        // 4
Math.random()         // Random number between 0 and 1
```

---

## ✏️ Practice Exercise

Open your browser console (F12 → Console tab) and try:

1. Create a `const` variable with your name
2. Create a `let` variable with your age
3. Create a template literal that says "I am [name] and I am [age] years old"
4. Create an array of 3 favorite foods
5. Create an object representing a book (title, author, pages)

<details>
<summary>Solution</summary>

```javascript
// 1. Name
const myName = "Alice";

// 2. Age
let myAge = 25;

// 3. Template literal
const bio = `I am ${myName} and I am ${myAge} years old`;
console.log(bio);

// 4. Array
const favoriteFoods = ["pizza", "sushi", "tacos"];
console.log(favoriteFoods);

// 5. Object
const book = {
  title: "The Great Gatsby",
  author: "F. Scott Fitzgerald",
  pages: 180
};
console.log(book);
```

</details>

---

## 🎯 Key Takeaways

1. **`let`** for values that change, **`const`** for values that don't
2. **Don't use `var`** (old way)
3. **camelCase** for variable names
4. **Seven data types:** String, Number, Boolean, undefined, null, Array, Object
5. **Template literals** (backticks) let you embed variables: `` `Hello ${name}` ``
6. **Arrays** use brackets: `[]`
7. **Objects** use braces: `{}`

---

## 🚀 Next Lesson

Now you can store data. Next, learn **functions** - reusable blocks of code!

**Next:** [Lesson 2: Functions →](./02-functions.md)

---

**Variables are the foundation of programming. Master these, and you're ready for anything.** 📦
