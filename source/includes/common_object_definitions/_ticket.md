
## Ticket

> Sample object:

```json
{
    "id": "89m32b0998",
    "queue": "T",
    "number": 2,
    "status": "BLOCKED",
    "lowEstimatedTime": "10",
    "highEstimatedTime": "15",
    "phone": "+51987776576",
    "messages": [
        "We have a promotion for you!"
    ],
    "channel": {
        "id": "a10",
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
        "status": "OPEN",
        "congestion_level": "MEDIUM"
    },
    "sector": {
        "id": "s8",
        "name": "Tower A",
        "shortName": "A",
        "status": "OPEN"
    },
    "service": {
        "id": "7b6",
        "name": "Plataforma",
        "shortName": "Plataforma"
    },
    "createdAt": "2017-02-20T10:00:00.000Z",
    "updatedAt": "2017-02-20T10:00:00.000Z",
    "print": [
        {
            "align": "CENTER",
            "font": "A_REGULAR",
            "previous": "Welcome to",
            "content": "Hiper",
            "next": "!"
        }
    ]
}
```

Model of ticket object.

<aside class="warning">
<strong>Caution:</strong> The entities associated to ticket not provide all their fields for performance reasons. If you need more information, you can use others endpoints to get this information using the ids returned in the ticket. You can to see the default information provided in the sample object.
</aside>

### Fields

* **id** <span class="param-type">String</span> <br>Ticket unique identifier.
* **queue** <span class="param-type">String</span> <br>Id of queue assigned to ticket.
* **number** <span class="param-type">Integer</span> <br>Position of ticket in queue.
* **status** <span class="param-type">Enum</span> <br>Current status of the branch. <p>*Possible values*: <ul><li><code>BLOCKED</code></li><li><code>ENABLED</code></li></ul></p>
* **lowEstimatedTime** <span class="param-type">Integer</span> <br> Lower bound of the estimated waiting time.
* **highEstimatedTime** <span class="param-type">Integer</span> <br> Upper bound of the estimated waiting time.
* **phone** <span class="param-type">String</span> <br>Customer phone for notifications.
* **messages** <span class="param-type">List\<String\></span> <br> Messages to print.
* **channel** <span class="param-type">[Channel](#channel)</span> <br>Channel associated.
* **branch** <span class="param-type">[Branch](#branch)</span> <br> Branch associated.</p>
* **sector** <span class="param-type">[Sector](#sector)</span> <br> Sector associated.</p>
* **service** <span class="param-type">[Service](#service)</span>  <br> Service associated.</p>
* **createdAt** <span class="param-type">DateTime</span> <br> Datetime of ticket creation. <p>*Standard*: <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p>
* **updatedAt** <span class="param-type">DateTime</span> <br> Datetime of the last update of ticket. <p>*Standard*: <code>[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)</code></p>  
* **print**
