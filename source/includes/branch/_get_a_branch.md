
## Get a branch

> Sample request:

```http
GET /customer/v1/branches/{branch_id} HTTP/1.1
```

> Sample success response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": "27b6",
    "name": "Hiper Central",
    "short_name": "Hiper",
    "code": "AG001",
    "address": "Calle Beta 181 - 195, Callao",
    "latitude": -12.049919,
    "longitude": -77.0845193,
    "status": "OPEN",
    "opening_time": "2017-02-20T14:00:00.000Z",
    "closing_time": "2017-02-20T23:00:00.000Z",
    "low_estimated_time": 10,
    "high_estimated_time": 15,
    "congestion_level": "MEDIUM",
    "is_virtual": true,
    "is_bookable": true,
    "sectors": [
        {
            "id": "s8",
            "name": "Tower A",
            "short_name": "A",
            "status": "OPEN",
            "services": ["s9","s10","s30"]
        }
    ]
}
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
HTTP/1.1 404 Not Found
Content-Type: application/json

{
    "message": "Branch not found."
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

Returns a specific branch requested by ID.


### Endpoint

`GET /customer/v1/branches/{branch_id}`

### Path Params

| |
|:---|
|**branch_id** *string* <span class="required-param">required</span> <br>Unique identifier of branch. For example `27b6`.|

### Query Params

| |
|:---|
|**fields** *array[string]* <span class="recomended-param">recomended</span> <br> Entity fields that will return at response. For example: `fields=id,name,short_name`. |

### Responses

| |
|:---|
|**200** *[Branch](#branch)* <br>A branch.|
|**400** *[Error](#error)* <br>Bad request. |
|**404** *[Error](#error)* <br>Branch not found. |
|**500** *[Error](#error)* <br>An error has occurred.|
