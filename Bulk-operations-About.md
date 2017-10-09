About
⚠️ Do NOT implement support for bulk operations unless you really need to. Performance is one good argument, but often you can rather design your application in a different way.

Bulk operations allow you to regroup multiple items to limit the number of requests. This is especially useful when you have performance issues due to the fact that there are too many requests being made against your API.

Let's suppose that you have employees (/employees) and you need to reassign many of them to a new location (e.g., location property of an employee).

When you do so, you can either:
* perform n requests: one POST request per employee with the new location value (e.g., POST /employees/123 ... /456... /789...)
* perform a single POST request against a specific collection resource (e.g., POST /employees-bulk) with all the updates to perform

# Section
* [[Bulk operations Types]]
* [[Bulk operations Atomic]]
* [[Bulk operations Non atomic]]
* [[Bulk operations Asynchronous]]
* [[Bulk operations HTTP status codes]]
* [[Bulk operations Resources naming convention]]
* [[Bulk operations Errors]]
* [[Bulk operations Creation example]]
* [[Bulk operations Update example]]
* [[Bulk operations Create and update example]]
