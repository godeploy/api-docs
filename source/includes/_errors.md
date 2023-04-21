# Errors

<aside class="notice">
Clients with Card payment terms can not use this API and will get an error. 
</aside>

The Order API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your JWT token is wrong.
404 | Not Found -- Requested resource was not found.
405 | Method Not Allowed -- You tried to access a request with an invalid method.
500 | Internal Server Error -- We had a problem with our server.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
