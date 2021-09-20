# **React**

## What is React

**React** is a **JavaScript** component-based library developed by **Facebook**. 

Here are some reasons why people use **React**:
- Applications can handle complex updates such as fetching large amounts of data and still feel fast and responsive.
- You can write reusable and small pieces of code rather than large chunks of code. It solves the maintainability issue that you tend to have when writing vanilla **HTML**.
- Performs well in large applications, particularly when you need to fetch, change and display data.

### Where else will I use React in the BIT degree?

Yes. You will use **React** in **Advanced Application Development**. If you choose to do **Mobile** or **Web** in **Studio 5/6**, you will use **React** or **React Native**.

### Additional information

There are plenty of component-based libraries and frameworks out there. The most popular ones are **Angular**, **React**, and **Vue.js**.

## Create React App

**Create React App** is a way to create a **SPA (single-page React application)**.

### What is a SPA?

It is a web application that loads only a single web document. It updates the content of the web document using **XMLHttpRequest** and **Fetch** when different content is to be shown.

### What are the benefits?

Users can use a web application without loading whole new pages from the server. It results in better performance and user experience.

### How to create a React web application

Run the following commands:

```md
npx create-react-app graysono-react-playground
cd graysono-react-playground
code .
```

**Note:** replace `graysono` with your **Otago Polytechnic** username.

### File structure

The following is your **React web application's** file structure: 

```md
graysono-react-playground
├── README.md
├── node_modules
├── package.json
├── .gitignore
├── public
│   ├── favicon.ico
│   ├── index.html
│   ├── logo192.png
│   ├── logo512.png
│   ├── manifest.json
│   └── robots.txt
└── src
    ├── App.css
    ├── App.js
    ├── App.test.js
    ├── index.css
    ├── index.js
    ├── logo.svg
    ├── serviceWorker.js
    └── setupTests.js
```

#### Activity

Please answer the following:

1. Provide a brief description of what type of information `package.json` contains.
2. What is `public/index.html`?
3. What is `src/index.js`?
4. Which directory does **Webpack** process?

Once you have finished, add, commit and push your answers to your **GitHub** in-class activities repository.

### Scripts

Go to `package.json`. In the `scripts`, there are four default `scripts`:

1. `npm start` - starts the development server. The default address is `localhost:3000`.
2. `npm test` - starts the test runner.
3. `npm run build` - bundles the application into static files for production. These can be found in the `build` directory.
4. `npm run eject` - removes the build tool, i.e., **Create React App**, copies build dependencies, configuration files, and scripts into your application as dependencies in `package.json`.

### Resources
- https://create-react-app.dev/docs/getting-started
- https://developer.mozilla.org/en-US/docs/Glossary/SPA
- https://developer.mozilla.org/en-US/docs/Glossary/AJAX
- https://create-react-app.dev/docs/getting-started
- https://create-react-app.dev/docs/folder-structure
- https://create-react-app.dev/docs/available-scripts

## JSX

Here is an example of **JSX**:

```js
const element = <h1>Hello, World!</h1> // Note: you can ommit the semi-colon
```

It looks like **HTML**, but if you were to run the example in an **HTML** file, it would not work.

### Expressions

The following is an example on how you can embed an expression in **JSX**:

```js
const name = 'John Doe'
const element = <h1>Hello, World! My name is {name}</h1>
```

Here we have declared a `const` variable called `name`. It can be used in **JSX** by enclosing it in curly braces. You can also embed any valid **JavaScript** expression as long as it is enclosed in curly braces. For example:

```js
// Embedding an in-built JavaScript function 
const element = <h1>{Math.random()}</h1>

// Embedding a user defined JavaScript function
const getRandomNumber = (max) => {
  return Math.floor(Math.random() * max)
}

const element = <h1>{getRandomNumber(3)}</h1>
```

### Attributes

The following is an example on how you can embed an expression in an attribute:

```js
const url = 'https://bit.ly/3CqHp70'
const description = 'This image contains a cat wearing a surgical mask'
const element = <img src={url} alt={description} />
```

### Nesting

The following is an example on how you can nest **JSX**:

```js
const element = (
  <div>
    <h1>Hello, World!</h1>
    <h2>My name is John Doe</h2>
  </div>
)
```

If you are nesting **JSX**, enclose the **JSX** in parentheses.

### Rendering

**React** elements, i.e., all the code examples above, are relatively cheap to create compared to **DOM (Document Object Model)** elements.

Go to `public/index.html`. On line 31, you should see the following:

```html
<div id="root"></div>
```

This **DOM** element is the **root node**, meaning everything inside this element will be managed by **React DOM**. Usually, a **React** application only has one **root node**.

Go to `src/App.js`. Replace all the code in this file with the following:

```js
import React from 'react'

const App = () => {
  return (
    <div>
      <h1>Hello, World!</h1>
    </div>
  )
}

export default App
```

You will learn the specifics of this code later. 

Go to `src/index.js`. Have a quick look at the imports on lines 1-5. You only need to care about lines 1, 2, and 4.

On lines 7-12, you should see the following:

```js
ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
)
```

A **React** component called `App` (first argument) is being render in the **root node** (second argument) using `ReactDOM.render()`. **Note:** `App` returns:

```js
<div>
  <h1>Hello, World!</h1>
</div>
```

### Start the development server

To start the **development server**, open the terminal in **Visual Studio Code**, and run the following command:

```md
npm start
```

It will run the `start` script as specified in `package.json`. It will open a new browser session and navigate you to `localhost:3000`. You should see the following:

<img src="https://raw.githubusercontent.com/otago-polytechnic-bit-courses/IN607-intro-app-dev-concepts/master/resources/img/08-react/08-react-1.png" width="350" />

### Other things to know about

- `ReactDOM.render()` gets the element, i.e., `<div>` in `public/index.html` by its id, i.e., `id="root"`.
- `ReactDOM.render()` only updates elements that have changed, i.e., it does not re-render the entire page, only the changed element(s). How it achieves this is by using the **virtual DOM**. More information here - https://reactjs.org/docs/faq-internals.html
- `React.StrictMode` is a tool that helps you find problems in your application. It only runs in development mode, meaning the production build is not impacted.

#### Activity

**Task 1:**

In `App.js`, declare the following **JavaScript** object inside of the `App` function:

```js
const team = {
  center: 'Joel Embiid',
  powerForward: 'Anthony Davis',
  smallForward: 'LeBron James',
  shootingGuard: 'James Harden',
  pointGuard: 'Stephen Curry'
}
```

Create a function called `displayTeam()` that accepts an argument called `team` (**JavaScript** object). Iterate through the **JavaScript** object. For each key/pair in the the **JavaScript** object, return a `<li>` containing the key, i.e., **center** and the value, i.e., **Joel Embiid**. Under `<h1>Hello, World!</h1>` in the `return` block, call the `displayTeam()` in an `<ul>` element.

**Expected output:**

<img src="https://raw.githubusercontent.com/otago-polytechnic-bit-courses/IN607-intro-app-dev-concepts/master/resources/img/08-react/08-react-2.png" width="350" />

**Task 2:**

Refactor the `displayTeam()` function so if a `team` is not given as an argument, return **No team provided** in an `<h1>` element.

**Expected output:**

<img src="https://raw.githubusercontent.com/otago-polytechnic-bit-courses/IN607-intro-app-dev-concepts/master/resources/img/08-react/08-react-3.png" width="350" />

**Task 3:**

Declare the following **JavaScript** array under the **JavaScript** object:

```js
const fruits = [
  'strawberry', 
  'banana', 
  'apple', 
  'blueberry', 
  'orange', 
  'grape'
]
```

Create a function called `filterFruits()` that accepts an argument called `fruits` (**JavaScript** array). Iterate through the **JavaScript** array. For each item in the the **JavaScript** array, return a `<li>` containing the item if its length is greater than 5. Under **Task 1/2** in the `return` block, call the `filterFruits()` in an `<ul>` element.

**Expected output:**

<img src="https://raw.githubusercontent.com/otago-polytechnic-bit-courses/IN607-intro-app-dev-concepts/master/resources/img/08-react/08-react-4.png" width="350" />

**Task 4:**

Refactor the `filterFruits()` function so if a `fruits` is not given as an argument, return **No fruits provided** in an `<h1>` element.

**Expected output:**

<img src="https://raw.githubusercontent.com/otago-polytechnic-bit-courses/IN607-intro-app-dev-concepts/master/resources/img/08-react/08-react-5.png" width="350" />

Once you have finished, add, commit and push your code to your **GitHub** in-class activities repository.

### Resources
- https://reactjs.org/docs/introducing-jsx.html
- https://reactjs.org/docs/rendering-elements.html
- https://reactjs.org/docs/react-dom.html
- https://reactjs.org/docs/strict-mode.html

## Components

**Components** allow you to split your **UI** into independent, reusable chunks of **JSX**.

### Class vs. Function components

In **React**, there are two ways to declare a **component**.

**Class component** example:

```js
class App extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello, World!</h1>
      </div>
    )
  }
}

export default App
```

**Function component** example:

```js
const App = () => {
  return (
    <div>
      <h1>Hello, World!</h1>
    </div>
  )
}

export default App
```

From **React's** point of view, the two ways are equivalent. In this module, you will use **function components**.

### Create a new component

In `src` a new directory called `components`, then create a new **JavaScript** file called `Welcome`. In this file, add the following:

```js
import React from 'react'

const Welcome = () => {
  return (
    <div>
      <h1>Welcome</h1>
    </div>
  )
}

export default Welcome
```

The following is how you import and use a **component**:

```js
import React from 'react'
import Welcome from './components/Welcome' // Importing the Welcome function component

const App = () => {
  ...
  
  return (
    <div>
      <h1>Hello, World!</h1>
      ...
      <Welcome />
    </div>
  )
}

...
```

When you nest **components** within **components**, you create a **component tree**. Currently, the **component tree** looks like this:

```md
App (parent) <- Welcome (child)
```

## Component lifecycle methods

Each **function component** has several **lifecycle methods** that are run at particular times during the rendering and commit process. 

If you are unsure what the **component lifecycle methods** are, please carefully read this resource - https://datacadamia.com/web/javascript/react/function/lifecycle?s[]=%2Aclass. 

### Props

When you declare a **class** or **function** component, you must never modify its props (properties) or act like **pure functions**. It is a strict rule that all **components** must adhere to. 

If you are unsure of what a **pure function** is, please carefully read this resource - https://www.freecodecamp.org/news/what-is-a-pure-function-in-javascript-acb887375dfe/ 

```js
...

const Welcome = (props) => {
  return (
    <div>
      <h1>Welcome {props.firstName}</h1> {/* Pass a prop called firstName */}
    </div>
  )
}

...
```

This is an example of how you can reuse a **component**:

```js
const App = () => {
  ...
  
  return (
    <div>
      <h1>Hello, World!</h1>
      ...
      <Welcome /> {/* This will render - Welcome in a h1. Note: a prop attribute is not given */}
      <Welcome firstName="John" /> {/* 
                                     This will render - Welcome John in a h1. Note: a prop 
                                     attribute is given. Make sure the prop attribute's name is the
                                     same as what is specified in parent component, i.e., Welcome.js. 
                                   */}
    </div>
  )
}

...
```

## Hooks

**Hooks** allow you to use **state** and other features without having to use **class components**. **Hooks** "hook into" **state** and the **component lifecycle** using **function components**. **Note:** you can not use **Hooks** with **class components**. 

### State Hook

Please read the following resource - https://reactjs.org/docs/hooks-state.html.

Here is an example of how you can use the `useEffect` hook:

```js
import React, { useState } from 'react' // Import the useState hook from the react dependency

const Counter = () => {
  const [count, setCount] = useState(0) // Local state variable called count. 
  
  // const [count, ...] - first argument allows you to get the state variable's value
  // const [..., setCount - second argument allows you to set the state variables's value
  // useState(0) - using the useState hook which sets an initial state value, i.e., 0
  
  // count can not be accessed outside this function component
  
  return (
    <div>
      <p>You clicked {count} times</p> {/* Display the count state variable in a <p> element */}
      <button onClick={() => setCount(count + 1)}> {/* Increment the count state variable by one */}
        Click me
      </button>
    </div>
}
```

You can declare as many state variables as you wish:

```js
const ExampleWithManyStates = () => {
  const [age, setAge] = useState(25)
  const [fruit, setFruit] = useState('apple')
  const [todos, setTodos] = useState([{ text: 'Learn new stuff' }])
}
```

#### Axios

The following few examples will be using **Axios**. Many of you have probably used a **promise** based HTTP client before, i.e., **Fetch**. You can think of **Axios** as **Fetch** on steroids. For more information, please carefully read this resource - https://axios-http.com/docs/intro.

To install **Axios**, open the terminal in **Visual Studio Code**, and run the following command:

```md
npm i axios
```

You can check the `dependencies` block in `package.json` to make sure you have installed **Axios**.

### Effect Hook

Please read the following resource - https://reactjs.org/docs/hooks-effect.html. 

Here is an example of how you can use the `useEffect` hook:

```js
import axios from 'axios'
import React, { useState, useEffect } from 'react' // Import the useEffect hook from the react dependency

const Post = () => {
  const [post, setPost] = useState([]) // State variables

  useEffect(() => {
    axios.get('https://jsonplaceholder.typicode.com/posts/1') // Making a request
    .then((response) => {
      setPost(response.data) // Set post to the response data
    })
  }, []) // The empty array means render once. If we pass in post, i.e., [post], 
         // it will re-render the component if post's data changes

  return (
    <div>
      {/* Displaying the post's title and body */}
      <h1>{post.title}</h1>
      <p>{post.body}</p>
    </div>
  )
}

export default Post
```

#### Activity

**Task 1:**

Please answer the following:

1. What is happening when you call `useEffect`?
2. Write a code example of how you can destructure **props** in a **function component**.

**Task 2:**



**Expected output:**


**Task 3:**



**Expected output:**


**Task 4:**



**Expected output:**


**Task 5:**



**Expected output:**

### Resources
- https://reactjs.org/docs/components-and-props.html
- https://reactjs.org/docs/react-component.html
- https://reactjs.org/docs/hooks-overview.html

<!-- 
## Styles

## Reactstrap

## Forms

### Headers

## Deployment -->