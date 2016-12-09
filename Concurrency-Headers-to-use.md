To support optimistic concurrency control, your API SHOULD return the following HTTP headers along with all resource representations (for single items):
* [ETag](https://en.wikipedia.org/wiki/HTTP_ETag)
* Last-Modified

For collections, the ETag values will be provided in the metadata (see later sections).

An ETag is an opaque identifier assigned to a specific version of a resource found at a given URL.

If the resource representation at that URL ever changes, a new ETag MUST be assigned by your API

The ETag value MUST be a collision-resistant hash of the resource's content

The ETag MAY for example be a SHA-512 hash of the representation or anything else that makes sense. You could also choose to combine the UUID of an entity with its last update timestamp and make a hash of that...

When the client updates a resource, it MUST provide an up to date ETag value in the _If-Match_ HTTP header in his request (see conditional requests section). The server can then compare that ETag with the ETag of the latest version of the resources.

If both ETag values match, then it means that the client has the latest/up to date version, thus the update can go through.

If the client has a different ETag value (i.e., outdated or invalid), then it means that it tries to update stale data. In that case, a 412 (Precondition Failed) error SHOULD be returned.