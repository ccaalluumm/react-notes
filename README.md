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
- Any code within { } will be treated as JavaScript
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

## Props (AKA Properties)
- Can be passed to child components as a unique HTML attribute, e.g. 
```javascript
<Animals animals={animals}>
```
- The child component can then access the props argument, e.g.
```javascript
const Animals = (props) => {
    return (
        <p>{props.animals.join(', ')}</p>
    )
};
```
- React allows components to assign **default props**, which will be assigned if the value of that prop is undefined, e.g. MyComponent.defaultProps = {}
- Props be assigned types to provide typechecking: MyComponent.propTypes = { handleClick: PropTypes.func.isRequired }
- PropTypes is imported independently from react with `import PropTypes from 'prop-types';
- If the component is an ES6 class, then props must be first accessed by refering to the class itself with the **this** keyword

## State
- React has three different types of components
    1. Stateless functional component: a function that returns JSX
    2. Stateless component: an ES6 class that does not track state
    3. Stateful component: an ES6 class that *does* track/maintain state
- State is data that needs to tracked by your application, and can change over time
- A stateful component can be made by declaring a state in the constructor:
```javascript
class Dog extends React.Component {
    constructor(props) {
        super(props);
        // Initialise state
        this.state = {
            name
        }
    }
}
```
- A component's state provides encapsulation, meaning only the class itself can access that state
- The **setState()** function takes in key-value pairs, which updates the components state, with the keys referring to state values
- The setState function call is asynchronous, so whenver defining class methods that alter state, always do so by passing a fresh call of state, i.e.
```javascript
// Bind the method to this class
this.increment = this.increment.bind(this);
increment() = {
    this.setState(state => {
        return {counter: state.counter + 1};
    })
}
```
- Components can be **controlled** meaning that they are rendered (controlled) by React rather than the browser

## Paradigms
- Undirectional data flow: state flows in one direction down the tree of the application
- Separation of state logic and UI
- The idea is to have one main component (commonly named App) that manages state, and then a bunch of UI components which are stateless, but can receive bits of application state via props

## Lifecycle Methods/Hooks
- A hook captured a component at a certain point in its lifecycle, e.g. when it updates, renders, etc.
- 