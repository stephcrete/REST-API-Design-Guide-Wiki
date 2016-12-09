# Update types
There are two main types of updates to consider:
* partial: SHOULD be done using POST
  * in this case only a subset of the properties MUST be provided
* full: MUST be done using PUT
  * in this case ALL resource properties MUST be provided (for idempotency)

# Target
To update a single item you SHOULD issue a POST or PUT request against the single item (e.g., .../v1/employees/123 to update employee 123).

# Rules for the client
* SHOULD use POST for partial updates
* MAY use PUT for full updates (idempotent), see PUT
* MUST define the Content-Type header to specify the media type of the request body
* MUST set the If-Match header with the ETag value known by the client (see concurrency section for details)
  * makes it a conditional request

# Rules for the server 
* MUST return
  * Success: HTTP 200 (OK)
    * or HTTP 204 (No content) if not returning content in the body
  * Failure due to invalid ETag: 412 (Precondition Failed)
* SHOULD set the Last-Modified header to the last modification time stamp
* SHOULD set the ETag header to the current ETag value
* MAY consider using vendor-specific media types to give semantics about the data.