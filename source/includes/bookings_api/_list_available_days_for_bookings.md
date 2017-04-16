
## List available days for booking

> Sample request:

```http
GET /v1/bookings/availability/service/s8/branch/27b6 HTTP/1.1
```

> Sample response:

```http
HTTP/1.1 200 OK
X-Pagination-Count: 7
X-Pagination-Page: 3
X-Pagination-Limit: 1
Content-Type: application/json

[
    {
        "day": "2017-02-20T00:00:00.000Z",
        "ranges": [
            {
                "startTime": "2017-02-20T14:00:00.000Z",
                "endTime": "2017-02-20T15:00:00.000Z"
            }
        ]
    }
]
```

Returns a list of days for book a specific service in a branch.

<aside class="warning">
<strong>Caution: </strong> You should consider the following:
<ul>
<li>This operation throw a error(404) when the service or branch referenced not exists or not exists configuration of availability for the service and branch requested.</li>
<li>An empty list is returned when not exist more bookings availables.</li>
<ul>
</aside>

<aside class="notice">
<strong>Order:</strong> The booking days are sorted ascendantly by <code>day</code>.
</aside>

### Endpoint

`GET /v1/bookings/availability/service/{serviceId}/branch/{branchId}`

### Path Params

* **serviceId** <span class="param-type">String</span> <span title="required" class="required-param">required</span> <br> Service unique identifier.
* **branchId** <span class="param-type">String</span> <span title="required" class="required-param">required</span> <br> Branch unique identifier.

### Query Params

* **offset** <span class="param-type">Integer</span> <br> Position in pagination.<p>*Default value:* <code>0</code><br>*Maximum value:* <code>9999</code></p>
* **limit** <span class="param-type">Integer</span> <br> Number of items to retrieve.<p>*Default value:* <code>10</code><br>*Maximum value:* <code>50</code></p>

### Responses

* **200** <span class="verb-description">Ok</span> *List\<[Day](#day)\>* <br>A list of days. Pagination headers are included: <ul><li><strong>X-Pagination-Count:</strong> Total number of items.</li><li><strong>X-Pagination-Page:</strong> Number of current page.</li><li><strong>X-Pagination-Limit:</strong> Limit of items per page.</li></ul>
* **400** <span class="verb-description">Bad Request</span> *[ValidationError](#validation-error)* <br>One or more parameters are not valid, returns a description of validation failed.
* **404** <span class="verb-description">Not Found</span> <br>The resource requested not found, returns a simple error message.
* **500** <span class="verb-description">Internal Server Error</span> *[Error](#error)* <br>An unexpected error has occurred, returns a simple error message.
