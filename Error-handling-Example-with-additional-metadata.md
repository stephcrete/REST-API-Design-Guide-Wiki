The following example shows how to provide additional metadata:

```
HTTP/1.1 400
{
    "type": "https://api.demo.nbb.be/v1/errors/validation",
    "title": "Validation errors",
    "titleKey": "errors.validation",
    "metadata": {
        "validationHash": "f7fbba6e0636f890e56fbbf3283e524c6fa3204ae298382d624741d0dc6638326e282c41be5e4254d8820772c5518a2c5a8c0c7f7eda19594a7eb539453e1ed7",
    },
    "errors": [
        {
            "type": "https://api.demo.nbb.be/v1/errors/validation-user-invalid",
            "title": "Invalid user information",
            "titleKey": "errors.validation.user.invalid",
            "detail": "The username does not respect the minimal length",
            "detailKey": "errors.validation.user.invalid.username.too.short",
            "fields": [
                "username"
            ],
            "identifier": "9335d74d-2649-4eec-a272-ab2803e25a40",
            "metadata": {
                "minimalUsernameLength": 8
            }
        }
    ]
}
```