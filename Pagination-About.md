#About
Most of the time for queries on collection resources (e.g., /users), your whole data set will be too large to return everything at once to the client; that's where pagination comes in.

Pagination is critically important for the performance of both the clients and servers, but also for customer satisfaction: reduce costs, improve performance, etc.

# Summary vs detailed representations
When a user fetches a collection resource, he SHOULD:
* get a small subset of the whole data set (cfr previous section about pagination)
  * ⚠️ you MUST respect the rules defined for pagination
* get a summary representation of each resource
* get the id (UUID) of each element in the response so that he knows where to find the detailed representation

This means that, when fetching a collection resource (e.g., /users), the client of an API MUST get a limited number of results (e.g., max 10) and a subset of the attributes for that resource.

The summary representation of an item in the returned collection SHOULD contain the id of the element so that the client is able to find the detailed representation.

Example:

```
GET /users
 
HTTP/1.1 200 OK
{
    "items": [
        {
            "uuid": "<uuid>",
            "firstName": "foo",
            "lastName": "bar"
        },
        {
            "uuid": "<uuid>",
            "firstName": "john",
            "lastName": "doe"
        },
        ...
    ],
    ...
}
```