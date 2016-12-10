# About
API keys are keys associated with each legitimate user or set of users for your application.

API keys can be used for two things:
* identification: restrict the usage of your API to legitimate users
* analytics: tracking API usage, calculating usage metrics, etc

In a sense, an API key is like a password; it'll be known and kept by your clients and they'll have to pass it along with each of their requests.

# Properties
An API key should have those properties:
* must be a relatively long, random string
* must be a unique identifier
* must be transmitted with each client request
* must be known by the client
* must be validated by the server (before any further request processing)
* must be unique to a client, user, device or software

# Tracking API usage and charge back
By using API keys, you can ease the tracking of how each client/user uses your API.

Each time a client/user will interact with your API, he'll have to provide his API key, meaning that your API can keep track of user/client activity.

You can for example use this information to track which resources the user consumed, how many times he called specific resources, how many records he retrieved, etc.

Based on the collected information, you can also define costs associated with the usage made by a specific client/user.

# HTTP headers to use
Two options:
* Authorization: ideally, your API key should be one of the parameters of the [Authorization header](https://tools.ietf.org/html/rfc7235#section-4.2)
* X-API-Key: another approach is to use a customer HTTP header

# Security guidelines
* API keys are sensitive but can easily be lost, stolen, etc (just like any password)
* DO NOT base all your security on the API key
  * authentication and authorization MUST NOT be based solely on the presence of an API key
* API keys MUST be passed either via headers or within the body of client requests. They MUST NOT be passed within the URL (cfr https://www.owasp.org/index.php/REST_Security_Cheat_Sheet)
  * the reason for this is that when they are in the URL, they can be captured in the logs of Web servers, proxies, etc.
* API keys MUST ONLY be exchanged over secure channels
* API keys MUST be stored in encrypted form
  * since they're like passwords, they have the same confidentiality requirements
* API keys MUST ONLY be readable by their owner
  * again, the confidentiality of the API keys is important
* API keys entropy matters
  * UUIDs can be used 
  * can be encoded with Url62 (i.e., URL-safe encoding)
* API keys MUST be revoked and renewed whenever you think they might have been compromised
* API keys MUST NEVER be exposed in the UI