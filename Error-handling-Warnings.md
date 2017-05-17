# About
In most applications you need to implement validation logic (whether for business or security reasons). Validation rules most often trigger errors (e.g., 4xx code where the client has provided invalid/incomplete input), but sometimes validations also result in warnings.

For example, when creating a new _contact_ through an address book API, the API might notice that no e-mail address has been provided by the client. Let's assume that it is not mandatory when creating a new contact but that it will prevent the API client from later using the "Send mail to" feature for that specific client. In this example, 
(i.e., the creation request is valid), the response should be 201 since the creation was successful, but warnings should be returned in the response to let the clients know.

# Rules
* Warnings MAY NOT be "blocking" and/or cause your API to return a 4xx code to your client.
* Warnings MAY NOT expose sensitive information (e.g., detailed validation rules not supposed to be known to the outside world)

# User experience
Warnings are mostly useful for improving the user experience. For this reason alone, we believe that it is important for your API to provide those to your API clients.

The reason why is that, based on warnings, your clients can quickly correct information they have provided or directly perform additional required actions easily.

# Design guidance

## Representation
The base design that we recommend is to expose warnings for specific resources as part of their representations. That way, API clients can model these and be aware that warnings may be returned along with the rest of the representation.

When doing so, we **heavily** recommend to isolate warnings in a _metadata_ object so as to make it clear that warnings are metadata and not part of the actual resource.

For example:
```
{
    uuid: "...",
    name: "...",
    ...
    metadata: {
        warnings: [
            <whatever you want>
        ]
    }
}
```
With the above structure, you make it very clear that warnings are not PART of the actual data but are metadata.

## When to include/exclude warnings
When warnings are raised subsequently to a CREATE operation, they SHOULD be returned directly. This behavior should not be optional. We assume that providing the warnings upon creation makes sense in most cases.

When API clients GET existing resources, they MAY decide to exclude the metadata. It is up to you to decide what should be the default behavior for your application/specific resource, but you SHOULD definitely consider adding support for excluding warnings (or even the whole metadata object); cfr filtering by excludes.

This may be seen as an optimization, but mobile usage scenarios and costly data plans should not be ignored when designing your API.

# Additional design considerations for warnings
As you may have noticed in the example above, we do not provide guidance regarding the structure or contents of the warnings. This is because it may vary a lot depending on the considered use cases.

As a rule of thumb though, we recommend including some unique "key/code" to your warnings as these allow your API clients to add more intelligence (and also easily add support for internationalization).

If you document all warning "keys/codes" in your API specifications, then clients may check for those specific warnings and build a better user experience based on those.

For example in the case where the e-mail was not defined for a contact, by receiving a warning such as "CONTACT_EMAIL_NOT_DEFINED", the API client could directly propose adding one.

# Dedicated resource for warnings
In some cases it might be useful to provide a dedicated resource where your API clients can check for the presence of warnings. For example a resource such as: .../contracts/<uuid>warnings).

This MAY be useful for cases where clients should be able to easily check for the presence of warnings without retrieving representations of the entities.

Another design approach for this would be to retrieve the representation and ONLY include metadata and/or warnings (e.g., using filtering by includes or styles), but this feels less intuitive and might also cause processing overhead depending on how the API is implemented.