# REACT-NOTES Topic Cover
| **Sl no.** | **Topic** |
| ------- | --------| 
| 1 |  Setup and Installation of Vite+React |
| 2 | Interview Question | 
| 3 | Hooks - useState, useEffect, useMemo, useContext, useRef, useReducer, useCallback, uselayoutEffect, useImperativeHandle  | 
| 3.1 | Custom Hook | 
| 3.2 | userId Hook| 
| 4 | state and props | 
| 5 | What is JSX|
| 6 | Difference Between Class Component and Functional Component in React 🚀 |
| 7 | What is the virtual DOM? How does react use the virtual DOM to render the UI? |
| 8 | What are the differences between controlled and uncontrolled components?|
| 9 | props drilling |
| 10 | virtual DOM |
| 11 | Reconciliation|
| 12 | Statefull and Stateless component |
| 13 | Life Cycle Method |
| -14 | React Router|
| -15 | Redux |
| 16 | Error Boundries |
| 17 | Strict Mode in React. |
| 18 | Lifting State |
| 19 | React Fragmentation |

```
Handle submit = e.preventDefault();
onClick((e)= setName(e.target.name); // e is SyntheticBaseEvent.
```


## Setup and Installation of app Vite+React

```
1. go to https://tailwindcss.com/docs/guides/vite
2. create one project
 (npm create vite@latest my-project -- --template react)
 cd my-project
 npm i
 npm run dev
4. install tailwind css and config files
5. follow the instructions step
6. run and use.
npm run dev
```
## Todo Operation
### Create:
```
 const [tasks, setTasks] = useState([]);
    const addTask = title => {
        const newTasks = [...tasks, { title, completed: false }];
        setTasks(newTasks);
    };
```
### Delete
```
 const handleDelete = (index) => {
    const updatedTasks = [...array];
    updatedTasks.splice(index, 1);
    setArray(updatedTasks);
  };
```
```
const handleDelete = (index) => {
  const updatedTasks = array.filter((_, i) => i !== index);
  setArray(updatedTasks);
};
```

# Interview Question

| **Sl no.** | **Question** |
| ------- | --------| 
| 1 | Differences between controlled and uncontrolled components in React, and when would you prefer one over the other |
| 2 | "What are React Hooks, and why were they introduced? | 
| 3 | What is the difference between useEffect and useLayoutEffect in React? | 
| 4 | What is React reconciliation, and how does the virtual DOM work? | 
| 5 | What are Higher-Order Components (HOC) in React? Can you give an example of how they are used? |
| 6 | What is the difference between Context API and Redux for state management? When should you use each? |
| 7 | What are the different lifecycle methods in React class components, and how do they map to React hooks in functional components? |
---
## 1. Controlled Components:
- In controlled components, form elements (like input, textarea, select) are bound to the component’s state. The React component controls the value of the form element.
- The state is updated based on user input through event handlers.
- It gives you more control over the form data because React is managing the state of the inputs.
- The component is under control of the component state.
- Internal state is not maintained
- It accept the current value as a props.
- controlled by the parent component.

## 2. Uncontrolled Components:
- In uncontrolled components, form elements manage their own state internally, and you interact with them through refs (short for references).
- React does not directly control the value of the input, and it relies on the DOM to manage the state.
- It is often used when you need to interact with the DOM directly or when you don’t need to track the input value in the React component.
- Component is under control of the DOM.
- Internal state is maintain.
- We access the value using ref.
- controlled by the DOM itself.

## 3.1 useEffect (Runs asynchronously after render)
- Executes after the browser paints the screen.
- Used for data fetching, subscriptions, or updating the DOM without blocking rendering.
- Does not block the UI, making it good for most use cases.

## 3.2 useLayoutEffect (Runs synchronously before the browser paints)
- Executes before the browser updates the screen.
- Used when you need to measure DOM elements or make layout adjustments before the user sees the change.
- Can block rendering, so use it carefully.

## 4 Virtual DOM (VDOM)
- React maintains a lightweight copy of the real DOM called the Virtual DOM.
- Instead of updating the actual DOM directly (which is slow), React updates the Virtual DOM first.
### Reconciliation (Efficiently updating the UI)
- When state or props change, React creates a new Virtual DOM tree.
- It compares (diffs) the new Virtual DOM with the previous one.
- Only the changed elements are updated in the real DOM (not the whole page).

## 5 A Higher-Order Component (HOC):
- It is a function that takes a component as input and returns a new enhanced component. It is used for code reusability, logic sharing, and enhancing components without modifying their original structure.
### Why use HOCs?
- To reuse logic across multiple components
- To add extra functionality (e.g., authentication, logging, data fetching)
- To separate concerns and make components cleaner
- Alternative to HOCs in Modern React? => React Hooks (useContext, useEffect) are now preferred over HOCs in many cases. 

### 6
| Feature |	Context API	 | Redux |
| ---------- | ------------ | ---------- |
| Purpose | 	Avoids prop drilling for passing data	| Manages complex global state efficiently |
| Best for | 	Small to medium apps with light state management |	Large apps needing predictable state updates | 
| State Management Type |	Centralized but simple |	Centralized and structured | 
| Performance | 	Re-renders all consumers on state change (unless optimized)	| Uses a single immutable store with optimized updates |
| Boilerplate Code	 | Minimal	| More setup required (reducers, actions, store) | 
| Asynchronous Handling | 	No built-in solution (needs useReducer or external libraries like useAsync)	| Uses redux-thunk or redux-saga for handling async operations | 
| Ease of Use |	Simple and built into React |	More complex but powerful for large-scale applications |

 ### 7
- componentDidMount() → useEffect() (with an empty dependency array [])
- componentDidUpdate() → useEffect() (with dependencies)
- componentWillUnmount() → Cleanup function inside useEffect()
- shouldComponentUpdate() → Optimizing re-renders (handled by React) with React.memo() or useMemo() for memoization

--- 
# React Notes Start
## What is React?
- React is a JavaScript library for building user interfaces. It is component-based, meaning that UI elements are broken down into reusable components. React follows a declarative approach, allowing developers to efficiently update and render the UI based on state changes.
- React is unidirection data flow ( means jo top level component hota hai uske down level component ko data transfer kr skte hai).

### Key Features:
- Component-Based – UI is built using reusable components.
- Virtual DOM – Improves performance by updating only changed elements.
- State Management – Uses hooks like useState, useReducer for handling state.
- Unidirectional Data Flow – Data flows in one direction for easier debugging.
- Hooks – Allows functional components to manage state and lifecycle.

### The important features of React are:

- It supports server-side rendering.
- It will make use of the virtual DOM rather than real DOM (Data Object Model) as RealDOM manipulations are expensive.
- It follows unidirectional data binding or data flow.
- It uses reusable or composable UI components for developing the view.

# Hooks:

## What are the rules that must be followed while using React Hooks?
- There are 2 rules which must be followed while you code with Hooks:
1. React Hooks must be called only at the top level. It is not allowed to call them inside the nested functions, loops, or conditions.
2. It is allowed to call the Hooks only from the React Function Components.
3. Hooks can not be conditional ( if else and switch case).

## useState (Manages Component State)
- Manages state in functional components.
- Manages local state
- Used to declare state variables in functional components.
  ```
  setCount(prev => prev+1) // keep mind
  ```

## useEffect (Handles Side Effects)
- Handles side effects like API calls, event listeners, or subscriptions.
```
  useEffect(() => {
    window.addEventListner(resize, ()=>{
     setWindow(window.innerWidth)
    }
    //....
  }, []); // Empty dependency array → runs once on mount
```
## useContext (Global State Management)
- Allows sharing data across components without props drilling.
- useContext return the contet value for the context you passed.
- The context API uses a provider to pass data to its child component. You will have to wrap all component with a provider component.
```
import { createContext, useContext } from "react";
const ThemeContext = createContext("light");

function ThemeComponent() {
  const theme = useContext(ThemeContext);
  return <p>Current Theme: {theme}</p>;
}
export default function App() {
  return (
    <ThemeContext.Provider value={dark}>
      <ThemeComponent />
    </ThemeContext.Provider>
  );
}
```
## useRef: (Accessing DOM & Persisting Values)
- Used for accessing DOM elements and persisting values without causing re-renders.
- Big usecases - used to refrence element inside the html.
- useRef Hook allow you to persist value b/w render.
- It can be access DOM element directly.
- useRef() can return only one item, It return an object called current.
- The useRef hook can also be used to keep track of previous state value.
  
```
import { useState, useEffect, useRef } from "react";
import "./styles.css";

export default function App() {
  const [name, setName] = useState("");
  const inputRef = useRef(0);

  const focus = () => {
    inputRef.current.focus();
    inputRef.current.input = 'Some Value'
  };

  return (
    <div className="App">
      <input
        ref={inputRef}
        type="text"
        onChange={(e) => setName(e.target.value)}
      />
      <h2>My name is {name}</h2>
      <button onClick={focus}>Focus</button>
    </div>
  );
}
}
```
## useReducer: (For Complex State Logic)
- An alternative to useState for complex state logic.
- useReducer is a React Hook that manages complex state logic in a React component. It is an alternative to useState when dealing with multiple related state values or complex state transitions.
- Syntax ``` const [state, dispatch] = useReducer(reducer, initialState); ```
  - reducer: A function that takes the current state and an action, then returns the new state.
  - initialState: The initial value of the state.
  - state: The current state value.
  - dispatch: A function to send actions to update the state.
  
```
import { useReducer, useState } from "react";
import "./styles.css";

// outside function
function reducer(todos, action) {
  switch (action.type) {
    case "add_todo":
      return [...todos, newTodo(action.payload.name)];
    default:
      return state;
  }
}

function newTodo(name) {
  return { _id: new Date(), name: name, complete: false };
}

export default function App() {
  const [todos, dispatch] = useReducer(reducer, []);
  const [name, setName] = useState("");

  function handleSubmit(e) {
    e.preventDefault();
    dispatch({ type: "add_todo", payload: { name: name } });
    setName("");
  }

  return (
    <>
      <form onSubmit={handleSubmit}>
        <input
          type="text"
          value={name}
          onChange={(e) => setName(e.target.value)}
        />
      </form>
    </>
  );
}
```
```
 const [name, setName] = useState("");
  const prevName = useRef("");

  useEffect(() => {
    prevName.current = name;
  }, [name]);

  return (
    <div className="App">
      <input type="text" onChange={(e) => setName(e.target.value)} />
      <h2>
        My name is {name} and prevName name is: {prevName.current}
      </h2>
    </div>
```
## useMemo: (Performance Optimization)
- Optimizes performance by memoizing computed values.
- memoization as caching a value so that it don't need to be recalculate.
- the useMemo Hooks only run when one of its dependies update.
- Syntax : ``` useMemo(calculatedValue, dependencies); ```
```
import React, { useState, useMemo } from "react";

const MemoExample = () => {
  const [numbers, setNumbers] = useState([1, 2, 3, 4, 5]);
  const [count, setCount] = useState(0);

  // Memoizing the sum of numbers
  const sum = useMemo(() => {
    console.log("Calculating sum...");
    return numbers.reduce((acc, num) => acc + num, 0);
  }, [numbers]); // Runs only when `numbers` change

  return (
    <div>
      <h2>Sum: {sum}</h2>
      <button onClick={() => setCount(count + 1)}>Re-render ({count})</button>
      <button onClick={() => setNumbers([...numbers, Math.floor(Math.random() * 10)])}>
        Add Random Number
      </button>
    </div>
  );
};
```
## useCallback: (Optimizing Function References)
- Memoizes functions to prevent unnecessary re-renders.
  ```
  import { useState, useCallback } from "react";
  import "./styles.css";
  
  export default function App() {
    const [number, setNumber] = useState(0);
  
    // Memoized function to return array of numbers this will be render not again and again only when number update it will be update number value.
    const getItem = useCallback(() => {
      return [number, number + 1, number + 2];
    }, [number]);
  
    // Call getItem() to get the values
    const items = getItem();
  
    return (
      <>
        <input
          type="text"
          value={number}
          onChange={(e) => setNumber(Number(e.target.value))} // Fix: Convert input to number
        />
        <br />
        {number !== 0 && (
          <>
            <h1>{items[0]}</h1>
            <h2>{items[1]}</h2>
            <h2>{items[2]}</h2>
          </>
        )}
      </>
    );
  }

  ```
 **Important Check** if you use usememo in place of usecallback then difference is usememo not return the function only value of the function but usecallback return the function.
| **Feature** | **useCallback** | **useMemo** |
| -------------- | ----------------------| --------------- |
| What it returns	| Returns a memoized function	 | Returns a memoized value |
| When to use? | 	When you want to memoize a function and avoid unnecessary re-creation on re-renders. | 	When you want to memoize the result of a computation and avoid unnecessary recalculations.|
| Use case	| Optimizing functions passed as props to child components. | 	Optimizing expensive calculations. |
| Return type |	Function |	Computed Value |

## useLayoutEffect: (Runs Before Paint)
- Similar to useEffect but runs synchronously after DOM mutations.
- useLayoutEffect is synchronous
- useLayoutEffect run between when react calculate the count and printed out the screen.
- When we are do something based on Layout of your DOM.

## useImperativeHandle: (Customizing ref Exposed Values)
- Customizes the instance value exposed when using ref.

## What is useId in React?
- useId is a React Hook introduced in React 18 that generates a unique ID. It is mainly used to associate form labels and elements while avoiding conflicts between multiple components.
- useId() generates a unique ID like "id-:r0:" or "id-xyz", ensuring that the label and input are correctly linked.
```
import { useId } from "react";
function CustomCheckbox() {
  const id = useId();

  return (
    <div>
      <input type="checkbox" id={id} />
      <label htmlFor={id}>Accept Terms</label>
    </div>
  );
}

export default function App() {
  return (
    <div>
      <CustomCheckbox />
      <CustomCheckbox />
    </div>
  );
}
```
####  Why Use useId?
- Avoid ID Collisions: If multiple instances of a component exist, using a hardcoded ID can cause conflicts.
- Server-Side Rendering (SSR) Safe: Ensures that IDs remain consistent between the server and client.

## What are Custom Hooks?
- A Custom Hook in React is a JavaScript function that starts with "use" and allows you to reuse logic across multiple components.
  ```
  import { useState, useEffect } from "react";
  const useFetch = (url) => {
    const [data, setData] = useState(null);
    const [loading, setLoading] = useState(true);
    const [error, setError] = useState(null);
  
    useEffect(() => {
      const fetchData = async () => {
        try {
          const response = await fetch(url);
          const result = await response.json();
          setData(result);
        } catch (err) {
          setError(err);
        } finally {
          setLoading(false);
        }
      };
      fetchData();
    }, [url]);
  
    return { data, loading, error };
  };
  export default useFetch;
  ```
  ```
  import React from "react";
  import useFetch from "./useFetch";
  const UserList = () => {
    const { data, loading, error } = useFetch("https://jsonplaceholder.typicode.com/users");
  
    if (loading) return <p>Loading...</p>;
    if (error) return <p>Error: {error.message}</p>;
  
    return (
      <ul>
        {data.map((user) => (
          <li key={user.id}>{user.name}</li>
        ))}
      </ul>
    );
  };
  export default UserList;
  ```

## State and Props
**State** 
- Stateis a mutable (changeable) object that stores data inside a component.
- A component owns and controls its state.
- When the state updates, the component re-renders automatically.
**props (peoperty)**
- props is like argument pass in a function, props you pass into the component and state is inside a component.
- Props are immutable and passed from a parent component to a child component.
- The child cannot modify props; they are read-only.
- Used for data sharing between components.

## What is JSX?
- JSX stands for JavaScript XML. It allows us to write HTML inside JavaScript and place them in the DOM without using functions like appendChild( ) or createElement( ).
  
## What is component?
- Component are independent and reusable bits of code.
- Component are function that return HTML element JSX.

## Difference Between Class Component and Functional Component in React 🚀
React provides two ways to create components:
1. Class Components (Old Approach)
2. Functional Components (Modern Approach)

 ### Class Component (Before React 16.8)
 - Uses ES6 class syntax.
 - Requires render() method.
 - Uses this.state for managing state.
 - Uses Lifecycle Methods (componentDidMount, componentDidUpdate, etc.).
 - More boilerplate code.
 - A class component must include the 'extend React.Component' statement. (create an Inheritance in react)

### Functional Component (Modern Approach)
- Uses JavaScript functions.
- No this keyword required.
- Uses useState, useEffect, and other React Hooks.
- Shorter and cleaner code.
- Easier to read, test, and optimize.

## What is the virtual DOM? How does react use the virtual DOM to render the UI?
- Virtual DOM is nothing but it is the virtual representation of the real DOM (Document Object Modal) so basically whenever the state of out application get update the virtual DOM get update instead of the real DOM.
- DOM manipulation is an integral part of any web application, but DOM manipulation is quite slow when compared to other operations in JavaScript. The efficiency of the application gets affected when several DOM manipulations are being done. Most JavaScript frameworks update the entire DOM even when a small part of the DOM changes.

##  What is prop drilling in React?
- Props Drilling refers to the process of passing data (props) from a parent component to a deeply nested child component, even if some intermediate components don’t need it.
- It can make the code harder to maintain and less scalable as the app grows.
- UseContext use to stop props drilling.

## WHat is Reconciliation? 
- Reconciliation is the process React uses to efficiently update the DOM when a component's state or props change. Instead of re-rendering the entire UI, React compares the new Virtual DOM with the previous Virtual DOM and applies only the necessary changes to the actual DOM.
- This makes updates faster, efficient, and smooth!

## What is Webpack.
- Webpack is a module bundler for JavaScript applications. It takes multiple files (JavaScript, CSS, images, etc.), processes them, and bundles them into a single (or multiple) optimized file(s) for better performance.
- Like crate react app, webpack is also a commond line tool used to create a bundle of assets (files and code).
- It doesn't run on the browser or on the server.
- It take all the js file and other assets file, transforming them into one large file. Now this compressed file can be sent to the browser or the server depending on which rendering style you have set up for your website.
- All different2 extension file convert into one single file.

## Name a few techniques to optimize React app performance.
- Using useMemo( ): t is a React hook that is used for caching CPU-Expensive functions.
- Using React.PureComponent: It is a base component class that checks the state and props of a component to know whether the component should be updated.
- Lazy Loading :  It is a technique used to reduce the load time of a React app. Lazy loading helps reduce the risk of web app performances to a minimum.

## Explain Strict Mode in React.
- React's Strict Mode is a development-only feature that helps identify potential problems in your application. It does not affect the production build and only runs in development mode.
#### It helps with:
- Identifying unsafe lifecycle methods in class components.
- Detecting side effects by intentionally double-invoking certain functions.
- Highlighting potential issues with deprecated APIs.
- Ensuring components are following best practices.
- Preventing accidental mutations of state.
  
#### Enable Strict Mode
```
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";

ReactDOM.createRoot(document.getElementById("root")).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

## What is propTypes in React?
- propTypes is a mechanism in React used for type-checking the props passed to a component. It helps catch bugs by ensuring that the correct data types are used.
```
import PropTypes from "prop-types";
const Greeting = ({ name, age }) => {
  return (
    <div>
      <h1>Hello, {name}!</h1>
      <p>You are {age} years old.</p>
    </div>
  );
};

// Define prop types
Greeting.propTypes = {
  name: PropTypes.string.isRequired, // name must be a string and required
  age: PropTypes.number, // age must be a number (optional)
};
export default Greeting;
```
Note: npm i props-type
Example Type: PropTypes.string, PropTypes.number, PropTypes.bool, PropTypes.object, PropTypes.array, PropTypes.func, PropTypes.element, PropTypes.shape({ key: PropTypes.string }).

## Lifting State Up in React 🚀
- Lifting State Up is a React pattern where state is moved from a child component to a common parent component to ensure better state management and data flow.
- Why Lift State Up?
 -To share data between sibling components.
 -To maintain a single source of truth for state.
 -To prevent unnecessary re-renders in child components.

```
import { useState } from "react";
const ChildA = ({ count, onIncrement }) => {
  return (
    <div>
      <h2>Child A Count: {count}</h2>
      <button onClick={onIncrement}>Increment</button>
    </div>
  );
};

const ChildB = ({ count }) => {
  return <h2>Child B can now see Count: {count}</h2>;
};

export default function App() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <ChildA count={count} onIncrement={() => setCount(count + 1)} />
      <ChildB count={count} />
    </div>
  );
}
```
## What is React Fragmentation? 
- React Fragment (<React.Fragment> or <>...</>)
- React Fragmentation refers to the use of React Fragments, which allow you to group multiple elements without adding extra nodes to the DOM.
  
### Why Use React Fragments?
- By default, React requires components to return a single parent element. If you return multiple elements without wrapping them, it will cause an error.
```
const List = () => {
  return (
    <>
      <li>Apple</li>
      <li>Banana</li>
    </>
  );
};
```
## Stateful vs Stateless Components in React 🚀
- In React, components can be categorized into Stateful (Class-based) and Stateless (Functional) Components, based on whether they manage their own state.
- Stateful: A Stateful Component is a component that manages state using this.state. These components track changes and re-render when the state is updated.
- Stateless: A Stateless Component is a simple function that only renders UI and does not manage state.

### Key Features of Stateful Components:
- ✅ Uses Class Components.
- ✅ Stores and manages state (this.state).
- ✅ Requires a constructor and this.setState to update state.
- ✅ More complex but powerful (before Hooks were introduced).

### Key Features of Stateless Components:
- ✅ Uses Functional Components.
- ✅ No state management (before React Hooks).
- ✅ Simpler and easier to read.
- ✅ Used for UI rendering only.

## LifeCycle  Method
- A component's lifecycle has three main phases: Mounting Phase, Updating Phase, and Unmounting Phase and Error Handling Phase.
- The Mounting Phase begins when a component is first created and inserted into the DOM. The Updating Phase occurs when a component's state or props change. And the Unmounting Phase occurs when a component is removed from the DOM.

### Mounting Phase:
- In this Phase three method is - constructor(), render() and getDerivedStateFromProps(props,state).
- ComponentDidMount: This method is called once the component has been mounted into the DOM. It is typically used to set up any necessary event listeners or timers, perform any necessary API calls or data fetching, and perform other initialization tasks that require access to the browser's DOM API.
  
| **Method** | **Description** | 
| -------------- | ----------------------| 
| constructor()	| Initializes state and binds methods. |
| static |  getDerivedStateFromProps()	Syncs state with props before rendering. Rarely used.|
| render() | 	Returns JSX to render the UI.|
| componentDidMount()	| Called after the component is mounted. Ideal for API calls or subscriptions.|

### Updating Phase
| **Method** | **Description** | 
| -------------- | ----------------------| 
| static | getDerivedStateFromProps()	Same as in Mounting phase; used when state depends on props. | 
| shouldComponentUpdate() |	Determines if a component should re-render. | 
| render() |	Re-renders the UI. | 
| getSnapshotBeforeUpdate() | 	Captures DOM information before update. |
| componentDidUpdate() |	Called after the component updates. Ideal for handling side-effects. |

### Unmounting Phase
| **Method** | **Description** | 
| -------------- | ----------------------| 
| componentWillUnmount() | 	Called before the component is destroyed. Ideal for cleanup (e.g., clearing timers, cancelling network requests, etc.). | 

### Error Handling Phase
| **Method** | **Description** | 
| -------------- | ----------------------| 
| static getDerivedStateFromError() | Catches errors and updates state accordingly. | 
| componentDidCatch()	| Logs the error or displays a fallback UI.|

## Error Boundaries
- Functional Components & Error Boundaries: You cannot create an Error Boundary using Hooks. It must be a class component. But you can use them to wrap functional components.
- Wrap in try and catch or console.error('error message')

# React Router 















 
