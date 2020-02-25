### What is a constructor in javascript?

Constructor function in JavaScript is used for creating new objects using a blueprint.

Objects can be created based on the the constructor function using the `new` keyword.

```javascript
function Human(firstName, lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
  this.fullName = function() {
    return this.firstName + " " + this.lastName;
  };
}

var person1 = new Human("Joe", "Smith");

console.log(person1); // Joe Smith
```
