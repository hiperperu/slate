
## List customer bookings

> Sample request:

```http
GET /v1/bookings/customer/c9mas9js/bookings HTTP/1.1
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
            "shortName": "Hiper",
            "address": "Calle Beta 181 - 195, Callao",
            "latitude": -12.049919,
            "longitude": -77.0845193,
            "status": "ACTIVE"
        },
        "service": {
            "id": "s8",
            "name": "Plataforma",
            "shortName": "Plataforma"
        },
        "startTime": "2017-02-20T14:00:00.000Z",
        "endTime": "2017-02-20T15:00:00.000Z",
        "createdAt": "2017-02-10T14:00:00.000Z",
        "updatedAt": "2017-02-10T14:00:00.000Z"
    }
]
```

Returns all bookings created by a specific customer.

<aside class="warning">
<strong>Caution:</strong>
You should consider the following:
<ul>
    <li>The bookings are not available anymore after the booking day.</li>
    <li>An empty list is returned when not exist registered bookings with the <code>customerId</code> received.</li>
<ul>
</aside>

<aside class="notice">
<strong>Order:</strong>
The bookings are sorted descendantly by the field: <code>createdAt</code>.
</aside>

### Endpoint

`GET /v1/bookings/customer/{customerId}/bookings`

### Path Params

* **customerId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Customer unique identifier (Obtained it from the customers integration interface).

### Query Params

* **fields** <span class="param-type">List\<String\></span> <span class="recomended-param">recomended</span><br>
Entity fields that will return at response. For example: `fields=id,code,status`.

### Responses

* **200** <span class="verb-description">Ok</span> <span class="param-type">List\<[Booking](#booking)\></span><br>
A list of bookings.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
