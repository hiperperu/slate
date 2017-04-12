
## Get a booking

> Sample request:

```http
GET /customer/v1/bookings/a90mos70om HTTP/1.1
```

> Sample response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": "a90mos70om",
    "code": "UxMa01m",
    "channel": "mobile",
    "status": "ACTIVE",
    "phone": "+51987776576",
    "branch": {
        "id": "27b6",
        "name": "Hiper Central",
        "short_name": "Hiper",
        "code": "AG001",
        "address": "Calle Beta 181 - 195, Callao",
        "latitude": -12.049919,
        "longitude": -77.0845193,
        "status": "OPEN",
        "opening_time": "2017-02-20T14:00:00.000Z",
        "closing_time": "2017-02-20T23:00:00.000Z",
        "congestion_level": "MEDIUM"
    },
    "service": {
        "id": "7b6",
        "name": "Plataforma",
        "short_name": "Plataforma"
    },
    "start_time": "2017-02-20T14:00:00.000Z",
    "end_time": "2017-02-20T15:00:00.000Z",
    "created_at": "2017-02-10T14:00:00.000Z",
    "updated_at": "2017-02-10T14:00:00.000Z"
}
```

Returns a customer booking by ID.

### Endpoint

`GET /customer/v1/bookings/{booking_id}`

### Path Params

| |
|:---|
|**booking_id** <span class="param-type">string</span> <span class="required-param">required</span> <br>Unique identifier of booking. |

### Query Params

| |
|:---|
|**fields** <span class="param-type">array[string]</span> <span class="recomended-param">recomended</span> <br> Entity fields that will return at response. For example: `fields=id,queue,number`. |

### Responses

| |
|:---|
|**200** <span class="verb-description">OK</span> *[Booking](#booking)* <br>Booking found, returns the booking requested.|
|**400** <span class="verb-description">Bad request</span> *[Error](#error)* <br>One or more parameters are not valid, returns a description of validation failed. |
|**404** <span class="verb-description">Not Found</span> <br>Booking not found. |
|**500** <span class="verb-description">Internal Server Error</span>*[Error](#error)* <br>An unexpected error has occurred, returns a description of the exception.|
