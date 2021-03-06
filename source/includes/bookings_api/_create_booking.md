
## Create booking

> Sample request:

```http
POST /v1/bookings/ HTTP/1.1
Content-Type: application/json

{
    "channel_id": "c10",
    "branch_id": "27b6",
    "service_id": "s8",
    "customer_id": "c9mas9js",
    "doc_type": "D",
    "doc_number": "90452291",
    "phone": "+51987882567",
    "start_time":"2017-02-20T14:00:00.000Z",
    "end_time":"2017-02-20T15:00:00.000Z"
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
        "short_name": "Hiper",
        "address": "Calle Beta 181 - 195, Callao",
        "latitude": -12.049919,
        "longitude": -77.0845193,
        "status": "ACTIVE"
    },
    "service": {
        "id": "s8",
        "name": "Plataforma",
        "short_name": "Plataforma"
    },
    "start_time": "2017-02-20T14:00:00.000Z",
    "end_time": "2017-02-20T15:00:00.000Z",
    "created_at": "2017-02-10T14:00:00.000Z"
}
```

Create a new customer booking and returns it.

<aside class="warning">
    <strong>Caution: </strong>
    You must consider the following before create a booking:
    <ul>
        <li>The referenced channel must support the requested service.</li>
        <li>The referenced branch must support the requested service .</li>
        <li>The referenced client must has no other booking in state <code>ACTIVE</code> or <code>PENDING</code> for the same requested service.</li>
        <li>The <code>start_time</code> and the <code>end_time</code> must be available.</li>
    <ul>
</aside>

### Endpoint

`POST /v1/bookings/`

### Request

* **channel_id** <span class="param-type">String</span> <span class="required-param">required</span><br>
Unique identifier of the channel used. This value must be set in the client application.

* **branch_id** <span class="param-type">String</span> <span class="required-param">required</span><br>
Unique identifier of the requested branch.

* **service_id** <span class="param-type">String</span> <span class="required-param">required</span><br>
Unique identifier of the requested service.

* **customer_id** <span class="param-type">String</span> <span class="required-param">required</span><br>
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
Customer phone for notifications associated to the booking.
<p>
    <span class="param-condition">Validation pattern:</span> `^\+[1-9]{1}[0-9]{3,14}$`
</p>

* **start_time** <span class="param-type">DateTime</span> <span class="required-param">required</span><br>
Start time of booking.
<p>
    <span class="param-condition">Format:</span> <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code>
</p>

* **end_time** <span class="param-type">DateTime</span> <span class="required-param">required</span><br>
End time of booking.
<p>
    <span class="param-condition">Format:</span> <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code>
</p>

### Responses

* **201** <span class="verb-description">Created</span> <span class="param-type">[Booking](#booking)</span><br>
Successful creation, returns the new booking.

* **400** <span class="verb-description">Bad Request</span> <span class="param-type">[Error](#error)</span><br>
One or more parameters are not valid, returns a description of validation failed.

* **500** <span class="verb-description">Internal Server Error</span> <span class="param-type">[Error](#error)</span><br>
An unexpected error has occurred, returns a simple error message.
