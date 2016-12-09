# Target
To retrieve a single item, you MUST issue a GET request against the resource (e.g., .../v1/employees/123 to retrieve employee 123).

# Rules for the client
* SHOULD define the Accept header to specify the list of media types it supports/prefers

# Rules for the server
* SHOULD return HTTP 200 if all went well
* SHOULD set the Content-Type header
* SHOULD return a subset of the items (take a look at the pagination section for precise guidelines and examples)
* SHOULD return metadata (about pagination and sorting, filtering, etags, ...)
  * refer to the corresponding sections
* SHOULD return a compact style if one is defined rather than the full representation
  * in that case, the identifier MUST be included (uuid) to allow the client to find where to get the full representation