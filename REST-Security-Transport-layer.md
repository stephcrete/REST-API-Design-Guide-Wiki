Transport layer security is of critical importance. 

The following security measures are designed to help protect applications against eavesdropping, man-in-the-middle (MITM) attacks and to protect confidentiality, integrity, ...

Don't even consider exposing a REST API without at the very least the following guidelines respected:
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

