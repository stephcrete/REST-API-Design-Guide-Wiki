If a bulk operation fails, then there are different approaches based on the error type. As usual:
* if the error is on the server side, then an HTTP 500 without any details
* if the error is due to the client request, then a 4xx status code with error details
* ... (refer to the status codes table in this document

# Link an error with a specific item
In the errors representation, you MAY add the _index_ property (see errors section) to create a link between a specific item in the provided collection and a specific error returned for the bulk operation.

Example:
```
HTTP/1.1 400
{
    "errors": [
        {
            "index": 0,
            ...
        }
    ]
}
```

In the above example, we know that an error occurred with the first item that we gave in the POSTed collection.