# About
Welcome!

The repository hosts the REST API Design Guide of [Statistics Canada](https://www.statcan.gc.ca/). It is a copy of the the REST API Design Guide of the [National Bank of Belgium](https://www.nbb.be) imported from the following github repository (https://github.com/NationalBankBelgium/REST-API-Design-Guide).

# Why
Choices choices choices...

There are many ways to implement RESTful APIs and, at this point in time, no clearly winning industry standard.
There are many design choices to make:
* high level design: pagination? filtering? search? sorting? ...
* detailed design: page=2? offset=10? version in the URL or in a header? ...

When there are many options to choose from, development teams can argue forever about the best solution for each use case.

There are various standardization efforts that cover a lot of ground and multiple ways to formalize "REST" APIs (e.g., json-api, OData, OpenAPI, ...) but none that catered for all aspects we wanted to cover in the APIs of Statistics Canada.

While preparing for the development of our APIs, we've decided to create our own design guide, with our own choices, covering our current and known future needs.

## REST-like or truly RESTful?
Leonard Richardson has listed different "maturity levels" for REST APIs. This is covered in details here: http://martinfowler.com/articles/richardsonMaturityModel.html

The Level 3, "Hypermedia Controls" introduces the notion of "discoverability" of the REST API, allowing your clients to "discover" the possible interactions within the responses provided by the server. This is often referred to as "HATEOAS" (Hypermedia As The Engine of Application State).

Roy Fielding (creator of REST) stated clearly that level 3 of the maturity model is actually mandatory for an API to be called a REST API: http://roy.gbiv.com/untangled/2008/rest-apis-must-be-hypertext-driven

Nevertheless, so far, we have chosen not to implement HATEOAS in our design; although this doesn't mean that we cannot add support for it at a later time. Take this choice with a grain of salt, it remains arbitrary. You might prefer implementing HATEOAS or similar solutions to go further with decoupling your client and server implementations and make your API truly RESTful. 

There are tools and libraries that can help you with implementing support for level 3 in an easy way (e.g., [Spring HATEOAS](http://projects.spring.io/spring-hateoas/), ...).

*So to be clear, this is not a truly RESTful API design guide.*

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