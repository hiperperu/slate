
## Bad Request

> Sample object:

```json
{
    "message": "Not allowed service for the branch.",
    "code": "9m86",
    "more_info": "https://bmatic.com/docs/errors/9m86"
}
```

HTTP body used when an error occurred.

<aside class="notice">The fields <code>code</code> and <code>more_info</code> to be return only when the error is documented.</aside>

### Fields
| |
|:---|
|**message** <span class="param-type">string</span> <span class="required-param">required</span> <br> A descriptive message regarding the exception.|
|**code** <span class="param-type">string</span> <br> An error code to find help for the exception.|
|**more_info** <span class="param-type">string</span> <br> The URL of BMatic's documentation for the error code.|
