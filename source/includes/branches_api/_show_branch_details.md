
## Show branch details

> Sample request:

```http
GET /v1/branches/{branch_id} HTTP/1.1
```

> Sample response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": "27b6",
    "name": "Hiper Central",
    "short_name": "Hiper",
    "address": "Calle Beta 181 - 195, Callao",
    "latitude": -12.049919,
    "longitude": -77.0845193,
    "status": "ACTIVE",
    "congestion": "MEDIUM",
    "low_estimated_time": 10,
    "high_estimated_time": 14,
    "sectors": [
        {
            "id": "m9",
            "name": "Tower A",
            "short_name": "A",
            "status": "ACTIVE"
        }
    ]
}
```

Returns a specific branch requested by ID.


### Endpoint

`GET /v1/branches/{branch_id}`

### Path Params

* **branch_id** <span class="param-type">String</span> <span class="required-param">required</span><br>
Branch unique identifier (Configured from Bmatic configuration panel).

### Query Params

* **fields** <span class="param-type">List\<String\></span> <span class="recomended-param">recomended</span><br>
Entity fields that will included in the response(See available fields in [the branch object definition](#branch)). For example: `fields=id,name,shortName`.

### Responses

* **200** <span class="verb-description">Ok</span> <span class="param-type">[Branch](#branch)</span><br>
A branch.

* **400** <span class="verb-description">Bad Request</span> <span class="param-type">[Error](#error)</span><br>
One or more parameters are not valid, returns a description of validation failed.

* **404** <span class="verb-description">Not Found</span> <span class="param-type">[Error](#error)</span><br>
The resource requested not found, returns a simple error message.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
