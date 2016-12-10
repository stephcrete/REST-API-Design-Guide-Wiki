Insecure Direct Object References (IDOR) is part of the OWASP top 10 vulnerabilities.

Whenever you expose data to the outside world, you MUST avoid exposing direct object references, because that is insecure.

The following page provides a good overview of the important security issues that you create through this: https://www.owasp.org/index.php/Top_10_2013-A4-Insecure_Direct_Object_References

Ideally, there SHOULD be an additional layer of abstraction between identifiers exposed to the client-side, and those used internally in the application. Additionally, the exposed identifiers SHOULD be unguessable (e.g. a long randomly-generated UUID).

With RESTful APIs, you MUST NOT expose a direct reference towards a specific entity that would allow an attacker to guess/calculate references towards other entities.

To make the risk more clear, here's an example:
* http://.../api/v1/client/1
* http://.../api/v1/client/2

Knowing the first link, it's very easy to guess that the second one could/should exist. This is actually bad from a security perspective. Combined with flaws in authorization, your API could end up exposing data that it shouldn't.

To make it harder for attackers to harvest your data and potentially take advantage of authorization flaws in your back-end, you should use globally unique identifiers (e.g., UUID or GUID) to refer to resources. We recommend the usage of [Universally Unique Identifiers (UUIDs)](https://en.wikipedia.org/wiki/Universally_unique_identifier)

Using UUIDs, your links would look like that instead:
* http://.../api/v1/client/f47ac10b-58cc-4372-a567-0e02b2c3d479
* http://.../api/v1/client/860b44d1-c2ef-4b74-94bb-84e381d51945

As you can see, each id is random, making the job of an attacker much harder.
Note that this absolutely DOES NOT remove the need for authorizing each and every resource access correctly.

# Avoid excessive model attributes
Avoid excessive model attributes in API responses. This is a major security issue with many APIs and it happens when one relies too much on the transparent serialization mechanisms.

Example:
```
class User {
    id;
    firstName;
    lastName;
    email;
    phone;
    address;
    username;
    password;
}
```

If we use transparent serialization mechanisms, then all the information present in instances of that class will be given to the API clients, thus we could end up with:

```
{
    id: "1",
    firstName: "foo",
    lastName: "bar",
    email: "foo.bar@nbb.be",
    phone: "+322...",
    address: "...",
    username: "foobar2000",
    password: "p0wn3d"
}
```

Of course one might wonder: should the password be part of the response to API calls? The answer is most probably "no".
Thus, always pay attention to what you serialize and do not hesitate to create REST-API-specific data transfer objects (DTOs) containing ONLY the information that should be serialized and given back to clients.