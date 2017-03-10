
## List all services

> Sample request:

```http
GET /customer/v1/services HTTP/1.1
```

> Sample success response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "id": "7b6",
        "name": "Plataforma",
        "short_name": "Plataforma"
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

{
    "message": "An error has ocurred.",
    "code": "ab90",
    "more_info": "https://bmatic.com/docs/errors/ab90"
}
```

Returns all available services that fulfill the filters.

<aside class="notice">
<strong>Order:</strong> The services are sorted by <code>short_name</code>.
</aside>

### Endpoint

`GET /customer/v1/services`

### Query Params

| |
|:---|
|**branch_id** *string* <br>Unique identifier of branch.|
|**sector_id** *string* <br>Unique identifier of sector.|
|**fields** *array[string]* <span class="recomended-param">recomended</span> <br> Entity fields that will return at response. For example: `fields=id,short_name`. |
|**offset** *int* <br> Position in pagination. Default is `0`, maximum is `99999`.|
|**limit** *int* <br> Number of items to retrieve. Default is `10`, maximum is `50`.|

### Responses

| |
|:---|
|**200** *array[[Branch](#branch)]* <br>A list of services. Pagination headers are included: <ul><li><strong>X-Pagination-Count:</strong> Total number of items.</li><li><strong>X-Pagination-Page:</strong> Number of the current page.</li><li><strong>X-Pagination-Limit:</strong> Number of items returned.</li></ul>|
|**400** *[Error](#error)* <br>Bad request. |
|**500** *[Error](#error)* <br>An error has occurred.|
