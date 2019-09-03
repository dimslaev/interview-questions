### Strict Mode

`use strict` is a way to enforce stricter parsing and error handling on JavaScript code at runtime.

- Makes debugging easier. Code errors that would otherwise have been ignored or would have failed silently will now generate errors.
- Prevents accidental globals. Without strict mode, assigning a value to an undeclared variable automatically creates a global variable with that name. This is one of the most common errors in JavaScript. In strict mode, attempting to do so throws an error.
- Eliminates this coercion. Without strict mode, a reference to a this value of null or undefined is automatically coerced to the global.
- Disallows duplicate parameter values (e.g., function foo(val1, val2, val1){})
- Throws error on invalid usage of delete. The delete operator (used to remove properties from objects) cannot be used on non-configurable properties of the object.
