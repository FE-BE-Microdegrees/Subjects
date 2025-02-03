# Pagination in React

Pagination is a technique that allows you to split a large dataset into smaller pages, making the display and management of data more user-friendly. In this tutorial, we'll explore how to implement pagination in a React application using **React Bootstrap**.

![React Pagination](React-Pagination.webp)

Image source: Dall-E by OpenAI

- [Pagination in React](#pagination-in-react)
  - [Learning Outcomes](#learning-outcomes)
  - [Introduction to Pagination](#introduction-to-pagination)
  - [Example: Pagination in React with React Bootstrap](#example-pagination-in-react-with-react-bootstrap)
    - [Creating and Setting Up the Project](#creating-and-setting-up-the-project)
  - [Application Components](#application-components)
    - [App.js](#appjs)
    - [PaginationComponent.js](#paginationcomponentjs)
  - [Explanations](#explanations)
  - [Review Questions](#review-questions)
  - [Exercise](#exercise)
  - [References](#references)

## Learning Outcomes

After completing this section, you should be able to:

- explain what pagination is and why it is used;
- create and implement a pagination component in React;
- integrate pagination with React Bootstrap components.

## Introduction to Pagination

Pagination is useful when you need to display a large amount of data but don't want to load and display all of it at once. Instead, the data is divided into pages, and users can navigate between these pages.

## Example: Pagination in React with React Bootstrap

Let's create a simple React application that displays a list of items and uses pagination to navigate between them.

### Creating and Setting Up the Project

1. **Create a new React project**:

   ```bash
   npx create-react-app react-pagination-example
   cd react-pagination-example
   ```

2. **Install React Bootstrap**:

   ```bash
   npm install react-bootstrap bootstrap
   ```

3. **Add Bootstrap styles to the `index.js` file**:

   ```javascript
   // index.js
   import "bootstrap/dist/css/bootstrap.min.css";
   ```

## Application Components

Create the following components in the app:

1. **App.js**: The main component that contains the list and pagination component.
2. **PaginationComponent.js**: The component that handles the pagination logic.

### App.js

```javascript
// App.js
import React, { useState } from "react";
import { Container, Row, Col, Card } from "react-bootstrap";
import PaginationComponent from "./PaginationComponent";

const data = Array.from({ length: 100 }, (_, i) => `Item ${i + 1}`);

const App = () => {
  const [currentPage, setCurrentPage] = useState(1);
  const itemsPerPage = 10;

  // Calculate the current page's data
  const indexOfLastItem = currentPage * itemsPerPage;
  const indexOfFirstItem = indexOfLastItem - itemsPerPage;
  const currentItems = data.slice(indexOfFirstItem, indexOfLastItem);

  return (
    <Container>
      <Row>
        {currentItems.map((item, index) => (
          <Col key={index} md={4} className="mb-4">
            <Card>
              <Card.Body>
                <Card.Title>{item}</Card.Title>
              </Card.Body>
            </Card>
          </Col>
        ))}
      </Row>
      <PaginationComponent
        itemsPerPage={itemsPerPage}
        totalItems={data.length}
        currentPage={currentPage}
        onPageChange={(pageNumber) => setCurrentPage(pageNumber)}
      />
    </Container>
  );
};

export default App;
```

### PaginationComponent.js

```javascript
// PaginationComponent.js
import React from "react";
import { Pagination } from "react-bootstrap";

const PaginationComponent = ({
  itemsPerPage,
  totalItems,
  currentPage,
  onPageChange,
}) => {
  const pageNumbers = [];

  for (let i = 1; i <= Math.ceil(totalItems / itemsPerPage); i++) {
    pageNumbers.push(i);
  }

  return (
    <Pagination>
      <Pagination.First
        onClick={() => onPageChange(1)}
        disabled={currentPage === 1}
      />
      <Pagination.Prev
        onClick={() => onPageChange(currentPage - 1)}
        disabled={currentPage === 1}
      />
      {pageNumbers.map((number) => (
        <Pagination.Item
          key={number}
          active={number === currentPage}
          onClick={() => onPageChange(number)}
        >
          {number}
        </Pagination.Item>
      ))}
      <Pagination.Next
        onClick={() => onPageChange(currentPage + 1)}
        disabled={currentPage === pageNumbers.length}
      />
      <Pagination.Last
        onClick={() => onPageChange(pageNumbers.length)}
        disabled={currentPage === pageNumbers.length}
      />
    </Pagination>
  );
};

export default PaginationComponent;
```

## Explanations

- **App.js**: This component holds the current page state and determines which items are displayed on the current page.

  - **data**: Sample data that is displayed across pages.
  - **currentPage**: A state variable that tracks the current page.
  - **indexOfLastItem** and **indexOfFirstItem**: Calculate which items belong to the current page.
  - **PaginationComponent**: We use this component to handle page navigation.

- **PaginationComponent.js**: This component is responsible for displaying the pagination buttons and triggering events.
  - **pageNumbers**: An array containing all the page numbers.
  - **Pagination**: The React Bootstrap `Pagination` component that contains navigation buttons.

## Review Questions

1. What is pagination and when is it useful?
2. How do you determine which items are displayed on the current page?
3. How do you use the React Bootstrap pagination component?

## Exercise

- **Create an app that displays a list of data with pagination**: Use the example above to build your own React app that displays a list of data and allows users to navigate through the pages.
- **Customize the pagination styles**: Try modifying the pagination component to match the design of your app.

## References

- [React Bootstrap Documentation](https://react-bootstrap.github.io/docs/components/pagination)
- [React Documentation - Lists and Keys](https://react.dev/learn/rendering-lists)
- [React Pagination Tutorial](https://www.freecodecamp.org/news/build-a-custom-pagination-component-in-react/)
