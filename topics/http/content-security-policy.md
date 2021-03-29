# Content Security Policy (CSP)

- added layer of security to help detect and mitigate certain types of attacks such as XSS and data injection
- designed to be fully backwards-compatible (except CSPv2)
- to enable CSP, configure web server to return the `Content-Security-Policy` HTTP header
- alternatively, a `<meta>` element can be used from within HTML code: `<meta http-equiv="Content-Security-Policy" content="default-src 'self'; img-src https://*; child-src 'none'">`
- XSS attacks exploit browser's trust of the content received from the server (host)
- therefore, malicious scripts trigger attacks because the browser trusts the source of the content, even if it is not exactly coming from where it seems to be coming from
- basically, "you can have a script that says it's executing from somewhere like facebook.com to do sharing, but it could actually be coming from a site like 'fa.cebook.com' which could be a hacker's host location. (very easy to overlook the fact that the bad domain looks like facebook.com)"
- server admins can specify which domains scripts and resources can be executed from within the page
- CSP-enabled browsers will hold to these restrictions and not execute ones that are not explicitly specified
- this includes inline scripts that can load other scripts
- admins can also specify what protocols are allowed (so a page will only accept HTTPS connections)
- by enforcing HTTPS, admins can also provide the `Strict-Transport-Security` HTTP header to ensure that browsers connect to them via encrypted channels (to prevent "packet sniffing" or "man-in-the-middle attacks"

## Implementation

- one example would be a page that only allows form execution to a specific location (endpoint)
- policies are authored in a series of directives (for resource types or policy areas)
- the use of `default-src` is a large set of default directives that can provide a base-level of security
- `default-src` or `script-src` directives are required to prevent inline scripts from executing as well as blocking the use of `eval()` in JavaScript
- `default-src` or `style-src` directives are required to restrict inline styles from being applied from a `<style>` element or `style` attribute (inline styles)

### Examples

- All content should come from site's own domain (excluding subdomains)
`Content-Security-Policy: default-src 'self'`

- Content can be accepted from own domain AND a trusted domain (including subdomains)
`Content-Security-Policy: default-src 'self' *.trusted.com`

- Image content can come from any domain, *BUT* audio/video media have to come from trusted providers (excluding their subdomains) *AND* scripts have to come from a trusted provided source:
`Content-Security-Policy: default-src 'self'; img-src *; media-src media1.com media2.com; script-src userscripts.example.com`

## Reports

- CSP can be tested and reported by using the `Content-Security-Policy-Report-Only` HTTP header
- Reports can also be sent while CSP is being enforced (as opposed to tested) by providing a `report-uri` location:
`Content-Security-Policy: default-src 'self'; report-uri http://reports.example.com/collector.cgi`
- The report will contain various keys and values of the offending locations or requests

-----

## Sources

- [Content Security Policy (CSP) - HTTP | MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)
