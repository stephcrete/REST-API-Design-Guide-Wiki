# 200 (OK)
Use cases:
* update/retrieve data
* bulk creation
* bulk update

You MUST NOT use 200 OK for everything!

# 201 (CREATED)
Should be used after a successful POST creation request.

The response should include the _Location_ header with a link towards the location of the created resource.

Use cases:
* create resources (single items)
