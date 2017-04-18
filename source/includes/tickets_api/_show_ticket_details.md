
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
    "queue": "T",
    "number": 2,
    "position": 10,
    "status": "BLOCKED",
    "lowEstimatedTime": "10",
    "highEstimatedTime": "15",
    "phone": "+51987776576",
    "messages": [
        "We have a promotion for you!"
    ],
    "channel": {
        "id": "c10",
        "name": "Mobile",
        "shortName": "Mobile"
    },
    "branch": {
        "id": "27b6",
        "name": "Hiper Central",
        "shortName": "Hiper",
        "address": "Calle Beta 181 - 195, Callao",
        "latitude": -12.049919,
        "longitude": -77.0845193,
        "status": "ACTIVE",
        "congestion": "MEDIUM"
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
Customer unique identifier (Obtained it from the customers integration interface).

* **ticketId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Ticket unique identifier (Generated in the ticket creation).

### Query Params

* **fields** <span class="param-type">List\<String\></span> <span class="recomended-param">recomended</span><br>
Entity fields that will return at response. For example: `fields=id,queue,number`.

### Responses

* **200** <span class="verb-description">OK</span> <span class="param-type">[Ticket](#ticket)</span><br>
A ticket.

* **404** <span class="verb-description">Not Found</span> <span class="param-type">[Error](#error)</span><br>
The resource requested not found, returns a simple error message.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
