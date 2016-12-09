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