[URIs](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier) are composed of multiple parts.

# Structure
`URI = scheme "://" authority "/" path [ "? query ] [ "#" fragment ]`

# Example
`https://www.nbb.be/hello-world?param1=value1&param2=value2#section1`

In the above example:
* protocol/scheme: https://
* sub-domain: www
* domain: nbb.be
* path: /hello-world
* query string: ?param1=value1
* query parameters
  * param1: value1 (key: value)
  * param2: value2
  * separator: &
* fragment: section1

# Rules

## URIs
The URIs MUST be:
* completely in lowercase
* with kebab/spinal case: a-super-uri (i.e., hyphens to separate elements)
* as flat as possible (resources should be just below the API entry point)
  * api/v1/employees rather than api/v1/enterprise/department/service/division/employees
  * do NOT cross-reference everything, there's no need to repeat the database relations in the URL representations
    * ⚠️ links like /api/v1/employees/{uuid}/manager don't need to exist because there's already an identifier for that resource: /employees/{uuid}
    * :white_check_mark: instead, you can either nest other objects in the responses or provide links to those objects
that's a tradeoff between client or server effort
     * :white_check_mark: although, when in doubt, think about how you would display the data to a human user without API concerns 
* no trailing forward slash ( / )
* no underscores ( _ )

## Resources

### Plural
The resource names MUST always use the plural form
* `/api/v1/cars`
* `/api/v1/payments`

If you mix singular and plural forms, your clients will have to deal with odd pluralization (e.g., person/people) which is bad for uniformity and accessibility.

### Nouns
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