
## Create ticket

> Sample request:

```http
POST /v1/tickets HTTP/1.1
Content-Type: application/json

{
    "branch_id": "27b6",
    "sector_id": "s8",
    "service_id": "7b6",
    "channel": "mobile",
    "customer_id": "a9087s902m"
}
```

> Sample response:

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

Create a new customer ticket and then returns it.

### Endpoint

`POST /v1/tickets`

### Request

* **channelId** <span class="param-type">String</span> <span class="required-param">required</span> <br> Unique identifier of the channel used.
* **branchId** <span class="param-type">String</span> <span class="required-param">required</span> <br> Unique identifier of branch request by customer.
* **sectorId** <span class="param-type">String</span> <span class="required-param">required</span> <br> Unique identifier of sector requested by customer.
* **serviceId** <span class="param-type">String</span> <span class="required-param">required</span> <br> Unique identifier of service requested by customer.
* **categoryId** <span class="param-type">String</span> <span class="required-param">required</span><br> Customer phone for notifications.
* **customerId** <span class="param-type">String</span> <span class="required-param">required</span> <br> Unique identifier of the channel used. Used only for audit purpose.
* **customerName** <span class="param-type">String</span> <span class="recomended-param">recomended</span><br> Unique identifier of customer id type.
* **customerDocument** <span class="param-type">String</span> <span class="recomended-param">recomended</span><br> Number of customer id.
* **customerPhone** <span class="param-type">String</span> <span class="recomended-param">recomended</span><br> Customer phone for notifications.
* **operatorId** <span class="param-type">String</span> <br> Customer phone for notifications.
* **messagesToCustomer** <span class="param-type">List\<String\></span> <br> Messages to print in ticket.
* **messagesToOperator** <span class="param-type">List\<String\></span> <br> Messages to show in counter.

### Responses

|**201** *[Ticket](#ticket)* <br>A ticket.|
|**400** *[Error](#error)* <br>Bad request. |
|**500** *[Error](#error)* <br>An error has occurred.|
