# Variables

## Description

- What is?
- How to declare?
- How to assign?
- Data types

## Learning Outcomes

After completing this topic, you'll be able to:
- Define what a variable is
- Declare variables
- Assign values to variables
- Explain the difference between `var`, `let`, and `const`

## What is a Variable?

A variable is a named storage location in a computer's memory that can be used to store data. Variables are used to store values that can be changed during the execution of a program. For example, a variable named `x` can be used to store the value `5`. The value of `x` can be changed to `10` by assigning the value `10` to `x`. Variables are used to store data that can be used later in the program.

We can imagine a variable as a box with label on it (variable name) that can hold something (value). We can put something in the box (assign a value) and we can take something out of the box (use the value).

## How to Declare a Variable?

In order to use a variable in a program, we must first declare it. In Javascript, we can declare a variable using the `var`, `let`, or `const` keywords.
- The `var` keyword is used to declare a variable that can be reassigned, but we should avoid using `var` nowadays and use `let` instead.
- The `let` keyword is used to declare a variable that can be reassigned.
- The `const` keyword is used to declare a variable that cannot be reassigned.

```javascript
let firstName; // declare a variable named x
let age, lastName; // declare multiple variables 
```

In previous example, we declared variables named `firstName`, `age`, and `lastName`. We can also declare variables and assign values to them at the same time.

## Assigning Values to Variables

We can assign values to variables using the assignment operator `=`. The value on the right side of the assignment operator is assigned to the variable on the left side of the assignment operator.

```javascript
let firstName = 'John'; // declare a variable named firstName and assign the value 'John' to it
let age = 25, lastName = 'Doe'; // declare multiple variables and assign values to them
const PI = 3.14; // declare a constant named PI and assign the value 3.14 to it
```

## Data Types

As we can see in the previous examples, we can assign different types of values to variables. In Javascript, there are 7 primitive data types:

- `string`: a sequence of characters enclosed in single or double quotes
- `number`: a numeric value
- `boolean`: a value that is either `true` or `false`
- `null`: a value that represents nothing
- `undefined`: a value that represents the absence of a value
- `symbol`: a unique value that is used to identify object properties
- `bigint`: a numeric value that is larger than the `Number.MAX_SAFE_INTEGER` value

```javascript
let firstName = 'John'; // string
let age = 25; // number
let isMarried = false; // boolean
let car = null; // null
let x; // undefined
let symbol = Symbol('symbol'); // symbol
let bigInt = 9007199254740991n; // bigint
```
