# Callback Function

![Callback Function](Callback.webp)

Image Source: Dall-E by OpenAI

- [Callback Function](#callback-function)
  - [Learning Outcomes](#learning-outcomes)
  - [What is a Callback Function?](#what-is-a-callback-function)
  - [Why are Callback Functions Used in Node.js?](#why-are-callback-functions-used-in-nodejs)
    - [Example: Synchronous File Reading](#example-synchronous-file-reading)
    - [Example: Asynchronous File Reading](#example-asynchronous-file-reading)

## Learning Outcomes

After completing this topic, you will:

- Be able to explain what a _Callback_ function is
- Understand why _Callback_ functions are used in Node.js
- Be able to use _Callback_ functions in Node.js

## What is a Callback Function?

A _Callback_ function is a function passed as an argument to another function, which is then executed inside the outer function to complete a specific task.

## Why are Callback Functions Used in Node.js?

Node.js has an asynchronous nature, making _Callback_ functions essential. For example, when reading a file from the disk, the operation takes time, but the program execution continues. Using a _Callback_ function allows an action to be triggered once the file reading is completed. Most Node.js modules are designed to support _Callback_ functions.

### Example: Synchronous File Reading

Consider reading a file `input.txt` synchronously as shown below:

`input.txt`:

```bash
Hello world!
```

```javascript
const fs = require("fs");
const data = fs.readFileSync("input.txt", { encoding: "utf8" });

console.log(data); // Displays the file content
console.log("Program Ended");
```

Here, the program blocks execution until the file is read, which is undesirable. The console output would look like this:

```bash
Hello world!
Program Ended
```

> `input.txt` and `{ encoding: 'utf8' }` are arguments to the `readFileSync` function, where the first specifies the file name and the second specifies the file's encoding.

### Example: Asynchronous File Reading

Instead, if we read the file asynchronously, it would look like this:

```javascript
const fs = require("fs");

// In addition to the previous arguments, an anonymous function is added
fs.readFile("input.txt", { encoding: "utf8" }, function (err, data) {
  if (err) return console.error(err);
  return console.log(data.toString());
});

console.log("Program Ended");
```

In this case, the program continues executing while the file is being read, and the Callback function is executed once the file reading is complete.

Console output:

```bash
Program Ended
Hello world!
```

For clarity, the above example can also be rewritten as:

```javascript
const fs = require("fs");

function callback(err, data) {
  if (err) return console.error(err);
  return console.log(data);
}

// A function name is passed as an argument without parentheses
fs.readFile("input.txt", { encoding: "utf8" }, callback);

console.log("Program Ended");
```

> Note that in the first example, the `readFileSync` function (synchronous) is used, while in the other cases, the asynchronous `readFile` function is used.

Sources:

- <https://developer.mozilla.org/en-US/docs/Glossary/Callback_function>
- <https://www.geeksforgeeks.org/node-js-callback-concept/>
