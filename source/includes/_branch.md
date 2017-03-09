
# Branch

Before you create tickets or bookings, you need a branch and sector provided by the endpoints of this section (The bookings creation not required a sector). You considere use the recomended parameters for obtain a better performance in your application.

## Branch Object

> Sample object:

```json
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

Model of branch object.

<aside class="warning">
<strong>Caution:</strong> The fields <code>low_estimated_time</code>, <code>high_estimated_time</code> and <code>congestion_level</code> are undefined when the branch is closed.
</aside>

### Fields

| |
|:---|
|**id** *string* <br>Branch unique identifier. <p>*Validation pattern*: <code>^[0-9a-z]{2,6}$</code></p> |
|**name** *string* <br>Complete name of the branch. <p>*Maximum length*: <code>120</code></p> |
|**short_name** *string* <br>Name to display in small devices. <p>*Maximum length*: <code>20</code></p> |
|**code** *string* <br>Unique identifier for the branch used in your company system. *Validation pattern*: <code>^[0-9A-Za-z]{1,16}$</code> |
|**address** *string* <br>Address of the branch. <p>*Maximum length*: <code>100</code></p> |
|**latitude** *float* <br>Latitude component of branch location. <p>*Range of values*: <code> -90 ≤ latitude ≤ 90</code></p> |
|**longitude** *float* <br>Longitude component of branch location. <p>*Range of values*: <code> -90 ≤ longitude ≤ 90</code></p> |
|**status** *enum* <br>Current status of the branch. <p>*Possible values*: <ul><li><code>OPEN</code></li><li><code>CLOSE</code></li></ul></p> |
|**opening_time** *date-time* <br>Opening time of the branch at current day, or next opening datetime. <p>*Standard*: <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p> |
|**closing_time** *date-time* <br>Closing time of the branch at current day, or next closing datetime. <p>*Standard*: <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p>  |
|**low_estimated_time** *integer* <br> Lower bound of the estimated waiting time. <p>*Minimun:* <code>0</code></p>|
|**high_estimated_time** *integer* <br> Upper bound of the estimated waiting time. <p>*Minimun:* <code>0</code></p>|
|**congestion_level** *enum* <br> Congestion level of the branch. <p>*Possible values*: <ul><li><code>LOW</code></li><li><code>MEDIUM</code></li><li><code>HIGH</code></li></ul></p>|
|**is_virtual** *boolean* <br> Indicator of the possibility to create virtual tickets.|
|**is_bookable** *boolean* <br>Indicator of the possibility to bookings.|
|**sectors** *array[[Sector](#sector)]* <br> List of the branch's sectors.<p>*Unique items:* <code>true</code><br>*Minimun items:* <code>1</code></p>|

## Sector Object

Model of sector object.

> Sample object:

```json
{
    "id": "s8",
    "name": "Tower A",
    "short_name": "A",
    "status": "OPEN",
    "services": ["s9","s10","s30"]
}
```

### Fields

| |
|:---|
|**id** *string* <br>Sector unique identifier. <p>*Validation pattern*: <code>^[0-9a-z]{2,6}$</code></p> |
|**name** *string* <br>Complete name of the sector. <p>*Maximum length*: <code>120</code></p> |
|**short_name** *string* <br>Name to display in small devices. <p>*Maximum length*: <code>20</code></p> |
|**status** *enum* <br>Current status of the sector. <p>*Possible values*: <ul><li><code>OPEN</code></li><li><code>CLOSE</code></li></ul></p> |
|**services** *array[string]* <br> List of ids of the services allowed at sector.<p>*Unique items:* <code>true</code><br>*Minimun items:* <code>1</code></p>|


## Get All Branches

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


## Get Branch

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


## Get Branch Sectors

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
