The other approach is to provide a way for your clients to specify exactly which fields they want. This approach is very efficient because your clients can get exactly what they need.

The main drawback is that your server must be able to construct objects dynamically depending on the requests that come in and this might force you to go below the OO level and to generate the correct representation on the fly (i.e., without much help of the serialization mechanism).

You SHOULD define fields to include as follows:

```
GET /dogs/1?fields=name,color,location
 
200 OK
{
    "uuid": "<uuid>",
    "name": "Beethoven",
    "color": "...",
    "location": "Neighbour's garden"
}
```

> For collection resources, your API should be intelligent enough and infer that the fields listed correspond to entity fields and NOT to the representation.
That is to say: your API SHOULD NOT require clients to specify fields like: "items.id" just to state that they want the id field which will be within an object in the "items" array returned by the collection resource; instead, your API should accept "id" as field value and filter intelligently.