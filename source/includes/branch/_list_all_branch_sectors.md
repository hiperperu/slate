
## List all branch sectors

> Sample request:

```http
GET /v1/branches/{branchId}/sectors?serviceId=s9 HTTP/1.1
```

> Sample response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "id": "m8",
        "name": "Tower A",
        "shortName": "A",
        "status": "OPEN",
        "services": ["s9","s10","s30"]
    }
]
```

Returns all sectors of a specific branch that fulfill the filters.

### Endpoint

`GET /v1/branches/{branchId}/sectors`

### Path params

* **branchId** *String* <span class="required-param">required</span> <br>Unique identifier of branch. For example `27b6`.

### Query Params

* **serviceId** *String* <br>Unique identifier of service requested by customer.
* **fields** *List\<String\>* <span class="recomended-param">recomended</span> <br> Entity fields that will return at response. For example: `fields=id,name,shortName`.

### Responses

* **200** <span class="verb-description">Ok</span> *List\<[Sector](#the-sector-object)\>* <br>A list of sectors.s
* **400** <span class="verb-description">Bad Request</span> *[Error](#the-error-object)* <br>One or more parameters are not valid, returns a description of validation failed.
* **500** <span class="verb-description">Internal Server Error</span> *[Error](#the-error-object)* <br>An unexpected error has occurred, returns a description of the exception.
