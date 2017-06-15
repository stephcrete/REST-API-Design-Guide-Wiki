Here are basic guidelines around API parameters.

# Path
Use for required elements.

If an element identifies a resource, it should be in the path. For example: `.../api/v1/cars/1`

# Query string
Use for options (e.g., paging, filtering, sorting, ...).
Query parameters should be written in camelCase (e.g., excludeMetadata)

# Body
Use for actual contents and for complex search queries (query by example)

# Headers
Use for global values (e.g., API keys, cookies, ...).

When you have the choice and security is not at risk, add support for passing information via the URL. This way clients can more easily test requests (e.g., possibility to select the data format of the response via a query parameter)