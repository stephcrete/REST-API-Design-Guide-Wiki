```
GET /dogs?sort=title+DESC,author+ASC
 
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
        "sortedBy": [
            {
                "field": "title",
                "order": "DESC"
            },
            {
                "field": "author",
                "order": "ASC"
            }
        ]
        ...
    }
}
```