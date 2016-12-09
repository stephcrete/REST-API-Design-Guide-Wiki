# About
If, for whichever reason, your API needs to move, either temporarily or permanently and you don't want to break existing clients, then you should redirect them automatically.

Your API clients should assume that any request may result in a redirection. Receiving an HTTP redirection is not an error and clients should follow the redirect.

# Rules
Redirect responses SHOULD always provide a Location header field containing the URI of the resource to which the client should repeat the requests.