Null values SHOULD be included in the responses and not omitted. Omitting fields that clients expect or might expect will cause surprises.

```
GET /user/1
Accept: application/json
HTTP/1.1 200 OK
{
    "firstName": "Sebastien",
    "lastName": "Dubois",
    "birthDate": null
}
```