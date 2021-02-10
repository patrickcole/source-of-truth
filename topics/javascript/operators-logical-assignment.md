# Operators - Logical Assignment

> Support was added in ES2021

## AND Assignment

```js
// syntax: x &&= y
// x: expression
// y: value to assign
```

If the value of `x` is **truthy**, then the value of `y` will be assigned to `x`.

Sources: [<sup>1</sup>](#source1)

```js
let x1 = 1; // <- truthy
let x2 = 0; // <- falsy
const Y_VAL = 100;

// if x is truthy, uses assignment:
console.log(x1 &&= Y_VAL); // => 100

// if x is falsy, does not use assignment:
console.log(x2 &&= Y_VAL); // => 0
```

## OR Assignment

```js
// syntax: x ||= y
// x: expression
// y: value to assign
```

If the value of `x` is **falsy**, then the value of `y` will be assigned to `x`. In the case, that `x` is truthy, the expression will be short-circuited. In other words, it will continue without re-assigning the `y` value to `x` since the expression is already true.

Sources: [<sup>1</sup>](#source1)

```js
let x3 = true; // <- truthy
let x4 = ''; // <- falsy

// if x is truthy, DO NOT reassign value:
console.log(x3 ||= 64); // => true

// if x is falsy, reassign value:
console.log(x4 ||= 'x was falsy, so we see this message');
// => x was falsy, so we see this message
```

## Nullish Assignment

```js
// syntax: x ??= y
// x: expression
// y: value to assign
```

If the value of `x` is either `null` or `undefined`, the value of `y` is reassigned. Useful for when properties do not currently exist on an object.

```js
// an object with just the property, 'id':
const x5 = { id: '939bac' };

// does not assign since 'id' is property in object:
console.log(x5.id ??= 0); // => '939bac';

// assigns value 'DefaultUser' as 'username' is not defined in object:
console.log(x5.username ??= 'DefaultUser'); // => 'DefaultUser'
```

-----

## Sources

<sup id="source1">1</sup> [Logical Assignment Operators by Aaron Goldsmith](https://dev.to/aarongoldsmith1/logical-assignment-operators-1g62)
