
## Update booking

> Sample request:

```http
PUT /v1/bookings/customer/c9mas9js/bookings/a90mos70om HTTP/1.1
Content-Type: application/json

{
    "phone": "+51908999189"
}
```

> Sample response:

```http
HTTP/1.1 204 No Content
```

Update a specific customer booking.

###Endpoint

`PUT /v1/bookings/customer/{customerId}/bookings/{bookingId}`

### Path Params

* **customerId** <span class="param-type">String</span> <span class="required-param">required</span> <br> Customer unique identifier.
* **bookingId** <span class="param-type">String</span> <span class="required-param">required</span> <br>Unique identifier of booking.

### Request

* **phone** <span class="param-type">String</span> <br> New customer phone for notifications. <p><span class="param-condition">Validation pattern: </span>`^+[1-9]{1}[0-9]{3,14}$`</p>

### Responses

* **204** *no content* <br>Successful update.
* **400** <span class="verb-description">Bad Request</span> *[ValidationError](#validation-error)* <br>One or more parameters are not valid, returns a description of validation failed.
* **404** <span class="verb-description">Not Found</span> *[Error](#error)* <br>The resource requested not found, returns a simple error message.
* **500** <span class="verb-description">Internal Server Error</span> *[Error](#error)* <br>An unexpected error has occurred, returns a simple error message.
