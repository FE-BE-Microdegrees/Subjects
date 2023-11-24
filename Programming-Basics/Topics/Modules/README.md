# Modules

## Description

In this topic, we'll learn about modules in Javascript.

- What is a module?
- How to export a module?
- How to import a module?
- How to use a module?

## Learning Outcomes

After completing this topic, you'll be able to:

- Define what a module is
- Explain how to export a module
- Explain how to import a module
- Explain how to use a module

## What is a Module?

A module is a Javascript file that contains code that can be reused in other Javascript files. Modules are used to organize code into logical units that can be reused in other parts of the program. Modules are used to create reusable code that can be used in other programs.

## How to Export a Module?

In order to export a module, we need to use the `module.exports` keyword followed by the name of the module that we want to export. For example, if we want to export a module named `myModule`, we can type `module.exports myModule;` or `module.exports { myModule, myModule1 };` (if we have multiple exports) in the Javascript file where we want to export the module.

```javascript
module.exports myModule; // export a module named myModule
```
or
```javascript
module.exports { myModule, myModule1 }; // export multiple modules named myModule and myModule1
```

## How to Import a Module?

In order to import a module, we need to use the `require` keyword followed by the name of the file containing module(s) that we want to import. For example, if we want to import a module named `myModule` from file `moduleFileName.js`, we can type `require('./moduleFileName');` in the Javascript file where we want to import the module (the `./` part is used to specify the path to the file containing the module(s) that we want to import). 

```javascript
const myModule = require('./moduleFileName'); // import a module from file named `moduleFileName.js`
```
or
```javascript
import { myModule, myModule1 } from './moduleFileName'; // import multiple modules named myModule and myModule1 from the `moduleFileName.js` file
```

## How to Use a Module?

To use module, we need to import it first. After we import the module, we can use it in our code. For example, if we have file called `calculate` that contains a function named `add`, we can import the module and use the function like this:

Contents of `calculate.js` file could be something like this:

```javascript
function add(a, b) {
  return a + b;
}

function subtract(a, b) {
  return a - b;
}

module.exports = { add, subtract }; // export the add and subtract functions
```

Contents of `index.js` file could be something like this:

```javascript
const calculate = require('./calculate'); // import the calculate module

const sum = calculate.add(5, 3); // call the add function from the calculate module and assign the result to the sum variable

console.log(sum); // print the value of the sum variable to the console
```

## Example of Using Modules

In next example, we create a new file named `index.js`, create a `calculate.js` file, export the `add` and `subtract` functions from the `calculate.js` file, import the `calculate.js` file in the `index.js` file, and use the `add` function in our code.

<video src="UsingModule.mp4" controls title="Using Module"></video>