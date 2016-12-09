# Warning
⚠️ You SHOULD NOT implement bulk deletion unless you really know what you're doing and why.

# Types
There are multiple types of bulk operations that we consider here:
* bulk creation
* bulk update
* bulk operation with both creates and updates

For all of these, the idea is that a POST is performed against a collection resource, with a collection of items (see example in the next section).

For each item, the REST API must identify whether it should be created or updated.

The distinction is easily made because:
* for a creation, the provided item does not have an ID
* for an update, the provided item does have an ID

# Delete
⚠️ Bulk delete SHOULD NOT be supported/used unless for specific use cases.

Only implement this if you **ABSOLUTELY** require it. Bulk deletion is a dangerous operation

Rules for the server:
* SHOULD return HTTP 204 (No Content) if the delete operation is immediate
* SHOULD return HTTP 202 (Accepted) if the delete operation is NOT immediate