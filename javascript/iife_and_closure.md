### Define IIFE

An IIFE, or Immediately Invoked Function Expression, is a common JavaScript design pattern used by most popular libraries (jQuery, Backbone.js, Modernizr, etc) to place all library code inside of a local scope.

An anonymous IIFE is not being assigned to a global variable, therefore no global property is being created, and all of the properties created inside of the function expression are scoped locally to the expression itself.

```javascript
// Anonymous function
(function() {
  var foo = function() {
    console.log("foo");
  };
})(); // The parentheses make sure the anonymous function gets called immediately

foo(); // foo is not defined
```

### Define Closure

A closure is a function having access to the parent scope, even after the parent function has closed.

```javascript
var add = (function() {
  var counter = 0;

  return function() {
    counter += 1;
    return counter;
  };
})();

console.log(add()); // 1
console.log(add()); // 2
console.log(add()); // 3
```

In the example above, the IIFE function is executed immediately and then closed.
What's assigned to the referrence `add` after the execution is the returned closure function, which in turn has access to the locally scoped variable `counter`.
