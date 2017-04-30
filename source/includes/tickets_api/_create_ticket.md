
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

Create a new customer ticket and returns it.

<aside class="warning">
<strong>Caution:</strong>
    You should consider the following before create a ticket:
    <ul>
        <li>The channel used should support the requested service.</li>
        <li>The requested branch should contain the requested sector.</li>
        <li>The requested sector should support the requested service.</li>
        <li>The customer should has no other ticket.</li>
        <li>The customer category referenced by the <code>categoryId</code> should has a queue configured for the requested service and the channel used.</li>
    <ul>
</aside>

### Endpoint

`POST /v1/tickets/customer/{customerId}/tickets`

### Path Params

* **customerId** <span class="param-type">String</span><br>
Customer unique identifier.

### Request

* **channelId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Unique identifier of the channel used. This value should be fixed in the client application.

* **branchId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Unique identifier of the requested branch.

* **sectorId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Unique identifier of the requested sector.

* **serviceId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Unique identifier of the requested service.

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
Customer phone for notifications associated to the ticket.
<p>
    <span class="param-condition">Validation pattern:</span> `^\+[1-9]{1}[0-9]{3,14}$`
</p>

### Responses

* **201** <span class="verb-description">Created</span> <span class="param-type">[Ticket](#ticket)</span><br>
Successful creation, returns the new ticket.

* **400** <span class="verb-description">Bad Request</span> <span class="param-type">[ValidationError](#validation-error)</span><br>
One or more parameters are not valid, returns a description of validation failed.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
