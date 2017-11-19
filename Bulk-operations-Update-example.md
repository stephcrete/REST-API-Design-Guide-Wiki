```
POST /employees-bulk
{
    "items": [
        {
            "uuid": "123",
            "location": "China",
            ...
        },
        {
            ...
        },
        ...
    ],
    metadata: {
        etags: {
            "<uuid>": "<etag>",
            ..
        }
    }
    ...
}
```

The example above assumes that ETags are mandatory in this case, thus there's an entry in the ETags map for each item.