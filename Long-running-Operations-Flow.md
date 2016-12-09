For long running operations, the approach to follow is to directly reply to the request with an acknowledgement and then let the client do polling to check the status of their request.

Flow:
* Request
* Response
  * 202 Accepted: acknowledgement
  * Location: `.../foo/bar` (i.e., where to check the status/get the final response)
* Request `.../foo/bar`
 * Response
   * 202 Accepted: current status of the request (as long as it isn't completed yet)
   * OR 200 OK with the data (if any)