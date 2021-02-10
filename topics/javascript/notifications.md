# Notifications

> This API is only available in secure (HTTPS) environments

```js
// window.Notification

if ( !window.Notification ) {
  console.log("Hey, you don't have the ability to display notifications!");
  // NOTE: this isn't the same as you haven't given 
  // permission to display notifications;
}
```

## Notification.permission

Check the permission status for notifications on the current site/app/origin.

- `default`: no permission set yet
- `granted`: permission given by user to display notifications
- `denied`: user has declined notifications

```js
if ( Notification.permission === "granted" ) {
  // display the notification
}
```

## Notification.requestPermission()

Invoke the browser's permission request prompt for notifications. The user can accept, deny or ignore the request.

Request is asynchronous, so a `Promise` is utilized to handle interaction.

To invoke within code:

```js
Notification.requestPermission().then( result => {
  if ( result === 'granted' ) {
    // display notification
    return;
  }
  // user did not accept permission request;
}).catch( err => console.error(err) ); // handle errors;
```

## new Notification()

Generates a new `Notification` object to display in the browser.

```js
// basic notification with message:
let hiNotification = new Notification(`Hello there!`);
```

In addition to the title message text, additional properties can be provided such as `body` and `icon`:

```js
let newMessageNotification = new Notification(`New Message`, {
  body: `You have a new message from Mark`,
  icon: `http://sample.com/icons/new`
})
```

Sources: [<sup>1</sup>](#source1)

-----

## Examples

- [JavaScript Notifications](https://www.javascripttutorial.net/web-apis/javascript-notification/)

## Sources

<sup id="source1">1</sup> [How to show desktop notifications using JavaScript by Atta](https://dev.to/attacomsian/how-to-show-desktop-notifications-using-javascript-5aco)
