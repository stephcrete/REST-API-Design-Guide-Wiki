# 200 (Ok)
Use cases:
* update/retrieve data
* bulk creation
* bulk update

:x: You MUST NOT use 200 OK for everything!

# 201 (Created)
Should be used after a successful POST creation request.

The response should include the _Location_ header with a link towards the location of the created resource.

Use cases:
* create resources (single items)

# 202 (Accepted)
Means that the request has been accepted for processing but the processing has NOT been completed.

The response should include the _Location_ header with a link towards the location where the final response can be polled & later obtained.

Use cases:
* asynchronous tasks (e.g., report generation)
* batch processing
* delete data
  * you SHOULD use this if the delete operation is NOT immediate. Your client needs to be able to poll for the final result

# 204 (No content)
Means that the requested operation succeeded but that no content is returned.

Use cases:
* delete data
  * you SHOULD use this if the delete operation is immediate

:x: You MUST NOT use this for out of bounds errors with pagination (check out the pagination section for details).

# :x: 206 (Partial content)
Means that the server has fulfilled the _partial_ GET request for the resource.

The request MUST have included a _Range_ header indicating the desired range, and MAY have included an _If-Range_ header to make the request conditional.

:x: You MUST NOT use this as we will not use Range headers in our APIs. Take a look at the pagination section for more details.