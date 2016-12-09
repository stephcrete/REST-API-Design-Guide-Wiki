If a relation of a resource is commonly requested alongside the resource, you MAY embed the relation's representation and avoid the second hit to the API:

```
GET .../v1/users/1
Accept: application/json
  
HTTP/1.1 200 OK
...
{
    "uuid": "<uuid>",
    ...,
    "contract": {
        uuid": "40525ee6-a49d-48b1-9481-bff40b5781df",
        "signedBy": "...",
        "timestamp": "...",
        ...
    }
}
```

> You can apply expansion to all relationship types. You can even combine this approach with filtering to give fine control to your API clients.