# React Notes
This repository serves as a collection of useful notes that I have taken while learning React.

## Introduction to React
- Open source **Javscript *view* library**
- Created by Facebook
- Its main features are: **components**, **state** handling and **props**
- Uses its own markup language called **JSX**, a combination of HTML and JavaScript

## JSX
- Can be thought of as a syntax extension of JavaScript
- Allows HTML to be written directly within JavaScript
- Any code with { } will be treated as JavaScript
- JSX is technically not true JavaScript, so it must be compiled into JavaScript
    - **Babel** is a popular [transpiler](http://composition.al/blog/2017/07/30/what-do-people-mean-when-they-say-transpiler/) that does this
- A JSX element must return only a single parent element

## React Rendering
- React takes JSX and renders it to the DOM via an API called **ReactDOM**
- The API contains a function called *render* that takes two parameters: A JSX element, and a DOM node the render the component in

## JSX vs HTML
- HTML keywords are now reserved by JavaScript, and so must be in camelCase
- Any JSX element can be written as a self-closing tag, and must be closed

## Components
- Everything in React is a component
- Two ways to create one:
    1. **JavaScript function**: creates a **stateless** (can receive and alter data, but not track changes to it) *functional* component:
    ```javascript
    const ExampleComponent = function () {
        return (
            <div className="customClass" />
        );
    };
    ```
    2. **ES6 Class**: creates a class, extending from **React.Component**:
    ```javascript
    class Dog extends React.Component {
        constructor(props) {
            super(props);
        }

        render () {
            return (
                <h1>I am a dog</h2>
            );
        }
    }
    ```
- The point of extending the class from React.Component is to gain access to React's features: local state, lifecycle hooks
- The call to super() constructs the class using the React.Component constructor
- Composition is simply the rendering of multiple React components within a single parent component
- 