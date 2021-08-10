# Functions

## Multiple Ways to Create Function

```js
// arrow assignment:
const multiply = (a, b) => a * b;
// assignment:
const multiply2 = function(a, b) {
  return a * b;
}
// function declaration:
function multiply3(a, b) {
  return a * b;
}

// using function constructor
const multiply4 = new Function("a", "b", "return a * b");
```

- the last parameter will always be the body, any parameters before body are arguments in function constructor.

## Arguments

- Inside each function is an `arguments` array which can be accessed:

```js
function multiply5() {
  console.log(arguments.callee.name);
  // => multiply5
  // this is not a good idea though:
  return arguments[0] * arguments[1];
}
multiply5(5,10); // => 50;
```

### Additional Properties:

- `arguments.callee.name`: what's the name of the function being called
- `arguments.callee.caller.name`: what's the name of the function that called this function. (could be another function name or global scope)

```js
function multiply6() {
  console.log(arguments.callee.name);
  console.log(arguments.callee.caller.name);
}

(function doMath() {
  multiply6(5,10);
})();

// multiply6
// doMath
```