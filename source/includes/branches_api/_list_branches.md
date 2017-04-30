
## List branches

> Sample request:

```http
GET /v1/branches/branch?offset=9&limit=1 HTTP/1.1
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
]
```

Returns all branches with their sectors that fulfill the filters.

<aside class="warning">
<strong>Caution:</strong>
    You should consider the next:
    <ul>
        <li>The branches to return should to be marked with the flag <code>exposed by the API</code> from Bmatic configuration panel.</li>
        <li>An empty collection is returned when no branch fulfill the filters.</li>
        <li>Filter branches by geolocalization it is necessary to specify <code>minLatitude</code>, <code>maxLatitude</code>, <code>minLongitude</code> and <code>maxLongitude</code>. If any of these parameters is not included then all will be ignored.</li>
        <li>To order the branches by proximity to the client location it is necessary specify <code>latitude</code> and <code>longitude</code>. If any of these parameters is not included then all will be ignored.</li>
    </ul>
</aside>

<aside class="notice">
<strong>Order:</strong>
    Branches are sorted by the shorter distance to client location.
</aside>

<aside class="success">
<strong>Remember:</strong>
    Customers prefer to attend the nearest branches, for that it is recommendable ever use <code>longitude</code>, <code>latitude</code>, <code>minLatitude</code>, <code>maxLatitude</code>, <code>minLongitude</code> and <code>maxLongitude</code> parameters.
</aside>

### Endpoint

`GET /v1/branches/branch`

### Query Params

* **latitude** <span class="param-type">Float</span> <span class="recomended-param">recomended</span><br>
Latitude component of customer location.

* **longitude** <span class="param-type">Float</span> <span class="recomended-param">recomended</span><br>
Longitude component of customer location.

* **minLatitude** <span class="param-type">Float</span> <span class="recomended-param">recomended</span><br>
Minimum latitude of the geographic area that has to contain the branches.

* **maxLatitude** <span class="param-type">Float</span> <span class="recomended-param">recomended</span><br>
Maximum latitude of the geographic area that has to contain the branches.

* **minLongitude** <span class="param-type">Float</span> <span class="recomended-param">recomended</span><br>
Minimum longitude of the geographic area that has to contain the branches.

* **maxLongitude** <span class="param-type">Float</span> <span class="recomended-param">recomended</span><br>
Maximum longitude of the geographic area that has to contain the branches.

* **serviceId** <span class="param-type">String</span><br>
Unique identifier of service supported by the branch.

* **fields** <span class="param-type">List\<String\></span> <span class="recomended-param">recomended</span><br>
Entity fields that will included in the response. For example: `fields=id,name,shortName`.

* **offset** <span class="param-type">Integer</span><br>
Position in pagination.
<p>
    <span class="param-condition">Default value:</span> <code>0</code><br>
    <span class="param-condition">Maximum value:</span> <code>9999</code>
</p>

* **limit** <span class="param-type">Integer</span><br>
Number of items to retrieve.
<p>
    <span class="param-condition">Default value:</span> <code>10</code><br>
    <span class="param-condition">Maximum value:</span> <code>50</code>
</p>

### Responses

* **200** <span class="verb-description">Ok</span> <span class="param-type">List\<[Branch](#branch)\></span><br>
A list of branches. Pagination headers are included:
<ul>
    <li><strong>X-Pagination-Count:</strong> Total number of items.</li>
    <li><strong>X-Pagination-Page:</strong> Number of current page.</li>
    <li><strong>X-Pagination-Limit:</strong> Limit of items per page.</li>
</ul>

* **400** <span class="verb-description">Bad Request</span> <span class="param-type">[ValidationError](#validation-error)</span><br>
One or more parameters are not valid, returns a description of validation failed.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
