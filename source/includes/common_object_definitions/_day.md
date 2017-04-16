
## Day

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
