# Rules
If you need to add caching and conditional requests support, then you SHOULD:
* add the Cache-Control header with appropriate configuration depending on your use case (see next section)
  * fine-grained control over caching of resources
* add the Last-Modified header
  * the Last-Modified header value should be a time stamp corresponding to the last known time when the resource was modified
* add the ETag header
  * hash of the resource
* support conditional requests
  * needed for optimistic concurrency control
  * improves performance by skipping execution if preconditions are not met