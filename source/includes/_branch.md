
# Branch
## Get All Branches


> Sample request:

```http
GET /customer/v1/branches?status=open HTTP/1.1
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
        "status": "open",
        "opening_time": "2017-02-20T14:00:00.000Z",
        "closing_time": "2017-02-20T23:00:00.000Z",
        "low_estimated_time": 10,
        "high_estimated_time": 15,
        "congestion_level": "medium",
        "is_virtual": true,
        "is_bookable": true
    }
]
```

> Sample error responses:

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
    "message": "Invalid congestion level"
}
```
```http
HTTP/1.1 500 Internal Server Error
Content-Type: application/json

{
    "code": "ab90"
    "message": "An error has ocurred"
    "more_info": "https://bmatic.com/docs/errors/ab90"
}
```

Returns all branches that fulfill the filters. Support to getting of branches by the customer location. When the parameters longitude and latitude were recived, the branches are sorted by the better distance to client location and the branches in the page returned are sorted by the more short estimated waiting time; else the branches only are sorted by the more short estimated waiting time.

### HTTP Request
`GET /customer/v1/branches`

### Query Parameters
Name | Type | Description
--- | --- | ---
latitude | integer | Optional. Latitude component of customer location.
longitude | integer | Optional. Longitude component of customer location.
distance | integer | Optional. Maximum distance from the customer location to the branch, per example 1000 meters.
service_id | string | Optional. Unique identifier of service requested by customer.
is_virtual | boolean | Optional. Flag of virtual ticket enable for branch.
is_bookable | boolean | Optional. Flag of booking enable for branch.
status | string | Optional. Status of branch.
code | string | Optional. Unique identifier for the branch used in your company system.
fields | array[string] | Optional. Entity fields that will return at response.
offset | integer | Optional. Position in pagination. Default is zero.
limit | integer | Optional. Number of items to retrieve. Default is 10, maximum is 50.

### Responses
Http code | Type | Description
--- | --- | ---
200 | array[[Branch](#branch)] | A list of branches.
400 | [Error](#error) | Bad request.
500 | [Error](#error) | An error has occurred.


## Get Branch

```http
GET /v1/branches/{branch_id} HTTP/1.1
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": "string",
    "name": "string",
    "short_name": "string",
    "code": "string",
    "address": "string",
    "latitude": "number",
    "longitude": "number",
    "status": "string",
    "opening_time": "string",
    "closing_time": "string",
    "low_estimated_time": "integer",
    "high_estimated_time": "integer",
    "congestion_level": "string",
    "is_virtual": "boolean",
    "is_bookable": "boolean"
}
```
```http
HTTP/1.1 400 Bad Request
```
```http
HTTP/1.1 404 Not Found
```
```http
HTTP/1.1 500 Internal Server Error
```

Returns a specific branch requested by ID.


### Parameters
Name | In | Type | Description
--- | --- | --- | ---
branch_id<span title="required" class="required">&nbsp;*&nbsp;</span> | path | string | Unique identifier of branch.
fields | query | array[string] | Optional. Entity fields that will return at response.

### Responses
Http code | Type | Description
--- | --- | ---
200 | [Branch](#branch) | A branch.
400 | no content | Bad request.
404 | no content | Branch not found.
500 | no content | An error has occurred.


## Get All Sectors

```http
GET /v1/branches/{branch_id}/sectors HTTP/1.1
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "id": "string",
        "name": "string",
        "short_name": "string",
        "status": "string",
        "opening_time": "string",
        "closing_time": "string"
    }
]
```
```http
HTTP/1.1 400 Bad Request
```
```http
HTTP/1.1 404 Not Found
```
```http
HTTP/1.1 500 Internal Server Error
```

Returns all sectors of a specific branch that fulfill the filters. The sectors are sorted by their name.


### Parameters
Name | In | Type | Description
--- | --- | --- | ---
branch_id<span title="required" class="required">&nbsp;*&nbsp;</span> | path | string | Unique identifier of branch.
service_id | query | string | Optional. Unique identifier of service requested by customer.
status | query | string | Optional. Status of sector.
fields | query | array[string] | Optional. Entity fields that will return at response.
offset | query | integer | Optional. Position in pagination. Default is zero.
limit | query | integer | Optional. Number of items to retrieve. Default is 10, maximum is 50.

### Responses
Http code | Type | Description
--- | --- | ---
200 | array[[Sector](#sector)] | A list of sectors.
400 | no content | Bad request.
404 | no content | Non exists sectors that fulfill the filters.
500 | no content | An error has occurred.


## Get Sector

```http
GET /v1/branches/{branch_id}/sectors/{sector_id} HTTP/1.1
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": "string",
    "name": "string",
    "short_name": "string",
    "status": "string",
    "opening_time": "string",
    "closing_time": "string"
}
```
```http
HTTP/1.1 400 Bad Request
```
```http
HTTP/1.1 404 Not Found
```
```http
HTTP/1.1 500 Internal Server Error
```

Returns a specific sector of a branch.


### Parameters
Name | In | Type | Description
--- | --- | --- | ---
branch_id<span title="required" class="required">&nbsp;*&nbsp;</span> | path | string | Unique identifier of branch.
sector_id<span title="required" class="required">&nbsp;*&nbsp;</span> | path | string | Unique identifier of sector.
fields | query | array[string] | Optional. Entity fields that will return at response.

### Responses
Http code | Type | Description
--- | --- | ---
200 | [Sector](#sector) | A sector.
400 | no content | Bad request.
404 | no content | Sector not found.
500 | no content | An error has occurred.
