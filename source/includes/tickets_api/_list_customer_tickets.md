
## List customer tickets

> Sample request:

```http
GET /v1/tickets?customer_id=c9mas9js HTTP/1.1
```

> Sample response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "id": "89m32b0",    
        "number": 2,
        "status": "BLOCKED",
        "phone": "+51987776576",
        "position": 10,
        "low_estimated_time": 10,
        "high_estimated_time": 15,
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
        "created_at": "2017-02-20T10:00:00.000Z",
        "updated_at": "2017-02-20T10:00:00.000Z",
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
]
```

Returns all tickets created by a specific customer.

<aside class="warning">
    <strong>Caution:</strong>
    You must consider the following:
    <ul>
        <li>When the teller calls the ticket, it is automatically deleted and is not available anymore.</li>
        <li>An empty list is returned when no registered tickets with the <code>customer_id</code> existed.</li>
    <ul>
</aside>

<aside class="notice">
    <strong>Order:</strong>
    The tickets are sorted descendant by the field: <code>created_at</code>.
</aside>

### Endpoint

`GET /v1/tickets`

### Query Params

* **customer_id** <span class="param-type">String</span> <span class="required-param">required</span> <br> Customer unique identifier.

* **fields** <span class="param-type">List\<String\></span> <span class="recomended-param">recomended</span><br>
Entity fields that will included in the response(See available fields in [the ticket object definition](#ticket)). For example: `fields=id,queueType,number`.

### Responses

* **200** <span class="verb-description">Ok</span> <span class="param-type">List\<[Ticket](#ticket)\></span><br>
A list of tickets.

* **400** <span class="verb-description">Bad Request</span> <span class="param-type">[Error](#error)</span><br>
One or more parameters are not valid, returns a description of validation failed.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
