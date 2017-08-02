# Plural
The resource names MUST always use the plural form
* `/api/v1/cars`
* `/api/v1/payments`

If you mix singular and plural forms, your clients will have to deal with odd pluralization (e.g., person/people) which is bad for uniformity and accessibility.

# Nouns
If you use verbs for resources, you'll create a bad Remote Procedure Call (RPC) API.
You'll end up with way too many operations and it'll make your API much harder to understand/use/maintain.

RESTful APIs SHOULD use nouns for resource names.

Good examples
* `/employees`
* `/cars`
* `/payments`
* `/bills`

Bad examples:
* `/addEmployee`
* `/buyCar`
* `/sendPayment`
* `/createBill`

# Kebab case
Resource names should be written using kebab-case (separate words by hyphens). This is explained here: ]]

Good example:
* `/contract-types`

Bad example:
* `/contractTypes`

Why? To more easily distinguish between the URI path elements and query parameters (which should use camelCase)

# Concrete names
Resources SHOULD have concrete names.

Beside the importance for clarity, choosing concrete names mean that you map resources to fine-grained concepts and that you limit the abstraction level.

If your resources are too abstract (e.g., articles), then you loose clarity and can quickly start mixing things up. Rather, go for concrete concepts (e.g., cars, phones, tablets, ...).

If we take a Cash handling application as example, it could have the high level notion of "Movements". 

Movements could be of different types; actually many if not all transactions within such an application could be considered to be movements (e.g., notifications, deposits, payments, ...).

For this reason, using _movement_ as a resource would be a bad design choice because then you would have to map a LOT of detailed operations on a single resource.

Instead, resources for such an application could be things such as notifications, deposits, ... (i.e., lower level/fine-grained concepts).

Another example: suppose that an application manages contracts of different types. Assuming that each contract type has many specificities (e.g., different relationships with other concepts), it would actually be bad from a design perspective to create a "contracts" resource as that would force you to manage all the contract details within the representation. Instead, you could have specific resources for each contract type.