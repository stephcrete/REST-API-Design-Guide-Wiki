One point worth keeping in mind while designing REST APIs is that you are not supposed to create a 1:1 mapping with your relational data model! REST resources are just REST resources, not database tables.!

When a use case requires that you compose/aggregate data coming from different places (e.g., multiple database tables, files, ...), then you have two basic choices.

You MAY let your API clients deal with the orchestration (i.e., let them interrogate n places to retrieve the necessary data and filter/sort/etc themselves). You SHOULD NOT do this in most cases.

The better alternative is to create REST resources that represent the aggregations/compositions that you require. For example, if you have a users resource and a loans resource, then nothing prevents you from creating a resource that exposes combinations of those in any way shape for form that fits your needs.

When you create compositions or aggregations, the semantics are up to you and depend on what you are trying to achieve. For example, you could decide that end users cannot send updates to a specific composed resource and return a 4xx code.

Or, to take another example, imagine that you create a composition between a _loans_ resource and a _users_ resource, you could let your API clients send updates of either the users, the loans, or both.