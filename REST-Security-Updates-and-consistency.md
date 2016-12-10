When REST API clients send update requests against your API, you MUST perform some basic checks:
* if a client tries to update /<resource>/<uuid>, then the <uuid> in the URL MUST match the UUID provided in the updated resource representation
  * inconsistency means either that the client was badly implemented, or that the client is malicious
  * :white_check_mark: this check is handled by the CORE framework if you use the provided facilities
* the ETag value passed by REST API clients for updates MUST be opaque and protected against manipulation by the clients; this is important because otherwise clients could manipulate update requests to update data using stale data
  * :white_check_mark: this check is handled by the CORE framework if you use the provided facilities
    * the ETag values are calculated by the framework based on
      * the time stamp at noon of the current day
      * the last modification time stamp of the entity
    * the ETag is then hashed and encrypted using a key known only by the back-end application
      * this ensures that clients cannot forge ETag values