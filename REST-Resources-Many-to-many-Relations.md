Usually, when you have many-to-many relations, you can expose the other side of the relationship on each side.

We'll take the following example: if you model _orders_ and _products_, products can be part of multiple orders and orders can contain multiple products.

In that case, you could make it so that the products are available from the orders and conversely, that orders are available from the products.

Now, for the case where you want to manipulate the many-to-many relationship, you can expose the relationship itself as a resource, allowing you to perform CRUD operations on it.

For example, you could create a resource such as orders-products:

```
GET .../orders-products/<uuid>
 
HTTP/1.1 200 OK
{
    "order": {
        "uuid": "..."
    },
    "product": {
        "uuid": "..."
    }
}
```

In the example above, retrieving a specific item in the many-to-many resource collection returns metadata about the association. The client can use that to locate the linked items.

You MAY also let your API client create the association themselves.

If your API clients do not need to retrieve only the association metadata or create the associations themselves, then you SHOULD simply add links or inline the relations on either or both sides (see section about entity and link expansion).

Here's an example:

```
GET .../orders/<uuid>
 
HTTP/1.1 200 OK
{
    ...
    "products": [
        {
            "uuid": "..."
        },
        ...
    ]
}
```

Depending on the quantity of data, you MAY either put the IDs or inline some or all of the data of the other side of the relationship.
You could also create specific resources under either or both sides to retrieve only the linked items.

Here's an example: `GET .../orders/<uuid>/products`

With the example above, you can also easily add support for pagination, filtering, sorting, ...