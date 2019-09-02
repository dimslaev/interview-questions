### Define Javascript? 
JavaScript is a lightweight, single-threaded, and interpreted programming language with object-oriented capabilities that allows you to build interactivity into otherwise static HTML pages.

### What is OOP? 

Object Oriented Programming (OOP) refers to using self-contained pieces of code (objects, functions) that can interact between each other to develop applications. 

OOP allows to for: 
- Reusable code
- Scalable architecture 
- Efficiency and readability 

In Javascript, OOP refers to: 
- Encapsulation and Inheritance
- Object literals and Constructor functions


### What is Encapsulation? 

Refers to enclosing all properties and methods of an object inside that object, which allows us to:
- Hide variables from the global scope
- Create new object instances from the same object 

```javascript
function User (name) {
    this.name = theName
}
Var user1 = new User(‘Dimitar’)
Var user2 = new User(‘Emil’)
```


### What is Inheritance? 

Inheritance allows us to: 
- Create new object based on existing object inheriting its methods and properties
- Extending and modifying the inherited properties and methods 

```javascript
function Student(name) {
  this.name = name
}

Student.prototype.print = function() {
  console.log(`Name: ${this.name}`)
}

function Teacher(name, subject) {
  Student.call(this, name)
  this.subject = subject
}

Teacher.prototype = Object.create(Student.prototype)

Var teacher1 = new Teacher(‘Troy’, ‘literature’)

teacher1.print() // Name: Troy
```


### What is IIFE?

IIFE stands for Immediately Invoked Function Expression. It is a JavaScript function that runs as soon as it is defined.

- IIFE protects the global namespace by not creating a named function
- Mainly used because of privacy
- All the variables inside the IIFE stay within the scope of the function

```javascript
(function() {
   let name = "IIFE"
   alert(name)
}
)()
```

### What is a First Class Function? 

A programming language is said to have First-class functions when functions in that language are treated like any other variable. 

A first class function can be: 

- passed as an argument to other functions
- returned by another function
- assigned as a value to a variable

```javascript
// Pass `sayHello` as an argument to `greeting` function
function sayHello() {
   return "Hello, "
}
function greeting(helloMessage, name) {
  console.log(helloMessage() + name)
}
greeting(sayHello, "JavaScript!")

// Return a function
function sayHello() {
   return function() {
      console.log("Hello!")
   }
}

// Assign a function to a variable
const foo = function() {
   console.log("foobar")
}
```


### What is closure? 
When we create a function inside another function in JavaScript, the inner function has access to the scope of the outer function as well as its own. 
- The inner function has access to the outer function even after the outer function has finished executing. 
- Closures are often used in JavaScript to protect variables from outside manipulation, or to hide implementation details.
- What other use cases? 
```javascript
function counter() {
  let total = 0

  return function count() {
    total++
    return total
  }
}

let count = counter()
```

- In the example above, we don’t have access to the total variable from outside of the `counter()`. We’re able to call `count` and increment `total` from the outside but we cannot access the value directly.



### Difference between “undefined” and “NULL”?
`Undefined` means a variable has been declared, but the value of that variable has not yet been defined.

```javascript
var user
console.log(user) // undefined 
```

`Null` means an empty or non-existent value. Also, it returns an object. 



### What is a Higher Order Function? 
These are functions that either return another function, or accept one or more function(s) as input parameters.
They are called higher-order because they are more concerned with higher-level concepts than lower-level details.
Higher-order functions allow us to compose our JavaScript applications from smaller, single-responsibility units of code




### Can you name two programming paradigms important for JavaScript app developers?
- Prototypal inheritance
- Functional programming (closures, first class functions, higher order functions)



### What are the different paradigms of a programming languages?


