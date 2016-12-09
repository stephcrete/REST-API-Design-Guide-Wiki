Whenever you design a REST API, you should strive for:
* simplicity and ease of use
    * be friendly to consumers of your API: try to make their life easier and less painful
    * focus on URIs and payloads: these are what your clients will have to live with, not your internal domain model
      * do not apply the SOAP-way when you create RESTful APIs, the clients are not the same (humans vs machines)
      * your API should be easily explorable through a standard Web browser
* consistency
  * aim for consistency across your API
  * do not implement similar things in different ways (e.g., never implement search or filtering in different manners)
* flexibility
  * empower the clients of your API
  * although, try to keep things simple unless there's no alternative