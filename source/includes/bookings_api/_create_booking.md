
## Create booking

> Sample request:

```http
POST /v1/bookings HTTP/1.1
Content-Type: application/json

{
    "branch_id": "27b6",
    "service_id": "7b6",
    "channel": "mobile",
    "customer_id": "a9087s902m",
    "start_time":"2017-02-20T14:00:00.000Z",
    "end_time":"2017-02-20T15:00:00.000Z"
}
```

> Sample response:

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "id": "a90mos70om",
    "code": "UxMa01m",
    "channel": "mobile",
    "status": "ACTIVE",
    "phone": "+51987776576",
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
    "service": {
        "id": "7b6",
        "name": "Plataforma",
        "short_name": "Plataforma"
    },
    "start_time": "2017-02-20T14:00:00.000Z",
    "end_time": "2017-02-20T15:00:00.000Z",
    "created_at": "2017-02-10T14:00:00.000Z",
    "updated_at": "2017-02-10T14:00:00.000Z"
}
```

Create a new customer booking and then it returns it.

<aside class="warning">
<strong>Caution: </strong> You have to consider the following before create a booking:
<ul>
<li>The branch referenced by the <code>branch_id</code> have to allow the bookings.</li>
<li>The <code>start_time</code> and the <code>end_time</code> have to be available for the branch and service.</li>
<li>If you send a <code>customer_id_type</code> it's mandatory send a <code>customer_id_number</code>.</li>
<li>If you send a <code>customer_id</code>, then the <code>customer_id_type</code> and  <code>customer_id_number</code> are ignored.</li>
<ul>
</aside>

### Endpoint

`POST /customer/v1/bookings`

### Request

| |
|:---|
|**branch_id** <span class="param-type">string</span> <span class="required-param">required</span> <br> Unique identifier of branch. |
|**service_id** <span class="param-type">string</span> <span class="required-param">required</span> <br> Unique identifier of service. |
|**channel** <span class="param-type">string</span> <span class="recomended-param">recomended</span><br> Free text to identify the channel used. Used only for audit purpose. <p><span class="param-condition">Maximum length:  </span>`20`</p> |
|**phone** <span class="param-type">string</span> <span class="recomended-param">recomended</span><br> Customer phone for notifications. <p><span class="param-condition">Validation pattern:  </span>`^+[1-9]{1}[0-9]{3,14}$`</p>|
|**start_time** <span class="param-type">date-time</span> <span class="required-param">required</span> <br> Start time of booking. <p><span class="param-condition">Format:  </span><code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p>|
|**end_time** <span class="param-type">date-time</span> <span class="required-param">required</span> <br> End time of booking. <p><span class="param-condition">Format:  </span><code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p> |
|**customer_id** <span class="param-type">string</span> <br> Customer unique identifier used in your company. <p><span class="param-condition">Validation pattern:  </span>`^[0-9A-Z]{1,20}$`</p> |
|**customer_id_type** <span class="param-type">string</span> <br> Unique identifier of customer id type. <p><span class="param-condition">Validation pattern:  </span>`^[0-9A-Z]{1,4}$`</p>|
|**customer_id_number** <span class="param-type">string</span>  <br> Number of customer id. <p><span class="param-condition">Validation pattern:  </span>`^[0-9A-Z]{1,16}$`</p>|

### Responses

| |
|:---|
|**201** <span class="verb-description">Created</span> *[Booking](#the-booking-object)* <br>Successful creation, returns the new booking created.|
|**400** <span class="verb-description">Bad Request</span> *[Error](#the-error-object)* <br>One or more parameters are not valid, returns a description of validation failed.  |
|**500** <span class="verb-description">Internal Server Error</span> *[Error](#the-error-object)* <br>An unexpected error has occurred, returns a description of the exception. |
