A key principle of REST involves separating your API into logical resources. These resources are manipulated using HTTP requests where the method (GET, POST, PUT, PATCH, DELETE) has specific meaning.

A REST resource is anything that can be referenced through the REST API.

Resources:
* are concrete concepts (e.g., cars, payments, articles, bills, ...)
* are coarse grained (i.e., high level)
* use nouns rather than verbs
* are associated with a specific URI (e.g., /api/v1/employees)
* URI should be descriptive and well structured

The goal of REST resources is to expose a uniform interface as described in the previous section.

> Although the internal models of your application may map neatly to resources, it isn't necessarily a one-to-one mapping. Avoid leaking implementation details out to your API.