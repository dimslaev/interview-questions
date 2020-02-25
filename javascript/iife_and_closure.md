### Define IIFE

An IIFE, or Immediately Invoked Function Expression, is a common JavaScript design pattern used by most popular libraries (jQuery, Backbone.js, Modernizr, etc) to place all library code inside of a local scope, thus preventing polution of the global scope.

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

Consider the following use cases:

#### Closures and Private Data

Closures are one of the most widely use cases for an IIFE.
A closure is a function having access to the parent scope, even after the parent function has been executed.
When an IIFE returns a closure function, it provides access to the local variables even when that function is executed outside of the IIFE's lexical scope.

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

Note that the `counter` variable is inaccessible from outside of the IIFE. Except for the function that's being returned, nobody can read or modify the `counter` variable. This allows for the creation of truly private state that can only be modified in a controlled fashion. The revealing module pattern relies heavily on this mechanism:

```javascript
const counter = (function() {
  let counterValue = 0;

  return {
    increment() {
      ++counterValue;
    },

    get value() {
      return counterValue;
    }
  };
})();

counter.increment();
console.log(counter.value); // 1

counter.increment();
counter.increment();
console.log(counter.value); // 3
```

#### Aliasing Variables

Sometimes, you might be in the situation that you're using two different libraries that expose a global variable with the same name. For instance, consider that you're using jQuery and another library that also assigns to the \$ global variable.

To resolve this naming conflict, you can wrap a piece of code with an IIFE that passes one of the global variables (e.g. jQuery) as an argument. Within the function, you can then refer to the value by a parameter name (e.g. \$) of your choosing:

```javascript
window.$ = function somethingElse() {
  // ...
};

(function($) {
  // ...
})(jQuery);
```
