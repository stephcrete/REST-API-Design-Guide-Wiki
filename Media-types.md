# About
[Media types](https://en.wikipedia.org/wiki/Media_type) (also known as MIME types or content types) play an important role for HTTP and RESTful APIs.

Media types provide a way for clients to specify the data format they expect and for the server to state the data format that they return.

A media type is composed of
* a type
* a subtype
* optional parameters.

Some examples:
* text/html
* application/json
* application/xml
* application/x-www-form-urlencoded

All media types are registered with the IANA; the official list is there: http://www.iana.org/assignments/media-types/media-types.xhtml

Most of the time with RESTful APIs, you'll use the "application/json" media type as that's the standard IANA registered media type for JSON.

# Vendor-specific media types
Media types use the subtype prefix "vnd" to indicate that they are owned or controlled by a "vendor". Vendor-specific media types convey a clear description of a message's content to the programs that understand their meaning.

You MAY consider using vendor-specific media types to convey more clearly the type of content that is associated with a request or response (i.e., give not only information about the content but also about its semantics). Although, we do not recommend that (yet).

Example with a request:
```
POST .../v1/employees
Content-Type: vnd.mycompany-employee-v1+json
{
    "firstName": "Dubois",
    "lastName": "Sebastien",
    ...
}
```

If the application knows that content type, it can parse it much more efficiently.