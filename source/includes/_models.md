
# Models
## Error

> Sample of error with help:

```json
{
    "message": "Not allowed service for the branch.",
    "code": "9m86",
    "more_info": "https://bmatic.com/docs/errors/9m86"
}
```

> Sample of simple error:

```json
{
    "message": "Branch not found.",
}
```

HTTP body used when an error occurred.

<aside class="notice">
All errors ocurred in the API return a message as information minimal.
</aside>

<aside class="notice">
All error fields are read only.
</aside>

### Fields
Name | Type | Description
--- | --- | ---
message<span title="required" class="required">&nbsp;\*&nbsp;</span>  | string | A descriptive message regarding the exception.
code | string | An error code to find help for the exception.
more_info | string | The URL of BMatic's documentation for the error code. If the error code is undefined then this value is undefined too.


## BookingRange
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


## BookingDay
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


## Booking
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
