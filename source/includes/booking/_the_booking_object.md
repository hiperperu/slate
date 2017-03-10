
## The Booking object

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
