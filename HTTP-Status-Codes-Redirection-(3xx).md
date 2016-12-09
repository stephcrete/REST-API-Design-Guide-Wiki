# 301 (Moved permanently)
The requested resource has been assigned to a new permenent URI and any future references to this resource SHOULD use one of the returned URIs.

For example, assuming that some 'users' resource is now served by another version:

```
.../api/v1/users
-> 301 .../api/v2/users
```

Use cases:
* permanent redirection

The response SHOULD include the _Location_ header.

# :x: 302 (Found)
This status code was misunderstood and wrongly implemented/used over the years.

For this reason, the HTTP specification has evolved and introduced the 303 and 307 status codes, which distinguish between the wrong and correct interpretations of the original 302 status code.

:x: You MUST NOT use this status code. Instead, look at 303 and 307.

# 303 (See other)
Indicates that a controller resource has finished its work, but instead of sending a potentially unwanted response body, it sends the client the URI of a response resource.

This can be the URI of a temporary status message, or the URI to some already existing, more permanent, resource.

This status code allows the API to send a reference to a resource without forcing the client to download its state. 

Instead, the client may send a GET request to the value of the Location header
SHOULD be used to refer the client to a different URI.

Use cases:
* redirect to another resource without forcing the data to the client

The response
* SHOULD include the _Location_ header
* SHOULD not include body content

# 304 (Not modified)
Used when there is state information associated with a resource but the client already has the most recent version.

Use cases:
* conditional requests

The response body SHOULD be empty.

# 307 (Temporary redirect)
Indicates that the REST API is not going to process the client's request. Instead, the client SHOULD re-submit the request to the URI specified by the response message's Location header. The new request MUST use the same verb (e.g., POST if the previous request was a POST).

The redirection is temporary and the client SHOULD continuie to use the same request URI for future requests.

Example: assuming that a "something" resource is temporarily served by another endpoint (e.g., component maintenance or smoke test). Could make a lot of sense considering microservices.

```
.../apiFoo/v1/something
-> 307 .../apiBar/v1/something
```

Use cases:
* temporarily redirect to another URI

The response SHOULD include the _Location_ header.