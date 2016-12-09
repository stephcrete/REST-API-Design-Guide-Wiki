To scope a search, you SHOULD support prefixing it with the scope of the search. For example, to search in dogs owned by resource ID 5678:
```
GET .../owners/5678/dogs?q=foo+bar
```

No need for explicitly adding "search" in the URI. This is made explicit by the presence of the 'q' parameter.