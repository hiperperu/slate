
## Update a ticket

> Sample request:

```http
PATCH /v1/tickets/89m32b0998 HTTP/1.1
Content-Type: application/json

{
    "status": "ENABLED"
}
```

> Sample success response:

```http
HTTP/1.1 204 No Content
```

> Sample error responses:

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
    "message": "Invalid status."
}
```
```http
HTTP/1.1 404 Not Found
Content-Type: application/json

{
    "message": "Ticket not found."
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

Update a specific customer ticket.

### Endpoint

`PATCH /customer/v1/tickets/{ticket_id}`

### Path Params

| |
|:---|
|**ticket_id** *string* <span class="required-param">required</span> <br>Unique identifier of ticket. For example `89m32b0998`.|

### Request

| |
|:---|
|**status** *enum* <br> New status for the ticket. Possible values are `BLOCKED` and `ENABLED`. |
|**phone** *string* <br> New customer phone for notifications. |

### Responses

| |
|:---|
|**204** *no content* <br>Successful update.|
|**400** *[Error](#error)* <br>Bad request. |
|**404** *[Error](#error)* <br>Ticket not found. |
|**500** *[Error](#error)* <br>An error has occurred.|
