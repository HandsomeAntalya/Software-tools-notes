# 7.2 Hello world in React

In this exercise we will build a simple React app that greets the user, and so demonstrates managing state and passing it between components. 

这个练习是写一个可以给人打招呼的网站

**Create a react app** folder with `npx create-react-app FOLDERNAME`. Edit the port if necessary, as described on the previous page. *(our folder name = reactapp, and it is located in cs/tb2/tools)*

You can start the development server (`npm start`) and it will automatically reload when it detects that you have edited a source file. This feature can be quite convenient to develop with.

We will create an app with three components: 我们将创建一个有三个组件的应用程序

- The app component manages some state, namely a person's name.(应用程序组件管理一些状态，即一个人的名字。)
- The input component lets you enter and change your name.(输入组件让你输入和改变你的名字。)
- The output compoment displays "Hello, NAME".(输出组件显示 "你好，NAME"。)

**Difference between npm start and npm run** 

 **`npm start`**is a specific command used to start the main application or server, while **`npm run`**
 is a more general command used to execute custom scripts defined in the **`package.json`**
 file. **`npm run build`**is a command used to execute the **`build`**script defined in the **`scripts`**
 section of a project's **`package.json`**file.

## A basic app

First, strip out the sample code so your `App.js` file looks like this:

```jsx

import './App.css';
import React from 'react';

class App extends React.Component {
  render() {
    return (
      <p>App</p> //the message is shown on the page
    )
  }
}

export default App;

```

Save the file - if the `npm run` server is running in another window, it will reload - and check that you get a page with just the text `App`.

*And then we can see the change on this page:* 

![截屏2023-04-20 14.32.45.png](7%202%20Hello%20world%20in%20React%20c47e340862734b5ba5338f39e81718df/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_14.32.45.png)

## Add some state

In the app class, we can add some state such as a name field:

```jsx

import './App.css';
import React from 'react';

class App extends React.Component {
  state = {
    name: 'David'
  }

  render() {
    return (
      <p>Hello, {this.state.name}!</p>
    )
  }
}

export default App;

```

Check that this now displays `Hello, David!`.

![截屏2023-04-20 14.35.10.png](7%202%20Hello%20world%20in%20React%20c47e340862734b5ba5338f39e81718df/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_14.35.10.png)

## Pass state between Components

Let's make a separate component to display the name - add this class before the `export default` line:

```jsx

class NameGreeter extends React.Component {
  render() {
    if (this.props.name === "") {
      return (
        <p>Hello!</p>
      )
    } else {
      return (
        <p>Hello, {this.props.name}!</p>
      )
    }
  }
}

```

This component expects one property (the react version of a "parameter") called `name` and displays either a generic greeting or a greeting with a name.这个组件期望一个名为name的属性（反应版本的 "参数"），并显示一个普通的问候语或一个带有名字的问候语。

Change the render method for the App class to this:

```jsx

render() {
  return (
    <NameGreeter name={this.state.name} />
  )
}

```

This tells react that when it's time to render the App, it should create a `NameGreeter` component and pass it one prop called `name` which has the value of the name in the current state.这告诉 react，当它要渲染 App 的时候，它应该创建一个 NameGreeter 组件，并把一个叫做 name 的道具传给它，这个道具有当前状态下的名字值。

Note how we refer to `this.state.name` in the component that owns the state, but `this.props.name` in the child component. Generally, `this.state` is a component's own state and `this.props` is state (or other things) that a component gets from its parent. 注意我们如何在拥有状态的组件中提到`this.state.name`，但在子组件中提到`this.props.name`。一般来说，`this.state`是组件自己的状态，`this.props`是组件从其父级获得的状态（或其他东西）。

You could try making more than one name greeter, but a JSX block must always have a single root tag so this won't work:你可以尝试制作一个以上的名字招呼器，但一个JSX块必须始终有一个根标签，所以这是不可能的：

```jsx
// don't do this
return (
  <NameGreeter name={this.state.name} /><NameGreeter name={this.state.name} />
)

```

But this is fine:

```java

return (
  <div>
    <NameGreeter name={this.state.name} />
    <NameGreeter name={this.state.name} />
  </div>
)

```

when writing JSX code in a React application, a ***JSX block must always have a single root*** element (or "root tag") that wraps all other elements within that block. This is because JSX is transpiled into JavaScript, and a single expression is expected to be returned from a component or a JSX block.

If you try to return multiple elements without wrapping them in a single root element, you will get a syntax error.

Here's an example of **incorrect** JSX with multiple root elements:

```jsx
//Don't write in this way
function MyComponent() {
  return (
    <div>Element 1</div><div>Element 2</div>
  );
}
```

To fix this, you can wrap the elements in a single root element, such as a **`<div>`**:

```jsx

function MyComponent() {
  return (
    <div>
      <div>Element 1</div>
      <div>Element 2</div>
    </div>
  );

```

Starting from React 16.0, you can use React Fragments to return multiple elements without adding extra nodes to the DOM. Fragments can be used as a lightweight wrapper around your elements:

```jsx
function MyComponent() {
  return (
    <>
      <div>Element 1</div>
      <div>Element 2</div>
    </>
  );
}
```

In this example, the **`<>`** and **`</>`** are shorthand syntax for **`<React.Fragment>`** and **`</React.Fragment>`**, respectively. This allows you to return multiple elements without introducing additional DOM elements, keeping your DOM structure cleaner.

## Change State 更改状态

We are going to make a `NameEditor` component with an input field to change the name. However, the name *belongs* to the app component: this is the *state lifting* pattern in React, where if more than one component wants to 'share' some state, then you make a common parent component to hold the state. Any changing of the state has to happen on the parent component that 'owns' it, so we have to create functions to pass it around correctly.

我们要做一个带有输入字段的NameEditor组件来改变名字。然而，这个名字属于应用程序组件：这是React中的状态提升模式，如果一个以上的组件想要 "共享 "一些状态，那么你要制作一个共同的父组件来保存状态。状态的任何改变都必须发生在 "拥有 "它的父组件上，所以我们必须创建函数来正确传递它。

First, **create a new component** like this:

```jsx
class NameEditor extends React.Component {
  render() {
    return (
      <p>
        <label for="name">Name: </label>
        <input type="text" id="name" value={this.props.name} />
      </p>
    )
  }
}
```

And change the render method of the `App` component to create a name editor:

```jsx

return (
  <div>
    <NameEditor name={this.state.name} />
    <NameGreeter name={this.state.name} />
  </div>
)

```

When you run this, it will show you an input box with the current name, but if you try and change it then React will change it straight back again.

Input and output in React works with *data binding*: react maintains the correspondence between items on the screen (such as the input field) and its own state, but by default this only works in one way: React makes sure that the components on the screen reflect React's own state.

To make the edit box work, we have to first create a function on the `App` component that allows the state to be updated:

```jsx
class App extends React.Component {
  constructor() {
    super();
    this.onNameChange = this.onNameChange.bind(this);
  }

  onNameChange(newName) {
        this.setState({name: newName})
  }

  // state and render method here, same as before
}
```

The real work is happening in `this.setState`, we can't just do `this.state.name = newName` as that would not trigger React's updates. The `setState` function which is part of React, apart from setting the new state, also re-renders any component that needs to update itself.

The constructor is just boilerplate code to correctly re-bind the `this` variable for `onNameChange`, you have to do this for every method you write in a React class. You also need to call the `super()` constructor explicitly at the start of the constructor, as this calls the `React.Component` constructor to set the component up correctly.

We also have to let the name editor know which function to call to process changes. Change the JSX line that creates it to

```jsx
<NameEditor name={this.state.name} onNameChange={this.onNameChange} />
```

![截屏2023-04-20 14.56.12.png](7%202%20Hello%20world%20in%20React%20c47e340862734b5ba5338f39e81718df/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_14.56.12.png)

We did not put brackets after the function name, as we don't want to call the function when the component is created or rendered, we just want to tell it "here's a function that you can call later when you need it".

Next, in the `NameEditor` class, we create a method to handle updates:

```jsx

constructor(props) {
  super(props);
  this.onNameChange = this.onNameChange.bind(this);
}

onNameChange(e) {
  this.props.onNameChange(e.target.value);
}

```

If our component takes props, then we should pass them to the super constructor too.

The parameter `e` is an element of type event, which is triggered by the input component when the user changes its value. The event class has a property `target` which refers to the element on the page that triggered it, and if that was an input box like it is here then we can read its `value`. This is what we pass, via `props`, back to the `App` component.

Finally, change the line that creates the input box to

```jsx

<input type="text" id="name" value={this.props.name} onChange={this.onNameChange} />
```

The `onChange` attribute of an `<input>` is defined in the HTML standard and takes a JavaScript function that should be called whenever the input value changes.

With all this in place, you should be able to run the app and edit the text box, and watch the greeting change as you do this.

![截屏2023-04-20 14.59.29.png](7%202%20Hello%20world%20in%20React%20c47e340862734b5ba5338f39e81718df/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_14.59.29.png)

## Sequence of Events

Make sure you understand what happens when you type in the input box. You can observe this yourself if you set breakpoints in the F12 debug tools:

1. You type in the input box.
2. The browser reacts by calling the input box's `onChange` function with one parameter, an `Event`. This function is `NameEditor.onNameChange`.
3. Your `NameEditor.onNameChange` calls `App.onNameChange`.
4. `App.onNameChange` calls React's `setState`.
5. In response to this, React calls `render()` on the `App`.
6. This triggers further `render()` calls in both `NameGreeter` and `NameEditor`.

![截屏2023-04-20 15.01.29.png](7%202%20Hello%20world%20in%20React%20c47e340862734b5ba5338f39e81718df/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_15.01.29.png)

to run this: 

## Build the app

When you have finished developing an app, run `npm run build`. This will create your app in `build/`, compiling the JSX to JavaScript and HTML files. You can open `build/index.html` in a web browser without a server running.

*To run this, we need another server to run, therefore, we can try darkhttpd.* 

![截屏2023-04-20 15.19.51.png](7%202%20Hello%20world%20in%20React%20c47e340862734b5ba5338f39e81718df/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_15.19.51.png)

![截屏2023-04-20 15.22.23.png](7%202%20Hello%20world%20in%20React%20c47e340862734b5ba5338f39e81718df/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_15.22.23.png)

*The final website might look like this*

![截屏2023-04-20 15.20.52.png](7%202%20Hello%20world%20in%20React%20c47e340862734b5ba5338f39e81718df/%25E6%2588%25AA%25E5%25B1%258F2023-04-20_15.20.52.png)

## Read all about it

We have essentially, with a different example, done step 10 of the [official React tutorial](https://reactjs.org/docs/lifting-state-up.html). After the workshop, you may want to read this page again.