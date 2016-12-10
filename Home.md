# About
Welcome!

This is the REST API Design Guide of the [National Bank of Belgium](https://www.nbb.be).
This guide describes all design choices made for the creation of RESTful APIs at the National Bank of Belgium.

# Why
Choices choices choices...

There are many ways to implement RESTful APIs and, at this point in time, no clearly winning industry standard.
There are many design choices to make:
* architecture: level 2? hypermedia?
* high level design: pagination? filtering? search? sorting? ...
* detailed design: page=2? offset=10? version in the URL or in a header? ...

When there are many options to choose from, development teams can argue forever about the best solution for each use case.

There are various standardization efforts that cover a lot of ground and multiple ways to formalize REST APIs (e.g., json-api, OData, OpenAPI, ...) but none that catered for all aspects we wanted to cover in the REST APIs of the National Bank of Belgium.

While preparing for the development of RESTful APIs for the National Bank of Belgium, we've decided to create our own design guide, with our own choices, covering our current and known future needs.

## REST maturity level
Being truly RESTful, according to experts means (among other things) implementing [HATEOAS](https://en.wikipedia.org/wiki/HATEOAS). While that is appealing, it also has security implications. We always say that security by obscurity is not security, but providing attackers with a full of your API is not necessarily wise..

At the National Bank of Belgium we have chosen to limit ourselves to Level 2 of [Richardson's Maturity Model](http://martinfowler.com/articles/richardsonMaturityModel.html).

If you're looking for a _truly_ RESTful API design guide, you should probably continue looking elsewhere :)

# Features
Our REST API Design Guide covers... 
* naming conventions and best practices (e.g., resource naming rules)
* the design of all major elements you would need for business applications
  * CRUD
  * pagination & associated metadata
  * sorting
  * filtering
  * bulk operations
  * concurrency control
  * error handling
  * ...

# Terms
Rules and guidelines in this design guide have different levels. Some are optional while some others are mandatory. Also, there are recommendations against some approaches, as well as things that are simply forbidden.

Here's how each term should be understood:
* MUST: it's mandatory (i.e., hard rule)
* MUST NOT: it's forbidden (i.e., hard rule)
* SHOULD: it's heavily recommended (i.e., soft rule)
* SHOULD NOT: there may exist valid reasons not to respect this but the implications should be well understood
* MAY/OPTIONAL: it's optional (i.e., advice)

Take a look at [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt) for more details.

# Contributing
Contributions are welcome. New designs or change proposals should be discussed via issues on this repository.