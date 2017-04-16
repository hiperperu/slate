
## Show branch details

> Sample request:

```http
GET /v1/branches/{branchId} HTTP/1.1
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
    "status": "OPEN",
    "isVirtual": true,
    "isBookable": true,
    "congestion": "MEDIUM",
    "lowEstimatedTime": 10,
    "highEstimatedTime": 14,
    "sectors": [
        {
            "id": "m8",
            "name": "Tower A",
            "shortName": "A",
            "status": "OPEN",
            "services": ["s9","s10","s30"]
        }
    ]
}
```

Returns a specific branch requested by ID.


### Endpoint

`GET /v1/branches/{branchId}`

### Path Params

* **branchId** *string* <span class="required-param">required</span> <br>Unique identifier of branch.

### Query Params

* **fields** *List\<String\>* <span class="recomended-param">recomended</span> <br> Entity fields that will return at response. For example: `fields=id,name,shortName`.

### Responses

* **200** <span class="verb-description">Ok</span> *[Branch](#the-branch-object)* <br>A branch.
* **404** <span class="verb-description">Not Found</span> *[Error](#the-error-object)* <br>The resource requested not found, returns a simple error message.
* **500** <span class="verb-description">Internal Server Error</span> *[Error](#the-error-object)* <br>An unexpected error has occurred, returns a description of the exception.
