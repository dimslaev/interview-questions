### How React works? How Virtual-DOM works in React?

Updating Real DOM is slow because any time a re-render happens the browser needs to do a number of expensive operations such as Recalculating the CSS and changed layouts.

React solves this by creating a virtual DOM - a javascript model of the real DOM (Document Object Model).

When state changes in a React component it firstly runs a “diffing” algorithm, which identifies what has changed in the virtual DOM. The second step is reconciliation, where it updates the real DOM with the results of diff, touching only the elements which have actually changed.

In React, each of our components have a state. This state is like an observable. Essentially, React knows when to re-render the scene because it is able to observe when this data changes. Dirty checking is slower than observables because we must poll the data at a regular interval and check all of the values in the data structure recursively. By comparison, setting a value on the state will signal to a listener that some state has changed, so React can simply listen for change events on the state and queue up re-rendering.

[hackernoon](https://hackernoon.com/virtual-dom-in-reactjs-43a3fdb1d130)
[medium](https://medium.com/@vigowebs/frequently-asked-react-js-interview-questions-and-answers-36f3dd99f486)

### What is JSX?

JSX is a syntax extension to JavaScript and comes with the full power of JavaScript.
It has an XML/HTML-like syntax which allows to write HTML-like code inside JavaScript/React code... Unlike the past, instead of putting JavaScript into HTML, JSX allows us to put HTML into JavaScript.

The first part of a JSX tag determines the type of the React element.

```javascript
<div className="sidebar" />;

// =>

React.createElement("div", { className: "sidebar" }, null);
```

Capitalized types indicate that the JSX tag is referring to a React component.

```javascript
<MyButton color="blue" shadowSize={2}>
  Click Me
</MyButton>;

// =>

React.createElement(MyButton, { color: "blue", shadowSize: 2 }, "Click Me");
```

### What's a React Element?

### Describe the component lifecycle in React

Lifecycle hooks can be grouped in 3 separate stages:

- Mounting (render, componentDidMount)
- Updating (shouldComponentUpdate, componentDidUpdate)
- Unmounting (componentWillUnmount)

The methods above are now considerred legacy, since the introduction of the so-called React Hooks.

- useState - Returns a stateful value (with initialState), and a function to update it.
- useEffect - Runs after the render is committed to the screen. Use cases include api calls, timers, loggers etc.
- useLayoutEffect - Runs before browser paint. Used for visible DOM mutations, so that users don't perceive a visual inconsistency.
- useContext - Returns the context of the nearest context provider. Used to avoid passing props to deeply nested children.
- useReducer - An alternative to useState. Returns the current state paired with a dispatch method. Use it to pass state along with method to to alter that state from a child component.
- useMemo
- useCallback
- useRef
- useImperativeHandle
- useDebugValue

### What are the differences between a class component and functional component?

Class components have local state and lifecycle hooks.
Functional components can receive props, but do not have local state or hooks. They can change the state of a parent class component only indirectly - via a callback function that uses setState passed as a prop.

### What are controlled and uncontrolled components in React?

- Controlled Component - it's value and change methods are linked to the state and handlers inside its parent component.
- Uncontrolled Component - it stores its own state internally, and you query the DOM using a ref to find its current value when you need it.

### Unidirectional data flow

Unidirectional data flow means that data can travel only in one direction - from parent to child components, or the other way around, but cannot travel from one child to another without passing through a common parent component.

In React, changing state on a Component will never affect its parent, or its siblings, or any other Component in the application: just its children.

This is the reason that the state is often moved up in the Component tree, so that it can be shared between components that need to access it.

### Immutability

When data is immutable, its state cannot change after it’s created. If you want to change an immutable object, you can’t. Instead, you create a new object with the new value.

Immutability is a hot topic because it relates to current paradigms (such as functional programming, ) and libraries (such as React, Vue.js, etc).

For example, in React, one should never mutate the state property of a component directly, but only through the `setState` method. The `setState` method creates a new copy of the virtual dom and applies changes to that copy without touching the previous state object.

In functional programming, Higher-order functions such as `map`, `filter`, `reduce`, and `concat` create copies of existing arrays and manipulate those copies without mutating the original ones.

```javascript
let updatedObj = this.state.obj.concat("new prop 1, new prop 2.");
this.setState({ obj: updatedObj });
```

### Functional programming
