In order to optimize your API, you MAY add support for caching and conditional requests. Although, don't try to add caching to your API unless you know you need to; there's a nice quote from Phil Harton that you should keep in mind: 

>"There are only two hard things in Computer Science: cache invalidation and naming things". Caching will bite you if not implemented properly.

By adding support for caching and conditional requests, you can:
* eliminate some security risks
  * for example: you could avoid that sensitive data be cached by intermediaries and clients (you cannot ensure it but you can ask nicely)
* gain performance and client-perceived latency
* increase reliability
* reduce the server load

# Sections
* [[Caching and conditional requests Rules]]
* [[Caching and conditional requests HTTP headers]]
* [[Conditional requests]]
* [[Cache control]]
