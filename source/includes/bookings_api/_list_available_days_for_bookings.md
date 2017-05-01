
## List available days for booking

> Sample request:

```http
GET /v1/bookings/availability?serviceId=s8&branchId=27b6 HTTP/1.1
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

Returns a list of days for book a service in a branch.

<aside class="warning">
    <strong>Caution: </strong> 
    You must consider the following:
    <ul>
        <li>An empty list is returned when there are no more bookings available or there is no availability setting for the requested service and branch.</li>
    <ul>
</aside>

<aside class="notice">
    <strong>Order:</strong>
    The booking days are sorted ascendantly by <code>day</code>.
</aside>

### Endpoint

`GET /v1/bookings/availability`

### Query Params

* **serviceId** <span class="param-type">String</span> <span title="required" class="required-param">required</span><br>
Unique identifier of requested service.

* **branchId** <span class="param-type">String</span> <span title="required" class="required-param">required</span><br>
Unique identifier of requested branch.

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

* **200** <span class="verb-description">Ok</span> <span class="param-type">List\<[Day](#day)\></span><br>
A list of days. Pagination headers are included:
<ul>
    <li><strong>X-Pagination-Count:</strong> Total number of items.</li>
    <li><strong>X-Pagination-Page:</strong> Number of current page.</li>
    <li><strong>X-Pagination-Limit:</strong> Limit of items per page.</li>
</ul>

* **400** <span class="verb-description">Bad Request</span> <span class="param-type">[Error](#error)</span><br>
One or more parameters are not valid, returns a description of validation failed.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
