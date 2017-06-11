
## Show ticket details

> Sample request:

```http
GET /v1/tickets/89m32b0 HTTP/1.1
```

> Sample response:

```http
HTTP/1.1 200 OK
Content-Type: application/json


{
    "id": "89m32b0",    
    "number": 2,
    "status": "ATTENDED",
    "position": 10,
    "low_estimated_time": 10,
    "high_estimated_time": 15,
    "phone": "+51987776576",
    "messages": [
        "We have a promotion for you!"
    ],
    "channel": {
        "id": "c10",
        "name": "Mobile"
    },
    "branch": {
        "id": "27b6",
        "name": "Hiper Central",
        "short_name": "Hiper",
        "address": "Calle Beta 181 - 195, Callao",
        "latitude": -12.049919,
        "longitude": -77.0845193,
        "status": "ACTIVE"
    },
    "sector": {
        "id": "m9",
        "name": "Tower A",
        "short_name": "A",
        "status": "ACTIVE"
    },
    "service": {
        "id": "s8",
        "name": "Plataforma",
        "short_name": "Plataforma"
    },
    "queue_type": {
        "id": "R0009",
        "code": "CC",
        "name": "Comercial"
    },
    "counter": {
        "id": "v10",
        "name": "V10",
        "teller": "achavez",
        "type": {
            "id": "v2002",
            "name": "Ventanilla"
        }
    },
    "created_at": "2017-02-20T10:00:00.000Z",
    "called_at": "2017-02-20T10:05:00.000Z",
    "started_at": "2017-02-20T10:05:18.000Z",
    "print": [
        {
            "align": "CENTER",
            "font": "A_REGULAR",
            "previous": "Welcome to",
            "content": "Hiper",
            "next": "!"
        }
    ]
}
```

Returns a customer ticket by ID.


### Endpoint

`GET /v1/tickets/{ticket_id}`

### Path Params

* **ticket_id** <span class="param-type">String</span> <span class="required-param">required</span><br>
Ticket unique identifier (Generated in the ticket creation).

### Query Params

* **fields** <span class="param-type">List\<String\></span> <span class="recomended-param">recomended</span><br>
Entity fields that will included in the response(See available fields in [the ticket object definition](#ticket)). For example: `fields=id,queue_type,number`.

### Responses

* **200** <span class="verb-description">OK</span> <span class="param-type">[Ticket](#ticket)</span><br>
A ticket.

* **400** <span class="verb-description">Bad Request</span> <span class="param-type">[Error](#error)</span><br>
One or more parameters are not valid, returns a description of validation failed.

* **404** <span class="verb-description">Not Found</span> <span class="param-type">[Error](#error)</span><br>
The resource requested not found, returns a simple error message.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
