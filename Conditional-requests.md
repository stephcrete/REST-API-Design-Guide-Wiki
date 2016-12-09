Conditional requests are used for two basic needs:
* optimistic concurrency control
* performance optimization

In order to support conditional requests you SHOULD check if the API client has added any of the following headers to its request:
* [If-Modified-Since](https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.25) (GET requests)
* If-None-Match (GET requests)
* If-Match (updates)
* If-Unmodified-Since (update)

If any of those headers are present, it means that the client issued a conditional request.

For GET requests, if any of the following is true, then you SHOULD return a 304 (Not Modified) with no body content:
* the time stamp provided with If-Modified-Since is the same last known time stamp when the resource was modified
* the ETag provided with the If-None-Match header matches the current ETag of the resource

By returning 304 Not Modified, you indicate to the client that the resource has not changed and that it can continue to use its cached version.

For updates, if any of the following is true, then you SHOULD return a 412 (Precondition Failed) header in your response to indicate the client that the preconditions were not met:
* the ETag provided with the If-Match header does not match the current ETag of the resource (i.e., the client tries to update stale data)
* the time stamp provided in the If-Unmodified-Since header does not match the current last modified time stamp of the resource

Your API client has specified the If-Match header on a request and the current ETag is different from the provided one, then you SHOULD return 412 (Precondition Failed) to indicate the client that the precondition was not met.