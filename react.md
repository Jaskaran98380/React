<div style="text-align:center;">
<h1>React.js</h1>
</div>

<div style="text-align: center;">
<img src="images.png" alt="alt text">
</div>

## Table of Contents
1. [Introduction to React](#introduction-to-react)
2. [Create a New React Project Using Vite](#create-a-new-react-project-using-vite)
3. [React Component Architecture](#react-component-architecture)
   - [Functional Components](#functional-components)
4. [JSX in React](#jsx-in-react)
5. [Props and State](#props-and-state)
   - [Props](#props)
   - [State](#state)
6. [Handling Events in React](#handling-events-in-react)

7. [Hooks in React](#hooks-in-react)
   - [useState](#usestate)
   - [useEffect](#useeffect)
8. [React Router](#react-router)
9. [Forms in React](#forms-in-react)
10. [Conditional Rendering](#conditional-rendering)
11. [Styling in React](#styling-in-react)
12. [Conclusion](#conclusion)
13. [References](#references)

---

## Introduction to React

React.js is a JavaScript library used for building user interfaces, primarily single-page applications. React allows developers to build complex UIs using reusable components that manage their own state. This component-based architecture, along with its virtual DOM implementation, makes React both efficient and easy to work with.


## Create a New React Project Using Vite
 - Open your terminal

 - Navigate to your projects folder
 ```bash
 cd path/to/your/projects/folder
```
- Create a new React project using Vite:
```bash
npm create vite@latest my-react-app -- --template react
```
- Replace my-react-app with your desired project name.
- The --template react part tells Vite to set up a React project.
------

- Navigate into the project directory:
```bash
cd my-react-app
```

-  Install Project Dependencies

```bash
npm install
```

- Open the Project in VS Code

- Start the Development Server
```bash
npm run dev
```





## React Component Architecture

React is built using components, which are the building blocks of any React application.

### Functional Components

Functional components are simple JavaScript functions that return React elements(JSX). They are stateless but they can handle local state and side effects using hooks.

```jsx
function Kna() {
    return <h1>Hello, {props.name}!</h1>;
}
```


### JSX in React
JSX stands for JavaScript XML and is a syntax extension of JavaScript that looks similar to Hyper Text Markup Language(HTML). It is used to describe what the UI should look like. JSX allows us to write HTML-like syntax directly in our JavaScript code, which React then transforms into lightweight JavaScript objects. 

```jsx
import React from 'react';

function Kna() {
    return (
        <div>
            <h1>Hello, world!</h1>
            <p>Welcome to my React app.</p>
        </div>
    );
}

export default Kna;

```
JSX makes the code more readable and easier to debug. It also allows embedding or adding JavaScript code within curly braces {} inside the JSX.

```jsx
const name = "John";
const element = <h1>Hello, {name}!</h1>;
```

### Props and State

#### Props

Props (short for "properties") are read-only inputs that are passed from a parent component to a child component. They are used to pass data and event handler functions to child components.

```jsx
//parent component

import React from 'react'
import Child from './components/Child'

const App = () => {
  return (
    <Child message="Message" />
  )
}

export default App
```

```jsx
//child component
import React from 'react'

const Child = ({message}) => {
  return (
    <div>Child {message}</div>
  )
}

export default Child
```
#### State
State is a local data storage that is private to a component and can be changed over time. Unlike props, state can be modified using the useState hook in functional components.

```jsx
import React, { useState } from 'react';

function App() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>
                Increment
            </button>
        </div>
    );
}

export default App
```

### Handling Events in React
React events are handled in a similar way to DOM events, but with some differences. In React, we attach an event handler (a function) to an element. This function runs when the event occurs.

Events are actions or occurrences that happen in the browser, such as clicks, key presses, or mouse movements. 

```jsx
function ActionButton() {
    function handleClick() {
        console.log('Button was clicked!');
    }

    return (
        <button onClick={handleClick}>
            Click me
        </button>
    );
}
```

### Hooks in React
Hooks are a way to use state and other React features in functional components. They allow us to manage local state, side effects, and more.

#### useState
The useState hook lets us add or manage state in functional components. It returns a stateful value and a function to update it.

```jsx
import React, { useState } from 'react';

function Counter() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>
                Increment
            </button>
        </div>
    );
}

export default Counter
```

#### useEffect
The useEffect hook lets us perform side effects in our components, such as fetching data or load fonts. The useEffect hook runs after the initial render of the component, but you can control when it runs by passing dependencies.

```jsx
import React, { useState, useEffect } from 'react';

function App() {
    const [count, setCount] = useState(0);

    useEffect(() => {
        console.log(`Count changed: ${count}`);

      
        return () => {
            console.log(`Cleanup before the next effect, count was: ${count}`);
        };
    }, [count]); 

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>Increment</button>
        </div>
    );
}

export default App;
```

### React Router
React Router is a popular library for handling routing in React applications. It allows us to define more than one route in our app and navigate between them without reloading the page.

```jsx
//App.jsx
import React from "react"
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import Home from "./components/Home";
import About from "./components/About";
import Contact from "./components/Contact";

const App = () =>{
    return (
        <Router>
            <Routes>
            <Route path="/home" element={<Home />} />
                <Route path="/about" element={<About />} />
                <Route path="/contact" element={<Contact />} />
            </Routes>
               
        </Router>
    );
}
export default App
```

```jsx
//Home.jsx
import React from 'react'

const Home = () => {
  return (
    <div>Home</div>
  )
}

export default Home
```

```jsx
//Contact.jsx
import React from 'react'

const Contact = () => {
  return (
    <div>Contact</div>
  )
}

export default Contact
```

```jsx
//About.jsx
import React from 'react'

const About = () => {
  return (
    <div>About</div>
  )
}

export default About
```


### Forms in React
Forms in React work similarly to HTML forms, but with some differences. We can control form input values by using useState().

```jsx
import React, { useState } from 'react';

function App() {
    const [value, setValue] = useState('');

    const handleChange = (event) => {
        setValue(event.target.value);
    };

    const handleSubmit = (event) => {
        console.log('A name was submitted: ' + value);
        event.preventDefault();
    };

    return (
        <form onSubmit={handleSubmit}>
            <label>
                Name:
                <input type="text" value={value} onChange={handleChange} />
            </label>
            <input type="submit" value="Submit" />
        </form>
    );
}

export default App
```


### Conditional Rendering

Conditional rendering in React works the same way as conditions in JavaScript. We can use if, else, and ternary operators to decide what to render based on a condition.

```jsx
function App(props) {
    const isLoggedIn = props.isLoggedIn;
    if (isLoggedIn) {
        return <h1>Welcome back!</h1>;
    } else {
        return <h1>Please sign up.</h1>;
    }
}
```

### Styling in React

We can style our React components using a variety of methods, including inline styles, CSS classes etc.

#### Inline Styles

We can apply inline styles directly in our JSX using the style attribute. Inline styles in React are specified as an object with camelCased properties.

```jsx
function App() {
    const style = {
        color: 'blue',
        backgroundColor: 'yellow',
        padding: '10px',
        height:'20px'
    };
    return <div style={style}></div>
}
```

#### CSS Classes

Another common way to style components is by using CSS classes. You can define styles in an external CSS file and apply them using the className attribute.

```jsx
import './App.css';

function App() {
    return <div className="styled-component">Styled Component</div>;
}
```

### Conclusion

React.js has become one of the most popular JavaScript libraries for building dynamic user interfaces due to its component-based architecture, efficient rendering through the virtual DOM, and ease of use with JSX. By mastering React's core concepts like components, state, props, and hooks, developers can build scalable and maintainable applications. 

### References

   - [React Official Documentation](https://legacy.reactjs.org/docs/getting-started.html)
   - [W3 Schools](https://www.w3schools.com/REACT/default.asp)


