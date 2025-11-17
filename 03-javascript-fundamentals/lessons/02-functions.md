# Lesson 2: Functions

> **"Functions are reusable blocks of code. Write once, use everywhere."**

---

## 🎯 What are Functions?

**Functions are reusable pieces of code that perform a specific task.**

Think of a function like a **recipe**:
- **Name:** "Make Coffee"
- **Ingredients:** (parameters)
- **Instructions:** (code inside function)
- **Result:** (return value)

**Instead of writing the same code over and over, write a function once and call it whenever you need it!**

---

## 📝 Function Syntax

### Basic Function:

```javascript
function greet() {
  console.log("Hello!");
}

// Call the function
greet();  // "Hello!"
```

**Parts:**
- `function` = Keyword
- `greet` = Function name
- `()` = Parameters (none in this example)
- `{}` = Function body (code to run)

---

## 🎨 Functions with Parameters

**Parameters** are inputs to the function:

```javascript
function greet(name) {
  console.log(`Hello, ${name}!`);
}

greet("Alice");  // "Hello, Alice!"
greet("Bob");    // "Hello, Bob!"
```

**Multiple parameters:**

```javascript
function add(a, b) {
  console.log(a + b);
}

add(5, 3);   // 8
add(10, 20); // 30
```

---

## 🔄 Return Values

Functions can **return** a value:

```javascript
function add(a, b) {
  return a + b;
}

const result = add(5, 3);  // result = 8
console.log(result);       // 8
```

**Without `return`, function gives back `undefined`:**

```javascript
function sayHello() {
  console.log("Hello");
  // No return statement
}

const result = sayHello();  // Logs "Hello"
console.log(result);        // undefined
```

---

## ⚡ Arrow Functions (Modern Syntax)

**Shorter way to write functions:**

```javascript
// Traditional function
function add(a, b) {
  return a + b;
}

// Arrow function
const add = (a, b) => {
  return a + b;
};

// Even shorter (one-line)
const add = (a, b) => a + b;
```

**Examples:**

```javascript
// No parameters
const greet = () => console.log("Hello!");

// One parameter (parentheses optional)
const double = num => num * 2;

// Multiple parameters
const multiply = (a, b) => a * b;

// Multi-line
const calculateTotal = (price, tax) => {
  const total = price + (price * tax);
  return total;
};
```

---

## 🎯 Default Parameters

```javascript
function greet(name = "Guest") {
  console.log(`Hello, ${name}!`);
}

greet("Alice");  // "Hello, Alice!"
greet();         // "Hello, Guest!" (uses default)
```

---

## 🎨 Real-World Examples

### Example 1: Calculate Area

```javascript
function calculateRectangleArea(width, height) {
  return width * height;
}

const area = calculateRectangleArea(10, 5);
console.log(`Area: ${area}`);  // "Area: 50"
```

### Example 2: Check if Adult

```javascript
function isAdult(age) {
  return age >= 18;
}

console.log(isAdult(25));  // true
console.log(isAdult(15));  // false
```

### Example 3: Format Price

```javascript
function formatPrice(price) {
  return `$${price.toFixed(2)}`;
}

console.log(formatPrice(19.5));   // "$19.50"
console.log(formatPrice(99.999)); // "$100.00"
```

---

## 🎯 Function Scope

**Variables inside functions are local** (only exist inside that function):

```javascript
function myFunction() {
  const message = "Hello";  // Only exists inside this function
  console.log(message);     // Works
}

myFunction();
console.log(message);  // ERROR! message doesn't exist here
```

**Variables outside functions are global** (accessible everywhere):

```javascript
const globalMessage = "Hello";

function myFunction() {
  console.log(globalMessage);  // Works!
}

myFunction();
console.log(globalMessage);  // Also works!
```

---

## 🎨 Complete Working Example

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Functions Demo</title>
</head>
<body>
  <h1>Functions Demo</h1>
  <button onclick="sayHello()">Click Me</button>
  <p id="output"></p>

  <script>
    // Function that runs when button is clicked
    function sayHello() {
      const output = document.getElementById('output');
      output.textContent = "Hello from a function!";
    }

    // Function with parameters
    function greet(name) {
      return `Hello, ${name}!`;
    }

    // Arrow function
    const add = (a, b) => a + b;

    // Function that uses other functions
    function displayGreeting(userName) {
      const greeting = greet(userName);
      console.log(greeting);
    }

    // Call functions
    console.log(greet("Alice"));
    console.log(add(5, 3));
    displayGreeting("Bob");

    // Function to calculate discount
    function applyDiscount(price, discountPercent) {
      const discount = price * (discountPercent / 100);
      const finalPrice = price - discount;
      return finalPrice.toFixed(2);
    }

    console.log(`Price after 20% discount: $${applyDiscount(100, 20)}`);
    // "Price after 20% discount: $80.00"
  </script>
</body>
</html>
```

---

## 🎯 Common Patterns

### Pattern 1: Validate Input

```javascript
function isValidEmail(email) {
  return email.includes("@") && email.includes(".");
}

console.log(isValidEmail("user@example.com"));  // true
console.log(isValidEmail("invalid"));           // false
```

### Pattern 2: Toggle Boolean

```javascript
function toggle(value) {
  return !value;
}

let isVisible = true;
isVisible = toggle(isVisible);  // false
isVisible = toggle(isVisible);  // true
```

### Pattern 3: Get Random Number

```javascript
function getRandomNumber(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

console.log(getRandomNumber(1, 10));  // Random number between 1 and 10
```

---

## ✏️ Practice Exercise

Write these functions:

1. `greet(name)` - Returns "Hello, [name]!"
2. `square(num)` - Returns the square of a number
3. `isEven(num)` - Returns true if number is even, false if odd
4. `getFullName(firstName, lastName)` - Returns full name
5. `celsiusToFahrenheit(celsius)` - Converts celsius to fahrenheit

<details>
<summary>Solution</summary>

```javascript
// 1. Greet
function greet(name) {
  return `Hello, ${name}!`;
}
console.log(greet("Alice"));  // "Hello, Alice!"

// 2. Square
function square(num) {
  return num * num;
}
console.log(square(5));  // 25

// 3. Is even
function isEven(num) {
  return num % 2 === 0;
}
console.log(isEven(4));  // true
console.log(isEven(7));  // false

// 4. Get full name
function getFullName(firstName, lastName) {
  return `${firstName} ${lastName}`;
}
console.log(getFullName("John", "Doe"));  // "John Doe"

// 5. Celsius to Fahrenheit
function celsiusToFahrenheit(celsius) {
  return (celsius * 9/5) + 32;
}
console.log(celsiusToFahrenheit(0));   // 32
console.log(celsiusToFahrenheit(100)); // 212
```

**Arrow function versions:**

```javascript
const greet = name => `Hello, ${name}!`;
const square = num => num * num;
const isEven = num => num % 2 === 0;
const getFullName = (firstName, lastName) => `${firstName} ${lastName}`;
const celsiusToFahrenheit = celsius => (celsius * 9/5) + 32;
```

</details>

---

## 🎯 Key Takeaways

1. **Functions** are reusable blocks of code
2. **Parameters** are inputs, **return** is output
3. **Arrow functions** `=>` are shorter syntax (modern way)
4. **Default parameters** provide fallback values
5. **Variables inside functions are local** (scope)
6. **Name functions clearly** (verb + noun: `calculateTotal`, `isValid`)

---

## 🚀 Next Lesson

Now you can write reusable code. Next, learn **arrays** - storing and manipulating lists of data!

**Next:** [Lesson 3: Arrays & Array Methods →](./03-arrays.md)

---

**Functions are the building blocks of programs. Master them, and you can build anything.** 🔨
