For clarity and implementation simplicity, bulk operations SHOULD be targeted at specific resources.

Specifically, assuming that you have a _/employees_ resource, bulk operations SHOULD be targeted at a _/employeesBulk_ resource.

For example in Java, this makes it much easier to implement:
* /employees maps to a method that accepts a single Employee object and returns an Employee object
* /employee maps to a method that accepts a list of Employee objects and returns a list of Employee objects