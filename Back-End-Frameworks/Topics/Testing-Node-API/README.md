# Node API Testing with Supertest, Mocha, and Chai: Running and Testing the Application

API testing is essential to ensure that the endpoints of your application are functioning correctly. In this tutorial, we'll discuss how to set up and test a Node.js API using Express with Supertest, Mocha, and Chai. First, we’ll separate the Express application logic and server startup into different files (`app.js` and `server.js`), which simplifies testing. Then, we’ll write and run tests to check various API endpoints.

![Node API Testing](Node-API-Testing.webp)

Image source: Dall-E by OpenAI

- [Node API Testing with Supertest, Mocha, and Chai: Running and Testing the Application](#node-api-testing-with-supertest-mocha-and-chai-running-and-testing-the-application)
  - [Learning Outcomes](#learning-outcomes)
  - [Project Structure](#project-structure)
  - [Setting Up the API](#setting-up-the-api)
    - [`app.js`](#appjs)
    - [`server.js`](#serverjs)
    - [`routes/posts.js`](#routespostsjs)
    - [`controllers/postsController.js`](#controllerspostscontrollerjs)
    - [`services/postsService.js`](#servicespostsservicejs)
  - [Writing Tests with Supertest, Mocha, and Chai](#writing-tests-with-supertest-mocha-and-chai)
    - [Creating the Test File](#creating-the-test-file)
    - [Writing the Tests](#writing-the-tests)
      - [`test/posts.test.js`](#testpoststestjs)
    - [Running the Tests](#running-the-tests)
  - [Checking Test Coverage](#checking-test-coverage)
    - [`nyc` Installation](#nyc-installation)
    - [`nyc` Setup](#nyc-setup)

## Learning Outcomes

By the end of this tutorial, students should be able to:

- Set up the Express application and server startup in separate files for easier testing.
- Test API endpoints using Supertest, Mocha, and Chai.
- Check test coverage using the `nyc` tool.

## Project Structure

```text
my-blog-api/
│
├── app.js          # Express app configuration
├── server.js       # Server startup
├── routes/
│   └── posts.js    # Defining API endpoints
├── controllers/
│   └── postsController.js  # Controllers for handling endpoints
└── services/
    └── postsService.js     # Services for business logic and data operations
└── test/
    └── posts.test.js       # Tests for the endpoints
└── package.json    # Project configuration and dependencies
```

## Setting Up the API

### `app.js`

Before we can write (or run) tests, we need to set up the Express application so that we can test it. To do this, we’ll separate the app and server startup into different files.

In `app.js`, we configure the Express application and the routers. This file contains all the application logic and configuration but doesn’t start the server.

```javascript
const express = require("express");
const postsRouter = require("./routes/posts");

const app = express();

// Middleware for handling JSON requests
app.use(express.json());

// Use the posts routes
app.use("/posts", postsRouter);

module.exports = app;
```

### `server.js`

The `server.js` file is responsible for starting the server. Here, we import the Express application defined in `app.js` and start it.

```javascript
const app = require("./app"); // Import the Express app
const PORT = process.env.PORT || 3000;

// Start the server
app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});
```

### `routes/posts.js`

We define the API endpoints and link them to the controllers in the `postsController.js` file.

```javascript
const express = require("express");
const router = express.Router();
const postsController = require("../controllers/postsController");

// Define the endpoints and link them to the controllers
router.get("/", postsController.getAllPosts);
router.post("/", postsController.createPost);
router.put("/:id", postsController.updatePost);
router.delete("/:id", postsController.deletePost);

module.exports = router;
```

### `controllers/postsController.js`

Controllers are responsible for handling HTTP requests and returning responses. They use services (`postsService.js`) to perform business logic and data operations.

```javascript
const postsService = require("../services/postsService");

// Get all posts
exports.getAllPosts = (req, res) => {
  const posts = postsService.getAllPosts();
  res.json(posts);
};

// Create a new post
exports.createPost = (req, res) => {
  const newPost = postsService.createPost(req.body);
  res.status(201).json(newPost);
};

// Update a post
exports.updatePost = (req, res) => {
  const updatedPost = postsService.updatePost(
    parseInt(req.params.id),
    req.body
  );
  if (updatedPost) {
    res.json(updatedPost);
  } else {
    res.status(404).send("Post not found");
  }
};

// Delete a post
exports.deletePost = (req, res) => {
  const deleted = postsService.deletePost(parseInt(req.params.id));
  if (deleted) {
    res.status(204).send();
  } else {
    res.status(404).send("Post not found");
  }
};
```

### `services/postsService.js`

Services handle business logic and data operations. They provide functions that controllers use.

```javascript
let posts = [
  { id: 1, title: "First Post", content: "This is the first post" },
  { id: 2, title: "Second Post", content: "This is the second post" },
];

// Get all posts
exports.getAllPosts = () => {
  return posts;
};

// Create a new post
exports.createPost = (postData) => {
  const newPost = {
    id: posts.length + 1,
    title: postData.title,
    content: postData.content,
  };
  posts.push(newPost);
  return newPost;
};

// Update a post
exports.updatePost = (postId, postData) => {
  const postIndex = posts.findIndex((post) => post.id === postId);
  if (postIndex !== -1) {
    posts[postIndex] = {
      id: postId,
      title: postData.title,
      content: postData.content,
    };
    return posts[postIndex];
  }
  return null;
};

// Delete a post
exports.deletePost = (postId) => {
  const postIndex = posts.findIndex((post) => post.id === postId);
  if (postIndex !== -1) {
    posts.splice(postIndex, 1);
    return true;
  }
  return false;
};
```

## Writing Tests with Supertest, Mocha, and Chai

Now that the app and server startup are separated, we can write and run tests without the server starting up.

Before we begin writing the tests, let’s install the necessary libraries and frameworks for testing:

```bash
npm install --save-dev mocha chai@4.4.1 supertest
```

> Note: We are using Chai version 4.4.1 because it is the latest version that supports Node.js `require` syntax.

Let’s also add a script to run the tests in the `package.json` file:

```json
{
  "scripts": {
    "test": "mocha  --exit"
  }
}
```

### Creating the Test File

Create the `test` directory and the `posts.test.js` file.

```bash
mkdir test
touch test/posts.test.js
```

### Writing the Tests

#### `test/posts.test.js`

```javascript
const request = require("supertest");
const chai = require("chai");
const app = require("../app"); // Import the Express app
const expect = chai.expect;

describe("Blog API", function () {
  // Test group

  describe("GET /posts", function () {
    // Single test
    it("should return all posts", async function () {
      const response = await request(app).get("/posts"); // Send request to /posts endpoint
      expect(response.status).to.equal(200); // Check that the response status is 200
      expect(response.body).to.be.an("array"); // Check that the response is an array
      expect(response.body.length).to.be.greaterThan(0); // Check that the array has more than 0 items
    });
  });

  describe("POST /posts", function () {
    it("should create a new post", async function () {
      const newPost = {
        title: "New Post",
        content: "This is a new post",
      };
      const response = await request(app).post("/posts").send(newPost);
      expect(response.status).to.equal(201);
      expect(response.body).to.include.keys("id", "title", "content");
      expect(response.body.title).to.equal(newPost.title);
    });
  });

  describe("PUT /posts/:id", function () {
    it("should update an existing post", async function () {
      const updatedPost = {
        title: "Updated Post",
        content: "This is an updated post",
      };
      const response = await request(app).put("/posts/1").send(updatedPost);
      expect(response.status).to.equal(200);
      expect(response.body).to.include.keys("id", "title", "content");
      expect(response.body.title).to.equal(updatedPost.title);
    });
  });

  describe("DELETE /posts/:id", function () {
    it("should delete an existing post", async function () {
      const response = await request(app).delete("/posts/1");
      expect(response.status).to.equal(204);
    });
  });
});
```

### Running the Tests

Run the tests using Mocha from the command line.

```bash
npm test
```

## Checking Test Coverage

We can check how much of the code is covered by tests using the `nyc` tool.

### `nyc` Installation

Install `nyc` using npm.

```bash
npm install --save-dev nyc
```

### `nyc` Setup

Add the following configuration to the `package.json` file:

```json
{
  "scripts": {
    "test": "nyc mocha --exit"
  },
  "nyc": {
    "reporter": ["text", "html"],
    "exclude": ["test/**"]
  }
}
```

Run the tests with `nyc` to view the coverage.

```bash
npm test
```

This command will generate a coverage report and display the results in the terminal. Additionally, you can find the HTML report in the `coverage` directory, which you can open in a web browser for a detailed overview of code coverage.
