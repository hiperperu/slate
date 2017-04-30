
## Cancel ticket

> Sample request:

```http
DELETE /v1/tickets/customer/c9mas9js/tickets/89m32b0 HTTP/1.1
```

> Sample response:

```http
HTTP/1.1 204 No Content
```

Cancel a customer ticket by ID.

### Endpoint

`DELETE /v1/tickets/customer/{customerId}/tickets/{ticketId}`

### Path Params

* **customerId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Customer unique identifier.

* **ticketId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Ticket unique identifier (Generated in the ticket creation).

### Responses

* **204** <span class="verb-description">No Content</span><br>
Successful cancelation.

* **400** <span class="verb-description">Bad Request</span> <span class="param-type">[Error](#error)</span><br>
One or more parameters are not valid, returns a description of validation failed.

* **404** <span class="verb-description">Not Found</span> <span class="param-type">[Error](#error)</span><br>
The resource requested not found, returns a simple error message.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
