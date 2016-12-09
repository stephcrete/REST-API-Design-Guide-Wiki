The following example shows how to provide parameter values:

```
HTTP/1.1 400
{
    "type": "https://api.demo.nbb.be/v1/errors/validation",
    "title": "Validation errors",
    "titleKey": "errors.validation",
    "errors": [
        {
            "type": "https://api.demo.nbb.be/v1/errors/validation-user-invalid",
            "title": "Invalid user information",
            "titleKey": "errors.validation.user.invalid",
            "detail": "The start date {0} must be after the current date {1}",
            "detailKey": "errors.validation.user.invalid.start.date.before.current.date",
            "detailKeyParameters": [
                "2015-12-01",
                "2015-12-05"
            ]
            "fields": [
                "start-date"
            ],
            "identifier": "9335d74d-2649-4eec-a272-ab2803e25a40"
        }
    ]
}
```