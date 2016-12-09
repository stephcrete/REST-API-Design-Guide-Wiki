```
HTTP/1.1 400
{
    "type": "https://api.demo.nbb.be/v1/errors/validation",
    "title": "Validation errors",
    "titleKey": "errors.validation",
    "errors": [
        {
            "type": "https://api.demo.nbb.be/v1/errors/user-invalid",
            "title": "Invalid user information",
            "titleKey": "errors.user.invalid",
            "detail": "The username is already in use",
            "detailKey": "errors.user.invalid.username.already.in.use",
            "fields": [
                "username"
            ],
            "instance": "4f4b3e6b-0707-4451-922f-53982ef83fdf"
        }
    ]
}
```

> Notice how the type, titleKey and detailKey define a namespace for errors of this specific type.
You SHOULD apply this consistently to avoid naming conflicts.