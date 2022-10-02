# About
We have considered two cases for internationalization:
* UI elements internationalization (ui labels, descriptions, ...)
* Business data with internationalization support

For the first use case, our goal is to provide a generic API that clients can interact with the get all UI-related translations at once, or specific messages. This is out of the scope of this REST API design guide.

⚠️ Here, we only provide design guidance for the second use case: internationalization of business data.

# Example
Suppose that an application manages products and that each product has a name and a description.

If the products support internationalization, then we could imagine that the name and description must be available in multiple languages in the data store. If you expose the products through a REST API, then either you provide all translations by default or you let the client choose the version he's interested in.

# Rules

## Clients should specify the languages they're interested in
Your API clients SHOULD provide the Accept-Language header with the language code(s) that they're interested in. For the accept header, the HTTP specification should be followed, thus the client MAY specify one or more languages/regions and give a quality to each (q=<quality>): https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html.

Language codes are described here: https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.10 and [RFC 1766](https://www.ietf.org/rfc/rfc1766.txt).

Example codes: fr-BE, nl-BE, fr, en-US, ...

## Specify the language of the response
Your API MUST include the Content-Language header to specify the language of the response.

Here's an example:
```
GET .../products/1234
Accept-Language: fr-BE
 
HTTP/1.1 200 OK
Content-Language: fr-BE
Content-Type: ...
{
    "product": "Valise en carton",
    "...": "..."
}
```

# Errors
Your API SHOULD return a 406 (Not Acceptable) error code if the client asks for a language code that is not supported by or not available for that specific resource/item. In that case, the response SHOULD include the list of supported/available language codes for that specific resource/item. For example:

```
GET .../products/1234
Accept-Language: fr-BE
 
HTTP/1.1 406 Not Acceptable
Accept-Language: nl-BE,en-US
```

# Wildcard
Your API clients MAY use a wildcard in the Accept-Language header '*' if they prefer to receive ANY representation rather than an error.

# Defining the languages in the URL
Your API SHOULD also support defining the language(s) in the URL by specifying a 'lang' parameter and give the same language codes as with the Accept-Language header; for example:

```
GET .../products/1234?lang=fr-BE
 
HTTP/1.1 200 OK
Content-Language: fr-BE
Content-Type: ...
 
{
    ...
}
```

You MAY also support the definition of multiple languages just like with the Accept-Language header.