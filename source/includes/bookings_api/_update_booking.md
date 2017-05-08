
## Update booking

> Sample request:

```http
PUT /v1/bookings/a90mos HTTP/1.1
Content-Type: application/json

{
    "phone": "+51908999189"
}
```

> Sample response:

```http
HTTP/1.1 204 No Content
```

Update a customer booking by ID.

###Endpoint

`PUT /v1/bookings/{booking_id}`

### Path Params

* **booking_id** <span class="param-type">String</span> <span class="required-param">required</span><br>
Booking unique identifier (Generated in the booking creation).

### Request

* **phone** <span class="param-type">String</span><br>
New customer phone for notifications.
<p>
    <span class="param-condition">Validation pattern:</span> `^\+[1-9]{1}[0-9]{3,14}$`
</p>

### Responses

* **204** <span class="verb-description">No Content</span><br>
Successful update.

* **400** <span class="verb-description">Bad Request</span> <span class="param-type">[Error](#error)</span><br>
One or more parameters are not valid, returns a description of validation failed.

* **404** <span class="verb-description">Not Found</span> <span class="param-type">[Error](#error)</span><br>
The resource requested not found, returns a simple error message.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
