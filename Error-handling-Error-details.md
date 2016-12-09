# General rules
When an error occurs that you consider to be due to the client (i.e., 4xx range), your API SHOULD provide error details in the response body to help the client know what it did wrong and what to fix. Consider that the front-end developer might not be you, thus be friendly and try to provide helpful messages and error details.

When returning error details, you SHOULD set the Content-Language header to the code corresponding to the language the messages you return are in (format: RFC5646: https://tools.ietf.org/html/rfc5646).

Your API MAY choose to stop processing as soon as a problem is encountered or it MAY continue processing multiple attributes and then return multiple validation problems in a single response. We heavily recommend to regroup validation errors together whenever possible in order to avoid ping-pong (very BAD for user experience).

If you return multiple errors at once, you SHOULD use 400 as return code, and provide a specific error code in each error object.

# Security rules
Things to avoid at all costs (for security reasons but not only):
* you MUST NEVER send stack traces to API clients
* you MUST NEVER send information about software and software versions as that could ease the work of an attacker