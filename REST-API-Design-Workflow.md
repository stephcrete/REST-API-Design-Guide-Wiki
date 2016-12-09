First, figure out the data set: what set of data / which concepts do you want to expose/manipulate through the API?

Second, split the data set into resources, then for each resource:
* identify...
  * the name of that resource?
  * if is it fine-grained enough?
* determine operations & map to verbs
  * what operations can be performed on that resource?
* determine what could go wrong for each operation?
 * which failures could occur for each operation (e.g., business rules, illegal operations, ...)
 * for each error: determine how to represent it and return it to the client (status codes, error payloads, ...)
* design representations
  * how should requests/responses look like?
    * for this you can leverage tools like Swagger UI
* design integration with existing resources
  * how is this resource related to other ones?
  * do other resources need to evolve to accomodate for this new resource?

> If you find things that don't fit the resource model, you might be facing a case where you need to define an _action_ rather than a _resource_. In that case, take a look at the corresponding section of the design guide.

ATTENTION:
> DO NOT try to create a 1:1 mapping between your relational model and your REST API, as it will only lead to maintenance issues down the road. Consider your data model and the REST resources as separate (although related) things, each with their own set of constraints and design.