Your API SHOULD support [optimistic concurrency control](https://en.wikipedia.org/wiki/Optimistic_concurrency_control), that is, allow clients to update data without necessarily acquiring locks on resources in advance while avoiding most cases where clients would overwrite each others changes when updates happen concurrently.

# Sections
* [[Concurrency Headers to use]]
* [[Concurrency vs Delete operation]]
* [[Concurrency vs Pagination]]
