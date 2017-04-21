# Errors

<aside class="notice">This error section is stored in a separate file in `includes/_errors.md`. Slate allows you to optionally separate out your docs into many files...just save them to the `includes` folder and add them to the top of your `index.md`'s frontmatter. Files are included in the order listed.</aside>

The Kittn API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request sucks
401 | Unauthorized -- Your API key is wrong
403 | Unverified Params
404 | Not Found -- The specified kitten could not be found
410 | Gone -- The kitten requested has been removed from our servers
412 | Operation Failure
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.

# Headers

<aside class="notice">
	Base Api call
</aside>

Header      | Value
----------- | -------
USER_ID		| LoggedIn user id
AUTH_TOKEN	| LoggedIn user token
Content-Type| 'application/json'
