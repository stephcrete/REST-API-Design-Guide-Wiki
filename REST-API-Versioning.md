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

> You MUST NOT use semver or similar versioning schemes (e.g., do NOT use v1.x or v1.x.y) as that would just mean that you create too many versions. Detailed version numbers imply a granularity of versioning that doesn't work well with APIs!

Here are some guiding principles for deciding when a new version of your API is actually needed:
* you SHOULD NOT create a new API version when you add fields/attributes to existing resources, if clients can simply ignore those (i.e., if clients MUST NOT add those in their requests)
* you SHOULD NOT create a new API version if you add new resources that clients don't necessarily need to interact with
* you MUST create a new API version if you modify existing resources in a way that will impact clients (e.g., new mandatory field, removal of a field, ...)
* you MUST create a new API version if you introduce new resources that clients MUST interact with
* you MUST create a new API version if you create new error types

> :white_check_mark: Maintain at least one version back, so that other applications depending on your API have time to upgrade to the new version rather than break them straight away.

> Create and maintain a changelog and a migration guide for your APIs so that clients can easily see what changed and how they can upgrade.