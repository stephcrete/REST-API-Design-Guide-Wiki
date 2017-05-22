# General rules
When an error occurs that you consider to be due to the client (i.e., 4xx range), your API SHOULD provide error details in the response body to help the client know what it did wrong and what to fix. Consider that the front-end developer might not be you, thus be friendly and try to provide helpful messages and error details.

When returning error details, you SHOULD set the Content-Language header to the code corresponding to the language the messages you return are in (format: RFC5646: https://tools.ietf.org/html/rfc5646).

Your API MAY choose to stop processing as soon as a problem is encountered or it MAY continue processing multiple attributes and then return multiple validation problems in a single response. We heavily recommend to regroup validation errors together whenever possible in order to avoid ping-pong (very BAD for user experience).

If you return multiple errors at once, you SHOULD use 400 as return code, and provide a specific error code in each error object.

# Security rules
Things to avoid at all costs (for security reasons but not only):
* you MUST NEVER send stack traces to API clients
* you MUST NEVER send information about software and software versions as that could ease the work of an attacker

# Representation
The error representation design is based on:
  * the "Problem Details for HTTP APIs" RFC 7807 proposed by M. Nottingham: https://tools.ietf.org/html/rfc7807
  * the JSON API specification: http://jsonapi.org/format/#errors. We inspired our errors representation off of their concepts
  * the OData specification: http://docs.oasis-open.org/odata/odata-json-format/v4.0/os/odata-json-format-v4.0-os.html#_Toc372793091
  * GitHub's API: https://developer.github.com/v3/#client-errors

Whether your API returns one error or multiple ones, you SHOULD return a JSON object containing at least an attribue called "errors", containing an array of errors objects:

```
{
    "errors": [
        ...
    ]
}
```

You MUST return at least one error object in the "errors" array. Each error object will provide details regarding a specific error.

# Additional fields
In addition to the "errors" array, the JSON object that your API returns SHOULD contain additional attributes to provide context:
* type: absolute URI that identifies the problem type
  * when dereferenced (i.e., accessed directly), it SHOULD provide human-readable documentation for the problem type (e.g., an HTML page)
  * ⚠️ target: DEVELOPERS, not application end users
* title: short human-readable summary of the problem type
  * ⚠️ target: DEVELOPERS, not application end users
* titleKey: a message key for the summary of the problem type
  * SHOULD be language-independent
  * SHOULD be translated by the client (optionally using other APIs)
  * the key SHOULD be human-readable (i.e., prefer SOME.ERROR.CODE rather than 0x0000007e)
* (optional) titleKeyParameters: array of strings, each string being the value of a parameter in the titleKey
  * the titleKey should contain placeholders with numeric values, for example {0}, {1}, ... 
  * ⚠️ the titleKeyParameters values MUST be provided in the correct order
    * assuming that the order is correct, the first message MUST be interpreted as the {0} in the titleKey
* (optional) instance: identifies the specific occurrence of the problem
  * this SHOULD be a UUID
  * you must think of the instance as a correlation identifier
  * the goal of that identifier is to help you correlate activities on the client side and on the server side
  * when an error is detected on the server side, you should
    * generate a UUID
    * add it to all relevant log/audit statements
    * provide it in the instance field described here
* (optional) timestamp: provides a timestamp for the error message
* (optional) metadata: provides additional error metadata. Metadata MUST be an object but MAY contain anything you want

You SHOULD see the above properties as more generic error information (e.g., validation error, business exception, etc). Error objects are those responsible for passing specific error information.

You MAY add any other relevant information. Just be careful not to expose security-sensitive information when doing so.

# Error objects
Each object placed in the errors array MAY contain the attributes listed in the previous section (i.e., type, title, titleKey, titleKeyParameters, instance, timestamp).

In addition, it SHOULD also include the following attributes:
* detail: human-readable explanation specific to this occurrence of the problem
  * ⚠️ target: DEVELOPERS, not application end users
* detailKey: a message key for the detailed explanation specific to this occurrence of the problem
  * SHOULD be language-independent
  * SHOULD be translated by the client (optionally using other APIs)
  * the key SHOULD be human-readable (i.e., prefer SOME.ERROR.CODE rather than 0x0000007e)
* (optional) detailKeyParameters: array of strings, each string being the value of a parameter in the detailKey
  * the detailKey MAY contain placeholders with numeric values, for example {0}, {1}, ...  
  * ⚠️ the detailKeyParameters values MUST be provided in the correct order
    * assuming that the order is correct, the first message MUST be interpreted as the {0} in the detailKey
* (optional) fields: array of strings, each string being the identifier of a field related to this specific error
  * the fields array provides a means to communicate clearly that an error relates to one or more fields
  * the fields array SHOULD help API clients to identify precisely where the error lies. It is your responsibility to provide a relevant set of identifiers (e.g., username, user.username, ...)
  * if there is a clear link between an error and specific field(s) then you SHOULD include the fields array
* (optional) status: the HTTP status code for this specific error
  * you MAY use then when you return multiple errors
* (optional) index: an integer value (zero-based) corresponding to the position in the source collection
  * this is useful for bulk operations where the error needs to be mapped back to a specific item in the source collection that was given
* (optional) metadata: provides additional error metadata. Metadata MUST be an object but MAY contain anything you want
Error handling Example with additional metadata

You MAY add any other relevant information. Just be careful not to expose security-sensitive information when doing so.

## Error keys/codes
Each error should have a unique "key/code" (e.g., detailKey or combination of titleKey and detailKey) as it will allow your API clients to add more intelligence. If you document all error "keys/codes" in your API specifications, then clients may check for those specific errors and build a better user experience based on those.

## Metadata
As can be see above, a "metadata" object can be added to both the general information part of the error payload and the error details.

This should be seen as a way to provide additional information in error payloads.
