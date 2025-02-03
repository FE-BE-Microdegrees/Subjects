# Props in React

Props (short for "properties") are a fundamental concept in React that enable data transfer between components. Props allow components to be **dynamic and reusable**, as they can receive and utilize external values. This chapter covers the basics of props, how to use them, and best practices.

![React Props](React-Props.webp)

Image source: Dall-E by OpenAI

- [Props in React](#props-in-react)
  - [Learning Outcomes](#learning-outcomes)
  - [What are Props?](#what-are-props)
    - [Using Props](#using-props)
      - [Example: Functional Component Using Props](#example-functional-component-using-props)
    - [Using Props in a Class-Based Component](#using-props-in-a-class-based-component)
      - [Example: Class-Based Component Using Props](#example-class-based-component-using-props)
    - [Passing Props](#passing-props)
      - [Example: Passing Props](#example-passing-props)
    - [Default Props](#default-props)
      - [Example: Default Props](#example-default-props)
    - [Validating Prop Types with PropTypes](#validating-prop-types-with-proptypes)
      - [Example: Using PropTypes](#example-using-proptypes)
      - [Example: Required Props](#example-required-props)
    - [Best Practices for Props](#best-practices-for-props)
  - [Resources](#resources)
  - [Review Questions or Exercises](#review-questions-or-exercises)
  - [Exercise](#exercise)

## Learning Outcomes

By the end of this chapter, students should be able to:

- Explain what props are and how they are used in React.
- Create components that receive and use props.
- Pass data from parent to child components using props.
- Use `PropTypes` to validate component props.

## What are Props?

Props are **read-only** data passed from a **parent component** to a **child component**. Props allow components to be dynamic and reusable because they receive values from external sources.

### Using Props

Props are passed to components similarly to HTML attributes.

#### Example: Functional Component Using Props

```javascript
import React from "react";

function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

export default Greeting;
```

The parent component can pass a `name` prop to the `Greeting` component like this:

```javascript
import React from "react";
import Greeting from "./Greeting";

function App() {
  return (
    <div>
      <Greeting name="John" />
      <Greeting name="Jane" />
    </div>
  );
}

export default App;
```

### Using Props in a Class-Based Component

Props can also be accessed in **class-based components** using `this.props`.

#### Example: Class-Based Component Using Props

```javascript
import React, { Component } from "react";

class Greeting extends Component {
  render() {
    return <h1>Hello, {this.props.name}!</h1>;
  }
}

export default Greeting;
```

The parent component can pass a `name` prop to the `Greeting` component like this:

```javascript
import React from "react";
import Greeting from "./Greeting";

class App extends React.Component {
  render() {
    return (
      <div>
        <Greeting name="John" />
        <Greeting name="Jane" />
      </div>
    );
  }
}

export default App;
```

### Passing Props

Props enable **data transfer between components**, allowing a hierarchical data flow. Sometimes, props are passed through multiple levels, a pattern known as **prop drilling**.

#### Example: Passing Props

```javascript
import React from "react";

function Grandchild(props) {
  return <h1>Hello, {props.name}!</h1>;
}

function Child(props) {
  return <Grandchild name={props.name} />;
}

function Parent() {
  return <Child name="John" />;
}

export default Parent;
```

### Default Props

You can define **default props** for components in case the parent component does not provide them.

#### Example: Default Props

```javascript
import React from "react";

function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

Greeting.defaultProps = {
  name: "Stranger",
};

export default Greeting;
```

### Validating Prop Types with PropTypes

React provides the `PropTypes` library to **validate the types of props**. This ensures that components receive the correct prop types and helps catch errors during development.

#### Example: Using PropTypes

```javascript
import React from "react";
import PropTypes from "prop-types";

function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

Greeting.propTypes = {
  name: PropTypes.string,
};

export default Greeting;
```

#### Example: Required Props

```javascript
Greeting.propTypes = {
  name: PropTypes.string.isRequired,
};
```

### Best Practices for Props

- **Use descriptive names:** Give props names that clearly indicate their purpose.
- **Set default values:** Use `defaultProps` to ensure props have a default value when not provided.
- **Validate props:** Use `PropTypes` to enforce correct prop types and catch potential errors.
- **Avoid unnecessary prop drilling:** If props need to be passed down multiple levels, consider using **Context API** or **state management libraries**.

## Resources

- [React Documentation](https://react.dev/)
- [JavaScript Front-End Frameworks and Libraries](https://www.javascriptstuff.com/)

## Review Questions or Exercises

- What are props, and how do they differ from state?
- How do you use props in functional components?
- How do you use props in class-based components?
- How can you set default props?
- How can you use `PropTypes` to validate props?

## Exercise

- Create a new React project using **Create React App**.
- Build a **functional component** that receives and displays a prop.
- Build a **class-based component** that receives and displays a prop.
- Define default props and demonstrate how they are applied.
- Use `PropTypes` to validate prop types and ensure the component receives the correct prop type.
- Implement **prop drilling** by passing props through multiple components to demonstrate hierarchical data flow.
