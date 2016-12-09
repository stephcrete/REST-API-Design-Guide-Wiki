The first thing to keep in mind is that there are multiple "clients" for your API:
* the end users
* the developers consuming your API
* the client applications interacting with your API
* the support teams

Each client has specific needs that you must care about:
* the end users
  * need short & descriptive error messages
  * need to be able to visually see where the issue(s) lie
  * don't want to play ping pong with your API: if there are 3 errors, then he should know about all these up-front, not one error at a time
* the developers
  * need detailed information to debug their code (without compromising the security of the systems)
* the client applications
  * need correct error codes for recovery actions
  * need details about the error to pinpoint where the issue lies (e.g., highlight all fields in error)
  * need to know which messages to display to the end users
* the support teams
  * need detailed information, keywords to look for in knowledge databases and correlation ids to be able to correlate what happened in the client application and on the back-end side