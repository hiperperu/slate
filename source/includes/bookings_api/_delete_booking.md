
## Delete booking

> Sample request:

```http
DELETE /customer/v1/bookings/a90mos70om HTTP/1.1
```

> Sample response:

```http
HTTP/1.1 204 No Content
```

Delete a customer booking by ID.


###Endpoint

`DELETE /customer/v1/bookings/{booking_id}`

### Path Params

| |
|:---|
|**booking_id** <span class="param-type">string</span> <span class="required-param">required</span> <br>Unique identifier of booking. |

### Responses

| |
|:---|
|**204** <span class="verb-description">No Content</span> <br>Successful deletion.|
|**404** <span class="verb-description">Not Found</span> <br>Booking not found. |
|**500** <span class="verb-description">Internal Server Error</span> *[Error](#error)* <br>An unexpected error has occurred, returns a description of the exception. |
