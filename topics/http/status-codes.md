# HTTP Status Codes

## Code Groups

### 1xx - Information

- **100 - Continue**: server has received request and client should send the request body. Server has not yet rejected request.
- **101 - Switching Protocols**: requester has asked server to switch protocols and server has agreed to make switch.
- **102 - Processing**: server has received request and is processing, no response yet.
- **103 - Early Hints**: used to return some response headers before final HTTP message.

### 2xx - Success

- **200 - OK**: standard response for successful HTTP request. Requested resource has been returned via the message body.
- **201 - Created**: request has been fulfilled and server acknowledged new resource was created.
- **202 - Accepted**: server has received and is processing the request, however no response is sent yet.
- **204 - No Content**: server successfully processed request, but no content is returned.

### 3xx - Redirection

- **301 - Moved Permanently**: resource's URL has been moved and is likely not to be moved in the future. Useful for browser to quickly redirect to new resource's final location.
- **305 - Use Proxy**: requested resource is available only via a proxy; address is provided in the response.
- **307 - Temporary Redirect**: requested resource has temporarily been moved to another url, but could return and future requests should use original url link.

### 4xx - Client Error

- **400 - Bad Request**: server cannot process request due to syntax error
- **401 - Unauthorized**: response sent back when authentication is used and has failed; requested resource is protected.
- **403 - Forbidden**: server understands request, however server is refusing to grant access due to authentication requirement
- **404 - Not Found**: resource could not be found at time of request
- **405 - Method Not Allowed**: request method is not supported for requested resource (ex: PUT in a read only resource)
- **414 - URI Too Long**: requested URI was too long for the server to process and understand; too much data in the query-string of a GET request.
- **429 - Too Many Requests**: client has sent too many requests in a specified amount of time; helps reduce flooding of traffic to server

### 5xx - Server Error

- **500 - Internal Server Error**: error message displayed that does not match any other server error cases
- **501 - Not Implemented**: server does not understand requested method or does not have the ability to fulfil sent request.
- **502 - Bad Gateway**: server is acting as a gateway and received an invalid response from server during request
- **503 - Service Unavailable**: server cannot handle requests due to maintenance, being down, or overloaded with requests.
- **511 - Network Authentication Required**: client needs to authenticate to obtain network access

-----

## Sources

- [HTTP Status Codes that You must know](https://dev.to/ayushi7rawat/http-status-codes-that-you-must-know-5edn)
- [Your Guide to HTTP Response Status Code](https://dev.to/ayabouchiha/http-response-status-code-43ai)
