
## List branches

> Sample request:

```http
GET /v1/branches?offset=9&limit=1 HTTP/1.1
```

> Sample response:

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
]
```

Returns all branches with their sectors that fulfill the filters.

<aside class="notice">
<strong>Order:</strong> The branches are sorted by the better distance to client location and then by its shortName.
</aside>

<aside class="success">
<strong>Remember:</strong> The customers prefer to attend the nearest branches, for that it is recommendable ever use the parameters <code>longitude</code>, <code>latitude</code>, <code>minLatitude</code>, <code>maxLatitude</code>, <code>minLongitude</code> and <code>maxLongitude</code>.
</aside>

### Endpoint

`GET /v1/branches/branch`

### Query Params

* **latitude** *Float* <span class="recomended-param">recomended</span><br> Latitude component of customer location.
* **longitude** *Float* <span class="recomended-param">recomended</span><br> Longitude component of customer location.
* **minLatitude** *Float* <span class="recomended-param">recomended</span><br> Minimun latitude of the area that has to contain the branches.
* **maxLatitude** *Float* <span class="recomended-param">recomended</span><br> Maximum latitude of the area that has to contain the branches.
* **minLongitude** *Float* <span class="recomended-param">recomended</span><br> Minimun longitude of the area that has to contain the branches.
* **maxLongitude** *Float* <span class="recomended-param">recomended</span><br> Maximum longitude of the area that has to contain the branches.
* **serviceId** *String* <br>Unique identifier of service requested by customer.
* **status** *Enum* <br> Current status of branch. <p>*Possible values*: <ul><li><code>ACTIVE</code></li><li><code>INACTIVE</code></li></ul></p>
* **fields** *List\<String\>* <span class="recomended-param">recomended</span> <br> Entity fields that will return at response. For example: `fields=id,name,shortName`.
* **offset** *Integer* <br> Position in pagination.<p>*Default value:* <code>0</code><br>*Maximum value:* <code>9999</code></p>
* **limit** *Integer* <br> Number of items to retrieve.<p>*Default value:* <code>10</code><br>*Maximum value:* <code>50</code></p>

### Responses

* **200** <span class="verb-description">Ok</span> *List\<[Branch](#branch)\>* <br>A list of branches. Pagination headers are included: <ul><li><strong>X-Pagination-Count:</strong> Total number of items.</li><li><strong>X-Pagination-Page:</strong> Number of current page.</li><li><strong>X-Pagination-Limit:</strong> Limit of items per page.</li></ul>
* **400** <span class="verb-description">Bad Request</span> *[Error](#the-error-object)* <br>One or more parameters are not valid, returns a description of validation failed.
* **500** <span class="verb-description">Internal Server Error</span> *[Error](#the-error-object)* <br>An unexpected error has occurred, returns a description of the exception.
