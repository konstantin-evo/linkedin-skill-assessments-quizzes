## React.js

#### Q1. If you want to import just the Component from the React library, what syntax do you use?

- [ ] `import React.Component from 'react'`
- [ ] `import [ Component ] from 'react'`
- [ ] `import Component from 'react'`
- [x] `import { Component } from 'react'`

#### Explanation

For importing a Component you can use `require()` and `module.exports`, but more recommended way is to use `import`
and `export` instead.

Example:

```javascript
import React, {Component} from 'react';

class Button extends Component {
    render() {
// ...
    }
}

export default Button; // Don’t forget to use export default
```

#### Q2. If a function component should always render the same way given the same props, what is a simple performance optimization available for it?

- [x] Wrap it in the `React.memo` higher-order component.
- [ ] Implement the `useReducer` Hook.
- [ ] Implement the `useMemo` Hook.
- [ ] Implement the `shouldComponentUpdate` lifecycle method.

#### Explanation

`React.memo` is a higher order component.

If your component renders the same result given the same props, you can wrap it in a call to `React.memo` for a
performance boost in some cases by memoizing the result.

This means that React will skip rendering the component, and reuse the last rendered result.

Example:

```javascript
const MyComponent = React.memo(function MyComponent(props) {
    /* render using props */
});
```

#### Q3. How do you fix the syntax error that results from running this code?

```
const person = (firstName, lastName) =>
{
  first: firstName,
  last: lastName
}
console.log(person("Jill", "Wilson"))
```

- [x] Wrap the object in parentheses.
- [ ] Call the function from another file.
- [ ] Add a return statement before the first curly brace.
- [ ] Replace the object with an array.

#### Explanation

JavaScript variables are containers for data values.

Value should be written within double or single quotes:

This code assigns a simple value (Fiat) to a variable named car:

```javascript
let car = "Fiat";
```

Objects are variables too. But objects can contain many values.

This code assigns many values (Fiat, 500, white) to a variable named car:

```javascript
const car = {type: "Fiat", model: "500", color: "white"};
```

#### Q4. If you see the following import in a file, what is being used for state management in the component?

`import React, {useState} from 'react';`

- [x] React Hooks
- [ ] stateful components
- [ ] math
- [ ] class components

#### Explanation

Hooks are backwards-compatible and let you use state and other React features without writing a class.

This example below renders a counter. When you click the button, it increments the value::

```javascript
import React, {useState} from 'react';

function Example() {
// Declare a new state variable, which we'll call "count"
    const [count, setCount] = useState(0);

    return (
        <div>
            <p>You clicked {count} times</p>
            <button onClick={() => setCount(count + 1)}>
                Click me
            </button>
        </div>
    );
}
```

Here, `useState` is a Hook. We call it inside a function component to add some local state to it. React will preserve
this state between re-renders.

`useState` returns a pair:

1. the current state value
2. a function that lets you update it.

You can call this function from an event handler or somewhere else. It’s similar to `this.setState` in a class, except
it doesn't merge the old and new state together.

The only argument to `useState` is the initial state. In the example above, it is `0` because our counter starts from
zero.

**Note**: unlike `this.state`, the state here doesn't have to be an object — although it can be if you want. The initial
state argument is only used during the first render.

#### Q5. Using object literal enhancement, you can put values back into an object. When you log person to the console, what is the output?

```javascript
const name = 'Rachel';
const age = 31;
const person = {name, age};
console.log(person);
```

- [ ] `{{name: "Rachel", age: 31}}`
- [x] `{name: "Rachel", age: 31}`
- [ ] `{person: "Rachel", person: 31}}`
- [ ] `{person: {name: "Rachel", age: 31}}`

#### Explanation

An object can have variables as properties or can have computed properties, as shown below:

```javascript
var firstName = "James";
var lastName = "Bond";

var person = {firstName, lastName}
```

Result:

```json
{
  firstName: "James",
  lastName: "Bond"
}
```

#### Q6. What is the testing library most often associated with React?

- [ ] Mocha
- [ ] Chai
- [ ] Sinon
- [x] Jest

#### Explanation

Jest is a JavaScript testing framework that allows developers to run tests on JavaScript and TypeScript code and can be
easily integrated with React JS.

#### Q7. To get the first item from the array ("cooking") using array destructuring, how do you adjust this line?

```javascript
const topics = ['cooking', 'art', 'history'];
```

- [ ] `const first = ["cooking", "art", "history"]`
- [ ] `const [] = ["cooking", "art", "history"]`
- [ ] `const [, first]["cooking", "art", "history"]`
- [x] `const [first] = ["cooking", "art", "history"]`

#### Explanation

To illustrate destructuring, we'll make a sandwich. Do you take everything out of the refrigerator to make your
sandwich? No, you only take out the items you would like to use on your sandwich.

Destructuring is exactly the same. We may have an array or object that we are working with, but we only need some
items contained in these.

Destructuring makes it easy to extract only what is needed.

Before (old way):

```javascript
const vehicles = ['mustang', 'f-150', 'expedition'];

const car = vehicles[0];
const truck = vehicles[1];
const suv = vehicles[2];
```

With destructuring:

```javascript
const vehicles = ['mustang', 'f-150', 'expedition'];

const [car, truck, suv] = vehicles;
```

We can even destructure deeply nested objects by referencing the nested object then using a colon and curly braces to
again destructure the items needed from the nested object:

```javascript
const vehicleOne = {
    brand: 'Ford',
    model: 'Mustang',
    type: 'car',
    year: 2021,
    color: 'red',
    registration: {
        city: 'Houston',
        state: 'Texas',
        country: 'USA'
    }
}

myVehicle(vehicleOne)

function myVehicle({model, registration: {state}}) {
    const message = 'My ' + model + ' is registered in ' + state + '.';
}
```

#### Q8. How do you handle passing through the component tree without having to pass props down manually at every level?

- [ ] React Send
- [ ] React Pinpoint
- [ ] React Router
- [x] React Context

#### Explanation

Context provides a way to pass data through the component tree without having to pass props down manually at every
level.

In a typical React application, data is passed top-down (parent to child) via `props`, but such usage can be cumbersome
for certain types of `props` (e.g. locale preference, UI theme) that are required by many components within an
application.

Context provides a way to share values like these between components without having to explicitly pass a prop through
every level of the tree.

Context is designed to share data that can be considered “global” for a tree of React components, such as the current
authenticated user, theme, or preferred language. For example, in the code below we manually thread through a “theme”
prop in order to style the Button component:

```javascript

class App extends React.Component {
    render() {
        return <Toolbar theme="dark"/>;
    }
}

function Toolbar(props) {
// The Toolbar component must take an extra "theme" prop
// and pass it to the ThemedButton. This can become painful
// if every single button in the app needs to know the theme
// because it would have to be passed through all components.
    return (
        <div>
            <ThemedButton theme={props.theme}/>
        </div>
    );
}

class ThemedButton extends React.Component {
    render() {
        return <Button theme={this.props.theme}/>;
    }
}
```

Using context, we can avoid passing props through intermediate elements:

```javascript
// Context lets us pass a value deep into the component tree
// without explicitly threading it through every component.
// Create a context for the current theme (with "light" as the default).
const ThemeContext = React.createContext('light');

class App extends React.Component {
    render() {
// Use a Provider to pass the current theme to the tree below.
// Any component can read it, no matter how deep it is.
// In this example, we're passing "dark" as the current value.
        return (
            <ThemeContext.Provider value="dark">
                <Toolbar/>
            </ThemeContext.Provider>
        );
    }
}

// A component in the middle doesn't have to
// pass the theme down explicitly anymore.
function Toolbar() {
    return (
        <div>
            <ThemedButton/>
        </div>
    );
}

class ThemedButton extends React.Component {
// Assign a contextType to read the current theme context.
// React will find the closest theme Provider above and use its value.
// In this example, the current theme is "dark".
    static contextType = ThemeContext;

    render() {
        return <Button theme={this.context}/>;
    }
}
```

#### Q9. What should the console read when the following code is run?

```javascript
const [, , animal] = ['Horse', 'Mouse', 'Cat'];
console.log(animal);
```

- [ ] Horse
- [x] Cat
- [ ] Mouse
- [ ] undefined

#### Q10. What is the name of the tool used to take JSX and turn it into createElement calls?

- [ ] JSX Editor
- [ ] ReactDOM
- [ ] Browser Buddy
- [x] Babel

#### Explanation

Babel’s use is not only rooted in React. Its main application is as a compiler to convert code written in
ECMAScript2015+ into backwards-compatible JavaScript.

While most popular browsers can support ECMAScript2015 ( or ES6), it’s always good practice to ensure that your code is
compatible with older versions of JavaScript. ES6 saw the introduction of `let`, `const`, Arrow Functions, Classes,
multi-line strings, and a host of other goodies.

Example:

```javascript
// Babel Input: ES2015 arrow function

const profile = (
    <div>
        <img src="avatar.png" className="profile"/>
        <h3>{[user.firstName, user.lastName].join(" ")}</h3>
    </div>
);

// Babel Output: ES5 equivalent
const profile = React.createElement(
    "div",
    null,
    React.createElement("img", {src: "avatar.png", className: "profile"}),
    React.createElement("h3", null, [user.firstName, user.lastName].join(" "))
);
```

#### Q11. Why might you use useReducer over useState in a React component?

- [ ] when you want to replace Redux
- [x] when you need to manage more complex state in an app
- [ ] when you want to improve performance
- [ ] when you want to break your production app

#### Explanation

`useReducer` is an alternative to `useState`. Accepts a reducer of type `(state, action) => newState`, and returns the current state paired with a
dispatch method.

Syntax:

```javascript
const [state, dispatch] = useReducer(reducer, initialArg, init);
```

`useReducer` is usually preferable to `useState` when you have complex state logic that involves multiple sub-values or when the next state depends on
the previous one.

`useReducer` also lets you optimize performance for components that trigger deep updates because you can pass dispatch down instead of callbacks.

Here’s the counter example using `useState`:

```javascript
function Counter({initialCount}) {
    const [count, setCount] = useState(initialCount);
    return (
        <>
            Count: {count}
            <button onClick={() => setCount(initialCount)}>Reset</button>
            <button onClick={() => setCount(prevCount => prevCount - 1)}>-</button>
            <button onClick={() => setCount(prevCount => prevCount + 1)}>+</button>
        </>
    );
}
```

Here’s the counter example from the useState section, rewritten to use a reducer:

```javascript
const initialState = {count: 0};

function reducer(state, action) {
    switch (action.type) {
        case 'increment':
            return {count: state.count + 1};
        case 'decrement':
            return {count: state.count - 1};
        default:
            throw new Error();
    }
}

function Counter() {
    const [state, dispatch] = useReducer(reducer, initialState);
    return (
        <>
            Count: {state.count}
            <button onClick={() => dispatch({type: 'decrement'})}>-</button>
            <button onClick={() => dispatch({type: 'increment'})}>+</button>
        </>
    );
}
```

#### Q12. Which props from the props object is available to the component with the following syntax?

```javascript
<Message {...props} />
```

- [ ] any that have not changed
- [x] all of them
- [ ] child props
- [ ] any that have changed

#### Explanation

The spread `(...)` syntax allows an iterable, such as an array or string, to be expanded in places where zero or more arguments (for function calls)
or elements (for array literals) are expected.

In an object literal, the spread syntax enumerates the properties of an object and adds the key-value pairs to the object being created.

#### Q13. Consider the following code from React Router. What do you call `:id` in the path prop?

```javascript
<Route path="/:id"/>
```

- [ ] This is a route modal
- [x] This is a route parameter
- [ ] This is a route splitter
- [ ] This is a route link

#### Explanation

React Router is a standard library for routing in React. It enables the navigation among views of various components in a React Application, allows
changing the browser URL, and keeps the UI in sync with the URL.

Example:

```javascript
import ReactDOM from "react-dom/client";
import {BrowserRouter, Routes, Route} from "react-router-dom";
import Layout from "./pages/Layout";
import Home from "./pages/Home";
import Blogs from "./pages/Blogs";
import Contact from "./pages/Contact";
import NoPage from "./pages/NoPage";

export default function App() {
    return (
        <BrowserRouter>
            <Routes>
                <Route path="/" element={<Layout/>}>
                    <Route index element={<Home/>}/>
                    <Route path="blogs" element={<Blogs/>}/>
                    <Route path="contact" element={<Contact/>}/>
                    <Route path="*" element={<NoPage/>}/>
                </Route>
            </Routes>
        </BrowserRouter>
    );
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App/>);
````

Route component will now help us to establish the link between component’s UI and the URL. To include routes to the application, add the code give
below to your app.js.

```javascript
<Route exact path='/' element={< Home/>}></Route>
<Route exact path='/about' element={< About/>}></Route>
<Route exact path='/contact' element={< Contact/>}></Route>
```

Let us now try to understand the props associated with the Route component.

1. exact: It is used to match the exact value with the URL. For e.g., `exact path=’/about’` will only render the component if it exactly matches the
   path but if we remove exact from the syntax, then UI will still be rendered even if the structure is like /about/10.
2. **path: Path specifies a pathname we assign to our component**.
3. element: It refers to the component which will render on matching the path.

#### Q14. If you created a component called Dish and rendered it to the DOM, what type of element would be rendered?

```javascript
function Dish() {
    return <h1>Mac and Cheese</h1>;
}

ReactDOM.render(<Dish/>, document.getElementById('root'));
```

- [ ] `div`
- [ ] section
- [ ] component
- [x] `h1`

#### Explanation

Class components uses render function. The `ReactDOM.render()` function takes two arguments

1. HTML code;
2. HTML element.

Purpose of `render()`:

1. React renders HTML to the web page by using a function called `render()`.
2. The purpose of the function is to display the specified HTML code inside the specified HTML element.
3. In the `render()` method, we can read props and state and return our JSX code to the root component of our app.
4. In the `render()` method, we can't change the state, and we can't cause side effects (such as making an HTTP request to the webserver).

Example:

```javascript
import React, {Component} from 'react';

export default class App extends Component {
    state = {
        PawriDays: [
            {id: '123s', Day: 'Monday'},
            {id: '234r', Day: 'Saturday'},
            {id: '12d5', Day: 'Sunday'}
        ]
    }

    render() {
        const PartyDays = this.state.PawriDays.length
        const style = {
            'textAlign': 'center',
            'color': 'green'
        }

        // Return JSX code
        return (
            <div style={style}>
                <h1>I am User</h1>
                <p>We party: {PartyDays} days a week</p>
            </div>
        );
    }
}
```

#### Q15. What does this React element look like given the following function?

#### Alternative: Given the following code, what does this React element look like?

```javascript
React.createElement('h1', null, "What's happening?");
```

- [ ] `<h1 props={null}>What's happening?</h1>`
- [x] `<h1>What's happening?</h1>`
- [ ] `<h1 id="component">What's happening?</h1>`
- [ ] `<h1 id="element">What's happening?</h1>`

#### Explanation

The `createElement()` method creates and returns a new React element of the given type. The type argument can be either a tag name string (such
as `'div'` or `'span'`), a React component type (a class or a function), or a React fragment type.

Syntax:

```javascript
React.createElement(
    type,
    [props],
    [...children]
)
```

Code written with JSX will be converted to use React.createElement(). You will not typically invoke React.createElement() directly if you are using
JSX. See React Without JSX to learn more.

Example:

```javascript
const myElement = React.createElement('h1', {}, 'I do not use JSX!');
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(myElement);
```

## Coursera Quiz - Building Interactive User Interfaces Using React Library - Build Stateful Components using React

#### Q1. How will the following JSX code be compiled to React code? <h1 title=”main”>Main article</h1>

- [ ] React.createElement(h1,{title:’main’},’Main article’);
- [x] React.createElement(‘h1’,{title:’main’},’Main article’);
- [ ] React.createElement(‘h1’,{title:’main’},{children:’Main article’});
- [ ] React.createElement(‘h1’,null,{title:”main”,”Main article”});

#### Explanation

React uses a special syntax that resembles HTML to declare components. This markup, called JSX, is embedded in the
component JavaScript and needs to be compiled to JavaScript before it's usable by the browser.

The online compiler for next generation JavaScript:
[babeljs.io/repl](https://babeljs.io/repl/)

```javascript
React.createElement(
    type,
    [props],
    [...children]
)
```

Example:

```javascript
class Hello extends React.Component {
    render() {
        return React.createElement('div', null, `Hello ${this.props.toWhat}`);
    }
}
```

Code written with JSX will be converted to use `React.createElement()`. You will not typically
invoke `React.createElement()` directly if you are using JSX.

**Note**: The answer to the question is related to the syntax of the `React.createElement()` operation.

#### Q2. What is the equivalent of the following React code snippet in JSX? `React.createElement('div',{styles:"color:red"},'data="content"');`

- [x] `<div styles="color:red">data="content"</div>`
- [ ] `<div style="color:red">data="content"</div>`
- [ ] The function call is invalid
- [ ] `<div>data="content"</div>`

#### Q3. Which of the following statements is true regarding the setState() function?

1. [ ] setState() is asynchronous inside event handlers
2. [ ] In react, we can pass an object or function as argument in setState() method.
3. [ ] If both Parent and Child call setState() during a click event, child is re-rendered twice to get the desired output.
4. [ ] Both Option1 and Option2
5. [x] Option1 , Option2 and Option3

#### Explanation

All the React components can have a state associated with them.

The state of a component can change either:

1. due to a response to an action performed by the user;
2. due to a response an event triggered by the system.

Whenever the state changes, React re-renders the component to the browser. Before updating the value of the state, we
need to build an initial state setup. Once we are done with it, we use the `setState()` method to change the state
object. It ensures that the component has been updated and calls for re-rendering of the component.

Example:

```javascript
import React, {Component} from 'react'

class App extends Component {
    constructor(props) {
        super(props)

        this.state = { // Set initial state
            greeting: 'Click the button to receive greetings'
        }

        // Binding this keyword
        this.updateState = this.updateState.bind(this)
    }

    updateState() { // Changing state
        this.setState({
            greeting: 'Konstantin.evo welcomes you !!'
        })
    }

    render() {
        return (
            <div>
                <h2>Greetings Portal</h2>
                <p>{this.state.greeting}</p>

                {/* Set click handler */}
                <button onClick={this.updateState}>
                    Click me!
                </button>
            </div>
        )
    }
}

export default App;
```

**setState() is asynchronous call**

That means if synchronous call get called it may not get updated at right time like to know
current value of object after update using `setState()` it may not get give current updated value on console.

To get some behavior of synchronous need to pass function instead of object to `setState()`.

**Function in `setState`**

Passing in a function into `setState()` instead of an object will give you a reliable value for your component's state
and props.

Example:

```javascript
submit()
{
    this.setState(function (prevState, props) {
        return {showForm: !prevState.showForm}
    });
}
```

#### Q4. Which of the following is not a valid setState() call signature?

1. [ ] this.setState({})
2. [ ] this.setState( )
3. [x] this.setState({},()=>{})
4. [ ] this.setState(()=>{})

#### Explanation

**Syntax**: We can use `setState()` to change the state of the component directly as well as through an arrow function.

```javascript
setState({stateName: updatedStateValue})
// OR
setState((prevState) => ({
    stateName: prevState.stateName + 1
}))
```

#### Q5. How will you access the employee state object when it is initially declared as following?

```
Super();
this.state = {
    Employee: {
        name:”James”,
        age:43,
        designation:”Manger”
    }
};
}
```

- [x] A

```javascript
render()
{
    const {employee} = this.state;
    Return(
        <div>
            <h2>Employee Name:</h2>
            {employee.name}
        </div>)
}
```

- [ ] B

```javascript
render()
{
    const employee = this.state;
    Return(
        <div>
            <h2>Employee Name:</h2>
            employee.name
        </div>)
}
```

- [ ] C

```javascript
render()
{
    const {employee} = this.state.employee;
    Return(
        <div>
            <h2>Employee Name:</h2>
            {employee.name}
        </div>)
}
```

- [ ] Not all the above

#### Explanation

The `state` and `props` in React are always in an object format. This means that the value could be accessed from the state and props via key-value
pair.

To access the normal state object, you can use the `key` name from the object. The state object will look as shown below.

```javascript
constructor()
{
    super();
    this.state = {
        employee: {
            firstname: "FirstName123",
            lasttname: "LastName123",
            age: "31",
            city: "xyzcity",
            department: "marketing",
            joiningyear: "2015"
        }
    };
}
```

There are several key-value pairs under the employee object, so if you want to get access to the actual employee state object, it can be accessed as
demonstrated below.

```javascript
render()
{
    const {employee} = this.state;

    return (
        <div>
            Access Normal Object
            <hr/>
            <table>
                <tr>
                    <td>First Name :</td>
                    <td>{employee.firstname}</td>
                </tr>
                <tr>
                    <td>Last Name :</td>
                    <td>{employee.lasttname}</td>
                </tr>
                <tr>
                    <td>Department :</td>
                    <td>{employee.department}</td>
                </tr>
            </table>
        </div>
    );
}
```

#### Q6. What is wrong with the following JSX code snippet and how will you fix it?

```
render()
{
    return (<div>Hello!</div><div>World!</div>);
}
```

1. [x] The code is absolutely fine
2. [ ] Gives compilation error stating “JSX expressions must have one parent element”
3. [ ] To avoid the error, change the code to:

```
render()
{
    return (<div>Hello World!</div>);
}
```

1. [ ] Gives runtime error stating “JSX expressions must have one parent element”
2. [ ] Both Option2 and Option3
3. [ ] Both Option3 and Option 4

#### Explanation

Class components uses render function. The `ReactDOM.render()` function takes two arguments

1. HTML code;
2. HTML element.

Purpose of `render()`:

1. React renders HTML to the web page by using a function called `render()`.
2. The purpose of the function is to display the specified HTML code inside the specified HTML element.
3. In the `render()` method, we can read props and state and return our JSX code to the root component of our app.
4. In the `render()` method, we cannot change the state, and we cannot cause side effects(such as making an HTTP request to the webserver).

Example:

```javascript
import React, {Component} from 'react';

export default class App extends Component {
    state = {
        PawriDays: [
            {id: '123s', Day: 'Monday'},
            {id: '234r', Day: 'Saturday'},
            {id: '12d5', Day: 'Sunday'}
        ]
    }

    render() {
        const PartyDays = this.state.PawriDays.length
        const style = {
            'textAlign': 'center',
            'color': 'green'
        }

        // Return JSX code
        return (
            <div style={style}>
                <h1>I am User</h1>
                <p>We party: {PartyDays} days a week</p>
            </div>
        );
    }
}
```

#### Q7. How will you add comments in JSX code?

[ ]

```javascript
return (
    <div>
        <h1>Hello World</h1>
        <!-- <p>My name is Bob</p> -->
        <p>Nice to meet you!</p>
    </div>
);
```

[ ]

```javascript
return (
    <div>
        <h1>Hello World</h1>
        //
        <p>My name is Bob</p>
        <p>Nice to meet you!</p>
    </div>
);
```

[x]

```javascript
return (
    <div>
        <h1>Hello World</h1>
        {/* <p>My name is Bob</p> */}
        <p>Nice to meet you!</p>
    </div>
);
```

[ ]

```javascript
return (
    <div>
        <h1>Hello World</h1>
        {//<p>My name is Bob</p>}
            <p>Nice to meet you!</p>
            </div>
            );
```

#### Explanation

JSX (JavaScript XML) is an extended form of JavaScript language syntax that provides a way to write HTML and JavaScript together. React developers are
very familiar with JSX.

Like other languages, JSX provides us with the ability to write comments.

Syntax:

```javascript
{/* This is a single line comment */
}

{/* This is
a multiline
comment */
}
```

#### Q8. Kevin got runtime error stating unexpected token `<` when he added JSX code inside the <script> tag in index.html file. How will he fix this error?

Modify the script tag like:

- [ ] `<script type=”text/javacsript”>`
- [ ] `<script type=”text/jsx”>`
- [x] `<script type=”text/babel”>`
- [ ] `<script type=”text/babeljs”>`

#### Explanation

Babel is a JavaScript compiler

Babel is a toolchain that is mainly used to convert ECMAScript 2015+ code into a backwards compatible version of JavaScript in current and older
browsers or environments.

When loaded in a browser, `@babel/standalone` will automatically compile and execute all script tags with type `text/babel` or `text/jsx`:

```
<div id="output"></div>
<!-- Load Babel -->
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
<!-- Your custom script here -->
<script type="text/babel">
    const getMessage = () => "Hello World";
    document.getElementById("output").innerHTML = getMessage();
</script>
```

#### Q9. Which of the following libraries is used to compile JSX?

1. [x] react
2. [ ] react-dom
3. [ ] @babel/standalone
4. [ ] Jsx-compiler

#### Explanation

React isn't the only library using JSX. Many others support it as well, such as Vue, preact, inferno, and more

Interchangeability with HTML, meaning we can more easily convert back and forth.

#### Q10. Identify the correct code from the following.

- [x]

```javascript
ReactDOM.render(“<h1>Hello</h1>”,
document.getElementById("root")
)
;
```

- [x]

```javascript
class App extends React.Component {
    render() {
        Return(
            <div>Hello!</div>
        );
    }
}

ReactDOM.render(<App/>, document.getElementById('root'));
```

- [x]

```javascript
const element = <h1>Hello</h1>;
ReactDOM.render(element, document.getElementById("root"));
```

- [ ]

```javascript
class App extends React.Component {
    render() {
        Return(
            <div>Hello!</div>
        );
    }
}

ReactDOM.render(<App/>, document.getElementById('root'), () => {
    console.log(“Root
    compoment
    is
    rendered”;
});
```

- [ ] Option1 , Option2 and Option3
- [ ] Option2 , Option3 and Option4

#### Explanation

The `ReactDOM.render()` function takes two arguments, HTML code and an HTML element.

The purpose of the function is to display the specified HTML code inside the specified HTML element.

Example:

```javascript
ReactDOM.render(<p>Hello</p>, document.getElementById('root'));
```

Example using Class:

```javascript

import React from 'react';
import ReactDOM from 'react-dom/client';

class Car extends React.Component {
    render() {
        return <h2>Hi, I am a Car!</h2>;
    }
}

ReactDOM.render(<Car/>, document.getElementById('root'));
```
