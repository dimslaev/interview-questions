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

Standalone function invocation.

```javascript
function foo() {
  console.log(this.a);
}

var a = 2;

foo(); // 2
```

Variables declared in global scope are properties of the global window object.

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

When the call-site has a context object, that object is implicitly used as the `this` binding of the function.

```javascript
function foo() {
  console.log(this.a);
}

var obj = {
  a: 2,
  foo: foo
};

obj.foo(); // 2
```

#### Explicit binding

Explicit binding is when we explicitly bind a context to the function. This is done with `call` or `apply`.

```javascript
function foo() {
  console.log(this);
};

var obj = {
  foo: foo
};

foo() // this === window
foo.call(obj, args1, args2, ...) // this === obj
foo.apply(obj, [array of args]) // this === obj
```

#### Hard binding

This is done with `bind` (ES5). `bind` returns a new function that is hard-coded to call the original function with the `this` context set as you specified.

Hard binding takes precedence over explicit binding.

```javascript
function foo() {
  console.log(this.a);
}

var obj1 = {
  a: 2
};

var obj2 = {
  a: 3
};

foo = foo.bind(obj1); // 2
foo.call(obj2); // 2
```

#### New binding

When a function is called with `new`, it does not care about implicit, explicit, or hard binding. It just creates the new context — which is the new instance.

```javascript
function foo(a) {
  this.a = a;
}

var bar = new foo(2);
console.log(bar.a); // 2
```

### Arrow functions

Arrow functions do not bind their own `this`, instead, they inherit it from the parent scope.
Therefore, none of the 4 binding methods would change the `this` context of an arrow function.

```javascript
const foo = () => {
  console.log(this);
};

const obj = {
  a: 2
};

foo = foo.bind(obj);

foo(); // window or global
```
