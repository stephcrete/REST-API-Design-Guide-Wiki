There are two major types of resources to consider: _collections_ and _single items_ (also called _documents_):

Examples
* collection: `/api/v1/cars`
* document (single item): `/api/v1/cars/123`

You could also consider a more fine grained classification:
* document: akin to an object instance
  * singular noun
* collection: server-managed directory of resources. Clients MAY propose new resources to be added but it's up to the collection to choose to create a new resource or not. A collection resource chooses what it wants to contain and decides the URIs of each contained resource
  * plural noun
* store: client-managed resource repository. A store resource lets an API client put resource in, get them back out, and decide when to delete them. Each stored resource has an URI that was chosen by a client when it was initially put into the store
  * plural noun
* controller: a controller resource models a procedural concept. Controller resources are like executable functions or actions. Check out the section about Actions for more details
verb or verb phrase