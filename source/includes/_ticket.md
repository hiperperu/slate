
# Ticket
## Get All Tickets

```http
GET /v1/tickets HTTP/1.1
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "id": "string"
    }
]
```
```http
HTTP/1.1 400 Bad Request
```
```http
HTTP/1.1 404 Not Found
```
```http
HTTP/1.1 500 Internal Server Error
```

Returns all tickets created by a specific customer, the tickets are sorted descendantly by the creation date.


### Parameters
Name | In | Type | Description
--- | --- | --- | ---
customer_id_type<span title="required" class="required">&nbsp;*&nbsp;</span> | query | string | Unique identifier of customer id type.
customer_id_number<span title="required" class="required">&nbsp;*&nbsp;</span> | query | string | Number of customer id.
fields | query | array[string] | Optional. Entity fields that will return at response.
offset | query | integer | Optional. Position in pagination. Default is zero.
limit | query | integer | Optional. Number of items to retrieve. Default is 10, maximum is 50.

### Responses
Http code | Type | Description
--- | --- | ---
200 | array[[Ticket](#ticket)] | A list of tickets.
400 | no content | Bad request.
404 | no content | Non exists tickets registered by the customer.
500 | no content | An error has occurred.

## Create Ticket

```http
POST /v1/tickets HTTP/1.1
```

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "id": "string"
}
```
```http
HTTP/1.1 400 Bad Request
```
```http
HTTP/1.1 500 Internal Server Error
```

Create a new customer ticket and then it returns it.


### Parameters
Name | In | Type | Description
--- | --- | --- | ---
channel<span title="required" class="required">&nbsp;*&nbsp;</span> | formData | string | Unique identifier of the channel used. This value is used to identify the type of device that consumes the API and should to be configured in administrative web of BMATIC.
branch_id<span title="required" class="required">&nbsp;*&nbsp;</span> | formData | string | Unique identifier of branch requested by customer.
sector_id<span title="required" class="required">&nbsp;*&nbsp;</span> | formData | string | Unique identifier of sector requested by customer.
service_id<span title="required" class="required">&nbsp;*&nbsp;</span> | formData | string | Unique identifier of service requested by customer.
customer_id_type | query | string | Optional. Unique identifier of customer id type.
customer_id_number | query | string | Optional. Number of customer id.
phone | formData | string | Optional. Customer phone for notifications.

### Responses
Http code | Type | Description
--- | --- | ---
201 | [Ticket](#ticket) | Successful creation.
400 | no content | Bad request.
500 | no content | An error has occurred.


## Get Ticket

```http
GET /v1/tickets/{ticket_id} HTTP/1.1
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": "string"
}
```
```http
HTTP/1.1 400 Bad Request
```
```http
HTTP/1.1 404 Not Found
```
```http
HTTP/1.1 500 Internal Server Error
```

Returns a customer ticket by ID.


### Parameters
Name | In | Type | Description
--- | --- | --- | ---
ticket_id<span title="required" class="required">&nbsp;*&nbsp;</span> | path | string | Unique identifier of ticket.
fields | query | array[string] | Optional. Entity fields that will return at response.

### Responses
Http code | Type | Description
--- | --- | ---
200 | [Ticket](#ticket) | A ticket.
400 | no content | Bad request.
404 | no content | Ticket not found.
500 | no content | An error has occurred.

## Update Ticket

```http
PUT /v1/tickets/{ticket_id} HTTP/1.1
```

```http
HTTP/1.1 204 No Content
```
```http
HTTP/1.1 400 Bad Request
```
```http
HTTP/1.1 404 Not Found
```
```http
HTTP/1.1 500 Internal Server Error
```

Update a specific customer ticket(At least one parameter must be sent).


### Parameters
Name | In | Type | Description
--- | --- | --- | ---
ticket_id<span title="required" class="required">&nbsp;*&nbsp;</span> | path | string | Unique identifier of ticket.
status | formData | string | Optional. Updated status of the ticket.
phone | formData | string | Optional. Updated of phone for notifications.

### Responses
Http code | Type | Description
--- | --- | ---
204 | no content | Successful update.
400 | no content | Bad request.
404 | no content | Ticket not found.
500 | no content | An error has occurred.

## Delete Ticket

```http
DELETE /v1/tickets/{ticket_id} HTTP/1.1
```

```http
HTTP/1.1 204 No Content
```
```http
HTTP/1.1 400 Bad Request
```
```http
HTTP/1.1 404 Not Found
```
```http
HTTP/1.1 500 Internal Server Error
```

Delete a customer ticket by ID.


### Parameters
Name | In | Type | Description
--- | --- | --- | ---
ticket_id<span title="required" class="required">&nbsp;*&nbsp;</span> | path | string | Unique identifier of ticket.

### Responses
Http code | Type | Description
--- | --- | ---
204 | no content | Successful deletion.
400 | no content | Bad request.
404 | no content | Ticket not found.
500 | no content | An error has occurred.
