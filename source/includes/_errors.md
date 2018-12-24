# Errors

<!-- <aside class="notice">
This error section is stored in a separate file in <code>includes/_errors.md</code>. Slate allows you to optionally separate out your docs into many files...just save them to the <code>includes</code> folder and add them to the top of your <code>index.md</code>'s frontmatter. Files are included in the order listed.
</aside> -->

KoiReader uses conventional HTTP response codes to indicate the success or failure of an API request. In general: Codes in the 2xx range indicate success. Codes in the 4xx range indicate an error that failed given the information provided (e.g., a required parameter was omitted, etc.). Codes in the 5xx range indicate an error with KoiReader's servers.
Some 4xx errors that could be handled programmatically (e.g., image resolution is too small) include an error code that briefly explains the error reported.

Following error codes are being used:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- The page requested is hidden for administrators only.
404 | Not Found -- The specified page could not be found.
405 | Method Not Allowed -- You tried to access a page with an invalid method.
406 | Not Acceptable -- You requested a format that isn't json.
413 | Request Entity Too Large -- You tried to upload a file with size more than 10MB.
429 | Too Many Requests -- You're requesting too many pages! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.

We recommend writing code that gracefully handles all possible API exceptions.
