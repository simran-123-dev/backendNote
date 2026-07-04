# 📘 Node.js Notes - File Handling in Node.js

> Based on Piyush Garg's **File Handling in NodeJS** video.

---

# 📌 What is File Handling?

File Handling refers to performing operations on files such as:

- Creating files
- Reading files
- Writing files
- Updating files
- Renaming files
- Deleting files

Node.js provides the built-in **File System (fs)** module for these operations.

---

# 📂 File System (fs) Module

The `fs` module is a **Core Module** in Node.js.

Import it using:

```javascript
const fs = require("fs");
```

No installation is required.

---

# 📖 Reading a File

## Synchronous Method

```javascript
const data = fs.readFileSync("hello.txt", "utf-8");

console.log(data);
```

### Characteristics

- Blocking
- Executes line by line
- Waits until file reading is completed

---

## Asynchronous Method

```javascript
fs.readFile("hello.txt", "utf-8", (err, data) => {
    if (err) {
        console.log(err);
        return;
    }

    console.log(data);
});
```

### Characteristics

- Non-blocking
- Uses Callback Function
- Better performance

---

# ✍️ Writing into a File

## Synchronous

```javascript
fs.writeFileSync("hello.txt", "Hello Node.js");
```

Creates the file if it doesn't exist.

If the file exists, its contents are overwritten.

---

## Asynchronous

```javascript
fs.writeFile(
    "hello.txt",
    "Hello Node.js",
    (err) => {
        if (err) console.log(err);
    }
);
```

---

# ➕ Appending Data

Adds new data without removing existing content.

```javascript
fs.appendFileSync(
    "hello.txt",
    "\nWelcome to Node.js"
);
```

---

# ❌ Deleting a File

```javascript
fs.unlinkSync("hello.txt");
```

Asynchronous version:

```javascript
fs.unlink("hello.txt", (err) => {
    if (err) console.log(err);
});
```

---

# ✏️ Renaming a File

```javascript
fs.renameSync(
    "hello.txt",
    "notes.txt"
);
```

---

# 📁 Creating a Folder

```javascript
fs.mkdirSync("Images");
```

---

# 🗑️ Removing a Folder

```javascript
fs.rmdirSync("Images");
```

> Modern Node.js versions also support:

```javascript
fs.rmSync("Images", {
    recursive: true
});
```

---

# 📄 Check if File Exists

```javascript
const exists = fs.existsSync("hello.txt");

console.log(exists);
```

Output:

```
true
```

or

```
false
```

---

# ⚡ Synchronous vs Asynchronous

| Synchronous | Asynchronous |
|-------------|--------------|
| Blocking | Non-blocking |
| Executes sequentially | Executes in background |
| Simpler | Better performance |
| Slower for large tasks | Faster and scalable |

---

# 🔄 Execution Flow

## Synchronous

```
Read File
    │
    ▼
Wait
    │
    ▼
Next Line Executes
```

---

## Asynchronous

```
Read File
    │
    ▼
Background
    │
    ▼
Continue Next Line
    │
    ▼
Callback Executes Later
```

---

# 📌 Common File System Methods

| Method | Purpose |
|---------|---------|
| readFileSync() | Read file synchronously |
| readFile() | Read file asynchronously |
| writeFileSync() | Write file synchronously |
| writeFile() | Write file asynchronously |
| appendFileSync() | Append data |
| unlinkSync() | Delete file |
| renameSync() | Rename file |
| mkdirSync() | Create directory |
| rmSync() | Delete directory |
| existsSync() | Check file existence |

---

# 🎯 Best Practice

✅ Prefer **Asynchronous methods** because Node.js is designed for **non-blocking I/O**.

Use synchronous methods mainly for:

- Small scripts
- Learning
- Startup configuration

---

# 📖 Interview Questions

### 1. Which module is used for file handling?

**Answer:** `fs` (File System) module.

---

### 2. Is `fs` a Core Module?

**Answer:** Yes.

---

### 3. Difference between `readFile()` and `readFileSync()`?

| readFile() | readFileSync() |
|-------------|----------------|
| Asynchronous | Synchronous |
| Non-blocking | Blocking |
| Uses callback | Returns data directly |

---

### 4. Which method adds data without replacing existing content?

```javascript
fs.appendFileSync()
```

---

### 5. Which method deletes a file?

```javascript
fs.unlinkSync()
```

or

```javascript
fs.unlink()
```

---

# 📝 Quick Revision

- `fs` is the File System module.
- Use `require("fs")` to import it.
- Read files using `readFile()` or `readFileSync()`.
- Write files using `writeFile()`.
- Append data using `appendFile()`.
- Delete files using `unlink()`.
- Rename files using `rename()`.
- Prefer asynchronous methods for better performance.

---

# 🎯 Key Takeaways

- File handling is done using the built-in **fs module**.
- Node.js supports both synchronous and asynchronous file operations.
- Asynchronous methods are faster because they do not block the event loop.
- Common operations include reading, writing, appending, deleting, and renaming files.
