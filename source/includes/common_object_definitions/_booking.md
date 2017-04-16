
## Booking

> Sample object:

```json
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

Model of booking object.

<aside class="warning">
<strong>Caution:</strong> The entities associated to ticket not provide all their fields for performance reasons. If you need more information, you can use others endpoints to get this information using the ids returned in the ticket. You can to see the default information provided in the sample object.
</aside>

### Fields

* **id** <span class="param-type">String</span> <br> Booking unique identifier.
* **code** <span class="param-type">String</span> <br> Booking code to display it to customer.
* **status** <span class="param-type">Enum</span> <br> Current status of the booking. <p>*Possible values*: <ul><li><code>ACTIVE</code></li><li><code>INACTIVE</code></li><li><code>DEFEATED</code></li></ul></p>
* **phone** <span class="param-type">String</span> <br> Customer phone for notifications.
* **channel** <span class="param-type">[Channel](#channel)</span> <br> Channel associated.
* **branch** <span class="param-type">[Branch](#branch)</span> <br> Branch associated.</p>
* **service** <span class="param-type">[Service](#service)</span> <br> Service associated.</p>
* **startTime** *date-time* <br> Start time of booking. <p>*Standard*: <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p>
* **endTime** *date-time* <br> End time of booking.<p>*Standard*: <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p>
* **createdAt** *date-time* <br> Datetime of ticket creation. <p>*Standard*: <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p>
* **updatedAt** *date-time* <br> Datetime of the last update of ticket. <p>*Standard*: <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p>
