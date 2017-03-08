
# Ticket

Your customers don't need anymore to be at branch for create attention tickets. You can use the endpoints of this section to allow them the ticket creation from anywhere easily, before the creation is necesary determine the branch, sector and service for the ticket.

## Ticket Object

> Sample Object:

```json
{
    "id": "89m32b0998",
    "queue": "T",
    "number": 2,
    "channel": "mobile",
    "status": "BLOCKED",
    "low_estimated_time": "10",
    "high_estimated_time": "15",
    "phone": "+51987776576",
    "messages":[
        "We have a promotion for you!"
    ],
    "branch": {
        "id": "27b6",
        "name": "Hiper Central",
        "short_name": "Hiper",
        "code": "AG001",
        "address": "Calle Beta 181 - 195, Callao",
        "latitude": -12.049919,
        "longitude": -77.0845193,
        "status": "OPEN",
        "opening_time": "2017-02-20T14:00:00.000Z",
        "closing_time": "2017-02-20T23:00:00.000Z",
        "congestion_level": "MEDIUM"
    },
    "sector": {
        "id": "s8",
        "name": "Tower A",
        "short_name": "A",
        "status": "OPEN"
    },
    "service": {
        "id": "7b6",
        "name": "Plataforma",
        "short_name": "Plataforma"
    },
    "created_at": "2017-02-20T10:00:00.000Z",
    "updated_at": "2017-02-20T10:00:00.000Z"
}
```

Model of ticket object.

<aside class="warning">
<strong>Caution:</strong> The entities associated to ticket not provide all their fields for performance reasons. If you need more information, you can use others endpoints to get this information using the ids returned in the ticket. You can to see the default information provided in the sample object.
</aside>

### Fields

| |
|:---|
|**id** *string* <br>Ticket unique identifier. <p>*Validation pattern*: <code>^[0-9a-z]{8,16}$</code></p> |
|**queue** *string* <br>Id of queue assigned to ticket. <p>*Validation pattern*: <code>^[0-9a-zA-Z]{1,4}$</code> |
|**number** *integer* <br>Position of ticket in queue. <p>*Minimun*: <code>1</code><br> *Maximum*: <code>9999</code></p> |
|**channel** *string* <br>Code of channel used. <p>*Maximum length*: <code>20</code></p> |
|**status** *enum* <br>Current status of the branch. <p>*Possible values*: <ul><li><code>BLOCKED</code></li><li><code>ENABLED</code></li></ul></p> |
|**low_estimated_time** *integer* <br> Lower bound of the estimated waiting time. <p>*Minimun:* <code>0</code></p>|
|**high_estimated_time** *integer* <br> Upper bound of the estimated waiting time. <p>*Minimun:* <code>0</code></p>|
|**phone** *string* <br>Customer phone for notifications. <p>*Validation pattern*: <code>^\+[1-9]{1}[0-9]{3,14}$</code></p> |
|**messages** *array[string]* <br> List of messages to customer.|
|**branch** *[Branch](#branch)* <br> Branch associated.</p> |
|**sector** *[Sector](#sector)* <br> Sector associated.</p> |
|**service** *[Service](#service)* <br> Service associated.</p> |
|**created_at** *date-time* <br> Datetime of ticket creation. <p>*Standard*: <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p> |
|**updated_at** *date-time* <br> Datetime of the last update of ticket. <p>*Standard*: <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p>  |

## Get All Tickets

> Sample Request:

```http
GET /customer/v1/tickets?customer_id=m809a31n HTTP/1.1
```

> Sample Success Response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "id": "89m32b0998",
        "queue": "T",
        "number": 2,
        "channel": "mobile",
        "status": "BLOCKED",
        "low_estimated_time": "10",
        "high_estimated_time": "15",
        "phone": "+51987776576",
        "messages":[
            "We have a promotion for you!"
        ],
        "branch": {
            "id": "27b6",
            "name": "Hiper Central",
            "short_name": "Hiper",
            "code": "AG001",
            "address": "Calle Beta 181 - 195, Callao",
            "latitude": -12.049919,
            "longitude": -77.0845193,
            "status": "OPEN",
            "opening_time": "2017-02-20T14:00:00.000Z",
            "closing_time": "2017-02-20T23:00:00.000Z",
            "congestion_level": "MEDIUM"
        },
        "sector": {
            "id": "s8",
            "name": "Tower A",
            "short_name": "A",
            "status": "OPEN"
        },
        "service": {
            "id": "7b6",
            "name": "Plataforma",
            "short_name": "Plataforma"
        },
        "created_at": "2017-02-20T10:00:00.000Z",
        "updated_at": "2017-02-20T10:00:00.000Z"
    }
]
```

> Sample error responses:

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
    "message": "Invalid customer ID."
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

Returns all tickets created by a specific customer.

<aside class="notice">
<strong>Order:</strong> The tickets are sorted descendantly by the field : <code>created_at</code>.
</aside>

<aside class="warning">
<strong>Caution:</strong> For this operation its necesary indicate a specific customer, You have two options, send the parameters <code>customer_id_type</code> and <code>customer_id_number</code> or just send <code>customer_id</code>. If you send all parameters, the API just consider the parameter <code>customer_id</code>.
</aside>

### HTTP Request

`GET /customer/v1/tickets`

### Query Params

| |
|:---|
|**customer_id** *string* <span class="recomended-param">recomended</span><br>Customer unique identifier used in your company. <p>*Validation pattern*: <code>^[0-9A-Za-z]{1,20}$</code></p> |
|**customer_id_type** *string* <br>Type of customer ID. <p>*Validation pattern*: <code>^[0-9a-zA-Z]{1,2}$</code></p> |
|**customer_id_number** *integer* <br>Number of customer ID. <p>*Validation pattern*: <code>^[0-9a-zA-Z]{1,16}$</code></p> |
|**fields** *array[string]* <span class="recomended-param">recomended</span> <br> Entity fields that will return at response. For example: `fields=id,queue,number`. |

### Responses

| |
|:---|
|**200** *array[[Ticket](#ticket)]* <br>A list of tickets. |
|**400** *[Error](#error)* <br>Bad request. |
|**500** *[Error](#error)* <br>An error has occurred.|

## Get Ticket

> Sample request:

```http
GET /customer/v1/tickets/89m32b0998 HTTP/1.1
```

> Sample success response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": "89m32b0998",
    "queue": "T",
    "number": 2,
    "channel": "mobile",
    "status": "BLOCKED",
    "low_estimated_time": "10",
    "high_estimated_time": "15",
    "phone": "+51987776576",
    "messages":[
        "We have a promotion for you!"
    ],
    "branch": {
        "id": "27b6",
        "name": "Hiper Central",
        "short_name": "Hiper",
        "code": "AG001",
        "address": "Calle Beta 181 - 195, Callao",
        "latitude": -12.049919,
        "longitude": -77.0845193,
        "status": "OPEN",
        "opening_time": "2017-02-20T14:00:00.000Z",
        "closing_time": "2017-02-20T23:00:00.000Z",
        "congestion_level": "MEDIUM"
    },
    "sector": {
        "id": "s8",
        "name": "Tower A",
        "short_name": "A",
        "status": "OPEN"
    },
    "service": {
        "id": "7b6",
        "name": "Plataforma",
        "short_name": "Plataforma"
    },
    "created_at": "2017-02-20T10:00:00.000Z",
    "updated_at": "2017-02-20T10:00:00.000Z"
}
```

> Sample error responses:

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
    "message": "Requested field not found."
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

Returns a customer ticket by ID.


### HTTP Request

`GET /customer/v1/tickets/{ticket_id}`

### Path Params

| |
|:---|
|**ticket_id** *string* <span class="required-param">required</span> <br>Unique identifier of Ticket. For example `89m32b0998`.|

### Query Params

| |
|:---|
|**fields** *array[string]* <span class="recomended-param">recomended</span> <br> Entity fields that will return at response. For example: `fields=id,queue,number`. |

### Responses

| |
|:---|
|**200** *[Ticket](#ticket)* <br>A ticket.|
|**400** *[Error](#error)* <br>Bad request. |
|**404** *[Error](#error)* <br>Ticket not found. |
|**500** *[Error](#error)* <br>An error has occurred.|

## Create Ticket

> Sample request:

```http
POST /customer/v1/tickets HTTP/1.1
Content-Type: application/json

{
    "channel": "mobile",
    "branch_id": "27b6",
    "sector_id": "s8",
    "service_id": "7b6",
    "customer_id": "a9087s902m"
}
```

> Sample success response:

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "id": "89m32b0998",
    "queue": "T",
    "number": 2,
    "channel": "mobile",
    "status": "BLOCKED",
    "low_estimated_time": "10",
    "high_estimated_time": "15",
    "phone": "+51987776576",
    "messages":[
        "We have a promotion for you!"
    ],
    "branch": {
        "id": "27b6",
        "name": "Hiper Central",
        "short_name": "Hiper",
        "code": "AG001",
        "address": "Calle Beta 181 - 195, Callao",
        "latitude": -12.049919,
        "longitude": -77.0845193,
        "status": "OPEN",
        "opening_time": "2017-02-20T14:00:00.000Z",
        "closing_time": "2017-02-20T23:00:00.000Z",
        "congestion_level": "MEDIUM"
    },
    "sector": {
        "id": "s8",
        "name": "Tower A",
        "short_name": "A",
        "status": "OPEN"
    },
    "service": {
        "id": "7b6",
        "name": "Plataforma",
        "short_name": "Plataforma"
    },
    "created_at": "2017-02-20T10:00:00.000Z",
    "updated_at": "2017-02-20T10:00:00.000Z"
}
```

> Sample error responses:

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
    "message": "Invalid customer ID."
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

Create a new customer ticket and then returns it.


### Request

| |
|:---|
|**fields** *array[string]* <span class="recomended-param">recomended</span> <br> Entity fields that will return at response. For example: `fields=id,queue,number`. |

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
