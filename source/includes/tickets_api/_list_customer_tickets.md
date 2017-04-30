
## List customer tickets

> Sample request:

```http
GET /v1/tickets/customer/c9mas9js/tickets HTTP/1.1
```

> Sample response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
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
            "name": "Mobile"
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
]
```

Returns all tickets created by a specific customer.

<aside class="warning">
<strong>Caution:</strong>
You should consider the following:
<ul>
    <li>When the ticket is called by the teller is automatically deleted and is not available anymore.</li>
    <li>An empty list is returned when not exist registered tickets with the <code>customerId</code> received.</li>
<ul>
</aside>

<aside class="notice">
<strong>Order:</strong>
The tickets are sorted descendantly by the field: <code>createdAt</code>.
</aside>

### Endpoint

`GET /v1/tickets/customer/{customerId}/tickets`

### Path Params

* **customerId** <span class="param-type">String</span> <span class="required-param">required</span> <br> Customer unique identifier.

### Query Params

* **fields** <span class="param-type">List\<String\></span> <span class="recomended-param">recomended</span><br>
Entity fields that will return at response. For example: `fields=id,queue,number`.

### Responses

* **200** <span class="verb-description">Ok</span> <span class="param-type">List\<[Ticket](#ticket)\></span><br>
A list of tickets.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
