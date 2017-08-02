In some circumstances, you might want to let the clients of your API be able to filter the data that you return to them.
What we mean by filtering in our case is _customizing the representations_. If you want to search then the filtering section is not what you're after.

Filtering is very useful to reduce bandwidth consumption and limit data exchanges to the bare minimum for specific use cases.

To do this, there are two approaches:
* YOU SHOULD define representation styles
* YOU MAY provide full flexibility through includes/excludes