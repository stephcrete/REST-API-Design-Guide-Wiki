There are over 70 HTTP status codes. However we do not need to use them all. We must avoid using too few or using too many. On one end, the API will lose clarity and on the other, developers will have to go to Wikipedia all the time to find what statuses mean.

To give you an idea of how large API providers use HTTP status codes
* Google GData API: 10 different codes
  * 200 201 304 400 401 403 404 409 410 500
* Netflix: 9 different codes
  * 200 201 304 400 401 403 404 412 500

There are really only 4 possible outcomes in the interaction between an app and an API:
* Everything worked (success): 2xx codes
* No problem occurred but further action is required by the client (redirection): 3xx codes
* The application (client) did something wrong (client error): 4xx codes
* The API did something wrong (server error): 5xx codes