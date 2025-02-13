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
| 7 | 
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
--- 
# React Notes Start



 
