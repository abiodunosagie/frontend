# 15 - API Integration in React & Next.js

> **"This is where everything comes together. Real apps with real data."**

You've learned HTML, CSS, JavaScript, React, Next.js, and APIs separately. Now we're going to **combine them all** to build production-ready applications.

---

## 🎯 What You'll Build

By the end of this module, you'll build:

1. **Weather App** - Real-time weather data with geolocation
2. **Movie Search** - Search and display movies from TMDB API
3. **GitHub Profile Viewer** - Display any GitHub user's repos and stats
4. **Full CRUD App** - Create, Read, Update, Delete with a real backend
5. **Authenticated App** - Login, protected routes, JWT tokens

**These are portfolio-worthy projects.** 🚀

---

## 📚 Lessons (Do in Order!)

### Week 1: API Integration Patterns
1. **[Fetching in React](./lessons/01-fetching-in-react.md)** - useEffect + fetch
2. **[Loading & Error States](./lessons/02-loading-error-states.md)** - Professional UX
3. **[Custom Hooks for APIs](./lessons/03-custom-hooks.md)** - Reusable fetch logic
4. **[Environment Variables](./lessons/04-environment-variables.md)** - Hiding API keys

### Week 2: Next.js API Integration
5. **[Server Components vs Client Components](./lessons/05-server-client.md)**
6. **[Data Fetching in Next.js](./lessons/06-nextjs-data-fetching.md)** - Server-side rendering
7. **[API Routes in Next.js](./lessons/07-api-routes.md)** - Build your own API endpoints
8. **[Server Actions](./lessons/08-server-actions.md)** - Modern Next.js pattern

### Week 3: Advanced Patterns
9. **[Caching Strategies](./lessons/09-caching.md)** - Avoid unnecessary requests
10. **[Optimistic Updates](./lessons/10-optimistic-updates.md)** - Instant UI feedback
11. **[Pagination](./lessons/11-pagination.md)** - Handle large datasets
12. **[Search & Filtering](./lessons/12-search-filtering.md)** - Interactive data display

### Week 4: Authentication & Security
13. **[API Authentication](./lessons/13-authentication.md)** - JWT, OAuth, API keys
14. **[Protected Routes](./lessons/14-protected-routes.md)** - Private pages
15. **[CORS & Security](./lessons/15-cors-security.md)** - Understanding security

---

## 🎯 Core Pattern: Fetching Data in React

### The Standard Pattern:

```javascript
import { useState, useEffect } from 'react';

function UserProfile({ userId }) {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    async function fetchUser() {
      try {
        setLoading(true);
        const response = await fetch(`https://api.example.com/users/${userId}`);

        if (!response.ok) {
          throw new Error('User not found');
        }

        const data = await response.json();
        setUser(data);
      } catch (err) {
        setError(err.message);
      } finally {
        setLoading(false);
      }
    }

    fetchUser();
  }, [userId]);  // Re-fetch when userId changes

  if (loading) return <div>Loading...</div>;
  if (error) return <div>Error: {error}</div>;
  if (!user) return null;

  return (
    <div>
      <h1>{user.name}</h1>
      <p>{user.email}</p>
    </div>
  );
}
```

### Let's Break It Down:

#### 1. **State Management**
```javascript
const [user, setUser] = useState(null);        // The data
const [loading, setLoading] = useState(true);  // Loading state
const [error, setError] = useState(null);      // Error state
```

**Three states every API call needs:**
- `data` - The actual data from the API
- `loading` - Are we currently fetching?
- `error` - Did something go wrong?

#### 2. **useEffect for Data Fetching**
```javascript
useEffect(() => {
  // Fetch data here
}, [userId]);  // Dependency array
```

**Why useEffect?**
- Runs after component mounts
- Runs again when dependencies change
- Perfect for API calls

#### 3. **Try/Catch/Finally**
```javascript
try {
  // Try to fetch
} catch (err) {
  // Handle errors
} finally {
  // Always runs (good for hiding loaders)
}
```

#### 4. **Conditional Rendering**
```javascript
if (loading) return <div>Loading...</div>;
if (error) return <div>Error: {error}</div>;
if (!user) return null;
```

**Always handle all three states!**

---

## 🎨 Real Example: Weather App

### Complete Working Example:

```javascript
'use client';  // Client component in Next.js

import { useState } from 'react';

export default function WeatherApp() {
  const [city, setCity] = useState('');
  const [weather, setWeather] = useState(null);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);

  async function getWeather(e) {
    e.preventDefault();

    if (!city.trim()) {
      setError('Please enter a city name');
      return;
    }

    try {
      setLoading(true);
      setError(null);

      const API_KEY = process.env.NEXT_PUBLIC_WEATHER_API_KEY;
      const response = await fetch(
        `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${API_KEY}&units=metric`
      );

      if (!response.ok) {
        throw new Error('City not found');
      }

      const data = await response.json();
      setWeather(data);
    } catch (err) {
      setError(err.message);
      setWeather(null);
    } finally {
      setLoading(false);
    }
  }

  return (
    <div className="max-w-md mx-auto p-6">
      <h1 className="text-3xl font-bold mb-6">Weather App</h1>

      <form onSubmit={getWeather} className="mb-6">
        <input
          type="text"
          value={city}
          onChange={(e) => setCity(e.target.value)}
          placeholder="Enter city name"
          className="w-full p-3 border rounded"
        />
        <button
          type="submit"
          disabled={loading}
          className="w-full mt-2 p-3 bg-blue-500 text-white rounded hover:bg-blue-600 disabled:bg-gray-400"
        >
          {loading ? 'Loading...' : 'Get Weather'}
        </button>
      </form>

      {error && (
        <div className="p-4 bg-red-100 text-red-700 rounded">
          {error}
        </div>
      )}

      {weather && (
        <div className="p-6 bg-white shadow-lg rounded">
          <h2 className="text-2xl font-bold">{weather.name}</h2>
          <p className="text-5xl my-4">{Math.round(weather.main.temp)}°C</p>
          <p className="text-xl capitalize">{weather.weather[0].description}</p>
          <div className="mt-4 grid grid-cols-2 gap-4">
            <div>
              <p className="text-gray-600">Feels Like</p>
              <p className="text-xl">{Math.round(weather.main.feels_like)}°C</p>
            </div>
            <div>
              <p className="text-gray-600">Humidity</p>
              <p className="text-xl">{weather.main.humidity}%</p>
            </div>
          </div>
        </div>
      )}
    </div>
  );
}
```

**This is a complete, production-ready component!**

---

## 🔧 Creating a Custom Hook (Reusable API Logic)

Instead of repeating fetch logic, create a reusable hook:

### `useFetch.js`:

```javascript
import { useState, useEffect } from 'react';

export function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    async function fetchData() {
      try {
        setLoading(true);
        const response = await fetch(url);

        if (!response.ok) {
          throw new Error(`HTTP error! Status: ${response.status}`);
        }

        const json = await response.json();
        setData(json);
      } catch (err) {
        setError(err.message);
      } finally {
        setLoading(false);
      }
    }

    if (url) {
      fetchData();
    }
  }, [url]);

  return { data, loading, error };
}
```

### Using the Custom Hook:

```javascript
function UserProfile({ userId }) {
  const { data: user, loading, error } = useFetch(
    `https://api.example.com/users/${userId}`
  );

  if (loading) return <div>Loading...</div>;
  if (error) return <div>Error: {error}</div>;

  return (
    <div>
      <h1>{user.name}</h1>
      <p>{user.email}</p>
    </div>
  );
}
```

**Much cleaner!** One hook, reuse everywhere.

---

## 🎯 Next.js Server Components (Modern Approach)

In Next.js 13+, you can fetch data on the server:

```javascript
// app/users/page.js (Server Component by default)

async function getUsers() {
  const response = await fetch('https://api.example.com/users', {
    cache: 'no-store'  // Always get fresh data
  });

  if (!response.ok) {
    throw new Error('Failed to fetch users');
  }

  return response.json();
}

export default async function UsersPage() {
  const users = await getUsers();

  return (
    <div>
      <h1>Users</h1>
      {users.map(user => (
        <div key={user.id}>
          <h2>{user.name}</h2>
          <p>{user.email}</p>
        </div>
      ))}
    </div>
  );
}
```

**Benefits:**
- Fetches on the server (faster initial load)
- No loading state needed (data is ready before render)
- SEO-friendly (search engines see the data)

---

## 🔐 Environment Variables (Hiding API Keys)

**Never commit API keys to GitHub!**

### In Next.js:

Create `.env.local`:

```env
NEXT_PUBLIC_WEATHER_API_KEY=your_api_key_here
NEXT_PUBLIC_TMDB_API_KEY=another_api_key
```

**Rules:**
- `NEXT_PUBLIC_` prefix → Accessible in browser
- No prefix → Only on server

### In React (Create React App):

Create `.env`:

```env
REACT_APP_API_KEY=your_api_key_here
```

**Must start with `REACT_APP_`**

### Using in Code:

```javascript
const apiKey = process.env.NEXT_PUBLIC_WEATHER_API_KEY;
```

### Add to `.gitignore`:

```
.env.local
.env
```

---

## 🎯 Full CRUD Example (Todo App with API)

### Component:

```javascript
'use client';

import { useState, useEffect } from 'react';

export default function TodoApp() {
  const [todos, setTodos] = useState([]);
  const [newTodo, setNewTodo] = useState('');
  const [loading, setLoading] = useState(true);

  // Fetch todos on mount
  useEffect(() => {
    fetchTodos();
  }, []);

  async function fetchTodos() {
    try {
      const response = await fetch('https://jsonplaceholder.typicode.com/todos?_limit=5');
      const data = await response.json();
      setTodos(data);
    } catch (error) {
      console.error('Error fetching todos:', error);
    } finally {
      setLoading(false);
    }
  }

  // CREATE
  async function addTodo(e) {
    e.preventDefault();
    if (!newTodo.trim()) return;

    try {
      const response = await fetch('https://jsonplaceholder.typicode.com/todos', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({
          title: newTodo,
          completed: false,
          userId: 1
        })
      });

      const todo = await response.json();

      // Add to local state (optimistic update)
      setTodos([...todos, todo]);
      setNewTodo('');
    } catch (error) {
      console.error('Error adding todo:', error);
    }
  }

  // UPDATE (Toggle complete)
  async function toggleTodo(id) {
    const todo = todos.find(t => t.id === id);

    try {
      const response = await fetch(`https://jsonplaceholder.typicode.com/todos/${id}`, {
        method: 'PATCH',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({
          completed: !todo.completed
        })
      });

      const updatedTodo = await response.json();

      // Update local state
      setTodos(todos.map(t => t.id === id ? updatedTodo : t));
    } catch (error) {
      console.error('Error updating todo:', error);
    }
  }

  // DELETE
  async function deleteTodo(id) {
    try {
      await fetch(`https://jsonplaceholder.typicode.com/todos/${id}`, {
        method: 'DELETE'
      });

      // Remove from local state
      setTodos(todos.filter(t => t.id !== id));
    } catch (error) {
      console.error('Error deleting todo:', error);
    }
  }

  if (loading) return <div>Loading...</div>;

  return (
    <div className="max-w-md mx-auto p-6">
      <h1 className="text-3xl font-bold mb-6">Todo App</h1>

      <form onSubmit={addTodo} className="mb-6">
        <input
          type="text"
          value={newTodo}
          onChange={(e) => setNewTodo(e.target.value)}
          placeholder="Add a new todo"
          className="w-full p-3 border rounded"
        />
        <button
          type="submit"
          className="w-full mt-2 p-3 bg-blue-500 text-white rounded hover:bg-blue-600"
        >
          Add Todo
        </button>
      </form>

      <div className="space-y-2">
        {todos.map(todo => (
          <div
            key={todo.id}
            className="flex items-center justify-between p-3 bg-white border rounded"
          >
            <div className="flex items-center gap-3">
              <input
                type="checkbox"
                checked={todo.completed}
                onChange={() => toggleTodo(todo.id)}
              />
              <span className={todo.completed ? 'line-through text-gray-500' : ''}>
                {todo.title}
              </span>
            </div>
            <button
              onClick={() => deleteTodo(todo.id)}
              className="text-red-500 hover:text-red-700"
            >
              Delete
            </button>
          </div>
        ))}
      </div>
    </div>
  );
}
```

**This demonstrates all CRUD operations!**

---

## 🎯 Key Takeaways

1. **Always handle three states:** data, loading, error
2. **Use useEffect for data fetching** in client components
3. **Use Server Components in Next.js** when possible (better performance)
4. **Create custom hooks** for reusable fetch logic
5. **Hide API keys** in environment variables
6. **Implement all CRUD operations:** Create, Read, Update, Delete

---

## 🚀 Projects to Build

Now build these on your own:

1. **Weather Dashboard** - Multiple cities, 5-day forecast
2. **Movie Database** - Search, filter, details page
3. **GitHub Explorer** - User search, repo list, stats
4. **Blog with CMS** - Full CRUD, markdown support
5. **E-commerce Product List** - Fetch products, add to cart

---

**You're now building real applications with real data. This is professional-level development.** 🎉
