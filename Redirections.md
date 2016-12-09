# About
If, for whichever reason, your API needs to move, either temporarily or permanently and you don't want to break existing clients, then you should redirect them automatically.

Your API clients should assume that any request may result in a redirection. Receiving an HTTP redirection is not an error and clients should follow the redirect.

# Rules
Redirect responses SHOULD always provide a Location header field containing the URI of the resource to which the client should repeat the requests.

# Permanent redirections
When a redirection is permanent, you should return a 301 status code. It means that the URI used by the client make the request has been superseded by the one specified in the Location header field of the response. This and all future requests should be directed to the new URI.

# Temporary redirections
When a redirection is temporary, you SHOULD return a 303 or 307 status code (see the status codes table for more guidance).