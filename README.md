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

<details>
  <summary><strong>What is VDOM in react js</strong></summary>

  In a traditional web application, the browser maintains a Document Object Model (DOM) which is a tree-like structure that represents the HTML elements in the web page. Whenever the state of the application changes, the browser needs to update the DOM to reflect those changes. This process of updating the DOM can be slow and resource-intensive, especially when there are a lot of changes.

ReactJS solves this problem by introducing the concept of a Virtual DOM. The Virtual DOM is a lightweight representation of the actual DOM. When the state of the application changes, ReactJS creates a new Virtual DOM tree and compares it with the previous Virtual DOM tree to identify the minimal number of changes needed to update the actual DOM. This process of comparing the Virtual DOM trees and updating the actual DOM is called reconciliation.

The Virtual DOM in ReactJS is an abstraction that allows ReactJS to optimize the updating process, resulting in a faster and more efficient application. By minimizing the number of changes required to update the DOM, ReactJS reduces the amount of work the browser needs to do, which leads to better performance and a smoother user experience.

In summary, the Virtual DOM is a key concept in ReactJS that allows for efficient and optimized updating of the actual DOM, resulting in better performance and a smoother user experience.
</details>

<details>
  <summary><strong>State management is react</strong></summary>

  In ReactJS, functional components can also manage state using the useState hook. The useState hook is a built-in hook that allows us to add state to functional components without the need to convert them to class components.

  Here's an example of how to use the useState hook to manage state in a functional component:
  
  ```js 
  import React, { useState } from 'react';

const Counter = () => {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
};
```

In the example above, we use the useState hook to define the initial state of the count variable to be 0. The useState hook returns an array with two elements: the current state value and a function to update the state. We use array destructuring to assign these values to count and setCount respectively.

To update the state, we call the setCount function with the new value of count. When the state changes, ReactJS will automatically re-render the component and its children.

Functional components can also use state management libraries like Redux and MobX in a similar way as class components. The only difference is that we use the useSelector and useDispatch hooks to access the state and dispatch actions respectively.

Overall, state management in functional components is very similar to class components and can be achieved using the useState hook or state management libraries.
</details>

<details>
  <summary><strong>What is Prop drilling</strong></summary>

  Prop drilling is a term used in ReactJS to describe the process of passing props from a parent component down to a child component, and then down to another child component, and so on, until the prop reaches the component that needs it.

Prop drilling can occur when a parent component needs to pass data to a deeply nested child component. To do this, the parent component must pass the data down through each intermediate component in the hierarchy, even if those intermediate components do not need the data.

Here's an example of how prop drilling can occur:

```js 
const App = () => {
  const [data, setData] = useState([]);

  const fetchData = async () => {
    // fetch data and update state
  };

  return (
    <div>
      <Header />
      <Main data={data} />
      <Footer />
    </div>
  );
};

const Main = ({ data }) => {
  return (
    <div>
      <Sidebar />
      <Content data={data} />
    </div>
  );
};

const Content = ({ data }) => {
  return (
    <div>
      {data.map((item) => (
        <Item key={item.id} item={item} />
      ))}
    </div>
  );
};

const Item = ({ item }) => {
  return <div>{item.name}</div>;
};

```
In the example above, the App component fetches data and passes it down to the Main component via the data prop. The Main component then passes the data prop down to the Content component, which maps over the data to render Item components.

In this scenario, the data prop is being drilled down through the Main and Content components, even though they do not use the data prop themselves. This can be inefficient and make the code more difficult to maintain.

To avoid prop drilling, we can use ReactJS's Context API or state management libraries like Redux and MobX to pass data down the component hierarchy without the need to pass props through intermediate components. These methods provide a more efficient and scalable solution to managing and passing state in ReactJS applications.
</details>

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

- What is react fiber

- Explain inline element or block element

- Difference between normal export and default export

![Screenshot_1](https://user-images.githubusercontent.com/24729773/230261043-a5e3bc3b-3f5c-4351-bf95-df7aef6ef574.png)
<img src="![Screenshot_1](https://user-images.githubusercontent.com/24729773/230261043-a5e3bc3b-3f5c-4351-bf95-df7aef6ef574.png)" />
