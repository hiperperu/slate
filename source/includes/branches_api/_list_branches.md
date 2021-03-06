
## List branches

> Sample request:

```http
GET /v1/branches/?offset=9&limit=1 HTTP/1.1
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
]
```

Returns all branches with their sectors that fulfill the filters.

<aside class="warning">
    <strong>Caution:</strong>
    You must consider the next:
    <ul>
        <li>An empty collection is returned when no branch fulfill the filters.</li>
        <li>To filter branches by geolocalization it is necessary to specify <code>min_latitude</code>, <code>max_latitude</code>, <code>min_longitude</code> and <code>max_longitude</code>. If any of these parameters is not included then all will be ignored.</li>
        <li>To sort branches by proximity to the client location it is necessary specify <code>latitude</code> and <code>longitude</code>. If any of these parameters is not included then all will be ignored.</li>
    </ul>
</aside>

<aside class="notice">
    <strong>Order:</strong>
    Branches are sorted by the shorter distance to client location and their short name.
</aside>

<aside class="success">
    <strong>Remember:</strong>
    Customers prefer to attend the nearest branches, so it is recommendable to use <code>longitude</code>, <code>latitude</code>, <code>min_latitude</code>, <code>max_latitude</code>, <code>min_longitude</code> and <code>max_longitude</code> parameters.
</aside>

### Endpoint

`GET /v1/branches/`

### Query Params

* **latitude** <span class="param-type">Float</span> <span class="recomended-param">recomended</span><br>
Latitude component of customer location.

* **longitude** <span class="param-type">Float</span> <span class="recomended-param">recomended</span><br>
Longitude component of customer location.

* **min_latitude** <span class="param-type">Float</span> <span class="recomended-param">recomended</span><br>
Minimum latitude of the geographic area that has to contain the branches.

* **max_latitude** <span class="param-type">Float</span> <span class="recomended-param">recomended</span><br>
Maximum latitude of the geographic area that has to contain the branches.

* **min_longitude** <span class="param-type">Float</span> <span class="recomended-param">recomended</span><br>
Minimum longitude of the geographic area that has to contain the branches.

* **max_longitude** <span class="param-type">Float</span> <span class="recomended-param">recomended</span><br>
Maximum longitude of the geographic area that has to contain the branches.

* **fields** <span class="param-type">List\<String\></span> <span class="recomended-param">recomended</span><br>
Entity fields that will included in the response(See available fields in [the branch object definition](#branch)). For example: `fields=id,name,short_name`.

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

* **400** <span class="verb-description">Bad Request</span> <span class="param-type">[Error](#error)</span><br>
One or more parameters are not valid, returns a description of validation failed.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
