# Mocha Testing Framework

Mocha is a popular JavaScript testing framework that allows you to write and run tests in both server-side (Node.js) and client-side (browser) environments. Mocha is flexible and extensible, supporting various testing styles, including BDD (Behavior-Driven Development) and TDD (Test-Driven Development).

![Mocha](Mocha.webp)

Image source: Dall-E by OpenAI

- [Mocha Testing Framework](#mocha-testing-framework)
  - [Learning Outcomes](#learning-outcomes)
  - [What is Mocha?](#what-is-mocha)
  - [Advantages of Mocha](#advantages-of-mocha)
  - [Installing and Setting Up Mocha](#installing-and-setting-up-mocha)
    - [1. Installing Mocha](#1-installing-mocha)
      - [Global Installation](#global-installation)
      - [Project-Level Installation](#project-level-installation)
    - [2. Creating a Test File](#2-creating-a-test-file)
  - [Writing Tests with Mocha](#writing-tests-with-mocha)
    - [Example: Simple Test](#example-simple-test)
      - [`sum.js` - Function to Test](#sumjs---function-to-test)
      - [`test/test.js` - Mocha Test](#testtestjs---mocha-test)
    - [Running Tests](#running-tests)
  - [Asynchronous Tests](#asynchronous-tests)
    - [Example: Asynchronous Test with Callbacks](#example-asynchronous-test-with-callbacks)
      - [`asyncFunction.js` - Asynchronous Function](#asyncfunctionjs---asynchronous-function)
      - [`test/asyncTest.js` - Mocha Test](#testasynctestjs---mocha-test)
    - [Example: Asynchronous Test with Promises](#example-asynchronous-test-with-promises)
      - [`asyncPromise.js` - Asynchronous Function](#asyncpromisejs---asynchronous-function)
      - [`test/asyncPromiseTest.js` - Mocha Test](#testasyncpromisetestjs---mocha-test)
  - [Using Chai Assertion Library](#using-chai-assertion-library)
    - [Installing Chai](#installing-chai)
    - [Example: Using Chai](#example-using-chai)
      - [`test/chaiTest.js` - Mocha Test with Chai](#testchaitestjs---mocha-test-with-chai)
  - [Additional Mocha Features](#additional-mocha-features)
    - [Hooks](#hooks)
      - [Example: Using Hooks](#example-using-hooks)

## Learning Outcomes

By the end of this material, learners should be able to:

- explain what Mocha is and why it is used;
- install and set up the Mocha testing framework;
- write and run basic tests using Mocha;
- use assertion libraries like Chai alongside Mocha.

## What is Mocha?

Mocha is a JavaScript testing framework designed for writing and running asynchronous tests. It provides a simple and flexible way to organize and manage tests and integrates well with other tools and frameworks.

## Advantages of Mocha

- **Flexibility:** Supports various testing styles and methodologies.
- **Asynchronicity:** Easy to write and run asynchronous tests.
- **Extensibility:** Integrates well with other tools and frameworks, such as Chai and Sinon.
- **Good documentation and community:** A large user base and plenty of resources.

## Installing and Setting Up Mocha

### 1. Installing Mocha

You can install Mocha either globally or at the project level using npm.

#### Global Installation

```bash
npm install --global mocha
```

#### Project-Level Installation

```bash
npm install --save-dev mocha
```

### 2. Creating a Test File

Create a directory named `test` in the root of your project and create a test file inside it, for example, `test.js`.

```bash
mkdir test
cd test
touch test.js
```

## Writing Tests with Mocha

Mocha uses BDD style functions to write tests, including `describe`, `it`, and `before`, `after`, `beforeEach`, `afterEach`.

### Example: Simple Test

#### `sum.js` - Function to Test

```javascript
function sum(a, b) {
  return a + b;
}

module.exports = sum;
```

#### `test/test.js` - Mocha Test

```javascript
const assert = require("assert");
const sum = require("../sum");

describe("Sum Function", function () {
  it("should return 3 when the inputs are 1 and 2", function () {
    assert.strictEqual(sum(1, 2), 3);
  });

  it("should return -1 when the inputs are -2 and 1", function () {
    assert.strictEqual(sum(-2, 1), -1);
  });
});
```

### Running Tests

Run the tests using Mocha from the command line.

```bash
npx mocha
```

## Asynchronous Tests

Mocha supports writing asynchronous tests using callbacks or promises.

### Example: Asynchronous Test with Callbacks

#### `asyncFunction.js` - Asynchronous Function

```javascript
function asyncFunction(callback) {
  setTimeout(() => {
    callback(null, "Hello World");
  }, 1000);
}

module.exports = asyncFunction;
```

#### `test/asyncTest.js` - Mocha Test

```javascript
const assert = require("assert");
const asyncFunction = require("../asyncFunction");

describe("AsyncFunction", function () {
  it('should return "Hello World" after 1 second', function (done) {
    asyncFunction(function (err, result) {
      assert.strictEqual(result, "Hello World");
      done();
    });
  });
});
```

### Example: Asynchronous Test with Promises

#### `asyncPromise.js` - Asynchronous Function

```javascript
function asyncPromise() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve("Hello World");
    }, 1000);
  });
}

module.exports = asyncPromise;
```

#### `test/asyncPromiseTest.js` - Mocha Test

```javascript
const assert = require("assert");
const asyncPromise = require("../asyncPromise");

describe("AsyncPromise", function () {
  it('should return "Hello World" after 1 second', function () {
    return asyncPromise().then((result) => {
      assert.strictEqual(result, "Hello World");
    });
  });
});
```

## Using Chai Assertion Library

Chai is a popular assertion library that can be used with Mocha. Chai supports various assertion styles, including TDD and BDD.

### Installing Chai

Install Chai at the project level.

```bash
npm install --save-dev chai
```

### Example: Using Chai

#### `test/chaiTest.js` - Mocha Test with Chai

```javascript
const chai = require("chai");
const expect = chai.expect;
const sum = require("../sum");

describe("Sum Function", function () {
  it("should return 3 when the inputs are 1 and 2", function () {
    expect(sum(1, 2)).to.equal(3);
  });

  it("should return -1 when the inputs are -2 and 1", function () {
    expect(sum(-2, 1)).to.equal(-1);
  });
});
```

## Additional Mocha Features

### Hooks

Mocha provides hooks (`before`, `after`, `beforeEach`, `afterEach`) that allow you to execute code before and after tests run.

#### Example: Using Hooks

```javascript
describe("Hooks Example", function () {
  before(function () {
    // Executed before all tests
  });

  after(function () {
    // Executed after all tests
  });

  beforeEach(function () {
    // Executed before each test
  });

  afterEach(function () {
    // Executed after each test
  });

  it("test case 1", function () {
    // Test code
  });

  it("test case 2", function () {
    // Test code
  });
});
```
