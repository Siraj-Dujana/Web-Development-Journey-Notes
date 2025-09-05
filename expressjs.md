# 🚀 **Library vs. Framework**  

### 📚 **Library:**  
A **library** is a collection of pre-written code that helps with specific tasks. You call the functions when needed.  
✅ **Example:** Axios (used for making HTTP requests).  

🔹 **Key Point:** A library helps with **small parts** of your application, giving you flexibility.  

### 🏗️ **Framework:**  
A **framework** provides a structured way to build applications, enforcing rules on how code should be written.  
✅ **Example:** Express.js (used for building web applications).  

🔹 **Key Point:** A framework **controls** the flow of your application and offers reusable components.  

---

# 🚀 **Express.js – The Minimalist Web Framework**  

Express.js is a **lightweight and flexible** web framework for Node.js that helps build server-side applications.  

### 🔥 **Why Use Express?**  
✔ **Listens for Requests** – Handles incoming HTTP requests (GET, POST, etc.).  
✔ **Parses Requests** – Reads and extracts data (JSON, form data, query params).  
✔ **Handles Routes** – Matches URLs with appropriate responses.  
✔ **Sends Responses** – Returns text, JSON, HTML, or files.  

---

## ✨ **Getting Started with Express**  

### 1️⃣ **Install Express**  
```bash
npm install express
```

### 2️⃣ **Import Express & Create Server**
```js
const express = require('express');
const app = express();
```

### 3️⃣ **Define a Route**
```js
app.get('/', (req, res) => {
    res.send('Welcome to Express.js!');
});
```

### 4️⃣ **Start the Server**
```js
app.listen(3000, () => {
    console.log('Server is running on http://localhost:3000');
});
```

---

# 🌍 **Ports and IPs**  

🔌 **Port** – A communication endpoint between client and server (e.g., 3000, 8080).  
💻 **IP Address** – Identifies a device on a network (e.g., `192.168.1.1`).  
🌐 **Why Both?** – The IP tells **where** to connect, and the port tells **which service** to connect to.  

---

# 🛠️ **Middleware – `app.use()`**  

📡 Middleware is a function that runs **before** sending a response.  
```js
app.use((req, res, next) => {
    console.log('A request was made!');
    next(); // Passes control to the next middleware
});
```

---

# 📝 **Handling Requests & Responses**  

### 🌐 **Request (req)** – Contains data sent by the user.  
### 📬 **Response (res)** – What the server sends back.  

Example:  
```js
app.use((req, res) => {
    console.log('Request received!');
    res.send('Hello, World!');
});
```

---

# 🛤️ **Routing in Express**  

### ✅ **Basic Route**  
```js
app.get('/', (req, res) => {
    res.send('Welcome to the homepage!');
});
```

### ❌ **Handling 404 Errors**  
```js
app.get('*', (req, res) => {
    res.send('This page doesn’t exist!');
});
```

---

# 🔄 **Nodemon – Auto Restart Server**  

### 💡 Install Nodemon  
```bash
npm install -g nodemon
```

### 🛠️ Run the Server  
```bash
nodemon express.js
```

🚀 **Nodemon automatically restarts your server when code changes.**  

---

# 🌍 **Path Parameters & Query Strings**  

### 📌 **Path Parameters** (Used for identifying a specific resource)  
🔹 `/user/123` → Fetches user with ID **123**  
```js
app.get('/user/:id', (req, res) => {
    const { id } = req.params;
    res.send(`User ID: ${id}`);
});
```

### 🔎 **Query Strings** (Used for searches & filters)  
🔹 `/search?name=John&age=25`  
```js
app.get('/search', (req, res) => {
    const { name, age } = req.query;
    res.send(`Searching for ${name}, age ${age}`);
});
```

---

# 🎨 **Templating with EJS**  

EJS allows dynamic HTML rendering using JavaScript.  

### 🛠️ **Install EJS**  
```bash
npm install ejs
```

### 🔧 **Use EJS in Express**  
```js
app.set('view engine', 'ejs');
```

### 🔧 **Views Directory **  
```js
project/
│
├─ app.js
└─ views/
   └─ index.ejs   <-- put your HTML code here
```

### 📄 **Render a Template**  
```js
app.get('/', (req, res) => {
    res.render('home.ejs');
});
```

### 🔀 **Conditional Statements in EJS**  
```html
<% if (userLoggedIn) { %>
    <h1>Welcome back, <%= username %>!</h1>
<% } else { %>
    <h1>Please log in.</h1>
<% } %>
```

### 📄 **Includes (Reusable Templates)**  
```html
<%- include("includes/header.ejs"); %>
```

---

# 🔄 **Handling GET & POST Requests**  

### ✅ **GET Request** – Retrieves data  
- Data sent in **query string** (visible in URL).  
- Used for fetching info.  

### ✉ **POST Request** – Submits data  
- Data sent in **request body** (hidden from URL).  
- Used for creating or updating info.  

🔹 **Handling POST Requests in Express**  
```js
app.use(express.urlencoded({ extended: true })); // Parse form data
app.use(express.json()); // Parse JSON data
```

---

# 🎭 **Object-Oriented Programming (OOP) in JavaScript**  

### 🏗️ **Why OOP?**  
✔ **Organizes Code**  
✔ **Reusability**  
✔ **Better Maintainability**  
✔ **Real-World Representation**  

### ⚡ **Creating Objects – The Inefficient Way**  
```js
const stu1 = { marks: 10, getMarks: function() { return this.marks; } };
const stu2 = { marks: 10, getMarks: function() { return this.marks; } };
```
🔴 **Problem:** Each object takes up separate memory.  

---

# 🏗️ **Better Way: Using Classes & Prototypes**  

### ✅ **Prototypes (Shared Methods for Efficiency)**  
```js
function Student(name, marks) {
    this.name = name;
    this.marks = marks;
}
Student.prototype.getMarks = function() {
    return this.marks;
};

let s1 = new Student('John', 90);
let s2 = new Student('Jane', 85);
```

---

# 🏛️ **Classes in JavaScript**  

✔ **A blueprint for creating objects**  
✔ **More readable & modern**  

```js
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }

    talk() {
        console.log(`Hi, my name is ${this.name}`);
    }
}

let p1 = new Person('Adam', 25);
```

---

# 🏗️ **Inheritance in JavaScript**  

🔹 **Child class gets properties from Parent class.**  

```js
class Student extends Person {
    constructor(name, age, marks) {
        super(name, age);
        this.marks = marks;
    }

    greet() {
        return "Hello!";
    }
}

let s1 = new Student('Emma', 22, 95);
```

---

# 🌎 **REST API – Building Web Services**  

✅ **REST (Representational State Transfer)**  
- A set of rules for designing APIs.  
- Uses HTTP methods:  
  - **GET** – Retrieve data  
  - **POST** – Create new data  
  - **PUT/PATCH** – Update data  
  - **DELETE** – Remove data  

✅ **Building an API for Quora Posts**  
1️⃣ **GET /posts** → View all posts  
2️⃣ **POST /posts** → Add a new post  
3️⃣ **GET /posts/:id** → View a specific post  
4️⃣ **PATCH /posts/:id** → Update a post  
5️⃣ **DELETE /posts/:id** → Delete a post  

---

💡 **Hope this makes Express.js & OOP clear! Let me know if you need more help! 🚀🔥**