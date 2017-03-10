
## List all branches

> Sample request:

```http
GET /customer/v1/branches?offset=9&limit=1 HTTP/1.1
```

> Sample success response:

```http
HTTP/1.1 200 OK
X-Pagination-Count: 32
X-Pagination-Page: 10
X-Pagination-Limit: 1
Content-Type: application/json

[
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
]
```

> Sample error responses:

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
    "message": "Invalid congestion level."
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

Returns all branches with their sectors that fulfill the filters.

<aside class="notice">
<strong>Order:</strong> The branches are sorted by the better distance to client location and the branches in the page returned are sorted by <code>low_estimated_time</code>. If the client location is not provided then the branches only are sorted by <code>low_estimated_time</code>.
</aside>

<aside class="success">
<strong>Remember:</strong> The customers prefer to attend the nearest branches,for that it is recommendable ever use the parameters <code>longitude</code>, <code>latitude</code>, <code>min_latitude</code>, <code>max_latitude</code>, <code>min_latitude</code> and <code>max_longitude</code>.
</aside>

### Endpoint

`GET /customer/v1/branches`

### Query Params

| |
|:---|
|**latitude** *float* <span class="recomended-param">recomended</span><br> Latitude component of customer location.|
|**longitude** *float* <span class="recomended-param">recomended</span><br> Longitude component of customer location. |
|**min_latitude** *float* <span class="recomended-param">recomended</span><br> Minimun latitude of the area that has to contain the branches.|
|**max_latitude** *float* <span class="recomended-param">recomended</span><br> Maximum latitude of the area that has to contain the branches.|
|**min_longitude** *float* <span class="recomended-param">recomended</span><br> Minimun longitude of the area that has to contain the branches. |
|**max_longitude** *float* <span class="recomended-param">recomended</span><br> Maximum longitude of the area that has to contain the branches. |
|**service_id** *string* <br>Unique identifier of service requested by customer.|
|**is_virtual** *boolean* <br> Flag of virtual ticket enable for branch. |
|**is_bookable** *boolean* <br> Flag of booking enable for branch. |
|**status** *enum* <br> Status of branch. Allowed values are `open` and `close`. |
|**code** *string* <br> Unique identifier for the branch used in your company system.|
|**fields** *array[string]* <span class="recomended-param">recomended</span> <br> Entity fields that will return at response. For example: `fields=id,name,short_name`. |
|**offset** *int* <br> Position in pagination. Default is `0`, maximum is `99999`.|
|**limit** *int* <br> Number of items to retrieve. Default is `10`, maximum is `50`.|

### Responses

| |
|:---|
|**200** *array[[Branch](#branch)]* <br>A list of branches. Pagination headers are included: <ul><li><strong>X-Pagination-Count:</strong> Total number of items.</li><li><strong>X-Pagination-Page:</strong> Number of the current page.</li><li><strong>X-Pagination-Limit:</strong> Number of items returned.</li></ul>|
|**400** *[Error](#error)* <br>Bad request. |
|**500** *[Error](#error)* <br>An error has occurred.|
