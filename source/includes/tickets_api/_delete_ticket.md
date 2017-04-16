
## Delete ticket

> Sample request:

```http
DELETE /v1/tickets/customer/c9mas9js/tickets/89m32b0 HTTP/1.1
```

> Sample response:

```http
HTTP/1.1 204 No Content
```

Delete a customer ticket by ID.

### Endpoint

`DELETE /v1/tickets/customer/{customerId}/tickets/{ticketId}`

### Path Params

* **customerId** <span class="param-type">String</span> <span class="required-param">required</span> <br>Customer unique identifier.
* **ticketId** <span class="param-type">String</span> <span class="required-param">required</span> <br>Ticket unique identifier.

### Responses

* **204** <span class="verb-description">No Content</span> <br>Successful deletion.
* **400** <span class="verb-description">Bad Request</span> *[ValidationError](#validation-error)* <br>One or more parameters are not valid, returns a description of validation failed.
* **404** <span class="verb-description">Not Found</span> <br>The resource requested not found, returns a simple error message.
* **500** <span class="verb-description">Internal Server Error</span> *[Error](#error)* <br>An unexpected error has occurred, returns a simple error message.
