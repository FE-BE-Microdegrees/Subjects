# React's `useEffect` Hook

The React `useEffect` hook allows you to perform side effects in functional components. It is widely used for asynchronous tasks such as data fetching, DOM updates, and timed actions. The `useEffect` hook is one of the most important hooks in React, as it helps manage component lifecycle events.

![UseEffect](UseEffect.webp)

Image source: Dall-E by OpenAI

- [React's `useEffect` Hook](#reacts-useeffect-hook)
  - [Learning Outcomes](#learning-outcomes)
  - [`useEffect` Hook Overview](#useeffect-hook-overview)
    - [`useEffect` Hook Syntax](#useeffect-hook-syntax)
  - [Examples of Using the `useEffect` Hook](#examples-of-using-the-useeffect-hook)
    - [1. Simple Use Case: Fetching Data from an API](#1-simple-use-case-fetching-data-from-an-api)
    - [2. Dependency Array: Update Based on Specific Changes](#2-dependency-array-update-based-on-specific-changes)
    - [3. Cleanup Function: Releasing Resources](#3-cleanup-function-releasing-resources)
    - [4. Timed Actions](#4-timed-actions)
  - [`useEffect` Hook Key Concepts](#useeffect-hook-key-concepts)

## Learning Outcomes

By the end of this material, learners should be able to:

- explain what the `useEffect` hook is and why it is used;
- use the `useEffect` hook to manage different side effects;
- understand how to use the `useEffect` hook with a dependency array;
- explain how and when to use the `useEffect` cleanup function.

## `useEffect` Hook Overview

The `useEffect` hook performs side effects in functional components. These side effects can include:

- fetching data from an API;
- reading or writing local storage data;
- adding and removing event listeners;
- managing timed actions like timers or intervals.

The `useEffect` hook operates in the lifecycle phases of components:

- **Mounting**: When the component is rendered and the `useEffect` hook is executed.
- **Updating**: When the component’s state or props change, and the component is re-rendered.
- **Unmounting**: When the component is removed from the DOM.

### `useEffect` Hook Syntax

```javascript
useEffect(
  () => {
    // Action to perform when the component is rendered
    return () => {
      // Cleanup action to perform when the component is unmounted or before the next action
    };
  },
  [
    /* Dependency array */
  ]
);
```

- **Action**: A function that is executed after the component renders.
- **Cleanup**: An optional function that is executed before the component unmounts or before the next action.
- **Dependency array**: An array of values. If any of these values change, the action will be re-executed.

## Examples of Using the `useEffect` Hook

### 1. Simple Use Case: Fetching Data from an API

One common use case for the `useEffect` hook is fetching data from an external API when the component is first rendered.

```javascript
import React, { useState, useEffect } from "react";

const UserList = () => {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    // Fetching data from an API
    fetch("https://jsonplaceholder.typicode.com/users")
      .then((response) => response.json())
      .then((data) => {
        setUsers(data);
        setLoading(false);
      })
      .catch((error) => {
        console.error("Error fetching data:", error);
        setLoading(false);
      });
  }, []); // Empty dependency array means this will only run once, after the first render

  if (loading) {
    return <div>Loading...</div>;
  }

  return (
    <div>
      <h2>User List</h2>
      <ul>
        {users.map((user) => (
          <li key={user.id}>{user.name}</li>
        ))}
      </ul>
    </div>
  );
};

export default UserList;
```

### 2. Dependency Array: Update Based on Specific Changes

The `useEffect` hook can be configured to execute actions only when certain values change by using the dependency array.

```javascript
import React, { useState, useEffect } from "react";

const Counter = () => {
  const [count, setCount] = useState(0);
  const [title, setTitle] = useState("React Counter");

  // This effect runs every time the 'count' changes
  useEffect(() => {
    document.title = `Count: ${count}`;
  }, [count]); // Depends only on the 'count' value

  return (
    <div>
      <h2>{title}</h2>
      <button onClick={() => setCount(count + 1)}>Increase Count</button>
      <p>Current Count: {count}</p>
      <input
        type="text"
        value={title}
        onChange={(e) => setTitle(e.target.value)}
        placeholder="Change title"
      />
    </div>
  );
};

export default Counter;
```

### 3. Cleanup Function: Releasing Resources

If a component adds an `event listener` or a timer, it should remove them when the component is unmounted or the effect runs again. The cleanup function is used to clear anything that is no longer needed.

```javascript
import React, { useState, useEffect } from "react";

const WindowWidth = () => {
  const [width, setWidth] = useState(window.innerWidth);

  useEffect(() => {
    const handleResize = () => setWidth(window.innerWidth);

    // Add event listener
    window.addEventListener("resize", handleResize);

    // Cleanup: remove event listener
    return () => {
      window.removeEventListener("resize", handleResize);
    };
  }, []); // Empty dependency array means this effect runs only once

  return (
    <div>
      <h2>Window Width: {width}px</h2>
    </div>
  );
};

export default WindowWidth;
```

### 4. Timed Actions

The `useEffect` hook can also be used for timed actions, such as intervals.

```javascript
import React, { useState, useEffect } from "react";

const Timer = () => {
  const [seconds, setSeconds] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      setSeconds((prev) => prev + 1);
    }, 1000);

    // Cleanup: clear the interval
    return () => clearInterval(interval);
  }, []); // Runs only once

  return (
    <div>
      <h2>Timer: {seconds} seconds</h2>
    </div>
  );
};

export default Timer;
```

## `useEffect` Hook Key Concepts

- **Dependency Array**: Controls when the effect runs. If it is left empty, the effect runs only once, after the first render. If it is set with specific values, the effect runs every time any of those values change.
- **Cleanup Function**: Used for releasing or cleaning up resources, such as removing event listeners or clearing timers. This function runs before the next effect or when the component unmounts.
- **Timing**: `useEffect` runs after the component renders. If you want to run code immediately before rendering, use the `useLayoutEffect` hook.
