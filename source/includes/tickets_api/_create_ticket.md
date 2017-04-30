
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
    "categoryId": "i10",
    "name": "Mr. Smith",
    "docType": "D",
    "docNumber": "90452291",
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
    "phone": "+51987882567",
    "messages": [
        "We have a promotion for you!"
    ],
    "channel": {
        "id": "c10",
        "name": "Mobile",
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

Create a new customer ticket and then returns it.

<aside class="warning">
<strong>Caution:</strong>
You should consider the following before create a ticket:
Validar estados
<ul>
    <li>The channel used should support the requested service.</li>
    <li>The requested branch should contain the requested sector.</li>
    <li>The requested sector should support the requested service.</li>
    <li>The customer should has no other ticket.</li>
    <li>The customer category referenced by the <code>categoryId</code> should has a queue configured for the requested service and the channel used.</li>
<ul>
</aside>

This operation can throw the next validation errors:

Code| Field |Message
---|---|---
40001|channelId|Channel not exists.
40002|serviceId|Service not exists.
40003|branchId|Branch not exists.
40004|sectorId|Sector not exists.
40005|categoryId|Customer category not exists.
40006|serviceId|Service not supported by the channel.
40008|serviceId|Service not supported by the sector.
40009|branchId|Branch is not the sector owner.
40010|customerId|Customer has another ticket.
40011|categoryId|Customer category has no configured queue type for the service and  channel.

### Endpoint

`POST /v1/tickets/customer/{customerId}/tickets`

### Path Params

* **customerId** <span class="param-type">String</span><br>
Customer unique identifier (Obtained it from the customers integration interface).

### Request

* **channelId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Unique identifier of the channel used. This value should to be fixed in the client application.

* **branchId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Unique identifier of the requested branch.

* **sectorId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Unique identifier of the requested sector.

* **serviceId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Unique identifier of the requested service.

* **categoryId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Customer category unique identifier (Obtained it from the customers integration interface).

* **name** <span class="param-type">String</span><br>
Name or alias of the client used for contact purpose.
<p>
    <span class="param-condition">Maximum length:</span> `50`
</p>

* **docType** <span class="param-type">String</span><br>
Type of document used to identify the client.
<p>
    <span class="param-condition">Maximum length:</span> `5`
</p>

* **docNumber** <span class="param-type">String</span><br>
Number of document used to identify the client.
<p>
    <span class="param-condition">Maximum length:</span> `20`
</p>

* **phone** <span class="param-type">String</span><br>
Customer phone for notifications associated to the booking.
<p>
    <span class="param-condition">Validation pattern:</span> `^+[1-9]{1}[0-9]{3,14}$`
</p>

* **teller** <span class="param-type">String</span> <br>
Account name of teller associated to the customer. When this parameter is provided, the ticket generated should associate to the counter of the teller referenced.

* **messagesToCustomer** <span class="param-type">List\<String\></span> <br> Messages to print in ticket (Obtained it from the customers integration interface).

* **messagesToTeller** <span class="param-type">List\<String\></span> <br> Messages to show in counter (Obtained it from the customers integration interface).

### Responses

* **201** <span class="verb-description">Created</span> <span class="param-type">[Ticket](#ticket)</span><br>
Successful creation, returns the new ticket.

* **400** <span class="verb-description">Bad Request</span> <span class="param-type">List\<[ValidationError](#validation-error)\></span><br>
One or more parameters are not valid, returns a description of validation failed.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
