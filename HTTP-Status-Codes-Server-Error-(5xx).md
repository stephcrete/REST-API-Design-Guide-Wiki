# Warning
For security reasons, when the server encounters an error that isn't related to the client request (i.e., not the fault of the client), it should not provide ANY details to the client. You never want to expose the internals of your server side to your API clients.

# 500 (Internal Server Error)
The server encountered an unexpected condition which prevented it from fulfilling the request

Use cases:
* generic server side error

:x: The response MUST NOT include any details in the response body

# 503 (Service Unavailable)
The server is currently unable to handle the request due to a temporary overloading or maintenance of the server

Use cases:
* API is down

:x: The response MUST NOT include any details in the response body