Your APIs MUST be versioned appropriately.

Once you release a public API, you've committed to never breaking things without notice. Versioning helps you iterate faster and prevents invalid requests from hitting updated endpoints.
* the API version MUST be specified in the URI
* the API version MUST always be present (i.e., including for the first version)
* the API version MUST be specified as 'v<number>'
* if a user tries to reach an API without specifying the version, they MUST get a 404 error response
* if a user tries to reach an API endpoint without specifying a resource (e.g., GET .../api/v1) the response body MAY contain basic information about the API in plain text (e.g., api name) 
  * from a security point of view, the response SHOULD be empty

You MAY help smooth transitions by offering multiple versions of your API for a period of time.

Examples:
* .../api/v1
* .../api/v2
* ...