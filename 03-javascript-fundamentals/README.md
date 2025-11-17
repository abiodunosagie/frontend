# 03 - JavaScript Fundamentals

> **"JavaScript is the programming language of the web. Without it, websites are just static documents."**

You've learned HTML (structure) and CSS (styling). Now it's time to add **interactivity and logic**.

---

## 🎯 What is JavaScript?

**JavaScript makes websites interactive:**
- Click a button → something happens
- Fill out a form → it validates your input
- Scroll down → new content loads
- Type in a search box → results appear

**Every interactive website uses JavaScript.**

---

## 📚 What You'll Learn

### Week 1: Basics
1. **Variables** - Storing data (`let`, `const`, `var`)
2. **Data Types** - Strings, numbers, booleans, arrays, objects
3. **Operators** - Math, comparison, logical
4. **Functions** - Reusable code blocks
5. **Conditionals** - If/else statements

### Week 2: Intermediate
6. **Loops** - For, while, forEach
7. **Arrays** - map, filter, reduce
8. **Objects** - Working with data
9. **Arrow Functions** - Modern syntax
10. **Destructuring** - Clean code patterns

### Week 3: Modern JavaScript
11. **Template Literals** - String interpolation
12. **Spread Operator** - `...` syntax
13. **Modules** - Import/export
14. **Promises** - Async basics
15. **Async/Await** - Modern async

---

## 🎯 Quick Example

```javascript
// Variables
let name = "Alice";
const age = 25;

// Function
function greet(person) {
  return `Hello, ${person}!`;
}

// Calling the function
console.log(greet(name)); // "Hello, Alice!"

// Array methods
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map(n => n * 2);
console.log(doubled); // [2, 4, 6, 8, 10]
```

---

## 🔥 Key Concepts

### 1. **Variables (Storage)**
```javascript
let score = 0;        // Can change
const name = "Alice"; // Can't change
```

### 2. **Functions (Reusable Code)**
```javascript
function add(a, b) {
  return a + b;
}

const result = add(5, 3); // 8
```

### 3. **Arrays (Lists)**
```javascript
const fruits = ["apple", "banana", "orange"];
console.log(fruits[0]); // "apple"
```

### 4. **Objects (Data Structures)**
```javascript
const person = {
  name: "Alice",
  age: 25,
  job: "Developer"
};

console.log(person.name); // "Alice"
```

### 5. **Conditionals (Logic)**
```javascript
if (age >= 18) {
  console.log("Adult");
} else {
  console.log("Minor");
}
```

---

## 🎨 Projects You'll Build

1. **Calculator** - Basic math operations
2. **Todo List** - Add, remove, complete tasks
3. **Quiz App** - Multiple choice questions
4. **Number Guessing Game** - Random number game
5. **Form Validator** - Check user input

---

**JavaScript turns static pages into interactive experiences. Let's master it.** 🚀
