
## Create ticket

> Sample request:

```http
POST /v1/tickets/customer/c9mas9js/tickets HTTP/1.1
Content-Type: application/json

{
    "channelId": "c10",
    "branchId": "27b6",
    "sectorId": "m9",
    "serviceId": "s8",
    "categoryId": "mobile",
    "name":"Mr. Smith",
    "document": "90452291",
    "phone": "+51987882567"
}
```

> Sample response:

```http
HTTP/1.1 201 Created
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
        "id": "a10",
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
        "id": "s8",
        "name": "Tower A",
        "shortName": "A",
        "status": "ACTIVE"
    },
    "service": {
        "id": "7b6",
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

Create a new customer ticket and then returns it.

<aside class="warning">
<strong>Caution: </strong> You should consider the following before create a ticket:
<ul>
<li>The channel referenced by the <code>channelId</code> have to support the service requested.</li>
<li>The branch referenced by the <code>branchId</code> have to contain the sector referenced by the <code>sectorId</code>. </li>
<li>The sector referenced by the <code>sectorId</code> have to support the service requested.</li>
<li>The client referenced by the <code>customerId</code> should has no other ticket.</li>
<li>The customer category referenced by the <code>categoryId</code> should has a queue configured for the service requested and the channel used.</li>
<ul>
</aside>

### Endpoint

`POST /v1/tickets/customer/{customerId}/tickets`

### Path Params

* **customerId** <span class="param-type">String</span> <br> Customer unique identifier.

### Request

* **channelId** <span class="param-type">String</span> <span class="required-param">required</span> <br> Channel unique identifier.
* **branchId** <span class="param-type">String</span> <span class="required-param">required</span> <br> Branch unique identifier.
* **sectorId** <span class="param-type">String</span> <span class="required-param">required</span> <br> Sector unique identifier.
* **serviceId** <span class="param-type">String</span> <span class="required-param">required</span> <br> Service unique identifier.
* **categoryId** <span class="param-type">String</span> <span class="required-param">required</span><br> Customer category unique identifier.
* **name** <span class="param-type">String</span> <br> Name or alias of client used for contact purpose. <p><span class="param-condition">Maximum length: </span>`50`</p>
* **document** <span class="param-type">String</span>  <br> Document number of customer. <p><span class="param-condition">Maximum length: </span>`20`</p>
* **phone** <span class="param-type">String</span> <br> Customer phone for notifications. <p><span class="param-condition">Validation pattern: </span>`^+[1-9]{1}[0-9]{3,14}$`</p>
* **teller** <span class="param-type">String</span> <br> Account name of teller associated to the customer. When this parameter is provided, the ticket generated should associate to the counter of the teller referenced.
* **messagesToCustomer** <span class="param-type">List\<String\></span> <br> Messages to print in ticket.
* **messagesToTeller** <span class="param-type">List\<String\></span> <br> Messages to show in counter.

### Responses

* **201** <span class="verb-description">Created</span> *[Ticket](#ticket)* <br>Successful creation, returns the new ticket created.
* **400** <span class="verb-description">Bad Request</span> *[ValidationError](#validation-error)* <br>One or more parameters are not valid, returns a description of validation failed.
* **500** <span class="verb-description">Internal Server Error</span> *[Error](#error)* <br>An unexpected error has occurred, returns a simple error message.
