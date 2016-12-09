# FIQL
For more advanced search functionality, you SHOULD take a look at FIQL: https://tools.ietf.org/html/draft-nottingham-atompub-fiql-00 and libraries that support it.

# JSON Body
An alternative for cases where the search combines many different fields is to pass a JSON body payload with all the search parameters.

It should return the same response as when applying local search:
```
POST .../v1/employees/search
 
{
    "firstName": "foo",
    ...
}
```