# Throttling

> JavaScript DOM Events

> Throttling is a technque in which, no matter how many times the user fires the event, the attached function will be executed only once in a given time interval.

- The event will only fire after a specified time amount, the user can click as many times as they wish.
- Implemented via the `setTimeout` Web API
- Included in underscore.js and lodash libraries.

## Uses

- scroll events
- resize events
- user controlled actions where events can fire off rapidly
- click events
- mouse move event

## Syntax / Concept

```js
var  throttleFunction  =  function (func, delay) {
	// If setTimeout is already scheduled, no need to do anything
	if (timerId) {
		return
	}

	// Schedule a setTimeout after delay seconds
	timerId  =  setTimeout(function () {
		func()
		
		// Once setTimeout function execution is finished, timerId = undefined so that in <br>
		// the next scroll event function execution can be scheduled by the setTimeout
		timerId  =  undefined;
	}, delay)
}

throttleFunction(callback, 1000)
```

-----

## Sources

- [Debouncing and Throttling in JavaScript](https://www.telerik.com/blogs/debouncing-and-throttling-in-javascript)
