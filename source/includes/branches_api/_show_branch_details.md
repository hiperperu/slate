
## Show branch details

> Sample request:

```http
GET /v1/branches/branch/{branchId} HTTP/1.1
```

> Sample response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": "27b6",
    "name": "Hiper Central",
    "shortName": "Hiper",
    "address": "Calle Beta 181 - 195, Callao",
    "latitude": -12.049919,
    "longitude": -77.0845193,
    "status": "ACTIVE",
    "congestion": "MEDIUM",
    "lowEstimatedTime": 10,
    "highEstimatedTime": 14,
    "sectors": [
        {
            "id": "m9",
            "name": "Tower A",
            "shortName": "A",
            "status": "ACTIVE",
            "services": ["s8", "s9", "s10", "s30"]
        }
    ]
}
```

Returns a specific branch requested by ID.


### Endpoint

`GET /v1/branches/branch/{branchId}`

### Path Params

* **branchId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Branch unique identifier (Configured from Bmatic configuration panel).

### Query Params

* **fields** <span class="param-type">List\<String\></span> <span class="recomended-param">recomended</span><br>
Entity fields that will return at response. For example: `fields=id,name,shortName`.

### Responses

* **200** <span class="verb-description">Ok</span> <span class="param-type">[Branch](#branch)</span><br>
A branch.

* **404** <span class="verb-description">Not Found</span> <span class="param-type">[Error](#error)</span><br>
The resource requested not found, returns a simple error message.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
