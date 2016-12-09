# Target
To retrieve a single item, you MUST issue a GET request against a single item (e.g., .../v1/employees/123 to retrieve employee 123).

# Rules for the client
* SHOULD define the Accept header to specify the list of media types it supports/prefers

# Rules for the server
* MUST return HTTP 404 (Not found) if the user was not found
* SHOULD return HTTP 200 (OK) if the user was found
* SHOULD set the Last-Modified header to the last modification time stamp
* SHOULD set the Content-Type header
* SHOULD set the ETag header to the current ETag value