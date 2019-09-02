### Conceptual Overview of "this"

`This` is not an author-time binding but a runtime binding. It's context depends on the conditions of the function's invocation.

`This` has nothing to do with where the function is declared, but has instead everything to do with the manner in which the function is called.

### Call-Site & Call-Stack

The _call-site_ - go locate where a function is called from.
The _call-stack_ - the stack of functions that have been called to get us to the current moment in execution.

```javascript
function baz() {
  bar(); // call-site for bar
}

function bar() {
  // call-stack is baz -> bar
  foo(); // call-site for foo
}

function foo() {
  // call-stack is baz -> bar -> foo
}

baz(); // call-site for for baz
```

### 4 types of binding

#### default binding

default binding = Standalone function invocation.

Variables declared in global scope are properties of the global window object.

```javascript
function foo() {
  console.log(this.a);
}

var a = 2;

foo(); // 2
```

If `strict mode` is in effect, the global object is not eligible for the default binding.

```javascript
function foo() {
  "use strict";
  console.log(this.a);
}

var a = 2;

foo(); // TypeError: `this` is `undefined`
```

#### Implicit binding

#### Explicit binding

#### Hard binding

#### New binding

### Arrow functions
