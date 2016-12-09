# Rules
You SHOULD:
* return a 200 (ok) status code if all went well (same as for automic bulk operations)
* return a 4xx status code with errors (including the index property) if an error occurred with one or more of the elements
  * you SHOULD return errors for all items for which there was an issue, including the index property (see errors section below)
  * your API client MUST be aware of the non-atomic property of the resource and of the fact that any item not listed in the errors object returned was processed

# Partial failure and error metadata
You MAY combine the representation of errors and of collections to provide a complete response to your API client in case of a partial failure.

To be clear, let's assume that your client has POSTed 20 items and that there were errors for two of those. Your response look like this:
```
HTTP/1.1 400
{
    "items": [
        { ... }
    ],
    "errors": [
        { ... }
    ]
}
```

So basically:
* all items that were successfully created/updated can be provided in the items array
* all errors that were raised can be appended to the errors array