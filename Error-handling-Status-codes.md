The first indication that your API can give about errors is the HTTP status code. HTTP is the standard of the web and the HTTP status codes should be used appropriately, thus choose carefully!

First and foremost, decide if the error is a client or server problem:
* use a 4xx status code for client errors
  * the client should be able to fix the error by sending a different request
  * in this case, you should provide error details in the response body (see next section)
  * if you return a single error then you SHOULD return the most precise code possible
  * if you return multiple errors at once then you return a 400 status code and provide specific details in the error details (refer to the next sections)
* use a 5xx status code for server errors
  * the request has failed due to some internal server error
  * for server errors, it's best to **disclose as little information as possible as that could introduce security weaknesses**

⚠️ You MUST NOT return HTTP 200 (OK) or HTTP 400 (Bad Request) in all cases, that defeats the whole purpose of REST

Look at the list of HTTP status codes list and select an appropriate one depending on the error.

For example:
* entity not found: 404 Not Found
* entity already exists: 409 Conflict
* missing field: 400 Bad Request
* invalid input: 400 Bad Request
* validation exception: 422 Unprocessable Entity
* business exception: 422 Unprocessable Entity
* ...

For guidelines about the exact status codes to use depending on the situation, take a look at the HTTP status codes section.

