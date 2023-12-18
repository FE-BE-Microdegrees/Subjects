# Data Structures

## Description

- What is data structure?
- Array
- Object

## Learning Outcomes

After completing this topic, you'll be able to:

- Define what a data structure is
- Explain what an array is
- Explain what an object is
- Use arrays and objects

## What is Data Structure?

We already know what variable is and that it is used to store data. But so far we were able to store only one value in a variable or describe only one thing. For example, we could have a variable named `firstName` that stores the first name of a person. But what if we want to store the first name, last name, age, and address of a person? We could create a variable for each of these values, but that would be very inefficient. Instead, we can use a data structure to store all of these values in one place.

A data structure is a way of organizing data in a computer's memory. Data structures are used to store collections of data. For example, we can use an **array** to store a list of numbers or a list of names. We can use an **object** to store information about a person (first name, last name, age, address, etc.). We can use a **set** to store a list of unique values. We can use a **map** to store a list of key-value pairs.

> Even though there are lot of different data structures, we'll focus on arrays and objects in this topic.

## Array

An array is a collection of values that are stored in a single variable. Arrays are used to store lists of values. Arrays are used to store collections of data that are related to each other. For example, we can use an array to store a list of numbers or a list of names.

To create an array, we use the `[]` operator. For example, we can create an array named `numbers` that contains the numbers `1`, `2`, and `3` like this:

```javascript
const numbers = [1, 2, 3];
```
Or we can create an array named `names` that contains the names `John`, `Jane`, and `Jack` like this:

```javascript
const names = ['John', 'Jane', 'Jack'];
```

We can access the values in an array using the index of the value. The index of the first value in an array is `0`. For example, if we want to access the first value in the `numbers` array, we can use the index `0` like this:

```javascript
const numbers = [1, 2, 3];

console.log(numbers[0]); // 1
```

We can also use the index of the value to change the value in the array. For example, if we want to change the value of the first value in the `numbers` array to `10`, we can use the index `0` like this:

```javascript
const numbers = [1, 2, 3];

numbers[0] = 10;

console.log(numbers); // [10, 2, 3]
```

There are lots of methods that we can use to manipulate arrays. For example, we can use the `push()` method to add a value to the end of an array, the `pop()` method to remove a value from the end of an array, the `shift()` method to remove a value from the beginning of an array, and the `unshift()` method to add a value to the beginning of an array.

All array methods are listed in the [Array Methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) section of the MDN web docs.

## Object

An object is a collection of key-value pairs that are stored in a single variable. Objects are used to store information about something. For example, we can use an object to store information about a person (first name, last name, age, address, etc.).

To create an object, we use the `{}` operator. For example, we can create an object named `person` that contains the first name `John`, the last name `Doe`, and the age `25` like this:

```javascript
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 25
};
```

We can access the values in an object using the key of the value. For example, if we want to access the first name in the `person` object, we can use the key `firstName` like this:

```javascript
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 25
};

console.log(person.firstName); // John
```

We can also use the key of the value to change the value in the object. For example, if we want to change the value of the first name in the `person` object to `Jane`, we can use the key `firstName` like this:

```javascript
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 25
};

person.firstName = 'Jane';

console.log(person); // { firstName: 'Jane', lastName: 'Doe', age: 25 }
```

As for arrays, there are lots of methods that we can use to manipulate objects also. For example, we can use the `Object.keys()` method to get an array of the keys in an object, the `Object.values()` method to get an array of the values in an object, and the `Object.entries()` method to get an array of the key-value pairs in an object.

All object methods are listed in the [Object Methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object) section of the MDN web docs.

## Exercises

TODO
