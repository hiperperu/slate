
## Show booking details

> Sample request:

```http
GET /v1/bookings/customer/c9mas9js/bookings/a90mos HTTP/1.1
```

> Sample response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

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
```

Returns a customer booking by ID.

### Endpoint

`GET /v1/bookings/customer/{customerId}/bookings/{bookingId}`

### Path Params

* **customerId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Customer unique identifier (Obtained it from the customers integration interface).

* **bookingId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Booking unique identifier (Generated in the booking creation).

### Query Params

* **fields** <span class="param-type">List\<String\></span> <span class="recomended-param">recomended</span><br>
Entity fields that will return at response. For example: `fields=id,code,status`.

### Responses

* **200** <span class="verb-description">OK</span> <span class="param-type">[Booking](#booking)</span><br>
A booking.

* **404** <span class="verb-description">Not Found</span> <span class="param-type">[Error](#error)</span><br>
The resource requested not found, returns a simple error message.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
