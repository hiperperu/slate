
## Cancel booking

> Sample request:

```http
DELETE /v1/bookings/customer/c9mas9js/bookings/a90mos HTTP/1.1
```

> Sample response:

```http
HTTP/1.1 204 No Content
```

Cancel a customer booking by ID.

###Endpoint

`DELETE /v1/bookings/customer/{customerId}/bookings/{bookingId}`

### Path Params

* **customerId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Customer unique identifier (Obtained it from the customers integration interface).

* **bookingId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Booking unique identifier (Generated in the booking creation).

### Responses

* **204** <span class="verb-description">No Content</span><br>
Successful cancelation.

* **400** <span class="verb-description">Bad Request</span> <span class="param-type">List\<[ValidationError](#validation-error)\></span><br>
One or more parameters are not valid, returns a description of validation failed.

* **404** <span class="verb-description">Not Found</span> <span class="param-type">[Error](#error)</span><br>
The resource requested not found, returns a simple error message.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
