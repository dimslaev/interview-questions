### VAR

_Scope of var_
Scope essentially means where these variables are available for use. var declarations are globally scoped or function/locally scoped.

The scope is global when a var variable is declared outside a function. This means that any variable that is declared with var outside a function block is available for use in the whole window.

var is function scoped when it is declared within a function. This means that it is available and can be accessed only within that function.

```javascript
var greeter = "hey hi";

function newFunction() {
  var hello = "hello";
}
```

Here, greeter is globally scoped because it exists outside a function while hello is function scoped. So we cannot access the variable hello outside of a function. So if we do this:

```javascript
var tester = "hey hi";

function newFunction() {
  var hello = "hello";
}
console.log(hello); // error: hello is not defined
```

_var variables can be re-declared and updated_

```javascript
var greeter = "hey hi";
var greeter = "say Hello instead";
```

and this also

```javascript
var greeter = "hey hi";
greeter = "say Hello instead";
```

_Hoisting of var_

Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their scope before code execution. This means that if we do this:

```javascript
console.log(greeter);
var greeter = "say hello";
```

it is interpreted as this:

```javascript
var greeter;
console.log(greeter); // greeter is undefined
greeter = "say hello";
```

So var variables are hoisted to the top of their scope and initialized with a value of undefined.

_Problem with var_

There's a weakness that comes with var. I'll use the example below to explain:

```javascript
var greeter = "hey hi";
var times = 4;

if (times > 3) {
  var greeter = "say Hello instead";
}

console.log(greeter); // "say Hello instead"
```

So, since times > 3 returns true, greeter is redefined to "say Hello instead". While this is not a problem if you knowingly want greeter to be redefined, it becomes a problem when you do not realize that a variable greeter has already been defined before.

### LET

let is now preferred for variable declaration. It's no surprise as it comes as an improvement to var declarations. It also solves the problem with var that we just covered. Let's consider why this is so.

let is block scoped
A block is a chunk of code bounded by {}. A block lives in curly braces. Anything within curly braces is a block.

So a variable declared in a block with let is only available for use within that block. Let me explain this with an example:

```javascript
let greeting = "say Hi";
let times = 4;

if (times > 3) {
  let hello = "say Hello instead";
  console.log(hello); // "say Hello instead"
}
console.log(hello); // hello is not defined
```

We see that using hello outside its block (the curly braces where it was defined) returns an error. This is because let variables are block scoped .

_let can be updated but not re-declared._

Just like var, a variable declared with let can be updated within its scope. Unlike var, a let variable cannot be re-declared within its scope. So while this will work:

```javascript
let greeting = "say Hi";
greeting = "say Hello instead";
```

this will return an error:

```javascript
let greeting = "say Hi";
let greeting = "say Hello instead"; // error: Identifier 'greeting' has already been declared
```

However, if the same variable is defined in different scopes, there will be no error:

```javascript
let greeting = "say Hi";
if (true) {
  let greeting = "say Hello instead";
  console.log(greeting); // "say Hello instead"
}
console.log(greeting); // "say Hi"
```

Why is there no error? This is because both instances are treated as different variables since they have different scopes.

This fact makes let a better choice than var. When using let, you don't have to bother if you have used a name for a variable before as a variable exists only within its scope.

Also, since a variable cannot be declared more than once within a scope, then the problem discussed earlier that occurs with var does not happen.

_Hoisting of let_

Just like var, let declarations are hoisted to the top. Unlike var which is initialized as undefined, the let keyword is not initialized. So if you try to use a let variable before declaration, you'll get a Reference Error.

### CONST

Variables declared with the const maintain constant values. const declarations share some similarities with let declarations.

_const declarations are block scoped_

Like let declarations, const declarations can only be accessed within the block they were declared.

_const cannot be updated or re-declared_

This means that the value of a variable declared with const remains the same within its scope. It cannot be updated or re-declared. So if we declare a variable with const, we can neither do this:

```javascript
const greeting = "say Hi";
greeting = "say Hello instead"; // error: Assignment to constant variable.
```

nor this:

```javascript
const greeting = "say Hi";
const greeting = "say Hello instead"; // error: Identifier 'greeting' has already been declared
```

Every const declaration, therefore, must be initialized at the time of declaration.

This behavior is somehow different when it comes to objects declared with const. While a const object cannot be updated, the properties of this objects can be updated. Therefore, if we declare a const object as this:

```javascript
const greeting = {
  message: "say Hi",
  times: 4,
};
```

while we cannot do this:

```javascript
const greeting = {
  words: "Hello",
  number: "five",
}; // error:  Assignment to constant variable.
```

we can do this:

```javascript
greeting.message = "say Hello instead";
```

This will update the value of greeting.message without returning errors.

_Hoisting of const_

Just like let, const declarations are hoisted to the top but are not initialized.

So just in case you missed the differences, here they are:

_var_ declarations are globally scoped or function scoped while _let_ and _const_ are block scoped.
_var_ variables can be updated and re-declared within its scope; _let_ variables can be updated but not re-declared; _const_ variables can neither be updated nor re-declared.
They are all hoisted to the top of their scope. But while _var_ variables are initialized with undefined, _let_ and _const_ variables are not initialized.
While _var_ and _let_ can be declared without being initialized, _const_ must be initialized during declaration.

[freecodecamp](https://www.freecodecamp.org/news/var-let-and-const-whats-the-difference/)
