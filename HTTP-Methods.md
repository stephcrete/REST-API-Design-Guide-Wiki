# About
You MUST map the correct HTTP methods to perform operations on your REST resources, otherwise you're not leveraging the HTTP protocol as you should with a REST API.

# Safe methods
Some HTTP methods SHOULD be SAFE (e.g., GET, HEAD, OPTIONS).

Safe operations are operations that SHOULD NOT change anything on the server side (i.e., those are READ-ONLY operations).

# Idempotent methods
Some HTTP methods SHOULD be IDEMPOTENT (e.g., GET, HEAD, DELETE, OPTIONS, PUT).

Idempotent operations...
* are operations that SHOULD produce the same result regardless of how many times they're executed.
* can modify resources, but those modifications should not change the resource representation. 

More information here: http://restcookbook.com/HTTP%20Methods/idempotency/

# GET
GET is used to retrieve resources

Characteristics:
* safe
* idempotent
* cacheable

# HEAD
HEAD is used to retrieve headers. Responses don't have a payload (body content).

Characteristics:
* safe
* idempotent
* cacheable
* can be issued against any resource to get the corresponding HTTP headers

# POST
POST is used to create and/or **partial** update resources.

Characteristics:
* NOT safe
* NOT idempotent

The response of a successful creation request
* MUST contain the _Location_ header to point to the location of the newly created resource
* MUST return 201 CREATED
* MAY include a representation of the created resource

The response of a successful update request
* MUST return 200 OK

# PATCH
PATCH MAY be used for **partial** updates. See [RFC 5789](https://tools.ietf.org/html/rfc5789)

Characteristics:
* NOT safe
* NOT idempotent

# DELETE
DELETE is used to... delete resources.

Characteristics
* NOT safe
* idempotent
* MAY return a representation or another payload
* the resource doesn't have to be removed immediately. A DELETE operation on a resource MAY be delayed or take time to be performed

# OPTIONS
OPTIONS is used to get the allowed communication options for the targeted resource

Characteristics:
* safe
* idempotent

MUST return a Allow header with allowed HTTP methods. Example:

```
OPTIONS /users
 
HTTP/1.1 200 OK
Allow: OPTIONS, GET, POST
...
```

# PUT
PUT is used to perform **full** updates.

Characteristics:
* NOT safe
* idempotent

Rules:
* you SHOULD NOT use PUT for creation; instead we recommend using POST in most cases
* :x: you MUST NOT use PUT for partial updates (partial updates are NOT idempotent)