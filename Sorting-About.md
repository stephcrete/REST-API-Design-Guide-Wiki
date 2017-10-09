You MAY implement support for sorting to let your API clients define the order in which the items in a response should be returned.

If you implement sorting then you SHOULD use the "sort" query string parameter with the following syntax:

```
sort=<field1>+<ASC|DESC>[,<field2>+<ASC|DESC>][, ...]
```

Example:
```
GET ...?sort=title+DESC
GET ...?sort=title+DESC,author+ASC
```
# Sections
* [[Sorting Metadata]]
* [[Sorting Example]]
