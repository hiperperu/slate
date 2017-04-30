
## Show ticket details

> Sample request:

```http
GET /v1/tickets/customer/c9mas9js/tickets/89m32b0 HTTP/1.1
```

> Sample response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": "89m32b0",    
    "number": 2,
    "status": "BLOCKED",
    "phone": "+51987776576",
    "position": 10,
    "lowEstimatedTime": 10,
    "highEstimatedTime": 15,
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
        "shortName": "Hiper",
        "address": "Calle Beta 181 - 195, Callao",
        "latitude": -12.049919,
        "longitude": -77.0845193,
        "status": "ACTIVE"
    },
    "sector": {
        "id": "m9",
        "name": "Tower A",
        "shortName": "A",
        "status": "ACTIVE"
    },
    "service": {
        "id": "s8",
        "name": "Plataforma",
        "shortName": "Plataforma"
    },
    "queueType": {
        "id": "R0009",
        "code": "CC",
        "name": "Comercial"
    },
    "counter": {
        "id": "v10",
        "name": "V10",
        "teller": "achavez"
    },
    "createdAt": "2017-02-20T10:00:00.000Z",
    "updatedAt": "2017-02-20T10:00:00.000Z",
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

`GET /v1/tickets/customer/{customerId}/tickets/{ticketId}`

### Path Params

* **customerId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Customer unique identifier.

* **ticketId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Ticket unique identifier (Generated in the ticket creation).

### Query Params

* **fields** <span class="param-type">List\<String\></span> <span class="recomended-param">recomended</span><br>
Entity fields that will included in the response(See available fields in [the ticket object definition](#ticket)). For example: `fields=id,queueType,number`.

### Responses

* **200** <span class="verb-description">OK</span> <span class="param-type">[Ticket](#ticket)</span><br>
A ticket.

* **400** <span class="verb-description">Bad Request</span> <span class="param-type">[ValidationError](#validation-error)</span><br>
One or more parameters are not valid, returns a description of validation failed.

* **404** <span class="verb-description">Not Found</span> <span class="param-type">[Error](#error)</span><br>
The resource requested not found, returns a simple error message.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
