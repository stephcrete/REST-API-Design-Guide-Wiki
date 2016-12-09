The simplest case is the one where you want to let the users of your API search for specific items of a specific resource. 

For example, to search for black dogs named "foo":
```
GET .../dogs?name=foo&color=black
```

With the above we simplify the URIs by sweeping parameters and other complexities under the question mark.

You can also support Google-style search on all fields using the "q" query parameter:
```
GET .../dogs?q=black
```
In the example above, 'q' represents the query string. Wildcards MAY also be used.