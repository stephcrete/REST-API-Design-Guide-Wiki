Given that bulk operations concern multiple items, you cannot use a code such as HTTP 202 (created), even if you performed a bulk creation operation since you won't be able to provide a single location back to your API client..

Instead, if the bulk operation is successful, you SHOULD return an HTTP 200 (ok) status code.