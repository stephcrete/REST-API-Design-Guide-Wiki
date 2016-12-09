# Delete types
When you perform a delete operation, the operation may be immediate or not (e.g., it could require some post processing).

# Target
To delete a single item you MUST issue a DELETE request against the single item (e.g., .../v1/employees/123 to delete employee 123).

# Rules for the client
* MAY provide the ETag value in order to state that it should only be deleted IF the ETag is the correct one (see concurrency section for details)

# Rules for the server
* SHOULD return HTTP 204 (No Content) if the deletion succeeded
* SHOULD return HTTP 202 (Accepted) if the deletion is accepted but is not immediate
  * in that case the _Location_ header should provide a link to where the client can poll for the final result of the operation
* MUST return 404 if the resource was not found
