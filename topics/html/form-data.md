# Form Data

- Low-level API that lets any JavaScript code participate in a form submission
- Executed via a `formdata` event listener attached to a live `<form>` element
- `FormData` event will fire with an object that holds all data for the form submission
- In the `FormData` listener, values can be added, modified or deleted before the actual submission is sent
- Inputs with `hidden` attributes are no longer needed as the form can use JavaScript to send additional data that is in the background of a form submission
- Custom elements via WebComponents can call methods and properties to make them hook into the FormData API natively

-----

## Sources

- [More capable form controls  |  web.dev](https://web.dev/more-capable-form-controls)
