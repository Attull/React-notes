<h1 align="center">
  React Notes
</h1>

<!-- <p align="center">
   <a style="text-decoration:none">
    <img src="https://img.shields.io/badge/Still%20Evolving-grey" alt="version" />
  </a> 
</p> -->

## Introduction

* React is a Javascript library focused on building rich user interfaces.
* It is not a framework.
* It does not handle ```http``` and ```requests```, but has a rich ecosystem to get that work done.
* It has a component based architecture.
* React follows a [Declaritive paradigm](https://en.wikipedia.org/wiki/Declarative_programming) instead of the conventional [Imperative paradigm](https://en.wikipedia.org/wiki/Imperative_programming).

## Creating a React Project

* There are **two** ways to create a React project

    1. Using ```npx``` :✔️<br/> 
      - **Node Package Runner**, which gets installed while installing Node<br/>
      - It allows to directly run create-react-app without installing it<br/>
      - Use command: ```npx create-react-app project_name```
    
    2. Using ```npm```: <br/>
      - It requires to install the ```create-react-app```globally and then use it to generate projects<br>
      - Use command: ```npm install create-react-app -g```<br>
    and then ```create-react-app project_name```

## Folder Structure

Creating a react project comes with some files, which we need to understand. Following are the files which we need to know for every react project we create.

* ```package.json```: This files contains the dependencies and scripts required for the project.

* ```node_modules```: This folder contains all the installed dependencies. It is generated either when you run **create-react-app** command or when you run **npm install** command.

* ```public```: This folder has an entry point to our react app.

  * ```index.html```: This is the only ```.html ``` file in our application as react is a single page application. This is the entry point which is served on the client side and typically no code is added to this file. 

  * ```manifest.json```: It is related to the progressive web applications.

  * ```favicon.ico```: Title bar icon file.

* ```src```: This is the folder where the actual code is written and organized. 

  * ```index.js```: This is the very first file which is called by the entry file i.e ```index.html```.

  * ```App.js```: This is the root component of our react app. All the other components are enclosed within this component. It is responsible for all the html displayed on the browser. ```index.js``` imports this App component. 

  * ```App.css```: Global styling options are written in this file. Eg. App theme can be written in this file.

  * ```App.test.js```: This file is used to write unit test cases.

  * ```index.css```: It applies styling to the body tag.

  * ```logo.svg```: reference in the App component

## Virtual DOM

- React uses the [virtual DOM](http://tonyfreed.com/blog/what_is_virtual_dom) to clone a node that already exists in the DOM

- Subtrees are created in the virtual DOM and then rendered based on state changes

- When a state change occurs two things happen:

    - React runs a diff to check what changed

    - Then it updates the DOM based on the result of that diff (Referred to as [reconciliation](https://facebook.github.io/react/docs/reconciliation.html))

- The Virtual DOM is considered the magic behind React. It batches DOM operations to keep everything quick and snappy because DOM manipulation is SLOW 

- Once a state is changed it triggers the [diff algorithm](https://facebook.github.io/react/docs/reconciliation.html) to check all components, re-rendering only those that have changed properties. 

## JSX

- JSX is a JavaScript Extension Syntax used in React to easily write HTML and JavaScript together

- To convert JSX into browser understandable JavaScript code, we use a tool like [Babel](https://babeljs.io/) which is a JavaScript compiler/transpiler.

- Let's see the breakdown of the JSX converting process to React.createElement function:

- E.g 

**JSX Code:**
          <h1 className:"topBarHeading">welcome to FSD classes</h1>

**compiles to**
          React.createElement("h1",
                                {className:"topBarHeading", "I am Himanshu"
                              })

## Components

* The entire react app is made up of small individual modules called as Components. 
* The **App** component is the root component (```App.js```)
* It contains all the other component.
* **Naming Convention**: Components are always named in Pascal Case i.e the starting character is always in uppercase. 
* Components are resuable.
* That means, same components can be reused with different **props** (properties) and **state** (data) to display different information.
* Component can contain another component. 
* Eg: 
![image](https://user-images.githubusercontent.com/37962354/87883461-2980b180-c9cd-11ea-9626-e02dbaab2bdf.png)
* All these are individual components are enclosed in the **App** component which is the root component.
* A component code is placed inside a Javascript file.✔️
* However, we can also have seperate components files with ```.jsx``` extension. 
* There are two types of Components: 
  * Functional Components
  * Class Components


### Functional Component

- Similar to a function and returns `jsx` that gets rendered to the DOM

```js
//Searchbar.js
const Searchbar = () => {
    return <input />;
};

//index.js
const App = () => {
    return (
        <div>
            <Searchbar />
        </div>
    );
}
```
- In functional components the `props` object is passed as an argument E.g:

```js
const App = (props) => { }
```

### Class Component

- Used whenever a component needs to have some kind of internal record keeping

- It is self aware and keeps track of anything that happens to it once it has been rendered

- It is created using an [ES6 `class`](https://github.com/DrkSephy/es6-cheatsheet#classes)

```js
class Searchbar extends React.Component {
    render() {
        return <input />;
    }
}
```

- By extending `React.Component` you give the `Searchbar` class added functionality (state and props)

- To call an instance of a `class` you have to wrap it in jsx tags E.g: `<Searchbar />`

- Start off with a functional component and as your component gets complex you can convert to a class

- In a `class` component `props` are available within the component and don't need to be passed in as an argument. It can be accessed in a method using `this.props`

### Event Handling

- Similar to a regular event handler, in react it is a function that runs anytime an event occurs

- In react you declare the event handler then pass it to the element that you want to monitor for events

- It is considered best practice to begin the name of an event handler with `on` or `handle` E.g:

```js
class Searchbar extends React.Component {
    handleInputChange(e) {
        console.log(e.target.value);
    }
    render() {
        return <input onChange={this.handleInputChange()} />;
    }
}
```

### State

- `state` is a plain javascript object that is used to record and react to user events

- Each `class` based component has its own state object

- Whenever `state` is changed a component re-renders and also forces all of its children to re-render as well

- Before `state` can be used in a component the object needs to be initialized E.g:

```js
class Searchbar extends React.Component {
    constructor(props) {
        super(props);
        this.state = { term: ''};
    }
    handleInputChange(e) {
        console.log(e.target.value);
    }
    render() {
        return <input onChange={this.handleInputChange()}/>;
    }
}
```

- The `constructor` function is called whenever a new instance of a `class` is created

- It is reserved for setting up certain configurations in a `class` such as initializing variables, initializing state or binding event handler methods

- `super` is a reference to the `constructor` method on the React.Component `class` that is getting extended. This means that is has its own `constructor` function and so to reference it we have to use the `super` keyword

- In the code above `state` has been initialized E.g: `this.state = { property1: '' }`

- This syntax should only be used to declare state within the `constructor` function

- `this.setState()` should be used to manipulate state after it has been initialized E.g `this.setState({ property1: 'new state'});`

```js
class Searchbar extends React.Component {
    constructor(props) {
        super(props);
        this.state = { term: ''};
    }
    render() {
        return (
            <div>
                <input
                    value={this.state.term}
                    onChange={(e) => this.setState({term: e.target.value })} />
            </div>
        );
    }
}
```
- In the code above the value of the input has been set to the `state`

- This means that the component is declarative, the `state` determines how the data or UI is manipulated.

- When an action (or change) occurs the component is already aware through its change in `state` and then re-renders


### Component Lifecycle
      constructor (good place to do one-time setup)
        ⬇
      render (Avoid doing anything beside returning JSX)
      `content visible on screen`
        ⬇
      componentDidMount (good place to do data loading)
      `Sit and wait for updates...`
        ⬇
      componentDidUpdate (Good place to do more data-loading when state/props change)
      `Sit and wait until this component is not longer shown`
        ⬇
       componentWillUnmount (Good place to do cleanup, especially for non-React stuff)
    
#### Other lifecycle methods (rarely used)
- shouldComponentUpdate
- getDerivedStateFromProps
- getSnapshotBeforeUpdate

### Event Handlers: Handling events with React elements is very similar to handling events on DOM elements
- `onClick` User clicks on something : A div can  be clicked
- `onChange` User changes text in an input
- `onSubmit` User submits a form

### React Refs
- Gives access to a single DOM element
- We create refs in the constructor -> Assign them to instance variables -> then pass to a particular JSX element as props

### React Hooks
#### Hooks System
- `useState`: Function that lets you use **state** in a functional component
- `useEffect`: Function that lets you use something like **lifecycle methods** in a functional component
- `useRef`: Function that lets you create a **ref** in a funcitonal component

`Hooks are way to write resuable code, instead of more classic techniques like inheritance`

#### 7 Primitive Hooks (Not a Technical term)
- useState
- useEffect
- useContext
- useReducer
- useCallback
- useMemo
- useRef
- Custom hook


#### Class Components v/s Function Components

| -        | Class Components           |  Function Components |
| :------------- |:-------------:| :-----:|
| Initalization     |`state = { activeIndex: 0 }` | `useState(0)` |
| Refernce     | `this.state.activeIndex`      |   `activeIndex` |
|Updates | `this.setState({ activeIndex: 10 })`      |    `setActiveIndex(10)` |


--------------------------------------------------------

# Redux
- React is to render and present data to user not handling

## What is Redux?
- State Managment Library
- Makes creating complex applications easier
- Not required to create a React App!
- Not explicitly designed to work with React!

## Redux Cycle
    Action Creator
        ⬇
    Action
        ⬇
    Dispatch
        ⬇
    Reducers
        ⬇
    State
   
