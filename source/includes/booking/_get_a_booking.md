
## Get a booking

> Sample request:

```http
GET /v1/bookings/a90mos70om HTTP/1.1
```

> Sample success response:

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

> Sample error responses:

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
    "message": "Requested field not found."
}
```
```http
HTTP/1.1 404 Not Found
Content-Type: application/json

{
    "message": "Booking not found."
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

Returns a customer booking by ID.

### Endpoint

`GET /customer/v1/bookings/{booking_id}`

### Path Params

| |
|:---|
|**booking_id** *string* <span class="required-param">required</span> <br>Unique identifier of Booking. For example `a90mos70om`.|

### Query Params

| |
|:---|
|**fields** *array[string]* <span class="recomended-param">recomended</span> <br> Entity fields that will return at response. For example: `fields=id,queue,number`. |

### Responses

| |
|:---|
|**200** *[Booking](#booking)* <br>A booking.|
|**400** *[Error](#error)* <br>Bad request. |
|**404** *[Error](#error)* <br>Booking not found. |
|**500** *[Error](#error)* <br>An error has occurred.|
