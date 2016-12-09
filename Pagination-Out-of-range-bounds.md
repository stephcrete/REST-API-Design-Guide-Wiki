If a client requests a range of items that yield no result, then you MUST still return a 200 OK with an empty _items_ array and _metadata_ object.

For example, assuming that there are 100 records available and that we perform a request that falls out of the existing range (in this case: too far):

```
GET /dogs?limit=10&offset=100
 
200 OK
{
    "items": [ ],
    "metadata": {
        "limit": 10,
        "offset": 100,
        "previousOffset": 90,
        "nextOffset": null,
        "currentPage": null,
        "pageCount": 10,
        "totalCount": 100
    }
}
```

In the above example, notice that:
* the nextOffset is null, indicating that there's no next page
* the currentPage is null, indicating that the currently requested page does not exist
* the previous offset points to the last page that actually exists

⚠️ The 204 (No Content) status code might look like a good fit for thus purpose, but it's actually not meant for this.
For more details, check out:
* http://tools.ietf.org/html/draft-ietf-httpbis-p2-semantics-19#section-7.2.5
* http://stackoverflow.com/questions/11402156/rest-status-code-204-on-paginated-result (2nd answer)