# Debouncing

> JavaScript & DOM Events

> No matter how many times the user fires the event, the attached function will be executed only after the specified time once the user stops firing the event.

- A method to verify that a given time has passed since the *user* executed the action.
- Each time the user executes an action, the timer resets and the user must wait until the specified time has elapsed.
- Implemented via the `setTimeout` Web API
- Included in underscore.js and lodash libraries.

## Uses

- Typing in form inputs (and making subsequent calls, such as a search query)

## Syntax / Concept

```js
let timerId;
var  debounceFunction  =  function (func, delay) {
	// Cancels the setTimeout method execution
	clearTimeout(timerId)

	// Executes the func after delay time.
	timerId  =  setTimeout(func, delay)
}

debounceFunction(callback, 200);
```

-----

## Sources

- [Debouncing and Throttling in JavaScript](https://www.telerik.com/blogs/debouncing-and-throttling-in-javascript)
