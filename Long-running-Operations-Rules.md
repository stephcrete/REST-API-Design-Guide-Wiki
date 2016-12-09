* the initial request SHOULD receive a 202 Accepted return code for acknowledgement (or an error code if something went wrong)
* the Location header SHOULD be added to the response
* polling requests SHOULD either receive
  * a 202 Accepted return code if the operation is not completed yet
    * the body MAY contain an object detailing the current state of the request (the design there is left for the application)
  * a 200 OK return code
    * the body MAY contain response data (if any)
    * the response MAY provide a Location header if results must be retrieved from somewhere else