### Pure functions 

1. Their return value depends solely on the value of their arguments.

```javascript
function pure(a, b) {
    return a * b; 
}
```

2. They don't have side effects (network or database calls).

```javascript
function impure(a, b) {
    let c;

    fetch('/api/values').then(function(value) {
        c = value;
    })

    return a * b * c; 
}
```

3. They do not overwrite the values passed to them.

```javascript
function pure(someArray) {
    return someArray.map(x => x * 2)
}

function impure(someArray) {
    someArray.forEach((x, i) => {
        someArray[i] = someArray[i] * 2
    }) 
    return someArray;
}
```

[From Redux Tutorial](https://egghead.io/lessons/react-redux-pure-and-impure-functions)