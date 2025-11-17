# Lesson 5: Loops & Conditionals

> **"Loops repeat code. Conditionals make decisions. Together, they make programs smart."**

---

## 🔀 PART 1: CONDITIONALS

### What are Conditionals?

**Conditionals let your code make decisions.**

Think of them like **traffic lights**:
- **IF** light is green → GO
- **ELSE IF** light is yellow → SLOW DOWN
- **ELSE** → STOP

---

## 🎯 if Statement

```javascript
const age = 18;

if (age >= 18) {
  console.log("You can vote!");
}
```

---

## 🎯 if...else

```javascript
const age = 16;

if (age >= 18) {
  console.log("You can vote!");
} else {
  console.log("Too young to vote.");
}
```

---

## 🎯 if...else if...else

```javascript
const score = 85;

if (score >= 90) {
  console.log("Grade: A");
} else if (score >= 80) {
  console.log("Grade: B");
} else if (score >= 70) {
  console.log("Grade: C");
} else if (score >= 60) {
  console.log("Grade: D");
} else {
  console.log("Grade: F");
}
// "Grade: B"
```

---

## 🎯 Comparison Operators

| Operator | Meaning | Example |
|----------|---------|---------|
| `===` | Equal (strict) | `5 === 5` → true |
| `!==` | Not equal | `5 !== 3` → true |
| `>` | Greater than | `5 > 3` → true |
| `<` | Less than | `3 < 5` → true |
| `>=` | Greater or equal | `5 >= 5` → true |
| `<=` | Less or equal | `3 <= 5` → true |

**Always use `===` not `==`!**

```javascript
5 === "5"  // false (different types)
5 == "5"   // true (converts types - confusing!)
```

---

## 🎯 Logical Operators

### AND (`&&`) - Both must be true

```javascript
const age = 25;
const hasLicense = true;

if (age >= 18 && hasLicense) {
  console.log("You can drive!");
}
```

### OR (`||`) - At least one must be true

```javascript
const isWeekend = true;
const isHoliday = false;

if (isWeekend || isHoliday) {
  console.log("No work today!");
}
```

### NOT (`!`) - Flips the value

```javascript
const isRaining = false;

if (!isRaining) {
  console.log("Let's go outside!");
}
```

---

## 🎯 Ternary Operator (Shorthand)

```javascript
// Long way
let message;
if (age >= 18) {
  message = "Adult";
} else {
  message = "Minor";
}

// Short way (ternary)
const message = age >= 18 ? "Adult" : "Minor";
```

**Syntax:** `condition ? valueIfTrue : valueIfFalse`

---

## 🔁 PART 2: LOOPS

### What are Loops?

**Loops repeat code multiple times.**

Instead of:
```javascript
console.log(1);
console.log(2);
console.log(3);
console.log(4);
console.log(5);
```

Use a loop:
```javascript
for (let i = 1; i <= 5; i++) {
  console.log(i);
}
```

---

## 🔄 for Loop

**Use when you know HOW MANY times to loop:**

```javascript
for (let i = 0; i < 5; i++) {
  console.log(i);
}
// 0, 1, 2, 3, 4
```

**Parts:**
1. `let i = 0` - Start
2. `i < 5` - Condition (keep going while true)
3. `i++` - After each loop (increment)

**Loop through array:**
```javascript
const fruits = ["apple", "banana", "orange"];

for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}
```

---

## 🔄 while Loop

**Use when you DON'T know how many times:**

```javascript
let count = 0;

while (count < 5) {
  console.log(count);
  count++;
}
// 0, 1, 2, 3, 4
```

**Real example:**
```javascript
let password = "";

while (password !== "secret") {
  password = prompt("Enter password:");
}

console.log("Access granted!");
```

---

## 🔄 do...while Loop

**Runs at LEAST ONCE (checks condition after):**

```javascript
let i = 0;

do {
  console.log(i);
  i++;
} while (i < 5);
```

---

## 🔄 for...of Loop (Arrays)

**Modern way to loop through arrays:**

```javascript
const fruits = ["apple", "banana", "orange"];

for (const fruit of fruits) {
  console.log(fruit);
}
// apple
// banana
// orange
```

---

## 🔄 for...in Loop (Objects)

**Loop through object properties:**

```javascript
const user = {
  name: "Alice",
  age: 25,
  email: "alice@example.com"
};

for (const key in user) {
  console.log(`${key}: ${user[key]}`);
}
// name: Alice
// age: 25
// email: alice@example.com
```

---

## 🎯 break and continue

### break - Exit loop early

```javascript
for (let i = 0; i < 10; i++) {
  if (i === 5) {
    break;  // Stop loop
  }
  console.log(i);
}
// 0, 1, 2, 3, 4 (stops at 5)
```

### continue - Skip to next iteration

```javascript
for (let i = 0; i < 5; i++) {
  if (i === 2) {
    continue;  // Skip 2
  }
  console.log(i);
}
// 0, 1, 3, 4 (skips 2)
```

---

## 🎨 Real-World Examples

### Example 1: Find in Array

```javascript
const users = ["Alice", "Bob", "Charlie", "David"];
const searchName = "Charlie";
let found = false;

for (const user of users) {
  if (user === searchName) {
    found = true;
    break;
  }
}

console.log(found ? "User found!" : "User not found");
```

### Example 2: Sum Numbers

```javascript
const numbers = [1, 2, 3, 4, 5];
let sum = 0;

for (const num of numbers) {
  sum += num;
}

console.log(`Total: ${sum}`);  // 15
```

### Example 3: Filter Even Numbers

```javascript
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const evenNumbers = [];

for (const num of numbers) {
  if (num % 2 === 0) {
    evenNumbers.push(num);
  }
}

console.log(evenNumbers);  // [2, 4, 6, 8, 10]
```

---

## 🎨 Complete Working Example

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Loops & Conditionals Demo</title>
</head>
<body>
  <h1>Loops & Conditionals</h1>
  <div id="output"></div>

  <script>
    const output = document.getElementById('output');

    // Example 1: Grade calculator
    function calculateGrade(score) {
      if (score >= 90) return "A";
      if (score >= 80) return "B";
      if (score >= 70) return "C";
      if (score >= 60) return "D";
      return "F";
    }

    const scores = [95, 82, 74, 58, 91];
    let html = "<h2>Grades:</h2>";

    for (let i = 0; i < scores.length; i++) {
      const grade = calculateGrade(scores[i]);
      html += `<p>Score ${scores[i]}: Grade ${grade}</p>`;
    }

    // Example 2: Filter products
    const products = [
      { name: "Laptop", price: 999, inStock: true },
      { name: "Mouse", price: 29, inStock: true },
      { name: "Keyboard", price: 79, inStock: false },
      { name: "Monitor", price: 299, inStock: true }
    ];

    html += "<h2>Available Products:</h2>";

    for (const product of products) {
      if (product.inStock) {
        html += `<p>${product.name} - $${product.price}</p>`;
      }
    }

    // Example 3: Countdown
    html += "<h2>Countdown:</h2>";
    for (let i = 5; i >= 1; i--) {
      html += `<p>${i}...</p>`;
    }
    html += "<p>Blast off! 🚀</p>";

    output.innerHTML = html;
  </script>
</body>
</html>
```

---

## ✏️ Practice Exercise

Write code to:

1. Check if a number is positive, negative, or zero
2. Loop through numbers 1-20 and print only multiples of 3
3. Find the largest number in an array
4. Count how many times "apple" appears in an array
5. Create a simple password checker (at least 8 characters)

<details>
<summary>Solution</summary>

```javascript
// 1. Positive, negative, or zero
function checkNumber(num) {
  if (num > 0) {
    return "Positive";
  } else if (num < 0) {
    return "Negative";
  } else {
    return "Zero";
  }
}

console.log(checkNumber(5));   // "Positive"
console.log(checkNumber(-3));  // "Negative"
console.log(checkNumber(0));   // "Zero"

// 2. Multiples of 3
for (let i = 1; i <= 20; i++) {
  if (i % 3 === 0) {
    console.log(i);
  }
}
// 3, 6, 9, 12, 15, 18

// 3. Largest number
const numbers = [45, 12, 98, 23, 67];
let largest = numbers[0];

for (const num of numbers) {
  if (num > largest) {
    largest = num;
  }
}

console.log(`Largest: ${largest}`);  // 98

// 4. Count "apple"
const fruits = ["apple", "banana", "apple", "orange", "apple"];
let appleCount = 0;

for (const fruit of fruits) {
  if (fruit === "apple") {
    appleCount++;
  }
}

console.log(`Apples: ${appleCount}`);  // 3

// 5. Password checker
function isValidPassword(password) {
  if (password.length >= 8) {
    return "Valid password";
  } else {
    return "Password must be at least 8 characters";
  }
}

console.log(isValidPassword("short"));      // Invalid
console.log(isValidPassword("longpassword")); // Valid
```

</details>

---

## 🎯 Which Loop to Use?

| Loop Type | When to Use |
|-----------|-------------|
| `for` | Know exact number of iterations |
| `while` | Don't know how many times |
| `do...while` | Need to run at least once |
| `for...of` | Loop through array items |
| `for...in` | Loop through object properties |

**Most common:** `for...of` for arrays, `for` when you need index

---

## 🎯 Key Takeaways

### Conditionals:
1. **`if/else`** for decisions
2. **`===`** not `==` for comparison
3. **`&&`** = AND, **`||`** = OR, **`!`** = NOT
4. **Ternary** `? :` for simple conditions

### Loops:
1. **`for`** when you know how many times
2. **`while`** when you don't know
3. **`for...of`** for arrays (modern)
4. **`for...in`** for objects
5. **`break`** exits loop, **`continue`** skips iteration

---

## 🚀 Next Lesson

You now have all the JavaScript fundamentals! Next, learn **DOM Manipulation** - making webpages interactive!

**Next:** [Module 04: DOM Manipulation →](../../04-dom-manipulation/README.md)

Or jump to **React** to learn modern component-based development!

---

**Loops and conditionals make programs smart. Master these, and you can build logic for anything.** 🔁
