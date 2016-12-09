# 400 (Bad request)
The request could not be understood by the server due to malformed syntax.
The client SHOULD NOT repeat the request without modifications.

Use cases:
* Invalid/incomplete request
* Return multiple client errors at once (cfr error handling section)

# 401 (Unauthorized)
The request requires user authentication.
The client MAY repeat the request with a suitable Authorization header field.

Use cases:
* Client not authenticated

# 403 (Forbidden)
The client is authenticated but not authorized
An API client might be allowed to use some API resources but not some others; in that case he should receive a 403 error

Use cases:
* Client not authorized/allowed

# 404 (Not Found)
The server has not found anything matching the request URI

Use cases:
* Not found

# 405 (Method Not Allowed)
The server has not found anything matching the Request-URI

Use cases:
* Operation is not allowed/supported