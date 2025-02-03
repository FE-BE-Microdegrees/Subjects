# React and Axios: Fetching and Displaying Data

React is a popular JavaScript library for building user interfaces, while Axios is a **promise-based HTTP client** used for fetching and sending data. Together, these tools allow developers to create **dynamic and data-driven web applications**. In this tutorial, we will cover how to install and set up Axios in a React project, fetch data from an external API, and display the retrieved data.

![React and Axios](React-Axios.webp)

Image source: Dall-E by OpenAI

- [React and Axios: Fetching and Displaying Data](#react-and-axios-fetching-and-displaying-data)
  - [Learning Outcomes](#learning-outcomes)
  - [Prerequisites](#prerequisites)
  - [Step 1: Setting Up the Project](#step-1-setting-up-the-project)
    - [1.1 Creating a React Project](#11-creating-a-react-project)
    - [1.2 Installing Axios](#12-installing-axios)
  - [Step 2: Fetching Data Using Axios](#step-2-fetching-data-using-axios)
    - [2.1 Creating the Component](#21-creating-the-component)
      - [Example: `UserList.js`](#example-userlistjs)
    - [Explanation](#explanation)
    - [2.2 Adding the Component to the Application](#22-adding-the-component-to-the-application)
      - [Example: `App.js`](#example-appjs)
  - [Step 3: Handling Errors and Best Practices](#step-3-handling-errors-and-best-practices)
    - [3.1 Handling Errors](#31-handling-errors)
    - [3.2 Managing Loading State](#32-managing-loading-state)
    - [3.3 Best Practices](#33-best-practices)
  - [Bonus Example: Fetching Data with Parameters](#bonus-example-fetching-data-with-parameters)
    - [4.1 Creating the Component](#41-creating-the-component)
      - [Example: `UserDetail.js`](#example-userdetailjs)
    - [4.2 Using the Component](#42-using-the-component)
      - [Example: `App.js`](#example-appjs-1)
      - [Example: `UserList.js` (Updated)](#example-userlistjs-updated)

---

## Learning Outcomes

By the end of this tutorial, learners should be able to:

- Install and configure Axios in a React project.
- Fetch data from an external API using Axios.
- Display fetched data in React components.
- Handle errors and loading states properly.

---

## Prerequisites

- Node.js and npm installed on your computer.
- Basic knowledge of React components and state management.

---

## Step 1: Setting Up the Project

### 1.1 Creating a React Project

If you don't have a React project yet, create one using Create React App.

```bash
npx create-react-app myapp
cd myapp
```

### 1.2 Installing Axios

Install the Axios module in your project.

```bash
npm install axios
```

---

## Step 2: Fetching Data Using Axios

### 2.1 Creating the Component

Create a new component that fetches data and displays it.

#### Example: `UserList.js`

```javascript
import React, { useState, useEffect } from "react";
import axios from "axios";

function UserList() {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    axios
      .get("https://jsonplaceholder.typicode.com/users")
      .then((response) => {
        setUsers(response.data);
        setLoading(false);
      })
      .catch((error) => {
        setError(error);
        setLoading(false);
      });
  }, []);

  if (loading) {
    return <p>Loading...</p>;
  }

  if (error) {
    return <p>Error: {error.message}</p>;
  }

  return (
    <div>
      <h1>User List</h1>
      <ul>
        {users.map((user) => (
          <li key={user.id}>{user.name}</li>
        ))}
      </ul>
    </div>
  );
}

export default UserList;
```

---

### Explanation

- **`useState`**: Manages state for users, loading state, and errors.
- **`useEffect`**: Fetches data from the API when the component mounts.
- **`axios.get`**: Makes a GET request to fetch data from `https://jsonplaceholder.typicode.com/users`.
- **`setUsers`**: Updates the users' state with the received data.
- **`setLoading`**: Updates the loading state.
- **`setError`**: Handles errors if the request fails.

---

### 2.2 Adding the Component to the Application

Modify the `App.js` file to display the `UserList` component.

#### Example: `App.js`

```javascript
import React from "react";
import UserList from "./UserList";

function App() {
  return (
    <div className="App">
      <UserList />
    </div>
  );
}

export default App;
```

---

## Step 3: Handling Errors and Best Practices

### 3.1 Handling Errors

The code already includes error handling. If the request fails, it updates the error state and displays an error message.

```javascript
if (error) {
  return <p>Error: {error.message}</p>;
}
```

---

### 3.2 Managing Loading State

It is important to handle loading state so users know when data is still being fetched.

```javascript
if (loading) {
  return <p>Loading...</p>;
}
```

---

### 3.3 Best Practices

- **Use the `useEffect` Hook**: Fetch data inside `useEffect` to trigger the request on component mount.
- **Error Boundaries**: Use error-handling components (`Error Boundaries`) to catch errors in components.
- **Abstraction**: Separate API calls into service files to keep code clean and reusable.

---

## Bonus Example: Fetching Data with Parameters

Let's add another example where we fetch data for a **specific user** using a parameter.

---

### 4.1 Creating the Component

Create a new component that fetches and displays data for a single user.

#### Example: `UserDetail.js`

```javascript
import React, { useState, useEffect } from "react";
import axios from "axios";

function UserDetail({ userId }) {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    axios
      .get(`https://jsonplaceholder.typicode.com/users/${userId}`)
      .then((response) => {
        setUser(response.data);
        setLoading(false);
      })
      .catch((error) => {
        setError(error);
        setLoading(false);
      });
  }, [userId]);

  if (loading) {
    return <p>Loading...</p>;
  }

  if (error) {
    return <p>Error: {error.message}</p>;
  }

  return (
    <div>
      <h1>{user.name}</h1>
      <p>Email: {user.email}</p>
      <p>Phone: {user.phone}</p>
    </div>
  );
}

export default UserDetail;
```

---

### 4.2 Using the Component

Modify `App.js` to display the `UserDetail` component.

#### Example: `App.js`

```javascript
import React, { useState } from "react";
import UserList from "./UserList";
import UserDetail from "./UserDetail";

function App() {
  const [selectedUserId, setSelectedUserId] = useState(null);

  return (
    <div className="App">
      <UserList onSelectUser={setSelectedUserId} />
      {selectedUserId && <UserDetail userId={selectedUserId} />}
    </div>
  );
}

export default App;
```

---

#### Example: `UserList.js` (Updated)

```jsx
import React, { useState, useEffect } from "react";
import axios from "axios";

function UserList({ onSelectUser }) {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    axios
      .get("https://jsonplaceholder.typicode.com/users")
      .then((response) => {
        setUsers(response.data);
        setLoading(false);
      })
      .catch((error) => {
        setError(error);
        setLoading(false);
      });
  }, []);

  if (loading) {
    return <p>Loading...</p>;
  }

  if (error) {
    return <p>Error: {error.message}</p>;
  }

  return (
    <div>
      <h1>User List</h1>
      <ul>
        {users.map((user) => (
          <li key={user.id} onClick={() => onSelectUser(user.id)}>
            {user.name}
          </li>
        ))}
      </ul>
    </div>
  );
}

export default UserList;
```
