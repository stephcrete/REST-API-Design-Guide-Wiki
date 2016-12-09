# About
For front-end consumption,your API MUST support JSON. If your API is to be consumed by other types of clients, then you should consider supporting multiple formats (e.g., XML).

JSON has preference because of its:
* ubiquity
* simplicity
* readability
* efficiency (lightweight)
* flexibility

# Selecting the format
Clients SHOULD be able to specify their preferred format using the Accept HTTP header which HTTP leverages for content negociation.

The Accept header lists the media types that the client is willing to process (comma-separated list).

Example:
```

GET /dogs/1234
Accept: application/json
 
HTTP/1.1 200 OK
{
    "name": "foo",
    ...
}
 
 
GET /dogs/1234
Accept: application/xml
 
HTTP/1.1 200 OK
 
<dog>
    <name>foo</name>
    ...
</dog>
```

> Both the client and server can define their preference for each media type!

Example:
```
GET .../dogs/1234
Accept: application/xml;q=0.9,application/json;q=0.1
```

# Selecting the format via the URL
Your API MAY also support defining the format in the URL by specifying extensions. For example:

```
GET .../dogs/1234.xml
```

The above notation is useful for easily interacting with the API with a simple client (e.g., a Web browser).