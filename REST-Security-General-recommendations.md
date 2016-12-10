Our most basic security guidelines:
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