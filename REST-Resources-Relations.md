Resources almost always have relations with other resources. Relations can be modeled in different ways using REST.

If a relation can only exist within another resource, then you SHOULD design it like this:
* GET /tickets/12/messages
  * retrieves list of messages for ticket #12
* GET /tickets/12/messages/5
  * retrieves message #5 for ticket #12
* POST /tickets/12/messages
  * creates a new message in ticket #12
* ...

If a relation can exist _independently_ of the resource, you MAY include an identifier for it in the output representation of the resource. The API client would then have to hit the relation's endpoint to get the representation:

```
GET .../v1/users/1
Accept: application/json
 
HTTP/1.1 200 OK
...
{
    "uuid": "<uuid>",
    ...,
    "contract": {
        "uuid": "40525ee6-a49d-48b1-9481-bff40b5781df"
    ...
}
```