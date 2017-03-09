# Errors

## Error Object

> Sample of error with help:

```json
{
    "message": "Not allowed service for the branch.",
    "code": "9m86",
    "more_info": "https://bmatic.com/docs/errors/9m86"
}
```

> Sample of simple error:

```json
{
    "message": "Branch not found.",
}
```

HTTP body used when an error occurred.

<aside class="notice">
All errors ocurred in the API return a message as information minimal.
</aside>

<aside class="notice">
All error fields are read only.
</aside>

### Fields
Name | Type | Description
--- | --- | ---
message<span title="required" class="required">&nbsp;\*&nbsp;</span>  | string | A descriptive message regarding the exception.
code | string | An error code to find help for the exception.
more_info | string | The URL of BMatic's documentation for the error code. If the error code is undefined then this value is undefined too.

## Error Types

<aside class="notice">This error section is stored in a separate file in `includes/_errors.md`. Slate allows you to optionally separate out your docs into many files...just save them to the `includes` folder and add them to the top of your `index.md`'s frontmatter. Files are included in the order listed.</aside>

The Kittn API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request sucks
401 | Unauthorized -- Your API key is wrong
403 | Forbidden -- The kitten requested is hidden for administrators only
404 | Not Found -- The specified kitten could not be found
405 | Method Not Allowed -- You tried to access a kitten with an invalid method
406 | Not Acceptable -- You requested a format that isn't json
410 | Gone -- The kitten requested has been removed from our servers
418 | I'm a teapot
429 | Too Many Requests -- You're requesting too many kittens! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
