# 📘 Node.js Notes - How Node.js Works Internally

> Based on Piyush Garg's **How Node.js Works?** video.

---

# 📌 Node.js Architecture

Node.js follows a **Single-Threaded, Event-Driven, Non-Blocking I/O Architecture**.

Although JavaScript runs on a **single main thread**, Node.js can handle thousands of requests efficiently using:

- V8 Engine
- Event Loop
- Event Queue
- libuv
- Thread Pool

---

# 🏗️ Components of Node.js Architecture

## 1. V8 Engine

Google's JavaScript Engine.

Responsibilities:

- Executes JavaScript code
- Converts JavaScript into Machine Code
- Provides very fast execution

---

## 2. Main Thread

- Executes JavaScript code.
- Handles synchronous (blocking) operations.
- Runs the Event Loop.

There is **only one main thread**.

---

## 3. Event Queue

The Event Queue stores incoming tasks or completed asynchronous callbacks.

Example:

```
Request 1
Request 2
Request 3
Request 4
```

The Event Loop continuously checks this queue.

---

## 4. Event Loop

The **Event Loop** is the heart of Node.js.

Responsibilities:

- Monitors the Event Queue.
- Picks completed tasks.
- Executes callback functions.
- Keeps the application responsive.

Without the Event Loop, asynchronous programming would not work.

---

## 5. libuv

**libuv** is a C library used internally by Node.js.

Responsibilities:

- Handles asynchronous I/O
- File System operations
- Networking
- DNS
- Thread Pool management

---

## 6. Thread Pool

Some operations are expensive and should not block the main thread.

Node.js sends these tasks to the **Thread Pool** managed by **libuv**.

Examples:

- File System (`fs`)
- Crypto
- DNS Lookup
- Compression

Default Thread Pool Size:

```text
4 Threads
```

It can be increased using the environment variable:

```bash
UV_THREADPOOL_SIZE=8
```

---

# 🔄 Request Flow

```text
            Client Request
                  │
                  ▼
           Node.js Server
                  │
                  ▼
             Event Queue
                  │
                  ▼
             Event Loop
          ┌──────────────┐
          │              │
          ▼              ▼
Blocking          Non-Blocking
Operation          Operation
   │                    │
   ▼                    ▼
Execute on        Thread Pool
Main Thread             │
                         ▼
                  Task Completed
                         │
                         ▼
                  Callback Queue
                         │
                         ▼
                    Event Loop
                         │
                         ▼
                  Send Response
```

---

# 🚫 Blocking Operations

Blocking operations stop the execution of the program until the current task finishes.

During this time, the main thread cannot process other requests.

Example:

```javascript
const fs = require("fs");

const data = fs.readFileSync("notes.txt", "utf8");

console.log(data);
console.log("Finished");
```

Execution:

```text
Read File
    │
    ▼
Wait...
    │
    ▼
Print Data
    │
    ▼
Finished
```

Characteristics:

- Synchronous
- Blocks the Main Thread
- Lower performance
- Not suitable for large applications

---

# ✅ Non-Blocking Operations

Non-blocking operations do not stop the execution of the program.

Node.js sends these tasks to the Thread Pool while the main thread continues executing other code.

Example:

```javascript
const fs = require("fs");

fs.readFile("notes.txt", "utf8", (err, data) => {
    console.log(data);
});

console.log("Finished");
```

Execution:

```text
Read File
    │
    ▼
Send to Thread Pool
    │
    ▼
Continue Execution
    │
    ▼
Print "Finished"
    │
    ▼
File Reading Completed
    │
    ▼
Execute Callback
```

Characteristics:

- Asynchronous
- Does not block the Main Thread
- High Performance
- Handles multiple requests efficiently

---

# 🔄 Blocking vs Non-Blocking

| Blocking | Non-Blocking |
|----------|--------------|
| Synchronous | Asynchronous |
| Waits for task completion | Continues execution immediately |
| Blocks Main Thread | Uses Thread Pool |
| Lower scalability | High scalability |
| Example: `readFileSync()` | Example: `readFile()` |

---

# 🧵 Thread Pool

The Thread Pool is a collection of worker threads managed by **libuv**.

Whenever Node.js encounters a heavy asynchronous task, it sends it to a worker thread.

Example Flow:

```text
Main Thread
      │
      ▼
Need Heavy Task?
      │
      ▼
Assign Worker Thread
      │
      ▼
Worker Executes Task
      │
      ▼
Return Result
      │
      ▼
Event Loop Executes Callback
```

---

# 📌 Operations that use Thread Pool

- File System (`fs`)
- Crypto (`bcrypt`, encryption)
- DNS Lookup
- Compression (zlib)

---

# ⚡ Why is Node.js Fast?

Node.js is fast because:

- Uses Google's V8 Engine
- Uses Event Loop
- Uses Non-Blocking I/O
- Uses libuv
- Uses Thread Pool for heavy tasks
- Avoids creating a new thread for every request

---

# 📖 Interview Questions

### 1. Why is Node.js called Single-Threaded?

Because JavaScript code executes on a single main thread.

---

### 2. What is the Event Loop?

The Event Loop continuously checks the Event Queue and executes completed asynchronous callbacks.

---

### 3. What is libuv?

A C library that provides asynchronous I/O and manages the Thread Pool.

---

### 4. What is the default Thread Pool size?

```text
4 Threads
```

It can be changed using:

```bash
UV_THREADPOOL_SIZE
```

---

### 5. Which operations use the Thread Pool?

- File System
- Crypto
- DNS
- Compression

---

### 6. Difference between Blocking and Non-Blocking?

| Blocking | Non-Blocking |
|----------|--------------|
| Synchronous | Asynchronous |
| Waits | Doesn't Wait |
| Blocks Main Thread | Uses Thread Pool |
| Slower | Faster |

---

# 📝 Quick Revision

- Node.js is Single-Threaded.
- JavaScript runs on one Main Thread.
- Event Loop handles asynchronous callbacks.
- Event Queue stores completed async tasks.
- libuv manages asynchronous operations.
- Heavy tasks are executed by the Thread Pool.
- Default Thread Pool Size = **4**.
- Prefer Non-Blocking APIs for better performance.

---

# 🎯 Key Takeaways

- Node.js achieves concurrency through the **Event Loop** and **libuv**, not by creating a thread for every request.
- Blocking operations pause the main thread, while non-blocking operations run in the background and improve scalability.
- Understanding the Event Loop and Thread Pool is essential for writing efficient Node.js applications.
