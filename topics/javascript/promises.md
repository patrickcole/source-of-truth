# Promises

## Background / Notes

- JavaScript is synchronous and mono-threaded, calls are executed in order
- Promises provide the ability to execute code asynchronously

## Syntax

```js
const statePromise = new Promise( (resolve, reject) => {
  // show a case for resolving
  const success = true;
  // using guard condition; showing
  // rejection logic first:
  if ( !success ) {
    reject('failed')
  }
  resolve('success!');
})
```

Now when ready to use Promise, can be invoked from variable it was saved under:

```js
statePromise
  .then(result => console.log(result))
  .catch(error => console.error(error))

// => "success"
```

Taking same example and converting it to `async/await`:

```js
(async () => {
  const state = await statePromise;
})();
```

Note the use of an `IIFE` to allow the `async` and `away` keywords to be applied.

Here's another example to append to previous example:

```js
const getAccessLevel = function(state) {
  // a promise inside a function MUST be returned
  // or the value will not propagate upwards:
  return new Promise( (resolve, reject) ) => {
    if ( state !== 'success' ) {
      reject('user not logged in');
    }
    resolve('administrator');
  });
}

// once again using an IIFE:
(async () => {
  const state = await statePromise; // get the state response
  const user = await getAccessLevel(state); // pass that into function that returns promise;
  console.log(user);
  // => "administrator"
})();
```

The example above shows that `getAccessLevel` AND the `console.log` must wait for `await statePromise` to be either resolved or rejected. (NOTE: Here I am not using try/catch blocks, but it is highly recommended)

------

## Sources

- [The Promises guide I would have loved as a junior developer(sic)](https://dev.to/spartakyste/the-promises-guide-i-would-have-loved-as-a-junior-developper-3621)
