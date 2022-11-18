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

