# HTTP Response Headers

## Accept-Ranges

Whether server supports the Range: request header

## Access-Control-*

Called CORS headers. These allow cross-origin requests.

## Age

How many seconds response has been cached

## Cache-Control

Various caching settings (such as no-cache)

## Connection

"close" means "close connection after this response"

## Content-Encoding

Goes with Accept-Encoding request header. Example: "gzip"

## Content-Language

Goes with Accept-Language request header: Example: "en-us"

## Content-Length

Length of body in bytes: Example: 12945

## Content-Type

Goes with Accept: request header. Example: "image/png"

## Date

When response was sent

## ETag

Hash of response body

## Expires

The rsponse is stale (should be re-requested) after this time

## Last-Modified

When content was last modified (not always accurate)

## Location

URL to redirect to (for a 3xx response)

## Set-Cookie

Sets a cookie

## Vary

Lists request headers to cache based on

## Via

Added by proxy servers. Example: Via: nginx

-----

## Sources

- Julia Evans @b0rk on Twitter
