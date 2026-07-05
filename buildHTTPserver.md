# 📘 Node.js Notes - HTTP Server in Node.js

> Based on Piyush Garg's **HTTP Server in Node.js** video.

---

# 📌 What is an HTTP Server?

An **HTTP Server** is a program that listens for incoming HTTP requests from clients (browsers, mobile apps, Postman, etc.) and sends back an HTTP response.

### Flow

```
Client (Browser/Postman)
        │
   HTTP Request
        │
        ▼
   Node.js Server
        │
   HTTP Response
        │
        ▼
Client Receives Data
```

---

# 🌐 What is HTTP?

HTTP stands for **HyperText Transfer Protocol**.

It is the communication protocol used between a client and a server.

Example:

```
Browser
   │
GET /
   │
   ▼
Server
   │
200 OK
Hello World
```

---

# 📦 HTTP Module

Node.js provides a built-in module named **http**.

No installation is required.

Import it using:

```javascript
const http = require("http");
```

---

# 🏗 Creating an HTTP Server

Use the `createServer()` method.

Example:

```javascript
const http = require("http");

const server = http.createServer((req, res) => {
    res.end("Hello World");
});
```

---

# ▶️ Listening on a Port

A server must listen on a port to receive requests.

Example:

```javascript
server.listen(8000, () => {
    console.log("Server Started");
});
```

Visit:

```
http://localhost:8000
```

Output:

```
Hello World
```

---

# 📌 What is a Port?

A **Port** is a communication endpoint where the server listens for requests.

Examples:

- 3000
- 5000
- 8000
- 8080

Example:

```javascript
server.listen(8000);
```

---

# 🔍 Request Object (`req`)

The `req` object contains information about the incoming request.

Useful properties:

```javascript
req.url
req.method
req.headers
```

Example:

```javascript
console.log(req.url);
```

---

# 📤 Response Object (`res`)

The `res` object is used to send data back to the client.

Example:

```javascript
res.end("Hello World");
```

---

# 📌 Handling Different Routes

Example:

```javascript
const server = http.createServer((req, res) => {

    if (req.url === "/") {
        res.end("Home Page");
    }

    else if (req.url === "/about") {
        res.end("About Page");
    }

    else {
        res.end("404 Not Found");
    }

});
```

---

# 📌 Handling Different HTTP Methods

Example:

```javascript
if (req.method === "GET") {
    res.end("GET Request");
}
```

Common HTTP Methods:

- GET
- POST
- PUT
- DELETE

---

# 📂 Complete Example

```javascript
const http = require("http");

const server = http.createServer((req, res) => {

    if (req.url === "/") {
        res.end("Welcome Home");
    }

    else if (req.url === "/about") {
        res.end("About Us");
    }

    else {
        res.end("404 Page Not Found");
    }

});

server.listen(8000, () => {
    console.log("Server Running");
});
```

---

# 🧠 Important Concepts

### Request

Data sent from client to server.

Example:

```
GET /about
```

---

### Response

Data sent from server to client.

Example:

```
About Page
```

---

### Server

A program that accepts requests and returns responses.

---

### localhost

`localhost` refers to your own computer.

Example:

```
http://localhost:8000
```

---

# 📖 Interview Questions

### 1. What is an HTTP Server?

A server that receives HTTP requests and returns HTTP responses.

---

### 2. Which module is used to create an HTTP server in Node.js?

```javascript
http
```

---

### 3. Which method creates a server?

```javascript
http.createServer()
```

---

### 4. Which method starts the server?

```javascript
server.listen()
```

---

### 5. What is `req`?

The request object containing client request information.

---

### 6. What is `res`?

The response object used to send data back to the client.

---

### 7. What does `res.end()` do?

It sends the response to the client and ends the request.

---

### 8. What is a Port?

A communication endpoint where the server listens for incoming requests.

---

# 📝 Quick Revision

- HTTP = HyperText Transfer Protocol
- `http` is a built-in Node.js module
- `http.createServer()` creates a server
- `server.listen(port)` starts the server
- `req` stores request information
- `res` sends data back to the client
- `res.end()` completes the response

---

# 🎯 Key Takeaways

- Node.js can create an HTTP server without Express.
- Every request has a **Request (`req`)** object and a **Response (`res`)** object.
- Servers listen on a specific port (e.g., 8000).
- Routing can be handled using `req.url`.
- Express internally simplifies many tasks built on top of Node's `http` module.
