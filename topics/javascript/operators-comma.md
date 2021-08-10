# Comma Operator

- Returns last expression in chain

```js
let grades = (90,85,100);
console.log(grades); // => 100
```

- Used in `for loops`:

```js
for ( const i = 0; i < 10; i++ ) { ... }
```

- Writing lambda functions:

```js
let data = [];
const lb = (a, b, arr) => (arr.push(a*b), a*b);
lb(5,5,data);
// => 25
console.log(data);
// => data[0] = 25;
```