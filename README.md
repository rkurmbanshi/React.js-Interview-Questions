# React.js-Interview-Questions

<details> <summary><strong>1. How to create custom hooks</strong></summary>
React Hooks are a powerful feature in React that allow developers to use state and other React features in functional components. Creating custom hooks can help you extract reusable logic from your components, making them more maintainable and easier to understand. Here's a step-by-step guide on how to create custom hooks in React:

Example:

```javascript

import { useState, useEffect } from 'react';

function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    fetch(url)
      .then((response) => response.json())
      .then((data) => {
        setData(data);
        setLoading(false);
      })
      .catch((error) => {
        setError(error);
        setLoading(false);
      });
  }, [url]);

  return { data, loading, error };
}

// Using custom hook in a component
function App() {
  const { data, loading, error } = useFetch('https://api.example.com/data');
  if (loading) return <div>Loading...</div>;
  if (error) return <div>Error: {error.message}</div>;
  return <div>{JSON.stringify(data)}</div>;
}
```
</details>
<details> <summary><strong>2. How to React Update DOM?</strong></summary>
React updates the DOM efficiently through a process called "reconciliation." When the state or props of a component change, React updates the virtual DOM first, then compares it with the real DOM to determine what needs to be updated, resulting in minimal changes to the real DOM.

</details>
<details> <summary><strong>3. What is VDOM in React.js?</strong></summary>
The Virtual DOM (VDOM) is an in-memory representation of the real DOM elements. It allows React to update the UI without directly manipulating the real DOM, making updates more efficient.

</details>
<details> <summary><strong>4. State Management in React</strong></summary>
State management in React can be done using useState, useReducer, or external libraries like Redux to manage global state. useState is used for managing component-specific states, while useReducer is often used for more complex state logic.

Example:

```javascript
const [count, setCount] = useState(0);

const increment = () => {
  setCount(count + 1);
};
</details>
<details> <summary><strong>5. What is Prop Drilling?</strong></summary>
Prop drilling is the process of passing data from a parent component to a deeply nested child component through props. This can become cumbersome when dealing with deeply nested components, leading to less maintainable code.
```
</details>
<details> <summary><strong>6. What is Redux?</strong></summary>
Redux is a state management library for JavaScript apps that helps manage and centralize application state. It uses a single store and actions to manage state transitions.

Example:

```javascript
const initialState = { count: 0 };

function reducer(state = initialState, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    default:
      return state;
  }
}
```
</details>
<details> <summary><strong>7. What is Middleware in Redux?</strong></summary>
Middleware in Redux is used to extend Redux with custom functionality like logging, API calls, and error handling. It intercepts actions before they reach the reducer.

Example:

```javascript
const loggerMiddleware = store => next => action => {
  console.log('Dispatching', action);
  return next(action);
};
```
</details>
<details> <summary><strong>8. What is Webpack?</strong></summary>
Webpack is a module bundler for JavaScript applications. It bundles JavaScript files and assets like images, CSS, and fonts into optimized files for deployment.

</details>
<details> <summary><strong>9. How to use styles in React.js?</strong></summary>
Styles in React can be applied in various ways: inline styles, CSS files, CSS modules, or CSS-in-JS solutions like styled-components.

Example of inline style:

```javascript
const style = { color: 'blue', fontSize: '20px' };
return <div style={style}>Hello World!</div>;
```
</details>
<details> <summary><strong>10. How to Handle Form and Its Validation in React?</strong></summary>
Forms in React are controlled components, meaning React controls the state of the form elements. You can validate form data either manually or using third-party libraries like Formik or React Hook Form.

Example:

```javascript
const [email, setEmail] = useState('');
const [error, setError] = useState('');

const validateEmail = () => {
  if (!email.includes('@')) {
    setError('Invalid email');
  } else {
    setError('');
  }
};

return (
  <form>
    <input type="email" value={email} onChange={(e) => setEmail(e.target.value)} />
    <button onClick={validateEmail}>Submit</button>
    {error && <p>{error}</p>}
  </form>
);
```
</details>
<details> <summary><strong>11. What is Context API in React?</strong></summary>
The Context API is a React feature that allows you to share state or values between components without having to pass props manually through every level of the component tree.

Example:

```javascript
const MyContext = React.createContext();

function Parent() {
  const value = 'Hello World';
  return (
    <MyContext.Provider value={value}>
      <Child />
    </MyContext.Provider>
  );
}

function Child() {
  const value = useContext(MyContext);
  return <div>{value}</div>;
}
```
</details>
<details> <summary><strong>12. Explain Local Storage and Session Storage and How to Secure Both Storages</strong></summary>
Local Storage stores data without an expiration time and persists even after the browser is closed.
Session Storage stores data for the duration of the page session.
Both can be accessed through JavaScript, but sensitive data should be encrypted before storage to ensure security.

Example:

```javascript
localStorage.setItem('user', JSON.stringify({ name: 'John' }));
const user = JSON.parse(localStorage.getItem('user'));
```
</details>
<details> <summary><strong>13. What are Web Workers?</strong></summary>
Web Workers allow JavaScript to run in the background without blocking the main thread. This is useful for handling complex or time-consuming tasks like data processing.

Example:

```javascript
const worker = new Worker('worker.js');

worker.postMessage('start');

worker.onmessage = function(e) {
  console.log('Message from worker: ' + e.data);
};
```
```javascript
//worker.js

javascript
Copy code
onmessage = function(e) {
  if (e.data === 'start') {
    postMessage('Worker started!');
  }
};
```
</details>
<details> <summary><strong>14. What is PWA (Progressive Web App)?</strong></summary>
A Progressive Web App (PWA) is a web application that uses modern web capabilities to deliver an app-like experience to users, including offline access and push notifications.

</details>
<details> <summary><strong>15. Difference Between Single Page Application (SPA) and Multi-Page Application (MPA)</strong></summary>
SPA: Loads a single HTML page, and content is dynamically updated via JavaScript, providing a smoother user experience without reloading the page.
MPA: Each user interaction typically triggers a full page reload, which can lead to a slower user experience.
</details>
<details> <summary><strong>16. Explain API Calls and Its Process</strong></summary>
API calls in React are typically made using the fetch API or libraries like Axios. When making an API call, React waits for the response asynchronously and updates the state based on the data received.

Example:

```javascript
useEffect(() => {
  fetch('https://api.example.com/data')
    .then(response => response.json())
    .then(data => setData(data));
}, []);
```
</details>
<details> <summary><strong>17. What is Optimization and How to Implement it in React JS?</strong></summary>
Optimization in React refers to techniques like memoization, lazy loading, and minimizing unnecessary re-renders to improve app performance. One such method is React.memo for functional components.

Example of React.memo:

```javascript
const MemoizedComponent = React.memo(function MyComponent({ name }) {
  console.log('Rendering', name);
  return <div>{name}</div>;
});
```
</details>
<details> <summary><strong>18. What is AMP (Accelerated Mobile Pages)?</strong></summary>
AMP is an open-source framework designed to make mobile web pages load faster. It uses a stripped-down version of HTML and JavaScript to ensure quicker loading times, particularly for content-heavy pages.

</details>
<details> <summary><strong>19. What is Page Layout Shift?</strong></summary>
Page Layout Shift (CLS) is a Core Web Vitals metric that measures visual stability. A high CLS means that the page elements shift unexpectedly as the page loads, which can negatively impact user experience.

</details>
<details> <summary><strong>20. What is Microservices?</strong></summary>
Microservices is an architectural style where a large application is built as a set of smaller, independent services that communicate over the network, each focusing on a specific business function.

</details>
<details> <summary><strong>21. Explain the "this" keyword in JavaScript?</strong></summary>
The this keyword in JavaScript refers to the context in which the current code is executed. Its value depends on how the function is called.

Example:

```javascript
const obj = {
  name: 'John',
  greet: function() {
    console.log(this.name);  // 'this' refers to 'obj'
  }
};
obj.greet();  // Output: John
```
</details>
<details> <summary><strong>22. What is a Semantic Element?</strong></summary>
Semantic HTML elements are those that clearly describe their meaning in a human- and machine-readable way. Examples include <article>, <section>, <header>, and <footer>.

Example:

```html
<article>
  <h1>Article Title</h1>
  <p>This is the content of the article.</p>
</article>
```
</details>
<details> <summary><strong>23. What is CSS Object?</strong></summary>
A CSS object typically refers to an object in JavaScript that holds CSS properties and values. This can be used to dynamically apply styles to elements in React components.

Example:

```javascript
const style = {
  color: 'red',
  fontSize: '20px',
};

return <div style={style}>Hello, World!</div>;
```
</details>
<details> <summary><strong>24. What is Redux?</strong></summary>
Redux is a predictable state container for JavaScript apps. It helps you write applications that behave consistently across different environments, with debugging and testing capabilities.

Example:

  ```javascript
const initialState = { count: 0 };

function reducer(state = initialState, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    default:
      return state;
  }
}
```
</details>
<details> <summary><strong>25. What is Observable in Redux?</strong></summary>
In Redux, an observable refers to a stream of data that can be observed, similar to how actions are dispatched in Redux. Observables are often used with middleware like Redux-Observable.

</details>
<details> <summary><strong>26. What is Flux?</strong></summary>
Flux is a pattern for managing data flow in JavaScript applications. It uses a unidirectional flow to manage the state, making it predictable. Redux is heavily inspired by Flux.

</details>
<details> <summary><strong>27. What is a Higher-Order Component (HOC)?</strong></summary>
A Higher-Order Component is a function that takes a component and returns a new component with additional props or logic.

Example:

  ```javascript
function withLoader(Component) {
  return function WithLoader(props) {
    if (props.loading) {
      return <div>Loading...</div>;
    }
    return <Component {...props} />;
  };
}
```
</details>

<details> <summary><strong>28. Difference Between Map and Reduce</strong></summary>
Map: Creates a new array by applying a function to each element of the original array.
Reduce: Reduces the array to a single value by applying a function to each element, accumulating the result.
Example of map:

  ```javascript
const numbers = [1, 2, 3];
const doubled = numbers.map(num => num * 2);
console.log(doubled); // [2, 4, 6]
Example of reduce:
```
  ```javascript
const numbers = [1, 2, 3];
const sum = numbers.reduce((acc, num) => acc + num, 0);
console.log(sum); // 6
```
</details>
<details> <summary><strong>29. What is React JS and its Pros and Cons?</strong></summary>
React is a JavaScript library for building user interfaces, primarily for single-page applications. It is declarative, component-based, and enables developers to create reusable UI components.

Pros:

Fast rendering with Virtual DOM
Component-based architecture
Reusable components
Strong community support
Cons:

Steeper learning curve
Requires build tools (Webpack, Babel)
Frequent updates with breaking changes
</details>
<details> <summary><strong>30. What is Batching?</strong></summary>
Batching refers to the process of grouping multiple updates into a single re-render in React. React batches updates to improve performance by reducing the number of re-renders.

Example:

  ```javascript
// React will batch these updates together and render only once
setCount(count + 1);
setFlag(!flag);
```
</details>
<details> <summary><strong>31. What is Diffing and Reconciliation?</strong></summary>
Diffing is the process React uses to compare the current Virtual DOM with the previous one and identify changes. Reconciliation is the process of updating the actual DOM to reflect the changes detected during the diffing process.

</details>
<details> <summary><strong>32. What is the useRef Hook?</strong></summary>
useRef is a React hook that allows you to persist a mutable value across renders. It is commonly used for accessing DOM elements directly or storing a value that doesn’t cause re-rendering when updated.

Example:

  ```javascript
const inputRef = useRef(null);

useEffect(() => {
  inputRef.current.focus();  // Focus the input field on component mount
}, []);

return <input ref={inputRef} />;
```
</details>
<details> <summary><strong>33. What is Pure Component?</strong></summary>
A PureComponent in React is a component that only re-renders when its props or state change. It implements shouldComponentUpdate with a shallow comparison of props and state.

Example:

  ```javascript
class MyComponent extends React.PureComponent {
  render() {
    return <div>{this.props.name}</div>;
  }
}
```
</details>
<details> <summary><strong>34. What is Pure Function?</strong></summary>
A pure function is a function that always produces the same output given the same input and does not cause side effects (like modifying global state or performing IO operations).

Example:

  ```javascript
function add(a, b) {
  return a + b;  // Pure function, no side effects
}
```
</details>
<details> <summary><strong>35. What is useState?</strong></summary>
useState is a hook that allows you to add state to functional components. It returns an array with the current state and a function to update it.

Example:

  ```javascript
const [count, setCount] = useState(0);

return (
  <div>
    <p>{count}</p>
    <button onClick={() => setCount(count + 1)}>Increment</button>
  </div>
);
```
</details>
<details> <summary><strong>36. What is useEffect?</strong></summary>
useEffect is a hook that performs side effects in functional components. It can be used for tasks like fetching data, updating the DOM, or subscribing to external events.

Example:

  ```javascript
useEffect(() => {
  console.log('Component mounted');
  return () => {
    console.log('Component unmounted');
  };
}, []);
```
</details>
<details> <summary><strong>37. What is useSelector?</strong></summary>
useSelector is a hook from React-Redux that allows you to extract data from the Redux store state.

Example:

  ```javascript
const count = useSelector(state => state.count);
```
</details>
<details> <summary><strong>38. What is useDispatch?</strong></summary>
useDispatch is a hook from React-Redux that gives you access to the dispatch function from Redux, which allows you to dispatch actions to the Redux store.

Example:

  ```javascript
const dispatch = useDispatch();

const increment = () => {
  dispatch({ type: 'INCREMENT' });
};
```
</details>
<details> <summary><strong>39. How to Configure a Store and Create a Slice in Redux?</strong></summary>
To configure a store and create a slice in Redux, you typically use Redux Toolkit, which simplifies store configuration and slice creation.

Example:

  ```javascript
import { configureStore, createSlice } from '@reduxjs/toolkit';

const counterSlice = createSlice({
  name: 'counter',
  initialState: { count: 0 },
  reducers: {
    increment: (state) => {
      state.count += 1;
    },
    decrement: (state) => {
      state.count -= 1;
    },
  },
});

const store = configureStore({
  reducer: counterSlice.reducer,
});

export default store;
```
</details>
<details> <summary><strong>40. What are Actions in Redux?</strong></summary>
Actions in Redux are plain JavaScript objects that describe an event that has occurred. They must have a type property and may include other data in the payload.

Example:

  ```javascript
const incrementAction = { type: 'INCREMENT' };
```
</details>

<details> <summary><strong>41. What is Saga?</strong></summary>
Redux-Saga is a middleware library used to handle side effects in Redux. It allows you to manage asynchronous actions like data fetching, more effectively using generators.

Example:

  ```javascript
import { takeEvery, call, put } from 'redux-saga/effects';

function* fetchData() {
  try {
    const response = yield call(fetch, 'https://api.example.com/data');
    const data = yield response.json();
    yield put({ type: 'FETCH_SUCCESS', data });
  } catch (error) {
    yield put({ type: 'FETCH_ERROR', error });
  }
}

function* watchFetchData() {
  yield takeEvery('FETCH_REQUEST', fetchData);
}
```
</details>
<details> <summary><strong>42. What is Shadow DOM?</strong></summary>
The Shadow DOM is a web standard that allows developers to encapsulate DOM and CSS styles within a component, creating a local scope for styles and structure.

Example:

  ```javascript
const shadowRoot = document.querySelector('#shadow-host').attachShadow({mode: 'open'});
shadowRoot.innerHTML = '<p>Shadow DOM content</p>';
```
</details>
<details> <summary><strong>43. Class vs Functional Component</strong></summary>
Class Components: Traditional components with state, lifecycle methods, and can be extended from React.Component.
Functional Components: Simpler components using hooks to manage state and side effects.
Example of a class component:

  ```javascript
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }
  
  render() {
    return (
      <div>
        <p>{this.state.count}</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>Increment</button>
      </div>
    );
  }
}
```
Example of a functional component:
  ```javascript
javascript
Copy code
const Counter = () => {
  const [count, setCount] = useState(0);
  
  return (
    <div>
      <p>{count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
};
```
</details>
<details> <summary><strong>44. useMemo vs React.memo</strong></summary>
useMemo: A hook that memoizes a function’s result to avoid expensive recalculations on each render.
React.memo: A higher-order component that memoizes a functional component, preventing unnecessary re-renders when props haven’t changed.
Example of useMemo:

  ```javascript
const expensiveCalculation = useMemo(() => calculateExpensiveValue(a, b), [a, b]);
```
Example of React.memo:

  ```javascript
const MyComponent = React.memo(({ name }) => {
  return <p>{name}</p>;
});
```
</details>
<details> <summary><strong>45. What is the Lifecycle in the Class Component?</strong></summary>
The lifecycle of a class component in React consists of the following phases:

Mounting: Component creation and insertion into the DOM.
Updating: Component re-rendering due to changes in state or props.
Unmounting: Component removal from the DOM.
Methods:

constructor()
componentDidMount()
shouldComponentUpdate()
render()
componentWillUnmount()
</details>
<details> <summary><strong>46. What is ComponentShouldUpdate Lifecycle Method?</strong></summary>
shouldComponentUpdate() is a lifecycle method in class components that allows you to control whether the component should re-render when its props or state change. By default, it returns true, but you can override it to prevent unnecessary renders.

Example:

  ```javascript
shouldComponentUpdate(nextProps, nextState) {
  return nextState.count !== this.state.count;  // Prevent re-render if count hasn't changed
}
```
</details>
<details> <summary><strong>47. State vs Props</strong></summary>
State: A local data storage for a component that can change over time.
Props: Read-only values passed from a parent component to a child component.
Example:

  ```javascript
const Parent = () => {
  const message = "Hello from parent!";
  return <Child message={message} />;
};

const Child = (props) => {
  return <p>{props.message}</p>; // Props are passed down from Parent
};
```
</details>
<details> <summary><strong>48. How to Pass Data from Child to Parent Component?</strong></summary>
To pass data from a child to a parent component, you can use a callback function that the parent passes to the child as a prop.

Example:

  ```javascript
const Parent = () => {
  const handleData = (data) => {
    console.log(data); // Receiving data from child
  };

  return <Child sendData={handleData} />;
};

const Child = ({ sendData }) => {
  return <button onClick={() => sendData("Hello from child!")}>Send Data</button>;
};
```
</details>
<details> <summary><strong>49. What are Controlled and Uncontrolled Components?</strong></summary>
Controlled Component: A component whose form elements are controlled by React state.
Uncontrolled Component: A component that manages its own state internally using ref.
Controlled Component Example:

  ```javascript
const ControlledInput = () => {
  const [value, setValue] = useState('');
  return <input value={value} onChange={(e) => setValue(e.target.value)} />;
};
```
Uncontrolled Component Example:

  ```javascript
const UncontrolledInput = () => {
  const inputRef = useRef();
  return <input ref={inputRef} />;
};
```
</details>
<details> <summary><strong>50. What is Stateless and Stateful Component?</strong></summary>
Stateless Component: A component that does not manage its own state. It only receives data via props.
Stateful Component: A component that manages its own state using useState or class-based state.
Stateful Component Example:

  ```javascript
const StatefulComponent = () => {
  const [count, setCount] = useState(0);
  return <button onClick={() => setCount(count + 1)}>{count}</button>;
};
```
Stateless Component Example:

  ```javascript
const StatelessComponent = ({ message }) => {
  return <p>{message}</p>;
};
```
</details>

<details> <summary><strong>51. What is Prop Drilling?</strong></summary>
Prop drilling refers to the process of passing data from a parent component to a deeply nested child component through multiple intermediate components.

Example:

  ```javascript
const Parent = () => {
  const message = "Hello from Parent!";
  return <Intermediate message={message} />;
};

const Intermediate = ({ message }) => {
  return <Child message={message} />;
};

const Child = ({ message }) => {
  return <p>{message}</p>;
};
```
</details>
<details> <summary><strong>52. How to Manage API Calls in React JS?</strong></summary>
In React, API calls can be managed using hooks like useEffect combined with fetch or libraries like axios to handle asynchronous operations.

Example using fetch:

  ```javascript
useEffect(() => {
  fetch('https://api.example.com/data')
    .then(response => response.json())
    .then(data => setData(data))
    .catch(error => console.error('Error fetching data:', error));
}, []);
```
Example using axios:

  ```javascript
useEffect(() => {
  axios.get('https://api.example.com/data')
    .then(response => setData(response.data))
    .catch(error => console.error('Error fetching data:', error));
}, []);
```
</details>
<details> <summary><strong>53. Which Lifecycle Method Performs an API Call?</strong></summary>
In class components, you would typically perform an API call inside the componentDidMount() lifecycle method, which is called once after the component has been mounted. In functional components, you can use useEffect for the same purpose.

Example in class component:

  ```javascript
class MyComponent extends React.Component {
  componentDidMount() {
    fetch('https://api.example.com/data')
      .then(response => response.json())
      .then(data => this.setState({ data }));
  }

  render() {
    return <div>{this.state.data}</div>;
  }
}
```
Example in functional component using useEffect:
  ```javascript
const MyComponent = () => {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(response => response.json())
      .then(data => setData(data));
  }, []); // Empty dependency array ensures it runs once

  return <div>{data}</div>;
};
```
</details>
<details> <summary><strong>54. How Many Ways to Use CSS?</strong></summary>
There are several ways to apply CSS in React components:

Inline styles
External CSS files
CSS Modules
Styled-components
SASS or SCSS
Example of inline styles:

  ```javascript
const style = { color: 'blue', fontSize: '20px' };
return <p style={style}>Styled Paragraph</p>;
```
Example of CSS Module:

  ```javascript
import styles from './MyComponent.module.css';

return <p className={styles.paragraph}>Styled with CSS Module</p>;
```
</details>
<details> <summary><strong>55. What is Box-Sizing in CSS?</strong></summary>
The box-sizing property defines how the total width and height of an element are calculated. By default, the width and height include only the content area, but setting box-sizing: border-box includes padding and border in the width/height calculation.

Example:

  ```css
div {
  width: 200px;
  height: 100px;
  padding: 20px;
  border: 5px solid black;
  box-sizing: border-box; /* Includes padding and border in the width and height */
}
```
</details>
<details> <summary><strong>56. Absolute vs Relative Position in CSS</strong></summary>
absolute positioning: An element is positioned relative to its closest positioned ancestor (non-static).
relative positioning: An element is positioned relative to its normal position in the document flow.
Example of absolute positioning:

  ```css
.absolute {
  position: absolute;
  top: 20px;
  left: 30px;
}
```
Example of relative positioning:

  ```css
.relative {
  position: relative;
  top: 10px;
  left: 20px;
}
```
</details>
<details> <summary><strong>57. What is Pseudo Class in CSS?</strong></summary>
A pseudo-class in CSS is used to define a special state of an element, like :hover, :focus, :active, etc.

Example:

  ```css
button:hover {
  background-color: green; /* Changes background color when button is hovered */
}
```
</details>
<details> <summary><strong>58. What is Modules CSS?</strong></summary>
CSS Modules is a way to scope CSS locally to a component in React. It avoids global CSS conflicts by giving each class a unique identifier.

Example:

  ```css
/* MyComponent.module.css */
.container {
  background-color: blue;
}
```
  ```javascript
import styles from './MyComponent.module.css';

const MyComponent = () => {
  return <div className={styles.container}>Content</div>;
};
```
</details>
<details> <summary><strong>59. Difference Between Reset vs Normalized CSS?</strong></summary>
Reset CSS: Removes all default styling from elements, resulting in a blank canvas.
Normalized CSS: Applies consistent styling across browsers while preserving useful default styles.
Example of Reset CSS:

  ```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```
Example of Normalized CSS:

  ```css
/* Normalize CSS Example */
html {
  font-size: 100%;
}

body {
  line-height: 1.5;
}
```
</details>
<details> <summary><strong>60. What are Pseudo-Elements and Pseudo-Classes?</strong></summary>
Pseudo-Elements: Target specific parts of an element like ::before, ::after, etc.
Pseudo-Classes: Apply styles based on user interaction or element state like :hover, :focus, etc.
Example of Pseudo-Element:

  ```css
p::before {
  content: "Prefix: ";
}
```
Example of Pseudo-Class:

  ```css
a:hover {
  color: red; /* Changes color when the link is hovered */
}
```
</details>

<details> <summary><strong>61. How to Call Multiple APIs at Once?</strong></summary>
To call multiple APIs concurrently in JavaScript, you can use Promise.all() which allows you to run multiple promises in parallel and wait for all of them to resolve.

Example:

  ```javascript
const fetchData = async () => {
  try {
    const [data1, data2] = await Promise.all([
      fetch('https://api.example1.com').then(res => res.json()),
      fetch('https://api.example2.com').then(res => res.json())
    ]);
    console.log(data1, data2);
  } catch (error) {
    console.error("Error fetching data:", error);
  }
};

useEffect(() => {
  fetchData();
}, []);
```
</details>
<details> <summary><strong>62. What is Redux?</strong></summary>
Redux is a state management library for JavaScript apps that provides a predictable state container, allowing developers to manage app state in a centralized store.

Example:

  ```javascript
// Action
const increment = () => ({
  type: 'INCREMENT'
});

// Reducer
const counter = (state = 0, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return state + 1;
    default:
      return state;
  }
};

// Store
const store = Redux.createStore(counter);

// Dispatch action
store.dispatch(increment());
console.log(store.getState()); // 1
```
</details>
<details> <summary><strong>63. What is Middleware in Redux?</strong></summary>
Middleware in Redux provides a way to intercept and modify actions before they reach the reducer. It's useful for handling asynchronous actions, logging, or other side effects.

Example using redux-thunk (for asynchronous actions):

  ```javascript
const fetchData = () => {
  return async dispatch => {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    dispatch({ type: 'SET_DATA', payload: data });
  };
};
```
</details>
<details> <summary><strong>64. What is Webpack?</strong></summary>
Webpack is a module bundler for JavaScript applications. It bundles JavaScript files, CSS, images, and other assets into one or more output files that can be served by a web server.

Example of a basic Webpack configuration:

  ```javascript
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist')
  },
  module: {
    rules: [
      {
        test: /\.css$/,
        use: ['style-loader', 'css-loader']
      }
    ]
  }
};
```
</details>
<details> <summary><strong>65. How to Use Styles in React JS?</strong></summary>
In React, you can apply styles using various methods such as inline styles, CSS files, CSS modules, and styled-components.

Example using inline styles:

  ```javascript
const buttonStyle = {
  backgroundColor: 'blue',
  color: 'white',
  padding: '10px 20px'
};

return <button style={buttonStyle}>Click Me</button>;
```
Example using styled-components:

  ```javascript
import styled from 'styled-components';

const Button = styled.button`
  background-color: blue;
  color: white;
  padding: 10px 20px;
`;

return <Button>Click Me</Button>;
```
</details>
<details> <summary><strong>66. How to Handle Form and its Validation in React?</strong></summary>
In React, form handling can be done using controlled components, where form data is managed in the component’s state, and validation can be added with conditionals or using third-party libraries like Formik or react-hook-form.

Example of a simple controlled form with validation:

javascript
Copy code
const Form = () => {
  const [name, setName] = useState('');
  const [error, setError] = useState('');

  const handleSubmit = (e) => {
    e.preventDefault();
    if (name.trim() === '') {
      setError('Name is required!');
    } else {
      setError('');
      alert(`Form submitted with name: ${name}`);
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        value={name}
        onChange={(e) => setName(e.target.value)}
        placeholder="Enter your name"
      />
      {error && <p>{error}</p>}
      <button type="submit">Submit</button>
    </form>
  );
};
</details>
<details> <summary><strong>67. What is Context API in React?</strong></summary>
The Context API allows you to share values (like themes or authentication status) between components without having to explicitly pass props through every level of the component tree.

Example:

javascript
Copy code
const ThemeContext = React.createContext();

const ThemeProvider = ({ children }) => {
  const [theme, setTheme] = useState('light');
  
  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      {children}
    </ThemeContext.Provider>
  );
};

const ThemedComponent = () => {
  const { theme, setTheme } = useContext(ThemeContext);
  return (
    <div style={{ background: theme === 'dark' ? 'black' : 'white' }}>
      <button onClick={() => setTheme(theme === 'dark' ? 'light' : 'dark')}>
        Toggle Theme
      </button>
    </div>
  );
};

const App = () => (
  <ThemeProvider>
    <ThemedComponent />
  </ThemeProvider>
);
</details>
<details> <summary><strong>68. Explain Local Storage and Session Storage and How to Secure Both Storages?</strong></summary>
LocalStorage: Stores data with no expiration date, it remains until it's explicitly deleted.
SessionStorage: Stores data for the duration of the page session (until the browser is closed).
Security Tips:

Avoid storing sensitive information like passwords in localStorage or sessionStorage as it is accessible by JavaScript.
Use encryption if you must store sensitive data.
Store tokens in secure HTTP-only cookies for better security.
Example:

javascript
Copy code
// Setting data in Local Storage
localStorage.setItem('name', 'John');

// Retrieving data from Local Storage
const name = localStorage.getItem('name');
console.log(name); // 'John'
</details>
<details> <summary><strong>69. What Are Web Workers?</strong></summary>
Web Workers allow for the execution of scripts in background threads. They are useful for performing computationally expensive tasks without blocking the main UI thread.

Example:

javascript
Copy code
const worker = new Worker('worker.js');
worker.postMessage('start task');

worker.onmessage = (e) => {
  console.log('Received from worker:', e.data);
};
worker.js:

javascript
Copy code
onmessage = (e) => {
  console.log('Message from main thread:', e.data);
  postMessage('Task completed');
};
</details>

<details> <summary><strong>70. What is PWA (Progressive Web App)?</strong></summary>
A Progressive Web App (PWA) is a type of application built using standard web technologies (HTML, CSS, and JavaScript) but offering similar performance and user experience to native apps. PWAs work offline, can be installed on devices, and are responsive.

Example:

javascript
Copy code
if ('serviceWorker' in navigator) {
  navigator.serviceWorker.register('/service-worker.js')
    .then((registration) => {
      console.log('Service Worker registered:', registration);
    })
    .catch((error) => {
      console.log('Service Worker registration failed:', error);
    });
}
</details>
<details> <summary><strong>71. Difference Between Single Page Application and Multi-Page Application</strong></summary>
Single Page Application (SPA): A web app that loads a single HTML page and dynamically updates as the user interacts with the app, providing a seamless experience (e.g., React).
Multi-Page Application (MPA): A traditional web application where each action (e.g., clicking a link) loads a new page from the server.
SPA Example: In React, navigation between components is handled without reloading the page.

MPA Example: Traditional web applications that reload a new page from the server when a link is clicked.

</details>
<details> <summary><strong>72. Explain API Calls and Their Process</strong></summary>
API calls are made to interact with external services or databases to fetch or manipulate data. In React, API calls can be made using fetch, axios, or other libraries.

Example of an API call using fetch:

javascript
Copy code
useEffect(() => {
  const fetchData = async () => {
    try {
      const response = await fetch('https://api.example.com/data');
      const data = await response.json();
      console.log(data);
    } catch (error) {
      console.error('Error fetching data:', error);
    }
  };

  fetchData();
}, []);
</details>
<details> <summary><strong>73. What is Optimization and How to Implement it in React JS?</strong></summary>
Optimization in React involves improving the performance of a React application by reducing unnecessary re-renders, minimizing network requests, and optimizing code execution. Some common techniques are memoization, code splitting, lazy loading, and more.

Example using React.memo:

javascript
Copy code
const MemoizedComponent = React.memo((props) => {
  // Only re-renders if props change
  return <div>{props.value}</div>;
});
Lazy Loading Example:

javascript
Copy code
const LazyComponent = React.lazy(() => import('./LazyComponent'));

<React.Suspense fallback={<div>Loading...</div>}>
  <LazyComponent />
</React.Suspense>
</details>
<details> <summary><strong>74. What is AMP (Accelerated Mobile Pages)?</strong></summary>
AMP is an open-source framework created to help web pages load faster on mobile devices by optimizing content for speed and performance. It uses a stripped-down version of HTML, CSS, and JavaScript.

Example of AMP HTML:

html
Copy code
<html ⚡>
  <head>
    <meta charset="utf-8">
    <script async src="https://cdn.ampproject.org/v0.js"></script>
    <style amp-custom>
      body { font-family: Arial, sans-serif; }
    </style>
  </head>
  <body>
    <h1>Welcome to AMP</h1>
    <p>This is a sample AMP page.</p>
  </body>
</html>
</details>
<details> <summary><strong>75. What is Page Layout Shift?</strong></summary>
Page Layout Shift refers to the unexpected shifting of web page content as the page loads, which negatively impacts user experience. This can happen if resources (like images or fonts) are loaded dynamically, causing elements to move around.

Fixing Layout Shifts Example:

css
Copy code
img {
  width: 100%;
  height: auto;
}
</details>
<details> <summary><strong>76. What is Microservices?</strong></summary>
Microservices is an architectural style where an application is developed as a collection of loosely coupled services, each responsible for a specific business functionality. Each service can be developed, deployed, and scaled independently.

Example: A large e-commerce platform might have microservices like payment processing, inventory management, user authentication, and product catalog, each developed as separate services.

</details>
<details> <summary><strong>77. Explain the `this` Keyword</strong></summary>
The this keyword refers to the current context in which a function is executing. It can refer to different objects depending on the function's call type, such as a method, an event handler, or a constructor function.

Example:

javascript
Copy code
const person = {
  name: 'Alice',
  greet() {
    console.log(this.name);  // Refers to person object
  }
};

person.greet();  // 'Alice'
</details>
<details> <summary><strong>78. What is a Semantic Element?</strong></summary>
Semantic elements are HTML tags that provide meaning to the content inside them, making the code more readable and accessible. These elements help search engines and developers understand the structure and importance of the content.

Example of Semantic Elements:

html
Copy code
<article>
  <header><h1>Article Title</h1></header>
  <section>
    <p>Content of the article...</p>
  </section>
  <footer>Author: John Doe</footer>
</article>
</details>
<details> <summary><strong>79. What is a CSS Object?</strong></summary>
A CSS object is an object in JavaScript that contains CSS properties and their values. You can dynamically apply styles to an element using a CSS object.

Example:

javascript
Copy code
const styles = {
  color: 'blue',
  backgroundColor: 'lightgray',
  padding: '10px',
};

return <div style={styles}>Styled Div</div>;
</details>

<details> <summary><strong>80. What is Redux?</strong></summary>
Redux is a predictable state container for JavaScript apps, used to manage the state of an application. It centralizes the state and allows components to access and modify it in a consistent and predictable way.

Example:

javascript
Copy code
const initialState = { count: 0 };

function reducer(state = initialState, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { ...state, count: state.count + 1 };
    case 'DECREMENT':
      return { ...state, count: state.count - 1 };
    default:
      return state;
  }
}

const store = createStore(reducer);
</details>
<details> <summary><strong>81. What is Observable in Redux?</strong></summary>
An observable in Redux is a pattern used to represent state as a stream of events that components can subscribe to and react to. It allows components to react to changes in state or other side-effects without directly querying the state.

Example: In combination with Redux-Saga or Redux-Observable, actions can be observed to trigger side effects like API calls.

javascript
Copy code
import { Observable } from 'rxjs';

const fetchDataObservable = new Observable((observer) => {
  fetch('/data')
    .then(response => response.json())
    .then(data => observer.next(data))
    .catch(err => observer.error(err));
});
</details>
<details> <summary><strong>82. What is Flux?</strong></summary>
Flux is an architecture for managing application state developed by Facebook. It emphasizes a unidirectional data flow, which makes state changes predictable and easier to trace.

Example: In Flux, the state is managed by a store, and actions are dispatched to the store to change the state.

javascript
Copy code
const store = {
  dispatch(action) {
    // Handle the action
  },
  getState() {
    // Return current state
  },
};
</details>
<details> <summary><strong>83. What is Higher-Order Component (HOC)?</strong></summary>
A Higher-Order Component is a function that takes a component and returns a new component with additional functionality. It’s used for code reuse, logic abstraction, and adding features to components.

Example:

javascript
Copy code
const withLoading = (WrappedComponent) => {
  return (props) => {
    if (props.isLoading) {
      return <div>Loading...</div>;
    }
    return <WrappedComponent {...props} />;
  };
};

const MyComponent = withLoading(MyComponent);
</details>
<details> <summary><strong>84. Difference Between Map and Reduce</strong></summary>
Map: It applies a function to each item in an array and returns a new array with the results.
Reduce: It accumulates the array items into a single value by applying a function.
Example of Map:

javascript
Copy code
const numbers = [1, 2, 3];
const squared = numbers.map(x => x * x);  // [1, 4, 9]
Example of Reduce:

javascript
Copy code
const numbers = [1, 2, 3];
const sum = numbers.reduce((acc, x) => acc + x, 0);  // 6
</details>
<details> <summary><strong>85. What is React JS and Its Pros and Cons?</strong></summary>
React JS is a JavaScript library for building user interfaces, primarily for single-page applications. It allows for building complex, interactive UIs through components.

Pros:

Component-based architecture
Virtual DOM for optimized performance
Strong community support
Cons:

Steeper learning curve for new developers
Large bundle size without proper optimization
</details>
<details> <summary><strong>86. What is Batching?</strong></summary>
Batching refers to the process of grouping multiple state updates into a single re-render to optimize performance. React batches state updates and re-renders in a single pass.

Example:

javascript
Copy code
setState({ count: 1 });
setState({ count: 2 });
// React batches these state updates and renders the component only once.
</details>
<details> <summary><strong>87. What is Diffing and Reconciliation?</strong></summary>
Diffing is the process React uses to compare the current and previous virtual DOM and determine the minimal set of changes needed to update the real DOM. Reconciliation is the process of applying those changes to the real DOM.

Example: React compares the previous and current virtual DOM trees and calculates the minimum set of changes to apply.

</details>
<details> <summary><strong>88. What is the `useRef` Hook?</strong></summary>
The useRef hook is used to persist values across renders without causing a re-render. It can also be used to reference DOM elements.

Example:

javascript
Copy code
const inputRef = useRef();
const focusInput = () => {
  inputRef.current.focus();  // Focus the input element
};

return <input ref={inputRef} />;
</details>
<details> <summary><strong>89. What is a Pure Component?</strong></summary>
A Pure Component is a React component that only re-renders when its props or state change. It implements a shallow comparison of props and state to optimize rendering.

Example:

javascript
Copy code
class PureComponentExample extends React.PureComponent {
  render() {
    return <div>{this.props.value}</div>;
  }
}
</details>

<details> <summary><strong>90. What is a Pure Function?</strong></summary>
A pure function is a function that always produces the same output for the same input and has no side effects. It does not modify any external state or variables.

Example:

javascript
Copy code
function add(a, b) {
  return a + b;  // This is a pure function
}
</details>
<details> <summary><strong>91. What is `useState`?</strong></summary>
useState is a React hook that allows you to add state to functional components. It returns a stateful value and a function to update it.

Example:

javascript
Copy code
const [count, setCount] = useState(0);

const increment = () => {
  setCount(count + 1);
};

return (
  <div>
    <p>{count}</p>
    <button onClick={increment}>Increment</button>
  </div>
);
</details>
<details> <summary><strong>92. What is `useEffect`?</strong></summary>
useEffect is a React hook that allows you to perform side effects in functional components. It runs after the render and can be used for things like data fetching, DOM manipulation, or subscriptions.

Example:

javascript
Copy code
useEffect(() => {
  console.log('Component mounted or updated');
}, [count]);  // This runs every time the `count` changes
</details>
<details> <summary><strong>93. What is `useSelector`?</strong></summary>
useSelector is a hook used to access the Redux store’s state in a functional component. It subscribes to the Redux store and re-renders the component whenever the selected state changes.

Example:

javascript
Copy code
const count = useSelector((state) => state.count);

return <div>{count}</div>;
</details>
<details> <summary><strong>94. What is `useDispatch`?</strong></summary>
useDispatch is a hook used to dispatch actions to the Redux store from within a functional component.

Example:

javascript
Copy code
const dispatch = useDispatch();

const increment = () => {
  dispatch({ type: 'INCREMENT' });
};

return <button onClick={increment}>Increment</button>;
</details>
<details> <summary><strong>95. How to Configure a Store and Create a Slice in Redux?</strong></summary>
To configure a store and create a slice, you need to use Redux Toolkit’s configureStore and createSlice functions.

Example:

javascript
Copy code
import { configureStore, createSlice } from '@reduxjs/toolkit';

const counterSlice = createSlice({
  name: 'counter',
  initialState: { count: 0 },
  reducers: {
    increment: (state) => { state.count += 1; },
    decrement: (state) => { state.count -= 1; },
  },
});

const store = configureStore({
  reducer: { counter: counterSlice.reducer },
});

export const { increment, decrement } = counterSlice.actions;
</details>
<details> <summary><strong>96. What are Actions in Redux?</strong></summary>
Actions in Redux are plain JavaScript objects that describe an event or action that occurred in the application. Each action must have a type field to indicate what happened.

Example:

javascript
Copy code
const incrementAction = { type: 'INCREMENT' };
const decrementAction = { type: 'DECREMENT' };
</details>
<details> <summary><strong>97. What is Redux Saga?</strong></summary>
Redux Saga is a middleware library used for handling side effects in Redux applications. It uses generator functions to manage asynchronous actions like data fetching.

Example:

javascript
Copy code
import { takeEvery, put } from 'redux-saga/effects';

function* incrementAsync() {
  yield delay(1000);  // Simulate async call
  yield put({ type: 'INCREMENT' });
}

function* watchIncrementAsync() {
  yield takeEvery('INCREMENT_ASYNC', incrementAsync);
}
</details>
<details> <summary><strong>98. What is Shadow DOM?</strong></summary>
The Shadow DOM is a web standard that allows developers to encapsulate a part of a DOM tree in a way that it is hidden from the main document. This helps in creating reusable components without worrying about CSS or JavaScript conflicts.

Example:

javascript
Copy code
const shadowRoot = document.getElementById('shadow-host').attachShadow({ mode: 'open' });
shadowRoot.innerHTML = '<p>This is inside the shadow DOM!</p>';
</details>
<details> <summary><strong>99. Class vs Functional Components</strong></summary>
Class Components: They are ES6 classes that can hold state and lifecycle methods.
Functional Components: They are simpler components that rely on hooks for managing state and side effects.
Example:

Class Component:

javascript
Copy code
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  render() {
    return <div>{this.state.count}</div>;
  }
}
Functional Component:

javascript
Copy code
const MyComponent = () => {
  const [count, setCount] = useState(0);
  return <div>{count}</div>;
};
</details>

<details> <summary><strong>100. What is the Lifecycle in a Class Component?</strong></summary>
In a class component, the lifecycle consists of several phases: mounting, updating, and unmounting. React provides lifecycle methods for each phase, such as componentDidMount, componentDidUpdate, and componentWillUnmount.

Example:

javascript
Copy code
class MyComponent extends React.Component {
  componentDidMount() {
    console.log('Component Mounted');
  }

  componentDidUpdate() {
    console.log('Component Updated');
  }

  componentWillUnmount() {
    console.log('Component Unmounted');
  }

  render() {
    return <div>Lifecycle Example</div>;
  }
}
</details>
<details> <summary><strong>101. What is the `componentShouldUpdate` Lifecycle Method?</strong></summary>
componentShouldUpdate is a lifecycle method that is called before the render method. It allows you to optimize performance by preventing unnecessary re-renders.

Example:

javascript
Copy code
class MyComponent extends React.Component {
  shouldComponentUpdate(nextProps, nextState) {
    if (nextState.count !== this.state.count) {
      return true;
    }
    return false;
  }

  render() {
    return <div>{this.state.count}</div>;
  }
}
</details>
<details> <summary><strong>102. State vs Props</strong></summary>
State: Data that is managed within a component and can be updated.
Props: Data passed to a component from a parent component, which cannot be directly modified by the child.
Example:

javascript
Copy code
const ParentComponent = () => {
  const parentData = 'Hello';
  return <ChildComponent message={parentData} />;
};

const ChildComponent = (props) => {
  return <div>{props.message}</div>;
};
</details>
<details> <summary><strong>103. How to Pass Data from Child to Parent Component?</strong></summary>
Data can be passed from a child component to a parent component via a callback function provided as a prop.

Example:

javascript
Copy code
const ParentComponent = () => {
  const handleData = (data) => {
    console.log(data);
  };

  return <ChildComponent sendData={handleData} />;
};

const ChildComponent = (props) => {
  return <button onClick={() => props.sendData('Data from child')}>Send Data</button>;
};
</details>
<details> <summary><strong>104. What are Controlled and Uncontrolled Components?</strong></summary>
Controlled Components: Components that are controlled by React state, where the input value is managed via useState or this.setState.
Uncontrolled Components: Components where the form data is handled by the DOM rather than React.
Example:

Controlled Component:
javascript
Copy code
const [value, setValue] = useState('');
const handleChange = (e) => setValue(e.target.value);

return <input type="text" value={value} onChange={handleChange} />;
Uncontrolled Component:
javascript
Copy code
const inputRef = useRef(null);

const handleSubmit = () => {
  alert(inputRef.current.value);
};

return <input ref={inputRef} type="text" />;
</details>
<details> <summary><strong>105. What is Stateless and Stateful Component?</strong></summary>
Stateless Components: Components that do not have any state and only render UI based on props.
Stateful Components: Components that have state and manage it within themselves.
Example:

Stateless Component:
javascript
Copy code
const StatelessComponent = (props) => {
  return <div>{props.text}</div>;
};
Stateful Component:
javascript
Copy code
class StatefulComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  render() {
    return <div>{this.state.count}</div>;
  }
}
</details>
<details> <summary><strong>106. What is Prop Drilling?</strong></summary>
Prop drilling refers to the process of passing data from a parent component to a deeply nested child component via multiple layers of intermediate components.

Example:

javascript
Copy code
const GrandparentComponent = () => {
  const message = 'Hello from Grandparent';
  return <ParentComponent message={message} />;
};

const ParentComponent = ({ message }) => {
  return <ChildComponent message={message} />;
};

const ChildComponent = ({ message }) => {
  return <div>{message}</div>;
};
</details>
<details> <summary><strong>107. How to Manage API Calls in React JS?</strong></summary>
API calls in React can be managed using hooks like useEffect to make calls when the component mounts, along with useState to store the fetched data.

Example:

javascript
Copy code
const [data, setData] = useState(null);

useEffect(() => {
  fetch('https://api.example.com/data')
    .then((response) => response.json())
    .then((result) => setData(result));
}, []);

return <div>{data ? JSON.stringify(data) : 'Loading...'}</div>;
</details>
<details> <summary><strong>108. Which Lifecycle Method Performs an API Call?</strong></summary>
In class components, componentDidMount is commonly used for API calls after the component has mounted. In functional components, useEffect serves a similar purpose.

Example (Class Component):

javascript
Copy code
class MyComponent extends React.Component {
  componentDidMount() {
    fetch('https://api.example.com/data')
      .then((response) => response.json())
      .then((data) => console.log(data));
  }

  render() {
    return <div>API Call in componentDidMount</div>;
  }
}
Example (Functional Component):

javascript
Copy code
useEffect(() => {
  fetch('https://api.example.com/data')
    .then((response) => response.json())
    .then((data) => console.log(data));
}, []);
</details>

<details> <summary><strong>109. What is Box-Sizing in CSS?</strong></summary>
box-sizing is a CSS property that controls how the total width and height of an element are calculated. The two main values are:

content-box: The width and height only include the content.
border-box: The width and height include the padding and border.
Example:

css
Copy code
.box {
  box-sizing: border-box;
  width: 100px;
  padding: 10px;
  border: 5px solid black;
}
</details>
<details> <summary><strong>110. Absolute vs Relative in CSS?</strong></summary>
Absolute: The element is positioned relative to its nearest positioned ancestor or the initial containing block.
Relative: The element is positioned relative to its normal position in the document flow.
Example:

css
Copy code
.absolute {
  position: absolute;
  top: 20px;
  left: 50px;
}

.relative {
  position: relative;
  top: 10px;
  left: 30px;
}
</details>
<details> <summary><strong>111. What is Pseudo-Class?</strong></summary>
A pseudo-class is used to define the special state of an element, such as when it's hovered over, focused, or selected.

Example:

css
Copy code
a:hover {
  color: red;
}

input:focus {
  border-color: blue;
}
</details>
<details> <summary><strong>112. What is Modules CSS?</strong></summary>
CSS Modules are a way to scope CSS styles to the component. This prevents style conflicts by generating unique class names for each class.

Example:

css
Copy code
/* styles.module.css */
.button {
  background-color: blue;
}
javascript
Copy code
import styles from './styles.module.css';

const Button = () => <button className={styles.button}>Click me</button>;
</details>
<details> <summary><strong>113. Difference Between Reset vs Normalized CSS?</strong></summary>
Reset CSS: Resets all browser default styles to a consistent baseline.
Normalize CSS: Preserves useful default styles but fixes common bugs across browsers.
Example:

Reset CSS:
css
Copy code
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
Normalize CSS:
css
Copy code
/* Normalize styles to make them consistent across browsers */
html {
  font-family: sans-serif;
}
</details>
<details> <summary><strong>114. What Are Pseudo-Elements and Pseudo-Classes?</strong></summary>
Pseudo-elements: Target parts of an element (e.g., ::before, ::after).
Pseudo-classes: Target an element's special state (e.g., :hover, :focus).
Example:

Pseudo-element:
css
Copy code
p::before {
  content: "Note: ";
  font-weight: bold;
}
Pseudo-class:
css
Copy code
button:hover {
  background-color: blue;
}
</details>
<details> <summary><strong>115. How to Call Multiple APIs at One Time?</strong></summary>
You can call multiple APIs simultaneously using Promise.all or Promise.allSettled.

Example:

javascript
Copy code
Promise.all([fetch('api1'), fetch('api2')])
  .then(([response1, response2]) => {
    return Promise.all([response1.json(), response2.json()]);
  })
  .then(([data1, data2]) => {
    console.log(data1, data2);
  });
</details>
<details> <summary><strong>116. What is Redux?</strong></summary>
Redux is a state management library for JavaScript apps. It helps to manage the state of an entire application using a single store.

Example:

javascript
Copy code
const initialState = { count: 0 };

function counterReducer(state = initialState, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { ...state, count: state.count + 1 };
    default:
      return state;
  }
}
</details>
<details> <summary><strong>117. What is Context API?</strong></summary>
The React Context API provides a way to pass data through the component tree without manually passing props down at every level.

Example:

javascript
Copy code
const MyContext = React.createContext();

const Parent = () => {
  return (
    <MyContext.Provider value="Hello from context">
      <Child />
    </MyContext.Provider>
  );
};

const Child = () => {
  const contextValue = useContext(MyContext);
  return <div>{contextValue}</div>;
};
</details>
<details> <summary><strong>118. What is Prop Drilling?</strong></summary>
Prop drilling refers to the process of passing data from a parent component down to a deeply nested child component through multiple intermediate components.

Example:

javascript
Copy code
const ParentComponent = () => {
  const data = 'Hello World';
  return <ChildComponent data={data} />;
};

const ChildComponent = ({ data }) => {
  return <div>{data}</div>;
};
</details>

<details> <summary><strong>119. What is Styled Component?</strong></summary>
Styled-components is a library for styling React components using tagged template literals. It allows you to write CSS directly in your JavaScript.

Example:

javascript
Copy code
import styled from 'styled-components';

const Button = styled.button`
  background-color: blue;
  color: white;
  padding: 10px;
`;

const App = () => <Button>Click Me</Button>;
</details>
<details> <summary><strong>120. What is Doctype in HTML?</strong></summary>
<!DOCTYPE> declaration defines the document type and version of HTML being used. It must be placed at the very beginning of the HTML document.

Example:

html
Copy code
<!DOCTYPE html>
<html>
  <head>
    <title>Example</title>
  </head>
  <body>
    <p>Hello, world!</p>
  </body>
</html>
</details>
<details> <summary><strong>121. What Are Meta Tags?</strong></summary>
Meta tags provide metadata about the HTML document, like the character set, author, description, or keywords. These tags are placed inside the <head> element.

Example:

html
Copy code
<meta charset="UTF-8">
<meta name="description" content="Learn web development">
</details>
<details> <summary><strong>122. What Are Semantic Elements?</strong></summary>
Semantic elements clearly describe their meaning in a human- and machine-readable way. Examples include <article>, <section>, <header>, and <footer>.

Example:

html
Copy code
<article>
  <h2>Article Title</h2>
  <p>Article content...</p>
</article>
</details>
<details> <summary><strong>123. What Are Styled-Components?</strong></summary>
Styled-components allow you to define component-level styles with a clean, JavaScript-based syntax. It enables automatic CSS scoping for each component.

Example:

javascript
Copy code
import styled from 'styled-components';

const Wrapper = styled.div`
  display: flex;
  align-items: center;
  justify-content: center;
`;

const App = () => (
  <Wrapper>
    <h1>Welcome to Styled Components!</h1>
  </Wrapper>
);
</details>
<details> <summary><strong>124. What is Sass?</strong></summary>
Sass (Syntactically Awesome Stylesheets) is a CSS preprocessor that adds features like variables, nested rules, and mixins to make CSS more maintainable.

Example:

scss
Copy code
$primary-color: #3498db;

.button {
  background-color: $primary-color;
  color: white;
}
</details>
<details> <summary><strong>125. What is Module CSS?</strong></summary>
CSS Modules are a way to scope styles locally to the component they belong to, avoiding global style conflicts.

Example:

css
Copy code
/* button.module.css */
.button {
  background-color: green;
}
javascript
Copy code
import styles from './button.module.css';

const Button = () => <button className={styles.button}>Click Me</button>;
</details>
<details> <summary><strong>126. How to Optimize Your Component?</strong></summary>
You can optimize components in React by using techniques such as memoization, lazy loading, avoiding unnecessary re-renders, and splitting the code.

Example:

javascript
Copy code
import React, { memo } from 'react';

const ExpensiveComponent = memo(() => {
  // This component will only re-render if props change
  return <div>Expensive Component</div>;
});
</details>
<details> <summary><strong>127. What is UseState?</strong></summary>
useState is a hook used to add state to functional components. It returns an array with two elements: the current state and a function to update it.

Example:

javascript
Copy code
const [count, setCount] = useState(0);

const increment = () => setCount(count + 1);
</details>
<details> <summary><strong>128. What is UseEffect?</strong></summary>
useEffect is a hook that allows you to perform side effects in functional components, such as fetching data, subscribing to events, or manually changing the DOM.

Example:

javascript
Copy code
useEffect(() => {
  fetchData();
}, []); // Runs once after the component mounts
</details>
<details> <summary><strong>129. What Are Class Components?</strong></summary>
Class components are the traditional way of defining components in React. They extend from React.Component and can hold state and lifecycle methods.

Example:

javascript
Copy code
class MyComponent extends React.Component {
  state = { count: 0 };

  render() {
    return <div>{this.state.count}</div>;
  }
}
</details>
<details> <summary><strong>130. What is ComponentShouldUpdate?</strong></summary>
componentShouldUpdate is a lifecycle method in class components that determines whether the component should re-render or not. It is used for performance optimization.

Example:

javascript
Copy code
class MyComponent extends React.Component {
  shouldComponentUpdate(nextProps, nextState) {
    return nextState.count !== this.state.count;
  }
}
</details>

<details> <summary><strong>131. Difference Between Functional and Class Components</strong></summary>
Class Components: Use ES6 class syntax, can hold state and lifecycle methods, and extend React.Component.
Functional Components: Simpler, use functions to define components, and can now hold state and side effects using hooks.
Example:

Class Component:
javascript
Copy code
class MyClassComponent extends React.Component {
  render() {
    return <div>Hello, Class Component!</div>;
  }
}
Functional Component:
javascript
Copy code
const MyFunctionalComponent = () => <div>Hello, Functional Component!</div>;
</details>
<details> <summary><strong>132. What Are State and Props?</strong></summary>
State: Represents data that can change over time and is managed within the component.
Props: Short for properties, are used to pass data from a parent component to a child component.
Example:

javascript
Copy code
// State example
const [count, setCount] = useState(0);

// Props example
const Parent = () => <Child name="John" />;
const Child = (props) => <div>Hello {props.name}</div>;
</details>
<details> <summary><strong>133. What is Prop Drilling?</strong></summary>
Prop drilling is the process of passing data from a parent component to deeply nested child components through props.

Example:

javascript
Copy code
const Parent = () => {
  const data = "Hello!";
  return <Child data={data} />;
};

const Child = ({ data }) => <GrandChild data={data} />;

const GrandChild = ({ data }) => <div>{data}</div>;
</details>
<details> <summary><strong>134. How to Pass Data from Child to Parent Component?</strong></summary>
Data can be passed from a child to a parent component using callback functions passed as props.

Example:

javascript
Copy code
const Parent = () => {
  const handleData = (data) => {
    console.log(data);
  };
  
  return <Child onData={handleData} />;
};

const Child = ({ onData }) => {
  onData("Hello from Child!");
  return <div>Child Component</div>;
};
</details>
<details> <summary><strong>135. What is Context API?</strong></summary>
The Context API is a way to share values between components without having to explicitly pass props through every level of the tree.

Example:

javascript
Copy code
const MyContext = React.createContext();

const Parent = () => (
  <MyContext.Provider value="Hello from Context">
    <Child />
  </MyContext.Provider>
);

const Child = () => {
  const value = useContext(MyContext);
  return <div>{value}</div>;
};
</details>
<details> <summary><strong>136. What Do You Prefer, Redux or Context API, and Why?</strong></summary>
Redux is often preferred for complex state management needs, where the application involves intricate state flows and asynchronous actions. Context API is more suitable for smaller applications or to pass data without needing a full state management solution.

</details>
<details> <summary><strong>137. What is Action Creator?</strong></summary>
Action creators are functions that return action objects. They help in creating actions for Redux.

Example:

javascript
Copy code
const addItem = (item) => ({
  type: 'ADD_ITEM',
  payload: item
});
</details>
<details> <summary><strong>138. What is Saga?</strong></summary>
Redux-Saga is a middleware for managing side effects in Redux. It listens to actions dispatched to the store and runs the necessary logic asynchronously.

Example:

javascript
Copy code
import { takeEvery, call, put } from 'redux-saga/effects';

function* fetchData() {
  const data = yield call(fetch, 'api/data');
  yield put({ type: 'DATA_FETCHED', data });
}

export default function* rootSaga() {
  yield takeEvery('FETCH_DATA', fetchData);
}
</details>
<details> <summary><strong>139. How to Call API with Saga?</strong></summary>
To call an API with Saga, use call to execute the API request and put to dispatch the result.

Example:

javascript
Copy code
function* fetchData() {
  const response = yield call(fetch, 'https://api.example.com/data');
  const data = yield response.json();
  yield put({ type: 'DATA_FETCHED', payload: data });
}
</details>
<details> <summary><strong>140. How to Auto-Call API by Redux and Saga?</strong></summary>
You can automatically trigger an API call using Redux-Saga by dispatching an action and setting up a watcher function with takeEvery or takeLatest.

Example:

javascript
Copy code
function* fetchDataOnMount() {
  yield put({ type: 'FETCH_DATA' });
}

function* rootSaga() {
  yield takeEvery('FETCH_DATA', fetchData);
}
</details>
<details> <summary><strong>141. What is Jest and React Testing Library?</strong></summary>
Jest: A JavaScript testing framework for running unit tests.
React Testing Library: A set of utilities to test React components in a way that mimics how the app will be used by end-users.
Example:

javascript
Copy code
import { render, screen } from '@testing-library/react';
import MyComponent from './MyComponent';

test('displays text', () => {
  render(<MyComponent />);
  expect(screen.getByText('Hello World')).toBeInTheDocument();
});
</details>

<details> <summary><strong>142. Optimization in React</strong></summary>
Optimization in React involves techniques to ensure smooth performance, such as minimizing unnecessary re-renders and optimizing resource-heavy operations.

Techniques:

Memoization: Using React.memo or useMemo to avoid unnecessary renders.
Lazy Loading: Using React.lazy and Suspense to load components only when needed.
Use of Pure Components: Avoiding re-renders by making components pure.
Example:

javascript
Copy code
const MyComponent = React.memo(({ data }) => {
  return <div>{data}</div>;
});
</details>
<details> <summary><strong>143. Explain useCallback and useMemo Hooks</strong></summary>
useCallback: Returns a memoized version of a function that only changes if one of the dependencies changes. It's useful for passing callbacks to child components without causing unnecessary re-renders.
Example:

javascript
Copy code
const memoizedCallback = useCallback(() => {
  // Function logic
}, [dependencies]);
useMemo: Memoizes a value and only recalculates it when one of the dependencies changes.
Example:

javascript
Copy code
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
</details>
<details> <summary><strong>144. Explain the New Features of React-Router</strong></summary>
React Router v6 introduced several new features, including:

Nested Routes: Simplified route nesting for better readability and code splitting.
Routes Element: Routes replaces Switch for rendering matched routes.
Relative Linking: Supports relative paths for navigation.
useNavigate: A hook for programmatic navigation.
Example:

javascript
Copy code
import { Routes, Route } from 'react-router-dom';

const App = () => (
  <Routes>
    <Route path="/" element={<Home />} />
    <Route path="/about" element={<About />} />
  </Routes>
);
</details>
<details> <summary><strong>145. Give an Example of Object Destructuring</strong></summary>
Object destructuring is a JavaScript feature that allows extracting values from objects into variables.

Example:

javascript
Copy code
const user = { name: 'John', age: 30 };
const { name, age } = user;
console.log(name); // John
console.log(age);  // 30
</details>
<details> <summary><strong>146. What Are Synthetic Events in React JS?</strong></summary>
Synthetic events are React's normalized events, which are wrapped around the browser's native events. They provide consistent behavior across different browsers.

Example:

javascript
Copy code
const handleClick = (event) => {
  event.preventDefault();
  console.log('Button clicked');
};

return <button onClick={handleClick}>Click Me</button>;
</details>
<details> <summary><strong>147. How to Check Your Event Working Properly in Different Browsers?</strong></summary>
To ensure compatibility across browsers, use tools like:

Browser Developer Tools: Check for errors and differences.
Polyfills: Use polyfills for features not supported in all browsers.
React's Synthetic Events: React’s event system abstracts away browser-specific differences.
</details>
<details> <summary><strong>148. What Are the Redux Components?</strong></summary>
Redux components include:

Store: Holds the application state.
Actions: Objects that describe changes to the state.
Reducers: Functions that handle state updates based on actions.
Dispatch: Sends actions to the store.
Selectors: Functions to access specific pieces of state.
Example:

javascript
Copy code
const rootReducer = (state = initialState, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    default:
      return state;
  }
};
</details>
<details> <summary><strong>149. Explain Lazy Loading in Detail in React JS</strong></summary>
Lazy loading in React allows components to be loaded only when needed, reducing the initial loading time.

Example:

javascript
Copy code
const MyComponent = React.lazy(() => import('./MyComponent'));

const App = () => (
  <Suspense fallback={<div>Loading...</div>}>
    <MyComponent />
  </Suspense>
);
</details>
<details> <summary><strong>150. What Are the Limitations of React JS?</strong></summary>
Some limitations of React include:

SEO: React is not SEO-friendly out of the box, though this can be overcome with server-side rendering (SSR).
Performance: Overuse of state can lead to performance issues.
Learning Curve: React's JSX syntax and hooks can be confusing for beginners.
</details>

<details> <summary><strong>151. What is Micro Front-End?</strong></summary>
Micro front-end is an architectural style where a front-end app is decomposed into smaller, independent pieces. Each part is developed, deployed, and maintained by a separate team.

Example:

Different micro front-end applications could be responsible for different sections of a website, like user profiles or shopping carts, each developed independently.
</details>
<details> <summary><strong>152. Why Do We Need React JS? Explain in Detail</strong></summary>
React is a popular JavaScript library because:

Declarative: Makes it easier to create interactive UIs.
Component-Based: Components can be reused, leading to better code maintainability.
Virtual DOM: React uses a virtual DOM to improve performance by reducing unnecessary DOM manipulations.
Example:

javascript
Copy code
function MyComponent() {
  return <h1>Hello, world!</h1>;
}
</details>
<details> <summary><strong>153. How to Set Initial Value in Redux?</strong></summary>
The initial value in Redux is set in the reducer by defining the initial state.

Example:

javascript
Copy code
const initialState = { count: 0 };

const counterReducer = (state = initialState, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    default:
      return state;
  }
};
</details>
<details> <summary><strong>154. What is SVG in HTML?</strong></summary>
SVG (Scalable Vector Graphics) is an XML-based format for vector images. It allows images to scale without losing quality, making it ideal for responsive designs.

Example:

html
Copy code
<svg width="100" height="100">
  <circle cx="50" cy="50" r="40" stroke="black" stroke-width="3" fill="red" />
</svg>
</details>
<details> <summary><strong>155. What is Charset in HTML?</strong></summary>
Charset (Character Set) defines the character encoding used to display text in a webpage. It ensures the text is rendered correctly.

Example:

html
Copy code
<meta charset="UTF-8">
</details>
<details> <summary><strong>156. What is the Drag and Drop API in HTML5?</strong></summary>
The Drag and Drop API allows users to drag elements within the browser and drop them into a different location. It's commonly used for file uploads or rearranging UI components.

Example:

html
Copy code
<div id="dragElement" draggable="true">Drag me</div>
javascript
Copy code
document.getElementById("dragElement").addEventListener("dragstart", (event) => {
  event.dataTransfer.setData("text", event.target.id);
});
</details>
<details> <summary><strong>157. What is Canvas in HTML5?</strong></summary>
The <canvas> element in HTML5 is used to draw graphics, such as images, shapes, and animations, using JavaScript.

Example:

html
Copy code
<canvas id="myCanvas" width="500" height="500"></canvas>
<script>
  var canvas = document.getElementById('myCanvas');
  var ctx = canvas.getContext('2d');
  ctx.fillStyle = 'green';
  ctx.fillRect(10, 10, 150, 100);
</script>
</details>
<details> <summary><strong>158. What is the Difference Between 2nd and 3rd Line for Below Code Snippet in React JS</strong></summary>
The second line of the code (setState('rohit patel');) updates the state, while the third line (state = 'rohit patel';) directly modifies the state variable, which is not allowed in React because state should not be mutated directly.

Code Snippet:

javascript
Copy code
let [state, setState] = useState('rohit');
setState('rohit patel');  // Correct way to update state
state = 'rohit patel';    // Incorrect way, direct mutation of state
</details>
<details> <summary><strong>159. Create Todo App and Implement These Functionalities (Add Todo, Complete Todo, Edit Todo, Delete Todo)</strong></summary>
A simple Todo App in React can be implemented using state and event handlers.

Example:

javascript
Copy code
import React, { useState } from 'react';

function TodoApp() {
  const [todos, setTodos] = useState([]);
  const [newTodo, setNewTodo] = useState('');

  const addTodo = () => {
    setTodos([...todos, { text: newTodo, completed: false }]);
    setNewTodo('');
  };

  const toggleTodo = (index) => {
    const updatedTodos = [...todos];
    updatedTodos[index].completed = !updatedTodos[index].completed;
    setTodos(updatedTodos);
  };

  const deleteTodo = (index) => {
    const updatedTodos = todos.filter((_, i) => i !== index);
    setTodos(updatedTodos);
  };

  return (
    <div>
      <input 
        type="text" 
        value={newTodo} 
        onChange={(e) => setNewTodo(e.target.value)} 
      />
      <button onClick={addTodo}>Add Todo</button>
      <ul>
        {todos.map((todo, index) => (
          <li key={index}>
            <input 
              type="checkbox" 
              checked={todo.completed} 
              onChange={() => toggleTodo(index)} 
            />
            {todo.text}
            <button onClick={() => deleteTodo(index)}>Delete</button>
          </li>
        ))}
      </ul>
    </div>
  );
}
</details>
<details> <summary><strong>160. Create Counter App and Implement These Functionalities (Start Counter, Pause Counter, Reset Counter)</strong></summary>
A simple counter app can be created using React state and setInterval.

Example:

javascript
Copy code
import React, { useState, useEffect } from 'react';

function CounterApp() {
  const [count, setCount] = useState(0);
  const [isRunning, setIsRunning] = useState(false);

  useEffect(() => {
    let interval;
    if (isRunning) {
      interval = setInterval(() => {
        setCount((prevCount) => prevCount + 1);
      }, 1000);
    } else {
      clearInterval(interval);
    }
    return () => clearInterval(interval);
  }, [isRunning]);

  const resetCounter = () => setCount(0);

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={() => setIsRunning(!isRunning)}>
        {isRunning ? 'Pause' : 'Start'}
      </button>
      <button onClick={resetCounter}>Reset</button>
    </div>
  );
}
</details>

<details> <summary><strong>161. What is Selectors in CSS?</strong></summary>
CSS selectors are used to select and style HTML elements. These selectors target elements based on various attributes like class, id, element type, etc.

Example:

css
Copy code
/* Select all paragraphs */
p {
  color: blue;
}

/* Select element with id "header" */
#header {
  background-color: yellow;
}

/* Select elements with class "button" */
.button {
  padding: 10px;
}
</details>
<details> <summary><strong>162. What is Sass in CSS?</strong></summary>
Sass (Syntactically Awesome Stylesheets) is a CSS preprocessor that extends CSS with features like variables, nested rules, and mixins, which make writing CSS more efficient.

Example:

scss
Copy code
$primary-color: #3498db;

.header {
  background-color: $primary-color;
  h1 {
    color: white;
  }
}
</details>
<details> <summary><strong>163. Explain Features of React JS</strong></summary>
React JS offers several features, including:

Component-Based: Breaks the UI into reusable components.
Declarative: React uses a declarative approach for building UIs, making the code easier to read and maintain.
Virtual DOM: React uses a virtual DOM to optimize rendering.
Hooks: Allows you to use state and other features without writing a class.
</details>
<details> <summary><strong>164. Explain Disadvantages of React JS</strong></summary>
Some disadvantages of React JS include:

Steep Learning Curve: React's concepts like JSX, hooks, and state management may be challenging for beginners.
High Pace of Changes: React frequently releases updates, which may require constant learning.
Large Bundle Size: React can lead to large JavaScript files if not optimized properly.
</details>
<details> <summary><strong>165. How to Handle Pagination and List Scrolling in React JS If the Quantity of Data is More Than (Explain React Window and React Virtualization)</strong></summary>
React Window and React Virtualization are libraries used to efficiently render large lists by only rendering visible items in the viewport, improving performance.

Example using React Window:

javascript
Copy code
import { FixedSizeList as List } from 'react-window';

function App() {
  const data = new Array(1000).fill('Item');
  return (
    <List height={400} itemCount={data.length} itemSize={35} width={300}>
      {({ index, style }) => (
        <div style={style}>{data[index]}</div>
      )}
    </List>
  );
}
</details>
<details> <summary><strong>166. What is Forward Ref in React JS?</strong></summary>
forwardRef is a higher-order component that allows you to forward a ref from a parent component to a child component.

Example:

javascript
Copy code
const Input = React.forwardRef((props, ref) => {
  return <input ref={ref} {...props} />;
});

function Parent() {
  const inputRef = useRef();
  return <Input ref={inputRef} />;
}
</details>
<details> <summary><strong>167. Explain SetState is Synchronous or Asynchronous in UseState Hook</strong></summary>
setState in React (when using useState) is asynchronous, meaning it doesn't immediately update the state after it is called. React batches state updates to optimize performance.

Example:

javascript
Copy code
const [count, setCount] = useState(0);

const increment = () => {
  setCount(count + 1); // This will be batched
  console.log(count);   // Logs the old state value
};
</details>
<details> <summary><strong>168. Create Custom Hook for API Call</strong></summary>
A custom hook can be created to abstract away the logic for making API calls in React components.

Example:

javascript
Copy code
import { useState, useEffect } from 'react';

function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetch(url)
      .then((response) => response.json())
      .then((data) => {
        setData(data);
        setLoading(false);
      });
  }, [url]);

  return { data, loading };
}

function App() {
  const { data, loading } = useFetch('https://api.example.com/data');

  if (loading) return <div>Loading...</div>;
  return <div>{JSON.stringify(data)}</div>;
}
</details>
<details> <summary><strong>169. What is Accessibility?</strong></summary>
Accessibility in web development refers to the practice of making websites usable by people with various disabilities, such as visual impairments, hearing loss, or mobility challenges.

Example:

Use semantic HTML elements, like <button> instead of <div>, and add aria-* attributes to improve accessibility.
</details>
<details> <summary><strong>170. What is Position in CSS?</strong></summary>
The position property in CSS specifies how an element is positioned on the page. It can have values like static, relative, absolute, and fixed.

Example:

css
Copy code
/* Absolute positioning */
.absolute {
  position: absolute;
  top: 10px;
  left: 20px;
}

/* Fixed positioning */
.fixed {
  position: fixed;
  bottom: 0;
  right: 0;
}
</details>

<details> <summary><strong>171. What is React Fiber?</strong></summary>
React Fiber is a complete rewrite of the React core algorithm, enabling incremental rendering and improved UI performance. It allows React to pause rendering work and come back to it later, leading to smoother animations and quicker updates.

Example:

Fiber allows React to split the rendering process into chunks, improving responsiveness in large apps.
</details>
<details> <summary><strong>172. Explain Inline Element or Block Element</strong></summary>
Inline Elements: Do not start on a new line and only take up as much width as necessary (e.g., <span>, <a>).
Block Elements: Start on a new line and take up the full width available (e.g., <div>, <p>).
Example:

html
Copy code
<p>This is a block element</p>
<span>This is an inline element</span>
</details>
<details> <summary><strong>173. Difference Between Normal Export and Default Export</strong></summary>
Normal Export: You can export multiple variables, functions, or objects.

javascript
Copy code
export const x = 10;
export function add() { return 5; }
Default Export: Only one export per file, and it can be imported without curly braces.

javascript
Copy code
const x = 10;
export default x;
</details>
<details> <summary><strong>174. Create Todo App and Implement These Functionalities (Add Todo, Complete Todo, Edit Todo, Delete Todo)</strong></summary>
A simple Todo app in React can be created with the following functionalities:

Example:

javascript
Copy code
import React, { useState } from 'react';

function TodoApp() {
  const [todos, setTodos] = useState([]);
  const [newTodo, setNewTodo] = useState('');

  const addTodo = () => {
    setTodos([...todos, { text: newTodo, completed: false }]);
    setNewTodo('');
  };

  const toggleComplete = (index) => {
    const newTodos = [...todos];
    newTodos[index].completed = !newTodos[index].completed;
    setTodos(newTodos);
  };

  const deleteTodo = (index) => {
    setTodos(todos.filter((_, i) => i !== index));
  };

  const editTodo = (index, newText) => {
    const newTodos = [...todos];
    newTodos[index].text = newText;
    setTodos(newTodos);
  };

  return (
    <div>
      <input
        type="text"
        value={newTodo}
        onChange={(e) => setNewTodo(e.target.value)}
      />
      <button onClick={addTodo}>Add Todo</button>

      <ul>
        {todos.map((todo, index) => (
          <li key={index}>
            <span
              style={{ textDecoration: todo.completed ? 'line-through' : '' }}
              onClick={() => toggleComplete(index)}
            >
              {todo.text}
            </span>
            <button onClick={() => editTodo(index, prompt('Edit todo:', todo.text))}>
              Edit
            </button>
            <button onClick={() => deleteTodo(index)}>Delete</button>
          </li>
        ))}
      </ul>
    </div>
  );
}
</details>
