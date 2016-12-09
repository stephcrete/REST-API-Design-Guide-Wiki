# HTTP headers
HTTP includes the Cache-Control header. Cache-Control lets you configure rules for caching.
In general, you SHOULD set Cache-Control with a max-age value (in seconds) equal to the freshness lifetime (up to you).
For example, if you configure it as follows, it tells your API clients that they can cache the results for 60 seconds:
```
Cache-Control: max-age=60
```

# Caching vs Security
> :warning: Your API MUST prevent clients & intermediaries from caching sensitive information:
```
Cache-Control: no-cache, no-store, must-revalidate
Pragma: nocache
Expires: 0
```

> Correctly evaluate whether the data can be cached or not. If it may be cached by the client, then you SHOULD NOT use the above.

# Reference
You can find a great guide about this here: https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching?hl=en