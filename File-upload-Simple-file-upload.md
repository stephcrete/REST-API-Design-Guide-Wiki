This section covers both the single and multiple file upload scenarios. As you'll see, both can be achieved in the same manner.

For simple file uploads:
* your client MUST perform a POST request
* your client MUST specify the Content-Type header and use the multipart/mixed (RFC 2046) media type (that media type allows for multiple parts to be specified in the body)
* your client SHOULD specify the charset parameter as part of the Content-Type header
  * if the charset is not defined, the default is US-ASCII
* your client MUST specify the boundary parameter as part of the Content-Type header
  * the boundary value MUST be a delimiter that MUST NOT be found in the rest of the payload. Example: `---------------------------<uuid>`
  * the boundary value MUST consist of 1-70 characters (ideally US-ASCII)

Example:
```
POST .../upload
Content-Type: multipart/mixed; charset=utf-8; boundary="---------------------------d0b473e2-0abf-433e-8c74-faee35ab6e91"
...
```

The client MUST add a _part_ in its request for each file.

For each part:
* the client MUST begin the part with the boundary defined in the request's Content-Type header
* the client MUST specify the Content-Type header and, at a minimum
  * your client MAY use the _application/octet-stream_ media type to state that it uploads raw content that should not be interpreted (see https://www.ietf.org/rfc/rfc2046.txt)
  * your client MAY instead use the media type corresponding to the file that is being uploaded (e.g., application/pdf for pdf files)
    * if the file type is unknown, the "application/octet-stream" media type MUST be used
  * your client MAY define the charset of the file contents
* the client MUST specify the Content-Disposition header with at a minimum: form-data; name="<name>"; filename="<filename>"
  * <name>: the name of the file, or some identifier that your API can recognize (e.g., holidays)
  * <filename>: the local filename on the user's filesystem (must be a US-ASCII approximation) (e.g., holidays-2016-03-10.xlsx)
  * your API MAY accept additional properties depending on your requirements (cfr RFC 2183: creation-date, modification-date, size or any custom ones)
* the client MAY add the Content-Encoding (RFC 7231) header to specify how the file data has been encoded in the request (so as not to lose details about the media type)
  * one example: base64 version of a JPEG file
  * another example: gzip version of a file for network efficiency
  * there can also be multiple values (which MUST then be specified in the order they were applied)
* the file data MUST be separated from the headers by one blank line

The last part MUST be followed by the boundary defined in the request's Content-Type header
* the client SHOULD specify the charset parameter in the Content-Type header

# Text for agents unable to handle multipart
Before the first part's boundary (and after the last), you MAY add text for agents that are not able to handle the multipart media type correctly.

Example:
```
POST .../upload
Content-Type: multipart/mixed; charset=utf-8; boundary="---------------------------d0b473e2-0abf-433e-8c74-faee35ab6e91"
 
Hey there, I'm going to be ignored!
 
---------------------------d0b473e2-0abf-433e-8c74-faee35ab6e91
...
---------------------------d0b473e2-0abf-433e-8c74-faee35ab6e91
 
Here there, I'm also going to be ignored!
```