```
POST /employees-bulk
{
    "items": [
        {
            "uuid": "123",
            "location": "China",
            ...
        },
        {
            "firstName": "foo",
            "lastName": "bar",
            ...
        },
        ...
    ],
    metadata: {
        etags: {
            "<uuid>": "<etag>",
            ..
        }
    }
    ...
}
```

Notice that:
* the first item in the provided collection has an ID --> update
* the second item in the provided collection does not have an ID -> create
* there's an entry in the ETags map for each update (if and only if the ETags are mandatory for the resource to update)
  * for items to create there's indeed no ETag to provide