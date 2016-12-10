A first approach for filtering is to define a "style", which is just a label that you put on a set of fields. By requesting some resource with a given style, API users can get the fields associated with that style.

Defining styles SHOULD be the default approach.

Here's an example without requesting a specific style:
```
GET /users/<uuid>
 
200 OK
{
    "uuid": "<uuid>",
    "firstName": "foo",
    "lastName": "bar",
    "street": "...",
    "city": "...",
    "postCode": "1000",
    "dateOfBirth": "...",
    ...
}
```

Now, assuming that the API provides a "compact" style for example, the request/response could look like:

```
GET /users/<uuid>?style=compact
 
200 OK
{
    "uuid": "<uuid>",
    "firstName": "foo",
    "lastName": "bar"
}
```

> Notice that the "uuid" is provided to allow the client to know where to find the full representation.

This approach works well if you know in advance how your API will be used and which exact fields are necessary. The drawback is that your client can only require those profiles, which might be either too much or not enough for them.