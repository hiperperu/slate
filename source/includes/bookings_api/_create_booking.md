
## Create booking

> Sample request:

```http
POST /v1/bookings/customer/c9mas9js/bookings HTTP/1.1
Content-Type: application/json

{
    "channelId": "c10",
    "branchId": "27b6",
    "serviceId": "s9",
    "name": "Mr. Smith",
    "document": "90452291",
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
        "status": "ACTIVE"
    },
    "service": {
        "id": "7b6",
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
<strong>Caution: </strong> You should consider the following before create a booking:
<ul>
<li>The channel referenced by the <code>channelId</code> have to support the service requested.</li>
<li>The branch referenced by the <code>branchId</code> have to support the service requested.</li>
<li>The client referenced by the <code>customerId</code> should has no other booking for the same requested service in state <code>ACTIVE</code> or <code>PENDING</code>.</li>
<li>The <code>startTime</code> and the <code>endTime</code> have to be available for the branch and service.</li>
<ul>
</aside>

### Endpoint

`POST /v1/bookings/customer/{customerId}/bookings`

### Path Params

* **customerId** <span class="param-type">String</span> <br> Customer unique identifier.

### Request

* **channelId** <span class="param-type">String</span> <span class="required-param">required</span><br> Channel unique identifier.
* **branchId** <span class="param-type">String</span> <span class="required-param">required</span> <br> Branch unique identifier.
* **serviceId** <span class="param-type">String</span> <span class="required-param">required</span> <br> Service unique identifier.
* **name** <span class="param-type">String</span> <br> Name or alias of client used for contact purpose. <p><span class="param-condition">Maximum length: </span>`50`</p>
* **document** <span class="param-type">String</span>  <br> Document number of customer. <p><span class="param-condition">Maximum length: </span>`20`</p>
* **phone** <span class="param-type">String</span> <br> Customer phone for notifications. <p><span class="param-condition">Validation pattern: </span>`^+[1-9]{1}[0-9]{3,14}$`</p>
* **startTime** <span class="param-type">DateTime</span> <span class="required-param">required</span> <br> Start time of booking. <p><span class="param-condition">Format:  </span><code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p>
* **endTime** <span class="param-type">DateTime</span> <span class="required-param">required</span> <br> End time of booking. <p><span class="param-condition">Format:  </span><code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p>

### Responses

* **201** <span class="verb-description">Created</span> *[Booking](#booking)* <br>Successful creation, returns the new booking created.
* **400** <span class="verb-description">Bad Request</span> *[ValidationError](#validation-error)* <br>One or more parameters are not valid, returns a description of validation failed.
* **500** <span class="verb-description">Internal Server Error</span> *[Error](#error)* <br>An unexpected error has occurred, returns a simple error message.
