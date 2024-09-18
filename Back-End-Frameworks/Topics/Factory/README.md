# Factory Design Pattern

The _Factory_ design pattern is a creational pattern. A "factory" is a superclass whose subclasses can influence which parameters are used to create an object. The factory superclass does two things:

- creates objects using a **hidden** superclass method
- refers to the created object through a **common** interface

The goal is to reduce code and minimize technical debt. Mainly, it should reduce the creation of new objects using the `new` keyword, for example:

```js
const bear = new Bear();
const parrot = new Parrot();
const goldfish = new Goldfish();
// etc.
```

---

## Use Case

The factory design pattern addresses problems that arise when object creation becomes complex or depends on dynamic conditions. This pattern separates the logic of creating objects from their usage, allowing the system to be more flexible and easier to maintain.

Three components in the Factory pattern:

1. **Product**: The object being created, which has a common interface, hidden from the client.
2. **Factory**: The class that contains the method for creating objects, typically hidden from the client.
3. **Client**: The class that uses the factory to create objects. This is the part that utilizes the factory.

---

## Example

### Cat Superclass ("Product" Component)

```js
// Superclass for a common interface
class Cat {
  constructor(name, age, color) {
    this.name = name;
    this.age = age;
    this.color = color;
  }
  introduce() {
    console.log(
      `My cat's name is ${this.name}, he is ${this.age} years old, and his fur color is ${this.color}.`
    );
  }
}
```

### Factory Class ("Factory" Component)

```js
class CatFactory {
  createCat(name, age, color) {
    // Factories should always contain at least a 'create()' method.
    return new Cat(name, age, color);
  }
}
```

The factory can also be implemented as a function, yielding the same result.

```js
function CatFactory(name, age, color) {
  return new Cat(name, age, color);
}
```

### Using the Factory ("Client" Component)

```js
const factory = new CatFactory();
const myCat = factory.createCat("Tom", 3, "gray");
const myOtherCat = factory.createCat("Max", 2, "white");
myCat.introduce(); // My cat's name is Tom, he is 3 years old, and his fur color is gray.
myOtherCat.introduce(); // My cat's name is Max, he is 2 years old, and his fur color is white.
```

---

## More Complex Example

In the previous example, we dealt only with cats. Now, let’s modify things to accommodate both cats and dogs.

### Product

```js
// Superclass for a common interface
class Animal {
  constructor(name, age, color, type) {
    this.name = name;
    this.age = age;
    this.color = color;
    this.type = type; // Adding the type of animal
  }
  introduce() {
    console.log(
      `My pet's name is ${this.name}, he is ${this.age} years old, and he is ${this.color} in color.`
    );
  }
  logActivity() {
    console.log(
      `Animal type: ${this.type}, activity: ${this.currentActivity()}`
    );
  }
  currentActivity() {
    return "Normal activity";
  }
}
```

### Subclasses

In comparison to the previous example, we now add subclasses to the _Animal_ class. This allows us to add unique properties as needed.

```js
class Cat extends Animal {
  constructor(name, age, color) {
    super(name, age, color, "Cat"); // Setting the type immediately since this class corresponds to that animal
  }
  currentActivity() {
    return "Playing with a toy mouse";
  }
}

class Dog extends Animal {
  constructor(name, age, color) {
    super(name, age, color, "Dog");
  }
  currentActivity() {
    return "Running around outside";
  }
}
```

### Factory

Here, I also add the _'type'_, which distinguishes between the two animals being created.

```js
class AnimalFactory {
  createAnimal(type, name, age, color) {
    if (type === "Cat") {
      return new Cat(name, age, color);
    } else if (type === "Dog") {
      return new Dog(name, age, color);
    } else {
      throw new Error("Invalid animal type"); // Our factory currently does not support other animals.
    }
  }
}
```

### Client

```js
const factory = new AnimalFactory();
const myCat = factory.createAnimal("Cat", "Tom", 3, "gray");
const myDog = factory.createAnimal("Dog", "Rex", 5, "brown");

myCat.introduce();
myDog.introduce();

myCat.logActivity(); // Animal type: Cat, activity: Playing with a toy mouse
myDog.logActivity(); // Animal type: Dog, activity: Running around outside
```

---

## Exercise

**Description**: The code must save company employees in a database. The database describes employees with three properties: name, job, and management level.

**Tasks**: Create a Product, a Factory for producing the product, and create objects through the factory into a "database" (the database here is an empty array `[]`).

**Expected Output**: The result of `console.log(database)` should be:

```json
[
  { "name": "John", "job": "Team lead", "level": "Senior" },
  { "name": "Mary", "job": "Developer", "level": "Junior" },
  { "name": "Juku", "job": "Tester", "level": "Intern" }
]
```

---

**Sources**:

- [Oodesign - factory pattern](https://www.oodesign.com/factory-pattern)
- [Refactoring Guru - factory method](https://refactoring.guru/design-patterns/factory-method)

**Author: Taavi Ansper**

## Factory Design Pattern Using a Functional Approach

The `Factory` design pattern can also be effectively utilized using a functional approach. The simplest way is to create a function that returns a new object. For example:

```js
function createCat(name, age, color) {
  return {
    name,
    age,
    color,
    introduce() {
      console.log(
        `My cat's name is ${this.name}, he is ${this.age} years old, and his fur color is ${this.color}.`
      );
    },
  };
}

const myCat = createCat("Tom", 3, "gray");
myCat.introduce(); // My cat's name is Tom, he is 3 years old, and his fur color is gray.
```
