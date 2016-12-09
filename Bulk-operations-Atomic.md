When you perform additions/modifications in bulk (e.g., POST a collection of items to create, ...), you MUST determine if those operations are atomic, non-atomic or asynchronous.

For operations that are atomic, you SHOULD return a 200 (ok) status code if all items could be created/updated (optionally returning a representation of all created resources in the body of your response).

If an issue occurred for any of the items, then you SHOULD return a 4xx status code.