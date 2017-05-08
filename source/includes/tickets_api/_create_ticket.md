
## Create ticket

> Sample request:

```http
POST /v1/tickets HTTP/1.1
Content-Type: application/json

{
    "channel_id": "c10",
    "branch_id": "27b6",
    "sector_id": "m9",
    "service_id": "s8",
    "status": "BLOCKED",
    "customer_id": "c9mas9js",
    "doc_type": "D",
    "doc_number": "90452291",
    "phone": "+51987882567"
}
```

> Sample response:

```http
HTTP/1.1 201 Created
Content-Type: application/json

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
    "queue_type": {
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
```

Create a new customer ticket and returns it.

<aside class="warning">
    <strong>Caution:</strong>
    You must consider the following before create a ticket:
    <ul>
        <li>The referenced channel must support the requested service.</li>
        <li>The referenced branch must contain the requested sector.</li>
        <li>The referenced sector must support the requested service.</li>
        <li>The customer must has no other ticket for the same service.</li>
    <ul>
</aside>

### Endpoint

`POST /v1/tickets`

### Request

* **channel_id** <span class="param-type">String</span> <span class="required-param">required</span><br>
Unique identifier of the channel used. This value must be set in the client application.

* **branch_id** <span class="param-type">String</span> <span class="required-param">required</span><br>
Unique identifier of the requested branch.

* **sector_id** <span class="param-type">String</span> <span class="required-param">required</span><br>
Unique identifier of the requested sector.

* **service_id** <span class="param-type">String</span> <span class="required-param">required</span><br>
Unique identifier of the requested service.

* **status** <span class="param-type">Enum</span><br>
Status of the ticket.
<p>
    <span class="param-condition">Possible values:</span>
    <ul>
        <li><code>BLOCKED</code>: When the ticket shouldn't called by teller.</li>
        <li><code>ENABLED</code>: When the can to be called by the teller.</li>
    </ul>
</p>

* **customer_id** <span class="param-type">String</span><br>
Customer unique identifier.

* **doc_type** <span class="param-type">String</span><br>
Type of document used to identify the client.
<p>
    <span class="param-condition">Maximum length:</span> `5`
</p>

* **doc_number** <span class="param-type">String</span><br>
Number of document used to identify the client.
<p>
    <span class="param-condition">Maximum length:</span> `20`
</p>

* **phone** <span class="param-type">String</span><br>
Customer phone for notifications associated to the ticket.
<p>
    <span class="param-condition">Validation pattern:</span> `^\+[1-9]{1}[0-9]{3,14}$`
</p>

### Responses

* **201** <span class="verb-description">Created</span> <span class="param-type">[Ticket](#ticket)</span><br>
Successful creation, returns the new ticket.

* **400** <span class="verb-description">Bad Request</span> <span class="param-type">[Error](#error)</span><br>
One or more parameters are not valid, returns a description of validation failed.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
