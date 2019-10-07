# Errors


The Higg Public API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is invalid or does not match requested account ID in the URL.
404 | Not Found -- The specified query produced no results
405 | Method Not Allowed -- You tried to access with an invalid method.
406 | Not Acceptable -- You requested a format that isn't json.
418 | I'm a teapot.
429 | Too Many Requests -- You're requesting too many kittens! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
