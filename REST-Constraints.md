* client server
  * the uniform interface provided by the REST Web Service separates clients from servers
* stateless
  * no client context is stored on the server between requests
  * each request contains all the information necessary to service the request
  * session state is held by the client
* cacheable
  * intermediaries can cache responses
  * responses must implicitly or explicitly define themselves as cacheable, or not, to prevent clients from reusing stale or inappropriate data
* layered
  * intermediary servers can be placed between the client and the server to improve scalability, provide load balancing, etc
* uniform interface
  * identification of resources
    * individual resources are identified in requests (for example using URIs for HTTP-based RESTful APIs)
    * everything has an id (:warning: expose [UUIDs](https://en.wikipedia.org/wiki/Universally_unique_identifier), not database identifiers!)
    * resources are conceptually separate from the representations that are returned to the client
      * the server may send data from its database as JSON or XML for example, none of which are the server's internal representation
  * manipulation of resources through these representations
    * when a client holds a representation of a resource, it has enough information to modify or delete the resource
  * self-descriptive message
    * each message includes enough information to describe how to process the message (e.g., which parser to invoke may be specified by an Internet media type (i.e., MIME type)
* hypermedia as the engine of application state (HATEOAS)
  * resource representations come along with hyperlinks making it easier for clients to identify possible actions
  * clients don't assume that any particular action is available for any particular resources

For a more detailed overview, check out the [REST Wikipedia page](https://en.wikipedia.org/wiki/Representational_state_transfer).