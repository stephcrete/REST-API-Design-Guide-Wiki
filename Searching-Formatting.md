If users want a different format (e.g., XML instead of JSON) for the search result, they SHOULD be able to use the Accept header (see data formats section).
```
GET /search?q=foo+bar
Accept: application/xml
```

If your API supports it, then they could add the extension in the URL:
```
GET /search.xml?q=foo+bar
```