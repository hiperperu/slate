
# Service
## Get All Services

```http
GET /v1/services HTTP/1.1
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "id": "string",
        "name": "string",
        "short_name": "string"
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

Returns all available services that fulfill the filters. The services are sorted by their name.


### Parameters
Name | In | Type | Description
--- | --- | --- | ---
branch_id | query | string | Optional. Unique identifier of branch.
sector_id | query | string | Optional. Unique identifier of sector.
fields | query | array[string] | Optional. Entity fields that will return at response.
offset | query | integer | Optional. Position in pagination. Default is zero.
limit | query | integer | Optional. Number of items to retrieve. Default is 10, maximum is 50.

### Responses
Http code | Type | Description
--- | --- | ---
200 | array[[Service](#service)] | A list of services.
400 | no content | Bad request.
404 | no content | Non exists available services that fulfill the filters.
500 | no content | An error has occurred.


## Get Service

```http
GET /v1/services/{service_id} HTTP/1.1
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": "string",
    "name": "string",
    "short_name": "string"
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

Returns a specific service requested by ID.


### Parameters
Name | In | Type | Description
--- | --- | --- | ---
service_id<span title="required" class="required">&nbsp;*&nbsp;</span> | path | string | Unique identifier of service.
fields | query | array[string] | Optional. Entity fields that will return at response.

### Responses
Http code | Type | Description
--- | --- | ---
200 | [Service](#service) | A service.
400 | no content | Bad request.
404 | no content | Service not found.
500 | no content | An error has occurred.
