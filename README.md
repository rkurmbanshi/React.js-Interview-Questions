# React.js-Interview-Questions

<details>
  <summary><strong>How to create custom hooks</strong></summary>
  
  React Hooks are a powerful feature in React that allow developers to use state and other React features in functional components. Creating custom hooks can help you  extract reusable logic from your components, making them more maintainable and easier to understand. Here's a step-by-step guide on how to create custom hooks in React:

Step 1: Identify the reusable logic
First, identify the logic that you want to extract from your component. It could be anything from managing state to handling API calls.

Step 2: Create a function that uses the useState or useEffect hooks
Next, create a function that uses the useState or useEffect hooks, depending on what your custom hook needs to do. You can also use other built-in hooks like useContext or useReducer if needed.

For example, if you want to create a custom hook that manages the state of a form input, you can create a function like this:

  ```js
  import { useState } from 'react';

  function useInput(initialValue) {
    const [value, setValue] = useState(initialValue);

    function handleChange(event) {
      setValue(event.target.value);
    }

    return [value, handleChange];
  }

  ```
  This hook uses the useState hook to manage the state of the input value and returns an array with the current value and a handleChange function that updates the value.

Step 3: Export the custom hook
Finally, export the custom hook so that it can be used in other components. You can name the custom hook whatever you like, as long as it starts with the prefix "use" to indicate that it's a hook.

```js
 export default useInput;
  ```
  
  Step 4: Use the custom hook in your components
Now that you've created your custom hook, you can use it in your components just like you would use any other hook:
  
  ```js
  import useInput from './useInput';

function MyForm() {
  const [name, setName] = useInput('');

  function handleSubmit(event) {
    event.preventDefault();
    console.log(name);
  }

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" value={name} onChange={setName} />
      <button type="submit">Submit</button>
    </form>
  );
}
  ```
  
  In this example, the useInput hook is used to manage the state of the input value in a form.

That's it! With just a few simple steps, you've created a custom hook that can be reused in any number of components.

</details>

<details>
  <summary><strong>How to react update DOM!</strong></summary>
  
  React updates the DOM (Document Object Model) through a process called reconciliation. When a component's state or props change, React will re-render the component and compare the new output with the old output. If there are differences, React will update the DOM accordingly. Here are the steps that React takes to update the DOM:

1. React updates the component's state or props.
2. React re-renders the component and generates a new virtual DOM tree.
3. React compares the new virtual DOM tree with the previous one to determine the differences (known as "diffing").
4. React generates a minimal set of DOM operations to update only the parts of the DOM that have changed.
5. React applies the DOM updates to the actual browser DOM.
  
Here's an example to illustrate how React updates the DOM:
  ```js
  import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={handleClick}>Increment</button>
    </div>
  );
}

  ```
  
  In this example, we have a simple Counter component that displays a count and a button that increments the count when clicked. When the button is clicked, React updates the count state and re-renders the component. React then generates a new virtual DOM tree and compares it with the previous one. In this case, the only difference is the updated count value. React generates a DOM update to change the text content of the p element to the new count value. Finally, React applies the DOM update to the browser DOM, and the count is updated on the screen.

Overall, React's process for updating the DOM is optimized for performance and efficiency, allowing for fast and responsive user interfaces.
  
</details>

- What is VDOM

- State management is react

- What is Prop drilling

- What is redux

- What is middleware in redux

- What is webpack

- How to use a style in react.js

- How to handle form and its validation in react

- What is context API in react

- Explain local storage and session storage and how to secure both storages

- What are web workers

- What is PWA

- Difference between single page application and multipage application

- Explain API calls and its process

- What is the optimization and how to implement it in react js? 

- What is amp

- What is page layout shift 

- What is microservices

- Explain this keyword

- What is the semantic element

- What is CSS object

- What is redux

- What is observable in redux

- What is flux

- What is higher-order component

- Difference between Map and reduce

- What is react js and its pros and cons

- What is batching

- What is diffing and reconciliation

- What is the useRef hook

- What is pure component

- What is pure function

- What is useState

- What is useEffect

- What is useSelector

- What is useDispatch

- How to configure a store and create a slice in redux

- What are actions in redux

- What is saga

- What is shadow dom

- class/functional component

- useMemo/useCallback

- useMemo/react.memo

- What is the lifecycle in the class component

- What is component Should Update lifecycle method

- State v/s props

- How to pass data by child component to the parent component

- What are controlled and uncontrolled component

- What is stateless and stateful component

- What is prop drilling

- How to manage API calls in react js

- Which lifecycle method performs an API call

- How many ways to use CSS

- What is box-sizing in CSS

- Absolute v/s relative in CSS

- What is Pseudo class

- What is modules css

- Difference between reset vs normalized CSS?

- What are pseudo-elements and pseudo-classes

- How to call multiple APIs in one time

- What is redux

- What is context API

- What is prop drilling

- What styled component

- What is doctype in HTML

- What are meta tags

- What are semantic elements

- What are styled-components

- What is sass

- What is module CSS

- How to optimize your component

- What is useState

- What is useEffect

- What are class components

- What is component should update 

- Diff between functional and class components

- What are state and props

- What is prop drilling

- How to pass data from child to parent component

- What is context API

- What you prefer redux and why not prefer context API

- What is action creator

- What is saga

- How to call API with saga

- How to auto-call API by redux and saga

- What is jest and react testing library

- Optimization in react

- Explain useCallback and usememo hook

- Explain the new features of new version of react-router

- Give an example of object destructuring

- What are the Synthetic Events in react js

- How to check your event working properly in different browsers

- What are the redux components

- Explain lazy loading in detail in react js

- What is the limitations of react js

- What is micro front-end

- Why we need react js explain in detail

- How to set Initial value in redux

- What is SVG in html

- What is charset in html

- What is drag and drop api in html5

- What is canvas in html5

- What is the difference between 2nd and 3rd line for bellow code snippet in react js<br/>

  line 1: let [state, setState] = useState('rohit');<br/>
  line 2: setState('rohit patel');<br/>
  line 3: state = 'rohit patel';
  
- Create todo app and impliment these functionality (Add todo, complete todo, edit todo, delete todo)

- Create a counter app and impliment these functionality (Start counter, pause counter, reset counter]

- What is selectors in css

- What is Sass in css

- Explain Features of react js

- Explain Disadvantages of react js

- How to handle pagination and list scrolling in react js If the quantity of data is more then [Explain react window and react virtualization]

- What is farward ref in react js

- Explain setState is synchronous or asynchronous in useState Hook<br/>
  const [state, setState] = useState("");

- Create custom hook for the API call

- What is accessibility

- What is position in CSS

