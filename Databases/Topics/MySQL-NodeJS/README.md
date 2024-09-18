# Connecting MySQL Database to Node.js and Express Using mysql2 Module

Connecting a MySQL database to a Node.js and Express framework allows for the creation of dynamic and data-driven web applications. The `mysql2` module is a fast and modern MySQL client for Node.js that supports all MySQL features. In this learning material, we will cover how to install and configure the `mysql2` module, establish a connection to a MySQL database, and perform database queries while structuring the application into services and controllers. We will also discuss preventing SQL injections using parameterized queries.

![MySQL-NodeJS](MySQL-Node.webp)

Image source: Dall-E by OpenAI

- [Connecting MySQL Database to Node.js and Express Using mysql2 Module](#connecting-mysql-database-to-nodejs-and-express-using-mysql2-module)
  - [Learning Outcomes](#learning-outcomes)
  - [Prerequisites](#prerequisites)
  - [Step 1: Setting Up the Project](#step-1-setting-up-the-project)
    - [1.1. Creating a Node.js Project](#11-creating-a-nodejs-project)
    - [1.2. Installing Required Dependencies](#12-installing-required-dependencies)
  - [Step 2: Structuring the Project](#step-2-structuring-the-project)
    - [2.1. Configuring the Connection](#21-configuring-the-connection)
    - [2.2. Creating Services](#22-creating-services)
    - [2.3. Creating Controllers](#23-creating-controllers)
    - [2.4. Creating the Express Server](#24-creating-the-express-server)
  - [SQL Injection and Parameterized Queries](#sql-injection-and-parameterized-queries)
    - [What is SQL Injection?](#what-is-sql-injection)
    - [Parameterized Queries](#parameterized-queries)
      - [Example: Using Parameterized Queries](#example-using-parameterized-queries)

## Learning Outcomes

By the end of this material, learners should be able to:

- Install and configure the `mysql2` module in a Node.js project;
- Establish a connection to a MySQL database;
- Perform basic CRUD (Create, Read, Update, Delete) queries to the database;
- Structure the application into services and controllers;
- Use parameterized queries to prevent SQL injections.

## Prerequisites

- Node.js and npm must be installed on your computer.
- A MySQL server must be running, and a database must be created.

## Step 1: Setting Up the Project

Create a new Node.js project and install the required dependencies.

### 1.1. Creating a Node.js Project

```bash
mkdir myapp
cd myapp
npm init -y
```

### 1.2. Installing Required Dependencies

Install the `express` and `mysql2` modules.

```bash
npm install express mysql2
```

## Step 2: Structuring the Project

Create the following directory structure:

```text
myapp/
├── controllers/
│   └── userController.js
├── services/
│   └── userService.js
├── db.js
├── index.js
└── package.json
```

### 2.1. Configuring the Connection

Create the `db.js` file, where we configure and establish the MySQL database connection.

```javascript
// db.js
const mysql = require("mysql2");

// Create a connection pool to allow multiple connections
const pool = mysql.createPool({
  host: "localhost",
  user: "root",
  password: "password",
  database: "blog",
});

// Enable promise support for the connection pool
const promisePool = pool.promise();

module.exports = promisePool;
```

Make sure to adjust `host`, `user`, `password`, and `database` according to your database settings.

### 2.2. Creating Services

Create the `userService.js` file, where we handle interactions with the database.

```javascript
// services/userService.js
const db = require("../db");

const getAllUsers = async () => {
  const [rows] = await db.query("SELECT * FROM users");
  return rows;
};

const getUserById = async (id) => {
  const [rows] = await db.query("SELECT * FROM users WHERE id = ?", [id]);
  return rows[0];
};

const createUser = async (username, email, password) => {
  const [result] = await db.query(
    "INSERT INTO users (username, email, password) VALUES (?, ?, ?)",
    [username, email, password]
  );
  return result.insertId;
};

const updateUser = async (id, username, email, password) => {
  const [result] = await db.query(
    "UPDATE users SET username = ?, email = ?, password = ? WHERE id = ?",
    [username, email, password, id]
  );
  return result.affectedRows;
};

const deleteUser = async (id) => {
  const [result] = await db.query("DELETE FROM users WHERE id = ?", [id]);
  return result.affectedRows;
};

module.exports = {
  getAllUsers,
  getUserById,
  createUser,
  updateUser,
  deleteUser,
};
```

### 2.3. Creating Controllers

Create the `userController.js` file, where we handle API endpoints.

```javascript
// controllers/userController.js
const userService = require("../services/userService");

const getUsers = async (req, res) => {
  try {
    const users = await userService.getAllUsers();
    res.status(200).json(users);
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
};

const getUser = async (req, res) => {
  try {
    const user = await userService.getUserById(req.params.id);
    if (!user) {
      return res.status(404).json({ error: "User not found" });
    }
    res.status(200).json(user);
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
};

const createUser = async (req, res) => {
  const { username, email, password } = req.body;
  try {
    const id = await userService.createUser(username, email, password);
    res.status(201).json({ id });
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
};

const updateUser = async (req, res) => {
  const { id } = req.params;
  const { username, email, password } = req.body;
  try {
    const affectedRows = await userService.updateUser(
      id,
      username,
      email,
      password
    );
    if (affectedRows === 0) {
      return res.status(404).json({ error: "User not found" });
    }
    res.status(200).json({ message: "User updated successfully" });
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
};

const deleteUser = async (req, res) => {
  const { id } = req.params;
  try {
    const affectedRows = await userService.deleteUser(id);
    if (affectedRows === 0) {
      return res.status(404).json({ error: "User not found" });
    }
    res.status(200).json({ message: "User deleted successfully" });
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
};

module.exports = {
  getUsers,
  getUser,
  createUser,
  updateUser,
  deleteUser,
};
```

### 2.4. Creating the Express Server

Create the `index.js` file, where we configure the Express server and connect the controllers.

```javascript
// index.js
const express = require("express");
const app = express();
const userController = require("./controllers/userController");

// Middleware for handling JSON requests
app.use(express.json());

// Basic route
app.get("/", (req, res) => {
  res.send("Hello World!");
});

// API endpoints
app.get("/users", userController.getUsers);
app.get("/users/:id", userController.getUser);
app.post("/users", userController.createUser);
app.put("/users/:id", userController.updateUser);
app.delete("/users/:id", userController.deleteUser);

// Start the server
const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});
```

## SQL Injection and Parameterized Queries

### What is SQL Injection?

SQL injection is an attack where a malicious user can input SQL code that alters the logic of queries and the structure of the database, potentially stealing data or compromising the system. It is one of the most common security risks in web applications.

### Parameterized Queries

Parameterized queries allow separating SQL code from user input, making it harder for SQL injection attacks to succeed.

#### Example: Using Parameterized Queries

All service queries already use parameters. We use the `?` symbol along with an array of arguments to securely insert user data into the query.

```javascript
const createUser = async (username, email, password) => {
  const [result] = await db.query(
    "INSERT INTO users (username, email, password) VALUES (?, ?, ?)",
    [username, email, password]
  );
  return result.insertId;
};
```

Using parameterized queries ensures that user input is handled safely, preventing SQL injection attacks.
