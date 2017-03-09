
# Booking

Allow to your customers reserve a attention schedule for a better customer experience reducing the waiting time and better the congestion of your branches. The endpoints of this section allow the creation of bookings from your application.

## Booking Object

> Sample object:

```json
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

Model of booking object.

### Fields

| |
|:---|
|**id** *string* <br>Booking unique identifier. <p>*Validation pattern*: <code>^[0-9a-z]{8,16}$</code></p> |
|**code** *string* <br>Booking code to display it to customer. <p>*Validation pattern*: <code>^[0-9a-zA-Z]{6,12}$</code> |
|**channel** *string* <br>Code of channel used. <p>*Maximum length*: <code>20</code></p> |
|**status** *enum* <br>Current status of the booking. <p>*Possible values*: <ul><li><code>ACTIVE</code></li><li><code>INACTIVE</code></li><li><code>DEFEATED</code></li></ul></p> |
|**phone** *string* <br>Customer phone for notifications. <p>*Validation pattern*: <code>^\+[1-9]{1}[0-9]{3,14}$</code></p> |
|**branch** *[Branch](#branch)* <br> Branch associated.</p> |
|**service** *[Service](#service)* <br> Service associated.</p> |
|**start_time** *date-time* <br> Start time of booking. <p>*Standard*: <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p> |
|**end_time** *date-time* <br> End time of booking.<p>*Standard*: <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p>  |
|**created_at** *date-time* <br> Datetime of ticket creation. <p>*Standard*: <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p> |
|**updated_at** *date-time* <br> Datetime of the last update of ticket. <p>*Standard*: <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p>  |


## Booking Day Object

> Sample object:

```json
{
    "day": "2017-02-20T00:00:00.000Z",
    "ranges": [
        {
            "start_time": "2017-02-20T14:00:00.000Z",
            "end_time": "2017-02-20T15:00:00.000Z"
        }
    ]
}
```

Model of day object with available bookings.


### Fields

| |
|:---|
|**day** *date-time* <br> Date with available bookings. <p>*Standard*: <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p> |
|**ranges** *array[[BookingRange](#booking_range_object)]* <br> List of time ranges with available bookings.  |

## Booking Range Object

> Sample object

```json
{
    "start_time": "2017-02-20T14:00:00.000Z",
    "end_time": "2017-02-20T15:00:00.000Z"
}
```

Model of time range object with available bookings.

### Fields

| |
|:---|
|**start_time** *date-time* <br> Start time of range. <p>*Standard*: <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p> |
|**end_time** *date-time* <br> End time of range.<p>*Standard*: <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p>  |


## Get Days For Book

> Sample request:

```http
GET /v1/bookings/days?branch_id=27b6&service_id=7b6 HTTP/1.1
```

> Sample success response:

```http
HTTP/1.1 200 OK
X-Pagination-Count: 7
X-Pagination-Page: 3
X-Pagination-Limit: 1
Content-Type: application/json

[
    {
        "day": "2017-02-20T00:00:00.000Z",
        "ranges": [
            {
                "start_time": "2017-02-20T14:00:00.000Z",
                "end_time": "2017-02-20T15:00:00.000Z"
            }
        ]
    }
]
```

> Sample error responses:

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
    "message": "Invalid branch ID."
}
```
```http
HTTP/1.1 500 Internal Server Error
Content-Type: application/json

{
    "message": "An error has ocurred.",
    "code": "ab90",
    "more_info": "https://bmatic.com/docs/errors/ab90"
}
```

Returns a list of days for book a specific service in a branch.

<aside class="notice">
<strong>Order:</strong> The booking days are sorted ascendantly by  <code>day</code>.
</aside>

### Endpoint

`GET /customer/v1/bookings/days`

### Query Params

| |
|:---|
|**branch_id** *string* <span title="required" class="required-param">required</span> <br> Unique identifier of branch requested.|
|**service_id** *string* <span title="required" class="required-param">required</span> <br> Unique identifier of service requested.|
|**offset** *int* <br> Position in pagination. Default is `0`, maximum is `99999`.|
|**limit** *int* <br> Number of items to retrieve. Default is `10`, maximum is `50`.|

### Responses

| |
|:---|
|**200** *array[[Booking](#booking-day-object)]* <br>A list of booking days. Pagination headers are included: <ul><li><strong>X-Pagination-Count:</strong> Total number of items.</li><li><strong>X-Pagination-Page:</strong> Number of the current page.</li><li><strong>X-Pagination-Limit:</strong> Number of items returned.</li></ul>|
|**400** *[Error](#error)* <br>Bad request. |
|**500** *[Error](#error)* <br>An error has occurred.|


## Get All Bookings

> Sample request:

```http
GET /customer/v1/bookings?customer_id=m809a31n HTTP/1.1
```

> Sample success response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
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
]
```

> Sample error responses:

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
    "message": "Invalid customer ID."
}
```
```http
HTTP/1.1 500 Internal Server Error
Content-Type: application/json

{
    "message": "An error has ocurred.",
    "code": "ab90",
    "more_info": "https://bmatic.com/docs/errors/ab90"
}
```

Returns all tickets created by a specific customer.

<aside class="notice">
<strong>Order:</strong> The bookings are sorted descendantly by the field : <code>created_at</code>.
</aside>

<aside class="warning">
<strong>Caution:</strong> For this operation its necesary indicate a specific customer, You have two options, send the parameters <code>customer_id_type</code> and <code>customer_id_number</code> or just send <code>customer_id</code>. If you send all parameters, the API just consider the parameter <code>customer_id</code>.
</aside>

### Endpoint

`GET /customer/v1/bookings`

### Query Params

| |
|:---|
|**customer_id** *string* <span class="recomended-param">recomended</span><br>Customer unique identifier used in your company. <p>*Validation pattern*: <code>^[0-9A-Za-z]{1,20}$</code></p> |
|**customer_id_type** *string* <br>Type of customer ID. <p>*Validation pattern*: <code>^[0-9a-zA-Z]{1,2}$</code></p> |
|**customer_id_number** *integer* <br>Number of customer ID. <p>*Validation pattern*: <code>^[0-9a-zA-Z]{1,16}$</code></p> |
|**fields** *array[string]* <span class="recomended-param">recomended</span> <br> Entity fields that will return at response. For example: `fields=id,code`. |

### Responses

| |
|:---|
|**200** *array[[Booking](#ticket)]* <br>A list of bookings. |
|**400** *[Error](#error)* <br>Bad request. |
|**500** *[Error](#error)* <br>An error has occurred.|


## Get Booking

> Sample request:

```http
GET /v1/bookings/a90mos70om HTTP/1.1
```

> Sample success response:

```http
HTTP/1.1 200 OK
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

> Sample error responses:

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
    "message": "Requested field not found."
}
```
```http
HTTP/1.1 404 Not Found
Content-Type: application/json

{
    "message": "Booking not found."
}
```
```http
HTTP/1.1 500 Internal Server Error
Content-Type: application/json

{
    "message": "An error has ocurred.",
    "code": "ab90",
    "more_info": "https://bmatic.com/docs/errors/ab90"
}
```

Returns a customer booking by ID.

### Endpoint

`GET /customer/v1/bookings/{booking_id}`

### Path Params

| |
|:---|
|**booking_id** *string* <span class="required-param">required</span> <br>Unique identifier of Booking. For example `a90mos70om`.|

### Query Params

| |
|:---|
|**fields** *array[string]* <span class="recomended-param">recomended</span> <br> Entity fields that will return at response. For example: `fields=id,queue,number`. |

### Responses

| |
|:---|
|**200** *[Booking](#booking)* <br>A booking.|
|**400** *[Error](#error)* <br>Bad request. |
|**404** *[Error](#error)* <br>Booking not found. |
|**500** *[Error](#error)* <br>An error has occurred.|

## Create Booking

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

> Sample success response:

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

> Sample error responses:

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
    "message": "Invalid branch ID."
}
```
```http
HTTP/1.1 500 Internal Server Error
Content-Type: application/json

{
    "message": "An error has ocurred.",
    "code": "ab90",
    "more_info": "https://bmatic.com/docs/errors/ab90"
}
```

Create a new customer booking and then it returns it.


### Endpoint

`POST /customer/v1/bookings`

### Request

| |
|:---|
|**branch_id** *string* <span class="required-param">required</span> <br> Unique identifier of branch request by customer. |
|**service_id** *string* <span class="required-param">required</span> <br> Unique identifier of service requested by customer. |
|**channel** *string* <span class="recomended-param">recomended</span><br> Unique identifier of the channel used. Used only for audit purpose. |
|**phone** *string* <span class="recomended-param">recomended</span><br> Customer phone for notifications. |
|**start_time** *string* <span class="required-param">required</span> <br> Start time of booking. |
|**end_time** *string* <span class="required-param">required</span> <br> End time of booking. |
|**customer_id** *string* <br> Unique identifier of the channel used. Used only for audit purpose. |
|**customer_id_type** *string* <br> Unique identifier of customer id type. |
|**customer_id_number** *string*  <br> Number of customer id. |

### Responses

| |
|:---|
|**201** *[Booking](#booking-object)* <br>A booking.|
|**400** *[Error](#error)* <br>Bad request. |
|**500** *[Error](#error)* <br>An error has occurred.|

## Update Booking

> Sample request:

```http
PATCH /customer/v1/bookings/a90mos70om HTTP/1.1
Content-Type: application/json

{
    "phone": "+51908999189"
}
```

> Sample success response:

```http
HTTP/1.1 204 No Content
```

> Sample errors responses:

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
    "message": "Invalid phone number."
}
```
```http
HTTP/1.1 404 Not Found
Content-Type: application/json

{
    "message": "Booking not found."
}
```
```http
HTTP/1.1 500 Internal Server Error
Content-Type: application/json

{
    "message": "An error has ocurred.",
    "code": "ab90",
    "more_info": "https://bmatic.com/docs/errors/ab90"
}
```

Update a specific customer booking.

###Endpoint

`PATCH /customer/v1/bookings/{booking_id}`

### Path Params

| |
|:---|
|**booking_id** *string* <span class="required-param">required</span> <br>Unique identifier of booking. For example `a90mos70om`.|

### Request

| |
|:---|
|**phone** *string* <br> New customer phone for notifications. |

### Responses

| |
|:---|
|**204** *no content* <br>Successful update.|
|**400** *[Error](#error)* <br>Bad request. |
|**404** *[Error](#error)* <br>Booking not found. |
|**500** *[Error](#error)* <br>An error has occurred.|

## Delete Booking

> Sample request:

```http
DELETE /customer/v1/bookings/a90mos70om HTTP/1.1
```

> Sample success response:

```http
HTTP/1.1 204 No Content
```

> Sample error responses:

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
    "message": "Invalid phone number."
}
```
```http
HTTP/1.1 404 Not Found
Content-Type: application/json

{
    "message": "Booking not found."
}
```
```http
HTTP/1.1 500 Internal Server Error
Content-Type: application/json

{
    "message": "An error has ocurred.",
    "code": "ab90",
    "more_info": "https://bmatic.com/docs/errors/ab90"
}
```

Delete a customer booking by ID.


###Endpoint

`DELETE /customer/v1/bookings/{booking_id}`

### Path Params

| |
|:---|
|**booking_id** *string* <span class="required-param">required</span> <br>Unique identifier of booking. For example `a90mos70om`.|

### Responses

| |
|:---|
|**204** *no content* <br>Successful deletion.|
|**400** *[Error](#error)* <br>Bad request. |
|**404** *[Error](#error)* <br>Booking not found. |
|**500** *[Error](#error)* <br>An error has occurred.|
