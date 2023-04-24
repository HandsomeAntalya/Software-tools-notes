# 5.2 Static structure

### HTML

The main html file `app.html` is surprisingly unassuming: it contains almost nothing of substance! In fact, we can quote the complete file here:

```jsx
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>The City of Bristol</title>
    <link href="https://fonts.googleapis.com/css2?family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="style.css" />
    <script src="script.js"></script>
  </head>
  <body>
    <header><h1>The City of Bristol</h1></header>
    <nav id="nav">
      <div class="initial">Initialising...</div>
    </nav>
    <main id="dataPane">
      <div class="initial">Please select one of the wards on the left to view more data about it.</div>
    </main>
    <footer>created by G. A. Kavvos</footer>
  </body>
</html>
```

This is a very standard HTML file, which readily passes the [W3 validator](https://validator.w3.org/). It consists of a `<head>`and a `<body>`.

• The `<head>` sets the title, loads some nice fonts from the web, and declares that `style.css` is the stylesheet. Finally, the `<script>` tag tells the browser that there is JavaScript code to be run in the file `script.js`, which will be retrieved from the same location as the page that is being loaded.

<aside>
💡 Advanced note:

</aside>

If you look at introductory content on JavaScript on the internet, you will find many examples where JavaScript is included in a so-called *inline* style. [For example](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script#examples), you might see code of the form

```jsx
<script>alert("Hello World!");</script>
```

which embeds a fragment of JavaScript directly in the HTML file, instead of putting it in a separate `.js` file, and including it using an `src=` attribute like we did above.

**Do not do this. This is very bad style. Always keep HTML and JS in separate files.**

不要把JS的code 写到HTML里面,总是保持分开就行.

- The `<body>` describes a document with four sections:
    - There is a `<header>` with a big heading reading "The City of Bristol".
    - There is a `<nav>` [navigation section](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/nav), with a single `<div>` (i.e. a [generic block container](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/div)) with placeholder text saying "Initialising...".
    
    The **`<nav>`** HTML element represents a section of a page whose purpose is to provide navigation links, either within the current document or to other documents. Common examples of navigation sections are menus, tables of contents, and indexes.
    
    ![截屏2023-04-13 19.21.45.png](5%202%20Static%20structure%205ae57393b45c49c3b8f7faf2dca7f033/%25E6%2588%25AA%25E5%25B1%258F2023-04-13_19.21.45.png)
    
    **<div>: The content Division element**
    
    The **`<div>`** HTML element is the generic container for flow content. It has no effect on the content or layout until styled in some way using CSS (e.g. styling is directly applied to it, or some kind of layout model like Flexbox is applied to its parent element).
    
    ![截屏2023-04-13 19.43.44.png](5%202%20Static%20structure%205ae57393b45c49c3b8f7faf2dca7f033/%25E6%2588%25AA%25E5%25B1%258F2023-04-13_19.43.44.png)
    
    - Then then there is a `<main>` section, which contains a single `<div>` with some instructions for using the app.
    - Finally, there is a `<footer>` with the author's name in it.

The two `<div>`'s are instances of the `.initial` class. Both `<nav>` and `<main>` have unique id attributes, so they can be referred to uniquely.

<aside>
💡 It is generally agreed that [id attributes must be unique](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/id) in an HTML document. However, there is no enforcing mechanism for this: the browser will *not* check that we have not mistakenly re-used an id for some other tag. Again, this is in the interest in providing a smooth user experience without errors. Do not abuse this!

</aside>

As a "pure" container, the `<div>`element does not inherently represent anything. Instead, it's used to group content so it can be easily styled using the `[class](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes#class)`or `[id](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes#id)` attributes, marking a section of a document as being written in a different language (using the `[lang](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes#lang)`attribute), and so on.

This sparse document structure will be all that we need to present our single-page application.

## CSS

Go ahead and open up `app.html` in your browser of choice. You will see that the structure described by the tags above appear in very particular places.

Indeed, the location and appearance of the four sections (header, nav, main, footer) are set in the `style.css` file, which is explicitly loaded in `app.html`. The main things to note are the first few lines

```css

html {
  font-size: 12pt;
  font-family: 'Libre Baskerville', serif;
}

body {
  display: grid;
  grid-template-columns: 200px 1fr;
}

```

which tell the browser to

- use the Libre Baskerville font (loaded in the `<head>`) throughout the entire document, and
- lay out the `<body>` of the document using CSS grids.

We will not dwell on the grid structure here, but note that, as the `<nav>` comes first, it becomes the first `200px` column, and the `<main>` section becomes the `1fr` column.

The `style.css` file also sets many other details, such as margins, colours, etc.

```css
nav {
  text-align: center;
}

nav > button {
  padding-top: 1em;
  padding-bottom: 1em;
  margin: 1em 1em 1em 1em;
  box-shadow: 5px 5px;
}
main {
  margin: 1em 0em 0em 1em;
}
```

In JavaScript, the static structure refers to the arrangement and organization of code, including variables, functions, and classes. This structure helps maintain a clean and readable codebase, making it easier to understand and modify the code.

Here are some essential aspects of the static structure in JavaScript:

1. Variables: Variables are used to store values in JavaScript. You can use **`var`**, **`let`**, or **`const`** to declare a variable. Variables declared with **`var`** are function-scoped, while **`let`** and **`const`** are block-scoped. The main difference between **`let`** and **`const`** is that **`const`** is used for values that should not be reassigned, while **`let`** is used for values that may change.
2. Data types: JavaScript has a few basic data types, such as strings, numbers, booleans, null, and undefined. Objects and arrays are also important data structures in JavaScript.
3. Functions: Functions are reusable blocks of code that can be called with specific inputs (arguments) and return a value. Functions can be declared using a function declaration, function expression, or an arrow function.
    
    Function declaration:
    
    ```jsx
    
    function add(a, b) {
      return a + b;
    }
    ```
    
    Function expression:
    
    ```jsx
    const add = function(a, b) {
      return a + b;
    };
    ```
    
    Arrow function:
    
    ```jsx
    
    const add = (a, b) => a + b;
    ```
    
4. Objects: Objects in JavaScript are key-value pairs, where the keys are strings, and the values can be any JavaScript data type. Objects are used to store and organize related data and can also contain methods (functions associated with the object).
    
    Example of an object:
    
    ```jsx
    
    const person = {
      firstName: 'John',
      lastName: 'Doe',
      age: 30,
      greet: function() {
        console.log(`Hello, my name is ${this.firstName} ${this.lastName}`);
      }
    };
    ```
    
5. Classes: JavaScript supports object-oriented programming with classes, which were introduced in ECMAScript 2015 (ES6). Classes are a blueprint for creating objects and can include properties and methods. Inheritance is also supported through the **`extends`** keyword.
    
    Example of a class:
    
    ```jsx
    javascriptCopy code
    class Person {
      constructor(firstName, lastName, age) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.age = age;
      }
    
      greet() {
        console.log(`Hello, my name is ${this.firstName} ${this.lastName}`);
      }
    }
    
    const john = new Person('John', 'Doe', 30);
    john.greet();
    
    ```