
## List all branch sectors

> Sample request:

```http
GET /v1/branches/{branch_id}/sectors?service_id=s9 HTTP/1.1
```

> Sample success response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "id": "s8",
        "name": "Tower A",
        "short_name": "A",
        "status": "OPEN",
        "services": ["s9","s10","s30"]
    }
]
```

> Sample error responses:

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
    "message": "Requested field not found."
}
```
```http
HTTP/1.1 500 Internal Server Error
Content-Type: application/json
uccess response
{
    "message": "An error has ocurred.",
    "code": "ab90",
    "more_info": "https://bmatic.com/docs/errors/ab90"
}
```

Returns all sectors of a specific branch that fulfill the filters.

<aside class="notice">
<strong>Order:</strong> The sectors are sorted by <code>short_name</code>.
</aside>

### Endpoint

`GET /customer/v1/branches/{branch_id}/sectors`

### Path params

| |
|:---|
|**branch_id** *string* <span class="required-param">required</span> <br>Unique identifier of branch. For example `27b6`.|

### Query Params

| |
|:---|
|**service_id** *string* <br>Unique identifier of service requested by customer.|
|**fields** *array[string]* <span class="recomended-param">recomended</span> <br> Entity fields that will return at response. For example: `fields=id,name,short_name`. |

### Responses

| |
|:---|
|**200** *array[[Sector](#sector)]* <br>A list of sectors.|
|**400** *[Error](#error)* <br>Bad request. |
|**500** *[Error](#error)* <br>An error has occurred.|
