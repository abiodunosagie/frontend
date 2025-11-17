# 13 - Fetch API & Async JavaScript

> **"Understanding async/await is the key to working with APIs professionally."**

Welcome to one of the most important concepts in modern JavaScript: **asynchronous programming**.

This is where beginners often get confused. Not anymore. We're going to make this crystal clear.

---

## 🎯 What You'll Master

By the end of this module, you'll:
- **Understand** what "asynchronous" means (and why it matters)
- **Use** the Fetch API confidently
- **Write** async/await code (the modern way)
- **Handle** loading states and errors
- **Make** GET and POST requests
- **Debug** async code effectively

---

## 🤔 The Problem: Why We Need Async

### Imagine This Scenario:

You're making breakfast:

**Synchronous (blocking) approach:**
1. Put bread in toaster → **Wait 2 minutes** ⏳
2. After toast is done, brew coffee → **Wait 5 minutes** ⏳
3. After coffee is done, cook eggs → **Wait 3 minutes** ⏳

**Total time: 10 minutes** (one thing at a time)

**Asynchronous (non-blocking) approach:**
1. Put bread in toaster (set it and forget it)
2. Start brewing coffee (while toast is toasting)
3. Start cooking eggs (while coffee is brewing)
4. Everything finishes around the same time

**Total time: ~5 minutes** (multiple things at once)

---

## 💻 How This Applies to Code

When you request data from an API:

**Synchronous (BAD):**
```javascript
const data = getDataFromAPI();  // ⏳ FREEZE for 2 seconds
console.log(data);  // Finally runs after 2 seconds
```

**Problem:** Your entire app freezes while waiting. Users can't click anything, scroll, or interact.

**Asynchronous (GOOD):**
```javascript
getDataFromAPI().then(data => {
  console.log(data);  // Runs when data arrives
});

console.log("This runs immediately!");  // Doesn't wait
```

**Result:** App stays responsive. Data loads in the background.

---

## 📚 Lessons (Do in Order!)

### Week 1: Understanding Async
1. **[Synchronous vs Asynchronous](./lessons/01-sync-vs-async.md)**
2. **[Promises Explained](./lessons/02-promises.md)** - The foundation
3. **[Async/Await](./lessons/03-async-await.md)** - The modern syntax

### Week 2: Fetch API Mastery
4. **[Fetch API Basics](./lessons/04-fetch-basics.md)** - GET requests
5. **[Fetch POST Requests](./lessons/05-fetch-post.md)** - Sending data
6. **[Headers & Options](./lessons/06-headers-options.md)** - Configuring requests
7. **[Error Handling](./lessons/07-error-handling.md)** - Network errors, HTTP errors

### Week 3: Real-World Patterns
8. **[Loading States](./lessons/08-loading-states.md)** - Show spinners while loading
9. **[Abort Controllers](./lessons/09-abort-controllers.md)** - Cancel requests
10. **[API Wrapper Functions](./lessons/10-api-wrappers.md)** - Reusable code

---

## 🎯 Core Concept: Promises

### What is a Promise?

A **Promise** is an object representing a value that will be available in the future.

**Real-life analogy:**
When you order food online:
1. You place the order (**Promise created**)
2. Food is being prepared (**Promise pending**)
3. **Either:**
   - Food arrives (**Promise fulfilled** ✅)
   - Order is canceled (**Promise rejected** ❌)

### The Three States:

```javascript
const promise = fetch('https://api.example.com/data');

// State 1: PENDING (request in progress)
// ⏳ Waiting for response...

// State 2: FULFILLED (success)
// ✅ Got the data!

// State 3: REJECTED (error)
// ❌ Network error / Server error
```

---

## 🔧 Two Ways to Handle Promises

### Method 1: `.then()` (Old Way)

```javascript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => {
    console.log(data);  // Use the data
  })
  .catch(error => {
    console.error('Error:', error);
  });
```

**Problems:**
- Can get messy with multiple API calls (callback hell)
- Hard to read

### Method 2: `async/await` (Modern Way) ⭐

```javascript
async function getData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    console.log(data);  // Use the data
  } catch (error) {
    console.error('Error:', error);
  }
}

getData();
```

**Benefits:**
- Looks like synchronous code (easier to read)
- Easier to debug
- Industry standard

**We'll use async/await throughout this course.**

---

## 💡 Understanding `async` and `await`

### The `async` Keyword

```javascript
async function myFunction() {
  // This function now returns a Promise
}
```

**What it does:**
- Marks a function as asynchronous
- Automatically wraps the return value in a Promise

### The `await` Keyword

```javascript
const data = await fetch('https://api.example.com/data');
```

**What it does:**
- **Pauses** the function until the Promise resolves
- Only works inside `async` functions
- Makes async code look synchronous

---

## 🎯 Your First Fetch Request (Step by Step)

### Example: Get a Random User

```javascript
async function getRandomUser() {
  // 1. Make the request
  const response = await fetch('https://randomuser.me/api/');

  // 2. Convert response to JSON
  const data = await response.json();

  // 3. Use the data
  console.log(data.results[0]);
}

getRandomUser();
```

### Let's Break It Down:

#### Step 1: Make the Request
```javascript
const response = await fetch('https://randomuser.me/api/');
```
- `fetch()` returns a Promise
- `await` pauses until the Promise resolves
- `response` contains the HTTP response (not the data yet!)

#### Step 2: Parse the JSON
```javascript
const data = await response.json();
```
- `response.json()` also returns a Promise
- It converts the response body to a JavaScript object
- `await` waits for the conversion to finish

#### Step 3: Use the Data
```javascript
console.log(data.results[0]);
```
- Now `data` is a regular JavaScript object
- Access properties like any object

---

## 🎨 Real Example: Display User Info

Create `fetch-demo.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Fetch API Demo</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      max-width: 600px;
      margin: 50px auto;
      padding: 20px;
    }
    button {
      background: #007bff;
      color: white;
      border: none;
      padding: 10px 20px;
      font-size: 16px;
      border-radius: 5px;
      cursor: pointer;
    }
    button:hover {
      background: #0056b3;
    }
    .user-card {
      border: 1px solid #ddd;
      border-radius: 10px;
      padding: 20px;
      margin-top: 20px;
      display: none;
    }
    .user-card img {
      border-radius: 50%;
    }
    .loading {
      color: #666;
      font-style: italic;
    }
    .error {
      color: red;
    }
  </style>
</head>
<body>
  <h1>Random User Generator</h1>
  <button id="getUser">Get Random User</button>

  <div id="loading" class="loading" style="display: none;">
    Loading...
  </div>

  <div id="error" class="error" style="display: none;"></div>

  <div id="userCard" class="user-card"></div>

  <script>
    const button = document.getElementById('getUser');
    const loading = document.getElementById('loading');
    const errorDiv = document.getElementById('error');
    const userCard = document.getElementById('userCard');

    button.addEventListener('click', getRandomUser);

    async function getRandomUser() {
      try {
        // Show loading, hide error and previous user
        loading.style.display = 'block';
        errorDiv.style.display = 'none';
        userCard.style.display = 'none';

        // Make API call
        const response = await fetch('https://randomuser.me/api/');

        // Check if response is OK
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }

        // Parse JSON
        const data = await response.json();
        const user = data.results[0];

        // Hide loading
        loading.style.display = 'none';

        // Display user
        displayUser(user);

      } catch (error) {
        // Hide loading
        loading.style.display = 'none';

        // Show error
        errorDiv.style.display = 'block';
        errorDiv.textContent = `Error: ${error.message}`;
      }
    }

    function displayUser(user) {
      userCard.style.display = 'block';
      userCard.innerHTML = `
        <img src="${user.picture.large}" alt="${user.name.first}">
        <h2>${user.name.first} ${user.name.last}</h2>
        <p><strong>Email:</strong> ${user.email}</p>
        <p><strong>Location:</strong> ${user.location.city}, ${user.location.country}</p>
        <p><strong>Age:</strong> ${user.dob.age}</p>
      `;
    }
  </script>
</body>
</html>
```

**Open this file and click the button!**

---

## 🔍 Anatomy of a Complete Fetch Request

```javascript
async function fetchData() {
  try {
    // 1. SHOW LOADING STATE
    setLoading(true);

    // 2. MAKE REQUEST
    const response = await fetch('https://api.example.com/data', {
      method: 'GET',  // HTTP method (GET, POST, PUT, DELETE)
      headers: {
        'Content-Type': 'application/json',
        'Authorization': 'Bearer YOUR_API_KEY'  // If needed
      }
    });

    // 3. CHECK IF SUCCESSFUL
    if (!response.ok) {
      throw new Error(`HTTP error! Status: ${response.status}`);
    }

    // 4. PARSE RESPONSE
    const data = await response.json();

    // 5. HIDE LOADING
    setLoading(false);

    // 6. USE DATA
    console.log(data);

  } catch (error) {
    // 7. HANDLE ERRORS
    setLoading(false);
    console.error('Error:', error);
    showError(error.message);
  }
}
```

---

## 🎯 Making Different Types of Requests

### GET Request (Read Data)

```javascript
const response = await fetch('https://api.example.com/users');
const users = await response.json();
```

### POST Request (Create Data)

```javascript
const response = await fetch('https://api.example.com/users', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    name: 'John Doe',
    email: 'john@example.com'
  })
});

const newUser = await response.json();
```

### PUT Request (Update Data)

```javascript
const response = await fetch('https://api.example.com/users/123', {
  method: 'PUT',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    name: 'Jane Doe'
  })
});

const updatedUser = await response.json();
```

### DELETE Request (Delete Data)

```javascript
const response = await fetch('https://api.example.com/users/123', {
  method: 'DELETE'
});

// Usually DELETE returns no content
if (response.ok) {
  console.log('User deleted');
}
```

---

## ✏️ Practice Exercise

**Build a "Posts Viewer" using JSONPlaceholder API**

Requirements:
1. Button to fetch posts
2. Show loading state while fetching
3. Display list of posts (title and body)
4. Handle errors if API fails
5. Style it nicely

**API Endpoint:** `https://jsonplaceholder.typicode.com/posts`

**Bonus:**
- Add a button to create a new post (POST request)
- Add ability to delete a post (DELETE request)

---

## 🎯 Key Takeaways

1. **Asynchronous code doesn't block** (app stays responsive)
2. **Promises represent future values** (pending → fulfilled/rejected)
3. **`async/await` makes async code readable** (looks synchronous)
4. **Always use try/catch** (error handling is not optional)
5. **Show loading states** (better UX)
6. **Check `response.ok`** (API might return 404, 500, etc.)

---

## 🚀 Next Module

Now that you understand fetch and async, let's learn REST API architecture and integrate APIs into React apps.

**Next:** [14-rest-apis](../14-rest-apis/README.md)

---

## 💭 Self-Check

Before moving on:
1. Can you explain what asynchronous means?
2. Do you understand the three states of a Promise?
3. Can you write an async function with try/catch?
4. Do you know the difference between `response` and the actual data?

If yes to all → You're ready for API integration! 🎉
If no to any → Re-read and do the practice exercise.

---

**Async/await is your superpower. Every modern web app uses this. You just learned professional-level JavaScript.** 💪
