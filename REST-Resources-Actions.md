# About
API calls that send a response that's not a resource per se are not uncommon depending on the domain. Actions like the following are your clue that you might not be dealing with a "resource" response:
* calculate
* translate
* convert
* ...

One example is if you want to convert a currency to another. Other examples include actions such as _login_ and _logout_.

In those cases, you are not dealing with resources, you are dealing with actions.

# Rules
First and foremost, you MUST try to limit the number of actions (see next section for help).

Actions...
* SHOULD be named using verbs and not nouns
* SHOULD be isolated from the rest of your API under an "actions" resource

To execute an action, your API clients MUST use POST. Here's an example:
```
POST .../api/v1/actions/convert
Accept: application/json
{
    "from": "USD",
    "to": "EUR",
    "amount": "25.00"
}
 
HTTP/1.1 200 OK
{
    "result": "22.46",
    "exchangeRate": "0.90"
}
```

We do NOT recommend this, but you MAY decide to provide an "actions" resource to which API users could POST the actions to execute and require that the payload contains the name of the action to perform. For example:

```
POST .../api/v1/actions
Accept: application/json
{
    "action": "CONVERT",
    {
        ...
    }
}
```

# Limiting the number of actions
To limit the number of actions in your REST API you could try to:
* restructure the action to appear like a field of a resource (works if the action doesn't take parameters)
  * for example, an activate action could be mapped to a boolean 'activated' field and updated via a PATCH to the resource
* treat the action like a sub-resource
  * for example, GitHub's API lets you star a gist with PUT /gists/:id/star and unstar via DELETE /gists/:id/star
* regroup/isolate actions under a generic pseudo-resource (e.g., utilities) so as to avoid creating an RPC-like API

If you MUST define the action apart from actual resources, then make sure to clearly document that the action is NOT a resource.