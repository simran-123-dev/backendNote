# 📘 Node.js Notes - Modules in Node.js

> Based on Piyush Garg's **Modules in NodeJS** video.

---

# 📌 What are Modules?

A **Module** is a reusable piece of code that contains related functionality.

Instead of writing everything in one file, we divide our code into multiple files called **modules**.

### Example

```
Project
│
├── index.js
├── math.js
└── user.js
```

Each file is a separate module.

---

# 🤔 Why do we use Modules?

- Better code organization
- Code reusability
- Easy maintenance
- Easier debugging
- Cleaner project structure

---

# 📦 Types of Modules

## 1. Core Modules (Built-in)

These modules come with Node.js.

Examples:

- fs
- http
- path
- os
- crypto
- events

No installation is required.

Example:

```javascript
const fs = require("fs");
```

---

## 2. Local Modules

Modules created by the developer.

Example:

```
math.js
```

Imported using:

```javascript
const math = require("./math");
```

---

## 3. Third-Party Modules

Installed using npm.

Example:

```bash
npm install express
```

Import:

```javascript
const express = require("express");
```

---

# 📥 require()

`require()` is used to import a module into another file.

Syntax:

```javascript
const moduleName = require("module-name");
```

Example:

```javascript
const fs = require("fs");
```

Local module:

```javascript
const math = require("./math");
```

---

# 📤 module.exports

Used to export functions, objects, or variables from a module.

Example:

```javascript
function add(a, b) {
    return a + b;
}

module.exports = add;
```

Import:

```javascript
const add = require("./math");

console.log(add(2, 3));
```

Output:

```
5
```

---

# 📤 Export Multiple Functions

```javascript
function add(a, b) {
    return a + b;
}

function sub(a, b) {
    return a - b;
}

module.exports = {
    add,
    sub
};
```

Import:

```javascript
const math = require("./math");

console.log(math.add(5, 2));
console.log(math.sub(5, 2));
```

---

# 📤 Using exports

Instead of:

```javascript
module.exports = {
    add,
    sub
};
```

You can also write:

```javascript
exports.add = add;
exports.sub = sub;
```

Both export functions from the module.

---

# 📂 Folder Structure Example

```
project/
│
├── index.js
├── math.js
└── package.json
```

---

# 💻 Example

## math.js

```javascript
function add(a, b) {
    return a + b;
}

module.exports = add;
```

---

## index.js

```javascript
const add = require("./math");

console.log(add(10, 20));
```

Output:

```
30
```

---

# 🔄 Module Flow

```
math.js
   │
module.exports
   │
   ▼
require("./math")
   │
   ▼
index.js
```

---

# 📌 Important Points

- Every JavaScript file in Node.js is treated as a module.
- `require()` imports modules.
- `module.exports` exports data or functions.
- Built-in modules do not require installation.
- Third-party modules are installed using npm.

---

# 📖 Interview Questions

### 1. What is a module?

A reusable piece of JavaScript code stored in a separate file.

---

### 2. What is require()?

A function used to import modules.

---

### 3. What is module.exports?

Used to export functions, objects, or variables from a module.

---

### 4. Name three built-in Node.js modules.

- fs
- http
- path

---

### 5. Difference between Local Module and Core Module?

| Local Module | Core Module |
|--------------|-------------|
| Created by developer | Built into Node.js |
| Imported using `./` | Imported by module name |
| Example: `math.js` | Example: `fs`, `http` |

---

# 📝 Quick Revision

- Module = Reusable code
- `require()` imports modules
- `module.exports` exports modules
- Every file is a module
- Types of modules:
  - Core Modules
  - Local Modules
  - Third-Party Modules

---

# 🎯 Key Takeaways

- Modules help organize code into smaller files.
- Use `require()` to import functionality.
- Use `module.exports` or `exports` to share functionality.
- Node.js applications rely heavily on modular programming.
