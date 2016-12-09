# Target
To retrieve a collection, you MUST issue a GET request against a collection (e.g., .../v1/employees to retrieve a subset of the employees.

# Rules for the client
* SHOULD define the Accept header to specify the list of media types it supports/prefers

# Rules for the server
* SHOULD return HTTP 200 if all went well
* SHOULD set the Content-Type header
* SHOULD return a **subset of the items** (take a look at the pagination section for precise guidelines and examples)
* SHOULD return metadata (about pagination and sorting, filtering, etags, ...)
refer to the corresponding sections
* SHOULD return a compact style if one is defined rather than the full representation
in that case, the identifier MUST be included (uuid) to allow the client to find where to get the full representation

# Pagination
Collections can be very large. For this reason, all collection responses SHOULD be paginated. Refer to the pagination section to see how this works.

⚠️ AVOID at all costs requesting many elements in a collection. Prefer issuing smaller, more targeted requests in order to limit the number of resources to retrieve at once. This is important for performance, but also for client costs & resource usage (e.g., bandwidth, memory consumption, page rendering speed, etc).