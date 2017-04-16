
## List available days for booking

> Sample request:

```http
GET /v1/bookings/days?branch_id=27b6&service_id=7b6 HTTP/1.1
```

> Sample success response:

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
                "start_time": "2017-02-20T14:00:00.000Z",
                "end_time": "2017-02-20T15:00:00.000Z"
            }
        ]
    }
]
```

> Sample error responses:

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
    "message": "Invalid branch ID."
}
```
```http
HTTP/1.1 500 Internal Server Error
Content-Type: application/json

{
    "message": "An error has ocurred.",
    "code": "ab90",
    "more_info": "https://bmatic.com/docs/errors/ab90"
}
```

Returns a list of days for book a specific service in a branch.

<aside class="notice">
<strong>Order:</strong> The booking days are sorted ascendantly by  <code>day</code>.
</aside>

### Endpoint

`GET /customer/v1/bookings/days`

### Query Params

| |
|:---|
|**branch_id** *string* <span title="required" class="required-param">required</span> <br> Unique identifier of branch requested.|
|**service_id** *string* <span title="required" class="required-param">required</span> <br> Unique identifier of service requested.|
|**offset** *int* <br> Position in pagination. Default is `0`, maximum is `99999`.|
|**limit** *int* <br> Number of items to retrieve. Default is `10`, maximum is `50`.|

### Responses

| |
|:---|
|**200** *array[[Booking](#booking-day-object)]* <br>A list of booking days. Pagination headers are included: <ul><li><strong>X-Pagination-Count:</strong> Total number of items.</li><li><strong>X-Pagination-Page:</strong> Number of the current page.</li><li><strong>X-Pagination-Limit:</strong> Number of items returned.</li></ul>|
|**400** *[Error](#error)* <br>Bad request. |
|**500** *[Error](#error)* <br>An error has occurred.|
