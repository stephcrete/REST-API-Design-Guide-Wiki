If you need to attach complex metadata with a file upload, then you MAY use the following approach. Although, in the general case, you SHOULD apply the solution proposed in the previous section.

Be aware that this approach is less performant as the encoding will make the payloads slightly heavier (normally not critical if small files are considered though).

With this approach:
* your client MUST perform a POST request
* your client MUST provide a JSON object in the body containing
  * a "files" array containing file objects (cfr below)
  * (optional) a "metadata" object containing additional information about the files/upload

File objects MUST contain:
* data: the file content as a base64 encoded string
* metadata: an object containing additional information about the file
  * name: the name of the file, or some identifier that your API can recognize (e.g., holidays)
* filename: the local filename on the user's filesystem (must be a US-ASCII approximation) (e.g., holidays-2016-03-10.xlsx)
* (optional) creationDate
* (optional) modificationDate
* (optional) size
* any other information you see fit

Top-level metadata object
* any information you see fit