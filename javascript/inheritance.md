### Classical inheritance vs Prototypal inheritance

_Classical inheritance_: instances inherit from classes (like a blueprint — a description of the class), and create sub-class relationships: hierarchical class taxonomies. Instances are typically instantiated via constructor functions with the `new` keyword. Class inheritance may or may not use the `class` keyword from ES6.

```javascript
class Animal {
  constructor(name) {
    this.speed = 0;
    this.name = name;
  }
  run(speed) {
    this.speed += speed;
    console.log(`${this.name} runs with speed ${this.speed}.`);
  }
  stop() {
    this.speed = 0;
    console.log(`${this.name} stands still.`);
  }
}

let animal = new Animal("My animal");

// Inherit from Animal by specifying "extends Animal"
class Rabbit extends Animal {
  constructor(name) {
    super();
    this.name = name;
  }

  hide() {
    console.log(`${this.name} hides!`);
  }
}

let rabbit = new Rabbit("White Rabbit");

rabbit.run(5); // White Rabbit runs with speed 5.
rabbit.hide(); // White Rabbit hides!
```

_Prototypal Inheritance_: instances inherit directly from other objects. Instances are typically instantiated via factory functions or `Object.create()`. Instances may be composed from many different objects, allowing for easy selective inheritance.

```javascript
function Animal(name) {
  this.speed = 0;
  this.name = name;
}

Animal.prototype.run = function(speed) {
  this.speed += speed;
  console.log(`${this.name} runs with speed ${this.speed}.`);
};

Animal.prototype.stop = function() {
  this.speed = 0;
  console.log(`${this.name} stands still.`);
};

let animal = new Animal("My animal");

function Rabbit(name) {
  Animal.call(this, name);
}

Rabbit.prototype = Object.create(Animal.prototype);

Rabbit.prototype.hide = function() {
  console.log(`${this.name} hides!`);
};

let rabbit = new Rabbit("White Rabbit");

rabbit.run(5); // White Rabbit runs with speed 5.
rabbit.hide(); // White Rabbit hides!
```

In JavaScript, prototypal inheritance is simpler & more flexible than class inheritance.

However, Inheritance makes us turn a blind eye to the inevitable fact that our class structure will most likely change in the future, and when it does, our tightly coupled inheritance structure is going to crumble.

A better approach is to use compostion.

### JavaScript Inheritance vs Composition

Rather than thinking in terms of what things are, what if we think in terms of what things do?

```javascript
const run = name => console.log(`This ${name} runs!`);
const stop = name => console.log(`This ${name} stops!`);
const hide = name => console.log(`This ${name} hides!`);

function Dog(name) {
  return Object.create({ run: () => run(name), stop: () => stop(name) });
}

const dog = Dog("dog");
dog.run(); // This dog runs!
dog.stop(); // This dog stops!

function Rabbit(name) {
  return Object.create({
    run: () => run(name),
    stop: () => stop(name),
    hide: () => hide(name)
  });
}

const rabbit = Rabbit("rabbit");

rabbit.run(); // This rabbit runs!
rabbit.hide(); // This rabbit hides!
```

### Composition in React

_"React has a powerful composition model, and we recommend using composition instead of inheritance to reuse code between components."_

```javascript
function FancyBorder(props) {
  return (
    <div className={"FancyBorder FancyBorder-" + props.color}>
      {props.children}
    </div>
  );
}
```

```javascript
function WelcomeDialog() {
  return (
    <FancyBorder color="blue">
      <h1 className="Dialog-title">Welcome</h1>
      <p className="Dialog-message">Thank you for visiting our spacecraft!</p>
    </FancyBorder>
  );
}
```
