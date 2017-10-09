Many developers don't like to think about exceptions and error handling, but it is a very important piece of the software development puzzle.

One thing to keep in mind is that, from the perspective of the client consuming your REST API, everything at the other side of the tunnel is a black box. Errors therefore become a key tool for providing context and visibility into how to use your API (in addition to the API documentation).

In this section we give some guidance regarding error handling, things to do and things to avoid as well as recommendations regarding how to represent errors in your payloads.

# Sections
* [[Error handling Expectations]]
* [[Error handling Status codes]]
* [[Error handling Error details]]
* [[Error handling Example with a single error]]
* [[Error handling Example with multiple errors]]
* [[Error handling Example with parameters]]
* [[Error handling Example with additional metadata]]
