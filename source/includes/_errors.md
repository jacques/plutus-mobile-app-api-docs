# Errors

The Plutus Platform API uses the following error codes:

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request has errors passing parameter validation
401 | Unauthorized -- The API key provided is incorrect
403 | Forbidden -- The requested resource is not available
404 | Not Found -- The specified resource could not be found
405 | Method Not Allowed -- You tried to access a resource with an invalid method
406 | Not Acceptable -- You requested a format that isn't json
410 | Gone -- The resource requested has been removed from our servers
429 | Too Many Requests -- You're requesting too many resources! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.