# About
Welcome!

This is the REST API Design Guide of the [National Bank of Belgium](https://www.nbb.be).
This guide describes all design choices made for the creation of RESTful APIs at the National Bank of Belgium.

# Why
Choices choices choices...

REST means many things to many people and, although there are more and more REST APIs, there is still no clear industry "winner" regarding exactly how a REST API should be implemented.

There are various standardization efforts and multiple ways to formalize REST APIs (e.g., json-api, OData, OpenAPI, ...) but none that included all aspects we wanted to cover in the REST APIs of the National Bank of Belgium.

## REST maturity level
Being truly RESTful, according to experts means (among other things) implementing [HATEOAS](https://en.wikipedia.org/wiki/HATEOAS). While that is appealing, it also has security implications. We always say that security by obscurity is not security, but providing attackers with a full of your API is not necessarily wise..

At the National Bank of Belgium we have chosen to limit ourselves to Level 2 of [Richardson's Maturity Model](http://martinfowler.com/articles/richardsonMaturityModel.html).

If you're looking for a truly RESTful API design guide, you should probably continue looking elsewhere :)

# Terms
Rules and guidelines in this design guide have different levels. Some are optional while some others are mandatory. Also, there are recommendations against some approaches, as well as things that are simply forbidden.

Here's how each term should be understood:
* MUST: it's mandatory (i.e., hard rule)
* MUST NOT: it's forbidden (i.e., hard rule)
* SHOULD: it's heavily recommended (i.e., soft rule)
* SHOULD NOT: there may exist valid reasons not to respect this but the implications should be well understood
* MAY/OPTIONAL: it's optional (i.e., advice)

Take a look at [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt) for more details.
