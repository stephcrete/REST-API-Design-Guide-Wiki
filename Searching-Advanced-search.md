# About
When you have too many search criteria, you might reach maximal URL length limitations. In that case, you should use the request body instead of URI query parameters. But do it only if you hit the limits!

In some cases, you might require support for more advanced operations (e.g., comparisons, bigger than, lower than, ...); for that situation, we recommend using FIQL.

# Request body
For cases where the search operation contains too many parameters, you SHOULD use the request body and pass a payload including all the search parameters.

It should return the same response as when applying local search. Example:
```
POST .../v1/employees/search
```

# FIQL
For more advanced search scenarios, you SHOULD take a look at FIQL: https://tools.ietf.org/html/draft-nottingham-atompub-fiql-00 and libraries that support it.
 
{
    "firstName": "foo",
    ...
}
```

# Vectorized requests
Sometimes, you might need to pass a set of values/scopes for a query. In that case you can pass a query parameter with an array of values separated by "," or ";" for a query parameter (i.e., search on a set of specific elements)

Example:
```
GET .../v1/employees?employer=id1;id2;id3
```

Related: https://api.stackexchange.com/docs/vectors