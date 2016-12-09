# 400 (Bad request)
The request could not be understood by the server due to malformed syntax.
The client SHOULD NOT repeat the request without modifications.

Use cases:
* invalid/incomplete request
* return multiple client errors at once (cfr error handling section)

# 401 (Unauthorized)
The request requires user authentication.
The client MAY repeat the request with a suitable Authorization header field.

Use cases:
* client not authenticated

# 403 (Forbidden)
The client is authenticated but not authorized
An API client might be allowed to use some API resources but not some others; in that case he should receive a 403 error

Use cases:
* client not authorized/allowed

# 404 (Not Found)
The server has not found anything matching the request URI

Use cases:
* not found

# 405 (Method Not Allowed)
The server has not found anything matching the Request-URI

Use cases:
* operation is not allowed/supported

# 406 (Not Acceptable)
The resource identified by the request is only capable of generating response entities which have content characteristics not acceptable according to the accept headers sent in the request.

Use cases:
* when the API is not able to generate any of the client's preferred media types as indicated by the Accept header
* when the API is not able to generate any of the client's preferred language representation as indicated by the Accept-Language header

The request MUST include the Accept header (e.g., Accept: application/json)
The request MAY include the Accept-Language header (e.g., Accept-Language: fr-BE)

# :x: 409 (Conflict)
Tells the client that they tried to put the REST API's resources into an impossible or inconsistent state

:x: You SHOULD NOT use this status code. It MAY make sense for business exceptions but we've chosen to use 422 instead.

# :x: 410 (Gone)
The requested resource is no longer available at the server and no forwarding address is known. This condition is expected to be considered permanent.

:x: You SHOULD NOT use this status code because the interface changes require the creation of new version of the API rather than the usage of this approach. For example, if v1 of your API provided a _cars_ collection resource, v2 could remove that resource or give it another name. If you still provide v1 along v2, then existing clients won't notice, there's thus no need for HTTP 410.

# 412 (Precondition Failed)
Indicates that the client specified one or more preconditions in its request headers, effectively telling the REST API to carry out its request only if certain conditions were met. This error indicates that those conditions were not met, so instead of carrying out the request, the API sends this status code.

Use cases:
* conditional requests

# 415 (Unsupported Media Type)
Indicates that the API is not able to process the client's supplied media type as indicated by the Content-Type request header

Use cases:
* unable to process the client's supplied media type

# :x: 416 (Request Range Not Satisfiable)
A server SHOULD return a response with this status code if a request included a Range request-header field (see [section 14.35 in RFC 2616](https://www.ietf.org/rfc/rfc2616.txt)), and none of the range-specifier values in this field overlap the current extent of the selected resource, and the request did not include an If-Range request-header field.

:x: You MUST NOT use this as we will not use Range headers. Take a look at the pagination section for more details.

# 422 (Unprocessable Entity)
The 422 status code means the server understands the content type of the request entity, and the syntax of the request is correct but refuses to process the contained instruction.

Use cases:
* business exceptions
  * received data is not acceptable (e.g., semantic issues)
  * business rules violations would occur if the request was accepted

Reference: http://www.bennadel.com/blog/2434-http-status-codes-for-invalid-data-400-vs-422.htm