
## Not Found

> Sample response:

```http
HTTP/1.1 404 Not Found
Content-Type: application/json

{
    "message": "Resource not found."
}
```

When a requested resource not found, a generic error message is returned.

<aside class="warning">
<strong>Caution:</strong>
If you obtain this type of error maybe you are request an invalid endpoint or the requested resource is not available anymore, please review the documentation of the operation invoked.
</aside>
