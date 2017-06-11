
## List customer bookings

> Sample request:

```http
GET /v1/bookings/?customer_id=c9mas9js HTTP/1.1
```

> Sample response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "id": "a90mos",
        "code": "UxMa01m",
        "status": "ACTIVE",
        "phone": "+51987882567",
        "channel": {
            "id": "c10",
            "name": "Mobile"
        },
        "branch": {
            "id": "27b6",
            "name": "Hiper Central",
            "short_name": "Hiper",
            "address": "Calle Beta 181 - 195, Callao",
            "latitude": -12.049919,
            "longitude": -77.0845193,
            "status": "ACTIVE"
        },
        "service": {
            "id": "s8",
            "name": "Plataforma",
            "short_name": "Plataforma"
        },
        "start_time": "2017-02-20T14:00:00.000Z",
        "end_time": "2017-02-20T15:00:00.000Z",
        "created_at": "2017-02-10T14:00:00.000Z"
    }
]
```

Returns all bookings created by a specific customer.

<aside class="warning">
    <strong>Caution:</strong>
    You must consider the following:
    <ul>
        <li>The bookings are not available anymore after the booking day.</li>
        <li>An empty list is returned when there is no registered bookings with the <code>customer_id</code> received.</li>
    <ul>
</aside>

<aside class="notice">
    <strong>Order:</strong>
    The bookings are sorted descendantly by the field: <code>created_at</code>.
</aside>

### Endpoint

`GET /v1/bookings/`

### Query Params

* **customer_id** <span class="param-type">String</span> <span class="required-param">required</span><br>
Customer unique identifier.

* **fields** <span class="param-type">List\<String\></span> <span class="recomended-param">recomended</span><br>
Entity fields that will included in the response(See available fields in [the booking object definition](#booking)). For example: `fields=id,code,status`.

### Responses

* **200** <span class="verb-description">Ok</span> <span class="param-type">List\<[Booking](#booking)\></span><br>
A list of bookings.

* **400** <span class="verb-description">Bad Request</span> <span class="param-type">[Error](#error)</span><br>
One or more parameters are not valid, returns a description of validation failed.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
