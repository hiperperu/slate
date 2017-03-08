
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

## Service

> Sample model:

```json
{
    "id": "7b6",
    "name": "Plataforma",
    "short_name": "Plataforma"
}
```

Service model.

<aside class="notice">
All service fields are mandatory and read only.
</aside>

### Fields
Name | Type | Description
--- | --- | ---
id<span title="required" class="required">&nbsp;\*&nbsp;</span> | string | Service unique identifier.
name<span title="required" class="required">&nbsp;\*&nbsp;</span> | string | Complete name of the service.
short_name<span title="required" class="required">&nbsp;\*&nbsp;</span> | string | Short name of service, used to display the service in small devices.

## Branch
```json
{
    "id": "string",
    "name": "string",
    "short_name": "string",
    "code": "string",
    "address": "string",
    "latitude": "number",
    "longitude": "number",
    "status": "string",
    "opening_time": "string",
    "closing_time": "string",
    "low_estimated_time": "integer",
    "high_estimated_time": "integer",
    "congestion_level": "string",
    "is_virtual": "boolean",
    "is_bookable": "boolean",
    "sectors": []
}
```

Branch of BMATIC.


### Fields
Name | Type | Description
--- | ---  | ---
id | string | Branch unique identifier.
name | string | Complete name of the branch.
short_name | string | Short name of branch, used to display it in small devices.
code | string | Unique identifier for the branch used in your company system.
address | string | Address of the branch.
latitude | number | Latitude component of branch location.
longitude | number | Longitude component of branch location.
status | string | Current status of the branch.<div>Possible values:</div><ul class="enum"><li>open</li><li>close</li></ul>
opening_time | string | Opening time of the branch at current day, or next opening datetime.
closing_time | string | Closing time of the branch at current day or next closing datetime.
low_estimated_time | integer | Lower bound of the estimated waiting time. It is undefined when the branch is closed.
high_estimated_time | integer | Upper bound of the estimated waiting time. It is undefined when the branch is closed.
congestion_level | string | Congestion level of the branch. It is undefined when the branch is closed. <div>Posible values:</div><ul class="enum"><li>low</li><li>medium</li><li>high</li></ul>
is_virtual | boolean | Indicator of the possibility to create virtual tickets.
is_bookable | boolean | Indicator of the possibility to bookings.
sectors| array[[Sector](#sector)] | List of the branch's sectors.


## Sector
```json
{
    "id": "string",
    "name": "string",
    "short_name": "string",
    "status": "string",
    "opening_time": "string",
    "closing_time": "string"
}
```

Branch sector of BMATIC.


### Fields
Name | Type | Format | Description
--- | --- | --- | ---
id | string |  | Sector unique identifier.
name | string |  | Complete name of sector.
short_name | string |  | Short name of sector, used to display it in small devices.
status | string | <div>Acceptable values:</div><ul class="enum"><li>open</li><li>close</li></ul> | Current status of the branch.
opening_time | string | date-time | Opening time of the sector at current day, or next opening datetime.
closing_time | string | date-time | Closing time of the sector at current day or next closing datetime.

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


## Ticket
```json
{
    "id": "string"
}
```

Ticket model.


### Fields
Name | Type | Format | Description
--- | --- | --- | ---
id | string |  | Ticket unique identifier.
