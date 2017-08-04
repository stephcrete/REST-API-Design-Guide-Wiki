Whenever dates and times need to be exchanged, they SHOULD respect the [ISO 8601](http://www.iso.org/iso/home/standards/iso8601.htm) standard.
time stamps SHOULD look like: YYYY-MM-DDTHH:MM:SSZ
dates SHOULD look like: YYYY-MM-DD
The exception to this rule is for HTTP headers which MUST be specified as per [RFC 1123](https://www.ietf.org/rfc/rfc1123.txt). You should format time stamps in HTTP headers like this: Sun, 06 Nov 1994 08:49:37 GMT
* in Java: "EEE, dd MMM yyyy HH:mm:ss 'GMT'"

Example: `1977-04-22T06:00:00Z`