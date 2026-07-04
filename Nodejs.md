# 📘 Node.js Notes - What is Node.js?

> Based on Piyush Garg's "What is Node.js?" video.

---

# 📌 What is Node.js?

Node.js is a **JavaScript Runtime Environment** built on Google's **V8 JavaScript Engine**.

It allows developers to run JavaScript **outside the browser**, mainly on the server side.

> **Important:** Node.js is **NOT** a programming language and **NOT** a framework.

---

# 🚀 Why Node.js?

Before Node.js:
- JavaScript could only run inside browsers.
- Backend development was done using Java, PHP, Python, etc.

After Node.js:
- JavaScript can be used for both frontend and backend development.
- Developers can build full-stack applications using a single language.

---

# ⚙️ Runtime Environment

A Runtime Environment provides everything required to execute a program.

### Example

```
JavaScript Code
       │
       ▼
Runtime Environment
       │
       ▼
Machine Code
       │
       ▼
Output
```

Node.js acts as the runtime environment for JavaScript outside the browser.

---

# 🔥 V8 JavaScript Engine

Node.js is built on Google's **V8 Engine**.

### Responsibilities

- Reads JavaScript code
- Compiles it into machine code
- Executes it efficiently

### Benefits

- Fast execution
- High performance
- Optimized memory usage

---

# 🌍 Browser vs Node.js

| Browser JavaScript | Node.js |
|--------------------|----------|
| Runs inside browser | Runs on server |
| Has DOM access | No DOM access |
| Used for UI | Used for backend |
| Handles client-side logic | Handles server-side logic |

---

# ⭐ Features of Node.js

- Fast execution
- Asynchronous programming
- Non-blocking I/O
- Event-driven architecture
- Cross-platform
- Large npm ecosystem
- Lightweight
- Scalable

---

# 📦 What is npm?

**npm = Node Package Manager**

It is used to:

- Install packages
- Manage project dependencies
- Run scripts
- Update packages

Example:

```bash
npm install express
```

---

# 💻 Applications of Node.js

Node.js is commonly used for:

- REST APIs
- Authentication Systems
- Chat Applications
- Social Media Backends
- E-commerce Websites
- Real-time Applications
- File Upload Systems
- Streaming Applications

---

# 📚 Important Terms

## Runtime Environment

Software that allows code to execute.

---

## V8 Engine

Google's JavaScript Engine that executes JavaScript.

---

## Backend

The server-side part of an application that handles:

- Database
- Authentication
- Business Logic
- APIs

---

## API

API (Application Programming Interface) enables communication between the frontend and backend.

Example:

```
Frontend
    │
    ▼
   API
    │
    ▼
Backend
```

---

# 🎯 Advantages of Node.js

- Uses JavaScript everywhere
- High performance
- Fast execution
- Supports asynchronous programming
- Handles multiple requests efficiently
- Huge open-source community
- Thousands of npm packages

---

# ❌ Limitations

- Not ideal for CPU-intensive tasks
- Single-threaded architecture
- Heavy computations can block the event loop

---

# 📖 Interview Questions

### 1. What is Node.js?

Node.js is a JavaScript Runtime Environment built on Google's V8 JavaScript Engine that allows JavaScript to run outside the browser.

---

### 2. Is Node.js a Programming Language?

No.

---

### 3. Is Node.js a Framework?

No.

---

### 4. Which Engine does Node.js use?

Google V8 JavaScript Engine.

---

### 5. Can Node.js access the DOM?

No.

DOM is available only inside browsers.

---

### 6. What is npm?

Node Package Manager used to install and manage Node.js packages.

---

# 📝 Quick Revision

- Node.js = JavaScript Runtime Environment
- Built on Google V8 Engine
- Runs JavaScript outside the browser
- Used for backend development
- Supports asynchronous programming
- Uses npm for package management

---

# 🧠 Key Takeaways

- JavaScript can run on the server using Node.js.
- Node.js is fast because it uses the V8 Engine.
- npm provides access to thousands of reusable packages.
- Node.js is widely used for backend development, APIs, and authentication systems.
