# React(slides)

![截屏2023-04-23 00.11.09.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.11.09.png)

![截屏2023-04-23 00.11.40.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.11.40.png)

React is a popular JavaScript library for building user interfaces, particularly web applications with complex and interactive UIs. Developed by Facebook, React's main goal is to make it easier for developers to build fast, scalable, and maintainable applications. React 是一种流行的 JavaScript 库，用于构建用户界面，特别适用于具有复杂和交互式 UI 的 Web 应用程序。由 Facebook 开发，React 的主要目标是使开发人员更容易构建快速、可扩展和可维护的应用程序。

React's core features include:

1. **Components 组件** : React promotes the use of reusable components, which are self-contained pieces of code responsible for rendering and managing a part of the user interface. Components can be easily combined and nested, allowing developers to create complex UIs by composing smaller, simpler components. React提倡使用可重用的组件，它们是独立的代码片断，负责渲染和管理用户界面的一部分。组件可以很容易地组合和嵌套，使开发者可以通过组合更小、更简单的组件来创建复杂的UI。
2. **Declarative UI**: In React, developers describe the desired UI state using a declarative syntax. React takes care of updating the actual UI to match the desired state. This simplifies the code and makes it easier to reason about the application's behavior. 在React中，开发者使用声明式语法描述所需的UI状态。React负责更新实际的用户界面以匹配所需的状态。这简化了代码，使其更容易推理应用程序的行为。
3. **Virtual DOM:** React uses a virtual representation of the DOM (Document Object Model) called the Virtual DOM. When the application state changes, React calculates the difference between the current Virtual DOM and the new one using a process called "reconciliation." Then, it updates only the parts of the real DOM that have changed, rather than updating the entire DOM. This optimization significantly improves the application's performance. React使用DOM（文档对象模型）的一个虚拟表示，称为虚拟DOM。当应用程序的状态发生变化时，React使用一个称为 "调和 "的过程来计算当前虚拟DOM和新DOM之间的差异。然后，它只更新真实DOM中已经变化的部分，而不是更新整个DOM。这种优化大大改善了应用程序的性能。
4. **Unidirectional data flow**: React enforces a unidirectional data flow, which means that data is passed down from parent components to child components through properties called "props." This approach makes it easier to track and manage the state of the application, as data always flows in a single direction. React强制执行单向数据流，这意味着数据通过被称为 "props "的属性从父组件向下传递到子组件。这种方法使得跟踪和管理应用程序的状态更加容易，因为数据总是在一个方向上流动。
5. **Integration with other libraries and frameworks:** React can be easily integrated with other libraries and frameworks such as Redux (for state management) or React Router (for client-side routing). This flexibility allows developers to choose the right tools for their specific use cases and requirements. React可以很容易地与其他库和框架集成，如Redux（用于状态管理）或React Router（用于客户端路由）。这种灵活性使开发人员能够为他们的特定用例和要求选择合适的工具。

React is widely used in both small and large-scale web applications, and its component-based architecture and performance optimizations have influenced the development of other UI libraries and frameworks. React Native, a separate project built on top of React, also allows developers to build native mobile applications for iOS and Android using the same principles and concepts as React.

React被广泛用于小型和大型网络应用，其基于组件的架构和性能优化影响了其他UI库和框架的发展。React Native是建立在React之上的一个独立项目，它也允许开发者使用与React相同的原则和概念为iOS和Android建立本地移动应用。

![截屏2023-04-23 00.11.50.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.11.50.png)

![截屏2023-04-23 00.12.01.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.12.01.png)

![截屏2023-04-23 00.12.42.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.12.42.png)

![截屏2023-04-23 00.13.00.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.13.00.png)

**npx create-react-app hello world (注意这里是npx, 不是npm)**

cd hello-world

npm start (start your server)

![截屏2023-04-23 00.13.55.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.13.55.png)

![截屏2023-04-23 00.14.19.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.14.19.png)

![截屏2023-04-23 00.14.41.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.14.41.png)

React root DOM node 

In React, the root DOM node is the entry point where the React application is attached to the actual HTML DOM. The root DOM node is a container that holds the entire React application and is typically a single HTML element (like a **`div`**) with a unique identifier (like an **`id`**). This root node is then used as the mounting point for the React component hierarchy. 在React中，根DOM节点是连接React应用程序和实际HTML DOM的入口点。根DOM节点是一个容器，包含整个React应用程序，通常是具有唯一标识符（如**`id`**）的单个HTML元素（如**`div`**）。然后，此根节点用作React组件层次结构的安装点。

To render a React component inside the root DOM node, you use the **`ReactDOM.render()`** method. This method takes two arguments: the first is the React element (component) you want to render, and the second is the root DOM node in which the React element should be rendered.在根DOM节点中呈现React组件，您可以使用**`ReactDOM.render()`**方法。此方法需要两个参数：第一个是您要呈现的React元素（组件），第二个是应在其中呈现React元素的根DOM节点。

Here's a simple example:

HTML file:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>React App</title>
</head>
<body>
  <div id="root"></div>
  <script src="index.js"></script>
</body>
</html>
```

JavaScript file (index.js):

```jsx
import React from 'react';
import ReactDOM from 'react-dom';

function App() {
  return (
    <div>
      <h1>Hello, React!</h1>
    </div>
  );
}

const rootDOM = document.getElementById('root');
ReactDOM.render(<App />, rootDOM);
```

In this example, the HTML file contains a **`div`** element with an **`id`** of "root," which serves as the root DOM node. The JavaScript file imports React and ReactDOM, defines a simple **`App`** component, and then renders the **`App`** component inside the root DOM node using **`ReactDOM.render()`**.

When the application is loaded in the browser, React takes control of the root DOM node and updates its content as needed based on the component hierarchy and state changes. The rest of the HTML file remains static and is not managed by React.

![截屏2023-04-23 00.15.30.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.15.30.png)

![截屏2023-04-23 00.16.38.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.16.38.png)

![截屏2023-04-23 00.16.50.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.16.50.png)

![截屏2023-04-23 00.17.03.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.17.03.png)

![截屏2023-04-23 00.17.20.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.17.20.png)

# React Part II

![截屏2023-04-23 00.22.14.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.22.14.png)

## Class based components

![截屏2023-04-23 00.23.48.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.23.48.png)

Class-based components are a way to create React components using ES6 classes. They provide an alternative to the functional components, which are functions that return JSX. Class-based components were the primary way of creating components with state and lifecycle methods before React introduced hooks.

**React component names must begin with an uppercase letter.**

Here's a simple example of a class-based component:

```jsx
import React, { Component } from 'react';

class MyComponent extends Component {
  render() {
    return (
      <div>
        <h1>Hello, React!</h1>
        <p>This is a class-based component.</p>
      </div>
    );
  }
}

export default MyComponent;
```

In this example, we define a class **`MyComponent`** that extends **`React.Component`**. Inside the class, we define a **`render()`** method, which returns the JSX for the component. The **`render()`** method is mandatory for every class-based component.

**What tool does React use to compile JSX: Babel**

Class-based components can also have state and lifecycle methods. Here's an example of a class-based component with state:

```jsx
import React, { Component } from 'react';

class Counter extends Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
  }

  increment = () => {
    this.setState({ count: this.state.count + 1 });
  };

  render() {
    return (
      <div>
        <h1>Count: {this.state.count}</h1>
        <button onClick={this.increment}>Increment</button>
      </div>
    );
  }
}

export default Counter;
```

In this example, we have a **`Counter`** component that maintains a state object with a single property **`count`**. We define a **`constructor()`** method to initialize the state and an **`increment()`** method to update the state. The **`render()`** method displays the current count and a button to increment it.

With the introduction of hooks in React 16.8, functional components can now manage state and lifecycle methods, making them a popular choice for most use cases. However, class-based components are still used in some older projects, and understanding them can be helpful when working with legacy code or when certain libraries require them.

![截屏2023-04-23 00.26.42.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.26.42.png)

![截屏2023-04-23 00.24.24.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.24.24.png)

![截屏2023-04-23 00.24.36.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.24.36.png)

You cannot change value if you pass value. 

When you pass a primitive value (like a number, string, or boolean) to a function, you are passing it by value. This means that a copy of the value is created, and the function works with this copy. Changing the value inside the function will not affect the original value outside the function. Here's an example:

```jsx
function changeValue(x) {
  x = 10;
}

let num = 5;
changeValue(num);
console.log(num); // Output: 5 (the original value remains unchanged)
```

However, when you pass an object (including arrays and functions) to a function, you are passing it by reference. This means that the function receives a reference to the original object, not a copy of the object. Modifying the object's properties inside the function will affect the original object outside the function:

```jsx
function changeProperty(obj) {
  obj.name = 'John';
}

let person = { name: 'Jane' };
changeProperty(person);
console.log(person.name); // Output: 'John' (the original object's property has been modified)
```

If you want to prevent the modification of an object's properties within a function, you can create a copy of the object before passing it to the function. One way to create a shallow copy of an object is by using the spread operator (**`...`**):

```jsx
let personCopy = { ...person };
changeProperty(personCopy);
console.log(person.name); // Output: 'Jane' (the original object remains unchanged)
```

Note that this technique only creates a shallow copy of the object, meaning that nested objects will still be referenced. To create a deep copy of an object, you can use libraries like Lodash or other techniques, such as **`JSON.parse(JSON.stringify(obj))`**.

In summary, when you pass a value to a function, whether it can be changed or not depends on whether it's a primitive value (passed by value) or an object (passed by reference).

![截屏2023-04-23 00.24.47.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.24.47.png)

**useState is hook**

In React, hooks are functions that allow you to use state and lifecycle features in functional components. They were introduced in React 16.8 and have become popular because they enable you to write cleaner and more concise code compared to class-based components. Hooks also make it easier to reuse stateful logic across different components without having to rely on higher-order components or render props.

There are several built-in hooks in React, and some of the most commonly used ones are:

1. **`useState`**: This hook allows you to add state to functional components. It returns an array containing the current state value and a function to update that state.

```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <h1>Count: {count}</h1>
      <button onClick={increment}>Increment</button>
    </div>
  );
}
```

1. **`useEffect`**: This hook lets you perform side effects, such as fetching data, subscriptions, or manually changing the DOM, in functional components. It is a combination of the **`componentDidMount`**, **`componentDidUpdate`**, and **`componentWillUnmount`** lifecycle methods in class-based components.

```jsx
import React, { useState, useEffect } from 'react';

function DataFetcher() {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then((response) => response.json())
      .then((data) => setData(data));
  }, []);

  return (
    <div>
      <h1>Data</h1>
      <ul>
        {data.map((item) => (
          <li key={item.id}>{item.name}</li>
        ))}
      </ul>
    </div>
  );
}
```

1. **`useContext`**: This hook allows you to use the React context API to access and modify the context values in functional components.

```jsx
import React, { useContext } from 'react';
import { ThemeContext } from './ThemeContext';

function ThemedButton() {
  const theme = useContext(ThemeContext);

  return (
    <button style={{ backgroundColor: theme.background, color: theme.foreground }}>
      Click me
    </button>
  );
}
```

These are just a few examples of the built-in hooks in React. There are several other hooks available, such as **`useReducer`**, **`useCallback`**, **`useMemo`**, and **`useRef`**. Additionally, you can create your own custom hooks to encapsulate and reuse stateful logic across multiple components.

**What is a common use case for ref? To directly access a DOM node**

A common use case for **`ref`** in React is to access and interact with a DOM element directly, especially when you need to perform an action that cannot be done through React's declarative approach. Some examples of when you might need to use **`ref`** include:

1. Managing focus, selection, or text input: When you need to programmatically set focus on an input element or manipulate the text selection, you can use a **`ref`** to get direct access to the DOM element.

```jsx
class TextInput extends React.Component {
  constructor(props) {
    super(props);
    this.textInput = React.createRef();
  }

  focusInput() {
    this.textInput.current.focus();
  }

  render() {
    return (
      <div>
        <input type="text" ref={this.textInput} />
        <button onClick={() => this.focusInput()}>Focus the input</button>
      </div>
    );
  }
}
```

1. Triggering animations: If you want to trigger an animation using a third-party library that requires direct manipulation of the DOM, you can use a **`ref`** to access the DOM element and apply the necessary changes.
2. Integrating with external libraries: When integrating with an external library that requires direct access to the DOM (e.g., jQuery plugins or D3.js visualizations), you can use a **`ref`** to pass the DOM element to the library.

Remember that using **`ref`** should be done sparingly, as it bypasses React's declarative nature and makes your code harder to understand and maintain. Always consider if there's a more "React-like" way to accomplish your goal before using **`ref`**.

Hooks have made it easier to write and maintain React code, and they are now the recommended way to manage state and side effects in functional components. (Hooks can not be conditional)

React Hooks are a way to use state and lifecycle features in functional components. They were introduced in React 16.8. There are certain rules you need to follow when using hooks:

1. Only call Hooks at the top level: Don't call hooks inside loops, conditions, or nested functions. This ensures that hooks are called in the same order each time a component renders. (Hooks can only be called at the top level of a component)
2. Only call Hooks from React functions: You should only call hooks from React functional components or custom hooks. Don't call hooks from regular JavaScript functions. (Hooks can only be called inside React Function components)

Following these rules will help ensure that your hooks work as expected, and the React team has created a plugin called **`eslint-plugin-react-hooks`** which enforces these rules automatically.

In addition to these rules, there are some best practices for using hooks:

1. Keep hooks small and focused: Each hook should have a specific purpose, making it easier to understand, test, and reuse.
2. Use custom hooks for complex logic: If you find yourself writing complex logic inside a component that uses hooks, consider creating a custom hook to encapsulate that logic.
3. Always test your hooks: Write tests for your custom hooks to ensure they work correctly and handle edge cases.

By following these rules and best practices, you'll ensure that your hooks work correctly and your code is maintainable and easy to understand.

**Not** a rule for the React: Hooks can be called in Class or Function components

**Although React Hooks generally replace class components, there are no plans to remove classes from React.**

**Why should you avoid copying the values of props into a component's state?**

Because that would create two instances of the same state that could become out of sync

![截屏2023-04-23 00.25.00.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.25.00.png)

![截屏2023-04-23 00.25.11.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.25.11.png)

# React Part III

![截屏2023-04-23 00.31.27.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.31.27.png)

The output looks like:

![截屏2023-04-23 00.34.00.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.34.00.png)

![截屏2023-04-23 00.34.29.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.34.29.png)

![截屏2023-04-23 00.35.11.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.35.11.png)

![截屏2023-04-23 00.36.14.png](React(slides)%20b52c8fc038ec46dba775b55135c855c3/%25E6%2588%25AA%25E5%25B1%258F2023-04-23_00.36.14.png)