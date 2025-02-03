# Error Handling in Express API

Error handling is a critical component of any API. Proper error handling not only improves the user experience but also keeps the application secure and maintainable. Express provides flexible methods for handling errors, allowing you to implement elegant and efficient error management in your API.

![Express Error Handling](Express-Error-Handling.webp)

Image source: Dall-E by OpenAI

- [Error Handling in Express API](#error-handling-in-express-api)
  - [Learning Outcomes](#learning-outcomes)
  - [Why is Error Handling Important?](#why-is-error-handling-important)
  - [Error Handling in Express](#error-handling-in-express)
    - [Custom Error Handlers in Endpoints](#custom-error-handlers-in-endpoints)
    - [Centralized Error Handling Middleware](#centralized-error-handling-middleware)
    - [Explanation](#explanation)
    - [Handling Asynchronous Errors](#handling-asynchronous-errors)
    - [Explanation](#explanation-1)
  - [Additional Methods for Handling Errors](#additional-methods-for-handling-errors)
    - [Logging Errors](#logging-errors)
    - [Handling Incorrect Requests](#handling-incorrect-requests)

## Learning Outcomes

By the end of this tutorial, students should be able to:

- Explain why error handling in Express is important.
- Implement custom error handlers in an Express API.
- Use middleware for handling errors.
- Implement a centralized error handler across the application.
- Handle asynchronous errors in Express.

## Why is Error Handling Important?

- **User Experience**: Well-designed error handling provides clear and helpful messages to users, helping them understand what went wrong and what to do next.
- **Security**: Hides internal system details and prevents leakage of sensitive information.
- **Maintainability**: Simplifies error tracking and debugging by providing developers with precise and useful logs.
- **Reliability**: Ensures that the application continues functioning even when errors occur.

## Error Handling in Express

Express allows handling errors in multiple ways, including:

1. **Custom error handlers**: Functions that handle errors for specific endpoints.
2. **Middleware (Centralized error handling)**: A global error handler that catches all errors in the application.
3. **Handling asynchronous errors**: Managing errors in asynchronous functions and promises.

### Custom Error Handlers in Endpoints

Sometimes, you need to handle errors specifically for certain endpoints. For example, if a request contains invalid input, you can return a custom error message:

```javascript
// routes/users.js
const express = require("express");
const router = express.Router();

// Example GET request that may produce an error
router.get("/:id", (req, res, next) => {
  const userId = req.params.id;

  // Check if ID is a number
  if (isNaN(userId)) {
    const error = new Error("Invalid user ID");
    error.status = 400;
    return next(error); // Pass the error to the next middleware or error handler
  }

  // Example user retrieval
  const user = { id: userId, name: "John Doe" };

  // If the user is not found
  if (!user) {
    const error = new Error("User not found");
    error.status = 404;
    return next(error);
  }

  // Return user data
  res.json(user);
});

module.exports = router;
```

### Centralized Error Handling Middleware

Express allows creating a centralized error-handling middleware that catches all errors in the application. This middleware is placed after all routes and other middleware.

```javascript
// app.js
const express = require("express");
const bodyParser = require("body-parser");
const usersRouter = require("./routes/users");

const app = express();

app.use(bodyParser.json());

app.use("/users", usersRouter);

// Central error handler
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(err.status || 500).json({
    success: false,
    message: err.message || "Internal Server Error",
  });
});

module.exports = app;
```

### Explanation

- **`app.use((err, req, res, next) => { ... })`**: This is the signature of an Express error-handling middleware. If any route or middleware calls `next(error)`, this middleware catches the error and processes it.
- **`err.status`**: The assigned error code if specified; otherwise, defaults to `500`.
- **`err.message`**: The error message returned in the response.
- **`console.error(err.stack)`**: Logs the error stack trace in the server console.

### Handling Asynchronous Errors

Asynchronous operations, such as retrieving data from an API or database, can generate errors that must be handled properly. In Express, you can use `try/catch` blocks and the `next` function to manage asynchronous errors.

```javascript
// routes/todos.js
const express = require("express");
const router = express.Router();
const todosService = require("../services/todosService");

// Example GET request using async/await
router.get("/:id", async (req, res, next) => {
  try {
    const todoId = req.params.id;

    if (isNaN(todoId)) {
      const error = new Error("Invalid todo ID");
      error.status = 400;
      throw error;
    }

    const todo = await todosService.getById(todoId);

    if (!todo) {
      const error = new Error("Todo not found");
      error.status = 404;
      throw error;
    }

    res.json(todo);
  } catch (error) {
    next(error); // Pass the error to the next middleware or error handler
  }
});

module.exports = router;
```

### Explanation

- **`try/catch` block**: Used to catch and handle errors in asynchronous operations.
- **`throw error`**: Throws errors from the `try` block to the `catch` block, which then forwards them to the Express error handler.
- **`next(error)`**: Called in the `catch` block to pass the error to the next middleware or error handler.

## Additional Methods for Handling Errors

### Logging Errors

A best practice is to log errors for future analysis and debugging. You can use logging libraries like `winston` or `morgan` to store logs in an external file or logging management system.

```javascript
const express = require("express");
const morgan = require("morgan");

const app = express();

// Morgan logs all requests
app.use(morgan("dev"));

// Your routes and middleware here

// Central error handler
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(err.status || 500).json({
    success: false,
    message: err.message || "Internal Server Error",
  });
});

module.exports = app;
```

### Handling Incorrect Requests

To avoid errors, it is good practice to add middleware that catches all incorrect requests and returns a 404 response.

```javascript
// app.js
const express = require("express");
const bodyParser = require("body-parser");
const usersRouter = require("./routes/users");

const app = express();

app.use(bodyParser.json());

app.use("/users", usersRouter);

// If no route matches, return 404
app.use((req, res, next) => {
  res.status(404).json({
    success: false,
    message: "Resource not found",
  });
});

// Central error handler
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(err.status || 500).json({
    success: false,
    message: err.message || "Internal Server Error",
  });
});

module.exports = app;
```
