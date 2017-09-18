# Rules
* requests for collections MUST always be paginated
* API clients MUST be able to clearly specify the slice of the data set they want to retrieve.
  * you MUST use _limit_ and _offset_ query string attributes for pagination. It's a pattern that is well understood and used in most databases
    * limit: the maximum number of elements to return at once
      * MUST NOT be < 0
      * MUST NOT be > 1000
    * offset: where to start
      * MUST NOT be < 0
    * offset and limit MUST both be specified by API clients. If either is missing, default values are applied
      * limit: 10
      * offset: 0
* a paginated response MUST contain
  * an "items" array containing the corresponding results
    * respecting the rules defined in the filtering section
  * a "metadata" object containing information about
    * the pagination values
    * the sorting parameters
    * the ETag values for all the given items
    * ...

# Metadata

## Pagination metadata
* pagination: an object  containing all the pagination metadata:
* limit: the requested limit (provided by the client)
* offset: the requested offset (provided by the client)
* previousOffset: the previous offset or null if there is none
* nextOffset: the next offset or null if there is none
* currentPage: the current page or null if it does not exist (e.g., out of bounds)
  * if the offset falls between two pages, then the currentPage number should be the one of the page that the first item of the resultset is part of
* pageCount: the total number of pages
* totalCount: the total number of elements in the collection

## Pagination metadata defaults
Pagination defaults vary depending on the size of the data.

You SHOULD use _limit=10_ and offset=0 as defaults.
These defaults SHOULD apply even if limit/offset are not specified explicitly in the request.

If each item is very large, then you MAY set the limit lower. On the opposite, if objects are very small, a larger limit could make sense (i.e., less requests = potentially increased performance perceived).

## Metadata for concurrency control
See concurrency section: [[Concurrency-vs-Pagination]]

## Metadata for sorting
See sorting section: [[Sorting-Metadata]]

## Metadata for warnings
Check out the following page: [[Error-handling-Warnings]]

## Custom metadata
In addition to all the above, you MAY also introduce custom metadata as you see fit. If you do so, for client implementation simplicity, you SHOULD add it inside a "custom" object within the "metadata" object.

## Omitting metadata
You MAY add support for a "excludeMetadata" URI parameter if you want your API clients to be able to exclude the metadata.

## Example
Check out the [[Pagination-Example]] page for a representative example.
Also check out examples of 