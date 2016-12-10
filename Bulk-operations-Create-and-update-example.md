```
POST /employees
{
    "items": [
        {
            "uuid": "123",
            "location": "China",
            ...
        },
        {
            "firstName": "foo",
            "lastName": "bar",
            ...
        },
        ...
    ],
    ...
}
```

Notice that:
* the first item in the provided collection has an ID --> update
* the second item in the provided collection does not have an ID -> create