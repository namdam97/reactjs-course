# 📝 Quick Reference - Cheat Sheet

> Tài liệu tham khảo nhanh các concepts quan trọng

---

## 🎨 CSS Quick Reference

### Flexbox Cheat Sheet

```css
/* Container */
.container {
    display: flex;
    
    /* Direction */
    flex-direction: row | column | row-reverse | column-reverse;
    
    /* Main axis alignment */
    justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly;
    
    /* Cross axis alignment */
    align-items: flex-start | flex-end | center | stretch | baseline;
    
    /* Wrap */
    flex-wrap: nowrap | wrap | wrap-reverse;
    
    /* Gap */
    gap: 1rem; /* or row-gap, column-gap */
}

/* Items */
.item {
    flex: 1; /* flex-grow: 1; flex-shrink: 1; flex-basis: 0; */
    align-self: auto | flex-start | flex-end | center | stretch;
}
```

### Grid Cheat Sheet

```css
.container {
    display: grid;
    
    /* Columns & Rows */
    grid-template-columns: 200px 1fr 2fr;
    grid-template-columns: repeat(3, 1fr);
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    
    grid-template-rows: 100px auto;
    
    /* Gap */
    gap: 1rem;
    column-gap: 1rem;
    row-gap: 2rem;
}

.item {
    /* Placement */
    grid-column: 1 / 3; /* start / end */
    grid-row: 1 / 2;
    
    /* Span */
    grid-column: span 2;
    grid-row: span 3;
}
```

### Responsive Design

```css
/* Mobile First Approach */

/* Base styles - Mobile */
.container {
    padding: 1rem;
}

/* Tablet */
@media (min-width: 768px) {
    .container {
        padding: 2rem;
    }
}

/* Desktop */
@media (min-width: 1024px) {
    .container {
        padding: 3rem;
        max-width: 1200px;
        margin: 0 auto;
    }
}

/* Common Breakpoints */
/* 
   Mobile: < 768px
   Tablet: 768px - 1024px
   Desktop: > 1024px
*/
```

---

## 💻 JavaScript Quick Reference

### Array Methods

```javascript
const numbers = [1, 2, 3, 4, 5];
const users = [
    { id: 1, name: "John", age: 25 },
    { id: 2, name: "Jane", age: 30 },
    { id: 3, name: "Bob", age: 20 }
];

// map - Transform array
const doubled = numbers.map(n => n * 2);
// [2, 4, 6, 8, 10]

const names = users.map(user => user.name);
// ["John", "Jane", "Bob"]

// filter - Filter array
const evens = numbers.filter(n => n % 2 === 0);
// [2, 4]

const adults = users.filter(user => user.age >= 25);
// [{ id: 1, name: "John", age: 25 }, { id: 2, name: "Jane", age: 30 }]

// reduce - Reduce to single value
const sum = numbers.reduce((acc, n) => acc + n, 0);
// 15

const totalAge = users.reduce((acc, user) => acc + user.age, 0);
// 75

// find - Find first match
const firstEven = numbers.find(n => n % 2 === 0);
// 2

const john = users.find(user => user.name === "John");
// { id: 1, name: "John", age: 25 }

// findIndex - Find index of first match
const index = numbers.findIndex(n => n === 3);
// 2

// some - Check if any matches
const hasEvens = numbers.some(n => n % 2 === 0);
// true

// every - Check if all match
const allPositive = numbers.every(n => n > 0);
// true

// forEach - Loop (no return value)
numbers.forEach(n => console.log(n));

// sort - Sort array (mutates original!)
const sorted = [...numbers].sort((a, b) => b - a);
// [5, 4, 3, 2, 1]

// includes - Check if includes value
numbers.includes(3); // true

// slice - Get portion (doesn't mutate)
const portion = numbers.slice(1, 3); // [2, 3]

// splice - Remove/add items (mutates!)
const removed = numbers.splice(1, 2); // removes index 1-2

// Chaining
const result = users
    .filter(user => user.age >= 25)
    .map(user => user.name)
    .sort();
// ["Jane", "John"]
```

### Object Methods

```javascript
const user = {
    id: 1,
    name: "John",
    age: 25,
    email: "john@example.com"
};

// Object.keys - Get keys as array
Object.keys(user);
// ["id", "name", "age", "email"]

// Object.values - Get values as array
Object.values(user);
// [1, "John", 25, "john@example.com"]

// Object.entries - Get [key, value] pairs
Object.entries(user);
// [["id", 1], ["name", "John"], ["age", 25], ["email", "john@example.com"]]

// Object.assign - Copy/merge objects
const updated = Object.assign({}, user, { age: 26 });

// Spread operator (preferred)
const updated = { ...user, age: 26 };

// Destructuring
const { name, age } = user;

// With rename
const { name: userName, age: userAge } = user;

// With default
const { role = "user" } = user;

// Rest
const { id, ...rest } = user;
// id = 1
// rest = { name: "John", age: 25, email: "john@example.com" }
```

### String Methods

```javascript
const str = "  Hello World  ";

str.trim();                    // "Hello World"
str.toLowerCase();             // "  hello world  "
str.toUpperCase();             // "  HELLO WORLD  "
str.includes("World");         // true
str.startsWith("  Hello");     // true
str.endsWith("World  ");       // true
str.replace("World", "JS");    // "  Hello JS  "
str.replaceAll("l", "L");      // "  HeLLo WorLd  "
str.split(" ");                // ["", "", "Hello", "World", "", ""]
str.slice(2, 7);               // "Hello"
str.charAt(2);                 // "H"

// Template literals
const name = "John";
const age = 25;
const message = `${name} is ${age} years old`;
```

### Async/Await

```javascript
// Promise
fetch('/api/users')
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error(error))
    .finally(() => console.log('Done'));

// async/await (preferred)
async function getUsers() {
    try {
        const response = await fetch('/api/users');
        const data = await response.json();
        return data;
    } catch (error) {
        console.error(error);
    } finally {
        console.log('Done');
    }
}

// Multiple async calls
async function getAllData() {
    // Sequential (slow)
    const users = await fetch('/api/users').then(r => r.json());
    const posts = await fetch('/api/posts').then(r => r.json());
    
    // Parallel (fast)
    const [users, posts] = await Promise.all([
        fetch('/api/users').then(r => r.json()),
        fetch('/api/posts').then(r => r.json())
    ]);
}

// Fetch with POST
async function createUser(userData) {
    const response = await fetch('/api/users', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
        },
        body: JSON.stringify(userData)
    });
    return response.json();
}
```

### DOM Manipulation

```javascript
// Select elements
const el = document.querySelector('#id');
const els = document.querySelectorAll('.class');

// Modify content
el.textContent = "Hello";
el.innerHTML = "<strong>Hello</strong>";

// Modify attributes
el.setAttribute('data-id', '123');
el.getAttribute('data-id');
el.removeAttribute('data-id');

// Modify classes
el.classList.add('active');
el.classList.remove('hidden');
el.classList.toggle('open');
el.classList.contains('active'); // true/false

// Modify styles
el.style.color = 'red';
el.style.backgroundColor = 'blue';

// Create & append
const div = document.createElement('div');
div.textContent = "Hello";
div.classList.add('box');
parent.appendChild(div);

// Remove
el.remove();

// Event listeners
button.addEventListener('click', (e) => {
    e.preventDefault();
    console.log('Clicked!');
});

// Event delegation
parent.addEventListener('click', (e) => {
    if (e.target.matches('.btn')) {
        console.log('Button clicked!');
    }
});
```

---

## ⚛️ React Quick Reference

### Component Basics

```jsx
// Function Component
function Greeting({ name }) {
    return <h1>Hello {name}!</h1>;
}

// Arrow Function Component (preferred)
const Greeting = ({ name }) => {
    return <h1>Hello {name}!</h1>;
};

// Shorthand (implicit return)
const Greeting = ({ name }) => <h1>Hello {name}!</h1>;

// Props destructuring
const UserCard = ({ name, age, email }) => {
    return (
        <div className="card">
            <h2>{name}</h2>
            <p>Age: {age}</p>
            <p>Email: {email}</p>
        </div>
    );
};

// Props with default values
const Button = ({ text = "Click me", onClick }) => {
    return <button onClick={onClick}>{text}</button>;
};

// Children prop
const Card = ({ children, title }) => {
    return (
        <div className="card">
            <h3>{title}</h3>
            {children}
        </div>
    );
};

// Usage: <Card title="Hello"><p>Content</p></Card>
```

### JSX

```jsx
// Variables
const name = "John";
<h1>Hello {name}</h1>

// Expressions
<p>{2 + 2}</p>
<p>{user.name.toUpperCase()}</p>

// Conditional rendering
{isLoggedIn && <Dashboard />}
{isLoggedIn ? <Dashboard /> : <Login />}

// Lists
<ul>
    {users.map(user => (
        <li key={user.id}>{user.name}</li>
    ))}
</ul>

// Attributes
<img src={imageUrl} alt="Description" />
<div className="container"></div>
<button onClick={handleClick}>Click</button>
<input value={value} onChange={handleChange} />

// Styles
<div style={{ color: 'red', fontSize: '16px' }}></div>

// Fragments
<>
    <h1>Title</h1>
    <p>Paragraph</p>
</>
```

### useState Hook

```jsx
import { useState } from 'react';

// Primitive values
const [count, setCount] = useState(0);
const [name, setName] = useState("");
const [isOpen, setIsOpen] = useState(false);

// Update
setCount(count + 1);
setName("John");
setIsOpen(!isOpen);

// Functional update (when new state depends on old)
setCount(prevCount => prevCount + 1);

// Objects
const [user, setUser] = useState({ name: "", email: "" });

// Update object - must create new object
setUser({ ...user, name: "John" });
setUser(prev => ({ ...prev, email: "john@example.com" }));

// Arrays
const [items, setItems] = useState([]);

// Add item
setItems([...items, newItem]);
setItems(prev => [...prev, newItem]);

// Remove item
setItems(items.filter(item => item.id !== id));

// Update item
setItems(items.map(item => 
    item.id === id ? { ...item, ...updates } : item
));

// Form state
const [formData, setFormData] = useState({
    name: "",
    email: "",
    password: ""
});

const handleChange = (e) => {
    setFormData({
        ...formData,
        [e.target.name]: e.target.value
    });
};
```

### useEffect Hook

```jsx
import { useEffect, useState } from 'react';

// Run once on mount
useEffect(() => {
    console.log('Component mounted');
}, []);

// Run when dependency changes
useEffect(() => {
    console.log('Count changed:', count);
}, [count]);

// Run on every render (avoid!)
useEffect(() => {
    console.log('Component rendered');
});

// Cleanup function
useEffect(() => {
    const timer = setInterval(() => {
        console.log('Tick');
    }, 1000);
    
    return () => {
        clearInterval(timer); // Cleanup
    };
}, []);

// Fetch data
useEffect(() => {
    const fetchData = async () => {
        const response = await fetch('/api/users');
        const data = await response.json();
        setUsers(data);
    };
    
    fetchData();
}, []);

// With loading & error states
const [data, setData] = useState(null);
const [loading, setLoading] = useState(true);
const [error, setError] = useState(null);

useEffect(() => {
    const fetchData = async () => {
        try {
            setLoading(true);
            const response = await fetch('/api/users');
            const result = await response.json();
            setData(result);
        } catch (err) {
            setError(err.message);
        } finally {
            setLoading(false);
        }
    };
    
    fetchData();
}, []);
```

### Event Handling

```jsx
// Click
const handleClick = () => {
    console.log('Clicked!');
};
<button onClick={handleClick}>Click</button>

// With parameter
const handleDelete = (id) => {
    console.log('Delete:', id);
};
<button onClick={() => handleDelete(user.id)}>Delete</button>

// Form submit
const handleSubmit = (e) => {
    e.preventDefault();
    console.log('Form submitted');
};
<form onSubmit={handleSubmit}>...</form>

// Input change
const handleChange = (e) => {
    setValue(e.target.value);
};
<input value={value} onChange={handleChange} />

// Checkbox
const handleCheck = (e) => {
    setChecked(e.target.checked);
};
<input type="checkbox" checked={checked} onChange={handleCheck} />

// Select
const handleSelect = (e) => {
    setSelected(e.target.value);
};
<select value={selected} onChange={handleSelect}>
    <option value="1">Option 1</option>
    <option value="2">Option 2</option>
</select>
```

### Forms

```jsx
// Controlled components
const [formData, setFormData] = useState({
    name: "",
    email: "",
    password: ""
});

const handleChange = (e) => {
    setFormData({
        ...formData,
        [e.target.name]: e.target.value
    });
};

const handleSubmit = (e) => {
    e.preventDefault();
    console.log('Submit:', formData);
};

return (
    <form onSubmit={handleSubmit}>
        <input
            type="text"
            name="name"
            value={formData.name}
            onChange={handleChange}
            placeholder="Name"
        />
        <input
            type="email"
            name="email"
            value={formData.email}
            onChange={handleChange}
            placeholder="Email"
        />
        <input
            type="password"
            name="password"
            value={formData.password}
            onChange={handleChange}
            placeholder="Password"
        />
        <button type="submit">Submit</button>
    </form>
);
```

### Custom Hooks

```jsx
// useFetch hook
function useFetch(url) {
    const [data, setData] = useState(null);
    const [loading, setLoading] = useState(true);
    const [error, setError] = useState(null);
    
    useEffect(() => {
        const fetchData = async () => {
            try {
                setLoading(true);
                const response = await fetch(url);
                const result = await response.json();
                setData(result);
            } catch (err) {
                setError(err.message);
            } finally {
                setLoading(false);
            }
        };
        
        fetchData();
    }, [url]);
    
    return { data, loading, error };
}

// Usage
const { data, loading, error } = useFetch('/api/users');

// useLocalStorage hook
function useLocalStorage(key, initialValue) {
    const [value, setValue] = useState(() => {
        const saved = localStorage.getItem(key);
        return saved ? JSON.parse(saved) : initialValue;
    });
    
    useEffect(() => {
        localStorage.setItem(key, JSON.stringify(value));
    }, [key, value]);
    
    return [value, setValue];
}

// Usage
const [name, setName] = useLocalStorage('name', '');

// useToggle hook
function useToggle(initialValue = false) {
    const [value, setValue] = useState(initialValue);
    const toggle = () => setValue(prev => !prev);
    return [value, toggle];
}

// Usage
const [isOpen, toggleOpen] = useToggle();
```

### Context API

```jsx
import { createContext, useContext, useState } from 'react';

// Create context
const ThemeContext = createContext();

// Provider component
export const ThemeProvider = ({ children }) => {
    const [theme, setTheme] = useState('light');
    
    const toggleTheme = () => {
        setTheme(prev => prev === 'light' ? 'dark' : 'light');
    };
    
    return (
        <ThemeContext.Provider value={{ theme, toggleTheme }}>
            {children}
        </ThemeContext.Provider>
    );
};

// Custom hook to use context
export const useTheme = () => {
    const context = useContext(ThemeContext);
    if (!context) {
        throw new Error('useTheme must be used within ThemeProvider');
    }
    return context;
};

// App.jsx
import { ThemeProvider } from './context/ThemeContext';

function App() {
    return (
        <ThemeProvider>
            <YourApp />
        </ThemeProvider>
    );
}

// Component using context
import { useTheme } from './context/ThemeContext';

function Header() {
    const { theme, toggleTheme } = useTheme();
    
    return (
        <header className={theme}>
            <button onClick={toggleTheme}>
                Toggle Theme
            </button>
        </header>
    );
}
```

### React Router

```jsx
import { BrowserRouter, Routes, Route, Link, useNavigate, useParams } from 'react-router-dom';

// App setup
function App() {
    return (
        <BrowserRouter>
            <nav>
                <Link to="/">Home</Link>
                <Link to="/about">About</Link>
                <Link to="/users">Users</Link>
            </nav>
            
            <Routes>
                <Route path="/" element={<Home />} />
                <Route path="/about" element={<About />} />
                <Route path="/users" element={<Users />} />
                <Route path="/users/:id" element={<UserDetail />} />
                <Route path="*" element={<NotFound />} />
            </Routes>
        </BrowserRouter>
    );
}

// useParams - Get URL params
function UserDetail() {
    const { id } = useParams();
    return <div>User ID: {id}</div>;
}

// useNavigate - Programmatic navigation
function Login() {
    const navigate = useNavigate();
    
    const handleLogin = () => {
        // Login logic...
        navigate('/dashboard');
    };
    
    return <button onClick={handleLogin}>Login</button>;
}

// Protected Route
const ProtectedRoute = ({ children }) => {
    const { user } = useAuth();
    return user ? children : <Navigate to="/login" />;
};

<Route 
    path="/dashboard" 
    element={
        <ProtectedRoute>
            <Dashboard />
        </ProtectedRoute>
    } 
/>
```

---

## 🔧 Common Patterns

### Loading State Pattern

```jsx
function UserList() {
    const [users, setUsers] = useState([]);
    const [loading, setLoading] = useState(true);
    const [error, setError] = useState(null);
    
    useEffect(() => {
        fetch('/api/users')
            .then(res => res.json())
            .then(data => {
                setUsers(data);
                setLoading(false);
            })
            .catch(err => {
                setError(err.message);
                setLoading(false);
            });
    }, []);
    
    if (loading) return <div>Loading...</div>;
    if (error) return <div>Error: {error}</div>;
    
    return (
        <ul>
            {users.map(user => (
                <li key={user.id}>{user.name}</li>
            ))}
        </ul>
    );
}
```

### Debounce Pattern

```jsx
function SearchInput() {
    const [query, setQuery] = useState("");
    const [results, setResults] = useState([]);
    
    useEffect(() => {
        const timer = setTimeout(() => {
            if (query) {
                fetch(`/api/search?q=${query}`)
                    .then(res => res.json())
                    .then(data => setResults(data));
            }
        }, 500); // Wait 500ms after user stops typing
        
        return () => clearTimeout(timer);
    }, [query]);
    
    return (
        <input
            value={query}
            onChange={(e) => setQuery(e.target.value)}
            placeholder="Search..."
        />
    );
}
```

### Pagination Pattern

```jsx
function UserList() {
    const [users, setUsers] = useState([]);
    const [page, setPage] = useState(1);
    const [totalPages, setTotalPages] = useState(1);
    
    useEffect(() => {
        fetch(`/api/users?page=${page}`)
            .then(res => res.json())
            .then(data => {
                setUsers(data.users);
                setTotalPages(data.totalPages);
            });
    }, [page]);
    
    return (
        <div>
            <ul>
                {users.map(user => (
                    <li key={user.id}>{user.name}</li>
                ))}
            </ul>
            
            <div>
                <button 
                    onClick={() => setPage(p => Math.max(1, p - 1))}
                    disabled={page === 1}
                >
                    Previous
                </button>
                
                <span>Page {page} of {totalPages}</span>
                
                <button 
                    onClick={() => setPage(p => Math.min(totalPages, p + 1))}
                    disabled={page === totalPages}
                >
                    Next
                </button>
            </div>
        </div>
    );
}
```

---

## 🐛 Common Mistakes & Solutions

### 1. Mutating State Directly

```jsx
// ❌ Wrong
const handleClick = () => {
    user.name = "John"; // Mutating
    setUser(user); // Won't trigger re-render
};

// ✅ Correct
const handleClick = () => {
    setUser({ ...user, name: "John" });
};
```

### 2. Infinite useEffect Loop

```jsx
// ❌ Wrong
useEffect(() => {
    setCount(count + 1); // Causes infinite loop
}, [count]);

// ✅ Correct
useEffect(() => {
    // Only run once
    setCount(1);
}, []);
```

### 3. Missing Key Prop

```jsx
// ❌ Wrong
{users.map((user, index) => (
    <div key={index}>{user.name}</div>
))}

// ✅ Correct
{users.map(user => (
    <div key={user.id}>{user.name}</div>
))}
```

### 4. Async State Updates

```jsx
// ❌ Wrong - state might be stale
const handleClick = () => {
    setCount(count + 1);
    setCount(count + 1); // Still uses old count
    // Result: count + 1, not count + 2
};

// ✅ Correct
const handleClick = () => {
    setCount(prev => prev + 1);
    setCount(prev => prev + 1);
    // Result: count + 2
};
```

### 5. Forgetting event.preventDefault()

```jsx
// ❌ Wrong - page will reload
const handleSubmit = (e) => {
    console.log('Submit');
};

// ✅ Correct
const handleSubmit = (e) => {
    e.preventDefault();
    console.log('Submit');
};
```

---

## 🚀 Performance Tips

### 1. Use Keys Properly
Always use unique, stable keys for lists (prefer `id` over `index`)

### 2. Avoid Inline Functions (for performance-critical components)
```jsx
// Less ideal (creates new function every render)
<button onClick={() => handleClick(id)}>Click</button>

// Better
const onClick = useCallback(() => handleClick(id), [id]);
<button onClick={onClick}>Click</button>
```

### 3. Memoize Expensive Calculations
```jsx
import { useMemo } from 'react';

const expensiveValue = useMemo(() => {
    return computeExpensiveValue(a, b);
}, [a, b]);
```

### 4. Split Components
Break large components into smaller ones for better re-render performance

### 5. Use Production Build
```bash
npm run build  # Creates optimized production build
```

---

**Bookmark this page! 🔖**

