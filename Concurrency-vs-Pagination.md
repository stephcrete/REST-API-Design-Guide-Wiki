# About
For paginated responses, concurrency specific metadata should be added to the "metadata" section, inside an "etags" object. That etags object will provide the mapping between the items in the "items" array and the ETag value for each.

With this, the client can directly get the ETag value for a specific item in the "items" array, using its UUID as key.

With that in hand, the client can then issue update requests for the specific items it wants.

# Metadata
Within the _metadata_ object of paginated responses, the following should be included:
* etags: an object containing UUID - ETag tuples (UUID as key)
  * the etags object provides the ETag values for all items present in the "items" array

This is necessary to avoid the "N+1" requests problem that we would have if a client wants to update multiple records while he has only the ETag for a collection and not the ETag value for all items in the paginated response.

> Note that we've used an object so that the lookup on the client-side can be done in constant time (i.e., O(1))

# Example
Check out the [[Pagination-Example]] page.