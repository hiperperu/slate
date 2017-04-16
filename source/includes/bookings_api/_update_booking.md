
## Update booking

> Sample request:

```http
PATCH /customer/v1/bookings/a90mos70om HTTP/1.1
Content-Type: application/json

{
    "phone": "+51908999189"
}
```

> Sample success response:

```http
HTTP/1.1 204 No Content
```

> Sample errors responses:

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
    "message": "Invalid phone number."
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

Update a specific customer booking.

###Endpoint

`PATCH /customer/v1/bookings/{booking_id}`

### Path Params

| |
|:---|
|**booking_id** *string* <span class="required-param">required</span> <br>Unique identifier of booking. For example `a90mos70om`.|

### Request

| |
|:---|
|**phone** *string* <br> New customer phone for notifications. |

### Responses

| |
|:---|
|**204** *no content* <br>Successful update.|
|**400** *[Error](#error)* <br>Bad request. |
|**404** *[Error](#error)* <br>Booking not found. |
|**500** *[Error](#error)* <br>An error has occurred.|
