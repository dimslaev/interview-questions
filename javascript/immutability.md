### Immutability

When data is immutable, its state cannot change after it’s created. If you want to change an immutable object, you can’t. Instead, you create a new object with the new value.

Immutability is a hot topic because it relates to current paradigms (such as functional programming) and libraries (such as React, Vue.js, etc).

For example, in React, one should never mutate the state property of a component directly, but only through the `setState` method. The `setState` method creates a new copy of the virtual dom and applies changes to that copy without touching the previous state object.

In functional programming, Higher-order functions such as `map`, `filter`, `reduce`, and `concat` create copies of existing arrays and manipulate those copies without mutating the original ones.

```javascript
let updatedObj = this.state.obj.concat("new prop 1, new prop 2.");
this.setState({ obj: updatedObj });
```
