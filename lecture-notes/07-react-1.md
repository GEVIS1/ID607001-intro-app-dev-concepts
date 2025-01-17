# 07: React 1

## Introduction

**React** is a **JavaScript** component-based library developed by **Facebook**.

Here are some reasons why people use **React**:

- Applications can handle complex updates such as fetching large amounts of data and still feel fast and responsive.
- You can write reusable and small pieces of code rather than large chunks of code. It solves the maintainability issue that you tend to have when writing **HTML**.
- Performs well in large applications, particularly when you need to fetch, change and render data.

### Where else will I use React in the BIT degree?

Yes. You will use **React** in **Advanced Application Development**. If you choose to do **Mobile** or **Web** in **Studio 5/6**, you will use **React** or **React Native**.

### Additional information

There are plenty of component-based libraries and frameworks out there. The most popular ones are **Angular**, **React**, and **Vue.js**.

### create-react-app

**create-react-app** is a way to create a **single-page React application (SPA)**.

**Resource:** <https://create-react-app.dev/docs/getting-started>

### What is a single page application?

It is a web application that loads only a single web document. It updates the content of the web document using **XMLHttpRequest** and **Fetch** when different content is to be shown.

**Resource:** <https://developer.mozilla.org/en-US/docs/Glossary/SPA>

### What are the benefits?

Users can use a web application without loading whole new pages from the server. It results in better performance and user experience.

### How to create a React application

Run the following commands:

```bash
npx create-react-app <Your OP username>-react
cd <Your OP username>-react
code .
```

### File structure

The following is your **React application's** file structure:

```bash
<Your OP username>-react
├── README.md
├── node_modules
├── package.json
├── .gitignore
├── public
│ ├── favicon.ico
│ ├── index.html
│ ├── logo192.png
│ ├── logo512.png
│ ├── manifest.json
│ └── robots.txt
└── src
│ ├── App.css
│ ├── App.js
│ ├── App.test.js
│ ├── index.css
│ ├── index.js
│ ├── logo.svg
│ ├── reportWebVitals.js
│ ├── setupTests.js
```

**Resource:** <https://create-react-app.dev/docs/folder-structure>

:question: **Interview Questions:**

1. Provide a brief description of what type of information `package.json` contains.
2. What is `public/index.html`?
3. What is `src/index.js`?

### Scripts

Go to `package.json`. In the `scripts`, there are four default `scripts`:

1. `npm start` - starts the development server. The default address is `localhost:3000`.
2. `npm test` - starts the test runner.
3. `npm run build` - bundles the application into static files for production. These can be found in the `build` directory.
4. `npm run eject` - removes the build tool, i.e., **Create React App**, copies build dependencies, configuration files, and scripts into your application as dependencies in `package.json`.

**Resource:** <https://create-react-app.dev/docs/available-scripts>

## JSX

Here is an example of **JSX**:

```javascript
const elementOne = <h1>Hello, World!</h1>;
```

It looks like **HTML**, but if you were to run the example in an **HTML** file, it would not work.

**Resource:** <https://reactjs.org/docs/introducing-jsx.html>

### Expressions

The following is an example of how you can embed an expression in **JSX**:

```javascript
const name = "John Doe";
const elementTwo = <h1>Hello, World! My name is {name}</h1>;
```

Here we have declared a `const` variable called `name`. It can be used in **JSX** by enclosing it in curly braces. You can also embed any valid **JavaScript** expression as long as it is enclosed in curly braces. For example:

```javascript
// Embedding an in-built JavaScript function
const elementThree = <h1>{Math.random()}</h1>;

const getRandomNumber = (max) => Math.floor(Math.random() * max);

// Embedding a user defined JavaScript function
const elementFour = <h1>{getRandomNumber(3)}</h1>;
```

### Attributes

The following is an example of how you can embed an expression in an attribute:

```javascript
const url = "https://bit.ly/3CqHp70";
const description = "This image contains a cat wearing a surgical mask";
const elementFive = (
  <img src={url} alt={description} width="500" height="350" />
);
```

### Nesting

The following is an example of how you can nest **JSX**:

```javascript
const elementSix = (
  <>
    <h1>Hello, World!</h1>
    <h2>My name is John Doe</h2>
  </>
);
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

```javascript
const App = () => {
  const elementOne = <h1>Hello, World!</h1>;

  const name = "John Doe";
  const elementTwo = <h1>Hello, World! My name is {name}</h1>;

  const elementThree = <h1>{Math.random()}</h1>;

  const getRandomNumber = (max) => Math.floor(Math.random() * max);
  const elementFour = <h1>{getRandomNumber(3)}</h1>;

  const url = "https://bit.ly/3CqHp70";
  const description = "This image contains a cat wearing a surgical mask";
  const elementFive = (
    <img src={url} alt={description} width="500" height="350" />
  );

  const elementSix = (
    <>
      <h1>Hello, World!</h1>
      <h2>My name is John Doe</h2>
    </>
  );

  return (
    <>
      {elementOne}
      {elementTwo}
      {elementThree}
      {elementFour}
      {elementFive}
      {elementSix}
    </>
  );
};

export default App;
```

You will learn the specifics of this code later.

Go to `src/index.js`. Have a quick look at the imports on lines 1-5. You only need to care about lines 1, 2, and 4.

On lines 7-12, you should see the following:

```javascript
ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById("root")
);
```

A **React** component called `App` (first argument) is being render in the **root node** (second argument) using `ReactDOM.render()`.

**Resources:**

- <https://reactjs.org/docs/rendering-elements.html>
- <https://reactjs.org/docs/react-dom.html>
- <https://reactjs.org/docs/strict-mode.html>

### Start the development server

To start the **development server**, open the terminal in **Visual Studio Code**, and run the following command:

```bash
npm start
```

It will run the `start` script as specified in `package.json`. It will open a new browser session and navigate you to `localhost:3000`. You should see the following:

<img src="https://github.com/otago-polytechnic-bit-courses/ID607001-intro-app-dev-concepts/blob/master/resources/img/07-react-1/07-react-1.png" />

### Other things to know about

- `ReactDOM.render()` gets the element, i.e., `<div>` in `public/index.html` by its id, i.e., `id="root"`.
- `ReactDOM.render()` only updates elements that have changed, i.e., it does not re-render the entire page, only the changed element(s). How it achieves this is by using the **virtual DOM**. More information here - <https://reactjs.org/docs/faq-internals.html>
- `React.StrictMode` is a tool that helps you find problems in your application. It only runs in development mode, meaning the production build is not impacted.

## Formative assessment

In this **in-class activity**, you will learn the basics of **React**.

### Submission

You must submit all program files via **GitHub Classroom**. Here is the URL to the repository you will use for this **in-class activity** – <https://classroom.github.com/a/_6KSahyX>. If you wish to have your code reviewed, message the course lecturer on **Microsoft Teams**. 

### Getting started

Open your repository in **Visual Studio Code** and solve the following four problems.

### Problem 1

In `App.js`, declare the following **JavaScript** object inside of the `App` function:

```js
const basketballTeam = {
  center: "Nikola Jokic",
  powerForward: "Anthony Davis",
  smallForward: "LeBron James",
  shootingGuard: "James Harden",
  pointGuard: "Stephen Curry",
};
```

Create an **arrow function** called `displayTeam()` that accepts an argument called `team` (**JavaScript** object). For each key/value pair in `team`, return a `<li>` containing the key, i.e., **center** and the value, i.e., **Nikola Jokic**. Render the `displayTeam()` function in an `<ul>` element.

**Expected output:**

<img src="https://github.com/otago-polytechnic-bit-courses/ID607001-intro-app-dev-concepts/blob/master/resources/img/07-react-1/07-react-2.png" width="450" height="350" />

### Problem 2

Refactor the `displayTeam()` function so that if `team` is not given, return **No team provided** in an `<h1>` element.

**Expected output:**

<img src="https://github.com/otago-polytechnic-bit-courses/ID607001-intro-app-dev-concepts/blob/master/resources/img/07-react-1/07-react-3.png" width="450" height="350" />

### Problem 3

Declare the following **JavaScript** array below `fruits` (**JavaScript** object):

```js
const fruits = [
  "strawberry",
  "banana",
  "apple",
  "blueberry",
  "orange",
  "grape",
];
```

Create an **arrow function** called `filterFruits()` that accepts an argument called `fruits` (**JavaScript** array). For each item in `fruits`, return a `<li>` containing the item if its length is ≤ 6. Render the `filterFruits()` function in an `<ul>` element under **problem 1** and **2**.

**Expected output:**

<img src="https://github.com/otago-polytechnic-bit-courses/ID607001-intro-app-dev-concepts/blob/master/resources/img/07-react-1/07-react-4.png" width="450" height="350" />

### Problem 4

Refactor the `filterFruits()` function so that if `fruits` is not given, return **No fruits provided** in an `<h1>` element.

**Expected output:**

<img src="https://github.com/otago-polytechnic-bit-courses/ID607001-intro-app-dev-concepts/blob/master/resources/img/07-react-1/07-react-5.png" width="450" height="350" />
