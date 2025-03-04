# REACT-NOTES

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
| 1 |  differences between controlled and uncontrolled components in React, and when would you prefer one over the other |
| 2 | "What are React Hooks, and why were they introduced? | 
| 3 | What is the difference between useEffect and useLayoutEffect in React? | 
| 4 | What is React reconciliation, and how does the virtual DOM work? | 
| 5 | What are Higher-Order Components (HOC) in React? Can you give an example of how they are used? |
| 6 | What is the difference between Context API and Redux for state management? When should you use each? |
| 7 | What are the different lifecycle methods in React class components, and how do they map to React hooks in functional components? |
| 8 |
---
### 1. Controlled Components:
- In controlled components, form elements (like input, textarea, select) are bound to the component’s state. The React component controls the value of the form element.
- The state is updated based on user input through event handlers.
- It gives you more control over the form data because React is managing the state of the inputs.
### 1.2 Uncontrolled Components:
- In uncontrolled components, form elements manage their own state internally, and you interact with them through refs (short for references).
- React does not directly control the value of the input, and it relies on the DOM to manage the state.
- It is often used when you need to interact with the DOM directly or when you don’t need to track the input value in the React component.

### 3.1 useEffect (Runs asynchronously after render)
- Executes after the browser paints the screen.
- Used for data fetching, subscriptions, or updating the DOM without blocking rendering.
- Does not block the UI, making it good for most use cases.

### 3.2 useLayoutEffect (Runs synchronously before the browser paints)
- Executes before the browser updates the screen.
- Used when you need to measure DOM elements or make layout adjustments before the user sees the change.
- Can block rendering, so use it carefully.

### 4 Virtual DOM (VDOM)
- React maintains a lightweight copy of the real DOM called the Virtual DOM.
- Instead of updating the actual DOM directly (which is slow), React updates the Virtual DOM first.
### Reconciliation (Efficiently updating the UI)
- When state or props change, React creates a new Virtual DOM tree.
- It compares (diffs) the new Virtual DOM with the previous one.
- Only the changed elements are updated in the real DOM (not the whole page).

### 5 A Higher-Order Component (HOC):
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

### Key Features:
- Component-Based – UI is built using reusable components.
- Virtual DOM – Improves performance by updating only changed elements.
- State Management – Uses hooks like useState, useReducer for handling state.
- Unidirectional Data Flow – Data flows in one direction for easier debugging.
- Hooks – Allows functional components to manage state and lifecycle.

# Hooks:

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
```
import { createContext, useContext } from "react";
const ThemeContext = createContext("light");

function ThemeComponent() {
  const theme = useContext(ThemeContext);
  return <p>Current Theme: {theme}</p>;
}
export default function App() {
  return (
    <ThemeContext.Provider value="dark">
      <ThemeComponent />
    </ThemeContext.Provider>
  );
}
```
## useRef: (Accessing DOM & Persisting Values)
- Used for accessing DOM elements and persisting values without causing re-renders.
```
import { useRef, useEffect } from "react";

function InputFocus() {
  const inputRef = useRef(null);

  useEffect(() => {
    inputRef.current.focus();
  }, []);

  return <input ref={inputRef} placeholder="Type here..." />;
}
```
## useReducer: (For Complex State Logic)
- An alternative to useState for complex state logic.
```
import { useReducer } from "react";

const reducer = (state, action) => {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    case "decrement":
      return { count: state.count - 1 };
    default:
      return state;
  }
};

function Counter() {
  const [state, dispatch] = useReducer(reducer, { count: 0 });

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: "increment" })}>+</button>
      <button onClick={() => dispatch({ type: "decrement" })}>-</button>
    </div>
  );
}
```
## useMemo: (Performance Optimization)
- Optimizes performance by memoizing computed values.
```
import { useState, useMemo } from "react";

function ExpensiveCalculation({ number }) {
  const computedValue = useMemo(() => {
    console.log("Computing...");
    return number * 2;
  }, [number]);

  return <p>Computed Value: {computedValue}</p>;
}  
```
## useCallback: (Optimizing Function References)
- Memoizes functions to prevent unnecessary re-renders.

## useLayoutEffect: (Runs Before Paint)
- Similar to useEffect but runs synchronously after DOM mutations.

## useImperativeHandle: (Customizing ref Exposed Values)
- Customizes the instance value exposed when using ref.

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











 
