# Target
To create a single item, you SHOULD issue a POST request against the parent collection (e.g., .../v1/employees to create a new employee).

⚠️ Do NOT forget that POST is not an idempotent operation: repeating POST operations multiple times do not guarantee the same result each time.

# Rules for the client
* MUST define the _Accept header_ to specify the list of media types it supports/prefers
* MUST define the _Content-Type_ header to specify the media type of the request body.
* MAY pass an _echo_ query parameter with the following values
  * ⚠️ ONLY if the server supports/accepts it
  * none: SHOULD not return a response body
  * id: SHOULD only return the id (UUID!) of the created resource(s)

# Rules for the server
* MUST return HTTP 201 (Created) if successful
* SHOULD return the representation of the created resource(s) (see below)
* SHOULD set the Content-Type header
* SHOULD set the Location header in the response
  * for a single item it SHOULD point to that specific item (e.g., Location: /employees/de305d54-75b4-431b-adb2-eb6b9e546014)
  * for a bulk creation operation it should point to a specific collection resource (see bulk operations section) (e.g., Location: /employeesBulk)
* SHOULD set the Last-Modified header
* MAY consider using vendor-specific media types to give semantics about the data

# Example
```
POST .../v1/employees
Accept: application/json
Content-Type: application/json
{
    "uuid": "...",
    "name": "..."
}
```

# Bulk creation
Note that for bulk operations, we have specific recommendations: bulk operations should be available through a dedicated resource (see bulk operations section for more details).