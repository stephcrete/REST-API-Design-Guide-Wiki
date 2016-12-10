# General security recommendations
* follow OWASP guidelines
  * top 10 vulnerabilities: https://www.owasp.org/index.php/OWASP_Top_Ten_Cheat_Sheet
  * REST Security Cheat Sheet: https://www.owasp.org/index.php/REST_Security_Cheat_Sheet
* validate & encode all inputs AND outputs correctly. You MUST NEVER trust what you receive (whether from the client or 
* exclude all security sensitive headers (e.g., disclosing server/libraries versions, etc)
* reject all bad input from the client side (4xx codes)
  * this should help protect against injection attacks
* log all suspicious activities (useful for forensics)
* have monitoring in place to detect abnormal usage of your API
* throttle API usage (see rate limiting section) to try and mitigate Denial of Service (DoS) attacks and block malicious users

# Transport layer security recommendations
These security measures are designed to help protect applications against eavesdropping, man-in-the-middle (MITM) attacks and to protect confidentiality, integrity, ...
* everything MUST be served over secure channels: TLS
  * only TLS 1.2 and newer SHOULD be used/proposed/accepted
    * SSLv3: Poodle attack
    * TLS 1.0: Beast attack
    * TLS 1.1: Freak attack
  * servers SHOULD be configured to ensure Perfect Forward Secrecy (PFS)
    * this is to ensure that, even if the private key of a server is leaked at some point, all the data transferred before that between clients and the server will still be protected
    * this is done by using a cipher suite with ephemeral Diffie-Hellman (DHE) or the elliptic-curve variant (ECDHE)
the crypto parameters MUST use a secure length that matches the supported keylength of the certificate (>= 2048 bits or equivalent Elliptic Curves)
    * generate individual DH-parameters to get unique prime numbers: openssl dhparam 2048 -out dhparam 2048.pem
  * including static content (images, scripts, css), login and logout pages, ...
    * this SHOULD avoid vectors for MITM and warnings about mixed content
* the certificate use for an application SHOULD
  * be specific to the application's DNS domain
  * NOT be a wildcard certificate
  * always provide all needed certificates (i.e., a full path from the certificate to the Root CA) so that clients can fully validate the trust chain
  * use AT A MINIMUM SHA-512
  * the OWASP recommendations MUST be followed/applied: https://www.owasp.org/index.php/Transport_Layer_Protection_Cheat_Sheet
* you MUST NOT mix encrypted and unencrypted content (aka mixed content) on the same host, as the request of any resource through HTTPS might disclose the session identifiers

> Some of these security measures SHOULD be taken care of by the infrastructure configuration, but MUST be applied to all applications

# Error handling
While handling errors on the server side:
* you MUST NEVER send stack traces to API clients
  * doing so provides too much insight into the inner workings of your application, potentially helping attackers
* you MUST NEVER send information about software and software versions as that could ease the work of an attacker
  * doing so provides too much insight into what is used to run your application. For example, if an attacker can find out that your application runs under Tomcat 8.5.1, then he can easily check all security flaws that your application server is not protected against and use these to attack your application and the underlying infrastructure

# Avoid Insecure Direct Object References (IDOR)
Whenever you expose data to the outside world, you MUST avoid exposing direct object references.

The following page provides a good overview of the important security issues that you create through this: https://www.owasp.org/index.php/Top_10_2013-A4-Insecure_Direct_Object_References

Ideally, there SHOULD be an additional layer of abstraction between identifiers exposed to the client-side, and those used internally in the application. Additionally, the exposed identifiers SHOULD be unguessable, e.g. a long randomly-generated UUID.

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