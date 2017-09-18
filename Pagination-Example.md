```
GET /dogs?limit=25&offset=50
 
200 OK
{
    "items": [
        {
            "uuid": "<uuid>",
            "name": "...",
            ...
        },
        {
            ...
        },
        ...
    ],
    "metadata": {
    ...
        "pagination": {
            "offset": 50,
            "limit": 25,
            "previousOffset": 25,
            "nextOffset": 75,
            "currentPage": 3,
            "pageCount": 40,
            "totalCount": 1000
        },
    ...
        "etags": {
            "<uuid>": "<etag>",
            ...
        },
    ...
        "sortedBy": [
            ...
        ],
    ...
        "warnings": [
            ...
        ],
    ...
        "custom": {
            "anythingYouWant": ...
            ....
        }
    }
}
```

| offset | limit | totalCount | previousOffset | nextOffset | currentPage | pageCount |
| --- | --- | --- | --- | --- | --- | --- |
| 0 | 10 | 53 | null | 10 | 1 | 6 |
| 10 | 10 | 53 | 0 | 20 | 2 | 6 |
| 13 | 10 | 53 | 3 | 23 | 2 | 6 |
| 20 | 10 | 53 | 10 | 30 | 3 | 6 |
| 30 | 10 | 53 | 20 | 40 | 4 | 6 |
| 40 | 10 | 53 | 30 | 50 | 5 | 6 |
| 50 | 10 | 53 | 40 | null | 6 | 6 |

```
> Handy formula: offset = (page - 1) * limit +1