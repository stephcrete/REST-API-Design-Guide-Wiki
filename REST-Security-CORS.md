# About
[Cross-Origin Resource Sharing (CORS)](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing) is a W3C standard used to configure cross-origin requests.

CORS can be configured/used by all browsers for implementing cross-domain requests. The spec defines a set of HTTP headers that allow the client browser and server to communicate about which requests are allowed.

For request methods other than GET, HEAD and POST, CORS defines a preflight request interaction. The preflight request occurs "behind-the-scenes" between a CORS-compliant user agent and server, in advance of the client's actual request to a cross-origin resource.

API clients send special HTTP request headers such as Origin and Access-Control-Request-Method.
* the Origin header value identifies the requesting client's scheme/host/port
* the Access-Control-Request-Method header value is sent in the CORS preflight request to indicate which HTTP method will be used in the client's actual request

# Rules
* your REST API SHOULD support CORS only if if needs to be accessed from different domains
* your REST API SHOULD use the Access-Control-Allow-Origin header to list the set of origins that are permitted cross-origin access to its resources.
  * if CORS is enabled for your REST API, then you MUST limit the list of allowed origins and be as precise as possible.

# References
* https://en.wikipedia.org/wiki/Cross-origin_resource_sharing
* https://developer.mozilla.org/en-US/docs/Web/HTTP/Access_control_CORS
* https://www.html5rocks.com/en/tutorials/cors/
* http://enable-cors.org/
