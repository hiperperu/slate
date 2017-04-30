
## Create booking

> Sample request:

```http
POST /v1/bookings/customer/c9mas9js/bookings HTTP/1.1
Content-Type: application/json

{
    "channelId": "c10",
    "branchId": "27b6",
    "serviceId": "s8",
    "name": "Mr. Smith",
    "docType": "D",
    "docNumber": "90452291",
    "phone": "+51987882567",
    "startTime":"2017-02-20T14:00:00.000Z",
    "endTime":"2017-02-20T15:00:00.000Z"
}
```

> Sample response:

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "id": "a90mos",
    "code": "UxMa01m",
    "status": "ACTIVE",
    "phone": "+51987882567",
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
    "service": {
        "id": "s8",
        "name": "Plataforma",
        "shortName": "Plataforma"
    },
    "startTime": "2017-02-20T14:00:00.000Z",
    "endTime": "2017-02-20T15:00:00.000Z",
    "createdAt": "2017-02-10T14:00:00.000Z",
    "updatedAt": "2017-02-10T14:00:00.000Z"
}
```

Create a new customer booking and then it returns it.

<aside class="warning">
<strong>Caution: </strong>
You should consider the following before create a booking:
<ul>
    <li>The channel referenced should support the service requested.</li>
    <li>The branch referenced should support the service requested.</li>
    <li>The client referenced should has no other booking in state <code>ACTIVE</code> or <code>PENDING</code> for the same requested service.</li>
    <li>The <code>startTime</code> and the <code>endTime</code> should to be available.</li>
<ul>
</aside>

This operation can throw the next validation errors:

Code| Field |Message
---|---|---
40001|channelId|Channel not exists.
40002|serviceId|Service not exists.
40003|branchId|Branch not exists.
40006|serviceId|Service not supported by the channel.
40007|serviceId|Service not supported by the branch.
40012|customerId|Customer has another valid booking for the same service.
40013|startTime|Booking start time not valid.
40014|endTime|Booking end time not valid.
40015|serviceId|Service not available in the requested time.

### Endpoint

`POST /v1/bookings/customer/{customerId}/bookings`

### Path Params

* **customerId** <span class="param-type">String</span><br>
Customer unique identifier (Obtained it from the customers integration interface).

### Request

* **channelId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Unique identifier of the channel used. This value should to be fixed in the client application.

* **branchId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Unique identifier of the requested branch.

* **serviceId** <span class="param-type">String</span> <span class="required-param">required</span><br>
Unique identifier of the requested service.

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

* **startTime** <span class="param-type">DateTime</span> <span class="required-param">required</span><br>
Start time of booking.
<p>
    <span class="param-condition">Format:</span> <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code>
</p>

* **endTime** <span class="param-type">DateTime</span> <span class="required-param">required</span><br>
End time of booking.
<p>
    <span class="param-condition">Format:</span> <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code>
</p>

### Responses

* **201** <span class="verb-description">Created</span> <span class="param-type">[Booking](#booking)</span><br>
Successful creation, returns the new booking.

* **400** <span class="verb-description">Bad Request</span> <span class="param-type">List\<[ValidationError](#validation-error)\></span><br>
One or more parameters are not valid, returns a description of validation failed.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
