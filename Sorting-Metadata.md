Just like with pagination, sorting information should be reflected in the API responses for collections.

If you implement sorting, then the response MUST contain a "metadata" object containing information about the sorting (see below). However, API clients MAY still exclude the metadata section by using the "excludeMetadata" query parameter.

The metadata object MUST contain:
* sortedBy: array of objects describing the sorting information

The items placed in the sortedBy array MUST contain:
* field: the field on which the sorting is done
* order: the order of the sorting on that field: ASC|DESC

The items placed in the sortedBy array MUST be defined in the correct order. The order will be kept (JSON mandates that arrays are ordered sequences).

## Example
Check out the example here: [[Sorting-Example]]
And also the example of how it fits along with the rest of the pagination metadata: [[Pagination-Example]]