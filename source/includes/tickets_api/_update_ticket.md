
## Update ticket

> Sample request:

```http
PUT /v1/tickets/89m32b0 HTTP/1.1
Content-Type: application/json

{
    "status": "ENABLED"
}
```

> Sample response:

```http
HTTP/1.1 204 No Content
```

Update a customer ticket by ID.

###Endpoint

`PUT /v1/tickets/{ticket_id}`

### Path Params

* **ticket_id** <span class="param-type">String</span> <span class="required-param">required</span><br>
Ticket unique identifier (Generated in the ticket creation).

### Request

* **status** <span class="param-type">Enum</span><br>
New status for the ticket.
<p>
    <span class="param-condition">Possible values:</span>  
    <ul>
        <li><code>BLOCKED</code></li>
        <li><code>ENABLED</code></li>
    </ul>
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
