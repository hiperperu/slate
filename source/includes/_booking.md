
# Booking


## Booking Range Object
```json
{
    "capacity": "integer",
    "start_time": "string",
    "end_time": "string"
}
```

Time range with available bookings.


### Fields
Name | Type | Format | Description
--- | --- | --- | ---
capacity | integer | int32 | Booking capacity of range.
start_time | string | date-time | Start time of range.
end_time | string | date-time | End time of range.


## Booking Day Object
```json
{
    "day": "string",
    "ranges": [
        {
            "capacity": "integer",
            "start_time": "string",
            "end_time": "string"
        }
    ]
}
```

Day with available bookings.


### Fields
Name | Type | Format | Description
--- | --- | --- | ---
day | string | date | Day of time ranges with available bookings.
ranges | array[[BookingRange](#bookingrange)] |  | List of time ranges with available bookings


## Booking Object
```json
{
    "id": "string"
}
```

Booking model.


### Fields
Name | Type | Format | Description
--- | --- | --- | ---
id | string |  | Booking unique identifier.


## Get All Bookings

```http
GET /v1/bookings HTTP/1.1
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "id": "string"
    }
]
```
```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
    "message": "Status sended is not valid."
}
```
```http
HTTP/1.1 404 Not Found
```
```http
HTTP/1.1 500 Internal Server Error
```

Returns all bookings created by a specific customer, the bookings are sorted descendantly by the creation date.


### Parameters
Name | In | Type | Description
--- | --- | --- | ---
customer_id_type<span title="required" class="required">&nbsp;*&nbsp;</span> | query | string | Unique identifier of customer id type.
customer_id_number<span title="required" class="required">&nbsp;*&nbsp;</span> | query | string | Number of customer id.
status | query | string | Optional. Status of booking.
fields | query | array[string] | Optional. Entity fields that will return at response.
offset | query | integer | Optional. Position in pagination. Default is zero.
limit | query | integer | Optional. Number of items to retrieve. Default is 10, maximum is 50.

### Responses
Http code | Type | Description
--- | --- | ---
200 | array[[Booking](#booking)] | A list of bookings.
400 | [Error](#error) | Bad request.
404 | no content | Non exists bookings that fulfill the filters.
500 | no content | An error has occurred.

## Create Booking

```http
POST /v1/bookings HTTP/1.1
```

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "id": "string"
}
```
```http
HTTP/1.1 400 Bad Request
```
```http
HTTP/1.1 500 Internal Server Error
```

Create a new customer booking and then it returns it.


### Parameters
Name | In | Type | Description
--- | --- | --- | ---
channel<span title="required" class="required">&nbsp;*&nbsp;</span> | formData | string | Unique identifier of the channel used. This value is used to identify the type of device that consumes the API and should to be configured in administrative web of BMATIC.
branch_id<span title="required" class="required">&nbsp;*&nbsp;</span> | formData | string | Unique identifier of branch requested.
service_id<span title="required" class="required">&nbsp;*&nbsp;</span> | formData | string | Unique identifier of service requested.
customer_id_type<span title="required" class="required">&nbsp;*&nbsp;</span> | formData | string | Unique identifier of customer id type.
customer_id_number<span title="required" class="required">&nbsp;*&nbsp;</span> | formData | string | Number of customer id.
start_time<span title="required" class="required">&nbsp;*&nbsp;</span> | formData | string | Start time of booking.
end_time<span title="required" class="required">&nbsp;*&nbsp;</span> | formData | string | End time of booking.

### Responses
Http code | Type | Description
--- | --- | ---
201 | [Booking](#booking) | Successful creation.
400 | no content | Bad request.
500 | no content | An error has occurred.


## Get Booking

```http
GET /v1/bookings/{booking_id} HTTP/1.1
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": "string"
}
```
```http
HTTP/1.1 400 Bad Request
```
```http
HTTP/1.1 404 Not Found
```
```http
HTTP/1.1 500 Internal Server Error
```

Returns a customer booking by ID.


### Parameters
Name | In | Type | Description
--- | --- | --- | ---
booking_id<span title="required" class="required">&nbsp;*&nbsp;</span> | path | string | Unique identifier of booking.
fields | query | array[string] | Optional. Entity fields that will return at response.

### Responses
Http code | Type | Description
--- | --- | ---
200 | [Booking](#booking) | A booking.
400 | no content | Bad request.
404 | no content | Booking not found.
500 | no content | An error has occurred.

## Delete Booking

```http
DELETE /v1/bookings/{booking_id} HTTP/1.1
```

```http
HTTP/1.1 204 No Content
```
```http
HTTP/1.1 400 Bad Request
```
```http
HTTP/1.1 404 Not Found
```
```http
HTTP/1.1 500 Internal Server Error
```

Delete a customer booking by ID.


### Parameters
Name | In | Type | Description
--- | --- | --- | ---
booking_id<span title="required" class="required">&nbsp;*&nbsp;</span> | path | string | Unique identifier of booking.

### Responses
Http code | Type | Description
--- | --- | ---
204 | no content | Successful deletion.
400 | no content | Bad request.
404 | no content | Booking not found.
500 | no content | An error has occurred.


## Get Days For Book

```http
GET /v1/bookings/days HTTP/1.1
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
    {
        "day": "string",
        "ranges": [
            {
                "capacity": "integer",
                "start_time": "string",
                "end_time": "string"
            }
        ]
    }
]
```
```http
HTTP/1.1 400 Bad Request
```
```http
HTTP/1.1 404 Not Found
```
```http
HTTP/1.1 500 Internal Server Error
```

Returns a list of days for book a specific service in a branch. The days are sorted ascendantly.


### Parameters
Name | In | Type | Description
--- | --- | --- | ---
branch_id<span title="required" class="required">&nbsp;*&nbsp;</span> | query | string | Unique identifier of branch requested.
service_id<span title="required" class="required">&nbsp;*&nbsp;</span> | query | string | Unique identifier of service requested.
offset | query | integer | Optional. Position in pagination. Default is zero.
limit | query | integer | Optional. Number of items to retrieve. Default is 10, maximum is 50.

### Responses
Http code | Type | Description
--- | --- | ---
200 | array[[BookingDay](#bookingday)] | A list of booking days.
400 | no content | Bad request.
404 | no content | Non exists available booking days.
500 | no content | An error has occurred.
