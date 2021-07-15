# Cookies

- Cookies allow websites to store persistent information. 
- Cookies are structured in a key/value format.
- Can store up to `4096` bytes of data.
- Each cookie can store:
  - Name
  - Value
  - Domain
  - Path
  - Expires / Max-Age
- Browsers can limit the number of cookies that are saved to a domain.

## Cookie Creation

There are two ways to create a cookie:

1. HTTP response
1. JavaScript

### HTTP Response

```txt
HTTP/2.0 200 OK
Content-type: text/html
Set-Cookie: version=1.0.0
Set-Cookie: appid=lemonlime
```

Can add additional properties such as `secure` and `HttpOnly`. Secure means that cookie can only be transferred over HTTPS connections. `HttpOnly` ensures that the cookie cannot be read by JavaScript on the browser.

### JavaScript

Syntax `document.cookie`

## Types of Cookies

- Session: removed when browser is closed
- Persistent: stay until expire or removed by choice
- Third-Party: cookies saved from other domains

## Cookie Length

- `Expires`: set a fixed expiration date in GMT
- `Max-Age`: set number of seconds cookie is active

### Examples

```js
// Expires example:
const campaignEndDate = new Date(2024, 11, 4);
document.cookie = `campaign=active; expires=${campaignEndDate.toUTCString()};`;

// Max-Age example:
const ONE_DAY_SECS = 24 * 60 * 60;
document.cookie =  `rent=92jalh293la; max-age=${ONE_DAY_SECS};`;
```
