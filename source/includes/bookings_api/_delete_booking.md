
## Delete booking

> Sample request:

```http
DELETE /v1/bookings/customer/c9mas9js/bookings/a90mos HTTP/1.1
```

> Sample response:

```http
HTTP/1.1 204 No Content
```

Delete a customer booking by ID.

<aside class="warning">
<strong>Caution: </strong> You should consider the following before delete a booking:
<ul>
<li>The booking to delete should to be in state <code>ACTIVE</code> or <code>PENDING</code>.</li>
<ul>
</aside>

###Endpoint

`DELETE /v1/bookings/customer/{customerId}/bookings/{bookingId}`

### Path Params

* **customerId** <span class="param-type">String</span> <span class="required-param">required</span> <br>Customer unique identifier.
* **bookingId** <span class="param-type">String</span> <span class="required-param">required</span> <br>Booking unique identifier.

### Responses

* **204** <span class="verb-description">No Content</span> <br>Successful deletion.
* **400** <span class="verb-description">Bad Request</span> *[ValidationError](#validation-error)* <br>One or more parameters are not valid, returns a description of validation failed.
* **404** <span class="verb-description">Not Found</span> <br>The resource requested not found, returns a simple error message.
* **500** <span class="verb-description">Internal Server Error</span> *[Error](#error)* <br>An unexpected error has occurred, returns a simple error message.
