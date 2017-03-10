
## The Ticket object

> Sample object:

```json
{
    "id": "89m32b0998",
    "queue": "T",
    "number": 2,
    "channel": "mobile",
    "status": "BLOCKED",
    "low_estimated_time": "10",
    "high_estimated_time": "15",
    "phone": "+51987776576",
    "messages":[
        "We have a promotion for you!"
    ],
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
    "sector": {
        "id": "s8",
        "name": "Tower A",
        "short_name": "A",
        "status": "OPEN"
    },
    "service": {
        "id": "7b6",
        "name": "Plataforma",
        "short_name": "Plataforma"
    },
    "created_at": "2017-02-20T10:00:00.000Z",
    "updated_at": "2017-02-20T10:00:00.000Z"
}
```

Model of ticket object.

<aside class="warning">
<strong>Caution:</strong> The entities associated to ticket not provide all their fields for performance reasons. If you need more information, you can use others endpoints to get this information using the ids returned in the ticket. You can to see the default information provided in the sample object.
</aside>

### Fields

| |
|:---|
|**id** *string* <br>Ticket unique identifier. <p>*Validation pattern*: <code>^[0-9a-z]{8,16}$</code></p> |
|**queue** *string* <br>Id of queue assigned to ticket. <p>*Validation pattern*: <code>^[0-9a-zA-Z]{1,4}$</code> |
|**number** *integer* <br>Position of ticket in queue. <p>*Minimun*: <code>1</code><br> *Maximum*: <code>9999</code></p> |
|**channel** *string* <br>Code of channel used. <p>*Maximum length*: <code>20</code></p> |
|**status** *enum* <br>Current status of the branch. <p>*Possible values*: <ul><li><code>BLOCKED</code></li><li><code>ENABLED</code></li></ul></p> |
|**low_estimated_time** *integer* <br> Lower bound of the estimated waiting time. <p>*Minimun:* <code>0</code></p>|
|**high_estimated_time** *integer* <br> Upper bound of the estimated waiting time. <p>*Minimun:* <code>0</code></p>|
|**phone** *string* <br>Customer phone for notifications. <p>*Validation pattern*: <code>^\+[1-9]{1}[0-9]{3,14}$</code></p> |
|**messages** *array[string]* <br> List of messages to customer.|
|**branch** *[Branch](#branch)* <br> Branch associated.</p> |
|**sector** *[Sector](#sector)* <br> Sector associated.</p> |
|**service** *[Service](#service)* <br> Service associated.</p> |
|**created_at** *date-time* <br> Datetime of ticket creation. <p>*Standard*: <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p> |
|**updated_at** *date-time* <br> Datetime of the last update of ticket. <p>*Standard*: <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p>  |
