[URIs](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier) are composed of multiple parts:

`URI = scheme "://" authority "/" path [ "? query ] [ "#" fragment ]`

Example: ``

In our REST APIs, the URIs MUST be:
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