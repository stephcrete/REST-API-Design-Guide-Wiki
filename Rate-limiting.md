# About
If your API has to be consumed by external partners but you need to control that they don't overuse your API, then you can add rate limits.

# HTTP headers to use
If you implement this, then your API should use the following HTTP headers:
* X-RateLimit-Limit
  * how many calls can be made before the rate limit reset
* X-RateLimit-Remaining
  * how many API calls remain
* X-RateLimit-Reset
  * remaining window before reset of the rate limit (UTC epoch seconds)